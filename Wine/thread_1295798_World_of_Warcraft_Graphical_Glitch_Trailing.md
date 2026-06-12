---
title: "World of Warcraft Graphical Glitch: Trailing"
date: 2009-10-19
forum: Wine
---

### Post by Linsolv on 2009-10-19
I'm not a moron. I have OpenGL enabled, I turned off the Full Screen Glow. I've tried switching **back** to d3d, which doesn't show anything.

The graphics are fine for anything that is staying still. However, anything that's MOVING leaves a trail behind it.

I've turned off specular lighting, projected textures, I have the resolution set to my desktop (1280x800; I'm using a laptop).

For a screenshot (about 5 minutes into the loading screen trying to get a proper screenshot, so it looks QUITE a bit worse than it would look normally): [http://i37.tinypic.com/8yzwhs.jpg](http://i37.tinypic.com/8yzwhs.jpg)

You can sort-of see what I mean behind the massive black splotches, in the form of the centipede-looking trail the frost wyrm left. When I alt-tabbed out of the window, that actually looked like dozens of frost wyrms, is the only difference.

While I'm not a moron, and CAN INDEED use Google, I am a Linux newbie, so if there's something that's inherently obvious to longtime Linux users, I could've missed that.

EDIT:
I'm using Wine 1.1.31;

When I run WoW, here's the output. Since I don't know much about what's important, I just copied everything from when WoW opened onward:

```
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
fixme:win:EnumDisplayDevicesW ((null),0,0x3aed4c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x3aeb4c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x3af27c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x3af390,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x3af528,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x3af524,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x3af4a0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x3af490,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x3aefa8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x3af0e0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x3ade8c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x3adeb4,0x00000000), stub!
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 5000
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 5000
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT 5000
fixme:reg:GetNativeSystemInfo (0x37404084) using GetSystemInfo()
fixme:win:EnumDisplayDevicesW ((null),0,0x3ad7fc,0x00000000), stub!
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:win:EnumDisplayDevicesW ((null),0,0x3ad7fc,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x3ad7fc,0x00000000), stub!

```My WINE is set to run Windows XP at the moment.

I'm using an Acer Aspire 5715z. The graphics driver I'm using for my hilariously underpowered computer is xserver-xorg-video-intel, since my lappy apparently uses an Intel GL960 chipset. Computer says it has a 1.7 GHz dual core processor, 160GB HD, 2GB RAM.

My config.wtf:
```
SET readTOS "1"
SET readEULA "1"
SET readScanning "-1"
SET readContest "-1"
SET readTerminationWithoutNotice "-1"
SET installType "Retail"
SET locale "enUS"
SET movie "0"
SET showToolsUI "1"
SET realmList "us.logon.worldofwarcraft.com"
SET patchlist "us.version.worldofwarcraft.com"
SET coresDetected "2"
SET hwDetect "0"
SET gxRefresh "60"
SET gxMultisampleQuality "0.000000"
SET videoOptionsVersion "2"
SET Gamma "1.000000"
SET Sound_OutputDriverName "System Default"
SET Sound_MusicVolume "0.40000000596046"
SET Sound_AmbienceVolume "0.60000002384186"
SET farclip "397"
SET gxAPI "opengl"
SET M2UseShaders "0"
SET lastCharacterIndex "8"
SET accounttype "LK"
SET realmName "Elune"
SET gameTip "6"
SET ffxGlow "0"
SET accountName "****"
SET ffxDeath "0"
SET ffxSpecial "0"
SET Sound_EnableAllSound "0"
SET projectedTextures "1"
SET gxResolution "1280x800"
SET gxFixLag "0"
SET DesktopGamma "1"
SET Sound_EnableSFX "0"
SET Sound_EnableAmbience "0"
SET Sound_EnableMusic "0"
SET Sound_EnableDSPEffects "0"
```EDIT AGAIN: I've downloaded a couple more OpenGL games to see if it might just be my OpenGL drivers. SMC (mario clone) ran fine, foobilliards ran fine. I realize this probably isn't a perfect test, but my internet connection can get spotty at times, and those were what I could conveniently download.

EDIT 3: It also crashes when I venture in through the login and character select screens. My character shifting their weight leaves a somewhat amusing kaleidoscope effect behind them, but I can select the name from the list and hit "enter world." Then it starts loading, shows me Arthas sitting on his throne and stuff, and then loads up to Dal (where I dropped my character off before I went on this Linux adventure) and then poops out a minute or two later. Not that I can see anything in that time. :p

---

### Post by fianor on 2009-10-29
Alright, reached this thread using google, having the same problem. 
Have an acer aspire 4730z laptop.
intel dual core T3200
Intel 4500m graphics
xorg-intel drivers, running the "safe" config from [this thread]("http://ubuntuforums.org/showthread.php?t=1130582")
running jaunty, latest build (28-16)
no problems with sound.
running everything on lowest settings possible.
resolution set at 1024-768, windowed mode. full screen is no better.
running in opengl mode. anything that moves leaves a trail.
d3d mode gives a black screen and a critical error in 5 seconds.

Any prod in the right direction would be greatly appreciated.

Thanks

---

### Post by ArcaVex on 2009-10-30
Might be better off asking on the World of Warcraft forums. (I know windows users have problems with Intel integrated chipsets)

I know this isn't an alternative (due to integrated cards) but a dedicated graphics card would greatly improve the problem, no doubt.


I have no problems with WoW in Wine using an nvidia 9800gt. Straight out of the box it worked. Look slightly... too straight graphics, so i switched to OpenGL, looks fine.

---

### Post by Curifinwe on 2009-10-31
hi had a similar problem with my laptop, i found a guide that told me to delete the open gl ref from my wow config file and then in the wine config to set vertex shader support to none and de-select pixel shader. It's kinda workable now, not perfect but definately playable. hope this helps.

---

### Post by jasonditz on 2009-10-31
Best of luck with it, I had a similar specced machine that I never did get Wow running acceptably on. Those intel graphics are really touchy with wine.

---

