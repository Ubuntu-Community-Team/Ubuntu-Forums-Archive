---
title: "cannot update grub after a kernel update (9.10)"
date: 2010-01-03
forum: Server Platforms
---

### Post by redactech on 2010-01-03
Hello dear friends

I have this brand new ubuntu server 9.10, I just did the first update and the update grub fail with the following error (:

```
update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-16-generic-pae
Found initrd image: /boot/initrd.img-2.6.31-16-generic-pae
grub-probe: error: no mapping exists for `sil_aiaiafafaccb5'
grub-probe: error: no mapping exists for `sil_aiaiafafaccb5'
Found linux image: /boot/vmlinuz-2.6.31-14-generic-pae
Found initrd image: /boot/initrd.img-2.6.31-14-generic-pae
grub-probe: error: no mapping exists for `sil_aiaiafafaccb5'
grub-probe: error: no mapping exists for `sil_aiaiafafaccb5'
Found memtest86+ image: /memtest86+.bin
done
```


fdisk give me that : 

```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60770   488134993+  8e  Linux LVM
/dev/sda2           60771       60801      249007+   5  Extended
/dev/sda5           60771       60801      248976   83  Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0007d07d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        7392    59376208+  83  Linux


```

The system is installed on the the /dev/sda

since I suspect the issue is grub2 with lvm here's the output of vgdisplay

```
--- Volume group ---
  VG Name               hochiminh
  System ID             
  Format                lvm2
  Metadata Areas        1
  Metadata Sequence No  3
  VG Access             read/write
  VG Status             resizable
  MAX LV                0
  Cur LV                2
  Open LV               2
  Max PV                0
  Cur PV                1
  Act PV                1
  VG Size               465.52 GB
  PE Size               4.00 MB
  Total PE              119173
  Alloc PE / Size       118684 / 463.61 GB
  Free  PE / Size       489 / 1.91 GB
  VG UUID               XUw1MW-nFNS-7y7O-wZ27-VR15-TxNZ-pzVVSE
   
  --- Logical volume ---
  LV Name                /dev/hochiminh/root
  VG Name                hochiminh
  LV UUID                2iEAO5-05R5-OwNK-c7JM-oj8I-Cc47-gY0mti
  LV Write Access        read/write
  LV Status              available
  # open                 1
  LV Size                462.55 GB
  Current LE             118414
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:3
   
  --- Logical volume ---
  LV Name                /dev/hochiminh/swap_1
  VG Name                hochiminh
  LV UUID                FwbE9C-apZ0-jwiv-ShTL-0iKQ-CK0q-jxis9h
  LV Write Access        read/write
  LV Status              available
  # open                 2
  LV Size                1.05 GB
  Current LE             270
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:4
   
  --- Physical volumes ---
  PV Name               /dev/mapper/sil_aiaiafafaccb1     
  PV UUID               d9fPxk-tSHL-Oaxs-eCI8-FHGp-vkNQ-TIQDYb
  PV Status             allocatable
  Total PE / Free PE    119173 / 489
```


I've lost several hours to search for similar issues and found nothing really similar (issue with dual booting, encrypted home- which I don't have etc etc)

Anyone have met this problem ?

---

### Post by sylvester_0 on 2010-01-03
Forgive me because I'm not that familiar with grub2, but what is the output of:

```
cat /boot/grub/device.map
```

Mine looks like this:

```
(hd0)	/dev/sda
```

Maybe you could make a backup of yours:

```
sudo cp /boot/grub/device.map{,.backup}
```

then edit yours to look like mine and run "sudo update-grub" again. I don't believe this could cause your server to stop booting but if worst comes to worse you could restore your old file using a live disk.

---

### Post by redactech on 2010-01-04
I have exactly the same device.map as yours...
```

cat /boot/grub/device.map.backup 
(hd0)	/dev/sda
(hd1)	/dev/sdb
(hd2)	/dev/sdc
```


So I'm stuck with that, I can't reboot the server until I fix this issue.

---

