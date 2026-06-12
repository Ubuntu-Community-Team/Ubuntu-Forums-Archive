---
title: "Problemas con el arranque del so"
date: 2012-01-03
forum: Software
---

### Post by morales.oscardavid on 2012-01-03
Buenas gente! es la primera vez que publico un comentario acá.
Soy novato en esto de linux, aunq tengo conocimientos básicos, los q me dieron en la facultad (:

Instalé en el día de ayer Ubuntu 11.10 Desktop y tengo un problema cuando enciendo la compu, se queda la pantalla lila, como si no arrancará el selector de S.O.
entonces la reinicio y todo bien...

alguien sabrá darme una solucion?? 

desde ya muchas gracias!! :)

---

### Post by aromo on 2012-01-03
Cuando la enciendes por primera vez se ve Ubuntu y unos puntos por debajo? o no?

Si lo hace quiere decir que si esta leyendo el boot sector.  Mira las ultimas lineas de /etc/messages.  P.Ej: tail -20 /etc/messages
te muestra las ultimas 20 lineas.

Yo estoy adivinando pero creo que puede tener algo que ver con el Kernel con que esta tratando de arrancar.

---

### Post by guillermolisi on 2012-01-03
Para tener una idea mas o menos certera de lo que puede estar sucediendo, lo mas aconsejado es leer los logs.
Si nos mostras los contenidos de /var/log/dmesg y /var/log/xorg.0.log es probable que podamos ayudarte mejor.

Por otra parte, despues de la instalacion, actualizaste el sistema completo ?

Si aun no lo hiciste, procede y volve a probar. Luego nos contas que tal te fue.

---

### Post by morales.oscardavid on 2012-01-03
Aromo, cuando la enciendo, despues de la pantalla de opciones de la placa (boot select y demas) aparece directamente la pantalla lila sin nada, reinicio y arranca normal.

[[COLOR=#339900]****[/COLOR]]("http://ubuntuforums.org/member.php?u=299461")guillermolisi, si, el sistema está actualizado. a la vdd no se leer mucho un log, pero aca va a ver que si me dan una mano
ese es /var/log/dmesg decime si posteo el otro, xq son super largos

Muchas gracias!!

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.0.0-14-generic (buildd@allspice) (gcc version 4.6.1 (Ubuntu/Linaro 4.6.1-9ubuntu3) ) #23-Ubuntu SMP Mon Nov 21 20:28:43 UTC 2011 (Ubuntu 3.0.0-14.23-generic 3.0.9)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-14-generic root=UUID=608b3374-3707-45d1-ae7e-215e34ac347a ro quiet splash vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009ec00 (usable)
[    0.000000]  BIOS-e820: 000000000009ec00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000cfe90000 (usable)
[    0.000000]  BIOS-e820: 00000000cfe90000 - 00000000cfea8000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000cfea8000 - 00000000cfed0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000cfed0000 - 00000000cff00000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff700000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000130000000 (usable)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI present.
[    0.000000] DMI: System manufacturer System Product Name/M4A77T/USB3, BIOS 0502    08/19/2010
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] No AGP bridge found
[    0.000000] last_pfn = 0x130000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000000 mask FFFF80000000 write-back
[    0.000000]   1 base 000080000000 mask FFFFC0000000 write-back
[    0.000000]   2 base 0000C0000000 mask FFFFF0000000 write-back
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] TOM2: 0000000130000000 aka 4864M
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 00000000d0000000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0xcfe90 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [ffff8800000ff780] ff780
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] Base memory trampoline at [ffff880000099000] 99000 size 20480
[    0.000000] Using GB pages for direct mapping
[    0.000000] init_memory_mapping: 0000000000000000-00000000cfe90000
[    0.000000]  0000000000 - 00c0000000 page 1G
[    0.000000]  00c0000000 - 00cfe00000 page 2M
[    0.000000]  00cfe00000 - 00cfe90000 page 4k
[    0.000000] kernel direct mapping tables up to cfe90000 @ 1fffd000-20000000
[    0.000000] init_memory_mapping: 0000000100000000-0000000130000000
[    0.000000]  0100000000 - 0130000000 page 2M
[    0.000000] kernel direct mapping tables up to 130000000 @ cfe8e000-cfe90000
[    0.000000] RAMDISK: 365b0000 - 372d0000
[    0.000000] ACPI: RSDP 00000000000fb730 00024 (v02 ACPIAM)
[    0.000000] ACPI: XSDT 00000000cfe90100 0005C (v01 081910 XSDT1957 20100819 MSFT 00000097)
[    0.000000] ACPI: FACP 00000000cfe90290 000F4 (v03 081910 FACP1957 20100819 MSFT 00000097)
[    0.000000] ACPI Warning: Optional field Pm2ControlBlock has zero address or length: 0x0000000000000000/0x1 (20110413/tbfadt-560)
[    0.000000] ACPI: DSDT 00000000cfe90450 0D820 (v01  A1655 A1655001 00000001 INTL 20060113)
[    0.000000] ACPI: FACS 00000000cfea8000 00040
[    0.000000] ACPI: APIC 00000000cfe90390 0007C (v01 081910 APIC1957 20100819 MSFT 00000097)
[    0.000000] ACPI: MCFG 00000000cfe90410 0003C (v01 081910 OEMMCFG  20100819 MSFT 00000097)
[    0.000000] ACPI: OEMB 00000000cfea8040 00072 (v01 081910 OEMB1957 20100819 MSFT 00000097)
[    0.000000] ACPI: SRAT 00000000cfe9f650 000E8 (v01 AMD    FAM_F_10 00000002 AMD  00000001)
[    0.000000] ACPI: HPET 00000000cfe9f740 00038 (v01 081910 OEMHPET  20100819 MSFT 00000097)
[    0.000000] ACPI: SSDT 00000000cfe9f780 0088C (v01 A M I  POWERNOW 00000001 AMD  00000001)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] SRAT: PXM 0 -> APIC 0x00 -> Node 0
[    0.000000] SRAT: PXM 0 -> APIC 0x01 -> Node 0
[    0.000000] SRAT: PXM 0 -> APIC 0x02 -> Node 0
[    0.000000] SRAT: PXM 0 -> APIC 0x03 -> Node 0
[    0.000000] SRAT: Node 0 PXM 0 0-a0000
[    0.000000] SRAT: Node 0 PXM 0 100000-d0000000
[    0.000000] SRAT: Node 0 PXM 0 100000000-130000000
[    0.000000] NUMA: Node 0 [0,a0000) + [100000,d0000000) -> [0,d0000000)
[    0.000000] NUMA: Node 0 [0,d0000000) + [100000000,130000000) -> [0,130000000)
[    0.000000] Initmem setup node 0 0000000000000000-0000000130000000
[    0.000000]   NODE_DATA [000000012fffb000 - 000000012fffffff]
[    0.000000]  [ffffea0000000000-ffffea00043fffff] PMD -> [ffff88012b600000-ffff88012effffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00130000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009e
[    0.000000]     0: 0x00000100 -> 0x000cfe90
[    0.000000]     0: 0x00100000 -> 0x00130000
[    0.000000] On node 0 totalpages: 1048094
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 5 pages reserved
[    0.000000]   DMA zone: 3921 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 833224 pages, LIFO batch:31
[    0.000000]   Normal zone: 2688 pages used for memmap
[    0.000000]   Normal zone: 193920 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x84] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x85] disabled)
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8300 base: 0xfed00000
[    0.000000] SMP: Allowing 6 CPUs, 2 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 000000000009f000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e4000
[    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000cfe90000 - 00000000cfea8000
[    0.000000] PM: Registered nosave memory: 00000000cfea8000 - 00000000cfed0000
[    0.000000] PM: Registered nosave memory: 00000000cfed0000 - 00000000cff00000
[    0.000000] PM: Registered nosave memory: 00000000cff00000 - 00000000ff700000
[    0.000000] PM: Registered nosave memory: 00000000ff700000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at cff00000 (gap: cff00000:2f800000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:6 nr_node_ids:1
[    0.000000] PERCPU: Embedded 27 pages/cpu @ffff88012fc00000 s79616 r8192 d22784 u262144
[    0.000000] pcpu-alloc: s79616 r8192 d22784 u262144 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 - - 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1031065
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.0.0-14-generic root=UUID=608b3374-3707-45d1-ae7e-215e34ac347a ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Node 0: aperture @ c4000000 size 32 MB
[    0.000000] Aperture pointing to e820 RAM. Ignoring.
[    0.000000] Your BIOS doesn't leave a aperture memory hole
[    0.000000] Please enable the IOMMU option in the BIOS setup
[    0.000000] This costs you 64 MB of RAM
[    0.000000] Mapping aperture over 65536 KB of RAM @ c4000000
[    0.000000] PM: Registered nosave memory: 00000000c4000000 - 00000000c8000000
[    0.000000] Memory: 3973816k/4980736k available (6109k kernel code, 788360k absent, 218560k reserved, 4876k data, 984k init)
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=6, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:16640 nr_irqs:728 16
[    0.000000] Extended CMOS year: 2000
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 33554432 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 3214.201 MHz processor.
[    0.004003] Calibrating delay loop (skipped), value calculated using timer frequency.. 6428.40 BogoMIPS (lpj=12856804)
[    0.004007] pid_max: default: 32768 minimum: 301
[    0.004027] Security Framework initialized
[    0.004038] AppArmor: AppArmor initialized
[    0.004040] Yama: becoming mindful.
[    0.004343] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.008231] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.008843] Mount-cache hash table entries: 256
[    0.008942] Initializing cgroup subsys cpuacct
[    0.008946] Initializing cgroup subsys memory
[    0.008953] Initializing cgroup subsys devices
[    0.008954] Initializing cgroup subsys freezer
[    0.008956] Initializing cgroup subsys net_cls
[    0.008957] Initializing cgroup subsys blkio
[    0.008962] Initializing cgroup subsys perf_event
[    0.008983] tseg: 0000000000
[    0.008993] CPU: Physical Processor ID: 0
[    0.008994] CPU: Processor Core ID: 0
[    0.008996] mce: CPU supports 6 MCE banks
[    0.010106] ACPI: Core revision 20110413
[    0.016009] ftrace: allocating 25647 entries in 101 pages
[    0.020348] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.061520] CPU0: AMD Phenom(tm) II X4 955 Processor stepping 02
[    0.064003] Performance Events: AMD PMU driver.
[    0.064003] ... version:                0
[    0.064003] ... bit width:              48
[    0.064003] ... generic registers:      4
[    0.064003] ... value mask:             0000ffffffffffff
[    0.064003] ... max period:             00007fffffffffff
[    0.064003] ... fixed-purpose events:   0
[    0.064003] ... event mask:             000000000000000f
[    0.064003] Booting Node   0, Processors  #1
[    0.064003] smpboot cpu 1: start_ip = 99000
[    0.152059]  #2
[    0.152060] smpboot cpu 2: start_ip = 99000
[    0.244061]  #3
[    0.244062] smpboot cpu 3: start_ip = 99000
[    0.336024] Brought up 4 CPUs
[    0.336026] Total of 4 processors activated (25714.50 BogoMIPS).
[    0.338383] devtmpfs: initialized
[    0.338383] PM: Registering ACPI NVS region at cfea8000 (163840 bytes)
[    0.338383] print_constraints: dummy: 
[    0.338383] Time: 19:28:05  Date: 01/02/12
[    0.338383] NET: Registered protocol family 16
[    0.338383] node 0 link 0: io port [1000, ffffff]
[    0.338383] TOM: 00000000d0000000 aka 3328M
[    0.338383] Fam 10h mmconf [e0000000, efffffff]
[    0.338383] node 0 link 0: mmio [e0000000, efffffff] ==> none
[    0.338383] node 0 link 0: mmio [f0000000, ffffffff]
[    0.338383] node 0 link 0: mmio [a0000, bffff]
[    0.338383] node 0 link 0: mmio [d0000000, dfffffff]
[    0.338383] TOM2: 0000000130000000 aka 4864M
[    0.338383] bus: [00, 07] on node 0 link 0
[    0.338383] bus: 00 index 0 [io  0x0000-0xffff]
[    0.338383] bus: 00 index 1 [mem 0xf0000000-0xffffffff]
[    0.338383] bus: 00 index 2 [mem 0x000a0000-0x000bffff]
[    0.338383] bus: 00 index 3 [mem 0xd0000000-0xdfffffff]
[    0.338383] bus: 00 index 4 [mem 0x130000000-0xfcffffffff]
[    0.338383] Extended Config Space enabled on 1 nodes
[    0.338383] ACPI: bus type pci registered
[    0.338383] Trying to unpack rootfs image as initramfs...
[    0.338383] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.338383] PCI: not using MMCONFIG
[    0.338383] PCI: Using configuration type 1 for base access
[    0.338383] PCI: Using configuration type 1 for extended access
[    0.340290] bio: create slab <bio-0> at 0
[    0.340816] ACPI: EC: Look up EC in DSDT
[    0.341961] ACPI: Executed 3 blocks of module-level executable AML code
[    0.416280] ACPI: Interpreter enabled
[    0.416285] ACPI: (supports S0 S1 S3 S4 S5)
[    0.416302] ACPI: Using IOAPIC for interrupt routing
[    0.416321] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.416821] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in ACPI motherboard resources
[    0.525785] Freeing initrd memory: 13440k freed
[    0.560667] ACPI: No dock devices found.
[    0.560670] HEST: Table not found.
[    0.560673] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.560733] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.560840] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7]
[    0.560842] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff]
[    0.560844] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.560845] pci_root PNP0A03:00: host bridge window [mem 0x000d0000-0x000dffff]
[    0.560847] pci_root PNP0A03:00: host bridge window [mem 0xcff00000-0xdfffffff]
[    0.560848] pci_root PNP0A03:00: host bridge window [mem 0xf0000000-0xfebfffff]
[    0.560859] pci 0000:00:00.0: [1002:5957] type 0 class 0x000600
[    0.560892] pci 0000:00:02.0: [1002:5978] type 1 class 0x000604
[    0.560912] pci 0000:00:02.0: PME# supported from D0 D3hot D3cold
[    0.560915] pci 0000:00:02.0: PME# disabled
[    0.560926] pci 0000:00:04.0: [1002:597a] type 1 class 0x000604
[    0.560946] pci 0000:00:04.0: PME# supported from D0 D3hot D3cold
[    0.560948] pci 0000:00:04.0: PME# disabled
[    0.560963] pci 0000:00:0a.0: [1002:597f] type 1 class 0x000604
[    0.560982] pci 0000:00:0a.0: PME# supported from D0 D3hot D3cold
[    0.560984] pci 0000:00:0a.0: PME# disabled
[    0.561007] pci 0000:00:11.0: [1002:4390] type 0 class 0x000101
[    0.561025] pci 0000:00:11.0: reg 10: [io  0xb000-0xb007]
[    0.561034] pci 0000:00:11.0: reg 14: [io  0xa000-0xa003]
[    0.561043] pci 0000:00:11.0: reg 18: [io  0x9000-0x9007]
[    0.561051] pci 0000:00:11.0: reg 1c: [io  0x8000-0x8003]
[    0.561060] pci 0000:00:11.0: reg 20: [io  0x7000-0x700f]
[    0.561069] pci 0000:00:11.0: reg 24: [mem 0xfbbffc00-0xfbbfffff]
[    0.561088] pci 0000:00:11.0: set SATA to AHCI mode
[    0.561120] pci 0000:00:12.0: [1002:4397] type 0 class 0x000c03
[    0.561133] pci 0000:00:12.0: reg 10: [mem 0xfbbfe000-0xfbbfefff]
[    0.561191] pci 0000:00:12.1: [1002:4398] type 0 class 0x000c03
[    0.561204] pci 0000:00:12.1: reg 10: [mem 0xfbbfd000-0xfbbfdfff]
[    0.561267] pci 0000:00:12.2: [1002:4396] type 0 class 0x000c03
[    0.561285] pci 0000:00:12.2: reg 10: [mem 0xfbbff800-0xfbbff8ff]
[    0.561350] pci 0000:00:12.2: supports D1 D2
[    0.561352] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
[    0.561355] pci 0000:00:12.2: PME# disabled
[    0.561374] pci 0000:00:13.0: [1002:4397] type 0 class 0x000c03
[    0.561386] pci 0000:00:13.0: reg 10: [mem 0xfbbfc000-0xfbbfcfff]
[    0.561445] pci 0000:00:13.1: [1002:4398] type 0 class 0x000c03
[    0.561457] pci 0000:00:13.1: reg 10: [mem 0xfbbfb000-0xfbbfbfff]
[    0.561521] pci 0000:00:13.2: [1002:4396] type 0 class 0x000c03
[    0.561539] pci 0000:00:13.2: reg 10: [mem 0xfbbff400-0xfbbff4ff]
[    0.561604] pci 0000:00:13.2: supports D1 D2
[    0.561605] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
[    0.561609] pci 0000:00:13.2: PME# disabled
[    0.561630] pci 0000:00:14.0: [1002:4385] type 0 class 0x000c05
[    0.561716] pci 0000:00:14.1: [1002:439c] type 0 class 0x000101
[    0.561731] pci 0000:00:14.1: reg 10: [io  0x0000-0x0007]
[    0.561740] pci 0000:00:14.1: reg 14: [io  0x0000-0x0003]
[    0.561748] pci 0000:00:14.1: reg 18: [io  0x0000-0x0007]
[    0.561757] pci 0000:00:14.1: reg 1c: [io  0x0000-0x0003]
[    0.561765] pci 0000:00:14.1: reg 20: [io  0xff00-0xff0f]
[    0.561811] pci 0000:00:14.2: [1002:4383] type 0 class 0x000403
[    0.561831] pci 0000:00:14.2: reg 10: [mem 0xfbbf4000-0xfbbf7fff 64bit]
[    0.561885] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
[    0.561889] pci 0000:00:14.2: PME# disabled
[    0.561900] pci 0000:00:14.3: [1002:439d] type 0 class 0x000601
[    0.561969] pci 0000:00:14.4: [1002:4384] type 1 class 0x000604
[    0.562006] pci 0000:00:14.5: [1002:4399] type 0 class 0x000c03
[    0.562018] pci 0000:00:14.5: reg 10: [mem 0xfbbfa000-0xfbbfafff]
[    0.562079] pci 0000:00:18.0: [1022:1200] type 0 class 0x000600
[    0.562091] pci 0000:00:18.1: [1022:1201] type 0 class 0x000600
[    0.562100] pci 0000:00:18.2: [1022:1202] type 0 class 0x000600
[    0.562110] pci 0000:00:18.3: [1022:1203] type 0 class 0x000600
[    0.562122] pci 0000:00:18.4: [1022:1204] type 0 class 0x000600
[    0.562163] pci 0000:01:00.0: [1002:68f9] type 0 class 0x000300
[    0.562174] pci 0000:01:00.0: reg 10: [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.562182] pci 0000:01:00.0: reg 18: [mem 0xfbce0000-0xfbcfffff 64bit]
[    0.562188] pci 0000:01:00.0: reg 20: [io  0xc000-0xc0ff]
[    0.562199] pci 0000:01:00.0: reg 30: [mem 0xfbcc0000-0xfbcdffff pref]
[    0.562213] pci 0000:01:00.0: supports D1 D2
[    0.562229] pci 0000:01:00.1: [1002:aa68] type 0 class 0x000403
[    0.562240] pci 0000:01:00.1: reg 10: [mem 0xfbcbc000-0xfbcbffff 64bit]
[    0.562276] pci 0000:01:00.1: supports D1 D2
[    0.568050] pci 0000:00:02.0: PCI bridge to [bus 01-01]
[    0.568055] pci 0000:00:02.0:   bridge window [io  0xc000-0xcfff]
[    0.568058] pci 0000:00:02.0:   bridge window [mem 0xfbc00000-0xfbcfffff]
[    0.568061] pci 0000:00:02.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.568094] pci 0000:02:00.0: [1033:0194] type 0 class 0x000c03
[    0.568112] pci 0000:02:00.0: reg 10: [mem 0xfbdfe000-0xfbdfffff 64bit]
[    0.568167] pci 0000:02:00.0: PME# supported from D0 D3hot D3cold
[    0.568170] pci 0000:02:00.0: PME# disabled
[    0.576051] pci 0000:00:04.0: PCI bridge to [bus 02-02]
[    0.576055] pci 0000:00:04.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.576058] pci 0000:00:04.0:   bridge window [mem 0xfbd00000-0xfbdfffff]
[    0.576061] pci 0000:00:04.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.576094] pci 0000:03:00.0: [10ec:8168] type 0 class 0x000200
[    0.576111] pci 0000:03:00.0: reg 10: [io  0xd800-0xd8ff]
[    0.576130] pci 0000:03:00.0: reg 18: [mem 0xfafff000-0xfaffffff 64bit pref]
[    0.576142] pci 0000:03:00.0: reg 20: [mem 0xfaff8000-0xfaffbfff 64bit pref]
[    0.576153] pci 0000:03:00.0: reg 30: [mem 0xfbef0000-0xfbefffff pref]
[    0.576181] pci 0000:03:00.0: supports D1 D2
[    0.576182] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.576185] pci 0000:03:00.0: PME# disabled
[    0.584053] pci 0000:00:0a.0: PCI bridge to [bus 03-03]
[    0.584057] pci 0000:00:0a.0:   bridge window [io  0xd000-0xdfff]
[    0.584059] pci 0000:00:0a.0:   bridge window [mem 0xfbe00000-0xfbefffff]
[    0.584062] pci 0000:00:0a.0:   bridge window [mem 0xfaf00000-0xfaffffff 64bit pref]
[    0.584095] pci 0000:04:05.0: [1106:3044] type 0 class 0x000c00
[    0.584121] pci 0000:04:05.0: reg 10: [mem 0xfbfff800-0xfbffffff]
[    0.584133] pci 0000:04:05.0: reg 14: [io  0xec00-0xec7f]
[    0.584211] pci 0000:04:05.0: supports D2
[    0.584213] pci 0000:04:05.0: PME# supported from D2 D3hot D3cold
[    0.584217] pci 0000:04:05.0: PME# disabled
[    0.584263] pci 0000:00:14.4: PCI bridge to [bus 04-04] (subtractive decode)
[    0.584266] pci 0000:00:14.4:   bridge window [io  0xe000-0xefff]
[    0.584270] pci 0000:00:14.4:   bridge window [mem 0xfbf00000-0xfbffffff]
[    0.584273] pci 0000:00:14.4:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.584275] pci 0000:00:14.4:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.584277] pci 0000:00:14.4:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.584279] pci 0000:00:14.4:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.584280] pci 0000:00:14.4:   bridge window [mem 0x000d0000-0x000dffff] (subtractive decode)
[    0.584282] pci 0000:00:14.4:   bridge window [mem 0xcff00000-0xdfffffff] (subtractive decode)
[    0.584284] pci 0000:00:14.4:   bridge window [mem 0xf0000000-0xfebfffff] (subtractive decode)
[    0.584297] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.584422] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE2._PRT]
[    0.584441] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE4._PRT]
[    0.584463] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCEA._PRT]
[    0.584492] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0PC._PRT]
[    0.584538]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.584541]  pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
[    0.584542] ACPI _OSC control for PCIe not granted, disabling ASPM
[    0.587101] ACPI: PCI Interrupt Link [LNKA] (IRQs 4 6 7 9 10 *11 12 14 15)
[    0.587128] ACPI: PCI Interrupt Link [LNKB] (IRQs 4 *6 7 9 10 11 12 14 15)
[    0.587153] ACPI: PCI Interrupt Link [LNKC] (IRQs 4 6 7 9 *10 11 12 14 15)
[    0.587176] ACPI: PCI Interrupt Link [LNKD] (IRQs 4 6 7 9 *10 11 12 14 15)
[    0.587200] ACPI: PCI Interrupt Link [LNKE] (IRQs 4 6 7 9 10 *11 12 14 15)
[    0.587226] ACPI: PCI Interrupt Link [LNKF] (IRQs 4 6 7 9 10 11 12 14 15) *0, disabled.
[    0.587250] ACPI: PCI Interrupt Link [LNKG] (IRQs 4 6 7 *9 10 11 12 14 15)
[    0.587274] ACPI: PCI Interrupt Link [LNKH] (IRQs 4 6 7 9 10 11 12 14 15) *0, disabled.
[    0.587344] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.587347] vgaarb: loaded
[    0.587348] vgaarb: bridge control possible 0000:01:00.0
[    0.587465] SCSI subsystem initialized
[    0.587483] libata version 3.00 loaded.
[    0.587483] usbcore: registered new interface driver usbfs
[    0.587483] usbcore: registered new interface driver hub
[    0.587483] usbcore: registered new device driver usb
[    0.587483] PCI: Using ACPI for IRQ routing
[    0.595863] PCI: pci_cache_line_size set to 64 bytes
[    0.595929] reserve RAM buffer: 000000000009ec00 - 000000000009ffff 
[    0.595930] reserve RAM buffer: 00000000cfe90000 - 00000000cfffffff 
[    0.595994] NetLabel: Initializing
[    0.595996] NetLabel:  domain hash size = 128
[    0.595996] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.596006] NetLabel:  unlabeled traffic allowed by default
[    0.596042] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.596045] hpet0: 4 comparators, 32-bit 14.318180 MHz counter
[    0.598072] Switching to clocksource hpet
[    0.598099] Switched to NOHz mode on CPU #0
[    0.598074] Switched to NOHz mode on CPU #1
[    0.598084] Switched to NOHz mode on CPU #2
[    0.598103] Switched to NOHz mode on CPU #3
[    0.600088] AppArmor: AppArmor Filesystem Enabled
[    0.600104] pnp: PnP ACPI init
[    0.600112] ACPI: bus type pnp registered
[    0.600181] pnp 00:00: [bus 00-ff]
[    0.600182] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.600184] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.600186] pnp 00:00: [io  0x0d00-0xffff window]
[    0.600187] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.600189] pnp 00:00: [mem 0x000d0000-0x000dffff window]
[    0.600190] pnp 00:00: [mem 0xcff00000-0xdfffffff window]
[    0.600192] pnp 00:00: [mem 0xf0000000-0xfebfffff window]
[    0.600221] pnp 00:00: Plug and Play ACPI device, IDs PNP0a03 (active)
[    0.600245] pnp 00:01: [dma 4]
[    0.600249] pnp 00:01: [io  0x0000-0x000f]
[    0.600250] pnp 00:01: [io  0x0081-0x0083]
[    0.600252] pnp 00:01: [io  0x0087]
[    0.600253] pnp 00:01: [io  0x0089-0x008b]
[    0.600254] pnp 00:01: [io  0x008f]
[    0.600255] pnp 00:01: [io  0x00c0-0x00df]
[    0.600271] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.600277] pnp 00:02: [io  0x0070-0x0071]
[    0.600285] pnp 00:02: [irq 8]
[    0.600301] pnp 00:02: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.600318] pnp 00:03: [io  0x0060]
[    0.600320] pnp 00:03: [io  0x0064]
[    0.600323] pnp 00:03: [irq 1]
[    0.600341] pnp 00:03: Plug and Play ACPI device, IDs PNP0303 PNP030b (active)
[    0.600359] pnp 00:04: [io  0x0061]
[    0.600374] pnp 00:04: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.600379] pnp 00:05: [io  0x00f0-0x00ff]
[    0.600383] pnp 00:05: [irq 13]
[    0.600398] pnp 00:05: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.600549] pnp 00:06: [io  0x03f8-0x03ff]
[    0.600552] pnp 00:06: [irq 4]
[    0.600554] pnp 00:06: [dma 0 disabled]
[    0.600592] pnp 00:06: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.600784] pnp 00:07: [io  0x0378-0x037f]
[    0.600787] pnp 00:07: [irq 7]
[    0.600788] pnp 00:07: [dma 0 disabled]
[    0.600863] pnp 00:07: Plug and Play ACPI device, IDs PNP0400 (active)
[    0.600918] pnp 00:08: [io  0x0000-0xffffffffffffffff disabled]
[    0.600920] pnp 00:08: [io  0x0290-0x0297]
[    0.600921] pnp 00:08: [io  0x02a0-0x02af]
[    0.600953] system 00:08: [io  0x0290-0x0297] has been reserved
[    0.600955] system 00:08: [io  0x02a0-0x02af] has been reserved
[    0.600957] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.600983] pnp 00:09: [mem 0xfed00000-0xfed003ff]
[    0.601000] pnp 00:09: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.601044] pnp 00:0a: [mem 0xfec00000-0xfec00fff]
[    0.601046] pnp 00:0a: [mem 0xfee00000-0xfee00fff]
[    0.601074] system 00:0a: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.601076] system 00:0a: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.601078] system 00:0a: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.601174] pnp 00:0b: [io  0x0010-0x001f]
[    0.601176] pnp 00:0b: [io  0x0022-0x003f]
[    0.601177] pnp 00:0b: [io  0x0062-0x0063]
[    0.601178] pnp 00:0b: [io  0x0065-0x006f]
[    0.601179] pnp 00:0b: [io  0x0072-0x007f]
[    0.601181] pnp 00:0b: [io  0x0080]
[    0.601182] pnp 00:0b: [io  0x0084-0x0086]
[    0.601183] pnp 00:0b: [io  0x0088]
[    0.601184] pnp 00:0b: [io  0x008c-0x008e]
[    0.601185] pnp 00:0b: [io  0x0090-0x009f]
[    0.601186] pnp 00:0b: [io  0x00a2-0x00bf]
[    0.601187] pnp 00:0b: [io  0x00b1]
[    0.601189] pnp 00:0b: [io  0x00e0-0x00ef]
[    0.601190] pnp 00:0b: [io  0x04d0-0x04d1]
[    0.601191] pnp 00:0b: [io  0x040b]
[    0.601192] pnp 00:0b: [io  0x04d6]
[    0.601193] pnp 00:0b: [io  0x0c00-0x0c01]
[    0.601194] pnp 00:0b: [io  0x0c14]
[    0.601195] pnp 00:0b: [io  0x0c50-0x0c51]
[    0.601197] pnp 00:0b: [io  0x0c52]
[    0.601198] pnp 00:0b: [io  0x0c6c]
[    0.601199] pnp 00:0b: [io  0x0c6f]
[    0.601200] pnp 00:0b: [io  0x0cd0-0x0cd1]
[    0.601201] pnp 00:0b: [io  0x0cd2-0x0cd3]
[    0.601202] pnp 00:0b: [io  0x0cd4-0x0cd5]
[    0.601203] pnp 00:0b: [io  0x0cd6-0x0cd7]
[    0.601204] pnp 00:0b: [io  0x0cd8-0x0cdf]
[    0.601205] pnp 00:0b: [io  0x0b00-0x0b3f]
[    0.601207] pnp 00:0b: [io  0x0800-0x089f]
[    0.601208] pnp 00:0b: [io  0x0000-0xffffffffffffffff disabled]
[    0.601209] pnp 00:0b: [io  0x0b00-0x0b0f]
[    0.601211] pnp 00:0b: [io  0x0b20-0x0b3f]
[    0.601212] pnp 00:0b: [io  0x0900-0x090f]
[    0.601213] pnp 00:0b: [io  0x0910-0x091f]
[    0.601214] pnp 00:0b: [io  0xfe00-0xfefe]
[    0.601215] pnp 00:0b: [io  0x0060-0x005f disabled]
[    0.601217] pnp 00:0b: [io  0x0064-0x0063 disabled]
[    0.601218] pnp 00:0b: [mem 0xcff00000-0xcfffffff]
[    0.601219] pnp 00:0b: [mem 0xffb80000-0xffbfffff]
[    0.601221] pnp 00:0b: [mem 0xfec10000-0xfec1001f]
[    0.601278] system 00:0b: [io  0x04d0-0x04d1] has been reserved
[    0.601280] system 00:0b: [io  0x040b] has been reserved
[    0.601281] system 00:0b: [io  0x04d6] has been reserved
[    0.601283] system 00:0b: [io  0x0c00-0x0c01] has been reserved
[    0.601284] system 00:0b: [io  0x0c14] has been reserved
[    0.601286] system 00:0b: [io  0x0c50-0x0c51] has been reserved
[    0.601287] system 00:0b: [io  0x0c52] has been reserved
[    0.601289] system 00:0b: [io  0x0c6c] has been reserved
[    0.601290] system 00:0b: [io  0x0c6f] has been reserved
[    0.601292] system 00:0b: [io  0x0cd0-0x0cd1] has been reserved
[    0.601294] system 00:0b: [io  0x0cd2-0x0cd3] has been reserved
[    0.601295] system 00:0b: [io  0x0cd4-0x0cd5] has been reserved
[    0.601297] system 00:0b: [io  0x0cd6-0x0cd7] has been reserved
[    0.601298] system 00:0b: [io  0x0cd8-0x0cdf] has been reserved
[    0.601300] system 00:0b: [io  0x0b00-0x0b3f] has been reserved
[    0.601302] system 00:0b: [io  0x0800-0x089f] has been reserved
[    0.601303] system 00:0b: [io  0x0b00-0x0b0f] has been reserved
[    0.601305] system 00:0b: [io  0x0b20-0x0b3f] has been reserved
[    0.601307] system 00:0b: [io  0x0900-0x090f] has been reserved
[    0.601308] system 00:0b: [io  0x0910-0x091f] has been reserved
[    0.601310] system 00:0b: [io  0xfe00-0xfefe] has been reserved
[    0.601312] system 00:0b: [mem 0xcff00000-0xcfffffff] has been reserved
[    0.601314] system 00:0b: [mem 0xffb80000-0xffbfffff] has been reserved
[    0.601316] system 00:0b: [mem 0xfec10000-0xfec1001f] has been reserved
[    0.601318] system 00:0b: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.601337] pnp 00:0c: [mem 0xe0000000-0xefffffff]
[    0.601364] system 00:0c: [mem 0xe0000000-0xefffffff] has been reserved
[    0.601366] system 00:0c: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.604129] pnp 00:0d: [mem 0x00000000-0x0009ffff]
[    0.604134] pnp 00:0d: [mem 0x000c0000-0x000cffff]
[    0.604136] pnp 00:0d: [mem 0x000e0000-0x000fffff]
[    0.604137] pnp 00:0d: [mem 0x00100000-0xcfefffff]
[    0.604139] pnp 00:0d: [mem 0xfec00000-0xffffffff]
[    0.604182] system 00:0d: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.604184] system 00:0d: [mem 0x000c0000-0x000cffff] could not be reserved
[    0.604186] system 00:0d: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.604188] system 00:0d: [mem 0x00100000-0xcfefffff] could not be reserved
[    0.604190] system 00:0d: [mem 0xfec00000-0xffffffff] could not be reserved
[    0.604192] system 00:0d: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.604261] pnp: PnP ACPI: found 14 devices
[    0.604262] ACPI: ACPI bus type pnp unregistered
[    0.609609] PCI: max bus depth: 1 pci_try_num: 2
[    0.609625] pci 0000:00:02.0: PCI bridge to [bus 01-01]
[    0.609628] pci 0000:00:02.0:   bridge window [io  0xc000-0xcfff]
[    0.609630] pci 0000:00:02.0:   bridge window [mem 0xfbc00000-0xfbcfffff]
[    0.609632] pci 0000:00:02.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.609635] pci 0000:00:04.0: PCI bridge to [bus 02-02]
[    0.609637] pci 0000:00:04.0:   bridge window [io  disabled]
[    0.609639] pci 0000:00:04.0:   bridge window [mem 0xfbd00000-0xfbdfffff]
[    0.609641] pci 0000:00:04.0:   bridge window [mem pref disabled]
[    0.609644] pci 0000:00:0a.0: PCI bridge to [bus 03-03]
[    0.609645] pci 0000:00:0a.0:   bridge window [io  0xd000-0xdfff]
[    0.609648] pci 0000:00:0a.0:   bridge window [mem 0xfbe00000-0xfbefffff]
[    0.609650] pci 0000:00:0a.0:   bridge window [mem 0xfaf00000-0xfaffffff 64bit pref]
[    0.609653] pci 0000:00:14.4: PCI bridge to [bus 04-04]
[    0.609655] pci 0000:00:14.4:   bridge window [io  0xe000-0xefff]
[    0.609660] pci 0000:00:14.4:   bridge window [mem 0xfbf00000-0xfbffffff]
[    0.609663] pci 0000:00:14.4:   bridge window [mem pref disabled]
[    0.609677] pci 0000:00:02.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.609681] pci 0000:00:02.0: setting latency timer to 64
[    0.609687] pci 0000:00:04.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.609689] pci 0000:00:04.0: setting latency timer to 64
[    0.609692] pci 0000:00:0a.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.609694] pci 0000:00:0a.0: setting latency timer to 64
[    0.609700] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.609702] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.609704] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.609705] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff]
[    0.609707] pci_bus 0000:00: resource 8 [mem 0xcff00000-0xdfffffff]
[    0.609708] pci_bus 0000:00: resource 9 [mem 0xf0000000-0xfebfffff]
[    0.609710] pci_bus 0000:01: resource 0 [io  0xc000-0xcfff]
[    0.609712] pci_bus 0000:01: resource 1 [mem 0xfbc00000-0xfbcfffff]
[    0.609713] pci_bus 0000:01: resource 2 [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.609715] pci_bus 0000:02: resource 1 [mem 0xfbd00000-0xfbdfffff]
[    0.609717] pci_bus 0000:03: resource 0 [io  0xd000-0xdfff]
[    0.609718] pci_bus 0000:03: resource 1 [mem 0xfbe00000-0xfbefffff]
[    0.609720] pci_bus 0000:03: resource 2 [mem 0xfaf00000-0xfaffffff 64bit pref]
[    0.609722] pci_bus 0000:04: resource 0 [io  0xe000-0xefff]
[    0.609723] pci_bus 0000:04: resource 1 [mem 0xfbf00000-0xfbffffff]
[    0.609725] pci_bus 0000:04: resource 4 [io  0x0000-0x0cf7]
[    0.609727] pci_bus 0000:04: resource 5 [io  0x0d00-0xffff]
[    0.609728] pci_bus 0000:04: resource 6 [mem 0x000a0000-0x000bffff]
[    0.609730] pci_bus 0000:04: resource 7 [mem 0x000d0000-0x000dffff]
[    0.609731] pci_bus 0000:04: resource 8 [mem 0xcff00000-0xdfffffff]
[    0.609733] pci_bus 0000:04: resource 9 [mem 0xf0000000-0xfebfffff]
[    0.609758] NET: Registered protocol family 2
[    0.609867] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.610782] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.613245] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.613550] TCP: Hash tables configured (established 524288 bind 65536)
[    0.613552] TCP reno registered
[    0.613559] UDP hash table entries: 2048 (order: 4, 65536 bytes)
[    0.613586] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
[    0.613693] NET: Registered protocol family 1
[    0.732112] pci 0000:01:00.0: Boot video device
[    0.738920] PCI: CLS 64 bytes, default 64
[    0.740170] PCI-DMA: Disabling AGP.
[    0.740244] PCI-DMA: aperture base @ c4000000 size 65536 KB
[    0.740246] PCI-DMA: using GART IOMMU.
[    0.740248] PCI-DMA: Reserving 64MB of IOMMU area in the AGP aperture
[    0.743799] audit: initializing netlink socket (disabled)
[    0.743813] type=2000 audit(1325532484.736:1): initialized
[    0.765427] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.781417] VFS: Disk quotas dquot_6.5.2
[    0.781458] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.781907] fuse init (API version 7.16)
[    0.781960] msgmni has been set to 7916
[    0.782321] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.782350] io scheduler noop registered
[    0.782351] io scheduler deadline registered
[    0.782377] io scheduler cfq registered (default)
[    0.782499] pcieport 0000:00:02.0: setting latency timer to 64
[    0.782528] pcieport 0000:00:02.0: irq 40 for MSI/MSI-X
[    0.782612] pcieport 0000:00:04.0: setting latency timer to 64
[    0.782629] pcieport 0000:00:04.0: irq 41 for MSI/MSI-X
[    0.782693] pcieport 0000:00:0a.0: setting latency timer to 64
[    0.782710] pcieport 0000:00:0a.0: irq 42 for MSI/MSI-X
[    0.782759] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.782774] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.782854] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.782858] ACPI: Power Button [PWRB]
[    0.782884] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.782886] ACPI: Power Button [PWRF]
[    0.782903] ACPI: acpi_idle registered with cpuidle
[    0.972301] ERST: Table is not found!
[    0.972343] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.992785] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.025427] 00:06: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.025651] Linux agpgart interface v0.103
[    1.026281] brd: module loaded
[    1.026560] loop: module loaded
[    1.026716] pata_acpi 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.026737] pata_acpi 0000:00:14.1: setting latency timer to 64
[    1.026983] Fixed MDIO Bus: probed
[    1.026998] PPP generic driver version 2.4.2
[    1.027025] tun: Universal TUN/TAP device driver, 1.6
[    1.027027] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.027076] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.027119] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.027138] ehci_hcd 0000:00:12.2: EHCI Host Controller
[    1.027170] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
[    1.027179] ehci_hcd 0000:00:12.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    1.027202] ehci_hcd 0000:00:12.2: debug port 1
[    1.027220] ehci_hcd 0000:00:12.2: irq 17, io mem 0xfbbff800
[    1.036033] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00
[    1.036116] hub 1-0:1.0: USB hub found
[    1.036119] hub 1-0:1.0: 6 ports detected
[    1.036245] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.036255] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    1.036277] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
[    1.036283] ehci_hcd 0000:00:13.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    1.036301] ehci_hcd 0000:00:13.2: debug port 1
[    1.036319] ehci_hcd 0000:00:13.2: irq 19, io mem 0xfbbff400
[    1.048033] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    1.048107] hub 2-0:1.0: USB hub found
[    1.048110] hub 2-0:1.0: 6 ports detected
[    1.048173] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.048236] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.048249] ohci_hcd 0000:00:12.0: OHCI Host Controller
[    1.048270] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 3
[    1.048291] ohci_hcd 0000:00:12.0: irq 16, io mem 0xfbbfe000
[    1.108086] hub 3-0:1.0: USB hub found
[    1.108092] hub 3-0:1.0: 3 ports detected
[    1.108216] ohci_hcd 0000:00:12.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.108226] ohci_hcd 0000:00:12.1: OHCI Host Controller
[    1.108251] ohci_hcd 0000:00:12.1: new USB bus registered, assigned bus number 4
[    1.108264] ohci_hcd 0000:00:12.1: irq 16, io mem 0xfbbfd000
[    1.168078] hub 4-0:1.0: USB hub found
[    1.168083] hub 4-0:1.0: 3 ports detected
[    1.168207] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.168218] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    1.168241] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 5
[    1.168261] ohci_hcd 0000:00:13.0: irq 18, io mem 0xfbbfc000
[    1.228077] hub 5-0:1.0: USB hub found
[    1.228082] hub 5-0:1.0: 3 ports detected
[    1.228205] ohci_hcd 0000:00:13.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.228216] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    1.228237] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 6
[    1.228250] ohci_hcd 0000:00:13.1: irq 18, io mem 0xfbbfb000
[    1.288079] hub 6-0:1.0: USB hub found
[    1.288085] hub 6-0:1.0: 3 ports detected
[    1.288208] ohci_hcd 0000:00:14.5: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.288220] ohci_hcd 0000:00:14.5: OHCI Host Controller
[    1.288243] ohci_hcd 0000:00:14.5: new USB bus registered, assigned bus number 7
[    1.288257] ohci_hcd 0000:00:14.5: irq 18, io mem 0xfbbfa000
[    1.348076] hub 7-0:1.0: USB hub found
[    1.348081] hub 7-0:1.0: 2 ports detected
[    1.348146] uhci_hcd: USB Universal Host Controller Interface driver
[    1.348193] i8042: PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    1.348195] i8042: PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    1.348311] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.348370] mousedev: PS/2 mouse device common for all mice
[    1.348438] rtc_cmos 00:02: RTC can wake from S4
[    1.348507] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    1.348528] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    1.348587] device-mapper: uevent: version 1.0.3
[    1.348629] device-mapper: ioctl: 4.20.0-ioctl (2011-02-02) initialised: [email]dm-devel@redhat.com[/email]
[    1.348634] cpuidle: using governor ladder
[    1.348635] cpuidle: using governor menu
[    1.348636] EFI Variables Facility v0.08 2004-May-17
[    1.348777] TCP cubic registered
[    1.348854] NET: Registered protocol family 10
[    1.349168] NET: Registered protocol family 17
[    1.349178] Registering the dns_resolver key type
[    1.349233] PM: Hibernation image not present or could not be loaded.
[    1.349243] registered taskstats version 1
[    1.361462]   Magic number: 12:60:495
[    1.361549] rtc_cmos 00:02: setting system clock to 2012-01-02 19:28:06 UTC (1325532486)
[    1.361564] powernow-k8: Found 1 AMD Phenom(tm) II X4 955 Processor (4 cpu cores) (version 2.20.00)
[    1.361590] powernow-k8:    0 : pstate 0 (3200 MHz)
[    1.361591] powernow-k8:    1 : pstate 1 (2500 MHz)
[    1.361593] powernow-k8:    2 : pstate 2 (2100 MHz)
[    1.361594] powernow-k8:    3 : pstate 3 (800 MHz)
[    1.362105] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.362107] EDD information not available.
[    1.363275] Freeing unused kernel memory: 984k freed
[    1.363450] Write protecting the kernel read-only data: 10240k
[    1.363614] Freeing unused kernel memory: 16k freed
[    1.367031] Freeing unused kernel memory: 1396k freed
[    1.370263] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[    1.378381] udevd[125]: starting version 173
[    1.394744] xhci_hcd 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.394770] xhci_hcd 0000:02:00.0: setting latency timer to 64
[    1.394773] xhci_hcd 0000:02:00.0: xHCI Host Controller
[    1.394836] xhci_hcd 0000:02:00.0: new USB bus registered, assigned bus number 8
[    1.394953] xhci_hcd 0000:02:00.0: irq 16, io mem 0xfbdfe000
[    1.395002] xhci_hcd 0000:02:00.0: irq 43 for MSI/MSI-X
[    1.395007] xhci_hcd 0000:02:00.0: irq 44 for MSI/MSI-X
[    1.395010] xhci_hcd 0000:02:00.0: irq 45 for MSI/MSI-X
[    1.395013] xhci_hcd 0000:02:00.0: irq 46 for MSI/MSI-X
[    1.395016] xhci_hcd 0000:02:00.0: irq 47 for MSI/MSI-X
[    1.395153] xHCI xhci_add_endpoint called for root hub
[    1.395155] xHCI xhci_check_bandwidth called for root hub
[    1.395179] hub 8-0:1.0: USB hub found
[    1.395185] hub 8-0:1.0: 2 ports detected
[    1.395234] xhci_hcd 0000:02:00.0: xHCI Host Controller
[    1.395257] xhci_hcd 0000:02:00.0: new USB bus registered, assigned bus number 9
[    1.398351] xHCI xhci_add_endpoint called for root hub
[    1.398352] xHCI xhci_check_bandwidth called for root hub
[    1.398374] hub 9-0:1.0: USB hub found
[    1.398379] hub 9-0:1.0: 2 ports detected
[    1.405611] ahci 0000:00:11.0: version 3.0
[    1.405646] ahci 0000:00:11.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    1.405789] ahci 0000:00:11.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[    1.405792] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part ccc 
[    1.406349] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.406368] r8169 0000:03:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.406392] r8169 0000:03:00.0: setting latency timer to 64
[    1.406433] r8169 0000:03:00.0: irq 48 for MSI/MSI-X
[    1.406747] r8169 0000:03:00.0: eth0: RTL8168d/8111d at 0xffffc90000660000, 20:cf:30:f3:fe:87, XID 083000c0 IRQ 48
[    1.409016] scsi0 : ahci
[    1.410385] scsi1 : ahci
[    1.410863] scsi2 : ahci
[    1.411590] scsi3 : ahci
[    1.411674] ata1: SATA max UDMA/133 abar m1024@0xfbbffc00 port 0xfbbffd00 irq 22
[    1.411677] ata2: SATA max UDMA/133 abar m1024@0xfbbffc00 port 0xfbbffd80 irq 22
[    1.411680] ata3: SATA max UDMA/133 abar m1024@0xfbbffc00 port 0xfbbffe00 irq 22
[    1.411683] ata4: SATA max UDMA/133 abar m1024@0xfbbffc00 port 0xfbbffe80 irq 22
[    1.413440] scsi4 : pata_atiixp
[    1.414954] scsi5 : pata_atiixp
[    1.415398] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xff00 irq 14
[    1.415401] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xff08 irq 15
[    1.564028] usb 5-1: new low speed USB device number 2 using ohci_hcd
[    1.728078] ata2: SATA link down (SStatus 0 SControl 300)
[    1.732047] ata4: SATA link down (SStatus 0 SControl 300)
[    1.740051] Refined TSC clocksource calibration: 3214.322 MHz.
[    1.740056] Switching to clocksource tsc
[    1.761216] input: Genius 2.4G Wireless Mouse and Keyboard as /devices/pci0000:00/0000:00:13.0/usb5/5-1/5-1:1.0/input/input3
[    1.761267] generic-usb 0003:0458:00AE.0001: input,hidraw0: USB HID v1.00 Keyboard [Genius 2.4G Wireless Mouse and Keyboard] on usb-0000:00:13.0-1/input0
[    1.770292] input: Genius 2.4G Wireless Mouse and Keyboard as /devices/pci0000:00/0000:00:13.0/usb5/5-1/5-1:1.1/input/input4
[    1.770348] generic-usb 0003:0458:00AE.0002: input,hidraw1: USB HID v1.00 Mouse [Genius 2.4G Wireless Mouse and Keyboard] on usb-0000:00:13.0-1/input1
[    1.770361] usbcore: registered new interface driver usbhid
[    1.770362] usbhid: USB HID core driver
[    1.904034] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.904060] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.905506] ata3.00: ATAPI: TSSTcorp CDDVDW SH-S223C, SB05, max MWDMA2
[    1.905923] ata1.00: ATA-8: WDC WD5000AAKX-001CA0, 15.01H15, max UDMA/133
[    1.905925] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.907020] ata1.00: configured for UDMA/133
[    1.907148] scsi 0:0:0:0: Direct-Access     ATA      WDC WD5000AAKX-0 15.0 PQ: 0 ANSI: 5
[    1.907248] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.907283] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    1.907363] sd 0:0:0:0: [sda] Write Protect is off
[    1.907366] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.907389] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.944994]  sda: sda1 sda2 < sda5 >
[    1.945247] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.706257] ata3.00: configured for PIO4
[    3.508185] scsi 2:0:0:0: CD-ROM            TSSTcorp CDDVDW SH-S223C  SB05 PQ: 0 ANSI: 5
[    3.511364] sr0: scsi3-mmc drive: 52x/52x writer dvd-ram cd/rw xa/form2 cdda tray
[    3.511366] cdrom: Uniform CD-ROM driver Revision: 3.20
[    3.511440] sr 2:0:0:0: Attached scsi CD-ROM sr0
[    3.511478] sr 2:0:0:0: Attached scsi generic sg1 type 5
[    3.513121] firewire_ohci 0000:04:05.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    3.576094] firewire_ohci: Added fw-ohci device 0000:04:05.0, OHCI v1.10, 4 IR + 8 IT contexts, quirks 0x11
[    3.757118] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    4.076085] firewire_core: created device fw0: GUID 0139407040100060, S400
[   33.792044] ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[   33.792047] ata3.00: failed command: IDENTIFY PACKET DEVICE
[   33.792051] ata3.00: cmd a1/00:01:00:00:00/00:00:00:00:00/00 tag 0 pio 512 in
[   33.792052]          res 40/00:03:00:00:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
[   33.792054] ata3.00: status: { DRDY }
[   33.792057] ata3: hard resetting link
[   34.284026] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   35.086240] ata3.00: configured for PIO4
[   35.886867] ata3: EH complete
[   37.806539] Adding 4191228k swap on /dev/sda5.  Priority:-1 extents:1 across:4191228k 
[   38.012835] udevd[389]: starting version 173
[   39.640903] parport_pc 00:07: reported by Plug and Play ACPI
[   39.640955] parport0: PC-style at 0x378, irq 7 [PCSPP]
[   39.702078] wmi: Mapper loaded
[   39.775653] lp0: using parport0 (interrupt-driven).
[   39.819992] ppdev: user-space parallel port driver
[   40.226769] type=1400 audit(1325532525.360:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=630 comm="apparmor_parser"
[   40.226782] type=1400 audit(1325532525.360:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=595 comm="apparmor_parser"
[   40.227096] type=1400 audit(1325532525.360:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=630 comm="apparmor_parser"
[   40.227112] type=1400 audit(1325532525.360:5): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=595 comm="apparmor_parser"
[   40.227305] type=1400 audit(1325532525.360:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=630 comm="apparmor_parser"
[   40.227326] type=1400 audit(1325532525.360:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=595 comm="apparmor_parser"
[   40.591894] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0xb00, revision 0
[   40.630112] MCE: In-kernel MCE decoding enabled.
[   40.673377] EDAC MC: Ver: 2.1.0
[   40.685890] SP5100 TCO timer: SP5100 TCO WatchDog Timer Driver v0.01
[   40.685951] SP5100 TCO timer: mmio address 0xfec000f0 already in use
[   40.984963] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   40.984966] Disabling lock debugging due to kernel taint
[   41.005107] AMD64 EDAC driver v3.4.0
[   41.005212] EDAC amd64: DRAM ECC disabled.
[   41.005217] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
[   41.005218]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
[   41.005219]  (Note that use of the override may cause unknown side effects.)
[   41.017782] [fglrx] Maximum main memory to use for locked dma buffers: 3798 MBytes.
[   41.017838] [fglrx]   vendor: 1002 device: 68f9 count: 1
[   41.018143] [fglrx] ioport: bar 4, base 0xc000, size: 0x100
[   41.018152] pci 0000:01:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   41.018156] pci 0000:01:00.0: setting latency timer to 64
[   41.018432] [fglrx] Kernel PAT support is enabled
[   41.018448] [fglrx] module loaded - fglrx 8.88.7 [Jul 28 2011] with 1 minors
[   41.224322] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   41.772685] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   41.845834] HDA Intel 0000:01:00.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[   41.845900] HDA Intel 0000:01:00.1: irq 49 for MSI/MSI-X
[   41.845921] HDA Intel 0000:01:00.1: setting latency timer to 64
[   41.921965] HDMI status: Pin=3 Presence_Detect=0 ELD_Valid=0
[   41.922056] input: HD-Audio Generic HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card1/input5
[   44.099618] type=1400 audit(1325532529.232:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=973 comm="apparmor_parser"
[   44.099958] type=1400 audit(1325532529.232:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=973 comm="apparmor_parser"
[   44.100186] type=1400 audit(1325532529.236:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=973 comm="apparmor_parser"
[   44.537207] type=1400 audit(1325532529.672:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm-guest-session-wrapper" pid=972 comm="apparmor_parser"
[   45.293228] r8169 0000:03:00.0: eth0: link down
[   45.293234] r8169 0000:03:00.0: eth0: link down
[   45.293604] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   45.424143] init: failsafe main process (925) killed by TERM signal
[   45.525163] init: apport pre-start process (1022) terminated with status 1
[   45.526731] init: apport post-stop process (1040) terminated with status 1

---

### Post by mama21mama on 2012-01-03
La 11.10 tiene un bug (bugaso)

[bug #811441]("http://blog.mamalibre.com.ar/post/solved-ubuntu-1110-oneiric-ocelot-upgrade-waiting-network-configuration")

Tal vez entrando en modo recovery y haciendo los pasos esos tengas mas chance. No se fijate.... proba.

Saludos

---

