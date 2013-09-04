# Terraformer ArcGIS JSON Parser

This plugin handles 2 way conversion between [GeoJSON](http://geojson.org/geojson-spec.html) and the [ArcGIS Geometryy](http://help.arcgis.com/en/arcgisserver/10.0/apis/rest/geometry.html) format used by Esri.

This package is part of the [Terraformer](https://github.com/Esri/Terraformer) project.

## Installing

### Node.js

    $ npm install terraformer-arcgis-parser

### Browser

In the browser, [Terraformer](http://github.com/esri/terraformer) is required.

You can use [Bower](http://bower.io/) to install the components if you like or download them and host them yourself.

```
$ bower install terraformer
$ bower install terraformer-arcgis-parser
```

## Usage

* `parse(json)` - parse ArcGIS JSON into a [Terraformer.Primitive](). If the object is in the Web Mercator spatial reference it will be converted to WGS84. Aliased as `fromGeoJSON`.
* `convert(json, spatialReference)` - Convert GeoJSON or a [Terraformer.Primitive]() into ARCGIS JSON. You can also pass a valid ArcGIS spatial reference like `{ wkid:102100 }` as the second parameter. By default [we assume WGS84 like GeoJSON](http://geojson.org/geojson-spec.html#coordinate-reference-system-objects). Aliased as `toGeoJSON`

### Node.js

    var ArcGIS = require('terraformer-wkt-parser');
    
    // parse ArcGIS JSON, convert it to a Terraformer.Primitive
    var primitive = ArcGIS.parse({
        x:"-122.6764",
        y:"45.5165",
        spatialReference: {
          wkid: 4326
        }
      });
    
    // take a Terraformer.Primitive or GeoJSON and convert it to ArcGIS JSON
    var point = ArcGIS.convert({
      "type": "Point",
      "coordinates": [45.5165, -122.6764]
    });

### Browser

The Terraformer ArcGIS Parser can be used in the browser with some simple includes.

```html
  <!-- Load the main Terraformer library -->
  <script src="terraformer.min.js" type="text/javascript"></script>
  
  <!-- Load the ArcGIS Parser -->
  <script src="terraformer-arcgis-parser.min.js" type="text/javascript"></script>
  
  <!-- Use it! -->
  <script>
    var primitive = Terraformer.ArcGIS.parse({
      x:"-122.6764",
      y:"45.5165",
      spatialReference: {
        wkid: 4326
      }
    });

    // take a Terraformer.Primitive or GeoJSON and convert it to ArcGIS JSON
    var point = Terraformer.ArcGIS.convert({
      "type": "Point",
      "coordinates": [45.5165, -122.6764]
    });
  </script>
  ```

[](Esri Tags: Terraformer GeoJSON ArcGIS)
[](Esri Language: JavaScript)