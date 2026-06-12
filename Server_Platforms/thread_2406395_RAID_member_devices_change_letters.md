---
title: "RAID member devices change letters"
date: 2018-11-20
forum: Server Platforms
---

### Post by clarknova on 2018-11-20
Ubuntu Server 16.04

I have a two-member RAID0 device that becomes inaccessible some time after boot. It appears the member drives both stop responding for about two seconds and then change their device lettering and become lost by mdadm. Both of the member devices are in an external enclosure and connected to the server by USB-3.

Things I'd like to know:

1. Why are the device letters changing? Is this because the drives are busy, or is the enclosure or some other component being flaky?
3. Can the devices be managed in a way that a 2-second timeout won't cause this problem?
4. Can the md0 device be managed in a way to make it resilient to a change like this?
5. Do I need to consider replacing the drive enclosure or cable?
6. What is the best way to deal with this remotely? I have found that a reboot will sometimes resolve this temporarily, and will sometimes result in an unresponsive server that has to be power-cycled.

Some background detail:

grep unifi /etc/fstab

```

UUID=2c5b6825-3b76-4fb6-bfa4-d8a533c7734d       /unifi  xfs     noatime,nodev,noexec,logdev=/dev/nvme0n1p2      0       0

```

blkid

```

blkid
/dev/nvme0n1p1: LABEL="ROOT" UUID="0265d652-3271-454e-a615-735969e4d8da" TYPE="ext4" PARTLABEL="ROOT" PARTUUID="7f77e7e0-17e1-4192-b1e3-f097f5e722b9"
/dev/nvme0n1p2: LOGUUID="2c5b6825-3b76-4fb6-bfa4-d8a533c7734d" TYPE="xfs_external_log" PARTLABEL="JOURNAL" PARTUUID="57be3812-87f1-49b8-ae4c-16f899d01c3c"
/dev/nvme0n1p3: UUID="29a54ab1-32c1-40db-9196-13c223b7150f" TYPE="swap" PARTLABEL="SWAP" PARTUUID="37ab550f-6242-45eb-ac3d-3c1519340555"
/dev/nvme0n1p4: UUID="CDD5-5655" TYPE="vfat" PARTLABEL="EFI" PARTUUID="35a960a5-317c-4488-bb2d-70914d4f0256"
/dev/sdc: UUID="33d48f90-1c58-12ad-0eb0-240f7a054b2f" UUID_SUB="a9a3925d-c3c7-c296-fb35-19c3a6d2365b" LABEL="wisemen-nvr:0" TYPE="linux_raid_member"
/dev/sdd: UUID="33d48f90-1c58-12ad-0eb0-240f7a054b2f" UUID_SUB="874fd9ca-9953-f7d3-355f-f24b61bf6790" LABEL="wisemen-nvr:0" TYPE="linux_raid_member"
/dev/nvme0n1: PTUUID="a1cf6f96-03db-4698-870b-6094a6196506" PTTYPE="gpt"

```

cat /proc/mdstat

```

Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid0 sdb[1] sda[0]
      7813774336 blocks super 1.2 512k chunks

unused devices: <none>

```

mdadm -D /dev/md0

```

/dev/md0:
        Version : 1.2
  Creation Time : Thu Apr 20 11:32:48 2017
     Raid Level : raid0
     Array Size : 7813774336 (7451.80 GiB 8001.30 GB)
   Raid Devices : 2
  Total Devices : 2
    Persistence : Superblock is persistent

    Update Time : Thu Apr 20 11:32:48 2017
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

     Chunk Size : 512K

    Number   Major   Minor   RaidDevice State
       0       8        0        0      active sync
       1       8       16        1      active sync


```

dmesg | grep sda

```

[    3.706073] sd 1:0:0:0: [sda] Very big device. Trying to use READ CAPACITY(16).
[    3.706205] sd 1:0:0:0: [sda] 7814037168 512-byte logical blocks: (4.00 TB/3.64 TiB)
[    3.706208] sd 1:0:0:0: [sda] 4096-byte physical blocks
[    3.706402] sd 1:0:0:0: [sda] Write Protect is off
[    3.706406] sd 1:0:0:0: [sda] Mode Sense: 67 00 10 08
[    3.706652] sd 1:0:0:0: [sda] No Caching mode page found
[    3.709558] sd 1:0:0:0: [sda] Assuming drive cache: write through
[   10.777397] sd 1:0:0:0: [sda] Very big device. Trying to use READ CAPACITY(16).
[   17.813038] sd 1:0:0:0: [sda] Very big device. Trying to use READ CAPACITY(16).
[   17.843650] sd 1:0:0:0: [sda] Attached SCSI disk
[   18.137391] md: bind<sda>
[   18.142358] md: zone0=[sda/sdb]
[277726.497508] scsi 1:0:0:0: [sda] killing request
[277726.497580] scsi 1:0:0:0: [sda] killing request
[277726.497604] scsi 1:0:0:0: [sda] FAILED Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[277726.497611] scsi 1:0:0:0: [sda] CDB: Write(16) 8a 00 00 00 00 01 8e 3b 50 00 00 00 00 b0 00 00
[277726.497616] blk_update_request: I/O error, dev sda, sector 6681219072
[277726.497700] scsi 1:0:0:0: [sda] FAILED Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[277726.497706] scsi 1:0:0:0: [sda] CDB: Write(16) 8a 00 00 00 00 01 8e 3b 50 b0 00 00 00 f0 00 00
[277726.497711] blk_update_request: I/O error, dev sda, sector 6681219248

```

dmesg | grep sdb

```

[    3.706520] sd 1:0:0:1: [sdb] Very big device. Trying to use READ CAPACITY(16).
[    3.706769] sd 1:0:0:1: [sdb] 7814037168 512-byte logical blocks: (4.00 TB/3.64 TiB)
[    3.706771] sd 1:0:0:1: [sdb] 4096-byte physical blocks
[    3.706904] sd 1:0:0:1: [sdb] Write Protect is off
[    3.706907] sd 1:0:0:1: [sdb] Mode Sense: 67 00 10 08
[    3.707035] sd 1:0:0:1: [sdb] No Caching mode page found
[    3.707037] sd 1:0:0:1: [sdb] Assuming drive cache: write through
[    3.709436] sd 1:0:0:1: [sdb] Very big device. Trying to use READ CAPACITY(16).
[   10.778083] sd 1:0:0:1: [sdb] Very big device. Trying to use READ CAPACITY(16).
[   17.812245] sd 1:0:0:1: [sdb] Attached SCSI disk
[   18.139867] md: bind<sdb>
[   18.142358] md: zone0=[sda/sdb]
[277726.501484] sd 1:0:0:1: [sdb] tag#0 FAILED Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[277726.501495] sd 1:0:0:1: [sdb] tag#0 CDB: Write(16) 8a 00 00 00 00 00 83 fd f0 00 00 00 00 f0 00 00
[277726.501501] blk_update_request: I/O error, dev sdb, sector 2214457344
[277726.501604] sd 1:0:0:1: [sdb] tag#0 FAILED Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[277726.501612] sd 1:0:0:1: [sdb] tag#0 CDB: Write(16) 8a 00 00 00 00 00 83 fd f0 f0 00 00 00 70 00 00
[277726.501616] blk_update_request: I/O error, dev sdb, sector 2214457584
[277726.501705] sd 1:0:0:1: [sdb] tag#0 FAILED Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[277726.501712] sd 1:0:0:1: [sdb] tag#0 CDB: Read(16) 88 00 00 00 00 01 37 c8 63 f8 00 00 00 08 00 00
[277726.501716] blk_update_request: I/O error, dev sdb, sector 5230846968
[277726.501803] sd 1:0:0:1: [sdb] tag#0 FAILED Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[277726.501810] sd 1:0:0:1: [sdb] tag#0 CDB: Write(16) 8a 00 00 00 00 01 36 22 00 00 00 00 00 b0 00 00
[277726.501814] blk_update_request: I/O error, dev sdb, sector 5203165184
[277726.501898] sd 1:0:0:1: [sdb] tag#0 FAILED Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[277726.501905] sd 1:0:0:1: [sdb] tag#0 CDB: Write(16) 8a 00 00 00 00 01 36 22 00 b0 00 00 00 f0 00 00
[277726.501910] blk_update_request: I/O error, dev sdb, sector 5203165360
[277726.501993] sd 1:0:0:1: [sdb] tag#0 FAILED Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[277726.502000] sd 1:0:0:1: [sdb] tag#0 CDB: Write(16) 8a 00 00 00 00 01 36 22 01 a0 00 00 00 10 00 00
[277726.502004] blk_update_request: I/O error, dev sdb, sector 5203165600
[277726.502145] sd 1:0:0:1: [sdb] tag#0 FAILED Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[277726.502153] sd 1:0:0:1: [sdb] tag#0 CDB: Write(16) 8a 00 00 00 00 01 07 b2 80 58 00 00 00 f0 00 00
[277726.502161] blk_update_request: I/O error, dev sdb, sector 4424106072
[277726.502249] sd 1:0:0:1: [sdb] tag#0 FAILED Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[277726.502256] sd 1:0:0:1: [sdb] tag#0 CDB: Write(16) 8a 00 00 00 00 01 07 b2 81 48 00 00 00 70 00 00
[277726.502260] blk_update_request: I/O error, dev sdb, sector 4424106312

```

dmesg | grep sdc

```

[277728.596091] sd 2:0:0:0: [sdc] Very big device. Trying to use READ CAPACITY(16).
[277728.597344] sd 2:0:0:0: [sdc] 7814037168 512-byte logical blocks: (4.00 TB/3.64 TiB)
[277728.597351] sd 2:0:0:0: [sdc] 4096-byte physical blocks
[277728.597646] sd 2:0:0:0: [sdc] Write Protect is off
[277728.597654] sd 2:0:0:0: [sdc] Mode Sense: 67 00 10 08
[277728.597946] sd 2:0:0:0: [sdc] No Caching mode page found
[277728.598014] sd 2:0:0:0: [sdc] Assuming drive cache: write through
[277728.598505] sd 2:0:0:0: [sdc] Very big device. Trying to use READ CAPACITY(16).
[277728.607644] sd 2:0:0:0: [sdc] Very big device. Trying to use READ CAPACITY(16).
[277728.608095] sd 2:0:0:0: [sdc] Attached SCSI disk

```

dmesg | grep sdd

```

[277728.599814] sd 2:0:0:1: [sdd] Very big device. Trying to use READ CAPACITY(16).
[277728.606591] sd 2:0:0:1: [sdd] 7814037168 512-byte logical blocks: (4.00 TB/3.64 TiB)
[277728.606602] sd 2:0:0:1: [sdd] 4096-byte physical blocks
[277728.606931] sd 2:0:0:1: [sdd] Write Protect is off
[277728.606942] sd 2:0:0:1: [sdd] Mode Sense: 67 00 10 08
[277728.607373] sd 2:0:0:1: [sdd] No Caching mode page found
[277728.608731] sd 2:0:0:1: [sdd] Assuming drive cache: write through
[277728.610044] sd 2:0:0:1: [sdd] Very big device. Trying to use READ CAPACITY(16).
[277728.619871] sd 2:0:0:1: [sdd] Very big device. Trying to use READ CAPACITY(16).
[277728.620357] sd 2:0:0:1: [sdd] Attached SCSI disk

```

mdadm -Q /dev/sda

```

mdadm: cannot open /dev/sda: No such file or directory

```

mdadm -Q /dev/sdb

```

mdadm: cannot open /dev/sdb: No such file or directory

```

mdadm -Q /dev/sdc

```

/dev/sdc: is not an md array
/dev/sdc: device 0 in 2 device undetected raid0 /dev/md/0.  Use mdadm --examine for more detail.

```

mdadm -Q /dev/sdd

```

/dev/sdd: is not an md array
/dev/sdd: device 1 in 2 device undetected raid0 /dev/md/0.  Use mdadm --examine for more detail.

```

mdadm --examine /dev/sdd

```

/dev/sdd:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 33d48f90:1c5812ad:0eb0240f:7a054b2f
           Name : wisemen-nvr:0  (local to host wisemen-nvr)
  Creation Time : Thu Apr 20 11:32:48 2017
     Raid Level : raid0
   Raid Devices : 2

 Avail Dev Size : 7813775024 (3725.90 GiB 4000.65 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
   Unused Space : before=262056 sectors, after=0 sectors
          State : clean
    Device UUID : 874fd9ca:9953f7d3:355ff24b:61bf6790

    Update Time : Thu Apr 20 11:32:48 2017
  Bad Block Log : 512 entries available at offset 72 sectors
       Checksum : f177dd16 - correct
         Events : 0

     Chunk Size : 512K

   Device Role : Active device 1
   Array State : AA ('A' == active, '.' == missing, 'R' == replacing)

```

mdadm --examine /dev/sdc

```

/dev/sdc:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 33d48f90:1c5812ad:0eb0240f:7a054b2f
           Name : wisemen-nvr:0  (local to host wisemen-nvr)
  Creation Time : Thu Apr 20 11:32:48 2017
     Raid Level : raid0
   Raid Devices : 2

 Avail Dev Size : 7813775024 (3725.90 GiB 4000.65 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
   Unused Space : before=262056 sectors, after=0 sectors
          State : clean
    Device UUID : a9a3925d:c3c7c296:fb3519c3:a6d2365b

    Update Time : Thu Apr 20 11:32:48 2017
  Bad Block Log : 512 entries available at offset 72 sectors
       Checksum : 88f28f6c - correct
         Events : 0

     Chunk Size : 512K

   Device Role : Active device 0
   Array State : AA ('A' == active, '.' == missing, 'R' == replacing)

```

---

### Post by TheFu on 2018-11-20
Use UUIDs for the devices, not /dev/sd[a-z]. [https://raid.wiki.kernel.org/index.php/RAID_setup](https://raid.wiki.kernel.org/index.php/RAID_setup) says:
> A safer mechanism is to use the uuid parameter and run:

```
  mdadm --scan --assemble --uuid=a26bf396:31389f83:0df1722d:f404fe4c
```

This will only assemble the array that you want - but it will work no matter what has happened to the device names. This is particularly cool if, for example, you add in a new SATA controller card and all of a sudden /dev/sda becomes /dev/sde!!! 

Don't use USB3 for RAID systems.  Move to eSATA, SAS, SATA or Infiniband connections.  USB connections are susceptible to loosing connectivity due to vibrations. 

And you might want to reconsider setting up RAID without having a partition table for human maintainability reasons.  This shouldn't have any impact good/bad with the issues, but humans expect to find a partition table on storage devices.

---

### Post by clarknova on 2018-11-20
> **TheFu said:**
> Use UUIDs for the devices, not /dev/sd[a-z]

Thank you, that sounds like what I need.

> Don't use USB3 for RAID systems.  Move to eSATA, SAS, SATA or Infiniband connections.  USB connections are susceptible to loosing connectivity due to vibrations.

That sounds like good advice, but I don't have much latitude in this case, as the server is an Intel NUC, and none of those alternatives are options. 

> And you might want to reconsider setting up RAID without having a partition table for human maintainability reasons.  This shouldn't have any impact good/bad with the issues, but humans expect to find a partition table on storage devices.

Fair enough.

---

### Post by clarknova on 2018-11-21
mdadm didn't like when I used --scan and --assemble together, so here are the commands that ended up working for me.

```

mdadm --assemble /dev/md0 /dev/disk/by-id/usb-WDC_WD40_PURX-64NZ6Y0_152D00539000-0\:0 /dev/disk/by-id/usb-WDC_WD40_PURX-64NZ6Y0_152D00539000-0\:1

```

```

mdadm --detail --scan >> /etc/mdadm/mdadm.conf

```

Time will tell if this configuration will survive the USB device name shuffle.

---

### Post by TheFu on 2018-11-21
Probably want to use by-uuid/ links, not those.  They appear to be position dependent with the :0 and :1  at the end.

---

### Post by clarknova on 2018-11-21
Those disks did not appear in the by-uuid directory for some reason. The array came up fine using by-id. Time will tell if it auto-recovers after the disks stop responding.

---

### Post by TheFu on 2018-11-21
I'd guess it is due to the USB interface.

Assuming you don't swap the USB connections around, perhaps using by-path/ would be better?  On very large servers, this is the recommended method, so that swapping out failed disks doesn't change everything.

---

