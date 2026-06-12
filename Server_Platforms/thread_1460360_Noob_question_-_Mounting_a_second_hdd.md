---
title: "Noob question - Mounting a second hdd"
date: 2010-04-22
forum: Server Platforms
---

### Post by twin-08 on 2010-04-22
Hey guys, I tried to mount my 2nd hdd and failed.

Is there anyway of deleteing 2 of the partitions of sdb that I have now atm and remaking them so that I can use it as a samba store drive.

Here is my fdisk info, ```

Disk /dev/sda: 40.0 GB, 40037760000 bytes
255 heads, 63 sectors/track, 4867 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000d8cfa

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4836    38845138+  8e  Linux LVM
/dev/sda2            4837        4867      249007+   5  Extended
/dev/sda5            4837        4867      248976   83  Linux

Disk /dev/sdb: 640.1 GB, 640135028736 bytes
16 heads, 63 sectors/track, 1240341 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0x79789ada

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               3     1240339   625129472    7  HPFS/NTFS
/dev/sdb2               2           2         504   83  Linux

Partition table entries are not in disk order

```

Thanks, Twin

---

### Post by cdenley on 2010-04-22
```

sudo apt-get install gparted
gksu gparted

```

---

### Post by arrrghhh on 2010-04-22
Isn't this the server section?  GParted doesn't work so well w/o X installed...

fdisk is probably what you should be looking at.

---

### Post by cdenley on 2010-04-22
> **arrrghhh said:**
> Isn't this the server section?  GParted doesn't work so well w/o X installed...

fdisk is probably what you should be looking at.

A server can have X even if the server edition's default configuration doesn't include it. I suppose I should have asked, though. He posted fdisk output, so he is aware of the command, but probably doesn't understand how to use it (as well as the mkfs command).

```

man fdisk
man mkfs

```

---

### Post by twin-08 on 2010-04-22
> **cdenley said:**
> A server can have X even if the server edition's default configuration doesn't include it. I suppose I should have asked, though. He posted fdisk output, so he is aware of the command, but probably doesn't understand how to use it (as well as the mkfs command).

Sorry when I run the command I get this (sorry for noob questions just trying to learn linux)

```
twin@linux-server:~$ gksu gparted

(gksu:9462): Gtk-WARNING **: cannot open display:

```

---

### Post by cdenley on 2010-04-22
> **twin-08 said:**
> Sorry when I run the command I get this (sorry for noob questions just trying to learn linux)

```
twin@linux-server:~$ gksu gparted

(gksu:9462): Gtk-WARNING **: cannot open display:

```

Apparently he was right, and you don't have X. Learn how to use fdisk and mkfs.

---

### Post by arrrghhh on 2010-04-22
> **cdenley said:**
> Apparently he was right, and you don't have X. Learn how to use fdisk and mkfs.

+1 my friend.  Don't need the unnecessary overhead of X just to manage your disks!!

---

### Post by twin-08 on 2010-04-22
Then what would be the commands to do it?

I tried researching and done some and failed =[

---

### Post by cdenley on 2010-04-22
> **twin-08 said:**
> Then what would be the commands to do it?

I tried researching and done some and failed =[
I already told you fdisk and mkfs.
```

sudo fdisk /dev/sdb

```
fdisk is generally interactive, so you will have to delete the partitions, create a partition, set the correct type, then write the new partition table. Then, assuming you have one partition, /dev/sdb1, and you want to make it an ext3 filesystem:
```

sudo mkfs -t ext3 /dev/sdb1

```

---

### Post by twin-08 on 2010-04-22
Ok I have deleted the partition however I don't understand how to set the correct type. I know that W writes the changes however how do I correct the types?

---

### Post by cdenley on 2010-04-22
> **twin-08 said:**
> Ok I have deleted the partition however I don't understand how to set the correct type. I know that W writes the changes however how do I correct the types?

```

Command (m for help): m
Command action
   a   toggle a bootable flag
   b   edit bsd disklabel
   c   toggle the dos compatibility flag
   d   delete a partition
   l   list known partition types
   m   print this menu
   **n   add a new partition**
   o   create a new empty DOS partition table
   p   print the partition table
   q   quit without saving changes
   s   create a new empty Sun disklabel
   **t   change a partition's system id**
   u   change display/entry units
   v   verify the partition table
   w   write table to disk and exit
   x   extra functionality (experts only)

```

You will probably want to use "83" to identify it as a Linux filesystem.

---

### Post by twin-08 on 2010-04-22
Which one of them corrects it, thats what I was meant to ask you.

---

### Post by cdenley on 2010-04-22
> **twin-08 said:**
> Which one of them corrects it, thats what I was meant to ask you.

Can you be more specific, or paste the text for fdisk where you are stuck?

---

### Post by twin-08 on 2010-04-22
I have deleted and recreated the partition however how do I correct the format/type of the drive?

---

### Post by cdenley on 2010-04-22
> **twin-08 said:**
> I have deleted and recreated the partition however how do I correct the format/type of the drive?

As the bolded text in the output I posted indicates, the letter "t" is used to "change a partition's system id".

---

### Post by twin-08 on 2010-04-22
Oh sorry thanks for the help :D

---

