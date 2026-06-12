---
title: "Adding a disk to and growing MD Raid 5 with LVM"
date: 2008-03-03
forum: Tutorials
---

### Post by jmandawg on 2008-03-03
I couldn't find a gude for doing this with LVM.  This was done on GUTSY, and appears to be working fine for me.   Do it at your own risk.  If you know of a better way to do something please let me know.

So i have an existing software Raid 5 with LVM and i have an extra disk laying around, that i want to add into the Raid array to have more Raid disk space.  

Here are the steps.  If i miss anything let me know, most of this is from memory:
I logged in as root, if you don't, you have to sudo everything or sudo -s.

1. install your disk into the system.
2. Get the name of the disk you want to add:

> 
[root@e6400:/home/moon/ 519]$lshw -C disk
  *-disk:0
       description: SCSI Disk
       product: ST3320620AS
       vendor: ATA
       physical id: 0
       bus info: scsi@0:0.0.0
       logical name: /dev/sda
       version: 3.AA
       serial: 3QF0AL47
       size: 298GB
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5
  *-disk:1
       description: SCSI Disk
       product: ST3320620AS
       vendor: ATA
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/sdb
       version: 3.AA
       serial: 5QF0PEWW
       size: 298GB
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5
  *-disk:2
       description: SCSI Disk
       product: ST3320620AS
       vendor: ATA
       physical id: 2
       bus info: scsi@4:0.0.0
       logical name: /dev/sdc
       version: 3.AA
       serial: 5QF0DMH5
       size: 298GB
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5
  *-disk:3
       description: SCSI Disk
       product: ST3320620AS
       vendor: ATA
       physical id: 3
       bus info: scsi@5:0.0.0
       logical name: /dev/sdd
       version: 3.AA
       serial: 5QF0S6XE
       size: 298GB
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5


So the disk i want to add in is /dev/sdd

2.  Partion this disk based on an existing disk in the array assuming /dev/sdb is already in the array:

Copy the partition from the existing drive in the raid.
> 

sfdisk -d /dev/sdb > partitions.sdb



edit the partitions.sdb file and change all the references to sdb to sdd

Now we partition the new drive
> 

sfdisk /dev/sdd < partitions.sdb



note:
I have 2 partition on my drive
/dev/sdd1 - Raid 0 on /dev/md0
/dev/sdd2 - Raid 5 on /dev/md1

3. Clean the superblock on the new drive partitions (In case it was in another Raid)  either way it won't hurt.

> 
mdadm --zero-superblock /dev/sdd1
mdadm --zero-superblock /dev/sdd2


4.  Add the new drives to the arry, i have a Raid 0 for partition /dev/sdd1 and a Raid 5 for partition /dev/sdd2
Set raid-devices to the new number of devices in your array,  i previously had 3.
> 
mdadm --add /dev/md0 /dev/sdd1
mdadm --grow /dev/md0 --raid-devices=4

mdadm --add /dev/md1 /dev/sdd2
mdadm --grow /dev/md1 --raid-devices=4


5. My Raid 0 (/dev/md0) is done, this is my /boot.

6. WAIT a long time for the Raid to rebuild itself.  To check the progress run this command:

> 
cat /proc/mdstat


7. When it is finally done you should be able to see the new size of the Raid arry:

> 
[root@e6400:/home/moon/ 503]$mdadm -D /dev/md1
/dev/md1:
        Version : 00.90.03
  Creation Time : Sat Mar  1 06:36:40 2008
     Raid Level : raid5
     Array Size : 937488768 (894.06 GiB 959.99 GB)
  Used Dev Size : 312496256 (298.02 GiB 320.00 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 1
    Persistence : Superblock is persistent

    Update Time : Mon Mar  3 09:39:06 2008
          State : active
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : 6edd19d2:6bc3e59d:ce21a63d:f12f7b33
         Events : 0.208309

    Number   Major   Minor   RaidDevice State
       0       8        2        0      active sync   /dev/sda2
       1       8       18        1      active sync   /dev/sdb2
       2       8       34        2      active sync   /dev/sdc2
       3       8       50        3      active sync   /dev/sdd2



8. Now we have to make changes to our LVM.  

Resize our physical volume
> 
[root@e6400:~/ 499]$pvresize /dev/md1
  Physical volume "/dev/md1" changed
  1 physical volume(s) resized / 0 physical volume(s) not resized
[root@e6400:~/ 500]$pvdisplay
  --- Physical volume ---
  PV Name               /dev/md1
  VG Name               VG_E6400
  PV Size               894.06 GB / not usable 192.00 KB
  Allocatable           yes
  PE Size (KByte)       4096
  Total PE              228879
  Free PE               76293
  Allocated PE          152586
  PV UUID               dw0IGv-j1WA-hd63-mY3K-i6mJ-4yX6-MQftH8


9. Resize our logical volume:
> 
[root@e6400:/home/moon/ 503]$lvresize -l 95%VG /dev/VG_E6400/LV_E6400


For some reason it would not let me use 100%, so i had to add the rest of the free disk (38.7GB) space using the resize command again:

> 
[root@e6400:/home/moon/ 503]$lvresize -L +38.7G /dev/VG_E6400/LV_E6400


10. Check that your LV was resized correctly:
> 
[root@e6400:/home/moon/ 503]$lvdisplay
  --- Logical volume ---
  LV Name                /dev/VG_E6400/LV_E6400
  VG Name                VG_E6400
  LV UUID                JIdQXg-C6Rv-WLq9-I61F-Foss-N8jE-wG13IQ
  LV Write Access        read/write
  LV Status              available
  # open                 1
  LV Size                888.06 GB
  Current LE             227343
  Segments               1
  Allocation             inherit
  Read ahead sectors     0
  Block device           254:1



11. If everything looks good, resize your file system (i use ext 3 you may have to run a different cmd if you run a differnt FS).  My volume was mouted as the root filesystem, so it did an online resize.  This is probably dangerous.

> 
[root@e6400:/home/moon/ 503]$resize2fs /dev/VG_E6400/LV_E6400


12. CHeck your disk space:
> 
[root@e6400:/home/moon/ 503]$df -h /
Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/VG_E6400-LV_E6400
                      875G  267G  564G  33% /



---

### Post by networkspeedy on 2009-12-22
This was excellent.

Many thank-you's, jmandawg

---

### Post by samjbobb on 2010-04-05
Thanks. Helped a bunch.

---

### Post by txtiger on 2012-01-29
I used this process on Ubuntu 10.10 and found I needed to go to a live CD to be able to do it right.  This was because I had symlinks from the home directory to the Raid drive and it would automount even when I thought it was unmounted.  Anyway, the LiveCD approach is probably safer anyway.

I captured the history of commands and then cleaned out the non-productive ones and commented them.

Here is what I did:

// First add the new drive to the array as a spare
// [These commands done without a literal history]
// use fdisk /dev/sdxx and create a partition with an Auto Raid type.  This is an fd type identifier
// I used disk utility gui to add it as a spare.
// Then rebooted to a live CD

NOTE: Do this from a Live CD!

// first get the data for the raid
mdadm -D /dev/md0

// now put it together to work on it
mdadm --assemble /dev/md0

// now get the info for the Volume Group and the Logical Volume
vgdisplay
lvdisplay
lvscan

// Be sure the volume is not mounted
umount /dev/vgRaid01/

//Now grow the array.  This was for increasing from 4 drives to 5
mdadm --grow /dev/md0 -n 5

// It didn't work because it had a write-intent bitmap.  I removed it with
mdadm --grow /dev/md0 -b none
// this was a pain for me to figure out.  Thanks go to the wonderful link at [https://raid.wiki.kernel.org/articles/g/r/o/Growing.html](https://raid.wiki.kernel.org/articles/g/r/o/Growing.html)
// recommended reading.  It is important to remove the bitmap!

// Now retry the grow
mdadm --grow /dev/md0 -n5
// It worked and began resyncing.  Monitor progress with
watch -n 10 cat /proc/mdstat

// When done (many hours for the 1TB add) check it to get the new extents
mdadm -D /dev/md0

// Now grow the physical volume to fill the Raid and then check it
pvresize /dev/md0
pvdisplay /dev/md0

// Get the Volume group and Logical volume data again but Note the 
// new Volume group extents.  In this case it was 3.726 Gigabytes
vgdisplay
lvdisplay

// now extend the Logical Volume to fill the new size
lvextend -L 3726G /dev/vgRaid01/lvRaid01

// now clean the file system.  There is no progress method for e2fsck so
// start a second terminal and execute the scary command at the bottom of this list
e2fsck -f /dev/vgRaid01/lvRaid01

// once that is complete grow the file system.  The progress bar may not work in some
// cases.  But for me this went fairly quickly when growing from 3TB to 4TB.
resize2fs -p /dev/vgRaid01/lvRaid01 

// At this point you need to edit /etc/mdadm/mdadm.conf to contain the new data.  You get that new data from mdadm -D /dev/md0  Also, don't forget to edit /etc/fstab in the event there waqs a UUID change.

// Reboot and debug if needed
---------------------------------------------------------------------------------------------------------------------

// This is done in the second terminal to track the lengthy process of doing the file system check
watch -n 10 pkill -SIGUSR1 e2fsck

// I double checked this because of the "pkill" and I knew killing the resize2fs could result in a loss of all data
// it turns out the -SIGUSR1 is the critical part.  It forces a
// status output from e2fsck.  It worked fine.

---

### Post by elhund on 2013-04-19
dont forget to add the device you expanded the array with in mdadm.conf on the
DEVICE option row. I didnt and my md array did not initialize on boot and gave
me the magic superblock error.

---

