---
title: "Boot/Wireless problems Serp"
date: 2008-07-29
forum: System76 Support
---

### Post by thinman1189 on 2008-07-29
I've been having a lot of boot and wireless problems. I just got my serp within the past two weeks and the problems have only intensified. There's lots of hangs when I boot. Sometimes multiple per boot, of varying length, sometimes just one long one. 

As for the wireless, it randomly drops sometimes. It may say reconnecting but I can still do most things (visit a new website - yes, digg up a story - no) then after 5 mins of "half internet" I'm fully dropped. Other times I'll just drop and not be able to see any wireless networks. Trying to manually connect to my network doesn't work. The only thing that fixes it is to reboot. Below is the output from dmesg after a boot with 1 long hang.

(more after the code)

```
0
[   13.813529] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 *7 10 12 14 15)
[   13.813599] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[   13.813674] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[   13.813745] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[   13.813815] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[   13.813885] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[   13.813987] Linux Plug and Play Support v0.97 (c) Adam Belay
[   13.814011] pnp: PnP ACPI init
[   13.814016] ACPI: bus type pnp registered
[   13.834009] pnp: PnP ACPI: found 11 devices
[   13.834010] ACPI: ACPI bus type pnp unregistered
[   13.834170] PCI: Using ACPI for IRQ routing
[   13.834171] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   13.834175] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.0
[   13.834177] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.3
[   13.845862] NET: Registered protocol family 8
[   13.845863] NET: Registered protocol family 20
[   13.845886] PCI-GART: No AMD northbridge found.
[   13.845891] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   13.845893] hpet0: 3 64-bit timers, 14318180 Hz
[   13.846915] AppArmor: AppArmor Filesystem Enabled
[   13.849844] Time: hpet clocksource has been installed.
[   13.849857] Switched to high resolution mode on CPU 0
[   13.850604] Switched to high resolution mode on CPU 1
[   13.850808] ACPI: EC: non-query interrupt received, switching to interrupt mode
[   13.857826] system 00:01: iomem range 0xfed1c000-0xfed1ffff could not be reserved
[   13.857828] system 00:01: iomem range 0xfed14000-0xfed17fff could not be reserved
[   13.857830] system 00:01: iomem range 0xfed18000-0xfed18fff could not be reserved
[   13.857833] system 00:01: iomem range 0xfed19000-0xfed19fff could not be reserved
[   13.857835] system 00:01: iomem range 0xe0000000-0xefffffff has been reserved
[   13.857837] system 00:01: iomem range 0xfed20000-0xfed3ffff could not be reserved
[   13.857839] system 00:01: iomem range 0xfed40000-0xfed44fff could not be reserved
[   13.857841] system 00:01: iomem range 0xfed45000-0xfed8ffff could not be reserved
[   13.857846] system 00:05: iomem range 0xfed00000-0xfed003ff could not be reserved
[   13.857850] system 00:07: ioport range 0x680-0x69f has been reserved
[   13.857852] system 00:07: ioport range 0x800-0x80f has been reserved
[   13.857854] system 00:07: ioport range 0x1000-0x107f has been reserved
[   13.857856] system 00:07: ioport range 0x1180-0x11bf has been reserved
[   13.857858] system 00:07: ioport range 0x1640-0x164f has been reserved
[   13.857860] system 00:07: ioport range 0xfe00-0xfe00 has been reserved
[   13.857862] system 00:07: ioport range 0xff00-0xff7f has been reserved
[   13.858164] PCI: Failed to allocate mem resource #6:20000@e0000000 for 0000:01:00.0
[   13.858166] PCI: Bridge: 0000:00:01.0
[   13.858167]   IO window: 2000-2fff
[   13.858170]   MEM window: c4000000-c6ffffff
[   13.858172]   PREFETCH window: d0000000-dfffffff
[   13.858174] PCI: Bridge: 0000:00:1c.0
[   13.858176]   IO window: 3000-3fff
[   13.858181]   MEM window: disabled.
[   13.858185]   PREFETCH window: cc000000-cdffffff
[   13.858190] PCI: Bridge: 0000:00:1c.1
[   13.858192]   IO window: 4000-4fff
[   13.858197]   MEM window: f0000000-f3ffffff
[   13.858201]   PREFETCH window: fa000000-fbffffff
[   13.858206] PCI: Bridge: 0000:00:1c.2
[   13.858209]   IO window: 5000-5fff
[   13.858213]   MEM window: f4000000-f7ffffff
[   13.858217]   PREFETCH window: fc000000-fdffffff
[   13.858221] PCI: Bridge: 0000:00:1c.3
[   13.858224]   IO window: 6000-6fff
[   13.858228]   MEM window: disabled.
[   13.858232]   PREFETCH window: c8000000-c9ffffff
[   13.858237] PCI: Bridge: 0000:00:1c.4
[   13.858237]   IO window: disabled.
[   13.858242]   MEM window: disabled.
[   13.858245]   PREFETCH window: disabled.
[   13.858250] PCI: Bridge: 0000:00:1c.5
[   13.858251]   IO window: disabled.
[   13.858256]   MEM window: f8000000-f80fffff
[   13.858259]   PREFETCH window: disabled.
[   13.858264] PCI: Bridge: 0000:00:1e.0
[   13.858265]   IO window: disabled.
[   13.858270]   MEM window: f8100000-f81fffff
[   13.858274]   PREFETCH window: disabled.
[   13.858286] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
[   13.858289] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   13.858310] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 17
[   13.858314] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   13.858336] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 16 (level, low) -> IRQ 16
[   13.858340] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   13.858362] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 18
[   13.858366] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   13.858387] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 19
[   13.858391] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[   13.858412] ACPI: PCI Interrupt 0000:00:1c.4[A] -> GSI 17 (level, low) -> IRQ 17
[   13.858417] PCI: Setting latency timer of device 0000:00:1c.4 to 64
[   13.858438] ACPI: PCI Interrupt 0000:00:1c.5[B] -> GSI 16 (level, low) -> IRQ 16
[   13.858442] PCI: Setting latency timer of device 0000:00:1c.5 to 64
[   13.858455] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   13.858461] NET: Registered protocol family 2
[   13.893844] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[   13.894676] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[   13.897898] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   13.898456] TCP: Hash tables configured (established 524288 bind 65536)
[   13.898458] TCP reno registered
[   13.909854] checking if image is initramfs... it is
[   14.453687] Freeing initrd memory: 7519k freed
[   14.456313] Simple Boot Flag at 0x38 set to 0x1
[   14.456971] audit: initializing netlink socket (disabled)
[   14.456987] audit(1217300717.252:1): initialized
[   14.458632] VFS: Disk quotas dquot_6.5.1
[   14.458678] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   14.458765] io scheduler noop registered
[   14.458767] io scheduler anticipatory registered
[   14.458768] io scheduler deadline registered
[   14.458845] io scheduler cfq registered (default)
[   14.464887] Boot video device is 0000:01:00.0
[   14.465017] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   14.465044] assign_interrupt_mode Found MSI capability
[   14.465066] Allocate Port Service[0000:00:01.0:pcie00]
[   14.465093] Allocate Port Service[0000:00:01.0:pcie02]
[   14.465154] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   14.465206] assign_interrupt_mode Found MSI capability
[   14.465248] Allocate Port Service[0000:00:1c.0:pcie00]
[   14.465271] Allocate Port Service[0000:00:1c.0:pcie02]
[   14.465356] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   14.465409] assign_interrupt_mode Found MSI capability
[   14.465450] Allocate Port Service[0000:00:1c.1:pcie00]
[   14.465474] Allocate Port Service[0000:00:1c.1:pcie02]
[   14.465560] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   14.465613] assign_interrupt_mode Found MSI capability
[   14.465654] Allocate Port Service[0000:00:1c.2:pcie00]
[   14.465678] Allocate Port Service[0000:00:1c.2:pcie02]
[   14.465764] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[   14.465817] assign_interrupt_mode Found MSI capability
[   14.465864] Allocate Port Service[0000:00:1c.3:pcie00]
[   14.465888] Allocate Port Service[0000:00:1c.3:pcie02]
[   14.465974] PCI: Setting latency timer of device 0000:00:1c.4 to 64
[   14.466027] assign_interrupt_mode Found MSI capability
[   14.466068] Allocate Port Service[0000:00:1c.4:pcie00]
[   14.466090] Allocate Port Service[0000:00:1c.4:pcie02]
[   14.466177] PCI: Setting latency timer of device 0000:00:1c.5 to 64
[   14.466229] assign_interrupt_mode Found MSI capability
[   14.466271] Allocate Port Service[0000:00:1c.5:pcie00]
[   14.466296] Allocate Port Service[0000:00:1c.5:pcie02]
[   14.483694] Real Time Clock Driver v1.12ac
[   14.483856] hpet_resources: 0xfed00000 is busy
[   14.483876] Linux agpgart interface v0.102
[   14.483877] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   14.484652] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   14.484698] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   14.484761] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   14.527152] serio: i8042 KBD port at 0x60,0x64 irq 1
[   14.527155] serio: i8042 AUX port at 0x60,0x64 irq 12
[   14.536799] mice: PS/2 mouse device common for all mice
[   14.536825] cpuidle: using governor ladder
[   14.536826] cpuidle: using governor menu
[   14.536923] NET: Registered protocol family 1
[   14.536992] registered taskstats version 1
[   14.537081]   Magic number: 0:15:59
[   14.537121] /build/buildd/linux-2.6.24/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   14.537123] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   14.537124] EDD information not available.
[   14.537129] Freeing unused kernel memory: 320k freed
[   14.563685] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   15.686419] fuse init (API version 7.9)
[   15.734209] ACPI: SSDT BFED9508, 02BC (r1  PmRef  Cpu0Ist     3000 INTL 20050624)
[   15.734365] ACPI: SSDT BFED8E99, 05EA (r1  PmRef  Cpu0Cst     3001 INTL 20050624)
[   15.735850] Monitor-Mwait will be used to enter C-1 state
[   15.735852] Monitor-Mwait will be used to enter C-2 state
[   15.735853] Monitor-Mwait will be used to enter C-3 state
[   15.735940] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   15.735943] ACPI: Processor [CPU0] (supports 8 throttling states)
[   15.736106] ACPI: SSDT BFED97C4, 00C8 (r1  PmRef  Cpu1Ist     3000 INTL 20050624)
[   15.736248] ACPI: SSDT BFED9483, 0085 (r1  PmRef  Cpu1Cst     3000 INTL 20050624)
[   15.737049] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[   15.737053] ACPI: Processor [CPU1] (supports 8 throttling states)
[   15.886957] usbcore: registered new interface driver usbfs
[   15.886972] usbcore: registered new interface driver hub
[   15.887275] usbcore: registered new device driver usb
[   15.891212] USB Universal Host Controller Interface driver v3.0
[   15.891252] ACPI: PCI Interrupt 0000:00:1a.0[A] -> GSI 16 (level, low) -> IRQ 16
[   15.891261] PCI: Setting latency timer of device 0000:00:1a.0 to 64
[   15.891264] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[   15.891435] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[   15.891465] uhci_hcd 0000:00:1a.0: irq 16, io base 0x00001800
[   15.891554] usb usb1: configuration #1 chosen from 1 choice
[   15.891568] hub 1-0:1.0: USB hub found
[   15.891573] hub 1-0:1.0: 2 ports detected
[   15.995512] ACPI: PCI Interrupt 0000:00:1a.1[B] -> GSI 21 (level, low) -> IRQ 21
[   15.995522] PCI: Setting latency timer of device 0000:00:1a.1 to 64
[   15.995525] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[   15.995540] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
[   15.995569] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00001820
[   15.995643] usb usb2: configuration #1 chosen from 1 choice
[   15.995658] hub 2-0:1.0: USB hub found
[   15.995662] hub 2-0:1.0: 2 ports detected
[   16.099366] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 23
[   16.099377] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   16.099380] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   16.099398] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 3
[   16.099428] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001840
[   16.099505] usb usb3: configuration #1 chosen from 1 choice
[   16.099526] hub 3-0:1.0: USB hub found
[   16.099531] hub 3-0:1.0: 2 ports detected
[   16.099687] SCSI subsystem initialized
[   16.164637] libata version 3.00 loaded.
[   16.203184] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 19
[   16.203192] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   16.203195] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   16.203210] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 4
[   16.203238] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001860
[   16.203308] usb usb4: configuration #1 chosen from 1 choice
[   16.203321] hub 4-0:1.0: USB hub found
[   16.203325] hub 4-0:1.0: 2 ports detected
[   16.322944] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[   16.322952] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   16.322955] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   16.322970] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 5
[   16.322999] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001880
[   16.323069] usb usb5: configuration #1 chosen from 1 choice
[   16.323084] hub 5-0:1.0: USB hub found
[   16.323088] hub 5-0:1.0: 2 ports detected
[   16.426933] ACPI: PCI Interrupt 0000:00:1a.7[C] -> GSI 18 (level, low) -> IRQ 18
[   16.428577] PCI: Setting latency timer of device 0000:00:1a.7 to 64
[   16.428583] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[   16.428625] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 6
[   16.432535] ehci_hcd 0000:00:1a.7: debug port 1
[   16.432540] PCI: cache line size of 32 is not supported by device 0000:00:1a.7
[   16.432545] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xf8404800
[   16.446727] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   16.446804] usb usb6: configuration #1 chosen from 1 choice
[   16.446821] hub 6-0:1.0: USB hub found
[   16.446826] hub 6-0:1.0: 4 ports detected
[   16.550685] ACPI: PCI Interrupt 0000:0e:06.0[A] -> GSI 22 (level, low) -> IRQ 22
[   16.603780] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[22]  MMIO=[f8100000-f81007ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[   16.607040] ahci 0000:00:1f.2: version 3.0
[   16.607082] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 19
[   16.630968] Clocksource tsc unstable (delta = -70607921 ns)
[   16.647122] usb 6-2: new high speed USB device using ehci_hcd and address 2
[   16.805567] usb 6-2: configuration #1 chosen from 1 choice
[   17.037297] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 3 Gbps 0x7 impl SATA mode
[   17.037302] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part 
[   17.037309] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   17.037831] scsi0 : ahci
[   17.037977] scsi1 : ahci
[   17.038085] scsi2 : ahci
[   17.038144] ata1: SATA max UDMA/133 abar m2048@0xf8404000 port 0xf8404100 irq 504
[   17.038147] ata2: SATA max UDMA/133 abar m2048@0xf8404000 port 0xf8404180 irq 504
[   17.038149] ata3: SATA max UDMA/133 abar m2048@0xf8404000 port 0xf8404200 irq 504
[   17.075584] usb 2-1: new full speed USB device using uhci_hcd and address 2
[   17.095988] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00023f82cd404c8f]
[   17.144975] usb 2-1: configuration #1 chosen from 1 choice
[   17.195144] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   17.196444] ata1.00: ATA-7: ST9200420AS, 3.AAA, max UDMA/133
[   17.196446] ata1.00: 390721968 sectors, multi 16: LBA48 NCQ (depth 31/32)
[   17.198058] ata1.00: configured for UDMA/133
[   17.218008] usb 2-2: new full speed USB device using uhci_hcd and address 3
[   17.262057] usb 2-2: configuration #1 chosen from 1 choice
[   17.274551] ata2: SATA link down (SStatus 0 SControl 300)
[   17.333452] ata3: SATA link down (SStatus 0 SControl 300)
[   17.333572] scsi 0:0:0:0: Direct-Access     ATA      ST9200420AS      3.AA PQ: 0 ANSI: 5
[   17.333650] tg3.c:v3.86 (November 9, 2007)
[   17.333729] ACPI: PCI Interrupt 0000:04:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[   17.333743] PCI: Setting latency timer of device 0000:04:00.0 to 64
[   17.338756] Driver 'sd' needs updating - please use bus_type methods
[   17.345911] sd 0:0:0:0: [sda] 390721968 512-byte hardware sectors (200050 MB)
[   17.345927] sd 0:0:0:0: [sda] Write Protect is off
[   17.345930] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   17.345951] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   17.346005] sd 0:0:0:0: [sda] 390721968 512-byte hardware sectors (200050 MB)
[   17.346022] sd 0:0:0:0: [sda] Write Protect is off
[   17.346024] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   17.346034] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   17.346036]  sda: sda1 sda2 sda3
[   17.357000] sd 0:0:0:0: [sda] Attached SCSI disk
[   17.359119] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   17.538940] Attempting manual resume
[   17.538942] swsusp: Resume From Partition 8:2
[   17.538943] PM: Checking swsusp image.
[   17.539099] PM: Resume from disk failed.
[   17.551790] kjournald starting.  Commit interval 5 seconds
[   17.551815] EXT3-fs: mounted filesystem with ordered data mode.
[   17.933898] eth0: Tigon3 [partno(none) rev b002 PHY(5787)] (PCI Express) 10/100/1000Base-T Ethernet 00:1b:38:d6:a1:c3
[   17.933901] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] WireSpeed[1] TSOcap[1]
[   17.933903] eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[   17.934177] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 23
[   17.935616] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   17.935621] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   17.935663] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 7
[   17.939557] ehci_hcd 0000:00:1d.7: debug port 1
[   17.939562] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   17.939567] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf8404c00
[   17.952624] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   17.952746] usb usb7: configuration #1 chosen from 1 choice
[   17.952762] hub 7-0:1.0: USB hub found
[   17.952766] hub 7-0:1.0: 6 ports detected
[   18.418224] usb 5-2: new low speed USB device using uhci_hcd and address 2
[   18.544433] usb 5-2: configuration #1 chosen from 1 choice
[   23.301641] ip_tables: (C) 2000-2006 Netfilter Core Team
[   23.330482] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   23.643412] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   23.663355] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   23.794754] input: Power Button (FF) as /devices/virtual/input/input2
[   23.826592] ACPI: Power Button (FF) [PWRF]
[   23.826634] input: Lid Switch as /devices/virtual/input/input3
[   23.826690] ACPI: Lid Switch [LID0]
[   23.826718] input: Power Button (CM) as /devices/virtual/input/input4
[   23.858539] ACPI: Power Button (CM) [PWRB]
[   23.858601] ACPI: WMI-Acer: Mapper loaded
[   23.876767] ACPI: AC Adapter [ACAD] (on-line)
[   24.008661] nvidia: module license 'NVIDIA' taints kernel.
[   24.015390] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:02/LNXVIDEO:00/input/input5
[   24.042249] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   24.055643] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:01/input/input6
[   24.313836] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   24.327855] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   24.327869] PCI: Setting latency timer of device 0000:01:00.0 to 64
[   24.327940] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  169.12  Thu Feb 14 17:51:09 PST 2008
[   24.349128] ACPI: Battery Slot [BAT1] (battery present)
[   24.409098] Bluetooth: Core ver 2.11
[   24.422290] NET: Registered protocol family 31
[   24.422292] Bluetooth: HCI device and connection manager initialized
[   24.422294] Bluetooth: HCI socket layer initialized
[   24.564513] Linux video capture interface: v2.00
[   24.581440] Bluetooth: HCI USB driver ver 2.9
[   24.584899] usbcore: registered new interface driver hci_usb
[   24.670834] iTCO_vendor_support: vendor-support=0
[   24.683712] ricoh-mmc: Ricoh MMC Controller disabling driver
[   24.683715] ricoh-mmc: Copyright(c) Philip Langdale
[   24.683746] ricoh-mmc: Ricoh MMC controller found at 0000:0e:06.2 [1180:0843] (rev 12)
[   24.683758] ricoh-mmc: Controller is now disabled.
[   24.740948] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   24.741007] iTCO_wdt: Found a ICH8M TCO device (Version=2, TCOBASE=0x1060)
[   24.741041] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   24.807248] uvcvideo: Found UVC 1.00 device USB 2.0 Camera (04f2:b018)
[   24.809158] usbcore: registered new interface driver uvcvideo
[   24.809160] USB Video Class driver (v0.1.0)
[   24.845005] sdhci: Secure Digital Host Controller Interface driver
[   24.845008] sdhci: Copyright(c) Pierre Ossman
[   24.845040] sdhci: SDHCI controller found at 0000:0e:06.1 [1180:0822] (rev 22)
[   24.845061] ACPI: PCI Interrupt 0000:0e:06.1[B] -> GSI 23 (level, low) -> IRQ 23
[   24.846554] sdhci:slot0: Will use DMA mode even though HW doesn't fully claim to support it.
[   24.846617] mmc0: SDHCI at 0xf8100800 irq 23 DMA
[   24.922123] input: PC Speaker as /devices/platform/pcspkr/input/input7
[   24.936912] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 19 (level, low) -> IRQ 19
[   24.936940] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   24.936949] ACPI: PCI interrupt for device 0000:00:1f.1 disabled
[   24.976965] usbcore: registered new interface driver hiddev
[   24.992046] input: Logitech USB Trackball as /devices/pci0000:00/0000:00:1d.2/usb5/5-2/5-2:1.0/input/input8
[   25.005552] ata_piix 0000:00:1f.1: version 2.12
[   25.005567] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 19 (level, low) -> IRQ 19
[   25.005596] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   25.015734] input,hidraw0: USB HID v1.10 Mouse [Logitech USB Trackball] on usb-0000:00:1d.2-2
[   25.015746] usbcore: registered new interface driver usbhid
[   25.015748] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   25.031690] scsi3 : ata_piix
[   25.033033] scsi4 : ata_piix
[   25.033461] ata4: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x18a0 irq 14
[   25.033463] ata5: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x18a8 irq 15
[   25.175639] iwl4965: Intel(R) Wireless WiFi Link 4965AGN driver for Linux, 1.2.0
[   25.175642] iwl4965: Copyright(c) 2003-2007 Intel Corporation
[   25.359883] ata4.00: ATAPI: MATSHITADVD-RAM UJ-850S, 1.60, max UDMA/33
[   25.535467] ata4.00: configured for UDMA/33
[   25.703976] scsi 3:0:0:0: CD-ROM            MATSHITA DVD-RAM UJ-850S  1.60 PQ: 0 ANSI: 5
[   25.704033] scsi 3:0:0:0: Attached scsi generic sg1 type 5
[   25.710756] ACPI: PCI Interrupt 0000:0c:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[   25.710793] PCI: Setting latency timer of device 0000:0c:00.0 to 64
[   25.712263] iwl4965: Detected Intel Wireless WiFi Link 4965AGN
[   25.712339] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 20 (level, low) -> IRQ 20
[   25.713693] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   26.514261] Driver 'sr' needs updating - please use bus_type methods
[   26.520999] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[   26.521003] Uniform CD-ROM driver Revision: 3.20
[   26.521055] sr 3:0:0:0: Attached scsi CD-ROM sr0
[   26.766641] iwl4965: Tunable channels: 11 802.11bg, 13 802.11a channels
[   26.767036] wmaster0: Selected rate control algorithm 'iwl-4965-rs'
[   27.110037] input: ImPS/2 Logitech Wheel Mouse as /devices/platform/i8042/serio1/input/input9
[   27.149803] lp: driver loaded but no devices found
[   27.256596] Adding 3862296k swap on /dev/sda2.  Priority:-1 extents:1 across:3862296k
[   27.558510] EXT3 FS on sda1, internal journal
[   27.989615] kjournald starting.  Commit interval 5 seconds
[   27.989887] EXT3 FS on sda3, internal journal
[   27.989893] EXT3-fs: mounted filesystem with ordered data mode.
[   28.680682] No dock devices found.
[  328.690410] iwl4965: Microcode SW error detected.  Restarting 0x82000000.
[  331.692082] iwl4965: Can't stop Rx DMA.
[  345.275945] NET: Registered protocol family 10
[  345.276481] lo: Disabled Privacy Extensions
[  345.277404] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  345.278437] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  357.547758] CPU0 attaching NULL sched-domain.
[  357.547763] CPU1 attaching NULL sched-domain.
[  357.574723] CPU0 attaching sched-domain:
[  357.574729]  domain 0: span 03
[  357.574730]   groups: 01 02
[  357.574733]   domain 1: span 03
[  357.574734]    groups: 03
[  357.574735] CPU1 attaching sched-domain:
[  357.574737]  domain 0: span 03
[  357.574738]   groups: 02 01
[  357.574740]   domain 1: span 03
[  357.574741]    groups: 03
[  358.945184] NET: Registered protocol family 17
[  360.741138] wlan0: Initial auth_alg=1
[  360.741150] wlan0: authenticate with AP 00:0c:41:6e:6a:d4
[  360.745143] wlan0: RX authentication from 00:0c:41:6e:6a:d4 (alg=1 transaction=2 status=0)
[  360.745150] wlan0: replying to auth challenge
[  360.749115] wlan0: RX authentication from 00:0c:41:6e:6a:d4 (alg=1 transaction=4 status=0)
[  360.749123] wlan0: authenticated
[  360.749128] wlan0: associate with AP 00:0c:41:6e:6a:d4
[  360.752823] wlan0: RX AssocResp from 00:0c:41:6e:6a:d4 (capab=0x411 status=0 aid=1)
[  360.752830] wlan0: associated
[  360.752836] wlan0: CTS protection enabled (BSSID=00:0c:41:6e:6a:d4)
[  360.764573] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  371.193181] wlan0: no IPv6 routers present
[  494.364873] wlan0: CTS protection disabled (BSSID=xx:xx:xx:xx:xx:xx)
[  494.767719] wlan0: CTS protection enabled (BSSID=xx:xx:xx:xx:xx:xx)

```

```
[   28.680682] No dock devices found.
[  328.690410] iwl4965: Microcode SW error detected.  Restarting 0x82000000.
[  331.692082] iwl4965: Can't stop Rx DMA.
```

I googled ```
iwl4965: Microcode SW error detected.  Restarting 0x82000000.
```

and got these [https://bugs.launchpad.net/linux/+bug/200509](https://bugs.launchpad.net/linux/+bug/200509) [https://lists.ubuntu.com/archives/kernel-bugs/2008-April/034929.html](https://lists.ubuntu.com/archives/kernel-bugs/2008-April/034929.html) [http://www.mail-archive.com/debian-kernel@lists.debian.org/msg33086.html](http://www.mail-archive.com/debian-kernel@lists.debian.org/msg33086.html) but I'm not sure if it's the same bug. 

There's another boot/network related thread for serp [http://ubuntuforums.org/showthread.php?t=837423](http://ubuntuforums.org/showthread.php?t=837423) but I'm not sure if that's relevant either. 

Also, I'm not sure if it's relevant but the last 2 lines of code repeat a lot if i run dmesg after a while. ```
[  494.364873] wlan0: CTS protection disabled (BSSID=xx:xx:xx:xx:xx:xx)
[  494.767719] wlan0: CTS protection enabled (BSSID=xx:xx:xx:xx:xx:xx)
``` (x's replaced)


The following is my system specs.
> Serval Performance
Options
*Operating System : Ubuntu 64 Bit 8.04 (Hardy Heron)
*Processor : Core 2 Duo T9300 2.5 GHz 800 MHz
*Memory : 4 GB - 2 x 2 GB DDR2 667 MHZ
*Hard Drive : 200 GB 7200 RPM SATA
*Optical Drive : CD-RW / DVD-RW
*Wireless : 802.11 agn
*Bluetooth : Bluetooth

Thanks in advance for the help.

---

### Post by thomasaaron on 2008-07-29
OK. Let's fix your booting issue first. Then see if that has any affect on the wireless. If not, we will fix the wireless next.

Here is how to fix the booting issue.

1. Go into your BIOS setup menus, to the Advanced tab, and disable AHCI.
(To get into your BIOS setup menu, press F2 when you see the manufacturer splash screen.)

2. add clocksource=jiffies to your kernel option by going to a terminal (Applications > Accessories > Terminal) and entering this command...

```
sudo gedit /boot/grub/menu.lst
```

First, find the line in the resulting file that looks something like this (yours may have different options, but it will start with "# defoptions=")...

# defoptions=quiet splash

...and add clocksource=jiffies to it to make it look something like this...

# defoptions=quiet splash clocksource=jiffies


Next, locate your first kernel line and add clocksource=jiffies
 to it, making it look something like this...

kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=3887ab68-7cd4-462e-9d56-8b2096f10353 clocksource=jiffies ro quiet splash

Save and Reboot.

Does that fix it?

---

### Post by thinman1189 on 2008-07-29
I've gotta go out to pick up my mom from the airport, so I'll try sometime today.

Here's another dmesg from the boot from right now. The splash screen wouldn't even load until I hit enter.

```
[   14.381795] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[   14.381887] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[   14.381976] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[   14.382066] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP05._PRT]
[   14.382156] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP06._PRT]
[   14.382261] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[   14.385663] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 *5 6 7 10 12 14 15)
[   14.385735] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[   14.385806] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 *7 10 12 14 15)
[   14.385876] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[   14.385951] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[   14.386022] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[   14.386091] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[   14.386161] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[   14.386263] Linux Plug and Play Support v0.97 (c) Adam Belay
[   14.386288] pnp: PnP ACPI init
[   14.386293] ACPI: bus type pnp registered
[   14.406328] pnp: PnP ACPI: found 11 devices
[   14.406330] ACPI: ACPI bus type pnp unregistered
[   14.406489] PCI: Using ACPI for IRQ routing
[   14.406490] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   14.406493] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.0
[   14.406496] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.3
[   14.418181] NET: Registered protocol family 8
[   14.418182] NET: Registered protocol family 20
[   14.418206] PCI-GART: No AMD northbridge found.
[   14.418210] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   14.418213] hpet0: 3 64-bit timers, 14318180 Hz
[   14.419234] AppArmor: AppArmor Filesystem Enabled
[   14.422162] Time: hpet clocksource has been installed.
[   14.422170] Switched to high resolution mode on CPU 0
[   14.422922] Switched to high resolution mode on CPU 1
[   14.430142] system 00:01: iomem range 0xfed1c000-0xfed1ffff could not be reserved
[   14.430145] system 00:01: iomem range 0xfed14000-0xfed17fff could not be reserved
[   14.430147] system 00:01: iomem range 0xfed18000-0xfed18fff could not be reserved
[   14.430149] system 00:01: iomem range 0xfed19000-0xfed19fff could not be reserved
[   14.430151] system 00:01: iomem range 0xe0000000-0xefffffff has been reserved
[   14.430153] system 00:01: iomem range 0xfed20000-0xfed3ffff could not be reserved
[   14.430156] system 00:01: iomem range 0xfed40000-0xfed44fff could not be reserved
[   14.430158] system 00:01: iomem range 0xfed45000-0xfed8ffff could not be reserved
[   14.430163] system 00:05: iomem range 0xfed00000-0xfed003ff could not be reserved
[   14.430167] system 00:07: ioport range 0x680-0x69f has been reserved
[   14.430169] system 00:07: ioport range 0x800-0x80f has been reserved
[   14.430171] system 00:07: ioport range 0x1000-0x107f has been reserved
[   14.430173] system 00:07: ioport range 0x1180-0x11bf has been reserved
[   14.430175] system 00:07: ioport range 0x1640-0x164f has been reserved
[   14.430177] system 00:07: ioport range 0xfe00-0xfe00 has been reserved
[   14.430179] system 00:07: ioport range 0xff00-0xff7f has been reserved
[   14.430481] PCI: Failed to allocate mem resource #6:20000@e0000000 for 0000:01:00.0
[   14.430483] PCI: Bridge: 0000:00:01.0
[   14.430485]   IO window: 2000-2fff
[   14.430487]   MEM window: c4000000-c6ffffff
[   14.430489]   PREFETCH window: d0000000-dfffffff
[   14.430491] PCI: Bridge: 0000:00:1c.0
[   14.430494]   IO window: 3000-3fff
[   14.430499]   MEM window: disabled.
[   14.430502]   PREFETCH window: cc000000-cdffffff
[   14.430507] PCI: Bridge: 0000:00:1c.1
[   14.430509]   IO window: 4000-4fff
[   14.430514]   MEM window: f0000000-f3ffffff
[   14.430517]   PREFETCH window: fa000000-fbffffff
[   14.430522] PCI: Bridge: 0000:00:1c.2
[   14.430524]   IO window: 5000-5fff
[   14.430530]   MEM window: f4000000-f7ffffff
[   14.430533]   PREFETCH window: fc000000-fdffffff
[   14.430538] PCI: Bridge: 0000:00:1c.3
[   14.430540]   IO window: 6000-6fff
[   14.430545]   MEM window: disabled.
[   14.430548]   PREFETCH window: c8000000-c9ffffff
[   14.430553] PCI: Bridge: 0000:00:1c.4
[   14.430554]   IO window: disabled.
[   14.430558]   MEM window: disabled.
[   14.430562]   PREFETCH window: disabled.
[   14.430566] PCI: Bridge: 0000:00:1c.5
[   14.430567]   IO window: disabled.
[   14.430572]   MEM window: f8000000-f80fffff
[   14.430575]   PREFETCH window: disabled.
[   14.430580] PCI: Bridge: 0000:00:1e.0
[   14.430581]   IO window: disabled.
[   14.430586]   MEM window: f8100000-f81fffff
[   14.430589]   PREFETCH window: disabled.
[   14.430602] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
[   14.430605] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   14.430626] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 17
[   14.430630] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   14.430652] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 16 (level, low) -> IRQ 16
[   14.430656] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   14.430678] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 18
[   14.430682] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   14.430703] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 19
[   14.430707] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[   14.430727] ACPI: PCI Interrupt 0000:00:1c.4[A] -> GSI 17 (level, low) -> IRQ 17
[   14.430732] PCI: Setting latency timer of device 0000:00:1c.4 to 64
[   14.430753] ACPI: PCI Interrupt 0000:00:1c.5[B] -> GSI 16 (level, low) -> IRQ 16
[   14.430757] PCI: Setting latency timer of device 0000:00:1c.5 to 64
[   14.430770] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   14.430776] NET: Registered protocol family 2
[   14.466161] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[   14.466993] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[   14.470218] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   14.470772] TCP: Hash tables configured (established 524288 bind 65536)
[   14.470774] TCP reno registered
[   14.482172] checking if image is initramfs... it is
[   15.026202] Freeing initrd memory: 7519k freed
[   15.030109] ACPI: EC: non-query interrupt received, switching to interrupt mode
[   15.030236] Simple Boot Flag at 0x38 set to 0x1
[   15.030884] audit: initializing netlink socket (disabled)
[   15.030900] audit(1217364635.252:1): initialized
[   15.032542] VFS: Disk quotas dquot_6.5.1
[   15.032588] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   15.032674] io scheduler noop registered
[   15.032676] io scheduler anticipatory registered
[   15.032677] io scheduler deadline registered
[   15.032754] io scheduler cfq registered (default)
[   15.038786] Boot video device is 0000:01:00.0
[   15.038918] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   15.038945] assign_interrupt_mode Found MSI capability
[   15.038967] Allocate Port Service[0000:00:01.0:pcie00]
[   15.038994] Allocate Port Service[0000:00:01.0:pcie02]
[   15.039054] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   15.039107] assign_interrupt_mode Found MSI capability
[   15.039148] Allocate Port Service[0000:00:1c.0:pcie00]
[   15.039172] Allocate Port Service[0000:00:1c.0:pcie02]
[   15.039258] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   15.039310] assign_interrupt_mode Found MSI capability
[   15.039352] Allocate Port Service[0000:00:1c.1:pcie00]
[   15.039375] Allocate Port Service[0000:00:1c.1:pcie02]
[   15.039461] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   15.039514] assign_interrupt_mode Found MSI capability
[   15.039555] Allocate Port Service[0000:00:1c.2:pcie00]
[   15.039579] Allocate Port Service[0000:00:1c.2:pcie02]
[   15.039665] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[   15.039718] assign_interrupt_mode Found MSI capability
[   15.039759] Allocate Port Service[0000:00:1c.3:pcie00]
[   15.039782] Allocate Port Service[0000:00:1c.3:pcie02]
[   15.039867] PCI: Setting latency timer of device 0000:00:1c.4 to 64
[   15.039920] assign_interrupt_mode Found MSI capability
[   15.039961] Allocate Port Service[0000:00:1c.4:pcie00]
[   15.039985] Allocate Port Service[0000:00:1c.4:pcie02]
[   15.040070] PCI: Setting latency timer of device 0000:00:1c.5 to 64
[   15.040123] assign_interrupt_mode Found MSI capability
[   15.040164] Allocate Port Service[0000:00:1c.5:pcie00]
[   15.040190] Allocate Port Service[0000:00:1c.5:pcie02]
[   15.057834] Real Time Clock Driver v1.12ac
[   15.057993] hpet_resources: 0xfed00000 is busy
[   15.058013] Linux agpgart interface v0.102
[   15.058014] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   15.058781] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   15.058828] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   15.058892] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   15.105214] serio: i8042 KBD port at 0x60,0x64 irq 1
[   15.105218] serio: i8042 AUX port at 0x60,0x64 irq 12
[   15.117103] mice: PS/2 mouse device common for all mice
[   15.117129] cpuidle: using governor ladder
[   15.117130] cpuidle: using governor menu
[   15.117227] NET: Registered protocol family 1
[   15.117296] registered taskstats version 1
[   15.117386]   Magic number: 0:97:853
[   15.117403]   hash matches device ptyv5
[   15.117424] /build/buildd/linux-2.6.24/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   15.117426] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   15.117427] EDD information not available.
[   15.117432] Freeing unused kernel memory: 320k freed
[   15.144083] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   16.254880] fuse init (API version 7.9)
[   16.279895] ACPI: SSDT BFED9508, 02BC (r1  PmRef  Cpu0Ist     3000 INTL 20050624)
[   16.280049] ACPI: SSDT BFED8E99, 05EA (r1  PmRef  Cpu0Cst     3001 INTL 20050624)
[   16.281551] Monitor-Mwait will be used to enter C-1 state
[   16.281553] Monitor-Mwait will be used to enter C-2 state
[   16.281554] Monitor-Mwait will be used to enter C-3 state
[   16.281650] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   16.281653] ACPI: Processor [CPU0] (supports 8 throttling states)
[   16.281824] ACPI: SSDT BFED97C4, 00C8 (r1  PmRef  Cpu1Ist     3000 INTL 20050624)
[   16.281966] ACPI: SSDT BFED9483, 0085 (r1  PmRef  Cpu1Cst     3000 INTL 20050624)
[   16.282665] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[   16.282668] ACPI: Processor [CPU1] (supports 8 throttling states)
[   16.373120] usbcore: registered new interface driver usbfs
[   16.373135] usbcore: registered new interface driver hub
[   16.373406] usbcore: registered new device driver usb
[   16.373955] USB Universal Host Controller Interface driver v3.0
[   16.373993] ACPI: PCI Interrupt 0000:00:1a.0[A] -> GSI 16 (level, low) -> IRQ 16
[   16.374001] PCI: Setting latency timer of device 0000:00:1a.0 to 64
[   16.374004] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[   16.374162] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[   16.374192] uhci_hcd 0000:00:1a.0: irq 16, io base 0x00001800
[   16.374276] usb usb1: configuration #1 chosen from 1 choice
[   16.374290] hub 1-0:1.0: USB hub found
[   16.374294] hub 1-0:1.0: 2 ports detected
[   16.475973] ACPI: PCI Interrupt 0000:00:1a.1[B] -> GSI 21 (level, low) -> IRQ 21
[   16.475982] PCI: Setting latency timer of device 0000:00:1a.1 to 64
[   16.475985] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[   16.476000] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
[   16.476029] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00001820
[   16.476099] usb usb2: configuration #1 chosen from 1 choice
[   16.476114] hub 2-0:1.0: USB hub found
[   16.476118] hub 2-0:1.0: 2 ports detected
[   16.542069] SCSI subsystem initialized
[   16.559790] libata version 3.00 loaded.
[   16.579821] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 23
[   16.579831] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   16.579834] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   16.579851] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 3
[   16.579880] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001840
[   16.579953] usb usb3: configuration #1 chosen from 1 choice
[   16.579969] hub 3-0:1.0: USB hub found
[   16.579973] hub 3-0:1.0: 2 ports detected
[   16.683637] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 19
[   16.683646] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   16.683650] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   16.683664] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 4
[   16.683700] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001860
[   16.683777] usb usb4: configuration #1 chosen from 1 choice
[   16.683792] hub 4-0:1.0: USB hub found
[   16.683796] hub 4-0:1.0: 2 ports detected
[   16.787468] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[   16.787476] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   16.787479] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   16.787495] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 5
[   16.787528] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001880
[   16.787617] usb usb5: configuration #1 chosen from 1 choice
[   16.787634] hub 5-0:1.0: USB hub found
[   16.787640] hub 5-0:1.0: 2 ports detected
[   16.844446] ACPI: PCI Interrupt 0000:00:1a.7[C] -> GSI 18 (level, low) -> IRQ 18
[   16.846130] PCI: Setting latency timer of device 0000:00:1a.7 to 64
[   16.846135] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[   16.846174] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 6
[   16.850089] ehci_hcd 0000:00:1a.7: debug port 1
[   16.850094] PCI: cache line size of 32 is not supported by device 0000:00:1a.7
[   16.850099] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xf8404800
[   16.865022] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   16.865100] usb usb6: configuration #1 chosen from 1 choice
[   16.865116] hub 6-0:1.0: USB hub found
[   16.865121] hub 6-0:1.0: 4 ports detected
[   52.126930] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 23
[   52.128287] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   52.128292] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   52.128333] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 7
[   52.132236] ehci_hcd 0000:00:1d.7: debug port 1
[   52.132246] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   52.132251] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf8404c00
[   52.145159] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   52.145275] usb usb7: configuration #1 chosen from 1 choice
[   52.145292] hub 7-0:1.0: USB hub found
[   52.145296] hub 7-0:1.0: 6 ports detected
[   52.216027] tg3.c:v3.86 (November 9, 2007)
[   52.216106] ACPI: PCI Interrupt 0000:04:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[   52.216120] PCI: Setting latency timer of device 0000:04:00.0 to 64
[   52.398174] Clocksource tsc unstable (delta = -256728423 ns)
[   52.438252] usb 6-2: new high speed USB device using ehci_hcd and address 2
[   52.597632] usb 6-2: configuration #1 chosen from 1 choice
[   52.599529] eth0: Tigon3 [partno(none) rev b002 PHY(5787)] (PCI Express) 10/100/1000Base-T Ethernet 00:1b:38:d6:a1:c3
[   52.599533] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] WireSpeed[1] TSOcap[1]
[   52.599534] eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[   52.599744] ahci 0000:00:1f.2: version 3.0
[   52.599768] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 19
[   52.881039] usb 2-1: new full speed USB device using uhci_hcd and address 2
[   52.903247] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 3 Gbps 0x7 impl SATA mode
[   52.903252] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part 
[   52.903259] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   52.903781] scsi0 : ahci
[   52.903911] scsi1 : ahci
[   52.904003] scsi2 : ahci
[   52.904059] ata1: SATA max UDMA/133 abar m2048@0xf8404000 port 0xf8404100 irq 504
[   52.904061] ata2: SATA max UDMA/133 abar m2048@0xf8404000 port 0xf8404180 irq 504
[   52.904064] ata3: SATA max UDMA/133 abar m2048@0xf8404000 port 0xf8404200 irq 504
[   52.917950] usb 2-1: configuration #1 chosen from 1 choice
[   52.987723] usb 2-2: new full speed USB device using uhci_hcd and address 3
[   53.036724] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   53.038257] ata1.00: ATA-7: ST9200420AS, 3.AAA, max UDMA/133
[   53.038259] ata1.00: 390721968 sectors, multi 16: LBA48 NCQ (depth 31/32)
[   53.039047] ata1.00: configured for UDMA/133
[   53.041790] usb 2-2: configuration #1 chosen from 1 choice
[   53.097226] usb 5-2: new low speed USB device using uhci_hcd and address 2
[   53.104794] ata2: SATA link down (SStatus 0 SControl 300)
[   53.130914] usb 5-2: configuration #1 chosen from 1 choice
[   53.140343] usbcore: registered new interface driver hiddev
[   53.149331] input: Logitech USB Trackball as /devices/pci0000:00/0000:00:1d.2/usb5/5-2/5-2:1.0/input/input2
[   53.155280] input,hidraw0: USB HID v1.10 Mouse [Logitech USB Trackball] on usb-0000:00:1d.2-2
[   53.155294] usbcore: registered new interface driver usbhid
[   53.155298] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   53.196958] ata3: SATA link down (SStatus 0 SControl 300)
[   53.197078] scsi 0:0:0:0: Direct-Access     ATA      ST9200420AS      3.AA PQ: 0 ANSI: 5
[   53.197309] ata_piix 0000:00:1f.1: version 2.12
[   53.197323] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 19 (level, low) -> IRQ 19
[   53.197348] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   53.197393] scsi3 : ata_piix
[   53.197498] scsi4 : ata_piix
[   53.197903] ata4: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x18a0 irq 14
[   53.197905] ata5: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x18a8 irq 15
[   53.201153] Driver 'sd' needs updating - please use bus_type methods
[   53.208663] sd 0:0:0:0: [sda] 390721968 512-byte hardware sectors (200050 MB)
[   53.208671] sd 0:0:0:0: [sda] Write Protect is off
[   53.208673] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   53.208683] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   53.208714] sd 0:0:0:0: [sda] 390721968 512-byte hardware sectors (200050 MB)
[   53.208720] sd 0:0:0:0: [sda] Write Protect is off
[   53.208721] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   53.208731] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   53.208734]  sda: sda1 sda2 sda3
[   53.343931] sd 0:0:0:0: [sda] Attached SCSI disk
[   53.346041] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   53.449826] ata4.00: ATAPI: MATSHITADVD-RAM UJ-850S, 1.60, max UDMA/33
[   53.529466] ata4.00: configured for UDMA/33
[   53.588730] Attempting manual resume
[   53.588732] swsusp: Resume From Partition 8:2
[   53.588733] PM: Checking swsusp image.
[   53.588932] PM: Resume from disk failed.
[   53.601735] kjournald starting.  Commit interval 5 seconds
[   53.601740] EXT3-fs: mounted filesystem with ordered data mode.
[   53.669756] scsi 3:0:0:0: CD-ROM            MATSHITA DVD-RAM UJ-850S  1.60 PQ: 0 ANSI: 5
[   53.669844] scsi 3:0:0:0: Attached scsi generic sg1 type 5
[   53.669951] ACPI: PCI Interrupt 0000:0e:06.0[A] -> GSI 22 (level, low) -> IRQ 22
[   53.722988] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[22]  MMIO=[f8100000-f81007ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[   54.227805] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00023f82cd404c8f]
[  360.393183] ip_tables: (C) 2000-2006 Netfilter Core Team
[  360.420269] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[  360.814034] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[  360.831339] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[  360.890512] ACPI: WMI-Acer: Mapper loaded
[  360.917643] input: Power Button (FF) as /devices/virtual/input/input3
[  360.937954] ACPI: Power Button (FF) [PWRF]
[  360.937993] input: Lid Switch as /devices/virtual/input/input4
[  360.938048] ACPI: Lid Switch [LID0]
[  360.938076] input: Power Button (CM) as /devices/virtual/input/input5
[  360.969888] ACPI: Power Button (CM) [PWRB]
[  360.984914] ACPI: AC Adapter [ACAD] (on-line)
[  361.026902] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:02/LNXVIDEO:00/input/input6
[  361.049769] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[  361.060525] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:01/input/input7
[  361.076720] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[  361.149936] ACPI: Battery Slot [BAT1] (battery present)
[  361.433255] nvidia: module license 'NVIDIA' taints kernel.
[  361.746014] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[  361.746029] PCI: Setting latency timer of device 0000:01:00.0 to 64
[  361.746128] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  169.12  Thu Feb 14 17:51:09 PST 2008
[  361.757908] Linux video capture interface: v2.00
[  361.833179] Bluetooth: Core ver 2.11
[  361.865890] NET: Registered protocol family 31
[  361.865892] Bluetooth: HCI device and connection manager initialized
[  361.865895] Bluetooth: HCI socket layer initialized
[  362.001432] ricoh-mmc: Ricoh MMC Controller disabling driver
[  362.001435] ricoh-mmc: Copyright(c) Philip Langdale
[  362.001466] ricoh-mmc: Ricoh MMC controller found at 0000:0e:06.2 [1180:0843] (rev 12)
[  362.001477] ricoh-mmc: Controller is now disabled.
[  362.010422] iTCO_vendor_support: vendor-support=0
[  362.023061] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[  362.023118] iTCO_wdt: Found a ICH8M TCO device (Version=2, TCOBASE=0x1060)
[  362.023152] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[  362.036979] Bluetooth: HCI USB driver ver 2.9
[  362.044617] usbcore: registered new interface driver hci_usb
[  362.047648] sdhci: Secure Digital Host Controller Interface driver
[  362.047649] sdhci: Copyright(c) Pierre Ossman
[  362.047678] sdhci: SDHCI controller found at 0000:0e:06.1 [1180:0822] (rev 22)
[  362.047700] ACPI: PCI Interrupt 0000:0e:06.1[B] -> GSI 23 (level, low) -> IRQ 23
[  362.049142] sdhci:slot0: Will use DMA mode even though HW doesn't fully claim to support it.
[  362.049202] mmc0: SDHCI at 0xf8100800 irq 23 DMA
[  362.118528] uvcvideo: Found UVC 1.00 device USB 2.0 Camera (04f2:b018)
[  362.120189] input: PC Speaker as /devices/platform/pcspkr/input/input8
[  362.120492] usbcore: registered new interface driver uvcvideo
[  362.120495] USB Video Class driver (v0.1.0)
[  362.174445] iwl4965: Intel(R) Wireless WiFi Link 4965AGN driver for Linux, 1.2.0
[  362.174448] iwl4965: Copyright(c) 2003-2007 Intel Corporation
[  362.174595] ACPI: PCI Interrupt 0000:0c:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[  362.174634] PCI: Setting latency timer of device 0000:0c:00.0 to 64
[  362.176044] iwl4965: Detected Intel Wireless WiFi Link 4965AGN
[  362.247519] Driver 'sr' needs updating - please use bus_type methods
[  362.263999] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[  362.264002] Uniform CD-ROM driver Revision: 3.20
[  362.264031] sr 3:0:0:0: Attached scsi CD-ROM sr0
[  362.391875] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 20 (level, low) -> IRQ 20
[  362.393313] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[  363.621993] iwl4965: Tunable channels: 11 802.11bg, 13 802.11a channels
[  363.622918] wmaster0: Selected rate control algorithm 'iwl-4965-rs'
[  363.958888] input: ImPS/2 Logitech Wheel Mouse as /devices/platform/i8042/serio1/input/input9
[  364.432931] lp: driver loaded but no devices found
[  364.524211] Adding 3862296k swap on /dev/sda2.  Priority:-1 extents:1 across:3862296k
[  364.758092] EXT3 FS on sda1, internal journal
[  365.153762] kjournald starting.  Commit interval 5 seconds
[  365.154185] EXT3 FS on sda3, internal journal
[  365.154191] EXT3-fs: mounted filesystem with ordered data mode.
[  365.896371] No dock devices found.
[  379.476858] NET: Registered protocol family 10
[  379.477397] lo: Disabled Privacy Extensions
[  379.478304] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  379.479299] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  393.540132] CPU0 attaching NULL sched-domain.
[  393.540139] CPU1 attaching NULL sched-domain.
[  393.582638] CPU0 attaching sched-domain:
[  393.582647]  domain 0: span 03
[  393.582650]   groups: 01 02
[  393.582655]   domain 1: span 03
[  393.582657]    groups: 03
[  393.582660] CPU1 attaching sched-domain:
[  393.582663]  domain 0: span 03
[  393.582666]   groups: 02 01
[  393.582669]   domain 1: span 03
[  393.582673]    groups: 03
[  394.856476] NET: Registered protocol family 17
[  396.698962] wlan0: Initial auth_alg=1
[  396.698973] wlan0: authenticate with AP 00:0c:41:6e:6a:d4
[  396.703013] wlan0: RX authentication from 00:0c:41:6e:6a:d4 (alg=1 transaction=2 status=0)
[  396.703021] wlan0: replying to auth challenge
[  396.705978] wlan0: RX authentication from 00:0c:41:6e:6a:d4 (alg=1 transaction=4 status=0)
[  396.705986] wlan0: authenticated
[  396.705990] wlan0: associate with AP 00:0c:41:6e:6a:d4
[  396.710955] wlan0: RX AssocResp from 00:0c:41:6e:6a:d4 (capab=0x411 status=0 aid=2)
[  396.710962] wlan0: associated
[  396.710968] wlan0: CTS protection enabled (BSSID=00:0c:41:6e:6a:d4)
[  396.722462] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  402.279282] wlan0: no IPv6 routers present

```

---

### Post by thomasaaron on 2008-07-29
The fix I gave you will cure it.

---

