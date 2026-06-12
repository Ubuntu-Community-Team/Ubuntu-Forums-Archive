---
title: "World of Warcraft question"
date: 2009-06-22
forum: Wine
---

### Post by Jurich244 on 2009-06-22
Hello,

I'm sure this has been posted a million times so I apologize if this has been covered.  I am rather new to ubuntu and linux in general.  Right now I am dual booting between Windows 7 and Ubuntu 9.04.  I have WoW installed on both Windows and Ubuntu using Wine.  Everything works great under Ubuntu and the install using wine was simple.  The performance between windows and linux is drastic however.  I was expecting to suffer some FPS drop but I am getting around 50% of what I do in windows.  I have a decent system with an E8400 3.0 GHz dual core processor and EVGA 260 vid card and I usually get > 100 FPS in zones and > 50 in cities.  Using wine in Ubuntu with the same in-game settings im getting about 50-60 in zones and about 20 in cities.  Is that normal?  Is there anything that can be done to increase performance at all?  I have already added the opengl line in the config file in the WTF folder as well as a couple other lines that were part of the instructions I was following during the install.  I know I wont get the same performance under linux then I will under Windows but is there something I can do to make it a bit better?  I like ubuntu much better then windows but am addicted to WoW and only can imagine how it will run in raids and bg's.  If there is anything I can do please let me know.  I am running the 64 bit version of Ubuntu 9.04 and the Nvidia 185 driver off their webiste.  As I said everything works great as far as sound, controls, and the graphic rendering but the performance is about 50% of that on my windows install.  HELP!

---

### Post by LoloftheRings on 2009-06-22
If I'm not mistaking, WoW can be ran in OpenGL.

WoW uses DirectX by default, which runs very poor with wine. OpenGL has a much better performance.
To run WoW in OpenGL mode, create a script in your home directory, or anywhere else you want it by going to places -> home and right click in the file browser (nautilus) -> create -> empty file. Call it runWow.sh and add the following content to the file:
```

#!/bin/bash
wine "C:\Program Files\World Of Warcraft\WoW.exe" -opengl&
sleep 2
renice -1 -p
renice -1 -p

```

Correct me in the script if I made typo's, I'm not sure where wow is installed by default.

When the script is saved, open a terminal ( Applications -> Accessoires -> Terminal) and run the following command:
```

chmod +x ~/runWow.sh

```

this will make the script executable.

Now, you can run the script by double clicking it. You could also make a menu entry using right click on the menu -> edit menu's

Happy gaming!

---

### Post by Rody on 2009-06-22
you could also just add 
SET gxAPI "OpenGL"


lots of good info for running wow on linux here 
[http://www.wowwiki.com/Linux/Wine#Typical_Config.wtf](http://www.wowwiki.com/Linux/Wine#Typical_Config.wtf)

---

### Post by themusicalduck on 2009-06-23
Remember to disable compiz before running wow or it'll affect the performance drastically.

---

### Post by Jurich244 on 2009-06-24
Hmmm it seems that if I leave my PC running for a bit the performance slowly declines.  If I restart I gain about 20 fps on average.  I use the Titan Panel addon to monitor performance and it shows this increase.  What could that mean?  Does restarting do anything beyond clearing RAM that may be causing this?  I have 4 GB of ram on the x64 version of ubuntu.

---

### Post by Rody on 2009-06-24
some info and a couple of things to try.

In the past I have had pretty poor performance with wine and WOW, but with newest drivers I am actually getting better performance than I do in windows.

update to latest linux drivers 
update to latest wine or better yet use crossover games

using crossover games made setting up games in linux much easer and if you dont want to take the time to learn how to set up wine with all the tricks and tips then crossover might be something for you to look into.

It has been a while sence i set up wine or crossover games but i think in each i had to set up my video card memory other wise it just swapped to disk all the time. 

It looks like you have the latest drivers but I dislike using Nvidias installer and use a precompiled driver from [https://launchpad.net/~brandonsnider/+archive/ppa](https://launchpad.net/~brandonsnider/+archive/ppa) . not sure if that makes any deference at all but it never hurts to check. 
here is a list of my config.wft

SET gxApi "OpenGL"
SET readTOS "1"
SET readEULA "1"
SET readScanning "-1"
SET readContest "-1"
SET locale "enUS"
SET hwDetect "0"
SET gxResolution "1680x1050"
SET gxRefresh "50"
SET gxMultisampleQuality "0.000000"
SET gxFixLag "0"
SET fullAlpha "1"
SET SmallCull "0.040000"
SET DistCull "500.000000"
SET trilinear "1"
SET frillDensity "24"
SET farclip "507"
SET specular "1"
SET pixelShaders "1"
SET unitDrawDist "300.000000"
SET accountName "username"
SET movie "0"
SET realmList "us.logon.worldofwarcraft.com"
SET readTerminationWithoutNotice "-1"
SET installType "Retail"
SET showToolsUI "1"
SET patchlist "us.version.worldofwarcraft.com"
SET coresDetected "8"
SET videoOptionsVersion "2"
SET Gamma "1.000000"
SET Sound_OutputDriverName "System Default"
SET Sound_MusicVolume "0.40000000596046"
SET Sound_AmbienceVolume "0.60000002384186"
SET mouseSpeed "0.5"
SET Sound_VoiceChatInputDriverName "System Default"
SET Sound_VoiceChatOutputDriverName "System Default"
SET ChatMusicVolume "0.29999998211861"
SET ChatSoundVolume "0.39999997615814"
SET ChatAmbienceVolume "0.29999998211861"
SET realmName "Bladefist"
SET gameTip "14"
SET VoiceActivationSensitivity "0.39999997615814"
SET uiScale "0.71999996900558"
SET useUiScale "1"
SET processAffinityMask "3"
SET accounttype "LK"
SET projectedTextures "1"
SET checkAddonVersion "0"
SET lastCharacterIndex "4"
SET Sound_EnableAmbience "0"

---

### Post by Rody on 2009-06-24
double post

---

