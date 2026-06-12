---
title: "wifi with wpa-psk"
date: 2008-08-28
forum: System76 Support
---

### Post by chuckdowning on 2008-08-28
I have a Pangolin version 3, which I purchased about 3 months ago.  Because ubuntu 8.04 kept crashing at that time, I have installed kubuntu 8.04 and have the latest updates.  I have tried everything I could find to get my NetGear wireless router talk to my System76 computer, using wpa-psk security.  Nothing seems to work--in fact I have locked up the computer twice, once with ndiswrapper; again by disconnecting my ethernet cable.  Where can I look now?

BTW, a simple Asus PDA works wirelessly out of the box with the NetGear router.

Thanks,

Chuck Downing
Highlands Ranch, Colorado

---

### Post by thomasaaron on 2008-08-29
Do you have knetworkmanager and wpa supplicant installed?
[http://kubuntuforums.net/forums/index.php?topic=5876.0](http://kubuntuforums.net/forums/index.php?topic=5876.0)


Looks like there are traditionally problems between kubuntu and wpa-psk...
[http://www.sharkyforums.com/archive/index.php/t-288228.html](http://www.sharkyforums.com/archive/index.php/t-288228.html)

---

### Post by chuckdowning on 2008-08-29
1. I have an up-to-date version of Kubuntu 8.04

2. FL91

3. I tried ndiswrapper with one of the Windows .ddls from the System76-supplied Driver Disc that came in the box.  This locked the machine on reboot so that I had to reinstall kubuntu.

I tried following several recommendations I found with Google, based on knowing that I have an Intel 4965 controller.  That, too, resulted in a lock-up at reboot.

I am about to try the above suggestions.

---

### Post by thomasaaron on 2008-08-29
You should not have to use ndiswrapper for anything on your laptop, including wireless. If it is still installed, it probably will interfere with knetworkmanager and wpa-supplicant. Ubuntu supports the 4965 card out of the box.

---

### Post by chuckdowning on 2008-08-29
Fantastic!!!

The document referenced at wlug.org.nz made everything work flawlessly.

Note: I had to disconnect my wired connection to enable the wireless one.  The next test will come in a few weeks while we are travelling.

Again, thomasaaron, thanks a bunch. :popcorn:

---

