---
title: "Can't assemble RAID5 because partitions missing, but they don't!"
date: 2008-08-20
forum: Server Platforms
---

### Post by m0rtal on 2008-08-20
I've encountered really strange problem.
Moving my 4-disk RAID5 array from Gentoo, I've installed mdadm, inserted the disks, ran "mdadm --assemble /dev/md0 /dev/sda1 /dev/sdb1 /dev/scd1 /dev/sde1" and found that partitions sdc1 and sde1 doesn't exists:
```
mdadm: looking for devices for /dev/md0
mdadm: cannot open device /dev/sdb1: No such file or directory
mdadm: /dev/sdb1 has no superblock - assembly aborted
```
BUT!
fdisk -l:
```
Disk /dev/sda: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       48641   390708801   fd  Linux raid autodetect

Disk /dev/sdb: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       48641   390708801   fd  Linux raid autodetect

Disk /dev/sdc: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       48641   390708801   fd  Linux raid autodetect

Disk /dev/sdd: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb4150c31

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       48641   390708801   fd  Linux raid autodetect

Disk /dev/sde: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xefe5efe5

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *           1        9356    75152038+  83  Linux
/dev/sde2            9357        9733     3028252+   5  Extended
/dev/sde5            9357        9733     3028221   82  Linux swap / Solaris
```
hmmmph... I went further:
mdadm --examine /dev/sda1:
```
/dev/sda1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : f845899e:40bc078f:aa7fb7ac:da25494b
  Creation Time : Wed Aug 29 17:02:05 2007
     Raid Level : raid5
  Used Dev Size : 390708736 (372.61 GiB 400.09 GB)
     Array Size : 1172126208 (1117.83 GiB 1200.26 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0

    Update Time : Mon Jun  9 15:26:21 2008
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0
       Checksum : d472d27 - correct
         Events : 0.259976

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     0       8        1        0      active sync   /dev/sda1

   0     0       8        1        0      active sync   /dev/sda1
   1     1       8       17        1      active sync
   2     2       8       33        2      active sync
   3     3       8       49        3      active sync   /dev/sdd1

```
so I'm right, it's 4-drive RAID5 with only two working partitions...
and, of course, running "mdadm --examine /dev/sdb1" gives this:
```
mdadm: cannot open /dev/sdb1: No such file or directory
```
how it is possible when there IS such device in system?
dmesg | grep -i sdb:
```
[   38.496194] sd 1:0:0:0: [sdb] 781422768 512-byte hardware sectors (400088 MB)
[   38.496202] sd 1:0:0:0: [sdb] Write Protect is off
[   38.496204] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   38.496215] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   38.496240] sd 1:0:0:0: [sdb] 781422768 512-byte hardware sectors (400088 MB)
[   38.496247] sd 1:0:0:0: [sdb] Write Protect is off
[   38.496249] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   38.496260] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   38.496263]  sdb: sdb1
[   38.505509] sd 1:0:0:0: [sdb] Attached SCSI disk
```
I switched back to Gentoo - RAID works fine!
WTF?!?!?!

---

### Post by fjgaude on 2008-08-20
Likely OS differences... you might try this in Ubuntu:

```
sudo --assemble -f --scan
```

And see what happens with the forced assemble.

Also take a look at your /etc/mdadm/mdadm.conf file and see if it was made correctly when you switched to Ubuntu. You should have deleted it and not used the one created in other than Ubuntu.

---

### Post by m0rtal on 2008-08-21
/etc/mdadm/mdadm.conf is "empty":
> # mdadm.conf
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

# This file was auto-generated on Wed, 20 Aug 2008 11:39:38 +0300
# by mkconf $Id$
and "mdadm --assemble -f --scan" gives this:
> mdadm: No arrays found in config file or automatically
I see the problem is not in array, it's some kind of misdetecting the drives themselves - two drives of four are seen with logical partitions, and other two don't? That's strange...

---

### Post by fjgaude on 2008-08-21
Okay, I've seen this before. Try this: uninstall **mdadm**, delete the mdadm.conf file in /etc/mdadm. Re-boot, then install mdadm and then do this:

```
sudo mdadm --assemble --scan
```

A new mdadm.conf file will be recreated, and you should be able to mount the array.

If not then something is different between the Gentoo mdadm, or md, than in Ubuntu.

Let us know how you are doing.

---

### Post by m0rtal on 2008-08-27
same :(

---

### Post by fjgaude on 2008-08-27
Maybe the mdadm.conf file is being placed in /etc and not in /etc/mdadm... something different between Gentoo and Ubuntu?

```
locate mdadm.conf
```

And see where the file is/

---

### Post by m0rtal on 2008-08-27
well, it's located where he belongs to, in /etc/mdadm/...

---

### Post by fjgaude on 2008-08-27
I guess we are left with the conclusion that Gentoo's **md** is different from Ubuntu's, eh?

I can't think of anything else to suggest.

---

### Post by m0rtal on 2008-08-27
it's very strange for me...
atm I can see only one option - buy a separate 1+TB HDD and copy all files on it in gentoo, then re-assemble array in ubuntu and copy all back...
expensive solution, though...

---

### Post by fjgaude on 2008-08-27
Well, terabyte drives are going for $169.00 in my area... no matter what, you ought to backup important data, raid or no raid. I use near-line and off-line backups... data is too important to loose.

BTW, I've moved my array through many motherboard and kernel updates without issue.

---

### Post by Multi-Medea on 2008-08-27
His problem is not with MD, it's with the kernel not finding the actual partitions (and thus creating entries in /dev).

Note that when he's trying to access /dev/sdb1 he's getting an error.

I've seen this problem in the past.  My kernel was not "seeing" the linux partition on a couple of SATA drives.  It was weird, because, for example, **fdisk /dev/sdb** would actually show that there was a linux partition on the disk.  Doing a **w** from fdisk fixed the problem, since it forced the kernel to reread the partition table, but it shouldn't have happened.

I haven't been able to reproduce the problem, but I'd be curious if the OP can give more info.

---

### Post by Multi-Medea on 2008-08-27
Stupid question, is there a reason why one should build an MD array out of actual partitions and not out of the whole disk?
If the /dev/sd?1 partitions cover the entire disk, why not simply us /dev/sd? as the compoments of the array (assuming that all drives are identical, of course)

---

### Post by m0rtal on 2008-08-27
> **fjgaude said:**
> BTW, I've moved my array through many motherboard and kernel updates without issue.
that's what bothers me much... soft raid is designed to be movable...

---

### Post by m0rtal on 2008-08-27
> **Multi-Medea said:**
> I've seen this problem in the past.  My kernel was not "seeing" the linux partition on a couple of SATA drives.  It was weird, because, for example, **fdisk /dev/sdb** would actually show that there was a linux partition on the disk.  Doing a **w** from fdisk fixed the problem, since it forced the kernel to reread the partition table, but it shouldn't have happened.
nice idea, I will try it tomorrow

---

### Post by fjgaude on 2008-08-28
Interesting, **fdisk -w**. All that does is print the version number of fdisk. I think I'm using only **cfdisk** from here on out... noticing in the man pages of the bugs in fdisk... <sigh>

Okay, kernels are different between Ubuntu and Gentoo...

I've made arrays from the whole disk, i.e., /sda as well as /sda1, just one partition of the whole disk. Soon will have the time to experiment more with arrays and mdadm... updating my six-drive system. <smile>

---

### Post by Multi-Medea on 2008-08-28
[QUOTE=fjgaude;5681170]Interesting, **fdisk -w**. All that does is print the version number of fdisk. I think I'm using only **cfdisk** from here on out... noticing in the man pages of the bugs in fdisk... <sigh>

No, not **fdisk -w**, run fdisk and give it the w command (write partition table)

---

### Post by fjgaude on 2008-08-29
Oh, and thanks. The write command, I see says the blind man. Still will always use cfdisk... <smile>

---

### Post by m0rtal on 2008-09-03
well, guys, I guess problem is in ubuntu's mdadm, and here's why:
when I remove mdadm, system can see and access ALL partitions, including those for raid, but after installing mdadm and rebooting, I can't acces them again.
Removing mdadm resolves access issue again.
Possible bug?

---

### Post by fjgaude on 2008-09-03
Bug, I can't... I've not much experience with partitioning an array, just using the array with whole drives, no partitions.

When you assemble the array, you see the partitions? I'm not following some of this.

After you have deleted the mdadm.conf file, uninstalled mdadm, rebooted, reinstalled mdadm, what does the mdadm.conf file look like?

---

### Post by m0rtal on 2008-09-04
mdadm.conf after removal, reboot, installation, reboot:
> # mdadm.conf
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
ARRAY /dev/md0 level=raid5 num-devices=3 UUID=fb8f5b47:1055b846:60bf95cb:a84fa631
ARRAY /dev/md0 level=raid5 num-devices=4 UUID=f845899e:40bc078f:aa7fb7ac:da25494b

# This file was auto-generated on Thu, 04 Sep 2008 11:18:53 +0300
# by mkconf $Id$
once again: when I remove mdadm, I can see partitions, when I install it, two of four partitions disappears.

---

### Post by fjgaude on 2008-09-04
```
# definitions of existing MD arrays
ARRAY /dev/md0 level=raid5 num-devices=3 UUID=fb8f5b47:1055b846:60bf95cb:a84fa631
ARRAY /dev/md0 level=raid5 num-devices=4 UUID=f845899e:40bc078f:aa7fb7ac:da25494b
```

These two lines show something irregular for sure. Two /dev/md0s with different UUIDs, and with a different number of devices. I wonder how that can come about?

The partitions you can see when mdadm is removed, they are not part of the array, huh?

I don't have any experience using an array with partitions not part of the array. But in Gentoo you are okay? I don't know what to tell you other than re-create after you have backed up all your data on the array.

---

### Post by m0rtal on 2008-09-27
I think I've found reason why I can't assemble my array:
mdadm --assemble --scan -v
> mdadm: looking for devices for further assembly
mdadm: no recogniseable superblock on /dev/disk/by-id/md-uuid-fb8f5b47:1055b846:60bf95cb:a84fa631
mdadm: **/dev/sdd1 is not built for host m0rtal-desktop**.
mdadm: no recogniseable superblock on /dev/sdd
mdadm: cannot open device /dev/sdc1: Device or resource busy
mdadm: cannot open device /dev/sdc: Device or resource busy
mdadm: cannot open device /dev/sdb1: Device or resource busy
mdadm: cannot open device /dev/sdb: Device or resource busy
mdadm: **/dev/sda1 is not built for host m0rtal-desktop**.
mdadm: no recogniseable superblock on /dev/sda

Now I will try to omit "not built" error.
Why other disks are busy - it's another interesting question...

---

### Post by fjgaude on 2008-09-27
Glad you are back at it... so many things to get right before all works correctly, eh?

---

### Post by m0rtal on 2008-09-27
Thanks :) Had a really tough days... nevertheless:

according to man pages, **mdadm --assemble --scan --auto-update-homehost** should help:
> If mdadm cannot find any array for the given host at all, and if --auto-update-homehost is given, then mdadm will search again for any array (not just an array created for this host) and will assemble each assuming --update=homehost. This will change the host tag in the superblock so that on the next run, these arrays will be found without the second pass. The intention of this feature is to support transitioning a set of md arrays to using homehost tagging. 
I was really glad to find it out, stopped /dev/md0, ran the command and...
> mdadm: SET_ARRAY_INFO failed for /dev/md/0: Device or resource busy
how can I see what's preventing me from writing to /dev/md/0 and why a hell mdadm needs **/md/0** instead of **/md0**?

---

### Post by m0rtal on 2008-09-27
Does anyone knows other correct way to update *homehost* info of the disk?

---

### Post by fjgaude on 2008-09-27
Well, I have no idea what is going on here... stop your array, unmount it. Then see if you can assemble, update host name.

I'm not sure if you've done this: delete the /etc/mdadm/mdadm.conf file, remove program mdadm, reboot, re-install mdadm, then do the assemble, scan, and see what happens.

In the mdadm.conf file you should be able to simply have HOMEHOST <system>. Did you change that for some reason?

---

### Post by m0rtal on 2008-09-27
> **fjgaude said:**
> Well, I have no idea what is going on here... stop your array, unmount it. Then see if you can assemble, update host name.
I can't assemble array - it consists of four drives, while system "sees" only two:
[i]mdadm: cannot open device /dev/sdb1: No such file or directory
mdadm: /dev/sdb1 has no superblock - assembly aborted[/i]

> I'm not sure if you've done this: delete the /etc/mdadm/mdadm.conf file, remove program mdadm, reboot, re-install mdadm, then do the assemble, scan, and see what happens.
I did it, always the same - only two drives of four appears to have valid info for assembling (so-called superblock).

> In the mdadm.conf file you should be able to simply have HOMEHOST <system>. Did you change that for some reason?
I tried removing it, setting to actual hostname, reverting to default "<system>" state... nothing helps!

---

### Post by m0rtal on 2008-09-27
BTW, these raid works correctly in Gentoo **_WITHOUT_** mdadm.conf at all!

---

### Post by fjgaude on 2008-09-27
I can't think of anything else to suggest... except to re-create in Ubuntu after you have saved all the important stuff on the array. Sorry about that!

---

### Post by m0rtal on 2008-09-27
Somehow I've managed to change UUID's of two of the drives - sda & sdd:
> /dev/sda1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : f845899e:40bc078f:2a9fac23:f1c4d926 **(local to host m0rtal-desktop)**
  Creation Time : Wed Aug 29 17:02:05 2007
     Raid Level : raid5
  Used Dev Size : 390708736 (372.61 GiB 400.09 GB)
     Array Size : 1172126208 (1117.83 GiB 1200.26 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0

    Update Time : Sat Sep 27 18:19:08 2008
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0
       Checksum : a597df07 - correct
         Events : 0.259984

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     0       8        1        0      active sync   /dev/sda1

   0     0       8        1        0      active sync   /dev/sda1
   1     1       8       17        1      active sync
   2     2       8       33        2      active sync
   3     3       8       49        3      active sync   /dev/sdd1

But, as usual, other two drives aren't available. Futhermore, now I can't access raid from Gentoo, so solution with moving all data to single drive is not available anymore :(
Please help :-/

---

### Post by fjgaude on 2008-09-27
What does the -D in mdadm show?

And what does your mdadm.conf file look like now?

As you likey know, the UUID for each drive is the same as the UUID for the array as shown in -E or -D.

---

### Post by trmentry on 2008-09-27
i"m not going to be much help here... but I did have an odd issue recently where I had my md0 showing up with 2 uuid strings.  this was after i moved the array from 1 ubuntu server to another.  7.10 to 8.04.1

Anyway... I was able to get the array up but it kept throwing drives and going degraded.

figured it was b/c of the 2nd uuid that wasn't in use.  

so i backed up my data, stopped the array, and wiped out the super blocks.

```

mdadm --zero-superblock /dev/sd[abcdefgh]

```

this effectively destroyed the array.. so dont' do it unless you absolute need to.

but after I did that and recreated the array... it stopped tossing random drives out of the array as failed.

i'm thinking that you're going to need to backup your data and do this, as even if you get it online, I suspect you will run into the random drive failure thing on the array with 2 differnet uuid.

---

### Post by m0rtal on 2008-09-27
> **fjgaude said:**
> What does the -D in mdadm show?
```
/dev/md0:
        Version : 00.90.03
  Creation Time : Wed Aug 29 16:26:35 2007
     Raid Level : raid5
     Array Size : 781422592 (745.22 GiB 800.18 GB)
  Used Dev Size : 390711296 (372.61 GiB 400.09 GB)
   Raid Devices : 3
  Total Devices : 2
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Wed Aug 29 16:32:53 2007
          State : clean, degraded
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : fb8f5b47:1055b846:2a9fac23:f1c4d926 (local to host m0rtal-desktop)
         Events : 0.14

    Number   Major   Minor   RaidDevice State
       0       0        0        0      removed
       1       8       16        1      active sync   /dev/sdb
       2       8       32        2      active sync   /dev/sdc
```
> And what does your mdadm.conf file look like now?
```
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
ARRAY /dev/md0 level=raid5 num-devices=4 UUID=f845899e:40bc078f:2a9fac23:f1c4d926

# This file was auto-generated on Sat, 27 Sep 2008 18:23:11 +0300
# by mkconf $Id$
```
note that I've removed line with num-devices=3 as it's totally incorrect
> As you likey know, the UUID for each drive is the same as the UUID for the array as shown in -E or -D.
yes, I know! and here they are:
UUID of an "array" (2 drives instead of 4): **fb8f5b47:1055b846:2a9fac23:f1c4d926**
vol_id of /dev/sda1:
```
ID_FS_USAGE=raid
ID_FS_TYPE=linux_raid_member
ID_FS_VERSION=0.90.0
ID_FS_UUID=**f845899e:40bc078f:2a9fac23:f1c4d926**
ID_FS_UUID_ENC=f845899e:40bc078f:2a9fac23:f1c4d926
ID_FS_LABEL=
ID_FS_LABEL_ENC=
ID_FS_LABEL_SAFE=

```
vol_id of /dev/sd**b1**:
```
/dev/sdb1: error opening volume
```
vol_id of /dev/sd**b**:
```
ID_FS_USAGE=raid
ID_FS_TYPE=linux_raid_member
ID_FS_VERSION=0.90.0
ID_FS_UUID=**fb8f5b47:1055b846:2a9fac23:f1c4d926**
ID_FS_UUID_ENC=fb8f5b47:1055b846:2a9fac23:f1c4d926
ID_FS_LABEL=
ID_FS_LABEL_ENC=
ID_FS_LABEL_SAFE=

```
sdc = sdb
sdd1 = sda1

same with mdadm --examine

EDIT:
holy crap... only now I'm noticing that they have different UUIDs!...
what a hell?! how can this happen?! what should I do now?

The "ARRAY" strings from automatically created mdadm.conf looks like:
ARRAY /dev/md0 level=raid5 num-devices=3 UUID=fb8f5b47:1055b846:2a9fac23:f1c4d926
ARRAY /dev/md0 level=raid5 num-devices=4 UUID=f845899e:40bc078f:2a9fac23:f1c4d926
We have here both UUIDs... and now I'm totally stunned... where to go from here?

---

### Post by m0rtal on 2008-09-27
> **trmentry said:**
> i"m not going to be much help here...
no you wrong! at least I get responses and thus moral support :)
anyway, guys, I'm overwhelmed with information, I'm still noob in linux, it's only my first 6 or so months, I'm stunned and frustrated...
I feel that the correct answer is nearby, it can be somehow connected with the mdadm seeing some parts of the array on partitions and other on disks (sda1 comparing to sdb), while they all still identical for fdisk, for example...
Hope I'll get enlightened soon and will be able to recover my data :)

---

### Post by m0rtal on 2008-09-27
To collect all things together.
fdisk -l sees everything fine:
```
Disk /dev/sda: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       48641   390708801   fd  Linux raid autodetect

Disk /dev/sdb: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       48641   390708801   fd  Linux raid autodetect

Disk /dev/sdc: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       48641   390708801   fd  Linux raid autodetect

Disk /dev/sdd: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb4150c31

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       48641   390708801   fd  Linux raid autodetect

```
mdadm, vol_id, blkid sees two disks with partitions (sda1 & sdd1) and two without (sdb & sdc).
Before I start messing with UUIDs, I was able to access raid from Gentoo regarding "different" partitioning schema's (I was creating that array simply copying first disk with dd, so they CAN'T be different).
In Ubuntu, I find out that I can't assemble array because of stupid *homehost* property, so I ran *mdadm --assemble --scan --auto-update-homehost*, and it rewrote UUIDs. [color=#999999]Now I can't access array from Gentoo too, stupid me :([/color]
Switching back to Gentoo shows that mdadm and other stuff _can_ access sdb1 and sdc1 partitions (!), but since they have incorrect UUID (due to homehost update), I can't assemble array here too. BTW, in Gentoo *--auto-update-homehost* or *--update=uuid* does absolutely nothing, mdadm keeps repeating that those partitions have incorrect UUID :( (which are now f845899e:40bc078f:aa7fb7ac:da25494b, like was all drives in the beginning)

---

### Post by fjgaude on 2008-09-27
I can't say how the UUIDs became different, and how sda became sda1.

You create using the whole disks, or using a partition that covers the whole disk.

The UUID tha mdadm gives the drives and the array is not the same UUID that the kernel gives the drives when it first recognizes them.

Think back, all the things that you did, is anything there that comes to mind? But please do relax while you are thinking about all this.

---

