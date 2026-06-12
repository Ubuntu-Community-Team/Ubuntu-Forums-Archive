---
title: "Harddrive woes"
date: 2012-08-10
forum: Server Platforms
---

### Post by Frankincense93 on 2012-08-10
Hi guys,

A new problem occurred today that may result in me buying a new hdd.

I ssh's into my home server this morning and i was presented with the fact i cannot do anything. After logging in, running most command results in:
```
-bash: /bin/su: Input/output error'.
```

I cannot restart because of this problem so I can't try that until later. 

fsck results in:
```

fsck
fsck from util-linux 2.20.1
e2fsck 1.42 (29-Nov-2011)
fsck.ext4: Superblock invalid, trying backup blocks...
fsck.ext4: Bad magic number in super-block while trying to open /dev/mapper/SERVER-root

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device&gt;
```

fdisk -l show:

```
fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00087990

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      499711      248832   83  Linux
/dev/sda2          501758   488396799   243947521    5  Extended
/dev/sda5          501760   488396799   243947520   8e  Linux LVM
fdisk: unable to read /dev/sdb: Inappropriate ioctl for device

```

fsck /dev/sda1 shows:

```
fsck /dev/sda1
fsck from util-linux 2.20.1
e2fsck 1.42 (29-Nov-2011)
/dev/sda1 is mounted.


WARNING!!!  The filesystem is mounted.   If you continue you ***WILL***
cause ***SEVERE*** filesystem damage.


Do you really want to continue<n>? no

check aborted.

```

I cannot open /var/log/messages because of the input/output error.

But i **can** access my usb external HDDs.

Do I have some kind of superblock/partition corruption? Is there anything else I can run to get more information?

---

### Post by Frankincense93 on 2012-08-10
Nothing?

Should I just buy a new HDD and load my backup onto it? Or is there anything else I can try?

---

### Post by chrislynch8 on 2012-08-10
So you CAN log into the server but some commands are not working is this correct?

Can you actually see that data on the disk?
If you have physical access to the server can you boot into a live Linux CD and run the checks on the disks?

Rgds
Chris

---

### Post by Frankincense93 on 2012-08-10
Yes I can log in, but I receive a:

```
Failed to add entry for user jack.

Last login: Thu Aug  9 19:33:07 2012 from jack

```

Error. When running 'ls' it doesn't show anything BUT I can traverse the folders???? i.e I can 'cd etc' but I can't see whats there!

I am currently out, but I will be at home later. What checks can I run?

---

### Post by LHammonds on 2012-08-11
Since you cannot run checks on mounted file systems and your root file system may be having problems too, you will need to boot the system using a LiveCD and run disk checks from there.

---

### Post by d4m1r on 2012-08-13
The filesystem might be corrupt, not the actual hardware. Trying reinstalling (backup first!) before buying a new HDD?

---

### Post by bakegoodz on 2012-08-14
I've used to ddrescue to save the backup ignorant's bacon several times
[http://www.gnu.org/software/ddrescue/manual/ddrescue_manual.html](http://www.gnu.org/software/ddrescue/manual/ddrescue_manual.html)

---

