---
title: "moving my RAID mirrors to a new system?"
date: 2020-03-30
forum: Server Platforms
---

### Post by jfaberna on 2020-03-30
I have searched for this issue but have not found the answer to my situation.

I have a working Ubuntu 18.04.4 Server that has been updated from 16.04 over the years and to fix some issue just needs to be rebuilt. 
My hardware is a Core i7 with /dev/sda as the boot drive.
/dev/md0 is a mdadm RAID 1 using /dev/sdb and /dev/sdc
/dev/md1 is a mdadm RAID 1 using /dev/sdd and /dev/sde

The RAID storage is all application data

How can I do a fresh Ubuntu 18.04.4 Server installation on /dev/sda and just add the existing RAIDs back in??

Jim A

---

### Post by TheFu on 2020-03-30
Please show the disk layout with commands.  i.e.  prove it. The commands that I’d use:
```

sudo fdisk -lm
df -hT -x squashfs -x tmpfs -x devtmpfs
lsblk -e 7 -o name,size,type,fstype,mountpoint
```

in theory, you'd just need to use **mdadm --detail --export** to save off the metadata for the array, then move the disks to a new system and use **mdadm --scan --assemble** based on the mdadm.conf file.  Be certain you create 100% great backups for any data you can't lose BEFORE starting.

Also, be certain to review the mdadm manpages for any caveats that are system dependent.  There's a section on export worth reviewing. 

it has been years, but I’ve moved SW-Raid arrays to new systems without issue 3 times.  No prep work before.   i was foolish and lucky. i know this now.  i just physically disconnected the array before doing the OS installs, then connected up the array when ready to setup the mdadm stuff.

BTW, hope you don't use the whole disk for any part of this.  Always use partitions. There are a number of reasons.

---

### Post by jfaberna on 2020-03-30
```
jim@mythbuntu:~$ sudo fdisk -l
Disk /dev/sda: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x06effeeb

Device     Boot     Start       End   Sectors   Size Id Type
/dev/sda1  *         2048 960190463 960188416 457.9G 83 Linux
/dev/sda2       960192512 976773167  16580656   7.9G 82 Linux swap / Solaris


The primary GPT table is corrupt, but the backup appears OK, so that will be used.
Disk /dev/sdb: 1.8 TiB, 2000398934016 bytes, 3907029168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: A6404841-6BA3-4ABE-9788-BAC0BBF7F865


Disk /dev/sdc: 1.8 TiB, 2000398934016 bytes, 3907029168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


The primary GPT table is corrupt, but the backup appears OK, so that will be used.
Disk /dev/sdd: 1.8 TiB, 2000398934016 bytes, 3907029168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 57DCE762-1D3A-8F4F-8C62-64E0BA3D32A2


The primary GPT table is corrupt, but the backup appears OK, so that will be used.
Disk /dev/sde: 1.8 TiB, 2000398934016 bytes, 3907029168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 57DCE762-1D3A-8F4F-8C62-64E0BA3D32A2


Disk /dev/sdf: 1.8 TiB, 2000398934016 bytes, 3907029168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 06E699C4-D649-C847-BF5A-FC28AC604FF6

Device     Start        End    Sectors  Size Type
/dev/sdf1   2048 3907029134 3907027087  1.8T Linux filesystem


Disk /dev/md1: 1.8 TiB, 2000264691712 bytes, 3906766976 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/md0: 1.8 TiB, 2000264691712 bytes, 3906766976 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes

```
```
jim@mythbuntu:~$ df -hT -x squashfs -x tmpfs -x devtmpfs
Filesystem     Type  Size  Used Avail Use% Mounted on
/dev/sda1      ext4  451G  9.7G  422G   3% /
/dev/md0       ext4  1.8T  430G  1.3T  25% /mnt/md0
/dev/md1       ext4  1.8T  364G  1.4T  21% /mnt/md1
/dev/sdf1      ext4  1.8T   80G  1.7T   5% /mnt/external-backup
```
```
jim@mythbuntu:~$ lsblk -e 7 -o name,size,type,fstype,mountpoint
NAME     SIZE TYPE  FSTYPE            MOUNTPOINT
sda    465.8G disk                    
&#9500;&#9472;sda1 457.9G part  ext4              /
&#9492;&#9472;sda2   7.9G part  swap              [SWAP]
sdb      1.8T disk  linux_raid_member 
&#9492;&#9472;md0    1.8T raid1 ext4              /mnt/md0
sdc      1.8T disk  linux_raid_member 
&#9492;&#9472;md0    1.8T raid1 ext4              /mnt/md0
sdd      1.8T disk  linux_raid_member 
&#9492;&#9472;md1    1.8T raid1 ext4              /mnt/md1
sde      1.8T disk  linux_raid_member 
&#9492;&#9472;md1    1.8T raid1 ext4              /mnt/md1
sdf      1.8T disk                    
&#9492;&#9472;sdf1   1.8T part  ext4              /mnt/external-backup

```

---

### Post by darkod on 2020-03-30
First thing to notice in the lsblk output is that you are using the whole disks as raid members. Ideally you should use partitions, like TheFu mentioned.

You could use this to redo the arrays. If you do want to do it, the high level plan would be something like:
1. Remove sdc from md0.
2. Zero the superblock on sdc and make one large gpt partition on it.
3. Create new md2 raid1 array from sdc1 and one missing member.
4. Copy all data from md0 to md2.
5. Destroy md0 array.
6. Zero the superblock on sdb, make one large gpt partition on it, and add it to md2.
7. Do the same for the other array.

If you just want to migrate the existing arrays, it should be very easy (high level plan). 
1. Using blkid and mdadm -D /dev/md0, and mdadm -D /dev/md1 note down the array UUIDs.
2. Install the new OS on sda with the array disks disconnected.
3. Connect the array disks and edit /etc/mdadm/mdadm.conf to add ARRAY definition with array name and UUID (I prefer doing this manually then using auto scan commands).
4. Reboot and check the arrays autoassemble correctly.
5. Add the fstab mount option as necessary.

Most of these steps are simple but if you need help with the exact commands to run, ask first. Be very careful not to run anything you don't understand it does.

---

### Post by TheFu on 2020-03-30
So, it looks like my guesses and your statements were all true.  Always best to be 100% certain by checking. We all forget details over time and sometimes forget quick changes made 8 months ago that changed everything as we were running out the door.

[LIST=1]
[*]Backup everything you don't want to lose. System, configs, data.  I've found that having a backup almost always means I never need it. OTOH, not having a current backup means I needed it badly. Call it Murphy's Insurance.
[*]Especially backup /etc/ and get a list of manually installed packages (**apt-mark**); that list can be used later to quickly reinstall those packages on the new OS. Obviously, the list needs to be included in the backup data. ;) 
[*]Disconnect the sd[bcde] disks from the system; either power or data cables or both. Basically, we want just the OS disk connected for a fresh install. This prevents the installer from doing unwanted things and limits our confusion as to where grub should be installed.
[*]Perform a fresh install onto sda - May want to use LVM so snapshots and other LVM-only capabilities are possible. Also, with LVM, you can add a mirror afterwards easily for any LVs.
[*]After the first reboot, restore most of the former data and configs, but not the stuff on the RAIDs or the packages that use the RAID data. Put the customized configs back where they need to be too.  I would NOT restore everything from /etc/ in the backups. The restore of that data needs to be highly selective.  Perhaps some apache/nginx config files, power settings, the mdadm.conf, /etc/hosts, stuff like that.  Check for *.local files too.
[*]Shutdown for the 2nd time post install, connect the disk array storage back up.
[*]Boot, configure the RAID storage as before. **mdadm --assemble** on each array, then probably just copy over the fstab lines for the md* mounts from before. May want to rethink using /mnt/, since the *Linux File System Hierarchy Standards* are clear that area is not for permanent storage - neither is /media/, BTW.  I doubt I'd change any mounts at this point, if I were you, honestly. However, standards are there for a reason and worth knowing. Ensure those mount point directories exist unless you are using systemd-mount or systemd-automount.
[*]**mount -a**  to mount the RAID arrays; 
[*]Install the last remaining settings, then the packages for those that actually access the RAID storage. These should automatically start, see the configs, find the data, and run nicely.
[*]Do a little "happy dance".  Absolutely critical step. ;)
[/LIST]
If everything goes well, this is 30-45 minutes of effort.

Consider setting up mdadm.conf to use UUIDs rather than devices.  Devices can change names/order.  It is an anti-pattern to use devices directly or to use whole drive devices rather than partitions.  I'm betting that changing to partitions for the arrays is something not worth your effort at this point. Heck, I wouldn't do it myself, until the next time you need to replace a failed disk.

BTW, here's my 2 RAID1 arrays:
```
$ more /proc/mdstat 
Personalities : [raid1] [linear] [multipath] [raid0] [raid6] [raid5] [raid4] [raid10] 
md1 : active raid1 sdd3[2] sdc3[3]
      1943010816 blocks super 1.2 [2/2] [UU]
      
md2 : active raid1 sdf2[1] sde2[0]
      1338985536 blocks [2/2] [UU]
      
unused devices: <none>

```

---

### Post by jfaberna on 2020-03-30
most helpful guys, thanks a lot.

I'd like to understand why use a partition instead of a drive?  i.e. using /dev/sdc1 vs. /dev/sdc in a raid??

The only problems I've had with these 2 arrays in the last year is when I get errors and one of the drives fails.  Turned out to be a SATA cable and not the drive, but recover is the same.

Also I looked at man mdadm and was confused on the zeroing of the superblock. Can you explain more??

Jim A

---

### Post by TheFu on 2020-03-30
Google found this: [https://raid.wiki.kernel.org/index.php/Partition_Types](https://raid.wiki.kernel.org/index.php/Partition_Types)
Partitions are mainly a protection tool. Hard to create a Raid on a partition that is marked for some other use.  When we use the whole disk, there isn't any protection.  
Alignment can be controlled. Using the whole disk, where does the partition table go? Does that cause misalignment for the RAiD data?
When it is time to upgrade disks, exact sizes are easier to control.

Do you keep a copy of the OS or boot areas cloned somewhere easily accessible?  i do. it goes on a partition on the RAiD disks that doesn't get used and isn't RAiD.

A few other reasons that slip my mind. Google should find those.

When i move my current mdadm SW-RAiD to new disks, it will either be to LVM-RAiD (managed by LVM commands, not mdadm) or ZFS both for greater flexibility and simplicity.

---

### Post by darkod on 2020-03-30
The mdadm superblock is where the partition (or drive) holds the information that it is part of an array. I mentioned zeroing it in case you want to use the drive/partition in new array. In such case it would be best to zero the superblock to remove info from previous array membership.

I personally prefer partitions to make sure a new disk will be able to be used in the array you have. Because to add new member it has to be same size or bigger, but not smaller. And drives from different manufacturers or families could have small difference in total size, even when it says the drives are 2TB for example.

That is why I create one big partition leaving the last 15-20MiB unused.

Lets say your current 2TB disk has a total of 1,900,860 MiB. So your raid1 array will also have that size, as each separate member disk.
One disk dies and you buy new 2TB but this one has 1,900,855 MiB. You won't be able to add it to the array because it is smaller than current members.

But if you created originally a partition of 1,900,840 MiB on your disks and used that for the array, and later you wan to add disk of 1,900,855 MiB you will still be able to make a partition of 1,900,840 MiB on it and use it for the array.

I think there are more benefits but I mainly use partitions because of this. Remember, since the HDDs were created it was always intended to be used as partitioned drives. Windows, Linux, etc, almost all OS creates partitions on the disk, not using the disk itself directly.

---

### Post by jfaberna on 2020-03-31
Great information!  Now I'm ready to do some experimenting with all this.

Thanks all,

Jim A

---

### Post by jfaberna on 2020-03-31
In my experiment I have a new mirror (/dev/md0) created with partitions /dev/sdc1 and /dev/sdd1
When I look at the /etc/mdadm/mdadm.conf I see this line:
```
ARRAY /dev/md0 metadata=1.2 name=jim-development:0 UUID=236440f0:f179f633:7327d22d:de2a6045

```
but when I do sudo blkid for /dev/md0 I see a different UUID.
```
/dev/md0: UUID="576082ff-2a0f-468c-b3a9-61879438d809" TYPE="ext4"

```
I'm pretty sure I use the UUID from blkid to put in the fstab for automatic mount.

Is there any significance to the different UUIDs?

FYI, my lsblk looks odd to me, but may be what you expected switching to using partitions instead of whole disks.
```
NAME        SIZE FSTYPE            TYPE  MOUNTPOINT
sda       465.8G                   disk  
&#9500;&#9472;sda1      487M vfat              part  /boot/efi
&#9500;&#9472;sda2      7.6G swap              part  [SWAP]
&#9492;&#9472;sda3    457.7G ext4              part  /
sdb         1.8T                   disk  
&#9492;&#9472;sdb1      1.8T ext4              part  /home
sdc       931.5G                   disk  
&#9492;&#9472;sdc1    931.4G linux_raid_member part  
  &#9492;&#9472;md127 931.3G ext4              raid1 /mnt/md0
sdd       931.5G                   disk  
&#9492;&#9472;sdd1    931.4G linux_raid_member part  
  &#9492;&#9472;md127 931.3G ext4              raid1 /mnt/md0

```

---

### Post by darkod on 2020-03-31
Yes, the md0 ext4 UUID you can use in fstab which is better option than using /dev/md0.

In mdadm.conf in the ARRAY configuration you use the UUID of the array itself, it will be a value shared between sdc1 and sdd1. You need to use that in mdadm.conf after creating new array to make sure it autoassembles on boot. If there is no ARRAY definition it will not autoassemble. You can also get this array UUID in sudo mdadm -D /dev/md0

---

### Post by jfaberna on 2020-03-31
It's strange to me that when I built the array I used the name /dev/md0, even when I mounted it manually.  But after I added the UUID to the fstab, it now is /dev/md127
```
ARRAY /dev/md0 metadata=1.2 name=jim-development:0 UUID=236440f0:f179f633:7327d22d:de2a6045

```
```
jim@jim-development:~$ lsblk
NAME      MAJ:MIN RM   SIZE RO TYPE  MOUNTPOINT
sda         8:0    0 465.8G  0 disk  
&#9500;&#9472;sda1      8:1    0   487M  0 part  /boot/efi
&#9500;&#9472;sda2      8:2    0   7.6G  0 part  [SWAP]
&#9492;&#9472;sda3      8:3    0 457.7G  0 part  /
sdb         8:16   0   1.8T  0 disk  
&#9492;&#9472;sdb1      8:17   0   1.8T  0 part  /home
sdc         8:32   0 931.5G  0 disk  
&#9492;&#9472;sdc1      8:33   0 931.4G  0 part  
  &#9492;&#9472;md127   9:127  0 931.3G  0 raid1 /mnt/md0
sdd         8:48   0 931.5G  0 disk  
&#9492;&#9472;sdd1      8:49   0 931.4G  0 part  
  &#9492;&#9472;md127   9:127  0 931.3G  0 raid1 /mnt/md0
``````


jim@jim-development:~$ sudo mdadm -D /dev/md127
/dev/md127:
           Version : 1.2
     Creation Time : Tue Mar 31 11:42:11 2020
        Raid Level : raid1
        Array Size : 976532480 (931.29 GiB 999.97 GB)
     Used Dev Size : 976532480 (931.29 GiB 999.97 GB)
      Raid Devices : 2
     Total Devices : 2
       Persistence : Superblock is persistent

     Intent Bitmap : Internal

       Update Time : Tue Mar 31 14:04:22 2020
             State : clean, resyncing 
    Active Devices : 2
   Working Devices : 2
    Failed Devices : 0
     Spare Devices : 0

Consistency Policy : bitmap

     Resync Status : 59% complete

              Name : jim-development:0  (local to host jim-development)
              UUID : 236440f0:f179f633:7327d22d:de2a6045
            Events : 7863

    Number   Major   Minor   RaidDevice State
       0       8       33        0      active sync   /dev/sdc1
       1       8       49        1      active sync   /dev/sdd1
```

---

### Post by darkod on 2020-03-31
I see the array is still syncing. Avoid testing too much until it finishes the sync. I have seen cases where it renames the array to md127, I don't know why it happens.
Basically the /dev/md0 in the ARRAY definition should make the device name static.

But let it sync first and then reboot and check what is the array called after the reboot.

---

### Post by jfaberna on 2020-03-31
it was still md127 after sync completed and a reboot. I'm going to redo all this and not mess with it until sync has complete. 

Does it matter if I use fdisk or parted to partition the drive to GPT and add partitions? both now support GPT.

---

### Post by darkod on 2020-03-31
I still prefer parted even after they have added gpt support to fdisk.

---

### Post by jfaberna on 2020-04-01
> **jfaberna said:**
> it was still md127 after sync completed and a reboot. I'm going to redo all this and not mess with it until sync has complete. 

I figured this one out.  It uses md127 if something is not just right.

I had forgotten to do the step:
```
sudo update-initramfs -u

```

---

