---
title: "Accidentally deleted partition disk in raid5 array, array now degraded"
date: 2013-10-14
forum: Server Platforms
---

### Post by StuartWhelan on 2013-10-14
Hello folks,


A few weeks ago I needed to fdisk an external USB drive. It would appear I have accidentally fdisked one of my md drives.


In addition, my BIOS somehow got reset to system defaults.


I attempted to boot from each drive in turn.


Upon boot I got warned of a degraded array. The system dropped to a diagnostic prompt.


I wanted to power off the system until I had time to deal with it, and because all the system fans were running 100%.


I typed exit, and the system booted. Ubuntu has now started, I have a UI, but the most of my data is missing.


I can not recall how the system was configured, or where the array was mounted.


Can anyone help me reassemble my system?


Here are some outputs:


```

cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=13.04
DISTRIB_CODENAME=raring
DISTRIB_DESCRIPTION="Ubuntu 13.04"

```


```

cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : inactive sdc1[4](S) sde1[3](S) sda1[5](S)
      2926754744 blocks super 1.2
       
unused devices: <none>

```


```

cat /etc/mdadm/mdadm.conf 
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
ARRAY /dev/md/0 metadata=1.2 UUID=0c20f9ba:575a24fe:6dba6a68:e7a99f42 name=ubuntu2:0


# This file was auto-generated on Wed, 30 Nov 2011 21:27:37 +1300

```


```

mdadm -D /dev/md0
mdadm: md device /dev/md0 does not appear to be active.

```

```

mdadm -E /dev/sd[abcde]1
/dev/sda1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 0c20f9ba:575a24fe:6dba6a68:e7a99f42
           Name : ubuntu2:0
  Creation Time : Fri Apr 29 22:42:26 2011
     Raid Level : raid5
   Raid Devices : 4


 Avail Dev Size : 1951172464 (930.39 GiB 999.00 GB)
     Array Size : 2926751232 (2791.17 GiB 2996.99 GB)
  Used Dev Size : 1951167488 (930.39 GiB 999.00 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 6053315c:cd0fbbfd:41f12c0c:49eb7408


    Update Time : Sun Oct 13 16:59:32 2013
       Checksum : 9634b06 - correct
         Events : 73845


         Layout : left-symmetric
     Chunk Size : 512K


   Device Role : Active device 3
   Array State : AAAA ('A' == active, '.' == missing)
/dev/sdc1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 0c20f9ba:575a24fe:6dba6a68:e7a99f42
           Name : ubuntu2:0
  Creation Time : Fri Apr 29 22:42:26 2011
     Raid Level : raid5
   Raid Devices : 4


 Avail Dev Size : 1951168512 (930.39 GiB 999.00 GB)
     Array Size : 2926751232 (2791.17 GiB 2996.99 GB)
  Used Dev Size : 1951167488 (930.39 GiB 999.00 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 6c118c9f:bc155b79:185a0af7:503ce13b


    Update Time : Sun Oct 13 16:59:32 2013
       Checksum : e6a7b96e - correct
         Events : 73845


         Layout : left-symmetric
     Chunk Size : 512K


   Device Role : Active device 0
   Array State : AAAA ('A' == active, '.' == missing)
mdadm: No md superblock detected on /dev/sdd1.
/dev/sde1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 0c20f9ba:575a24fe:6dba6a68:e7a99f42
           Name : ubuntu2:0
  Creation Time : Fri Apr 29 22:42:26 2011
     Raid Level : raid5
   Raid Devices : 4


 Avail Dev Size : 1951168512 (930.39 GiB 999.00 GB)
     Array Size : 2926751232 (2791.17 GiB 2996.99 GB)
  Used Dev Size : 1951167488 (930.39 GiB 999.00 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : e79c656b:72d23108:cf6e2251:59e1e8c7


    Update Time : Sun Oct 13 16:59:32 2013
       Checksum : 2777bb5e - correct
         Events : 73845


         Layout : left-symmetric
     Chunk Size : 512K


   Device Role : Active device 2
   Array State : AAAA ('A' == active, '.' == missing)



```




```

fdisk -l:
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0001b4cc


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63  1951174574   975587256   fd  Linux raid autodetect


Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000d3a9e


   Device Boot      Start         End      Blocks   Id  System
/dev/sdb2      1951172608  1953523711     1175552   82  Linux swap / Solaris


Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000208a1


   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *        2048  1855866879   927932416   83  Linux
/dev/sdd2      1855868926  1953523711    48827393    5  Extended
/dev/sdd5      1855868928  1953523711    48827392   82  Linux swap / Solaris


Disk /dev/sde: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00061f13


   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *        2048  1951172607   975585280   fd  Linux raid autodetect
/dev/sde2      1951172608  1953523711     1175552   82  Linux swap / Solaris


Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002bc41


   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *        2048  1951172607   975585280   fd  Linux raid autodetect
/dev/sdc2      1951172608  1953523711     1175552   82  Linux swap / Solaris



```

---

### Post by SaturnusDJ on 2013-10-14
To fdisk isn't quite a clear verb.

If you formatted the partition/filesystem on the md device, you are in trouble.

If you formatted the partition on a member of the raid array, the fix isn't that hard:

Now, before going along, realize to: Understand the commands before using them!

1. Copy the partition scheme from one of the existing members to the disk you've erased.
A command like this should do the job:
```
sfdisk -d /dev/sda | sfdisk /dev/sdd 
```
If this doesn't work, look at the alternate method from the first link in my signature.

2. Stop all the arrays containing members we need for the array we need to fix.
```
mdadm --stop /dev/md0
```

3. Now start the array degraded.
```

mdadm --assemble /dev/md0 --uuid=0c20f9ba:575a24fe:6dba6a68:e7a99f42

```
If this doesn't work, add the --force and --run flags. This is safe because the event count is in sync.

The array should be running as /dev/md0 now. You should have a backup. If you don't have one, now is a chance because the device is mountable. If you are going to backup now, only backup stuff you can't miss. That's because we want a minimum load on a degraded array.

Note that the following operation isn't dangerous, but the amount of reads/writes as a result sometimes kill disks. That's why you always need backups and need to know the S.M.A.R.T. status of your drives.

4. ```

mdadm --manage /dev/md0 --add /dev/sdd1

```
Resync will start and afterwards everything is back to normal.

---

### Post by StuartWhelan on 2013-10-14
Many thanks for the reply, I appreciate your time and expertise.

I made the mistake in the gnome-disks application, I believe I deleted the partition.

I didn't realise something had gone wrong until the reboot, at which time I sat back and had a good think about what might have happened.

I believe it may be sdb that one I deleted, as it has no partition 0.

I did a sfdisk -d /dev/sdc | sfdisk /dev/sdb

I then tried to stop the array, but got:

```

root@ubuntu:~# mdadm --stop /dev/md0
mdadm: Cannot get exclusive access to /dev/md0:Perhaps a running process, mounted filesystem or active volume group?

```

fuser /dev/md0 and lsof /dev/md0 both return no output.

```

root@ubuntu:~# ps -ef |grep md0
root     23705     2  0 07:21 ?        00:00:00 [md0_raid5]
root     25617 23039  0 07:36 pts/3    00:00:00 grep --color=auto md0

```

I tried to kill and kill -9 23705, but it did not die.

Not sure where to go from here. A --force on the madm stop did not help.



Thanks again,
Stuart.

---

### Post by SaturnusDJ on 2013-10-14
Two quick options:

1. Work from liveCD.

2. Prevent any mdadm startup.
Edit /lib/udev/rules.d/64-md-raid.rules
Comment out the line saying ACTION=="add", RUN+="/sbin/mdadm --incremental $tempnode"
Maybe this is enough (I'm not 100% sure), otherwise also comment out the array definitions in /etc/mdadm/mdadm.conf.
And then run update-initramfs -u.

---

### Post by StuartWhelan on 2013-10-15
I booted off a livecd, and installed mdadm.

I assembled the array using the command below, which came up with 4 devices.
```
[COLOR=#000000][FONT=Ubuntu Mono]mdadm --assemble /dev/md0 --uuid=0c20f9ba:575a24fe:6dba6a68:e7a99f42
```[/FONT][/COLOR]

I attempted to add /dev/sdd1, but it says: /dev/sdd1 not large enough to join array.

I am not certain if sdd1 was ever in the array.

The scary thing now is this:

When I mount /dev/sdd1 I have all my recent files. /var/log has log files up to the 14th of Oct 2013. My bacula backups for the rest of the network are all there.

When I mount /dev/md/0, none of the files are newer than 2011.

How do you think I should proceed?

---

### Post by SaturnusDJ on 2013-10-15
Ok the data array is sd[a,b,c,e]1.

You erased /dev/sdb1.
/dev/sda1 is missing a swap partition, but that might be on purpose.

The array can't come up with 4 drives cause there are only 3. Or something is seriously not right.
What did
```
cat /proc/mdstat

```
say?

It looks like /dev/sdd is a standalone disk.

---

### Post by StuartWhelan on 2013-10-16
Thank you again for your help and expertise.


I have decided to rebuild the system from scratch, it was first built back in 2009, and the ubuntu install has been incrementally upgraded through over the years.


I will disconnect /dev/sdd1 from the motherboard.


I will then rebuild the sever from scratch, using the other drives as a raid 5 array.


Once it is freshly built I will copy the data I want to keep from /dev/sdd1 back onto the array.

Thanks again and kind regards,
Stuart.

---

