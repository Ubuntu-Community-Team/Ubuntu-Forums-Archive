---
title: "IE and Activex controls"
date: 2011-02-16
forum: Wine
---

### Post by DavinA on 2011-02-16
OK, maybe I'm missing something, or it's just not possible, but I'm having trouble accomplishing this:

I need to get a 32 bit version of IE running on my Ubuntu 10.10 (Wine 1.2) box AND install an activex control.  The activex control is called WebCamX.cab and I need it to remotely access our surveillence system. Unfortunately, our system only supports 32bit IE.  The cams cannot be remotely viewed under any other browser.

I tried IEs4linux, but couldn't get it to install since wineprefix* is deprecated.  I'm installing IE 6 & 8 via winetricks now, though I don't have much hope. I've already installed IE7 via winetricks, and though it runs ok, it won't install the activex control.  I've even tried manually downloading the control, extracting with cabextract, and tried manually installing, with no apparent luck.

Any tips, tricks, ideas would be greatly appreciated. Perhaps there are some libraries which need to be overridden?

NOTE: I do have access to a XP Install CD, but my system does not have the space for a dual boot, nor the resources for a VM.

---

### Post by DavinA on 2011-02-16
Well, I take back the part about IE6....

Winetricks won't install it since IE7 is already on. IE8 is downloading/installing now.

---

### Post by DavinA on 2011-02-16
Couldn't even get IE8 to run right until I added the registry value DWORD HKCU\Software\Microsoft\Internet Explorer\Main named TabProcGrowth value 0.  But alas, no luck with IE8 either.

Managed to get IE6 installed by uninstalling 7&8 via Wine uninstall software first (derp!). But, somewhere along the line, the DVR server crashed, and I can't access it till tomorrow, so I'm done for tonight.  I'll check back tomorrow, hopefully I'll (PLEASE LORD PLEASE) find some advice. ;)

---

### Post by bmullan on 2011-03-08
> **DavinA said:**
> OK, maybe I'm missing something, or it's just not possible, but I'm having trouble accomplishing this:

I need to get a 32 bit version of IE running on my Ubuntu 10.10 (Wine 1.2) box AND install an activex control.  The activex control is called WebCamX.cab and I need it to remotely access our surveillence system. Unfortunately, our system only supports 32bit IE.  The cams cannot be remotely viewed under any other browser.

I tried IEs4linux, but couldn't get it to install since wineprefix* is deprecated.  I'm installing IE 6 & 8 via winetricks now, though I don't have much hope. I've already installed IE7 via winetricks, and though it runs ok, it won't install the activex control.  I've even tried manually downloading the control, extracting with cabextract, and tried manually installing, with no apparent luck.

Any tips, tricks, ideas would be greatly appreciated. Perhaps there are some libraries which need to be overridden?

NOTE: I do have access to a XP Install CD, but my system does not have the space for a dual boot, nor the resources for a VM.

I've been using CodeWeaver's custom Wine tools and they run a lot of software that the generic Wine doesn't -or- doesn't do easily.   You might want to check their web site.   Their software is well worth the little they charge for it.

I also just checked and I using CodeWeaver's apps I have Internet Explorer 8 installed and running on my ubuntu 10.10 system.
[http://www.codeweavers.com/products/](http://www.codeweavers.com/products/)

---

