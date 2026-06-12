---
title: "Dmesg for System76 laptops"
date: 2009-11-25
forum: System76 Support
---

### Post by topher80 on 2009-11-25
Anyone who owns a System76 laptop, can you please post your dmesg here. I asked thomasaaron a few days ago but he never responded. I would like to purchase one of these laptops but I also want to boot one of the BSDs on it and I'd like to see what is compatible and what is not before purchasing.

Thanks!

---

### Post by thomasaaron on 2009-11-25
Did you get *no* response from me? I remember sending an email with dmidecode, lspci and lsusb to someone, but I can't tell for sure if it was you.

If you have a yahoo email address, check your spam folder.

Otherwise you can call me, and we'll try to figure it out.

I don't think dmesg is going to give you what you are looking for. dmesg is kernel output, not a hardware list.

If I'm understanding your needs correctly, you will need dmidecode, lspci and lsusb.


EDIT:

Actually, I see three emails from you. One is asking my recommendation on a desktop for a graphics designer (which I answered), and two announcing a change of address.

You might want to send me a test email to see if I'm getting them from your new email address.

---

### Post by topher80 on 2009-11-25
Hi,

Sorry I have only PM'ed you once about this... I haven't emailed you regarding this issue. 

Here is an example of the sort of thing I'm looking for specifically from the Lemur 

[http://www.openbsd-wiki.org/index.php?title=Dmesg](http://www.openbsd-wiki.org/index.php?title=Dmesg)

If dmidecode, lspci and lsusb provide all this info, then great! I will PM you my email address. 

Thanks!

---

### Post by thomasaaron on 2009-11-25
Hi, that explains it.

I never check PMs. I can barely keep up with emails, forum posts and testing.

In the meantime... you're right, that is a dmesg output. Ubuntu's dmesg is attached.

---

### Post by topher80 on 2009-11-25
I don't think the attachment worked... post again please.

---

### Post by thomasaaron on 2009-11-25
Let's do it this way, then...

> [    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.31-15-generic (buildd@yellow) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #50-Ubuntu SMP Tue Nov 10 14:53:52 UTC 2009 (Ubuntu 2.6.31-15.50-generic)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-15-generic root=UUID=79ccda19-264b-47cb-84b3-8d31ecffdb5c ro quiet splash acpi_os_name=Linux acpi_osi=
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009d400 (usable)
[    0.000000]  BIOS-e820: 000000000009d400 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d2000 - 00000000000d4000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007d6a1000 (usable)
[    0.000000]  BIOS-e820: 000000007d6a1000 - 000000007d6a7000 (reserved)
[    0.000000]  BIOS-e820: 000000007d6a7000 - 000000007d7ba000 (usable)
[    0.000000]  BIOS-e820: 000000007d7ba000 - 000000007d80f000 (reserved)
[    0.000000]  BIOS-e820: 000000007d80f000 - 000000007d908000 (usable)
[    0.000000]  BIOS-e820: 000000007d908000 - 000000007db0f000 (reserved)
[    0.000000]  BIOS-e820: 000000007db0f000 - 000000007db19000 (usable)
[    0.000000]  BIOS-e820: 000000007db19000 - 000000007db1f000 (reserved)
[    0.000000]  BIOS-e820: 000000007db1f000 - 000000007db64000 (usable)
[    0.000000]  BIOS-e820: 000000007db64000 - 000000007db9f000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007db9f000 - 000000007dbe4000 (usable)
[    0.000000]  BIOS-e820: 000000007dbe4000 - 000000007dbff000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007dbff000 - 000000007dc00000 (usable)
[    0.000000]  BIOS-e820: 000000007dc00000 - 000000007de00000 (reserved)
[    0.000000]  BIOS-e820: 000000007e000000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  BIOS-e820: 00000000fed10000 - 00000000fed14000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed18000 - 00000000fed1a000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff800000 - 0000000100000000 (reserved)
[    0.000000] DMI present.
[    0.000000] Phoenix BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0x7dc00 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 07E000000 mask FFE000000 uncachable
[    0.000000]   1 base 000000000 mask F80000000 write-back
[    0.000000]   2 base 0FFE00000 mask FFFE00000 write-protect
[    0.000000]   3 base 07DE00000 mask FFFE00000 uncachable
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009d400 (usable)
[    0.000000]  modified: 000000000009d400 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000d2000 - 00000000000d4000 (reserved)
[    0.000000]  modified: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000007d6a1000 (usable)
[    0.000000]  modified: 000000007d6a1000 - 000000007d6a7000 (reserved)
[    0.000000]  modified: 000000007d6a7000 - 000000007d7ba000 (usable)
[    0.000000]  modified: 000000007d7ba000 - 000000007d80f000 (reserved)
[    0.000000]  modified: 000000007d80f000 - 000000007d908000 (usable)
[    0.000000]  modified: 000000007d908000 - 000000007db0f000 (reserved)
[    0.000000]  modified: 000000007db0f000 - 000000007db19000 (usable)
[    0.000000]  modified: 000000007db19000 - 000000007db1f000 (reserved)
[    0.000000]  modified: 000000007db1f000 - 000000007db64000 (usable)
[    0.000000]  modified: 000000007db64000 - 000000007db9f000 (ACPI NVS)
[    0.000000]  modified: 000000007db9f000 - 000000007dbe4000 (usable)
[    0.000000]  modified: 000000007dbe4000 - 000000007dbff000 (ACPI data)
[    0.000000]  modified: 000000007dbff000 - 000000007dc00000 (usable)
[    0.000000]  modified: 000000007dc00000 - 000000007de00000 (reserved)
[    0.000000]  modified: 000000007e000000 - 0000000080000000 (reserved)
[    0.000000]  modified: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  modified: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  modified: 00000000fed00000 - 00000000fed00400 (reserved)
[    0.000000]  modified: 00000000fed10000 - 00000000fed14000 (reserved)
[    0.000000]  modified: 00000000fed18000 - 00000000fed1a000 (reserved)
[    0.000000]  modified: 00000000fed1c000 - 00000000fed90000 (reserved)
[    0.000000]  modified: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  modified: 00000000ff800000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] init_memory_mapping: 0000000000000000-000000007dc00000
[    0.000000] NX (Execute Disable) protection: active
[    0.000000]  0000000000 - 007dc00000 page 2M
[    0.000000] kernel direct mapping tables up to 7dc00000 @ 10000-13000
[    0.000000] RAMDISK: 37833000 - 37fef10f
[    0.000000] ACPI: RSDP 00000000000f7800 00024 (v02 PTLTD )
[    0.000000] ACPI: XSDT 000000007dbf888e 00064 (v01 PTLTD  	 XSDT   06040000  LTP 00000000)
[    0.000000] ACPI: FACP 000000007dbe8000 000F4 (v03 INTEL  CRESTLNE 06040000 ALAN 00000001)
[    0.000000] ACPI: DSDT 000000007dbe9000 0647A (v02 Intel  CANTIGA  06040000 INTL 20050624)
[    0.000000] ACPI: FACS 000000007db9efc0 00040
[    0.000000] ACPI: HPET 000000007dbfeefc 00038 (v01 INTEL  CRESTLNE 06040000 LOHR 0000005A)
[    0.000000] ACPI: MCFG 000000007dbfef34 0003C (v01 INTEL  CRESTLNE 06040000 LOHR 0000005A)
[    0.000000] ACPI: APIC 000000007dbfef70 00068 (v01 PTLTD  	 APIC   06040000  LTP 00000000)
[    0.000000] ACPI: BOOT 000000007dbfefd8 00028 (v01 PTLTD  $SBFTBL$ 06040000  LTP 00000001)
[    0.000000] ACPI: SSDT 000000007dbe7000 00655 (v01  PmRef    CpuPm 00003000 INTL 20050624)
[    0.000000] ACPI: SSDT 000000007dbe6000 00259 (v01  PmRef  Cpu0Tst 00003000 INTL 20050624)
[    0.000000] ACPI: SSDT 000000007dbe5000 0020F (v01  PmRef    ApTst 00003000 INTL 20050624)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000007dc00000
[    0.000000] Bootmem setup node 0 0000000000000000-000000007dc00000
[    0.000000]   NODE_DATA [0000000000011000 - 0000000000015fff]
[    0.000000]   bootmap [0000000000016000 -  0000000000025b7f] pages 10
[    0.000000] (7 early reservations) ==> bootmem [0000000000 - 007dc00000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
[    0.000000]   #2 [0001000000 - 00019e4ccc]    TEXT DATA BSS ==> [0001000000 - 00019e4ccc]
[    0.000000]   #3 [0037833000 - 0037fef10f]          RAMDISK ==> [0037833000 - 0037fef10f]
[    0.000000]   #4 [000009d400 - 0000100000]    BIOS reserved ==> [000009d400 - 0000100000]
[    0.000000]   #5 [00019e5000 - 00019e5238]              BRK ==> [00019e5000 - 00019e5238]
[    0.000000]   #6 [0000010000 - 0000011000]          PGTABLE ==> [0000010000 - 0000011000]
[    0.000000] found SMP MP-table at [ffff8800000f7890] f7890
[    0.000000]  [ffffea0000000000-ffffea0001bfffff] PMD -> [ffff880001e00000-ffff8800039fffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00100000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[8] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009d
[    0.000000]     0: 0x00000100 -> 0x0007d6a1
[    0.000000]     0: 0x0007d6a7 -> 0x0007d7ba
[    0.000000]     0: 0x0007d80f -> 0x0007d908
[    0.000000]     0: 0x0007db0f -> 0x0007db19
[    0.000000]     0: 0x0007db1f -> 0x0007db64
[    0.000000]     0: 0x0007db9f -> 0x0007dbe4
[    0.000000]     0: 0x0007dbff -> 0x0007dc00
[    0.000000] On node 0 totalpages: 514255
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 102 pages reserved
[    0.000000]   DMA zone: 3823 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 6986 pages used for memmap
[    0.000000]   DMA32 zone: 503288 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 000000000009d000 - 000000000009e000
[    0.000000] PM: Registered nosave memory: 000000000009e000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000d2000
[    0.000000] PM: Registered nosave memory: 00000000000d2000 - 00000000000d4000
[    0.000000] PM: Registered nosave memory: 00000000000d4000 - 00000000000e4000
[    0.000000] PM: Registered nosave memory: 00000000000e4000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 000000007d6a1000 - 000000007d6a7000
[    0.000000] PM: Registered nosave memory: 000000007d7ba000 - 000000007d80f000
[    0.000000] PM: Registered nosave memory: 000000007d908000 - 000000007db0f000
[    0.000000] PM: Registered nosave memory: 000000007db19000 - 000000007db1f000
[    0.000000] PM: Registered nosave memory: 000000007db64000 - 000000007db9f000
[    0.000000] PM: Registered nosave memory: 000000007dbe4000 - 000000007dbff000
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 80000000:60000000)
[    0.000000] NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 30 pages at ffff8800019f7000, static data 90720 bytes
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 507111
[    0.000000] Policy zone: DMA32
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-15-generic root=UUID=79ccda19-264b-47cb-84b3-8d31ecffdb5c ro quiet splash acpi_os_name=Linux acpi_osi=
[    0.000000] ACPI: _OSI method disabled
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] xsave/xrstor: enabled xstate_bv 0x3, cntxt size 0x240
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 2009892k/2060288k available (5315k kernel code, 3268k absent, 47128k reserved, 3018k data, 660k init)
[    0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] NR_IRQS:4352 nr_irqs:424
[    0.000000] Extended CMOS year: 2000
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1296.709 MHz processor.
[    0.001281] Console: colour VGA+ 80x25
[    0.001285] console [tty0] enabled
[    0.010000] allocated 20971520 bytes of page_cgroup
[    0.010000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.010000] hpet clockevent registered
[    0.010000] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
[    0.010000] Calibrating delay loop (skipped), value calculated using timer frequency.. 2593.41 BogoMIPS (lpj=12967090)
[    0.010000] Security Framework initialized
[    0.010000] AppArmor: AppArmor initialized
[    0.010000] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.010000] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.010000] Mount-cache hash table entries: 256
[    0.010000] Initializing cgroup subsys ns
[    0.010000] Initializing cgroup subsys cpuacct
[    0.010000] Initializing cgroup subsys memory
[    0.010000] Initializing cgroup subsys freezer
[    0.010000] Initializing cgroup subsys net_cls
[    0.010000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.010000] CPU: L2 cache: 3072K
[    0.010000] CPU 0/0x0 -> Node 0
[    0.010000] CPU: Physical Processor ID: 0
[    0.010000] CPU: Processor Core ID: 0
[    0.010000] mce: CPU supports 6 MCE banks
[    0.010000] CPU0: Thermal monitoring enabled (TM2)
[    0.010000] using mwait in idle threads.
[    0.010000] Performance Counters: Core2 events, Intel PMU driver.
[    0.010000] ... version:                 2
[    0.010000] ... bit width:               40
[    0.010000] ... generic counters:        2
[    0.010000] ... value mask:              000000ffffffffff
[    0.010000] ... max period:              000000007fffffff
[    0.010000] ... fixed-purpose counters:  3
[    0.010000] ... counter mask:            0000000700000003
[    0.010000] ACPI: Core revision 20090521
[    0.010000] ACPI: Overriding _OS definition to 'Linux'
[    0.020080] Setting APIC routing to flat
[    0.020446] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.132947] CPU0: Genuine Intel(R) CPU           U7300  @ 1.30GHz stepping 0a
[    0.140000] Booting processor 1 APIC 0x1 ip 0x6000
[    0.010000] Initializing CPU#1
[    0.010000] Calibrating delay using timer specific routine.. 2593.50 BogoMIPS (lpj=12967541)
[    0.010000] CPU: L1 I cache: 32K, L1 D cache: 32K
[    0.010000] CPU: L2 cache: 3072K
[    0.010000] CPU 1/0x1 -> Node 0
[    0.010000] CPU: Physical Processor ID: 0
[    0.010000] CPU: Processor Core ID: 1
[    0.010000] mce: CPU supports 6 MCE banks
[    0.010000] CPU1: Thermal monitoring enabled (TM2)
[    0.010000] x86 PAT enabled: cpu 1, old 0x7040600070406, new 0x7010600070106
[    0.292105] CPU1: Genuine Intel(R) CPU           U7300  @ 1.30GHz stepping 0a
[    0.292117] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[    0.300025] Brought up 2 CPUs
[    0.300029] Total of 2 processors activated (5186.92 BogoMIPS).
[    0.300089] CPU0 attaching sched-domain:
[    0.300094]  domain 0: span 0-1 level MC
[    0.300097]   groups: 0 1
[    0.300105] CPU1 attaching sched-domain:
[    0.300108]  domain 0: span 0-1 level MC
[    0.300111]   groups: 1 0
[    0.300207] Booting paravirtualized kernel on bare hardware
[    0.300263] regulator: core version 0.5
[    0.300263] Time:  3:31:14  Date: 11/25/09
[    0.300263] NET: Registered protocol family 16
[    0.300295] ACPI: bus type pci registered
[    0.300407] PCI: MCFG configuration 0: base e0000000 segment 0 buses 0 - 255
[    0.300411] PCI: MCFG area at e0000000 reserved in E820
[    0.315950] PCI: Using MMCONFIG at e0000000 - efffffff
[    0.315953] PCI: Using configuration type 1 for base access
[    0.317212] bio: create slab <bio-0> at 0
[    0.317212] ACPI: EC: Look up EC in DSDT
[    0.320021] ACPI: EC: non-query interrupt received, switching to interrupt mode
[    0.340258] ACPI: Interpreter enabled
[    0.340264] ACPI: (supports S0 S3 S4 S5)
[    0.340297] ACPI: Using IOAPIC for interrupt routing
[    0.350438] ACPI: EC: GPE = 0x17, I/O: command/status = 0x66, data = 0x62
[    0.350442] ACPI: EC: driver started in interrupt mode
[    0.350817] ACPI: No dock devices found.
[    0.351633] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.351760] pci 0000:00:02.0: reg 10 64bit mmio: [0xf8000000-0xf83fffff]
[    0.351771] pci 0000:00:02.0: reg 18 64bit mmio: [0xd0000000-0xdfffffff]
[    0.351778] pci 0000:00:02.0: reg 20 io port: [0x1800-0x1807]
[    0.351832] pci 0000:00:02.1: reg 10 64bit mmio: [0xf8400000-0xf84fffff]
[    0.351998] pci 0000:00:1a.0: reg 20 io port: [0x1820-0x183f]
[    0.352104] pci 0000:00:1a.1: reg 20 io port: [0x1840-0x185f]
[    0.352210] pci 0000:00:1a.2: reg 20 io port: [0x1860-0x187f]
[    0.352321] pci 0000:00:1a.7: reg 10 32bit mmio: [0xf8904800-0xf8904bff]
[    0.352398] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.352405] pci 0000:00:1a.7: PME# disabled
[    0.352471] pci 0000:00:1b.0: reg 10 64bit mmio: [0xf8700000-0xf8703fff]
[    0.352541] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.352547] pci 0000:00:1b.0: PME# disabled
[    0.352646] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.352652] pci 0000:00:1c.0: PME# disabled
[    0.352755] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.352761] pci 0000:00:1c.1: PME# disabled
[    0.352865] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.352872] pci 0000:00:1c.4: PME# disabled
[    0.352959] pci 0000:00:1d.0: reg 20 io port: [0x1880-0x189f]
[    0.353063] pci 0000:00:1d.1: reg 20 io port: [0x18a0-0x18bf]
[    0.353185] pci 0000:00:1d.2: reg 20 io port: [0x18c0-0x18df]
[    0.353307] pci 0000:00:1d.7: reg 10 32bit mmio: [0xf8904c00-0xf8904fff]
[    0.353385] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.353392] pci 0000:00:1d.7: PME# disabled
[    0.353665] pci 0000:00:1f.2: reg 10 io port: [0x1818-0x181f]
[    0.353674] pci 0000:00:1f.2: reg 14 io port: [0x180c-0x180f]
[    0.353684] pci 0000:00:1f.2: reg 18 io port: [0x1810-0x1817]
[    0.353694] pci 0000:00:1f.2: reg 1c io port: [0x1808-0x180b]
[    0.353704] pci 0000:00:1f.2: reg 20 io port: [0x18e0-0x18ff]
[    0.353714] pci 0000:00:1f.2: reg 24 32bit mmio: [0xf8904000-0xf89047ff]
[    0.353769] pci 0000:00:1f.2: PME# supported from D3hot
[    0.353775] pci 0000:00:1f.2: PME# disabled
[    0.353824] pci 0000:00:1f.3: reg 10 64bit mmio: [0x000000-0x0000ff]
[    0.353846] pci 0000:00:1f.3: reg 20 io port: [0x1c00-0x1c1f]
[    0.353980] pci 0000:02:00.0: reg 10 64bit mmio: [0xf8500000-0xf8501fff]
[    0.354104] pci 0000:02:00.0: PME# supported from D0 D3hot D3cold
[    0.354113] pci 0000:02:00.0: PME# disabled
[    0.354206] pci 0000:00:1c.0: bridge 32bit mmio: [0xf8500000-0xf85fffff]
[    0.354277] pci 0000:00:1c.1: bridge io port: [0x2000-0x2fff]
[    0.354283] pci 0000:00:1c.1: bridge 32bit mmio: [0xf4000000-0xf7ffffff]
[    0.354294] pci 0000:00:1c.1: bridge 64bit mmio pref: [0xf0000000-0xf3ffffff]
[    0.354357] pci 0000:06:00.0: reg 10 32bit mmio: [0xf8604000-0xf86040ff]
[    0.354535] pci 0000:06:00.2: reg 10 32bit mmio: [0xf8604400-0xf86044ff]
[    0.354710] pci 0000:06:00.3: reg 10 32bit mmio: [0xf8604800-0xf86048ff]
[    0.354884] pci 0000:06:00.5: reg 10 32bit mmio: [0xf8600000-0xf8603fff]
[    0.354906] pci 0000:06:00.5: reg 18 io port: [0x3400-0x347f]
[    0.354918] pci 0000:06:00.5: reg 1c io port: [0x3000-0x30ff]
[    0.354997] pci 0000:06:00.5: PME# supported from D0 D3hot D3cold
[    0.355005] pci 0000:06:00.5: PME# disabled
[    0.355089] pci 0000:00:1c.4: bridge io port: [0x3000-0x3fff]
[    0.355096] pci 0000:00:1c.4: bridge 32bit mmio: [0xf8600000-0xf86fffff]
[    0.355179] pci 0000:00:1e.0: transparent bridge
[    0.355227] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.355451] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.355704] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.355813] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    0.355921] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP05._PRT]
[    0.371668] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 *5 6 7 10 12 14 15)
[    0.371825] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.371975] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[    0.372122] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.372270] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    0.372418] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    0.372566] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.372713] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 *7 11 12 14 15)
[    0.372951] SCSI subsystem initialized
[    0.372978] libata version 3.00 loaded.
[    0.372978] usbcore: registered new interface driver usbfs
[    0.372978] usbcore: registered new interface driver hub
[    0.372978] usbcore: registered new device driver usb
[    0.372978] ACPI: WMI: Mapper loaded
[    0.372978] PCI: Using ACPI for IRQ routing
[    0.400010] Bluetooth: Core ver 2.15
[    0.400031] NET: Registered protocol family 31
[    0.400031] Bluetooth: HCI device and connection manager initialized
[    0.400031] Bluetooth: HCI socket layer initialized
[    0.400031] NetLabel: Initializing
[    0.400031] NetLabel:  domain hash size = 128
[    0.400031] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.400048] NetLabel:  unlabeled traffic allowed by default
[    0.400117] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.400125] hpet0: 4 comparators, 64-bit 14.318180 MHz counter
[    0.440012] pnp: PnP ACPI init
[    0.440025] ACPI: bus type pnp registered
[    0.441293] pnp 00:05: io resource (0x3322-0x3323) overlaps 0000:00:1c.4 BAR 13 (0x3000-0x3fff), disabling
[    0.443281] pnp: PnP ACPI: found 10 devices
[    0.443285] ACPI: ACPI bus type pnp unregistered
[    0.443301] system 00:03: iomem range 0xfed00000-0xfed003ff has been reserved
[    0.443312] system 00:05: ioport range 0x680-0x69f has been reserved
[    0.443316] system 00:05: ioport range 0x400-0x47f has been reserved
[    0.443320] system 00:05: ioport range 0x480-0x48f has been reserved
[    0.443325] system 00:05: ioport range 0xffff-0xffff has been reserved
[    0.443329] system 00:05: ioport range 0xffff-0xffff has been reserved
[    0.443333] system 00:05: ioport range 0x1000-0x107f has been reserved
[    0.443337] system 00:05: ioport range 0x1180-0x11ff has been reserved
[    0.443345] system 00:05: ioport range 0x164e-0x164f has been reserved
[    0.443349] system 00:05: ioport range 0xfe00-0xfe00 has been reserved
[    0.443359] system 00:09: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    0.443364] system 00:09: iomem range 0xfed10000-0xfed13fff has been reserved
[    0.443368] system 00:09: iomem range 0xfed18000-0xfed18fff has been reserved
[    0.443372] system 00:09: iomem range 0xfed19000-0xfed19fff has been reserved
[    0.443376] system 00:09: iomem range 0xe0000000-0xefffffff has been reserved
[    0.443380] system 00:09: iomem range 0xfed20000-0xfed3ffff has been reserved
[    0.443385] system 00:09: iomem range 0xfed45000-0xfed8ffff has been reserved
[    0.448130] AppArmor: AppArmor Filesystem Enabled
[    0.448211] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
[    0.448214] pci 0000:00:1c.0:   IO window: disabled
[    0.448223] pci 0000:00:1c.0:   MEM window: 0xf8500000-0xf85fffff
[    0.448228] pci 0000:00:1c.0:   PREFETCH window: disabled
[    0.448235] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:04
[    0.448240] pci 0000:00:1c.1:   IO window: 0x2000-0x2fff
[    0.448248] pci 0000:00:1c.1:   MEM window: 0xf4000000-0xf7ffffff
[    0.448255] pci 0000:00:1c.1:   PREFETCH window: 0x000000f0000000-0x000000f3ffffff
[    0.448265] pci 0000:00:1c.4: PCI bridge, secondary bus 0000:06
[    0.448270] pci 0000:00:1c.4:   IO window: 0x3000-0x3fff
[    0.448278] pci 0000:00:1c.4:   MEM window: 0xf8600000-0xf86fffff
[    0.448285] pci 0000:00:1c.4:   PREFETCH window: disabled
[    0.448291] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:07
[    0.448293] pci 0000:00:1e.0:   IO window: disabled
[    0.448301] pci 0000:00:1e.0:   MEM window: disabled
[    0.448307] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.448322]   alloc irq_desc for 17 on node 0
[    0.448325]   alloc kstat_irqs on node 0
[    0.448331] pci 0000:00:1c.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.448339] pci 0000:00:1c.0: setting latency timer to 64
[    0.448349]   alloc irq_desc for 16 on node 0
[    0.448352]   alloc kstat_irqs on node 0
[    0.448357] pci 0000:00:1c.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    0.448363] pci 0000:00:1c.1: setting latency timer to 64
[    0.448374] pci 0000:00:1c.4: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.448380] pci 0000:00:1c.4: setting latency timer to 64
[    0.448390] pci 0000:00:1e.0: setting latency timer to 64
[    0.448396] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.448400] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]
[    0.448404] pci_bus 0000:02: resource 1 mem: [0xf8500000-0xf85fffff]
[    0.448408] pci_bus 0000:04: resource 0 io:  [0x2000-0x2fff]
[    0.448411] pci_bus 0000:04: resource 1 mem: [0xf4000000-0xf7ffffff]
[    0.448415] pci_bus 0000:04: resource 2 pref mem [0xf0000000-0xf3ffffff]
[    0.448418] pci_bus 0000:06: resource 0 io:  [0x3000-0x3fff]
[    0.448422] pci_bus 0000:06: resource 1 mem: [0xf8600000-0xf86fffff]
[    0.448426] pci_bus 0000:07: resource 3 io:  [0x00-0xffff]
[    0.448429] pci_bus 0000:07: resource 4 mem: [0x000000-0xffffffffffffffff]
[    0.448471] NET: Registered protocol family 2
[    0.448656] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
[    0.449716] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[    0.452132] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.452794] TCP: Hash tables configured (established 262144 bind 65536)
[    0.452798] TCP reno registered
[    0.452954] NET: Registered protocol family 1
[    0.453042] Trying to unpack rootfs image as initramfs...
[    0.502156] Switched to high resolution mode on CPU 1
[    0.510008] Switched to high resolution mode on CPU 0
[    0.739690] Freeing initrd memory: 7920k freed
[    0.744174] Simple Boot Flag at 0x36 set to 0x80
[    0.744437] Scanning for low memory corruption every 60 seconds
[    0.744638] audit: initializing netlink socket (disabled)
[    0.744663] type=2000 audit(1259119873.740:1): initialized
[    0.759818] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.761948] VFS: Disk quotas dquot_6.5.2
[    0.762033] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.762859] fuse init (API version 7.12)
[    0.762976] msgmni has been set to 3941
[    0.763255] alg: No test for stdrng (krng)
[    0.763274] io scheduler noop registered
[    0.763278] io scheduler anticipatory registered
[    0.763281] io scheduler deadline registered
[    0.763336] io scheduler cfq registered (default)
[    0.763352] pci 0000:00:02.0: Boot video device
[    0.763736]   alloc irq_desc for 24 on node 0
[    0.763740]   alloc kstat_irqs on node 0
[    0.763756] pcieport-driver 0000:00:1c.0: irq 24 for MSI/MSI-X
[    0.763770] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    0.764003]   alloc irq_desc for 25 on node 0
[    0.764006]   alloc kstat_irqs on node 0
[    0.764018] pcieport-driver 0000:00:1c.1: irq 25 for MSI/MSI-X
[    0.764032] pcieport-driver 0000:00:1c.1: setting latency timer to 64
[    0.764259]   alloc irq_desc for 26 on node 0
[    0.764262]   alloc kstat_irqs on node 0
[    0.764274] pcieport-driver 0000:00:1c.4: irq 26 for MSI/MSI-X
[    0.764288] pcieport-driver 0000:00:1c.4: setting latency timer to 64
[    0.764444] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.764618] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.765412] ACPI Error (psargs-0359): [\_PR_.CPU0._PSS] Namespace lookup failure, AE_NOT_FOUND
[    0.765459] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.AC__.ADJP] (Node ffff88007b331de0), AE_NOT_FOUND
[    0.765498] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.AC__._PSR] (Node ffff88007b331da0), AE_NOT_FOUND
[    0.765540] ACPI Exception: AE_NOT_FOUND, Error reading AC Adapter state 20090521 ac-138
[    0.765631] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    0.765636] ACPI: Power Button [PWRF]
[    0.765721] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.765730] ACPI: Power Button [PWRB]
[    0.765794] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    0.765802] ACPI: Sleep Button [SLPB]
[    0.765862] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input3
[    0.783127] ACPI: Lid Switch [LID0]
[    0.784309] ACPI: SSDT 000000007db1aca0 00223 (v01  PmRef  Cpu0Ist 00003000 INTL 20050624)
[    0.784999] ACPI: SSDT 000000007db196a0 005D7 (v01  PmRef  Cpu0Cst 00003001 INTL 20050624)
[    0.788425] Monitor-Mwait will be used to enter C-1 state
[    0.788462] Monitor-Mwait will be used to enter C-2 state
[    0.788493] Monitor-Mwait will be used to enter C-3 state
[    0.788504] Marking TSC unstable due to TSC halts in idle
[    0.788530] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    0.788564] processor LNXCPU:00: registered as cooling_device0
[    0.788570] ACPI: Processor [CPU0] (supports 8 throttling states)
[    0.789227] ACPI: SSDT 000000007db1aa20 001CF (v01  PmRef    ApIst 00003000 INTL 20050624)
[    0.789767] ACPI: SSDT 000000007db1af20 0008D (v01  PmRef    ApCst 00003000 INTL 20050624)
[    0.791169] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    0.791197] processor LNXCPU:01: registered as cooling_device1
[    0.791203] ACPI: Processor [CPU1] (supports 8 throttling states)
[    0.801724] thermal LNXTHERM:01: registered as thermal_zone0
[    0.801736] ACPI: Thermal Zone [TZ0] (25 C)
[    0.803453] Linux agpgart interface v0.103
[    0.803465] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.805170] brd: module loaded
[    0.805798] loop: module loaded
[    0.805895] input: Macintosh mouse button emulation as /devices/virtual/input/input4
[    0.806040] ahci 0000:00:1f.2: version 3.0
[    0.806057]   alloc irq_desc for 19 on node 0
[    0.806060]   alloc kstat_irqs on node 0
[    0.806068] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.806107]   alloc irq_desc for 27 on node 0
[    0.806110]   alloc kstat_irqs on node 0
[    0.806121] ahci 0000:00:1f.2: irq 27 for MSI/MSI-X
[    0.806167] ahci: SSS flag set, parallel bus scan disabled
[    0.806197] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 4 ports 3 Gbps 0x1 impl SATA mode
[    0.806202] ahci 0000:00:1f.2: flags: 64bit ncq sntf stag pm led clo pmp pio slum part 
[    0.806209] ahci 0000:00:1f.2: setting latency timer to 64
[    0.806400] scsi0 : ahci
[    0.806509] scsi1 : ahci
[    0.806627] scsi2 : ahci
[    0.806703] scsi3 : ahci
[    0.806810] ata1: SATA max UDMA/133 abar m2048@0xf8904000 port 0xf8904100 irq 27
[    0.806850] ata2: DUMMY
[    0.806852] ata3: DUMMY
[    0.806854] ata4: DUMMY
[    0.808410] Fixed MDIO Bus: probed
[    0.808464] PPP generic driver version 2.4.2
[    0.808627] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.808696] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 19 (level, low) -> IRQ 19
[    0.808711] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    0.808716] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    0.808827] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    0.812753] ehci_hcd 0000:00:1a.7: debug port 1
[    0.812762] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    0.812782] ehci_hcd 0000:00:1a.7: irq 19, io mem 0xf8904800
[    0.830022] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    0.830167] usb usb1: configuration #1 chosen from 1 choice
[    0.830208] hub 1-0:1.0: USB hub found
[    0.830218] hub 1-0:1.0: 6 ports detected
[    0.830335]   alloc irq_desc for 23 on node 0
[    0.830338]   alloc kstat_irqs on node 0
[    0.830345] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.830358] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.830363] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.830413] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    0.834371] ehci_hcd 0000:00:1d.7: debug port 1
[    0.834380] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.834396] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf8904c00
[    0.845137] ACPI: Battery Slot [BAT0] (battery present)
[    0.850017] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.850098] usb usb2: configuration #1 chosen from 1 choice
[    0.850137] hub 2-0:1.0: USB hub found
[    0.850146] hub 2-0:1.0: 6 ports detected
[    0.850284] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.850307] uhci_hcd: USB Universal Host Controller Interface driver
[    0.850416] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.850425] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    0.850430] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    0.850481] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    0.850563] uhci_hcd 0000:00:1a.0: irq 16, io base 0x00001820
[    0.850758] usb usb3: configuration #1 chosen from 1 choice
[    0.850795] hub 3-0:1.0: USB hub found
[    0.850804] hub 3-0:1.0: 2 ports detected
[    0.850906]   alloc irq_desc for 21 on node 0
[    0.850909]   alloc kstat_irqs on node 0
[    0.850915] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.850923] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    0.850928] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    0.850971] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    0.851019] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00001840
[    0.851202] usb usb4: configuration #1 chosen from 1 choice
[    0.851239] hub 4-0:1.0: USB hub found
[    0.851247] hub 4-0:1.0: 2 ports detected
[    0.851446] uhci_hcd 0000:00:1a.2: PCI INT C -> GSI 19 (level, low) -> IRQ 19
[    0.851455] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[    0.851460] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    0.851502] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
[    0.851533] uhci_hcd 0000:00:1a.2: irq 19, io base 0x00001860
[    0.851643] usb usb5: configuration #1 chosen from 1 choice
[    0.851683] hub 5-0:1.0: USB hub found
[    0.851696] hub 5-0:1.0: 2 ports detected
[    0.851795] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.851804] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.851809] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.851859] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
[    0.851930] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001880
[    0.852080] usb usb6: configuration #1 chosen from 1 choice
[    0.852160] hub 6-0:1.0: USB hub found
[    0.852169] hub 6-0:1.0: 2 ports detected
[    0.852307] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.852315] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.852320] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.852366] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
[    0.852396] uhci_hcd 0000:00:1d.1: irq 19, io base 0x000018a0
[    0.852506] usb usb7: configuration #1 chosen from 1 choice
[    0.852543] hub 7-0:1.0: USB hub found
[    0.852552] hub 7-0:1.0: 2 ports detected
[    0.852655]   alloc irq_desc for 18 on node 0
[    0.852658]   alloc kstat_irqs on node 0
[    0.852664] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.852672] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.852677] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.852719] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
[    0.852767] uhci_hcd 0000:00:1d.2: irq 18, io base 0x000018c0
[    0.852949] usb usb8: configuration #1 chosen from 1 choice
[    0.852986] hub 8-0:1.0: USB hub found
[    0.852998] hub 8-0:1.0: 2 ports detected
[    0.853225] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.861772] i8042.c: Detected active multiplexing controller, rev 1.1.
[    0.870760] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.870767] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    0.870772] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    0.870776] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    0.870780] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    0.870859] mice: PS/2 mouse device common for all mice
[    0.871081] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    0.871116] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    0.871246] device-mapper: uevent: version 1.0.3
[    0.871359] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
[    0.871458] device-mapper: multipath: version 1.1.0 loaded
[    0.871464] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.871780] cpuidle: using governor ladder
[    0.871940] cpuidle: using governor menu
[    0.872507] TCP cubic registered
[    0.872695] NET: Registered protocol family 10
[    0.873308] lo: Disabled Privacy Extensions
[    0.873734] NET: Registered protocol family 17
[    0.873758] Bluetooth: L2CAP ver 2.13
[    0.873761] Bluetooth: L2CAP socket layer initialized
[    0.873767] Bluetooth: SCO (Voice Link) ver 0.6
[    0.873770] Bluetooth: SCO socket layer initialized
[    0.873814] Bluetooth: RFCOMM TTY layer initialized
[    0.873818] Bluetooth: RFCOMM socket layer initialized
[    0.873821] Bluetooth: RFCOMM ver 1.11
[    0.874732] PM: Resume from disk failed.
[    0.874749] registered taskstats version 1
[    0.874903]   Magic number: 1:702:513
[    0.875004] rtc_cmos 00:06: setting system clock to 2009-11-25 03:31:14 UTC (1259119874)
[    0.875009] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.875011] EDD information not available.
[    0.906834] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[    1.002556] Clocksource tsc unstable (delta = -115353122 ns)
[    1.150093] usb 1-1: new high speed USB device using ehci_hcd and address 2
[    1.330136] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.373819] ata1.00: ATA-8: WDC WD2500BEVT-00ZCT0, 11.01A11, max UDMA/133
[    1.373824] ata1.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    1.375656] ata1.00: configured for UDMA/133
[    1.390250] scsi 0:0:0:0: Direct-Access     ATA      WDC WD2500BEVT-0 11.0 PQ: 0 ANSI: 5
[    1.390411] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.390428] sd 0:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    1.390492] sd 0:0:0:0: [sda] Write Protect is off
[    1.390496] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.390530] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.390707]  sda: sda1 sda2 < sda5 >
[    1.431045] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.431087] Freeing unused kernel memory: 660k freed
[    1.431355] Write protecting the kernel read-only data: 7584k
[    1.483218] usb 1-1: configuration #1 chosen from 1 choice
[    1.572554] agpgart-intel 0000:00:00.0: Intel Mobile Intel® GM45 Express Chipset
[    1.574054] agpgart-intel 0000:00:00.0: detected 32764K stolen memory
[    1.579259] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[    1.664881] [drm] Initialized drm 1.1.0 20060810
[    1.697618] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.697625] i915 0000:00:02.0: setting latency timer to 64
[    1.715698]   alloc irq_desc for 28 on node 0
[    1.715702]   alloc kstat_irqs on node 0
[    1.715715] i915 0000:00:02.0: irq 28 for MSI/MSI-X
[    1.823620] [drm] i2c_init DPDDC-B
[    1.833577] [drm] i2c_init DPDDC-C
[    1.838655] [drm] i2c_init DPDDC-D
[    1.976614] i2c-adapter i2c-2: unable to read EDID block.
[    1.976619] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[    1.981085] i2c-adapter i2c-4: unable to read EDID block.
[    1.981088] i915 0000:00:02.0: HDMI Type A-2: no EDID data
[    1.992715] [drm] fb0: inteldrmfb frame buffer device
[    1.998833] acpi device:06: registered as cooling_device2
[    1.999002] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:03/input/input6
[    1.999042] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[    1.999071] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    2.396907] [drm] LVDS-8: set mode 1366x768 18
[    3.003313] Console: switching to colour frame buffer device 170x48
[    3.154735] xor: automatically using best checksumming function: generic_sse
[    3.202510]    generic_sse:  4954.800 MB/sec
[    3.202514] xor: using function: generic_sse (4954.800 MB/sec)
[    3.208494] device-mapper: dm-raid45: initialized v0.2594b
[    3.404795] PM: Starting manual resume from disk
[    3.404800] PM: Resume from partition 8:5
[    3.404803] PM: Checking hibernation image.
[    3.404955] PM: Resume from disk failed.
[    3.439600] EXT4-fs (sda1): barriers enabled
[    3.465013] kjournald2 starting: pid 420, dev sda1:8, commit interval 5 seconds
[    3.465037] EXT4-fs (sda1): delayed allocation enabled
[    3.465042] EXT4-fs: file extents enabled
[    3.484763] EXT4-fs: mballoc enabled
[    3.484782] EXT4-fs (sda1): mounted filesystem with ordered data mode
[    4.025562] type=1505 audit(1259119877.645:2): operation="profile_load" pid=443 name=/usr/share/gdm/guest-session/Xsession
[    4.028624] type=1505 audit(1259119877.645:3): operation="profile_load" pid=444 name=/sbin/dhclient3
[    4.029728] type=1505 audit(1259119877.645:4): operation="profile_load" pid=444 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    4.030352] type=1505 audit(1259119877.655:5): operation="profile_load" pid=444 name=/usr/lib/connman/scripts/dhclient-script
[    4.073509] type=1505 audit(1259119877.695:6): operation="profile_load" pid=445 name=/usr/bin/evince
[    4.091450] type=1505 audit(1259119877.715:7): operation="profile_load" pid=445 name=/usr/bin/evince-previewer
[    4.102051] type=1505 audit(1259119877.725:8): operation="profile_load" pid=445 name=/usr/bin/evince-thumbnailer
[    4.123831] type=1505 audit(1259119877.745:9): operation="profile_load" pid=447 name=/usr/lib/cups/backend/cups-pdf
[    5.414753] Adding 5911880k swap on /dev/sda5.  Priority:-1 extents:1 across:5911880k 
[    5.762883] EXT4-fs (sda1): internal journal on sda1:8
[    5.959373] udev: starting version 147
[    6.483805] jme: JMicron JMC2XX ethernet driver version 1.0.4
[    6.486575] jme 0000:06:00.5: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    6.486595] jme 0000:06:00.5: setting latency timer to 64
[    6.486788] jme 0000:06:00.5: PME# disabled
[    6.488136] eth0: JMC250 Gigabit Ethernet ver:13 rev:3 macaddr:00:90:f5:91:04:26
[    6.488742] jmb38x_ms 0000:06:00.3: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    6.488752] jmb38x_ms 0000:06:00.3: setting latency timer to 64
[    6.516891] sdhci: Secure Digital Host Controller Interface driver
[    6.516895] sdhci: Copyright(c) Pierre Ossman
[    6.522618] cfg80211: Calling CRDA to update world regulatory domain
[    6.610194] Linux video capture interface: v2.00
[    6.676182] sdhci-pci 0000:06:00.0: SDHCI controller found [197b:2382] (rev 80)
[    6.676212] sdhci-pci 0000:06:00.0: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    6.676262] sdhci-pci 0000:06:00.0: setting latency timer to 64
[    6.676331] Registered led device: mmc0::
[    6.676380] mmc0: SDHCI controller on PCI [0000:06:00.0] using ADMA
[    6.676437] sdhci-pci 0000:06:00.2: SDHCI controller found [197b:2381] (rev 80)
[    6.676458] sdhci-pci 0000:06:00.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    6.676467] sdhci-pci 0000:06:00.2: Refusing to bind to secondary interface.
[    6.676476] sdhci-pci 0000:06:00.2: PCI INT B disabled
[    6.901918] lp: driver loaded but no devices found
[    6.920260] uvcvideo: Found UVC 1.00 device BisonCam, NB Pro (5986:0241)
[    6.920280] uvcvideo: No valid video chain found.
[    6.920310] usbcore: registered new interface driver uvcvideo
[    6.920314] USB Video Class driver (v0.1.0)
[    7.279677] Synaptics Touchpad, model: 1, fw: 7.2, id: 0x1c0b1, caps: 0xd04731/0xa42000
[    7.313756] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input7
[    7.400506] cfg80211: World regulatory domain updated:
[    7.400510] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[    7.400515] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    7.400519] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    7.400523] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    7.400527] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    7.400531] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    7.454126] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
[    7.454131] iwlagn: Copyright(c) 2003-2009 Intel Corporation
[    7.454295] iwlagn 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    7.454306] iwlagn 0000:02:00.0: setting latency timer to 64
[    7.454344] iwlagn 0000:02:00.0: Detected Intel Wireless WiFi Link 5100AGN REV=0x54
[    7.485885] ip_tables: (C) 2000-2006 Netfilter Core Team
[    7.496313] iwlagn 0000:02:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[    7.496385]   alloc irq_desc for 29 on node 0
[    7.496388]   alloc kstat_irqs on node 0
[    7.496412] iwlagn 0000:02:00.0: irq 29 for MSI/MSI-X
[    7.854517] phy0: Selected rate control algorithm 'iwl-agn-rs'
[    7.944698] udev: renamed network interface wlan0 to wlan1
[    8.132403]   alloc irq_desc for 22 on node 0
[    8.132409]   alloc kstat_irqs on node 0
[    8.132418] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    8.132464] HDA Intel 0000:00:1b.0: setting latency timer to 64
[    8.387035] hda_codec: Unknown model for ALC272, trying auto-probe from BIOS...
[    8.387988] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input8
[   10.486604] __ratelimit: 6 callbacks suppressed
[   10.486609] type=1505 audit(1259119884.105:12): operation="profile_replace" pid=893 name=/usr/share/gdm/guest-session/Xsession
[   10.488950] type=1505 audit(1259119884.105:13): operation="profile_replace" pid=894 name=/sbin/dhclient3
[   10.490073] type=1505 audit(1259119884.115:14): operation="profile_replace" pid=894 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   10.490681] type=1505 audit(1259119884.115:15): operation="profile_replace" pid=894 name=/usr/lib/connman/scripts/dhclient-script
[   10.495287] type=1505 audit(1259119884.115:16): operation="profile_replace" pid=895 name=/usr/bin/evince
[   10.513191] type=1505 audit(1259119884.135:17): operation="profile_replace" pid=895 name=/usr/bin/evince-previewer
[   10.523733] type=1505 audit(1259119884.145:18): operation="profile_replace" pid=895 name=/usr/bin/evince-thumbnailer
[   10.537624] type=1505 audit(1259119884.155:19): operation="profile_replace" pid=897 name=/usr/lib/cups/backend/cups-pdf
[   10.538930] type=1505 audit(1259119884.155:20): operation="profile_replace" pid=897 name=/usr/sbin/cupsd
[   10.543094] type=1505 audit(1259119884.165:21): operation="profile_replace" pid=898 name=/usr/sbin/tcpdump
[   13.381263] iwlagn 0000:02:00.0: firmware: requesting iwlwifi-5000-2.ucode
[   13.547209] iwlagn 0000:02:00.0: loaded firmware version 8.24.2.12
[   13.714547] Registered led device: iwl-phy0::radio
[   13.714579] Registered led device: iwl-phy0::assoc
[   13.714606] Registered led device: iwl-phy0::RX
[   13.714633] Registered led device: iwl-phy0::TX
[   13.750858] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[   13.821740] jme 0000:06:00.5: PME# disabled
[   13.821834]   alloc irq_desc for 30 on node 0
[   13.821838]   alloc kstat_irqs on node 0
[   13.821858] jme 0000:06:00.5: irq 30 for MSI/MSI-X
[   13.822278] eth0: Link is down.
[   13.822626] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   15.119207] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[   15.119213] vboxdrv: Successfully done.
[   15.119216] vboxdrv: Found 2 processor cores.
[   15.119300] VBoxDrv: dbg - g_abExecMemory=ffffffffa0352480
[   15.119325] vboxdrv: fAsync=0 offMin=0x1a6 offMax=0x687
[   15.119387] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   15.119390] vboxdrv: Successfully loaded version 3.0.12 (interface 0x00110000).
[   15.526106] VBoxNetFlt: dbg - g_abExecMemory=ffffffffa04f1220
[   15.531477] VBoxNetAdp: dbg - g_abExecMemory=ffffffffa050ab20
[   17.743070] ppdev: user-space parallel port driver
[   18.571039] i2c-adapter i2c-2: unable to read EDID block.
[   18.571044] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   18.575509] i2c-adapter i2c-2: unable to read EDID block.
[   18.575513] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   18.580057] i2c-adapter i2c-4: unable to read EDID block.
[   18.580062] i915 0000:00:02.0: HDMI Type A-2: no EDID data
[   18.584527] i2c-adapter i2c-4: unable to read EDID block.
[   18.584531] i915 0000:00:02.0: HDMI Type A-2: no EDID data
[   18.740495] i2c-adapter i2c-2: unable to read EDID block.
[   18.740501] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   18.745363] i2c-adapter i2c-2: unable to read EDID block.
[   18.745368] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   18.764164] i2c-adapter i2c-4: unable to read EDID block.
[   18.764170] i915 0000:00:02.0: HDMI Type A-2: no EDID data
[   18.768726] i2c-adapter i2c-4: unable to read EDID block.
[   18.768730] i915 0000:00:02.0: HDMI Type A-2: no EDID data
[   23.108265] i2c-adapter i2c-2: unable to read EDID block.
[   23.108271] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   23.112747] i2c-adapter i2c-2: unable to read EDID block.
[   23.112751] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   23.117254] i2c-adapter i2c-4: unable to read EDID block.
[   23.117258] i915 0000:00:02.0: HDMI Type A-2: no EDID data
[   23.121730] i2c-adapter i2c-4: unable to read EDID block.
[   23.121733] i915 0000:00:02.0: HDMI Type A-2: no EDID data
[   23.290918] i2c-adapter i2c-2: unable to read EDID block.
[   23.290925] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   23.295379] i2c-adapter i2c-2: unable to read EDID block.
[   23.295383] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   23.299890] i2c-adapter i2c-4: unable to read EDID block.
[   23.299894] i915 0000:00:02.0: HDMI Type A-2: no EDID data
[   23.304734] i2c-adapter i2c-4: unable to read EDID block.
[   23.304739] i915 0000:00:02.0: HDMI Type A-2: no EDID data
[   23.489777] i2c-adapter i2c-2: unable to read EDID block.
[   23.489783] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   23.495639] i2c-adapter i2c-2: unable to read EDID block.
[   23.495644] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   23.512521] i2c-adapter i2c-4: unable to read EDID block.
[   23.512530] i915 0000:00:02.0: HDMI Type A-2: no EDID data
[   23.517033] i2c-adapter i2c-4: unable to read EDID block.
[   23.517037] i915 0000:00:02.0: HDMI Type A-2: no EDID data
[   38.064123] i2c-adapter i2c-2: unable to read EDID block.
[   38.064131] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   38.074857] i2c-adapter i2c-2: unable to read EDID block.
[   38.074866] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   38.079396] i2c-adapter i2c-4: unable to read EDID block.
[   38.079400] i915 0000:00:02.0: HDMI Type A-2: no EDID data
[   38.084646] i2c-adapter i2c-4: unable to read EDID block.
[   38.084650] i915 0000:00:02.0: HDMI Type A-2: no EDID data
[   38.261180] i2c-adapter i2c-2: unable to read EDID block.
[   38.261187] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   38.266062] i2c-adapter i2c-2: unable to read EDID block.
[   38.266067] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   38.272906] i2c-adapter i2c-4: unable to read EDID block.
[   38.272912] i915 0000:00:02.0: HDMI Type A-2: no EDID data
[   38.277980] i2c-adapter i2c-4: unable to read EDID block.
[   38.277985] i915 0000:00:02.0: HDMI Type A-2: no EDID data
[   38.440923] i2c-adapter i2c-2: unable to read EDID block.
[   38.440928] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   38.445751] i2c-adapter i2c-2: unable to read EDID block.
[   38.445756] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   38.450267] i2c-adapter i2c-4: unable to read EDID block.
[   38.450271] i915 0000:00:02.0: HDMI Type A-2: no EDID data
[   38.455317] i2c-adapter i2c-4: unable to read EDID block.
[   38.455321] i915 0000:00:02.0: HDMI Type A-2: no EDID data
[   39.818673] i2c-adapter i2c-2: unable to read EDID block.
[   39.818679] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   39.823155] i2c-adapter i2c-2: unable to read EDID block.
[   39.823159] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[   39.827656] i2c-adapter i2c-4: unable to read EDID block.
[   39.827659] i915 0000:00:02.0: HDMI Type A-2: no EDID data
[   39.832130] i2c-adapter i2c-4: unable to read EDID block.
[   39.832134] i915 0000:00:02.0: HDMI Type A-2: no EDID data
[   52.756175] wlan1: authenticate with AP 00:21:29:b0:6b:51
[   52.758059] wlan1: authenticated
[   52.758063] wlan1: associate with AP 00:21:29:b0:6b:51
[   52.760795] wlan1: RX AssocResp from 00:21:29:b0:6b:51 (capab=0x411 status=0 aid=2)
[   52.760799] wlan1: associated
[   52.762175] ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[   52.995061] Intel AES-NI instructions are not detected.
[   53.050624] padlock: VIA PadLock not detected.
[   63.150021] wlan1: no IPv6 routers present
[   70.214191] process `skype.real' is using obsolete setsockopt SO_BSDCOMPAT
[  693.512720] wlan1: deauthenticating by local choice (reason=3)
[  693.672064] wlan1: disassociating by local choice (reason=3)
[  694.204416] PM: Syncing filesystems ... done.
[  694.210055] PM: Preparing system for mem sleep
[  694.210061] Freezing user space processes ... (elapsed 0.00 seconds) done.
[  694.211254] Freezing remaining freezable tasks ... (elapsed 0.00 seconds) done.
[  694.211311] PM: Entering mem sleep
[  694.211327] Suspending console(s) (use no_console_suspend to debug)
[  694.310105] sd 0:0:0:0: [sda] Synchronizing SCSI cache
[  694.377799] sd 0:0:0:0: [sda] Stopping disk
[  695.471028] ACPI handle has no context!
[  695.490244] ACPI handle has no context!
[  695.490253] jmb38x_ms 0000:06:00.3: PME# disabled
[  695.490264] jmb38x_ms 0000:06:00.3: PCI INT C disabled
[  695.490273] ACPI handle has no context!
[  695.510231] sdhci-pci 0000:06:00.0: PME# disabled
[  695.510240] sdhci-pci 0000:06:00.0: PCI INT B disabled
[  695.590109] ehci_hcd 0000:00:1d.7: PCI INT A disabled
[  695.590121] uhci_hcd 0000:00:1d.2: PCI INT C disabled
[  695.590131] uhci_hcd 0000:00:1d.1: PCI INT B disabled
[  695.590140] uhci_hcd 0000:00:1d.0: PCI INT A disabled
[  695.700531] HDA Intel 0000:00:1b.0: PCI INT A disabled
[  695.720152] ehci_hcd 0000:00:1a.7: PCI INT C disabled
[  695.720162] uhci_hcd 0000:00:1a.2: PCI INT C disabled
[  695.720172] uhci_hcd 0000:00:1a.1: PCI INT B disabled
[  695.720187] uhci_hcd 0000:00:1a.0: PCI INT A disabled
[  695.850176] PM: suspend devices took 1.650 seconds
[  695.850517] ehci_hcd 0000:00:1d.7: PME# disabled
[  695.870391] ehci_hcd 0000:00:1a.7: PME# disabled
[  696.110069] ACPI: Preparing to enter system sleep state S3
[  696.215518] Disabling non-boot CPUs ...
[  696.320022] CPU 1 is now offline
[  696.320026] SMP alternatives: switching to UP code
[  696.330240] CPU0 attaching NULL sched-domain.
[  696.330246] CPU1 attaching NULL sched-domain.
[  696.330258] CPU0 attaching NULL sched-domain.
[  696.330515] CPU1 is down
[  696.330568] Extended CMOS year: 2000
[  696.330568] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[  696.330568] Back to C!
[  696.330568] CPU0: Thermal LVT vector (0xfa) already installed
[  696.330568] Extended CMOS year: 2000
[  696.330568] Enabling non-boot CPUs ...
[  696.330568] SMP alternatives: switching to SMP code
[  696.340615] Booting processor 1 APIC 0x1 ip 0x6000
[  696.330064] Initializing CPU#1
[  696.330064] Calibrating delay using timer specific routine.. 2593.54 BogoMIPS (lpj=12967724)
[  696.330064] CPU: L1 I cache: 32K, L1 D cache: 32K
[  696.330064] CPU: L2 cache: 3072K
[  696.330064] CPU 1/0x1 -> Node 0
[  696.330064] CPU: Physical Processor ID: 0
[  696.330064] CPU: Processor Core ID: 1
[  696.330064] mce: CPU supports 6 MCE banks
[  696.330064] CPU1: Thermal monitoring enabled (TM2)
[  696.330064] x86 PAT enabled: cpu 1, old 0x7040600070406, new 0x7010600070106
[  696.502279] CPU1: Genuine Intel(R) CPU           U7300  @ 1.30GHz stepping 0a
[  696.502356] CPU0 attaching NULL sched-domain.
[  696.502520] Switched to high resolution mode on CPU 1
[  696.540029] CPU0 attaching sched-domain:
[  696.540033]  domain 0: span 0-1 level MC
[  696.540036]   groups: 0 1
[  696.540043] CPU1 attaching sched-domain:
[  696.540045]  domain 0: span 0-1 level MC
[  696.540048]   groups: 1 0
[  696.542521] CPU1 is up
[  696.542525] ACPI: Waking up from system sleep state S3
[  702.360261] i915 0000:00:02.0: restoring config space at offset 0xf (was 0x100, writing 0x105)
[  702.360278] i915 0000:00:02.0: restoring config space at offset 0x1 (was 0x900007, writing 0x900407)
[  702.360352] uhci_hcd 0000:00:1a.0: restoring config space at offset 0x1 (was 0x2900005, writing 0x2900001)
[  702.360403] uhci_hcd 0000:00:1a.1: restoring config space at offset 0x1 (was 0x2900005, writing 0x2900001)
[  702.360452] uhci_hcd 0000:00:1a.2: restoring config space at offset 0x1 (was 0x2900005, writing 0x2900001)
[  702.360511] ehci_hcd 0000:00:1a.7: restoring config space at offset 0x1 (was 0x2900106, writing 0x2900102)
[  702.360537] ehci_hcd 0000:00:1a.7: PME# disabled
[  702.360560] HDA Intel 0000:00:1b.0: restoring config space at offset 0xf (was 0x100, writing 0x10b)
[  702.360586] HDA Intel 0000:00:1b.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[  702.360595] HDA Intel 0000:00:1b.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100102)
[  702.360635] pcieport-driver 0000:00:1c.0: restoring config space at offset 0xf (was 0x40100, writing 0x4010a)
[  702.360650] pcieport-driver 0000:00:1c.0: restoring config space at offset 0x9 (was 0x10001, writing 0x1fff1)
[  702.360657] pcieport-driver 0000:00:1c.0: restoring config space at offset 0x8 (was 0x0, writing 0xf850f850)
[  702.360664] pcieport-driver 0000:00:1c.0: restoring config space at offset 0x7 (was 0x20000000, writing 0x200000f0)
[  702.360672] pcieport-driver 0000:00:1c.0: restoring config space at offset 0x6 (was 0x0, writing 0x30200)
[  702.360682] pcieport-driver 0000:00:1c.0: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
[  702.360691] pcieport-driver 0000:00:1c.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100507)
[  702.360749] pcieport-driver 0000:00:1c.1: restoring config space at offset 0xf (was 0x40200, writing 0x40205)
[  702.360765] pcieport-driver 0000:00:1c.1: restoring config space at offset 0x9 (was 0x10001, writing 0xf3f1f001)
[  702.360774] pcieport-driver 0000:00:1c.1: restoring config space at offset 0x7 (was 0x20000000, writing 0x2020)
[  702.360786] pcieport-driver 0000:00:1c.1: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
[  702.360795] pcieport-driver 0000:00:1c.1: restoring config space at offset 0x1 (was 0x100000, writing 0x100507)
[  702.360853] pcieport-driver 0000:00:1c.4: restoring config space at offset 0xf (was 0x40100, writing 0x4010a)
[  702.360869] pcieport-driver 0000:00:1c.4: restoring config space at offset 0x9 (was 0x10001, writing 0x1fff1)
[  702.360878] pcieport-driver 0000:00:1c.4: restoring config space at offset 0x7 (was 0x20000000, writing 0x3030)
[  702.360890] pcieport-driver 0000:00:1c.4: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
[  702.360899] pcieport-driver 0000:00:1c.4: restoring config space at offset 0x1 (was 0x100000, writing 0x100507)
[  702.360974] uhci_hcd 0000:00:1d.0: restoring config space at offset 0x1 (was 0x2900005, writing 0x2900001)
[  702.361024] uhci_hcd 0000:00:1d.1: restoring config space at offset 0x1 (was 0x2900005, writing 0x2900001)
[  702.361073] uhci_hcd 0000:00:1d.2: restoring config space at offset 0x1 (was 0x2900005, writing 0x2900001)
[  702.361131] ehci_hcd 0000:00:1d.7: restoring config space at offset 0x1 (was 0x2900106, writing 0x2900102)
[  702.361157] ehci_hcd 0000:00:1d.7: PME# disabled
[  702.361169] pci 0000:00:1e.0: restoring config space at offset 0xf (was 0x40000, writing 0x400ff)
[  702.361185] pci 0000:00:1e.0: restoring config space at offset 0x9 (was 0x10001, writing 0x1fff1)
[  702.361192] pci 0000:00:1e.0: restoring config space at offset 0x8 (was 0x0, writing 0xfff0)
[  702.361199] pci 0000:00:1e.0: restoring config space at offset 0x7 (was 0x22800000, writing 0x228000f0)
[  702.361214] pci 0000:00:1e.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100107)
[  702.361298] ahci 0000:00:1f.2: restoring config space at offset 0xf (was 0x200, writing 0x20a)
[  702.361327] ahci 0000:00:1f.2: restoring config space at offset 0x1 (was 0x2b00007, writing 0x2b00407)
[  702.361391] pci 0000:00:1f.3: restoring config space at offset 0x4 (was 0x4, writing 0x80000004)
[  702.361442] iwlagn 0000:02:00.0: restoring config space at offset 0xf (was 0x100, writing 0x105)
[  702.361481] iwlagn 0000:02:00.0: restoring config space at offset 0x4 (was 0x4, writing 0xf8500004)
[  702.361491] iwlagn 0000:02:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[  702.361503] iwlagn 0000:02:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100106)
[  702.361632] sdhci-pci 0000:06:00.0: restoring config space at offset 0x1 (was 0x100100, writing 0x100107)
[  702.361723] pci 0000:06:00.2: restoring config space at offset 0x1 (was 0x100100, writing 0x100103)
[  702.361813] jmb38x_ms 0000:06:00.3: restoring config space at offset 0x1 (was 0x100100, writing 0x100107)
[  702.361868] jme 0000:06:00.5: restoring config space at offset 0xf (was 0x300, writing 0x30a)
[  702.422363] i915 0000:00:02.0: setting latency timer to 64
[  702.484525] [drm] LVDS-8: set mode 1366x768 18
[  702.504852] pci 0000:00:02.1: PME# disabled
[  702.504867] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[  702.504875] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[  702.504902] usb usb3: root hub lost power or was reset
[  702.504925] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[  702.504933] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[  702.504959] usb usb4: root hub lost power or was reset
[  702.504981] uhci_hcd 0000:00:1a.2: PCI INT C -> GSI 19 (level, low) -> IRQ 19
[  702.504989] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[  702.505015] usb usb5: root hub lost power or was reset
[  702.505037] ehci_hcd 0000:00:1a.7: PME# disabled
[  702.505043] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 19 (level, low) -> IRQ 19
[  702.505052] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[  702.505064] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[  702.505072] HDA Intel 0000:00:1b.0: setting latency timer to 64
[  702.505109] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[  702.505117] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[  702.505143] usb usb6: root hub lost power or was reset
[  702.505165] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[  702.505173] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[  702.505200] usb usb7: root hub lost power or was reset
[  702.505220] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[  702.505229] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[  702.505255] usb usb8: root hub lost power or was reset
[  702.505276] ehci_hcd 0000:00:1d.7: PME# disabled
[  702.505281] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[  702.505290] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[  702.505304] pci 0000:00:1e.0: setting latency timer to 64
[  702.505319] ahci 0000:00:1f.2: setting latency timer to 64
[  702.505399] sdhci-pci 0000:06:00.0: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[  702.505416] sdhci-pci 0000:06:00.0: setting latency timer to 64
[  702.505445] pci 0000:06:00.2: PME# disabled
[  702.505455] jmb38x_ms 0000:06:00.3: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[  702.505463] jmb38x_ms 0000:06:00.3: setting latency timer to 64
[  702.505485] jme 0000:06:00.5: PME# disabled
[  702.583685] sd 0:0:0:0: [sda] Starting disk
[  703.030061] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[  703.074894] ata1.00: configured for UDMA/133
[  703.160920] PM: resume devices took 0.800 seconds
[  703.160989] PM: Finishing wakeup.
[  703.160996] Restarting tasks ... done.
[  703.352396] Registered led device: iwl-phy0::radio
[  703.352482] Registered led device: iwl-phy0::assoc
[  703.352553] Registered led device: iwl-phy0::RX
[  703.352626] Registered led device: iwl-phy0::TX
[  703.412326] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[  703.415778] jme 0000:06:00.5: PME# disabled
[  703.416049] jme 0000:06:00.5: irq 30 for MSI/MSI-X
[  703.416160] eth0: Link is down.
[  703.416462] eth0: Link is down.
[  703.416840] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  709.877438] wlan1: authenticate with AP 00:21:29:b0:6b:51
[  709.879291] wlan1: authenticated
[  709.879300] wlan1: associate with AP 00:21:29:b0:6b:51
[  709.881914] wlan1: RX AssocResp from 00:21:29:b0:6b:51 (capab=0x411 status=0 aid=2)
[  709.881924] wlan1: associated
[  709.883794] ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[  720.180035] wlan1: no IPv6 routers present
[ 3884.608960] CE: hpet increasing min_delta_ns to 15000 nsec
[ 5813.990118] usb 6-1: new full speed USB device using uhci_hcd and address 2
[ 5814.191602] usb 6-1: configuration #1 chosen from 1 choice
[ 5814.669561] usblp0: USB Bidirectional printer dev 2 if 1 alt 0 proto 2 vid 0x03F0 pid 0x4B11
[ 5814.669616] usbcore: registered new interface driver usblp
[ 5816.380222] usb 6-1: usbfs: interface 1 claimed by usblp while 'usb' sets config #1
[ 5823.865764] usblp0: removed
[ 6930.741818] npviewer.bin[5209]: segfault at ff99cd48 ip 00000000ff99cd48 sp 00000000ff80d73c error 14
[ 8097.252652] wlan1: disassociating by local choice (reason=3)
[ 8097.390046] wlan1: deauthenticating by local choice (reason=3)
[ 8098.852882] PM: Syncing filesystems ... done.
[ 8098.944993] PM: Preparing system for mem sleep
[ 8098.944999] Freezing user space processes ... (elapsed 0.12 seconds) done.
[ 8099.070847] Freezing remaining freezable tasks ... (elapsed 0.00 seconds) done.
[ 8099.070901] PM: Entering mem sleep
[ 8099.070918] Suspending console(s) (use no_console_suspend to debug)
[ 8099.170109] sd 0:0:0:0: [sda] Synchronizing SCSI cache
[ 8099.170284] sd 0:0:0:0: [sda] Stopping disk
[ 8100.280989] ACPI handle has no context!
[ 8100.300194] ACPI handle has no context!
[ 8100.300203] jmb38x_ms 0000:06:00.3: PME# disabled
[ 8100.300213] jmb38x_ms 0000:06:00.3: PCI INT C disabled
[ 8100.300223] ACPI handle has no context!
[ 8100.320227] sdhci-pci 0000:06:00.0: PME# disabled
[ 8100.320236] sdhci-pci 0000:06:00.0: PCI INT B disabled
[ 8100.400107] ehci_hcd 0000:00:1d.7: PCI INT A disabled
[ 8100.400118] uhci_hcd 0000:00:1d.2: PCI INT C disabled
[ 8100.400128] uhci_hcd 0000:00:1d.1: PCI INT B disabled
[ 8100.400137] uhci_hcd 0000:00:1d.0: PCI INT A disabled
[ 8100.510511] HDA Intel 0000:00:1b.0: PCI INT A disabled
[ 8100.530107] ehci_hcd 0000:00:1a.7: PCI INT C disabled
[ 8100.530116] uhci_hcd 0000:00:1a.2: PCI INT C disabled
[ 8100.530126] uhci_hcd 0000:00:1a.1: PCI INT B disabled
[ 8100.530136] uhci_hcd 0000:00:1a.0: PCI INT A disabled
[ 8100.630186] PM: suspend devices took 1.560 seconds
[ 8100.630523] ehci_hcd 0000:00:1d.7: PME# disabled
[ 8100.650390] ehci_hcd 0000:00:1a.7: PME# disabled
[ 8100.890066] ACPI: Preparing to enter system sleep state S3
[ 8100.995524] Disabling non-boot CPUs ...
[ 8101.100018] CPU 1 is now offline
[ 8101.100022] SMP alternatives: switching to UP code
[ 8101.110186] CPU0 attaching NULL sched-domain.
[ 8101.110190] CPU1 attaching NULL sched-domain.
[ 8101.110202] CPU0 attaching NULL sched-domain.
[ 8101.110469] CPU1 is down
[ 8101.110522] Extended CMOS year: 2000
[ 8101.110522] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[ 8101.110522] Back to C!
[ 8101.110522] CPU0: Thermal LVT vector (0xfa) already installed
[ 8101.110522] Extended CMOS year: 2000
[ 8101.110522] Enabling non-boot CPUs ...
[ 8101.110522] SMP alternatives: switching to SMP code
[ 8101.120567] Booting processor 1 APIC 0x1 ip 0x6000
[ 8101.110029] Initializing CPU#1
[ 8101.110029] Calibrating delay using timer specific routine.. 2593.52 BogoMIPS (lpj=12967632)
[ 8101.110029] CPU: L1 I cache: 32K, L1 D cache: 32K
[ 8101.110029] CPU: L2 cache: 3072K
[ 8101.110029] CPU 1/0x1 -> Node 0
[ 8101.110029] CPU: Physical Processor ID: 0
[ 8101.110029] CPU: Processor Core ID: 1
[ 8101.110029] mce: CPU supports 6 MCE banks
[ 8101.110029] CPU1: Thermal monitoring enabled (TM2)
[ 8101.110029] x86 PAT enabled: cpu 1, old 0x7040600070406, new 0x7010600070106
[ 8101.282329] CPU1: Genuine Intel(R) CPU           U7300  @ 1.30GHz stepping 0a
[ 8101.282402] CPU0 attaching NULL sched-domain.
[ 8101.282519] Switched to high resolution mode on CPU 1
[ 8101.320029] CPU0 attaching sched-domain:
[ 8101.320034]  domain 0: span 0-1 level MC
[ 8101.320037]   groups: 0 1
[ 8101.320043] CPU1 attaching sched-domain:
[ 8101.320045]  domain 0: span 0-1 level MC
[ 8101.320048]   groups: 1 0
[ 8101.322521] CPU1 is up
[ 8101.322525] ACPI: Waking up from system sleep state S3
[ 8107.540171] i915 0000:00:02.0: restoring config space at offset 0xf (was 0x100, writing 0x105)
[ 8107.540188] i915 0000:00:02.0: restoring config space at offset 0x1 (was 0x900007, writing 0x900407)
[ 8107.540262] uhci_hcd 0000:00:1a.0: restoring config space at offset 0x1 (was 0x2900005, writing 0x2900001)
[ 8107.540313] uhci_hcd 0000:00:1a.1: restoring config space at offset 0x1 (was 0x2900005, writing 0x2900001)
[ 8107.540363] uhci_hcd 0000:00:1a.2: restoring config space at offset 0x1 (was 0x2900005, writing 0x2900001)
[ 8107.540422] ehci_hcd 0000:00:1a.7: restoring config space at offset 0x1 (was 0x2900106, writing 0x2900102)
[ 8107.540448] ehci_hcd 0000:00:1a.7: PME# disabled
[ 8107.540471] HDA Intel 0000:00:1b.0: restoring config space at offset 0xf (was 0x100, writing 0x10b)
[ 8107.540497] HDA Intel 0000:00:1b.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[ 8107.540506] HDA Intel 0000:00:1b.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100102)
[ 8107.540545] pcieport-driver 0000:00:1c.0: restoring config space at offset 0xf (was 0x40100, writing 0x4010a)
[ 8107.540561] pcieport-driver 0000:00:1c.0: restoring config space at offset 0x9 (was 0x10001, writing 0x1fff1)
[ 8107.540568] pcieport-driver 0000:00:1c.0: restoring config space at offset 0x8 (was 0x0, writing 0xf850f850)
[ 8107.540575] pcieport-driver 0000:00:1c.0: restoring config space at offset 0x7 (was 0x20000000, writing 0xf0)
[ 8107.540582] pcieport-driver 0000:00:1c.0: restoring config space at offset 0x6 (was 0x0, writing 0x30200)
[ 8107.540593] pcieport-driver 0000:00:1c.0: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
[ 8107.540602] pcieport-driver 0000:00:1c.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100507)
[ 8107.540661] pcieport-driver 0000:00:1c.1: restoring config space at offset 0xf (was 0x40200, writing 0x40205)
[ 8107.540676] pcieport-driver 0000:00:1c.1: restoring config space at offset 0x9 (was 0x10001, writing 0xf3f1f001)
[ 8107.540685] pcieport-driver 0000:00:1c.1: restoring config space at offset 0x7 (was 0x20000000, writing 0x20002020)
[ 8107.540698] pcieport-driver 0000:00:1c.1: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
[ 8107.540707] pcieport-driver 0000:00:1c.1: restoring config space at offset 0x1 (was 0x100000, writing 0x100507)
[ 8107.540765] pcieport-driver 0000:00:1c.4: restoring config space at offset 0xf (was 0x40100, writing 0x4010a)
[ 8107.540781] pcieport-driver 0000:00:1c.4: restoring config space at offset 0x9 (was 0x10001, writing 0x1fff1)
[ 8107.540790] pcieport-driver 0000:00:1c.4: restoring config space at offset 0x7 (was 0x20000000, writing 0x20003030)
[ 8107.540802] pcieport-driver 0000:00:1c.4: restoring config space at offset 0x3 (was 0x810000, writing 0x810010)
[ 8107.540811] pcieport-driver 0000:00:1c.4: restoring config space at offset 0x1 (was 0x100000, writing 0x100507)
[ 8107.540887] uhci_hcd 0000:00:1d.0: restoring config space at offset 0x1 (was 0x2900005, writing 0x2900001)
[ 8107.540937] uhci_hcd 0000:00:1d.1: restoring config space at offset 0x1 (was 0x2900005, writing 0x2900001)
[ 8107.540987] uhci_hcd 0000:00:1d.2: restoring config space at offset 0x1 (was 0x2900005, writing 0x2900001)
[ 8107.541045] ehci_hcd 0000:00:1d.7: restoring config space at offset 0x1 (was 0x2900106, writing 0x2900102)
[ 8107.541071] ehci_hcd 0000:00:1d.7: PME# disabled
[ 8107.541084] pci 0000:00:1e.0: restoring config space at offset 0xf (was 0x40000, writing 0x400ff)
[ 8107.541100] pci 0000:00:1e.0: restoring config space at offset 0x9 (was 0x10001, writing 0x1fff1)
[ 8107.541106] pci 0000:00:1e.0: restoring config space at offset 0x8 (was 0x0, writing 0xfff0)
[ 8107.541114] pci 0000:00:1e.0: restoring config space at offset 0x7 (was 0x22800000, writing 0x228000f0)
[ 8107.541129] pci 0000:00:1e.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100107)
[ 8107.541214] ahci 0000:00:1f.2: restoring config space at offset 0xf (was 0x200, writing 0x20a)
[ 8107.541243] ahci 0000:00:1f.2: restoring config space at offset 0x1 (was 0x2b00007, writing 0x2b00407)
[ 8107.541307] pci 0000:00:1f.3: restoring config space at offset 0x4 (was 0x4, writing 0x80000004)
[ 8107.541358] iwlagn 0000:02:00.0: restoring config space at offset 0xf (was 0x100, writing 0x105)
[ 8107.541398] iwlagn 0000:02:00.0: restoring config space at offset 0x4 (was 0x4, writing 0xf8500004)
[ 8107.541408] iwlagn 0000:02:00.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[ 8107.541420] iwlagn 0000:02:00.0: restoring config space at offset 0x1 (was 0x100000, writing 0x100506)
[ 8107.541546] sdhci-pci 0000:06:00.0: restoring config space at offset 0x1 (was 0x100100, writing 0x100107)
[ 8107.541636] pci 0000:06:00.2: restoring config space at offset 0x1 (was 0x100100, writing 0x100103)
[ 8107.541726] jmb38x_ms 0000:06:00.3: restoring config space at offset 0x1 (was 0x100100, writing 0x100107)
[ 8107.541781] jme 0000:06:00.5: restoring config space at offset 0xf (was 0x300, writing 0x30a)
[ 8107.597165] i915 0000:00:02.0: setting latency timer to 64
[ 8107.659699] [drm] LVDS-8: set mode 1366x768 18
[ 8107.679930] pci 0000:00:02.1: PME# disabled
[ 8107.679945] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[ 8107.679954] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[ 8107.679981] usb usb3: root hub lost power or was reset
[ 8107.680022] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[ 8107.680030] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[ 8107.680057] usb usb4: root hub lost power or was reset
[ 8107.680078] uhci_hcd 0000:00:1a.2: PCI INT C -> GSI 19 (level, low) -> IRQ 19
[ 8107.680086] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[ 8107.680113] usb usb5: root hub lost power or was reset
[ 8107.680135] ehci_hcd 0000:00:1a.7: PME# disabled
[ 8107.680141] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 19 (level, low) -> IRQ 19
[ 8107.680149] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[ 8107.680162] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[ 8107.680170] HDA Intel 0000:00:1b.0: setting latency timer to 64
[ 8107.680209] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[ 8107.680217] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[ 8107.680244] usb usb6: root hub lost power or was reset
[ 8107.680277] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[ 8107.680285] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[ 8107.680312] usb usb7: root hub lost power or was reset
[ 8107.680333] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[ 8107.680341] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[ 8107.680368] usb usb8: root hub lost power or was reset
[ 8107.680389] ehci_hcd 0000:00:1d.7: PME# disabled
[ 8107.680395] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[ 8107.680404] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[ 8107.680429] pci 0000:00:1e.0: setting latency timer to 64
[ 8107.680444] ahci 0000:00:1f.2: setting latency timer to 64
[ 8107.680523] sdhci-pci 0000:06:00.0: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[ 8107.680540] sdhci-pci 0000:06:00.0: setting latency timer to 64
[ 8107.680568] pci 0000:06:00.2: PME# disabled
[ 8107.680576] jmb38x_ms 0000:06:00.3: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[ 8107.680584] jmb38x_ms 0000:06:00.3: setting latency timer to 64
[ 8107.680605] jme 0000:06:00.5: PME# disabled
[ 8108.210067] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[ 8108.262880] ata1.00: configured for UDMA/133
[ 8108.276503] sd 0:0:0:0: [sda] Starting disk
[ 8108.341079] PM: resume devices took 0.800 seconds
[ 8108.341149] PM: Finishing wakeup.
[ 8108.341156] Restarting tasks ... 
[ 8108.400158] usb 6-1: USB disconnect, address 2
[ 8108.430577] done.
[ 8108.686980] irq 18: nobody cared (try booting with the "irqpoll" option)
[ 8108.686991] Pid: 5538, comm: pm-suspend Not tainted 2.6.31-15-generic #50-Ubuntu
[ 8108.686995] Call Trace:
[ 8108.686997]  <IRQ>  [<ffffffff810b52d6>] __report_bad_irq+0x26/0xa0
[ 8108.687013]  [<ffffffff810b54dc>] note_interrupt+0x18c/0x1d0
[ 8108.687018]  [<ffffffff810b5b55>] handle_fasteoi_irq+0xd5/0x100
[ 8108.687024]  [<ffffffff81014c1d>] handle_irq+0x1d/0x30
[ 8108.687028]  [<ffffffff810140f7>] do_IRQ+0x67/0xe0
[ 8108.687034]  [<ffffffff81012a13>] ret_from_intr+0x0/0x11
[ 8108.687037]  <EOI> 
[ 8108.687041] handlers:
[ 8108.687044] [<ffffffff8139cc30>] (usb_hcd_irq+0x0/0x80)
[ 8108.687053] [<ffffffffa0150140>] (jmb38x_ms_isr+0x0/0x210 [jmb38x_ms])
[ 8108.687075] Disabling IRQ #18
[ 8108.725092] Registered led device: iwl-phy0::radio
[ 8108.725137] Registered led device: iwl-phy0::assoc
[ 8108.725177] Registered led device: iwl-phy0::RX
[ 8108.725218] Registered led device: iwl-phy0::TX
[ 8108.792573] usb 7-2: new low speed USB device using uhci_hcd and address 2
[ 8108.803244] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[ 8108.804414] jme 0000:06:00.5: PME# disabled
[ 8108.804526] jme 0000:06:00.5: irq 30 for MSI/MSI-X
[ 8108.804613] eth0: Link is down.
[ 8108.804909] eth0: Link is down.
[ 8108.805252] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 8108.985306] usb 7-2: configuration #1 chosen from 1 choice
[ 8109.106150] usbcore: registered new interface driver hiddev
[ 8109.106291] usbcore: registered new interface driver usbhid
[ 8109.106295] usbhid: v2.6:USB HID core driver
[ 8109.229595] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.1/usb7/7-2/7-2:1.0/input/input9
[ 8109.229705] logitech 0003:046D:C517.0001: input,hidraw0: USB HID v1.10 Keyboard [Logitech USB Receiver] on usb-0000:00:1d.1-2/input0
[ 8109.261239] logitech 0003:046D:C517.0002: fixing up Logitech keyboard report descriptor
[ 8109.263418] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.1/usb7/7-2/7-2:1.1/input/input10
[ 8109.263998] logitech 0003:046D:C517.0002: input,hiddev96,hidraw1: USB HID v1.10 Mouse [Logitech USB Receiver] on usb-0000:00:1d.1-2/input1
[ 8111.541210] cfg80211: Found new beacon on frequency: 5745 MHz (Ch 149) on phy0
[ 8115.204656] wlan1: authenticate with AP 00:21:91:dc:b0:17
[ 8115.207122] wlan1: authenticated
[ 8115.207129] wlan1: associate with AP 00:21:91:dc:b0:17
[ 8115.211016] wlan1: RX AssocResp from 00:21:91:dc:b0:17 (capab=0x431 status=0 aid=5)
[ 8115.211025] wlan1: associated
[ 8115.216108] ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[ 8117.272907] iwlagn 0000:02:00.0: iwl_tx_agg_start on ra = 00:21:91:dc:b0:17 tid = 0
[ 8125.390051] wlan1: no IPv6 routers present
[ 8136.480891] i2c-adapter i2c-2: unable to read EDID block.
[ 8136.480897] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[ 8136.485868] i2c-adapter i2c-2: unable to read EDID block.
[ 8136.485873] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[ 8136.490534] i2c-adapter i2c-4: unable to read EDID block.
[ 8136.490539] i915 0000:00:02.0: HDMI Type A-2: no EDID data
[ 8136.495793] i2c-adapter i2c-4: unable to read EDID block.
[ 8136.495798] i915 0000:00:02.0: HDMI Type A-2: no EDID data
[ 8136.801848] [drm] DAC-6: set mode  19
[ 8157.937125] i2c-adapter i2c-2: unable to read EDID block.
[ 8157.937131] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[ 8157.941589] i2c-adapter i2c-2: unable to read EDID block.
[ 8157.941592] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[ 8157.946360] i2c-adapter i2c-4: unable to read EDID block.
[ 8157.946365] i915 0000:00:02.0: HDMI Type A-2: no EDID data
[ 8157.950845] i2c-adapter i2c-4: unable to read EDID block.
[ 8157.950849] i915 0000:00:02.0: HDMI Type A-2: no EDID data
[ 8158.276830] i2c-adapter i2c-2: unable to read EDID block.
[ 8158.276836] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[ 8158.281315] i2c-adapter i2c-2: unable to read EDID block.
[ 8158.281319] i915 0000:00:02.0: HDMI Type A-1: no EDID data
[ 8158.286092] i2c-adapter i2c-4: unable to read EDID block.
[ 8158.286096] i915 0000:00:02.0: HDMI Type A-2: no EDID data
[ 8158.290576] i2c-adapter i2c-4: unable to read EDID block.
[ 8158.290580] i915 0000:00:02.0: HDMI Type A-2: no EDID data
[ 8158.970582] [drm] DAC-6: set mode  28
[ 8341.135577] npviewer.bin[5295]: segfault at ff99cd48 ip 00000000ff99cd48 sp 00000000ffc73bac error 14

---

### Post by topher80 on 2009-11-25
Thank you!

---

