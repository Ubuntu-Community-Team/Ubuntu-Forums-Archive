---
title: "Ubuntu 11.10 as XEN guest, kernel 3.0.0 network issue"
date: 2012-01-26
forum: Virtualisation
---

### Post by Max Planck on 2012-01-26
I have purchased a XEN-based VPS hosting. It came with Ubuntu 10.04 LTS preinstalled, I upgraded to Ubuntu 11.10. Everything is ok --except that when booting with kernel 3.0.0-15-virtual I get no internet connection. At boot I get "Waiting for network configuration..." and "Waiting up to 60 more seconds for network configuration...", then it just moves on.

If I boot with kernel 2.6.35-32-virtual everything is ok.
I'll be using 2.6 anyway, but I wonder if that's just a configuration issue on my side or is it a known bug. Any help? Thanks!

ifconfig shows only lo interface.

ifup eth0: interface eth0 already configured

/etc/network/interfaces:
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

```

dmesg:
```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.0.0-15-virtual (buildd@crested) (gcc version 4.6.1 (Ubuntu/Linaro 4.6.1-9ubuntu3) ) #26-Ubuntu SMP Fri Jan 20 20:57:08 UTC 2012 (Ubuntu 3.0.0-15.26-virtual 3.0.13)
[    0.000000] Command line: BOOT_IMAGE=/vmlinuz-3.0.0-15-virtual root=/dev/mapper/flame-root ro quiet
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000020000000 (usable)
[    0.000000]  BIOS-e820: 00000000fc000000 - 0000000100000000 (reserved)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI 2.4 present.
[    0.000000] DMI: Xen HVM domU, BIOS 4.0.1 01/13/2011
[    0.000000] Hypervisor detected: Xen HVM
[    0.000000] Xen version 4.0.
[    0.000000] Xen Platform PCI: I/O protocol version 1
[    0.000000] Netfront and the Xen platform PCI driver have been compiled for this kernel: unplug emulated NICs.
[    0.000000] Blkfront and the Xen platform PCI driver have been compiled for this kernel: unplug emulated disks.
[    0.000000] You might have to change the root device
[    0.000000] from /dev/hd[a-d] to /dev/xvd[a-d]
[    0.000000] in your root= kernel command line option
[    0.000000] HVMOP_pagetable_dying not supported
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] No AGP bridge found
[    0.000000] last_pfn = 0x20000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: write-back
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF write-combining
[    0.000000]   C0000-FFFFF write-back
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 00F0000000 mask FFF8000000 uncachable
[    0.000000]   1 base 00F8000000 mask FFFC000000 uncachable
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] found SMP MP-table at [ffff8800000fbc80] fbc80
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] Base memory trampoline at [ffff88000009a000] 9a000 size 20480
[    0.000000] init_memory_mapping: 0000000000000000-0000000020000000
[    0.000000]  0000000000 - 0020000000 page 2M
[    0.000000] kernel direct mapping tables up to 20000000 @ 1fffe000-20000000
[    0.000000] RAMDISK: 1f40e000 - 1f881000
[    0.000000] ACPI: RSDP 00000000000ea020 00024 (v02    Xen)
[    0.000000] ACPI: XSDT 00000000fc012cb0 00034 (v01    Xen      HVM 00000000 HVML 00000000)
[    0.000000] ACPI: FACP 00000000fc012ad0 000F4 (v04    Xen      HVM 00000000 HVML 00000000)
[    0.000000] ACPI: DSDT 00000000fc002c40 0FE0B (v02    Xen      HVM 00000000 INTL 20090123)
[    0.000000] ACPI: FACS 00000000fc002c00 00040
[    0.000000] ACPI: APIC 00000000fc012bd0 000D8 (v02    Xen      HVM 00000000 HVML 00000000)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-0000000020000000
[    0.000000] Initmem setup node 0 0000000000000000-0000000020000000
[    0.000000]   NODE_DATA [000000001fffb000 - 000000001fffffff]
[    0.000000]  [ffffea0000000000-ffffea00007fffff] PMD -> [ffff88001e800000-ffff88001effffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   empty
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x00020000
[    0.000000] On node 0 totalpages: 130959
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 5 pages reserved
[    0.000000]   DMA zone: 3922 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 1736 pages used for memmap
[    0.000000]   DMA32 zone: 125240 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x1f48
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x04] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x06] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x08] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x0a] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x0c] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x0e] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x10] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x09] lapic_id[0x12] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0a] lapic_id[0x14] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0b] lapic_id[0x16] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0c] lapic_id[0x18] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0d] lapic_id[0x1a] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x0e] lapic_id[0x1c] disabled)
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 17, address 0xfec00000, GSI 0-47
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 5 global_irq 5 low level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 10 global_irq 10 low level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 11 global_irq 11 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ5 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ10 used by override.
[    0.000000] ACPI: IRQ11 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 15 CPUs, 13 hotplug CPUs
[    0.000000] nr_irqs_gsi: 64
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 20000000 (gap: 20000000:dc000000)
[    0.000000] Booting paravirtualized kernel on Xen HVM
[    0.000000] setup_percpu: NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:15 nr_node_ids:1
[    0.000000] PERCPU: Embedded 27 pages/cpu @ffff88001fc00000 s79296 r8192 d23104 u131072
[    0.000000] pcpu-alloc: s79296 r8192 d23104 u131072 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 00 01 02 03 04 05 06 07 08 09 10 11 12 13 14 -- 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 129162
[    0.000000] Policy zone: DMA32
[    0.000000] Kernel command line: BOOT_IMAGE=/vmlinuz-3.0.0-15-virtual root=/dev/mapper/flame-root ro quiet
[    0.000000] PID hash table entries: 2048 (order: 2, 16384 bytes)
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 493796k/524288k available (6212k kernel code, 452k absent, 30040k reserved, 6903k data, 900k init)
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=15, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:4352 nr_irqs:1208 16
[    0.000000] Xen HVM callback vector for event delivery is enabled
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 4194304 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Detected 2133.476 MHz processor.
[    0.008000] Calibrating delay loop (skipped), value calculated using timer frequency.. 4266.95 BogoMIPS (lpj=8533904)
[    0.008000] pid_max: default: 32768 minimum: 301
[    0.008000] Security Framework initialized
[    0.008000] AppArmor: AppArmor initialized
[    0.008000] Yama: becoming mindful.
[    0.008000] Dentry cache hash table entries: 65536 (order: 7, 524288 bytes)
[    0.008000] Inode-cache hash table entries: 32768 (order: 6, 262144 bytes)
[    0.008000] Mount-cache hash table entries: 256
[    0.008000] Initializing cgroup subsys cpuacct
[    0.008000] Initializing cgroup subsys memory
[    0.008000] Initializing cgroup subsys devices
[    0.008000] Initializing cgroup subsys freezer
[    0.008000] Initializing cgroup subsys net_cls
[    0.008000] Initializing cgroup subsys blkio
[    0.008000] Initializing cgroup subsys perf_event
[    0.008000] CPU: Physical Processor ID: 0
[    0.008000] CPU: Processor Core ID: 0
[    0.008000] mce: CPU supports 9 MCE banks
[    0.010065] ACPI: Core revision 20110413
[    0.016950] ftrace: allocating 26078 entries in 103 pages
[    0.048095] Switched APIC routing to physical flat.
[    0.052348] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=0 pin2=0
[    0.092767] CPU0: Intel(R) Xeon(R) CPU           E5506  @ 2.13GHz stepping 05
[    0.092779] Xen: using vcpuop timer interface
[    0.092789] installing Xen timer for CPU 0
[    0.092856] Performance Events: unsupported p6 CPU model 26 no PMU driver, software events only.
[    0.093562] register_vcpu_info failed: err=-38
[    0.093575] cpu 1 spinlock event irq 69
[    0.093636] Booting Node   0, Processors  #1
[    0.093638] smpboot cpu 1: start_ip = 9a000
[    0.184076] Brought up 2 CPUs
[    0.184071] installing Xen timer for CPU 1
[    0.184083] Total of 2 processors activated (8532.61 BogoMIPS).
[    0.184560] devtmpfs: initialized
[    0.185628] print_constraints: dummy: 
[    0.185669] Time: 17:44:33  Date: 01/26/12
[    0.185711] NET: Registered protocol family 16
[    0.185865] Trying to unpack rootfs image as initramfs...
[    0.196127] ACPI: bus type pci registered
[    0.196443] PCI: Using configuration type 1 for base access
[    0.197173] bio: create slab <bio-0> at 0
[    0.199807] ACPI: EC: Look up EC in DSDT
[    0.205071] ACPI: Interpreter enabled
[    0.205074] ACPI: (supports S0 S3 S4 S5)
[    0.205089] ACPI: Using IOAPIC for interrupt routing
[    0.277427] ACPI: No dock devices found.
[    0.277432] HEST: Table not found.
[    0.277436] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.277515] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.277640] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7]
[    0.277643] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff]
[    0.277646] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.277648] pci_root PNP0A03:00: host bridge window [mem 0xf0000000-0xfbffffff]
[    0.277819] pci 0000:00:00.0: [8086:1237] type 0 class 0x000600
[    0.279172] pci 0000:00:01.0: [8086:7000] type 0 class 0x000601
[    0.281125] pci 0000:00:01.1: [8086:7010] type 0 class 0x000101
[    0.282243] pci 0000:00:01.1: reg 20: [io  0xc220-0xc22f]
[    0.283165] pci 0000:00:01.2: [8086:7020] type 0 class 0x000c03
[    0.284340] pci 0000:00:01.2: reg 20: [io  0xc200-0xc21f]
[    0.285078] pci 0000:00:01.3: [8086:7113] type 0 class 0x000680
[    0.285111] * Found PM-Timer Bug on the chipset. Due to workarounds for a bug,
[    0.285112] * this clock source is slow. Consider trying other clock sources
[    0.286620] Freeing initrd memory: 4556k freed
[    0.286770] pci 0000:00:01.3: quirk: [io  0x1f40-0x1f7f] claimed by PIIX4 ACPI
[    0.287370] pci 0000:00:02.0: [1013:00b8] type 0 class 0x000300
[    0.287681] pci 0000:00:02.0: reg 10: [mem 0xf0000000-0xf1ffffff pref]
[    0.287927] pci 0000:00:02.0: reg 14: [mem 0xf3000000-0xf3000fff]
[    0.289524] pci 0000:00:03.0: [5853:0001] type 0 class 0x00ff80
[    0.289952] pci 0000:00:03.0: reg 10: [io  0xc000-0xc0ff]
[    0.290267] pci 0000:00:03.0: reg 14: [mem 0xf2000000-0xf2ffffff pref]
[    0.294290] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.294706]  pci0000:00: Unable to request _OSC control (_OSC support mask: 0x1e)
[    0.491382] ACPI: PCI Interrupt Link [LNKA] (IRQs *5 10 11)
[    0.491610] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 *10 11)
[    0.491816] ACPI: PCI Interrupt Link [LNKC] (IRQs 5 10 *11)
[    0.492017] ACPI: PCI Interrupt Link [LNKD] (IRQs *5 10 11)
[    0.492135] xen/balloon: Initialising balloon driver.
[    0.492139] last_pfn = 0x20000 max_arch_pfn = 0x400000000
[    0.492157] xen-balloon: Initialising balloon driver.
[    0.492288] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.492292] vgaarb: loaded
[    0.492293] vgaarb: bridge control possible 0000:00:02.0
[    0.492476] SCSI subsystem initialized
[    0.492523] libata version 3.00 loaded.
[    0.492523] usbcore: registered new interface driver usbfs
[    0.492523] usbcore: registered new interface driver hub
[    0.492523] usbcore: registered new device driver usb
[    0.492523] PCI: Using ACPI for IRQ routing
[    0.492523] PCI: pci_cache_line_size set to 64 bytes
[    0.492606] reserve RAM buffer: 000000000009fc00 - 000000000009ffff 
[    0.492715] NetLabel: Initializing
[    0.492717] NetLabel:  domain hash size = 128
[    0.492718] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.492728] NetLabel:  unlabeled traffic allowed by default
[    0.492765] Switching to clocksource xen
[    0.493092] Switched to NOHz mode on CPU #0
[    0.494612] Switched to NOHz mode on CPU #1
[    0.497674] AppArmor: AppArmor Filesystem Enabled
[    0.497707] pnp: PnP ACPI init
[    0.497720] ACPI: bus type pnp registered
[    0.497748] pnp 00:00: [mem 0x00000000-0x0009ffff]
[    0.497778] system 00:00: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.497782] system 00:00: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.497869] pnp 00:01: [bus 00-ff]
[    0.497871] pnp 00:01: [io  0x0cf8-0x0cff]
[    0.497873] pnp 00:01: [io  0x0000-0x0cf7 window]
[    0.497875] pnp 00:01: [io  0x0d00-0xffff window]
[    0.497877] pnp 00:01: [mem 0x000a0000-0x000bffff window]
[    0.497879] pnp 00:01: [mem 0xf0000000-0xfbffffff window]
[    0.497910] pnp 00:01: Plug and Play ACPI device, IDs PNP0a03 (active)
[    0.497919] pnp 00:02: [io  0x10c0-0x1141]
[    0.497920] pnp 00:02: [io  0xb044-0xb047]
[    0.497943] system 00:02: [io  0x10c0-0x1141] has been reserved
[    0.497945] system 00:02: [io  0xb044-0xb047] has been reserved
[    0.497948] system 00:02: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.497980] pnp 00:03: [io  0x0010-0x001f]
[    0.497982] pnp 00:03: [io  0x0022-0x002d]
[    0.497983] pnp 00:03: [io  0x0030-0x003f]
[    0.497985] pnp 00:03: [io  0x0044-0x005f]
[    0.497987] pnp 00:03: [io  0x0062-0x0063]
[    0.497988] pnp 00:03: [io  0x0065-0x006f]
[    0.497990] pnp 00:03: [io  0x0072-0x007f]
[    0.497992] pnp 00:03: [io  0x0080]
[    0.497994] pnp 00:03: [io  0x0084-0x0086]
[    0.497995] pnp 00:03: [io  0x0088]
[    0.497997] pnp 00:03: [io  0x008c-0x008e]
[    0.497999] pnp 00:03: [io  0x0090-0x009f]
[    0.498000] pnp 00:03: [io  0x00a2-0x00bd]
[    0.498005] pnp 00:03: [io  0x00e0-0x00ef]
[    0.498007] pnp 00:03: [io  0x08a0-0x08a3]
[    0.498009] pnp 00:03: [io  0x0cc0-0x0ccf]
[    0.498010] pnp 00:03: [io  0x04d0-0x04d1]
[    0.498039] system 00:03: [io  0x08a0-0x08a3] has been reserved
[    0.498042] system 00:03: [io  0x0cc0-0x0ccf] has been reserved
[    0.498044] system 00:03: [io  0x04d0-0x04d1] has been reserved
[    0.498047] system 00:03: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.498058] pnp 00:04: [dma 4]
[    0.498060] pnp 00:04: [io  0x0000-0x000f]
[    0.498062] pnp 00:04: [io  0x0081-0x0083]
[    0.498063] pnp 00:04: [io  0x0087]
[    0.498065] pnp 00:04: [io  0x0089-0x008b]
[    0.498067] pnp 00:04: [io  0x008f]
[    0.498068] pnp 00:04: [io  0x00c0-0x00df]
[    0.498070] pnp 00:04: [io  0x0480-0x048f]
[    0.498090] pnp 00:04: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.498100] pnp 00:05: [io  0x0070-0x0071]
[    0.498133] pnp 00:05: [irq 8]
[    0.498152] pnp 00:05: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.498160] pnp 00:06: [io  0x0061]
[    0.498178] pnp 00:06: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.498215] pnp 00:07: [irq 12]
[    0.498236] pnp 00:07: Plug and Play ACPI device, IDs PNP0f13 (active)
[    0.498251] pnp 00:08: [io  0x0060]
[    0.498252] pnp 00:08: [io  0x0064]
[    0.498273] pnp 00:08: [irq 1]
[    0.498293] pnp 00:08: Plug and Play ACPI device, IDs PNP0303 PNP030b (active)
[    0.498308] pnp 00:09: [io  0x03f0-0x03f5]
[    0.498310] pnp 00:09: [io  0x03f7]
[    0.498330] pnp 00:09: [irq 6]
[    0.498332] pnp 00:09: [dma 2]
[    0.498356] pnp 00:09: Plug and Play ACPI device, IDs PNP0700 (active)
[    0.498382] pnp 00:0a: [io  0x03f8-0x03ff]
[    0.498403] pnp 00:0a: [irq 4]
[    0.498425] pnp 00:0a: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.498458] pnp 00:0b: [io  0x0378-0x037f]
[    0.498480] pnp 00:0b: [irq 7]
[    0.498502] pnp 00:0b: Plug and Play ACPI device, IDs PNP0400 (active)
[    0.516803] pnp: PnP ACPI: found 12 devices
[    0.516805] ACPI: ACPI bus type pnp unregistered
[    0.522715] PCI: max bus depth: 0 pci_try_num: 1
[    0.522722] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.522724] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.522727] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.522729] pci_bus 0000:00: resource 7 [mem 0xf0000000-0xfbffffff]
[    0.522769] NET: Registered protocol family 2
[    0.522843] IP route cache hash table entries: 4096 (order: 3, 32768 bytes)
[    0.523037] TCP established hash table entries: 16384 (order: 6, 262144 bytes)
[    0.523121] TCP bind hash table entries: 16384 (order: 6, 262144 bytes)
[    0.523177] TCP: Hash tables configured (established 16384 bind 16384)
[    0.523179] TCP reno registered
[    0.523183] UDP hash table entries: 256 (order: 1, 8192 bytes)
[    0.523189] UDP-Lite hash table entries: 256 (order: 1, 8192 bytes)
[    0.523315] NET: Registered protocol family 1
[    0.523324] pci 0000:00:00.0: Limiting direct PCI/PCI transfers
[    0.523384] pci 0000:00:01.0: PIIX3: Enabling Passive Release
[    0.523448] pci 0000:00:01.0: Activating ISA DMA hang workarounds
[    0.523762] pci 0000:00:02.0: Boot video device
[    0.523824] PCI: CLS 0 bytes, default 64
[    0.524229] audit: initializing netlink socket (disabled)
[    0.524238] type=2000 audit(1327599876.071:1): initialized
[    0.549223] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.550939] VFS: Disk quotas dquot_6.5.2
[    0.551006] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.551648] fuse init (API version 7.16)
[    0.551740] msgmni has been set to 973
[    0.552276] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.552320] io scheduler noop registered
[    0.552322] io scheduler deadline registered (default)
[    0.552366] io scheduler cfq registered
[    0.552443] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.552468] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.552517] efifb: probing for efifb
[    0.552651] efifb: framebuffer at 0xf0000000, mapped to 0xffffc90000180000, using 1408k, total 1408k
[    0.552654] efifb: mode is 800x600x24, linelength=2400, pages=1
[    0.552655] efifb: scrolling: redraw
[    0.552657] efifb: Truecolor: size=0:8:8:8, shift=0:16:8:0
[    0.555715] Console: switching to colour frame buffer device 100x37
[    0.557839] fb0: EFI VGA frame buffer device
[    0.557902] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    0.557907] ACPI: Power Button [PWRF]
[    0.557957] input: Sleep Button as /devices/LNXSYSTM:00/LNXSLPBN:00/input/input1
[    0.557960] ACPI: Sleep Button [SLPF]
[    0.557982] ACPI: acpi_idle registered with cpuidle
[    0.581162] ERST: Table is not found!
[    0.581261] xen-platform-pci 0000:00:03.0: PCI INT A -> GSI 28 (level, low) -> IRQ 28
[    0.581306] Grant table initialized
[    0.582901] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.610678] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.776242] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.780169] Linux agpgart interface v0.103
[    0.781205] brd: module loaded
[    0.781698] loop: module loaded
[    0.786798] blkfront device/vbd/768 num-ring-pages 1 nr_ents 32.
[    0.787508] vbd vbd-5632: 19 xenbus_dev_probe on device/vbd/5632
[    0.796625] ata_piix 0000:00:01.1: version 2.13
[    0.796965] ata_piix 0000:00:01.1: setting latency timer to 64
[    0.797673] scsi0 : ata_piix
[    0.797776] scsi1 : ata_piix
[    0.797813] ata1: PATA max MWDMA2 cmd 0x1f0 ctl 0x3f6 bmdma 0xc220 irq 14
[    0.797815] ata2: PATA max MWDMA2 cmd 0x170 ctl 0x376 bmdma 0xc228 irq 15
[    0.798082] Fixed MDIO Bus: probed
[    0.798104] PPP generic driver version 2.4.2
[    0.798153] Initialising Xen virtual ethernet driver.
[    0.804539] blkfront: xvda: barrier or flush: disabled
[    0.806158] tun: Universal TUN/TAP device driver, 1.6
[    0.806160] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.806257] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.806271] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.806279] uhci_hcd: USB Universal Host Controller Interface driver
[    0.806425] uhci_hcd 0000:00:01.2: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    0.806557] uhci_hcd 0000:00:01.2: setting latency timer to 64
[    0.806614] uhci_hcd 0000:00:01.2: UHCI Host Controller
[    0.806663] uhci_hcd 0000:00:01.2: new USB bus registered, assigned bus number 1
[    0.807141] uhci_hcd 0000:00:01.2: irq 23, io base 0x0000c200
[    0.808204] hub 1-0:1.0: USB hub found
[    0.808209] hub 1-0:1.0: 2 ports detected
[    0.808534] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.810393] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.810400] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.810470] mousedev: PS/2 mouse device common for all mice
[    0.810684] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    0.810748] rtc0: alarms up to one day, 114 bytes nvram
[    0.810850] device-mapper: uevent: version 1.0.3
[    0.810922] device-mapper: ioctl: 4.20.0-ioctl (2011-02-02) initialised: dm-devel@redhat.com
[    0.810929] cpuidle: using governor ladder
[    0.810930] cpuidle: using governor menu
[    0.810932] EFI Variables Facility v0.08 2004-May-17
[    0.811163] TCP cubic registered
[    0.811280] NET: Registered protocol family 10
[    0.811947] NET: Registered protocol family 17
[    0.811961] Registering the dns_resolver key type
[    0.812067] PM: Hibernation image not present or could not be loaded.
[    0.812081] registered taskstats version 1
[    0.812699] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[    0.815692]  xvda: xvda1 xvda2 < xvda5 >
[    0.816282] vif vif-0: 2 parsing device/vif/0/mac
[    0.916033] XENBUS: Device with no driver: device/vfb/0
[    0.916037] XENBUS: Device with no driver: device/console/0
[    0.916040] XENBUS: Device with no driver: device/vbd/5632
[    0.916064]   Magic number: 12:410:745
[    0.916172] rtc_cmos 00:05: setting system clock to 2012-01-26 17:44:34 UTC (1327599874)
[    0.916199] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.916201] EDD information not available.
[    0.957473] ata2.01: NODEV after polling detection
[    0.958297] ata2.00: ATAPI: QEMU DVD-ROM, 0.10.2, max UDMA/100
[    0.959667] ata2.00: configured for MWDMA2
[    0.961807] scsi 1:0:0:0: CD-ROM            QEMU     QEMU DVD-ROM     0.10 PQ: 0 ANSI: 5
[    0.965959] sr0: scsi3-mmc drive: 4x/4x xa/form2 tray
[    0.965962] cdrom: Uniform CD-ROM driver Revision: 3.20
[    0.966068] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    0.966127] sr 1:0:0:0: Attached scsi generic sg0 type 5
[    0.967843] Freeing unused kernel memory: 900k freed
[    0.968072] Write protecting the kernel read-only data: 12288k
[    0.974570] Freeing unused kernel memory: 1960k freed
[    0.979467] Freeing unused kernel memory: 1364k freed
[    0.996172] udevd[86]: starting version 173
[    1.102374] FDC 0 is a S82078B
[    1.120035] usb 1-2: new full speed USB device number 2 using uhci_hcd
[    1.236938] EXT4-fs (dm-0): mounted filesystem with ordered data mode. Opts: (null)
[    1.524049] Refined TSC clocksource calibration: 2133.410 MHz.
[    3.513036] Adding 905212k swap on /dev/mapper/flame-swap_1.  Priority:-1 extents:1 across:905212k 
[    3.541543] udevd[328]: starting version 173
[    3.608787] lp: driver loaded but no devices found
[    3.624676] EXT4-fs (dm-0): re-mounted. Opts: errors=remount-ro
[    3.719603] type=1400 audit(1327599877.297:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=475 comm="apparmor_parser"
[    3.719986] type=1400 audit(1327599877.297:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=475 comm="apparmor_parser"
[    3.720255] type=1400 audit(1327599877.301:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=475 comm="apparmor_parser"
[    3.826857] parport_pc 00:0b: reported by Plug and Play ACPI
[    3.827797] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[    3.912465] lp0: using parport0 (interrupt-driven).
[    3.977707] ppdev: user-space parallel port driver
[    4.203995] input: ImExPS/2 Generic Explorer Mouse as /devices/platform/i8042/serio1/input/input3
[  123.877712] type=1400 audit(1327599997.457:5): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=787 comm="apparmor_parser"
[  123.877837] type=1400 audit(1327599997.457:6): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=786 comm="apparmor_parser"
[  123.878230] type=1400 audit(1327599997.457:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=786 comm="apparmor_parser"
[  123.878478] type=1400 audit(1327599997.457:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=786 comm="apparmor_parser"
[  123.918508] init: rc-sysinit main process (768) killed by TERM signal
[  123.919405] init: apport pre-start process (811) terminated with status 1
[  123.926821] init: apport post-stop process (829) terminated with status 1

```

---

### Post by Max Planck on 2012-01-27
Tried to configure a static ip interface instead of dhcp. Again, it works in 2.6.xx but not in 3.x. I even tried 3.1 and 3.2 kernels, same problem.

ifup eth0 now returns: RTNETLINK answers: File exists. Failed to bring up eth0.

However I discovered that in 3.x my "virtual" eth0 MAC address is empty: 00:00:00:00:00:00, where in 2.6 I have a "real" address.
A message on the XEN mailing list [1] makes me think this is an issue on my hosting provider side.


[1] [http://old-list-archives.xen.org/archives/html/xen-devel/2011-10/msg02154.html](http://old-list-archives.xen.org/archives/html/xen-devel/2011-10/msg02154.html)

---

