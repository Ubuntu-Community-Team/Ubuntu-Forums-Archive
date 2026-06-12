---
title: "Trusty point release (update) fail."
date: 2015-10-20
forum: Ubuntu Development Version
---

### Post by ventrical on 2015-10-20
Did an update/upgrade on a client's desktop and like all the ubuntu's before it, it crashed the nVidia desktop to the point where I could not get in. Being in a hurry I was able to swap out the hdd to another desktop system and it is all up  and running, jockeyed over to an Intel based graphics hardware. However I cannot pump up the resolution  so I will swap the drive out to yet another more current system. Versatility factor with ubuntu is we can swap out drives with practically zero defects but updating to the point release does obsolete out certain hardwares.  It's really a thorn in the side of user_space and for some reason it's really aggravating and I can see why new converts are discouraged really quick and want to go running back to  that other internet of bings. :(

Regards..

---

### Post by Beren Camlost on 2015-10-25
Updating X will in most cases (if not always) break the proprietary Nvidia driver. This I have come quite accustomed to and have come up with a simple and much more convenient way of recovering the system. Mind you, this happens at least every point release if you go with the hardware enablement stacks.

Boot the system into recovery mode. Hold down the Shift key to enter Grub menu if it doesn't boot into Grub menu automatically. Open a Root Session. First we need to remount / with read and write permissions:
```
# mount -o remount,rw /
```

Secondly, mount your partition scheme according to /etc/fstab:
```
# mountall
```

I always keep a copy of the Nvidia installer lying about, so I can easily recover from graphics driver breakdowns like these:
```
# cd /<path-to-Nvidia-driver-installer>
# ./NVIDIA-Linux-<architecture>-<driver-version>.run
```

Probably just old bad habit but I always reboot after a driver installation:
```
# reboot
```

Should keep future point release updates free of hdd swapping :)

---

### Post by ventrical on 2015-10-26
Thanks.

---

