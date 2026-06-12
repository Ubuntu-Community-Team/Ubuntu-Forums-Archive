---
title: "Warcraft 3 doesn't open with OpenGL"
date: 2008-12-20
forum: Wine
---

### Post by dethredic on 2008-12-20
So, I just installed WC3, and when I go to run it it asks me to install directx 8.1 or later. I told it to run in opengl mode though.

I used this to run it:

> wine '/home/phil/.wine/dosdevices/c:/Program Files/Warcraft III/War3.exe' -opengl 

I then tried this:
> 
phil@ubuntu:~$ wine '/home/phil/.wine/dosdevices/c:/Program Files/Warcraft III/War3.exe' -opengl &
[1] 29646
phil@ubuntu:~$ err:ole:CoCreateInstance apartment not initialised
Xlib:  extension "GLX" missing on display ":0.0".
err:wgl:X11DRV_WineGL_InitOpenglInfo  couldn't initialize OpenGL, expect problems
err:d3d:WineD3D_CreateFakeGLContext Can't find a suitable iPixelFormat
err:d3d:InitAdapters Failed to get a gl context for default adapter
err:d3d:WineDirect3DCreate Direct3D8 is not available without opengl
fixme:win:EnumDisplayDevicesW ((null),0,0x32f46c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x32f4a4,0x00000000), stub!
fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 16


I dunno why it opengl doesn't like meh.

---

### Post by binbash on 2008-12-20
this is a problem with your xorg.conf

Google > Xlib: extension "GLX" missing on display ":0.0".

or quickly try this : 

Section "Extensions"
Option "Composite" "Disable"
EndSection

add this to your xorg.conf .

---

### Post by dethredic on 2008-12-20
> **binbash said:**
> this is a problem with your xorg.conf

Google > Xlib: extension "GLX" missing on display ":0.0".

or quickly try this : 

Section "Extensions"
Option "Composite" "Disable"
EndSection

add this to your xorg.conf .

added and it doesn't work.

---

### Post by YokoZar on 2008-12-21
Don't launch it that way

cd to the directory and then launch it:

wine war3.exe -opengl


Also you need to enable proprietary video drivers it looks like OpenGL is completely disabled (or did you perhaps compile Wine yourself and do it incorrectly?)

---

