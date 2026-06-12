---
title: "RAID5 not working"
date: 2009-08-10
forum: Server Platforms
---

### Post by adlabens on 2009-08-10
This post is long, but I'm in desperate need of help and would like to provide as much info as possible.  If there are other questions, please ask - I'll get immediate email notification & will respond asap.

In January, I built a brand new box with Ubuntu 8.10 Server edition, and it's been running like a champ ever since - including several vacation periods where the whole thing was shut down while we were gone & rebooted perfectly, upon return, without any manual intervention.  We went out of town for a week (after shutting down the entire home network) and came back this past Friday afternoon.  I booted the entire network and everything was working perfectly as I uploaded 1100+ photos from our netbook.  

When I went to rename a folder on the server, it gave me an error, said it couldn't find the folder.  Things got crazy from there.  I rebooted the WinXP Pro workstation and that didn't help, then I shut down & rebooted the server and that's when I had no more network storage (or data).

It's an ASUS motherboard with slots for 5 SATA-II drives, an E-SATA drive (unused), and an IDE drive for CD/DVD (from which I did my installation).

There are 5 HDDs in the system, all Western Digital.  The first one is 80 GB and it's dedicated to everything but data - it's got the OS & all swap files on it.  I got the system running with that before I started the RAID5 array installation.  The RAID5 array has 4 (exact same model #) 250 GB HDDs, and it appears that two of them are not mounting, tho I don't **think** anything is particularly wrong with them.

I am currently logged in as root.

mdadm --assemble --scan
> mdadm: /dev/md/0 assembled from 2 drives - not enough to start the array.

fdisk -l
> Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41413535

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       30401   244196001   fd  Linux raid autodetect

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0002d3a2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001   fd  Linux raid autodetect

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00010f8f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       30401   244196001   fd  Linux raid autodetect

Disk /dev/sdd: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0005380d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1        9327    74919096   83  Linux
/dev/sdd2            9328        9729     3229065    5  Extended
/dev/sdd5            9328        9729     3229033+  82  Linux swap / Solaris

Disk /dev/sde: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000b3fcd

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1       30401   244196001   fd  Linux raid autodetect


cat /proc/mdstat
> Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : inactive sde1[0](S) sdc1[4](S) sdb1[2](S) sda1[1](S)
      976783360 blocks super 1.0

unused devices: <none>


lshw (This one is long, but I've not deleted any of the output from this command - in case there's something important here, but I've **bolded** & **[COLOR="Red"]colored[/COLOR]** info that seems to be most important. Also, I apologize for the formatting, I've tried to make this one as readable as the output, but the "indent" & "/indent" indicators don't seem to want to cooperate with me at this late hour.)
> rch-server
[INDENT]    description: Desktop Computer
    product: System Product Name
    vendor: System manufacturer
    version: System Version
    serial: System Serial Number
    width: 64 bits
    capabilities: smbios-2.5 dmi-2.5 vsyscall64 vsyscall32
    configuration: boot=normal chassis=desktop uuid=00DC001E-8C00-0168-D3E2-0022157336AF

[/INDENT]  *-core
[INDENT]       description: Motherboard
       product: M3A78-EM
       vendor: ASUSTeK Computer INC.
       physical id: 0
       version: Rev X.0x
       serial: MS1C87BX3700923
       slot: To Be Filled By O.E.M.

     *-firmware
[INDENT]          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 0407 (07/02/2008)
          size: 64KiB
          capacity: 960KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification

[/INDENT]     *-cpu
[INDENT]          description: CPU
          product: AMD Athlon(tm) 64 X2 Dual Core Processor 6400+
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: AMD Athlon(tm) 64 X2 Dual Core Processor 6400+
          serial: To Be Filled By O.E.M.
          slot: AM2
          size: 3200MHz
          capacity: 3200MHz
          width: 64 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow rep_good nopl pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy

[/INDENT]        *-cache:0
[INDENT]             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 256KiB
             capacity: 256KiB
             capabilities: pipeline-burst internal varies data

 [/INDENT]       *-cache:1
[INDENT]             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 2MiB
             capacity: 2MiB
             capabilities: pipeline-burst internal varies unified

 [/INDENT]       *-cache:2 DISABLED
[INDENT]             description: L3 cache
             physical id: 7
             slot: L3-Cache
             capabilities: internal

[/INDENT]     *-memory
[INDENT]          description: System Memory
          physical id: 3c
          slot: System board or motherboard
          size: 4GiB

[/INDENT]        *-bank:0
[INDENT]             description: DIMM Synchronous 800 MHz (1.2 ns)
             product: PartNum0
             vendor: Manufacturer0
             physical id: 0
             serial: SerNum0
             slot: DIMM0
             size: 2GiB
             width: 64 bits
             clock: 800MHz (1.2ns)

[/INDENT]        *-bank:1
[INDENT]             description: DIMM Synchronous 800 MHz (1.2 ns)
             product: PartNum1
             vendor: Manufacturer1
             physical id: 1
             serial: SerNum1
             slot: DIMM1
             size: 2GiB
             width: 64 bits
             clock: 800MHz (1.2ns)

[/INDENT]        *-bank:2
[INDENT]             description: DIMM [empty]
             product: PartNum2
             vendor: Manufacturer2
             physical id: 2
             serial: SerNum2
             slot: DIMM2

[/INDENT]        *-bank:3
[INDENT]             description: DIMM [empty]
             product: PartNum3
             vendor: Manufacturer3
             physical id: 3
             serial: SerNum3
             slot: DIMM3

[/INDENT]     *-pci:0
[INDENT]          description: Host bridge
          product: RS780 Host Bridge
          vendor: Advanced Micro Devices [AMD]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz

[/INDENT]        *-pci:0
[INDENT]             description: PCI bridge
             product: ASUSTeK Computer Inc.
             vendor: ASUSTeK Computer Inc.
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci ht bus_master cap_list

[/INDENT]           *-display UNCLAIMED
[INDENT]                description: VGA compatible controller
                product: Radeon HD 3200 Graphics
                vendor: ATI Technologies Inc
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi bus_master cap_list
                configuration: latency=0

[/INDENT]           *-multimedia
[INDENT]                description: Audio device
                product: RS780 Azalia controller
                vendor: ATI Technologies Inc
                physical id: 5.1
                bus info: pci@0000:01:05.1
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi bus_master cap_list
                configuration: driver=HDA Intel latency=0 module=snd_hda_intel

[/INDENT]        *-pci:1
[INDENT]             description: PCI bridge
             product: RS780 PCI to PCI bridge (PCIE port 2)
             vendor: Advanced Micro Devices [AMD]
             physical id: 6
             bus info: pci@0000:00:06.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht bus_master cap_list
             configuration: driver=pcieport-driver

[/INDENT]           *-network
[INDENT]                description: Ethernet interface
                product: RTL8111/8168B PCI Express Gigabit Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: 02
                serial: 00:22:15:73:36:af
                size: 1GB/s
                capacity: 1GB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.2.2 latency=0 link=yes module=r8169 multicast=yes port=twisted pair speed=1GB/s

[/INDENT]        *-storage
[INDENT]             description: SATA controller
             product: SB700/SB800 SATA Controller [IDE mode]
             vendor: ATI Technologies Inc
             physical id: 11
             bus info: pci@0000:00:11.0
             logical name: scsi0
             logical name: scsi1
             logical name: scsi2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: storage pm bus_master cap_list emulated
             configuration: driver=ahci latency=64 module=ahci

[/INDENT]           *-disk:0
[INDENT]                description: ATA Disk
                product: **WDC WD2500AAKS-0**
                vendor: Western Digital
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: **/dev/sda**
                version: 01.0
                serial: **WD-WMART1760390**
                size: 232GiB (250GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=41413535

              *-volume
[INDENT]                   description: Linux raid autodetect partition
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: **/dev/sda1**
                   capacity: 232GiB
                   capabilities: primary multi

[/INDENT][/INDENT]           *-disk:1
[INDENT]                description: ATA Disk
                product: **WDC WD2500AAKS-0**
                vendor: Western Digital
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: **/dev/sdb**
                version: 01.0
                serial:** WD-WMAT15924203**
                size: 232GiB (250GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=0002d3a2

              *-volume
[INDENT]                   description: Linux raid autodetect partition
                   physical id: 1
                   bus info: scsi@1:0.0.0,1
                   logical name: **/dev/sdb1**
                   capacity: 232GiB
                   capabilities: primary multi

[/INDENT][/INDENT]           *-disk:2
[INDENT]                description: ATA Disk
                product: **WDC WD2500AAKS-0**
                vendor: Western Digital
                physical id: 0.0.0
                bus info: scsi@2:0.0.0
                logical name: **/dev/sdc**
                version: 01.0
                serial: **WD-WMAT15923873**
                size: 232GiB (250GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=00010f8f

              *-volume
[INDENT]                   description: EXT3 volume
                   physical id: 1
                   bus info: scsi@2:0.0.0,1
                   logical name: **/dev/sdc1**
                   version: 1.0
                   serial: 585932a4-6e29-4fae-b0c5-b26c430f8b42
                   size: 846GiB
                   capabilities: primary multi journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2011-12-14 03:43:17 filesystem=ext3 label=ï¿½ lastmountpoint=ï¿½ ï¿½ÒÒï¿½ ï¿½ modified=2009-08-07 19:11:26 mounted=2026-08-12 13:59:58 **[COLOR="Red"]state=unknown[/COLOR]**

[/INDENT][/INDENT]        *-usb:0
[INDENT]             description: USB Controller
             product: SB700/SB800 USB OHCI0 Controller
             vendor: ATI Technologies Inc
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64 module=ohci_hcd

[/INDENT]        *-usb:1
[INDENT]             description: USB Controller
             product: SB700 USB OHCI1 Controller
             vendor: ATI Technologies Inc
             physical id: 12.1
             bus info: pci@0000:00:12.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64 module=ohci_hcd

[/INDENT]        *-usb:2
[INDENT]             description: USB Controller
             product: SB700/SB800 USB EHCI Controller
             vendor: ATI Technologies Inc
             physical id: 12.2
             bus info: pci@0000:00:12.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=64 module=ehci_hcd

[/INDENT]        *-usb:3
[INDENT]             description: USB Controller
             product: SB700/SB800 USB OHCI0 Controller
             vendor: ATI Technologies Inc
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64 module=ohci_hcd

[/INDENT]        *-usb:4
[INDENT]             description: USB Controller
             product: SB700 USB OHCI1 Controller
             vendor: ATI Technologies Inc
             physical id: 13.1
             bus info: pci@0000:00:13.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64 module=ohci_hcd

[/INDENT]        *-usb:5
[INDENT]             description: USB Controller
             product: SB700/SB800 USB EHCI Controller
             vendor: ATI Technologies Inc
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=64 module=ehci_hcd

[/INDENT]        *-serial
[INDENT]             description: SMBus
             product: SBx00 SMBus Controller
             vendor: ATI Technologies Inc
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 3a
             width: 32 bits
             clock: 66MHz
             capabilities: ht cap_list
             configuration: driver=piix4_smbus latency=0 module=i2c_piix4

[/INDENT]        *-ide
[INDENT]             description: IDE interface
             product: SB700/SB800 IDE Controller
             vendor: ATI Technologies Inc
             physical id: 14.1
             bus info: pci@0000:00:14.1
             logical name: scsi4
             logical name: scsi5
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide msi bus_master cap_list emulated
             configuration: driver=pata_atiixp latency=64 module=pata_atiixp

[/INDENT]           *-cdrom
[INDENT]                description: DVD reader
                product: ROM
                vendor: 16X DVD-
                physical id: 0
                bus info: scsi@4:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/dvd
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 107G
                capabilities: removable audio dvd
                configuration: ansiversion=5 status=nodisc

[/INDENT]           *-disk:0
[INDENT]                description: ATA Disk
                product: **WDC WD800JD-00MS**
                vendor: Western Digital
                physical id: 1
                bus info: scsi@5:0.0.0
                logical name: **/dev/sdd**
                version: 10.0
                serial: **WD-WMAM9CRJ5825**
                size: 74GiB (80GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=0005380d

[INDENT]              *-volume:0
[INDENT]                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@5:0.0.0,1
                   logical name: /**dev/sdd1**
                   logical name: /
                   logical name: /dev/.static/dev
                   version: 1.0
                   serial: 06c0dfc0-4fa7-4e53-a4b9-b41f698bb49e
                   size: 71GiB
                   capacity: 71GiB
                   capabilities: primary **bootable journaled** extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2009-01-11 17:39:13 filesystem=ext3 modified=2009-08-09 22:24:04 mount.fstype=ext3 mount.options=ro,errors=remount-ro,data=ordered mounted=2009-08-09 22:24:04 **state=mounted**

[/INDENT]              *-volume:1
[INDENT]                   description: Extended partition
                   physical id: 2
                   bus info: scsi@5:0.0.0,2
                   logical name: **/dev/sdd2**
                   size: 3153MiB
                   capacity: 3153MiB
                   capabilities: primary extended partitioned partitioned:extended

[/INDENT]                 *-logicalvolume
[INDENT]                      description: **Linux swap** / Solaris partition
                      physical id: 5
                      logical name: **/dev/sdd5**
                      capacity: 3153MiB
                      capabilities: nofs

[/INDENT]           *-disk:1
[INDENT]                description: ATA Disk
                product: **WDC WD2500AAKS-0**
                vendor: Western Digital
                physical id: 0.1.0
                bus info: scsi@5:0.1.0
                logical name: **/dev/sde**
                version: 01.0
                serial: **WD-WMART1755547**
                size: 232GiB (250GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=000b3fcd

[INDENT]              *-volume
[INDENT]                   description: EXT3 volume
                   vendor: Linux
                   physical id: 1
                   bus info: scsi@5:0.1.0,1
                   logical name: **/dev/sde1**
                   version: 1.0
                   serial: 5ad9e3a3-6e29-4f8e-b0c5-b26c430f8b42
                   size: 698GiB
                   capabilities: primary multi journaled extended_attributes large_files huge_files recover ext3 ext2 initialized
                   configuration: created=2008-12-07 18:52:07 filesystem=ext3 modified=2009-08-07 19:11:26 mounted=2009-08-07 19:11:26 **[COLOR="Red"]state=unknown[/COLOR]**

[/INDENT][/INDENT][/INDENT]        *-isa
[INDENT]             description: ISA bridge
             product: SB700/SB800 LPC host controller
             vendor: ATI Technologies Inc
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0

[/INDENT]        *-pci:2
[INDENT]             description: PCI bridge
             product: SBx00 PCI to PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master

[/INDENT]        *-usb:6
[INDENT]             description: USB Controller
             product: SB700/SB800 USB OHCI2 Controller
             vendor: ATI Technologies Inc
             physical id: 14.5
             bus info: pci@0000:00:14.5
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=64 module=ohci_hcd

[/INDENT]     *-pci:1
[INDENT]          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz

[/INDENT]     *-pci:2
[INDENT]          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz

[/INDENT]     *-pci:3
[INDENT]          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz

[/INDENT]     *-pci:4
[INDENT]          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp module=k8temp
[/INDENT]root@RCH-SERVER:/#


So, now I know which two drives appear to be in trouble.

Contents of mdadm.conf:
> # mdadm.conf
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
ARRAY /dev/md/0 level=raid5 metadata=1.0 num-devices=4 UUID=13782a18:85c82f51:e999ccd0:c2ca0614 name=0

# This file was auto-generated on Sat, 08 Aug 2009 22:15:09 -0500
"mdadm.conf" 23L, 729C


root@RCH-SERVER:/dev/disk/by-id# ls
> ata-WDC_WD2500AAKS-00B3A0_WD-WMAT15923873
ata-WDC_WD2500AAKS-00B3A0_WD-WMAT15923873-part1
ata-WDC_WD2500AAKS-00B3A0_WD-WMAT15924203
ata-WDC_WD2500AAKS-00B3A0_WD-WMAT15924203-part1
ata-WDC_WD2500AAKS-00VSA0_WD-WMART1755547
ata-WDC_WD2500AAKS-00VSA0_WD-WMART1755547-part1
ata-WDC_WD2500AAKS-00VSA0_WD-WMART1760390
ata-WDC_WD2500AAKS-00VSA0_WD-WMART1760390-part1
ata-WDC_WD800JD-00MSA1_WD-WMAM9CRJ5825
ata-WDC_WD800JD-00MSA1_WD-WMAM9CRJ5825-part1
ata-WDC_WD800JD-00MSA1_WD-WMAM9CRJ5825-part2
ata-WDC_WD800JD-00MSA1_WD-WMAM9CRJ5825-part5
scsi-1ATA_WDC_WD2500AAKS-00B3A0_WD-WMAT15923873
scsi-1ATA_WDC_WD2500AAKS-00B3A0_WD-WMAT15923873-part1
scsi-1ATA_WDC_WD2500AAKS-00B3A0_WD-WMAT15924203
scsi-1ATA_WDC_WD2500AAKS-00B3A0_WD-WMAT15924203-part1
scsi-1ATA_WDC_WD2500AAKS-00VSA0_WD-WMART1755547
scsi-1ATA_WDC_WD2500AAKS-00VSA0_WD-WMART1755547-part1
scsi-1ATA_WDC_WD2500AAKS-00VSA0_WD-WMART1760390
scsi-1ATA_WDC_WD2500AAKS-00VSA0_WD-WMART1760390-part1
scsi-1ATA_WDC_WD800JD-00MSA1_WD-WMAM9CRJ5825
scsi-1ATA_WDC_WD800JD-00MSA1_WD-WMAM9CRJ5825-part1
scsi-1ATA_WDC_WD800JD-00MSA1_WD-WMAM9CRJ5825-part2
scsi-1ATA_WDC_WD800JD-00MSA1_WD-WMAM9CRJ5825-part5
root@RCH-SERVER:/dev/disk/by-id#


root@RCH-SERVER:/dev/disk/by-path# ls
> pci-0000:00:11.0-scsi-0:0:0:0        pci-0000:00:14.1-scsi-1:0:0:0
pci-0000:00:11.0-scsi-0:0:0:0-part1  pci-0000:00:14.1-scsi-1:0:0:0-part1
pci-0000:00:11.0-scsi-1:0:0:0        pci-0000:00:14.1-scsi-1:0:0:0-part2
pci-0000:00:11.0-scsi-1:0:0:0-part1  pci-0000:00:14.1-scsi-1:0:0:0-part5
pci-0000:00:11.0-scsi-2:0:0:0        pci-0000:00:14.1-scsi-1:0:1:0
pci-0000:00:11.0-scsi-2:0:0:0-part1  pci-0000:00:14.1-scsi-1:0:1:0-part1
pci-0000:00:14.1-scsi-0:0:0:0

root@RCH-SERVER:/dev/disk/by-uuid# ls
> 06c0dfc0-4fa7-4e53-a4b9-b41f698bb49e  4081d67c-74af-49ed-9b87-a312983ada62

I'm certain there's something I can do to enable me to connect an external 1 tb drive and get a good backup of this.  I DO have another 80 gb hdd that is ready to connect to replace the existing OS hdd, if nothing else will work (& Hopefully that will, but I want to try to fix it, first).

ALL help is GREATLY appreciated.

Thank you VERY much!
David Labens
San Antonio, TX

---

### Post by samosamo on 2009-08-10
See the (S) next to the device names in mdstat?  I'm pretty sure that means "spare disk."  Obviously you didn't set 4 drives to spares on accident, right?  Something got messed up.  It happens.  I pray for you and your family that you have a good backup regimen.

So you tried to assemble and it failed. Let's find out why. Get more details on the array using this command:

```
sudo mdadm --detail /dev/md?
```

Also, please carefully look through "dmesg" and "tail -n 1000 /var/log/syslog" and post anything that looks suspect.

---

### Post by adlabens on 2009-08-10
Samosamo, THANK you for the response.  I'm unsure of what I'm seeing, and especially of what I'm looking for.  I've posted the full response to each of the 3 commands you've requested.  

One note, someone mentioned that all the drives are marked as "spares" and I just want to reassemble the array, at least to get data off of it.

THANK YOU, and here's the info:



root@RCH-SERVER:/dev# mdadm --detail /dev/md?
> mdadm: md device /dev/md0 does not appear to be active.



root@RCH-SERVER:/dev# dmesg
> [    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.27-7-server (buildd@yellow) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu10) ) #1 SMP Fri Oct 24 07:20:47 UTC 2008 (Ubuntu 2.6.27-7.14-server)
[    0.000000] Command line: root=UUID=06c0dfc0-4fa7-4e53-a4b9-b41f698bb49e ro quiet splash
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009ec00 (usable)
[    0.000000]  BIOS-e820: 000000000009ec00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000cff80000 (usable)
[    0.000000]  BIOS-e820: 00000000cff80000 - 00000000cff8e000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000cff8e000 - 00000000cffd0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000cffd0000 - 00000000d0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff700000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000120000000 (usable)
[    0.000000] last_pfn = 0x120000 max_arch_pfn = 0x3ffffffff
[    0.000000] last_pfn = 0xcff80 max_arch_pfn = 0x3ffffffff
[    0.000000] init_memory_mapping
[    0.000000]  0000000000 - 00cfe00000 page 2M
[    0.000000]  00cfe00000 - 00cff80000 page 4k
[    0.000000] kernel direct mapping tables up to cff80000 @ 8000-e000
[    0.000000] last_map_addr: cff80000 end: cff80000
[    0.000000] init_memory_mapping
[    0.000000]  0100000000 - 0120000000 page 2M
[    0.000000] kernel direct mapping tables up to 120000000 @ c000-12000
[    0.000000] last_map_addr: 120000000 end: 120000000
[    0.000000] RAMDISK: 3771a000 - 37fef0dc
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP 000FB530, 0014 (r0 ACPIAM)
[    0.000000] ACPI: RSDT CFF80000, 003C (r1 070208 RSDT1243 20080702 MSFT       97)
[    0.000000] ACPI: FACP CFF80200, 0084 (r1 070208 FACP1243 20080702 MSFT       97)
[    0.000000] ACPI: DSDT CFF805C0, A331 (r1  A1044 A1044001        1 INTL 20051117)
[    0.000000] ACPI: FACS CFF8E000, 0040
[    0.000000] ACPI: APIC CFF80390, 006C (r1 070208 APIC1243 20080702 MSFT       97)
[    0.000000] ACPI: MCFG CFF80400, 003C (r1 070208 OEMMCFG  20080702 MSFT       97)
[    0.000000] ACPI: OEMB CFF8E040, 0071 (r1 070208 OEMB1243 20080702 MSFT       97)
[    0.000000] ACPI: HPET CFF8A900, 0038 (r1 070208 OEMHPET  20080702 MSFT       97)
[    0.000000] ACPI: SSDT CFF8A940, 0350 (r1 A_M_I_ POWERNOW        1 AMD         1)
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-0000000120000000
[    0.000000] Bootmem setup node 0 0000000000000000-0000000120000000
[    0.000000]   NODE_DATA [0000000000001000 - 0000000000005fff]
[    0.000000]   bootmap [000000000000d000 -  0000000000030fff] pages 24
[    0.000000] (7 early reservations) ==> bootmem [0000000000 - 0120000000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
[    0.000000]   #2 [0000200000 - 00008b6f9c]    TEXT DATA BSS ==> [0000200000 - 00008b6f9c]
[    0.000000]   #3 [003771a000 - 0037fef0dc]          RAMDISK ==> [003771a000 - 0037fef0dc]
[    0.000000]   #4 [000009ec00 - 0000100000]    BIOS reserved ==> [000009ec00 - 0000100000]
[    0.000000]   #5 [0000008000 - 000000c000]          PGTABLE ==> [0000008000 - 000000c000]
[    0.000000]   #6 [000000c000 - 000000d000]          PGTABLE ==> [000000c000 - 000000d000]
[    0.000000] found SMP MP-table at [ffff8800000ff780] 000ff780
[    0.000000]  [ffffe20000000000-ffffe200047fffff] PMD -> [ffff880028200000-ffff88002bdfffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00120000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x0000009e
[    0.000000]     0: 0x00000100 -> 0x000cff80
[    0.000000]     0: 0x00100000 -> 0x00120000
[    0.000000] On node 0 totalpages: 982814
[    0.000000]   DMA zone: 2109 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 831424 pages, LIFO batch:31
[    0.000000]   Normal zone: 129024 pages, LIFO batch:31
[    0.000000] Detected use of extended apic ids on hypertransport bus
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 0, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Setting APIC routing to flat
[    0.000000] ACPI: HPET id: 0x8300 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 000000000009f000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e4000
[    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000cff80000 - 00000000cff8e000
[    0.000000] PM: Registered nosave memory: 00000000cff8e000 - 00000000cffd0000
[    0.000000] PM: Registered nosave memory: 00000000cffd0000 - 00000000d0000000
[    0.000000] PM: Registered nosave memory: 00000000d0000000 - 00000000ff700000
[    0.000000] PM: Registered nosave memory: 00000000ff700000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at d4000000 (gap: d0000000:2f700000)
[    0.000000] PERCPU: Allocating 64928 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 4, nr_node_ids 1
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 962557
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: root=UUID=06c0dfc0-4fa7-4e53-a4b9-b41f698bb49e ro quiet splash
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] TSC: PIT calibration confirmed by PMTIMER.
[    0.000000] TSC: using PIT calibration value
[    0.000000] Detected 3214.173 MHz processor.
[    0.010000] Console: colour VGA+ 80x25
[    0.010000] console [tty0] enabled
[    0.010000] Checking aperture...
[    0.010000] No AGP bridge found
[    0.010000] Node 0: aperture @ f36a000000 size 32 MB
[    0.010000] Aperture beyond 4GB. Ignoring.
[    0.010000] Your BIOS doesn't leave a aperture memory hole
[    0.010000] Please enable the IOMMU option in the BIOS setup
[    0.010000] This costs you 64 MB of RAM
[    0.010000] Mapping aperture over 65536 KB of RAM @ 20000000
[    0.010000] PM: Registered nosave memory: 0000000020000000 - 0000000024000000
[    0.010000] Memory: 3787848k/4718592k available (3110k kernel code, 143408k reserved, 1573k data, 536k init)
[    0.010000] CPA: page pool initialized 1 of 1 pages preallocated
[    0.010000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.010000] hpet clockevent registered
[    0.010006] Calibrating delay loop (skipped), value calculated using timer frequency.. 6428.34 BogoMIPS (lpj=32141730)
[    0.010026] Security Framework initialized
[    0.010031] SELinux:  Disabled at boot.
[    0.010040] AppArmor: AppArmor initialized
[    0.010313] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.012312] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.013255] Mount-cache hash table entries: 256
[    0.013399] Initializing cgroup subsys ns
[    0.013402] Initializing cgroup subsys cpuacct
[    0.013403] Initializing cgroup subsys memory
[    0.013414] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.013416] CPU: L2 Cache: 1024K (64 bytes/line)
[    0.013417] CPU 0/0 -> Node 0
[    0.013418] tseg: 0000000000
[    0.013427] CPU: Physical Processor ID: 0
[    0.013428] CPU: Processor Core ID: 0
[    0.013435] using C1E aware idle routine
[    0.014339] ACPI: Core revision 20080609
[    0.016827] ACPI: Checking initramfs for custom DSDT
[    0.241458] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.341472] CPU0: AMD Athlon(tm) 64 X2 Dual Core Processor 6400+ stepping 03
[    0.341475] Using local APIC timer interrupts.
[    0.350000] APIC timer calibration result 12555362
[    0.350002] Detected 12.555 MHz APIC timer.
[    0.350105] Booting processor 1/1 ip 6000
[    0.010000] Initializing CPU#1
[    0.010000] Calibrating delay using timer specific routine.. 6428.42 BogoMIPS (lpj=32142135)
[    0.010000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.010000] CPU: L2 Cache: 1024K (64 bytes/line)
[    0.010000] CPU 1/1 -> Node 0
[    0.010000] CPU: Physical Processor ID: 0
[    0.010000] CPU: Processor Core ID: 1
[    0.510186] CPU1: AMD Athlon(tm) 64 X2 Dual Core Processor 6400+ stepping 03
[    0.510199] Brought up 2 CPUs
[    0.510201] Total of 2 processors activated (12856.77 BogoMIPS).
[    0.510238] CPU0 attaching sched-domain:
[    0.510240]  domain 0: span 0-1 level CPU
[    0.510242]   groups: 0 1
[    0.510244]   domain 1: span 0-1 level NODE
[    0.510246]    groups: 0-1
[    0.510249] CPU1 attaching sched-domain:
[    0.510250]  domain 0: span 0-1 level CPU
[    0.510251]   groups: 1 0
[    0.510253]   domain 1: span 0-1 level NODE
[    0.510254]    groups: 0-1
[    0.510312] net_namespace: 1552 bytes
[    0.510312] Booting paravirtualized kernel on bare hardware
[    0.510312] Time:  3:23:49  Date: 08/10/09
[    0.510312] NET: Registered protocol family 16
[    0.510312] node 0 link 0: io port [1000, ffffff]
[    0.510312] TOM: 00000000d0000000 aka 3328M
[    0.510312] node 0 link 0: mmio [a0000, bffff]
[    0.510312] node 0 link 0: mmio [d0000000, efffffff]
[    0.510312] node 0 link 0: mmio [f0000000, fbcfffff]
[    0.510312] node 0 link 0: mmio [fbd00000, fbdfffff]
[    0.510312] node 0 link 0: mmio [fbe00000, ffefffff]
[    0.510312] TOM2: 0000000130000000 aka 4864M
[    0.510312] bus: [00,07] on node 0 link 0
[    0.510312] bus: 00 index 0 io port: [0, ffff]
[    0.510312] bus: 00 index 1 mmio: [a0000, bffff]
[    0.510312] bus: 00 index 2 mmio: [d0000000, ffffffff]
[    0.510312] bus: 00 index 3 mmio: [130000000, fcffffffff]
[    0.510312] ACPI: bus type pci registered
[    0.510312] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.510312] PCI: Not using MMCONFIG.
[    0.510312] PCI: Using configuration type 1 for base access
[    0.510312] mtrr: your CPUs had inconsistent fixed MTRR settings
[    0.510312] mtrr: probably your BIOS does not setup all CPUs.
[    0.510312] mtrr: corrected configuration.
[    0.510590] ACPI: EC: Look up EC in DSDT
[    0.523026] ACPI: Interpreter enabled
[    0.523028] ACPI: (supports S0 S1 S3 S4 S5)
[    0.523041] ACPI: Using IOAPIC for interrupt routing
[    0.523094] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.527741] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
[    0.535543] PCI: Using MMCONFIG at e0000000 - efffffff
[    0.541893] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.541893] pci 0000:00:06.0: PME# supported from D0 D3hot D3cold
[    0.541893] pci 0000:00:06.0: PME# disabled
[    0.541893] PCI: 0000:00:11.0 reg 10 io port: [c000, c007]
[    0.541893] PCI: 0000:00:11.0 reg 14 io port: [b000, b003]
[    0.541893] PCI: 0000:00:11.0 reg 18 io port: [a000, a007]
[    0.541893] PCI: 0000:00:11.0 reg 1c io port: [9000, 9003]
[    0.541893] PCI: 0000:00:11.0 reg 20 io port: [8000, 800f]
[    0.541893] PCI: 0000:00:11.0 reg 24 32bit mmio: [fbcff800, fbcffbff]
[    0.541893] pci 0000:00:11.0: set SATA to AHCI mode
[    0.541893] PCI: 0000:00:12.0 reg 10 32bit mmio: [fbcfe000, fbcfefff]
[    0.541893] PCI: 0000:00:12.1 reg 10 32bit mmio: [fbcfd000, fbcfdfff]
[    0.541893] PCI: 0000:00:12.2 reg 10 32bit mmio: [fbcff000, fbcff0ff]
[    0.541893] pci 0000:00:12.2: supports D1
[    0.541893] pci 0000:00:12.2: supports D2
[    0.541893] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
[    0.541893] pci 0000:00:12.2: PME# disabled
[    0.541893] PCI: 0000:00:13.0 reg 10 32bit mmio: [fbcfc000, fbcfcfff]
[    0.541893] PCI: 0000:00:13.1 reg 10 32bit mmio: [fbcfb000, fbcfbfff]
[    0.541893] PCI: 0000:00:13.2 reg 10 32bit mmio: [fbcfa800, fbcfa8ff]
[    0.541893] pci 0000:00:13.2: supports D1
[    0.541893] pci 0000:00:13.2: supports D2
[    0.541893] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
[    0.541893] pci 0000:00:13.2: PME# disabled
[    0.541893] PCI: 0000:00:14.1 reg 10 io port: [0, 7]
[    0.541893] PCI: 0000:00:14.1 reg 14 io port: [0, 3]
[    0.541893] PCI: 0000:00:14.1 reg 18 io port: [0, 7]
[    0.541893] PCI: 0000:00:14.1 reg 1c io port: [0, 3]
[    0.541893] PCI: 0000:00:14.1 reg 20 io port: [ff00, ff0f]
[    0.541893] PCI: 0000:00:14.5 reg 10 32bit mmio: [fbcf9000, fbcf9fff]
[    0.541893] PCI: 0000:01:05.0 reg 10 32bit mmio: [d0000000, dfffffff]
[    0.541893] PCI: 0000:01:05.0 reg 14 io port: [d000, d0ff]
[    0.541893] PCI: 0000:01:05.0 reg 18 32bit mmio: [fbef0000, fbefffff]
[    0.541893] PCI: 0000:01:05.0 reg 24 32bit mmio: [fbd00000, fbdfffff]
[    0.541893] pci 0000:01:05.0: supports D1
[    0.541893] pci 0000:01:05.0: supports D2
[    0.541893] PCI: 0000:01:05.1 reg 10 32bit mmio: [fbee8000, fbeebfff]
[    0.541893] pci 0000:01:05.1: supports D1
[    0.541893] pci 0000:01:05.1: supports D2
[    0.541893] PCI: bridge 0000:00:01.0 io port: [d000, dfff]
[    0.541893] PCI: bridge 0000:00:01.0 32bit mmio: [fbd00000, fbefffff]
[    0.541893] PCI: bridge 0000:00:01.0 64bit mmio pref: [d0000000, dfffffff]
[    0.541893] PCI: 0000:02:00.0 reg 10 io port: [e800, e8ff]
[    0.541893] PCI: 0000:02:00.0 reg 18 64bit mmio: [fbfff000, fbffffff]
[    0.541893] PCI: 0000:02:00.0 reg 20 32bit mmio: [faff0000, faffffff]
[    0.541893] PCI: 0000:02:00.0 reg 30 32bit mmio: [fbfc0000, fbfdffff]
[    0.541893] pci 0000:02:00.0: supports D1
[    0.541893] pci 0000:02:00.0: supports D2
[    0.541893] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.541893] pci 0000:02:00.0: PME# disabled
[    0.541893] PCI: bridge 0000:00:06.0 io port: [e000, efff]
[    0.541893] PCI: bridge 0000:00:06.0 32bit mmio: [fbf00000, fbffffff]
[    0.541893] PCI: bridge 0000:00:06.0 64bit mmio pref: [faf00000, faffffff]
[    0.541893] pci 0000:00:14.4: transparent bridge
[    0.541893] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.541893] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.541893] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE6._PRT]
[    0.541893] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0PC._PRT]
[    0.550075] ACPI: PCI Interrupt Link [LNKA] (IRQs 4 *7 10 11 12 14 15)
[    0.550203] ACPI: PCI Interrupt Link [LNKB] (IRQs *4 7 10 11 12 14 15)
[    0.550334] ACPI: PCI Interrupt Link [LNKC] (IRQs 4 7 *10 11 12 14 15)
[    0.550466] ACPI: PCI Interrupt Link [LNKD] (IRQs 4 7 *10 11 12 14 15)
[    0.550597] ACPI: PCI Interrupt Link [LNKE] (IRQs 4 7 10 11 12 14 15) *0, disabled.
[    0.550729] ACPI: PCI Interrupt Link [LNKF] (IRQs 4 7 10 11 12 14 15) *0, disabled.
[    0.550861] ACPI: PCI Interrupt Link [LNKG] (IRQs 4 7 10 *11 12 14 15)
[    0.550992] ACPI: PCI Interrupt Link [LNKH] (IRQs 4 7 10 11 12 14 15) *0, disabled.
[    0.551049] ACPI Warning (tbutils-0217): Incorrect checksum in table [OEMB] - F2, should be EA [20080609]
[    0.551049] Linux Plug and Play Support v0.97 (c) Adam Belay
[    0.551049] pnp: PnP ACPI init
[    0.551049] ACPI: bus type pnp registered
[    0.551049] pnp: PnP ACPI: found 14 devices
[    0.551049] ACPI: ACPI bus type pnp unregistered
[    0.551049] PCI: Using ACPI for IRQ routing
[    0.590006] NET: Registered protocol family 8
[    0.590008] NET: Registered protocol family 20
[    0.590030] NetLabel: Initializing
[    0.590031] NetLabel:  domain hash size = 128
[    0.590032] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.590042] NetLabel:  unlabeled traffic allowed by default
[    0.590094] PCI-DMA: Disabling AGP.
[    0.590175] PCI-DMA: aperture base @ 20000000 size 65536 KB
[    0.590175] PCI-DMA: using GART IOMMU.
[    0.590175] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture
[    0.590548] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.590553] hpet0: 4 32-bit timers, 14318180 Hz
[    0.593386] tracer: 1286 pages allocated for 65536 entries of 80 bytes
[    0.593387]    actual entries 65586
[    0.593476] AppArmor: AppArmor Filesystem Enabled
[    0.593500] ACPI: RTC can wake from S4
[    0.600014] Switched to high resolution mode on CPU 0
[    0.600151] Switched to high resolution mode on CPU 1
[    0.630049] system 00:09: iomem range 0xfec00000-0xfec00fff has been reserved
[    0.630051] system 00:09: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.630056] system 00:0a: ioport range 0x4d0-0x4d1 has been reserved
[    0.630058] system 00:0a: ioport range 0x40b-0x40b has been reserved
[    0.630060] system 00:0a: ioport range 0x4d6-0x4d6 has been reserved
[    0.630062] system 00:0a: ioport range 0xc00-0xc01 has been reserved
[    0.630064] system 00:0a: ioport range 0xc14-0xc14 has been reserved
[    0.630065] system 00:0a: ioport range 0xc50-0xc51 has been reserved
[    0.630067] system 00:0a: ioport range 0xc52-0xc52 has been reserved
[    0.630069] system 00:0a: ioport range 0xc6c-0xc6c has been reserved
[    0.630070] system 00:0a: ioport range 0xc6f-0xc6f has been reserved
[    0.630072] system 00:0a: ioport range 0xcd0-0xcd1 has been reserved
[    0.630074] system 00:0a: ioport range 0xcd2-0xcd3 has been reserved
[    0.630076] system 00:0a: ioport range 0xcd4-0xcd5 has been reserved
[    0.630077] system 00:0a: ioport range 0xcd6-0xcd7 has been reserved
[    0.630079] system 00:0a: ioport range 0xcd8-0xcdf has been reserved
[    0.630081] system 00:0a: ioport range 0xb00-0xb3f has been reserved
[    0.630082] system 00:0a: ioport range 0x800-0x89f has been reserved
[    0.630084] system 00:0a: ioport range 0xb20-0xb2f has been reserved
[    0.630086] system 00:0a: ioport range 0x900-0x90f has been reserved
[    0.630088] system 00:0a: ioport range 0x910-0x91f has been reserved
[    0.630090] system 00:0a: ioport range 0xfe00-0xfefe has been reserved
[    0.630092] system 00:0a: iomem range 0xffb80000-0xffbfffff could not be reserved
[    0.630094] system 00:0a: iomem range 0xfec10000-0xfec1001f has been reserved
[    0.630096] system 00:0a: iomem range 0xfed40000-0xfed44fff has been reserved
[    0.630100] system 00:0b: ioport range 0x230-0x23f has been reserved
[    0.630102] system 00:0b: ioport range 0x290-0x29f has been reserved
[    0.630106] system 00:0b: ioport range 0xa20-0xa2f has been reserved
[    0.630107] system 00:0b: ioport range 0xa30-0xa3f has been reserved
[    0.630111] system 00:0c: iomem range 0xe0000000-0xefffffff has been reserved
[    0.630116] system 00:0d: iomem range 0x0-0x9ffff could not be reserved
[    0.630117] system 00:0d: iomem range 0xc0000-0xcffff has been reserved
[    0.630119] system 00:0d: iomem range 0xe0000-0xfffff could not be reserved
[    0.630121] system 00:0d: iomem range 0x100000-0xcfffffff could not be reserved
[    0.630123] system 00:0d: iomem range 0xfed45000-0xffffffff could not be reserved
[    0.635348] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.635350] pci 0000:00:01.0:   IO window: 0xd000-0xdfff
[    0.635354] pci 0000:00:01.0:   MEM window: 0xfbd00000-0xfbefffff
[    0.635356] pci 0000:00:01.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
[    0.635360] pci 0000:00:06.0: PCI bridge, secondary bus 0000:02
[    0.635361] pci 0000:00:06.0:   IO window: 0xe000-0xefff
[    0.635364] pci 0000:00:06.0:   MEM window: 0xfbf00000-0xfbffffff
[    0.635366] pci 0000:00:06.0:   PREFETCH window: 0x000000faf00000-0x000000faffffff
[    0.635369] pci 0000:00:14.4: PCI bridge, secondary bus 0000:03
[    0.635371] pci 0000:00:14.4:   IO window: disabled
[    0.635375] pci 0000:00:14.4:   MEM window: disabled
[    0.635379] pci 0000:00:14.4:   PREFETCH window: disabled
[    0.635396] pci 0000:00:06.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.635399] pci 0000:00:06.0: setting latency timer to 64
[    0.635405] bus: 00 index 0 io port: [0, ffff]
[    0.635406] bus: 00 index 1 mmio: [0, ffffffffffffffff]
[    0.635408] bus: 01 index 0 io port: [d000, dfff]
[    0.635409] bus: 01 index 1 mmio: [fbd00000, fbefffff]
[    0.635410] bus: 01 index 2 mmio: [d0000000, dfffffff]
[    0.635412] bus: 01 index 3 mmio: [0, 0]
[    0.635413] bus: 02 index 0 io port: [e000, efff]
[    0.635414] bus: 02 index 1 mmio: [fbf00000, fbffffff]
[    0.635415] bus: 02 index 2 mmio: [faf00000, faffffff]
[    0.635416] bus: 02 index 3 mmio: [0, 0]
[    0.635418] bus: 03 index 0 mmio: [0, 0]
[    0.635419] bus: 03 index 1 mmio: [0, 0]
[    0.635420] bus: 03 index 2 mmio: [0, 0]
[    0.635421] bus: 03 index 3 io port: [0, ffff]
[    0.635422] bus: 03 index 4 mmio: [0, ffffffffffffffff]
[    0.635431] NET: Registered protocol family 2
[    0.720123] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.721282] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.724359] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.724771] TCP: Hash tables configured (established 524288 bind 65536)
[    0.724773] TCP reno registered
[    0.750094] NET: Registered protocol family 1
[    0.750177] checking if image is initramfs... it is
[    1.227122] Freeing initrd memory: 9044k freed
[    1.232253] audit: initializing netlink socket (disabled)
[    1.232263] type=2000 audit(1249874629.231:1): initialized
[    1.236054] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.238638] VFS: Disk quotas dquot_6.5.1
[    1.238718] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.238812] msgmni has been set to 7415
[    1.238913] io scheduler noop registered
[    1.238914] io scheduler anticipatory registered
[    1.238916] io scheduler deadline registered (default)
[    1.239037] io scheduler cfq registered
[    1.239130] pci 0000:01:05.0: Boot video device
[    1.239241] pcieport-driver 0000:00:06.0: setting latency timer to 64
[    1.239262] pcieport-driver 0000:00:06.0: found MSI capability
[    1.239285] pci_express 0000:00:06.0:pcie00: allocate port service
[    1.271915] hpet_resources: 0xfed00000 is busy
[    1.271984] Linux agpgart interface v0.103
[    1.271987] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.273970] brd: module loaded
[    1.274031] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    1.274127] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    1.274128] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    1.274244] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.320433] mice: PS/2 mouse device common for all mice
[    1.320581] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    1.320608] rtc0: alarms up to one month, y3k, hpet irqs
[    1.320658] cpuidle: using governor ladder
[    1.320660] cpuidle: using governor menu
[    1.320914] TCP cubic registered
[    1.321115] registered taskstats version 1
[    1.321210]   Magic number: 5:899:360
[    1.321330] rtc_cmos 00:03: setting system clock to 2009-08-10 03:23:50 UTC (1249874630)
[    1.321332] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.321334] EDD information not available.
[    1.321361] Freeing unused kernel memory: 536k freed
[    1.321579] Write protecting the kernel read-only data: 4344k
[    1.341622] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    1.381878] fuse init (API version 7.9)
[    1.394889] processor ACPI0007:00: registered as cooling_device0
[    1.394893] ACPI: Processor [P001] (supports 8 throttling states)
[    1.394946] processor ACPI0007:01: registered as cooling_device1
[    1.404517] device-mapper: uevent: version 1.0.3
[    1.404704] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: [email]dm-devel@redhat.com[/email]
[    1.415510] md: linear personality registered for level -1
[    1.417734] md: multipath personality registered for level -4
[    1.419703] md: raid0 personality registered for level 0
[    1.422615] md: raid1 personality registered for level 1
[    1.424401] xor: automatically using best checksumming function: generic_sse
[    1.471256]    generic_sse:  9881.200 MB/sec
[    1.471258] xor: using function: generic_sse (9881.200 MB/sec)
[    1.472077] async_tx: api initialized (async)
[    1.641259] raid6: int64x1   3195 MB/s
[    1.811260] raid6: int64x2   4255 MB/s
[    1.981261] raid6: int64x4   3976 MB/s
[    2.151270] raid6: int64x8   2779 MB/s
[    2.321257] raid6: sse2x1    4421 MB/s
[    2.491266] raid6: sse2x2    6057 MB/s
[    2.661259] raid6: sse2x4    6198 MB/s
[    2.661260] raid6: using algorithm sse2x4 (6198 MB/s)
[    2.661263] md: raid6 personality registered for level 6
[    2.661264] md: raid5 personality registered for level 5
[    2.661265] md: raid4 personality registered for level 4
[    2.673228] md: raid10 personality registered for level 10
[    2.819841] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    2.819860] r8169 0000:02:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    2.819874] r8169 0000:02:00.0: setting latency timer to 64
[    2.820184] eth0: RTL8168c/8111c at 0xffffc2000063c000, 00:22:15:73:36:af, XID 3c4000c0 IRQ 2302
[    2.829630] No dock devices found.
[    2.836380] usbcore: registered new interface driver usbfs
[    2.836399] usbcore: registered new interface driver hub
[    2.836444] usbcore: registered new device driver usb
[    2.848901] SCSI subsystem initialized
[    2.858732] libata version 3.00 loaded.
[    2.860978] ahci 0000:00:11.0: version 3.0
[    2.860995] ahci 0000:00:11.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    2.861096] ahci 0000:00:11.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[    2.861099] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part
[    2.861378] scsi0 : ahci
[    2.861479] scsi1 : ahci
[    2.861550] scsi2 : ahci
[    2.861634] scsi3 : ahci
[    2.861719] ata1: SATA max UDMA/133 abar m1024@0xfbcff800 port 0xfbcff900 irq 22
[    2.861722] ata2: SATA max UDMA/133 abar m1024@0xfbcff800 port 0xfbcff980 irq 22
[    2.861724] ata3: SATA max UDMA/133 abar m1024@0xfbcff800 port 0xfbcffa00 irq 22
[    2.861727] ata4: SATA max UDMA/133 abar m1024@0xfbcff800 port 0xfbcffa80 irq 22
[    2.867275] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[    3.390026] ata1: softreset failed (device not ready)
[    3.390063] ata1: failed due to HW bug, retry pmp=0
[    3.570033] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    3.571617] ata1.00: ATA-8: WDC WD2500AAKS-00VSA0, 01.01B01, max UDMA/133
[    3.571619] ata1.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    3.572663] ata1.00: configured for UDMA/133
[    4.120022] ata2: softreset failed (device not ready)
[    4.120055] ata2: failed due to HW bug, retry pmp=0
[    4.300031] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    4.301549] ata2.00: ATA-8: WDC WD2500AAKS-00B3A0, 01.03A01, max UDMA/133
[    4.301551] ata2.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    4.302397] ata2.00: configured for UDMA/133
[    4.851268] ata3: softreset failed (device not ready)
[    4.851301] ata3: failed due to HW bug, retry pmp=0
[    5.031278] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    5.032064] ata3.00: ATA-8: WDC WD2500AAKS-00B3A0, 01.03A01, max UDMA/133
[    5.032065] ata3.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    5.032913] ata3.00: configured for UDMA/133
[    5.400035] ata4: SATA link down (SStatus 0 SControl 300)
[    5.420091] scsi 0:0:0:0: Direct-Access     ATA      WDC WD2500AAKS-0 01.0 PQ: 0 ANSI: 5
[    5.420182] scsi 1:0:0:0: Direct-Access     ATA      WDC WD2500AAKS-0 01.0 PQ: 0 ANSI: 5
[    5.420254] scsi 2:0:0:0: Direct-Access     ATA      WDC WD2500AAKS-0 01.0 PQ: 0 ANSI: 5
[    5.420894] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    5.420907] ohci_hcd 0000:00:12.0: OHCI Host Controller
[    5.420938] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 1
[    5.420969] ohci_hcd 0000:00:12.0: irq 16, io mem 0xfbcfe000
[    5.485382] usb usb1: configuration #1 chosen from 1 choice
[    5.485401] hub 1-0:1.0: USB hub found
[    5.485410] hub 1-0:1.0: 3 ports detected
[    5.591427] ohci_hcd 0000:00:12.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    5.591438] ohci_hcd 0000:00:12.1: OHCI Host Controller
[    5.591463] ohci_hcd 0000:00:12.1: new USB bus registered, assigned bus number 2
[    5.591478] ohci_hcd 0000:00:12.1: irq 16, io mem 0xfbcfd000
[    5.655364] usb usb2: configuration #1 chosen from 1 choice
[    5.655382] hub 2-0:1.0: USB hub found
[    5.655390] hub 2-0:1.0: 3 ports detected
[    5.761409] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    5.761424] ehci_hcd 0000:00:12.2: EHCI Host Controller
[    5.761454] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 3
[    5.761495] ehci_hcd 0000:00:12.2: debug port 1
[    5.761513] ehci_hcd 0000:00:12.2: irq 17, io mem 0xfbcff000
[    5.780023] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    5.780128] usb usb3: configuration #1 chosen from 1 choice
[    5.780147] hub 3-0:1.0: USB hub found
[    5.780153] hub 3-0:1.0: 6 ports detected
[    5.890929] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    5.890939] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    5.890963] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 4
[    5.890987] ohci_hcd 0000:00:13.0: irq 18, io mem 0xfbcfc000
[    5.955352] usb usb4: configuration #1 chosen from 1 choice
[    5.955375] hub 4-0:1.0: USB hub found
[    5.955383] hub 4-0:1.0: 3 ports detected
[    6.062262] ohci_hcd 0000:00:13.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    6.062272] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    6.062293] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 5
[    6.062307] ohci_hcd 0000:00:13.1: irq 18, io mem 0xfbcfb000
[    6.124094] usb usb5: configuration #1 chosen from 1 choice
[    6.124113] hub 5-0:1.0: USB hub found
[    6.124120] hub 5-0:1.0: 3 ports detected
[    6.230161] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    6.230170] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    6.230190] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 6
[    6.230227] ehci_hcd 0000:00:13.2: debug port 1
[    6.230241] ehci_hcd 0000:00:13.2: irq 19, io mem 0xfbcfa800
[    6.260015] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    6.260076] usb usb6: configuration #1 chosen from 1 choice
[    6.260093] hub 6-0:1.0: USB hub found
[    6.260097] hub 6-0:1.0: 6 ports detected
[    6.361136] pata_atiixp 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    6.361162] pata_atiixp 0000:00:14.1: setting latency timer to 64
[    6.361233] scsi4 : pata_atiixp
[    6.362293] scsi5 : pata_atiixp
[    6.363563] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xff00 irq 14
[    6.363565] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xff08 irq 15
[    6.560478] ata5.00: ATAPI: 16X DVD-ROM, 107G, max UDMA/33
[    6.600422] ata5.00: configured for UDMA/33
[    6.800504] ata6.00: ATA-7: WDC WD800JD-00MSA1, 10.01E01, max UDMA/133
[    6.800506] ata6.00: 156301488 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    6.800716] ata6.01: ATA-8: WDC WD2500AAKS-00VSA0, 01.01B01, max UDMA/133
[    6.800718] ata6.01: 488397168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    6.820498] ata6.00: configured for UDMA/100
[    6.861796] ata6.01: configured for UDMA/100
[    6.862745] scsi 4:0:0:0: CD-ROM            16X DVD- ROM              107G PQ: 0 ANSI: 5
[    6.862853] scsi 5:0:0:0: Direct-Access     ATA      WDC WD800JD-00MS 10.0 PQ: 0 ANSI: 5
[    6.862940] scsi 5:0:1:0: Direct-Access     ATA      WDC WD2500AAKS-0 01.0 PQ: 0 ANSI: 5
[    6.867879] ohci_hcd 0000:00:14.5: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    6.867892] ohci_hcd 0000:00:14.5: OHCI Host Controller
[    6.867917] ohci_hcd 0000:00:14.5: new USB bus registered, assigned bus number 7
[    6.867933] ohci_hcd 0000:00:14.5: irq 18, io mem 0xfbcf9000
[    6.924143] usb usb7: configuration #1 chosen from 1 choice
[    6.924170] hub 7-0:1.0: USB hub found
[    6.924178] hub 7-0:1.0: 2 ports detected
[    7.036996] scsi 0:0:0:0: Attached scsi generic sg0 type 0
[    7.037024] scsi 1:0:0:0: Attached scsi generic sg1 type 0
[    7.037050] scsi 2:0:0:0: Attached scsi generic sg2 type 0
[    7.037079] scsi 4:0:0:0: Attached scsi generic sg3 type 5
[    7.037104] scsi 5:0:0:0: Attached scsi generic sg4 type 0
[    7.037129] scsi 5:0:1:0: Attached scsi generic sg5 type 0
[    7.056666] Driver 'sd' needs updating - please use bus_type methods
[    7.056772] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[    7.056792] sd 0:0:0:0: [sda] Write Protect is off
[    7.056794] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    7.056828] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.056909] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[    7.056926] sd 0:0:0:0: [sda] Write Protect is off
[    7.056928] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    7.056960] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.056963]  sda: sda1
[    7.072049] sd 0:0:0:0: [sda] Attached SCSI disk
[    7.072146] sd 1:0:0:0: [sdb] 488397168 512-byte hardware sectors (250059 MB)
[    7.072173] sd 1:0:0:0: [sdb] Write Protect is off
[    7.072175] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    7.072223] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.072293] sd 1:0:0:0: [sdb] 488397168 512-byte hardware sectors (250059 MB)
[    7.072317] sd 1:0:0:0: [sdb] Write Protect is off
[    7.072319] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    7.072365] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.072368]  sdb: sdb1
[    7.088826] sd 1:0:0:0: [sdb] Attached SCSI disk
[    7.088908] sd 2:0:0:0: [sdc] 488397168 512-byte hardware sectors (250059 MB)
[    7.088928] sd 2:0:0:0: [sdc] Write Protect is off
[    7.088929] sd 2:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    7.088962] sd 2:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.089019] sd 2:0:0:0: [sdc] 488397168 512-byte hardware sectors (250059 MB)
[    7.089036] sd 2:0:0:0: [sdc] Write Protect is off
[    7.089038] sd 2:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    7.089070] sd 2:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.089073]  sdc:<4>Driver 'sr' needs updating - please use bus_type methods
[    7.104828]  sdc1
[    7.104916] sd 2:0:0:0: [sdc] Attached SCSI disk
[    7.105046] sd 5:0:0:0: [sdd] 156301488 512-byte hardware sectors (80026 MB)
[    7.105073] sd 5:0:0:0: [sdd] Write Protect is off
[    7.105075] sd 5:0:0:0: [sdd] Mode Sense: 00 3a 00 00
[    7.105110] sd 5:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.105168] sd 5:0:0:0: [sdd] 156301488 512-byte hardware sectors (80026 MB)
[    7.105186] sd 5:0:0:0: [sdd] Write Protect is off
[    7.105188] sd 5:0:0:0: [sdd] Mode Sense: 00 3a 00 00
[    7.105221] sd 5:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.105223]  sdd:sr0: scsi3-mmc drive: 0x/48x cd/rw xa/form2 cdda tray
[    7.108874] Uniform CD-ROM driver Revision: 3.20
[    7.108932] sr 4:0:0:0: Attached scsi CD-ROM sr0
[    7.120745]  sdd1 sdd2 < sdd5 >
[    7.140379] sd 5:0:0:0: [sdd] Attached SCSI disk
[    7.140471] sd 5:0:1:0: [sde] 488397168 512-byte hardware sectors (250059 MB)
[    7.140491] sd 5:0:1:0: [sde] Write Protect is off
[    7.140493] sd 5:0:1:0: [sde] Mode Sense: 00 3a 00 00
[    7.140528] sd 5:0:1:0: [sde] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.140584] sd 5:0:1:0: [sde] 488397168 512-byte hardware sectors (250059 MB)
[    7.140602] sd 5:0:1:0: [sde] Write Protect is off
[    7.140603] sd 5:0:1:0: [sde] Mode Sense: 00 3a 00 00
[    7.140637] sd 5:0:1:0: [sde] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.140639]  sde: sde1
[    7.159857] sd 5:0:1:0: [sde] Attached SCSI disk
[    7.314713] md: md0 stopped.
[    7.385581] md: bind<sda1>
[    7.385711] md: bind<sdb1>
[    7.385830] md: bind<sdc1>
[    7.386007] md: bind<sde1>
[    7.397150] md: md0 stopped.
[    7.397162] md: unbind<sde1>
[    7.440177] md: export_rdev(sde1)
[    7.440185] md: unbind<sdc1>
[    7.470019] md: export_rdev(sdc1)
[    7.470026] md: unbind<sdb1>
[    7.510016] md: export_rdev(sdb1)
[    7.510021] md: unbind<sda1>
[    7.540015] md: export_rdev(sda1)
[    7.543999] md: bind<sda1>
[    7.544135] md: bind<sdb1>
[    7.544255] md: bind<sdc1>
[    7.544422] md: bind<sde1>
[   12.606980] kjournald starting.  Commit interval 5 seconds
[   12.606990] EXT3-fs: mounted filesystem with ordered data mode.
[   13.463541] ip_tables: (C) 2000-2006 Netfilter Core Team
[   15.421328] Adding 3229024k swap on /dev/sdd5.  Priority:-1 extents:1 across:3229024k
[   15.718025] EXT3 FS on sdd1, internal journal
[   15.853748] loop: module loaded
[   15.894818] lp: driver loaded but no devices found
[   17.002733] udevd version 124 started
[   17.179361] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   17.204221] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[   17.216051] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   17.270112] ACPI: Power Button (FF) [PWRF]
[   17.270503] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input3
[   17.340066] ACPI: Power Button (CM) [PWRB]
[   17.340309] ACPI: WMI: Mapper loaded
[   17.577687] HDA Intel 0000:01:05.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[   17.577704] HDA Intel 0000:01:05.1: setting latency timer to 64
[   17.655303] ACPI: I/O resource piix4_smbus [0xb00-0xb07] conflicts with ACPI region SOR1 [0xb00-0xb0f]
[   17.655306] ACPI: Device needs an ACPI driver
[   17.655312] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0xb00, revision 0
[   18.191901] input: PC Speaker as /devices/platform/pcspkr/input/input4
[   18.375204] md: md0 stopped.
[   18.375217] md: unbind<sde1>
[   18.431447] md: export_rdev(sde1)
[   18.431650] md: unbind<sdc1>
[   18.492212] md: export_rdev(sdc1)
[   18.492365] md: unbind<sdb1>
[   18.561408] md: export_rdev(sdb1)
[   18.561551] md: unbind<sda1>
[   18.621298] md: export_rdev(sda1)
[   18.645735] md: bind<sda1>
[   18.645860] md: bind<sdb1>
[   18.645981] md: bind<sdc1>
[   18.646162] md: bind<sde1>
[   18.664701] md: md0 stopped.
[   18.664714] md: unbind<sde1>
[   18.720176] md: export_rdev(sde1)
[   18.720185] md: unbind<sdc1>
[   18.750015] md: export_rdev(sdc1)
[   18.750022] md: unbind<sdb1>
[   18.780016] md: export_rdev(sdb1)
[   18.780021] md: unbind<sda1>
[   18.810015] md: export_rdev(sda1)
[   18.813603] md: bind<sda1>
[   18.813729] md: bind<sdb1>
[   18.813878] md: bind<sdc1>
[   18.814059] md: bind<sde1>
[   20.165079] r8169: eth0: link up
[   20.165096] r8169: eth0: link up
[   21.173350] NET: Registered protocol family 10
[   21.173662] lo: Disabled Privacy Extensions
[   21.965175] type=1505 audit(1249875246.129:2): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=4381
[   21.965320] type=1505 audit(1249875246.129:3): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=4381
[   24.532625] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   26.313053] ppdev: user-space parallel port driver
[ 2373.576261] md: md0 stopped.
[ 2373.576288] md: unbind<sde1>
[ 2373.630170] md: export_rdev(sde1)
[ 2373.630354] md: unbind<sdc1>
[ 2373.660020] md: export_rdev(sdc1)
[ 2373.660190] md: unbind<sdb1>
[ 2373.690020] md: export_rdev(sdb1)
[ 2373.690186] md: unbind<sda1>
[ 2373.720019] md: export_rdev(sda1)
[ 2373.779226] md: bind<sda1>
[ 2373.779371] md: bind<sdb1>
[ 2373.779489] md: bind<sdc1>
[ 2373.779663] md: bind<sde1>
[31086.816352] md: md0 stopped.
[31086.816370] md: unbind<sde1>
[31086.871446] md: export_rdev(sde1)
[31086.871499] md: unbind<sdc1>
[31086.901271] md: export_rdev(sdc1)
[31086.901315] md: unbind<sdb1>
[31086.931269] md: export_rdev(sdb1)
[31086.931317] md: unbind<sda1>
[31086.961269] md: export_rdev(sda1)
[31087.027536] md: bind<sda1>
[31087.027660] md: bind<sdb1>
[31087.027778] md: bind<sdc1>
[31087.027955] md: bind<sde1>
root@RCH-SERVER:/dev#




root@RCH-SERVER:/dev# tail -n 1000 /var/log/syslog
> Aug 10 06:39:00 RCH-SERVER syslogd 1.5.0#2ubuntu6: restart.
Aug 10 06:40:01 RCH-SERVER /USR/SBIN/CRON[7873]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Aug 10 06:50:01 RCH-SERVER /USR/SBIN/CRON[7921]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Aug 10 07:00:01 RCH-SERVER /USR/SBIN/CRON[7968]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Aug 10 07:10:01 RCH-SERVER /USR/SBIN/CRON[8091]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Aug 10 07:11:50 RCH-SERVER kernel: [31086.816352] md: md0 stopped.
Aug 10 07:11:50 RCH-SERVER kernel: [31086.816370] md: unbind<sde1>
Aug 10 07:11:51 RCH-SERVER kernel: [31086.871446] md: export_rdev(sde1)
Aug 10 07:11:51 RCH-SERVER kernel: [31086.871499] md: unbind<sdc1>
Aug 10 07:11:51 RCH-SERVER kernel: [31086.901271] md: export_rdev(sdc1)
Aug 10 07:11:51 RCH-SERVER kernel: [31086.901315] md: unbind<sdb1>
Aug 10 07:11:51 RCH-SERVER kernel: [31086.931269] md: export_rdev(sdb1)
Aug 10 07:11:51 RCH-SERVER kernel: [31086.931317] md: unbind<sda1>
Aug 10 07:11:51 RCH-SERVER kernel: [31086.961269] md: export_rdev(sda1)
Aug 10 07:11:51 RCH-SERVER kernel: [31087.027536] md: bind<sda1>
Aug 10 07:11:51 RCH-SERVER kernel: [31087.027660] md: bind<sdb1>
Aug 10 07:11:51 RCH-SERVER kernel: [31087.027778] md: bind<sdc1>
Aug 10 07:11:51 RCH-SERVER kernel: [31087.027955] md: bind<sde1>
Aug 10 07:17:01 RCH-SERVER /USR/SBIN/CRON[8156]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug 10 07:20:01 RCH-SERVER /USR/SBIN/CRON[8187]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Aug 10 07:30:01 RCH-SERVER /USR/SBIN/CRON[8243]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Aug 10 07:40:01 RCH-SERVER /USR/SBIN/CRON[8300]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Aug 10 07:50:01 RCH-SERVER /USR/SBIN/CRON[8356]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Aug 10 08:00:01 RCH-SERVER /USR/SBIN/CRON[8412]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Aug 10 08:10:01 RCH-SERVER /USR/SBIN/CRON[8469]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Aug 10 08:17:01 RCH-SERVER /USR/SBIN/CRON[8523]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug 10 08:20:01 RCH-SERVER /USR/SBIN/CRON[8555]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Aug 10 08:30:01 RCH-SERVER /USR/SBIN/CRON[8611]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Aug 10 08:40:01 RCH-SERVER /USR/SBIN/CRON[8668]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Aug 10 08:50:01 RCH-SERVER /USR/SBIN/CRON[8724]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Aug 10 09:00:01 RCH-SERVER /USR/SBIN/CRON[8780]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Aug 10 09:10:01 RCH-SERVER /USR/SBIN/CRON[8837]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Aug 10 09:17:01 RCH-SERVER /USR/SBIN/CRON[8890]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug 10 09:20:01 RCH-SERVER /USR/SBIN/CRON[8923]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Aug 10 09:30:02 RCH-SERVER /USR/SBIN/CRON[8979]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Aug 10 09:40:01 RCH-SERVER /USR/SBIN/CRON[9035]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Aug 10 09:50:01 RCH-SERVER /USR/SBIN/CRON[9092]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Aug 10 10:00:01 RCH-SERVER /USR/SBIN/CRON[9148]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Aug 10 10:10:01 RCH-SERVER /USR/SBIN/CRON[9204]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Aug 10 10:17:01 RCH-SERVER /USR/SBIN/CRON[9258]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug 10 10:20:01 RCH-SERVER /USR/SBIN/CRON[9291]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Aug 10 10:30:01 RCH-SERVER /USR/SBIN/CRON[9347]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Aug 10 10:40:01 RCH-SERVER /USR/SBIN/CRON[9403]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Aug 10 10:50:01 RCH-SERVER /USR/SBIN/CRON[9461]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Aug 10 11:00:01 RCH-SERVER /USR/SBIN/CRON[9517]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Aug 10 11:10:01 RCH-SERVER /USR/SBIN/CRON[9572]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Aug 10 11:17:01 RCH-SERVER /USR/SBIN/CRON[9626]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug 10 11:20:01 RCH-SERVER /USR/SBIN/CRON[9643]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Aug 10 11:30:01 RCH-SERVER /USR/SBIN/CRON[9699]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Aug 10 11:40:01 RCH-SERVER /USR/SBIN/CRON[9754]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Aug 10 11:50:01 RCH-SERVER /USR/SBIN/CRON[9811]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Aug 10 12:00:01 RCH-SERVER /USR/SBIN/CRON[9867]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Aug 10 12:10:01 RCH-SERVER /USR/SBIN/CRON[9923]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Aug 10 12:17:01 RCH-SERVER /USR/SBIN/CRON[9976]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug 10 12:20:01 RCH-SERVER /USR/SBIN/CRON[10010]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Aug 10 12:30:01 RCH-SERVER /USR/SBIN/CRON[10067]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Aug 10 12:40:01 RCH-SERVER /USR/SBIN/CRON[10123]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Aug 10 12:50:01 RCH-SERVER /USR/SBIN/CRON[10180]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Aug 10 13:00:01 RCH-SERVER /USR/SBIN/CRON[10236]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Aug 10 13:10:01 RCH-SERVER /USR/SBIN/CRON[10292]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Aug 10 13:17:01 RCH-SERVER /USR/SBIN/CRON[10345]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug 10 13:20:01 RCH-SERVER /USR/SBIN/CRON[10378]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Aug 10 13:30:01 RCH-SERVER /USR/SBIN/CRON[10435]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Aug 10 13:40:01 RCH-SERVER /USR/SBIN/CRON[10492]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Aug 10 13:50:01 RCH-SERVER /USR/SBIN/CRON[10547]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Aug 10 14:00:01 RCH-SERVER /USR/SBIN/CRON[10604]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Aug 10 14:10:01 RCH-SERVER /USR/SBIN/CRON[10660]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Aug 10 14:17:01 RCH-SERVER /USR/SBIN/CRON[10713]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug 10 14:20:01 RCH-SERVER /USR/SBIN/CRON[10746]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Aug 10 14:30:01 RCH-SERVER /USR/SBIN/CRON[10803]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Aug 10 14:40:01 RCH-SERVER /USR/SBIN/CRON[10861]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Aug 10 14:50:01 RCH-SERVER /USR/SBIN/CRON[10915]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Aug 10 15:00:01 RCH-SERVER /USR/SBIN/CRON[10972]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Aug 10 15:10:01 RCH-SERVER /USR/SBIN/CRON[11028]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Aug 10 15:17:01 RCH-SERVER /USR/SBIN/CRON[11081]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug 10 15:20:01 RCH-SERVER /USR/SBIN/CRON[11114]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Aug 10 15:30:01 RCH-SERVER /USR/SBIN/CRON[11171]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Aug 10 15:40:01 RCH-SERVER /USR/SBIN/CRON[11228]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Aug 10 15:50:01 RCH-SERVER /USR/SBIN/CRON[11283]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Aug 10 16:00:01 RCH-SERVER /USR/SBIN/CRON[11339]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Aug 10 16:10:01 RCH-SERVER /USR/SBIN/CRON[11396]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Aug 10 16:17:01 RCH-SERVER /USR/SBIN/CRON[11450]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug 10 16:20:01 RCH-SERVER /USR/SBIN/CRON[11482]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Aug 10 16:30:01 RCH-SERVER /USR/SBIN/CRON[11538]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Aug 10 16:40:01 RCH-SERVER /USR/SBIN/CRON[11596]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Aug 10 16:50:01 RCH-SERVER /USR/SBIN/CRON[11651]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Aug 10 17:00:01 RCH-SERVER /USR/SBIN/CRON[11707]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Aug 10 17:10:01 RCH-SERVER /USR/SBIN/CRON[11764]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)


---

### Post by adlabens on 2009-08-15
Any help, suggestions, etc. will be greatly appreciated.

Thanks,
David

---

### Post by fjgaude on 2009-08-16
Okay, what does your **/etc/mdadm/mdadm,conf** file look like?

And show us the offput from this:

```
sudo fdisk -l
```

I'm not much good at reading log files. <smile>

---

### Post by adlabens on 2009-08-16
Frank,

mdadm.conf shows:
> # mdadm.conf
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
ARRAY /dev/md/0 level=raid5 metadata=1.0 num-devices=4 UUID=13782a18:85c82f51:e999ccd0:c2ca0614 name=0

# This file was auto-generated on Sun, 11 Jan 2009 19:39:47 -0600
"mdadm.conf" 23L, 729C


AND ... fdisk -l responds with:

> Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41413535

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       30401   244196001   fd  Linux raid autodetect

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0002d3a2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001   fd  Linux raid autodetect

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00010f8f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       30401   244196001   fd  Linux raid autodetect

Disk /dev/sdd: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00055741

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1        9327    74919096   83  Linux
/dev/sdd2            9328        9729     3229065    5  Extended
/dev/sdd5            9328        9729     3229033+  82  Linux swap / Solaris

Disk /dev/sde: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000b3fcd

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1       30401   244196001   fd  Linux raid autodetect


Thanks,
David

---

### Post by fjgaude on 2009-08-16
All the drives seem to be okay. One more time:

```
sudo mdadm -E /dev/md0
```

That will verify the UUID of the array with the same UUID shown in mdadm.conf.

Plus, in the **mdadm.conf** file, where did that "metadata 1.0" come from? I would edit it out. BTW, what version of the OS and mdadm are you using?

As a last resort you could try this:

```
sudo mdadm --assemble --force /dev/md0
```

Do you have a mountpoint for the array?

---

### Post by JonLy on 2009-08-18
Hi
 
I'm very new to Linux but have bought exactly the same motherboard and am in the process of setting it up, i have noticed that you have:
 
*-storage 
[INDENT]description: SATA controller
product: SB700/SB800 SATA Controller [COLOR=red][IDE mode]
[/COLOR]vendor: ATI Technologies Inc

[/INDENT]and if i run lshw mine says:
 *-storage
             description: RAID bus controller
             product: SB700/SB800 SATA Controller [COLOR=red][RAID5 mode]
[/COLOR]             vendor: ATI Technologies Inc

So from that i suggest that you need to go into the bios and change that setting back to RAID, maybe the bios got reset during the powered off period.
 
If this does indeed fix it then you can return a favour by telling me how i can get my raid working.  I have 3 drives installed and have the bios set to raid, i expected that i would just see 1 logical drive in the OS but i can still see all 3 drives, do i need to run some software in ubuntu to do the actual raid?
 
Cheers
Jon

---

### Post by adlabens on 2009-08-18
> **JonLy said:**
> Hi
 
I'm very new to Linux but have bought exactly the same motherboard and am in the process of setting it up, i have noticed that you have:
 
*-storage 
[INDENT]description: SATA controller
product: SB700/SB800 SATA Controller [COLOR=red][IDE mode]
[/COLOR]vendor: ATI Technologies Inc

[/INDENT]and if i run lshw mine says:
 *-storage
             description: RAID bus controller
             product: SB700/SB800 SATA Controller [COLOR=red][RAID5 mode]
[/COLOR]             vendor: ATI Technologies Inc

So from that i suggest that you need to go into the bios and change that setting back to RAID, maybe the bios got reset during the powered off period.
 
If this does indeed fix it then you can return a favour by telling me how i can get my raid working.  I have 3 drives installed and have the bios set to raid, i expected that i would just see 1 logical drive in the OS but i can still see all 3 drives, do i need to run some software in ubuntu to do the actual raid?
 
Cheers
Jon

Jon,

I appreciate your suggestion, but I'll respectfully disagree.  

The "RAID" array that comes on the motherboard is a software RAID & not a hardware RAID.  

This means that the motherboard has to deal with the RAID as a single device rather than separate & individual drives.  It's very deceiving because you're setting parameters on the hardware, but it's NOT a hardware RAID array.  I learned this by asking a lot of questions in the beginning - here & the Ubuntu forums website, and the general consensus was that using the RAID array on the motherboard had a lot more drawbacks and compromises than I was willing to accept, and that using the IDE on the motherboard and the RAID configured and managed in the Operating System gave a lot more flexibility and options.  After doing that research, it was, essentially, a no-brainer decision.  But, I did originally think it was best because it was hardware, and I built the system once like that.  It worked ok, and I may never need or use any of the differences, but that was the route I chose to travel.

Also, the RAID array in Linux is upgradeable with new versions (updates & upgrades) of Linux, while the motherboard RAID array is not. 

I actually have built this box about 6 times, each time documenting exactly what I did and improving each time - it was both a major learning experience for me, and a method of documenting the best practices so that I could rebuild it from scratch in the future after I'll have long forgotten what I did.  Only the first time did I built it using the motherboard setting for RAID.  After that, I built it using the "on-board" IDE settings and let Linux configure the drives as RAID.  

It's more efficient to let the operating system do the operating system stuff, and let the motherboard do nothing but the motherboard.

Plus, for the discussion of repairing the drives - in the "I'm here & it's now" reality of my situation, it would destroy the data to go back and do it over.  So, here I am, with what I've got, and I can only move forward from here.

I have also downloaded SmartMonTools & installed it on the operating system ("apt-get install smartmontools" I believe).  The diagnostics have indicated that 3 of my RAIDed drives are in perfect health and only one (/dev/sdc) has read errors.  I've got a new drive, same model as the other RAIDed drives, on the way, & it should be here Friday.  Meanwhile, I'm examining the options of whether it would be best to ...
[LIST=1]
[*]Remove the bad drive and have it rebuild the data using the 3 remaining drives, or
[*]Replace the bad drive and have it rebuild the drive using the data on the other 3 drives, or
[*]Copying the data from the bad drive using a product such as SpinRite to the replacement drive and then having the OS re-sync the data.
[/LIST]I'm not sure which will provide useable data with less errors or misplaced bits.

As for your particular situation, I'd suggest doing something really strange but completely interesting - IF you have a separate drive that you are using for your OS.  I've got 5 drives installed, 1 80 gb OS drive and 4 250 gb drives for the RAID5 array.  I have two spare 80 gb OS drives, with Ubuntu Server 8.10 installed on one, and OpenSuse (& it's GUI) installed on another.  

Now, if you've got a dedicated OS drive, and dedicated drives for your RAID5 array, then I'd suggest ... doing exactly what I did.  Reset your drives to IDE, then download and install OpenSuSE & it's GUI, and build your system.  Have it working.  Make sure that you know it's working.  THEN, shut it down, disconnect the data cables for the RAID array, remove EVERYTHING from your OS HDD, and do it over using Ubuntu Server edition with no GUI (CLI - Command Line Interface), and it's a really simple MDADM command to have the OS recognize and build the RAID array automatically.  I can even email you the word.doc file I created with the processes I used, tho I must admit that it may not be perfect because, after doing the build so many times, I may have done things a bit differently somewhere & forgotten to document it.  I wrote the document not to teach someone else, but to help me when the time comes that I'll have to rebuild the system because the OS disk crashes.  Are you on Facebook (I don't want to post my email address here, tho I MAY have set my profile to allow PMs & emails)?

-> David

---

### Post by JonLy on 2009-08-19
Hi David,
 
Thanks for the tip, i do indeed have a seperate OS drive. I'm still in the process of setting it all up so your document will be greatly received :) I've PM'd you my email address. 
I'm off to download OpenSuSE now.
 
Cheers
Jon

---

### Post by adlabens on 2009-08-19
I downloaded & installed SmartMonTools, and ran diagnostics.  It is consistently showing the 3 drives /dev/sda, /dev/sdb, & /dev/sde are fine (/dev/sdd is the OS drive, so that one doesn't count), but that /dev/sdc has a consistent read error.

So, I ordered a new drive, exact same model # as the original 4, and it'll be in tomorrow.  After I get off work tomorrow, I'll unmount the old drive, fsdisk the new one to match one of the others, and then mount the new one, and it SHOULD have my data back & operational before bed time.

I'll post results here after it's done.

---

### Post by adlabens on 2009-09-11
Final update: The only solution was, with the RAID5 array unmounted, was to connect just the OS HDD and the damaged drive and a brand new blank drive, download & install ddrescue, and then run through multiple copy routines to get every possible bit of data off the old/damaged drive. I copied from the damaged drive with it in every possible position except having it in the freezer (because freezing it can move things around inside just enough to get a good reading, sometimes). Once I had that done, then I had to reassemble the RAID5 array, still unmounted, and (still unmounted) had to have it recreate the data, (fdisk with an option, I believe), and then mount the drive. Once done, I copied ALL the data to a 1 TB drive in my XP box, and found that there were 3 pictures that would not copy because the bytes were set to ZERO. There were 3 other pics that had the exact same data. So, from what I can tell, out of 12,000 pictures PLUS a total of 250 GB data, I lost less than 10 mb in six files. Not bad.

My choices were to use DDRESCUE or SpinWrite, and DDRESCUE is Linux, so that's the way I went.

Case closed!

---

