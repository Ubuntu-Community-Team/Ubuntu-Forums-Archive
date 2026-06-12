---
title: "FS booting on Read Only Mode"
date: 2020-02-18
forum: Server Platforms
---

### Post by matusa15 on 2020-02-18
Hello.... I have very little linux experience, I have a home server and now is booting in RO.. no clue why or what to do about it.
Please find attached the dmesg output in it helps to troubleshoot the problem


Ill appreciate any help!!

Thanks

Cesar

---

### Post by TheFu on 2020-02-18
When a file system goes read-only, that means there is some sort of corruption that needs to be fixed (usually by a power spike) or some failing hardware like a HDD or disk controller.  Sometimes it is a loose SATA or power cable.

I didn't pull the odt file.  Sorry.  Just not comfortable opening random files off the internet.  If you would show the relevant parts of the logs here, making it easier for someone to help, that could be useful.

**fsck** is the normal way to fix a corrupted ext2/3/4 file system.  To run it, the file system cannot be mounted/active. For example:
```
sudo umount /dev/sdb1
sudo fsck /dev/sdb1
```
You can use **df -Th** to see the device name and mount point and file system type.  fsck doesn't work for NTFS, vFAT, exFAT, ZFS and a few other types of file systems. Almost all native Linux file systems will support fsck. 
If the problem is on the / file system, then depending on the OS version, we can tell it to run fsck at boot. Often, it is easiest to just boot from a "Try Ubuntu" flash drive and run the FSCK command.
If LVM or encryption are used, things are a little more complicated, but still workable.  Run this command:
```
lsblk -o name,size,type,fstype,mountpoint
```

If the storage is an SSD, this is the first warning that it is failing. There might be a few hours or 6 months remaining of life. When SSDs fail, there's no way to get any data off them.  Get backup religion ASAP.  If you have great backups, then perhaps keep using the SSD until it fails completely.  I've had 2 SSDs fail this way. My newer SSDs were respected, durable, known endurance, models from a respected brand.

If the fsck doesn't fix it, time to check the SMART data by using **smartctl**. There are lots of thread here for that. Search and you will find them. SMART data won't fix anything, but it will provide data to make decisions.

---

### Post by matusa15 on 2020-02-18
Hello,

Thanks for your anwser.

I had som power issues, so that looks like the root problem, no SSD drive

I booted the system in recovery mode and ran fcsk, but i got this message :

fcsk: /etc/fstab : parse error at line 2 -- ignored
/dev/md0 is mounted
e2fcsk : Cannot continue, aborting

I cant sudo anythinf wither, i got this message :

"unable to resolve host ubutnuserver : resource temporarily unabiale"

I chek that my hosts file is missing the hostname, but since the syste is in RO.. i dont know what to do...

I looks like Im goint to restart from scracth... i guess that i will doccument every step this time....

thanks!!!

this is the dmsg, no clue whats relevant, a coleague told me run that command and google the errors... I did it.. but, nothing htat i could understand

[    0.000000] microcode: microcode updated early to revision 0x21, date = 2019-02-13
[    0.000000] Linux version 4.15.0-76-generic (buildd@lcy01-amd64-029) (gcc version 7.4.0 (Ubuntu 7.4.0-1ubuntu1~18.04.1)) #86-Ubuntu SMP Fri Jan 17 17:24:28 UTC 2020 (Ubuntu 4.15.0-76.86-generic 4.15.18)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-4.15.0-76-generic root=UUID=f3332ca4-174c-11e9-a357-00fd45fd5d0c ro maybe-ubiquity
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] x86/fpu: Supporting XSAVE feature 0x001: 'x87 floating point registers'
[    0.000000] x86/fpu: Supporting XSAVE feature 0x002: 'SSE registers'
[    0.000000] x86/fpu: Supporting XSAVE feature 0x004: 'AVX registers'
[    0.000000] x86/fpu: xstate_offset[2]:  576, xstate_sizes[2]:  256
[    0.000000] x86/fpu: Enabled xstate features 0x7, context size is 832 bytes, using 'standard' format.
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x00000000000997ff] usable
[    0.000000] BIOS-e820: [mem 0x0000000000099800-0x0000000000099bff] reserved
[    0.000000] BIOS-e820: [mem 0x000000000009e000-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000f0000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000f1de3fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000f1de4000-0x00000000f1dedfff] ACPI data
[    0.000000] BIOS-e820: [mem 0x00000000f1dee000-0x00000000f7ffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fee0ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ff800000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000010bffefff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.7 present.
[    0.000000] DMI: HP ProLiant MicroServer Gen8, BIOS J06 11/02/2015
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] e820: last_pfn = 0x10bfff max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: write-back
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0F4000000 mask FFC000000 uncachable
[    0.000000]   1 base 0F8000000 mask FF8000000 uncachable
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000]   8 disabled
[    0.000000]   9 disabled
[    0.000000] x86/PAT: Configuration [0-7]: WB  WC  UC- UC  WB  WP  UC- WT  
[    0.000000] e820: last_pfn = 0xf1de4 max_arch_pfn = 0x400000000
[    0.000000] found SMP MP-table at [mem 0x000f4f80-0x000f4f8f]
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] BRK [0xa3b8e000, 0xa3b8efff] PGTABLE
[    0.000000] BRK [0xa3b8f000, 0xa3b8ffff] PGTABLE
[    0.000000] BRK [0xa3b90000, 0xa3b90fff] PGTABLE
[    0.000000] BRK [0xa3b91000, 0xa3b91fff] PGTABLE
[    0.000000] BRK [0xa3b92000, 0xa3b92fff] PGTABLE
[    0.000000] BRK [0xa3b93000, 0xa3b93fff] PGTABLE
[    0.000000] BRK [0xa3b94000, 0xa3b94fff] PGTABLE
[    0.000000] BRK [0xa3b95000, 0xa3b95fff] PGTABLE
[    0.000000] RAMDISK: [mem 0x3118b000-0x348bcfff]
[    0.000000] ACPI: Early table checksum verification disabled
[    0.000000] ACPI: RSDP 0x00000000000F4F00 000024 (v02 HP    )
[    0.000000] ACPI: XSDT 0x00000000F1DE6400 0000B4 (v01 HP     ProLiant 00000002 \xd2?   0000162E)
[    0.000000] ACPI: FACP 0x00000000F1DE6540 0000F4 (v03 HP     ProLiant 00000002 \xd2?   0000162E)
[    0.000000] ACPI BIOS Warning (bug): 32/64X length mismatch in FADT/Pm1aControlBlock: 16/32 (20170831/tbfadt-603)
[    0.000000] ACPI BIOS Warning (bug): 32/64X length mismatch in FADT/Pm2ControlBlock: 8/32 (20170831/tbfadt-603)
[    0.000000] ACPI BIOS Warning (bug): Invalid length for FADT/Pm1aControlBlock: 32, using default 16 (20170831/tbfadt-708)
[    0.000000] ACPI BIOS Warning (bug): Invalid length for FADT/Pm2ControlBlock: 32, using default 8 (20170831/tbfadt-708)
[    0.000000] ACPI: DSDT 0x00000000F1DE6640 001C1A (v01 HP     DSDT     00000001 INTL 20030228)
[    0.000000] ACPI: FACS 0x00000000F1DE4140 000040
[    0.000000] ACPI: FACS 0x00000000F1DE4140 000040
[    0.000000] ACPI: SPCR 0x00000000F1DE4180 000050 (v01 HP     SPCRRBSU 00000001 \xd2?   0000162E)
[    0.000000] ACPI: MCFG 0x00000000F1DE4200 00003C (v01 HP     ProLiant 00000001      00000000)
[    0.000000] ACPI: HPET 0x00000000F1DE4240 000038 (v01 HP     ProLiant 00000002 \xd2?   0000162E)
[    0.000000] ACPI: FFFF 0x00000000F1DE4280 000064 (v02 HP     ProLiant 00000002 \xd2?   0000162E)
[    0.000000] ACPI: SPMI 0x00000000F1DE4300 000040 (v05 HP     ProLiant 00000001 \xd2?   0000162E)
[    0.000000] ACPI: ERST 0x00000000F1DE4340 000230 (v01 HP     ProLiant 00000001 \xd2?   0000162E)
[    0.000000] ACPI: APIC 0x00000000F1DE4580 000252 (v01 HP     ProLiant 00000002      00000000)
[    0.000000] ACPI: FFFF 0x00000000F1DE4800 000176 (v01 HP     ProLiant 00000001 \xd2?   0000162E)
[    0.000000] ACPI: BERT 0x00000000F1DE4980 000030 (v01 HP     ProLiant 00000001 \xd2?   0000162E)
[    0.000000] ACPI: HEST 0x00000000F1DE49C0 0000BC (v01 HP     ProLiant 00000001 \xd2?   0000162E)
[    0.000000] ACPI: FFFF 0x00000000F1DE4A80 001914 (v01 HP     ProLiant 00000001 \xd2?   0000162E)
[    0.000000] ACPI: FFFF 0x00000000F1DE63C0 00002D (v01 HP     ProLiant 00000001      00000000)
[    0.000000] ACPI: SSDT 0x00000000F1DE8280 000137 (v03 HP     CRSPCI0  00000002 HP   00000001)
[    0.000000] ACPI: SSDT 0x00000000F1DE83C0 000177 (v03 HP     riser0   00000002 INTL 20030228)
[    0.000000] ACPI: SSDT 0x00000000F1DE8540 0001E1 (v01 HP     pcc      00000001 INTL 20090625)
[    0.000000] ACPI: SSDT 0x00000000F1DE8740 000377 (v01 HP     pmab     00000001 INTL 20090625)
[    0.000000] ACPI: SSDT 0x00000000F1DE8AC0 0009E4 (v01 INTEL  PPM RCM  80000001 INTL 20061109)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x000000010bffefff]
[    0.000000] NODE_DATA(0) allocated [mem 0x10bfd4000-0x10bffefff]
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x0000000000001000-0x0000000000ffffff]
[    0.000000]   DMA32    [mem 0x0000000001000000-0x00000000ffffffff]
[    0.000000]   Normal   [mem 0x0000000100000000-0x000000010bffefff]
[    0.000000]   Device   empty
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x0000000000001000-0x0000000000098fff]
[    0.000000]   node   0: [mem 0x0000000000100000-0x00000000f1de3fff]
[    0.000000]   node   0: [mem 0x0000000100000000-0x000000010bffefff]
[    0.000000] Reserved but unavailable: 104 pages
[    0.000000] Initmem setup node 0 [mem 0x0000000000001000-0x000000010bffefff]
[    0.000000] On node 0 totalpages: 1039739
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 21 pages reserved
[    0.000000]   DMA zone: 3992 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 16320 pages used for memmap
[    0.000000]   DMA32 zone: 986596 pages, LIFO batch:31
[    0.000000]   Normal zone: 768 pages used for memmap
[    0.000000]   Normal zone: 49151 pages, LIFO batch:15
[    0.000000] ACPI: PM-Timer IO Port: 0x908
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0xff] dfl dfl lint[0x1])
[    0.000000] IOAPIC[0]: apic_id 8, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] smpboot: Allowing 64 CPUs, 60 hotplug CPUs
[    0.000000] PM: Registered nosave memory: [mem 0x00000000-0x00000fff]
[    0.000000] PM: Registered nosave memory: [mem 0x00099000-0x00099fff]
[    0.000000] PM: Registered nosave memory: [mem 0x00099000-0x0009dfff]
[    0.000000] PM: Registered nosave memory: [mem 0x0009e000-0x0009ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000effff]
[    0.000000] PM: Registered nosave memory: [mem 0x000f0000-0x000fffff]
[    0.000000] PM: Registered nosave memory: [mem 0xf1de4000-0xf1dedfff]
[    0.000000] PM: Registered nosave memory: [mem 0xf1dee000-0xf7ffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xf8000000-0xfebfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xfee0ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfee10000-0xff7fffff]
[    0.000000] PM: Registered nosave memory: [mem 0xff800000-0xffffffff]
[    0.000000] e820: [mem 0xf8000000-0xfebfffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] clocksource: refined-jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645519600211568 ns
[    0.000000] random: get_random_bytes called from start_kernel+0x99/0x4fd with crng_init=0
[    0.000000] setup_percpu: NR_CPUS:8192 nr_cpumask_bits:64 nr_cpu_ids:64 nr_node_ids:1
[    0.000000] percpu: Embedded 45 pages/cpu s147456 r8192 d28672 u262144
[    0.000000] pcpu-alloc: s147456 r8192 d28672 u262144 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 00 01 02 03 04 05 06 07 [0] 08 09 10 11 12 13 14 15 
[    0.000000] pcpu-alloc: [0] 16 17 18 19 20 21 22 23 [0] 24 25 26 27 28 29 30 31 
[    0.000000] pcpu-alloc: [0] 32 33 34 35 36 37 38 39 [0] 40 41 42 43 44 45 46 47 
[    0.000000] pcpu-alloc: [0] 48 49 50 51 52 53 54 55 [0] 56 57 58 59 60 61 62 63 
[    0.000000] Built 1 zonelists, mobility grouping on.  Total pages: 1022566
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.15.0-76-generic root=UUID=f3332ca4-174c-11e9-a357-00fd45fd5d0c ro maybe-ubiquity
[    0.000000] log_buf_len individual max cpu contribution: 4096 bytes
[    0.000000] log_buf_len total cpu_extra contributions: 258048 bytes
[    0.000000] log_buf_len min size: 262144 bytes
[    0.000000] log_buf_len: 524288 bytes
[    0.000000] early log buf free: 251424(95%)
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 3928268K/4158956K available (12300K kernel code, 2481K rwdata, 4260K rodata, 2428K init, 2704K bss, 230688K reserved, 0K cma-reserved)
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=64, Nodes=1
[    0.000000] Kernel/User page tables isolation: enabled
[    0.000000] ftrace: allocating 39322 entries in 154 pages
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU restricting CPUs from NR_CPUS=8192 to nr_cpu_ids=64.
[    0.000000] 	Tasks RCU enabled.
[    0.000000] RCU: Adjusting geometry for rcu_fanout_leaf=16, nr_cpu_ids=64
[    0.000000] NR_IRQS: 524544, nr_irqs: 936, preallocated irqs: 16
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] ACPI: Core revision 20170831
[    0.000000] ACPI: 6 ACPI AML tables successfully acquired and loaded
[    0.000000] clocksource: hpet: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 133484882848 ns
[    0.000000] hpet clockevent registered
[    0.000000] APIC: Switch to symmetric I/O mode setup
[    0.000000] Switched APIC routing to physical flat.
[    0.000000] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.020000] tsc: Fast TSC calibration using PIT
[    0.024000] tsc: Detected 3392.165 MHz processor
[    0.024000] Calibrating delay loop (skipped), value calculated using timer frequency.. 6784.33 BogoMIPS (lpj=13568660)
[    0.024000] pid_max: default: 65536 minimum: 512
[    0.024000] Security Framework initialized
[    0.024000] Yama: becoming mindful.
[    0.024000] AppArmor: AppArmor initialized
[    0.028256] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.028961] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.029065] Mount-cache hash table entries: 8192 (order: 4, 65536 bytes)
[    0.029145] Mountpoint-cache hash table entries: 8192 (order: 4, 65536 bytes)
[    0.029507] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
[    0.029572] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
[    0.029646] CPU0: Thermal monitoring enabled (TM1)
[    0.029715] process: using mwait in idle threads
[    0.029780] Last level iTLB entries: 4KB 512, 2MB 8, 4MB 8
[    0.029844] Last level dTLB entries: 4KB 512, 2MB 32, 4MB 32, 1GB 0
[    0.029910] Spectre V1 : Mitigation: usercopy/swapgs barriers and __user pointer sanitization
[    0.029989] Spectre V2 : Mitigation: Full generic retpoline
[    0.030052] Spectre V2 : Spectre v2 / SpectreRSB mitigation: Filling RSB on context switch
[    0.030131] Spectre V2 : Enabling Restricted Speculation for firmware calls
[    0.030203] Spectre V2 : mitigation: Enabling conditional Indirect Branch Prediction Barrier
[    0.030281] Spectre V2 : User space: Mitigation: STIBP via seccomp and prctl
[    0.030348] Speculative Store Bypass: Mitigation: Speculative Store Bypass disabled via prctl and seccomp
[    0.030449] MDS: Mitigation: Clear CPU buffers
[    0.030675] Freeing SMP alternatives memory: 36K
[    0.032459] TSC deadline timer enabled
[    0.032464] smpboot: CPU0: Intel(R) Core(TM) i3-3240 CPU @ 3.40GHz (family: 0x6, model: 0x3a, stepping: 0x9)
[    0.032636] Performance Events: PEBS fmt1+, IvyBridge events, 16-deep LBR, full-width counters, Broken BIOS detected, complain to your hardware vendor.
[    0.032738] [Firmware Bug]: the BIOS has corrupted hw-PMU resources (MSR 38d is 330)
[    0.032818] Intel PMU driver.
[    0.032884] ... version:                3
[    0.032949] ... bit width:              48
[    0.036001] ... generic registers:      4
[    0.036065] ... value mask:             0000ffffffffffff
[    0.036128] ... max period:             00007fffffffffff
[    0.036191] ... fixed-purpose events:   3
[    0.036253] ... event mask:             000000070000000f
[    0.036379] Hierarchical SRCU implementation.
[    0.040150] NMI watchdog: Enabled. Permanently consumes one hw-PMU counter.
[    0.040234] smp: Bringing up secondary CPUs ...
[    0.040378] x86: Booting SMP configuration:
[    0.040440] .... node  #0, CPUs:        #1  #2
[    0.046067] MDS CPU bug present and SMT on, data leak possible. See [https://www.kernel.org/doc/html/latest/admin-guide/hw-vuln/mds.html](https://www.kernel.org/doc/html/latest/admin-guide/hw-vuln/mds.html) for more details.
[    0.046067]   #3
[    0.048050] smp: Brought up 1 node, 4 CPUs
[    0.048145] smpboot: Max logical packages: 16
[    0.048208] smpboot: Total of 4 processors activated (27137.32 BogoMIPS)
[    0.050616] devtmpfs: initialized
[    0.050616] x86/mm: Memory block size: 128MB
[    0.050616] evm: security.selinux
[    0.050616] evm: security.SMACK64
[    0.050616] evm: security.SMACK64EXEC
[    0.050616] evm: security.SMACK64TRANSMUTE
[    0.050616] evm: security.SMACK64MMAP
[    0.050616] evm: security.apparmor
[    0.050616] evm: security.ima
[    0.052005] evm: security.capability
[    0.052106] clocksource: jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645041785100000 ns
[    0.052128] futex hash table entries: 16384 (order: 8, 1048576 bytes)
[    0.052416] pinctrl core: initialized pinctrl subsystem
[    0.052569] RTC time: 12:38:11, date: 02/18/20
[    0.052740] NET: Registered protocol family 16
[    0.052863] audit: initializing netlink subsys (disabled)
[    0.052932] audit: type=2000 audit(1582029491.052:1): state=initialized audit_enabled=0 res=1
[    0.052932] cpuidle: using governor ladder
[    0.052932] cpuidle: using governor menu
[    0.052932] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.052932] ACPI: bus type PCI registered
[    0.052932] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.052932] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf4000000-0xf7ffffff] (base 0xf4000000)
[    0.052932] PCI: MMCONFIG at [mem 0xf4000000-0xf7ffffff] reserved in E820
[    0.052932] PCI: Using configuration type 1 for base access
[    0.052932] core: PMU erratum BJ122, BV98, HSD29 worked around, HT is on
[    0.056057] HugeTLB registered 2.00 MiB page size, pre-allocated 0 pages
[    0.056125] ACPI: Added _OSI(Module Device)
[    0.056188] ACPI: Added _OSI(Processor Device)
[    0.056251] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.056314] ACPI: Added _OSI(Processor Aggregator Device)
[    0.056378] ACPI: Added _OSI(Linux-Dell-Video)
[    0.056441] ACPI: Added _OSI(Linux-Lenovo-NV-HDMI-Audio)
[    0.056506] ACPI: Added _OSI(Linux-HPI-Hybrid-Graphics)
[    0.058117] ACPI: Interpreter enabled
[    0.058193] ACPI: (supports S0 S4 S5)
[    0.058259] ACPI: Using IOAPIC for interrupt routing
[    0.058342] HEST: Table parsing has been initialized.
[    0.058410] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.061466] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-14])
[    0.061536] acpi PNP0A08:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
[    0.061714] acpi PNP0A08:00: _OSC: platform does not support [PCIeHotplug PME AER PCIeCapability]
[    0.061794] acpi PNP0A08:00: _OSC: not requesting control; platform does not support [PCIeCapability]
[    0.061874] acpi PNP0A08:00: _OSC: OS requested [PCIeHotplug PME AER PCIeCapability]
[    0.061953] acpi PNP0A08:00: _OSC: platform willing to grant []
[    0.062018] acpi PNP0A08:00: _OSC failed (AE_SUPPORT); disabling ASPM
[    0.062098] acpi PNP0A08:00: host bridge window expanded to [mem 0xfed00000-0xfed44fff window]; [mem 0xfed00000-0xfed44fff window] ignored
[    0.062278] PCI host bridge to bus 0000:00
[    0.062343] pci_bus 0000:00: root bus resource [mem 0xf8000000-0xfbffffff window]
[    0.062421] pci_bus 0000:00: root bus resource [io  0x1000-0xffff window]
[    0.062487] pci_bus 0000:00: root bus resource [io  0x0000-0x03af window]
[    0.062552] pci_bus 0000:00: root bus resource [io  0x03e0-0x0cf7 window]
[    0.062617] pci_bus 0000:00: root bus resource [io  0x0d00-0x0fff window]
[    0.062683] pci_bus 0000:00: root bus resource [mem 0xfed00000-0xfed44fff window]
[    0.062762] pci_bus 0000:00: root bus resource [io  0x03b0-0x03bb window]
[    0.062828] pci_bus 0000:00: root bus resource [io  0x03c0-0x03df window]
[    0.062895] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff window]
[    0.062973] pci_bus 0000:00: root bus resource [bus 00-14]
[    0.063043] pci 0000:00:00.0: [8086:0150] type 00 class 0x060000
[    0.063109] pci 0000:00:01.0: [8086:0151] type 01 class 0x060400
[    0.063190] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.063257] pci 0000:00:06.0: [8086:015d] type 01 class 0x060400
[    0.063331] pci 0000:00:06.0: PME# supported from D0 D3hot D3cold
[    0.063405] pci 0000:00:1a.0: [8086:1c2d] type 00 class 0x0c0320
[    0.063425] pci 0000:00:1a.0: reg 0x10: [mem 0xfacf0000-0xfacf03ff]
[    0.063501] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    0.063550] pci 0000:00:1c.0: [8086:1c10] type 01 class 0x060400
[    0.063625] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.063679] pci 0000:00:1c.4: [8086:1c18] type 01 class 0x060400
[    0.063752] pci 0000:00:1c.4: PME# supported from D0 D3hot D3cold
[    0.063806] pci 0000:00:1c.6: [8086:1c1c] type 01 class 0x060400
[    0.063880] pci 0000:00:1c.6: PME# supported from D0 D3hot D3cold
[    0.063930] pci 0000:00:1c.7: [8086:1c1e] type 01 class 0x060400
[    0.064006] pci 0000:00:1c.7: PME# supported from D0 D3hot D3cold
[    0.064063] pci 0000:00:1d.0: [8086:1c26] type 00 class 0x0c0320
[    0.064082] pci 0000:00:1d.0: reg 0x10: [mem 0xface0000-0xface03ff]
[    0.064157] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    0.064201] pci 0000:00:1e.0: [8086:244e] type 01 class 0x060401
[    0.064284] pci 0000:00:1f.0: [8086:1c54] type 00 class 0x060100
[    0.064423] pci 0000:00:1f.2: [8086:1c02] type 00 class 0x010601
[    0.064438] pci 0000:00:1f.2: reg 0x10: [io  0x10c0-0x10c7]
[    0.064444] pci 0000:00:1f.2: reg 0x14: [io  0x10c8-0x10cb]
[    0.064450] pci 0000:00:1f.2: reg 0x18: [io  0x10d0-0x10d7]
[    0.064456] pci 0000:00:1f.2: reg 0x1c: [io  0x10d8-0x10db]
[    0.064462] pci 0000:00:1f.2: reg 0x20: [io  0x10e0-0x10ff]
[    0.064468] pci 0000:00:1f.2: reg 0x24: [mem 0xfacd0000-0xfacd07ff]
[    0.064503] pci 0000:00:1f.2: PME# supported from D3hot
[    0.064834] pci 0000:00:01.0: PCI bridge to [bus 07]
[    0.064939] pci 0000:00:06.0: PCI bridge to [bus 02]
[    0.065042] pci 0000:00:1c.0: PCI bridge to [bus 0d]
[    0.065162] pci 0000:03:00.0: [14e4:165f] type 00 class 0x020000
[    0.065198] pci 0000:03:00.0: reg 0x10: [mem 0xfabf0000-0xfabfffff 64bit pref]
[    0.065216] pci 0000:03:00.0: reg 0x18: [mem 0xfabe0000-0xfabeffff 64bit pref]
[    0.065233] pci 0000:03:00.0: reg 0x20: [mem 0xfabd0000-0xfabdffff 64bit pref]
[    0.065245] pci 0000:03:00.0: reg 0x30: [mem 0x00000000-0x0001ffff pref]
[    0.065345] pci 0000:03:00.0: PME# supported from D0 D3hot D3cold
[    0.065418] pci 0000:03:00.1: [14e4:165f] type 00 class 0x020000
[    0.065454] pci 0000:03:00.1: reg 0x10: [mem 0xfabc0000-0xfabcffff 64bit pref]
[    0.065472] pci 0000:03:00.1: reg 0x18: [mem 0xfabb0000-0xfabbffff 64bit pref]
[    0.065489] pci 0000:03:00.1: reg 0x20: [mem 0xfaba0000-0xfabaffff 64bit pref]
[    0.065501] pci 0000:03:00.1: reg 0x30: [mem 0x00000000-0x0001ffff pref]
[    0.065601] pci 0000:03:00.1: PME# supported from D0 D3hot D3cold
[    0.076034] pci 0000:00:1c.4: PCI bridge to [bus 03]
[    0.076118] pci 0000:00:1c.4:   bridge window [mem 0xfab00000-0xfabfffff 64bit pref]
[    0.076176] pci 0000:04:00.0: [1912:0014] type 00 class 0x0c0330
[    0.076225] pci 0000:04:00.0: reg 0x10: [mem 0xfbff0000-0xfbff1fff 64bit]
[    0.076409] pci 0000:04:00.0: PME# supported from D0 D3hot D3cold
[    0.088028] pci 0000:00:1c.6: PCI bridge to [bus 04]
[    0.088109] pci 0000:00:1c.6:   bridge window [mem 0xfbf00000-0xfbffffff]
[    0.088172] pci 0000:01:00.0: [103c:3306] type 00 class 0x088000
[    0.088200] pci 0000:01:00.0: reg 0x10: [io  0x3000-0x30ff]
[    0.088213] pci 0000:01:00.0: reg 0x14: [mem 0xfbef0000-0xfbef01ff]
[    0.088225] pci 0000:01:00.0: reg 0x18: [io  0x3400-0x34ff]
[    0.088390] pci 0000:01:00.1: [102b:0533] type 00 class 0x030000
[    0.088419] pci 0000:01:00.1: reg 0x10: [mem 0xf9000000-0xf9ffffff pref]
[    0.088431] pci 0000:01:00.1: reg 0x14: [mem 0xfbee0000-0xfbee3fff]
[    0.088443] pci 0000:01:00.1: reg 0x18: [mem 0xfb000000-0xfb7fffff]
[    0.088604] pci 0000:01:00.2: [103c:3307] type 00 class 0x088000
[    0.088632] pci 0000:01:00.2: reg 0x10: [io  0x3800-0x38ff]
[    0.088644] pci 0000:01:00.2: reg 0x14: [mem 0xfaff0000-0xfaff00ff]
[    0.088657] pci 0000:01:00.2: reg 0x18: [mem 0xfae00000-0xfaefffff]
[    0.088669] pci 0000:01:00.2: reg 0x1c: [mem 0xfad80000-0xfadfffff]
[    0.088681] pci 0000:01:00.2: reg 0x20: [mem 0xfad70000-0xfad77fff]
[    0.088694] pci 0000:01:00.2: reg 0x24: [mem 0xfad60000-0xfad67fff]
[    0.088707] pci 0000:01:00.2: reg 0x30: [mem 0x00000000-0x0000ffff pref]
[    0.088774] pci 0000:01:00.2: PME# supported from D0 D3hot D3cold
[    0.088828] pci 0000:01:00.4: [103c:3300] type 00 class 0x0c0300
[    0.088902] pci 0000:01:00.4: reg 0x20: [io  0x3c00-0x3c1f]
[    0.100027] pci 0000:00:1c.7: PCI bridge to [bus 01]
[    0.100106] pci 0000:00:1c.7:   bridge window [io  0x3000-0x3fff]
[    0.100108] pci 0000:00:1c.7:   bridge window [mem 0xfad00000-0xfbefffff]
[    0.100112] pci 0000:00:1c.7:   bridge window [mem 0xf9000000-0xf9ffffff 64bit pref]
[    0.100169] pci 0000:00:1e.0: PCI bridge to [bus 14] (subtractive decode)
[    0.100240] pci 0000:00:1e.0:   bridge window [mem 0xf8000000-0xfbffffff window] (subtractive decode)
[    0.100241] pci 0000:00:1e.0:   bridge window [io  0x1000-0xffff window] (subtractive decode)
[    0.100242] pci 0000:00:1e.0:   bridge window [io  0x0000-0x03af window] (subtractive decode)
[    0.100243] pci 0000:00:1e.0:   bridge window [io  0x03e0-0x0cf7 window] (subtractive decode)
[    0.100244] pci 0000:00:1e.0:   bridge window [io  0x0d00-0x0fff window] (subtractive decode)
[    0.100244] pci 0000:00:1e.0:   bridge window [mem 0xfed00000-0xfed44fff window] (subtractive decode)
[    0.100245] pci 0000:00:1e.0:   bridge window [io  0x03b0-0x03bb window] (subtractive decode)
[    0.100246] pci 0000:00:1e.0:   bridge window [io  0x03c0-0x03df window] (subtractive decode)
[    0.100247] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff window] (subtractive decode)
[    0.100279] pci_bus 0000:00: on NUMA node 0
[    0.100496] ACPI: PCI Interrupt Link [LNKA] (IRQs 5 7 10 *11)
[    0.100609] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 *7 10 11)
[    0.100719] ACPI: PCI Interrupt Link [LNKC] (IRQs 5 7 10 *11)
[    0.100828] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 7 *10 11)
[    0.100938] ACPI: PCI Interrupt Link [LNKE] (IRQs *5 7 10 11)
[    0.101048] ACPI: PCI Interrupt Link [LNKF] (IRQs 5 7 10 11) *4
[    0.101156] ACPI: PCI Interrupt Link [LNKG] (IRQs 5 7 10 11) *0, disabled.
[    0.101267] ACPI: PCI Interrupt Link [LNKH] (IRQs 5 7 10 11) *0, disabled.
[    0.101603] SCSI subsystem initialized
[    0.101689] libata version 3.00 loaded.
[    0.101689] pci 0000:01:00.1: vgaarb: setting as boot VGA device
[    0.101689] pci 0000:01:00.1: vgaarb: VGA device added: decodes=io+mem,owns=io+mem,locks=none
[    0.101689] pci 0000:01:00.1: vgaarb: bridge control possible
[    0.101689] vgaarb: loaded
[    0.101689] ACPI: bus type USB registered
[    0.101689] usbcore: registered new interface driver usbfs
[    0.101689] usbcore: registered new interface driver hub
[    0.101689] usbcore: registered new device driver usb
[    0.101689] EDAC MC: Ver: 3.0.0
[    0.101689] PCI: Using ACPI for IRQ routing
[    0.104036] PCI: pci_cache_line_size set to 64 bytes
[    0.104086] e820: reserve RAM buffer [mem 0x00099800-0x0009ffff]
[    0.104087] e820: reserve RAM buffer [mem 0xf1de4000-0xf3ffffff]
[    0.104088] e820: reserve RAM buffer [mem 0x10bfff000-0x10bffffff]
[    0.104172] NetLabel: Initializing
[    0.104234] NetLabel:  domain hash size = 128
[    0.104297] NetLabel:  protocols = UNLABELED CIPSOv4 CALIPSO
[    0.104374] NetLabel:  unlabeled traffic allowed by default
[    0.104503] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    0.104573] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    0.106665] clocksource: Switched to clocksource hpet
[    0.112995] VFS: Disk quotas dquot_6.6.0
[    0.113100] VFS: Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.113281] AppArmor: AppArmor Filesystem Enabled
[    0.113369] pnp: PnP ACPI init
[    0.113646] system 00:00: [io  0x0408-0x040f] has been reserved
[    0.113712] system 00:00: [io  0x04d0-0x04d1] has been reserved
[    0.113777] system 00:00: [io  0x0310-0x0313] has been reserved
[    0.113842] system 00:00: [io  0x0316-0x0317] has been reserved
[    0.113908] system 00:00: [io  0x0700-0x071f] has been reserved
[    0.113973] system 00:00: [io  0x0880-0x08ff] has been reserved
[    0.114038] system 00:00: [io  0x0900-0x097f] has been reserved
[    0.114102] system 00:00: [io  0x0cd4-0x0cd7] has been reserved
[    0.114167] system 00:00: [io  0x0cd0-0x0cd3] has been reserved
[    0.114233] system 00:00: [io  0x0f50-0x0f58] has been reserved
[    0.114299] system 00:00: [io  0x0ca0-0x0ca1] has been reserved
[    0.114363] system 00:00: [io  0x0ca4-0x0ca5] has been reserved
[    0.114428] system 00:00: [io  0x02f8-0x02ff] has been reserved
[    0.114494] system 00:00: [mem 0xf4000000-0xf7ffffff] has been reserved
[    0.114559] system 00:00: [mem 0xfe000000-0xfebfffff] has been reserved
[    0.114628] system 00:00: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.114696] pnp 00:01: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.114716] pnp 00:02: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.114733] pnp 00:03: Plug and Play ACPI device, IDs PNP0f13 PNP0f0e (active)
[    0.114878] pnp: PnP ACPI: found 4 devices
[    0.120883] clocksource: acpi_pm: mask: 0xffffff max_cycles: 0xffffff, max_idle_ns: 2085701024 ns
[    0.121016] pci 0000:00:1c.4: BAR 14: assigned [mem 0xf8000000-0xf80fffff]
[    0.121084] pci 0000:00:01.0: PCI bridge to [bus 07]
[    0.121158] pci 0000:00:06.0: PCI bridge to [bus 02]
[    0.121229] pci 0000:00:1c.0: PCI bridge to [bus 0d]
[    0.121302] pci 0000:03:00.0: BAR 6: assigned [mem 0xf8000000-0xf801ffff pref]
[    0.121380] pci 0000:03:00.1: BAR 6: assigned [mem 0xf8020000-0xf803ffff pref]
[    0.121457] pci 0000:00:1c.4: PCI bridge to [bus 03]
[    0.121524] pci 0000:00:1c.4:   bridge window [mem 0xf8000000-0xf80fffff]
[    0.121591] pci 0000:00:1c.4:   bridge window [mem 0xfab00000-0xfabfffff 64bit pref]
[    0.121675] pci 0000:00:1c.6: PCI bridge to [bus 04]
[    0.121741] pci 0000:00:1c.6:   bridge window [mem 0xfbf00000-0xfbffffff]
[    0.121813] pci 0000:01:00.2: BAR 6: assigned [mem 0xfad00000-0xfad0ffff pref]
[    0.121892] pci 0000:00:1c.7: PCI bridge to [bus 01]
[    0.121955] pci 0000:00:1c.7:   bridge window [io  0x3000-0x3fff]
[    0.122023] pci 0000:00:1c.7:   bridge window [mem 0xfad00000-0xfbefffff]
[    0.122091] pci 0000:00:1c.7:   bridge window [mem 0xf9000000-0xf9ffffff 64bit pref]
[    0.122173] pci 0000:00:1e.0: PCI bridge to [bus 14]
[    0.122244] pci_bus 0000:00: resource 4 [mem 0xf8000000-0xfbffffff window]
[    0.122245] pci_bus 0000:00: resource 5 [io  0x1000-0xffff window]
[    0.122246] pci_bus 0000:00: resource 6 [io  0x0000-0x03af window]
[    0.122247] pci_bus 0000:00: resource 7 [io  0x03e0-0x0cf7 window]
[    0.122248] pci_bus 0000:00: resource 8 [io  0x0d00-0x0fff window]
[    0.122248] pci_bus 0000:00: resource 9 [mem 0xfed00000-0xfed44fff window]
[    0.122249] pci_bus 0000:00: resource 10 [io  0x03b0-0x03bb window]
[    0.122250] pci_bus 0000:00: resource 11 [io  0x03c0-0x03df window]
[    0.122251] pci_bus 0000:00: resource 12 [mem 0x000a0000-0x000bffff window]
[    0.122252] pci_bus 0000:03: resource 1 [mem 0xf8000000-0xf80fffff]
[    0.122253] pci_bus 0000:03: resource 2 [mem 0xfab00000-0xfabfffff 64bit pref]
[    0.122254] pci_bus 0000:04: resource 1 [mem 0xfbf00000-0xfbffffff]
[    0.122255] pci_bus 0000:01: resource 0 [io  0x3000-0x3fff]
[    0.122256] pci_bus 0000:01: resource 1 [mem 0xfad00000-0xfbefffff]
[    0.122256] pci_bus 0000:01: resource 2 [mem 0xf9000000-0xf9ffffff 64bit pref]
[    0.122258] pci_bus 0000:14: resource 4 [mem 0xf8000000-0xfbffffff window]
[    0.122258] pci_bus 0000:14: resource 5 [io  0x1000-0xffff window]
[    0.122259] pci_bus 0000:14: resource 6 [io  0x0000-0x03af window]
[    0.122260] pci_bus 0000:14: resource 7 [io  0x03e0-0x0cf7 window]
[    0.122261] pci_bus 0000:14: resource 8 [io  0x0d00-0x0fff window]
[    0.122262] pci_bus 0000:14: resource 9 [mem 0xfed00000-0xfed44fff window]
[    0.122262] pci_bus 0000:14: resource 10 [io  0x03b0-0x03bb window]
[    0.122263] pci_bus 0000:14: resource 11 [io  0x03c0-0x03df window]
[    0.122264] pci_bus 0000:14: resource 12 [mem 0x000a0000-0x000bffff window]
[    0.122331] NET: Registered protocol family 2
[    0.122595] TCP established hash table entries: 32768 (order: 6, 262144 bytes)
[    0.122738] TCP bind hash table entries: 32768 (order: 7, 524288 bytes)
[    0.122907] TCP: Hash tables configured (established 32768 bind 32768)
[    0.123055] UDP hash table entries: 2048 (order: 4, 65536 bytes)
[    0.123135] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
[    0.123327] NET: Registered protocol family 1
[    0.160331] pci 0000:01:00.1: Video device with shadowed ROM at [mem 0x000c0000-0x000dffff]
[    0.160588] PCI: CLS 64 bytes, default 64
[    0.160617] Unpacking initramfs...
[    0.733920] Freeing initrd memory: 56520K
[    0.734014] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.734082] software IO TLB: mapped [mem 0xedde4000-0xf1de4000] (64MB)
[    0.734492] Scanning for low memory corruption every 60 seconds
[    0.743168] Initialise system trusted keyrings
[    0.743241] Key type blacklist registered
[    0.743328] workingset: timestamp_bits=36 max_order=20 bucket_order=0
[    0.744170] zbud: loaded
[    0.744670] squashfs: version 4.0 (2009/01/31) Phillip Lougher
[    0.744856] fuse init (API version 7.26)
[    0.746393] Key type asymmetric registered
[    0.746466] Asymmetric key parser 'x509' registered
[    0.746596] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 246)
[    0.746754] io scheduler noop registered
[    0.746824] io scheduler deadline registered
[    0.746938] io scheduler cfq registered (default)
[    0.747995] intel_idle: MWAIT substates: 0x1120
[    0.747996] intel_idle: v0.4.1 model 0x3A
[    0.748161] intel_idle: lapic_timer_reliable_states 0xffffffff
[    0.748218] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    0.748338] ACPI: Power Button [PWRF]
[    0.748686] (NULL device *): hwmon_device_register() is deprecated. Please convert the driver to use hwmon_device_register_with_info().
[    0.748803] thermal LNXTHERM:00: registered as thermal_zone0
[    0.748871] ACPI: Thermal Zone [THM0] (8 C)
[    0.748982] ERST: Error Record Serialization Table (ERST) support is initialized.
[    0.749064] pstore: using zlib compression
[    0.749131] pstore: Registered erst as persistent store backend
[    0.749257] GHES: APEI firmware first mode is enabled by APEI bit and WHEA _OSC.
[    0.749401] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.770235] serial8250: ttyS1 at I/O 0x2f8 (irq = 3, base_baud = 115200) is a 16550A
[    0.772873] Linux agpgart interface v0.103
[    0.778555] loop: module loaded
[    0.778867] libphy: Fixed MDIO Bus: probed
[    0.778938] tun: Universal TUN/TAP device driver, 1.6
[    0.779067] PPP generic driver version 2.4.2
[    0.779204] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.779279] ehci-pci: EHCI PCI platform driver
[    0.779570] ehci-pci 0000:00:1a.0: EHCI Host Controller
[    0.779642] ehci-pci 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    0.779734] ehci-pci 0000:00:1a.0: debug port 2
[    0.783705] ehci-pci 0000:00:1a.0: cache line size of 64 is not supported
[    0.783717] ehci-pci 0000:00:1a.0: irq 21, io mem 0xfacf0000
[    0.796034] ehci-pci 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    0.796157] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    0.796227] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.796308] usb usb1: Product: EHCI Host Controller
[    0.796375] usb usb1: Manufacturer: Linux 4.15.0-76-generic ehci_hcd
[    0.796443] usb usb1: SerialNumber: 0000:00:1a.0
[    0.796596] hub 1-0:1.0: USB hub found
[    0.796666] hub 1-0:1.0: 2 ports detected
[    0.797042] ehci-pci 0000:00:1d.0: EHCI Host Controller
[    0.797114] ehci-pci 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.797204] ehci-pci 0000:00:1d.0: debug port 2
[    0.801161] ehci-pci 0000:00:1d.0: cache line size of 64 is not supported
[    0.801169] ehci-pci 0000:00:1d.0: irq 20, io mem 0xface0000
[    0.816035] ehci-pci 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    0.816143] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    0.816215] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.816296] usb usb2: Product: EHCI Host Controller
[    0.816363] usb usb2: Manufacturer: Linux 4.15.0-76-generic ehci_hcd
[    0.816431] usb usb2: SerialNumber: 0000:00:1d.0
[    0.816635] hub 2-0:1.0: USB hub found
[    0.816705] hub 2-0:1.0: 2 ports detected
[    0.816890] ehci-platform: EHCI generic platform driver
[    0.816982] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.817059] ohci-pci: OHCI PCI platform driver
[    0.817141] ohci-platform: OHCI generic platform driver
[    0.817219] uhci_hcd: USB Universal Host Controller Interface driver
[    0.817442] uhci_hcd 0000:01:00.4: UHCI Host Controller
[    0.817515] uhci_hcd 0000:01:00.4: new USB bus registered, assigned bus number 3
[    0.817612] uhci_hcd 0000:01:00.4: detected 8 ports
[    0.817679] uhci_hcd 0000:01:00.4: port count misdetected? forcing to 2 ports
[    0.817776] uhci_hcd 0000:01:00.4: irq 16, io base 0x00003c00
[    0.817885] usb usb3: New USB device found, idVendor=1d6b, idProduct=0001
[    0.817954] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.818035] usb usb3: Product: UHCI Host Controller
[    0.818102] usb usb3: Manufacturer: Linux 4.15.0-76-generic uhci_hcd
[    0.818171] usb usb3: SerialNumber: 0000:01:00.4
[    0.818361] hub 3-0:1.0: USB hub found
[    0.818430] hub 3-0:1.0: 2 ports detected
[    0.818680] xhci_hcd 0000:04:00.0: Resetting
[    1.132031] usb 1-1: new high-speed USB device number 2 using ehci-pci
[    1.152033] usb 3-1: new full-speed USB device number 2 using uhci_hcd
[    1.152124] usb 2-1: new high-speed USB device number 2 using ehci-pci
[    1.288396] usb 1-1: New USB device found, idVendor=8087, idProduct=0024
[    1.288472] usb 1-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.288889] hub 1-1:1.0: USB hub found
[    1.289137] hub 1-1:1.0: 6 ports detected
[    1.308330] usb 2-1: New USB device found, idVendor=8087, idProduct=0024
[    1.308407] usb 2-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.308737] hub 2-1:1.0: USB hub found
[    1.309014] hub 2-1:1.0: 6 ports detected
[    1.317576] usb 3-1: New USB device found, idVendor=03f0, idProduct=7029
[    1.317652] usb 3-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.317726] usb 3-1: Product: Virtual Keyboard 
[    1.317797] usb 3-1: Manufacturer: BMC
[    1.596032] usb 2-1.3: new high-speed USB device number 3 using ehci-pci
[    1.704365] usb 2-1.3: New USB device found, idVendor=0424, idProduct=2660
[    1.704442] usb 2-1.3: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.704929] hub 2-1.3:1.0: USB hub found
[    1.705119] hub 2-1.3:1.0: 2 ports detected
[    1.756029] tsc: Refined TSC clocksource calibration: 3392.293 MHz
[    1.756174] clocksource: tsc: mask: 0xffffffffffffffff max_cycles: 0x30e5de2a436, max_idle_ns: 440795285127 ns
[    1.852281] xhci_hcd 0000:04:00.0: xHCI Host Controller
[    1.852363] xhci_hcd 0000:04:00.0: new USB bus registered, assigned bus number 4
[    1.857843] xhci_hcd 0000:04:00.0: hcc params 0x014051cf hci version 0x100 quirks 0x0000000000000410
[    1.858268] usb usb4: New USB device found, idVendor=1d6b, idProduct=0002
[    1.858342] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.858427] usb usb4: Product: xHCI Host Controller
[    1.858498] usb usb4: Manufacturer: Linux 4.15.0-76-generic xhci-hcd
[    1.858571] usb usb4: SerialNumber: 0000:04:00.0
[    1.858790] hub 4-0:1.0: USB hub found
[    1.858871] hub 4-0:1.0: 2 ports detected
[    1.859053] xhci_hcd 0000:04:00.0: xHCI Host Controller
[    1.859127] xhci_hcd 0000:04:00.0: new USB bus registered, assigned bus number 5
[    1.859214] xhci_hcd 0000:04:00.0: Host supports USB 3.0  SuperSpeed
[    1.861273] usb usb5: We don't know the algorithms for LPM for this host, disabling LPM.
[    1.861383] usb usb5: New USB device found, idVendor=1d6b, idProduct=0003
[    1.861456] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.861541] usb usb5: Product: xHCI Host Controller
[    1.861612] usb usb5: Manufacturer: Linux 4.15.0-76-generic xhci-hcd
[    1.861685] usb usb5: SerialNumber: 0000:04:00.0
[    1.861884] hub 5-0:1.0: USB hub found
[    1.861965] hub 5-0:1.0: 2 ports detected
[    1.862247] i8042: PNP: PS/2 Controller [PNP0303:KBD,PNP0f0e:PS2M] at 0x60,0x64 irq 1,12
[    1.864188] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.864269] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.864509] mousedev: PS/2 mouse device common for all mice
[    1.864739] rtc_cmos 00:01: RTC can wake from S4
[    1.865024] rtc_cmos 00:01: rtc core: registered rtc_cmos as rtc0
[    1.865130] rtc_cmos 00:01: alarms up to one day, 114 bytes nvram, hpet irqs
[    1.865214] i2c /dev entries driver
[    1.865359] device-mapper: uevent: version 1.0.3
[    1.865594] device-mapper: ioctl: 4.37.0-ioctl (2017-09-20) initialised: [email]dm-devel@redhat.com[/email]
[    1.865706] intel_pstate: Intel P-state driver initializing
[    1.866204] ledtrig-cpu: registered to indicate activity on CPUs
[    1.866721] NET: Registered protocol family 10
[    1.869691] Segment Routing with IPv6
[    1.869775] NET: Registered protocol family 17
[    1.869874] Key type dns_resolver registered
[    1.870127] mce: Using 7 MCE banks
[    1.870208] RAS: Correctable Errors collector initialized.
[    1.870302] microcode: sig=0x306a9, pf=0x2, revision=0x21
[    1.870409] microcode: Microcode Update Driver: v2.2.
[    1.870416] sched_clock: Marking stable (1870406328, 0)->(1852444471, 17961857)
[    1.870712] registered taskstats version 1
[    1.870784] Loading compiled-in X.509 certificates
[    1.872630] Loaded X.509 cert 'Build time autogenerated kernel key: 665cd2b89e03521f57c41865f552ebce30a0c7fb'
[    1.872733] zswap: loaded using pool lzo/zbud
[    1.875090] Key type big_key registered
[    1.875158] Key type trusted registered
[    1.876355] Key type encrypted registered
[    1.876423] AppArmor: AppArmor sha1 policy hashing enabled
[    1.876492] ima: No TPM chip found, activating TPM-bypass! (rc=-19)
[    1.876563] ima: Allocated hash algorithm: sha1
[    1.876640] evm: HMAC attrs: 0x1
[    1.876994]   Magic number: 8:181:633
[    1.877162] rtc_cmos 00:01: setting system clock to 2020-02-18 12:38:13 UTC (1582029493)
[    1.877280] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.877348] EDD information not available.
[    1.878932] Freeing unused kernel image memory: 2428K
[    1.900079] Write protecting the kernel read-only data: 20480k
[    1.900959] Freeing unused kernel image memory: 2008K
[    1.901513] Freeing unused kernel image memory: 1884K
[    1.922958] x86/mm: Checked W+X mappings: passed, no W+X pages found.
[    1.923033] x86/mm: Checking user space page tables
[    1.936262] x86/mm: Checked W+X mappings: passed, no W+X pages found.
[    2.063580] pps_core: LinuxPPS API ver. 1 registered
[    2.063665] pps_core: Software ver. 5.3.6 - Copyright 2005-2007 Rodolfo Giometti <giometti@linux.it>
[    2.066257] PTP clock support registered
[    2.078073] tg3.c:v3.137 (May 11, 2014)
[    2.081562] ahci 0000:00:1f.2: version 3.0
[    2.081962] ahci 0000:00:1f.2: SSS flag set, parallel bus scan disabled
[    2.085808] hidraw: raw HID events driver (C) Jiri Kosina
[    2.092147] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 6 Gbps 0x3f impl SATA mode
[    2.092248] ahci 0000:00:1f.2: flags: 64bit ncq sntf ilck stag pm led clo pmp pio slum part ems apst 
[    2.096492] usbcore: registered new interface driver usbhid
[    2.096583] usbhid: USB HID core driver
[    2.097930] tg3 0000:03:00.0 eth0: Tigon3 [partno(N/A) rev 5720000] (PCI Express) MAC address 00:fd:45:fd:5d:0c
[    2.098023] tg3 0000:03:00.0 eth0: attached PHY is 5720C (10/100/1000Base-T Ethernet) (WireSpeed[1], EEE[1])
[    2.098112] tg3 0000:03:00.0 eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[1] TSOcap[1]
[    2.098198] tg3 0000:03:00.0 eth0: dma_rwctrl[00000001] dma_mask[64-bit]
[    2.116584] tg3 0000:03:00.1 eth1: Tigon3 [partno(N/A) rev 5720000] (PCI Express) MAC address 00:fd:45:fd:5d:0d
[    2.116682] tg3 0000:03:00.1 eth1: attached PHY is 5720C (10/100/1000Base-T Ethernet) (WireSpeed[1], EEE[1])
[    2.116776] tg3 0000:03:00.1 eth1: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[1] TSOcap[1]
[    2.116866] tg3 0000:03:00.1 eth1: dma_rwctrl[00000001] dma_mask[64-bit]
[    2.157642] [TTM] Zone  kernel: Available graphics memory: 1995572 kiB
[    2.157728] [TTM] Initializing pool allocator
[    2.157813] [TTM] Initializing DMA pool allocator
[    2.172353] scsi host0: ahci
[    2.172707] scsi host1: ahci
[    2.172980] scsi host2: ahci
[    2.173243] scsi host3: ahci
[    2.173527] scsi host4: ahci
[    2.173786] scsi host5: ahci
[    2.173959] ata1: SATA max UDMA/133 abar m2048@0xfacd0000 port 0xfacd0100 irq 29
[    2.174056] ata2: SATA max UDMA/133 abar m2048@0xfacd0000 port 0xfacd0180 irq 29
[    2.174152] ata3: SATA max UDMA/133 abar m2048@0xfacd0000 port 0xfacd0200 irq 29
[    2.174246] ata4: SATA max UDMA/133 abar m2048@0xfacd0000 port 0xfacd0280 irq 29
[    2.174343] ata5: SATA max UDMA/133 abar m2048@0xfacd0000 port 0xfacd0300 irq 29
[    2.174438] ata6: SATA max UDMA/133 abar m2048@0xfacd0000 port 0xfacd0380 irq 29
[    2.176150] tg3 0000:03:00.0 eno1: renamed from eth0
[    2.178502] input: BMC Virtual Keyboard  as /devices/pci0000:00/0000:00:1c.7/0000:01:00.4/usb3/3-1/3-1:1.0/0003:03F0:7029.0001/input/input4
[    2.200814] tg3 0000:03:00.1 eno2: renamed from eth1
[    2.201837] fbcon: mgadrmfb (fb0) is primary device
[    2.236193] hid-generic 0003:03F0:7029.0001: input,hidraw0: USB HID v1.01 Keyboard [BMC Virtual Keyboard ] on usb-0000:01:00.4-1/input0
[    2.236453] input: BMC Virtual Keyboard  as /devices/pci0000:00/0000:00:1c.7/0000:01:00.4/usb3/3-1/3-1:1.1/0003:03F0:7029.0002/input/input5
[    2.236633] hid-generic 0003:03F0:7029.0002: input,hidraw1: USB HID v1.01 Mouse [BMC Virtual Keyboard ] on usb-0000:01:00.4-1/input1
[    2.367648] Console: switching to colour frame buffer device 128x48
[    2.399699] mgag200 0000:01:00.1: fb0: mgadrmfb frame buffer device
[    2.420061] [drm] Initialized mgag200 1.0.0 20110418 for 0000:01:00.1 on minor 0
[    2.648038] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.649998] ata1.00: ATA-8: WDC WD15EARS-00MVWB0, 50.0AB50, max UDMA/133
[    2.650064] ata1.00: 2930277168 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
[    2.652902] ata1.00: configured for UDMA/133
[    2.653290] scsi 0:0:0:0: Direct-Access     ATA      WDC WD15EARS-00M AB50 PQ: 0 ANSI: 5
[    2.653799] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.653816] sd 0:0:0:0: [sda] 2930277168 512-byte logical blocks: (1.50 TB/1.36 TiB)
[    2.653960] sd 0:0:0:0: [sda] Write Protect is off
[    2.654010] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.654067] sd 0:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[    2.660021] raid6: sse2x1   gen()  4512 MB/s
[    2.708019] raid6: sse2x1   xor()  3361 MB/s
[    2.718144]  sda: sda1 sda2
[    2.718900] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.756015] raid6: sse2x2   gen()  5528 MB/s
[    2.804006] raid6: sse2x2   xor()  5674 MB/s
[    2.852008] raid6: sse2x4   gen()  8919 MB/s
[    2.900008] raid6: sse2x4   xor()  6182 MB/s
[    2.901031] raid6: using algorithm sse2x4 gen() 8919 MB/s
[    2.902088] raid6: .... xor() 6182 MB/s, rmw enabled
[    2.903140] raid6: using ssse3x2 recovery algorithm
[    2.904247] clocksource: Switched to clocksource tsc
[    2.906561] xor: automatically using best checksumming function   avx       
[    2.908648] async_tx: api initialized (async)
[    3.059854] Btrfs loaded, crc32c=crc32c-intel
[    3.172040] ata2: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    3.174509] ata2.00: ATA-10: WDC WD40EFRX-68N32N0, 82.00A82, max UDMA/133
[    3.175839] ata2.00: 7814037168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    3.177721] ata2.00: configured for UDMA/133
[    3.179302] scsi 1:0:0:0: Direct-Access     ATA      WDC WD40EFRX-68N 0A82 PQ: 0 ANSI: 5
[    3.181007] sd 1:0:0:0: Attached scsi generic sg1 type 0
[    3.181045] sd 1:0:0:0: [sdb] 7814037168 512-byte logical blocks: (4.00 TB/3.64 TiB)
[    3.184768] sd 1:0:0:0: [sdb] 4096-byte physical blocks
[    3.186508] sd 1:0:0:0: [sdb] Write Protect is off
[    3.188022] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    3.188066] sd 1:0:0:0: [sdb] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[    3.223471] EXT4-fs (sda2): recovery complete
[    3.224699] EXT4-fs (sda2): mounted filesystem with ordered data mode. Opts: (null)
[    3.313978] random: fast init done
[    3.660044] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    3.661807] ata3.00: ATA-10: WDC WD40EFRX-68N32N0, 82.00A82, max UDMA/133
[    3.662935] ata3.00: 7814037168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    3.664980] ata3.00: configured for UDMA/133
[    3.666392] scsi 2:0:0:0: Direct-Access     ATA      WDC WD40EFRX-68N 0A82 PQ: 0 ANSI: 5
[    3.667785] sd 2:0:0:0: Attached scsi generic sg2 type 0
[    3.667803] sd 2:0:0:0: [sdc] 7814037168 512-byte logical blocks: (4.00 TB/3.64 TiB)
[    3.669980] sd 2:0:0:0: [sdc] 4096-byte physical blocks
[    3.671080] sd 2:0:0:0: [sdc] Write Protect is off
[    3.672149] sd 2:0:0:0: [sdc] Mode Sense: 00 3a 00 00
[    3.672179] sd 2:0:0:0: [sdc] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[    3.738253]  sdb: sdb1
[    3.739954] sd 1:0:0:0: [sdb] Attached SCSI disk
[    3.982427] ata4: SATA link down (SStatus 0 SControl 300)
[    4.219751]  sdc: sdc1
[    4.221504] sd 2:0:0:0: [sdc] Attached SCSI disk
[    4.298476] ata5: SATA link down (SStatus 0 SControl 300)
[    4.614430] ata6: SATA link down (SStatus 0 SControl 300)
[    5.132391] random: crng init done
[    5.280564] ip_tables: (C) 2000-2006 Netfilter Core Team
[    5.364733] systemd[1]: systemd 237 running in system mode. (+PAM +AUDIT +SELINUX +IMA +APPARMOR +SMACK +SYSVINIT +UTMP +LIBCRYPTSETUP +GCRYPT +GNUTLS +ACL +XZ +LZ4 +SECCOMP +BLKID +ELFUTILS +KMOD -IDN2 +IDN -PCRE2 default-hierarchy=hybrid)
[    5.384204] systemd[1]: Detected architecture x86-64.
[    5.490861] systemd[1]: Set hostname to <ubunteserver>.
[    5.786161] systemd-fstab-generator[375]: Mount point 0 is not a valid path, ignoring.
[    8.562399] systemd[1]: Created slice System Slice.
[    8.610623] systemd[1]: Listening on fsck to fsckd communication Socket.
[    8.660085] systemd[1]: Listening on udev Kernel Socket.
[    8.708356] systemd[1]: Listening on /dev/initctl Compatibility Named Pipe.
[    8.756828] systemd[1]: Listening on udev Control Socket.
[    8.805001] systemd[1]: Started Forward Password Requests to Wall Directory Watch.
[    8.852645] systemd[1]: Listening on Journal Socket (/dev/log).
[    9.904871] EXT4-fs (sda2): Couldn't remount RDWR because of unprocessed orphan inode list.  Please umount/remount instead
[   10.113040] Loading iSCSI transport class v2.0-870.
[   10.329173] systemd-journald[406]: Received request to flush runtime journal from PID 1
[   10.403356] iscsi: registered transport (tcp)
[   11.060295] iscsi: registered transport (iser)
[   12.645173] ipmi message handler version 39.2
[   12.677131] ipmi device interface
[   12.779101] power_meter ACPI000D:00: Found ACPI power meter.
[   12.779123] power_meter ACPI000D:00: Ignoring unsafe software power cap!
[   12.779125] power_meter ACPI000D:00: hwmon_device_register() is deprecated. Please convert the driver to use hwmon_device_register_with_info().
[   12.780058] IPMI System Interface driver.
[   12.780077] ipmi_si dmi-ipmi-si.0: ipmi_platform: probing via SMBIOS
[   12.780080] ipmi_si: SMBIOS: io 0xca2 regsize 1 spacing 1 irq 0
[   12.780081] ipmi_si: Adding SMBIOS-specified kcs state machine
[   12.780105] ipmi_si IPI0001:00: ipmi_platform: probing via ACPI
[   12.780129] ipmi_si IPI0001:00: [io  0x0ca2-0x0ca3] regsize 1 spacing 1 irq 0
[   12.780131] ipmi_si dmi-ipmi-si.0: Removing SMBIOS-specified kcs state machine in favor of ACPI
[   12.780132] ipmi_si: Adding ACPI-specified kcs state machine
[   12.780157] ipmi_platform: probing via SPMI
[   12.780158] ipmi_si: SPMI: io 0xca2 regsize 2 spacing 2 irq 0
[   12.780159] (NULL device *): SPMI-specified kcs state machine: duplicate
[   12.780179] ipmi_si: Trying ACPI-specified kcs state machine at i/o address 0xca2, slave address 0x20, irq 0
[   12.908355] ACPI Warning: SystemIO range 0x0000000000000928-0x000000000000092F conflicts with OpRegion 0x0000000000000920-0x000000000000092F (\SGPE) (20170831/utaddress-247)
[   12.908360] ACPI Warning: SystemIO range 0x0000000000000928-0x000000000000092F conflicts with OpRegion 0x0000000000000920-0x000000000000092F (\SGPE) (20170831/utaddress-247)
[   12.908363] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   12.908387] lpc_ich: Resource conflict(s) found affecting gpio_ich
[   12.920789] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   13.355091] ipmi_si IPI0001:00: Found new BMC (man_id: 0x00000b, prod_id: 0x2000, dev_id: 0x13)
[   13.417709] ipmi_si IPI0001:00: IPMI kcs interface initialized
[   13.446102] IPMI SSIF Interface driver
[   13.481214] RAPL PMU: API unit is 2^-32 Joules, 3 fixed counters, 163840 ms ovfl timer
[   13.481216] RAPL PMU: hw unit of domain pp0-core 2^-16 Joules
[   13.481217] RAPL PMU: hw unit of domain package 2^-16 Joules
[   13.481218] RAPL PMU: hw unit of domain pp1-gpu 2^-16 Joules
[   14.040294] gpio_ich: GPIO from 436 to 511 on gpio_ich
[   14.620151] intel_rapl: Found RAPL domain package
[   14.620154] intel_rapl: Found RAPL domain core
[   16.552457] md127: detected capacity change from 0 to 8001569161216
[   18.209818] EXT4-fs (md127): mounted filesystem with ordered data mode. Opts: (null)
[   20.205382] audit: type=1400 audit(1582029511.823:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/lxc-start" pid=880 comm="apparmor_parser"
[   20.207187] audit: type=1400 audit(1582029511.823:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/man" pid=881 comm="apparmor_parser"
[   20.207196] audit: type=1400 audit(1582029511.823:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="man_filter" pid=881 comm="apparmor_parser"
[   20.207202] audit: type=1400 audit(1582029511.823:5): apparmor="STATUS" operation="profile_load" profile="unconfined" name="man_groff" pid=881 comm="apparmor_parser"
[   20.209224] audit: type=1400 audit(1582029511.827:6): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=879 comm="apparmor_parser"
[   20.209231] audit: type=1400 audit(1582029511.827:7): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=879 comm="apparmor_parser"
[   20.209235] audit: type=1400 audit(1582029511.827:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-helper" pid=879 comm="apparmor_parser"
[   20.209240] audit: type=1400 audit(1582029511.827:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=879 comm="apparmor_parser"
[   20.211037] audit: type=1400 audit(1582029511.827:10): apparmor="STATUS" operation="profile_load" profile="unconfined" name="lxc-container-default" pid=878 comm="apparmor_parser"
[   20.211048] audit: type=1400 audit(1582029511.827:11): apparmor="STATUS" operation="profile_load" profile="unconfined" name="lxc-container-default-cgns" pid=878 comm="apparmor_parser"
[   23.477659] IPv6: ADDRCONF(NETDEV_UP): eno2: link is not ready
[   23.615200] IPv6: ADDRCONF(NETDEV_UP): eno1: link is not ready
[   27.085266] tg3 0000:03:00.0 eno1: Link is up at 1000 Mbps, full duplex
[   27.085276] tg3 0000:03:00.0 eno1: Flow control is on for TX and on for RX
[   27.085281] tg3 0000:03:00.0 eno1: EEE is disabled
[   27.085303] IPv6: ADDRCONF(NETDEV_CHANGE): eno1: link becomes ready
[   32.319485] new mount options do not match the existing superblock, will be ignored
[  316.380013] EXT4-fs (sda2): error count since last fsck: 5
[  316.380014] EXT4-fs (sda2): initial error at time 1581661515: __ext4_get_inode_loc:4642: inode 6684891: block 26738733
[  316.380016] EXT4-fs (sda2): last error at time 1581661521: ext4_journal_check_start:61: inode 6684894: block 26738733
[  499.624093] usb 3-1: USB disconnect, device number 2

---

