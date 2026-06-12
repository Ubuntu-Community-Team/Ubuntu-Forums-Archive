---
title: "Software RAID 5 fails with read activity"
date: 2010-09-11
forum: Server Platforms
---

### Post by r00tuk on 2010-09-11
Hello All

I am having a very unusual problem with Ubuntu server 10.04, RAID 5 with LVM.  I tried searching but could not find anything useful.  I am able to reproduce the fault and captured fault details below.  Apologies for the long post:-(

I migrated from OpenSolaris and ZFS last weekend due to uncertainty around the OS project.  The server was stable under Solaris/OpenSolaris and ZFS for several years, so this issue must be driver/configuration related.  

Whilst testing the configuration I noticed (how could I not!) that the RAID array was failing when there was only read activity, but not when there was also write at the same time.  The array degrades with 2 disk failures after about 10 minutes or so.  The server needs to be rebooted to activate the RAID again and this is done by recreating it.  So far I have not noticed any data loss, nor does it go through the "initialize" phase reported in /dev/mdstat.

Relevant Server Hardware Data.
root@druss:~$ uname -a
Linux druss 2.6.32-24-server #42-Ubuntu SMP Fri Aug 20 15:38:55 UTC 2010 x86_64 GNU/Linux

*** IDE CONTROLLER DETAILS ***
$lshw
"...
*-ide:1
             description: IDE interface
             product: MCP51 Serial ATA Controller
             vendor: nVidia Corporation
             physical id: e
             bus info: pci@0000:00:0e.0
             version: a1
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list
             configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3
             resources: irq:23 ioport:9f0(size=8) ioport:bf0(size=4) ioport:970(size=8) ioport:b70(size=4) ioport:d400(size=16) memory:cb007000-cb007fff
        *-ide:2
             description: IDE interface
             product: MCP51 Serial ATA Controller
             vendor: nVidia Corporation
             physical id: f
             bus info: pci@0000:00:0f.0
             version: a1
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master cap_list
             configuration: driver=sata_nv latency=0 maxlatency=1 mingnt=3
             resources: irq:22 ioport:9e0(size=8) ioport:be0(size=4) ioport:960(size=8) ioport:b60(size=4) ioport:e800(size=16) memory:cb004000-cb004fff
..."

*** ACTIVE RAID 5 ARRAY DETAILS ***
$cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid5 sde1[3] sdd1[2] sdb1[1] sda1[0]
      1465148736 blocks level 5, 64k chunk, algorithm 2 [4/4] [UUUU]
      
unused devices: <none>

*** MDADM.CONF DETAILS ***
$ cat /etc/mdadm.conf
DEVICE partitions
CREATE owner=root group=disk mode=0660 auto=yes
MAILADDR root@druss
ARRAY /dev/md0 level=raid5 num-devices=4 metadata=00.90 spares=0 UUID=f7cca4e7:cb549ed9:ee4bd1e2:1fd77dba

Below is what is written to /var/log/messages when the fault starts.

*** START OF FAILURE ***
<BS>Sep 10 15:24:17 druss kernel: [60228.010178] ata5: hard resetting link
Sep 10 15:24:17 druss kernel: [60228.010181] ata5: nv: skipping hardreset on occupied port
Sep 10 15:24:17 druss kernel: [60228.010730] ata6: hard resetting link
Sep 10 15:24:17 druss kernel: [60228.010733] ata6: nv: skipping hardreset on occupied port
Sep 10 15:24:18 druss kernel: [60228.500052] ata5: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Sep 10 15:24:18 druss kernel: [60228.500214] ata6: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Sep 10 15:24:23 druss kernel: [60233.520034] ata6.00: qc timeout (cmd 0x27)
Sep 10 15:24:23 druss kernel: [60233.520041] ata6.00: failed to read native max address (err_mask=0x4)
Sep 10 15:24:23 druss kernel: [60233.520074] ata6: hard resetting link
Sep 10 15:24:23 druss kernel: [60233.520078] ata6: nv: skipping hardreset on occupied port
Sep 10 15:24:23 druss kernel: [60233.520098] ata5.00: qc timeout (cmd 0x27)
Sep 10 15:24:23 druss kernel: [60233.520105] ata5.00: failed to read native max address (err_mask=0x4)
Sep 10 15:24:23 druss kernel: [60233.520129] ata5: hard resetting link
Sep 10 15:24:23 druss kernel: [60233.520132] ata5: nv: skipping hardreset on occupied port
Sep 10 15:24:23 druss kernel: [60234.010051] ata6: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Sep 10 15:24:23 druss kernel: [60234.010069] ata5: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Sep 10 15:24:33 druss kernel: [60244.030041] ata5.00: qc timeout (cmd 0x27)
Sep 10 15:24:33 druss kernel: [60244.030050] ata5.00: failed to read native max address (err_mask=0x4)
Sep 10 15:24:33 druss kernel: [60244.030080] ata5: limiting SATA link speed to 1.5 Gbps
Sep 10 15:24:33 druss kernel: [60244.030091] ata5: hard resetting link
Sep 10 15:24:33 druss kernel: [60244.030094] ata5: nv: skipping hardreset on occupied port
Sep 10 15:24:33 druss kernel: [60244.031280] ata6.00: qc timeout (cmd 0x27)
Sep 10 15:24:33 druss kernel: [60244.031287] ata6.00: failed to read native max address (err_mask=0x4)
Sep 10 15:24:33 druss kernel: [60244.031307] ata6: limiting SATA link speed to 1.5 Gbps
Sep 10 15:24:33 druss kernel: [60244.031315] ata6: hard resetting link
Sep 10 15:24:33 druss kernel: [60244.031317] ata6: nv: skipping hardreset on occupied port
Sep 10 15:24:34 druss kernel: [60244.520082] ata5: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Sep 10 15:24:34 druss kernel: [60244.520196] ata6: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
Sep 10 15:24:44 druss kernel: [60254.540038] ata5.00: qc timeout (cmd 0x27)
Sep 10 15:24:44 druss kernel: [60254.540047] ata5.00: failed to read native max address (err_mask=0x4)
Sep 10 15:24:44 druss kernel: [60254.540071] ata5.00: disabled
Sep 10 15:24:44 druss kernel: [60254.540082] ata5.00: device reported invalid CHS sector 0
Sep 10 15:24:44 druss kernel: [60254.540087] ata5.00: device reported invalid CHS sector 0
Sep 10 15:24:44 druss kernel: [60254.540091] ata5.00: device reported invalid CHS sector 0
Sep 10 15:24:44 druss kernel: [60254.540109] ata5: hard resetting link
Sep 10 15:24:44 druss kernel: [60254.540135] ata6.00: qc timeout (cmd 0x27)
Sep 10 15:24:44 druss kernel: [60254.540142] ata6.00: failed to read native max address (err_mask=0x4)
Sep 10 15:24:44 druss kernel: [60254.540159] ata6.00: disabled
Sep 10 15:24:44 druss kernel: [60254.540166] ata6.00: device reported invalid CHS sector 0
Sep 10 15:24:44 druss kernel: [60254.540170] ata6.00: device reported invalid CHS sector 0
Sep 10 15:24:44 druss kernel: [60254.540173] ata6.00: device reported invalid CHS sector 0
Sep 10 15:24:44 druss kernel: [60254.540176] ata6.00: device reported invalid CHS sector 0
Sep 10 15:24:44 druss kernel: [60254.540180] ata6.00: device reported invalid CHS sector 0
Sep 10 15:24:44 druss kernel: [60254.540194] ata6: hard resetting link
Sep 10 15:24:45 druss kernel: [60255.450054] ata6: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Sep 10 15:24:45 druss kernel: [60255.450087] ata6: EH complete
Sep 10 15:24:45 druss kernel: [60255.450121] sd 5:0:0:0: [sde] Unhandled error code
Sep 10 15:24:45 druss kernel: [60255.450127] sd 5:0:0:0: [sde] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Sep 10 15:24:45 druss kernel: [60255.450134] sd 5:0:0:0: [sde] CDB: Read(10): 28 00 12 7e
Sep 10 15:24:45 druss kernel: [60255.450145] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
Sep 10 15:24:45 druss kernel: [60255.450155]  4a 80 00 00 80 00
Sep 10 15:24:45 druss kernel: [60255.450172] ata5: EH complete
Sep 10 15:24:45 druss kernel: [60255.450227] sd 5:0:0:0: [sde] Unhandled error code
Sep 10 15:24:45 druss kernel: [60255.450231] sd 5:0:0:0: [sde] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Sep 10 15:24:45 druss kernel: [60255.450236] sd 5:0:0:0: [sde] CDB: Read(10): 28 00 12 7e 49 80 00 00 80 00
Sep 10 15:24:45 druss kernel: [60255.450278] sd 5:0:0:0: [sde] Unhandled error code
Sep 10 15:24:45 druss kernel: [60255.450281] sd 5:0:0:0: [sde] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Sep 10 15:24:45 druss kernel: [60255.450286] sd 5:0:0:0: [sde] CDB: Read(10): 28 00 12 7e 49 00 00 00 80 00
Sep 10 15:24:45 druss kernel: [60255.450324] sd 5:0:0:0: [sde] Unhandled error code
Sep 10 15:24:45 druss kernel: [60255.450327] sd 5:0:0:0: [sde] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Sep 10 15:24:45 druss kernel: [60255.450332] sd 5:0:0:0: [sde] CDB: Read(10): 28 00 12 7e 48 80 00 00 80 00
Sep 10 15:24:45 druss kernel: [60255.450371] sd 5:0:0:0: [sde] Unhandled error code
Sep 10 15:24:45 druss kernel: [60255.450374] sd 5:0:0:0: [sde] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Sep 10 15:24:45 druss kernel: [60255.450379] sd 5:0:0:0: [sde] CDB: Read(10): 28 00 12 7e 47 80 00 00 80 00
Sep 10 15:24:45 druss kernel: [60255.450421] sd 4:0:0:0: [sdd] Unhandled error code
Sep 10 15:24:45 druss kernel: [60255.450424] sd 4:0:0:0: [sdd] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Sep 10 15:24:45 druss kernel: [60255.450429] sd 4:0:0:0: [sdd] CDB: Read(10): 28 00 12 7e 49 b0 00 00 d0 00
Sep 10 15:24:45 druss kernel: [60255.450515] sd 4:0:0:0: [sdd] Unhandled error code
Sep 10 15:24:45 druss kernel: [60255.450524] sd 4:0:0:0: [sdd] Unhandled error code
Sep 10 15:24:45 druss kernel: [60255.450532] sd 4:0:0:0: [sdd] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Sep 10 15:24:45 druss kernel: [60255.450545] sd 4:0:0:0: [sdd] CDB: Read(10): 28 00 12 7e 4a 80 00 00 80 00
Sep 10 15:24:45 druss kernel: [60255.450580] sd 4:0:0:0: [sdd] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Sep 10 15:24:45 druss kernel: [60255.450587] sd 4:0:0:0: [sdd] CDB: Read(10): 28 00 12 7e 49 00 00 00 b0 00
Sep 10 15:24:45 druss kernel: [60255.450610] sd 4:0:0:0: [sdd] Unhandled error code
Sep 10 15:24:45 druss kernel: [60255.450612] sd 4:0:0:0: [sdd] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Sep 10 15:24:45 druss kernel: [60255.450616] sd 4:0:0:0: [sdd] CDB: Read(10): 28 00 12 7e 47 b0 00 00 d0 00
Sep 10 15:24:45 druss kernel: [60255.451122] sd 4:0:0:0: [sdd] Unhandled error code
Sep 10 15:24:45 druss kernel: [60255.451126] sd 4:0:0:0: [sdd] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Sep 10 15:24:45 druss kernel: [60255.451131] sd 4:0:0:0: [sdd] CDB: Read(10): 28 00 12 7e 49 00 00 00 80 00
Sep 10 15:24:45 druss kernel: [60255.451633] sd 4:0:0:0: [sdd] Unhandled error code
Sep 10 15:24:45 druss kernel: [60255.451636] sd 4:0:0:0: [sdd] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Sep 10 15:24:45 druss kernel: [60255.451641] sd 4:0:0:0: [sdd] CDB: Read(10): 28 00 12 7e 47 80 00 00 48 00
Sep 10 15:24:45 druss kernel: [60255.460534] sd 4:0:0:0: [sdd] Unhandled error code
Sep 10 15:24:45 druss kernel: [60255.460538] sd 4:0:0:0: [sdd] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Sep 10 15:24:45 druss kernel: [60255.460544] sd 4:0:0:0: [sdd] CDB: Read(10): 28 00 12 7e 47 c8 00 00 38 00
Sep 10 15:24:45 druss kernel: [60255.460967] raid5:md0: read error not correctable (sector 310263752 on sdd1).
Sep 10 15:24:45 druss kernel: [60255.460972] raid5:md0: read error not correctable (sector 310263760 on sdd1).
Sep 10 15:24:45 druss kernel: [60255.460977] raid5:md0: read error not correctable (sector 310263768 on sdd1).
Sep 10 15:24:45 druss kernel: [60255.460982] raid5:md0: read error not correctable (sector 310263776 on sdd1).
Sep 10 15:24:45 druss kernel: [60255.460987] raid5:md0: read error not correctable (sector 310263784 on sdd1).
Sep 10 15:24:45 druss kernel: [60255.460991] raid5:md0: read error not correctable (sector 310263792 on sdd1).
Sep 10 15:24:45 druss kernel: [60255.460996] raid5:md0: read error not correctable (sector 310263800 on sdd1).
Sep 10 15:24:45 druss kernel: [60255.461007] sd 5:0:0:0: [sde] Unhandled error code
Sep 10 15:24:45 druss kernel: [60255.461010] sd 5:0:0:0: [sde] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK
Sep 10 15:24:45 druss kernel: [60255.461016] sd 5:0:0:0: [sde] CDB: Read(10): 28 00 12 7e 48 00 00 00 80 00
Sep 10 15:24:45 druss kernel: [60255.461452] raid5:md0: read error not correctable (sector 310263808 on sde1).
Sep 10 15:24:45 druss kernel: [60255.461457] raid5:md0: read error not correctable (sector 310263816 on sde1).
Sep 10 15:24:45 druss kernel: [60255.461462] raid5:md0: read error not correctable (sector 310263824 on sde1).
Sep 10 15:24:45 druss kernel: [60255.510014] RAID5 conf printout:
Sep 10 15:24:45 druss kernel: [60255.510018]  --- rd:4 wd:2
Sep 10 15:24:45 druss kernel: [60255.510022]  disk 0, o:1, dev:sda1
Sep 10 15:24:45 druss kernel: [60255.510025]  disk 1, o:1, dev:sdb1
Sep 10 15:24:45 druss kernel: [60255.510029]  disk 2, o:0, dev:sdd1
Sep 10 15:24:45 druss kernel: [60255.510032]  disk 3, o:0, dev:sde1
Sep 10 15:24:45 druss kernel: [60255.540016] RAID5 conf printout:
Sep 10 15:24:45 druss kernel: [60255.540020]  --- rd:4 wd:2
Sep 10 15:24:45 druss kernel: [60255.540023]  disk 0, o:1, dev:sda1
Sep 10 15:24:45 druss kernel: [60255.540026]  disk 1, o:1, dev:sdb1
Sep 10 15:24:45 druss kernel: [60255.540029]  disk 3, o:0, dev:sde1
Sep 10 15:24:45 druss kernel: [60255.540043] RAID5 conf printout:
Sep 10 15:24:45 druss kernel: [60255.540047]  --- rd:4 wd:2
Sep 10 15:24:45 druss kernel: [60255.540050]  disk 0, o:1, dev:sda1
Sep 10 15:24:45 druss kernel: [60255.540053]  disk 1, o:1, dev:sdb1
Sep 10 15:24:45 druss kernel: [60255.540056]  disk 3, o:0, dev:sde1
Sep 10 15:24:45 druss kernel: [60255.580015] RAID5 conf printout:
Sep 10 15:24:45 druss kernel: [60255.580019]  --- rd:4 wd:2
Sep 10 15:24:45 druss kernel: [60255.580023]  disk 0, o:1, dev:sda1
Sep 10 15:24:45 druss kernel: [60255.580026]  disk 1, o:1, dev:sdb1
Sep 10 15:25:41 druss kernel: [60312.034533] __ratelimit: 13 callbacks suppressed
Sep 10 15:25:41 druss kernel: [60312.034977] lost page write due to I/O error on dm-0

*** /PROC/MDSTAT DETAILS STRAIGHT AFTER THE FAULT.  THE SERVER IS shutdown -r now AT THIS POINT ***
cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid5 sde1[3] sdd1[2] sdb1[4](F) sda1[5](F)
      1465148736 blocks level 5, 64k chunk, algorithm 2 [4/2] [__UU]
      
unused devices: <none>
 
*** FOLLOWING STEPS COMPLETED WHEN SERVER REBOOTS ***
root@druss:~$ mdadm --create --verbose /dev/md0 --level=5 --raid-devices=4 --assume-clean /dev/sd[abde]1
mdadm: metadata format 00.90 unknown, ignored.
mdadm: layout defaults to left-symmetric
mdadm: chunk size defaults to 64K
mdadm: /dev/sda1 appears to be part of a raid array:
    level=raid5 devices=4 ctime=Fri Sep 10 16:00:35 2010
mdadm: /dev/sdb1 appears to be part of a raid array:
    level=raid5 devices=4 ctime=Fri Sep 10 16:00:35 2010
mdadm: /dev/sdd1 appears to be part of a raid array:
    level=raid5 devices=4 ctime=Fri Sep 10 16:00:35 2010
mdadm: /dev/sde1 appears to be part of a raid array:
    level=raid5 devices=4 ctime=Fri Sep 10 16:00:35 2010
mdadm: size set to 488382912K
Continue creating array? y
mdadm: array /dev/md0 started.
root@druss:~$ mount /dev/vg
vg0/         vga_arbiter  
root@druss:~$ mount /dev/vg0/lvol0 /data
root@druss:~$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : active raid5 sde1[3] sdd1[2] sdb1[1] sda1[0]
      1465148736 blocks level 5, 64k chunk, algorithm 2 [4/4] [UUUU]
      
unused devices: <none>

root@druss:~$ fsck -f /dev/vg0/lvol0 
fsck from util-linux-ng 2.17.2
e2fsck 1.41.11 (14-Mar-2010)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
/dev/mapper/vg0-lvol0: 39748/67108864 files (3.5% non-contiguous), 61228208/268435456 blocks

Any help are advice is going to be appreciated!  

Thanks

r00tuk

---

### Post by r00tuk on 2010-09-13
Resolved by upgrading to Maverick Meerkat.  I would love to know what the bug/configuration error is that caused this severe defect. :S

I really hope that whatever was in Lucid does not EVER make it into Maverick because then it will be the start of a sh1tty week. :(

---

### Post by fjgaude on 2010-09-13
I've been using Lucid since its Beta, over six months ago, and **mdadm** raid5 without issue. I don't use LVM though.

---

### Post by r00tuk on 2010-09-26
> **fjgaude said:**
> I've been using Lucid since its Beta, over six months ago, and **mdadm** raid5 without issue. I don't use LVM though.

I did a straight upgrade (do-release-upgrade -d) to Maverick without changing any Lucid configurations.  After successfully completing the same tests as in Lucid, did I create the LVM volumes.

No issues with the EXT4 filesystem, RAID or LVM since.

---

