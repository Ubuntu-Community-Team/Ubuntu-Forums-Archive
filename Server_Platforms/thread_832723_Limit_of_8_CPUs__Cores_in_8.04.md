---
title: "Limit of 8 CPUs / Cores in 8.04 ???"
date: 2008-06-18
forum: Server Platforms
---

### Post by oakey_99 on 2008-06-18
Is Ubuntu 8.04 32bit install limited to 8 processors ???

I have the correct SMP kernel. Server has 8 hyper threaded CPU's (So 8 x 2 = 16 total) but will only start up and use 8. BIOS see's all 16 processors etc etc.

$ uname -a
2.6.24-17-server #1 SMP Thu May 1 15:05:55 UTC 2008 i686 GNU/Linux
..................................................................
Messages Log File:

Jun 18 10:19:56 plat-vm-host-3 kernel: Inspecting /boot/System.map-2.6.24-17-server
Jun 18 10:19:56 plat-vm-host-3 kernel: Loaded 28739 symbols from /boot/System.map-2.6.24-17-server.
Jun 18 10:19:56 plat-vm-host-3 kernel: Symbols match kernel version 2.6.24.
Jun 18 10:19:56 plat-vm-host-3 kernel: Loaded 12253 symbols from 65 modules.
Jun 18 10:19:56 plat-vm-host-3 kernel: [    0.000000] Initializing cgroup subsys cpuset
Jun 18 10:19:56 plat-vm-host-3 kernel: [    0.000000] Initializing cgroup subsys cpu
Jun 18 10:19:56 plat-vm-host-3 kernel: [    0.000000] Linux version 2.6.24-17-server (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Thu May 1 15:05:55 UTC 2008 (Ubuntu 2.6.24-17.31-server)
Jun 18 10:19:56 plat-vm-host-3 kernel: [    0.000000] BIOS-provided physical RAM map:
Jun 18 10:19:56 plat-vm-host-3 kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f400 (usable)
Jun 18 10:19:56 plat-vm-host-3 kernel: [    0.000000]  BIOS-e820: 000000000009f400 - 00000000000a0000 (reserved)
Jun 18 10:19:56 plat-vm-host-3 kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Jun 18 10:19:56 plat-vm-host-3 kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 00000000efff0000 (usable)
Jun 18 10:19:56 plat-vm-host-3 kernel: [    0.000000]  BIOS-e820: 00000000efff0000 - 00000000f0000000 (ACPI data)
Jun 18 10:19:56 plat-vm-host-3 kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
Jun 18 10:19:56 plat-vm-host-3 kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee10000 (reserved)
Jun 18 10:19:56 plat-vm-host-3 kernel: [    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
Jun 18 10:19:56 plat-vm-host-3 kernel: [    0.000000]  BIOS-e820: 0000000100000000 - 000000030ffff000 (usable)
Jun 18 10:19:56 plat-vm-host-3 kernel: [    0.000000] 11647MB HIGHMEM available.
Jun 18 10:19:56 plat-vm-host-3 kernel: [    0.000000] 896MB LOWMEM available.
Jun 18 10:19:56 plat-vm-host-3 kernel: [    0.000000] found SMP MP-table at 000f4fd0
Jun 18 10:19:56 plat-vm-host-3 kernel: [    0.000000] Zone PFN ranges:
Jun 18 10:19:56 plat-vm-host-3 kernel: [    0.000000]   DMA             0 ->     4096
Jun 18 10:19:56 plat-vm-host-3 kernel: [    0.000000]   Normal       4096 ->   229376
Jun 18 10:19:56 plat-vm-host-3 kernel: [    0.000000]   HighMem    229376 ->  3211263
Jun 18 10:19:56 plat-vm-host-3 kernel: [    0.000000] Movable zone start PFN for each node
Jun 18 10:19:56 plat-vm-host-3 kernel: [    0.000000] early_node_map[1] active PFN ranges
Jun 18 10:19:56 plat-vm-host-3 kernel: [    0.000000]     0:        0 ->  3211263
Jun 18 10:19:56 plat-vm-host-3 kernel: [    0.000000] DMI 2.3 present.
Jun 18 10:19:56 plat-vm-host-3 kernel: [    0.000000] ACPI: RSDP signature @ 0xC00F4F70 checksum 0
Jun 18 10:19:56 plat-vm-host-3 kernel: [    0.000000] ACPI: RSDP 000F4F70, 0014 (r0 HP    )
Jun 18 10:19:56 plat-vm-host-3 kernel: [    0.000000] ACPI: RSDT EFFF0000, 0038 (r1 HP     P44             1             0)
Jun 18 10:19:56 plat-vm-host-3 kernel: [    0.000000] ACPI: FACP EFFF0040, 0074 (r1 HP     P44             1             0)
Jun 18 10:19:56 plat-vm-host-3 kernel: [    0.000000] ACPI: DSDT EFFF0288, 5D4C (r1 HP     P44             1 MSFT  100000B)
Jun 18 10:19:56 plat-vm-host-3 kernel: [    0.000000] ACPI: FACS EFFF00C0, 0040
Jun 18 10:19:56 plat-vm-host-3 kernel: [    0.000000] ACPI: APIC EFFF0100, 00E0 (r1 HP     P44             1             0)
Jun 18 10:19:56 plat-vm-host-3 kernel: [    0.000000] ACPI: SRAT EFFF01E0, 0058 (r1 HP     P44             3             0)
Jun 18 10:19:56 plat-vm-host-3 kernel: [    0.000000] ACPI: SPCR EFFF0238, 0050 (r1 HP     SPCR_ROM        1             0)
Jun 18 10:19:56 plat-vm-host-3 kernel: [    0.000000] ACPI: SSDT EFFF8000, 4FAE (r1 HP     P44             2 MSFT  100000B)
Jun 18 10:19:56 plat-vm-host-3 kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x920
Jun 18 10:19:56 plat-vm-host-3 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Jun 18 10:19:56 plat-vm-host-3 kernel: [    0.000000] Processor #0 15:2 APIC version 20
Jun 18 10:19:56 plat-vm-host-3 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
Jun 18 10:19:56 plat-vm-host-3 kernel: [    0.000000] Processor #1 15:2 APIC version 20
Jun 18 10:19:56 plat-vm-host-3 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] enabled)
Jun 18 10:19:56 plat-vm-host-3 kernel: [    0.000000] Processor #2 15:2 APIC version 20
Jun 18 10:19:56 plat-vm-host-3 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
Jun 18 10:19:56 plat-vm-host-3 kernel: [    0.000000] Processor #3 15:2 APIC version 20
Jun 18 10:19:56 plat-vm-host-3 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x04] enabled)
Jun 18 10:19:56 plat-vm-host-3 kernel: [    0.000000] Processor #4 15:2 APIC version 20
Jun 18 10:19:56 plat-vm-host-3 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x05] enabled)
Jun 18 10:19:56 plat-vm-host-3 kernel: [    0.000000] Processor #5 15:2 APIC version 20
Jun 18 10:19:56 plat-vm-host-3 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x06] enabled)
Jun 18 10:19:56 plat-vm-host-3 kernel: [    0.000000] Processor #6 15:2 APIC version 20
Jun 18 10:19:56 plat-vm-host-3 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x07] enabled)
Jun 18 10:19:56 plat-vm-host-3 kernel: [    0.000000] Processor #7 15:2 APIC version 20
Jun 18 10:19:56 plat-vm-host-3 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x09] lapic_id[0x08] enabled)
Jun 18 10:19:56 plat-vm-host-3 kernel: [    0.000000] Processor #8 15:2 APIC version 20
Jun 18 10:19:56 plat-vm-host-3 kernel: [    0.000000] WARNING: NR_CPUS limit of 8 reached.  Processor ignored.
Jun 18 10:19:56 plat-vm-host-3 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x0a] lapic_id[0x09] enabled)
Jun 18 10:19:56 plat-vm-host-3 kernel: [    0.000000] Processor #9 15:2 APIC version 20
Jun 18 10:19:56 plat-vm-host-3 kernel: [    0.000000] WARNING: NR_CPUS limit of 8 reached.  Processor ignored.
Jun 18 10:19:56 plat-vm-host-3 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x0b] lapic_id[0x0a] enabled)
Jun 18 10:19:56 plat-vm-host-3 kernel: [    0.000000] Processor #10 15:2 APIC version 20
Jun 18 10:19:56 plat-vm-host-3 kernel: [    0.000000] WARNING: NR_CPUS limit of 8 reached.  Processor ignored.
Jun 18 10:19:56 plat-vm-host-3 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x0c] lapic_id[0x0b] enabled)
Jun 18 10:19:56 plat-vm-host-3 kernel: [    0.000000] Processor #11 15:2 APIC version 20
Jun 18 10:19:56 plat-vm-host-3 kernel: [    0.000000] WARNING: NR_CPUS limit of 8 reached.  Processor ignored.
Jun 18 10:19:56 plat-vm-host-3 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x0d] lapic_id[0x0c] enabled)
Jun 18 10:19:56 plat-vm-host-3 kernel: [    0.000000] Processor #12 15:2 APIC version 20
Jun 18 10:19:56 plat-vm-host-3 kernel: [    0.000000] WARNING: NR_CPUS limit of 8 reached.  Processor ignored.
Jun 18 10:19:56 plat-vm-host-3 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x0e] lapic_id[0x0d] enabled)
Jun 18 10:19:56 plat-vm-host-3 kernel: [    0.000000] Processor #13 15:2 APIC version 20
Jun 18 10:19:56 plat-vm-host-3 kernel: [    0.000000] WARNING: NR_CPUS limit of 8 reached.  Processor ignored.
Jun 18 10:19:56 plat-vm-host-3 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x0f] lapic_id[0x0e] enabled)
Jun 18 10:19:56 plat-vm-host-3 kernel: [    0.000000] Processor #14 15:2 APIC version 20
Jun 18 10:19:56 plat-vm-host-3 kernel: [    0.000000] WARNING: NR_CPUS limit of 8 reached.  Processor ignored.
Jun 18 10:19:56 plat-vm-host-3 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x10] lapic_id[0x0f] enabled)
Jun 18 10:19:56 plat-vm-host-3 kernel: [    0.000000] Processor #15 15:2 APIC version 20
Jun 18 10:19:56 plat-vm-host-3 kernel: [    0.000000] WARNING: NR_CPUS limit of 8 reached.  Processor ignored.
Jun 18 10:19:56 plat-vm-host-3 kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0xff] dfl dfl lint[0x1])
Jun 18 10:19:56 plat-vm-host-3 kernel: [    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
Jun 18 10:19:56 plat-vm-host-3 kernel: [    0.000000] IOAPIC[0]: apic_id 1, version 17, address 0xfec00000, GSI 0-15
Jun 18 10:19:56 plat-vm-host-3 kernel: [    0.000000] ACPI: IOAPIC (id[0x03] address[0xfec01000] gsi_base[16])
Jun 18 10:19:56 plat-vm-host-3 kernel: [    0.000000] IOAPIC[1]: apic_id 3, version 17, address 0xfec01000, GSI 16-31
Jun 18 10:19:56 plat-vm-host-3 kernel: [    0.000000] ACPI: IOAPIC (id[0x05] address[0xfec02000] gsi_base[32])
Jun 18 10:19:56 plat-vm-host-3 kernel: [    0.000000] IOAPIC[2]: apic_id 5, version 17, address 0xfec02000, GSI 32-47
Jun 18 10:19:56 plat-vm-host-3 kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
Jun 18 10:19:56 plat-vm-host-3 kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 3 I/O APICs
Jun 18 10:19:56 plat-vm-host-3 kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Jun 18 10:19:56 plat-vm-host-3 kernel: [    0.000000] Allocating PCI resources starting at f1000000 (gap: f0000000:0ec00000)
Jun 18 10:19:56 plat-vm-host-3 kernel: [    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
Jun 18 10:19:56 plat-vm-host-3 kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
Jun 18 10:19:56 plat-vm-host-3 kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
Jun 18 10:19:56 plat-vm-host-3 kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 3186176
Jun 18 10:19:56 plat-vm-host-3 kernel: [    0.000000] Kernel command line: root=UUID=ad403fdb-4edd-48df-8c1c-1aeff0b0b904 ro quiet splash
Jun 18 10:19:56 plat-vm-host-3 kernel: [    0.000000] Enabling fast FPU save and restore... done.
Jun 18 10:19:56 plat-vm-host-3 kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Jun 18 10:19:56 plat-vm-host-3 kernel: [    0.000000] Initializing CPU#0
Jun 18 10:19:56 plat-vm-host-3 kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Jun 18 10:19:56 plat-vm-host-3 kernel: [    0.000000] Detected 2997.795 MHz processor.
Jun 18 10:19:56 plat-vm-host-3 kernel: [   96.590419] Console: colour VGA+ 80x25
Jun 18 10:19:56 plat-vm-host-3 kernel: [   96.590425] console [tty0] enabled
Jun 18 10:19:56 plat-vm-host-3 kernel: [   96.593561] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Jun 18 10:19:56 plat-vm-host-3 kernel: [   96.595295] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Jun 18 10:19:56 plat-vm-host-3 kernel: [   98.232371] Memory: 12468504k/12845052k available (2255k kernel code, 113060k reserved, 1032k data, 384k init, 11665340k highmem)
Jun 18 10:19:56 plat-vm-host-3 kernel: [   98.232390] virtual kernel memory layout:
Jun 18 10:19:56 plat-vm-host-3 kernel: [   98.232391]     fixmap  : 0xfff4c000 - 0xfffff000   ( 716 kB)
Jun 18 10:19:56 plat-vm-host-3 kernel: [   98.232392]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
Jun 18 10:19:56 plat-vm-host-3 kernel: [   98.232393]     vmalloc : 0xf8800000 - 0xffbfe000   ( 115 MB)
Jun 18 10:19:56 plat-vm-host-3 kernel: [   98.232394]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
Jun 18 10:19:56 plat-vm-host-3 kernel: [   98.232396]       .init : 0xc043c000 - 0xc049c000   ( 384 kB)
Jun 18 10:19:56 plat-vm-host-3 kernel: [   98.232397]       .data : 0xc0333ef5 - 0xc0435fe4   (1032 kB)
Jun 18 10:19:56 plat-vm-host-3 kernel: [   98.232398]       .text : 0xc0100000 - 0xc0333ef5   (2255 kB)
Jun 18 10:19:56 plat-vm-host-3 kernel: [   98.232401] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Jun 18 10:19:56 plat-vm-host-3 kernel: [   98.232504] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=8, Nodes=1
Jun 18 10:19:56 plat-vm-host-3 kernel: [   98.382278] Calibrating delay using timer specific routine.. 6000.21 BogoMIPS (lpj=30001074)
Jun 18 10:19:56 plat-vm-host-3 kernel: [   98.382371] Security Framework initialized
Jun 18 10:19:56 plat-vm-host-3 kernel: [   98.382390] SELinux:  Disabled at boot.
Jun 18 10:19:56 plat-vm-host-3 kernel: [   98.382466] AppArmor: AppArmor initialized
Jun 18 10:19:56 plat-vm-host-3 kernel: [   98.382474] Failure registering capabilities with primary security module.
Jun 18 10:19:56 plat-vm-host-3 kernel: [   98.382490] Mount-cache hash table entries: 512
Jun 18 10:19:56 plat-vm-host-3 kernel: [   98.382918] Initializing cgroup subsys ns
Jun 18 10:19:56 plat-vm-host-3 kernel: [   98.382925] Initializing cgroup subsys cpuacct
Jun 18 10:19:56 plat-vm-host-3 kernel: [   98.382964] CPU: Trace cache: 12K uops, L1 D cache: 8K
Jun 18 10:19:56 plat-vm-host-3 kernel: [   98.382967] CPU: L2 cache: 512K
Jun 18 10:19:56 plat-vm-host-3 kernel: [   98.382968] CPU: L3 cache: 4096K
Jun 18 10:19:56 plat-vm-host-3 kernel: [   98.382972] CPU: Physical Processor ID: 0
Jun 18 10:19:56 plat-vm-host-3 kernel: [   98.383010] Compat vDSO mapped to ffffe000.
Jun 18 10:19:56 plat-vm-host-3 kernel: [   98.383035] Checking 'hlt' instruction... OK.
Jun 18 10:19:56 plat-vm-host-3 kernel: [   98.422894] SMP alternatives: switching to UP code
Jun 18 10:19:56 plat-vm-host-3 kernel: [   98.425327] Early unpacking initramfs... done
Jun 18 10:19:56 plat-vm-host-3 kernel: [   98.794192] ACPI: Core revision 20070126
Jun 18 10:19:56 plat-vm-host-3 kernel: [   98.794475] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Jun 18 10:19:56 plat-vm-host-3 kernel: [   98.799998] CPU0: Intel(R) Xeon(TM) MP CPU 3.00GHz stepping 06
Jun 18 10:19:56 plat-vm-host-3 kernel: [   98.800044] SMP alternatives: switching to SMP code
Jun 18 10:19:56 plat-vm-host-3 kernel: [   98.801199] Booting processor 1/1 eip 3000
Jun 18 10:19:56 plat-vm-host-3 kernel: [   98.812086] Initializing CPU#1
Jun 18 10:19:56 plat-vm-host-3 kernel: [   98.961271] Calibrating delay using timer specific routine.. 5995.55 BogoMIPS (lpj=29977770)
Jun 18 10:19:56 plat-vm-host-3 kernel: [   98.961304] CPU: Trace cache: 12K uops, L1 D cache: 8K
Jun 18 10:19:56 plat-vm-host-3 kernel: [   98.961307] CPU: L2 cache: 512K
Jun 18 10:19:56 plat-vm-host-3 kernel: [   98.961308] CPU: L3 cache: 4096K
Jun 18 10:19:56 plat-vm-host-3 kernel: [   98.961312] CPU: Physical Processor ID: 0
Jun 18 10:19:56 plat-vm-host-3 kernel: [   98.962429] CPU1: Intel(R) Xeon(TM) MP CPU 3.00GHz stepping 06
Jun 18 10:19:56 plat-vm-host-3 kernel: [   98.962522] SMP alternatives: switching to SMP code
Jun 18 10:19:56 plat-vm-host-3 kernel: [   98.963763] Booting processor 2/2 eip 3000
Jun 18 10:19:56 plat-vm-host-3 kernel: [   98.974585] Initializing CPU#2
Jun 18 10:19:56 plat-vm-host-3 kernel: [   99.120995] Calibrating delay using timer specific routine.. 5995.72 BogoMIPS (lpj=29978628)
Jun 18 10:19:56 plat-vm-host-3 kernel: [   99.121025] CPU: Trace cache: 12K uops, L1 D cache: 8K
Jun 18 10:19:56 plat-vm-host-3 kernel: [   99.121027] CPU: L2 cache: 512K
Jun 18 10:19:56 plat-vm-host-3 kernel: [   99.121029] CPU: L3 cache: 4096K
Jun 18 10:19:56 plat-vm-host-3 kernel: [   99.121032] CPU: Physical Processor ID: 1
Jun 18 10:19:56 plat-vm-host-3 kernel: [   99.122161] CPU2: Intel(R) Xeon(TM) MP CPU 3.00GHz stepping 06
Jun 18 10:19:56 plat-vm-host-3 kernel: [   99.122202] SMP alternatives: switching to SMP code
Jun 18 10:19:56 plat-vm-host-3 kernel: [   99.122679] Booting processor 3/3 eip 3000
Jun 18 10:19:56 plat-vm-host-3 kernel: [   99.133600] Initializing CPU#3
Jun 18 10:19:56 plat-vm-host-3 kernel: [   99.280718] Calibrating delay using timer specific routine.. 5995.76 BogoMIPS (lpj=29978837)
Jun 18 10:19:56 plat-vm-host-3 kernel: [   99.280751] CPU: Trace cache: 12K uops, L1 D cache: 8K
Jun 18 10:19:56 plat-vm-host-3 kernel: [   99.280754] CPU: L2 cache: 512K
Jun 18 10:19:56 plat-vm-host-3 kernel: [   99.280755] CPU: L3 cache: 4096K
Jun 18 10:19:56 plat-vm-host-3 kernel: [   99.280758] CPU: Physical Processor ID: 1
Jun 18 10:19:56 plat-vm-host-3 kernel: [   99.281867] CPU3: Intel(R) Xeon(TM) MP CPU 3.00GHz stepping 06
Jun 18 10:19:56 plat-vm-host-3 kernel: [   99.281908] SMP alternatives: switching to SMP code
Jun 18 10:19:56 plat-vm-host-3 kernel: [   99.282385] Booting processor 4/4 eip 3000
Jun 18 10:19:56 plat-vm-host-3 kernel: [   99.293304] Initializing CPU#4
Jun 18 10:19:56 plat-vm-host-3 kernel: [   99.440441] Calibrating delay using timer specific routine.. 5995.79 BogoMIPS (lpj=29978974)
Jun 18 10:19:56 plat-vm-host-3 kernel: [   99.440471] CPU: Trace cache: 12K uops, L1 D cache: 8K
Jun 18 10:19:56 plat-vm-host-3 kernel: [   99.440473] CPU: L2 cache: 512K
Jun 18 10:19:56 plat-vm-host-3 kernel: [   99.440475] CPU: L3 cache: 4096K
Jun 18 10:19:56 plat-vm-host-3 kernel: [   99.440477] CPU: Physical Processor ID: 2
Jun 18 10:19:56 plat-vm-host-3 kernel: [   99.441574] CPU4: Intel(R) Xeon(TM) MP CPU 3.00GHz stepping 06
Jun 18 10:19:56 plat-vm-host-3 kernel: [   99.441612] SMP alternatives: switching to SMP code
Jun 18 10:19:56 plat-vm-host-3 kernel: [   99.442087] Booting processor 5/5 eip 3000
Jun 18 10:19:56 plat-vm-host-3 kernel: [   99.453009] Initializing CPU#5
Jun 18 10:19:56 plat-vm-host-3 kernel: [   99.600164] Calibrating delay using timer specific routine.. 5995.74 BogoMIPS (lpj=29978745)
Jun 18 10:19:56 plat-vm-host-3 kernel: [   99.600196] CPU: Trace cache: 12K uops, L1 D cache: 8K
Jun 18 10:19:56 plat-vm-host-3 kernel: [   99.600199] CPU: L2 cache: 512K
Jun 18 10:19:56 plat-vm-host-3 kernel: [   99.600201] CPU: L3 cache: 4096K
Jun 18 10:19:56 plat-vm-host-3 kernel: [   99.600204] CPU: Physical Processor ID: 2
Jun 18 10:19:56 plat-vm-host-3 kernel: [   99.601282] CPU5: Intel(R) Xeon(TM) MP CPU 3.00GHz stepping 06
Jun 18 10:19:56 plat-vm-host-3 kernel: [   99.601322] SMP alternatives: switching to SMP code
Jun 18 10:19:56 plat-vm-host-3 kernel: [   99.601799] Booting processor 6/6 eip 3000
Jun 18 10:19:56 plat-vm-host-3 kernel: [   99.612717] Initializing CPU#6
Jun 18 10:19:56 plat-vm-host-3 kernel: [   99.759887] Calibrating delay using timer specific routine.. 5995.76 BogoMIPS (lpj=29978833)
Jun 18 10:19:56 plat-vm-host-3 kernel: [   99.759917] CPU: Trace cache: 12K uops, L1 D cache: 8K
Jun 18 10:19:56 plat-vm-host-3 kernel: [   99.759919] CPU: L2 cache: 512K
Jun 18 10:19:56 plat-vm-host-3 kernel: [   99.759921] CPU: L3 cache: 4096K
Jun 18 10:19:56 plat-vm-host-3 kernel: [   99.759923] CPU: Physical Processor ID: 3
Jun 18 10:19:56 plat-vm-host-3 kernel: [   99.760990] CPU6: Intel(R) Xeon(TM) MP CPU 3.00GHz stepping 06
Jun 18 10:19:56 plat-vm-host-3 kernel: [   99.761026] SMP alternatives: switching to SMP code
Jun 18 10:19:56 plat-vm-host-3 kernel: [   99.761503] Booting processor 7/7 eip 3000
Jun 18 10:19:56 plat-vm-host-3 kernel: [   99.772425] Initializing CPU#7
Jun 18 10:19:56 plat-vm-host-3 kernel: [   99.919610] Calibrating delay using timer specific routine.. 5995.83 BogoMIPS (lpj=29979175)
Jun 18 10:19:56 plat-vm-host-3 kernel: [   99.919642] CPU: Trace cache: 12K uops, L1 D cache: 8K
Jun 18 10:19:56 plat-vm-host-3 kernel: [   99.919645] CPU: L2 cache: 512K
Jun 18 10:19:56 plat-vm-host-3 kernel: [   99.919647] CPU: L3 cache: 4096K
Jun 18 10:19:56 plat-vm-host-3 kernel: [   99.919650] CPU: Physical Processor ID: 3
Jun 18 10:19:56 plat-vm-host-3 kernel: [   99.920790] CPU7: Intel(R) Xeon(TM) MP CPU 3.00GHz stepping 06
Jun 18 10:19:56 plat-vm-host-3 kernel: [   99.920811] Total of 8 processors activated (47970.40 BogoMIPS).
Jun 18 10:19:56 plat-vm-host-3 kernel: [   99.921352] ENABLING IO-APIC IRQs
Jun 18 10:19:56 plat-vm-host-3 kernel: [   99.921611] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Jun 18 10:19:56 plat-vm-host-3 kernel: [  100.139597] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
Jun 18 10:19:56 plat-vm-host-3 kernel: [  100.159735] checking TSC synchronization [CPU#0 -> CPU#2]: passed.
Jun 18 10:19:56 plat-vm-host-3 kernel: [  100.179906] checking TSC synchronization [CPU#0 -> CPU#3]: passed.
Jun 18 10:19:56 plat-vm-host-3 kernel: [  100.200057] checking TSC synchronization [CPU#0 -> CPU#4]: passed.
Jun 18 10:19:56 plat-vm-host-3 kernel: [  100.220228] checking TSC synchronization [CPU#0 -> CPU#5]: passed.
Jun 18 10:19:56 plat-vm-host-3 kernel: [  100.240388] checking TSC synchronization [CPU#0 -> CPU#6]: passed.
Jun 18 10:19:56 plat-vm-host-3 kernel: [  100.260560] checking TSC synchronization [CPU#0 -> CPU#7]: passed.
Jun 18 10:19:56 plat-vm-host-3 kernel: [  100.280571] Brought up 8 CPUs
Jun 18 10:19:56 plat-vm-host-3 kernel: [  100.281925] net_namespace: 64 bytes
Jun 18 10:19:56 plat-vm-host-3 kernel: [  100.281939] Booting paravirtualized kernel on bare hardware
Jun 18 10:19:56 plat-vm-host-3 kernel: [  100.282597] Time:  0:19:14  Date: 06/18/08
Jun 18 10:19:56 plat-vm-host-3 kernel: [  100.282690] NET: Registered protocol family 16
Jun 18 10:19:56 plat-vm-host-3 kernel: [  100.283108] EISA bus registered
Jun 18 10:19:56 plat-vm-host-3 kernel: [  100.283117] ACPI: bus type pci registered
Jun 18 10:19:56 plat-vm-host-3 kernel: [  100.283714] PCI: PCI BIOS revision 2.10 entry at 0xf1135, last bus=22
Jun 18 10:19:56 plat-vm-host-3 kernel: [  100.283718] PCI: Using configuration type 1
Jun 18 10:19:56 plat-vm-host-3 kernel: [  100.283722] Setting up standard PCI resources
Jun 18 10:19:56 plat-vm-host-3 kernel: [  100.310474] ACPI: Interpreter enabled
Jun 18 10:19:56 plat-vm-host-3 kernel: [  100.310479] ACPI: (supports S0 S4 S5)
Jun 18 10:19:56 plat-vm-host-3 kernel: [  100.310493] ACPI: Using IOAPIC for interrupt routing
Jun 18 10:19:56 plat-vm-host-3 kernel: [  100.324935] ACPI: PCI Root Bridge [PCI0] (0000:00)
Jun 18 10:19:56 plat-vm-host-3 kernel: [  100.329907] ACPI: PCI Root Bridge [PCI1] (0000:03)
Jun 18 10:19:56 plat-vm-host-3 kernel: [  100.330548] ACPI: PCI Root Bridge [PCI2] (0000:07)
Jun 18 10:19:56 plat-vm-host-3 kernel: [  100.331197] ACPI: PCI Root Bridge [PCI3] (0000:0b)
Jun 18 10:19:56 plat-vm-host-3 kernel: [  100.331824] ACPI: PCI Root Bridge [PCI4] (0000:0f)
Jun 18 10:19:56 plat-vm-host-3 kernel: [  100.332451] ACPI: PCI Root Bridge [PCI5] (0000:13)
Jun 18 10:19:56 plat-vm-host-3 kernel: [  100.333714] ACPI: PCI Interrupt Link [IUSB] (IRQs *10)
Jun 18 10:19:56 plat-vm-host-3 kernel: [  100.333859] ACPI: Invalid IRQ 0
Jun 18 10:19:56 plat-vm-host-3 kernel: [  100.333959] ACPI: PCI Interrupt Link [IN16] (IRQs) *0, disabled.
Jun 18 10:19:56 plat-vm-host-3 kernel: [  100.334105] ACPI: Invalid IRQ 0
Jun 18 10:19:56 plat-vm-host-3 kernel: [  100.334207] ACPI: PCI Interrupt Link [IN17] (IRQs) *0, disabled.
Jun 18 10:19:56 plat-vm-host-3 kernel: [  100.334347] ACPI: Invalid IRQ 0
Jun 18 10:19:56 plat-vm-host-3 kernel: [  100.334447] ACPI: PCI Interrupt Link [IN18] (IRQs) *0, disabled.
Jun 18 10:19:56 plat-vm-host-3 kernel: [  100.334587] ACPI: Invalid IRQ 0
Jun 18 10:19:56 plat-vm-host-3 kernel: [  100.334686] ACPI: PCI Interrupt Link [IN19] (IRQs) *0, disabled.
Jun 18 10:19:56 plat-vm-host-3 kernel: [  100.334827] ACPI: Invalid IRQ 0
Jun 18 10:19:56 plat-vm-host-3 kernel: [  100.334928] ACPI: PCI Interrupt Link [IN20] (IRQs) *0, disabled.
Jun 18 10:19:56 plat-vm-host-3 kernel: [  100.335068] ACPI: Invalid IRQ 0
Jun 18 10:19:56 plat-vm-host-3 kernel: [  100.335170] ACPI: PCI Interrupt Link [IN21] (IRQs) *0, disabled.
Jun 18 10:19:56 plat-vm-host-3 kernel: [  100.335310] ACPI: Invalid IRQ 0
Jun 18 10:19:56 plat-vm-host-3 kernel: [  100.335411] ACPI: PCI Interrupt Link [IN22] (IRQs) *0, disabled.
Jun 18 10:19:56 plat-vm-host-3 kernel: [  100.335553] ACPI: Invalid IRQ 0
Jun 18 10:19:56 plat-vm-host-3 kernel: [  100.335655] ACPI: PCI Interrupt Link [IN23] (IRQs) *0, disabled.
Jun 18 10:19:56 plat-vm-host-3 kernel: [  100.335796] ACPI: Invalid IRQ 0
Jun 18 10:19:56 plat-vm-host-3 kernel: [  100.335898] ACPI: PCI Interrupt Link [IN24] (IRQs) *0, disabled.
Jun 18 10:19:56 plat-vm-host-3 kernel: [  100.336040] ACPI: Invalid IRQ 0
Jun 18 10:19:56 plat-vm-host-3 kernel: [  100.336140] ACPI: PCI Interrupt Link [IN25] (IRQs) *0, disabled.
Jun 18 10:19:56 plat-vm-host-3 kernel: [  100.336283] ACPI: Invalid IRQ 0
Jun 18 10:19:56 plat-vm-host-3 kernel: [  100.336408] ACPI: PCI Interrupt Link [IN26] (IRQs) *0, disabled.
Jun 18 10:19:56 plat-vm-host-3 kernel: [  100.336552] ACPI: Invalid IRQ 0
Jun 18 10:19:56 plat-vm-host-3 kernel: [  100.336652] ACPI: PCI Interrupt Link [IN27] (IRQs) *0, disabled.
Jun 18 10:19:56 plat-vm-host-3 kernel: [  100.336793] ACPI: Invalid IRQ 0
Jun 18 10:19:56 plat-vm-host-3 kernel: [  100.336892] ACPI: PCI Interrupt Link [IN28] (IRQs) *0, disabled.
Jun 18 10:19:56 plat-vm-host-3 kernel: [  100.337036] ACPI: Invalid IRQ 0
Jun 18 10:19:56 plat-vm-host-3 kernel: [  100.337136] ACPI: PCI Interrupt Link [IN29] (IRQs) *0, disabled.
Jun 18 10:19:56 plat-vm-host-3 kernel: [  100.337374] ACPI: PCI Interrupt Link [IN30] (IRQs *11)
Jun 18 10:19:56 plat-vm-host-3 kernel: [  100.337613] ACPI: PCI Interrupt Link [IN31] (IRQs *3)
Jun 18 10:19:56 plat-vm-host-3 kernel: [  100.337849] ACPI: PCI Interrupt Link [IN32] (IRQs *11)
Jun 18 10:19:56 plat-vm-host-3 kernel: [  100.337989] ACPI: Invalid IRQ 0
Jun 18 10:19:56 plat-vm-host-3 kernel: [  100.338087] ACPI: PCI Interrupt Link [IN33] (IRQs) *0, disabled.
Jun 18 10:19:56 plat-vm-host-3 kernel: [  100.338228] ACPI: Invalid IRQ 0
Jun 18 10:19:56 plat-vm-host-3 kernel: [  100.338327] ACPI: PCI Interrupt Link [IN34] (IRQs) *0, disabled.
Jun 18 10:19:56 plat-vm-host-3 kernel: [  100.338564] ACPI: PCI Interrupt Link [IN35] (IRQs *5)
Jun 18 10:19:56 plat-vm-host-3 kernel: [  100.338705] ACPI: Invalid IRQ 0
Jun 18 10:19:56 plat-vm-host-3 kernel: [  100.338803] ACPI: PCI Interrupt Link [IN36] (IRQs) *0, disabled.
Jun 18 10:19:56 plat-vm-host-3 kernel: [  100.339046] ACPI: PCI Interrupt Link [IN37] (IRQs *3)
Jun 18 10:19:56 plat-vm-host-3 kernel: [  100.339286] ACPI: PCI Interrupt Link [IN38] (IRQs *10)
Jun 18 10:19:56 plat-vm-host-3 kernel: [  100.339523] ACPI: PCI Interrupt Link [IN39] (IRQs *11)
Jun 18 10:19:56 plat-vm-host-3 kernel: [  100.339764] ACPI: PCI Interrupt Link [IN40] (IRQs *7)
Jun 18 10:19:56 plat-vm-host-3 kernel: [  100.340008] ACPI: PCI Interrupt Link [IN41] (IRQs *5)
Jun 18 10:19:56 plat-vm-host-3 kernel: [  100.340149] ACPI: Invalid IRQ 0
Jun 18 10:19:56 plat-vm-host-3 kernel: [  100.340249] ACPI: PCI Interrupt Link [IN42] (IRQs) *0, disabled.
Jun 18 10:19:56 plat-vm-host-3 kernel: [  100.340396] ACPI: Invalid IRQ 0
Jun 18 10:19:56 plat-vm-host-3 kernel: [  100.340502] ACPI: PCI Interrupt Link [IN43] (IRQs) *0, disabled.
Jun 18 10:19:56 plat-vm-host-3 kernel: [  100.340643] ACPI: Invalid IRQ 0
Jun 18 10:19:56 plat-vm-host-3 kernel: [  100.340744] ACPI: PCI Interrupt Link [IN44] (IRQs) *0, disabled.
Jun 18 10:19:56 plat-vm-host-3 kernel: [  100.340887] ACPI: Invalid IRQ 0
Jun 18 10:19:56 plat-vm-host-3 kernel: [  100.340989] ACPI: PCI Interrupt Link [IN45] (IRQs) *0, disabled.
Jun 18 10:19:56 plat-vm-host-3 kernel: [  100.341156] ACPI: Invalid IRQ 0
Jun 18 10:19:56 plat-vm-host-3 kernel: [  100.341255] ACPI: PCI Interrupt Link [IN46] (IRQs) *0, disabled.
Jun 18 10:19:56 plat-vm-host-3 kernel: [  100.341400] ACPI: Invalid IRQ 0
Jun 18 10:19:56 plat-vm-host-3 kernel: [  100.341500] ACPI: PCI Interrupt Link [IN47] (IRQs) *0, disabled.
Jun 18 10:19:56 plat-vm-host-3 kernel: [  100.341799] Linux Plug and Play Support v0.97 (c) Adam Belay
Jun 18 10:19:56 plat-vm-host-3 kernel: [  100.341874] pnp: PnP ACPI init
Jun 18 10:19:56 plat-vm-host-3 kernel: [  100.341885] ACPI: bus type pnp registered
Jun 18 10:19:56 plat-vm-host-3 kernel: [  100.349725] pnp: PnP ACPI: found 14 devices
Jun 18 10:19:56 plat-vm-host-3 kernel: [  100.349728] ACPI: ACPI bus type pnp unregistered
Jun 18 10:19:56 plat-vm-host-3 kernel: [  100.349733] PnPBIOS: Disabled by ACPI PNP
Jun 18 10:19:56 plat-vm-host-3 kernel: [  100.350124] PCI: Using ACPI for IRQ routing
Jun 18 10:19:56 plat-vm-host-3 kernel: [  100.350128] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Jun 18 10:19:56 plat-vm-host-3 kernel: [  100.365412] PCI: Device 0000:00:0f.0 not found by BIOS
Jun 18 10:19:56 plat-vm-host-3 kernel: [  100.376810] PCI: Device 0000:00:0f.3 not found by BIOS
Jun 18 10:19:56 plat-vm-host-3 kernel: [  100.384579] PCI: Device 0000:00:17.0 not found by BIOS
Jun 18 10:19:56 plat-vm-host-3 kernel: [  100.388308] PCI: Device 0000:00:18.0 not found by BIOS
Jun 18 10:19:56 plat-vm-host-3 kernel: [  100.392042] PCI: Device 0000:00:18.2 not found by BIOS
Jun 18 10:19:56 plat-vm-host-3 kernel: [  100.395770] PCI: Device 0000:00:18.4 not found by BIOS
Jun 18 10:19:56 plat-vm-host-3 kernel: [  100.399504] PCI: Device 0000:00:18.6 not found by BIOS
Jun 18 10:19:56 plat-vm-host-3 kernel: [  100.403233] PCI: Device 0000:00:19.0 not found by BIOS
Jun 18 10:19:56 plat-vm-host-3 kernel: [  100.406961] PCI: Device 0000:00:19.2 not found by BIOS
Jun 18 10:19:56 plat-vm-host-3 kernel: [  100.488667] NET: Registered protocol family 8
Jun 18 10:19:56 plat-vm-host-3 kernel: [  100.488670] NET: Registered protocol family 20
Jun 18 10:19:56 plat-vm-host-3 kernel: [  100.488723] NetLabel: Initializing
Jun 18 10:19:56 plat-vm-host-3 kernel: [  100.488726] NetLabel:  domain hash size = 128
Jun 18 10:19:56 plat-vm-host-3 kernel: [  100.488728] NetLabel:  protocols = UNLABELED CIPSOv4
Jun 18 10:19:56 plat-vm-host-3 kernel: [  100.488754] NetLabel:  unlabeled traffic allowed by default
Jun 18 10:19:56 plat-vm-host-3 kernel: [  100.488819] AppArmor: AppArmor Filesystem Enabled
Jun 18 10:19:56 plat-vm-host-3 kernel: [  100.498627] Time: tsc clocksource has been installed.
Jun 18 10:19:56 plat-vm-host-3 kernel: [  100.538608] system 00:01: ioport range 0xf50-0xf58 has been reserved
Jun 18 10:19:56 plat-vm-host-3 kernel: [  100.538612] system 00:01: ioport range 0xf57-0xf57 has been reserved
Jun 18 10:19:56 plat-vm-host-3 kernel: [  100.538614] system 00:01: ioport range 0x700-0x76f has been reserved
Jun 18 10:19:56 plat-vm-host-3 kernel: [  100.538617] system 00:01: ioport range 0x900-0x95f has been reserved
Jun 18 10:19:56 plat-vm-host-3 kernel: [  100.538620] system 00:01: ioport range 0x800-0x81f has been reserved
Jun 18 10:19:56 plat-vm-host-3 kernel: [  100.538623] system 00:01: ioport range 0xc00-0xcd7 has been reserved
Jun 18 10:19:56 plat-vm-host-3 kernel: [  100.538626] system 00:01: ioport range 0x1000-0x107f has been reserved
Jun 18 10:19:56 plat-vm-host-3 kernel: [  100.538629] system 00:01: ioport range 0x1080-0x10ff has been reserved
Jun 18 10:19:56 plat-vm-host-3 kernel: [  100.538632] system 00:01: iomem range 0xc0000-0xdffff could not be reserved
Jun 18 10:19:56 plat-vm-host-3 kernel: [  100.569246] NET: Registered protocol family 2
Jun 18 10:19:56 plat-vm-host-3 kernel: [  100.678529] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Jun 18 10:19:56 plat-vm-host-3 kernel: [  100.679420] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Jun 18 10:19:56 plat-vm-host-3 kernel: [  100.685180] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Jun 18 10:19:56 plat-vm-host-3 kernel: [  100.688050] TCP: Hash tables configured (established 131072 bind 65536)
Jun 18 10:19:56 plat-vm-host-3 kernel: [  100.688054] TCP reno registered
Jun 18 10:19:56 plat-vm-host-3 kernel: [  100.708607] checking if image is initramfs... it is
Jun 18 10:19:56 plat-vm-host-3 kernel: [  101.422938] Freeing initrd memory: 7285k freed
Jun 18 10:19:56 plat-vm-host-3 kernel: [  101.424215] audit: initializing netlink socket (disabled)
Jun 18 10:19:56 plat-vm-host-3 kernel: [  101.424243] audit(1213748353.010:1): initialized
Jun 18 10:19:56 plat-vm-host-3 kernel: [  101.426831] highmem bounce pool size: 64 pages
Jun 18 10:19:56 plat-vm-host-3 kernel: [  101.426840] Total HugeTLB memory allocated, 0
Jun 18 10:19:56 plat-vm-host-3 kernel: [  101.430816] VFS: Disk quotas dquot_6.5.1
Jun 18 10:19:56 plat-vm-host-3 kernel: [  101.430974] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Jun 18 10:19:56 plat-vm-host-3 kernel: [  101.431391] io scheduler noop registered
Jun 18 10:19:56 plat-vm-host-3 kernel: [  101.431394] io scheduler anticipatory registered
Jun 18 10:19:56 plat-vm-host-3 kernel: [  101.431397] io scheduler deadline registered (default)
Jun 18 10:19:56 plat-vm-host-3 kernel: [  101.431411] io scheduler cfq registered
Jun 18 10:19:56 plat-vm-host-3 kernel: [  101.448248] isapnp: Scanning for PnP cards...
Jun 18 10:19:56 plat-vm-host-3 kernel: [  101.804940] isapnp: No Plug & Play device found
Jun 18 10:19:56 plat-vm-host-3 kernel: [  101.849348] Real Time Clock Driver v1.12ac
Jun 18 10:19:56 plat-vm-host-3 kernel: [  101.849612] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Jun 18 10:19:56 plat-vm-host-3 kernel: [  101.849800] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Jun 18 10:19:56 plat-vm-host-3 kernel: [  101.850797] 00:04: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Jun 18 10:19:56 plat-vm-host-3 kernel: [  101.852442] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Jun 18 10:19:56 plat-vm-host-3 kernel: [  101.852573] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Jun 18 10:19:56 plat-vm-host-3 kernel: [  101.852750] PNP: PS/2 Controller [PNP0303:KBD,PNP0f0e:PS2M] at 0x60,0x64 irq 1,12
Jun 18 10:19:56 plat-vm-host-3 kernel: [  101.854362] serio: i8042 KBD port at 0x60,0x64 irq 1
Jun 18 10:19:56 plat-vm-host-3 kernel: [  101.854373] serio: i8042 AUX port at 0x60,0x64 irq 12
Jun 18 10:19:56 plat-vm-host-3 kernel: [  101.916749] mice: PS/2 mouse device common for all mice
Jun 18 10:19:56 plat-vm-host-3 kernel: [  101.916963] EISA: Probing bus 0 at eisa.0
Jun 18 10:19:56 plat-vm-host-3 kernel: [  101.916968] EISA: Cannot allocate resource for mainboard
Jun 18 10:19:56 plat-vm-host-3 kernel: [  101.916972] Cannot allocate resource for EISA slot 1
Jun 18 10:19:56 plat-vm-host-3 kernel: [  101.916974] Cannot allocate resource for EISA slot 2
Jun 18 10:19:56 plat-vm-host-3 kernel: [  101.917003] EISA: Detected 0 cards.
Jun 18 10:19:56 plat-vm-host-3 kernel: [  101.917009] cpuidle: using governor ladder
Jun 18 10:19:56 plat-vm-host-3 kernel: [  101.917011] cpuidle: using governor menu
Jun 18 10:19:56 plat-vm-host-3 kernel: [  101.917252] NET: Registered protocol family 1
Jun 18 10:19:56 plat-vm-host-3 kernel: [  101.917315] Using IPI No-Shortcut mode
Jun 18 10:19:56 plat-vm-host-3 kernel: [  101.917364] registered taskstats version 1
Jun 18 10:19:56 plat-vm-host-3 kernel: [  101.917690]   Magic number: 12:618:304
Jun 18 10:19:56 plat-vm-host-3 kernel: [  101.917909]   hash matches device tty33
Jun 18 10:19:56 plat-vm-host-3 kernel: [  101.917950] BIOS EDD facility v0.16 2004-Jun-25, 6 devices found
Jun 18 10:19:56 plat-vm-host-3 kernel: [  101.919044] Freeing unused kernel memory: 384k freed
Jun 18 10:19:56 plat-vm-host-3 kernel: [  101.958442] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
Jun 18 10:19:56 plat-vm-host-3 kernel: [  103.265603] fuse init (API version 7.9)
Jun 18 10:19:56 plat-vm-host-3 kernel: [  103.293424] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
Jun 18 10:19:56 plat-vm-host-3 kernel: [  103.293458] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
Jun 18 10:19:56 plat-vm-host-3 kernel: [  103.293490] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
Jun 18 10:19:56 plat-vm-host-3 kernel: [  103.293519] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
Jun 18 10:19:56 plat-vm-host-3 kernel: [  103.293550] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
Jun 18 10:19:56 plat-vm-host-3 kernel: [  103.293604] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
Jun 18 10:19:56 plat-vm-host-3 kernel: [  103.293633] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
Jun 18 10:19:56 plat-vm-host-3 kernel: [  103.293661] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
Jun 18 10:19:56 plat-vm-host-3 kernel: [  103.295654] ACPI: Thermal Zone [THM1] (16 C)
Jun 18 10:19:56 plat-vm-host-3 kernel: [  103.685427] SCSI subsystem initialized
Jun 18 10:19:56 plat-vm-host-3 kernel: [  103.703770] HP CISS Driver (v 3.6.14)
Jun 18 10:19:56 plat-vm-host-3 kernel: [  103.704351] ACPI: PCI Interrupt 0000:00:0e.0[A] -> GSI 40 (level, low) -> IRQ 16
Jun 18 10:19:56 plat-vm-host-3 kernel: [  103.709287] Intel(R) PRO/1000 Network Driver - version 7.3.20-k2-NAPI
Jun 18 10:19:56 plat-vm-host-3 kernel: [  103.709292] Copyright (c) 1999-2006 Intel Corporation.
Jun 18 10:19:56 plat-vm-host-3 kernel: [  103.729307] usbcore: registered new interface driver usbfs
Jun 18 10:19:56 plat-vm-host-3 kernel: [  103.729353] usbcore: registered new interface driver hub
Jun 18 10:19:56 plat-vm-host-3 kernel: [  103.729437] usbcore: registered new device driver usb
Jun 18 10:19:56 plat-vm-host-3 kernel: [  103.757781] Floppy drive(s): fd0 is 1.44M
Jun 18 10:19:56 plat-vm-host-3 kernel: [  103.776165] FDC 0 is a National Semiconductor PC87306
Jun 18 10:19:56 plat-vm-host-3 kernel: [  103.806114] cciss0: <0xb178> at PCI 0000:00:0e.0 IRQ 16 using DAC
Jun 18 10:19:56 plat-vm-host-3 kernel: [  103.835984]       blocks= 1171856412 block_size= 512
Jun 18 10:19:56 plat-vm-host-3 kernel: [  103.845959]       heads=255, sectors=63, cylinders=72945
Jun 18 10:19:56 plat-vm-host-3 kernel: [  103.845961] 
Jun 18 10:19:56 plat-vm-host-3 kernel: [  103.846374]       blocks= 1171856412 block_size= 512
Jun 18 10:19:56 plat-vm-host-3 kernel: [  103.846486]       heads=255, sectors=63, cylinders=72945
Jun 18 10:19:56 plat-vm-host-3 kernel: [  103.846488] 
Jun 18 10:19:56 plat-vm-host-3 kernel: [  103.846491]  cciss/c0d0: p1 p2 p3 p4
Jun 18 10:19:56 plat-vm-host-3 kernel: [  103.853736] ACPI: PCI Interrupt Link [IUSB] enabled at IRQ 10
Jun 18 10:19:56 plat-vm-host-3 kernel: [  103.853748] ACPI: PCI Interrupt 0000:00:0f.2[A] -> Link [IUSB] -> GSI 10 (level, low) -> IRQ 10
Jun 18 10:19:56 plat-vm-host-3 kernel: [  103.853778] ohci_hcd 0000:00:0f.2: OHCI Host Controller
Jun 18 10:19:56 plat-vm-host-3 kernel: [  103.854494] ohci_hcd 0000:00:0f.2: new USB bus registered, assigned bus number 1
Jun 18 10:19:56 plat-vm-host-3 kernel: [  103.854521] ohci_hcd 0000:00:0f.2: irq 10, io mem 0xf5f70000
Jun 18 10:19:56 plat-vm-host-3 kernel: [  103.918163] usb usb1: configuration #1 chosen from 1 choice
Jun 18 10:19:56 plat-vm-host-3 kernel: [  103.918212] hub 1-0:1.0: USB hub found
Jun 18 10:19:56 plat-vm-host-3 kernel: [  103.918228] hub 1-0:1.0: 4 ports detected
Jun 18 10:19:56 plat-vm-host-3 kernel: [  104.026324] scsi0 : pata_serverworks
Jun 18 10:19:56 plat-vm-host-3 kernel: [  104.026490] scsi1 : pata_serverworks
Jun 18 10:19:56 plat-vm-host-3 kernel: [  104.026545] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x2820 irq 14
Jun 18 10:19:56 plat-vm-host-3 kernel: [  104.026550] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x2828 irq 15
Jun 18 10:19:56 plat-vm-host-3 kernel: [  104.366102] ata1.00: ATAPI: DV-28E-C, B.4F, max UDMA/25
Jun 18 10:19:56 plat-vm-host-3 kernel: [  104.561994] ata1.00: configured for UDMA/25
Jun 18 10:19:56 plat-vm-host-3 kernel: [  104.726554] scsi 0:0:0:0: CD-ROM            TEAC     DV-28E-C         B.4F PQ: 0 ANSI: 5
Jun 18 10:19:56 plat-vm-host-3 kernel: [  104.726962] ACPI: PCI Interrupt 0000:13:01.0[A] -> GSI 31 (level, low) -> IRQ 17
Jun 18 10:19:56 plat-vm-host-3 kernel: [  104.938898] Attempting manual resume
Jun 18 10:19:56 plat-vm-host-3 kernel: [  105.015475] e1000: 0000:13:01.0: e1000_probe: (PCI-X:100MHz:64-bit) 00:04:23:ce:62:7e
Jun 18 10:19:56 plat-vm-host-3 kernel: [  105.032445] kjournald starting.  Commit interval 5 seconds
Jun 18 10:19:56 plat-vm-host-3 kernel: [  105.032459] EXT3-fs: mounted filesystem with ordered data mode.
Jun 18 10:19:56 plat-vm-host-3 kernel: [  105.064054] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
Jun 18 10:19:56 plat-vm-host-3 kernel: [  105.064121] ACPI: PCI Interrupt 0000:13:01.1[B] -> GSI 30 (level, low) -> IRQ 18
Jun 18 10:19:56 plat-vm-host-3 kernel: [  105.353643] e1000: 0000:13:01.1: e1000_probe: (PCI-X:100MHz:64-bit) 00:04:23:ce:62:7f
Jun 18 10:19:56 plat-vm-host-3 kernel: [  105.403312] e1000: eth1: e1000_probe: Intel(R) PRO/1000 Network Connection
Jun 18 10:19:56 plat-vm-host-3 kernel: [  108.140188] Linux agpgart interface v0.102
Jun 18 10:19:56 plat-vm-host-3 kernel: [  108.203214] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jun 18 10:19:56 plat-vm-host-3 kernel: [  108.257747] piix4_smbus 0000:00:0f.0: Found 0000:00:0f.0 device
Jun 18 10:19:56 plat-vm-host-3 kernel: [  108.290269] cpqphp: Compaq Hot Plug PCI Controller Driver version: 0.9.8
Jun 18 10:19:56 plat-vm-host-3 kernel: [  108.290424] ACPI: PCI Interrupt 0000:00:1e.0[A] -> GSI 35 (level, low) -> IRQ 19
Jun 18 10:19:56 plat-vm-host-3 kernel: [  108.290442] cpqphp: Hot Plug Subsystem Device ID: a2f8
Jun 18 10:19:56 plat-vm-host-3 kernel: [  108.290448] cpqphp: Initializing the PCI hot plug controller residing on PCI bus 0
Jun 18 10:19:56 plat-vm-host-3 kernel: [  108.290463] PCI: Using BIOS Interrupt Routing Table
Jun 18 10:19:56 plat-vm-host-3 kernel: [  108.290632] PCI: Using BIOS Interrupt Routing Table
Jun 18 10:19:56 plat-vm-host-3 kernel: [  108.619253] input: Power Button (FF) as /devices/virtual/input/input2
Jun 18 10:19:56 plat-vm-host-3 kernel: [  108.697635] ACPI: Power Button (FF) [PWRF]
Jun 18 10:19:56 plat-vm-host-3 kernel: [  108.844568] e1000: eth0: e1000_watchdog: NIC Link is Up 1000 Mbps Full Duplex, Flow Control: RX
Jun 18 10:19:56 plat-vm-host-3 kernel: [  108.879536] input: PC Speaker as /devices/platform/pcspkr/input/input3
Jun 18 10:19:56 plat-vm-host-3 kernel: [  109.146530] input: PS/2 Logitech Mouse as /devices/platform/i8042/serio1/input/input4
Jun 18 10:19:56 plat-vm-host-3 kernel: [  109.195249] NET: Registered protocol family 10
Jun 18 10:19:56 plat-vm-host-3 kernel: [  109.195987] lo: Disabled Privacy Extensions
Jun 18 10:19:56 plat-vm-host-3 kernel: [  109.315400] ACPI: PCI Interrupt 0000:03:1e.0[A] -> GSI 35 (level, low) -> IRQ 19
Jun 18 10:19:56 plat-vm-host-3 kernel: [  109.315425] cpqphp: Hot Plug Subsystem Device ID: a2fe
Jun 18 10:19:56 plat-vm-host-3 kernel: [  109.315437] cpqphp: Initializing the PCI hot plug controller residing on PCI bus 3
Jun 18 10:19:56 plat-vm-host-3 kernel: [  109.315450] scb2_flash: warning - can't reserve rom window, continuing
Jun 18 10:19:56 plat-vm-host-3 kernel: [  109.315496] PCI: Using BIOS Interrupt Routing Table
Jun 18 10:19:56 plat-vm-host-3 kernel: [  110.331729] ACPI: PCI Interrupt 0000:07:1e.0[A] -> GSI 35 (level, low) -> IRQ 19
Jun 18 10:19:56 plat-vm-host-3 kernel: [  110.331748] cpqphp: Hot Plug Subsystem Device ID: a2fe
Jun 18 10:19:56 plat-vm-host-3 kernel: [  110.331755] cpqphp: Initializing the PCI hot plug controller residing on PCI bus 7
Jun 18 10:19:56 plat-vm-host-3 kernel: [  110.331792] PCI: Using BIOS Interrupt Routing Table
Jun 18 10:19:56 plat-vm-host-3 kernel: [  111.349917] ACPI: PCI Interrupt 0000:0b:1e.0[A] -> GSI 35 (level, low) -> IRQ 19
Jun 18 10:19:56 plat-vm-host-3 kernel: [  111.349927] cpqphp: Hot Plug Subsystem Device ID: a2fe
Jun 18 10:19:56 plat-vm-host-3 kernel: [  111.349932] cpqphp: Initializing the PCI hot plug controller residing on PCI bus 11
Jun 18 10:19:56 plat-vm-host-3 kernel: [  111.349946] PCI: Using BIOS Interrupt Routing Table
Jun 18 10:19:56 plat-vm-host-3 kernel: [  112.368155] ACPI: PCI Interrupt 0000:0f:1e.0[A] -> GSI 35 (level, low) -> IRQ 19
Jun 18 10:19:56 plat-vm-host-3 kernel: [  112.368166] cpqphp: Hot Plug Subsystem Device ID: a2fe
Jun 18 10:19:56 plat-vm-host-3 kernel: [  112.368170] cpqphp: Initializing the PCI hot plug controller residing on PCI bus 15
Jun 18 10:19:56 plat-vm-host-3 kernel: [  112.368182] PCI: Using BIOS Interrupt Routing Table
Jun 18 10:19:56 plat-vm-host-3 kernel: [  113.376416] ACPI: PCI Interrupt 0000:13:1e.0[A] -> GSI 35 (level, low) -> IRQ 19
Jun 18 10:19:56 plat-vm-host-3 kernel: [  113.376426] cpqphp: Hot Plug Subsystem Device ID: a2fe
Jun 18 10:19:56 plat-vm-host-3 kernel: [  113.376431] cpqphp: Initializing the PCI hot plug controller residing on PCI bus 19
Jun 18 10:19:56 plat-vm-host-3 kernel: [  113.376442] PCI: Using BIOS Interrupt Routing Table
Jun 18 10:19:56 plat-vm-host-3 kernel: [  114.421456] Driver 'sr' needs updating - please use bus_type methods
Jun 18 10:19:56 plat-vm-host-3 kernel: [  114.437982] sr0: scsi3-mmc drive: 24x/24x cd/rw xa/form2 cdda tray
Jun 18 10:19:56 plat-vm-host-3 kernel: [  114.437986] Uniform CD-ROM driver Revision: 3.20
Jun 18 10:19:56 plat-vm-host-3 kernel: [  114.454702] sr 0:0:0:0: Attached scsi generic sg0 type 5
Jun 18 10:19:56 plat-vm-host-3 kernel: [  115.591206] loop: module loaded
Jun 18 10:19:56 plat-vm-host-3 kernel: [  115.635987] lp: driver loaded but no devices found
Jun 18 10:19:56 plat-vm-host-3 kernel: [  115.845517] Adding 10241428k swap on /dev/cciss/c0d0p2.  Priority:-1 extents:1 across:10241428k
Jun 18 10:19:56 plat-vm-host-3 kernel: [  116.477715] EXT3 FS on cciss/c0d0p3, internal journal
Jun 18 10:19:56 plat-vm-host-3 kernel: [  117.218654] kjournald starting.  Commit interval 5 seconds
Jun 18 10:19:56 plat-vm-host-3 kernel: [  117.223923] EXT3 FS on cciss/c0d0p1, internal journal
Jun 18 10:19:56 plat-vm-host-3 kernel: [  117.223934] EXT3-fs: mounted filesystem with ordered data mode.
Jun 18 10:19:56 plat-vm-host-3 kernel: [  117.235037] kjournald starting.  Commit interval 5 seconds
Jun 18 10:19:56 plat-vm-host-3 kernel: [  117.240959] EXT3 FS on cciss/c0d0p4, internal journal
Jun 18 10:19:56 plat-vm-host-3 kernel: [  117.240965] EXT3-fs: mounted filesystem with ordered data mode.
Jun 18 10:19:56 plat-vm-host-3 kernel: [  117.704294] ip_tables: (C) 2000-2006 Netfilter Core Team
Jun 18 10:19:56 plat-vm-host-3 kernel: [  118.187595] No dock devices found.
Jun 18 10:19:57 plat-vm-host-3 kernel: [  119.472089] apm: BIOS not found.
Jun 18 10:19:57 plat-vm-host-3 kernel: [  119.626718] ppdev: user-space parallel port driver
Jun 18 10:19:57 plat-vm-host-3 kernel: [  119.702984] audit(1213748397.443:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5438 profile="/usr/sbin/cupsd" namespace="default"
Jun 18 10:19:57 plat-vm-host-3 dhcdbd: Started up.
Jun 18 10:19:58 plat-vm-host-3 kernel: [  120.497422] ADDRCONF(NETDEV_UP): eth1: link is not ready
Jun 18 10:19:58 plat-vm-host-3 kernel: [  120.504401] e1000: eth1: e1000_watchdog: NIC Link is Up 1000 Mbps Full Duplex, Flow Control: RX
Jun 18 10:19:58 plat-vm-host-3 kernel: [  120.508622] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
Jun 18 10:19:58 plat-vm-host-3 kernel: [  120.575838] Bluetooth: Core ver 2.11
Jun 18 10:19:58 plat-vm-host-3 kernel: [  120.576285] NET: Registered protocol family 31
Jun 18 10:19:58 plat-vm-host-3 kernel: [  120.576289] Bluetooth: HCI device and connection manager initialized
Jun 18 10:19:58 plat-vm-host-3 kernel: [  120.576299] Bluetooth: HCI socket layer initialized
Jun 18 10:19:58 plat-vm-host-3 kernel: [  120.596890] Bluetooth: L2CAP ver 2.9
Jun 18 10:19:58 plat-vm-host-3 kernel: [  120.596898] Bluetooth: L2CAP socket layer initialized
Jun 18 10:19:58 plat-vm-host-3 kernel: [  120.646318] Bluetooth: RFCOMM socket layer initialized
Jun 18 10:19:58 plat-vm-host-3 kernel: [  120.646348] Bluetooth: RFCOMM TTY layer initialized
Jun 18 10:19:58 plat-vm-host-3 kernel: [  120.646352] Bluetooth: RFCOMM ver 1.8
Jun 18 10:19:59 plat-vm-host-3 kernel: [  122.041896] mtrr: type mismatch for f6000000,800000 old: write-back new: write-combining
Jun 18 10:19:59 plat-vm-host-3 kernel: [  122.056438] mtrr: type mismatch for f6000000,800000 old: write-back new: write-combining
Jun 18 10:20:00 plat-vm-host-3 dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth1 for sub-path eth1.dbus.get.reason
Jun 18 10:20:01 plat-vm-host-3 kernel: [  123.338485] vmmon: module license 'unspecified' taints kernel.
Jun 18 10:20:01 plat-vm-host-3 kernel: [  123.390924] bridge-eth0: already up
Jun 18 10:20:02 plat-vm-host-3 kernel: [  124.664747] NET: Registered protocol family 17
Jun 18 10:20:04 plat-vm-host-3 kernel: [  126.268932] device eth0 entered promiscuous mode
Jun 18 10:20:04 plat-vm-host-3 kernel: [  126.268945] audit(1213748404.025:3): dev=eth0 prom=256 old_prom=0 auid=4294967295
Jun 18 10:20:04 plat-vm-host-3 kernel: [  126.269237] bridge-eth0: enabled promiscuous mode
Jun 18 10:20:16 plat-vm-host-3 kernel: [  138.555946] device eth0 left promiscuous mode
Jun 18 10:20:16 plat-vm-host-3 kernel: [  138.555983] audit(1213748416.327:4): dev=eth0 prom=0 old_prom=256 auid=4294967295
Jun 18 10:20:16 plat-vm-host-3 kernel: [  138.556251] bridge-eth0: disabled promiscuous mode
Jun 18 10:20:16 plat-vm-host-3 kernel: [  138.556434] device eth0 entered promiscuous mode
Jun 18 10:20:16 plat-vm-host-3 kernel: [  138.556448] audit(1213748416.327:5): dev=eth0 prom=256 old_prom=0 auid=4294967295
Jun 18 10:20:16 plat-vm-host-3 kernel: [  138.556711] bridge-eth0: enabled promiscuous mode
.................................................................

CPU INFO:

$ cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 15
model           : 2
model name      : Intel(R) Xeon(TM) MP CPU 3.00GHz
stepping        : 6
cpu MHz         : 2997.795
cache size      : 4096 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 1
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe pebs bts sync_rdtsc cid xtpr
bogomips        : 6000.21
clflush size    : 64

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 15
model           : 2
model name      : Intel(R) Xeon(TM) MP CPU 3.00GHz
stepping        : 6
cpu MHz         : 2997.795
cache size      : 4096 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 1
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe pebs bts sync_rdtsc cid xtpr
bogomips        : 5995.55
clflush size    : 64

processor       : 2
vendor_id       : GenuineIntel
cpu family      : 15
model           : 2
model name      : Intel(R) Xeon(TM) MP CPU 3.00GHz
stepping        : 6
cpu MHz         : 2997.795
cache size      : 4096 KB
physical id     : 1
siblings        : 2
core id         : 0
cpu cores       : 1
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe pebs bts sync_rdtsc cid xtpr
bogomips        : 5995.72
clflush size    : 64

processor       : 3
vendor_id       : GenuineIntel
cpu family      : 15
model           : 2
model name      : Intel(R) Xeon(TM) MP CPU 3.00GHz
stepping        : 6
cpu MHz         : 2997.795
cache size      : 4096 KB
physical id     : 1
siblings        : 2
core id         : 0
cpu cores       : 1
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe pebs bts sync_rdtsc cid xtpr
bogomips        : 5995.76
clflush size    : 64

processor       : 4
vendor_id       : GenuineIntel
cpu family      : 15
model           : 2
model name      : Intel(R) Xeon(TM) MP CPU 3.00GHz
stepping        : 6
cpu MHz         : 2997.795
cache size      : 4096 KB
physical id     : 2
siblings        : 2
core id         : 0
cpu cores       : 1
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe pebs bts sync_rdtsc cid xtpr
bogomips        : 5995.79
clflush size    : 64

processor       : 5
vendor_id       : GenuineIntel
cpu family      : 15
model           : 2
model name      : Intel(R) Xeon(TM) MP CPU 3.00GHz
stepping        : 6
cpu MHz         : 2997.795
cache size      : 4096 KB
physical id     : 2
siblings        : 2
core id         : 0
cpu cores       : 1
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe pebs bts sync_rdtsc cid xtpr
bogomips        : 5995.74
clflush size    : 64

processor       : 6
vendor_id       : GenuineIntel
cpu family      : 15
model           : 2
model name      : Intel(R) Xeon(TM) MP CPU 3.00GHz
stepping        : 6
cpu MHz         : 2997.795
cache size      : 4096 KB
physical id     : 3
siblings        : 2
core id         : 0
cpu cores       : 1
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe pebs bts sync_rdtsc cid xtpr
bogomips        : 5995.76
clflush size    : 64

processor       : 7
vendor_id       : GenuineIntel
cpu family      : 15
model           : 2
model name      : Intel(R) Xeon(TM) MP CPU 3.00GHz
stepping        : 6
cpu MHz         : 2997.795
cache size      : 4096 KB
physical id     : 3
siblings        : 2
core id         : 0
cpu cores       : 1
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe pebs bts sync_rdtsc cid xtpr
bogomips        : 5995.83
clflush size    : 64

So is it possible to get all 16 working with this install, or will i have to install the 64bit version ? (if the hardware is 64bit).

Regards,
Shannon

---

### Post by oakey_99 on 2008-06-18
Previously used Windows server 2003 32bit as the 64bit advised that hardware does not support 64bit ... hence why i installed the 32bit version of Ubuntu.

---

### Post by gtdaqua on 2008-06-18
```

$ cat /proc/cpuinfo
processor : 0
vendor_id : GenuineIntel
cpu family : 15
model : 2
model name : Intel(R) Xeon(TM) MP CPU 3.00GHz
stepping : 6
cpu MHz : 2997.795
cache size : 4096 KB
physical id : 0
siblings : 2
core id : 0
cpu cores : 1
fdiv_bug : no
hlt_bug : no
f00f_bug : no
coma_bug : no
fpu : yes
fpu_exception : yes
cpuid level : 2
wp : yes
**flags : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe pebs bts sync_rdtsc cid xtpr**
bogomips : 6000.21
clflush size : 64

```

The "flags" section must have **"lm"** listed for 64-bit capabilities. So yours is not a 64-bit processor. <strike>Also, Xeon MPs are 32-bit only</strike>. I am just telling you this, that, if you want to check 64-bit capabilities, then look for the "lm" module in the "flags" section.

---

### Post by oakey_99 on 2008-07-03
Anyone ?

---

### Post by promodus on 2008-07-03
> 
Also, Xeon MPs are 32-bit only.

Not entirely:
[http://www.intel.com/design/xeon/datashts/306751.htm](http://www.intel.com/design/xeon/datashts/306751.htm)

---

### Post by gtdaqua on 2008-07-03
> s Ubuntu 8.04 32bit install limited to 8 processors ???

Yes. 64 bit is limited to 64 CPUs. Type this to see your kernel's CPU limit:

```

cat /boot/config-2.6.24-19-generic | grep NR_CPUS

```

Supposedly there is a way to change this.

---

### Post by gtdaqua on 2008-07-03
> **promodus said:**
> Not entirely:
[http://www.intel.com/design/xeon/datashts/306751.htm](http://www.intel.com/design/xeon/datashts/306751.htm)

I stand corrected! Sorry for the wrong info. There are 64-bit Xeon MPs.

---

### Post by Robstarusa on 2008-07-03
> **gtdaqua said:**
> Yes. 64 bit is limited to 64 CPUs. Type this to see your kernel's CPU limit:

```

cat /boot/config-2.6.24-19-generic | grep NR_CPUS

```

Supposedly there is a way to change this.

Can you simply edit this in the .config & recompile or is something more needed?

---

### Post by oakey_99 on 2008-07-10
Ok i have run the command 

cat /boot/config-2.6.24-17-server | grep NR_CPUS

and it does return

CONFIG_NR_CPUS=8

So, i guess the question is, can this be changed by simply editing the value of in the .config file and re-compiling the kernel? Or is this impossible? Would love to know without wasting a weekend to install again on the server :-)

---

