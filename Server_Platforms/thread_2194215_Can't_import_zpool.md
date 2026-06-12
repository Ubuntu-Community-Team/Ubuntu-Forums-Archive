---
title: "Can't import zpool"
date: 2013-12-17
forum: Server Platforms
---

### Post by povlhp on 2013-12-17
The story short. Installed ubuntu on HP Microserver N54L 250GB disk. Created 2 zpools on the  4x3TB disk. 2.5GB of each with raidz5 (parity), and the last 500GB on each for raidz0 striping. Worked fine. Shutdown. Install ESXi, install ubuntu in VM, used Virtual RDMs to map my 4x3TB drives.

zpool import works fine on the first zfs partition on the drives, the one with raid 5. Had to use -f since I forgot to export the fs first.

But I can't import the raid0 zpool. It contains only non-critical data (freshly installed virtual machines, transmission-cache etc), but I would like to recover it if I can, and learn in the process.

Any pointers to what I can do ?

Here is the result:

root@ubuntu:~# zpool import
   pool: fastzfs
     id: 965923234905660723
  state: UNAVAIL
 status: One or more devices contains corrupted data.
 action: The pool cannot be imported due to damaged devices or data.
   see: [http://zfsonlinux.org/msg/ZFS-8000-5E](http://zfsonlinux.org/msg/ZFS-8000-5E)
 config:


        fastzfs                                           UNAVAIL  insufficient replicas
          scsi-1ATA_WDC_WD30EFRX-68EUZN0_WD-WMC4N0237360  UNAVAIL
          scsi-1ATA_WDC_WD30EFRX-68EUZN0_WD-WMC4N0489568  UNAVAIL
          scsi-1ATA_WDC_WD30EFRX-68EUZN0_WD-WMC4N0329878  UNAVAIL
          scsi-1ATA_WDC_WD30EFRX-68EUZN0_WD-WMC4N0231724  UNAVAIL


The disks exists (of course, I could import the zpool spanning the first partition on each)

root@ubuntu:~# ls /dev/disk/by-id/
ata-VMware_Virtual_IDE_CDROM_Drive_10000000000000000001
dm-name-ubuntu--vg-root
dm-name-ubuntu--vg-swap_1
dm-uuid-LVM-CX4l82lOiwxFJrBIk64G1oEQclvNrfdAcNaOeMdojaoWaZmNcfjlgFNa21RBBpmy
dm-uuid-LVM-CX4l82lOiwxFJrBIk64G1oEQclvNrfdALl4QoAdKAo6ZzllCOJ7OhXfclCnVDjYk
scsi-1ATA_WDC_WD30EFRX-68EUZN0_WD-WMC4N0231724
scsi-1ATA_WDC_WD30EFRX-68EUZN0_WD-WMC4N0231724-part1
scsi-1ATA_WDC_WD30EFRX-68EUZN0_WD-WMC4N0231724-part2
scsi-1ATA_WDC_WD30EFRX-68EUZN0_WD-WMC4N0237360
scsi-1ATA_WDC_WD30EFRX-68EUZN0_WD-WMC4N0237360-part1
scsi-1ATA_WDC_WD30EFRX-68EUZN0_WD-WMC4N0237360-part2
scsi-1ATA_WDC_WD30EFRX-68EUZN0_WD-WMC4N0329878
scsi-1ATA_WDC_WD30EFRX-68EUZN0_WD-WMC4N0329878-part1
scsi-1ATA_WDC_WD30EFRX-68EUZN0_WD-WMC4N0329878-part2
scsi-1ATA_WDC_WD30EFRX-68EUZN0_WD-WMC4N0489568
scsi-1ATA_WDC_WD30EFRX-68EUZN0_WD-WMC4N0489568-part1
scsi-1ATA_WDC_WD30EFRX-68EUZN0_WD-WMC4N0489568-part2


#parted -l
...
Model: ATA WDC WD30EFRX-68E (scsi)
Disk /dev/sdb: 3001GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt


Number  Start   End     Size    File system  Name     Flags
 1      1049kB  2500GB  2500GB  zfs          primary  msftdata
 2      2500GB  3001GB  501GB   zfs          primary  msftdata
...
Model: ATA WDC WD30EFRX-68E (scsi)
Disk /dev/sdc: 3001GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt


Number  Start   End     Size    File system  Name     Flags
 1      1049kB  2500GB  2500GB  zfs          primary  msftdata
 2      2500GB  3001GB  501GB   zfs          primary  msftdata



The command:
zpool import -f -F -n fastzfs

returns with no output/dev/disk/by-id/ata-WDC_WD30EFRX-68EUZN0_WD-WMC4N0231724-part2


Running "cat /dev/disk/by-id/scsi-1ATA_WDC_WD30EFRX-68EUZN0_WD-WMC4N0231724-part2|strings|less"
shows that the original name for the devices where on the (S)ATA bus

/dev/disk/by-id/ata-WDC_WD30EFRX-68EUZN0_WD-WMC4N0231724-part2

---

### Post by povlhp on 2013-12-17
Can't nobody help ? I am not sure what the problem is. 
Can I create a new raidz pool adding the existing partitions and have it work that way ?
Or is the problem it is the 2nd partition ? Or the diskname is too long / the -part2 has been cut ?
I don't really have the time to go down this track and look in the source - But I would call it likely. The "partitions" are UNAVAIL, or in use if I try to force it. Which could indicate, that the import is trying to import the raw disk, or the already imported partition 1, and not the part2.

Should be "test-able" creating a file with dd, and try some fdisk magic.

Will give it until tomorrow I think, and then just wipe the partitions and recreate the pool.

---

### Post by tgalati4 on 2013-12-17
You have a lot going on here.  Because you added EXSi and then added Ubuntu server as a virtual machine, you have confounded the problem.  Try putting Ubuntu server on bare metal and see if you can see both zpools.  If so, then you might ask for support on the EXSi forums and see if anyone else has experienced the same behavior.  My instinct tells me that there may be a limitation (intentional or not) of one zpool per set of physical disks for vm's because of how the virtual storage pools are abstracted.

A Haiku:

Two zpools are built.
EXSi added, but . . .
Can't see them, what's up?

---

### Post by povlhp on 2013-12-17
I am pretty sure that it is not a VMWare issue. I am using RDM (fully virtual raw disks, not VDMK files), which is supposed to work fine. Since I had it working on raw hardware before, multiple zpools per physical disk should be OK.  More or less like using files instead of partitions. Can you recommend any bootable liveUSB with zfs support ? FreeNAS under VMWare did not even recognise the first stripe.

---

### Post by povlhp on 2013-12-17
Decided to try and create a new pool with the same partitions. It ended up empty. But now I have my new pool and the diskspace is back.
zpool import still shows the remains of my old fastzfs spool. Can't get rid of that, but I don't see it as a problem.

---

### Post by tgalati4 on 2013-12-17
There are different versions of zfs.  It's possible that the freenas you used had an older version of zfs and thus could not read your zpools.  When you had it working on raw hardware, what operating system were you using?

---

### Post by povlhp on 2013-12-18
I am pretty sure it was zfs version 28 in all instances (zfs on linux), which FreeNAS supposedly supports.
But, FreeNAS might have had trouble with the GPT partitioning or something else. I am now back to a fresh install with Ubuntu as host, and then VMWare Player in nogui mode after install to run my VMs.

What are the opinions here on how to best utilize 4 disks ? Some places says that number of disks in a ZFS pool should be 2^x +1. That is, 3 disks seems to be recommended over 4 disks for a raidz / Raid5 ?

I am able to move data off and reformat everything. Also thinking about doing that, to make my stripe the first and fastest partition. And possible move the logs from the raidz there (parity is to prevent data rot of photos, movies and other non-recoverable data - If the stripe crashes during write, fine, I will just write the data again).

---

### Post by povlhp on 2013-12-18
Now I am back with native ubuntu 12.04 LTS. My first pool on the drives imports fine, the 2nd pool (the stripe) fails again. This time with different errors, but still like truncated names for the drives. Guess the problem is the 2 pools per drive. Recreating it gives -part2 as part of the name as intended, but I get a warning when creating that it is part of an exported pool. So it knows about it. Maybe it is the 3GB disks that are the issue here, and the partition starting at 2.5 GB ? Or maybe it is that the disk/by-id changes from ata -> scsi on the 2nd zpool in the devicenames, and it will not look that far. I see a risk here, in moving the disks to another platform where they will be seen as SCSI instead of at a names. Maybe some ln -s in /dev could have worked.

[FONT=Menlo]# zpool import[/FONT]
[FONT=Menlo]   pool: massive[/FONT]
[FONT=Menlo]     id: 14748827223284037050[/FONT]
[FONT=Menlo]  state: ONLINE[/FONT]
[FONT=Menlo] action: The pool can be imported using its name or numeric identifier.[/FONT]
[FONT=Menlo] config:[/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]	massive                                             ONLINE[/FONT]
[FONT=Menlo]	  raidz1-0                                          ONLINE[/FONT]
[FONT=Menlo]	    ata-WDC_WD30EFRX-68EUZN0_WD-WMC4N0237360-part1  ONLINE[/FONT]
[FONT=Menlo]	    ata-WDC_WD30EFRX-68EUZN0_WD-WMC4N0489568-part1  ONLINE[/FONT]
[FONT=Menlo]	    ata-WDC_WD30EFRX-68EUZN0_WD-WMC4N0329878-part1  ONLINE[/FONT]
[FONT=Menlo]	    ata-WDC_WD30EFRX-68EUZN0_WD-WMC4N0231724-part1  ONLINE[/FONT]


[FONT=Menlo]   pool: zfsraid[/FONT]
[FONT=Menlo]     id: 6726670054161551716[/FONT]
[FONT=Menlo]  state: FAULTED[/FONT]
[FONT=Menlo] status: One or more devices contains corrupted data.[/FONT]
[FONT=Menlo] action: The pool cannot be imported due to damaged devices or data.[/FONT]
[FONT=Menlo]   see: [http://zfsonlinux.org/msg/ZFS-8000-5E](http://zfsonlinux.org/msg/ZFS-8000-5E)[/FONT]
[FONT=Menlo] config:[/FONT]
[FONT=Menlo]
[/FONT]
[FONT=Menlo]	zfsraid                                     FAULTED  corrupted data[/FONT]
[FONT=Menlo]	  ata-WDC_WD30EFRX-68EUZN0_WD-WMC4N0237360  UNAVAIL  corrupted data[/FONT]
[FONT=Menlo]	  ata-WDC_WD30EFRX-68EUZN0_WD-WMC4N0489568  UNAVAIL  corrupted data[/FONT]
[FONT=Menlo]	  ata-WDC_WD30EFRX-68EUZN0_WD-WMC4N0329878  UNAVAIL  corrupted data[/FONT]
[FONT=Menlo]	  ata-WDC_WD30EFRX-68EUZN0_WD-WMC4N0231724  UNAVAIL  corrupted data[/FONT]

---

### Post by tgalati4 on 2013-12-18
I would never mix RAID modes on the same disk.  What is the Use Case for this server?  How is it going to be used?  That will determine how you set up the disks.  RAID is not a backup solution--it is a data availability solution.  I would use JBOD and simple zfs on all 4 disks with manual rsync mirroring as needed to the other disks.  

Why do you need RAID0?  Is it for speed?  What does RAID5 give you over simple zfs file system with manual rsync to a backup drive for data that doesn't change very often?  Why is it a good idea to have RAID0 and RAID5 on the same physical disks?  How do the write heads and controllers deal with the workload?  Just because you can, does not mean it is a good idea.  And unlike Wikipedia, some ideas are better on paper than in practice.

If you absolutely have to have RAID (because you have infinite patience) then I would set up a simple zfs RAID1 of 6 TB each 2 x 2 drives.  Do you need parity when you have zfs?

[http://www.zfsbuild.com/2010/05/26/zfs-raid-levels/](http://www.zfsbuild.com/2010/05/26/zfs-raid-levels/)

You could set up RAID10, but this is overkill for a home server.

---

