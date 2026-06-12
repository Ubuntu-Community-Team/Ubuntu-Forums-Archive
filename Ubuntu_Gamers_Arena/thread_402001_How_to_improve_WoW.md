---
title: "How to improve WoW"
date: 2007-04-05
forum: Ubuntu Gamers Arena
---

### Post by UltimaDude on 2007-04-05
Here is my World Of Warcraft config, I can run World Of Warcraft easily, with just a bit of lagg in populated places,
You might want to configure the resolution and ENGB:

SET gxResolution "1280x1024"
SET gxRefresh "60"
SET hwDetect "0"
SET movie "0"
SET readTOS "1"
SET realmList "eu.logon.worldofwarcraft.com"
SET gxMultisampleQuality "0.000000"
SET readEULA "1"
SET readScanning "-1"
SET realmName "Turalyon"
SET gameTip "16"
SET gxCursor "0"
SET SmallCull "0.040000"
SET frillDensity "32"
SET farclip "357"
SET Gamma "0.600000"
SET MusicVolume "0.60000002384186"
SET SoundVolume "1"
SET SoundOutputSystem "1"
SET SoundBufferSize "150"
SET MasterVolume "1"
SET ffx "0"
SET AmbienceVolume "0.60000002384186"
SET uiScale "1"
SET mouseSpeed "1"
SET cameraPitchMoveSpeed "90"
SET cameraYawMoveSpeed "180"
SET cameraPitchSmoothSpeed "45"
SET cameraYawSmoothSpeed "180"
SET cameraSmoothStyle "0"
SET cameraSmoothTrackingStyle "0"
SET cameraDistanceMaxFactor "1"
SET SoundZoneMusicNoDelay "1"
SET gxColorBits "24"
SET statusBarText "1"
SET gxApi "opengl"
SET ffxDeath "0"
SET minimapZoom "0"
SET guildMemberNotify "1"
SET profanityFilter "0"
SET readContest "-1"
SET gxDepthBits "24"
SET expansionMovie "0"
SET locale "enGB"

If you also have any questions about running WoW ask them here and i'll answer as soon as possible.

---

### Post by sammyd253 on 2007-04-05
I don't want to hijack this post, but I find this post interesting.  I haven't installed WoW on my Ubuntu setup but would like to in the future.  Could you or anybody else point me to a thread that contains documentation on installing WoW in Ubuntu?  If you could that'd be awesome, and I'd really appriciate it!  Thanks!

---

### Post by shavenlunatic on 2007-04-05
> **sammyd253 said:**
> I don't want to hijack this post, but I find this post interesting.  I haven't installed WoW on my Ubuntu setup but would like to in the future.  Could you or anybody else point me to a thread that contains documentation on installing WoW in Ubuntu?  If you could that'd be awesome, and I'd really appriciate it!  Thanks!

[www.winehq.com](www.winehq.com)

---

### Post by UltimaDude on 2007-04-05
> **sammyd253 said:**
> I don't want to hijack this post, but I find this post interesting.  I haven't installed WoW on my Ubuntu setup but would like to in the future.  Could you or anybody else point me to a thread that contains documentation on installing WoW in Ubuntu?  If you could that'd be awesome, and I'd really appriciate it!  Thanks!
If your wondering about installing World Of Warcraft its pretty easy, its basically putting in the CD and running the installer.exe when it asks for another disc, just putting it in, though this can be different on different types of hardware so I reccomend checking [http://www.winehq.com](http://www.winehq.com) which was in the last post.

---

### Post by compiledkernel on 2007-04-05
This is the extensive WoW howto held by the community. 

[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

---

### Post by sammyd253 on 2007-04-05
Nice, I like.  I'm not sure if it will work for me atm though.

I want to install Fiesty x86-64 on my system.  Will Wine run on this platform?  Is there a 64-bit version of Wine or can I install a 32-bit version in a 64-bit environment?

Once Wine is installed on a x86-64 copy of Fiesty, will WoW install, with the latest patches, and the Burning Crusade add-on?

---

### Post by UltimaDude on 2007-04-05
> **sammyd253 said:**
> Nice, I like.  I'm not sure if it will work for me atm though.

I want to install Fiesty x86-64 on my system.  Will Wine run on this platform?  Is there a 64-bit version of Wine or can I install a 32-bit version in a 64-bit environment?

Once Wine is installed on a x86-64 copy of Fiesty, will WoW install, with the latest patches, and the Burning Crusade add-on?

Simple64 has a download for Wine, and it works since I play WoW on 64 Bit fiesty with 32 bit wine.

---

### Post by sammyd253 on 2007-04-05
Excellent.  Do you have Burning Crusade installed as well?

---

### Post by tcpip4lyfe on 2007-04-05
When I played WoW I used cedega for 2 years. I tried both Wine and Cedega and for my setup at least, Cedega ran much better.  Here is a copy that I have saved of my config.wtf.

```
SET hwDetect "0"
SET lodDist "100.000000"
SET SmallCull "0.010000"
SET DistCull "500.000000"
SET farclip "477"
SET movie "0"
SET readTOS "1"
SET readEULA "1"
SET readScanning "-1"
SET readContest "-1"
SET gxMultisampleQuality "0.000000"
SET accountName "*****"
SET locale "enUS"
SET Gamma "0.700000"
SET MusicVolume "0.40000000596046"
SET SoundVolume "1"
SET MasterVolume "1"
SET EnableMusic "0"
SET realmName "Boulderfist"
SET gameTip "50"
SET AmbienceVolume "0.60000002384186"
SET uiScale "1"
SET mouseSpeed "1"
SET profanityFilter "0"
SET cameraYawMoveSpeed "180"
SET cameraYawSmoothSpeed "180"
SET cameraDistanceMaxFactor "2"
SET scriptMemory "131072"
SET minimapInsideZoom "0"
SET minimapZoom "0"
SET weatherDensity "3"
SET ShowTargetCastbar "1"
SET ShowVKeyCastbar "1"
SET gxResolution "1440x900"
SET frillDensity "48"
SET particleDensity "1.000000"
SET unitDrawDist "300.000000"
SET gxCursor "0"
SET SoundOutputSystem "1"
SET useWeatherShaders "0"
SET guildMemberNotify "1"
SET autoClearAFK "0"
SET gxColorBits "24"
SET gxDepthBits "24"
SET fullAlpha "1"
SET trilinear "1"
SET specular "1"
SET realmList "us.logon.worldofwarcraft.com"
SET soundMaxHardwareChannels "12"
SET gxTripleBuffer "1"
SET M2UsePixelShaders "1"
SET ffx "0"
SET gxapi "opengl"
SET timingTestError "3"
SET shadowLevel "0"
SET cameraView "0"
SET expansionMovie "0"
SET gxRefresh "60"
SET checkAddonVersion "0"
```

Try running the game in D3D and opengl by running 

wine wow -d3d or wine wow -opengl

After 2 years of tweaking I was able to get 30-40 fps at the bank in IF (back when people were in IF) and about 40-50 fps everywhere else with modest hardware.

Nvidia gforce 6600
athlon 2.2ghz 32bit
1 gig ram

[URL="http://transgaming.org/forum/"]
http://transgaming.org/forum/[/URL]  is a good place to check out tweeks even if you dont use cedega.

---

### Post by UltimaDude on 2007-04-05
> **sammyd253 said:**
> Excellent.  Do you have Burning Crusade installed as well?

Yes, Burning Crusade is installed on my computer, it runs perfect, though there might be a different if I remove The Burning Crusade.

---

### Post by sammyd253 on 2007-04-05
Will installing it on Ubuntu work if I install WoW and Burning Crusade and fully update it on Windows first, then copy that directory over to Ubuntu, and use Wine to install?

---

### Post by UltimaDude on 2007-04-05
I'm not really sure, it might work but it might not, it should work though it might not work after the next update 2.13 unless you copy the registry details over, I would reccomend doing a fresh install on your Ubuntu partition and then updating it, it works.

---

### Post by ArtificialSynapse on 2007-04-05
That should work, no real reason to do that though, it's really easy to install wow through wine on ubuntu.

I copied all the files from the wow cd's into a folder, and then ran the installer.exe, but I believe you can just run it right from the cd's 

```
wine installer.exe
```

---

### Post by UltimaDude on 2007-04-05
> **ArtificialSynapse said:**
> That should work, no real reason to do that though, it's really easy to install wow through wine on ubuntu.

I copied all the files from the wow cd's into a folder, and then ran the installer.exe, but I believe you can just run it right from the cd's 

```
wine installer.exe
```
That is true, the one thing that annoys me is that I cannot read the percent due to the small writing, I Have to go close to my monitor :lolflag:

---

