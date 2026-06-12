---
title: "Migrate Ubuntu VM to EC2"
date: 2018-02-22
forum: Virtualisation
---

### Post by pksinghlinux on 2018-02-22
Hi,

I have may ubuntu VM which currently running on Jiffybox, now I want to migrate it to AWS EC2 instance, my current ubuntu version is 14.04, I tried to take backup (in RAW) format and try to put it in AWS, but AWS throwing error that "not contain any partition table".

When I check jiffybox VM partition using fdisk -l, it showing me out put.
```

root@j310660:~# fdisk -l

Disk /dev/xvda: 304.9 GB, 304942678016 bytes
255 heads, 63 sectors/track, 37073 cylinders, total 595591168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/xvda doesn't contain a valid partition table

Disk /dev/xvdb: 17.2 GB, 17179869184 bytes
255 heads, 63 sectors/track, 2088 cylinders, total 33554432 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/xvdb doesn't contain a valid partition table
```
this is my fstab entry 

```
/dev/xvda       /               ext4    noatime                 0       1
/dev/xvdb       none            swap    sw                      0       0
proc            /proc           proc    defaults                0       0
dev            /dev            tmpfs   rw                      0       0
root@j310660:~#
```


I really wondering how could migrate this VM to AWS, please help me on this.

---

### Post by ajgreeny on 2018-02-22
*Thread moved to **Virtualisation**.* which is more appropriate and a better fit.

---

### Post by LHammonds on 2018-02-22
Maybe fsarchiver can come to the rescue?

Here are my [backup and restore instructions]("http://hammondslegacy.com/forum/viewtopic.php?f=40&t=220#p452") but I have no idea how they apply to 3rd-party hosts.  I host my own ESXi systems.

LHammonds

---

