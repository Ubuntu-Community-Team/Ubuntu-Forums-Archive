---
title: "graphical glitches and no sound in WoW"
date: 2010-03-03
forum: Wine
---

### Post by aggronieszka on 2010-03-03
Hi all!

I just recently took the plunge and installed Linux as the main OS on my gaming rig. I am a computer technician by profession, so I'm experienced, but I am admittedly a linux nub. (I do have some proficiency in unix, but mostly basic stuff).

I have installed WoW with wine and it runs ok, playable when solo or 10 man, but I definitely can't do a 25 man, and I am also getting some graphical glitches that are getting under my skin.

When in a 25 man, the game stutters down to 5fps even with graphics all the way down. On Win7, I was getting 15-20fps with mid graphics settings.

As for the glitches, when moving along certain axes, my toon will move forward, but limbs stop moving, or they stutter but the movement isin't fluid. If you can image how silly it looks when on a mount, flying forward and the wings are moving only an inch up or down.

Also textures at the ground level are not laying flat on top of the ground, rather, they sink below in a grid like pattern. When I target a mob, for example, the red ring on the ground around them looks like something made by a drug addict tripping on acid.

I am also getting no sound, but that's the least of my problems.

I am using something called NVidia X Server  along with the Nvidia proprietary graphics driver version 185. Version 173 crashes my machine. Without either Server X or the driver, I can't launch WoW at all.

All software updates have been done, and I am using the newest version of Wine.

I have performed the graphics tweeks outlined in the WoW wine wiki howto. They certainly helped, allowing my machine to run WoW in the first place. I am running with all settings at minimum at the moment as I had a 25 man last night.

As for the sound, I have played around with winecfg, in the audio tab, I have checked both ALSA and OSS drivers (as outlined in the wiki). No sound from game whatsoever.

If it helps, here is my config.wtf file:

```

SET locale "enUS"
SET realmList "us.logon.worldofwarcraft.com"
SET patchlist "us.version.worldofwarcraft.com"
SET hwDetect "0"
SET gxRefresh "50"
SET gxMultisampleQuality "0.000000"
SET gxFixLag "0"
SET videoOptionsVersion "3"
SET movie "0"
SET Gamma "1.000000"
SET showToolsUI "1"
SET Sound_OutputDriverName "System Default"
SET Sound_MusicVolume "0.40000000596046"
SET Sound_AmbienceVolume "0.40000000596046"
SET farclip "177"
SET specular "1"
SET ffxDeath "0"
SET ffxGlow "0"
SET gxResolution "1920x1200"
SET gxTripleBuffer "1"
SET mouseSpeed "1"
SET lastCharacterIndex "3"
SET readTOS "1"
SET readEULA "1"
SET accounttype "LK"
SET VoiceActivationSensitivity "0.39999997615814"
SET ChatMusicVolume "0.29999998211861"
SET ChatSoundVolume "0.39999997615814"
SET ChatAmbienceVolume "0.29999998211861"
SET realmName "removed"
SET gameTip "28"
SET accountName "removed"
SET checkAddonVersion "0"
SET textureFilteringMode "0"
SET Sound_EnableSFX "0"
SET baseMip "1"
SET environmentDetail "0.5"
SET weatherDensity "0"
SET Sound_EnableErrorSpeech "0"
SET Sound_SFXVolume "0.10000000149012"
SET Sound_EnablePetSounds "0"
SET Sound_EnableSoundWhenGameIsInBG "1"
SET UIFaster "2"
```

If you need more information, I'll happily provide it.

Thanks!

---

### Post by aggronieszka on 2010-03-05
Is there a better place I can pose these questions?

---

### Post by Soulcage on 2010-03-05
Try adding: SET gxApi "opengl" to you config.wtf file and check out [http://appdb.winehq.org/objectManager.php?sClass=version&iId=17421]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=17421")
Also you're never supposed to have oss and alsa both selected you're supposed to try alsa then if that doesn't work switch to oss.

---

### Post by aggronieszka on 2010-03-05
Adding that additional line to my config,wtf file did the trick for the graphics glitches. I can't wait to see if it improves my fps in raids. THANK YOU!

I could have sworn I read in a how to wiki to select both audio drivers. I thought it was bizarre since it goes against everything I know about drivers. Anyway, I'll take a more thorough look through the link you sent me. I think I have some more tweaking to do.

Thanks so much!

---

### Post by aggronieszka on 2010-03-05
After playing around in game after making that change in my config file, I've found that the only thing fixed by it is the target circle. Now my mouse is choppy and lagging and the movement glitch is still there. I also can't tab out anymore without the game freezing up on me.

Guess I need to keep playing around with it.

---

### Post by Soulcage on 2010-03-06
Yeah blizzard was lazy and left out the hardware cursor in opengl mode there is a link to a patch on that page, though you would have to compile wine to get it to work I think.

---

