---
title: "mdadm RAID5 degraded at boot"
date: 2007-10-25
forum: Server Platforms
---

### Post by StonedSidney on 2007-10-25
OK, this post is quite similar to some others, but does differ in the details. Honest. 

I am running 6.06 Dapper desktop and I have defined 2 raid arrays:
md0= Raid 1 and comprises 2 partitions: /dev/sdb5 & /dev/sdc5
md1= Raid 5 and comprises 3 partitions: /dev/sda5, /dev/sdb6 & /dev/sdb6

When I boot, the raid 5 array (md1) starts up automatically (doen't delay booting) but is always degraded. The array is accessible and works fine, but does not automatically fix itself. These points seem different to the other posts to this forum.

Every time it states that /dev/sda5 has been removed. So I do a  ```
sudo mdadm --manage --verbose /dev/md1 --add /dev/sda5
```
and the array rebuilds perfectly (after a few hours).
```

dmesg | grep md

[   53.112670] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[   53.112676] md: bitmap version 4.39
[   53.115299] md: raid5 personality registered as nr 4
[   53.219683] md: md0 stopped.
[   53.229037] md: bind<sda5>
[   64.180700] ata3: SATA max UDMA/100 cmd 0xFFFFC20000050000 ctl 0x0 bmdma 0x0 irq 233
[   64.180731] ata4: SATA max UDMA/100 cmd 0xFFFFC20000052000 ctl 0x0 bmdma 0x0 irq 233
[   64.180762] ata5: SATA max UDMA/100 cmd 0xFFFFC20000054000 ctl 0x0 bmdma 0x0 irq 233
[   64.180794] ata6: SATA max UDMA/100 cmd 0xFFFFC20000056000 ctl 0x0 bmdma 0x0 irq 233
[   67.004617] md: md1 stopped.
[   67.289683] md: bind<sdc6>
[   67.291904] md: bind<sdb6>
[   67.292582] raid5: allocated 3212kB for md1
[   67.292587] raid5: raid level 5 set md1 active with 2 out of 3 devices, algorithm 2
[   67.292753] md: md0 stopped.
[   67.292759] md: unbind<sda5>
[   67.292777] md: export_rdev(sda5)
[   67.349696] md: bind<sdc5>
[   67.349897] md: bind<sdb5>
[   67.448352] md: raid1 personality registered as nr 3
[   67.450110] raid1: raid set md0 active with 2 out of 2 mirrors
[   68.663313] EXT3 FS on md1, internal journal
[   68.703808] EXT3 FS on md0, internal journal
 
```

The UUID in mdadm.conf matches the output of mdadm --detail /dev/md1:
```
 sudo cat /etc/mdadm/mdadm.conf
DEVICE /dev/sd* /dev/md*
ARRAY /dev/md1 level=raid5 num-devices=3 UUID=111e1ef0:ae1c770b:21ba128f:c59ee166
ARRAY /dev/md0 level=raid1 num-devices=2 UUID=e9952b0e:8217ea9a:a0d43473:1587f669

```
```
 sudo mdadm --detail --verbose /dev/md1
/dev/md1:
        Version : 00.90.03
  Creation Time : Wed May 16 17:02:53 2007
     Raid Level : raid5
     Array Size : 313154816 (298.65 GiB 320.67 GB)
    Device Size : 156577408 (149.32 GiB 160.34 GB)
   Raid Devices : 3
  Total Devices : 3
Preferred Minor : 1
    Persistence : Superblock is persistent

    Update Time : Fri Oct 26 07:44:29 2007
          State : clean
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : 111e1ef0:ae1c770b:21ba128f:c59ee166
         Events : 0.996326

    Number   Major   Minor   RaidDevice State
       0       8        5        0      active sync   /dev/sda5
       1       8       22        1      active sync   /dev/sdb6
       2       8       38        2      active sync   /dev/sdc6

```

Filesystem on both arrays is ext3 (and performance is poor).

Regarding phyical drive connection:
[LIST]
/dev/sda is connected to the 1st mothboard SATA port and has the / and /boot etc. partitions
[/LIST]
[LIST]
/dev/sdb and /dev/sdc are connected to a SATA port extender
[/LIST]
[LIST]
/dev/sdd is also connected to the SATA port extender, but is not part of any array
[/LIST]
Could it be that all SDAx partitions are locked during the boot process and unanavailable to mount? The arrays are mounted by fstab. Note that the Raid1 arrary mounts perfectly, but does not use an SDA partition.... [the sda drive is fully used so I can't easily create a new array for testing]

The very first time the RAID5 arrary broke was after I insterted a USB pen drive. The USB drive caused the drive names to change and again /sda5 got removed so the array went degraded. Could this problem be a hangover from that (and why did that happen anyway?)?

I welcome any suggestions - please let me know if anymore info is needed.

---

### Post by qmerge on 2007-10-29
I had the same problem.
One way to fix it is:
mdadm -S /dev/md3
mdadm -A /dev/md3 /dev/md1 /dev/sdk3 /dev/sdl3 /dev/sdm3 /dev/sdn3

It should reassemble without requiring rebuild
The problem went away when I went to 7.4 (or after a re-image)

Now I get a worse problem (because of using USB drives?)
The UUID's get corrupted when the drives move.
here's my notes:
# Always use partitions, and number each RAID set the same 
# First determine what's what 
mdadm -Q /dev/sd?1
# Try normal Assembly 
 mdadm -A  /dev/md0 /dev/sdb1 /dev/sdj1 /dev/sdh1 /dev/sdi1 /dev/sda1 
# Try forced Assemble 
 mdadm -A --force /dev/md0 /dev/sdb1 /dev/sdj1 /dev/sdh1 /dev/sdi1 /dev/sda1 
# Try creation without check 
 mdadm --create /dev/md0 --assume-clean --level=5 --raid-devices=5  /dev/sdb1 /dev/sdj1 /dev/sdh1 /dev/sdi1  missing 
# the drive should mount 
mount /dev/md0 /backup

---

