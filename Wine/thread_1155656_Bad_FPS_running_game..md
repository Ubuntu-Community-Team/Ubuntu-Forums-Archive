---
title: "Bad FPS running game."
date: 2009-05-11
forum: Wine
---

### Post by Spacemonstar on 2009-05-11
I'm a complete newbie when it comes to linux and appreciate any hep that can be given.

I've spent the better part of 2 days researching on how to improve my fps to run my current choice of game, namely Legend of Mir 2. This game runs in 640x480 16bpp colour depth (even though it thinks its 8bpp!).

I've tried changing my resolution and colour depth to match the game, then running to no effect.
I've tried changing to OpenGL (the game doesn't support it).
I've tried the new NVIDIA Drivers (and lost about 5 hours of my life repairing Ubuntu!) with no effect
I've tried (and currently still using) the restricted NVIDIA Drivers.
I've tried as many different Wine configurations as possible.
I've tried development and stable versions of wine.
I've tried Cedega which didn't want to install.
I've tried Crossover which didn't allow the game to run.
I recently just tried running wine from within Terminal in order to get the error dump below.

There are other things I've tried, but I've lost count now!
At the moment I am working with a fresh install. Wine 1.1.12 current Development release, restricted drivers and nothing else.

I noticed a few errors in the following log, but I'm at a loss on how to fix them. Your help would be appreciated.


This was run in 16bpp
```

paulbrook@home:~/.wine/drive_c/GamepotUSA/Mir2$ fixme:ole:TLB_ReadTypeLib Header type magic 0x00905a4d not supported.
err:ole:TLB_ReadTypeLib Loading of typelib L"C:\\GamepotUSA\\Mir2\\Mir2Patch.exe" failed with error 0
fixme:ole:TLB_ReadTypeLib Header type magic 0x00905a4d not supported.
err:ole:TLB_ReadTypeLib Loading of typelib L"C:\\GamepotUSA\\Mir2\\Mir2Patch.exe" failed with error 0
fixme:shdocvw:PersistStreamInit_InitNew (0x140270)
fixme:shdocvw:OleObject_Advise (0x140270)->(0x861e1c, 0x861e74)
fixme:shdocvw:ViewObject_SetAdvise (0x140270)->(1 00000000 0x861e1c)
fixme:shdocvw:ViewObject_Draw (0x140270)->(1 -1 (nil) (nil) (nil) 0x30c 0x861e8c 0x861e8c (nil) 00000000)
fixme:system:SetProcessDPIAware stub!
fixme:dwmapi:DwmIsCompositionEnabled 0x33c4f4
0[1464e0]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\nss3.dll") - Symbol NSGetModule not found
0[1464e0]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\sqlite3.dll") - Symbol NSGetModule not found
0[1464e0]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\js3250.dll") - Symbol NSGetModule not found
0[1464e0]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\nssckbi.dll") - Symbol NSGetModule not found
0[1464e0]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\nspr4.dll") - Symbol NSGetModule not found
0[1464e0]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\xul.dll") - Symbol NSGetModule not found
0[1464e0]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\ssl3.dll") - Symbol NSGetModule not found
0[1464e0]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\plugins\npnul32.dll") - Symbol NSGetModule not found
0[1464e0]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\plc4.dll") - Symbol NSGetModule not found
0[1464e0]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\freebl3.dll") - Symbol NSGetModule not found
0[1464e0]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\plds4.dll") - Symbol NSGetModule not found
0[1464e0]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\nssutil3.dll") - Symbol NSGetModule not found
0[1464e0]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\xpcom.dll") - Symbol NSGetModule not found
0[1464e0]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\nssdbm3.dll") - Symbol NSGetModule not found
0[1464e0]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\softokn3.dll") - Symbol NSGetModule not found
0[1464e0]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\smime3.dll") - Symbol NSGetModule not found
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x140310)->((null) 1 0x33ca8c (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x140310)->((null) 25 2 0x33caa0 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x140310)->((null) 26 2 0x33caa0 (nil))
fixme:ole:TLB_ReadTypeLib Header type magic 0x00905a4d not supported.
err:ole:TLB_ReadTypeLib Loading of typelib L"C:\\GamepotUSA\\Mir2\\Mir2Patch.exe" failed with error 0
fixme:ole:TLB_ReadTypeLib Header type magic 0x00905a4d not supported.
err:ole:TLB_ReadTypeLib Loading of typelib L"C:\\GamepotUSA\\Mir2\\Mir2Patch.exe" failed with error 0
fixme:ole:TLB_ReadTypeLib Header type magic 0x00905a4d not supported.
err:ole:TLB_ReadTypeLib Loading of typelib L"C:\\GamepotUSA\\Mir2\\Mir2Patch.exe" failed with error 0
fixme:ole:TLB_ReadTypeLib Header type magic 0x00905a4d not supported.
err:ole:TLB_ReadTypeLib Loading of typelib L"C:\\GamepotUSA\\Mir2\\Mir2Patch.exe" failed with error 0
fixme:shdocvw:ClientSite_GetContainer (0x140310)->(0x33cadc)
fixme:shdocvw:ClOleCommandTarget_Exec (0x140310)->({000214d1-0000-0000-c000-000000000046} 37 0 0x33cbb0 (nil))
fixme:shdocvw:HttpNegotiate_BeginningTransaction (0x13fe10)->(L"" L"" 0 0x33cbe8)
fixme:shdocvw:ClOleCommandTarget_Exec (0x140310)->((null) 29 2 0x33c8cc (nil))
fixme:shdocvw:DocHostUIHandler_GetDropTarget (0x140310)
fixme:shdocvw:ClientSite_GetContainer (0x140310)->(0x33c758)
fixme:shdocvw:InPlaceFrame_SetStatusText (0x140310)->(0xb7e90051)
fixme:shdocvw:ClOleCommandTarget_Exec (0x140310)->((null) 25 2 0x33c68c (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x140310)->((null) 26 2 0x33c68c (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x140310)->((null) 21 2 (nil) (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x140310)->((null) 28 2 0x33c884 (nil))
0[1464e0]: NPN Logging Active!
0[1464e0]: General Plugin Logging Active! (nsPluginHostImpl::ctor)
0[1464e0]: NPP Logging Active!
0[1464e0]: nsPluginHostImpl::ctor
fixme:resource:GetGuiResources (0xffffffff,0): stub
fixme:shdocvw:ViewObject_SetAdvise (0x140270)->(1 00000000 (nil))
fixme:shdocvw:OleObject_Unadvise (0x140270)->(0)
fixme:shdocvw:OleObject_Close (0x140270)->(1)
fixme:mshtml:HlinkTarget_SetBrowseContext (0x141998)->((nil))
err:ole:CoGetClassObject class {88d969c0-f192-11d4-a65f-0040963251e5} not registered
err:ole:create_server class {88d969c0-f192-11d4-a65f-0040963251e5} not registered
err:ole:CoGetClassObject no class object {88d969c0-f192-11d4-a65f-0040963251e5} could be created for context 0x5
err:msxml:xmlnode_get_baseName Unhandled type 8
err:msxml:xmlnode_get_baseName Unhandled type 8
err:msxml:xmlnode_get_baseName Unhandled type 8
err:msxml:xmlnode_get_baseName Unhandled type 8
fixme:win:EnumDisplayDevicesW ((null),0,0x33ea30,0x00000000), stub!
fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 16 to 8
fixme:ddraw:IDirectDrawImpl_WaitForVerticalBlank (0x1838a8)->(1,(nil)): Stub
fixme:shdocvw:OleObject_Close (0x17f5e8)->(1)
fixme:msxml:DllCanUnloadNow

```
This was run in 8bpp (edited - removed the same code from beginning)
```

Xlib:  extension "GLX" missing on display ":0.0".
err:wgl:X11DRV_WineGL_InitOpenglInfo  couldn't initialize OpenGL, expect problems
err:d3d:WineD3D_CreateFakeGLContext Can't find a suitable iPixelFormat
err:d3d:InitAdapters Failed to get a gl context for default adapter
fixme:ddraw:IDirectDrawImpl_WaitForVerticalBlank (0x1843c0)->(1,(nil)): Stub
fixme:shdocvw:OleObject_Close (0x1800f8)->(1)
fixme:msxml:DllCanUnloadNow 

```

---

### Post by asdfoo on 2009-05-11
1.1.12 is broken, please don't use it. 1.1.21 is the latest development release

which video card and drivers do you have now?  the log suggests they aren't installed properly

glxinfo | grep -i version
glxinfo | grep renderer

---

### Post by Spacemonstar on 2009-05-11
> **asdfoo said:**
> 1.1.12 is broken, please don't use it. 1.1.21 is the latest development release

which video card and drivers do you have now?  the log suggests they aren't installed properly

glxinfo | grep -i version
glxinfo | grep renderer

Hi, thanks for responding. 

In the interim I disabled the restricted drivers and started using Envy (again). I finally got OpenGL to work as it wasn't before, but I'm still suffering the same problem.
Here is the information you are after:
```

paulbrook@home:~$ glxinfo | grep -i version
server glx version string: 1.4
client glx version string: 1.4
GLX version: 1.3
OpenGL version string: 2.1.2 NVIDIA 173.14.16
OpenGL shading language version string: 1.20 NVIDIA via Cg compiler
paulbrook@home:~$ glxinfo | grep renderer
OpenGL renderer string: Quadro FX 1300/PCI/SSE2

```


n.B - I am/was using the 1.1.21 drivers :)

---

### Post by asdfoo on 2009-05-11
> **Spacemonstar said:**
> Hi, thanks for responding. 

In the interim I disabled the restricted drivers and started using Envy (again). I finally got OpenGL to work as it wasn't before, but I'm still suffering the same problem.
Here is the information you are after:
```

paulbrook@home:~$ glxinfo | grep -i version
server glx version string: 1.4
client glx version string: 1.4
GLX version: 1.3
OpenGL version string: 2.1.2 NVIDIA 173.14.16
OpenGL shading language version string: 1.20 NVIDIA via Cg compiler
paulbrook@home:~$ glxinfo | grep renderer
OpenGL renderer string: Quadro FX 1300/PCI/SSE2

```


n.B - I am/was using the 1.1.21 drivers :)

Hmm, it could be a performance issue in Wine related to the lack of a DIB engine which is said to give a speed boost to games like Age of Empires and other isometric tile/sprite based games.

There is an unofficial patch which requires patching and recompiling Wine that may help your situation.

I tried to register to download and test this game for myself to best advise you but the account registration page is buggy, it keeps telling me to check my nickname and my email is invalid.

I tried to register here: [http://mir2.gamepotusa.com/index.html](http://mir2.gamepotusa.com/index.html)

But also found [http://www.legendofmir.net/](http://www.legendofmir.net/) which says they have shutdown the servers as of March 31st.. maybe this is why I can't register.

Is there a different way you play the game, a private server or something?

---

### Post by Spacemonstar on 2009-05-11
> **asdfoo said:**
> Hmm, it could be a performance issue in Wine related to the lack of a DIB engine which is said to give a speed boost to games like Age of Empires and other isometric tile/sprite based games.

There is an unofficial patch which requires patching and recompiling Wine that may help your situation.

I tried to register to download and test this game for myself to best advise you but the account registration page is buggy, it keeps telling me to check my nickname and my email is invalid.

I tried to register here: [http://mir2.gamepotusa.com/index.html](http://mir2.gamepotusa.com/index.html)

But also found [http://www.legendofmir.net/](http://www.legendofmir.net/) which says they have shutdown the servers as of March 31st.. maybe this is why I can't register.

Is there a different way you play the game, a private server or something?

The original link you have: [http://mir2.gamepotusa.com/index.html](http://mir2.gamepotusa.com/index.html) is the correct one. You must 'Check the Availability' of all 3 parts, username/email/nickname or something like that. It's only after all three are validated that it will let you through. They don't tell you that though. The game was just released from beta so I'll allow them a little indiscretion!

The previous distributors (Game Network) destroyed Legend of Mir 2 and it has now been taken up by the American company 'Gamepot USA'.

I did read about the DIB engine speeding up sprite based games like Legend of Mir 2. But it was just a glean over. I'll go and check up on that now.

I'm also trying Wine 1.1.16 now as it's mentioned in WineHQ AppDB as working well with Mir 2... Unfortunately the test was done for a private server executable rather than the official one.

I'll post back here with any errors I get from that.

---

### Post by Spacemonstar on 2009-05-11
<!-- edit -->

I just found a nice deb package with 1.1.21 and DIB engine.. Saved me a task I guess as I had no idea what to do:

[http://bugs.winehq.org/show_bug.cgi?id=421#c197](http://bugs.winehq.org/show_bug.cgi?id=421#c197)

The game is now working MUCH better than it was. My only problem now is the text is all thick black and basically impossible to read. I think there are some improvenments made for this further down the page, but I'm at a loss with what to do with them lol..

I apprecaite your help in getting me onto the DIB track anyway. My friends and I can at least play now as we use TS2 anyway.
If you know how to fix the text issue, that would be great :P

---

### Post by asdfoo on 2009-05-11
> **Spacemonstar said:**
> <!-- edit -->

I just found a nice deb package with 1.1.21 and DIB engine.. Saved me a task I guess as I had no idea what to do:

[http://bugs.winehq.org/show_bug.cgi?id=421#c197](http://bugs.winehq.org/show_bug.cgi?id=421#c197)

The game is now working MUCH better than it was. My only problem now is the text is all thick black and basically impossible to read. I think there are some improvenments made for this further down the page, but I'm at a loss with what to do with them lol..

I apprecaite your help in getting me onto the DIB track anyway. My friends and I can at least play now as we use TS2 anyway.
If you know how to fix the text issue, that would be great :P

The text issue could be a short coming of the work-in-progress-DIB-engine, I'd report the problem to the person who provided the deb package, otherwise if you build from source then apply the DIB patches yourself you could post on bugzilla, but since you're using the package it's better to report it to the person who is providing it.

---

