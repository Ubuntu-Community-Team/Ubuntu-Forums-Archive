---
title: "Raid1 problem on Blade 100"
date: 2007-09-24
forum: Sun Sparc Users
---

### Post by amcginty on 2007-09-24
Hi all,
Took a while to get going, but I've been able to install Ubuntu 6.06.  Been very happy with the process of building a firewall; dhcp; and everything else.

The last task was to install two existing 160G hard drives in a Raid1 configuration.
The challenge was that they contained data already.

I read thru many posts;faq's; tutorials (all of which said repeatedly to back up your data). Unfortunately, I learned very early on a bad habit of not doing this. And every time I have a hd crash, I vow to start, but like anyone that has ever battled a bad habit, I have not been successful.  Thus wanting a Raid1 configuration.

Now to the problem. I had everything nearly set up:

4 partitions on each drive with the same parameters.
The first partition was to be a boot,
2 and 3 data (app, whatever)
4 swap.

I had all my data on partiton 2 of the first disk, and was working with mdadm to pair up the other partitions.

My data is now gone (pictures, songs, apps, .... everything)

It was there one moment, and after a reboot, gone:

Here's the spec's:

fdisk -l 

Disk /dev/hdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1         609     4891761   fd  Linux raid autodetect
/dev/hdb2             610        9296    69778327+  fd  Linux raid autodetect
/dev/hdb3            9297       19199    79545847+  fd  Linux raid autodetect
/dev/hdb4           19200       19457     2072385   fd  Linux raid autodetect

Disk /dev/hdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1         609     4891761   fd  Linux raid autodetect
/dev/hdc2             610        9296    69778327+  fd  Linux raid autodetect
/dev/hdc3            9297       19199    79545847+  fd  Linux raid autodetect
/dev/hdc4           19200       19457     2072385   fd  Linux raid autodetect



I've tried reiserfsck  and get the reiserfs superblock cannot be found.

I've looked at testdisk but don't know what I'm doing.

Any advise or recommendations?

Much appreciated.

---

### Post by amcginty on 2007-09-25
More detail on what I was doing:

Initially, the two 160G drives were on NAS.
Moved all data onto one drive, and placed emptied drive into the Sun box.
FDisk'ed with 4 partitions
1, 3, 4 were Raid type
2 was ReiserFS

I did this so I could move the data from the NAS to part #2, 
then take NAS drive offline, and install into Sun box.

FDisk'ed drive #2 with 4 partitions, all Raid type.

Built a Raid1 with partition #1 from both drives.
Built a Raid1 with partition #3 from both drives.

When that happened, Partition #2 on the first drive seemed to flip the partition type, and poof, everything's gone.

---

### Post by amcginty on 2007-10-09
After much hesitation, reading, reading, reading some more,,,,, I performed the following:

I found that you can work with disk images created with dd and dd_rescue

First I created an image of the first disk, second partiton (I knew my data was here initially).
     > dd_rescue /dev/hdd2 /opt9/hdd2.dd

Then stepped through the combination of commands:
     > reiserfsck --check hdd2.dd
     > reiserfsck --rebuild-sb hdd2.dd
     > reiserfsck --rebuild-tree hdd2.dd

And finally (after about 6-8 hours):
     > mount -o loop -t reiserfs hdd2.dd /opt4


So, I've learned: backup first and backup often. Not to another partition, but to offline media (tape, cd, dvd) or another drive on another system.

Reboot often when making system changes, after each change (I compounded my problem by making many partition changes to multiple disks before rebooting)

I have decided against Raid'ing my two drives, I will use one as live and the other as data backup for my live drive and my lan. And I am working on setting up a tape backup unit.

I hope others find my painful experience useful ( or at least entertaining).

---

