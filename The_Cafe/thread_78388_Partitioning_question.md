---
title: "Partitioning question"
date: 2005-10-18
forum: The Cafe
---

### Post by joselin on 2005-10-18
Now i have this partition table:
```

HD -
    |- NTFS (winXP) 10GB
    |- Extended
          | - hda6 (/home) 10GB
          | - other ext partitions

```
Is there a way for modify it, for get the following? I will try it with gparted but don't allow me to do it.
```

HD -
    |- EXT3 (/home) 20GB
    |- Extended
          | - other ext partitions

```
I want to remove winXP partion and enlarge my home.

Any ideas???

Regards

---

### Post by az on 2005-10-18
0- back up your important data

Boot a live cd (like the installer or a graphical live cd)

Using parted or a graphical frontend to parted

1-delete partition 1

2- copy partition hda6 to where partition 1 was.

3- delete hda6

4-  make partition 1 bigger

5-  Change fstab (and grub if neccessary)

---

### Post by joselin on 2005-10-18
[QUOTE=azz]0- back up your important data

Boot a live cd (like the installer or a graphical live cd)

Using parted or a graphical frontend to parted


1-delete partition 1

2- copy partition hda6 to where partition 1 was.

3- delete hda6

4-  make partition 1 bigger

5-  Change fstab (and grub if neccessary)[/QUOTE]


I did points 1 and 2 without troubles. But when i try to delete hda6, can't do it. Seems that swap partition (hda9) is in use by the live cd. I received a message sending that i need to umount partitions greater than hda6 (i suppose that means hda7, hda8...), but i can't umount hda9.

Any ideas???

Regards.

---

### Post by erikpiper on 2005-10-18
Type sudo swapoff /dev/hda4 (Or hda whatever)

---

### Post by joselin on 2005-10-25
[QUOTE=erikpiper]Type sudo swapoff /dev/hda4 (Or hda whatever)[/QUOTE]

This works. But, only for general information:

After my last attemp, my partition table were like the following.
```

HD -
    |- hda1 (/home)
    |- Extended
         | - hda5 (can't remember mountpoint)
         | - free space
         | - hda6 (can't remember mountpoint)
         | - hda7 (can't remember mountpoint)
         | - others ....

```
hda1: could not be resized.
extended: could not be resized.
I tryed to copy hda7 to free space, and after that all extended partition dissapears.
I thought that when you copy a partition to other place (at least in gparted) the program try to rename al partions in the hd, and after rename the free space to hda6, the following were another hda6... the program fails and the info in all the extended partition dead. 

Be carefull... and sorry for my english..... ;)

Redards,
Jose

---

