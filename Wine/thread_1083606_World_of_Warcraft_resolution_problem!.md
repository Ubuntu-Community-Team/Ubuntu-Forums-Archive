---
title: "World of Warcraft resolution problem!"
date: 2009-03-01
forum: Wine
---

### Post by tony_the_m on 2009-03-01
Well I used to run WoW in 1280x1024 but my desktop resolution is 1680x1050 and every time I want to play WoW I have to change the resolution, because if I don't then this error comes up.

screenshot:
[IMG]http://farm4.static.flickr.com/3348/3318225347_aa06aa0e73.jpg?v=0[/IMG]

Any ideas to make the resolution change its self?

---

### Post by amritmatharu on 2009-03-01
Not sure which resolution you want to use? but open up your config.wtf and add

SET gxResolution "1600x900"

(replacing the 1600x900 with your resolution)

and if that doesn't work, holla

---

### Post by tony_the_m on 2009-03-02
The idea was that the game can't run my desktop resolution.

:lolflag:

---

### Post by airtonix on 2009-03-02
you havent supplied us with all the information about your system.

provide outputs of : 
[pastebin]("http://paste.ubuntu.com/") of : sudo lshw
[pastebin]("http://paste.ubuntu.com/") of : sudo lspci
[pastebin]("http://paste.ubuntu.com/") of : sudo glxinfo
your monitor model and make
screenshots of each tab from your winecfg
[pastebin]("http://paste.ubuntu.com/") of your config.wtf

---

### Post by wolfmanjack on 2009-03-03
Have you tried changing the game resolution in the config.wtf?

What also could help is 
[http://www.wowinterface.com/downloads/info5202-ApplyToForehead.html](http://www.wowinterface.com/downloads/info5202-ApplyToForehead.html)
since you haven't mentioned that you use it.

Good luck

---

### Post by NoranaC on 2009-03-03
I've been having the same problem except not that I upgraded to 8.10, I get that error no matter what I do with the screen resolution and with the config.wtf file...

---

### Post by tony_the_m on 2009-03-04
OK here there are!

Config.wtf:
```
SET readTOS "1"
SET readEULA "1"
SET readScanning "-1"
SET readContest "-1"
SET readTerminationWithoutNotice "-1"
SET installType "Retail"
SET locale "enUS"
SET movie "0"
SET showToolsUI "1"
SET realmList "list.eternion-wow.com"
SET coresDetected "1"
SET hwDetect "0"
SET gxColorBits "24"
SET gxDepthBits "24"
SET gxResolution "1280x1024"
SET gxMultisampleQuality "0.000000"
SET gxFixLag "0"
SET videoOptionsVersion "1"
SET mouseSpeed "1"
SET Gamma "1.000000"
SET Sound_VoiceChatInputDriverName "System Default"
SET Sound_VoiceChatOutputDriverName "System Default"
SET Sound_OutputDriverName "System Default"
SET Sound_MusicVolume "0.40000000596046"
SET Sound_AmbienceVolume "0.60000002384186"
SET farclip "507"
SET particleDensity "1.000000"
SET realmName "NEW HIGH RATES NORTHREND"
SET SoundOutputSystem "&#8220;1&#8243;"
SET SoundBufferSize "&#8220;100&#8243;"
SET gxRefresh "58"
SET environmentDetail "1.5"
SET weatherDensity "1"
SET textureFilteringMode "5"
SET shadowLevel "0"
SET specular "1"
SET Sound_MasterVolume "1"
SET Sound_SFXVolume "1"
SET gameTip "12"
SET checkAddonVersion "0"
SET groundEffectDensity "24"
SET groundEffectDist "80"
SET useUiScale "1"
```

wine cfg:
[IMG]http://farm4.static.flickr.com/3332/3327625499_c4c36dfebc.jpg?v=0[/IMG]

And if I set the resolution higher the game works slower.

---

