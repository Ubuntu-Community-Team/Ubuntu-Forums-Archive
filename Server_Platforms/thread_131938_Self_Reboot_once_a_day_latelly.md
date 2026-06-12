---
title: "Self Reboot once a day latelly"
date: 2006-02-17
forum: Server Platforms
---

### Post by theQmaster on 2006-02-17
Hello All,

I'm experiencing this annoyance on my machine Ubuntu Hoary with the lastest patches. Once in a while once or many times a day the server self reboots, gracefully true but it reboots an I have no idea why. This machine is a server so runs all day long.

I get a mail in my mail box, I'm paste  it here below. 


[SIZE="1"]From [email]logcheck@localhost.loca[/email]ldomain  Fri Feb 17 06:42:22 2006
Return-Path: <logcheck@localhost.localdomain>
X-Original-To: root
Delivered-To: [email]mc@localhost.loca[/email]ldomain
Received: by localhost.localdomain (Postfix, from userid 116)
    id 48F2B83C4AF; Fri, 17 Feb 2006 06:42:21 -0600 (CST)
To: [email]root@localhost.loca[/email]ldomain
Subject:** Reboot: localhost 2006-02-17 06:41 Security Events**
Message-Id: <20060217124221.48F2B83C4AF@localhost.localdomain>
Date: Fri, 17 Feb 2006 06:42:21 -0600 (CST)
From: [email]logcheck@localhost.loca[/email]ldomain
Status: RO
Content-Length: 22436
Lines: 257

This email is sent by logcheck. If you wish to no-longer receive it,
you can either deinstall the logcheck package or modify its
configuration file (/etc/logcheck/logcheck.conf).

Security Events
=-=-=-=-=-=-=-=
Feb 17 06:42:00 zeus perl: (pam_unix) authentication failure; logname= uid=0 euid=0 tty= ruser= rhost=  user=root

System Events
=-=-=-=-=-=-=
Feb 17 06:41:46 zeus syslogd 1.4.1#16ubuntu6: restart.
Feb 17 06:41:46 zeus kernel: Inspecting /boot/System.map-2.6.10-6-686
Feb 17 06:41:46 zeus kernel: Loaded 26814 symbols from /boot/System.map-2.6.10-6-686.
Feb 17 06:41:46 zeus kernel: Symbols match kernel version 2.6.10.
Feb 17 06:41:46 zeus kernel: No module symbols loaded - kernel modules not enabled.
Feb 17 06:41:46 zeus kernel: Linux version 2.6.10-6-686 (buildd@terranova) (gcc version 3.3.5 (Debian 1:3.3.5-8ubuntu2)) #1 Mon Jan 16 18:36:48 UTC 2006
Feb 17 06:41:46 zeus kernel: BIOS-provided physical RAM map:
Feb 17 06:41:46 zeus kernel:  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Feb 17 06:41:46 zeus kernel:  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Feb 17 06:41:46 zeus kernel:  BIOS-e820: 00000000000e6000 - 0000000000100000 (reserved)
Feb 17 06:41:46 zeus kernel:  BIOS-e820: 0000000000100000 - 000000003ffb0000 (usable)
Feb 17 06:41:46 zeus kernel:  BIOS-e820: 000000003ffb0000 - 000000003ffc0000 (ACPI data)
Feb 17 06:41:46 zeus kernel:  BIOS-e820: 000000003ffc0000 - 000000003fff0000 (ACPI NVS)
Feb 17 06:41:46 zeus kernel:  BIOS-e820: 000000003fff0000 - 0000000040000000 (reserved)
Feb 17 06:41:46 zeus kernel:  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
Feb 17 06:41:46 zeus kernel: 127MB HIGHMEM available.
Feb 17 06:41:46 zeus kernel: 896MB LOWMEM available.
Feb 17 06:41:46 zeus kernel: On node 0 totalpages: 262064
Feb 17 06:41:46 zeus kernel:   DMA zone: 4096 pages, LIFO batch:1
Feb 17 06:41:46 zeus kernel:   Normal zone: 225280 pages, LIFO batch:16
Feb 17 06:41:46 zeus kernel:   HighMem zone: 32688 pages, LIFO batch:7
Feb 17 06:41:46 zeus kernel: DMI 2.3 present.
Feb 17 06:41:46 zeus kernel: Built 1 zonelists
Feb 17 06:41:46 zeus kernel: Kernel command line: root=/dev/sda1 ro quiet splash acpi=off
Feb 17 06:41:46 zeus kernel: Found and enabled local APIC!
Feb 17 06:41:46 zeus kernel: mapped APIC to ffffd000 (fee00000)
Feb 17 06:41:46 zeus kernel: Initializing CPU#0
Feb 17 06:41:46 zeus kernel: PID hash table entries: 4096 (order: 12, 65536 bytes)
Feb 17 06:41:46 zeus kernel: Detected 2084.378 MHz processor.
Feb 17 06:41:46 zeus kernel: Using tsc for high-res timesource
Feb 17 06:41:46 zeus kernel: Console: colour VGA+ 80x25
Feb 17 06:41:46 zeus kernel: Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Feb 17 06:41:46 zeus kernel: Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Feb 17 06:41:46 zeus kernel: Memory: 1031280k/1048256k available (1588k kernel code, 16308k reserved, 713k data, 164k init, 130752k highmem)
Feb 17 06:41:46 zeus kernel: Checking if this processor honours the WP bit even in supervisor mode... Ok.
Feb 17 06:41:46 zeus kernel: Calibrating delay loop... 4087.80 BogoMIPS (lpj=2043904)
Feb 17 06:41:46 zeus kernel: Security Framework v1.0.0 initialized
Feb 17 06:41:46 zeus kernel: SELinux:  Disabled at boot.
Feb 17 06:41:46 zeus kernel: Mount-cache hash table entries: 512 (order: 0, 4096 bytes)
Feb 17 06:41:46 zeus kernel: CPU: After generic identify, caps: 0383fbff c1c3fbff 00000000 00000000 00000000 00000000
Feb 17 06:41:46 zeus kernel: CPU: After vendor identify, caps: 0383fbff c1c3fbff 00000000 00000000 00000000 00000000
Feb 17 06:41:46 zeus kernel: CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Feb 17 06:41:46 zeus kernel: CPU: L2 Cache: 512K (64 bytes/line)
Feb 17 06:41:46 zeus kernel: CPU: After all inits, caps: 0383fbff c1c3fbff 00000000 00000020 00000000 00000000
Feb 17 06:41:46 zeus kernel: Intel machine check architecture supported.
Feb 17 06:41:46 zeus kernel: Intel machine check reporting enabled on CPU#0.
Feb 17 06:41:46 zeus kernel: CPU: AMD Athlon(tm) XP 2800+ stepping 00
Feb 17 06:41:46 zeus kernel: Enabling fast FPU save and restore... done.
Feb 17 06:41:46 zeus kernel: Enabling unmasked SIMD FPU exception support... done.
Feb 17 06:41:46 zeus kernel: Checking 'hlt' instruction... OK.
Feb 17 06:41:46 zeus kernel: checking if image is initramfs...it isn't (bad gzip magic numbers); looks like an initrd
Feb 17 06:41:46 zeus kernel: Freeing initrd memory: 4528k freed
Feb 17 06:41:46 zeus kernel: NET: Registered protocol family 16
Feb 17 06:41:46 zeus kernel: PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=1
Feb 17 06:41:46 zeus kernel: PCI: Using configuration type 1
Feb 17 06:41:46 zeus kernel: mtrr: v2.0 (20020519)
Feb 17 06:41:46 zeus kernel: ACPI: Subsystem revision 20050211
Feb 17 06:41:46 zeus kernel: ACPI: Interpreter disabled.
Feb 17 06:41:46 zeus kernel: Linux Plug and Play Support v0.97 (c) Adam Belay
Feb 17 06:41:46 zeus kernel: pnp: PnP ACPI: disabled
Feb 17 06:41:46 zeus kernel: PnPBIOS: Scanning system for PnP BIOS support...
Feb 17 06:41:46 zeus kernel: PnPBIOS: Found PnP BIOS installation structure at 0xc00f8af0
Feb 17 06:41:46 zeus kernel: PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0x48ba, dseg 0xf0000
Feb 17 06:41:46 zeus kernel: PnPBIOS: Missing SMALL_TAG_ENDDEP tag
Feb 17 06:41:46 zeus kernel: PnPBIOS: 16 nodes reported by PnP BIOS; 16 recorded by driver
Feb 17 06:41:46 zeus kernel: PCI: Probing PCI hardware
Feb 17 06:41:46 zeus kernel: PCI: Probing PCI hardware (bus 00)
Feb 17 06:41:46 zeus kernel: PCI: Via IRQ fixup
Feb 17 06:41:46 zeus kernel: PCI: Using IRQ router default [1106/3227] at 0000:00:11.0
Feb 17 06:41:46 zeus kernel: PCI: IRQ 0 for device 0000:00:0f.1 doesn't match PIRQ mask - try pci=usepirqmask
Feb 17 06:41:46 zeus kernel: pnp: 00:0b: ioport range 0x290-0x297 has been reserved
Feb 17 06:41:46 zeus kernel: pnp: 00:0c: ioport range 0x4d0-0x4d1 has been reserved
Feb 17 06:41:46 zeus kernel: pnp: 00:0c: ioport range 0xcf8-0xcff could not be reserved
Feb 17 06:41:46 zeus kernel: pnp: 00:0c: ioport range 0x290-0x2cf could not be reserved
Feb 17 06:41:46 zeus kernel: audit: initializing netlink socket (disabled)
Feb 17 06:41:46 zeus kernel: audit(1140180079.219:0): initialized
Feb 17 06:41:46 zeus kernel: highmem bounce pool size: 64 pages
Feb 17 06:41:46 zeus kernel: VFS: Disk quotas dquot_6.5.1
Feb 17 06:41:46 zeus kernel: Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Feb 17 06:41:46 zeus kernel: devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
Feb 17 06:41:46 zeus kernel: devfs: boot_options: 0x0
Feb 17 06:41:46 zeus kernel: Initializing Cryptographic API
Feb 17 06:41:46 zeus kernel: isapnp: Scanning for PnP cards...
Feb 17 06:41:46 zeus kernel: spurious 8259A interrupt: IRQ7.
Feb 17 06:41:46 zeus kernel: isapnp: No Plug & Play device found
Feb 17 06:41:46 zeus kernel: serio: i8042 AUX port at 0x60,0x64 irq 12
Feb 17 06:41:46 zeus kernel: serio: i8042 KBD port at 0x60,0x64 irq 1
Feb 17 06:41:46 zeus kernel: Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
Feb 17 06:41:46 zeus kernel: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Feb 17 06:41:46 zeus kernel: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Feb 17 06:41:46 zeus kernel: io scheduler noop registered
Feb 17 06:41:46 zeus kernel: io scheduler anticipatory registered
Feb 17 06:41:46 zeus kernel: io scheduler deadline registered
Feb 17 06:41:46 zeus kernel: io scheduler cfq registered
Feb 17 06:41:46 zeus kernel: RAMDISK driver initialized: 16 RAM disks of 8192K size 1024 blocksize
Feb 17 06:41:46 zeus kernel: NET: Registered protocol family 2
Feb 17 06:41:46 zeus kernel: IP: routing cache hash table of 8192 buckets, 64Kbytes
Feb 17 06:41:46 zeus kernel: TCP: Hash tables configured (established 262144 bind 65536)
Feb 17 06:41:46 zeus kernel: NET: Registered protocol family 8
Feb 17 06:41:46 zeus kernel: NET: Registered protocol family 20
Feb 17 06:41:46 zeus kernel: Restarting tasks...<6> Strange, kswapd0 not stopped
Feb 17 06:41:46 zeus kernel:  Strange, kpnpbiosd not stopped
Feb 17 06:41:46 zeus kernel:  Strange, kseriod not stopped
Feb 17 06:41:46 zeus kernel:  done
Feb 17 06:41:46 zeus kernel: RAMDISK: cramfs filesystem found at block 0
Feb 17 06:41:46 zeus kernel: RAMDISK: Loading 4528KiB [1 disk] into ram disk... |^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^H\^H|^H/^H-^Hdone.
Feb 17 06:41:46 zeus kernel: VFS: Mounted root (cramfs filesystem) readonly.
Feb 17 06:41:46 zeus kernel: Freeing unused kernel memory: 164k freed
Feb 17 06:41:46 zeus kernel: NET: Registered protocol family 1
Feb 17 06:41:46 zeus kernel: SCSI subsystem initialized
Feb 17 06:41:46 zeus kernel: libata version 1.10 loaded.
Feb 17 06:41:46 zeus kernel: sata_via version 1.1
Feb 17 06:41:46 zeus kernel: sata_via(0000:00:0f.0): routed to hard irq line 10
Feb 17 06:41:46 zeus kernel: ata1: SATA max UDMA/133 cmd 0xEC00 ctl 0xE802 bmdma 0xDC00 irq 10
Feb 17 06:41:46 zeus kernel: ata2: SATA max UDMA/133 cmd 0xE400 ctl 0xE002 bmdma 0xDC08 irq 10
Feb 17 06:41:46 zeus kernel: ata1: dev 0 cfg 49:2f00 82:706b 83:7e01 84:4023 85:7069 86:3c01 87:4023 88:407f
Feb 17 06:41:46 zeus kernel: ata1: dev 0 ATA, max UDMA/133, 156301488 sectors: lba48
Feb 17 06:41:46 zeus kernel: ata1: dev 0 configured for UDMA/133
Feb 17 06:41:46 zeus kernel: scsi0 : sata_via
Feb 17 06:41:46 zeus kernel: ata2: no device found (phy stat 00000000)
Feb 17 06:41:46 zeus kernel: scsi1 : sata_via
Feb 17 06:41:46 zeus kernel: elevator: using anticipatory as default io scheduler
Feb 17 06:41:46 zeus kernel:   Vendor: ATA       Model: WDC WD800JD-00LU  Rev: 06.0
Feb 17 06:41:46 zeus kernel:   Type:   Direct-Access                      ANSI SCSI revision: 05
Feb 17 06:41:46 zeus kernel: SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
Feb 17 06:41:46 zeus kernel: SCSI device sda: drive cache: write back
Feb 17 06:41:46 zeus kernel: SCSI device sda: 156301488 512-byte hdwr sectors (80026 MB)
Feb 17 06:41:46 zeus kernel: SCSI device sda: drive cache: write back
Feb 17 06:41:46 zeus kernel:  /dev/scsi/host0/bus0/target0/lun0: p1 p2 < p5 >
Feb 17 06:41:46 zeus kernel: Attached scsi disk sda at scsi0, channel 0, id 0, lun 0
Feb 17 06:41:46 zeus kernel: Stopping tasks: ==|
Feb 17 06:41:46 zeus kernel: Freeing memory...  ^H-^H\^H|^H/^Hdone (392 pages freed)
Feb 17 06:41:46 zeus kernel: Restarting tasks... done
Feb 17 06:41:46 zeus kernel: EXT3-fs: INFO: recovery required on readonly filesystem.
Feb 17 06:41:46 zeus kernel: EXT3-fs: write access will be enabled during recovery.
Feb 17 06:41:46 zeus kernel: EXT3-fs: sda1: orphan cleanup on readonly fs
Feb 17 06:41:46 zeus kernel: kjournald starting.  Commit interval 5 seconds
Feb 17 06:41:46 zeus kernel: ext3_orphan_cleanup: deleting unreferenced inode 8650858
Feb 17 06:41:46 zeus kernel: EXT3-fs: sda1: 1 orphan inode deleted
Feb 17 06:41:46 zeus kernel: EXT3-fs: recovery complete.
Feb 17 06:41:46 zeus kernel: EXT3-fs: mounted filesystem with ordered data mode.
Feb 17 06:41:46 zeus kernel: Adding 2650684k swap on /dev/sda5.  Priority:-1 extents:1
Feb 17 06:41:46 zeus kernel: EXT3 FS on sda1, internal journal
Feb 17 06:41:46 zeus kernel: Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Feb 17 06:41:46 zeus kernel: ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Feb 17 06:41:46 zeus kernel: Probing IDE interface ide0...
Feb 17 06:41:46 zeus kernel: Probing IDE interface ide1...
Feb 17 06:41:46 zeus kernel: hdc: Hewlett-Packard CD-Writer Plus 9300, ATAPI CD/DVD-ROM drive
Feb 17 06:41:46 zeus kernel: Probing IDE interface ide2...
Feb 17 06:41:46 zeus kernel: Probing IDE interface ide3...
Feb 17 06:41:46 zeus kernel: Probing IDE interface ide4...
Feb 17 06:41:46 zeus kernel: Probing IDE interface ide5...
Feb 17 06:41:46 zeus kernel: ide1 at 0x170-0x177,0x376 on irq 15
Feb 17 06:41:46 zeus kernel: hdc: ATAPI 32X CD-ROM CD-R/RW drive, 4096kB Cache
Feb 17 06:41:46 zeus kernel: Uniform CD-ROM driver Revision: 3.20
Feb 17 06:41:46 zeus kernel: parport: PnPBIOS parport detected.
Feb 17 06:41:46 zeus kernel: parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
Feb 17 06:41:46 zeus kernel: lp0: using parport0 (interrupt-driven).
Feb 17 06:41:46 zeus kernel: mice: PS/2 mouse device common for all mice
Feb 17 06:41:46 zeus kernel: Linux agpgart interface v0.100 (c) Dave Jones
Feb 17 06:41:46 zeus kernel: nvidia: module license 'NVIDIA' taints kernel.
Feb 17 06:41:46 zeus kernel: NVRM: loading NVIDIA Linux x86 NVIDIA Kernel Module  1.0-7174  Tue Mar 22 06:44:39 PST 2005
Feb 17 06:41:46 zeus kernel: Capability LSM initialized
Feb 17 06:41:46 zeus kernel: device-mapper: 4.3.0-ioctl (2004-09-30) initialised: [email]dm-devel@redhat.com[/email]
Feb 17 06:41:46 zeus kernel: md: md driver 0.90.1 MAX_MD_DEVS=256, MD_SB_DISKS=27
Feb 17 06:41:46 zeus kernel: Real Time Clock Driver v1.12
Feb 17 06:41:46 zeus kernel: input: PC Speaker
Feb 17 06:41:46 zeus kernel: inserting floppy driver for 2.6.10-6-686
Feb 17 06:41:46 zeus kernel: Floppy drive(s): fd0 is 1.44M
Feb 17 06:41:46 zeus kernel: FDC 0 is a post-1991 82077
Feb 17 06:41:46 zeus kernel: agpgart: Detected VIA KT880 chipset
Feb 17 06:41:46 zeus kernel: agpgart: Maximum main memory to use for agp memory: 941M
Feb 17 06:41:46 zeus kernel: agpgart: AGP aperture is 64M @ 0xe0000000
Feb 17 06:41:46 zeus kernel: cpci_hotplug: CompactPCI Hot Plug Core version: 0.2
Feb 17 06:41:46 zeus kernel: pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Feb 17 06:41:46 zeus kernel: shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x1001
Feb 17 06:41:46 zeus kernel: pciehp: acpi_pciehprm:get_device PCI ROOT HID fail=0x1001
Feb 17 06:41:46 zeus kernel: VP_IDE: IDE controller at PCI slot 0000:00:0f.1
Feb 17 06:41:46 zeus kernel: PCI: IRQ 0 for device 0000:00:0f.1 doesn't match PIRQ mask - try pci=usepirqmask
Feb 17 06:41:46 zeus kernel: VP_IDE: chipset revision 6
Feb 17 06:41:46 zeus kernel: VP_IDE: not 100%% native mode: will probe irqs later
Feb 17 06:41:46 zeus kernel: VP_IDE: VIA vt8237 (rev 00) IDE UDMA133 controller on pci0000:00:0f.1
Feb 17 06:41:46 zeus kernel:     ide0: BM-DMA at 0xfc00-0xfc07, BIOS settings: hda:pio, hdb:pio
Feb 17 06:41:46 zeus kernel: VP_IDE: port 0x0170 already claimed by ide1
Feb 17 06:41:46 zeus kernel: Probing IDE interface ide0...
Feb 17 06:41:46 zeus kernel: usbcore: registered new driver usbfs
Feb 17 06:41:46 zeus kernel: usbcore: registered new driver hub
Feb 17 06:41:46 zeus kernel: USB Universal Host Controller Interface driver v2.2
Feb 17 06:41:46 zeus kernel: uhci_hcd 0000:00:10.0: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
Feb 17 06:41:46 zeus kernel: uhci_hcd 0000:00:10.0: irq 11, io base 0xc000
Feb 17 06:41:46 zeus kernel: uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
Feb 17 06:41:46 zeus kernel: hub 1-0:1.0: USB hub found
Feb 17 06:41:46 zeus kernel: hub 1-0:1.0: 2 ports detected
Feb 17 06:41:46 zeus kernel: uhci_hcd 0000:00:10.1: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (#2)
Feb 17 06:41:46 zeus kernel: uhci_hcd 0000:00:10.1: irq 11, io base 0xc400
Feb 17 06:41:46 zeus kernel: uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
Feb 17 06:41:46 zeus kernel: hub 2-0:1.0: USB hub found
Feb 17 06:41:46 zeus kernel: hub 2-0:1.0: 2 ports detected
Feb 17 06:41:46 zeus kernel: uhci_hcd 0000:00:10.2: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (#3)
Feb 17 06:41:46 zeus kernel: uhci_hcd 0000:00:10.2: irq 10, io base 0xc800
Feb 17 06:41:46 zeus kernel: uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
Feb 17 06:41:46 zeus kernel: hub 3-0:1.0: USB hub found
Feb 17 06:41:46 zeus kernel: hub 3-0:1.0: 2 ports detected
Feb 17 06:41:46 zeus kernel: uhci_hcd 0000:00:10.3: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (#4)
Feb 17 06:41:46 zeus kernel: uhci_hcd 0000:00:10.3: irq 10, io base 0xcc00
Feb 17 06:41:46 zeus kernel: uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
Feb 17 06:41:46 zeus kernel: hub 4-0:1.0: USB hub found
Feb 17 06:41:46 zeus kernel: hub 4-0:1.0: 2 ports detected
Feb 17 06:41:46 zeus kernel: ehci_hcd 0000:00:10.4: VIA Technologies, Inc. USB 2.0
Feb 17 06:41:46 zeus kernel: ehci_hcd 0000:00:10.4: irq 5, pci mem 0xfebff800
Feb 17 06:41:46 zeus kernel: ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 5
Feb 17 06:41:46 zeus kernel: ehci_hcd 0000:00:10.4: USB 2.0 initialized, EHCI 1.00, driver 26 Oct 2004
Feb 17 06:41:46 zeus kernel: hub 5-0:1.0: USB hub found
Feb 17 06:41:46 zeus kernel: hub 5-0:1.0: 8 ports detected
Feb 17 06:41:46 zeus kernel: via82xx: Assuming DXS channels with 48k fixed sample rate.
Feb 17 06:41:46 zeus kernel:          Please try dxs_support=1 or dxs_support=4 option
Feb 17 06:41:46 zeus kernel:          and report if it works on your machine.
Feb 17 06:41:46 zeus kernel: PCI: Setting latency timer of device 0000:00:11.5 to 64
Feb 17 06:41:46 zeus kernel: via-rhine.c:v1.10-LK1.2.0-2.6 June-10-2004 Written by Donald Becker
Feb 17 06:41:46 zeus kernel: eth0: VIA Rhine II at 0xd400, 00:0b:6a:b7:c6:dc, IRQ 11.
Feb 17 06:41:46 zeus kernel: eth0: MII PHY found at address 1, status 0x786d advertising 05e1 Link 45e1.
Feb 17 06:41:46 zeus kernel: eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Feb 17 06:41:46 zeus kernel: apm: BIOS not found.
Feb 17 06:41:46 zeus authdaemond.plain: modules="authpam", daemons=5
Feb 17 06:41:48 zeus postfix/master[5550]: daemon started -- version 2.1.5
Feb 17 06:41:55 zeus sshd[5842]: Server listening on 0.0.0.0 port 5678.
Feb 17 06:41:57 zeus anacron[5883]: Anacron 2.3 started on 2006-02-17
Feb 17 06:41:57 zeus anacron[5883]: Will run job `cron.daily' in 5 min.
Feb 17 06:41:57 zeus anacron[5883]: Jobs will be executed sequentially
Feb 17 06:41:57 zeus udev[5895]: creating device node '/dev/vcs7'
Feb 17 06:41:57 zeus udev[5897]: creating device node '/dev/vcsa7'
Feb 17 06:42:01 zeus udev[6017]: removing device node '/dev/vcs1'
Feb 17 06:42:01 zeus udev[6023]: removing device node '/dev/vcsa1'
Feb 17 06:42:01 zeus udev[6043]: creating device node '/dev/vcs1'
Feb 17 06:42:01 zeus udev[6045]: creating device node '/dev/vcsa1'
Feb 17 06:42:01 zeus udev[6047]: creating device node '/dev/vcs2'
Feb 17 06:42:01 zeus udev[6049]: creating device node '/dev/vcsa2'
Feb 17 06:42:01 zeus udev[6051]: creating device node '/dev/vcs3'
Feb 17 06:42:01 zeus udev[6053]: creating device node '/dev/vcsa3'
Feb 17 06:42:01 zeus udev[6057]: creating device node '/dev/vcs5'
Feb 17 06:42:01 zeus udev[6059]: creating device node '/dev/vcsa4'
Feb 17 06:42:01 zeus udev[6061]: creating device node '/dev/vcsa5'
Feb 17 06:42:01 zeus udev[6063]: creating device node '/dev/vcs6'
Feb 17 06:42:01 zeus udev[6065]: creating device node '/dev/vcsa6'
Feb 17 06:42:01 zeus udev[6055]: creating device node '/dev/vcs4'
Feb 17 06:42:02 zeus webmin[5868]: Webmin starting
[/SIZE]

---

### Post by theQmaster on 2006-02-17
I can directly link each of these restarts with 2 entries in miniserver.error file

[17/Feb/2006:06:42:02 -0600] miniserv.pl started
[17/Feb/2006:06:42:02 -0600] PAM authentication enabled

Any clue ?

---

### Post by fguilhon on 2006-10-27
I once have a problem like this. The machine self rebooting with no reason...
It turned out to be a memory problem. Not sure if that's your case... but if in doubt, you should check with memtest.

---

