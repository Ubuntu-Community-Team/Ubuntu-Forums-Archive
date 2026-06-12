---
title: "Hibernate won't work"
date: 2015-04-08
forum: Ubuntu Studio
---

### Post by lucmorizur on 2015-04-08
Hi;

I'm very new to Ubuntu Studio. I performed a search for "hibernate" in posts titles of Ubuntu Studio forum, and didn't find any match.

I'm using a Dell Latitude E6420 laptop. It is provided for me by my job and is using Win7 for professional needs. Previously I installed XUbuntu on it with a dual boot, and hibernate under Ubuntu was working. Then I determined that the best flavour of Ubuntu for me would finally be Ubuntu Studio, and in the same time I decided to implement the very good idea that was given to me, to be able to boot Ubuntu only when a dedicated USB key was inserted.

That's my current situation now: no more dual boot on the system (Win7 starts normally without any choice, if no USB key is plugged in), but if the dedicated USB key is in, the booted system is Ubuntu Studio by default (14.04 at the time this message is written; of course a GRUB choice can allow me to boot something else: CloneZilla, Win7...).

The issue is that now hibernate doesn't work any more under Ubuntu Studio. (It's OK with Win7.) I structured the hard drive the same way as with my previous Ubuntu installation: a 5 GiB swap partition is present, and the system has "only" 4 GiB RAM. I installed pm-utils package. pm-suspend command works fine. Win7 and Ubuntu don't share anything at all on the hard drive. A precision: as for the installation of the Ubuntu boot on the USB key, I mapped the /boot folder on the 5 GiB ext2 partition of this USB key, on which is the "boot" flag.

Something which I find strange, is that GParted tags the swap partition as "swap-suspend" while I feel it should be tagged "swap-linux" (see screenshot attached).

Well, maybe I'll try some of the threads I suggest in this (long :? ) message: format swap partition so it's tagged as "swap-linux"; or reinstall everything with /boot folder on hard drive instead of being on the USB key :( ...

In the meanwhile, many thanks to anyone giving idea(s) :) .

Thanks for reading until here :P !

--
*Luc*

---

