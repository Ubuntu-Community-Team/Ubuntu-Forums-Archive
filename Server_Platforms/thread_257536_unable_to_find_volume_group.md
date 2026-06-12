---
title: "unable to find volume group"
date: 2006-09-14
forum: Server Platforms
---

### Post by acehigh on 2006-09-14
Hi all,

I recently updated my amd64 ubuntu server with a new disk so I decided to test RAID5 (3 disks) and LVM (Before was RAID1 and no LVM).
My actual RAID config is:

Personalities : [raid1] [raid5]
md1 : active raid5 sda2[0] sdc2[2] sdb2[1]
      397656704 blocks level 5, 64k chunk, algorithm 2 [3/3] [UUU]

md0 : active raid1 sda1[0] sdb1[2](S) sdc1[1]
      289024 blocks [2/2] [UU]

While  the file system structure is:

/dev/mapper/acme_raid5-root / reiserfs rw 0 0
proc /proc proc rw 0 0
/sys /sys sysfs rw 0 0
varrun /var/run tmpfs rw 0 0
varlock /var/lock tmpfs rw 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
devshm /dev/shm tmpfs rw 0 0
/dev/md0 /boot ext3 rw 0 0
/dev/mapper/acme_raid5-home /home reiserfs rw 0 0
/dev/mapper/acme_raid5-var /var reiserfs rw 0 0

Basically I made a small RAID1 device to hold /boot (since a RAID5 /boot doesn't work) and a RAID5 device divided with LVM to hold all the rest of the fs.

The problem is:

when I boot from /dev/sda1 (GRUB) everything is ok. When I change the boot device in the BIOS to start from /dev/sdc1 (GRUB installed also there) the kernel loads up and after activating md0 and md1 i get the error:

**unable to find volume group /dev/mapper/acme****_raid5-root**

Obviously I want to be able to boot from the second RAID1 device in case of a fault from /dev/sda!
How can I resolve this?
Any suggestion appreciated.

---

### Post by acehigh on 2006-09-15
Any suggestions yet?
Did I post in the wrong place?

---

### Post by acehigh on 2006-09-17
Maybe it was a silly question, maybe not...

Noone told me that the root partition can't live on a LVM.

Reinstalling everything with the root partition on a small raid1 partition worked ok.

Anyway... don't bother to answer me all together...:(

---

### Post by keithweddell on 2006-09-17
I'd help if I could but I just don't know enough about this stuff.  Sorry.

Keith

---

