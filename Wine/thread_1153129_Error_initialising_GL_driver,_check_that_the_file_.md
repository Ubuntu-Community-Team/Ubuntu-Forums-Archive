---
title: "Error initialising GL driver, check that the file 'opengl32.dll' exists.. Half-Life"
date: 2009-05-08
forum: Wine
---

### Post by skierkyles on 2009-05-08
Im trying to run Half-Life 1 and Counter Strike through steam, and when I try to start either game, I get 

```
Error initialising GL driver, check that the file 'opengl32.dll' exists
```

I have found a few threads similar to my problem, but none of there solutions seem to work..

I have a NVidia graphics card with the 185.53 driver.

and I'm running Wine 1.1.20

---

### Post by cogadh on 2009-05-08
It might help if you told us what you have already tried and provided Wine's terminal output.

---

### Post by skierkyles on 2009-05-08
This thread suggested installing a few dependencies. 
[http://ubuntuforums.org/showthread.php?t=306319](http://ubuntuforums.org/showthread.php?t=306319)
Its pretty old, and I dont think it even applys to my problem though. 
```
fontforge libgl1-mesa-dev libgtk1.2 xorg-dev 
```
I installed all these.

and what should I do for the terminal output? When I do wine hl.exe it just tries to run the program, and prints out nothing, but comes up with the same error.

```
kyle@kyle-PC:~/WineDrive/Program Files/Steam/steamapps/mysteamname/half-life$ wine hl.exe
kyle@kyle-PC:~/WineDrive/Program Files/Steam/steamapps/mysteamname/half-life$ 
```

---

### Post by cogadh on 2009-05-08
That's because the Steam version needs to be run with Steam:
```
cd ~/.wine/drive_c/Progam\ Files/Steam
wine steam.exe -applaunch 70
```
Don't change directories into the steamapps directory, just go as far as the main Steam directory and run it from there. One minor configuration change you should make is turning off Steam's community features before running a game. That has been a problem with games run through Steam for a while and I'm not sure it has been fully corrected in Wine yet.

You probably didn't need to install any of those extra packages, but they shouldn't hurt anything if they are there.

---

### Post by skierkyles on 2009-05-08
Thanks for clearing up how to start the game, how do I determine what number a game is?

anyway, I disabled all the community features, and started the game like you said and I get alot of stuff, but I think the troubled lines are...
```

err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
err:wgl:has_opengl Failed to load libGL: libGL.so.1: cannot open shared object file: No such file or directory
err:wgl:has_opengl OpenGL support is disabled.
err:d3d:WineD3D_CreateFakeGLContext Can't find a suitable iPixelFormat
err:d3d:InitAdapters Failed to get a gl context for default adapter
err:d3d:WineDirect3DCreate Direct3D9 is not available without opengl
err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
fixme:shdocvw:ViewObject_SetAdvise (0x18cdf8)->(1 00000002 0x1e53338)
fixme:shdocvw:PersistStreamInit_InitNew (0x18cdf8)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0x18cdf8)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x18cdf8)->(ffffffff)
fixme:shdocvw:OleInPlaceObject_InPlaceDeactivate (0x18cdf8)
fixme:shdocvw:OleInPlaceObject_UIDeactivate (0x18cdf8)
fixme:shdocvw:OleObject_Close (0x18cdf8)->(1)
err:module:load_builtin_dll failed to load .so lib for builtin L"OPENGL32.dll": libGL.so.1: cannot open shared object file: No such file or directory
err:module:import_dll Loading library OPENGL32.dll (which is needed by L"C:\\Program Files\\Steam\\GameOverlayRenderer.dll") failed (error c000007a).
err:module:load_builtin_dll failed to load .so lib for builtin L"OPENGL32.dll": libGL.so.1: cannot open shared object file: No such file or directory
err:module:import_dll Loading library OPENGL32.dll (which is needed by L"C:\\Program Files\\Steam\\GameOverlayRenderer.dll") failed (error c000007a).
err:wgl:has_opengl Failed to load libGL: libGL.so.1: cannot open shared object file: No such file or directory
err:wgl:has_opengl OpenGL support is disabled.
err:d3d:WineD3D_CreateFakeGLContext Can't find a suitable iPixelFormat
err:d3d:InitAdapters Failed to get a gl context for default adapter
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found 1440x900x32 @0! (XRandR)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found 640x480x16 @0! (XRandR)
err:module:load_builtin_dll failed to load .so lib for builtin L"opengl32.dll": libGL.so.1: cannot open shared object file: No such file or directory
err:ntdll:RtlpWaitForCriticalSection section 0xcf709c "?" wait timed out in thread 001f, blocked by 0020, retrying (60 sec)
```

I have tried reinstalling my graphics drivers, and that didnt help at all.

Thanks a bunch for the help so far!

---

### Post by cogadh on 2009-05-08
You can find the applaunch numbers here:
[http://developer.valvesoftware.com/wiki/Steam_Application_IDs](http://developer.valvesoftware.com/wiki/Steam_Application_IDs)

Are you using the pre-compiled Wine package from Wine HQ, or did you compile it yourself?

---

### Post by skierkyles on 2009-05-08
Im using the packages from this repo

[http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

---

### Post by asdfoo on 2009-05-08
> err:wgl:has_opengl Failed to load libGL: libGL.so.1: cannot open shared object file: No such file or directory
err:wgl:has_opengl OpenGL support is disabled.


Reinstall your drivers.

---

### Post by NightMKoder on 2009-05-08
Also make sure that glxgears shows gears spinning. Otherwise, not a wine issue.

---

### Post by cogadh on 2009-05-08
Considering it is specifying a certain missing library, have you checked to see if that library is actually present in /usr/lib? You might also want to confirm that the package that includes that library, libgl1-mesa-glx, is actually installed or reinstall it.

---

### Post by asdfoo on 2009-05-08
> **cogadh said:**
> Considering it is specifying a certain missing library, have you checked to see if that library is actually present in /usr/lib? You might also want to confirm that the package that includes that library, libgl1-mesa-glx, is actually installed or reinstall it.

why install mesa? he said in his original post he has nvidia.  like I said 3 posts ago he should reinstall his drivers, if it's a 64bit system then maybe he forgot to install the 32bit gl drivers which would provide libgl.so.1

---

### Post by skierkyles on 2009-05-08
Epic high-5 to everybody, Updated to the 185.18.08 driver, which reinstalled the 32bit gl stuff, and now it works!

Thanks Kyle

---

### Post by cogadh on 2009-05-08
> **asdfoo said:**
> why install mesa? he said in his original post he has nvidia.  like I said 3 posts ago he should reinstall his drivers, if it's a 64bit system then maybe he forgot to install the 32bit gl drivers which would provide libgl.so.1
Because that package is one of the dependencies of the Nvidia driver package and the library in that package is the one Wine is complaining about missing. If for some reason that package was not installed or installed incorrectly, he could have fixed the problem without having to re-install his drivers by simply installing that particular package.

---

### Post by asdfoo on 2009-05-09
> **cogadh said:**
> Because that package is one of the dependencies of the Nvidia driver package and the library in that package is the one Wine is complaining about missing. If for some reason that package was not installed or installed incorrectly, he could have fixed the problem without having to re-install his drivers by simply installing that particular package.

unlikely... libGL.so.1 is the nvidia binary driver not mesa.

---

### Post by cogadh on 2009-05-09
It may be included with the Nvidia driver package, but it is not actually the driver (that's nvidia_drv.so) and it is not the only way to get that file. It is simply a part of the OpenGL API that is included with the driver as well as some other packages, including the one I mentioned. That package also happens to be one of the Nvidia driver dependencies, so if anyone is using the Nvidia driver, it should be installed already. 

If you don't believe me, check the package information in Synaptic yourself, you may be surprised by what you find.

---

### Post by asdfoo on 2009-05-09
> **cogadh said:**
> It may be included with the Nvidia driver package, but it is not actually the driver (that's nvidia_drv.so) and it is not the only way to get that file. It is simply a part of the OpenGL API that is included with the driver as well as some other packages, including the one I mentioned. That package also happens to be one of the Nvidia driver dependencies, so if anyone is using the Nvidia driver, it should be installed already. 

If you don't believe me, check the package information in Synaptic yourself, you may be surprised by what you find.

asdfoo@tonewise:/usr/lib$ strings libGL.so.1 | grep NVIDIA
NVIDIA Corporation
NVIDIA OpenGL Driver requires CPUs with SSE to run.
nvidia id: NVIDIA OpenGL Shared Library  180.51  Fri Apr 17 00:34:49 PDT 2009

---

### Post by cogadh on 2009-05-10
Regardless of whether or not that shared OpenGL library is provided with the Nvidia driver, it is not the actual driver, it is not unique to Nvidia and you can get it from multiple sources, including the package I mentioned, without needing to reinstall your drivers.

---

### Post by asdfoo on 2009-05-10
> **cogadh said:**
> Regardless of whether or not that shared OpenGL library is provided with the Nvidia driver, it is not the actual driver, it is not unique to Nvidia and you can get it from multiple sources, including the package I mentioned, without needing to reinstall your drivers.

It is specific to nvidia, all the OpenGL calls go through libGL.so, including vendor specific extensions, so you need the one supplied by nvidia if anything is to work correctly.

The one provided by mesa is for DRI.

---

