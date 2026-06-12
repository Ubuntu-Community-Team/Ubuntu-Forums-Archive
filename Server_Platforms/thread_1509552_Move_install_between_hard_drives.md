---
title: "Move install between hard drives"
date: 2010-06-14
forum: Server Platforms
---

### Post by spongypants23 on 2010-06-14
Hey gang,

I've installed Ubuntu Server 10.04 on a 100GB hard drive, and it's all nice and configured, with websites, mail server + content checks, MySQL, the works. Took me about two or three weeks to get it nice and running.

Problem is, the hard drive is old, and 100GB will eventually be too small for where I'm going with this.

Is there a nice, easy way to migrate the installation to a larger hard drive, or do I have to re-install and re-configure everything again?

(Can dd be used safely?)

---

### Post by ian dobson on 2010-06-14
Hi,

Boot from a live CD then dd the whole drive to the new drive. Then use fdisk to delete the partition table on the new drive and create a new one (this won't delete your data, it'll only update the partition table). Reboot again from the live cd then do a resize for your fs.

Regards
Ian Dobson

---

### Post by spongypants23 on 2010-06-14
Hi,

I should have mentioned this in my first post, but I also set up the server with the "and set up LVM" option. Does that complicate things?

Also, could you be a little more specific? The 100GB drive has an ext4 and a swap, and my target drive is a blank 200GB. I'm not sure what to run in dd, nor fdisk. Doesn't deleting the partition table delete the drive's partitions?

---

### Post by psusi on 2010-06-14
If you are using lvm then it is a snap and you can even have the system pick up and move the root volume while you are running from it.  First make sure you are using lvm.  Post the output of sudo lvs and sudo pvs.  Also df.

---

### Post by spongypants23 on 2010-06-14
sudo lvs:
```
  LV     VG      Attr   LSize   Origin Snap%  Move Log Copy%  Convert
  root   Bardulf -wi-ao 109.57g
  swap_1 Bardulf -wi-ao   4.68g
```

sudo pvs:
```
  PV         VG      Fmt  Attr PSize   PFree
 /dev/sda5  Bardulf lvm2 a-   114.26g    0
```

df:
```
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/mapper/Bardulf-root
                     113093304   6260204 101088256   6% /
none                    892628       212    892416   1% /dev
none                    897212         0    897212   0% /dev/shm
none                    897212       112    897100   1% /var/run
none                    897212         0    897212   0% /var/lock
none                    897212         0    897212   0% /lib/init/rw
none                 113093304   6260204 101088256   6% /var/lib/ureadahead/debugfs
/dev/sda1               233191     31470    189280  15% /boot
```

---

### Post by psusi on 2010-06-14
Hrm... it looks like you have a separate /boot partition.  Are you planning on removing the old disk?  If so you will need to move /boot to the new disk.  If you will keep both disks, then you can leave /boot alone and just add the new disk to the volume group, then you can extend the logical volume to use up more space on the second disk.

What is the new disk?  /dev/sdb?  Also what does sudo fdisk -l /dev/sda show?

---

