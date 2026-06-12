---
title: "Issues Connecting DLP-RFID1 (USB RFID Reader/Writer) in RFDump / RFIDIOt"
date: 2008-02-19
forum: Security Discussions
---

### Post by JKX on 2008-02-19
I'm a computer security student doing research on RFID and am currently trying to conduct some tests on RFID hardware/software.

I'm running Ubuntu 7.10 and I'm using DLP-RFID1, which is an RFID reader/writer from DLP Designs. The issue is that I'm having difficulty with, is getting the DLP-RFID1 to connect to the programs that I want to use. RFDump and RFIDIOt. To start off, Ubuntu knows that the device is connected. It comes up when I do an 'lsusb'. Also, after reading around I found out that after 2.6.9 the drivers are auto installed. So I don't think this is the issue either..

After reading the READMEs and checking the default configs and preferences it seems that the programs  want to connect to /dev/ttyS1. The DLP-RFID1 is a USB device. In the READMEs it was suggested to use /dev/ttyUSB0 for a USB reader/writer device. This doesn't work. There are also other USB# I have in my /dev which I have tried and they don't work either.

At that point my next step was to try the device manager and I got many directory paths for the USB device. The /dev dir lead me to /dev/bus/001/002 and using this as a path dir to the device didn't get it to work with the programs either. 

After doing a lot of looking around online for answers I have come up short. If anyone could give me a direction to do in or any straight answers I would appreciate it greatly !!

If you require any more info please ask and I will not hesitate to give !!

Sincerely,

JKX

---

### Post by JKX on 2008-02-19
**_UPDATE:_** Here is some more information for anyone who might be able to help!
[B]
This is the output from an "lsusb" command:[/B]

Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 0e0f:0002  
Bus 002 Device 002: ID 0403:fbfc Future Technology Devices International, Ltd 
Bus 002 Device 001: ID 0000:0000 

The device also operates on the  "ftdi_sio.tar.gz" driver.

**The output from a "dmesg":**

[    0.000000] Linux version 2.6.22-14-generic (buildd@terranova) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Tue Feb 12 07:42:25 UTC 2008 (Ubuntu 2.6.22-14.52-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000ca000 - 00000000000cc000 (reserved)
[    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001fef0000 (usable)
[    0.000000]  BIOS-e820: 000000001fef0000 - 000000001feff000 (ACPI data)
[    0.000000]  BIOS-e820: 000000001feff000 - 000000001ff00000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000001ff00000 - 0000000020000000 (usable)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fffe0000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 512MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f6c90
[    0.000000] Entering add_active_range(0, 0, 131072) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   131072
[    0.000000]   HighMem    131072 ->   131072
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   131072
[    0.000000] On node 0 totalpages: 131072
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 992 pages used for memmap
[    0.000000]   Normal zone: 125984 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP signature @ 0xC00F6C20 checksum 0
[    0.000000] ACPI: RSDP 000F6C20, 0014 (r0 PTLTD )
[    0.000000] ACPI: RSDT 1FEFAB5A, 0030 (r1 PTLTD    RSDT    6040000  LTP        0)
[    0.000000] ACPI: FACP 1FEFEF06, 0074 (r1 INTEL  440BX     6040000 PTL     F4240)
[    0.000000] ACPI: DSDT 1FEFAB8A, 437C (r1 PTLTD  Custom    6040000 MSFT  100000D)
[    0.000000] ACPI: FACS 1FEFFFC0, 0040
[    0.000000] ACPI: APIC 1FEFEF7A, 005E (r1 PTLTD       APIC    6040000  LTP        0)
[    0.000000] ACPI: BOOT 1FEFEFD8, 0028 (r1 PTLTD  $SBFTBL$  6040000  LTP        1)
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:14 APIC version 17
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1 6:14 APIC version 17
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:dec00000)
[    0.000000] Built 1 zonelists.  Total pages: 130048
[    0.000000] Kernel command line: root=UUID=6348b9d1-fa1c-434a-b144-31344a363db4 ro quiet splash
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] Detected 1995.111 MHz processor.
[    9.844262] Console: colour VGA+ 80x25
[    9.845120] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[    9.845861] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[    9.846719] Memory: 508300k/524288k available (2015k kernel code, 15444k reserved, 915k data, 364k init, 0k highmem)
[    9.846762] virtual kernel memory layout:
[    9.846766]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[    9.846768]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    9.846772]     vmalloc : 0xe0800000 - 0xff7fe000   ( 495 MB)
[    9.846774]     lowmem  : 0xc0000000 - 0xe0000000   ( 512 MB)
[    9.846775]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[    9.846777]       .data : 0xc02f7e86 - 0xc03dce84   ( 915 kB)
[    9.846778]       .text : 0xc0100000 - 0xc02f7e86   (2015 kB)
[    9.846857] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[    9.847714] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[    9.928297] Calibrating delay using timer specific routine.. 3997.28 BogoMIPS (lpj=7994569)
[    9.928359] Security Framework v1.0.0 initialized
[    9.928421] SELinux:  Disabled at boot.
[    9.928484] Mount-cache hash table entries: 512
[    9.928546] CPU: After generic identify, caps: 0fe9fbff 00100000 00000000 00000000 00000001 00000000 00000000
[    9.928609] CPU: L1 I cache: 32K, L1 D cache: 32K
[    9.928640] CPU: L2 cache: 2048K
[    9.928702] CPU: After all inits, caps: 0fe9fbff 00100000 00000000 00003940 00000001 00000000 00000000
[    9.928765] Compat vDSO mapped to ffffe000.
[    9.928827] Checking 'hlt' instruction... OK.
[    9.944274] SMP alternatives: switching to UP code
[    9.944336] Early unpacking initramfs... done
[   10.232120] ACPI: Core revision 20070126
[   10.232182] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   10.232495] CPU0: Intel(R) Core(TM) Duo CPU      T2450  @ 2.00GHz stepping 08
[   10.232716] SMP alternatives: switching to SMP code
[   10.236172] Booting processor 1/1 eip 3000
[   10.247612] Initializing CPU#1
[   10.324097] Calibrating delay using timer specific routine.. 3991.34 BogoMIPS (lpj=7982691)
[   10.324580] CPU: After generic identify, caps: 0fe9fbff 00100000 00000000 00000000 00000001 00000000 00000000
[   10.324833] CPU: L1 I cache: 32K, L1 D cache: 32K
[   10.324863] CPU: L2 cache: 2048K
[   10.325069] CPU: After all inits, caps: 0fe9fbff 00100000 00000000 00003940 00000001 00000000 00000000
[   10.325726] CPU1: Intel(R) Core(TM) Duo CPU      T2450  @ 2.00GHz stepping 08
[   10.325789] Total of 2 processors activated (7988.63 BogoMIPS).
[   10.325851] ENABLING IO-APIC IRQs
[   10.326076] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   10.473539] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[   10.495532] Brought up 2 CPUs
[   10.556059] migration_cost=1571
[   10.558031] Booting paravirtualized kernel on bare hardware
[   10.558156] Time: 17:32:59  Date: 01/19/108
[   10.558218] NET: Registered protocol family 16
[   10.560510] EISA bus registered
[   10.560573] ACPI: bus type pci registered
[   10.560635] PCI: PCI BIOS revision 2.10 entry at 0xfd9a0, last bus=2
[   10.560674] PCI: Using configuration type 1
[   10.560726] Setting up standard PCI resources
[   10.568060] ACPI: EC: Look up EC in DSDT
[   10.584051] ACPI: Interpreter enabled
[   10.584084] ACPI: (supports S0 S1 S4 S5)
[   10.584147] ACPI: Using IOAPIC for interrupt routing
[   10.601018] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   10.601081] PCI: Probing PCI hardware (bus 00)
[   10.604056] PCI quirk: region 1000-103f claimed by PIIX4 ACPI
[   10.604096] PCI quirk: region 1040-104f claimed by PIIX4 SMB
[   10.608096] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   10.610005] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 6 7 9 10 11 14 15)
[   10.610068] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 *11 14 15)
[   10.610130] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 *10 11 14 15)
[   10.610193] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 *9 10 11 14 15)
[   10.614322] Linux Plug and Play Support v0.97 (c) Adam Belay
[   10.614368] pnp: PnP ACPI init
[   10.614430] ACPI: bus type pnp registered
[   10.640491] pnp: PnP ACPI: found 12 devices
[   10.640542] ACPI: ACPI bus type pnp unregistered
[   10.640605] PnPBIOS: Disabled by ACPI PNP
[   10.640783] PCI: Using ACPI for IRQ routing
[   10.640845] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   10.660014] NET: Registered protocol family 8
[   10.660030] NET: Registered protocol family 20
[   10.664032] Time: tsc clocksource has been installed.
[   10.691999] PCI: Bridge: 0000:00:01.0
[   10.692017]   IO window: disabled.
[   10.692080]   MEM window: disabled.
[   10.692137]   PREFETCH window: disabled.
[   10.692200] PCI: Bridge: 0000:00:11.0
[   10.692240]   IO window: 2000-2fff
[   10.692282]   MEM window: e8900000-e89fffff
[   10.692316]   PREFETCH window: 30000000-300fffff
[   10.692378] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   10.692441] ACPI: PCI Interrupt 0000:00:11.0[A] -> GSI 18 (level, low) -> IRQ 16
[   10.692503] NET: Registered protocol family 2
[   10.731992] IP route cache hash table entries: 16384 (order: 4, 65536 bytes)
[   10.732055] TCP established hash table entries: 65536 (order: 7, 786432 bytes)
[   10.732117] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   10.732180] TCP: Hash tables configured (established 65536 bind 65536)
[   10.732242] TCP reno registered
[   10.743999] checking if image is initramfs... it is
[   11.075848] Freeing initrd memory: 7034k freed
[   11.076193] Simple Boot Flag at 0x36 set to 0x1
[   11.080131] audit: initializing netlink socket (disabled)
[   11.080193] audit(1203442376.696:1): initialized
[   11.086347] VFS: Disk quotas dquot_6.5.1
[   11.086547] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   11.087973] io scheduler noop registered
[   11.088000] io scheduler anticipatory registered
[   11.088007] io scheduler deadline registered
[   11.088070] io scheduler cfq registered (default)
[   11.088374] Limiting direct PCI/PCI transfers.
[   11.088506] Boot video device is 0000:00:0f.0
[   11.089983] isapnp: Scanning for PnP cards...
[   11.190102] Switched to high resolution mode on CPU 1
[   11.195112] Switched to high resolution mode on CPU 0
[   11.444282] isapnp: No Plug & Play device found
[   11.487886] Real Time Clock Driver v1.12ac
[   11.488117] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   11.491556] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   11.491755] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   11.492380] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   11.492747] 00:0a: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   11.494074] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   11.495655] input: Macintosh mouse button emulation as /class/input/input0
[   11.495903] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:MOUS] at 0x60,0x64 irq 1,12
[   12.002813] serio: i8042 KBD port at 0x60,0x64 irq 1
[   12.002908] serio: i8042 AUX port at 0x60,0x64 irq 12
[   12.003742] mice: PS/2 mouse device common for all mice
[   12.004321] EISA: Probing bus 0 at eisa.0
[   12.004379] Cannot allocate resource for EISA slot 1
[   12.004416] Cannot allocate resource for EISA slot 2
[   12.004473] EISA: Detected 0 cards.
[   12.004531] TCP cubic registered
[   12.004589] NET: Registered protocol family 1
[   12.004647] Using IPI No-Shortcut mode
[   12.004881]   Magic number: 12:682:542
[   12.004939] Freeing unused kernel memory: 364k freed
[   12.005254] input: AT Translated Set 2 keyboard as /class/input/input1
[   13.322599] AppArmor: AppArmor initialized<5>audit(1203442379.196:2):  type=1505 info="AppArmor initialized" pid=1177
[   13.347468] fuse init (API version 7.8)
[   13.363205] Failure registering capabilities with primary security module.
[   13.406669] ACPI: Processor [CPU0] (supports 8 throttling states)
[   13.406775] ACPI: Processor [CPU1] (supports 8 throttling states)
[   13.406861] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
[   13.406947] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
[   13.908089] SCSI subsystem initialized
[   13.910885] Fusion MPT base driver 3.04.04
[   13.910902] Copyright (c) 1999-2007 LSI Logic Corporation
[   13.911469] Fusion MPT SPI Host driver 3.04.04
[   13.911996] ACPI: PCI Interrupt 0000:00:10.0[A] -> GSI 17 (level, low) -> IRQ 17
[   13.912123] mptbase: Initiating ioc0 bringup
[   13.926838] usbcore: registered new interface driver usbfs
[   13.926965] usbcore: registered new interface driver hub
[   13.979139] usbcore: registered new device driver usb
[   13.983025] libata version 2.21 loaded.
[   13.988211] USB Universal Host Controller Interface driver v3.0
[   13.991207] Floppy drive(s): fd0 is 1.44M
[   13.995688] pcnet32.c:v1.33 27.Jun.2006 [email]tsbogend@alpha.franken.de[/email]
[   14.006808] FDC 0 is a post-1991 82077
[   14.030178] ioc0: 53C1030: Capabilities={Initiator}
[   14.158353] scsi0 : ioc0: LSI53C1030, FwRev=01032920h, Ports=1, MaxQ=128, IRQ=17
[   14.274056] scsi 0:0:0:0: Direct-Access     VMware,  VMware Virtual S 1.0  PQ: 0 ANSI: 2
[   14.274125]  target0:0:0: Beginning Domain Validation
[   14.274195]  target0:0:0: Domain Validation skipping write tests
[   14.274218]  target0:0:0: Ending Domain Validation
[   14.274288]  target0:0:0: FAST-40 WIDE SCSI 80.0 MB/s ST (25 ns, offset 127)
[   14.280994] ACPI: PCI Interrupt 0000:02:02.0[A] -> GSI 16 (level, low) -> IRQ 18
[   14.281063] ehci_hcd 0000:02:02.0: EHCI Host Controller
[   14.281132] ACPI: PCI Interrupt 0000:00:07.2[D] -> GSI 19 (level, low) -> IRQ 19
[   14.281202] uhci_hcd 0000:00:07.2: UHCI Host Controller
[   14.281271] ehci_hcd 0000:02:02.0: new USB bus registered, assigned bus number 1
[   14.281341] uhci_hcd 0000:00:07.2: new USB bus registered, assigned bus number 2
[   14.281479] PCI: cache line size of 32 is not supported by device 0000:02:02.0
[   14.281509] uhci_hcd 0000:00:07.2: irq 19, io base 0x00001060
[   14.282031] ehci_hcd 0000:02:02.0: irq 18, io mem 0xe8900000
[   14.282100] ehci_hcd 0000:02:02.0: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   14.282838] usb usb2: configuration #1 chosen from 1 choice
[   14.283153] hub 2-0:1.0: USB hub found
[   14.283282] hub 2-0:1.0: 2 ports detected
[   14.291173] sd 0:0:0:0: [sda] 20971520 512-byte hardware sectors (10737 MB)
[   14.291406] sd 0:0:0:0: [sda] Write Protect is off
[   14.291438] sd 0:0:0:0: [sda] Mode Sense: 5d 00 00 00
[   14.291543] sd 0:0:0:0: [sda] Cache data unavailable
[   14.291571] sd 0:0:0:0: [sda] Assuming drive cache: write through
[   14.292105] sd 0:0:0:0: [sda] 20971520 512-byte hardware sectors (10737 MB)
[   14.292254] sd 0:0:0:0: [sda] Write Protect is off
[   14.292259] sd 0:0:0:0: [sda] Mode Sense: 5d 00 00 00
[   14.292328] sd 0:0:0:0: [sda] Cache data unavailable
[   14.292332] sd 0:0:0:0: [sda] Assuming drive cache: write through
[   14.292402]  sda: sda1 sda2 < sda5 >
[   14.335120] sd 0:0:0:0: [sda] Attached SCSI disk
[   14.338411] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   14.390096] usb usb1: configuration #1 chosen from 1 choice
[   14.390330] hub 1-0:1.0: USB hub found
[   14.390514] hub 1-0:1.0: 6 ports detected
[   14.456576] Attempting manual resume
[   14.456614] swsusp: Resume From Partition 8:5
[   14.456632] PM: Checking swsusp image.
[   14.456771] PM: Resume from disk failed.
[   14.486310] kjournald starting.  Commit interval 5 seconds
[   14.486385] EXT3-fs: mounted filesystem with ordered data mode.
[   14.494849] ata_piix 0000:00:07.1: version 2.11
[   14.495053] scsi1 : ata_piix
[   14.495171] scsi2 : ata_piix
[   14.495240] ata1: PATA max UDMA/33 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x00011050 irq 14
[   14.495258] ata2: PATA max UDMA/33 cmd 0x00010170 ctl 0x00010376 bmdma 0x00011058 irq 15
[   14.495474] ata1: port disabled. ignoring.
[   14.806591] ata2.00: ATAPI: VMware Virtual IDE CDROM Drive, 00000001, max UDMA/33
[   14.962067] ata2.00: configured for UDMA/33
[   14.966678] scsi 2:0:0:0: CD-ROM            BT5342M  ZZF932V          1.01 PQ: 0 ANSI: 5
[   14.966750] scsi 2:0:0:0: Attached scsi generic sg1 type 5
[   14.966965] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 18 (level, low) -> IRQ 16
[   14.967109] pcnet32: PCnet/PCI II 79C970A at 0x2000, 00 0c 29 8f f0 9b assigned IRQ 16.
[   14.969648] eth0: registered as PCnet/PCI II 79C970A
[   14.969720] pcnet32: 1 cards_found.
[   32.818947] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   32.843132] shpchp: Unknown symbol acpi_run_oshp
[   32.843204] shpchp: Unknown symbol pci_hp_change_slot_info
[   32.843277] shpchp: Unknown symbol pci_hp_register
[   32.843454] shpchp: Unknown symbol pci_hp_deregister
[   32.843617] shpchp: Unknown symbol acpi_get_hp_params_from_firmware
[   32.867092] input: PC Speaker as /class/input/input2
[   32.980337] Linux agpgart interface v0.102 (c) Dave Jones
[   33.025274] agpgart: Detected an Intel 440BX Chipset.
[   33.029535] agpgart: AGP aperture is 256M @ 0x0
[   33.399516] input: ImPS/2 Generic Wheel Mouse as /class/input/input3
[   33.430017] parport_pc 00:08: reported by Plug and Play ACPI
[   33.431268] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   33.484235] piix4_smbus 0000:00:07.3: Found 0000:00:07.3 device
[   33.484510] piix4_smbus 0000:00:07.3: Host SMBus controller not enabled!
[   33.490452] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   34.058288] sr0: scsi3-mmc drive: 32x/32x cd/rw xa/form2 cdda tray
[   34.058452] Uniform CD-ROM driver Revision: 3.20
[   34.058982] sr 2:0:0:0: Attached scsi CD-ROM sr0
[   36.502962] ACPI: PCI Interrupt 0000:02:01.0[A] -> GSI 19 (level, low) -> IRQ 19
[   38.644233] lp0: using parport0 (interrupt-driven).
[   38.760010] Adding 489940k swap on /dev/sda5.  Priority:-1 extents:1 across:489940k
[   39.272766] EXT3 FS on sda1, internal journal
[   41.300339] No dock devices found.
[   41.437164] input: Power Button (FF) as /class/input/input4
[   41.437643] ACPI: Power Button (FF) [PWRF]
[   41.471408] ACPI: AC Adapter [ACAD] (on-line)
[   43.831147] ppdev: user-space parallel port driver
[   43.931765] eth0: link up
[   44.794022] audit(1203442411.294:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4520 profile="/usr/sbin/cupsd"
[   47.149944] vmmemctl: module license 'unspecified' taints kernel.
[   47.208574] VMware memory control driver initialized
[   47.209869] vmmemctl: started kernel thread pid=4730
[   47.966881] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   47.966950] apm: disabled - APM is not SMP safe.
[   48.765004] Failure registering capabilities with primary security module.
[   49.522223] Bluetooth: Core ver 2.11
[   49.522830] NET: Registered protocol family 31
[   49.522855] Bluetooth: HCI device and connection manager initialized
[   49.522988] Bluetooth: HCI socket layer initialized
[   49.546161] Bluetooth: L2CAP ver 2.8
[   49.546179] Bluetooth: L2CAP socket layer initialized
[   49.654756] Bluetooth: RFCOMM socket layer initialized
[   49.655151] Bluetooth: RFCOMM TTY layer initialized
[   49.655171] Bluetooth: RFCOMM ver 1.8
[   54.286584] NET: Registered protocol family 17
[   61.550545] NET: Registered protocol family 10
[   61.558224] lo: Disabled Privacy Extensions
[   72.178178] eth0: no IPv6 routers present
[  288.012338] usb 2-1: new full speed USB device using uhci_hcd and address 2
[  288.289663] usb 2-1: configuration #1 chosen from 1 choice
[  288.546308] usb 2-2: new full speed USB device using uhci_hcd and address 3
[  288.692711] usb 2-2: configuration #1 chosen from 1 choice
[  288.698426] hub 2-2:1.0: USB hub found
[  288.701939] hub 2-2:1.0: 7 ports detected

Thanks in advance to anyone who can help me out!

---

### Post by JKX on 2008-03-24
I see many people have viewed this topic but no one seems to have an answer or was able to help at all.

I have successfully mapped the device to /dev. It's a rather pain in the @55 solution, but it gets the job done. I will post the walk through to the solution soon in case any one else gets stuck in the same situation.

Cheers,

JKX

---

### Post by Kenny_K on 2008-04-10
I have the same problem and I am interested in how you mapped the usb device to the /dev and got it working. 

Regards,

Kenny

---

### Post by JKX on 2008-04-13
Within the next week or so I will post my findings for you. Just out of curiosities sake what applications are you wanting to use the DLP-RFID1 for?

---

### Post by Kenny_K on 2008-04-14
I would like to play with the reader using linux and also test some tools that are already written for serial devices.

---

### Post by slink3r on 2008-04-29
It's been some time since this thread, I was wondering about your results from the DLP unit.

Did you get it up and operational, and was it in a decent amount of time? On top of that, could you get relevant information such as distance of RFID tag from reader through this unit?

Working on an RFID-related project, hoping to know of more RFID products - preferably ones that have farther ranged read than this one.

-BAF

---

### Post by punkkRFID on 2008-05-16
Hi .. i want know if you had revolve your problem and use without problem DPL-RFID1 with RFDump of RFDump.org , i if you want talk me about version of RFDump use and other ... contact me

---

### Post by sirflipzalot2 on 2008-07-21
I will be a senior in computer science this coming fall and am think about doing something RFID for my senior project. Have you come up with anything progress about your thread? I'd be very interested to hear. :P :guitar: Thanks!

---

