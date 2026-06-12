---
title: "Patching Wine for Shin Megami Tensei"
date: 2010-06-25
forum: Wine
---

### Post by Zireth ZH on 2010-06-25
Hey guys im trying to run Shin Megami Tensei, i need a patch for wine so the game can fully render the graphics or something. its called SW vertex blending i think...

 Ive been looking for the how to's on how to patch wine .. but i cant follow.. 

please can someone guide me in this process? thanks

this is the patch 

[http://dl.dropbox.com/u/4482398/wine-vertblend/wine-1.1.31_vertblend.patch](http://dl.dropbox.com/u/4482398/wine-vertblend/wine-1.1.31_vertblend.patch)


Developer of the patch says: 

''Patch implementing software vertex blending in wine-1.1.44

Patch ported to wine-1.1.44.

P.S.: Apply the patch with `patch -p1 -i /PATH TO/vertex_blend_sw-1.1.44.diff`
inside the wine source tree.
P.P.S.: I'm the original developer of this patch. ;)''

---

### Post by asdfoo on 2010-06-25
You need to download a copy of the wine source, apply the patch with the command listed there, build the source and then run that copy of Wine which you have compiled.

[http://wiki.winehq.org/Patching](http://wiki.winehq.org/Patching)

---

