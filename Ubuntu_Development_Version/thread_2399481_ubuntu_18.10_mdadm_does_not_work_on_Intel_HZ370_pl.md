---
title: "ubuntu 18.10 mdadm does not work on Intel H/Z370 platform"
date: 2018-08-25
forum: Ubuntu Development Version
---

### Post by ma20at on 2018-08-25
it seems that Ubuntu 18.10 mdraid do not support the latest intel rst raid on H/Z370 platform.

i tried to assemble the existing raid groups but failed, and i change to dmraid and it works. 




```
root@ubt1810:/var/lib/libvirt/images# lsb_release -a

No LSB modules are available.

Distributor ID: Ubuntu

Description:    Ubuntu Cosmic Cuttlefish (development branch)

Release:        18.10

Codename:       cosmic




root@ubt1810:/var/lib/libvirt/images# mdadm --detail-platform

mdadm: imsm capabilities not found for controller: /sys/devices/pci0000:00/0000:00:17.0 (type SATA)

       Platform : Intel(R) Rapid Storage Technology enterprise

    RAID Levels : raid0 raid1 raid10 raid5

    Chunk Sizes : 4k 8k 16k 32k 64k 128k

    2TB volumes : supported

      2TB disks : supported

      Max Disks : 12

    Max Volumes : 2 per array, 12 per platform

    NVMe Device : /sys/devices/pci0000:00/0000:00:1d.0/0000:03:00.0




root@ubt1810:/var/lib/libvirt/images# mdadm -Esv

ARRAY metadata=imsm UUID=af51d449:603db42c:756ba42d:5428da14

   devices=/dev/sdb,/dev/sda

ARRAY /dev/md/BackupVol container=af51d449:603db42c:756ba42d:5428da14 member=0 UUID=180df093:bf11cf29:f4b2ea28:d59184f9




ARRAY metadata=imsm UUID=2ab0836f:f1dd69e4:fe0120dc:308ece0f

   devices=/dev/sdc,/dev/sdd

ARRAY /dev/md/NASvol container=2ab0836f:f1dd69e4:fe0120dc:308ece0f member=0 UUID=dd395b79:b830c522:8a7eee05:aa2b9700




root@ubt1810:/var/lib/libvirt/images# mdadm -Av /dev/md0 -e imsm /dev/sda /dev/sdb

mdadm: looking for devices for /dev/md0

mdadm: No OROM/EFI properties for /dev/sda

mdadm: no RAID superblock on /dev/sda

mdadm: /dev/sda has no superblock - assembly aborted

root@ubt1810:/var/lib/libvirt/images# mdadm -E /dev/sda

/dev/sda:

          Magic : Intel Raid ISM Cfg Sig.

        Version : 1.3.00

    Orig Family : 39e5ca6d

         Family : 39e5ca6d

     Generation : 0001b63e

     Attributes : All supported

           UUID : af51d449:603db42c:756ba42d:5428da14

       Checksum : 4ba86402 correct

    MPB Sectors : 1

          Disks : 2

   RAID Devices : 1




  Disk00 Serial : Z505240P

          State : active

             Id : 00000000

    Usable Size : 5860529152 (2794.52 GiB 3000.59 GB)




[BackupVol]:

           UUID : 180df093:bf11cf29:f4b2ea28:d59184f9

     RAID Level : 1

        Members : 2

          Slots : [UU]

    Failed disk : none

      This Slot : 0

    Sector Size : 512

     Array Size : 5860528647 (2794.52 GiB 3000.59 GB)

   Per Dev Size : 5860528911 (2794.52 GiB 3000.59 GB)

  Sector Offset : 0

    Num Stripes : 22892692

     Chunk Size : 64 KiB

       Reserved : 0

  Migrate State : idle

      Map State : normal

    Dirty State : clean

     RWH Policy : off




  Disk01 Serial : 65C48WS2S

          State : active

             Id : 00000001

    Usable Size : 5860529152 (2794.52 GiB 3000.59 GB)

root@ubt1810:/var/lib/libvirt/images# dmesg|grep 0000:00:17

[    0.358707] pci 0000:00:17.0: [8086:2822] type 00 class 0x010400

[    0.358751] pci 0000:00:17.0: reg 0x10: [mem 0xa1434000-0xa1435fff]

[    0.358770] pci 0000:00:17.0: reg 0x14: [mem 0xa143a000-0xa143a0ff]

[    0.358789] pci 0000:00:17.0: reg 0x18: [io  0x4090-0x4097]

[    0.358807] pci 0000:00:17.0: reg 0x1c: [io  0x4080-0x4083]

[    0.358826] pci 0000:00:17.0: reg 0x20: [io  0x4060-0x407f]

[    0.358845] pci 0000:00:17.0: reg 0x24: [mem 0xa1439000-0xa14397ff]

[    0.358952] pci 0000:00:17.0: PME# supported from D3hot

[    3.160396] iommu: Adding device 0000:00:17.0 to group 5

[    3.374007] ahci 0000:00:17.0: version 3.0

[    3.374211] ahci 0000:00:17.0: controller can't do SNTF, turning off CAP_SNTF

[    3.374516] ahci 0000:00:17.0: AHCI 0001.0301 32 slots 6 ports 6 Gbps 0x3f impl RAID mode

[    3.374519] ahci 0000:00:17.0: flags: 64bit ncq clo only pio slum part ems deso sadm sds apst 

root@ubt1810:/var/lib/libvirt/images# dmraid -r

/dev/sda: isw, "isw_jhbdgaihh", GROUP, ok, 5860533166 sectors, data@ 0

/dev/sdc: isw, "isw_eacjbghfjb", GROUP, ok, 5860533166 sectors, data@ 0

/dev/sdb: isw, "isw_jhbdgaihh", GROUP, ok, 5860533166 sectors, data@ 0

/dev/sdd: isw, "isw_eacjbghfjb", GROUP, ok, 5860533166 sectors, data@ 0
```

---

### Post by wildmanne39 on 2018-08-25
Hello and welcome to the forum!

*Thread moved to **Ubuntu Development Version for a more appropriate fit**.*

Please use the default font color and properties unless you need to highlight or draw attention to a part of your post.

Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

