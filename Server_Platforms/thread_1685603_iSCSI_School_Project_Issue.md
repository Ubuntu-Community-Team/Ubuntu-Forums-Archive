---
title: "iSCSI School Project Issue"
date: 2011-02-10
forum: Server Platforms
---

### Post by robot682 on 2011-02-10
I have a school project that involves connecting to a SAN.  open-iscsi found the SAN and connects to it.  I can see the data stores when I run *fdisk -l*   they are listed as */dev/dm-0 *and [I]/dev/dm-1

[/I]I can run *fdisk* on them and partition them and the partitions are created successfully.  Which creates a partition called */dev/dm-1-l0.  *(Or something similar  I am typing this from memory)   

When I try to run *mkfs.ext3 /dev/dm-1-l0* it errors out saying that it cannot format the partition because it is mounted.

When I run *mount* no /dev/dm devices are listed at all.  Any help would be appreciated.  Thanks.

p.s.  Running Ubuntu Server 10.10 32-bit.

---

### Post by robot682 on 2011-02-11
Turns out I made an error.  We are using multiple SANS.  My group memebers had made storage on one, but not the other.  I was connected to the one with no availible storage.  
 
I logged in to the controller's web interface and created storage.  After that ubuntu found it.  Also, /dev/dm-0 was related to the local LVM.

---

### Post by doogy2004 on 2011-02-11
to see a list of mounted disks and usage stats do a
```
df -h
```

then unmount the disk with
```
sudo umount FOLDERDISKMOUNTEDON
```

---

