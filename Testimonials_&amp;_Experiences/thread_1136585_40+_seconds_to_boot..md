---
title: "40+ seconds to boot."
date: 2009-04-25
forum: Testimonials &amp; Experiences
---

### Post by acidboot3r on 2009-04-25
My computer takes over 40 seconds to go from grub to my desktop. I believe that is out of the norm.

I have a bootlog and a bootchart for you to analyze.


Here is the bootlog, I don't know which one it is exactly, so I'm going to post up everything I think is important:

```

[    0.000000] BIOS EBDA/lowmem at: 0009e800/0009e800
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.28-11-generic (buildd@palmer) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 (Ubuntu 2.6.28-11.42-generic)
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
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009e800 (usable)
[    0.000000]  BIOS-e820: 000000000009e800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003fe90000 (usable)
[    0.000000]  BIOS-e820: 000000003fe90000 - 000000003fee3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003fee3000 - 000000003fef0000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003fef0000 - 000000003ff00000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.5 present.
[    0.000000] last_pfn = 0x3fe90 max_arch_pfn = 0x100000
[    0.000000] Scanning 2 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 0000000000007000 (usable)
[    0.000000]  modified: 0000000000007000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 0000000000091800 (usable)
[    0.000000]  modified: 000000000009e800 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000003fe90000 (usable)
[    0.000000]  modified: 000000003fe90000 - 000000003fee3000 (ACPI NVS)
[    0.000000]  modified: 000000003fee3000 - 000000003fef0000 (ACPI data)
[    0.000000]  modified: 000000003fef0000 - 000000003ff00000 (reserved)
[    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] kernel direct mapping tables up to 373fe000 @ 10000-16000
[    0.000000] RAMDISK: 378be000 - 37fef4ef
[    0.000000] Allocated new RAMDISK: 00881000 - 00fb24ef
[    0.000000] Move RAMDISK from 00000000378be000 - 0000000037fef4ee to 00881000 - 00fb24ee
[    0.000000] ACPI: RSDP 000F96C0, 0024 (r2 DELL  )
[    0.000000] ACPI: XSDT 3FEE3080, 005C (r1 DELL    FX09    42302E31 AWRD        0)
[    0.000000] ACPI: FACP 3FEE7200, 00F4 (r3 DELL    FX09    42302E31 AWRD        0)
[    0.000000] FADT: X_PM1a_EVT_BLK.bit_width (8) does not match PM1_EVT_LEN (4)
[    0.000000] ACPI: DSDT 3FEE3200, 3FFC (r1 DELL   AWRDACPI     1000 MSFT  3000000)
[    0.000000] ACPI: FACS 3FE90000, 0040
[    0.000000] ACPI: HPET 3FEE73C0, 0038 (r1 DELL    FX09    42302E31 AWRD       98)
[    0.000000] ACPI: MCFG 3FEE7400, 003C (r1 DELL    FX09    42302E31 AWRD        0)
[    0.000000] ACPI: SLIC 3FEE7440, 0176 (r1 DELL    FX09    42302E31 AWRD        0)
[    0.000000] ACPI: DMY2 3FEE75C0, 0080 (r1 DELL    FX09    42302E31 AWRD        0)
[    0.000000] ACPI: APIC 3FEE7300, 0084 (r1 DELL    FX09    42302E31 AWRD        0)
[    0.000000] ACPI: SSDT 3FEE7CA0, 0380 (r1  PmRef    CpuPm     3000 INTL 20041203)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 138MB HIGHMEM available.
[    0.000000] 883MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 373fe000
[    0.000000]   low ram: 00000000 - 373fe000
[    0.000000]   bootmap 00012000 - 00018e80
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00373fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 000087c52c]    TEXT DATA BSS ==> [0000100000 - 000087c52c]
[    0.000000]   #4 [000087d000 - 0000881000]    INIT_PG_TABLE ==> [000087d000 - 0000881000]
[    0.000000]   #5 [000009e800 - 0000100000]    BIOS reserved ==> [000009e800 - 0000100000]
[    0.000000]   #6 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
[    0.000000]   #7 [0000881000 - 0000fb24ef]      NEW RAMDISK ==> [0000881000 - 0000fb24ef]
[    0.000000]   #8 [0000012000 - 0000019000]          BOOTMAP ==> [0000012000 - 0000019000]
[    0.000000] found SMP MP-table at [c00f3e30] 000f3e30
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000373fe
[    0.000000]   HighMem  0x000373fe -> 0x0003fe90
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[4] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x00000007
[    0.000000]     0: 0x00000010 -> 0x00000091
[    0.000000]     0: 0x00000100 -> 0x0003fe90
[    0.000000] On node 0 totalpages: 261652
[    0.000000] free_area_init_node: node 0, pgdat c06d0f80, node_mem_map c1000000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3940 pages, LIFO batch:0
[    0.000000]   Normal zone: 1736 pages used for memmap
[    0.000000]   Normal zone: 220470 pages, LIFO batch:31
[    0.000000]   HighMem zone: 278 pages used for memmap
[    0.000000]   HighMem zone: 35196 pages, LIFO batch:7
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 0000000000007000 - 0000000000010000
[    0.000000] PM: Registered nosave memory: 0000000000091000 - 000000000009f000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 3ff00000:a0100000)
[    0.000000] PERCPU: Allocating 45056 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 4, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 259606
[    0.000000] Kernel command line: root=UUID=ec9e7d1b-33dd-4ba8-894b-072c0f8ea699 ro quiet splash
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1994.867 MHz processor.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] allocated 5235520 bytes of page_cgroup
[    0.004000] please try cgroup_disable=memory option if you don't want
[    0.004000] Scanning for low memory corruption every 60 seconds
[    0.004000] Memory: 1016900k/1047104k available (4126k kernel code, 29384k reserved, 2208k data, 532k init, 141896k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xf7bfe000 - 0xff3fe000   ( 120 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xf73fe000   ( 883 MB)
[    0.004000]       .init : 0xc0737000 - 0xc07bc000   ( 532 kB)
[    0.004000]       .data : 0xc0507a6f - 0xc072fe60   (2208 kB)
[    0.004000]       .text : 0xc0100000 - 0xc0507a6f   (4126 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.004000] hpet clockevent registered
[    0.004000] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
[    0.004000] Calibrating delay loop (skipped), value calculated using timer frequency.. 3989.73 BogoMIPS (lpj=7979468)
[    0.004000] Security Framework initialized
[    0.004000] SELinux:  Disabled at boot.
[    0.004000] AppArmor: AppArmor initialized
[    0.004000] Mount-cache hash table entries: 512
[    0.004000] Initializing cgroup subsys ns
[    0.004000] Initializing cgroup subsys cpuacct
[    0.004000] Initializing cgroup subsys memory
[    0.004000] Initializing cgroup subsys freezer
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 2048K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 0
[    0.004000] using mwait in idle threads.
[    0.004000] Checking 'hlt' instruction... OK.
[    0.018408] ACPI: Core revision 20080926
[    0.019938] ACPI: Checking initramfs for custom DSDT
[    0.316407] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.358325] CPU0: Intel(R) Core(TM)2 Duo CPU     E4400  @ 2.00GHz stepping 0d
[    0.360001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 3989.97 BogoMIPS (lpj=7979949)
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 2048K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.444468] CPU1: Intel(R) Core(TM)2 Duo CPU     E4400  @ 2.00GHz stepping 0d
[    0.444483] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.448036] Brought up 2 CPUs
[    0.448039] Total of 2 processors activated (7979.70 BogoMIPS).
[    0.448086] CPU0 attaching sched-domain:
[    0.448089]  domain 0: span 0-1 level MC
[    0.448091]   groups: 0 1
[    0.448097] CPU1 attaching sched-domain:
[    0.448099]  domain 0: span 0-1 level MC
[    0.448102]   groups: 1 0
[    0.448169] net_namespace: 776 bytes
[    0.448169] Booting paravirtualized kernel on bare hardware
[    0.448322] Time:  8:46:59  Date: 04/25/09
[    0.448322] regulator: core version 0.5
[    0.448322] NET: Registered protocol family 16
[    0.448322] EISA bus registered
[    0.448322] ACPI: bus type pci registered
[    0.448322] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.448322] PCI: MCFG area at e0000000 reserved in E820
[    0.448322] PCI: Using MMCONFIG for extended config space
[    0.448322] PCI: Using configuration type 1 for base access
[    0.449103] ACPI: EC: Look up EC in DSDT
[    0.456354] ACPI: Interpreter enabled
[    0.456359] ACPI: (supports S0 S3 S4 S5)
[    0.456378] ACPI: Using IOAPIC for interrupt routing
[    0.460567] ACPI: No dock devices found.
[    0.460578] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.460670] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.460673] pci 0000:00:01.0: PME# disabled
[    0.460738] pci 0000:00:19.0: reg 10 32bit mmio: [0xfdfc0000-0xfdfdffff]
[    0.460745] pci 0000:00:19.0: reg 14 32bit mmio: [0xfdfff000-0xfdffffff]
[    0.460751] pci 0000:00:19.0: reg 18 io port: [0xff00-0xff1f]
[    0.460776] pci 0000:00:19.0: PME# supported from D0 D3hot D3cold
[    0.460780] pci 0000:00:19.0: PME# disabled
[    0.460831] pci 0000:00:1a.0: reg 20 io port: [0xfe00-0xfe1f]
[    0.460893] pci 0000:00:1a.1: reg 20 io port: [0xfd00-0xfd1f]
[    0.460956] pci 0000:00:1a.2: reg 20 io port: [0xfc00-0xfc1f]
[    0.461008] pci 0000:00:1a.7: reg 10 32bit mmio: [0xfdffe000-0xfdffe3ff]
[    0.461046] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.461050] pci 0000:00:1a.7: PME# disabled
[    0.461087] pci 0000:00:1b.0: reg 10 64bit mmio: [0xfdff4000-0xfdff7fff]
[    0.461116] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.461120] pci 0000:00:1b.0: PME# disabled
[    0.461173] pci 0000:00:1d.0: reg 20 io port: [0xfb00-0xfb1f]
[    0.461237] pci 0000:00:1d.1: reg 20 io port: [0xfa00-0xfa1f]
[    0.461300] pci 0000:00:1d.2: reg 20 io port: [0xf900-0xf91f]
[    0.461352] pci 0000:00:1d.7: reg 10 32bit mmio: [0xfdffd000-0xfdffd3ff]
[    0.461390] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.461394] pci 0000:00:1d.7: PME# disabled
[    0.461504] pci 0000:00:1f.0: quirk: region 0400-047f claimed by ICH6 ACPI/GPIO/TCO
[    0.461508] pci 0000:00:1f.0: quirk: region 0480-04bf claimed by ICH6 GPIO
[    0.461549] pci 0000:00:1f.2: reg 10 io port: [0xf800-0xf807]
[    0.461555] pci 0000:00:1f.2: reg 14 io port: [0xf700-0xf703]
[    0.461561] pci 0000:00:1f.2: reg 18 io port: [0xf600-0xf607]
[    0.461567] pci 0000:00:1f.2: reg 1c io port: [0xf500-0xf503]
[    0.461572] pci 0000:00:1f.2: reg 20 io port: [0xf400-0xf40f]
[    0.461578] pci 0000:00:1f.2: reg 24 io port: [0xf300-0xf30f]
[    0.461614] pci 0000:00:1f.3: reg 10 64bit mmio: [0xfdffc000-0xfdffc0ff]
[    0.461628] pci 0000:00:1f.3: reg 20 io port: [0x500-0x51f]
[    0.461671] pci 0000:00:1f.5: reg 10 io port: [0xf100-0xf107]
[    0.461676] pci 0000:00:1f.5: reg 14 io port: [0xf000-0xf003]
[    0.461682] pci 0000:00:1f.5: reg 18 io port: [0xef00-0xef07]
[    0.461688] pci 0000:00:1f.5: reg 1c io port: [0xee00-0xee03]
[    0.461694] pci 0000:00:1f.5: reg 20 io port: [0xed00-0xed0f]
[    0.461700] pci 0000:00:1f.5: reg 24 io port: [0xec00-0xec0f]
[    0.461748] pci 0000:01:00.0: reg 10 64bit mmio: [0xd0000000-0xdfffffff]
[    0.461758] pci 0000:01:00.0: reg 18 64bit mmio: [0xfddf0000-0xfddfffff]
[    0.461764] pci 0000:01:00.0: reg 20 io port: [0xce00-0xceff]
[    0.461773] pci 0000:01:00.0: reg 30 32bit mmio: [0x000000-0x01ffff]
[    0.461782] pci 0000:01:00.0: supports D1 D2
[    0.461823] pci 0000:00:01.0: bridge io port: [0xc000-0xcfff]
[    0.461827] pci 0000:00:01.0: bridge 32bit mmio: [0xfdd00000-0xfddfffff]
[    0.461832] pci 0000:00:01.0: bridge 64bit mmio pref: [0xd0000000-0xdfffffff]
[    0.461880] pci 0000:00:1e.0: transparent bridge
[    0.461884] pci 0000:00:1e.0: bridge io port: [0xd000-0xdfff]
[    0.461888] pci 0000:00:1e.0: bridge 32bit mmio: [0xfdc00000-0xfdcfffff]
[    0.461894] pci 0000:00:1e.0: bridge 64bit mmio pref: [0xfde00000-0xfdefffff]
[    0.461904] bus 00 -> node 0
[    0.461911] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.462175] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[    0.477443] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 7 9 10 11 12 14 15)
[    0.477565] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[    0.477686] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 *9 10 11 12 14 15)
[    0.477805] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[    0.477925] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 *10 11 12 14 15)
[    0.478044] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[    0.478164] ACPI: PCI Interrupt Link [LNK0] (IRQs *3 4 5 7 9 10 11 12 14 15)
[    0.478283] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 *4 5 7 9 10 11 12 14 15)
[    0.478492] ACPI: WMI: Mapper loaded
[    0.478528] SCSI subsystem initialized
[    0.478528] libata version 3.00 loaded.
[    0.478528] usbcore: registered new interface driver usbfs
[    0.478528] usbcore: registered new interface driver hub
[    0.478528] usbcore: registered new device driver usb
[    0.478528] PCI: Using ACPI for IRQ routing
[    0.484013] Bluetooth: Core ver 2.13
[    0.484035] NET: Registered protocol family 31
[    0.484035] Bluetooth: HCI device and connection manager initialized
[    0.484035] Bluetooth: HCI socket layer initialized
[    0.484035] NET: Registered protocol family 8
[    0.484035] NET: Registered protocol family 20
[    0.484052] NetLabel: Initializing
[    0.484054] NetLabel:  domain hash size = 128
[    0.484057] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.484085] NetLabel:  unlabeled traffic allowed by default
[    0.484109] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.484114] hpet0: 4 comparators, 64-bit 14.318180 MHz counter
[    0.488083] AppArmor: AppArmor Filesystem Enabled
[    0.496033] pnp: PnP ACPI init
[    0.496046] ACPI: bus type pnp registered
[    0.498007] pnp: PnP ACPI: found 12 devices
[    0.498009] ACPI: ACPI bus type pnp unregistered
[    0.498012] PnPBIOS: Disabled by ACPI PNP
[    0.498021] system 00:01: ioport range 0x4d0-0x4d1 has been reserved
[    0.498024] system 00:01: ioport range 0x800-0x87f has been reserved
[    0.498026] system 00:01: ioport range 0x290-0x297 has been reserved
[    0.498029] system 00:01: ioport range 0x880-0x88f has been reserved
[    0.498037] system 00:08: ioport range 0x400-0x4bf could not be reserved
[    0.498043] system 00:0a: iomem range 0xe0000000-0xefffffff has been reserved
[    0.498049] system 00:0b: iomem range 0xf0000-0xfffff could not be reserved
[    0.498052] system 00:0b: iomem range 0x3ff00000-0x3fffffff has been reserved
[    0.498054] system 00:0b: iomem range 0xfed00000-0xfed000ff has been reserved
[    0.498057] system 00:0b: iomem range 0x3fe90000-0x3fefffff could not be reserved
[    0.498060] system 00:0b: iomem range 0x0-0x9ffff could not be reserved
[    0.498062] system 00:0b: iomem range 0x100000-0x3fe8ffff could not be reserved
[    0.498065] system 00:0b: iomem range 0xfec00000-0xfec00fff has been reserved
[    0.498068] system 00:0b: iomem range 0xfed14000-0xfed1dfff has been reserved
[    0.498070] system 00:0b: iomem range 0xfed20000-0xfed9ffff has been reserved
[    0.498073] system 00:0b: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.498076] system 00:0b: iomem range 0xffb00000-0xffb7ffff has been reserved
[    0.498078] system 00:0b: iomem range 0xfff00000-0xffffffff has been reserved
[    0.498081] system 00:0b: iomem range 0xe0000-0xeffff has been reserved
[    0.500544] Switched to high resolution mode on CPU 1
[    0.504030] Switched to high resolution mode on CPU 0
[    0.532762] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.532765] pci 0000:00:01.0:   IO window: 0xc000-0xcfff
[    0.532769] pci 0000:00:01.0:   MEM window: 0xfdd00000-0xfddfffff
[    0.532772] pci 0000:00:01.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
[    0.532777] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:02
[    0.532780] pci 0000:00:1e.0:   IO window: 0xd000-0xdfff
[    0.532785] pci 0000:00:1e.0:   MEM window: 0xfdc00000-0xfdcfffff
[    0.532789] pci 0000:00:1e.0:   PREFETCH window: 0x000000fde00000-0x000000fdefffff
[    0.532801] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.532805] pci 0000:00:01.0: setting latency timer to 64
[    0.532811] pci 0000:00:1e.0: setting latency timer to 64
[    0.532815] bus: 00 index 0 io port: [0x00-0xffff]
[    0.532817] bus: 00 index 1 mmio: [0x000000-0xffffffff]
[    0.532819] bus: 01 index 0 io port: [0xc000-0xcfff]
[    0.532821] bus: 01 index 1 mmio: [0xfdd00000-0xfddfffff]
[    0.532823] bus: 01 index 2 mmio: [0xd0000000-0xdfffffff]
[    0.532825] bus: 01 index 3 mmio: [0x0-0x0]
[    0.532827] bus: 02 index 0 io port: [0xd000-0xdfff]
[    0.532829] bus: 02 index 1 mmio: [0xfdc00000-0xfdcfffff]
[    0.532831] bus: 02 index 2 mmio: [0xfde00000-0xfdefffff]
[    0.532833] bus: 02 index 3 io port: [0x00-0xffff]
[    0.532835] bus: 02 index 4 mmio: [0x000000-0xffffffff]
[    0.532842] NET: Registered protocol family 2
[    0.548102] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.548354] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.548698] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.548874] TCP: Hash tables configured (established 131072 bind 65536)
[    0.548876] TCP reno registered
[    0.556134] NET: Registered protocol family 1
[    0.556267] checking if image is initramfs... it is
[    1.571255] Freeing initrd memory: 7365k freed
[    1.571468] cpufreq: No nForce2 chipset.
[    1.571603] audit: initializing netlink socket (disabled)
[    1.571625] type=2000 audit(1240649219.568:1): initialized
[    1.578614] highmem bounce pool size: 64 pages
[    1.578619] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.579916] VFS: Disk quotas dquot_6.5.1
[    1.579972] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.580554] fuse init (API version 7.10)
[    1.580635] msgmni has been set to 1724
[    1.580803] alg: No test for stdrng (krng)
[    1.580815] io scheduler noop registered
[    1.580817] io scheduler anticipatory registered
[    1.580819] io scheduler deadline registered
[    1.580831] io scheduler cfq registered (default)
[    1.580964] pci 0000:01:00.0: Boot video device
[    1.582808] pcieport-driver 0000:00:01.0: setting latency timer to 64
[    1.582844] pcieport-driver 0000:00:01.0: found MSI capability
[    1.582868] pcieport-driver 0000:00:01.0: irq 2303 for MSI/MSI-X
[    1.582877] pci_express 0000:00:01.0:pcie00: allocate port service
[    1.582891] pci_express 0000:00:01.0:pcie03: allocate port service
[    1.582948] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.582957] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.583091] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.583094] ACPI: Power Button (FF) [PWRF]
[    1.583137] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    1.583140] ACPI: Power Button (CM) [PWRB]
[    1.583190] fan PNP0C0B:00: registered as cooling_device0
[    1.583195] ACPI: Fan [FAN] (on)
[    1.583589] ACPI: SSDT 3FEE7680, 026C (r1  PmRef  Cpu0Ist     3000 INTL 20041203)
[    1.583820] processor ACPI_CPU:00: registered as cooling_device1
[    1.583998] ACPI: SSDT 3FEE7B40, 0152 (r1  PmRef  Cpu1Ist     3000 INTL 20041203)
[    1.584212] processor ACPI_CPU:01: registered as cooling_device2
[    1.586076] thermal LNXTHERM:01: registered as thermal_zone0
[    1.586336] ACPI: Thermal Zone [THRM] (40 C)
[    1.586384] isapnp: Scanning for PnP cards...
[    1.939338] isapnp: No Plug & Play device found
[    1.948767] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.949770] brd: module loaded
[    1.950066] loop: module loaded
[    1.950131] Fixed MDIO Bus: probed
[    1.950136] PPP generic driver version 2.4.2
[    1.950188] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    1.950216] Driver 'sd' needs updating - please use bus_type methods
[    1.950225] Driver 'sr' needs updating - please use bus_type methods
[    1.950292] ata_piix 0000:00:1f.2: version 2.12
[    1.950305] ata_piix 0000:00:1f.2: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.950309] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    1.950350] ata_piix 0000:00:1f.2: setting latency timer to 64
[    1.950401] scsi0 : ata_piix
[    1.950470] scsi1 : ata_piix
[    1.951114] ata1: SATA max UDMA/133 cmd 0xf800 ctl 0xf700 bmdma 0xf400 irq 19
[    1.951119] ata2: SATA max UDMA/133 cmd 0xf600 ctl 0xf500 bmdma 0xf408 irq 19
[    2.744077] ata1.00: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.744090] ata1.01: SATA link down (SStatus 0 SControl 300)
[    2.752324] ata1.00: ATA-7: WDC WD2500JS-75NCB3, 10.02E04, max UDMA/133
[    2.752328] ata1.00: 488281250 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    2.760360] ata1.00: configured for UDMA/133
[    3.556074] ata2.00: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    3.556088] ata2.01: SATA link down (SStatus 0 SControl 300)
[    3.564207] ata2.00: ATAPI: HL-DT-ST DVD+/-RW GSA-H73N, B103, max UDMA/100
[    3.580236] ata2.00: configured for UDMA/100
[    3.580739] scsi 0:0:0:0: Direct-Access     ATA      WDC WD2500JS-75N 10.0 PQ: 0 ANSI: 5
[    3.580830] sd 0:0:0:0: [sda] 488281250 512-byte hardware sectors: (250 GB/232 GiB)
[    3.580845] sd 0:0:0:0: [sda] Write Protect is off
[    3.580848] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.580872] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.580930] sd 0:0:0:0: [sda] 488281250 512-byte hardware sectors: (250 GB/232 GiB)
[    3.580944] sd 0:0:0:0: [sda] Write Protect is off
[    3.580946] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.580970] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.580973]  sda: sda1 sda2 sda3 < sda5 sda6 >
[    3.633557] sd 0:0:0:0: [sda] Attached SCSI disk
[    3.633595] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    3.635245] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVD+-RW GSA-H73N B103 PQ: 0 ANSI: 5
[    3.639849] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[    3.639853] Uniform CD-ROM driver Revision: 3.20
[    3.639987] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    3.640028] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    3.640045] ata_piix 0000:00:1f.5: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    3.640048] ata_piix 0000:00:1f.5: MAP [ P0 -- P1 -- ]
[    3.640084] ata_piix 0000:00:1f.5: setting latency timer to 64
[    3.640126] scsi2 : ata_piix
[    3.640179] scsi3 : ata_piix
[    3.640468] ata3: SATA max UDMA/133 cmd 0xf100 ctl 0xf000 bmdma 0xed00 irq 19
[    3.640472] ata4: SATA max UDMA/133 cmd 0xef00 ctl 0xee00 bmdma 0xed08 irq 19
[    3.970639] ata3: SATA link down (SStatus 0 SControl 300)
[    4.298639] ata4: SATA link down (SStatus 0 SControl 300)
[    4.299253] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    4.299271] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    4.299288] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    4.299291] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    4.299343] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    4.303261] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    4.303275] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xfdffe000
[    4.316029] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    4.316123] usb usb1: configuration #1 chosen from 1 choice
[    4.316167] hub 1-0:1.0: USB hub found
[    4.316183] hub 1-0:1.0: 6 ports detected
[    4.316282] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    4.316292] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    4.316295] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    4.316333] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    4.320228] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    4.320240] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfdffd000
[    4.332029] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    4.332121] usb usb2: configuration #1 chosen from 1 choice
[    4.332160] hub 2-0:1.0: USB hub found
[    4.332169] hub 2-0:1.0: 6 ports detected
[    4.332264] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    4.332279] uhci_hcd: USB Universal Host Controller Interface driver
[    4.332299] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    4.332305] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    4.332308] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    4.332351] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    4.332379] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000fe00
[    4.332448] usb usb3: configuration #1 chosen from 1 choice
[    4.332473] hub 3-0:1.0: USB hub found
[    4.332479] hub 3-0:1.0: 2 ports detected
[    4.332561] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    4.332567] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    4.332570] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    4.332608] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    4.332635] uhci_hcd 0000:00:1a.1: irq 21, io base 0x0000fd00
[    4.332701] usb usb4: configuration #1 chosen from 1 choice
[    4.332724] hub 4-0:1.0: USB hub found
[    4.332730] hub 4-0:1.0: 2 ports detected
[    4.332803] uhci_hcd 0000:00:1a.2: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    4.332808] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[    4.332811] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    4.332852] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
[    4.332872] uhci_hcd 0000:00:1a.2: irq 19, io base 0x0000fc00
[    4.332938] usb usb5: configuration #1 chosen from 1 choice
[    4.332963] hub 5-0:1.0: USB hub found
[    4.332968] hub 5-0:1.0: 2 ports detected
[    4.333045] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    4.333050] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    4.333053] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    4.333092] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
[    4.333112] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000fb00
[    4.333181] usb usb6: configuration #1 chosen from 1 choice
[    4.333205] hub 6-0:1.0: USB hub found
[    4.333210] hub 6-0:1.0: 2 ports detected
[    4.333286] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    4.333292] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    4.333295] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    4.333335] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
[    4.333356] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000fa00
[    4.333422] usb usb7: configuration #1 chosen from 1 choice
[    4.333447] hub 7-0:1.0: USB hub found
[    4.333452] hub 7-0:1.0: 2 ports detected
[    4.333532] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    4.333538] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    4.333541] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    4.333581] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
[    4.333602] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000f900
[    4.333666] usb usb8: configuration #1 chosen from 1 choice
[    4.333690] hub 8-0:1.0: USB hub found
[    4.333695] hub 8-0:1.0: 2 ports detected
[    4.333819] usbcore: registered new interface driver libusual
[    4.333847] usbcore: registered new interface driver usbserial
[    4.333857] USB Serial support registered for generic
[    4.333873] usbcore: registered new interface driver usbserial_generic
[    4.333875] usbserial: USB Serial Driver core
[    4.333925] PNP: No PS/2 controller found. Probing ports directly.
[    4.334211] serio: i8042 KBD port at 0x60,0x64 irq 1
[    4.334215] serio: i8042 AUX port at 0x60,0x64 irq 12
[    4.336576] mice: PS/2 mouse device common for all mice
[    4.348604] rtc_cmos 00:04: RTC can wake from S4
[    4.348654] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    4.348688] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
[    4.348742] device-mapper: uevent: version 1.0.3
[    4.348820] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
[    4.348886] device-mapper: multipath: version 1.0.5 loaded
[    4.348888] device-mapper: multipath round-robin: version 1.0.0 loaded
[    4.348960] EISA: Probing bus 0 at eisa.0
[    4.348986] EISA: Detected 0 cards.
[    4.349030] cpuidle: using governor ladder
[    4.349032] cpuidle: using governor menu
[    4.349518] TCP cubic registered
[    4.349610] NET: Registered protocol family 10
[    4.350030] lo: Disabled Privacy Extensions
[    4.350354] NET: Registered protocol family 17
[    4.350369] Bluetooth: L2CAP ver 2.11
[    4.350371] Bluetooth: L2CAP socket layer initialized
[    4.350374] Bluetooth: SCO (Voice Link) ver 0.6
[    4.350376] Bluetooth: SCO socket layer initialized
[    4.350397] Bluetooth: RFCOMM socket layer initialized
[    4.350402] Bluetooth: RFCOMM TTY layer initialized
[    4.350404] Bluetooth: RFCOMM ver 1.10
[    4.350991] Using IPI No-Shortcut mode
[    4.351057] registered taskstats version 1
[    4.351166]   Magic number: 5:947:776
[    4.351224] rtc_cmos 00:04: setting system clock to 2009-04-25 08:47:03 UTC (1240649223)
[    4.351227] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    4.351228] EDD information not available.
[    4.351461] Freeing unused kernel memory: 532k freed
[    4.351581] Write protecting the kernel text: 4128k
[    4.351625] Write protecting the kernel read-only data: 1532k
[    4.511200] e1000e: Intel(R) PRO/1000 Network Driver - 0.3.3.3-k6
[    4.511203] e1000e: Copyright (c) 1999-2008 Intel Corporation.
[    4.511260] e1000e 0000:00:19.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    4.511270] e1000e 0000:00:19.0: setting latency timer to 64
[    4.511387] e1000e 0000:00:19.0: irq 2302 for MSI/MSI-X
[    4.598598] 0000:00:19.0: eth0: (PCI Express:2.5GB/s:Width x1) 00:1a:a0:93:ad:6a
[    4.598601] 0000:00:19.0: eth0: Intel(R) PRO/10/100 Network Connection
[    4.598628] 0000:00:19.0: eth0: MAC: 6, PHY: 7, PBA No: ffffff-0ff
[    4.600375] FDC 0 is a post-1991 82077
[    4.740522] usb 1-4: new high speed USB device using ehci_hcd and address 3
[    5.028538] usb 1-4: configuration #1 chosen from 1 choice
[    5.228159] PM: Starting manual resume from disk
[    5.228162] PM: Resume from partition 8:6
[    5.228164] PM: Checking hibernation image.
[    5.228299] PM: Resume from disk failed.
[    5.249790] kjournald starting.  Commit interval 5 seconds
[    5.249809] EXT3-fs: mounted filesystem with ordered data mode.
[    5.308065] usb 2-5: new high speed USB device using ehci_hcd and address 2
[    5.503106] usb 2-5: configuration #1 chosen from 1 choice
[    5.740040] usb 4-1: new full speed USB device using uhci_hcd and address 2
[    5.781350] Initializing USB Mass Storage driver...
[    5.781471] scsi4 : SCSI emulation for USB Mass Storage devices
[    5.781537] usb-storage: device found at 2
[    5.781540] usb-storage: waiting for device to settle before scanning
[    5.781547] usbcore: registered new interface driver usb-storage
[    5.781550] USB Mass Storage support registered.
[    5.909868] usb 4-1: configuration #1 chosen from 1 choice
[    5.913118] scsi5 : SCSI emulation for USB Mass Storage devices
[    5.913286] usb-storage: device found at 2
[    5.913288] usb-storage: waiting for device to settle before scanning
[    6.152529] usb 5-1: new low speed USB device using uhci_hcd and address 2
[    6.327146] usb 5-1: configuration #1 chosen from 1 choice
[    6.568040] usb 5-2: new full speed USB device using uhci_hcd and address 3
[    6.798172] usb 5-2: configuration #1 chosen from 1 choice
[    6.801113] hub 5-2:1.0: USB hub found
[    6.803074] hub 5-2:1.0: 4 ports detected
[    7.089112] usb 5-2.2: new low speed USB device using uhci_hcd and address 4
[    7.220175] usb 5-2.2: configuration #1 chosen from 1 choice
[    7.297109] usb 5-2.3: new full speed USB device using uhci_hcd and address 5
[    7.422188] usb 5-2.3: configuration #1 chosen from 1 choice
[    9.354555] udev: starting version 141
[    9.465277] Linux agpgart interface v0.103
[    9.581539] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[    9.615387] [fglrx] Maximum main memory to use for locked dma buffers: 919 MBytes.
[    9.615476] [fglrx]   vendor: 1002 device: 94c3 count: 1
[    9.615793] [fglrx] ioport: bar 4, base 0xce00, size: 0x100
[    9.615809] pci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    9.615816] pci 0000:01:00.0: setting latency timer to 64
[    9.617068] [fglrx] Driver built-in PAT support is enabled successfully
[    9.617733] [fglrx] module loaded - fglrx 8.60.3 [Apr  1 2009] with 1 minors
[    9.991804] Linux video capture interface: v2.00
[   10.003972] yealink: invalid payload size 64, expected 16
[   10.004027] input: Yealink usb-p1k as /devices/pci0000:00/0000:00:1a.2/usb5/5-2/5-2.3/5-2.3:1.3/input/input3
[   10.010458] usbcore: registered new interface driver yealink
[   10.010480] yealink: yld-20051230:Yealink phone driver
[   10.018145] usblp0: USB Bidirectional printer dev 2 if 0 alt 0 proto 2 vid 0x04F9 pid 0x01AB
[   10.018171] usbcore: registered new interface driver usblp
[   10.018350] usbcore: registered new interface driver hiddev
[   10.022276] yealink: unexpected response fd
[   10.033651] input: Dell Dell USB Keyboard as /devices/pci0000:00/0000:00:1a.2/usb5/5-1/5-1:1.0/input/input4
[   10.033870] generic-usb 0003:413C:2003.0001: input,hidraw0: USB HID v1.10 Keyboard [Dell Dell USB Keyboard] on usb-0000:00:1a.2-1/input0
[   10.036193] iTCO_vendor_support: vendor-support=0
[   10.038281] yealink: unexpected response fd
[   10.046593] input: USB Optical Mouse as /devices/pci0000:00/0000:00:1a.2/usb5/5-2/5-2.2/5-2.2:1.0/input/input5
[   10.048655] generic-usb 0003:0461:4D15.0002: input,hidraw1: USB HID v1.11 Mouse [USB Optical Mouse] on usb-0000:00:1a.2-2.2/input0
[   10.048683] usbcore: registered new interface driver usbhid
[   10.048704] usbhid: v2.6:USB HID core driver
[   10.054282] yealink: unexpected response fd
[   10.056864] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05
[   10.057156] iTCO_wdt: Found a ICH9R TCO device (Version=2, TCOBASE=0x0460)
[   10.057271] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   10.070290] yealink: unexpected response fd
[   10.086288] yealink: unexpected response fd
[   10.102284] yealink: unexpected response fd
[   10.118284] yealink: unexpected response fd
[   10.134289] yealink: unexpected response fd
[   10.150286] yealink: unexpected response fd
[   10.166290] yealink: unexpected response fd
[   10.182294] yealink: unexpected response fd
[   10.198290] yealink: unexpected response fd
[   10.214290] yealink: unexpected response fd
[   10.230291] yealink: unexpected response fd
[   10.246294] yealink: unexpected response fd
[   10.262293] yealink: unexpected response fd
[   10.278293] yealink: unexpected response fd
[   10.294296] yealink: unexpected response fd
[   10.310297] yealink: unexpected response fd
[   10.326301] yealink: unexpected response fd
[   10.342300] yealink: unexpected response fd
[   10.358307] yealink: unexpected response fd
[   10.371674] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   10.374307] yealink: unexpected response fd
[   10.376160] input: PC Speaker as /devices/platform/pcspkr/input/input6
[   10.390307] yealink: unexpected response fd
[   10.406309] yealink: unexpected response fd
[   10.422307] yealink: unexpected response fd
[   10.431507] uvcvideo: Found UVC 1.00 device <unnamed> (046d:08ca)
[   10.436093] input: UVC Camera (046d:08ca) as /devices/pci0000:00/0000:00:1a.7/usb1/1-4/1-4:1.0/input/input7
[   10.438309] yealink: unexpected response fd
[   10.440179] usbcore: registered new interface driver uvcvideo
[   10.440210] USB Video Class driver (v0.1.0)
[   10.454310] yealink: unexpected response fd
[   10.470309] yealink: unexpected response fd
[   10.486313] yealink: unexpected response fd
[   10.502314] yealink: unexpected response fd
[   10.518309] yealink: unexpected response fd
[   10.534314] yealink: unexpected response fd
[   10.550316] yealink: unexpected response fd
[   10.566318] yealink: unexpected response fd
[   10.571088] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   10.571190] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   10.582316] yealink: unexpected response fd
[   10.598317] yealink: unexpected response fd
[   10.603902] usbcore: registered new interface driver snd-usb-audio
[   10.614321] yealink: unexpected response fd
[   10.630320] yealink: unexpected response fd
[   10.646323] yealink: unexpected response fd
[   10.662324] yealink: unexpected response fd
[   10.678323] yealink: unexpected response fd
[   10.694325] yealink: unexpected response fd
[   10.710327] yealink: unexpected response fd
[   10.726327] yealink: unexpected response fd
[   10.742325] yealink: unexpected response fd
[   10.758329] yealink: unexpected response fd
[   10.774328] yealink: unexpected response fd
[   10.786268] usb-storage: device scan complete
[   10.790267] scsi 4:0:0:0: Direct-Access     TEAC     USB   HS-CF Card 4.08 PQ: 0 ANSI: 0
[   10.790329] yealink: unexpected response fd
[   10.796031] scsi 4:0:0:1: Direct-Access     TEAC     USB   HS-xD/SM   4.08 PQ: 0 ANSI: 0
[   10.799521] scsi 4:0:0:2: Direct-Access     TEAC     USB   HS-MS Card 4.08 PQ: 0 ANSI: 0
[   10.802764] scsi 4:0:0:3: Direct-Access     TEAC     USB   HS-SD Card 4.08 PQ: 0 ANSI: 0
[   10.806334] yealink: unexpected response fd
[   10.807242] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[   10.807326] sd 4:0:0:0: Attached scsi generic sg2 type 0
[   10.812587] sd 4:0:0:1: [sdc] Attached SCSI removable disk
[   10.812656] sd 4:0:0:1: Attached scsi generic sg3 type 0
[   10.818281] sd 4:0:0:2: [sdd] Attached SCSI removable disk
[   10.818357] sd 4:0:0:2: Attached scsi generic sg4 type 0
[   10.821035] lp: driver loaded but no devices found
[   10.822332] yealink: unexpected response fd
[   10.826735] sd 4:0:0:3: [sde] Attached SCSI removable disk
[   10.826807] sd 4:0:0:3: Attached scsi generic sg5 type 0
[   10.838334] yealink: unexpected response fd
[   10.854334] yealink: unexpected response fd
[   10.870338] yealink: unexpected response fd
[   10.886338] yealink: unexpected response fd
[   10.902339] yealink: unexpected response fd
[   10.909143] Adding 578300k swap on /dev/sda6.  Priority:-1 extents:1 across:578300k
[   10.914138] usb-storage: device scan complete
[   10.918341] yealink: unexpected response fd
[   10.921153] scsi 5:0:0:0: Direct-Access     Brother  MFC-240C         1.00 PQ: 0 ANSI: 2
[   10.934341] yealink: unexpected response fd
[   10.950343] yealink: unexpected response fd
[   10.966343] yealink: unexpected response fd
[   10.971273] sd 5:0:0:0: [sdf] Attached SCSI removable disk
[   10.971350] sd 5:0:0:0: Attached scsi generic sg6 type 0
[   10.982345] yealink: unexpected response fd
[   10.998344] yealink: unexpected response fd
[   11.014344] yealink: unexpected response fd
[   11.030344] yealink: unexpected response fd
[   11.046346] yealink: unexpected response fd
[   11.062351] yealink: unexpected response fd
[   11.078349] yealink: unexpected response fd
[   11.094349] yealink: unexpected response fd
[   11.110351] yealink: unexpected response fd
[   11.126350] yealink: unexpected response fd
[   11.142353] yealink: unexpected response fd
[   11.158353] yealink: unexpected response fd
[   11.174355] yealink: unexpected response fd
[   11.190355] yealink: unexpected response fd
[   11.206356] yealink: unexpected response fd
[   11.222358] yealink: unexpected response fd
[   11.238364] yealink: unexpected response fd
[   11.254359] yealink: unexpected response fd
[   11.270360] yealink: unexpected response fd
[   11.286361] yealink: unexpected response fd
[   11.302362] yealink: unexpected response fd
[   11.318362] yealink: unexpected response fd
[   11.334364] yealink: unexpected response fd
[   11.350366] yealink: unexpected response fd
[   11.366366] yealink: unexpected response fd
[   11.382367] yealink: unexpected response fd
[   11.398369] yealink: unexpected response fd
[   11.414369] yealink: unexpected response fd
[   11.430371] yealink: unexpected response fd
[   11.446373] yealink: unexpected response fd
[   11.451280] EXT3 FS on sda5, internal journal
[   11.462377] yealink: unexpected response fd
[   11.478376] yealink: unexpected response fd
[   11.494380] yealink: unexpected response fd
[   11.510378] yealink: unexpected response fd
[   11.526380] yealink: unexpected response fd
[   11.542379] yealink: unexpected response fd
[   11.558380] yealink: unexpected response fd
[   11.574383] yealink: unexpected response fd
[   11.590384] yealink: unexpected response fd
[   11.606385] yealink: unexpected response fd
[   11.622383] yealink: unexpected response fd
[   11.638384] yealink: unexpected response fd
[   11.654385] yealink: unexpected response fd
[   11.670386] yealink: unexpected response fd
[   11.686387] yealink: unexpected response fd
[   11.702388] yealink: unexpected response fd
[   11.718389] yealink: unexpected response fd
[   11.734390] yealink: unexpected response fd
[   11.750391] yealink: unexpected response fd
[   11.766392] yealink: unexpected response fd
[   11.782394] yealink: unexpected response fd
[   11.798394] yealink: unexpected response fd
[   11.814396] yealink: unexpected response fd
[   11.830397] yealink: unexpected response fd
[   11.846397] yealink: unexpected response fd
[   11.862399] yealink: unexpected response fd
[   11.878400] yealink: unexpected response fd
[   11.894400] yealink: unexpected response fd
[   11.910402] yealink: unexpected response fd
[   11.926403] yealink: unexpected response fd
[   11.942404] yealink: unexpected response fd
[   11.958405] yealink: unexpected response fd
[   11.974406] yealink: unexpected response fd
[   11.990407] yealink: unexpected response fd
[   12.006408] yealink: unexpected response fd
[   12.022409] yealink: unexpected response fd
[   12.038410] yealink: unexpected response fd
[   12.054411] yealink: unexpected response fd
[   12.070414] yealink: unexpected response fd
[   12.086414] yealink: unexpected response fd
[   12.102417] yealink: unexpected response fd
[   12.118421] yealink: unexpected response fd
[   12.134419] yealink: unexpected response fd
[   12.150420] yealink: unexpected response fd
[   12.166421] yealink: unexpected response fd
[   12.182422] yealink: unexpected response fd
[   12.198425] yealink: unexpected response fd
[   12.214425] yealink: unexpected response fd
[   12.230426] yealink: unexpected response fd
[   12.246426] yealink: unexpected response fd
[   12.262429] yealink: unexpected response fd
[   12.278429] yealink: unexpected response fd
[   12.294433] yealink: unexpected response fd
[   12.310429] yealink: unexpected response fd
[   12.326428] yealink: unexpected response fd
[   12.342432] yealink: unexpected response fd
[   12.351705] type=1505 audit(1240645631.496:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2195
[   12.358438] yealink: unexpected response fd
[   12.374433] yealink: unexpected response fd
[   12.390433] yealink: unexpected response fd
[   12.396011] type=1505 audit(1240645631.544:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2199
[   12.396105] type=1505 audit(1240645631.544:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2199
[   12.396143] type=1505 audit(1240645631.544:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2199
[   12.396178] type=1505 audit(1240645631.544:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2199
[   12.406441] yealink: unexpected response fd
[   12.422437] yealink: unexpected response fd
[   12.438437] yealink: unexpected response fd
[   12.454441] yealink: unexpected response fd
[   12.470438] yealink: unexpected response fd
[   12.486438] yealink: unexpected response fd
[   12.502440] yealink: unexpected response fd
[   12.518445] yealink: unexpected response fd
[   12.519967] type=1505 audit(1240645631.664:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2204
[   12.520141] type=1505 audit(1240645631.668:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2204
[   12.534450] yealink: unexpected response fd
[   12.546553] type=1505 audit(1240645631.692:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2208
[   12.550451] yealink: unexpected response fd
[   12.566450] yealink: unexpected response fd
[   12.582453] yealink: unexpected response fd
[   12.598448] yealink: unexpected response fd
[   12.614452] yealink: unexpected response fd
[   12.630454] yealink: unexpected response fd
[   12.646454] yealink: unexpected response fd
[   12.662456] yealink: unexpected response fd
[   12.678457] yealink: unexpected response fd
[   12.694458] yealink: unexpected response fd
[   12.710461] yealink: unexpected response fd
[   12.726459] yealink: unexpected response fd
[   12.742458] yealink: unexpected response fd
[   12.758464] yealink: unexpected response fd
[   12.774462] yealink: unexpected response fd
[   12.790469] yealink: unexpected response fd
[   12.806471] yealink: unexpected response fd
[   12.822463] yealink: unexpected response fd
[   12.838471] yealink: unexpected response fd
[   12.854471] yealink: unexpected response fd
[   12.870470] yealink: unexpected response fd
[   12.886473] yealink: unexpected response fd
[   12.902470] yealink: unexpected response fd
[   12.918473] yealink: unexpected response fd
[   12.934477] yealink: unexpected response fd
[   12.950476] yealink: unexpected response fd
[   12.966476] yealink: unexpected response fd
[   12.982475] yealink: unexpected response fd
[   12.998477] yealink: unexpected response fd
[   13.014477] yealink: unexpected response fd
[   13.030479] yealink: unexpected response fd
[   13.046479] yealink: unexpected response fd
[   13.062479] yealink: unexpected response fd
[   13.078483] yealink: unexpected response fd
[   13.094486] yealink: unexpected response fd
[   13.110481] yealink: unexpected response fd
[   13.126488] yealink: unexpected response fd
[   13.142488] yealink: unexpected response fd
[   13.158488] yealink: unexpected response fd
[   13.174488] yealink: unexpected response fd
[   13.190489] yealink: unexpected response fd
[   13.206490] yealink: unexpected response fd
[   13.222491] yealink: unexpected response fd
[   13.238492] yealink: unexpected response fd
[   13.254493] yealink: unexpected response fd
[   13.270495] yealink: unexpected response fd
[   13.286492] yealink: unexpected response fd
[   13.302530] yealink: unexpected response fd
[   13.318493] yealink: unexpected response fd
[   13.334494] yealink: unexpected response fd
[   13.350497] yealink: unexpected response fd
[   13.366498] yealink: unexpected response fd
[   13.382503] yealink: unexpected response fd
[   13.398502] yealink: unexpected response fd
[   13.414504] yealink: unexpected response fd
[   13.430502] yealink: unexpected response fd
[   13.446503] yealink: unexpected response fd
[   13.462504] yealink: unexpected response fd
[   13.478504] yealink: unexpected response fd
[   13.494507] yealink: unexpected response fd
[   13.510515] yealink: unexpected response fd
[   13.526512] yealink: unexpected response fd
[   13.542511] yealink: unexpected response fd
[   13.558514] yealink: unexpected response fd
[   13.574519] yealink: unexpected response fd
[   13.590518] yealink: unexpected response fd
[   13.606515] yealink: unexpected response fd
[   13.622518] yealink: unexpected response fd
[   13.638521] yealink: unexpected response fd
[   13.654521] yealink: unexpected response fd
[   13.670524] yealink: unexpected response fd
[   13.686524] yealink: unexpected response fd
[   13.702524] yealink: unexpected response fd
[   13.718526] yealink: unexpected response fd
[   13.734530] yealink: unexpected response fd
[   13.750526] yealink: unexpected response fd
[   13.766525] yealink: unexpected response fd
[   13.782529] yealink: unexpected response fd
[   13.798534] yealink: unexpected response fd
[   13.814532] yealink: unexpected response fd
[   13.830530] yealink: unexpected response fd
[   13.846538] yealink: unexpected response fd
[   13.862539] yealink: unexpected response fd
[   13.878539] yealink: unexpected response fd
[   13.894537] yealink: unexpected response fd
[   13.910539] yealink: unexpected response fd
[   13.926539] yealink: unexpected response fd
[   13.942541] yealink: unexpected response fd
[   13.958540] yealink: unexpected response fd
[   13.974546] yealink: unexpected response fd
[   13.990546] yealink: unexpected response fd
[   14.006546] yealink: unexpected response fd
[   14.022547] yealink: unexpected response fd
[   14.038548] yealink: unexpected response fd
[   14.054547] yealink: unexpected response fd
[   14.070548] yealink: unexpected response fd
[   14.086551] yealink: unexpected response fd
[   14.102550] yealink: unexpected response fd
[   14.118552] yealink: unexpected response fd
[   14.134555] yealink: unexpected response fd
[   14.150553] yealink: unexpected response fd
[   14.166557] yealink: unexpected response fd
[   14.182556] yealink: unexpected response fd
[   14.198556] yealink: unexpected response fd
[   14.214557] yealink: unexpected response fd
[   14.230559] yealink: unexpected response fd
[   14.246558] yealink: unexpected response fd
[   14.262561] yealink: unexpected response fd
[   14.278564] yealink: unexpected response fd
[   14.294563] yealink: unexpected response fd
[   14.310561] yealink: unexpected response fd
[   14.326566] yealink: unexpected response fd
[   14.342567] yealink: unexpected response fd
[   14.358571] yealink: unexpected response fd
[   14.374569] yealink: unexpected response fd
[   14.390569] yealink: unexpected response fd
[   14.406572] yealink: unexpected response fd
[   14.422572] yealink: unexpected response fd
[   14.438574] yealink: unexpected response fd
[   14.454575] yealink: unexpected response fd
[   14.470573] yealink: unexpected response fd
[   14.486595] yealink: unexpected response fd
[   14.502575] yealink: unexpected response fd
[   14.518579] yealink: unexpected response fd
[   14.534579] yealink: unexpected response fd
[   14.550579] yealink: unexpected response fd
[   14.566581] yealink: unexpected response fd
[   14.582583] yealink: unexpected response fd
[   14.598586] yealink: unexpected response fd
[   14.614590] yealink: unexpected response fd
[   14.630588] yealink: unexpected response fd
[   14.646593] yealink: unexpected response fd
[   14.662590] yealink: unexpected response fd
[   14.678590] yealink: unexpected response fd
[   14.694590] yealink: unexpected response fd
[   14.710593] yealink: unexpected response fd
[   14.726597] yealink: unexpected response fd
[   14.742613] yealink: unexpected response fd
[   14.758594] yealink: unexpected response fd
[   14.774594] yealink: unexpected response fd
[   14.790597] yealink: unexpected response fd
[   14.806598] yealink: unexpected response fd
[   14.822598] yealink: unexpected response fd
[   14.838601] yealink: unexpected response fd
[   14.854601] yealink: unexpected response fd
[   14.870599] yealink: unexpected response fd
[   14.886606] yealink: unexpected response fd
[   14.902610] yealink: unexpected response fd
[   14.918606] yealink: unexpected response fd
[   14.934606] yealink: unexpected response fd
[   14.950608] yealink: unexpected response fd
[   14.966606] yealink: unexpected response fd
[   14.982610] yealink: unexpected response fd
[   14.998610] yealink: unexpected response fd
[   15.014614] yealink: unexpected response fd
[   15.030615] yealink: unexpected response fd
[   15.046614] yealink: unexpected response fd
[   15.062615] yealink: unexpected response fd
[   15.078616] yealink: unexpected response fd
[   15.094633] yealink: unexpected response fd
[   15.110620] yealink: unexpected response fd
[   15.126621] yealink: unexpected response fd
[   15.142623] yealink: unexpected response fd
[   15.158622] yealink: unexpected response fd
[   15.174621] yealink: unexpected response fd
[   15.190623] yealink: unexpected response fd
[   15.206623] yealink: unexpected response fd
[   15.222629] yealink: unexpected response fd
[   15.238625] yealink: unexpected response fd
[   15.250035] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   15.250037] Bluetooth: BNEP filters: protocol multicast
[   15.254632] yealink: unexpected response fd
[   15.270628] yealink: unexpected response fd
[   15.280015] Bridge firewalling registered
[   15.286636] yealink: unexpected response fd
[   15.302633] yealink: unexpected response fd
[   15.318631] yealink: unexpected response fd
[   15.334633] yealink: unexpected response fd
[   15.350633] yealink: unexpected response fd
[   15.366635] yealink: unexpected response fd
[   15.382655] yealink: unexpected response fd
[   15.398635] yealink: unexpected response fd
[   15.414638] yealink: unexpected response fd
[   15.430634] yealink: unexpected response fd
[   15.446639] yealink: unexpected response fd
[   15.462639] yealink: unexpected response fd
[   15.478648] yealink: unexpected response fd
[   15.494644] yealink: unexpected response fd
[   15.510644] yealink: unexpected response fd
[   15.526649] yealink: unexpected response fd
[   15.542646] yealink: unexpected response fd
[   15.558647] yealink: unexpected response fd
[   15.574647] yealink: unexpected response fd
[   15.590653] yealink: unexpected response fd
[   15.606654] yealink: unexpected response fd
[   15.622652] yealink: unexpected response fd
[   15.638657] yealink: unexpected response fd
[   15.654655] yealink: unexpected response fd
[   15.670655] yealink: unexpected response fd
[   15.686655] yealink: unexpected response fd
[   15.702658] yealink: unexpected response fd
[   15.718658] yealink: unexpected response fd
[   15.734663] yealink: unexpected response fd
[   15.750658] yealink: unexpected response fd
[   15.766666] yealink: unexpected response fd
[   15.782662] yealink: unexpected response fd
[   15.798663] yealink: unexpected response fd
[   15.814668] yealink: unexpected response fd
[   15.830663] yealink: unexpected response fd
[   15.846666] yealink: unexpected response fd
[   15.862668] yealink: unexpected response fd
[   15.878668] yealink: unexpected response fd
[   15.894670] yealink: unexpected response fd
[   15.910671] yealink: unexpected response fd
[   15.926672] yealink: unexpected response fd
[   15.942675] yealink: unexpected response fd
[   15.958674] yealink: unexpected response fd
[   15.974673] yealink: unexpected response fd
[   15.990675] yealink: unexpected response fd
[   16.006674] yealink: unexpected response fd
[   16.022679] yealink: unexpected response fd
[   16.038678] yealink: unexpected response fd
[   16.054681] yealink: unexpected response fd
[   16.070681] yealink: unexpected response fd
[   16.086682] yealink: unexpected response fd
[   16.102683] yealink: unexpected response fd
[   16.118684] yealink: unexpected response fd
[   16.134686] yealink: unexpected response fd
[   16.150692] yealink: unexpected response fd
[   16.166688] yealink: unexpected response fd
[   16.182689] yealink: unexpected response fd
[   16.198695] yealink: unexpected response fd
[   16.214691] yealink: unexpected response fd
[   16.230693] yealink: unexpected response fd
[   16.246693] yealink: unexpected response fd
[   16.262693] yealink: unexpected response fd
[   16.278695] yealink: unexpected response fd
[   16.294699] yealink: unexpected response fd
[   16.310697] yealink: unexpected response fd
[   16.326700] yealink: unexpected response fd
[   16.342703] yealink: unexpected response fd
[   16.358704] yealink: unexpected response fd
[   16.374708] yealink: unexpected response fd
[   16.390705] yealink: unexpected response fd
[   16.406701] yealink: unexpected response fd
[   16.422705] yealink: unexpected response fd
[   16.438706] yealink: unexpected response fd
[   16.454714] yealink: unexpected response fd
[   16.470710] yealink: unexpected response fd
[   16.486712] yealink: unexpected response fd
[   16.502712] yealink: unexpected response fd
[   16.518709] yealink: unexpected response fd
[   16.534713] yealink: unexpected response fd
[   16.550713] yealink: unexpected response fd
[   16.566714] yealink: unexpected response fd
[   16.582718] yealink: unexpected response fd
[   16.598716] yealink: unexpected response fd
[   16.614716] yealink: unexpected response fd
[   16.630419] ppdev: user-space parallel port driver
[   16.630722] yealink: unexpected response fd
[   16.646719] yealink: unexpected response fd
[   16.662719] yealink: unexpected response fd
[   16.678722] yealink: unexpected response fd
[   16.694729] yealink: unexpected response fd
[   16.710724] yealink: unexpected response fd
[   16.726724] yealink: unexpected response fd
[   16.742725] yealink: unexpected response fd
[   16.758732] yealink: unexpected response fd
[   16.774727] yealink: unexpected response fd
[   16.790732] yealink: unexpected response fd
[   16.806729] yealink: unexpected response fd
[   16.822736] yealink: unexpected response fd
[   16.838730] yealink: unexpected response fd
[   16.854735] yealink: unexpected response fd
[   16.870734] yealink: unexpected response fd
[   16.886738] yealink: unexpected response fd
[   16.902739] yealink: unexpected response fd
[   16.918737] yealink: unexpected response fd
[   16.934740] yealink: unexpected response fd
[   16.950744] yealink: unexpected response fd
```


Here is my bootchart:


[img]http://i41.tinypic.com/t7g47c.jpg[/img]

---

### Post by ninjapirate89 on 2009-04-25
It looks like your bootchart says 18 seconds, but I think that is from grub to login window. Do you perhaps have a lot of programs set to autostart under Startup Applications?

---

### Post by acidboot3r on 2009-04-25
No, I just installed Ubuntu 9.04 a few days ago. Yeah sure I installed a few programs but I never set any of them to launch at startup myself. They might have done that on their own perhaps. 

18 seconds? Perhaps it is 18 seconds, but to me it feels like 40. I'll get a stopwatch and time it from grub to login window myself. Anyways, after logging on into my account, there is a black screen on the desktop for like 5 seconds before the desktop shows. I presume that it's loading everything up, but is that normal?

---

### Post by ninjapirate89 on 2009-04-25
> **acidboot3r said:**
> Anyways, after logging on into my account, there is a black screen on the desktop for like 5 seconds before the desktop shows. I presume that it's loading everything up, but is that normal?

Yeah mine does that too, although I'm not sure it qualifies as "normal behavior".

---

### Post by acidboot3r on 2009-04-25
Ok, using a stopwatch and I recorded the amount of time it took to go from GRUB to the login screen. It actually took around 30 secs, not 18. Perhaps my bootchart is reading everything wrong?

And can you tell me what the hell the yealink: unexpected response thing in my bootlog is?

[IMG]http://i43.tinypic.com/ff1pv7.png[/IMG]

---

### Post by ninjapirate89 on 2009-04-25
> **acidboot3r said:**
> Ok, using a stopwatch and I recorded the amount of time it took to go from GRUB to the login screen. It actually took around 30 secs, not 18. Perhaps my bootchart is reading everything wrong?

And can you tell me what the hell the yealink: unexpected response thing in my bootlog is?

How long does your GRUB screen stay up? I have mine set to three seconds since I dual-boot with Windows but rarely use it.

Sorry I don't know what the yealink thing is. I've only used bootchart to test the time. I can't tell you anything else about the info on the chart.

---

### Post by acidboot3r on 2009-04-25
I dual boot with Windows Vista, and Vista is the default (I use it more than Ubuntu) and is set to boot into it in 2 seconds. I always have to manually select Ubuntu to boot into it.

---

### Post by ninjapirate89 on 2009-04-25
> **acidboot3r said:**
> I dual boot with Windows Vista, and Vista is the default (I use it more than Ubuntu) and is set to boot into it in 2 seconds. I always have to manually select Ubuntu to boot into it.

Sorry I can't be of any more help. Just out of curiosity, have you timed how long it takes for Vista to start up? I haven't used it and don't know how it compares.

---

### Post by acidboot3r on 2009-04-25
Ok i booted into Vista and it's comparatively similar to Ubuntu. It took it 30-35 seconds to go from GRUB to the Vista login screen.

Thanks for your help anyways.

---

### Post by Herman on 2009-04-25
When recording boot-up times, it's a good idea to try to record the time until the operating system is actually ready to use.
Some operating systems will show the desktop early, but then it may remain frozen for a considerable amount of time before the operating system is really able to perform any useful tasks.

I would call a boot-up time of around 90 seconds to be fairly normal for an average computer, starting from the time I hit 'Enter', at the GRUB prompt, through login and on until the network icon appears, as that seems to be the last visible occurrence before Ubuntu is fully booted, and ready to perform any task.
Your 30 - 35 seconds and 40+ seconds seems quick to me. You must have a good computer! :)

I was recording some boot-up times a few days ago, thinking it might be an indication of the speed of different file systems.

Actually, boot time isn't a problem worth worrying about too much in Linux operating systems because they rarely need to be rebooted anyway. Once in a while we receive a new kernel in an update, but other than that, Ubuntu never needs to be rebooted.
We should be able to leave our computers running indefinitely. Some Linux servers stay up for years without needing a reboot.
Nowadays I usually shut my computer down if I will be away from it for more than an hour or so, or overnight to save energy and try to reduce greenhouse gasses. It's debatable if turning the computer off saves very much energy though, since the computer will go to sleep and after about an hour it will be using hardly any energy at all. The monitor will be off and the hard disks should be spun down by then. There are settings in 'System'-->'Preferences'-->'Power Management' where we can adjust how much time the computer should be idle before the monitor switches off and how long before the computer will 'go to sleep'. I just looked and it looks like the default is set to 'never' (go to sleep). I set mine to turn off the monitor after 20 minutes and to go to sleep after 30 minutes of idleness. 
That would probably be a better idea than shutting down. :)

---

### Post by Sef on 2009-04-25
Moved to Testimonials and Experiences since it is the former.

---

### Post by ninjapirate89 on 2009-04-25
I know this thread got moved to Testimonials & Experiences but I'd say the OP still wants to know what yealink: unexpected response means.

---

### Post by cariboo on 2009-04-25
If you do a search on the error, it looks like a skype phone error, but it is pretty hard to tell with a truncated dmesg output.

---

