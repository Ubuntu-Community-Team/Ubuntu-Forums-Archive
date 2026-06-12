---
title: "failed 10.04 install using raid1"
date: 2010-07-13
forum: Server Platforms
---

### Post by wlott on 2010-07-13
I'm trying to install 10.04 64bit server edition using raid1 for /home, and I can't get it to work.  This machine has a 640GB drive and a 500GB drive.  Using the installer, I setup three parititons on the the 640: 108GB for /, 32 GB for swap, and 500GB for raid.  I've setup a single partition on the 500GB also for raid.  And then I combined the two 500GB partitions using raid1 for /home.

The installer finishes fine, but when I boot fsck thinks that /dev/md0 has a hosed super-block and the system hangs.

Using a live CD, I commented out the line for /home in /etc/fstab.  That let me boot.  Looking at /proc/mdstat it looks like it tried to build /dev/md0 out of sda3+sdb (the whole second drive) instead of sda3+sdb1 (the only partition on the second drive).  If I stop the array and rebuild it correctly, fsck is happy with the filesystem on /dev/md0.  Here is the results of "grep md /var/log/messages":

```
Jul 13 11:22:59 gunner kernel: [    0.831433] md: linear personality registered for level -1
Jul 13 11:22:59 gunner kernel: [    0.840695] md: multipath personality registered for level -4
Jul 13 11:22:59 gunner kernel: [    0.857565] md: raid0 personality registered for level 0
Jul 13 11:22:59 gunner kernel: [    0.863252] md: raid1 personality registered for level 1
Jul 13 11:22:59 gunner kernel: [    1.767513] md: bind<sda3>
Jul 13 11:22:59 gunner kernel: [    2.486781] md: bind<sdb>
Jul 13 11:22:59 gunner kernel: [    2.488065] raid1: md0 is not clean -- starting background reconstruction
Jul 13 11:22:59 gunner kernel: [    2.488067] raid1: raid set md0 active with 2 out of 2 mirrors
Jul 13 11:22:59 gunner kernel: [    2.488094] md0: detected capacity change from 0 to 500106723328
Jul 13 11:22:59 gunner kernel: [    2.488165] md: resync of RAID array md0
Jul 13 11:22:59 gunner kernel: [    2.488168] md: minimum _guaranteed_  speed: 1000 KB/sec/disk.
Jul 13 11:22:59 gunner kernel: [    2.488170] md: using maximum available idle IO bandwidth (but not more than 200000 KB/sec) for resync.
Jul 13 11:22:59 gunner kernel: [    2.488174] md: using 128k window, over a total of 488385472 blocks.
Jul 13 11:22:59 gunner kernel: [    2.488176] md: resuming resync of md0 from checkpoint.
Jul 13 11:22:59 gunner kernel: [    2.488970]  md0: unknown partition table
Jul 13 11:22:59 gunner kernel: [    4.501760] ata7: PATA max UDMA/100 cmd 0xec00 ctl 0xe880 bmdma 0xe400 irq 16
Jul 13 11:22:59 gunner kernel: [    4.501762] ata8: PATA max UDMA/133 cmd 0xe800 ctl 0xe480 bmdma 0xe408 irq 16
Jul 13 11:22:59 gunner kernel: [    4.843585] md: raid6 personality registered for level 6
Jul 13 11:22:59 gunner kernel: [    4.843587] md: raid5 personality registered for level 5
Jul 13 11:22:59 gunner kernel: [    4.843589] md: raid4 personality registered for level 4
Jul 13 11:22:59 gunner kernel: [    4.848419] md: raid10 personality registered for level 10
Jul 13 11:25:09 gunner kernel: [  138.071228] md: md0: resync done.
Jul 13 11:25:09 gunner kernel: [  138.092346] md: checkpointing resync of md0.
Jul 13 11:25:09 gunner kernel: [  138.158365] md: md0 stopped.
Jul 13 11:25:09 gunner kernel: [  138.158374] md: unbind<sdb>
Jul 13 11:25:09 gunner kernel: [  138.220022] md: export_rdev(sdb)
Jul 13 11:25:09 gunner kernel: [  138.220059] md: unbind<sda3>
Jul 13 11:25:09 gunner kernel: [  138.300019] md: export_rdev(sda3)
Jul 13 11:25:20 gunner kernel: [  148.322724] md: md0 still in use.
Jul 13 11:25:20 gunner kernel: [  148.381205] md: bind<sdb1>
Jul 13 11:25:20 gunner kernel: [  148.381345] md: bind<sda3>
Jul 13 11:25:20 gunner kernel: [  148.414172] raid1: md0 is not clean -- starting background reconstruction
Jul 13 11:25:20 gunner kernel: [  148.414175] raid1: raid set md0 active with 2 out of 2 mirrors
Jul 13 11:25:20 gunner kernel: [  148.414199] md0: detected capacity change from 0 to 500106723328
Jul 13 11:25:20 gunner kernel: [  148.414438]  md0:
Jul 13 11:25:20 gunner kernel: [  148.414525] md: resync of RAID array md0
Jul 13 11:25:20 gunner kernel: [  148.414528] md: minimum _guaranteed_  speed: 1000 KB/sec/disk.
Jul 13 11:25:20 gunner kernel: [  148.414531] md: using maximum available idle IO bandwidth (but not more than 200000 KB/sec) for resync.
Jul 13 11:25:20 gunner kernel: [  148.414536] md: using 128k window, over a total of 488385472 blocks.
Jul 13 11:25:20 gunner kernel: [  148.414539] md: resuming resync of md0 from checkpoint.

```

That log clearly shows it binding to the wrong device at 2.486781 second.  The unbind/bind at 138 and 148 seconds is where I ran 'mdadm --stop' and 'mdadm --assemble ...' by hand.

But I can't figure out how to get it to *boot* using the correct array setup.  I've tried listing the correct devices in mdadm.conf, but that didn't help.  I guess I could start over and setup the raid volume to use the whole second device instead of the a partition, but I want to know *why* it is failing.

-William

---

### Post by ruffEdgz on 2010-07-13
I'm curious how your parition is setup so could you do a: 

```
fdisk -l
```

Could you also explain how you setup each partition so for example:

/dev/sda
sda1 ---> /
sda2 ---> /boot
sda3 ---> swap
....
....
....etc....

The reason why I'm asking is for a RAID1 to work, you need two partitions to be the same size for it to work. So I could see how you used sda1 for boot, sda2 for / and sda3 for swap but made 2 logical volumes (sda5 and sda6 made from sda4) for your RAID1 home directory.

Thanks and if you want, I can write up something to make this work using the software raid application.

---

### Post by wlott on 2010-07-13
```
wlott@gunner:~$ sudo fdisk -l

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00096610

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13131   105467904   83  Linux
/dev/sda2           13131       17021    31250432   82  Linux swap / Solaris
/dev/sda3           17021       77826   488412160   fd  Linux raid autodetect

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000e4cb8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60802   488385536   fd  Linux raid autodetect

Disk /dev/md0: 500.1 GB, 500106723328 bytes
2 heads, 4 sectors/track, 122096368 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table

```

sda1 is /, sda2 is swap, sda3 is 1/2 the raid1
sdb1 is the other half of the raid1

I didn't setup a seperate /boot partition because, well, I wasn't sure one was needed.

I've also noticed that /dev/sdb and /dev/sdb1 both have the same uuid:

```
wlott@gunner:~$ sudo blkid /dev/sdb /dev/sdb1
/dev/sdb: UUID="a5134384-b6ac-9e50-7ce7-c79d99884b9a" TYPE="linux_raid_member"
/dev/sdb1: UUID="a5134384-b6ac-9e50-7ce7-c79d99884b9a" TYPE="linux_raid_member"

```

I have no idea if that is normal, but it seems like it could be a problem.

---

### Post by ruffEdgz on 2010-07-13
Good catch!

That might be the reason why its trying to use sdb instead of sdb1. To be safe, you might want to clear the partition tables, recreate sdb1 again and this time around, only setup the dmraid to point to sdb1 (I can only assume this wasn't done before but if it was done this way before,I appologize).

Once sdb1 has a UUID and not sdb, that should help your out with a RAID1 /home directory :D

---

### Post by wlott on 2010-07-13
I believe that that is exactly what I did.  I wiped both drives with a 'dd if=/dev/zero of=/dev/sd[ab]', ran the ubuntu server installer, and used it to create a partition table on each drive.  I didn't do any manual dmraid setup myself--everything was via the installer.

---

### Post by wlott on 2010-07-13
Workaround found.  I didn't realize that I needed to run update-initramfs after changing /etc/mdadm/mdadm.conf.  Once I did that, my explicit list of devices (as opposed to 'partitions') in mdadm.conf took effect and the array assembles correctly on boot.

But I still have no explanation as to why /dev/sdb looks like a valid raid partition.

---

### Post by wlott on 2010-07-13
It looks like the superblocks for /dev/sdb and /dev/sdb1 are in the same place.  In a fit of cleaverness, I decided to try to clear out the superblock info for /dev/sdb.  Well, it appears to have clobbered the superblock for /dev/sdb1 also.  If the superblock for both the whole disk and the partition are in the same place, that would explain why the uuids are the same, etc.

Next up: reinstall from scratch but use sdb instead of sdb1 for the raid setup.

---

### Post by YesWeCan on 2010-07-14
I have had my share of raid mounting problems during boot with 10.04.
I had to:
- uninstall dmraid. It seems that this is automatically installed in 9.10 and 10.04 and if there is any legacy fake raid stuff in your system it will foul things up.
- tell mdadm to use partition UUIDs rather than letters in /etc/mdadm/mdadm.conf. You ought to end up with /dev/sda3 and /dev/sdb1 having the same UUID. In mdadm.conf tell it to scan for devices with this UUID.

---

### Post by ruffEdgz on 2010-07-14
> **wlott said:**
> It looks like the superblocks for /dev/sdb and /dev/sdb1 are in the same place.  In a fit of cleaverness, I decided to try to clear out the superblock info for /dev/sdb.  Well, it appears to have clobbered the superblock for /dev/sdb1 also.  If the superblock for both the whole disk and the partition are in the same place, that would explain why the uuids are the same, etc.

Next up: reinstall from scratch but use sdb instead of sdb1 for the raid setup.
Glad to hear that its slowly but surely coming together for you. Hope to hear in the next post that all is well with your RAID1 home directory.

@YesWeCan - Good points about software RAIDS on a Ubuntu system.

---

### Post by wlott on 2010-07-14
Okay, I finally got it to "work".  I created three partitions on /dev/sdb, 1 and 3 being empty padding and partition 2 being most of the drive:

```
wlott@gunner:~$ sudo fdisk -l /dev/sdb

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000608c4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1           2       15041   83  Linux
/dev/sdb2               3       60800   488359935   fd  Linux raid autodetect
/dev/sdb3           60801       60801        8032+  83  Linux

```

With this setup, the raid scanning stuff doesn't get confused and decide to use /dev/sdb instead of a partition on /dev/sdb.  I don't know if both padding partitions are necessary--I got tired of reinstalling just to test out different configurations.  I also couldn't get it to work when I tried to use /dev/sdb as the second raid device.  That config also failed to boot, but again, I was too burned out troubleshooting to try to figure out why.  Especially when I was pretty sure that this extra padding partitions idea should work.

Thanks for the help everyone.

-William

---

