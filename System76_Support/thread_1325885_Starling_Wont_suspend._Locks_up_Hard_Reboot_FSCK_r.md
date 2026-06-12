---
title: "Starling Wont suspend. Locks up Hard Reboot FSCK required"
date: 2009-11-13
forum: System76 Support
---

### Post by Maczimus on 2009-11-13
Hey running 9.10...just installed the new driver, however my netbook will not suspend correctly. it completely locks up. doesnt matter if i fn/f1 or set it to suspend on close lid...the hard drive stops, the screen flashes but then the mouse cursor stops and i cannot do anything except hold the power button. once i reboot it cannot mount my home partition and i have to esc and run fsck to get it to fix the errors once that is done it boots normally, 9.04 did suspend correctly but not 9.10... any suggestions?

I just went back to 9.04 and it still does not suspend correctly. Although it is not giving me the file system erros it did before it just goes to a blinking cursor on a blank screen but will not actually power down. any suggestions???

---

### Post by thomasaaron on 2009-11-16
Did you do a fresh install on 9.10. If so, you will loose your wireless functionality. The 2.4.0 System76 driver will give you short-range wireless, but the full fix isn't ready yet.

You said you went back to 9.04. How? Did you re-install, or did you just boot into the previous kernel?

Sounds like you may have done an online upgrade that was corrupted. Your best bet is probably a fresh install of 9.04 and the 2.4.0 System76 Driver. see...

[http://knowledge76.com/index.php/Restoring_Your_Netbook](http://knowledge76.com/index.php/Restoring_Your_Netbook)

---

