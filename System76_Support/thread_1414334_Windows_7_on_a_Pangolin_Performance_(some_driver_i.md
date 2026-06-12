---
title: "Windows 7 on a Pangolin Performance (some driver issues)"
date: 2010-02-23
forum: System76 Support
---

### Post by malachias on 2010-02-23
I'm trying to dual-boot linux and win7 on my (pretty) new pangolin performance, and almost everything works out of the box. However, there are a few important issues.

First, it says that my display driver is correct and up to date "Generic non-PnP Monitor" by microsoft, 6.1.7600.16385 released on 6/21/2006. However, it does not seem to support the screen's native resolution of 1600x900 (the highest the display settings allow me to go is 1280x800)

Second, scrolling using the touchpad does not seem to work - I may have overlooked some settings on this one however.

Finally, the fingerprint scanner does not have a driver, and nor do two identically named "Base System Device"s

Of these I really only case about the resolution, and scrolling to a lesser extent, but answers to all would be nice. Thanks!

---

### Post by gamerchick02 on 2010-02-23
Open up your device manager and see if you have un-detected devices.

Right click on the devices, connect to the internet, and get the drivers for them.

Do you have an ATI or a nVidia graphics card?  You will have to get the specs from the System76 site and then grab the drivers from the correct manufacturer.

I had this same problem with Win7 on my Panp5.

I have not gotten the fingerprint scanner to work yet.

Amy

---

### Post by Noah0504 on 2010-02-23
> **malachias said:**
> Finally, the fingerprint scanner does not have a driver, and nor do two identically named "Base System Device"s

[http://ubuntuforums.org/showthread.php?t=1412903](http://ubuntuforums.org/showthread.php?t=1412903)

That hopefully will take care of the base system devices.

[http://www.synaptics.com/support/drivers](http://www.synaptics.com/support/drivers)

That should take care of the touchpad.

---

### Post by malachias on 2010-02-23
Thanks for the tips!

Turns out there was a bit of a hitch with the video drivers as System76 has switched the graphics cards in Pangolin Performances from nvidia to ATI but I got the right drivers eventually :)

*sigh* I would kill for lspci and the like in Win - still, new games are new games, what can you do hehe

---

### Post by gamerchick02 on 2010-02-26
I'd like lspci and the like on Windows as well.  Too bad Windows isn't as easy to use as Linux is!  ;)

Glad you got the drivers ok.

Amy

---

