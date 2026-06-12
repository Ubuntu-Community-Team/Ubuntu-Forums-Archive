---
title: "Ghosbusters+Wine"
date: 2010-06-26
forum: Wine
---

### Post by Tumpster on 2010-06-26
Just bought the game Ghostbusters and I see it runs fine on Wine under the 1.35 edition but I'm getting an error on it. This is the error I read: 
Msg: Texture 'ui\font_calibri.tga' was selected for rendering without being cached
File: texture.cpp
Line: 3793
Time: Tue Jul 14 22:05:24 2009
User: Eric
Computer: ERIC
Source code revision: 2009/05/26 15:39:43 (92949)

Now I've perused the Atari forums but nothing seems to work so far. Thought I'd put it out there to see if anyone can help me crack this one, looking forward to giving it a shot. 

Specs:
AMD Phenom 2 X4 955
4GB DDR3 1600 Ram
MSI NF980-G65
Nvidia 9800GTX+ OC'd

Any ideas?

---

### Post by cogadh on 2010-06-26
What does Wine say about the error? Run the game from the terminal to get Wine's error output.

---

### Post by Tumpster on 2010-06-29
> **cogadh said:**
> What does Wine say about the error? Run the game from the terminal to get Wine's error output.

It's not wine having the error, its that code I'm getting that it then hits back to the desktop.

---

### Post by cogadh on 2010-06-29
Actually it is Wine having the error, otherwise the game would keep working without producing any error codes. The message you got is what the game would have reported to Windows, but it is not what Wine would "say" about the error, so it is virtually meaningless from a troubleshooting perspective. When you run Wine from the terminal, it produces its own error output that may explain what happened from Wine's perspective, which is far more meaningful in this situation.

---

### Post by Tumpster on 2010-07-01
```
err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
fixme:win:EnumDisplayDevicesW ((null),0,0x32cc68,0x00000000), stub!
fixme:dwmapi:DwmSetWindowAttribute (0x300a2, 2, 0x32d574, 4) stub
fixme:dwmapi:DwmSetWindowAttribute (0x300a2, 3, 0x32d570, 4) stub
fixme:dwmapi:DwmSetWindowAttribute (0x300a2, 4, 0x32d56c, 4) stub
err:ole:RevokeDragDrop invalid hwnd (nil)
err:ole:RevokeDragDrop invalid hwnd 0x1011a
err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
fixme:win:EnumDisplayDevicesW ((null),0,0x33eba4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33e238,0x00000000), stub!
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found 1440x900x32 @60! (XRandR)
fixme:d3d:swapchain_init Add OpenGL context recreation support to context_validate_onscreen_formats
fixme:d3d:state_lastpixel Last Pixel Drawing Disabled, not handled yet
err:mmdevapi:AudioClient_Destroy >>>>>>>>>>>> Received AL error 0xa001 on context 0x7c842400, AudioClient_Destroy:334
AL lib: ALc.c:1798: alcCloseDevice(): destroying 1 Context(s)

```

Thats what I get.

---

### Post by Tumpster on 2010-07-02
Anyone?

---

