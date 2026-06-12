---
title: "Trying to format a drive as ext4, unsupported disklabel?"
date: 2018-03-17
forum: Server Platforms
---

### Post by Higgins909 on 2018-03-17
I'm following this page to install another hdd. 

[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)

 According to "df -T" all my disks are "type" ext4.  I added a 2tb drive early last year and now I'm trying to add another of the exact same and can't figure out why I can't format it the want I want to.

I'm at the part of Command Line Formatting.  This is what the CLI looks like when I try to enter it.

```


root@DeSer:/home/admin-ben# fdisk mkfs -t ext4 /dev/sdf1
fdisk: unsupported disklabel: ext4
root@DeSer:/home/admin-ben#


```

Can someone tell me what I'm doing wrong?

Thanks,
    Higgins909

---

### Post by Dennis N on 2018-03-17
'disk label' is a synonym for the type of partition table the disk has: **msdos** or **gpt**. Creating one on an empty disk is the first step in setting up a new disk drive. After creating the disk label, you are then able to partition it and format the partitions (as ext4, for example).

gparted uses the term **partition table** rather than **disk label**.

If using gparted, **Device > Create Partition Table** will make a valid disk label.
If using parted, the command is **mklabel**

Using these will make any existing data on the disk unusable.

---

### Post by darkod on 2018-03-18
If you take a better look at that procedure you linked, you use fdisk only to create the partition and you format it with mkfs (not with fdisk like you are trying). I personally like using parted for creating partitions because it supports both msdos and gpt disks. fdisk should be used only for msdos.

Anyway, to format sdf1 you have two similar commands that do the same, so you can use any of them. I usually use the second one.
```
sudo mkfs -t ext4 /dev/sdf1
sudo mkfs.ext4 /dev/sdf1
```

That should achieve what you want...

---

