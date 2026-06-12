---
title: "problems with 7TiB partition"
date: 2007-04-26
forum: Server Platforms
---

### Post by philipMac on 2007-04-26
Hi, 
I have just bought a server, and stuck Feisty onto it. 
The server is running a 3Ware hardware RAID card, and is set at RAID 6, leaving me with 7TiB of usable space, almost all of which I want to dedicate to /home
The installer borked, and couldn't deal with this size of partition, so I carved a small 10G boot volume out of the partition with the 3ware BIOS tool thing, and put the OS there. 
I now want to partition up the remaining space. 
Gparted seems to not want to allow me make this partition the size I want it to be, presumably because the block size is set small. 
This might be a silly question, but how do I adjust the block size upwards to allow a partition of this size? It should be doable with ext3 without much difficultly wrt to size limitations, I am under the impression that ext3, under a 64bit machine with max block size can go up to 32TiB. 


Thanks for any advice guys.

---

### Post by philipMac on 2007-04-27
sudo mkfs.ext3 /dev/sdb
(*now* parted works!)

(parted)
print                                                            

Disk /dev/sdb: 6989GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start   End     Size    File system  Flags
 1      0.00kB  6989GB  6989GB  ext3              <<<<<!!!!! This was
blank before, parted saw nothing here.

$ cat /proc/partitions
major minor  #blocks  name

   8     0   10485759 sda
   8     1     248976 sda1
   8     2          1 sda2
   8     5    1951866 sda5
   8     6     979933 sda6
   8     7    7301511 sda7
   8    16 6825306112 sdb



sudo vol_id -u /dev/sdb

add line :
UUID=blah /home ext3 defaults 0 2
to /etc/fstab

sudo mount /dev/sdb /mnt

mv /home/* /mnt/

umount /mnt

mount /home <- fails... never heard of this new UUID

shutdown -r now 
log in, and now everything is fine.



So, that was the issue, mkfs.ext3 /dev/sdb, once that command went
through, it went and set the disk up perfectly.

---

