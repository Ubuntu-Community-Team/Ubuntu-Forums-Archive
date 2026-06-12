---
title: "Running WoW Through Wine, &quot;Failed to find a suitable display device&quot;"
date: 2010-07-11
forum: Wine
---

### Post by omnisource on 2010-07-11
Alright, So I finally got wow installed and running through wine, it patched all the way up just fine, and I installed my latest nVidia drivers. Then when I goto play the game, I get this error "Failed to find suitable display device." Well I searched and found this fix in the wowwiki, but I have no clue how to do what they are saying, can I get some help with this? Thanks


**  Failed to find a suitable display  device. **

 This is usually direct3d in cause. You may try to overwrite the  d3d9.dll, or use the builtin one if you're already overwriting it. Try  switching between [gxApi]("http://www.wowwiki.com/CVar_gxApi") opengl and d3d as well. Also, if using  OpenGL, ensure that glx is loaded in the Module section of your  xorg.conf file.

---

### Post by asdfoo on 2010-07-12
are you on 64bit and forgot to install the nv 32bit opengl compat drivers?

---

### Post by Rody on 2010-07-15
> **asdfoo said:**
> are you on 64bit and forgot to install the nv 32bit opengl compat drivers?


You should not have to do that. The nvidia drivers loaded in any of the latest ubuntu releses should work just find to play wow, it is posable that you have a configuration error, try nvidia-xconfig. I guess we are not supposed to have a Xorg.conf but maybe this will fix it.

rody

---

