---
title: "Diablo 2 white screen"
date: 2011-02-12
forum: Wine
---

### Post by cbob on 2011-02-12
Hello,

I've just installed Diablo 2 + LOD, that worked fine. Starting the game also work, the blizzard videos roll by with sound and all. But when the menu is suppose to appear the the screen (virtual desktop) turns white and gamma shoots up.

Some system info:
```

$ lsb_release -d
Description:    Ubuntu 10.10
$ wine --version
wine-1.3.13

```When im running the game:
```
$ wine .wine/drive_c/users/bob/Desktop/Diablo\ II/Diablo\ II.exe 
fixme:advapi:SetSecurityInfo stub
err:d3d:check_fbo_compat >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from Framebuffer format check @ utils.c / 1090
err:d3d:check_fbo_compat >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from Framebuffer format check @ utils.c / 1090
err:d3d:check_fbo_compat >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from Framebuffer format check @ utils.c / 1090
err:d3d:check_fbo_compat >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from Framebuffer format check @ utils.c / 1090
err:d3d:check_fbo_compat >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from Framebuffer format check @ utils.c / 1090
fixme:win:EnumDisplayDevicesW ((null),0,0x33e9e8,0x00000000), stub!
fixme:x11drv:X11DRV_desktop_SetCurrentMode Cannot change screen BPP from 32 to 16
fixme:d3d:swapchain_init Add OpenGL context recreation support to context_validate_onscreen_formats
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x4024328,0x4024228): stub
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x4024328,0x4024228): stub
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x4024328,0x4024228): stub
fixme:x11drv:X11DRV_desktop_SetCurrentMode Cannot change screen BPP from 32 to 16
fixme:d3d:swapchain_init Add OpenGL context recreation support to context_validate_onscreen_formats
err:ddraw:ddraw_surface7_Flip Can't find a flip target
err:ddraw:ddraw_surface7_Flip Can't find a flip target
[B]fixme:x11drv:X11DRV_desktop_SetCurrentMode Cannot change screen BPP from 32 to 16
fixme:d3d:swapchain_init Add OpenGL context recreation support to context_validate_onscreen_formats[/B]

```The bold text is what happens when screen(desktop) goes white.

Wine config:

[LIST]
[*]Running in virtual desktop (800x600)
[*]Unchecked 'Allow the window manager to controll the windows'
[*]Audio ASLA
[/LIST]
```
$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)

```Installed PlayOnLinux, but that did nothing.

How to proceed?

regards,
cbob

---

### Post by artemka373 on 2011-03-28
I have GMA 3150
```

$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller (rev 02)
```

1. Yes, "Emulate a virtual desktop" should be checked.
2.1 Try enabling/disabling pixel/vertex shaders (without -opengl I can play only with only Pixel Shaders).
2.2 Try to start Game.exe -opengl (with Pixel and Vertex shaders enabled). It is much faster, though I have shadows all over the screen :(

---

### Post by mastablasta on 2011-03-28
additionally there is a patch that makes it play well in OpenGL. Also try fullscreen.

---

### Post by Soulcage on 2011-03-29
You could try running the game in 3dfx using this: [http://www.svenswrapper.de/english/index.html]("http://www.svenswrapper.de/english/index.html")
You extract the files into the diablo II folder then run the exe, then you can set it to use your desktop resolution then save or w/e. Then you run the diablo II video tester or w/e then choose 3dfx (or was it glide). Then run the game. Although you might have problems because you're using an intel gpu.

---

### Post by cbob on 2011-03-29
All of the sudden, all this awesome tips! I can however not attempt any of them for a few day, but thought I say thanks in advance:D and I'll get back later to inform of any successes.

regards,
cbob

---

### Post by oblidor on 2011-03-31
Run the D2Vidtest and choose the 2D and not Direct3D and it works perfectly. with the 3D it gives a white screen with a yellow square.

---

### Post by cbob on 2011-05-04
Sorry for the delay!

Using your tips it now works fine! Thanks!

So some summary of how i got it to work(changes from post #1):

[LIST]
[*]Vertex shaders to none
[*]Installed patch 1.13c
[*]Ran D2Vidtest and chose 2D instead of 3D
[*]Ran game without CD
[/LIST]
Thanks again!

/cbob

---

