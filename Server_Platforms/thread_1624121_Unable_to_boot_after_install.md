---
title: "Unable to boot after install"
date: 2010-11-17
forum: Server Platforms
---

### Post by jmast01 on 2010-11-17
I am trying to setup a computer to host network files for several users. I need to set it up with raid 1 mirroring, have two 500 GB drives. I was trying to do this with hardware raid but was unable to so. I have since installed Ubuntu 10.04 server with software raid, with the Samba file server. I get through the installation just fine. But when you start the computer it shows

mount: mounting /dev/disk/by-uuid/xxxx on /root failed: Invalid argument
mount: mounting /dev on /root/dev failed no such file or directory
mount: mounting /sys on /root/sys failed no such file or directory
mount: mounting /proc on /root/proc failed no such file or directory
Target file system doesn't have /sbin/init no init found
Try passing init=bootarg

Busybox v1.13.3
(initrmfs)

I am not sure how to correct this. I am not that familiar with Ubuntu and would appreciate any help.

---

### Post by CharlesA on 2010-11-17
How did you do the mountpoint for "/" ?

It shouldn't be /root.

---

### Post by jmast01 on 2010-11-17
When setting up the Partition I made two partitions one for / and one for swap. I did the same partitions on both drives and then configured software raid for each. Then from the raid partitions I have one as / and 3 gb for swap, and then finished the install.

---

### Post by CharlesA on 2010-11-17
Best thing to do would probably be to boot from a livecd and see if you can see what fstab says.

---

### Post by jmast01 on 2010-11-17
It shows 

/etc/fstab: static file system information



proc           /proc                  proc no dev, no exec no suid  0    0
/ was on     /dev/md0 during install uuid=xxx(same as listed during bootup)    ext4
errors=remount -ro   0    1
swap was on /dev/md1 during install      uuid=xxxx  none swap
sw          0            0

---

### Post by CharlesA on 2010-11-17
That looks fine. Not sure why it's having problems.

It looks like it's trying to mount those devices to the wrong path (/root/whatever instead of /whatever)

---

