---
title: "mdadm does not assemble raid10 on bootup"
date: 2009-03-03
forum: Server Platforms
---

### Post by tiennes on 2009-03-03
Hi all I dont know what I am doing wrong

System setup 1 Disk non raid as system disk
and 4 disk as raid 10 (2 partiions md1 md2) supposed to be /home one day.

I am running ubuntu amd64 9.04 alpha but I think this shouldnt be the issue

any input appreciated Thanks tiennes



uname -a 

```
Linux sindar 2.6.28-8-generic #26-Ubuntu SMP Wed Feb 25 04:27:53 UTC 2009 x86_64 GNU/Linux

```

After Booting cat /proc/mdstat 
```


Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md2 : inactive sdc2[1](S) sde2[3](S) sdd2[2](S) sdb2[0](S)
      78139392 blocks
       
md1 : inactive sdc1[1](S) sde1[3](S) sdd1[2](S) sdb1[0](S)
      1171876864 blocks


```


with sudo mdadm -As
```


mdadm: /dev/md1 has been started with 4 drives.
mdadm: /dev/md2 has been started with 4 drives.

[sudo] password for Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md2 : active raid10 sdb2[0] sde2[3] sdd2[2] sdc2[1]
      19534848 blocks 256K chunks 4 far-copies [4/4] [UUUU]
      
md1 : active raid10 sdb1[0] sde1[3] sdd1[2] sdc1[1]
      292968448 blocks 256K chunks 4 far-copies [4/4] [UUUU]



```

It seems to be to be that the assemble does not get startet on boot

dmesg | grep md
```
[    4.885503] md: linear personality registered for level -1
[    4.887902] md: multipath personality registered for level -4
[    4.890118] md: raid0 personality registered for level 0
[    4.893220] md: raid1 personality registered for level 1
[    5.392173] md: raid6 personality registered for level 6
[    5.392259] md: raid5 personality registered for level 5
[    5.392345] md: raid4 personality registered for level 4
[    5.404305] md: raid10 personality registered for level 10
[    5.609947] md: bind<sdb1>
[    5.610325] mdadm[1164]: segfault at 0 ip 000000000040839b sp 00007fff5ad72850 error 4 in mdadm[400000+2a000]
[    5.612209] md: bind<sdb2>
[    5.612563] mdadm[1178]: segfault at 0 ip 000000000040839b sp 00007fff25f18a00 error 4 in mdadm[400000+2a000]
[    5.637860] md: bind<sdd1>
[    5.638354] mdadm[1185]: segfault at 0 ip 000000000040839b sp 00007fffc3170c50 error 4 in mdadm[400000+2a000]
[    5.639329] md: bind<sdd2>
[    5.639668] mdadm[1234]: segfault at 0 ip 000000000040839b sp 00007fff24abf5a0 error 4 in mdadm[400000+2a000]
[    5.641893] md: bind<sde1>
[    5.642705] mdadm[1220]: segfault at 0 ip 000000000040839b sp 00007fff49098b80 error 4 in mdadm[400000+2a000]
[    5.643119] md: bind<sde2>
[    5.643831] mdadm[1243]: segfault at 0 ip 000000000040839b sp 00007fff8c4ccfb0 error 4 in mdadm[400000+2a000]
[    5.665339] md: bind<sdc1>
[    5.665664] md: bind<sdc2>
[    5.666406] mdadm[1312]: segfault at 0 ip 000000000040839b sp 00007ffffb1c2ca0 error 4 in mdadm[400000+2a000]
[    5.667382] mdadm[1183]: segfault at 0 ip 000000000040839b sp 00007fff2215dc40 error 4 in mdadm[400000+2a000]

```

here some additional files

full dmesg```

[    0.552122] usbcore: registered new device driver usb
[    0.552122] PCI: Using ACPI for IRQ routing
[    0.568011] Bluetooth: Core ver 2.13
[    0.568104] NET: Registered protocol family 31
[    0.568119] Bluetooth: HCI device and connection manager initialized
[    0.568211] Bluetooth: HCI socket layer initialized
[    0.568295] NET: Registered protocol family 8
[    0.568377] NET: Registered protocol family 20
[    0.568471] NetLabel: Initializing
[    0.568471] NetLabel:  domain hash size = 128
[    0.568471] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.568471] NetLabel:  unlabeled traffic allowed by default
[    0.568471] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.568471] hpet0: 4 comparators, 64-bit 14.318180 MHz counter
[    0.572072] AppArmor: AppArmor Filesystem Enabled
[    0.576009] Switched to high resolution mode on CPU 0
[    0.577434] Switched to high resolution mode on CPU 1
[    0.588032] pnp: PnP ACPI init
[    0.588118] ACPI: bus type pnp registered
[    0.592247] pnp: PnP ACPI: found 17 devices
[    0.592330] ACPI: ACPI bus type pnp unregistered
[    0.592420] system 00:01: iomem range 0xfed14000-0xfed19fff has been reserved
[    0.592520] system 00:07: ioport range 0x290-0x29f has been reserved
[    0.592614] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
[    0.592705] system 00:08: ioport range 0x800-0x87f has been reserved
[    0.592796] system 00:08: ioport range 0x500-0x57f has been reserved
[    0.592888] system 00:08: iomem range 0xfed08000-0xfed08fff has been reserved
[    0.592982] system 00:08: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    0.593076] system 00:08: iomem range 0xfed20000-0xfed3ffff has been reserved
[    0.593171] system 00:08: iomem range 0xfed50000-0xfed8ffff has been reserved
[    0.593268] system 00:0b: iomem range 0xffc00000-0xffefffff has been reserved
[    0.593365] system 00:0d: iomem range 0xfec00000-0xfec00fff has been reserved
[    0.593460] system 00:0d: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.593557] system 00:0f: iomem range 0xe0000000-0xefffffff has been reserved
[    0.593655] system 00:10: iomem range 0x0-0x9ffff could not be reserved
[    0.593747] system 00:10: iomem range 0xc0000-0xcffff has been reserved
[    0.593839] system 00:10: iomem range 0xe0000-0xfffff could not be reserved
[    0.593933] system 00:10: iomem range 0x100000-0x7fffffff could not be reserved
[    0.599061] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.599151] pci 0000:00:01.0:   IO window: 0xc000-0xcfff
[    0.599239] pci 0000:00:01.0:   MEM window: 0xfa000000-0xfe8fffff
[    0.599330] pci 0000:00:01.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
[    0.599459] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:04
[    0.599548] pci 0000:00:1c.0:   IO window: disabled
[    0.599634] pci 0000:00:1c.0:   MEM window: disabled
[    0.599721] pci 0000:00:1c.0:   PREFETCH window: 0x000000f8f00000-0x000000f8ffffff
[    0.599851] pci 0000:00:1c.4: PCI bridge, secondary bus 0000:03
[    0.599941] pci 0000:00:1c.4:   IO window: 0xe000-0xefff
[    0.600050] pci 0000:00:1c.4:   MEM window: 0xfea00000-0xfeafffff
[    0.600142] pci 0000:00:1c.4:   PREFETCH window: disabled
[    0.600232] pci 0000:00:1c.5: PCI bridge, secondary bus 0000:02
[    0.600321] pci 0000:00:1c.5:   IO window: 0xd000-0xdfff
[    0.600410] pci 0000:00:1c.5:   MEM window: 0xfe900000-0xfe9fffff
[    0.600501] pci 0000:00:1c.5:   PREFETCH window: disabled
[    0.600591] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:05
[    0.600680] pci 0000:00:1e.0:   IO window: disabled
[    0.600767] pci 0000:00:1e.0:   MEM window: 0xfeb00000-0xfebfffff
[    0.600858] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.600954] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.601048] pci 0000:00:01.0: setting latency timer to 64
[    0.601055] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.601149] pci 0000:00:1c.0: setting latency timer to 64
[    0.601154] pci 0000:00:1c.4: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.601248] pci 0000:00:1c.4: setting latency timer to 64
[    0.601254] pci 0000:00:1c.5: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.601348] pci 0000:00:1c.5: setting latency timer to 64
[    0.601354] pci 0000:00:1e.0: setting latency timer to 64
[    0.601357] bus: 00 index 0 io port: [0x00-0xffff]
[    0.601441] bus: 00 index 1 mmio: [0x000000-0xffffffffffffffff]
[    0.601530] bus: 01 index 0 io port: [0xc000-0xcfff]
[    0.601614] bus: 01 index 1 mmio: [0xfa000000-0xfe8fffff]
[    0.601701] bus: 01 index 2 mmio: [0xd0000000-0xdfffffff]
[    0.601788] bus: 01 index 3 mmio: [0x0-0x0]
[    0.601869] bus: 04 index 0 mmio: [0x0-0x0]
[    0.601950] bus: 04 index 1 mmio: [0x0-0x0]
[    0.602031] bus: 04 index 2 mmio: [0xf8f00000-0xf8ffffff]
[    0.602117] bus: 04 index 3 mmio: [0x0-0x0]
[    0.602199] bus: 03 index 0 io port: [0xe000-0xefff]
[    0.602284] bus: 03 index 1 mmio: [0xfea00000-0xfeafffff]
[    0.602370] bus: 03 index 2 mmio: [0x0-0x0]
[    0.602451] bus: 03 index 3 mmio: [0x0-0x0]
[    0.602533] bus: 02 index 0 io port: [0xd000-0xdfff]
[    0.602617] bus: 02 index 1 mmio: [0xfe900000-0xfe9fffff]
[    0.602704] bus: 02 index 2 mmio: [0x0-0x0]
[    0.602785] bus: 02 index 3 mmio: [0x0-0x0]
[    0.602866] bus: 05 index 0 mmio: [0x0-0x0]
[    0.602948] bus: 05 index 1 mmio: [0xfeb00000-0xfebfffff]
[    0.603034] bus: 05 index 2 mmio: [0x0-0x0]
[    0.603116] bus: 05 index 3 io port: [0x00-0xffff]
[    0.603200] bus: 05 index 4 mmio: [0x000000-0xffffffffffffffff]
[    0.603295] NET: Registered protocol family 2
[    0.640079] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
[    0.640500] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[    0.642112] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.642685] TCP: Hash tables configured (established 262144 bind 65536)
[    0.642777] TCP reno registered
[    0.652139] NET: Registered protocol family 1
[    0.652347] checking if image is initramfs... it is
[    1.332081] Freeing initrd memory: 8106k freed
[    1.335998] audit: initializing netlink socket (disabled)
[    1.336114] type=2000 audit(1236068358.336:1): initialized
[    1.343923] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.346183] VFS: Disk quotas dquot_6.5.1
[    1.346336] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.347269] msgmni has been set to 3972
[    1.347515] alg: No test for stdrng (krng)
[    1.347605] io scheduler noop registered
[    1.347686] io scheduler anticipatory registered
[    1.347769] io scheduler deadline registered
[    1.347907] io scheduler cfq registered (default)
[    1.348151] pci 0000:01:00.0: Boot video device
[    1.350669] pcieport-driver 0000:00:01.0: setting latency timer to 64
[    1.350696] pcieport-driver 0000:00:01.0: found MSI capability
[    1.350802] pcieport-driver 0000:00:01.0: irq 2303 for MSI/MSI-X
[    1.350810] pci_express 0000:00:01.0:pcie00: allocate port service
[    1.350846] pci_express 0000:00:01.0:pcie03: allocate port service
[    1.350908] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    1.350937] pcieport-driver 0000:00:1c.0: found MSI capability
[    1.351045] pcieport-driver 0000:00:1c.0: irq 2302 for MSI/MSI-X
[    1.351055] pci_express 0000:00:1c.0:pcie00: allocate port service
[    1.351087] pci_express 0000:00:1c.0:pcie02: allocate port service
[    1.351120] pci_express 0000:00:1c.0:pcie03: allocate port service
[    1.351190] pcieport-driver 0000:00:1c.4: setting latency timer to 64
[    1.351219] pcieport-driver 0000:00:1c.4: found MSI capability
[    1.351326] pcieport-driver 0000:00:1c.4: irq 2301 for MSI/MSI-X
[    1.351336] pci_express 0000:00:1c.4:pcie00: allocate port service
[    1.351371] pci_express 0000:00:1c.4:pcie02: allocate port service
[    1.351403] pci_express 0000:00:1c.4:pcie03: allocate port service
[    1.351474] pcieport-driver 0000:00:1c.5: setting latency timer to 64
[    1.351503] pcieport-driver 0000:00:1c.5: found MSI capability
[    1.351610] pcieport-driver 0000:00:1c.5: irq 2300 for MSI/MSI-X
[    1.351620] pci_express 0000:00:1c.5:pcie00: allocate port service
[    1.351654] pci_express 0000:00:1c.5:pcie02: allocate port service
[    1.351687] pci_express 0000:00:1c.5:pcie03: allocate port service
[    1.351810] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.352359] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.352686] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.352816] ACPI: Power Button (FF) [PWRF]
[    1.352966] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    1.353099] ACPI: Power Button (CM) [PWRB]
[    1.353550] processor ACPI_CPU:00: registered as cooling_device0
[    1.353695] processor ACPI_CPU:01: registered as cooling_device1
[    1.388856] Linux agpgart interface v0.103
[    1.388941] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.389136] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.389681] 00:0c: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.391205] brd: module loaded
[    1.391913] loop: module loaded
[    1.392160] Fixed MDIO Bus: probed
[    1.392242] PPP generic driver version 2.4.2
[    1.392437] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    1.392615] Driver 'sd' needs updating - please use bus_type methods
[    1.392735] Driver 'sr' needs updating - please use bus_type methods
[    1.392907] ahci 0000:00:1f.2: version 3.0
[    1.392921] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.393041] ahci 0000:00:1f.2: irq 2299 for MSI/MSI-X
[    1.393109] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 6 ports 3 Gbps 0x3f impl SATA mode
[    1.393241] ahci 0000:00:1f.2: flags: 64bit ncq sntf stag pm led clo pmp pio slum part ems 
[    1.393373] ahci 0000:00:1f.2: setting latency timer to 64
[    1.393713] scsi0 : ahci
[    1.393913] scsi1 : ahci
[    1.394080] scsi2 : ahci
[    1.394248] scsi3 : ahci
[    1.394415] scsi4 : ahci
[    1.394582] scsi5 : ahci
[    1.394811] ata1: SATA max UDMA/133 abar m2048@0xf9ffe800 port 0xf9ffe900 irq 2299
[    1.394939] ata2: SATA max UDMA/133 abar m2048@0xf9ffe800 port 0xf9ffe980 irq 2299
[    1.395068] ata3: SATA max UDMA/133 abar m2048@0xf9ffe800 port 0xf9ffea00 irq 2299
[    1.395196] ata4: SATA max UDMA/133 abar m2048@0xf9ffe800 port 0xf9ffea80 irq 2299
[    1.395323] ata5: SATA max UDMA/133 abar m2048@0xf9ffe800 port 0xf9ffeb00 irq 2299
[    1.395451] ata6: SATA max UDMA/133 abar m2048@0xf9ffe800 port 0xf9ffeb80 irq 2299
[    1.876041] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.878162] ata1.00: ATA-8: WDC WD740HLFS-01G6U0, 04.04V01, max UDMA/133
[    1.878266] ata1.00: 145226112 sectors, multi 0: LBA48 NCQ (depth 31/32)
[    1.881176] ata1.00: configured for UDMA/133
[    2.380046] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.386443] ata2.00: ATA-7: SAMSUNG HD322HJ, 1AC01113, max UDMA7
[    2.386535] ata2.00: 625142448 sectors, multi 0: LBA48 NCQ (depth 31/32)
[    2.393024] ata2.00: configured for UDMA/133
[    2.892040] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.898441] ata3.00: ATA-7: SAMSUNG HD322HJ, 1AC01113, max UDMA7
[    2.898533] ata3.00: 625142448 sectors, multi 0: LBA48 NCQ (depth 31/32)
[    2.905025] ata3.00: configured for UDMA/133
[    3.404044] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    3.410445] ata4.00: ATA-7: SAMSUNG HD322HJ, 1AC01113, max UDMA7
[    3.410537] ata4.00: 625142448 sectors, multi 0: LBA48 NCQ (depth 31/32)
[    3.417031] ata4.00: configured for UDMA/133
[    3.916040] ata5: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    3.922438] ata5.00: ATA-7: SAMSUNG HD322HJ, 1AC01113, max UDMA7
[    3.922530] ata5.00: 625142448 sectors, multi 0: LBA48 NCQ (depth 31/32)
[    3.930423] ata5.00: configured for UDMA/133
[    4.264034] ata6: SATA link down (SStatus 0 SControl 300)
[    4.280137] scsi 0:0:0:0: Direct-Access     ATA      WDC WD740HLFS-01 04.0 PQ: 0 ANSI: 5
[    4.280430] sd 0:0:0:0: [sda] 145226112 512-byte hardware sectors: (74.3 GB/69.2 GiB)
[    4.280577] sd 0:0:0:0: [sda] Write Protect is off
[    4.280662] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.280685] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.280881] sd 0:0:0:0: [sda] 145226112 512-byte hardware sectors: (74.3 GB/69.2 GiB)
[    4.281021] sd 0:0:0:0: [sda] Write Protect is off
[    4.281105] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.281128] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.281263]  sda: sda1 sda2 sda3
[    4.292874] sd 0:0:0:0: [sda] Attached SCSI disk
[    4.293043] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    4.293188] scsi 1:0:0:0: Direct-Access     ATA      SAMSUNG HD322HJ  1AC0 PQ: 0 ANSI: 5
[    4.293462] sd 1:0:0:0: [sdb] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
[    4.293602] sd 1:0:0:0: [sdb] Write Protect is off
[    4.293686] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    4.293709] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.293886] sd 1:0:0:0: [sdb] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
[    4.294025] sd 1:0:0:0: [sdb] Write Protect is off
[    4.294110] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    4.294132] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.294267]  sdb: sdb1 sdb2
[    4.304304] sd 1:0:0:0: [sdb] Attached SCSI disk
[    4.304460] sd 1:0:0:0: Attached scsi generic sg1 type 0
[    4.304600] scsi 2:0:0:0: Direct-Access     ATA      SAMSUNG HD322HJ  1AC0 PQ: 0 ANSI: 5
[    4.304863] sd 2:0:0:0: [sdc] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
[    4.305002] sd 2:0:0:0: [sdc] Write Protect is off
[    4.305087] sd 2:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    4.305110] sd 2:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.305284] sd 2:0:0:0: [sdc] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
[    4.305423] sd 2:0:0:0: [sdc] Write Protect is off
[    4.305507] sd 2:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    4.305529] sd 2:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.305664]  sdc: sdc1 sdc2
[    4.313349] sd 2:0:0:0: [sdc] Attached SCSI disk
[    4.313513] sd 2:0:0:0: Attached scsi generic sg2 type 0
[    4.313652] scsi 3:0:0:0: Direct-Access     ATA      SAMSUNG HD322HJ  1AC0 PQ: 0 ANSI: 5
[    4.313919] sd 3:0:0:0: [sdd] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
[    4.314059] sd 3:0:0:0: [sdd] Write Protect is off
[    4.314143] sd 3:0:0:0: [sdd] Mode Sense: 00 3a 00 00
[    4.314165] sd 3:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.314340] sd 3:0:0:0: [sdd] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
[    4.314479] sd 3:0:0:0: [sdd] Write Protect is off
[    4.314563] sd 3:0:0:0: [sdd] Mode Sense: 00 3a 00 00
[    4.314585] sd 3:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.314720]  sdd: sdd1 sdd2
[    4.319267] sd 3:0:0:0: [sdd] Attached SCSI disk
[    4.319429] sd 3:0:0:0: Attached scsi generic sg3 type 0
[    4.319569] scsi 4:0:0:0: Direct-Access     ATA      SAMSUNG HD322HJ  1AC0 PQ: 0 ANSI: 5
[    4.319843] sd 4:0:0:0: [sde] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
[    4.319983] sd 4:0:0:0: [sde] Write Protect is off
[    4.320071] sd 4:0:0:0: [sde] Mode Sense: 00 3a 00 00
[    4.320094] sd 4:0:0:0: [sde] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.320269] sd 4:0:0:0: [sde] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
[    4.320408] sd 4:0:0:0: [sde] Write Protect is off
[    4.320493] sd 4:0:0:0: [sde] Mode Sense: 00 3a 00 00
[    4.320515] sd 4:0:0:0: [sde] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.320650]  sde: sde1 sde2
[    4.330505] sd 4:0:0:0: [sde] Attached SCSI disk
[    4.330664] sd 4:0:0:0: Attached scsi generic sg4 type 0
[    4.331801] pata_marvell 0000:03:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    4.331953] pata_marvell 0000:03:00.0: setting latency timer to 64
[    4.332010] scsi6 : pata_marvell
[    4.332187] scsi7 : pata_marvell
[    4.332336] ata7: PATA max UDMA/100 cmd 0xec00 ctl 0xe880 bmdma 0xe400 irq 16
[    4.332430] ata8: PATA max UDMA/133 cmd 0xe800 ctl 0xe480 bmdma 0xe408 irq 16
[    4.496390] ata7.00: ATAPI: HL-DT-ST DVDRAM GSA-H42L, SL00, max UDMA/66
[    4.512399] ata7.00: configured for UDMA/66
[    4.683211] isa bounce pool size: 16 pages
[    4.686590] scsi 6:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-H42L  SL00 PQ: 0 ANSI: 5
[    4.698232] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    4.698363] Uniform CD-ROM driver Revision: 3.20
[    4.698593] sr 6:0:0:0: Attached scsi CD-ROM sr0
[    4.698677] sr 6:0:0:0: Attached scsi generic sg5 type 5
[    4.699447] usbcore: registered new interface driver libusual
[    4.699609] usbcore: registered new interface driver usbserial
[    4.699731] USB Serial support registered for generic
[    4.699850] usbcore: registered new interface driver usbserial_generic
[    4.699942] usbserial: USB Serial Driver core
[    4.700114] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    4.700204] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    4.700847] serio: i8042 KBD port at 0x60,0x64 irq 1
[    4.716126] mice: PS/2 mouse device common for all mice
[    4.752149] rtc_cmos 00:03: RTC can wake from S4
[    4.752302] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    4.752413] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    4.752601] device-mapper: uevent: version 1.0.3
[    4.752793] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
[    4.752980] device-mapper: multipath: version 1.0.5 loaded
[    4.753068] device-mapper: multipath round-robin: version 1.0.0 loaded
[    4.753198] cpuidle: using governor ladder
[    4.753279] cpuidle: using governor menu
[    4.753751] TCP cubic registered
[    4.753904] NET: Registered protocol family 10
[    4.754318] lo: Disabled Privacy Extensions
[    4.754643] NET: Registered protocol family 17
[    4.754765] Bluetooth: L2CAP ver 2.11
[    4.754844] Bluetooth: L2CAP socket layer initialized
[    4.754930] Bluetooth: SCO (Voice Link) ver 0.6
[    4.755013] Bluetooth: SCO socket layer initialized
[    4.755123] Bluetooth: RFCOMM socket layer initialized
[    4.755212] Bluetooth: RFCOMM TTY layer initialized
[    4.755296] Bluetooth: RFCOMM ver 1.10
[    4.755546] registered taskstats version 1
[    4.755739]   Magic number: 1:323:320
[    4.755837] tty tty45: hash matches
[    4.755967] rtc_cmos 00:03: setting system clock to 2009-03-03 08:19:22 UTC (1236068362)
[    4.756098] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    4.756187] EDD information not available.
[    4.756296] Freeing unused kernel memory: 532k freed
[    4.756562] Write protecting the kernel read-only data: 6592k
[    4.784975] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    4.867298] fuse init (API version 7.10)
[    4.885503] md: linear personality registered for level -1
[    4.887902] md: multipath personality registered for level -4
[    4.890118] md: raid0 personality registered for level 0
[    4.893220] md: raid1 personality registered for level 1
[    4.895268] xor: automatically using best checksumming function: generic_sse
[    4.912001]    generic_sse:  7824.000 MB/sec
[    4.912084] xor: using function: generic_sse (7824.000 MB/sec)
[    4.913163] async_tx: api initialized (async)
[    4.984013] raid6: int64x1   1935 MB/s
[    5.052015] raid6: int64x2   2651 MB/s
[    5.120019] raid6: int64x4   2481 MB/s
[    5.188033] raid6: int64x8   1863 MB/s
[    5.256005] raid6: sse2x1    3680 MB/s
[    5.324015] raid6: sse2x2    4286 MB/s
[    5.392008] raid6: sse2x4    6182 MB/s
[    5.392087] raid6: using algorithm sse2x4 (6182 MB/s)
[    5.392173] md: raid6 personality registered for level 6
[    5.392259] md: raid5 personality registered for level 5
[    5.392345] md: raid4 personality registered for level 4
[    5.404305] md: raid10 personality registered for level 10
[    5.438231] uhci_hcd: USB Universal Host Controller Interface driver
[    5.438373] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    5.438474] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    5.438477] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    5.438627] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    5.438776] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000b800
[    5.438937] usb usb1: configuration #1 chosen from 1 choice
[    5.439047] hub 1-0:1.0: USB hub found
[    5.439131] hub 1-0:1.0: 2 ports detected
[    5.439302] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    5.439400] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    5.439402] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    5.439531] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
[    5.439685] uhci_hcd 0000:00:1a.1: irq 21, io base 0x0000b880
[    5.439828] usb usb2: configuration #1 chosen from 1 choice
[    5.439936] hub 2-0:1.0: USB hub found
[    5.441534] hub 2-0:1.0: 2 ports detected
[    5.441687] uhci_hcd 0000:00:1a.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    5.441786] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[    5.441788] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    5.441910] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 3
[    5.442063] uhci_hcd 0000:00:1a.2: irq 18, io base 0x0000bc00
[    5.442213] usb usb3: configuration #1 chosen from 1 choice
[    5.442321] hub 3-0:1.0: USB hub found
[    5.442404] hub 3-0:1.0: 2 ports detected
[    5.442556] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    5.442653] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    5.442656] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    5.442780] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 4
[    5.442931] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000b080
[    5.443077] usb usb4: configuration #1 chosen from 1 choice
[    5.443184] hub 4-0:1.0: USB hub found
[    5.443266] hub 4-0:1.0: 2 ports detected
[    5.443416] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    5.443513] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    5.443516] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    5.443637] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 5
[    5.443788] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000b400
[    5.443933] usb usb5: configuration #1 chosen from 1 choice
[    5.444041] hub 5-0:1.0: USB hub found
[    5.444124] hub 5-0:1.0: 2 ports detected
[    5.444274] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    5.444372] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    5.444374] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    5.444497] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 6
[    5.444647] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000b480
[    5.444791] usb usb6: configuration #1 chosen from 1 choice
[    5.444900] hub 6-0:1.0: USB hub found
[    5.444983] hub 6-0:1.0: 2 ports detected
[    5.499927] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    5.500043] Warning! ehci_hcd should always be loaded before uhci_hcd and ohci_hcd, not after
[    5.500205] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    5.500332] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    5.500335] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    5.500490] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 7
[    5.504505] ehci_hcd 0000:00:1a.7: debug port 1
[    5.504595] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    5.504602] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xf9fffc00
[    5.520023] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    5.520187] usb usb7: configuration #1 chosen from 1 choice
[    5.520298] hub 7-0:1.0: USB hub found
[    5.520382] hub 7-0:1.0: 6 ports detected
[    5.520561] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    5.520670] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    5.520673] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    5.520801] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 8
[    5.523034] ATL1E 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    5.523147] ATL1E 0000:02:00.0: setting latency timer to 64
[    5.524833] ehci_hcd 0000:00:1d.7: debug port 1
[    5.524922] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    5.524929] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf9fff800
[    5.543462] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    5.543634] usb usb8: configuration #1 chosen from 1 choice
[    5.543745] hub 8-0:1.0: USB hub found
[    5.543832] hub 8-0:1.0: 6 ports detected
[    5.550183] ohci1394 0000:05:03.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    5.602045] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[19]  MMIO=[febef000-febef7ff]  Max Packet=[2048]  IR/IT contexts=[8/8]
[    5.609947] md: bind<sdb1>
[    5.610325] mdadm[1164]: segfault at 0 ip 000000000040839b sp 00007fff5ad72850 error 4 in mdadm[400000+2a000]
[    5.612209] md: bind<sdb2>
[    5.612563] mdadm[1178]: segfault at 0 ip 000000000040839b sp 00007fff25f18a00 error 4 in mdadm[400000+2a000]
[    5.637860] md: bind<sdd1>
[    5.638354] mdadm[1185]: segfault at 0 ip 000000000040839b sp 00007fffc3170c50 error 4 in mdadm[400000+2a000]
[    5.639329] md: bind<sdd2>
[    5.639668] mdadm[1234]: segfault at 0 ip 000000000040839b sp 00007fff24abf5a0 error 4 in mdadm[400000+2a000]
[    5.641893] md: bind<sde1>
[    5.642705] mdadm[1220]: segfault at 0 ip 000000000040839b sp 00007fff49098b80 error 4 in mdadm[400000+2a000]
[    5.643119] md: bind<sde2>
[    5.643831] mdadm[1243]: segfault at 0 ip 000000000040839b sp 00007fff8c4ccfb0 error 4 in mdadm[400000+2a000]
[    5.665339] md: bind<sdc1>
[    5.665664] md: bind<sdc2>
[    5.666406] mdadm[1312]: segfault at 0 ip 000000000040839b sp 00007ffffb1c2ca0 error 4 in mdadm[400000+2a000]
[    5.667382] mdadm[1183]: segfault at 0 ip 000000000040839b sp 00007fff2215dc40 error 4 in mdadm[400000+2a000]
[    5.862877] PM: Starting manual resume from disk
[    5.862962] PM: Resume from partition 8:2
[    5.862963] PM: Checking hibernation image.
[    5.863035] PM: Resume from disk failed.
[    5.875187] EXT4-fs: barriers enabled
[    5.881097] kjournald2 starting.  Commit interval 5 seconds
[    5.881110] EXT4-fs: delayed allocation enabled
[    5.881112] EXT4-fs: file extents enabled
[    5.885368] EXT4-fs: mballoc enabled
[    5.885449] EXT4-fs: mounted filesystem with ordered data mode.
[    6.096534] usb 5-2: new low speed USB device using uhci_hcd and address 2
[    6.460114] usb 5-2: configuration #1 chosen from 1 choice
[    6.884123] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[001e8c0001815c6c]
[    8.687177] udev: starting version 139
[    8.869004] usbcore: registered new interface driver hiddev
[    8.884657] input: Razer Razer 1600dpi 3 button optical mouse as /devices/pci0000:00/0000:00:1d.1/usb5/5-2/5-2:1.0/input/input4
[    8.916141] generic-usb 0003:1532:0003.0001: input,hidraw0: USB HID v1.10 Mouse [Razer Razer 1600dpi 3 button optical mouse] on usb-0000:00:1d.1-2/input0
[    8.916318] usbcore: registered new interface driver usbhid
[    8.916423] usbhid: v2.6:USB HID core driver
[    9.065200] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    9.065395] HDA Intel 0000:00:1b.0: setting latency timer to 64
[    9.171404] iTCO_vendor_support: vendor-support=0
[    9.190087] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05
[    9.190296] iTCO_wdt: Found a ICH10R TCO device (Version=2, TCOBASE=0x0860)
[    9.190463] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[    9.216084] cfg80211: Calling CRDA to update world regulatory domain
[    9.316041] input: PC Speaker as /devices/platform/pcspkr/input/input5
[    9.510306] ath5k_pci 0000:05:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    9.510479] ath5k_pci 0000:05:00.0: registered as 'phy0'
[    9.596814] phy0: Selected rate control algorithm 'pid'
[    9.657615] ath5k phy0: Atheros AR2414 chip found (MAC: 0x79, PHY: 0x45)
[    9.790928] lp: driver loaded but no devices found
[    9.806699] ppdev: user-space parallel port driver
[    9.919227] Adding 5855684k swap on /dev/sda2.  Priority:-1 extents:1 across:5855684k
[   10.010455] EXT4 FS on sda3, internal journal on sda3:8
[   10.218790] EXT4-fs: unable to read superblock
[   10.371778] type=1505 audit(1236068368.112:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=3021
[   10.440679] type=1505 audit(1236068368.184:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=3025
[   10.440785] type=1505 audit(1236068368.184:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=3025
[   10.440828] type=1505 audit(1236068368.184:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=3025
[   10.440869] type=1505 audit(1236068368.184:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=3025
[   10.564339] type=1505 audit(1236068368.304:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=3030
[   10.564483] type=1505 audit(1236068368.304:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=3030
[   10.600341] type=1505 audit(1236068368.340:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=3034
[   12.238291] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   12.238293] Bluetooth: BNEP filters: protocol multicast
[   12.287978] Bridge firewalling registered
[   17.256921] ATL1E 0000:02:00.0: irq 2298 for MSI/MSI-X
[   17.257078] ATL1E 0000:02:00.0: ATL1E: eth0 NIC Link is Up<1000 Mbps Full Duplex>
[   17.257363] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   17.257721] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   17.300828] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   20.272510] wlan0: direct probe to AP 00:1a:4f:93:ac:54 try 1
[   20.275533] wlan0 direct probe responded
[   20.275536] wlan0: authenticate with AP 00:1a:4f:93:ac:54
[   20.277721] wlan0: authenticated
[   20.277725] wlan0: associate with AP 00:1a:4f:93:ac:54
[   20.280312] wlan0: RX AssocResp from 00:1a:4f:93:ac:54 (capab=0x401 status=0 aid=2)
[   20.280314] wlan0: associated
[   20.280587] wlan0: disassociating by local choice (reason=3)
[   21.755844] warning: `pulseaudio' uses 32-bit capabilities (legacy support in use)
[   28.212509] eth0: no IPv6 routers present


```

/etc/fstab

```

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda3 during installation
UUID=dcf81f22-e3db-4a09-a2f7-7f27874e8f07 /               ext4    relatime,errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=dc35f8fc-55d5-4d77-af79-b646c8390a7a /boot           ext2    relatime        0       2




#UUID=98bab6ad:a1aff66a:0c6752e2:cee47139 /var/www	   ext4    relatime	   0	   2
/dev/md2 /mnt/raid2 ext4 defaults 0 0
#/dev/md1 /home ext4 defaults 0 0



# none was on /dev/sda2 during installation
UUID=1a81de76-f1e6-49f7-ab7a-07a4c6493323 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


```


```

# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.

DEVICE /dev/sdb1 /dev/sdc1 /dev/sdd1 /dev/sde1
DEVICE /dev/sdb2 /dev/sdc2 /dev/sdd2 /dev/sde2
DEVICE partitions

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays


ARRAY /dev/md1 level=raid10 auto=md num-devices=4 UUID=48336996:25d081cb:0c6752e2:cee47139
ARRAY /dev/md2 level=raid10 auto=md num-devices=4 UUID=98bab6ad:a1aff66a:0c6752e2:cee47139


# This file was auto-generated on Sat, 21 Feb 2009 23:36:30 +0100
# by mkconf $Id$


```

---

### Post by ikonia on 2009-03-03
first thing is - why are you using Jaunty ? if this is doe debugging - then log a bug surly, Jaunty is still in development.


Second thing is check the uuid's of the disks that are needed to start the array.

Make sure they are available, also make sure your mdadm init script is there to pickup monitor as this will also assemble/start them for you.

---

### Post by Nohthee8 on 2009-04-16
Hi,

Please forgive me and re-direct me if I'm posting in the wrong place. I am new to Ubuntu Forums (although I've been using Linux since 1994) and I have tried to read all the rules and sticky posts.

The reason I'm writing here is that I seem to have similar symptoms to the original poster, but with four qualifications:

1. I'm using Intrepid Ibex, so if it's the same problem, it's not a Jaunty-specific issue.

2. I haven't (yet) been able to assemble my problem array manually.

3. Whether I file a new bug, or confirm an existing one, still I need help to work around the problem.

4. I've found this upstream bug report that appears to describe similar conditions:
   
   [http://bugzilla.kernel.org/show_bug.cgi?id=11967](http://bugzilla.kernel.org/show_bug.cgi?id=11967)
  
   "When disks are removed from a raid10 set, then readded,
    the raid10 driver marks the disks as spare and doesn't resync."
   

Although I'm a fairly experienced Linux user, I'm pretty new to RAID, so I need advice on how to proceed.

In particular, I need help in diagnosing the problem safely and precisely, so that I don't inadvertently render recoverable data, unrecoverable.

My /proc/mdstat
[HTML]
<pre>

Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md1 : inactive sdb4[0](S) sdf4[4](S) sde4[3](S) sdd4[2](S) sdc4[1](S)
      4829419520 blocks

md0 : active raid1 sdb2[0] sdf2[2](S) sdc2[1]
      9767424 blocks [2/2] [UU]

unused devices: <none>
</pre>
[/HTML]

I can post a whole load of other logs and diagnostics (e.g. from mdadm) if there is anyone interested in pursuing this problem.

---

