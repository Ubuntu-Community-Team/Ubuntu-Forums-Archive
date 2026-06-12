---
title: "I'm looking for a Digital Terrain Modelling app"
date: 2007-10-23
forum: The Cafe
---

### Post by bwallum on 2007-10-23
Hi

I have x,y,z co-ordinates from a ground survey and want to generate a 3D digital terrain model from them. The data is in a simple csv text file.

I then want to export the model and import it into SketchUp for further processing.

Does anybody know of any apps that will run in Gutsy and produce a rendered 3D surface model?

Thanks
Bob

---

### Post by bwallum on 2007-10-31
For those interested:-

Gmsh (open source) allows x,y,z co-ordinates to be imported from an ASCII text file. Points can be linked with lines and lines linked with planes. Surfaces can be created and meshed. The resulting surface can be exported as a vrml file. Very good programme for manually editing small detail. Gives good visualisation of survey data.

Load through Applications>Add/remove search for Gmsh.

---

### Post by PartisanEntity on 2007-10-31
I was reading about such an application the other day, apparently it has been around since the 80's and is quite mature: [**GRASS: Geostatistics and spatial data analysis**]("http://grass.itc.it/statsgrass/index.php"). It does 3D modelling too I think, check out Google images.

---

### Post by bwallum on 2007-11-03
Thanks for that, I think I have Gmsh going well now and it is supported by Ubuntu. I just need to get the output into a dxf format. I can get vrml and spl out, blender can import it allegedly and export to dxf.

---

