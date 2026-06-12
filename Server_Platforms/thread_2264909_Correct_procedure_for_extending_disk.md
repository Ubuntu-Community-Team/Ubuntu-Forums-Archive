---
title: "Correct procedure for extending disk"
date: 2015-02-11
forum: Server Platforms
---

### Post by tdmtmanu on 2015-02-11
Hello,
I have many server with Ubuntu Server 14.04 LTS.
I have 2 Virtual Disk: one for S.O. Ubuntu, second for my data.
Many times I need to extend second disk.
I follow this guide (VMware KB: Extending a logical volume in a virtual machine running Red Hat or Cent OS ) but after 4 primary partitions can no longer extend the disk.


What is the procedure / method to extend a linux disk ?
create partitions of type extended rather than primary?
Or is there another way?


Tnx
Manuel

---

### Post by darkod on 2015-02-11
On a disk with msdos partition table you have limitation of 4 primary partitions or 3 primary and 1 extended that holds more logical partitions inside.

Ideally for storage flexibility you should use LVM that allows easy expanding after adding new disks. On the vmware side you can simply add more virtual disks instead of expanding the current one and its partitions and then use these new disks in the lvm setup.

On a disk with gpt partition table you can have more than 4 partitions but still creating new partition after each expanding is not efficient. Is that what you are doing now?

I would suggest you start considering lvm.

---

### Post by tdmtmanu on 2015-02-11
Hello,
I use LVM.
This is one example:

root@cls3-web1:/home/graffiti# lsblk
NAME                                    MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda                                       8:0    0    10G  0 disk
&#9500;&#9472;sda1                                    8:1    0   243M  0 part /boot
&#9500;&#9472;sda2                                    8:2    0     1K  0 part
&#9492;&#9472;sda5                                    8:5    0   9.8G  0 part
  &#9500;&#9472;cls3--web1--vg-root (dm-2)          252:2    0   5.8G  0 lvm  /
  &#9492;&#9472;cls3--web1--vg-swap_1 (dm-3)        252:3    0     4G  0 lvm  [SWAP]
sdb                                       8:16   0     5G  0 disk
&#9492;&#9472;sdb1                                    8:17   0     5G  0 part
  &#9492;&#9472;cls3--web1--vg--website-data (dm-1) 252:1    0     5G  0 lvm  /data/websites
sdc                                       8:32   0    30G  0 disk
&#9492;&#9472;sdc1                                    8:33   0    30G  0 part
  &#9492;&#9472;cls3--web1--vg--files-data (dm-0)   252:0    0    30G  0 lvm  /data/files
sr0                                      11:0    1  1024M  0 rom


SDA (10 Gb) is one virtual disk on vmware
SDB (5 Gb) is another virtual disk on vmware
SDC (30 Gb) is another virtual disk on vmware

If I need to extend sdb disk, i increase size on vmware, but after on linux I need to create new physical volume (sdb2 for example) and extend volume group.
But I have limit of 4 sdb/partition ... or I need to use extended partition instead of primary ?

---

### Post by darkod on 2015-02-11
First of all, if possible, try allocating bigger disks because these sizes are very small so you will constantly need to be adding disks.

Since you have lvm I would add a new vmware disk (it will be sdd in linux), create a partition taking the whole disk (sdd1) and then add /dev/sdd1 to the volume group and extend the logical volume you want to extend.

But you can also extend sdb in vmware and create sdb2 partition and add it to the lvm. That will work too with the difference that you are working on the partition table on the working sdb disk. Be careful not to make any error. If you add a new sdd working on its table is less risky.

---

### Post by MAFoElffen on 2015-02-12
Several ways. As said, I use LVM and mdadm. Logically, those 2 are the easiest and cleanest methods. I find LVM the easiest as you don't have to have pieces that are all the same size. I usually add in 2-4 TB disks. 2TB disks are still price -wise the best value choice for me.

Virtual disks are still disk, logically.

Another method not mentioned yet is sort of oldschool, but still effective-- Mount a disk as a directory in your filesystem...

---

