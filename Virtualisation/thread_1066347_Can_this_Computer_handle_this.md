---
title: "Can this Computer handle this?"
date: 2009-02-10
forum: Virtualisation
---

### Post by fr0sty on 2009-02-10
Hello all!

My parents have an older Hp Pavilion a250n from 2003 that i have installed Ubuntu 8.04 on. They want me to reinstall XP home but I would like to see if the computer would be capable of running XP under Virtualbox would work instead. Here are the specs of the computer (i am considering making the total ammount of RAM to be 1.5GB):

Pentium 4 / 2.60 GHz with HyperThreading Technology 800 MHz front side bus
1.5GB of PC2700 DDR SDRAM 
nVidia Geforce4 MX 440 (Is this video card good enough?)
      8x AGP card
      Up to 64 MB DDR video
      TV-Out
 120 GB HDD

HP's specs on the comp: [http://h10025.www1.hp.com/ewfrf/wc/document?lc=en&dlc=en&cc=us&docname=c00024879](http://h10025.www1.hp.com/ewfrf/wc/document?lc=en&dlc=en&cc=us&docname=c00024879)

Is this computer too old to handle Virtualizing XP? Or could this be done without too much sacrificing of performance? We don't use Xp for anything besides itunes, Office 2007, and other minor programs. The main reason why I would like to virtualize is to help prevent the amount of damage done by viruses last time. It rendered the computer useless. This way we still have reliable Ubuntu there in case of Xp failure and it is a lot safer than what it used to be. I have tried with converting them over to Linux completely, but they want those programs that Linux doesn't run so well. Oh and Wine is outa the question.

Thank you anyone who reads and gives any advice on this.

---

### Post by HotShotDJ on 2009-02-10
> **fr0sty said:**
> 1.5GB of PC2700 DDR SDRAM This is the only thing that I can see that might slow things up.  But then again, it might be sufficient for what they want to do.  Make sure that you only assign a maximum of 50% of the available physical RAM to the Virtual Machine.  If you are planning on buying more RAM anyway, consider increasing it to a full 2 Gig.  Then you will have no trouble at all with VirtualBox running on Ubuntu 8.04 & VirtualBox on that system.

I also recommend that you use the full PUEL version rather than the OSE version that comes in the standard Ubuntu Repositories.  That way, you'll have USB support (for things like an external hard drive, flash drive, and/or USB printer).  See [http://ubuntuforums.org/showpost.php?p=6398716&postcount=1](http://ubuntuforums.org/showpost.php?p=6398716&postcount=1) for complete instructions on how to install VirtualBox with USB support.

---

### Post by fr0sty on 2009-02-10
Thank You very much. The OSE version isn't that great without the USB support. I love Virtualbox because I'm able to run Windows 7 beta quite smoothly on my comp. My comp is way newer (custom built with Ubuntu 8.04 replacing Vista) than my parents comp. (Oh and the beta is def not as good as Ubuntu.) Your help has been amazing as this really made my day. Thanks!

---

### Post by HermanAB on 2009-02-10
I've run XP on Virtualbox on an Eee PC 701.  That machine of yours will do fine.

Cheers,

Herman

---

