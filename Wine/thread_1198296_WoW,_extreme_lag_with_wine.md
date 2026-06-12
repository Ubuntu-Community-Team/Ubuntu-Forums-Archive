---
title: "WoW, extreme lag with wine"
date: 2009-06-27
forum: Wine
---

### Post by barato on 2009-06-27
I am using ATI graphics card, and I finally got it to allow me to enter the game world without crashing.

Now that I am in though, I am lagging LIKE CRAZY. For some reason I am only getting 1 fps.

My computer specs are:
AMD Athlon 64 
ATI Radeon Express Video Card 
2 GB DDR2 RAM

My WTF config File says
SET readTOS "1"
SET readEULA "1"
SET readScanning "-1"
SET readContest "-1"
SET readTerminationWithoutNotice "1"
SET installType "Retail"
SET locale "enGB"
SET movie "0"
SET showToolsUI "0"
SET portal "eu"
SET realmList "realm.neverendless-wow.com"
SET patchlist "logon.neverendless-wow.com"
SET coresDetected "2"
SET hwDetect "0"
SET gxColorBits "24"
SET gxDepthBits "24"
SET gxRefresh "60"
SET gxMultisampleQuality "0.000000"
SET videoOptionsVersion "1"
SET Gamma "1.000000"
SET Sound_OutputDriverName "System Default"
SET Sound_MusicVolume "0.40000000596046"
SET Sound_AmbienceVolume "0.60000002384186"
SET farclip "397"
SET particleDensity "1.000000"
SET spellEffectLevel "3"
SET groundEffectDensity "24"
SET gxApi "opengl"
SET ffxDeath "0"
SET ffxGlow "0"
SET SoundOutputSystem "1"
SET SoundBufferSize "150"
SET realmName "Neverendless-WoW 3.0.9"
SET gameTip "9"
SET gxResolution "800x600"
SET ffxNetherWorld "0"
SET M2UseShaders "0"
SET mouseSpeed "1"
SET Sound_VoiceChatInputDriverName "System Default"
SET Sound_VoiceChatOutputDriverName "System Default"
SET accountName "barato"
SET DesktopGamma "1"
SET gxTripleBuffer "1"
SET baseMip "1"
SET environmentDetail "0.75"
SET UIFaster "2"



Any ideas how to bump it up to atleast 30 fps?

---

### Post by ELD on 2009-06-27
Please use the WINE forum for WINE related questions :)

---

### Post by Blood//Stain//Child on 2009-06-27
> **barato said:**
> I am using ATI graphics card, and I finally got it to allow me to enter the game world without crashing.

Now that I am in though, I am lagging LIKE CRAZY. For some reason I am only getting 1 fps.

My computer specs are:
AMD Athlon 64 
ATI Radeon Express Video Card 
2 GB DDR2 RAM

My WTF config File says
SET readTOS "1"
SET readEULA "1"
SET readScanning "-1"
SET readContest "-1"
SET readTerminationWithoutNotice "1"
SET installType "Retail"
SET locale "enGB"
SET movie "0"
SET showToolsUI "0"
SET portal "eu"
SET realmList "realm.neverendless-wow.com"
SET patchlist "logon.neverendless-wow.com"
SET coresDetected "2"
SET hwDetect "0"
SET gxColorBits "24"
SET gxDepthBits "24"
SET gxRefresh "60"
SET gxMultisampleQuality "0.000000"
SET videoOptionsVersion "1"
SET Gamma "1.000000"
SET Sound_OutputDriverName "System Default"
SET Sound_MusicVolume "0.40000000596046"
SET Sound_AmbienceVolume "0.60000002384186"
SET farclip "397"
SET particleDensity "1.000000"
SET spellEffectLevel "3"
SET groundEffectDensity "24"
SET gxApi "opengl"
SET ffxDeath "0"
SET ffxGlow "0"
SET SoundOutputSystem "1"
SET SoundBufferSize "150"
SET realmName "Neverendless-WoW 3.0.9"
SET gameTip "9"
SET gxResolution "800x600"
SET ffxNetherWorld "0"
SET M2UseShaders "0"
SET mouseSpeed "1"
SET Sound_VoiceChatInputDriverName "System Default"
SET Sound_VoiceChatOutputDriverName "System Default"
SET accountName "barato"
SET DesktopGamma "1"
SET gxTripleBuffer "1"
SET baseMip "1"
SET environmentDetail "0.75"
SET UIFaster "2"



Any ideas how to bump it up to atleast 30 fps?

What kind of Radeon Xpress do you have?

---

### Post by barato on 2009-06-27
I just realized that I posted this into the wrong forum. My bad, I haven't been on the forum for a good year so I didn't notice the creation of the new subforum. Therefore, I must apologize for that, and if someone can move this topic to that forum that would be much appreciated. 


My ATI graphics card is an ATI Radeon Xpress 1250.

---

### Post by gjoellee on 2009-06-28
Here are some reasons that often cause great lag on Windows games in Linux:

-You have not installed a driver for your graphics card
-WINE is badly configured
-You have set game graphics to maximum (this can be changed in the game and can dramatically improve your FPS)
-You may be using a bad version of WINE. To be safe it is smart to stay with the current WINE 1.0.1 version which is the latest stable version of WINE
-Bad support for your graphics card

---

### Post by Blood//Stain//Child on 2009-06-28
> **gjoellee said:**
> Here are some reasons that often cause great lag on Windows games in Linux:

-You have not installed a driver for your graphics card
-WINE is badly configured
-You have set game graphics to maximum (this can be changed in the game and can dramatically improve your FPS)
-You may be using a bad version of WINE. To be safe it is smart to stay with the current WINE 1.0.1 version which is the latest stable version of WINE
-Bad support for your graphics card

He was using the Opensource driver on Jaunty. I think that pretty much says everything about the speed issue.

---

### Post by agavril on 2009-06-28
No, his main problem is ATI is the worst that is why he is lagging because ATI just doesn't work well with anything

---

### Post by Blood//Stain//Child on 2009-06-28
> **agavril said:**
> No, his main problem is ATI is the worst that is why he is lagging because ATI just doesn't work well with anything

ATi works fine with Windows, so that's a non-valid statement. It is also perfectly possible to get WoW running at a reasonable framerate with the proprietary driver on Ubuntu 8.10 or before. His problem is that he's using Jaunty and therefore forced to use the Opensource Radeon driver, which has very poor 3D performance for the time being.

---

### Post by Th3_uN1Qu3 on 2009-07-02
When you said forced it just means that it isn't installed by default, enable the installation of restricted drivers then update to the latest version from ATi's site, works perfectly.

---

### Post by ministoat on 2009-07-25
I'd like to know if you got anywhere with this - I'm using jaunty and an xpress 1250 too, I cannot even get wow to run with severe graphic mess :(

---

### Post by Rrasyrogenees on 2009-07-25
i have only a small idea that might help some... 2gb ram might not be enough... if you can get 4 it might improve a lot too... i currently have 8gb but since i am running WoW on my 32-bit ubuntu that is irrelevant cause only 4gb is recognized on 32-bit but it works great nonetheless. 

and, oh yes, make sure the driver is working well on your card, it will make a difference too

---

### Post by hikaricore on 2009-07-25
2Gb is plenty for WoW.

---

