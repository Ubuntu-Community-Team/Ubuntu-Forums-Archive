---
title: "PTViewer / java applets / apache2 server"
date: 2007-02-08
forum: Server Platforms
---

### Post by DoorGunner on 2007-02-08
Hi 

I have an apache2 server with php5 in which i am trying to run a java applet.

I downloaded PTViewer. Ran a jar xf ptviewer2.5.jar. To the best of my knowledge you just place the ptviewer.jar and the ptviewer.class onto where your photos and html are stored. 

The code i entered into the html is 
> 
<applet
   archive="ptviewer.jar"
   code="ptviewer.class"
   width="400"
   height="300">
   <param
     name="loag"
     value="/var/www/e107_images/loag.jpg" />
 </applet>

technically the PTVieweer applet should run in my website. Instead it shows up for less than a second and disappears.

on a second application I get the box that it should show up in but it has a small X instead of the photo.

Can anyone advise?

---

