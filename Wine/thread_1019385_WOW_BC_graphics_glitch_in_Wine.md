---
title: "WOW BC graphics glitch in Wine"
date: 2008-12-23
forum: Wine
---

### Post by rehaby on 2008-12-23
I get this strange graphic glitch on the login page of World of WArcraft with Burning Crusade when running for the first time. WOW is fully patched and running in the latest stable release of wine.

Anyone can help?

---

### Post by rehaby on 2008-12-23
ok so after a bit of work i managed to get the screen looking like this:

anyone have any further advice?

---

### Post by Espionage724 on 2008-12-26
Same issue here although its with WotLK.

My idea:

WoW (since 3.0.2) uses a new shader effect for shadows. So I assume that shader is messing with WoW and Wine and...yea

---

### Post by seals77 on 2009-02-19
hi, I have this same problem with wow wotlk:


**my system specs**:[U] intel core duo 2.0 GHz 
                 Chipset Intel® G31 Express
                 2 GB of RAM
                 Intel® Graphics Media Accelerator X3100 [/U]

**direct rendering: Yes**
Config.wtf 

[I]
SET ffxGlow "0"
SET gxColorBits "24"
SET gxDepthBits "24"
SET gxResolution "800x600"
SET hwDetect "0"
SET lodDist "100.000000"
SET SmallCull "0.070000"
SET DistCull "350.000000"
SET frillDensity "8"
SET farclip "177"
SET particleDensity "1.000000"
SET realmList "kitakami-2.jyxo.com"
SET readTOS "1"
SET readEULA "1"
SET readScanning "-1"
SET readContest "-1"
SET locale "enUS"
SET gxMultisampleQuality "0.000000"
SET movie "0"
SET M2UseShaders "0"
SET SoundOutputSystem "1"
SET SoundBufferSize "200"
SET readTerminationWithoutNotice "-1"
SET patchlist "us.version.worldofwarcraft.com"
SET coresDetected "2"
SET videoOptionsVersion "1"
SET showToolsUI "1"
SET UIFaster "2"
SET Sound_OutputDriverName "System Default"
SET gxCursor "0"
SET Gamma "1.000000"
SET Sound_VoiceChatInputDriverName "System Default"
SET Sound_VoiceChatOutputDriverName "System Default"
SET gameTip "91"
SET uiScale "1"
SET groundEffectDist "70"
SET DesktopGamma "1"
SET weatherDensity "0"
SET shadowLOD "0"
SET shadowLevel "0"
SET ffxDeath "0"
SET gxFixLag "0"
SET textureFilteringMode "0"
SET rwrw "data3535"
SET Sound_OutputQuality "2"
SET ChatMusicVolume "0.30000001192093"
SET ChatSoundVolume "0.40000000596046"
SET ChatAmbienceVolume "0.30000001192093"
SET Sound_MasterVolume "1"
SET Sound_SFXVolume "1"
SET Sound_MusicVolume "0.40000000596046"
SET Sound_AmbienceVolume "0.60000002384186"
SET OutboundChatVolume "1"
SET InboundChatVolume "1"
SET VoiceActivationSensitivity "0.40000003576279"
SET gxWindow "1"
SET gxMaximize "1"
SET mouseSpeed "1.5"
SET baseMip "1"
SET gxRefresh "60"
SET realmName "AnthoriA RC3 - jyxo.com"
SET installType "Retail"
SET portal "us"
[/I]

I run wow with "wine WoW.exe -opengl"
I run wow with "wine WoW.exe -d3d"
see attachments
pls help me.
wow the burning crusade worked good
sorry for my english

---

### Post by seals77 on 2009-02-19
added: login - opengl

---

