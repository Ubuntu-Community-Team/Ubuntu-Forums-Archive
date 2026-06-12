---
title: "LVM2 Question"
date: 2014-10-28
forum: Server Platforms
---

### Post by tcalbrecht on 2014-10-28
Greetings.

I've installed LVM2 on Trusty Tahr, created two physical volumes to use and everything seems to be working fine.  I performed basically the following steps:

```
pvcreate /dev/sdc1
vgcreate fileserver /dev/sdc1
lvcreate --name lvol1 --size 100G fileserver
mkfs.reiserfs /dev/fileserver/lvol1

lvextend -L+100G  /dev/fileserver/lvol1
lvextend -L+50G  /dev/fileserver/lvol1

pvcreate /dev/sdb1
vgextend fileserver /dev/sdb1

lvextend -L+100G  /dev/fileserver/lvol1
```

Various commands show the following:

```
tom@benny:/etc$ sudo pvdisplay
  --- Physical volume ---
  PV Name               /dev/sdc1
  VG Name               fileserver
  PV Size               298.09 GiB / not usable 4.34 MiB
  Allocatable           yes (but full)
  PE Size               4.00 MiB
  Total PE              76310
  Free PE               0
  Allocated PE          76310
  PV UUID               6iZryI-9o6f-YD07-Wwz8-yWaL-j0RA-Af09cb

  --- Physical volume ---
  PV Name               /dev/sdb1
  VG Name               fileserver
  PV Size               298.09 GiB / not usable 4.34 MiB
  Allocatable           yes
  PE Size               4.00 MiB
  Total PE              76310
  Free PE               63020
  Allocated PE          13290
  PV UUID               br0SsS-ssUn-A26M-2pxA-5f5S-tRdX-Q6Ny1E

tom@benny:/etc$ sudo vgdisplay
  --- Volume group ---
  VG Name               fileserver
  System ID
  Format                lvm2
  Metadata Areas        2
  Metadata Sequence No  8
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                1
  Open LV               1
  Max PV                0
  Cur PV                2
  Act PV                2
  VG Size               596.17 GiB
  PE Size               4.00 MiB
  Total PE              152620
  Alloc PE / Size       89600 / 350.00 GiB
  Free  PE / Size       63020 / 246.17 GiB
  VG UUID               C12uLd-Goyo-Keej-YFb0-zMN5-9F5D-i2bsUy

tom@benny:/etc$ sudo pvs
  PV         VG         Fmt  Attr PSize   PFree
  /dev/sdb1  fileserver lvm2 a--  298.09g 246.17g
  /dev/sdc1  fileserver lvm2 a--  298.09g      0

tom@benny:/etc$ sudo lvdisplay -m
  --- Logical volume ---
  LV Path                /dev/fileserver/lvol1
  LV Name                lvol1
  VG Name                fileserver
  LV UUID                RcIeZi-q2ll-DfXT-30W9-31J3-8hUZ-UldEjg
  LV Write Access        read/write
  LV Creation host, time benny, 2014-10-24 21:40:29 -0400
  LV Status              available
  # open                 2
  LV Size                350.00 GiB
  Current LE             89600
  Segments               2
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:0

  --- Segments ---
  Logical extent 0 to 76309:
    Type                linear
    Physical volume     /dev/sdc1
    Physical extents    0 to 76309

  Logical extent 76310 to 89599:
    Type                linear
    Physical volume     /dev/sdb1
    Physical extents    0 to 13289

```

However, when I look at the filesystem with df -h is see the following:

```
Filesystem                    Size  Used Avail Use% Mounted on
/dev/sda1                     145G   12G  126G   9% /
none                          4.0K     0  4.0K   0% /sys/fs/cgroup
udev                          994M  4.0K  994M   1% /dev
tmpfs                         201M  4.8M  196M   3% /run
none                          5.0M     0  5.0M   0% /run/lock
none                         1004M  516K 1003M   1% /run/shm
none                          100M   64K  100M   1% /run/user
/dev/mapper/fileserver-lvol1  250G  218G   33G  87% /mnt/lvol1

```

It shows 250G rather than the expected 350G.  Is this normal or did something go wrong?  Why does the one pv show it being full?

Thanks.

Tom

---

### Post by steeldriver on 2014-10-28
I'm not familiar with resiserfs but when I did a similar thing with an ext filesystem it was also necessary to grow the actual filesystem itself (resize_reiserfs?)

---

### Post by tcalbrecht on 2014-10-29
That did it.  Thanks very much!!

Tom

---

