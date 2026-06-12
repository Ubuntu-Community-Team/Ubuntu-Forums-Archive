---
title: "VirtualBox not working after fresh install of Ubuntu 16.04LTS"
date: 2016-05-27
forum: Virtualisation
---

### Post by michael_hansen2 on 2016-05-27
Since doing a fresh install of Ubuntu 16.04LTS I have been unable to get VirtualBox to work. I've looked everywhere online and none of the solutions provided has worked for me. Its a huge problem as I use it for work so I really hope that someone can help me.

When I attempt to start a VirtualBox I get this message: "Kernel driver not installed". I'm then told to run '/sbin/rcvboxdrv setup' using sudo

When I do that I get this message:

```
Stopping VirtualBox kernel modules ...done.
Uninstalling old VirtualBox DKMS kernel modules ...done.
Trying to register the VirtualBox kernel modules using DKMS ...done.
Starting VirtualBox kernel modules ...failed!
  (modprobe vboxdrv failed. Please use 'dmesg' to find out why)
```


I then run dmesg which gives me all this info:


```
[    0.000000] microcode: CPU0 microcode updated early to revision 0x1c, date = 2015-02-26
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 4.4.0-21-generic (buildd@lgw01-21) (gcc version 5.3.1 20160413 (Ubuntu 5.3.1-14ubuntu2) ) #37-Ubuntu SMP Mon Apr 18 18:33:37 UTC 2016 (Ubuntu 4.4.0-21.37-generic 4.4.6)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-4.4.0-21-generic.efi.signed root=UUID=2e35bc21-197b-4cc5-966c-6d8450c4fd2c ro quiet splash vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] x86/fpu: xstate_offset[2]:  576, xstate_sizes[2]:  256
[    0.000000] x86/fpu: Supporting XSAVE feature 0x01: 'x87 floating point registers'
[    0.000000] x86/fpu: Supporting XSAVE feature 0x02: 'SSE registers'
[    0.000000] x86/fpu: Supporting XSAVE feature 0x04: 'AVX registers'
[    0.000000] x86/fpu: Enabled xstate features 0x7, context size is 832 bytes, using 'standard' format.
[    0.000000] x86/fpu: Using 'eager' FPU context switches.
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009efff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009f000-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x000000001fffffff] usable
[    0.000000] BIOS-e820: [mem 0x0000000020000000-0x00000000201fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000020200000-0x0000000040003fff] usable
[    0.000000] BIOS-e820: [mem 0x0000000040004000-0x0000000040004fff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000040005000-0x00000000cc9d1fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000cc9d2000-0x00000000ccfabfff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ccfac000-0x00000000ccfbbfff] ACPI data
[    0.000000] BIOS-e820: [mem 0x00000000ccfbc000-0x00000000cd241fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000cd242000-0x00000000cd812fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000cd813000-0x00000000cd813fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000cd814000-0x00000000cd856fff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000cd857000-0x00000000cdc78fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000cdc79000-0x00000000cdff3fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000cdff4000-0x00000000cdffffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000cf000000-0x00000000df1fffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000f8000000-0x00000000fbffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed00000-0x00000000fed03fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed1c000-0x00000000fed1ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ff000000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000041fdfffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] e820: update [mem 0x8870c018-0x8871c057] usable ==> usable
[    0.000000] e820: update [mem 0x886ff018-0x8870b857] usable ==> usable
[    0.000000] extended physical RAM map:
[    0.000000] reserve setup_data: [mem 0x0000000000000000-0x000000000009efff] usable
[    0.000000] reserve setup_data: [mem 0x000000000009f000-0x000000000009ffff] reserved
[    0.000000] reserve setup_data: [mem 0x0000000000100000-0x000000001fffffff] usable
[    0.000000] reserve setup_data: [mem 0x0000000020000000-0x00000000201fffff] reserved
[    0.000000] reserve setup_data: [mem 0x0000000020200000-0x0000000040003fff] usable
[    0.000000] reserve setup_data: [mem 0x0000000040004000-0x0000000040004fff] reserved
[    0.000000] reserve setup_data: [mem 0x0000000040005000-0x00000000886ff017] usable
[    0.000000] reserve setup_data: [mem 0x00000000886ff018-0x000000008870b857] usable
[    0.000000] reserve setup_data: [mem 0x000000008870b858-0x000000008870c017] usable
[    0.000000] reserve setup_data: [mem 0x000000008870c018-0x000000008871c057] usable
[    0.000000] reserve setup_data: [mem 0x000000008871c058-0x00000000cc9d1fff] usable
[    0.000000] reserve setup_data: [mem 0x00000000cc9d2000-0x00000000ccfabfff] reserved
[    0.000000] reserve setup_data: [mem 0x00000000ccfac000-0x00000000ccfbbfff] ACPI data
[    0.000000] reserve setup_data: [mem 0x00000000ccfbc000-0x00000000cd241fff] ACPI NVS
[    0.000000] reserve setup_data: [mem 0x00000000cd242000-0x00000000cd812fff] reserved
[    0.000000] reserve setup_data: [mem 0x00000000cd813000-0x00000000cd813fff] usable
[    0.000000] reserve setup_data: [mem 0x00000000cd814000-0x00000000cd856fff] ACPI NVS
[    0.000000] reserve setup_data: [mem 0x00000000cd857000-0x00000000cdc78fff] usable
[    0.000000] reserve setup_data: [mem 0x00000000cdc79000-0x00000000cdff3fff] reserved
[    0.000000] reserve setup_data: [mem 0x00000000cdff4000-0x00000000cdffffff] usable
[    0.000000] reserve setup_data: [mem 0x00000000cf000000-0x00000000df1fffff] reserved
[    0.000000] reserve setup_data: [mem 0x00000000f8000000-0x00000000fbffffff] reserved
[    0.000000] reserve setup_data: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
[    0.000000] reserve setup_data: [mem 0x00000000fed00000-0x00000000fed03fff] reserved
[    0.000000] reserve setup_data: [mem 0x00000000fed1c000-0x00000000fed1ffff] reserved
[    0.000000] reserve setup_data: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
[    0.000000] reserve setup_data: [mem 0x00000000ff000000-0x00000000ffffffff] reserved
[    0.000000] reserve setup_data: [mem 0x0000000100000000-0x000000041fdfffff] usable
[    0.000000] efi: EFI v2.31 by American Megatrends
[    0.000000] efi:  ACPI=0xccfaf000  ACPI 2.0=0xccfaf000  SMBIOS=0xf04c0  MPS=0xfd4b0 
[    0.000000] SMBIOS 2.7 present.
[    0.000000] DMI: System manufacturer System Product Name/P8Z77-V LK, BIOS 0908 11/16/2012
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] e820: last_pfn = 0x41fe00 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-DFFFF uncachable
[    0.000000]   E0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask C00000000 write-back
[    0.000000]   1 base 400000000 mask FE0000000 write-back
[    0.000000]   2 base 0E0000000 mask FE0000000 uncachable
[    0.000000]   3 base 0D0000000 mask FF0000000 uncachable
[    0.000000]   4 base 0CF000000 mask FFF000000 uncachable
[    0.000000]   5 base 41FE00000 mask FFFE00000 uncachable
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000]   8 disabled
[    0.000000]   9 disabled
[    0.000000] x86/PAT: Configuration [0-7]: WB  WC  UC- UC  WB  WC  UC- WT  
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 16GB, type WB
[    0.000000] reg 1, base: 16GB, range: 512MB, type WB
[    0.000000] reg 2, base: 3584MB, range: 512MB, type UC
[    0.000000] reg 3, base: 3328MB, range: 256MB, type UC
[    0.000000] reg 4, base: 3312MB, range: 16MB, type UC
[    0.000000] reg 5, base: 16894MB, range: 2MB, type UC
[    0.000000] total RAM covered: 16110M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K     chunk_size: 32M     num_reg: 8      lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 3GB, range: 256MB, type WB
[    0.000000] reg 3, base: 3312MB, range: 16MB, type UC
[    0.000000] reg 4, base: 4GB, range: 4GB, type WB
[    0.000000] reg 5, base: 8GB, range: 8GB, type WB
[    0.000000] reg 6, base: 16GB, range: 512MB, type WB
[    0.000000] reg 7, base: 16894MB, range: 2MB, type UC
[    0.000000] e820: update [mem 0xcf000000-0xffffffff] usable ==> reserved
[    0.000000] e820: last_pfn = 0xce000 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [mem 0x000fd860-0x000fd86f] mapped at [ffff8800000fd860]
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] Base memory trampoline at [ffff880000097000] 97000 size 24576
[    0.000000] BRK [0x031fe000, 0x031fefff] PGTABLE
[    0.000000] BRK [0x031ff000, 0x031fffff] PGTABLE
[    0.000000] BRK [0x03200000, 0x03200fff] PGTABLE
[    0.000000] BRK [0x03201000, 0x03201fff] PGTABLE
[    0.000000] BRK [0x03202000, 0x03202fff] PGTABLE
[    0.000000] BRK [0x03203000, 0x03203fff] PGTABLE
[    0.000000] RAMDISK: [mem 0x3c799000-0x3e9dafff]
[    0.000000] Secure boot enabled
[    0.000000] ACPI: Early table checksum verification disabled
[    0.000000] ACPI: RSDP 0x00000000CCFAF000 000024 (v02 ALASKA)
[    0.000000] ACPI: XSDT 0x00000000CCFAF078 00006C (v01 ALASKA A M I    01072009 AMI  00010013)
[    0.000000] ACPI: FACP 0x00000000CCFB9D40 00010C (v05 ALASKA A M I    01072009 AMI  00010013)
[    0.000000] ACPI: DSDT 0x00000000CCFAF180 00ABBB (v02 ALASKA A M I    00000022 INTL 20051117)
[    0.000000] ACPI: FACS 0x00000000CD240080 000040
[    0.000000] ACPI: APIC 0x00000000CCFB9E50 000072 (v03 ALASKA A M I    01072009 AMI  00010013)
[    0.000000] ACPI: FPDT 0x00000000CCFB9EC8 000044 (v01 ALASKA A M I    01072009 AMI  00010013)
[    0.000000] ACPI: MCFG 0x00000000CCFB9F10 00003C (v01 ALASKA A M I    01072009 MSFT 00000097)
[    0.000000] ACPI: HPET 0x00000000CCFB9F50 000038 (v01 ALASKA A M I    01072009 AMI. 00000005)
[    0.000000] ACPI: SSDT 0x00000000CCFB9F88 00036D (v01 SataRe SataTabl 00001000 INTL 20091112)
[    0.000000] ACPI: SSDT 0x00000000CCFBA2F8 0009AA (v01 PmRef  Cpu0Ist  00003000 INTL 20051117)
[    0.000000] ACPI: SSDT 0x00000000CCFBACA8 000A92 (v01 PmRef  CpuPm    00003000 INTL 20051117)
[    0.000000] ACPI: BGRT 0x00000000CCFBB798 000038 (v00 ALASKA A M I    01072009 AMI  00010013)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x000000041fdfffff]
[    0.000000] NODE_DATA(0) allocated [mem 0x41fde9000-0x41fdedfff]
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x0000000000001000-0x0000000000ffffff]
[    0.000000]   DMA32    [mem 0x0000000001000000-0x00000000ffffffff]
[    0.000000]   Normal   [mem 0x0000000100000000-0x000000041fdfffff]
[    0.000000]   Device   empty
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x0000000000001000-0x000000000009efff]
[    0.000000]   node   0: [mem 0x0000000000100000-0x000000001fffffff]
[    0.000000]   node   0: [mem 0x0000000020200000-0x0000000040003fff]
[    0.000000]   node   0: [mem 0x0000000040005000-0x00000000cc9d1fff]
[    0.000000]   node   0: [mem 0x00000000cd813000-0x00000000cd813fff]
[    0.000000]   node   0: [mem 0x00000000cd857000-0x00000000cdc78fff]
[    0.000000]   node   0: [mem 0x00000000cdff4000-0x00000000cdffffff]
[    0.000000]   node   0: [mem 0x0000000100000000-0x000000041fdfffff]
[    0.000000] Initmem setup node 0 [mem 0x0000000000001000-0x000000041fdfffff]
[    0.000000] On node 0 totalpages: 4114846
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 25 pages reserved
[    0.000000]   DMA zone: 3998 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 13040 pages used for memmap
[    0.000000]   DMA32 zone: 834560 pages, LIFO batch:31
[    0.000000]   Normal zone: 51192 pages used for memmap
[    0.000000]   Normal zone: 3276288 pages, LIFO batch:31
[    0.000000] tboot: non-0 tboot_addr but it is not of type E820_RESERVED
[    0.000000] Reserving Intel graphics stolen memory at 0xcf200000-0xdf1fffff
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0xff] high edge lint[0x1])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a701 base: 0xfed00000
[    0.000000] smpboot: Allowing 4 CPUs, 0 hotplug CPUs
[    0.000000] PM: Registered nosave memory: [mem 0x00000000-0x00000fff]
[    0.000000] PM: Registered nosave memory: [mem 0x0009f000-0x0009ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000fffff]
[    0.000000] PM: Registered nosave memory: [mem 0x20000000-0x201fffff]
[    0.000000] PM: Registered nosave memory: [mem 0x40004000-0x40004fff]
[    0.000000] PM: Registered nosave memory: [mem 0x886ff000-0x886fffff]
[    0.000000] PM: Registered nosave memory: [mem 0x8870b000-0x8870bfff]
[    0.000000] PM: Registered nosave memory: [mem 0x8870c000-0x8870cfff]
[    0.000000] PM: Registered nosave memory: [mem 0x8871c000-0x8871cfff]
[    0.000000] PM: Registered nosave memory: [mem 0xcc9d2000-0xccfabfff]
[    0.000000] PM: Registered nosave memory: [mem 0xccfac000-0xccfbbfff]
[    0.000000] PM: Registered nosave memory: [mem 0xccfbc000-0xcd241fff]
[    0.000000] PM: Registered nosave memory: [mem 0xcd242000-0xcd812fff]
[    0.000000] PM: Registered nosave memory: [mem 0xcd814000-0xcd856fff]
[    0.000000] PM: Registered nosave memory: [mem 0xcdc79000-0xcdff3fff]
[    0.000000] PM: Registered nosave memory: [mem 0xce000000-0xceffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xcf000000-0xdf1fffff]
[    0.000000] PM: Registered nosave memory: [mem 0xdf200000-0xf7ffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xf8000000-0xfbffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfc000000-0xfebfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xfec00fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec01000-0xfecfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed00000-0xfed03fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed04000-0xfed1bfff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed1c000-0xfed1ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed20000-0xfedfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfee00000-0xfee00fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfee01000-0xfeffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xff000000-0xffffffff]
[    0.000000] e820: [mem 0xdf200000-0xf7ffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] clocksource: refined-jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645519600211568 ns
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 33 pages/cpu @ffff88041fa00000 s98008 r8192 d28968 u524288
[    0.000000] pcpu-alloc: s98008 r8192 d28968 u524288 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 4050525
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.4.0-21-generic.efi.signed root=UUID=2e35bc21-197b-4cc5-966c-6d8450c4fd2c ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 15887604K/16459384K available (8356K kernel code, 1278K rwdata, 3920K rodata, 1476K init, 1292K bss, 571780K reserved, 0K cma-reserved)
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     Build-time adjustment of leaf fanout to 64.
[    0.000000]     RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=4.
[    0.000000] RCU: Adjusting geometry for rcu_fanout_leaf=64, nr_cpu_ids=4
[    0.000000] NR_IRQS:16640 nr_irqs:456 16
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] clocksource: hpet: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 133484882848 ns
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.000000] tsc: Detected 3410.120 MHz processor
[    0.000025] Calibrating delay loop (skipped), value calculated using timer frequency.. 6820.24 BogoMIPS (lpj=13640480)
[    0.000027] pid_max: default: 32768 minimum: 301
[    0.000031] ACPI: Core revision 20150930
[    0.004688] ACPI: 4 ACPI AML tables successfully acquired and loaded
[    0.005395] Security Framework initialized
[    0.005397] Yama: becoming mindful.
[    0.005407] AppArmor: AppArmor initialized
[    0.006062] Dentry cache hash table entries: 2097152 (order: 12, 16777216 bytes)
[    0.008938] Inode-cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.010218] Mount-cache hash table entries: 32768 (order: 6, 262144 bytes)
[    0.010230] Mountpoint-cache hash table entries: 32768 (order: 6, 262144 bytes)
[    0.010413] Initializing cgroup subsys io
[    0.010416] Initializing cgroup subsys memory
[    0.010420] Initializing cgroup subsys devices
[    0.010422] Initializing cgroup subsys freezer
[    0.010424] Initializing cgroup subsys net_cls
[    0.010425] Initializing cgroup subsys perf_event
[    0.010427] Initializing cgroup subsys net_prio
[    0.010428] Initializing cgroup subsys hugetlb
[    0.010430] Initializing cgroup subsys pids
[    0.010446] CPU: Physical Processor ID: 0
[    0.010447] CPU: Processor Core ID: 0
[    0.010451] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
[    0.010451] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
[    0.010711] mce: CPU supports 9 MCE banks
[    0.010721] CPU0: Thermal monitoring enabled (TM1)
[    0.010728] process: using mwait in idle threads
[    0.010730] Last level iTLB entries: 4KB 512, 2MB 8, 4MB 8
[    0.010731] Last level dTLB entries: 4KB 512, 2MB 32, 4MB 32, 1GB 0
[    0.011045] Freeing SMP alternatives memory: 28K (ffffffff820b2000 - ffffffff820b9000)
[    0.080286] ftrace: allocating 31878 entries in 125 pages
[    0.091086] smpboot: Max logical packages: 1
[    0.091088] smpboot: APIC(0) Converting physical 0 to logical package 0
[    0.091466] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.131151] TSC deadline timer enabled
[    0.131153] smpboot: CPU0: Intel(R) Core(TM) i5-3570K CPU @ 3.40GHz (family: 0x6, model: 0x3a, stepping: 0x9)
[    0.131164] Performance Events: PEBS fmt1+, 16-deep LBR, IvyBridge events, full-width counters, Intel PMU driver.
[    0.131179] ... version:                3
[    0.131180] ... bit width:              48
[    0.131180] ... generic registers:      8
[    0.131181] ... value mask:             0000ffffffffffff
[    0.131181] ... max period:             0000ffffffffffff
[    0.131182] ... fixed-purpose events:   3
[    0.131183] ... event mask:             00000007000000ff
[    0.131734] x86: Booting SMP configuration:
[    0.131735] .... node  #0, CPUs:      #1
[    0.132277] microcode: CPU1 microcode updated early to revision 0x1c, date = 2015-02-26
[    0.134650] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.134710]  #2
[    0.135200] microcode: CPU2 microcode updated early to revision 0x1c, date = 2015-02-26
[    0.137595]  #3
[    0.138070] microcode: CPU3 microcode updated early to revision 0x1c, date = 2015-02-26
[    0.140417] x86: Booted up 1 node, 4 CPUs
[    0.140419] smpboot: Total of 4 processors activated (27280.96 BogoMIPS)
[    0.142839] devtmpfs: initialized
[    0.145516] evm: security.selinux
[    0.145517] evm: security.SMACK64
[    0.145518] evm: security.SMACK64EXEC
[    0.145518] evm: security.SMACK64TRANSMUTE
[    0.145519] evm: security.SMACK64MMAP
[    0.145520] evm: security.ima
[    0.145520] evm: security.capability
[    0.145564] PM: Registering ACPI NVS region [mem 0xccfbc000-0xcd241fff] (2646016 bytes)
[    0.145586] PM: Registering ACPI NVS region [mem 0xcd814000-0xcd856fff] (274432 bytes)
[    0.145641] clocksource: jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645041785100000 ns
[    0.145694] pinctrl core: initialized pinctrl subsystem
[    0.145779] RTC time: 13:52:36, date: 05/27/16
[    0.145858] NET: Registered protocol family 16
[    0.156418] cpuidle: using governor ladder
[    0.168420] cpuidle: using governor menu
[    0.168424] PCCT header not found.
[    0.168515] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.168516] ACPI: bus type PCI registered
[    0.168517] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.168565] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf8000000-0xfbffffff] (base 0xf8000000)
[    0.168567] PCI: MMCONFIG at [mem 0xf8000000-0xfbffffff] reserved in E820
[    0.168572] PCI: Using configuration type 1 for base access
[    0.168674] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.168680] core: PMU erratum BJ122, BV98, HSD29 workaround disabled, HT off
[    0.180684] ACPI: Added _OSI(Module Device)
[    0.180686] ACPI: Added _OSI(Processor Device)
[    0.180686] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.180687] ACPI: Added _OSI(Processor Aggregator Device)
[    0.182501] ACPI: Executed 1 blocks of module-level executable AML code
[    0.184179] ACPI: Dynamic OEM Table Load:
[    0.184184] ACPI: SSDT 0xFFFF88040DAF9000 00083B (v01 PmRef  Cpu0Cst  00003001 INTL 20051117)
[    0.184532] ACPI: Dynamic OEM Table Load:
[    0.184535] ACPI: SSDT 0xFFFF88040D5D5400 000303 (v01 PmRef  ApIst    00003000 INTL 20051117)
[    0.184827] ACPI: Dynamic OEM Table Load:
[    0.184829] ACPI: SSDT 0xFFFF88040D5D0E00 000119 (v01 PmRef  ApCst    00003000 INTL 20051117)
[    0.185414] ACPI: Interpreter enabled
[    0.185418] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20150930/hwxface-580)
[    0.185421] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20150930/hwxface-580)
[    0.185431] ACPI: (supports S0 S3 S4 S5)
[    0.185432] ACPI: Using IOAPIC for interrupt routing
[    0.185449] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.189495] ACPI: Power Resource [FN00] (off)
[    0.189550] ACPI: Power Resource [FN01] (off)
[    0.189603] ACPI: Power Resource [FN02] (off)
[    0.189655] ACPI: Power Resource [FN03] (off)
[    0.189707] ACPI: Power Resource [FN04] (off)
[    0.190099] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-3e])
[    0.190103] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    0.190245] acpi PNP0A08:00: _OSC: platform does not support [PCIeHotplug PME]
[    0.190330] acpi PNP0A08:00: _OSC: OS now controls [AER PCIeCapability]
[    0.190331] acpi PNP0A08:00: FADT indicates ASPM is unsupported, using BIOS configuration
[    0.190621] PCI host bridge to bus 0000:00
[    0.190623] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7 window]
[    0.190624] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff window]
[    0.190626] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff window]
[    0.190627] pci_bus 0000:00: root bus resource [mem 0x000d0000-0x000d3fff window]
[    0.190628] pci_bus 0000:00: root bus resource [mem 0x000d4000-0x000d7fff window]
[    0.190629] pci_bus 0000:00: root bus resource [mem 0x000d8000-0x000dbfff window]
[    0.190630] pci_bus 0000:00: root bus resource [mem 0x000dc000-0x000dffff window]
[    0.190631] pci_bus 0000:00: root bus resource [mem 0xdf200000-0xfeafffff window]
[    0.190633] pci_bus 0000:00: root bus resource [bus 00-3e]
[    0.190638] pci 0000:00:00.0: [8086:0150] type 00 class 0x060000
[    0.190709] pci 0000:00:01.0: [8086:0151] type 01 class 0x060400
[    0.190733] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.190767] pci 0000:00:01.0: System wakeup disabled by ACPI
[    0.190796] pci 0000:00:02.0: [8086:0162] type 00 class 0x030000
[    0.190805] pci 0000:00:02.0: reg 0x10: [mem 0xf7800000-0xf7bfffff 64bit]
[    0.190809] pci 0000:00:02.0: reg 0x18: [mem 0xe0000000-0xefffffff 64bit pref]
[    0.190812] pci 0000:00:02.0: reg 0x20: [io  0xf000-0xf03f]
[    0.190902] pci 0000:00:14.0: [8086:1e31] type 00 class 0x0c0330
[    0.190929] pci 0000:00:14.0: reg 0x10: [mem 0xf7d00000-0xf7d0ffff 64bit]
[    0.190984] pci 0000:00:14.0: PME# supported from D3hot D3cold
[    0.191019] pci 0000:00:14.0: System wakeup disabled by ACPI
[    0.191047] pci 0000:00:16.0: [8086:1e3a] type 00 class 0x078000
[    0.191075] pci 0000:00:16.0: reg 0x10: [mem 0xf7d1a000-0xf7d1a00f 64bit]
[    0.191132] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
[    0.191199] pci 0000:00:1a.0: [8086:1e2d] type 00 class 0x0c0320
[    0.191224] pci 0000:00:1a.0: reg 0x10: [mem 0xf7d18000-0xf7d183ff]
[    0.191292] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    0.191338] pci 0000:00:1a.0: System wakeup disabled by ACPI
[    0.191366] pci 0000:00:1b.0: [8086:1e20] type 00 class 0x040300
[    0.191388] pci 0000:00:1b.0: reg 0x10: [mem 0xf7d10000-0xf7d13fff 64bit]
[    0.191437] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.191476] pci 0000:00:1b.0: System wakeup disabled by ACPI
[    0.191502] pci 0000:00:1c.0: [8086:1e10] type 01 class 0x060400
[    0.191572] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.191611] pci 0000:00:1c.0: System wakeup disabled by ACPI
[    0.191640] pci 0000:00:1c.4: [8086:1e18] type 01 class 0x060400
[    0.191710] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.191750] pci 0000:00:1c.4: System wakeup disabled by ACPI
[    0.191776] pci 0000:00:1c.5: [8086:244e] type 01 class 0x060401
[    0.191846] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    0.191885] pci 0000:00:1c.5: System wakeup disabled by ACPI
[    0.191912] pci 0000:00:1c.7: [8086:1e1e] type 01 class 0x060400
[    0.191981] pci 0000:00:1c.7: PME# supported from D0 D3hot D3cold
[    0.192019] pci 0000:00:1c.7: System wakeup disabled by ACPI
[    0.192046] pci 0000:00:1d.0: [8086:1e26] type 00 class 0x0c0320
[    0.192072] pci 0000:00:1d.0: reg 0x10: [mem 0xf7d17000-0xf7d173ff]
[    0.192140] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    0.192185] pci 0000:00:1d.0: System wakeup disabled by ACPI
[    0.192212] pci 0000:00:1f.0: [8086:1e44] type 00 class 0x060100
[    0.192361] pci 0000:00:1f.2: [8086:1e02] type 00 class 0x010601
[    0.192383] pci 0000:00:1f.2: reg 0x10: [io  0xf0b0-0xf0b7]
[    0.192389] pci 0000:00:1f.2: reg 0x14: [io  0xf0a0-0xf0a3]
[    0.192395] pci 0000:00:1f.2: reg 0x18: [io  0xf090-0xf097]
[    0.192402] pci 0000:00:1f.2: reg 0x1c: [io  0xf080-0xf083]
[    0.192408] pci 0000:00:1f.2: reg 0x20: [io  0xf060-0xf07f]
[    0.192415] pci 0000:00:1f.2: reg 0x24: [mem 0xf7d16000-0xf7d167ff]
[    0.192445] pci 0000:00:1f.2: PME# supported from D3hot
[    0.192501] pci 0000:00:1f.3: [8086:1e22] type 00 class 0x0c0500
[    0.192516] pci 0000:00:1f.3: reg 0x10: [mem 0xf7d15000-0xf7d150ff 64bit]
[    0.192534] pci 0000:00:1f.3: reg 0x20: [io  0xf040-0xf05f]
[    0.192622] pci 0000:00:01.0: PCI bridge to [bus 01]
[    0.192664] pci 0000:00:1c.0: PCI bridge to [bus 02]
[    0.192729] pci 0000:03:00.0: [10ec:8168] type 00 class 0x020000
[    0.192775] pci 0000:03:00.0: reg 0x10: [io  0xe000-0xe0ff]
[    0.192807] pci 0000:03:00.0: reg 0x18: [mem 0xf0004000-0xf0004fff 64bit pref]
[    0.192827] pci 0000:03:00.0: reg 0x20: [mem 0xf0000000-0xf0003fff 64bit pref]
[    0.192914] pci 0000:03:00.0: supports D1 D2
[    0.192915] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.192959] pci 0000:03:00.0: System wakeup disabled by ACPI
[    0.200458] pci 0000:00:1c.4: PCI bridge to [bus 03]
[    0.200463] pci 0000:00:1c.4:   bridge window [io  0xe000-0xefff]
[    0.200472] pci 0000:00:1c.4:   bridge window [mem 0xf0000000-0xf00fffff 64bit pref]
[    0.200540] pci 0000:04:00.0: [1b21:1080] type 01 class 0x060401
[    0.200667] pci 0000:04:00.0: System wakeup disabled by ACPI
[    0.200688] pci 0000:00:1c.5: PCI bridge to [bus 04-05] (subtractive decode)
[    0.200698] pci 0000:00:1c.5:   bridge window [io  0x0000-0x0cf7 window] (subtractive decode)
[    0.200699] pci 0000:00:1c.5:   bridge window [io  0x0d00-0xffff window] (subtractive decode)
[    0.200700] pci 0000:00:1c.5:   bridge window [mem 0x000a0000-0x000bffff window] (subtractive decode)
[    0.200701] pci 0000:00:1c.5:   bridge window [mem 0x000d0000-0x000d3fff window] (subtractive decode)
[    0.200702] pci 0000:00:1c.5:   bridge window [mem 0x000d4000-0x000d7fff window] (subtractive decode)
[    0.200703] pci 0000:00:1c.5:   bridge window [mem 0x000d8000-0x000dbfff window] (subtractive decode)
[    0.200704] pci 0000:00:1c.5:   bridge window [mem 0x000dc000-0x000dffff window] (subtractive decode)
[    0.200705] pci 0000:00:1c.5:   bridge window [mem 0xdf200000-0xfeafffff window] (subtractive decode)
[    0.200811] pci 0000:04:00.0: PCI bridge to [bus 05] (subtractive decode)
[    0.200831] pci 0000:04:00.0:   bridge window [io  0x0000-0x0cf7 window] (subtractive decode)
[    0.200833] pci 0000:04:00.0:   bridge window [io  0x0d00-0xffff window] (subtractive decode)
[    0.200834] pci 0000:04:00.0:   bridge window [mem 0x000a0000-0x000bffff window] (subtractive decode)
[    0.200835] pci 0000:04:00.0:   bridge window [mem 0x000d0000-0x000d3fff window] (subtractive decode)
[    0.200836] pci 0000:04:00.0:   bridge window [mem 0x000d4000-0x000d7fff window] (subtractive decode)
[    0.200837] pci 0000:04:00.0:   bridge window [mem 0x000d8000-0x000dbfff window] (subtractive decode)
[    0.200838] pci 0000:04:00.0:   bridge window [mem 0x000dc000-0x000dffff window] (subtractive decode)
[    0.200839] pci 0000:04:00.0:   bridge window [mem 0xdf200000-0xfeafffff window] (subtractive decode)
[    0.200909] pci 0000:06:00.0: [1b21:1042] type 00 class 0x0c0330
[    0.200960] pci 0000:06:00.0: reg 0x10: [mem 0xf7c00000-0xf7c07fff 64bit]
[    0.201097] pci 0000:06:00.0: PME# supported from D3hot D3cold
[    0.201128] pci 0000:06:00.0: System wakeup disabled by ACPI
[    0.208459] pci 0000:00:1c.7: PCI bridge to [bus 06]
[    0.208467] pci 0000:00:1c.7:   bridge window [mem 0xf7c00000-0xf7cfffff]
[    0.208844] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 10 *11 12 14 15)
[    0.208879] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 10 11 12 *14 15)
[    0.208912] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 *6 10 11 12 14 15)
[    0.208945] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 10 11 12 14 *15)
[    0.208977] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    0.209010] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 *10 11 12 14 15)
[    0.209042] ACPI: PCI Interrupt Link [LNKG] (IRQs *3 4 5 6 10 11 12 14 15)
[    0.209075] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 6 10 11 12 14 15)
[    0.209245] ACPI: Enabled 4 GPEs in block 00 to 3F
[    0.209318] vgaarb: setting as boot device: PCI:0000:00:02.0
[    0.209319] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.209321] vgaarb: loaded
[    0.209322] vgaarb: bridge control possible 0000:00:02.0
[    0.209474] SCSI subsystem initialized
[    0.209496] libata version 3.00 loaded.
[    0.209511] ACPI: bus type USB registered
[    0.209522] usbcore: registered new interface driver usbfs
[    0.209527] usbcore: registered new interface driver hub
[    0.209536] usbcore: registered new device driver usb
[    0.209650] PCI: Using ACPI for IRQ routing
[    0.211002] PCI: pci_cache_line_size set to 64 bytes
[    0.211045] e820: reserve RAM buffer [mem 0x0009f000-0x0009ffff]
[    0.211046] e820: reserve RAM buffer [mem 0x40004000-0x43ffffff]
[    0.211047] e820: reserve RAM buffer [mem 0x886ff018-0x8bffffff]
[    0.211048] e820: reserve RAM buffer [mem 0x8870c018-0x8bffffff]
[    0.211048] e820: reserve RAM buffer [mem 0xcc9d2000-0xcfffffff]
[    0.211050] e820: reserve RAM buffer [mem 0xcd814000-0xcfffffff]
[    0.211051] e820: reserve RAM buffer [mem 0xcdc79000-0xcfffffff]
[    0.211052] e820: reserve RAM buffer [mem 0xce000000-0xcfffffff]
[    0.211053] e820: reserve RAM buffer [mem 0x41fe00000-0x41fffffff]
[    0.211129] NetLabel: Initializing
[    0.211130] NetLabel:  domain hash size = 128
[    0.211131] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.211140] NetLabel:  unlabeled traffic allowed by default
[    0.211187] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    0.211190] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    0.213209] clocksource: Switched to clocksource hpet
[    0.217269] AppArmor: AppArmor Filesystem Enabled
[    0.217318] pnp: PnP ACPI init
[    0.217394] system 00:00: [mem 0xfed40000-0xfed44fff] has been reserved
[    0.217397] system 00:00: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.217451] system 00:01: [io  0x0680-0x069f] has been reserved
[    0.217453] system 00:01: [io  0x1000-0x100f] has been reserved
[    0.217454] system 00:01: [io  0xffff] has been reserved
[    0.217455] system 00:01: [io  0xffff] has been reserved
[    0.217456] system 00:01: [io  0x0400-0x0453] could not be reserved
[    0.217457] system 00:01: [io  0x0458-0x047f] has been reserved
[    0.217459] system 00:01: [io  0x0500-0x057f] has been reserved
[    0.217460] system 00:01: [io  0x164e-0x164f] has been reserved
[    0.217462] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.217479] pnp 00:02: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.217512] system 00:03: [io  0x0454-0x0457] has been reserved
[    0.217515] system 00:03: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
[    0.217570] system 00:04: [io  0x0290-0x029f] has been reserved
[    0.217572] system 00:04: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.217603] system 00:05: [io  0x04d0-0x04d1] has been reserved
[    0.217605] system 00:05: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.217744] pnp 00:06: [dma 0 disabled]
[    0.217777] pnp 00:06: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.217916] system 00:07: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.217918] system 00:07: [mem 0xfed10000-0xfed17fff] has been reserved
[    0.217919] system 00:07: [mem 0xfed18000-0xfed18fff] has been reserved
[    0.217920] system 00:07: [mem 0xfed19000-0xfed19fff] has been reserved
[    0.217922] system 00:07: [mem 0xf8000000-0xfbffffff] has been reserved
[    0.217923] system 00:07: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.217924] system 00:07: [mem 0xfed90000-0xfed93fff] has been reserved
[    0.217925] system 00:07: [mem 0xfed45000-0xfed8ffff] has been reserved
[    0.217927] system 00:07: [mem 0xff000000-0xffffffff] has been reserved
[    0.217928] system 00:07: [mem 0xfee00000-0xfeefffff] could not be reserved
[    0.217929] system 00:07: [mem 0xdf200000-0xdf200fff] has been reserved
[    0.217931] system 00:07: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.218027] system 00:08: [mem 0x20000000-0x201fffff] has been reserved
[    0.218028] system 00:08: [mem 0x40004000-0x40004fff] has been reserved
[    0.218030] system 00:08: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.218044] pnp: PnP ACPI: found 9 devices
[    0.223783] clocksource: acpi_pm: mask: 0xffffff max_cycles: 0xffffff, max_idle_ns: 2085701024 ns
[    0.223829] pci 0000:00:01.0: PCI bridge to [bus 01]
[    0.223834] pci 0000:00:1c.0: PCI bridge to [bus 02]
[    0.223844] pci 0000:00:1c.4: PCI bridge to [bus 03]
[    0.223846] pci 0000:00:1c.4:   bridge window [io  0xe000-0xefff]
[    0.223852] pci 0000:00:1c.4:   bridge window [mem 0xf0000000-0xf00fffff 64bit pref]
[    0.223857] pci 0000:04:00.0: PCI bridge to [bus 05]
[    0.223876] pci 0000:00:1c.5: PCI bridge to [bus 04-05]
[    0.223885] pci 0000:00:1c.7: PCI bridge to [bus 06]
[    0.223889] pci 0000:00:1c.7:   bridge window [mem 0xf7c00000-0xf7cfffff]
[    0.223897] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7 window]
[    0.223898] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff window]
[    0.223900] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff window]
[    0.223901] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000d3fff window]
[    0.223902] pci_bus 0000:00: resource 8 [mem 0x000d4000-0x000d7fff window]
[    0.223903] pci_bus 0000:00: resource 9 [mem 0x000d8000-0x000dbfff window]
[    0.223904] pci_bus 0000:00: resource 10 [mem 0x000dc000-0x000dffff window]
[    0.223905] pci_bus 0000:00: resource 11 [mem 0xdf200000-0xfeafffff window]
[    0.223907] pci_bus 0000:03: resource 0 [io  0xe000-0xefff]
[    0.223908] pci_bus 0000:03: resource 2 [mem 0xf0000000-0xf00fffff 64bit pref]
[    0.223909] pci_bus 0000:04: resource 4 [io  0x0000-0x0cf7 window]
[    0.223910] pci_bus 0000:04: resource 5 [io  0x0d00-0xffff window]
[    0.223911] pci_bus 0000:04: resource 6 [mem 0x000a0000-0x000bffff window]
[    0.223912] pci_bus 0000:04: resource 7 [mem 0x000d0000-0x000d3fff window]
[    0.223913] pci_bus 0000:04: resource 8 [mem 0x000d4000-0x000d7fff window]
[    0.223915] pci_bus 0000:04: resource 9 [mem 0x000d8000-0x000dbfff window]
[    0.223916] pci_bus 0000:04: resource 10 [mem 0x000dc000-0x000dffff window]
[    0.223917] pci_bus 0000:04: resource 11 [mem 0xdf200000-0xfeafffff window]
[    0.223918] pci_bus 0000:05: resource 4 [io  0x0000-0x0cf7 window]
[    0.223919] pci_bus 0000:05: resource 5 [io  0x0d00-0xffff window]
[    0.223920] pci_bus 0000:05: resource 6 [mem 0x000a0000-0x000bffff window]
[    0.223921] pci_bus 0000:05: resource 7 [mem 0x000d0000-0x000d3fff window]
[    0.223922] pci_bus 0000:05: resource 8 [mem 0x000d4000-0x000d7fff window]
[    0.223923] pci_bus 0000:05: resource 9 [mem 0x000d8000-0x000dbfff window]
[    0.223925] pci_bus 0000:05: resource 10 [mem 0x000dc000-0x000dffff window]
[    0.223926] pci_bus 0000:05: resource 11 [mem 0xdf200000-0xfeafffff window]
[    0.223927] pci_bus 0000:06: resource 1 [mem 0xf7c00000-0xf7cfffff]
[    0.223950] NET: Registered protocol family 2
[    0.224081] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.224238] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.224347] TCP: Hash tables configured (established 131072 bind 65536)
[    0.224369] UDP hash table entries: 8192 (order: 6, 262144 bytes)
[    0.224407] UDP-Lite hash table entries: 8192 (order: 6, 262144 bytes)
[    0.224461] NET: Registered protocol family 1
[    0.224470] pci 0000:00:02.0: Video device with shadowed ROM
[    0.265238] PCI: CLS mismatch (64 != 32), using 64 bytes
[    0.265319] Trying to unpack rootfs image as initramfs...
[    0.640109] Freeing initrd memory: 35080K (ffff88003c799000 - ffff88003e9db000)
[    0.640151] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.640153] software IO TLB [mem 0xbcaf6000-0xc0af6000] (64MB) mapped at [ffff8800bcaf6000-ffff8800c0af5fff]
[    0.640201] RAPL PMU detected, API unit is 2^-32 Joules, 3 fixed counters 163840 ms ovfl timer
[    0.640202] hw unit of domain pp0-core 2^-16 Joules
[    0.640203] hw unit of domain package 2^-16 Joules
[    0.640204] hw unit of domain pp1-gpu 2^-16 Joules
[    0.640328] Scanning for low memory corruption every 60 seconds
[    0.640549] futex hash table entries: 1024 (order: 4, 65536 bytes)
[    0.640570] audit: initializing netlink subsys (disabled)
[    0.640582] audit: type=2000 audit(1464357156.580:1): initialized
[    0.640895] Initialise system trusted keyring
[    0.640965] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.641925] zbud: loaded
[    0.642060] VFS: Disk quotas dquot_6.6.0
[    0.642080] VFS: Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.642376] fuse init (API version 7.23)
[    0.642458] Key type big_key registered
[    0.642714] Key type asymmetric registered
[    0.642716] Asymmetric key parser 'x509' registered
[    0.642742] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 249)
[    0.642763] io scheduler noop registered
[    0.642765] io scheduler deadline registered (default)
[    0.642784] io scheduler cfq registered
[    0.643235] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.643240] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.643260] efifb: probing for efifb
[    0.643267] efifb: framebuffer at 0xe0000000, mapped to 0xffffc90001c00000, using 3072k, total 3072k
[    0.643268] efifb: mode is 1024x768x32, linelength=4096, pages=1
[    0.643268] efifb: scrolling: redraw
[    0.643269] efifb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    0.643326] Console: switching to colour frame buffer device 128x48
[    0.643337] fb0: EFI VGA frame buffer device
[    0.643343] intel_idle: MWAIT substates: 0x1120
[    0.643344] intel_idle: v0.4.1 model 0x3A
[    0.643345] intel_idle: lapic_timer_reliable_states 0xffffffff
[    0.643477] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0
[    0.643480] ACPI: Power Button [PWRB]
[    0.643503] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input1
[    0.643505] ACPI: Power Button [PWRF]
[    0.643980] thermal LNXTHERM:00: registered as thermal_zone0
[    0.643981] ACPI: Thermal Zone [TZ00] (28 C)
[    0.644120] thermal LNXTHERM:01: registered as thermal_zone1
[    0.644121] ACPI: Thermal Zone [TZ01] (30 C)
[    0.644143] GHES: HEST is not enabled!
[    0.644209] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.664618] 00:06: ttyS0 at I/O 0x3f8 (irq = 4, base_baud = 115200) is a 16550A
[    0.665839] Linux agpgart interface v0.103
[    0.667697] brd: module loaded
[    0.668434] loop: module loaded
[    0.668565] libphy: Fixed MDIO Bus: probed
[    0.668568] tun: Universal TUN/TAP device driver, 1.6
[    0.668568] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.668594] PPP generic driver version 2.4.2
[    0.668632] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.668635] ehci-pci: EHCI PCI platform driver
[    0.668708] ehci-pci 0000:00:1a.0: EHCI Host Controller
[    0.668713] ehci-pci 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    0.668723] ehci-pci 0000:00:1a.0: debug port 2
[    0.672614] ehci-pci 0000:00:1a.0: cache line size of 64 is not supported
[    0.672622] ehci-pci 0000:00:1a.0: irq 23, io mem 0xf7d18000
[    0.681207] ehci-pci 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    0.681241] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    0.681242] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.681243] usb usb1: Product: EHCI Host Controller
[    0.681244] usb usb1: Manufacturer: Linux 4.4.0-21-generic ehci_hcd
[    0.681245] usb usb1: SerialNumber: 0000:00:1a.0
[    0.681416] hub 1-0:1.0: USB hub found
[    0.681422] hub 1-0:1.0: 2 ports detected
[    0.681571] ehci-pci 0000:00:1d.0: EHCI Host Controller
[    0.681575] ehci-pci 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.681584] ehci-pci 0000:00:1d.0: debug port 2
[    0.685491] ehci-pci 0000:00:1d.0: cache line size of 64 is not supported
[    0.685495] ehci-pci 0000:00:1d.0: irq 23, io mem 0xf7d17000
[    0.697227] ehci-pci 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    0.697273] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    0.697274] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.697275] usb usb2: Product: EHCI Host Controller
[    0.697276] usb usb2: Manufacturer: Linux 4.4.0-21-generic ehci_hcd
[    0.697277] usb usb2: SerialNumber: 0000:00:1d.0
[    0.697425] hub 2-0:1.0: USB hub found
[    0.697431] hub 2-0:1.0: 2 ports detected
[    0.697521] ehci-platform: EHCI generic platform driver
[    0.697529] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.697533] ohci-pci: OHCI PCI platform driver
[    0.697541] ohci-platform: OHCI generic platform driver
[    0.697546] uhci_hcd: USB Universal Host Controller Interface driver
[    0.697623] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    0.697627] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 3
[    0.698697] xhci_hcd 0000:00:14.0: hcc params 0x20007181 hci version 0x100 quirks 0x0000b930
[    0.698701] xhci_hcd 0000:00:14.0: cache line size of 64 is not supported
[    0.698802] usb usb3: New USB device found, idVendor=1d6b, idProduct=0002
[    0.698804] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.698805] usb usb3: Product: xHCI Host Controller
[    0.698806] usb usb3: Manufacturer: Linux 4.4.0-21-generic xhci-hcd
[    0.698807] usb usb3: SerialNumber: 0000:00:14.0
[    0.698954] hub 3-0:1.0: USB hub found
[    0.698963] hub 3-0:1.0: 4 ports detected
[    0.699186] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    0.699188] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 4
[    0.699209] usb usb4: New USB device found, idVendor=1d6b, idProduct=0003
[    0.699210] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.699211] usb usb4: Product: xHCI Host Controller
[    0.699212] usb usb4: Manufacturer: Linux 4.4.0-21-generic xhci-hcd
[    0.699213] usb usb4: SerialNumber: 0000:00:14.0
[    0.699359] hub 4-0:1.0: USB hub found
[    0.699368] hub 4-0:1.0: 4 ports detected
[    0.699635] xhci_hcd 0000:06:00.0: xHCI Host Controller
[    0.699639] xhci_hcd 0000:06:00.0: new USB bus registered, assigned bus number 5
[    0.758987] xhci_hcd 0000:06:00.0: hcc params 0x0200f180 hci version 0x96 quirks 0x00080000
[    0.759123] usb usb5: New USB device found, idVendor=1d6b, idProduct=0002
[    0.759125] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.759126] usb usb5: Product: xHCI Host Controller
[    0.759127] usb usb5: Manufacturer: Linux 4.4.0-21-generic xhci-hcd
[    0.759128] usb usb5: SerialNumber: 0000:06:00.0
[    0.759272] hub 5-0:1.0: USB hub found
[    0.759282] hub 5-0:1.0: 2 ports detected
[    0.759342] xhci_hcd 0000:06:00.0: xHCI Host Controller
[    0.759344] xhci_hcd 0000:06:00.0: new USB bus registered, assigned bus number 6
[    0.759375] usb usb6: We don't know the algorithms for LPM for this host, disabling LPM.
[    0.759385] usb usb6: New USB device found, idVendor=1d6b, idProduct=0003
[    0.759387] usb usb6: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.759388] usb usb6: Product: xHCI Host Controller
[    0.759389] usb usb6: Manufacturer: Linux 4.4.0-21-generic xhci-hcd
[    0.759390] usb usb6: SerialNumber: 0000:06:00.0
[    0.759508] hub 6-0:1.0: USB hub found
[    0.759518] hub 6-0:1.0: 2 ports detected
[    0.759606] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    0.761952] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.761955] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.762109] mousedev: PS/2 mouse device common for all mice
[    0.762304] rtc_cmos 00:02: RTC can wake from S4
[    0.762464] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    0.762486] rtc_cmos 00:02: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    0.762492] i2c /dev entries driver
[    0.762524] device-mapper: uevent: version 1.0.3
[    0.762615] device-mapper: ioctl: 4.34.0-ioctl (2015-10-28) initialised: dm-devel@redhat.com
[    0.762624] Intel P-state driver initializing.
[    0.762761] ledtrig-cpu: registered to indicate activity on CPUs
[    0.762766] EFI Variables Facility v0.08 2004-May-17
[    0.766494] efivars: duplicate variable: SbAslBufferPtrVar-01f33c25-764d-43ea-aeea-6b5a41f3f3e8
[    0.766957] NET: Registered protocol family 10
[    0.767238] NET: Registered protocol family 17
[    0.767260] Key type dns_resolver registered
[    0.767529] microcode: CPU0 sig=0x306a9, pf=0x2, revision=0x1c
[    0.767558] microcode: CPU1 sig=0x306a9, pf=0x2, revision=0x1c
[    0.767580] microcode: CPU2 sig=0x306a9, pf=0x2, revision=0x1c
[    0.767592] microcode: CPU3 sig=0x306a9, pf=0x2, revision=0x1c
[    0.767657] microcode: Microcode Update Driver: v2.01 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    0.767873] registered taskstats version 1
[    0.767900] Loading compiled-in X.509 certificates
[    0.769207] Loaded X.509 cert 'Build time autogenerated kernel key: fc7c0e9f152f32eca50ea2d9722926e5127af244'
[    0.769232] zswap: loaded using pool lzo/zbud
[    0.770553] Key type trusted registered
[    0.772875] Key type encrypted registered
[    0.772880] AppArmor: AppArmor sha1 policy hashing enabled
[    0.772882] ima: No TPM chip found, activating TPM-bypass!
[    0.772901] evm: HMAC attrs: 0x1
[    0.773137]   Magic number: 0:740:888
[    0.773240] rtc_cmos 00:02: setting system clock to 2016-05-27 13:52:36 UTC (1464357156)
[    0.773298] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.773299] EDD information not available.
[    0.774164] Freeing unused kernel memory: 1476K (ffffffff81f41000 - ffffffff820b2000)
[    0.774165] Write protecting the kernel read-only data: 14336k
[    0.774507] Freeing unused kernel memory: 1872K (ffff88000282c000 - ffff880002a00000)
[    0.774778] Freeing unused kernel memory: 176K (ffff880002dd4000 - ffff880002e00000)
[    0.780854] random: systemd-udevd urandom read with 2 bits of entropy available
[    0.799533] FUJITSU Extended Socket Network Device Driver - version 1.0 - Copyright (c) 2015 FUJITSU LIMITED
[    0.800635] wmi: Mapper loaded
[    0.808027] [drm] Initialized drm 1.1.0 20060810
[    0.809883] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    0.809890] r8169 0000:03:00.0: can't disable ASPM; OS doesn't have ASPM control
[    0.810584] r8169 0000:03:00.0 eth0: RTL8168f/8111f at 0xffffc900018b6000, 08:60:6e:88:ce:bd, XID 08000800 IRQ 31
[    0.810586] r8169 0000:03:00.0 eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
[    0.811163] ahci 0000:00:1f.2: version 3.0
[    0.825238] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 6 Gbps 0x1f impl SATA mode
[    0.825241] ahci 0000:00:1f.2: flags: 64bit ncq led clo pio slum part ems apst 
[    0.829329] r8169 0000:03:00.0 enp3s0: renamed from eth0
[    0.857830] scsi host0: ahci
[    0.858088] scsi host1: ahci
[    0.858328] scsi host2: ahci
[    0.858508] scsi host3: ahci
[    0.858610] scsi host4: ahci
[    0.858671] scsi host5: ahci
[    0.858698] ata1: SATA max UDMA/133 abar m2048@0xf7d16000 port 0xf7d16100 irq 32
[    0.858699] ata2: SATA max UDMA/133 abar m2048@0xf7d16000 port 0xf7d16180 irq 32
[    0.858701] ata3: SATA max UDMA/133 abar m2048@0xf7d16000 port 0xf7d16200 irq 32
[    0.858703] ata4: SATA max UDMA/133 abar m2048@0xf7d16000 port 0xf7d16280 irq 32
[    0.858705] ata5: SATA max UDMA/133 abar m2048@0xf7d16000 port 0xf7d16300 irq 32
[    0.858705] ata6: DUMMY
[    0.859388] [drm] Memory usable by graphics device = 2048M
[    0.859391] checking generic (e0000000 300000) vs hw (e0000000 10000000)
[    0.859392] fb: switching to inteldrmfb from EFI VGA
[    0.859410] Console: switching to colour dummy device 80x25
[    0.859458] [drm] Replacing VGA console driver
[    0.865296] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[    0.865297] [drm] Driver supports precise vblank timestamp query.
[    0.865888] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[    0.871589] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[    0.871739] acpi device:49: registered as cooling_device9
[    0.871782] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input3
[    0.871843] [drm] Initialized i915 1.6.0 20151010 for 0000:00:02.0 on minor 0
[    0.993221] usb 1-1: new high-speed USB device number 2 using ehci-pci
[    1.009218] usb 3-2: new high-speed USB device number 2 using xhci_hcd
[    1.009234] usb 2-1: new high-speed USB device number 2 using ehci-pci
[    1.102160] fbcon: inteldrmfb (fb0) is primary device
[    1.102206] Console: switching to colour frame buffer device 240x67
[    1.102226] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[    1.125210] usb 5-2: new full-speed USB device number 2 using xhci_hcd
[    1.125623] usb 1-1: New USB device found, idVendor=8087, idProduct=0024
[    1.125624] usb 1-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.125811] hub 1-1:1.0: USB hub found
[    1.125910] hub 1-1:1.0: 6 ports detected
[    1.141598] usb 2-1: New USB device found, idVendor=8087, idProduct=0024
[    1.141600] usb 2-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.141980] hub 2-1:1.0: USB hub found
[    1.142037] hub 2-1:1.0: 8 ports detected
[    1.177224] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.177260] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.177283] ata1: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    1.177300] ata2: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    1.177327] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.177610] ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20150930/psargs-359)
[    1.177613] ACPI Error: Method parse/execution failed [\_SB.PCI0.SAT0.SPT1._GTF] (Node ffff88040f4ce2a8), AE_NOT_FOUND (20150930/psparse-542)
[    1.177757] ata2.00: ATA-9: M4-CT256M4SSD2, 040H, max UDMA/100
[    1.177761] ata2.00: 500118192 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.177915] ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20150930/psargs-359)
[    1.177918] ACPI Error: Method parse/execution failed [\_SB.PCI0.SAT0.SPT3._GTF] (Node ffff88040f4ce398), AE_NOT_FOUND (20150930/psparse-542)
[    1.178125] ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20150930/psargs-359)
[    1.178128] ACPI Error: Method parse/execution failed [\_SB.PCI0.SAT0.SPT1._GTF] (Node ffff88040f4ce2a8), AE_NOT_FOUND (20150930/psparse-542)
[    1.178136] ata4.00: ATA-8: WDC WD1001FALS-00J7B1, 05.00K05, max UDMA/133
[    1.178138] ata4.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.178244] ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20150930/psargs-359)
[    1.178247] ACPI Error: Method parse/execution failed [\_SB.PCI0.SAT0.SPT4._GTF] (Node ffff88040f4ce410), AE_NOT_FOUND (20150930/psparse-542)
[    1.178255] ata2.00: configured for UDMA/100
[    1.178343] ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20150930/psargs-359)
[    1.178345] ACPI Error: Method parse/execution failed [\_SB.PCI0.SAT0.SPT2._GTF] (Node ffff88040f4ce320), AE_NOT_FOUND (20150930/psparse-542)
[    1.178349] ata3.00: ATAPI: PIONEER DVD-RW  DVR-212D, 1.15, max UDMA/66
[    1.178579] ata5.00: ATA-8: ST3500320AS, SD15, max UDMA/133
[    1.178581] ata5.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    1.178826] ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20150930/psargs-359)
[    1.178830] ACPI Error: Method parse/execution failed [\_SB.PCI0.SAT0.SPT3._GTF] (Node ffff88040f4ce398), AE_NOT_FOUND (20150930/psparse-542)
[    1.179028] ata4.00: configured for UDMA/133
[    1.179512] ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20150930/psargs-359)
[    1.179515] ACPI Error: Method parse/execution failed [\_SB.PCI0.SAT0.SPT2._GTF] (Node ffff88040f4ce320), AE_NOT_FOUND (20150930/psparse-542)
[    1.179522] ata3.00: configured for UDMA/66 (SET_XFERMODE skipped)
[    1.179996] ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20150930/psargs-359)
[    1.180001] ACPI Error: Method parse/execution failed [\_SB.PCI0.SAT0.SPT4._GTF] (Node ffff88040f4ce410), AE_NOT_FOUND (20150930/psparse-542)
[    1.180342] ata5.00: configured for UDMA/133
[    1.184209] ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20150930/psargs-359)
[    1.184214] ACPI Error: Method parse/execution failed [\_SB.PCI0.SAT0.SPT0._GTF] (Node ffff88040f4ce230), AE_NOT_FOUND (20150930/psparse-542)
[    1.184705] ata1.00: ATA-8: WDC WD20EARX-00PASB0, 51.0AB51, max UDMA/133
[    1.184710] ata1.00: 3907029168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.191722] ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20150930/psargs-359)
[    1.191735] ACPI Error: Method parse/execution failed [\_SB.PCI0.SAT0.SPT0._GTF] (Node ffff88040f4ce230), AE_NOT_FOUND (20150930/psparse-542)
[    1.192722] ata1.00: configured for UDMA/133
[    1.193033] scsi 0:0:0:0: Direct-Access     ATA      WDC WD20EARX-00P AB51 PQ: 0 ANSI: 5
[    1.193315] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.193319] sd 0:0:0:0: [sda] 3907029168 512-byte logical blocks: (2.00 TB/1.82 TiB)
[    1.193321] sd 0:0:0:0: [sda] 4096-byte physical blocks
[    1.193376] sd 0:0:0:0: [sda] Write Protect is off
[    1.193377] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.193386] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.193569] scsi 1:0:0:0: Direct-Access     ATA      M4-CT256M4SSD2   040H PQ: 0 ANSI: 5
[    1.193830] sd 1:0:0:0: Attached scsi generic sg1 type 0
[    1.193832] sd 1:0:0:0: [sdb] 500118192 512-byte logical blocks: (256 GB/238 GiB)
[    1.193942] sd 1:0:0:0: [sdb] Write Protect is off
[    1.193945] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    1.193964] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.195474]  sdb: sdb1 sdb2 sdb3
[    1.195786] sd 1:0:0:0: [sdb] Attached SCSI disk
[    1.200151] scsi 2:0:0:0: CD-ROM            PIONEER  DVD-RW  DVR-212D 1.15 PQ: 0 ANSI: 5
[    1.214505]  sda: sda1
[    1.214730] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.223130] sr 2:0:0:0: [sr0] scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[    1.223134] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.223301] sr 2:0:0:0: Attached scsi CD-ROM sr0
[    1.223446] sr 2:0:0:0: Attached scsi generic sg2 type 5
[    1.223617] scsi 3:0:0:0: Direct-Access     ATA      WDC WD1001FALS-0 0K05 PQ: 0 ANSI: 5
[    1.223729] sd 3:0:0:0: Attached scsi generic sg3 type 0
[    1.223739] sd 3:0:0:0: [sdc] 1953525168 512-byte logical blocks: (1.00 TB/932 GiB)
[    1.223855] scsi 4:0:0:0: Direct-Access     ATA      ST3500320AS      SD15 PQ: 0 ANSI: 5
[    1.223889] sd 3:0:0:0: [sdc] Write Protect is off
[    1.223892] sd 3:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    1.223932] sd 4:0:0:0: [sdd] 976773168 512-byte logical blocks: (500 GB/466 GiB)
[    1.223948] sd 4:0:0:0: Attached scsi generic sg4 type 0
[    1.223949] sd 4:0:0:0: [sdd] Write Protect is off
[    1.223950] sd 4:0:0:0: [sdd] Mode Sense: 00 3a 00 00
[    1.223951] sd 3:0:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.223957] sd 4:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.235487]  sdd: sdd1 < sdd5 >
[    1.235716] sd 4:0:0:0: [sdd] Attached SCSI disk
[    1.266531]  sdc: sdc1 sdc2 sdc3 sdc4
[    1.267236] sd 3:0:0:0: [sdc] Attached SCSI disk
[    1.397204] usb 1-1.5: new full-speed USB device number 3 using ehci-pci
[    1.410452] usb 3-2: New USB device found, idVendor=046d, idProduct=081b
[    1.410457] usb 3-2: New USB device strings: Mfr=0, Product=0, SerialNumber=2
[    1.410460] usb 3-2: SerialNumber: F1AD8E40
[    1.490768] usb 5-2: New USB device found, idVendor=046d, idProduct=c318
[    1.490773] usb 5-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.490776] usb 5-2: Product: Logitech Illuminated Keyboard
[    1.490778] usb 5-2: Manufacturer: Logitech
[    1.492776] usb 1-1.5: New USB device found, idVendor=046d, idProduct=c52b
[    1.492778] usb 1-1.5: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.492779] usb 1-1.5: Product: USB Receiver
[    1.492780] usb 1-1.5: Manufacturer: Logitech
[    1.494786] hidraw: raw HID events driver (C) Jiri Kosina
[    1.502177] usbcore: registered new interface driver usbhid
[    1.502180] usbhid: USB HID core driver
[    1.503246] input: Logitech Logitech Illuminated Keyboard as /devices/pci0000:00/0000:00:1c.7/0000:06:00.0/usb5/5-2/5-2:1.0/0003:046D:C318.0001/input/input6
[    1.504493] logitech-djreceiver 0003:046D:C52B.0005: hiddev0,hidraw0: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1a.0-1.5/input2
[    1.557400] hid-generic 0003:046D:C318.0001: input,hidraw1: USB HID v1.11 Keyboard [Logitech Logitech Illuminated Keyboard] on usb-0000:06:00.0-2/input0
[    1.557917] input: Logitech Logitech Illuminated Keyboard as /devices/pci0000:00/0000:00:1c.7/0000:06:00.0/usb5/5-2/5-2:1.1/0003:046D:C318.0002/input/input7
[    1.620910] input: Logitech Performance MX as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.5/1-1.5:1.2/0003:046D:C52B.0005/0003:046D:101A.0006/input/input8
[    1.637197] tsc: Refined TSC clocksource calibration: 3410.013 MHz
[    1.637202] clocksource: tsc: mask: 0xffffffffffffffff max_cycles: 0x3127418e06e, max_idle_ns: 440795285561 ns
[    1.669553] hid-generic 0003:046D:C318.0002: input,hiddev0,hidraw2: USB HID v1.11 Device [Logitech Logitech Illuminated Keyboard] on usb-0000:06:00.0-2/input1
[    1.669591] logitech-hidpp-device 0003:046D:101A.0006: input,hidraw3: USB HID v1.11 Mouse [Logitech Performance MX] on usb-0000:00:1a.0-1.5:1
[    1.788293] EXT4-fs (sdb2): mounted filesystem with ordered data mode. Opts: (null)
[    1.864913] efivars: duplicate variable: SbAslBufferPtrVar-01f33c25-764d-43ea-aeea-6b5a41f3f3e8
[    1.872174] systemd[1]: systemd 229 running in system mode. (+PAM +AUDIT +SELINUX +IMA +APPARMOR +SMACK +SYSVINIT +UTMP +LIBCRYPTSETUP +GCRYPT +GNUTLS +ACL +XZ -LZ4 +SECCOMP +BLKID +ELFUTILS +KMOD -IDN)
[    1.872258] systemd[1]: Detected architecture x86-64.
[    1.872444] systemd[1]: Set hostname to <desktop>.
[    1.963374] systemd[1]: Listening on /dev/initctl Compatibility Named Pipe.
[    1.963429] systemd[1]: Listening on Journal Socket (/dev/log).
[    1.963455] systemd[1]: Listening on Journal Socket.
[    1.963520] systemd[1]: Created slice System Slice.
[    1.973267] systemd[1]: Starting Uncomplicated firewall...
[    1.973331] systemd[1]: Created slice system-getty.slice.
[    1.973612] systemd[1]: Mounting Huge Pages File System...
[    1.973657] systemd[1]: Listening on Syslog Socket.
[    1.973975] systemd[1]: Started Braille Device Support.
[    1.974537] systemd[1]: Starting Create list of required static device nodes for the current kernel...
[    1.974596] systemd[1]: Started Forward Password Requests to Wall Directory Watch.
[    1.974649] systemd[1]: Listening on fsck to fsckd communication Socket.
[    1.974980] systemd[1]: Mounting POSIX Message Queue File System...
[    1.974997] systemd[1]: Reached target User and Group Name Lookups.
[    1.975041] systemd[1]: Reached target Remote File Systems (Pre).
[    1.975053] systemd[1]: Reached target Remote File Systems.
[    1.975811] random: nonblocking pool is initialized
[    1.975918] systemd[1]: Started Read required files in advance.
[    1.975998] systemd[1]: Listening on udev Control Socket.
[    1.976068] systemd[1]: Created slice system-systemd\x2dfsck.slice.
[    1.976129] systemd[1]: Created slice system-tor.slice.
[    1.976373] systemd[1]: Mounting Debug File System...
[    1.976410] systemd[1]: Listening on udev Kernel Socket.
[    1.976753] systemd[1]: Set up automount Arbitrary Executable File Formats File System Automount Point.
[    1.978925] systemd[1]: Reached target Encrypted Volumes.
[    1.979015] systemd[1]: Created slice User and Session Slice.
[    1.979027] systemd[1]: Reached target Slices.
[    1.980662] systemd[1]: Starting Load Kernel Modules...
[    1.980735] systemd[1]: Listening on Journal Audit Socket.
[    1.981002] systemd[1]: Starting Journal Service...
[    1.981862] systemd[1]: Started Uncomplicated firewall.
[    1.981983] systemd[1]: Started Create list of required static device nodes for the current kernel.
[    1.984459] systemd[1]: Mounted POSIX Message Queue File System.
[    1.984487] systemd[1]: Mounted Huge Pages File System.
[    1.984504] systemd[1]: Mounted Debug File System.
[    1.997381] systemd[1]: Starting Create Static Device Nodes in /dev...
[    1.998415] lp: driver loaded but no devices found
[    2.000163] ppdev: user-space parallel port driver
[    2.003346] systemd[1]: Started Load Kernel Modules.
[    2.004898] systemd[1]: Starting Apply Kernel Variables...
[    2.005271] systemd[1]: Mounting FUSE Control File System...
[    2.006459] systemd[1]: Mounted FUSE Control File System.
[    2.012550] systemd[1]: Started Apply Kernel Variables.
[    2.016801] systemd[1]: Started Create Static Device Nodes in /dev.
[    2.017144] systemd[1]: Starting udev Kernel Device Manager...
[    2.019857] systemd[1]: Started Journal Service.
[    2.076091] EXT4-fs (sdb2): re-mounted. Opts: errors=remount-ro
[    2.083597] systemd-journald[273]: Received request to flush runtime journal from PID 1
[    2.142641] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    2.146861] ACPI Warning: SystemIO range 0x0000000000000428-0x000000000000042F conflicts with OpRegion 0x0000000000000400-0x000000000000047F (\PMIO) (20150930/utaddress-254)
[    2.146865] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    2.146868] ACPI Warning: SystemIO range 0x0000000000000540-0x000000000000054F conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20150930/utaddress-254)
[    2.146870] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    2.146871] ACPI Warning: SystemIO range 0x0000000000000530-0x000000000000053F conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20150930/utaddress-254)
[    2.146873] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    2.146873] ACPI Warning: SystemIO range 0x0000000000000500-0x000000000000052F conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20150930/utaddress-254)
[    2.146875] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    2.146876] lpc_ich: Resource conflict(s) found affecting gpio_ich
[    2.146988] EDAC MC: Ver: 3.0.0
[    2.191618] media: Linux media interface: v0.10
[    2.204096] Linux video capture interface: v2.00
[    2.206196] snd_hda_intel 0000:00:1b.0: enabling device (0000 -> 0002)
[    2.211367] AVX version of gcm_enc/dec engaged.
[    2.211370] AES CTR mode by8 optimization enabled
[    2.212236] Adding 16458748k swap on /dev/sdb3.  Priority:-1 extents:1 across:16458748k SSFS
[    2.226704] snd_hda_codec_realtek hdaudioC0D0: autoconfig for ALC892: line_outs=4 (0x14/0x15/0x16/0x17/0x0) type:line
[    2.226707] snd_hda_codec_realtek hdaudioC0D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[    2.226708] snd_hda_codec_realtek hdaudioC0D0:    hp_outs=1 (0x1b/0x0/0x0/0x0/0x0)
[    2.226709] snd_hda_codec_realtek hdaudioC0D0:    mono: mono_out=0x0
[    2.226710] snd_hda_codec_realtek hdaudioC0D0:    dig-out=0x11/0x1e
[    2.226711] snd_hda_codec_realtek hdaudioC0D0:    inputs:
[    2.226713] snd_hda_codec_realtek hdaudioC0D0:      Front Mic=0x19
[    2.226714] snd_hda_codec_realtek hdaudioC0D0:      Rear Mic=0x18
[    2.226715] snd_hda_codec_realtek hdaudioC0D0:      Line=0x1a
[    2.272398] input: HDA Intel PCH Front Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[    2.272444] input: HDA Intel PCH Rear Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[    2.272478] input: HDA Intel PCH Line as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[    2.272516] input: HDA Intel PCH Line Out Front as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[    2.272551] input: HDA Intel PCH Line Out Surround as /devices/pci0000:00/0000:00:1b.0/sound/card0/input13
[    2.272590] input: HDA Intel PCH Line Out CLFE as /devices/pci0000:00/0000:00:1b.0/sound/card0/input14
[    2.272635] input: HDA Intel PCH Line Out Side as /devices/pci0000:00/0000:00:1b.0/sound/card0/input15
[    2.272717] input: HDA Intel PCH Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input16
[    2.272765] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input17
[    2.272803] input: HDA Intel PCH HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input18
[    2.273853] intel_rapl: Found RAPL domain package
[    2.273854] intel_rapl: Found RAPL domain core
[    2.273855] intel_rapl: Found RAPL domain uncore
[    2.273862] intel_rapl: RAPL package 0 domain package locked by BIOS
[    2.293752] asus_wmi: ASUS WMI generic driver loaded
[    2.294920] asus_wmi: Initialization: 0x0
[    2.294934] asus_wmi: BIOS WMI version: 0.9
[    2.294956] asus_wmi: SFUN value: 0x0
[    2.295160] input: Eee PC WMI hotkeys as /devices/platform/eeepc-wmi/input/input19
[    2.298903] asus_wmi: Number of fans: 1
[    2.416135] EXT4-fs (sdc1): mounted filesystem with ordered data mode. Opts: (null)
[    2.593577] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    2.637360] clocksource: Switched to clocksource tsc
[    3.545636] usb 3-2: set resolution quirk: cval->res = 384
[    3.545902] usbcore: registered new interface driver snd-usb-audio
[    3.545937] uvcvideo: Found UVC 1.00 device <unnamed> (046d:081b)
[    3.560908] input: UVC Camera (046d:081b) as /devices/pci0000:00/0000:00:14.0/usb3/3-2/3-2:1.0/input/input20
[    3.560980] usbcore: registered new interface driver uvcvideo
[    3.560981] USB Video Class driver (1.1.1)
[    3.960429] [drm:intel_set_pch_fifo_underrun_reporting [i915]] *ERROR* uncleared pch fifo underrun on pch transcoder A
[    3.960443] [drm:intel_pch_fifo_underrun_irq_handler [i915]] *ERROR* PCH transcoder A FIFO underrun
[  219.298881] EXT4-fs (sdd5): mounted filesystem with ordered data mode. Opts: (null)
[  219.382546] audit: type=1400 audit(1464357375.112:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="system_tor" pid=757 comm="apparmor_parser"
[  219.383408] audit: type=1400 audit(1464357375.112:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=756 comm="apparmor_parser"
[  219.383412] audit: type=1400 audit(1464357375.112:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=756 comm="apparmor_parser"
[  219.383416] audit: type=1400 audit(1464357375.112:5): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-helper" pid=756 comm="apparmor_parser"
[  219.383418] audit: type=1400 audit(1464357375.112:6): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=756 comm="apparmor_parser"
[  219.383807] audit: type=1400 audit(1464357375.112:7): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/ubuntu-core-launcher" pid=760 comm="apparmor_parser"
[  219.384452] audit: type=1400 audit(1464357375.112:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/lightdm/lightdm-guest-session" pid=755 comm="apparmor_parser"
[  219.384457] audit: type=1400 audit(1464357375.112:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/lightdm/lightdm-guest-session//chromium" pid=755 comm="apparmor_parser"
[  219.386549] audit: type=1400 audit(1464357375.116:10): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cups-browsed" pid=762 comm="apparmor_parser"
[  219.387685] audit: type=1400 audit(1464357375.116:11): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=763 comm="apparmor_parser"
[  219.677181] IPv6: ADDRCONF(NETDEV_UP): enp3s0: link is not ready
[  219.797267] r8169 0000:03:00.0 enp3s0: link down
[  219.797286] r8169 0000:03:00.0 enp3s0: link down
[  219.797344] IPv6: ADDRCONF(NETDEV_UP): enp3s0: link is not ready
[  222.526387] usb 3-2: reset high-speed USB device number 2 using xhci_hcd
[  222.635696] r8169 0000:03:00.0 enp3s0: link up
[  222.635705] IPv6: ADDRCONF(NETDEV_CHANGE): enp3s0: link becomes ready
[ 6273.916982] capability: warning: `VirtualBox' uses 32-bit capabilities (legacy support in use)

```

I'm not quite sure how to read this log. Anyone has any ideas? Any tips would greatly be appreciated

---

### Post by QDR06VV9 on 2016-05-27
What dose this return from the terminal
```
apt-cache policy linux-headers-generic
```

---

### Post by michael_hansen2 on 2016-05-27
It returns this:

```
linux-headers-generic:
  Installed: 4.4.0.21.22
  Candidate: 4.4.0.22.23
  Version table:
     4.4.0.22.23 500
        500 http://ca.archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu xenial-security/main amd64 Packages
 *** 4.4.0.21.22 500
        500 http://ca.archive.ubuntu.com/ubuntu xenial/main amd64 Packages
        100 /var/lib/dpkg/status
```

---

### Post by QDR06VV9 on 2016-05-27
Is this an EFI bios machine?

---

### Post by michael_hansen2 on 2016-05-27
Are you asking if my motherboard supports EFI?

---

### Post by QDR06VV9 on 2016-05-27
Yes

---

### Post by michael_hansen2 on 2016-05-27
I'm not quite sure if EFI and UEFI is the same, but my motherboard supports UEFI. Its ASUS P8Z77-V LK. Its also set to boot into UEFI btw

---

### Post by QDR06VV9 on 2016-05-27
You can find out by inputting this in the terminal
```
dmesg | grep "EFI v"
```

This will return a line like this, if the system was booted off of EFI:

```
[ 0.000000] EFI v2.00 by American Megatrends
```

---

### Post by QDR06VV9 on 2016-05-27
> **michael_hansen2 said:**
> I'm not quite sure if EFI and UEFI is the same, but my motherboard supports UEFI. Its ASUS P8Z77-V LK. Its also set to boot into UEFI btw
And is Secure Boot enabled?

---

### Post by QDR06VV9 on 2016-05-27
I ran into this issue a few days ago with a Friends laptop and the issue was SecureBoot. Seems if SecureBoot is enabled in the machine's BIOS then Ubuntu enforces the signing chain of bootloader, kernel and kernel modules. This, I assume, is what is causing modprobe to fail when installing the virtualbox kernel modules.

Check out the Ubuntu's SecurityTeam SecureBoot page for more information including potential workarounds.
[https://wiki.ubuntu.com/SecurityTeam/SecureBoot](https://wiki.ubuntu.com/SecurityTeam/SecureBoot)
I took the easy way out and just disabled SecureBoot and everything works fine now. 
**But he is not dual booting Windows/Ubuntu Just Ubuntu.**

---

### Post by michael_hansen2 on 2016-05-27
Sweeet. That did the trick. I had enabled SecureBoot, but it was at the default setting (Windows). I changed it to "Other OS" and that did the trick! Thank you so much :)

---

### Post by QDR06VV9 on 2016-05-27
Very nice and Glad I could help.
Now if you be as kind and mark this as solved as to help others that come looking for similar problem.
Best Regards

---

### Post by philipp-potocki on 2016-06-01
This is great advice and my VirtualBox service ran right away after disabling secure boot and rebooting.

However, it stopped working again after the last software update one or two days ago.  :-(

Edit: Actually, the system says upon starting that the Virtualbox service wasn't running. However, starting VirtualBox and a virtual machine works, anyway, as I've just found out. Well, that's good enough for now.

---

