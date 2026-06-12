---
title: "World of Warcraft can't start, please help."
date: 2009-11-27
forum: Wine
---

### Post by TheNerdAL on 2009-11-27
Okay, so the intro movie starts, but after that, it says this: 


==============================================================================
World of WarCraft (build 8874)

Exe:      Z:\home\adrian\Desktop\World of Warcraft\WoW.exe
Time:     Nov 27, 2009 10:46:43.227 AM
User:     adrian
Computer: LaraComputer
------------------------------------------------------------------------------

This application has encountered a critical error:

ERROR #132 (0x85100084) Fatal Exception
Program:    Z:\home\adrian\Desktop\World of Warcraft\WoW.exe
Exception:    0xC0000005 (ACCESS_VIOLATION) at 0073:343BBD2D

The instruction at "0x343BBD2D" referenced memory at "0x343BBD2D".
The memory could not be "read".


WoWBuild: 8874
Settings: 
SET locale "enUS"
SET videoOptionsVersion "1"
SET movie "0"
SET realmList "us.logon.worldofwarcraft.com"
SET coresDetected "1"
SET hwDetect "0"
SET gxRefresh "60"
SET gxMultisampleQuality "0.000000"
SET gxFixLag "0"
SET Gamma "1.000000"
SET showToolsUI "1"
SET Sound_OutputDriverName "System Default"
SET Sound_MusicVolume "0.40000000596046"
SET Sound_AmbienceVolume "0.60000002384186"
SET farclip "450.000000"
SET specular "1"
SET particleDensity "0.4"
SET groundEffectDensity "24"
SET gxResolution "800x600"
SET gxWindow "1"
SET gxApi "opengl"
SET gxColorBits "24"
SET gxDepthBits "24"
SET readTOS "-1"
SET readEULA "-1"
SET readTerminationWithoutNotice "-1"
SET readScanning "-1"
SET readContest "-1"
SET expansionMovie "0"
SET portal "us"



It also says some other stuff but I think it is for Blizzard.

Can anyone help?! :(

---

### Post by staf0048 on 2009-11-27
Have you tried updating your WINE version?  Stable version is currently 1.0.1 and dev version is up to 1.1.33 according to their website.  I'm currently running off of the lastest dev and it's fixed many of the issues I've had running some games.

---

### Post by TheNerdAL on 2009-11-27
> **staf0048 said:**
> Have you tried updating your WINE version?  Stable version is currently 1.0.1 and dev version is up to 1.1.33 according to their website.  I'm currently running off of the lastest dev and it's fixed many of the issues I've had running some games.

Yes, that is updated.

---

### Post by TheNerdAL on 2009-11-27
Anyone?

---

### Post by Pikestaff on 2009-11-27
When I've gotten that error message in the past it's been an OpenGL related thing.  Of course, there's not a whole lot we Linux WoWers can do about it, and it puts the Mac people in a bind too.

I think mine was just fixed in a later patch, but that error can also be caused by other issues... you might try some of the things Blizz suggests here: [http://eu.blizzard.com/support/article.xml?locale=en_GB&articleId=24198](http://eu.blizzard.com/support/article.xml?locale=en_GB&articleId=24198) (modified for Linux, of course)

---

### Post by staf0048 on 2009-11-27
Another option you can try is "Play on Linux", which is a WINE wrapper.  I just looked through the availalbe apps, and they have a script to help you install and configure WOW specifically for WINE.

Website is:  [http://www.playonlinux.com/en](http://www.playonlinux.com/en)

FYI - The program gets installed into your Games directory by default, even though it's a utility for all types of apps.

---

### Post by Alatar1 on 2009-11-28
Ya i would try the play on linux, I use it and I don't get any errors like that :) also if it doesn't work.. more info and what hardware your rockin would be helpful.

---

### Post by brian70809 on 2009-11-28
make sure the OpenGL drivers are working.

Go to termina and type "glxgears"...

are you running an Nvidia card?  Get the latest drivers.  They have updated OpenGL drivers in them and work frantastic.

good luck!

---

### Post by TheNerdAL on 2009-11-28
> **staf0048 said:**
> Another option you can try is "Play on Linux", which is a WINE wrapper.  I just looked through the availalbe apps, and they have a script to help you install and configure WOW specifically for WINE.

Website is:  [http://www.playonlinux.com/en](http://www.playonlinux.com/en)

FYI - The program gets installed into your Games directory by default, even though it's a utility for all types of apps.

It Says I need CDs or a DVD, I want to install the trial version.

---

### Post by TheNerdAL on 2009-11-28
> **brian70809 said:**
> make sure the OpenGL drivers are working.

Go to termina and type "glxgears"...

are you running an Nvidia card?  Get the latest drivers.  They have updated OpenGL drivers in them and work frantastic.

good luck!
 
I don't have a Nvidia Card.

---

### Post by brian70809 on 2009-11-29
unless things have changed.  ATI cards are a little rough on the driver side.

does the GLXGEARS test work for you?

---

