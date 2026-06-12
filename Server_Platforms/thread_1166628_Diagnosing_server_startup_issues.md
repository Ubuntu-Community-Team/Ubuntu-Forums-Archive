---
title: "Diagnosing server startup issues"
date: 2009-05-21
forum: Server Platforms
---

### Post by sp0nge on 2009-05-21
Hello again!

I have an old sony vaio that runs Ubuntu 8.04 Server and has done rather well until a recent restart. I had a brief power outage and had to flip the breakers, when I turned the server back on, it took forever to boot up. At first I thought perhaps the hard drive got fried, but I hooked up a monitor and saw I/O Error messages during startup for about 10 minutes. I couldn't record them because (a) I didn't think of it at the time and (b) it's really a PITA to get a monitor hooked up to it. 

OK, so I was prepared (am prepared) to live with a 12 minute startup time if necessary. Then I was talking to a buddy in passing who said "there has to be a log you can check for that".. but is there? I'm rather new to server admin, which is why it's here in my house while I learn.. but are there logs that record hard drive errors at startup?

---

### Post by Vegan on 2009-05-21
You might have a damaged disk. My own server's disk fried and I often find myself at clients with fried disks.

Anything with moving parts is vulnerable. My antique IBM server has seen 5 disks over the years. Each year they are bigger and cheaper but the old IBM still boots.

Even with a spare junk disk the server runs, a testament to a 10 year old disk (Fujitsu) that still is error free.

I have disassembled a lot of dead notebooks. One that was fumbled gave up RAM, disk, dvd and a Windows License. The disk made it and still works. The motherboard was cracked.

The power supply on notebooks is not very sophisticated. Still it should not cause harm. Try replacing the disk and install Linux fresh and see if that helps.

---

### Post by lykwydchykyn on 2009-05-22
I believe that stuff should be in the output of dmesg.  Also check /var/log/kern.log.

---

### Post by apel_2804 on 2009-05-22
yes check and/or post your ```
dmesg
``` output and your ```
/var/log/messages
```

---

### Post by andyrowe on 2009-05-22
My understanding (and I'm new to Linux) is that Linux doesn't write data to the disc right away and caches data and writes it later to help the machine run faster. So... unexpected shutdowns can corupt the data on the hard drive. that is probably what all the I/O errors are about. Gurus feel free to correct me if I'm wrong

---

### Post by sp0nge on 2009-05-22
Honestly, I'm hoping to avoid having to rebuild the machine. While I'm prepared to do so, I have jumped to the conclusion of a bad drive too often and I simply don't want to accept that the hard drive goes bad with the little use it's gotten over time. But I suppose anything is possible.

The output follows:
```
dmesg:
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-23-server (buildd@vernadsky) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Mon Jan 26 00:55:21 UTC 2009 (Ubuntu 2.6.24-23.48-server)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 00000000000a0000 (usable)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001fffc000 (usable)
[    0.000000]  BIOS-e820: 000000001fffc000 - 000000001ffff000 (ACPI data)
[    0.000000]  BIOS-e820: 000000001ffff000 - 0000000020000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 511MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 131068) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   131068
[    0.000000]   HighMem    131068 ->   131068
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   131068
[    0.000000] On node 0 totalpages: 131068
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 991 pages used for memmap
[    0.000000]   Normal zone: 125981 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F5B30 checksum 0
[    0.000000] ACPI: RSDP 000F5B30, 0014 (r0 ASUS  )
[    0.000000] ACPI: RSDT 1FFFC000, 002C (r1 ASUS   CUSL-LV  30303031 MSFT 31313031)
[    0.000000] ACPI: FACP 1FFFC080, 0074 (r1 ASUS   CUSL-LV  30303031 MSFT 31313031)
[    0.000000] ACPI: DSDT 1FFFC100, 28E5 (r1   ASUS CUSL-LV      1000 MSFT  100000B)
[    0.000000] ACPI: FACS 1FFFF000, 0040
[    0.000000] ACPI: BOOT 1FFFC040, 0028 (r1 ASUS   CUSL-LV  30303031 MSFT 31313031)
[    0.000000] ACPI: DMI detected: Sony
[    0.000000] ACPI: PM-Timer IO Port: 0xe408
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:dfff0000)
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 130045
[    0.000000] Kernel command line: root=UUID=7a5c5a11-ca1c-42e9-9c30-0d5a2c9d2c6f ro quiet splash
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] mapped APIC to ffffb000 (0140e000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] Detected 868.668 MHz processor.
[   54.263665] Console: colour VGA+ 80x25
[   54.263675] console [tty0] enabled
[   54.264612] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   54.265691] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   54.307138] Memory: 507756k/524272k available (2258k kernel code, 15988k reserved, 1037k data, 384k init, 0k highmem)
[   54.307158] virtual kernel memory layout:
[   54.307161]     fixmap  : 0xfff4c000 - 0xfffff000   ( 716 kB)
[   54.307165]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
[   54.307168]     vmalloc : 0xe0800000 - 0xffbfe000   ( 499 MB)
[   54.307171]     lowmem  : 0xc0000000 - 0xdfffc000   ( 511 MB)
[   54.307174]       .init : 0xc043e000 - 0xc049e000   ( 384 kB)
[   54.307178]       .data : 0xc03349d9 - 0xc0437fe4   (1037 kB)
[   54.307181]       .text : 0xc0100000 - 0xc03349d9   (2258 kB)
[   54.307189] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   54.307266] SLUB: Genslabs=11, HWalign=32, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   54.457190] Calibrating delay using timer specific routine.. 1738.56 BogoMIPS (lpj=8692849)
[   54.457247] Security Framework initialized
[   54.457263] SELinux:  Disabled at boot.
[   54.457293] AppArmor: AppArmor initialized
[   54.457302] Failure registering capabilities with primary security module.
[   54.457323] Mount-cache hash table entries: 512
[   54.457574] Initializing cgroup subsys ns
[   54.457583] Initializing cgroup subsys cpuacct
[   54.457603] CPU: After generic identify, caps: 0383f9ff 00000000 00000000 00000000 00000000 00000000 00000000 00000000
[   54.457627] CPU: L1 I cache: 16K, L1 D cache: 16K
[   54.457633] CPU: L2 cache: 256K
[   54.457641] CPU: After all inits, caps: 0383f9ff 00000000 00000000 00000040 00000000 00000000 00000000 00000000
[   54.457663] Compat vDSO mapped to ffffe000.
[   54.457691] Checking 'hlt' instruction... OK.
[   54.497738] SMP alternatives: switching to UP code
[   54.500323] Freeing SMP alternatives: 12k freed
[   54.500607] Early unpacking initramfs... done
[   55.232406] ACPI: Core revision 20070126
[   55.232593] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   55.235278] ACPI: setting ELCR to 0200 (from 1c08)
[   55.235563] CPU0: Intel Pentium III (Coppermine) stepping 06
[   55.235577] SMP motherboard not detected.
[   55.235583] Local APIC not detected. Using dummy APIC emulation.
[   55.235703] Brought up 1 CPUs
[   55.235744] CPU0 attaching sched-domain:
[   55.235751]  domain 0: span 01
[   55.235755]   groups: 01
[   55.236239] net_namespace: 64 bytes
[   55.236261] Booting paravirtualized kernel on bare hardware
[   55.237670] Time: 17:24:10  Date: 05/16/09
[   55.237747] NET: Registered protocol family 16
[   55.238277] EISA bus registered
[   55.238304] ACPI: bus type pci registered
[   55.239689] PCI: PCI BIOS revision 2.10 entry at 0xf0900, last bus=2
[   55.239697] PCI: Using configuration type 1
[   55.239728] Setting up standard PCI resources
[   55.249579] ACPI: EC: Look up EC in DSDT
[   55.253995] ACPI: Interpreter enabled
[   55.254003] ACPI: (supports S0 S1 S3 S4 S5)
[   55.254039] ACPI: Using PIC for interrupt routing
[   55.271564] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   55.271876] PCI quirk: region e400-e47f claimed by ICH4 ACPI/GPIO/TCO
[   55.271885] PCI quirk: region ec00-ec3f claimed by ICH4 GPIO
[   55.272570] PCI: Transparent bridge - 0000:00:1e.0
[   55.272607] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   55.272845] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[   55.272985] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI2._PRT]
[   55.326361] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[   55.326594] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[   55.326798] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 11 *12 14 15)
[   55.327001] ACPI: PCI Interrupt Link [LNKD] (IRQs *3 4 5 6 7 9 10 11 12 14 15)
[   55.327281] Linux Plug and Play Support v0.97 (c) Adam Belay
[   55.327365] pnp: PnP ACPI init
[   55.327387] ACPI: bus type pnp registered
[   55.332681] pnp: PnP ACPI: found 12 devices
[   55.332690] ACPI: ACPI bus type pnp unregistered
[   55.332700] PnPBIOS: Disabled by ACPI PNP
[   55.333386] PCI: Using ACPI for IRQ routing
[   55.333396] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   55.356666] NET: Registered protocol family 8
[   55.356672] NET: Registered protocol family 20
[   55.356769] NetLabel: Initializing
[   55.356774] NetLabel:  domain hash size = 128
[   55.356778] NetLabel:  protocols = UNLABELED CIPSOv4
[   55.356811] NetLabel:  unlabeled traffic allowed by default
[   55.356911] AppArmor: AppArmor Filesystem Enabled
[   55.366542] Time: tsc clocksource has been installed.
[   55.386640] system 00:00: iomem range 0x0-0x9ffff could not be reserved
[   55.386650] system 00:00: iomem range 0xf0000-0xfffff could not be reserved
[   55.386657] system 00:00: iomem range 0x100000-0x1fffffff could not be reserved
[   55.386665] system 00:00: iomem range 0xffb80000-0xffbfffff has been reserved
[   55.386673] system 00:00: iomem range 0xfff80000-0xffffffff could not be reserved
[   55.386693] system 00:02: ioport range 0x3f0-0x3f1 has been reserved
[   55.386701] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
[   55.386718] system 00:03: ioport range 0xe400-0xe47f has been reserved
[   55.386726] system 00:03: ioport range 0xec00-0xec3f has been reserved
[   55.386733] system 00:03: ioport range 0x290-0x297 has been reserved
[   55.386740] system 00:03: ioport range 0x200-0x207 has been reserved
[   55.417841] PCI: Bridge: 0000:00:01.0
[   55.417848]   IO window: disabled.
[   55.417857]   MEM window: d6000000-d7efffff
[   55.417864]   PREFETCH window: d7f00000-e3ffffff
[   55.417875] PCI: Bridge: 0000:00:1e.0
[   55.417880]   IO window: c000-dfff
[   55.417888]   MEM window: d4000000-d5ffffff
[   55.417894]   PREFETCH window: disabled.
[   55.417912] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   55.417924] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   55.417957] NET: Registered protocol family 2
[   55.516657] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   55.517253] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[   55.517635] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[   55.518100] TCP: Hash tables configured (established 16384 bind 16384)
[   55.518109] TCP reno registered
[   55.546817] checking if image is initramfs...<7>Switched to high resolution mode on CPU 0
[   56.174824]  it is
[   56.940680] Freeing initrd memory: 7184k freed
[   56.941196] Simple Boot Flag at 0x3a set to 0x1
[   56.942080] audit: initializing netlink socket (disabled)
[   56.942113] audit(1242494651.640:1): initialized
[   56.942475] Total HugeTLB memory allocated, 0
[   56.947915] VFS: Disk quotas dquot_6.5.1
[   56.948154] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   56.948724] io scheduler noop registered
[   56.948733] io scheduler anticipatory registered
[   56.948739] io scheduler deadline registered (default)
[   56.948778] io scheduler cfq registered
[   56.948851] Boot video device is 0000:01:00.0
[   56.949561] isapnp: Scanning for PnP cards...
[   57.305958] isapnp: No Plug & Play device found
[   57.396200] Real Time Clock Driver v1.12ac
[   57.396405] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   57.396591] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   57.398154] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   57.400063] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   57.400267] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   57.400510] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[   57.400518] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[   57.401005] serio: i8042 KBD port at 0x60,0x64 irq 1
[   57.425390] mice: PS/2 mouse device common for all mice
[   57.425701] EISA: Probing bus 0 at eisa.0
[   57.425760] EISA: Detected 0 cards.
[   57.425768] cpuidle: using governor ladder
[   57.425773] cpuidle: using governor menu
[   57.426143] NET: Registered protocol family 1
[   57.426221] Using IPI No-Shortcut mode
[   57.426301] registered taskstats version 1
[   57.426516]   Magic number: 9:373:441
[   57.426706] BIOS EDD facility v0.16 2004-Jun-25, 6 devices found
[   57.428440] Freeing unused kernel memory: 384k freed
[   57.428591] Write protecting the kernel read-only data: 828k
[   57.895957] fuse init (API version 7.9)
[   57.949345] ACPI: Invalid PBLK length [5]
[   58.964924] SCSI subsystem initialized
[   59.255755] libata version 3.00 loaded.
[   59.273897] 8139too Fast Ethernet driver 0.9.28
[   59.274766] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 10
[   59.274773] PCI: setting IRQ 10 as level-triggered
[   59.274780] ACPI: PCI Interrupt 0000:02:0d.0[A] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
[   59.274805] PCI: Setting latency timer of device 0000:02:0d.0 to 64
[   59.275708] eth0: RealTek RTL8139 at 0xd000, 00:e0:18:cf:6d:8d, IRQ 10
[   59.275714] eth0:  Identified 8139 chip type 'RTL-8139C'
[   59.313924] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[   59.435332] usbcore: registered new interface driver usbfs
[   59.435387] usbcore: registered new interface driver hub
[   59.463250] usbcore: registered new device driver usb
[   59.516955] ata_piix 0000:00:1f.1: version 2.12
[   59.517087] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   59.547784] scsi0 : ata_piix
[   59.596648] scsi1 : ata_piix
[   59.597697] ata1: PATA max UDMA/66 cmd 0x1f0 ctl 0x3f6 bmdma 0xb800 irq 14
[   59.597705] ata2: PATA max UDMA/66 cmd 0x170 ctl 0x376 bmdma 0xb808 irq 15
[   59.605651] USB Universal Host Controller Interface driver v3.0
[   59.637519] Floppy drive(s): fd0 is 1.44M
[   59.657338] FDC 0 is a post-1991 82077
[   59.774772] ata1.00: ATA-5: WDC WD400BB-00DEA0, 05.03E05, max UDMA/100
[   59.774785] ata1.00: 78165360 sectors, multi 16: LBA 
[   59.774822] ata1.00: limited to UDMA/33 due to 40-wire cable
[   59.815110] ata1.00: configured for UDMA/33
[   60.333533] ata2.00: ATAPI: Pioneer DVD-ROM ATAPIModel DVD-116  0102, E1.02, max UDMA/66
[   60.333598] ata2.01: ATAPI: SONY    CD-RW  CRX140E, 1.1b, max UDMA/33
[   60.333630] ata2.00: limited to UDMA/33 due to 40-wire cable
[   60.533265] ata2.00: configured for UDMA/33
[   60.733065] ata2.01: configured for UDMA/33
[   60.733347] scsi 0:0:0:0: Direct-Access     ATA      WDC WD400BB-00DE 05.0 PQ: 0 ANSI: 5
[   60.735026] scsi 1:0:0:0: CD-ROM            PIONEER  DVD-ROM DVD-116R 1.02 PQ: 0 ANSI: 5
[   60.738481] scsi 1:0:1:0: CD-ROM            SONY     CD-RW  CRX140E   1.1b PQ: 0 ANSI: 5
[   60.742966] PCI: Enabling device 0000:02:0e.0 (0000 -> 0002)
[   60.743780] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 12
[   60.743788] PCI: setting IRQ 12 as level-triggered
[   60.743795] ACPI: PCI Interrupt 0000:02:0e.0[A] -> Link [LNKC] -> GSI 12 (level, low) -> IRQ 12
[   60.743811] PCI: Setting latency timer of device 0000:02:0e.0 to 64
[   60.795177] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[12]  MMIO=[d4800000-d48007ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   60.821040] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 3
[   60.821052] PCI: setting IRQ 3 as level-triggered
[   60.821058] ACPI: PCI Interrupt 0000:00:1f.2[D] -> Link [LNKD] -> GSI 3 (level, low) -> IRQ 3
[   60.821082] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   60.821090] uhci_hcd 0000:00:1f.2: UHCI Host Controller
[   60.821589] uhci_hcd 0000:00:1f.2: new USB bus registered, assigned bus number 1
[   60.821632] uhci_hcd 0000:00:1f.2: irq 3, io base 0x0000b400
[   60.821959] usb usb1: configuration #1 chosen from 1 choice
[   60.822017] hub 1-0:1.0: USB hub found
[   60.822032] hub 1-0:1.0: 2 ports detected
[   61.042871] Driver 'sd' needs updating - please use bus_type methods
[   61.043059] sd 0:0:0:0: [sda] 78165360 512-byte hardware sectors (40021 MB)
[   61.043093] sd 0:0:0:0: [sda] Write Protect is off
[   61.043100] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   61.043149] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   61.043262] sd 0:0:0:0: [sda] 78165360 512-byte hardware sectors (40021 MB)
[   61.043290] sd 0:0:0:0: [sda] Write Protect is off
[   61.043296] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   61.043343] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   61.043353]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   61.163539]  sda1 sda2 < sda5 >
[   61.202102] sd 0:0:0:0: [sda] Attached SCSI disk
[   61.203845] usb 1-2: new full speed USB device using uhci_hcd and address 2
[   61.217437] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   61.217485] sr 1:0:0:0: Attached scsi generic sg1 type 5
[   61.217529] scsi 1:0:1:0: Attached scsi generic sg2 type 5
[   61.220389] sr0: scsi3-mmc drive: 40x/40x cd/rw xa/form2 cdda tray
[   61.220403] Uniform CD-ROM driver Revision: 3.20
[   61.220531] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   61.386438] usb 1-2: configuration #1 chosen from 1 choice
[   61.392406] hub 1-2:1.0: USB hub found
[   61.393690] hub 1-2:1.0: 3 ports detected
[   62.132022] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[080046030063e851]
[   70.422895] sr1: scsi3-mmc drive: 32x/32x writer cd/rw xa/form2 cdda tray
[   70.423027] sr 1:0:1:0: Attached scsi CD-ROM sr1
[   73.832514] sr0: CDROM not ready.  Make sure there is a disc in the drive.
[  147.351455] ata2.01: qc timeout (cmd 0xa0)
[  147.351478] ata2.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[  147.351552] ata2.01: cmd a0/00:00:00:0c:00/00:00:00:00:00/b0 tag 0 pio 12 in
[  147.351556]          cdb 43 00 00 00 00 00 00 00  0c 00 00 00 00 00 00 00
[  147.351560]          res 51/24:03:00:0c:00/00:00:00:00:00/b0 Emask 0x5 (timeout)
[  147.351613] ata2.01: status: { DRDY ERR }
[  152.387859] ata2: port is slow to respond, please be patient (Status 0xd0)
[  157.364339] ata2: device not ready (errno=-16), forcing hardreset
[  157.364347] ata2: soft resetting link
[  158.084096] ata2.00: configured for UDMA/33
[  158.283909] ata2.01: configured for UDMA/33
[  158.283933] ata2: EH complete
[  221.578876] ata2.01: qc timeout (cmd 0xa0)
[  221.578894] ata2.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[  221.578962] ata2.01: cmd a0/00:00:00:0c:00/00:00:00:00:00/b0 tag 0 pio 12 in
[  221.578966]          cdb 43 00 00 00 00 00 00 00  0c 00 00 00 00 00 00 00
[  221.578970]          res 51/24:03:00:0c:00/00:00:00:00:00/b0 Emask 0x5 (timeout)
[  221.579021] ata2.01: status: { DRDY ERR }
[  226.615299] ata2: port is slow to respond, please be patient (Status 0xd0)
[  231.591776] ata2: device not ready (errno=-16), forcing hardreset
[  231.591783] ata2: soft resetting link
[  232.311537] ata2.00: configured for UDMA/33
[  232.511351] ata2.01: configured for UDMA/33
[  232.511372] ata2: EH complete
[  250.465145] Attempting manual resume
[  250.465155] swsusp: Resume From Partition 8:5
[  250.465160] PM: Checking swsusp image.
[  250.465507] PM: Resume from disk failed.
[  250.515174] EXT3-fs: INFO: recovery required on readonly filesystem.
[  250.515188] EXT3-fs: write access will be enabled during recovery.
[  257.767146] kjournald starting.  Commit interval 5 seconds
[  257.767192] EXT3-fs: sda1: orphan cleanup on readonly fs
[  257.795034] ext3_orphan_cleanup: deleting unreferenced inode 81925
[  257.795100] ext3_orphan_cleanup: deleting unreferenced inode 81924
[  257.795116] ext3_orphan_cleanup: deleting unreferenced inode 81923
[  257.795131] ext3_orphan_cleanup: deleting unreferenced inode 81922
[  257.795146] ext3_orphan_cleanup: deleting unreferenced inode 81921
[  257.795159] EXT3-fs: sda1: 5 orphan inodes deleted
[  257.795164] EXT3-fs: recovery complete.
[  257.819671] EXT3-fs: mounted filesystem with ordered data mode.
[  263.135071] input: PC Speaker as /devices/platform/pcspkr/input/input1
[  264.898343] iTCO_vendor_support: vendor-support=0
[  264.933418] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[  264.933602] iTCO_wdt: Found a ICH TCO device (Version=1, TCOBASE=0xe460)
[  264.933658] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[  265.069951] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[  265.151837] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[  265.224151] sr0: CDROM not ready.  Make sure there is a disc in the drive.
[  265.238042] Linux agpgart interface v0.102
[  265.508054] parport_pc 00:09: reported by Plug and Play ACPI
[  265.508107] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[  265.602000] agpgart: Detected an Intel i815 Chipset.
[  265.606028] agpgart: AGP aperture is 64M @ 0xe4000000
[  265.790196] intel_rng: FWH not detected
[  265.958003] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
[  265.958039] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[  266.297221] intel8x0_measure_ac97_clock: measured 52698 usecs
[  266.297232] intel8x0: clocking to 48000
[  266.740351] input: Power Button (FF) as /devices/virtual/input/input2
[  266.766964] ACPI: Power Button (FF) [PWRF]
[  266.767168] input: Power Button (CM) as /devices/virtual/input/input3
[  266.806906] ACPI: Power Button (CM) [PWRB]
[  269.366979] ip_tables: (C) 2000-2006 Netfilter Core Team
[  269.902291] nf_conntrack version 0.5.0 (8192 buckets, 32768 max)
[  270.331585] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  271.267334] NET: Registered protocol family 10
[  271.268089] lo: Disabled Privacy Extensions
[  281.386140] eth0: no IPv6 routers present
[  297.214292] ata2.01: qc timeout (cmd 0xa0)
[  297.214320] ata2.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[  297.214405] ata2.01: cmd a0/00:00:00:0c:00/00:00:00:00:00/b0 tag 0 pio 12 in
[  297.214409]          cdb 43 00 00 00 00 00 00 00  0c 00 00 00 00 00 00 00
[  297.214413]          res 51/24:03:00:0c:00/00:00:00:00:00/b0 Emask 0x5 (timeout)
[  297.214475] ata2.01: status: { DRDY ERR }
[  302.250486] ata2: port is slow to respond, please be patient (Status 0xd0)
[  307.226750] ata2: device not ready (errno=-16), forcing hardreset
[  307.226759] ata2: soft resetting link
[  307.946487] ata2.00: configured for UDMA/33
[  308.146292] ata2.01: configured for UDMA/33
[  308.146330] ata2: EH complete
[  393.801800] ata2.01: qc timeout (cmd 0xa0)
[  393.801825] ata2.01: limiting speed to UDMA/25:PIO4
[  393.801834] ata2.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[  393.801918] ata2.01: cmd a0/00:00:00:0c:00/00:00:00:00:00/b0 tag 0 pio 12 in
[  393.801922]          cdb 43 00 00 00 00 00 00 00  0c 40 00 00 00 00 00 00
[  393.801926]          res 51/24:03:00:0c:00/00:00:00:00:00/b0 Emask 0x5 (timeout)
[  393.801988] ata2.01: status: { DRDY ERR }
[  398.838003] ata2: port is slow to respond, please be patient (Status 0xd0)
[  403.814265] ata2: device not ready (errno=-16), forcing hardreset
[  403.814275] ata2: soft resetting link
[  404.534000] ata2.00: configured for UDMA/33
[  404.733804] ata2.01: configured for UDMA/25
[  404.733838] ata2: EH complete
[  442.981315] loop: module loaded
[  443.057994] lp0: using parport0 (interrupt-driven).
[  443.494819] Adding 1502036k swap on /dev/sda5.  Priority:-1 extents:1 across:1502036k
[  443.884686] EXT3 FS on sda1, internal journal
[  467.986178] ata2.01: qc timeout (cmd 0xa0)
[  467.986214] ata2.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[  467.986300] ata2.01: cmd a0/00:00:00:0c:00/00:00:00:00:00/b0 tag 0 pio 12 in
[  467.986304]          cdb 43 00 00 00 00 00 00 00  0c 40 00 00 00 00 00 00
[  467.986308]          res 51/24:03:00:0c:00/00:00:00:00:00/b0 Emask 0x5 (timeout)
[  467.986370] ata2.01: status: { DRDY ERR }
[  473.024103] ata2: port is slow to respond, please be patient (Status 0xd0)
[  478.008602] ata2: device not ready (errno=-16), forcing hardreset
[  478.008617] ata2: soft resetting link
[  478.708367] ata2.00: configured for UDMA/33
[  478.888179] ata2.01: configured for UDMA/25
[  478.888227] ata2: EH complete
[  542.210432] ata2.01: qc timeout (cmd 0xa0)
[  542.210464] ata2.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[  542.210558] ata2.01: cmd a0/00:00:00:0c:00/00:00:00:00:00/b0 tag 0 pio 12 in
[  542.210562]          cdb 43 00 00 00 00 00 00 00  0c 40 00 00 00 00 00 00
[  542.210566]          res 51/24:03:00:0c:00/00:00:00:00:00/b0 Emask 0x5 (timeout)
[  542.210627] ata2.01: status: { DRDY ERR }
[  547.246629] ata2: port is slow to respond, please be patient (Status 0xd0)
[  552.222895] ata2: device not ready (errno=-16), forcing hardreset
[  552.222909] ata2: soft resetting link
[  552.922641] ata2.00: configured for UDMA/33
[  553.102463] ata2.01: configured for UDMA/25
[  553.102510] ata2: EH complete
[  640.136940] ata2.01: qc timeout (cmd 0xa0)
[  640.136971] ata2.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[  640.137056] ata2.01: cmd a0/00:00:00:0c:00/00:00:00:00:00/b0 tag 0 pio 12 in
[  640.137060]          cdb 43 00 00 00 00 00 00 00  0c 00 00 00 00 00 00 00
[  640.137063]          res 51/24:03:00:0c:00/00:00:00:00:00/b0 Emask 0x5 (timeout)
[  640.137125] ata2.01: status: { DRDY ERR }
[  645.173137] ata2: port is slow to respond, please be patient (Status 0xd0)
[  650.149405] ata2: device not ready (errno=-16), forcing hardreset
[  650.149419] ata2: soft resetting link
[  650.849149] ata2.00: configured for UDMA/33
[  651.028971] ata2.01: configured for UDMA/25
[  651.029016] ata2: EH complete
[  714.351244] ata2.01: qc timeout (cmd 0xa0)
[  714.351277] ata2.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[  714.351329] ata2.01: cmd a0/00:00:00:0c:00/00:00:00:00:00/b0 tag 0 pio 12 in
[  714.351333]          cdb 43 00 00 00 00 00 00 00  0c 00 00 00 00 00 00 00
[  714.351337]          res 51/24:03:00:0c:00/00:00:00:00:00/b0 Emask 0x5 (timeout)
[  714.351366] ata2.01: status: { DRDY ERR }
[  719.387440] ata2: port is slow to respond, please be patient (Status 0xd0)
[  724.363706] ata2: device not ready (errno=-16), forcing hardreset
[  724.363721] ata2: soft resetting link
[  725.083436] ata2.00: configured for UDMA/33
[  725.263259] ata2.01: configured for UDMA/25
[  725.263304] ata2: EH complete
[  788.595539] ata2.01: qc timeout (cmd 0xa0)
[  788.595572] ata2.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[  788.595624] ata2.01: cmd a0/00:00:00:0c:00/00:00:00:00:00/b0 tag 0 pio 12 in
[  788.595628]          cdb 43 00 00 00 00 00 00 00  0c 00 00 00 00 00 00 00
[  788.595632]          res 51/24:03:00:0c:00/00:00:00:00:00/b0 Emask 0x5 (timeout)
[  788.595661] ata2.01: status: { DRDY ERR }
[  793.631722] ata2: port is slow to respond, please be patient (Status 0xd0)
[  798.607987] ata2: device not ready (errno=-16), forcing hardreset
[  798.608003] ata2: soft resetting link
[  799.327715] ata2.00: configured for UDMA/33
[  799.507538] ata2.01: configured for UDMA/25
[  799.507583] ata2: EH complete
[331006.349765] console-kit-dae[28505]: segfault at 00000000 eip b7e19577 esp bf821a94 error 4
[497976.352567] usb 1-2.3: new full speed USB device using uhci_hcd and address 3
[497976.483673] usb 1-2.3: configuration #1 chosen from 1 choice
[497976.869981] usbcore: registered new interface driver cdc_ether
[497977.088662] eth1: register 'rndis_host' at usb-0000:00:1f.2-2.3, RNDIS device, 80:00:60:0f:e8:00
[497977.088713] usbcore: registered new interface driver rndis_host
[498048.163185] usb 1-2.3: USB disconnect, address 3
[498048.163378] eth1: unregister 'rndis_host' usb-0000:00:1f.2-2.3, RNDIS device
[498581.449552] usb 1-2.3: new full speed USB device using uhci_hcd and address 4
[498581.580671] usb 1-2.3: configuration #1 chosen from 1 choice
[498581.785992] eth1: register 'rndis_host' at usb-0000:00:1f.2-2.3, RNDIS device, 80:00:60:0f:e8:00
[498643.565861] usb 1-2.3: USB disconnect, address 4
[498643.566054] eth1: unregister 'rndis_host' usb-0000:00:1f.2-2.3, RNDIS device
[499480.726302] usb 1-2.3: new full speed USB device using uhci_hcd and address 5
[499480.857408] usb 1-2.3: configuration #1 chosen from 1 choice
[499480.949860] eth1: register 'rndis_host' at usb-0000:00:1f.2-2.3, RNDIS device, 80:00:60:0f:e8:00
[499542.064309] usb 1-2.3: USB disconnect, address 5
[499542.064503] eth1: unregister 'rndis_host' usb-0000:00:1f.2-2.3, RNDIS device
[499780.491879] usb 1-2.3: new full speed USB device using uhci_hcd and address 6
[499780.622988] usb 1-2.3: configuration #1 chosen from 1 choice
[499780.752410] eth1: register 'rndis_host' at usb-0000:00:1f.2-2.3, RNDIS device, 80:00:60:0f:e8:00
[499867.821577] usb 1-2.3: USB disconnect, address 6
[499867.821773] eth1: unregister 'rndis_host' usb-0000:00:1f.2-2.3, RNDIS device
[500380.142947] usb 1-2.3: new full speed USB device using uhci_hcd and address 7
[500380.274041] usb 1-2.3: configuration #1 chosen from 1 choice
[500380.402484] eth1: register 'rndis_host' at usb-0000:00:1f.2-2.3, RNDIS device, 80:00:60:0f:e8:00
[500442.024450] usb 1-2.3: USB disconnect, address 7
[500442.024669] eth1: unregister 'rndis_host' usb-0000:00:1f.2-2.3, RNDIS device
[501279.469593] usb 1-2.3: new full speed USB device using uhci_hcd and address 8
[501279.600684] usb 1-2.3: configuration #1 chosen from 1 choice
[501279.693134] eth1: register 'rndis_host' at usb-0000:00:1f.2-2.3, RNDIS device, 80:00:60:0f:e8:00
[501340.791691] usb 1-2.3: USB disconnect, address 8
[501340.791889] eth1: unregister 'rndis_host' usb-0000:00:1f.2-2.3, RNDIS device
[502178.866166] usb 1-2.3: new full speed USB device using uhci_hcd and address 9
[502178.997273] usb 1-2.3: configuration #1 chosen from 1 choice
[502179.090700] eth1: register 'rndis_host' at usb-0000:00:1f.2-2.3, RNDIS device, 80:00:60:0f:e8:00
[502240.310079] usb 1-2.3: USB disconnect, address 9
[502240.310272] eth1: unregister 'rndis_host' usb-0000:00:1f.2-2.3, RNDIS device
[504876.895984] usb 1-2.3: new full speed USB device using uhci_hcd and address 10
[504877.026092] usb 1-2.3: configuration #1 chosen from 1 choice
[504877.118546] eth1: register 'rndis_host' at usb-0000:00:1f.2-2.3, RNDIS device, 80:00:60:0f:e8:00
[504938.147069] usb 1-2.3: USB disconnect, address 10
[504938.147264] eth1: unregister 'rndis_host' usb-0000:00:1f.2-2.3, RNDIS device
[505409.087469] usb 1-2.3: new full speed USB device using uhci_hcd and address 11
[505409.218578] usb 1-2.3: configuration #1 chosen from 1 choice
[505409.369972] eth1: register 'rndis_host' at usb-0000:00:1f.2-2.3, RNDIS device, 80:00:60:0f:e8:00
[505421.599245] usb 1-2.3: USB disconnect, address 11
[505421.599435] eth1: unregister 'rndis_host' usb-0000:00:1f.2-2.3, RNDIS device
```

For /var/log/messages, I pasted the most recent startup events. The entire file is attached:
```

May 16 13:31:01 arena syslogd 1.5.0#1ubuntu1: restart.
May 16 13:31:01 arena kernel: Inspecting /boot/System.map-2.6.24-23-server
May 16 13:31:02 arena kernel: Loaded 28764 symbols from /boot/System.map-2.6.24-23-server.
May 16 13:31:02 arena kernel: Symbols match kernel version 2.6.24.
May 16 13:31:02 arena kernel: Loaded 14697 symbols from 60 modules.
May 16 13:31:02 arena kernel: [    0.000000] Initializing cgroup subsys cpuset
May 16 13:31:02 arena kernel: [    0.000000] Initializing cgroup subsys cpu
May 16 13:31:02 arena kernel: [    0.000000] Linux version 2.6.24-23-server (buildd@vernadsky) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Mon Jan 26 00:55:21 UTC 2009 (Ubuntu 2.6.24-23.48-server)
May 16 13:31:02 arena kernel: [    0.000000] BIOS-provided physical RAM map:
May 16 13:31:02 arena kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 00000000000a0000 (usable)
May 16 13:31:02 arena kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
May 16 13:31:02 arena kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000001fffc000 (usable)
May 16 13:31:02 arena kernel: [    0.000000]  BIOS-e820: 000000001fffc000 - 000000001ffff000 (ACPI data)
May 16 13:31:02 arena kernel: [    0.000000]  BIOS-e820: 000000001ffff000 - 0000000020000000 (ACPI NVS)
May 16 13:31:02 arena kernel: [    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
May 16 13:31:02 arena kernel: [    0.000000] 0MB HIGHMEM available.
May 16 13:31:02 arena kernel: [    0.000000] 511MB LOWMEM available.
May 16 13:31:02 arena kernel: [    0.000000] Zone PFN ranges:
May 16 13:31:02 arena kernel: [    0.000000]   DMA             0 ->     4096
May 16 13:31:02 arena kernel: [    0.000000]   Normal       4096 ->   131068
May 16 13:31:02 arena kernel: [    0.000000]   HighMem    131068 ->   131068
May 16 13:31:02 arena kernel: [    0.000000] Movable zone start PFN for each node
May 16 13:31:02 arena kernel: [    0.000000] early_node_map[1] active PFN ranges
May 16 13:31:02 arena kernel: [    0.000000]     0:        0 ->   131068
May 16 13:31:02 arena kernel: [    0.000000] DMI 2.3 present.
May 16 13:31:02 arena kernel: [    0.000000] ACPI: RSDP signature @ 0xC00F5B30 checksum 0
May 16 13:31:02 arena kernel: [    0.000000] ACPI: RSDP 000F5B30, 0014 (r0 ASUS  )
May 16 13:31:02 arena kernel: [    0.000000] ACPI: RSDT 1FFFC000, 002C (r1 ASUS   CUSL-LV  30303031 MSFT 31313031)
May 16 13:31:02 arena kernel: [    0.000000] ACPI: FACP 1FFFC080, 0074 (r1 ASUS   CUSL-LV  30303031 MSFT 31313031)
May 16 13:31:02 arena kernel: [    0.000000] ACPI: DSDT 1FFFC100, 28E5 (r1   ASUS CUSL-LV      1000 MSFT  100000B)
May 16 13:31:02 arena kernel: [    0.000000] ACPI: FACS 1FFFF000, 0040
May 16 13:31:02 arena kernel: [    0.000000] ACPI: BOOT 1FFFC040, 0028 (r1 ASUS   CUSL-LV  30303031 MSFT 31313031)
May 16 13:31:02 arena kernel: [    0.000000] ACPI: DMI detected: Sony
May 16 13:31:02 arena kernel: [    0.000000] ACPI: PM-Timer IO Port: 0xe408
May 16 13:31:02 arena kernel: [    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:dfff0000)
May 16 13:31:02 arena kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
May 16 13:31:02 arena kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
May 16 13:31:02 arena kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 130045
May 16 13:31:02 arena kernel: [    0.000000] Kernel command line: root=UUID=7a5c5a11-ca1c-42e9-9c30-0d5a2c9d2c6f ro quiet splash
May 16 13:31:02 arena kernel: [    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
May 16 13:31:02 arena kernel: [    0.000000] Enabling fast FPU save and restore... done.
May 16 13:31:02 arena kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
May 16 13:31:02 arena kernel: [    0.000000] Initializing CPU#0
May 16 13:31:02 arena kernel: [    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
May 16 13:31:02 arena kernel: [    0.000000] Detected 868.668 MHz processor.
May 16 13:31:02 arena kernel: [   54.263665] Console: colour VGA+ 80x25
May 16 13:31:02 arena kernel: [   54.263675] console [tty0] enabled
May 16 13:31:02 arena kernel: [   54.264612] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
May 16 13:31:02 arena kernel: [   54.265691] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
May 16 13:31:02 arena kernel: [   54.307138] Memory: 507756k/524272k available (2258k kernel code, 15988k reserved, 1037k data, 384k init, 0k highmem)
May 16 13:31:02 arena kernel: [   54.307158] virtual kernel memory layout:
May 16 13:31:02 arena kernel: [   54.307161]     fixmap  : 0xfff4c000 - 0xfffff000   ( 716 kB)
May 16 13:31:02 arena kernel: [   54.307165]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
May 16 13:31:02 arena kernel: [   54.307168]     vmalloc : 0xe0800000 - 0xffbfe000   ( 499 MB)
May 16 13:31:02 arena kernel: [   54.307171]     lowmem  : 0xc0000000 - 0xdfffc000   ( 511 MB)
May 16 13:31:02 arena kernel: [   54.307174]       .init : 0xc043e000 - 0xc049e000   ( 384 kB)
May 16 13:31:02 arena kernel: [   54.307178]       .data : 0xc03349d9 - 0xc0437fe4   (1037 kB)
May 16 13:31:02 arena kernel: [   54.307181]       .text : 0xc0100000 - 0xc03349d9   (2258 kB)
May 16 13:31:02 arena kernel: [   54.307189] Checking if this processor honours the WP bit even in supervisor mode... Ok.
May 16 13:31:02 arena kernel: [   54.307266] SLUB: Genslabs=11, HWalign=32, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
May 16 13:31:02 arena kernel: [   54.457190] Calibrating delay using timer specific routine.. 1738.56 BogoMIPS (lpj=8692849)
May 16 13:31:02 arena kernel: [   54.457247] Security Framework initialized
May 16 13:31:02 arena kernel: [   54.457263] SELinux:  Disabled at boot.
May 16 13:31:02 arena kernel: [   54.457293] AppArmor: AppArmor initialized
May 16 13:31:02 arena kernel: [   54.457302] Failure registering capabilities with primary security module.
May 16 13:31:02 arena kernel: [   54.457323] Mount-cache hash table entries: 512
May 16 13:31:02 arena kernel: [   54.457574] Initializing cgroup subsys ns
May 16 13:31:02 arena kernel: [   54.457583] Initializing cgroup subsys cpuacct
May 16 13:31:02 arena kernel: [   54.457627] CPU: L1 I cache: 16K, L1 D cache: 16K
May 16 13:31:02 arena kernel: [   54.457633] CPU: L2 cache: 256K
May 16 13:31:02 arena kernel: [   54.457663] Compat vDSO mapped to ffffe000.
May 16 13:31:02 arena kernel: [   54.457691] Checking 'hlt' instruction... OK.
May 16 13:31:02 arena kernel: [   54.497738] SMP alternatives: switching to UP code
May 16 13:31:02 arena kernel: [   54.500323] Freeing SMP alternatives: 12k freed
May 16 13:31:02 arena kernel: [   54.500607] Early unpacking initramfs... done
May 16 13:31:02 arena kernel: [   55.232406] ACPI: Core revision 20070126
May 16 13:31:02 arena kernel: [   55.232593] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
May 16 13:31:02 arena kernel: [   55.235278] ACPI: setting ELCR to 0200 (from 1c08)
May 16 13:31:02 arena kernel: [   55.235563] CPU0: Intel Pentium III (Coppermine) stepping 06
May 16 13:31:02 arena kernel: [   55.235577] SMP motherboard not detected.
May 16 13:31:02 arena kernel: [   55.235583] Local APIC not detected. Using dummy APIC emulation.
May 16 13:31:02 arena kernel: [   55.235703] Brought up 1 CPUs
May 16 13:31:02 arena kernel: [   55.236239] net_namespace: 64 bytes
May 16 13:31:02 arena kernel: [   55.236261] Booting paravirtualized kernel on bare hardware
May 16 13:31:02 arena kernel: [   55.237670] Time: 17:24:10  Date: 05/16/09
May 16 13:31:02 arena kernel: [   55.237747] NET: Registered protocol family 16
May 16 13:31:02 arena kernel: [   55.238277] EISA bus registered
May 16 13:31:02 arena kernel: [   55.238304] ACPI: bus type pci registered
May 16 13:31:02 arena kernel: [   55.239689] PCI: PCI BIOS revision 2.10 entry at 0xf0900, last bus=2
May 16 13:31:02 arena kernel: [   55.239697] PCI: Using configuration type 1
May 16 13:31:02 arena kernel: [   55.239728] Setting up standard PCI resources
May 16 13:31:02 arena kernel: [   55.253995] ACPI: Interpreter enabled
May 16 13:31:02 arena kernel: [   55.254003] ACPI: (supports S0 S1 S3 S4 S5)
May 16 13:31:02 arena kernel: [   55.254039] ACPI: Using PIC for interrupt routing
May 16 13:31:02 arena kernel: [   55.271564] ACPI: PCI Root Bridge [PCI0] (0000:00)
May 16 13:31:02 arena kernel: [   55.271876] PCI quirk: region e400-e47f claimed by ICH4 ACPI/GPIO/TCO
May 16 13:31:02 arena kernel: [   55.271885] PCI quirk: region ec00-ec3f claimed by ICH4 GPIO
May 16 13:31:02 arena kernel: [   55.272570] PCI: Transparent bridge - 0000:00:1e.0
May 16 13:31:02 arena kernel: [   55.326361] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
May 16 13:31:02 arena kernel: [   55.326594] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
May 16 13:31:02 arena kernel: [   55.326798] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 11 *12 14 15)
May 16 13:31:02 arena kernel: [   55.327001] ACPI: PCI Interrupt Link [LNKD] (IRQs *3 4 5 6 7 9 10 11 12 14 15)
May 16 13:31:02 arena kernel: [   55.327281] Linux Plug and Play Support v0.97 (c) Adam Belay
May 16 13:31:02 arena kernel: [   55.327365] pnp: PnP ACPI init
May 16 13:31:02 arena kernel: [   55.327387] ACPI: bus type pnp registered
May 16 13:31:02 arena kernel: [   55.332681] pnp: PnP ACPI: found 12 devices
May 16 13:31:02 arena kernel: [   55.332690] ACPI: ACPI bus type pnp unregistered
May 16 13:31:02 arena kernel: [   55.332700] PnPBIOS: Disabled by ACPI PNP
May 16 13:31:02 arena kernel: [   55.333386] PCI: Using ACPI for IRQ routing
May 16 13:31:02 arena kernel: [   55.333396] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
May 16 13:31:02 arena kernel: [   55.356666] NET: Registered protocol family 8
May 16 13:31:02 arena kernel: [   55.356672] NET: Registered protocol family 20
May 16 13:31:02 arena kernel: [   55.356769] NetLabel: Initializing
May 16 13:31:02 arena kernel: [   55.356774] NetLabel:  domain hash size = 128
May 16 13:31:02 arena kernel: [   55.356778] NetLabel:  protocols = UNLABELED CIPSOv4
May 16 13:31:02 arena kernel: [   55.356811] NetLabel:  unlabeled traffic allowed by default
May 16 13:31:02 arena kernel: [   55.356911] AppArmor: AppArmor Filesystem Enabled
May 16 13:31:02 arena kernel: [   55.366542] Time: tsc clocksource has been installed.
May 16 13:31:02 arena kernel: [   55.386640] system 00:00: iomem range 0x0-0x9ffff could not be reserved
May 16 13:31:02 arena kernel: [   55.386650] system 00:00: iomem range 0xf0000-0xfffff could not be reserved
May 16 13:31:02 arena kernel: [   55.386657] system 00:00: iomem range 0x100000-0x1fffffff could not be reserved
May 16 13:31:02 arena kernel: [   55.386665] system 00:00: iomem range 0xffb80000-0xffbfffff has been reserved
May 16 13:31:02 arena kernel: [   55.386673] system 00:00: iomem range 0xfff80000-0xffffffff could not be reserved
May 16 13:31:02 arena kernel: [   55.386693] system 00:02: ioport range 0x3f0-0x3f1 has been reserved
May 16 13:31:02 arena kernel: [   55.386701] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
May 16 13:31:02 arena kernel: [   55.386718] system 00:03: ioport range 0xe400-0xe47f has been reserved
May 16 13:31:02 arena kernel: [   55.386726] system 00:03: ioport range 0xec00-0xec3f has been reserved
May 16 13:31:02 arena kernel: [   55.386733] system 00:03: ioport range 0x290-0x297 has been reserved
May 16 13:31:02 arena kernel: [   55.386740] system 00:03: ioport range 0x200-0x207 has been reserved
May 16 13:31:02 arena kernel: [   55.417841] PCI: Bridge: 0000:00:01.0
May 16 13:31:02 arena kernel: [   55.417848]   IO window: disabled.
May 16 13:31:02 arena kernel: [   55.417857]   MEM window: d6000000-d7efffff
May 16 13:31:02 arena kernel: [   55.417864]   PREFETCH window: d7f00000-e3ffffff
May 16 13:31:02 arena kernel: [   55.417875] PCI: Bridge: 0000:00:1e.0
May 16 13:31:02 arena kernel: [   55.417880]   IO window: c000-dfff
May 16 13:31:02 arena kernel: [   55.417888]   MEM window: d4000000-d5ffffff
May 16 13:31:02 arena kernel: [   55.417894]   PREFETCH window: disabled.
May 16 13:31:02 arena kernel: [   55.417957] NET: Registered protocol family 2
May 16 13:31:02 arena kernel: [   55.516657] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
May 16 13:31:02 arena kernel: [   55.517253] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
May 16 13:31:02 arena kernel: [   55.517635] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
May 16 13:31:02 arena kernel: [   55.518100] TCP: Hash tables configured (established 16384 bind 16384)
May 16 13:31:02 arena kernel: [   55.518109] TCP reno registered
May 16 13:31:02 arena kernel: [   55.546817] checking if image is initramfs...<7>Switched to high resolution mode on CPU 0
May 16 13:31:02 arena kernel: [   56.174824]  it is
May 16 13:31:02 arena kernel: [   56.940680] Freeing initrd memory: 7184k freed
May 16 13:31:02 arena kernel: [   56.941196] Simple Boot Flag at 0x3a set to 0x1
May 16 13:31:02 arena kernel: [   56.942080] audit: initializing netlink socket (disabled)
May 16 13:31:02 arena kernel: [   56.942113] audit(1242494651.640:1): initialized
May 16 13:31:02 arena kernel: [   56.942475] Total HugeTLB memory allocated, 0
May 16 13:31:02 arena kernel: [   56.947915] VFS: Disk quotas dquot_6.5.1
May 16 13:31:02 arena kernel: [   56.948154] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
May 16 13:31:02 arena kernel: [   56.948724] io scheduler noop registered
May 16 13:31:02 arena kernel: [   56.948733] io scheduler anticipatory registered
May 16 13:31:02 arena kernel: [   56.948739] io scheduler deadline registered (default)
May 16 13:31:02 arena kernel: [   56.948778] io scheduler cfq registered
May 16 13:31:02 arena kernel: [   56.949561] isapnp: Scanning for PnP cards...
May 16 13:31:02 arena kernel: [   57.305958] isapnp: No Plug & Play device found
May 16 13:31:02 arena kernel: [   57.396200] Real Time Clock Driver v1.12ac
May 16 13:31:02 arena kernel: [   57.396405] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
May 16 13:31:02 arena kernel: [   57.396591] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
May 16 13:31:02 arena kernel: [   57.398154] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
May 16 13:31:02 arena kernel: [   57.400063] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
May 16 13:31:02 arena kernel: [   57.400267] input: Macintosh mouse button emulation as /devices/virtual/input/input0
May 16 13:31:02 arena kernel: [   57.400510] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
May 16 13:31:02 arena kernel: [   57.400518] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
May 16 13:31:02 arena kernel: [   57.401005] serio: i8042 KBD port at 0x60,0x64 irq 1
May 16 13:31:02 arena kernel: [   57.425390] mice: PS/2 mouse device common for all mice
May 16 13:31:02 arena kernel: [   57.425701] EISA: Probing bus 0 at eisa.0
May 16 13:31:02 arena kernel: [   57.425760] EISA: Detected 0 cards.
May 16 13:31:02 arena kernel: [   57.425768] cpuidle: using governor ladder
May 16 13:31:02 arena kernel: [   57.425773] cpuidle: using governor menu
May 16 13:31:02 arena kernel: [   57.426143] NET: Registered protocol family 1
May 16 13:31:02 arena kernel: [   57.426221] Using IPI No-Shortcut mode
May 16 13:31:02 arena kernel: [   57.426301] registered taskstats version 1
May 16 13:31:02 arena kernel: [   57.426516]   Magic number: 9:373:441
May 16 13:31:02 arena kernel: [   57.426706] BIOS EDD facility v0.16 2004-Jun-25, 6 devices found
May 16 13:31:02 arena kernel: [   57.428440] Freeing unused kernel memory: 384k freed
May 16 13:31:02 arena kernel: [   57.428591] Write protecting the kernel read-only data: 828k
May 16 13:31:02 arena kernel: [   57.895957] fuse init (API version 7.9)
May 16 13:31:02 arena kernel: [   58.964924] SCSI subsystem initialized
May 16 13:31:02 arena kernel: [   59.273897] 8139too Fast Ethernet driver 0.9.28
May 16 13:31:02 arena kernel: [   59.274766] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 10
May 16 13:31:02 arena kernel: [   59.274780] ACPI: PCI Interrupt 0000:02:0d.0[A] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
May 16 13:31:02 arena kernel: [   59.275708] eth0: RealTek RTL8139 at 0xd000, 00:e0:18:cf:6d:8d, IRQ 10
May 16 13:31:02 arena kernel: [   59.313924] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
May 16 13:31:02 arena kernel: [   59.435332] usbcore: registered new interface driver usbfs
May 16 13:31:02 arena kernel: [   59.435387] usbcore: registered new interface driver hub
May 16 13:31:02 arena kernel: [   59.463250] usbcore: registered new device driver usb
May 16 13:31:02 arena kernel: [   59.547784] scsi0 : ata_piix
May 16 13:31:02 arena kernel: [   59.596648] scsi1 : ata_piix
May 16 13:31:02 arena kernel: [   59.597697] ata1: PATA max UDMA/66 cmd 0x1f0 ctl 0x3f6 bmdma 0xb800 irq 14
May 16 13:31:02 arena kernel: [   59.597705] ata2: PATA max UDMA/66 cmd 0x170 ctl 0x376 bmdma 0xb808 irq 15
May 16 13:31:02 arena kernel: [   59.605651] USB Universal Host Controller Interface driver v3.0
May 16 13:31:02 arena kernel: [   59.637519] Floppy drive(s): fd0 is 1.44M
May 16 13:31:02 arena kernel: [   59.657338] FDC 0 is a post-1991 82077
May 16 13:31:02 arena kernel: [   59.774772] ata1.00: ATA-5: WDC WD400BB-00DEA0, 05.03E05, max UDMA/100
May 16 13:31:02 arena kernel: [   59.774785] ata1.00: 78165360 sectors, multi 16: LBA 
May 16 13:31:02 arena kernel: [   59.774822] ata1.00: limited to UDMA/33 due to 40-wire cable
May 16 13:31:02 arena kernel: [   59.815110] ata1.00: configured for UDMA/33
May 16 13:31:02 arena kernel: [   60.333533] ata2.00: ATAPI: Pioneer DVD-ROM ATAPIModel DVD-116  0102, E1.02, max UDMA/66
May 16 13:31:02 arena kernel: [   60.333598] ata2.01: ATAPI: SONY    CD-RW  CRX140E, 1.1b, max UDMA/33
May 16 13:31:02 arena kernel: [   60.333630] ata2.00: limited to UDMA/33 due to 40-wire cable
May 16 13:31:02 arena kernel: [   60.533265] ata2.00: configured for UDMA/33
May 16 13:31:02 arena kernel: [   60.733065] ata2.01: configured for UDMA/33
May 16 13:31:02 arena kernel: [   60.733347] scsi 0:0:0:0: Direct-Access     ATA      WDC WD400BB-00DE 05.0 PQ: 0 ANSI: 5
May 16 13:31:02 arena kernel: [   60.735026] scsi 1:0:0:0: CD-ROM            PIONEER  DVD-ROM DVD-116R 1.02 PQ: 0 ANSI: 5
May 16 13:31:02 arena kernel: [   60.738481] scsi 1:0:1:0: CD-ROM            SONY     CD-RW  CRX140E   1.1b PQ: 0 ANSI: 5
May 16 13:31:02 arena kernel: [   60.742966] PCI: Enabling device 0000:02:0e.0 (0000 -> 0002)
May 16 13:31:02 arena kernel: [   60.743780] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 12
May 16 13:31:02 arena kernel: [   60.743795] ACPI: PCI Interrupt 0000:02:0e.0[A] -> Link [LNKC] -> GSI 12 (level, low) -> IRQ 12
May 16 13:31:02 arena kernel: [   60.795177] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[12]  MMIO=[d4800000-d48007ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
May 16 13:31:02 arena kernel: [   60.821040] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 3
May 16 13:31:02 arena kernel: [   60.821058] ACPI: PCI Interrupt 0000:00:1f.2[D] -> Link [LNKD] -> GSI 3 (level, low) -> IRQ 3
May 16 13:31:02 arena kernel: [   60.821090] uhci_hcd 0000:00:1f.2: UHCI Host Controller
May 16 13:31:02 arena kernel: [   60.821589] uhci_hcd 0000:00:1f.2: new USB bus registered, assigned bus number 1
May 16 13:31:02 arena kernel: [   60.821632] uhci_hcd 0000:00:1f.2: irq 3, io base 0x0000b400
May 16 13:31:02 arena kernel: [   60.821959] usb usb1: configuration #1 chosen from 1 choice
May 16 13:31:02 arena kernel: [   60.822017] hub 1-0:1.0: USB hub found
May 16 13:31:02 arena kernel: [   60.822032] hub 1-0:1.0: 2 ports detected
May 16 13:31:02 arena kernel: [   61.042871] Driver 'sd' needs updating - please use bus_type methods
May 16 13:31:02 arena kernel: [   61.043059] sd 0:0:0:0: [sda] 78165360 512-byte hardware sectors (40021 MB)
May 16 13:31:02 arena kernel: [   61.043093] sd 0:0:0:0: [sda] Write Protect is off
May 16 13:31:02 arena kernel: [   61.043149] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May 16 13:31:02 arena kernel: [   61.043262] sd 0:0:0:0: [sda] 78165360 512-byte hardware sectors (40021 MB)
May 16 13:31:02 arena kernel: [   61.043290] sd 0:0:0:0: [sda] Write Protect is off
May 16 13:31:02 arena kernel: [   61.043343] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
May 16 13:31:02 arena kernel: [   61.043353]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
May 16 13:31:02 arena kernel: [   61.163539]  sda1 sda2 < sda5 >
May 16 13:31:02 arena kernel: [   61.202102] sd 0:0:0:0: [sda] Attached SCSI disk
May 16 13:31:02 arena kernel: [   61.203845] usb 1-2: new full speed USB device using uhci_hcd and address 2
May 16 13:31:02 arena kernel: [   61.217437] sd 0:0:0:0: Attached scsi generic sg0 type 0
May 16 13:31:02 arena kernel: [   61.217485] sr 1:0:0:0: Attached scsi generic sg1 type 5
May 16 13:31:02 arena kernel: [   61.217529] scsi 1:0:1:0: Attached scsi generic sg2 type 5
May 16 13:31:02 arena kernel: [   61.220389] sr0: scsi3-mmc drive: 40x/40x cd/rw xa/form2 cdda tray
May 16 13:31:02 arena kernel: [   61.220403] Uniform CD-ROM driver Revision: 3.20
May 16 13:31:02 arena kernel: [   61.386438] usb 1-2: configuration #1 chosen from 1 choice
May 16 13:31:02 arena kernel: [   61.392406] hub 1-2:1.0: USB hub found
May 16 13:31:02 arena kernel: [   61.393690] hub 1-2:1.0: 3 ports detected
May 16 13:31:02 arena kernel: [   70.422895] sr1: scsi3-mmc drive: 32x/32x writer cd/rw xa/form2 cdda tray
May 16 13:31:02 arena kernel: [   73.832514] sr0: CDROM not ready.  Make sure there is a disc in the drive.
May 16 13:31:02 arena kernel: [  147.351455] ata2.01: qc timeout (cmd 0xa0)
May 16 13:31:02 arena kernel: [  147.351556]          cdb 43 00 00 00 00 00 00 00  0c 00 00 00 00 00 00 00
May 16 13:31:02 arena kernel: [  147.351560]          res 51/24:03:00:0c:00/00:00:00:00:00/b0 Emask 0x5 (timeout)
May 16 13:31:02 arena kernel: [  152.387859] ata2: port is slow to respond, please be patient (Status 0xd0)
May 16 13:31:02 arena kernel: [  157.364339] ata2: device not ready (errno=-16), forcing hardreset
May 16 13:31:02 arena kernel: [  157.364347] ata2: soft resetting link
May 16 13:31:02 arena kernel: [  158.084096] ata2.00: configured for UDMA/33
May 16 13:31:02 arena kernel: [  158.283909] ata2.01: configured for UDMA/33
May 16 13:31:02 arena kernel: [  158.283933] ata2: EH complete
May 16 13:31:02 arena kernel: [  221.578876] ata2.01: qc timeout (cmd 0xa0)
May 16 13:31:02 arena kernel: [  221.578966]          cdb 43 00 00 00 00 00 00 00  0c 00 00 00 00 00 00 00
May 16 13:31:02 arena kernel: [  221.578970]          res 51/24:03:00:0c:00/00:00:00:00:00/b0 Emask 0x5 (timeout)
May 16 13:31:02 arena kernel: [  226.615299] ata2: port is slow to respond, please be patient (Status 0xd0)
May 16 13:31:02 arena kernel: [  231.591776] ata2: device not ready (errno=-16), forcing hardreset
May 16 13:31:02 arena kernel: [  231.591783] ata2: soft resetting link
May 16 13:31:02 arena kernel: [  232.311537] ata2.00: configured for UDMA/33
May 16 13:31:02 arena kernel: [  232.511351] ata2.01: configured for UDMA/33
May 16 13:31:02 arena kernel: [  232.511372] ata2: EH complete
May 16 13:31:02 arena kernel: [  250.465145] Attempting manual resume
May 16 13:31:02 arena kernel: [  250.515174] EXT3-fs: INFO: recovery required on readonly filesystem.
May 16 13:31:02 arena kernel: [  250.515188] EXT3-fs: write access will be enabled during recovery.
May 16 13:31:02 arena kernel: [  257.767146] kjournald starting.  Commit interval 5 seconds
May 16 13:31:02 arena kernel: [  257.767192] EXT3-fs: sda1: orphan cleanup on readonly fs
May 16 13:31:02 arena kernel: [  257.795159] EXT3-fs: sda1: 5 orphan inodes deleted
May 16 13:31:02 arena kernel: [  257.795164] EXT3-fs: recovery complete.
May 16 13:31:02 arena kernel: [  257.819671] EXT3-fs: mounted filesystem with ordered data mode.
May 16 13:31:02 arena kernel: [  263.135071] input: PC Speaker as /devices/platform/pcspkr/input/input1
May 16 13:31:02 arena kernel: [  264.898343] iTCO_vendor_support: vendor-support=0
May 16 13:31:02 arena kernel: [  264.933418] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
May 16 13:31:02 arena kernel: [  264.933602] iTCO_wdt: Found a ICH TCO device (Version=1, TCOBASE=0xe460)
May 16 13:31:02 arena kernel: [  264.933658] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
May 16 13:31:02 arena kernel: [  265.069951] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
May 16 13:31:02 arena kernel: [  265.151837] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
May 16 13:31:02 arena kernel: [  265.224151] sr0: CDROM not ready.  Make sure there is a disc in the drive.
May 16 13:31:02 arena kernel: [  265.238042] Linux agpgart interface v0.102
May 16 13:31:02 arena kernel: [  265.508054] parport_pc 00:09: reported by Plug and Play ACPI
May 16 13:31:02 arena kernel: [  265.508107] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
May 16 13:31:02 arena kernel: [  265.602000] agpgart: Detected an Intel i815 Chipset.
May 16 13:31:02 arena kernel: [  265.606028] agpgart: AGP aperture is 64M @ 0xe4000000
May 16 13:31:02 arena kernel: [  265.958003] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
May 16 13:31:02 arena kernel: [  266.297221] intel8x0_measure_ac97_clock: measured 52698 usecs
May 16 13:31:02 arena kernel: [  266.297232] intel8x0: clocking to 48000
May 16 13:31:02 arena kernel: [  266.740351] input: Power Button (FF) as /devices/virtual/input/input2
May 16 13:31:02 arena kernel: [  266.766964] ACPI: Power Button (FF) [PWRF]
May 16 13:31:02 arena kernel: [  266.767168] input: Power Button (CM) as /devices/virtual/input/input3
May 16 13:31:02 arena kernel: [  266.806906] ACPI: Power Button (CM) [PWRB]
May 16 13:31:02 arena kernel: [  269.366979] ip_tables: (C) 2000-2006 Netfilter Core Team
May 16 13:31:02 arena kernel: [  269.902291] nf_conntrack version 0.5.0 (8192 buckets, 32768 max)
May 16 13:31:02 arena kernel: [  270.331585] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
May 16 13:31:02 arena kernel: [  271.267334] NET: Registered protocol family 10
May 16 13:31:02 arena kernel: [  271.268089] lo: Disabled Privacy Extensions
May 16 13:31:02 arena kernel: [  297.214292] ata2.01: qc timeout (cmd 0xa0)
May 16 13:31:02 arena kernel: [  297.214409]          cdb 43 00 00 00 00 00 00 00  0c 00 00 00 00 00 00 00
May 16 13:31:02 arena kernel: [  297.214413]          res 51/24:03:00:0c:00/00:00:00:00:00/b0 Emask 0x5 (timeout)
May 16 13:31:02 arena kernel: [  302.250486] ata2: port is slow to respond, please be patient (Status 0xd0)
May 16 13:31:02 arena kernel: [  307.226750] ata2: device not ready (errno=-16), forcing hardreset
May 16 13:31:02 arena kernel: [  307.226759] ata2: soft resetting link
May 16 13:31:02 arena kernel: [  307.946487] ata2.00: configured for UDMA/33
May 16 13:31:02 arena kernel: [  308.146292] ata2.01: configured for UDMA/33
May 16 13:31:02 arena kernel: [  308.146330] ata2: EH complete
May 16 13:31:02 arena kernel: [  393.801800] ata2.01: qc timeout (cmd 0xa0)
May 16 13:31:02 arena kernel: [  393.801825] ata2.01: limiting speed to UDMA/25:PIO4
May 16 13:31:02 arena kernel: [  393.801922]          cdb 43 00 00 00 00 00 00 00  0c 40 00 00 00 00 00 00
May 16 13:31:02 arena kernel: [  393.801926]          res 51/24:03:00:0c:00/00:00:00:00:00/b0 Emask 0x5 (timeout)
May 16 13:31:02 arena kernel: [  398.838003] ata2: port is slow to respond, please be patient (Status 0xd0)
May 16 13:31:02 arena kernel: [  403.814265] ata2: device not ready (errno=-16), forcing hardreset
May 16 13:31:02 arena kernel: [  403.814275] ata2: soft resetting link
May 16 13:31:02 arena kernel: [  404.534000] ata2.00: configured for UDMA/33
May 16 13:31:02 arena kernel: [  404.733804] ata2.01: configured for UDMA/25
May 16 13:31:02 arena kernel: [  404.733838] ata2: EH complete
May 16 13:31:02 arena kernel: [  442.981315] loop: module loaded
May 16 13:31:02 arena kernel: [  443.057994] lp0: using parport0 (interrupt-driven).
May 16 13:31:02 arena kernel: [  443.494819] Adding 1502036k swap on /dev/sda5.  Priority:-1 extents:1 across:1502036k
May 16 13:31:02 arena kernel: [  443.884686] EXT3 FS on sda1, internal journal
May 16 13:31:03 arena kernel: [  467.986178] ata2.01: qc timeout (cmd 0xa0)
May 16 13:31:03 arena kernel: [  467.986304]          cdb 43 00 00 00 00 00 00 00  0c 40 00 00 00 00 00 00
May 16 13:31:03 arena kernel: [  467.986308]          res 51/24:03:00:0c:00/00:00:00:00:00/b0 Emask 0x5 (timeout)
May 16 13:31:08 arena kernel: [  473.024103] ata2: port is slow to respond, please be patient (Status 0xd0)
May 16 13:31:13 arena kernel: [  478.008602] ata2: device not ready (errno=-16), forcing hardreset
May 16 13:31:13 arena kernel: [  478.008617] ata2: soft resetting link
May 16 13:31:14 arena kernel: [  478.708367] ata2.00: configured for UDMA/33
May 16 13:31:14 arena kernel: [  478.888179] ata2.01: configured for UDMA/25
May 16 13:31:14 arena kernel: [  478.888227] ata2: EH complete
May 16 13:32:17 arena kernel: [  542.210432] ata2.01: qc timeout (cmd 0xa0)
May 16 13:32:17 arena kernel: [  542.210562]          cdb 43 00 00 00 00 00 00 00  0c 40 00 00 00 00 00 00
May 16 13:32:17 arena kernel: [  542.210566]          res 51/24:03:00:0c:00/00:00:00:00:00/b0 Emask 0x5 (timeout)
May 16 13:32:22 arena kernel: [  547.246629] ata2: port is slow to respond, please be patient (Status 0xd0)
May 16 13:32:27 arena kernel: [  552.222895] ata2: device not ready (errno=-16), forcing hardreset
May 16 13:32:27 arena kernel: [  552.222909] ata2: soft resetting link
May 16 13:32:28 arena kernel: [  552.922641] ata2.00: configured for UDMA/33
May 16 13:32:28 arena kernel: [  553.102463] ata2.01: configured for UDMA/25
May 16 13:32:28 arena kernel: [  553.102510] ata2: EH complete
May 16 13:33:55 arena kernel: [  640.136940] ata2.01: qc timeout (cmd 0xa0)
May 16 13:33:55 arena kernel: [  640.137060]          cdb 43 00 00 00 00 00 00 00  0c 00 00 00 00 00 00 00
May 16 13:33:55 arena kernel: [  640.137063]          res 51/24:03:00:0c:00/00:00:00:00:00/b0 Emask 0x5 (timeout)
May 16 13:34:00 arena kernel: [  645.173137] ata2: port is slow to respond, please be patient (Status 0xd0)
May 16 13:34:05 arena kernel: [  650.149405] ata2: device not ready (errno=-16), forcing hardreset
May 16 13:34:05 arena kernel: [  650.149419] ata2: soft resetting link
May 16 13:34:06 arena kernel: [  650.849149] ata2.00: configured for UDMA/33
May 16 13:34:06 arena kernel: [  651.028971] ata2.01: configured for UDMA/25
May 16 13:34:06 arena kernel: [  651.029016] ata2: EH complete
May 16 13:35:09 arena kernel: [  714.351244] ata2.01: qc timeout (cmd 0xa0)
May 16 13:35:09 arena kernel: [  714.351333]          cdb 43 00 00 00 00 00 00 00  0c 00 00 00 00 00 00 00
May 16 13:35:09 arena kernel: [  714.351337]          res 51/24:03:00:0c:00/00:00:00:00:00/b0 Emask 0x5 (timeout)
May 16 13:35:14 arena kernel: [  719.387440] ata2: port is slow to respond, please be patient (Status 0xd0)
May 16 13:35:19 arena kernel: [  724.363706] ata2: device not ready (errno=-16), forcing hardreset
May 16 13:35:19 arena kernel: [  724.363721] ata2: soft resetting link
May 16 13:35:20 arena kernel: [  725.083436] ata2.00: configured for UDMA/33
May 16 13:35:20 arena kernel: [  725.263259] ata2.01: configured for UDMA/25
May 16 13:35:20 arena kernel: [  725.263304] ata2: EH complete
May 16 13:36:24 arena kernel: [  788.595539] ata2.01: qc timeout (cmd 0xa0)
May 16 13:36:24 arena kernel: [  788.595628]          cdb 43 00 00 00 00 00 00 00  0c 00 00 00 00 00 00 00
May 16 13:36:24 arena kernel: [  788.595632]          res 51/24:03:00:0c:00/00:00:00:00:00/b0 Emask 0x5 (timeout)
May 16 13:36:29 arena kernel: [  793.631722] ata2: port is slow to respond, please be patient (Status 0xd0)
May 16 13:36:34 arena kernel: [  798.607987] ata2: device not ready (errno=-16), forcing hardreset
May 16 13:36:34 arena kernel: [  798.608003] ata2: soft resetting link
May 16 13:36:34 arena kernel: [  799.327715] ata2.00: configured for UDMA/33
May 16 13:36:35 arena kernel: [  799.507538] ata2.01: configured for UDMA/25
May 16 13:36:35 arena kernel: [  799.507583] ata2: EH complete

```

Thanks for the input.

---

### Post by andyrowe on 2009-05-22
sp0nge:
best way to check the drive is run a S.M.A.R.T. check on it. You must first install the tool. Then run it on the suspected drive. It will output info telling you if the drive is bad. Here is a link to a thread in which some folks much brighter then I explained to me how to do it.
[http://ubuntuforums.org/showthread.php?t=1158383](http://ubuntuforums.org/showthread.php?t=1158383)
see post #7 for explaination of how to run S.M.A.R.T. test

---

### Post by apel_2804 on 2009-05-22
Seams that one of your optical drives did not respond properly, try to remove them and have a look if it boot faster, ata2.01 is your sony drive, just unplug the data cable.

[   60.738481] scsi 1:0:1:0: CD-ROM            SONY     CD-RW  CRX140E   1.1b PQ: 0 ANSI: 5

...
May 16 13:34:00 arena kernel: [  645.173137] ata2: port is slow to respond, please be patient (Status 0xd0)
May 16 13:34:05 arena kernel: [  650.149405] ata2: device not ready (errno=-16), forcing hardreset
May 16 13:34:05 arena kernel: [  650.149419] ata2: soft resetting link
May 16 13:34:06 arena kernel: [  650.849149] ata2.00: configured for UDMA/33
May 16 13:34:06 arena kernel: [  651.028971] ata2.01: configured for UDMA/25
May 16 13:34:06 arena kernel: [  651.029016] ata2: EH complete
May 16 13:35:09 arena kernel: [  714.351244] ata2.01: qc timeout (cmd 0xa0)
May 16 13:35:09 arena kernel: [  714.351333]          cdb 43 00 00 00 00 00 00 00  0c 00 00 00 00 00 00 00
May 16 13:35:09 arena kernel: [  714.351337]          res 51/24:03:00:0c:00/00:00:00:00:00/b0 Emask 0x5 (timeout)
May 16 13:35:14 arena kernel: [  719.387440] ata2: port is slow to respond, please be patient (Status 0xd0)
May 16 13:35:19 arena kernel: [  724.363706] ata2: device not ready (errno=-16), forcing hardreset
May 16 13:35:19 arena kernel: [  724.363721] ata2: soft resetting link
May 16 13:35:20 arena kernel: [  725.083436] ata2.00: configured for UDMA/33
May 16 13:35:20 arena kernel: [  725.263259] ata2.01: configured for UDMA/25
May 16 13:35:20 arena kernel: [  725.263304] ata2: EH complete
May 16 13:36:24 arena kernel: [  788.595539] ata2.01: qc timeout (cmd 0xa0)
May 16 13:36:24 arena kernel: [  788.595628]          cdb 43 00 00 00 00 00 00 00  0c 00 00 00 00 00 00 00
May 16 13:36:24 arena kernel: [  788.595632]          res 51/24:03:00:0c:00/00:00:00:00:00/b0 Emask 0x5 (timeout)
...

---

### Post by windependence on 2009-05-22
Yes but the optical isn't his problem.

You need to do an fsck on the drive but it has to be mounted read write so it can be repaired. This means you'll have to boot from a live disk and then mount your entire disk in rw mode. Then do an fsck with the repair option. I'll see if i can dig up an article on this. It's been a while since I had to do this.

-Tim

---

### Post by sp0nge on 2009-05-26
Great info here and I am really hoping to avoid rebuilding this server- though I just bought a new hard drive in case it bites the dust! I will research the fsck option before I take it on the chin and just rebuild...

The optical drives are not the issue. I only use one of the drives to install the OS, and the one is still functioning, so all is well with for my needs... this is just a home server for my family to park files- I just want to learn how to overcome the loss and hopefully get a lesson in data recovery within a linux environment. 

If anyone has a guide or any input on doing this fsck option, I am greatful for the help.. but I'll keep working on it through this week before I just take the loss and install the new drive.

---

### Post by windependence on 2009-05-26
Boot a rescue CD. Run fsck against each Linux partition except swap. Give the correct file system type for each partition. For example:

```
fsck -t ext3  /dev/hda1
fsck -t reiserfs  /dev/hda3

```
You may have to remount your filesystems first in read/write mode by doing this:

```
mount -o remount,rw /
```

That one mounts the root partition (/) but you get the idea. You will want to do each partition on the drive.

Good luck!

-Tim

---

### Post by sp0nge on 2009-05-28
Well I may do that yet.

I pirated a hard drive from a spare machine- one which has been functioning perfectly fine. When I started up the LiveCD, I got another error message after selecting the language.. 

*the numbers in [] change with each reboot
```

[  35.680153] ACPI: Invalid PBLK lenght [5]
<pause for about 2 minutes
[ 170.550830] ata2.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[ 170.515787  ata2.01] : cmd a0/00:00:0c:00/00:00:00:00/0b tag 0 pio 12 in 
[ 170.515787  ata2.01] : status: { DRDY ERR }
```

Google results all point to this being a hard drive issue but how can that be when I cam pop the drive back into it's native machine and it fires right up and works wintout issue?

am I missing something?

I downloaded the rescue disk and will try the other suggestions next.

---

### Post by rhcm123 on 2009-05-28
It may be an issue with your optical drive, but it's more likeley ACPI. Don't know why your server is complaining about it now, but this error has appeared before, particularly with ASUS mobo's, on all kinds of OS's (google it):
[http://ubuntuforums.org/showthread.php?t=937872](http://ubuntuforums.org/showthread.php?t=937872)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/197267](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/197267)
[http://linux.derkeiler.com/Mailing-Lists/Fedora/2007-06/msg04317.html](http://linux.derkeiler.com/Mailing-Lists/Fedora/2007-06/msg04317.html)

The other error (ata2.01) appears to be related, as quoted here from the last link i provided:
```
* Right after PBLK message, I get "Red Hat nash version 6.0.9 starting" - and right after that comes the main problem (takes about a minute or so while the messages repeat a few times):

ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 cdb 0x0 data 4096 in
ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
```

This primarily seems to be a problem between ASUS motherboards and ACPI. Try changing GRUB to boot your kernel with the extra module setting acpi=off to fix this. (ACPI is used for hibernation/standby, which most servers don't need). This blog here should give you an idea on how to change grub settings: [http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)

---

### Post by sp0nge on 2009-05-30
Well I decided to bite the bullet. 

I just took the hard drive out of this old thing and decided to rebuild the server. It's now up and running and being re-configured as I write this. 

Thanks for the input and insight!

---

### Post by rhcm123 on 2009-08-11
> **sp0nge said:**
> Well I decided to bite the bullet. 

I just took the hard drive out of this old thing and decided to rebuild the server. It's now up and running and being re-configured as I write this. 

Thanks for the input and insight!

sorry to ressurect this, but i was just reading through some old subscribed threads here and i noticed this post  -i am actually doing the same thing because my "50,000 volts" surge protector didn't really work in the latest lightening storm... one dead hard drive... and my backup disk is a little courrupted, but e2fsck appears to have fixd it.... :(

---

### Post by garfonzo on 2009-08-12
> **rhcm123 said:**
> sorry to ressurect this, but i was just reading through some old subscribed threads here and i noticed this post  -i am actually doing the same thing because my "50,000 volts" surge protector didn't really work in the latest lightening storm... one dead hard drive... and my backup disk is a little courrupted, but e2fsck appears to have fixd it.... :(

So, did you fix it? I ran into the exact same problem (well, my hard drive went nutz giving the same errors outlined in the OPs reply #12). 

If you are looking for help, I started a thread [I started over here.]("http://ubuntuforums.org/showthread.php?t=1235725") I did resolve the issue and discussed how I did it. I wouldn't want to do it again, but I think it is fixable. For me it boiled down to the file system going into read-only mode as a safeguard against me trying to dump 250GB on a 20GB hard drive (I forgot to mount my 500GB drive and did a backup to a mount point with no disc mounted). I had to fix it from a rescue disk, but after that all was fine again.

---

### Post by rhcm123 on 2009-08-12
> **garfonzo said:**
> So, did you fix it? I ran into the exact same problem (well, my hard drive went nutz giving the same errors outlined in the OPs reply #12). 

If you are looking for help, I started a thread [I started over here.]("http://ubuntuforums.org/showthread.php?t=1235725") I did resolve the issue and discussed how I did it. I wouldn't want to do it again, but I think it is fixable. For me it boiled down to the file system going into read-only mode as a safeguard against me trying to dump 250GB on a 20GB hard drive (I forgot to mount my 500GB drive and did a backup to a mount point with no disc mounted). I had to fix it from a rescue disk, but after that all was fine again.

the backup disk was partially corrupted, so im copying all the data off it then im going to reformat it, to be rid of the damaged file system. the main disk is just screwed, its suffered quit a bit

---

