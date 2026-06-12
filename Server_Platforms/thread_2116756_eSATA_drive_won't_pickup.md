---
title: "eSATA drive won't pickup"
date: 2013-02-16
forum: Server Platforms
---

### Post by cocoa117 on 2013-02-16
Hi, anyone have idea how to make Ubuntu 12.04 server pick up a ESATA hard disk? 

Here is what I have tested and working.
(1) the machine's BIOS can see the attached and powered on eSATA hard disk.
(2) the eSATA hard disk is functional. I have attached it to two different machines running Win7 and Ubuntu 12.04 desktop. Both pick it up fine.
(3) If I run ubuntu 12.04 live CD on the server, the live CD ubuntu can pick up the eSATA without issue. And here is the list of disks when running live CD

ll /sys/class/scsi_host/
lrwxrwxrwx  1 root root 0 Feb 16 21:36 host0 -> ../../devices/pci0000:00/0000:00:11.0/host0/scsi_host/host0/
lrwxrwxrwx  1 root root 0 Feb 16 21:36 host1 -> ../../devices/pci0000:00/0000:00:11.0/host1/scsi_host/host1/
lrwxrwxrwx  1 root root 0 Feb 16 21:36 host2 -> ../../devices/pci0000:00/0000:00:11.0/host2/scsi_host/host2/
lrwxrwxrwx  1 root root 0 Feb 16 21:36 host3 -> ../../devices/pci0000:00/0000:00:11.0/host3/scsi_host/host3/
lrwxrwxrwx  1 root root 0 Feb 16 21:36 host4 -> ../../devices/pci0000:00/0000:00:12.2/usb1/1-1/1-1:1.0/host4/scsi_host/host4/
lrwxrwxrwx  1 root root 0 Feb 16 21:36 host5 -> ../../devices/pci0000:00/0000:00:14.1/host5/scsi_host/host5/
lrwxrwxrwx  1 root root 0 Feb 16 21:36 host6 -> ../../devices/pci0000:00/0000:00:14.1/host6/scsi_host/host6/

dmesg | grep -i ata
[    0.000000]  BIOS-e820: 00000000ddfa0000 - 00000000ddfae000 (ACPI data)
[    0.000000]   NODE_DATA [000000021fffb000 - 000000021fffffff]
[    0.000000] Memory: 8061348k/8912896k available (6566k kernel code, 557960k absent, 293588k reserved, 6637k data, 920k init)
[    0.212012] _OSC request data:1 17 
[    3.496217] libata version 3.00 loaded.
[    6.446778] ahci 0000:00:11.0: AHCI 0001.0200 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[    6.448210] ata1: SATA max UDMA/133 abar m1024@0xfe6ffc00 port 0xfe6ffd00 irq 41
[    6.448215] ata2: SATA max UDMA/133 abar m1024@0xfe6ffc00 port 0xfe6ffd80 irq 41
[    6.448220] ata3: SATA max UDMA/133 abar m1024@0xfe6ffc00 port 0xfe6ffe00 irq 41
[    6.448224] ata4: SATA max UDMA/133 abar m1024@0xfe6ffc00 port 0xfe6ffe80 irq 41
[    6.448468] pata_acpi 0000:00:14.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    6.448502] pata_acpi 0000:00:14.1: setting latency timer to 64
[    6.936116] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    6.940139] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    6.944155] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    6.944796] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    6.944934] ata4.00: ATA-8: ST2000DL003-9VT166, CC45, max UDMA/133
[    6.944940] ata4.00: 3907029168 sectors, multi 0: LBA48 NCQ (depth 31/32)
[    6.945827] ata4.00: configured for UDMA/133
[    6.955052] ata2.00: ATA-8: WDC WD5000AACS-00ZUB0, 01.01B01, max UDMA/133
[    6.955058] ata2.00: 976773168 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
[    6.955962] ata2.00: configured for UDMA/133
[    6.959966] ata1.00: ATA-8: WDC WD5000AACS-00ZUB0, 01.01B01, max UDMA/133
[    6.959972] ata1.00: 976773168 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
[    6.960877] ata1.00: configured for UDMA/133
[    6.961187] scsi 0:0:0:0: Direct-Access     ATA      WDC WD5000AACS-0 01.0 PQ: 0 ANSI: 5
[    6.961612] scsi 1:0:0:0: Direct-Access     ATA      WDC WD5000AACS-0 01.0 PQ: 0 ANSI: 5
[    6.965901] ata3.00: ATA-8: WDC WD5000AACS-00ZUB0, 01.01B01, max UDMA/133
[    6.965906] ata3.00: 976773168 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
[    6.966809] ata3.00: configured for UDMA/133
[    6.967113] scsi 2:0:0:0: Direct-Access     ATA      WDC WD5000AACS-0 01.0 PQ: 0 ANSI: 5
[    6.967502] scsi 3:0:0:0: Direct-Access     ATA      ST2000DL003-9VT1 CC45 PQ: 0 ANSI: 5
[    6.991142] Write protecting the kernel read-only data: 12288k
[    7.196064] scsi5 : pata_atiixp
[    7.198500] scsi6 : pata_atiixp
[    7.199363] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xff00 irq 14
[    7.199367] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xff08 irq 15
[    7.384640] ata5.00: ATA-7: SAMSUNG HD154UI, 1AG01118, max UDMA7
[    7.384646] ata5.00: 2930277168 sectors, multi 16: LBA48 
[    7.384966] ata5.01: ATA-8: ST2000DL003-9VT166, CC45, max UDMA/133
[    7.384972] ata5.01: 3907029168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    7.384980] ata5.00: limited to UDMA/33 due to 40-wire cable
[    7.384983] ata5.01: limited to UDMA/33 due to 40-wire cable
[    7.392638] ata5.00: configured for UDMA/33
[    7.408743] ata5.01: configured for UDMA/33
[    7.409016] scsi 5:0:0:0: Direct-Access     ATA      SAMSUNG HD154UI  1AG0 PQ: 0 ANSI: 5
[    7.410036] scsi 5:0:1:0: Direct-Access     ATA      ST2000DL003-9VT1 CC45 PQ: 0 ANSI: 5
[   70.816124] ata5: lost interrupt (Status 0x51)
[   70.816145] ata5.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[   70.816152] ata5.00: failed command: SMART
[   70.816161] ata5.00: cmd b0/d1:01:00:4f:c2/00:00:00:00:00/00 tag 0 pio 512 in
[   70.816167] ata5.00: status: { DRDY }
[   70.816194] ata5: soft resetting link
[   70.996556] ata5.00: configured for UDMA/33
[   71.020683] ata5.01: configured for UDMA/33
[   71.020721] ata5: EH complete

parted -l
Model: ATA WDC WD5000AACS-0 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type      File system  Flags
 1      1049kB  500MB  499MB  primary                boot, raid
 2      501MB   500GB  500GB  extended
 5      501MB   500GB  500GB  logical                raid


Model: ATA WDC WD5000AACS-0 (scsi)
Disk /dev/sdb: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type      File system  Flags
 1      1049kB  500MB  499MB  primary                boot, raid
 2      501MB   500GB  500GB  extended
 5      501MB   500GB  500GB  logical                raid


Model: ATA WDC WD5000AACS-0 (scsi)
Disk /dev/sdc: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type      File system  Flags
 1      1049kB  500MB  499MB  primary                boot, raid
 2      501MB   500GB  500GB  extended
 5      501MB   500GB  500GB  logical                raid



                                                                          
Error: /dev/sdd: unrecognised disk label

Model: ATA SAMSUNG HD154UI (scsi)
Disk /dev/sde: 1500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  1500GB  1500GB  primary



                                                                          
Error: /dev/sdf: unrecognised disk label

Model: Kingston DT 101 G2 (scsi)
Disk /dev/sdg: 8022MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  3671MB  3670MB  primary  ntfs         boot
 2      3671MB  8022MB  4351MB  primary  fat32


Here is the what I have got when running 12.04 server
dmesg | grep -i ata
[    0.000000]  BIOS-e820: 00000000ddfa0000 - 00000000ddfae000 (ACPI data)
[    0.000000]   NODE_DATA [000000021fffb000 - 000000021fffffff]
[    0.000000] Memory: 8058168k/8912896k available (6569k kernel code, 557960k absent, 296768k reserved, 6634k data, 924k init)
[    0.248203] _OSC request data:1 17 
[    0.276147] libata version 3.00 loaded.
[    1.495962] ahci 0000:00:11.0: AHCI 0001.0200 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[    1.497483] ata1: SATA max UDMA/133 abar m1024@0xfe6ffc00 port 0xfe6ffd00 irq 41
[    1.497492] ata2: SATA max UDMA/133 abar m1024@0xfe6ffc00 port 0xfe6ffd80 irq 41
[    1.497500] ata3: SATA max UDMA/133 abar m1024@0xfe6ffc00 port 0xfe6ffe00 irq 41
[    1.497508] ata4: SATA max UDMA/133 abar m1024@0xfe6ffc00 port 0xfe6ffe80 irq 41
[    1.497731] pata_acpi 0000:00:14.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.497768] pata_acpi 0000:00:14.1: setting latency timer to 64
[    1.984145] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.988138] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.992157] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.992753] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.992908] ata4.00: ATA-8: ST2000DL003-9VT166, CC45, max UDMA/133
[    1.992920] ata4.00: 3907029168 sectors, multi 0: LBA48 NCQ (depth 31/32)
[    1.993764] ata4.00: configured for UDMA/133
[    2.007684] ata3.00: ATA-8: WDC WD5000AACS-00ZUB0, 01.01B01, max UDMA/133
[    2.007696] ata3.00: 976773168 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
[    2.008587] ata3.00: configured for UDMA/133
[    2.013473] ata1.00: ATA-8: WDC WD5000AACS-00ZUB0, 01.01B01, max UDMA/133
[    2.013484] ata1.00: 976773168 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
[    2.014376] ata1.00: configured for UDMA/133
[    2.014691] scsi 0:0:0:0: Direct-Access     ATA      WDC WD5000AACS-0 01.0 PQ: 0 ANSI: 5
[    2.367211] ata2.00: ATA-8: WDC WD5000AACS-00ZUB0, 01.01B01, max UDMA/133
[    2.367222] ata2.00: 976773168 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
[    2.368148] ata2.00: configured for UDMA/133
[    2.368422] scsi 1:0:0:0: Direct-Access     ATA      WDC WD5000AACS-0 01.0 PQ: 0 ANSI: 5
[    2.368850] scsi 2:0:0:0: Direct-Access     ATA      WDC WD5000AACS-0 01.0 PQ: 0 ANSI: 5
[    2.369132] scsi 3:0:0:0: Direct-Access     ATA      ST2000DL003-9VT1 CC45 PQ: 0 ANSI: 5
[    2.392371] Write protecting the kernel read-only data: 12288k
[    2.537210] scsi4 : pata_atiixp
[    2.538331] scsi5 : pata_atiixp
[    2.539179] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xff00 irq 14
[    2.539187] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xff08 irq 15
[    2.707517] ata5.00: failed to IDENTIFY (device reports invalid type, err_mask=0x0)
[    7.864460] ata5.00: failed to IDENTIFY (device reports invalid type, err_mask=0x0)
[   13.012752] ata5.01: ATA-8: ST2000DL003-9VT166, CC45, max UDMA/133
[   13.012798] ata5.01: 3907029168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   13.012844] ata5.01: limited to UDMA/33 due to 40-wire cable
[   13.028725] ata5.01: configured for UDMA/33
[   13.029033] scsi 4:0:1:0: Direct-Access     ATA      ST2000DL003-9VT1 CC45 PQ: 0 ANSI: 5
[   31.115187] EXT4-fs (dm-11): mounted filesystem with ordered data mode. Opts: (null)
[   38.019304] EXT4-fs (dm-15): mounted filesystem with ordered data mode. Opts: acl
[   38.680499] EXT4-fs (dm-1): mounted filesystem with ordered data mode. Opts: (null)


ll /sys/class/scsi_host/
0 lrwxrwxrwx 1 root root 0 Feb 16 21:46 host0 -> ../../devices/pci0000:00/0000:00:11.0/host0/scsi_host/host0/
0 lrwxrwxrwx 1 root root 0 Feb 16 21:46 host1 -> ../../devices/pci0000:00/0000:00:11.0/host1/scsi_host/host1/
0 lrwxrwxrwx 1 root root 0 Feb 16 21:46 host2 -> ../../devices/pci0000:00/0000:00:11.0/host2/scsi_host/host2/
0 lrwxrwxrwx 1 root root 0 Feb 16 21:46 host3 -> ../../devices/pci0000:00/0000:00:11.0/host3/scsi_host/host3/
0 lrwxrwxrwx 1 root root 0 Feb 16 21:46 host4 -> ../../devices/pci0000:00/0000:00:14.1/host4/scsi_host/host4/
0 lrwxrwxrwx 1 root root 0 Feb 16 21:46 host5 -> ../../devices/pci0000:00/0000:00:14.1/host5/scsi_host/host5/

It seems the following error messages making eSATA not running under 12.04 server
[    2.707517] ata5.00: failed to IDENTIFY (device reports invalid type, err_mask=0x0)
[    7.864460] ata5.00: failed to IDENTIFY (device reports invalid type, err_mask=0x0)

Any thoughts?

---

