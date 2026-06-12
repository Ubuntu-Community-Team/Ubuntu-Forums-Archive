---
title: "Steam, Day of Defeat Source fps"
date: 2009-08-04
forum: Wine
---

### Post by nothreat33 on 2009-08-04
I just installed steam and Day of Defeat source without a problem. The game runs fine except for one thing. My frames per second are less than half what I get on my windows installation on the same computer. I have the GeForce 8800 GT, and version 180 recommended nvidia driver installed. When I run glxgears I get between 7500-8500 fps, so i'm pretty certain my graphics driver is working properly. I also get about the same frames when using 1024x768 and 1280x1024.

Anyone have a fix for the low fps? I've heard it's a known issue. Also some textures aren't loading. If i get this game running i wont need windows anymore so i really want to fix this.

---

### Post by castlefox on 2009-08-05
Are all of the texture turned down?  

Dont forget to turn off AA

---

### Post by darklegion on 2009-08-06
Wine has a bug that causes low performance with Source games (except the original HL2).If you want to get your hands dirty, you can try one of the patches here: [http://bugs.winehq.org/show_bug.cgi?id=12453](http://bugs.winehq.org/show_bug.cgi?id=12453)

Or you can try a lower dxlevel on the commandline like this:
```
wine <name of exe> -dxlevel 81
```
Exchange 81 for 70, if it's still too slow.

---

