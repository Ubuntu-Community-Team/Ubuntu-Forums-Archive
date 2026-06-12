---
title: "RAID5 + LVM - how to resize the LVM after growing RAID5?"
date: 2012-09-07
forum: Server Platforms
---

### Post by szafran on 2012-09-07
Hi,

I'm having problems with my LVM (I'm a begginer with LVM) that's setup on my RAID5. The story is that I've had a 4x 2TB HDD RAID5 with an LVM setup. Now I've added an HDD to the RAID5 array. After reshaping:
```
md5 : active raid5 sdd1[0] sdm1[4] sdn1[3] sdf1[2] sde1[1]
      7814047744 blocks super 1.2 level 5, 512k chunk, algorithm 2 [5/5] [UUUUU]
```

```
(parted) print
Model: Linux Software RAID Array (md)
Disk /dev/md5: 8002GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

```

```
  VG          #PV #LV #SN Attr   VSize VFree
  lvm-magazyn   1   1   0 wz--n- 5,46t     0

```

So the LVM is the same size as before (nothing special with that), but it does not see the additional free space provided by adding the new 2TB HDD.

How can I make it see the new space so I can extend my LV's ?

_____
Best regards
Szafran

---

### Post by rubylaser on 2012-09-08
I don't use LVM on top of mdadm unless, I need to support snapshots, so my LVM commands are a little rusty.  Basically, you'll need to extend your logical volume and then extend your filesystem.  I assume your physical volume is on /dev/md5 and already shows the correct size. Maybe someone with more recent LVM experience will double check this first.

```
pvdisplay
```

If so, just extend your logical volume to use all free space
```
lvresize -l +100%FREE /dev/mapper/logical_volume_name
```

Finally, extend the filesystem (I'm assuming ext4).
```
umount /dev/mapper/lvm-magazyn
fsck.ext4 /dev/mapper/lvm-magazyn
resize2fs /dev/mapper/lvm-magazyn
mount -a
```

---

### Post by rubylaser on 2012-09-08
Sorry, double post.

---

### Post by szafran on 2012-09-08
> **rubylaser said:**
> I assume your physical volume is on /dev/md5 and already shows the correct size.

The thing is it doesn't, and that's the main problem - LVM doesn't get that the size of the disk has changed (the vg size didn't even change with the /dev/md5 size change). The rest is a walk in the park.

---

### Post by rubylaser on 2012-09-08
All I see above is that your volume group hasn't been resized. I don't see your Physical Volume's size. Can you post the output of these?
```
pvdisplay
```
```
vgdisplay
```
and
```
lvdisplay
```

---

### Post by szafran on 2012-09-08
```
unused devices: <none>
root@szafran:~# pvdisplay
  --- Physical volume ---
  PV Name               /dev/md5p1
  VG Name               lvm-magazyn
  PV Size               5,46 TiB / not usable 2,98 MiB
  Allocatable           yes (but full)
  PE Size               4,00 MiB
  Total PE              1907725
  Free PE               0
  Allocated PE          1907725
  PV UUID               VhmHMA-310b-piUL-PtkI-iad2-wXBt-Pr3tPz

```

```
root@szafran:~# vgdisplay
  --- Volume group ---
  VG Name               lvm-magazyn
  System ID
  Format                lvm2
  Metadata Areas        1
  Metadata Sequence No  69
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                1
  Open LV               1
  Max PV                0
  Cur PV                1
  Act PV                1
  VG Size               5,46 TiB
  PE Size               4,00 MiB
  Total PE              1431306
  Alloc PE / Size       1431306 / 5,46 TiB
  Free  PE / Size       0 / 0
  VG UUID               ry4ome-QzhJ-OH1O-4hpW-SULs-n385-KGjcqj

```

```
root@szafran:~# lvdisplay
  --- Logical volume ---
  LV Path                /dev/lvm-magazyn/vm-100-disk-1
  LV Name                vm-100-disk-1
  VG Name                lvm-magazyn
  LV UUID                CoC8Hz-CUWV-g1eO-biDz-266q-Qu4V-AMuOfc
  LV Write Access        read/write
  LV Creation host, time ,
  LV Status              available
  # open                 1
  LV Size                5,46 TiB
  Current LE             1431306
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     8192
  Block device           253:1

```

---

### Post by rubylaser on 2012-09-08
You have a partition on your mdadm array md5p1, so you'll need to expand the partition with parted first to allow your volume group to see the new space on your array.

---

### Post by szafran on 2012-09-08
> **rubylaser said:**
> You have a partition on your mdadm array md5p1, so you'll need to expand the partition with parted first to allow your volume group to see the new space on your array.

Parted says that it can't find a filesystem on that partition, and therefore it wont resize it. And in GParted any resize options are greyed out, so they can't be used.

---

