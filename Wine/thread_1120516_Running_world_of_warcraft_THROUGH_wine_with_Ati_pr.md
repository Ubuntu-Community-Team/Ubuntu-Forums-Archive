---
title: "Running world of warcraft THROUGH wine with Ati problems."
date: 2009-04-09
forum: Wine
---

### Post by newbmica on 2009-04-09
Hi! this is probably a problem u've guys read about a thousand times, but I'm sorry, I've been troubleshooting for three days now, and I cant seem to find anyone with the same problem as I have.

Wow starts without any problem with wine, I dont get any errors in terminal(will post what the terminal tells me further down), and wow works great, nonlaggy etc until I enter an special area, like a house, town or instance.
Then my wow screen goes all like:

[http://www.pici.se/p/gBoWvpplP/](http://www.pici.se/p/gBoWvpplP/)

I got am running this on an Asus Laptop with the name M51KR-AS032C
With Ati Mobility Radeon HD 3470.

I installed everything from the installation guide found on this forum.
[http://ubuntuforums.org/showthread.php?t=654681](http://ubuntuforums.org/showthread.php?t=654681)

when I type fglrxinfo in terminal I get this message:
```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon HD 3400 Series
OpenGL version string: 2.1.8543 Release
```

and this is my terminal message during the boot of wow, and the second it takes to walk to an inn.
```
sopan@Slashie:~/.wine/drive_c/World of Warcraft$ wine Wow.exe 
fixme:advapi:SetSecurityInfo stub
archive Data\enGB\patch-enGB.MPQ opened
archive Data\patch.MPQ opened
archive Data\enGB\patch-enGB-2.MPQ opened
archive Data\patch-2.MPQ opened
archive Data\expansion.MPQ opened
archive Data\lichking.MPQ opened
archive Data\common.MPQ opened
archive Data\common-2.MPQ opened
archive Data\enGB\locale-enGB.MPQ opened
archive Data\enGB\speech-enGB.MPQ opened
archive Data\enGB\expansion-locale-enGB.MPQ opened
archive Data\enGB\lichking-locale-enGB.MPQ opened
archive Data\enGB\expansion-speech-enGB.MPQ opened
archive Data\enGB\lichking-speech-enGB.MPQ opened
fixme:powrprof:DllMain (0x7c2c0000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:powrprof:DllMain (0x7c2c0000, 0, (nil)) not fully implemented
fixme:win:EnumDisplayDevicesW ((null),0,0x39edbc,0x00000000), stub!
err:wgl:get_render_type_from_fbconfig Unknown render_type: 0
err:wgl:get_render_type_from_fbconfig Unknown render_type: 0
fixme:d3d:IWineD3DImpl_FillGLCaps OpenGL implementation supports 16 vertex samplers and 16 total samplers
fixme:d3d:IWineD3DImpl_FillGLCaps Expected vertex samplers + MAX_TEXTURES(=8) > combined_samplers
fixme:win:EnumDisplayDevicesW ((null),0,0x39ebc8,0x00000000), stub!
err:wgl:X11DRV_wglGetPixelFormatAttribivARB unexpected RenderType(8)
err:wgl:X11DRV_wglGetPixelFormatAttribivARB unexpected RenderType(8)
fixme:d3d:IWineD3DImpl_FillGLCaps OpenGL implementation supports 16 vertex samplers and 16 total samplers
fixme:d3d:IWineD3DImpl_FillGLCaps Expected vertex samplers + MAX_TEXTURES(=8) > combined_samplers
fixme:win:EnumDisplayDevicesW ((null),0,0x39f0a0,0x00000000), stub!
err:wgl:X11DRV_wglGetPixelFormatAttribivARB unexpected RenderType(8)
err:wgl:X11DRV_wglGetPixelFormatAttribivARB unexpected RenderType(8)
fixme:win:EnumDisplayDevicesW ((null),0,0x39f434,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f5a0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f59c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f588,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f150,0x00000000), stub!
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x13f058,0x13ef78): stub
fixme:win:EnumDisplayDevicesW ((null),0,0x39df1c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39df44,0x00000000), stub!
err:wgl:X11DRV_wglGetPixelFormatAttribivARB unexpected RenderType(8)
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 5000
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 5000
fixme:reg:GetNativeSystemInfo (0x37404084) using GetSystemInfo()
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:imm:ImmReleaseContext (0x30028, 0x138e38): stub
fixme:winsock:WSAIoctl unsupported WS_IOCTL cmd (9800000c)
fixme:win:EnumDisplayDevicesW ((null),0,0x39dae4,0x00000000), stub!
err:ntdll:RtlpWaitForCriticalSection section 0x67c0104 "?" wait timed out in thread 0021, blocked by 0009, retrying (60 sec)
```

I might add I use Wine-1.1.18.

Anyone have a simular problem or know how to fix this? I've never considered myself an addict until now, when I cant play :]

and again, I am sorry if this has been posten a thousand times, it's just that I cant find it anywhere, not even on google.
ty for your patient and that you've read this far.

I hope you can help me!
Mica

---

### Post by hikaricore on 2009-04-09
Could be the age old minimap bug.
It's a common issue with ATI cards.

Search around for a "minimap auto hide" mod if I recall, I can't find it but I imagine its' still around somewhere.

Not saying this is it for sure bu it's worth thinking about.  Also be sure you have the very latest version of the drivers for you card installed.

---

### Post by newbmica on 2009-04-09
it is worth trying, googling as a maniac for it now ^^ ty, I will tell when I find it if it works.

Edit: it worked just by just minimizing the minimap without any addons... didnt believe it would be this simple, I think I love you ^^ thanks

---

### Post by hikaricore on 2009-04-09
lol i love you too, in a totally platonic way of course...  :p

just glad to help

---

### Post by amritmatharu on 2009-04-09
Yeah, try turning off your mini-map before you enter a city. I used to have this problem, but for some reason, it doesn't go crazy anymore :|

---

