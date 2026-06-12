---
title: "RAID 5 : How do you prevent it to start if it is degraded?"
date: 2009-07-03
forum: Server Platforms
---

### Post by bshagnasty on 2009-07-03
The great advantage of a RAID-5 array is that if one drive in your array fails, you can still continue to read/write without any problem. Later you just add a drive and rebuild the array (takes about 6 hours with cpu util ~100%).

I have a Mac pro, with 4 1TB drives. Within OS X, I run ubuntu as a virtual machine. I've configured Virtualbox to expose those drives *directly* to ubuntu (the mac has no access to them). However, *sometimes* when I startup the machine and subsequently start the virtual machine, mdadm thinks that /dev/sda is missing and goes ahead and starts the array as "degraded" with 3 drives.

I can correct this situation by issuing:

mdadm --manage /dev/md0 -a /dev/sda

later on and it will "recover" the degraded array.  The recovery is long and tedious (mainly because it pegs the CPU all the way to 100%, makes it run hot and probably heats up the hard drives as well).


I wanted to know if there is any config parameter that would *PREVENT* the array from starting up if a drive was missing (hopefully the monitor mode would still work notifying me of the problem, which I can later fix and not have to go through a recovery).

I highly appreciate any suggestions!

---

### Post by fjgaude on 2009-07-06
I'm not sure what's going on but usually when a drive is dropped from an array and then can later be added back, we have a UUID situation. Likely the array UUID that shows in the **/etc/mdadm/mdadm.conf** file is not the one showing for /dev/sda.

Run these and compare:

```
sudo mdadm -E /dev/sda
```

and

```
sudo mdadm -D /dev/md0
```

assumming the array is md0.

Notice the UUID shown for each. If they are not the same then you might wish to zero the superblock for sda and then add it back. Understand?

---

### Post by bshagnasty on 2009-07-06
Yes, sir! Understood.  I will compare and report. If it is indeed a UUID problem, I can fix the problem at the root.   But still, it would be nice to have mdadm not start the array if drives are missing (so that it would not get in to a degraded state and avoid the 600min rebuild with lotsa heat as a bonus).  Thanks for your suggestion, I really appreciate it!

---

### Post by fjgaude on 2009-07-06
It would be nice, I guess! Severs don't get re-booted often. They run and run. You can always use the **mdadm** stop command to not have it run. It whole idea when a drive fails is to have the array keep on running. That's RAID in action.

Good luck with what is going on with your setup and drives.

---

