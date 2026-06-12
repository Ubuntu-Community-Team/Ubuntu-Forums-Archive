---
title: "Blank windows when running install shield"
date: 2009-02-28
forum: Wine
---

### Post by hotweiss on 2009-02-28
I am trying to install UpToDate with no avail. I keep on getting these blank install windows:

[IMG]http://img527.imageshack.us/img527/3209/screenshotzxl.png[/IMG]

When I hover my mouse over certain areas of the window my cursor changes to a text box cursor and I can tab to exit the window.

I am using Wine 1.1.16

I get one of these two error messages in Terminal:

> fixme:msvcrt:MSVCRT__wsopen : pmode 0x01b6 ignored
fixme:msvcrt:MSVCRT__wsopen : pmode 0x01b6 ignored
fixme:msvcrt:MSVCRT__wsopen : pmode 0x01b6 ignored
fixme:msvcrt:MSVCRT__wsopen : pmode 0x01b6 ignored
fixme:msvcrt:MSVCRT__wsopen : pmode 0x01b6 ignored
fixme:font:WineEngAddFontResourceEx Ignoring flags 10
fixme:font:WineEngAddFontResourceEx Ignoring flags 10
fixme:font:WineEngAddFontResourceEx Ignoring flags 10
fixme:font:WineEngAddFontResourceEx Ignoring flags 10
fixme:font:WineEngAddFontResourceEx Ignoring flags 10
fixme:font:WineEngAddFontResourceEx Ignoring flags 10
fixme:font:WineEngAddFontResourceEx Ignoring flags 10
fixme:font:WineEngAddFontResourceEx Ignoring flags 10
fixme:win:EnumDisplayDevicesW ((null),0,0x7cec4734,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),1,0x7cec4734,0x00000000), stub!
fixme:d3d:IWineD3DImpl_FillGLCaps OpenGL implementation supports 32 vertex samplers and 32 total samplers
fixme:d3d:IWineD3DImpl_FillGLCaps Expected vertex samplers + MAX_TEXTURES(=8) > combined_samplers
fixme:win:EnumDisplayDevicesW ((null),0,0x7cec41b8,0x00000000), stub!
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:font:WineEngCreateFontInstance Untranslated charset 255
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:imm:ImmGetOpenStatus (0x291b8d0): semi-stub
fixme:imm:ImeHandleNotify WM_IME_NOTIFY:IMN_SETCOMPOSITIONWINDOW

> fixme:msvcrt:MSVCRT__wsopen : pmode 0x01b6 ignored
fixme:msvcrt:MSVCRT__wsopen : pmode 0x01b6 ignored
fixme:msvcrt:MSVCRT__wsopen : pmode 0x01b6 ignored
fixme:msvcrt:MSVCRT__wsopen : pmode 0x01b6 ignored
fixme:msvcrt:MSVCRT__wsopen : pmode 0x01b6 ignored
fixme:font:WineEngAddFontResourceEx Ignoring flags 10
fixme:font:WineEngAddFontResourceEx Ignoring flags 10
fixme:font:WineEngAddFontResourceEx Ignoring flags 10
fixme:font:WineEngAddFontResourceEx Ignoring flags 10
fixme:font:WineEngAddFontResourceEx Ignoring flags 10
fixme:font:WineEngAddFontResourceEx Ignoring flags 10
fixme:font:WineEngAddFontResourceEx Ignoring flags 10
fixme:font:WineEngAddFontResourceEx Ignoring flags 10
fixme:win:EnumDisplayDevicesW ((null),0,0x7cec1734,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),1,0x7cec1734,0x00000000), stub!
fixme:d3d:IWineD3DImpl_FillGLCaps OpenGL implementation supports 32 vertex samplers and 32 total samplers
fixme:d3d:IWineD3DImpl_FillGLCaps Expected vertex samplers + MAX_TEXTURES(=8) > combined_samplers
fixme:win:EnumDisplayDevicesW ((null),0,0x7cec11b8,0x00000000), stub!
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:font:WineEngCreateFontInstance Untranslated charset 255
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:CreateContext Cannot activate context to set up defaults
err:d3d:IWineD3DSwapChainImpl_CreateContextForThread Failed to create a new context for the swapchain
err:dbghelp:pe_load_dbg_file Couldn't find .DBG file "COMCTL32.dbg" ("P")
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:wgl:internal_SetPixelFormat Invalid operation on root_window
err:d3d:CreateContext SetPixelFormat failed on HDC=0x1d0 for iPixelFormat=3
err:d3d:IWineD3DSwapChainImpl_CreateContextForThread Failed to create a new context for the swapchain
err:ole:CoUninitialize Mismatched CoUninitialize


---

### Post by amauk on 2009-02-28
you can try using the wine config tool to enable desktop emulation
this often corrects display issues with windows apps

open up a terminal, and type
```
winecfg
```
under the "graphics" tab, enable the virtual desktop
pick suitable dimensions for your screen resolution

---

### Post by hotweiss on 2009-02-28
> **amauk said:**
> you can try using the wine config tool to enable desktop emulation
this often corrects display issues with windows apps

open up a terminal, and type
```
winecfg
```
under the "graphics" tab, enable the virtual desktop
pick suitable dimensions for your screen resolution

Turning on Virtual Desktop has done nothing...

PS-with wine 1.1.16 the virtual desktop does not have it's own background...

---

### Post by KhaaL on 2009-03-02
is this affected by wether or not compiz is running?

---

### Post by hotweiss on 2009-03-02
> **KhaaL said:**
> is this affected by wether or not compiz is running?

No, turning off compiz does nothing...

---

