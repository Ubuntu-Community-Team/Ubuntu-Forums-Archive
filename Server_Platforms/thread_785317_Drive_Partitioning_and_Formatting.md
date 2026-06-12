---
title: "Drive Partitioning and Formatting"
date: 2008-05-07
forum: Server Platforms
---

### Post by KrGAce on 2008-05-07
Hi,

Probably a simple solution is out there, however being somewhat new to Ubuntu, I have installed the 8.04 server and had it format my main drive.  I now have 3 other SATA drives in the box that need to be formatted and partitioned and thus mounted for use. (I left these alone during the install).  How can I do that within Ubuntu, with Gparted? or another way, preferably a GUI way, but with directions I can do command line if need be.

many thanks in advance.


Aceman

---

### Post by bluefrog on 2008-05-07
if you want GUI install ubuntu-desktop on top of your server.

Otherwise parted is simple enough to create partitions

with 3 disks you might want to consider LVM (pvcreate, vgcreate, lvcreate).
raid if your machine can stand it (ut it sad to leave out of the raid your fisrt disk)

James Dupin

---

### Post by songshu on 2008-05-07
if you have a live cd lying around you could use that to format the disks with gparted and then add them later in your /etc/fstab but why bother and ruin the fun ;)

if you do 
```
fdisk -l
```

you will get a list of your partitions like this below, you can see only 1 is formatted ( /dev/sdc) and the other ones are not

```
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1          12       96358+  83  Linux
/dev/sdc2             609       60801   483500272+   5  Extended
/dev/sdc3              13         608     4787370   83  Linux
/dev/sdc5             609         669      489951   82  Linux swap / Solaris
/dev/sdc6             670       60801   483010258+  8e  Linux LVM

Partition table entries are not in disk order

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sde: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdf: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System

```

then you could do
```
fdisk /dev/sdd
```


and then choose
```
n   add a new partition
```

when you have a partition you can format the drive like so

```
mkfs.ext3 /dev/sdd
```

with this done you could mount the disk with
mount /dev/sdd /the/place/you/choose

offcourse if you want to make this mount permanently
you couls do something like this
```
nano /etc/fstab
```

```
/dev/sdd /the/place/you/choose           ext3    defaults        0       2
```



or something like this

---

### Post by KrGAce on 2008-05-07
> **bluefrog said:**
> if you want GUI install ubuntu-desktop on top of your server.

Otherwise parted is simple enough to create partitions

with 3 disks you might want to consider LVM (pvcreate, vgcreate, lvcreate).
raid if your machine can stand it (ut it sad to leave out of the raid your fisrt disk)

James Dupin

Yeah I have installed the GUI (sorry server gurus, the Windows in me, made me) but right now I cannot "see" the drives, because I think they need to be formatted.  Gparted in GUI let me do that?

AceMan

---

### Post by songshu on 2008-05-07
sounds about correct.
if your disk is not mounted to your system, the system can not see it.

fdisk would show the drives as would gparted.

fdisk is already installed, gparted is in the repo's

apt-get install gparted or via synaptic if you really have to ;)

---

### Post by KrGAce on 2008-05-07
> **songshu said:**
> sounds about correct.
if your disk is not mounted to your system, the system can not see it.

fdisk would show the drives as would gparted.

fdisk is already installed, gparted is in the repo's

apt-get install gparted or via synaptic if you really have to ;)

Okay great thanks, I downloaded gparted on my laptop (where I have 8.04 desktop installed) just to see if it was in there.  Will try it on my new server later today.  Thanks for the responses to all.  Between Google and this Ubuntu Forum, what more could you really need?

Thanks again,

AceMan

---

### Post by songshu on 2008-05-07
good question

[IMG]http://stuffeducatedlatinoslike.files.wordpress.com/2008/03/beer.jpg[/IMG]

---

### Post by KrGAce on 2008-05-07
Oh yeah...sorry...that helps too.  Especially if it's ice cold.


;)

---

