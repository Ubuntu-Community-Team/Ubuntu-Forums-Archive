---
title: "Nvidia Driver"
date: 2009-08-04
forum: Server Platforms
---

### Post by fhunkydelix on 2009-08-04
I tried to install my driver using Hardware drivers and activate the Nvidia accelerated graphics driver version 173 but it won't activate. now i installed blender to make sure i had openGL or my right driver installed but this showed:


Processing triggers for libc6 ...
ldconfig deferred processing now taking place
fhunkybuntu@FhunkyServer:~$ blender
Compiled with Python version 2.6.2.
Checking for installed Python... got it!
Xlib:  extension "GLX" missing on display ":0.0".
intern/ghost/intern/GHOST_WindowX11.cpp:177: X11 glxChooseVisual() failed for OpenGL, verify working openGL system!
X Error of failed request:  BadWindow (invalid Window parameter)
  Major opcode of failed request:  18 (X_ChangeProperty)
  Resource id in failed request:  0x9
  Serial number of failed request:  12
  Current serial number in output stream:  13

---

