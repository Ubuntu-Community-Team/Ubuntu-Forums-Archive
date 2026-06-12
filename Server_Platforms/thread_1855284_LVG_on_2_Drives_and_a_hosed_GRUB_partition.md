---
title: "LVG on 2 Drives and a hosed GRUB partition"
date: 2011-10-05
forum: Server Platforms
---

### Post by srich on 2011-10-05
I have 2 x 1TB drives with the following layout

/dev/sda1 = /boot
/dev/sda2 = LVG
/dev/sdb1 = LVG Member

I am running Ubuntu Server 10.04 LTS

Somehow, during a shutdown, my VG def (I assume) got corrupted.  Over the past 4 hours, I think I have now managed to hose my GRUB seeing that when I boot, I get a GRUB rescue prompt and just above that I get error: unknown filesystem.
I can boot from Ubuntu Live CD and mount /dev/sda1 and see all the files.  I then, scan for LGs and activate the LVG.  When I go to mount the LV, I get the following:

$ sudo mount /dev/kaminoroot ./root
mount: wrong fs type, bad option, bad superblock on /dev/mapper/kamino-root,
  missing codepage or helper program, or other error
  In some cases useful info is found in syslog - try
  dmesg | tail or so

vgdisplay shows the proper information
lvdisplay shows 2 volumes with LV status = available
pvdisplay shows /dev/sda2 and /dev/sdb1
fdisk -l shows
  /dev/sda1 as System: GPT
  /dev/sdb1 as System: Linux LVM
  (funny, I don't see an entry for /dev/sda2 which is the LVG)

My VG was created as an EXT4 FS.

Any ideas?

---

### Post by lcman on 2011-10-06
> **srich said:**
> I have 2 x 1TB drives with the following layout

/dev/sda1 = /boot
/dev/sda2 = LVG
/dev/sdb1 = LVG Member

I am running Ubuntu Server 10.04 LTS

Somehow, during a shutdown, my VG def (I assume) got corrupted.  Over the past 4 hours, I think I have now managed to hose my GRUB seeing that when I boot, I get a GRUB rescue prompt and just above that I get error: unknown filesystem.
I can boot from Ubuntu Live CD and mount /dev/sda1 and see all the files.  I then, scan for LGs and activate the LVG.  When I go to mount the LV, I get the following:

$ sudo mount /dev/kaminoroot ./root
mount: wrong fs type, bad option, bad superblock on /dev/mapper/kamino-root,
  missing codepage or helper program, or other error
  In some cases useful info is found in syslog - try
  dmesg | tail or so

vgdisplay shows the proper information
lvdisplay shows 2 volumes with LV status = available
pvdisplay shows /dev/sda2 and /dev/sdb1
fdisk -l shows
  /dev/sda1 as System: GPT
  /dev/sdb1 as System: Linux LVM
  (funny, I don't see an entry for /dev/sda2 which is the LVG)

My VG was created as an EXT4 FS.

Any ideas?

You don't overlay filesystems on vg but on lv. You probably just didn't format your lvs.
```
sudo mke2fs -t ext4 -j /dev/volumegroup/logicalvolume
```

should do the trick.

---

### Post by srich on 2011-10-06
This volume was up and running (for about 6 months now) until an unclean shutdown/reboot.  I have ~1TB of files.  Will this command wipe my data?

---

### Post by jazzon on 2011-10-06
Cant help you ouit but to answer your last question YES!  Data will be gone!!

---

### Post by iburry on 2011-10-06
I recently had a similar problem when the primary hard drive in my file server failed. Either lvm isn't as bulletproof as I thought, or I screwed something up, or a combination of the two. In any case, it looks like you're in the 'attempted data recovery' stage:

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

good luck

---

