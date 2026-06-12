---
title: "World of warcraft issues. [with a few fixed ones]"
date: 2009-07-22
forum: Wine
---

### Post by dslreports_snakeoil on 2009-07-22
Running ubuntu 9.04
Wine 1.1.26
Video Card: Nvidia 7600GT.
Server version number: 11.0
Nvidia Driver version:180.44

I am playing this on a 42" 1080P TV


Curse: I was able to get curse working by installing IE8 [IE8 doesn't work, but that is ok].

World of Warcraft: The launcher ran fine, before installing IE8. After IE8, I run the wow launcher and all I see is the launcher art with no news or ads. The play button works how ever and I can log into the game.

In game:
So far the only issue is that my toon's legs stop moving every so often. The npcs/enviroment seem to be fine. Everything else is working fine. The text is a little fuzzy, but ok.

Here is my config.wtf 

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
SET gxRefresh "63"
SET gxMultisample "1"
SET gxMultisampleQuality "0.000000"
SET videoOptionsVersion "2"
SET Gamma "0.700000"
SET lastCharacterIndex "7"
SET accounttype "LK"
SET Sound_OutputDriverName "System Default"
SET Sound_MusicVolume "0.40000000596046"
SET Sound_AmbienceVolume "0.60000002384186"
SET farclip "617"
SET specular "1"
SET groundEffectDensity "24"
SET projectedTextures "1"
SET realmName "Llane"
SET gameTip "5"
SET gxApi "opengl"
SET M2UseShaders "0"
SET mouseSpeed "1"
SET VoiceActivationSensitivity "0.39999997615814"
SET ChatMusicVolume "0.29999998211861"
SET ChatSoundVolume "0.39999997615814"
SET ChatAmbienceVolume "0.29999998211861"
SET accountName *removed to protect the innocent*
SET gxResolution "1280x800"
SET checkAddonVersion "0"


I do have the game set to full screen, so it fills the entire screen.

---

### Post by Rody on 2009-07-22
the legs stoping is a bug in wine i think you can fix it by disabling key repeat. ( system/preferences/keyboard in general tab )

---

### Post by dslreports_snakeoil on 2009-07-23
That worked. not the side effect of that is having to hit backspace or delete several times lol...
But I know the fix for that. Thank you.

I saw this over at wineHQ.

How would I use this? I am new to ubuntu and have no idea about scripts.
#Wow.sh
xset -r 24
xset -r 25
xset -r 26
xset -r 38
xset -r 39
xset -r 40
padsp "/home/xpander/Games/World of Warcraft/Wow.exe" -opengl  <--for example this line would point to the wow.exe which is in my .wine dir?

---

