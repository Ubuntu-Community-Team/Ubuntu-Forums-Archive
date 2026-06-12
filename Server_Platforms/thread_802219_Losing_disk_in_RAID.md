---
title: "Losing disk in RAID?"
date: 2008-05-21
forum: Server Platforms
---

### Post by quad3d@work on 2008-05-21
I notice this weird problem with 8.04 server. Sometimes after reboot it'll lose one of the disk in RAID5 and hot spare kicks in; I have to "*mdadm /dev/md0 --add /dev/sdX*".


Have PE 2950 with MD1000 15 SAS 300GBs.


** Internal RAID controller; 6 local disks on HW RAID5.**
===============================
01:00.0 RAID bus controller: LSI Logic / Symbios Logic MegaRAID SAS 1078 (rev 04)
 Subsystem: Dell PERC 6/i Integrated RAID Controller
 Flags: bus master, fast devsel, latency 0, IRQ 16
 Memory at fc880000 (64-bit, non-prefetchable) [size=256K]
 I/O ports at ec00 [size=256]
 Memory at fc840000 (64-bit, non-prefetchable) [size=256K]
 Expansion ROM at fc700000 [disabled] [size=32K]
 Capabilities: <access denied>
 
 
** Brick controller. 15 drives; 14 active, 1 spare. Soft RAID5.**
=========
0b:08.0 SCSI storage controller: LSI Logic / Symbios Logic SAS1068 PCI-X Fusion-MPT SAS (rev 01)
 Subsystem: Dell SAS 5/E Adapter Controller
 Flags: bus master, 66MHz, medium devsel, latency 72, IRQ 16
 I/O ports at dc00 [disabled] [size=256]
 Memory at fc5fc000 (64-bit, non-prefetchable) [size=16K]
 Memory at fc5e0000 (64-bit, non-prefetchable) [size=64K]
 Expansion ROM at fc600000 [disabled] [size=1M]
 Capabilities: <access denied>





Here is some outputs...
** root@sydvm01:~# mdadm --misc --detail /dev/md0**
/dev/md0:
        Version : 00.90.03
  Creation Time : Tue May 20 21:10:36 2008
     Raid Level : raid5
     Array Size : 3808592320 (3632.16 GiB 3900.00 GB)
  Used Dev Size : 292968640 (279.40 GiB 300.00 GB)
   Raid Devices : 14
  Total Devices : 14
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Wed May 21 01:34:36 2008
          State : clean
 Active Devices : 14
Working Devices : 14
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : 1184b2fc:1476e7c1:51eca089:628ed995 (local to host sydvm01)
         Events : 0.28

    Number   Major   Minor   RaidDevice State
       0       8       16        0      active sync   /dev/sdb
       1       8       32        1      active sync   /dev/sdc
       2       8       48        2      active sync   /dev/sdd
       3       8       64        3      active sync   /dev/sde
       4       8       80        4      active sync   /dev/sdf
       5       8       96        5      active sync   /dev/sdg
       6       8      112        6      active sync   /dev/sdh
       7       8      128        7      active sync   /dev/sdi
       8       8      144        8      active sync   /dev/sdj
       9       8      160        9      active sync   /dev/sdk
      10       8      176       10      active sync   /dev/sdl
      11       8      192       11      active sync   /dev/sdm
      12       8      240       12      active sync   /dev/sdp
      13       8      224       13      active sync   /dev/sdo
** root@sydvm01:~# mdadm /dev/md0 --add /dev/sdn**
mdadm: added /dev/sdn
** root@sydvm01:~# mdadm --misc --detail /dev/md0**
/dev/md0:
        Version : 00.90.03
  Creation Time : Tue May 20 21:10:36 2008
     Raid Level : raid5
     Array Size : 3808592320 (3632.16 GiB 3900.00 GB)
  Used Dev Size : 292968640 (279.40 GiB 300.00 GB)
   Raid Devices : 14
  Total Devices : 15
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Wed May 21 08:18:20 2008
          State : clean
 Active Devices : 14
Working Devices : 15
 Failed Devices : 0
  Spare Devices : 1

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : 1184b2fc:1476e7c1:51eca089:628ed995 (local to host sydvm01)
         Events : 0.32

    Number   Major   Minor   RaidDevice State
       0       8       16        0      active sync   /dev/sdb
       1       8       32        1      active sync   /dev/sdc
       2       8       48        2      active sync   /dev/sdd
       3       8       64        3      active sync   /dev/sde
       4       8       80        4      active sync   /dev/sdf
       5       8       96        5      active sync   /dev/sdg
       6       8      112        6      active sync   /dev/sdh
       7       8      128        7      active sync   /dev/sdi
       8       8      144        8      active sync   /dev/sdj
       9       8      160        9      active sync   /dev/sdk
      10       8      176       10      active sync   /dev/sdl
      11       8      192       11      active sync   /dev/sdm
      12       8      240       12      active sync   /dev/sdp
      13       8      224       13      active sync   /dev/sdo

      14       8      208        -      spare   /dev/sdn



**root@sydvm01:/etc/mdadm# cat mdadm.conf**
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

# This file was auto-generated on Tue, 20 May 2008 20:52:09 -0500
# by mkconf $Id$


Any suggestions?

---

### Post by finite9 on 2008-05-21
no suggestions, but I get the same thing on CentOS 5.1 using software RAID1.

Reboot "often" loses one of the disks (same disk all the time) and I need to re-add it and it takes forever to resync.

Are you sure your controller is good?

I suspect my controller but have not had chance to really test this.  I also get lock ups where the ONLY solution is to poweroff everything * and then unplug the eSATA cable* to get it to work again.

This is new hardware, 2 eSATA 500GB, 2 new cables and a sil CardBus controller.

I suggest you mail the linux-raid mailing list instead of the ubuntu forums.

---

### Post by quad3d@work on 2008-05-21
This is brand new server, there is no way for me to test this since I don't have another server with same SAS card free for spare testing.

For me this isn't same drive all the time, it randomly loses a drive. Sometimes it boots fine.

Guess I'll just write a script to email me when it has less than 15 drives in that RAID brick. Thanks.

---

### Post by finite9 on 2008-05-22
i think I know why mine fails: spindown on the external eSATA discs.  RAID cant handle spindown.

---

### Post by axel1973 on 2009-03-31
dont know if your case is solved yet. but i wanted to share some experience with you out there who might get in similar trouble.

years n years ago i had some trouble with an HP SCSI Raid. The Raid worked fine for installation. But it fails within 14 Days or so.

The Reason / The Solution: since we bought a brand new HP server back then, we asked HP what the problem is. They told us "the firmware of the used HP HDs are too old and not the same on all drives".

So this is just a lil hint if you got into trouble like that. If possible check all your harddisc if their firmare is up-to-date and that all disks use the same version. this could help make your Hardware-Raid more stable.

---

