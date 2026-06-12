---
title: "RAID 5, one disk failed.  Will not start degraded, mdadm: cannot load array metadata"
date: 2014-03-11
forum: Server Platforms
---

### Post by steve_bell2 on 2014-03-11
I have a vexing conundrum.  

I have a software RAID-5 with 5 disks (Seagate ST31500341AS).  SMART was saying that one was at risk of IMMINENT FAILURE.  I had done this before (those HDDs are known for a short lifespan) and it was pretty straightforward, so I went ahead and replaced it with a new disk, also a 1500GB Seagate.   The array wouldn't start in degraded mode, and any command from mdadm would fail saying that the device was busy.  It seemed like it was busy taunting me.

This seemed like a similar situation:  [http://ubuntuforums.org/showthread.php?t=854528](http://ubuntuforums.org/showthread.php?t=854528)

So I followed the instructions there, ultimately running
```

sudo mdadm --assemble --run --force /dev/md0 /dev/sd[bdef]**1**
```

since the good disks were sd[bdef].  Well, I think this made the problem worse, because now I have a new, bogus, not running partially assembled RAID array called /dev/md126 (my original one is called servyRAID). 

Now when I try to add the new disk as a component in Disk Utility  I'm getting "Error adding component to array", with details "Error  adding spare:  mdadm exited with exit code 1:mdadm: cannot load array  metadata from /dev/md127.

 Since people ask, here is the /etc/mdadm/mdadm.conf, which is basically stock:

```

servy:~> cat /etc/mdadm/mdadm.conf
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE partitions

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays

# This file was auto-generated on Fri, 01 Oct 2010 07:48:19 -0700
# by mkconf $Id$

```
and here is output from fdisk -l
```

servy:~> sudo fdisk -l
[sudo] password for steve:

Disk /dev/cciss/c0d0: 72.8 GB, 72833679360 bytes
255 heads, 63 sectors/track, 8854 cylinders, total 142253280 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000ef4a9

           Device Boot      Start         End      Blocks   Id  System
/dev/cciss/c0d0p1   *          63   136359719    68179828+  83  Linux
/dev/cciss/c0d0p2       136359720   142239509     2939895    5  Extended
/dev/cciss/c0d0p5       136359783   142239509     2939863+  82  Linux swap / Solaris

Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000519d9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63  3907024064  1953512001    7  HPFS/NTFS/exFAT

Disk /dev/sdc: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb952b952

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63  2930272064  1465136001   fd  Linux raid autodetect

Disk /dev/sdg: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0003d7f6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1              63  2930272064  1465136001   fd  Linux raid autodetect

Disk /dev/sdh: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b382a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdh1              63  2930272064  1465136001   fd  Linux raid autodetect

Disk /dev/sdi: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc866121e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdi1              63  2930272064  1465136001   fd  Linux raid autodetect

Disk /dev/sdj: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc8661221

   Device Boot      Start         End      Blocks   Id  System
/dev/sdj1              63  2930272064  1465136001   fd  Linux raid autodetect

```
/dev/sda1 is a backup disk where I (reassuringly) have all of my most important data backed up.  I am interested in getting the 330 DVDs that I have (legally) ripped, though, which isn't backed up and is hopefully still accessible on the 4 good disks.

I'm pretty much at the frontier of my knowledge and have started to make the situation worse.  I was hoping that this forum could reverse the trend.  Any help would be much appreciated.  Thanks!

---

