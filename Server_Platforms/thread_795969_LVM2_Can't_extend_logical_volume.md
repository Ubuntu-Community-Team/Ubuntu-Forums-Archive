---
title: "LVM2 Can't extend logical volume"
date: 2008-05-16
forum: Server Platforms
---

### Post by kxmas on 2008-05-16
This is driving me nuts.  I know I have some 381 gigs free, but I can't add it to my logical volume group.  Any tips would be appreciated

I've tried a few variants of this, but the output is always the same...
```
root@kevcomp6:~# lvextend -L 1.17TB  /dev/media_volume_group/media_logical_volume
  Rounding up size to full physical extent 1.17 TB
  Using stripesize of last segment 4.00 KB
  Rounding size (306709 extents) down to stripe boundary size for segment (306708 extents)
  Extending logical volume media_logical_volume to 1.17 TB
  Insufficient suitable allocatable extents for logical volume media_logical_volume: 97448 more required
```

```
root@kevcomp6:~# lvextend -l +97784 /dev/media_volume_group/media_logical_volume
  Using stripesize of last segment 4.00 KB
  Extending logical volume media_logical_volume to 1.17 TB
  Insufficient suitable allocatable extents for logical volume media_logical_volume: 97676 more required
root@kevcomp6:~# lvextend -l +100%FREE /dev/media_volume_group/media_logical_volume
  Using stripesize of last segment 4.00 KB
  Extending logical volume media_logical_volume to 1.17 TB
  Insufficient suitable allocatable extents for logical volume media_logical_volume: 97676 more required
```




Here's some output...
```
root@kevcomp6:~# pvdisplay
  --- Physical volume ---
  PV Name               /dev/sdb2
  VG Name               media_volume_group
  PV Size               267.45 GB / not usable 1.74 MB
  Allocatable           yes (but full)
  PE Size (KByte)       4096
  Total PE              68468
  Free PE               0
  Allocated PE          68468
  PV UUID               7XcKwp-jgHY-yPx8-WQQU-s5NL-3Pci-rRF6s9

  --- Physical volume ---
  PV Name               /dev/sdc1
  VG Name               media_volume_group
  PV Size               465.76 GB / not usable 1.50 MB
  Allocatable           yes
  PE Size (KByte)       4096
  Total PE              119234
  Free PE               54
  Allocated PE          119180
  PV UUID               syV6bd-l3sB-vSl3-CElF-k134-p1uW-X2dzUu

  --- Physical volume ---
  PV Name               /dev/sdd1
  VG Name               media_volume_group
  PV Size               465.76 GB / not usable 1.50 MB
  Allocatable           yes
  PE Size (KByte)       4096
  Total PE              119234
  Free PE               97730
  Allocated PE          21504
  PV UUID               hvc3t5-nX8m-PxFs-EqKo-Ka7K-kysH-Njjlo8

root@kevcomp6:~# vgs -o +vg_free_count,vg_extent_count
  VG                 #PV #LV #SN Attr   VSize VFree   Free  #Ext
  media_volume_group   3   1   0 wz--n- 1.17T 381.97G 97784 306936

root@kevcomp6:~# vgdisplay
  --- Volume group ---
  VG Name               media_volume_group
  System ID
  Format                lvm2
  Metadata Areas        3
  Metadata Sequence No  38
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                1
  Open LV               0
  Max PV                0
  Cur PV                3
  Act PV                3
  VG Size               1.17 TB
  PE Size               4.00 MB
  Total PE              306936
  Alloc PE / Size       209152 / 817.00 GB
  Free  PE / Size       97784 / 381.97 GB
  VG UUID               E541oT-H0oF-m6Kd-WYJZ-dNeJ-MAhP-4cAgzW

root@kevcomp6:~# lvdisplay
  --- Logical volume ---
  LV Name                /dev/media_volume_group/media_logical_volume
  VG Name                media_volume_group
  LV UUID                0rYWQv-o2qK-Rrj4-Pmo6-xW6N-NZiH-gCIr2O
  LV Write Access        read/write
  LV Status              available
  # open                 0
  LV Size                817.00 GB
  Current LE             209152
  Segments               4
  Allocation             inherit
  Read ahead sectors     0
  Block device           254:0


```

---

### Post by ikonia on 2008-05-16
I'll just check I'm not being silly here, but it looks like you've not got enough space in your volume goup.


eg:

VG Size               1.17 TB
  PE Size               4.00 MB
  Total PE              306936
  Alloc PE / Size       209152 / 817.00 GB
  Free  PE / Size       97784 / 381.97 GB
  VG UUID               E541oT-H0oF-m6Kd-WYJZ-dNeJ-MAhP-4cAgzW


817GB used, free 381.97GB + rounding = not enough space. 


Try dropping it down to say -L 1.15TB, or use the FREE or MAX options to extend to the max free space.

---

### Post by kxmas on 2008-05-16
I've tried that.  Didn't work either.

```
root@kevcomp6:~# lvextend -l+100%FREE /dev/media_volume_group/media_logical_volume
  Using stripesize of last segment 4.00 KB
  Extending logical volume media_logical_volume to 1.17 TB
  Insufficient suitable allocatable extents for logical volume media_logical_volume: 97676 more required
```

```
lvextend -L +1G /dev/media_volume_group/media_logical_volume
  Using stripesize of last segment 4.00 KB
  Extending logical volume media_logical_volume to 818.00 GB
  Insufficient suitable allocatable extents for logical volume media_logical_volume: 148 more required
```

---

### Post by Quackrabbit on 2008-05-16
lvextend -L +1G means to add 1G to the existing LV...

Try adding what you have free space, or drop the +

Try something like:
lvextend -L 1.17TB 

or

lvextend -L +317G

You might even want to add --test to be sure.

---

### Post by kxmas on 2008-05-16
yes, I ran the -L +1G as a response to ikonia who wanted me to decrease the amount a little bit.  I was demonstrating that growing it by even the smallest amount didn't work.

Here's the output of the commands you suggested.

```
root@kevcomp6:~# lvextend -L 1.17TB --test /dev/media_volume_group/media_logical_volume
  Test mode: Metadata will NOT be updated.
  Rounding up size to full physical extent 1.17 TB
  Using stripesize of last segment 4.00 KB
  Rounding size (306709 extents) down to stripe boundary size for segment (306708 extents)
  Extending logical volume media_logical_volume to 1.17 TB
  Insufficient suitable allocatable extents for logical volume media_logical_volume: 97448 more required
```

```
root@kevcomp6:~# lvextend -L +317G --test /dev/media_volume_group/media_logical_volume
  Test mode: Metadata will NOT be updated.
  Using stripesize of last segment 4.00 KB
  Extending logical volume media_logical_volume to 1.11 TB
  Insufficient suitable allocatable extents for logical volume media_logical_volume: 81044 more required
```

---

### Post by fajans on 2010-10-27
Hey, kxmas,

Did solve that issue?
I have exactly the same silly problem which drives me mad. 
code:

root@main:~# vgdisplay 
  --- Volume group ---
  VG Name               data
  System ID             
  Format                lvm2
  Metadata Areas        2
  Metadata Sequence No  3
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                1
  Open LV               0
  Max PV                0
  Cur PV                2
  Act PV                2
  VG Size               1,01 TiB
  PE Size               4,00 MiB
  Total PE              264419
  Alloc PE / Size       176128 / 688,00 GiB
  Free  PE / Size       88291 / 344,89 GiB
  VG UUID               iwQeFy-TzwQ-0Gd3-WOhv-TNE2-Uzcv-cnep3R

root@main:~# lvextend /dev/data/lvol0 /dev/sda4
  Extending logical volume lvol0 to 1,01 TiB
  Insufficient suitable contiguous allocatable extents for logical volume lvol0: 88120 more required

---

### Post by thdyck on 2011-07-01
Hi kxmas,

I had the same problem. Check that the LV is not set to only allow contiguous additional allocations.

e.g.

```

# unmount the file system on the LV
...

# lvdisplay /dev/vg_md3/lv_vmhost_data_vmimages
  --- Logical volume ---
  LV Name                /dev/vg_md3/lv_vmhost_data_vmimages
  VG Name                vg_md3
  LV UUID                rKg2j6-nz4J-c6kj-CbEn-zHIq-9jFE-Td02d1
  LV Write Access        read/write
  LV Status              available
  # open                 0
  LV Size                173.86 GiB
  Current LE             44507
  Segments               1
  Allocation             contiguous          <== THIS LINE
  Read ahead sectors     8192
  - currently set to     256
  Block device           251:9

# lvchange /dev/vg_md3/lv_vmhost_data_vmimages --alloc inherit
  Logical volume "lv_vmhost_data_vmimages" changed
# lvdisplay /dev/vg_md3/lv_vmhost_data_vmimages
  --- Logical volume ---
  LV Name                /dev/vg_md3/lv_vmhost_data_vmimages
  VG Name                vg_md3
  LV UUID                rKg2j6-nz4J-c6kj-CbEn-zHIq-9jFE-Td02d1
  LV Write Access        read/write
  LV Status              available
  # open                 0
  LV Size                173.86 GiB
  Current LE             44507
  Segments               1
  Allocation             inherit
  Read ahead sectors     8192
  - currently set to     256
  Block device           251:9

# lvresize /dev/vg_md3/lv_vmhost_data_vmimages --size +75GB
  Extending logical volume lv_vmhost_data_vmimages to 248.86 GiB
  Logical volume lv_vmhost_data_vmimages successfully resized

# check the file system
e2fsck /dev/vg_md3/lv_vmhost_data_vmimages

# grow the file system
resize2fs /dev/vg_md3/lv_vmhost_data_vmimages

```

Regards,
Tim Miller Dyck

---

