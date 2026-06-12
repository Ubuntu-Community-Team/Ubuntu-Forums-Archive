---
title: "Previously working EVE install now crashing after splash screen"
date: 2011-06-09
forum: Wine
---

### Post by sbf2009 on 2011-06-09
I tried seeing what was going on using Terminal and got this:

```
sbf2009@GAUSSERV:~$ wine C:\Program\ Files/CCP/EVE/eve.exe
err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
fixme:heap:HeapSetInformation 0x47e000 0 0x33f648 4
EVE Client version 6.45 build 267203 starting  18:12:06
Network layer using: StacklessIO
Multi-Language System: Client using language [EN]
Starting up Trinity through _trinity_deploy.dll ...
err:winediag:X11DRV_WineGL_InitOpenglInfo Unable to activate OpenGL context, most likely your OpenGL drivers haven't been installed correctly
err:wgl:X11DRV_WineGL_InitOpenglInfo  couldn't initialize OpenGL, expect problems
err:d3d_caps:WineD3D_CreateFakeGLContext Can't find a suitable iPixelFormat.
err:d3d:InitAdapters Failed to get a gl context for default adapter
Direct3D9 is not available without OpenGL.
err:d3d_caps:WineD3D_CreateFakeGLContext Can't find a suitable iPixelFormat.
err:d3d:InitAdapters Failed to get a gl context for default adapter
Direct3D9 is not available without OpenGL.
An exception has occurred.  It has been logged in the log server as exception #1

```I think I may have recently updated my system and caused something to break with one of those updates.

---

### Post by jtarin on 2011-06-09
> Unable to activate OpenGL context, most likely your OpenGL drivers haven't been installed correctlySeems you changed your video driver maybe.
Have you tried winetricks?

([http://wiki.winehq.org/winetricks](http://wiki.winehq.org/winetricks) )

That should help you to install Opengl support for wine.

It is under "ddr=opengl Set DirectDrawRenderer to OpenGL"


You may want to give playonlinux a try also: [http://www.playonlinux.com/en/](http://www.playonlinux.com/en/)

---

### Post by sbf2009 on 2011-06-13
I had winetricks up already...but I guess it won't hurt to reinstall. Never heard of play on linux though.

---

### Post by sbf2009 on 2011-06-13
Fixed it, turns out I have to reinstall NVIDIA drivers every time I update....:neutral:

---

### Post by Perfect Storm on 2011-06-13
> **sbf2009 said:**
> Fixed it, turns out I have to reinstall NVIDIA drivers every time I update....:neutral:

Sounds like you have installed Nvidia driver manually. This won't happen if you use the driver from Ubuntu's 'Additional Drivers'.

---

### Post by Elfy on 2011-06-13
Thread moved to Wine.

---

