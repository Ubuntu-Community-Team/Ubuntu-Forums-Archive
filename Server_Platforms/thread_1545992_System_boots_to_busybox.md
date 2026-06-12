---
title: "System boots to busybox"
date: 2010-08-04
forum: Server Platforms
---

### Post by akester on 2010-08-04
The system is an old AMD Duron 650MHz that was dug out of the garbage, trying to set it up as a light duty server.

I installed ubuntu 10.04 with no errors or troubles during the install, however whenever the system is booted it sits at a cursor for about a minute then goes into busybox giving the error "Gave up waiting on root device." and says that the hard drive does not excist.

If I sit at busybox for about another minute and type exit it then boots ubuntu 10.04 with no errors or issues.

I am wondering if this is an issue with the Hard Drive or with grub.

Thanks for any help!

---

### Post by ruffEdgz on 2010-08-04
I'm curious what your /etc/fstab looks like. Do you mind posting that so we can see if anything in there might be causing the mounting of your root filesystem to 'give up'?

Thanks!

---

### Post by akester on 2010-08-04
Thanks for the quick reply!

Here is /etc/fstab
> 
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=5ac7d3a6-5966-4578-8650-41e45199ca9e /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=f0bd844e-3d0f-4e9f-a35e-a9425353b65f none            swap    sw              0       0
As well, here is dmesg.  I'm not sure if this helps, it might be before dmesg starts logging.

> 
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.32-21-generic (buildd@rothera) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 (Ubuntu 2.6.32-21.32-generic 2.6.32.11+drm33.2)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000ec000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000013ff0000 (usable)
[    0.000000]  BIOS-e820: 0000000013ff0000 - 0000000013ff8000 (ACPI data)
[    0.000000]  BIOS-e820: 0000000013ff8000 - 0000000014000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.3 present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0x13ff0 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask FF0000000 write-back
[    0.000000]   1 base 010000000 mask FFC000000 write-back
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009fc00 (usable)
[    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000ec000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 0000000013ff0000 (usable)
[    0.000000]  modified: 0000000013ff0000 - 0000000013ff8000 (ACPI data)
[    0.000000]  modified: 0000000013ff8000 - 0000000014000000 (ACPI NVS)
[    0.000000]  modified: 00000000ffff0000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-0000000013ff0000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0013c00000 page 2M
[    0.000000]  0013c00000 - 0013ff0000 page 4k
[    0.000000] kernel direct mapping tables up to 13ff0000 @ 10000-15000
[    0.000000] RAMDISK: 0e89c000 - 0f033872
[    0.000000] ACPI: RSDP 000fa910 00014 (v00 AMI   )
[    0.000000] ACPI: RSDT 13ff0000 00028 (v01 AMIINT          00000010 MSFT 00000097)
[    0.000000] ACPI: FACP 13ff0030 00074 (v01 AMIINT          00000010 MSFT 00000097)
[    0.000000] ACPI: DSDT 13ff00b0 02951 (v01    VIA   VT8371 00001000 MSFT 0100000B)
[    0.000000] ACPI: FACS 13ff8000 00040
[    0.000000] ACPI: BIOS age (1997) fails cutoff (2000), acpi=force is required to enable ACPI
[    0.000000] ACPI: Disabling ACPI support
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 319MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 13ff0000
[    0.000000]   low ram: 0 - 13ff0000
[    0.000000]   node 0 low ram: 00000000 - 13ff0000
[    0.000000]   node 0 bootmap 00011000 - 00013800
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 0013ff0000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008d9e98]    TEXT DATA BSS ==> [0000100000 - 00008d9e98]
[    0.000000]   #4 [000e89c000 - 000f033872]          RAMDISK ==> [000e89c000 - 000f033872]
[    0.000000]   #5 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #6 [00008da000 - 00008dd0ad]              BRK ==> [00008da000 - 00008dd0ad]
[    0.000000]   #7 [0000010000 - 0000011000]          PGTABLE ==> [0000010000 - 0000011000]
[    0.000000]   #8 [0000011000 - 0000014000]          BOOTMAP ==> [0000011000 - 0000014000]
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x00013ff0
[    0.000000]   HighMem  0x00013ff0 -> 0x00013ff0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x00013ff0
[    0.000000] On node 0 totalpages: 81791
[    0.000000] free_area_init_node: node 0, pgdat c0798720, node_mem_map c1001200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 608 pages used for memmap
[    0.000000]   Normal zone: 77200 pages, LIFO batch:15
[    0.000000] Using APIC driver default
[    0.000000] SFI: Simple Firmware Interface v0.7 [http://simplefirmware.org](http://simplefirmware.org)
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] APIC: disable apic facility
[    0.000000] nr_irqs_gsi: 16
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000ec000
[    0.000000] PM: Registered nosave memory: 00000000000ec000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 14000000 (gap: 14000000:ebff0000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @c1400000 s36024 r0 d21320 u4194304
[    0.000000] pcpu-alloc: s36024 r0 d21320 u4194304 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 81151
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-21-generic root=UUID=5ac7d3a6-5966-4578-8650-41e45199ca9e ro quiet
[    0.000000] PID hash table entries: 2048 (order: 1, 8192 bytes)
[    0.000000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 1637760 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (00000000:00000000)
[    0.000000] Memory: 306352k/327616k available (4673k kernel code, 20484k reserved, 2122k data, 656k init, 0k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xd47f0000 - 0xff7fe000   ( 688 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xd3ff0000   ( 319 MB)
[    0.000000]       .init : 0xc07a3000 - 0xc0847000   ( 656 kB)
[    0.000000]       .data : 0xc0590613 - 0xc07a2e48   (2122 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0590613   (4673 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=32, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] NR_IRQS:2304 nr_irqs:256
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 649.983 MHz processor.
[    0.004015] Calibrating delay loop (skipped), value calculated using timer frequency.. 1299.96 BogoMIPS (lpj=2599932)
[    0.004089] Security Framework initialized
[    0.004193] AppArmor: AppArmor initialized
[    0.004221] Mount-cache hash table entries: 512
[    0.004663] Initializing cgroup subsys ns
[    0.004680] Initializing cgroup subsys cpuacct
[    0.004696] Initializing cgroup subsys memory
[    0.004726] Initializing cgroup subsys devices
[    0.004736] Initializing cgroup subsys freezer
[    0.004745] Initializing cgroup subsys net_cls
[    0.004805] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004816] CPU: L2 Cache: 64K (64 bytes/line)
[    0.004831] mce: CPU supports 4 MCE banks
[    0.004895] Performance Events: AMD PMU driver.
[    0.004945] ... version:                0
[    0.004951] ... bit width:              48
[    0.004958] ... generic registers:      4
[    0.004966] ... value mask:             0000ffffffffffff
[    0.004974] ... max period:             00007fffffffffff
[    0.004982] ... fixed-purpose events:   0
[    0.004989] ... event mask:             000000000000000f
[    0.005004] Checking 'hlt' instruction... OK.
[    0.020208] SMP alternatives: switching to UP code
[    0.038379] Freeing SMP alternatives: 19k freed
[    0.038479] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.038513] ftrace: allocating 21771 entries in 43 pages
[    0.048209] Enabling APIC mode:  Flat.  Using 0 I/O APICs
[    0.048223] weird, boot CPU (#0) not listed by the BIOS.
[    0.048231] SMP motherboard not detected.
[    0.048241] Local APIC not detected. Using dummy APIC emulation.
[    0.048247] SMP disabled
[    0.048993] Brought up 1 CPUs
[    0.049006] Total of 1 processors activated (1299.96 BogoMIPS).
[    0.049487] CPU0 attaching NULL sched-domain.
[    0.050040] devtmpfs: initialized
[    0.051307] regulator: core version 0.5
[    0.051386] Time: 19:59:40  Date: 08/04/10
[    0.051582] NET: Registered protocol family 16
[    0.052073] EISA bus registered
[    0.084678] PCI: PCI BIOS revision 2.10 entry at 0xfdb71, last bus=1
[    0.084689] PCI: Using configuration type 1 for base access
[    0.087930] bio: create slab <bio-0> at 0
[    0.088231] ACPI: Interpreter disabled.
[    0.088474] vgaarb: loaded
[    0.088880] SCSI subsystem initialized
[    0.089135] libata version 3.00 loaded.
[    0.089437] usbcore: registered new interface driver usbfs
[    0.089480] usbcore: registered new interface driver hub
[    0.089591] usbcore: registered new device driver usb
[    0.090061] PCI: Probing PCI hardware
[    0.090074] PCI: Probing PCI hardware (bus 00)
[    0.090211] pci 0000:00:00.0: reg 10 32bit mmio pref: [0xe0000000-0xe3ffffff]
[    0.090263] pci 0000:00:00.0: Disabling VIA memory write queue (PCI ID 0305, rev 02): [55] 89 & 1f -> 09
[    0.090365] pci 0000:00:01.0: supports D1
[    0.090514] pci 0000:00:07.1: reg 20 io port: [0xffa0-0xffaf]
[    0.090614] pci 0000:00:07.2: reg 20 io port: [0xc000-0xc01f]
[    0.090709] pci 0000:00:07.3: reg 20 io port: [0xc400-0xc41f]
[    0.090834] pci 0000:00:07.4: quirk: region 0800-08ff claimed by vt82c586 ACPI
[    0.090847] pci 0000:00:07.4: quirk: region 0c00-0c7f claimed by vt82c686 HW-mon
[    0.090858] pci 0000:00:07.4: quirk: region 0400-040f claimed by vt82c686 SMB
[    0.090927] pci 0000:00:07.5: reg 10 io port: [0xd000-0xd0ff]
[    0.090941] pci 0000:00:07.5: reg 14 io port: [0xcc00-0xcc03]
[    0.090955] pci 0000:00:07.5: reg 18 io port: [0xc800-0xc803]
[    0.091057] pci 0000:00:0f.0: reg 10 io port: [0xbc00-0xbcff]
[    0.091071] pci 0000:00:0f.0: reg 14 32bit mmio: [0xdfffff00-0xdfffffff]
[    0.091121] pci 0000:00:0f.0: supports D1 D2
[    0.091130] pci 0000:00:0f.0: PME# supported from D1 D2 D3hot D3cold
[    0.091140] pci 0000:00:0f.0: PME# disabled
[    0.091229] pci 0000:01:00.0: reg 10 32bit mmio: [0xd8000000-0xdbffffff]
[    0.091265] pci 0000:01:00.0: reg 30 32bit mmio pref: [0xdfef0000-0xdfefffff]
[    0.091296] pci 0000:01:00.0: supports D1 D2
[    0.091352] pci 0000:00:01.0: bridge io port: [0x9000-0x9fff]
[    0.091363] pci 0000:00:01.0: bridge 32bit mmio: [0xd7e00000-0xdfefffff]
[    0.091376] pci 0000:00:01.0: bridge 32bit mmio pref: [0xd7c00000-0xd7cfffff]
[    0.092093] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.092293] pci 0000:00:07.0: VIA IRQ router [1106:0686]
[    0.092730] NetLabel: Initializing
[    0.092738] NetLabel:  domain hash size = 128
[    0.092744] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.092793] NetLabel:  unlabeled traffic allowed by default
[    0.092932] Switching to clocksource tsc
[    0.099273] AppArmor: AppArmor Filesystem Enabled
[    0.099292] pnp: PnP ACPI: disabled
[    0.099306] PnPBIOS: Scanning system for PnP BIOS support...
[    0.099406] PnPBIOS: Found PnP BIOS installation structure at 0xc00f7550
[    0.099417] PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0x63e4, dseg 0xf0000
[    0.100614] PnPBIOS: 13 nodes reported by PnP BIOS; 13 recorded by driver
[    0.100657] system 00:00: iomem range 0x0-0x9fbff could not be reserved
[    0.100670] system 00:00: iomem range 0x9fc00-0x9ffff could not be reserved
[    0.100682] system 00:00: iomem range 0xec000-0xeffff could not be reserved
[    0.100693] system 00:00: iomem range 0xf0000-0xfffff could not be reserved
[    0.100705] system 00:00: iomem range 0x100000-0x13feffff could not be reserved
[    0.100716] system 00:00: iomem range 0x13ff0000-0x13ff7fff could not be reserved
[    0.100728] system 00:00: iomem range 0x13ff8000-0x13ffffff could not be reserved
[    0.100740] system 00:00: iomem range 0xffff0000-0xffffffff has been reserved
[    0.101380] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.101393] pci 0000:00:01.0:   IO window: 0x9000-0x9fff
[    0.101407] pci 0000:00:01.0:   MEM window: 0xd7e00000-0xdfefffff
[    0.101419] pci 0000:00:01.0:   PREFETCH window: 0xd7c00000-0xd7cfffff
[    0.101454] pci 0000:00:01.0: setting latency timer to 64
[    0.101469] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.101479] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.101490] pci_bus 0000:01: resource 0 io:  [0x9000-0x9fff]
[    0.101500] pci_bus 0000:01: resource 1 mem: [0xd7e00000-0xdfefffff]
[    0.101510] pci_bus 0000:01: resource 2 pref mem [0xd7c00000-0xd7cfffff]
[    0.101640] NET: Registered protocol family 2
[    0.101962] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[    0.103005] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    0.103684] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[    0.104441] TCP: Hash tables configured (established 16384 bind 16384)
[    0.104453] TCP reno registered
[    0.104813] NET: Registered protocol family 1
[    0.104880] pci 0000:00:01.0: disabling DAC on VIA PCI bridge
[    0.104896] pci 0000:00:07.0: Disabling VIA external APIC routing
[    0.104970] pci 0000:01:00.0: Boot video device
[    0.105652] cpufreq-nforce2: No nForce2 chipset.
[    0.105732] Scanning for low memory corruption every 60 seconds
[    0.106166] audit: initializing netlink socket (disabled)
[    0.106211] type=2000 audit(1280951980.102:1): initialized
[    0.137917] Trying to unpack rootfs image as initramfs...
[    0.172466] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.183525] VFS: Disk quotas dquot_6.5.2
[    0.183861] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.191188] fuse init (API version 7.13)
[    0.191649] msgmni has been set to 599
[    0.192650] alg: No test for stdrng (krng)
[    0.192841] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.192853] io scheduler noop registered
[    0.192860] io scheduler anticipatory registered
[    0.192867] io scheduler deadline registered
[    0.193017] io scheduler cfq registered (default)
[    0.193368] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.193458] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.204441] isapnp: Scanning for PnP cards...
[    0.210755] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.211106] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.211367] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.212198] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.212532] 00:09: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.265321] brd: module loaded
[    0.267148] loop: module loaded
[    0.267557] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    0.269361] Fixed MDIO Bus: probed
[    0.269491] PPP generic driver version 2.4.2
[    0.269703] tun: Universal TUN/TAP device driver, 1.6
[    0.269712] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.270060] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.270157] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.270203] uhci_hcd: USB Universal Host Controller Interface driver
[    0.270361] PCI: setting IRQ 11 as level-triggered
[    0.270372] uhci_hcd 0000:00:07.2: found PCI INT D -> IRQ 11
[    0.270404] uhci_hcd 0000:00:07.2: sharing IRQ 11 with 0000:00:07.3
[    0.270424] uhci_hcd 0000:00:07.2: sharing IRQ 11 with 0000:00:0f.0
[    0.270455] uhci_hcd 0000:00:07.2: UHCI Host Controller
[    0.270644] uhci_hcd 0000:00:07.2: new USB bus registered, assigned bus number 1
[    0.270708] uhci_hcd 0000:00:07.2: irq 11, io base 0x0000c000
[    0.276453] usb usb1: configuration #1 chosen from 1 choice
[    0.276569] hub 1-0:1.0: USB hub found
[    0.276619] hub 1-0:1.0: 2 ports detected
[    0.276817] uhci_hcd 0000:00:07.3: found PCI INT D -> IRQ 11
[    0.276848] uhci_hcd 0000:00:07.3: sharing IRQ 11 with 0000:00:07.2
[    0.276871] uhci_hcd 0000:00:07.3: sharing IRQ 11 with 0000:00:0f.0
[    0.276906] uhci_hcd 0000:00:07.3: UHCI Host Controller
[    0.277109] uhci_hcd 0000:00:07.3: new USB bus registered, assigned bus number 2
[    0.277168] uhci_hcd 0000:00:07.3: irq 11, io base 0x0000c400
[    0.277553] usb usb2: configuration #1 chosen from 1 choice
[    0.277682] hub 2-0:1.0: USB hub found
[    0.277718] hub 2-0:1.0: 2 ports detected
[    0.278025] PNP: PS/2 Controller [PNP0303] at 0x60,0x64 irq 1
[    0.278035] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    0.278290] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.283879] mice: PS/2 mouse device common for all mice
[    0.284313] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    0.284369] rtc0: alarms up to one day, 114 bytes nvram
[    0.284687] device-mapper: uevent: version 1.0.3
[    0.285281] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[    0.287192] device-mapper: multipath: version 1.1.0 loaded
[    0.287208] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.287893] EISA: Probing bus 0 at eisa.0
[    0.288005] EISA: Detected 0 cards.
[    0.293383] cpuidle: using governor ladder
[    0.293396] cpuidle: using governor menu
[    0.295105] TCP cubic registered
[    0.295645] NET: Registered protocol family 10
[    0.297242] lo: Disabled Privacy Extensions
[    0.298277] NET: Registered protocol family 17
[    0.298437] powernow-k8: Processor cpuid 630 not supported
[    0.298455] Using IPI No-Shortcut mode
[    0.298793] PM: Resume from disk failed.
[    0.298947] registered taskstats version 1
[    0.302618]   Magic number: 6:769:1000
[    0.302700]  pnp1: hash matches
[    0.302777] pnp 00:02: hash matches
[    0.302915] rtc_cmos 00:04: setting system clock to 2010-08-04 19:59:40 UTC (1280951980)
[    0.302928] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.302935] EDD information not available.
[    0.305693] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    0.891246] isapnp: No Plug & Play device found
[    1.339591] Freeing initrd memory: 7774k freed
[    1.371841] Freeing unused kernel memory: 656k freed
[    1.374871] Write protecting the kernel text: 4676k
[    1.375103] Write protecting the kernel read-only data: 1840k
[    1.467749] udev: starting version 151
[    1.847512] pata_via 0000:00:07.1: version 0.3.4
[    1.863613] scsi0 : pata_via
[    1.867419] scsi1 : pata_via
[    1.867959] ata1: PATA max UDMA/66 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    1.867975] ata2: PATA max UDMA/66 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    1.913803] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    1.913880] 8139cp 0000:00:0f.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
[    2.039438] ata1.01: ATAPI: ATAPI   CD-RW 52X24X, MB51, max UDMA/33
[    2.055573] ata1.01: configured for UDMA/33
[    2.057608] scsi 0:0:1:0: CD-ROM            ATAPI    CD-RW 52X24X     MB51 PQ: 0 ANSI: 5
[    2.064542] sr0: scsi3-mmc drive: 52x/52x writer cd/rw xa/form2 cdda tray
[    2.064560] Uniform CD-ROM driver Revision: 3.20
[    2.065868] sr 0:0:1:0: Attached scsi CD-ROM sr0
[    2.066671] sr 0:0:1:0: Attached scsi generic sg0 type 5
[    7.263661] ata2: link is slow to respond, please be patient (ready=0)
[   12.080229] ata2: SRST failed (errno=-16)
[   17.276842] ata2: link is slow to respond, please be patient (ready=0)
[   22.093416] ata2: SRST failed (errno=-16)
[   27.290031] ata2: link is slow to respond, please be patient (ready=0)
[   53.109187] ata2.01: link status unknown, clearing UNKNOWN to NONE
[   53.118151] ata2.00: ATA-4: WDC WD204BA, 16.13M16, max UDMA/66
[   53.118163] ata2.00: 39876480 sectors, multi 16: LBA 
[   53.118234] ata2.00: limited to UDMA/33 due to 40-wire cable
[   53.134119] ata2.00: configured for UDMA/33
[   53.134593] scsi 1:0:0:0: Direct-Access     ATA      WDC WD204BA      16.1 PQ: 0 ANSI: 5
[   53.136469] sd 1:0:0:0: Attached scsi generic sg1 type 0
[   53.137242] sd 1:0:0:0: [sda] 39876480 512-byte logical blocks: (20.4 GB/19.0 GiB)
[   53.137436] sd 1:0:0:0: [sda] Write Protect is off
[   53.137448] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   53.137547] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   53.138195]  sda: sda1 sda2 < sda5 >
[   53.178696] sd 1:0:0:0: [sda] Attached SCSI disk
[   53.204199] 8139too Fast Ethernet driver 0.9.28
[   53.204367] 8139too 0000:00:0f.0: found PCI INT A -> IRQ 11
[   53.204399] 8139too 0000:00:0f.0: sharing IRQ 11 with 0000:00:07.2
[   53.204413] 8139too 0000:00:0f.0: sharing IRQ 11 with 0000:00:07.3
[   53.207205] eth0: RealTek RTL8139 at 0xbc00, 00:17:3f:9b:57:e1, IRQ 11
[  187.829959] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
[  187.829983] EXT4-fs (sda1): write access will be enabled during recovery
[  198.797395] EXT4-fs (sda1): orphan cleanup on readonly fs
[  198.797436] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 1044769
[  198.797767] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 1044767
[  198.797846] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 1044764
[  198.797910] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 1044762
[  198.797972] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 1044760
[  198.798032] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 1044759
[  198.798096] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 1044753
[  198.798279] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 1044493
[  198.798527] EXT4-fs (sda1): 8 orphan inodes deleted
[  198.798541] EXT4-fs (sda1): recovery complete
[  198.962182] EXT4-fs (sda1): mounted filesystem with ordered data mode
[  207.482916] Adding 874488k swap on /dev/sda5.  Priority:-1 extents:1 across:874488k 
[  207.638429] udev: starting version 151
[  208.106223] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[  208.536185] Linux agpgart interface v0.103
[  208.717176] parport_pc: VIA 686A/8231 detected
[  208.717187] parport_pc: probing current configuration
[  208.717216] parport_pc: Current parallel port base: 0x378
[  208.717324] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]
[  208.804205] parport_pc: VIA parallel port: io=0x378, irq=7
[  208.963718] lp0: using parport0 (interrupt-driven).
[  209.019956] agpgart: Detected VIA Twister-K/KT133x/KM133 chipset
[  209.099787] agpgart-via 0000:00:00.0: AGP aperture is 64M @ 0xe0000000
[  209.163302] type=1505 audit(1280952189.356:2):  operation="profile_load" pid=369 name="/sbin/dhclient3"
[  209.164981] type=1505 audit(1280952189.360:3):  operation="profile_load" pid=369 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[  209.165591] type=1505 audit(1280952189.360:4):  operation="profile_load" pid=369 name="/usr/lib/connman/scripts/dhclient-script"
[  209.284969] ppdev: user-space parallel port driver
[  209.336132] vga16fb: initializing
[  209.336160] vga16fb: mapped to 0xc00a0000
[  209.337041] fb0: VGA16 VGA frame buffer device
[  209.867914] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[  210.102276] Console: switching to colour frame buffer device 80x30
[  210.157513] PCI: setting IRQ 10 as level-triggered
[  210.157531] VIA 82xx Audio 0000:00:07.5: found PCI INT C -> IRQ 10
[  210.157747] VIA 82xx Audio 0000:00:07.5: setting latency timer to 64
[  210.765855] type=1505 audit(1280952190.960:5):  operation="profile_replace" pid=491 name="/sbin/dhclient3"
[  210.766882] type=1505 audit(1280952190.960:6):  operation="profile_replace" pid=491 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[  210.767542] type=1505 audit(1280952190.960:7):  operation="profile_replace" pid=491 name="/usr/lib/connman/scripts/dhclient-script"
[  210.862856] type=1505 audit(1280952191.056:8):  operation="profile_load" pid=496 name="/usr/lib/cups/backend/cups-pdf"
[  210.891115] type=1505 audit(1280952191.084:9):  operation="profile_load" pid=496 name="/usr/sbin/cupsd"
[  210.949028] type=1505 audit(1280952191.144:10):  operation="profile_load" pid=503 name="/usr/sbin/tcpdump"
[  212.306817] RPC: Registered udp transport module.
[  212.306832] RPC: Registered tcp transport module.
[  212.306840] RPC: Registered tcp NFSv4.1 backchannel transport module.
[  212.460642] Installing knfsd (copyright (C) 1996 [EMAIL="okir@monad.swb.de"]okir@monad.swb.de[/EMAIL]).
[  212.749796] svc: failed to register lockdv1 RPC service (errno 97).
[  212.757398] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[  212.758050] NFSD: starting 90-second grace period
[  220.628996] eth0: no IPv6 routers present


---

### Post by akester on 2010-08-04
Not to bump, but I also outputted /proc/cmdline and /proc/modules per the busybox suggestions.

/proc/cmdline
> 
BOOT_IMAGE=/boot/vmlinuz-2.6.32-21-generic root=UUID=5ac7d3a6-5966-4578-8650-41e45199ca9e ro quiet


/proc/modules
> 
nfsd 238935 11 - Live 0xd4bec000
lockd 64849 1 nfsd, Live 0xd4b8d000
nfs_acl 2245 1 nfsd, Live 0xd4b6d000
auth_rpcgss 33735 1 nfsd, Live 0xd4b59000
sunrpc 193181 10 nfsd,lockd,nfs_acl,auth_rpcgss, Live 0xd4b08000
exportfs 3437 1 nfsd, Live 0xd4ac1000
snd_via82xx 20058 0 - Live 0xd4a8c000
gameport 9089 1 snd_via82xx, Live 0xd4a77000
snd_ac97_codec 100646 1 snd_via82xx, Live 0xd4a4c000
ac97_bus 1002 1 snd_ac97_codec, Live 0xd4a21000
snd_pcm 70662 2 snd_via82xx,snd_ac97_codec, Live 0xd4a02000
snd_timer 19098 1 snd_pcm, Live 0xd49dc000
snd_page_alloc 7076 2 snd_via82xx,snd_pcm, Live 0xd49a2000
fbcon 35102 71 - Live 0xd498d000
tileblit 2031 1 fbcon, Live 0xd497a000
snd_mpu401_uart 5617 1 snd_via82xx, Live 0xd4957000
font 7557 1 fbcon, Live 0xd493c000
bitblit 4707 1 fbcon, Live 0xd492e000
softcursor 1189 1 bitblit, Live 0xd491b000
snd_rawmidi 19056 1 snd_mpu401_uart, Live 0xd4911000
snd_seq_device 5700 1 snd_rawmidi, Live 0xd48cf000
vga16fb 11385 1 - Live 0xd48b2000
vgastate 8961 1 vga16fb, Live 0xd48ad000
snd 54148 7 snd_via82xx,snd_ac97_codec,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device, Live 0xd4818000
via686a 10986 0 - Live 0xd47f0000
ppdev 5259 0 - Live 0xd4967000
via_agp 5310 1 - Live 0xd495a000
soundcore 6620 1 snd, Live 0xd494c000
i2c_viapro 5573 0 - Live 0xd493f000
lp 7028 0 - Live 0xd4932000
parport_pc 25962 1 - Live 0xd491e000
agpgart 31724 1 via_agp, Live 0xd48f0000
shpchp 28820 0 - Live 0xd48d3000
parport 32635 3 ppdev,lp,parport_pc, Live 0xd48b6000
8139too 18545 0 - Live 0xd4828000
8139cp 16186 0 - Live 0xd4812000
mii 4381 2 8139too,8139cp, Live 0xd4801000
pata_via 7272 2 - Live 0xd47f6000


As well, here is grub.cfg
> 
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 5ac7d3a6-5966-4578-8650-41e45199ca9e
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 5ac7d3a6-5966-4578-8650-41e45199ca9e
set locale_dir=($root)/boot/grub/locale
set lang=C.UTF-8
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 5ac7d3a6-5966-4578-8650-41e45199ca9e
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=5ac7d3a6-5966-4578-8650-41e45199ca9e ro   quiet
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 5ac7d3a6-5966-4578-8650-41e45199ca9e
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=5ac7d3a6-5966-4578-8650-41e45199ca9e ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 5ac7d3a6-5966-4578-8650-41e45199ca9e
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 5ac7d3a6-5966-4578-8650-41e45199ca9e
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###


I'm not sure what to look for in any of these files.

Thanks again for any help!

---

### Post by ruffEdgz on 2010-08-04
Its a good thing you posted that extra information because I think I have something that might be able to help.

I found this link that has something similar to your problem: [http://www.uluga.ubuntuforums.org/showthread.php?t=1068895]("http://www.uluga.ubuntuforums.org/showthread.php?t=1068895")

When looking at your /boot/grub/grub.cfg file, I noticed that this entry didn't have an option that could help with this issue:
```

menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
recordfail
insmod ext2
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 5ac7d3a6-5966-4578-8650-41e45199ca9e
linux /boot/vmlinuz-2.6.32-21-generic root=UUID=5ac7d3a6-5966-4578-8650-41e45199ca9e ro quiet
initrd /boot/initrd.img-2.6.32-21-generic
}

```

Try adding to this entry of your grub.cfg file the following below (add 'rootdelay'):
```

linux /boot/vmlinuz-2.6.32-21-generic root=UUID=5ac7d3a6-5966-4578-8650-41e45199ca9e ro **rootdelay=30** quiet

```

When adding that option to grub, you can increase/decrease it to whatever you wish. I have mine set to '10' but I thought with your system, we can try '30' and if need be, you can add or subtract depending on the output.

Hope this helps.

---

### Post by akester on 2010-08-04
That seemed to fix it!  I ended up setting the rootdelay to 300, eventually I'll toy with it to bring it down to something more sane.

Thank you so much for the help!

---

### Post by NocturnalDDD on 2010-08-10
I was recently bitten by this problem on my wife's computer.  We had recently changed it from Windows XP to a dual boot XP/Ubuntu 10.04.  She likes the extra speed of Linux.  

10.04 worked like a champ for a couple weeks then after an upgrade we started getting the "waiting for root device" error.  I knew it wasn't a hardware problem as it booted fine to XP and would boot to 10.04 if you waited for a while and hit 'exit'.

I'm a complete idiot when it comes to Linux and was stumped with the problem.  Ended up spending hours searching the web to solve the problem and eventually came up with the following.  I'm sure there's a better and more professional method but this worked for us and that's all that counts in the end!

I ended up editing the /boot/grub/grub.cfg file (I know you shouldn't touch it but I didn't know how to make the change any other way).  I tried the change on an older build first and it worked so made the change to the current build and it's back the booting fast and first time every time.

Note that in the example below I just grabbed some text from a previous message as I'm not on my linux machine and I'm sure the kernel versions are not the current ones.

In the /boot/grub/grub.cfg file I changed

linux /boot/vmlinuz-2.6.32-21-generic root=UUID=5ac7d3a6-5966-4578-8650-41e45199ca9e ro quiet

to

linux /boot/vmlinuz-2.6.32-21-generic root=/dev/sda5 ro quiet

sda5 being my linux boot partition

If anyone can suggest a better way to implement this so it's permanent and works with further kernel updates I'd appreciate it!

---

### Post by akester on 2010-08-20
The underlying problem for me was that the boot drive was on the secondary IDE channel.  You might start a new thread to get more help.

---

