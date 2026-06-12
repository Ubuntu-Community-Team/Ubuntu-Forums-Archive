---
title: "Slow Boot - Surface Pro 3"
date: 2015-03-18
forum: Ubuntu Development Version
---

### Post by gunksta on 2015-03-18
I have installed Ubuntu onto a Microsoft Surface Pro 3.

I confess - it is snazzy hardware.

But, my computer takes a long time, well over a minute to boot. I am not familiar with UEFI systems, and UEFI cannot be fully disabled on this "laptop", so it is possible that I am doing something wrong with that, but it does eventually boot.

Below is s recent boot log. Any thoughts are gladly accepted. It strikes me that this makes it appear that it is booting reasonably well. I have been struggling to get it to recognize the encrypted swap file I set up, but it is currently disabled so that should not be a factor here.

```

03/18/15 08:39:03 PM    optimus    kernel    [    0.336815] NetLabel: Initializing
03/18/15 08:39:03 PM    optimus    kernel    [    0.336816] NetLabel:  domain hash size = 128
03/18/15 08:39:03 PM    optimus    kernel    [    0.336818] NetLabel:  protocols = UNLABELED CIPSOv4
03/18/15 08:39:03 PM    optimus    kernel    [    0.336833] NetLabel:  unlabeled traffic allowed by default
03/18/15 08:39:03 PM    optimus    kernel    [    0.336913] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
03/18/15 08:39:03 PM    optimus    kernel    [    0.336920] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
03/18/15 08:39:03 PM    optimus    kernel    [    0.338968] Switched to clocksource hpet
03/18/15 08:39:03 PM    optimus    kernel    [    0.346009] AppArmor: AppArmor Filesystem Enabled
03/18/15 08:39:03 PM    optimus    kernel    [    0.346091] pnp: PnP ACPI init
03/18/15 08:39:03 PM    optimus    kernel    [    0.346431] system 00:00: [io  0x0680-0x069f] has been reserved
03/18/15 08:39:03 PM    optimus    kernel    [    0.346435] system 00:00: [io  0xffff] has been reserved
03/18/15 08:39:03 PM    optimus    kernel    [    0.346438] system 00:00: [io  0xffff] has been reserved
03/18/15 08:39:03 PM    optimus    kernel    [    0.346441] system 00:00: [io  0xffff] has been reserved
03/18/15 08:39:03 PM    optimus    kernel    [    0.346443] system 00:00: [io  0x1800-0x18fe] could not be reserved
03/18/15 08:39:03 PM    optimus    kernel    [    0.346446] system 00:00: [io  0x164e-0x164f] has been reserved
03/18/15 08:39:03 PM    optimus    kernel    [    0.346451] system 00:00: Plug and Play ACPI device, IDs PNP0c02 (active)
03/18/15 08:39:03 PM    optimus    kernel    [    0.346516] pnp 00:01: Plug and Play ACPI device, IDs PNP0b00 (active)
03/18/15 08:39:03 PM    optimus    kernel    [    0.346575] system 00:02: [io  0x1854-0x1857] has been reserved
03/18/15 08:39:03 PM    optimus    kernel    [    0.346579] system 00:02: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
03/18/15 08:39:03 PM    optimus    kernel    [    0.359170] system 00:03: [mem 0xfed1c000-0xfed1ffff] has been reserved
03/18/15 08:39:03 PM    optimus    kernel    [    0.359174] system 00:03: [mem 0xfed10000-0xfed17fff] has been reserved
03/18/15 08:39:03 PM    optimus    kernel    [    0.359176] system 00:03: [mem 0xfed18000-0xfed18fff] has been reserved
03/18/15 08:39:03 PM    optimus    kernel    [    0.359178] system 00:03: [mem 0xfed19000-0xfed19fff] has been reserved
03/18/15 08:39:03 PM    optimus    kernel    [    0.359181] system 00:03: [mem 0xe0000000-0xefffffff] has been reserved
03/18/15 08:39:03 PM    optimus    kernel    [    0.359183] system 00:03: [mem 0xfed20000-0xfed3ffff] has been reserved
03/18/15 08:39:03 PM    optimus    kernel    [    0.359185] system 00:03: [mem 0xfed90000-0xfed93fff] could not be reserved
03/18/15 08:39:03 PM    optimus    kernel    [    0.359188] system 00:03: [mem 0xff000000-0xffffffff] has been reserved
03/18/15 08:39:03 PM    optimus    kernel    [    0.359190] system 00:03: [mem 0xfee00000-0xfeefffff] has been reserved
03/18/15 08:39:03 PM    optimus    kernel    [    0.359192] system 00:03: [mem 0xaf210000-0xaf21ffff] has been reserved
03/18/15 08:39:03 PM    optimus    kernel    [    0.359195] system 00:03: Plug and Play ACPI device, IDs PNP0c02 (active)
03/18/15 08:39:03 PM    optimus    kernel    [    0.359574] system 00:04: [mem 0xfe104000-0xfe104fff] has been reserved
03/18/15 08:39:03 PM    optimus    kernel    [    0.359577] system 00:04: [mem 0xfe106000-0xfe106fff] has been reserved
03/18/15 08:39:03 PM    optimus    kernel    [    0.359580] system 00:04: Plug and Play ACPI device, IDs PNP0c02 (active)
03/18/15 08:39:03 PM    optimus    kernel    [    0.360297] pnp: PnP ACPI: found 5 devices
03/18/15 08:39:03 PM    optimus    kernel    [    0.367090] pci 0000:00:1c.0: PCI bridge to [bus 01]
03/18/15 08:39:03 PM    optimus    kernel    [    0.367105] pci 0000:00:1c.0:   bridge window [mem 0xc0400000-0xc05fffff]
03/18/15 08:39:03 PM    optimus    kernel    [    0.367115] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
03/18/15 08:39:03 PM    optimus    kernel    [    0.367117] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
03/18/15 08:39:03 PM    optimus    kernel    [    0.367119] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
03/18/15 08:39:03 PM    optimus    kernel    [    0.367121] pci_bus 0000:00: resource 7 [mem 0x000c0000-0x000c3fff]
03/18/15 08:39:03 PM    optimus    kernel    [    0.367123] pci_bus 0000:00: resource 8 [mem 0x000c4000-0x000c7fff]
03/18/15 08:39:03 PM    optimus    kernel    [    0.367125] pci_bus 0000:00: resource 9 [mem 0x000c8000-0x000cbfff]
03/18/15 08:39:03 PM    optimus    kernel    [    0.367127] pci_bus 0000:00: resource 10 [mem 0x000cc000-0x000cffff]
03/18/15 08:39:03 PM    optimus    kernel    [    0.367129] pci_bus 0000:00: resource 11 [mem 0x000d0000-0x000d3fff]
03/18/15 08:39:03 PM    optimus    kernel    [    0.367131] pci_bus 0000:00: resource 12 [mem 0x000d4000-0x000d7fff]
03/18/15 08:39:03 PM    optimus    kernel    [    0.367133] pci_bus 0000:00: resource 13 [mem 0x000d8000-0x000dbfff]
03/18/15 08:39:03 PM    optimus    kernel    [    0.367134] pci_bus 0000:00: resource 14 [mem 0x000dc000-0x000dffff]
03/18/15 08:39:03 PM    optimus    kernel    [    0.367136] pci_bus 0000:00: resource 15 [mem 0x000e0000-0x000e3fff]
03/18/15 08:39:03 PM    optimus    kernel    [    0.367138] pci_bus 0000:00: resource 16 [mem 0x000e4000-0x000e7fff]
03/18/15 08:39:03 PM    optimus    kernel    [    0.367140] pci_bus 0000:00: resource 17 [mem 0x000e8000-0x000ebfff]
03/18/15 08:39:03 PM    optimus    kernel    [    0.367142] pci_bus 0000:00: resource 18 [mem 0x000ec000-0x000effff]
03/18/15 08:39:03 PM    optimus    kernel    [    0.367144] pci_bus 0000:00: resource 19 [mem 0x000f0000-0x000fffff]
03/18/15 08:39:03 PM    optimus    kernel    [    0.367146] pci_bus 0000:00: resource 20 [mem 0xfed40000-0xfed44fff]
03/18/15 08:39:03 PM    optimus    kernel    [    0.367148] pci_bus 0000:00: resource 21 [mem 0xaf200000-0xfeafffff]
03/18/15 08:39:03 PM    optimus    kernel    [    0.367150] pci_bus 0000:01: resource 1 [mem 0xc0400000-0xc05fffff]
03/18/15 08:39:03 PM    optimus    kernel    [    0.367184] NET: Registered protocol family 2
03/18/15 08:39:03 PM    optimus    kernel    [    0.367397] TCP established hash table entries: 65536 (order: 7, 524288 bytes)
03/18/15 08:39:03 PM    optimus    kernel    [    0.367574] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
03/18/15 08:39:03 PM    optimus    kernel    [    0.367724] TCP: Hash tables configured (established 65536 bind 65536)
03/18/15 08:39:03 PM    optimus    kernel    [    0.367743] TCP: reno registered
03/18/15 08:39:03 PM    optimus    kernel    [    0.367757] UDP hash table entries: 4096 (order: 5, 131072 bytes)
03/18/15 08:39:03 PM    optimus    kernel    [    0.367790] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
03/18/15 08:39:03 PM    optimus    kernel    [    0.367853] NET: Registered protocol family 1
03/18/15 08:39:03 PM    optimus    kernel    [    0.367872] pci 0000:00:02.0: Video device with shadowed ROM
03/18/15 08:39:03 PM    optimus    kernel    [    0.368204] PCI: CLS 64 bytes, default 64
03/18/15 08:39:03 PM    optimus    kernel    [    0.368258] Trying to unpack rootfs image as initramfs...
03/18/15 08:39:03 PM    optimus    kernel    [    1.021445] Freeing initrd memory: 29708K (ffff8800345ea000 - ffff8800362ed000)
03/18/15 08:39:03 PM    optimus    kernel    [    1.021482] dmar: ACPI device "INT33C2:00" under DMAR at fed91000 as 00:15.1
03/18/15 08:39:03 PM    optimus    kernel    [    1.021487] dmar: ACPI device "INT33C3:00" under DMAR at fed91000 as 00:15.2
03/18/15 08:39:03 PM    optimus    kernel    [    1.021498] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
03/18/15 08:39:03 PM    optimus    kernel    [    1.021501] software IO TLB [mem 0xa419d000-0xa819d000] (64MB) mapped at [ffff8800a419d000-ffff8800a819cfff]
03/18/15 08:39:03 PM    optimus    kernel    [    1.021747] RAPL PMU detected, hw unit 2^-14 Joules, API unit is 2^-32 Joules, 4 fixed counters 655360 ms ovfl timer
03/18/15 08:39:03 PM    optimus    kernel    [    1.021811] microcode: CPU0 sig=0x40651, pf=0x40, revision=0x1c
03/18/15 08:39:03 PM    optimus    kernel    [    1.021822] microcode: CPU1 sig=0x40651, pf=0x40, revision=0x1c
03/18/15 08:39:03 PM    optimus    kernel    [    1.021832] microcode: CPU2 sig=0x40651, pf=0x40, revision=0x1c
03/18/15 08:39:03 PM    optimus    kernel    [    1.021841] microcode: CPU3 sig=0x40651, pf=0x40, revision=0x1c
03/18/15 08:39:03 PM    optimus    kernel    [    1.021908] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
03/18/15 08:39:03 PM    optimus    kernel    [    1.021944] Scanning for low memory corruption every 60 seconds
03/18/15 08:39:03 PM    optimus    kernel    [    1.022348] futex hash table entries: 1024 (order: 4, 65536 bytes)
03/18/15 08:39:03 PM    optimus    kernel    [    1.022370] Initialise system trusted keyring
03/18/15 08:39:03 PM    optimus    kernel    [    1.022395] audit: initializing netlink subsys (disabled)
03/18/15 08:39:03 PM    optimus    kernel    [    1.022410] audit: type=2000 audit(1426725451.016:1): initialized
03/18/15 08:39:03 PM    optimus    kernel    [    1.022832] HugeTLB registered 2 MB page size, pre-allocated 0 pages
03/18/15 08:39:03 PM    optimus    kernel    [    1.024686] zpool: loaded
03/18/15 08:39:03 PM    optimus    kernel    [    1.024689] zbud: loaded
03/18/15 08:39:03 PM    optimus    kernel    [    1.024898] VFS: Disk quotas dquot_6.5.2
03/18/15 08:39:03 PM    optimus    kernel    [    1.024942] VFS: Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
03/18/15 08:39:03 PM    optimus    kernel    [    1.025521] fuse init (API version 7.23)
03/18/15 08:39:03 PM    optimus    kernel    [    1.025695] Key type big_key registered
03/18/15 08:39:03 PM    optimus    kernel    [    1.026140] Key type asymmetric registered
03/18/15 08:39:03 PM    optimus    kernel    [    1.026144] Asymmetric key parser 'x509' registered
03/18/15 08:39:03 PM    optimus    kernel    [    1.026204] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
03/18/15 08:39:03 PM    optimus    kernel    [    1.026251] io scheduler noop registered
03/18/15 08:39:03 PM    optimus    kernel    [    1.026255] io scheduler deadline registered (default)
03/18/15 08:39:03 PM    optimus    kernel    [    1.026296] io scheduler cfq registered
03/18/15 08:39:03 PM    optimus    kernel    [    1.026710] pcieport 0000:00:1c.0: Signaling PME through PCIe PME interrupt
03/18/15 08:39:03 PM    optimus    kernel    [    1.026714] pci 0000:01:00.0: Signaling PME through PCIe PME interrupt
03/18/15 08:39:03 PM    optimus    kernel    [    1.026725] pcie_pme 0000:00:1c.0:pcie01: service driver pcie_pme loaded
03/18/15 08:39:03 PM    optimus    kernel    [    1.026734] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
03/18/15 08:39:03 PM    optimus    kernel    [    1.026754] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
03/18/15 08:39:03 PM    optimus    kernel    [    1.026807] efifb: probing for efifb
03/18/15 08:39:03 PM    optimus    kernel    [    1.026825] efifb: framebuffer at 0xb0000000, mapped to 0xffffc90010e80000, using 1920k, total 1920k
03/18/15 08:39:03 PM    optimus    kernel    [    1.026827] efifb: mode is 800x600x32, linelength=3200, pages=1
03/18/15 08:39:03 PM    optimus    kernel    [    1.026828] efifb: scrolling: redraw
03/18/15 08:39:03 PM    optimus    kernel    [    1.026830] efifb: Truecolor: size=8:8:8:8, shift=24:16:8:0
03/18/15 08:39:03 PM    optimus    kernel    [    1.026929] Console: switching to colour frame buffer device 100x37
03/18/15 08:39:03 PM    optimus    kernel    [    1.026940] fb0: EFI VGA frame buffer device
03/18/15 08:39:03 PM    optimus    kernel    [    1.026952] intel_idle: MWAIT substates: 0x11142120
03/18/15 08:39:03 PM    optimus    kernel    [    1.026954] intel_idle: v0.4 model 0x45
03/18/15 08:39:03 PM    optimus    kernel    [    1.026955] intel_idle: lapic_timer_reliable_states 0xffffffff
03/18/15 08:39:03 PM    optimus    kernel    [    1.042641] ACPI: AC Adapter [AC0] (on-line)
03/18/15 08:39:03 PM    optimus    kernel    [    1.042802] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:14/PNP0C0D:00/input/input0
03/18/15 08:39:03 PM    optimus    kernel    [    1.042819] ACPI: Lid Switch [LID0]
03/18/15 08:39:03 PM    optimus    kernel    [    1.090642] [Firmware Bug]: Invalid critical threshold (98)
03/18/15 08:39:03 PM    optimus    kernel    [    1.114638] thermal LNXTHERM:00: registered as thermal_zone0
03/18/15 08:39:03 PM    optimus    kernel    [    1.114642] ACPI: Thermal Zone [TZ0] (-270 C)
03/18/15 08:39:03 PM    optimus    kernel    [    1.114729] acpi PNP0C0A:00: Driver battery requests probe deferral
03/18/15 08:39:03 PM    optimus    kernel    [    1.114736] GHES: HEST is not enabled!
03/18/15 08:39:03 PM    optimus    kernel    [    1.114988] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
03/18/15 08:39:03 PM    optimus    kernel    [    1.117746] Linux agpgart interface v0.103
03/18/15 08:39:03 PM    optimus    kernel    [    1.119177] brd: module loaded
03/18/15 08:39:03 PM    optimus    kernel    [    1.119895] loop: module loaded
03/18/15 08:39:03 PM    optimus    kernel    [    1.120133] libphy: Fixed MDIO Bus: probed
03/18/15 08:39:03 PM    optimus    kernel    [    1.120137] tun: Universal TUN/TAP device driver, 1.6
03/18/15 08:39:03 PM    optimus    kernel    [    1.120139] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
03/18/15 08:39:03 PM    optimus    kernel    [    1.120193] PPP generic driver version 2.4.2
03/18/15 08:39:03 PM    optimus    kernel    [    1.120414] xhci_hcd 0000:00:14.0: xHCI Host Controller
03/18/15 08:39:03 PM    optimus    kernel    [    1.120422] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 1
03/18/15 08:39:03 PM    optimus    kernel    [    1.120512] xhci_hcd 0000:00:14.0: cache line size of 64 is not supported
03/18/15 08:39:03 PM    optimus    kernel    [    1.120604] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
03/18/15 08:39:03 PM    optimus    kernel    [    1.120607] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
03/18/15 08:39:03 PM    optimus    kernel    [    1.120609] usb usb1: Product: xHCI Host Controller
03/18/15 08:39:03 PM    optimus    kernel    [    1.120611] usb usb1: Manufacturer: Linux 3.19.0-9-generic xhci-hcd
03/18/15 08:39:03 PM    optimus    kernel    [    1.120613] usb usb1: SerialNumber: 0000:00:14.0
03/18/15 08:39:03 PM    optimus    kernel    [    1.120743] hub 1-0:1.0: USB hub found
03/18/15 08:39:03 PM    optimus    kernel    [    1.120756] hub 1-0:1.0: 9 ports detected
03/18/15 08:39:03 PM    optimus    kernel    [    1.122359] xhci_hcd 0000:00:14.0: xHCI Host Controller
03/18/15 08:39:03 PM    optimus    kernel    [    1.122363] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 2
03/18/15 08:39:03 PM    optimus    kernel    [    1.122399] usb usb2: New USB device found, idVendor=1d6b, idProduct=0003
03/18/15 08:39:03 PM    optimus    kernel    [    1.122401] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
03/18/15 08:39:03 PM    optimus    kernel    [    1.122403] usb usb2: Product: xHCI Host Controller
03/18/15 08:39:03 PM    optimus    kernel    [    1.122405] usb usb2: Manufacturer: Linux 3.19.0-9-generic xhci-hcd
03/18/15 08:39:03 PM    optimus    kernel    [    1.122407] usb usb2: SerialNumber: 0000:00:14.0
03/18/15 08:39:03 PM    optimus    kernel    [    1.122524] hub 2-0:1.0: USB hub found
03/18/15 08:39:03 PM    optimus    kernel    [    1.122546] hub 2-0:1.0: 4 ports detected
03/18/15 08:39:03 PM    optimus    kernel    [    1.122922] usb: failed to peer usb2-port2 and usb1-port1 by location (usb2-port2:none) (usb1-port1:usb2-port1)
03/18/15 08:39:03 PM    optimus    kernel    [    1.122925] usb usb2-port2: failed to peer to usb1-port1 (-16)
03/18/15 08:39:03 PM    optimus    kernel    [    1.122926] usb: port power management may be unreliable
03/18/15 08:39:03 PM    optimus    kernel    [    1.123244] usb: failed to peer usb2-port4 and usb1-port1 by location (usb2-port4:none) (usb1-port1:usb2-port1)
03/18/15 08:39:03 PM    optimus    kernel    [    1.123246] usb usb2-port4: failed to peer to usb1-port1 (-16)
03/18/15 08:39:03 PM    optimus    kernel    [    1.123327] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
03/18/15 08:39:03 PM    optimus    kernel    [    1.123334] ehci-pci: EHCI PCI platform driver
03/18/15 08:39:03 PM    optimus    kernel    [    1.123347] ehci-platform: EHCI generic platform driver
03/18/15 08:39:03 PM    optimus    kernel    [    1.123359] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
03/18/15 08:39:03 PM    optimus    kernel    [    1.123364] ohci-pci: OHCI PCI platform driver
03/18/15 08:39:03 PM    optimus    kernel    [    1.123376] ohci-platform: OHCI generic platform driver
03/18/15 08:39:03 PM    optimus    kernel    [    1.123387] uhci_hcd: USB Universal Host Controller Interface driver
03/18/15 08:39:03 PM    optimus    kernel    [    1.123442] i8042: PNP: No PS/2 controller found. Probing ports directly.
03/18/15 08:39:03 PM    optimus    kernel    [    1.657518] i8042: Can't read CTR while initializing i8042
03/18/15 08:39:03 PM    optimus    kernel    [    1.657523] i8042: probe of i8042 failed with error -5
03/18/15 08:39:03 PM    optimus    kernel    [    1.657633] mousedev: PS/2 mouse device common for all mice
03/18/15 08:39:03 PM    optimus    kernel    [    1.657791] rtc_cmos 00:01: RTC can wake from S4
03/18/15 08:39:03 PM    optimus    kernel    [    1.657938] rtc_cmos 00:01: rtc core: registered rtc_cmos as rtc0
03/18/15 08:39:03 PM    optimus    kernel    [    1.657974] rtc_cmos 00:01: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
03/18/15 08:39:03 PM    optimus    kernel    [    1.657996] i2c /dev entries driver
03/18/15 08:39:03 PM    optimus    kernel    [    1.658076] device-mapper: uevent: version 1.0.3
03/18/15 08:39:03 PM    optimus    kernel    [    1.658162] device-mapper: ioctl: 4.29.0-ioctl (2014-10-28) initialised: dm-devel@redhat.com
03/18/15 08:39:03 PM    optimus    kernel    [    1.658189] Intel P-state driver initializing.
03/18/15 08:39:03 PM    optimus    kernel    [    1.658340] Consider also installing thermald for improved thermal control.
03/18/15 08:39:03 PM    optimus    kernel    [    1.658347] ledtrig-cpu: registered to indicate activity on CPUs
03/18/15 08:39:03 PM    optimus    kernel    [    1.658353] EFI Variables Facility v0.08 2004-May-17
03/18/15 08:39:03 PM    optimus    kernel    [    1.662079] PCCT header not found.
03/18/15 08:39:03 PM    optimus    kernel    [    1.662080] ACPI PCC probe failed.
03/18/15 08:39:03 PM    optimus    kernel    [    1.662158] TCP: cubic registered
03/18/15 08:39:03 PM    optimus    kernel    [    1.662253] NET: Registered protocol family 10
03/18/15 08:39:03 PM    optimus    kernel    [    1.662455] NET: Registered protocol family 17
03/18/15 08:39:03 PM    optimus    kernel    [    1.662468] Key type dns_resolver registered
03/18/15 08:39:03 PM    optimus    kernel    [    1.662830] Loading compiled-in X.509 certificates
03/18/15 08:39:03 PM    optimus    kernel    [    1.663524] Loaded X.509 cert 'Magrathea: Glacier signing key: 9089f89ac460c1e211b30b5e52029c33367403bd'
03/18/15 08:39:03 PM    optimus    kernel    [    1.663537] registered taskstats version 1
03/18/15 08:39:03 PM    optimus    kernel    [    1.664948] Key type trusted registered
03/18/15 08:39:03 PM    optimus    kernel    [    1.667715] Key type encrypted registered
03/18/15 08:39:03 PM    optimus    kernel    [    1.667723] AppArmor: AppArmor sha1 policy hashing enabled
03/18/15 08:39:03 PM    optimus    kernel    [    1.667727] ima: No TPM chip found, activating TPM-bypass!
03/18/15 08:39:03 PM    optimus    kernel    [    1.667747] evm: HMAC attrs: 0x1
03/18/15 08:39:03 PM    optimus    kernel    [    1.668162] acpi PNP0C0A:00: Driver battery requests probe deferral
03/18/15 08:39:03 PM    optimus    kernel    [    1.668179]   Magic number: 7:984:607
03/18/15 08:39:03 PM    optimus    kernel    [    1.668290] rtc_cmos 00:01: setting system clock to 2015-03-19 00:37:31 UTC (1426725451)
03/18/15 08:39:03 PM    optimus    kernel    [    1.668365] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
03/18/15 08:39:03 PM    optimus    kernel    [    1.668366] EDD information not available.
03/18/15 08:39:03 PM    optimus    kernel    [    1.668487] PM: Hibernation image not present or could not be loaded.
03/18/15 08:39:03 PM    optimus    kernel    [    1.668801] Freeing unused kernel memory: 1408K (ffffffff81d35000 - ffffffff81e95000)
03/18/15 08:39:03 PM    optimus    kernel    [    1.668803] Write protecting the kernel read-only data: 12288k
03/18/15 08:39:03 PM    optimus    kernel    [    1.669016] Freeing unused kernel memory: 192K (ffff8800027d0000 - ffff880002800000)
03/18/15 08:39:03 PM    optimus    kernel    [    1.669108] Freeing unused kernel memory: 348K (ffff880002ba9000 - ffff880002c00000)
03/18/15 08:39:03 PM    optimus    kernel    [    1.681831] random: systemd-udevd urandom read with 3 bits of entropy available
03/18/15 08:39:03 PM    optimus    kernel    [    1.706146] sdhci: Secure Digital Host Controller Interface driver
03/18/15 08:39:03 PM    optimus    kernel    [    1.706149] sdhci: Copyright(c) Pierre Ossman
03/18/15 08:39:03 PM    optimus    kernel    [    1.713418] [drm] Initialized drm 1.1.0 20060810
03/18/15 08:39:03 PM    optimus    kernel    [    1.714895] ahci 0000:00:1f.2: version 3.0
03/18/15 08:39:03 PM    optimus    kernel    [    1.730222] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 3 ports 6 Gbps 0x1 impl SATA mode
03/18/15 08:39:03 PM    optimus    kernel    [    1.730227] ahci 0000:00:1f.2: flags: 64bit ncq pm led clo only pio slum part deso sadm sds apst 
03/18/15 08:39:03 PM    optimus    kernel    [    1.730791] scsi host0: ahci
03/18/15 08:39:03 PM    optimus    kernel    [    1.732682] scsi host1: ahci
03/18/15 08:39:03 PM    optimus    kernel    [    1.732796] scsi host2: ahci
03/18/15 08:39:03 PM    optimus    kernel    [    1.732843] ata1: SATA max UDMA/133 abar m2048@0xc061a000 port 0xc061a100 irq 44
03/18/15 08:39:03 PM    optimus    kernel    [    1.732845] ata2: DUMMY
03/18/15 08:39:03 PM    optimus    kernel    [    1.732846] ata3: DUMMY
03/18/15 08:39:03 PM    optimus    kernel    [    1.732924] acpi PNP0C0A:00: Driver battery requests probe deferral
03/18/15 08:39:03 PM    optimus    kernel    [    1.733013] i915 0000:00:02.0: can't derive routing for PCI INT A
03/18/15 08:39:03 PM    optimus    kernel    [    1.733016] i915 0000:00:02.0: PCI INT A: no GSI
03/18/15 08:39:03 PM    optimus    kernel    [    1.733387] [drm] Memory usable by graphics device = 2048M
03/18/15 08:39:03 PM    optimus    kernel    [    1.733389] checking generic (b0000000 1e0000) vs hw (b0000000 10000000)
03/18/15 08:39:03 PM    optimus    kernel    [    1.733390] fb: switching to inteldrmfb from EFI VGA
03/18/15 08:39:03 PM    optimus    kernel    [    1.733404] Console: switching to colour dummy device 80x25
03/18/15 08:39:03 PM    optimus    kernel    [    1.733452] [drm] Replacing VGA console driver
03/18/15 08:39:03 PM    optimus    kernel    [    1.758329] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
03/18/15 08:39:03 PM    optimus    kernel    [    1.758332] [drm] Driver supports precise vblank timestamp query.
03/18/15 08:39:03 PM    optimus    kernel    [    1.758421] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
03/18/15 08:39:03 PM    optimus    kernel    [    1.820075] fbcon: inteldrmfb (fb0) is primary device
03/18/15 08:39:03 PM    optimus    kernel    [    1.820137] Console: switching to colour frame buffer device 270x90
03/18/15 08:39:03 PM    optimus    kernel    [    1.820177] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
03/18/15 08:39:03 PM    optimus    kernel    [    1.820178] i915 0000:00:02.0: registered panic notifier
03/18/15 08:39:03 PM    optimus    kernel    [    1.820931] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
03/18/15 08:39:03 PM    optimus    kernel    [    1.821030] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input1
03/18/15 08:39:03 PM    optimus    kernel    [    1.821105] [drm] Initialized i915 1.6.0 20141121 for 0000:00:02.0 on minor 0
03/18/15 08:39:03 PM    optimus    kernel    [    1.821135] acpi PNP0C0A:00: Driver battery requests probe deferral
03/18/15 08:39:03 PM    optimus    kernel    [    1.866214] usb 1-3: new full-speed USB device number 2 using xhci_hcd
03/18/15 08:39:03 PM    optimus    kernel    [    1.994621] usb 1-3: No LPM exit latency info found, disabling LPM.
03/18/15 08:39:03 PM    optimus    kernel    [    1.996305] usb 1-3: New USB device found, idVendor=045e, idProduct=07dc
03/18/15 08:39:03 PM    optimus    kernel    [    1.996309] usb 1-3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
03/18/15 08:39:03 PM    optimus    kernel    [    1.996312] usb 1-3: Product: Surface Type Cover
03/18/15 08:39:03 PM    optimus    kernel    [    1.996313] usb 1-3: Manufacturer: Microsoft
03/18/15 08:39:03 PM    optimus    kernel    [    1.996315] usb 1-3: SerialNumber: 031420450654
03/18/15 08:39:03 PM    optimus    kernel    [    1.996958] acpi PNP0C0A:00: Driver battery requests probe deferral
03/18/15 08:39:03 PM    optimus    kernel    [    1.999753] hidraw: raw HID events driver (C) Jiri Kosina
03/18/15 08:39:03 PM    optimus    kernel    [    2.002822] acpi PNP0C0A:00: Driver battery requests probe deferral
03/18/15 08:39:03 PM    optimus    kernel    [    2.002824] usbcore: registered new interface driver usbhid
03/18/15 08:39:03 PM    optimus    kernel    [    2.002826] usbhid: USB HID core driver
03/18/15 08:39:03 PM    optimus    kernel    [    2.005289] input: Microsoft Surface Type Cover as /devices/pci0000:00/0000:00:14.0/usb1/1-3/1-3:1.0/0003:045E:07DC.0001/input/input2
03/18/15 08:39:03 PM    optimus    kernel    [    2.018108] tsc: Refined TSC clocksource calibration: 2294.687 MHz
03/18/15 08:39:03 PM    optimus    kernel    [    2.050105] ata1: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
03/18/15 08:39:03 PM    optimus    kernel    [    2.050751] ata1.00: ATA-8: HFS256G3AMNB-2200A, 10108L00, max UDMA/133
03/18/15 08:39:03 PM    optimus    kernel    [    2.050756] ata1.00: 500118192 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
03/18/15 08:39:03 PM    optimus    kernel    [    2.051416] ata1.00: configured for UDMA/133
03/18/15 08:39:03 PM    optimus    kernel    [    2.051631] scsi 0:0:0:0: Direct-Access     ATA      HFS256G3AMNB-220 8L00 PQ: 0 ANSI: 5
03/18/15 08:39:03 PM    optimus    kernel    [    2.051959] acpi PNP0C0A:00: Driver battery requests probe deferral
03/18/15 08:39:03 PM    optimus    kernel    [    2.052002] sd 0:0:0:0: [sda] 500118192 512-byte logical blocks: (256 GB/238 GiB)
03/18/15 08:39:03 PM    optimus    kernel    [    2.052026] sd 0:0:0:0: Attached scsi generic sg0 type 0
03/18/15 08:39:03 PM    optimus    kernel    [    2.052055] sd 0:0:0:0: [sda] Write Protect is off
03/18/15 08:39:03 PM    optimus    kernel    [    2.052060] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
03/18/15 08:39:03 PM    optimus    kernel    [    2.052076] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
03/18/15 08:39:03 PM    optimus    kernel    [    2.055111]  sda: sda1 sda2 sda3 sda4 sda5 sda6 sda7
03/18/15 08:39:03 PM    optimus    kernel    [    2.056225] sd 0:0:0:0: [sda] Attached SCSI disk
03/18/15 08:39:03 PM    optimus    kernel    [    2.058518] microsoft 0003:045E:07DC.0001: input,hiddev0,hidraw0: USB HID v1.11 Keyboard [Microsoft Surface Type Cover] on usb-0000:00:14.0-3/input0
03/18/15 08:39:03 PM    optimus    kernel    [    2.058675] acpi PNP0C0A:00: Driver battery requests probe deferral
03/18/15 08:39:03 PM    optimus    kernel    [    2.162028] usb 1-7: new high-speed USB device number 3 using xhci_hcd
03/18/15 08:39:03 PM    optimus    kernel    [    2.291760] usb 1-7: New USB device found, idVendor=045e, idProduct=07be
03/18/15 08:39:03 PM    optimus    kernel    [    2.291765] usb 1-7: New USB device strings: Mfr=1, Product=2, SerialNumber=0
03/18/15 08:39:03 PM    optimus    kernel    [    2.291767] usb 1-7: Product: Microsoft LifeCam Front
03/18/15 08:39:03 PM    optimus    kernel    [    2.291769] usb 1-7: Manufacturer: QCM
03/18/15 08:39:03 PM    optimus    kernel    [    2.292536] acpi PNP0C0A:00: Driver battery requests probe deferral
03/18/15 08:39:03 PM    optimus    kernel    [    2.457898] usb 1-8: new high-speed USB device number 4 using xhci_hcd
03/18/15 08:39:03 PM    optimus    kernel    [    2.587648] usb 1-8: New USB device found, idVendor=045e, idProduct=07bf
03/18/15 08:39:03 PM    optimus    kernel    [    2.587653] usb 1-8: New USB device strings: Mfr=1, Product=2, SerialNumber=0
03/18/15 08:39:03 PM    optimus    kernel    [    2.587655] usb 1-8: Product: Microsoft LifeCam Rear
03/18/15 08:39:03 PM    optimus    kernel    [    2.587657] usb 1-8: Manufacturer: QCM
03/18/15 08:39:03 PM    optimus    kernel    [    2.588312] acpi PNP0C0A:00: Driver battery requests probe deferral
03/18/15 08:39:03 PM    optimus    kernel    [    3.017709] Switched to clocksource tsc
03/18/15 08:39:03 PM    optimus    kernel    [    3.456856] EXT4-fs (sda7): mounted filesystem with ordered data mode. Opts: (null)
03/18/15 08:39:03 PM    optimus    kernel    [    3.608646] systemd[1]: Inserted module 'autofs4'
03/18/15 08:39:03 PM    optimus    kernel    [    3.629871] systemd[1]: systemd 219 running in system mode. (+PAM +AUDIT +SELINUX +IMA +APPARMOR +SMACK +SYSVINIT +UTMP +LIBCRYPTSETUP +GCRYPT -GNUTLS +ACL +XZ -LZ4 -SECCOMP +BLKID -ELFUTILS +KMOD -IDN)
03/18/15 08:39:03 PM    optimus    kernel    [    3.630029] systemd[1]: Detected architecture 'x86-64'.
03/18/15 08:39:03 PM    optimus    kernel    [    3.630558] systemd[1]: Set hostname to <optimus>.
03/18/15 08:39:03 PM    optimus    kernel    [    3.687748] systemd[1]: Unit type .busname is not supported on this system.
03/18/15 08:39:03 PM    optimus    kernel    [    3.730970] systemd[1]: Set up automount Arbitrary Executable File Formats File System Automount Point.
03/18/15 08:39:03 PM    optimus    kernel    [    3.730986] systemd[1]: Starting Arbitrary Executable File Formats File System Automount Point.
03/18/15 08:39:03 PM    optimus    kernel    [    3.731033] systemd[1]: Reached target Remote File Systems (Pre).
03/18/15 08:39:03 PM    optimus    kernel    [    3.731042] systemd[1]: Starting Remote File Systems (Pre).
03/18/15 08:39:03 PM    optimus    kernel    [    3.731097] systemd[1]: Created slice Root Slice.
03/18/15 08:39:03 PM    optimus    kernel    [    3.731107] systemd[1]: Starting Root Slice.
03/18/15 08:39:03 PM    optimus    kernel    [    3.731224] systemd[1]: Created slice User and Session Slice.
03/18/15 08:39:03 PM    optimus    kernel    [    3.731234] systemd[1]: Starting User and Session Slice.
03/18/15 08:39:03 PM    optimus    kernel    [    3.731307] systemd[1]: Listening on Journal Socket.
03/18/15 08:39:03 PM    optimus    kernel    [    3.731323] systemd[1]: Starting Journal Socket.
03/18/15 08:39:03 PM    optimus    kernel    [    3.731377] systemd[1]: Listening on fsck to fsckd communication Socket.
03/18/15 08:39:03 PM    optimus    kernel    [    3.731387] systemd[1]: Starting fsck to fsckd communication Socket.
03/18/15 08:39:03 PM    optimus    kernel    [    3.731431] systemd[1]: Listening on Delayed Shutdown Socket.
03/18/15 08:39:03 PM    optimus    kernel    [    3.731440] systemd[1]: Starting Delayed Shutdown Socket.
03/18/15 08:39:03 PM    optimus    kernel    [    3.731495] systemd[1]: Listening on Journal Socket (/dev/log).
03/18/15 08:39:03 PM    optimus    kernel    [    3.731502] systemd[1]: Starting Journal Socket (/dev/log).
03/18/15 08:39:03 PM    optimus    kernel    [    3.731541] systemd[1]: Listening on Syslog Socket.
03/18/15 08:39:03 PM    optimus    kernel    [    3.731548] systemd[1]: Starting Syslog Socket.
03/18/15 08:39:03 PM    optimus    kernel    [    3.731591] systemd[1]: Listening on udev Control Socket.
03/18/15 08:39:03 PM    optimus    kernel    [    3.731598] systemd[1]: Starting udev Control Socket.
03/18/15 08:39:03 PM    optimus    kernel    [    3.731643] systemd[1]: Listening on Journal Audit Socket.
03/18/15 08:39:03 PM    optimus    kernel    [    3.731650] systemd[1]: Starting Journal Audit Socket.
03/18/15 08:39:03 PM    optimus    kernel    [    3.731680] systemd[1]: Started Forward Password Requests to Wall Directory Watch.
03/18/15 08:39:03 PM    optimus    kernel    [    3.731687] systemd[1]: Starting Forward Password Requests to Wall Directory Watch.
03/18/15 08:39:03 PM    optimus    kernel    [    3.731727] systemd[1]: Listening on udev Kernel Socket.
03/18/15 08:39:03 PM    optimus    kernel    [    3.731735] systemd[1]: Starting udev Kernel Socket.
03/18/15 08:39:03 PM    optimus    kernel    [    3.731829] systemd[1]: Created slice System Slice.
03/18/15 08:39:03 PM    optimus    kernel    [    3.731842] systemd[1]: Starting System Slice.
03/18/15 08:39:03 PM    optimus    kernel    [    3.732239] systemd[1]: Starting udev Coldplug all Devices...
03/18/15 08:39:03 PM    optimus    kernel    [    3.732375] systemd[1]: Created slice system-systemd\x2dcryptsetup.slice.
03/18/15 08:39:03 PM    optimus    kernel    [    3.732392] systemd[1]: Starting system-systemd\x2dcryptsetup.slice.
03/18/15 08:39:03 PM    optimus    kernel    [    3.732797] systemd[1]: Starting Journal Service...
03/18/15 08:39:03 PM    optimus    kernel    [    3.733231] systemd[1]: Starting Setup Virtual Console...
03/18/15 08:39:03 PM    optimus    kernel    [    3.733684] systemd[1]: Starting Create list of required static device nodes for the current kernel...
03/18/15 08:39:03 PM    optimus    kernel    [    3.734055] systemd[1]: Mounting Debug File System...
03/18/15 08:39:03 PM    optimus    kernel    [    3.734407] systemd[1]: Starting Nameserver information manager...
03/18/15 08:39:03 PM    optimus    kernel    [    3.738378] systemd[1]: Starting Load Kernel Modules...
03/18/15 08:39:03 PM    optimus    kernel    [    3.739078] systemd[1]: Starting Uncomplicated firewall...
03/18/15 08:39:03 PM    optimus    kernel    [    3.739901] systemd[1]: Started Read required files in advance.
03/18/15 08:39:03 PM    optimus    kernel    [    3.740160] systemd[1]: Starting Read required files in advance...
03/18/15 08:39:03 PM    optimus    kernel    [    3.740304] systemd[1]: Created slice system-getty.slice.
03/18/15 08:39:03 PM    optimus    kernel    [    3.740318] systemd[1]: Starting system-getty.slice.
03/18/15 08:39:03 PM    optimus    kernel    [    3.740638] systemd[1]: Mounting Huge Pages File System...
03/18/15 08:39:03 PM    optimus    kernel    [    3.740993] systemd[1]: Starting File System Check on Root Device...
03/18/15 08:39:03 PM    optimus    kernel    [    3.741057] systemd[1]: Reached target Slices.
03/18/15 08:39:03 PM    optimus    kernel    [    3.741071] systemd[1]: Starting Slices.
03/18/15 08:39:03 PM    optimus    kernel    [    3.741206] systemd[1]: Created slice system-systemd\x2dfsck.slice.
03/18/15 08:39:03 PM    optimus    kernel    [    3.741219] systemd[1]: Starting system-systemd\x2dfsck.slice.
03/18/15 08:39:03 PM    optimus    kernel    [    3.743714] systemd[1]: Started Set Up Additional Binary Formats.
03/18/15 08:39:03 PM    optimus    kernel    [    3.744183] systemd[1]: Mounting POSIX Message Queue File System...
03/18/15 08:39:03 PM    optimus    kernel    [    3.744354] systemd[1]: Listening on /dev/initctl Compatibility Named Pipe.
03/18/15 08:39:03 PM    optimus    kernel    [    3.744371] systemd[1]: Starting /dev/initctl Compatibility Named Pipe.
03/18/15 08:39:03 PM    optimus    kernel    [    3.744920] systemd[1]: Started Setup Virtual Console.
03/18/15 08:39:03 PM    optimus    kernel    [    3.745199] systemd[1]: Started Create list of required static device nodes for the current kernel.
03/18/15 08:39:03 PM    optimus    kernel    [    3.747336] systemd[1]: Starting Create Static Device Nodes in /dev...
03/18/15 08:39:03 PM    optimus    kernel    [    3.750507] systemd[1]: Mounted POSIX Message Queue File System.
03/18/15 08:39:03 PM    optimus    kernel    [    3.754079] systemd[1]: Mounted Huge Pages File System.
03/18/15 08:39:03 PM    optimus    kernel    [    3.754820] systemd[1]: Started Nameserver information manager.
03/18/15 08:39:03 PM    optimus    kernel    [    3.758629] systemd[1]: Mounted Debug File System.
03/18/15 08:39:03 PM    optimus    kernel    [    3.759983] systemd[1]: Started Uncomplicated firewall.
03/18/15 08:39:03 PM    optimus    kernel    [    3.769342] systemd[1]: Started File System Check Daemon to report status.
03/18/15 08:39:03 PM    optimus    kernel    [    3.769520] systemd[1]: Starting File System Check Daemon to report status...
03/18/15 08:39:03 PM    optimus    kernel    [    3.769845] systemd[1]: Started Journal Service.
03/18/15 08:39:03 PM    optimus    kernel    [    3.771730] lp: driver loaded but no devices found
03/18/15 08:39:03 PM    optimus    kernel    [    3.773942] ppdev: user-space parallel port driver
03/18/15 08:39:03 PM    optimus    kernel    [    3.779988] acpi PNP0C0A:00: Driver battery requests probe deferral
03/18/15 08:39:03 PM    optimus    kernel    [    3.780016] acpi PNP0C0A:00: Driver battery requests probe deferral
03/18/15 08:39:03 PM    optimus    kernel    [    3.780074] acpi PNP0C0A:00: Driver battery requests probe deferral
03/18/15 08:39:03 PM    optimus    kernel    [    3.872489] EXT4-fs (sda7): re-mounted. Opts: errors=remount-ro
03/18/15 08:39:03 PM    optimus    kernel    [    3.878726] systemd-journald[233]: Received request to flush runtime journal from PID 1
03/18/15 08:39:03 PM    optimus    kernel    [    3.937840] acpi PNP0C0A:00: Driver battery requests probe deferral
03/18/15 08:39:03 PM    optimus    kernel    [    3.941177] acpi PNP0C0A:00: Driver battery requests probe deferral
03/18/15 08:39:03 PM    optimus    kernel    [    3.941181] dw_dmac INTL9C60:00: can't request region for resource [mem 0x00000000-0x00000fff]
03/18/15 08:39:03 PM    optimus    kernel    [    3.941183] dw_dmac: probe of INTL9C60:00 failed with error -16
03/18/15 08:39:03 PM    optimus    kernel    [    3.983399] acpi PNP0C0A:00: Driver battery requests probe deferral
03/18/15 08:39:03 PM    optimus    kernel    [    4.011232] acpi PNP0C0A:00: Driver battery requests probe deferral
03/18/15 08:39:03 PM    optimus    kernel    [    4.096158] snd_hda_intel 0000:00:03.0: enabling device (0000 -> 0002)
03/18/15 08:39:03 PM    optimus    kernel    [    4.096301] acpi PNP0C0A:00: Driver battery requests probe deferral
03/18/15 08:39:03 PM    optimus    kernel    [    4.096302] snd_hda_intel 0000:00:1b.0: enabling device (0000 -> 0002)
03/18/15 08:39:03 PM    optimus    kernel    [    4.096468] acpi PNP0C0A:00: Driver battery requests probe deferral
03/18/15 08:39:03 PM    optimus    kernel    [    4.111916] sound hdaudioC1D0: autoconfig: line_outs=1 (0x14/0x0/0x0/0x0/0x0) type:speaker
03/18/15 08:39:03 PM    optimus    kernel    [    4.111919] sound hdaudioC1D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
03/18/15 08:39:03 PM    optimus    kernel    [    4.111921] sound hdaudioC1D0:    hp_outs=1 (0x21/0x0/0x0/0x0/0x0)
03/18/15 08:39:03 PM    optimus    kernel    [    4.111922] sound hdaudioC1D0:    mono: mono_out=0x0
03/18/15 08:39:03 PM    optimus    kernel    [    4.111923] sound hdaudioC1D0:    inputs:
03/18/15 08:39:03 PM    optimus    kernel    [    4.111925] sound hdaudioC1D0:      Mic=0x18
03/18/15 08:39:03 PM    optimus    kernel    [    4.111926] sound hdaudioC1D0:      Internal Mic=0x12
03/18/15 08:39:03 PM    optimus    kernel    [    4.117073] input: HDA Intel PCH Mic as /devices/pci0000:00/0000:00:1b.0/sound/card1/input3
03/18/15 08:39:03 PM    optimus    kernel    [    4.117154] input: HDA Intel PCH Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card1/input4
03/18/15 08:39:03 PM    optimus    kernel    [    4.120982] input: HDA Intel HDMI HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:03.0/sound/card0/input5
03/18/15 08:39:03 PM    optimus    kernel    [    4.121031] input: HDA Intel HDMI HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:03.0/sound/card0/input6
03/18/15 08:39:03 PM    optimus    kernel    [    4.121074] input: HDA Intel HDMI HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:03.0/sound/card0/input7
03/18/15 08:39:03 PM    optimus    kernel    [    4.160000] acpi PNP0C0A:00: Driver battery requests probe deferral
03/18/15 08:39:03 PM    optimus    kernel    [    4.161177] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
03/18/15 08:39:03 PM    optimus    kernel    [    4.162692] acpi PNP0C0A:00: Driver battery requests probe deferral
03/18/15 08:39:03 PM    optimus    kernel    [    4.175687] cfg80211: Calling CRDA to update world regulatory domain
03/18/15 08:39:03 PM    optimus    kernel    [    4.183267] mwifiex_pcie 0000:01:00.0: enabling device (0000 -> 0002)
03/18/15 08:39:03 PM    optimus    kernel    [    4.183477] mwifiex: rx work enabled, cpus 4
03/18/15 08:39:03 PM    optimus    kernel    [    4.183582] acpi PNP0C0A:00: Driver battery requests probe deferral
03/18/15 08:39:03 PM    optimus    kernel    [    4.282145] AVX2 version of gcm_enc/dec engaged.
03/18/15 08:39:03 PM    optimus    kernel    [    4.282148] AES CTR mode by8 optimization enabled
03/18/15 08:39:03 PM    optimus    kernel    [    4.298493] mwifiex_pcie 0000:01:00.0: PCI-E is the winner
03/18/15 08:39:03 PM    optimus    kernel    [    4.303304] acpi PNP0C0A:00: Driver battery requests probe deferral
03/18/15 08:39:03 PM    optimus    kernel    [    4.308691] intel_rapl: Found RAPL domain package
03/18/15 08:39:03 PM    optimus    kernel    [    4.308695] intel_rapl: Found RAPL domain core
03/18/15 08:39:03 PM    optimus    kernel    [    4.308697] intel_rapl: Found RAPL domain uncore
03/18/15 08:39:03 PM    optimus    kernel    [    4.308699] intel_rapl: Found RAPL domain dram
03/18/15 08:39:03 PM    optimus    kernel    [    4.722739] random: nonblocking pool is initialized
03/18/15 08:39:03 PM    optimus    kernel    [    4.729748] acpi PNP0C0A:00: Driver battery requests probe deferral
03/18/15 08:39:03 PM    optimus    kernel    [    4.744633] i2c_hid i2c-MSHW0030:00: error in i2c_hid_init_report size:63 / ret_size:0
03/18/15 08:39:03 PM    optimus    kernel    [    4.746456] i2c_hid i2c-MSHW0030:00: error in i2c_hid_init_report size:63 / ret_size:0
03/18/15 08:39:03 PM    optimus    kernel    [    4.748029] i2c_hid i2c-MSHW0030:00: error in i2c_hid_init_report size:19 / ret_size:0
03/18/15 08:39:03 PM    optimus    kernel    [    4.748818] i2c_hid i2c-MSHW0030:00: error in i2c_hid_init_report size:19 / ret_size:0
03/18/15 08:39:03 PM    optimus    kernel    [    4.749862] i2c_hid i2c-MSHW0030:00: error in i2c_hid_init_report size:19 / ret_size:0
03/18/15 08:39:03 PM    optimus    kernel    [    4.750653] i2c_hid i2c-MSHW0030:00: error in i2c_hid_init_report size:19 / ret_size:0
03/18/15 08:39:03 PM    optimus    kernel    [    4.751441] i2c_hid i2c-MSHW0030:00: error in i2c_hid_init_report size:19 / ret_size:0
03/18/15 08:39:03 PM    optimus    kernel    [    4.752237] i2c_hid i2c-MSHW0030:00: error in i2c_hid_init_report size:19 / ret_size:0
03/18/15 08:39:03 PM    optimus    kernel    [    4.753127] i2c_hid i2c-MSHW0030:00: error in i2c_hid_init_report size:19 / ret_size:0
03/18/15 08:39:03 PM    optimus    kernel    [    4.753303] acpi PNP0C0A:00: Driver battery requests probe deferral
03/18/15 08:39:03 PM    optimus    kernel    [    4.763858] acpi PNP0C0A:00: Driver battery requests probe deferral
03/18/15 08:39:03 PM    optimus    kernel    [    4.764130] acpi PNP0C0A:00: Driver battery requests probe deferral
03/18/15 08:39:03 PM    optimus    kernel    [    4.764307] acpi PNP0C0A:00: Driver battery requests probe deferral
03/18/15 08:39:03 PM    optimus    kernel    [    4.764659] acpi PNP0C0A:00: Driver battery requests probe deferral
03/18/15 08:39:03 PM    optimus    kernel    [    4.765160] acpi PNP0C0A:00: Driver battery requests probe deferral
03/18/15 08:39:03 PM    optimus    kernel    [    4.766776] acpi PNP0C0A:00: Driver battery requests probe deferral
03/18/15 08:39:03 PM    optimus    kernel    [    4.801178] i2c_hid i2c-NTRG0001:01: error in i2c_hid_init_report size:9 / ret_size:0
03/18/15 08:39:03 PM    optimus    kernel    [    4.801543] i2c_hid i2c-NTRG0001:01: error in i2c_hid_init_report size:5 / ret_size:0
03/18/15 08:39:03 PM    optimus    kernel    [    4.801927] i2c_hid i2c-NTRG0001:01: error in i2c_hid_init_report size:5 / ret_size:259
03/18/15 08:39:03 PM    optimus    kernel    [    4.802378] i2c_hid i2c-NTRG0001:01: error in i2c_hid_init_report size:8 / ret_size:259
03/18/15 08:39:03 PM    optimus    kernel    [    4.803000] i2c_hid i2c-NTRG0001:01: error in i2c_hid_init_report size:15 / ret_size:259
03/18/15 08:39:03 PM    optimus    kernel    [    4.803677] i2c_hid i2c-NTRG0001:01: error in i2c_hid_init_report size:4 / ret_size:0
03/18/15 08:39:03 PM    optimus    kernel    [    4.811435] i2c_hid i2c-NTRG0001:01: error in i2c_hid_init_report size:63 / ret_size:0
03/18/15 08:39:03 PM    optimus    kernel    [    4.811841] i2c_hid i2c-NTRG0001:01: error in i2c_hid_init_report size:7 / ret_size:0
03/18/15 08:39:03 PM    optimus    kernel    [    4.811963] input: NTRG0001:01 1B96:1B05 Pen as /devices/pci0000:00/INT33C3:00/i2c-10/i2c-NTRG0001:01/0018:1B96:1B05.0003/input/input8
03/18/15 08:39:03 PM    optimus    kernel    [    4.812210] input: NTRG0001:01 1B96:1B05 as /devices/pci0000:00/INT33C3:00/i2c-10/i2c-NTRG0001:01/0018:1B96:1B05.0003/input/input9
03/18/15 08:39:03 PM    optimus    kernel    [    4.812334] hid-multitouch 0018:1B96:1B05.0003: input,hidraw1: <UNKNOWN> HID v1.00 Mouse [NTRG0001:01 1B96:1B05] on 
03/18/15 08:39:03 PM    optimus    kernel    [    4.812367] acpi PNP0C0A:00: Driver battery requests probe deferral
03/18/15 08:39:03 PM    optimus    kernel    [    5.181480] cfg80211: World regulatory domain updated:
03/18/15 08:39:03 PM    optimus    kernel    [    5.181486] cfg80211:  DFS Master region: unset
03/18/15 08:39:03 PM    optimus    kernel    [    5.181488] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
03/18/15 08:39:03 PM    optimus    kernel    [    5.181492] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
03/18/15 08:39:03 PM    optimus    kernel    [    5.181496] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
03/18/15 08:39:03 PM    optimus    kernel    [    5.181499] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm), (N/A)
03/18/15 08:39:03 PM    optimus    kernel    [    5.181502] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
03/18/15 08:39:03 PM    optimus    kernel    [    5.181505] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
03/18/15 08:39:03 PM    optimus    kernel    [    5.297108] audit: type=1400 audit(1426725455.126:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=2054 comm="apparmor_parser"
03/18/15 08:39:03 PM    optimus    kernel    [    5.297117] audit: type=1400 audit(1426725455.126:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=2054 comm="apparmor_parser"
03/18/15 08:39:03 PM    optimus    kernel    [    5.297122] audit: type=1400 audit(1426725455.126:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-helper" pid=2054 comm="apparmor_parser"
03/18/15 08:39:03 PM    optimus    kernel    [    5.297127] audit: type=1400 audit(1426725455.126:5): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=2054 comm="apparmor_parser"
03/18/15 08:39:03 PM    optimus    kernel    [    5.300607] audit: type=1400 audit(1426725455.130:6): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/telepathy/mission-control-5" pid=2054 comm="apparmor_parser"
03/18/15 08:39:03 PM    optimus    kernel    [    5.300618] audit: type=1400 audit(1426725455.130:7): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/telepathy/telepathy-*" pid=2054 comm="apparmor_parser"
03/18/15 08:39:03 PM    optimus    kernel    [    5.300623] audit: type=1400 audit(1426725455.130:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="pxgsettings" pid=2054 comm="apparmor_parser"
03/18/15 08:39:03 PM    optimus    kernel    [    5.300629] audit: type=1400 audit(1426725455.130:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="sanitized_helper" pid=2054 comm="apparmor_parser"
03/18/15 08:39:03 PM    optimus    kernel    [    5.300634] audit: type=1400 audit(1426725455.130:10): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/telepathy/telepathy-ofono" pid=2054 comm="apparmor_parser"
03/18/15 08:39:03 PM    optimus    kernel    [    6.063919] usb 1-6: new high-speed USB device number 5 using xhci_hcd
03/18/15 08:39:03 PM    optimus    kernel    [    6.099968] mwifiex_pcie 0000:01:00.0: WLAN FW is active
03/18/15 08:39:03 PM    optimus    kernel    [    6.193406] usb 1-6: New USB device found, idVendor=1286, idProduct=204b
03/18/15 08:39:03 PM    optimus    kernel    [    6.193414] usb 1-6: New USB device strings: Mfr=1, Product=2, SerialNumber=3
03/18/15 08:39:03 PM    optimus    kernel    [    6.193419] usb 1-6: Product: Bluetooth and Wireless LAN Composite Device
03/18/15 08:39:03 PM    optimus    kernel    [    6.193422] usb 1-6: Manufacturer: Marvell
03/18/15 08:39:03 PM    optimus    kernel    [    6.193426] usb 1-6: SerialNumber: 0000000000000000
03/18/15 08:39:03 PM    optimus    kernel    [    6.195367] ieee80211 phy0: ignoring F/W country code US
03/18/15 08:39:03 PM    optimus    kernel    [    6.195418] acpi PNP0C0A:00: Driver battery requests probe deferral
03/18/15 08:39:03 PM    optimus    kernel    [    6.199309] mwifiex_pcie 0000:01:00.0: driver_version = mwifiex 1.0 (15.68.4.p112) 
03/18/15 08:39:03 PM    optimus    kernel    [    6.218264] Bluetooth: Core ver 2.20
03/18/15 08:39:03 PM    optimus    kernel    [    6.218292] NET: Registered protocol family 31
03/18/15 08:39:03 PM    optimus    kernel    [    6.218295] Bluetooth: HCI device and connection manager initialized
03/18/15 08:39:03 PM    optimus    kernel    [    6.218302] Bluetooth: HCI socket layer initialized
03/18/15 08:39:03 PM    optimus    kernel    [    6.218306] Bluetooth: L2CAP socket layer initialized
03/18/15 08:39:03 PM    optimus    kernel    [    6.218316] Bluetooth: SCO socket layer initialized
03/18/15 08:39:03 PM    optimus    kernel    [    6.221767] acpi PNP0C0A:00: Driver battery requests probe deferral
03/18/15 08:39:03 PM    optimus    kernel    [    6.222369] acpi PNP0C0A:00: Driver battery requests probe deferral
03/18/15 08:39:03 PM    optimus    kernel    [    6.222513] usbcore: registered new interface driver btusb
03/18/15 08:39:03 PM    optimus    kernel    [    6.272272] audit_printk_skb: 60 callbacks suppressed
03/18/15 08:39:03 PM    optimus    kernel    [    6.272284] audit: type=1400 audit(1426725456.102:31): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=2892 comm="apparmor_parser"
03/18/15 08:39:03 PM    optimus    kernel    [    6.272290] audit: type=1400 audit(1426725456.102:32): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=2892 comm="apparmor_parser"
03/18/15 08:39:03 PM    optimus    kernel    [    6.272294] audit: type=1400 audit(1426725456.102:33): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-helper" pid=2892 comm="apparmor_parser"
03/18/15 08:39:03 PM    optimus    kernel    [    6.272297] audit: type=1400 audit(1426725456.102:34): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=2892 comm="apparmor_parser"
03/18/15 08:39:03 PM    optimus    kernel    [    6.274539] audit: type=1400 audit(1426725456.102:35): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/telepathy/mission-control-5" pid=2892 comm="apparmor_parser"
03/18/15 08:39:03 PM    optimus    kernel    [    6.274553] audit: type=1400 audit(1426725456.102:36): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/telepathy/telepathy-*" pid=2892 comm="apparmor_parser"
03/18/15 08:39:03 PM    optimus    kernel    [    6.295880] audit: type=1400 audit(1426725456.126:37): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="pxgsettings" pid=2892 comm="apparmor_parser"
03/18/15 08:39:03 PM    optimus    kernel    [    6.295894] audit: type=1400 audit(1426725456.126:38): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="sanitized_helper" pid=2892 comm="apparmor_parser"
03/18/15 08:39:03 PM    optimus    kernel    [    6.295903] audit: type=1400 audit(1426725456.126:39): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/telepathy/telepathy-ofono" pid=2892 comm="apparmor_parser"
03/18/15 08:39:03 PM    optimus    kernel    [    6.297143] audit: type=1400 audit(1426725456.126:40): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cups-browsed" pid=2892 comm="apparmor_parser"
03/18/15 08:39:03 PM    optimus    kernel    [   93.818055] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
03/18/15 08:39:03 PM    optimus    kernel    [   93.818061] Bluetooth: BNEP filters: protocol multicast
03/18/15 08:39:03 PM    optimus    kernel    [   93.818068] Bluetooth: BNEP socket layer initialized
03/18/15 08:39:03 PM    optimus    kernel    [   93.831571] Bluetooth: RFCOMM TTY layer initialized
03/18/15 08:39:03 PM    optimus    kernel    [   93.831581] Bluetooth: RFCOMM socket layer initialized
03/18/15 08:39:03 PM    optimus    kernel    [   93.831590] Bluetooth: RFCOMM ver 1.11
03/18/15 08:39:03 PM    optimus    rsyslogd-2039    Could no open output pipe '/dev/xconsole': Permission denied [try http://www.rsyslog.com/e/2039 ]
03/18/15 08:39:03 PM    optimus    systemd[1]    Started System Logging Service.
03/18/15 08:39:03 PM    optimus    whoopsie[2986]    [20:39:03] Using lock path: /var/lock/whoopsie/lock
03/18/15 08:39:03 PM    optimus    loadcpufreq[3003]    ...done.
03/18/15 08:39:03 PM    optimus    systemd[1]    Started LSB: Load kernel modules needed to enable cpufreq scaling.
03/18/15 08:39:03 PM    optimus    sensors[3060]    acpitz-virtual-0
03/18/15 08:39:03 PM    optimus    sensors[3060]    Adapter: Virtual device
03/18/15 08:39:03 PM    optimus    sensors[3060]    temp1:       -270.4°C
03/18/15 08:39:03 PM    optimus    sensors[3060]    coretemp-isa-0000
03/18/15 08:39:03 PM    optimus    sensors[3060]    Adapter: ISA adapter
03/18/15 08:39:03 PM    optimus    sensors[3060]    Physical id 0:  +33.0°C  (high = +100.0°C, crit = +100.0°C)
03/18/15 08:39:03 PM    optimus    sensors[3060]    Core 0:         +30.0°C  (high = +100.0°C, crit = +100.0°C)
03/18/15 08:39:03 PM    optimus    sensors[3060]    Core 1:         +33.0°C  (high = +100.0°C, crit = +100.0°C)
03/18/15 08:39:03 PM    optimus    systemd[1]    Started Initialize hardware monitoring sensors.
03/18/15 08:39:03 PM    optimus    systemd[1]    Starting Authenticate and Authorize Users to Run Privileged Tasks...
03/18/15 08:39:03 PM    optimus    systemd[1]    Starting LSB: set CPUFreq kernel parameters...
03/18/15 08:39:03 PM    optimus    systemd[1]    Started Login Service.
03/18/15 08:39:03 PM    optimus    cpufrequtils[3092]    * CPUFreq Utilities: Setting ondemand CPUFreq governor...
03/18/15 08:39:03 PM    optimus    cpufrequtils[3092]    * disabled, governor not available...
03/18/15 08:39:03 PM    optimus    cpufrequtils[3092]    ...done.
03/18/15 08:39:03 PM    optimus    systemd[1]    Started LSB: set CPUFreq kernel parameters.
03/18/15 08:39:03 PM    optimus    polkitd[3091]    started daemon version 0.105 using authority implementation `local' version `0.105'
03/18/15 08:39:03 PM    optimus    dbus[3013]    [system] Successfully activated service 'org.freedesktop.PolicyKit1'
03/18/15 08:39:03 PM    optimus    systemd[1]    Started Authenticate and Authorize Users to Run Privileged Tasks.
03/18/15 08:39:03 PM    optimus    accounts-daemon[2984]    started daemon version 0.6.37
03/18/15 08:39:03 PM    optimus    systemd[1]    Started Accounts Service.
03/18/15 08:39:03 PM    optimus    NetworkManager[2990]    <info> VPN: loaded org.freedesktop.NetworkManager.pptp
03/18/15 08:39:03 PM    optimus    NetworkManager[2990]    <info> DNS: loaded plugin dnsmasq
03/18/15 08:39:03 PM    optimus    dbus[3013]    [system] Activating via systemd: service name='org.freedesktop.NetworkManager' unit='dbus-org.freedesktop.NetworkManager.service'
03/18/15 08:39:03 PM    optimus    systemd[1]    Started Modem Manager.
03/18/15 08:39:03 PM    optimus    NetworkManager[2990]    <info> init!
03/18/15 08:39:03 PM    optimus    NetworkManager[2990]    <info> update_system_hostname
03/18/15 08:39:03 PM    optimus    NetworkManager[2990]    <info>       interface-parser: parsing file /etc/network/interfaces
03/18/15 08:39:03 PM    optimus    NetworkManager[2990]    <info>       interface-parser: finished parsing file /etc/network/interfaces
03/18/15 08:39:03 PM    optimus    NetworkManager[2990]    <info> management mode: unmanaged
03/18/15 08:39:03 PM    optimus    NetworkManager[2990]    <info> devices added (path: /sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/net/mlan0, iface: mlan0)
03/18/15 08:39:03 PM    optimus    NetworkManager[2990]    <info> device added (path: /sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/net/mlan0, iface: mlan0): no ifupdown configuration found.
03/18/15 08:39:03 PM    optimus    NetworkManager[2990]    <info> devices added (path: /sys/devices/virtual/net/lo, iface: lo)
03/18/15 08:39:03 PM    optimus    NetworkManager[2990]    <info> device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
03/18/15 08:39:03 PM    optimus    NetworkManager[2990]    <info> end _init.
03/18/15 08:39:03 PM    optimus    NetworkManager[2990]    <info> Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
03/18/15 08:39:03 PM    optimus    NetworkManager[2990]    (NetworkManager:2990): GLib-CRITICAL **: g_dir_read_name: assertion 'dir != NULL' failed
03/18/15 08:39:03 PM    optimus    NetworkManager[2990]    <info> new connection /etc/NetworkManager/system-connections/gunksta
03/18/15 08:39:03 PM    optimus    NetworkManager[2990]    <info> new connection /etc/NetworkManager/system-connections/kandy
03/18/15 08:39:03 PM    optimus    NetworkManager[2990]    <info> SCPlugin-Ofono: (14014048) ... get_connections.
03/18/15 08:39:03 PM    optimus    NetworkManager[2990]    <info> SCPlugin-Ofono: (14014048) connections count: 0
03/18/15 08:39:03 PM    optimus    NetworkManager[2990]    <info> get unmanaged devices count: 0
03/18/15 08:39:03 PM    optimus    NetworkManager[2990]    <info> monitoring kernel firmware directory '/lib/firmware'.
03/18/15 08:39:03 PM    optimus    NetworkManager[2990]    <info> monitoring ifupdown state file '/run/network/ifstate'.
03/18/15 08:39:03 PM    optimus    NetworkManager[2990]    <info> rfkill0: found WiFi radio killswitch (at /sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0/ieee80211/phy0/rfkill0) (driver mwifiex_pcie)
03/18/15 08:39:03 PM    optimus    NetworkManager[2990]    <info> Loaded device plugin: /usr/lib/x86_64-linux-gnu/NetworkManager/libnm-device-plugin-bluetooth.so
03/18/15 08:39:03 PM    optimus    NetworkManager[2990]    <info> Loaded device plugin: /usr/lib/x86_64-linux-gnu/NetworkManager/libnm-device-plugin-adsl.so
03/18/15 08:39:03 PM    optimus    NetworkManager[2990]    <info> Loaded device plugin: /usr/lib/x86_64-linux-gnu/NetworkManager/libnm-device-plugin-wwan.so
03/18/15 08:39:03 PM    optimus    NetworkManager[2990]    <info> Loaded device plugin: /usr/lib/x86_64-linux-gnu/NetworkManager/libnm-device-plugin-wifi.so
03/18/15 08:39:03 PM    optimus    dbus[3013]    [system] Successfully activated service 'org.freedesktop.NetworkManager'
03/18/15 08:39:03 PM    optimus    NetworkManager[2990]    <info> WiFi enabled by radio killswitch; enabled by state file
03/18/15 08:39:03 PM    optimus    NetworkManager[2990]    <info> WWAN enabled by radio killswitch; enabled by state file
03/18/15 08:39:03 PM    optimus    NetworkManager[2990]    <info> WiMAX enabled by radio killswitch; enabled by state file
03/18/15 08:39:03 PM    optimus    NetworkManager[2990]    <info> Networking is enabled by state file
03/18/15 08:39:03 PM    optimus    NetworkManager[2990]    nm_device_get_device_type: assertion 'NM_IS_DEVICE (self)' failed
03/18/15 08:39:03 PM    optimus    NetworkManager[2990]    <info> (lo): link connected
03/18/15 08:39:03 PM    optimus    NetworkManager[2990]    <info> (lo): carrier is ON
03/18/15 08:39:03 PM    optimus    NetworkManager[2990]    <info> (lo): new Generic device (driver: 'unknown' ifindex: 1)
03/18/15 08:39:03 PM    optimus    NetworkManager[2990]    <info> (lo): exported as /org/freedesktop/NetworkManager/Devices/0
03/18/15 08:39:03 PM    optimus    NetworkManager[2990]    <info> (mlan0): using nl80211 for WiFi device control
03/18/15 08:39:03 PM    optimus    NetworkManager[2990]    <info> (mlan0): driver supports Access Point (AP) mode
03/18/15 08:39:03 PM    optimus    systemd[1]    Starting Network Manager Wait Online...
03/18/15 08:39:03 PM    optimus    systemd[1]    Reached target Network.
03/18/15 08:39:03 PM    optimus    systemd[1]    Starting Network.
03/18/15 08:39:03 PM    optimus    systemd[1]    Starting /etc/rc.local Compatibility...
03/18/15 08:39:03 PM    optimus    NetworkManager[2990]    <info> (mlan0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
03/18/15 08:39:03 PM    optimus    systemd[1]    Started /etc/rc.local Compatibility.
03/18/15 08:39:03 PM    optimus    systemd[1]    Starting Wait for Plymouth Boot Screen to Quit...
03/18/15 08:39:03 PM    optimus    systemd[1]    Starting Terminate Plymouth Boot Screen...
03/18/15 08:39:03 PM    optimus    NetworkManager[2990]    <info> (mlan0): preparing device
03/18/15 08:39:03 PM    optimus    dbus[3013]    [system] Activating via systemd: service name='fi.w1.wpa_supplicant1' unit='wpa_supplicant.service'
03/18/15 08:39:03 PM    optimus    NetworkManager[2990]    <info> urfkill disappeared from the bus
03/18/15 08:39:03 PM    optimus    systemd[1]    Starting WPA supplicant...
03/18/15 08:39:03 PM    optimus    whoopsie[2986]    [20:39:03] offline
03/18/15 08:39:03 PM    optimus    NetworkManager[2990]    <info> use BlueZ version 4
03/18/15 08:39:03 PM    optimus    dbus[3013]    [system] Successfully activated service 'fi.w1.wpa_supplicant1'
03/18/15 08:39:03 PM    optimus    NetworkManager[2990]    <info> wpa_supplicant started
03/18/15 08:39:03 PM    optimus    wpa_supplicant[3111]    Successfully initialized wpa_supplicant
03/18/15 08:39:03 PM    optimus    NetworkManager[2990]    <info> ModemManager available in the bus
03/18/15 08:39:03 PM    optimus    systemd[1]    Started WPA supplicant.
03/18/15 08:39:03 PM    optimus    systemd[1]    Received SIGRTMIN+21 from PID 173 (plymouthd).
03/18/15 08:39:03 PM    optimus    wpa_supplicant[3111]    dbus: wpa_dbus_get_object_properties: failed to get object properties: (none) none
03/18/15 08:39:03 PM    optimus    wpa_supplicant[3111]    dbus: Failed to construct signal
03/18/15 08:39:03 PM    optimus    NetworkManager[2990]    <warn> could not get interface properties: No readable properties in this interface.
03/18/15 08:39:03 PM    optimus    NetworkManager[2990]    <info> (mlan0): supplicant interface state: starting -> ready
03/18/15 08:39:03 PM    optimus    NetworkManager[2990]    <info> (mlan0): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
03/18/15 08:39:03 PM    optimus    NetworkManager[2990]    <warn> could not get interface properties: No readable properties in this interface.
03/18/15 08:39:03 PM    optimus    wpa_supplicant[3111]    mlan0: CTRL-EVENT-SCAN-STARTED
03/18/15 08:39:03 PM    optimus    systemd[1]    Started Wait for Plymouth Boot Screen to Quit.
03/18/15 08:39:03 PM    optimus    systemd[1]    Started Terminate Plymouth Boot Screen.
03/18/15 08:39:03 PM    optimus    systemd[1]    Started Simple Desktop Display Manager.
03/18/15 08:39:03 PM    optimus    systemd[1]    Starting Simple Desktop Display Manager...
03/18/15 08:39:03 PM    optimus    bluetoothd[2982]    Adapter /org/bluez/2982/hci0 has been enabled
03/18/15 08:39:03 PM    optimus    bluetoothd[2982]    bluetoothd[2982]: Adapter /org/bluez/2982/hci0 has been enabled
03/18/15 08:39:04 PM    optimus    systemd[1]    Created slice user-115.slice.
03/18/15 08:39:04 PM    optimus    systemd[1]    Starting user-115.slice.
03/18/15 08:39:04 PM    optimus    systemd[1]    Starting User Manager for UID 115...
03/18/15 08:39:04 PM    optimus    systemd[1]    Started Session 1 of user sddm.
03/18/15 08:39:04 PM    optimus    systemd[1]    Starting Session 1 of user sddm.
03/18/15 08:39:04 PM    optimus    systemd[3123]    Unit type .busname is not supported on this system.
03/18/15 08:39:04 PM    optimus    systemd[3123]    Reached target Sockets.
03/18/15 08:39:04 PM    optimus    systemd[3123]    Starting Sockets.
03/18/15 08:39:04 PM    optimus    systemd[3123]    Reached target Timers.
03/18/15 08:39:04 PM    optimus    systemd[3123]    Starting Timers.
03/18/15 08:39:04 PM    optimus    systemd[3123]    Reached target Paths.
03/18/15 08:39:04 PM    optimus    systemd[3123]    Starting Paths.
03/18/15 08:39:04 PM    optimus    systemd[3123]    Reached target Basic System.
03/18/15 08:39:04 PM    optimus    systemd[3123]    Starting Basic System.
03/18/15 08:39:04 PM    optimus    systemd[3123]    Reached target Default.
03/18/15 08:39:04 PM    optimus    systemd[3123]    Startup finished in 6ms.
03/18/15 08:39:04 PM    optimus    systemd[3123]    Starting Default.
03/18/15 08:39:04 PM    optimus    systemd[1]    Started User Manager for UID 115.
03/18/15 08:39:04 PM    optimus    org.kde.kded5[3134]    Qt: Session management error: networkIdsList argument is NULL
03/18/15 08:39:04 PM    optimus    org.kde.kded5[3134]    klauncher not running... launching kdeinit
03/18/15 08:39:04 PM    optimus    org.kde.kded5[3134]    kdeinit5: preparing to launch 'libkdeinit5_klauncher'
03/18/15 08:39:04 PM    optimus    org.kde.kded5[3134]    kdeinit5: Launched KLauncher, pid = 3142, result = 0
03/18/15 08:39:04 PM    optimus    org.kde.kded5[3134]    Qt: Session management error: networkIdsList argument is NULL
03/18/15 08:39:04 PM    optimus    org.kde.kded5[3134]    Connecting to deprecated signal QDBusConnectionInterface::serviceOwnerChanged(QString,QString,QString)
03/18/15 08:39:04 PM    optimus    org.kde.kded5[3134]    kdeinit5: opened connection to :0
03/18/15 08:39:04 PM    optimus    org.kde.kded5[3134]    kdeinit5: Got EXT_EXEC '/usr/bin/kbuildsycoca5' from launcher.
03/18/15 08:39:04 PM    optimus    org.kde.kded5[3134]    kdeinit5: preparing to launch '/usr/bin/kbuildsycoca5'
03/18/15 08:39:04 PM    optimus    org.kde.kded5[3134]    kf5.kinit.klauncher: "/usr/bin/kbuildsycoca5" (pid 3144) up and running.
03/18/15 08:39:04 PM    optimus    org.kde.kded5[3134]    kbuildsycoca5 running...
03/18/15 08:39:04 PM    optimus    org.kde.kded5[3134]    kf5.kservice.sycoca: Trying to open ksycoca from "/var/lib/sddm/.cache/ksycoca5"
03/18/15 08:39:04 PM    optimus    org.kde.kded5[3134]    checking file timestamps
03/18/15 08:39:04 PM    optimus    org.kde.kded5[3134]    timestamps check ok
03/18/15 08:39:04 PM    optimus    org.kde.kded5[3134]    Emitting notifyDatabaseChanged ()
03/18/15 08:39:04 PM    optimus    org.kde.kded5[3134]    kdeinit5: PID 3144 terminated.
03/18/15 08:39:04 PM    optimus    org.kde.kded5[3134]    kf5.kservice.sycoca: Trying to open ksycoca from "/var/lib/sddm/.cache/ksycoca5"
03/18/15 08:39:04 PM    optimus    org.kde.kded5[3134]    kf5.kded: kded module "kcookiejar" still uses .desktop files ("kded/kcookiejar.desktop"). Please port it to JSON metadata.
03/18/15 08:39:04 PM    optimus    org.kde.kded5[3134]    kf5.kded: kded module "ktouchpadenabler" still uses .desktop files ("kded/ktouchpadenabler.desktop"). Please port it to JSON metadata.
03/18/15 08:39:04 PM    optimus    org.kde.kded5[3134]    kf5.kded: kded module "khotkeys" still uses .desktop files ("kded/khotkeys.desktop"). Please port it to JSON metadata.
03/18/15 08:39:04 PM    optimus    org.kde.kded5[3134]    kf5.kded: kded module "kscreen" still uses .desktop files ("kded/kscreen.desktop"). Please port it to JSON metadata.
03/18/15 08:39:04 PM    optimus    org.kde.kded5[3134]    kf5.kded: kded module "keyboard" still uses .desktop files ("kded/keyboard.desktop"). Please port it to JSON metadata.
03/18/15 08:39:04 PM    optimus    org.kde.kded5[3134]    kf5.kded: kded module "proxyscout" still uses .desktop files ("kded/proxyscout.desktop"). Please port it to JSON metadata.
03/18/15 08:39:04 PM    optimus    org.kde.kded5[3134]    kf5.kded: kded module "platformstatus" still uses .desktop files ("kded/platformstatus.desktop"). Please port it to JSON metadata.
03/18/15 08:39:04 PM    optimus    org.kde.kded5[3134]    kf5.kded: kded module "appmenu" still uses .desktop files ("kded/appmenu.desktop"). Please port it to JSON metadata.
03/18/15 08:39:04 PM    optimus    org.kde.kded5[3134]    kf5.kded: kded module "touchpad" still uses .desktop files ("kded/touchpad.desktop"). Please port it to JSON metadata.
03/18/15 08:39:04 PM    optimus    org.kde.kded5[3134]    kf5.kded: kded module "ktimezoned" still uses .desktop files ("kded/ktimezoned.desktop"). Please port it to JSON metadata.
03/18/15 08:39:04 PM    optimus    org.kde.kded5[3134]    kf5.kded: kded module "statusnotifierwatcher" still uses .desktop files ("kded/statusnotifierwatcher.desktop"). Please port it to JSON metadata.
03/18/15 08:39:04 PM    optimus    org.kde.kded5[3134]    kf5.kded: kded module "kpasswdserver" still uses .desktop files ("kded/kpasswdserver.desktop"). Please port it to JSON metadata.
03/18/15 08:39:04 PM    optimus    org.kde.kded5[3134]    kf5.kded: kded module "printmanager" still uses .desktop files ("kded/printmanager.desktop"). Please port it to JSON metadata.
03/18/15 08:39:04 PM    optimus    org.kde.kded5[3134]    kf5.kded: kded module "powerdevil" still uses .desktop files ("kded/powerdevil.desktop"). Please port it to JSON metadata.
03/18/15 08:39:04 PM    optimus    org.kde.kded5[3134]    kf5.kded: kded module "remotedirnotify" still uses .desktop files ("kded/remotedirnotify.desktop"). Please port it to JSON metadata.
03/18/15 08:39:04 PM    optimus    org.kde.kded5[3134]    kf5.kded: kded module "notificationhelper" still uses .desktop files ("kded/notificationhelper.desktop"). Please port it to JSON metadata.
03/18/15 08:39:04 PM    optimus    org.kde.kded5[3134]    kf5.kded: kded module "recentdocumentsnotifier" still uses .desktop files ("kded/recentdocumentsnotifier.desktop"). Please port it to JSON metadata.
03/18/15 08:39:04 PM    optimus    org.kde.kded5[3134]    kf5.kded: kded module "networkwatcher" still uses .desktop files ("kded/networkwatcher.desktop"). Please port it to JSON metadata.
03/18/15 08:39:04 PM    optimus    org.kde.kded5[3134]    kf5.kded: kded module "ksysguard" still uses .desktop files ("kded/ksysguard.desktop"). Please port it to JSON metadata.
03/18/15 08:39:04 PM    optimus    org.kde.kded5[3134]    kf5.kded: kded module "solidautoeject" still uses .desktop files ("kded/solidautoeject.desktop"). Please port it to JSON metadata.
03/18/15 08:39:04 PM    optimus    org.kde.kded5[3134]    kf5.kded: kded module "networkstatus" still uses .desktop files ("kded/networkstatus.desktop"). Please port it to JSON metadata.
03/18/15 08:39:04 PM    optimus    org.kde.kded5[3134]    kf5.kded: kded module "desktopnotifier" still uses .desktop files ("kded/desktopnotifier.desktop"). Please port it to JSON metadata.
03/18/15 08:39:04 PM    optimus    org.kde.kded5[3134]    kf5.kded: kded module "soliduiserver" still uses .desktop files ("kded/soliduiserver.desktop"). Please port it to JSON metadata.
03/18/15 08:39:04 PM    optimus    org.kde.kded5[3134]    kf5.kded: kded module "networkmanagement" still uses .desktop files ("kded/networkmanagement.desktop"). Please port it to JSON metadata.
03/18/15 08:39:04 PM    optimus    org.kde.kded5[3134]    kf5.kded: kded module "freespacenotifier" still uses .desktop files ("kded/freespacenotifier.desktop"). Please port it to JSON metadata.
03/18/15 08:39:04 PM    optimus    org.kde.kded5[3134]    kf5.kded: kded module "kded_baloosearch_kio" still uses .desktop files ("kded/baloosearchfolderupdater.desktop"). Please port it to JSON metadata.
03/18/15 08:39:04 PM    optimus    org.kde.kded5[3134]    kf5.kservice.sycoca: Trying to open ksycoca from "/var/lib/sddm/.cache/ksycoca5"
03/18/15 08:39:04 PM    optimus    org.kde.kded5[3134]    kdeinit5: Got EXEC_NEW '/usr/lib/x86_64-linux-gnu/libexec/kf5/kconf_update' from launcher.
03/18/15 08:39:04 PM    optimus    org.kde.kded5[3134]    kdeinit5: preparing to launch '/usr/lib/x86_64-linux-gnu/libexec/kf5/kconf_update'
03/18/15 08:39:04 PM    optimus    org.kde.kded5[3134]    kf5.kinit.klauncher: "/usr/lib/x86_64-linux-gnu/libexec/kf5/kconf_update" (pid 3145) up and running.
03/18/15 08:39:04 PM    optimus    org.kde.kded5[3134]    kdeinit5: PID 3145 terminated.
03/18/15 08:39:04 PM    optimus    org.kde.kded5[3134]    kdeinit5: Got EXT_EXEC '/usr/bin/kbuildsycoca5' from launcher.
03/18/15 08:39:04 PM    optimus    org.kde.kded5[3134]    kdeinit5: preparing to launch '/usr/bin/kbuildsycoca5'
03/18/15 08:39:04 PM    optimus    org.kde.kded5[3134]    kf5.kinit.klauncher: "/usr/bin/kbuildsycoca5" (pid 3146) up and running.
03/18/15 08:39:04 PM    optimus    org.kde.kded5[3134]    kbuildsycoca5 running...
03/18/15 08:39:04 PM    optimus    org.kde.kded5[3134]    kf5.kservice.sycoca: Trying to open ksycoca from "/var/lib/sddm/.cache/ksycoca5"
03/18/15 08:39:04 PM    optimus    org.kde.kded5[3134]    Reusing existing ksycoca
03/18/15 08:39:04 PM    optimus    org.kde.kded5[3134]    Recreating ksycoca file ("/var/lib/sddm/.cache/ksycoca5", version 300)
03/18/15 08:39:05 PM    optimus    org.kde.kded5[3134]    Still in the time dict (i.e. deleted files) ("apps")
03/18/15 08:39:05 PM    optimus    org.kde.kded5[3134]    Menu "applications-kmenuedit.menu" not found.
03/18/15 08:39:05 PM    optimus    org.kde.kded5[3134]    Saving
03/18/15 08:39:05 PM    optimus    org.kde.kded5[3134]    Emitting notifyDatabaseChanged ("apps")
03/18/15 08:39:05 PM    optimus    org.kde.kded5[3134]    kdeinit5: PID 3146 terminated.
03/18/15 08:39:05 PM    optimus    org.kde.kded5[3134]    kf5.kservice.sycoca: Trying to open ksycoca from "/var/lib/sddm/.cache/ksycoca5"
03/18/15 08:39:05 PM    optimus    org.kde.kded5[3134]    kf5.kded: kded module "soliduiserver" still uses .desktop files ("kded/soliduiserver.desktop"). Please port it to JSON metadata.
03/18/15 08:39:05 PM    optimus    org.kde.kded5[3134]    kf5.kded: kded module "powerdevil" still uses .desktop files ("kded/powerdevil.desktop"). Please port it to JSON metadata.
03/18/15 08:39:05 PM    optimus    org.kde.kded5[3134]    kf5.kded: kded module "ksysguard" still uses .desktop files ("kded/ksysguard.desktop"). Please port it to JSON metadata.
03/18/15 08:39:05 PM    optimus    org.kde.kded5[3134]    kf5.kded: kded module "statusnotifierwatcher" still uses .desktop files ("kded/statusnotifierwatcher.desktop"). Please port it to JSON metadata.
03/18/15 08:39:05 PM    optimus    org.kde.kded5[3134]    kf5.kded: kded module "networkstatus" still uses .desktop files ("kded/networkstatus.desktop"). Please port it to JSON metadata.
03/18/15 08:39:05 PM    optimus    org.kde.kded5[3134]    kf5.kded: kded module "khotkeys" still uses .desktop files ("kded/khotkeys.desktop"). Please port it to JSON metadata.
03/18/15 08:39:05 PM    optimus    org.kde.kded5[3134]    kf5.kded: kded module "proxyscout" still uses .desktop files ("kded/proxyscout.desktop"). Please port it to JSON metadata.
03/18/15 08:39:05 PM    optimus    org.kde.kded5[3134]    kf5.kded: kded module "networkmanagement" still uses .desktop files ("kded/networkmanagement.desktop"). Please port it to JSON metadata.
03/18/15 08:39:05 PM    optimus    org.kde.kded5[3134]    kf5.kded: kded module "printmanager" still uses .desktop files ("kded/printmanager.desktop"). Please port it to JSON metadata.
03/18/15 08:39:05 PM    optimus    org.kde.kded5[3134]    kf5.kded: kded module "networkwatcher" still uses .desktop files ("kded/networkwatcher.desktop"). Please port it to JSON metadata.
03/18/15 08:39:05 PM    optimus    org.kde.kded5[3134]    kf5.kded: kded module "ktimezoned" still uses .desktop files ("kded/ktimezoned.desktop"). Please port it to JSON metadata.
03/18/15 08:39:05 PM    optimus    org.kde.kded5[3134]    kf5.kded: kded module "platformstatus" still uses .desktop files ("kded/platformstatus.desktop"). Please port it to JSON metadata.
03/18/15 08:39:05 PM    optimus    org.kde.kded5[3134]    kf5.kded: kded module "desktopnotifier" still uses .desktop files ("kded/desktopnotifier.desktop"). Please port it to JSON metadata.
03/18/15 08:39:05 PM    optimus    org.kde.kded5[3134]    kf5.kded: kded module "remotedirnotify" still uses .desktop files ("kded/remotedirnotify.desktop"). Please port it to JSON metadata.
03/18/15 08:39:05 PM    optimus    org.kde.kded5[3134]    kf5.kded: kded module "notificationhelper" still uses .desktop files ("kded/notificationhelper.desktop"). Please port it to JSON metadata.
03/18/15 08:39:05 PM    optimus    org.kde.kded5[3134]    kf5.kded: kded module "freespacenotifier" still uses .desktop files ("kded/freespacenotifier.desktop"). Please port it to JSON metadata.
03/18/15 08:39:05 PM    optimus    org.kde.kded5[3134]    kf5.kded: kded module "touchpad" still uses .desktop files ("kded/touchpad.desktop"). Please port it to JSON metadata.
03/18/15 08:39:05 PM    optimus    org.kde.kded5[3134]    kf5.kded: kded module "solidautoeject" still uses .desktop files ("kded/solidautoeject.desktop"). Please port it to JSON metadata.
03/18/15 08:39:05 PM    optimus    org.kde.kded5[3134]    kf5.kded: kded module "recentdocumentsnotifier" still uses .desktop files ("kded/recentdocumentsnotifier.desktop"). Please port it to JSON metadata.
03/18/15 08:39:05 PM    optimus    org.kde.kded5[3134]    kf5.kded: kded module "keyboard" still uses .desktop files ("kded/keyboard.desktop"). Please port it to JSON metadata.
03/18/15 08:39:05 PM    optimus    org.kde.kded5[3134]    kf5.kded: kded module "kpasswdserver" still uses .desktop files ("kded/kpasswdserver.desktop"). Please port it to JSON metadata.
03/18/15 08:39:05 PM    optimus    org.kde.kded5[3134]    kf5.kded: kded module "ktouchpadenabler" still uses .desktop files ("kded/ktouchpadenabler.desktop"). Please port it to JSON metadata.
03/18/15 08:39:05 PM    optimus    org.kde.kded5[3134]    kf5.kded: kded module "appmenu" still uses .desktop files ("kded/appmenu.desktop"). Please port it to JSON metadata.
03/18/15 08:39:05 PM    optimus    org.kde.kded5[3134]    kf5.kded: kded module "kded_baloosearch_kio" still uses .desktop files ("kded/baloosearchfolderupdater.desktop"). Please port it to JSON metadata.
03/18/15 08:39:05 PM    optimus    org.kde.kded5[3134]    kf5.kded: kded module "kcookiejar" still uses .desktop files ("kded/kcookiejar.desktop"). Please port it to JSON metadata.
03/18/15 08:39:05 PM    optimus    org.kde.kded5[3134]    kf5.kded: kded module "kscreen" still uses .desktop files ("kded/kscreen.desktop"). Please port it to JSON metadata.
03/18/15 08:39:05 PM    optimus    dbus[3013]    [system] Activating via systemd: service name='org.freedesktop.UDisks2' unit='udisks2.service'
03/18/15 08:39:05 PM    optimus    systemd[1]    Starting Disk Manager...
03/18/15 08:39:05 PM    optimus    udisksd[3147]    udisks daemon version 2.1.5 starting
03/18/15 08:39:05 PM    optimus    dbus[3013]    [system] Successfully activated service 'org.freedesktop.UDisks2'
03/18/15 08:39:05 PM    optimus    udisksd[3147]    Acquired the name org.freedesktop.UDisks2 on the system message bus
03/18/15 08:39:05 PM    optimus    systemd[1]    Started Disk Manager.
03/18/15 08:39:05 PM    optimus    dbus[3013]    [system] Activating via systemd: service name='org.freedesktop.UPower' unit='upower.service'
03/18/15 08:39:05 PM    optimus    systemd[1]    Starting Daemon for power management...
03/18/15 08:39:05 PM    optimus    dbus[3013]    [system] Successfully activated service 'org.freedesktop.UPower'
03/18/15 08:39:05 PM    optimus    systemd[1]    Started Daemon for power management.
03/18/15 08:39:05 PM    optimus    ModemManager[2995]    <warn>  Couldn't find support for device at '/sys/devices/pci0000:00/0000:00:1c.0/0000:01:00.0': not supported by any plugin
03/18/15 08:39:06 PM    optimus    NetworkManager[2990]    <info> Auto-activating connection 'kandy'.
03/18/15 08:39:06 PM    optimus    NetworkManager[2990]    <info> Activation (mlan0) starting connection 'kandy'
03/18/15 08:39:06 PM    optimus    NetworkManager[2990]    <info> Activation (mlan0) Stage 1 of 5 (Device Prepare) scheduled...
03/18/15 08:39:06 PM    optimus    NetworkManager[2990]    <info> Activation (mlan0) Stage 1 of 5 (Device Prepare) started...
03/18/15 08:39:06 PM    optimus    NetworkManager[2990]    <info> (mlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
03/18/15 08:39:06 PM    optimus    NetworkManager[2990]    <info> NetworkManager state is now CONNECTING
03/18/15 08:39:06 PM    optimus    NetworkManager[2990]    <info> Activation (mlan0) Stage 2 of 5 (Device Configure) scheduled...
03/18/15 08:39:06 PM    optimus    NetworkManager[2990]    <info> Activation (mlan0) Stage 1 of 5 (Device Prepare) complete.
03/18/15 08:39:06 PM    optimus    NetworkManager[2990]    <info> Activation (mlan0) Stage 2 of 5 (Device Configure) starting...
03/18/15 08:39:06 PM    optimus    NetworkManager[2990]    <info> (mlan0): device state change: prepare -> config (reason 'none') [40 50 0]
03/18/15 08:39:06 PM    optimus    NetworkManager[2990]    <info> Activation (mlan0/wireless): connection 'kandy' has security, and secrets exist.  No new secrets needed.
03/18/15 08:39:06 PM    optimus    NetworkManager[2990]    <info> Config: added 'ssid' value 'kandy'
03/18/15 08:39:06 PM    optimus    NetworkManager[2990]    <info> Config: added 'scan_ssid' value '1'
03/18/15 08:39:06 PM    optimus    NetworkManager[2990]    <info> Config: added 'key_mgmt' value 'WPA-PSK'
03/18/15 08:39:06 PM    optimus    NetworkManager[2990]    <info> Config: added 'auth_alg' value 'OPEN'
03/18/15 08:39:06 PM    optimus    NetworkManager[2990]    <info> Config: added 'psk' value '<omitted>'
03/18/15 08:39:06 PM    optimus    NetworkManager[2990]    <info> Activation (mlan0) Stage 2 of 5 (Device Configure) complete.
03/18/15 08:39:06 PM    optimus    NetworkManager[2990]    <info> (mlan0): supplicant interface state: ready -> inactive
03/18/15 08:39:06 PM    optimus    NetworkManager[2990]    <info> Config: set interface ap_scan to 1
03/18/15 08:39:06 PM    optimus    wpa_supplicant[3111]    mlan0: Trying to associate with 08:86:3b:8a:11:dc (SSID='kandy' freq=2437 MHz)
03/18/15 08:39:06 PM    optimus    wpa_supplicant[3111]    mlan0: Associated with 08:86:3b:8a:11:dc
03/18/15 08:39:06 PM    optimus    NetworkManager[2990]    <info> (mlan0): supplicant interface state: inactive -> associating
03/18/15 08:39:06 PM    optimus    kernel    [   96.194285] cfg80211: Calling CRDA for country: TW
03/18/15 08:39:06 PM    optimus    kernel    [   96.196147] cfg80211: Regulatory domain changed to country: TW
03/18/15 08:39:06 PM    optimus    kernel    [   96.196149] cfg80211:  DFS Master region: unset
03/18/15 08:39:06 PM    optimus    kernel    [   96.196150] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
03/18/15 08:39:06 PM    optimus    kernel    [   96.196151] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm), (N/A)
03/18/15 08:39:06 PM    optimus    kernel    [   96.196152] cfg80211:   (5270000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 1700 mBm), (0 s)
03/18/15 08:39:06 PM    optimus    kernel    [   96.196153] cfg80211:   (5735000 KHz - 5815000 KHz @ 40000 KHz), (300 mBi, 3000 mBm), (N/A)
03/18/15 08:39:06 PM    optimus    NetworkManager[2990]    <info> (mlan0): supplicant interface state: associating -> associated
03/18/15 08:39:07 PM    optimus    NetworkManager[2990]    <info> (mlan0): supplicant interface state: associated -> 4-way handshake
03/18/15 08:39:07 PM    optimus    wpa_supplicant[3111]    mlan0: WPA: Key negotiation completed with 08:86:3b:8a:11:dc [PTK=CCMP GTK=CCMP]
03/18/15 08:39:07 PM    optimus    wpa_supplicant[3111]    mlan0: CTRL-EVENT-CONNECTED - Connection to 08:86:3b:8a:11:dc completed [id=0 id_str=]
03/18/15 08:39:07 PM    optimus    NetworkManager[2990]    <info> (mlan0): supplicant interface state: 4-way handshake -> completed
03/18/15 08:39:07 PM    optimus    NetworkManager[2990]    <info> Activation (mlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'kandy'.
03/18/15 08:39:07 PM    optimus    NetworkManager[2990]    <info> Activation (mlan0) Stage 3 of 5 (IP Configure Start) scheduled.
03/18/15 08:39:07 PM    optimus    NetworkManager[2990]    <info> Activation (mlan0) Stage 3 of 5 (IP Configure Start) started...
03/18/15 08:39:07 PM    optimus    NetworkManager[2990]    <info> (mlan0): device state change: config -> ip-config (reason 'none') [50 70 0]
03/18/15 08:39:07 PM    optimus    NetworkManager[2990]    <info> Activation (mlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
03/18/15 08:39:07 PM    optimus    NetworkManager[2990]    <info> dhclient started with pid 3176
03/18/15 08:39:07 PM    optimus    NetworkManager[2990]    <info> Activation (mlan0) Stage 3 of 5 (IP Configure Start) complete.
03/18/15 08:39:07 PM    optimus    NetworkManager[2990]    <info> (mlan0): DHCPv4 state changed nbi -> preinit
03/18/15 08:39:07 PM    optimus    dhclient    DHCPDISCOVER on mlan0 to 255.255.255.255 port 67 interval 3 (xid=0x513bf916)
03/18/15 08:39:07 PM    optimus    dhclient    DHCPREQUEST of 192.168.2.12 on mlan0 to 255.255.255.255 port 67 (xid=0x513bf916)
03/18/15 08:39:07 PM    optimus    dhclient    DHCPOFFER of 192.168.2.12 from 192.168.2.1
03/18/15 08:39:07 PM    optimus    dhclient    DHCPACK of 192.168.2.12 from 192.168.2.1
03/18/15 08:39:07 PM    optimus    NetworkManager[2990]    <info> (mlan0): DHCPv4 state changed preinit -> bound
03/18/15 08:39:07 PM    optimus    NetworkManager[2990]    <info>   address 192.168.2.12
03/18/15 08:39:07 PM    optimus    NetworkManager[2990]    <info>   plen 24 (255.255.255.0)
03/18/15 08:39:07 PM    optimus    NetworkManager[2990]    <info>   gateway 192.168.2.1
03/18/15 08:39:07 PM    optimus    NetworkManager[2990]    <info>   server identifier 192.168.2.1
03/18/15 08:39:07 PM    optimus    NetworkManager[2990]    <info>   lease time -1
03/18/15 08:39:07 PM    optimus    NetworkManager[2990]    <info>   nameserver '192.168.2.1'
03/18/15 08:39:07 PM    optimus    NetworkManager[2990]    <info>   domain name 'Belkin'
03/18/15 08:39:07 PM    optimus    NetworkManager[2990]    <info> Activation (mlan0) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
03/18/15 08:39:07 PM    optimus    NetworkManager[2990]    <info> Activation (mlan0) Stage 5 of 5 (IPv4 Commit) started...
03/18/15 08:39:07 PM    optimus    avahi-daemon[3012]    Joining mDNS multicast group on interface mlan0.IPv4 with address 192.168.2.12.
03/18/15 08:39:07 PM    optimus    avahi-daemon[3012]    New relevant interface mlan0.IPv4 for mDNS.
03/18/15 08:39:07 PM    optimus    avahi-daemon[3012]    Registering new address record for 192.168.2.12 on mlan0.IPv4.
03/18/15 08:39:07 PM    optimus    NetworkManager[2990]    <info> (mlan0): device state change: ip-config -> ip-check (reason 'none') [70 80 0]
03/18/15 08:39:07 PM    optimus    NetworkManager[2990]    <info> Activation (mlan0) Stage 5 of 5 (IPv4 Commit) complete.
03/18/15 08:39:07 PM    optimus    NetworkManager[2990]    <info> (mlan0): device state change: ip-check -> secondaries (reason 'none') [80 90 0]
03/18/15 08:39:07 PM    optimus    NetworkManager[2990]    <info> (mlan0): device state change: secondaries -> activated (reason 'none') [90 100 0]
03/18/15 08:39:07 PM    optimus    NetworkManager[2990]    <info> NetworkManager state is now CONNECTED_LOCAL
03/18/15 08:39:07 PM    optimus    dhclient    bound to 192.168.2.12 -- renewal in 2147483648 seconds.
03/18/15 08:39:07 PM    optimus    NetworkManager[2990]    <info> NetworkManager state is now CONNECTED_GLOBAL
03/18/15 08:39:07 PM    optimus    NetworkManager[2990]    <info> Policy set 'kandy' (mlan0) as default for IPv4 routing and DNS.
03/18/15 08:39:07 PM    optimus    NetworkManager[2990]    <info> DNS: starting dnsmasq...
03/18/15 08:39:07 PM    optimus    NetworkManager[2990]    <warn> dnsmasq not available on the bus, can't update servers.
03/18/15 08:39:07 PM    optimus    NetworkManager[2990]    <error> [1426725547.210767] [dns-manager/nm-dns-dnsmasq.c:398] update(): dnsmasq owner not found on bus: Could not get owner of name 'org.freedesktop.NetworkManager.dnsmasq': no such name
03/18/15 08:39:07 PM    optimus    NetworkManager[2990]    <warn> DNS: plugin dnsmasq update failed
03/18/15 08:39:07 PM    optimus    NetworkManager[2990]    <info> Writing DNS information to /sbin/resolvconf
03/18/15 08:39:07 PM    optimus    whoopsie[2986]    [20:39:07] Cannot reach: https://daisy.ubuntu.com
03/18/15 08:39:07 PM    optimus    dnsmasq[3179]    started, version 2.72 cache disabled
03/18/15 08:39:07 PM    optimus    dnsmasq[3179]    compile time options: IPv6 GNU-getopt DBus i18n IDN DHCP DHCPv6 no-Lua TFTP conntrack ipset auth DNSSEC loop-detect
03/18/15 08:39:07 PM    optimus    dnsmasq[3179]    DBus support enabled: connected to system bus
03/18/15 08:39:07 PM    optimus    dnsmasq[3179]    warning: no upstream servers configured
03/18/15 08:39:07 PM    optimus    avahi-daemon[3012]    Joining mDNS multicast group on interface mlan0.IPv6 with address fe80::c233:5eff:fe10:cbd1.
03/18/15 08:39:07 PM    optimus    avahi-daemon[3012]    New relevant interface mlan0.IPv6 for mDNS.
03/18/15 08:39:07 PM    optimus    avahi-daemon[3012]    Registering new address record for fe80::c233:5eff:fe10:cbd1 on mlan0.*.
03/18/15 08:39:07 PM    optimus    kernel    [   97.570293] IPv6: mlan0: IPv6 duplicate address fe80::c233:5eff:fe10:cbd1 detected!
03/18/15 08:39:07 PM    optimus    NetworkManager[2990]    <info> Activation (mlan0) successful, device activated.
03/18/15 08:39:07 PM    optimus    NetworkManager[2990]    <info> startup complete
03/18/15 08:39:07 PM    optimus    dbus[3013]    [system] Activating via systemd: service name='org.freedesktop.nm_dispatcher' unit='dbus-org.freedesktop.nm-dispatcher.service'
03/18/15 08:39:07 PM    optimus    systemd[1]    Started Network Manager Wait Online.
03/18/15 08:39:07 PM    optimus    systemd[1]    Reached target Network is Online.
03/18/15 08:39:07 PM    optimus    systemd[1]    Starting Network is Online.
03/18/15 08:39:07 PM    optimus    NetworkManager[2990]    <warn> dnsmasq appeared on DBus: :1.22
03/18/15 08:39:07 PM    optimus    systemd[1]    Starting LSB: Tool to automatically collect and submit kernel crash signatures...
03/18/15 08:39:07 PM    optimus    NetworkManager[2990]    <info> Writing DNS information to /sbin/resolvconf
03/18/15 08:39:07 PM    optimus    dnsmasq[3179]    setting upstream servers from DBus
03/18/15 08:39:07 PM    optimus    dnsmasq[3179]    using nameserver 192.168.2.1#53
03/18/15 08:39:07 PM    optimus    systemd[1]    Starting LSB: start DirMngr daemon...
03/18/15 08:39:07 PM    optimus    systemd[1]    Starting LSB: Cleans up any mess left by 0dns-up...
03/18/15 08:39:07 PM    optimus    systemd[1]    Starting LSB: minidlna server...
03/18/15 08:39:07 PM    optimus    systemd[1]    Starting Network Manager Script Dispatcher Service...
03/18/15 08:39:07 PM    optimus    dirmngr[3224]    * Starting DirMngr dirmngr
03/18/15 08:39:07 PM    optimus    dns-clean[3226]    * Restoring resolver state...
03/18/15 08:39:07 PM    optimus    dns-clean[3226]    ...done.
03/18/15 08:39:07 PM    optimus    systemd[1]    Started LSB: Cleans up any mess left by 0dns-up.
03/18/15 08:39:07 PM    optimus    dbus[3013]    [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
03/18/15 08:39:07 PM    optimus    systemd[1]    Started Network Manager Script Dispatcher Service.
03/18/15 08:39:07 PM    optimus    nm-dispatcher    Dispatching action 'up' for mlan0
03/18/15 08:39:07 PM    optimus    systemd[1]    Started LSB: Tool to automatically collect and submit kernel crash signatures.
03/18/15 08:39:07 PM    optimus    dirmngr[3224]    ...done.
03/18/15 08:39:07 PM    optimus    systemd[1]    Started LSB: start DirMngr daemon.
03/18/15 08:39:07 PM    optimus    systemd[1]    Started LSB: minidlna server.
03/18/15 08:39:07 PM    optimus    systemd[1]    Reached target Multi-User System.
03/18/15 08:39:07 PM    optimus    systemd[1]    Starting Multi-User System.
03/18/15 08:39:07 PM    optimus    systemd[1]    Reached target Graphical Interface.
03/18/15 08:39:07 PM    optimus    systemd[1]    Starting Graphical Interface.
03/18/15 08:39:07 PM    optimus    systemd[1]    Starting Update UTMP about System Runlevel Changes...
03/18/15 08:39:07 PM    optimus    systemd[1]    Started Stop ureadahead data collection 45s after completed startup.
03/18/15 08:39:07 PM    optimus    systemd[1]    Starting Stop ureadahead data collection 45s after completed startup.
03/18/15 08:39:07 PM    optimus    systemd[1]    Started Update UTMP about System Runlevel Changes.
03/18/15 08:39:08 PM    optimus    whoopsie[2986]    [20:39:08] The default IPv4 route is: /org/freedesktop/NetworkManager/ActiveConnection/0
03/18/15 08:39:08 PM    optimus    whoopsie[2986]    [20:39:08] Not a paid data plan: /org/freedesktop/NetworkManager/ActiveConnection/0
03/18/15 08:39:08 PM    optimus    whoopsie[2986]    [20:39:08] Found usable connection: /org/freedesktop/NetworkManager/ActiveConnection/0
03/18/15 08:39:08 PM    optimus    whoopsie[2986]    [20:39:08] online
03/18/15 08:39:09 PM    optimus    sddm-helper    pam_ecryptfs: Passphrase file wrapped
03/18/15 08:39:10 PM    optimus    systemd[1]    Created slice user-1000.slice.
03/18/15 08:39:10 PM    optimus    systemd[1]    Starting user-1000.slice.
03/18/15 08:39:10 PM    optimus    systemd[1]    Starting User Manager for UID 1000...
03/18/15 08:39:10 PM    optimus    systemd[1]    Started Session 2 of user andy.
03/18/15 08:39:10 PM    optimus    systemd[1]    Starting Session 2 of user andy.
03/18/15 08:39:10 PM    optimus    systemd[3386]    Unit type .busname is not supported on this system.
03/18/15 08:39:10 PM    optimus    systemd[3386]    Unit boot-efi.mount is bound to inactive unit. Stopping, too.
03/18/15 08:39:10 PM    optimus    systemd[3386]    Startup finished in 15ms.
03/18/15 08:39:10 PM    optimus    systemd[1]    Started User Manager for UID 1000.
03/18/15 08:39:10 PM    optimus    systemd[3386]    Reached target Timers.
03/18/15 08:39:10 PM    optimus    systemd[3386]    Starting Timers.
03/18/15 08:39:10 PM    optimus    systemd[3386]    Reached target Paths.
03/18/15 08:39:10 PM    optimus    systemd[3386]    Starting Paths.
03/18/15 08:39:10 PM    optimus    systemd[3386]    Reached target Sockets.
03/18/15 08:39:10 PM    optimus    systemd[3386]    Starting Sockets.
03/18/15 08:39:10 PM    optimus    systemd[3386]    Reached target Basic System.
03/18/15 08:39:10 PM    optimus    systemd[3386]    Starting Basic System.
03/18/15 08:39:10 PM    optimus    systemd[3386]    Reached target Default.
03/18/15 08:39:10 PM    optimus    systemd[3386]    Starting Default.
03/18/15 08:39:10 PM    optimus    dbus[3013]    [system] Activating via systemd: service name='org.freedesktop.ConsoleKit' unit='console-kit-daemon.service'
03/18/15 08:39:10 PM    optimus    systemd[1]    Starting Console Manager...
03/18/15 08:39:10 PM    optimus    console-kit-daemon[3449]    missing action
03/18/15 08:39:10 PM    optimus    dbus[3013]    [system] Successfully activated service 'org.freedesktop.ConsoleKit'
03/18/15 08:39:10 PM    optimus    systemd[1]    Started Console Manager.
03/18/15 08:39:10 PM    optimus    sddm[3116]    Checking for pam module
03/18/15 08:39:10 PM    optimus    sddm[3116]    Got pam-login
03/18/15 08:39:10 PM    optimus    sddm[3116]    kwalletd: Waiting for hash on 17-
03/18/15 08:39:10 PM    optimus    sddm[3116]    kwalletd: waitingForEnvironment on: 20
03/18/15 08:39:10 PM    optimus    sddm[3116]    kwalletd: client connected
03/18/15 08:39:10 PM    optimus    sddm[3116]    kwalletd: client disconnected
03/18/15 08:39:11 PM    optimus    org.kde.kglobalaccel[3523]    kf5.kiconthemes: "Theme tree: (Breeze)"
03/18/15 08:39:11 PM    optimus    org.kde.kglobalaccel[3523]    Loading group  "KDE Keyboard Layout Switcher"
03/18/15 08:39:11 PM    optimus    org.kde.kglobalaccel[3523]    Loading group  "kcm_touchpad"
03/18/15 08:39:11 PM    optimus    org.kde.kglobalaccel[3523]    Loading group  "amarok"
03/18/15 08:39:11 PM    optimus    org.kde.kglobalaccel[3523]    "decreaseVolume" skipping because key "" is already taken
03/18/15 08:39:11 PM    optimus    org.kde.kglobalaccel[3523]    "skipTrack" skipping because key "" is already taken
03/18/15 08:39:11 PM    optimus    org.kde.kglobalaccel[3523]    Loading group  "khotkeys"
03/18/15 08:39:11 PM    optimus    org.kde.kglobalaccel[3523]    "{d03619b6-9b3c-48cc-9d9c-a2aadb485550}" skipping because key "" is already taken
03/18/15 08:39:11 PM    optimus    org.kde.kglobalaccel[3523]    Loading group  "kmix"
03/18/15 08:39:11 PM    optimus    org.kde.kglobalaccel[3523]    Loading group  "kwin"
03/18/15 08:39:11 PM    optimus    org.kde.kglobalaccel[3523]    Loading group  "ksmserver"
03/18/15 08:39:11 PM    optimus    org.kde.kglobalaccel[3523]    Loading group  "krunner"
03/18/15 08:39:11 PM    optimus    org.kde.kglobalaccel[3523]    Loading group  "yakuake"
03/18/15 08:39:11 PM    optimus    org.kde.kglobalaccel[3523]    Loading group  "plasmashell"
03/18/15 08:39:11 PM    optimus    org.kde.kglobalaccel[3523]    Loading group  "kded5"
03/18/15 08:39:11 PM    optimus    org.kde.kglobalaccel[3523]    Registering key "Ctrl+Esc" for "kded5" : "Show System Activity"
03/18/15 08:39:11 PM    optimus    org.kde.kglobalaccel[3523]    Registering key "Ctrl+Alt+L" for "ksmserver" : "Lock Session"
03/18/15 08:39:11 PM    optimus    org.kde.kglobalaccel[3523]    Registering key "Screensaver" for "ksmserver" : "Lock Session"
03/18/15 08:39:11 PM    optimus    org.kde.kglobalaccel[3523]    Registering key "Display" for "kded5" : "display"
03/18/15 08:39:11 PM    optimus    dbus[3013]    [system] Activating service name='org.kde.powerdevil.backlighthelper' (using servicehelper)
03/18/15 08:39:11 PM    optimus    dbus[3013]    [system] Successfully activated service 'org.kde.powerdevil.backlighthelper'
03/18/15 08:39:11 PM    optimus    org.kde.kglobalaccel[3523]    Registering key "Monitor Brightness Up" for "kded5" : "Increase Screen Brightness"
03/18/15 08:39:11 PM    optimus    org.kde.kglobalaccel[3523]    Registering key "Monitor Brightness Down" for "kded5" : "Decrease Screen Brightness"
03/18/15 08:39:11 PM    optimus    org.kde.kglobalaccel[3523]    Registering key "Keyboard Brightness Up" for "kded5" : "Increase Keyboard Brightness"
03/18/15 08:39:11 PM    optimus    org.kde.kglobalaccel[3523]    Registering key "Keyboard Brightness Down" for "kded5" : "Decrease Keyboard Brightness"
03/18/15 08:39:11 PM    optimus    org.kde.kglobalaccel[3523]    Registering key "Keyboard Light On/Off" for "kded5" : "Toggle Keyboard Backlight"
03/18/15 08:39:11 PM    optimus    org.kde.kglobalaccel[3523]    Registering key "Sleep" for "kded5" : "Sleep"
03/18/15 08:39:11 PM    optimus    org.kde.kglobalaccel[3523]    Registering key "Hibernate" for "kded5" : "Hibernate"
03/18/15 08:39:11 PM    optimus    org.kde.kglobalaccel[3523]    "Hibernate" : Failed to register  "Hibernate"
03/18/15 08:39:11 PM    optimus    org.kde.kglobalaccel[3523]    Registering key "Power Off" for "kded5" : "PowerOff"
03/18/15 08:39:11 PM    optimus    org.kde.kglobalaccel[3523]    Unregistering key "Keyboard Brightness Up" for "kded5" : "Increase Keyboard Brightness"
03/18/15 08:39:11 PM    optimus    org.kde.kglobalaccel[3523]    Unregistering key "Keyboard Brightness Down" for "kded5" : "Decrease Keyboard Brightness"
03/18/15 08:39:11 PM    optimus    org.kde.kglobalaccel[3523]    Unregistering key "Keyboard Light On/Off" for "kded5" : "Toggle Keyboard Backlight"
03/18/15 08:39:11 PM    optimus    org.kde.kglobalaccel[3523]    Registering key "Alt+F3" for "kwin" : "Window Operations Menu"
03/18/15 08:39:11 PM    optimus    org.kde.kglobalaccel[3523]    Registering key "Alt+F4" for "kwin" : "Window Close"
03/18/15 08:39:11 PM    optimus    org.kde.kglobalaccel[3523]    Registering key "Ctrl+Alt+A" for "kwin" : "Activate Window Demanding Attention"
03/18/15 08:39:11 PM    optimus    org.kde.kglobalaccel[3523]    Registering key "Ctrl+F12" for "plasmashell" : "show dashboard"
03/18/15 08:39:11 PM    optimus    org.kde.kglobalaccel[3523]    Registering key "Meta+Q" for "plasmashell" : "manage activities"
03/18/15 08:39:11 PM    optimus    org.kde.kglobalaccel[3523]    Registering key "Meta+Tab" for "plasmashell" : "next activity"
03/18/15 08:39:11 PM    optimus    org.kde.kglobalaccel[3523]    Registering key "Meta+Shift+Tab" for "plasmashell" : "previous activity"
03/18/15 08:39:11 PM    optimus    org.kde.kglobalaccel[3523]    Registering key "Meta+Alt+Up" for "kwin" : "Switch Window Up"
03/18/15 08:39:11 PM    optimus    org.kde.kglobalaccel[3523]    Registering key "Meta+S" for "plasmashell" : "stop current activity"
03/18/15 08:39:11 PM    optimus    org.kde.kglobalaccel[3523]    Registering key "Meta+Alt+Down" for "kwin" : "Switch Window Down"
03/18/15 08:39:11 PM    optimus    org.kde.kglobalaccel[3523]    Registering key "Meta+Alt+Right" for "kwin" : "Switch Window Right"
03/18/15 08:39:11 PM    optimus    org.kde.kglobalaccel[3523]    Registering key "Meta+Alt+Left" for "kwin" : "Switch Window Left"
03/18/15 08:39:11 PM    optimus    org.kde.kglobalaccel[3523]    Registering key "Alt+Space" for "krunner" : "run command"
03/18/15 08:39:11 PM    optimus    org.kde.kglobalaccel[3523]    Registering key "Alt+F2" for "krunner" : "run command"
03/18/15 08:39:11 PM    optimus    org.kde.kglobalaccel[3523]    Registering key "Search" for "krunner" : "run command"
03/18/15 08:39:11 PM    optimus    org.kde.kglobalaccel[3523]    Registering key "Alt+Shift+F2" for "krunner" : "run command on clipboard contents"
03/18/15 08:39:11 PM    optimus    org.kde.kglobalaccel[3523]    Registering key "Ctrl+Alt+Esc" for "kwin" : "Kill Window"
03/18/15 08:39:11 PM    optimus    org.kde.kglobalaccel[3523]    Registering key "Alt+Shift+F12" for "kwin" : "Suspend Compositing"
03/18/15 08:39:11 PM    optimus    org.kde.kglobalaccel[3523]    Registering key "Alt+Tab" for "kwin" : "Walk Through Windows"
03/18/15 08:39:11 PM    optimus    org.kde.kglobalaccel[3523]    Registering key "Alt+Shift+Backtab" for "kwin" : "Walk Through Windows (Reverse)"
03/18/15 08:39:11 PM    optimus    org.kde.kglobalaccel[3523]    Registering key "Alt+`" for "kwin" : "Walk Through Windows of Current Application"
03/18/15 08:39:11 PM    optimus    org.kde.kglobalaccel[3523]    Registering key "Alt+~" for "kwin" : "Walk Through Windows of Current Application (Reverse)"
03/18/15 08:39:11 PM    optimus    org.kde.kglobalaccel[3523]    adding shift to the grab
03/18/15 08:39:11 PM    optimus    org.kde.kglobalaccel[3523]    Registering key "Ctrl+F1" for "kwin" : "Switch to Desktop 1"
03/18/15 08:39:11 PM    optimus    org.kde.kglobalaccel[3523]    Registering key "Ctrl+F2" for "kwin" : "Switch to Desktop 2"
03/18/15 08:39:11 PM    optimus    org.kde.kglobalaccel[3523]    Registering key "Ctrl+F3" for "kwin" : "Switch to Desktop 3"
03/18/15 08:39:11 PM    optimus    org.kde.kglobalaccel[3523]    Registering key "Ctrl+F4" for "kwin" : "Switch to Desktop 4"
03/18/15 08:39:11 PM    optimus    org.kde.kglobalaccel[3523]    Registering key "Ctrl+Alt+Del" for "ksmserver" : "Log Out"
03/18/15 08:39:11 PM    optimus    org.kde.kglobalaccel[3523]    Registering key "Ctrl+Alt+Shift+Del" for "ksmserver" : "Log Out Without Confirmation"
03/18/15 08:39:11 PM    optimus    org.kde.kglobalaccel[3523]    Registering key "Ctrl+Alt+Shift+PgDown" for "ksmserver" : "Halt Without Confirmation"
03/18/15 08:39:11 PM    optimus    org.kde.kglobalaccel[3523]    Registering key "Ctrl+Alt+Shift+PgUp" for "ksmserver" : "Reboot Without Confirmation"
03/18/15 08:39:12 PM    optimus    dbus[3013]    [system] Activating via systemd: service name='org.freedesktop.RealtimeKit1' unit='rtkit-daemon.service'
03/18/15 08:39:12 PM    optimus    systemd[1]    Starting RealtimeKit Scheduling Policy Service...
03/18/15 08:39:12 PM    optimus    dbus[3013]    [system] Successfully activated service 'org.freedesktop.RealtimeKit1'
03/18/15 08:39:12 PM    optimus    rtkit-daemon[3641]    Successfully called chroot.
03/18/15 08:39:12 PM    optimus    rtkit-daemon[3641]    Successfully dropped privileges.
03/18/15 08:39:12 PM    optimus    rtkit-daemon[3641]    Successfully limited resources.
03/18/15 08:39:12 PM    optimus    rtkit-daemon[3641]    Running.
03/18/15 08:39:12 PM    optimus    rtkit-daemon[3641]    Watchdog thread running.
03/18/15 08:39:12 PM    optimus    rtkit-daemon[3641]    Canary thread running.
03/18/15 08:39:12 PM    optimus    systemd[1]    Started RealtimeKit Scheduling Policy Service.
03/18/15 08:39:12 PM    optimus    rtkit-daemon[3641]    Successfully made thread 3639 of process 3639 (n/a) owned by '1000' high priority at nice level -11.
03/18/15 08:39:12 PM    optimus    rtkit-daemon[3641]    Supervising 1 threads of 1 processes of 1 users.
03/18/15 08:39:12 PM    optimus    pulseaudio[3639]    [pulseaudio] alsa-util.c: Disabling timer-based scheduling because running inside a VM.
03/18/15 08:39:12 PM    optimus    rtkit-daemon[3641]    Supervising 1 threads of 1 processes of 1 users.
03/18/15 08:39:12 PM    optimus    rtkit-daemon[3641]    Successfully made thread 3656 of process 3639 (n/a) owned by '1000' RT at priority 5.
03/18/15 08:39:12 PM    optimus    rtkit-daemon[3641]    Supervising 2 threads of 1 processes of 1 users.
03/18/15 08:39:12 PM    optimus    org.kde.kglobalaccel[3523]    Registering key "Ctrl+F8" for "kwin" : "ShowDesktopGrid"
03/18/15 08:39:12 PM    optimus    org.kde.kglobalaccel[3523]    Registering key "Alt+F1" for "plasmashell" : "activate widget 2"
03/18/15 08:39:12 PM    optimus    org.kde.kglobalaccel[3523]    Registering key "Ctrl+F9" for "kwin" : "Expose"
03/18/15 08:39:12 PM    optimus    org.kde.kglobalaccel[3523]    Registering key "Ctrl+F10" for "kwin" : "ExposeAll"
03/18/15 08:39:12 PM    optimus    org.kde.kglobalaccel[3523]    Registering key "Launch (C)" for "kwin" : "ExposeAll"
03/18/15 08:39:12 PM    optimus    org.kde.kglobalaccel[3523]    Registering key "Ctrl+F7" for "kwin" : "ExposeClass"
03/18/15 08:39:12 PM    optimus    rtkit-daemon[3641]    Supervising 2 threads of 1 processes of 1 users.
03/18/15 08:39:12 PM    optimus    rtkit-daemon[3641]    Successfully made thread 3660 of process 3639 (n/a) owned by '1000' RT at priority 5.
03/18/15 08:39:12 PM    optimus    rtkit-daemon[3641]    Supervising 3 threads of 1 processes of 1 users.
03/18/15 08:39:12 PM    optimus    rtkit-daemon[3641]    Supervising 3 threads of 1 processes of 1 users.
03/18/15 08:39:12 PM    optimus    rtkit-daemon[3641]    Successfully made thread 3661 of process 3639 (n/a) owned by '1000' RT at priority 5.
03/18/15 08:39:12 PM    optimus    rtkit-daemon[3641]    Supervising 4 threads of 1 processes of 1 users.
03/18/15 08:39:12 PM    optimus    org.kde.kglobalaccel[3523]    Registering key "Meta+=" for "kwin" : "view_zoom_in"
03/18/15 08:39:12 PM    optimus    org.kde.kglobalaccel[3523]    Registering key "Meta+-" for "kwin" : "view_zoom_out"
03/18/15 08:39:12 PM    optimus    org.kde.kglobalaccel[3523]    Registering key "Meta+0" for "kwin" : "view_actual_size"
03/18/15 08:39:12 PM    optimus    org.kde.kglobalaccel[3523]    Registering key "Meta+Left" for "kwin" : "MoveZoomLeft"
03/18/15 08:39:12 PM    optimus    org.kde.kglobalaccel[3523]    Registering key "Meta+Right" for "kwin" : "MoveZoomRight"
03/18/15 08:39:12 PM    optimus    bluetoothd[2982]    Endpoint registered: sender=:1.45 path=/MediaEndpoint/BlueZ4/HFPAG
03/18/15 08:39:12 PM    optimus    bluetoothd[2982]    Endpoint registered: sender=:1.45 path=/MediaEndpoint/BlueZ4/HFPHS
03/18/15 08:39:12 PM    optimus    bluetoothd[2982]    Endpoint registered: sender=:1.45 path=/MediaEndpoint/BlueZ4/A2DPSource
03/18/15 08:39:12 PM    optimus    bluetoothd[2982]    Endpoint registered: sender=:1.45 path=/MediaEndpoint/BlueZ4/A2DPSink
03/18/15 08:39:12 PM    optimus    bluetoothd[2982]    bluetoothd[2982]: Endpoint registered: sender=:1.45 path=/MediaEndpoint/BlueZ4/HFPAG
03/18/15 08:39:12 PM    optimus    bluetoothd[2982]    bluetoothd[2982]: Endpoint registered: sender=:1.45 path=/MediaEndpoint/BlueZ4/HFPHS
03/18/15 08:39:12 PM    optimus    bluetoothd[2982]    bluetoothd[2982]: Endpoint registered: sender=:1.45 path=/MediaEndpoint/BlueZ4/A2DPSource
03/18/15 08:39:12 PM    optimus    bluetoothd[2982]    bluetoothd[2982]: Endpoint registered: sender=:1.45 path=/MediaEndpoint/BlueZ4/A2DPSink
03/18/15 08:39:12 PM    optimus    org.kde.kglobalaccel[3523]    Registering key "Meta+Up" for "kwin" : "MoveZoomUp"
03/18/15 08:39:12 PM    optimus    org.kde.kglobalaccel[3523]    Registering key "Meta+Down" for "kwin" : "MoveZoomDown"
03/18/15 08:39:12 PM    optimus    org.kde.kglobalaccel[3523]    Registering key "Meta+F5" for "kwin" : "MoveMouseToFocus"
03/18/15 08:39:12 PM    optimus    kernel    [  102.422028] snd_hda_intel 0000:00:1b.0: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
03/18/15 08:39:12 PM    optimus    org.kde.kglobalaccel[3523]    Registering key "Meta+F6" for "kwin" : "MoveMouseToCenter"
03/18/15 08:39:12 PM    optimus    rtkit-daemon[3641]    Successfully made thread 3667 of process 3667 (n/a) owned by '1000' high priority at nice level -11.
03/18/15 08:39:12 PM    optimus    rtkit-daemon[3641]    Supervising 5 threads of 2 processes of 1 users.
03/18/15 08:39:12 PM    optimus    pulseaudio[3667]    [pulseaudio] pid.c: Daemon already running.
03/18/15 08:39:12 PM    optimus    org.kde.kglobalaccel[3523]    Registering key "Volume Up" for "kmix" : "increase_volume"
03/18/15 08:39:12 PM    optimus    org.a11y.Bus[3523]    Activating service name='org.a11y.atspi.Registry'
03/18/15 08:39:12 PM    optimus    org.kde.kglobalaccel[3523]    Registering key "Volume Down" for "kmix" : "decrease_volume"
03/18/15 08:39:12 PM    optimus    org.kde.kglobalaccel[3523]    Registering key "Volume Mute" for "kmix" : "mute"
03/18/15 08:39:12 PM    optimus    org.a11y.Bus[3523]    Successfully activated service 'org.a11y.atspi.Registry'
03/18/15 08:39:12 PM    optimus    org.a11y.atspi.Registry[3689]    SpiRegistry daemon is running with well-known name - org.a11y.atspi.Registry
03/18/15 08:39:12 PM    optimus    NetworkManager[2990]    <info> Activation (mlan0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
03/18/15 08:39:12 PM    optimus    NetworkManager[2990]    <info> Activation (mlan0) Stage 4 of 5 (IPv6 Configure Timeout) started...
03/18/15 08:39:12 PM    optimus    NetworkManager[2990]    <info> Activation (mlan0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
03/18/15 08:39:12 PM    optimus    pulseaudio[3639]    message repeated 2 times: [ [pulseaudio] alsa-util.c: Disabling timer-based scheduling because running inside a VM.]
03/18/15 08:39:13 PM    optimus    org.kde.kglobalaccel[3523]    Registering key "Ctrl+Alt+K" for "KDE Keyboard Layout Switcher" : "Switch to Next Keyboard Layout"
03/18/15 08:39:13 PM    optimus    org.kde.kglobalaccel[3523]    1
03/18/15 08:39:13 PM    optimus    org.kde.kglobalaccel[3523]    Registering key "Print" for "khotkeys" : "{554bf4a4-ce8e-455a-906a-4f417f1860ee}"
03/18/15 08:39:13 PM    optimus    org.kde.kglobalaccel[3523]    2
03/18/15 08:39:13 PM    optimus    NetworkManager[2990]    <info> WiFi hardware radio set enabled
03/18/15 08:39:13 PM    optimus    NetworkManager[2990]    <info> WWAN hardware radio set enabled
03/18/15 08:39:13 PM    optimus    pulseaudio[3639]    [alsa-sink-ALC288 Analog] alsa-sink.c: ALSA woke us up to write new data to the device, but there was actually nothing to write!
03/18/15 08:39:13 PM    optimus    pulseaudio[3639]    [alsa-sink-ALC288 Analog] alsa-sink.c: Most likely this is a bug in the ALSA driver 'snd_hda_intel'. Please report this issue to the ALSA developers.
03/18/15 08:39:13 PM    optimus    pulseaudio[3639]    [alsa-sink-ALC288 Analog] alsa-sink.c: We were woken up with POLLOUT set -- however a subsequent snd_pcm_avail() returned 0 or another value < min_avail.
03/18/15 08:39:13 PM    optimus    org.kde.kglobalaccel[3523]    2
03/18/15 08:39:14 PM    optimus    org.kde.kglobalaccel[3523]    Registering key "Meta+A" for "amarok" : "playlist_add"
03/18/15 08:39:14 PM    optimus    org.kde.kglobalaccel[3523]    Registering key "Meta+Shift++" for "amarok" : "seek_forward_medium"
03/18/15 08:39:14 PM    optimus    org.kde.kglobalaccel[3523]    Registering key "Meta+Shift+-" for "amarok" : "seek_backward_medium"
03/18/15 08:39:14 PM    optimus    org.kde.kglobalaccel[3523]    Registering key "Media Previous" for "amarok" : "prev"
03/18/15 08:39:14 PM    optimus    org.kde.kglobalaccel[3523]    Registering key "Media Next" for "amarok" : "next"
03/18/15 08:39:14 PM    optimus    org.kde.kglobalaccel[3523]    Registering key "Meta++" for "amarok" : "increaseVolume"
03/18/15 08:39:14 PM    optimus    org.kde.kglobalaccel[3523]    adding shift to the grab
03/18/15 08:39:14 PM    optimus    org.kde.kglobalaccel[3523]    Registering key "Meta+O" for "amarok" : "showNotificationPopup"
03/18/15 08:39:14 PM    optimus    org.kde.kglobalaccel[3523]    Registering key "Meta+M" for "amarok" : "mute"
03/18/15 08:39:14 PM    optimus    org.kde.kglobalaccel[3523]    Registering key "Meta+L" for "amarok" : "loveTrack"
03/18/15 08:39:14 PM    optimus    org.kde.kglobalaccel[3523]    Registering key "Meta+1" for "amarok" : "rate1"
03/18/15 08:39:14 PM    optimus    org.kde.kglobalaccel[3523]    Registering key "Meta+2" for "amarok" : "rate2"
03/18/15 08:39:14 PM    optimus    org.kde.kglobalaccel[3523]    Registering key "Meta+3" for "amarok" : "rate3"
03/18/15 08:39:14 PM    optimus    org.kde.kglobalaccel[3523]    Registering key "Meta+4" for "amarok" : "rate4"
03/18/15 08:39:14 PM    optimus    org.kde.kglobalaccel[3523]    Registering key "Meta+5" for "amarok" : "rate5"
03/18/15 08:39:14 PM    optimus    org.kde.kglobalaccel[3523]    Registering key "Media Stop" for "amarok" : "stop"
03/18/15 08:39:14 PM    optimus    org.kde.kglobalaccel[3523]    Registering key "Meta+Shift+V" for "amarok" : "stop_after_current"
03/18/15 08:39:14 PM    optimus    org.kde.kglobalaccel[3523]    Registering key "Media Play" for "amarok" : "play_pause"
03/18/15 08:39:14 PM    optimus    org.kde.kglobalaccel[3523]    Registering key "Ctrl+Alt+X" for "plasmashell" : "clipboard_action"
03/18/15 08:39:14 PM    optimus    org.kde.kglobalaccel[3523]    Registering key "Ctrl+Alt+R" for "plasmashell" : "repeat_action"
03/18/15 08:39:15 PM    optimus    ntpdate[3381]    adjust time server 91.189.94.4 offset 0.336561 sec
03/18/15 08:39:18 PM    optimus    kernel    [  108.686093] Valid eCryptfs headers not found in file header region or xattr region, inode 10107650
03/18/15 08:39:20 PM    optimus    org.kde.kglobalaccel[3523]    Got XKeyPress event
03/18/15 08:39:20 PM    optimus    org.kde.kglobalaccel[3523]    "Alt+F2" = "run command"
03/18/15 08:39:35 PM    optimus    org.kde.kglobalaccel[3523]    Got XKeyPress event
03/18/15 08:39:35 PM    optimus    org.kde.kglobalaccel[3523]    "Alt+F2" = "run command"
03/18/15 08:39:37 PM    optimus    org.kde.kglobalaccel[3523]    Got XKeyPress event
03/18/15 08:39:37 PM    optimus    org.kde.kglobalaccel[3523]    "Alt+F2" = "run command"
03/18/15 08:39:43 PM    optimus    org.kde.kglobalaccel[3523]    Got XKeyPress event
03/18/15 08:39:43 PM    optimus    org.kde.kglobalaccel[3523]    "Alt+F2" = "run command"
03/18/15 08:39:49 PM    optimus    org.kde.kglobalaccel[3523]    Got XKeyPress event
03/18/15 08:39:49 PM    optimus    org.kde.kglobalaccel[3523]    "Alt+Tab" = "Walk Through Windows"
03/18/15 08:39:51 PM    optimus    org.kde.kglobalaccel[3523]    Got XKeyPress event
03/18/15 08:39:51 PM    optimus    org.kde.kglobalaccel[3523]    "Alt+F2" = "run command"
03/18/15 08:39:52 PM    optimus    systemd[1]    Starting Stop ureadahead data collection...
03/18/15 08:39:52 PM    optimus    systemd[1]    Stopped Read required files in advance.
03/18/15 08:39:52 PM    optimus    systemd[1]    Started Stop ureadahead data collection.

```

---

### Post by grahammechanical on 2015-03-18
Just so that we clearly understand. Is this vivid vervet (15.04) and is it Kubuntu?

Vivid vervet has recently switched to using systemd instead of upstart. I am running Ubuntu vivid vervet and systemd adds about 80 seconds to the loading time. The Advanced Options sub-menu does give us an upstart option. Try that and see it the loading time is any different.

It is also useful to know if a bug applies to one flavour of Ubuntu or to all of them. this is why it would be nice to know if this is Ubuntu or Kubuntu.

Regards.

---

### Post by gunksta on 2015-03-18
I apologize. My comments should have included that information. 

Yes. I am running Vivid and I am running Kubuntu.

I did not think about switch to systemd would cause such a slowdown. Ouch. Unfortunately, my "old" laptop, a one year old Dell XPS 13 died from a violent motherboard problem and I keep my server on LTS releases. Thus, I thought I might have messed up the installation onto this hardware that I've only had a few days. I will try the upstart option and report back. I did some quick googling and I see what you mean. Lots of people are reporting slow boots, quite similar to mine.

Very interesting.

---

### Post by gunksta on 2015-03-18
OK. I think you are correct. I just did a quick update and reset my computer.

And it got worse. A lot worse. I have to start X manually now with a good old-fashionned startx after logging into a tty.

I did not see an option to boot via upstart when I booted up. Looking at my installed packages, I do not have upstart installed. Given how widespread this issue is, I may just cool my jets for a few days to see if they can get it resolved, although I would like to boot to sddm, not tty1.

---

### Post by gunksta on 2015-03-18
After resetting a couple of times, I got tired of it and installed upstart. I reset the computer, and it booted like a greased pig.

Whatever the merits / demerits of systemd, Ubuntu isn't quite ready for it. Maybe they will get it ready in time for Vivid, but if not, I would prefer they wait. That was ugly.

---

### Post by grahammechanical on 2015-03-19
You are right. Upstart has been removed but upstart-bin is still on my system. I was sure that whether we were upgrading an existing 15.04 install or putting in a new install from a daily image we would get an option to load with upstart in the Advanced Options for Ubuntu sub-menu.

I have been running vivid since the start of the development cycle. At first upstart was the default. Then we got a systemd option as an Advanced option and just recently things were switched around with systemd as default and upstart as an Advanced option. I do expect all the upstart code to be removed at some point but Ubuntu phones do not use systemd.  So, the matter of convergence comes into it. The desktop devs had better not be too quick getting completely rid of upstart until the phone devs have caught up.

Regards.

---

### Post by ventrical on 2015-03-19
> **grahammechanical said:**
> You are right. Upstart has been removed but upstart-bin is still on my system. I was sure that whether we were upgrading an existing 15.04 install or putting in a new install from a daily image we would get an option to load with upstart in the Advanced Options for Ubuntu sub-menu.

I have been running vivid since the start of the development cycle. At first upstart was the default. Then we got a systemd option as an Advanced option and just recently things were switched around with systemd as default and upstart as an Advanced option. I do expect all the upstart code to be removed at some point but Ubuntu phones do not use systemd.  So, the matter of convergence comes into it. The desktop devs had better not be too quick getting completely rid of upstart until the phone devs have caught up.

Regards.

I still have the upstart option in GRuB (after todays upgrade) and the only difference I notice is about 1 second faster to desktop on my fastest machine with upstart - but systemD is not really complaining.

This on original ubuntu-desktop-unity install.

 So I am a little perplexed as to what I am doing wrong , or , what I am doing right ?

Regards..

---

### Post by grahammechanical on 2015-03-19
I just installed Kubuntu vivid daily and it does not have an upstart option as an Advanced option. It is loading with systemd. Getting to recovery mode shows systemd messages. And loading seems a lot quicker than on my Ubuntu vivid. But there are other problems with Kubuntu that make it unusable. Getting the screen resolution completely wrong. Everything over sized.

It may be a problem between kernel 3.19.0-9 and Nouveau. I will try again and tick to install Nvidia drivers.

Regards.

---

### Post by ventrical on 2015-03-19
> **grahammechanical said:**
> I just installed Kubuntu vivid daily and it does not have an upstart option as an Advanced option. It is loading with systemd. Getting to recovery mode shows systemd messages. And loading seems a lot quicker than on my Ubuntu vivid. But there are other problems with Kubuntu that make it unusable. Getting the screen resolution completely wrong. Everything over sized.

It may be a problem between kernel 3.19.0-9 and Nouveau. I will try again and tick to install Nvidia drivers.

Regards.

I stand corrected here. I will upgrade my install of Kubuntu and report back. Kubuntu has been working exceptionally well this cycle .. now I have some trepidation to update :)

Regards..

---

### Post by ventrical on 2015-03-19
After update/upgrade - it appeared that there was another entry in Grub. I assumed it was upstart but it is generic systemD boot. The other options are systemD and (recovery mode). Very weird behaviour. It will not boot into desktop. I have to:

```

sudo service sddm restart

```

to get desktop .. so somthing busted in the upgrade as which is why I had trepidation to update :) It was working beautifully before update . But we are here to update these things and try to break our installs so things are rolling allong as expected.

btw .. goto

kinfocenter>graphical information>OpenGL and click and see if you get mouse spin also.

```
        [FONT=monospace][COLOR=#000000]*-display [/COLOR]
                description: VGA compatible controller 
                product: GT218 [GeForce 210] 
                vendor: NVIDIA Corporation 
                physical id: 0 
                bus info: pci@0000:01:00.0 
                version: a2 
                width: 64 bits 
                clock: 33MHz 
                capabilities: vga_controller bus_master cap_list rom 
                configuration: driver=nouveau latency=0 
                resource
[/FONT]
   
```

---

### Post by ventrical on 2015-03-19
Also did not upgrade kernel:

```

       [FONT=monospace][COLOR=#000000]ventrical@ventrical-desktop:~$ uname -a                                                  [/COLOR]
Linux ventrical-desktop 3.18.0-11-generic #12-Ubuntu SMP Fri Jan 23 22:53:58 UTC 2015 x8
6_64 x86_64 x86_64 GNU/Linux                                                             
ventrical@ventrical-desktop:~$                                                           
 
```
  
[/FONT]

---

### Post by ventrical on 2015-03-19
..and..

```

sudo update-grub

```

recognized 3.19.n-n kernel but did not list it in grub. 

A real mess indeed compared to where it started a few days back.

Regards..

---

