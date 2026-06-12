---
title: "mdadm issue with Raid1 and spare"
date: 2011-11-11
forum: Server Platforms
---

### Post by vaguy02 on 2011-11-11
I have a server with an OS drive (10.04LTS) and 2TB RAID1 (2 drives). The OS drive recently crashed (hardware failure), the drive was replace and the OS reinstalled from scratch. I attempted to do a mdadm --assemble on the raid. 1 Drive went immediately into active sync status, but it shows the other drive as removed. Then it shows the second drive in a spare status. 

I attempted to stop md0, do a --assemble --force on both drives again, still no luck. 1 drive in active sync, one "removed", and one in spare status. These 2 were the same original drives. 

I'm pulling my hair out trying to get the one drive into active status and the array out of degraded. Any help?

*PS. The kicker is, I can't loose the data on the drives. No backsup, can you believe that?*

> 
/dev/md0:
        Version : 00.90
  Creation Time : Sat May 14 20:03:36 2011
     Raid Level : raid1
     Array Size : 1953511936 (1863.01 GiB 2000.40 GB)
  Used Dev Size : 1953511936 (1863.01 GiB 2000.40 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Fri Nov 11 15:44:18 2011
          State : clean, degraded
 Active Devices : 1
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 1

           UUID : d8e1d827:944982b6:409a2900:8a49c38d (local to host library)
         Events : 0.58462

    Number   Major   Minor   RaidDevice State
       0       8       33        0      active sync   /dev/sdc1
       1       0        0        1      removed

       2       8       49        -      spare   /dev/sdd1



---

### Post by cconstantine on 2011-11-11
what does 'cat /proc/mdstat' show?

---

### Post by vaguy02 on 2011-11-11
As requested.

> Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid1 sdc1[0] sdd1[2](S)
      1953511936 blocks [2/1] [U_]


---

### Post by darkod on 2011-11-11
I'm no expert in raid, but have you tried adding the disk to the array similar to what this link says:
[http://www.howtoforge.com/replacing_hard_disks_in_a_raid1_array](http://www.howtoforge.com/replacing_hard_disks_in_a_raid1_array)

Up to point 3 it removes the failed hdd, which you have already done it seems. Step 4 continues with adding the new disk. Note that your case is slightly different because you have the new disk marked as spare right now, while in this tutorial there is no such thing.
But I still think it's the same principle.

---

### Post by vaguy02 on 2011-11-12
Thanks for your reply. Yes, I have tried that. It says drive re-added, but it goes right back into the spare state.

---

### Post by darkod on 2011-11-12
Are the disks identical? By identical I don't mean whether they are both 2TB. Did you make the new disk with the same layout?
The link I posted with that tutorial had a really nice sfdisk command to create the same layout on the new disk.

Even though softraid1 should work with identical partitions, if you are using proper mirror I guess it's better to mirror the disk layout too.

I'm running out of ideas otherwise.

I found one link with similar problem, and it says they just recreated the array without losing the data, but I wouldn't recommend that. The tutorials say once you have your array created you never need to recreate it. It worked for someone else but it might not work for you and delete all your data, creating a new empty array.

---

### Post by vaguy02 on 2011-11-12
The two 2TB drives are the original drives before the crash, only the OS drive failed. Partition and Data on both drives are identical from when the RAID was operational. 

I found the same article before posting here... I was hoping there was something I was missing. It seems like it should be easy to change the status of the drive, but it doesn't seem like that's an option anywhere. 

I guess I will need to "Beg, Borrow, or Steal" another 2TB and copy all data off the two drives and recreate the array.

---

### Post by darkod on 2011-11-12
O, yeah, I forgot, it was the OS disk. Reading too many threads here. :)

Is it possible that the letters of the disks have changed with plugging in the new OS disk? Did you double check that? They are sdc and sdd as before? And the OS disk is what, sda?

---

### Post by vaguy02 on 2011-11-12
Actually, I don't honestly remember what the drive letters were before the crash. It didn't require alot of maintenance. I know it's currently assigned the following.

> Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1d339316

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      121601   976760001   fd  Linux raid autodetect

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1d339316

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121601   976760001   fd  Linux raid autodetect

Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xeb1b8512

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      243201  1953512001   fd  Linux raid autodetect

Disk /dev/sde: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00022d55

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1       38531   309494784   83  Linux
/dev/sde2           38531       38905     3002369    5  Extended
/dev/sde5           38531       38905     3002368   82  Linux swap / Solaris

Disk /dev/sdd: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xeb1b8511

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1      243201  1953512001   fd  Linux raid autodetect

Disk /dev/md0: 2000.4 GB, 2000396222464 bytes
2 heads, 4 sectors/track, 488377984 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table


---

### Post by darkod on 2011-11-12
Sorry, this is beyond my knowledge of softraid.

That last line is getting me worried, I don't know if it's normal fdisk not to recognize the partition table of /dev/md0.

---

### Post by vaguy02 on 2011-11-12
You know.... I was worried about the same thing. But I was able to mount the drive with "sudo mount -t ntfs /dev/md0 /media/a" without any issues and access the data. I'm really not sure why it says there is no partition table.

---

### Post by darkod on 2011-11-12
One thing you could do without begging around for a new 2TB disk. But note that I don't have any real experience with mdadm and this might be like playing with your data. :)

1. Remove /dev/sdd1 from your array (it's marked as spare anyway). The command was in that link about replacing a disk. Your array should still work fine as degraded with /dev/sdc1.
2. Format sdd. Copy all data from array to sdd. Unplug sdd from the computer.
3. Kill your array. Not just stopping it, destroy it.

Now comes the interesting part which I am not sure will work:

4. Create a new array of two devices but have only sdc in it. Let it run degraded from start.
5. Copy the data back.
6. Plug sdd as second disk and let it sync.

Hope it goes well for you, what ever you do. :)

---

### Post by darkod on 2011-11-12
A small explanation about my idea above. :)
I was thinking about my network disk, a WD My World Edition. My model has only one HDD of 1TB. But they also sell a model with two HDDs in RAID1, again 1TB storage.

I guess to save money, my guess is they decided to develop only one firmware for both models. So even though I have a single HDD, when I SSH into it and run /proc/mdstat it shows a RAID1 array with one disk missing.

That's how it came from factory. It always run as degraded, which is logical since it's only one HDD. But I have no idea why they developed it that way.

You only need to run your new array degraded for a little while until you copy the data back and join the second disk.

---

### Post by MysteryMetal on 2012-06-04
I also encountered the issue of adding a drive to a RAID 1 array with mdadm where the new drive always became a spare.  I found that the active drive in the array was generating "Unrecovered read error - auto reallocate failed" while mdadm executed the sync on the newly added drive.  The sync process terminated immediately upon hitting the read error on the active drive and put the newly added drive into spare status.  There was no indication that the sync had stopped or failed based on messages that mdadm sent to stdout, stderr or any logs under /var/log.  I did see the disk read error in dmesg and /var/log/syslog.

I tried several methods suggested on various message boards to get the newly added drive to sync into the array, with no success.  I was able to solve the issue, though it took 9 hours of downtime since my root file system was in the affected array.

Solution
=========

Note that this solution carries a HIGH RISK of data loss.  Be sure your data is backed up and that you understand each command you execute.  The steps below were executed on a host running Ubuntu Server 10.04.3 LTS

* Ran a full system backup.  I used the processes that are already in place on my systems to do regularly scheduled backups

* Noted that the "active" drive was mapped to /dev/sdc and that the "spare" drive was mapped to /dev/sdb

* Failed all devices that physically resided on the "spare" drive
   mdadm --manage /dev/md0 --fail /dev/sdb1
   mdadm --manage /dev/md1 --fail /dev/sdb2
   mdadm --manage /dev/md2 --fail /dev/sdb3

* Removed all devices that physically resided on the "spare" drive
   mdadm --manage /dev/md0 --remove /dev/sdb1
   mdadm --manage /dev/md1 --remove /dev/sdb2
   mdadm --manage /dev/md2 --remove /dev/sdb3

* Cleared start of each partition on the "spare" drive
   dd if=/dev/zero of=/dev/sdb1 bs=10240000 count=1
   dd if=/dev/zero of=/dev/sdb2 bs=10240000 count=1
   dd if=/dev/zero of=/dev/sdb3 bs=10240000 count=1

* Cleared partition table on the "spare" drive
   dd if=/dev/zero of=/dev/sdb bs=10240000 count=1

* Shutdown host
   shutdown -h now

* Booted host from CD.  I used Ubuntu Rescue Remix, but there are other options available

* Verified the identity of the "active" and "spare" drives and which devices they were mapped to using fdisk.  The mappings had not changed from their pre-shutdown values, but I could not assume that they had not.
   fdisk -l

* Copied entire "active" drive onto the "spare" drive using dd.  This took over 8 hours for a 500 Gb drive.  Time will vary depending on size of disk and i/o throughput on the drive and host.  No data read errors were generated during the copy process in my case.  Had there been an error, I would have restarted dd with appropriate offsets after the position where the error occurred.  No guarantee it would have worked, but I have had success in the past.
   dd if=/dev/sdc of=dev/sdb >/tmp/dd.out 2>&1 &

* Checked stdout, stderr (redirected to file earlier) and logs for errors

* Shutdown host
   shutdown -h now

* Physically removed drive that was previously "active"

* Booted host using the drive that was previously "spare".  It came up without any issues.  If the host had failed to come up properly, I would have reverted back to the drive that was previously "active"

* Shutdown host
   shutdown -h now

* Installed new, empty drive (to replace the previously "active" drive)

* Booted host again using the drive that was previously "spare"

* Created partitions on the new drive
   sfdisk -d /dev/sdb | sfdisk --force /dev/sdc

* Added devices to the RAID 1 arrays.  All devices successfully synchronized and became active
   mdadm --manage /dev/md0 --add /dev/sdc1
   mdadm --manage /dev/md1 --add /dev/sdc2
   mdadm --manage /dev/md2 --add /dev/sdc3


All Done.  Not sure why dd or the full backup at the beginning didn't generate read errors while mdadm did.  A long SMART test also encountered read errors.  As far as I can tell, all data was copied successfully.

---

