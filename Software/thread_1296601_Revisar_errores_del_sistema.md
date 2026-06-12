---
title: "Revisar errores del sistema"
date: 2009-10-20
forum: Software
---

### Post by alberto71 on 2009-10-20
Hola.

Dado que tengo un problema esquivo en cuanto a su causa, estuve revisando el Visor de Sucesos, pero como ni siquiera se bien lo que busco, se me hace casi imposible sacar provecho de la herramienta.

Me explico. Cada tanto tiempo, pueden pasar días o semanas, mi pc se congela y no hay **AltGR+SysRq+REISUB** o **Ctrl+Alt+Fx** que me salve, simplemente se freeza por completo y no responden ni los periféricos de entrada. Solo puedo resetear.

De las veces que recuerdo, ocurre con algo de multimedia, ver un video por ejemplo. Pero dado que no siempre se cuelga en las mismas circunstancias y por ende, no puedo repetir/aislar el error, decidí bucear en el Visor de Sucesos pero hasta ahora no encontré nada.

Tengo códecs para todo lo que uso, que no pasa de .avi-mpeg-mp4-rmvb; así que no me parece problema de códces, la prueba es que un archivo que supuestamente tildó mi pc, al reiniciar se visualiza a la perfección.

Alguien sabe como o donde puedo encontrar el último error ocurrido en el sistema para así poder determinar que le pasa a mi JJ?

Gracias.

---

### Post by josecuervo86 on 2009-10-20
Probaste con ```
dmesg
``` en una terminal?

---

### Post by alberto71 on 2009-10-22
Hola.

Transcribo aquí lo que me sale tras el comando dmesg:

```
[    0.000000] BIOS EBDA/lowmem at: 0009fc00/0009fc00
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.28-15-generic (buildd@rothera) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #52-Ubuntu SMP Wed Sep 9 10:49:34 UTC 2009 (Ubuntu 2.6.28-15.52-generic)
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
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000006ffa0000 (usable)
[    0.000000]  BIOS-e820: 000000006ffa0000 - 000000006ffae000 (ACPI data)
[    0.000000]  BIOS-e820: 000000006ffae000 - 000000006ffe0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000006ffe0000 - 000000006ffee000 (reserved)
[    0.000000]  BIOS-e820: 000000006fff0000 - 0000000080100000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] DMI present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working it around.
[    0.000000] last_pfn = 0x6ffa0 max_arch_pfn = 0x100000
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009fc00 (usable)
[    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000006ffa0000 (usable)
[    0.000000]  modified: 000000006ffa0000 - 000000006ffae000 (ACPI data)
[    0.000000]  modified: 000000006ffae000 - 000000006ffe0000 (ACPI NVS)
[    0.000000]  modified: 000000006ffe0000 - 000000006ffee000 (reserved)
[    0.000000]  modified: 000000006fff0000 - 0000000080100000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] kernel direct mapping tables up to 373fe000 @ 10000-16000
[    0.000000] RAMDISK: 378bd000 - 37fef0f0
[    0.000000] Allocated new RAMDISK: 0087d000 - 00faf0f0
[    0.000000] Move RAMDISK from 00000000378bd000 - 0000000037fef0ef to 0087d000 - 00faf0ef
[    0.000000] ACPI: RSDP 000F9D50, 0014 (r0 ACPIAM)
[    0.000000] ACPI: RSDT 6FFA0000, 0044 (r1 112707 RSDT0943 20071127 MSFT       97)
[    0.000000] ACPI: FACP 6FFA0200, 0084 (r1 112707 FACP0943 20071127 MSFT       97)
[    0.000000] ACPI: DSDT 6FFA04A0, 576F (r1  1AAAA 1AAAA000        0 INTL 20051117)
[    0.000000] ACPI: FACS 6FFAE000, 0040
[    0.000000] ACPI: APIC 6FFA0390, 0080 (r1 112707 APIC0943 20071127 MSFT       97)
[    0.000000] ACPI: MCFG 6FFA0410, 003C (r1 112707 OEMMCFG  20071127 MSFT       97)
[    0.000000] ACPI: WDRT 6FFA0450, 0047 (r1 112707 NV-WDRT  20071127 MSFT       97)
[    0.000000] ACPI: OEMB 6FFAE040, 0071 (r1 112707 OEMB0943 20071127 MSFT       97)
[    0.000000] ACPI: HPET 6FFA5C10, 0038 (r1 112707 OEMHPET0 20071127 MSFT       97)
[    0.000000] ACPI: NVHD 6FFAE0C0, 0554 (r1 112707  NVHDCP  20071127 MSFT       97)
[    0.000000] ACPI: SSDT 6FFAEF40, 0A7C (r1 DpgPmm    CpuPm       12 INTL 20051117)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 907MB HIGHMEM available.
[    0.000000] 883MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 373fe000
[    0.000000]   low ram: 00000000 - 373fe000
[    0.000000]   bootmap 00012000 - 00018e80
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00373fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008780ac]    TEXT DATA BSS ==> [0000100000 - 00008780ac]
[    0.000000]   #4 [0000879000 - 000087d000]    INIT_PG_TABLE ==> [0000879000 - 000087d000]
[    0.000000]   #5 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #6 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
[    0.000000]   #7 [000087d000 - 0000faf0f0]      NEW RAMDISK ==> [000087d000 - 0000faf0f0]
[    0.000000]   #8 [0000012000 - 0000019000]          BOOTMAP ==> [0000012000 - 0000019000]
[    0.000000] found SMP MP-table at [c00ff780] 000ff780
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000373fe
[    0.000000]   HighMem  0x000373fe -> 0x0006ffa0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0006ffa0
[    0.000000] On node 0 totalpages: 458543
[    0.000000] free_area_init_node: node 0, pgdat c06cb780, node_mem_map c1000200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1736 pages used for memmap
[    0.000000]   Normal zone: 220470 pages, LIFO batch:31
[    0.000000]   HighMem zone: 1816 pages used for memmap
[    0.000000]   HighMem zone: 230538 pages, LIFO batch:31
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x82] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x83] disabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80100000:7eb00000)
[    0.000000] PERCPU: Allocating 45056 bytes of per cpu data
[    0.000000] NR_CPUS: 64, nr_cpu_ids: 4, nr_node_ids 1
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 454959
[    0.000000] Kernel command line: root=UUID=3da5b27e-61ce-454f-8cfd-fdb677d4a136 ro quiet splash 
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1999.914 MHz processor.
[    0.004000] spurious 8259A interrupt: IRQ7.
[    0.004000] Console: colour VGA+ 80x25
[    0.004000] console [tty0] enabled
[    0.004000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.004000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.004000] allocated 9172800 bytes of page_cgroup
[    0.004000] please try cgroup_disable=memory option if you don't want
[    0.004000] Scanning for low memory corruption every 60 seconds
[    0.004000] Memory: 1794008k/1834624k available (4116k kernel code, 39360k reserved, 2199k data, 532k init, 929416k highmem)
[    0.004000] virtual kernel memory layout:
[    0.004000]     fixmap  : 0xffc77000 - 0xfffff000   (3616 kB)
[    0.004000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.004000]     vmalloc : 0xf7bfe000 - 0xff3fe000   ( 120 MB)
[    0.004000]     lowmem  : 0xc0000000 - 0xf73fe000   ( 883 MB)
[    0.004000]       .init : 0xc0733000 - 0xc07b8000   ( 532 kB)
[    0.004000]       .data : 0xc05050ff - 0xc072ae60   (2199 kB)
[    0.004000]       .text : 0xc0100000 - 0xc05050ff   (4116 kB)
[    0.004000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.004000] SLUB: Genslabs=12, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.004000] hpet clockevent registered
[    0.004000] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.004000] Calibrating delay loop (skipped), value calculated using timer frequency.. 3999.82 BogoMIPS (lpj=7999656)
[    0.004000] Security Framework initialized
[    0.004000] SELinux:  Disabled at boot.
[    0.004000] AppArmor: AppArmor initialized
[    0.004000] Mount-cache hash table entries: 512
[    0.004000] Initializing cgroup subsys ns
[    0.004000] Initializing cgroup subsys cpuacct
[    0.004000] Initializing cgroup subsys memory
[    0.004000] Initializing cgroup subsys freezer
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 1024K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 0
[    0.004000] using mwait in idle threads.
[    0.004000] Checking 'hlt' instruction... OK.
[    0.018399] ACPI: Core revision 20080926
[    0.019802] ACPI: Checking initramfs for custom DSDT
[    0.313884] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.353579] CPU0: Intel(R) Pentium(R) Dual  CPU  E2180  @ 2.00GHz stepping 0d
[    0.356001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.004000] Initializing CPU#1
[    0.004000] Calibrating delay using timer specific routine.. 3999.97 BogoMIPS (lpj=7999957)
[    0.004000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.004000] CPU: L2 cache: 1024K
[    0.004000] CPU: Physical Processor ID: 0
[    0.004000] CPU: Processor Core ID: 1
[    0.440287] CPU1: Intel(R) Pentium(R) Dual  CPU  E2180  @ 2.00GHz stepping 0d
[    0.440303] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.444039] Brought up 2 CPUs
[    0.444041] Total of 2 processors activated (7999.80 BogoMIPS).
[    0.444110] CPU0 attaching sched-domain:
[    0.444113]  domain 0: span 0-1 level MC
[    0.444115]   groups: 0 1
[    0.444121] CPU1 attaching sched-domain:
[    0.444123]  domain 0: span 0-1 level MC
[    0.444125]   groups: 1 0
[    0.444194] net_namespace: 776 bytes
[    0.444194] Booting paravirtualized kernel on bare hardware
[    0.444323] Time: 14:03:43  Date: 10/22/09
[    0.444323] regulator: core version 0.5
[    0.444323] NET: Registered protocol family 16
[    0.444323] EISA bus registered
[    0.444323] ACPI: bus type pci registered
[    0.444323] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.444323] PCI: Not using MMCONFIG.
[    0.444412] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=4
[    0.444414] PCI: Using configuration type 1 for base access
[    0.445252] ACPI: EC: Look up EC in DSDT
[    0.456733] ACPI: Interpreter enabled
[    0.456737] ACPI: (supports S0 S1 S3 S4 S5)
[    0.456758] ACPI: Using IOAPIC for interrupt routing
[    0.456812] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.461842] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
[    0.461844] PCI: Using MMCONFIG for extended config space
[    0.470661] ACPI: No dock devices found.
[    0.470728] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.471704] pci 0000:00:03.0: reg 10 io port: [0x4f00-0x4fff]
[    0.471756] pci 0000:00:03.1: reg 10 io port: [0x4900-0x493f]
[    0.471772] pci 0000:00:03.1: reg 20 io port: [0x4d00-0x4d3f]
[    0.471777] pci 0000:00:03.1: reg 24 io port: [0x4e00-0x4e3f]
[    0.471791] pci 0000:00:03.1: PME# supported from D3hot D3cold
[    0.471797] pci 0000:00:03.1: PME# disabled
[    0.471964] pci 0000:00:04.0: reg 10 32bit mmio: [0xfeaff000-0xfeafffff]
[    0.471992] pci 0000:00:04.0: supports D1 D2
[    0.471994] pci 0000:00:04.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.471998] pci 0000:00:04.0: PME# disabled
[    0.472033] pci 0000:00:04.1: reg 10 32bit mmio: [0xfeafec00-0xfeafecff]
[    0.472063] pci 0000:00:04.1: supports D1 D2
[    0.472065] pci 0000:00:04.1: PME# supported from D0 D1 D2 D3hot D3cold
[    0.472069] pci 0000:00:04.1: PME# disabled
[    0.472120] pci 0000:00:08.0: reg 20 io port: [0xffa0-0xffaf]
[    0.472164] pci 0000:00:09.0: reg 10 32bit mmio: [0xfeaf8000-0xfeafbfff]
[    0.472193] pci 0000:00:09.0: PME# supported from D3hot D3cold
[    0.472196] pci 0000:00:09.0: PME# disabled
[    0.472264] pci 0000:00:0b.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.472267] pci 0000:00:0b.0: PME# disabled
[    0.472305] pci 0000:00:0c.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.472309] pci 0000:00:0c.0: PME# disabled
[    0.472346] pci 0000:00:0d.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.472350] pci 0000:00:0d.0: PME# disabled
[    0.472382] pci 0000:00:0e.0: reg 10 io port: [0xe480-0xe487]
[    0.472387] pci 0000:00:0e.0: reg 14 io port: [0xe400-0xe403]
[    0.472392] pci 0000:00:0e.0: reg 18 io port: [0xe080-0xe087]
[    0.472397] pci 0000:00:0e.0: reg 1c io port: [0xe000-0xe003]
[    0.472402] pci 0000:00:0e.0: reg 20 io port: [0xdc00-0xdc0f]
[    0.472406] pci 0000:00:0e.0: reg 24 32bit mmio: [0xfeafc000-0xfeafdfff]
[    0.472448] pci 0000:00:0f.0: reg 10 32bit mmio: [0xfeaf7000-0xfeaf7fff]
[    0.472454] pci 0000:00:0f.0: reg 14 io port: [0xd880-0xd887]
[    0.472459] pci 0000:00:0f.0: reg 18 32bit mmio: [0xfeafe800-0xfeafe8ff]
[    0.472464] pci 0000:00:0f.0: reg 1c 32bit mmio: [0xfeafe400-0xfeafe40f]
[    0.472481] pci 0000:00:0f.0: supports D1 D2
[    0.472483] pci 0000:00:0f.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.472488] pci 0000:00:0f.0: PME# disabled
[    0.472515] pci 0000:00:10.0: reg 10 32bit mmio: [0xfd000000-0xfdffffff]
[    0.472523] pci 0000:00:10.0: reg 14 64bit mmio: [0xd0000000-0xdfffffff]
[    0.472531] pci 0000:00:10.0: reg 1c 64bit mmio: [0xfc000000-0xfcffffff]
[    0.472539] pci 0000:00:10.0: reg 30 32bit mmio: [0xfeac0000-0xfeadffff]
[    0.472604] pci 0000:01:06.0: reg 10 32bit mmio: [0xfebff000-0xfebfffff]
[    0.472672] pci 0000:01:06.1: reg 10 32bit mmio: [0xfebfe800-0xfebfefff]
[    0.472712] pci 0000:01:06.1: supports D1 D2
[    0.472714] pci 0000:01:06.1: PME# supported from D1 D2 D3hot
[    0.472719] pci 0000:01:06.1: PME# disabled
[    0.472764] pci 0000:00:0a.0: transparent bridge
[    0.472769] pci 0000:00:0a.0: bridge 32bit mmio: [0xfeb00000-0xfebfffff]
[    0.472937] bus 00 -> node 0
[    0.472944] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.473233] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.473397] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR10._PRT]
[    0.473514] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR11._PRT]
[    0.473631] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR12._PRT]
[    0.484273] ACPI: PCI Interrupt Link [LNKA] (IRQs 16 17 18 19) *0, disabled.
[    0.484534] ACPI: PCI Interrupt Link [LNKB] (IRQs 16 17 18 19) *10
[    0.484787] ACPI: PCI Interrupt Link [LNKC] (IRQs 16 17 18 19) *0, disabled.
[    0.485039] ACPI: PCI Interrupt Link [LNKD] (IRQs 16 17 18 19) *0, disabled.
[    0.485289] ACPI: PCI Interrupt Link [LNEA] (IRQs 16 17 18 19) *0, disabled.
[    0.485539] ACPI: PCI Interrupt Link [LNEB] (IRQs 16 17 18 19) *0, disabled.
[    0.485790] ACPI: PCI Interrupt Link [LNEC] (IRQs 16 17 18 19) *0, disabled.
[    0.486040] ACPI: PCI Interrupt Link [LNED] (IRQs 16 17 18 19) *0, disabled.
[    0.486296] ACPI: PCI Interrupt Link [LUB0] (IRQs 20 21 22 23) *10
[    0.486551] ACPI: PCI Interrupt Link [LUB2] (IRQs 20 21 22 23) *11
[    0.486806] ACPI: PCI Interrupt Link [LMAC] (IRQs 20 21 22 23) *10
[    0.487061] ACPI: PCI Interrupt Link [LAZA] (IRQs 20 21 22 23) *10
[    0.487318] ACPI: PCI Interrupt Link [SGRU] (IRQs 20 21 22 23) *10
[    0.487576] ACPI: PCI Interrupt Link [LSMB] (IRQs 20 21 22 23) *11
[    0.487829] ACPI: PCI Interrupt Link [LPMU] (IRQs 20 21 22 23) *0, disabled.
[    0.488088] ACPI: PCI Interrupt Link [LSA0] (IRQs 20 21 22 23) *5
[    0.488384] ACPI: PCI Interrupt Link [LATA] (IRQs 20 21 22 23) *0, disabled.
[    0.488508] ACPI Warning (tbutils-0217): Incorrect checksum in table [OEMB] - 42, should be 3D [20080926]
[    0.488640] ACPI: WMI: Mapper loaded
[    0.488695] SCSI subsystem initialized
[    0.488695] libata version 3.00 loaded.
[    0.488695] usbcore: registered new interface driver usbfs
[    0.488695] usbcore: registered new interface driver hub
[    0.488695] usbcore: registered new device driver usb
[    0.488695] PCI: Using ACPI for IRQ routing
[    0.496013] Bluetooth: Core ver 2.13
[    0.496039] NET: Registered protocol family 31
[    0.496039] Bluetooth: HCI device and connection manager initialized
[    0.496039] Bluetooth: HCI socket layer initialized
[    0.496039] NET: Registered protocol family 8
[    0.496039] NET: Registered protocol family 20
[    0.496051] NetLabel: Initializing
[    0.496054] NetLabel:  domain hash size = 128
[    0.496057] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.496076] NetLabel:  unlabeled traffic allowed by default
[    0.496102] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 31
[    0.496107] hpet0: 3 comparators, 32-bit 25.000000 MHz counter
[    0.500090] AppArmor: AppArmor Filesystem Enabled
[    0.504012] Switched to high resolution mode on CPU 0
[    0.504350] Switched to high resolution mode on CPU 1
[    0.507951] pnp: PnP ACPI init
[    0.507967] ACPI: bus type pnp registered
[    0.513510] pnp: PnP ACPI: found 15 devices
[    0.513512] ACPI: ACPI bus type pnp unregistered
[    0.513515] PnPBIOS: Disabled by ACPI PNP
[    0.513528] system 00:06: ioport range 0x4d0-0x4d1 has been reserved
[    0.513531] system 00:06: ioport range 0x800-0x80f has been reserved
[    0.513533] system 00:06: ioport range 0x4000-0x407f has been reserved
[    0.513536] system 00:06: ioport range 0x4080-0x40ff has been reserved
[    0.513538] system 00:06: ioport range 0x4400-0x447f has been reserved
[    0.513541] system 00:06: ioport range 0x4480-0x44ff has been reserved
[    0.513543] system 00:06: ioport range 0x4800-0x487f has been reserved
[    0.513546] system 00:06: ioport range 0x4880-0x48ff has been reserved
[    0.513548] system 00:06: iomem range 0xfec80000-0xfd93ffff could not be reserved
[    0.513551] system 00:06: iomem range 0xfed02000-0xfed03fff has been reserved
[    0.513554] system 00:06: iomem range 0xfed04000-0xfed04fff has been reserved
[    0.513557] system 00:06: iomem range 0xfee01000-0xfeefffff has been reserved
[    0.513563] system 00:09: iomem range 0xfec00000-0xfec00fff has been reserved
[    0.513565] system 00:09: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.513572] system 00:0c: ioport range 0xa00-0xa0f has been reserved
[    0.513574] system 00:0c: ioport range 0xa10-0xa1f has been reserved
[    0.513579] system 00:0d: iomem range 0xe0000000-0xefffffff has been reserved
[    0.513585] system 00:0e: iomem range 0x0-0x9ffff could not be reserved
[    0.513588] system 00:0e: iomem range 0xc0000-0xcffff could not be reserved
[    0.513591] system 00:0e: iomem range 0xe0000-0xfffff could not be reserved
[    0.513593] system 00:0e: iomem range 0x100000-0x7fffffff could not be reserved
[    0.513596] system 00:0e: iomem range 0xfec00000-0xffffffff could not be reserved
[    0.548306] pci 0000:00:0a.0: PCI bridge, secondary bus 0000:01
[    0.548308] pci 0000:00:0a.0:   IO window: disabled
[    0.548313] pci 0000:00:0a.0:   MEM window: 0xfeb00000-0xfebfffff
[    0.548317] pci 0000:00:0a.0:   PREFETCH window: disabled
[    0.548322] pci 0000:00:0b.0: PCI bridge, secondary bus 0000:02
[    0.548324] pci 0000:00:0b.0:   IO window: disabled
[    0.548328] pci 0000:00:0b.0:   MEM window: disabled
[    0.548331] pci 0000:00:0b.0:   PREFETCH window: disabled
[    0.548335] pci 0000:00:0c.0: PCI bridge, secondary bus 0000:03
[    0.548337] pci 0000:00:0c.0:   IO window: disabled
[    0.548341] pci 0000:00:0c.0:   MEM window: disabled
[    0.548344] pci 0000:00:0c.0:   PREFETCH window: disabled
[    0.548349] pci 0000:00:0d.0: PCI bridge, secondary bus 0000:04
[    0.548350] pci 0000:00:0d.0:   IO window: disabled
[    0.548354] pci 0000:00:0d.0:   MEM window: disabled
[    0.548357] pci 0000:00:0d.0:   PREFETCH window: disabled
[    0.548367] pci 0000:00:0a.0: setting latency timer to 64
[    0.548374] pci 0000:00:0b.0: setting latency timer to 64
[    0.548381] pci 0000:00:0c.0: setting latency timer to 64
[    0.548387] pci 0000:00:0d.0: setting latency timer to 64
[    0.548390] bus: 00 index 0 io port: [0x00-0xffff]
[    0.548392] bus: 00 index 1 mmio: [0x000000-0xffffffff]
[    0.548395] bus: 01 index 0 mmio: [0x0-0x0]
[    0.548397] bus: 01 index 1 mmio: [0xfeb00000-0xfebfffff]
[    0.548399] bus: 01 index 2 mmio: [0x0-0x0]
[    0.548400] bus: 01 index 3 io port: [0x00-0xffff]
[    0.548402] bus: 01 index 4 mmio: [0x000000-0xffffffff]
[    0.548404] bus: 02 index 0 mmio: [0x0-0x0]
[    0.548406] bus: 02 index 1 mmio: [0x0-0x0]
[    0.548408] bus: 02 index 2 mmio: [0x0-0x0]
[    0.548409] bus: 02 index 3 mmio: [0x0-0x0]
[    0.548411] bus: 03 index 0 mmio: [0x0-0x0]
[    0.548413] bus: 03 index 1 mmio: [0x0-0x0]
[    0.548414] bus: 03 index 2 mmio: [0x0-0x0]
[    0.548416] bus: 03 index 3 mmio: [0x0-0x0]
[    0.548418] bus: 04 index 0 mmio: [0x0-0x0]
[    0.548419] bus: 04 index 1 mmio: [0x0-0x0]
[    0.548421] bus: 04 index 2 mmio: [0x0-0x0]
[    0.548423] bus: 04 index 3 mmio: [0x0-0x0]
[    0.548431] NET: Registered protocol family 2
[    0.560109] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.560384] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.560834] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.561129] TCP: Hash tables configured (established 131072 bind 65536)
[    0.561132] TCP reno registered
[    0.568177] NET: Registered protocol family 1
[    0.568304] checking if image is initramfs... it is
[    1.169550] Freeing initrd memory: 7368k freed
[    1.169768] cpufreq: No nForce2 chipset.
[    1.169904] audit: initializing netlink socket (disabled)
[    1.169929] type=2000 audit(1256220223.168:1): initialized
[    1.176986] highmem bounce pool size: 64 pages
[    1.176991] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.178256] VFS: Disk quotas dquot_6.5.1
[    1.178314] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.178896] fuse init (API version 7.10)
[    1.178975] msgmni has been set to 1704
[    1.179141] alg: No test for stdrng (krng)
[    1.179153] io scheduler noop registered
[    1.179155] io scheduler anticipatory registered
[    1.179157] io scheduler deadline registered
[    1.179170] io scheduler cfq registered (default)
[    1.201551] pci 0000:00:10.0: Boot video device
[    1.207128] pcieport-driver 0000:00:0b.0: setting latency timer to 64
[    1.207166] pcieport-driver 0000:00:0b.0: found MSI capability
[    1.207191] pcieport-driver 0000:00:0b.0: irq 2303 for MSI/MSI-X
[    1.207201] pci_express 0000:00:0b.0:pcie00: allocate port service
[    1.207215] pci_express 0000:00:0b.0:pcie03: allocate port service
[    1.207264] pcieport-driver 0000:00:0c.0: setting latency timer to 64
[    1.207300] pcieport-driver 0000:00:0c.0: found MSI capability
[    1.207322] pcieport-driver 0000:00:0c.0: irq 2302 for MSI/MSI-X
[    1.207331] pci_express 0000:00:0c.0:pcie00: allocate port service
[    1.207343] pci_express 0000:00:0c.0:pcie03: allocate port service
[    1.207392] pcieport-driver 0000:00:0d.0: setting latency timer to 64
[    1.207428] pcieport-driver 0000:00:0d.0: found MSI capability
[    1.207449] pcieport-driver 0000:00:0d.0: irq 2301 for MSI/MSI-X
[    1.207459] pci_express 0000:00:0d.0:pcie00: allocate port service
[    1.207471] pci_express 0000:00:0d.0:pcie03: allocate port service
[    1.207528] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.207539] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.207679] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.207681] ACPI: Power Button (FF) [PWRF]
[    1.207734] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    1.207744] ACPI: Power Button (CM) [PWRB]
[    1.208274] ACPI: SSDT 6FFAE620, 0235 (r1 DpgPmm  P001Ist       11 INTL 20051117)
[    1.208639] processor ACPI_CPU:00: registered as cooling_device0
[    1.208643] ACPI: Processor [P001] (supports 8 throttling states)
[    1.208967] ACPI: SSDT 6FFAEAB0, 0235 (r1 DpgPmm  P002Ist       12 INTL 20051117)
[    1.209301] processor ACPI_CPU:01: registered as cooling_device1
[    1.213101] thermal LNXTHERM:01: registered as thermal_zone0
[    1.213267] ACPI: Thermal Zone [THRM] (30 C)
[    1.213317] isapnp: Scanning for PnP cards...
[    1.566215] isapnp: No Plug & Play device found
[    1.576328] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.576423] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.576715] 00:04: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.577564] brd: module loaded
[    1.577864] loop: module loaded
[    1.577928] Fixed MDIO Bus: probed
[    1.577934] PPP generic driver version 2.4.2
[    1.577987] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    1.578016] Driver 'sd' needs updating - please use bus_type methods
[    1.578025] Driver 'sr' needs updating - please use bus_type methods
[    1.578066] ahci 0000:00:0e.0: version 3.0
[    1.578440] ACPI: PCI Interrupt Link [LSA0] enabled at IRQ 23
[    1.578448] ahci 0000:00:0e.0: PCI INT A -> Link[LSA0] -> GSI 23 (level, low) -> IRQ 23
[    1.578490] ahci 0000:00:0e.0: irq 2300 for MSI/MSI-X
[    1.578541] ahci 0000:00:0e.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl IDE mode
[    1.578544] ahci 0000:00:0e.0: flags: 64bit sntf led clo pmp pio 
[    1.578548] ahci 0000:00:0e.0: setting latency timer to 64
[    1.578935] scsi0 : ahci
[    1.579047] scsi1 : ahci
[    1.579103] scsi2 : ahci
[    1.579160] scsi3 : ahci
[    1.579252] ata1: SATA max UDMA/133 abar m8192@0xfeafc000 port 0xfeafc100 irq 2300
[    1.579255] ata2: SATA max UDMA/133 abar m8192@0xfeafc000 port 0xfeafc180 irq 2300
[    1.579257] ata3: SATA max UDMA/133 abar m8192@0xfeafc000 port 0xfeafc200 irq 2300
[    1.579260] ata4: SATA max UDMA/133 abar m8192@0xfeafc000 port 0xfeafc280 irq 2300
[    2.060024] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.060793] ata1.00: ATA-8: WDC WD3200AAKS-00B3A0, 01.03A01, max UDMA/133
[    2.060797] ata1.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    2.061695] ata1.00: configured for UDMA/133
[    2.948020] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.962771] ata2.00: ATA-7: WDC WD3200KS-00PFB0, 21.00M21, max UDMA/133
[    2.962775] ata2.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 0/1)
[    2.963572] ata2.00: configured for UDMA/133
[    3.280029] ata3: SATA link down (SStatus 0 SControl 300)
[    4.168020] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    4.171454] ata4.00: ATAPI: HL-DT-ST DVDRAM GH22NS40, NL00, max UDMA/100
[    4.175256] ata4.00: configured for UDMA/100
[    4.177663] scsi 0:0:0:0: Direct-Access     ATA      WDC WD3200AAKS-0 01.0 PQ: 0 ANSI: 5
[    4.177753] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
[    4.177768] sd 0:0:0:0: [sda] Write Protect is off
[    4.177771] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.177795] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.177865] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
[    4.177879] sd 0:0:0:0: [sda] Write Protect is off
[    4.177881] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.177904] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.177908]  sda: sda1 sda2 sda3 < sda5 sda6 sda7 > sda4
[    4.275186] sd 0:0:0:0: [sda] Attached SCSI disk
[    4.275236] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    4.275306] scsi 1:0:0:0: Direct-Access     ATA      WDC WD3200KS-00P 21.0 PQ: 0 ANSI: 5
[    4.275385] sd 1:0:0:0: [sdb] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
[    4.275399] sd 1:0:0:0: [sdb] Write Protect is off
[    4.275401] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    4.275426] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.275473] sd 1:0:0:0: [sdb] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
[    4.275488] sd 1:0:0:0: [sdb] Write Protect is off
[    4.275490] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    4.275513] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.275516]  sdb: sdb1 < sdb5 sdb6 sdb7 >
[    4.311568] sd 1:0:0:0: [sdb] Attached SCSI disk
[    4.311603] sd 1:0:0:0: Attached scsi generic sg1 type 0
[    4.314896] scsi 3:0:0:0: CD-ROM            HL-DT-ST DVDRAM GH22NS40  NL00 PQ: 0 ANSI: 5
[    4.326059] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    4.326063] Uniform CD-ROM driver Revision: 3.20
[    4.326209] sr 3:0:0:0: Attached scsi CD-ROM sr0
[    4.326244] sr 3:0:0:0: Attached scsi generic sg2 type 5
[    4.326485] pata_amd 0000:00:08.0: version 0.3.10
[    4.326527] pata_amd 0000:00:08.0: setting latency timer to 64
[    4.326606] scsi4 : pata_amd
[    4.326661] scsi5 : pata_amd
[    4.327704] ata5: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    4.327707] ata6: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    4.491091] ata6: port disabled. ignoring.
[    4.491595] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    4.491973] ACPI: PCI Interrupt Link [LUB2] enabled at IRQ 22
[    4.491981] ehci_hcd 0000:00:04.1: PCI INT B -> Link[LUB2] -> GSI 22 (level, low) -> IRQ 22
[    4.492007] ehci_hcd 0000:00:04.1: setting latency timer to 64
[    4.492010] ehci_hcd 0000:00:04.1: EHCI Host Controller
[    4.492066] ehci_hcd 0000:00:04.1: new USB bus registered, assigned bus number 1
[    4.492090] ehci_hcd 0000:00:04.1: debug port 1
[    4.492095] ehci_hcd 0000:00:04.1: cache line size of 32 is not supported
[    4.492109] ehci_hcd 0000:00:04.1: irq 22, io mem 0xfeafec00
[    4.504033] ehci_hcd 0000:00:04.1: USB 2.0 started, EHCI 1.00
[    4.504138] usb usb1: configuration #1 chosen from 1 choice
[    4.504179] hub 1-0:1.0: USB hub found
[    4.504193] hub 1-0:1.0: 10 ports detected
[    4.504299] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    4.504671] ACPI: PCI Interrupt Link [LUB0] enabled at IRQ 21
[    4.504677] ohci_hcd 0000:00:04.0: PCI INT A -> Link[LUB0] -> GSI 21 (level, low) -> IRQ 21
[    4.504688] ohci_hcd 0000:00:04.0: setting latency timer to 64
[    4.504691] ohci_hcd 0000:00:04.0: OHCI Host Controller
[    4.504731] ohci_hcd 0000:00:04.0: new USB bus registered, assigned bus number 2
[    4.504753] ohci_hcd 0000:00:04.0: irq 21, io mem 0xfeaff000
[    4.562070] usb usb2: configuration #1 chosen from 1 choice
[    4.562095] hub 2-0:1.0: USB hub found
[    4.562102] hub 2-0:1.0: 10 ports detected
[    4.562193] uhci_hcd: USB Universal Host Controller Interface driver
[    4.562283] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    4.564826] serio: i8042 KBD port at 0x60,0x64 irq 1
[    4.564831] serio: i8042 AUX port at 0x60,0x64 irq 12
[    4.568064] mice: PS/2 mouse device common for all mice
[    4.580117] rtc_cmos 00:08: RTC can wake from S4
[    4.580164] rtc_cmos 00:08: rtc core: registered rtc_cmos as rtc0
[    4.580206] rtc0: alarms up to one year, y3k, 114 bytes nvram, hpet irqs
[    4.580267] device-mapper: uevent: version 1.0.3
[    4.580350] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
[    4.580417] device-mapper: multipath: version 1.0.5 loaded
[    4.580419] device-mapper: multipath round-robin: version 1.0.0 loaded
[    4.580493] EISA: Probing bus 0 at eisa.0
[    4.580508] Cannot allocate resource for EISA slot 4
[    4.580521] EISA: Detected 0 cards.
[    4.580565] cpuidle: using governor ladder
[    4.580567] cpuidle: using governor menu
[    4.581063] TCP cubic registered
[    4.581155] NET: Registered protocol family 10
[    4.581582] lo: Disabled Privacy Extensions
[    4.581906] NET: Registered protocol family 17
[    4.581922] Bluetooth: L2CAP ver 2.11
[    4.581924] Bluetooth: L2CAP socket layer initialized
[    4.581927] Bluetooth: SCO (Voice Link) ver 0.6
[    4.581929] Bluetooth: SCO socket layer initialized
[    4.581957] Bluetooth: RFCOMM socket layer initialized
[    4.581965] Bluetooth: RFCOMM TTY layer initialized
[    4.581966] Bluetooth: RFCOMM ver 1.10
[    4.582578] Using IPI No-Shortcut mode
[    4.582651] registered taskstats version 1
[    4.582777]   Magic number: 13:674:81
[    4.582862] rtc_cmos 00:08: setting system clock to 2009-10-22 14:03:47 UTC (1256220227)
[    4.582865] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    4.582867] EDD information not available.
[    4.583149] Freeing unused kernel memory: 532k freed
[    4.583270] Write protecting the kernel text: 4120k
[    4.583314] Write protecting the kernel read-only data: 1524k
[    4.602746] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    4.844566] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 19
[    4.844578] ohci1394 0000:01:06.1: PCI INT A -> Link[LNKB] -> GSI 19 (level, low) -> IRQ 19
[    4.852519] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
[    4.852920] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 20
[    4.852928] forcedeth 0000:00:0f.0: PCI INT A -> Link[LMAC] -> GSI 20 (level, low) -> IRQ 20
[    4.852933] forcedeth 0000:00:0f.0: setting latency timer to 64
[    4.894376] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[febfe800-febfefff]  Max Packet=[1024]  IR/IT contexts=[4/4]
[    5.004529] usb 1-2: new high speed USB device using ehci_hcd and address 3
[    5.137634] usb 1-2: configuration #1 chosen from 1 choice
[    5.137951] hub 1-2:1.0: USB hub found
[    5.138286] hub 1-2:1.0: 4 ports detected
[    5.377220] forcedeth 0000:00:0f.0: ifname eth0, PHY OUI 0x732 @ 1, addr 00:1e:90:7d:16:67
[    5.377224] forcedeth 0000:00:0f.0: highdma pwrctl mgmt timirq gbit lnktim msi desc-v3
[    5.668034] usb 2-1: new full speed USB device using ohci_hcd and address 2
[    5.866209] PM: Starting manual resume from disk
[    5.866212] PM: Resume from partition 8:7
[    5.866214] PM: Checking hibernation image.
[    5.866344] PM: Resume from disk failed.
[    5.882431] EXT4-fs: barriers enabled
[    5.889448] usb 2-1: configuration #1 chosen from 1 choice
[    5.890317] kjournald2 starting.  Commit interval 5 seconds
[    5.890330] EXT4-fs: delayed allocation enabled
[    5.890333] EXT4-fs: file extents enabled
[    5.891080] EXT4-fs: mballoc enabled
[    5.891084] EXT4-fs: mounted filesystem with ordered data mode.
[    6.196043] usb 2-3: new full speed USB device using ohci_hcd and address 3
[    6.399230] usb 2-3: configuration #1 chosen from 1 choice
[    6.704034] usb 2-4: new full speed USB device using ohci_hcd and address 4
[    6.928252] usb 2-4: configuration #1 chosen from 1 choice
[    7.132509] usb 1-2.3: new high speed USB device using ehci_hcd and address 6
[    7.316547] usb 1-2.3: configuration #1 chosen from 1 choice
[    7.388525] usb 1-2.4: new full speed USB device using ehci_hcd and address 7
[    7.484495] usb 1-2.4: configuration #1 chosen from 1 choice
[    9.076587] udev: starting version 141
[    9.312809] [ueagle-atm] driver ueagle 1.4 loaded
[    9.312835] usb 2-3: [ueagle-atm] ADSL device founded vid (0X1110) pid (0X9022) Rev (0X5000): Eagle II
[    9.351449] usblp0: USB Bidirectional printer dev 4 if 0 alt 0 proto 2 vid 0x03F0 pid 0x7304
[    9.351479] usbcore: registered new interface driver usblp
[    9.360032] usbcore: registered new interface driver hiddev
[    9.360798] input: UCQ01000                         Samsung UC Audio as /devices/pci0000:00/0000:00:04.1/usb1/1-2/1-2.4/1-2.4:1.3/input/input4
[    9.387748] generic-usb 0003:4C2D:2900.0001: input,hidraw0: USB HID v1.00 Device [UCQ01000                         Samsung UC Audio] on usb-0000:00:04.1-2.4/input3
[    9.387775] usbcore: registered new interface driver usbhid
[    9.387817] usbhid: v2.6:USB HID core driver
[    9.488048] usb 2-3: reset full speed USB device using ohci_hcd and address 3
[    9.694271] usb 2-3: [ueagle-atm] pre-firmware device, uploading firmware
[    9.694322] usb 2-3: [ueagle-atm] loading firmware ueagle-atm/eagleII.fw
[    9.694327] usb 2-3: firmware: requesting ueagle-atm/eagleII.fw
[    9.694391] usbcore: registered new interface driver ueagle-atm
[    9.989687] Linux video capture interface: v2.00
[   10.246535] parport_pc 00:05: reported by Plug and Play ACPI
[   10.246580] parport0: PC-style at 0x378, irq 7 [PCSPP]
[   10.365296] Linux agpgart interface v0.103
[   10.412128] uvcvideo: Found UVC 1.00 device Saturn USB 2.0 Camera. (0ac8:c303)
[   10.413073] input: Saturn USB 2.0 Camera. as /devices/pci0000:00/0000:00:04.1/usb1/1-2/1-2.3/1-2.3:1.0/input/input5
[   10.417456] usbcore: registered new interface driver uvcvideo
[   10.417479] USB Video Class driver (v0.1.0)
[   10.437223] ppdev: user-space parallel port driver
[   10.521619] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[   10.578893] nvidia: module license 'NVIDIA' taints kernel.
[   10.737162] psmouse serio1: ID: 10 00 64ACPI: PCI Interrupt Link [SGRU] enabled at IRQ 23
[   10.832993] nvidia 0000:00:10.0: PCI INT A -> Link[SGRU] -> GSI 23 (level, low) -> IRQ 23
[   10.832999] nvidia 0000:00:10.0: setting latency timer to 64
[   10.834250] NVRM: loading NVIDIA UNIX x86 Kernel Module  180.44  Mon Mar 23 14:59:10 PST 2009
[   10.854314] ip_tables: (C) 2000-2006 Netfilter Core Team
[   10.897381] usbcore: registered new interface driver snd-usb-audio
[   10.908659] HDA Intel 0000:00:09.0: power state changed by ACPI to D0
[   10.909090] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 22
[   10.909097] HDA Intel 0000:00:09.0: PCI INT A -> Link[LAZA] -> GSI 22 (level, low) -> IRQ 22
[   10.909163] HDA Intel 0000:00:09.0: setting latency timer to 64
[   10.921726] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   10.921947] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Please use
[   10.921950] nf_conntrack.acct=1 kernel paramater, acct=1 nf_conntrack module option or
[   10.921952] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
[   11.018612] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input6
[   12.258380] usb 2-3: [ueagle-atm] firmware uploaded
[   12.284053] usb 2-3: USB disconnect, address 3
[   12.350609] lp0: using parport0 (interrupt-driven).
[   12.393721] w83627ehf: Found W83627DHG chip at 0xa10
[   12.425311] coretemp coretemp.0: Using relative temperature scale!
[   12.425355] coretemp coretemp.1: Using relative temperature scale!
[   12.552103] Adding 2273156k swap on /dev/sda7.  Priority:-1 extents:1 across:2273156k
[   13.088737] EXT4 FS on sda2, internal journal on sda2:8
[   13.875481] EXT4-fs: barriers enabled
[   13.891701] kjournald2 starting.  Commit interval 5 seconds
[   13.892187] EXT4 FS on sda5, internal journal on sda5:8
[   13.892189] EXT4-fs: delayed allocation enabled
[   13.892191] EXT4-fs: file extents enabled
[   13.892474] EXT4-fs: mballoc enabled
[   13.892478] EXT4-fs: mounted filesystem with ordered data mode.
[   14.852559] usb 2-3: new full speed USB device using ohci_hcd and address 5
[   14.944339] type=1505 audit(1256231037.861:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2369
[   14.989785] type=1505 audit(1256231037.905:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2373
[   14.989919] type=1505 audit(1256231037.905:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2373
[   14.989964] type=1505 audit(1256231037.905:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2373
[   14.990002] type=1505 audit(1256231037.905:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2373
[   15.068881] usb 2-3: configuration #1 chosen from 1 choice
[   15.118520] type=1505 audit(1256231038.033:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2378
[   15.118717] type=1505 audit(1256231038.033:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2378
[   15.121574] usb 2-3: [ueagle-atm] ADSL device founded vid (0X1110) pid (0X9021) Rev (0X500B): Eagle II
[   15.146751] type=1505 audit(1256231038.061:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2384
[   15.300047] usb 2-3: reset full speed USB device using ohci_hcd and address 5
[   15.575529] usb 2-3: [ueagle-atm] using iso mode
[   15.580641] usb 2-3: [ueagle-atm] (re)booting started
[   16.689080] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   16.689084] vboxdrv: Successfully done.
[   16.689086] vboxdrv: Found 2 processor cores.
[   16.689178] vboxdrv: fAsync=0 offMin=0x208 offMax=0x209e
[   16.689231] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   16.689233] vboxdrv: Successfully loaded version 3.0.8 (interface 0x000e0000).
[   17.000066] usb 2-3: firmware: requesting ueagle-atm/DSPep.bin
[   17.404603] usb 2-3: [ueagle-atm] ATU-R firmware version : 44e2ea17
[   17.404611] usb 2-3: firmware: requesting ueagle-atm/CMVep.bin.v2
[   17.408578] usb 2-3: [Ueagle-atm] requesting firmware ueagle-atm/CMVep.bin.v2 failed, try to get older cmvs
[   17.408583] usb 2-3: firmware: requesting ueagle-atm/CMVep.bin
[   17.435833] usb 2-3: [Ueagle-atm] use deprecated cmvs version, please update your firmware
[   17.490733] usb 2-3: [ueagle-atm] modem started, waiting synchronization...
[   18.840902] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   18.840905] Bluetooth: BNEP filters: protocol multicast
[   18.990593] Bridge firewalling registered
[   22.355256] ppdev0: registered pardevice
[   22.404256] ppdev0: unregistered pardevice
[   28.556108] usb 2-3: [ueagle-atm] modem operational
[   28.974328] PPP BSD Compression module registered
[   32.368823] nas0: no IPv6 routers present
[  108.122661] Too big adjustment 32
[  108.189198] Too big adjustment 32
[  129.034773] Too big adjustment 32
[  129.093170] Too big adjustment 32
[  132.172629] Inbound IN=ppp0 OUT= MAC= SRC=186.124.217.249 DST=186.124.5.61 LEN=48 TOS=0x00 PREC=0x00 TTL=123 ID=12332 DF PROTO=TCP SPT=17304 DPT=135 WINDOW=16384 RES=0x00 SYN URGP=0 
[  262.459249] Inbound IN=ppp0 OUT= MAC= SRC=190.229.26.131 DST=186.124.5.61 LEN=48 TOS=0x00 PREC=0x00 TTL=125 ID=44483 DF PROTO=TCP SPT=3697 DPT=445 WINDOW=65535 RES=0x00 SYN URGP=0 
[  267.484457] Inbound IN=ppp0 OUT= MAC= SRC=114.44.12.111 DST=186.124.5.61 LEN=48 TOS=0x00 PREC=0x00 TTL=115 ID=22319 DF PROTO=TCP SPT=1075 DPT=445 WINDOW=65535 RES=0x00 SYN URGP=0 
[  270.595588] Inbound IN=ppp0 OUT= MAC= SRC=114.44.12.111 DST=186.124.5.61 LEN=48 TOS=0x00 PREC=0x00 TTL=115 ID=22735 DF PROTO=TCP SPT=1075 DPT=445 WINDOW=65535 RES=0x00 SYN URGP=0 
```

De todas maneras, solo puedo tirar este comando una vez que reinié la pc, no sé si contiene info como para saber que pasó.

---

