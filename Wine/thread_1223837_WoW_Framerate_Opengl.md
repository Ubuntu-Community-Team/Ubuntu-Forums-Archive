---
title: "WoW Framerate Opengl"
date: 2009-07-26
forum: Wine
---

### Post by alexj777 on 2009-07-26
1

---

### Post by Rocket2DMn on 2009-07-26
Moved to the Wine forum area.

---

### Post by OrbJinzo on 2009-07-26
whats your config.wtf look like? Also are you running the lastest fglrx drivers?

---

### Post by alexj777 on 2009-07-27
I'm running the latest ATi drivers installed from their site (the ones that aren't supported nor recommended). 

SET locale "enUS"
SET realmList "us.logon.worldofwarcraft.com"
SET patchlist "us.version.worldofwarcraft.com"
SET coresDetected "3"
SET processAffinityMask "3"
SET hwDetect "0"
SET gxRefresh "60"
SET gxMultisampleQuality "0.000000"
SET gxFixLag "0"
SET videoOptionsVersion "2"
SET movie "0"
SET expansionMovie "0"
SET Gamma "1.500000"
SET showToolsUI "1"
SET Sound_OutputDriverName "System Default"
SET Sound_MusicVolume "0.40000000596046"
SET Sound_AmbienceVolume "0.60000002384186"
SET farclip "1277"
SET SoundOUtputSystem "1"
SET SoundBufferSize "150"
SET mouseSpeed "1"
SET readTOS "1"
SET readEULA "1"
SET accounttype "CL"
SET VoiceActivationSensitivity "0.39999997615814"
SET ChatMusicVolume "0.29999998211861"
SET ChatSoundVolume "0.39999997615814"
SET ChatAmbienceVolume "0.29999998211861"
SET realmName "Kel'Thuzad"
SET gameTip "27"
SET gxResolution "1360x768"
SET textureFilteringMode "5"
SET particleDensity "1"
SET environmentDetail "1.5"
SET weatherDensity "3"
SET componentTextureLevel "9"
SET shadowLevel "0"
SET groundEffectDensity "64"
SET groundEffectDist "140"
SET accountName "alexj777"
SET ffxGlow "0"
SET gxApi "opengl"
SET ffxDeath "0"
SET UIFaster "2"

---

### Post by NightMKoder on 2009-07-27
You could try offscreenrenderingmode = pbuffer (google it), as ati drivers suck. Other than that - complain to ATI.

---

### Post by dslreports_snakeoil on 2009-07-27
I have 2 boxes:

Linux: 20 to 35 FPS. Graphic details ultra.
Windows Vista: 30 to 60 FPS. Details at high.

---

### Post by sackbj on 2009-07-27
Wouldn't it make more sense to compare boxes with both set at the same detail level?  20 to 35 at Ultra seems like it might jump up to 30 to 60 at high.

---

### Post by lestatius on 2009-07-28
I had the same problem, I then found this article. I have the  4890HD Radeon myself. Works perfectly fine now.


[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

---

