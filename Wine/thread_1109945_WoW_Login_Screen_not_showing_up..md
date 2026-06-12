---
title: "WoW Login Screen not showing up."
date: 2009-03-29
forum: Wine
---

### Post by arapiama on 2009-03-29
So, after I searched through like 10 billion forums searching for help on why I was getting the "Memory Cannot Be Read" error when I opened WoW with OpenGl, it finally stopped crashing. 

However, I still cannot see the login screen. The dragon looks like a bunch of blueish spots, and where there is the Account Name and Password boxes, 
on my screen they are blacked out. Kinda flickers whenever I click.

I tweaked my Config.wtf file...

SET readTOS "1"
SET readEULA "1"
SET readScanning "1"
SET readContest "1"
SET readTerminationWithoutNotice "-1"
SET installType "Retail"
SET gxWindow "1"
SET locale "enUS"
SET movie "0"
SET showToolsUI "1"
SET portal "us"
SET realmList "us.logon.worldofwarcraft.com"
SET patchlist "us.version.worldofwarcraft.com"
SET coresDetected "2"
SET hwDetect "0"
SET gxColorBits "24"
SET gxDepthBits "24"
SET gxResolution "1024x768"
SET gxRefresh "60"
SET gxMultisampleQuality "0.000000"
SET gxFixLag "0"
SET videoOptionsVersion "1"
SET Gamma "1.000000"
SET Sound_OutputDriverName "System Default"
SET Sound_MusicVolume "0.40000000596046"
SET Sound_AmbienceVolume "0.60000002384186"
SET farclip "777.000000"
SET specular "1"
SET particleDensity "1.000000"
SET spellEffectLevel "6"
SET groundEffectDensity "24"

I'm not that knowledgeable using computers...took me like a hour to even find the ******* Config.wtf file. Are there any suggestions on what I may be doing wrong?

I also get this...

sean@sean-laptop:~$ wine "C:\Program Files\World of Warcraft\Wow.exe" -opengl
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
fixme:win:EnumDisplayDevicesW ((null),0,0x39edbc,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39ebe0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f0b8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f434,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f5a0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f59c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f588,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f150,0x00000000), stub!
failed to open C:/Program Files/World of Warcraft/Interface/AddOns
fixme:win:EnumDisplayDevicesW ((null),0,0x39df1c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39df44,0x00000000), stub!
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 5000
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 5000
fixme:reg:GetNativeSystemInfo (0x37402bc4) using GetSystemInfo()
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 5000
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:imm:ImmReleaseContext (0x30028, 0x137860): stub


...if that's any help?

---

### Post by MaximB on 2009-03-29
Post this at the Wine forums.

---

