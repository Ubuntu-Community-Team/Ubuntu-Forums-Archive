---
title: "WoW Wotlk - Wine - Intel Graphics - glitches...."
date: 2008-12-02
forum: Wine
---

### Post by scheuri on 2008-12-02
Hi all

**Information:**
I own a Lenovo X200 with Intel 4500 graphics integrated.
I am using Ubuntu 8.10, Wine 1.1.9, Intel-Driver 2.4.1, Mesa-Driver 7.2, used winetricks and aptitude to install mstcorefonst...
I also used the regedit-trick for WoW/WINE.

dpkg -l
```
ii  xserver-xorg-video-intel                  2:2.4.1-1ubuntu10
ii  libgl1-mesa-dri          7.2-1ubuntu2                            
ii  libgl1-mesa-glx          7.2-1ubuntu2                                
ii  libglu1-mesa             7.2-1ubuntu2             
ii  mesa-utils               7.2-1ubuntu2
```  

lspci (part of it)
```
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
```

glxinfo and glxgears (part of it)
```

OpenGL vendor string: Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Mobile Intel® GM45 Express Chipset 20061102 x86/MMX/SSE2
OpenGL version string: 1.4 Mesa 7.2

3666 frames in 5.0 seconds = 733.096 FPS
3917 frames in 5.0 seconds = 783.260 FPS
3702 frames in 5.0 seconds = 740.303 FPS

```



My WTF/Config.wtf
```
SET readTOS "1"
SET readEULA "1"
SET readScanning "1"
SET readContest "-1"
SET locale "deDE"
SET hwDetect "0"
SET gxColorBits "24"
SET gxDepthBits "24"
SET gxResolution "1280x800"
SET gxRefresh "60"
SET gxMultisampleQuality "0.000000"
SET gxFixLag "0"
SET fullAlpha "1"
SET doodadAnim "0"
SET SmallCull "0.040000"
SET DistCull "500.000000"
SET trilinear "1"
SET frillDensity "24"
SET farclip "177"
SET specular "1"
SET pixelShaders "0"
SET particleDensity "1.000000"
SET unitDrawDist "300.000000"
SET movie "0"
SET realmList "eu.logon.worldofwarcraft.com"
SET gxApi "opengl"
SET ffxDeath "0"
SET ffxGlow "0"
SET SoundOutputSystem "1"
SET SoundBufferSize "150"
SET readTerminationWithoutNotice "1"
SET coresDetected "2"
SET gxWindow "1"
SET videoOptionsVersion "1"
SET Gamma "1.000000"
SET showToolsUI "1"
SET Sound_VoiceChatInputDriverName "Systemstandard"
SET Sound_VoiceChatOutputDriverName "Systemstandard"
SET Sound_OutputDriverName "System Default"
SET Sound_MasterVolume "1"
SET Sound_SFXVolume "0.10000000149012"
SET Sound_MusicVolume "0.30000001192093"
SET Sound_AmbienceVolume "0.20000000298023"
SET patchlist "eu.version.worldofwarcraft.com"
SET gameTip "21"
SET uiScale "1"
SET mouseSpeed "0.5"
SET ChatMusicVolume "0.29999998211861"
SET ChatSoundVolume "0.39999997615814"
SET ChatAmbienceVolume "0.29999998211861"
SET Sound_EnableMusic "0"
SET OutboundChatVolume "1"
SET InboundChatVolume "1"
SET VoiceActivationSensitivity "0.39999997615814"
SET showPartyDebuffs "0"
SET installType "Retail"
SET portal "eu"
SET textureFilteringMode "0"
SET Sound_OutputQuality "0"
SET Sound_EnableAmbience "0"
SET Sound_EnableDSPEffects "0"
SET baseMip "1"
SET environmentDetail "0.5"
SET weatherDensity "0"
SET M2UseShaders "0"
SET fixedFunction "1"
```
That one works fine on my other machine, which actually uses a nvidia-card.

**Problem:**
I can log in and I have stuttery sound...that is not much of an issue, but graphics are bad...so far "only" the action bars, the minimap and occassionally the pic of my char...
They seem out of line like a bad screen on TV.
See the attachments....
And I can not see text (no help text, no chat, no quest text, etc.)

Does anyone have an idea what I might do to make it work?

Cheers
scheuri

---

### Post by seals77 on 2009-01-11
):P hi, i have this same problem, i have intel integrated graphic card too.
In glxgears - fps +- 900 an i have installed mesa driver. 
When i run WoW in max. details have got small FPS (edited Config.wtf and I have change in registry) and graphic is very bad 
If i run it in min. details i have better fps, bud bad graphic too...


sorry for my english

---

### Post by Eviljim on 2009-01-11
Unfortunatley the Intel graphics cards are a bit hit and miss. Some work ok, yet others dont. There arent any propietery drivers from intel either.

Dont think there is a great deal you can really do on this issue.

---

