---
title: "Run WoW on Ubuntu"
date: 2010-11-16
forum: Wine
---

### Post by Arkentos on 2010-11-16
Ok, i have World of Warcraft installed on my PC, Ubuntu is running great, wine installed and working just fine, but when I run WoW, it runs REALLY slow, so i checked about the direct rendering and it says NO, so how can I make it to say YES?

I have a GeForce FX 5200 128 MB graphic card if that helps somehow?

---

### Post by WorMzy on 2010-11-16
Don't run it myself, but have you checked the Howto on this page: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=20549&iTestingId=58605]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=20549&iTestingId=58605")?

Also, make sure you've installed propriety drivers (under System -> Administration -> Hardware Drivers) for your graphics card.

---

### Post by Arkentos on 2010-11-16
My WoW runs ok, i can log in, and play a bit, but a bit slow, and some of the texture isnt showing at all?
I just wanna know how can i make direct rendering say YES instead of NO, how can I support it?
Does something need to be installed or?

---

### Post by Kyrue on 2010-11-16
check out Cedega Gaming Service. It's pretty much guaranteed to work.

---

### Post by doctorzeus on 2010-11-16
> **Arkentos said:**
> Ok, i have World of Warcraft installed on my PC, Ubuntu is running great, wine installed and working just fine, but when I run WoW, it runs REALLY slow, so i checked about the direct rendering and it says NO, so how can I make it to say YES?

I have a GeForce FX 5200 128 MB graphic card if that helps somehow?

WOW due to popular demand and support basically should run fine on Linux, your graphics card could be better as its best to have a one-up on the normal Windows system requirements for a game when running on wine...have you tried turning the performance settings down as well as turning off any post-processing settings (wine doesn't cope well with it from my experience). Do you have the latest graphics drivers along with the recommended dll's for the game?

Also like WorMzy said update your graphics driver, although the actual manufacturers websites are usually better cause they may have more up-to-date versions...

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=1922](http://appdb.winehq.org/objectManager.php?sClass=application&iId=1922)
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=14154](http://appdb.winehq.org/objectManager.php?sClass=version&iId=14154)

Doctorzeus

---

### Post by doctorzeus on 2010-11-16
> **Kyrue said:**
> check out Cedega Gaming Service. It's pretty much guaranteed to work.

Not exactly, you can never "Guarantee" that any Windows game will work on any Linux Distro with Cedega... :popcorn:

> 
Quote From YokoZar:

This is not true at all. Wine has full DirectX 9 support. (ActiveX is something different entirely.)

Try Wine first. There are many programs (games included) that work better in Wine, and many don't even work at all in Cedega. Wine is developing at a faster rate than Cedega too, so the things that are in Wine's favor are only to get even more in Wine's favor as time goes on. Wine's also free.


The fun of Linux is gaining and using the knowhow to get these games to work anyways :)

Doctorzeus

---

### Post by cwwilson721 on 2010-11-16
Rather than making the OP PAY to run WoW (Heck, it's already $15/month), DON'T recommend Cedega.

WoW runs GREAT in wine. But you need a few basic things:
[LIST]
[*]Install/run fusion-icon, so you can easily disable Compiz (NEVER run Compiz while running WoW)
[*]Install your proprietary drivers for Nvidia (In 10.10, System > Administration > Additional Drivers). No need to install the ones from Nvidia, because your old card doesn't use the newest anyway
[*]Run WoW in wine in Windows XP mode (Or sound can get borked, and updates actually seem to work. Use Applications > Wine > Configure Wine)
[*]While in Configure, make sure your sound is set to ONLY use alsa.
[*]Run WoW in opengl mode. Either edit your config.wtf, and add the line "SET gxApi=opengl" or, as I do, add "-opengl" to the end of the launch command
[/LIST]

If you follow these recommendations, you should be running WoW fine. If you don't, be prepared for alot of frustration.

Good luck, and if you need help with any of those steps, they are ALL well covered in the forum (Just use the forum search. It's your friend)

---

