# simple-page
simple web page
link to live site: https://psolsrud.github.io/simple-page/.

Test text


<html>
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="initial-scale=1, maximum-scale=1, user-scalable=no">
  <title>Cambridge Map JS Test</title>
  <style>
    html, body, #viewDiv {
      padding: 0;
      margin: 0;
      height: 100%;
      width: 100%;
    }
  </style>
  <link rel="stylesheet" href="https://js.arcgis.com/4.11/esri/css/main.css">
  <script src="https://js.arcgis.com/4.11/"></script>

  <script>
    require([
      "esri/Map",
      "esri/views/MapView",
      "esri/layers/FeatureLayer"
    ], function(Map, MapView, FeatureLayer) {
      
      var map = new Map({
        basemap: "topo-vector"
      });

      var view = new MapView({
        container: "viewDiv",  
        map: map,
        center: [-93.226037,45.565689],
        zoom: 15
             });

     //////////////////////////// 
      
       // Define a popup for Trailheads
      var popupCambridgeBusiness = {
        "title": "{COMPANY}",
        "content": "<b>Address:</b> {ADDRESS}<br><b>Employees:</b> {EMPLOYEES}<br><b>Sales:</b> {SALESCODE}"
      }
      
      
      
      
        // Create the layer and add Cambridge Business Location Data to Map
      
      var Enriched_Cambridge_business_employeeslayer = new FeatureLayer({
        url: "https://services3.arcgis.com/juvie9NFXORsK38U/ArcGIS/rest/services/Enriched_Cambridge_business_employees/FeatureServer/0",
        outFields: ["COMPANY"],
        popupTemplate: popupCambridgeBusiness
      });
      
      
      //Add the layer
      map.add(Enriched_Cambridge_business_employeeslayer, 0);
      
  /////////////////////////////////

    });
  </script>
</head>
<body>
  <div id="viewDiv"></div>
</body>
</html> 
