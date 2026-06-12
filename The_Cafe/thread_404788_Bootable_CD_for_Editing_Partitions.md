---
title: "Bootable CD for Editing Partitions?"
date: 2007-04-08
forum: The Cafe
---

### Post by cmillican on 2007-04-08
I have a Zune from before I switched to Ubuntu about 2 months ago. I was a power user on Windows and I'm learning quickly on Linux. I would like to install Windows on a separate partition than my Ubuntu, but I need a way to edit them. I would like to take out 10 GB from my main partition and free space up so I may install Windows. Does anyone know a good, free bootable CD program that would allow me to do this?

Thanks,
Chris

---

### Post by maniacmusician on 2007-04-08
[GParted]("http://gparted.sourceforge.net") has a live CD that's entirely based around partitioning. 

I should warn you, if you install Windows after you install Linux, Windows will hijack your bootloader and leave you without access to your Linux partition. At this point, you'll have to use a linux-based LiveCD to reinstall the GRUB bootloader to your hard drive, and this may qualify as an "advanced" or "expert" task for some people. Just giving you a heads up. This is why it's generally recommended that Windows be installed first, and then Linux.

---

### Post by strabes on 2007-04-08
Here's how to restore grub after installing windows: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by cmillican on 2007-04-08
Ok, thanks y'all. I'll look into those and decide whether or not I want to go Windows first.

---

