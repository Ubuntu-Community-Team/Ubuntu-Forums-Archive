---
title: "Open-Source Map-tool to use in a software"
date: 2010-11-12
forum: The Cafe
---

### Post by Kdar on 2010-11-12
Is there some open-source map-tool that can be used in a software?

I am having in mind something like google-maps or Google Earth.

---

### Post by ve4cib on 2010-11-12
Depending on what exactly it is you want to do, there are a few options:

[OpenStreetMap](http://www.openstreetmap.org/) has reasonably good-quality street maps for most of the world.  OpenCycleMap is a related project for bicycle and walking paths.

[OpenLayers](http://openlayers.org/) is a Javascript library for rendering tiled map services in a browser.  It can consume Google Maps data, OpenStreetMap, Yahoo Maps, Bing Maps, ArcGIS services, and pretty much anything else that can provide tiled map data.  It may also do dynamic maps, but I can't remember for sure.  OpenLayers is simply a set of tools to display and manipulate the maps; it doesn't actually give you any mapping data on its own.

[OSGeo.org](http://www.osgeo.org/) is the Open Source Geospatial Foundation.  They've got a whole slew of resources (from tile server software to clients to conferences, etc...) that may be useful to you.

What kind of map data & functionality are you looking for exactly?

---

### Post by Kdar on 2010-11-12
I am looking more for a 3d-map. Something to which I can add some basic meshes, objests.. etc.. able to change it.

I guess, maybe something like one of those terrain gaming engines, but more light-weight.

---

### Post by sanderd17 on 2010-11-29
you can use marble, but marble only displays free information. So sattelite images and openstreetmap.

---

