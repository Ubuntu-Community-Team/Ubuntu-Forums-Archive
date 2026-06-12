---
title: "IBM Power 720 Ethernet not working"
date: 2016-08-12
forum: Server Platforms
---

### Post by pa8600 on 2016-08-12
So I recently acquired an IBM Power 720 PPC based server. The hardware test disc shows that everything is working, however Ubuntu PPC Setup does not see the 4 port Ethernet, and neither does the installed OS. Debian also does not initially sense the network device, and it doesn't show up in lspci, however after Debian setup detects network hardware and it sees the 4 ethernet ports I notice a lot of references to ibmebus and ethernet showing up in dmesg. 

On Ubuntu however I see nothing about ibmebus in my dmesg. I have to bypass the onboard ethernet with a USB ethernet dongle. Is there a way of getting ethernet working by say, rebuilding the kernel or building a kernel module?

uname output:
Linux 4.4.0-34-powerpc64-smp #53-Ubuntu SMP Wed Jul 27 17:57:18 UTC 2016 ppc64 ppc64 ppc64 GNU/Linux


dmesg output:
```
$ dmesg
[    0.000000] Allocated 2359296 bytes for 1024 pacas at c00000000eca0000
[    0.000000] Using pSeries machine description
[    0.000000] Page sizes from device-tree:
[    0.000000] base_shift=12: shift=12, sllp=0x0000, avpnm=0x00000000, tlbiel=1, penc=0
[    0.000000] base_shift=12: shift=16, sllp=0x0000, avpnm=0x00000000, tlbiel=1, penc=7
[    0.000000] base_shift=12: shift=24, sllp=0x0000, avpnm=0x00000000, tlbiel=1, penc=56
[    0.000000] base_shift=16: shift=16, sllp=0x0110, avpnm=0x00000000, tlbiel=1, penc=1
[    0.000000] base_shift=16: shift=24, sllp=0x0110, avpnm=0x00000000, tlbiel=1, penc=8
[    0.000000] base_shift=24: shift=24, sllp=0x0100, avpnm=0x00000001, tlbiel=0, penc=0
[    0.000000] base_shift=34: shift=34, sllp=0x0120, avpnm=0x000007ff, tlbiel=0, penc=3
[    0.000000] Page orders: linear mapping = 24, virtual = 12, io = 12, vmemmap = 24
[    0.000000] Using 1TB segments
[    0.000000] Found initrd at 0xc000000005380000:0xc0000000076a8000
[    0.000000] Partition configured for 16 cpus.
[    0.000000] CPU maps initialized for 4 threads per core
[    0.000000]  (thread shift is 2)
[    0.000000] Freed 2322432 bytes for unused pacas
[    0.000000] Starting Linux ppc64 #53-Ubuntu SMP Wed Jul 27 17:57:18 UTC 2016
[    0.000000] -----------------------------------------------------
[    0.000000] ppc64_pft_size    = 0x1b
[    0.000000] phys_mem_size     = 0x1de000000
[    0.000000] cpu_features      = 0x0b7e7ae418500049
[    0.000000]   possible        = 0x1fffffef18500649
[    0.000000]   always          = 0x0000000018100040
[    0.000000] cpu_user_features = 0xdc0065c2 0x20000000
[    0.000000] mmu_features      = 0x7c000001
[    0.000000] firmware_features = 0x00000001845ffc5f
[    0.000000] htab_hash_mask    = 0xfffff
[    0.000000] -----------------------------------------------------
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 4.4.0-34-powerpc64-smp (buildd@fisher03) (gcc version 5.3.1 20160413 (Ubuntu 5.3.1-14ubuntu2.1) ) #53-Ubuntu SMP Wed Jul 27 17:57:18 UTC 2016 (Ubuntu 4.4.0-34.53-powerpc64-smp 4.4.15)
[    0.000000] Node 0 Memory: 0x0-0x1de000000
[    0.000000] numa: Initmem setup node 0 [mem 0x00000000-0x1ddffffff]
[    0.000000] numa:   NODE_DATA [mem 0x1ddf11b00-0x1ddf1bfff]
[    0.000000] Section 475 and 477 (node 0) have a circular dependency on usemap and pgdat allocations
[    0.000000] PCI host bridge /pci@800000020000200  ranges:
[    0.000000]   IO 0x00003dffe01f0000..0x00003dffe01fffff -> 0x00000000000f0000
[    0.000000]  MEM 0x00003c0000000000..0x00003c007fffffff -> 0x0000000080000000
[    0.000000] PCI host bridge /pci@800000020000201  ranges:
[    0.000000]   IO 0x00003dffe02f0000..0x00003dffe02fffff -> 0x00000000000f0000
[    0.000000]  MEM 0x00003c0080000000..0x00003c00ffffffff -> 0x0000000080000000
[    0.000000] PCI host bridge /pci@800000020000202  ranges:
[    0.000000]   IO 0x00003dffe03f0000..0x00003dffe03fffff -> 0x00000000000f0000
[    0.000000]  MEM 0x00003c0100000000..0x00003c017fffffff -> 0x0000000080000000
[    0.000000] PCI host bridge /pci@800000020000204  ranges:
[    0.000000]   IO 0x00003dffe11f0000..0x00003dffe11fffff -> 0x00000000000f0000
[    0.000000]  MEM 0x00003c0400000000..0x00003c047fefffff -> 0x0000000080000000
[    0.000000] PCI host bridge /pci@800000020000205  ranges:
[    0.000000]   IO 0x00003dffe12f0000..0x00003dffe12fffff -> 0x00000000000f0000
[    0.000000]  MEM 0x00003c0480000000..0x00003c04ffefffff -> 0x0000000080000000
[    0.000000] PCI host bridge /pci@800000020000206  ranges:
[    0.000000]   IO 0x00003dffe13f0000..0x00003dffe13fffff -> 0x00000000000f0000
[    0.000000]  MEM 0x00003c0500000000..0x00003c057fefffff -> 0x0000000080000000
[    0.000000] PCI host bridge /pci@800000020000207  ranges:
[    0.000000]   IO 0x00003dffe14f0000..0x00003dffe14fffff -> 0x00000000000f0000
[    0.000000]  MEM 0x00003c0580000000..0x00003c05ffefffff -> 0x0000000080000000
[    0.000000] PPC64 nvram contains 15360 bytes
[    0.000000] Top of RAM: 0x1de000000, Total RAM: 0x1de000000
[    0.000000] Memory hole size: 0MB
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x0000000000000000-0x00000001ddffffff]
[    0.000000]   DMA32    empty
[    0.000000]   Normal   empty
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x0000000000000000-0x00000001ddffffff]
[    0.000000] Initmem setup node 0 [mem 0x0000000000000000-0x00000001ddffffff]
[    0.000000] On node 0 totalpages: 1957888
[    0.000000]   DMA zone: 30592 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 1957888 pages, LIFO batch:31
[    0.000000] PERCPU: Embedded 26 pages/cpu @c0000001ddc00000 s68248 r0 d38248 u131072
[    0.000000] pcpu-alloc: s68248 r0 d38248 u131072 alloc=1*1048576
[    0.000000] pcpu-alloc: [0] 00 01 02 03 04 05 06 07 [0] 08 09 10 11 12 13 14 15
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1927296
[    0.000000] Policy zone: DMA
[    0.000000] Kernel command line: root=UUID=117c3cf5-6ab6-4af0-bdce-84e2548f0489 ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Sorting __ex_table...
[    0.000000] Memory: 7548528K/7831552K available (11132K kernel code, 2056K rwdata, 4480K rodata, 8672K init, 2394K bss, 283024K reserved, 0K cma-reserved)
[    0.000000] SLUB: HWalign=128, Order=0-3, MinObjects=0, CPUs=16, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]  Build-time adjustment of leaf fanout to 64.
[    0.000000]  RCU restricting CPUs from NR_CPUS=1024 to nr_cpu_ids=16.
[    0.000000] RCU: Adjusting geometry for rcu_fanout_leaf=64, nr_cpu_ids=16
[    0.000000] NR_IRQS:512 nr_irqs:512 16
[    0.000000] pic: no ISA interrupt controller
[    0.000000] time_init: decrementer frequency = 512.000000 MHz
[    0.000000] time_init: processor frequency   = 3000.000000 MHz
[    0.000002] clocksource: timebase: mask: 0xffffffffffffffff max_cycles: 0x761537d007, max_idle_ns: 440795202126 ns
[    0.000003] clocksource: timebase mult[1f40000] shift[24] registered
[    0.000006] clockevent: decrementer mult[83126e98] shift[32] cpu[0]
[    0.000100] Console: colour dummy device 80x25
[    0.000149] console [tty0] enabled
[    0.000261] pid_max: default: 32768 minimum: 301
[    0.000287] Security Framework initialized
[    0.000289] Yama: becoming mindful.
[    0.000311] AppArmor: AppArmor initialized
[    0.001267] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.005521] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.007187] Mount-cache hash table entries: 16384 (order: 5, 131072 bytes)
[    0.007206] Mountpoint-cache hash table entries: 16384 (order: 5, 131072 bytes)
[    0.007523] Initializing cgroup subsys io
[    0.007528] Initializing cgroup subsys memory
[    0.007536] Initializing cgroup subsys devices
[    0.007539] Initializing cgroup subsys freezer
[    0.007542] Initializing cgroup subsys net_cls
[    0.007545] Initializing cgroup subsys perf_event
[    0.007548] Initializing cgroup subsys net_prio
[    0.007551] Initializing cgroup subsys hugetlb
[    0.007554] Initializing cgroup subsys pids
[    0.007565] ftrace: allocating 29327 entries in 173 pages
[    0.018772] EEH: pSeries platform initialized
[    0.018789] POWER7 performance monitor hardware support registered
[    0.023387] Brought up 16 CPUs
[    0.023394] Node 0 CPUs: 0-15
[    0.023418] Enabling Asymmetric SMT scheduling
[    0.023776] devtmpfs: initialized
[    0.049887] evm: security.selinux
[    0.049889] evm: security.SMACK64
[    0.049890] evm: security.SMACK64EXEC
[    0.049891] evm: security.SMACK64TRANSMUTE
[    0.049892] evm: security.SMACK64MMAP
[    0.049893] evm: security.ima
[    0.049895] evm: security.capability
[    0.050043] EEH: devices created
[    0.050168] clocksource: jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645041785100000 ns
[    0.050567] NET: Registered protocol family 16
[    0.063827] EEH: PCI Enhanced I/O Error Handling Enabled
[    0.072803] cpuidle: using governor ladder
[    0.080873] cpuidle: using governor menu
[    0.081058] pstore: Registered nvram as persistent store backend
[    0.087755] PCI: Probing PCI hardware
[    0.087839] PCI host bridge to bus 0000:00
[    0.087845] pci_bus 0000:00: root bus resource [io  0x100000-0x10ffff] (bus address [0xf0000-0xfffff])
[    0.087850] pci_bus 0000:00: root bus resource [mem 0x3c0000000000-0x3c007fffffff] (bus address [0x80000000-0xffffffff])
[    0.087853] pci_bus 0000:00: root bus resource [bus 00-ff]
[    0.120525] IOMMU table initialized, virtual merging enabled
[    0.120581] iommu: Adding device 0000:00:01.0 to group 0
[    0.120746] PCI host bridge to bus 0001:00
[    0.120752] pci_bus 0001:00: root bus resource [io  0x201000-0x210fff] (bus address [0xf0000-0xfffff])
[    0.120755] pci_bus 0001:00: root bus resource [mem 0x3c0080000000-0x3c00ffffffff] (bus address [0x80000000-0xffffffff])
[    0.120757] pci_bus 0001:00: root bus resource [bus 00-ff]
[    0.122114] pci 0001:00:01.0: supports D1 D2
[    0.122116] pci 0001:00:01.0: PME# supported from D0 D1 D2 D3hot
[    0.124246] pci 0001:00:01.1: supports D1 D2
[    0.124249] pci 0001:00:01.1: PME# supported from D0 D1 D2 D3hot
[    0.126382] pci 0001:00:01.2: supports D1 D2
[    0.126384] pci 0001:00:01.2: PME# supported from D0 D1 D2 D3hot
[    0.150028] iommu: Adding device 0001:00:01.0 to group 1
[    0.150125] iommu: Adding device 0001:00:01.1 to group 1
[    0.150162] iommu: Adding device 0001:00:01.2 to group 1
[    0.150264] PCI host bridge to bus 0002:00
[    0.150269] pci_bus 0002:00: root bus resource [io  0x302000-0x311fff] (bus address [0xf0000-0xfffff])
[    0.150271] pci_bus 0002:00: root bus resource [mem 0x3c0100000000-0x3c017fffffff] (bus address [0x80000000-0xffffffff])
[    0.150274] pci_bus 0002:00: root bus resource [bus 00-ff]
[    0.173157] PCI host bridge to bus 0003:01
[    0.173163] pci_bus 0003:01: root bus resource [io  0x403000-0x412fff] (bus address [0xf0000-0xfffff])
[    0.173166] pci_bus 0003:01: root bus resource [mem 0x3c0400000000-0x3c047fefffff] (bus address [0x80000000-0xffefffff])
[    0.173168] pci_bus 0003:01: root bus resource [bus 01-ff]
[    0.175419] pci 0003:01:00.0: supports D1 D2
[    0.199577] iommu: Adding device 0003:01:00.0 to group 3
[    0.203865] iommu: Adding device 0003:02:00.0 to group 3
[    0.203999] PCI host bridge to bus 0004:01
[    0.204004] pci_bus 0004:01: root bus resource [io  0x504000-0x513fff] (bus address [0xf0000-0xfffff])
[    0.204006] pci_bus 0004:01: root bus resource [mem 0x3c0480000000-0x3c04ffefffff] (bus address [0x80000000-0xffefffff])
[    0.204009] pci_bus 0004:01: root bus resource [bus 01-ff]
[    0.226893] PCI host bridge to bus 0005:01
[    0.226899] pci_bus 0005:01: root bus resource [io  0x605000-0x614fff] (bus address [0xf0000-0xfffff])
[    0.226902] pci_bus 0005:01: root bus resource [mem 0x3c0500000000-0x3c057fefffff] (bus address [0x80000000-0xffefffff])
[    0.226904] pci_bus 0005:01: root bus resource [bus 01-ff]
[    0.249823] PCI host bridge to bus 0006:01
[    0.249829] pci_bus 0006:01: root bus resource [io  0x706000-0x715fff] (bus address [0xf0000-0xfffff])
[    0.249831] pci_bus 0006:01: root bus resource [mem 0x3c0580000000-0x3c05ffefffff] (bus address [0x80000000-0xffefffff])
[    0.249834] pci_bus 0006:01: root bus resource [bus 01-ff]
[    0.273726] PCI: Probing PCI hardware done
[    0.285596] vgaarb: device added: PCI:0003:02:00.0,decodes=io+mem,owns=none,locks=none
[    0.285598] vgaarb: loaded
[    0.285600] vgaarb: bridge control possible 0003:02:00.0
[    0.285920] SCSI subsystem initialized
[    0.286010] libata version 3.00 loaded.
[    0.286057] usbcore: registered new interface driver usbfs
[    0.286069] usbcore: registered new interface driver hub
[    0.286139] usbcore: registered new device driver usb
[    0.286526] NetLabel: Initializing
[    0.286528] NetLabel:  domain hash size = 128
[    0.286529] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.286541] NetLabel:  unlabeled traffic allowed by default
[    0.286675] clocksource: Switched to clocksource timebase
[    0.296821] AppArmor: AppArmor Filesystem Enabled
[    0.299789] NET: Registered protocol family 2
[    0.300038] TCP established hash table entries: 65536 (order: 7, 524288 bytes)
[    0.300350] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.300704] TCP: Hash tables configured (established 65536 bind 65536)
[    0.300739] UDP hash table entries: 4096 (order: 5, 131072 bytes)
[    0.300798] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
[    0.300913] NET: Registered protocol family 1
[    0.411029] pci 0001:00:01.2: enabling device (0140 -> 0142)
[    0.411599] pci 0003:01:00.0: TI XIO2000a quirk detected; secondary bus fast back-to-back transfers disabled
[    0.411894] PCI: CLS 128 bytes, default 128
[    0.411950] Trying to unpack rootfs image as initramfs...
[    1.004602] Freeing initrd memory: 36000K (c000000005380000 - c0000000076a8000)
[    1.004876] RTAS daemon started
[    1.005556] RTAS: event: 17, Type: EPOW, Severity: 1
[    1.023158] futex hash table entries: 4096 (order: 7, 524288 bytes)
[    1.023322] audit: initializing netlink subsys (disabled)
[    1.023339] audit: type=2000 audit(1470975771.016:1): initialized
[    1.024013] Initialise system trusted keyring
[    1.024251] HugeTLB registered 64 KB page size, pre-allocated 0 pages
[    1.024253] HugeTLB registered 16 MB page size, pre-allocated 0 pages
[    1.024255] HugeTLB registered 16 GB page size, pre-allocated 0 pages
[    1.026191] zbud: loaded
[    1.026466] VFS: Disk quotas dquot_6.6.0
[    1.026509] VFS: Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.026882] squashfs: version 4.0 (2009/01/31) Phillip Lougher
[    1.027148] fuse init (API version 7.23)
[    1.027323] Key type big_key registered
[    1.027346] Allocating IMA MOK and blacklist keyrings.
[    1.028078] Key type asymmetric registered
[    1.028086] Asymmetric key parser 'x509' registered
[    1.028170] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 249)
[    1.028278] io scheduler noop registered
[    1.028281] io scheduler deadline registered (default)
[    1.028328] io scheduler cfq registered
[    1.028423] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.028430] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.028530] Using unsupported 640x480 display at 3c0478000000, depth=8, pitch=640
[    1.039749] Console: switching to colour frame buffer device 80x30
[    1.050844] fb0: Open Firmware frame buffer device on /pci@800000020000204/pci@0/display@0
[    1.051464] HVSI: registered 2 devices
[    1.051474] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.053226] pmac_zilog: 0.6 (Benjamin Herrenschmidt <benh@kernel.crashing.org>)
[    1.053366] Linux agpgart interface v0.103
[    1.057640] brd: module loaded
[    1.060242] loop: module loaded
[    1.060651] libphy: Fixed MDIO Bus: probed
[    1.060655] tun: Universal TUN/TAP device driver, 1.6
[    1.060657] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.060719] PPP generic driver version 2.4.2
[    1.060799] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.060815] ehci-pci: EHCI PCI platform driver
[    1.061351] ehci-pci 0001:00:01.2: EHCI Host Controller
[    1.061359] ehci-pci 0001:00:01.2: new USB bus registered, assigned bus number 1
[    1.061802] ehci-pci 0001:00:01.2: irq 323, io mem 0x3c00ffffd000
[    1.070678] ehci-pci 0001:00:01.2: USB 2.0 started, EHCI 1.00
[    1.070745] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    1.070748] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.070751] usb usb1: Product: EHCI Host Controller
[    1.070753] usb usb1: Manufacturer: Linux 4.4.0-34-powerpc64-smp ehci_hcd
[    1.070756] usb usb1: SerialNumber: 0001:00:01.2
[    1.070918] hub 1-0:1.0: USB hub found
[    1.070928] hub 1-0:1.0: 5 ports detected
[    1.071163] ehci-platform: EHCI generic platform driver
[    1.071176] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.071190] ohci-pci: OHCI PCI platform driver
[    1.071680] ohci-pci 0001:00:01.0: OHCI PCI host controller
[    1.071687] ohci-pci 0001:00:01.0: new USB bus registered, assigned bus number 2
[    1.071778] ohci-pci 0001:00:01.0: irq 321, io mem 0x3c00ffffe000
[    1.156746] usb usb2: New USB device found, idVendor=1d6b, idProduct=0001
[    1.156749] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.156751] usb usb2: Product: OHCI PCI host controller
[    1.156753] usb usb2: Manufacturer: Linux 4.4.0-34-powerpc64-smp ohci_hcd
[    1.156755] usb usb2: SerialNumber: 0001:00:01.0
[    1.156876] hub 2-0:1.0: USB hub found
[    1.156885] hub 2-0:1.0: 3 ports detected
[    1.157425] ohci-pci 0001:00:01.1: OHCI PCI host controller
[    1.157432] ohci-pci 0001:00:01.1: new USB bus registered, assigned bus number 3
[    1.157507] ohci-pci 0001:00:01.1: irq 322, io mem 0x3c00fffff000
[    1.240725] usb usb3: New USB device found, idVendor=1d6b, idProduct=0001
[    1.240728] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.240730] usb usb3: Product: OHCI PCI host controller
[    1.240732] usb usb3: Manufacturer: Linux 4.4.0-34-powerpc64-smp ohci_hcd
[    1.240733] usb usb3: SerialNumber: 0001:00:01.1
[    1.240854] hub 3-0:1.0: USB hub found
[    1.240862] hub 3-0:1.0: 2 ports detected
[    1.240962] ohci-platform: OHCI generic platform driver
[    1.240973] uhci_hcd: USB Universal Host Controller Interface driver
[    1.241201] mousedev: PS/2 mouse device common for all mice
[    1.241259] i2c /dev entries driver
[    1.241377] device-mapper: uevent: version 1.0.3
[    1.241463] device-mapper: ioctl: 4.34.0-ioctl (2015-10-28) initialised: dm-devel@redhat.com
[    1.241732] pseries_idle_driver registered
[    1.241755] ledtrig-cpu: registered to indicate activity on CPUs
[    1.242250] NET: Registered protocol family 10
[    1.242619] NET: Registered protocol family 17
[    1.242640] Key type dns_resolver registered
[    1.242989] registered taskstats version 1
[    1.243015] Loading compiled-in X.509 certificates
[    1.243998] Loaded X.509 cert 'Build time autogenerated kernel key: baaff8c8ed04180934a838772169534a17b051a4'
[    1.244033] zswap: loaded using pool lzo/zbud
[    1.247713] Key type trusted registered
[    1.254760] Key type encrypted registered
[    1.254772] AppArmor: AppArmor sha1 policy hashing enabled
[    1.254780] ima: No TPM chip found, activating TPM-bypass!
[    1.254821] evm: HMAC attrs: 0x1
[    1.257536] hctosys: unable to open rtc device (rtc0)
[    1.257779] PM: Hibernation image not present or could not be loaded.
[    1.259774] Freeing unused kernel memory: 8672K (c000000000f47000 - c0000000017bf000)
[    1.289075] random: systemd-udevd urandom read with 39 bits of entropy available
[    1.346961] ipr: IBM Power RAID SCSI Device Driver version: 2.6.3 (October 17, 2015)
[    1.346996] ipr 0000:00:01.0: Found IOA with IRQ: 305
[    1.347611] ipr 0000:00:01.0: Cannot enable MSI.
[    1.352768] ipr 0000:00:01.0: Starting IOA initialization sequence.
[    1.352786] scsi host0: IBM 0 Storage Adapter
[    1.353370] ipr 0000:00:01.0: Adapter firmware version: 04200020
[    1.356421] ipr 0000:00:01.0: IOA initialized.
[    1.359019] scsi 0:255:255:255: No Device         IBM      572C001SISIOA    0150 PQ: 0 ANSI: 0
[    1.386710] usb 1-1: new high-speed USB device number 2 using ehci-pci
[    1.394142] scsi 0:8:0:0: Enclosure         IBM      VSBPD6E4A  3GSAS   02 PQ: 0 ANSI: 2
[    1.429516] scsi 0:8:1:0: Enclosure         IBM      VSBPD6E4B  3GSAS   03 PQ: 0 ANSI: 2
[    1.532960] usb 1-1: New USB device found, idVendor=0b95, idProduct=7e2b
[    1.532965] usb 1-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    1.532968] usb 1-1: Product: AX88772B
[    1.532970] usb 1-1: Manufacturer: ASIX Elec. Corp.
[    1.532972] usb 1-1: SerialNumber: 05FAF1
[    1.886675] usb 3-1: new low-speed USB device number 2 using ohci-pci
[    2.090713] usb 3-1: New USB device found, idVendor=0430, idProduct=0005
[    2.090716] usb 3-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    2.101566] hidraw: raw HID events driver (C) Jiri Kosina
[    2.109843] usbcore: registered new interface driver usbhid
[    2.109846] usbhid: USB HID core driver
[    2.115031] input: HID 0430:0005 as /devices/pci0001:00/0001:00:01.1/usb3/3-1/3-1:1.0/0003:0430:0005.0001/input/input0
[    2.170831] hid-generic 0003:0430:0005.0001: input,hidraw0: USB HID v1.00 Keyboard [HID 0430:0005] on usb-0001:00:01.1-1/input0
[    2.984277] ata1.00: ATAPI: IBM     RMBO0040532, SA61, max UDMA/100
[    2.986791] ata1.00: configured for UDMA/100
[    2.989874] scsi 0:6:0:0: CD-ROM            IBM      RMBO0040532      SA61 PQ: 0 ANSI: 2
[    2.990867] scsi 0:0:0:0: Direct-Access     HP       EG0300FAWHV      HPDE PQ: 0 ANSI: 5
[    2.998827] scsi 0:255:255:255: Attached scsi generic sg0 type 31
[    2.999024] scsi 0:8:0:0: Attached scsi generic sg1 type 13
[    2.999204] scsi 0:8:1:0: Attached scsi generic sg2 type 13
[    3.002394] sr 0:6:0:0: [sr0] scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    3.002398] cdrom: Uniform CD-ROM driver Revision: 3.20
[    3.002632] sr 0:6:0:0: Attached scsi CD-ROM sr0
[    3.002803] sr 0:6:0:0: Attached scsi generic sg3 type 5
[    3.003157] sd 0:0:0:0: Attached scsi generic sg4 type 0
[    3.003488] sd 0:0:0:0: [sda] 585937500 512-byte logical blocks: (300 GB/279 GiB)
[    3.005222] sd 0:0:0:0: [sda] Write Protect is off
[    3.005226] sd 0:0:0:0: [sda] Mode Sense: cb 00 10 08
[    3.006571] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, supports DPO and FUA
[    3.019313]  sda: sda1 sda2 sda3 < sda5 >
[    3.024222] sd 0:0:0:0: [sda] Attached SCSI disk
[    3.240961] random: nonblocking pool is initialized
[    6.029552] scsi 0:8:0:0: Wrong diagnostic page; asked for 10 got 0
[    9.024766] scsi 0:8:1:0: Wrong diagnostic page; asked for 10 got 0
[    9.027134] ses 0:8:0:0: Attached Enclosure device
[    9.027145] ses 0:8:1:0: Attached Enclosure device
[   10.161576] md: linear personality registered for level -1
[   10.166965] md: multipath personality registered for level -4
[   10.172696] md: raid0 personality registered for level 0
[   10.178885] md: raid1 personality registered for level 1
[   10.250676] raid6: altivecx1 gen()  5137 MB/s
[   10.318673] raid6: altivecx2 gen()  6979 MB/s
[   10.386676] raid6: altivecx4 gen()  7567 MB/s
[   10.454675] raid6: altivecx8 gen()  7519 MB/s
[   10.522699] raid6: int64x1  gen()  1940 MB/s
[   10.590694] raid6: int64x1  xor()  1176 MB/s
[   10.658696] raid6: int64x2  gen()  2612 MB/s
[   10.726682] raid6: int64x2  xor()  1796 MB/s
[   10.794672] raid6: int64x4  gen()  3332 MB/s
[   10.862681] raid6: int64x4  xor()  2238 MB/s
[   10.930672] raid6: int64x8  gen()  2893 MB/s
[   10.998671] raid6: int64x8  xor()  2155 MB/s
[   10.998674] raid6: using algorithm altivecx4 gen() 7567 MB/s
[   10.998677] raid6: using intx1 recovery algorithm
[   10.999817] xor: measuring software checksum speed
[   11.038670]    8regs     : 11376.000 MB/sec
[   11.078671]    8regs_prefetch: 10240.000 MB/sec
[   11.118668]    32regs    : 12061.000 MB/sec
[   11.158671]    32regs_prefetch: 11142.000 MB/sec
[   11.198668]    altivec   : 14580.000 MB/sec
[   11.198672] xor: using function: altivec (14580.000 MB/sec)
[   11.199726] async_tx: api initialized (async)
[   11.207965] md: raid6 personality registered for level 6
[   11.207969] md: raid5 personality registered for level 5
[   11.207971] md: raid4 personality registered for level 4
[   11.221080] md: raid10 personality registered for level 10
[   11.293378] Btrfs loaded
[   11.479236] EXT4-fs (sda2): mounted filesystem with ordered data mode. Opts: (null)
[   12.251402] systemd[1]: systemd 229 running in system mode. (+PAM +AUDIT +SELINUX +IMA +APPARMOR +SMACK +SYSVINIT +UTMP +LIBCRYPTSETUP +GCRYPT +GNUTLS +ACL +XZ -LZ4 +SECCOMP +BLKID +ELFUTILS +KMOD -IDN)
[   12.251868] systemd[1]: Detected architecture ppc64.
[   12.257546] systemd[1]: Set hostname to <tacobell>.
[   13.166464] systemd[1]: Listening on LVM2 metadata daemon socket.
[   13.166958] systemd[1]: Created slice System Slice.
[   13.167011] systemd[1]: Listening on Journal Socket (/dev/log).
[   13.167379] systemd[1]: Created slice system-serial\x2dgetty.slice.
[   13.167411] systemd[1]: Listening on udev Kernel Socket.
[   13.167456] systemd[1]: Listening on udev Control Socket.
[   13.167495] systemd[1]: Listening on Device-mapper event daemon FIFOs.
[   13.167572] systemd[1]: Listening on Journal Audit Socket.
[   13.167727] systemd[1]: Set up automount Arbitrary Executable File Formats File System Automount Point.
[   13.167746] systemd[1]: Reached target User and Group Name Lookups.
[   13.167760] systemd[1]: Reached target Encrypted Volumes.
[   13.167812] systemd[1]: Started Forward Password Requests to Wall Directory Watch.
[   13.167844] systemd[1]: Listening on Syslog Socket.
[   13.168178] systemd[1]: Created slice User and Session Slice.
[   13.168192] systemd[1]: Reached target Slices.
[   13.168220] systemd[1]: Listening on LVM2 poll daemon socket.
[   13.168260] systemd[1]: Listening on /dev/initctl Compatibility Named Pipe.
[   13.168305] systemd[1]: Listening on Journal Socket.
[   13.186881] systemd[1]: Starting Create list of required static device nodes for the current kernel...
[   13.188130] systemd[1]: Mounting POSIX Message Queue File System...
[   13.189362] systemd[1]: Mounting Debug File System...
[   13.190555] systemd[1]: Starting Set console keymap...
[   13.191780] systemd[1]: Starting Journal Service...
[   13.302884] systemd[1]: Starting Load Kernel Modules...
[   13.303863] systemd[1]: Mounting Huge Pages File System...
[   13.304859] systemd[1]: Started Read required files in advance.
[   13.307119] systemd[1]: Starting Nameserver information manager...
[   13.308104] systemd[1]: Starting Uncomplicated firewall...
[   13.309553] systemd[1]: Starting Monitoring of LVM2 mirrors, snapshots etc. using dmeventd or progress polling...
[   13.309656] systemd[1]: Listening on fsck to fsckd communication Socket.
[   13.331874] systemd[1]: Started Create list of required static device nodes for the current kernel.
[   13.360677] systemd[1]: Starting Create Static Device Nodes in /dev...
[   13.593634] systemd[1]: Started Journal Service.
[   13.617835] Loading iSCSI transport class v2.0-870.
[   13.813701] iscsi: registered transport (tcp)
[   14.439835] iscsi: registered transport (iser)
[   14.841195] EXT4-fs (sda2): re-mounted. Opts: errors=remount-ro
[   14.953290] systemd-journald[1065]: Received request to flush runtime journal from PID 1
[   16.436494] rtc-generic rtc-generic: rtc core: registered rtc-generic as rtc0
[   16.539279] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   17.291223] audit: type=1400 audit(1470975787.280:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/lxc-start" pid=2356 comm="apparmor_parser"
[   17.298681] audit: type=1400 audit(1470975787.284:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/tcpdump" pid=2360 comm="apparmor_parser"
[   17.303732] audit: type=1400 audit(1470975787.292:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=2355 comm="apparmor_parser"
[   17.303746] audit: type=1400 audit(1470975787.292:5): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=2355 comm="apparmor_parser"
[   17.303758] audit: type=1400 audit(1470975787.292:6): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-helper" pid=2355 comm="apparmor_parser"
[   17.303769] audit: type=1400 audit(1470975787.292:7): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=2355 comm="apparmor_parser"
[   17.306563] audit: type=1400 audit(1470975787.292:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/snapd/snap-confine" pid=2358 comm="apparmor_parser"
[   17.307310] audit: type=1400 audit(1470975787.300:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="lxc-container-default" pid=2354 comm="apparmor_parser"
[   17.307326] audit: type=1400 audit(1470975787.300:10): apparmor="STATUS" operation="profile_load" profile="unconfined" name="lxc-container-default-cgns" pid=2354 comm="apparmor_parser"
[   17.307339] audit: type=1400 audit(1470975787.300:11): apparmor="STATUS" operation="profile_load" profile="unconfined" name="lxc-container-default-with-mounting" pid=2354 comm="apparmor_parser"
[   17.331821] Adding 11890684k swap on /dev/sda5.  Priority:-1 extents:1 across:11890684k FS
[   17.516893] cgroup: new mount options do not match the existing superblock, will be ignored
[   17.570127] asix 1-1:1.0 eth0: register 'asix' at usb-0001:00:01.2-1, ASIX AX88772 USB 2.0 Ethernet, 9c:eb:e8:06:c6:1e
[   17.570176] usbcore: registered new interface driver asix
[   17.575631] asix 1-1:1.0 enx9cebe806c61e: renamed from eth0
[   18.262681] asix 1-1:1.0 enx9cebe806c61e: link down
[   18.263972] IPv6: ADDRCONF(NETDEV_UP): enx9cebe806c61e: link is not ready
[   19.368693] IPv6: ADDRCONF(NETDEV_CHANGE): enx9cebe806c61e: link becomes ready
[   19.369426] asix 1-1:1.0 enx9cebe806c61e: link up, 100Mbps, full-duplex, lpa 0xCDE1
[   24.676487] genirq: Flags mismatch irq 16. 00000000 (hvc_console) vs. 00000000 (hvsi)
[   24.676921] hvc_open: request_irq failed with rc -16.


```
lspci output:
```
0000:00:01.0 RAID bus controller: IBM Obsidian chipset SCSI controller (rev 03)
0001:00:01.0 USB controller: NEC Corporation OHCI USB Controller (rev 43)
0001:00:01.1 USB controller: NEC Corporation OHCI USB Controller (rev 43)
0001:00:01.2 USB controller: NEC Corporation uPD72010x USB 2.0 Controller (rev 04)
0003:01:00.0 PCI bridge: Texas Instruments XIO2000(A)/XIO2200A PCI Express-to-PCI Bridge (rev 03)
0003:02:00.0 VGA compatible controller: Matrox Electronics Systems Ltd. Millennium G550 (rev 01)


```

---

### Post by darkod on 2016-08-12
You might be missing the driver if it's not included for the adapter model. But I have no idea where exactly to search, try Google first.

---

### Post by pa8600 on 2016-08-12
> **darkod said:**
> You might be missing the driver if it's not included for the adapter model. But I have no idea where exactly to search, try Google first.

The driver's in the kernel sources, but it's not built at all in Ubuntu PPC for some reason.

I just filed a bug, since everything else in the machine is supported and works otherwise.

---

### Post by MAFoElffen on 2016-08-13
Need info... The 4 vertical RJ-45 ports on the back of your server is an IBM IVE daughter card. IVE stands for Integrated Virtual Ethernet. The other 2 RJ-45 ports are the HMC (hardware management console) ports. The note they have in their manual is that if you have a cable plugged into one of those parts, that it turns off the IVE ports.

Lets just say that the IVE is Special and needs drivers. They are not default as separate ports, but as a network pool or as pooled bridge connections for virtual networks. There are Rhel and Suse drivers for it... and a whole chapter on their configuration.
[http://www.redbooks.ibm.com/redpapers/pdfs/redp4984.pdf](http://www.redbooks.ibm.com/redpapers/pdfs/redp4984.pdf)

What was referred to as network LAN adapters in section 2.7.3 of that tech manual (for the host to connect to it's network), are via PCIe NIC cards... Those network cards, the Lnux Distro's have a better chance of finding and supporting. Look on page 7, figure 1-3.

EDIT--
That make more sense now? I'm not possitive on that, but (1) I don't see Ubuntu support for IBM Power7, but see it on IBM Power8. (2) Since Debian is upstream from Ubuntu, It is curious that you say that works, but Ubuntu does not, when I do not see a IVE driver in Debian either. (3) I saw your bug here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1612725](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1612725)

---

