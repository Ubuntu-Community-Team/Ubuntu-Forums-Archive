---
title: "N Router USB Adapter driver on Starling"
date: 2009-11-08
forum: System76 Support
---

### Post by Teasdale on 2009-11-08
I have a Netgear N Wireless router, which means my Starling with its b/g card, has a hard time connecting.

I purchased a Netgear Rangemax Wireless-N USB 2.0 Adapter (WN111) adapter, but it has to install something via the software CD. That shouldn't be a problem, but the external CD drive I bought to go with the Starling appears to be dead.

I thought I might install the software by loading the CD to my USB flash/thumb drive, but the Starling won't run the autorun exe file from the thumb drive. Is there some sequence of process I need to do to install the software (probably a driver) to make the USB adapter work? Or is the driver probably only for Windows? Neither the box nor the instructions specify Windows, but maybe it's assumed.

I see that others have had this problem before me. 
[http://www.computing.net/answers/linux/connect-my-wn111-rangemax/30304.html](http://www.computing.net/answers/linux/connect-my-wn111-rangemax/30304.html)

[http://ubuntuforums.org/showthread.php?t=859481](http://ubuntuforums.org/showthread.php?t=859481)

[http://ubuntuforums.org/showthread.php?t=807225](http://ubuntuforums.org/showthread.php?t=807225)

[http://georgia.ubuntuforums.org/showthread.php?t=893879&page=2](http://georgia.ubuntuforums.org/showthread.php?t=893879&page=2)

---

### Post by jml on 2009-11-08
You should be able to connect to your router without resorting to a USB dongle.  Go into the setup application of your router and configure it for a mixed environment, (802.11g/n etc.)   It may come set up for .n only by default.  Most routers will usually allow you to access the set up routines by connecting via CAT 5 cable and then typing in a url into your web browser.  Your router's documentation should give you the specifics.

With regards to your optical drive.  It may not be dead.  First see if it is recognized by your Starling when it's plugged in.  Go to places>computer and see if it is listed.  If it is, then try to play a music CD in it.  If it plays then you know that the drive is OK.  When you say that the drive will not run the ".exe" file, that suggests to me that you are trying to run a Window's application.  Ubuntu cannot run Window's applications out of the box.  And, yes, Teasdale, unless Linux, or Mac OSX is specified, you can assume that the software is probably Window's specific.

Hopefully, my first suggestion will get you connected.  Good luck.

Joe

---

### Post by Teasdale on 2009-11-15
I solved my problem.

I wanted a laptop so I could work in bed. I returned the USB adapter; there was a very helpful guy at the store who suggested I use a "Powerline Ethernet Switch." One unit plugs into my router and an electrical outlet; the other unit plugs into an outlet behind my bed and there's an ethernet cord from it that I plug into my Starling. The two units communicate wirelessly. *It works*. There was no software set-up. I can now take my Starling to bed and work into the wee hours. :)

---

