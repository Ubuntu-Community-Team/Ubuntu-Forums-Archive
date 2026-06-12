---
title: "The Third Time"
date: 2006-11-16
forum: Utah Team - US
---

### Post by urrybr on 2006-11-16
](*,) I have been running 5.06 on an AMD Opteron, 2-Dual-core, 6GB RAM.  We use this machine, with iSCSI to control an Overland Tape Library doing "one-off" backups of image data.  We use BRU to control the library, etc.

Two days ago, I started four backup jobs.  When I came back, yesterday, it looked like the box had gone into hibernation.  I worked with it for several minutes, to no avail.  Then I did what was possibly the dumbest thing: I reset the server.

The box wouldn't boot up.  This is the third time that I've had a crash like this.  Do you have any suggestions?  I have apps on this box that I would rather not have to reinstall with a fresh install of 5.06

---

### Post by Technoviking on 2006-11-16
Does the machine POST, does grub load, how far does it get into the boot?

---

### Post by urrybr on 2006-11-16
It gets to the splash screen.  At that point, it seems to hang, and then the splash screen goes away, and I see a massive amount of data scrolling down the screen.  The final message is that it can't execute the /sbin/getty.

---

