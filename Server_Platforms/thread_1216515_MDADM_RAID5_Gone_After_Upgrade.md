---
title: "MDADM RAID5 Gone After Upgrade"
date: 2009-07-18
forum: Server Platforms
---

### Post by MilkeySUFC on 2009-07-18
Help!

I had a Ubuntu 8.10 machine with OS on small IDE drive & 3 500Mb SATA in MDADM RAID5.

When I did an upgrade to 9.04, my RADI5 is no longer available.

GParted shows the 3 disks as unallocated.

What can I do to try get the RAID5 back?

Milkey

---

### Post by fjgaude on 2009-07-18
Try simply doing this:

```
sudo mdadm --examine --scan --config=mdadm.conf >> /etc/mdadm/mdadm.conf
```

That should do it. Let us know how things go.

---

### Post by MilkeySUFC on 2009-07-20
> **fjgaude said:**
> Try simply doing this:

```
sudo mdadm --examine --scan --config=mdadm.conf >> /etc/mdadm/mdadm.conf
```

That should do it. Let us know how things go.

It did! Thank you. And running:

mdadm -A -s

Started them (with 2 drives out of 3)

Does that mean it's only picked up 2 drives? Or because it's RAID5 it's a slightly ambiguous message?

Also I see two drives in my "Places" menu. Not a huge issue, granted, but I'd like to understand why - if possible.


Many thanks,
Milkey

---

### Post by fjgaude on 2009-07-20
It's not right. What does this show:

```
sudo mdadm -D /dev/md0
```

or whatever your array is named.

Also could you show your ```
mdadm.conf
``` file?

---

### Post by MilkeySUFC on 2009-07-29
I was called away for work "a few days" - never expected it to take this long!!

Here's the relevant info:

```
/dev/md0:
        Version : 00.90
  Creation Time : Sat Sep 13 22:01:45 2008
     Raid Level : raid5
     Array Size : 976772992 (931.52 GiB 1000.22 GB)
  Used Dev Size : 488386496 (465.76 GiB 500.11 GB)
   Raid Devices : 3
  Total Devices : 2
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Mon Jul 20 06:47:09 2009
          State : clean, degraded
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : 1f659e11:e42b9499:d55eef21:1448959e (local to host MZJ-Tower)
         Events : 0.14116

    Number   Major   Minor   RaidDevice State
       0       0        0        0      removed
       1       8       16        1      active sync   /dev/sdb
       2       8       32        2      active sync   /dev/sdc

```

and

```
mike@MZJ-Tower:/etc$ cat /etc/mdadm/mdadm.conf
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

# This file was auto-generated on Sat, 13 Sep 2008 21:30:34 +0100
# by mkconf $Id$
ARRAY /dev/md0 level=raid5 num-devices=3 UUID=1f659e11:e42b9499:d55eef21:1448959e

```

What seems to be the problem, doctor?

---

### Post by MilkeySUFC on 2009-07-29
Another update:

sudo mdadm -E /dev/sda

```

dev/sda:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 1f659e11:e42b9499:d55eef21:1448959e (local to host MZJ-Tower)
  Creation Time : Sat Sep 13 22:01:45 2008
     Raid Level : raid5
  Used Dev Size : 488386496 (465.76 GiB 500.11 GB)
     Array Size : 976772992 (931.52 GiB 1000.22 GB)
   Raid Devices : 3
  Total Devices : 3
Preferred Minor : 0

    Update Time : Wed Jul 29 16:24:31 2009
          State : clean
 Active Devices : 2
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 1
       Checksum : 46be3964 - correct
         Events : 14136

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     3       8        0        3      spare   /dev/sda

   0     0       0        0        0      removed
   1     1       8       16        1      active sync   /dev/sdb
   2     2       8       32        2      active sync   /dev/sdc
   3     3       8        0        3      spare   /dev/sda

```

---

### Post by fjgaude on 2009-07-29
Okay, but is what you showed for your **mdadm.conf** file really what you get? It shows a date months old. Did you edit the original to show the new UUID for the array?

If this was my array, I'd try simply adding the /dev/sda back in:

```
sudo mdadm /dev/md0 --add /dev/sda
```

and see what happens.

Most of us have found it is better to have one partition instead of using the whole drive, i.e., sda1 and not sda. I forget why at the moment.

Use this to see the re-sync of the array:

```
sudo watch cat /proc/mdstat
```

Let us know if the add-drive worked. Thanks!

---

### Post by MilkeySUFC on 2009-07-29
Definitely what I get after your post #2. I didn't have an mdadm.conf before that.

```
sudo mdadm /dev/md0 --add /dev/sda
``` 

gives:

With array started
```
mdadm: Cannot open /dev/sda: Device or resource busy

```

With array stopped
```
mdadm: cannot get array info for /dev/md0

```

It was a long time ago I originally built the RAID5 (and I'm not totally sure how I built it!!)

---

### Post by fjgaude on 2009-07-29
Okay with the mdadm.conf file.

Gosh, sounds like the /sda is bad as a drive. But likely not. If it is truly a spare then it has to have its superblock zeroed:

```
sudo mdadm --zero-superblock /dev/sda
```

This will get it out of being part of the original array.

Just a later thought, try assembleing the array like so:

```
sudo mdadm --assemble --scan
```

This will assemble with /sda if all three drives have the same UUID, the one that is in your mdadm.conf file. If this doesn't work, do the superblock zero.

---

### Post by grantemsley on 2009-07-29
If it's the problem I ran into, the drive is NOT bad...it has been added as a separate array.

When I rebooted my server with no array listed in mdadm.conf, it built /dev/md0 with just one disk.  When I tried to rebuild the array, it added the remaining 3 disks to a second array...and I couldn't remove the first one.

Check to see if you have multiple arrays listed in /proc/mdstat.  If you do, you'll need to remove the badly configured one before you can add the disk back to the array.  Unfortunately, at this point, it's going to automatically rebuild the array when you put the drive in.

---

### Post by MilkeySUFC on 2009-07-30
Thanks for all your help, again.

Strangely, even though the 
```
sudo mdadm /dev/md0 --add /dev/sda
```

gave me errors, after rebooting, and on a whim running 

```
sudo watch cat /proc/mdstat
```

showed the array rebuilding and eventually it finished, et voila! I now belive I have a fully working RAID5 array again.

Thanks,
Milkey

---

### Post by fjgaude on 2009-07-30
Wow, wonder what we have learned from all this... anyway, glad things are finally working correctly.

---

