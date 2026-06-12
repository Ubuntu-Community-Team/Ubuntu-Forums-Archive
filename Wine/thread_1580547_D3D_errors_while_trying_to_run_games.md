---
title: "D3D errors while trying to run games"
date: 2010-09-23
forum: Wine
---

### Post by weavil on 2010-09-23
New linux user, I did search around but couldn't find a solution. 

Trying to run WoW SC2 and HL2 get same error on all. 

In WoW config.wtf I added 

SET gxAPI "OpenGL"

glxinfo | grep rendering
direct rendering: Yes

fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 5700 Series
OpenGL version string: 4.0.10188 Compatibility Profile Context

wine --version
wine-1.2


Pop up error when trying to run wow.exe

Failed to find a suitable display device. Exiting program.

Error in term

err:wgl:X11DRV_WineGL_InitOpenglInfo  couldn't initialize OpenGL, expect problems
archive Data\enUS\patch-enUS.MPQ opened
archive Data\patch.MPQ opened
archive Data\enUS\patch-enUS-2.MPQ opened
archive Data\enUS\patch-enUS-3.MPQ opened
archive Data\patch-2.MPQ opened
archive Data\patch-3.MPQ opened
archive Data\expansion.MPQ opened
archive Data\lichking.MPQ opened
archive Data\common.MPQ opened
archive Data\common-2.MPQ opened
archive Data\enUS\locale-enUS.MPQ opened
archive Data\enUS\speech-enUS.MPQ opened
archive Data\enUS\expansion-locale-enUS.MPQ opened
archive Data\enUS\lichking-locale-enUS.MPQ opened
archive Data\enUS\expansion-speech-enUS.MPQ opened
archive Data\enUS\lichking-speech-enUS.MPQ opened
fixme:win:EnumDisplayDevicesW ((null),0,0x195ee20,0x00000000), stub!
err:d3d_caps:WineD3D_CreateFakeGLContext Can't find a suitable iPixelFormat.
err:d3d:InitAdapters Failed to get a gl context for default adapter
Direct3D9 is not available without OpenGL.
err:d3d_caps:WineD3D_CreateFakeGLContext Can't find a suitable iPixelFormat.
err:d3d:InitAdapters Failed to get a gl context for default adapter
Direct3D9 is not available without OpenGL.

In "HKEY_CURRENT_USER/Software/Wine" I have no entry for Direct3d.

---

### Post by weavil on 2010-09-23
I added

[HKEY_CURRENT_USER\Software\Wine\Direct3D]
"Multisampling"="enabled"
"DirectDrawRenderer"="opengl"
"RenderTargetLockMode"="auto
"StrictDrawOrdering"="disabled"
"OffscreenRenderingMode"="fbo"
"UseGLSL"="enabled"
"VideoMemorySize"="2048"

same error however.

---

### Post by cwwilson721 on 2010-09-23
You don't state it in your posts, but do you have the proprietary drivers installed?

---

### Post by weavil on 2010-09-23
SOLVED

I was using:

ATI Catalyst™ 10.9 Proprietary Linux x86 Display Driver

uninstalled

using 

ATI/AMD proprietary FGLRX graphics driver.
from Hardware Drivers

works fine now... ; /

Could someone to explain to me why?

---

