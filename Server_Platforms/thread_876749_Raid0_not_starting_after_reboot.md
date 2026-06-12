---
title: "Raid0 not starting after reboot"
date: 2008-08-01
forum: Server Platforms
---

### Post by mjo_se on 2008-08-01
Hi.

I month ago I created a raid0 of two partitions. The command I used was
> root@rt:~# mdadm -Cv /dev/md1 -l0 -n2 -c128 /dev/sde4 /dev/sdf2
However, I did not save the configuration into /etc/mdadm/mdadm.conf and I think this is the reason the array does not start after my reboot.

Some info:
> 
root@rt:~# fdisk -l /dev/sdf

Disk /dev/sdf: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4a44301f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1        2980    23936818+  83  Linux
/dev/sdf2            2981       24321   171421582+  83  Linux

root@rt:~# fdisk -l /dev/sde

Disk /dev/sde: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x23e923e9

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *           1          62      497983+  83  Linux
/dev/sde2              63         548     3903795   82  Linux swap / Solaris
/dev/sde3             549        2980    19535040   83  Linux
/dev/sde4            2981       24321   171421582+  83  Linux

root@rt:~# mdadm --examine /dev/sde4
mdadm: No md superblock detected on /dev/sde4.

root@rt:~# mdadm --examine /dev/sdf2
/dev/sdf2:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : cf2c6121:10be48da:d7c001fd:1f6c6f91 (local to host rt)
  Creation Time : Sun Jul  6 20:59:08 2008
     Raid Level : raid0
  Used Dev Size : 0
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 1

    Update Time : Sun Jul  6 20:59:08 2008
          State : active
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 112697fa - correct
         Events : 0.1

     Chunk Size : 128K

      Number   Major   Minor   RaidDevice State
this     1       8       82        1      active sync   /dev/sdf2

   0     0       8       68        0      active sync
   1     1       8       82        1      active sync   /dev/sdf2

I am a bit worried by the output of examination of sde4, but I am not sure what it means.

I do not have any essential data on this array that has not been backed up (it is a raid0 after all), but I would prefer to restart the array instead of restoring things from a backup.

Any ideas on how I should proceed?

---

### Post by siDDis on 2008-08-01
Maybe this thread can help you

[http://ubuntuforums.org/showthread.php?t=854528](http://ubuntuforums.org/showthread.php?t=854528)

---

### Post by mjo_se on 2008-08-01
Thanks a lot for the reply siDDis 

I tried the solution described in the thread, but got this:
> 
root@rt:~#  mdadm --assemble --run --force --verbose /dev/md1 /dev/sde4 /dev/sdf2
mdadm: looking for devices for /dev/md1
mdadm: no recogniseable superblock on /dev/sde4
mdadm: /dev/sde4 has no superblock - assembly aborted

Looks like the missing superblock on sde4 is a problem.
I also tried to recreate the array:
> 
root@rt:~# mdadm -Cv /dev/md1 -l0 -n2 -c128 --verbose /dev/sde4 /dev/sdf2
mdadm: /dev/sde4 is too small: 0K
mdadm: /dev/sdf2 appears to be part of a raid array:
    level=raid0 devices=2 ctime=Sun Jul  6 20:59:08 2008
mdadm: create aborted


---

### Post by mjo_se on 2008-08-01
ok, there is definitely something wrong with sde4:
> 
root@rt:~# dd if=/dev/sde4 of=/mnt/storage/sde4_backup count=40
0+0 records in
0+0 records out
0 bytes (0 B) copied, 2.2877e-05 s, 0.0 kB/s


Other partitions on this disk are fine. I have / and swap here so I would have noticed :-)

---

### Post by mjo_se on 2008-08-01
My guess is that the kernel read the partition table wrong or something. Anyway, I rebooted and now the array works like a charm.

---

