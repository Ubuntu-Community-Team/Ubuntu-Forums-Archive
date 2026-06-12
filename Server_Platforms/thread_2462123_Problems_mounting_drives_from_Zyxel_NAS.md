---
title: "Problems mounting drives from Zyxel NAS"
date: 2021-05-14
forum: Server Platforms
---

### Post by alexsr700 on 2021-05-14
Hello everyone,
I have moved my Zyxel NSA325v2 from stock to OpenWRT and would now like to backup my drives using my Raspberry Pi.

Problem is mounting the drives. The drives (4 in total) were all working well and had no issues. 
So, per recommendation, I tried a few things but cannot seem to get anywhere.

For your information, the drives are from two 2-tier NAS devices. So in theory 2 RAID systems which were not running as a real RAID but as 4 "independent" drives. Zyxel seemingly always creates a RAID system even though I opted for single drive setup.

The following is from one of the drives (randomly selected):

```
Disk /dev/sda: 1.7 TiB, 1801763774464 bytes, 3519069872 sectors
Disk model: 000-2AE166      
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x00000000

Device     Boot Start        End    Sectors Size Id Type
/dev/sda1           1 4294967295 4294967295   2T ee GPT
root@piserver:/home/pi# 
root@piserver:/home/pi# mdadm -E /dev/sda
/dev/sda:
   MBR Magic : aa55
Partition[0] :   4294967295 sectors at            1 (type ee)
root@piserver:/home/pi# 
root@piserver:/home/pi# mdadm -A -f /dev/md0 /dev/sda2 /dev/sdb2
mdadm: cannot open device /dev/sda2: No such file or directory
mdadm: /dev/sda2 has no superblock - assembly aborted
root@piserver:/home/pi# mdadm -A -f /dev/md0 /dev/sda1
mdadm: cannot open device /dev/sda1: No such file or directory
mdadm: /dev/sda1 has no superblock - assembly aborted
root@piserver:/home/pi#
```

Result of second disc from the same NAS
```

Disk /dev/sda: 1.7 TiB, 1801763774464 bytes, 3519069872 sectors
Disk model: 000-2AE166      
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x11717ad9

Device     Boot Start        End    Sectors Size Id Type
/dev/sda1           1 4294967295 4294967295   2T ee GPT
root@piserver:/home/pi# 
root@piserver:/home/pi# mdadm -E /dev/sda
/dev/sda:
   MBR Magic : aa55
Partition[0] :   4294967295 sectors at            1 (type ee)
root@piserver:/home/pi# 
root@piserver:/home/pi# mdadm -A -f /dev/md0 /dev/sda2 /dev/sdb2
mdadm: cannot open device /dev/sda2: No such file or directory
mdadm: /dev/sda2 has no superblock - assembly aborted
root@piserver:/home/pi# 
root@piserver:/home/pi# mdadm -A -f /dev/md0 /dev/sda1
mdadm: cannot open device /dev/sda1: No such file or directory
mdadm: /dev/sda1 has no superblock - assembly aborted
root@piserver:/home/pi# 
``` 
Reference is also [https://kb.zyxel.com/KB/searchArticle!gwsViewDetail.action?articleOid=013308&lang=EN](https://kb.zyxel.com/KB/searchArticle!gwsViewDetail.action?articleOid=013308&lang=EN)

Does anybody have any ideas?

Thank you for your help :)
Alex

---

