---
title: "Accessing TV Card in Windoze xp in virtual box."
date: 2010-01-13
forum: Virtualisation
---

### Post by hariks0 on 2010-01-13
I have tried a lot of threads for using my TV Tuner in Ubuntu and have given up. As it worked perfectly with windoze xp, I installed wxp in virtualbox but there is no tv tuner card visible in the device manager. How can i make widowze detect it?

Thanks in advance.

---

### Post by ajgreeny on 2010-01-13
I suspect that if the card is not available in the host system, ubuntu, it will not be available in the guest system either.  Hardware drivers are needed for the host for them to work in the guest, I think, they do not use their own windows drivers.

---

### Post by hariks0 on 2010-01-13
But it worked in wxp while i used dualboot.

---

### Post by ajgreeny on 2010-01-14
That's because when dual booting you would have been using the windows drivers for the card.  When in a VM the drivers used are the ubuntu ones, which it appears do not exist.

I'm sorry to say, but I don't think you are going to have any luck with your wish to use it in a VM of windows.

---

### Post by hariks0 on 2010-01-14
Then can you please help me to setup cable TV in Ubuntu itself? That is the only thing now I use windoze for.The hardware info is as follows:-

Philips SAA713x TV Card and it has FM Radio reception also.

In the installation screen [from CD] there is another option that reads Install Bt 878 V Card. I installed Philips SAA713x as found in the package cover. In windows this worked fine.

---

### Post by Jose Catre-Vandis on 2010-01-15
Please post relevant **dmesg** and **lspci -v** outputs. You may be needing some firmware to get your card going in Ubuntu.

However, it won't be picked up by XP inside Virtualbox

---

### Post by hariks0 on 2010-01-15
Thank you.Here are the outputs. They are very long and I don't know which part you need.
```
hari@Indira:~$ dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.31-17-generic (buildd@palmer) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #54-Ubuntu SMP Thu Dec 10 16:20:31 UTC 2009 (Ubuntu 2.6.31-17.54-generic)
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
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000008f000 (usable)
[    0.000000]  BIOS-e820: 000000000008f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000009e5a9000 (usable)
[    0.000000]  BIOS-e820: 000000009e5a9000 - 000000009e6ad000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000009e6ad000 - 000000009f594000 (usable)
[    0.000000]  BIOS-e820: 000000009f594000 - 000000009f59c000 (reserved)
[    0.000000]  BIOS-e820: 000000009f59c000 - 000000009f62a000 (usable)
[    0.000000]  BIOS-e820: 000000009f62a000 - 000000009f62e000 (reserved)
[    0.000000]  BIOS-e820: 000000009f62e000 - 000000009f6a9000 (usable)
[    0.000000]  BIOS-e820: 000000009f6a9000 - 000000009f6e9000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000009f6e9000 - 000000009f6ed000 (usable)
[    0.000000]  BIOS-e820: 000000009f6ed000 - 000000009f6ff000 (ACPI data)
[    0.000000]  BIOS-e820: 000000009f6ff000 - 000000009f700000 (usable)
[    0.000000]  BIOS-e820: 000000009f700000 - 00000000a0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.4 present.
[    0.000000] last_pfn = 0x9f700 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-FFFFF uncachable
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 080000000 mask FE0000000 write-back
[    0.000000]   2 base 09F800000 mask FFF800000 uncachable
[    0.000000]   3 base 09F700000 mask FFFF00000 uncachable
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 0000000000002000 - 0000000000006000 (usable) ==> (reserved)
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 000000000008f000 (usable)
[    0.000000]  modified: 000000000008f000 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000009e5a9000 (usable)
[    0.000000]  modified: 000000009e5a9000 - 000000009e6ad000 (ACPI NVS)
[    0.000000]  modified: 000000009e6ad000 - 000000009f594000 (usable)
[    0.000000]  modified: 000000009f594000 - 000000009f59c000 (reserved)
[    0.000000]  modified: 000000009f59c000 - 000000009f62a000 (usable)
[    0.000000]  modified: 000000009f62a000 - 000000009f62e000 (reserved)
[    0.000000]  modified: 000000009f62e000 - 000000009f6a9000 (usable)
[    0.000000]  modified: 000000009f6a9000 - 000000009f6e9000 (ACPI NVS)
[    0.000000]  modified: 000000009f6e9000 - 000000009f6ed000 (usable)
[    0.000000]  modified: 000000009f6ed000 - 000000009f6ff000 (ACPI data)
[    0.000000]  modified: 000000009f6ff000 - 000000009f700000 (usable)
[    0.000000]  modified: 000000009f700000 - 00000000a0000000 (reserved)
[    0.000000]  modified: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 7000-c000
[    0.000000] RAMDISK: 375f4000 - 37fefcad
[    0.000000] Allocated new RAMDISK: 008ad000 - 012a8cad
[    0.000000] Move RAMDISK from 00000000375f4000 - 0000000037fefcac to 008ad000 - 012a8cac
[    0.000000] ACPI: RSDP 000fe020 00014 (v00 INTEL )
[    0.000000] ACPI: RSDT 9f6fd038 00050 (v01 INTEL  D945GCR  0000000A      01000013)
[    0.000000] ACPI: FACP 9f6fc000 00074 (v01 INTEL  D945GCR  0000000A MSFT 01000013)
[    0.000000] ACPI: DSDT 9f6f7000 04C39 (v01 INTEL  D945GCR  0000000A MSFT 01000013)
[    0.000000] ACPI: FACS 9f6a9000 00040
[    0.000000] ACPI: APIC 9f6f6000 00078 (v01 INTEL  D945GCR  0000000A MSFT 01000013)
[    0.000000] ACPI: WDDT 9f6f5000 00040 (v01 INTEL  D945GCR  0000000A MSFT 01000013)
[    0.000000] ACPI: MCFG 9f6f4000 0003C (v01 INTEL  D945GCR  0000000A MSFT 01000013)
[    0.000000] ACPI: ASF! 9f6f3000 000A6 (v32 INTEL  D945GCR  0000000A MSFT 01000013)
[    0.000000] ACPI: HPET 9f6f2000 00038 (v01 INTEL  D945GCR  0000000A MSFT 01000013)
[    0.000000] ACPI: SSDT 9f6f1000 001BC (v01 INTEL     CpuPm 0000000A MSFT 01000013)
[    0.000000] ACPI: SSDT 9f6f0000 00175 (v01 INTEL   Cpu0Ist 0000000A MSFT 01000013)
[    0.000000] ACPI: SSDT 9f6ef000 00175 (v01 INTEL   Cpu1Ist 0000000A MSFT 01000013)
[    0.000000] ACPI: SSDT 9f6ee000 00175 (v01 INTEL   Cpu2Ist 0000000A MSFT 01000013)
[    0.000000] ACPI: SSDT 9f6ed000 00175 (v01 INTEL   Cpu3Ist 0000000A MSFT 01000013)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 1663MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000]   node 0 low ram: 00000000 - 377fe000
[    0.000000]   node 0 bootmap 00008000 - 0000ef00
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008a80a0]    TEXT DATA BSS ==> [0000100000 - 00008a80a0]
[    0.000000]   #4 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #5 [00008a9000 - 00008ac161]              BRK ==> [00008a9000 - 00008ac161]
[    0.000000]   #6 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
[    0.000000]   #7 [00008ad000 - 00012a8cad]      NEW RAMDISK ==> [00008ad000 - 00012a8cad]
[    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]
[    0.000000] found SMP MP-table at [c00fe200] fe200
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0009f700
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[8] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x0000008f
[    0.000000]     0: 0x00000100 -> 0x0009e5a9
[    0.000000]     0: 0x0009e6ad -> 0x0009f594
[    0.000000]     0: 0x0009f59c -> 0x0009f62a
[    0.000000]     0: 0x0009f62e -> 0x0009f6a9
[    0.000000]     0: 0x0009f6e9 -> 0x0009f6ed
[    0.000000]     0: 0x0009f6ff -> 0x0009f700
[    0.000000] On node 0 totalpages: 652585
[    0.000000] free_area_init_node: node 0, pgdat c0784960, node_mem_map c12a9000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3947 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 3327 pages used for memmap
[    0.000000]   HighMem zone: 422049 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 000000000008f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at a0000000 (gap: a0000000:5ff80000)
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages at c26a3000, static data 35612 bytes
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 647482
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-17-generic root=UUID=70c1fc36-030d-4e26-a9e8-3f3ce5f98a47 ro vga=771 quiet splash
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 13061120 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0009f700)
[    0.000000] Memory: 2557112k/2612224k available (4566k kernel code, 52340k reserved, 2142k data, 540k init, 1701504k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc078e000 - 0xc0815000   ( 540 kB)
[    0.000000]       .data : 0xc0575a64 - 0xc078d408   (2142 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0575a64   (4566 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=128, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] NR_IRQS:2304 nr_irqs:440
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2992.666 MHz processor.
[    0.000028] Console: colour dummy device 80x25
[    0.000033] console [tty0] enabled
[    0.000162] hpet clockevent registered
[    0.000166] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.000172] Calibrating delay loop (skipped), value calculated using timer frequency.. 5985.33 BogoMIPS (lpj=11970664)
[    0.000193] Security Framework initialized
[    0.000214] AppArmor: AppArmor initialized
[    0.000224] Mount-cache hash table entries: 512
[    0.000377] Initializing cgroup subsys ns
[    0.000382] Initializing cgroup subsys cpuacct
[    0.000388] Initializing cgroup subsys memory
[    0.000395] Initializing cgroup subsys freezer
[    0.000398] Initializing cgroup subsys net_cls
[    0.000420] CPU: Trace cache: 12K uops, L1 D cache: 16K
[    0.000424] CPU: L2 cache: 2048K
[    0.000428] CPU: Physical Processor ID: 0
[    0.000430] CPU: Processor Core ID: 0
[    0.000434] mce: CPU supports 4 MCE banks
[    0.000447] CPU0: Thermal monitoring enabled (TM1)
[    0.000453] using mwait in idle threads.
[    0.000460] Performance Counters: no PMU driver, software counters only.
[    0.000467] Checking 'hlt' instruction... OK.
[    0.019539] ACPI: Core revision 20090521
[    0.031262] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.070959] CPU0: Intel(R) Pentium(R) D CPU 3.00GHz stepping 05
[    0.072001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 5985.04 BogoMIPS (lpj=11970096)
[    0.004000] CPU: Trace cache: 12K uops, L1 D cache: 16K
[    0.004000] CPU: L2 cache: 2048K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.004000] mce: CPU supports 4 MCE banks
[    0.004000] CPU1: Thermal monitoring enabled (TM1)
[    0.004000] x86 PAT enabled: cpu 1, old 0x7040600070406, new 0x7010600070106
[    0.157112] CPU1: Intel(R) Pentium(R) D CPU 3.00GHz stepping 05
[    0.157129] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.160019] Brought up 2 CPUs
[    0.160024] Total of 2 processors activated (11970.38 BogoMIPS).
[    0.160080] CPU0 attaching sched-domain:
[    0.160084]  domain 0: span 0-1 level CPU
[    0.160088]   groups: 0 1
[    0.160096] CPU1 attaching sched-domain:
[    0.160099]  domain 0: span 0-1 level CPU
[    0.160102]   groups: 1 0
[    0.160179] Booting paravirtualized kernel on bare hardware
[    0.160310] regulator: core version 0.5
[    0.160310] Time: 14:42:00  Date: 01/15/10
[    0.160310] NET: Registered protocol family 16
[    0.160310] EISA bus registered
[    0.160310] ACPI: bus type pci registered
[    0.160370] PCI: MCFG configuration 0: base f0000000 segment 0 buses 0 - 127
[    0.160374] PCI: Not using MMCONFIG.
[    0.164893] PCI: Using configuration type 1 for base access
[    0.166265] bio: create slab <bio-0> at 0
[    0.166265] ACPI: EC: Look up EC in DSDT
[    0.171964] ACPI: Interpreter enabled
[    0.171972] ACPI: (supports S0 S1 S3 S4 S5)
[    0.172012] ACPI: Using IOAPIC for interrupt routing
[    0.172060] PCI: MCFG configuration 0: base f0000000 segment 0 buses 0 - 127
[    0.175297] PCI: MCFG area at f0000000 reserved in ACPI motherboard resources
[    0.175301] PCI: updated MCFG configuration 0: base f0000000 segment 0 buses 0 - 63
[    0.175304] PCI: Using MMCONFIG for extended config space
[    0.180865] ACPI: No dock devices found.
[    0.182244] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.182358] pci 0000:00:02.0: reg 10 32bit mmio: [0xb0200000-0xb027ffff]
[    0.182366] pci 0000:00:02.0: reg 14 io port: [0x20e0-0x20e7]
[    0.182373] pci 0000:00:02.0: reg 18 32bit mmio: [0xa0000000-0xafffffff]
[    0.182379] pci 0000:00:02.0: reg 1c 32bit mmio: [0xb0280000-0xb02bffff]
[    0.182480] pci 0000:00:1b.0: reg 10 64bit mmio: [0xb02c0000-0xb02c3fff]
[    0.182532] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.182538] pci 0000:00:1b.0: PME# disabled
[    0.182611] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.182617] pci 0000:00:1c.0: PME# disabled
[    0.182692] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.182697] pci 0000:00:1c.1: PME# disabled
[    0.182772] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.182777] pci 0000:00:1c.2: PME# disabled
[    0.182855] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.182861] pci 0000:00:1c.3: PME# disabled
[    0.182919] pci 0000:00:1d.0: reg 20 io port: [0x2080-0x209f]
[    0.182979] pci 0000:00:1d.1: reg 20 io port: [0x2060-0x207f]
[    0.183039] pci 0000:00:1d.2: reg 20 io port: [0x2040-0x205f]
[    0.183098] pci 0000:00:1d.3: reg 20 io port: [0x2020-0x203f]
[    0.183164] pci 0000:00:1d.7: reg 10 32bit mmio: [0xb02c4000-0xb02c43ff]
[    0.183224] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.183230] pci 0000:00:1d.7: PME# disabled
[    0.183374] pci 0000:00:1f.0: quirk: region 0400-047f claimed by ICH6 ACPI/GPIO/TCO
[    0.183380] pci 0000:00:1f.0: quirk: region 0500-053f claimed by ICH6 GPIO
[    0.183384] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0680 (mask 007f)
[    0.183436] pci 0000:00:1f.1: reg 10 io port: [0x00-0x07]
[    0.183444] pci 0000:00:1f.1: reg 14 io port: [0x00-0x03]
[    0.183453] pci 0000:00:1f.1: reg 18 io port: [0x00-0x07]
[    0.183461] pci 0000:00:1f.1: reg 1c io port: [0x00-0x03]
[    0.183469] pci 0000:00:1f.1: reg 20 io port: [0x20b0-0x20bf]
[    0.183520] pci 0000:00:1f.2: reg 10 io port: [0x20c8-0x20cf]
[    0.183528] pci 0000:00:1f.2: reg 14 io port: [0x20ec-0x20ef]
[    0.183535] pci 0000:00:1f.2: reg 18 io port: [0x20c0-0x20c7]
[    0.183543] pci 0000:00:1f.2: reg 1c io port: [0x20e8-0x20eb]
[    0.183551] pci 0000:00:1f.2: reg 20 io port: [0x20a0-0x20af]
[    0.183580] pci 0000:00:1f.2: PME# supported from D3hot
[    0.183585] pci 0000:00:1f.2: PME# disabled
[    0.183639] pci 0000:00:1f.3: reg 20 io port: [0x2000-0x201f]
[    0.183792] pci 0000:02:00.0: reg 10 io port: [0x1000-0x10ff]
[    0.183818] pci 0000:02:00.0: reg 18 64bit mmio: [0xb0100000-0xb0100fff]
[    0.183844] pci 0000:02:00.0: reg 30 32bit mmio: [0xfffe0000-0xffffffff]
[    0.183899] pci 0000:02:00.0: supports D1 D2
[    0.183902] pci 0000:02:00.0: PME# supported from D1 D2 D3hot D3cold
[    0.183908] pci 0000:02:00.0: PME# disabled
[    0.183973] pci 0000:00:1c.1: bridge io port: [0x1000-0x1fff]
[    0.183978] pci 0000:00:1c.1: bridge 32bit mmio: [0xb0100000-0xb01fffff]
[    0.184147] pci 0000:05:04.0: reg 10 32bit mmio: [0xb0000000-0xb00003ff]
[    0.184204] pci 0000:05:04.0: supports D1 D2
[    0.184252] pci 0000:00:1e.0: transparent bridge
[    0.184260] pci 0000:00:1e.0: bridge 32bit mmio: [0xb0000000-0xb00fffff]
[    0.184292] pci_bus 0000:00: on NUMA node 0
[    0.184298] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.184548] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P32_._PRT]
[    0.184689] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
[    0.184778] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX1._PRT]
[    0.184867] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX2._PRT]
[    0.184956] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX3._PRT]
[    0.190350] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 10 *11 12)
[    0.190498] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 9 *10 11 12)
[    0.190645] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 *10 11 12)
[    0.190796] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 *9 10 11 12)
[    0.190942] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
[    0.191090] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
[    0.191237] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 *9 10 11 12)
[    0.191384] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 9 10 *11 12)
[    0.191627] SCSI subsystem initialized
[    0.191655] libata version 3.00 loaded.
[    0.191655] usbcore: registered new interface driver usbfs
[    0.191655] usbcore: registered new interface driver hub
[    0.191655] usbcore: registered new device driver usb
[    0.192078] ACPI: WMI: Mapper loaded
[    0.192081] PCI: Using ACPI for IRQ routing
[    0.204013] Bluetooth: Core ver 2.15
[    0.204039] NET: Registered protocol family 31
[    0.204039] Bluetooth: HCI device and connection manager initialized
[    0.204039] Bluetooth: HCI socket layer initialized
[    0.204039] NetLabel: Initializing
[    0.204039] NetLabel:  domain hash size = 128
[    0.204040] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.204058] NetLabel:  unlabeled traffic allowed by default
[    0.204098] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.204106] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.220012] pnp: PnP ACPI init
[    0.220028] ACPI: bus type pnp registered
[    0.223613] pnp: PnP ACPI: found 13 devices
[    0.223617] ACPI: ACPI bus type pnp unregistered
[    0.223622] PnPBIOS: Disabled by ACPI PNP
[    0.223635] system 00:01: iomem range 0xf0000000-0xf3ffffff has been reserved
[    0.223640] system 00:01: iomem range 0xfed13000-0xfed13fff has been reserved
[    0.223644] system 00:01: iomem range 0xfed14000-0xfed17fff has been reserved
[    0.223648] system 00:01: iomem range 0xfed18000-0xfed18fff has been reserved
[    0.223651] system 00:01: iomem range 0xfed19000-0xfed19fff has been reserved
[    0.223655] system 00:01: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    0.223659] system 00:01: iomem range 0xfed20000-0xfed3ffff has been reserved
[    0.223662] system 00:01: iomem range 0xfed45000-0xfed99fff has been reserved
[    0.223666] system 00:01: iomem range 0xc0000-0xdffff could not be reserved
[    0.223670] system 00:01: iomem range 0xe0000-0xfffff could not be reserved
[    0.223680] system 00:06: ioport range 0x500-0x53f has been reserved
[    0.223684] system 00:06: ioport range 0x400-0x47f has been reserved
[    0.223688] system 00:06: ioport range 0x680-0x6ff has been reserved
[    0.223692] system 00:06: ioport range 0x770-0x77f has been reserved
[    0.258395] AppArmor: AppArmor Filesystem Enabled
[    0.258418] pci 0000:02:00.0: BAR 6: no parent found for of device [0xfffe0000-0xffffffff]
[    0.258468] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:01
[    0.258472] pci 0000:00:1c.0:   IO window: disabled
[    0.258477] pci 0000:00:1c.0:   MEM window: disabled
[    0.258482] pci 0000:00:1c.0:   PREFETCH window: disabled
[    0.258489] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:02
[    0.258493] pci 0000:00:1c.1:   IO window: 0x1000-0x1fff
[    0.258499] pci 0000:00:1c.1:   MEM window: 0xb0100000-0xb01fffff
[    0.258505] pci 0000:00:1c.1:   PREFETCH window: 0xb0300000-0xb03fffff
[    0.258510] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:03
[    0.258512] pci 0000:00:1c.2:   IO window: disabled
[    0.258518] pci 0000:00:1c.2:   MEM window: disabled
[    0.258523] pci 0000:00:1c.2:   PREFETCH window: disabled
[    0.258527] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:04
[    0.258530] pci 0000:00:1c.3:   IO window: disabled
[    0.258535] pci 0000:00:1c.3:   MEM window: disabled
[    0.258540] pci 0000:00:1c.3:   PREFETCH window: disabled
[    0.258545] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:05
[    0.258548] pci 0000:00:1e.0:   IO window: disabled
[    0.258554] pci 0000:00:1e.0:   MEM window: 0xb0000000-0xb00fffff
[    0.258558] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.258572]   alloc irq_desc for 17 on node -1
[    0.258576]   alloc kstat_irqs on node -1
[    0.258583] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.258589] pci 0000:00:1c.0: setting latency timer to 64
[    0.258600]   alloc irq_desc for 16 on node -1
[    0.258603]   alloc kstat_irqs on node -1
[    0.258608] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.258613] pci 0000:00:1c.1: setting latency timer to 64
[    0.258622]   alloc irq_desc for 18 on node -1
[    0.258624]   alloc kstat_irqs on node -1
[    0.258629] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.258634] pci 0000:00:1c.2: setting latency timer to 64
[    0.258643]   alloc irq_desc for 19 on node -1
[    0.258645]   alloc kstat_irqs on node -1
[    0.258650] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.258655] pci 0000:00:1c.3: setting latency timer to 64
[    0.258663] pci 0000:00:1e.0: setting latency timer to 64
[    0.258669] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.258672] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.258676] pci_bus 0000:02: resource 0 io:  [0x1000-0x1fff]
[    0.258679] pci_bus 0000:02: resource 1 mem: [0xb0100000-0xb01fffff]
[    0.258682] pci_bus 0000:02: resource 2 pref mem [0xb0300000-0xb03fffff]
[    0.258686] pci_bus 0000:05: resource 1 mem: [0xb0000000-0xb00fffff]
[    0.258689] pci_bus 0000:05: resource 3 io:  [0x00-0xffff]
[    0.258692] pci_bus 0000:05: resource 4 mem: [0x000000-0xffffffff]
[    0.258737] NET: Registered protocol family 2
[    0.258865] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.259302] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.259882] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.260183] TCP: Hash tables configured (established 131072 bind 65536)
[    0.260186] TCP reno registered
[    0.260285] NET: Registered protocol family 1
[    0.260366] Trying to unpack rootfs image as initramfs...
[    0.501028] Switched to high resolution mode on CPU 1
[    0.503992] Switched to high resolution mode on CPU 0
[    0.589158] Freeing initrd memory: 10223k freed
[    0.595026] cpufreq-nforce2: No nForce2 chipset.
[    0.595064] Scanning for low memory corruption every 60 seconds
[    0.595185] audit: initializing netlink socket (disabled)
[    0.595201] type=2000 audit(1263566520.592:1): initialized
[    0.604322] highmem bounce pool size: 64 pages
[    0.604329] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.606197] VFS: Disk quotas dquot_6.5.2
[    0.606278] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.607035] fuse init (API version 7.12)
[    0.607148] msgmni has been set to 1692
[    0.607490] alg: No test for stdrng (krng)
[    0.607520] io scheduler noop registered
[    0.607524] io scheduler anticipatory registered
[    0.607526] io scheduler deadline registered
[    0.607587] io scheduler cfq registered (default)
[    0.607602] pci 0000:00:02.0: Boot video device
[    0.607941]   alloc irq_desc for 24 on node -1
[    0.607945]   alloc kstat_irqs on node -1
[    0.607958] pcieport-driver 0000:00:1c.0: irq 24 for MSI/MSI-X
[    0.607969] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    0.608150]   alloc irq_desc for 25 on node -1
[    0.608153]   alloc kstat_irqs on node -1
[    0.608162] pcieport-driver 0000:00:1c.1: irq 25 for MSI/MSI-X
[    0.608172] pcieport-driver 0000:00:1c.1: setting latency timer to 64
[    0.608319]   alloc irq_desc for 26 on node -1
[    0.608322]   alloc kstat_irqs on node -1
[    0.608332] pcieport-driver 0000:00:1c.2: irq 26 for MSI/MSI-X
[    0.608342] pcieport-driver 0000:00:1c.2: setting latency timer to 64
[    0.608488]   alloc irq_desc for 27 on node -1
[    0.608491]   alloc kstat_irqs on node -1
[    0.608500] pcieport-driver 0000:00:1c.3: irq 27 for MSI/MSI-X
[    0.608510] pcieport-driver 0000:00:1c.3: setting latency timer to 64
[    0.608625] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.608768] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.608922] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    0.608927] ACPI: Power Button [PWRF]
[    0.608993] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1
[    0.609001] ACPI: Sleep Button [SLPB]
[    0.609383] processor LNXCPU:00: registered as cooling_device0
[    0.609508] processor LNXCPU:01: registered as cooling_device1
[    0.611183] isapnp: Scanning for PnP cards...
[    0.964614] isapnp: No Plug & Play device found
[    0.966060] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.966174] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.966638] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.967948] brd: module loaded
[    0.968550] loop: module loaded
[    0.968639] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    0.968780] ata_piix 0000:00:1f.1: version 2.13
[    0.968795] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.968837] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.968922] scsi0 : ata_piix
[    0.969035] scsi1 : ata_piix
[    0.969466] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x20b0 irq 14
[    0.969471] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x20b8 irq 15
[    0.969505] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.969512] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    0.969563] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.969628] scsi2 : ata_piix
[    0.969703] ata2: port disabled. ignoring.
[    0.969751] scsi3 : ata_piix
[    0.970541] ata3: SATA max UDMA/133 cmd 0x20c8 ctl 0x20ec bmdma 0x20a0 irq 19
[    0.970545] ata4: SATA max UDMA/133 cmd 0x20c0 ctl 0x20e8 bmdma 0x20a8 irq 19
[    0.971731] Fixed MDIO Bus: probed
[    0.971778] PPP generic driver version 2.4.2
[    0.971897] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.971920]   alloc irq_desc for 23 on node -1
[    0.971923]   alloc kstat_irqs on node -1
[    0.971931] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.971945] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.971950] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.972009] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.975929] ehci_hcd 0000:00:1d.7: debug port 1
[    0.975937] ehci_hcd 0000:00:1d.7: cache line size of 128 is not supported
[    0.975952] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xb02c4000
[    0.988013] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.988129] usb usb1: configuration #1 chosen from 1 choice
[    0.988170] hub 1-0:1.0: USB hub found
[    0.988180] hub 1-0:1.0: 8 ports detected
[    0.988264] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.988288] uhci_hcd: USB Universal Host Controller Interface driver
[    0.988317] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.988324] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.988329] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.988369] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.988396] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00002080
[    0.988493] usb usb2: configuration #1 chosen from 1 choice
[    0.988530] hub 2-0:1.0: USB hub found
[    0.988539] hub 2-0:1.0: 2 ports detected
[    0.988600] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.988608] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.988612] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.988651] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.988676] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00002060
[    0.988779] usb usb3: configuration #1 chosen from 1 choice
[    0.988816] hub 3-0:1.0: USB hub found
[    0.988824] hub 3-0:1.0: 2 ports detected
[    0.988886] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.988894] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.988898] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.988937] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.988970] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00002040
[    0.989062] usb usb4: configuration #1 chosen from 1 choice
[    0.989100] hub 4-0:1.0: USB hub found
[    0.989109] hub 4-0:1.0: 2 ports detected
[    0.989165] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    0.989173] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    0.989177] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    0.989220] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    0.989254] uhci_hcd 0000:00:1d.3: irq 16, io base 0x00002020
[    0.989348] usb usb5: configuration #1 chosen from 1 choice
[    0.989385] hub 5-0:1.0: USB hub found
[    0.989394] hub 5-0:1.0: 2 ports detected
[    0.989518] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    0.992138] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.992147] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.992249] mice: PS/2 mouse device common for all mice
[    0.992375] rtc_cmos 00:03: RTC can wake from S4
[    0.992415] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    0.992443] rtc0: alarms up to one month, 114 bytes nvram, hpet irqs
[    0.992584] device-mapper: uevent: version 1.0.3
[    0.992702] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.992827] device-mapper: multipath: version 1.1.0 loaded
[    0.992832] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.993001] EISA: Probing bus 0 at eisa.0
[    0.993008] Cannot allocate resource for EISA slot 1
[    0.993010] Cannot allocate resource for EISA slot 2
[    0.993032] EISA: Detected 0 cards.
[    0.993200] cpuidle: using governor ladder
[    0.993203] cpuidle: using governor menu
[    0.993921] TCP cubic registered
[    0.994096] NET: Registered protocol family 10
[    0.994737] lo: Disabled Privacy Extensions
[    0.995250] NET: Registered protocol family 17
[    0.995272] Bluetooth: L2CAP ver 2.13
[    0.995275] Bluetooth: L2CAP socket layer initialized
[    0.995279] Bluetooth: SCO (Voice Link) ver 0.6
[    0.995281] Bluetooth: SCO socket layer initialized
[    0.995327] Bluetooth: RFCOMM TTY layer initialized
[    0.995332] Bluetooth: RFCOMM socket layer initialized
[    0.995334] Bluetooth: RFCOMM ver 1.11
[    0.995741] Using IPI No-Shortcut mode
[    0.995819] PM: Resume from disk failed.
[    0.995835] registered taskstats version 1
[    0.995964]   Magic number: 10:264:738
[    0.996029] rtc_cmos 00:03: setting system clock to 2010-01-15 14:42:01 UTC (1263566521)
[    0.996042] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.996045] EDD information not available.
[    1.011612] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    1.132180] ata3.01: NODEV after polling detection
[    1.140222] ata3.00: ATAPI: TSSTcorp CDDVDW SH-S203B, SB00, max UDMA/100
[    1.156255] ata3.00: configured for UDMA/100
[    1.157578] scsi 2:0:0:0: CD-ROM            TSSTcorp CDDVDW SH-S203B  SB00 PQ: 0 ANSI: 5
[    1.161926] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.161932] Uniform CD-ROM driver Revision: 3.20
[    1.162058] sr 2:0:0:0: Attached scsi CD-ROM sr0
[    1.162113] sr 2:0:0:0: Attached scsi generic sg0 type 5
[    1.164931] ata4.00: ATA-7: ST3250820SV, 3.ACH, max UDMA/133
[    1.164937] ata4.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.231597] ata4.00: configured for UDMA/133
[    1.231720] scsi 3:0:0:0: Direct-Access     ATA      ST3250820SV      3.AC PQ: 0 ANSI: 5
[    1.231880] sd 3:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    1.231900] sd 3:0:0:0: Attached scsi generic sg1 type 0
[    1.231966] sd 3:0:0:0: [sda] Write Protect is off
[    1.231970] sd 3:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.232011] sd 3:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.232182]  sda: sda1 sda2 < sda5 sda6 sda7 sda8 sda9 >
[    1.349053] sd 3:0:0:0: [sda] Attached SCSI disk
[    1.349077] Freeing unused kernel memory: 540k freed
[    1.349501] Write protecting the kernel text: 4568k
[    1.349560] Write protecting the kernel read-only data: 1836k
[    1.500574] ramzswap: disk size set to 642188 kB
[    1.533932] Linux agpgart interface v0.103
[    1.538868] agpgart-intel 0000:00:00.0: Intel 945G Chipset
[    1.539713] agpgart-intel 0000:00:00.0: detected 7932K stolen memory
[    1.543066] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xa0000000
[    1.586605] [drm] Initialized drm 1.1.0 20060810
[    1.666641] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.666649] i915 0000:00:02.0: setting latency timer to 64
[    1.672224] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.672246] r8169 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.672305] r8169 0000:02:00.0: setting latency timer to 64
[    1.672370]   alloc irq_desc for 28 on node -1
[    1.672373]   alloc kstat_irqs on node -1
[    1.672391] r8169 0000:02:00.0: irq 28 for MSI/MSI-X
[    1.673375] eth0: RTL8168b/8111b at 0xf85e2000, 00:19:d1:a7:15:66, XID 38500000 IRQ 28
[    1.683145] Adding 642184k swap on /dev/ramzswap0.  Priority:100 extents:1 across:642184k SSD
[    1.688562] usb 2-2: new full speed USB device using uhci_hcd and address 2
[    1.805155] [drm] fb0: inteldrmfb frame buffer device
[    1.805166] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    1.811716] Console: switching to colour frame buffer device 128x48
[    1.876264] [drm] DAC-6: set mode 1024x768 17
[    1.946517] usb 2-2: configuration #1 chosen from 1 choice
[    2.188021] usb 3-2: new full speed USB device using uhci_hcd and address 2
[    2.304057] vesafb: framebuffer at 0xa0000000, mapped to 0xf8b00000, using 512k, total 512k
[    2.304062] vesafb: mode is 800x600x8, linelength=832, pages=0
[    2.304065] vesafb: scrolling: redraw
[    2.304072] vesafb: Pseudocolor: size=0:8:8:8, shift=0:0:0:0
[    2.304138] fb1: VESA VGA frame buffer device
[    2.491212] xor: automatically using best checksumming function: pIII_sse
[    2.508504]    pIII_sse  :  4529.000 MB/sec
[    2.508508] xor: using function: pIII_sse (4529.000 MB/sec)
[    2.511676] device-mapper: dm-raid45: initialized v0.2594b
[    3.076968] PM: Starting manual resume from disk
[    3.076973] PM: Resume from partition 8:7
[    3.076976] PM: Checking hibernation image.
[    3.077116] PM: Resume from disk failed.
[    3.096449] EXT4-fs (sda8): INFO: recovery required on readonly filesystem
[    3.096457] EXT4-fs (sda8): write access will be enabled during recovery
[    3.099826] EXT4-fs (sda8): barriers enabled
[    3.637343] kjournald2 starting: pid 446, dev sda8:8, commit interval 5 seconds
[    3.637365] EXT4-fs (sda8): delayed allocation enabled
[    3.637370] EXT4-fs: file extents enabled
[    3.638842] EXT4-fs: mballoc enabled
[    3.638862] EXT4-fs (sda8): recovery complete
[    3.639182] EXT4-fs (sda8): mounted filesystem with ordered data mode
[   12.353590] usb 3-2: configuration #1 chosen from 1 choice
[   23.575089] udev: starting version 147
[   23.609371] Adding 4883720k swap on /dev/sda7.  Priority:-1 extents:1 across:4883720k 
[   23.885777] Linux video capture interface: v2.00
[   24.007168] parport_pc 00:07: reported by Plug and Play ACPI
[   24.007196] parport0: PC-style at 0x378, irq 7 [PCSPP,EPP]
[   24.021639] psmouse serio1: ID: 10 00 64
[   24.055903] gspca: main v2.6.0 registered
[   24.059299] gspca: probing 04fc:0561
[   24.066171] Bluetooth: Generic Bluetooth USB driver ver 0.5
[   24.066306] usbcore: registered new interface driver btusb
[   24.072854] intel_rng: FWH not detected
[   24.077776] ppdev: user-space parallel port driver
[   24.345479] lp0: using parport0 (interrupt-driven).
[   24.404984] gspca: probe ok
[   24.405018] usbcore: registered new interface driver spca561
[   24.405023] spca561: registered
[   24.453497] saa7130/34: v4l2 driver version 0.2.15 loaded
[   24.453565] saa7134 0000:05:04.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   24.453578] saa7130[0]: found at 0000:05:04.0, rev: 1, irq: 18, latency: 32, mmio: 0xb0000000
[   24.453586] saa7134: <rant>
[   24.453587] saa7134:  Congratulations!  Your TV card vendor saved a few
[   24.453589] saa7134:  cents for a eeprom, thus your pci board has no
[   24.453590] saa7134:  subsystem ID and I can't identify it automatically
[   24.453592] saa7134: </rant>
[   24.453593] saa7134: I feel better now.  Ok, here are the good news:
[   24.453594] saa7134: You can use the card=<nr> insmod option to specify
[   24.453595] saa7134: which board do you have.  The list:
[   24.453599] saa7134:   card=0 -> UNKNOWN/GENERIC                         
[   24.453603] saa7134:   card=1 -> Proteus Pro [philips reference design]   1131:2001 1131:2001
[   24.453610] saa7134:   card=2 -> LifeView FlyVIDEO3000                    5168:0138 4e42:0138
[   24.453616] saa7134:   card=3 -> LifeView/Typhoon FlyVIDEO2000            5168:0138 4e42:0138
[   24.453622] saa7134:   card=4 -> EMPRESS                                  1131:6752
[   24.453627] saa7134:   card=5 -> SKNet Monster TV                         1131:4e85
[   24.453631] saa7134:   card=6 -> Tevion MD 9717                          
[   24.453635] saa7134:   card=7 -> KNC One TV-Station RDS / Typhoon TV Tune 1131:fe01 1894:fe01
[   24.453641] saa7134:   card=8 -> Terratec Cinergy 400 TV                  153b:1142
[   24.453646] saa7134:   card=9 -> Medion 5044                             
[   24.453649] saa7134:   card=10 -> Kworld/KuroutoShikou SAA7130-TVPCI      
[   24.453653] saa7134:   card=11 -> Terratec Cinergy 600 TV                  153b:1143
[   24.453658] saa7134:   card=12 -> Medion 7134                              16be:0003 16be:5000
[   24.453664] saa7134:   card=13 -> Typhoon TV+Radio 90031                  
[   24.453668] saa7134:   card=14 -> ELSA EX-VISION 300TV                     1048:226b
[   24.453672] saa7134:   card=15 -> ELSA EX-VISION 500TV                     1048:226a
[   24.453677] saa7134:   card=16 -> ASUS TV-FM 7134                          1043:4842 1043:4830 1043:4840
[   24.453684] saa7134:   card=17 -> AOPEN VA1000 POWER                       1131:7133
[   24.453689] saa7134:   card=18 -> BMK MPEX No Tuner                       
[   24.453692] saa7134:   card=19 -> Compro VideoMate TV                      185b:c100
[   24.453697] saa7134:   card=20 -> Matrox CronosPlus                        102b:48d0
[   24.453702] saa7134:   card=21 -> 10MOONS PCI TV CAPTURE CARD              1131:2001
[   24.453707] saa7134:   card=22 -> AverMedia M156 / Medion 2819             1461:a70b
[   24.453711] saa7134:   card=23 -> BMK MPEX Tuner                          
[   24.453715] saa7134:   card=24 -> KNC One TV-Station DVR                   1894:a006
[   24.453720] saa7134:   card=25 -> ASUS TV-FM 7133                          1043:4843
[   24.453725] saa7134:   card=26 -> Pinnacle PCTV Stereo (saa7134)           11bd:002b
[   24.453729] saa7134:   card=27 -> Manli MuchTV M-TV002                    
[   24.453733] saa7134:   card=28 -> Manli MuchTV M-TV001                    
[   24.453737] saa7134:   card=29 -> Nagase Sangyo TransGear 3000TV           1461:050c
[   24.453741] saa7134:   card=30 -> Elitegroup ECS TVP3XP FM1216 Tuner Card( 1019:4cb4
[   24.453746] saa7134:   card=31 -> Elitegroup ECS TVP3XP FM1236 Tuner Card  1019:4cb5
[   24.453751] saa7134:   card=32 -> AVACS SmartTV                           
[   24.453755] saa7134:   card=33 -> AVerMedia DVD EZMaker                    1461:10ff
[   24.453759] saa7134:   card=34 -> Noval Prime TV 7133                     
[   24.453763] saa7134:   card=35 -> AverMedia AverTV Studio 305              1461:2115
[   24.453768] saa7134:   card=36 -> UPMOST PURPLE TV                         12ab:0800
[   24.453773] saa7134:   card=37 -> Items MuchTV Plus / IT-005              
[   24.453776] saa7134:   card=38 -> Terratec Cinergy 200 TV                  153b:1152
[   24.453781] saa7134:   card=39 -> LifeView FlyTV Platinum Mini             5168:0212 4e42:0212 5169:1502
[   24.453788] saa7134:   card=40 -> Compro VideoMate TV PVR/FM               185b:c100
[   24.453793] saa7134:   card=41 -> Compro VideoMate TV Gold+                185b:c100
[   24.453797] saa7134:   card=42 -> Sabrent SBT-TVFM (saa7130)              
[   24.453801] saa7134:   card=43 -> :Zolid Xpert TV7134                     
[   24.453805] saa7134:   card=44 -> Empire PCI TV-Radio LE                  
[   24.453808] saa7134:   card=45 -> Avermedia AVerTV Studio 307              1461:9715
[   24.453813] saa7134:   card=46 -> AVerMedia Cardbus TV/Radio (E500)        1461:d6ee
[   24.453818] saa7134:   card=47 -> Terratec Cinergy 400 mobile              153b:1162
[   24.453822] saa7134:   card=48 -> Terratec Cinergy 600 TV MK3              153b:1158
[   24.453827] saa7134:   card=49 -> Compro VideoMate Gold+ Pal               185b:c200
[   24.453832] saa7134:   card=50 -> Pinnacle PCTV 300i DVB-T + PAL           11bd:002d
[   24.453837] saa7134:   card=51 -> ProVideo PV952                           1540:9524
[   24.453841] saa7134:   card=52 -> AverMedia AverTV/305                     1461:2108
[   24.453846] saa7134:   card=53 -> ASUS TV-FM 7135                          1043:4845
[   24.453851] saa7134:   card=54 -> LifeView FlyTV Platinum FM / Gold        5168:0214 5168:5214 1489:0214 5168:0304
[   24.453859] saa7134:   card=55 -> LifeView FlyDVB-T DUO / MSI TV@nywhere D 5168:0306 4e42:0306
[   24.453864] saa7134:   card=56 -> Avermedia AVerTV 307                     1461:a70a
[   24.453869] saa7134:   card=57 -> Avermedia AVerTV GO 007 FM               1461:f31f
[   24.453874] saa7134:   card=58 -> ADS Tech Instant TV (saa7135)            1421:0350 1421:0351 1421:0370 1421:1370
[   24.453882] saa7134:   card=59 -> Kworld/Tevion V-Stream Xpert TV PVR7134 
[   24.453885] saa7134:   card=60 -> LifeView/Typhoon/Genius FlyDVB-T Duo Car 5168:0502 4e42:0502 1489:0502
[   24.453892] saa7134:   card=61 -> Philips TOUGH DVB-T reference design     1131:2004
[   24.453897] saa7134:   card=62 -> Compro VideoMate TV Gold+II             
[   24.453901] saa7134:   card=63 -> Kworld Xpert TV PVR7134                 
[   24.453904] saa7134:   card=64 -> FlyTV mini Asus Digimatrix               1043:0210
[   24.453909] saa7134:   card=65 -> V-Stream Studio TV Terminator           
[   24.453913] saa7134:   card=66 -> Yuan TUN-900 (saa7135)                  
[   24.453916] saa7134:   card=67 -> Beholder BeholdTV 409 FM                 0000:4091
[   24.453921] saa7134:   card=68 -> GoTView 7135 PCI                         5456:7135
[   24.453926] saa7134:   card=69 -> Philips EUROPA V3 reference design       1131:2004
[   24.453931] saa7134:   card=70 -> Compro Videomate DVB-T300                185b:c900
[   24.453936] saa7134:   card=71 -> Compro Videomate DVB-T200                185b:c901
[   24.453940] saa7134:   card=72 -> RTD Embedded Technologies VFG7350        1435:7350
[   24.453945] saa7134:   card=73 -> RTD Embedded Technologies VFG7330        1435:7330
[   24.453950] saa7134:   card=74 -> LifeView FlyTV Platinum Mini2            14c0:1212
[   24.453955] saa7134:   card=75 -> AVerMedia AVerTVHD MCE A180              1461:1044
[   24.453959] saa7134:   card=76 -> SKNet MonsterTV Mobile                   1131:4ee9
[   24.453964] saa7134:   card=77 -> Pinnacle PCTV 40i/50i/110i (saa7133)     11bd:002e
[   24.453969] saa7134:   card=78 -> ASUSTeK P7131 Dual                       1043:4862
[   24.453974] saa7134:   card=79 -> Sedna/MuchTV PC TV Cardbus TV/Radio (ITO
[   24.453977] saa7134:   card=80 -> ASUS Digimatrix TV                       1043:0210
[   24.453982] saa7134:   card=81 -> Philips Tiger reference design           1131:2018
[   24.453987] saa7134:   card=82 -> MSI TV@Anywhere plus                     1462:6231 1462:8624
[   24.453993] saa7134:   card=83 -> Terratec Cinergy 250 PCI TV              153b:1160
[   24.453997] saa7134:   card=84 -> LifeView FlyDVB Trio                     5168:0319
[   24.454002] saa7134:   card=85 -> AverTV DVB-T 777                         1461:2c05 1461:2c05
[   24.454008] saa7134:   card=86 -> LifeView FlyDVB-T / Genius VideoWonder D 5168:0301 1489:0301
[   24.454014] saa7134:   card=87 -> ADS Instant TV Duo Cardbus PTV331        0331:1421
[   24.454019] saa7134:   card=88 -> Tevion/KWorld DVB-T 220RF                17de:7201
[   24.454023] saa7134:   card=89 -> ELSA EX-VISION 700TV                     1048:226c
[   24.454028] saa7134:   card=90 -> Kworld ATSC110/115                       17de:7350 17de:7352
[   24.454034] saa7134:   card=91 -> AVerMedia A169 B                         1461:7360
[   24.454038] saa7134:   card=92 -> AVerMedia A169 B1                        1461:6360
[   24.454043] saa7134:   card=93 -> Medion 7134 Bridge #2                    16be:0005
[   24.454048] saa7134:   card=94 -> LifeView FlyDVB-T Hybrid Cardbus/MSI TV  5168:3306 5168:3502 5168:3307 4e42:3502
[   24.454056] saa7134:   card=95 -> LifeView FlyVIDEO3000 (NTSC)             5169:0138
[   24.454060] saa7134:   card=96 -> Medion Md8800 Quadro                     16be:0007 16be:0008 16be:000d
[   24.454067] saa7134:   card=97 -> LifeView FlyDVB-S /Acorp TV134DS         5168:0300 4e42:0300
[   24.454073] saa7134:   card=98 -> Proteus Pro 2309                         0919:2003
[   24.454078] saa7134:   card=99 -> AVerMedia TV Hybrid A16AR                1461:2c00
[   24.454083] saa7134:   card=100 -> Asus Europa2 OEM                         1043:4860
[   24.454087] saa7134:   card=101 -> Pinnacle PCTV 310i                       11bd:002f
[   24.454092] saa7134:   card=102 -> Avermedia AVerTV Studio 507              1461:9715
[   24.454097] saa7134:   card=103 -> Compro Videomate DVB-T200A              
[   24.454101] saa7134:   card=104 -> Hauppauge WinTV-HVR1110 DVB-T/Hybrid     0070:6700 0070:6701 0070:6702 0070:6703 0070:6704 0070:6705
[   24.454111] saa7134:   card=105 -> Terratec Cinergy HT PCMCIA               153b:1172
[   24.454116] saa7134:   card=106 -> Encore ENLTV                             1131:2342 1131:2341 3016:2344
[   24.454123] saa7134:   card=107 -> Encore ENLTV-FM                          1131:230f
[   24.454127] saa7134:   card=108 -> Terratec Cinergy HT PCI                  153b:1175
[   24.454132] saa7134:   card=109 -> Philips Tiger - S Reference design      
[   24.454136] saa7134:   card=110 -> Avermedia M102                           1461:f31e
[   24.454140] saa7134:   card=111 -> ASUS P7131 4871                          1043:4871
[   24.454145] saa7134:   card=112 -> ASUSTeK P7131 Hybrid                     1043:4876
[   24.454150] saa7134:   card=113 -> Elitegroup ECS TVP3XP FM1246 Tuner Card  1019:4cb6
[   24.454155] saa7134:   card=114 -> KWorld DVB-T 210                         17de:7250
[   24.454159] saa7134:   card=115 -> Sabrent PCMCIA TV-PCB05                  0919:2003
[   24.454164] saa7134:   card=116 -> 10MOONS TM300 TV Card                    1131:2304
[   24.454169] saa7134:   card=117 -> Avermedia Super 007                      1461:f01d
[   24.454174] saa7134:   card=118 -> Beholder BeholdTV 401                    0000:4016
[   24.454179] saa7134:   card=119 -> Beholder BeholdTV 403                    0000:4036
[   24.454183] saa7134:   card=120 -> Beholder BeholdTV 403 FM                 0000:4037
[   24.454188] saa7134:   card=121 -> Beholder BeholdTV 405                    0000:4050
[   24.454193] saa7134:   card=122 -> Beholder BeholdTV 405 FM                 0000:4051
[   24.454198] saa7134:   card=123 -> Beholder BeholdTV 407                    0000:4070
[   24.454203] saa7134:   card=124 -> Beholder BeholdTV 407 FM                 0000:4071
[   24.454207] saa7134:   card=125 -> Beholder BeholdTV 409                    0000:4090
[   24.454212] saa7134:   card=126 -> Beholder BeholdTV 505 FM                 5ace:5050
[   24.454217] saa7134:   card=127 -> Beholder BeholdTV 507 FM / BeholdTV 509  5ace:5070 5ace:5090
[   24.454223] saa7134:   card=128 -> Beholder BeholdTV Columbus TVFM          0000:5201
[   24.454228] saa7134:   card=129 -> Beholder BeholdTV 607 FM                 5ace:6070
[   24.454232] saa7134:   card=130 -> Beholder BeholdTV M6                     5ace:6190
[   24.454237] saa7134:   card=131 -> Twinhan Hybrid DTV-DVB 3056 PCI          1822:0022
[   24.454242] saa7134:   card=132 -> Genius TVGO AM11MCE                     
[   24.454246] saa7134:   card=133 -> NXP Snake DVB-S reference design        
[   24.454249] saa7134:   card=134 -> Medion/Creatix CTX953 Hybrid             16be:0010
[   24.454254] saa7134:   card=135 -> MSI TV@nywhere A/D v1.1                  1462:8625
[   24.454259] saa7134:   card=136 -> AVerMedia Cardbus TV/Radio (E506R)       1461:f436
[   24.454263] saa7134:   card=137 -> AVerMedia Hybrid TV/Radio (A16D)         1461:f936
[   24.454268] saa7134:   card=138 -> Avermedia M115                           1461:a836
[   24.454273] saa7134:   card=139 -> Compro VideoMate T750                    185b:c900
[   24.454278] saa7134:   card=140 -> Avermedia DVB-S Pro A700                 1461:a7a1
[   24.454282] saa7134:   card=141 -> Avermedia DVB-S Hybrid+FM A700           1461:a7a2
[   24.454287] saa7134:   card=142 -> Beholder BeholdTV H6                     5ace:6290
[   24.454292] saa7134:   card=143 -> Beholder BeholdTV M63                    5ace:6191
[   24.454296] saa7134:   card=144 -> Beholder BeholdTV M6 Extra               5ace:6193
[   24.454301] saa7134:   card=145 -> AVerMedia MiniPCI DVB-T Hybrid M103      1461:f636 1461:f736
[   24.454307] saa7134:   card=146 -> ASUSTeK P7131 Analog                    
[   24.454310] saa7134:   card=147 -> Asus Tiger 3in1                          1043:4878
[   24.454315] saa7134:   card=148 -> Encore ENLTV-FM v5.3                     1a7f:2008
[   24.454320] saa7134:   card=149 -> Avermedia PCI pure analog (M135A)        1461:f11d
[   24.454325] saa7134:   card=150 -> Zogis Real Angel 220                    
[   24.454328] saa7134:   card=151 -> ADS Tech Instant HDTV                    1421:0380
[   24.454333] saa7134:   card=152 -> Asus Tiger Rev:1.00                      1043:4857
[   24.454338] saa7134:   card=153 -> Kworld Plus TV Analog Lite PCI           17de:7128
[   24.454343] saa7134:   card=154 -> Avermedia AVerTV GO 007 FM Plus          1461:f31d
[   24.454347] saa7134:   card=155 -> Hauppauge WinTV-HVR1150 ATSC/QAM-Hybrid  0070:6706 0070:6708
[   24.454353] saa7134:   card=156 -> Hauppauge WinTV-HVR1120 DVB-T/Hybrid     0070:6707 0070:6709 0070:670a
[   24.454360] saa7134:   card=157 -> Avermedia AVerTV Studio 507UA            1461:a11b
[   24.454365] saa7134:   card=158 -> AVerMedia Cardbus TV/Radio (E501R)       1461:b7e9
[   24.454369] saa7134:   card=159 -> Beholder BeholdTV 505 RDS                0000:505b
[   24.454374] saa7134:   card=160 -> Beholder BeholdTV 507 RDS                0000:5071
[   24.454379] saa7134:   card=161 -> Beholder BeholdTV 507 RDS                0000:507b
[   24.454384] saa7134:   card=162 -> Beholder BeholdTV 607 FM                 5ace:6071
[   24.454388] saa7134:   card=163 -> Beholder BeholdTV 609 FM                 5ace:6090
[   24.454393] saa7134:   card=164 -> Beholder BeholdTV 609 FM                 5ace:6091
[   24.454398] saa7134:   card=165 -> Beholder BeholdTV 607 RDS                5ace:6072
[   24.454403] saa7134:   card=166 -> Beholder BeholdTV 607 RDS                5ace:6073
[   24.454407] saa7134:   card=167 -> Beholder BeholdTV 609 RDS                5ace:6092
[   24.454412] saa7134:   card=168 -> Beholder BeholdTV 609 RDS                5ace:6093
[   24.454418] saa7130[0]: subsystem: 1131:0000, board: UNKNOWN/GENERIC [card=0,autodetected]
[   24.454432] saa7130[0]: board init: gpio is 60c000
[   24.454438] IRQ 18/saa7130[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[   24.521276] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input4
[   24.556216] saa7130[0]: Huh, no eeprom present (err=-5)?
[   24.556222] i2c-adapter i2c-1: Invalid 7-bit address 0x7a
[   24.556815] saa7130[0]: registered device video1 [v4l2]
[   24.556848] saa7130[0]: registered device vbi0
[   24.791502] ip_tables: (C) 2000-2006 Netfilter Core Team
[   24.924208] saa7134 ALSA driver for DMA sound loaded
[   24.924213] saa7130[0]/alsa: UNKNOWN/GENERIC doesn't support digital audio
[   24.971916]   alloc irq_desc for 22 on node -1
[   24.971921]   alloc kstat_irqs on node -1
[   24.971930] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   24.971971] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   25.076317] hda_codec: Unknown model for ALC888, trying auto-probe from BIOS...
[   25.076427] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input5
[   28.400134] EXT4-fs (sda8): internal journal on sda8:8
[   29.192860] EXT4-fs (sda1): barriers enabled
[   29.208058] kjournald2 starting: pid 921, dev sda1:8, commit interval 5 seconds
[   29.208470] EXT4-fs (sda1): internal journal on sda1:8
[   29.208477] EXT4-fs (sda1): delayed allocation enabled
[   29.208483] EXT4-fs: file extents enabled
[   29.211082] EXT4-fs: mballoc enabled
[   29.211100] EXT4-fs (sda1): mounted filesystem with ordered data mode
[   30.634303] EXT4-fs (sda9): barriers enabled
[   30.640042] kjournald2 starting: pid 929, dev sda9:8, commit interval 5 seconds
[   30.640190] EXT4-fs (sda9): internal journal on sda9:8
[   30.640197] EXT4-fs (sda9): delayed allocation enabled
[   30.640203] EXT4-fs: file extents enabled
[   30.647477] EXT4-fs: mballoc enabled
[   30.647499] EXT4-fs (sda9): mounted filesystem with ordered data mode
[   30.778103] type=1505 audit(1263566551.279:2): operation="profile_load" pid=981 name=/usr/share/gdm/guest-session/Xsession
[   30.780575] type=1505 audit(1263566551.283:3): operation="profile_load" pid=988 name=/sbin/dhclient3
[   30.781336] type=1505 audit(1263566551.283:4): operation="profile_load" pid=988 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   30.781746] type=1505 audit(1263566551.283:5): operation="profile_load" pid=988 name=/usr/lib/connman/scripts/dhclient-script
[   30.785965] type=1505 audit(1263566551.287:6): operation="profile_load" pid=989 name=/usr/bin/evince
[   30.815913] type=1505 audit(1263566551.315:7): operation="profile_load" pid=989 name=/usr/bin/evince-previewer
[   30.822992] type=1505 audit(1263566551.323:8): operation="profile_load" pid=989 name=/usr/bin/evince-thumbnailer
[   30.857655] r8169: eth0: link down
[   30.857802] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   30.894960] type=1505 audit(1263566551.395:9): operation="profile_load" pid=1069 name=/usr/bin/freshclam
[   30.897426] type=1505 audit(1263566551.399:10): operation="profile_load" pid=1070 name=/usr/lib/cups/backend/cups-pdf
[   30.898307] type=1505 audit(1263566551.399:11): operation="profile_load" pid=1070 name=/usr/sbin/cupsd
[   34.489455] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   34.489460] Bluetooth: BNEP filters: protocol multicast
[   34.522002] Bridge firewalling registered
[   34.891915] CPU0 attaching NULL sched-domain.
[   34.891923] CPU1 attaching NULL sched-domain.
[   34.904603] CPU0 attaching sched-domain:
[   34.904608]  domain 0: span 0-1 level MC
[   34.904613]   groups: 0 1
[   34.904619]   domain 1: span 0-1 level CPU
[   34.904626]    groups: 0-1 (__cpu_power = 2048)
[   34.904633] CPU1 attaching sched-domain:
[   34.904636]  domain 0: span 0-1 level MC
[   34.904640]   groups: 1 0
[   34.904649]   domain 1: span 0-1 level CPU
[   34.904655]    groups: 0-1 (__cpu_power = 2048)
[   35.180203] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   35.180208] vboxdrv: Successfully done.
[   35.180210] vboxdrv: Found 2 processor cores.
[   35.180304] vboxdrv: fAsync=0 offMin=0x861 offMax=0x41be
[   35.180361] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   35.180365] vboxdrv: Successfully loaded version 3.1.2 (interface 0x00100001).
[   42.663078] CPU0 attaching NULL sched-domain.
[   42.663086] CPU1 attaching NULL sched-domain.
[   42.672621] CPU0 attaching sched-domain:
[   42.672628]  domain 0: span 0-1 level CPU
[   42.672633]   groups: 0 1
[   42.672646] CPU1 attaching sched-domain:
[   42.672650]  domain 0: span 0-1 level CPU
[   42.672654]   groups: 1 0
[   43.637099] [drm] DAC-6: set mode  18
[  229.191615] r8169: eth0: link up
[  229.191787] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  239.888015] eth0: no IPv6 routers present
hari@Indira:~$ 

```
```
hari@Indira:~$ lspci -v
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
	Subsystem: Intel Corporation Device d606
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
	Subsystem: Intel Corporation Device d606
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at b0200000 (32-bit, non-prefetchable) [size=512K]
	I/O ports at 20e0 [size=8]
	Memory at a0000000 (32-bit, prefetchable) [size=256M]
	Memory at b0280000 (32-bit, non-prefetchable) [size=256K]
	Capabilities: <access denied>
	Kernel driver in use: i915
	Kernel modules: i915

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
	Subsystem: Intel Corporation Device d606
	Flags: bus master, fast devsel, latency 0, IRQ 22
	Memory at b02c0000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 00001000-00001fff
	Memory behind bridge: b0100000-b01fffff
	Prefetchable memory behind bridge: ffffffffb0300000-00000000b03fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	Capabilities: <access denied>
	Kernel driver in use: pcieport-driver
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
	Subsystem: Intel Corporation Device d606
	Flags: bus master, medium devsel, latency 0, IRQ 23
	I/O ports at 2080 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
	Subsystem: Intel Corporation Device d606
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 2060 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
	Subsystem: Intel Corporation Device d606
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 2040 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
	Subsystem: Intel Corporation Device d606
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 2020 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01) (prog-if 20)
	Subsystem: Intel Corporation Device d606
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at b02c4000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1) (prog-if 01)
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=32
	Memory behind bridge: b0000000-b00fffff
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
	Subsystem: Intel Corporation Device d606
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: iTCO_wdt, intel-rng

00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01) (prog-if 8a [Master SecP PriP])
	Subsystem: Intel Corporation Device d606
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 20b0 [size=16]
	Kernel driver in use: ata_piix

00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01) (prog-if 8f [Master SecP SecO PriP PriO])
	Subsystem: Intel Corporation Device d606
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
	I/O ports at 20c8 [size=8]
	I/O ports at 20ec [size=4]
	I/O ports at 20c0 [size=8]
	I/O ports at 20e8 [size=4]
	I/O ports at 20a0 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
	Subsystem: Intel Corporation Device d606
	Flags: medium devsel, IRQ 9
	I/O ports at 2000 [size=32]
	Kernel modules: i2c-i801

02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
	Subsystem: Intel Corporation Device d606
	Flags: bus master, fast devsel, latency 0, IRQ 28
	I/O ports at 1000 [size=256]
	Memory at b0100000 (64-bit, non-prefetchable) [size=4K]
	Expansion ROM at b0300000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: r8169
	Kernel modules: r8169

05:04.0 Multimedia controller: Philips Semiconductors SAA7130 Video Broadcast Decoder (rev 01)
	Subsystem: Philips Semiconductors Device 0000
	Flags: bus master, medium devsel, latency 32, IRQ 18
	Memory at b0000000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: saa7134
	Kernel modules: saa7134

hari@Indira:~$ 

```

---

### Post by Jose Catre-Vandis on 2010-01-15
As you can see the nice cheeky comment in dmesg about the lack of an eeprom for your card (if you scroll through you will see all the cards it "could" be)

What is the make, manufacture, model of your TV card (please supply as many details as possible, then we may be able to narrow it down a bit.

Also didn't check with you if this is an analog or dvb card?

However, the process you may want to try is as follows:

Boot up in Ubuntu
Open a terminal
Type the following one after another, replacing card and tuner numbers where I put XXs
```
sudo rmmod saa7134-dvb (for dvb)
sudo rmmod saa7134-alsa
sudo rmmod saa7134

then

sudo modprobe saa7134 card=XX tuner=XX
(you should get a short delay before the prompt returns)

sudo modprobe saa7134-dvb (for dvb)
sudo modprobe saa7134
```

If you have the right card and tuner check dmesg again and see if the device is loaded.
Then you have the joys of scanning for channels. Kaffiene proves the most user friendly way.

These settings, once correct can be loaded on boot by adding to a conf file

Having done a quick search your card might be **saa7134 card=98 tuner=69**

---

### Post by hariks0 on 2010-01-15
Thank you very much. Only tell me where can i get the card and tuner numbers from. The info I can gather is as follows:-

PlayTV Pro3 manufactured by Prolink, Taiwan
Card Philips - PV A7130P FRH [FI] - As printed in the box.
The software I used in Wxp is HonestechTVR

Thank you once again.

---

### Post by Jose Catre-Vandis on 2010-01-15
After further searching, try these parameters:

card=42 tuner=38

---

### Post by hariks0 on 2010-01-15
Thank you for the quick reply. I ran the codes and the output is as follows:-

```

hari@Indira:~$ sudo rmmod saa7134-dvb
[sudo] password for hari: 
[COLOR="Red"]ERROR: Module saa7134_dvb does not exist in /proc/modules[/COLOR]
hari@Indira:~$ sudo rmmod saa7134-alsa
hari@Indira:~$ sudo rmmod saa7134
hari@Indira:~$ sudo modprobe saa7134 card=42 tuner=38
hari@Indira:~$ sudo modprobe saa7134-dvb
hari@Indira:~$ sudo modprobe saa7134
hari@Indira:~$

```

Does the error message has anything to do as I am using a cable tv network without a Set Top Box/DVB ?

The output of 'dmesg' is as follows:-

```
hari@Indira:~$ dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.31-17-generic (buildd@palmer) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #54-Ubuntu SMP Thu Dec 10 16:20:31 UTC 2009 (Ubuntu 2.6.31-17.54-generic)
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
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000008f000 (usable)
[    0.000000]  BIOS-e820: 000000000008f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000009e5a9000 (usable)
[    0.000000]  BIOS-e820: 000000009e5a9000 - 000000009e6ad000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000009e6ad000 - 000000009f594000 (usable)
[    0.000000]  BIOS-e820: 000000009f594000 - 000000009f59c000 (reserved)
[    0.000000]  BIOS-e820: 000000009f59c000 - 000000009f62a000 (usable)
[    0.000000]  BIOS-e820: 000000009f62a000 - 000000009f62e000 (reserved)
[    0.000000]  BIOS-e820: 000000009f62e000 - 000000009f6a9000 (usable)
[    0.000000]  BIOS-e820: 000000009f6a9000 - 000000009f6e9000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000009f6e9000 - 000000009f6ed000 (usable)
[    0.000000]  BIOS-e820: 000000009f6ed000 - 000000009f6ff000 (ACPI data)
[    0.000000]  BIOS-e820: 000000009f6ff000 - 000000009f700000 (usable)
[    0.000000]  BIOS-e820: 000000009f700000 - 00000000a0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.4 present.
[    0.000000] last_pfn = 0x9f700 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-FFFFF uncachable
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 080000000 mask FE0000000 write-back
[    0.000000]   2 base 09F800000 mask FFF800000 uncachable
[    0.000000]   3 base 09F700000 mask FFFF00000 uncachable
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 0000000000002000 - 0000000000006000 (usable) ==> (reserved)
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 000000000008f000 (usable)
[    0.000000]  modified: 000000000008f000 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000009e5a9000 (usable)
[    0.000000]  modified: 000000009e5a9000 - 000000009e6ad000 (ACPI NVS)
[    0.000000]  modified: 000000009e6ad000 - 000000009f594000 (usable)
[    0.000000]  modified: 000000009f594000 - 000000009f59c000 (reserved)
[    0.000000]  modified: 000000009f59c000 - 000000009f62a000 (usable)
[    0.000000]  modified: 000000009f62a000 - 000000009f62e000 (reserved)
[    0.000000]  modified: 000000009f62e000 - 000000009f6a9000 (usable)
[    0.000000]  modified: 000000009f6a9000 - 000000009f6e9000 (ACPI NVS)
[    0.000000]  modified: 000000009f6e9000 - 000000009f6ed000 (usable)
[    0.000000]  modified: 000000009f6ed000 - 000000009f6ff000 (ACPI data)
[    0.000000]  modified: 000000009f6ff000 - 000000009f700000 (usable)
[    0.000000]  modified: 000000009f700000 - 00000000a0000000 (reserved)
[    0.000000]  modified: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 7000-c000
[    0.000000] RAMDISK: 375f4000 - 37fefcad
[    0.000000] Allocated new RAMDISK: 008ad000 - 012a8cad
[    0.000000] Move RAMDISK from 00000000375f4000 - 0000000037fefcac to 008ad000 - 012a8cac
[    0.000000] ACPI: RSDP 000fe020 00014 (v00 INTEL )
[    0.000000] ACPI: RSDT 9f6fd038 00050 (v01 INTEL  D945GCR  0000000A      01000013)
[    0.000000] ACPI: FACP 9f6fc000 00074 (v01 INTEL  D945GCR  0000000A MSFT 01000013)
[    0.000000] ACPI: DSDT 9f6f7000 04C39 (v01 INTEL  D945GCR  0000000A MSFT 01000013)
[    0.000000] ACPI: FACS 9f6a9000 00040
[    0.000000] ACPI: APIC 9f6f6000 00078 (v01 INTEL  D945GCR  0000000A MSFT 01000013)
[    0.000000] ACPI: WDDT 9f6f5000 00040 (v01 INTEL  D945GCR  0000000A MSFT 01000013)
[    0.000000] ACPI: MCFG 9f6f4000 0003C (v01 INTEL  D945GCR  0000000A MSFT 01000013)
[    0.000000] ACPI: ASF! 9f6f3000 000A6 (v32 INTEL  D945GCR  0000000A MSFT 01000013)
[    0.000000] ACPI: HPET 9f6f2000 00038 (v01 INTEL  D945GCR  0000000A MSFT 01000013)
[    0.000000] ACPI: SSDT 9f6f1000 001BC (v01 INTEL     CpuPm 0000000A MSFT 01000013)
[    0.000000] ACPI: SSDT 9f6f0000 00175 (v01 INTEL   Cpu0Ist 0000000A MSFT 01000013)
[    0.000000] ACPI: SSDT 9f6ef000 00175 (v01 INTEL   Cpu1Ist 0000000A MSFT 01000013)
[    0.000000] ACPI: SSDT 9f6ee000 00175 (v01 INTEL   Cpu2Ist 0000000A MSFT 01000013)
[    0.000000] ACPI: SSDT 9f6ed000 00175 (v01 INTEL   Cpu3Ist 0000000A MSFT 01000013)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 1663MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000]   node 0 low ram: 00000000 - 377fe000
[    0.000000]   node 0 bootmap 00008000 - 0000ef00
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008a80a0]    TEXT DATA BSS ==> [0000100000 - 00008a80a0]
[    0.000000]   #4 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #5 [00008a9000 - 00008ac161]              BRK ==> [00008a9000 - 00008ac161]
[    0.000000]   #6 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
[    0.000000]   #7 [00008ad000 - 00012a8cad]      NEW RAMDISK ==> [00008ad000 - 00012a8cad]
[    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]
[    0.000000] found SMP MP-table at [c00fe200] fe200
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0009f700
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[8] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x0000008f
[    0.000000]     0: 0x00000100 -> 0x0009e5a9
[    0.000000]     0: 0x0009e6ad -> 0x0009f594
[    0.000000]     0: 0x0009f59c -> 0x0009f62a
[    0.000000]     0: 0x0009f62e -> 0x0009f6a9
[    0.000000]     0: 0x0009f6e9 -> 0x0009f6ed
[    0.000000]     0: 0x0009f6ff -> 0x0009f700
[    0.000000] On node 0 totalpages: 652585
[    0.000000] free_area_init_node: node 0, pgdat c0784960, node_mem_map c12a9000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3947 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 3327 pages used for memmap
[    0.000000]   HighMem zone: 422049 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 000000000008f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at a0000000 (gap: a0000000:5ff80000)
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages at c26a3000, static data 35612 bytes
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 647482
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-17-generic root=UUID=70c1fc36-030d-4e26-a9e8-3f3ce5f98a47 ro vga=771 quiet splash
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 13061120 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0009f700)
[    0.000000] Memory: 2557112k/2612224k available (4566k kernel code, 52340k reserved, 2142k data, 540k init, 1701504k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc078e000 - 0xc0815000   ( 540 kB)
[    0.000000]       .data : 0xc0575a64 - 0xc078d408   (2142 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0575a64   (4566 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=128, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] NR_IRQS:2304 nr_irqs:440
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2992.263 MHz processor.
[    0.000027] Console: colour dummy device 80x25
[    0.000032] console [tty0] enabled
[    0.000161] hpet clockevent registered
[    0.000166] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.000172] Calibrating delay loop (skipped), value calculated using timer frequency.. 5984.52 BogoMIPS (lpj=11969052)
[    0.000192] Security Framework initialized
[    0.000213] AppArmor: AppArmor initialized
[    0.000223] Mount-cache hash table entries: 512
[    0.000375] Initializing cgroup subsys ns
[    0.000381] Initializing cgroup subsys cpuacct
[    0.000386] Initializing cgroup subsys memory
[    0.000394] Initializing cgroup subsys freezer
[    0.000397] Initializing cgroup subsys net_cls
[    0.000419] CPU: Trace cache: 12K uops, L1 D cache: 16K
[    0.000423] CPU: L2 cache: 2048K
[    0.000426] CPU: Physical Processor ID: 0
[    0.000428] CPU: Processor Core ID: 0
[    0.000433] mce: CPU supports 4 MCE banks
[    0.000446] CPU0: Thermal monitoring enabled (TM1)
[    0.000451] using mwait in idle threads.
[    0.000459] Performance Counters: no PMU driver, software counters only.
[    0.000466] Checking 'hlt' instruction... OK.
[    0.019540] ACPI: Core revision 20090521
[    0.031252] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.070943] CPU0: Intel(R) Pentium(R) D CPU 3.00GHz stepping 05
[    0.072001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 5984.97 BogoMIPS (lpj=11969947)
[    0.004000] CPU: Trace cache: 12K uops, L1 D cache: 16K
[    0.004000] CPU: L2 cache: 2048K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.004000] mce: CPU supports 4 MCE banks
[    0.004000] CPU1: Thermal monitoring enabled (TM1)
[    0.004000] x86 PAT enabled: cpu 1, old 0x7040600070406, new 0x7010600070106
[    0.157205] CPU1: Intel(R) Pentium(R) D CPU 3.00GHz stepping 05
[    0.157221] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.160019] Brought up 2 CPUs
[    0.160023] Total of 2 processors activated (11969.49 BogoMIPS).
[    0.160078] CPU0 attaching sched-domain:
[    0.160082]  domain 0: span 0-1 level CPU
[    0.160086]   groups: 0 1
[    0.160094] CPU1 attaching sched-domain:
[    0.160097]  domain 0: span 0-1 level CPU
[    0.160100]   groups: 1 0
[    0.160177] Booting paravirtualized kernel on bare hardware
[    0.160330] regulator: core version 0.5
[    0.160330] Time: 17:24:00  Date: 01/15/10
[    0.160330] NET: Registered protocol family 16
[    0.160330] EISA bus registered
[    0.160330] ACPI: bus type pci registered
[    0.160371] PCI: MCFG configuration 0: base f0000000 segment 0 buses 0 - 127
[    0.160375] PCI: Not using MMCONFIG.
[    0.164997] PCI: Using configuration type 1 for base access
[    0.166366] bio: create slab <bio-0> at 0
[    0.166366] ACPI: EC: Look up EC in DSDT
[    0.172084] ACPI: Interpreter enabled
[    0.172092] ACPI: (supports S0 S1 S3 S4 S5)
[    0.172124] ACPI: Using IOAPIC for interrupt routing
[    0.172171] PCI: MCFG configuration 0: base f0000000 segment 0 buses 0 - 127
[    0.175417] PCI: MCFG area at f0000000 reserved in ACPI motherboard resources
[    0.175422] PCI: updated MCFG configuration 0: base f0000000 segment 0 buses 0 - 63
[    0.175425] PCI: Using MMCONFIG for extended config space
[    0.180952] ACPI: No dock devices found.
[    0.182321] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.182436] pci 0000:00:02.0: reg 10 32bit mmio: [0xb0200000-0xb027ffff]
[    0.182443] pci 0000:00:02.0: reg 14 io port: [0x20e0-0x20e7]
[    0.182450] pci 0000:00:02.0: reg 18 32bit mmio: [0xa0000000-0xafffffff]
[    0.182456] pci 0000:00:02.0: reg 1c 32bit mmio: [0xb0280000-0xb02bffff]
[    0.182557] pci 0000:00:1b.0: reg 10 64bit mmio: [0xb02c0000-0xb02c3fff]
[    0.182609] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.182615] pci 0000:00:1b.0: PME# disabled
[    0.182688] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.182694] pci 0000:00:1c.0: PME# disabled
[    0.182769] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.182774] pci 0000:00:1c.1: PME# disabled
[    0.182849] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.182854] pci 0000:00:1c.2: PME# disabled
[    0.182932] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.182937] pci 0000:00:1c.3: PME# disabled
[    0.182996] pci 0000:00:1d.0: reg 20 io port: [0x2080-0x209f]
[    0.183055] pci 0000:00:1d.1: reg 20 io port: [0x2060-0x207f]
[    0.183115] pci 0000:00:1d.2: reg 20 io port: [0x2040-0x205f]
[    0.183174] pci 0000:00:1d.3: reg 20 io port: [0x2020-0x203f]
[    0.183239] pci 0000:00:1d.7: reg 10 32bit mmio: [0xb02c4000-0xb02c43ff]
[    0.183299] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.183305] pci 0000:00:1d.7: PME# disabled
[    0.183449] pci 0000:00:1f.0: quirk: region 0400-047f claimed by ICH6 ACPI/GPIO/TCO
[    0.183454] pci 0000:00:1f.0: quirk: region 0500-053f claimed by ICH6 GPIO
[    0.183459] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0680 (mask 007f)
[    0.183510] pci 0000:00:1f.1: reg 10 io port: [0x00-0x07]
[    0.183519] pci 0000:00:1f.1: reg 14 io port: [0x00-0x03]
[    0.183527] pci 0000:00:1f.1: reg 18 io port: [0x00-0x07]
[    0.183535] pci 0000:00:1f.1: reg 1c io port: [0x00-0x03]
[    0.183543] pci 0000:00:1f.1: reg 20 io port: [0x20b0-0x20bf]
[    0.183594] pci 0000:00:1f.2: reg 10 io port: [0x20c8-0x20cf]
[    0.183602] pci 0000:00:1f.2: reg 14 io port: [0x20ec-0x20ef]
[    0.183609] pci 0000:00:1f.2: reg 18 io port: [0x20c0-0x20c7]
[    0.183617] pci 0000:00:1f.2: reg 1c io port: [0x20e8-0x20eb]
[    0.183624] pci 0000:00:1f.2: reg 20 io port: [0x20a0-0x20af]
[    0.183654] pci 0000:00:1f.2: PME# supported from D3hot
[    0.183659] pci 0000:00:1f.2: PME# disabled
[    0.183713] pci 0000:00:1f.3: reg 20 io port: [0x2000-0x201f]
[    0.183865] pci 0000:02:00.0: reg 10 io port: [0x1000-0x10ff]
[    0.183892] pci 0000:02:00.0: reg 18 64bit mmio: [0xb0100000-0xb0100fff]
[    0.183918] pci 0000:02:00.0: reg 30 32bit mmio: [0xfffe0000-0xffffffff]
[    0.183973] pci 0000:02:00.0: supports D1 D2
[    0.183976] pci 0000:02:00.0: PME# supported from D1 D2 D3hot D3cold
[    0.183982] pci 0000:02:00.0: PME# disabled
[    0.184055] pci 0000:00:1c.1: bridge io port: [0x1000-0x1fff]
[    0.184061] pci 0000:00:1c.1: bridge 32bit mmio: [0xb0100000-0xb01fffff]
[    0.184221] pci 0000:05:04.0: reg 10 32bit mmio: [0xb0000000-0xb00003ff]
[    0.184278] pci 0000:05:04.0: supports D1 D2
[    0.184326] pci 0000:00:1e.0: transparent bridge
[    0.184334] pci 0000:00:1e.0: bridge 32bit mmio: [0xb0000000-0xb00fffff]
[    0.184366] pci_bus 0000:00: on NUMA node 0
[    0.184372] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.184620] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P32_._PRT]
[    0.184761] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
[    0.184851] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX1._PRT]
[    0.184940] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX2._PRT]
[    0.185029] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX3._PRT]
[    0.190418] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 10 *11 12)
[    0.190567] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 9 *10 11 12)
[    0.190711] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 *10 11 12)
[    0.190859] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 *9 10 11 12)
[    0.191002] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
[    0.191147] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
[    0.191292] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 *9 10 11 12)
[    0.191435] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 9 10 *11 12)
[    0.191677] SCSI subsystem initialized
[    0.191706] libata version 3.00 loaded.
[    0.191706] usbcore: registered new interface driver usbfs
[    0.191706] usbcore: registered new interface driver hub
[    0.191706] usbcore: registered new device driver usb
[    0.192077] ACPI: WMI: Mapper loaded
[    0.192081] PCI: Using ACPI for IRQ routing
[    0.204013] Bluetooth: Core ver 2.15
[    0.204038] NET: Registered protocol family 31
[    0.204038] Bluetooth: HCI device and connection manager initialized
[    0.204038] Bluetooth: HCI socket layer initialized
[    0.204038] NetLabel: Initializing
[    0.204038] NetLabel:  domain hash size = 128
[    0.204040] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.204058] NetLabel:  unlabeled traffic allowed by default
[    0.204097] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.204105] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.220014] pnp: PnP ACPI init
[    0.220029] ACPI: bus type pnp registered
[    0.223606] pnp: PnP ACPI: found 13 devices
[    0.223610] ACPI: ACPI bus type pnp unregistered
[    0.223614] PnPBIOS: Disabled by ACPI PNP
[    0.223628] system 00:01: iomem range 0xf0000000-0xf3ffffff has been reserved
[    0.223632] system 00:01: iomem range 0xfed13000-0xfed13fff has been reserved
[    0.223636] system 00:01: iomem range 0xfed14000-0xfed17fff has been reserved
[    0.223640] system 00:01: iomem range 0xfed18000-0xfed18fff has been reserved
[    0.223643] system 00:01: iomem range 0xfed19000-0xfed19fff has been reserved
[    0.223647] system 00:01: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    0.223651] system 00:01: iomem range 0xfed20000-0xfed3ffff has been reserved
[    0.223655] system 00:01: iomem range 0xfed45000-0xfed99fff has been reserved
[    0.223659] system 00:01: iomem range 0xc0000-0xdffff could not be reserved
[    0.223663] system 00:01: iomem range 0xe0000-0xfffff could not be reserved
[    0.223673] system 00:06: ioport range 0x500-0x53f has been reserved
[    0.223677] system 00:06: ioport range 0x400-0x47f has been reserved
[    0.223680] system 00:06: ioport range 0x680-0x6ff has been reserved
[    0.223684] system 00:06: ioport range 0x770-0x77f has been reserved
[    0.258392] AppArmor: AppArmor Filesystem Enabled
[    0.258415] pci 0000:02:00.0: BAR 6: no parent found for of device [0xfffe0000-0xffffffff]
[    0.258465] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:01
[    0.258468] pci 0000:00:1c.0:   IO window: disabled
[    0.258474] pci 0000:00:1c.0:   MEM window: disabled
[    0.258479] pci 0000:00:1c.0:   PREFETCH window: disabled
[    0.258485] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:02
[    0.258490] pci 0000:00:1c.1:   IO window: 0x1000-0x1fff
[    0.258496] pci 0000:00:1c.1:   MEM window: 0xb0100000-0xb01fffff
[    0.258501] pci 0000:00:1c.1:   PREFETCH window: 0xb0300000-0xb03fffff
[    0.258507] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:03
[    0.258509] pci 0000:00:1c.2:   IO window: disabled
[    0.258515] pci 0000:00:1c.2:   MEM window: disabled
[    0.258519] pci 0000:00:1c.2:   PREFETCH window: disabled
[    0.258524] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:04
[    0.258527] pci 0000:00:1c.3:   IO window: disabled
[    0.258532] pci 0000:00:1c.3:   MEM window: disabled
[    0.258537] pci 0000:00:1c.3:   PREFETCH window: disabled
[    0.258542] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:05
[    0.258544] pci 0000:00:1e.0:   IO window: disabled
[    0.258550] pci 0000:00:1e.0:   MEM window: 0xb0000000-0xb00fffff
[    0.258555] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.258569]   alloc irq_desc for 17 on node -1
[    0.258573]   alloc kstat_irqs on node -1
[    0.258580] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.258587] pci 0000:00:1c.0: setting latency timer to 64
[    0.258598]   alloc irq_desc for 16 on node -1
[    0.258601]   alloc kstat_irqs on node -1
[    0.258607] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.258613] pci 0000:00:1c.1: setting latency timer to 64
[    0.258623]   alloc irq_desc for 18 on node -1
[    0.258626]   alloc kstat_irqs on node -1
[    0.258631] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.258637] pci 0000:00:1c.2: setting latency timer to 64
[    0.258645]   alloc irq_desc for 19 on node -1
[    0.258647]   alloc kstat_irqs on node -1
[    0.258652] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.258657] pci 0000:00:1c.3: setting latency timer to 64
[    0.258665] pci 0000:00:1e.0: setting latency timer to 64
[    0.258671] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.258674] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.258678] pci_bus 0000:02: resource 0 io:  [0x1000-0x1fff]
[    0.258681] pci_bus 0000:02: resource 1 mem: [0xb0100000-0xb01fffff]
[    0.258684] pci_bus 0000:02: resource 2 pref mem [0xb0300000-0xb03fffff]
[    0.258688] pci_bus 0000:05: resource 1 mem: [0xb0000000-0xb00fffff]
[    0.258691] pci_bus 0000:05: resource 3 io:  [0x00-0xffff]
[    0.258694] pci_bus 0000:05: resource 4 mem: [0x000000-0xffffffff]
[    0.258740] NET: Registered protocol family 2
[    0.258868] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.259311] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.259890] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.260191] TCP: Hash tables configured (established 131072 bind 65536)
[    0.260194] TCP reno registered
[    0.260293] NET: Registered protocol family 1
[    0.260376] Trying to unpack rootfs image as initramfs...
[    0.501159] Switched to high resolution mode on CPU 1
[    0.504031] Switched to high resolution mode on CPU 0
[    0.589363] Freeing initrd memory: 10223k freed
[    0.595233] cpufreq-nforce2: No nForce2 chipset.
[    0.595271] Scanning for low memory corruption every 60 seconds
[    0.595391] audit: initializing netlink socket (disabled)
[    0.595407] type=2000 audit(1263576239.592:1): initialized
[    0.604526] highmem bounce pool size: 64 pages
[    0.604538] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.606398] VFS: Disk quotas dquot_6.5.2
[    0.606478] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.607236] fuse init (API version 7.12)
[    0.607349] msgmni has been set to 1692
[    0.607682] alg: No test for stdrng (krng)
[    0.607712] io scheduler noop registered
[    0.607715] io scheduler anticipatory registered
[    0.607718] io scheduler deadline registered
[    0.607779] io scheduler cfq registered (default)
[    0.607794] pci 0000:00:02.0: Boot video device
[    0.608147]   alloc irq_desc for 24 on node -1
[    0.608151]   alloc kstat_irqs on node -1
[    0.608164] pcieport-driver 0000:00:1c.0: irq 24 for MSI/MSI-X
[    0.608175] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    0.608337]   alloc irq_desc for 25 on node -1
[    0.608340]   alloc kstat_irqs on node -1
[    0.608349] pcieport-driver 0000:00:1c.1: irq 25 for MSI/MSI-X
[    0.608359] pcieport-driver 0000:00:1c.1: setting latency timer to 64
[    0.608504]   alloc irq_desc for 26 on node -1
[    0.608507]   alloc kstat_irqs on node -1
[    0.608517] pcieport-driver 0000:00:1c.2: irq 26 for MSI/MSI-X
[    0.608526] pcieport-driver 0000:00:1c.2: setting latency timer to 64
[    0.608672]   alloc irq_desc for 27 on node -1
[    0.608675]   alloc kstat_irqs on node -1
[    0.608684] pcieport-driver 0000:00:1c.3: irq 27 for MSI/MSI-X
[    0.608694] pcieport-driver 0000:00:1c.3: setting latency timer to 64
[    0.608809] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.608951] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.609108] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    0.609113] ACPI: Power Button [PWRF]
[    0.609179] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1
[    0.609187] ACPI: Sleep Button [SLPB]
[    0.609569] processor LNXCPU:00: registered as cooling_device0
[    0.609692] processor LNXCPU:01: registered as cooling_device1
[    0.611363] isapnp: Scanning for PnP cards...
[    0.964633] isapnp: No Plug & Play device found
[    0.966090] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.966203] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.966666] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.967973] brd: module loaded
[    0.968573] loop: module loaded
[    0.968662] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    0.968803] ata_piix 0000:00:1f.1: version 2.13
[    0.968818] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.968861] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.968947] scsi0 : ata_piix
[    0.969059] scsi1 : ata_piix
[    0.969487] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x20b0 irq 14
[    0.969491] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x20b8 irq 15
[    0.969521] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.969528] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    0.969579] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.969645] scsi2 : ata_piix
[    0.969719] ata2: port disabled. ignoring.
[    0.969766] scsi3 : ata_piix
[    0.970554] ata3: SATA max UDMA/133 cmd 0x20c8 ctl 0x20ec bmdma 0x20a0 irq 19
[    0.970558] ata4: SATA max UDMA/133 cmd 0x20c0 ctl 0x20e8 bmdma 0x20a8 irq 19
[    0.971746] Fixed MDIO Bus: probed
[    0.971793] PPP generic driver version 2.4.2
[    0.971912] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.971935]   alloc irq_desc for 23 on node -1
[    0.971938]   alloc kstat_irqs on node -1
[    0.971946] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.971959] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.971964] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.972039] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.975951] ehci_hcd 0000:00:1d.7: debug port 1
[    0.975959] ehci_hcd 0000:00:1d.7: cache line size of 128 is not supported
[    0.975974] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xb02c4000
[    0.988013] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.988131] usb usb1: configuration #1 chosen from 1 choice
[    0.988172] hub 1-0:1.0: USB hub found
[    0.988182] hub 1-0:1.0: 8 ports detected
[    0.988266] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.988290] uhci_hcd: USB Universal Host Controller Interface driver
[    0.988320] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.988327] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.988332] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.988372] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.988399] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00002080
[    0.988496] usb usb2: configuration #1 chosen from 1 choice
[    0.988533] hub 2-0:1.0: USB hub found
[    0.988542] hub 2-0:1.0: 2 ports detected
[    0.988603] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.988611] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.988616] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.988655] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.988680] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00002060
[    0.988784] usb usb3: configuration #1 chosen from 1 choice
[    0.988820] hub 3-0:1.0: USB hub found
[    0.988829] hub 3-0:1.0: 2 ports detected
[    0.988891] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.988898] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.988902] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.988941] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.988974] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00002040
[    0.989067] usb usb4: configuration #1 chosen from 1 choice
[    0.989103] hub 4-0:1.0: USB hub found
[    0.989112] hub 4-0:1.0: 2 ports detected
[    0.989168] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    0.989175] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    0.989179] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    0.989222] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    0.989256] uhci_hcd 0000:00:1d.3: irq 16, io base 0x00002020
[    0.989350] usb usb5: configuration #1 chosen from 1 choice
[    0.989386] hub 5-0:1.0: USB hub found
[    0.989395] hub 5-0:1.0: 2 ports detected
[    0.989518] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    0.992140] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.992149] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.992245] mice: PS/2 mouse device common for all mice
[    0.992371] rtc_cmos 00:03: RTC can wake from S4
[    0.992411] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    0.992439] rtc0: alarms up to one month, 114 bytes nvram, hpet irqs
[    0.992580] device-mapper: uevent: version 1.0.3
[    0.992702] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.992835] device-mapper: multipath: version 1.1.0 loaded
[    0.992840] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.993010] EISA: Probing bus 0 at eisa.0
[    0.993017] Cannot allocate resource for EISA slot 1
[    0.993020] Cannot allocate resource for EISA slot 2
[    0.993041] EISA: Detected 0 cards.
[    0.993217] cpuidle: using governor ladder
[    0.993220] cpuidle: using governor menu
[    0.993908] TCP cubic registered
[    0.994083] NET: Registered protocol family 10
[    0.994725] lo: Disabled Privacy Extensions
[    0.995221] NET: Registered protocol family 17
[    0.995245] Bluetooth: L2CAP ver 2.13
[    0.995247] Bluetooth: L2CAP socket layer initialized
[    0.995251] Bluetooth: SCO (Voice Link) ver 0.6
[    0.995253] Bluetooth: SCO socket layer initialized
[    0.995300] Bluetooth: RFCOMM TTY layer initialized
[    0.995304] Bluetooth: RFCOMM socket layer initialized
[    0.995307] Bluetooth: RFCOMM ver 1.11
[    0.995712] Using IPI No-Shortcut mode
[    0.995791] PM: Resume from disk failed.
[    0.995807] registered taskstats version 1
[    0.995937]   Magic number: 10:273:441
[    0.995961] pcieport-driver 0000:00:1c.2: hash matches
[    0.996005] rtc_cmos 00:03: setting system clock to 2010-01-15 17:24:00 UTC (1263576240)
[    0.996026] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.996029] EDD information not available.
[    1.011273] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    1.132181] ata3.01: NODEV after polling detection
[    1.140223] ata3.00: ATAPI: TSSTcorp CDDVDW SH-S203B, SB00, max UDMA/100
[    1.156256] ata3.00: configured for UDMA/100
[    1.157563] scsi 2:0:0:0: CD-ROM            TSSTcorp CDDVDW SH-S203B  SB00 PQ: 0 ANSI: 5
[    1.161644] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.161650] Uniform CD-ROM driver Revision: 3.20
[    1.161777] sr 2:0:0:0: Attached scsi CD-ROM sr0
[    1.161832] sr 2:0:0:0: Attached scsi generic sg0 type 5
[    1.168049] ata4.00: ATA-7: ST3250820SV, 3.ACH, max UDMA/133
[    1.168054] ata4.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.243050] ata4.00: configured for UDMA/133
[    1.243196] scsi 3:0:0:0: Direct-Access     ATA      ST3250820SV      3.AC PQ: 0 ANSI: 5
[    1.243357] sd 3:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    1.243378] sd 3:0:0:0: Attached scsi generic sg1 type 0
[    1.243434] sd 3:0:0:0: [sda] Write Protect is off
[    1.243438] sd 3:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.243473] sd 3:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.243641]  sda: sda1 sda2 < sda5 sda6 sda7 sda8 sda9 >
[    1.360541] sd 3:0:0:0: [sda] Attached SCSI disk
[    1.360564] Freeing unused kernel memory: 540k freed
[    1.360988] Write protecting the kernel text: 4568k
[    1.361047] Write protecting the kernel read-only data: 1836k
[    1.511575] ramzswap: disk size set to 642188 kB
[    1.544834] Linux agpgart interface v0.103
[    1.548225] agpgart-intel 0000:00:00.0: Intel 945G Chipset
[    1.549081] agpgart-intel 0000:00:00.0: detected 7932K stolen memory
[    1.552387] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xa0000000
[    1.588607] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.588631] r8169 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.588684] r8169 0000:02:00.0: setting latency timer to 64
[    1.588751]   alloc irq_desc for 28 on node -1
[    1.588754]   alloc kstat_irqs on node -1
[    1.588773] r8169 0000:02:00.0: irq 28 for MSI/MSI-X
[    1.589712] eth0: RTL8168b/8111b at 0xf80a4000, 00:19:d1:a7:15:66, XID 38500000 IRQ 28
[    1.657614] usb 2-2: new full speed USB device using uhci_hcd and address 2
[    1.670041] Adding 642184k swap on /dev/ramzswap0.  Priority:100 extents:1 across:642184k SSD
[    1.673932] [drm] Initialized drm 1.1.0 20060810
[    1.688410] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.688417] i915 0000:00:02.0: setting latency timer to 64
[    1.817922] [drm] fb0: inteldrmfb frame buffer device
[    1.817934] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    1.824413] Console: switching to colour frame buffer device 128x48
[    1.863624] usb 2-2: configuration #1 chosen from 1 choice
[    1.890082] [drm] DAC-6: set mode 1024x768 17
[    2.104023] usb 3-2: new full speed USB device using uhci_hcd and address 2
[    2.265488] vesafb: framebuffer at 0xa0000000, mapped to 0xf8b00000, using 512k, total 512k
[    2.265493] vesafb: mode is 800x600x8, linelength=832, pages=0
[    2.265496] vesafb: scrolling: redraw
[    2.265503] vesafb: Pseudocolor: size=0:8:8:8, shift=0:0:0:0
[    2.265572] fb1: VESA VGA frame buffer device
[    2.439068] xor: automatically using best checksumming function: pIII_sse
[    2.456011]    pIII_sse  :  4528.000 MB/sec
[    2.456017] xor: using function: pIII_sse (4528.000 MB/sec)
[    2.459036] device-mapper: dm-raid45: initialized v0.2594b
[    2.980056] PM: Starting manual resume from disk
[    2.980061] PM: Resume from partition 8:7
[    2.980063] PM: Checking hibernation image.
[    2.980226] PM: Resume from disk failed.
[    2.999835] EXT4-fs (sda8): INFO: recovery required on readonly filesystem
[    2.999841] EXT4-fs (sda8): write access will be enabled during recovery
[    3.003290] EXT4-fs (sda8): barriers enabled
[    3.228084] kjournald2 starting: pid 420, dev sda8:8, commit interval 5 seconds
[    3.228105] EXT4-fs (sda8): delayed allocation enabled
[    3.228111] EXT4-fs: file extents enabled
[    3.229573] EXT4-fs: mballoc enabled
[    3.229593] EXT4-fs (sda8): recovery complete
[    3.229910] EXT4-fs (sda8): mounted filesystem with ordered data mode
[   12.270109] usb 3-2: configuration #1 chosen from 1 choice
[   21.857263] udev: starting version 147
[   21.877316] Adding 4883720k swap on /dev/sda7.  Priority:-1 extents:1 across:4883720k 
[   22.217404] Linux video capture interface: v2.00
[   22.339468] parport_pc 00:07: reported by Plug and Play ACPI
[   22.339497] parport0: PC-style at 0x378, irq 7 [PCSPP,EPP]
[   22.398023] Bluetooth: Generic Bluetooth USB driver ver 0.5
[   22.398168] usbcore: registered new interface driver btusb
[   22.401980] ppdev: user-space parallel port driver
[   22.430017] intel_rng: FWH not detected
[   22.437951] gspca: main v2.6.0 registered
[   22.445514] gspca: probing 04fc:0561
[   22.485031] lp0: using parport0 (interrupt-driven).
[   22.576468] psmouse serio1: ID: 10 00 64
[   22.702087] saa7130/34: v4l2 driver version 0.2.15 loaded
[   22.702149] saa7134 0000:05:04.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   22.702158] saa7130[0]: found at 0000:05:04.0, rev: 1, irq: 18, latency: 32, mmio: 0xb0000000
[   22.702166] saa7134: <rant>
[   22.702167] saa7134:  Congratulations!  Your TV card vendor saved a few
[   22.702169] saa7134:  cents for a eeprom, thus your pci board has no
[   22.702170] saa7134:  subsystem ID and I can't identify it automatically
[   22.702172] saa7134: </rant>
[   22.702173] saa7134: I feel better now.  Ok, here are the good news:
[   22.702174] saa7134: You can use the card=<nr> insmod option to specify
[   22.702175] saa7134: which board do you have.  The list:
[   22.702179] saa7134:   card=0 -> UNKNOWN/GENERIC                         
[   22.702183] saa7134:   card=1 -> Proteus Pro [philips reference design]   1131:2001 1131:2001
[   22.702190] saa7134:   card=2 -> LifeView FlyVIDEO3000                    5168:0138 4e42:0138
[   22.702196] saa7134:   card=3 -> LifeView/Typhoon FlyVIDEO2000            5168:0138 4e42:0138
[   22.702202] saa7134:   card=4 -> EMPRESS                                  1131:6752
[   22.702207] saa7134:   card=5 -> SKNet Monster TV                         1131:4e85
[   22.702211] saa7134:   card=6 -> Tevion MD 9717                          
[   22.702215] saa7134:   card=7 -> KNC One TV-Station RDS / Typhoon TV Tune 1131:fe01 1894:fe01
[   22.702221] saa7134:   card=8 -> Terratec Cinergy 400 TV                  153b:1142
[   22.702225] saa7134:   card=9 -> Medion 5044                             
[   22.702229] saa7134:   card=10 -> Kworld/KuroutoShikou SAA7130-TVPCI      
[   22.702233] saa7134:   card=11 -> Terratec Cinergy 600 TV                  153b:1143
[   22.702237] saa7134:   card=12 -> Medion 7134                              16be:0003 16be:5000
[   22.702243] saa7134:   card=13 -> Typhoon TV+Radio 90031                  
[   22.702247] saa7134:   card=14 -> ELSA EX-VISION 300TV                     1048:226b
[   22.702252] saa7134:   card=15 -> ELSA EX-VISION 500TV                     1048:226a
[   22.702256] saa7134:   card=16 -> ASUS TV-FM 7134                          1043:4842 1043:4830 1043:4840
[   22.702263] saa7134:   card=17 -> AOPEN VA1000 POWER                       1131:7133
[   22.702268] saa7134:   card=18 -> BMK MPEX No Tuner                       
[   22.702272] saa7134:   card=19 -> Compro VideoMate TV                      185b:c100
[   22.702276] saa7134:   card=20 -> Matrox CronosPlus                        102b:48d0
[   22.702281] saa7134:   card=21 -> 10MOONS PCI TV CAPTURE CARD              1131:2001
[   22.702286] saa7134:   card=22 -> AverMedia M156 / Medion 2819             1461:a70b
[   22.702291] saa7134:   card=23 -> BMK MPEX Tuner                          
[   22.702294] saa7134:   card=24 -> KNC One TV-Station DVR                   1894:a006
[   22.702299] saa7134:   card=25 -> ASUS TV-FM 7133                          1043:4843
[   22.702304] saa7134:   card=26 -> Pinnacle PCTV Stereo (saa7134)           11bd:002b
[   22.702309] saa7134:   card=27 -> Manli MuchTV M-TV002                    
[   22.702312] saa7134:   card=28 -> Manli MuchTV M-TV001                    
[   22.702316] saa7134:   card=29 -> Nagase Sangyo TransGear 3000TV           1461:050c
[   22.702321] saa7134:   card=30 -> Elitegroup ECS TVP3XP FM1216 Tuner Card( 1019:4cb4
[   22.702325] saa7134:   card=31 -> Elitegroup ECS TVP3XP FM1236 Tuner Card  1019:4cb5
[   22.702330] saa7134:   card=32 -> AVACS SmartTV                           
[   22.702334] saa7134:   card=33 -> AVerMedia DVD EZMaker                    1461:10ff
[   22.702339] saa7134:   card=34 -> Noval Prime TV 7133                     
[   22.702342] saa7134:   card=35 -> AverMedia AverTV Studio 305              1461:2115
[   22.702347] saa7134:   card=36 -> UPMOST PURPLE TV                         12ab:0800
[   22.702352] saa7134:   card=37 -> Items MuchTV Plus / IT-005              
[   22.702355] saa7134:   card=38 -> Terratec Cinergy 200 TV                  153b:1152
[   22.702360] saa7134:   card=39 -> LifeView FlyTV Platinum Mini             5168:0212 4e42:0212 5169:1502
[   22.702367] saa7134:   card=40 -> Compro VideoMate TV PVR/FM               185b:c100
[   22.702372] saa7134:   card=41 -> Compro VideoMate TV Gold+                185b:c100
[   22.702376] saa7134:   card=42 -> Sabrent SBT-TVFM (saa7130)              
[   22.702380] saa7134:   card=43 -> :Zolid Xpert TV7134                     
[   22.702383] saa7134:   card=44 -> Empire PCI TV-Radio LE                  
[   22.702387] saa7134:   card=45 -> Avermedia AVerTV Studio 307              1461:9715
[   22.702392] saa7134:   card=46 -> AVerMedia Cardbus TV/Radio (E500)        1461:d6ee
[   22.702397] saa7134:   card=47 -> Terratec Cinergy 400 mobile              153b:1162
[   22.702401] saa7134:   card=48 -> Terratec Cinergy 600 TV MK3              153b:1158
[   22.702406] saa7134:   card=49 -> Compro VideoMate Gold+ Pal               185b:c200
[   22.702411] saa7134:   card=50 -> Pinnacle PCTV 300i DVB-T + PAL           11bd:002d
[   22.702415] saa7134:   card=51 -> ProVideo PV952                           1540:9524
[   22.702420] saa7134:   card=52 -> AverMedia AverTV/305                     1461:2108
[   22.702425] saa7134:   card=53 -> ASUS TV-FM 7135                          1043:4845
[   22.702430] saa7134:   card=54 -> LifeView FlyTV Platinum FM / Gold        5168:0214 5168:5214 1489:0214 5168:0304
[   22.702437] saa7134:   card=55 -> LifeView FlyDVB-T DUO / MSI TV@nywhere D 5168:0306 4e42:0306
[   22.702443] saa7134:   card=56 -> Avermedia AVerTV 307                     1461:a70a
[   22.702448] saa7134:   card=57 -> Avermedia AVerTV GO 007 FM               1461:f31f
[   22.702453] saa7134:   card=58 -> ADS Tech Instant TV (saa7135)            1421:0350 1421:0351 1421:0370 1421:1370
[   22.702461] saa7134:   card=59 -> Kworld/Tevion V-Stream Xpert TV PVR7134 
[   22.702464] saa7134:   card=60 -> LifeView/Typhoon/Genius FlyDVB-T Duo Car 5168:0502 4e42:0502 1489:0502
[   22.702471] saa7134:   card=61 -> Philips TOUGH DVB-T reference design     1131:2004
[   22.702476] saa7134:   card=62 -> Compro VideoMate TV Gold+II             
[   22.702480] saa7134:   card=63 -> Kworld Xpert TV PVR7134                 
[   22.702483] saa7134:   card=64 -> FlyTV mini Asus Digimatrix               1043:0210
[   22.702488] saa7134:   card=65 -> V-Stream Studio TV Terminator           
[   22.702492] saa7134:   card=66 -> Yuan TUN-900 (saa7135)                  
[   22.702495] saa7134:   card=67 -> Beholder BeholdTV 409 FM                 0000:4091
[   22.702500] saa7134:   card=68 -> GoTView 7135 PCI                         5456:7135
[   22.702505] saa7134:   card=69 -> Philips EUROPA V3 reference design       1131:2004
[   22.702510] saa7134:   card=70 -> Compro Videomate DVB-T300                185b:c900
[   22.702514] saa7134:   card=71 -> Compro Videomate DVB-T200                185b:c901
[   22.702519] saa7134:   card=72 -> RTD Embedded Technologies VFG7350        1435:7350
[   22.702524] saa7134:   card=73 -> RTD Embedded Technologies VFG7330        1435:7330
[   22.702529] saa7134:   card=74 -> LifeView FlyTV Platinum Mini2            14c0:1212
[   22.702533] saa7134:   card=75 -> AVerMedia AVerTVHD MCE A180              1461:1044
[   22.702538] saa7134:   card=76 -> SKNet MonsterTV Mobile                   1131:4ee9
[   22.702543] saa7134:   card=77 -> Pinnacle PCTV 40i/50i/110i (saa7133)     11bd:002e
[   22.702547] saa7134:   card=78 -> ASUSTeK P7131 Dual                       1043:4862
[   22.702552] saa7134:   card=79 -> Sedna/MuchTV PC TV Cardbus TV/Radio (ITO
[   22.702556] saa7134:   card=80 -> ASUS Digimatrix TV                       1043:0210
[   22.702561] saa7134:   card=81 -> Philips Tiger reference design           1131:2018
[   22.702565] saa7134:   card=82 -> MSI TV@Anywhere plus                     1462:6231 1462:8624
[   22.702571] saa7134:   card=83 -> Terratec Cinergy 250 PCI TV              153b:1160
[   22.702576] saa7134:   card=84 -> LifeView FlyDVB Trio                     5168:0319
[   22.702580] saa7134:   card=85 -> AverTV DVB-T 777                         1461:2c05 1461:2c05
[   22.702586] saa7134:   card=86 -> LifeView FlyDVB-T / Genius VideoWonder D 5168:0301 1489:0301
[   22.702592] saa7134:   card=87 -> ADS Instant TV Duo Cardbus PTV331        0331:1421
[   22.702597] saa7134:   card=88 -> Tevion/KWorld DVB-T 220RF                17de:7201
[   22.702602] saa7134:   card=89 -> ELSA EX-VISION 700TV                     1048:226c
[   22.702606] saa7134:   card=90 -> Kworld ATSC110/115                       17de:7350 17de:7352
[   22.702612] saa7134:   card=91 -> AVerMedia A169 B                         1461:7360
[   22.702617] saa7134:   card=92 -> AVerMedia A169 B1                        1461:6360
[   22.702622] saa7134:   card=93 -> Medion 7134 Bridge #2                    16be:0005
[   22.702626] saa7134:   card=94 -> LifeView FlyDVB-T Hybrid Cardbus/MSI TV  5168:3306 5168:3502 5168:3307 4e42:3502
[   22.702634] saa7134:   card=95 -> LifeView FlyVIDEO3000 (NTSC)             5169:0138
[   22.702639] saa7134:   card=96 -> Medion Md8800 Quadro                     16be:0007 16be:0008 16be:000d
[   22.702646] saa7134:   card=97 -> LifeView FlyDVB-S /Acorp TV134DS         5168:0300 4e42:0300
[   22.702652] saa7134:   card=98 -> Proteus Pro 2309                         0919:2003
[   22.702656] saa7134:   card=99 -> AVerMedia TV Hybrid A16AR                1461:2c00
[   22.702661] saa7134:   card=100 -> Asus Europa2 OEM                         1043:4860
[   22.702666] saa7134:   card=101 -> Pinnacle PCTV 310i                       11bd:002f
[   22.702671] saa7134:   card=102 -> Avermedia AVerTV Studio 507              1461:9715
[   22.702675] saa7134:   card=103 -> Compro Videomate DVB-T200A              
[   22.702679] saa7134:   card=104 -> Hauppauge WinTV-HVR1110 DVB-T/Hybrid     0070:6700 0070:6701 0070:6702 0070:6703 0070:6704 0070:6705
[   22.702689] saa7134:   card=105 -> Terratec Cinergy HT PCMCIA               153b:1172
[   22.702694] saa7134:   card=106 -> Encore ENLTV                             1131:2342 1131:2341 3016:2344
[   22.702701] saa7134:   card=107 -> Encore ENLTV-FM                          1131:230f
[   22.702705] saa7134:   card=108 -> Terratec Cinergy HT PCI                  153b:1175
[   22.702710] saa7134:   card=109 -> Philips Tiger - S Reference design      
[   22.702714] saa7134:   card=110 -> Avermedia M102                           1461:f31e
[   22.702718] saa7134:   card=111 -> ASUS P7131 4871                          1043:4871
[   22.702723] saa7134:   card=112 -> ASUSTeK P7131 Hybrid                     1043:4876
[   22.702728] saa7134:   card=113 -> Elitegroup ECS TVP3XP FM1246 Tuner Card  1019:4cb6
[   22.702733] saa7134:   card=114 -> KWorld DVB-T 210                         17de:7250
[   22.702737] saa7134:   card=115 -> Sabrent PCMCIA TV-PCB05                  0919:2003
[   22.702742] saa7134:   card=116 -> 10MOONS TM300 TV Card                    1131:2304
[   22.702747] saa7134:   card=117 -> Avermedia Super 007                      1461:f01d
[   22.702752] saa7134:   card=118 -> Beholder BeholdTV 401                    0000:4016
[   22.702756] saa7134:   card=119 -> Beholder BeholdTV 403                    0000:4036
[   22.702761] saa7134:   card=120 -> Beholder BeholdTV 403 FM                 0000:4037
[   22.702766] saa7134:   card=121 -> Beholder BeholdTV 405                    0000:4050
[   22.702771] saa7134:   card=122 -> Beholder BeholdTV 405 FM                 0000:4051
[   22.702776] saa7134:   card=123 -> Beholder BeholdTV 407                    0000:4070
[   22.702780] saa7134:   card=124 -> Beholder BeholdTV 407 FM                 0000:4071
[   22.702785] saa7134:   card=125 -> Beholder BeholdTV 409                    0000:4090
[   22.702790] saa7134:   card=126 -> Beholder BeholdTV 505 FM                 5ace:5050
[   22.702795] saa7134:   card=127 -> Beholder BeholdTV 507 FM / BeholdTV 509  5ace:5070 5ace:5090
[   22.702801] saa7134:   card=128 -> Beholder BeholdTV Columbus TVFM          0000:5201
[   22.702805] saa7134:   card=129 -> Beholder BeholdTV 607 FM                 5ace:6070
[   22.702810] saa7134:   card=130 -> Beholder BeholdTV M6                     5ace:6190
[   22.702815] saa7134:   card=131 -> Twinhan Hybrid DTV-DVB 3056 PCI          1822:0022
[   22.702820] saa7134:   card=132 -> Genius TVGO AM11MCE                     
[   22.702823] saa7134:   card=133 -> NXP Snake DVB-S reference design        
[   22.702827] saa7134:   card=134 -> Medion/Creatix CTX953 Hybrid             16be:0010
[   22.702832] saa7134:   card=135 -> MSI TV@nywhere A/D v1.1                  1462:8625
[   22.702836] saa7134:   card=136 -> AVerMedia Cardbus TV/Radio (E506R)       1461:f436
[   22.702841] saa7134:   card=137 -> AVerMedia Hybrid TV/Radio (A16D)         1461:f936
[   22.702846] saa7134:   card=138 -> Avermedia M115                           1461:a836
[   22.702851] saa7134:   card=139 -> Compro VideoMate T750                    185b:c900
[   22.702855] saa7134:   card=140 -> Avermedia DVB-S Pro A700                 1461:a7a1
[   22.702860] saa7134:   card=141 -> Avermedia DVB-S Hybrid+FM A700           1461:a7a2
[   22.702865] saa7134:   card=142 -> Beholder BeholdTV H6                     5ace:6290
[   22.702869] saa7134:   card=143 -> Beholder BeholdTV M63                    5ace:6191
[   22.702874] saa7134:   card=144 -> Beholder BeholdTV M6 Extra               5ace:6193
[   22.702879] saa7134:   card=145 -> AVerMedia MiniPCI DVB-T Hybrid M103      1461:f636 1461:f736
[   22.702884] saa7134:   card=146 -> ASUSTeK P7131 Analog                    
[   22.702888] saa7134:   card=147 -> Asus Tiger 3in1                          1043:4878
[   22.702893] saa7134:   card=148 -> Encore ENLTV-FM v5.3                     1a7f:2008
[   22.702898] saa7134:   card=149 -> Avermedia PCI pure analog (M135A)        1461:f11d
[   22.702902] saa7134:   card=150 -> Zogis Real Angel 220                    
[   22.702906] saa7134:   card=151 -> ADS Tech Instant HDTV                    1421:0380
[   22.702911] saa7134:   card=152 -> Asus Tiger Rev:1.00                      1043:4857
[   22.702915] saa7134:   card=153 -> Kworld Plus TV Analog Lite PCI           17de:7128
[   22.702920] saa7134:   card=154 -> Avermedia AVerTV GO 007 FM Plus          1461:f31d
[   22.702925] saa7134:   card=155 -> Hauppauge WinTV-HVR1150 ATSC/QAM-Hybrid  0070:6706 0070:6708
[   22.702930] saa7134:   card=156 -> Hauppauge WinTV-HVR1120 DVB-T/Hybrid     0070:6707 0070:6709 0070:670a
[   22.702937] saa7134:   card=157 -> Avermedia AVerTV Studio 507UA            1461:a11b
[   22.702942] saa7134:   card=158 -> AVerMedia Cardbus TV/Radio (E501R)       1461:b7e9
[   22.702947] saa7134:   card=159 -> Beholder BeholdTV 505 RDS                0000:505b
[   22.702951] saa7134:   card=160 -> Beholder BeholdTV 507 RDS                0000:5071
[   22.702956] saa7134:   card=161 -> Beholder BeholdTV 507 RDS                0000:507b
[   22.702961] saa7134:   card=162 -> Beholder BeholdTV 607 FM                 5ace:6071
[   22.702966] saa7134:   card=163 -> Beholder BeholdTV 609 FM                 5ace:6090
[   22.702970] saa7134:   card=164 -> Beholder BeholdTV 609 FM                 5ace:6091
[   22.702975] saa7134:   card=165 -> Beholder BeholdTV 607 RDS                5ace:6072
[   22.702980] saa7134:   card=166 -> Beholder BeholdTV 607 RDS                5ace:6073
[   22.702984] saa7134:   card=167 -> Beholder BeholdTV 609 RDS                5ace:6092
[   22.702989] saa7134:   card=168 -> Beholder BeholdTV 609 RDS                5ace:6093
[   22.702995] saa7130[0]: subsystem: 1131:0000, board: UNKNOWN/GENERIC [card=0,autodetected]
[   22.703010] saa7130[0]: board init: gpio is 60c000
[   22.703015] IRQ 18/saa7130[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[   22.792117] gspca: probe ok
[   22.792149] usbcore: registered new interface driver spca561
[   22.792154] spca561: registered
[   22.810777] saa7130[0]: Huh, no eeprom present (err=-5)?
[   22.810784] i2c-adapter i2c-1: Invalid 7-bit address 0x7a
[   22.811387] saa7130[0]: registered device video1 [v4l2]
[   22.811419] saa7130[0]: registered device vbi0
[   22.890411] ip_tables: (C) 2000-2006 Netfilter Core Team
[   23.068779] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input4
[   23.222710] saa7134 ALSA driver for DMA sound loaded
[   23.222715] saa7130[0]/alsa: UNKNOWN/GENERIC doesn't support digital audio
[   23.537451]   alloc irq_desc for 22 on node -1
[   23.537455]   alloc kstat_irqs on node -1
[   23.537465] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   23.537507] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   23.641398] hda_codec: Unknown model for ALC888, trying auto-probe from BIOS...
[   23.641498] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input5
[   24.016177] EXT4-fs (sda8): internal journal on sda8:8
[   25.351134] EXT4-fs (sda1): barriers enabled
[   25.365340] kjournald2 starting: pid 886, dev sda1:8, commit interval 5 seconds
[   25.365577] EXT4-fs (sda1): internal journal on sda1:8
[   25.365584] EXT4-fs (sda1): delayed allocation enabled
[   25.365588] EXT4-fs: file extents enabled
[   25.368407] EXT4-fs: mballoc enabled
[   25.368429] EXT4-fs (sda1): mounted filesystem with ordered data mode
[   26.201317] EXT4-fs (sda9): barriers enabled
[   26.203229] kjournald2 starting: pid 893, dev sda9:8, commit interval 5 seconds
[   26.203364] EXT4-fs (sda9): internal journal on sda9:8
[   26.203372] EXT4-fs (sda9): delayed allocation enabled
[   26.203377] EXT4-fs: file extents enabled
[   26.210700] EXT4-fs: mballoc enabled
[   26.210720] EXT4-fs (sda9): mounted filesystem with ordered data mode
[   26.359478] r8169: eth0: link up
[   26.359491] r8169: eth0: link up
[   26.483588] type=1505 audit(1263576265.984:2): operation="profile_load" pid=1052 name=/usr/share/gdm/guest-session/Xsession
[   26.520021] type=1505 audit(1263576266.024:3): operation="profile_load" pid=1054 name=/sbin/dhclient3
[   26.520788] type=1505 audit(1263576266.024:4): operation="profile_load" pid=1054 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   26.521207] type=1505 audit(1263576266.024:5): operation="profile_load" pid=1054 name=/usr/lib/connman/scripts/dhclient-script
[   26.536022] type=1505 audit(1263576266.039:6): operation="profile_load" pid=1055 name=/usr/bin/evince
[   26.548050] type=1505 audit(1263576266.052:7): operation="profile_load" pid=1055 name=/usr/bin/evince-previewer
[   26.555719] type=1505 audit(1263576266.055:8): operation="profile_load" pid=1055 name=/usr/bin/evince-thumbnailer
[   26.566281] type=1505 audit(1263576266.067:9): operation="profile_load" pid=1059 name=/usr/bin/freshclam
[   26.573091] type=1505 audit(1263576266.076:10): operation="profile_load" pid=1063 name=/usr/lib/cups/backend/cups-pdf
[   26.573965] type=1505 audit(1263576266.076:11): operation="profile_load" pid=1063 name=/usr/sbin/cupsd
[   29.323836] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   29.323841] Bluetooth: BNEP filters: protocol multicast
[   29.356939] Bridge firewalling registered
[   29.642170] CPU0 attaching NULL sched-domain.
[   29.642178] CPU1 attaching NULL sched-domain.
[   29.660131] CPU0 attaching sched-domain:
[   29.660137]  domain 0: span 0-1 level MC
[   29.660141]   groups: 0 1
[   29.660147]   domain 1: span 0-1 level CPU
[   29.660150]    groups: 0-1 (__cpu_power = 2048)
[   29.660158] CPU1 attaching sched-domain:
[   29.660160]  domain 0: span 0-1 level MC
[   29.660164]   groups: 1 0
[   29.660169]   domain 1: span 0-1 level CPU
[   29.660172]    groups: 0-1 (__cpu_power = 2048)
[   29.866588] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   29.866592] vboxdrv: Successfully done.
[   29.866595] vboxdrv: Found 2 processor cores.
[   29.866695] vboxdrv: fAsync=0 offMin=0x78f offMax=0x387c
[   29.866755] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   29.866758] vboxdrv: Successfully loaded version 3.1.2 (interface 0x00100001).
[   30.004777] CPU0 attaching NULL sched-domain.
[   30.004785] CPU1 attaching NULL sched-domain.
[   30.016612] CPU0 attaching sched-domain:
[   30.016618]  domain 0: span 0-1 level CPU
[   30.016623]   groups: 0 1
[   30.016636] CPU1 attaching sched-domain:
[   30.016639]  domain 0: span 0-1 level CPU
[   30.016642]   groups: 1 0
[   31.166611] [drm] DAC-6: set mode  18
[   36.788018] eth0: no IPv6 routers present
[  126.751878] saa7134 ALSA driver for DMA sound unloaded
[  207.008992] saa7130/34: v4l2 driver version 0.2.15 loaded
[  207.009060] saa7130[0]: found at 0000:05:04.0, rev: 1, irq: 18, latency: 32, mmio: 0xb0000000
[  207.009071] saa7130[0]: subsystem: 1131:0000, board: Sabrent SBT-TVFM (saa7130) [card=42,insmod option]
[  207.009104] saa7130[0]: board init: gpio is 60c000
[  207.009111] IRQ 18/saa7130[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[  207.112263] saa7130[0]: Huh, no eeprom present (err=-5)?
[  207.112270] i2c-adapter i2c-1: Invalid 7-bit address 0x7a
[  207.176020] All bytes are equal. It is not a TEA5767
[  207.176155] tuner 1-0060: chip found @ 0xc0 (saa7130[0])
[  207.196024] tuner-simple 1-0060: creating new instance
[  207.196030] tuner-simple 1-0060: type set to 38 (Philips PAL/SECAM multi (FM1216ME MK3))
[  207.204133] saa7130[0]: registered device video1 [v4l2]
[  207.204176] saa7130[0]: registered device vbi0
[  207.204217] saa7130[0]: registered device radio0
[  207.214094] saa7134 ALSA driver for DMA sound loaded
[  207.214101] saa7130[0]/alsa: Sabrent SBT-TVFM (saa7130) doesn't support digital audio
hari@Indira:~$
```

---

### Post by Jose Catre-Vandis on 2010-01-15
I am pretty sure you don't have a dvb card, so just leave out the commands with -dvb at the end.

Use tvtime to view TV/scan for channels etc. Not sure how this works with a cable connection, but guess if it works under windows set the correct source in tvtime and you should be good to go.

---

### Post by hariks0 on 2010-01-15
The screenshot of TVTime is attached. Input configuration ==> Change Video Source is not opening anything.

---

### Post by Jose Catre-Vandis on 2010-01-16
Have you got a webcam plugged in? Looks like it is trying for that?

How is your tv cable connected, via composite? svideo? normal aerial connection?

Sorry I can't test as only have dvb on board

---

### Post by hariks0 on 2010-01-16
Yes. I have a usb webcam connected. Should I remove it and try? The cable is connected directly like an RF adapter.There is another small wire as areal for FM Radio also.

---

### Post by Jose Catre-Vandis on 2010-01-16
Yes please, just while we are trying to get setup. This may change the device order for your video devices following a reboot, but ubuntu normally sorts itself out on this one.

---

### Post by hariks0 on 2010-01-16
I started Ubuntu after removing the webcam. Entered those commands. Rebooted. Now the TVTime screen is Empty - No Blue display No OSD. Is there any other thing to be done?

---

### Post by Jose Catre-Vandis on 2010-01-17
You'll need to run the module commands after a reboot.

To help, and save you having to enter the commands each time, do the following:

```
sudo nano /etc/modprobe.d/saa7134.conf
```
add the options to this file as follows:
```
options card=42 tuner=38
```

Reboot

Check your dmesg to ensure modules are loaded and your card is recognised. Now you can forget about that bit, and concentrate on the other bit - getting tvtime running

---

### Post by Jose Catre-Vandis on 2010-01-22
@ hariks0

Have you made any progress?

---

### Post by hariks0 on 2010-01-22
> **Jose Catre-Vandis said:**
> @ hariks0

Have you made any progress?

Thank you first for follow up. But, No. I was not able to make any progress. The Nano opened a windows with no contents. I pasted the options command into it and rebooted. But it did not work. I thought I should no longer trouble you. But you were more generous.

Thank you once again.

---

### Post by Jose Catre-Vandis on 2010-01-23
OK so what does your dmesg look like now?

---

### Post by hariks0 on 2010-01-25
Sorry for the delay. I was out of home. I don't know where to look in the output hence I have posed the complete output here.The output of the dmesg is

```
hari@Indira:~$ dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.31-17-generic (buildd@palmer) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #54-Ubuntu SMP Thu Dec 10 16:20:31 UTC 2009 (Ubuntu 2.6.31-17.54-generic)
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
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000008f000 (usable)
[    0.000000]  BIOS-e820: 000000000008f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000009e5a9000 (usable)
[    0.000000]  BIOS-e820: 000000009e5a9000 - 000000009e6ad000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000009e6ad000 - 000000009f594000 (usable)
[    0.000000]  BIOS-e820: 000000009f594000 - 000000009f59c000 (reserved)
[    0.000000]  BIOS-e820: 000000009f59c000 - 000000009f62a000 (usable)
[    0.000000]  BIOS-e820: 000000009f62a000 - 000000009f62e000 (reserved)
[    0.000000]  BIOS-e820: 000000009f62e000 - 000000009f6a9000 (usable)
[    0.000000]  BIOS-e820: 000000009f6a9000 - 000000009f6e9000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000009f6e9000 - 000000009f6ed000 (usable)
[    0.000000]  BIOS-e820: 000000009f6ed000 - 000000009f6ff000 (ACPI data)
[    0.000000]  BIOS-e820: 000000009f6ff000 - 000000009f700000 (usable)
[    0.000000]  BIOS-e820: 000000009f700000 - 00000000a0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.4 present.
[    0.000000] last_pfn = 0x9f700 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-FFFFF uncachable
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 080000000 mask FE0000000 write-back
[    0.000000]   2 base 09F800000 mask FFF800000 uncachable
[    0.000000]   3 base 09F700000 mask FFFF00000 uncachable
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 0000000000002000 - 0000000000006000 (usable) ==> (reserved)
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 000000000008f000 (usable)
[    0.000000]  modified: 000000000008f000 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000009e5a9000 (usable)
[    0.000000]  modified: 000000009e5a9000 - 000000009e6ad000 (ACPI NVS)
[    0.000000]  modified: 000000009e6ad000 - 000000009f594000 (usable)
[    0.000000]  modified: 000000009f594000 - 000000009f59c000 (reserved)
[    0.000000]  modified: 000000009f59c000 - 000000009f62a000 (usable)
[    0.000000]  modified: 000000009f62a000 - 000000009f62e000 (reserved)
[    0.000000]  modified: 000000009f62e000 - 000000009f6a9000 (usable)
[    0.000000]  modified: 000000009f6a9000 - 000000009f6e9000 (ACPI NVS)
[    0.000000]  modified: 000000009f6e9000 - 000000009f6ed000 (usable)
[    0.000000]  modified: 000000009f6ed000 - 000000009f6ff000 (ACPI data)
[    0.000000]  modified: 000000009f6ff000 - 000000009f700000 (usable)
[    0.000000]  modified: 000000009f700000 - 00000000a0000000 (reserved)
[    0.000000]  modified: 00000000fff80000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 7000-c000
[    0.000000] RAMDISK: 375f4000 - 37fefe1c
[    0.000000] Allocated new RAMDISK: 008ad000 - 012a8e1c
[    0.000000] Move RAMDISK from 00000000375f4000 - 0000000037fefe1b to 008ad000 - 012a8e1b
[    0.000000] ACPI: RSDP 000fe020 00014 (v00 INTEL )
[    0.000000] ACPI: RSDT 9f6fd038 00050 (v01 INTEL  D945GCR  0000000A      01000013)
[    0.000000] ACPI: FACP 9f6fc000 00074 (v01 INTEL  D945GCR  0000000A MSFT 01000013)
[    0.000000] ACPI: DSDT 9f6f7000 04C39 (v01 INTEL  D945GCR  0000000A MSFT 01000013)
[    0.000000] ACPI: FACS 9f6a9000 00040
[    0.000000] ACPI: APIC 9f6f6000 00078 (v01 INTEL  D945GCR  0000000A MSFT 01000013)
[    0.000000] ACPI: WDDT 9f6f5000 00040 (v01 INTEL  D945GCR  0000000A MSFT 01000013)
[    0.000000] ACPI: MCFG 9f6f4000 0003C (v01 INTEL  D945GCR  0000000A MSFT 01000013)
[    0.000000] ACPI: ASF! 9f6f3000 000A6 (v32 INTEL  D945GCR  0000000A MSFT 01000013)
[    0.000000] ACPI: HPET 9f6f2000 00038 (v01 INTEL  D945GCR  0000000A MSFT 01000013)
[    0.000000] ACPI: SSDT 9f6f1000 001BC (v01 INTEL     CpuPm 0000000A MSFT 01000013)
[    0.000000] ACPI: SSDT 9f6f0000 00175 (v01 INTEL   Cpu0Ist 0000000A MSFT 01000013)
[    0.000000] ACPI: SSDT 9f6ef000 00175 (v01 INTEL   Cpu1Ist 0000000A MSFT 01000013)
[    0.000000] ACPI: SSDT 9f6ee000 00175 (v01 INTEL   Cpu2Ist 0000000A MSFT 01000013)
[    0.000000] ACPI: SSDT 9f6ed000 00175 (v01 INTEL   Cpu3Ist 0000000A MSFT 01000013)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 1663MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000]   node 0 low ram: 00000000 - 377fe000
[    0.000000]   node 0 bootmap 00008000 - 0000ef00
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008a80a0]    TEXT DATA BSS ==> [0000100000 - 00008a80a0]
[    0.000000]   #4 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #5 [00008a9000 - 00008ac161]              BRK ==> [00008a9000 - 00008ac161]
[    0.000000]   #6 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
[    0.000000]   #7 [00008ad000 - 00012a8e1c]      NEW RAMDISK ==> [00008ad000 - 00012a8e1c]
[    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]
[    0.000000] found SMP MP-table at [c00fe200] fe200
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x0009f700
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[8] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x0000008f
[    0.000000]     0: 0x00000100 -> 0x0009e5a9
[    0.000000]     0: 0x0009e6ad -> 0x0009f594
[    0.000000]     0: 0x0009f59c -> 0x0009f62a
[    0.000000]     0: 0x0009f62e -> 0x0009f6a9
[    0.000000]     0: 0x0009f6e9 -> 0x0009f6ed
[    0.000000]     0: 0x0009f6ff -> 0x0009f700
[    0.000000] On node 0 totalpages: 652585
[    0.000000] free_area_init_node: node 0, pgdat c0784960, node_mem_map c12a9000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3947 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 3327 pages used for memmap
[    0.000000]   HighMem zone: 422049 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 000000000008f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at a0000000 (gap: a0000000:5ff80000)
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages at c26a3000, static data 35612 bytes
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 647482
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-17-generic root=UUID=70c1fc36-030d-4e26-a9e8-3f3ce5f98a47 ro vga=771 quiet splash
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 13061120 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:0009f700)
[    0.000000] Memory: 2557112k/2612224k available (4566k kernel code, 52340k reserved, 2142k data, 540k init, 1701504k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc078e000 - 0xc0815000   ( 540 kB)
[    0.000000]       .data : 0xc0575a64 - 0xc078d408   (2142 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0575a64   (4566 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=128, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] NR_IRQS:2304 nr_irqs:440
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2992.416 MHz processor.
[    0.000028] Console: colour dummy device 80x25
[    0.000032] console [tty0] enabled
[    0.000161] hpet clockevent registered
[    0.000166] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.000172] Calibrating delay loop (skipped), value calculated using timer frequency.. 5984.83 BogoMIPS (lpj=11969664)
[    0.000193] Security Framework initialized
[    0.000213] AppArmor: AppArmor initialized
[    0.000223] Mount-cache hash table entries: 512
[    0.000374] Initializing cgroup subsys ns
[    0.000380] Initializing cgroup subsys cpuacct
[    0.000385] Initializing cgroup subsys memory
[    0.000393] Initializing cgroup subsys freezer
[    0.000396] Initializing cgroup subsys net_cls
[    0.000417] CPU: Trace cache: 12K uops, L1 D cache: 16K
[    0.000422] CPU: L2 cache: 2048K
[    0.000425] CPU: Physical Processor ID: 0
[    0.000427] CPU: Processor Core ID: 0
[    0.000431] mce: CPU supports 4 MCE banks
[    0.000445] CPU0: Thermal monitoring enabled (TM1)
[    0.000450] using mwait in idle threads.
[    0.000457] Performance Counters: no PMU driver, software counters only.
[    0.000465] Checking 'hlt' instruction... OK.
[    0.019539] ACPI: Core revision 20090521
[    0.031239] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.070932] CPU0: Intel(R) Pentium(R) D CPU 3.00GHz stepping 05
[    0.072001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 5985.12 BogoMIPS (lpj=11970258)
[    0.004000] CPU: Trace cache: 12K uops, L1 D cache: 16K
[    0.004000] CPU: L2 cache: 2048K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.004000] mce: CPU supports 4 MCE banks
[    0.004000] CPU1: Thermal monitoring enabled (TM1)
[    0.004000] x86 PAT enabled: cpu 1, old 0x7040600070406, new 0x7010600070106
[    0.157104] CPU1: Intel(R) Pentium(R) D CPU 3.00GHz stepping 05
[    0.157120] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.160018] Brought up 2 CPUs
[    0.160023] Total of 2 processors activated (11969.96 BogoMIPS).
[    0.160079] CPU0 attaching sched-domain:
[    0.160083]  domain 0: span 0-1 level CPU
[    0.160087]   groups: 0 1
[    0.160095] CPU1 attaching sched-domain:
[    0.160098]  domain 0: span 0-1 level CPU
[    0.160101]   groups: 1 0
[    0.160179] Booting paravirtualized kernel on bare hardware
[    0.160331] regulator: core version 0.5
[    0.160331] Time: 17:17:38  Date: 01/25/10
[    0.160331] NET: Registered protocol family 16
[    0.160331] EISA bus registered
[    0.160331] ACPI: bus type pci registered
[    0.160369] PCI: MCFG configuration 0: base f0000000 segment 0 buses 0 - 127
[    0.160374] PCI: Not using MMCONFIG.
[    0.164897] PCI: Using configuration type 1 for base access
[    0.166272] bio: create slab <bio-0> at 0
[    0.166272] ACPI: EC: Look up EC in DSDT
[    0.171981] ACPI: Interpreter enabled
[    0.171989] ACPI: (supports S0 S1 S3 S4 S5)
[    0.172029] ACPI: Using IOAPIC for interrupt routing
[    0.172077] PCI: MCFG configuration 0: base f0000000 segment 0 buses 0 - 127
[    0.175266] PCI: MCFG area at f0000000 reserved in ACPI motherboard resources
[    0.175271] PCI: updated MCFG configuration 0: base f0000000 segment 0 buses 0 - 63
[    0.175274] PCI: Using MMCONFIG for extended config space
[    0.180830] ACPI: No dock devices found.
[    0.182214] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.182329] pci 0000:00:02.0: reg 10 32bit mmio: [0xb0200000-0xb027ffff]
[    0.182336] pci 0000:00:02.0: reg 14 io port: [0x20e0-0x20e7]
[    0.182343] pci 0000:00:02.0: reg 18 32bit mmio: [0xa0000000-0xafffffff]
[    0.182349] pci 0000:00:02.0: reg 1c 32bit mmio: [0xb0280000-0xb02bffff]
[    0.182450] pci 0000:00:1b.0: reg 10 64bit mmio: [0xb02c0000-0xb02c3fff]
[    0.182503] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.182508] pci 0000:00:1b.0: PME# disabled
[    0.182582] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.182587] pci 0000:00:1c.0: PME# disabled
[    0.182662] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.182667] pci 0000:00:1c.1: PME# disabled
[    0.182743] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.182748] pci 0000:00:1c.2: PME# disabled
[    0.182826] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.182831] pci 0000:00:1c.3: PME# disabled
[    0.182890] pci 0000:00:1d.0: reg 20 io port: [0x2080-0x209f]
[    0.182950] pci 0000:00:1d.1: reg 20 io port: [0x2060-0x207f]
[    0.183009] pci 0000:00:1d.2: reg 20 io port: [0x2040-0x205f]
[    0.183068] pci 0000:00:1d.3: reg 20 io port: [0x2020-0x203f]
[    0.183134] pci 0000:00:1d.7: reg 10 32bit mmio: [0xb02c4000-0xb02c43ff]
[    0.183194] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.183200] pci 0000:00:1d.7: PME# disabled
[    0.183344] pci 0000:00:1f.0: quirk: region 0400-047f claimed by ICH6 ACPI/GPIO/TCO
[    0.183349] pci 0000:00:1f.0: quirk: region 0500-053f claimed by ICH6 GPIO
[    0.183354] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0680 (mask 007f)
[    0.183406] pci 0000:00:1f.1: reg 10 io port: [0x00-0x07]
[    0.183414] pci 0000:00:1f.1: reg 14 io port: [0x00-0x03]
[    0.183422] pci 0000:00:1f.1: reg 18 io port: [0x00-0x07]
[    0.183430] pci 0000:00:1f.1: reg 1c io port: [0x00-0x03]
[    0.183439] pci 0000:00:1f.1: reg 20 io port: [0x20b0-0x20bf]
[    0.183489] pci 0000:00:1f.2: reg 10 io port: [0x20c8-0x20cf]
[    0.183497] pci 0000:00:1f.2: reg 14 io port: [0x20ec-0x20ef]
[    0.183504] pci 0000:00:1f.2: reg 18 io port: [0x20c0-0x20c7]
[    0.183512] pci 0000:00:1f.2: reg 1c io port: [0x20e8-0x20eb]
[    0.183519] pci 0000:00:1f.2: reg 20 io port: [0x20a0-0x20af]
[    0.183549] pci 0000:00:1f.2: PME# supported from D3hot
[    0.183554] pci 0000:00:1f.2: PME# disabled
[    0.183607] pci 0000:00:1f.3: reg 20 io port: [0x2000-0x201f]
[    0.183760] pci 0000:02:00.0: reg 10 io port: [0x1000-0x10ff]
[    0.183786] pci 0000:02:00.0: reg 18 64bit mmio: [0xb0100000-0xb0100fff]
[    0.183812] pci 0000:02:00.0: reg 30 32bit mmio: [0xfffe0000-0xffffffff]
[    0.183867] pci 0000:02:00.0: supports D1 D2
[    0.183870] pci 0000:02:00.0: PME# supported from D1 D2 D3hot D3cold
[    0.183876] pci 0000:02:00.0: PME# disabled
[    0.183940] pci 0000:00:1c.1: bridge io port: [0x1000-0x1fff]
[    0.183945] pci 0000:00:1c.1: bridge 32bit mmio: [0xb0100000-0xb01fffff]
[    0.184114] pci 0000:05:04.0: reg 10 32bit mmio: [0xb0000000-0xb00003ff]
[    0.184171] pci 0000:05:04.0: supports D1 D2
[    0.184220] pci 0000:00:1e.0: transparent bridge
[    0.184227] pci 0000:00:1e.0: bridge 32bit mmio: [0xb0000000-0xb00fffff]
[    0.184260] pci_bus 0000:00: on NUMA node 0
[    0.184265] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.184513] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P32_._PRT]
[    0.184655] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX0._PRT]
[    0.184745] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX1._PRT]
[    0.184833] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX2._PRT]
[    0.184922] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX3._PRT]
[    0.190314] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 10 *11 12)
[    0.190463] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 9 *10 11 12)
[    0.190609] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 *10 11 12)
[    0.190760] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 *9 10 11 12)
[    0.190906] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
[    0.191053] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
[    0.191201] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 *9 10 11 12)
[    0.191346] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 9 10 *11 12)
[    0.191590] SCSI subsystem initialized
[    0.191619] libata version 3.00 loaded.
[    0.191619] usbcore: registered new interface driver usbfs
[    0.191619] usbcore: registered new interface driver hub
[    0.191619] usbcore: registered new device driver usb
[    0.192070] ACPI: WMI: Mapper loaded
[    0.192074] PCI: Using ACPI for IRQ routing
[    0.204013] Bluetooth: Core ver 2.15
[    0.204039] NET: Registered protocol family 31
[    0.204039] Bluetooth: HCI device and connection manager initialized
[    0.204039] Bluetooth: HCI socket layer initialized
[    0.204039] NetLabel: Initializing
[    0.204039] NetLabel:  domain hash size = 128
[    0.204040] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.204057] NetLabel:  unlabeled traffic allowed by default
[    0.204096] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.204104] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.220013] pnp: PnP ACPI init
[    0.220029] ACPI: bus type pnp registered
[    0.223605] pnp: PnP ACPI: found 13 devices
[    0.223608] ACPI: ACPI bus type pnp unregistered
[    0.223613] PnPBIOS: Disabled by ACPI PNP
[    0.223626] system 00:01: iomem range 0xf0000000-0xf3ffffff has been reserved
[    0.223631] system 00:01: iomem range 0xfed13000-0xfed13fff has been reserved
[    0.223635] system 00:01: iomem range 0xfed14000-0xfed17fff has been reserved
[    0.223639] system 00:01: iomem range 0xfed18000-0xfed18fff has been reserved
[    0.223642] system 00:01: iomem range 0xfed19000-0xfed19fff has been reserved
[    0.223646] system 00:01: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    0.223650] system 00:01: iomem range 0xfed20000-0xfed3ffff has been reserved
[    0.223653] system 00:01: iomem range 0xfed45000-0xfed99fff has been reserved
[    0.223657] system 00:01: iomem range 0xc0000-0xdffff could not be reserved
[    0.223661] system 00:01: iomem range 0xe0000-0xfffff could not be reserved
[    0.223671] system 00:06: ioport range 0x500-0x53f has been reserved
[    0.223675] system 00:06: ioport range 0x400-0x47f has been reserved
[    0.223679] system 00:06: ioport range 0x680-0x6ff has been reserved
[    0.223683] system 00:06: ioport range 0x770-0x77f has been reserved
[    0.258389] AppArmor: AppArmor Filesystem Enabled
[    0.258412] pci 0000:02:00.0: BAR 6: no parent found for of device [0xfffe0000-0xffffffff]
[    0.258461] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:01
[    0.258464] pci 0000:00:1c.0:   IO window: disabled
[    0.258470] pci 0000:00:1c.0:   MEM window: disabled
[    0.258475] pci 0000:00:1c.0:   PREFETCH window: disabled
[    0.258482] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:02
[    0.258486] pci 0000:00:1c.1:   IO window: 0x1000-0x1fff
[    0.258492] pci 0000:00:1c.1:   MEM window: 0xb0100000-0xb01fffff
[    0.258498] pci 0000:00:1c.1:   PREFETCH window: 0xb0300000-0xb03fffff
[    0.258503] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:03
[    0.258506] pci 0000:00:1c.2:   IO window: disabled
[    0.258511] pci 0000:00:1c.2:   MEM window: disabled
[    0.258516] pci 0000:00:1c.2:   PREFETCH window: disabled
[    0.258521] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:04
[    0.258523] pci 0000:00:1c.3:   IO window: disabled
[    0.258529] pci 0000:00:1c.3:   MEM window: disabled
[    0.258533] pci 0000:00:1c.3:   PREFETCH window: disabled
[    0.258538] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:05
[    0.258541] pci 0000:00:1e.0:   IO window: disabled
[    0.258547] pci 0000:00:1e.0:   MEM window: 0xb0000000-0xb00fffff
[    0.258551] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.258565]   alloc irq_desc for 17 on node -1
[    0.258569]   alloc kstat_irqs on node -1
[    0.258576] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.258582] pci 0000:00:1c.0: setting latency timer to 64
[    0.258595]   alloc irq_desc for 16 on node -1
[    0.258598]   alloc kstat_irqs on node -1
[    0.258603] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.258609] pci 0000:00:1c.1: setting latency timer to 64
[    0.258618]   alloc irq_desc for 18 on node -1
[    0.258620]   alloc kstat_irqs on node -1
[    0.258625] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.258631] pci 0000:00:1c.2: setting latency timer to 64
[    0.258639]   alloc irq_desc for 19 on node -1
[    0.258641]   alloc kstat_irqs on node -1
[    0.258646] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.258651] pci 0000:00:1c.3: setting latency timer to 64
[    0.258659] pci 0000:00:1e.0: setting latency timer to 64
[    0.258665] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.258668] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.258672] pci_bus 0000:02: resource 0 io:  [0x1000-0x1fff]
[    0.258675] pci_bus 0000:02: resource 1 mem: [0xb0100000-0xb01fffff]
[    0.258678] pci_bus 0000:02: resource 2 pref mem [0xb0300000-0xb03fffff]
[    0.258682] pci_bus 0000:05: resource 1 mem: [0xb0000000-0xb00fffff]
[    0.258685] pci_bus 0000:05: resource 3 io:  [0x00-0xffff]
[    0.258688] pci_bus 0000:05: resource 4 mem: [0x000000-0xffffffff]
[    0.258733] NET: Registered protocol family 2
[    0.258861] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.259300] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.259880] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.260181] TCP: Hash tables configured (established 131072 bind 65536)
[    0.260185] TCP reno registered
[    0.260283] NET: Registered protocol family 1
[    0.260364] Trying to unpack rootfs image as initramfs...
[    0.501034] Switched to high resolution mode on CPU 1
[    0.504017] Switched to high resolution mode on CPU 0
[    0.587301] Freeing initrd memory: 10223k freed
[    0.593187] cpufreq-nforce2: No nForce2 chipset.
[    0.593223] Scanning for low memory corruption every 60 seconds
[    0.593343] audit: initializing netlink socket (disabled)
[    0.593360] type=2000 audit(1264439857.592:1): initialized
[    0.602468] highmem bounce pool size: 64 pages
[    0.602480] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.604346] VFS: Disk quotas dquot_6.5.2
[    0.604426] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.605181] fuse init (API version 7.12)
[    0.605295] msgmni has been set to 1692
[    0.605628] alg: No test for stdrng (krng)
[    0.605658] io scheduler noop registered
[    0.605661] io scheduler anticipatory registered
[    0.605664] io scheduler deadline registered
[    0.605724] io scheduler cfq registered (default)
[    0.605738] pci 0000:00:02.0: Boot video device
[    0.606077]   alloc irq_desc for 24 on node -1
[    0.606080]   alloc kstat_irqs on node -1
[    0.606093] pcieport-driver 0000:00:1c.0: irq 24 for MSI/MSI-X
[    0.606104] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    0.606270]   alloc irq_desc for 25 on node -1
[    0.606273]   alloc kstat_irqs on node -1
[    0.606283] pcieport-driver 0000:00:1c.1: irq 25 for MSI/MSI-X
[    0.606293] pcieport-driver 0000:00:1c.1: setting latency timer to 64
[    0.606444]   alloc irq_desc for 26 on node -1
[    0.606447]   alloc kstat_irqs on node -1
[    0.606457] pcieport-driver 0000:00:1c.2: irq 26 for MSI/MSI-X
[    0.606467] pcieport-driver 0000:00:1c.2: setting latency timer to 64
[    0.606613]   alloc irq_desc for 27 on node -1
[    0.606617]   alloc kstat_irqs on node -1
[    0.606626] pcieport-driver 0000:00:1c.3: irq 27 for MSI/MSI-X
[    0.606636] pcieport-driver 0000:00:1c.3: setting latency timer to 64
[    0.606751] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.606894] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.607048] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    0.607053] ACPI: Power Button [PWRF]
[    0.607119] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1
[    0.607126] ACPI: Sleep Button [SLPB]
[    0.607509] processor LNXCPU:00: registered as cooling_device0
[    0.607634] processor LNXCPU:01: registered as cooling_device1
[    0.609325] isapnp: Scanning for PnP cards...
[    0.962572] isapnp: No Plug & Play device found
[    0.964025] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.964137] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.964598] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.965909] brd: module loaded
[    0.966497] loop: module loaded
[    0.966587] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    0.966726] ata_piix 0000:00:1f.1: version 2.13
[    0.966741] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.966784] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.966869] scsi0 : ata_piix
[    0.966980] scsi1 : ata_piix
[    0.967413] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x20b0 irq 14
[    0.967418] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x20b8 irq 15
[    0.967448] ata_piix 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.967455] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    0.967506] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.967571] scsi2 : ata_piix
[    0.967646] ata2: port disabled. ignoring.
[    0.967694] scsi3 : ata_piix
[    0.968491] ata3: SATA max UDMA/133 cmd 0x20c8 ctl 0x20ec bmdma 0x20a0 irq 19
[    0.968496] ata4: SATA max UDMA/133 cmd 0x20c0 ctl 0x20e8 bmdma 0x20a8 irq 19
[    0.969670] Fixed MDIO Bus: probed
[    0.969717] PPP generic driver version 2.4.2
[    0.969836] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.969859]   alloc irq_desc for 23 on node -1
[    0.969863]   alloc kstat_irqs on node -1
[    0.969870] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.969884] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.969889] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.969949] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.973866] ehci_hcd 0000:00:1d.7: debug port 1
[    0.973874] ehci_hcd 0000:00:1d.7: cache line size of 128 is not supported
[    0.973889] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xb02c4000
[    0.988012] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.988131] usb usb1: configuration #1 chosen from 1 choice
[    0.988172] hub 1-0:1.0: USB hub found
[    0.988182] hub 1-0:1.0: 8 ports detected
[    0.988266] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.988290] uhci_hcd: USB Universal Host Controller Interface driver
[    0.988319] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.988326] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.988330] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.988371] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.988398] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00002080
[    0.988494] usb usb2: configuration #1 chosen from 1 choice
[    0.988531] hub 2-0:1.0: USB hub found
[    0.988540] hub 2-0:1.0: 2 ports detected
[    0.988601] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.988609] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.988614] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.988653] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.988678] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00002060
[    0.988782] usb usb3: configuration #1 chosen from 1 choice
[    0.988818] hub 3-0:1.0: USB hub found
[    0.988826] hub 3-0:1.0: 2 ports detected
[    0.988888] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.988895] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.988899] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.988939] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.988971] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00002040
[    0.989063] usb usb4: configuration #1 chosen from 1 choice
[    0.989101] hub 4-0:1.0: USB hub found
[    0.989110] hub 4-0:1.0: 2 ports detected
[    0.989166] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    0.989173] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    0.989178] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    0.989220] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    0.989254] uhci_hcd 0000:00:1d.3: irq 16, io base 0x00002020
[    0.989348] usb usb5: configuration #1 chosen from 1 choice
[    0.989385] hub 5-0:1.0: USB hub found
[    0.989394] hub 5-0:1.0: 2 ports detected
[    0.989518] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    0.992144] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.992153] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.992246] mice: PS/2 mouse device common for all mice
[    0.992366] rtc_cmos 00:03: RTC can wake from S4
[    0.992406] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    0.992433] rtc0: alarms up to one month, 114 bytes nvram, hpet irqs
[    0.992573] device-mapper: uevent: version 1.0.3
[    0.992690] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.992802] device-mapper: multipath: version 1.1.0 loaded
[    0.992806] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.992998] EISA: Probing bus 0 at eisa.0
[    0.993010] Cannot allocate resource for EISA slot 1
[    0.993013] Cannot allocate resource for EISA slot 2
[    0.993035] EISA: Detected 0 cards.
[    0.993201] cpuidle: using governor ladder
[    0.993205] cpuidle: using governor menu
[    0.993919] TCP cubic registered
[    0.994095] NET: Registered protocol family 10
[    0.994719] lo: Disabled Privacy Extensions
[    0.995188] NET: Registered protocol family 17
[    0.995210] Bluetooth: L2CAP ver 2.13
[    0.995212] Bluetooth: L2CAP socket layer initialized
[    0.995216] Bluetooth: SCO (Voice Link) ver 0.6
[    0.995218] Bluetooth: SCO socket layer initialized
[    0.995262] Bluetooth: RFCOMM TTY layer initialized
[    0.995268] Bluetooth: RFCOMM socket layer initialized
[    0.995271] Bluetooth: RFCOMM ver 1.11
[    0.995696] Using IPI No-Shortcut mode
[    0.995774] PM: Resume from disk failed.
[    0.995790] registered taskstats version 1
[    0.995921]   Magic number: 10:370:290
[    0.995936] tty tty23: hash matches
[    0.995988] rtc_cmos 00:03: setting system clock to 2010-01-25 17:17:38 UTC (1264439858)
[    0.995992] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.995994] EDD information not available.
[    1.011616] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    1.132240] ata3.01: NODEV after polling detection
[    1.140363] ata3.00: ATAPI: TSSTcorp CDDVDW SH-S203B, SB00, max UDMA/100
[    1.156256] ata3.00: configured for UDMA/100
[    1.157555] scsi 2:0:0:0: CD-ROM            TSSTcorp CDDVDW SH-S203B  SB00 PQ: 0 ANSI: 5
[    1.161653] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.161659] Uniform CD-ROM driver Revision: 3.20
[    1.161779] sr 2:0:0:0: Attached scsi CD-ROM sr0
[    1.161834] sr 2:0:0:0: Attached scsi generic sg0 type 5
[    1.178187] ata4.00: ATA-7: ST3250820SV, 3.ACH, max UDMA/133
[    1.178192] ata4.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    1.244855] ata4.00: configured for UDMA/133
[    1.245030] scsi 3:0:0:0: Direct-Access     ATA      ST3250820SV      3.AC PQ: 0 ANSI: 5
[    1.245187] sd 3:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    1.245211] sd 3:0:0:0: Attached scsi generic sg1 type 0
[    1.245270] sd 3:0:0:0: [sda] Write Protect is off
[    1.245274] sd 3:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.245310] sd 3:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.245480]  sda: sda1 sda2 < sda5 sda6 sda7 sda8 sda9 >
[    1.362319] sd 3:0:0:0: [sda] Attached SCSI disk
[    1.362342] Freeing unused kernel memory: 540k freed
[    1.362768] Write protecting the kernel text: 4568k
[    1.362827] Write protecting the kernel read-only data: 1836k
[    1.514249] ramzswap: disk size set to 642188 kB
[    1.589447] Linux agpgart interface v0.103
[    1.593265] agpgart-intel 0000:00:00.0: Intel 945G Chipset
[    1.594107] agpgart-intel 0000:00:00.0: detected 7932K stolen memory
[    1.597567] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xa0000000
[    1.650308] Adding 642184k swap on /dev/ramzswap0.  Priority:100 extents:1 across:642184k SSD
[    1.657527] usb 3-2: new full speed USB device using uhci_hcd and address 2
[    1.664896] [drm] Initialized drm 1.1.0 20060810
[    1.684867] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.684875] i915 0000:00:02.0: setting latency timer to 64
[    1.691770] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.691790] r8169 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.691845] r8169 0000:02:00.0: setting latency timer to 64
[    1.691909]   alloc irq_desc for 28 on node -1
[    1.691912]   alloc kstat_irqs on node -1
[    1.691930] r8169 0000:02:00.0: irq 28 for MSI/MSI-X
[    1.692851] eth0: RTL8168b/8111b at 0xf8632000, 00:19:d1:a7:15:66, XID 38500000 IRQ 28
[    1.816240] [drm] fb0: inteldrmfb frame buffer device
[    1.816250] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    1.823253] Console: switching to colour frame buffer device 128x48
[    1.888748] [drm] DAC-6: set mode 1024x768 17
[    2.326900] vesafb: framebuffer at 0xa0000000, mapped to 0xf8b00000, using 512k, total 512k
[    2.326905] vesafb: mode is 800x600x8, linelength=832, pages=0
[    2.326908] vesafb: scrolling: redraw
[    2.326915] vesafb: Pseudocolor: size=0:8:8:8, shift=0:0:0:0
[    2.326983] fb1: VESA VGA frame buffer device
[    2.507819] xor: automatically using best checksumming function: pIII_sse
[    2.524007]    pIII_sse  :  4528.000 MB/sec
[    2.524011] xor: using function: pIII_sse (4528.000 MB/sec)
[    2.527010] device-mapper: dm-raid45: initialized v0.2594b
[    3.023739] PM: Starting manual resume from disk
[    3.023746] PM: Resume from partition 8:7
[    3.023748] PM: Checking hibernation image.
[    3.023899] PM: Resume from disk failed.
[    3.046798] EXT4-fs (sda8): INFO: recovery required on readonly filesystem
[    3.046805] EXT4-fs (sda8): write access will be enabled during recovery
[    3.054988] EXT4-fs (sda8): barriers enabled
[    4.292401] kjournald2 starting: pid 440, dev sda8:8, commit interval 5 seconds
[    4.292426] EXT4-fs (sda8): delayed allocation enabled
[    4.292433] EXT4-fs: file extents enabled
[    4.293911] EXT4-fs: mballoc enabled
[    4.293931] EXT4-fs (sda8): recovery complete
[    4.305035] EXT4-fs (sda8): mounted filesystem with ordered data mode
[   11.917508] usb 3-2: configuration #1 chosen from 1 choice
[   22.896831] udev: starting version 147
[   22.957955] Adding 4883720k swap on /dev/sda7.  Priority:-1 extents:1 across:4883720k 
[   23.182531] ip_tables: (C) 2000-2006 Netfilter Core Team
[   23.241487] parport_pc 00:07: reported by Plug and Play ACPI
[   23.241520] parport0: PC-style at 0x378, irq 7 [PCSPP,EPP]
[   23.357282] Bluetooth: Generic Bluetooth USB driver ver 0.5
[   23.357422] usbcore: registered new interface driver btusb
[   23.377234] lp0: using parport0 (interrupt-driven).
[   23.412214] psmouse serio1: ID: 10 00 64
[   23.474962] ppdev: user-space parallel port driver
[   23.649170] intel_rng: FWH not detected
[   23.692675] Linux video capture interface: v2.00
[   23.896010] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input4
[   24.010652] saa7130/34: v4l2 driver version 0.2.15 loaded
[   24.010711] saa7134 0000:05:04.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   24.010720] saa7130[0]: found at 0000:05:04.0, rev: 1, irq: 18, latency: 32, mmio: 0xb0000000
[   24.010727] saa7134: <rant>
[   24.010728] saa7134:  Congratulations!  Your TV card vendor saved a few
[   24.010730] saa7134:  cents for a eeprom, thus your pci board has no
[   24.010731] saa7134:  subsystem ID and I can't identify it automatically
[   24.010732] saa7134: </rant>
[   24.010733] saa7134: I feel better now.  Ok, here are the good news:
[   24.010735] saa7134: You can use the card=<nr> insmod option to specify
[   24.010736] saa7134: which board do you have.  The list:
[   24.010740] saa7134:   card=0 -> UNKNOWN/GENERIC                         
[   24.010744] saa7134:   card=1 -> Proteus Pro [philips reference design]   1131:2001 1131:2001
[   24.010750] saa7134:   card=2 -> LifeView FlyVIDEO3000                    5168:0138 4e42:0138
[   24.010756] saa7134:   card=3 -> LifeView/Typhoon FlyVIDEO2000            5168:0138 4e42:0138
[   24.010762] saa7134:   card=4 -> EMPRESS                                  1131:6752
[   24.010766] saa7134:   card=5 -> SKNet Monster TV                         1131:4e85
[   24.010771] saa7134:   card=6 -> Tevion MD 9717                          
[   24.010775] saa7134:   card=7 -> KNC One TV-Station RDS / Typhoon TV Tune 1131:fe01 1894:fe01
[   24.010781] saa7134:   card=8 -> Terratec Cinergy 400 TV                  153b:1142
[   24.010785] saa7134:   card=9 -> Medion 5044                             
[   24.010789] saa7134:   card=10 -> Kworld/KuroutoShikou SAA7130-TVPCI      
[   24.010792] saa7134:   card=11 -> Terratec Cinergy 600 TV                  153b:1143
[   24.010797] saa7134:   card=12 -> Medion 7134                              16be:0003 16be:5000
[   24.010803] saa7134:   card=13 -> Typhoon TV+Radio 90031                  
[   24.010806] saa7134:   card=14 -> ELSA EX-VISION 300TV                     1048:226b
[   24.010811] saa7134:   card=15 -> ELSA EX-VISION 500TV                     1048:226a
[   24.010815] saa7134:   card=16 -> ASUS TV-FM 7134                          1043:4842 1043:4830 1043:4840
[   24.010822] saa7134:   card=17 -> AOPEN VA1000 POWER                       1131:7133
[   24.010827] saa7134:   card=18 -> BMK MPEX No Tuner                       
[   24.010830] saa7134:   card=19 -> Compro VideoMate TV                      185b:c100
[   24.010835] saa7134:   card=20 -> Matrox CronosPlus                        102b:48d0
[   24.010840] saa7134:   card=21 -> 10MOONS PCI TV CAPTURE CARD              1131:2001
[   24.010845] saa7134:   card=22 -> AverMedia M156 / Medion 2819             1461:a70b
[   24.010849] saa7134:   card=23 -> BMK MPEX Tuner                          
[   24.010853] saa7134:   card=24 -> KNC One TV-Station DVR                   1894:a006
[   24.010858] saa7134:   card=25 -> ASUS TV-FM 7133                          1043:4843
[   24.010862] saa7134:   card=26 -> Pinnacle PCTV Stereo (saa7134)           11bd:002b
[   24.010867] saa7134:   card=27 -> Manli MuchTV M-TV002                    
[   24.010871] saa7134:   card=28 -> Manli MuchTV M-TV001                    
[   24.010874] saa7134:   card=29 -> Nagase Sangyo TransGear 3000TV           1461:050c
[   24.010879] saa7134:   card=30 -> Elitegroup ECS TVP3XP FM1216 Tuner Card( 1019:4cb4
[   24.010883] saa7134:   card=31 -> Elitegroup ECS TVP3XP FM1236 Tuner Card  1019:4cb5
[   24.010888] saa7134:   card=32 -> AVACS SmartTV                           
[   24.010892] saa7134:   card=33 -> AVerMedia DVD EZMaker                    1461:10ff
[   24.010896] saa7134:   card=34 -> Noval Prime TV 7133                     
[   24.010900] saa7134:   card=35 -> AverMedia AverTV Studio 305              1461:2115
[   24.010904] saa7134:   card=36 -> UPMOST PURPLE TV                         12ab:0800
[   24.010909] saa7134:   card=37 -> Items MuchTV Plus / IT-005              
[   24.010913] saa7134:   card=38 -> Terratec Cinergy 200 TV                  153b:1152
[   24.010917] saa7134:   card=39 -> LifeView FlyTV Platinum Mini             5168:0212 4e42:0212 5169:1502
[   24.010924] saa7134:   card=40 -> Compro VideoMate TV PVR/FM               185b:c100
[   24.010929] saa7134:   card=41 -> Compro VideoMate TV Gold+                185b:c100
[   24.010933] saa7134:   card=42 -> Sabrent SBT-TVFM (saa7130)              
[   24.010937] saa7134:   card=43 -> :Zolid Xpert TV7134                     
[   24.010940] saa7134:   card=44 -> Empire PCI TV-Radio LE                  
[   24.010944] saa7134:   card=45 -> Avermedia AVerTV Studio 307              1461:9715
[   24.010948] saa7134:   card=46 -> AVerMedia Cardbus TV/Radio (E500)        1461:d6ee
[   24.010953] saa7134:   card=47 -> Terratec Cinergy 400 mobile              153b:1162
[   24.010958] saa7134:   card=48 -> Terratec Cinergy 600 TV MK3              153b:1158
[   24.010962] saa7134:   card=49 -> Compro VideoMate Gold+ Pal               185b:c200
[   24.010967] saa7134:   card=50 -> Pinnacle PCTV 300i DVB-T + PAL           11bd:002d
[   24.010972] saa7134:   card=51 -> ProVideo PV952                           1540:9524
[   24.010976] saa7134:   card=52 -> AverMedia AverTV/305                     1461:2108
[   24.010981] saa7134:   card=53 -> ASUS TV-FM 7135                          1043:4845
[   24.010986] saa7134:   card=54 -> LifeView FlyTV Platinum FM / Gold        5168:0214 5168:5214 1489:0214 5168:0304
[   24.010994] saa7134:   card=55 -> LifeView FlyDVB-T DUO / MSI TV@nywhere D 5168:0306 4e42:0306
[   24.010999] saa7134:   card=56 -> Avermedia AVerTV 307                     1461:a70a
[   24.011004] saa7134:   card=57 -> Avermedia AVerTV GO 007 FM               1461:f31f
[   24.011009] saa7134:   card=58 -> ADS Tech Instant TV (saa7135)            1421:0350 1421:0351 1421:0370 1421:1370
[   24.011016] saa7134:   card=59 -> Kworld/Tevion V-Stream Xpert TV PVR7134 
[   24.011020] saa7134:   card=60 -> LifeView/Typhoon/Genius FlyDVB-T Duo Car 5168:0502 4e42:0502 1489:0502
[   24.011027] saa7134:   card=61 -> Philips TOUGH DVB-T reference design     1131:2004
[   24.011031] saa7134:   card=62 -> Compro VideoMate TV Gold+II             
[   24.011035] saa7134:   card=63 -> Kworld Xpert TV PVR7134                 
[   24.011039] saa7134:   card=64 -> FlyTV mini Asus Digimatrix               1043:0210
[   24.011043] saa7134:   card=65 -> V-Stream Studio TV Terminator           
[   24.011047] saa7134:   card=66 -> Yuan TUN-900 (saa7135)                  
[   24.011050] saa7134:   card=67 -> Beholder BeholdTV 409 FM                 0000:4091
[   24.011055] saa7134:   card=68 -> GoTView 7135 PCI                         5456:7135
[   24.011060] saa7134:   card=69 -> Philips EUROPA V3 reference design       1131:2004
[   24.011064] saa7134:   card=70 -> Compro Videomate DVB-T300                185b:c900
[   24.011069] saa7134:   card=71 -> Compro Videomate DVB-T200                185b:c901
[   24.011073] saa7134:   card=72 -> RTD Embedded Technologies VFG7350        1435:7350
[   24.011078] saa7134:   card=73 -> RTD Embedded Technologies VFG7330        1435:7330
[   24.011083] saa7134:   card=74 -> LifeView FlyTV Platinum Mini2            14c0:1212
[   24.011087] saa7134:   card=75 -> AVerMedia AVerTVHD MCE A180              1461:1044
[   24.011092] saa7134:   card=76 -> SKNet MonsterTV Mobile                   1131:4ee9
[   24.011097] saa7134:   card=77 -> Pinnacle PCTV 40i/50i/110i (saa7133)     11bd:002e
[   24.011101] saa7134:   card=78 -> ASUSTeK P7131 Dual                       1043:4862
[   24.011106] saa7134:   card=79 -> Sedna/MuchTV PC TV Cardbus TV/Radio (ITO
[   24.011109] saa7134:   card=80 -> ASUS Digimatrix TV                       1043:0210
[   24.011114] saa7134:   card=81 -> Philips Tiger reference design           1131:2018
[   24.011119] saa7134:   card=82 -> MSI TV@Anywhere plus                     1462:6231 1462:8624
[   24.011124] saa7134:   card=83 -> Terratec Cinergy 250 PCI TV              153b:1160
[   24.011129] saa7134:   card=84 -> LifeView FlyDVB Trio                     5168:0319
[   24.011134] saa7134:   card=85 -> AverTV DVB-T 777                         1461:2c05 1461:2c05
[   24.011139] saa7134:   card=86 -> LifeView FlyDVB-T / Genius VideoWonder D 5168:0301 1489:0301
[   24.011145] saa7134:   card=87 -> ADS Instant TV Duo Cardbus PTV331        0331:1421
[   24.011150] saa7134:   card=88 -> Tevion/KWorld DVB-T 220RF                17de:7201
[   24.011154] saa7134:   card=89 -> ELSA EX-VISION 700TV                     1048:226c
[   24.011159] saa7134:   card=90 -> Kworld ATSC110/115                       17de:7350 17de:7352
[   24.011165] saa7134:   card=91 -> AVerMedia A169 B                         1461:7360
[   24.011169] saa7134:   card=92 -> AVerMedia A169 B1                        1461:6360
[   24.011174] saa7134:   card=93 -> Medion 7134 Bridge #2                    16be:0005
[   24.011178] saa7134:   card=94 -> LifeView FlyDVB-T Hybrid Cardbus/MSI TV  5168:3306 5168:3502 5168:3307 4e42:3502
[   24.011186] saa7134:   card=95 -> LifeView FlyVIDEO3000 (NTSC)             5169:0138
[   24.011191] saa7134:   card=96 -> Medion Md8800 Quadro                     16be:0007 16be:0008 16be:000d
[   24.011197] saa7134:   card=97 -> LifeView FlyDVB-S /Acorp TV134DS         5168:0300 4e42:0300
[   24.011203] saa7134:   card=98 -> Proteus Pro 2309                         0919:2003
[   24.011208] saa7134:   card=99 -> AVerMedia TV Hybrid A16AR                1461:2c00
[   24.011212] saa7134:   card=100 -> Asus Europa2 OEM                         1043:4860
[   24.011217] saa7134:   card=101 -> Pinnacle PCTV 310i                       11bd:002f
[   24.011222] saa7134:   card=102 -> Avermedia AVerTV Studio 507              1461:9715
[   24.011226] saa7134:   card=103 -> Compro Videomate DVB-T200A              
[   24.011230] saa7134:   card=104 -> Hauppauge WinTV-HVR1110 DVB-T/Hybrid     0070:6700 0070:6701 0070:6702 0070:6703 0070:6704 0070:6705
[   24.011240] saa7134:   card=105 -> Terratec Cinergy HT PCMCIA               153b:1172
[   24.011244] saa7134:   card=106 -> Encore ENLTV                             1131:2342 1131:2341 3016:2344
[   24.011251] saa7134:   card=107 -> Encore ENLTV-FM                          1131:230f
[   24.011256] saa7134:   card=108 -> Terratec Cinergy HT PCI                  153b:1175
[   24.011260] saa7134:   card=109 -> Philips Tiger - S Reference design      
[   24.011264] saa7134:   card=110 -> Avermedia M102                           1461:f31e
[   24.011269] saa7134:   card=111 -> ASUS P7131 4871                          1043:4871
[   24.011273] saa7134:   card=112 -> ASUSTeK P7131 Hybrid                     1043:4876
[   24.011278] saa7134:   card=113 -> Elitegroup ECS TVP3XP FM1246 Tuner Card  1019:4cb6
[   24.011283] saa7134:   card=114 -> KWorld DVB-T 210                         17de:7250
[   24.011287] saa7134:   card=115 -> Sabrent PCMCIA TV-PCB05                  0919:2003
[   24.011292] saa7134:   card=116 -> 10MOONS TM300 TV Card                    1131:2304
[   24.011297] saa7134:   card=117 -> Avermedia Super 007                      1461:f01d
[   24.011302] saa7134:   card=118 -> Beholder BeholdTV 401                    0000:4016
[   24.011306] saa7134:   card=119 -> Beholder BeholdTV 403                    0000:4036
[   24.011311] saa7134:   card=120 -> Beholder BeholdTV 403 FM                 0000:4037
[   24.011316] saa7134:   card=121 -> Beholder BeholdTV 405                    0000:4050
[   24.011320] saa7134:   card=122 -> Beholder BeholdTV 405 FM                 0000:4051
[   24.011325] saa7134:   card=123 -> Beholder BeholdTV 407                    0000:4070
[   24.011329] saa7134:   card=124 -> Beholder BeholdTV 407 FM                 0000:4071
[   24.011334] saa7134:   card=125 -> Beholder BeholdTV 409                    0000:4090
[   24.011339] saa7134:   card=126 -> Beholder BeholdTV 505 FM                 5ace:5050
[   24.011343] saa7134:   card=127 -> Beholder BeholdTV 507 FM / BeholdTV 509  5ace:5070 5ace:5090
[   24.011349] saa7134:   card=128 -> Beholder BeholdTV Columbus TVFM          0000:5201
[   24.011354] saa7134:   card=129 -> Beholder BeholdTV 607 FM                 5ace:6070
[   24.011358] saa7134:   card=130 -> Beholder BeholdTV M6                     5ace:6190
[   24.011363] saa7134:   card=131 -> Twinhan Hybrid DTV-DVB 3056 PCI          1822:0022
[   24.011368] saa7134:   card=132 -> Genius TVGO AM11MCE                     
[   24.011371] saa7134:   card=133 -> NXP Snake DVB-S reference design        
[   24.011375] saa7134:   card=134 -> Medion/Creatix CTX953 Hybrid             16be:0010
[   24.011380] saa7134:   card=135 -> MSI TV@nywhere A/D v1.1                  1462:8625
[   24.011384] saa7134:   card=136 -> AVerMedia Cardbus TV/Radio (E506R)       1461:f436
[   24.011389] saa7134:   card=137 -> AVerMedia Hybrid TV/Radio (A16D)         1461:f936
[   24.011394] saa7134:   card=138 -> Avermedia M115                           1461:a836
[   24.011398] saa7134:   card=139 -> Compro VideoMate T750                    185b:c900
[   24.011403] saa7134:   card=140 -> Avermedia DVB-S Pro A700                 1461:a7a1
[   24.011408] saa7134:   card=141 -> Avermedia DVB-S Hybrid+FM A700           1461:a7a2
[   24.011412] saa7134:   card=142 -> Beholder BeholdTV H6                     5ace:6290
[   24.011417] saa7134:   card=143 -> Beholder BeholdTV M63                    5ace:6191
[   24.011422] saa7134:   card=144 -> Beholder BeholdTV M6 Extra               5ace:6193
[   24.011426] saa7134:   card=145 -> AVerMedia MiniPCI DVB-T Hybrid M103      1461:f636 1461:f736
[   24.011432] saa7134:   card=146 -> ASUSTeK P7131 Analog                    
[   24.011436] saa7134:   card=147 -> Asus Tiger 3in1                          1043:4878
[   24.011440] saa7134:   card=148 -> Encore ENLTV-FM v5.3                     1a7f:2008
[   24.011445] saa7134:   card=149 -> Avermedia PCI pure analog (M135A)        1461:f11d
[   24.011450] saa7134:   card=150 -> Zogis Real Angel 220                    
[   24.011453] saa7134:   card=151 -> ADS Tech Instant HDTV                    1421:0380
[   24.011458] saa7134:   card=152 -> Asus Tiger Rev:1.00                      1043:4857
[   24.011462] saa7134:   card=153 -> Kworld Plus TV Analog Lite PCI           17de:7128
[   24.011467] saa7134:   card=154 -> Avermedia AVerTV GO 007 FM Plus          1461:f31d
[   24.011472] saa7134:   card=155 -> Hauppauge WinTV-HVR1150 ATSC/QAM-Hybrid  0070:6706 0070:6708
[   24.011478] saa7134:   card=156 -> Hauppauge WinTV-HVR1120 DVB-T/Hybrid     0070:6707 0070:6709 0070:670a
[   24.011484] saa7134:   card=157 -> Avermedia AVerTV Studio 507UA            1461:a11b
[   24.011489] saa7134:   card=158 -> AVerMedia Cardbus TV/Radio (E501R)       1461:b7e9
[   24.011494] saa7134:   card=159 -> Beholder BeholdTV 505 RDS                0000:505b
[   24.011498] saa7134:   card=160 -> Beholder BeholdTV 507 RDS                0000:5071
[   24.011503] saa7134:   card=161 -> Beholder BeholdTV 507 RDS                0000:507b
[   24.011508] saa7134:   card=162 -> Beholder BeholdTV 607 FM                 5ace:6071
[   24.011512] saa7134:   card=163 -> Beholder BeholdTV 609 FM                 5ace:6090
[   24.011517] saa7134:   card=164 -> Beholder BeholdTV 609 FM                 5ace:6091
[   24.011522] saa7134:   card=165 -> Beholder BeholdTV 607 RDS                5ace:6072
[   24.011526] saa7134:   card=166 -> Beholder BeholdTV 607 RDS                5ace:6073
[   24.011531] saa7134:   card=167 -> Beholder BeholdTV 609 RDS                5ace:6092
[   24.011535] saa7134:   card=168 -> Beholder BeholdTV 609 RDS                5ace:6093
[   24.011541] saa7130[0]: subsystem: 1131:0000, board: UNKNOWN/GENERIC [card=0,autodetected]
[   24.011555] saa7130[0]: board init: gpio is 60c000
[   24.011561] IRQ 18/saa7130[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[   24.112220] saa7130[0]: Huh, no eeprom present (err=-5)?
[   24.112226] i2c-adapter i2c-1: Invalid 7-bit address 0x7a
[   24.112824] saa7130[0]: registered device video0 [v4l2]
[   24.112856] saa7130[0]: registered device vbi0
[   24.264752] saa7134 ALSA driver for DMA sound loaded
[   24.264758] saa7130[0]/alsa: UNKNOWN/GENERIC doesn't support digital audio
[   24.504117]   alloc irq_desc for 22 on node -1
[   24.504121]   alloc kstat_irqs on node -1
[   24.504131] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   24.504173] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   24.608220] hda_codec: Unknown model for ALC888, trying auto-probe from BIOS...
[   24.608316] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input5
[   25.064569] EXT4-fs (sda8): internal journal on sda8:8
[   26.909500] EXT4-fs (sda1): barriers enabled
[   26.923642] kjournald2 starting: pid 888, dev sda1:8, commit interval 5 seconds
[   26.923877] EXT4-fs (sda1): internal journal on sda1:8
[   26.923883] EXT4-fs (sda1): delayed allocation enabled
[   26.923887] EXT4-fs: file extents enabled
[   26.926480] EXT4-fs: mballoc enabled
[   26.926500] EXT4-fs (sda1): mounted filesystem with ordered data mode
[   27.758999] EXT4-fs (sda9): barriers enabled
[   27.759830] kjournald2 starting: pid 895, dev sda9:8, commit interval 5 seconds
[   27.759989] EXT4-fs (sda9): internal journal on sda9:8
[   27.759996] EXT4-fs (sda9): delayed allocation enabled
[   27.760001] EXT4-fs: file extents enabled
[   27.767268] EXT4-fs: mballoc enabled
[   27.767288] EXT4-fs (sda9): mounted filesystem with ordered data mode
[   27.904325] type=1505 audit(1264439885.408:2): operation="profile_load" pid=1027 name=/usr/share/gdm/guest-session/Xsession
[   27.906817] type=1505 audit(1264439885.408:3): operation="profile_load" pid=1028 name=/sbin/dhclient3
[   27.907579] type=1505 audit(1264439885.408:4): operation="profile_load" pid=1028 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   27.908006] type=1505 audit(1264439885.412:5): operation="profile_load" pid=1028 name=/usr/lib/connman/scripts/dhclient-script
[   27.912162] type=1505 audit(1264439885.416:6): operation="profile_load" pid=1029 name=/usr/bin/evince
[   27.924209] type=1505 audit(1264439885.428:7): operation="profile_load" pid=1029 name=/usr/bin/evince-previewer
[   27.935214] type=1505 audit(1264439885.436:8): operation="profile_load" pid=1029 name=/usr/bin/evince-thumbnailer
[   27.945861] type=1505 audit(1264439885.448:9): operation="profile_load" pid=1031 name=/usr/bin/freshclam
[   27.948296] type=1505 audit(1264439885.452:10): operation="profile_load" pid=1032 name=/usr/lib/cups/backend/cups-pdf
[   27.949205] type=1505 audit(1264439885.452:11): operation="profile_load" pid=1032 name=/usr/sbin/cupsd
[   28.026942] r8169: eth0: link up
[   28.026950] r8169: eth0: link up
[   30.923844] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   30.923849] Bluetooth: BNEP filters: protocol multicast
[   31.063942] Bridge firewalling registered
[   31.337411] CPU0 attaching NULL sched-domain.
[   31.337419] CPU1 attaching NULL sched-domain.
[   31.352583] CPU0 attaching sched-domain:
[   31.352589]  domain 0: span 0-1 level MC
[   31.352594]   groups: 0 1
[   31.352602]   domain 1: span 0-1 level CPU
[   31.352606]    groups: 0-1 (__cpu_power = 2048)
[   31.352615] CPU1 attaching sched-domain:
[   31.352618]  domain 0: span 0-1 level MC
[   31.352622]   groups: 1 0
[   31.352633]   domain 1: span 0-1 level CPU
[   31.352636]    groups: 0-1 (__cpu_power = 2048)
[   31.554344] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   31.554349] vboxdrv: Successfully done.
[   31.554351] vboxdrv: Found 2 processor cores.
[   31.554445] vboxdrv: fAsync=0 offMin=0x816 offMax=0x33bd
[   31.554502] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   31.554505] vboxdrv: Successfully loaded version 3.1.2 (interface 0x00100001).
[   32.349503] CPU0 attaching NULL sched-domain.
[   32.349512] CPU1 attaching NULL sched-domain.
[   32.364590] CPU0 attaching sched-domain:
[   32.364596]  domain 0: span 0-1 level CPU
[   32.364600]   groups: 0 1
[   32.364609] CPU1 attaching sched-domain:
[   32.364613]  domain 0: span 0-1 level CPU
[   32.364617]   groups: 1 0
[   35.457422] [drm] DAC-6: set mode  18
[   39.000512] eth0: no IPv6 routers present
hari@Indira:~$ 

```

---

### Post by Jose Catre-Vandis on 2010-01-25
This is the part you are interested in:```
[   24.010652] saa7130/34: v4l2 driver version 0.2.15 loaded
[   24.010711] saa7134 0000:05:04.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   24.010720] saa7130[0]: found at 0000:05:04.0, rev: 1, irq: 18, latency: 32, mmio: 0xb0000000
[   24.010727] saa7134: <rant>
[   24.010728] saa7134:  Congratulations!  Your TV card vendor saved a few
[   24.010730] saa7134:  cents for a eeprom, thus your pci board has no
[   24.010731] saa7134:  subsystem ID and I can't identify it automatically
[   24.010732] saa7134: </rant>
[   24.010733] saa7134: I feel better now.  Ok, here are the good news:
[   24.010735] saa7134: You can use the card=<nr> insmod option to specify
[   24.010736] saa7134: which board do you have.  The list:
[   24.010740] saa7134:   card=0 -> UNKNOWN/GENERIC                         
[   24.010744] saa7134:   card=1 -> Proteus Pro [philips reference design]   1131:2001 1131:2001
[   24.010750] saa7134:   card=2 -> LifeView FlyVIDEO3000                    5168:0138 4e42:0138
[   24.010756] saa7134:   card=3 -> LifeView/Typhoon FlyVIDEO2000            5168:0138 4e42:0138
[   24.010762] saa7134:   card=4 -> EMPRESS                                  1131:6752
[   24.010766] saa7134:   card=5 -> SKNet Monster TV                         1131:4e85
[   24.010771] saa7134:   card=6 -> Tevion MD 9717                          
[   24.010775] saa7134:   card=7 -> KNC One TV-Station RDS / Typhoon TV Tune 1131:fe01 1894:fe01
[   24.010781] saa7134:   card=8 -> Terratec Cinergy 400 TV                  153b:1142
[   24.010785] saa7134:   card=9 -> Medion 5044                             
[   24.010789] saa7134:   card=10 -> Kworld/KuroutoShikou SAA7130-TVPCI      
[   24.010792] saa7134:   card=11 -> Terratec Cinergy 600 TV                  153b:1143
[   24.010797] saa7134:   card=12 -> Medion 7134                              16be:0003 16be:5000
[   24.010803] saa7134:   card=13 -> Typhoon TV+Radio 90031                  
[   24.010806] saa7134:   card=14 -> ELSA EX-VISION 300TV                     1048:226b
[   24.010811] saa7134:   card=15 -> ELSA EX-VISION 500TV                     1048:226a
[   24.010815] saa7134:   card=16 -> ASUS TV-FM 7134                          1043:4842 1043:4830 1043:4840
[   24.010822] saa7134:   card=17 -> AOPEN VA1000 POWER                       1131:7133
[   24.010827] saa7134:   card=18 -> BMK MPEX No Tuner                       
[   24.010830] saa7134:   card=19 -> Compro VideoMate TV                      185b:c100
[   24.010835] saa7134:   card=20 -> Matrox CronosPlus                        102b:48d0
[   24.010840] saa7134:   card=21 -> 10MOONS PCI TV CAPTURE CARD              1131:2001
[   24.010845] saa7134:   card=22 -> AverMedia M156 / Medion 2819             1461:a70b
[   24.010849] saa7134:   card=23 -> BMK MPEX Tuner                          
[   24.010853] saa7134:   card=24 -> KNC One TV-Station DVR                   1894:a006
[   24.010858] saa7134:   card=25 -> ASUS TV-FM 7133                          1043:4843
[   24.010862] saa7134:   card=26 -> Pinnacle PCTV Stereo (saa7134)           11bd:002b
[   24.010867] saa7134:   card=27 -> Manli MuchTV M-TV002                    
[   24.010871] saa7134:   card=28 -> Manli MuchTV M-TV001                    
[   24.010874] saa7134:   card=29 -> Nagase Sangyo TransGear 3000TV           1461:050c
[   24.010879] saa7134:   card=30 -> Elitegroup ECS TVP3XP FM1216 Tuner Card( 1019:4cb4
[   24.010883] saa7134:   card=31 -> Elitegroup ECS TVP3XP FM1236 Tuner Card  1019:4cb5
[   24.010888] saa7134:   card=32 -> AVACS SmartTV                           
[   24.010892] saa7134:   card=33 -> AVerMedia DVD EZMaker                    1461:10ff
[   24.010896] saa7134:   card=34 -> Noval Prime TV 7133                     
[   24.010900] saa7134:   card=35 -> AverMedia AverTV Studio 305              1461:2115
[   24.010904] saa7134:   card=36 -> UPMOST PURPLE TV                         12ab:0800
[   24.010909] saa7134:   card=37 -> Items MuchTV Plus / IT-005              
[   24.010913] saa7134:   card=38 -> Terratec Cinergy 200 TV                  153b:1152
[   24.010917] saa7134:   card=39 -> LifeView FlyTV Platinum Mini             5168:0212 4e42:0212 5169:1502
[   24.010924] saa7134:   card=40 -> Compro VideoMate TV PVR/FM               185b:c100
[   24.010929] saa7134:   card=41 -> Compro VideoMate TV Gold+                185b:c100
[   24.010933] saa7134:   card=42 -> Sabrent SBT-TVFM (saa7130)              
[   24.010937] saa7134:   card=43 -> :Zolid Xpert TV7134                     
[   24.010940] saa7134:   card=44 -> Empire PCI TV-Radio LE                  
[   24.010944] saa7134:   card=45 -> Avermedia AVerTV Studio 307              1461:9715
[   24.010948] saa7134:   card=46 -> AVerMedia Cardbus TV/Radio (E500)        1461:d6ee
[   24.010953] saa7134:   card=47 -> Terratec Cinergy 400 mobile              153b:1162
[   24.010958] saa7134:   card=48 -> Terratec Cinergy 600 TV MK3              153b:1158
[   24.010962] saa7134:   card=49 -> Compro VideoMate Gold+ Pal               185b:c200
[   24.010967] saa7134:   card=50 -> Pinnacle PCTV 300i DVB-T + PAL           11bd:002d
[   24.010972] saa7134:   card=51 -> ProVideo PV952                           1540:9524
[   24.010976] saa7134:   card=52 -> AverMedia AverTV/305                     1461:2108
[   24.010981] saa7134:   card=53 -> ASUS TV-FM 7135                          1043:4845
[   24.010986] saa7134:   card=54 -> LifeView FlyTV Platinum FM / Gold        5168:0214 5168:5214 1489:0214 5168:0304
[   24.010994] saa7134:   card=55 -> LifeView FlyDVB-T DUO / MSI TV@nywhere D 5168:0306 4e42:0306
[   24.010999] saa7134:   card=56 -> Avermedia AVerTV 307                     1461:a70a
[   24.011004] saa7134:   card=57 -> Avermedia AVerTV GO 007 FM               1461:f31f
[   24.011009] saa7134:   card=58 -> ADS Tech Instant TV (saa7135)            1421:0350 1421:0351 1421:0370 1421:1370
[   24.011016] saa7134:   card=59 -> Kworld/Tevion V-Stream Xpert TV PVR7134 
[   24.011020] saa7134:   card=60 -> LifeView/Typhoon/Genius FlyDVB-T Duo Car 5168:0502 4e42:0502 1489:0502
[   24.011027] saa7134:   card=61 -> Philips TOUGH DVB-T reference design     1131:2004
[   24.011031] saa7134:   card=62 -> Compro VideoMate TV Gold+II             
[   24.011035] saa7134:   card=63 -> Kworld Xpert TV PVR7134                 
[   24.011039] saa7134:   card=64 -> FlyTV mini Asus Digimatrix               1043:0210
[   24.011043] saa7134:   card=65 -> V-Stream Studio TV Terminator           
[   24.011047] saa7134:   card=66 -> Yuan TUN-900 (saa7135)                  
[   24.011050] saa7134:   card=67 -> Beholder BeholdTV 409 FM                 0000:4091
[   24.011055] saa7134:   card=68 -> GoTView 7135 PCI                         5456:7135
[   24.011060] saa7134:   card=69 -> Philips EUROPA V3 reference design       1131:2004
[   24.011064] saa7134:   card=70 -> Compro Videomate DVB-T300                185b:c900
[   24.011069] saa7134:   card=71 -> Compro Videomate DVB-T200                185b:c901
[   24.011073] saa7134:   card=72 -> RTD Embedded Technologies VFG7350        1435:7350
[   24.011078] saa7134:   card=73 -> RTD Embedded Technologies VFG7330        1435:7330
[   24.011083] saa7134:   card=74 -> LifeView FlyTV Platinum Mini2            14c0:1212
[   24.011087] saa7134:   card=75 -> AVerMedia AVerTVHD MCE A180              1461:1044
[   24.011092] saa7134:   card=76 -> SKNet MonsterTV Mobile                   1131:4ee9
[   24.011097] saa7134:   card=77 -> Pinnacle PCTV 40i/50i/110i (saa7133)     11bd:002e
[   24.011101] saa7134:   card=78 -> ASUSTeK P7131 Dual                       1043:4862
[   24.011106] saa7134:   card=79 -> Sedna/MuchTV PC TV Cardbus TV/Radio (ITO
[   24.011109] saa7134:   card=80 -> ASUS Digimatrix TV                       1043:0210
[   24.011114] saa7134:   card=81 -> Philips Tiger reference design           1131:2018
[   24.011119] saa7134:   card=82 -> MSI TV@Anywhere plus                     1462:6231 1462:8624
[   24.011124] saa7134:   card=83 -> Terratec Cinergy 250 PCI TV              153b:1160
[   24.011129] saa7134:   card=84 -> LifeView FlyDVB Trio                     5168:0319
[   24.011134] saa7134:   card=85 -> AverTV DVB-T 777                         1461:2c05 1461:2c05
[   24.011139] saa7134:   card=86 -> LifeView FlyDVB-T / Genius VideoWonder D 5168:0301 1489:0301
[   24.011145] saa7134:   card=87 -> ADS Instant TV Duo Cardbus PTV331        0331:1421
[   24.011150] saa7134:   card=88 -> Tevion/KWorld DVB-T 220RF                17de:7201
[   24.011154] saa7134:   card=89 -> ELSA EX-VISION 700TV                     1048:226c
[   24.011159] saa7134:   card=90 -> Kworld ATSC110/115                       17de:7350 17de:7352
[   24.011165] saa7134:   card=91 -> AVerMedia A169 B                         1461:7360
[   24.011169] saa7134:   card=92 -> AVerMedia A169 B1                        1461:6360
[   24.011174] saa7134:   card=93 -> Medion 7134 Bridge #2                    16be:0005
[   24.011178] saa7134:   card=94 -> LifeView FlyDVB-T Hybrid Cardbus/MSI TV  5168:3306 5168:3502 5168:3307 4e42:3502
[   24.011186] saa7134:   card=95 -> LifeView FlyVIDEO3000 (NTSC)             5169:0138
[   24.011191] saa7134:   card=96 -> Medion Md8800 Quadro                     16be:0007 16be:0008 16be:000d
[   24.011197] saa7134:   card=97 -> LifeView FlyDVB-S /Acorp TV134DS         5168:0300 4e42:0300
[   24.011203] saa7134:   card=98 -> Proteus Pro 2309                         0919:2003
[   24.011208] saa7134:   card=99 -> AVerMedia TV Hybrid A16AR                1461:2c00
[   24.011212] saa7134:   card=100 -> Asus Europa2 OEM                         1043:4860
[   24.011217] saa7134:   card=101 -> Pinnacle PCTV 310i                       11bd:002f
[   24.011222] saa7134:   card=102 -> Avermedia AVerTV Studio 507              1461:9715
[   24.011226] saa7134:   card=103 -> Compro Videomate DVB-T200A              
[   24.011230] saa7134:   card=104 -> Hauppauge WinTV-HVR1110 DVB-T/Hybrid     0070:6700 0070:6701 0070:6702 0070:6703 0070:6704 0070:6705
[   24.011240] saa7134:   card=105 -> Terratec Cinergy HT PCMCIA               153b:1172
[   24.011244] saa7134:   card=106 -> Encore ENLTV                             1131:2342 1131:2341 3016:2344
[   24.011251] saa7134:   card=107 -> Encore ENLTV-FM                          1131:230f
[   24.011256] saa7134:   card=108 -> Terratec Cinergy HT PCI                  153b:1175
[   24.011260] saa7134:   card=109 -> Philips Tiger - S Reference design      
[   24.011264] saa7134:   card=110 -> Avermedia M102                           1461:f31e
[   24.011269] saa7134:   card=111 -> ASUS P7131 4871                          1043:4871
[   24.011273] saa7134:   card=112 -> ASUSTeK P7131 Hybrid                     1043:4876
[   24.011278] saa7134:   card=113 -> Elitegroup ECS TVP3XP FM1246 Tuner Card  1019:4cb6
[   24.011283] saa7134:   card=114 -> KWorld DVB-T 210                         17de:7250
[   24.011287] saa7134:   card=115 -> Sabrent PCMCIA TV-PCB05                  0919:2003
[   24.011292] saa7134:   card=116 -> 10MOONS TM300 TV Card                    1131:2304
[   24.011297] saa7134:   card=117 -> Avermedia Super 007                      1461:f01d
[   24.011302] saa7134:   card=118 -> Beholder BeholdTV 401                    0000:4016
[   24.011306] saa7134:   card=119 -> Beholder BeholdTV 403                    0000:4036
[   24.011311] saa7134:   card=120 -> Beholder BeholdTV 403 FM                 0000:4037
[   24.011316] saa7134:   card=121 -> Beholder BeholdTV 405                    0000:4050
[   24.011320] saa7134:   card=122 -> Beholder BeholdTV 405 FM                 0000:4051
[   24.011325] saa7134:   card=123 -> Beholder BeholdTV 407                    0000:4070
[   24.011329] saa7134:   card=124 -> Beholder BeholdTV 407 FM                 0000:4071
[   24.011334] saa7134:   card=125 -> Beholder BeholdTV 409                    0000:4090
[   24.011339] saa7134:   card=126 -> Beholder BeholdTV 505 FM                 5ace:5050
[   24.011343] saa7134:   card=127 -> Beholder BeholdTV 507 FM / BeholdTV 509  5ace:5070 5ace:5090
[   24.011349] saa7134:   card=128 -> Beholder BeholdTV Columbus TVFM          0000:5201
[   24.011354] saa7134:   card=129 -> Beholder BeholdTV 607 FM                 5ace:6070
[   24.011358] saa7134:   card=130 -> Beholder BeholdTV M6                     5ace:6190
[   24.011363] saa7134:   card=131 -> Twinhan Hybrid DTV-DVB 3056 PCI          1822:0022
[   24.011368] saa7134:   card=132 -> Genius TVGO AM11MCE                     
[   24.011371] saa7134:   card=133 -> NXP Snake DVB-S reference design        
[   24.011375] saa7134:   card=134 -> Medion/Creatix CTX953 Hybrid             16be:0010
[   24.011380] saa7134:   card=135 -> MSI TV@nywhere A/D v1.1                  1462:8625
[   24.011384] saa7134:   card=136 -> AVerMedia Cardbus TV/Radio (E506R)       1461:f436
[   24.011389] saa7134:   card=137 -> AVerMedia Hybrid TV/Radio (A16D)         1461:f936
[   24.011394] saa7134:   card=138 -> Avermedia M115                           1461:a836
[   24.011398] saa7134:   card=139 -> Compro VideoMate T750                    185b:c900
[   24.011403] saa7134:   card=140 -> Avermedia DVB-S Pro A700                 1461:a7a1
[   24.011408] saa7134:   card=141 -> Avermedia DVB-S Hybrid+FM A700           1461:a7a2
[   24.011412] saa7134:   card=142 -> Beholder BeholdTV H6                     5ace:6290
[   24.011417] saa7134:   card=143 -> Beholder BeholdTV M63                    5ace:6191
[   24.011422] saa7134:   card=144 -> Beholder BeholdTV M6 Extra               5ace:6193
[   24.011426] saa7134:   card=145 -> AVerMedia MiniPCI DVB-T Hybrid M103      1461:f636 1461:f736
[   24.011432] saa7134:   card=146 -> ASUSTeK P7131 Analog                    
[   24.011436] saa7134:   card=147 -> Asus Tiger 3in1                          1043:4878
[   24.011440] saa7134:   card=148 -> Encore ENLTV-FM v5.3                     1a7f:2008
[   24.011445] saa7134:   card=149 -> Avermedia PCI pure analog (M135A)        1461:f11d
[   24.011450] saa7134:   card=150 -> Zogis Real Angel 220                    
[   24.011453] saa7134:   card=151 -> ADS Tech Instant HDTV                    1421:0380
[   24.011458] saa7134:   card=152 -> Asus Tiger Rev:1.00                      1043:4857
[   24.011462] saa7134:   card=153 -> Kworld Plus TV Analog Lite PCI           17de:7128
[   24.011467] saa7134:   card=154 -> Avermedia AVerTV GO 007 FM Plus          1461:f31d
[   24.011472] saa7134:   card=155 -> Hauppauge WinTV-HVR1150 ATSC/QAM-Hybrid  0070:6706 0070:6708
[   24.011478] saa7134:   card=156 -> Hauppauge WinTV-HVR1120 DVB-T/Hybrid     0070:6707 0070:6709 0070:670a
[   24.011484] saa7134:   card=157 -> Avermedia AVerTV Studio 507UA            1461:a11b
[   24.011489] saa7134:   card=158 -> AVerMedia Cardbus TV/Radio (E501R)       1461:b7e9
[   24.011494] saa7134:   card=159 -> Beholder BeholdTV 505 RDS                0000:505b
[   24.011498] saa7134:   card=160 -> Beholder BeholdTV 507 RDS                0000:5071
[   24.011503] saa7134:   card=161 -> Beholder BeholdTV 507 RDS                0000:507b
[   24.011508] saa7134:   card=162 -> Beholder BeholdTV 607 FM                 5ace:6071
[   24.011512] saa7134:   card=163 -> Beholder BeholdTV 609 FM                 5ace:6090
[   24.011517] saa7134:   card=164 -> Beholder BeholdTV 609 FM                 5ace:6091
[   24.011522] saa7134:   card=165 -> Beholder BeholdTV 607 RDS                5ace:6072
[   24.011526] saa7134:   card=166 -> Beholder BeholdTV 607 RDS                5ace:6073
[   24.011531] saa7134:   card=167 -> Beholder BeholdTV 609 RDS                5ace:6092
[   24.011535] saa7134:   card=168 -> Beholder BeholdTV 609 RDS                5ace:6093
[   24.011541] saa7130[0]: subsystem: 1131:0000, board: UNKNOWN/GENERIC [card=0,autodetected]
[   24.011555] saa7130[0]: board init: gpio is 60c000
[   24.011561] IRQ 18/saa7130[0]: IRQF_DISABLED is not guaranteed on shared IRQs
[   24.112220] saa7130[0]: Huh, no eeprom present (err=-5)?
[   24.112226] i2c-adapter i2c-1: Invalid 7-bit address 0x7a
[   24.112824] saa7130[0]: registered device video0 [v4l2]
[   24.112856] saa7130[0]: registered device vbi0
[   24.264752] saa7134 ALSA driver for DMA sound loaded
[   24.264758] saa7130[0]/alsa: UNKNOWN/GENERIC doesn't support digital audio

```
and it is clear that you card is not loading.

Now we know that:
> sudo rmmod saa7134
sudo modprobe saa7134 card=42 tuner=38

I think I got the contents wrong in your saa7134.conf file. Try this:```
options saa7134 card=42 tuner=38
``` Hopefully this will work on boot.

Also try running tvtime in a terminal to see what,if any error messages you get.

---

### Post by Thomas Garman on 2010-01-25
I read this thread and searched around online after seeing what is suggested and I wonder is what you are doing here would also make a Pinnacle PCTV HD usb stick work.  I followed the EM28XX driver suggestions from the french site (which other people say works) and I havent been able to get anything going.

Incidentally, it works just fine in Vista with Mediacenter

---

### Post by Jose Catre-Vandis on 2010-01-26
> **Thomas Garman said:**
> I read this thread and searched around online after seeing what is suggested and I wonder is what you are doing here would also make a Pinnacle PCTV HD usb stick work.  I followed the EM28XX driver suggestions from the french site (which other people say works) and I havent been able to get anything going.

Incidentally, it works just fine in Vista with Mediacenter

OK Thomas, its not to clear what you have done so far, so can you please post back any relevant output from:
```
dmesg
lsusb
lspci -v
lsmod
```

Also please list clearly all product names and details to help identify the device. If you look at the list above, you will see that there are several Pinnacle cards identified, and I can also confirm that EM28xx is amongst them. The device should be in the kernel by now?

What are you using to scan for channels and to play/playback?

and which "french site" ?

---

### Post by tver3305 on 2010-07-22
I had to record a radio station for monitoring purposes under ubuntu.
I am using[INDENT]Ubuntu 10.04
LightView PCI Tv Card
[/INDENT]**Disclaimer**

[LIST]
[*]I am an average Linux user, and though I know about dmesg and some other commands, I dont know where exactly to use them and when, but I do know what they do
[*]I am an experienced windoze user
[*]Forget about using vm xp to access the tv card. If ubuntu cant see, then the vm wont either, [http://ubuntuforums.org/showthread.php?t=848664http://](http://ubuntuforums.org/showthread.php?t=848664http://)
[/LIST]
<rant>
Installing tv cards under ubuntu sucks:cry:
Installing LightView tv card is unplesant :(
</rant>

So I set about installing the card. Ubuntu could not see the card and on running dmesg, there was the eeprom rant. Here is my dmesg, or at least the bit that matters most.
```

[   12.424449]  sdb1
[   12.428060] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[   12.428100] sd 4:0:0:0: [sdb] Attached SCSI disk
[   12.433074] Linux video capture interface: v2.00
[   12.457876] [drm] Initialized drm 1.1.0 20060810
[   12.468219] saa7130/34: v4l2 driver version 0.2.15 loaded
[   12.468263]   alloc irq_desc for 20 on node -1
[   12.468264]   alloc kstat_irqs on node -1
[   12.468270] saa7134 0000:03:04.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[   12.468275] saa7130[0]: found at 0000:03:04.0, rev: 1, irq: 20, latency: 64, mmio: 0xfebffc00
[   12.468286] saa7134: <rant>
[   12.468286] saa7134:  Congratulations!  Your TV card vendor saved a few
[   12.468287] saa7134:  cents for a eeprom, thus your pci board has no
[   12.468288] saa7134:  subsystem ID and I can't identify it automatically
[   12.468288] saa7134: </rant>
[   12.468289] saa7134: I feel better now.  Ok, here are the good news:
[   12.468290] saa7134: You can use the card=<nr> insmod option to specify
[   12.468290] saa7134: which board do you have.  The list:
[   12.468292] saa7134:   card=0 -> UNKNOWN/GENERIC                         
[   12.468295] saa7134:   card=1 -> Proteus Pro [philips reference design]   1131:2001 1131:2001
[   12.468298] saa7134:   card=2 -> LifeView FlyVIDEO3000                    5168:0138 4e42:0138
[   12.468301] saa7134:   card=3 -> LifeView/Typhoon FlyVIDEO2000            5168:0138 4e42:0138
[   12.468304] saa7134:   card=4 -> EMPRESS                                  1131:6752
[   12.468306] saa7134:   card=5 -> SKNet Monster TV                         1131:4e85
[   12.468308] saa7134:   card=6 -> Tevion MD 9717                          
[   12.468310] saa7134:   card=7 -> KNC One TV-Station RDS / Typhoon TV Tune 1131:fe01 1894:fe01
[   12.468313] saa7134:   card=8 -> Terratec Cinergy 400 TV                  153b:1142
[   12.468316] saa7134:   card=9 -> Medion 5044                             
[   12.468318] saa7134:   card=10 -> Kworld/KuroutoShikou SAA7130-TVPCI      
[   12.468320] saa7134:   card=11 -> Terratec Cinergy 600 TV                  153b:1143
[   12.468322] saa7134:   card=12 -> Medion 7134                              16be:0003 16be:5000
[   12.468325] saa7134:   card=13 -> Typhoon TV+Radio 90031                  
[   12.468327] saa7134:   card=14 -> ELSA EX-VISION 300TV                     1048:226b
[   12.468330] saa7134:   card=15 -> ELSA EX-VISION 500TV                     1048:226a
[   12.468332] saa7134:   card=16 -> ASUS TV-FM 7134                          1043:4842 1043:4830 1043:4840
[   12.468335] saa7134:   card=17 -> AOPEN VA1000 POWER                       1131:7133
[   12.468338] saa7134:   card=18 -> BMK MPEX No Tuner                       
[   12.468340] saa7134:   card=19 -> Compro VideoMate TV                      185b:c100
[   12.468342] saa7134:   card=20 -> Matrox CronosPlus                        102b:48d0
[   12.468345] saa7134:   card=21 -> 10MOONS PCI TV CAPTURE CARD              1131:2001
[   12.468347] saa7134:   card=22 -> AverMedia M156 / Medion 2819             1461:a70b
[   12.468350] saa7134:   card=23 -> BMK MPEX Tuner                          
[   12.468352] saa7134:   card=24 -> KNC One TV-Station DVR                   1894:a006
[   12.468354] saa7134:   card=25 -> ASUS TV-FM 7133                          1043:4843
[   12.468357] saa7134:   card=26 -> Pinnacle PCTV Stereo (saa7134)           11bd:002b
[   12.468359] saa7134:   card=27 -> Manli MuchTV M-TV002                    
[   12.468361] saa7134:   card=28 -> Manli MuchTV M-TV001                    
[   12.468363] saa7134:   card=29 -> Nagase Sangyo TransGear 3000TV           1461:050c
[   12.468365] saa7134:   card=30 -> Elitegroup ECS TVP3XP FM1216 Tuner Card( 1019:4cb4
[   12.468368] saa7134:   card=31 -> Elitegroup ECS TVP3XP FM1236 Tuner Card  1019:4cb5
[   12.468370] saa7134:   card=32 -> AVACS SmartTV                           
[   12.468372] saa7134:   card=33 -> AVerMedia DVD EZMaker                    1461:10ff
[   12.468375] saa7134:   card=34 -> Noval Prime TV 7133                     
[   12.468377] saa7134:   card=35 -> AverMedia AverTV Studio 305              1461:2115
[   12.468379] saa7134:   card=36 -> UPMOST PURPLE TV                         12ab:0800
[   12.468382] saa7134:   card=37 -> Items MuchTV Plus / IT-005              
[   12.468383] saa7134:   card=38 -> Terratec Cinergy 200 TV                  153b:1152
[   12.468386] saa7134:   card=39 -> LifeView FlyTV Platinum Mini             5168:0212 4e42:0212 5169:1502
[   12.468389] saa7134:   card=40 -> Compro VideoMate TV PVR/FM               185b:c100
[   12.468392] saa7134:   card=41 -> Compro VideoMate TV Gold+                185b:c100
[   12.468394] saa7134:   card=42 -> Sabrent SBT-TVFM (saa7130)              
[   12.468396] saa7134:   card=43 -> :Zolid Xpert TV7134                     
[   12.468398] saa7134:   card=44 -> Empire PCI TV-Radio LE                  
[   12.468400] saa7134:   card=45 -> Avermedia AVerTV Studio 307              1461:9715
[   12.468403] saa7134:   card=46 -> AVerMedia Cardbus TV/Radio (E500)        1461:d6ee
[   12.468405] saa7134:   card=47 -> Terratec Cinergy 400 mobile              153b:1162
[   12.468407] saa7134:   card=48 -> Terratec Cinergy 600 TV MK3              153b:1158
[   12.468410] saa7134:   card=49 -> Compro VideoMate Gold+ Pal               185b:c200
[   12.468412] saa7134:   card=50 -> Pinnacle PCTV 300i DVB-T + PAL           11bd:002d
[   12.468415] saa7134:   card=51 -> ProVideo PV952                           1540:9524
[   12.468417] saa7134:   card=52 -> AverMedia AverTV/305                     1461:2108
[   12.468420] saa7134:   card=53 -> ASUS TV-FM 7135                          1043:4845
[   12.468422] saa7134:   card=54 -> LifeView FlyTV Platinum FM / Gold        5168:0214 5168:5214 1489:0214 5168:0304
[   12.468426] saa7134:   card=55 -> LifeView FlyDVB-T DUO / MSI TV@nywhere D 5168:0306 4e42:0306
[   12.468429] saa7134:   card=56 -> Avermedia AVerTV 307                     1461:a70a
[   12.468431] saa7134:   card=57 -> Avermedia AVerTV GO 007 FM               1461:f31f
[   12.468434] saa7134:   card=58 -> ADS Tech Instant TV (saa7135)            1421:0350 1421:0351 1421:0370 1421:1370
[   12.468438] saa7134:   card=59 -> Kworld/Tevion V-Stream Xpert TV PVR7134 
[   12.468440] saa7134:   card=60 -> LifeView/Typhoon/Genius FlyDVB-T Duo Car 5168:0502 4e42:0502 1489:0502
[   12.468443] saa7134:   card=61 -> Philips TOUGH DVB-T reference design     1131:2004
[   12.468446] saa7134:   card=62 -> Compro VideoMate TV Gold+II             
[   12.468448] saa7134:   card=63 -> Kworld Xpert TV PVR7134                 
[   12.468450] saa7134:   card=64 -> FlyTV mini Asus Digimatrix               1043:0210
[   12.468452] saa7134:   card=65 -> V-Stream Studio TV Terminator           
[   12.468454] saa7134:   card=66 -> Yuan TUN-900 (saa7135)                  
[   12.468456] saa7134:   card=67 -> Beholder BeholdTV 409 FM                 0000:4091
[   12.468458] saa7134:   card=68 -> GoTView 7135 PCI                         5456:7135
[   12.468461] saa7134:   card=69 -> Philips EUROPA V3 reference design       1131:2004
[   12.468463] saa7134:   card=70 -> Compro Videomate DVB-T300                185b:c900
[   12.468466] saa7134:   card=71 -> Compro Videomate DVB-T200                185b:c901
[   12.468468] saa7134:   card=72 -> RTD Embedded Technologies VFG7350        1435:7350
[   12.468471] saa7134:   card=73 -> RTD Embedded Technologies VFG7330        1435:7330
[   12.468473] saa7134:   card=74 -> LifeView FlyTV Platinum Mini2            14c0:1212
[   12.468475] saa7134:   card=75 -> AVerMedia AVerTVHD MCE A180              1461:1044
[   12.468478] saa7134:   card=76 -> SKNet MonsterTV Mobile                   1131:4ee9
[   12.468480] saa7134:   card=77 -> Pinnacle PCTV 40i/50i/110i (saa7133)     11bd:002e
[   12.468483] saa7134:   card=78 -> ASUSTeK P7131 Dual                       1043:4862
[   12.468485] saa7134:   card=79 -> Sedna/MuchTV PC TV Cardbus TV/Radio (ITO
[   12.468487] saa7134:   card=80 -> ASUS Digimatrix TV                       1043:0210
[   12.468490] saa7134:   card=81 -> Philips Tiger reference design           1131:2018
[   12.468492] saa7134:   card=82 -> MSI TV@Anywhere plus                     1462:6231 1462:8624
[   12.468495] saa7134:   card=83 -> Terratec Cinergy 250 PCI TV              153b:1160
[   12.468498] saa7134:   card=84 -> LifeView FlyDVB Trio                     5168:0319
[   12.468500] saa7134:   card=85 -> AverTV DVB-T 777                         1461:2c05 1461:2c05
[   12.468503] saa7134:   card=86 -> LifeView FlyDVB-T / Genius VideoWonder D 5168:0301 1489:0301
[   12.468506] saa7134:   card=87 -> ADS Instant TV Duo Cardbus PTV331        0331:1421
[   12.468509] saa7134:   card=88 -> Tevion/KWorld DVB-T 220RF                17de:7201
[   12.468511] saa7134:   card=89 -> ELSA EX-VISION 700TV                     1048:226c
[   12.468514] saa7134:   card=90 -> Kworld ATSC110/115                       17de:7350 17de:7352
[   12.468517] saa7134:   card=91 -> AVerMedia A169 B                         1461:7360
[   12.468519] saa7134:   card=92 -> AVerMedia A169 B1                        1461:6360
[   12.468522] saa7134:   card=93 -> Medion 7134 Bridge #2                    16be:0005
[   12.468524] saa7134:   card=94 -> LifeView FlyDVB-T Hybrid Cardbus/MSI TV  5168:3306 5168:3502 5168:3307 4e42:3502
[   12.468528] saa7134:   card=95 -> LifeView FlyVIDEO3000 (NTSC)             5169:0138
[   12.468531] saa7134:   card=96 -> Medion Md8800 Quadro                     16be:0007 16be:0008 16be:000d
[   12.468534] saa7134:   card=97 -> LifeView FlyDVB-S /Acorp TV134DS         5168:0300 4e42:0300
[   12.468537] saa7134:   card=98 -> Proteus Pro 2309                         0919:2003
[   12.468540] saa7134:   card=99 -> AVerMedia TV Hybrid A16AR                1461:2c00
[   12.468542] saa7134:   card=100 -> Asus Europa2 OEM                         1043:4860
[   12.468544] saa7134:   card=101 -> Pinnacle PCTV 310i                       11bd:002f
[   12.468547] saa7134:   card=102 -> Avermedia AVerTV Studio 507              1461:9715
[   12.468549] saa7134:   card=103 -> Compro Videomate DVB-T200A              
[   12.468551] saa7134:   card=104 -> Hauppauge WinTV-HVR1110 DVB-T/Hybrid     0070:6700 0070:6701 0070:6702 0070:6703 0070:6704 0070:6705
[   12.468556] saa7134:   card=105 -> Terratec Cinergy HT PCMCIA               153b:1172
[   12.468558] saa7134:   card=106 -> Encore ENLTV                             1131:2342 1131:2341 3016:2344
[   12.468562] saa7134:   card=107 -> Encore ENLTV-FM                          1131:230f
[   12.468564] saa7134:   card=108 -> Terratec Cinergy HT PCI                  153b:1175
[   12.468567] saa7134:   card=109 -> Philips Tiger - S Reference design      
[   12.468569] saa7134:   card=110 -> Avermedia M102                           1461:f31e
[   12.468571] saa7134:   card=111 -> ASUS P7131 4871                          1043:4871
[   12.468574] saa7134:   card=112 -> ASUSTeK P7131 Hybrid                     1043:4876
[   12.468576] saa7134:   card=113 -> Elitegroup ECS TVP3XP FM1246 Tuner Card  1019:4cb6
[   12.468579] saa7134:   card=114 -> KWorld DVB-T 210                         17de:7250
[   12.468581] saa7134:   card=115 -> Sabrent PCMCIA TV-PCB05                  0919:2003
[   12.468583] saa7134:   card=116 -> 10MOONS TM300 TV Card                    1131:2304
[   12.468586] saa7134:   card=117 -> Avermedia Super 007                      1461:f01d
[   12.468588] saa7134:   card=118 -> Beholder BeholdTV 401                    0000:4016
[   12.468591] saa7134:   card=119 -> Beholder BeholdTV 403                    0000:4036
[   12.468593] saa7134:   card=120 -> Beholder BeholdTV 403 FM                 0000:4037
[   12.468595] saa7134:   card=121 -> Beholder BeholdTV 405                    0000:4050
[   12.468598] saa7134:   card=122 -> Beholder BeholdTV 405 FM                 0000:4051
[   12.468600] saa7134:   card=123 -> Beholder BeholdTV 407                    0000:4070
[   12.468603] saa7134:   card=124 -> Beholder BeholdTV 407 FM                 0000:4071
[   12.468605] saa7134:   card=125 -> Beholder BeholdTV 409                    0000:4090
[   12.468607] saa7134:   card=126 -> Beholder BeholdTV 505 FM                 5ace:5050
[   12.468610] saa7134:   card=127 -> Beholder BeholdTV 507 FM / BeholdTV 509  5ace:5070 5ace:5090
[   12.468613] saa7134:   card=128 -> Beholder BeholdTV Columbus TVFM          0000:5201
[   12.468615] saa7134:   card=129 -> Beholder BeholdTV 607 FM                 5ace:6070
[   12.468618] saa7134:   card=130 -> Beholder BeholdTV M6                     5ace:6190
[   12.468620] saa7134:   card=131 -> Twinhan Hybrid DTV-DVB 3056 PCI          1822:0022
[   12.468623] saa7134:   card=132 -> Genius TVGO AM11MCE                     
[   12.468625] saa7134:   card=133 -> NXP Snake DVB-S reference design        
[   12.468627] saa7134:   card=134 -> Medion/Creatix CTX953 Hybrid             16be:0010
[   12.468629] saa7134:   card=135 -> MSI TV@nywhere A/D v1.1                  1462:8625
[   12.468632] saa7134:   card=136 -> AVerMedia Cardbus TV/Radio (E506R)       1461:f436
[   12.468634] saa7134:   card=137 -> AVerMedia Hybrid TV/Radio (A16D)         1461:f936
[   12.468636] saa7134:   card=138 -> Avermedia M115                           1461:a836
[   12.468639] saa7134:   card=139 -> Compro VideoMate T750                    185b:c900
[   12.468641] saa7134:   card=140 -> Avermedia DVB-S Pro A700                 1461:a7a1
[   12.468644] saa7134:   card=141 -> Avermedia DVB-S Hybrid+FM A700           1461:a7a2
[   12.468646] saa7134:   card=142 -> Beholder BeholdTV H6                     5ace:6290
[   12.468649] saa7134:   card=143 -> Beholder BeholdTV M63                    5ace:6191
[   12.468651] saa7134:   card=144 -> Beholder BeholdTV M6 Extra               5ace:6193
[   12.468654] saa7134:   card=145 -> AVerMedia MiniPCI DVB-T Hybrid M103      1461:f636 1461:f736
[   12.468657] saa7134:   card=146 -> ASUSTeK P7131 Analog                    
[   12.468659] saa7134:   card=147 -> Asus Tiger 3in1                          1043:4878
[   12.468661] saa7134:   card=148 -> Encore ENLTV-FM v5.3                     1a7f:2008
[   12.468663] saa7134:   card=149 -> Avermedia PCI pure analog (M135A)        1461:f11d
[   12.468666] saa7134:   card=150 -> Zogis Real Angel 220                    
[   12.468668] saa7134:   card=151 -> ADS Tech Instant HDTV                    1421:0380
[   12.468670] saa7134:   card=152 -> Asus Tiger Rev:1.00                      1043:4857
[   12.468673] saa7134:   card=153 -> Kworld Plus TV Analog Lite PCI           17de:7128
[   12.468675] saa7134:   card=154 -> Avermedia AVerTV GO 007 FM Plus          1461:f31d
[   12.468677] saa7134:   card=155 -> Hauppauge WinTV-HVR1150 ATSC/QAM-Hybrid  0070:6706 0070:6708
[   12.468680] saa7134:   card=156 -> Hauppauge WinTV-HVR1120 DVB-T/Hybrid     0070:6707 0070:6709 0070:670a
[   12.468684] saa7134:   card=157 -> Avermedia AVerTV Studio 507UA            1461:a11b
[   12.468686] saa7134:   card=158 -> AVerMedia Cardbus TV/Radio (E501R)       1461:b7e9
[   12.468689] saa7134:   card=159 -> Beholder BeholdTV 505 RDS                0000:505b
[   12.468691] saa7134:   card=160 -> Beholder BeholdTV 507 RDS                0000:5071
[   12.468694] saa7134:   card=161 -> Beholder BeholdTV 507 RDS                0000:507b
[   12.468696] saa7134:   card=162 -> Beholder BeholdTV 607 FM                 5ace:6071
[   12.468698] saa7134:   card=163 -> Beholder BeholdTV 609 FM                 5ace:6090
[   12.468701] saa7134:   card=164 -> Beholder BeholdTV 609 FM                 5ace:6091
[   12.468703] saa7134:   card=165 -> Beholder BeholdTV 607 RDS                5ace:6072
[   12.468706] saa7134:   card=166 -> Beholder BeholdTV 607 RDS                5ace:6073
[   12.468708] saa7134:   card=167 -> Beholder BeholdTV 609 RDS                5ace:6092
[   12.468711] saa7134:   card=168 -> Beholder BeholdTV 609 RDS                5ace:6093
[   12.468713] saa7134:   card=169 -> Compro VideoMate S350/S300               185b:c900
[   12.468716] saa7134:   card=170 -> AverMedia AverTV Studio 505              1461:a115
[   12.468718] saa7134:   card=171 -> Beholder BeholdTV X7                     5ace:7595
[   12.468721] saa7134:   card=172 -> RoverMedia TV Link Pro FM                19d1:0138
[   12.468723] saa7134:   card=173 -> Zolid Hybrid TV Tuner PCI                1131:2004
[   12.468726] saa7134:   card=174 -> Asus Europa Hybrid OEM                   1043:4847
[   12.468729] saa7130[0]: subsystem: 1131:0000, board: UNKNOWN/GENERIC [card=0,autodetected]
[   12.468760] saa7130[0]: board init: gpio is 804000

```After reading this forum and running lsusb, sorry I cant be able to post it here, I realized that my card closely resembles hariks0's card.

I followed the instructions of Jose Catre-Vandis,
```

sudo rmmod saa7134-alsa
sudo rmmod saa7134

then 

sudo modprobe saa7134 card=42 tuner=38 (It was quite fast, I can say)
sudo modprobe saa7134_alsa
sudo modprobe saa7134

```and it worked.

In a nut-shell, **if you are having LightView Tv Card, try the settings above**.

I installed gnomeradio and it picked the radio. I can pleasantly say that the radio reception is quite good, actually better than when I was using Honestech in windoze. There were some other settings involved including chmod'n the radio file to 777, cant remember which file, will post it when I get back to that machine.

For recording, pulseaudio didnt work for me, and neither was compiling mplayer with radio support. I ended up using old sound recorder to do the recording. It picks up gnomeradio output though the volume can be quite low.

One thing I didnt understand was how gnome radio is working. It seems to have its own sound properties manager, which by-pases gnome sound manager. When I mute the volume from gnome, I still can hear gnomeradio playing. I have to mute from gnomeradio.

When I exit gnomeradio a hush sound is heard which I cant mute. I am left to having gnomeradio on but muted.

Anyone with an idea of whats happening?

---

### Post by hariks0 on 2010-07-22
I am happy to see that at least another person was able to make use of this thread and his TV Tuner as well under Ubuntu. Mine still does not work :(. I will come back with the out come of the commands mentioned in tver3305's post. By the way, I am now using Ultimate Edition 2.7 [based on lucid] and Windows 7 32 bit Ultimate.

---

### Post by kh1116 on 2010-07-24
Hold up, i just installed this card saa7134, and have everything just about working except for radio. As for your sound problem, there is an option "mute on exit" you may want to try. (check the link)
[http://tinypic.com/view.php?pic=14cs8qw&s=3](http://tinypic.com/view.php?pic=14cs8qw&s=3)

what did you put for "radio device" to get the tuner working?

---

### Post by benplanet on 2010-08-18
which app do you guys use in ubuntu for TV capture? Mythtv is simply overkill.

---

### Post by cpcpcp on 2010-09-03
DVB TV card works ok in windows (dual boot) but in Linux (Ubuntu 10.04) the card is not seen when I try either  TV Time,ME TV, etc. Why is this? What should I do? The card is a fairly recent product of Peak (DVB-T Digital TV PCI card) and [EMAIL="support@peakhardware.com"]support@peakhardware.com[/EMAIL] does not respond:o
I have seen requests for the output of  lspci and dmesg so here is what I have been able to copy and paste.
 Over to you ;)
```
cjp@cjp-desktop:~$ lspci
00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev f3)
00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)
00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev f2)
00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev f2)
00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev f3)
00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev f3)
00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev f3)
00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev f3)
00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:06.0 SCSI storage controller: Initio Corporation INI-950 SCSI Adapter (rev 02)
01:07.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 62)
01:07.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 65)
05:00.0 VGA compatible controller: nVidia Corporation G96 [GeForce 9500 GT] (rev a1)

``````
[287787.612928] sr 3:0:1:0: [sr1] Add. Sense: Illegal mode for this track
[287787.612933] sr 3:0:1:0: [sr1] CDB: Read(10): 28 00 00 00 00 10 00 00 02 00
[287787.612940] end_request: I/O error, dev sr1, sector 64
[287787.613850] sr 3:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[287787.613853] sr 3:0:1:0: [sr1] Sense Key : Illegal Request [current] 
[287787.613858] sr 3:0:1:0: [sr1] Add. Sense: Illegal mode for this track
[287787.613862] sr 3:0:1:0: [sr1] CDB: Read(10): 28 00 00 00 00 10 00 00 02 00
[287787.613870] end_request: I/O error, dev sr1, sector 64
[287787.614775] sr 3:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[287787.614778] sr 3:0:1:0: [sr1] Sense Key : Illegal Request [current] 
[287787.614781] sr 3:0:1:0: [sr1] Add. Sense: Illegal mode for this track
[287787.614786] sr 3:0:1:0: [sr1] CDB: Read(10): 28 00 00 00 00 40 00 00 02 00
[287787.614794] end_request: I/O error, dev sr1, sector 256
[287787.615703] sr 3:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[287787.615706] sr 3:0:1:0: [sr1] Sense Key : Illegal Request [current] 
[287787.615710] sr 3:0:1:0: [sr1] Add. Sense: Illegal mode for this track
[287787.615714] sr 3:0:1:0: [sr1] CDB: Read(10): 28 00 00 00 00 40 00 00 02 00
[287787.615722] end_request: I/O error, dev sr1, sector 256
[287787.616622] sr 3:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[287787.616625] sr 3:0:1:0: [sr1] Sense Key : Illegal Request [current] 
[287787.616629] sr 3:0:1:0: [sr1] Add. Sense: Illegal mode for this track
[287787.616633] sr 3:0:1:0: [sr1] CDB: Read(10): 28 00 00 00 00 42 00 00 02 00
[287787.616640] end_request: I/O error, dev sr1, sector 264
[287787.617668] sr 3:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[287787.617671] sr 3:0:1:0: [sr1] Sense Key : Illegal Request [current] 
[287787.617675] sr 3:0:1:0: [sr1] Add. Sense: Illegal mode for this track
[287787.617680] sr 3:0:1:0: [sr1] CDB: Read(10): 28 00 00 00 00 42 00 00 02 00
[287787.617687] end_request: I/O error, dev sr1, sector 264
[287787.618689] sr 3:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[287787.618692] sr 3:0:1:0: [sr1] Sense Key : Illegal Request [current] 
[287787.618696] sr 3:0:1:0: [sr1] Add. Sense: Illegal mode for this track
[287787.618701] sr 3:0:1:0: [sr1] CDB: Read(10): 28 00 00 00 00 44 00 00 02 00
[287787.618708] end_request: I/O error, dev sr1, sector 272
[287787.619617] sr 3:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[287787.619620] sr 3:0:1:0: [sr1] Sense Key : Illegal Request [current] 
[287787.619623] sr 3:0:1:0: [sr1] Add. Sense: Illegal mode for this track
[287787.619628] sr 3:0:1:0: [sr1] CDB: Read(10): 28 00 00 00 00 44 00 00 02 00
[287787.619635] end_request: I/O error, dev sr1, sector 272
[287787.620534] sr 3:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[287787.620537] sr 3:0:1:0: [sr1] Sense Key : Illegal Request [current] 
[287787.620540] sr 3:0:1:0: [sr1] Add. Sense: Illegal mode for this track
[287787.620545] sr 3:0:1:0: [sr1] CDB: Read(10): 28 00 00 00 00 c0 00 00 02 00
[287787.620552] end_request: I/O error, dev sr1, sector 768
[287787.621442] sr 3:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[287787.621447] sr 3:0:1:0: [sr1] Sense Key : Illegal Request [current] 
[287787.621452] sr 3:0:1:0: [sr1] Add. Sense: Illegal mode for this track
[287787.621458] sr 3:0:1:0: [sr1] CDB: Read(10): 28 00 00 00 00 c0 00 00 02 00
[287787.621466] end_request: I/O error, dev sr1, sector 768
[287787.622397] sr 3:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[287787.622401] sr 3:0:1:0: [sr1] Sense Key : Illegal Request [current] 
[287787.622404] sr 3:0:1:0: [sr1] Add. Sense: Illegal mode for this track
[287787.622409] sr 3:0:1:0: [sr1] CDB: Read(10): 28 00 00 00 00 c2 00 00 02 00
[287787.622417] end_request: I/O error, dev sr1, sector 776
[287787.623322] sr 3:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[287787.623326] sr 3:0:1:0: [sr1] Sense Key : Illegal Request [current] 
[287787.623330] sr 3:0:1:0: [sr1] Add. Sense: Illegal mode for this track
[287787.623334] sr 3:0:1:0: [sr1] CDB: Read(10): 28 00 00 00 00 c2 00 00 02 00
[287787.623342] end_request: I/O error, dev sr1, sector 776
[287787.624371] sr 3:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[287787.624375] sr 3:0:1:0: [sr1] Sense Key : Illegal Request [current] 
[287787.624379] sr 3:0:1:0: [sr1] Add. Sense: Illegal mode for this track
[287787.624384] sr 3:0:1:0: [sr1] CDB: Read(10): 28 00 00 00 00 c4 00 00 02 00
[287787.624392] end_request: I/O error, dev sr1, sector 784
[287787.625299] sr 3:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[287787.625303] sr 3:0:1:0: [sr1] Sense Key : Illegal Request [current] 
[287787.625307] sr 3:0:1:0: [sr1] Add. Sense: Illegal mode for this track
[287787.625311] sr 3:0:1:0: [sr1] CDB: Read(10): 28 00 00 00 00 c4 00 00 02 00
[287787.625318] end_request: I/O error, dev sr1, sector 784
[287787.626203] sr 3:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[287787.626206] sr 3:0:1:0: [sr1] Sense Key : Illegal Request [current] 
[287787.626210] sr 3:0:1:0: [sr1] Add. Sense: Illegal mode for this track
[287787.626215] sr 3:0:1:0: [sr1] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[287787.626222] end_request: I/O error, dev sr1, sector 0
[287787.627128] sr 3:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[287787.627131] sr 3:0:1:0: [sr1] Sense Key : Illegal Request [current] 
[287787.627135] sr 3:0:1:0: [sr1] Add. Sense: Illegal mode for this track
[287787.627140] sr 3:0:1:0: [sr1] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[287787.627147] end_request: I/O error, dev sr1, sector 0
[287787.628051] sr 3:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[287787.628056] sr 3:0:1:0: [sr1] Sense Key : Illegal Request [current] 
[287787.628065] sr 3:0:1:0: [sr1] Add. Sense: Illegal mode for this track
[287787.628072] sr 3:0:1:0: [sr1] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[287787.628095] end_request: I/O error, dev sr1, sector 0
[287787.628970] sr 3:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[287787.628974] sr 3:0:1:0: [sr1] Sense Key : Illegal Request [current] 
[287787.628977] sr 3:0:1:0: [sr1] Add. Sense: Illegal mode for this track
[287787.628982] sr 3:0:1:0: [sr1] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[287787.628989] end_request: I/O error, dev sr1, sector 0
[287787.629897] sr 3:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[287787.629901] sr 3:0:1:0: [sr1] Sense Key : Illegal Request [current] 
[287787.629905] sr 3:0:1:0: [sr1] Add. Sense: Illegal mode for this track
[287787.629910] sr 3:0:1:0: [sr1] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[287787.629917] end_request: I/O error, dev sr1, sector 0
[287787.632598] sr 3:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[287787.632604] sr 3:0:1:0: [sr1] Sense Key : Illegal Request [current] 
[287787.632609] sr 3:0:1:0: [sr1] Add. Sense: Illegal mode for this track
[287787.632616] sr 3:0:1:0: [sr1] CDB: Read(10): 28 00 00 00 00 04 00 00 02 00
[287787.632624] end_request: I/O error, dev sr1, sector 16
[287787.633569] sr 3:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[287787.633573] sr 3:0:1:0: [sr1] Sense Key : Illegal Request [current] 
[287787.633576] sr 3:0:1:0: [sr1] Add. Sense: Illegal mode for this track
[287787.633581] sr 3:0:1:0: [sr1] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[287787.633588] end_request: I/O error, dev sr1, sector 0
[287787.634514] sr 3:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[287787.634521] sr 3:0:1:0: [sr1] Sense Key : Illegal Request [current] 
[287787.634526] sr 3:0:1:0: [sr1] Add. Sense: Illegal mode for this track
[287787.634532] sr 3:0:1:0: [sr1] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[287787.634541] end_request: I/O error, dev sr1, sector 0
[287787.635461] sr 3:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[287787.635464] sr 3:0:1:0: [sr1] Sense Key : Illegal Request [current] 
[287787.635468] sr 3:0:1:0: [sr1] Add. Sense: Illegal mode for this track
[287787.635473] sr 3:0:1:0: [sr1] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[287787.635480] end_request: I/O error, dev sr1, sector 0
[287787.636446] sr 3:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[287787.636449] sr 3:0:1:0: [sr1] Sense Key : Illegal Request [current] 
[287787.636453] sr 3:0:1:0: [sr1] Add. Sense: Illegal mode for this track
[287787.636457] sr 3:0:1:0: [sr1] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[287787.636464] end_request: I/O error, dev sr1, sector 0
[287787.637385] sr 3:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[287787.637389] sr 3:0:1:0: [sr1] Sense Key : Illegal Request [current] 
[287787.637392] sr 3:0:1:0: [sr1] Add. Sense: Illegal mode for this track
[287787.637397] sr 3:0:1:0: [sr1] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[287787.637404] end_request: I/O error, dev sr1, sector 0
[287787.638310] sr 3:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[287787.638314] sr 3:0:1:0: [sr1] Sense Key : Illegal Request [current] 
[287787.638317] sr 3:0:1:0: [sr1] Add. Sense: Illegal mode for this track
[287787.638322] sr 3:0:1:0: [sr1] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[287787.638330] end_request: I/O error, dev sr1, sector 0
[287787.642417] sr 3:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[287787.642421] sr 3:0:1:0: [sr1] Sense Key : Illegal Request [current] 
[287787.642425] sr 3:0:1:0: [sr1] Add. Sense: Illegal mode for this track
[287787.642431] sr 3:0:1:0: [sr1] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[287787.642438] end_request: I/O error, dev sr1, sector 0
[287787.643338] sr 3:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[287787.643341] sr 3:0:1:0: [sr1] Sense Key : Illegal Request [current] 
[287787.643345] sr 3:0:1:0: [sr1] Add. Sense: Illegal mode for this track
[287787.643350] sr 3:0:1:0: [sr1] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[287787.643357] end_request: I/O error, dev sr1, sector 0
[287787.644255] sr 3:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[287787.644259] sr 3:0:1:0: [sr1] Sense Key : Illegal Request [current] 
[287787.644263] sr 3:0:1:0: [sr1] Add. Sense: Illegal mode for this track
[287787.644269] sr 3:0:1:0: [sr1] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[287787.644276] end_request: I/O error, dev sr1, sector 0
[287787.645189] sr 3:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[287787.645193] sr 3:0:1:0: [sr1] Sense Key : Illegal Request [current] 
[287787.645196] sr 3:0:1:0: [sr1] Add. Sense: Illegal mode for this track
[287787.645201] sr 3:0:1:0: [sr1] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[287787.645208] end_request: I/O error, dev sr1, sector 0
[287787.646119] sr 3:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[287787.646123] sr 3:0:1:0: [sr1] Sense Key : Illegal Request [current] 
[287787.646126] sr 3:0:1:0: [sr1] Add. Sense: Illegal mode for this track
[287787.646131] sr 3:0:1:0: [sr1] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[287787.646139] end_request: I/O error, dev sr1, sector 0
[287787.647049] sr 3:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[287787.647052] sr 3:0:1:0: [sr1] Sense Key : Illegal Request [current] 
[287787.647056] sr 3:0:1:0: [sr1] Add. Sense: Illegal mode for this track
[287787.647061] sr 3:0:1:0: [sr1] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[287787.647068] end_request: I/O error, dev sr1, sector 0
[287787.647975] sr 3:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[287787.647978] sr 3:0:1:0: [sr1] Sense Key : Illegal Request [current] 
[287787.647981] sr 3:0:1:0: [sr1] Add. Sense: Illegal mode for this track
[287787.647987] sr 3:0:1:0: [sr1] CDB: Read(10): 28 00 00 00 00 20 00 00 02 00
[287787.647994] end_request: I/O error, dev sr1, sector 128
[287787.648893] sr 3:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[287787.648896] sr 3:0:1:0: [sr1] Sense Key : Illegal Request [current] 
[287787.648900] sr 3:0:1:0: [sr1] Add. Sense: Illegal mode for this track
[287787.648905] sr 3:0:1:0: [sr1] CDB: Read(10): 28 00 00 00 00 20 00 00 02 00
[287787.648912] end_request: I/O error, dev sr1, sector 128
[287787.649828] sr 3:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[287787.649831] sr 3:0:1:0: [sr1] Sense Key : Illegal Request [current] 
[287787.649835] sr 3:0:1:0: [sr1] Add. Sense: Illegal mode for this track
[287787.649839] sr 3:0:1:0: [sr1] CDB: Read(10): 28 00 00 00 00 04 00 00 02 00
[287787.649847] end_request: I/O error, dev sr1, sector 16
[287787.650751] sr 3:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[287787.650755] sr 3:0:1:0: [sr1] Sense Key : Illegal Request [current] 
[287787.650758] sr 3:0:1:0: [sr1] Add. Sense: Illegal mode for this track
[287787.650763] sr 3:0:1:0: [sr1] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[287787.650771] end_request: I/O error, dev sr1, sector 0
[287787.651847] sr 3:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[287787.651850] sr 3:0:1:0: [sr1] Sense Key : Illegal Request [current] 
[287787.651854] sr 3:0:1:0: [sr1] Add. Sense: Illegal mode for this track
[287787.651859] sr 3:0:1:0: [sr1] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[287787.651867] end_request: I/O error, dev sr1, sector 0
[287787.652767] sr 3:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[287787.652770] sr 3:0:1:0: [sr1] Sense Key : Illegal Request [current] 
[287787.652774] sr 3:0:1:0: [sr1] Add. Sense: Illegal mode for this track
[287787.652778] sr 3:0:1:0: [sr1] CDB: Read(10): 28 00 00 00 00 02 00 00 02 00
[287787.652786] end_request: I/O error, dev sr1, sector 8
[287787.653700] sr 3:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[287787.653704] sr 3:0:1:0: [sr1] Sense Key : Illegal Request [current] 
[287787.653707] sr 3:0:1:0: [sr1] Add. Sense: Illegal mode for this track
[287787.653712] sr 3:0:1:0: [sr1] CDB: Read(10): 28 00 00 00 00 04 00 00 02 00
[287787.653719] end_request: I/O error, dev sr1, sector 16
[287787.654627] sr 3:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[287787.654631] sr 3:0:1:0: [sr1] Sense Key : Illegal Request [current] 
[287787.654634] sr 3:0:1:0: [sr1] Add. Sense: Illegal mode for this track
[287787.654639] sr 3:0:1:0: [sr1] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[287787.654647] end_request: I/O error, dev sr1, sector 0
[287787.655551] sr 3:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[287787.655555] sr 3:0:1:0: [sr1] Sense Key : Illegal Request [current] 
[287787.655558] sr 3:0:1:0: [sr1] Add. Sense: Illegal mode for this track
[287787.655563] sr 3:0:1:0: [sr1] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[287787.655571] end_request: I/O error, dev sr1, sector 0
[287787.656470] sr 3:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[287787.656473] sr 3:0:1:0: [sr1] Sense Key : Illegal Request [current] 
[287787.656477] sr 3:0:1:0: [sr1] Add. Sense: Illegal mode for this track
[287787.656481] sr 3:0:1:0: [sr1] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[287787.656488] end_request: I/O error, dev sr1, sector 0
[287787.657403] sr 3:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[287787.657406] sr 3:0:1:0: [sr1] Sense Key : Illegal Request [current] 
[287787.657410] sr 3:0:1:0: [sr1] Add. Sense: Illegal mode for this track
[287787.657415] sr 3:0:1:0: [sr1] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[287787.657422] end_request: I/O error, dev sr1, sector 0
[287787.658330] sr 3:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[287787.658333] sr 3:0:1:0: [sr1] Sense Key : Illegal Request [current] 
[287787.658337] sr 3:0:1:0: [sr1] Add. Sense: Illegal mode for this track
[287787.658342] sr 3:0:1:0: [sr1] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[287787.658349] end_request: I/O error, dev sr1, sector 0
[287787.659259] sr 3:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[287787.659263] sr 3:0:1:0: [sr1] Sense Key : Illegal Request [current] 
[287787.659266] sr 3:0:1:0: [sr1] Add. Sense: Illegal mode for this track
[287787.659271] sr 3:0:1:0: [sr1] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[287787.659279] end_request: I/O error, dev sr1, sector 0
[287787.660449] sr 3:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[287787.660453] sr 3:0:1:0: [sr1] Sense Key : Illegal Request [current] 
[287787.660457] sr 3:0:1:0: [sr1] Add. Sense: Illegal mode for this track
[287787.660461] sr 3:0:1:0: [sr1] CDB: Read(10): 28 00 00 00 00 02 00 00 02 00
[287787.660468] end_request: I/O error, dev sr1, sector 8
[287787.661384] sr 3:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[287787.661387] sr 3:0:1:0: [sr1] Sense Key : Illegal Request [current] 
[287787.661391] sr 3:0:1:0: [sr1] Add. Sense: Illegal mode for this track
[287787.661396] sr 3:0:1:0: [sr1] CDB: Read(10): 28 00 00 00 00 20 00 00 02 00
[287787.661403] end_request: I/O error, dev sr1, sector 128
[287787.662301] sr 3:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[287787.662305] sr 3:0:1:0: [sr1] Sense Key : Illegal Request [current] 
[287787.662309] sr 3:0:1:0: [sr1] Add. Sense: Illegal mode for this track
[287787.662313] sr 3:0:1:0: [sr1] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[287787.662321] end_request: I/O error, dev sr1, sector 0
[287787.663237] sr 3:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[287787.663241] sr 3:0:1:0: [sr1] Sense Key : Illegal Request [current] 
[287787.663245] sr 3:0:1:0: [sr1] Add. Sense: Illegal mode for this track
[287787.663249] sr 3:0:1:0: [sr1] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[287787.663257] end_request: I/O error, dev sr1, sector 0
[287787.664157] sr 3:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[287787.664161] sr 3:0:1:0: [sr1] Sense Key : Illegal Request [current] 
[287787.664165] sr 3:0:1:0: [sr1] Add. Sense: Illegal mode for this track
[287787.664169] sr 3:0:1:0: [sr1] CDB: Read(10): 28 00 00 00 04 00 00 00 02 00
[287787.664177] end_request: I/O error, dev sr1, sector 4096
[287787.818764] sr 3:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[287787.818771] sr 3:0:1:0: [sr1] Sense Key : Illegal Request [current] 
[287787.818776] sr 3:0:1:0: [sr1] Add. Sense: Illegal mode for this track
[287787.818782] sr 3:0:1:0: [sr1] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[287787.818791] end_request: I/O error, dev sr1, sector 0
[287787.819708] sr 3:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[287787.819711] sr 3:0:1:0: [sr1] Sense Key : Illegal Request [current] 
[287787.819714] sr 3:0:1:0: [sr1] Add. Sense: Illegal mode for this track
[287787.819719] sr 3:0:1:0: [sr1] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[287787.819727] end_request: I/O error, dev sr1, sector 0
[287787.820626] sr 3:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[287787.820630] sr 3:0:1:0: [sr1] Sense Key : Illegal Request [current] 
[287787.820633] sr 3:0:1:0: [sr1] Add. Sense: Illegal mode for this track
[287787.820638] sr 3:0:1:0: [sr1] CDB: Read(10): 28 00 00 00 00 00 00 00 02 00
[287787.820645] end_request: I/O error, dev sr1, sector 0
[315075.852042] usb 1-9: new high speed USB device using ehci_hcd and address 6
[315075.985516] usb 1-9: configuration #1 chosen from 1 choice
[315075.986141] scsi10 : SCSI emulation for USB Mass Storage devices
[315075.986265] usb-storage: device found at 6
[315075.986268] usb-storage: waiting for device to settle before scanning
[315080.984312] usb-storage: device scan complete
[315080.985785] scsi 10:0:0:0: Direct-Access     Nokia    S60              1.0  PQ: 0 ANSI: 0
[315080.986321] sd 10:0:0:0: Attached scsi generic sg5 type 0
[315080.991137] sd 10:0:0:0: [sdd] 15564800 512-byte logical blocks: (7.96 GB/7.42 GiB)
[315080.991503] sd 10:0:0:0: [sdd] Write Protect is off
[315080.991507] sd 10:0:0:0: [sdd] Mode Sense: 03 00 00 00
[315080.991509] sd 10:0:0:0: [sdd] Assuming drive cache: write through
[315080.993127] sd 10:0:0:0: [sdd] Assuming drive cache: write through
[315080.993131]  sdd:
[315081.129256] sd 10:0:0:0: [sdd] Assuming drive cache: write through
[315081.129262] sd 10:0:0:0: [sdd] Attached SCSI removable disk
[317358.215954] usb 1-9: USB disconnect, address 6
[354397.940294] usb 1-1: new high speed USB device using ehci_hcd and address 7
[354398.074906] usb 1-1: configuration #1 chosen from 1 choice
[354398.075462] scsi11 : SCSI emulation for USB Mass Storage devices
[354398.075605] usb-storage: device found at 7
[354398.075608] usb-storage: waiting for device to settle before scanning
[354398.089812] usb 1-1: USB disconnect, address 7
[354398.388030] usb 1-1: new high speed USB device using ehci_hcd and address 8
[354398.523152] usb 1-1: configuration #1 chosen from 1 choice
[354398.524861] scsi12 : SCSI emulation for USB Mass Storage devices
[354398.525172] usb-storage: device found at 8
[354398.525174] usb-storage: waiting for device to settle before scanning
[354403.525231] usb-storage: device scan complete
[354403.527071] scsi 12:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
[354403.527684] scsi 12:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
[354403.528305] scsi 12:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ: 0 ANSI: 0
[354403.528794] scsi 12:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0
[354403.531106] sd 12:0:0:0: Attached scsi generic sg5 type 0
[354403.533631] sd 12:0:0:1: Attached scsi generic sg6 type 0
[354403.534416] sd 12:0:0:2: Attached scsi generic sg7 type 0
[354403.534961] sd 12:0:0:3: Attached scsi generic sg8 type 0
[354434.112065] usb 1-1: reset high speed USB device using ehci_hcd and address 8
[354444.356029] usb 1-1: reset high speed USB device using ehci_hcd and address 8
[354460.600037] usb 1-1: reset high speed USB device using ehci_hcd and address 8
[354460.848030] usb 1-1: reset high speed USB device using ehci_hcd and address 8
[354471.092027] usb 1-1: reset high speed USB device using ehci_hcd and address 8
[354471.226948] sd 12:0:0:0: Device offlined - not ready after error recovery
[354471.226984] sd 12:0:0:0: rejecting I/O to offline device
[354471.226992] sd 12:0:0:0: rejecting I/O to offline device
[354471.226996] sd 12:0:0:0: rejecting I/O to offline device
[354471.227000] sd 12:0:0:0: [sdd] READ CAPACITY failed
[354471.227002] sd 12:0:0:0: [sdd] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[354471.227006] sd 12:0:0:0: [sdd] Sense not available.
[354471.227011] sd 12:0:0:0: rejecting I/O to offline device
[354471.227016] sd 12:0:0:0: [sdd] Write Protect is off
[354471.227018] sd 12:0:0:0: [sdd] Mode Sense: 00 00 00 00
[354471.227021] sd 12:0:0:0: [sdd] Assuming drive cache: write through
[354471.227178] sd 12:0:0:0: [sdd] Attached SCSI removable disk
[354471.234709] sd 12:0:0:1: [sde] Attached SCSI removable disk
[354471.235702] sd 12:0:0:2: [sdf] Attached SCSI removable disk
[354471.236325] sd 12:0:0:3: [sdg] Attached SCSI removable disk
[354777.447227] usb 1-1: USB disconnect, address 8
[354795.384027] usb 1-1: new high speed USB device using ehci_hcd and address 9
[354795.519024] usb 1-1: configuration #1 chosen from 1 choice
[354795.519691] scsi13 : SCSI emulation for USB Mass Storage devices
[354795.519848] usb-storage: device found at 9
[354795.519850] usb-storage: waiting for device to settle before scanning
[354800.516217] usb-storage: device scan complete
[354800.518182] scsi 13:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
[354800.518793] scsi 13:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
[354800.519416] scsi 13:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ: 0 ANSI: 0
[354800.520365] scsi 13:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0
[354800.520976] sd 13:0:0:0: Attached scsi generic sg5 type 0
[354800.523325] sd 13:0:0:1: Attached scsi generic sg6 type 0
[354800.524350] sd 13:0:0:2: Attached scsi generic sg7 type 0
[354800.524832] sd 13:0:0:3: Attached scsi generic sg8 type 0
[354831.100037] usb 1-1: reset high speed USB device using ehci_hcd and address 9
[354841.344257] usb 1-1: reset high speed USB device using ehci_hcd and address 9
[354857.588029] usb 1-1: reset high speed USB device using ehci_hcd and address 9
[354857.836034] usb 1-1: reset high speed USB device using ehci_hcd and address 9
[354859.931201] usb 1-1: USB disconnect, address 9
[354859.931320] sd 13:0:0:0: Device offlined - not ready after error recovery
[354859.931465] sd 13:0:0:2: [sdf] READ CAPACITY failed
[354859.931468] sd 13:0:0:2: [sdf] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[354859.931472] sd 13:0:0:2: [sdf] Sense not available.
[354859.931482] sd 13:0:0:3: [sdg] READ CAPACITY failed
[354859.931484] sd 13:0:0:3: [sdg] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[354859.931487] sd 13:0:0:3: [sdg] Sense not available.
[354859.931501] sd 13:0:0:2: [sdf] Write Protect is off
[354859.931504] sd 13:0:0:2: [sdf] Mode Sense: 00 06 04 5e
[354859.931507] sd 13:0:0:2: [sdf] Assuming drive cache: write through
[354859.931694] sd 13:0:0:3: [sdg] Write Protect is off
[354859.931697] sd 13:0:0:3: [sdg] Mode Sense: 00 06 04 5e
[354859.931699] sd 13:0:0:3: [sdg] Assuming drive cache: write through
[354859.932777] sd 13:0:0:1: [sde] READ CAPACITY failed
[354859.932783] sd 13:0:0:1: [sde] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[354859.932788] sd 13:0:0:1: [sde] Sense not available.
[354859.932802] sd 13:0:0:0: [sdd] READ CAPACITY failed
[354859.932805] sd 13:0:0:0: [sdd] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[354859.932808] sd 13:0:0:0: [sdd] Sense not available.
[354859.932820] sd 13:0:0:0: [sdd] Write Protect is off
[354859.932823] sd 13:0:0:0: [sdd] Mode Sense: 00 06 04 5e
[354859.932825] sd 13:0:0:0: [sdd] Assuming drive cache: write through
[354859.933007] sd 13:0:0:1: [sde] Write Protect is off
[354859.933010] sd 13:0:0:1: [sde] Mode Sense: 00 06 04 5e
[354859.933012] sd 13:0:0:1: [sde] Assuming drive cache: write through
[354859.933146] sd 13:0:0:1: [sde] READ CAPACITY failed
[354859.933149] sd 13:0:0:1: [sde] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[354859.933152] sd 13:0:0:1: [sde] Sense not available.
[354859.933164] sd 13:0:0:1: [sde] Assuming drive cache: write through
[354859.933167] sd 13:0:0:1: [sde] Attached SCSI removable disk
[354859.933200] sd 13:0:0:0: [sdd] READ CAPACITY failed
[354859.933202] sd 13:0:0:0: [sdd] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[354859.933205] sd 13:0:0:0: [sdd] Sense not available.
[354859.933217] sd 13:0:0:0: [sdd] Assuming drive cache: write through
[354859.933219] sd 13:0:0:0: [sdd] Attached SCSI removable disk
[354859.934558] sd 13:0:0:3: [sdg] READ CAPACITY failed
[354859.934564] sd 13:0:0:3: [sdg] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[354859.934568] sd 13:0:0:3: [sdg] Sense not available.
[354859.934625] sd 13:0:0:3: [sdg] Assuming drive cache: write through
[354859.934630] sd 13:0:0:3: [sdg] Attached SCSI removable disk
[354859.934738] sd 13:0:0:2: [sdf] READ CAPACITY failed
[354859.934740] sd 13:0:0:2: [sdf] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[354859.934743] sd 13:0:0:2: [sdf] Sense not available.
[354859.934957] sd 13:0:0:2: [sdf] Assuming drive cache: write through
[354859.934960] sd 13:0:0:2: [sdf] Attached SCSI removable disk
[354909.228027] usb 1-1: new high speed USB device using ehci_hcd and address 10
[354909.362987] usb 1-1: configuration #1 chosen from 1 choice
[355299.875433] __ratelimit: 116 callbacks suppressed
[355299.875439] totem[21668]: segfault at 0 ip (null) sp b207acac error 4 in libgsttag-0.10.so.0.19.2[110000+11000]
[355543.102653] usb 1-1: USB disconnect, address 10
[355543.372040] usb 1-1: new high speed USB device using ehci_hcd and address 11
[355543.520030] hub 1-0:1.0: unable to enumerate USB device on port 1
[355562.832025] usb 1-1: new high speed USB device using ehci_hcd and address 12
[355563.408022] usb 1-1: device not accepting address 12, error -71
[355563.520023] usb 1-1: new high speed USB device using ehci_hcd and address 13
[355563.654672] usb 1-1: configuration #1 chosen from 1 choice
[355563.655289] scsi14 : SCSI emulation for USB Mass Storage devices
[355563.655418] usb-storage: device found at 13
[355563.655421] usb-storage: waiting for device to settle before scanning
[355568.652255] usb-storage: device scan complete
[355568.653836] scsi 14:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
[355568.654458] scsi 14:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
[355568.655081] scsi 14:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ: 0 ANSI: 0
[355568.655705] scsi 14:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0
[355568.656662] sd 14:0:0:0: Attached scsi generic sg5 type 0
[355568.663280] sd 14:0:0:1: Attached scsi generic sg6 type 0
[355568.663451] sd 14:0:0:2: Attached scsi generic sg7 type 0
[355568.663587] sd 14:0:0:3: Attached scsi generic sg8 type 0
[355599.104020] usb 1-1: reset high speed USB device using ehci_hcd and address 13
[355609.352020] usb 1-1: reset high speed USB device using ehci_hcd and address 13
[355623.034362] sd 14:0:0:0: [sdd] Attached SCSI removable disk
[355623.038488] sd 14:0:0:1: [sde] Attached SCSI removable disk
[355623.039300] sd 14:0:0:2: [sdf] Attached SCSI removable disk
[355623.039978] sd 14:0:0:3: [sdg] Attached SCSI removable disk
[355660.112023] usb 1-1: reset high speed USB device using ehci_hcd and address 13
[355670.356025] usb 1-1: reset high speed USB device using ehci_hcd and address 13
[355686.600025] usb 1-1: reset high speed USB device using ehci_hcd and address 13
[355686.848095] usb 1-1: reset high speed USB device using ehci_hcd and address 13
[355697.092024] usb 1-1: reset high speed USB device using ehci_hcd and address 13
[355697.225750] sd 14:0:0:0: Device offlined - not ready after error recovery
[358718.280026] usb 1-9: new high speed USB device using ehci_hcd and address 14
[358718.413696] usb 1-9: configuration #1 chosen from 1 choice
[358718.414007] scsi15 : SCSI emulation for USB Mass Storage devices
[358718.414164] usb-storage: device found at 14
[358718.414166] usb-storage: waiting for device to settle before scanning
[358718.656685] usb 1-1: USB disconnect, address 13
[358718.768028] usb 1-1: new high speed USB device using ehci_hcd and address 15
[358718.902815] usb 1-1: configuration #1 chosen from 1 choice
[358718.903130] scsi16 : SCSI emulation for USB Mass Storage devices
[358718.903290] usb-storage: device found at 15
[358718.903292] usb-storage: waiting for device to settle before scanning
[358723.412272] usb-storage: device scan complete
[358723.413981] scsi 15:0:0:0: Direct-Access     ChipBank SD/MM Reader     4080 PQ: 0 ANSI: 2
[358723.414451] sd 15:0:0:0: Attached scsi generic sg5 type 0
[358723.417087] sd 15:0:0:0: [sdd] 7741440 512-byte logical blocks: (3.96 GB/3.69 GiB)
[358723.417871] sd 15:0:0:0: [sdd] Write Protect is off
[358723.417875] sd 15:0:0:0: [sdd] Mode Sense: 0b 00 00 08
[358723.417878] sd 15:0:0:0: [sdd] Assuming drive cache: write through
[358723.419921] sd 15:0:0:0: [sdd] Assuming drive cache: write through
[358723.419929]  sdd: sdd1 sdd2 < sdd5 >
[358723.424987] sd 15:0:0:0: [sdd] Assuming drive cache: write through
[358723.424993] sd 15:0:0:0: [sdd] Attached SCSI removable disk
[358723.901255] usb-storage: device scan complete
[358723.903817] scsi 16:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
[358723.904351] scsi 16:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
[358723.904964] scsi 16:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ: 0 ANSI: 0
[358723.905599] scsi 16:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0
[358723.906241] sd 16:0:0:0: Attached scsi generic sg6 type 0
[358723.911145] sd 16:0:0:0: [sde] Attached SCSI removable disk
[358723.912361] sd 16:0:0:1: Attached scsi generic sg7 type 0
[358723.912678] sd 16:0:0:2: Attached scsi generic sg8 type 0
[358723.914462] sd 16:0:0:3: Attached scsi generic sg9 type 0
[358723.915726] sd 16:0:0:1: [sdf] Attached SCSI removable disk
[358723.918348] sd 16:0:0:2: [sdg] Attached SCSI removable disk
[358723.921592] sd 16:0:0:3: [sdh] Attached SCSI removable disk
[358726.273898] EXT4-fs (sdd1): recovery complete
[358726.281469] EXT4-fs (sdd1): mounted filesystem with ordered data mode
[358816.037787] sd 15:0:0:0: [sdd] Assuming drive cache: write through
[358816.037796]  sdd:
[358885.432473] ISO 9660 Extensions: Microsoft Joliet Level 3
[358885.432726] ISO 9660 Extensions: RRIP_1991A
[360186.061603] usb 1-9: USB disconnect, address 14
[373456.076064] usb 1-10: new high speed USB device using ehci_hcd and address 16
[373456.209939] usb 1-10: configuration #1 chosen from 1 choice
[373456.210770] scsi17 : SCSI emulation for USB Mass Storage devices
[373456.210888] usb-storage: device found at 16
[373456.210890] usb-storage: waiting for device to settle before scanning
[373461.208252] usb-storage: device scan complete
[373461.209974] scsi 17:0:0:0: Direct-Access     USB Mass Storage Device        PQ: 0 ANSI: 0 CCS
[373461.210460] sd 17:0:0:0: Attached scsi generic sg5 type 0
[373461.216450] sd 17:0:0:0: [sdd] 15544320 512-byte logical blocks: (7.95 GB/7.41 GiB)
[373461.217875] sd 17:0:0:0: [sdd] Write Protect is off
[373461.217881] sd 17:0:0:0: [sdd] Mode Sense: 03 00 00 00
[373461.217884] sd 17:0:0:0: [sdd] Assuming drive cache: write through
[373461.220822] sd 17:0:0:0: [sdd] Assuming drive cache: write through
[373461.220829]  sdd: sdd1
[373461.224957] sd 17:0:0:0: [sdd] Assuming drive cache: write through
[373461.224963] sd 17:0:0:0: [sdd] Attached SCSI removable disk
[373550.119548] ISO 9660 Extensions: Microsoft Joliet Level 3
[373550.119619] ISO 9660 Extensions: RRIP_1991A
[375748.473903] usb 1-10: USB disconnect, address 16
[381330.708033] usb 1-10: new high speed USB device using ehci_hcd and address 17
[381330.842146] usb 1-10: configuration #1 chosen from 1 choice
[381330.842444] scsi18 : SCSI emulation for USB Mass Storage devices
[381330.842605] usb-storage: device found at 17
[381330.842607] usb-storage: waiting for device to settle before scanning
[381335.841215] usb-storage: device scan complete
[381335.843172] scsi 18:0:0:0: Direct-Access     USB Mass Storage Device        PQ: 0 ANSI: 0 CCS
[381335.843659] sd 18:0:0:0: Attached scsi generic sg5 type 0
[381335.848649] sd 18:0:0:0: [sdd] 15544320 512-byte logical blocks: (7.95 GB/7.41 GiB)
[381335.850254] sd 18:0:0:0: [sdd] Write Protect is off
[381335.850260] sd 18:0:0:0: [sdd] Mode Sense: 03 00 00 00
[381335.850263] sd 18:0:0:0: [sdd] Assuming drive cache: write through
[381335.854030] sd 18:0:0:0: [sdd] Assuming drive cache: write through
[381335.854036]  sdd: sdd1
[381335.858030] sd 18:0:0:0: [sdd] Assuming drive cache: write through
[381335.858036] sd 18:0:0:0: [sdd] Attached SCSI removable disk
[383256.993681] sd 18:0:0:0: [sdd] Assuming drive cache: write through
[383256.993688]  sdd:
[383346.740524] ISO 9660 Extensions: Microsoft Joliet Level 3
[383346.740567] ISO 9660 Extensions: RRIP_1991A
[387061.217381] usb 1-10: USB disconnect, address 17
[396712.990900] usb 3-4: USB disconnect, address 2
[483383.871780] isofs_fill_super: bread failed, dev=loop0, iso_blknum=16, block=32
[537995.510714] tvtime[13274]: segfault at 6b0 ip 0804d824 sp bfb0215c error 4 in tvtime[8048000+76000]
[538011.617958] tvtime[13277]: segfault at 6b0 ip 0804d824 sp bfd9101c error 4 in tvtime[8048000+76000]
[538098.786795] tvtime[13284]: segfault at 6b0 ip 0804d824 sp bf80c53c error 4 in tvtime[8048000+76000]

```PS what are all these "illegal requests" I saw?
Chris

---

