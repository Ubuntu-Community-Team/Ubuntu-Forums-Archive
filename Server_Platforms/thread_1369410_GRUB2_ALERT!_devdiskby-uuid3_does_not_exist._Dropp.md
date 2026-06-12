---
title: "GRUB2: ALERT! /dev/disk/by-uuid/3 does not exist. Dropping to a shell."
date: 2009-12-31
forum: Server Platforms
---

### Post by bprof on 2009-12-31
I finished installing ubuntu 9.10 on a box rebooted after the installation and got this error

ALERT! /dev/disk/by-uuid/3.. does not exist. Dropping to a shell.

I have enabled
GRUB_DISABLE_LINUX_UUID=true

In /etc/fstab

I've changed the UUID to /dev/sdX

But both did not help, the error is still showing.

Anyone have any idea how to get rid of it?

Thanks

---

### Post by bprof on 2009-12-31
Pressing shift to get to grub menu and changing the UUID to /dev/sdX did not help. The message changed to 

ALERT! /dev/sdX does not exist. Dropping to a shell.

Now the thing is if I use Ubutnu CD as a resuce CD it shows /dev/sdX it allows me to use it. Why grub2 can't see it? is puzzling me.

---

### Post by dbcoolio on 2010-02-08
I just got this problem on my EEEpc 900A, and I think I got it working, but it may be a temporary fix. 

I booted up with a live CD, and I found that I could still read the partition fine, but it no longer had a UUID.  I then tried editing the line on grub so that instead of the ROOT=UUID- part it read ROOT=DEV=/dev/sda1

With that I was able to boot up fine, so I changed my /etc/fstab to also use /dev/sda1 instead of the UUID.  It now seems to be working, and ls -l /dev/disk/by-uuid/ is showing the original UUID again.

---

### Post by adam814 on 2010-02-09
Ubuntu uses UUIDs for a reason.  If the disk ordering changes on the system (I've heard of some BIOSes deciding almost randomly which disk is /dev/sda and which is /dev/sdb) you won't be able to boot.

---

