---
title: "World of Warcraft Problems"
date: 2009-05-02
forum: Wine
---

### Post by ILikeToast on 2009-05-02
Hello. I'm having some issues with running Warcraft on my WINE. I'm using Ubuntu 9.04. My video card is an older ATI Radeon 9200. My processor is an Intel Pentium 4. Yes, I know my rig sucks. Yes, I've made peace with that. 

So I can log in and character select just fine. But whenever I pick a character, and the world loads up, before I can move my character, the game crashes. 

> This application has encountered a critical error:

ERROR #132 (0x85100084) Fatal Exception
Program:	Z:\home\mathieu\Documents\World of Warcraft\Wow.exe
Exception:	0xC0000005 (ACCESS_VIOLATION) at 0073:00000000

The instruction at "0x00000000" referenced memory at "0x00000000".
The memory could not be "read".


These are some of the settings it's currently running at. 

> WoWBuild: 9835
Realm: Dalaran [206.17.111.123:3724]
Local Zone: Ironforge
Local Player: Rizatexas, 0500000002AD3198, (-4962.7,-905.954,504.708)
Total lua memory: 9616KB
Add Ons: 
Settings: 
SET hwDetect "0"
SET gxAPI "OpenGL"
SET UIFaster "2"
SET gxResolution "1152x864"
SET gxMultisampleQuality "0.000000"
SET gxFixLag "0"
SET fullAlpha "1"
SET lodDist "100.000000"
SET SmallCull "0.040000"
SET DistCull "500.000000"
SET trilinear "1"
SET frillDensity "24"
SET farclip "177"
SET pixelShaders "1"
SET particleDensity "0.30000001192093"
SET unitDrawDist "300.000000"
SET movie "0"
SET readTOS "1"
SET readEULA "1"
SET readScanning "-1"
SET readContest "-1"
SET realmList "us.logon.worldofwarcraft.com"
SET locale "enUS"
SET readTerminationWithoutNotice "-1"
SET installType "Retail"
SET expansionMovie "0"
SET showToolsUI "1"
SET patchlist "us.version.worldofwarcraft.com"
SET coresDetected "2"
SET videoOptionsVersion "1"
SET Gamma "1.300000"
SET Sound_OutputDriverName "System Default"
SET Sound_MusicVolume "0.40000000596046"
SET Sound_AmbienceVolume "0.60000002384186"
SET realmName "Dalaran"
SET mouseSpeed "1"
SET Sound_VoiceChatInputDriverName "System Default"
SET Sound_VoiceChatOutputDriverName "System Default"
SET Sound_EnableAllSound "0"
SET gameTip "112"
SET ChatMusicVolume "0.29999998211861"
SET ChatSoundVolume "0.39999997615814"
SET ChatAmbienceVolume "0.29999998211861"
SET VoiceActivationSensitivity "0.39999997615814"
SET baseMip "1"
SET spellEffectLevel "0"
SET groundEffectDensity "24"
SET groundEffectDist "70"
SET environmentDetail "0.5"
SET weatherDensity "0"
SET accounttype "BC"
SET lastCharacterIndex "2"

I would really appreciate it if any of you could help me. Like the junkie on the streetcorner, I really need my fix. Won't you be my enabler? 

Thanks again.

---

### Post by Clydtsdk-Rivendare on 2009-05-02
Just a bit of hope -- I've had this issue myself before and I got around it somehow, except it was on startup, with a much older version of wine.

Try messing with your video settings -- IIRC that's how I got around it... Wish I could be more help tho.

---

### Post by ELDal on 2009-05-02
This looks somewhat familiar, try changing the following lines.
SET pixelShaders "**0**"
SET trilinear "**0**"

and it would help if you posted a full error log (located in World of Warcraft/Errors)

---

### Post by asdfoo on 2009-05-02
buggy video drivers most likely... if you upgrade get a nvidia card next time.

as suggested by the other posters, try to turn off as much affects and lower the settings.

---

