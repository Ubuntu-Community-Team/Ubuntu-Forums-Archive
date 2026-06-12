---
title: "Persistent mdraid partition"
date: 2007-11-18
forum: Server Platforms
---

### Post by galeron on 2007-11-18
Hi,

I used to have 2 250GB hard disks in a RAID1 array run by mdadm.

I transplanted these disks to another computer and used fdisk to format them, putting normal Linux partitions in place, as opposed to Linux RAID autodetect partitions previously.

However, a "blkid /dev/sdc1" says that the newly created partition is a mdraid partition.

I've ran fdisk and cfdisk many times but to no avail.

Attempting to ignore that, I used "mkfs -t xfs /dev/sdc1" to put a XFS filesystem on it, but mkfs.xfs complains that it cannot be found.

I'm at my wits' end here. Any help is greatly appreciated!

Thanks

---

### Post by koenn on 2007-11-18
what fdisk commands did you use to remove the md partition and replace it by an ordinary linux partition ?

---

### Post by galeron on 2007-11-18
Hi,

I used the standard "sudo fdisk /dev/sdc" command.

Then, within fdisk,
d (to delete my partition. /dev/sdc1 was automatically selected as it was the only partition)
n (to create new partition)
p (primary partition)
1 (select partition number)
<enter> (first cylinder/block - take defaults)
<enter> (last cylinder/block - take defaults, so the partition is the largest size possible)
t (select partition type, even though type 83 is the default)
83 (select Linux partition)
w (write changes to disk)

---

### Post by koenn on 2007-11-20
sounds about right. 
what does 
```
sudo fdisk -l 

```
say. (thats -l lowercase L for list)
it should show partitions with partition type, like so:
```
@ix:~# fdisk -l

Disk /dev/hda: 81.9 GB, 81964302336 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               9         639     5068507+  83  Linux
/dev/hda4             640         704      522112+  82  Linux swap / Solaris
```

---

### Post by galeron on 2007-11-21
```

Disk /dev/sdc: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x58293607

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       30515   245111706   fd  Linux raid autodetect

```

---

### Post by galeron on 2007-11-21
Another thing is that /dev/sdb is also an ex-mdadm member. I fdisk'ed it like I normally do, and the output of fdisk and blkid are inconsistent with each other

```

Disk /dev/sdb: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000eaa76

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30515   245111706   83  Linux

```

```

/dev/sdb1: UUID="3a25ce91-41cb-2677-f2c0-66ea4b422a58" TYPE="mdraid" 

```

Ideas?

---

### Post by koenn on 2007-11-21
strange. 
What if you try delete the partition table, and immediately write that change to disk (w in fdsik), then check (l) , should give an empty or non-existent partition table, then create and write a type 83 partition ? 

things to consider
you have to be root, I assume
you may have to reboot for the partition table to be re-read and thus for changes to become visible. 

Other than that, no, no ideas.

---

