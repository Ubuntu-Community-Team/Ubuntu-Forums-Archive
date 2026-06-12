---
title: "Ubuntu 9.10 boot failure"
date: 2010-05-18
forum: Ubuntu One (CLOSED)
---

### Post by surfbear on 2010-05-18
I am a linux newbie, I have been using ubuntu with no major problems for 1 month, until two days ago i had a boot failure and havn't been able to resolve it upto to this moment.

I am stuck at this point with no clue how to proceed. I have done a lot of research in linux forums and therefore i have collected some information  about the error which could be helpful:

The error message is:

```
Gave up waiting for root device. Common problems:
- Boot args (cat /proc/cmdline)
- Check rootdelay= (did the system wait long enough ?)
- Check root = (did the system wait for the right device ?)
- Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/bd4d1516-41d3-4fe1-97b2-398c355683bc does not exist . Dropping to a shell!
```

I have used my ubuntu installation cd and ran the try ubuntu option and typed the following commands in the ubuntu terminal.

Typing cat /etc/fstab, i get:

```
aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda5 swap swap defaults 0 0
```

Typing sudo fdisk -l, i get:

```
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e90bc

Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      109419   878908086   83  Linux
/dev/sda2   *      109420      109432      102400    7  HPFS/NTFS
/dev/sda3          109432      120863    91821056    7  HPFS/NTFS
/dev/sda4          120864      121601     5927985    5  Extended
/dev/sda5          120864      121601     5927953+  82  Linux swap / Solaris
```

Typing sudo blkid, i get :

```
/dev/loop0: TYPE="squashfs" 
/dev/sda2: UUID="B044235644231F1A" LABEL="System Reserved" TYPE="ntfs" 
/dev/sda3: UUID="680E257C0E254502" TYPE="ntfs" 
/dev/sda5: UUID="7f3bdbc1-0c69-43ec-859f-cf9163dbd3ec" TYPE="swap"
```

I hope anyone out here can help with this issue.

Thank you in advance

---

