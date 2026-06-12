---
title: "Intrepid Server ZFS hard drive confusion"
date: 2009-01-12
forum: Server Platforms
---

### Post by mwinstead3790 on 2009-01-12
Alright, I'm running Intrepid server with zfs controlling two zpools. I want to add another drive to back up a pre-prepared backup for the root drive (not anything special, default partitioning/ext3 synchronized with rsyc); this drive is recognized as /dev/sdg when inserted. The problem is that /dev/sdg is currently used for a data drive in a zpool "vol0". So when I put in the new drive, It puts vol0 offline, if i remove it, everything goes back to normal.

So, I'm thinking that if i remove /dev/sdg from vol0, insert the new drive, then re-add the phisical disk back to the pool with its new designation, it'll work. But zfs doesn't support removing an in-use drive (or at least the version that i'm using). I've thought maybe creating a vdev data file on a different drive, adding it as a spare and then swapping /dev/sdg for the vdev (which would allow me to remove /dev/sdg). 

If i did that, what would be the most effective way of creating a ~40GB datafile? Otherwise, how could i re-designate the drives perhaps by using UUIDs, or something similar?

Here's some data:

I installed zfs from this repository (one I read on ubuntu documentation, if there's a different one I need to be using/the version held there would help me, plz let me know):

deb [http://ppa.launchpad.net/brcha/ubuntu](http://ppa.launchpad.net/brcha/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/brcha/ubuntu](http://ppa.launchpad.net/brcha/ubuntu) intrepid main

-Before Insertion-
```

root@file:~# zpool iostat -v

               capacity     operations    bandwidth
pool         used  avail   read  write   read  write
----------  -----  -----  -----  -----  -----  -----
multimedia   258G   169G     10      0  1.35M    167
  sdb1       115G  34.1G      4      0   618K     61
  sdf1       143G   135G      6      0   764K    105
----------  -----  -----  -----  -----  -----  -----
vol0         152G   169G      0      0  5.22K    117
  sdi       41.8G  15.2G      0      0  1.27K     25
  sdg       37.2G  75.0M      0      0  1.41K     20
  sdd       43.9G  30.6G      0      0  1.58K     29
  sdc       28.8G   123G      0      0    983     41
----------  -----  -----  -----  -----  -----  -----

root@file:~# zpool status
  pool: multimedia
 state: ONLINE
 scrub: none requested
config:

        NAME        STATE     READ WRITE CKSUM
        multimedia  ONLINE       0     0     0
          sdb1      ONLINE       0     0     0
          sdf1      ONLINE       0     0     0

errors: No known data errors

  pool: vol0
 state: ONLINE
 scrub: none requested
config:

        NAME        STATE     READ WRITE CKSUM
        vol0        ONLINE       0     0     0
          sdi       ONLINE       0     0     0
          sdg       ONLINE       0     0     0
          sdd       ONLINE       0     0     0
          sdc       ONLINE       0     0     0

errors: No known data errors

```

-After New Drive is Inserted-

```

root@file:~# zpool iostat -v
               capacity     operations    bandwidth
pool         used  avail   read  write   read  write
----------  -----  -----  -----  -----  -----  -----
multimedia   258G   169G    280      4  34.6M  29.4K
  sdb1       115G  34.1G    125      1  15.4M  12.0K
  sdf1       143G   135G    155      3  19.1M  17.4K
----------  -----  -----  -----  -----  -----  -----

```
```

root@file:~# zpool status
  pool: multimedia
 state: ONLINE
 scrub: none requested
config:

        NAME        STATE     READ WRITE CKSUM
        multimedia  ONLINE       0     0     0
          sdb1      ONLINE       0     0     0
          sdf1      ONLINE       0     0     0

errors: No known data errors

  pool: vol0
 state: UNAVAIL
status: One or more devices could not be used because the label is missing
        or invalid.  There are insufficient replicas for the pool to continue
        functioning.
action: Destroy and re-create the pool from a backup source.
   see: http://www.sun.com/msg/ZFS-8000-5E
 scrub: none requested
config:

        NAME        STATE     READ WRITE CKSUM
        vol0        UNAVAIL      0     0     0  insufficient replicas
          sdi       ONLINE       0     0     0
          sdg       UNAVAIL      0     0     0  corrupted data
          sdd       ONLINE       0     0     0
          sdc       ONLINE       0     0     0

```
```

root@file:~# fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x32673266

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9729    78148161   83  Linux

Disk /dev/sdb: 160.0 GB, 160000000000 bytes
16 heads, 63 sectors/track, 310019 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0xb9c919f4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      310019   156249544+  83  Linux

Disk /dev/sdc: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x61b9e64e

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdd: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6f8c6f8c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1        9729    78148161   8e  Linux LVM

Disk /dev/sde: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd81ab2a0

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1       91201   732572001   83  Linux

Disk /dev/sdf: 300.0 GB, 300069052416 bytes
255 heads, 63 sectors/track, 36481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x685e62e6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1       36481   293033601    7  HPFS/NTFS

Disk /dev/sdg: 6448 MB, 6448619520 bytes
255 heads, 63 sectors/track, 784 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0c60e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1               1         720     5783368+  83  Linux
/dev/sdg2             721         784      514080    5  Extended
/dev/sdg5             721         784      514048+  82  Linux swap / Solaris

Disk /dev/sdh: 10.2 GB, 10239860736 bytes
255 heads, 63 sectors/track, 1244 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x85bd85bd

   Device Boot      Start         End      Blocks   Id  System
/dev/sdh1   *           1        1186     9526513+  83  Linux
/dev/sdh2            1187        1244      465885    5  Extended
/dev/sdh5            1187        1244      465853+  82  Linux swap / Solaris

Disk /dev/sdi: 61.4 GB, 61471162368 bytes
255 heads, 63 sectors/track, 7473 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x700d700d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdi1               1        7473    60026841   8e  Linux LVM

```

Sorry, with all the data inserted like that, this post got really long, but thanks in advance to those who help.

---

### Post by electrogeist on 2009-01-16
Ok since noone else is picking at this...

> **mwinstead3790 said:**
> Otherwise, how could i re-designate the drives perhaps by using UUIDs, or something similar?

I think this is on the right track - however aren't UUID's only assigned to partitions?  From what I see, there are no partitions on the 4 disks comprising vol0.  ZFS is using the whole disks? And thats ok if it is!  You really don't need partitions as long as you remember not let a util do something stupid later mistaking it for a big unused drive.

Now I could be wrong about the feasibility of UUID's for non-partitioned drives, but if I'm not I can think of 2 alternatives:

1) Can you make ZFS use the drives referenced by /dev/disk/by-id/___ instead of /dev/sd_

2) Write some udev rules, at the least you should be able to have them named after checking the drive serial numbers

---

### Post by mwinstead3790 on 2009-01-17
Alright, I'm going to look into these options as soon as I get the time.

---

### Post by mwinstead3790 on 2009-01-17
Udev is the trick! Using rules to compare hard disk attributes and then creating rules for special devices in /dev makes up for this quirk of zfs-fuse. So, here's how I did it:

Reference [this]("http://ubuntuforums.org/showthread.php?t=168221"), most of what I'm doing is based off of it.

Then, open a terminal and get ready.

1) Find out which disks you're wanting to work with. We're looking for the /dev/sd_ 

```

fdisk -l

```

2) Now we get into the udev portion. I elected to use the SUBSYSTEM and model attributes to designate the drives. I could imagine that if one has multiple identical drives, you may want to add in the KERNELS option as well to specify the path through the buses to the drive. Be sure to replace the underscore with the disk you're working with. 

```

udevinfo -a -p $(udevinfo -q path -n /dev/sd_)

```

3) This command outputs a ton of information, but the best goodies are in the section with ATTRS{model} and ATTRS{vendor}. A cut-down version of mine for /dev/sdg follows with the most helpful lines in red.

```

root@file:~# udevinfo -a -p $(udevinfo -q path -n /dev/sdg) 

Udevinfo starts with the device specified by the devpath and then
walks up the chain of parent deices. It prints for every device
found, all possible attributes in the udev rules key format.
A rule to match, can be composed by the attributes of the device
and the attributes from one single parent device.

  looking at device '/devices/pci0000:00/0000:00:0f.1/host5/target5:0:1/5:0:1:0/block/sdg':
    KERNEL=="sdg"
    [COLOR="Red"]SUBSYSTEM=="block"[/COLOR]
    DRIVER==""
    ATTR{range}=="16"
    ATTR{removable}=="0"
    ATTR{ro}=="0"
    ATTR{size}=="78165360"
    ATTR{capability}=="12"
    ATTR{stat}==" 1125991    13850 264526933 44024770    24778      869  2194036   653510        0  7447280 44677070"

  looking at parent device '/devices/pci0000:00/0000:00:0f.1/host5/target5:0:1/5:0:1:0/block':
    KERNELS=="block"
    SUBSYSTEMS==""
    DRIVERS==""

  looking at parent device '/devices/pci0000:00/0000:00:0f.1/host5/target5:0:1/5:0:1:0':
    KERNELS=="5:0:1:0"
    SUBSYSTEMS=="scsi"
    DRIVERS=="sd"
    ATTRS{device_blocked}=="0"
    ATTRS{type}=="0"
    ATTRS{scsi_level}=="6"
    ATTRS{vendor}=="ATA     "
    [COLOR="Red"]ATTRS{model}=="WDC WD400EB-11CP"[/COLOR]
    ATTRS{rev}=="06.0"
    ATTRS{state}=="running"
    ATTRS{timeout}=="30"
    ATTRS{iocounterbits}=="32"
    ATTRS{iorequest_cnt}=="0x11932c"
    ATTRS{iodone_cnt}=="0x11932c"
    ATTRS{ioerr_cnt}=="0x0"
    ATTRS{modalias}=="scsi:t-0x00"
    ATTRS{evt_media_change}=="0"
    ATTRS{queue_depth}=="1"
    ATTRS{queue_type}=="none"

```

5) With this information, we can write our udev rule. The guide recommends a file with a name of 10-local.rules in /etc/udev/rules.d; the files in this directory are parsed in numerical order like those in the /etc/rc*.d/ directories, so if you decide to use something else, be sure to have your udev rules run before the others. Fire up you're favorite text editor and paste in something like this:

```

SUBSYSTEM=="block",ATTRS{model}=="WDC WD400EB-CP",KERNEL=="sd?1",NAME="zfs-WD40GB",SYMLINK="zfs-disks/IDE_WD40GB"

```

Since I'm working with zfs with these drives, I decided to make me a folder of symlinks to each drive for future reference along with prefixing the device names with "zfs-". Also, I noted that in some of my drive models there were spaces after the last letter of the model and the last quote. They are required for the rule to work, so adding "|grep ATTRS{model}>>/etc/udev/rules.d/10-local.rules" to the udev infor-gathering command will copy the exact model to the end of the file.

6) With the devices now made, I copied the data off of vol0, destroyed it and created a new vol0 with the new devices.

```

>umount /vol0

>zpool destroy vol0

>zpool create vol0 /dev/zfs-MX160GB /dev/zfs-MX60GB /dev/zfs-ST80GB /dev/zfs-WD40GB 

```

That was it, now I'm back up and running with the new designations. Note that the /dev/disk/ directories won't work as zfs won't dive further than /dev/, as noted [here]("http://groups.google.com/group/zfs-fuse/browse_thread/thread/e5f820c662fae8bf"). I may update the Ubuntu wiki page to note this quirk of zfs if the time/bordom arises.

Thanks to electrogeist!

---

