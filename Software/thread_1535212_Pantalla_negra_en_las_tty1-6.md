---
title: "Pantalla negra en las tty1-6"
date: 2010-07-20
forum: Software
---

### Post by jc_jc on 2010-07-20
Pantalla negra en las tty1-6 con el cursor parpadeando.
No puedo logarme ni nada.
Cambio a modo gráfico (alt+f7) y perfecto.
SO: Ubuntu 10.04 (2.6.32)
Gnome 2.30.2
Cuando cambio a la tty1 (ctrl+alt+f1) lo único que me aparece es:
resume: libgcript version: 1.4.4
_
y debajo el cursor parpadeando y en las tty2 ... tty6 sólo el cursor parpadeante.
Repito cambio a modo gráfico y todo va perfecto.
Probé a cambiar la resolución (siguiendo un blog muy interesante [http://niblanconinegro.es/blog/2008/08/cambiar-la-resolucion-de-las-tty-en-ubuntu/](http://niblanconinegro.es/blog/2008/08/cambiar-la-resolucion-de-las-tty-en-ubuntu/) ):
1. /etc/initramfs-tools/modules
2. /etc/modprobe.d/blacklist-framebuffer
3. /boot/grub/menu.lst
... pero sigo sin poder logarme en las tty1-6
Parece que alguien dio con la solución en [www.ubuntu-es.org/node/37007#comment-85640]("http://www.ubuntu-es.org/node/37007#comment-85640") 
un foro del 2007 pero me quedé con las ganas porque el link de la solución en la segunda página
[http://foros.ubuntu-cl.org/viewtopic.php?t=1391&](http://foros.ubuntu-cl.org/viewtopic.php?t=1391&) ... se me pierde...

Más info:
Comunicado de error tras iniciar terminal modo texto (con pantalla negra...)
Desde el VISOR DE SUCESOS:
En auth.log

Jul 22 12:40:45 jc kernel: [24655.190921] [drm:drm_mode_getfb] *ERROR* invalid framebuffer id

Alguien tiene alguna idea para solucionar esto ???

Diario de abordo
xx días sin poder utilizar las tty1-6
Ultimas maniobras realizadas:
Desde un live CD he chequeado el disco (fsck)
También lo intenté con e2fsck ...  
Ya que usaba el live CD aproveché para darme el gustazo de ver las tty1-6 en correcto funcionamiento...

No es que necesite las tty1-6... pero me fastidia no saber qué es lo que sucedió para que no funcionen correctamente y cómo retornarlas a su natural ser...

... a nadie más le reconcome esta situación???

---

### Post by Patriciologico on 2010-07-21
Hola jc_jc

Te recomiendo leer [http://ubuntuforums.org/showthread.php?t=1319475](http://ubuntuforums.org/showthread.php?t=1319475) ya que ingresas a una comunidad nueva es bueno que sigas el orden que llevamos. Tu post fue movido.

Saludos

---

### Post by Carlos C on 2010-07-24
¿dmesg no te entrega algún otro mensaje de error? ¿Qué tarjeta de video utilizas? ¿Tienes un escritorio extendido? Esto último te lo pregunto ya que con escritorio extendido a un monitor adicional he tenido problemas para ingresar a las tty y he necesitado configurar correctamente mi xorg.conf.

Saludos.

---

### Post by jc_jc on 2010-07-25
> **Carlos C said:**
> ¿dmesg no te entrega algún otro mensaje de error? ¿Qué tarjeta de video utilizas? ¿Tienes un escritorio extendido? Esto último te lo pregunto ya que con escritorio extendido a un monitor adicional he tenido problemas para ingresar a las tty y he necesitado configurar correctamente mi xorg.conf.

Saludos.
Antes que nada, muchas gracias por tu interés.
Te comento:
**¿dmesg no te entrega algún otro mensaje de error?**
        [    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.32-23-generic (buildd@rothera) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #37-Ubuntu SMP Fri Jun 11 07:54:58 UTC 2010 (Ubuntu 2.6.32-23.37-generic 2.6.32.15+drm33.5)
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
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bf4d2000 (usable)
[    0.000000]  BIOS-e820: 00000000bf4d2000 - 00000000bf4dd000 (reserved)
[    0.000000]  BIOS-e820: 00000000bf4dd000 - 00000000bf534000 (usable)
[    0.000000]  BIOS-e820: 00000000bf534000 - 00000000bf537000 (reserved)
[    0.000000]  BIOS-e820: 00000000bf537000 - 00000000bf5bb000 (usable)
[    0.000000]  BIOS-e820: 00000000bf5bb000 - 00000000bf5bf000 (reserved)
[    0.000000]  BIOS-e820: 00000000bf5bf000 - 00000000bf678000 (usable)
[    0.000000]  BIOS-e820: 00000000bf678000 - 00000000bf6bf000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bf6bf000 - 00000000bf700000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000bf700000 - 00000000c0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed20000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.4 present.
[    0.000000] last_pfn = 0xbf678 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0FFFE0000 mask FFFFE0000 write-protect
[    0.000000]   1 base 000000000 mask F80000000 write-back
[    0.000000]   2 base 080000000 mask FC0000000 write-back
[    0.000000]   3 base 0BF800000 mask FFF800000 uncachable
[    0.000000]   4 base 0BF700000 mask FFFF00000 uncachable
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820 update range: 0000000000002000 - 0000000000006000 (usable) ==> (reserved)
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000002000 (usable)
[    0.000000]  modified: 0000000000002000 - 0000000000006000 (reserved)
[    0.000000]  modified: 0000000000006000 - 000000000009fc00 (usable)
[    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000bf4d2000 (usable)
[    0.000000]  modified: 00000000bf4d2000 - 00000000bf4dd000 (reserved)
[    0.000000]  modified: 00000000bf4dd000 - 00000000bf534000 (usable)
[    0.000000]  modified: 00000000bf534000 - 00000000bf537000 (reserved)
[    0.000000]  modified: 00000000bf537000 - 00000000bf5bb000 (usable)
[    0.000000]  modified: 00000000bf5bb000 - 00000000bf5bf000 (reserved)
[    0.000000]  modified: 00000000bf5bf000 - 00000000bf678000 (usable)
[    0.000000]  modified: 00000000bf678000 - 00000000bf6bf000 (ACPI NVS)
[    0.000000]  modified: 00000000bf6bf000 - 00000000bf700000 (ACPI data)
[    0.000000]  modified: 00000000bf700000 - 00000000c0000000 (reserved)
[    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  modified: 00000000fed14000 - 00000000fed1a000 (reserved)
[    0.000000]  modified: 00000000fed1c000 - 00000000fed20000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-00000000377fe000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037400000 page 2M
[    0.000000]  0037400000 - 00377fe000 page 4k
[    0.000000] kernel direct mapping tables up to 377fe000 @ 7000-c000
[    0.000000] RAMDISK: 3780e000 - 37fef151
[    0.000000] Allocated new RAMDISK: 008e0000 - 010c1151
[    0.000000] Move RAMDISK from 000000003780e000 - 0000000037fef150 to 008e0000 - 010c1150
[    0.000000] ACPI: RSDP 000fe020 00024 (v02 HP    )
[    0.000000] ACPI: XSDT bf6fe120 00064 (v01 HPQOEM SLIC-MPC 00000001      01000013)
[    0.000000] ACPI: FACP bf6fd000 000F4 (v04 HP     SPARTAN  00000001 LOHR 00000000)
[    0.000000] ACPI: DSDT bf6f4000 0802F (v01 HP     SPARTAN  00000001 LOHR 00000000)
[    0.000000] ACPI: FACS bf67d000 00040
[    0.000000] ACPI: APIC bf6f3000 00068 (v02 HPQOEM SLIC-MPC 00000001 LOHR 00000000)
[    0.000000] ACPI: HPET bf6f2000 00038 (v01 HPQOEM SLIC-MPC 00000001 LOHR 00000000)
[    0.000000] ACPI: MCFG bf6f1000 0003C (v01 HPQOEM SLIC-MPC 00000001 LOHR 00000000)
[    0.000000] ACPI: ASF! bf6f0000 000A5 (v32 HPQOEM SLIC-MPC 00000001 LOHR 00000000)
[    0.000000] ACPI: SLIC bf6ef000 00176 (v01 HPQOEM SLIC-MPC 00000001 LOHR 00000000)
[    0.000000] ACPI: BOOT bf6ee000 00028 (v01 HPQOEM SLIC-MPC 00000001 LOHR 00000000)
[    0.000000] ACPI: SSDT bf6ed000 004C4 (v01  PmRef    CpuPm 00003000 INTL 20051117)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 2174MB HIGHMEM available.
[    0.000000] 887MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 377fe000
[    0.000000]   low ram: 0 - 377fe000
[    0.000000]   node 0 low ram: 00000000 - 377fe000
[    0.000000]   node 0 bootmap 00008000 - 0000ef00
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00377fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008dbeb8]    TEXT DATA BSS ==> [0000100000 - 00008dbeb8]
[    0.000000]   #4 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #5 [00008dc000 - 00008df194]              BRK ==> [00008dc000 - 00008df194]
[    0.000000]   #6 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
[    0.000000]   #7 [00008e0000 - 00010c1151]      NEW RAMDISK ==> [00008e0000 - 00010c1151]
[    0.000000]   #8 [0000008000 - 000000f000]          BOOTMAP ==> [0000008000 - 000000f000]
[    0.000000] found SMP MP-table at [c00fe270] fe270
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000000 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000377fe
[    0.000000]   HighMem  0x000377fe -> 0x000bf678
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[6] active PFN ranges
[    0.000000]     0: 0x00000000 -> 0x00000002
[    0.000000]     0: 0x00000006 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x000bf4d2
[    0.000000]     0: 0x000bf4dd -> 0x000bf534
[    0.000000]     0: 0x000bf537 -> 0x000bf5bb
[    0.000000]     0: 0x000bf5bf -> 0x000bf678
[    0.000000] On node 0 totalpages: 783873
[    0.000000] free_area_init_node: node 0, pgdat c0798760, node_mem_map c10c3000
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3963 pages, LIFO batch:0
[    0.000000]   Normal zone: 1744 pages used for memmap
[    0.000000]   Normal zone: 221486 pages, LIFO batch:31
[    0.000000]   HighMem zone: 4349 pages used for memmap
[    0.000000]   HighMem zone: 552299 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 0000000000002000 - 0000000000006000
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at c0000000 (gap: c0000000:20000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @c2c00000 s36056 r0 d21288 u2097152
[    0.000000] pcpu-alloc: s36056 r0 d21288 u2097152 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 1 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 777748
[    0.000000] Kernel command line: root=UUID=3e3c3bd2-8587-450a-8bbd-72b7c321bf31 ro quiet splash vga=792
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 15679840 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (000377fe:000bf678)
[    0.000000] Memory: 3077456k/3135968k available (4676k kernel code, 56968k reserved, 2118k data, 660k init, 2226592k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xf7ffe000 - 0xff7fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf77fe000   ( 887 MB)
[    0.000000]       .init : 0xc07a3000 - 0xc0848000   ( 660 kB)
[    0.000000]       .data : 0xc0591293 - 0xc07a2e88   (2118 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0591293   (4676 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] NR_IRQS:2304 nr_irqs:424
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1828.877 MHz processor.
[    0.004006] Calibrating delay loop (skipped), value calculated using timer frequency.. 3657.75 BogoMIPS (lpj=7315508)
[    0.004024] Security Framework initialized
[    0.004047] AppArmor: AppArmor initialized
[    0.004054] Mount-cache hash table entries: 512
[    0.008134] Initializing cgroup subsys ns
[    0.008139] Initializing cgroup subsys cpuacct
[    0.008143] Initializing cgroup subsys memory
[    0.008151] Initializing cgroup subsys devices
[    0.008154] Initializing cgroup subsys freezer
[    0.008157] Initializing cgroup subsys net_cls
[    0.008179] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.008182] CPU: L2 cache: 2048K
[    0.008185] CPU: Physical Processor ID: 0
[    0.008187] CPU: Processor Core ID: 0
[    0.008191] mce: CPU supports 6 MCE banks
[    0.008200] CPU0: Thermal monitoring enabled (TM1)
[    0.008204] using mwait in idle threads.
[    0.008212] Performance Events: Core2 events, Intel PMU driver.
[    0.008221] ... version:                2
[    0.008223] ... bit width:              40
[    0.008225] ... generic registers:      2
[    0.008228] ... value mask:             000000ffffffffff
[    0.008230] ... max period:             000000007fffffff
[    0.008232] ... fixed-purpose events:   3
[    0.008234] ... event mask:             0000000700000003
[    0.008239] Checking 'hlt' instruction... OK.
[    0.026939] ACPI: Core revision 20090903
[    0.040010] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.040015] ftrace: allocating 21776 entries in 43 pages
[    0.044063] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.044440] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.087183] CPU0: Intel(R) Core(TM)2 Duo CPU     T5550  @ 1.83GHz stepping 0d
[    0.088001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.008000] Initializing CPU#1
[    0.008000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.008000] CPU: L2 cache: 2048K
[    0.008000] CPU: Physical Processor ID: 0
[    0.008000] CPU: Processor Core ID: 1
[    0.008000] CPU1: Thermal monitoring enabled (TM1)
[    0.172050] CPU1: Intel(R) Core(TM)2 Duo CPU     T5550  @ 1.83GHz stepping 0d
[    0.172064] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.176020] Brought up 2 CPUs
[    0.176023] Total of 2 processors activated (7315.26 BogoMIPS).
[    0.176511] CPU0 attaching sched-domain:
[    0.176514]  domain 0: span 0-1 level MC
[    0.176517]   groups: 0 1
[    0.176525] CPU1 attaching sched-domain:
[    0.176527]  domain 0: span 0-1 level MC
[    0.176529]   groups: 1 0
[    0.176631] devtmpfs: initialized
[    0.176631] regulator: core version 0.5
[    0.176631] Time: 10:18:41  Date: 07/25/10
[    0.176631] NET: Registered protocol family 16
[    0.176631] Trying to unpack rootfs image as initramfs...
[    0.176631] EISA bus registered
[    0.176631] ACPI: bus type pci registered
[    0.176631] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.176631] PCI: MCFG area at e0000000 reserved in E820
[    0.176631] PCI: Using MMCONFIG for extended config space
[    0.176631] PCI: Using configuration type 1 for base access
[    0.180108] bio: create slab <bio-0> at 0
[    0.181252] ACPI: EC: Look up EC in DSDT
[    0.206029] ACPI: Executed 1 blocks of module-level executable AML code
[    0.207200] ACPI: BIOS _OSI(Linux) query ignored
[    0.232916] ACPI: Interpreter enabled
[    0.232916] ACPI: (supports S0 S3 S4 S5)
[    0.232916] ACPI: Using IOAPIC for interrupt routing
[    0.321873] ACPI: EC: GPE storm detected, transactions will use polling mode
[    0.347252] [Firmware Bug]: ACPI: ACPI brightness control misses _BQC function
[    0.348564] ACPI: EC: GPE = 0x1c, I/O: command/status = 0x66, data = 0x62
[    0.348888] ACPI: No dock devices found.
[    0.349555] ACPI Warning for \_SB_.PCI0._OSC: Parameter count mismatch - ASL declared 5, ACPI requires 4 (20090903/nspredef-336)
[    0.349564] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.349676] pci 0000:00:02.0: reg 10 64bit mmio: [0xd1000000-0xd10fffff]
[    0.349685] pci 0000:00:02.0: reg 18 64bit mmio pref: [0xc0000000-0xcfffffff]
[    0.349691] pci 0000:00:02.0: reg 20 io port: [0x30b0-0x30b7]
[    0.349742] pci 0000:00:02.1: reg 10 64bit mmio: [0xd1100000-0xd11fffff]
[    0.349881] pci 0000:00:1b.0: reg 10 64bit mmio: [0xd2400000-0xd2403fff]
[    0.349953] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.349959] pci 0000:00:1b.0: PME# disabled
[    0.350070] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.350075] pci 0000:00:1c.0: PME# disabled
[    0.350159] pci 0000:00:1d.0: reg 20 io port: [0x3060-0x307f]
[    0.350236] pci 0000:00:1d.1: reg 20 io port: [0x3040-0x305f]
[    0.350312] pci 0000:00:1d.2: reg 20 io port: [0x3020-0x303f]
[    0.350393] pci 0000:00:1d.7: reg 10 32bit mmio: [0xd2404000-0xd24043ff]
[    0.350467] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.350473] pci 0000:00:1d.7: PME# disabled
[    0.350675] pci 0000:00:1f.0: quirk: region 0400-047f claimed by ICH6 ACPI/GPIO/TCO
[    0.350680] pci 0000:00:1f.0: quirk: region 0500-053f claimed by ICH6 GPIO
[    0.350687] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 2 PIO at ff2c (mask 0003)
[    0.350768] pci 0000:00:1f.2: reg 10 io port: [0x30a8-0x30af]
[    0.350777] pci 0000:00:1f.2: reg 14 io port: [0x30bc-0x30bf]
[    0.350786] pci 0000:00:1f.2: reg 18 io port: [0x30a0-0x30a7]
[    0.350796] pci 0000:00:1f.2: reg 1c io port: [0x30b8-0x30bb]
[    0.350805] pci 0000:00:1f.2: reg 20 io port: [0x3090-0x309f]
[    0.350814] pci 0000:00:1f.2: reg 24 io port: [0x3080-0x308f]
[    0.350849] pci 0000:00:1f.2: PME# supported from D3hot
[    0.350855] pci 0000:00:1f.2: PME# disabled
[    0.350887] pci 0000:00:1f.3: reg 10 32bit mmio: [0xd2404400-0xd24044ff]
[    0.350917] pci 0000:00:1f.3: reg 20 io port: [0x3000-0x301f]
[    0.351031] pci 0000:01:00.0: reg 10 64bit mmio: [0xd1300000-0xd130ffff]
[    0.351223] pci 0000:00:1c.0: bridge io port: [0x2000-0x2fff]
[    0.351229] pci 0000:00:1c.0: bridge 32bit mmio: [0xd1300000-0xd23fffff]
[    0.351239] pci 0000:00:1c.0: bridge 64bit mmio pref: [0xd0000000-0xd0ffffff]
[    0.351296] pci 0000:02:01.0: reg 10 io port: [0x1000-0x10ff]
[    0.351307] pci 0000:02:01.0: reg 14 32bit mmio: [0xd1200000-0xd12000ff]
[    0.351377] pci 0000:02:01.0: supports D1 D2
[    0.351380] pci 0000:02:01.0: PME# supported from D1 D2 D3hot D3cold
[    0.351386] pci 0000:02:01.0: PME# disabled
[    0.351460] pci 0000:00:1e.0: transparent bridge
[    0.351466] pci 0000:00:1e.0: bridge io port: [0x1000-0x1fff]
[    0.351472] pci 0000:00:1e.0: bridge 32bit mmio: [0xd1200000-0xd12fffff]
[    0.351497] pci_bus 0000:00: on NUMA node 0
[    0.351502] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.351776] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P32_._PRT]
[    0.351859] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP1._PRT]
[    0.352098] ACPI Warning for \_SB_.PCI0._OSC: Parameter count mismatch - ASL declared 5, ACPI requires 4 (20090903/nspredef-336)
[    0.357878] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 10 *11 12)
[    0.358007] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 9 *10 11 12)
[    0.358134] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 10 *11 12)
[    0.358263] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 10 *11 12)
[    0.358388] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 *11 12)
[    0.358513] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 *11 12)
[    0.358641] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 9 10 *11 12)
[    0.358766] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 9 10 *11 12)
[    0.358900] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.358913] vgaarb: loaded
[    0.359052] SCSI subsystem initialized
[    0.359155] libata version 3.00 loaded.
[    0.359245] usbcore: registered new interface driver usbfs
[    0.359259] usbcore: registered new interface driver hub
[    0.359291] usbcore: registered new device driver usb
[    0.359461] ACPI: WMI: Mapper loaded
[    0.359463] PCI: Using ACPI for IRQ routing
[    0.359647] NetLabel: Initializing
[    0.359650] NetLabel:  domain hash size = 128
[    0.359651] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.359665] NetLabel:  unlabeled traffic allowed by default
[    0.359702] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.359708] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.364024] Switching to clocksource tsc
[    0.366392] AppArmor: AppArmor Filesystem Enabled
[    0.366408] pnp: PnP ACPI init
[    0.366424] ACPI: bus type pnp registered
[    0.401519] Freeing initrd memory: 8068k freed
[    0.436603] pnp 00:01: io resource (0x164e-0x164f) overlaps 0000:00:1e.0 BAR 13 (0x1000-0x1fff), disabling
[    0.437296] pnp: PnP ACPI: found 9 devices
[    0.437299] ACPI: ACPI bus type pnp unregistered
[    0.437304] PnPBIOS: Disabled by ACPI PNP
[    0.437319] system 00:01: ioport range 0x600-0x60f has been reserved
[    0.437322] system 00:01: ioport range 0x610-0x610 has been reserved
[    0.437326] system 00:01: ioport range 0x800-0x80f has been reserved
[    0.437329] system 00:01: ioport range 0x810-0x817 has been reserved
[    0.437332] system 00:01: ioport range 0x400-0x47f has been reserved
[    0.437335] system 00:01: ioport range 0x500-0x53f has been reserved
[    0.437338] system 00:01: ioport range 0xff2c-0xff2f has been reserved
[    0.437343] system 00:01: iomem range 0xe0000000-0xefffffff has been reserved
[    0.437346] system 00:01: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    0.437349] system 00:01: iomem range 0xfed14000-0xfed17fff has been reserved
[    0.437353] system 00:01: iomem range 0xfed18000-0xfed18fff has been reserved
[    0.437356] system 00:01: iomem range 0xfed19000-0xfed19fff has been reserved
[    0.437360] system 00:01: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.437363] system 00:01: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.472127] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:01
[    0.472132] pci 0000:00:1c.0:   IO window: 0x2000-0x2fff
[    0.472140] pci 0000:00:1c.0:   MEM window: 0xd1300000-0xd23fffff
[    0.472146] pci 0000:00:1c.0:   PREFETCH window: 0x000000d0000000-0x000000d0ffffff
[    0.472155] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:02
[    0.472159] pci 0000:00:1e.0:   IO window: 0x1000-0x1fff
[    0.472167] pci 0000:00:1e.0:   MEM window: 0xd1200000-0xd12fffff
[    0.472172] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.472194]   alloc irq_desc for 18 on node -1
[    0.472197]   alloc kstat_irqs on node -1
[    0.472203] pci 0000:00:1c.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.472210] pci 0000:00:1c.0: setting latency timer to 64
[    0.472220] pci 0000:00:1e.0: setting latency timer to 64
[    0.472225] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.472228] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.472231] pci_bus 0000:01: resource 0 io:  [0x2000-0x2fff]
[    0.472234] pci_bus 0000:01: resource 1 mem: [0xd1300000-0xd23fffff]
[    0.472237] pci_bus 0000:01: resource 2 pref mem [0xd0000000-0xd0ffffff]
[    0.472240] pci_bus 0000:02: resource 0 io:  [0x1000-0x1fff]
[    0.472243] pci_bus 0000:02: resource 1 mem: [0xd1200000-0xd12fffff]
[    0.472246] pci_bus 0000:02: resource 3 io:  [0x00-0xffff]
[    0.472248] pci_bus 0000:02: resource 4 mem: [0x000000-0xffffffff]
[    0.472295] NET: Registered protocol family 2
[    0.472408] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.472802] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.473384] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.473612] TCP: Hash tables configured (established 131072 bind 65536)
[    0.473614] TCP reno registered
[    0.473689] NET: Registered protocol family 1
[    0.473710] pci 0000:00:02.0: Boot video device
[    0.473925] Simple Boot Flag value 0x5 read from CMOS RAM was invalid
[    0.473928] Simple Boot Flag at 0x44 set to 0x1
[    0.474114] cpufreq-nforce2: No nForce2 chipset.
[    0.474142] Scanning for low memory corruption every 60 seconds
[    0.474267] audit: initializing netlink socket (disabled)
[    0.474278] type=2000 audit(1280053120.471:1): initialized
[    0.485313] highmem bounce pool size: 64 pages
[    0.485319] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.487043] VFS: Disk quotas dquot_6.5.2
[    0.487112] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.487758] fuse init (API version 7.13)
[    0.487853] msgmni has been set to 1679
[    0.488092] alg: No test for stdrng (krng)
[    0.488150] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.488154] io scheduler noop registered
[    0.488156] io scheduler anticipatory registered
[    0.488159] io scheduler deadline registered
[    0.488201] io scheduler cfq registered (default)
[    0.488367]   alloc irq_desc for 24 on node -1
[    0.488370]   alloc kstat_irqs on node -1
[    0.488383] pcieport 0000:00:1c.0: irq 24 for MSI/MSI-X
[    0.488396] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.488514] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.488533] Firmware did not grant requested _OSC control
[    0.488573] Firmware did not grant requested _OSC control
[    0.488591] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.603548] ACPI: AC Adapter [AC] (on-line)
[    0.603643] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.603646] ACPI: Power Button [PWRB]
[    0.603698] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input1
[    0.603739] ACPI: Lid Switch [LID0]
[    0.603787] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input2
[    0.603794] ACPI: Sleep Button [SLPB]
[    0.603854] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    0.603856] ACPI: Power Button [PWRF]
[    0.604498] ACPI: SSDT bf67cc90 001EA (v01  PmRef  Cpu0Ist 00003000 INTL 20051117)
[    0.605075] ACPI: SSDT bf67b610 005D7 (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.605533] Monitor-Mwait will be used to enter C-1 state
[    0.605564] Monitor-Mwait will be used to enter C-2 state
[    0.605591] Monitor-Mwait will be used to enter C-3 state
[    0.605600] Marking TSC unstable due to TSC halts in idle
[    0.605648] Switching to clocksource hpet
[    0.605707] processor LNXCPU:00: registered as cooling_device0
[    0.606097] ACPI: SSDT bf67cf10 000C4 (v01  PmRef  Cpu1Ist 00003000 INTL 20051117)
[    0.606490] ACPI: SSDT bf67ed10 00083 (v01  PmRef  Cpu1Cst 00003000 INTL 20051117)
[    0.607096] processor LNXCPU:01: registered as cooling_device1
[    0.736060] thermal LNXTHERM:01: registered as thermal_zone0
[    0.736070] ACPI: Thermal Zone [TZ01] (0 C)
[    0.736214] isapnp: Scanning for PnP cards...
[    0.737715] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.739197] brd: module loaded
[    0.739721] loop: module loaded
[    0.739809] input: Macintosh mouse button emulation as /devices/virtual/input/input4
[    0.739898] ata_piix 0000:00:1f.2: version 2.13
[    0.739918]   alloc irq_desc for 17 on node -1
[    0.739920]   alloc kstat_irqs on node -1
[    0.739926] ata_piix 0000:00:1f.2: PCI INT C -> GSI 17 (level, low) -> IRQ 17
[    0.739933] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[    0.864130] ACPI: Battery Slot [BAT0] (battery present)
[    0.896030] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.896112] scsi0 : ata_piix
[    0.896192] scsi1 : ata_piix
[    0.897299] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x3090 irq 14
[    0.897303] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x3098 irq 15
[    0.897667] Fixed MDIO Bus: probed
[    0.897707] PPP generic driver version 2.4.2
[    0.897746] tun: Universal TUN/TAP device driver, 1.6
[    0.897748] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.897841] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.897863]   alloc irq_desc for 23 on node -1
[    0.897865]   alloc kstat_irqs on node -1
[    0.897870] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.897881] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.897885] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.897920] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.897954] ehci_hcd 0000:00:1d.7: debug port 1
[    0.901834] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.901950] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xd2404000
[    0.920017] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.920123] usb usb1: configuration #1 chosen from 1 choice
[    0.920157] hub 1-0:1.0: USB hub found
[    0.920165] hub 1-0:1.0: 6 ports detected
[    0.920232] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.920247] uhci_hcd: USB Universal Host Controller Interface driver
[    0.920269]   alloc irq_desc for 21 on node -1
[    0.920272]   alloc kstat_irqs on node -1
[    0.920276] uhci_hcd 0000:00:1d.0: PCI INT D -> GSI 21 (level, low) -> IRQ 21
[    0.920284] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.920288] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.920322] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.920361] uhci_hcd 0000:00:1d.0: irq 21, io base 0x00003060
[    0.920464] usb usb2: configuration #1 chosen from 1 choice
[    0.920493] hub 2-0:1.0: USB hub found
[    0.920500] hub 2-0:1.0: 2 ports detected
[    0.920551]   alloc irq_desc for 20 on node -1
[    0.920553]   alloc kstat_irqs on node -1
[    0.920558] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 20 (level, low) -> IRQ 20
[    0.920565] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.920569] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.920602] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.920639] uhci_hcd 0000:00:1d.1: irq 20, io base 0x00003040
[    0.920738] usb usb3: configuration #1 chosen from 1 choice
[    0.920770] hub 3-0:1.0: USB hub found
[    0.920777] hub 3-0:1.0: 2 ports detected
[    0.920828]   alloc irq_desc for 19 on node -1
[    0.920830]   alloc kstat_irqs on node -1
[    0.920835] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 19 (level, low) -> IRQ 19
[    0.920842] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.920846] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.920878] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.920916] uhci_hcd 0000:00:1d.2: irq 19, io base 0x00003020
[    0.921022] usb usb4: configuration #1 chosen from 1 choice
[    0.921050] hub 4-0:1.0: USB hub found
[    0.921057] hub 4-0:1.0: 2 ports detected
[    0.921159] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[    0.952583] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.952596] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.952714] mice: PS/2 mouse device common for all mice
[    0.953716] rtc_cmos 00:03: RTC can wake from S4
[    0.953760] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    0.953794] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
[    0.953900] device-mapper: uevent: version 1.0.3
[    0.953996] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
[    0.954069] device-mapper: multipath: version 1.1.0 loaded
[    0.954072] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.954185] EISA: Probing bus 0 at eisa.0
[    0.954192] Cannot allocate resource for EISA slot 1
[    0.954194] Cannot allocate resource for EISA slot 2
[    0.954196] Cannot allocate resource for EISA slot 3
[    0.954220] EISA: Detected 0 cards.
[    0.954373] cpuidle: using governor ladder
[    0.954502] cpuidle: using governor menu
[    0.954999] TCP cubic registered
[    0.955167] NET: Registered protocol family 10
[    0.955692] lo: Disabled Privacy Extensions
[    0.956103] NET: Registered protocol family 17
[    0.956487] Using IPI No-Shortcut mode
[    0.956561] PM: Resume from disk failed.
[    0.956578] registered taskstats version 1
[    0.956899]   Magic number: 2:216:326
[    0.956970] rtc_cmos 00:03: setting system clock to 2010-07-25 10:18:42 UTC (1280053122)
[    0.956974] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.956975] EDD information not available.
[    0.973944] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[    1.068344] ata1.00: ATA-8: Hitachi HTS542516K9SA00, BBCOC32P, max UDMA/100
[    1.068348] ata1.00: 312581808 sectors, multi 16: LBA48 
[    1.084302] ata1.00: configured for UDMA/100
[    1.090436] isapnp: No Plug & Play device found
[    1.090561] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS54251 BBCO PQ: 0 ANSI: 5
[    1.090694] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.090772] sd 0:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    1.090852] sd 0:0:0:0: [sda] Write Protect is off
[    1.090856] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.090871] ata2.00: ATAPI: TSSTcorp CDDVDW TS-L632H, HS02, max MWDMA2
[    1.090883] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.091078]  sda: sda1 sda2 sda3
[    1.120292] ata2.00: configured for MWDMA2
[    1.126463] scsi 1:0:0:0: CD-ROM            TSSTcorp CDDVDW TS-L632H  HS02 PQ: 0 ANSI: 5
[    1.128186] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.138162] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.138165] Uniform CD-ROM driver Revision: 3.20
[    1.138246] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.138291] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.138356] Freeing unused kernel memory: 660k freed
[    1.138783] Write protecting the kernel text: 4680k
[    1.138843] Write protecting the kernel read-only data: 1840k
[    1.157515] udev: starting version 151
[    1.228063] usb 1-6: new high speed USB device using ehci_hcd and address 2
[    1.254099] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    1.254124] 8139cp 0000:02:01.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip, use 8139too
[    1.272209] 8139too Fast Ethernet driver 0.9.28
[    1.272260]   alloc irq_desc for 16 on node -1
[    1.272262]   alloc kstat_irqs on node -1
[    1.272270] 8139too 0000:02:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.272284] 8139too 0000:02:01.0: setting latency timer to 64
[    1.273905] eth0: RealTek RTL8139 at 0x1000, 00:1e:ec:2d:26:fd, IRQ 16
[    1.435036] usb 1-6: configuration #1 chosen from 1 choice
[    1.568972] PM: Marking nosave pages: 0000000000002000 - 0000000000006000
[    1.568977] PM: Marking nosave pages: 000000000009f000 - 0000000000100000
[    1.568982] PM: Basic memory bitmaps created
[    1.583513] PM: Basic memory bitmaps freed
[    1.588680] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
[    1.588685] EXT4-fs (sda1): write access will be enabled during recovery
[    2.762720] EXT4-fs (sda1): orphan cleanup on readonly fs
[    2.762729] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 2644
[    2.762826] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 4364
[    2.762847] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 4346
[    2.808624] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 4538
[    2.808673] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 127
[    2.812445] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 115
[    2.824939] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 33851
[    2.843262] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 40144
[    2.857027] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 2825
[    2.880620] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 1669
[    2.880704] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 4523
[    2.880724] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 1768
[    2.880742] EXT4-fs (sda1): 12 orphan inodes deleted
[    2.880746] EXT4-fs (sda1): recovery complete
[    3.146755] EXT4-fs (sda1): mounted filesystem with ordered data mode
[    5.836873] Adding 6136820k swap on /dev/sda2.  Priority:-1 extents:1 across:6136820k 
[    6.812098] udev: starting version 151
[    7.541479] cfg80211: Calling CRDA to update world regulatory domain
[    7.924330] Linux agpgart interface v0.103
[    8.089241] Linux video capture interface: v2.00
[    8.162114] uvcvideo: Found UVC 1.00 device Webcam-101 (064e:c108)
[    8.173954] input: Webcam-101 as /devices/pci0000:00/0000:00:1d.7/usb1/1-6/1-6:1.0/input/input6
[    8.174062] usbcore: registered new interface driver uvcvideo
[    8.174110] USB Video Class driver (v0.1.0)
[    8.206061] agpgart-intel 0000:00:00.0: Intel 965GM Chipset
[    8.206829] agpgart-intel 0000:00:00.0: detected 7676K stolen memory
[    8.212363] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xc0000000
[    8.495679] ath5k 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    8.495696] ath5k 0000:01:00.0: setting latency timer to 64
[    8.495727] ath5k 0000:01:00.0: registered as 'phy0'
[    8.540464] [drm] Initialized drm 1.1.0 20060810
[    8.634776] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    8.634784] i915 0000:00:02.0: setting latency timer to 64
[    8.641014]   alloc irq_desc for 25 on node -1
[    8.641018]   alloc kstat_irqs on node -1
[    8.641028] i915 0000:00:02.0: irq 25 for MSI/MSI-X
[    8.641038] [drm] set up 7M of stolen space
[    8.767817] [drm] initialized overlay support
[    8.998496] ath: EEPROM regdomain: 0x67
[    8.998498] ath: EEPROM indicates we should expect a direct regpair map
[    8.998502] ath: Country alpha2 being used: 00
[    8.998504] ath: Regpair used: 0x67
[    9.107598] input: PS/2 Mouse as /devices/platform/i8042/serio1/input/input7
[    9.144085] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input8
[    9.147189] cfg80211: World regulatory domain updated:
[    9.147192]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[    9.147195]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    9.147198]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    9.147201]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    9.147204]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    9.147207]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    9.366628] fb0: inteldrmfb frame buffer device
[    9.366632] registered panic notifier
[    9.367399] [Firmware Bug]: ACPI: ACPI brightness control misses _BQC function
[    9.402341] phy0: Selected rate control algorithm 'minstrel'
[    9.403193] Registered led device: ath5k-phy0::rx
[    9.403212] Registered led device: ath5k-phy0::tx
[    9.403216] ath5k phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
[    9.424158] acpi device:15: registered as cooling_device2
[    9.424435] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input9
[    9.424492] ACPI: Video Device [OVGA] (multi-head: yes  rom: no  post: no)
[    9.424520] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    9.536857] vga16fb: initializing
[    9.536861] vga16fb: mapped to 0xc00a0000
[    9.536866] vga16fb: not registering due to another framebuffer present
[    9.619625] lp: driver loaded but no devices found
[    9.717574] type=1505 audit(1280053131.259:2):  operation="profile_load" pid=600 name="/sbin/dhclient3"
[    9.718406] type=1505 audit(1280053131.259:3):  operation="profile_load" pid=600 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[    9.718810] type=1505 audit(1280053131.259:4):  operation="profile_load" pid=600 name="/usr/lib/connman/scripts/dhclient-script"
[    9.756728] Console: switching to colour frame buffer device 160x50
[   10.595169]   alloc irq_desc for 22 on node -1
[   10.595173]   alloc kstat_irqs on node -1
[   10.595181] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   10.595218] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   10.692325] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   10.692512] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   10.692655] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[  353.611521] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  353.641748] eth0: link down
[  353.642487] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  380.617257] wlan0: deauthenticating from 00:13:f7:99:0b:02 by local choice (reason=3)
[  380.617332] wlan0: direct probe to AP 00:13:f7:99:0b:02 (try 1)
[  380.626683] wlan0: direct probe responded
[  380.626691] wlan0: authenticate with AP 00:13:f7:99:0b:02 (try 1)
[  380.632208] wlan0: authenticated
[  380.632236] wlan0: associate with AP 00:13:f7:99:0b:02 (try 1)
[  380.646611] wlan0: RX AssocResp from 00:13:f7:99:0b:02 (capab=0x431 status=0 aid=2)
[  380.646616] wlan0: associated
[  380.647403] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  383.253947] padlock: VIA PadLock not detected.
[  391.360183] wlan0: no IPv6 routers present
[  543.742741] [drm:drm_mode_getfb] *ERROR* invalid framebuffer id

**¿Qué tarjeta de video utilizas?**
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)[B]

 ¿Tienes un escritorio extendido? [/B]
Creo que no...
Sólo tengo el monitor del portátil.

En **xorg.conf** está así:

Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

---

### Post by Carlos C on 2010-07-25
Te sugiero que intentes lo siguiente, en el terminal escribe:
```
sudo gedit /etc/default/grub
```
Luego busca la línea que dice:
```
#GRUB_TERMINAL=console
```
y elimina el signo "#" para que deje de ser un comentario. Debiera quedar así:
```
GRUB_TERMINAL=console
```
Luego grabas los cambios y cierras el archivo. A continuación ejecuta el siguiente comando:
```
sudo update-grub
```
y reinicias el sistema. Si no funciona siempre puedes volver atrás.

Saludos.

---

### Post by jc_jc on 2010-07-26
... he instalado GRUB2 y ya tengo el archivo grub en etc/default
Lo he editado y descomentado la línea
GRUB_TERMINAL=console
y a continuación:
update-grub

También he reiniciado... y seguimos igual      brrrrrrrrrrrrrrrrr!

Seguiré buscando una solución a este enigma...

---

### Post by jc_jc on 2010-08-27
... ejemmm! así son las cosas...
sudo init 1
...
login
pass
... y lo mismo hasta la tty6
Por fin :)
Espero que no le pase a nadie y si le pasa, ésta ha sido mi solución.
Gracias a quienes se interesaron ... en especial a Carlos C

---

