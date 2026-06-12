---
title: "Lost data recovery in elementary 0.4 luki, ubuntu 16.04 LTS"
date: 2016-11-07
forum: Ubuntu/Debian BASED
---

### Post by prashantshukla003 on 2016-11-07
I installed elementary 0.4 luki over Windows 7. Unfortunately I lost all my drives' data. Please suggest me an app to recover my lost data.

---

### Post by Bucky Ball on 2016-11-07
Welcome. Testdisk may be your best shot. Download and create bootable media with the [SystemRescueCD]("http://www.system-rescue-cd.org/Download"). Testdisk is on that along with a lot of other useful recovery tools.

Get SystemRescueCD on USB or CD and boot to that. You'll get to a desktop where you can run testdisk.

The most important things is *do not use the disk you are trying to recover data from for anything but recovering data*. In other words, only boot from live media (SysResCD, Ubuntu 'live' session from 'Try Ubuntu'). The more you use the disk the less chance you have of recovering the deleted data on it (because the data is not actually deleted, but its location is marked as 'writable' so when you use the disk there is a very real chance you will write new data over the old).

Too late now, but worth remembering for the future: always keep reliable back ups of anything you don't want to lose. This goes for any time, but especially when you do something like install an OS, whether you're familiar with the process or not. ;)

Good luck.

---

### Post by howefield on 2016-11-07
Thread moved to the "*Ubuntu/Debian BASED*" forum.

---

