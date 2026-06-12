---
title: "Running WoW error..."
date: 2009-02-07
forum: Wine
---

### Post by Ice799 on 2009-02-07
When I try to run WoW I get:

Xlib:  extension "GLX" missing on display ":0.0".
err:wgl:X11DRV_WineGL_InitOpenglInfo  couldn't initialize OpenGL, expect problems
fixme:advapi:SetSecurityInfo stub
fixme:powrprof:DllMain (0x7cfe0000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:powrprof:DllMain (0x7cfe0000, 0, (nil)) not fully implemented
fixme:win:EnumDisplayDevicesW ((null),0,0x33ede4,0x00000000), stub!
err:d3d:WineD3D_CreateFakeGLContext Can't find a suitable iPixelFormat
err:d3d:InitAdapters Failed to get a gl context for default adapter
err:d3d:WineDirect3DCreate Direct3D9 is not available without opengl
err:d3d:WineD3D_CreateFakeGLContext Can't find a suitable iPixelFormat
err:d3d:InitAdapters Failed to get a gl context for default adapter
err:d3d:WineDirect3DCreate Direct3D9 is not available without opengl
fixme:win:EnumDisplayDevicesW ((null),0,0x33f34c,0x00000000), stub!

And then this in another window:
This application has encountered a critical error:

ERROR #132 (0x85100084) Fatal Exception
Program:	C:\Program Files\World of Warcraft\WoW.exe
Exception:	0xC0000005 (ACCESS_VIOLATION) at 0023:0067BF05

The instruction at "0x0067BF05" referenced memory at "0x00000054".
The memory could not be "read".


WoWBuild: 6080

I am running a x86-64bit Ubuntu 8.10.

I know probably been posted before but i couldnt finding anything on the post that i looked on... I went to [https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft) and didnt find anything that helped me

Anyone know how to fix this?

EDIT: Strach this fixed it myself...  after few hours of messing around i found that my video card driver got disabled after running wow it messed up my resolution and gave me out out of range error and it basically zoomed into a spot then turn off my monitor... so had to reboot go into recovery.. then boot into failsafe and disable my driver reboot enable drivers and it runs

:D

---

