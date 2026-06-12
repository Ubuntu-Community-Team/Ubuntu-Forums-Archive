---
title: "Raid 1 help please."
date: 2010-12-12
forum: Server Platforms
---

### Post by bigsigh on 2010-12-12
I've assembled a server with a pair of drives using the Ubuntu 10.04  server install following the raid setup instructions in the Ubuntu wiki.  There are only two drives and the server boots from the raid, according  to the wiki this creates a potential issue with boot and initrmfs and  the default install setup for the raid is degraded????

It appears I've screwed something up or failed to implement a step for I only see one drive listed.

Would someone mind reading this output and give me their observations of what I failed to do properly and how I might fix it?


Linux server3 2.6.32-26-generic-pae #48-Ubuntu SMP Wed Nov 24 10:31:20  UTC  2010                                                                               i686 GNU/Linux
Ubuntu 10.04.1 LTS

  System information as of Sun Dec 12 10:42:06 MST 2010

  System load:  0.62               Processes:           220
  Usage of /:   9.6% of 458.45GB   Users logged in:     1
  Memory usage: 16%                IP address for eth1: 192.168.0.143
  Swap usage:   0%


user@server3:~$ cat /proc/mdstat

Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]

md0 : active raid1 sdb[1]
      488385472 blocks [2/1] [_U]

unused devices: <none>

user@server3:~$ sudo mdadm --query --detail /dev/md0

/dev/md0:
        Version : 00.90
  Creation Time : Wed Jul  7 22:43:50 2010
     Raid Level : raid1
     Array Size : 488385472 (465.76 GiB 500.11 GB)
  Used Dev Size : 488385472 (465.76 GiB 500.11 GB)
   Raid Devices : 2
  Total Devices : 1
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Sun Dec 12 10:47:40 2010
          State : active, degraded
 Active Devices : 1
Working Devices : 1
 Failed Devices : 0
  Spare Devices : 0


    Number   Major   Minor   RaidDevice State
       0       0        0        0      removed
       1       8       16        1      active sync   /dev/sdb

user@server3:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0006e4d3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60802   488385536   fd  Linux raid autodetect

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/md0: 500.1 GB, 500106723328 bytes
2 heads, 4 sectors/track, 122096368 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table


Thank you for any help.

---

### Post by rubylaser on 2010-12-12
It appears that you've removed /dev/sda from the RAID array.  Since, that device used to be in there, it's probably easiest to zero it's superblock, then add it back to the array, like this...
```
mdadm --zero-superblock /dev/sda
```
```
mdadm --manage /dev/md0 --add /dev/sda
```

Without more info on the commands you ran and a look at your partitioning with an fdisk -l this should get you back on the right track.

---

### Post by bigsigh on 2010-12-12
Hi,
Thank you for looking at my issue.
I left the commands I used in my orig post, the last block of text in my post lists the output from fdisk -l, is that the info you were looking for?

I'm confused.

From my original post here I've copied parts:
cat /proc/mdstat

Number   Major   Minor   RaidDevice State
       0       0        0        0      removed
       1       8       16        1      active sync   /dev/sdb

and here:
sudo mdadm --query --detail /dev/md0

/dev/md0:
     Raid Level : raid1
   Raid Devices : 2
  Total Devices : 1

This matches what you've said about removal since device 0 should be sda I assume, I don't know what I did to remove a drive.

I have the gnome desktop installed and using the gui disk utility it shows sda1 as a ext3 volume partition type Linux RAID autodetect and is also Not Mounted.
Whereas the sdb drive volume is RAID component.
I believe this info matches up with the output of fdisk in my orig post.

Your observation has me thinking that the server is running off sda alone and not in raid, though there is a raid volume running(?) that is sdb?
But......
 mount -l
/dev/md0 on / type ext3 (rw,errors=remount-ro)
and....
 df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/md0              459G   44G  392G  11% /
none                  2.0G  200K  2.0G   1% /dev
none                  2.0G  216K  2.0G   1% /dev/shm
none                  2.0G   96K  2.0G   1% /var/run
none                  2.0G     0  2.0G   0% /var/lock
none                  2.0G     0  2.0G   0% /lib/init/rw
none                  459G   44G  392G  11% /var/lib/ureadahead/debugfs

Indicates the server is running on raid not a solo drive but as you've stated a raid array with a single drive.

I have a couple of virtual machines running in vb that I will need to export copies of before I mess with this. The Ubuntu server install is merely the host for the virt machines. I want to be able to reimport good current machines if I should destroy and have to rebuild the host before I try to fix the raid.

If I can't 'fix' the raid without destroying the Ubuntu 10.04 host I may instead install esxi to this server if I can figure out how to import the vb machines into it just to minimize the host overhead, I like vb so I'm loathe to do that.

Thanks again for any more observations.

---

### Post by rubylaser on 2010-12-13
Your root filesystem is running of of the degraded RAID array on /dev/sdb. The commands I gave you would remove the RAID info from sda and then add it back to the array.

I personally love Proxmox for virtualization. [http://pve.proxmox.com/wiki/Main_Page]("http://pve.proxmox.com/wiki/Main_Page")

Proxmox VE is a professional virtualization solution developped under GPL license that runs on Debian Lenny. It has a bare metal installer, like VMWARE ESXi. It also has many nice features, like clustering, web interface management, live migration (for KVM), snapshots (with LVM), backup with vzdump. Proxmox provides two virtualization solutions, both GPL : openvz and KVM.

In contrast, Virtualbox is aimed primarily as a desktop solution. I'm afraid to rely on VB in the long term, because VirtualBox, which was bought by SUN, is now owned by Oracle. And, maybe you saw what happened with OpenSolaris?

Man, that sounds like an add, but I just thought I give you another option if you haven't heard of Proxmox.

---

### Post by bigsigh on 2010-12-14
The ongoing saga. 

zero superblock gives:
mdadm: Couldn't open /dev/sda for write - not zeroing

based on a few posts I read I actually swapped the two drives on the sata ports they were connected to, this accomplished nothing.

But.

It appears one drive has a master boot record and the other does not. I'm not clear on this, because, I continued with: 
```
sudo mdadm -D /dev/md0
```          
 and so the differences are now

State : clean, degraded

    Number   Major   Minor   RaidDevice State
       0       0        0        0      removed
       1       8        0        1      active sync   /dev/sda

and now sdb is removed and sda is active.

So, for giggles I: 
```
sudo mdadm --assemble /dev/md0 --uuid=5c4d63e3:a0fb0746:e8d51f2c:92958083
```mdadm: device /dev/md0 already active - cannot assemble it

```
 sudo cat /proc/mdstat
```Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid1 sda[1]
      488385472 blocks [2/1] [_U]

unused devices: <none>

and I: 
```
mdadm --manage /dev/md0 --add /dev/sdb
```mdadm: error opening /dev/md0: Permission denied

Boo. So I: 
```
sudo mdadm --create /dev/md0 -v -l 1 -n 2 /dev/sda /dev/sdb
```mdadm: another array by this name is already running.

So I: 
```
sudo mdadm --manage /dev/md0 --add /dev/sdb1
```and

mdadm: added /dev/sdb1

```
 sudo cat /proc/mdstat
```Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid1 sdb1[2] sda[1]
      488385472 blocks [2/1] [_U]
      [>....................]  recovery =  3.1% (15244096/488385472) finish=85.9min speed=91765K/sec

unused devices: <none>

```
 sudo fdisk -l
```Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sda doesn't contain a valid partition table

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0006e4d3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       60802   488385536   fd  Linux raid autodetect

Disk /dev/md0: 500.1 GB, 500106723328 bytes
2 heads, 4 sectors/track, 122096368 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table


I'm quite confused. I'm going to let this finish the recovery and see what I end up with.

I'm concerned about md0 being made up of sda and sdb1, why does one have the partition and not the other?

The whole point of is a server built upon two mirrored drives, if one fails, the server install isn't destroyed, it is powered down, the bad drive is replaced and and booting up the new drive is mirrored and voila.

Perhaps I missing something, well no doubt I am.

---

### Post by bigsigh on 2010-12-15
and so.....

 sudo mdadm -D /dev/md0
/dev/md0:
        Version : 00.90
  Creation Time : Wed Jul  7 22:43:50 2010
     Raid Level : raid1
     Array Size : 488385472 (465.76 GiB 500.11 GB)
  Used Dev Size : 488385472 (465.76 GiB 500.11 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Tue Dec 14 20:10:15 2010
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

           UUID : 5c4d63e3:a0fb0746:e8d51f2c:92958083
         Events : 0.18006424

    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       8        0        1      active sync   /dev/sda

fdisk -l returns the same info in the previous post.....

Another question, what will happen on reboot since the mdadm.conf states "DEVICE partitions"?

```
cat /proc/partitions
```
major minor  #blocks  name

   8        0  488386584 sda
   8       16  488386584 sdb
   8       17  488385536 sdb1
   9        0  488385472 md0

Will this drop or remove sdb1 from the array on boot?

Does mdadm.conf need to state DEVICE /dev/sda /dev/sdb1 in order to boot without dropping a drive from the array?

This array was created by the Ubuntu server installer, why weren't the two drives partitioned as sda and sdb alone? Why is there a partition on only one drive?

---

### Post by SaturnusDJ on 2010-12-15
Ubuntu installs right away to RAID1. I did the same with 10.04 and converted to RAID5 later.
Something must have gone wrong during the install because in your first post there already is a disk (sdb) in the array in stead of a partition from this or another disk.


I don't know for sure what will happen when you boot, I've read it is possible to have a mdadm array that consists of a harddrive without partition, but this is not recommended.

A reinstall would be nice. If you are able to reinstall, follow a 'How to install Ubuntu on mdadm RAID1' or so then...

If you can't reinstall, try to boot from the one actually having a partition. If this works, do step 2 from here [http://ubuntuforums.org/showthread.php?t=1636977](http://ubuntuforums.org/showthread.php?t=1636977) but of course copying from the one containing partitions to the one that has not...whatever /dev/sd* they may be. That should give the other disk the same partitioning layout (not data!). Afterwards you can start putting them in RAID1. Be sure to start with the one having the correct data.


If you can't reinstall and can't boot from the partitioned harddisk...you can try to kick the one with the partition out of the array and do
```
mdadm --manage /dev/md0 --add /dev/sdb
```
in stead of
```
mdadm --manage /dev/md0 --add /dev/sdb1
```
as you did earlier.
Personally, I don't like this however.

---

### Post by bigsigh on 2010-12-15
Thank you for your observations.

> **SaturnusDJ said:**
> I've read it is possible to have a mdadm array that consists of a harddrive without partition, but this is not recommended.

Interesting, I have been building ubuntu desktop installs with swap files, and that may have been my intention here, I needed a host for vm's and so built this server for that some time ago and am only now following up........ you know how it goes, hence I've discovered this issue, everything performs fine, the vm's are exported and backed up but this issue defeats the purpose of mirroring drives obviously.


> A reinstall would be nice. If you are able to reinstall, follow a 'How to install Ubuntu on mdadm RAID1' or so then...This is the quide I used originally, [https://help.ubuntu.com/10.04/serverguide/C/advanced-installation.html](https://help.ubuntu.com/10.04/serverguide/C/advanced-installation.html) though I was confused about the booting into a degraded array part and am wondering if that is my issue.

I would like to 'fix' this, so I better understand my raid tools, a reinstall is the easy way out. That said, I won't have time to continue on with this for another day.

---

### Post by bigsigh on 2010-12-17
So, I shutdown the vm's and rebooted. Fail.

I swapped the drives around to where I had them originally, blah, blah.
I tried so many different approaches that I no longer remember.

I finally booted a live Mint dvd, installed mdadm and zero'd the superblock on sbd and the superblock based on boot  sda1 while reading boot errors one of which stated there were duplicate(?) superblocks on sda and sda1.

Then used the grub2 cli to boot to hd0,1, from here [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2) and so the server is back up. Being under time constraints I put the monitor back where I got it and started the vm's back up, the grub.cfg is still setup for raid, I did not update-grub it at this time so I'll probably have to grub rescue next boot.

Now currently, I have set up the partition on sdb to match sda except for the boot flag. I am now offsite and have done this remotely.

I did indeed set this server up with a swap file.

```

sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0006e4d3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60802   488385536   fd  Linux raid autodetect

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0006ad7c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001   fd  Linux raid autodetect

cat /proc/partitions

major minor  #blocks  name

   8        0  488386584 sda
   8        1  488385536 sda1
   8       16  488386584 sdb
   8       17  488384001 sdb1

cat /proc/mdstat

Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
unused devices: <none>


```Should both drives have the boot flag?

Any suggestions on where to start to morph this back into a functioning raid1?
 
The point here is to have the vm's backed up off disk and if a disk fails to not have the server go down, but to allow the bad drive to be swapped out and replaced.

I could have blown this out and reinstalled tonight, but I'd like to see if I can fix it so it works the way I want and learn something in the process, one of those battles I want to win I guess.
I'm going to sleep.

---

