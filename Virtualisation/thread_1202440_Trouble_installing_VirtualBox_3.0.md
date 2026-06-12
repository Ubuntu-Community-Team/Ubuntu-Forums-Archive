---
title: "Trouble installing VirtualBox 3.0"
date: 2009-07-02
forum: Virtualisation
---

### Post by irv on 2009-07-02
I have been trying to load Virtualbox 3.0 and been having some problems. Maybe someone can help here.
When I install the .deb package I get this message:
> Setting up virtualbox-3.0 (3.0.0-49315_Ubuntu_Jaunty)...
addgroup: The group 'vboxusers' already exists as a system group. Exiting.
Starting VirtualBox Kernel Module
modprobe vboxnetflt failed:
dmesg to find out why
If I run dmesg here is what I get.
```
[    0.648860] pci 0000:00:01.0:   PREFETCH window: 0x000000e0000000-0x000000efffffff
[    0.648865] pci 0000:00:05.0: PCI bridge, secondary bus 0000:0b
[    0.648866] pci 0000:00:05.0:   IO window: disabled
[    0.648870] pci 0000:00:05.0:   MEM window: 0xfe800000-0xfe8fffff
[    0.648873] pci 0000:00:05.0:   PREFETCH window: disabled
[    0.648877] pci 0000:00:07.0: PCI bridge, secondary bus 0000:0c
[    0.648879] pci 0000:00:07.0:   IO window: 0xd000-0xdfff
[    0.648883] pci 0000:00:07.0:   MEM window: 0xfe600000-0xfe7fffff
[    0.648886] pci 0000:00:07.0:   PREFETCH window: 0x000000f0000000-0x000000f01fffff
[    0.648890] pci 0000:00:14.4: PCI bridge, secondary bus 0000:03
[    0.648893] pci 0000:00:14.4:   IO window: disabled
[    0.648901] pci 0000:00:14.4:   MEM window: 0xfe500000-0xfe5fffff
[    0.648906] pci 0000:00:14.4:   PREFETCH window: disabled
[    0.648921] pci 0000:00:05.0: setting latency timer to 64
[    0.648926] pci 0000:00:07.0: setting latency timer to 64
[    0.648934] bus: 00 index 0 io port: [0x00-0xffff]
[    0.648937] bus: 00 index 1 mmio: [0x000000-0xffffffff]
[    0.648939] bus: 01 index 0 io port: [0xe000-0xefff]
[    0.648941] bus: 01 index 1 mmio: [0xfe900000-0xfeafffff]
[    0.648944] bus: 01 index 2 mmio: [0xe0000000-0xefffffff]
[    0.648946] bus: 01 index 3 mmio: [0x0-0x0]
[    0.648948] bus: 0b index 0 mmio: [0x0-0x0]
[    0.648950] bus: 0b index 1 mmio: [0xfe800000-0xfe8fffff]
[    0.648952] bus: 0b index 2 mmio: [0x0-0x0]
[    0.648954] bus: 0b index 3 mmio: [0x0-0x0]
[    0.648956] bus: 0c index 0 io port: [0xd000-0xdfff]
[    0.648959] bus: 0c index 1 mmio: [0xfe600000-0xfe7fffff]
[    0.648962] bus: 0c index 2 mmio: [0xf0000000-0xf01fffff]
[    0.648964] bus: 0c index 3 mmio: [0x0-0x0]
[    0.648966] bus: 03 index 0 mmio: [0x0-0x0]
[    0.648968] bus: 03 index 1 mmio: [0xfe500000-0xfe5fffff]
[    0.648970] bus: 03 index 2 mmio: [0x0-0x0]
[    0.648972] bus: 03 index 3 io port: [0x00-0xffff]
[    0.648974] bus: 03 index 4 mmio: [0x000000-0xffffffff]
[    0.648985] NET: Registered protocol family 2
[    0.664083] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.664374] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.664990] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.665309] TCP: Hash tables configured (established 131072 bind 65536)
[    0.665312] TCP reno registered
[    0.668120] NET: Registered protocol family 1
[    0.668258] checking if image is initramfs... it is
[    1.321482] Freeing initrd memory: 7819k freed
[    1.321517] Simple Boot Flag at 0x79 set to 0x1
[    1.321680] cpufreq: No nForce2 chipset.
[    1.321806] audit: initializing netlink socket (disabled)
[    1.321825] type=2000 audit(1246519340.320:1): initialized
[    1.330257] highmem bounce pool size: 64 pages
[    1.330262] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.331553] VFS: Disk quotas dquot_6.5.1
[    1.331613] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.332263] fuse init (API version 7.10)
[    1.332342] msgmni has been set to 1662
[    1.332560] alg: No test for stdrng (krng)
[    1.332572] io scheduler noop registered
[    1.332574] io scheduler anticipatory registered
[    1.332576] io scheduler deadline registered
[    1.332591] io scheduler cfq registered (default)
[    1.332726] pci 0000:01:05.0: Boot video device
[    1.336385] pcieport-driver 0000:00:05.0: setting latency timer to 64
[    1.336408] pcieport-driver 0000:00:05.0: found MSI capability
[    1.336427] pcieport-driver 0000:00:05.0: irq 2303 for MSI/MSI-X
[    1.336435] pci_express 0000:00:05.0:pcie00: allocate port service
[    1.336448] pci_express 0000:00:05.0:pcie03: allocate port service
[    1.336484] pcieport-driver 0000:00:07.0: setting latency timer to 64
[    1.336505] pcieport-driver 0000:00:07.0: found MSI capability
[    1.336519] pcieport-driver 0000:00:07.0: irq 2302 for MSI/MSI-X
[    1.336527] pci_express 0000:00:07.0:pcie00: allocate port service
[    1.336539] pci_express 0000:00:07.0:pcie02: allocate port service
[    1.336550] pci_express 0000:00:07.0:pcie03: allocate port service
[    1.336601] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.336640] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.336769] ACPI: AC Adapter [AC] (on-line)
[    1.368770] ACPI: Battery Slot [BAT0] (battery present)
[    1.368842] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    1.369335] ACPI: Lid Switch [LID]
[    1.369379] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    1.369387] ACPI: Power Button (CM) [PBTN]
[    1.369428] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    1.369431] ACPI: Sleep Button (CM) [SBTN]
[    1.369693] ACPI: processor limited to max C-state 1
[    1.369745] processor ACPI_CPU:00: registered as cooling_device0
[    1.369751] ACPI: Processor [CPU0] (supports 8 throttling states)
[    1.369838] processor ACPI_CPU:01: registered as cooling_device1
[    1.369842] ACPI: Processor [CPU1] (supports 8 throttling states)
[    1.374731] thermal LNXTHERM:01: registered as thermal_zone0
[    1.378530] ACPI: Thermal Zone [THM] (58 C)
[    1.378584] isapnp: Scanning for PnP cards...
[    1.735085] isapnp: No Plug & Play device found
[    1.745232] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.746197] brd: module loaded
[    1.746506] loop: module loaded
[    1.746578] Fixed MDIO Bus: probed
[    1.746584] PPP generic driver version 2.4.2
[    1.746642] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    1.746669] Driver 'sd' needs updating - please use bus_type methods
[    1.746678] Driver 'sr' needs updating - please use bus_type methods
[    1.746715] ahci 0000:00:12.0: version 3.0
[    1.746736] ahci 0000:00:12.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    1.746767] ahci 0000:00:12.0: controller can't do 64bit DMA, forcing 32bit
[    1.746862] ahci 0000:00:12.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[    1.746866] ahci 0000:00:12.0: flags: ncq sntf ilck pm led clo pmp pio slum part 
[    1.747358] scsi0 : ahci
[    1.747516] scsi1 : ahci
[    1.747624] scsi2 : ahci
[    1.747727] scsi3 : ahci
[    1.747921] ata1: SATA max UDMA/133 abar m1024@0xfec01000 port 0xfec01100 irq 22
[    1.747925] ata2: SATA max UDMA/133 abar m1024@0xfec01000 port 0xfec01180 irq 22
[    1.747929] ata3: SATA max UDMA/133 abar m1024@0xfec01000 port 0xfec01200 irq 22
[    1.747933] ata4: SATA max UDMA/133 abar m1024@0xfec01000 port 0xfec01280 irq 22
[    2.228031] ata1: softreset failed (device not ready)
[    2.228038] ata1: failed due to HW bug, retry pmp=0
[    2.392049] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.420684] ata1.00: ATA-8: WDC WD2500BEVS-75UST0, 01.01A01, max UDMA/133
[    2.420687] ata1.00: 488397168 sectors, multi 8: LBA48 NCQ (depth 31/32)
[    2.420708] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[    2.421559] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[    2.421562] ata1.00: configured for UDMA/133
[    2.756045] ata2: SATA link down (SStatus 0 SControl 300)
[    3.092046] ata3: SATA link down (SStatus 0 SControl 300)
[    3.428045] ata4: SATA link down (SStatus 0 SControl 300)
[    3.444134] scsi 0:0:0:0: Direct-Access     ATA      WDC WD2500BEVS-7 01.0 PQ: 0 ANSI: 5
[    3.444228] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors: (250 GB/232 GiB)
[    3.444245] sd 0:0:0:0: [sda] Write Protect is off
[    3.444248] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.444273] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.444347] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors: (250 GB/232 GiB)
[    3.444361] sd 0:0:0:0: [sda] Write Protect is off
[    3.444364] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.444387] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.444392]  sda: sda1 sda2 sda3 sda4 < sda5 sda6 >
[    3.525617] sd 0:0:0:0: [sda] Attached SCSI disk
[    3.525665] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    3.525954] pata_atiixp 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.526087] scsi4 : pata_atiixp
[    3.526176] scsi5 : pata_atiixp
[    3.527807] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xbfa0 irq 14
[    3.527810] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xbfa8 irq 15
[    3.712499] ata5.00: ATAPI: PBDS DVD+/-RW DS-8W1P, BD1B, max UDMA/33
[    3.752456] ata5.00: configured for UDMA/33
[    3.910259] scsi 4:0:0:0: CD-ROM            PBDS     DVD+-RW DS-8W1P  BD1B PQ: 0 ANSI: 5
[    3.921485] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    3.921488] Uniform CD-ROM driver Revision: 3.20
[    3.921585] sr 4:0:0:0: Attached scsi CD-ROM sr0
[    3.921630] sr 4:0:0:0: Attached scsi generic sg1 type 5
[    3.922105] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    3.922131] ehci_hcd 0000:00:13.5: PCI INT D -> GSI 20 (level, low) -> IRQ 20
[    3.922153] ehci_hcd 0000:00:13.5: EHCI Host Controller
[    3.922210] ehci_hcd 0000:00:13.5: new USB bus registered, assigned bus number 1
[    3.922240] ehci_hcd 0000:00:13.5: applying AMD SB600/SB700 USB freeze workaround
[    3.922260] ehci_hcd 0000:00:13.5: debug port 1
[    3.922277] ehci_hcd 0000:00:13.5: irq 20, io mem 0xffa80000
[    3.932035] ehci_hcd 0000:00:13.5: USB 2.0 started, EHCI 1.00
[    3.932119] usb usb1: configuration #1 chosen from 1 choice
[    3.932147] hub 1-0:1.0: USB hub found
[    3.932155] hub 1-0:1.0: 10 ports detected
[    3.932282] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    3.932300] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.932311] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    3.932355] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 2
[    3.932380] ohci_hcd 0000:00:13.0: irq 16, io mem 0xffb00000
[    3.992061] usb usb2: configuration #1 chosen from 1 choice
[    3.992085] hub 2-0:1.0: USB hub found
[    3.992099] hub 2-0:1.0: 2 ports detected
[    3.992191] ohci_hcd 0000:00:13.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    3.992203] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    3.992247] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 3
[    3.992271] ohci_hcd 0000:00:13.1: irq 17, io mem 0xffb01000
[    4.048055] usb usb3: configuration #1 chosen from 1 choice
[    4.048079] hub 3-0:1.0: USB hub found
[    4.048091] hub 3-0:1.0: 2 ports detected
[    4.048179] ohci_hcd 0000:00:13.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    4.048191] ohci_hcd 0000:00:13.2: OHCI Host Controller
[    4.048236] ohci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 4
[    4.048259] ohci_hcd 0000:00:13.2: irq 18, io mem 0xffb02000
[    4.104054] usb usb4: configuration #1 chosen from 1 choice
[    4.104080] hub 4-0:1.0: USB hub found
[    4.104092] hub 4-0:1.0: 2 ports detected
[    4.104177] ohci_hcd 0000:00:13.3: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    4.104187] ohci_hcd 0000:00:13.3: OHCI Host Controller
[    4.104227] ohci_hcd 0000:00:13.3: new USB bus registered, assigned bus number 5
[    4.104244] ohci_hcd 0000:00:13.3: irq 17, io mem 0xffb03000
[    4.160057] usb usb5: configuration #1 chosen from 1 choice
[    4.160080] hub 5-0:1.0: USB hub found
[    4.160093] hub 5-0:1.0: 2 ports detected
[    4.160176] ohci_hcd 0000:00:13.4: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    4.160187] ohci_hcd 0000:00:13.4: OHCI Host Controller
[    4.160230] ohci_hcd 0000:00:13.4: new USB bus registered, assigned bus number 6
[    4.160247] ohci_hcd 0000:00:13.4: irq 18, io mem 0xffb04000
[    4.216055] usb usb6: configuration #1 chosen from 1 choice
[    4.216078] hub 6-0:1.0: USB hub found
[    4.216091] hub 6-0:1.0: 2 ports detected
[    4.216183] uhci_hcd: USB Universal Host Controller Interface driver
[    4.216261] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    4.219631] serio: i8042 KBD port at 0x60,0x64 irq 1
[    4.219636] serio: i8042 AUX port at 0x60,0x64 irq 12
[    4.221059] mice: PS/2 mouse device common for all mice
[    4.237080] rtc_cmos 00:03: RTC can wake from S4
[    4.237117] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    4.237150] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    4.237210] device-mapper: uevent: version 1.0.3
[    4.237338] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
[    4.237507] device-mapper: multipath: version 1.0.5 loaded
[    4.237510] device-mapper: multipath round-robin: version 1.0.0 loaded
[    4.237630] EISA: Probing bus 0 at eisa.0
[    4.237642] Cannot allocate resource for EISA slot 1
[    4.237674] EISA: Detected 0 cards.
[    4.237806] cpuidle: using governor ladder
[    4.237808] cpuidle: using governor menu
[    4.238318] TCP cubic registered
[    4.238422] NET: Registered protocol family 10
[    4.238837] lo: Disabled Privacy Extensions
[    4.239158] NET: Registered protocol family 17
[    4.239175] Bluetooth: L2CAP ver 2.11
[    4.239177] Bluetooth: L2CAP socket layer initialized
[    4.239179] Bluetooth: SCO (Voice Link) ver 0.6
[    4.239181] Bluetooth: SCO socket layer initialized
[    4.239243] Bluetooth: RFCOMM socket layer initialized
[    4.239249] Bluetooth: RFCOMM TTY layer initialized
[    4.239251] Bluetooth: RFCOMM ver 1.10
[    4.239304] powernow-k8: Found 1 AMD Turion(tm) 64 X2 Mobile Technology TL-58 processors (2 cpu cores) (version 2.20.00)
[    4.239358] powernow-k8:    0 : fid 0xb (1900 MHz), vid 0x12
[    4.239361] powernow-k8:    1 : fid 0xa (1800 MHz), vid 0x13
[    4.239364] powernow-k8:    2 : fid 0x8 (1600 MHz), vid 0x14
[    4.239366] powernow-k8:    3 : fid 0x0 (800 MHz), vid 0x1e
[    4.239422] Using IPI No-Shortcut mode
[    4.239526] registered taskstats version 1
[    4.239692]   Magic number: 1:717:368
[    4.239805] rtc_cmos 00:03: setting system clock to 2009-07-02 07:22:23 UTC (1246519343)
[    4.239808] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    4.239810] EDD information not available.
[    4.240189] Freeing unused kernel memory: 532k freed
[    4.240369] Write protecting the kernel text: 4112k
[    4.240443] Write protecting the kernel read-only data: 1524k
[    4.240570] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    4.245046] usb 1-2: new high speed USB device using ehci_hcd and address 2
[    4.326990] vesafb: framebuffer at 0xe0000000, mapped to 0xf7d00000, using 1875k, total 16384k
[    4.326995] vesafb: mode is 800x600x16, linelength=1600, pages=16
[    4.326998] vesafb: protected mode interface info at c000:a026
[    4.327001] vesafb: pmi: set display start = c00ca0b0, set palette = c00ca16e
[    4.327003] vesafb: scrolling: redraw
[    4.327006] vesafb: Truecolor: size=0:5:6:5, shift=0:11:5:0
[    4.327087] Console: switching to colour frame buffer device 100x37
[    4.356400] fb0: VESA VGA frame buffer device
[    4.377440] usb 1-2: configuration #1 chosen from 1 choice
[    4.377512] hub 1-2:1.0: USB hub found
[    4.377612] hub 1-2:1.0: 4 ports detected
[    4.567839] b43-pci-bridge 0000:0b:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    4.567852] b43-pci-bridge 0000:0b:00.0: setting latency timer to 64
[    4.620051] usb 1-6: new high speed USB device using ehci_hcd and address 5
[    4.625098] ssb: Sonics Silicon Backplane found on PCI device 0000:0b:00.0
[    4.645430] ohci1394 0000:03:01.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    4.697231] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[23]  MMIO=[fe5fd800-fe5fdfff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    4.727037] b44 0000:03:00.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    4.783153] usb 1-6: configuration #1 chosen from 1 choice
[    4.789093] ssb: Sonics Silicon Backplane found on PCI device 0000:03:00.0
[    4.789118] b44.c:v2.0
[    4.809803] eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:1d:09:a6:0e:20
[    5.045026] usb 3-1: new low speed USB device using ohci_hcd and address 2
[    5.218943] PM: Starting manual resume from disk
[    5.218947] PM: Resume from partition 8:5
[    5.218949] PM: Checking hibernation image.
[    5.219149] PM: Resume from disk failed.
[    5.240156] usb 3-1: configuration #1 chosen from 1 choice
[    5.241359] EXT4-fs: barriers enabled
[    5.247792] usbcore: registered new interface driver hiddev
[    5.253383] input: HID 1267:0103 as /devices/pci0000:00/0000:00:13.1/usb3/3-1/3-1:1.0/input/input5
[    5.257087] generic-usb 0003:1267:0103.0001: input,hidraw0: USB HID v1.10 Keyboard [HID 1267:0103] on usb-0000:00:13.1-1/input0
[    5.264891] kjournald2 starting.  Commit interval 5 seconds
[    5.264908] EXT4-fs: delayed allocation enabled
[    5.264910] EXT4-fs: file extents enabled
[    5.273267] EXT4-fs: mballoc enabled
[    5.273272] EXT4-fs: mounted filesystem with ordered data mode.
[    5.273453] input: HID 1267:0103 as /devices/pci0000:00/0000:00:13.1/usb3/3-1/3-1:1.1/input/input6
[    5.281392] generic-usb 0003:1267:0103.0002: input,hidraw1: USB HID v1.10 Device [HID 1267:0103] on usb-0000:00:13.1-1/input1
[    5.281417] usbcore: registered new interface driver usbhid
[    5.281421] usbhid: v2.6:USB HID core driver
[    5.505045] usb 3-2: new low speed USB device using ohci_hcd and address 3
[    5.673145] usb 3-2: configuration #1 chosen from 1 choice
[    5.680340] input: KYE USB MOUSE as /devices/pci0000:00/0000:00:13.1/usb3/3-2/3-2:1.0/input/input7
[    5.680453] generic-usb 0003:0458:0007.0003: input,hidraw2: USB HID v1.10 Mouse [KYE USB MOUSE] on usb-0000:00:13.1-2/input0
[    5.977280] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[484fc000263719a1]
[    9.637692] udev: starting version 141
[   10.145158] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   10.221095] input: PC Speaker as /devices/platform/pcspkr/input/input8
[   10.242039] ricoh-mmc: Ricoh MMC Controller disabling driver
[   10.242043] ricoh-mmc: Copyright(c) Philip Langdale
[   10.242076] ricoh-mmc: Ricoh MMC controller found at 0000:03:01.2 [1180:0843] (rev 12)
[   10.242094] ricoh-mmc: Controller is now disabled.
[   10.245765] sdhci: Secure Digital Host Controller Interface driver
[   10.245768] sdhci: Copyright(c) Pierre Ossman
[   10.247489] sdhci-pci 0000:03:01.1: SDHCI controller found [1180:0822] (rev 22)
[   10.247507] sdhci-pci 0000:03:01.1: PCI INT B -> GSI 20 (level, low) -> IRQ 20
[   10.250708] mmc0: SDHCI controller on PCI [0000:03:01.1] using DMA
[   10.261698] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   10.275739] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0x10c0, revision 0
[   10.298096] Linux agpgart interface v0.103
[   10.369984] acpi device:31: registered as cooling_device2
[   10.370669] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:2d/device:2e/input/input9
[   10.378200] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[   10.467252] Linux video capture interface: v2.00
[   10.564072] cfg80211: Calling CRDA to update world regulatory domain
[   10.579359] uvcvideo: Found UVC 1.00 device Laptop Integrated Webcam (05a9:2640)
[   10.582032] uvcvideo: Failed to query (135) UVC control 1 (unit 0) : -32 (exp. 26).
[   10.582695] input: Laptop Integrated Webcam as /devices/pci0000:00/0000:00:13.5/usb1/1-6/1-6:1.0/input/input10
[   10.586300] usbcore: registered new interface driver uvcvideo
[   10.586304] USB Video Class driver (v0.1.0)
[   10.596190] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[   10.653722] cfg80211: World regulatory domain updated:
[   10.653726] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   10.653730] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.653733] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   10.653735] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   10.653738] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.653740] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.838793] b43-phy0: Broadcom 4311 WLAN found
[   10.904977] phy0: Selected rate control algorithm 'pid'
[   10.956822] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   11.059449] Broadcom 43xx driver loaded [ Features: PLR, Firmware-ID: FW13 ]
[   11.469573] Synaptics Touchpad, model: 1, fw: 6.3, id: 0x1a0b1, caps: 0xa04793/0x300000
[   11.469580] serio: Synaptics pass-through port at isa0060/serio1/input0
[   11.506088] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input11
[   11.739623] lp: driver loaded but no devices found
[   11.866068] Adding 176672k swap on /dev/sda5.  Priority:-1 extents:1 across:176672k
[   12.413611] EXT4 FS on sda3, internal journal on sda3:8
[   13.543904] type=1505 audit(1246537352.801:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2227
[   13.601601] type=1505 audit(1246537352.860:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2231
[   13.601745] type=1505 audit(1246537352.860:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2231
[   13.601799] type=1505 audit(1246537352.860:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2231
[   13.601849] type=1505 audit(1246537352.860:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2231
[   13.761565] type=1505 audit(1246537353.020:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2236
[   13.761770] type=1505 audit(1246537353.020:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2236
[   13.860732] type=1505 audit(1246537353.117:9): operation="profile_load" name="/usr/sbin/mysqld" name2="default" pid=2240
[   13.895028] type=1505 audit(1246537353.153:10): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2244
[   20.562521] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   20.562525] vboxdrv: Successfully done.
[   20.562528] vboxdrv: Found 2 processor cores.
[   20.563591] vboxdrv: fAsync=1 offMin=0x2b5c79 offMax=0x2b5c79
[   20.563660] vboxdrv: TSC mode is 'asynchronous', kernel timer mode is 'normal'.
[   20.563663] vboxdrv: Successfully loaded version 2.1.4_OSE (interface 0x000a0009).
[   22.821225] input: b43-phy0 as /devices/virtual/input/input12
[   22.872055] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[   22.965364] b43 ssb0:0: firmware: requesting b43/pcm5.fw
[   22.983856] b43 ssb0:0: firmware: requesting b43/b0g0initvals5.fw
[   22.990054] b43 ssb0:0: firmware: requesting b43/b0g0bsinitvals5.fw
[   23.112043] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[   23.192624] Registered led device: b43-phy0::tx
[   23.192647] Registered led device: b43-phy0::rx
[   23.192674] Registered led device: b43-phy0::radio
[   23.208044] b43-phy0: Radio turned on by software
[   23.208568] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   23.416034] CE: hpet increasing min_delta_ns to 15000 nsec
[   23.416034] CE: hpet increasing min_delta_ns to 22500 nsec
[   23.630089] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   23.630093] Bluetooth: BNEP filters: protocol multicast
[   23.654546] Bridge firewalling registered
[   24.685705] ppdev: user-space parallel port driver
[   24.754143] pci 0000:01:05.0: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[   24.836751] [drm] Initialized drm 1.1.0 20060810
[   24.892922] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   24.933443] [drm] Initialized radeon 1.29.0 20080528 on minor 0
[   25.557675] [drm] Setting GART location based on new memory map
[   25.558324] [drm] Loading RS690/RS740 Microcode
[   25.558396] [drm] Num pipes: 1
[   25.558403] [drm] writeback test succeeded in 1 usecs
[   27.044449] input: b43-phy0 as /devices/virtual/input/input13
[   27.208047] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[   27.281665] Registered led device: b43-phy0::tx
[   27.281699] Registered led device: b43-phy0::rx
[   27.281729] Registered led device: b43-phy0::radio
[   27.297663] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   27.408243] ata1.00: exception Emask 0x50 SAct 0x3 SErr 0x680900 action 0x6 frozen
[   27.408249] ata1.00: irq_stat 0x08000000, interface fatal error
[   27.408253] ata1: SError: { UnrecovData HostInt 10B8B BadCRC Handshk }
[   27.408260] ata1.00: cmd 60/20:00:28:0d:fc/00:00:13:00:00/40 tag 0 ncq 16384 in
[   27.408261]          res 40/00:0c:20:b2:cd/00:00:13:00:00/40 Emask 0x50 (ATA bus error)
[   27.408264] ata1.00: status: { DRDY }
[   27.408269] ata1.00: cmd 60/e0:08:20:b2:cd/00:00:13:00:00/40 tag 1 ncq 114688 in
[   27.408270]          res 40/00:0c:20:b2:cd/00:00:13:00:00/40 Emask 0x50 (ATA bus error)
[   27.408273] ata1.00: status: { DRDY }
[   27.408279] ata1: hard resetting link
[   27.892034] ata1: softreset failed (device not ready)
[   27.892038] ata1: failed due to HW bug, retry pmp=0
[   28.056045] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   28.090364] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[   28.091213] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[   28.091217] ata1.00: configured for UDMA/133
[   28.091227] ata1: EH complete
[   28.091273] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors: (250 GB/232 GiB)
[   28.091292] sd 0:0:0:0: [sda] Write Protect is off
[   28.091294] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   28.091318] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   28.209243] wlan0: authenticate with AP 00:18:39:dc:1b:9b
[   28.221956] wlan0: authenticate with AP 00:18:39:dc:1b:9b
[   28.228746] wlan0: authenticated
[   28.228749] wlan0: associate with AP 00:18:39:dc:1b:9b
[   28.231818] wlan0: RX AssocResp from 00:18:39:dc:1b:9b (capab=0x401 status=0 aid=1)
[   28.231821] wlan0: associated
[   28.232086] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   39.005015] wlan0: no IPv6 routers present
[   87.000042] Clocksource tsc unstable (delta = -287968698 ns)
[  153.186654] warning: `VirtualBox' uses 32-bit capabilities (legacy support in use)
[  157.278119] ata1.00: exception Emask 0x50 SAct 0x1 SErr 0x680900 action 0x6 frozen
[  157.278131] ata1.00: irq_stat 0x08000000, interface fatal error
[  157.278142] ata1: SError: { UnrecovData HostInt 10B8B BadCRC Handshk }
[  157.278157] ata1.00: cmd 60/38:00:10:27:f1/00:00:14:00:00/40 tag 0 ncq 28672 in
[  157.278161]          res 40/00:04:10:27:f1/00:00:14:00:00/40 Emask 0x50 (ATA bus error)
[  157.278168] ata1.00: status: { DRDY }
[  157.278181] ata1: hard resetting link
[  157.760155] ata1: softreset failed (device not ready)
[  157.760168] ata1: failed due to HW bug, retry pmp=0
[  157.925074] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[  157.951942] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  157.952838] ata1.00: SB600 AHCI: limiting to 255 sectors per cmd
[  157.952846] ata1.00: configured for UDMA/133
[  157.952869] ata1: EH complete
[  157.952977] sd 0:0:0:0: [sda] 488397168 512-byte hardware sectors: (250 GB/232 GiB)
[  157.954470] sd 0:0:0:0: [sda] Write Protect is off
[  157.954477] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  157.954543] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 1000.778376] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[ 1000.778385] vboxdrv: Successfully done.
[ 1000.778391] vboxdrv: Found 2 processor cores.
[ 1000.778566] vboxdrv: fAsync=1 offMin=0x17bdb5 offMax=0x17bdb5
[ 1000.778699] vboxdrv: TSC mode is 'asynchronous', kernel timer mode is 'normal'.
[ 1000.778704] vboxdrv: Successfully loaded version 3.0.0 (interface 0x000e0000).
[ 1001.003945] vboxnetflt: disagrees about version of symbol SUPDrvLinuxIDC
[ 1001.003958] vboxnetflt: Unknown symbol SUPDrvLinuxIDC
irv@irv-new-laptop:~$ 

```
I am not sure what this is telling me.
I had to un-install VirtualBox 2.1.4-OSE before I could install 3.0 or I would get a conflict error, so I did this.
It says that 3.0 is installed, but it dose not show up on the menu anywhere, and I am not sure how to run it from a terminal.
Can anyone help?
Thanks

---

### Post by irv on 2009-07-02
I did a kernel update today and had to reboot. After this VirtualBox is working and it shows up on the System Tools menu.
The only other problem I have is my window is transparent and it is hard to see anything in it because of my background on my desktop. Is there a way to turn the transparency off?
Thanks

---

