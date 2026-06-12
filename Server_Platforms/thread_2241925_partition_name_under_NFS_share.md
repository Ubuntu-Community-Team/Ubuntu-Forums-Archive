---
title: "partition name under NFS share"
date: 2014-08-29
forum: Server Platforms
---

### Post by laurence5 on 2014-08-29
Hi having successfully set up my NFS share, I am having another problem. I am sharing two drives - one, a physical hard drive, which I have successfully renamed to Alex, and which shows on the network and on fdisk as /media/loz/Alex
My second however, is a LVM partition, and I wish to change the name to Poppy, which I cannot seem to do - it appears on my share as:  /media/loz/13894248-ab99-431d-b6e7-8a2ef331a9cf, which is cubersome to type and doesn't look nice. 

I have tried e2label and tune2fs, but get the error:
Bad magic number in super-block while trying to open **** Couldn't find valid filesystem superblock

I have read that this is a partitioning issue, but as the partition was created with gparted and has only been used in my server box, I assumed it would be an ext4 partition.
The partition is on sda, which contains the /boot sector and the /swap volume, so I am reluctant to start playing without knowing fully what I am doing, so any help would be appreciated, thanks

---

### Post by lukeiamyourfather on 2014-08-29
Stuff under /media is temporarily mounted, like a USB flash drive and the names of the mounts are determined automatically. If you want to name the mounts whatever you want then use /etc/fstab to configure where to mount the partitions and what to call them. 

[https://help.ubuntu.com/community/AutomaticallyMountPartitions#Editing_Ubuntu.27s_filesystem_table](https://help.ubuntu.com/community/AutomaticallyMountPartitions#Editing_Ubuntu.27s_filesystem_table)

---

### Post by laurence5 on 2014-08-29
OK, thanks for the help, I will look into this (although a quick scan shows that I may already be out of my depth!)

---

