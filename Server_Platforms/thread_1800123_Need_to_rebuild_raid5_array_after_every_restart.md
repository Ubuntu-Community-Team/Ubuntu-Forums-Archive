---
title: "Need to rebuild raid5 array after every restart"
date: 2011-07-08
forum: Server Platforms
---

### Post by prasoon612 on 2011-07-08
Hi

I have software raid 5 array, each time I reboot my server, I have to rebuild array again. Rebuilding array takes too long. I am using ubuntu server 10.10.

---

### Post by rubylaser on 2011-07-08
Sounds like you don't have your /etc/mdadm/mdadm.conf file set up correctly.  What's the output of 
```
cat /proc/mdstat
```
and
```
cat /etc/mdadm/mdadm.conf
```

---

### Post by prasoon612 on 2011-07-08
array in rebuilding right now.

$:/etc$ cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid5 sdb1[3] sdc1[1] sdd1[0]
      3906959232 blocks level 5, 64k chunk, algorithm 2 [3/2] [UU_]
      [===========>.........]  recovery = 59.9% (1170647128/1953479616) finish=985.1min speed=13243K/sec
      
unused devices: <none>


$:/etc$ cat mdadm/mdadm.conf
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
ARRAY /dev/md0 level=raid5 num-devices=3 UUID=59b56ff2:ad84926a:49ce1f6e:101c6db6

# This file was auto-generated on Tue, 08 Feb 2011 18:09:33 -0800
# by mkconf $Id$

---

### Post by rubylaser on 2011-07-08
Your mdadm.conf looks okay as long as the UUID matches the metadata on your disks.

```
mdadm -E /dev/sd[bcd]1 | grep UUID
```
```
mdadm --detail /dev/md0 | grep UUID
```

and do you have any messages in the syslog or dmesg?

---

### Post by prasoon612 on 2011-07-08
UUID is also fine,

:~$ sudo mdadm --detail /dev/md0 | grep UUID
     UUID : 59b56ff2:ad84926a:49ce1f6e:101c6db6 

:~$ sudo mdadm -E /dev/sd[bcd]1 | grep UUID
           UUID : 59b56ff2:ad84926a:49ce1f6e:101c6db6 
           UUID : 59b56ff2:ad84926a:49ce1f6e:101c6db6
           UUID : 59b56ff2:ad84926a:49ce1f6e:101c6db6


last few lines of dmesg

[   67.880091] md: md0 still in use.
[  170.039236] md: md0 still in use.
[  400.791069] md/raid:md_d0: device sdc1 operational as raid disk 0
[  400.791429] md/raid:md_d0: allocated 3230kB
[  400.791589] md/raid:md_d0: not enough operational devices (2/3 failed)
[  400.791805] RAID conf printout:
[  400.791807]  --- level:5 rd:3 wd:1
[  400.791810]  disk 0, o:1, dev:sdc1
[  400.792113] md/raid:md_d0: failed to run raid set.
[  400.792181] md: pers->run() failed ...
[  441.904788] md: md_d0 stopped.
[  441.904795] md: unbind<sdc1>
[  441.930702] md: export_rdev(sdc1)
[  455.098539] md: md127 stopped.
[  475.379551] md: bind<sdd1>
[  475.819550] md: bind<sdc1>
[  476.317170] md: bind<sdb1>
[  476.319449] md/raid:md0: device sdc1 operational as raid disk 1
[  476.319452] md/raid:md0: device sdd1 operational as raid disk 0
[  476.319742] md/raid:md0: allocated 3230kB
[  476.319770] md/raid:md0: raid level 5 active with 2 out of 3 devices, algorithm 2
[  476.319859] RAID conf printout:
[  476.319860]  --- level:5 rd:3 wd:2
[  476.319862]  disk 0, o:1, dev:sdd1
[  476.319864]  disk 1, o:1, dev:sdc1
[  476.319885] md0: detected capacity change from 0 to 4000726253568
[  476.319960]  md0:
[  476.320010] RAID conf printout:
[  476.320012]  --- level:5 rd:3 wd:2
[  476.320014]  disk 0, o:1, dev:sdd1
[  476.320015]  disk 1, o:1, dev:sdc1
[  476.320016]  disk 2, o:1, dev:sdb1
[  476.320166] md: recovery of RAID array md0
[  476.320169] md: minimum _guaranteed_  speed: 1000 KB/sec/disk.
[  476.320170] md: using maximum available idle IO bandwidth (but not more than 200000 KB/sec) for recovery.
[  476.320177] md: using 128k window, over a total of 1953479616 blocks.
[  476.647743]  unknown partition table
[  602.036548] EXT4-fs (md0): Couldn't mount because of unsupported optional features (3d00001)
[ 1666.279462] md: md127 stopped.
[ 7932.926851] md: ioctl lock interrupted, reason -4, cmd -2146170606
[14873.220463] usb 2-1.2: USB disconnect, address 4
[14873.220469] usb 2-1.2.1: USB disconnect, address 7
[LEFT]
[/LEFT]

---

### Post by tgalati4 on 2011-07-08
Your last two entries give me the impression that you are using USB drives?

If so, I would not expect reliable software RAID behavior with USB drives.

If not USB drives, then are these "Green" drives?  From your printout, it looks like 2 out of the 3 drives fall out of the RAID at 400 seconds for unknown reasons--perhaps they went to sleep?

---

### Post by prasoon612 on 2011-07-08
Yes, I am using USB drive.

"it looks like 2 out of the 3 drives fall out of the RAID at 400 seconds for unknown reasons-"  -- this happens after I rebooted machine.

---

### Post by itzamecwp on 2011-07-09
I had a similar problem with my ARRAY that would go to pieces after a reboot.

The trick for me was to run 'update-initramfs -k all -u' after setting up mdadm.conf.


All hail Milli for solving that one for me!
[http://ubuntuforums.org/archive/index.php/t-1168360.html](http://ubuntuforums.org/archive/index.php/t-1168360.html)

---

