---
title: "Downgrading to Win7"
date: 2013-12-06
forum: Windows
---

### Post by dieseler01 on 2013-12-06
I bought the following computer [http://h10025.www1.hp.com/ewfrf/wc/document?cc=us&lc=en&dlc=en&docname=c03518194#N726](http://h10025.www1.hp.com/ewfrf/wc/document?cc=us&lc=en&dlc=en&docname=c03518194#N726) on a pretty good deal, and it came with Win8 installed.    I tried out Win8 for awhile and never could come to like it. So I decided to downgrade to Win7 along with dual booting Ubuntu.

Well, after a bit of work and searching I have everything working except the wireless/bluetooth combo card.  It's based on a BCM43228 wireless and BCM20702A0 bluetooth but of course is HP propiety card and they only offer Win8 drivers that won't install on Win7.   Any ideas where I can find Win7 drivers for this thing?  I really hate to go buy a new wireless card just for Win7!

---

### Post by electrohandyman501 on 2013-12-06
I'd hate to say, if the mfgr didn't write drivers for it, not sure who else would. 
If the win 7 generic drivers don't cut it then I think your only option would be to replace it with one that is win 7 compatable.
It's a risk of trying to use old software on hardware that wasn't designed for the backward compatability.

---

### Post by varunendra on 2013-12-06
It shouldn't matter where the driver comes from. If it supports the card and is meant for the OS version in question, it should work. As such, I think this one from lenovo should work for you : [http://support.lenovo.com/en_IN/downloads/detail.page?DocID=DS036171](http://support.lenovo.com/en_IN/downloads/detail.page?DocID=DS036171)

(although I hate that ridiculous download size. I'm sure the useful content size is not more than 2-4 MBs in that package)

---

### Post by dieseler01 on 2013-12-07
> **electrohandyman501 said:**
> I'd hate to say, if the mfgr didn't write drivers for it, not sure who else would. 
If the win 7 generic drivers don't cut it then I think your only option would be to replace it with one that is win 7 compatable.
It's a risk of trying to use old software on hardware that wasn't designed for the backward compatability.

I realized it was a risk before I tried it.  But with a generic chipset, often other drivers can be found. (Found a Dell driver for the LAN for example).  Or generic drivers like the BCM STA for linux might be floating around,  sometimes it's just hard to get Windows generic drivers to recognize the hardware.

> **varunendra said:**
> It shouldn't matter where the driver comes from. If it supports the card and is meant for the OS version in question, it should work. As such, I think this one from lenovo should work for you : [http://support.lenovo.com/en_IN/downloads/detail.page?DocID=DS036171](http://support.lenovo.com/en_IN/downloads/detail.page?DocID=DS036171)

(although I hate that ridiculous download size. I'm sure the useful content size is not more than 2-4 MBs in that package)

WOW, that is some download size!  I'll give it a go though,  thank you!

---

### Post by dieseler01 on 2013-12-07
Success!

The problem was Win7 not recognizing the hardware.  Manually selecting the hardware from the list rather than trying to load my own worked like a champ!

---

