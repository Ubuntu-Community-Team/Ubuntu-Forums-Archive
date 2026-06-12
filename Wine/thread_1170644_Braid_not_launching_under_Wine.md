---
title: "Braid not launching under Wine"
date: 2009-05-26
forum: Wine
---

### Post by Bohemenian on 2009-05-26
I'm trying to get Braid working under Ubuntu 9.04 and Wine 1.0.1. 
I have downloaded Braid through Gamersgate and installation runs no problem. But when trying to launch the game, the process kicks at it for a couple of seconds at most, then just dies.
When trying to launch through the terminal, I get the following output:
fixme:mixer:ALSA_MixerInit No master control found on HDA ATI HDMI, disabling mixer
fixme:system:SystemParametersInfoW Unimplemented action: 59 (SPI_SETSTICKYKEYS)
fixme:system:SystemParametersInfoW Unimplemented action: 53 (SPI_SETTOGGLEKEYS)
fixme:system:SystemParametersInfoW Unimplemented action: 51 (SPI_SETFILTERKEYS)

Now the I don't really know what to do with this, but my best bet was that someone around here does :D

---

### Post by hikaricore on 2009-05-26
Never heard of it.
Here's the appdb page incase anyone's posted anything useful there: [http://appdb.winehq.org/objectManager.php?sClass=application&iId=9535](http://appdb.winehq.org/objectManager.php?sClass=application&iId=9535)

---

### Post by asdfoo on 2009-05-26
Just use a more recent version of Wine than 1.0.1.  [http://winehq.org/download](http://winehq.org/download)

---

### Post by Bohemenian on 2009-05-27
Ok, I updated Wine, but that alone didn't do it, I still get the same error output. Although I did find this at WineHQ

> did not work: 

 bmonkey@burning-studio:~/Download/Braid$ env WINEPREFIX=/home/bmonkey/winebottles/Braid wine "C:\Braiddemo\braid.exe" 
fixme:system:SystemParametersInfoW Unimplemented action: 59 (SPI_SETSTICKYKEYS) 
fixme:system:SystemParametersInfoW Unimplemented action: 53 (SPI_SETTOGGLEKEYS) 
fixme:system:SystemParametersInfoW Unimplemented action: 51 (SPI_SETFILTERKEYS) 
 bmonkey@burning-studio:~/Download/Braid$  

did work perfectly: 

 bmonkey@burning-studio:~/winebottles/Braid/drive_c/Braiddemo$ env WINEPREFIX=/home/bmonkey/winebottles/Braid wine braid.exeThis seems like my problem and a solution, but I don't understand what he does in his solution, really. I have no winebottles directory. I would greatly appreciate if anyone could "translate" this for me.

---

### Post by rasmus_ on 2009-05-27
You can have several "C-drives" and configurations of wine in your system. The default one being ~/.wine

Some people create a new one for each new application since wine tend to trash the entire drive if the installation is faulty.

```
env WINEPREFIX=/home/bmonkey/winebottles/Braid
```

Simply tells wine to use the installation residing in a particular directory. If you didn't use it during installation you shouldn't use it when you run your application.

I guess the difference between the two lines is the working directory; in the first line the application is launched from some other directory. In the second line the application is launched from its installation directory.

---

### Post by asdfoo on 2009-05-27
yeah, if you read the Wine FAQ it tells you to cd into the install dir first.

---

### Post by Bohemenian on 2009-05-27
Here's something else i read in the appdb 
> **What does not** (work)
 Playing on an ati graphic card.      
   I tried the game on both my laptop with an nvidia graphic card and my desktop with an ati graphic card.     
    I even got the errors about my display driver myself, so I'm gonna drop this particular game until Jonathan Blow releases a Linux-version.
But thx for the assistance. I'm starting to learn my way around wine, and I'll make sure to have a second look in the FAQ and the appdb next time ^^

I was almost about to submit this post with a little comment about how gold rating was somewhat high for this game, even though it was my first experience with Wine, when I noticed someone rated it garbage at the appdb. Phew, now I know gold apps doesn't mean that the program won't start :D

---

### Post by chiquitin on 2009-10-10
I have no problem launching it. The only thing that doesnt work for me is video. I can hear the music. Even hear when he jumps when I press spacebar. But I just see a black screen. Im using Wine 1.1.30

---

