---
title: "cannot boot with multiple RAID 1 devices"
date: 2010-08-28
forum: Server Platforms
---

### Post by space_squirrel on 2010-08-28
Hello,
after giving up on fakeraid (the motherboard controller is not recognized by ubiquity) I am trying to install Ubuntu server 10.04 x64 on a HP DL180G6 server using software RAID1, with the following configuration:

sda: 250Gb
sdb: 250Gb
sdc:500Gb
sdd:500Gb

sda1 + sdb1 = md0  /
sda2 + sdb2 = md1  /tmp
sda3 + sdb3 = md2  /mnt/backup
sda4 + sdb4 = md3  swap
sdc1 + sdc1 = md4  /var
sdc2 + sdd2 = md5  /home

The installation goes on smoothly,but upon reboot md4 and md5 are not recognized. Instead, the system looks for md5p2 (I already checked and md5 does not contain a partition table, just a partition). Error message is

mount: wrong fs type [...] on /dev/md5p2

The files /etc/fstab and /etc/mdadm.conf look normal. The partitioning was performed with the installation textual tool. If I move the contents of /var and /home to the root partition and remove md4 and md5 from fstab, the system boots normally. Inittab's contents look normal. I tried disabling filesystem checks, to no avail.

Any hint on what to investigate?

Thanks

-- 
s.s.

---

### Post by ian dobson on 2010-08-28
Hi,

Please show your /etc/mdadm.conf and did you recreate the inital ramfs? (update-initramfs -u) I had problems booting from my mdadm array until in recreated the initramdisk.

Regards
Ian Dobson

---

### Post by space_squirrel on 2010-08-28
> **ian dobson said:**
> (cut) Please show your /etc/mdadm.conf and did you recreate the inital ramfs? (update-initramfs -u) I had problems booting from my mdadm array until in recreated the initramdisk.

Hello Ian,
thank you for your reply.

I tried recreating the ramfs, but although it does not show the error message any more, it still hangs at the same point.

Here is the requested file:

/etc/mdadm/mdadm.conf
```
# mdadm.conf
# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE partitions

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays
ARRAY /dev/md0 level=raid1 num-devices=2  UUID=b2bd08e0:c4916a86:3936bf3c:6657999f
ARRAY /dev/md1 level=raid1 num-devices=2  UUID=bf408db6:5767bdc8:bb047ee1:178ffc10
ARRAY /dev/md2 level=raid1 num-devices=2  UUID=2065e513:a65d7e44:54521f58:7753bc51
ARRAY /dev/md3 level=raid1 num-devices=2  UUID=a33fdf03:3434c645:4a636017:b0be6e2e
ARRAY /dev/md4 level=raid1 num-devices=2  UUID=62c304f9:3946fac3:49ac5634:1559ba4b
ARRAY /dev/md5 level=raid1 num-devices=2  UUID=754cba3f:ff8f6224:cc6ce561:109ece9f

# This file was auto-generated on Fri, 27 Aug 2010 17:50:41 +0200
# by mkconf $Id$
```After two installation attempts, I am now trying to wipe MD4 and MD5 and recreate them by hand.
If in the meantime you could think of something, please do tell me.

Kind Regards
-- 
s.s.

---

### Post by space_squirrel on 2010-08-28
First it does not recognize the controller. Then it messes up software raid partitions. Then it hides logs during boot. All before it even boots for the first time.

Heck with it.

-- 
s.s.

---

