---
title: "Booting off RAID1 Dapper 6.06.1 server"
date: 2006-09-22
forum: Server Platforms
---

### Post by aztechclan on 2006-09-22
Hi,
Just tried a fresh install of Dapper 6.06.1 server edition.  I went through the install and setup 4 raid1 devices easy as pie.  I've got swap,/,/boot,and /var as my partitions and the installer formatted them just fine across the 2 sata disks..  However, when attempting to boot for the 1st time I get a grub error:

root (hd0,0)
  Filesystem type unknown, partition type 0xfd
kernel /vmlinuz-2.6.15-26-server root=/dev/md2 ro quiet splash

Error 17: Cannot mount selected partition

I have a feeling this is a kernel/initrd issue, is there anything I can do for a quick fix?

Thanks!

---

### Post by steven43126 on 2006-09-23
Hi i recently had the exact same problem. Though i would have thought RAID support be compiled in to the kernel i may be wrong. The error only appeared when i partitioned my drive with swap and one large RAID 1 root partiotion.

However when i tried again i created a boot and root partition both in RAID 1 and bingo it worked. Why i don't know maybe it's a bug in the installer? obviously the kernel must have support as it worked for me just not the first time !

As a quick fix you can always boot from a livecd, mount one hard drive only, recompile your own kernel and initrd, Then write grub to both hard drives. Create the RAID arrays and let them sync. Then reboot and everything *should*  just work ;) should been the operative word ;)

Hope this help's

---

### Post by aztechclan on 2006-09-25
Sweetness!!  Well, thanks to both your response and also this bug description I decided that perhaps Ubuntu isn't happy unless the very first raid device is /boot.  I went ahead with this theory and the install/reboot worked flawlessly.  My new partition scheme is RAID1 for /boot, then RAID1 for /, then RAID1 for swap (in that order).  Awesome!

here's a link to what I believe to be the source of the bug.
[https://launchpad.net/distros/ubuntu/+source/debian-installer/+bug/33649](https://launchpad.net/distros/ubuntu/+source/debian-installer/+bug/33649)

---

