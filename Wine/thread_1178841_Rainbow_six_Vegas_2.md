---
title: "Rainbow six Vegas 2"
date: 2009-06-04
forum: Wine
---

### Post by Cody the Linux Guru on 2009-06-04
I just though i would inform everyone about the current running condition of one of my favorite games rainbow six vegas 2 it install fine without any tweaks but running the actual game there are a few tweaks you have to make

hkey_current_user > software > wine > Direct3D 
and put in
"OffscreenRenderingMode=fbo" in order to just start the game or else it will say your video card is not supported

also it has the same mouse problem  that crysis has that if you turn in a direction the mouse will go off screen so you have to go to

hkey_current_user > software > wine > DirectInput 
and set "MouseWarpOverride" to force 

then after you done all that it runs fine except for it crashing every 3 minutes :( so if anyone can find a fix for that the game will be perfect any help at all would be much appreciated ;)

---

