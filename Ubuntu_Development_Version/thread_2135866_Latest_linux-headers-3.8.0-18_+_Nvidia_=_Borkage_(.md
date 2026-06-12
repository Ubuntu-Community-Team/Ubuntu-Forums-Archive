---
title: "Latest linux-headers-3.8.0-18 + Nvidia = Borkage (Again)"
date: 2013-04-15
forum: Ubuntu Development Version
---

### Post by victor9098 on 2013-04-15
Just got the latest linux-headers-3.8.0-18 update. After a restart Grub launches, if I choose Ubuntu (its either that or a memory test) I get a screen of jumbled text and nothing else happens. Do a hard shutdown, grub launches again and use the advanced options to pick the previous kernel and everything back to normal.

Using the Nvidia 310 updates repo.

At least they are being consistent this cycle :-D

UPDATE - Removing the Nvidia repo and using the default Xorg graphics lets the system boot up normally.

UPDATE - [Bug #1169325]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-310-updates/+bug/1169325") reported. Reported against the nvidia repo, but maybe it should be the kernel? There was also a 310-updates update.

---

### Post by mloebl on 2013-04-16
It seems to have taken out my NVIDIA HDMI Audio as well (both with the 310 and 319.)  Spent a bit of time digging into it last night before bed, will look later today when I get home.

-Mike

---

### Post by tdockery97 on 2013-04-16
It did the same to my ATI proprietary graphics driver.  The first reboot after the updates it just crashed.  I rebooted again and it reverted to the opensource Gallium driver.  I reinstalled the ATI driver using the Additional Drivers function and it reinstalled perfectly.  First time I've been able to recover from a graphics borkage so easily.

---

### Post by victor9098 on 2013-04-16
Reinstalling 13.04 right now. Grub kept launching on start-up. Tried the boot repair tool but no joy. System would not turn off or restart either, monitor would switch off but box would stay on indefinitely so had to do hard shut downs. The last three kernel updates have been a nightmare.

---

### Post by kurt18947 on 2013-04-16
I must be living right, or my kindly disposition toward penguins is paying off.:)  The only Nvidia issue I've had in the last month with 13.04 is very infrequent refusal to awaken from suspend. I get a flashing cursor and that's it.  A hard reset fixes restores normal function and I can see no rhyme nor reason.  I suspect the frequent updates and packages that are not in sync may have something to do with it.

---

### Post by pqwoerituytrueiwoq on 2013-04-16
no issues here, but i am using xorg edgers
[[IMG]http://i.imgur.com/Ea9W9Mts.png[/IMG]]("http://imgur.com/Ea9W9Mt") - xfwm4 is working
[[IMG]http://i.imgur.com/aqwOxHes.png[/IMG]]("http://imgur.com/aqwOxHe") - compiz is working
using latest kernel (not using the proposed source)

edit: no hdmi audio in volume control, i use analog audio by my tricking the tv into thinking i am using dvi
edit: i used to get odd beeps from my tv that were barley audible, i no longer have these beeps now :)
when this audio gets fixed i need to know how to break it like this

---

### Post by victor9098 on 2013-04-16
Just did a fresh reinstall, never bothered with the nvidia repos, left the 'proposed' unchecked and after updating to the latest kernel I am back to the grub screen on boot and the computer refusing to turn off. :confused:

---

### Post by mloebl on 2013-04-16
I just rolled back to 3.8.0-17 and HDMI Audio works fine.  I will probably put in a bug if there isn't one already.

EDIT:  Bug started for HDMI Audio, will gather some more details soon [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1169761](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1169761)

---

### Post by victor9098 on 2013-04-17
I am getting some strange behaviour. Restarting the computer usually causes it to freeze on shutdown. Shutting down seems to work. But when I boot up the Bios screen launches, then the plymouth Ubuntu screen...then it jumps back to the Bios screen, grub launches, Ubuntu is the only option to choose, then the system starts as normal.

---

### Post by Harry33 on 2013-04-18
A new kernel v. 3.8 is available from RR repos now (3.8.0-19.29).
That is based on mainline 3.8.8.

Here:
[https://launchpad.net/ubuntu/raring/+source/linux/3.8.0-19.29](https://launchpad.net/ubuntu/raring/+source/linux/3.8.0-19.29)

---

### Post by victor9098 on 2013-04-18
Yeah, updated and tried with the Nvidia 310 repo. Borkage ensued. Rolled back to an older kernel, and went back to the standard xorg driver. Back to normal now, though obviously without any Nvidia repo's.

---

### Post by Rukiri on 2013-04-18
Try kernel 3.9, seems to work for me, 3.8.7 works as well (when compiled not from ubuntu sources).

---

