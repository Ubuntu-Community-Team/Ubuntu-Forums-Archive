---
title: "Program to install ath9k_htc (Atheros Linux Driver)"
date: 2010-08-30
forum: Tutorials
---

### Post by vagrale13 on 2010-08-30
**:arrow: All the below no need for next version Ubuntu Maverick**** 10.10** 

First see see the list of supported chipset here [http://linuxwireless.org/en/users/Drivers/ath9k_htc/devices](http://linuxwireless.org/en/users/Drivers/ath9k_htc/devices)

you can find your usb wireless chipset with the command
```
lsusb
```if the driver support your chipset, continue.

Install the **ath9k_htc-installer**
[IMG]http://img822.imageshack.us/img822/3866/ath9khtcinstaller.png[/IMG]

For **Ubuntu Lucid 10.04 LTS** and oldest download the *.deb* package from here [https://sourceforge.net/projects/ath9k-htc/files/ath9k_htc-installer/](https://sourceforge.net/projects/ath9k-htc/files/ath9k_htc-installer/) and install it!

For **Ubuntu Maverick 10.10** download this .deb package [https://sourceforge.net/projects/ath9k-htc/files/ath9k_htc-installer-Ubuntu%20Maverick%2010.10-fixed/]("https://sourceforge.net/projects/ath9k-htc/files/ath9k_htc-installer-Ubuntu%20Maverick%2010.10-fixed/") and install it!
But on **Maverick** must be works out of the box *usb wireless*

If someone install the older *.deb*, remove it first from synaptic the package name "**ath9k_htc-install**" 
and then, install it!

[IMG]http://img69.imageshack.us/img69/4276/screenshotfs.png[/IMG]

After opening the program for installation the driver from *menu - Applications - System Tools - ath9k_htc-installer*
and follow the instructions to make installing the driver. :KS

[LEFT]
[LIST]
[*] *Every time where upgrade kernel, must be run the program.*
[*]* It is &#925;&#927;&#932; necessary to connect the internet to run the program.*
[*]* The .deb package is tested on Ubuntu 10.04 32bit[IMG]http://www.google.gr/images/cleardot.gif[/IMG] but logically it can be work in all versions.*
[/LIST]
[/LEFT]
    
More information about driver here [http://linuxwireless.org/en/users/Drivers/ath9k_htc](http://linuxwireless.org/en/users/Drivers/ath9k_htc)

More info about program & code you can find here [https://launchpad.net/ath9k-htc-installer](https://launchpad.net/ath9k-htc-installer)

If you want, see the video *how-to* here [http://www.youtube.com/watch?v=kAMaixDsles](http://www.youtube.com/watch?v=kAMaixDsles)

---

### Post by vagrale13 on 2010-09-06
The **ath9k_htc-installer** (most), has changed and has upload the code to launchpad!
The changes made, are shown in video! :rolleyes:

---

### Post by mad hamish on 2010-09-30
Thanks :P, used it to get my WNA1100 wireless USB Adapter working

---

### Post by Corey4666 on 2010-10-01
Won't work with my netgear wna1100 :confused:

---

### Post by vagrale13 on 2010-10-02
> **Corey4666 said:**
> Won't work with my netgear wna1100 :confused:
Can you post the output of commands
```
lsusb
uname -r
lsmod | grep ath9k
dmesg
```

---

### Post by Corey4666 on 2010-10-02
```
eviscerate@EVI-MAIN:~$ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 04f3:0230 Elan Microelectronics Corp. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0781:5406 SanDisk Corp. Cruzer Micro U3
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 003: ID 0403:6001 Future Technology Devices International, Ltd FT232 USB-Serial (UART) IC
Bus 002 Device 002: ID 0d8c:0121 C-Media Electronics, Inc. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 058f:6362 Alcor Micro Corp. Flash Card Reader/Writer
Bus 001 Device 002: ID 0846:9030 NetGear, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
eviscerate@EVI-MAIN:~$ 
eviscerate@EVI-MAIN:~$ uname -r
2.6.32-5-686
eviscerate@EVI-MAIN:~$ 
eviscerate@EVI-MAIN:~$ lsmod | grep ath9k
eviscerate@EVI-MAIN:~$ 
eviscerate@EVI-MAIN:~$ dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.32-5-686 (Debian 2.6.32-15) (ben@decadent.org.uk) (gcc version 4.3.5 (Debian 4.3.5-1) ) #1 SMP Tue Jun 1 04:59:47 UTC 2010
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
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f400 (usable)
[    0.000000]  BIOS-e820: 000000000009f400 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e6000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000cffb0000 (usable)
[    0.000000]  BIOS-e820: 00000000cffb0000 - 00000000cffbe000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000cffbe000 - 00000000cffe0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000cffe0000 - 00000000cffee000 (reserved)
[    0.000000]  BIOS-e820: 00000000cfff0000 - 00000000d0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff700000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000130000000 (usable)
[    0.000000] DMI present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0xcffb0 max_arch_pfn = 0x100000
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
[    0.000000] initial memory mapped : 0 - 01800000
[    0.000000] init_memory_mapping: 0000000000000000-00000000373fe000
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 0037000000 page 2M
[    0.000000]  0037000000 - 00373fe000 page 4k
[    0.000000] kernel direct mapping tables up to 373fe000 @ 10000-16000
[    0.000000] RAMDISK: 377dd000 - 37fef780
[    0.000000] Allocated new RAMDISK: 00100000 - 00912780
[    0.000000] Move RAMDISK from 00000000377dd000 - 0000000037fef77f to 00100000 - 0091277f
[    0.000000] ACPI: RSDP 000fa1c0 00014 (v00 ACPIAM)
[    0.000000] ACPI: RSDT cffb0000 00038 (v01 071508 RSDT1902 20080715 MSFT 00000097)
[    0.000000] ACPI: FACP cffb0200 00084 (v01 071508 FACP1902 20080715 MSFT 00000097)
[    0.000000] ACPI Warning: Optional field Pm2ControlBlock has zero address or length: 0000000000000000/1 (20090903/tbfadt-557)
[    0.000000] ACPI: DSDT cffb0490 09CFC (v01  78DBA 78DBA715 00000000 INTL 20051117)
[    0.000000] ACPI: FACS cffbe000 00040
[    0.000000] ACPI: APIC cffb0390 0006C (v01 071508 APIC1902 20080715 MSFT 00000097)
[    0.000000] ACPI: MCFG cffb0400 0003C (v01 071508 OEMMCFG  20080715 MSFT 00000097)
[    0.000000] ACPI: OEMB cffbe040 00072 (v01 071508 OEMB1902 20080715 MSFT 00000097)
[    0.000000] ACPI: HPET cffba190 00038 (v01 071508 OEMHPET  20080715 MSFT 00000097)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 2443MB HIGHMEM available.
[    0.000000] 883MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 373fe000
[    0.000000]   low ram: 0 - 373fe000
[    0.000000]   node 0 low ram: 00000000 - 373fe000
[    0.000000]   node 0 bootmap 00012000 - 00018e80
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 00373fe000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0001000000 - 00014c3154]    TEXT DATA BSS ==> [0001000000 - 00014c3154]
[    0.000000]   #4 [000009f400 - 0000100000]    BIOS reserved ==> [000009f400 - 0000100000]
[    0.000000]   #5 [00014c4000 - 00014ca0e5]              BRK ==> [00014c4000 - 00014ca0e5]
[    0.000000]   #6 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
[    0.000000]   #7 [0000100000 - 0000912780]      NEW RAMDISK ==> [0000100000 - 0000912780]
[    0.000000]   #8 [0000012000 - 0000019000]          BOOTMAP ==> [0000012000 - 0000019000]
[    0.000000] found SMP MP-table at [c00ff780] ff780
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x000373fe
[    0.000000]   HighMem  0x000373fe -> 0x000cffb0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x000cffb0
[    0.000000] On node 0 totalpages: 851775
[    0.000000] free_area_init_node: node 0, pgdat c13ae680, node_mem_map c14cc200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1736 pages used for memmap
[    0.000000]   Normal zone: 220470 pages, LIFO batch:31
[    0.000000]   HighMem zone: 4888 pages used for memmap
[    0.000000]   HighMem zone: 620698 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8300 base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e6000
[    0.000000] PM: Registered nosave memory: 00000000000e6000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at d0000000 (gap: d0000000:10000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] NR_CPUS:32 nr_cpumask_bits:32 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @c3000000 s34136 r0 d23208 u1048576
[    0.000000] pcpu-alloc: s34136 r0 d23208 u1048576 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 845119
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-5-686 root=UUID=edb62478-f7fa-41f3-92d4-71c239172b3c ro quiet
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] Initializing HighMem for node 0 (000373fe:000cffb0)
[    0.000000] Memory: 3365020k/3407552k available (2490k kernel code, 40912k reserved, 1318k data, 372k init, 2502344k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xffd56000 - 0xfffff000   (2724 kB)
[    0.000000]     pkmap   : 0xff400000 - 0xff800000   (4096 kB)
[    0.000000]     vmalloc : 0xf7bfe000 - 0xff3fe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf73fe000   ( 883 MB)
[    0.000000]       .init : 0xc13b9000 - 0xc1416000   ( 372 kB)
[    0.000000]       .data : 0xc126e965 - 0xc13b81e0   (1318 kB)
[    0.000000]       .text : 0xc1000000 - 0xc126e965   (2490 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] NR_IRQS:1280
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] hpet clockevent registered
[    0.000000] HPET: 4 timers in total, 1 timers will be used for per-cpu timer
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2300.475 MHz processor.
[    0.004004] Calibrating delay loop (skipped), value calculated using timer frequency.. 4600.95 BogoMIPS (lpj=9201900)
[    0.004017] Security Framework initialized
[    0.004022] SELinux:  Disabled at boot.
[    0.004028] Mount-cache hash table entries: 512
[    0.004118] Initializing cgroup subsys ns
[    0.004121] Initializing cgroup subsys cpuacct
[    0.004124] Initializing cgroup subsys devices
[    0.004126] Initializing cgroup subsys freezer
[    0.004128] Initializing cgroup subsys net_cls
[    0.004143] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.004145] CPU: L2 Cache: 512K (64 bytes/line)
[    0.004147] CPU: Physical Processor ID: 0
[    0.004149] CPU: Processor Core ID: 0
[    0.004152] mce: CPU supports 6 MCE banks
[    0.004160] using C1E aware idle routine
[    0.004165] Performance Events: AMD PMU driver.
[    0.004169] ... version:                0
[    0.004171] ... bit width:              48
[    0.004172] ... generic registers:      4
[    0.004174] ... value mask:             0000ffffffffffff
[    0.004176] ... max period:             00007fffffffffff
[    0.004178] ... fixed-purpose events:   0
[    0.004179] ... event mask:             000000000000000f
[    0.004183] Checking 'hlt' instruction... OK.
[    0.020791] ACPI: Core revision 20090903
[    0.032049] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.032384] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.073349] CPU0: AMD Phenom(tm) 9600 Quad-Core Processor stepping 02
[    0.076001] Booting processor 1 APIC 0x1 ip 0x6000
[    0.008000] Initializing CPU#1
[    0.008000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.008000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.008000] CPU: Physical Processor ID: 0
[    0.008000] CPU: Processor Core ID: 1
[    0.160032] CPU1: AMD Phenom(tm) 9600 Quad-Core Processor stepping 02
[    0.160043] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.164090] Booting processor 2 APIC 0x2 ip 0x6000
[    0.008000] Initializing CPU#2
[    0.008000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.008000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.008000] CPU: Physical Processor ID: 0
[    0.008000] CPU: Processor Core ID: 2
[    0.252047] CPU2: AMD Phenom(tm) 9600 Quad-Core Processor stepping 02
[    0.252062] checking TSC synchronization [CPU#0 -> CPU#2]: passed.
[    0.256090] Booting processor 3 APIC 0x3 ip 0x6000
[    0.008000] Initializing CPU#3
[    0.008000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.008000] CPU: L2 Cache: 512K (64 bytes/line)
[    0.008000] CPU: Physical Processor ID: 0
[    0.008000] CPU: Processor Core ID: 3
[    0.344056] CPU3: AMD Phenom(tm) 9600 Quad-Core Processor stepping 02
[    0.344072] checking TSC synchronization [CPU#0 -> CPU#3]: passed.
[    0.348047] Brought up 4 CPUs
[    0.348049] Total of 4 processors activated (18401.73 BogoMIPS).
[    0.349006] CPU0 attaching sched-domain:
[    0.349009]  domain 0: span 0-3 level MC
[    0.349011]   groups: 0 1 2 3
[    0.349016] CPU1 attaching sched-domain:
[    0.349018]  domain 0: span 0-3 level MC
[    0.349020]   groups: 1 2 3 0
[    0.349024] CPU2 attaching sched-domain:
[    0.349026]  domain 0: span 0-3 level MC
[    0.349028]   groups: 2 3 0 1
[    0.349032] CPU3 attaching sched-domain:
[    0.349033]  domain 0: span 0-3 level MC
[    0.349035]   groups: 3 0 1 2
[    0.349128] devtmpfs: initialized
[    0.349128] regulator: core version 0.5
[    0.349128] NET: Registered protocol family 16
[    0.349128] ACPI: bus type pci registered
[    0.349128] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.349128] PCI: MCFG area at e0000000 reserved in E820
[    0.349128] PCI: Using MMCONFIG for extended config space
[    0.349128] PCI: Using configuration type 1 for base access
[    0.349128] bio: create slab <bio-0> at 0
[    0.349128] ACPI: EC: Look up EC in DSDT
[    0.353383] ACPI Error (psargs-0359): [ECEN] Namespace lookup failure, AE_NOT_FOUND
[    0.353389] ACPI Error (psparse-0537): Method parse/execution failed [\] (Node c14bb530), AE_NOT_FOUND
[    0.353626] ACPI: Executed 5 blocks of module-level executable AML code
[    0.360305] ACPI: Interpreter enabled
[    0.360313] ACPI: (supports S0 S1 S4 S5)
[    0.360334] ACPI: Using IOAPIC for interrupt routing
[    0.367972] ACPI Error: No handler for Region [SACS] (f6c440c8) [PCI_Config] (20090903/evregion-319)
[    0.367977] ACPI Error: Region PCI_Config(2) has no handler (20090903/exfldio-295)
[    0.367982] ACPI Error (psparse-0537): Method parse/execution failed [\PRID.P_D0._STA] (Node f6c1a750), AE_NOT_EXIST
[    0.368023] ACPI Error: No handler for Region [SACS] (f6c440c8) [PCI_Config] (20090903/evregion-319)
[    0.368028] ACPI Error: Region PCI_Config(2) has no handler (20090903/exfldio-295)
[    0.368032] ACPI Error (psparse-0537): Method parse/execution failed [\PRID.P_D1._STA] (Node f6c1a7f8), AE_NOT_EXIST
[    0.368090] ACPI Error: No handler for Region [SACS] (f6c440c8) [PCI_Config] (20090903/evregion-319)
[    0.368094] ACPI Error: Region PCI_Config(2) has no handler (20090903/exfldio-295)
[    0.368099] ACPI Error (psparse-0537): Method parse/execution failed [\SECD.S_D0._STA] (Node f6c1a960), AE_NOT_EXIST
[    0.368129] ACPI Error: No handler for Region [SACS] (f6c440c8) [PCI_Config] (20090903/evregion-319)
[    0.368133] ACPI Error: Region PCI_Config(2) has no handler (20090903/exfldio-295)
[    0.368137] ACPI Error (psparse-0537): Method parse/execution failed [\SECD.S_D1._STA] (Node f6c1aa08), AE_NOT_EXIST
[    0.368250] ACPI Warning: Incorrect checksum in table [OEMB] - E1, should be DC (20090903/tbutils-314)
[    0.368354] ACPI: No dock devices found.
[    0.368508] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.368603] pci 0000:00:02.0: PME# supported from D0 D3hot D3cold
[    0.368606] pci 0000:00:02.0: PME# disabled
[    0.368644] pci 0000:00:07.0: PME# supported from D0 D3hot D3cold
[    0.368647] pci 0000:00:07.0: PME# disabled
[    0.368699] pci 0000:00:11.0: reg 10 io port: [0xc000-0xc007]
[    0.368706] pci 0000:00:11.0: reg 14 io port: [0xb000-0xb003]
[    0.368713] pci 0000:00:11.0: reg 18 io port: [0xa000-0xa007]
[    0.368720] pci 0000:00:11.0: reg 1c io port: [0x9000-0x9003]
[    0.368726] pci 0000:00:11.0: reg 20 io port: [0x8000-0x800f]
[    0.368734] pci 0000:00:11.0: reg 24 32bit mmio: [0xfbfff800-0xfbfffbff]
[    0.368751] pci 0000:00:11.0: set SATA to AHCI mode
[    0.368795] pci 0000:00:12.0: reg 10 32bit mmio: [0xfbffe000-0xfbffefff]
[    0.368848] pci 0000:00:12.1: reg 10 32bit mmio: [0xfbffd000-0xfbffdfff]
[    0.368918] pci 0000:00:12.2: reg 10 32bit mmio: [0xfbfff000-0xfbfff0ff]
[    0.368968] pci 0000:00:12.2: supports D1 D2
[    0.368970] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
[    0.368974] pci 0000:00:12.2: PME# disabled
[    0.369004] pci 0000:00:13.0: reg 10 32bit mmio: [0xfbffc000-0xfbffcfff]
[    0.369057] pci 0000:00:13.1: reg 10 32bit mmio: [0xfbffb000-0xfbffbfff]
[    0.369126] pci 0000:00:13.2: reg 10 32bit mmio: [0xfbffa800-0xfbffa8ff]
[    0.369176] pci 0000:00:13.2: supports D1 D2
[    0.369178] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
[    0.369182] pci 0000:00:13.2: PME# disabled
[    0.369293] pci 0000:00:14.1: reg 10 io port: [0x00-0x07]
[    0.369300] pci 0000:00:14.1: reg 14 io port: [0x00-0x03]
[    0.369307] pci 0000:00:14.1: reg 18 io port: [0x00-0x07]
[    0.369313] pci 0000:00:14.1: reg 1c io port: [0x00-0x03]
[    0.369320] pci 0000:00:14.1: reg 20 io port: [0xff00-0xff0f]
[    0.369384] pci 0000:00:14.2: reg 10 64bit mmio: [0xfbff4000-0xfbff7fff]
[    0.369425] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
[    0.369429] pci 0000:00:14.2: PME# disabled
[    0.369531] pci 0000:00:14.5: reg 10 32bit mmio: [0xfbff9000-0xfbff9fff]
[    0.369676] pci 0000:01:00.0: reg 10 32bit mmio: [0xfd000000-0xfdffffff]
[    0.369686] pci 0000:01:00.0: reg 14 64bit mmio pref: [0xd0000000-0xdfffffff]
[    0.369695] pci 0000:01:00.0: reg 1c 64bit mmio: [0xfc000000-0xfcffffff]
[    0.369701] pci 0000:01:00.0: reg 24 io port: [0xd800-0xd87f]
[    0.369707] pci 0000:01:00.0: reg 30 32bit mmio pref: [0xfeae0000-0xfeafffff]
[    0.369744] pci 0000:01:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    0.369802] pci 0000:00:02.0: bridge io port: [0xd000-0xdfff]
[    0.369805] pci 0000:00:02.0: bridge 32bit mmio: [0xfc000000-0xfeafffff]
[    0.369809] pci 0000:00:02.0: bridge 64bit mmio pref: [0xd0000000-0xdfffffff]
[    0.369844] pci 0000:02:00.0: reg 10 io port: [0xe800-0xe8ff]
[    0.369859] pci 0000:02:00.0: reg 18 64bit mmio: [0xfebff000-0xfebfffff]
[    0.369870] pci 0000:02:00.0: reg 20 64bit mmio pref: [0xfaff0000-0xfaffffff]
[    0.369876] pci 0000:02:00.0: reg 30 32bit mmio pref: [0xfebc0000-0xfebdffff]
[    0.369905] pci 0000:02:00.0: supports D1 D2
[    0.369907] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.369911] pci 0000:02:00.0: PME# disabled
[    0.376077] pci 0000:00:07.0: bridge io port: [0xe000-0xefff]
[    0.376080] pci 0000:00:07.0: bridge 32bit mmio: [0xfeb00000-0xfebfffff]
[    0.376084] pci 0000:00:07.0: bridge 64bit mmio pref: [0xfaf00000-0xfaffffff]
[    0.376140] pci 0000:00:14.4: transparent bridge
[    0.376159] pci_bus 0000:00: on NUMA node 0
[    0.376163] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.376362] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE2._PRT]
[    0.376427] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE7._PRT]
[    0.376498] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0PC._PRT]
[    0.380826] ACPI: PCI Interrupt Link [LNKA] (IRQs 4 7 *10 11 12 14 15)
[    0.380930] ACPI: PCI Interrupt Link [LNKB] (IRQs 4 7 10 *11 12 14 15)
[    0.381031] ACPI: PCI Interrupt Link [LNKC] (IRQs 4 7 *10 11 12 14 15)
[    0.381146] ACPI: PCI Interrupt Link [LNKD] (IRQs 4 7 10 *11 12 14 15)
[    0.381270] ACPI: PCI Interrupt Link [LNKE] (IRQs 4 7 10 11 12 14 15) *0, disabled.
[    0.381377] ACPI: PCI Interrupt Link [LNKF] (IRQs 4 7 10 11 12 14 15) *0, disabled.
[    0.381477] ACPI: PCI Interrupt Link [LNKG] (IRQs 4 *10 11 12 14 15)
[    0.381587] ACPI: PCI Interrupt Link [LNKH] (IRQs 4 7 10 11 12 14 15) *0, disabled.
[    0.381688] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.381691] vgaarb: loaded
[    0.381715] PCI: Using ACPI for IRQ routing
[    0.381715] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 24, 0
[    0.381715] hpet0: 4 comparators, 32-bit 14.318180 MHz counter
[    0.382205] Switching to clocksource tsc
[    0.384893] pnp: PnP ACPI init
[    0.384902] ACPI: bus type pnp registered
[    0.389859] ACPI Error: No handler for Region [SACS] (f6c440c8) [PCI_Config] (20090903/evregion-319)
[    0.389864] ACPI Error: Region PCI_Config(2) has no handler (20090903/exfldio-295)
[    0.389869] ACPI Error (psparse-0537): Method parse/execution failed [\PRID.P_D0._STA] (Node f6c1a750), AE_NOT_EXIST
[    0.389890] ACPI Error (uteval-0250): Method execution failed [\PRID.P_D0._STA] (Node f6c1a750), AE_NOT_EXIST
[    0.389908] ACPI Error: No handler for Region [SACS] (f6c440c8) [PCI_Config] (20090903/evregion-319)
[    0.389912] ACPI Error: Region PCI_Config(2) has no handler (20090903/exfldio-295)
[    0.389917] ACPI Error (psparse-0537): Method parse/execution failed [\PRID.P_D1._STA] (Node f6c1a7f8), AE_NOT_EXIST
[    0.389937] ACPI Error (uteval-0250): Method execution failed [\PRID.P_D1._STA] (Node f6c1a7f8), AE_NOT_EXIST
[    0.389956] ACPI Error: No handler for Region [SACS] (f6c440c8) [PCI_Config] (20090903/evregion-319)
[    0.389960] ACPI Error: Region PCI_Config(2) has no handler (20090903/exfldio-295)
[    0.389964] ACPI Error (psparse-0537): Method parse/execution failed [\SECD.S_D0._STA] (Node f6c1a960), AE_NOT_EXIST
[    0.389984] ACPI Error (uteval-0250): Method execution failed [\SECD.S_D0._STA] (Node f6c1a960), AE_NOT_EXIST
[    0.390000] ACPI Error: No handler for Region [SACS] (f6c440c8) [PCI_Config] (20090903/evregion-319)
[    0.390005] ACPI Error: Region PCI_Config(2) has no handler (20090903/exfldio-295)
[    0.390010] ACPI Error (psparse-0537): Method parse/execution failed [\SECD.S_D1._STA] (Node f6c1aa08), AE_NOT_EXIST
[    0.390030] ACPI Error (uteval-0250): Method execution failed [\SECD.S_D1._STA] (Node f6c1aa08), AE_NOT_EXIST
[    0.390040] pnp: PnP ACPI: found 15 devices
[    0.390041] ACPI: ACPI bus type pnp unregistered
[    0.390044] PnPBIOS: Disabled by ACPI PNP
[    0.390056] system 00:09: ioport range 0xe00-0xe0f has been reserved
[    0.390059] system 00:09: ioport range 0xe80-0xe8f has been reserved
[    0.390062] system 00:09: ioport range 0xf40-0xf4f has been reserved
[    0.390065] system 00:09: ioport range 0xa30-0xa3f has been reserved
[    0.390070] system 00:0b: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.390073] system 00:0b: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.390078] system 00:0c: ioport range 0x4d0-0x4d1 has been reserved
[    0.390081] system 00:0c: ioport range 0x40b-0x40b has been reserved
[    0.390083] system 00:0c: ioport range 0x4d6-0x4d6 has been reserved
[    0.390086] system 00:0c: ioport range 0xc00-0xc01 has been reserved
[    0.390088] system 00:0c: ioport range 0xc14-0xc14 has been reserved
[    0.390091] system 00:0c: ioport range 0xc50-0xc51 has been reserved
[    0.390094] system 00:0c: ioport range 0xc52-0xc52 has been reserved
[    0.390096] system 00:0c: ioport range 0xc6c-0xc6c has been reserved
[    0.390099] system 00:0c: ioport range 0xc6f-0xc6f has been reserved
[    0.390102] system 00:0c: ioport range 0xcd0-0xcd1 has been reserved
[    0.390104] system 00:0c: ioport range 0xcd2-0xcd3 has been reserved
[    0.390107] system 00:0c: ioport range 0xcd4-0xcd5 has been reserved
[    0.390110] system 00:0c: ioport range 0xcd6-0xcd7 has been reserved
[    0.390112] system 00:0c: ioport range 0xcd8-0xcdf has been reserved
[    0.390115] system 00:0c: ioport range 0x800-0x89f has been reserved
[    0.390118] system 00:0c: ioport range 0xb00-0xb0f has been reserved
[    0.390120] system 00:0c: ioport range 0xb20-0xb3f has been reserved
[    0.390123] system 00:0c: ioport range 0x900-0x90f has been reserved
[    0.390126] system 00:0c: ioport range 0x910-0x91f has been reserved
[    0.390129] system 00:0c: ioport range 0xfe00-0xfefe has been reserved
[    0.390132] system 00:0c: iomem range 0xffb80000-0xffbfffff has been reserved
[    0.390135] system 00:0c: iomem range 0xfec10000-0xfec1001f has been reserved
[    0.390140] system 00:0d: iomem range 0xe0000000-0xefffffff has been reserved
[    0.390145] system 00:0e: iomem range 0x0-0x9ffff could not be reserved
[    0.390148] system 00:0e: iomem range 0xc0000-0xcffff could not be reserved
[    0.390151] system 00:0e: iomem range 0xe0000-0xfffff could not be reserved
[    0.390153] system 00:0e: iomem range 0x100000-0xcfffffff could not be reserved
[    0.390156] system 00:0e: iomem range 0xfec00000-0xffffffff could not be reserved
[    0.424902] pci 0000:00:02.0: PCI bridge, secondary bus 0000:01
[    0.424905] pci 0000:00:02.0:   IO window: 0xd000-0xdfff
[    0.424908] pci 0000:00:02.0:   MEM window: 0xfc000000-0xfeafffff
[    0.424911] pci 0000:00:02.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
[    0.424916] pci 0000:00:07.0: PCI bridge, secondary bus 0000:02
[    0.424918] pci 0000:00:07.0:   IO window: 0xe000-0xefff
[    0.424921] pci 0000:00:07.0:   MEM window: 0xfeb00000-0xfebfffff
[    0.424924] pci 0000:00:07.0:   PREFETCH window: 0x000000faf00000-0x000000faffffff
[    0.424929] pci 0000:00:14.4: PCI bridge, secondary bus 0000:03
[    0.424930] pci 0000:00:14.4:   IO window: disabled
[    0.424935] pci 0000:00:14.4:   MEM window: disabled
[    0.424939] pci 0000:00:14.4:   PREFETCH window: disabled
[    0.424952] pci 0000:00:02.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.424957] pci 0000:00:02.0: setting latency timer to 64
[    0.424963] pci 0000:00:07.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.424966] pci 0000:00:07.0: setting latency timer to 64
[    0.424974] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.424977] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.424979] pci_bus 0000:01: resource 0 io:  [0xd000-0xdfff]
[    0.424982] pci_bus 0000:01: resource 1 mem: [0xfc000000-0xfeafffff]
[    0.424984] pci_bus 0000:01: resource 2 pref mem [0xd0000000-0xdfffffff]
[    0.424987] pci_bus 0000:02: resource 0 io:  [0xe000-0xefff]
[    0.424989] pci_bus 0000:02: resource 1 mem: [0xfeb00000-0xfebfffff]
[    0.424991] pci_bus 0000:02: resource 2 pref mem [0xfaf00000-0xfaffffff]
[    0.424994] pci_bus 0000:03: resource 3 io:  [0x00-0xffff]
[    0.424996] pci_bus 0000:03: resource 4 mem: [0x000000-0xffffffff]
[    0.425022] NET: Registered protocol family 2
[    0.425100] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.425365] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.425860] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.426114] TCP: Hash tables configured (established 131072 bind 65536)
[    0.426117] TCP reno registered
[    0.426184] NET: Registered protocol family 1
[    0.607994] pci 0000:01:00.0: Boot video device
[    0.608038] Unpacking initramfs...
[    0.812387] Freeing initrd memory: 8265k freed
[    0.816015] audit: initializing netlink socket (disabled)
[    0.816027] type=2000 audit(1286006562.815:1): initialized
[    0.816236] highmem bounce pool size: 64 pages
[    0.816240] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.817480] VFS: Disk quotas dquot_6.5.2
[    0.817529] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.817592] msgmni has been set to 1703
[    0.817811] alg: No test for stdrng (krng)
[    0.817857] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.817860] io scheduler noop registered
[    0.817862] io scheduler anticipatory registered
[    0.817864] io scheduler deadline registered
[    0.817896] io scheduler cfq registered (default)
[    0.817994] pcieport 0000:00:02.0: irq 25 for MSI/MSI-X
[    0.818000] pcieport 0000:00:02.0: setting latency timer to 64
[    0.818069] pcieport 0000:00:07.0: irq 26 for MSI/MSI-X
[    0.818073] pcieport 0000:00:07.0: setting latency timer to 64
[    0.818180] isapnp: Scanning for PnP cards...
[    1.175176] isapnp: No Plug & Play device found
[    1.176283] Linux agpgart interface v0.103
[    1.176529] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    1.176639] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.176926] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.177091] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    1.177093] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    1.177233] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.177282] mice: PS/2 mouse device common for all mice
[    1.177318] rtc_cmos 00:03: RTC can wake from S4
[    1.177344] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    1.177370] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    1.177381] cpuidle: using governor ladder
[    1.177383] cpuidle: using governor menu
[    1.177387] No iBFT detected.
[    1.177732] TCP cubic registered
[    1.177860] NET: Registered protocol family 10
[    1.178303] lo: Disabled Privacy Extensions
[    1.178619] Mobile IPv6
[    1.178621] NET: Registered protocol family 17
[    1.178634] Using IPI No-Shortcut mode
[    1.178683] PM: Resume from disk failed.
[    1.178687] registered taskstats version 1
[    1.178992] rtc_cmos 00:03: setting system clock to 2010-10-02 08:02:43 UTC (1286006563)
[    1.179026] Initalizing network drop monitor service
[    1.179053] Freeing unused kernel memory: 372k freed
[    1.179279] Write protecting the kernel text: 2492k
[    1.179317] Write protecting the kernel read-only data: 916k
[    1.195736] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input0
[    1.197598] udev: starting version 157
[    1.252854] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.252880] r8169 0000:02:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.252911] r8169 0000:02:00.0: setting latency timer to 64
[    1.252953] r8169 0000:02:00.0: irq 27 for MSI/MSI-X
[    1.253484] eth0: RTL8168c/8111c at 0xf7cb4000, 00:e0:4d:98:77:cc, XID 1c4000c0 IRQ 27
[    1.256682] usbcore: registered new interface driver usbfs
[    1.256710] usbcore: registered new interface driver hub
[    1.263075] thermal LNXTHERM:01: registered as thermal_zone0
[    1.263081] ACPI: Thermal Zone [THRM] (27 C)
[    1.265033] usbcore: registered new device driver usb
[    1.275170] SCSI subsystem initialized
[    1.291431] libata version 3.00 loaded.
[    1.293153] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.293195] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.293215] ehci_hcd 0000:00:12.2: EHCI Host Controller
[    1.293237] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
[    1.293264] ehci_hcd 0000:00:12.2: applying AMD SB600/SB700 USB freeze workaround
[    1.293278] ehci_hcd 0000:00:12.2: debug port 1
[    1.293301] ehci_hcd 0000:00:12.2: irq 17, io mem 0xfbfff000
[    1.300043] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.305525] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00
[    1.305550] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    1.305553] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.305555] usb usb1: Product: EHCI Host Controller
[    1.305557] usb usb1: Manufacturer: Linux 2.6.32-5-686 ehci_hcd
[    1.305559] usb usb1: SerialNumber: 0000:00:12.2
[    1.305639] usb usb1: configuration #1 chosen from 1 choice
[    1.305669] hub 1-0:1.0: USB hub found
[    1.305677] hub 1-0:1.0: 6 ports detected
[    1.305743] ahci 0000:00:11.0: version 3.0
[    1.305769] ahci 0000:00:11.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    1.305877] ahci 0000:00:11.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[    1.305881] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part ccc 
[    1.306190] scsi0 : ahci
[    1.306280] scsi1 : ahci
[    1.306334] scsi2 : ahci
[    1.306388] scsi3 : ahci
[    1.306429] ata1: SATA max UDMA/133 abar m1024@0xfbfff800 port 0xfbfff900 irq 22
[    1.306433] ata2: SATA max UDMA/133 abar m1024@0xfbfff800 port 0xfbfff980 irq 22
[    1.306436] ata3: SATA max UDMA/133 abar m1024@0xfbfff800 port 0xfbfffa00 irq 22
[    1.306441] ata4: SATA max UDMA/133 abar m1024@0xfbfff800 port 0xfbfffa80 irq 22
[    1.306499] pata_atiixp 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.306538] pata_atiixp 0000:00:14.1: setting latency timer to 64
[    1.306600] scsi4 : pata_atiixp
[    1.306677] scsi5 : pata_atiixp
[    1.307830] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xff00 irq 14
[    1.307833] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xff08 irq 15
[    1.307884] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.307900] ohci_hcd 0000:00:12.0: OHCI Host Controller
[    1.307912] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 2
[    1.307938] ohci_hcd 0000:00:12.0: irq 16, io mem 0xfbffe000
[    1.364029] usb usb2: New USB device found, idVendor=1d6b, idProduct=0001
[    1.364031] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.364033] usb usb2: Product: OHCI Host Controller
[    1.364035] usb usb2: Manufacturer: Linux 2.6.32-5-686 ohci_hcd
[    1.364037] usb usb2: SerialNumber: 0000:00:12.0
[    1.364104] usb usb2: configuration #1 chosen from 1 choice
[    1.364131] hub 2-0:1.0: USB hub found
[    1.364143] hub 2-0:1.0: 3 ports detected
[    1.364203] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.364214] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    1.364221] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 3
[    1.364239] ehci_hcd 0000:00:13.2: applying AMD SB600/SB700 USB freeze workaround
[    1.364253] ehci_hcd 0000:00:13.2: debug port 1
[    1.364270] ehci_hcd 0000:00:13.2: irq 19, io mem 0xfbffa800
[    1.376020] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    1.376033] usb usb3: New USB device found, idVendor=1d6b, idProduct=0002
[    1.376035] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.376037] usb usb3: Product: EHCI Host Controller
[    1.376039] usb usb3: Manufacturer: Linux 2.6.32-5-686 ehci_hcd
[    1.376041] usb usb3: SerialNumber: 0000:00:13.2
[    1.376095] usb usb3: configuration #1 chosen from 1 choice
[    1.376125] hub 3-0:1.0: USB hub found
[    1.376130] hub 3-0:1.0: 6 ports detected
[    1.376206] ohci_hcd 0000:00:12.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.376215] ohci_hcd 0000:00:12.1: OHCI Host Controller
[    1.376222] ohci_hcd 0000:00:12.1: new USB bus registered, assigned bus number 4
[    1.376236] ohci_hcd 0000:00:12.1: irq 16, io mem 0xfbffd000
[    1.436020] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
[    1.436023] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.436025] usb usb4: Product: OHCI Host Controller
[    1.436027] usb usb4: Manufacturer: Linux 2.6.32-5-686 ohci_hcd
[    1.436028] usb usb4: SerialNumber: 0000:00:12.1
[    1.436080] usb usb4: configuration #1 chosen from 1 choice
[    1.436105] hub 4-0:1.0: USB hub found
[    1.436112] hub 4-0:1.0: 3 ports detected
[    1.436158] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.436167] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    1.436174] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 5
[    1.436192] ohci_hcd 0000:00:13.0: irq 18, io mem 0xfbffc000
[    1.496013] usb usb5: New USB device found, idVendor=1d6b, idProduct=0001
[    1.496016] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.496018] usb usb5: Product: OHCI Host Controller
[    1.496020] usb usb5: Manufacturer: Linux 2.6.32-5-686 ohci_hcd
[    1.496022] usb usb5: SerialNumber: 0000:00:13.0
[    1.496074] usb usb5: configuration #1 chosen from 1 choice
[    1.496097] hub 5-0:1.0: USB hub found
[    1.496108] hub 5-0:1.0: 3 ports detected
[    1.496151] ohci_hcd 0000:00:13.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.496161] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    1.496167] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 6
[    1.496180] ohci_hcd 0000:00:13.1: irq 18, io mem 0xfbffb000
[    1.556051] usb usb6: New USB device found, idVendor=1d6b, idProduct=0001
[    1.556054] usb usb6: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.556056] usb usb6: Product: OHCI Host Controller
[    1.556058] usb usb6: Manufacturer: Linux 2.6.32-5-686 ohci_hcd
[    1.556060] usb usb6: SerialNumber: 0000:00:13.1
[    1.556111] usb usb6: configuration #1 chosen from 1 choice
[    1.556134] hub 6-0:1.0: USB hub found
[    1.556147] hub 6-0:1.0: 3 ports detected
[    1.556190] ohci_hcd 0000:00:14.5: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.556200] ohci_hcd 0000:00:14.5: OHCI Host Controller
[    1.556207] ohci_hcd 0000:00:14.5: new USB bus registered, assigned bus number 7
[    1.556220] ohci_hcd 0000:00:14.5: irq 18, io mem 0xfbff9000
[    1.616010] usb 1-1: new high speed USB device using ehci_hcd and address 2
[    1.616027] usb usb7: New USB device found, idVendor=1d6b, idProduct=0001
[    1.616029] usb usb7: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.616031] usb usb7: Product: OHCI Host Controller
[    1.616033] usb usb7: Manufacturer: Linux 2.6.32-5-686 ohci_hcd
[    1.616035] usb usb7: SerialNumber: 0000:00:14.5
[    1.616089] usb usb7: configuration #1 chosen from 1 choice
[    1.616113] hub 7-0:1.0: USB hub found
[    1.616120] hub 7-0:1.0: 2 ports detected
[    1.624025] ata1: SATA link down (SStatus 0 SControl 300)
[    1.624052] ata2: SATA link down (SStatus 0 SControl 300)
[    1.624097] ata4: SATA link down (SStatus 0 SControl 300)
[    1.765037] usb 1-1: New USB device found, idVendor=0846, idProduct=9030
[    1.765041] usb 1-1: New USB device strings: Mfr=16, Product=32, SerialNumber=48
[    1.765043] usb 1-1: Product: WNA1100
[    1.765045] usb 1-1: Manufacturer: NETGEAR WNA
[    1.765047] usb 1-1: SerialNumber: 12345
[    1.765120] usb 1-1: configuration #1 chosen from 1 choice
[    1.792021] ata3: softreset failed (device not ready)
[    1.792067] ata3: applying SB600 PMP SRST workaround and retrying
[    1.952031] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.952839] ata3.00: ATA-7: HDS728080PLA380, PF2OA6EA, max UDMA/133
[    1.952842] ata3.00: 160836480 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.953815] ata3.00: configured for UDMA/133
[    1.968112] scsi 2:0:0:0: Direct-Access     ATA      HDS728080PLA380  PF2O PQ: 0 ANSI: 5
[    2.156024] usb 1-5: new high speed USB device using ehci_hcd and address 6
[    2.290606] usb 1-5: New USB device found, idVendor=058f, idProduct=6362
[    2.290609] usb 1-5: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    2.290611] usb 1-5: Product: Mass Storage Device
[    2.290613] usb 1-5: Manufacturer: Generic
[    2.290614] usb 1-5: SerialNumber: 058F312D81B1
[    2.290664] usb 1-5: configuration #1 chosen from 1 choice
[    2.297753] Initializing USB Mass Storage driver...
[    2.297846] scsi6 : SCSI emulation for USB Mass Storage devices
[    2.297906] usb-storage: device found at 6
[    2.297908] usb-storage: waiting for device to settle before scanning
[    2.297918] usbcore: registered new interface driver usb-storage
[    2.297921] USB Mass Storage support registered.
[    2.325710] ata6.00: ATA-6: WDC WD2500JB-00FUA0, 15.05R15, max UDMA/100
[    2.325713] ata6.00: 488397168 sectors, multi 16: LBA48 
[    2.325747] ata6.01: ATAPI: ATAPI   DVD A  DH20A4P, 9P59, max UDMA/66
[    2.345655] ata6.00: configured for UDMA/100
[    2.376419] ata6.01: configured for UDMA/66
[    2.377180] scsi 5:0:0:0: Direct-Access     ATA      WDC WD2500JB-00F 15.0 PQ: 0 ANSI: 5
[    2.378341] scsi 5:0:1:0: CD-ROM            ATAPI    DVD A  DH20A4P   9P59 PQ: 0 ANSI: 5
[    2.385463] sd 2:0:0:0: [sda] 160836480 512-byte logical blocks: (82.3 GB/76.6 GiB)
[    2.385502] sd 2:0:0:0: [sda] Write Protect is off
[    2.385505] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.385521] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.385617]  sda:
[    2.385699] sd 5:0:0:0: [sdb] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    2.385731] sd 5:0:0:0: [sdb] Write Protect is off
[    2.385733] sd 5:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    2.385747] sd 5:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.385826]  sdb: sda1 sda2 < sdb1
[    2.396034] sd 5:0:0:0: [sdb] Attached SCSI disk
[    2.407754]  sda5 sda6 >
[    2.414278] sd 2:0:0:0: [sda] Attached SCSI disk
[    2.450998] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.451003] Uniform CD-ROM driver Revision: 3.20
[    2.451077] sr 5:0:1:0: Attached scsi CD-ROM sr0
[    2.455059] sd 2:0:0:0: Attached scsi generic sg0 type 0
[    2.455089] sd 5:0:0:0: Attached scsi generic sg1 type 0
[    2.455119] sr 5:0:1:0: Attached scsi generic sg2 type 5
[    2.552081] usb 4-1: new low speed USB device using ohci_hcd and address 2
[    2.726789] usb 4-1: New USB device found, idVendor=04f3, idProduct=0230
[    2.726792] usb 4-1: New USB device strings: Mfr=0, Product=2, SerialNumber=0
[    2.726794] usb 4-1: Product: USB+PS/2 Optical Mouse
[    2.726871] usb 4-1: configuration #1 chosen from 1 choice
[    2.739185] usbcore: registered new interface driver hiddev
[    2.742994] input: USB+PS/2 Optical Mouse as /devices/pci0000:00/0000:00:12.1/usb4/4-1/4-1:1.0/input/input1
[    2.743056] generic-usb 0003:04F3:0230.0001: input,hidraw0: USB HID v1.11 Mouse [USB+PS/2 Optical Mouse] on usb-0000:00:12.1-1/input0
[    2.743083] usbcore: registered new interface driver usbhid
[    2.743086] usbhid: v2.6:USB HID core driver
[    2.844018] usb 3-3: new high speed USB device using ehci_hcd and address 2
[    2.974119] usb 3-3: New USB device found, idVendor=0781, idProduct=5406
[    2.974123] usb 3-3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    2.974125] usb 3-3: Product: U3 Cruzer Micro
[    2.974127] usb 3-3: Manufacturer: SanDisk
[    2.974129] usb 3-3: SerialNumber: 1738310F1D535C34
[    2.974207] usb 3-3: configuration #1 chosen from 1 choice
[    2.974332] scsi7 : SCSI emulation for USB Mass Storage devices
[    2.974457] usb-storage: device found at 2
[    2.974459] usb-storage: waiting for device to settle before scanning
[    3.107632] EXT4-fs (sda1): mounted filesystem with ordered data mode
[    3.240011] usb 2-2: new full speed USB device using ohci_hcd and address 2
[    3.414631] usb 2-2: New USB device found, idVendor=0d8c, idProduct=0121
[    3.414634] usb 2-2: New USB device strings: Mfr=3, Product=1, SerialNumber=0
[    3.414637] usb 2-2: Product: USB PnP Audio Device
[    3.414640] usb 2-2: Manufacturer: C-Media Electronics Inc.
[    3.414728] usb 2-2: configuration #1 chosen from 1 choice
[    3.422720] input: C-Media Electronics Inc. USB PnP Audio Device as /devices/pci0000:00/0000:00:12.0/usb2/2-2/2-2:1.2/input/input2
[    3.422761] generic-usb 0003:0D8C:0121.0002: input,hidraw1: USB HID v1.00 Device [C-Media Electronics Inc. USB PnP Audio Device] on usb-0000:00:12.0-2/input2
[    3.692022] usb 2-3: new full speed USB device using ohci_hcd and address 3
[    3.869531] usb 2-3: New USB device found, idVendor=0403, idProduct=6001
[    3.869534] usb 2-3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    3.869537] usb 2-3: Product: FT232R USB UART
[    3.869539] usb 2-3: Manufacturer: FTDI
[    3.869541] usb 2-3: SerialNumber: A600aEvn
[    3.869623] usb 2-3: configuration #1 chosen from 1 choice
[    3.948381] udev: starting version 157
[    4.093063] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input3
[    4.093081] ACPI: Power Button [PWRB]
[    4.093141] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input4
[    4.093144] ACPI: Power Button [PWRF]
[    4.168342] input: PC Speaker as /devices/platform/pcspkr/input/input5
[    4.359042] [drm] Initialized drm 1.1.0 20060810
[    4.417549] parport_pc 00:08: reported by Plug and Play ACPI
[    4.417613] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[    4.435125] ACPI: I/O resource piix4_smbus [0xb00-0xb07] conflicts with ACPI region SOR1 [0xb00-0xb0f]
[    4.435174] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    4.438275] processor LNXCPU:00: registered as cooling_device0
[    4.438329] processor LNXCPU:01: registered as cooling_device1
[    4.438364] processor LNXCPU:02: registered as cooling_device2
[    4.438398] processor LNXCPU:03: registered as cooling_device3
[    4.900057] nouveau 0000:01:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    4.900063] nouveau 0000:01:00.0: setting latency timer to 64
[    4.901950] [drm] nouveau 0000:01:00.0: Detected an NV40 generation card (0x04b100a2)
[    4.902264] [drm] nouveau 0000:01:00.0: Attempting to load BIOS image from PROM
[    4.912986] usbcore: registered new interface driver usbserial
[    4.913005] USB Serial support registered for generic
[    4.913053] usbcore: registered new interface driver usbserial_generic
[    4.913055] usbserial: USB Serial Driver core
[    4.953130] USB Serial support registered for FTDI USB Serial Device
[    4.953268] ftdi_sio 2-3:1.0: FTDI USB Serial Device converter detected
[    4.953345] usb 2-3: Detected FT232RL
[    4.953347] usb 2-3: Number of endpoints 2
[    4.953349] usb 2-3: Endpoint 1 MaxPacketSize 64
[    4.953351] usb 2-3: Endpoint 2 MaxPacketSize 64
[    4.953353] usb 2-3: Setting MaxPacketSize 64
[    4.954373] usb 2-3: FTDI USB Serial Device converter now attached to ttyUSB0
[    4.954385] usbcore: registered new interface driver ftdi_sio
[    4.954387] ftdi_sio: v1.5.0:USB FTDI Serial Converters Driver
[    4.973327] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    5.069404] usbcore: registered new interface driver snd-usb-audio
[    5.119845] [drm] nouveau 0000:01:00.0: ... appears to be valid
[    5.119848] [drm] nouveau 0000:01:00.0: BIT BIOS found
[    5.119851] [drm] nouveau 0000:01:00.0: Bios version 05.73.22.18
[    5.119854] [drm] nouveau 0000:01:00.0: TMDS table script pointers not stubbed
[    5.119856] [drm] nouveau 0000:01:00.0: BIT table 'd' not found
[    5.119859] [drm] nouveau 0000:01:00.0: Found Display Configuration Block version 3.0
[    5.119862] [drm] nouveau 0000:01:00.0: DCB connector table: VHER 0x30 5 10 2
[    5.119865] [drm] nouveau 0000:01:00.0:   0: 0x00001030: type 0x30 idx 0 tag 0x07
[    5.119868] [drm] nouveau 0000:01:00.0:   1: 0x00002130: type 0x30 idx 1 tag 0x08
[    5.119870] [drm] nouveau 0000:01:00.0:   2: 0x00000210: type 0x10 idx 2 tag 0xff
[    5.119873] [drm] nouveau 0000:01:00.0:   3: 0x00000211: type 0x11 idx 2 tag 0xff
[    5.119875] [drm] nouveau 0000:01:00.0:   4: 0x00000213: type 0x13 idx 2 tag 0xff
[    5.119878] [drm] nouveau 0000:01:00.0: Raw DCB entry 0: 01000300 00000028
[    5.119881] [drm] nouveau 0000:01:00.0: Raw DCB entry 1: 03000302 00000000
[    5.119884] [drm] nouveau 0000:01:00.0: Raw DCB entry 2: 04011310 00000028
[    5.119886] [drm] nouveau 0000:01:00.0: Raw DCB entry 3: 04011312 00000000
[    5.119888] [drm] nouveau 0000:01:00.0: Raw DCB entry 4: 020223f1 00c0c080
[    5.119897] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 0 at offset 0xDE3C
[    5.119995] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 1 at offset 0xE4B6
[    5.168029] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 2 at offset 0xEB4C
[    5.168049] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 3 at offset 0xECCC
[    5.188614] hda_codec: ALC888: BIOS auto-probing.
[    5.190501] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:14.2/input/input6
[    5.192019] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 4 at offset 0xEE26
[    5.206136] [TTM] Zone  kernel: Available graphics memory: 436242 kiB.
[    5.206138] [TTM] Zone highmem: Available graphics memory: 1687414 kiB.
[    5.206149] [drm] nouveau 0000:01:00.0: 256 MiB VRAM
[    5.207085] [drm] nouveau 0000:01:00.0: 64 MiB GART (aperture)
[    5.208398] [drm] nouveau 0000:01:00.0: Allocating FIFO number 0
[    5.209748] [drm] nouveau 0000:01:00.0: nouveau_channel_alloc: initialised FIFO 0
[    5.209756] [drm] nouveau 0000:01:00.0: Initial CRTC_OWNER is 0
[    5.209764] [drm] nouveau 0000:01:00.0: Saving VGA fonts
[    5.260519] [drm] nouveau 0000:01:00.0: Detected a DVI-I connector
[    5.260575] [drm] nouveau 0000:01:00.0: Detected a DVI-I connector
[    5.260599] [drm] nouveau 0000:01:00.0: Detected a TV connector
[    5.262436] [drm] nouveau 0000:01:00.0: Setting dpms mode 3 on vga encoder (output 0)
[    5.262439] [drm] nouveau 0000:01:00.0: Setting dpms mode 3 on tmds encoder (output 1)
[    5.262442] [drm] nouveau 0000:01:00.0: Setting dpms mode 3 on vga encoder (output 2)
[    5.262445] [drm] nouveau 0000:01:00.0: Setting dpms mode 3 on tmds encoder (output 3)
[    5.262447] [drm] nouveau 0000:01:00.0: Setting dpms mode 3 on TV encoder (output 4)
[    5.448159] [drm] nouveau 0000:01:00.0: allocated 1440x900 fb: 0x49000, bo f65b3c00
[    5.459343] [drm] nouveau 0000:01:00.0: Output DVI-I-1 is running on CRTC 0 using output A
[    5.459347] [drm] nouveau 0000:01:00.0: 0xD1F4: Parsing digital output script table
[    5.516026] [drm] nouveau 0000:01:00.0: Setting dpms mode 0 on tmds encoder (output 1)
[    5.516031] [drm] nouveau 0000:01:00.0: Output DVI-I-1 is running on CRTC 0 using output A
[    5.517086] Console: switching to colour frame buffer device 180x56
[    5.518050] fb0: nouveaufb frame buffer device
[    5.518051] registered panic notifier
[    5.518057] [drm] Initialized nouveau 0.0.15 20090420 for 0000:01:00.0 on minor 0
[    6.001386] Adding 3066872k swap on /dev/sda5.  Priority:-1 extents:1 across:3066872k 
[    6.291160] loop: module loaded
[    6.768962] kjournald starting.  Commit interval 5 seconds
[    6.769163] EXT3 FS on sda6, internal journal
[    6.769168] EXT3-fs: mounted filesystem with ordered data mode.
[    7.105785] fuse init (API version 7.13)
[    7.300941] usb-storage: device scan complete
[    7.301554] scsi 6:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
[    7.302170] scsi 6:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
[    7.302801] scsi 6:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ: 0 ANSI: 0
[    7.303418] scsi 6:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0
[    7.303786] sd 6:0:0:0: Attached scsi generic sg3 type 0
[    7.303912] sd 6:0:0:1: Attached scsi generic sg4 type 0
[    7.304027] sd 6:0:0:2: Attached scsi generic sg5 type 0
[    7.305893] sd 6:0:0:3: Attached scsi generic sg6 type 0
[    7.310043] sd 6:0:0:0: [sdc] Attached SCSI removable disk
[    7.310680] sd 6:0:0:1: [sdd] Attached SCSI removable disk
[    7.311289] sd 6:0:0:2: [sde] Attached SCSI removable disk
[    7.311912] sd 6:0:0:3: [sdf] Attached SCSI removable disk
[    7.972214] usb-storage: device scan complete
[    7.972571] scsi 7:0:0:0: Direct-Access     SanDisk  U3 Cruzer Micro  8.02 PQ: 0 ANSI: 0 CCS
[    7.972966] sd 7:0:0:0: Attached scsi generic sg7 type 0
[    7.973564] sd 7:0:0:0: [sdg] 3907583 512-byte logical blocks: (2.00 GB/1.86 GiB)
[    7.974307] sd 7:0:0:0: [sdg] Write Protect is off
[    7.974310] sd 7:0:0:0: [sdg] Mode Sense: 45 00 00 08
[    7.974312] sd 7:0:0:0: [sdg] Assuming drive cache: write through
[    7.977179] sd 7:0:0:0: [sdg] Assuming drive cache: write through
[    7.977192]  sdg: sdg1
[    7.980427] sd 7:0:0:0: [sdg] Assuming drive cache: write through
[    7.980438] sd 7:0:0:0: [sdg] Attached SCSI removable disk
[    9.607056] Bluetooth: Core ver 2.15
[    9.607240] NET: Registered protocol family 31
[    9.607242] Bluetooth: HCI device and connection manager initialized
[    9.607246] Bluetooth: HCI socket layer initialized
[    9.755413] Bluetooth: L2CAP ver 2.14
[    9.755416] Bluetooth: L2CAP socket layer initialized
[    9.784546] Bluetooth: RFCOMM TTY layer initialized
[    9.784550] Bluetooth: RFCOMM socket layer initialized
[    9.784552] Bluetooth: RFCOMM ver 1.11
[    9.841754] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    9.841757] Bluetooth: BNEP filters: protocol multicast
[    9.885763] Bridge firewalling registered
[    9.895644] r8169: eth0: link down
[    9.895844] ADDRCONF(NETDEV_UP): eth0: link is not ready
[    9.981055] Bluetooth: SCO (Voice Link) ver 0.6
[    9.981057] Bluetooth: SCO socket layer initialized
[   11.147194] [drm] nouveau 0000:01:00.0: Allocating FIFO number 1
[   11.148514] [drm] nouveau 0000:01:00.0: nouveau_channel_alloc: initialised FIFO 1
[   42.159842] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
eviscerate@EVI-MAIN:~$ 


```


By the way everything installed fine, and I started up the program and it loaded and asked me to restart the PC. 
Nothing shows up in the wireless connections though.

---

### Post by vagrale13 on 2010-10-02
Post the output of commands
```
cat /etc/modules
ls -l /lib/firmware/ar*
```

---

### Post by Corey4666 on 2010-10-02
```

eviscerate@EVI-MAIN:~$ cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.
# Parameters can be specified after the module name.

loop
ath9k_htc
ath9k_htc
eviscerate@EVI-MAIN:~$ 
eviscerate@EVI-MAIN:~$ ls -l /lib/firmware/ar*
-rw-r--r-- 1 root root 70608 Aug 29 20:12 /lib/firmware/ar7010.fw
-rw-r--r-- 1 root root 51280 Jul 11 10:16 /lib/firmware/ar9271.fw
eviscerate@EVI-MAIN:~$ 
```

---

### Post by vagrale13 on 2010-10-02
Strange! :confused:
What version **Ubuntu** have you?

Run 
```
sudo gedit /etc/modules
```and delete one line **ath9k_htc** 
to become like this
```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.
# Parameters can be specified after the module name.

loop
ath9k_htc
```save and close it!
Then run 
```
sudo modprobe ath9k_htc
```and post the output of 
```
lsmod | grep ath9k
```and see if it works!

---

### Post by Corey4666 on 2010-10-02
```

eviscerate@EVI-MAIN:~$ sudo modprobe ath9k_htc
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
FATAL: Module ath9k_htc not found.
eviscerate@EVI-MAIN:~$ lsmod | grep ath9k
eviscerate@EVI-MAIN:~$ 
```

:confused:

---

### Post by vagrale13 on 2010-10-02
Have you installed ndiswrapper before? 
If yes, i think there is the problem, because ndiswrapper driver stop to work more other drivers! If you want to try ath9k_htc driver, you must remove ndiswrapper first, and then try to install it! 
But must know that many times is not enough simply to remove it, 
but reinstall distro, because ndiswrapper is changing many system files, 
but many times works after just remove ndiswrapper! :KS

---

### Post by Corey4666 on 2010-10-02
do you know the command to remove ndiswrapper? I installed it from a .deb and I never updated it or tried using it with any driver files yet. So I am assuming It probably has not got integrated into my system much.

---

### Post by vagrale13 on 2010-10-02
> **Corey4666 said:**
> do you know the command to remove ndiswrapper? I installed it from a .deb and I never updated it or tried using it with any driver files yet. So I am assuming It probably has not got integrated into my system much.
Try to remove from synaptic the packages
```
ndisgtk
ndiswrapper-utils
ndiswrapper-common
```

---

### Post by Corey4666 on 2010-10-03
Hey, I have a clean install of ubuntu 8.10 64bit. I tried installing ath9k_htc_installer_1.0_all.deb again, Then ran it from the application menu and restarted the PC. I still don't see nothing changed! I look in network connections, seems like nothing is happening. :(

To remind you, I am using NETGEAR WNA1100 USB adapter.

---

### Post by vagrale13 on 2010-10-03
> **Corey4666 said:**
> Hey, I have a clean install of ubuntu 8.10 64bit. I tried installing ath9k_htc_installer_1.0_all.deb again, Then ran it from the application menu and restarted the PC. I still don't see nothing changed! I look in network connections, seems like nothing is happening. :(

To remind you, I am using NETGEAR WNA1100 USB adapter.
Why you install 8.10 and not 10.04 LTS or 10.10 ? :confused:
Post #[**3**]("http://ubuntuforums.org/showpost.php?p=9909230&postcount=3") say that with the same usb wireless work!
can you post again the output of commands
```
uname -r
lsmod | grep ath9k
dmesg
cat /etc/modules
ls -l /lib/firmware/ar*
```

---

### Post by Corey4666 on 2010-10-03
There.. Reason I use a older version is because I have a FAP limit on my internet. I can download the new version over night but my internet is so slow it wouldn't be possible. Also i usually get corrupted downloads over a few hundred mb's. This copy of ubuntu I have was mailed to me.

```
eviscerate@evi-main:~$ uname -r
2.6.27-7-generic



eviscerate@evi-main:~$ lsmod | grep ath9k
ath9k_htc              61188  0 
mac80211              285840  1 ath9k_htc
ath9k_common           15232  1 ath9k_htc
ath9k_hw              317744  2 ath9k_htc,ath9k_common
led_class              13192  1 ath9k_htc
ath                    19712  2 ath9k_htc,ath9k_hw
cfg80211              178248  3 ath9k_htc,mac80211,ath
compat_firmware_class    18048  1 ath9k_htc
usbcore               175376  12 ath9k_htc,compat,snd_usb_audio,snd_usb_lib,ftdi_sio,usbserial,usb_storage,usbhid,libusual,ehci_hcd,ohci_hcd



[    0.720105] system 00:0e: ioport range 0xcd8-0xcdf has been reserved
[    0.720107] system 00:0e: ioport range 0x800-0x89f has been reserved
[    0.720109] system 00:0e: ioport range 0xb00-0xb0f has been reserved
[    0.720111] system 00:0e: ioport range 0xb20-0xb3f has been reserved
[    0.720112] system 00:0e: ioport range 0x900-0x90f has been reserved
[    0.720114] system 00:0e: ioport range 0x910-0x91f has been reserved
[    0.720117] system 00:0e: ioport range 0xfe00-0xfefe has been reserved
[    0.720119] system 00:0e: iomem range 0xffb80000-0xffbfffff could not be reserved
[    0.720121] system 00:0e: iomem range 0xfec10000-0xfec1001f has been reserved
[    0.720127] system 00:0f: iomem range 0xe0000000-0xefffffff could not be reserved
[    0.720133] system 00:10: iomem range 0x0-0x9ffff could not be reserved
[    0.720135] system 00:10: iomem range 0xc0000-0xcffff has been reserved
[    0.720137] system 00:10: iomem range 0xe0000-0xfffff could not be reserved
[    0.720139] system 00:10: iomem range 0x100000-0xcfffffff could not be reserved
[    0.720141] system 00:10: iomem range 0xfec00000-0xffffffff could not be reserved
[    0.725283] pci 0000:00:02.0: PCI bridge, secondary bus 0000:01
[    0.725286] pci 0000:00:02.0:   IO window: 0xd000-0xdfff
[    0.725289] pci 0000:00:02.0:   MEM window: 0xfc000000-0xfeafffff
[    0.725292] pci 0000:00:02.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
[    0.725296] pci 0000:00:07.0: PCI bridge, secondary bus 0000:02
[    0.725298] pci 0000:00:07.0:   IO window: 0xe000-0xefff
[    0.725301] pci 0000:00:07.0:   MEM window: 0xfeb00000-0xfebfffff
[    0.725303] pci 0000:00:07.0:   PREFETCH window: 0x000000faf00000-0x000000faffffff
[    0.725306] pci 0000:00:14.4: PCI bridge, secondary bus 0000:03
[    0.725308] pci 0000:00:14.4:   IO window: disabled
[    0.725312] pci 0000:00:14.4:   MEM window: disabled
[    0.725316] pci 0000:00:14.4:   PREFETCH window: disabled
[    0.725333] pci 0000:00:02.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.725337] pci 0000:00:02.0: setting latency timer to 64
[    0.725343] pci 0000:00:07.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.725345] pci 0000:00:07.0: setting latency timer to 64
[    0.725353] bus: 00 index 0 io port: [0, ffff]
[    0.725354] bus: 00 index 1 mmio: [0, ffffffffffffffff]
[    0.725356] bus: 01 index 0 io port: [d000, dfff]
[    0.725358] bus: 01 index 1 mmio: [fc000000, feafffff]
[    0.725359] bus: 01 index 2 mmio: [d0000000, dfffffff]
[    0.725360] bus: 01 index 3 mmio: [0, 0]
[    0.725362] bus: 02 index 0 io port: [e000, efff]
[    0.725363] bus: 02 index 1 mmio: [feb00000, febfffff]
[    0.725364] bus: 02 index 2 mmio: [faf00000, faffffff]
[    0.725366] bus: 02 index 3 mmio: [0, 0]
[    0.725367] bus: 03 index 0 mmio: [0, 0]
[    0.725368] bus: 03 index 1 mmio: [0, 0]
[    0.725369] bus: 03 index 2 mmio: [0, 0]
[    0.725371] bus: 03 index 3 io port: [0, ffff]
[    0.725372] bus: 03 index 4 mmio: [0, ffffffffffffffff]
[    0.725384] NET: Registered protocol family 2
[    0.764157] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.765456] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.769074] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.769520] TCP: Hash tables configured (established 524288 bind 65536)
[    0.769522] TCP reno registered
[    0.780112] NET: Registered protocol family 1
[    0.780223] checking if image is initramfs... it is
[    1.357146] Freeing initrd memory: 8446k freed
[    1.361924] audit: initializing netlink socket (disabled)
[    1.361937] type=2000 audit(1286105599.360:1): initialized
[    1.366688] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.369110] VFS: Disk quotas dquot_6.5.1
[    1.369186] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.369277] msgmni has been set to 7920
[    1.369389] io scheduler noop registered
[    1.369391] io scheduler anticipatory registered
[    1.369392] io scheduler deadline registered
[    1.369500] io scheduler cfq registered (default)
[    1.552057] pci 0000:01:00.0: Boot video device
[    1.552167] pcieport-driver 0000:00:02.0: setting latency timer to 64
[    1.552187] pcieport-driver 0000:00:02.0: found MSI capability
[    1.552210] pci_express 0000:00:02.0:pcie00: allocate port service
[    1.552280] pcieport-driver 0000:00:07.0: setting latency timer to 64
[    1.552298] pcieport-driver 0000:00:07.0: found MSI capability
[    1.552318] pci_express 0000:00:07.0:pcie00: allocate port service
[    1.586293] hpet_resources: 0xfed00000 is busy
[    1.586385] Linux agpgart interface v0.103
[    1.586389] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.586536] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.587243] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    1.588982] brd: module loaded
[    1.589053] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    1.589163] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PSMS] at 0x60,0x64 irq 1,12
[    1.589578] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.589585] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.617636] mice: PS/2 mouse device common for all mice
[    1.617768] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    1.617791] rtc0: alarms up to one month, y3k, hpet irqs
[    1.617836] cpuidle: using governor ladder
[    1.617837] cpuidle: using governor menu
[    1.618183] TCP cubic registered
[    1.618398] registered taskstats version 1
[    1.618537]   Magic number: 14:443:579
[    1.618617] mem kmem: hash matches
[    1.618623] pci_bus 0000:00: hash matches
[    1.618675] rtc_cmos 00:05: setting system clock to 2010-10-03 11:33:20 UTC (1286105600)
[    1.618678] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.618679] EDD information not available.
[    1.618721] Freeing unused kernel memory: 536k freed
[    1.618919] Write protecting the kernel read-only data: 4348k
[    1.636008] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    1.740256] fuse init (API version 7.9)
[    1.764778] processor ACPI0007:00: registered as cooling_device0
[    1.764783] ACPI: Processor [P001] (supports 8 throttling states)
[    1.764881] processor ACPI0007:01: registered as cooling_device1
[    1.764945] processor ACPI0007:02: registered as cooling_device2
[    1.765012] processor ACPI0007:03: registered as cooling_device3
[    1.767572] thermal LNXTHERM:01: registered as thermal_zone0
[    1.767896] ACPI: Thermal Zone [THRM] (24 C)
[    1.956937] usbcore: registered new interface driver usbfs
[    1.956969] usbcore: registered new interface driver hub
[    1.957182] No dock devices found.
[    1.966815] usbcore: registered new device driver usb
[    1.967270] SCSI subsystem initialized
[    1.974119] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.974186] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.974211] ohci_hcd 0000:00:12.0: OHCI Host Controller
[    1.974284] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 1
[    1.974332] ohci_hcd 0000:00:12.0: irq 16, io mem 0xfbffe000
[    1.987935] libata version 3.00 loaded.
[    2.033199] usb usb1: configuration #1 chosen from 1 choice
[    2.033232] hub 1-0:1.0: USB hub found
[    2.033247] hub 1-0:1.0: 3 ports detected
[    2.241304] ohci_hcd 0000:00:12.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.241325] ohci_hcd 0000:00:12.1: OHCI Host Controller
[    2.241350] ohci_hcd 0000:00:12.1: new USB bus registered, assigned bus number 2
[    2.241370] ohci_hcd 0000:00:12.1: irq 16, io mem 0xfbffd000
[    2.301159] usb usb2: configuration #1 chosen from 1 choice
[    2.301188] hub 2-0:1.0: USB hub found
[    2.301205] hub 2-0:1.0: 3 ports detected
[    2.412559] usb 1-2: new full speed USB device using ohci_hcd and address 2
[    2.508282] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    2.508299] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    2.508330] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 3
[    2.508380] ohci_hcd 0000:00:13.0: irq 18, io mem 0xfbffc000
[    2.568076] usb usb3: configuration #1 chosen from 1 choice
[    2.568101] hub 3-0:1.0: USB hub found
[    2.568110] hub 3-0:1.0: 3 ports detected
[    2.579107] usb 1-2: configuration #1 chosen from 1 choice
[    2.672165] ahci 0000:00:11.0: version 3.0
[    2.672202] ahci 0000:00:11.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    2.672314] ahci 0000:00:11.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[    2.672317] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part 
[    2.672590] scsi0 : ahci
[    2.672703] scsi1 : ahci
[    2.673056] scsi2 : ahci
[    2.673119] scsi3 : ahci
[    2.673207] ata1: SATA max UDMA/133 abar m1024@0xfbfff800 port 0xfbfff900 irq 22
[    2.673211] ata2: SATA max UDMA/133 abar m1024@0xfbfff800 port 0xfbfff980 irq 22
[    2.673214] ata3: SATA max UDMA/133 abar m1024@0xfbfff800 port 0xfbfffa00 irq 22
[    2.673217] ata4: SATA max UDMA/133 abar m1024@0xfbfff800 port 0xfbfffa80 irq 22
[    2.716014] usb 1-3: new full speed USB device using ohci_hcd and address 3
[    2.888584] usb 1-3: configuration #1 chosen from 1 choice
[    2.993530] ata1: SATA link down (SStatus 0 SControl 300)
[    3.028013] usb 2-1: new low speed USB device using ohci_hcd and address 2
[    3.197619] usb 2-1: configuration #1 chosen from 1 choice
[    3.328042] ata2: SATA link down (SStatus 0 SControl 300)
[    3.333516] usb 2-2: new full speed USB device using ohci_hcd and address 3
[    3.501565] usb 2-2: configuration #1 chosen from 1 choice
[    3.832026] ata3: softreset failed (device not ready)
[    3.832031] ata3: failed due to HW bug, retry pmp=0
[    3.996039] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    4.002790] ata3.00: ATA-7: HDS728080PLA380, PF2OA6EA, max UDMA/133
[    4.002792] ata3.00: 160836480 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    4.003580] ata3.00: configured for UDMA/133
[    4.336040] ata4: SATA link down (SStatus 0 SControl 300)
[    4.352125] scsi 2:0:0:0: Direct-Access     ATA      HDS728080PLA380  PF2O PQ: 0 ANSI: 5
[    4.352236] ohci_hcd 0000:00:13.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    4.352252] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    4.352286] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 4
[    4.352305] ohci_hcd 0000:00:13.1: irq 18, io mem 0xfbffb000
[    4.412097] usb usb4: configuration #1 chosen from 1 choice
[    4.412121] hub 4-0:1.0: USB hub found
[    4.412132] hub 4-0:1.0: 3 ports detected
[    4.621204] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    4.621221] ehci_hcd 0000:00:12.2: EHCI Host Controller
[    4.621256] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 5
[    4.621307] ehci_hcd 0000:00:12.2: debug port 1
[    4.621325] ehci_hcd 0000:00:12.2: irq 17, io mem 0xfbfff000
[    4.756022] usb 4-1: new full speed USB device using ohci_hcd and address 2
[    4.768021] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    4.768119] usb usb5: configuration #1 chosen from 1 choice
[    4.768143] hub 5-0:1.0: USB hub found
[    4.768150] hub 5-0:1.0: 6 ports detected
[    4.927018] usb 4-1: not running at top speed; connect to a high speed hub
[    4.939743] usb 4-1: configuration #1 chosen from 1 choice
[    4.943633] usb 1-2: USB disconnect, address 2
[    4.977425] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    4.977436] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    4.977460] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 6
[    4.977492] ehci_hcd 0000:00:13.2: debug port 1
[    4.977512] ehci_hcd 0000:00:13.2: irq 19, io mem 0xfbffa800
[    4.989523] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    4.989609] usb usb6: configuration #1 chosen from 1 choice
[    4.989631] hub 6-0:1.0: USB hub found
[    4.989636] hub 6-0:1.0: 6 ports detected
[    5.072025] usb 1-3: USB disconnect, address 3
[    5.197549] ohci_hcd 0000:00:14.5: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    5.197559] ohci_hcd 0000:00:14.5: OHCI Host Controller
[    5.197590] ohci_hcd 0000:00:14.5: new USB bus registered, assigned bus number 7
[    5.197605] ohci_hcd 0000:00:14.5: irq 18, io mem 0xfbff9000
[    5.201534] usb 2-1: USB disconnect, address 2
[    5.256093] usb usb7: configuration #1 chosen from 1 choice
[    5.256116] hub 7-0:1.0: USB hub found
[    5.256131] hub 7-0:1.0: 2 ports detected
[    5.328029] usb 2-2: USB disconnect, address 3
[    5.356196] pata_atiixp 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    5.356224] pata_atiixp 0000:00:14.1: setting latency timer to 64
[    5.356621] scsi4 : pata_atiixp
[    5.356693] scsi5 : pata_atiixp
[    5.358139] ata5: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xff00 irq 14
[    5.358142] ata6: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xff08 irq 15
[    5.456028] usb 4-1: USB disconnect, address 2
[    5.877650] ata6.00: ATA-6: WDC WD2500JB-00FUA0, 15.05R15, max UDMA/100
[    5.877652] ata6.00: 488397168 sectors, multi 16: LBA48 
[    5.877670] ata6.01: ATAPI: ATAPI   DVD A  DH20A4P, 9P59, max UDMA/66
[    5.895117] ata6.00: configured for UDMA/100
[    5.925913] ata6.01: configured for UDMA/66
[    5.926001] scsi 5:0:0:0: Direct-Access     ATA      WDC WD2500JB-00F 15.0 PQ: 0 ANSI: 5
[    5.929608] scsi 5:0:1:0: CD-ROM            ATAPI    DVD A  DH20A4P   9P59 PQ: 0 ANSI: 5
[    5.931806] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    5.931837] r8169 0000:02:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    5.931861] r8169 0000:02:00.0: setting latency timer to 64
[    5.932190] eth0: RTL8168c/8111c at 0xffffc2000064a000, 00:e0:4d:98:77:cc, XID 3c4000c0 IRQ 2301
[    5.951025] scsi 2:0:0:0: Attached scsi generic sg0 type 0
[    5.951060] scsi 5:0:0:0: Attached scsi generic sg1 type 0
[    5.951100] scsi 5:0:1:0: Attached scsi generic sg2 type 5
[    5.977540] usb 5-5: new high speed USB device using ehci_hcd and address 5
[    5.996060] Driver 'sd' needs updating - please use bus_type methods
[    5.996217] sd 2:0:0:0: [sda] 160836480 512-byte hardware sectors (82348 MB)
[    5.996231] sd 2:0:0:0: [sda] Write Protect is off
[    5.996234] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.996252] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.996326] sd 2:0:0:0: [sda] 160836480 512-byte hardware sectors (82348 MB)
[    5.996336] sd 2:0:0:0: [sda] Write Protect is off
[    5.996338] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.996355] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.996358]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[    6.010287]  sda1 sda2 < sda5 >
[    6.032130] sd 2:0:0:0: [sda] Attached SCSI disk
[    6.032219] sd 5:0:0:0: [sdb] 488397168 512-byte hardware sectors (250059 MB)
[    6.032235] sd 5:0:0:0: [sdb] Write Protect is off
[    6.032237] sd 5:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    6.032258] sd 5:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.032317] sd 5:0:0:0: [sdb] 488397168 512-byte hardware sectors (250059 MB)
[    6.032329] sd 5:0:0:0: [sdb] Write Protect is off
[    6.032331] sd 5:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    6.032351] sd 5:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.032354]  sdb: sdb1 sdb2 < sdb5 >
[    6.068685] sd 5:0:0:0: [sdb] Attached SCSI disk
[    6.074657] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    6.074662] Uniform CD-ROM driver Revision: 3.20
[    6.074776] sr 5:0:1:0: Attached scsi CD-ROM sr0
[    6.113048] usb 5-5: configuration #1 chosen from 1 choice
[    6.115945] usbcore: registered new interface driver libusual
[    6.115967] usbcore: registered new interface driver hiddev
[    6.124849] Initializing USB Mass Storage driver...
[    6.376025] usb 1-2: new full speed USB device using ohci_hcd and address 4
[    6.542789] usb 1-2: configuration #1 chosen from 1 choice
[    6.804020] usb 1-3: new full speed USB device using ohci_hcd and address 5
[    6.981681] usb 1-3: configuration #1 chosen from 1 choice
[    7.096029] usb 6-4: new high speed USB device using ehci_hcd and address 2
[    7.229742] usb 6-4: configuration #1 chosen from 1 choice
[    7.230078] scsi6 : SCSI emulation for USB Mass Storage devices
[    7.230174] usb-storage: device found at 5
[    7.230176] usb-storage: waiting for device to settle before scanning
[    7.234683] input: C-Media Electronics Inc. USB PnP Audio Device as /devices/pci0000:00/0000:00:12.0/usb1/1-2/1-2:1.2/input/input2
[    7.256130] input,hidraw0: USB HID v1.00 Device [C-Media Electronics Inc. USB PnP Audio Device] on usb-0000:00:12.0-2
[    7.256206] usbcore: registered new interface driver usbhid
[    7.256210] usbhid: v2.6:USB HID core driver
[    7.256575] scsi7 : SCSI emulation for USB Mass Storage devices
[    7.256734] usb-storage: device found at 2
[    7.256738] usb-storage: waiting for device to settle before scanning
[    7.256742] usbcore: registered new interface driver usb-storage
[    7.256746] USB Mass Storage support registered.
[    7.313000] PM: Starting manual resume from disk
[    7.313004] PM: Resume from partition 8:21
[    7.313006] PM: Checking hibernation image.
[    7.313184] PM: Resume from disk failed.
[    7.386837] kjournald starting.  Commit interval 5 seconds
[    7.386847] EXT3-fs: mounted filesystem with ordered data mode.
[    7.493522] usb 2-1: new low speed USB device using ohci_hcd and address 4
[    7.660706] usb 2-1: configuration #1 chosen from 1 choice
[    7.668849] input: PS/2+USB Mouse as /devices/pci0000:00/0000:00:12.1/usb2/2-1/2-1:1.0/input/input3
[    7.677586] input,hidraw1: USB HID v1.11 Mouse [PS/2+USB Mouse] on usb-0000:00:12.1-1
[   12.228241] usb-storage: device scan complete
[   12.228807] scsi 6:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
[   12.229292] scsi 6:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
[   12.229916] scsi 6:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ: 0 ANSI: 0
[   12.230414] scsi 6:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0
[   12.231360] sd 6:0:0:0: [sdc] Attached SCSI removable disk
[   12.231462] sd 6:0:0:0: Attached scsi generic sg3 type 0
[   12.232205] sd 6:0:0:1: [sdd] Attached SCSI removable disk
[   12.232248] sd 6:0:0:1: Attached scsi generic sg4 type 0
[   12.232953] sd 6:0:0:2: [sde] Attached SCSI removable disk
[   12.232996] sd 6:0:0:2: Attached scsi generic sg5 type 0
[   12.233703] sd 6:0:0:3: [sdf] Attached SCSI removable disk
[   12.233745] sd 6:0:0:3: Attached scsi generic sg6 type 0
[   12.256714] usb-storage: device scan complete
[   12.257052] scsi 7:0:0:0: Direct-Access     SanDisk  U3 Cruzer Micro  8.02 PQ: 0 ANSI: 0 CCS
[   12.257795] sd 7:0:0:0: [sdg] 3907583 512-byte hardware sectors (2001 MB)
[   12.258295] sd 7:0:0:0: [sdg] Write Protect is off
[   12.258297] sd 7:0:0:0: [sdg] Mode Sense: 45 00 00 08
[   12.258298] sd 7:0:0:0: [sdg] Assuming drive cache: write through
[   12.259419] sd 7:0:0:0: [sdg] 3907583 512-byte hardware sectors (2001 MB)
[   12.259919] sd 7:0:0:0: [sdg] Write Protect is off
[   12.259921] sd 7:0:0:0: [sdg] Mode Sense: 45 00 00 08
[   12.259922] sd 7:0:0:0: [sdg] Assuming drive cache: write through
[   12.259925]  sdg: sdg1
[   12.260832] sd 7:0:0:0: [sdg] Attached SCSI removable disk
[   12.260882] sd 7:0:0:0: Attached scsi generic sg7 type 0
[   12.618725] udevd version 124 started
[   12.902743] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   12.906080] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   12.918072] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input4
[   12.941070] ACPI: Power Button (FF) [PWRF]
[   12.941480] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input5
[   12.973041] ACPI: Power Button (CM) [PWRB]
[   12.973309] ACPI: WMI: Mapper loaded
[   13.038213] parport_pc 00:0a: reported by Plug and Play ACPI
[   13.038275] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   13.146823] usbcore: registered new interface driver usbserial
[   13.146889] usbserial: USB Serial support registered for generic
[   13.146937] usbcore: registered new interface driver usbserial_generic
[   13.146938] usbserial: USB Serial Driver core
[   13.200162] usbserial: USB Serial support registered for FTDI USB Serial Device
[   13.200258] ftdi_sio 1-3:1.0: FTDI USB Serial Device converter detected
[   13.201447] ftdi_sio: Detected FT232RL
[   13.201658] usb 1-3: FTDI USB Serial Device converter now attached to ttyUSB0
[   13.201679] usbcore: registered new interface driver ftdi_sio
[   13.201681] ftdi_sio: v1.4.3:USB FTDI Serial Converters Driver
[   13.261764] ACPI: I/O resource piix4_smbus [0xb00-0xb07] conflicts with ACPI region SOR1 [0xb00-0xb0f]
[   13.261768] ACPI: Device needs an ACPI driver
[   13.261777] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0xb00, revision 0
[   13.548990] input: PC Speaker as /devices/platform/pcspkr/input/input6
[   13.811512] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   13.835486] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[   13.966505] usbcore: registered new interface driver snd-usb-audio
[   14.605534] lp0: using parport0 (interrupt-driven).
[   14.684532] Compat-wireless backport release: compat-wireless-2010-08-23-11-g4207d04
[   14.684537] Backport based on linux-next.git next-20100827
[   14.865609] cfg80211: Calling CRDA to update world regulatory domain
[   14.953664] usbcore: registered new interface driver ath9k_hif_usb
[   15.132441] Adding 9936160k swap on /dev/sdb5.  Priority:-1 extents:1 across:9936160k
[   15.686315] EXT3 FS on sdb1, internal journal
[   16.700786] type=1505 audit(1286105615.285:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=5069
[   16.843225] type=1505 audit(1286105615.425:3): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=5074
[   16.843508] type=1505 audit(1286105615.425:4): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=5074
[   16.992086] ip_tables: (C) 2000-2006 Netfilter Core Team
[   17.831070] powernow-k8: Found 1 AMD Phenom(tm) 9600 Quad-Core Processor processors (4 cpu cores) (version 2.20.00)
[   17.831108] powernow-k8: ACPI Processor support is required for SMP systems but is absent. Please load the ACPI Processor module before starting this driver.
[   17.831147] powernow-k8: ACPI Processor support is required for SMP systems but is absent. Please load the ACPI Processor module before starting this driver.
[   17.831186] powernow-k8: ACPI Processor support is required for SMP systems but is absent. Please load the ACPI Processor module before starting this driver.
[   17.831217] powernow-k8: ACPI Processor support is required for SMP systems but is absent. Please load the ACPI Processor module before starting this driver.
[   18.573147] warning: `avahi-daemon' uses 32-bit capabilities (legacy support in use)
[   18.739462] ppdev: user-space parallel port driver
[   20.189714] Bluetooth: Core ver 2.13
[   20.190654] NET: Registered protocol family 31
[   20.190657] Bluetooth: HCI device and connection manager initialized
[   20.190662] Bluetooth: HCI socket layer initialized
[   20.208304] Bluetooth: L2CAP ver 2.11
[   20.208317] Bluetooth: L2CAP socket layer initialized
[   20.223748] Bluetooth: SCO (Voice Link) ver 0.6
[   20.223761] Bluetooth: SCO socket layer initialized
[   20.240702] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   20.240720] Bluetooth: BNEP filters: protocol multicast
[   20.281138] Bridge firewalling registered
[   20.282412] pan0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature.
[   20.330291] Bluetooth: RFCOMM socket layer initialized
[   20.331588] Bluetooth: RFCOMM TTY layer initialized
[   20.331593] Bluetooth: RFCOMM ver 1.10
[   24.458340] r8169: eth0: link down
[   25.993397] hda-intel: Invalid position buffer, using LPIB read method instead.
[  108.972483] type=1503 audit(1286105707.557:5): operation="inode_permission" requested_mask="r::" denied_mask="r::" fsuid=7 name="/proc/6626/net/" pid=6626 profile="/usr/sbin/cupsd"
[  109.051019] NET: Registered protocol family 10
[  109.052253] lo: Disabled Privacy Extensions
[  109.053345] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  109.054857] type=1503 audit(1286105707.637:6): operation="socket_create" family="ax25" sock_type="dgram" protocol=0 pid=6626 profile="/usr/sbin/cupsd"
[  109.054868] type=1503 audit(1286105707.637:7): operation="socket_create" family="netrom" sock_type="seqpacket" protocol=0 pid=6626 profile="/usr/sbin/cupsd"
[  109.054874] type=1503 audit(1286105707.637:8): operation="socket_create" family="rose" sock_type="dgram" protocol=0 pid=6626 profile="/usr/sbin/cupsd"
[  109.054878] type=1503 audit(1286105707.637:9): operation="socket_create" family="ipx" sock_type="dgram" protocol=0 pid=6626 profile="/usr/sbin/cupsd"
[  109.054882] type=1503 audit(1286105707.637:10): operation="socket_create" family="appletalk" sock_type="dgram" protocol=0 pid=6626 profile="/usr/sbin/cupsd"
[  109.054886] type=1503 audit(1286105707.637:11): operation="socket_create" family="econet" sock_type="dgram" protocol=0 pid=6626 profile="/usr/sbin/cupsd"
[  109.054891] type=1503 audit(1286105707.637:12): operation="socket_create" family="ash" sock_type="dgram" protocol=0 pid=6626 profile="/usr/sbin/cupsd"
[  109.054895] type=1503 audit(1286105707.637:13): operation="socket_create" family="x25" sock_type="seqpacket" protocol=0 pid=6626 profile="/usr/sbin/cupsd"
[  109.054978] type=1503 audit(1286105707.637:14): operation="inode_permission" requested_mask="::r" denied_mask="::r" fsuid=7 name="/proc/6626/net/dev" pid=6626 profile="/usr/sbin/cupsd"
[  110.204250] ppdev0: registered pardevice
[  110.252065] ppdev0: unregistered pardevice
[  110.876380] ppdev0: registered pardevice
[  110.924308] ppdev0: unregistered pardevice
[  110.949933] ppdev0: registered pardevice
[  110.996381] ppdev0: unregistered pardevice
[ 2385.684481] usb 6-4: USB disconnect, address 2
[ 2385.719364] scsi 7:0:0:0: rejecting I/O to dead device
[ 7575.900059] usb 6-4: new high speed USB device using ehci_hcd and address 3
[ 7576.033826] usb 6-4: configuration #1 chosen from 1 choice
[ 7576.034892] scsi8 : SCSI emulation for USB Mass Storage devices
[ 7576.035913] usb-storage: device found at 3
[ 7576.035919] usb-storage: waiting for device to settle before scanning
[ 7581.032264] usb-storage: device scan complete
[ 7581.032959] scsi 8:0:0:0: Direct-Access     SanDisk  U3 Cruzer Micro  8.02 PQ: 0 ANSI: 0 CCS
[ 7581.036084] sd 8:0:0:0: [sdg] 3907583 512-byte hardware sectors (2001 MB)
[ 7581.036582] sd 8:0:0:0: [sdg] Write Protect is off
[ 7581.036585] sd 8:0:0:0: [sdg] Mode Sense: 45 00 00 08
[ 7581.036587] sd 8:0:0:0: [sdg] Assuming drive cache: write through
[ 7581.038831] sd 8:0:0:0: [sdg] 3907583 512-byte hardware sectors (2001 MB)
[ 7581.039329] sd 8:0:0:0: [sdg] Write Protect is off
[ 7581.039331] sd 8:0:0:0: [sdg] Mode Sense: 45 00 00 08
[ 7581.039333] sd 8:0:0:0: [sdg] Assuming drive cache: write through
[ 7581.039336]  sdg: sdg1
[ 7581.041648] sd 8:0:0:0: [sdg] Attached SCSI removable disk
[ 7581.043645] sd 8:0:0:0: Attached scsi generic sg7 type 0
[ 7720.502720] usb 6-4: USB disconnect, address 3
[ 7720.506774] Buffer I/O error on device sdg1, logical block 480
[ 7720.506784] lost page write due to I/O error on sdg1
[ 7720.518859] scsi 8:0:0:0: rejecting I/O to dead device
[ 7818.852060] usb 6-4: new high speed USB device using ehci_hcd and address 4
[ 7818.985799] usb 6-4: configuration #1 chosen from 1 choice
[ 7818.987119] scsi9 : SCSI emulation for USB Mass Storage devices
[ 7818.989468] usb-storage: device found at 4
[ 7818.989477] usb-storage: waiting for device to settle before scanning
[ 7823.988225] usb-storage: device scan complete
[ 7823.988689] scsi 9:0:0:0: Direct-Access     SanDisk  U3 Cruzer Micro  8.02 PQ: 0 ANSI: 0 CCS
[ 7823.991934] sd 9:0:0:0: [sdg] 3907583 512-byte hardware sectors (2001 MB)
[ 7823.992430] sd 9:0:0:0: [sdg] Write Protect is off
[ 7823.992432] sd 9:0:0:0: [sdg] Mode Sense: 45 00 00 08
[ 7823.992434] sd 9:0:0:0: [sdg] Assuming drive cache: write through
[ 7823.994677] sd 9:0:0:0: [sdg] 3907583 512-byte hardware sectors (2001 MB)
[ 7823.995176] sd 9:0:0:0: [sdg] Write Protect is off
[ 7823.995178] sd 9:0:0:0: [sdg] Mode Sense: 45 00 00 08
[ 7823.995180] sd 9:0:0:0: [sdg] Assuming drive cache: write through
[ 7823.995183]  sdg: sdg1
[ 7823.996122] sd 9:0:0:0: [sdg] Attached SCSI removable disk
[ 7823.996250] sd 9:0:0:0: Attached scsi generic sg7 type 0






eviscerate@evi-main:~$ cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
rtc
ath9k_htc




eviscerate@evi-main:~$ ls -l /lib/firmware/ar*
-rw-r--r-- 1 root root 70608 2010-08-29 20:12 /lib/firmware/ar7010.fw
-rw-r--r-- 1 root root 51280 2010-07-11 10:16 /lib/firmware/ar9271.fw




```

---

### Post by Corey4666 on 2010-10-03
UPDATE:

Well, when I booted down the ubuntu system it said something about Ath9k firmware failed.

---

### Post by vagrale13 on 2010-10-04
With the messages shows that the driver installed fine and must be works!:?

I think better solution is with some way install *Lucid 10.04 LTS* and try again with *ath9k_htc-installer* or to install *Maverick* *10.10* and logical will work out of the box or to install newer kernel and try again!
Post the output of
```
iwconfig
sudo iwlist scan
```

---

### Post by walt.smith1960 on 2010-10-14
Kudos to vagrale13! His .deb package installed and the lovely blue light came on!! :D I've been fighting with an RT3572 based N adapter (Engenius EUB9801) off and on for months. I bought this Netgear WNA1100 an hour ago.  My OS is a somewhat abused Lucid 32 bit desktop install.  Well built .deb packages are truly a blessing for the less knowledgeable among us. Thank You again.

---

### Post by aniruddha on 2010-10-17
Hey, vagrale13, when you say that ubuntu 10.10 should support this out of the box what do you mean? I am trying to get a NETGEAR N 150 USB wireless wna1100 to run on my recently installed 10.10 system (64 bit). I used the gui program to get it to run fine in 10.04 (many thanks for that). But, the same program does not run in 10.10 (it says that there is a programming error in aptdaemon) and the blue light does not turn on in my adapter. Any help?

---

### Post by vagrale13 on 2010-10-18
> **aniruddha said:**
> Hey, vagrale13, when you say that ubuntu 10.10 should support this out of the box what do you mean? I am trying to get a NETGEAR N 150 USB wireless wna1100 to run on my recently installed 10.10 system (64 bit). I used the gui program to get it to run fine in 10.04 (many thanks for that). But, the same program does not run in 10.10 (it says that there is a programming error in aptdaemon) and the blue light does not turn on in my adapter. Any help?
I think must be works out of the box in maverick your usb wireless! :confused:
Try with the *.deb* for **Ubuntu Maverick 10.10**
read the first post [http://ubuntuforums.org/showthread.php?t=1564278 ]("http://ubuntuforums.org/showthread.php?t=1564278")
and see if it works for you! :KS

---

### Post by aniruddha on 2010-10-27
Awesome. The new .deb fixed the issue completely. Many thanks for all the help! This truly is a life saver.

---

### Post by ilovemoon86 on 2010-11-06
Hi vagrale13, :)
unfortunately your package doesn't work with my NETGEAR N150 WNA1100... :confused:

Now my connection works thanks to my brother's RT2501USB Wireless Adapter :S

OUTPUT OF SOME COMMANDS

> #lsusb
...
Bus 002 Device 002: ID 148f:2573 Ralink Technology, Corp. RT2501USB Wireless Adapter
Bus 001 Device 003: ID 0846:9030 NetGear, Inc.
...

#uname -rm
2.6.32-26-generic x86_64

#lsmod | grep ath9k
(nothing!!!)

#dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.32-26-generic (buildd@crested) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #46-Ubuntu SMP Tue Oct 26 16:47:18 UTC 2010 (Ubuntu 2.6.32-26.46-generic 2.6.32.24+drm33.11)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-26-generic root=UUID=153ef51e-5bb5-4326-9d6d-752eda07ad37 ro quiet splash
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009b000 (usable)
[    0.000000]  BIOS-e820: 000000000009b000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000bffa0000 (usable)
[    0.000000]  BIOS-e820: 00000000bffa0000 - 00000000bffae000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000bffae000 - 00000000bffe0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000bffe0000 - 00000000c0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] DMI present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0xbffa0 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-DFFFF write-protect
[    0.000000]   E0000-EFFFF write-through
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 080000000 mask FC0000000 write-back
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
[    0.000000]  modified: 0000000000010000 - 000000000009b000 (usable)
[    0.000000]  modified: 000000000009b000 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 00000000bffa0000 (usable)
[    0.000000]  modified: 00000000bffa0000 - 00000000bffae000 (ACPI data)
[    0.000000]  modified: 00000000bffae000 - 00000000bffe0000 (ACPI NVS)
[    0.000000]  modified: 00000000bffe0000 - 00000000c0000000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] init_memory_mapping: 0000000000000000-00000000bffa0000
[    0.000000] NX (Execute Disable) protection: active
[    0.000000]  0000000000 - 00bfe00000 page 2M
[    0.000000]  00bfe00000 - 00bffa0000 page 4k
[    0.000000] kernel direct mapping tables up to bffa0000 @ 10000-15000
[    0.000000] RAMDISK: 377fb000 - 37fef535
[    0.000000] ACPI: RSDP 00000000000fc440 00014 (v00 HPQOEM)
[    0.000000] ACPI: RSDT 00000000bffa0000 00044 (v01 HPQOEM SLIC-CPC 20080905 MSFT 00000097)
[    0.000000] ACPI: FACP 00000000bffa0200 00084 (v02 HPQOEM SLIC-CPC 20080905 MSFT 00000097)
[    0.000000] ACPI: DSDT 00000000bffa0440 04E91 (v01 HPQOEM SLIC-CPC 00000000 INTL 20051117)
[    0.000000] ACPI: FACS 00000000bffae000 00040
[    0.000000] ACPI: APIC 00000000bffa0390 0006C (v01 HPQOEM SLIC-CPC 20080905 MSFT 00000097)
[    0.000000] ACPI: MCFG 00000000bffa0400 0003C (v01 HPQOEM SLIC-CPC 20080905 MSFT 00000097)
[    0.000000] ACPI: OEMB 00000000bffae040 00072 (v01 HPQOEM SLIC-CPC 20080905 MSFT 00000097)
[    0.000000] ACPI: HPET 00000000bffa52e0 00038 (v01 HPQOEM SLIC-CPC 20080905 MSFT 00000097)
[    0.000000] ACPI: GSCI 00000000bffae0c0 02024 (v01 HPQOEM SLIC-CPC 20080905 MSFT 00000097)
[    0.000000] ACPI: SLIC 00000000bffb00f0 00176 (v01 HPQOEM SLIC-CPC 00000001 MSFT 00000001)
[    0.000000] ACPI: SSDT 00000000bffb14b0 0082F (v01 HPQOEM SLIC-CPC 00000012 INTL 20051117)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-00000000bffa0000
[    0.000000] Bootmem setup node 0 0000000000000000-00000000bffa0000
[    0.000000]   NODE_DATA [0000000000013000 - 0000000000017fff]
[    0.000000]   bootmap [0000000000018000 -  000000000002fff7] pages 18
[    0.000000] (7 early reservations) ==> bootmem [0000000000 - 00bffa0000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
[    0.000000]   #2 [0001000000 - 0001a2fa64]    TEXT DATA BSS ==> [0001000000 - 0001a2fa64]
[    0.000000]   #3 [00377fb000 - 0037fef535]          RAMDISK ==> [00377fb000 - 0037fef535]
[    0.000000]   #4 [000009b000 - 0000100000]    BIOS reserved ==> [000009b000 - 0000100000]
[    0.000000]   #5 [0001a30000 - 0001a307cc]              BRK ==> [0001a30000 - 0001a307cc]
[    0.000000]   #6 [0000010000 - 0000013000]          PGTABLE ==> [0000010000 - 0000013000]
[    0.000000] found SMP MP-table at [ffff8800000ff780] ff780
[    0.000000]  [ffffea0000000000-ffffea00029fffff] PMD -> [ffff880002000000-ffff8800049fffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00100000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009b
[    0.000000]     0: 0x00000100 -> 0x000bffa0
[    0.000000] On node 0 totalpages: 786219
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 107 pages reserved
[    0.000000]   DMA zone: 3816 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 10695 pages used for memmap
[    0.000000]   DMA32 zone: 771545 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a301 base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 000000000009b000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e4000
[    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at c0000000 (gap: c0000000:3ee00000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880001c00000 s91544 r8192 d23144 u524288
[    0.000000] pcpu-alloc: s91544 r8192 d23144 u524288 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 775361
[    0.000000] Policy zone: DMA32
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-26-generic root=UUID=153ef51e-5bb5-4326-9d6d-752eda07ad37 ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 3082588k/3145344k available (5421k kernel code, 468k absent, 62288k reserved, 2980k data, 876k init)
[    0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] NR_IRQS:4352 nr_irqs:440
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 31457280 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2400.085 MHz processor.
[    0.010006] Calibrating delay loop (skipped), value calculated using timer frequency.. 4800.17 BogoMIPS (lpj=24000850)
[    0.010033] Security Framework initialized
[    0.010051] AppArmor: AppArmor initialized
[    0.010408] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.013842] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.015523] Mount-cache hash table entries: 256
[    0.015689] Initializing cgroup subsys ns
[    0.015694] Initializing cgroup subsys cpuacct
[    0.015697] Initializing cgroup subsys memory
[    0.015706] Initializing cgroup subsys devices
[    0.015708] Initializing cgroup subsys freezer
[    0.015710] Initializing cgroup subsys net_cls
[    0.015732] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.015734] CPU: L2 cache: 4096K
[    0.015737] CPU 0/0x0 -> Node 0
[    0.015739] CPU: Physical Processor ID: 0
[    0.015740] CPU: Processor Core ID: 0
[    0.015743] mce: CPU supports 6 MCE banks
[    0.015751] CPU0: Thermal monitoring enabled (TM2)
[    0.015755] using mwait in idle threads.
[    0.015756] Performance Events: Core2 events, Intel PMU driver.
[    0.015762] ... version:                2
[    0.015764] ... bit width:              40
[    0.015765] ... generic registers:      2
[    0.015766] ... value mask:             000000ffffffffff
[    0.015768] ... max period:             000000007fffffff
[    0.015770] ... fixed-purpose events:   3
[    0.015771] ... event mask:             0000000700000003
[    0.021178] ACPI: Core revision 20090903
[    0.030007] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.030012] ftrace: allocating 22543 entries in 89 pages
[    0.038576] Setting APIC routing to flat
[    0.038933] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.139351] CPU0: Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz stepping 0b
[    0.140000] APIC calibration not consistent with PM-Timer: 149ms instead of 100ms
[    0.140000] APIC delta adjusted to PM-Timer: 1666629 (2499931)
[    0.140000] Booting processor 1 APIC 0x1 ip 0x6000
[    0.020000] Initializing CPU#1
[    0.020000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.020000] CPU: L2 cache: 4096K
[    0.020000] CPU 1/0x1 -> Node 0
[    0.020000] CPU: Physical Processor ID: 0
[    0.020000] CPU: Processor Core ID: 1
[    0.020000] CPU1: Thermal monitoring enabled (TM2)
[    0.290093] CPU1: Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz stepping 0b
[    0.290100] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.300111] Booting processor 2 APIC 0x2 ip 0x6000
[    0.020000] Initializing CPU#2
[    0.020000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.020000] CPU: L2 cache: 4096K
[    0.020000] CPU 2/0x2 -> Node 0
[    0.020000] CPU: Physical Processor ID: 0
[    0.020000] CPU: Processor Core ID: 2
[    0.020000] CPU2: Thermal monitoring enabled (TM2)
[    0.460073] CPU2: Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz stepping 0b
[    0.460080] checking TSC synchronization [CPU#0 -> CPU#2]: passed.
[    0.470075] Booting processor 3 APIC 0x3 ip 0x6000
[    0.020000] Initializing CPU#3
[    0.020000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.020000] CPU: L2 cache: 4096K
[    0.020000] CPU 3/0x3 -> Node 0
[    0.020000] CPU: Physical Processor ID: 0
[    0.020000] CPU: Processor Core ID: 3
[    0.020000] CPU3: Thermal monitoring enabled (TM2)
[    0.630115] CPU3: Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz stepping 0b
[    0.630121] checking TSC synchronization [CPU#0 -> CPU#3]: passed.
[    0.640011] Brought up 4 CPUs
[    0.640014] Total of 4 processors activated (19199.96 BogoMIPS).
[    0.641590] CPU0 attaching sched-domain:
[    0.641593]  domain 0: span 0-1 level MC
[    0.641596]   groups: 0 1
[    0.641599]   domain 1: span 0-3 level CPU
[    0.641601]    groups: 0-1 (cpu_power = 2048) 2-3 (cpu_power = 2048)
[    0.641608] CPU1 attaching sched-domain:
[    0.641610]  domain 0: span 0-1 level MC
[    0.641612]   groups: 1 0
[    0.641615]   domain 1: span 0-3 level CPU
[    0.641617]    groups: 0-1 (cpu_power = 2048) 2-3 (cpu_power = 2048)
[    0.641622] CPU2 attaching sched-domain:
[    0.641624]  domain 0: span 2-3 level MC
[    0.641626]   groups: 2 3
[    0.641629]   domain 1: span 0-3 level CPU
[    0.641631]    groups: 2-3 (cpu_power = 2048) 0-1 (cpu_power = 2048)
[    0.641636] CPU3 attaching sched-domain:
[    0.641638]  domain 0: span 2-3 level MC
[    0.641640]   groups: 3 2
[    0.641643]   domain 1: span 0-3 level CPU
[    0.641644]    groups: 2-3 (cpu_power = 2048) 0-1 (cpu_power = 2048)
[    0.641761] devtmpfs: initialized
[    0.641761] regulator: core version 0.5
[    0.641761] Time: 17:14:56  Date: 11/06/10
[    0.641761] NET: Registered protocol family 16
[    0.641761] ACPI: bus type pci registered
[    0.641761] Trying to unpack rootfs image as initramfs...
[    0.641761] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.641761] PCI: Not using MMCONFIG.
[    0.641761] PCI: Using configuration type 1 for base access
[    0.641761] bio: create slab <bio-0> at 0
[    0.641761] ACPI: EC: Look up EC in DSDT
[    0.642526] ACPI: Executed 1 blocks of module-level executable AML code
[    0.650292] ACPI: Interpreter enabled
[    0.650295] ACPI: (supports S0 S1 S3 S4 S5)
[    0.650315] ACPI: Using IOAPIC for interrupt routing
[    0.650360] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.652189] PCI: MCFG area at e0000000 reserved in ACPI motherboard resources
[    0.655728] PCI: Using MMCONFIG at e0000000 - efffffff
[    0.662869] ACPI: No dock devices found.
[    0.663001] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.663098] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.663101] pci 0000:00:01.0: PME# disabled
[    0.663183] pci 0000:00:1a.0: reg 20 io port: [0xb400-0xb41f]
[    0.663261] pci 0000:00:1a.1: reg 20 io port: [0xb480-0xb49f]
[    0.663341] pci 0000:00:1a.7: reg 10 32bit mmio: [0xfe8fec00-0xfe8fefff]
[    0.663396] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.663400] pci 0000:00:1a.7: PME# disabled
[    0.663446] pci 0000:00:1b.0: reg 10 64bit mmio: [0xfe8f4000-0xfe8f7fff]
[    0.663495] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.663499] pci 0000:00:1b.0: PME# disabled
[    0.663576] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.663580] pci 0000:00:1c.0: PME# disabled
[    0.663658] pci 0000:00:1c.2: PME# supported from D0 D3hot D3cold
[    0.663662] pci 0000:00:1c.2: PME# disabled
[    0.663731] pci 0000:00:1d.0: reg 20 io port: [0xb800-0xb81f]
[    0.663810] pci 0000:00:1d.1: reg 20 io port: [0xb880-0xb89f]
[    0.663886] pci 0000:00:1d.2: reg 20 io port: [0xbc00-0xbc1f]
[    0.663962] pci 0000:00:1d.3: reg 20 io port: [0xc000-0xc01f]
[    0.664039] pci 0000:00:1d.7: reg 10 32bit mmio: [0xfe8ff800-0xfe8ffbff]
[    0.664094] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.664098] pci 0000:00:1d.7: PME# disabled
[    0.664232] pci 0000:00:1f.0: quirk: region 0800-087f claimed by ICH6 ACPI/GPIO/TCO
[    0.664236] pci 0000:00:1f.0: quirk: region 0480-04bf claimed by ICH6 GPIO
[    0.664239] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0a00 (mask 00ff)
[    0.664316] pci 0000:00:1f.2: reg 10 io port: [0xc880-0xc887]
[    0.664323] pci 0000:00:1f.2: reg 14 io port: [0xc800-0xc803]
[    0.664329] pci 0000:00:1f.2: reg 18 io port: [0xc480-0xc487]
[    0.664335] pci 0000:00:1f.2: reg 1c io port: [0xc400-0xc403]
[    0.664342] pci 0000:00:1f.2: reg 20 io port: [0xc080-0xc09f]
[    0.664348] pci 0000:00:1f.2: reg 24 32bit mmio: [0xfe8ff000-0xfe8ff7ff]
[    0.664389] pci 0000:00:1f.2: PME# supported from D3hot
[    0.664393] pci 0000:00:1f.2: PME# disabled
[    0.664429] pci 0000:00:1f.3: reg 10 64bit mmio: [0xfe8ffc00-0xfe8ffcff]
[    0.664445] pci 0000:00:1f.3: reg 20 io port: [0x400-0x41f]
[    0.664496] pci 0000:04:00.0: reg 10 64bit mmio pref: [0xd0000000-0xdfffffff]
[    0.664504] pci 0000:04:00.0: reg 18 64bit mmio: [0xfeaf0000-0xfeafffff]
[    0.664509] pci 0000:04:00.0: reg 20 io port: [0xd000-0xd0ff]
[    0.664517] pci 0000:04:00.0: reg 30 32bit mmio pref: [0xfeac0000-0xfeadffff]
[    0.664534] pci 0000:04:00.0: supports D1 D2
[    0.664581] pci 0000:00:01.0: bridge io port: [0xd000-0xdfff]
[    0.664584] pci 0000:00:01.0: bridge 32bit mmio: [0xfea00000-0xfeafffff]
[    0.664588] pci 0000:00:01.0: bridge 64bit mmio pref: [0xd0000000-0xdfffffff]
[    0.664793] pci 0000:02:00.0: reg 10 io port: [0xe800-0xe8ff]
[    0.664867] pci 0000:02:00.0: reg 18 64bit mmio: [0xfebff000-0xfebfffff]
[    0.664917] pci 0000:02:00.0: reg 20 64bit mmio pref: [0xfdff0000-0xfdffffff]
[    0.664943] pci 0000:02:00.0: reg 30 32bit mmio pref: [0xfebc0000-0xfebdffff]
[    0.665095] pci 0000:02:00.0: supports D1 D2
[    0.665096] pci 0000:02:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.665110] pci 0000:02:00.0: PME# disabled
[    0.665234] pci 0000:00:1c.2: bridge io port: [0xe000-0xefff]
[    0.665238] pci 0000:00:1c.2: bridge 32bit mmio: [0xfeb00000-0xfebfffff]
[    0.665244] pci 0000:00:1c.2: bridge 64bit mmio pref: [0xfdf00000-0xfdffffff]
[    0.665284] pci 0000:01:05.0: reg 10 32bit mmio: [0xfe9ff000-0xfe9fffff]
[    0.665331] pci 0000:01:05.0: supports D1 D2
[    0.665333] pci 0000:01:05.0: PME# supported from D0 D1 D2 D3hot
[    0.665337] pci 0000:01:05.0: PME# disabled
[    0.665374] pci 0000:00:1e.0: transparent bridge
[    0.665381] pci 0000:00:1e.0: bridge 32bit mmio: [0xfe900000-0xfe9fffff]
[    0.665407] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.665515] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.665602] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[    0.665654] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P6._PRT]
[    0.677399] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[    0.677495] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[    0.677589] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[    0.677683] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11 12 14 *15)
[    0.677776] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 *4 5 6 7 10 11 12 14 15)
[    0.677871] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 *7 10 11 12 14 15)
[    0.677965] ACPI: PCI Interrupt Link [LNKG] (IRQs *3 4 5 6 7 10 11 12 14 15)
[    0.678058] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 11 12 *14 15)
[    0.678162] vgaarb: device added: PCI:0000:04:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.678166] vgaarb: loaded
[    0.678262] SCSI subsystem initialized
[    0.678271] libata version 3.00 loaded.
[    0.678271] usbcore: registered new interface driver usbfs
[    0.678271] usbcore: registered new interface driver hub
[    0.678271] usbcore: registered new device driver usb
[    0.678271] ACPI: WMI: Mapper loaded
[    0.678271] PCI: Using ACPI for IRQ routing
[    0.678271] NetLabel: Initializing
[    0.678271] NetLabel:  domain hash size = 128
[    0.678271] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.678271] NetLabel:  unlabeled traffic allowed by default
[    0.678271] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.678271] hpet0: 4 comparators, 64-bit 14.318180 MHz counter
[    0.700065] Switching to clocksource tsc
[    0.702010] AppArmor: AppArmor Filesystem Enabled
[    0.702028] pnp: PnP ACPI init
[    0.702048] ACPI: bus type pnp registered
[    0.704277] pnp: PnP ACPI: found 16 devices
[    0.704279] ACPI: ACPI bus type pnp unregistered
[    0.704291] system 00:01: iomem range 0xfed14000-0xfed19fff has been reserved
[    0.704298] system 00:06: ioport range 0x4d0-0x4d1 has been reserved
[    0.704300] system 00:06: ioport range 0x800-0x87f has been reserved
[    0.704303] system 00:06: ioport range 0x480-0x4bf has been reserved
[    0.704305] system 00:06: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    0.704308] system 00:06: iomem range 0xfed20000-0xfed8ffff has been reserved
[    0.704313] system 00:08: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.704315] system 00:08: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.704320] system 00:0b: ioport range 0xa00-0xadf has been reserved
[    0.704325] system 00:0d: iomem range 0xffc00000-0xffefffff has been reserved
[    0.704330] system 00:0e: iomem range 0xe0000000-0xefffffff has been reserved
[    0.704335] system 00:0f: iomem range 0x0-0x9ffff could not be reserved
[    0.704337] system 00:0f: iomem range 0xc0000-0xcffff has been reserved
[    0.704339] system 00:0f: iomem range 0xe0000-0xfffff could not be reserved
[    0.704342] system 00:0f: iomem range 0x100000-0xbfffffff could not be reserved
[    0.709078] pci 0000:00:01.0: PCI bridge, secondary bus 0000:04
[    0.709081] pci 0000:00:01.0:   IO window: 0xd000-0xdfff
[    0.709084] pci 0000:00:01.0:   MEM window: 0xfea00000-0xfeafffff
[    0.709087] pci 0000:00:01.0:   PREFETCH window: 0x000000d0000000-0x000000dfffffff
[    0.709091] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:03
[    0.709094] pci 0000:00:1c.0:   IO window: 0x1000-0x1fff
[    0.709100] pci 0000:00:1c.0:   MEM window: 0xc0000000-0xc01fffff
[    0.709104] pci 0000:00:1c.0:   PREFETCH window: 0x000000c0200000-0x000000c03fffff
[    0.709111] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:02
[    0.709114] pci 0000:00:1c.2:   IO window: 0xe000-0xefff
[    0.709119] pci 0000:00:1c.2:   MEM window: 0xfeb00000-0xfebfffff
[    0.709124] pci 0000:00:1c.2:   PREFETCH window: 0x000000fdf00000-0x000000fdffffff
[    0.709131] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:01
[    0.709132] pci 0000:00:1e.0:   IO window: disabled
[    0.709137] pci 0000:00:1e.0:   MEM window: 0xfe900000-0xfe9fffff
[    0.709141] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.709157]   alloc irq_desc for 16 on node -1
[    0.709159]   alloc kstat_irqs on node -1
[    0.709165] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.709169] pci 0000:00:01.0: setting latency timer to 64
[    0.709177] pci 0000:00:1c.0: enabling device (0104 -> 0107)
[    0.709180]   alloc irq_desc for 17 on node -1
[    0.709181]   alloc kstat_irqs on node -1
[    0.709184] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.709189] pci 0000:00:1c.0: setting latency timer to 64
[    0.709197]   alloc irq_desc for 18 on node -1
[    0.709199]   alloc kstat_irqs on node -1
[    0.709201] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.709206] pci 0000:00:1c.2: setting latency timer to 64
[    0.709213] pci 0000:00:1e.0: setting latency timer to 64
[    0.709217] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.709219] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]
[    0.709221] pci_bus 0000:04: resource 0 io:  [0xd000-0xdfff]
[    0.709223] pci_bus 0000:04: resource 1 mem: [0xfea00000-0xfeafffff]
[    0.709225] pci_bus 0000:04: resource 2 pref mem [0xd0000000-0xdfffffff]
[    0.709228] pci_bus 0000:03: resource 0 io:  [0x1000-0x1fff]
[    0.709230] pci_bus 0000:03: resource 1 mem: [0xc0000000-0xc01fffff]
[    0.709232] pci_bus 0000:03: resource 2 pref mem [0xc0200000-0xc03fffff]
[    0.709234] pci_bus 0000:02: resource 0 io:  [0xe000-0xefff]
[    0.709236] pci_bus 0000:02: resource 1 mem: [0xfeb00000-0xfebfffff]
[    0.709238] pci_bus 0000:02: resource 2 pref mem [0xfdf00000-0xfdffffff]
[    0.709240] pci_bus 0000:01: resource 1 mem: [0xfe900000-0xfe9fffff]
[    0.709242] pci_bus 0000:01: resource 3 io:  [0x00-0xffff]
[    0.709244] pci_bus 0000:01: resource 4 mem: [0x000000-0xffffffffffffffff]
[    0.709278] NET: Registered protocol family 2
[    0.709436] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.710799] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.718263] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.719261] TCP: Hash tables configured (established 524288 bind 65536)
[    0.719264] TCP reno registered
[    0.719410] NET: Registered protocol family 1
[    0.719554] pci 0000:04:00.0: Boot video device
[    0.719907] Scanning for low memory corruption every 60 seconds
[    0.720028] audit: initializing netlink socket (disabled)
[    0.720039] type=2000 audit(1289063695.719:1): initialized
[    0.728340] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.729634] VFS: Disk quotas dquot_6.5.2
[    0.729701] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.730248] fuse init (API version 7.13)
[    0.730328] msgmni has been set to 6020
[    0.730613] alg: No test for stdrng (krng)
[    0.730661] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.730664] io scheduler noop registered
[    0.730665] io scheduler anticipatory registered
[    0.730667] io scheduler deadline registered
[    0.730698] io scheduler cfq registered (default)
[    0.730830]   alloc irq_desc for 24 on node -1
[    0.730832]   alloc kstat_irqs on node -1
[    0.730840] pcieport 0000:00:01.0: irq 24 for MSI/MSI-X
[    0.730845] pcieport 0000:00:01.0: setting latency timer to 64
[    0.730943]   alloc irq_desc for 25 on node -1
[    0.730945]   alloc kstat_irqs on node -1
[    0.730952] pcieport 0000:00:1c.0: irq 25 for MSI/MSI-X
[    0.730961] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.731090]   alloc irq_desc for 26 on node -1
[    0.731091]   alloc kstat_irqs on node -1
[    0.731098] pcieport 0000:00:1c.2: irq 26 for MSI/MSI-X
[    0.731107] pcieport 0000:00:1c.2: setting latency timer to 64
[    0.731187] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.731259] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.731357] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.731360] ACPI: Power Button [PWRB]
[    0.731398] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.731400] ACPI: Power Button [PWRF]
[    0.732018] ACPI: SSDT 00000000bffb0270 00277 (v01 HPQOEM SLIC-CPC 00000011 INTL 20051117)
[    0.732237] processor LNXCPU:00: registered as cooling_device0
[    0.732595] ACPI: SSDT 00000000bffb0700 00277 (v01 HPQOEM SLIC-CPC 00000012 INTL 20051117)
[    0.732786] processor LNXCPU:01: registered as cooling_device1
[    0.733133] ACPI: SSDT 00000000bffb0b90 00277 (v01 HPQOEM SLIC-CPC 00000012 INTL 20051117)
[    0.733329] processor LNXCPU:02: registered as cooling_device2
[    0.733695] ACPI: SSDT 00000000bffb1020 00277 (v01 HPQOEM SLIC-CPC 00000012 INTL 20051117)
[    0.733888] processor LNXCPU:03: registered as cooling_device3
[    0.736946] Linux agpgart interface v0.103
[    0.736974] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.738130] brd: module loaded
[    0.738545] loop: module loaded
[    0.738617] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    0.738968] Fixed MDIO Bus: probed
[    0.738997] PPP generic driver version 2.4.2
[    0.739022] tun: Universal TUN/TAP device driver, 1.6
[    0.739024] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.739088] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.739109] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.739120] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    0.739123] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    0.739152] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    0.739180] ehci_hcd 0000:00:1a.7: debug port 1
[    0.743062] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    0.743080] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xfe8fec00
[    0.769677] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    0.769826] usb usb1: configuration #1 chosen from 1 choice
[    0.769860] hub 1-0:1.0: USB hub found
[    0.769868] hub 1-0:1.0: 4 ports detected
[    0.769930]   alloc irq_desc for 23 on node -1
[    0.769932]   alloc kstat_irqs on node -1
[    0.769938] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.769966] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.769969] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.770006] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    0.770033] ehci_hcd 0000:00:1d.7: debug port 1
[    0.773913] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.773935] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xfe8ff800
[    0.799674] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.799792] usb usb2: configuration #1 chosen from 1 choice
[    0.799821] hub 2-0:1.0: USB hub found
[    0.799830] hub 2-0:1.0: 8 ports detected
[    0.799900] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.799922] uhci_hcd: USB Universal Host Controller Interface driver
[    0.799966] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.799973] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    0.799982] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    0.800016] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    0.800055] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000b400
[    0.800134] usb usb3: configuration #1 chosen from 1 choice
[    0.800158] hub 3-0:1.0: USB hub found
[    0.800163] hub 3-0:1.0: 2 ports detected
[    0.800200]   alloc irq_desc for 21 on node -1
[    0.800202]   alloc kstat_irqs on node -1
[    0.800207] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.800212] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    0.800215] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    0.800240] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    0.800269] uhci_hcd 0000:00:1a.1: irq 21, io base 0x0000b480
[    0.800348] usb usb4: configuration #1 chosen from 1 choice
[    0.800368] hub 4-0:1.0: USB hub found
[    0.800373] hub 4-0:1.0: 2 ports detected
[    0.800418] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.800423] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.800426] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.800451] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    0.800473] uhci_hcd 0000:00:1d.0: irq 23, io base 0x0000b800
[    0.800552] usb usb5: configuration #1 chosen from 1 choice
[    0.800572] hub 5-0:1.0: USB hub found
[    0.800577] hub 5-0:1.0: 2 ports detected
[    0.800614]   alloc irq_desc for 19 on node -1
[    0.800616]   alloc kstat_irqs on node -1
[    0.800619] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.800624] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.800627] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.800653] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    0.800682] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000b880
[    0.800762] usb usb6: configuration #1 chosen from 1 choice
[    0.800782] hub 6-0:1.0: USB hub found
[    0.800787] hub 6-0:1.0: 2 ports detected
[    0.800826] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.800831] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.800834] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.800859] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    0.800884] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000bc00
[    0.800971] usb usb7: configuration #1 chosen from 1 choice
[    0.800996] hub 7-0:1.0: USB hub found
[    0.801001] hub 7-0:1.0: 2 ports detected
[    0.801037] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 16 (level, low) -> IRQ 16
[    0.801042] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    0.801045] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    0.801082] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 8
[    0.801106] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000c000
[    0.801183] usb usb8: configuration #1 chosen from 1 choice
[    0.801207] hub 8-0:1.0: USB hub found
[    0.801213] hub 8-0:1.0: 2 ports detected
[    0.801300] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    0.803402] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.803407] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.803508] mice: PS/2 mouse device common for all mice
[    0.803598] rtc_cmos 00:03: RTC can wake from S4
[    0.803629] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    0.803656] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    0.803773] device-mapper: uevent: version 1.0.3
[    0.803856] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
[    0.803943] device-mapper: multipath: version 1.1.0 loaded
[    0.803945] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.804140] cpuidle: using governor ladder
[    0.804142] cpuidle: using governor menu
[    0.804421] TCP cubic registered
[    0.804540] NET: Registered protocol family 10
[    0.804910] lo: Disabled Privacy Extensions
[    0.805138] NET: Registered protocol family 17
[    0.806206] PM: Resume from disk failed.
[    0.806218] registered taskstats version 1
[    0.806674]   Magic number: 2:452:238
[    0.806749] rtc_cmos 00:03: setting system clock to 2010-11-06 17:14:56 UTC (1289063696)
[    0.806752] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.806753] EDD information not available.
[    0.807983] Freeing initrd memory: 8145k freed
[    0.811139] Freeing unused kernel memory: 876k freed
[    0.811337] Write protecting the kernel read-only data: 7696k
[    0.825290] udev: starting version 151
[    0.831317] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    0.846391] ahci 0000:00:1f.2: version 3.0
[    0.846411] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.846456]   alloc irq_desc for 27 on node -1
[    0.846458]   alloc kstat_irqs on node -1
[    0.846469] ahci 0000:00:1f.2: irq 27 for MSI/MSI-X
[    0.846479] ahci 0000:00:1f.2: controller can't do SNTF, turning off CAP_SNTF
[    0.846527] ahci: SSS flag set, parallel bus scan disabled
[    0.846571] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 6 ports 3 Gbps 0x3f impl RAID mode
[    0.846574] ahci 0000:00:1f.2: flags: 64bit ncq stag pm led clo pio slum part ccc ems sxs 
[    0.846579] ahci 0000:00:1f.2: setting latency timer to 64
[    0.862032] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    0.862075] r8169 0000:02:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.862162] r8169 0000:02:00.0: setting latency timer to 64
[    0.862308]   alloc irq_desc for 28 on node -1
[    0.862310]   alloc kstat_irqs on node -1
[    0.862346] r8169 0000:02:00.0: irq 28 for MSI/MSI-X
[    0.862888] eth0: RTL8168c/8111c at 0xffffc90000650000, 00:22:15:9d:f6:62, XID 1c4000c0 IRQ 28
[    0.873056]   alloc irq_desc for 20 on node -1
[    0.873059]   alloc kstat_irqs on node -1
[    0.873065] ohci1394 0000:01:05.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.932451] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[20]  MMIO=[fe9ff000-fe9ff7ff]  Max Packet=[2048]  IR/IT contexts=[8/8]
[    0.940473] scsi0 : ahci
[    0.940627] scsi1 : ahci
[    0.940704] scsi2 : ahci
[    0.940788] scsi3 : ahci
[    0.940863] scsi4 : ahci
[    0.940943] scsi5 : ahci
[    0.941112] ata1: SATA max UDMA/133 abar m2048@0xfe8ff000 port 0xfe8ff100 irq 27
[    0.941115] ata2: SATA max UDMA/133 abar m2048@0xfe8ff000 port 0xfe8ff180 irq 27
[    0.941118] ata3: SATA max UDMA/133 abar m2048@0xfe8ff000 port 0xfe8ff200 irq 27
[    0.941121] ata4: SATA max UDMA/133 abar m2048@0xfe8ff000 port 0xfe8ff280 irq 27
[    0.941123] ata5: SATA max UDMA/133 abar m2048@0xfe8ff000 port 0xfe8ff300 irq 27
[    0.941126] ata6: SATA max UDMA/133 abar m2048@0xfe8ff000 port 0xfe8ff380 irq 27
[    1.090048] usb 1-3: new high speed USB device using ehci_hcd and address 2
[    1.260953] usb 1-3: configuration #1 chosen from 1 choice
[    1.293793] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.294528] ata1.00: ATA-8: WDC WD3200AAJS-65B4A0, 01.03A01, max UDMA/133
[    1.294532] ata1.00: 625142448 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
[    1.295354] ata1.00: configured for UDMA/133
[    1.313900] scsi 0:0:0:0: Direct-Access     ATA      WDC WD3200AAJS-6 01.0 PQ: 0 ANSI: 5
[    1.314080] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.314111] sd 0:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    1.314172] sd 0:0:0:0: [sda] Write Protect is off
[    1.314174] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.314197] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.314314]  sda: sda1 < sda5 sda6 sda7 > sda2
[    1.345092] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.390024] usb 2-1: new high speed USB device using ehci_hcd and address 2
[    1.675765] usb 2-1: configuration #1 chosen from 1 choice
[    1.790079] usb 2-5: new high speed USB device using ehci_hcd and address 3
[    2.060040] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.061167] ata2.00: ATAPI: Optiarc DVD RW AD-7201S5, 1H0E, max UDMA/100
[    2.062652] ata2.00: configured for UDMA/100
[    2.081587] scsi 1:0:0:0: CD-ROM            Optiarc  DVD RW AD-7201S5 1H0E PQ: 0 ANSI: 5
[    2.086260] sr0: scsi3-mmc drive: 40x/40x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.086265] Uniform CD-ROM driver Revision: 3.20
[    2.086398] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.086488] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.250147] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[001e8c000175445b]
[    2.433788] ata3: SATA link down (SStatus 0 SControl 300)
[    2.485091] usb 2-5: configuration #1 chosen from 1 choice
[    2.490860] Initializing USB Mass Storage driver...
[    2.491001] scsi6 : SCSI emulation for USB Mass Storage devices
[    2.491081] usb-storage: device found at 3
[    2.491083] usb-storage: waiting for device to settle before scanning
[    2.491096] usbcore: registered new interface driver usb-storage
[    2.491099] USB Mass Storage support registered.
[    2.800029] ata4: SATA link down (SStatus 0 SControl 300)
[    3.173778] ata5: SATA link down (SStatus 0 SControl 300)
[    3.543777] ata6: SATA link down (SStatus 0 SControl 300)
[    4.006736] kjournald starting.  Commit interval 5 seconds
[    4.006752] EXT3-fs: mounted filesystem with ordered data mode.
[    7.490414] usb-storage: device scan complete
[    7.496772] scsi 6:0:0:0: Direct-Access     Generic- Compact Flash    1.00 PQ: 0 ANSI: 0 CCS
[    7.503012] scsi 6:0:0:1: Direct-Access     Generic- SM/xD-Picture    1.00 PQ: 0 ANSI: 0 CCS
[    7.509262] scsi 6:0:0:2: Direct-Access     Generic- SD/MMC           1.00 PQ: 0 ANSI: 0 CCS
[    7.515515] scsi 6:0:0:3: Direct-Access     Generic- MS/MS-Pro        1.00 PQ: 0 ANSI: 0 CCS
[    7.516081] sd 6:0:0:0: Attached scsi generic sg2 type 0
[    7.516190] sd 6:0:0:1: Attached scsi generic sg3 type 0
[    7.516304] sd 6:0:0:2: Attached scsi generic sg4 type 0
[    7.516433] sd 6:0:0:3: Attached scsi generic sg5 type 0
[    7.519874] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[    7.520622] sd 6:0:0:1: [sdc] Attached SCSI removable disk
[    7.521367] sd 6:0:0:2: [sdd] Attached SCSI removable disk
[    7.522124] sd 6:0:0:3: [sde] Attached SCSI removable disk
[    9.883514] udev: starting version 151
[    9.960750] Adding 3148668k swap on /dev/sda5.  Priority:-1 extents:1 across:3148668k 
[   10.033517] type=1505 audit(1289063705.717:2):  operation="profile_load" pid=593 name="/sbin/dhclient3"
[   10.034167] type=1505 audit(1289063705.727:3):  operation="profile_load" pid=593 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   10.034474] type=1505 audit(1289063705.727:4):  operation="profile_load" pid=593 name="/usr/lib/connman/scripts/dhclient-script"
[   10.140975] [drm] Initialized drm 1.1.0 20060810
[   10.202331] lp: driver loaded but no devices found
[   10.213194] cfg80211: Calling CRDA to update world regulatory domain
[   10.276682] cfg80211: World regulatory domain updated:
[   10.276684]  (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   10.276687]  (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.276689]  (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   10.276691]  (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   10.276694]  (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.276696]  (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.313187] [drm] radeon defaulting to kernel modesetting.
[   10.313189] [drm] radeon kernel modesetting enabled.
[   10.313235] radeon 0000:04:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   10.313240] radeon 0000:04:00.0: setting latency timer to 64
[   10.315694] [drm] radeon: Initializing kernel modesetting.
[   10.315891] [drm] register mmio base: 0xFEAF0000
[   10.315893] [drm] register mmio size: 65536
[   10.316017] ATOM BIOS: 113
[   10.316029] [drm] Clocks initialized !
[   10.318547] [drm] Detected VRAM RAM=256M, BAR=256M
[   10.318556] [drm] RAM width 64bits DDR
[   10.318668] [TTM] Zone  kernel: Available graphics memory: 1545806 kiB.
[   10.318691] [drm] radeon: 256M of VRAM memory ready
[   10.318693] [drm] radeon: 512M of GTT memory ready.
[   10.318735]   alloc irq_desc for 29 on node -1
[   10.318737]   alloc kstat_irqs on node -1
[   10.318746] radeon 0000:04:00.0: irq 29 for MSI/MSI-X
[   10.318751] radeon 0000:04:00.0: radeon: using MSI.
[   10.318775] [drm] radeon: irq initialized.
[   10.318778] [drm] GART: num cpu pages 131072, num gpu pages 131072
[   10.319169] [drm] Loading RV620 Microcode
[   10.319249] platform radeon_cp.0: firmware: requesting radeon/RV620_pfp.bin
[   10.412455] platform radeon_cp.0: firmware: requesting radeon/RV620_me.bin
[   10.414530] platform radeon_cp.0: firmware: requesting radeon/R600_rlc.bin
[   10.448806] [drm] ring test succeeded in 1 usecs
[   10.448905] [drm] radeon: ib pool ready.
[   10.448977] [drm] ib test succeeded in 0 usecs
[   10.448979] [drm] Enabling audio support
[   10.449190] [drm] Radeon Display Connectors
[   10.449192] [drm] Connector 0:
[   10.449193] [drm]   VGA
[   10.449195] [drm]   DDC: 0x7e50 0x7e50 0x7e54 0x7e54 0x7e58 0x7e58 0x7e5c 0x7e5c
[   10.449197] [drm]   Encoders:
[   10.449198] [drm]     CRT2: INTERNAL_KLDSCP_DAC2
[   10.449200] [drm] Connector 1:
[   10.449201] [drm]   DVI-I
[   10.449202] [drm]   HPD1
[   10.449204] [drm]   DDC: 0x7e40 0x7e40 0x7e44 0x7e44 0x7e48 0x7e48 0x7e4c 0x7e4c
[   10.449205] [drm]   Encoders:
[   10.449206] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
[   10.449208] [drm]     DFP1: INTERNAL_KLDSCP_LVTMA
[   10.562938] [drm] fb mappable at 0xD0141000
[   10.562940] [drm] vram apper at 0xD0000000
[   10.562942] [drm] size 7257600
[   10.562943] [drm] fb depth is 24
[   10.562944] [drm]    pitch is 6912
[   10.563003] fb0: radeondrmfb frame buffer device
[   10.563005] registered panic notifier
[   10.563009] [drm] Initialized radeon 2.0.0 20080528 for 0000:04:00.0 on minor 0
[   10.609316] phy0 -> rt2500usb_init_eeprom: Error - Invalid RT chipset detected.
[   10.609352] phy0 -> rt2x00lib_probe_dev: Error - Failed to allocate device.
[   10.609422] usbcore: registered new interface driver rt2500usb
[   10.749717] vga16fb: initializing
[   10.749720] vga16fb: mapped to 0xffff8800000a0000
[   10.749723] vga16fb: not registering due to another framebuffer present
[   10.908093] Console: switching to colour frame buffer device 210x65
[   10.961169] input: ImPS/2 Logitech Wheel Mouse as /devices/platform/i8042/serio1/input/input4
[   11.177293]   alloc irq_desc for 22 on node -1
[   11.177296]   alloc kstat_irqs on node -1
[   11.177304] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   11.177344] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   11.223606] phy1: Selected rate control algorithm 'minstrel'
[   11.224239] Registered led device: rt73usb-phy1::radio
[   11.224257] Registered led device: rt73usb-phy1::assoc
[   11.224273] Registered led device: rt73usb-phy1::quality
[   11.224814] usbcore: registered new interface driver rt73usb
[   11.343142] hda_codec: ALC1200: BIOS auto-probing.
[   11.344812] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input5
[   11.447699] EXT3 FS on sda6, internal journal
[   11.779535] EXT4-fs (sda7): mounted filesystem with ordered data mode
[   12.062589] EXT4-fs (sda2): mounted filesystem with ordered data mode
[   12.142846] type=1505 audit(1289063707.835:5):  operation="profile_replace" pid=914 name="/sbin/dhclient3"
[   12.143430] type=1505 audit(1289063707.835:6):  operation="profile_replace" pid=914 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   12.143691] r8169: eth0: link down
[   12.143745] type=1505 audit(1289063707.835:7):  operation="profile_replace" pid=914 name="/usr/lib/connman/scripts/dhclient-script"
[   12.144237] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   12.145650] rt73usb 2-1:1.0: firmware: requesting rt73.bin
[   12.146555] type=1505 audit(1289063707.835:8):  operation="profile_load" pid=918 name="/usr/lib/cups/backend/cups-pdf"
[   12.147270] type=1505 audit(1289063707.835:9):  operation="profile_load" pid=918 name="/usr/sbin/cupsd"
[   12.149233] type=1505 audit(1289063707.835:10):  operation="profile_load" pid=922 name="/usr/sbin/mysqld-akonadi"
[   12.150707] type=1505 audit(1289063707.835:11):  operation="profile_load" pid=923 name="/usr/sbin/tcpdump"
[   12.249333] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   12.435183] ppdev: user-space parallel port driver
[  179.079857] wlan0: deauthenticating from 00:19:3e:40:b1:af by local choice (reason=3)
[  179.083575] wlan0: direct probe to AP 00:19:3e:40:b1:af (try 1)
[  179.085588] wlan0: direct probe responded
[  179.085590] wlan0: authenticate with AP 00:19:3e:40:b1:af (try 1)
[  179.087326] wlan0: authenticated
[  179.087349] wlan0: associate with AP 00:19:3e:40:b1:af (try 1)
[  179.089831] wlan0: RX AssocResp from 00:19:3e:40:b1:af (capab=0x411 status=0 aid=2)
[  179.089834] wlan0: associated
[  179.103532] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  189.181280] wlan0: no IPv6 routers present
[  279.715302] lo: Disabled Privacy Extensions
[ 2443.540023] No probe response from AP 00:19:3e:40:b1:af after 500ms, disconnecting.
[ 2445.113952] wlan0: direct probe to AP 00:19:3e:40:b1:af (try 1)
[ 2445.115964] wlan0: direct probe responded
[ 2445.115967] wlan0: authenticate with AP 00:19:3e:40:b1:af (try 1)
[ 2445.117700] wlan0: authenticated
[ 2445.117723] wlan0: associate with AP 00:19:3e:40:b1:af (try 1)
[ 2445.120080] wlan0: RX AssocResp from 00:19:3e:40:b1:af (capab=0x411 status=0 aid=2)
[ 2445.120085] wlan0: associated
[ 2445.160491] usb 1-3: USB disconnect, address 2
[ 2449.952526] usb 1-3: new high speed USB device using ehci_hcd and address 3
[ 2450.123508] usb 1-3: configuration #1 chosen from 1 choice
[ 2528.540021] No probe response from AP 00:19:3e:40:b1:af after 500ms, disconnecting.
[ 2542.544663] wlan0: direct probe to AP 00:19:3e:40:b1:af (try 1)
[ 2542.740025] wlan0: direct probe to AP 00:19:3e:40:b1:af (try 2)
[ 2542.940028] wlan0: direct probe to AP 00:19:3e:40:b1:af (try 3)
[ 2542.946897] wlan0: direct probe responded
[ 2542.946901] wlan0: authenticate with AP 00:19:3e:40:b1:af (try 1)
[ 2543.140026] wlan0: authenticate with AP 00:19:3e:40:b1:af (try 2)
[ 2543.145880] wlan0: authenticated
[ 2543.145901] wlan0: associate with AP 00:19:3e:40:b1:af (try 1)
[ 2543.196628] wlan0: RX AssocResp from 00:19:3e:40:b1:af (capab=0x411 status=0 aid=2)
[ 2543.196631] wlan0: associated
[ 2544.611826] wlan0: deauthenticating from 00:19:3e:40:b1:af by local choice (reason=3)
[ 2544.810301] wlan0: deauthenticating from 00:19:3e:40:b1:af by local choice (reason=3)
[ 2545.011023] wlan0: direct probe to AP 00:19:3e:40:b1:af (try 1)
[ 2545.200049] wlan0: direct probe to AP 00:19:3e:40:b1:af (try 2)
[ 2545.400018] wlan0: direct probe to AP 00:19:3e:40:b1:af (try 3)
[ 2545.600020] wlan0: direct probe to AP 00:19:3e:40:b1:af timed out
[ 2555.979916] wlan0: direct probe to AP 00:19:3e:40:b1:af (try 1)
[ 2556.181279] wlan0: direct probe to AP 00:19:3e:40:b1:af (try 2)
[ 2556.185536] wlan0: direct probe responded
[ 2556.185540] wlan0: authenticate with AP 00:19:3e:40:b1:af (try 1)
[ 2556.188150] wlan0: authenticated
[ 2556.188172] wlan0: associate with AP 00:19:3e:40:b1:af (try 1)
[ 2556.206404] wlan0: RX AssocResp from 00:19:3e:40:b1:af (capab=0x411 status=0 aid=2)
[ 2556.206408] wlan0: associated
[ 2603.540035] No probe response from AP 00:19:3e:40:b1:af after 500ms, disconnecting.
[ 2605.174181] wlan0: direct probe to AP 00:19:3e:40:b1:af (try 1)
[ 2605.374045] wlan0: direct probe to AP 00:19:3e:40:b1:af (try 2)
[ 2605.570052] wlan0: direct probe to AP 00:19:3e:40:b1:af (try 3)
[ 2605.770026] wlan0: direct probe to AP 00:19:3e:40:b1:af timed out
[ 2616.491803] wlan0: direct probe to AP 00:19:3e:40:b1:af (try 1)
[ 2616.493815] wlan0: direct probe responded
[ 2616.493819] wlan0: authenticate with AP 00:19:3e:40:b1:af (try 1)
[ 2616.495548] wlan0: authenticated
[ 2616.495570] wlan0: associate with AP 00:19:3e:40:b1:af (try 1)
[ 2616.497928] wlan0: RX AssocResp from 00:19:3e:40:b1:af (capab=0x411 status=0 aid=2)
[ 2616.497930] wlan0: associated
[ 6331.379639] lo: Disabled Privacy Extensions

I'll appreciate your help! ;)

---

### Post by vagrale13 on 2010-11-09
> **ilovemoon86 said:**
> Hi vagrale13, :)
unfortunately your package doesn't work with my NETGEAR N150 WNA1100... :confused:

Now my connection works thanks to my brother's RT2501USB Wireless Adapter :S

OUTPUT OF SOME COMMANDS



I'll appreciate your help! ;)
Can you post the output of commands
```
cat /etc/modules
ls -l /lib/firmware/ar*
```

---

### Post by rileyedward on 2010-11-15
new to ubuntu, love it so far.
My wna1100 was working fine in 10.04, upgraded to 10.10 and reloaded ath9k and still it worked fine.  did some recent updates form the update manager and i've got all kinds of issues now.  #1 being wna 1100 does not work any longer.  i have removed and reinstalled ath9k and still nothing. 
lsusb shows it, but it no workie......
#2 also now on reboot I can't use my usb wireless key board and mouse.  I have to type in my password on a second serial keyboard and wait about five minutes and then the usb stuff starts working.

using my htc evo for internet now, tethering from wifi.  that works great right off the bat, just an FYI 
thanks in advance for any suggetions.

results of :

uname -r
lsmod | grep ath9k
dmesg
cat /etc/modules
ls -l /lib/firmware/ar*


[    0.308495] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.309166] fuse init (API version 7.14)
[    0.309252] msgmni has been set to 1657
[    0.316437] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.316442] io scheduler noop registered
[    0.316444] io scheduler deadline registered
[    0.316461] io scheduler cfq registered (default)
[    0.316601] pcieport 0000:00:02.0: setting latency timer to 64
[    0.316620]   alloc irq_desc for 40 on node -1
[    0.316622]   alloc kstat_irqs on node -1
[    0.316632] pcieport 0000:00:02.0: irq 40 for MSI/MSI-X
[    0.316692] pcieport 0000:00:03.0: setting latency timer to 64
[    0.316707]   alloc irq_desc for 41 on node -1
[    0.316709]   alloc kstat_irqs on node -1
[    0.316714] pcieport 0000:00:03.0: irq 41 for MSI/MSI-X
[    0.316764] pcieport 0000:00:04.0: setting latency timer to 64
[    0.316779]   alloc irq_desc for 42 on node -1
[    0.316780]   alloc kstat_irqs on node -1
[    0.316785] pcieport 0000:00:04.0: irq 42 for MSI/MSI-X
[    0.316855] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.316880] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.317084] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.317091] ACPI: Power Button [PWRB]
[    0.317152] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.317155] ACPI: Power Button [PWRF]
[    0.317215] ACPI: Fan [FAN] (on)
[    0.317594] ACPI: acpi_idle registered with cpuidle
[    0.322302] thermal LNXTHERM:01: registered as thermal_zone0
[    0.322311] ACPI: Thermal Zone [THRM] (15 C)
[    0.322365] ERST: Table is not found!
[    0.328468] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.329829] brd: module loaded
[    0.330326] loop: module loaded
[    0.330615] pata_acpi 0000:00:0d.0: setting latency timer to 64
[    0.331010] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 23
[    0.331018]   alloc irq_desc for 23 on node -1
[    0.331020]   alloc kstat_irqs on node -1
[    0.331033] pata_acpi 0000:00:0e.0: PCI INT A -> Link[APSI] -> GSI 23 (level, low) -> IRQ 23
[    0.331076] pata_acpi 0000:00:0e.0: setting latency timer to 64
[    0.331083] pata_acpi 0000:00:0e.0: PCI INT A disabled
[    0.331412] Fixed MDIO Bus: probed
[    0.331448] PPP generic driver version 2.4.2
[    0.331489] tun: Universal TUN/TAP device driver, 1.6
[    0.331491] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.331570] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.331886] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 22
[    0.331889]   alloc irq_desc for 22 on node -1
[    0.331890]   alloc kstat_irqs on node -1
[    0.331899] ehci_hcd 0000:00:0b.1: PCI INT B -> Link[APCL] -> GSI 22 (level, low) -> IRQ 22
[    0.331922] ehci_hcd 0000:00:0b.1: setting latency timer to 64
[    0.331925] ehci_hcd 0000:00:0b.1: EHCI Host Controller
[    0.331961] ehci_hcd 0000:00:0b.1: new USB bus registered, assigned bus number 1
[    0.331990] ehci_hcd 0000:00:0b.1: debug port 1
[    0.332049] ehci_hcd 0000:00:0b.1: cache line size of 32 is not supported
[    0.332088] isapnp: Scanning for PnP cards...
[    0.337572] ehci_hcd 0000:00:0b.1: irq 22, io mem 0xfebfe000
[    0.387625] ehci_hcd 0000:00:0b.1: USB 2.0 started, EHCI 1.00
[    0.387820] hub 1-0:1.0: USB hub found
[    0.387825] hub 1-0:1.0: 8 ports detected
[    0.387918] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.388336] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 21
[    0.388342]   alloc irq_desc for 21 on node -1
[    0.388344]   alloc kstat_irqs on node -1
[    0.388356] ohci_hcd 0000:00:0b.0: PCI INT A -> Link[APCF] -> GSI 21 (level, low) -> IRQ 21
[    0.388380] ohci_hcd 0000:00:0b.0: setting latency timer to 64
[    0.388383] ohci_hcd 0000:00:0b.0: OHCI Host Controller
[    0.388431] ohci_hcd 0000:00:0b.0: new USB bus registered, assigned bus number 2
[    0.388471] ohci_hcd 0000:00:0b.0: irq 21, io mem 0xfebff000
[    0.473639] hub 2-0:1.0: USB hub found
[    0.473648] hub 2-0:1.0: 8 ports detected
[    0.473736] uhci_hcd: USB Universal Host Controller Interface driver
[    0.473844] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    [COLOR="red"]0.473846] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp[/COLOR]
[    0.474831] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.474924] mice: PS/2 mouse device common for all mice
[    0.475063] rtc_cmos 00:04: RTC can wake from S4
[    0.475105] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    0.475138] rtc0: alarms up to one year, y3k, 242 bytes nvram
[    0.475248] device-mapper: uevent: version 1.0.3
[    0.479577] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: [email]dm-devel@redhat.com[/email]
[    0.484095] device-mapper: multipath: version 1.1.1 loaded
[    0.484101] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.484342] EISA: Probing bus 0 at eisa.0
[    0.484346] EISA: Cannot allocate resource for mainboard
[    0.484348] Cannot allocate resource for EISA slot 1
[    0.484351] Cannot allocate resource for EISA slot 2
[    0.484353] Cannot allocate resource for EISA slot 3
[    0.484355] Cannot allocate resource for EISA slot 4
[    0.484357] Cannot allocate resource for EISA slot 5
[    0.484359] Cannot allocate resource for EISA slot 6
[    0.484361] Cannot allocate resource for EISA slot 7
[    0.484364] Cannot allocate resource for EISA slot 8
[    0.484365] EISA: Detected 0 cards.
[    0.492117] cpuidle: using governor ladder
[    0.492121] cpuidle: using governor menu
[    0.492459] TCP cubic registered
[    0.492595] NET: Registered protocol family 10
[    0.492959] lo: Disabled Privacy Extensions
[    0.493149] NET: Registered protocol family 17
[    0.493196] powernow-k8: Found 1 AMD Athlon(tm) 64 Processor 3500+ (1 cpu cores) (version 2.20.00)
[    0.493255] powernow-k8:    0 : fid 0xe (2200 MHz), vid 0x6
[    0.493257] powernow-k8:    1 : fid 0xc (2000 MHz), vid 0x8
[    0.493260] powernow-k8:    2 : fid 0xa (1800 MHz), vid 0xa
[    0.493262] powernow-k8:    3 : fid 0x2 (1000 MHz), vid 0x12
[    0.493305] Using IPI No-Shortcut mode
[    0.493420] [COLOR="red"]PM: Resume from disk failed.[/COLOR]
[    0.493441] registered taskstats version 1
[    0.493715]   Magic number: 2:734:232
[    0.493861] rtc_cmos 00:04: setting system clock to 2010-11-14 14:13:23 UTC (1289744003)
[    0.493865] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.493867] [COLOR="red"]EDD information not available[/COLOR].
[    0.500789] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[    0.739614] usb 1-2: new high speed USB device using ehci_hcd and address 2
[    0.863732] Freeing initrd memory: 10512k freed
[    0.963794] [COLOR="red"]isapnp: No Plug & Play device found[/COLOR]
[    0.963810] Freeing unused kernel memory: 684k freed
[    0.964720] Write protecting the kernel text: 4932k
[    0.964749] Write protecting the kernel read-only data: 1976k
[    0.982320] udev[63]: starting version 163
[    1.191860] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.64.
[    1.192275] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 20
[    1.192282]   alloc irq_desc for 20 on node -1
[    1.192284]   alloc kstat_irqs on node -1
[    1.192297] forcedeth 0000:00:14.0: PCI INT A -> Link[APCH] -> GSI 20 (level, low) -> IRQ 20
[    1.192302] forcedeth 0000:00:14.0: setting latency timer to 64
[    1.192363] nv_probe: set workaround bit for reversed mac addr
[    1.266249] ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
[    1.266257]   alloc irq_desc for 19 on node -1
[    1.266260]   alloc kstat_irqs on node -1
[    1.266273] firewire_ohci 0000:04:06.0: PCI INT A -> Link[APC4] -> GSI 19 (level, low) -> IRQ 19
[    1.320074] firewire_ohci: Added fw-ohci device 0000:04:06.0, OHCI v1.10, 4 IR + 8 IT contexts, quirks 0x2
[    1.712730] forcedeth 0000:00:14.0: ifname eth0, PHY OUI 0x50ef @ 1, addr 00:15:58:1f:76:20
[    1.712735] forcedeth 0000:00:14.0: highdma pwrctl lnktim desc-v3
[    1.712847] pata_amd 0000:00:0d.0: version 0.4.1
[    1.712904] pata_amd 0000:00:0d.0: setting latency timer to 64
[    1.713612] scsi0 : pata_amd
[    1.713769] scsi1 : pata_amd
[    1.714543] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xf400 irq 14
[    1.714546] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xf408 irq 15
[    1.714673] sata_nv 0000:00:0e.0: version 3.5
[    1.714687] sata_nv 0000:00:0e.0: PCI INT A -> Link[APSI] -> GSI 23 (level, low) -> IRQ 23
[    1.714691] sata_nv 0000:00:0e.0: Using SWNCQ mode
[    1.714755] sata_nv 0000:00:0e.0: setting latency timer to 64
[    1.715228] scsi2 : sata_nv
[    1.715338] scsi3 : sata_nv
[    1.715534] ata3: SATA max UDMA/133 cmd 0x9f0 ctl 0xbf0 bmdma 0xe000 irq 23
[    1.715537] ata4: SATA max UDMA/133 cmd 0x970 ctl 0xb70 bmdma 0xe008 irq 23
[    1.820120] firewire_core: created device fw0: GUID 00016c200019542f, S400
[    1.897981] ata1.00: ATA-7: WDC WD1200BB-00RDA0, 20.00K20, max UDMA/100
[    1.897984] ata1.00: 234441648 sectors, multi 16: LBA48 
[    1.898150] ata1.01: ATA-7: ST3200826A, 3.03, max UDMA/100
[    1.898153] ata1.01: 390721968 sectors, multi 16: LBA48 
[    1.898175] ata1: nv_mode_filter: 0x3f39f&0x3f39f->0x3f39f, BIOS=0x3f000 (0xc6c6c000) ACPI=0x3f01f (20:20:0x1f)
[    1.898181] ata1: nv_mode_filter: 0x3f39f&0x3f39f->0x3f39f, BIOS=0x3f000 (0xc6c6c000) ACPI=0x3f01f (20:20:0x1f)
[    1.904419] ata1.00: configured for UDMA/100
[    1.920367] ata1.01: configured for UDMA/100
[    1.920488] scsi 0:0:0:0: Direct-Access     ATA      WDC WD1200BB-00R 20.0 PQ: 0 ANSI: 5
[    1.920643] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.920891] scsi 0:0:1:0: Direct-Access     ATA      ST3200826A       3.03 PQ: 0 ANSI: 5
[    1.920988] sd 0:0:1:0: Attached scsi generic sg1 type 0
[    1.921236] sd 0:0:0:0: [sda] 234441648 512-byte logical blocks: (120 GB/111 GiB)
[    1.921280] sd 0:0:0:0: [sda] Write Protect is off
[    1.921283] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.921302] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.921433]  sda: sda1 sda2 < sda5 sda6
[    1.942300] sd 0:0:1:0: [sdb] 390721968 512-byte logical blocks: (200 GB/186 GiB)
[    1.954062]  sda7 >
[    1.954707] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.954748] sd 0:0:1:0: [sdb] Write Protect is off
[    1.954751] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[    1.954768] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.954879]  sdb: sdb1 sdb2 < sdb5 >
[    2.001712] sd 0:0:1:0: [sdb] Attached SCSI disk
[    2.024032] ata3: SATA link down (SStatus 0 SControl 300)
[    2.084316] ata2.00: ATAPI: TSSTcorpCD/DVDW SH-S182M, SB00, max UDMA/33
[    2.084341] ata2: nv_mode_filter: 0x739f&0x739f->0x739f, BIOS=0x7000 (0xc6c6c000) ACPI=0x701f (60:600:0x13)
[    2.100263] ata2.00: configured for UDMA/33
[    2.101584] scsi 1:0:0:0: CD-ROM            TSSTcorp CD/DVDW SH-S182M SB00 PQ: 0 ANSI: 5
[    2.108599] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.108603] Uniform CD-ROM driver Revision: 3.20
[    2.108894] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    2.109002] sr 1:0:0:0: Attached scsi generic sg2 type 5
[    2.420028] ata4: SATA link down (SStatus 0 SControl 300)
[    3.343860] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[   15.200312] udev[387]: starting version 163
[   15.201991] Adding 4805628k swap on /dev/sda5.  Priority:-1 extents:1 across:4805628k 
[   15.357290] i2c i2c-0: nForce2 SMBus adapter at 0xfc00
[   15.357319] i2c i2c-1: nForce2 SMBus adapter at 0xf800
[   15.366164] lp: driver loaded but no devices found
[   15.428063] [COLOR="red"]Compat-wireless backport release: compat-wireless-2010-10-14-1-gf0578ae[/COLOR]
[   15.428068] Backport based on linux-next.git next-20101015
[   15.501601] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   15.574846] parport_pc 00:07: reported by Plug and Play ACPI
[   15.574902] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   15.608287] Linux agpgart interface v0.103
[   15.684173] Linux video capture interface: v2.00
[   15.730037] lp0: using parport0 (interrupt-driven).
[   15.848078] usb 1-2: device descriptor read/64, error -110
[   15.905562] ppdev: user-space parallel port driver
[   15.926340] cfg80211: Calling CRDA to update world regulatory domain
[   15.936627] type=1400 audit(1289762018.941:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=663 comm="apparmor_parser"
[   15.936920] type=1400 audit(1289762018.941:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=663 comm="apparmor_parser"
[   15.937086] type=1400 audit(1289762018.941:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=663 comm="apparmor_parser"
[   15.969843] ivtv: Start initialization, version 1.4.1
[   15.969979] ivtv0: Initializing card 0
[   15.969984] ivtv0: Autodetected Hauppauge card (cx23416 based)
[   15.982411] ACPI: PCI Interrupt Link [APC1] enabled at IRQ 16
[   15.982419]   alloc irq_desc for 16 on node -1
[   15.982421]   alloc kstat_irqs on node -1
[   15.982435] ivtv 0000:04:07.0: PCI INT A -> Link[APC1] -> GSI 16 (level, low) -> IRQ 16
[   15.982444] ivtv0: Unreasonably low latency timer, setting to 64 (was 32)
[   16.035978] tveeprom 2-0050: Hauppauge model 26582, rev F0B2, serial# 9410763
[   16.035981] tveeprom 2-0050: tuner model is TCL M2523_5N_E (idx 112, type 50)
[   16.035985] tveeprom 2-0050: TV standards NTSC(M) (eeprom 0x08)
[   16.035987] tveeprom 2-0050: audio processor is CX25843 (idx 37)
[   16.035990] tveeprom 2-0050: decoder processor is CX25843 (idx 30)
[   16.035992] tveeprom 2-0050: has no radio
[   16.035996] ivtv0: Autodetected Hauppauge WinTV PVR-150
[   16.060268] cfg80211: World regulatory domain updated:
[   16.060274]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   16.060278]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   16.060281]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   16.060284]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   16.060286]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   16.060289]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   16.086074] [drm] Initialized drm 1.1.0 20060810
[   16.287437] [COLOR="red"]usbcore: registered new interface driver ath9k_hif_usb[/COLOR]
[   16.313204] ACPI: PCI Interrupt Link [APC5] enabled at IRQ 16
[   16.313213] nouveau 0000:03:00.0: PCI INT A -> Link[APC5] -> GSI 16 (level, low) -> IRQ 16
[   16.313219] nouveau 0000:03:00.0: setting latency timer to 64
[   16.333700] [drm] nouveau 0000:03:00.0: Detected an NV50 generation card (0x096000c1)
[   16.342236] [drm] nouveau 0000:03:00.0: Attempting to load BIOS image from PRAMIN
[   16.399224] [drm] nouveau 0000:03:00.0: ... appears to be valid
[   16.399229] [drm] nouveau 0000:03:00.0: BIT BIOS found
[   16.399233] [drm] nouveau 0000:03:00.0: Bios version 62.94.4b.00
[   16.399237] [drm] nouveau 0000:03:00.0: TMDS table revision 2.0 not currently supported
[   16.399241] [drm] nouveau 0000:03:00.0: Found Display Configuration Block version 4.0
[   16.399244] [drm] nouveau 0000:03:00.0: Raw DCB entry 0: 02000300 00000028
[   16.399248] [drm] nouveau 0000:03:00.0: Raw DCB entry 1: 01000302 00020030
[   16.399251] [drm] nouveau 0000:03:00.0: Raw DCB entry 2: 04011310 00000028
[   16.399254] [drm] nouveau 0000:03:00.0: Raw DCB entry 3: 02011312 00020030
[   16.399256] [drm] nouveau 0000:03:00.0: Raw DCB entry 4: 010223f1 00c0c080
[   16.399259] [drm] nouveau 0000:03:00.0: Raw DCB entry 5: 04022342 00020030
[   16.399263] [drm] nouveau 0000:03:00.0: DCB connector table: VHER 0x40 5 16 4
[   16.399266] [drm] nouveau 0000:03:00.0:   0: 0x00001030: type 0x30 idx 0 tag 0x07
[   16.399269] [drm] nouveau 0000:03:00.0:   1: 0x00002130: type 0x30 idx 1 tag 0x08
[   16.399273] [drm] nouveau 0000:03:00.0:   2: 0x00000210: type 0x10 idx 2 tag 0xff
[   16.399276] [drm] nouveau 0000:03:00.0:   3: 0x00000211: type 0x11 idx 3 tag 0xff
[   16.399279] [drm] nouveau 0000:03:00.0:   4: 0x00000213: type 0x13 idx 4 tag 0xff
[   16.399282] [drm] nouveau 0000:03:00.0:   5: 0x00010261: type 0x61 idx 5 tag 0x51
[   16.399291] [drm] nouveau 0000:03:00.0: Parsing VBIOS init table 0 at offset 0xD20A
[   16.499547] cx25840 2-0044: cx25843-24 found @ 0x88 (ivtv i2c driver #0)
[   16.502176] ACPI: PCI Interrupt Link [APCJ] enabled at IRQ 23
[   16.502184] Intel ICH 0000:00:10.2: PCI INT C -> Link[APCJ] -> GSI 23 (level, low) -> IRQ 23
[   16.502224] Intel ICH 0000:00:10.2: setting latency timer to 64
[   16.550878] tuner 2-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[   16.579810] wm8775 2-001b: chip found @ 0x36 (ivtv i2c driver #0)
[   16.658980] type=1400 audit(1289762019.661:5): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=885 comm="apparmor_parser"
[   16.664839] tuner-simple 2-0061: creating new instance
[   16.664845] tuner-simple 2-0061: type set to 50 (TCL 2002N)
[   16.666411] ivtv0: Registered device video0 for encoder MPG (4096 kB)
[   16.666506] ivtv0: Registered device video32 for encoder YUV (2048 kB)
[   16.666595] ivtv0: Registered device vbi0 for encoder VBI (1024 kB)
[   16.666700] ivtv0: Registered device video24 for encoder PCM (320 kB)
[   16.666703] ivtv0: Initialized card: Hauppauge WinTV PVR-150
[   16.667558] ivtv: End initialization
[   16.675736] type=1400 audit(1289762019.677:6): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=888 comm="apparmor_parser"
[   16.679440] type=1400 audit(1289762019.681:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=888 comm="apparmor_parser"
[   16.679634] type=1400 audit(1289762019.681:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=888 comm="apparmor_parser"
[   16.694378] type=1400 audit(1289762019.697:9): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=895 comm="apparmor_parser"
[   16.702624] type=1400 audit(1289762019.705:10): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=895 comm="apparmor_parser"
[   16.709860] type=1400 audit(1289762019.713:11): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-thumbnailer" pid=895 comm="apparmor_parser"
[   16.736194] [drm] nouveau 0000:03:00.0: Parsing VBIOS init table 1 at offset 0xD657
[   16.752121] [drm] nouveau 0000:03:00.0: Parsing VBIOS init table 2 at offset 0xE6A7
[   16.752133] [drm] nouveau 0000:03:00.0: Parsing VBIOS init table 3 at offset 0xE7F0
[   16.764170] [drm] nouveau 0000:03:00.0: Parsing VBIOS init table 4 at offset 0xEA5C
[   16.764174] [drm] nouveau 0000:03:00.0: Parsing VBIOS init table at offset 0xEAC1
[   16.788029] [drm] nouveau 0000:03:00.0: 0xEAC1: Condition still not met after 20ms, skipping following opcodes
[   16.788041] [drm] nouveau 0000:03:00.0: 0xC1DC: parsing output script 0
[   16.788048] [drm] nouveau 0000:03:00.0: 0xC1DC: parsing output script 0
[   16.788055] [drm] nouveau 0000:03:00.0: 0xAC16: parsing output script 0
[   16.788057] [drm] nouveau 0000:03:00.0: 0xC1DC: parsing output script 0
[   16.788070] [drm] nouveau 0000:03:00.0: Detected 1024MiB VRAM
[   16.899953] intel8x0_measure_ac97_clock: measured 126691 usecs (6144 samples)
[   16.899957] intel8x0: clocking to 48000
[   16.952994] e[COLOR="red"]th0: no link during initialization.
[   16.953568] ADDRCONF(NETDEV_UP): eth0: link is not ready[/COLOR]
[   17.016270] [TTM] Zone  kernel: Available graphics memory: 429880 kiB.
[   17.016274] [TTM] Zone highmem: Available graphics memory: 1547548 kiB.
[   17.016276] [TTM] Initializing pool allocator.
[   17.027375] [drm] nouveau 0000:03:00.0: 512 MiB GART (aperture)
[   17.027733] [drm] nouveau 0000:03:00.0: Allocating FIFO number 1
[   17.030933] [drm] nouveau 0000:03:00.0: nouveau_channel_alloc: initialised FIFO 1
[   17.031450] [drm] nouveau 0000:03:00.0: Detected a DAC output
[   17.031454] [drm] nouveau 0000:03:00.0: Detected a TMDS output
[   17.031457] [drm] nouveau 0000:03:00.0: Detected a DAC output
[   17.031460] [drm] nouveau 0000:03:00.0: Detected a TMDS output
[   17.031464] [drm] nouveau 0000:03:00.0: DCB encoder 1 unknown
[   17.031466] [drm] nouveau 0000:03:00.0: Detected a TMDS output
[   17.031469] [drm] nouveau 0000:03:00.0: Detected a DVI-I connector
[   17.031712] [drm] nouveau 0000:03:00.0: Detected a DVI-I connector
[   17.031868] [drm] nouveau 0000:03:00.0: Detected a TV connector
[   17.339043] ivtv0: Loaded v4l-cx2341x-enc.fw firmware (376836 bytes)
[   17.381283] [drm] nouveau 0000:03:00.0: allocated 1360x768 fb: 0x40250000, bo f4990a00
[   17.384765] [drm] nouveau 0000:03:00.0: 0x11F7: parsing clock script 0
[   17.387971] Console: switching to colour frame buffer device 170x48
[   17.389002] fb0: nouveaufb frame buffer device
[   17.389004] drm: registered panic notifier
[   17.389008] Slow work thread pool: Starting up
[   17.395674] Slow work thread pool: Ready
[   17.395690] [drm] Initialized nouveau 0.0.16 20090420 for 0000:03:00.0 on minor 0
[   17.548146] ivtv0: Encoder revision: 0x02060039
[   18.627884] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   18.834176] [drm] nouveau 0000:03:00.0: Allocating FIFO number 2
[   18.847000] [drm] nouveau 0000:03:00.0: nouveau_channel_alloc: initialised FIFO 2
[   20.827440] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   29.341516] cx25840 2-0044: loaded v4l-cx25840.fw firmware (16382 bytes)
[   31.068053] [COLOR="red"]usb 1-2: device descriptor read/64, error -110
[   31.284029] usb 1-2: new high speed USB device using ehci_hcd and address 3
[   46.396037] usb 1-2: device descriptor read/64, error -110
[   61.612042] usb 1-2: device descriptor read/64, error -110
[   61.828045] usb 1-2: new high speed USB device using ehci_hcd and address 4
[   72.236026] usb 1-2: device not accepting address 4, error -110
[   72.348031] usb 1-2: new high speed USB device using ehci_hcd and address 5[/COLOR]
[   79.576038] Clocksource tsc unstable (delta = -272725301 ns)
[   82.756046][COLOR="red"] usb 1-2: device not accepting address 5, error -110
[   82.756071] hub 1-0:1.0: unable to enumerate USB device on port 2
[   83.060260] usb 1-8: new high speed USB device using ehci_hcd and address 8[/COLOR]
[   83.370755] usbcore: registered new interface driver cdc_ether
[   83.403535] 
[   93.792024] usb0: no IPv6 routers present
[   98.688039] usb 2-2: device descriptor read/64, error -110rndis_host 1-8:1.0: usb0: register 'rndis_host' at usb-0000:00:0b.1-8, RNDIS device, 72:b6:12:a2:7d:57
[   83.403563] [COLOR="red"]usbcore: registered new interface driver rndis_host
[   83.417348] rndis_wlan: disagrees about version of symbol cfg80211_scan_done
[   83.417355] rndis_wlan: Unknown symbol cfg80211_scan_done (err -22)
[   83.417825] rndis_wlan: disagrees about version of symbol cfg80211_disconnected
[   83.417827] rndis_wlan: Unknown symbol cfg80211_disconnected (err -22)
[   83.418216] rndis_wlan: disagrees about version of symbol wiphy_register
[   83.418219] rndis_wlan: Unknown symbol wiphy_register (err -22)
[   83.418311] rndis_wlan: disagrees about version of symbol wiphy_new
[   83.418313] rndis_wlan: Unknown symbol wiphy_new (err -22)
[   83.418409] rndis_wlan: disagrees about version of symbol cfg80211_roamed
[   83.418411] rndis_wlan: Unknown symbol cfg80211_roamed (err -22)
[   83.418506] rndis_wlan: disagrees about version of symbol cfg80211_inform_bss
[   83.418508] rndis_wlan: Unknown symbol cfg80211_inform_bss (err -22)
[   83.418657] rndis_wlan: disagrees about version of symbol cfg80211_ibss_joined
[   83.418659] rndis_wlan: Unknown symbol cfg80211_ibss_joined (err -22)
[   83.418971] rndis_wlan: disagrees about version of symbol cfg80211_michael_mic_failure
[   83.418973] rndis_wlan: Unknown symbol cfg80211_michael_mic_failure (err -22)
[   83.419123] rndis_wlan: disagrees about version of symbol cfg80211_connect_result
[   83.419126] rndis_wlan: Unknown symbol cfg80211_connect_result (err -22)
[   83.419308] rndis_wlan: disagrees about version of symbol wiphy_unregister
[   83.419310] rndis_wlan: Unknown symbol wiphy_unregister (err -22)
[   83.419524] rndis_wlan: disagrees about version of symbol __ieee80211_get_channel
[   83.419526] rndis_wlan: Unknown symbol __ieee80211_get_channel (err -22)
[   83.422049] rndis_wlan: disagrees about version of symbol wiphy_free
[   83.422052] rndis_wlan: Unknown symbol wiphy_free (err -22)
[   83.512059] usb 2-2: new full speed USB device using ohci_hcd and address 2ng ohci_hcd and address 2
[  113.968049] usb 2-2: device descriptor read/64, error -110
[  114.248038] usb 2-2: new full speed USB device using ohci_hcd and address 3
[  129.424028] usb 2-2: device descriptor read/64, error -110
[  144.704041] usb 2-2: device descriptor read/64, error -110
[  144.984082] usb 2-2: new full speed USB device using ohci_hcd and address 4
[  155.392032] usb 2-2: device not accepting address 4, error -110
[  155.568090] usb 2-2: new full speed USB device using ohci_hcd and address 5
[  165.976034] usb 2-2: device not accepting address 5, error -110
[  165.976056] hub 2-0:1.0: unable to enumerate USB device on port 2
[  166.152046] usb 2-4: new full speed USB device using ohci_hcd and address 6
[  166.432094] Initializing USB Mass Storage driver...
[  166.432281] scsi4 : usb-storage 2-4:1.0
[  166.432581] usbcore: registered new interface driver usb-storage
[  166.432585] USB Mass Storage support registered.[/COLOR]
[  166.676038] usb 2-7: new low speed USB device using ohci_hcd and address 7
[  166.973662] usbcore: registered new interface driver hiddev
[  166.977171] usbcore: registered new interface driver usbhid
[  166.977179] usbhid: USB HID core driver
[  167.008282] input: Microsoft Microsoft Wireless Optical Desktop® 2.10 as /devices/pci0000:00/0000:00:0b.0/usb2/2-7/2-7:1.0/input/input3
[  167.010621] microsoft 0003:045E:009D.0001: input,hidraw0: USB HID v1.11 Keyboard [Microsoft Microsoft Wireless Optical Desktop® 2.10] on usb-0000:00:0b.0-7/input0
[  167.052637] input: Microsoft Microsoft Wireless Optical Desktop® 2.10 as /devices/pci0000:00/0000:00:0b.0/usb2/2-7/2-7:1.1/input/input4
[  167.053147] microsoft 0003:045E:009D.0002: input,hidraw1: USB HID v1.11 Mouse [Microsoft Microsoft Wireless Optical Desktop® 2.10] on usb-0000:00:0b.0-7/input1
[  167.444178] scsi 4:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
[  167.451170] scsi 4:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
[  167.458168] scsi 4:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ: 0 ANSI: 0
[  167.465170] scsi 4:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0
[  167.469157] sd 4:0:0:0: Attached scsi generic sg3 type 0
[  167.470490] sd 4:0:0:1: Attached scsi generic sg4 type 0
[  167.471824] sd 4:0:0:2: Attached scsi generic sg5 type 0
[  167.473859] sd 4:0:0:3: Attached scsi generic sg6 type 0
[  167.503686] sd 4:0:0:0: [sdc] Attached SCSI removable disk
[  167.533228] sd 4:0:0:1: [sdd] Attached SCSI removable disk
[  167.544180] sd 4:0:0:2: [sde] Attached SCSI removable disk
[  167.758170] sd 4:0:0:3: [sdf] Attached SCSI removable disk
[  354.816310] lo: Disabled Privacy Extensions
[10350.629198] usb 1-8: USB disconnect, address 8
[10350.629495] rndis_host 1-8:1.0: usb0: unregister 'rndis_host' usb-0000:00:0b.1-8, RNDIS device
[69163.308035] usb 1-8: new high speed USB device using ehci_hcd and address 9
[69163.465521] scsi5 : usb-storage 1-8:1.0
[69164.471219] scsi 5:0:0:0: Direct-Access     HTC      Android Phone    0100 PQ: 0 ANSI: 2
[69164.475159] sd 5:0:0:0: Attached scsi generic sg7 type 0
[69164.492490] sd 5:0:0:0: [sdg] Attached SCSI removable disk
[69169.259511] sd 5:0:0:0: [sdg] 15544320 512-byte logical blocks: (7.95 GB/7.41 GiB)
[69169.261751] sd 5:0:0:0: [sdg] Assuming drive cache: write through
[69169.267751] sd 5:0:0:0: [sdg] Assuming drive cache: write through
[69169.267766]  sdg: sdg1
[69229.762908] usb 1-8: USB disconnect, address 9
[69230.252042] usb 1-8: new high speed USB device using ehci_hcd and address 10
[69230.421184] rndis_host 1-8:1.0: usb0: register 'rndis_host' at usb-0000:00:0b.1-8, RNDIS device, 72:b6:12:a2:7d:57
[69241.456028] usb0: no IPv6 routers present
[69432.045980] lo: Disabled Privacy Extensions
kenneth@kenneth-basment:~$ cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
ath9k_htc
ath9k_htc

I've highlighted some things that jump out at me, not sure if i understand any of it though?
thanks again

---

### Post by vagrale13 on 2010-11-15
[B]@[rileyedward]("http://ubuntuforums.org/member.php?u=1142663")
[/B]Open terminal and run
```
sudo gedit /etc/modules
```remove one line with **ath9k_htc**
save it and exit

Then, remove **ath9k_htc-installer** from *synaptic*
download *.deb* package for **Ubuntu Maverick 10.10** and install it [http://ubuntuforums.org/showthread.php?t=1564278](http://ubuntuforums.org/showthread.php?t=1564278)
and run again [B]ath9k_htc-installer.
[/B]Reboot and see if it works!

If problem does exist**, **open terminal, and post the output of 4 commands
```
uname -a
lsmod | grep ath9k
ls -l /lib/firmware/ar*
dmesg | grep usb
```

---

### Post by rileyedward on 2010-11-15
The above is the output currently of the 4 commands you have listed, I'll try the .deb and let you know 
many thanks,

---

### Post by rileyedward on 2010-11-15
This is new, i did download the new .deb for 10.10 and it was working until i did the last couple update from the update manager.  then as stated before, i started having issues. I did not get this error last time i installed, but i also did'nt remove the line " ath9k_htc " before.

[COLOR="Red"]"There seems to be a programming error in aptdaemon, the software that allows you to install/remove software and to perform other package management related tasks. Please report this error at [http://launchpad.net/aptdaemon/+filebug](http://launchpad.net/aptdaemon/+filebug) and retry."[/COLOR]

---

### Post by rileyedward on 2010-11-15
kenneth@kenneth-basment:~$ ls -l /lib/firmware/ar*
-rw-r--r-- 1 root root 83968 2010-08-16 15:02 /lib/firmware/ar9170-1.fw
-rw-r--r-- 1 root root  3508 2010-08-16 15:02 /lib/firmware/ar9170-2.fw
-rw-r--r-- 1 root root 15960 2010-08-16 15:02 /lib/firmware/ar9170.fw
-rw-r--r-- 1 root root 51280 2010-08-16 15:02 /lib/firmware/ar9271.fw



kenneth@kenneth-basment:~$ dmesg | grep usb
[    0.206342] usbcore: registered new interface driver usbfs
[    0.206355] usbcore: registered new interface driver hub
[    0.206381] usbcore: registered new device driver usb
[    0.739614] usb 1-2: new high speed USB device using ehci_hcd and address 2
[   15.848078] usb 1-2: device descriptor read/64, error -110
[   16.287437] usbcore: registered new interface driver ath9k_hif_usb
[   31.068053] usb 1-2: device descriptor read/64, error -110
[   31.284029] usb 1-2: new high speed USB device using ehci_hcd and address 3
[   46.396037] usb 1-2: device descriptor read/64, error -110
[   61.612042] usb 1-2: device descriptor read/64, error -110
[   61.828045] usb 1-2: new high speed USB device using ehci_hcd and address 4
[   72.236026] usb 1-2: device not accepting address 4, error -110
[   72.348031] usb 1-2: new high speed USB device using ehci_hcd and address 5
[   82.756046] usb 1-2: device not accepting address 5, error -110
[   83.060260] usb 1-8: new high speed USB device using ehci_hcd and address 8
[   83.370755] usbcore: registered new interface driver cdc_ether
[   83.403535] rndis_host 1-8:1.0: usb0: register 'rndis_host' at usb-0000:00:0b.1-8, RNDIS device, 72:b6:12:a2:7d:57
[   83.403563] usbcore: registered new interface driver rndis_host
[   83.512059] usb 2-2: new full speed USB device using ohci_hcd and address 2
[   93.792024] usb0: no IPv6 routers present
[   98.688039] usb 2-2: device descriptor read/64, error -110
[  113.968049] usb 2-2: device descriptor read/64, error -110
[  114.248038] usb 2-2: new full speed USB device using ohci_hcd and address 3
[  129.424028] usb 2-2: device descriptor read/64, error -110
[  144.704041] usb 2-2: device descriptor read/64, error -110
[  144.984082] usb 2-2: new full speed USB device using ohci_hcd and address 4
[  155.392032] usb 2-2: device not accepting address 4, error -110
[  155.568090] usb 2-2: new full speed USB device using ohci_hcd and address 5
[  165.976034] usb 2-2: device not accepting address 5, error -110
[  166.152046] usb 2-4: new full speed USB device using ohci_hcd and address 6
[  166.432281] scsi4 : usb-storage 2-4:1.0
[  166.432581] usbcore: registered new interface driver usb-storage
[  166.676038] usb 2-7: new low speed USB device using ohci_hcd and address 7
[  166.973662] usbcore: registered new interface driver hiddev
[  166.977171] usbcore: registered new interface driver usbhid
[  166.977179] usbhid: USB HID core driver
[  167.008282] input: Microsoft Microsoft Wireless Optical Desktop® 2.10 as /devices/pci0000:00/0000:00:0b.0/usb2/2-7/2-7:1.0/input/input3
[  167.010621] microsoft 0003:045E:009D.0001: input,hidraw0: USB HID v1.11 Keyboard [Microsoft Microsoft Wireless Optical Desktop® 2.10] on usb-0000:00:0b.0-7/input0
[  167.052637] input: Microsoft Microsoft Wireless Optical Desktop® 2.10 as /devices/pci0000:00/0000:00:0b.0/usb2/2-7/2-7:1.1/input/input4
[  167.053147] microsoft 0003:045E:009D.0002: input,hidraw1: USB HID v1.11 Mouse [Microsoft Microsoft Wireless Optical Desktop® 2.10] on usb-0000:00:0b.0-7/input1
[10350.629198] usb 1-8: USB disconnect, address 8
[10350.629495] rndis_host 1-8:1.0: usb0: unregister 'rndis_host' usb-0000:00:0b.1-8, RNDIS device
[69163.308035] usb 1-8: new high speed USB device using ehci_hcd and address 9
[69163.465521] scsi5 : usb-storage 1-8:1.0
[69229.762908] usb 1-8: USB disconnect, address 9
[69230.252042] usb 1-8: new high speed USB device using ehci_hcd and address 10
[69230.421184] rndis_host 1-8:1.0: usb0: register 'rndis_host' at usb-0000:00:0b.1-8, RNDIS device, 72:b6:12:a2:7d:57
[69241.456028] usb0: no IPv6 routers present
[73002.647326] usb 1-8: USB disconnect, address 10
[73002.648490] rndis_host 1-8:1.0: usb0: unregister 'rndis_host' usb-0000:00:0b.1-8, RNDIS device
[108159.164052] usb 1-8: new high speed USB device using ehci_hcd and address 11
[108159.321137] scsi6 : usb-storage 1-8:1.0
[108174.513460] usb 1-8: USB disconnect, address 11
[108175.008082] usb 1-8: new high speed USB device using ehci_hcd and address 12
[108175.177513] rndis_host 1-8:1.0: usb0: register 'rndis_host' at usb-0000:00:0b.1-8, RNDIS device, 72:b6:12:a2:7d:57
[108185.448025] usb0: no IPv6 routers present

---

### Post by rileyedward on 2010-11-15
kenneth@kenneth-basment:~$ lsmod | grep ath9k
ath9k_htc              42935  0 
mac80211              239388  1 ath9k_htc
led_class               2633  1 ath9k_htc
ath9k_common            2563  1 ath9k_htc
ath9k_hw              285208  2 ath9k_htc,ath9k_common
ath                    13033  2 ath9k_htc,ath9k_hw
cfg80211              139875  3 ath9k_htc,mac80211,ath

---

### Post by rileyedward on 2010-11-15
kenneth@kenneth-basment:~$ uname -a
Linux kenneth-basment 2.6.35-23-generic #37-Ubuntu SMP Fri Nov 5 19:17:11 UTC 2010 i686 GNU/Linux

---

### Post by vagrale13 on 2010-11-16
*Reboot* and select to continued with older kernel, e.g. 
**Ubuntu, with Linux 2.6.35-14-generic**

older than *2.6.35-23-generic *
and see if it  works your usb wireless again!

[IMG]http://img228.imageshack.us/img228/2343/screenshotev.png[/IMG]

---

### Post by owlcroft on 2010-11-22
If I may break into this discussion, I , too, am having some problems with a WNA1100 and hope I can get some help here.

I have downloaded and installed the **.deb** package for the Atheros driver, and run the install, and every indication is that it worked satisfactorily--except that I have zero connectivity.

The Hardware Drivers window (under System) tells me that an "**Atheros driver 801.11n HTC based wireless devices**" driver is both **Enabled** and **In Use**.  Using *lsusb* shows the correct **NetGear, Inc.** entry of **0846:9030**.  An *lsmod | grep ath9k* gives:
```

ath9k_htc               62980
mac80211               299920
ath9k_common             8960
led_class                7176
ath                     13440
cfg80211               188488
compat-firmware-class   14592
usbcore                170288
```

Just to be sure, I also tried (after rebooting a couple of times to no avail) *sudo modprobe ath9k_htc*, also with no results.  Using *cat /etc/modules* includes a single instance of **ath9k_htc** in the results list.  but using *iwconfig* shows **no wireless extensions**, and *sudo iwlist scan* gives a cannot be scanned result.

In short, it all looks good except that there is no connection.  Clicking on the Network Settings shows no wireless entry.  Nor is there any light at all from the physical device.

The Ubuntu is 8.04; I'd like to upgrade that, but have gotten into Driver Hell with the nVidia video card proprietary driver, and am struggling with how to uninstall it and install a non-proprietary driver, and cannot upgrade till I do because else I have nothing but bare minimal 480x600 video.  (Also, right now I have no internet connection at all for that computer till either I get this driver fixed or our local ISP restores our windstorm-interrupted service, which may be many days yet.)

Any thoughts on what could be wrong and how it might be fixed?

LATER ADD: I think I have now identified the problem.  Using *dmsg | grep ath* shows that the driver activation is failing with **Error -22**, and a separate message is more exact, showing that it is unable to find the firmware file, **ar9271.fw**--even though a copy is correctly located in **/lib/firmware** plus a duplicate in **/lib/firmware/[kernelfolder]**.  This problem seems, from Googling, to be a well-known one, but it is unclear to me if there is any known solution; it is apparently a race condition of some sort, so the driver will work on some systems and "mysteriously" fail on others.  It may be that newer versions of the kernel, the driver, both or either, fix the problem, but what I've read so far is too technical for my level for me to be sure.  Still looking for help.

---

### Post by vagrale13 on 2010-11-26
**@owlcroft**
I think *ath9k_htc* doesn' t work in **Ubuntu 8.04**, because uses old kernel!

A test you can do, is to install newer kernel! I try it to *virtualbox* and i had no problems!
 First you must download from somewhere the following the packages 
 **1)** **wireless-crda_1.12_i386.deb** from here [http://repos.um.ac.ir/ubuntu/pool/main/w/wireless-crda/](http://repos.um.ac.ir/ubuntu/pool/main/w/wireless-crda/)

**2)** Download the *kernel 2.6.32XXX* from here [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.32/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.32/")

you need the 3 packages 
*a)* **linux-headers-2.6.32-020632-generic_2.6.32-020632_XXXX.deb**
*b)* **linux-image-2.6.32-020632-generic_2.6.32-020632_XXXX.deb**
*c)* **linux-headers-2.6.32-020632_2.6.32-020632_all.deb**
where **XXXX** is *i386* for **32bit **or* amd64* for **64bit **
accordingly what version you have.

Install first **wireless-crda** deb with double-click, 
then put *3 .deb* packages of kernel to your home folder,
and run 
```
sudo dpkg -i *.deb
```reboot and after install and run [ath9k_htc-installer_1-0_all.deb]("http://sourceforge.net/projects/ath9k-htc/files/ath9k_htc-installer/ath9k_htc-installer_1-0_all.deb/download")

then reboot again, and see if it works! 

All that i tested with *Virtualbox*, and i' m not sure if it works!

If you have error somewhere, don' t reboot, 
post your problem first, and wait to answer you someone if the problem is big!:popcorn:
[IMG]http://img404.imageshack.us/img404/3874/screenshotbke.png[/IMG]

---

### Post by stergios1 on 2010-12-06
[vagrale13]("http://ubuntuforums.org/member.php?u=952139") patrioth, i install compact-wireless drivers exo tp-link wn722wn ath9k_htc
trexo backtrack 4 meso virtualbox

after make, make install, make unload, modprobe ath9k_htc
no wireless adapter found
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.
after i did  modprobe -r ath9k_htc and then modprobe -v ath9k_htc i take this:

insmod /lib/modules/2.6.35.8/kernel/drivers/leds/led-class.ko
insmod /lib/modules/2.6.35.8/updates/compat/compat.ko
insmod /lib/modules/2.6.35.8/kernel/net/rfkill/rfkill.ko
insmod /lib/modules/2.6.35.8/updates/net/wireless/cfg80211.ko
insmod /lib/modules/2.6.35.8/updates/drivers/net/wireless/ath/ath.ko
insmod /lib/modules/2.6.35.8/updates/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
insmod /lib/modules/2.6.35.8/updates/drivers/net/wireless/ath/ath9k/ath9k_common.ko
insmod /lib/modules/2.6.35.8/updates/net/mac80211/mac80211.ko
insmod /lib/modules/2.6.35.8/updates/drivers/net/wireless/ath/ath9k/ath9k_htc.ko

I can't find my wireless card when i type iwconfig can you help me please?

---

### Post by owlcroft on 2010-12-09
Sorry for the delay in responding.

The 8.04 may or may not be the problem.  But we have, at least for now, abandoned the install attempt, as the intended use of the wireless connection--to pick up Sprint wireless briadband--turned out to be of no real point (we are in a very rural area, and Sprint's coverage here is too weak to be reliably useful).  Thanks to everybody for trying.  I just wish now we hadn't spent the money on the hardware. . . .

---

### Post by mculbertson on 2010-12-27
Vagrale13,

Thanks for this it works perfectly for me on KDE and Ubuntu installs. :D

---

### Post by snoopy-2009 on 2011-03-08
wow.. so apparently my girlfriends laptop has a newly formed spontanious-reboot trick, which is quickly growing old to me. this is the third time ive typed a post such as this (in the last 15 mins), this time im playing it smart, and typing it out in gedit (on MY no-net machine, as of this time), and will copy it over when im safely done typing and is saved..lol.. that really ticked me off the 2nd time, because it was more elaborate than the first.. of course, and as is this one. :) (anyway, i did a quick ubuntu install earlier today, just to get her laptop up and running for internet purposes to research this issue, without having to boot back and forth from the windows partion on MY primary pc.) this turned out to be an overheating problem.

i feel as ive done as much research as i can on the ath9k_htc (htc being the usb driver, as im told by the linuxwireless people). and ive read this thread all the way through numerous times in the last week, in attempt to get my WNA1100 working on linux. im new to linux, as in the last week; i started with slackware, failed, replaced it with backtrack4r2, also a fail, but in that research, i noticed seeing the posts searching through google, mentioning somthing along the lines of "[SOLVED] Ath9k_htc Installer and Ubuntu 10.10" and also saw your reccomendation to someone else to use ubuntu 10.10. which brought me here. i see other people getting my exact usb adapter to work on their linux, and im not understanding why it wont on mine.

i hope i didnt leave out any other information youve requested from other posters prior to this, this is my attempt to make your life just a LITTLE less difficult, by not leaving an uninformitive post saying such things as "I CANT GET MY WNA1100 TO WORK! FIX IT FOR MEEE!!" lol.. so i wrote down all the cmd outputs youve asked for, and here they are. the only thing im aware is missing, is the top half of the output of the 'Dmesg" cmd, as it was much too long, and wouldnt let me scroll up far enough (this is where i left a super mario bros gag, in the 2nd attempt to post this.. for some comic relif; about not being able to scroll backwards.. sad chuckle.. not so funny this time around..)

anyway, heres what i got.. 

```
root@SNooPY-Ubuntu:/home/snoopy# lsusb
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c52e Logitech, Inc. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 090c:1000 Feiya Technology Corp. Flash Drive
Bus 001 Device 002: ID 0846:9030 NetGear, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
root@SNooPY-Ubuntu:/home/snoopy# uname -r
2.6.35-22-generic
root@SNooPY-Ubuntu:/home/snoopy# lsmod | grep ath9k
ath9k_htc              46587  0 
ath9k_common            6874  1 ath9k_htc
ath9k_hw              314699  2 ath9k_htc,ath9k_common
mac80211              266657  2 ath9k_htc,ath9k_common
led_class               3393  1 ath9k_htc
ath                    10413  2 ath9k_htc,ath9k_hw
cfg80211              170293  4 ath9k_htc,ath9k_common,mac80211,ath
root@SNooPY-Ubuntu:/home/snoopy# cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
rtc
ath9k_htc
root@SNooPY-Ubuntu:/home/snoopy# ls -l /lib/firmware/ar*
-rw-r--r-- 1 root root 70608 2010-08-29 20:12 /lib/firmware/ar7010.fw
-rw-r--r-- 1 root root 83968 2010-08-16 15:02 /lib/firmware/ar9170-1.fw
-rw-r--r-- 1 root root  3508 2010-08-16 15:02 /lib/firmware/ar9170-2.fw
-rw-r--r-- 1 root root 15960 2010-08-16 15:02 /lib/firmware/ar9170.fw
-rw-r--r-- 1 root root 51280 2010-08-16 15:02 /lib/firmware/ar9271.fw
root@SNooPY-Ubuntu:/home/snoopy# 

```

and this is the dmesg output mentioned, being cut off at the head.
```
[    0.350737] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.350846] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0PC._PRT]
[    0.350972] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE2._PRT]
[    0.351040] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCE6._PRT]
[    0.368322] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.368428] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.368531] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.368633] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.368743] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.368845] ACPI: PCI Interrupt Link [LNKF] (IRQs 9) *0, disabled.
[    0.368943] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.369049] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.369087] HEST: Table is not found!
[    0.369193] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.369197] vgaarb: loaded
[    0.369367] SCSI subsystem initialized
[    0.380212] libata version 3.00 loaded.
[    0.380212] usbcore: registered new interface driver usbfs
[    0.380212] usbcore: registered new interface driver hub
[    0.380216] usbcore: registered new device driver usb
[    0.380289] ACPI: WMI: Mapper loaded
[    0.380291] PCI: Using ACPI for IRQ routing
[    0.380294] PCI: pci_cache_line_size set to 64 bytes
[    0.380624] reserve RAM buffer: 000000000009fc00 - 000000000009ffff 
[    0.380627] reserve RAM buffer: 000000005ffd0000 - 000000005fffffff 
[    0.380761] NetLabel: Initializing
[    0.380762] NetLabel:  domain hash size = 128
[    0.380764] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.380780] NetLabel:  unlabeled traffic allowed by default
[    0.380819] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.380825] hpet0: 4 comparators, 32-bit 14.318180 MHz counter
[    0.382866] Switching to clocksource hpet
[    0.392043] AppArmor: AppArmor Filesystem Enabled
[    0.392068] pnp: PnP ACPI init
[    0.392095] ACPI: bus type pnp registered
[    0.395727] pnp 00:0a: disabling [mem 0xfebff000-0xfebff7ff] because it overlaps 0000:00:14.4 BAR 14 [mem 0xfeb00000-0xfebfffff]
[    0.397174] pnp: PnP ACPI: found 17 devices
[    0.397176] ACPI: ACPI bus type pnp unregistered
[    0.397191] system 00:09: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.397194] system 00:09: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.397201] system 00:0a: [io  0x04d0-0x04d1] has been reserved
[    0.397204] system 00:0a: [io  0x040b] has been reserved
[    0.397206] system 00:0a: [io  0x04d6] has been reserved
[    0.397209] system 00:0a: [io  0x0c00-0x0c01] has been reserved
[    0.397212] system 00:0a: [io  0x0c14] has been reserved
[    0.397214] system 00:0a: [io  0x0c50-0x0c51] has been reserved
[    0.397217] system 00:0a: [io  0x0c52] has been reserved
[    0.397219] system 00:0a: [io  0x0c6c] has been reserved
[    0.397222] system 00:0a: [io  0x0c6f] has been reserved
[    0.397224] system 00:0a: [io  0x0cd0-0x0cd1] has been reserved
[    0.397227] system 00:0a: [io  0x0cd2-0x0cd3] has been reserved
[    0.397230] system 00:0a: [io  0x0cd4-0x0cd5] has been reserved
[    0.397233] system 00:0a: [io  0x0cd6-0x0cd7] has been reserved
[    0.397235] system 00:0a: [io  0x0cd8-0x0cdf] has been reserved
[    0.397238] system 00:0a: [io  0x0800-0x089f] has been reserved
[    0.397241] system 00:0a: [io  0x0b10-0x0b1f] has been reserved
[    0.397244] system 00:0a: [io  0x0900-0x090f] has been reserved
[    0.397246] system 00:0a: [io  0x0910-0x091f] has been reserved
[    0.397249] system 00:0a: [io  0xfe00-0xfefe] has been reserved
[    0.397253] system 00:0a: [mem 0xffb80000-0xffbfffff] has been reserved
[    0.397256] system 00:0a: [mem 0xfed00000-0xfed003ff] has been reserved
[    0.397259] system 00:0a: [mem 0xffeff000-0xffeff7ff] has been reserved
[    0.397262] system 00:0a: [mem 0xfff80000-0xffffffff] has been reserved
[    0.397267] system 00:0d: [io  0x0a00-0x0a0f] has been reserved
[    0.397270] system 00:0d: [io  0x0a10-0x0a1f] has been reserved
[    0.397275] system 00:0e: [mem 0xe0000000-0xefffffff] has been reserved
[    0.397280] system 00:0f: [mem 0xf0000000-0xf08fffff] has been reserved
[    0.397286] system 00:10: [mem 0x00000000-0x0009ffff] could not be reserved
[    0.397288] system 00:10: [mem 0x000c0000-0x000cffff] has been reserved
[    0.397291] system 00:10: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.397294] system 00:10: [mem 0x00100000-0x5fffffff] could not be reserved
[    0.403374] pci 0000:00:02.0: PCI bridge to [bus 01-01]
[    0.403378] pci 0000:00:02.0:   bridge window [io  0xc000-0xcfff]
[    0.403382] pci 0000:00:02.0:   bridge window [mem 0xfe900000-0xfe9fffff]
[    0.403387] pci 0000:00:02.0:   bridge window [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.403392] pci 0000:00:06.0: PCI bridge to [bus 02-02]
[    0.403394] pci 0000:00:06.0:   bridge window [io  0xd000-0xdfff]
[    0.403398] pci 0000:00:06.0:   bridge window [mem 0xfea00000-0xfeafffff]
[    0.403402] pci 0000:00:06.0:   bridge window [mem pref disabled]
[    0.403407] pci 0000:00:14.4: PCI bridge to [bus 03-03]
[    0.403410] pci 0000:00:14.4:   bridge window [io  0xe000-0xefff]
[    0.403416] pci 0000:00:14.4:   bridge window [mem 0xfeb00000-0xfebfffff]
[    0.403421] pci 0000:00:14.4:   bridge window [mem pref disabled]
[    0.403439] pci 0000:00:02.0: setting latency timer to 64
[    0.403446] pci 0000:00:06.0: setting latency timer to 64
[    0.403456] pci_bus 0000:00: resource 4 [io  0x0000-0xffff]
[    0.403458] pci_bus 0000:00: resource 5 [mem 0x60000000-0xfcffffffff]
[    0.403461] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.403463] pci_bus 0000:01: resource 0 [io  0xc000-0xcfff]
[    0.403466] pci_bus 0000:01: resource 1 [mem 0xfe900000-0xfe9fffff]
[    0.403468] pci_bus 0000:01: resource 2 [mem 0xd0000000-0xdfffffff 64bit pref]
[    0.403471] pci_bus 0000:02: resource 0 [io  0xd000-0xdfff]
[    0.403473] pci_bus 0000:02: resource 1 [mem 0xfea00000-0xfeafffff]
[    0.403476] pci_bus 0000:03: resource 0 [io  0xe000-0xefff]
[    0.403478] pci_bus 0000:03: resource 1 [mem 0xfeb00000-0xfebfffff]
[    0.403481] pci_bus 0000:03: resource 4 [io  0x0000-0xffff]
[    0.403483] pci_bus 0000:03: resource 5 [mem 0x60000000-0xfcffffffff]
[    0.403486] pci_bus 0000:03: resource 6 [mem 0x000a0000-0x000bffff]
[    0.403534] NET: Registered protocol family 2
[    0.403673] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
[    0.404789] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[    0.409098] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.410131] TCP: Hash tables configured (established 262144 bind 65536)
[    0.410135] TCP reno registered
[    0.410148] UDP hash table entries: 1024 (order: 3, 32768 bytes)
[    0.410197] UDP-Lite hash table entries: 1024 (order: 3, 32768 bytes)
[    0.410364] NET: Registered protocol family 1
[    0.562565] pci 0000:01:00.0: Boot video device
[    0.562579] PCI: CLS 64 bytes, default 64
[    0.585936] Scanning for low memory corruption every 60 seconds
[    0.586090] audit: initializing netlink socket (disabled)
[    0.586107] type=2000 audit(1299541866.580:1): initialized
[    0.610369] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.611768] VFS: Disk quotas dquot_6.5.2
[    0.611820] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.612421] fuse init (API version 7.14)
[    0.612506] msgmni has been set to 2968
[    0.612970] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.612974] io scheduler noop registered
[    0.612976] io scheduler deadline registered
[    0.613012] io scheduler cfq registered (default)
[    0.613187] pcieport 0000:00:02.0: setting latency timer to 64
[    0.613219]   alloc irq_desc for 40 on node 0
[    0.613221]   alloc kstat_irqs on node 0
[    0.613233] pcieport 0000:00:02.0: irq 40 for MSI/MSI-X
[    0.613336] pcieport 0000:00:06.0: setting latency timer to 64
[    0.613362]   alloc irq_desc for 41 on node 0
[    0.613363]   alloc kstat_irqs on node 0
[    0.613369] pcieport 0000:00:06.0: irq 41 for MSI/MSI-X
[    0.613463] aer 0000:00:02.0:pcie02: AER service couldn't init device: no _OSC support
[    0.613471] aer 0000:00:06.0:pcie02: AER service couldn't init device: no _OSC support
[    0.613488] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.613509] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.613727] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.613742] ACPI: Power Button [PWRB]
[    0.613794] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.613797] ACPI: Power Button [PWRF]
[    0.614071] ACPI: acpi_idle registered with cpuidle
[    0.614097] ACPI: duty_cycle spans bit 4
[    0.617604] ERST: Table is not found!
[    0.617829] Linux agpgart interface v0.103
[    0.617836] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.617980] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.618301] 00:05: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.619487] brd: module loaded
[    0.619984] loop: module loaded
[    0.620354]   alloc irq_desc for 16 on node 0
[    0.620356]   alloc kstat_irqs on node 0
[    0.620366] pata_acpi 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.620415] pata_acpi 0000:00:14.1: setting latency timer to 64
[    0.620756] Fixed MDIO Bus: probed
[    0.620790] PPP generic driver version 2.4.2
[    0.620825] tun: Universal TUN/TAP device driver, 1.6
[    0.620826] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.620895] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.620941]   alloc irq_desc for 19 on node 0
[    0.620942]   alloc kstat_irqs on node 0
[    0.620946] ehci_hcd 0000:00:13.5: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.620968] ehci_hcd 0000:00:13.5: EHCI Host Controller
[    0.621034] ehci_hcd 0000:00:13.5: new USB bus registered, assigned bus number 1
[    0.621068] ehci_hcd 0000:00:13.5: applying AMD SB600/SB700 USB freeze workaround
[    0.621085] ehci_hcd 0000:00:13.5: debug port 1
[    0.621113] ehci_hcd 0000:00:13.5: irq 19, io mem 0xfe8ff000
[    0.640021] ehci_hcd 0000:00:13.5: USB 2.0 started, EHCI 1.00
[    0.640139] hub 1-0:1.0: USB hub found
[    0.640144] hub 1-0:1.0: 10 ports detected
[    0.640243] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.640285] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.640296] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    0.640326] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 2
[    0.640353] ohci_hcd 0000:00:13.0: irq 16, io mem 0xfe8fe000
[    0.704111] hub 2-0:1.0: USB hub found
[    0.704118] hub 2-0:1.0: 2 ports detected
[    0.704203]   alloc irq_desc for 17 on node 0
[    0.704205]   alloc kstat_irqs on node 0
[    0.704209] ohci_hcd 0000:00:13.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.704220] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    0.704252] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 3
[    0.704275] ohci_hcd 0000:00:13.1: irq 17, io mem 0xfe8fd000
[    0.741059] Freeing initrd memory: 16276k freed
[    0.764118] hub 3-0:1.0: USB hub found
[    0.764125] hub 3-0:1.0: 2 ports detected
[    0.764262]   alloc irq_desc for 18 on node 0
[    0.764263]   alloc kstat_irqs on node 0
[    0.764267] ohci_hcd 0000:00:13.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.764278] ohci_hcd 0000:00:13.2: OHCI Host Controller
[    0.764317] ohci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 4
[    0.764342] ohci_hcd 0000:00:13.2: irq 18, io mem 0xfe8fc000
[    0.824106] hub 4-0:1.0: USB hub found
[    0.824113] hub 4-0:1.0: 2 ports detected
[    0.824231] ohci_hcd 0000:00:13.3: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.824242] ohci_hcd 0000:00:13.3: OHCI Host Controller
[    0.824285] ohci_hcd 0000:00:13.3: new USB bus registered, assigned bus number 5
[    0.824304] ohci_hcd 0000:00:13.3: irq 17, io mem 0xfe8fb000
[    0.884107] hub 5-0:1.0: USB hub found
[    0.884113] hub 5-0:1.0: 2 ports detected
[    0.884221] ohci_hcd 0000:00:13.4: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.884232] ohci_hcd 0000:00:13.4: OHCI Host Controller
[    0.884265] ohci_hcd 0000:00:13.4: new USB bus registered, assigned bus number 6
[    0.884283] ohci_hcd 0000:00:13.4: irq 18, io mem 0xfe8fa000
[    0.944105] hub 6-0:1.0: USB hub found
[    0.944112] hub 6-0:1.0: 2 ports detected
[    0.944207] uhci_hcd: USB Universal Host Controller Interface driver
[    0.944367] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    0.947439] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.947446] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.947566] mice: PS/2 mouse device common for all mice
[    0.947676] rtc_cmos 00:02: RTC can wake from S4
[    0.947721] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    0.947752] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    0.947845] device-mapper: uevent: version 1.0.3
[    0.947972] device-mapper: ioctl: 4.17.0-ioctl (2010-03-05) initialised: dm-devel@redhat.com
[    0.948131] device-mapper: multipath: version 1.1.1 loaded
[    0.948135] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.948434] cpuidle: using governor ladder
[    0.948436] cpuidle: using governor menu
[    0.948716] TCP cubic registered
[    0.948839] NET: Registered protocol family 10
[    0.949278] lo: Disabled Privacy Extensions
[    0.949514] NET: Registered protocol family 17
[    0.949552] powernow-k8: Found 1 AMD Athlon(tm) 64 X2 Dual Core Processor 5600+ (2 cpu cores) (version 2.20.00)
[    0.949565] [Firmware Bug]: powernow-k8: No compatible ACPI _PSS objects found.
[    0.949566] [Firmware Bug]: powernow-k8: Try again with latest BIOS.
[    0.949657] PM: Resume from disk failed.
[    0.949672] registered taskstats version 1
[    0.950816]   Magic number: 3:287:908
[    0.950876] mem port: hash matches
[    0.950953] rtc_cmos 00:02: setting system clock to 2011-03-07 23:51:07 UTC (1299541867)
[    0.950956] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.950957] EDD information not available.
[    0.951038] Freeing unused kernel memory: 908k freed
[    0.951574] Write protecting the kernel read-only data: 10240k
[    0.951734] Freeing unused kernel memory: 416k freed
[    0.952182] Freeing unused kernel memory: 1644k freed
[    0.962550] usb 1-1: new high speed USB device using ehci_hcd and address 2
[    0.973539] udev[109]: starting version 163
[    1.124615] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.124652] r8169 0000:02:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.124716] r8169 0000:02:00.0: setting latency timer to 64
[    1.124781]   alloc irq_desc for 42 on node 0
[    1.124783]   alloc kstat_irqs on node 0
[    1.124802] r8169 0000:02:00.0: irq 42 for MSI/MSI-X
[    1.125452] r8169 0000:02:00.0: eth0: RTL8168b/8111b at 0xffffc9000037e000, 00:19:db:69:96:56, XID 18000000 IRQ 42
[    1.126377] [drm] Initialized drm 1.1.0 20060810
[    1.128480] scsi0 : pata_atiixp
[    1.130941] Floppy drive(s): fd0 is 1.44M
[    1.131015] scsi1 : pata_atiixp
[    1.132396] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xff00 irq 14
[    1.132399] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xff08 irq 15
[    1.132739] ahci 0000:00:12.0: version 3.0
[    1.132758]   alloc irq_desc for 22 on node 0
[    1.132760]   alloc kstat_irqs on node 0
[    1.132768] ahci 0000:00:12.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    1.132811] ahci 0000:00:12.0: controller can't do 64bit DMA, forcing 32bit
[    1.132932] ahci 0000:00:12.0: AHCI 0001.0100 32 slots 4 ports 3 Gbps 0xf impl SATA mode
[    1.132936] ahci 0000:00:12.0: flags: ncq sntf ilck led clo pmp pio ccc 
[    1.133440] scsi2 : ahci
[    1.133540] scsi3 : ahci
[    1.133611] scsi4 : ahci
[    1.133681] scsi5 : ahci
[    1.133818] ata3: SATA max UDMA/133 abar m1024@0xfe8ff800 port 0xfe8ff900 irq 22
[    1.133822] ata4: SATA max UDMA/133 abar m1024@0xfe8ff800 port 0xfe8ff980 irq 22
[    1.133826] ata5: SATA max UDMA/133 abar m1024@0xfe8ff800 port 0xfe8ffa00 irq 22
[    1.133830] ata6: SATA max UDMA/133 abar m1024@0xfe8ff800 port 0xfe8ffa80 irq 22
[    1.153976] FDC 0 is a post-1991 82077
[    1.250028] usb 1-3: new high speed USB device using ehci_hcd and address 3
[    1.290799] ata1.00: ATAPI: SAMSUNG CDRW/DVD SM-348B, T500, max UDMA/33
[    1.336318] ata1.00: configured for UDMA/33
[    1.337496] scsi 0:0:0:0: CD-ROM            SAMSUNG  CDRW/DVD SM-348B T500 PQ: 0 ANSI: 5
[    1.338352] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[    1.338356] Uniform CD-ROM driver Revision: 3.20
[    1.338483] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    1.338562] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    1.422934] Initializing USB Mass Storage driver...
[    1.423145] scsi6 : usb-storage 1-3:1.0
[    1.423278] usbcore: registered new interface driver usb-storage
[    1.423280] USB Mass Storage support registered.
[    1.482541] ata5: SATA link down (SStatus 0 SControl 300)
[    1.482615] ata4: SATA link down (SStatus 0 SControl 300)
[    1.482626] ata6: SATA link down (SStatus 0 SControl 300)
[    1.660023] ata3: softreset failed (device not ready)
[    1.660027] ata3: applying SB600 PMP SRST workaround and retrying
[    1.840028] usb 3-2: new full speed USB device using ohci_hcd and address 2
[    1.840039] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.841475] ata3.00: ATA-8: ST3500320AS, SD15, max UDMA/133
[    1.841478] ata3.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    1.841496] ata3.00: SB600 AHCI: limiting to 255 sectors per cmd
[    1.843259] ata3.00: SB600 AHCI: limiting to 255 sectors per cmd
[    1.843262] ata3.00: configured for UDMA/133
[    1.843436] scsi 2:0:0:0: Direct-Access     ATA      ST3500320AS      SD15 PQ: 0 ANSI: 5
[    1.843633] sd 2:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    1.843643] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    1.843802] sd 2:0:0:0: [sda] Write Protect is off
[    1.843806] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.843853] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.844156]  sda: sda1 sda2 sda3
[    1.890299] sd 2:0:0:0: [sda] Attached SCSI disk
[    1.926661] [drm] radeon defaulting to kernel modesetting.
[    1.926665] [drm] radeon kernel modesetting enabled.
[    1.927681] radeon 0000:01:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.927689] radeon 0000:01:00.0: setting latency timer to 64
[    1.931650] [drm] initializing kernel modesetting (RV530 0x1002:0x71C1).
[    1.931842] [drm] register mmio base: 0xFE9F0000
[    1.931844] [drm] register mmio size: 65536
[    1.932666] ATOM BIOS: VT
[    1.932715] [drm] Generation 2 PCI interface, using max accessible memory
[    1.932721] radeon 0000:01:00.0: VRAM: 512M 0x00000000 - 0x1FFFFFFF (512M used)
[    1.932724] radeon 0000:01:00.0: GTT: 512M 0x20000000 - 0x3FFFFFFF
[    1.932824]   alloc irq_desc for 43 on node 0
[    1.932827]   alloc kstat_irqs on node 0
[    1.932841] radeon 0000:01:00.0: irq 43 for MSI/MSI-X
[    1.932847] radeon 0000:01:00.0: radeon: using MSI.
[    1.932879] [drm] radeon: irq initialized.
[    1.933481] [drm] Detected VRAM RAM=512M, BAR=256M
[    1.933487] [drm] RAM width 128bits DDR
[    1.933726] [TTM] Zone  kernel: Available graphics memory: 769430 kiB.
[    1.933728] [TTM] Initializing pool allocator.
[    1.933756] [drm] radeon: 512M of VRAM memory ready
[    1.933758] [drm] radeon: 512M of GTT memory ready.
[    1.933790] [drm] GART: num cpu pages 131072, num gpu pages 131072
[    1.936526] [drm] radeon: 1 quad pipes, 2 z pipes initialized.
[    1.938112] [drm] PCIE GART of 512M enabled (table at 0x00040000).
[    1.938199] [drm] Loading R500 Microcode
[    1.941591] [drm] radeon: ring at 0x0000000020000000
[    1.941627] [drm] ring test succeeded in 6 usecs
[    1.941801] [drm] radeon: ib pool ready.
[    1.941914] [drm] ib test succeeded in 0 usecs
[    1.941923] failed to evaluate ATIF got AE_BAD_PARAMETER
[    1.941926] radeon 0000:01:00.0: Error during ACPI methods call
[    1.941961] [drm] Default TV standard: NTSC
[    1.941964] [drm] Default TV standard: NTSC
[    1.942066] [drm] Default TV standard: NTSC
[    1.942133] [drm] Radeon Display Connectors
[    1.942135] [drm] Connector 0:
[    1.942136] [drm]   DVI-I
[    1.942138] [drm]   HPD2
[    1.942140] [drm]   DDC: 0x7e40 0x7e40 0x7e44 0x7e44 0x7e48 0x7e48 0x7e4c 0x7e4c
[    1.942142] [drm]   Encoders:
[    1.942144] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
[    1.942146] [drm]     DFP3: INTERNAL_LVTM1
[    1.942147] [drm] Connector 1:
[    1.942149] [drm]   S-video
[    1.942150] [drm]   Encoders:
[    1.942151] [drm]     TV1: INTERNAL_KLDSCP_DAC2
[    1.942152] [drm] Connector 2:
[    1.942154] [drm]   DVI-I
[    1.942155] [drm]   HPD1
[    1.942157] [drm]   DDC: 0x7e50 0x7e50 0x7e54 0x7e54 0x7e58 0x7e58 0x7e5c 0x7e5c
[    1.942158] [drm]   Encoders:
[    1.942160] [drm]     CRT2: INTERNAL_KLDSCP_DAC2
[    1.942161] [drm]     DFP1: INTERNAL_KLDSCP_TMDS1
[    2.065947] usbcore: registered new interface driver hiddev
[    2.069339] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:13.1/usb3/3-2/3-2:1.0/input/input2
[    2.069456] generic-usb 0003:046D:C52E.0001: input,hidraw0: USB HID v1.11 Keyboard [Logitech USB Receiver] on usb-0000:00:13.1-2/input0
[    2.074715] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:13.1/usb3/3-2/3-2:1.1/input/input3
[    2.074940] generic-usb 0003:046D:C52E.0002: input,hiddev96,hidraw1: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:13.1-2/input1
[    2.074957] usbcore: registered new interface driver usbhid
[    2.074959] usbhid: USB HID core driver
[    2.109475] [drm] fb mappable at 0xD00C0000
[    2.109479] [drm] vram apper at 0xD0000000
[    2.109480] [drm] size 3145728
[    2.109482] [drm] fb depth is 24
[    2.109483] [drm]    pitch is 4096
[    2.151006] Console: switching to colour frame buffer device 128x48
[    2.160090] fb0: radeondrmfb frame buffer device
[    2.160092] drm: registered panic notifier
[    2.160096] Slow work thread pool: Starting up
[    2.160179] Slow work thread pool: Ready
[    2.160186] [drm] Initialized radeon 2.5.0 20080528 for 0000:01:00.0 on minor 0
[    2.257594] blkid[329]: segfault at ffffffff9496d96c ip 00007ff7c21f1898 sp 00007fff1d4446d0 error 4 in libblkid.so.1[7ff7c21e1000+1c000]
[    2.739468] scsi 6:0:0:0: Direct-Access     JetFlash Transcend 4GB    1100 PQ: 0 ANSI: 0 CCS
[    2.740017] sd 6:0:0:0: Attached scsi generic sg2 type 0
[    2.741447] sd 6:0:0:0: [sdb] 7913472 512-byte logical blocks: (4.05 GB/3.77 GiB)
[    2.742311] sd 6:0:0:0: [sdb] Write Protect is off
[    2.742314] sd 6:0:0:0: [sdb] Mode Sense: 43 00 00 00
[    2.742317] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[    2.745053] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[    2.745063]  sdb: sdb1
[    2.748336] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[    2.748344] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[    2.812019] EXT4-fs (sda2): mounted filesystem with ordered data mode. Opts: (null)
[   10.199236] Adding 5253116k swap on /dev/sda3.  Priority:-1 extents:1 across:5253116k 
[   10.224288] udev[455]: starting version 163
[   10.299075] lp: driver loaded but no devices found
[   10.349919] ACPI: resource piix4_smbus [io  0x0b00-0x0b07] conflicts with ACPI region SMOV [irq 2816-2822 64bit disabled]
[   10.349924] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   10.404388] k8temp 0000:00:18.3: Temperature readouts might be wrong - check erratum #141
[   10.461273] EDAC MC: Ver: 2.1.0 Sep 19 2010
[   10.505857] EXT4-fs (sda2): re-mounted. Opts: errors=remount-ro
[   10.514772] EDAC amd64_edac:  Ver: 3.3.0 Sep 19 2010
[   10.515231] cfg80211: Calling CRDA to update world regulatory domain
[   10.541862] EDAC amd64: This node reports that Memory ECC is currently disabled, set F3x44[22] (0000:00:18.3).
[   10.541876] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
[   10.541877]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
[   10.541879]  (Note that use of the override may cause unknown side effects.)
[   10.541919] amd64_edac: probe of 0000:00:18.2 failed with error -22
[   10.614266] parport_pc 00:07: reported by Plug and Play ACPI
[   10.614321] parport0: PC-style at 0x3bc, irq 7 [PCSPP]
[   10.635920] type=1400 audit(1299541877.174:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=753 comm="apparmor_parser"
[   10.636197] type=1400 audit(1299541877.174:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=753 comm="apparmor_parser"
[   10.636351] type=1400 audit(1299541877.174:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=753 comm="apparmor_parser"
[   10.641810] ppdev: user-space parallel port driver
[   10.666316] cfg80211: World regulatory domain updated:
[   10.666322]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   10.666326]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.666328]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   10.666331]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   10.666333]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.666336]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.693915] lp0: using parport0 (interrupt-driven).
[   10.789348] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   10.789416]   alloc irq_desc for 44 on node 0
[   10.789418]   alloc kstat_irqs on node 0
[   10.789435] HDA Intel 0000:00:14.2: irq 44 for MSI/MSI-X
[   10.804844] CA0106 0000:03:00.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   10.804875] snd-ca0106: Model 1012 Rev 00000000 Serial 10121102
[   11.096339] usbcore: registered new interface driver ath9k_hif_usb
[   11.102902] blkid[827]: segfault at ffffffff9495596c ip 00007fb76afa9898 sp 00007fff25c244b0 error 4 in libblkid.so.1.1.0[7fb76af99000+1c000]
[   11.203167] type=1400 audit(1299541877.744:5): apparmor="STATUS" operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" pid=979 comm="apparmor_parser"
[   11.203198] type=1400 audit(1299541877.744:6): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=980 comm="apparmor_parser"
[   11.203471] type=1400 audit(1299541877.744:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=980 comm="apparmor_parser"
[   11.203629] type=1400 audit(1299541877.744:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=980 comm="apparmor_parser"
[   11.207611] type=1400 audit(1299541877.744:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=983 comm="apparmor_parser"
[   11.207956] type=1400 audit(1299541877.744:10): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=983 comm="apparmor_parser"
[   11.332328] r8169 0000:02:00.0: eth0: link down
[   11.332847] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   11.797949] [drm:drm_mode_getfb] *ERROR* invalid framebuffer id
[   12.191400] EXT4-fs (sda2): re-mounted. Opts: errors=remount-ro,commit=0
[   13.750825] EXT4-fs (sda2): re-mounted. Opts: errors=remount-ro,commit=0
[   21.223492] Intel AES-NI instructions are not detected.
[   21.251543] padlock: VIA PadLock not detected.
[   27.079504] UDF-fs: Partition marked readonly; forcing readonly mount
[   27.100896] UDF-fs INFO UDF: Mounting volume 'Repair disc Windows 7 64-bit', timestamp 2010/12/10 14:02 (1ed4)

```

if there is somewhere the dmesg cmd logs its output, or another way for me to get that info for you, if deems important enough, just let me know.


the only other thing i can think of to mention, is since MY system isnt internet ready without this adapter, i am unaware of how to "install my kernel headers" without internet.. i ran the cmd i found elsewhere on my girlfriends laptop, and i did not seem to encounter any errors, but at the same time, have no idea if it worked or not.. but it makes it further than my machine does, mine has no internet to reach any of the downloads.. what im hoping is that you will tell me theres a way to download the headers i need (on alternate system, the internet laptop) and transfer them pre-install via a usb stick, cd-r, external hdd (usb) or such.. 

i hope this didnt seem too long, i just wanted to at least TRY to prevent you from asking unneccesary questions that i should have had the know-how to post in the beginning.

---

### Post by snoopy-2009 on 2011-03-09
okay, so beore you begin attempting to troubleshoot my issues, please disregard. ive stumbled accross Natty 11.04 and the wna1100 DOES include out-o-the-box support, and is even connected to the internet during the new ubuntu installation, and can download all updates on its own and all :)

sorry or wasting any time i may have caused.. even just by causing you to read my entire previous post.. lol.. tyvm anyway :)

---

### Post by ianmga on 2011-06-02
Important! If you follow the installation steps for a clean install of Ubuntu 10.04 and still cannot get da' thing to work check whether the htc_9271.fw file is in /lib/firmware. If it isn't you can... google it I guess, then copy it there. 

Adding the file worked for me. I kicked myself in the nuts for several hours trying to troubleshoot it.

---

### Post by carlomagn0 on 2011-08-22
[SIZE=2]hello, I have the same issue as Mr. Stergios post!

usb WN722N  of TP-LINK.

The installation of ath9k_htc was Ok, but I can not see muy modem!

Have any of you solved this?  I just get into this few days ago.

Thank you in advance.

[/SIZE]
> **stergios1 said:**
> [vagrale13]("http://ubuntuforums.org/member.php?u=952139") patrioth, i install compact-wireless drivers exo tp-link wn722wn ath9k_htc
trexo backtrack 4 meso virtualbox

after make, make install, make unload, modprobe ath9k_htc
no wireless adapter found
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.
after i did  modprobe -r ath9k_htc and then modprobe -v ath9k_htc i take this:

...
I can't find my wireless card when i type iwconfig can you help me please?

---

### Post by carlomagn0 on 2011-08-22
Hello,
IT DIDN'T work for me.
I have Ubuntu 10.04.  

Still have the modem not functioning.

BR

> **ianmga said:**
> Important! If you follow the installation steps for a clean install of Ubuntu 10.04 and still cannot get da' thing to work check whether the htc_9271.fw file is in /lib/firmware. If it isn't you can... google it I guess, then copy it there. 

Adding the file worked for me. I kicked myself in the nuts for several hours trying to troubleshoot it.

---

### Post by vagrale13 on 2011-08-24
[B]@[carlomagn0]("http://ubuntuforums.org/member.php?u=1050404")
[/B]Can you post the output of commands
```
lsusb
iwconfig
dmesg
lsmod | grep ath9k
cat /etc/modules
ls -l /lib/firmware/ar*
```

---

### Post by carlomagn0 on 2011-08-24
> **vagrale13 said:**
> [B]@[carlomagn0]("http://ubuntuforums.org/member.php?u=1050404")
[/B]Can you post the output of commands
```
lsusb
iwconfig
dmesg
lsmod | grep ath9k
cat /etc/modules
ls -l /lib/firmware/ar*
```

Hello,
Here it is.  
Thank you in advance!

```
lsusb
xxx:~/Documentos$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0cf3:9271 Atheros Communications, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


iwconfig
xxx:~/Documentos$ iwconfig
lo        no wireless extensions.
eth0      no wireless extensions.


dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.32-33-generic (buildd@zirconium) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #72-Ubuntu SMP Fri Jul 29 21:08:37 UTC 2011 (Ubuntu 2.6.32-33.72-generic 2.6.32.41+drm33.18)
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
[    0.000000]  BIOS-e820: 0000000000100000 - 000000002bfd0000 (usable)
[    0.000000]  BIOS-e820: 000000002bfd0000 - 000000002bfdf000 (ACPI data)
[    0.000000]  BIOS-e820: 000000002bfdf000 - 000000002c000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000fffc0000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.3 present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0x2bfd0 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask FE0000000 write-back
[    0.000000]   1 base 020000000 mask FF8000000 write-back
[    0.000000]   2 base 028000000 mask FFC000000 write-back
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
[    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000002bfd0000 (usable)
[    0.000000]  modified: 000000002bfd0000 - 000000002bfdf000 (ACPI data)
[    0.000000]  modified: 000000002bfdf000 - 000000002c000000 (ACPI NVS)
[    0.000000]  modified: 00000000fffc0000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-000000002bfd0000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 002bc00000 page 2M
[    0.000000]  002bc00000 - 002bfd0000 page 4k
[    0.000000] kernel direct mapping tables up to 2bfd0000 @ 10000-15000
[    0.000000] RAMDISK: 2087b000 - 2101b26a
[    0.000000] ACPI: RSDP 000f70f0 00014 (v00 ACPIAM)
[    0.000000] ACPI: RSDT 2bfd0000 00030 (v01 A M I  OEMRSDT  02000404 MSFT 00000097)
[    0.000000] ACPI: FACP 2bfd0200 00081 (v02 A M I  OEMFACP  02000404 MSFT 00000097)
[    0.000000] ACPI: DSDT 2bfd03f0 0344B (v01   M963    M963G 00000000 INTL 02002026)
[    0.000000] ACPI: FACS 2bfdf000 00040
[    0.000000] ACPI: APIC 2bfd0390 0005C (v01 A M I  OEMAPIC  02000404 MSFT 00000097)
[    0.000000] ACPI: OEMB 2bfdf040 00040 (v01 A M I  AMI_OEM  02000404 MSFT 00000097)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 703MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 2bfd0000
[    0.000000]   low ram: 0 - 2bfd0000
[    0.000000]   node 0 low ram: 00000000 - 2bfd0000
[    0.000000]   node 0 bootmap 00011000 - 000167fc
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 002bfd0000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008e0ef8]    TEXT DATA BSS ==> [0000100000 - 00008e0ef8]
[    0.000000]   #4 [002087b000 - 002101b26a]          RAMDISK ==> [002087b000 - 002101b26a]
[    0.000000]   #5 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #6 [00008e1000 - 00008e40e1]              BRK ==> [00008e1000 - 00008e40e1]
[    0.000000]   #7 [0000010000 - 0000011000]          PGTABLE ==> [0000010000 - 0000011000]
[    0.000000]   #8 [0000011000 - 0000017000]          BOOTMAP ==> [0000011000 - 0000017000]
[    0.000000] found SMP MP-table at [c00ff780] ff780
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x0002bfd0
[    0.000000]   HighMem  0x0002bfd0 -> 0x0002bfd0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0002bfd0
[    0.000000] On node 0 totalpages: 180063
[    0.000000] free_area_init_node: node 0, pgdat c079a7c0, node_mem_map c1001200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1376 pages used for memmap
[    0.000000]   Normal zone: 174704 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x81] disabled)
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 2 CPUs, 1 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 2c000000 (gap: 2c000000:d3fc0000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @c1800000 s36312 r0 d21032 u2097152
[    0.000000] pcpu-alloc: s36312 r0 d21032 u2097152 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 1 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 178655
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-33-generic root=UUID=bf2e253f-1dc2-4187-aba1-32ef8c0a29bb ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 3603200 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (00000000:00000000)
[    0.000000] Memory: 693908k/720704k available (4675k kernel code, 25996k reserved, 2127k data, 668k init, 0k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xec7d0000 - 0xff7fe000   ( 304 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xebfd0000   ( 703 MB)
[    0.000000]       .init : 0xc07a5000 - 0xc084c000   ( 668 kB)
[    0.000000]       .data : 0xc0590de7 - 0xc07a4d88   (2127 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0590de7   (4675 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=128, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] NR_IRQS:2304 nr_irqs:424
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1700.095 MHz processor.
[    0.004009] Calibrating delay loop (skipped), value calculated using timer frequency.. 3400.19 BogoMIPS (lpj=6800380)
[    0.004052] Security Framework initialized
[    0.004096] AppArmor: AppArmor initialized
[    0.004114] Mount-cache hash table entries: 512
[    0.004415] Initializing cgroup subsys ns
[    0.004429] Initializing cgroup subsys cpuacct
[    0.004438] Initializing cgroup subsys memory
[    0.004454] Initializing cgroup subsys devices
[    0.004461] Initializing cgroup subsys freezer
[    0.004468] Initializing cgroup subsys net_cls
[    0.004524] CPU: Trace cache: 12K uops, L1 D cache: 8K
[    0.004533] CPU: L2 cache: 128K
[    0.004537] CPU: Hyper-Threading is disabled
[    0.004546] mce: CPU supports 4 MCE banks
[    0.004566] CPU0: Thermal monitoring enabled (TM1)
[    0.004588] Performance Events: no PMU driver, software events only.
[    0.004603] Checking 'hlt' instruction... OK.
[    0.021602] SMP alternatives: switching to UP code
[    0.039787] ACPI: Core revision 20090903
[    0.050823] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.050839] ftrace: allocating 21725 entries in 43 pages
[    0.052190] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.056184] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.095886] CPU0: Intel(R) Celeron(R) CPU 1.70GHz stepping 03
[    0.096001] Brought up 1 CPUs
[    0.096001] Total of 1 processors activated (3400.19 BogoMIPS).
[    0.096001] CPU0 attaching NULL sched-domain.
[    0.096001] devtmpfs: initialized
[    0.096001] regulator: core version 0.5
[    0.096001] Time: 23:39:31  Date: 08/23/11
[    0.096001] NET: Registered protocol family 16
[    0.096001] EISA bus registered
[    0.096001] ACPI: bus type pci registered
[    0.096636] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=1
[    0.096642] PCI: Using configuration type 1 for base access
[    0.099150] bio: create slab <bio-0> at 0
[    0.100335] ACPI: EC: Look up EC in DSDT
[    0.108371] ACPI: Executed 1 blocks of module-level executable AML code
[    0.119531] ACPI: Interpreter enabled
[    0.119542] ACPI: (supports S0 S1 S4 S5)
[    0.119588] ACPI: Using IOAPIC for interrupt routing
[    0.137670] ACPI Warning: Incorrect checksum in table [OEMB] - 0F, should be 0C (20090903/tbutils-314)
[    0.137852] ACPI: No dock devices found.
[    0.138117] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.138236] pci 0000:00:00.0: reg 10 32bit mmio: [0xe0000000-0xe3ffffff]
[    0.138504] pci 0000:00:02.5: reg 20 io port: [0xffa0-0xffaf]
[    0.138547] pci 0000:00:02.5: PME# supported from D3cold
[    0.138555] pci 0000:00:02.5: PME# disabled
[    0.138607] pci 0000:00:02.7: reg 10 io port: [0xe800-0xe8ff]
[    0.138618] pci 0000:00:02.7: reg 14 io port: [0xec00-0xec7f]
[    0.138678] pci 0000:00:02.7: supports D1 D2
[    0.138682] pci 0000:00:02.7: PME# supported from D3hot D3cold
[    0.138690] pci 0000:00:02.7: PME# disabled
[    0.138725] pci 0000:00:03.0: reg 10 32bit mmio: [0xdfffc000-0xdfffcfff]
[    0.138801] pci 0000:00:03.1: reg 10 32bit mmio: [0xdfffd000-0xdfffdfff]
[    0.138875] pci 0000:00:03.2: reg 10 32bit mmio: [0xdfffe000-0xdfffefff]
[    0.138965] pci 0000:00:03.3: reg 10 32bit mmio: [0xdffff000-0xdfffffff]
[    0.139029] pci 0000:00:03.3: PME# supported from D0 D3hot D3cold
[    0.139036] pci 0000:00:03.3: PME# disabled
[    0.139093] pci 0000:00:04.0: reg 10 io port: [0xe400-0xe4ff]
[    0.139105] pci 0000:00:04.0: reg 14 32bit mmio: [0xdfffb000-0xdfffbfff]
[    0.139142] pci 0000:00:04.0: reg 30 32bit mmio pref: [0xdffc0000-0xdffdffff]
[    0.139170] pci 0000:00:04.0: supports D1 D2
[    0.139174] pci 0000:00:04.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.139181] pci 0000:00:04.0: PME# disabled
[    0.139295] pci 0000:01:00.0: reg 10 32bit mmio pref: [0xd0000000-0xd7ffffff]
[    0.139306] pci 0000:01:00.0: reg 14 32bit mmio: [0xdfee0000-0xdfefffff]
[    0.139316] pci 0000:01:00.0: reg 18 io port: [0xdc00-0xdc7f]
[    0.139364] pci 0000:01:00.0: supports D1 D2
[    0.139422] pci 0000:00:01.0: bridge io port: [0xd000-0xdfff]
[    0.139430] pci 0000:00:01.0: bridge 32bit mmio: [0xdfe00000-0xdfefffff]
[    0.139438] pci 0000:00:01.0: bridge 32bit mmio pref: [0xcfd00000-0xdfcfffff]
[    0.139453] pci_bus 0000:00: on NUMA node 0
[    0.139469] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.143359] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 10 *11 12 14 15)
[    0.143622] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.143869] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 *10 11 12 14 15)
[    0.144164] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 7 10 11 12 14 15)
[    0.144409] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 *5 7 10 11 12 14 15)
[    0.144650] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 *5 7 10 11 12 14 15)
[    0.144890] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 *7 10 11 12 14 15)
[    0.145140] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 7 10 11 12 14 15)
[    0.145432] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.145440] vgaarb: loaded
[    0.145761] SCSI subsystem initialized
[    0.145956] libata version 3.00 loaded.
[    0.146222] usbcore: registered new interface driver usbfs
[    0.146254] usbcore: registered new interface driver hub
[    0.146377] usbcore: registered new device driver usb
[    0.146832] ACPI: WMI: Mapper loaded
[    0.146838] PCI: Using ACPI for IRQ routing
[    0.147137] NetLabel: Initializing
[    0.147144] NetLabel:  domain hash size = 128
[    0.147147] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.147181] NetLabel:  unlabeled traffic allowed by default
[    0.147312] Switching to clocksource tsc
[    0.147999] AppArmor: AppArmor Filesystem Enabled
[    0.147999] pnp: PnP ACPI init
[    0.147999] ACPI: bus type pnp registered
[    0.158902] pnp: PnP ACPI: found 12 devices
[    0.158910] ACPI: ACPI bus type pnp unregistered
[    0.158918] PnPBIOS: Disabled by ACPI PNP
[    0.158959] system 00:09: ioport range 0x290-0x297 has been reserved
[    0.158967] system 00:09: ioport range 0x480-0x48f has been reserved
[    0.158975] system 00:09: ioport range 0x4d0-0x4d1 has been reserved
[    0.158981] system 00:09: ioport range 0x800-0x87f has been reserved
[    0.158987] system 00:09: ioport range 0x8e0-0x8ff has been reserved
[    0.158997] system 00:09: iomem range 0xfff80000-0xffffffff could not be reserved
[    0.159003] system 00:09: iomem range 0xffe80000-0xffefffff has been reserved
[    0.159010] system 00:09: iomem range 0xfed00000-0xfed003ff has been reserved
[    0.159027] system 00:0a: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.159033] system 00:0a: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.159061] system 00:0b: iomem range 0x0-0x9ffff could not be reserved
[    0.159067] system 00:0b: iomem range 0xc0000-0xdffff could not be reserved
[    0.159073] system 00:0b: iomem range 0xe0000-0xfffff could not be reserved
[    0.159080] system 00:0b: iomem range 0x100000-0x2bffffff could not be reserved
[    0.194104] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.194114] pci 0000:00:01.0:   IO window: 0xd000-0xdfff
[    0.194124] pci 0000:00:01.0:   MEM window: 0xdfe00000-0xdfefffff
[    0.194132] pci 0000:00:01.0:   PREFETCH window: 0xcfd00000-0xdfcfffff
[    0.194161] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.194167] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.194173] pci_bus 0000:01: resource 0 io:  [0xd000-0xdfff]
[    0.194178] pci_bus 0000:01: resource 1 mem: [0xdfe00000-0xdfefffff]
[    0.194183] pci_bus 0000:01: resource 2 pref mem [0xcfd00000-0xdfcfffff]
[    0.194260] NET: Registered protocol family 2
[    0.194470] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.195235] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.196683] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.197386] TCP: Hash tables configured (established 131072 bind 65536)
[    0.197393] TCP reno registered
[    0.197632] NET: Registered protocol family 1
[    0.197748] pci 0000:01:00.0: Boot video device
[    0.198076] cpufreq-nforce2: No nForce2 chipset.
[    0.198140] Scanning for low memory corruption every 60 seconds
[    0.198432] audit: initializing netlink socket (disabled)
[    0.198462] type=2000 audit(1314142771.196:1): initialized
[    0.211892] Trying to unpack rootfs image as initramfs...
[    0.229305] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.232627] VFS: Disk quotas dquot_6.5.2
[    0.232796] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.240925] fuse init (API version 7.13)
[    0.241246] msgmni has been set to 1355
[    0.241930] alg: No test for stdrng (krng)
[    0.242143] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.242152] io scheduler noop registered
[    0.242157] io scheduler anticipatory registered
[    0.242163] io scheduler deadline registered
[    0.242285] io scheduler cfq registered (default)
[    0.242509] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.242567] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.242783] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.242798] ACPI: Power Button [PWRB]
[    0.242919] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1
[    0.242930] ACPI: Sleep Button [SLPB]
[    0.243029] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.243035] ACPI: Power Button [PWRF]
[    0.243477] processor LNXCPU:00: registered as cooling_device0
[    0.264647] isapnp: Scanning for PnP cards...
[    0.273780] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.273958] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.274179] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.274975] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.325766] brd: module loaded
[    0.327202] loop: module loaded
[    0.327471] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    0.327772] pata_sis 0000:00:02.5: version 0.5.2
[    0.332990] scsi0 : pata_sis
[    0.333301] scsi1 : pata_sis
[    0.334815] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    0.334822] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    0.335684] Fixed MDIO Bus: probed
[    0.335776] PPP generic driver version 2.4.2
[    0.335935] tun: Universal TUN/TAP device driver, 1.6
[    0.335941] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.336245] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.336303]   alloc irq_desc for 23 on node -1
[    0.336309]   alloc kstat_irqs on node -1
[    0.336324] ehci_hcd 0000:00:03.3: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    0.336356] ehci_hcd 0000:00:03.3: EHCI Host Controller
[    0.336491] ehci_hcd 0000:00:03.3: new USB bus registered, assigned bus number 1
[    0.336901] ehci_hcd 0000:00:03.3: cache line size of 128 is not supported
[    0.336943] ehci_hcd 0000:00:03.3: irq 23, io mem 0xdffff000
[    0.348833] ehci_hcd 0000:00:03.3: USB 2.0 started, EHCI 1.00
[    0.349112] usb usb1: configuration #1 chosen from 1 choice
[    0.349187] hub 1-0:1.0: USB hub found
[    0.349215] hub 1-0:1.0: 8 ports detected
[    0.349358] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.349405]   alloc irq_desc for 20 on node -1
[    0.349411]   alloc kstat_irqs on node -1
[    0.349424] ohci_hcd 0000:00:03.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.349466] ohci_hcd 0000:00:03.0: OHCI Host Controller
[    0.349624] ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus number 2
[    0.349683] ohci_hcd 0000:00:03.0: irq 20, io mem 0xdfffc000
[    0.422538] usb usb2: configuration #1 chosen from 1 choice
[    0.422614] hub 2-0:1.0: USB hub found
[    0.422645] hub 2-0:1.0: 3 ports detected
[    0.422768]   alloc irq_desc for 21 on node -1
[    0.422774]   alloc kstat_irqs on node -1
[    0.422789] ohci_hcd 0000:00:03.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.422823] ohci_hcd 0000:00:03.1: OHCI Host Controller
[    0.422970] ohci_hcd 0000:00:03.1: new USB bus registered, assigned bus number 3
[    0.423025] ohci_hcd 0000:00:03.1: irq 21, io mem 0xdfffd000
[    0.510429] usb usb3: configuration #1 chosen from 1 choice
[    0.510510] hub 3-0:1.0: USB hub found
[    0.510541] hub 3-0:1.0: 3 ports detected
[    0.510670]   alloc irq_desc for 22 on node -1
[    0.510676]   alloc kstat_irqs on node -1
[    0.510698] ohci_hcd 0000:00:03.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    0.510734] ohci_hcd 0000:00:03.2: OHCI Host Controller
[    0.510886] ohci_hcd 0000:00:03.2: new USB bus registered, assigned bus number 4
[    0.510941] ohci_hcd 0000:00:03.2: irq 22, io mem 0xdfffe000
[    0.603002] usb usb4: configuration #1 chosen from 1 choice
[    0.603081] hub 4-0:1.0: USB hub found
[    0.603107] hub 4-0:1.0: 2 ports detected
[    0.603236] uhci_hcd: USB Universal Host Controller Interface driver
[    0.603431] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    0.603827] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.603853] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.609379] mice: PS/2 mouse device common for all mice
[    0.609839] rtc_cmos 00:02: RTC can wake from S4
[    0.610011] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    0.610056] rtc0: alarms up to one month, 114 bytes nvram
[    0.610358] device-mapper: uevent: version 1.0.3
[    0.610764] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[    0.612428] device-mapper: multipath: version 1.1.0 loaded
[    0.612440] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.612955] EISA: Probing bus 0 at eisa.0
[    0.613029] EISA: Detected 0 cards.
[    0.616880] cpuidle: using governor ladder
[    0.616888] cpuidle: using governor menu
[    0.617846] TCP cubic registered
[    0.618228] NET: Registered protocol family 10
[    0.620032] NET: Registered protocol family 17
[    0.620171] Using IPI No-Shortcut mode
[    0.620488] PM: Resume from disk failed.
[    0.620534] registered taskstats version 1
[    0.620906]   Magic number: 7:315:707
[    0.621048] rtc_cmos 00:02: setting system clock to 2011-08-23 23:39:32 UTC (1314142772)
[    0.621058] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.621061] EDD information not available.
[    0.628445] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    0.713921] ata1.00: ATA-6: ST340014A, 8.54, max UDMA/100
[    0.713929] ata1.00: 78165360 sectors, multi 16: LBA48 
[    0.714149] ata1.01: ATA-7: SAMSUNG SP0411N, TW100-13, max UDMA/100
[    0.714156] ata1.01: 78242976 sectors, multi 16: LBA48 
[    0.729855] ata1.00: configured for UDMA/100
[    0.789097] ata1.01: configured for UDMA/100
[    0.960903] isapnp: No Plug & Play device found
[    0.961239] scsi 0:0:0:0: Direct-Access     ATA      ST340014A        8.54 PQ: 0 ANSI: 5
[    0.961628] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    0.962049] scsi 0:0:1:0: Direct-Access     ATA      SAMSUNG SP0411N  TW10 PQ: 0 ANSI: 5
[    0.962540] sd 0:0:1:0: Attached scsi generic sg1 type 0
[    0.962994] sd 0:0:0:0: [sda] 78165360 512-byte logical blocks: (40.0 GB/37.2 GiB)
[    0.963224] sd 0:0:0:0: [sda] Write Protect is off
[    0.963232] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    0.963353] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.963960]  sda: sda1 sda2 sda3 < sda5
[    1.001969] sd 0:0:1:0: [sdb] 78242976 512-byte logical blocks: (40.0 GB/37.3 GiB)
[    1.018981]  sda6 sda7 sda8 sda9 >
[    1.064204] sd 0:0:1:0: [sdb] Write Protect is off
[    1.064214] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[    1.064371] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.065037]  sdb: sdb1 sdb2 sdb3 <
[    1.085092] Freeing initrd memory: 7808k freed
[    1.096178]  sdb5 sdb6
[    1.121820] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.121852]  sdb7
[    1.128522] ata2.00: ATAPI: HL-DT-STDVD-RAM GH22NP20, 1.00, max UDMA/66
[    1.128583] ata2.00: limited to UDMA/33 due to 40-wire cable
[    1.134805]  sdb8 >
[    1.136369] sd 0:0:1:0: [sdb] Attached SCSI disk
[    1.144552] ata2.00: configured for UDMA/33
[    1.147017] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVD-RAM GH22NP20 1.00 PQ: 0 ANSI: 5
[    1.151130] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.151140] Uniform CD-ROM driver Revision: 3.20
[    1.151416] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.151595] sr 1:0:0:0: Attached scsi generic sg2 type 5
[    1.151757] Freeing unused kernel memory: 668k freed
[    1.152972] Write protecting the kernel text: 4676k
[    1.153037] Write protecting the kernel read-only data: 1848k
[    1.209876] udev: starting version 151
[    1.844281] sis900.c: v1.08.10 Apr. 2 2006
[    1.844351]   alloc irq_desc for 19 on node -1
[    1.844358]   alloc kstat_irqs on node -1
[    1.844374] sis900 0000:00:04.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.845624] 0000:00:04.0: Realtek RTL8201 PHY transceiver found at address 1.
[    1.858248] 0000:00:04.0: Using transceiver found at address 1 as default
[    1.933701] eth0: SiS 900 PCI Fast Ethernet at 0xe400, IRQ 19, 00:0d:87:c7:52:00
[    3.293480] EXT4-fs (sda6): mounted filesystem with ordered data mode
[   14.943448] Adding 610428k swap on /dev/sda7.  Priority:-1 extents:1 across:610428k 
[   14.996406] udev: starting version 151
[   15.338539] lp: driver loaded but no devices found
[   15.709491] Linux agpgart interface v0.103
[   15.727590] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   15.912710] agpgart-sis 0000:00:00.0: SiS chipset [1039/0661]
[   16.082633] agpgart-sis 0000:00:00.0: AGP aperture is 64M @ 0xe0000000
[   16.178257] vga16fb: initializing
[   16.178266] vga16fb: mapped to 0xc00a0000
[   16.178429] fb0: VGA16 VGA frame buffer device
[   16.392680] psmouse serio1: ID: 10 00 64
[   16.568675] Compat-wireless backport release: compat-wireless-2011-05-23
[   16.568684] Backport based on linux-next.git next-20110527
[   16.717453] type=1505 audit(1314160788.594:2):  operation="profile_load" pid=517 name="/sbin/dhclient3"
[   16.718403] type=1505 audit(1314160788.594:3):  operation="profile_load" pid=517 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   16.718937] type=1505 audit(1314160788.594:4):  operation="profile_load" pid=517 name="/usr/lib/connman/scripts/dhclient-script"
[   16.991284] cfg80211: Calling CRDA to update world regulatory domain
[   17.015056] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input5
[   17.055689] cfg80211: World regulatory domain updated:
[   17.055697] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   17.055704] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.055710] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   17.055715] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   17.055720] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.055726] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.192365] Console: switching to colour frame buffer device 80x30
[   17.444296] usbcore: registered new interface driver ath9k_htc
[   17.734554]   alloc irq_desc for 18 on node -1
[   17.734562]   alloc kstat_irqs on node -1
[   17.734578] Intel ICH 0000:00:02.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[   18.060095] intel8x0_measure_ac97_clock: measured 53998 usecs (2598 samples)
[   18.060104] intel8x0: clocking to 48000
[  105.537074] EXT4-fs (sda6): warning: mounting fs with errors, running e2fsck is recommended
[  105.792606] EXT4-fs (sda8): mounted filesystem with ordered data mode
[  106.311878] type=1505 audit(1314160878.186:5):  operation="profile_load" pid=753 name="/usr/share/gdm/guest-session/Xsession"
[  106.370386] type=1505 audit(1314160878.246:6):  operation="profile_replace" pid=755 name="/sbin/dhclient3"
[  106.371403] type=1505 audit(1314160878.246:7):  operation="profile_replace" pid=755 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[  106.371964] type=1505 audit(1314160878.246:8):  operation="profile_replace" pid=755 name="/usr/lib/connman/scripts/dhclient-script"
[  106.536619] type=1505 audit(1314160878.414:9):  operation="profile_load" pid=761 name="/usr/bin/evince"
[  106.632427] type=1505 audit(1314160878.510:10):  operation="profile_load" pid=761 name="/usr/bin/evince-previewer"
[  106.676099] type=1505 audit(1314160878.554:11):  operation="profile_load" pid=761 name="/usr/bin/evince-thumbnailer"
[  106.787429] type=1505 audit(1314160878.662:12):  operation="profile_load" pid=832 name="/usr/bin/freshclam"
[  106.828916] type=1505 audit(1314160878.706:13):  operation="profile_load" pid=833 name="/usr/lib/cups/backend/cups-pdf"
[  106.830117] type=1505 audit(1314160878.706:14):  operation="profile_load" pid=833 name="/usr/sbin/cupsd"
[  108.219690] ppdev: user-space parallel port driver
[  108.617233] eth0: Media Link On 100mbps full-duplex 
[  117.144045] eth0: no IPv6 routers present
[29325.716077] usb 1-6: new high speed USB device using ehci_hcd and address 2
[29325.865285] usb 1-6: configuration #1 chosen from 1 choice
[29326.381794] usb 1-6: ath9k_htc: Transferred FW: htc_9271.fw, size: 51272
[29326.616847] ath9k_htc 1-6:1.0: ath9k_htc: HTC initialized with 33 credits
[29326.825565] ath9k_htc 1-6:1.0: ath9k_htc: FW Version: 1.1
[29326.825573] ath9k_htc 1-6:1.0: ath9k_htc: Please upgrade to FW version 1.3
[29326.826316] Failed to initialize the device
[29326.837242] ath9k_htc: probe of 1-6:1.0 failed with error -22


lsmod | grep ath9k
xxx:~/Documentos$ lsmod | grep ath9k
ath9k_htc              52997  0 
mac80211              258552  1 ath9k_htc
ath9k_common            2443  1 ath9k_htc
ath9k_hw              285336  2 ath9k_htc,ath9k_common
ath                    14236  2 ath9k_htc,ath9k_hw
cfg80211              162152  3 ath9k_htc,mac80211,ath
compat                 19219  3 ath9k_htc,mac80211,cfg80211
compat_firmware_class     6200  1 ath9k_htc
led_class               2864  2 ath9k_htc,compat


cat /etc/modules
xxx:~/Documentos$ cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp

# Generated by ath9k_htc-installer on lun ago 22 13:44:11 2011
ath9k_htc


ls -l /lib/firmware/ar*
:~/Documentos$ ls -l /lib/firmware/ar*
-rw-r--r-- 1 root root 70624 2011-02-18 13:01 /lib/firmware/ar7010_1_1.fw
-rw-r--r-- 1 root root 83968 2010-12-14 11:25 /lib/firmware/ar9170-1.fw
-rw-r--r-- 1 root root  3508 2010-12-14 11:25 /lib/firmware/ar9170-2.fw
-rw-r--r-- 1 root root 15960 2010-12-14 11:26 /lib/firmware/ar9170.fw
```

---

### Post by vagrale13 on 2011-08-24
Download firmware **ar9271.fw** from here [http://git.kernel.org/?p=linux/kernel/git/dwmw2/linux-firmware.git;a=history;f=ar9271.fw;h=d0ee74a1c8dccb7cc21f5be90f1d4048fa9dbf9e;hb=HEAD](http://git.kernel.org/?p=linux/kernel/git/dwmw2/linux-firmware.git;a=history;f=ar9271.fw;h=d0ee74a1c8dccb7cc21f5be90f1d4048fa9dbf9e;hb=HEAD)
put it to your home folder - open terminal and run
```
 sudo mv ar9271.fw /lib/firmware
```reboot and then see if it works!

If not, post again the output of commands
```
dmesg
ls -l /lib/firmware/ar*
```

---

### Post by carlomagn0 on 2011-08-31
Hi,

I did like you indicated, but it still not function.
Here are the output of the commands.

```
BR

---------

xxx:~$ dmesg 

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.32-33-generic (buildd@zirconium) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #72-Ubuntu SMP Fri Jul 29 21:08:37 UTC 2011 (Ubuntu 2.6.32-33.72-generic 2.6.32.41+drm33.18)
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
[    0.000000]  BIOS-e820: 0000000000100000 - 000000002bfd0000 (usable)
[    0.000000]  BIOS-e820: 000000002bfd0000 - 000000002bfdf000 (ACPI data)
[    0.000000]  BIOS-e820: 000000002bfdf000 - 000000002c000000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000fffc0000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.3 present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0x2bfd0 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask FE0000000 write-back
[    0.000000]   1 base 020000000 mask FF8000000 write-back
[    0.000000]   2 base 028000000 mask FFC000000 write-back
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
[    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000002bfd0000 (usable)
[    0.000000]  modified: 000000002bfd0000 - 000000002bfdf000 (ACPI data)
[    0.000000]  modified: 000000002bfdf000 - 000000002c000000 (ACPI NVS)
[    0.000000]  modified: 00000000fffc0000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 00c00000
[    0.000000] init_memory_mapping: 0000000000000000-000000002bfd0000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 002bc00000 page 2M
[    0.000000]  002bc00000 - 002bfd0000 page 4k
[    0.000000] kernel direct mapping tables up to 2bfd0000 @ 10000-15000
[    0.000000] RAMDISK: 2087b000 - 2101b26a
[    0.000000] ACPI: RSDP 000f70f0 00014 (v00 ACPIAM)
[    0.000000] ACPI: RSDT 2bfd0000 00030 (v01 A M I  OEMRSDT  02000404 MSFT 00000097)
[    0.000000] ACPI: FACP 2bfd0200 00081 (v02 A M I  OEMFACP  02000404 MSFT 00000097)
[    0.000000] ACPI: DSDT 2bfd03f0 0344B (v01   M963    M963G 00000000 INTL 02002026)
[    0.000000] ACPI: FACS 2bfdf000 00040
[    0.000000] ACPI: APIC 2bfd0390 0005C (v01 A M I  OEMAPIC  02000404 MSFT 00000097)
[    0.000000] ACPI: OEMB 2bfdf040 00040 (v01 A M I  AMI_OEM  02000404 MSFT 00000097)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 703MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 2bfd0000
[    0.000000]   low ram: 0 - 2bfd0000
[    0.000000]   node 0 low ram: 00000000 - 2bfd0000
[    0.000000]   node 0 bootmap 00011000 - 000167fc
[    0.000000] (9 early reservations) ==> bootmem [0000000000 - 002bfd0000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
[    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
[    0.000000]   #3 [0000100000 - 00008e0ef8]    TEXT DATA BSS ==> [0000100000 - 00008e0ef8]
[    0.000000]   #4 [002087b000 - 002101b26a]          RAMDISK ==> [002087b000 - 002101b26a]
[    0.000000]   #5 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #6 [00008e1000 - 00008e40e1]              BRK ==> [00008e1000 - 00008e40e1]
[    0.000000]   #7 [0000010000 - 0000011000]          PGTABLE ==> [0000010000 - 0000011000]
[    0.000000]   #8 [0000011000 - 0000017000]          BOOTMAP ==> [0000011000 - 0000017000]
[    0.000000] found SMP MP-table at [c00ff780] ff780
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x0002bfd0
[    0.000000]   HighMem  0x0002bfd0 -> 0x0002bfd0
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0002bfd0
[    0.000000] On node 0 totalpages: 180063
[    0.000000] free_area_init_node: node 0, pgdat c079a7c0, node_mem_map c1001200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1376 pages used for memmap
[    0.000000]   Normal zone: 174704 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x81] disabled)
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 2 CPUs, 1 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 2c000000 (gap: 2c000000:d3fc0000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @c1800000 s36312 r0 d21032 u2097152
[    0.000000] pcpu-alloc: s36312 r0 d21032 u2097152 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 1 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 178655
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-33-generic root=UUID=bf2e253f-1dc2-4187-aba1-32ef8c0a29bb ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] allocated 3603200 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (00000000:00000000)
[    0.000000] Memory: 693908k/720704k available (4675k kernel code, 25996k reserved, 2127k data, 668k init, 0k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff1d000 - 0xfffff000   ( 904 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xec7d0000 - 0xff7fe000   ( 304 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xebfd0000   ( 703 MB)
[    0.000000]       .init : 0xc07a5000 - 0xc084c000   ( 668 kB)
[    0.000000]       .data : 0xc0590de7 - 0xc07a4d88   (2127 kB)
[    0.000000]       .text : 0xc0100000 - 0xc0590de7   (4675 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=13, HWalign=128, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] NR_IRQS:2304 nr_irqs:424
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1699.950 MHz processor.
[    0.004009] Calibrating delay loop (skipped), value calculated using timer frequency.. 3399.90 BogoMIPS (lpj=6799800)
[    0.004051] Security Framework initialized
[    0.004093] AppArmor: AppArmor initialized
[    0.004112] Mount-cache hash table entries: 512
[    0.004414] Initializing cgroup subsys ns
[    0.004428] Initializing cgroup subsys cpuacct
[    0.004437] Initializing cgroup subsys memory
[    0.004453] Initializing cgroup subsys devices
[    0.004459] Initializing cgroup subsys freezer
[    0.004465] Initializing cgroup subsys net_cls
[    0.004520] CPU: Trace cache: 12K uops, L1 D cache: 8K
[    0.004528] CPU: L2 cache: 128K
[    0.004533] CPU: Hyper-Threading is disabled
[    0.004542] mce: CPU supports 4 MCE banks
[    0.004562] CPU0: Thermal monitoring enabled (TM1)
[    0.004584] Performance Events: no PMU driver, software events only.
[    0.004600] Checking 'hlt' instruction... OK.
[    0.021593] SMP alternatives: switching to UP code
[    0.039792] ACPI: Core revision 20090903
[    0.050781] ftrace: converting mcount calls to 0f 1f 44 00 00
[    0.050797] ftrace: allocating 21725 entries in 43 pages
[    0.052191] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.056158] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.095858] CPU0: Intel(R) Celeron(R) CPU 1.70GHz stepping 03
[    0.096001] Brought up 1 CPUs
[    0.096001] Total of 1 processors activated (3399.90 BogoMIPS).
[    0.096001] CPU0 attaching NULL sched-domain.
[    0.096001] devtmpfs: initialized
[    0.096001] regulator: core version 0.5
[    0.096001] Time: 10:02:10  Date: 08/31/11
[    0.096001] NET: Registered protocol family 16
[    0.096001] EISA bus registered
[    0.096001] ACPI: bus type pci registered
[    0.096630] PCI: PCI BIOS revision 2.10 entry at 0xf0031, last bus=1
[    0.096636] PCI: Using configuration type 1 for base access
[    0.099143] bio: create slab <bio-0> at 0
[    0.100325] ACPI: EC: Look up EC in DSDT
[    0.108372] ACPI: Executed 1 blocks of module-level executable AML code
[    0.119535] ACPI: Interpreter enabled
[    0.119546] ACPI: (supports S0 S1 S4 S5)
[    0.119592] ACPI: Using IOAPIC for interrupt routing
[    0.137697] ACPI Warning: Incorrect checksum in table [OEMB] - 0F, should be 0C (20090903/tbutils-314)
[    0.137877] ACPI: No dock devices found.
[    0.138142] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.138258] pci 0000:00:00.0: reg 10 32bit mmio: [0xe0000000-0xe3ffffff]
[    0.138525] pci 0000:00:02.5: reg 20 io port: [0xffa0-0xffaf]
[    0.138568] pci 0000:00:02.5: PME# supported from D3cold
[    0.138575] pci 0000:00:02.5: PME# disabled
[    0.138627] pci 0000:00:02.7: reg 10 io port: [0xe800-0xe8ff]
[    0.138638] pci 0000:00:02.7: reg 14 io port: [0xec00-0xec7f]
[    0.138698] pci 0000:00:02.7: supports D1 D2
[    0.138702] pci 0000:00:02.7: PME# supported from D3hot D3cold
[    0.138709] pci 0000:00:02.7: PME# disabled
[    0.138745] pci 0000:00:03.0: reg 10 32bit mmio: [0xdfffc000-0xdfffcfff]
[    0.138824] pci 0000:00:03.1: reg 10 32bit mmio: [0xdfffd000-0xdfffdfff]
[    0.138900] pci 0000:00:03.2: reg 10 32bit mmio: [0xdfffe000-0xdfffefff]
[    0.138988] pci 0000:00:03.3: reg 10 32bit mmio: [0xdffff000-0xdfffffff]
[    0.139053] pci 0000:00:03.3: PME# supported from D0 D3hot D3cold
[    0.139060] pci 0000:00:03.3: PME# disabled
[    0.139117] pci 0000:00:04.0: reg 10 io port: [0xe400-0xe4ff]
[    0.139129] pci 0000:00:04.0: reg 14 32bit mmio: [0xdfffb000-0xdfffbfff]
[    0.139166] pci 0000:00:04.0: reg 30 32bit mmio pref: [0xdffc0000-0xdffdffff]
[    0.139193] pci 0000:00:04.0: supports D1 D2
[    0.139198] pci 0000:00:04.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.139205] pci 0000:00:04.0: PME# disabled
[    0.139319] pci 0000:01:00.0: reg 10 32bit mmio pref: [0xd0000000-0xd7ffffff]
[    0.139330] pci 0000:01:00.0: reg 14 32bit mmio: [0xdfee0000-0xdfefffff]
[    0.139340] pci 0000:01:00.0: reg 18 io port: [0xdc00-0xdc7f]
[    0.139387] pci 0000:01:00.0: supports D1 D2
[    0.139445] pci 0000:00:01.0: bridge io port: [0xd000-0xdfff]
[    0.139453] pci 0000:00:01.0: bridge 32bit mmio: [0xdfe00000-0xdfefffff]
[    0.139461] pci 0000:00:01.0: bridge 32bit mmio pref: [0xcfd00000-0xdfcfffff]
[    0.139476] pci_bus 0000:00: on NUMA node 0
[    0.139492] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.143327] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 10 *11 12 14 15)
[    0.143590] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.143834] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 *10 11 12 14 15)
[    0.144126] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 7 10 11 12 14 15)
[    0.144369] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 *5 7 10 11 12 14 15)
[    0.144612] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 *5 7 10 11 12 14 15)
[    0.144852] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 *7 10 11 12 14 15)
[    0.145105] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 7 10 11 12 14 15)
[    0.145399] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.145407] vgaarb: loaded
[    0.145729] SCSI subsystem initialized
[    0.145923] libata version 3.00 loaded.
[    0.146194] usbcore: registered new interface driver usbfs
[    0.146226] usbcore: registered new interface driver hub
[    0.146355] usbcore: registered new device driver usb
[    0.146824] ACPI: WMI: Mapper loaded
[    0.146831] PCI: Using ACPI for IRQ routing
[    0.147136] NetLabel: Initializing
[    0.147143] NetLabel:  domain hash size = 128
[    0.147146] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.147182] NetLabel:  unlabeled traffic allowed by default
[    0.147314] Switching to clocksource tsc
[    0.148001] AppArmor: AppArmor Filesystem Enabled
[    0.148001] pnp: PnP ACPI init
[    0.148001] ACPI: bus type pnp registered
[    0.158993] pnp: PnP ACPI: found 12 devices
[    0.159001] ACPI: ACPI bus type pnp unregistered
[    0.159008] PnPBIOS: Disabled by ACPI PNP
[    0.159051] system 00:09: ioport range 0x290-0x297 has been reserved
[    0.159058] system 00:09: ioport range 0x480-0x48f has been reserved
[    0.159066] system 00:09: ioport range 0x4d0-0x4d1 has been reserved
[    0.159072] system 00:09: ioport range 0x800-0x87f has been reserved
[    0.159078] system 00:09: ioport range 0x8e0-0x8ff has been reserved
[    0.159088] system 00:09: iomem range 0xfff80000-0xffffffff could not be reserved
[    0.159095] system 00:09: iomem range 0xffe80000-0xffefffff has been reserved
[    0.159101] system 00:09: iomem range 0xfed00000-0xfed003ff has been reserved
[    0.159117] system 00:0a: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.159124] system 00:0a: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.159151] system 00:0b: iomem range 0x0-0x9ffff could not be reserved
[    0.159157] system 00:0b: iomem range 0xc0000-0xdffff could not be reserved
[    0.159164] system 00:0b: iomem range 0xe0000-0xfffff could not be reserved
[    0.159170] system 00:0b: iomem range 0x100000-0x2bffffff could not be reserved
[    0.194201] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.194210] pci 0000:00:01.0:   IO window: 0xd000-0xdfff
[    0.194220] pci 0000:00:01.0:   MEM window: 0xdfe00000-0xdfefffff
[    0.194228] pci 0000:00:01.0:   PREFETCH window: 0xcfd00000-0xdfcfffff
[    0.194257] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.194263] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.194269] pci_bus 0000:01: resource 0 io:  [0xd000-0xdfff]
[    0.194274] pci_bus 0000:01: resource 1 mem: [0xdfe00000-0xdfefffff]
[    0.194279] pci_bus 0000:01: resource 2 pref mem [0xcfd00000-0xdfcfffff]
[    0.194356] NET: Registered protocol family 2
[    0.194564] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.195334] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.196755] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.197480] TCP: Hash tables configured (established 131072 bind 65536)
[    0.197486] TCP reno registered
[    0.197726] NET: Registered protocol family 1
[    0.197840] pci 0000:01:00.0: Boot video device
[    0.198167] cpufreq-nforce2: No nForce2 chipset.
[    0.198233] Scanning for low memory corruption every 60 seconds
[    0.198525] audit: initializing netlink socket (disabled)
[    0.198554] type=2000 audit(1314784930.196:1): initialized
[    0.213203] Trying to unpack rootfs image as initramfs...
[    0.229160] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.236318] VFS: Disk quotas dquot_6.5.2
[    0.236482] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.238156] fuse init (API version 7.13)
[    0.238465] msgmni has been set to 1355
[    0.245255] alg: No test for stdrng (krng)
[    0.245472] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.245481] io scheduler noop registered
[    0.245487] io scheduler anticipatory registered
[    0.245492] io scheduler deadline registered
[    0.245615] io scheduler cfq registered (default)
[    0.245847] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.245904] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.246126] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.246142] ACPI: Power Button [PWRB]
[    0.246269] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1
[    0.246280] ACPI: Sleep Button [SLPB]
[    0.246385] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.246392] ACPI: Power Button [PWRF]
[    0.246850] processor LNXCPU:00: registered as cooling_device0
[    0.268922] isapnp: Scanning for PnP cards...
[    0.275189] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.275368] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.275585] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.276340] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.283530] brd: module loaded
[    0.333546] loop: module loaded
[    0.333824] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    0.334113] pata_sis 0000:00:02.5: version 0.5.2
[    0.334439] scsi0 : pata_sis
[    0.334729] scsi1 : pata_sis
[    0.336252] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    0.336260] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    0.337178] Fixed MDIO Bus: probed
[    0.337273] PPP generic driver version 2.4.2
[    0.337432] tun: Universal TUN/TAP device driver, 1.6
[    0.337438] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.337734] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.337794]   alloc irq_desc for 23 on node -1
[    0.337801]   alloc kstat_irqs on node -1
[    0.337815] ehci_hcd 0000:00:03.3: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    0.337847] ehci_hcd 0000:00:03.3: EHCI Host Controller
[    0.337977] ehci_hcd 0000:00:03.3: new USB bus registered, assigned bus number 1
[    0.338049] ehci_hcd 0000:00:03.3: cache line size of 128 is not supported
[    0.338090] ehci_hcd 0000:00:03.3: irq 23, io mem 0xdffff000
[    0.349117] ehci_hcd 0000:00:03.3: USB 2.0 started, EHCI 1.00
[    0.349410] usb usb1: configuration #1 chosen from 1 choice
[    0.349486] hub 1-0:1.0: USB hub found
[    0.349512] hub 1-0:1.0: 8 ports detected
[    0.349660] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.349709]   alloc irq_desc for 20 on node -1
[    0.349715]   alloc kstat_irqs on node -1
[    0.349730] ohci_hcd 0000:00:03.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.349771] ohci_hcd 0000:00:03.0: OHCI Host Controller
[    0.349929] ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus number 2
[    0.349989] ohci_hcd 0000:00:03.0: irq 20, io mem 0xdfffc000
[    0.422465] usb usb2: configuration #1 chosen from 1 choice
[    0.422541] hub 2-0:1.0: USB hub found
[    0.422575] hub 2-0:1.0: 3 ports detected
[    0.422704]   alloc irq_desc for 21 on node -1
[    0.422710]   alloc kstat_irqs on node -1
[    0.422724] ohci_hcd 0000:00:03.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.422759] ohci_hcd 0000:00:03.1: OHCI Host Controller
[    0.422903] ohci_hcd 0000:00:03.1: new USB bus registered, assigned bus number 3
[    0.422959] ohci_hcd 0000:00:03.1: irq 21, io mem 0xdfffd000
[    0.514927] usb usb3: configuration #1 chosen from 1 choice
[    0.515007] hub 3-0:1.0: USB hub found
[    0.515036] hub 3-0:1.0: 3 ports detected
[    0.515175]   alloc irq_desc for 22 on node -1
[    0.515182]   alloc kstat_irqs on node -1
[    0.515197] ohci_hcd 0000:00:03.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    0.515235] ohci_hcd 0000:00:03.2: OHCI Host Controller
[    0.515385] ohci_hcd 0000:00:03.2: new USB bus registered, assigned bus number 4
[    0.515440] ohci_hcd 0000:00:03.2: irq 22, io mem 0xdfffe000
[    0.602494] usb usb4: configuration #1 chosen from 1 choice
[    0.602575] hub 4-0:1.0: USB hub found
[    0.602601] hub 4-0:1.0: 2 ports detected
[    0.602728] uhci_hcd: USB Universal Host Controller Interface driver
[    0.602928] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    0.603328] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.603353] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.605458] mice: PS/2 mouse device common for all mice
[    0.605927] rtc_cmos 00:02: RTC can wake from S4
[    0.606095] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    0.606139] rtc0: alarms up to one month, 114 bytes nvram
[    0.606440] device-mapper: uevent: version 1.0.3
[    0.609466] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[    0.610482] device-mapper: multipath: version 1.1.0 loaded
[    0.610493] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.613706] EISA: Probing bus 0 at eisa.0
[    0.613753] EISA: Detected 0 cards.
[    0.616355] cpuidle: using governor ladder
[    0.616363] cpuidle: using governor menu
[    0.617396] TCP cubic registered
[    0.617790] NET: Registered protocol family 10
[    0.619551] NET: Registered protocol family 17
[    0.619685] Using IPI No-Shortcut mode
[    0.619997] PM: Resume from disk failed.
[    0.620029] registered taskstats version 1
[    0.620357]   Magic number: 7:363:23
[    0.620494] rtc_cmos 00:02: setting system clock to 2011-08-31 10:02:10 UTC (1314784930)
[    0.620502] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.620506] EDD information not available.
[    0.624460] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    0.709300] ata1.00: ATA-6: ST340014A, 8.54, max UDMA/100
[    0.709308] ata1.00: 78165360 sectors, multi 16: LBA48 
[    0.709514] ata1.01: ATA-7: SAMSUNG SP0411N, TW100-13, max UDMA/100
[    0.709521] ata1.01: 78242976 sectors, multi 16: LBA48 
[    0.725344] ata1.00: configured for UDMA/100
[    0.733667] ata1.01: configured for UDMA/100
[    0.964464] isapnp: No Plug & Play device found
[    0.964841] scsi 0:0:0:0: Direct-Access     ATA      ST340014A        8.54 PQ: 0 ANSI: 5
[    0.965227] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    0.965638] scsi 0:0:1:0: Direct-Access     ATA      SAMSUNG SP0411N  TW10 PQ: 0 ANSI: 5
[    0.966125] sd 0:0:1:0: Attached scsi generic sg1 type 0
[    0.966561] sd 0:0:0:0: [sda] 78165360 512-byte logical blocks: (40.0 GB/37.2 GiB)
[    0.966798] sd 0:0:0:0: [sda] Write Protect is off
[    0.966806] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    0.966927] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.967550]  sda: sda1 sda2 sda3 < sda5
[    1.008765] sd 0:0:1:0: [sdb] 78242976 512-byte logical blocks: (40.0 GB/37.3 GiB)
[    1.016895] usb 4-2: new full speed USB device using ohci_hcd and address 2
[    1.026287]  sda6 sda7 sda8 sda9 >
[    1.070658] sd 0:0:1:0: [sdb] Write Protect is off
[    1.070668] sd 0:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[    1.070832] sd 0:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.071486]  sdb: sdb1 sdb2 sdb3 <
[    1.087491] Freeing initrd memory: 7808k freed
[    1.103011]  sdb5 sdb6
[    1.126961] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.126993]  sdb7
[    1.132517] ata2.00: ATAPI: HL-DT-STDVD-RAM GH22NP20, 1.00, max UDMA/66
[    1.132577] ata2.00: limited to UDMA/33 due to 40-wire cable
[    1.139949]  sdb8 >
[    1.141521] sd 0:0:1:0: [sdb] Attached SCSI disk
[    1.148544] ata2.00: configured for UDMA/33
[    1.150933] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVD-RAM GH22NP20 1.00 PQ: 0 ANSI: 5
[    1.155064] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.155076] Uniform CD-ROM driver Revision: 3.20
[    1.155356] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.155538] sr 1:0:0:0: Attached scsi generic sg2 type 5
[    1.155706] Freeing unused kernel memory: 668k freed
[    1.156929] Write protecting the kernel text: 4676k
[    1.156992] Write protecting the kernel read-only data: 1848k
[    1.213956] udev: starting version 151
[    1.244449] usb 4-2: not running at top speed; connect to a high speed hub
[    1.262428] usb 4-2: configuration #1 chosen from 1 choice
[    1.868635] sis900.c: v1.08.10 Apr. 2 2006
[    1.868708]   alloc irq_desc for 19 on node -1
[    1.868715]   alloc kstat_irqs on node -1
[    1.868730] sis900 0000:00:04.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.869973] 0000:00:04.0: Realtek RTL8201 PHY transceiver found at address 1.
[    1.882892] 0000:00:04.0: Using transceiver found at address 1 as default
[    1.941630] eth0: SiS 900 PCI Fast Ethernet at 0xe400, IRQ 19, 00:0d:87:c7:52:00
[    3.499175] EXT4-fs (sda6): mounted filesystem with ordered data mode
[   15.129081] Adding 610428k swap on /dev/sda7.  Priority:-1 extents:1 across:610428k 
[   15.214641] udev: starting version 151
[   15.420728] lp: driver loaded but no devices found
[   15.707581] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   15.916471] Linux agpgart interface v0.103
[   16.144108] agpgart-sis 0000:00:00.0: SiS chipset [1039/0661]
[   16.245955] vga16fb: initializing
[   16.245965] vga16fb: mapped to 0xc00a0000
[   16.246126] fb0: VGA16 VGA frame buffer device
[   16.348298] agpgart-sis 0000:00:00.0: AGP aperture is 64M @ 0xe0000000
[   16.468924] psmouse serio1: ID: 10 00 64
[   16.746552] Compat-wireless backport release: compat-wireless-2011-05-23
[   16.746561] Backport based on linux-next.git next-20110527
[   16.901165] cfg80211: Calling CRDA to update world regulatory domain
[   16.987647] cfg80211: World regulatory domain updated:
[   16.987655] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   16.987661] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   16.987667] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   16.987672] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   16.987677] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   16.987682] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.010590] type=1505 audit(1314802946.887:2):  operation="profile_load" pid=531 name="/sbin/dhclient3"
[   17.086642] type=1505 audit(1314802946.963:3):  operation="profile_load" pid=531 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   17.087186] type=1505 audit(1314802946.963:4):  operation="profile_load" pid=531 name="/usr/lib/connman/scripts/dhclient-script"
[   17.117137] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input5
[   17.146544] type=1505 audit(1314802947.023:5):  operation="profile_replace" pid=544 name="/sbin/dhclient3"
[   17.147539] type=1505 audit(1314802947.023:6):  operation="profile_replace" pid=544 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   17.155493] type=1505 audit(1314802947.031:7):  operation="profile_replace" pid=544 name="/usr/lib/connman/scripts/dhclient-script"
[   17.601276] Console: switching to colour frame buffer device 80x30
[   17.940055]   alloc irq_desc for 18 on node -1
[   17.940062]   alloc kstat_irqs on node -1
[   17.940077] Intel ICH 0000:00:02.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[   18.136474] usb 4-2: ath9k_htc: Transferred FW: htc_9271.fw, size: 51272
[   18.272065] intel8x0_measure_ac97_clock: measured 55579 usecs (2673 samples)
[   18.272074] intel8x0: clocking to 48000
[   19.136054] ath9k_htc 4-2:1.0: ath9k_htc: Target is unresponsive
[   19.136071] Failed to initialize the device
[   19.207387] ath9k_htc: probe of 4-2:1.0 failed with error -22
[   19.207462] usbcore: registered new interface driver ath9k_htc
[   20.499069] EXT4-fs (sda6): warning: mounting fs with errors, running e2fsck is recommended
[   20.734463] EXT4-fs (sda8): mounted filesystem with ordered data mode
[   21.098935] type=1505 audit(1314802950.975:8):  operation="profile_load" pid=763 name="/usr/share/gdm/guest-session/Xsession"
[   21.150653] type=1505 audit(1314802951.027:9):  operation="profile_replace" pid=769 name="/sbin/dhclient3"
[   21.151669] type=1505 audit(1314802951.027:10):  operation="profile_replace" pid=769 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   21.169526] type=1505 audit(1314802951.047:11):  operation="profile_replace" pid=769 name="/usr/lib/connman/scripts/dhclient-script"
[   23.103670] ppdev: user-space parallel port driver
[   23.541243] eth0: Media Link On 100mbps full-duplex 
[   31.940043] eth0: no IPv6 routers present

xxx:~$ ls -l /lib/firmware/ar*

-rw-r--r-- 1 root    root    70624 2011-02-18 13:01 /lib/firmware/ar7010_1_1.fw
-rw-r--r-- 1 root    root    83968 2010-12-14 11:25 /lib/firmware/ar9170-1.fw
-rw-r--r-- 1 root    root     3508 2010-12-14 11:25 /lib/firmware/ar9170-2.fw
-rw-r--r-- 1 root    root    15960 2010-12-14 11:26 /lib/firmware/ar9170.fw
-rw-r--r-- 1 cquirog cquirog 51312 2011-08-30 18:29 /lib/firmware/ar9271.fw
```

---

### Post by vagrale13 on 2011-08-31
**@[carlomagn0]("http://ubuntuforums.org/member.php?u=1050404")**
Maybe something going wrong with the driver... 
Can you try with the last compat-wireless?

If you don' t know how-to, open terminal and run the follwing commands (you must have internet conection)
```
wget http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2.6.tar.bz2 -O compat-wireless-2.6.tar.bz2
``````
tar jxvf compat-wireless-2.6.tar.bz2
``````
cd compat-wireless-*
``````
./scripts/driver-select ath9k_htc
``````
make && sudo make install
```Then reboot  and see if it works!

---

### Post by gad241 on 2011-10-25
I got my Netgear WNA1100 working using the ath9k_htc_installer on the second try. On the first try I let the installer do its thing and rebooted the machine. Still no wireless. Removed the ath9k_htc_installer through Synaptic. I then went to this website:
 [http://linuxwireless.org/en/users/Drivers/ath9k_htc#Configuring_your_kernel]("http://linuxwireless.org/en/users/Drivers/ath9k_htc#Configuring_your_kernel")

downloaded the two htc drivers (AR9271 - htc_9271.fw and AR7010 - htc_7010.fw) and dumped them in the /lib/firmware directory.

Ran the ath9k_htc_installer again, machine rebooted. Wireless connection established. I imagine that the ath9k installer is loading these same drivers but the first go around didn't work for me.

---

### Post by DaveZppln on 2011-11-19
Snoopy-2009 said the WNA1100 has out-of-the-box support for 11.04. Does anyone know if this is the case for 11.10??

---

### Post by thetruckinglife on 2011-11-27
installation worked with Netgear WNA1100
after doing a clean install of Ubuntu 10.10 
i copied the ath9k_htc-installer.1.0.1-maverick-fixed.deb from my sd card to my Downloads folder.
opened the installer and software center opens up and installs the program
when done it will show a reinstall button in the software center
go to applications menu sytem tools and click on ath9k_htc-installer
it does take a few minutes to install just be patiient.
when it is done click on restart.
when the desktop is back up plug in your usb card the system should recognize your card and say wireless networks available.

have not read this entire thread so this may already be posted.
just happy i am able to use Ubuntu 10.10 again.
now for some them customizing and compiz fun :lolflag:

---

### Post by thetruckinglife on 2011-11-27
> **DaveZppln said:**
> Snoopy-2009 said the WNA1100 has out-of-the-box support for 11.04. Does anyone know if this is the case for 11.10??

hmm not sure what out of the box means but when i did a clean install of Ubuntu 11.10 (when it was released) my wna1100 was up and ready
i put my card in the usb slot then did the install and when it was done wireless networks were available for use.

---

### Post by owlcroft on 2011-12-10
I am very frustrated.  Let me present the situation.  Ubuntu 10.10, clean install (some while ago).

From this URL--

**[http://sourceforge.net/projects/ath9k-htc/files/ath9k_htc-installer-Ubuntu%20Maverick%2010.10-fixed/](http://sourceforge.net/projects/ath9k-htc/files/ath9k_htc-installer-Ubuntu%20Maverick%2010.10-fixed/)**

--I downloaded this .deb package:

**ath9k_htc-installer.1.0.1-maverick-fixed.deb** 	2010-10-18

I double-clicked it, Software Center came up, I clicked Install, and it installed right off.  I then went to the menu and activated the installer program, which appeared to run fine, then rebooted.

In fact, everything looks fine, except that the WNA1100 blue light doesn't come on, and Network Manager reports no wireless connections.

My Linux kernel is 2.6.35-31-generic (the latest, I believe).  Here are the outputs of some of the commands I see often wanted for diagnostics:

```
**lsusb**
Bus 010 Device 002: ID 04f9:0028 Brother Industries, Ltd Printer
Bus 010 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 009 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 046d:c404 Logitech, Inc. TrackMan Wheel
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 0846:9030 NetGear, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

```
**iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
```

```
**dmesg | grep ath**
[   11.515998] usbcore: registered new interface driver ath9k_hif_usb
[  106.224804] usb 2-1: ath9k_htc: Transferred FW: ar9271.fw, size: 51280
[  106.489789] usb 2-1: ath9k_htc: HTC initialized with 33 credits
[  106.960758] ath: EEPROM regdomain: 0x60
[  106.960762] ath: EEPROM indicates we should expect a direct regpair map
[  106.960767] ath: Country alpha2 being used: 00
[  106.960770] ath: Regpair used: 0x60
[  107.009840] Registered led device: ath9k-phy0::radio
[  107.009883] Registered led device: ath9k-phy0::assoc
[  107.009923] Registered led device: ath9k-phy0::tx
[  107.009968] Registered led device: ath9k-phy0::rx
[  107.009973] usb 2-1: ath9k_htc: USB layer initialized
[  919.343372] usb 2-1: ath9k_htc: USB layer deinitialized
[  930.807366] usb 2-1: ath9k_htc: Transferred FW: ar9271.fw, size: 51280
[  931.072365] usb 2-1: ath9k_htc: HTC initialized with 33 credits
[  931.553635] ath: EEPROM regdomain: 0x60
[  931.553639] ath: EEPROM indicates we should expect a direct regpair map
[  931.553644] ath: Country alpha2 being used: 00
[  931.553646] ath: Regpair used: 0x60
[  931.558162] Registered led device: ath9k-phy1::radio
[  931.558204] Registered led device: ath9k-phy1::assoc
[  931.558249] Registered led device: ath9k-phy1::tx
[  931.558286] Registered led device: ath9k-phy1::rx
[  931.558291] usb 2-1: ath9k_htc: USB layer initialized
```

```
**lsmod | grep ath9k**
ath9k_htc              48888  0 
mac80211              274352  1 ath9k_htc
led_class               3393  1 ath9k_htc
ath9k_common            3143  1 ath9k_htc
ath9k_hw              306666  2 ath9k_htc,ath9k_common
ath                    16045  2 ath9k_htc,ath9k_hw
cfg80211              164649  3 ath9k_htc,mac80211,ath
```

```
**cat /etc/modules**
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
rtc
sg

# Generated by sensors-detect on Wed Dec 22 14:39:56 2010
# Chip drivers
it87

ath9k_htc
```

```
**ls -l /lib/firmware/ar***
-rw-r--r-- 1 root root 70624 2011-02-18 10:04 /lib/firmware/ar7010_1_1.fw
-rw-r--r-- 1 root root 70608 2010-08-29 17:12 /lib/firmware/ar7010.fw
-rw-r--r-- 1 root root 83968 2010-12-13 12:01 /lib/firmware/ar9170-1.fw
-rw-r--r-- 1 root root  3508 2010-12-13 12:01 /lib/firmware/ar9170-2.fw
-rw-r--r-- 1 root root 15960 2010-12-13 12:01 /lib/firmware/ar9170.fw
-rw-r--r-- 1 root root 51280 2010-12-13 12:01 /lib/firmware/ar9271.fw
```

In the directory **/lib/firmware/** are (among others) these files:

```
-rw-r--r--  1 root root   70624 2011-02-18 10:04 ar7010_1_1.fw
-rw-r--r--  1 root root   70608 2010-08-29 17:12 ar7010.fw
-rw-r--r--  1 root root   83968 2010-12-13 12:01 ar9170-1.fw
-rw-r--r--  1 root root    3508 2010-12-13 12:01 ar9170-2.fw
-rw-r--r--  1 root root   15960 2010-12-13 12:01 ar9170.fw
-rw-r--r--  1 root root   51280 2010-12-13 12:01 ar9271.fw
drwxr-xr-x  2 root root    4096 2010-12-13 12:01 ath3k-1.fw
-rw-r--r--  1 root root  246804 2010-12-13 12:01 ath3k-2.fw
-rw-r--r--  1 eric eric   72992 2011-12-10 15:35 htc_7010.fw
-rw-r--r--  1 root root   51272 2011-12-09 17:02 htc_9271.fw
```

Any ideas or help?  Please?

---

### Post by vagrale13 on 2011-12-17
[B]@[owlcroft]("http://ubuntuforums.org/member.php?u=40290")
[/B]Strange, must be works!:confused:
Maybe you can try with the last driver changes.
For how to see here [http://ubuntuforums.org/showpost.php?p=11205958&postcount=47](http://ubuntuforums.org/showpost.php?p=11205958&postcount=47)
and then reboot, and see if it works!

---

### Post by owlcroft on 2011-12-17
Thank you.  I'll give it a try soon now, and report results here.

---

### Post by owlcroft on 2011-12-17
Well, I looked more closely and I am not at present using compat-wireless, and I do have the very latest kernel installed.  I am reluctant to add compat-wireless in when, from its documentation, it appears intended only to provide backwards support for older kernels.

From the various data readouts above, is there anything at all that doesn't look right?

---

### Post by vviinnccee on 2012-01-03
Hello,

It seems to me that I am in a situation similar to [post 42]("http://ubuntuforums.org/showpost.php?p=11176925&postcount=42"), since I have a clean 10.04 32 bit install. It's on an old computer (evo n800v). It's also a netgear WNA1100. I have tried several configurations, and here are the results.

In all the following situations, I am using
[LIST]
[*]version 1.3 of htc_9271.fw and htc_7010.fw in /lib/firmware, as available here : [http://linuxwireless.org/download/htc_fw/](http://linuxwireless.org/download/htc_fw/)
[*]ar9271.fw as in [post 45]("http://ubuntuforums.org/showpost.php?p=11183178&postcount=45"), also in /lib/firmware
[/LIST]

I also have different results of lsusb, depending of ... something (but I don't know what).

Sometimes this
```
lsusb
Bus 001 Device 002: ID 0cf3:9271 Atheros Communications, Inc. 
```

or sometimes this
```
lsusb
Bus 001 Device 003: ID 0846:9030 NetGear, Inc.

```


_**v1.0.4 of the package**_: not working

In kern.log
```
[   84.220142] usb 1-1: new high speed USB device using ehci_hcd and address 2
[   84.354023] usb 1-1: configuration #1 chosen from 1 choice
```

and that's all ... the firmware is not loading, nothing

```
lsusb
Bus 001 Device 002: ID 0cf3:9271 Atheros Communications, Inc. 
```


_**v1.0.3**_: works sometimes

After the first restart, I plugged and it was working

```
[  105.296101] usb 1-1: new high speed USB device using ehci_hcd and address 2
[  105.446566] usb 1-1: configuration #1 chosen from 1 choice
[  105.818366] usb 1-1: ath9k_htc: Transferred FW: htc_9271.fw, size: 51272
[  106.054488] ath9k_htc 1-1:1.0: ath9k_htc: HTC initialized with 33 credits
[  106.264220] ath9k_htc 1-1:1.0: ath9k_htc: FW Version: 1.3
[  106.264230] ath: EEPROM regdomain: 0x60
[  106.264237] ath: EEPROM indicates we should expect a direct regpair map
[  106.264247] ath: Country alpha2 being used: 00
[  106.264254] ath: Regpair used: 0x60
[  106.264266] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[  106.264276] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (N/A mBi, 2000 mBm)
(...)
[  106.267527] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[  106.395490] ieee80211 phy0: Atheros AR9271 Rev:1
[  106.405166] Registered led device: ath9k_htc-phy0
[  106.405178] usb 1-1: ath9k_htc: USB layer initialized
[  106.598553] ADDRCONF(NETDEV_UP): wlan%d: link is not ready
```

Working also after I unpluged and re-pluged again, several times.

Also:
```
lsusb
Bus 001 Device 003: ID 0846:9030 NetGear, Inc. 
```

Second restart: (with the device plugged in during the restart)

It was working, but after an unplug and a re-plug, was not working anymore.

```
[  115.680183] usb 1-1: new high speed USB device using ehci_hcd and address 3
[  115.829418] usb 1-1: configuration #1 chosen from 1 choice
[  116.155647] usb 1-1: ath9k_htc: Transferred FW: htc_9271.fw, size: 51272
[  116.391644] ath9k_htc 1-1:1.0: ath9k_htc: HTC initialized with 33 credits
[  116.545517] ath: Invalid EEPROM Magic. Endianness mismatch.
[  116.545534] ath: Unable to initialize hardware; initialization status: -22
[  116.545546] ath: Unable to initialize hardware; initialization status: -22
[  116.545570] Failed to initialize the device
[  116.555420] ath9k_htc: probe of 1-1:1.0 failed with error -22

```

```
lsusb
Bus 001 Device 003: ID 0846:9030 NetGear, Inc. 
```

Sometimes it's the following error:

```
[ 2994.096182] usb 1-1: new high speed USB device using ehci_hcd and address 6
[ 2994.230315] usb 1-1: configuration #1 chosen from 1 choice
[ 2994.554475] usb 1-1: ath9k_htc: Transferred FW: htc_9271.fw, size: 51272
[ 2994.790608] ath9k_htc 1-1:1.0: ath9k_htc: HTC initialized with 33 credits
[ 2994.943605] ath: Bad EEPROM checksum 0x43e5 or revision 0x000f
[ 2994.943624] ath: Unable to initialize hardware; initialization status: -22
[ 2994.943636] ath: Unable to initialize hardware; initialization status: -22
[ 2994.943660] Failed to initialize the device
[ 2994.953945] ath9k_htc: probe of 1-1:1.0 failed with error -22

```

I experienced this behaviour several times with this version 1.0.3 : it was working after the first restart, but not after the second restart (whever the device was plugged or not during the restart)

_**v1.0.2**_: not working at all (first restart and after)

```
[  363.340172] usb 1-1: new high speed USB device using ehci_hcd and address 3
[  363.474499] usb 1-1: configuration #1 chosen from 1 choice
[  363.798504] usb 1-1: ath9k_htc: Transferred FW: ar9271.fw, size: 51312
[  364.064617] usb 1-1: ath9k_htc: HTC initialized with 33 credits
[  364.232657] ath: Invalid EEPROM Magic. Endianness mismatch.
[  364.232673] ath: Unable to initialize hardware; initialization status: -22
[  364.232685] ath: Unable to initialize hardware; initialization status: -22
[  364.232709] Failed to initialize the device
[  364.233928] ath9k_hif_usb: probe of 1-1:1.0 failed with error -22
```

**_v1.0.0_**: not working at all (first restart and after)

```
[  125.168171] usb 1-1: new high speed USB device using ehci_hcd and address 3
[  125.302501] usb 1-1: configuration #1 chosen from 1 choice
[  125.629265] usb 1-1: ath9k_htc: Transferred FW: ar9271.fw, size: 51280
[  125.897252] usb 1-1: ath9k_htc: HTC initialized with 33 credits
[  126.297162] Failed to initialize the device
[  126.298285] ath9k_hif_usb: probe of 1-1:1.0 failed with error -22
```


**_Last compat-wireless_**, as in [post 47]("http://ubuntuforums.org/showpost.php?p=11205958&postcount=47"):
```
[   53.376142] usb 1-1: new high speed USB device using ehci_hcd and address 2
[   53.509958] usb 1-1: configuration #1 chosen from 1 choice
[   53.926294] usb 1-1: ath9k_htc: Transferred FW: htc_9271.fw, size: 51272
[   54.162159] ath9k_htc 1-1:1.0: ath9k_htc: HTC initialized with 33 credits
[   54.329489] ath: Invalid EEPROM Magic. Endianness mismatch.
[   54.329500] ath: Unable to initialize hardware; initialization status: -22
[   54.329507] ath: Unable to initialize hardware; initialization status: -22
[   54.329529] Failed to initialize the device
[   54.338768] ath9k_htc: probe of 1-1:1.0 failed with error -22
```

```
lsusb
Bus 001 Device 003: ID 0cf3:9271 Atheros Communications, Inc.
```

I'm thinking of buying thinkpenguin's usb wifi, since the netgear wna1100 is the second usb wifi I try on Ubuntu, spending a lot of time in this ... I hate netgear now. And D-Link. And all the others.

Don't hesitate to tell me if you want me to try some things.

Vincent

---

### Post by srijit92 on 2012-11-22
I have Netgear WNA1100 (Athreos 9271) based USB WiFi DOngle. I cannot start wlan0.I have installed the required firmware in /lib/firmware. OS is Ubuntu Server 12.04

Following are my configurations:

root@ubuntu:~# lsmod | grep ath9k
ath9k_htc              90811  0
mac80211              436455  1 ath9k_htc
ath9k_common           13781  1 ath9k_htc
ath9k_hw              391554  2 ath9k_htc,ath9k_common
ath                    19387  3 ath9k_htc,ath9k_common,ath9k_hw
cfg80211              178679  3 ath9k_htc,mac80211,ath



/network/interfaces

# The loopback network interface
auto lo eth0
iface lo inet loopback

# The primary network interface
iface eth0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


root@ubuntu:~# lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0846:9030 NetGear, Inc. WNA1100 Wireless-N 150 [Atheros AR9271]

root@ubuntu:~# iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

eth0      no wireless extensions.

---

