---
title: "WoW terminal output"
date: 2009-01-07
forum: Wine
---

### Post by EnderEcho on 2009-01-07
Intrepid on a intel 4500HD. Been working on getting WoW up and running for a little while. The graphics get all jumbled after launcher.

Crashes when I run in D3D mode. How can I get output after system reboots?

When I run on Opengl mode this is what I get:

ender@ubuntu:~$ wine "C:\Program Files\World of Warcraft\WoW.exe" 
fixme:advapi:SetSecurityInfo stub 
archive Data\enUS\patch-enUS.MPQ opened 
archive Data\patch.MPQ opened 
archive Data\expansion.MPQ opened 
archive Data\common.MPQ opened 
archive Data\common-2.MPQ opened 
archive Data\enUS\locale-enUS.MPQ opened 
archive Data\enUS\speech-enUS.MPQ opened 
archive Data\enUS\expansion-locale-enUS.MPQ opened 
archive Data\enUS\expansion-speech-enUS.MPQ opened 
fixme:win:EnumDisplayDevicesW ((null),0,0x39edbc,0x00000000), stub! 
fixme:win:EnumDisplayDevicesW ((null),0,0x39ebe0,0x00000000), stub! 
fixme:win:EnumDisplayDevicesW ((null),0,0x39f2d8,0x00000000), stub! 
fixme:win:EnumDisplayDevicesW ((null),0,0x39f434,0x00000000), stub! 
fixme:win:EnumDisplayDevicesW ((null),0,0x39f5a0,0x00000000), stub! 
fixme:win:EnumDisplayDevicesW ((null),0,0x39f59c,0x00000000), stub! 
fixme:win:EnumDisplayDevicesW ((null),0,0x39f530,0x00000000), stub! 
fixme:win:EnumDisplayDevicesW ((null),0,0x39f520,0x00000000), stub! 
fixme:win:EnumDisplayDevicesW ((null),0,0x39f018,0x00000000), stub! 
fixme:win:EnumDisplayDevicesW ((null),0,0x39f150,0x00000000), stub! 
failed to open C:/Program Files/World of Warcraft/Interface/AddOns 
fixme:win:EnumDisplayDevicesW ((null),0,0x39df1c,0x00000000), stub! 
fixme:win:EnumDisplayDevicesW ((null),0,0x39df44,0x00000000), stub! 
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB 
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 5000 
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB 
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 5000 
fixme:reg:GetNativeSystemInfo (0x374026a4) using GetSystemInfo() 
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB 
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB 
fixme:imm:ImmReleaseContext (0x20028, 0x13c8d0): stub 
ender@ubuntu:~$ 


Running it in a virtual desktop. With all the Config.wtf tips from the WoW wiki.

Any help would be greatly appreciated. This has been taking me quite a while.

---

### Post by EnderEcho on 2009-01-14
Im running it effectively in D3D mode. Im running wine in windows 98 mode with pixel shader turned off. 

Anyone know how i can get more FPS?

---

