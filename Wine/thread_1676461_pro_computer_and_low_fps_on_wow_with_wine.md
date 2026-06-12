---
title: "pro computer and low fps on wow with wine"
date: 2011-01-27
forum: Wine
---

### Post by dementhor on 2011-01-27
Hello,

I have the following specs :

AMD Phenom II x4 945
ATI Radeon HD5750OC - 1024MB
4 GB RAM
HDD WD CaviarBlack SATA 3 1TB

Kubuntu 10.10 x64, kernel 2.6.37 and latest ati radeon drivers 11.1.

However WoW runs like crap in wine. i get 60fps indoors and 14 or so outdoor. I have set the disabledextensions in wine and have the following .wtf configuration :

[HTML]SET locale "enGB"
SET patchlist "enGB.patch.battle.net:1119/patch"
SET hwDetect "0"
SET gxResolution "1920x1080"
SET gxRefresh "60"
SET gxMultisampleQuality "0.000000"
SET videoOptionsVersion "4"
SET textureFilteringMode "5"
SET playIntroMovie "4"
SET Gamma "1.000000"
SET readTOS "1"
SET readEULA "1"
SET readTerminationWithoutNotice "1"
SET showToolsUI "1"
SET Sound_OutputQuality "2"
SET Sound_NumChannels "64"
SET Sound_EnableReverb "1"
SET Sound_EnableHardware "1"
SET Sound_MusicVolume "0.60000002384186"
SET Sound_AmbienceVolume "0.60000002384186"
SET componentTextureLevel "9"
SET terrainMipLevel "0"
SET farclip "1250"
SET groundEffectDensity "40"
SET groundEffectDist "110"
SET environmentDetail "150"
SET projectedTextures "1"
SET weatherDensity "3"
SET enterWorld "1"
SET mouseSpeed "1.3999999761581"
SET accounttype "CT"
SET ChatMusicVolume "0.29999998211861"
SET ChatSoundVolume "0.39999997615814"
SET ChatAmbienceVolume "0.29999998211861"
SET VoiceActivationSensitivity "0.39999997615814"
SET realmName "Sylvanas"
SET gameTip "74"
SET reflectionMode "0"
SET gxTripleBuffer "1"
SET ffxGlow "0"
SET ffxDeath "0"
SET uiScale "0.79999995231628"
SET useUiScale "1"
SET M2UseShaders "0"
SET processAffinityMask "15"
SET coresDetected "4"
SET questLogCollapseFilter "-1"
SET movieSubtitle "1"
SET shadowLevel "0"
SET specular "1"
SET maxFPS "100"
SET gxWindow "1"
SET Sound_SFXVolume "0.60000002384186"
SET gxMultisample "8"
SET gxApi "OpenGL"[/HTML]

Does anyone have any ideea why this is happening? WoW is installed on a NTFS partition and Wine is X64. I have noticed that on increased HDD activity fps drops, but it's still low in general.

Thank you!

---

### Post by Halzen on 2011-01-27
Couple things you should try out first:

1. Linux doesn't like NTFS, and still won't regardless of whatever workarounds you may have applied. Try moving WoW over to the native Linux partition, or to a shared drive in Ext format.

2. You have 8x multisampling on, and that HURTS. Try turning it down to 2x, or even off completely for debugging purposes.

3. If you have the right Wine overrides on, you can try running WoW in DirectX mode. Be sure to take out the OpenGL line in both your config.wtf and whatever launch command you may be using.

---

### Post by dementhor on 2011-01-27
1. Will do.
2. On Win7 i got all settings maxed and fps will not go below 30 except Ogrimmar(swarm of players). I tried 2x and any other lower settings like distance and whatever, but no improvement. Seems to me that the graphic card is capable and performance is limited by software.
3. I tryed but i can't see all textures, meaning i see all buttons and such but anything else is black except some fires here and there.

---

### Post by dementhor on 2011-02-05
No change in performance with ext4 fs either.

---

### Post by Soulcage on 2011-02-05
I think I've read that disabling GLSL helps with ATI users.
[http://wiki.winehq.org/UsefulRegistryKeys]("http://wiki.winehq.org/UsefulRegistryKeys")

---

### Post by pakau on 2011-10-06
man theres no work around.. linux + wine runs games , but is still buggy... FP's normaly only go between 15-25  FPS ... ( excluding some games. ) wait 2 more years and it will just like windows.

---

