---
title: "extend my root fs to entire disk"
date: 2012-04-29
forum: Server Platforms
---

### Post by davidmaxwaterman on 2012-04-29
Hi,

I recently switched the disks on my md raid1 system disks for bigger ones. That seemed to go ok, but I'm not yet utilising the full extra space (I went from 80GB to 200GB drives).

Each of the disks in the array are :

```
/dev/sda1            2048   390721967   195359960   fd  Linux RAID autodetect
```

so the partitions on the drives see the entire space.

However, the pv seems to still be at the old value :

```
# pvdisplay /dev/md1
  --- Physical volume ---
  PV Name               /dev/md1
  VG Name               server
  PV Size               74.53 GiB / not usable 3.31 MiB
  Allocatable           yes 
  PE Size               4.00 MiB
  Total PE              19078
  Free PE               134
  Allocated PE          18944
  PV UUID               2Zxdfy-pQOv-tuFl-beGD-3QqZ-NyJW-NPWGQW

```

as are :

```
# vgdisplay
  --- Volume group ---
  VG Name               server
  System ID             
  Format                lvm2
  Metadata Areas        1
  Metadata Sequence No  9
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                2
  Open LV               2
  Max PV                0
  Cur PV                1
  Act PV                1
  VG Size               74.52 GiB
  PE Size               4.00 MiB
  Total PE              19078
  Alloc PE / Size       18944 / 74.00 GiB
  Free  PE / Size       134 / 536.00 MiB
  VG UUID               oX1vhp-WqV9-fVSG-dgvk-yMS2-Jsum-gG2MrY

```

and :

```
# lvdisplay
  --- Logical volume ---
  LV Name                /dev/server/root
  VG Name                server
  LV UUID                vJla9i-epDU-3cgk-t5im-EGwK-CkLu-eg1oii
  LV Write Access        read/write
  LV Status              available
  # open                 1
  LV Size                70.00 GiB
  Current LE             17920
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:0
   
  --- Logical volume ---
  LV Name                /dev/server/swap
  VG Name                server
  LV UUID                zWkfZH-bSSe-eSny-5AwL-NzPo-sAmK-9Yx3FL
  LV Write Access        read/write
  LV Status              available
  # open                 2
  LV Size                4.00 GiB
  Current LE             1024
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:1

```

```
# df -hl
Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/server-root
                       69G   49G   17G  75% /

```

```
# grep server /etc/fstab
/dev/server/root / ext4 errors=remount-ro 0 1
/dev/server/swap none swap sw 0 0

```

It's the /dev/server/root where I would like to see the extra space.

I supposed I needed to pvextend /dev/md1 first, so I tried that, and it seemed to give me an appropriate response :

```
# pvresize /dev/md1
  Physical volume "/dev/md1" changed
  1 physical volume(s) resized / 0 physical volume(s) not resized

```

Though nothing has changed, so perhaps it thinks it already fills available space.

Searching for similar experiences, I find that most create a partition and add that to the volume group. I'd kind prefer to avoid that, if possible (since it's all on the same disk, I don't see why it is necessary[1]).

How to proceed?

Max.

[1] Though I, admittedly, don't know what I'm talking about.

---

