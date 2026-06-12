---
title: "WoW + Wine on Macbook"
date: 2009-07-11
forum: Wine
---

### Post by ShiChelle on 2009-07-11
I recently installed Ubuntu 8.10 on my Macbook (4,1 with all the default hardware). I've been trying to get WoW running under Wine and I managed to get to the character selection screen (the login screen menus are all buggy). However, towards the end of loading, the loading picture (WotLK because I probably logged off in Dalaran) disappears and only the loading bar is visible. A moment or two passes and the whole thing crashes. I might note that I'm running WoW using DirectX, NOT OpenGL like many other people because of the hardware on my laptop (simply, it will not run at all using opengl and does a rather nasty crash when I try to get the login screen up).

I tried a combination of things on [https://help.ubuntu.com/community/WorldofWarcraft/Troubleshooting](https://help.ubuntu.com/community/WorldofWarcraft/Troubleshooting) this troubleshooting page, but so far I can't get the whole thing running (I did the first fix for Intel drivers and that helped me get closer to playing the game; the "ATI enter game world crash" fix does not work because I don't have an ATI video card, but that is the problem I'm having).

Any suggestions for me to try to get WoW working again or should I not bother and resize my OS X partition and download the Mac version? :/

---

### Post by Vakman on 2009-07-12
Do you have your graphic driver installed? If yes, then have you tried to emulate a virtual desktop for WoW under winecfg? Also ensure you are using the newest version of Wine, currently 1.1.24. To check if you have the newest version of Wine open a terminal and type ```
wine --version
```
Let us know.

---

### Post by ShiChelle on 2009-07-12
Yes, I have the latest version of Wine installed. Also, I tried the emulate virtual desktop option. The game loads and I can play now, but my graphics are HORRIBLY messed up. I'd post a screenshot, but apparently Fn+Shift+F11 for print screen does not work in Linux... Oh, and I had to click the WoW screen away after trying to exit the game, but at least it didn't crash.

EDIT: New problem: The login screen isn't recognising my keystrokes anymore, so I can't even log in now! D:

---

### Post by ShiChelle on 2009-07-13
Bump for unresolved issues. <.<

 By the way, this is what displays when I try to run WoW from the terminal:

```
fixme:advapi:SetSecurityInfo stub
archive Data\enUS\patch-enUS.MPQ opened
archive Data\patch.MPQ opened
archive Data\enUS\patch-enUS-2.MPQ opened
archive Data\patch-2.MPQ opened
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
fixme:win:EnumDisplayDevicesW ((null),0,0x39edac,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39ebc4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f3f0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f588,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f584,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f578,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f5d0,0x00000000), stub!
err:d3d:CreateContext Requesting MultiSampleType=4
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
err:d3d:WineD3D_ChoosePixelFormat Can't find a suitable iPixelFormat
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0x1426b8) Event query: Unimplemented, but pretending to be supported
fixme:win:EnumDisplayDevicesW ((null),0,0x39f140,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39deec,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39df24,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39ded4,0x00000000), stub!
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 5000
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 5000
fixme:reg:GetNativeSystemInfo (0x374040a4) using GetSystemInfo()
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
```

---

### Post by ThisEndlessFall on 2009-07-13
If you have a Macbook then why don't you just use the native OSX WoW client? 

Or did you completely remove OSX?

---

### Post by ShiChelle on 2009-07-13
> **ThisEndlessFall said:**
> If you have a Macbook then why don't you just use the native OSX WoW client? 

Or did you completely remove OSX?
I said in my first post "Any suggestions for me to try to get WoW working again or should I not bother and resize my OS X partition and download the Mac version? :/" I'd rather run WoW in Ubuntu if I can seeing as I do everything else on it. I don't really use OS X, but I keep it there with minimum space allocated to it as a back-up.

---

