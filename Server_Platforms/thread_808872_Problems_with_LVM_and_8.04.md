---
title: "Problems with LVM and 8.04"
date: 2008-05-26
forum: Server Platforms
---

### Post by jb1 on 2008-05-26
```
root@spice:/sbin# lvcreate -l 44712 raid -n lvm0
File descriptor 3 left open
File descriptor 4 left open
File descriptor 5 left open
File descriptor 6 left open
  Logical volume "lvm0" created

root@spice:/sbin# lvdisplay /dev/raid/lvm0
File descriptor 3 left open
File descriptor 4 left open
File descriptor 5 left open
File descriptor 6 left open
  --- Logical volume ---
  LV Name                /dev/raid/lvm0
  VG Name                raid
  LV UUID                3DCAxo-202D-EMBN-4NRm-m7ez-SOa9-GZSrbq
  LV Write Access        read/write
  LV Status              available
  # open                 0
  LV Size                2.73 TB
  Current LE             44712
  Segments               1
  Allocation             inherit
  Read ahead sectors     0
  Block device           253:0
```


Any ideas?

---

