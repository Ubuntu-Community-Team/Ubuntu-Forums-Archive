---
title: "problems with partitioning"
date: 2016-06-28
forum: Ubuntu Studio
---

### Post by muzzol on 2016-06-28
I-m having problems with partitioning a fresh SDD drive. On installation I choose manual partitioning and I get this table

[ATTACH=CONFIG]269836[/ATTACH]



if I start gnome-disks manually I get the correct partitions

[ATTACH=CONFIG]269837[/ATTACH]

the only thing I did was partitioning the disk with a typical setup, like a lot of times.

Is there anything wrong with partman?

---

### Post by jejeman on 2016-06-29
Do 
```
sudo parted -l
```

---

### Post by oldfred on 2016-06-29
Your first screen shot shows sda as FAT32.
We do not format drives like sda.

But second screen shot looks more normal. 
Not sure how it could be both?

Since MBR, post the output of parted as jejeman requested, but also post this (should be same as parted list):
sudo fdisk -lu

---

### Post by yoshii on 2016-06-30
I think what the person above was trying to say is instead of formatting with FAT32, choose ext3 or ext4.  I prefer ext3 as it is almost as advanced as ext4 but more resilient against data corruption during power failures than ext4.  Ext2 is oldest and good for Puppy Linux installs that need encryption.  Good luck.  

It could be that your flash drive is wearing down also.  NAND technology is like that sometimes, but I'm not sure.

---

