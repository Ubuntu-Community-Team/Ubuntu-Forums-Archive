---
title: "WoW Error unable to start"
date: 2009-02-15
forum: Wine
---

### Post by Scrix on 2009-02-15
At first the game would not start for me I would just get an error and exit do desktop in a lower screen resolution. I tried running the game in the screen res and it played the start-up cinematic and went to a white screen and got the same error basically I think there's a problem with my video settings, and cant figure out what. also the sound still plays until I exit the game 

==============================================================================
World of WarCraft (build 9551)

Exe:      C:\Program Files\World of Warcraft\Wow.exe
Time:     Feb 15, 2009 11:25:19.489 AM
User:     griffin
Computer: griffin-desktop
------------------------------------------------------------------------------

This application has encountered a critical error:

ERROR #132 (0x85100084) Fatal Exception
Program:	C:\Program Files\World of Warcraft\Wow.exe
Exception:	0xC0000005 (ACCESS_VIOLATION) at 0073:005D37F8

The instruction at "0x005D37F8" referenced memory at "0xFFB31C7C".
The memory could not be "read".


WoWBuild: 9551
Settings: 
SET readTOS "-1"
SET readEULA "-1"
SET readScanning "-1"
SET readContest "-1"
SET readTerminationWithoutNotice "-1"
SET installType "Retail"
SET locale "enUS"
SET movie "0"
SET showToolsUI "1"
SET portal "us"
SET realmList "us.logon.worldofwarcraft.com"
SET patchlist "us.version.worldofwarcraft.com"
SET coresDetected "4"
SET processAffinityMask "3"
SET hwDetect "0"
SET gxColorBits "24"
SET gxDepthBits "24"
SET gxResolution "1024x768"
SET gxRefresh "60"
SET gxMultisampleQuality "0.000000"
SET gxFixLag "0"
SET videoOptionsVersion "1"
SET Gamma "1.000000"
SET Sound_OutputDriverName "System Default"
SET Sound_MusicVolume "0.40000000596046"
SET Sound_AmbienceVolume "0.60000002384186"
SET farclip "777.000000"
SET specular "1"
SET particleDensity "1.000000"
SET groundEffectDensity "24"
------------------------------------------------------------------------------

---

### Post by Mmmbopdowedop on 2009-02-15
Have you tried running it in OpenGL?
Sounds like this could be your problem if you haven't tried already.

Add the line:
> SET gxApi "opengl"
to your config.wtf file

You should really read this guide if you haven't already: [https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

Good luck.

---

### Post by Scrix on 2009-02-15
Thanks for the reply. Yeah I have read that entire guide along with the troubleshooting guide and cannot seem to find the config.wtf file. I am not new to this game and know how to find such files but all i have in my wtf are the run once files, am I looking in the wrong spot?

---

### Post by Mmmbopdowedop on 2009-02-15
Assuming the directory you are looking in is:

> ..\Program Files\World of Warcraft\WTF

Then yeah, you are looking in the right spot.
If you can't see the Config.wtf in there, then just create a new file, named that & paste the following:
> 
SET gxApi "opengl"
SET readTOS "-1"
SET readEULA "-1"
SET readScanning "-1"
SET readContest "-1"
SET readTerminationWithoutNotice "-1"
SET installType "Retail"
SET locale "enUS"
SET movie "0"
SET showToolsUI "1"
SET portal "us"
SET realmList "us.logon.worldofwarcraft.com"
SET patchlist "us.version.worldofwarcraft.com"
SET coresDetected "4"
SET processAffinityMask "3"
SET hwDetect "0"
SET gxColorBits "24"
SET gxDepthBits "24"
SET gxResolution "1024x768"
SET gxRefresh "60"
SET gxMultisampleQuality "0.000000"
SET gxFixLag "0"
SET videoOptionsVersion "1"
SET Gamma "1.000000"
SET Sound_OutputDriverName "System Default"
SET Sound_MusicVolume "0.40000000596046"
SET Sound_AmbienceVolume "0.60000002384186"
SET farclip "777.000000"
SET specular "1"
SET particleDensity "1.000000"
SET groundEffectDensity "24"


Then try and start it up again. :)

---

### Post by Scrix on 2009-02-15
ah, yeah that is where I was looking and nothing was there, but i will do that thanks 
also I just set my resolution way too low... cant even see anything
you know how to fix that?

---

### Post by Mmmbopdowedop on 2009-02-15
System -> Preferences -> Screen Resolution (?)

Not sure if that's what you mean/wanted.

---

### Post by Scrix on 2009-02-15
yeah thats how i set it so low, but now i cant really see anything at all... no big deal ill find a way to fix it

---

### Post by Pikestaff on 2009-02-18
For the record, me (and from what I can tell from the official forums, some other OpenGL folks as well) get this same error message and crash randomly while playing the game.  For me it happens anytime a mage table is summoned, and when the last boss in Gundrak turns into a rhino.  At least I can get into the game, though, unlike you.

I did get a Blue response on the issue from a kind Blizz techie who said he reported it as a bug for me.  Whether or not it's related to your issue or when it will be fixed I don't know, but the error message is exactly the same.

I'm afraid that doesn't exactly solve your problem but I wanted to let you know that there is a possibility it's a game bug and not a WoW-on-Linux thing.  Good luck getting it up and running though.

---

### Post by auntiestacey on 2009-02-19
Hey Scrix, I was having the same issue (found your post while looking for a solution).
I found that although ubuntu found and installed my video driver it was not the latest recommended version. Vers 177 was installed but the latest is 180. I had to manually update. Once I updated and rebooted wow came up with no problems. (Except no sound, but I think I know how to fix that.)

FYI- I use Synaptic Package Manager

Hope this helps.

---

