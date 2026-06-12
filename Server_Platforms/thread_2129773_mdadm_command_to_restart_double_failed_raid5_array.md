---
title: "mdadm command to restart double failed raid5 array"
date: 2013-03-27
forum: Server Platforms
---

### Post by helasz on 2013-03-27
Hi All,

I am searching for the appropriate (ie. less risky) mdadm command to reassemble a double failed 4-partition raid5 array.

In my understanding (see test details below) I have 4 raid5 devices  (partitions) ceasing to work after two of them was kicked out together  from the array; two devices are  known to have some (reproducable) read  issues in a couple of sectors. Beside the read errors the state of the  array members seems (see below) to be good. I have read the mdadm manual  (more than once) and googling since two weeks, having collected a  remarkable amount of useful information. However I still see more than  one possible solutions at mdadm command level I can not see which is the  best.

  a) preliminary information
     clean (no hardware raid mix) software raid by mdadm
     raid5 was constructed from 4 partitions, no spare devices
     (partition size set to 1998000 MB in cfdisk for each)

     'sudo lshw --class disk --class storage' output is as follows
     (I dropped irrelevant IDE DVDROM info):

```

    *-disk:0
          description: ATA Disk
          product: ST2000DM001-9YN1
          vendor: Seagate
          physical id: 0
          bus info: scsi@2:0.0.0
          logical name: /dev/sda
          version: CC4B
          serial: Z1F1F34H
          size: 1863GiB (2TB)
          capabilities: partitioned partitioned:dos
          configuration: ansiversion=5 signature=b1d50fca
     *-disk:1
          description: ATA Disk
          product: ST2000DM001-9YN1
          vendor: Seagate
          physical id: 1
          bus info: scsi@2:0.1.0
          logical name: /dev/sdb
          version: CC4B
          serial: Z240E6XY
          size: 1863GiB (2TB)
          capabilities: partitioned partitioned:dos
          configuration: ansiversion=5 signature=b1d50fcb
     *-disk:2
          description: ATA Disk
          product: WDC WD20EURS-63S
          vendor: Western Digital
          physical id: 2
          bus info: scsi@3:0.0.0
          logical name: /dev/sdc
          version: 51.0
          serial: WD-WCAZAJ047801
          size: 1863GiB (2TB)
          capabilities: partitioned partitioned:dos
          configuration: ansiversion=5 signature=f781685f
     *-disk:3
          description: ATA Disk
          product: WDC WD20EURS-63S
          vendor: Western Digital
          physical id: 3
          bus info: scsi@3:0.1.0
          logical name: /dev/sdd
          version: 51.0
          serial: WD-WCAZAJ035055
          size: 1863GiB (2TB)
          capabilities: partitioned partitioned:dos
          configuration: ansiversion=5 signature=f9764a66 


```

    [I know from forums that WD Green is not really apropriate
    for raid, but I have received not chosen the HDDs]

  b) actions undetaken after failure
     - signed the exact order (sda-d) of the HDDs they were mounted
       in the failed state on old hardware
     - copy all the 4 raid5 partitions bitwise to other trustful HDDs  one by one on another trustful hardware; to my surprise while  the  Seagate HDDs copied just fine, both WDs did show a couple (5-8) of  read  errors, different in number and different in physical position  inside  the devices/partitions
     - I carried out the factory test  (this time under Windows) which  returned saying there were read errors which  probably may be repaired  by the factory program; I did NOT allowed any  corrections on the drives  in order to save the unaltered state in which the  devices failed
     - suspected cause of the failure is power issue (PSU?)
     - replaced the hardware the raid was run on  (motherboard, CPU,  PSU) took the suspect old hardware apart and  reconnected each drive to  the new motherboard in the same order they were previously on the old   hardware; I discovered that SATA order was different, so I changed  connections in a way sd[abcd] respect the original order


     c) test reults

     - according to individual raid superblocks (v1.2) taken from  mdadm's examine function two devices (sdb and sdd) slipped out from the  array at exactly the same time, the other two (sda,sdc) both failed to  update - these also at the same time - 144 s later and (probably) there  the raid array stopped working (produced events for instance were 58 on  both drives slipped out sooner and 64 on both failed later)

'sudo mdadm --examine /dev/sd[abcd]1' says

```


/dev/sda1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 4d398627:56d0269a:4ff424de:ea1140a8
           Name : DPC1351:0  (local to host DPC1351)
  Creation Time : Mon Dec 10 13:14:33 2012
     Raid Level : raid5
   Raid Devices : 4

 Avail Dev Size : 3902087006 (1860.66 GiB 1997.87 GB)
     Array Size : 5853129216 (5581.98 GiB 5993.60 GB)
  Used Dev Size : 3902086144 (1860.66 GiB 1997.87 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 0849c3b5:6e5aa1aa:738299f5:52c8278c

    Update Time : Wed Feb 27 10:38:36 2013
       Checksum : b1bbd51a - correct
         Events : 64

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 0
   Array State : AA.. ('A' == active, '.' == missing)

/dev/sdb1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 4d398627:56d0269a:4ff424de:ea1140a8
           Name : DPC1351:0  (local to host DPC1351)
  Creation Time : Mon Dec 10 13:14:33 2012
     Raid Level : raid5
   Raid Devices : 4

 Avail Dev Size : 3902087006 (1860.66 GiB 1997.87 GB)
     Array Size : 5853129216 (5581.98 GiB 5993.60 GB)
  Used Dev Size : 3902086144 (1860.66 GiB 1997.87 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : active
    Device UUID : 04038f90:42c95e7a:fa802ec6:abe3f179

    Update Time : Wed Feb 27 10:36:12 2013
       Checksum : 1aa2173f - correct
         Events : 58

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 2
   Array State : AAAA ('A' == active, '.' == missing)

/dev/sdc1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 4d398627:56d0269a:4ff424de:ea1140a8
           Name : DPC1351:0  (local to host DPC1351)
  Creation Time : Mon Dec 10 13:14:33 2012
     Raid Level : raid5
   Raid Devices : 4

 Avail Dev Size : 3902087006 (1860.66 GiB 1997.87 GB)
     Array Size : 5853129216 (5581.98 GiB 5993.60 GB)
  Used Dev Size : 3902086144 (1860.66 GiB 1997.87 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : fa68d73e:74cb4d26:baf10849:389d44e5

    Update Time : Wed Feb 27 10:38:36 2013
       Checksum : 6308ab37 - correct
         Events : 64

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 1
   Array State : AA.. ('A' == active, '.' == missing)

/dev/sdd1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 4d398627:56d0269a:4ff424de:ea1140a8
           Name : DPC1351:0  (local to host DPC1351)
  Creation Time : Mon Dec 10 13:14:33 2012
     Raid Level : raid5
   Raid Devices : 4

 Avail Dev Size : 3902087006 (1860.66 GiB 1997.87 GB)
     Array Size : 5853129216 (5581.98 GiB 5993.60 GB)
  Used Dev Size : 3902086144 (1860.66 GiB 1997.87 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : active
    Device UUID : 0c3d2376:685f7ca9:c1fa192f:b7893426

    Update Time : Wed Feb 27 10:36:12 2013
       Checksum : 44820749 - correct
         Events : 58

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 3
   Array State : AAAA ('A' == active, '.' == missing)


```

     - according to individual raid superblockstwo devices (sdb and sdd;  produced events number: 58) slipped out from the array at  exactly the  same time, the other two (sda,sdc;produced events number: 64) both  failed to update -  these also at the same time - 144 s later and  (probably) there the raid  array stopped working 
     - interestingly enough it was not the two WD drive or the two Seagate to go down together, but one of both at a time
     - superblocks with v1.2 metadata on each partition seems to be consistent, each data matches my settings and/or makes sense
     - actually the array does not start (sudo mdadm --assemble --scan) saying:

```


  mdadm: /dev/md/0 assembled from 2 drives - not enough to start the array.
  mdadm: No arrays found in config file or automatically


```

 
     - mdadm.conf [see attached] says there is a spare drive if I am not  wrong, but this was not the case at starting the array (there were no  spare drive)

```


  ARRAY /dev/md0 metadata=1.2 spares=1 name=DPC1351:0 UUID=4d398627:56d0269a:4ff424de:ea1140a8


```

     - I do not understand entirely the dmesg messages relative to the  raid array and its memebers [see dmesg.hdd.message], it seems to me that  after raid array has stopped, superblock of md0 was checked against  ext4, however the md0 raid has XFS (appr. 5.5 TB) so no wonder there is  no ext4. Apparently there is unsuccessful check against cramfs and  squashfs as well.

```

SCSI subsystem initialized
libata version 3.00 loaded.
...
scsi0 : ata_piix
scsi1 : ata_piix
ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
ata_piix 0000:00:1f.2: setting latency timer to 64
scsi2 : ata_piix
scsi3 : ata_piix
ata3: SATA max UDMA/133 cmd 0xd080 ctl 0xd000 bmdma 0xc800 irq 19
ata4: SATA max UDMA/133 cmd 0xcc00 ctl 0xc880 bmdma 0xc808 irq 19
...
ata3.00: ATA-8: ST2000DM001-9YN164, CC4B, max UDMA/133
ata3.00: 3907029168 sectors, multi 16: LBA48 NCQ (depth 0/32)
ata3.01: ATA-8: ST2000DM001-9YN164, CC4B, max UDMA/133
ata3.01: 3907029168 sectors, multi 16: LBA48 NCQ (depth 0/32)
ata3.00: configured for UDMA/133
ata4.00: ATA-8: WDC WD20EURS-63S48Y0, 51.0AB51, max UDMA/133
ata4.00: 3907029168 sectors, multi 16: LBA48 NCQ (depth 0/32)
ata4.01: ATA-8: WDC WD20EURS-63S48Y0, 51.0AB51, max UDMA/133
ata4.01: 3907029168 sectors, multi 16: LBA48 NCQ (depth 0/32)
ata3.01: configured for UDMA/133
scsi 2:0:0:0: Direct-Access     ATA      ST2000DM001-9YN1 CC4B PQ: 0 ANSI: 5
sd 2:0:0:0: Attached scsi generic sg0 type 0
sd 2:0:0:0: [sda] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
sd 2:0:0:0: [sda] 4096-byte physical blocks
sd 2:0:0:0: [sda] Write Protect is off
sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
ata4.00: configured for UDMA/133
 sda: sda1 sda2
scsi 2:0:1:0: Direct-Access     ATA      ST2000DM001-9YN1 CC4B PQ: 0 ANSI: 5
sd 2:0:1:0: Attached scsi generic sg1 type 0
sd 2:0:0:0: [sda] Attached SCSI disk
sd 2:0:1:0: [sdb] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
sd 2:0:1:0: [sdb] 4096-byte physical blocks
sd 2:0:1:0: [sdb] Write Protect is off
sd 2:0:1:0: [sdb] Mode Sense: 00 3a 00 00
sd 2:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
 sdb: sdb1 sdb2
sd 2:0:1:0: [sdb] Attached SCSI disk
ata4.01: configured for UDMA/133
scsi 3:0:0:0: Direct-Access     ATA      WDC WD20EURS-63S 51.0 PQ: 0 ANSI: 5
sd 3:0:0:0: Attached scsi generic sg2 type 0
scsi 3:0:1:0: Direct-Access     ATA      WDC WD20EURS-63S 51.0 PQ: 0 ANSI: 5
sd 3:0:1:0: Attached scsi generic sg3 type 0
sd 3:0:0:0: [sdc] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
sd 3:0:0:0: [sdc] 4096-byte physical blocks
sd 3:0:0:0: [sdc] Write Protect is off
sd 3:0:0:0: [sdc] Mode Sense: 00 3a 00 00
sd 3:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
 sdc: sdc1 sdc2
sd 3:0:1:0: [sdd] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
sd 3:0:1:0: [sdd] 4096-byte physical blocks
sd 3:0:1:0: [sdd] Write Protect is off
sd 3:0:1:0: [sdd] Mode Sense: 00 3a 00 00
sd 3:0:1:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
sd 3:0:0:0: [sdc] Attached SCSI disk
 sdd: sdd1 sdd2
sd 3:0:1:0: [sdd] Attached SCSI disk
...
mdadm: sending ioctl 800c0910 to a partition!
mdadm: sending ioctl 800c0910 to a partition!
mdadm: sending ioctl 1261 to a partition!
mdadm: sending ioctl 1261 to a partition!
mdadm: sending ioctl 1261 to a partition!
mdadm: sending ioctl 1261 to a partition!
mdadm: sending ioctl 1261 to a partition!
mdadm: sending ioctl 1261 to a partition!
mdadm: sending ioctl 1261 to a partition!
mdadm: sending ioctl 1261 to a partition!
md: md0 stopped.
md: bind<sdc1>
md: bind<sdb1>
md: bind<sdd1>
md: bind<sda1>
md: md0 stopped.
md: unbind<sda1>
md: export_rdev(sda1)
md: unbind<sdd1>
md: export_rdev(sdd1)
md: unbind<sdb1>
md: export_rdev(sdb1)
md: unbind<sdc1>
md: export_rdev(sdc1)
EXT4-fs (md0): unable to read superblock
EXT4-fs (md0): unable to read superblock
EXT4-fs (md0): unable to read superblock
cramfs: wrong magic
SQUASHFS error: squashfs_read_data failed to read block 0x0
SQUASHFS error: unable to read squashfs_super_block
...

```

     - I know smart test results would show valuable infos, but   unfortunately I do not have any (since motherboard did not support  switch it on/off, I  needed to switch on via software, which I was about  to do while setting  up automatic daily e-mail report on smart info two  months after the  array was started - unfortunately crash arrived  before time)


Conclusion: in my understanding I have 4 raid5 devices (partitions), two  of which is known to have some (reproducable) read issues in a couple  of sectors. 

Question: [provided that I do not care to loose a couple of files (ie  where the read issues are eventually) if I can recover most of the 2.5  TB data] what is the less risky way to restart the array:

1) restart with all the four HDDs (?), resyncing (?)

2) restart with three drives (taking into the array the less erroneous WD) and 
  a) adding immediately a 4th new drive to the array to be snyced
  
  b) adding a 4th new drive to the array only after the resyncing has completed
  
  c) any other solution?

What mdadm command should I fire in the given case?
Should I provide any further information?

Many thanks of the time and attention of anybody in advance!

---

### Post by darkod on 2013-03-27
First important thing is to note down the device order also. According to the --examine results and the Device Role field, the order seems to be sda1, sdc1, sdb1, sdd1.

Since the event counters are very close, first thing I would try is forced assemble and make sure the device order is correct:
```
sudo mdadm --assemble --force /dev/md0 /dev/sda1 /dev/sdc1 /dev/sdb1 /dev/sdd1
```

If that works, let it sync fully and then you can probably comment out the ARRAY definition in mdadm.conf that says there is one spare and make a new definition. I'll look up the command to do that once the array is working.

If the forced assemble doesn't work, the second option is this:
```
sudo mdadm --assemble --run --force /dev/md0 /dev/sda1 /dev/sdc1 /dev/sdb1 /dev/sdd1
```

See how that goes. If both options don't work, there is a third final option, but i hope it won't get that far. :)

---

### Post by helasz on 2013-03-27
Hi Darko,

Many many thanks for your tips! The first one worked prefectly.

Much appreciated!

helasz

PS: I can not find how to mark "solved" this thread. Among "Thread Tools" I do not find the relative menu item.

---

### Post by darkod on 2013-03-27
No problem. If you want to make a new ARRAY definition in mdadm.conf, first comment out the current one (put a # symbol at the front of the line), and then you can make a new definition of the running array with:
```
sudo mdadm --detail --scan >> /etc/mdadm/mdadm.conf
```

---

### Post by rubylaser on 2013-03-27
+1 darkod for your nice clear directions :)

---

### Post by darkod on 2013-03-27
> **rubylaser said:**
> +1 darkod for your nice clear directions :)

Thanks. :)

Yeah, the Mark as Solved seems to be broken right now. I'm not as admin so I can't mark it for you.

---

