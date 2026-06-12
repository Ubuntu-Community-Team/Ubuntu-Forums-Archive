---
title: "Window screen goes grey when the window dragged"
date: 2011-06-03
forum: Wine
---

### Post by nandish_punto on 2011-06-03
Hi,

I am running a swing application installed as windows application using wine on Ubuntu 11. The screen freezes when i try to drag the window . The window goes grey and on mouse hover I see some elements in the window. I get the following error at the console 

fixme:exec:SHELL_execute flags ignored: 0x00000100

C:\Program Files\Portal Software\PricingCenter\lib>fixme:win:EnumDisplayDevicesW ((null),0,0x32ac60,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),1,0x32ac60,0x00000000), stub!
fixme:ddraw:DirectDrawEnumerateExA flags 0x00000001 not handled
fixme:d3d_caps:select_card_intel_mesa Card selection not handled for Mesa Intel driver
fixme:d3d_caps:init_driver_info Unhandled vendor 8086.
err:d3d:check_fbo_compat >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from Framebuffer format check @ utils.c / 968
fixme:d3d:check_fbo_compat Format WINED3DFMT_R32_FLOAT with rendertarget flag is not supported as FBO color attachment, and no fallback specified.
err:d3d:check_fbo_compat >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from Framebuffer format check @ utils.c / 968
fixme:d3d:check_fbo_compat Format WINED3DFMT_R32G32_FLOAT with rendertarget flag is not supported as FBO color attachment, and no fallback specified.
err:d3d:check_fbo_compat >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from Framebuffer format check @ utils.c / 968
fixme:d3d:check_fbo_compat Format WINED3DFMT_R16_FLOAT with rendertarget flag is not supported as FBO color attachment, and no fallback specified.
err:d3d:check_fbo_compat >>>>>>>>>>>>>>>>> GL_INVALID_VALUE (0x501) from Framebuffer format check @ utils.c / 968
fixme:d3d:check_fbo_compat Format WINED3DFMT_R16G16_FLOAT with rendertarget flag is not supported as FBO color attachment, and no fallback specified.
fixme:d3d:check_filter Error during filtering test for format 822d, returning no filtering
fixme:d3d:check_filter Error during filtering test for format 822f, returning no filtering
fixme:win:EnumDisplayDevicesW ((null),0,0x33b9d0,0x00000000), stub!
fixme:font:WineEngCreateFontInstance Untranslated charset 255
fixme:imm:ImmGetOpenStatus (0xb0116e0): semi-stub
fixme:imm:NotifyIME IMC_SETCANDIDATEPOS
fixme:imm:ImeHandleNotify WM_IME_NOTIFY:IMN_SETCANDIDATEPOS
fixme:imm:NotifyIME IMC_SETCANDIDATEPOS
fixme:imm:ImeHandleNotify WM_IME_NOTIFY:IMN_SETCANDIDATEPOS
fixme:imm:NotifyIME IMC_SETCANDIDATEPOS
fixme:imm:ImeHandleNotify WM_IME_NOTIFY:IMN_SETCANDIDATEPOS
fixme:imm:NotifyIME IMC_SETCANDIDATEPOS
fixme:imm:ImeHandleNotify WM_IME_NOTIFY:IMN_SETCANDIDATEPOS


Any help much appreciated

Nandish

---

### Post by nandish_punto on 2011-06-03
This is the bug exactly I meant
[http://bugs.winehq.org/show_bug.cgi?id=16358](http://bugs.winehq.org/show_bug.cgi?id=16358)

---

### Post by bobwyajnr on 2011-06-03
Hi **nandish_punto**

Do you have a link for the application? Is it free or does it have a demo/trial? I'll try running it on my systems (with 'real' graphics cards) and see if the problem persists...

Too much for the Intel mesa driver? :popcorn:

Bob

---

### Post by nandish_punto on 2011-06-06
Hey Bob,

Its an internal application.
I will install some other app and see if the problem persists. Will inform you shortly

Regards,
Nandish

---

