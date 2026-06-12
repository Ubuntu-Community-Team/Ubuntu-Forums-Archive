---
title: "Can't mount mdadm RAID array! File system corruption?"
date: 2015-03-08
forum: Server Platforms
---

### Post by mouse4 on 2015-03-08
A couple day ago, my raid device, /dev/md0, stopped being mounted correctly. As far as I can tell, all the hard drives are fine. I'm not quite sure what the problem was, but I was able to reassemble it with:
```
mdadm --assemble --scan
```
The array was assembled correctly and I was able to mount it and read my data, woo! After looking through my files for a couple minutes, the mount randomly disappeared. The server was completely fine, the array was still running, but it was unmounted. I noticed the array had started syncing. I'm not sure why, but I let it run anyway. Since then, all my attempts to re-mount the array have failed.

**Configuration:**

Here's the definition of the array in /etc/mdadm/mdadm.conf:
```
ARRAY /dev/md0 UUID=842d50ab:3df297d8:64254cbe:abebaaa2
```

Relevant line in fstab:
```
/dev/md0 /media/mediamonkey ext4 defaults 0 0
```

**Assembling the array:**

When I assemble the array (verbose logging turned on):
```
> mdadm --assemble /dev/md0 --verbosemdadm: looking for devices for /dev/md0
mdadm: no RAID superblock on /dev/sdf
mdadm: cannot open device /dev/sr0: No medium found
mdadm: no RAID superblock on /dev/dm-1
mdadm: no RAID superblock on /dev/dm-0
mdadm: no RAID superblock on /dev/sde
mdadm: no RAID superblock on /dev/sdd
mdadm: no RAID superblock on /dev/sdc
mdadm: no RAID superblock on /dev/sdb
mdadm: no RAID superblock on /dev/sda5
mdadm: no RAID superblock on /dev/sda2
mdadm: no RAID superblock on /dev/sda1
mdadm: no RAID superblock on /dev/sda
mdadm: /dev/sdf1 is identified as a member of /dev/md0, slot 4.
mdadm: /dev/sde1 is identified as a member of /dev/md0, slot 3.
mdadm: /dev/sdd1 is identified as a member of /dev/md0, slot 2.
mdadm: /dev/sdc1 is identified as a member of /dev/md0, slot 1.
mdadm: /dev/sdb1 is identified as a member of /dev/md0, slot 0.
mdadm: added /dev/sdc1 to /dev/md0 as 1
mdadm: added /dev/sdd1 to /dev/md0 as 2
mdadm: added /dev/sde1 to /dev/md0 as 3
mdadm: added /dev/sdf1 to /dev/md0 as 4
mdadm: added /dev/sdb1 to /dev/md0 as 0
mdadm: /dev/md0 has been started with 5 drives.
```
Is it unusual/alarming that mdadm is telling me it can't find any RAID superblocks?

This is what the assembled array looks like:
```
/dev/md0:
        Version : 0.90
  Creation Time : Thu Jul  1 17:34:00 2010
     Raid Level : raid5
     Array Size : 5860548352 (5589.05 GiB 6001.20 GB)
  Used Dev Size : 1465137088 (1397.26 GiB 1500.30 GB)
   Raid Devices : 5
  Total Devices : 5
Preferred Minor : 0
    Persistence : Superblock is persistent


    Update Time : Sun Mar  8 00:46:06 2015
          State : clean
 Active Devices : 5
Working Devices : 5
 Failed Devices : 0
  Spare Devices : 0


         Layout : left-symmetric
     Chunk Size : 64K


           UUID : 842d50ab:3df297d8:64254cbe:abebaaa2
         Events : 0.133893


    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       8       33        1      active sync   /dev/sdc1
       2       8       49        2      active sync   /dev/sdd1
       3       8       65        3      active sync   /dev/sde1
       4       8       81        4      active sync   /dev/sdf1
```

...dmesg output after assembling:
```
[ 6110.241565] md: md0 stopped.
[ 6110.242853] md: bind<sdc1>
[ 6110.243059] md: bind<sdd1>
[ 6110.243260] md: bind<sde1>
[ 6110.243401] md: bind<sdf1>
[ 6110.243615] md: bind<sdb1>
[ 6110.267849] md/raid:md0: device sdb1 operational as raid disk 0
[ 6110.267852] md/raid:md0: device sdf1 operational as raid disk 4
[ 6110.267853] md/raid:md0: device sde1 operational as raid disk 3
[ 6110.267854] md/raid:md0: device sdd1 operational as raid disk 2
[ 6110.267856] md/raid:md0: device sdc1 operational as raid disk 1
[ 6110.268185] md/raid:md0: allocated 5394kB
[ 6110.268211] md/raid:md0: raid level 5 active with 5 out of 5 devices, algorithm 2
[ 6110.268213] RAID conf printout:
[ 6110.268214]  --- level:5 rd:5 wd:5
[ 6110.268216]  disk 0, o:1, dev:sdb1
[ 6110.268218]  disk 1, o:1, dev:sdc1
[ 6110.268219]  disk 2, o:1, dev:sdd1
[ 6110.268220]  disk 3, o:1, dev:sde1
[ 6110.268221]  disk 4, o:1, dev:sdf1
[ 6110.268240] md0: detected capacity change from 0 to 6001201512448
[ 6110.268793]  md0: unknown partition table
```

and... for good measure:
```
> cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]md0 : active raid5 sdb1[0] sdf1[4] sde1[3] sdd1[2] sdc1[1]
      5860548352 blocks level 5, 64k chunk, algorithm 2 [5/5] [UUUUU]


unused devices: <none>
```

**Attempting to mount the array:**

And finally, here's the mount command:
```
> mount -a
mount: wrong fs type, bad option, bad superblock on /dev/md0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```
...which comes with these nasty logs in dmesg:
```
[ 6212.077338] EXT4-fs (md0): ext4_check_descriptors: Checksum for group 0 failed (30771!=57397)
[ 6212.077342] EXT4-fs (md0): group descriptors corrupted!
```
[B]
Other possibly useful logs:
[/B]fdisk output (only with drives in the array. I delete the irrelevant output)
```
> fdisk -l

Disk /dev/sdb: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00097ecc


   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048  2930276351  1465137152   fd  Linux raid autodetect


Disk /dev/sdc: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0009a176


   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048  2930276351  1465137152   fd  Linux raid autodetect


Disk /dev/sdd: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0005aacb


   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1            2048  2930276351  1465137152   fd  Linux raid autodetect


Disk /dev/sde: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0009a176


   Device Boot      Start         End      Blocks   Id  System
/dev/sde1            2048  2930276351  1465137152   fd  Linux raid autodetect


Disk /dev/sdf: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x97d873ba


   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1            2048  2930276351  1465137152   fd  Linux raid autodetect


Disk /dev/md0: 6001.2 GB, 6001201512448 bytes
2 heads, 4 sectors/track, 1465137088 cylinders, total 11721096704 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 65536 bytes / 262144 bytes
Disk identifier: 0x00000000


Disk /dev/md0 doesn't contain a valid partition table
```

------------------------------------------------------------------------------------------------------------------------------------------------------

Any help would be much appreciated! At this point, I'm very worried all my data is lost (I unwisely did not make backups... as you can see the array was made in 2010, when I was just a kid and I didn't bother setting up backups many year later :( ).

---

### Post by MAFoElffen on 2015-03-08
If it is data you really cannot do without, if you don't have backups of it... Image the disks to get a fall-back point, so you can try to recover it... and if one technique fails, you can still try something wlse...

The errors look to me as if the the raid was syncing or in the middle of a write, when the system had an unplanned system shutdown (like a power failuer?) What it looks like now, is that the RAID is up, but the superblock in the filesystem are still out-there. That is the susperblock it is referring to. There are backups in various locations. You just need to find and restore them.

Check for backup superblocks, replace the md0 with your partition name
```

$ sudo mke2fs -n /dev/md0

```
The "-n" option causes mke2fs to not actually create a filesystem, but rather it will display what it would do if it were to create a filesystem. Do it this way is be used to determine the location of the backup superblocks for the filesystem, so long as the mke2fs parameters that were passed when the filesystem was originally created, are used again. (With the -n option added, so that is doesn't create a new filesystem over the old one in the RAID container.) You should get output similar to:
[code[
Superblock backups stored on blocks:
32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208
[/code]

Restore the superblock from the backup, again replacing the md0 with your partition name, and block_number with the first backup superblock in the specific output it returned with the above command
```

# sudo e2fsck -b block_number /dev/md0

```
This may take a while to finish. Do not interupt it // wait for it to finish (returns to the prompt.) Now reboot, and your superblock should be fixed. If it’s not, repeat the steps, but restore a different backup superblock

---

### Post by darkod on 2015-03-08
Becore messing with the superblocks did you try the simple fsck? I didn't see it in your post. You have to run it on unmounted array but it doesn't mount right now anyway.

Try something like:
sudo fsck /dev/md0

---

### Post by mouse4 on 2015-03-08
Running fsck /dev/md0 exposes endless errors, starting with "one or more block group descriptor checksums are invalid". :( I'm afraid to allow fsck to fix anything. Would it be safe to run?

Also, going to make backup images of the disks today and try using a backup superblock!

---

