---
title: "Wine 1.1.23 Ubuntu 9.0.4 World of Warcraft Squished"
date: 2009-06-20
forum: Wine
---

### Post by Pantalaimon on 2009-06-20
Fixed :: I edited the config.wtf file's resolution value. Set it to my main monitor's current resolution and it worked.
Though I did have to open it from the terminal.



Alright.

So I got WoW working today. Kinda.
It works, but its got a slight problem.

The screen looks squished. its possible the aspect ratio is off, but I'm not sure.
I have switched between the only two available video resolutions, and they change absolutely nothing.

Essentially, the lag isn't bad. Its just that it looks squished.

Wine 1.1.23
Ubuntu 9.0.4
NVidia GeForce 6200 graphics card (Thats what XServer tells me)

No. I haven't run this from the terminal. I haven't a clue how. (Total Linux newbie)

For the record, WoW is installed under.
/media/disk/Program Files/World Of Warcraft

I have created a config.wtf file in the WTF directory.

```

SET gxApi "opengl"
SET locale "enUS"
SET realmList "us.logon.worldofwarcraft.com"
SET patchlist "us.version.worldofwarcraft.com"
SET coresDetected "1"
SET hwDetect "0"
SET gxResolution "2960x1050"
SET gxRefresh "50"
SET gxMultisampleQuality "0.000000"
SET gxFixLag "0"
SET videoOptionsVersion "2"
SET movie "0"
SET expansionMovie "0"
SET Gamma "1.000000"
SET readTOS "1"
SET readEULA "1"
SET showToolsUI "1"
SET Sound_OutputDriverName "System Default"
SET Sound_MusicVolume "0.40000000596046"
SET Sound_AmbienceVolume "0.60000002384186"
SET farclip "727"
SET specular "1"
SET groundEffectDensity "24"
SET projectedTextures "1"
SET lastCharacterIndex "3"
SET accounttype "BC"
SET realmName "Deathwing"
SET gameTip "1"

```Although, honestly I only put the SET gxApi "opengl" line in there.
So I'd assume that the rest is automatic.

Help?

So, I also included a screen capture of the login page.
It shows the basic problem.
[http://img.photobucket.com/albums/v207/Zlord/Screenshot.png](http://img.photobucket.com/albums/v207/Zlord/Screenshot.png)
Also a cap of the in game. Complete with screwy video menu
[http://img.photobucket.com/albums/v207/Zlord/Screenshot-1.png](http://img.photobucket.com/albums/v207/Zlord/Screenshot-1.png)

---

### Post by Pantalaimon on 2009-06-20
Figured out how to run it from the terminal.

Here's everything.

```

pantalaimon@ryan-desktop:~$ wine "/media/disk/Program Files/World of Warcraft/Wow.exe" -opengl
fixme:advapi:SetSecurityInfo stub
archive Data\enUS\patch-enUS.MPQ opened
archive Data\patch.MPQ opened
archive Data\enUS\patch-enUS-2.MPQ opened
archive Data\patch-2.MPQ opened
archive Data\expansion.MPQ opened
archive Data\common.MPQ opened
archive Data\common-2.MPQ opened
archive Data\enUS\locale-enUS.MPQ opened
archive Data\enUS\speech-enUS.MPQ opened
archive Data\enUS\expansion-locale-enUS.MPQ opened
archive Data\enUS\expansion-speech-enUS.MPQ opened
fixme:win:EnumDisplayDevicesW ((null),0,0x39edac,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39ebd0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f0a8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f2dc,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f3f0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f588,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f584,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f510,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f500,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f008,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39f140,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39deec,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x39df24,0x00000000), stub!
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 5000
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 5000
fixme:reg:GetNativeSystemInfo (0x374040a4) using GetSystemInfo()
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:imm:ImmReleaseContext (0x30030, 0x13f678): stub
fixme:win:EnumDisplayDevicesW ((null),0,0x39dae4,0x00000000), stub!
failed to open Z:/media/disk/Program Files/World of Warcraft/Data/Interface/Icons
failed to open Z:/media/disk/Program Files/World of Warcraft/Interface/Icons
pantalaimon@ryan-desktop:~$ 

```

---

### Post by NightMKoder on 2009-06-20
Twinview is a problem I think. Try disabling your dual monitor setup and see if it helps.

If it does, there was a guide to getting games working with a dual monitor setup by starting a new x server.

---

