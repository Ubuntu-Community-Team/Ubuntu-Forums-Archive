---
title: "Ubuntu Server + Software Raid1"
date: 2007-10-08
forum: Server Platforms
---

### Post by Termina on 2007-10-08
I have two 80GB SATA drives in RAID1 software raid.

I also have an IDE drive.

Debian, this setup wasn't a problem. Ubuntu, however, is having difficulty.

/dev/hda1 is /boot, with md1 being / (and a few other md#s in there as /home, /tmp)

What I see is:

Loading, please wait...
mdadm: No devices listed in conf file were found
kinit: name_to_dev_t(/dev/md4) = md4(9,4)
kinit: tring to resume from /dev/md4
......
mount: Mounting /dev/md1 on /root failed: Device or resource busy
.....
Target filesystem doesn't have /sbin/init
...
This drops me down to (initramfs).

Anyone know why this would be happening? Rescue mode allows me to mount/chroot into the md# devices just fine.

---

### Post by ksudbury on 2007-10-08
What does "cat /proc/mdstat" show you ? 

Have you tried rebuilding the raid at all? has this problem just cropped up or has is this a fresh install? 

Also just read these steps, [http://www.howtoforge.com/linux_software_raid](http://www.howtoforge.com/linux_software_raid) and double check you have correctly configured your raid. 

Also how did you configure your raid ? what is each disk doing etc? is the raid on the two sata drives and the boot partition on the pata disk?

---

