---
title: "World of Warcraft in wine"
date: 2009-05-26
forum: Wine
---

### Post by imattacus on 2009-05-26
OK, I just installed WoW on ubuntu using wine and the installation seemed to work so i patched up to 3.1.2. Then I launched the game but it was really laggy so i closed it and looked around the forums for help and found  [this guide]("http://ubuntuforums.org/showthread.php?t=120615") So i added in the text it told me to into the config.wtf file in the WTF folder. I'm guessing this forces the game to launch in opengl mode as it was talking about opengl. Heres my config.wtf ```
SET readTOS "1"
SET readEULA "1"
SET readTerminationWithoutNotice "1"
SET readScanning "-1"
SET readContest "-1"
SET locale "enGB"
SET movie "0"
SET showToolsUI "1"
SET portal "eu"
SET realmList "wowbeez.no-ip.org"
SET coresDetected "2"
SET hwDetect "0"
SET gxResolution "1280x800"
SET gxRefresh "60"
SET gxMultisampleQuality "0.000000"
SET gxFixLag "0"
SET videoOptionsVersion "2"
SET Sound_OutputDriverName "System Default"
SET farclip "507"
SET specular "1"
SET particleDensity "0.40000000596046"
SET spellEffectLevel "3"
SET groundEffectDensity "24"
SET realmName "(3.1.2) WOTLK Xtreme I80"
SET installType "Retail"
SET accountName "imattacus"
SET mouseSpeed "1"
SET Gamma "1.000000"
SET accounttype "LK"
SET Sound_MusicVolume "0.40000000596046"
SET Sound_AmbienceVolume "0.60000002384186"
SET gameTip "1"
SET gxApi "opengl"
SET SoundOutputSystem "1"
SET SoundBufferSize "100"
SET gxColorBits "24"
SET gxDepthBits "24"

```That was my config.wtf. When I launched the game to start playing it did a really weird thing that it didnt do before everything interactive went black: 
[IMG]http://img21.imageshack.us/img21/7292/wowerror.png[/IMG]

So anyway Basically in a nutshell:
I would like to improve the performance of World of warcraft running under wine without making it go all black and weird.. :) I hope I've provided enough "evidence" to show you whats happening :)

---

### Post by themusicalduck on 2009-05-26
Have you tried disabling compiz effects?

---

### Post by imattacus on 2009-05-26
Just disabled them and still no luck:( ANy other answers?

---

### Post by hikaricore on 2009-05-26
What video hardware/drivers are you using?
You really need to provide more info per the sticky at the top of this forum when posting.

---

### Post by imattacus on 2009-05-26
[CENTER]ah nevermind... I think i will have to go without... I wish wow would make a linux version. I hear they had one
[/CENTER]

---

### Post by themusicalduck on 2009-05-26
I think I see your problem.. In your WTF file you have SET gxApi "opengl" whereas it should be SET gxApi "OpenGL" as in with the capitals included. It's might be still trying to render using directX because of that.

Also adding these lines might help performance too

SET ffxGlow "0"
SET ffxSpecial "0"

---

### Post by imattacus on 2009-05-27
OK thanks I will try this to see if it makes a difference (fingers crossed) and I didnt mean to post my relamlist with my config by the way :lolflag:

---

### Post by asdfoo on 2009-05-27
> **imattacus said:**
> OK thanks I will try this to see if it makes a difference (fingers crossed) and I didnt mean to post my relamlist with my config by the way :lolflag:

if it doesn't work, tell us which video card and drivers you have (glxinfo prints that info)

---

