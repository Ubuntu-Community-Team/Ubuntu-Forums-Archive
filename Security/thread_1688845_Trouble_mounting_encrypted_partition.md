---
title: "Trouble mounting encrypted partition"
date: 2011-02-15
forum: Security
---

### Post by barbobot on 2011-02-15
So I decided it would be a good week to re-install ubuntu on an encrypted lvm. This was my first mistake.

So let me explain a bit about my system.

I have / mounted on my first harddrive, (/dev/sda1) I have 2 other harddrives (/dev/sdb and /dev/sdc), during the install I accidentally hit the wrong harddrive I wanted to encrypt (/dev/sdb), and I typed in the password (however I don't think any formatting was done)

So now, my second harddrive needs a password to mount it.

Here is what I've tried doing:
cryptsetup luksOpen /dev/sdb1 2tb

Password:

No error if I enter the correct password, but there is an error if I type in the incorrect on (duh! but this tells me that there is a chance I can still use the drive, I hope I'm correct)

Next I do the following:
mount /dev/mapper/2tb /media/2tb/

mount: you must specify the filesystem type

Yikes! So I've tried doing ext2-4 but none worked. I'm kind of at a loss here, is there a way to fix this?

Here is the relevant portion from fdisk -l

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00026dc9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      243202  1953513472   83  Linux

---

### Post by bodhi.zazen on 2011-02-16
Where are you using LVM ?

I assume you are using LVM in the crypt ? In that case you need to activate your LVM partition(s)

```
sudo vgscan
sudo vgchange -ay
```

Then mount your lvm

```
mount /dev/mapper/lvm-root /mount/point
```

If it is not an LVM problem, did you format the crypt ?

---

