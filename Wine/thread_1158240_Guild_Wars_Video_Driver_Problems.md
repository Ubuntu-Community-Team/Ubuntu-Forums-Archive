---
title: "Guild Wars Video Driver Problems"
date: 2009-05-13
forum: Wine
---

### Post by clrogers on 2009-05-13
I recently upgraded my OS to Ubuntu Studio 9.04. I reinstalled wine and Guild Wars but can't get the program to launch. I can't find any information on how to fix this problem. I've tried reinstalling the graphics driver, both from the package and also from the hardware drivers program to no avail. I have also tried to uninstall and reinstall Guild Wars.

Ubuntu 9.04 with Studio extras
Wine 1.1.21
Terminal Output:

~/.wine/drive_c/Program Files/Guild Wars$ wine Gw.exe
err:wgl:get_formats glXChooseFBConfig returns NULL
err:d3d:WineD3D_CreateFakeGLContext Can't find a suitable iPixelFormat
err:d3d:InitAdapters Failed to get a gl context for default adapter
err:d3d:WineDirect3DCreate Direct3D8 is not available without opengl
err:wgl:get_formats glXChooseFBConfig returns NULL
err:d3d:WineD3D_CreateFakeGLContext Can't find a suitable iPixelFormat
err:d3d:InitAdapters Failed to get a gl context for default adapter
err:d3d:WineDirect3DCreate Direct3D8 is not available without opengl
err:ntdll:RtlpWaitForCriticalSection section 0x7e464900 "x11drv_main.c: X11DRV_CritSection" wait timed out in thread 0017, blocked by 0009, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0x7ec2cfe0 "gdiobj.c: GDI_level" wait timed out in thread 0029, blocked by 0017, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0xa10550 "?" wait timed out in thread 001b, blocked by 001c, retrying (60 sec)
err:seh:raise_exception Exception frame is not in stack limits => unable to dispatch exception.
Terminated

NVIDIA GeForce 8800m GTS
NVIDIA-Linux-x86_64-180.51.pkg2.run

---

### Post by asdfoo on 2009-05-14
> **clrogers said:**
> I recently upgraded my OS to Ubuntu Studio 9.04. I reinstalled wine and Guild Wars but can't get the program to launch. I can't find any information on how to fix this problem. I've tried reinstalling the graphics driver, both from the package and also from the hardware drivers program to no avail. I have also tried to uninstall and reinstall Guild Wars.

Ubuntu 9.04 with Studio extras
Wine 1.1.21
Terminal Output:

~/.wine/drive_c/Program Files/Guild Wars$ wine Gw.exe
err:wgl:get_formats glXChooseFBConfig returns NULL
err:d3d:WineD3D_CreateFakeGLContext Can't find a suitable iPixelFormat
err:d3d:InitAdapters Failed to get a gl context for default adapter
err:d3d:WineDirect3DCreate Direct3D8 is not available without opengl
err:wgl:get_formats glXChooseFBConfig returns NULL
err:d3d:WineD3D_CreateFakeGLContext Can't find a suitable iPixelFormat
err:d3d:InitAdapters Failed to get a gl context for default adapter
err:d3d:WineDirect3DCreate Direct3D8 is not available without opengl
err:ntdll:RtlpWaitForCriticalSection section 0x7e464900 "x11drv_main.c: X11DRV_CritSection" wait timed out in thread 0017, blocked by 0009, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0x7ec2cfe0 "gdiobj.c: GDI_level" wait timed out in thread 0029, blocked by 0017, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0xa10550 "?" wait timed out in thread 001b, blocked by 001c, retrying (60 sec)
err:seh:raise_exception Exception frame is not in stack limits => unable to dispatch exception.
Terminated

NVIDIA GeForce 8800m GTS
NVIDIA-Linux-x86_64-180.51.pkg2.run

It says you don't have 32bit opengl drivers, you need to say Yes when it prompts you during the nvidia install.

---

### Post by clrogers on 2009-05-15
I wish it were that simple, but every time I have installed the video drivers I have chosen to install the 32bit opengl drivers. Is there something else I am missing?

---

