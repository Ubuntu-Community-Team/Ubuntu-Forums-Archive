---
title: "HP ProLiant DL380G6 server crashing."
date: 2012-01-04
forum: Server Platforms
---

### Post by knutz on 2012-01-04
Hi everybody.

We recently got our hands on a HP ProLiant G6 server and my first thought was of course that ubuntu had to be installed on it. 

This server has an ordinary desktop 64 bit ubuntu installation on it and have been running for some time, but it crashes and restarts once in a while and not being an ubuntu-guru, I can't seem to find the problem and even though I've been through various log files.
The server runs as a VirtualBox server with several headless virtual machines running on it.


Can some one please help me on this? Any ideas?
And what log files/info do you guys need?


Thank you.

---

### Post by knutz on 2012-01-04
Output of dmesg:
```
[    0.000000] PM: Registered nosave memory: 00000000ff800000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at e4000000 (gap: e4000000:1ac00000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:16 nr_node_ids:1
[    0.000000] early_res array is doubled to 128 at [3e800 - 3f7ff]
[    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880001e00000 s92160 r8192 d22528 u131072
[    0.000000] pcpu-alloc: s92160 r8192 d22528 u131072 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 00 01 02 03 04 05 06 07 08 09 10 11 12 13 14 15
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 9820878
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-31-generic root=UUID=ad4e7026-0b6e-456a-bc9a-bd4ed9f4ab51 ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Subtract (71 early reservations)
[    0.000000]   #1 [0001000000 - 0001d63a74]   TEXT DATA BSS
[    0.000000]   #2 [0037566000 - 0037ff0000]         RAMDISK
[    0.000000]   #3 [0001d64000 - 0001d64128]             BRK
[    0.000000]   #4 [000009f400 - 00000f4f80]   BIOS reserved
[    0.000000]   #5 [00000f4f80 - 00000f4f90]    MP-table mpf
[    0.000000]   #6 [00000f4f90 - 00000ff91f]   BIOS reserved
[    0.000000]   #7 [00000ffca3 - 0000100000]   BIOS reserved
[    0.000000]   #8 [00000ff91f - 00000ffca3]    MP-table mpc
[    0.000000]   #9 [0000010000 - 0000012000]      TRAMPOLINE
[    0.000000]   #10 [0000012000 - 0000016000]     ACPI WAKEUP
[    0.000000]   #11 [0000016000 - 000001a000]         PGTABLE
[    0.000000]   #12 [000001a000 - 000003e000]         PGTABLE
[    0.000000]   #13 [0100000000 - 0100005000]       NODE_DATA
[    0.000000]   #14 [0001d64140 - 0001d65140]         BOOTMEM
[    0.000000]   #15 [0001d65140 - 0001d66140]         BOOTMEM
[    0.000000]   #16 [0001d66140 - 0001d67140]         BOOTMEM
[    0.000000]   #17 [0002167140 - 0002168dc0]         BOOTMEM
[    0.000000]   #18 [0100005000 - 0100006000]         BOOTMEM
[    0.000000]   #19 [0100006000 - 0100007000]         BOOTMEM
[    0.000000]   #20 [0100200000 - 0121800000]        MEMMAP 0
[    0.000000]   #21 [0001d63a80 - 0001d63c00]         BOOTMEM
[    0.000000]   #22 [0001d67140 - 0001d7f140]         BOOTMEM
[    0.000000]   #23 [0001d7f140 - 0001d97140]         BOOTMEM
[    0.000000]   #24 [0001d98000 - 0001d99000]         BOOTMEM
[    0.000000]   #25 [0001d63c00 - 0001d63c41]         BOOTMEM
[    0.000000]   #26 [0001d63c80 - 0001d63d06]         BOOTMEM
[    0.000000]   #27 [0001d63d40 - 0001d63fa8]         BOOTMEM
[    0.000000]   #28 [0001d97140 - 0001d971a8]         BOOTMEM
[    0.000000]   #29 [0001d971c0 - 0001d97228]         BOOTMEM
[    0.000000]   #30 [0001d97240 - 0001d972a8]         BOOTMEM
[    0.000000]   #31 [0001d972c0 - 0001d97328]         BOOTMEM
[    0.000000]   #32 [0001d97340 - 0001d973a8]         BOOTMEM
[    0.000000]   #33 [0001d973c0 - 0001d97428]         BOOTMEM
[    0.000000]   #34 [0001d97440 - 0001d974a8]         BOOTMEM
[    0.000000]   #35 [0001d974c0 - 0001d97528]         BOOTMEM
[    0.000000]   #36 [0001d97540 - 0001d975a8]         BOOTMEM
[    0.000000]   #37 [0001d975c0 - 0001d97628]         BOOTMEM
[    0.000000]   #38 [0001d63fc0 - 0001d63fe0]         BOOTMEM
[    0.000000]   #39 [0001d97640 - 0001d97660]         BOOTMEM
[    0.000000]   #40 [0001d97680 - 0001d976a0]         BOOTMEM
[    0.000000]   #41 [0001d976c0 - 0001d9772a]         BOOTMEM
[    0.000000]   #42 [0001d97740 - 0001d977aa]         BOOTMEM
[    0.000000]   #43 [0001e00000 - 0001e1e000]         BOOTMEM
[    0.000000]   #44 [0001e20000 - 0001e3e000]         BOOTMEM
[    0.000000]   #45 [0001e40000 - 0001e5e000]         BOOTMEM
[    0.000000]   #46 [0001e60000 - 0001e7e000]         BOOTMEM
[    0.000000]   #47 [0001e80000 - 0001e9e000]         BOOTMEM
[    0.000000]   #48 [0001ea0000 - 0001ebe000]         BOOTMEM
[    0.000000]   #49 [0001ec0000 - 0001ede000]         BOOTMEM
[    0.000000]   #50 [0001ee0000 - 0001efe000]         BOOTMEM
[    0.000000]   #51 [0001f00000 - 0001f1e000]         BOOTMEM
[    0.000000]   #52 [0001f20000 - 0001f3e000]         BOOTMEM
[    0.000000]   #53 [0001f40000 - 0001f5e000]         BOOTMEM
[    0.000000]   #54 [0001f60000 - 0001f7e000]         BOOTMEM
[    0.000000]   #55 [0001f80000 - 0001f9e000]         BOOTMEM
[    0.000000]   #56 [0001fa0000 - 0001fbe000]         BOOTMEM
[    0.000000]   #57 [0001fc0000 - 0001fde000]         BOOTMEM
[    0.000000]   #58 [0001fe0000 - 0001ffe000]         BOOTMEM
[    0.000000]   #59 [0001d977c0 - 0001d977c8]         BOOTMEM
[    0.000000]   #60 [0001d97800 - 0001d97808]         BOOTMEM
[    0.000000]   #61 [0001d97840 - 0001d97880]         BOOTMEM
[    0.000000]   #62 [0001d97880 - 0001d97900]         BOOTMEM
[    0.000000]   #63 [0001d97900 - 0001d97a10]         BOOTMEM
[    0.000000]   #64 [0001d97a40 - 0001d97a88]         BOOTMEM
[    0.000000]   #65 [0001d97ac0 - 0001d97b08]         BOOTMEM
[    0.000000]   #66 [0001d99000 - 0001da1000]         BOOTMEM
[    0.000000]   #67 [0002169000 - 0006169000]         BOOTMEM
[    0.000000]   #68 [0001da1000 - 0001dc1000]         BOOTMEM
[    0.000000]   #69 [0001ffe000 - 000203e000]         BOOTMEM
[    0.000000]   #70 [000003f800 - 0000047800]         BOOTMEM
[    0.000000] Memory: 39195788k/40370172k available (5726k kernel code, 534724k absent, 639660k reserved, 5372k data, 912k init)
[    0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=16, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]  RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]  RCU-based detection of stalled CPUs is disabled.
[    0.000000]  Verbose stalled-CPUs detection is disabled.
[    0.000000] NR_IRQS:16640 nr_irqs:1216
[    0.000000] Extended CMOS year: 2000
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 398458880 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.010000] Detected 2266.526 MHz processor.
[    0.000007] Calibrating delay loop (skipped), value calculated using timer frequency.. 4533.05 BogoMIPS (lpj=22665260)
[    0.000011] pid_max: default: 32768 minimum: 301
[    0.000032] Security Framework initialized
[    0.000044] AppArmor: AppArmor initialized
[    0.000045] Yama: becoming mindful.
[    0.005541] Dentry cache hash table entries: 8388608 (order: 14, 67108864 bytes)
[    0.033055] Inode-cache hash table entries: 4194304 (order: 13, 33554432 bytes)
[    0.045459] Mount-cache hash table entries: 256
[    0.045575] Initializing cgroup subsys ns
[    0.045578] Initializing cgroup subsys cpuacct
[    0.045582] Initializing cgroup subsys memory
[    0.045589] Initializing cgroup subsys devices
[    0.045591] Initializing cgroup subsys freezer
[    0.045593] Initializing cgroup subsys net_cls
[    0.045613] CPU: Physical Processor ID: 0
[    0.045614] CPU: Processor Core ID: 0
[    0.045619] mce: CPU supports 9 MCE banks
[    0.045629] CPU0: Thermal monitoring enabled (TM1)
[    0.045635] using mwait in idle threads.
[    0.045637] Performance Events: PEBS fmt1+, Nehalem events, Intel PMU driver.
[    0.045643] ... version:                3
[    0.045644] ... bit width:              48
[    0.045645] ... generic registers:      4
[    0.045646] ... value mask:             0000ffffffffffff
[    0.045648] ... max period:             000000007fffffff
[    0.045649] ... fixed-purpose events:   3
[    0.045650] ... event mask:             000000070000000f
[    0.047637] ACPI: Core revision 20100428
[    0.051254] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.051258] ftrace: allocating 22699 entries in 90 pages
[    0.058114] DMAR: Host address width 39
[    0.058116] DMAR: DRHD base: 0x000000e7ffe000 flags: 0x1
[    0.058124] IOMMU 0: reg_base_addr e7ffe000 ver 1:0 cap c90780106f0462 ecap f0207e
[    0.058126] DMAR: RMRR base: 0x000000df7fc000 end: 0x000000df7fdfff
[    0.058128] DMAR: RMRR base: 0x000000df7f5000 end: 0x000000df7fafff
[    0.058130] DMAR: ATSR flags: 0x0
[    0.058235] IOAPIC id 8 under DRHD base  0xe7ffe000 IOMMU 0
[    0.058237] IOAPIC id 0 under DRHD base  0xe7ffe000 IOMMU 0
[    0.058450] Enabled Interrupt-remapping
[    0.058454] Setting APIC routing to physical flat
[    0.058720]   alloc irq_desc for 64 on node 0
[    0.058722]   alloc kstat_irqs on node 0
[    0.058734] alloc irq_2_iommu on node 0
[    0.058740] alloc irq_2_iommu on node 0
[    0.058744] alloc irq_2_iommu on node 0
[    0.058749] alloc irq_2_iommu on node 0
[    0.058754] alloc irq_2_iommu on node 0
[    0.058758] alloc irq_2_iommu on node 0
[    0.058763] alloc irq_2_iommu on node 0
[    0.058768] alloc irq_2_iommu on node 0
[    0.058772] alloc irq_2_iommu on node 0
[    0.058777] alloc irq_2_iommu on node 0
[    0.058782] alloc irq_2_iommu on node 0
[    0.058787] alloc irq_2_iommu on node 0
[    0.058791] alloc irq_2_iommu on node 0
[    0.058796] alloc irq_2_iommu on node 0
[    0.058801] alloc irq_2_iommu on node 0
[    0.058955] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.158791] CPU0: Intel(R) Xeon(R) CPU           E5520  @ 2.27GHz stepping 05
[    0.278682] Booting Node   0, Processors  #1 #2 #3 #4 #5 #6 #7
[    1.536558] Brought up 8 CPUs
[    1.536561] Total of 8 processors activated (36267.25 BogoMIPS).
[    1.541070] devtmpfs: initialized
[    1.541984] regulator: core version 0.5
[    1.542007] Time: 18:01:02  Date: 01/03/12
[    1.542036] NET: Registered protocol family 16
[    1.542116] Trying to unpack rootfs image as initramfs...
[    1.542131] ACPI: bus type pci registered
[    1.542189] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xe0000000-0xe3ffffff] (base 0xe0000000)
[    1.542191] PCI: MMCONFIG at [mem 0xe0000000-0xe3ffffff] reserved in E820
[    1.550182] PCI: Using configuration type 1 for base access
[    1.550847] bio: create slab <bio-0> at 0
[    1.551588] ACPI: EC: Look up EC in DSDT
[    1.551711] ACPI Error: Field [CDW3] at 96 exceeds Buffer [NULL] size 64 (bits) (20100428/dsopcode-597)
[    1.551716] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_._OSC] (Node ffff880973489b20), AE_AML_BUFFER_LIMIT
[    1.554577] ACPI: Interpreter enabled
[    1.554579] ACPI: (supports S0 S4 S5)
[    1.554591] ACPI: Using IOAPIC for interrupt routing
[    1.557633] ACPI: No dock devices found.
[    1.557636] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    1.557653] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-19])
[    1.557689] pci_root PNP0A08:00: host bridge window [mem 0xe7000000-0xfbffffff]
[    1.557691] pci_root PNP0A08:00: host bridge window [io  0x1000-0x4fff]
[    1.557693] pci_root PNP0A08:00: host bridge window [io  0x0000-0x03af]
[    1.557695] pci_root PNP0A08:00: host bridge window [io  0x03e0-0x0cf7]
[    1.557697] pci_root PNP0A08:00: host bridge window [io  0x0d00-0x0fff]
[    1.557699] pci_root PNP0A08:00: host bridge window [mem 0xfed00000-0xfed03fff]
[    1.557701] pci_root PNP0A08:00: host bridge window [mem 0xfed00000-0xfed44fff]
[    1.557703] pci_root PNP0A08:00: host bridge window [io  0x03b0-0x03bb]
[    1.557705] pci_root PNP0A08:00: host bridge window [io  0x03c0-0x03df]
[    1.557707] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    1.557758] pci 0000:00:00.0: PME# supported from D0 D3hot D3cold
[    1.557761] pci 0000:00:00.0: PME# disabled
[    1.557814] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    1.557817] pci 0000:00:01.0: PME# disabled
[    1.557868] pci 0000:00:02.0: PME# supported from D0 D3hot D3cold
[    1.557870] pci 0000:00:02.0: PME# disabled
[    1.557920] pci 0000:00:03.0: PME# supported from D0 D3hot D3cold
[    1.557923] pci 0000:00:03.0: PME# disabled
[    1.557973] pci 0000:00:04.0: PME# supported from D0 D3hot D3cold
[    1.557976] pci 0000:00:04.0: PME# disabled
[    1.558026] pci 0000:00:05.0: PME# supported from D0 D3hot D3cold
[    1.558029] pci 0000:00:05.0: PME# disabled
[    1.558078] pci 0000:00:06.0: PME# supported from D0 D3hot D3cold
[    1.558081] pci 0000:00:06.0: PME# disabled
[    1.558131] pci 0000:00:07.0: PME# supported from D0 D3hot D3cold
[    1.558134] pci 0000:00:07.0: PME# disabled
[    1.558184] pci 0000:00:08.0: PME# supported from D0 D3hot D3cold
[    1.558187] pci 0000:00:08.0: PME# disabled
[    1.558238] pci 0000:00:09.0: PME# supported from D0 D3hot D3cold
[    1.558241] pci 0000:00:09.0: PME# disabled
[    1.558290] pci 0000:00:0a.0: PME# supported from D0 D3hot D3cold
[    1.558293] pci 0000:00:0a.0: PME# disabled
[    1.558998] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    1.559001] pci 0000:00:1c.0: PME# disabled
[    1.559062] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    1.559066] pci 0000:00:1c.2: PME# disabled
[    1.559133] pci 0000:00:1d.0: reg 20: [io  0x1000-0x101f]
[    1.559228] pci 0000:00:1d.1: reg 20: [io  0x1020-0x103f]
[    1.559323] pci 0000:00:1d.2: reg 20: [io  0x1040-0x105f]
[    1.559416] pci 0000:00:1d.3: reg 20: [io  0x1060-0x107f]
[    1.559490] pci 0000:00:1d.7: reg 10: [mem 0xf1df0000-0xf1df03ff]
[    1.559540] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    1.559544] pci 0000:00:1d.7: PME# disabled
[    1.559689] pci 0000:00:1f.2: reg 10: [io  0x1080-0x1087]
[    1.559694] pci 0000:00:1f.2: reg 14: [io  0x1088-0x108b]
[    1.559699] pci 0000:00:1f.2: reg 18: [io  0x1090-0x1097]
[    1.559703] pci 0000:00:1f.2: reg 1c: [io  0x1098-0x109b]
[    1.559708] pci 0000:00:1f.2: reg 20: [io  0x10a0-0x10af]
[    1.559713] pci 0000:00:1f.2: reg 24: [io  0x10b0-0x10bf]
[    1.559794] pci 0000:04:00.0: reg 10: [mem 0xfbc00000-0xfbffffff 64bit]
[    1.559802] pci 0000:04:00.0: reg 18: [mem 0xfbbf0000-0xfbbf0fff 64bit]
[    1.559807] pci 0000:04:00.0: reg 20: [io  0x4000-0x40ff]
[    1.559816] pci 0000:04:00.0: reg 30: [mem 0x00000000-0x0007ffff pref]
[    1.559837] pci 0000:04:00.0: supports D1
[    1.559838] pci 0000:04:00.0: PME# supported from D0
[    1.559841] pci 0000:04:00.0: PME# disabled
[    1.576409] pci 0000:00:01.0: PCI bridge to [bus 04-04]
[    1.576413] pci 0000:00:01.0:   bridge window [io  0x4000-0x4fff]
[    1.576416] pci 0000:00:01.0:   bridge window [mem 0xfbb00000-0xfbffffff]
[    1.576421] pci 0000:00:01.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    1.576454] pci 0000:00:02.0: PCI bridge to [bus 05-05]
[    1.576457] pci 0000:00:02.0:   bridge window [io  0xf000-0x0000] (disabled)
[    1.576460] pci 0000:00:02.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    1.576465] pci 0000:00:02.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    1.576497] pci 0000:00:03.0: PCI bridge to [bus 10-12]
[    1.576501] pci 0000:00:03.0:   bridge window [io  0xf000-0x0000] (disabled)
[    1.576505] pci 0000:00:03.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    1.576509] pci 0000:00:03.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    1.576541] pci 0000:00:04.0: PCI bridge to [bus 13-13]
[    1.576544] pci 0000:00:04.0:   bridge window [io  0xf000-0x0000] (disabled)
[    1.576547] pci 0000:00:04.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    1.576552] pci 0000:00:04.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    1.576584] pci 0000:00:05.0: PCI bridge to [bus 14-16]
[    1.576587] pci 0000:00:05.0:   bridge window [io  0xf000-0x0000] (disabled)
[    1.576590] pci 0000:00:05.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    1.576594] pci 0000:00:05.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    1.576626] pci 0000:00:06.0: PCI bridge to [bus 17-19]
[    1.576629] pci 0000:00:06.0:   bridge window [io  0xf000-0x0000] (disabled)
[    1.576632] pci 0000:00:06.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    1.576637] pci 0000:00:06.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    1.576669] pci 0000:00:07.0: PCI bridge to [bus 0d-0f]
[    1.576672] pci 0000:00:07.0:   bridge window [io  0xf000-0x0000] (disabled)
[    1.576675] pci 0000:00:07.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    1.576680] pci 0000:00:07.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    1.576712] pci 0000:00:08.0: PCI bridge to [bus 0a-0c]
[    1.576715] pci 0000:00:08.0:   bridge window [io  0xf000-0x0000] (disabled)
[    1.576718] pci 0000:00:08.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    1.576722] pci 0000:00:08.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    1.576754] pci 0000:00:09.0: PCI bridge to [bus 07-09]
[    1.576757] pci 0000:00:09.0:   bridge window [io  0xf000-0x0000] (disabled)
[    1.576760] pci 0000:00:09.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    1.576765] pci 0000:00:09.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    1.576797] pci 0000:00:0a.0: PCI bridge to [bus 06-06]
[    1.576800] pci 0000:00:0a.0:   bridge window [io  0xf000-0x0000] (disabled)
[    1.576803] pci 0000:00:0a.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    1.576807] pci 0000:00:0a.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    1.576880] pci 0000:02:00.0: reg 10: [mem 0xf4000000-0xf5ffffff 64bit]
[    1.576909] pci 0000:02:00.0: reg 30: [mem 0x00000000-0x0000ffff pref]
[    1.576951] pci 0000:02:00.0: PME# supported from D0 D3hot D3cold
[    1.576955] pci 0000:02:00.0: PME# disabled
[    1.577010] pci 0000:02:00.1: reg 10: [mem 0xf2000000-0xf3ffffff 64bit]
[    1.577038] pci 0000:02:00.1: reg 30: [mem 0x00000000-0x0000ffff pref]
[    1.577080] pci 0000:02:00.1: PME# supported from D0 D3hot D3cold
[    1.577084] pci 0000:02:00.1: PME# disabled
[    1.596374] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    1.596378] pci 0000:00:1c.0:   bridge window [io  0xf000-0x0000] (disabled)
[    1.596382] pci 0000:00:1c.0:   bridge window [mem 0xf2000000-0xf5ffffff]
[    1.596387] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    1.596462] pci 0000:03:00.0: reg 10: [mem 0xf8000000-0xf9ffffff 64bit]
[    1.596491] pci 0000:03:00.0: reg 30: [mem 0x00000000-0x0000ffff pref]
[    1.596535] pci 0000:03:00.0: PME# supported from D0 D3hot D3cold
[    1.596539] pci 0000:03:00.0: PME# disabled
[    1.596594] pci 0000:03:00.1: reg 10: [mem 0xf6000000-0xf7ffffff 64bit]
[    1.596622] pci 0000:03:00.1: reg 30: [mem 0x00000000-0x0000ffff pref]
[    1.596664] pci 0000:03:00.1: PME# supported from D0 D3hot D3cold
[    1.596668] pci 0000:03:00.1: PME# disabled
[    1.616346] pci 0000:00:1c.2: PCI bridge to [bus 03-03]
[    1.616350] pci 0000:00:1c.2:   bridge window [io  0xf000-0x0000] (disabled)
[    1.616354] pci 0000:00:1c.2:   bridge window [mem 0xf6000000-0xf9ffffff]
[    1.616360] pci 0000:00:1c.2:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    1.616411] pci 0000:01:03.0: reg 10: [mem 0xe8000000-0xefffffff pref]
[    1.616417] pci 0000:01:03.0: reg 14: [io  0x3000-0x30ff]
[    1.616423] pci 0000:01:03.0: reg 18: [mem 0xf1ff0000-0xf1ffffff]
[    1.616444] pci 0000:01:03.0: reg 30: [mem 0x00000000-0x0001ffff pref]
[    1.616464] pci 0000:01:03.0: supports D1 D2
[    1.616493] pci 0000:01:04.0: reg 10: [io  0x2800-0x28ff]
[    1.616499] pci 0000:01:04.0: reg 14: [mem 0xf1fe0000-0xf1fe01ff]
[    1.616541] pci 0000:01:04.0: PME# supported from D0 D3hot D3cold
[    1.616545] pci 0000:01:04.0: PME# disabled
[    1.616577] pci 0000:01:04.2: reg 10: [io  0x3400-0x34ff]
[    1.616584] pci 0000:01:04.2: reg 14: [mem 0xf1fd0000-0xf1fd07ff]
[    1.616591] pci 0000:01:04.2: reg 18: [mem 0xf1fc0000-0xf1fc3fff]
[    1.616598] pci 0000:01:04.2: reg 1c: [mem 0xf1f00000-0xf1f7ffff]
[    1.616615] pci 0000:01:04.2: reg 30: [mem 0x00000000-0x0000ffff pref]
[    1.616636] pci 0000:01:04.2: PME# supported from D0 D3hot D3cold
[    1.616641] pci 0000:01:04.2: PME# disabled
[    1.616694] pci 0000:01:04.4: reg 20: [io  0x3800-0x381f]
[    1.616725] pci 0000:01:04.4: PME# supported from D0 D3hot D3cold
[    1.616729] pci 0000:01:04.4: PME# disabled
[    1.616759] pci 0000:01:04.6: reg 10: [mem 0xf1ef0000-0xf1ef00ff]
[    1.616805] pci 0000:01:04.6: PME# supported from D0 D3hot D3cold
[    1.616809] pci 0000:01:04.6: PME# disabled
[    1.616848] pci 0000:00:1e.0: PCI bridge to [bus 01-01] (subtractive decode)
[    1.616851] pci 0000:00:1e.0:   bridge window [io  0x2000-0x3fff]
[    1.616855] pci 0000:00:1e.0:   bridge window [mem 0xf1e00000-0xf1ffffff]
[    1.616860] pci 0000:00:1e.0:   bridge window [mem 0xe8000000-0xefffffff 64bit pref]
[    1.616862] pci 0000:00:1e.0:   bridge window [mem 0xe7000000-0xfbffffff] (subtractive decode)
[    1.616864] pci 0000:00:1e.0:   bridge window [io  0x1000-0x4fff] (subtractive decode)
[    1.616866] pci 0000:00:1e.0:   bridge window [io  0x0000-0x03af] (subtractive decode)
[    1.616868] pci 0000:00:1e.0:   bridge window [io  0x03e0-0x0cf7] (subtractive decode)
[    1.616870] pci 0000:00:1e.0:   bridge window [io  0x0d00-0x0fff] (subtractive decode)
[    1.616872] pci 0000:00:1e.0:   bridge window [mem 0xfed00000-0xfed03fff] (subtractive decode)
[    1.616874] pci 0000:00:1e.0:   bridge window [mem 0xfed00000-0xfed44fff] (subtractive decode)
[    1.616876] pci 0000:00:1e.0:   bridge window [io  0x03b0-0x03bb] (subtractive decode)
[    1.616878] pci 0000:00:1e.0:   bridge window [io  0x03c0-0x03df] (subtractive decode)
[    1.616880] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    1.616928] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    1.617093] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.IP2P._PRT]
[    1.617143] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.IPT1._PRT]
[    1.617182] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.IPT3._PRT]
[    1.617219] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PT01._PRT]
[    1.617254] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PT03._PRT]
[    1.617303] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PT04._PRT]
[    1.617351] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PT05._PRT]
[    1.617399] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PT06._PRT]
[    1.617450] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PT07._PRT]
[    1.617531] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PT08._PRT]
[    1.617610] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PT09._PRT]
[    1.617690] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PT0A._PRT]
[    1.622077] ACPI: PCI Interrupt Link [LNKA] (IRQs 5 *7 10 11)
[    1.622146] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7 10 *11)
[    1.622209] ACPI: PCI Interrupt Link [LNKC] (IRQs *5 7 10 11)
[    1.622271] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 7 *10 11)
[    1.622334] ACPI: PCI Interrupt Link [LNKE] (IRQs *5 7 10 11)
[    1.622396] ACPI: PCI Interrupt Link [LNKF] (IRQs 5 7 *10 11)
[    1.622459] ACPI: PCI Interrupt Link [LNKG] (IRQs 5 7 *10 11)
[    1.622520] ACPI: PCI Interrupt Link [LNKH] (IRQs 5 *7 10 11)
[    1.622574] HEST: HEST table parsing is initialized.
[    1.622642] vgaarb: device added: PCI:0000:01:03.0,decodes=io+mem,owns=io+mem,locks=none
[    1.622646] vgaarb: loaded
[    1.622753] SCSI subsystem initialized
[    1.622901] libata version 3.00 loaded.
[    1.622941] usbcore: registered new interface driver usbfs
[    1.622949] usbcore: registered new interface driver hub
[    1.622968] usbcore: registered new device driver usb
[    1.623067] ACPI: WMI: Mapper loaded
[    1.623069] PCI: Using ACPI for IRQ routing
[    1.623071] PCI: pci_cache_line_size set to 64 bytes
[    1.623199] reserve RAM buffer: 000000000009f400 - 000000000009ffff
[    1.623201] reserve RAM buffer: 00000000df63f000 - 00000000dfffffff
[    1.623203] reserve RAM buffer: 00000000df64d000 - 00000000dfffffff
[    1.623205] reserve RAM buffer: 000000099ffff000 - 000000099fffffff
[    1.623276] NetLabel: Initializing
[    1.623278] NetLabel:  domain hash size = 128
[    1.623279] NetLabel:  protocols = UNLABELED CIPSOv4
[    1.623290] NetLabel:  unlabeled traffic allowed by default
[    1.623313] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
[    1.623317] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    1.623321] hpet0: 4 comparators, 64-bit 14.318180 MHz counter
[    1.686351] Switching to clocksource tsc
[    1.694430] AppArmor: AppArmor Filesystem Enabled
[    1.694444] pnp: PnP ACPI init
[    1.694462] ACPI: bus type pnp registered
[    1.695751] pnp: PnP ACPI: found 11 devices
[    1.695753] ACPI: ACPI bus type pnp unregistered
[    1.695763] system 00:01: [io  0x0408-0x040f] has been reserved
[    1.695765] system 00:01: [io  0x04d0-0x04d1] has been reserved
[    1.695768] system 00:01: [io  0x0700-0x071f] has been reserved
[    1.695770] system 00:01: [io  0x0880-0x08ff] has been reserved
[    1.695772] system 00:01: [io  0x0900-0x097f] has been reserved
[    1.695775] system 00:01: [io  0x0c80-0x0c83] has been reserved
[    1.695777] system 00:01: [io  0x0cd4-0x0cd7] has been reserved
[    1.695779] system 00:01: [io  0x0f50-0x0f58] has been reserved
[    1.695782] system 00:01: [io  0x0ca0-0x0ca1] has been reserved
[    1.695784] system 00:01: [io  0x0ca4-0x0ca5] has been reserved
[    1.695787] system 00:01: [io  0x02f8-0x02ff] has been reserved
[    1.695790] system 00:01: [mem 0xe0000000-0xe3ffffff] has been reserved
[    1.695792] system 00:01: [mem 0xfe000000-0xfebfffff] has been reserved
[    1.695795] system 00:01: [mem 0xe7ffe000-0xe7ffffff] has been reserved
[    1.701599] pci 0000:00:01.0: BAR 15: assigned [mem 0xe7000000-0xe70fffff pref]
[    1.701602] pci 0000:00:1c.0: BAR 15: assigned [mem 0xe7100000-0xe71fffff pref]
[    1.701605] pci 0000:00:1c.2: BAR 15: assigned [mem 0xe7200000-0xe72fffff pref]
[    1.701608] pci 0000:04:00.0: BAR 6: assigned [mem 0xe7000000-0xe707ffff pref]
[    1.701610] pci 0000:00:01.0: PCI bridge to [bus 04-04]
[    1.701613] pci 0000:00:01.0:   bridge window [io  0x4000-0x4fff]
[    1.701617] pci 0000:00:01.0:   bridge window [mem 0xfbb00000-0xfbffffff]
[    1.701620] pci 0000:00:01.0:   bridge window [mem 0xe7000000-0xe70fffff pref]
[    1.701625] pci 0000:00:02.0: PCI bridge to [bus 05-05]
[    1.701627] pci 0000:00:02.0:   bridge window [io  disabled]
[    1.701630] pci 0000:00:02.0:   bridge window [mem disabled]
[    1.701633] pci 0000:00:02.0:   bridge window [mem pref disabled]
[    1.701638] pci 0000:00:03.0: PCI bridge to [bus 10-12]
[    1.701640] pci 0000:00:03.0:   bridge window [io  disabled]
[    1.701643] pci 0000:00:03.0:   bridge window [mem disabled]
[    1.701646] pci 0000:00:03.0:   bridge window [mem pref disabled]
[    1.701651] pci 0000:00:04.0: PCI bridge to [bus 13-13]
[    1.701652] pci 0000:00:04.0:   bridge window [io  disabled]
[    1.701656] pci 0000:00:04.0:   bridge window [mem disabled]
[    1.701659] pci 0000:00:04.0:   bridge window [mem pref disabled]
[    1.701663] pci 0000:00:05.0: PCI bridge to [bus 14-16]
[    1.701665] pci 0000:00:05.0:   bridge window [io  disabled]
[    1.701668] pci 0000:00:05.0:   bridge window [mem disabled]
[    1.701671] pci 0000:00:05.0:   bridge window [mem pref disabled]
[    1.701676] pci 0000:00:06.0: PCI bridge to [bus 17-19]
[    1.701677] pci 0000:00:06.0:   bridge window [io  disabled]
[    1.701681] pci 0000:00:06.0:   bridge window [mem disabled]
[    1.701684] pci 0000:00:06.0:   bridge window [mem pref disabled]
[    1.701689] pci 0000:00:07.0: PCI bridge to [bus 0d-0f]
[    1.701690] pci 0000:00:07.0:   bridge window [io  disabled]
[    1.701694] pci 0000:00:07.0:   bridge window [mem disabled]
[    1.701696] pci 0000:00:07.0:   bridge window [mem pref disabled]
[    1.701701] pci 0000:00:08.0: PCI bridge to [bus 0a-0c]
[    1.701703] pci 0000:00:08.0:   bridge window [io  disabled]
[    1.701706] pci 0000:00:08.0:   bridge window [mem disabled]
[    1.701709] pci 0000:00:08.0:   bridge window [mem pref disabled]
[    1.701714] pci 0000:00:09.0: PCI bridge to [bus 07-09]
[    1.701715] pci 0000:00:09.0:   bridge window [io  disabled]
[    1.701719] pci 0000:00:09.0:   bridge window [mem disabled]
[    1.701722] pci 0000:00:09.0:   bridge window [mem pref disabled]
[    1.701726] pci 0000:00:0a.0: PCI bridge to [bus 06-06]
[    1.701728] pci 0000:00:0a.0:   bridge window [io  disabled]
[    1.701731] pci 0000:00:0a.0:   bridge window [mem disabled]
[    1.701734] pci 0000:00:0a.0:   bridge window [mem pref disabled]
[    1.701740] pci 0000:02:00.0: BAR 6: assigned [mem 0xe7100000-0xe710ffff pref]
[    1.701742] pci 0000:02:00.1: BAR 6: assigned [mem 0xe7110000-0xe711ffff pref]
[    1.701744] pci 0000:00:1c.0: PCI bridge to [bus 02-02]
[    1.701746] pci 0000:00:1c.0:   bridge window [io  disabled]
[    1.701750] pci 0000:00:1c.0:   bridge window [mem 0xf2000000-0xf5ffffff]
[    1.701754] pci 0000:00:1c.0:   bridge window [mem 0xe7100000-0xe71fffff pref]
[    1.701760] pci 0000:03:00.0: BAR 6: assigned [mem 0xe7200000-0xe720ffff pref]
[    1.701762] pci 0000:03:00.1: BAR 6: assigned [mem 0xe7210000-0xe721ffff pref]
[    1.701764] pci 0000:00:1c.2: PCI bridge to [bus 03-03]
[    1.701766] pci 0000:00:1c.2:   bridge window [io  disabled]
[    1.701770] pci 0000:00:1c.2:   bridge window [mem 0xf6000000-0xf9ffffff]
[    1.701774] pci 0000:00:1c.2:   bridge window [mem 0xe7200000-0xe72fffff pref]
[    1.701781] pci 0000:01:03.0: BAR 6: assigned [mem 0xf1e00000-0xf1e1ffff pref]
[    1.701783] pci 0000:01:04.2: BAR 6: assigned [mem 0xf1e20000-0xf1e2ffff pref]
[    1.701785] pci 0000:00:1e.0: PCI bridge to [bus 01-01]
[    1.701788] pci 0000:00:1e.0:   bridge window [io  0x2000-0x3fff]
[    1.701792] pci 0000:00:1e.0:   bridge window [mem 0xf1e00000-0xf1ffffff]
[    1.701796] pci 0000:00:1e.0:   bridge window [mem 0xe8000000-0xefffffff 64bit pref]
[    1.701809] pci 0000:00:01.0: setting latency timer to 64
[    1.701816] pci 0000:00:02.0: setting latency timer to 64
[    1.701823] pci 0000:00:03.0: setting latency timer to 64
[    1.701830] pci 0000:00:04.0: setting latency timer to 64
[    1.701837] pci 0000:00:05.0: setting latency timer to 64
[    1.701844] pci 0000:00:06.0: setting latency timer to 64
[    1.701851] pci 0000:00:07.0: setting latency timer to 64
[    1.701858] pci 0000:00:08.0: setting latency timer to 64
[    1.701865] pci 0000:00:09.0: setting latency timer to 64
[    1.701872] pci 0000:00:0a.0: setting latency timer to 64
[    1.701880]   alloc irq_desc for 16 on node -1
[    1.701882]   alloc kstat_irqs on node -1
[    1.701886] alloc irq_2_iommu on node -1
[    1.701891] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.701895] pci 0000:00:1c.0: setting latency timer to 64
[    1.701902] pci 0000:00:1c.2: PCI INT C -> GSI 16 (level, low) -> IRQ 16
[    1.701905] pci 0000:00:1c.2: setting latency timer to 64
[    1.701911] pci 0000:00:1e.0: setting latency timer to 64
[    1.701915] pci_bus 0000:00: resource 4 [mem 0xe7000000-0xfbffffff]
[    1.701917] pci_bus 0000:00: resource 5 [io  0x1000-0x4fff]
[    1.701919] pci_bus 0000:00: resource 6 [io  0x0000-0x03af]
[    1.701921] pci_bus 0000:00: resource 7 [io  0x03e0-0x0cf7]
[    1.701922] pci_bus 0000:00: resource 8 [io  0x0d00-0x0fff]
[    1.701924] pci_bus 0000:00: resource 9 [mem 0xfed00000-0xfed03fff]
[    1.701926] pci_bus 0000:00: resource 10 [mem 0xfed00000-0xfed44fff]
[    1.701928] pci_bus 0000:00: resource 11 [io  0x03b0-0x03bb]
[    1.701930] pci_bus 0000:00: resource 12 [io  0x03c0-0x03df]
[    1.701932] pci_bus 0000:00: resource 13 [mem 0x000a0000-0x000bffff]
[    1.701934] pci_bus 0000:04: resource 0 [io  0x4000-0x4fff]
[    1.701936] pci_bus 0000:04: resource 1 [mem 0xfbb00000-0xfbffffff]
[    1.701938] pci_bus 0000:04: resource 2 [mem 0xe7000000-0xe70fffff pref]
[    1.701941] pci_bus 0000:02: resource 1 [mem 0xf2000000-0xf5ffffff]
[    1.701943] pci_bus 0000:02: resource 2 [mem 0xe7100000-0xe71fffff pref]
[    1.701945] pci_bus 0000:03: resource 1 [mem 0xf6000000-0xf9ffffff]
[    1.701947] pci_bus 0000:03: resource 2 [mem 0xe7200000-0xe72fffff pref]
[    1.701949] pci_bus 0000:01: resource 0 [io  0x2000-0x3fff]
[    1.701951] pci_bus 0000:01: resource 1 [mem 0xf1e00000-0xf1ffffff]
[    1.701953] pci_bus 0000:01: resource 2 [mem 0xe8000000-0xefffffff 64bit pref]
[    1.701955] pci_bus 0000:01: resource 4 [mem 0xe7000000-0xfbffffff]
[    1.701957] pci_bus 0000:01: resource 5 [io  0x1000-0x4fff]
[    1.701959] pci_bus 0000:01: resource 6 [io  0x0000-0x03af]
[    1.701961] pci_bus 0000:01: resource 7 [io  0x03e0-0x0cf7]
[    1.701963] pci_bus 0000:01: resource 8 [io  0x0d00-0x0fff]
[    1.701964] pci_bus 0000:01: resource 9 [mem 0xfed00000-0xfed03fff]
[    1.701966] pci_bus 0000:01: resource 10 [mem 0xfed00000-0xfed44fff]
[    1.701968] pci_bus 0000:01: resource 11 [io  0x03b0-0x03bb]
[    1.701970] pci_bus 0000:01: resource 12 [io  0x03c0-0x03df]
[    1.701972] pci_bus 0000:01: resource 13 [mem 0x000a0000-0x000bffff]
[    1.702002] NET: Registered protocol family 2
[    1.702415] IP route cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    1.704008] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    1.707269] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    1.707688] TCP: Hash tables configured (established 524288 bind 65536)
[    1.707691] TCP reno registered
[    1.707783] UDP hash table entries: 32768 (order: 8, 1048576 bytes)
[    1.708311] UDP-Lite hash table entries: 32768 (order: 8, 1048576 bytes)
[    1.708852] NET: Registered protocol family 1
[    1.726636] pci 0000:01:03.0: Boot video device
[    1.727258] PCI: CLS 64 bytes, default 64
[    1.727260] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    1.727262] Placing 64MB software IO TLB between ffff880002169000 - ffff880006169000
[    1.727264] software IO TLB at phys 0x2169000 - 0x6169000
[    1.727724] Scanning for low memory corruption every 60 seconds
[    1.727855] audit: initializing netlink socket (disabled)
[    1.727863] type=2000 audit(1325613662.550:1): initialized
[    1.744700] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.746104] VFS: Disk quotas dquot_6.5.2
[    1.746163] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.746708] fuse init (API version 7.14)
[    1.746786] msgmni has been set to 32768
[    1.770294] Freeing initrd memory: 10792k freed
[    1.773851] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    1.773854] io scheduler noop registered
[    1.773856] io scheduler deadline registered
[    1.773892] io scheduler cfq registered (default)
[    1.774022] pcieport 0000:00:01.0: setting latency timer to 64
[    1.774050]   alloc irq_desc for 65 on node -1
[    1.774052]   alloc kstat_irqs on node -1
[    1.774057] alloc irq_2_iommu on node -1
[    1.774066] pcieport 0000:00:01.0: irq 65 for MSI/MSI-X
[    1.774127] pcieport 0000:00:02.0: setting latency timer to 64
[    1.774152]   alloc irq_desc for 66 on node -1
[    1.774153]   alloc kstat_irqs on node -1
[    1.774156] alloc irq_2_iommu on node -1
[    1.774162] pcieport 0000:00:02.0: irq 66 for MSI/MSI-X
[    1.774217] pcieport 0000:00:03.0: setting latency timer to 64
[    1.774242]   alloc irq_desc for 67 on node -1
[    1.774243]   alloc kstat_irqs on node -1
[    1.774245] alloc irq_2_iommu on node -1
[    1.774252] pcieport 0000:00:03.0: irq 67 for MSI/MSI-X
[    1.774304] pcieport 0000:00:04.0: setting latency timer to 64
[    1.774328]   alloc irq_desc for 68 on node -1
[    1.774330]   alloc kstat_irqs on node -1
[    1.774332] alloc irq_2_iommu on node -1
[    1.774338] pcieport 0000:00:04.0: irq 68 for MSI/MSI-X
[    1.774392] pcieport 0000:00:05.0: setting latency timer to 64
[    1.774416]   alloc irq_desc for 69 on node -1
[    1.774418]   alloc kstat_irqs on node -1
[    1.774420] alloc irq_2_iommu on node -1
[    1.774427] pcieport 0000:00:05.0: irq 69 for MSI/MSI-X
[    1.774479] pcieport 0000:00:06.0: setting latency timer to 64
[    1.774503]   alloc irq_desc for 70 on node -1
[    1.774504]   alloc kstat_irqs on node -1
[    1.774507] alloc irq_2_iommu on node -1
[    1.774513] pcieport 0000:00:06.0: irq 70 for MSI/MSI-X
[    1.774567] pcieport 0000:00:07.0: setting latency timer to 64
[    1.774592]   alloc irq_desc for 71 on node -1
[    1.774593]   alloc kstat_irqs on node -1
[    1.774595] alloc irq_2_iommu on node -1
[    1.774602] pcieport 0000:00:07.0: irq 71 for MSI/MSI-X
[    1.774653] pcieport 0000:00:08.0: setting latency timer to 64
[    1.774678]   alloc irq_desc for 72 on node -1
[    1.774679]   alloc kstat_irqs on node -1
[    1.774682] alloc irq_2_iommu on node -1
[    1.774688] pcieport 0000:00:08.0: irq 72 for MSI/MSI-X
[    1.774742] pcieport 0000:00:09.0: setting latency timer to 64
[    1.774767]   alloc irq_desc for 73 on node -1
[    1.774768]   alloc kstat_irqs on node -1
[    1.774770] alloc irq_2_iommu on node -1
[    1.774777] pcieport 0000:00:09.0: irq 73 for MSI/MSI-X
[    1.774829] pcieport 0000:00:0a.0: setting latency timer to 64
[    1.774854]   alloc irq_desc for 74 on node -1
[    1.774855]   alloc kstat_irqs on node -1
[    1.774857] alloc irq_2_iommu on node -1
[    1.774864] pcieport 0000:00:0a.0: irq 74 for MSI/MSI-X
[    1.774921] pcieport 0000:00:1c.0: setting latency timer to 64
[    1.774949]   alloc irq_desc for 75 on node -1
[    1.774951]   alloc kstat_irqs on node -1
[    1.774953] alloc irq_2_iommu on node -1
[    1.774960] pcieport 0000:00:1c.0: irq 75 for MSI/MSI-X
[    1.775021] pcieport 0000:00:1c.2: setting latency timer to 64
[    1.775050]   alloc irq_desc for 76 on node -1
[    1.775051]   alloc kstat_irqs on node -1
[    1.775053] alloc irq_2_iommu on node -1
[    1.775060] pcieport 0000:00:1c.2: irq 76 for MSI/MSI-X
[    1.775129] aer 0000:00:01.0:pcie02: AER service couldn't init device: no _OSC support
[    1.775137] aer 0000:00:02.0:pcie02: AER service couldn't init device: no _OSC support
[    1.775143] aer 0000:00:03.0:pcie02: AER service couldn't init device: no _OSC support
[    1.775148] aer 0000:00:04.0:pcie02: AER service couldn't init device: no _OSC support
[    1.775154] aer 0000:00:05.0:pcie02: AER service couldn't init device: no _OSC support
[    1.775160] aer 0000:00:06.0:pcie02: AER service couldn't init device: no _OSC support
[    1.775165] aer 0000:00:07.0:pcie02: AER service couldn't init device: no _OSC support
[    1.775171] aer 0000:00:08.0:pcie02: AER service couldn't init device: no _OSC support
[    1.775176] aer 0000:00:09.0:pcie02: AER service couldn't init device: no _OSC support
[    1.775182] aer 0000:00:0a.0:pcie02: AER service couldn't init device: no _OSC support
[    1.775200] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.775219] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.775284] intel_idle: MWAIT substates: 0x1120
[    1.775286] intel_idle: v0.4 model 0x1A
[    1.775287] intel_idle: lapic_timer_reliable_states 0x2
[    1.775402] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.775407] ACPI: Power Button [PWRF]
[    1.775717] ACPI: acpi_idle yielding to intel_idle
[    1.777152] thermal LNXTHERM:01: registered as thermal_zone0
[    1.777158] ACPI: Thermal Zone [THM0] (8 C)
[    1.777234] [Firmware Bug]: ERST: ERST table is invalid
[    1.777394] Linux agpgart interface v0.103
[    1.777414] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    1.777511] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.777581] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    1.777861] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.778788] brd: module loaded
[    1.779214] loop: module loaded
[    1.779354] ata_piix 0000:00:1f.2: version 2.13
[    1.779366]   alloc irq_desc for 17 on node -1
[    1.779368]   alloc kstat_irqs on node -1
[    1.779371] alloc irq_2_iommu on node -1
[    1.779377] ata_piix 0000:00:1f.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.779381] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    1.937494] ata_piix 0000:00:1f.2: setting latency timer to 64
[    1.937561] scsi0 : ata_piix
[    1.937647] scsi1 : ata_piix
[    1.937685] ata1: SATA max UDMA/133 cmd 0x1080 ctl 0x1088 bmdma 0x10a0 irq 17
[    1.937691] ata2: SATA max UDMA/133 cmd 0x1090 ctl 0x1098 bmdma 0x10a8 irq 17
[    1.938026] Fixed MDIO Bus: probed
[    1.938058] PPP generic driver version 2.4.2
[    1.938096] tun: Universal TUN/TAP device driver, 1.6
[    1.938098] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.938172] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.938192]   alloc irq_desc for 20 on node -1
[    1.938194]   alloc kstat_irqs on node -1
[    1.938198] alloc irq_2_iommu on node -1
[    1.938204] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    1.938228] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    1.938232] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    1.938274] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    1.938310] ehci_hcd 0000:00:1d.7: debug port 1
[    1.942199] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
[    1.942215] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xf1df0000
[    1.957445] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    1.957574] hub 1-0:1.0: USB hub found
[    1.957580] hub 1-0:1.0: 8 ports detected
[    1.957670] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.957686] uhci_hcd: USB Universal Host Controller Interface driver
[    1.957739] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    1.957745] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.957749] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    1.957787] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.957811] uhci_hcd 0000:00:1d.0: irq 20, io base 0x00001000
[    1.957928] hub 2-0:1.0: USB hub found
[    1.957933] hub 2-0:1.0: 2 ports detected
[    1.958004]   alloc irq_desc for 23 on node -1
[    1.958006]   alloc kstat_irqs on node -1
[    1.958010] alloc irq_2_iommu on node -1
[    1.958017] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 23 (level, low) -> IRQ 23
[    1.958022] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    1.958026] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    1.958060] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    1.958092] uhci_hcd 0000:00:1d.1: irq 23, io base 0x00001020
[    1.958208] hub 3-0:1.0: USB hub found
[    1.958213] hub 3-0:1.0: 2 ports detected
[    1.958286]   alloc irq_desc for 22 on node -1
[    1.958288]   alloc kstat_irqs on node -1
[    1.958292] alloc irq_2_iommu on node -1
[    1.958298] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    1.958304] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    1.958307] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    1.958341] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    1.958373] uhci_hcd 0000:00:1d.2: irq 22, io base 0x00001040
[    1.958492] hub 4-0:1.0: USB hub found
[    1.958496] hub 4-0:1.0: 2 ports detected
[    1.958565] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    1.958571] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    1.958574] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    1.958608] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    1.958632] uhci_hcd 0000:00:1d.3: irq 23, io base 0x00001060
[    1.958760] hub 5-0:1.0: USB hub found
[    1.958764] hub 5-0:1.0: 2 ports detected
[    1.958839] uhci_hcd 0000:01:04.4: PCI INT B -> GSI 22 (level, low) -> IRQ 22
[    1.958846] uhci_hcd 0000:01:04.4: UHCI Host Controller
[    1.958886] uhci_hcd 0000:01:04.4: new USB bus registered, assigned bus number 6
[    1.958899] uhci_hcd 0000:01:04.4: port count misdetected? forcing to 2 ports
[    1.959519] uhci_hcd 0000:01:04.4: irq 22, io base 0x00003800
[    1.959683] hub 6-0:1.0: USB hub found
[    1.959687] hub 6-0:1.0: 2 ports detected
[    1.959811] PNP: PS/2 Controller [PNP0303:KBD,PNP0f0e:PS2M] at 0x60,0x64 irq 1,12
[    1.961446] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.961453] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.961524] mice: PS/2 mouse device common for all mice
[    1.961602] rtc_cmos 00:0a: RTC can wake from S4
[    1.961641] rtc_cmos 00:0a: rtc core: registered rtc_cmos as rtc0
[    1.961667] rtc0: alarms up to one year, y3k, 114 bytes nvram, hpet irqs
[    1.961775] device-mapper: uevent: version 1.0.3
[    1.961854] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: dm-devel@redhat.com
[    1.962030] device-mapper: multipath: version 1.1.1 loaded
[    1.962033] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.962624] cpuidle: using governor ladder
[    1.962991] cpuidle: using governor menu
[    1.963309] TCP cubic registered
[    1.963456] NET: Registered protocol family 10
[    1.963890] lo: Disabled Privacy Extensions
[    1.964132] NET: Registered protocol family 17
[    1.964346] PM: Resume from disk failed.
[    1.964358] registered taskstats version 1
[    1.964973]   Magic number: 12:64:38
[    1.964981] bdi 7:3: hash matches
[    1.965000] rtc_cmos 00:0a: hash matches
[    1.965231] rtc_cmos 00:0a: setting system clock to 2012-01-03 18:01:03 UTC (1325613663)
[    1.965235] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.965237] EDD information not available.
[    2.275783] usb 6-1: new full speed USB device using uhci_hcd and address 2
[    2.555268] usb 6-2: new full speed USB device using uhci_hcd and address 3
[    2.646127] ata2.00: SATA link down (SStatus 4 SControl 300)
[    2.646142] ata2.01: SATA link down (SStatus 4 SControl 300)
[    2.720094] hub 6-2:1.0: USB hub found
[    2.722352] hub 6-2:1.0: 7 ports detected
[    2.794927] ata1.00: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.794943] ata1.01: SATA link down (SStatus 4 SControl 300)
[    2.794955] ata1.01: link offline, clearing class 3 to NONE
[    2.814980] ata1.00: ATAPI: TEAC    DV-W28S-RS, G.C4, max UDMA/100
[    2.854920] ata1.00: configured for UDMA/100
[    2.936146] scsi 0:0:0:0: CD-ROM            TEAC     DV-W28S-RS       G.C4 PQ: 0 ANSI: 5
[    3.048005] sr0: scsi3-mmc drive: 8x/8x writer dvd-ram cd/rw xa/form2 cdda tray
[    3.048009] Uniform CD-ROM driver Revision: 3.20
[    3.048103] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    3.048158] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    3.048342] Freeing unused kernel memory: 912k freed
[    3.048484] Write protecting the kernel read-only data: 10240k
[    3.050151] Freeing unused kernel memory: 400k freed
[    3.050871] Freeing unused kernel memory: 1640k freed
[    3.070376] udev[149]: starting version 163
[    3.094748] HP CISS Driver (v 3.6.20)
[    3.096215]   alloc irq_desc for 28 on node -1
[    3.096220]   alloc kstat_irqs on node -1
[    3.096228] alloc irq_2_iommu on node -1
[    3.096239] cciss 0000:04:00.0: PCI INT A -> GSI 28 (level, low) -> IRQ 28
[    3.096328]   alloc irq_desc for 77 on node -1
[    3.096331]   alloc kstat_irqs on node -1
[    3.096337] alloc irq_2_iommu on node -1
[    3.096345] cciss 0000:04:00.0: irq 77 for MSI/MSI-X
[    3.096349]   alloc irq_desc for 78 on node -1
[    3.096352]   alloc kstat_irqs on node -1
[    3.096356] alloc irq_2_iommu on node -1
[    3.096363] cciss 0000:04:00.0: irq 78 for MSI/MSI-X
[    3.096366]   alloc irq_desc for 79 on node -1
[    3.096369]   alloc kstat_irqs on node -1
[    3.096373] alloc irq_2_iommu on node -1
[    3.096380] cciss 0000:04:00.0: irq 79 for MSI/MSI-X
[    3.096384]   alloc irq_desc for 80 on node -1
[    3.096387]   alloc kstat_irqs on node -1
[    3.096390] alloc irq_2_iommu on node -1
[    3.096398] cciss 0000:04:00.0: irq 80 for MSI/MSI-X
[    3.106175] cciss0: <0x323a> at PCI 0000:04:00.0 IRQ 79 using DAC
[    3.109745]  cciss/c0d0: p1 p2 < p5 >
[    3.132453] usbcore: registered new interface driver hiddev
[    3.137006] input: HP Virtual Keyboard as /devices/pci0000:00/0000:00:1e.0/0000:01:04.4/usb6/6-1/6-1:1.0/input/input1
[    3.137117] generic-usb 0003:03F0:1027.0001: input,hidraw0: USB HID v1.01 Keyboard [HP Virtual Keyboard] on usb-0000:01:04.4-1/input0
[    3.143432] input: HP Virtual Keyboard as /devices/pci0000:00/0000:00:1e.0/0000:01:04.4/usb6/6-1/6-1:1.1/input/input2
[    3.143567] generic-usb 0003:03F0:1027.0002: input,hidraw1: USB HID v1.01 Mouse [HP Virtual Keyboard] on usb-0000:01:04.4-1/input1
[    3.143592] usbcore: registered new interface driver usbhid
[    3.143596] usbhid: USB HID core driver
[    3.357451] EXT4-fs (cciss!c0d0p1): INFO: recovery required on readonly filesystem
[    3.357457] EXT4-fs (cciss!c0d0p1): write access will be enabled during recovery
[    3.619804] EXT4-fs (cciss!c0d0p1): orphan cleanup on readonly fs
[    3.630144] EXT4-fs (cciss!c0d0p1): ext4_orphan_cleanup: deleting unreferenced inode 60558515
[    3.651084] EXT4-fs (cciss!c0d0p1): ext4_orphan_cleanup: deleting unreferenced inode 68158494
[    3.674897] EXT4-fs (cciss!c0d0p1): ext4_orphan_cleanup: deleting unreferenced inode 68158460
[    3.674959] EXT4-fs (cciss!c0d0p1): ext4_orphan_cleanup: deleting unreferenced inode 100663304
[    3.674972] EXT4-fs (cciss!c0d0p1): ext4_orphan_cleanup: deleting unreferenced inode 100663302
[    3.674981] EXT4-fs (cciss!c0d0p1): ext4_orphan_cleanup: deleting unreferenced inode 100663301
[    3.674990] EXT4-fs (cciss!c0d0p1): ext4_orphan_cleanup: deleting unreferenced inode 100663300
[    3.674998] EXT4-fs (cciss!c0d0p1): ext4_orphan_cleanup: deleting unreferenced inode 100663299
[    3.675006] EXT4-fs (cciss!c0d0p1): 8 orphan inodes deleted
[    3.675009] EXT4-fs (cciss!c0d0p1): recovery complete
[    3.676155] JBD: barrier-based sync failed on cciss!c0d0p1-8 - disabling barriers
[    3.683723] EXT4-fs (cciss!c0d0p1): mounted filesystem with ordered data mode. Opts: (null)
[    9.639675] Adding 17910780k swap on /dev/cciss/c0d0p5.  Priority:-1 extents:1 across:17910780k
[    9.668575] udev[407]: starting version 163
[    9.682886] lp: driver loaded but no devices found
[    9.728899] bnx2: Broadcom NetXtreme II Gigabit Ethernet Driver bnx2 v2.0.15 (May 4, 2010)
[    9.728966] bnx2 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    9.728978] bnx2 0000:02:00.0: setting latency timer to 64
[    9.747058] ipmi message handler version 39.2
[    9.761617] EDAC MC: Ver: 2.1.0 Nov 28 2011
[    9.765764] IPMI System Interface driver.
[    9.765794] ipmi_si 0000:01:04.6: probing via PCI
[    9.765811]   alloc irq_desc for 21 on node -1
[    9.765814]   alloc kstat_irqs on node -1
[    9.765822] alloc irq_2_iommu on node -1
[    9.765831] ipmi_si 0000:01:04.6: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    9.765838] ipmi_si 0000:01:04.6: [mem 0xf1ef0000-0xf1ef00ff] regsize 1 spacing 1 irq 21
[    9.765842] ipmi_si: Adding PCI-specified kcs state machine
[    9.765877] ipmi_si: probing via ACPI
[    9.765937] ipmi_si 00:02: (null) regsize 1 spacing 1 irq 0
[    9.765940] ipmi_si: Adding ACPI-specified kcs state machine
[    9.765959] ipmi_si: probing via SMBIOS
[    9.765962] ipmi_si: Adding SMBIOS-specified kcs state machineipmi_si: duplicate interface
[    9.765973] ipmi_si: probing via SPMI
[    9.765976] ipmi_si: Adding SPMI-specified kcs state machineipmi_si: duplicate interface
[    9.765982] ipmi_si: Trying PCI-specified kcs state machine at mem address 0xf1ef0000, slave address 0x0, irq 21
[    9.767990] hpilo 0000:01:04.2: PCI INT B -> GSI 22 (level, low) -> IRQ 22
[    9.776779] EDAC i7core: Driver loaded.
[    9.790895] bnx2 0000:02:00.0: eth0: Broadcom NetXtreme II BCM5709 1000Base-T (C0) PCI Express found at mem f4000000, IRQ 16, node addr 00:25:b3:23:c4:92
[    9.790930] bnx2 0000:02:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    9.790941] bnx2 0000:02:00.1: setting latency timer to 64
[    9.798001] type=1400 audit(1325613671.333:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=676 comm="apparmor_parser"
[    9.798871] type=1400 audit(1325613671.333:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=676 comm="apparmor_parser"
[    9.799343] type=1400 audit(1325613671.333:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=676 comm="apparmor_parser"
[    9.802045] bnx2 0000:02:00.1: eth1: Broadcom NetXtreme II BCM5709 1000Base-T (C0) PCI Express found at mem f2000000, IRQ 17, node addr 00:25:b3:23:c4:94
[    9.802083]   alloc irq_desc for 18 on node -1
[    9.802087]   alloc kstat_irqs on node -1
[    9.802095] alloc irq_2_iommu on node -1
[    9.802105] bnx2 0000:03:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    9.802116] bnx2 0000:03:00.0: setting latency timer to 64
[    9.808329] [drm] Initialized drm 1.1.0 20060810
[    9.814139] bnx2 0000:03:00.0: eth2: Broadcom NetXtreme II BCM5709 1000Base-T (C0) PCI Express found at mem f8000000, IRQ 18, node addr 00:25:b3:23:c4:96
[    9.814178]   alloc irq_desc for 19 on node -1
[    9.814182]   alloc kstat_irqs on node -1
[    9.814189] alloc irq_2_iommu on node -1
[    9.814199] bnx2 0000:03:00.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    9.814211] bnx2 0000:03:00.1: setting latency timer to 64
[    9.819368] bnx2 0000:03:00.1: eth3: Broadcom NetXtreme II BCM5709 1000Base-T (C0) PCI Express found at mem f6000000, IRQ 19, node addr 00:25:b3:23:c4:98
[    9.861364] [drm] radeon defaulting to kernel modesetting.
[    9.861370] [drm] radeon kernel modesetting enabled.
[    9.861483] radeon 0000:01:03.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    9.861584] EXT4-fs (cciss!c0d0p1): re-mounted. Opts: errors=remount-ro
[    9.863535] [drm] initializing kernel modesetting (RV100 0x1002:0x515E).
[    9.864009] [drm] register mmio base: 0xF1FF0000
[    9.864013] [drm] register mmio size: 65536
[    9.864195] radeon 0000:01:03.0: VRAM: 128M 0xE8000000 - 0xEFFFFFFF (64M used)
[    9.864201] radeon 0000:01:03.0: GTT: 512M 0xC8000000 - 0xE7FFFFFF
[    9.894188] [drm] radeon: irq initialized.
[    9.897115] [drm] Detected VRAM RAM=128M, BAR=128M
[    9.897119] [drm] RAM width 16bits DDR
[    9.897200] [TTM] Zone  kernel: Available graphics memory: 19604766 kiB.
[    9.897202] [TTM] Zone   dma32: Available graphics memory: 2097152 kiB.
[    9.897205] [TTM] Initializing pool allocator.
[    9.897227] [drm] radeon: 64M of VRAM memory ready
[    9.897229] [drm] radeon: 512M of GTT memory ready.
[    9.897250] [drm] GART: num cpu pages 131072, num gpu pages 131072
[    9.918830] [drm] Loading R100 Microcode
[    9.920367] [drm] radeon: ring at 0x00000000C8000000
[    9.920392] [drm] ring test succeeded in 1 usecs
[    9.920542] [drm] radeon: ib pool ready.
[    9.922536] [drm] ib test succeeded in 0 usecs
[    9.922698] [drm] Radeon Display Connectors
[    9.922701] [drm] Connector 0:
[    9.922702] [drm]   VGA
[    9.922705] [drm]   DDC: 0x60 0x60 0x60 0x60 0x60 0x60 0x60 0x60
[    9.922707] [drm]   Encoders:
[    9.922709] [drm]     CRT1: INTERNAL_DAC1
[    9.922710] [drm] Connector 1:
[    9.922712] [drm]   VGA
[    9.922714] [drm]   DDC: 0x6c 0x6c 0x6c 0x6c 0x6c 0x6c 0x6c 0x6c
[    9.922716] [drm]   Encoders:
[    9.922717] [drm]     CRT2: INTERNAL_DAC2
[    9.983073] [drm] fb mappable at 0xE8040000
[    9.983076] [drm] vram apper at 0xE8000000
[    9.983078] [drm] size 786432
[    9.983080] [drm] fb depth is 8
[    9.983081] [drm]    pitch is 1024
[   10.133451] ipmi_si 0000:01:04.6: Using irq 21
[   10.141627] Console: switching to colour frame buffer device 128x48
[   10.149399] fb0: radeondrmfb frame buffer device
[   10.149400] drm: registered panic notifier
[   10.149403] Slow work thread pool: Starting up
[   10.149559] Slow work thread pool: Ready
[   10.149570] [drm] Initialized radeon 2.5.0 20080528 for 0000:01:03.0 on minor 0
[   10.172009] type=1400 audit(1325613671.713:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=901 comm="apparmor_parser"
[   10.172058] type=1400 audit(1325613671.713:6): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=900 comm="apparmor_parser"
[   10.172541] type=1400 audit(1325613671.713:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=901 comm="apparmor_parser"
[   10.172794] type=1400 audit(1325613671.713:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=904 comm="apparmor_parser"
[   10.172975] type=1400 audit(1325613671.713:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=901 comm="apparmor_parser"
[   10.173847] type=1400 audit(1325613671.713:10): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=904 comm="apparmor_parser"
[   10.174235] type=1400 audit(1325613671.713:11): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=906 comm="apparmor_parser"
[   10.209299]   alloc irq_desc for 81 on node -1
[   10.209302]   alloc kstat_irqs on node -1
[   10.209307] alloc irq_2_iommu on node -1
[   10.209313] bnx2 0000:02:00.0: irq 81 for MSI/MSI-X
[   10.209315]   alloc irq_desc for 82 on node -1
[   10.209316]   alloc kstat_irqs on node -1
[   10.209318] alloc irq_2_iommu on node -1
[   10.209322] bnx2 0000:02:00.0: irq 82 for MSI/MSI-X
[   10.209323]   alloc irq_desc for 83 on node -1
[   10.209324]   alloc kstat_irqs on node -1
[   10.209326] alloc irq_2_iommu on node -1
[   10.209330] bnx2 0000:02:00.0: irq 83 for MSI/MSI-X
[   10.209331]   alloc irq_desc for 84 on node -1
[   10.209332]   alloc kstat_irqs on node -1
[   10.209334] alloc irq_2_iommu on node -1
[   10.209337] bnx2 0000:02:00.0: irq 84 for MSI/MSI-X
[   10.209339]   alloc irq_desc for 85 on node -1
[   10.209340]   alloc kstat_irqs on node -1
[   10.209342] alloc irq_2_iommu on node -1
[   10.209345] bnx2 0000:02:00.0: irq 85 for MSI/MSI-X
[   10.209347]   alloc irq_desc for 86 on node -1
[   10.209348]   alloc kstat_irqs on node -1
[   10.209350] alloc irq_2_iommu on node -1
[   10.209353] bnx2 0000:02:00.0: irq 86 for MSI/MSI-X
[   10.209355]   alloc irq_desc for 87 on node -1
[   10.209356]   alloc kstat_irqs on node -1
[   10.209357] alloc irq_2_iommu on node -1
[   10.209361] bnx2 0000:02:00.0: irq 87 for MSI/MSI-X
[   10.209363]   alloc irq_desc for 88 on node -1
[   10.209364]   alloc kstat_irqs on node -1
[   10.209365] alloc irq_2_iommu on node -1
[   10.209369] bnx2 0000:02:00.0: irq 88 for MSI/MSI-X
[   10.209371]   alloc irq_desc for 89 on node -1
[   10.209372]   alloc kstat_irqs on node -1
[   10.209374] alloc irq_2_iommu on node -1
[   10.209378] bnx2 0000:02:00.0: irq 89 for MSI/MSI-X
[   10.264956] bnx2 0000:02:00.0: eth0: using MSIX
[   10.266878] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   10.268259]   alloc irq_desc for 90 on node -1
[   10.268262]   alloc kstat_irqs on node -1
[   10.268268] alloc irq_2_iommu on node -1
[   10.268276] bnx2 0000:02:00.1: irq 90 for MSI/MSI-X
[   10.268278]   alloc irq_desc for 91 on node -1
[   10.268280]   alloc kstat_irqs on node -1
[   10.268283] alloc irq_2_iommu on node -1
[   10.268288] bnx2 0000:02:00.1: irq 91 for MSI/MSI-X
[   10.268290]   alloc irq_desc for 92 on node -1
[   10.268291]   alloc kstat_irqs on node -1
[   10.268293] alloc irq_2_iommu on node -1
[   10.268298] bnx2 0000:02:00.1: irq 92 for MSI/MSI-X
[   10.268300]   alloc irq_desc for 93 on node -1
[   10.268301]   alloc kstat_irqs on node -1
[   10.268304] alloc irq_2_iommu on node -1
[   10.268308] bnx2 0000:02:00.1: irq 93 for MSI/MSI-X
[   10.268310]   alloc irq_desc for 94 on node -1
[   10.268312]   alloc kstat_irqs on node -1
[   10.268315] alloc irq_2_iommu on node -1
[   10.268320] bnx2 0000:02:00.1: irq 94 for MSI/MSI-X
[   10.268322]   alloc irq_desc for 95 on node -1
[   10.268324]   alloc kstat_irqs on node -1
[   10.268326] alloc irq_2_iommu on node -1
[   10.268331] bnx2 0000:02:00.1: irq 95 for MSI/MSI-X
[   10.268333]   alloc irq_desc for 96 on node -1
[   10.268335]   alloc kstat_irqs on node -1
[   10.268337] alloc irq_2_iommu on node -1
[   10.268342] bnx2 0000:02:00.1: irq 96 for MSI/MSI-X
[   10.268344]   alloc irq_desc for 97 on node -1
[   10.268346]   alloc kstat_irqs on node -1
[   10.268349] alloc irq_2_iommu on node -1
[   10.268354] bnx2 0000:02:00.1: irq 97 for MSI/MSI-X
[   10.268356]   alloc irq_desc for 98 on node -1
[   10.268359]   alloc kstat_irqs on node -1
[   10.268361] alloc irq_2_iommu on node -1
[   10.268366] bnx2 0000:02:00.1: irq 98 for MSI/MSI-X
[   10.327479] bnx2 0000:02:00.1: eth1: using MSIX
[   10.328896] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   10.367223] ipmi_si 0000:01:04.6: Found new BMC (man_id: 0x00000b, prod_id: 0x0000, dev_id: 0x11)
[   10.367235] ipmi_si 0000:01:04.6: IPMI kcs interface initialized
[   10.385824]   alloc irq_desc for 99 on node -1
[   10.385827]   alloc kstat_irqs on node -1
[   10.385833] alloc irq_2_iommu on node -1
[   10.385840] bnx2 0000:03:00.0: irq 99 for MSI/MSI-X
[   10.385841]   alloc irq_desc for 100 on node -1
[   10.385842]   alloc kstat_irqs on node -1
[   10.385844] alloc irq_2_iommu on node -1
[   10.385848] bnx2 0000:03:00.0: irq 100 for MSI/MSI-X
[   10.385850]   alloc irq_desc for 101 on node -1
[   10.385851]   alloc kstat_irqs on node -1
[   10.385853] alloc irq_2_iommu on node -1
[   10.385857] bnx2 0000:03:00.0: irq 101 for MSI/MSI-X
[   10.385858]   alloc irq_desc for 102 on node -1
[   10.385860]   alloc kstat_irqs on node -1
[   10.385861] alloc irq_2_iommu on node -1
[   10.385865] bnx2 0000:03:00.0: irq 102 for MSI/MSI-X
[   10.385866]   alloc irq_desc for 103 on node -1
[   10.385868]   alloc kstat_irqs on node -1
[   10.385869] alloc irq_2_iommu on node -1
[   10.385874] bnx2 0000:03:00.0: irq 103 for MSI/MSI-X
[   10.385875]   alloc irq_desc for 104 on node -1
[   10.385877]   alloc kstat_irqs on node -1
[   10.385878] alloc irq_2_iommu on node -1
[   10.385882] bnx2 0000:03:00.0: irq 104 for MSI/MSI-X
[   10.385884]   alloc irq_desc for 105 on node -1
[   10.385885]   alloc kstat_irqs on node -1
[   10.385887] alloc irq_2_iommu on node -1
[   10.385890] bnx2 0000:03:00.0: irq 105 for MSI/MSI-X
[   10.385892]   alloc irq_desc for 106 on node -1
[   10.385893]   alloc kstat_irqs on node -1
[   10.385895] alloc irq_2_iommu on node -1
[   10.385899] bnx2 0000:03:00.0: irq 106 for MSI/MSI-X
[   10.385900]   alloc irq_desc for 107 on node -1
[   10.385901]   alloc kstat_irqs on node -1
[   10.385903] alloc irq_2_iommu on node -1
[   10.385907] bnx2 0000:03:00.0: irq 107 for MSI/MSI-X
[   10.396039] ppdev: user-space parallel port driver
[   10.443340] bnx2 0000:03:00.0: eth2: using MSIX
[   10.445128] ADDRCONF(NETDEV_UP): eth2: link is not ready
[   10.446946]   alloc irq_desc for 108 on node -1
[   10.446949]   alloc kstat_irqs on node -1
[   10.446956] alloc irq_2_iommu on node -1
[   10.446964] bnx2 0000:03:00.1: irq 108 for MSI/MSI-X
[   10.446966]   alloc irq_desc for 109 on node -1
[   10.446968]   alloc kstat_irqs on node -1
[   10.446971] alloc irq_2_iommu on node -1
[   10.446976] bnx2 0000:03:00.1: irq 109 for MSI/MSI-X
[   10.446978]   alloc irq_desc for 110 on node -1
[   10.446980]   alloc kstat_irqs on node -1
[   10.446983] alloc irq_2_iommu on node -1
[   10.446987] bnx2 0000:03:00.1: irq 110 for MSI/MSI-X
[   10.446989]   alloc irq_desc for 111 on node -1
[   10.446991]   alloc kstat_irqs on node -1
[   10.446994] alloc irq_2_iommu on node -1
[   10.446998] bnx2 0000:03:00.1: irq 111 for MSI/MSI-X
[   10.447001]   alloc irq_desc for 112 on node -1
[   10.447002]   alloc kstat_irqs on node -1
[   10.447005] alloc irq_2_iommu on node -1
[   10.447009] bnx2 0000:03:00.1: irq 112 for MSI/MSI-X
[   10.447012]   alloc irq_desc for 113 on node -1
[   10.447014]   alloc kstat_irqs on node -1
[   10.447016] alloc irq_2_iommu on node -1
[   10.447021] bnx2 0000:03:00.1: irq 113 for MSI/MSI-X
[   10.447023]   alloc irq_desc for 114 on node -1
[   10.447025]   alloc kstat_irqs on node -1
[   10.447027] alloc irq_2_iommu on node -1
[   10.447032] bnx2 0000:03:00.1: irq 114 for MSI/MSI-X
[   10.447034]   alloc irq_desc for 115 on node -1
[   10.447036]   alloc kstat_irqs on node -1
[   10.447038] alloc irq_2_iommu on node -1
[   10.447043] bnx2 0000:03:00.1: irq 115 for MSI/MSI-X
[   10.447045]   alloc irq_desc for 116 on node -1
[   10.447047]   alloc kstat_irqs on node -1
[   10.447049] alloc irq_2_iommu on node -1
[   10.447054] bnx2 0000:03:00.1: irq 116 for MSI/MSI-X
[   10.503147] bnx2 0000:03:00.1: eth3: using MSIX
[   10.504934] ADDRCONF(NETDEV_UP): eth3: link is not ready
[   10.513934] JBD: barrier-based sync failed on cciss!c0d0p1-8 - disabling barriers
[   10.795857] vboxdrv: Found 8 processor cores.
[   10.796694] VBoxDrv: dbg - g_abExecMemory=ffffffffa0261400
[   10.796949] vboxdrv: fAsync=0 offMin=0x20f offMax=0xcf4d
[   10.797033] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   10.797037] vboxdrv: Successfully loaded version 4.1.8 (interface 0x00190000).
[   11.014720] vboxpci: IOMMU not found (not registered)
[   12.128194] EXT4-fs (cciss!c0d0p1): re-mounted. Opts: errors=remount-ro,commit=0
[   12.468697] JBD: barrier-based sync failed on cciss!c0d0p1-8 - disabling barriers
[   12.651669] EXT4-fs (cciss!c0d0p1): re-mounted. Opts: errors=remount-ro,commit=0
[   12.957995] JBD: barrier-based sync failed on cciss!c0d0p1-8 - disabling barriers
[   13.616856] bnx2 0000:02:00.0: eth0: NIC Copper Link is Up, 1000 Mbps full duplex
[   13.618144] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   17.029018] Registering the dns_resolver key type
[   24.167228] eth0: no IPv6 routers present
[49301.077177] warning: `VBoxHeadless' uses 32-bit capabilities (legacy support in use)
[49614.563434] device eth0 entered promiscuous mode
[50395.599824] CE: hpet increased min_delta_ns to 7500 nsec
[60027.764961] CE: hpet increased min_delta_ns to 11250 nsec
[65961.200234] device eth0 left promiscuous mode
[65966.901136] vboxnetflt: dropped 0 out of 3943051 packets

```

---

