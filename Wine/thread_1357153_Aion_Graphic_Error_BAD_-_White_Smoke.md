---
title: "Aion Graphic Error BAD - White Smoke"
date: 2009-12-16
forum: Wine
---

### Post by anku on 2009-12-16
I can get Aion to start up, login, and even enter my character, BUT i get this weird white box/smoke/cloud which effects my whole screen. 

I have tried changing the environment of wine, change some of the settings within Aion, and tried emulating Desktop with Wine. 

AND after tweaking and trying to run Aion for about 10 minutes, my whole computer freezes. This includes starting up Aion, shutting it down, opening winecfg, and using the terminal. 
NOTE:  The game does in fact freeze my whole computer, and I only get these freezes when the game is open. 

Ubuntu 9.10 x64 
ATI 4800 
ATI Drivers 2.1.9016 
Wine 1.1.33 
No Visual Effect

---

### Post by anku on 2009-12-29
bump

---

### Post by Acidphase on 2011-06-19
Well guess no one answered this after a Year lol.

The problem is that ATI GLSL in aion well just doesn't work fix:
Run in temrinal

wine regedit

Navigate to:
HKEY_CURRENT_USER\Software\Wine\Direct3D

Add Sting 
UseGLSL = disabled

Hope this helps a year later .... lol

---

