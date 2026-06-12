---
title: "WoW doesn't run at all"
date: 2009-07-25
forum: Wine
---

### Post by ministoat on 2009-07-25
I know i'm fighting a losing battle since i'm on jaunty with an unsupported chipset - radeon xpress 1250.

All that I really want to be able to do is log on to check auctions etc, i'm not bothered about raiding on this system - it's my laptop.

So I am able to run the launcher occasionally, and this displays fine.

Once or twice I have been able to run the game directly from wow.exe but there is severe graphical corruption, and most of the time the game does not run at all. 

I'm using ubuntu 9.04, x64 and the latest version of wine, and the graphics driver that comes with the kernel; glxgears gets me ~480 fps.

WTF file is:
SET locale "enGB"
SET portal "eu"
SET realmList "eu.logon.worldofwarcraft.com"
SET patchlist "eu.version.worldofwarcraft.com"
SET coresDetected "2"
SET hwDetect "0"
SET gxRefresh "60"
SET gxMultisampleQuality "0.000000"
SET gxFixLag "0"
SET videoOptionsVersion "2"
SET movie "0"
SET Gamma "1.000000"
SET showToolsUI "1"
SET Sound_OutputDriverName "System Default"
SET Sound_MusicVolume "0.40000000596046"
SET Sound_AmbienceVolume "0.60000002384186"
SET farclip "507"
SET specular "1"
SET particleDensity "0.69999998807907"
SET groundEffectDensity "24"
SET projectedTextures "1"
SET gxResolution "1280x800"
SET SoundOutputSystem "1"
SET SoundBufferSize "150"
SET mouseSpeed "1"
SET lastCharacterIndex "3"
SET readTOS "1"
SET readEULA "1"
SET readTerminationWithoutNotice "1"
SET accounttype "LK"
SET VoiceActivationSensitivity "0.39999997615814"
SET ChatMusicVolume "0.29999998211861"
SET ChatSoundVolume "0.39999997615814"
SET ChatAmbienceVolume "0.29999998211861"
SET realmName "thelandofhardship"
SET gameTip "3"
SET UIFaster "2"
SET accountName "isnothereduh"
SET checkAddonVersion "0"
SET uiScale "0.79999995231628"
SET useUiScale "1"
SET gxApi "opengl"
SET ffxDeath "0"
SET ffxGlow "0"
SET ffxSpecial "0"

---

### Post by NightMKoder on 2009-07-25
ATI with open source drivers? you have a deathwish don't you.

Install official ATI drivers: [http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)

If all works you're in luck; if not, set offscreenrenderingmode = backbuffer.

---

### Post by ministoat on 2009-07-25
I would if i could ;)

radeon xpress 1250 is not supported for the x server 1.6 which comes with 9.04..like i say, it's just for a quick log on/off really.

---

### Post by NightMKoder on 2009-07-25
Ah did not know that. Sorry.

You can risk it all and try karmic (newer mesa drivers) or just try installing mesa from karmic on jaunty. Either way, without an upgrade of mesa or catalyst drivers you're probably not going to get it to work.

For starters, try offscreenrenderingmode=backbuffer.

EDIT: also try UseGLSL=false. And turn down the graphics settings in wow (through config.wtf)

---

