---
title: "WOW starting black screen + cursor"
date: 2010-01-21
forum: Wine
---

### Post by Sebastian Perez Teres on 2010-01-21
Hi all, im having trouble with World of Warcraft under wine 1.0.1 on ubuntu 9.10. I have a Toshiba Satellite L305-S5939, it comes with a Intel GMA 4500MHD i followed this thread [https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

The problem is when i start the game i get a black screen and the little hand cursor... i can move it and even click the buttons and they work, but i cant see anything. It throws no error messages... Please help, I cant find any solution, here is a screenshot... [IMG]http://www.freeimagehosting.net/uploads/th.8b1f72d66d.png[/IMG]

Thanks in advance :popcorn:

---

### Post by 8Kuula on 2010-01-21
Edit your config.wtf file and add line:
```
SET ffxGlow "0"
```
If it is not there, change to "0" if it is.
*crosses fingers*

---

### Post by Sebastian Perez Teres on 2010-01-22
It was already there and it was also set to 0 so that didnt do it :(, but thanks any way, here is my config.wtf

```
SET locale "enUS"
SET realmList "login.uber-wow.info"
SET patchlist "us.version.worldofwarcraft.com"
SET coresDetected "2"
SET hwDetect "0"
SET gxRefresh "60"
SET gxMultisampleQuality "0.000000"
SET videoOptionsVersion "2"
SET textureFilteringMode "0"
SET movie "0"
SET Gamma "1.000000"
SET showToolsUI "1"
SET Sound_OutputDriverName "System Default"
SET Sound_MusicVolume "0.60000002384186"
SET Sound_AmbienceVolume "0.60000002384186"
SET MaxLights "1"
SET farclip "177"
SET readTOS "1"
SET readEULA "1"
SET gxWindow "1"
SET accounttype "LK"
SET Sound_SFXVolume "0.60000002384186"
SET realmName "Uber-Blizz 3.3.0a"
SET CombatLogRangeParty "2000"
SET CombatLogRangePartyPet "2000"
SET CombatLogRangeFriendlyPlayers "2000"
SET CombatLogRangeFriendlyPlayersPets "2000"
SET CombatLogRangeHostilePlayers "2000"
SET CombatLogRangeHostilePlayersPets "2000"
SET CombatLogRangeCreature "2000"
SET groundEffectDist "70"
SET environmentDetail "0.5"
SET particleDensity "0.10000000149012"
SET ffxGlow "0"
SET timingTestError "0"
SET readScanning "-1"
SET readContest "-1"
SET readTerminationWithoutNotice "-1"
SET installType "Retail"
SET showGameTips "0"
SET checkAddonVersion "0"
SET weatherDensity "0"
SET mouseSpeed "1.5"
SET gxMaximize "1"
SET gxResolution "1280x800"
SET gxTripleBuffer "1"
SET baseMip "1"
SET ffxDeath "0"
SET uiScale "0.75999999046326"
SET useUiScale "1"
SET Sound_NumChannels "64"
SET gxApi "opengl"
SET M2UseShaders "0"
```

I was thinking maybe it has something to do with the video card, but i cant figure out what is wrong :confused:

---

