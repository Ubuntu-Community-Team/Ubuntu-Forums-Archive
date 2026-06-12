---
title: "Ubuntu Doesn't Boot"
date: 2011-06-19
forum: Server Platforms
---

### Post by faraz.yashar on 2011-06-19
I'm almost positive that this has something to do with some missing boot nonsense on the drive.(Grub perhaps?)

I installed 11.04 server on a computer with two drives.  I have not set the hardware to define a master and slave.  One drive is 160 GB (sda); the other is 120 GB. (sdb)  I formated both using GParted to ext4. The BIOS knows to check the 160 for booting info first.

Ubuntu installation began, and all went well.  I used the guided partition option with LVM to set up a partition of 32 GB on sda for the installation.  Then I installed grub as no previous OS was installed.

Upon booting, the computer runs through bios and hangs at a blinking cursor as if it couldn't find a device to boot from: I figure no drive on the computer contains the magic needed to get things rolling.

---

### Post by TechSupportx86 on 2011-06-19
Are you sure GRUB is installed on the 160 and not the 120? Since the hardware isn't setup for master/slave it's possible the ubuntu installer decided the 120 was going to be sda and 160 to be sdb and installed everything there (BiOS has no say here).

If you can, open the one-time boot menu (usually F12 or F9) and try booting from the 120 (if you haven't already).

---

### Post by faraz.yashar on 2011-06-19
I just ran the installation on one of the drives alone, and then added the other drive to the set up.  That seemed to take care of things.

---

