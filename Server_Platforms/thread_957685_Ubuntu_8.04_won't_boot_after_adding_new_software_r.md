---
title: "Ubuntu 8.04 won't boot after adding new software raid10"
date: 2008-10-24
forum: Server Platforms
---

### Post by rondin on 2008-10-24
I am currently having 2x 500GB hard drives, 3 partitions. sda1 for Boot, sda2 for / and sda3 for swap and 2 raid arrays, md0 raid1 for boot and md1 raid10 for /. (The swap partitions are not on a raid)

Here is my fdisk
```

root@fs1:~# fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00066974

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      104391   fd  Linux raid autodetect
/dev/sda2              14       60314   484367782+  fd  Linux raid autodetect
/dev/sda3           60315       60801     3911827+  82  Linux swap / Solaris

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00078211

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1          13      104391   fd  Linux raid autodetect
/dev/sdc2              14       60314   484367782+  fd  Linux raid autodetect
/dev/sdc3           60315       60801     3911827+  82  Linux swap / Solaris

Disk /dev/md0: 106 MB, 106823680 bytes
2 heads, 4 sectors/track, 26080 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x1dd13404

    Device Boot      Start         End      Blocks   Id  System

Disk /dev/md1: 495.9 GB, 495992504320 bytes
2 heads, 4 sectors/track, 121091920 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x420f65f6

    Device Boot      Start         End      Blocks   Id  System

```

I am using lvm2, i have one volume group vg-fs1 and several lvs.
I want to add another 2x 500G drives for backups. And I have folowed the following procedure:

I used fdisk to create a new partition on both drives and take the whole space with partition type fd (Linux raid)

```

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001   fd  Linux raid autodetect
/dev/sdd1               1       60801   488384001   fd  Linux raid autodetect

```

Now I created my new raid array:

**mdadm -v --create /dev/md2 --level=raid10 --raid-devices=2 /dev/sdb1 /dev/sdd1 --auto=md**

I was checking /proc/mdstat to make sure that my raid array is 100% complete.

After my raid was complete, I run

[B]pvcreate /dev/md2
vgextend "vg-fs1" /dev/md2[/B]

Now I have checked my Free PE doing vgdisplay vg-fs1 and it was 16717 (1813 from previous and 14904 from the two new drives /dev/md2). So now I am creating a logical volume, making sure that I will only use the nodes from /dev/md2, so I did:

**lvcreate -l 14904 -n lv-backup vg-fs1 /dev/md2**

My Logical volume was successfully created. Now I run:

```
root@fs1:~# **mkfs.ext3 /dev/mapper/vg--fs1-lv--backup**
mke2fs 1.40.8 (13-Mar-2008)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
30523392 inodes, 122093568 blocks
6104678 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=0
3726 block groups
32768 blocks per group, 32768 fragments per group
8192 inodes per group
Superblock backups stored on blocks: 
	32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
	4096000, 7962624, 11239424, 20480000, 23887872, 71663616, 78675968, 
	102400000

Writing inode tables: done                            
Creating journal (32768 blocks): done
Writing superblocks and filesystem accounting information: done

This filesystem will be automatically checked every 37 mounts or
180 days, whichever comes first.  Use tune2fs -c or -i to override.

```

After everything was done successfully, it's time to add the raid array + the new partition on the boot, so I did:

**mdadm --detail --scan**

I took my last line for my md2 array containing the UUID and I added it to /etc/mdadm/mdadm.conf

Then:

[b]mkdir /backup
blkid | grep backup[/b]

I took the UUID and I have added the following lines to /etc/fstab
```

# /dev/mapper/vg--fs1-lv--backup
UUID=9b1006b6-7959-418f-8381-d6f7deaae282 /backup         ext3    relatime,acl,errors=remount-ro 0       2

```

Then I had to add a symbolic link because for some reason it wasn't automatically there:
[b]
cd /dev/disk/by-uuid
ln -s 9b1006b6-7959-418f-8381-d6f7deaae282 ../../mapper/vg--fs1-lv--backup
[/b]

So after that I was able to successfully mount all my partitions with

**mount -a**

Now checking:

```
root@fs1:~# **df -h**
Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/vg--fs1-lv--home
                      199G  128G   62G  68% /
varrun                998M  644K  997M   1% /var/run
varlock               998M     0  998M   0% /var/lock
udev                  998M  108K  998M   1% /dev
devshm                998M     0  998M   0% /dev/shm
/dev/md0               99M   25M   69M  27% /boot
/dev/mapper/vg--fs1-lv--tmp
                     1016M   34M  932M   4% /tmp
/dev/mapper/vg--fs1-lv--var
                      8.0G  1.1G  6.5G  14% /var
/dev/mapper/vg--fs1-lv--ldaphome
                      199G   31G  158G  17% /ldaphome
/dev/mapper/vg--fs1-lv--backup
                      463G  199M  439G   1% /backup

```

My raid arrays seemed to be working ok:

```

root@fs1:~# **mdadm --detail /dev/md2**
/dev/md2:
        Version : 00.90.03
  Creation Time : Fri Oct 24 12:34:33 2008
     Raid Level : raid10
     Array Size : 488383936 (465.76 GiB 500.11 GB)
  Used Dev Size : 488383936 (465.76 GiB 500.11 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 2
    Persistence : Superblock is persistent

    Update Time : Fri Oct 24 15:11:00 2008
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

         Layout : near=2, far=1
     Chunk Size : 64K

           UUID : 6237bdce:db890272:0bc4cc31:79b33017 (local to host fs1.mydomain.local)
         Events : 0.6

    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       8       49        1      active sync   /dev/sdd1

root@fs1:~# **mdadm --detail /dev/md1**
/dev/md1:
        Version : 00.90.03
  Creation Time : Fri Aug 15 13:02:57 2008
     Raid Level : raid10
     Array Size : 484367680 (461.93 GiB 495.99 GB)
  Used Dev Size : 484367680 (461.93 GiB 495.99 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 1
    Persistence : Superblock is persistent

    Update Time : Fri Oct 24 15:14:00 2008
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

         Layout : near=2, far=1
     Chunk Size : 64K

           UUID : 8ba38298:d0d49e52:f7ea6dbe:7db6dc24
         Events : 0.12

    Number   Major   Minor   RaidDevice State
       0       8        2        0      active sync   /dev/sda2
       1       8       34        1      active sync   /dev/sdc2

```

Then I run fdisk -l but I've got an error at end:
Disk /dev/md2 doesn't contain a valid partition table

Then I tried to correct that with
```

root@fs1:~# fdisk /dev/sdb1
Device contains neither a valid DOS partition table, nor Sun, SGI or OSF disklabel
Building a new DOS disklabel with disk identifier 0x0859670a.
Changes will remain in memory only, until you decide to write them.
After that, of course, the previous content won't be recoverable.


The number of cylinders for this disk is set to 60800.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)
Warning: invalid flag 0x0000 of partition table 4 will be corrected by w(rite)
Command (m for help): p

Disk /dev/sdb1: 500.1 GB, 500105217024 bytes
255 heads, 63 sectors/track, 60800 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0859670a

     Device Boot      Start         End      Blocks   Id  System

Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.

WARNING: Re-reading the partition table failed with error 22: Invalid argument.
The kernel still uses the old table.
The new table will be used at the next reboot.
Syncing disks.

```

Then I did the same for sdd1 and md2.

Now fdisk is clean and it doesn't give me any more errors:

```

root@fs1:~# fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00066974

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      104391   fd  Linux raid autodetect
/dev/sda2              14       60314   484367782+  fd  Linux raid autodetect
/dev/sda3           60315       60801     3911827+  82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5dc31e7d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001   fd  Linux raid autodetect

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00078211

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1          13      104391   fd  Linux raid autodetect
/dev/sdc2              14       60314   484367782+  fd  Linux raid autodetect
/dev/sdc3           60315       60801     3911827+  82  Linux swap / Solaris

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2870da8c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       60801   488384001   fd  Linux raid autodetect

Disk /dev/md0: 106 MB, 106823680 bytes
2 heads, 4 sectors/track, 26080 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x1dd13404

    Device Boot      Start         End      Blocks   Id  System

Disk /dev/md1: 495.9 GB, 495992504320 bytes
2 heads, 4 sectors/track, 121091920 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x420f65f6

    Device Boot      Start         End      Blocks   Id  System

Disk /dev/md2: 500.1 GB, 500105150464 bytes
2 heads, 4 sectors/track, 122095984 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x52bcff93

    Device Boot      Start         End      Blocks   Id  System

```

After that I thought that everything was successful. The only thing that was weird is that mdadm --detail /dev/md2 was saying that (local to host fs1.mydomain.local) Next to the UUID line and the error that i've got with fdisk before I force a w.

After that I wasn't able to reboot the computer, It would get stuck right after grub, and it wouldn't give any error messages. So I wasn't able to trace anything on the log files as well.

Any ideas of what is going on or how I can trace the problem?

---

