---
title: "mdadm: doesn't contain a valid partition table after reboot"
date: 2011-04-14
forum: Server Platforms
---

### Post by fermulator on 2011-04-14
This is really weird.

As per [http://ubuntuforums.org/showthread.php?t=1719427](http://ubuntuforums.org/showthread.php?t=1719427), I had a working array.  I failed out one of the drives for fun.

```
fermulator@fermmy-server:/mnt$ cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md2000 : active raid6 sdk[3] sdl[0] sdj[1]
      3907026944 blocks level 6, 64k chunk, algorithm 2 [4/3] [UU_U]
```

Yet ... fdisk claims these disks no longer have /dev/sdX1 partitions ... :-(

```
fermulator@fermmy-server:/mnt$ sudo fdisk -ulc /dev/sd[klj]

Disk /dev/sdj: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdj doesn't contain a valid partition table

Disk /dev/sdk: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdk doesn't contain a valid partition table

Disk /dev/sdl: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdl doesn't contain a valid partition table

```

Even the disk that I had failed out previously claims invalid partition:

```
fermulator@fermmy-server:/mnt$ sudo fdisk -ulc /dev/sdi

Disk /dev/sdi: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdi doesn't contain a valid partition table

```

Even still ... mdadm recognizes the superblock on these devices:

```
fermulator@fermmy-server:/mnt$ sudo mdadm -E /dev/sd[ijkl]
/dev/sdi:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 74fae2cf:63dcb956:01f5a1db:50a22640 (local to host fermmy-server)
  Creation Time : Sat Apr  2 12:04:52 2011
     Raid Level : raid6
  Used Dev Size : 1953513472 (1863.02 GiB 2000.40 GB)
     Array Size : 3907026944 (3726.03 GiB 4000.80 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 2000

    Update Time : Sat Apr  2 15:22:10 2011
          State : active
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0
       Checksum : e43ac053 - correct
         Events : 7

     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     2       8      208        2      active sync

   0     0       8      176        0      active sync   /dev/sdl
   1     1       8      192        1      active sync
   2     2       8      208        2      active sync
   3     3       8      224        3      active sync
/dev/sdj:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 74fae2cf:63dcb956:01f5a1db:50a22640 (local to host fermmy-server)
  Creation Time : Sat Apr  2 12:04:52 2011
     Raid Level : raid6
  Used Dev Size : 1953513472 (1863.02 GiB 2000.40 GB)
     Array Size : 3907026944 (3726.03 GiB 4000.80 GB)
   Raid Devices : 4
  Total Devices : 3
Preferred Minor : 2000

    Update Time : Thu Apr 14 20:54:57 2011
          State : clean
 Active Devices : 3
Working Devices : 3
 Failed Devices : 1
  Spare Devices : 0
       Checksum : e44b8223 - correct
         Events : 20912

     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     1       8      144        1      active sync   /dev/sdj

   0     0       8      176        0      active sync   /dev/sdl
   1     1       8      144        1      active sync   /dev/sdj
   2     2       0        0        2      faulty removed
   3     3       8      160        3      active sync   /dev/sdk
/dev/sdk:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 74fae2cf:63dcb956:01f5a1db:50a22640 (local to host fermmy-server)
  Creation Time : Sat Apr  2 12:04:52 2011
     Raid Level : raid6
  Used Dev Size : 1953513472 (1863.02 GiB 2000.40 GB)
     Array Size : 3907026944 (3726.03 GiB 4000.80 GB)
   Raid Devices : 4
  Total Devices : 3
Preferred Minor : 2000

    Update Time : Thu Apr 14 20:54:57 2011
          State : clean
 Active Devices : 3
Working Devices : 3
 Failed Devices : 1
  Spare Devices : 0
       Checksum : e44b8237 - correct
         Events : 20912

     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     3       8      160        3      active sync   /dev/sdk

   0     0       8      176        0      active sync   /dev/sdl
   1     1       8      144        1      active sync   /dev/sdj
   2     2       0        0        2      faulty removed
   3     3       8      160        3      active sync   /dev/sdk
/dev/sdl:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 74fae2cf:63dcb956:01f5a1db:50a22640 (local to host fermmy-server)
  Creation Time : Sat Apr  2 12:04:52 2011
     Raid Level : raid6
  Used Dev Size : 1953513472 (1863.02 GiB 2000.40 GB)
     Array Size : 3907026944 (3726.03 GiB 4000.80 GB)
   Raid Devices : 4
  Total Devices : 3
Preferred Minor : 2000

    Update Time : Thu Apr 14 20:54:57 2011
          State : clean
 Active Devices : 3
Working Devices : 3
 Failed Devices : 1
  Spare Devices : 0
       Checksum : e44b8241 - correct
         Events : 20912

     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     0       8      176        0      active sync   /dev/sdl

   0     0       8      176        0      active sync   /dev/sdl
   1     1       8      144        1      active sync   /dev/sdj
   2     2       0        0        2      faulty removed
   3     3       8      160        3      active sync   /dev/sdk

```

Obviously, /dev/sdi used to be /dev/sdl.  In order to re-add /dev/sdi to the array, I'll have to wipe the superblock and manually re-add.

QUESTION: Why do the disks claim invalid partition tables now?  Before proceeding, I want to make sure there's nothing wrong ...

And ... this is scary.  Is mdadm using the DEVICES rather than the partitions as members of the array since the reboot???

```
fermulator@fermmy-server:/mnt$ sudo mdadm --query --detail /dev/md2000
/dev/md2000:
        Version : 00.90
  Creation Time : Sat Apr  2 12:04:52 2011
     Raid Level : raid6
     Array Size : 3907026944 (3726.03 GiB 4000.80 GB)
  Used Dev Size : 1953513472 (1863.02 GiB 2000.40 GB)
   Raid Devices : 4
  Total Devices : 3
Preferred Minor : 2000
    Persistence : Superblock is persistent

    Update Time : Thu Apr 14 20:54:57 2011
          State : clean, degraded
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0

     Chunk Size : 64K

           UUID : 74fae2cf:63dcb956:01f5a1db:50a22640 (local to host fermmy-server)
         Events : 0.20912

    Number   Major   Minor   RaidDevice State
       0       8      176        0      active sync   /dev/sdl
       1       8      144        1      active sync   /dev/sdj
       2       0        0        2      removed
       3       8      160        3      active sync   /dev/sdk

```

---

### Post by mn_voyageur on 2011-04-15
This is exactly what was happening to me.  Eventually, I lost all but one drive.

Edit:I never switched to drives, I always had the partition, sdb1, sdc1, etc, but I lost the drive as you did.

Now, [COLOR="Blue"][md0 does not have a valid partition table.]("http://ubuntuforums.org/showpost.php?p=10678336&postcount=9")[/COLOR]

It will be interesting to see what suggestions you receive.  

Not to digress, but how did you get the scroll bar to appear in your 4th section of code?

Thanks,
MarkN

---

### Post by dtfinch on 2011-04-15
fermulator:
You made a raid out of full disks instead of partitions this time, indicated by the lack of partition numbers in the /proc/mdstat output, so the partition tables would have been overwritten. Any attempt to recreate them would probably corrupt your raid.

mn_voyageur:
/dev/md0 normally would not have a partition table. Before now I didn't think they could be partitioned. It's possible, but you have to specify "--audo=mdp" when you create it: [https://raid.wiki.kernel.org/index.php/Partitioning_RAID_/_LVM_on_RAID](https://raid.wiki.kernel.org/index.php/Partitioning_RAID_/_LVM_on_RAID)

I often go with the LVM on md raid option to make it easier if I need to grow, shrink, or move a volume. Though on at least Lucid I always have to [edit a udev rule](http://ubuntuforums.org/showthread.php?t=1564411) to get it to detect LVM volumes on raid during bootup.

---

### Post by mn_voyageur on 2011-04-15
dtfinch,

mdadm would work without a partition table?

Edit: If mdadm requires a partition table, then it must have had one. Mdadm did work.  When I started loosing drives/partitions, that's when I could no longer mount md0

MarkN

---

### Post by rubylaser on 2011-04-15
It's perfectly fine for /dev/md0 to not have a valid partition table when viewed with fdisk.  Here's my perfectly working mdadm array for an example.

```
Disk /dev/md0: 6001.2 GB, 6001212260352 bytes
2 heads, 4 sectors/track, 1465139712 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 524288 bytes / 3145728 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table

```

Typically, after you've created the array, you would add a filesystem to the array, something like this (leaving out options to tune for stride and stride_width for this example).
```
mkfs.ext4 /dev/md0
```

You'll notice that no partition was created on the array first.  That's why fdisk reports the invalid partition table error...There is no partition :)

---

### Post by fermulator on 2011-04-15
> **dtfinch said:**
> fermulator:
You made a raid out of full disks instead of partitions this time, indicated by the lack of partition numbers in the /proc/mdstat output, so the partition tables would have been overwritten. Any attempt to recreate them would probably corrupt your raid.

Sorry, no.  I *did not* create the RAID against devices rather than partitions.  Look at [http://ubuntuforums.org/showthread.php?t=1719427](http://ubuntuforums.org/showthread.php?t=1719427).  In every instances there, it was clearly made with working partitions...

```
fermulator@fermmy-server:~$ cat /proc/mdstat 
Personalities : [linear] [multipath] [raid1] [raid0] [raid6] [raid5] [raid4] [raid10] 
md2000 : active raid6 sdo1[3] sdn1[2] sdm1[1] sdl1[0]
      3907026944 blocks level 6, 64k chunk, algorithm 2 [4/4] [UUUU]
```

Yet, now, after a failed disk, and a reboot, it seems to have auto-assembled itself on top of the devices rather than the partitions. :-(

```
fermulator@fermmy-server:~$ cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md2000 : active raid6 sdk[3] sdl[0] sdj[1]
      3907026944 blocks level 6, 64k chunk, algorithm 2 [4/3] [UU_U]

```

 ... and ... subsequently corrupted the partition table?  Can I recover this situation somehow?

---

### Post by dtfinch on 2011-04-15
The UUID is different from your previous thread, and the creation time is a day later.

There is the possibility that the partitions happened to stretch until the very end disk, rather than leaving a few blocks free at the end ([related bug here](https://bugs.launchpad.net/ubuntu/+source/partman-base/+bug/569900)). So the superblocks happen to be at the very end of the disk, causing mdadm to think they belong to the full disks rather than the partitions. That would also explain why they're the same size as reported with the partitions, rather than slightly bigger.

I don't know why mdadm would zero the beginnings of the disks though, rather than leaving them untouched as they're outside the used area.

---

### Post by fermulator on 2011-04-16
So basically I'm fubar'd and have to re-create the array?

---

### Post by fermulator on 2011-04-19
This is ridiculous.  I have performed a full re-creation of my array, and after a reboot, it has eaten the disks again.

```
fermulator@fermmy-server:/media/arrays/md2000$ cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md2000 : active raid6 sdg1[4] sdk[2] sdj[1] sdl[3] sdi[0]
      5860540416 blocks level 6, 64k chunk, algorithm 2 [5/5] [UUUUU]

```

```
fermulator@fermmy-server:/mnt$ sudo fdisk -l /dev/sd[ghijkl] | grep raid
[sudo] password for fermulator: 
Disk /dev/sdi doesn't contain a valid partition table
Disk /dev/sdj doesn't contain a valid partition table
Disk /dev/sdk doesn't contain a valid partition table
Disk /dev/sdl doesn't contain a valid partition table
/dev/sdg1               1      765634  1953513560   fd  Linux raid autodetect
/dev/sdh1               1      765634  1953513560   fd  Linux raid autodetect

```

CONTEXT:
 * /dev/sd[ijkl] were the original creation.
 * /dev/sdg1 was newly added to the array (grow operation)
 * /dev/sdl1 is newly prepped for another addition (grow operation), but I stopped because I just noticed that the partitions are fubar'd again on the original four.

I'm terrified for the safety of my data.  Does anyone have any good ideas for troubleshooting?

---

### Post by dtfinch on 2011-04-19
It looks like you made the same mistake again, using partitions that extend to the last sector of the disk (size according to fdisk is the same as before). Mdadm can't tell whether the superblock belongs to the partition or the full disk.

Any one of the following should prevent this in the future:
1) Using slightly smaller partitions. Verify that the "end" sector according to fdisk is less than the total sectors by at least 256.
2) Using a newer mdadm metadata version when creating the raid. The default 0.90 places the superblock at the end of the device. 1.1 and 1.2 place theirs at the beginning, which should make this issue impossible, but in doing so confuse grub (not an issue unless it's your boot partition), which I assume is why 0.90 was left as the default.
3) You could also edit mdadm.conf to change "DEVICE partitions" to "DEVICE /dev/sd??" ([as suggested here](https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/599515))

---

### Post by fermulator on 2011-04-28
Thanks dtfinch.

I went with option 2) version 1.1 metadata.  Since I was creating partitions 2048 blocks into the drive (DOS compatibility disabled [c] and in sector mode [u]), and I'm not booting off this array, storing the meta data at the start of the drive made a lot of sense.

Here's what I've got now for reference.

```
fermulator@fermmy-server:~$ cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md2000 : active raid6 sdh1[5] sdl1[3] sdk1[2] sdg1[4] sdj1[1] sdi1[0]
      7814053632 blocks super 1.1 level 6, 64k chunk, algorithm 2 [6/6] [UUUUUU]

```

```
fermulator@fermmy-server:~$ sudo mdadm -Q --detail /dev/md2000
/dev/md2000:
        Version : 01.01
  Creation Time : Fri Apr 22 01:12:07 2011
     Raid Level : raid6
     Array Size : 7814053632 (7452.06 GiB 8001.59 GB)
  Used Dev Size : 3907026816 (3726.03 GiB 4000.80 GB)
   Raid Devices : 6
  Total Devices : 6
Preferred Minor : 2000
    Persistence : Superblock is persistent

    Update Time : Wed Apr 27 22:54:41 2011
          State : clean
 Active Devices : 6
Working Devices : 6
 Failed Devices : 0
  Spare Devices : 0

     Chunk Size : 64K

           Name : fermmy-server:2000  (local to host fermmy-server)
           UUID : 15d2158f:5cf74d95:fd7f5607:0e447573
         Events : 11842

    Number   Major   Minor   RaidDevice State
       0       8      129        0      active sync   /dev/sdi1
       1       8      145        1      active sync   /dev/sdj1
       2       8      161        2      active sync   /dev/sdk1
       3       8      177        3      active sync   /dev/sdl1
       5       8      113        4      active sync   /dev/sdh1
       4       8       97        5      active sync   /dev/sdg1

```

```
fermulator@fermmy-server:~$ sudo fdisk -ul /dev/sd[ghijkl] | grep -E Start\|/dev/sd
Disk /dev/sdg: 2000.4 GB, 2000398934016 bytes
   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1            2048  3907029167  1953513560   fd  Linux raid autodetect
Disk /dev/sdh: 2000.4 GB, 2000398934016 bytes
   Device Boot      Start         End      Blocks   Id  System
/dev/sdh1            2048  3907029167  1953513560   fd  Linux raid autodetect
Disk /dev/sdi: 2000.4 GB, 2000398934016 bytes
   Device Boot      Start         End      Blocks   Id  System
/dev/sdi1            2048  3907029167  1953513560   fd  Linux raid autodetect
Disk /dev/sdj: 2000.4 GB, 2000398934016 bytes
   Device Boot      Start         End      Blocks   Id  System
/dev/sdj1            2048  3907029167  1953513560   fd  Linux raid autodetect
Disk /dev/sdk: 2000.4 GB, 2000398934016 bytes
   Device Boot      Start         End      Blocks   Id  System
/dev/sdk1            2048  3907029167  1953513560   fd  Linux raid autodetect
Disk /dev/sdl: 2000.4 GB, 2000398934016 bytes
   Device Boot      Start         End      Blocks   Id  System
/dev/sdl1            2048  3907029167  1953513560   fd  Linux raid autodetect

```

---

### Post by AllGamer on 2011-04-28
i'm facing a similar problem here
[http://ubuntuforums.org/showthread.php?p=10734927](http://ubuntuforums.org/showthread.php?p=10734927)

mdadm RAID5 was running fine, until i reinstalled the OS

the OS sits on its own separate drive, not part of the mdadm RAID5

according to what you guys have commented above, i too had no partitions set on the individual devices, nor partition on the md0 device.

the RAID was a straight assembly of 4 disk using the full length of the drive, then /dev/md0 was formatted with EXT3

anyways, i'm having a hard time trying to make the /dev/md0 to mount

it keeps complaining about Error mounting: mount: wrong fs type, bad option, bad superblock on /dev/md0

and i don't know what to do without causing more damage

---

### Post by lister171254 on 2011-06-21
Similar problem after growing the array.

Everything works, but fdisk reports that /dev/md0 does not have a partition table.

Is this a problem, is there a fix, or should I ignore this.

Thanks

---

### Post by vcrpcant on 2011-07-30
Same here,
sudo fdisk -l says: Disk /dev/md0 doesn't contain a valid partition table (md2 too)

is it safe to ignore it ou what?

---

### Post by krisb82 on 2012-03-27
**HELP!!**

I'm bumping this thread in hopes to get some advice on the same problem. I'm a noob to Linux and setup a RAID5 volume last week using mdadm and Webmin. Everything was working fine and I added an EXT4 partition to /dev/md0 and was able to save data to it after mounting at /mnt/<mount>. I tested it for a while and even was able to reboot and get the volume to come back up after booting a few times.

I felt I was fine to go ahead and put this volume into production as a Samba share for my company's design team (the volume is *not* a boot volume; my OS is installed on a separate HD). However, after a system-suggested reboot this morning I got an error that /dev/md0 could not be mounted on /mnt/<mount>. I skipped it and then ran fdisk -l to find that all member disks properly showing their "Linux raid autodetect" partitions; however, /dev/md0 lists the error: "Disk /dev/md0 doesn't contain a valid partition table."

Am I out of luck here? I just had the design manager come ask me for an update and I don't know what to tell him. I'm worried that in trouble on this one. Any way of recovering my data? I was just about to setup the backup system today...of course, a day too late!

---

### Post by krisb82 on 2012-03-27
Follow up to previous post:
After reading through others' posts I did check to make sure that my UUID matched on my mdadm config file and on my entry in FSTAB. I noticed that I had added a uid and gid of the main share user account to the options of FSTAB:
```

UUID=<UUID>   /mnt/design   ext4   defaults,uid=1001,gid=1001   0  0

```
Upon viewing log files after trying to mount the share found that the uid/gid entry may have been the culprit.

After editing the FSTAB entry to:
```

UUID=<UUID>    /mnt/design    ext4    defaults    0 0

```
and running "sudo mount -a" I had success!!

I'm still stumped, however, as to why the uid/gid would get in the way. Any thought?

---

### Post by rubylaser on 2012-03-27
There's really no need for uid or gid in your situation as those are not ext4 filesystem options.  As an aside, I always mount mdadm arrays by their device name.  Because they are already defined by UUID in /etc/mdadm/mdadm.conf they can't get mounted incorrectly.  I would modify your /etc/fstab to look like this.

```
/dev/md0 /mnt/design    ext4    defaults    0 0
```

Glad you got it working.

---

