---
title: "[SOLVED] wow probelem"
date: 2008-07-17
forum: Ubuntu Gamers Arena
---

### Post by trigsenior on 2008-07-17
hello,

I have been having some problems with World of war craft , i have the trial eu version.

this is my grapics card it runs wow just .. 

Intel Corporation 82945G/GZ Integrated Graphics Controller


I would try explaing but a picture is worth a thousand word :)

[http://i281.photobucket.com/albums/kk210/trigsenior/WoWScrnShot_071708_215551.jpg](http://i281.photobucket.com/albums/kk210/trigsenior/WoWScrnShot_071708_215551.jpg)

[http://i281.photobucket.com/albums/kk210/trigsenior/WoWScrnShot_071708_215520.jpg](http://i281.photobucket.com/albums/kk210/trigsenior/WoWScrnShot_071708_215520.jpg)

many many thanxs =)

ps : im using ubuntu hardy

---

### Post by Inxsible on 2008-07-17
> **trigsenior said:**
> ..... but a picture is worth a thousand word :)
 I agree with it....but its only true when someone points out what the hell to look for in the picture.

---

### Post by namegame on 2008-07-17
> **Inxsible said:**
> I agree with it....but its only true when someone points out what the hell to look for in the picture.

The ground isn't showing up correctly.

---

### Post by trigsenior on 2008-07-17
hello,

I recently installed wow the eu trial version the install went fine.
However when the game started the grahics were weird the floor was see through . I have done all the necessary tweaks from here.

[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

here are some screen shots

[http://i281.photobucket.com/albums/kk210/trigsenior/WoWScrnShot_071708_215520.jpg](http://i281.photobucket.com/albums/kk210/trigsenior/WoWScrnShot_071708_215520.jpg)

[http://i281.photobucket.com/albums/kk210/trigsenior/WoWScrnShot_071708_215551.jpg](http://i281.photobucket.com/albums/kk210/trigsenior/WoWScrnShot_071708_215551.jpg)


my grahics card -

Intel Corporation 82945G/GZ Integrated Graphics Controller

ubuntu hardy -

wine version-

wine-1.0

many many thanxs =)

---

### Post by Afkpuz on 2008-07-17
try running it from the command line and adding 
```
-opengl
```

That might not be the right syntax, but there is a command to run wine using opengl.  I had that problem with warcraft 3, but using opengl fixed it.

---

### Post by trigsenior on 2008-07-17
ok thanks for your reply =) 



I ran it in terminal as you said still didnt fix it 

```
 env WINEPREFI env WINEPREFIX="/home/emilien/.wine" wine "C:\World of Warcraft\Launcher.exe"  -opengl
env: WINEPREFI: No such file or directory
emilien@emilien-desktop:~$ env WINEPREFIX="/home/emilien/.wine" wine "C:\World of Warcraft\Launcher.exe"  -opengl
fixme:shdocvw:PersistStreamInit_Load (0x133348)->(0x32e328)
fixme:shdocvw:OleControl_FreezeEvents (0x133348)->(1)
fixme:shdocvw:OleControl_FreezeEvents (0x133348)->(0)
fixme:shell:IShellLinkA_fnGetPath (0x1339a0): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x133980): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x133d20): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x133d20): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x133d20): WIN32_FIND_DATA is not yet filled.
fixme:shell:IShellLinkA_fnGetPath (0x133d20): WIN32_FIND_DATA is not yet filled.
fixme:iphlpapi:NotifyAddrChange (Handle 0x7d88da08, overlapped 0x7d88d9ec): stub
fixme:system:SetProcessDPIAware stub!
fixme:msimtf:CActiveIMM_Create ((nil) {08c0e040-62d1-11d1-9326-0060b067b86e} 0x12eef34)
fixme:ole:CoCreateInstance no instance created for interface {08c0e040-62d1-11d1-9326-0060b067b86e} of class {4955dd33-b159-11d0-8fcf-00aa006bcc59}, hres is 0x80004002
fixme:shdocvw:ClOleCommandTarget_QueryStatus (0x1333e4)->((null) 1 0x32bcf4 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1333e4)->((null) 25 2 0x32bd08 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1333e4)->((null) 26 2 0x32bd08 (nil))
fixme:shdocvw:ClientSite_GetContainer (0x1333e4)->(0x32bd44)
fixme:shdocvw:ClOleCommandTarget_Exec (0x1333e4)->({000214d1-0000-0000-c000-000000000046} 37 0 0x32be08 (nil))
fixme:shdocvw:HttpNegotiate_BeginningTransaction (0x133888)->(L"" L"" 0 0x32be40)
fixme:shdocvw:ClOleCommandTarget_Exec (0x1333e4)->((null) 29 2 0x32ea0c (nil))
fixme:shdocvw:DocHostUIHandler_GetDropTarget (0x1333e4)
fixme:shdocvw:ClientSite_GetContainer (0x1333e4)->(0x32e84c)
fixme:shdocvw:InPlaceFrame_SetStatusText (0x1333e4)->(0xb7e8e6d1)
fixme:shdocvw:ClOleCommandTarget_Exec (0x1333e4)->((null) 25 2 0x32e780 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1333e4)->((null) 26 2 0x32e780 (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1333e4)->((null) 21 2 (nil) (nil))
fixme:shdocvw:ClOleCommandTarget_Exec (0x1333e4)->((null) 28 2 0x32e9ac (nil))
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (10000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 10000
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (10000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 10000
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (10000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 10000
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (10000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 10000
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (10000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 10000
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (10000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 10000
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (10000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 10000
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (10000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 10000
fixme:shdocvw:OleInPlaceObject_InPlaceDeactivate (0x133348)
fixme:mshtml:HlinkTarget_SetBrowseContext (0x14c690)->((nil))
fixme:shdocvw:OleObject_Close (0x133348)->(1)
fixme:shell:DllCanUnloadNow stub
fixme:msimtf:DllCanUnloadNow ()
emilien@emilien-desktop:~$ fixme:advapi:SetSecurityInfo stub
archive Data\patch.MPQ opened
archive Data\enGB\patch-enGB.MPQ opened
archive Data\enGB\patch-enGB-2.MPQ opened
archive Data\patch-2.MPQ opened
archive Data\common.MPQ opened
archive Data\enGB\locale-enGB.MPQ opened
archive Data\enGB\speech-enGB.MPQ opened
fixme:win:EnumDisplayDevicesW ((null),0,0x33eda4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33ec94,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f2c8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f42c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5a8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5a0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f528,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f518,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f000,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f144,0x00000000), stub!
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 5000
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 5000
fixme:reg:GetNativeSystemInfo (0x37402bc4) using GetSystemInfo()
fixme:imm:ImmReleaseContext (0x190074, 0x1378d0): stub
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:winsock:WSAIoctl unsupported WS_IOCTL cmd (9800000c)
fixme:win:EnumDisplayDevicesW ((null),0,0x33d194,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33d200,0x00000000), stub!
fixme:imm:ImmAssociateContextEx (0x190074, (nil), 16): stub



```

here is the config file in wow if it help 

```
SET gxApi "opengl"
SET locale "enGB"
SET realmList "eu.logon.worldofwarcraft.com"
SET patchlist "eu.version.worldofwarcraft.com"
SET coresDetected "2"
SET hwDetect "0"
SET gxColorBits "24"
SET gxDepthBits "24"
SET gxResolution "1024x768"
SET gxRefresh "60"
SET gxMultisampleQuality "0.000000"
SET gxFixLag "0"
SET videoOptionsVersion "1"
SET textureFilteringMode "0"
SET pixelShaders "1"
SET movie "0"
SET readTOS "1"
SET readEULA "1"
SET readTerminationWithoutNotice "1"
SET showToolsUI "1"
SET Sound_OutputDriverName "System Default"
SET SmallCull "0.080000"
SET DistCull "350.000000"
SET farclip "400.000000"
SET specular "1"
SET particleDensity "1.000000"
SET realmName "Lightning's Blade"
SET ffxDeath "0"
SET ffxGlow "0"
SET M2UseShaders "0"
SET Sound_VoiceChatInputDriverName "System Default"
SET Sound_VoiceChatOutputDriverName "System Default"
SET cameraPitchMoveSpeed "90"
SET cameraPitchSmoothSpeed "45"
SET gameTip "2"
```

---

### Post by trigsenior on 2008-07-18
sorry i double posted accidently , i posted it and it didn't seem to come up then i did it again . 

other post -

[http://ubuntuforums.org/showthread.php?t=862591](http://ubuntuforums.org/showthread.php?t=862591)

---

### Post by trigsenior on 2008-07-18
bump

---

### Post by SunnyRabbiera on 2008-07-18
its possible to get WOW working in ubuntu, but check all the issues about it on the forums with the search function...
sometimes getting games like this working in linux can be a pain, but that is because games have microsoft in mind, thats why most dual boot for games.

---

