---
title: "GRUB software RAID1 question."
date: 2009-11-12
forum: Server Platforms
---

### Post by robhauge on 2009-11-12
Hello.

I just installed an Ubuntu server 9.10 with software RAID 1 using GRUB 1
I installed GRUB on both disks using the following procedure:

```

Disk 0:
grub> root (hd0,0)
grub> setup (hd0) 

Disk 1:
grub> root (hd1,0)
grub> setup (hd1) 

```

I have tested booting on both disks by disconnecting the cables on each. It is working ok.
I can’t understand why this works when I unplug disk0. Disk 1 should be mapped to disk 0:  Stage 1,5 should then be looking for GRUB stage2 on a “disk1” that don’t exist.
Why does this work?
I think the correct way to do this is by this method:

```


Disk 0:
grub> root (hd0,0)
grub> setup (hd0) 

Disk 1:
grub> device (hd0) /dev/sdb   # maps /dev/sdb onto the "hd0" 
grub> root (hd0,0)            
grub> setup (hd0)             # installs GRUB to hd0 aka. /dev/sdb

```
Is there any mechanism in GRUB setup that catches this?

---

### Post by robhauge on 2009-11-13
Maybe GRUB uses drive from BIOS when drive number matches in  root (hd1,0) setup (hd1). 

Setting variable 0x40 in STAGE1 to value 0xFF in the setup process.

(If it is 0xFF, use a drive passed by BIOS.)

Then it doesn't matter what drive number it receives.

---

