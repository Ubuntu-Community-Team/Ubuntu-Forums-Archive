---
title: "Problem with mdadm raid 5"
date: 2012-02-21
forum: Server Platforms
---

### Post by mxyzptlk1 on 2012-02-21
I have some problems with my raid. It started when I reinstalled my ubuntu server, and used the drives in my old raid 5, to create a completely new one. (had some bugs with my previous setup..

The problems seam to be that I didn't erase the drives before I reinstalled the server. My newly installed server tried to start the old raid at first start up. I then formatted the drives in the raid, and created a new raid (/dev/md1).

Now, every time I reboot my server, it tries to assemble both /dev/md0 (my old raid) and /dev/md127 (not a clue what that is all about). I have to manually stop these devices, and assemble my new raid, /dev/md1.
When I last did this, it started with 5 out of 6 drives... so I thought that I could add the last drive manually (mdadm --add /dev/sdb1). This, I guess, was not the way to do it... I added sdb1 as a spare device, and not as the device it should be.

When the server tries to assemble md0, it does it with just one device. /dev/sdf (not sdf1). This was one of the mistakes I made with the old server, which was one of the reasons as to why I was going to redo everything, and do it right this time.... I was never able to remove sdf from the raid, since it's not a partition....

This is what my files look like at the moment:

mdstat:
```

Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md1 : active raid5 sdb1[7] sdf1[6] sdg1[5] sde1[3] sdd1[2] sdc1[1]
      9767559680 blocks super 1.2 level 5, 512k chunk, algorithm 2 [6/5] [_UUUUU]
      [=============>.......]  recovery = 66.1% (1291673528/1953511936) finish=215.7min speed=51117K/sec
      
unused devices: <none>

```fdisk -l
```


Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0005bb0f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   484206591   242102272   83  Linux
/dev/sda2       484208638   488396799     2094081    5  Extended
/dev/sda5       484208640   488396799     2094080   82  Linux swap / Solaris

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
63 heads, 63 sectors/track, 984386 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x87eb524f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048  3907029167  1953513560   fd  Linux raid autodetect

Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
63 heads, 63 sectors/track, 984386 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xf40865d4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048  3907029167  1953513560   fd  Linux raid autodetect

Disk /dev/sdd: 2000.4 GB, 2000398934016 bytes
63 heads, 63 sectors/track, 984386 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x898dceae

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1            2048  3907029167  1953513560   fd  Linux raid autodetect

Disk /dev/sde: 2000.4 GB, 2000398934016 bytes
18 heads, 63 sectors/track, 3445352 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xcb79cc05

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1            2048  3907029167  1953513560   fd  Linux raid autodetect

Disk /dev/sdf: 2000.4 GB, 2000398934016 bytes
18 heads, 63 sectors/track, 3445352 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x566e97a1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1            2048  3907029167  1953513560   fd  Linux raid autodetect

Disk /dev/sdg: 2000.4 GB, 2000398934016 bytes
63 heads, 63 sectors/track, 984386 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x1eca617b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1            2048  3907029167  1953513560   fd  Linux raid autodetect

Disk /dev/mapper/cryptswap1: 2144 MB, 2144337920 bytes
255 heads, 63 sectors/track, 260 cylinders, total 4188160 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x8a9dcc3d


Disk /dev/md1: 10002.0 GB, 10001981112320 bytes
2 heads, 4 sectors/track, -1853077376 cylinders, total 19535119360 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 524288 bytes / 2621440 bytes
Disk identifier: 0x00000000


```mdadm.conf
```
DEVICE /dev/sdb1 /dev/sdc1 /dev/sdd1 /dev/sde1 /dev/sdf1 /dev/sdg1
ARRAY /dev/md1 metadata=1.2 name=mediaserver:1 UUID=486e13c8:c1ca1609:fa5242ce:a58b6eca

```fstab
```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=f7e48fe6-35be-4a86-8316-a7afe175ceb4 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
#UUID=16eed124-88b5-48f9-a586-8e40ecf58570 none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0

/dev/md1    /home/anton/media    ext4    defaults    1    2

```
Ask if you need any more information...
I really do appreciate any assistance on this! I'm really stuck!

---

### Post by rubylaser on 2012-02-21
Did you zero the superblock on /dev/sdf?

```
mdadm --zero-superblock /dev/sdf
```

---

### Post by mxyzptlk1 on 2012-02-22
> **rubylaser said:**
> Did you zero the superblock on /dev/sdf?

```
mdadm --zero-superblock /dev/sdf
```

What does it mean to do that? Since now, that drive is a part of my new raid.... If I were to do something that would erase it, it could harm my new raid?

---

### Post by rubylaser on 2012-02-22
That would not hurt your array.  I would bet if you do this, you have mdadm metadata on both the raw device and the partition.

```
mdadm -E /dev/sdf
mdadm -E /dev/sdf1
```

If this is the case, zeroing the superblock on the raw device will allow mdadm to assemble the array without problems.

---

### Post by kevinthecomputerguy on 2012-02-22
+1 rubylaser
 
I had a similar issue and that zero command fixed it for me.

---

