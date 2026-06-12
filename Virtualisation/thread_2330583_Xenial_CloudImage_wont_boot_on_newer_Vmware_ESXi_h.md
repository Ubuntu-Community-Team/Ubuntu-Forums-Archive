---
title: "Xenial CloudImage wont boot on newer Vmware ESXi hardware version 11"
date: 2016-07-13
forum: Virtualisation
---

### Post by galballyj on 2016-07-13
I'm running ESXi 6 under vSphere 6 Enterprise Plus utilising most of the ENTPLUS Features.

I have taken the latest Xenial cloud image from:
[https://cloud-images.ubuntu.com/xenial/current/](https://cloud-images.ubuntu.com/xenial/current/)

Converted the VMDK to ESXi format with vmkfstools, set PW on ubuntu user, removed cloud-init and generally just got everything working exactly as i want it (done apt-get update) This all runs fine with the VM configured with vm hardware version 10 and below. (ESXi 5.5 compatible)

If i upgrade the VM Hardware to v11 the machine will no longer boot (see attached screenshot)

I have successfully installed ubuntu 16.04 from the ISO onto a v11 VM without issue and also Ubuntu 16.04 is on the vmware guest OS support matrix as fully supported.

presumably there's *something* inside this cloud image that doesnt understand the vm hardware version, but does anyone know what?

[IMG]http://img.photobucket.com/albums/0603/GalballyJ/Various%20Stuff/Capture.jpg[/IMG]

---

### Post by galballyj on 2016-07-13
interesting observation, with the machine stuck here the CPU is pegged @ 100%

currently configured with 1x vCPU, 1GB RAM, LSI logic Parallel with 10GB disk on SCSI 0:0

---

### Post by galballyj on 2016-07-13
Kern.log from a WORKING Boot with v10 hardware below.

```
Jul 13 11:37:01 ubuntu kernel: [    0.000000] Initializing cgroup subsys cpusetJul 13 11:37:01 ubuntu kernel: [    0.000000] Initializing cgroup subsys cpu
Jul 13 11:37:01 ubuntu kernel: [    0.000000] Initializing cgroup subsys cpuacct
Jul 13 11:37:01 ubuntu kernel: [    0.000000] Linux version 4.4.0-28-generic (buildd@lcy01-13) (gcc version 5.3.1 20160413 (Ubuntu 5.3.1-14ubuntu2.1) ) #47-Ubuntu SMP Fri Jun 24 10:09:13 UTC 2016 (Ubuntu 4.4.0-28.47-generic 4.4.13)
Jul 13 11:37:01 ubuntu kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-4.4.0-28-generic root=LABEL=cloudimg-rootfs ro console=tty1 console=ttyS0
Jul 13 11:37:01 ubuntu kernel: [    0.000000] KERNEL supported cpus:
Jul 13 11:37:01 ubuntu kernel: [    0.000000]   Intel GenuineIntel
Jul 13 11:37:01 ubuntu kernel: [    0.000000]   AMD AuthenticAMD
Jul 13 11:37:01 ubuntu kernel: [    0.000000]   Centaur CentaurHauls
Jul 13 11:37:01 ubuntu kernel: [    0.000000] Disabled fast string operations
Jul 13 11:37:01 ubuntu kernel: [    0.000000] x86/fpu: xstate_offset[2]:  576, xstate_sizes[2]:  256
Jul 13 11:37:01 ubuntu kernel: [    0.000000] x86/fpu: Supporting XSAVE feature 0x01: 'x87 floating point registers'
Jul 13 11:37:01 ubuntu kernel: [    0.000000] x86/fpu: Supporting XSAVE feature 0x02: 'SSE registers'
Jul 13 11:37:01 ubuntu kernel: [    0.000000] x86/fpu: Supporting XSAVE feature 0x04: 'AVX registers'
Jul 13 11:37:01 ubuntu kernel: [    0.000000] x86/fpu: Enabled xstate features 0x7, context size is 832 bytes, using 'standard' format.
Jul 13 11:37:01 ubuntu kernel: [    0.000000] x86/fpu: Using 'lazy' FPU context switches.
Jul 13 11:37:01 ubuntu kernel: [    0.000000] e820: BIOS-provided physical RAM map:
Jul 13 11:37:01 ubuntu kernel: [    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009f7ff] usable
Jul 13 11:37:01 ubuntu kernel: [    0.000000] BIOS-e820: [mem 0x000000000009f800-0x000000000009ffff] reserved
Jul 13 11:37:01 ubuntu kernel: [    0.000000] BIOS-e820: [mem 0x00000000000dc000-0x00000000000fffff] reserved
Jul 13 11:37:01 ubuntu kernel: [    0.000000] BIOS-e820: [mem 0x0000000000100000-0x000000003feeffff] usable
Jul 13 11:37:01 ubuntu kernel: [    0.000000] BIOS-e820: [mem 0x000000003fef0000-0x000000003fefefff] ACPI data
Jul 13 11:37:01 ubuntu kernel: [    0.000000] BIOS-e820: [mem 0x000000003feff000-0x000000003fefffff] ACPI NVS
Jul 13 11:37:01 ubuntu kernel: [    0.000000] BIOS-e820: [mem 0x000000003ff00000-0x000000003fffffff] usable
Jul 13 11:37:01 ubuntu kernel: [    0.000000] BIOS-e820: [mem 0x00000000f0000000-0x00000000f7ffffff] reserved
Jul 13 11:37:01 ubuntu kernel: [    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec0ffff] reserved
Jul 13 11:37:01 ubuntu kernel: [    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
Jul 13 11:37:01 ubuntu kernel: [    0.000000] BIOS-e820: [mem 0x00000000fffe0000-0x00000000ffffffff] reserved
Jul 13 11:37:01 ubuntu kernel: [    0.000000] NX (Execute Disable) protection: active
Jul 13 11:37:01 ubuntu kernel: [    0.000000] SMBIOS 2.4 present.
Jul 13 11:37:01 ubuntu kernel: [    0.000000] DMI: VMware, Inc. VMware Virtual Platform/440BX Desktop Reference Platform, BIOS 6.00 09/21/2015
Jul 13 11:37:01 ubuntu kernel: [    0.000000] Hypervisor detected: VMware
Jul 13 11:37:01 ubuntu kernel: [    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
Jul 13 11:37:01 ubuntu kernel: [    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
Jul 13 11:37:01 ubuntu kernel: [    0.000000] e820: last_pfn = 0x40000 max_arch_pfn = 0x400000000
Jul 13 11:37:01 ubuntu kernel: [    0.000000] MTRR default type: uncachable
Jul 13 11:37:01 ubuntu kernel: [    0.000000] MTRR fixed ranges enabled:
Jul 13 11:37:01 ubuntu kernel: [    0.000000]   00000-9FFFF write-back
Jul 13 11:37:01 ubuntu kernel: [    0.000000]   A0000-BFFFF uncachable
Jul 13 11:37:01 ubuntu kernel: [    0.000000]   C0000-CBFFF write-protect
Jul 13 11:37:01 ubuntu kernel: [    0.000000]   CC000-EFFFF uncachable
Jul 13 11:37:01 ubuntu kernel: [    0.000000]   F0000-FFFFF write-protect
Jul 13 11:37:01 ubuntu kernel: [    0.000000] MTRR variable ranges enabled:
Jul 13 11:37:01 ubuntu kernel: [    0.000000]   0 base 0000000000 mask FFC0000000 write-back
Jul 13 11:37:01 ubuntu kernel: [    0.000000]   1 disabled
Jul 13 11:37:01 ubuntu kernel: [    0.000000]   2 disabled
Jul 13 11:37:01 ubuntu kernel: [    0.000000]   3 disabled
Jul 13 11:37:01 ubuntu kernel: [    0.000000]   4 disabled
Jul 13 11:37:01 ubuntu kernel: [    0.000000]   5 disabled
Jul 13 11:37:01 ubuntu kernel: [    0.000000]   6 disabled
Jul 13 11:37:01 ubuntu kernel: [    0.000000]   7 disabled
Jul 13 11:37:01 ubuntu kernel: [    0.000000] x86/PAT: Configuration [0-7]: WB  WC  UC- UC  WB  WC  UC- WT  
Jul 13 11:37:01 ubuntu kernel: [    0.000000] found SMP MP-table at [mem 0x000f6b30-0x000f6b3f] mapped at [ffff8800000f6b30]
Jul 13 11:37:01 ubuntu kernel: [    0.000000] Scanning 1 areas for low memory corruption
Jul 13 11:37:01 ubuntu kernel: [    0.000000] Base memory trampoline at [ffff880000099000] 99000 size 24576
Jul 13 11:37:01 ubuntu kernel: [    0.000000] BRK [0x02200000, 0x02200fff] PGTABLE
Jul 13 11:37:01 ubuntu kernel: [    0.000000] BRK [0x02201000, 0x02201fff] PGTABLE
Jul 13 11:37:01 ubuntu kernel: [    0.000000] BRK [0x02202000, 0x02202fff] PGTABLE
Jul 13 11:37:01 ubuntu kernel: [    0.000000] BRK [0x02203000, 0x02203fff] PGTABLE
Jul 13 11:37:01 ubuntu kernel: [    0.000000] RAMDISK: [mem 0x371b0000-0x378cffff]
Jul 13 11:37:01 ubuntu kernel: [    0.000000] ACPI: Early table checksum verification disabled
Jul 13 11:37:01 ubuntu kernel: [    0.000000] ACPI: RSDP 0x00000000000F6AC0 000024 (v02 PTLTD )
Jul 13 11:37:01 ubuntu kernel: [    0.000000] ACPI: XSDT 0x000000003FEF114C 00005C (v01 INTEL  440BX    06040000 VMW  01324272)
Jul 13 11:37:01 ubuntu kernel: [    0.000000] ACPI: FACP 0x000000003FEFEE73 0000F4 (v04 INTEL  440BX    06040000 PTL  000F4240)
Jul 13 11:37:01 ubuntu kernel: [    0.000000] ACPI: DSDT 0x000000003FEF13B4 00DABF (v01 PTLTD  Custom   06040000 MSFT 03000001)
Jul 13 11:37:01 ubuntu kernel: [    0.000000] ACPI: FACS 0x000000003FEFFFC0 000040
Jul 13 11:37:01 ubuntu kernel: [    0.000000] ACPI: FACS 0x000000003FEFFFC0 000040
Jul 13 11:37:01 ubuntu kernel: [    0.000000] ACPI: BOOT 0x000000003FEF138C 000028 (v01 PTLTD  $SBFTBL$ 06040000  LTP 00000001)
Jul 13 11:37:01 ubuntu kernel: [    0.000000] ACPI: APIC 0x000000003FEF133C 000050 (v01 PTLTD  ? APIC   06040000  LTP 00000000)
Jul 13 11:37:01 ubuntu kernel: [    0.000000] ACPI: MCFG 0x000000003FEF1300 00003C (v01 PTLTD  $PCITBL$ 06040000  LTP 00000001)
Jul 13 11:37:01 ubuntu kernel: [    0.000000] ACPI: SRAT 0x000000003FEF1248 0000B8 (v02 VMWARE MEMPLUG  06040000 VMW  00000001)
Jul 13 11:37:01 ubuntu kernel: [    0.000000] ACPI: HPET 0x000000003FEF1210 000038 (v01 VMWARE VMW HPET 06040000 VMW  00000001)
Jul 13 11:37:01 ubuntu kernel: [    0.000000] ACPI: WAET 0x000000003FEF11E8 000028 (v01 VMWARE VMW WAET 06040000 VMW  00000001)
Jul 13 11:37:01 ubuntu kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Jul 13 11:37:01 ubuntu kernel: [    0.000000] SRAT: PXM 0 -> APIC 0x00 -> Node 0
Jul 13 11:37:01 ubuntu kernel: [    0.000000] SRAT: Node 0 PXM 0 [mem 0x00000000-0x0009ffff]
Jul 13 11:37:01 ubuntu kernel: [    0.000000] SRAT: Node 0 PXM 0 [mem 0x00100000-0x0fffffff]
Jul 13 11:37:01 ubuntu kernel: [    0.000000] SRAT: Node 0 PXM 0 [mem 0x10000000-0x3fffffff]
Jul 13 11:37:01 ubuntu kernel: [    0.000000] NUMA: Node 0 [mem 0x00000000-0x0009ffff] + [mem 0x00100000-0x0fffffff] -> [mem 0x00000000-0x0fffffff]
Jul 13 11:37:01 ubuntu kernel: [    0.000000] NUMA: Node 0 [mem 0x00000000-0x0fffffff] + [mem 0x10000000-0x3fffffff] -> [mem 0x00000000-0x3fffffff]
Jul 13 11:37:01 ubuntu kernel: [    0.000000] NODE_DATA(0) allocated [mem 0x3fffb000-0x3fffffff]
Jul 13 11:37:01 ubuntu kernel: [    0.000000] Zone ranges:
Jul 13 11:37:01 ubuntu kernel: [    0.000000]   DMA      [mem 0x0000000000001000-0x0000000000ffffff]
Jul 13 11:37:01 ubuntu kernel: [    0.000000]   DMA32    [mem 0x0000000001000000-0x000000003fffffff]
Jul 13 11:37:01 ubuntu kernel: [    0.000000]   Normal   empty
Jul 13 11:37:01 ubuntu kernel: [    0.000000]   Device   empty
Jul 13 11:37:01 ubuntu kernel: [    0.000000] Movable zone start for each node
Jul 13 11:37:01 ubuntu kernel: [    0.000000] Early memory node ranges
Jul 13 11:37:01 ubuntu kernel: [    0.000000]   node   0: [mem 0x0000000000001000-0x000000000009efff]
Jul 13 11:37:01 ubuntu kernel: [    0.000000]   node   0: [mem 0x0000000000100000-0x000000003feeffff]
Jul 13 11:37:01 ubuntu kernel: [    0.000000]   node   0: [mem 0x000000003ff00000-0x000000003fffffff]
Jul 13 11:37:01 ubuntu kernel: [    0.000000] Initmem setup node 0 [mem 0x0000000000001000-0x000000003fffffff]
Jul 13 11:37:01 ubuntu kernel: [    0.000000] On node 0 totalpages: 262030
Jul 13 11:37:01 ubuntu kernel: [    0.000000]   DMA zone: 64 pages used for memmap
Jul 13 11:37:01 ubuntu kernel: [    0.000000]   DMA zone: 21 pages reserved
Jul 13 11:37:01 ubuntu kernel: [    0.000000]   DMA zone: 3998 pages, LIFO batch:0
Jul 13 11:37:01 ubuntu kernel: [    0.000000]   DMA32 zone: 4032 pages used for memmap
Jul 13 11:37:01 ubuntu kernel: [    0.000000]   DMA32 zone: 258032 pages, LIFO batch:31
Jul 13 11:37:01 ubuntu kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
Jul 13 11:37:01 ubuntu kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Jul 13 11:37:01 ubuntu kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Jul 13 11:37:01 ubuntu kernel: [    0.000000] IOAPIC[0]: apic_id 1, version 17, address 0xfec00000, GSI 0-23
Jul 13 11:37:01 ubuntu kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
Jul 13 11:37:01 ubuntu kernel: [    0.000000] ACPI: IRQ0 used by override.
Jul 13 11:37:01 ubuntu kernel: [    0.000000] ACPI: IRQ9 used by override.
Jul 13 11:37:01 ubuntu kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Jul 13 11:37:01 ubuntu kernel: [    0.000000] ACPI: HPET id: 0x8086af01 base: 0xfed00000
Jul 13 11:37:01 ubuntu kernel: [    0.000000] smpboot: Allowing 1 CPUs, 0 hotplug CPUs
Jul 13 11:37:01 ubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x00000000-0x00000fff]
Jul 13 11:37:01 ubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009f000-0x0009ffff]
Jul 13 11:37:01 ubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dbfff]
Jul 13 11:37:01 ubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000dc000-0x000fffff]
Jul 13 11:37:01 ubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x3fef0000-0x3fefefff]
Jul 13 11:37:01 ubuntu kernel: [    0.000000] PM: Registered nosave memory: [mem 0x3feff000-0x3fefffff]
Jul 13 11:37:01 ubuntu kernel: [    0.000000] e820: [mem 0x40000000-0xefffffff] available for PCI devices
Jul 13 11:37:01 ubuntu kernel: [    0.000000] Booting paravirtualized kernel on bare hardware
Jul 13 11:37:01 ubuntu kernel: [    0.000000] clocksource: refined-jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645519600211568 ns
Jul 13 11:37:01 ubuntu kernel: [    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:1 nr_node_ids:1
Jul 13 11:37:01 ubuntu kernel: [    0.000000] PERCPU: Embedded 33 pages/cpu @ffff88003fc00000 s98008 r8192 d28968 u2097152
Jul 13 11:37:01 ubuntu kernel: [    0.000000] pcpu-alloc: s98008 r8192 d28968 u2097152 alloc=1*2097152
Jul 13 11:37:01 ubuntu kernel: [    0.000000] pcpu-alloc: [0] 0 
Jul 13 11:37:01 ubuntu kernel: [    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 257913
Jul 13 11:37:01 ubuntu kernel: [    0.000000] Policy zone: DMA32
Jul 13 11:37:01 ubuntu kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.4.0-28-generic root=LABEL=cloudimg-rootfs ro console=tty1 console=ttyS0
Jul 13 11:37:01 ubuntu kernel: [    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
Jul 13 11:37:01 ubuntu kernel: [    0.000000] Calgary: detecting Calgary via BIOS EBDA area
Jul 13 11:37:01 ubuntu kernel: [    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
Jul 13 11:37:01 ubuntu kernel: [    0.000000] Memory: 1005500K/1048120K available (8368K kernel code, 1280K rwdata, 3928K rodata, 1480K init, 1292K bss, 42620K reserved, 0K cma-reserved)
Jul 13 11:37:01 ubuntu kernel: [    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
Jul 13 11:37:01 ubuntu kernel: [    0.000000] Hierarchical RCU implementation.
Jul 13 11:37:01 ubuntu kernel: [    0.000000]     Build-time adjustment of leaf fanout to 64.
Jul 13 11:37:01 ubuntu kernel: [    0.000000]     RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=1.
Jul 13 11:37:01 ubuntu kernel: [    0.000000] RCU: Adjusting geometry for rcu_fanout_leaf=64, nr_cpu_ids=1
Jul 13 11:37:01 ubuntu kernel: [    0.000000] NR_IRQS:16640 nr_irqs:256 16
Jul 13 11:37:01 ubuntu kernel: [    0.000000] Console: colour VGA+ 80x25
Jul 13 11:37:01 ubuntu kernel: [    0.000000] console [tty1] enabled
Jul 13 11:37:01 ubuntu kernel: [    0.000000] console [ttyS0] enabled
Jul 13 11:37:01 ubuntu kernel: [    0.000000] clocksource: hpet: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 133484882848 ns
Jul 13 11:37:01 ubuntu kernel: [    0.000000] hpet clockevent registered
Jul 13 11:37:01 ubuntu kernel: [    0.000000] TSC freq read from hypervisor : 2600.000 MHz
Jul 13 11:37:01 ubuntu kernel: [    0.000000] tsc: Detected 2600.000 MHz processor
Jul 13 11:37:01 ubuntu kernel: [    0.000090] Calibrating delay loop (skipped) preset value.. 5200.00 BogoMIPS (lpj=10400000)
Jul 13 11:37:01 ubuntu kernel: [    0.001331] pid_max: default: 32768 minimum: 301
Jul 13 11:37:01 ubuntu kernel: [    0.002003] ACPI: Core revision 20150930
Jul 13 11:37:01 ubuntu kernel: [    0.010020] ACPI: 1 ACPI AML tables successfully acquired and loaded
Jul 13 11:37:01 ubuntu kernel: [    0.011057] Security Framework initialized
Jul 13 11:37:01 ubuntu kernel: [    0.011660] Yama: becoming mindful.
Jul 13 11:37:01 ubuntu kernel: [    0.012194] AppArmor: AppArmor initialized
Jul 13 11:37:01 ubuntu kernel: [    0.012864] Dentry cache hash table entries: 131072 (order: 8, 1048576 bytes)
Jul 13 11:37:01 ubuntu kernel: [    0.014018] Inode-cache hash table entries: 65536 (order: 7, 524288 bytes)
Jul 13 11:37:01 ubuntu kernel: [    0.015066] Mount-cache hash table entries: 2048 (order: 2, 16384 bytes)
Jul 13 11:37:01 ubuntu kernel: [    0.016009] Mountpoint-cache hash table entries: 2048 (order: 2, 16384 bytes)
Jul 13 11:37:01 ubuntu kernel: [    0.017169] Initializing cgroup subsys io
Jul 13 11:37:01 ubuntu kernel: [    0.017769] Initializing cgroup subsys memory
Jul 13 11:37:01 ubuntu kernel: [    0.018410] Initializing cgroup subsys devices
Jul 13 11:37:01 ubuntu kernel: [    0.019071] Initializing cgroup subsys freezer
Jul 13 11:37:01 ubuntu kernel: [    0.019720] Initializing cgroup subsys net_cls
Jul 13 11:37:01 ubuntu kernel: [    0.020368] Initializing cgroup subsys perf_event
Jul 13 11:37:01 ubuntu kernel: [    0.021055] Initializing cgroup subsys net_prio
Jul 13 11:37:01 ubuntu kernel: [    0.021714] Initializing cgroup subsys hugetlb
Jul 13 11:37:01 ubuntu kernel: [    0.022397] Initializing cgroup subsys pids
Jul 13 11:37:01 ubuntu kernel: [    0.023096] Disabled fast string operations
Jul 13 11:37:01 ubuntu kernel: [    0.023714] CPU: Physical Processor ID: 0
Jul 13 11:37:01 ubuntu kernel: [    0.024312] ENERGY_PERF_BIAS: Set to 'normal', was 'performance'
Jul 13 11:37:01 ubuntu kernel: [    0.025161] ENERGY_PERF_BIAS: View and update with x86_energy_perf_policy(8)
Jul 13 11:37:01 ubuntu kernel: [    0.026144] mce: CPU supports 0 MCE banks
Jul 13 11:37:01 ubuntu kernel: [    0.026763] Last level iTLB entries: 4KB 512, 2MB 8, 4MB 8
Jul 13 11:37:01 ubuntu kernel: [    0.027551] Last level dTLB entries: 4KB 512, 2MB 32, 4MB 32, 1GB 0
Jul 13 11:37:01 ubuntu kernel: [    0.039352] Freeing SMP alternatives memory: 28K (ffffffff820b4000 - ffffffff820bb000)
Jul 13 11:37:01 ubuntu kernel: [    0.049335] ftrace: allocating 31920 entries in 125 pages
Jul 13 11:37:01 ubuntu kernel: [    0.076350] smpboot: Max logical packages: 1
Jul 13 11:37:01 ubuntu kernel: [    0.076983] smpboot: APIC(0) Converting physical 0 to logical package 0
Jul 13 11:37:01 ubuntu kernel: [    0.077988] x2apic: IRQ remapping doesn't support X2APIC mode
Jul 13 11:37:01 ubuntu kernel: [    0.079311] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Jul 13 11:37:01 ubuntu kernel: [    0.226553] smpboot: CPU0: Intel(R) Xeon(R) CPU E5-2670 0 @ 2.60GHz (family: 0x6, model: 0x2d, stepping: 0x2)
Jul 13 11:37:01 ubuntu kernel: [    0.228081] Performance Events: 16-deep LBR, SandyBridge events, core PMU driver.
Jul 13 11:37:01 ubuntu kernel: [    0.229289] core: PEBS disabled due to CPU errata, please upgrade microcode
Jul 13 11:37:01 ubuntu kernel: [    0.230268] core: CPUID marked event: 'cpu cycles' unavailable
Jul 13 11:37:01 ubuntu kernel: [    0.231099] core: CPUID marked event: 'instructions' unavailable
Jul 13 11:37:01 ubuntu kernel: [    0.231945] core: CPUID marked event: 'bus cycles' unavailable
Jul 13 11:37:01 ubuntu kernel: [    0.232772] core: CPUID marked event: 'cache references' unavailable
Jul 13 11:37:01 ubuntu kernel: [    0.233666] core: CPUID marked event: 'cache misses' unavailable
Jul 13 11:37:01 ubuntu kernel: [    0.234521] core: CPUID marked event: 'branch instructions' unavailable
Jul 13 11:37:01 ubuntu kernel: [    0.235450] core: CPUID marked event: 'branch misses' unavailable
Jul 13 11:37:01 ubuntu kernel: [    0.236312] ... version:                1
Jul 13 11:37:01 ubuntu kernel: [    0.236905] ... bit width:              48
Jul 13 11:37:01 ubuntu kernel: [    0.237509] ... generic registers:      4
Jul 13 11:37:01 ubuntu kernel: [    0.238137] ... value mask:             0000ffffffffffff
Jul 13 11:37:01 ubuntu kernel: [    0.238898] ... max period:             000000007fffffff
Jul 13 11:37:01 ubuntu kernel: [    0.239657] ... fixed-purpose events:   0
Jul 13 11:37:01 ubuntu kernel: [    0.240250] ... event mask:             000000000000000f
Jul 13 11:37:01 ubuntu kernel: [    0.241535] x86: Booted up 1 node, 1 CPUs
Jul 13 11:37:01 ubuntu kernel: [    0.242139] smpboot: Total of 1 processors activated (5200.00 BogoMIPS)
Jul 13 11:37:01 ubuntu kernel: [    0.243225] NMI watchdog: disabled (cpu0): hardware events not enabled
Jul 13 11:37:01 ubuntu kernel: [    0.244146] NMI watchdog: Shutting down hard lockup detector on all cpus
Jul 13 11:37:01 ubuntu kernel: [    0.245118] devtmpfs: initialized
Jul 13 11:37:01 ubuntu kernel: [    0.247171] evm: security.selinux
Jul 13 11:37:01 ubuntu kernel: [    0.247678] evm: security.SMACK64
Jul 13 11:37:01 ubuntu kernel: [    0.248180] evm: security.SMACK64EXEC
Jul 13 11:37:01 ubuntu kernel: [    0.248727] evm: security.SMACK64TRANSMUTE
Jul 13 11:37:01 ubuntu kernel: [    0.249330] evm: security.SMACK64MMAP
Jul 13 11:37:01 ubuntu kernel: [    0.249873] evm: security.ima
Jul 13 11:37:01 ubuntu kernel: [    0.250340] evm: security.capability
Jul 13 11:37:01 ubuntu kernel: [    0.250956] PM: Registering ACPI NVS region [mem 0x3feff000-0x3fefffff] (4096 bytes)
Jul 13 11:37:01 ubuntu kernel: [    0.252115] clocksource: jiffies: mask: 0xffffffff max_cycles: 0xffffffff, max_idle_ns: 7645041785100000 ns
Jul 13 11:37:01 ubuntu kernel: [    0.253579] pinctrl core: initialized pinctrl subsystem
Jul 13 11:37:01 ubuntu kernel: [    0.254494] RTC time: 10:36:55, date: 07/13/16
Jul 13 11:37:01 ubuntu kernel: [    0.255236] NET: Registered protocol family 16
Jul 13 11:37:01 ubuntu kernel: [    0.256023] cpuidle: using governor ladder
Jul 13 11:37:01 ubuntu kernel: [    0.256626] cpuidle: using governor menu
Jul 13 11:37:01 ubuntu kernel: [    0.257200] PCCT header not found.
Jul 13 11:37:01 ubuntu kernel: [    0.257731] Simple Boot Flag at 0x36 set to 0x80
Jul 13 11:37:01 ubuntu kernel: [    0.258435] ACPI: bus type PCI registered
Jul 13 11:37:01 ubuntu kernel: [    0.260152] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
Jul 13 11:37:01 ubuntu kernel: [    0.261621] PCI: MMCONFIG for domain 0000 [bus 00-7f] at [mem 0xf0000000-0xf7ffffff] (base 0xf0000000)
Jul 13 11:37:01 ubuntu kernel: [    0.262935] PCI: MMCONFIG at [mem 0xf0000000-0xf7ffffff] reserved in E820
Jul 13 11:37:01 ubuntu kernel: [    0.263879] PCI: Using configuration type 1 for base access
Jul 13 11:37:01 ubuntu kernel: [    0.264699] core: PMU erratum BJ122, BV98, HSD29 workaround disabled, HT off
Jul 13 11:37:01 ubuntu kernel: [    0.266575] ACPI: Added _OSI(Module Device)
Jul 13 11:37:01 ubuntu kernel: [    0.267220] ACPI: Added _OSI(Processor Device)
Jul 13 11:37:01 ubuntu kernel: [    0.267860] ACPI: Added _OSI(3.0 _SCP Extensions)
Jul 13 11:37:01 ubuntu kernel: [    0.268530] ACPI: Added _OSI(Processor Aggregator Device)
Jul 13 11:37:01 ubuntu kernel: [    0.274648] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
Jul 13 11:37:01 ubuntu kernel: [    0.276790] ACPI: Interpreter enabled
Jul 13 11:37:01 ubuntu kernel: [    0.277378] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20150930/hwxface-580)
Jul 13 11:37:01 ubuntu kernel: [    0.278856] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S3_] (20150930/hwxface-580)
Jul 13 11:37:01 ubuntu kernel: [    0.280286] ACPI: (supports S0 S1 S4 S5)
Jul 13 11:37:01 ubuntu kernel: [    0.280881] ACPI: Using IOAPIC for interrupt routing
Jul 13 11:37:01 ubuntu kernel: [    0.281665] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
Jul 13 11:37:01 ubuntu kernel: [    0.320176] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-7f])
Jul 13 11:37:01 ubuntu kernel: [    0.321052] acpi PNP0A03:00: _OSC: OS supports [ExtendedConfig ASPM ClockPM Segments MSI]
Jul 13 11:37:01 ubuntu kernel: [    0.322352] acpi PNP0A03:00: _OSC: platform does not support [AER]
Jul 13 11:37:01 ubuntu kernel: [    0.323357] acpi PNP0A03:00: _OSC: OS now controls [PCIeHotplug PME PCIeCapability]
Jul 13 11:37:01 ubuntu kernel: [    0.325703] PCI host bridge to bus 0000:00
Jul 13 11:37:01 ubuntu kernel: [    0.326313] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff window]
Jul 13 11:37:01 ubuntu kernel: [    0.327380] pci_bus 0000:00: root bus resource [mem 0x000cc000-0x000cffff window]
Jul 13 11:37:01 ubuntu kernel: [    0.328445] pci_bus 0000:00: root bus resource [mem 0x000d0000-0x000d3fff window]
Jul 13 11:37:01 ubuntu kernel: [    0.329512] pci_bus 0000:00: root bus resource [mem 0x000d4000-0x000d7fff window]
Jul 13 11:37:01 ubuntu kernel: [    0.330588] pci_bus 0000:00: root bus resource [mem 0x000d8000-0x000dbfff window]
Jul 13 11:37:01 ubuntu kernel: [    0.331655] pci_bus 0000:00: root bus resource [mem 0x40000000-0xfebfffff window]
Jul 13 11:37:01 ubuntu kernel: [    0.332718] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7 window]
Jul 13 11:37:01 ubuntu kernel: [    0.333657] pci_bus 0000:00: root bus resource [io  0x0d00-0xfeff window]
Jul 13 11:37:01 ubuntu kernel: [    0.334602] pci_bus 0000:00: root bus resource [bus 00-7f]
Jul 13 11:37:01 ubuntu kernel: [    0.335414] pci 0000:00:00.0: [8086:7190] type 00 class 0x060000
Jul 13 11:37:01 ubuntu kernel: [    0.335851] pci 0000:00:01.0: [8086:7191] type 01 class 0x060400
Jul 13 11:37:01 ubuntu kernel: [    0.336211] pci 0000:00:07.0: [8086:7110] type 00 class 0x060100
Jul 13 11:37:01 ubuntu kernel: [    0.336689] pci 0000:00:07.1: [8086:7111] type 00 class 0x01018a
Jul 13 11:37:01 ubuntu kernel: [    0.337698] pci 0000:00:07.1: reg 0x20: [io  0x1060-0x106f]
Jul 13 11:37:01 ubuntu kernel: [    0.338110] pci 0000:00:07.1: legacy IDE quirk: reg 0x10: [io  0x01f0-0x01f7]
Jul 13 11:37:01 ubuntu kernel: [    0.339099] pci 0000:00:07.1: legacy IDE quirk: reg 0x14: [io  0x03f6]
Jul 13 11:37:01 ubuntu kernel: [    0.340006] pci 0000:00:07.1: legacy IDE quirk: reg 0x18: [io  0x0170-0x0177]
Jul 13 11:37:01 ubuntu kernel: [    0.340989] pci 0000:00:07.1: legacy IDE quirk: reg 0x1c: [io  0x0376]
Jul 13 11:37:01 ubuntu kernel: [    0.342039] pci 0000:00:07.3: [8086:7113] type 00 class 0x068000
Jul 13 11:37:01 ubuntu kernel: [    0.343161] pci 0000:00:07.3: quirk: [io  0x1000-0x103f] claimed by PIIX4 ACPI
Jul 13 11:37:01 ubuntu kernel: [    0.344201] pci 0000:00:07.3: quirk: [io  0x1040-0x104f] claimed by PIIX4 SMB
Jul 13 11:37:01 ubuntu kernel: [    0.345386] pci 0000:00:07.7: [15ad:0740] type 00 class 0x088000
Jul 13 11:37:01 ubuntu kernel: [    0.345977] pci 0000:00:07.7: reg 0x10: [io  0x1080-0x10bf]
Jul 13 11:37:01 ubuntu kernel: [    0.346464] pci 0000:00:07.7: reg 0x14: [mem 0xfebfe000-0xfebfffff 64bit]
Jul 13 11:37:01 ubuntu kernel: [    0.348551] pci 0000:00:0f.0: [15ad:0405] type 00 class 0x030000
Jul 13 11:37:01 ubuntu kernel: [    0.349869] pci 0000:00:0f.0: reg 0x10: [io  0x1070-0x107f]
Jul 13 11:37:01 ubuntu kernel: [    0.351078] pci 0000:00:0f.0: reg 0x14: [mem 0xec000000-0xefffffff pref]
Jul 13 11:37:01 ubuntu kernel: [    0.352264] pci 0000:00:0f.0: reg 0x18: [mem 0xfe000000-0xfe7fffff]
Jul 13 11:37:01 ubuntu kernel: [    0.357085] pci 0000:00:0f.0: reg 0x30: [mem 0x00000000-0x00007fff pref]
Jul 13 11:37:01 ubuntu kernel: [    0.357759] pci 0000:00:10.0: [1000:0030] type 00 class 0x010000
Jul 13 11:37:01 ubuntu kernel: [    0.358530] pci 0000:00:10.0: reg 0x10: [io  0x1400-0x14ff]
Jul 13 11:37:01 ubuntu kernel: [    0.359279] pci 0000:00:10.0: reg 0x14: [mem 0xfeba0000-0xfebbffff 64bit]
Jul 13 11:37:01 ubuntu kernel: [    0.360026] pci 0000:00:10.0: reg 0x1c: [mem 0xfebc0000-0xfebdffff 64bit]
Jul 13 11:37:01 ubuntu kernel: [    0.361492] pci 0000:00:10.0: reg 0x30: [mem 0x00000000-0x00003fff pref]
Jul 13 11:37:01 ubuntu kernel: [    0.361659] pci 0000:00:11.0: [15ad:0790] type 01 class 0x060401
Jul 13 11:37:01 ubuntu kernel: [    0.362038] pci 0000:00:11.0: System wakeup disabled by ACPI
Jul 13 11:37:01 ubuntu kernel: [    0.362960] pci 0000:00:15.0: [15ad:07a0] type 01 class 0x060400
Jul 13 11:37:01 ubuntu kernel: [    0.363402] pci 0000:00:15.0: PME# supported from D0 D3hot D3cold
Jul 13 11:37:01 ubuntu kernel: [    0.363528] pci 0000:00:15.0: System wakeup disabled by ACPI
Jul 13 11:37:01 ubuntu kernel: [    0.364414] pci 0000:00:15.1: [15ad:07a0] type 01 class 0x060400
Jul 13 11:37:01 ubuntu kernel: [    0.364859] pci 0000:00:15.1: PME# supported from D0 D3hot D3cold
Jul 13 11:37:01 ubuntu kernel: [    0.364984] pci 0000:00:15.1: System wakeup disabled by ACPI
Jul 13 11:37:01 ubuntu kernel: [    0.365870] pci 0000:00:15.2: [15ad:07a0] type 01 class 0x060400
Jul 13 11:37:01 ubuntu kernel: [    0.366322] pci 0000:00:15.2: PME# supported from D0 D3hot D3cold
Jul 13 11:37:01 ubuntu kernel: [    0.366448] pci 0000:00:15.2: System wakeup disabled by ACPI
Jul 13 11:37:01 ubuntu kernel: [    0.367334] pci 0000:00:15.3: [15ad:07a0] type 01 class 0x060400
Jul 13 11:37:01 ubuntu kernel: [    0.367778] pci 0000:00:15.3: PME# supported from D0 D3hot D3cold
Jul 13 11:37:01 ubuntu kernel: [    0.367903] pci 0000:00:15.3: System wakeup disabled by ACPI
Jul 13 11:37:01 ubuntu kernel: [    0.368787] pci 0000:00:15.4: [15ad:07a0] type 01 class 0x060400
Jul 13 11:37:01 ubuntu kernel: [    0.369240] pci 0000:00:15.4: PME# supported from D0 D3hot D3cold
Jul 13 11:37:01 ubuntu kernel: [    0.369376] pci 0000:00:15.4: System wakeup disabled by ACPI
Jul 13 11:37:01 ubuntu kernel: [    0.370268] pci 0000:00:15.5: [15ad:07a0] type 01 class 0x060400
Jul 13 11:37:01 ubuntu kernel: [    0.370719] pci 0000:00:15.5: PME# supported from D0 D3hot D3cold
Jul 13 11:37:01 ubuntu kernel: [    0.370845] pci 0000:00:15.5: System wakeup disabled by ACPI
Jul 13 11:37:01 ubuntu kernel: [    0.371729] pci 0000:00:15.6: [15ad:07a0] type 01 class 0x060400
Jul 13 11:37:01 ubuntu kernel: [    0.372171] pci 0000:00:15.6: PME# supported from D0 D3hot D3cold
Jul 13 11:37:01 ubuntu kernel: [    0.372295] pci 0000:00:15.6: System wakeup disabled by ACPI
Jul 13 11:37:01 ubuntu kernel: [    0.373179] pci 0000:00:15.7: [15ad:07a0] type 01 class 0x060400
Jul 13 11:37:01 ubuntu kernel: [    0.373619] pci 0000:00:15.7: PME# supported from D0 D3hot D3cold
Jul 13 11:37:01 ubuntu kernel: [    0.373743] pci 0000:00:15.7: System wakeup disabled by ACPI
Jul 13 11:37:01 ubuntu kernel: [    0.374659] pci 0000:00:16.0: [15ad:07a0] type 01 class 0x060400
Jul 13 11:37:01 ubuntu kernel: [    0.375100] pci 0000:00:16.0: PME# supported from D0 D3hot D3cold
Jul 13 11:37:01 ubuntu kernel: [    0.375225] pci 0000:00:16.0: System wakeup disabled by ACPI
Jul 13 11:37:01 ubuntu kernel: [    0.376109] pci 0000:00:16.1: [15ad:07a0] type 01 class 0x060400
Jul 13 11:37:01 ubuntu kernel: [    0.376559] pci 0000:00:16.1: PME# supported from D0 D3hot D3cold
Jul 13 11:37:01 ubuntu kernel: [    0.376683] pci 0000:00:16.1: System wakeup disabled by ACPI
Jul 13 11:37:01 ubuntu kernel: [    0.377566] pci 0000:00:16.2: [15ad:07a0] type 01 class 0x060400
Jul 13 11:37:01 ubuntu kernel: [    0.378005] pci 0000:00:16.2: PME# supported from D0 D3hot D3cold
Jul 13 11:37:01 ubuntu kernel: [    0.378135] pci 0000:00:16.2: System wakeup disabled by ACPI
Jul 13 11:37:01 ubuntu kernel: [    0.379021] pci 0000:00:16.3: [15ad:07a0] type 01 class 0x060400
Jul 13 11:37:01 ubuntu kernel: [    0.379462] pci 0000:00:16.3: PME# supported from D0 D3hot D3cold
Jul 13 11:37:01 ubuntu kernel: [    0.379586] pci 0000:00:16.3: System wakeup disabled by ACPI
Jul 13 11:37:01 ubuntu kernel: [    0.380471] pci 0000:00:16.4: [15ad:07a0] type 01 class 0x060400
Jul 13 11:37:01 ubuntu kernel: [    0.380915] pci 0000:00:16.4: PME# supported from D0 D3hot D3cold
Jul 13 11:37:01 ubuntu kernel: [    0.381040] pci 0000:00:16.4: System wakeup disabled by ACPI
Jul 13 11:37:01 ubuntu kernel: [    0.381935] pci 0000:00:16.5: [15ad:07a0] type 01 class 0x060400
Jul 13 11:37:01 ubuntu kernel: [    0.382384] pci 0000:00:16.5: PME# supported from D0 D3hot D3cold
Jul 13 11:37:01 ubuntu kernel: [    0.382509] pci 0000:00:16.5: System wakeup disabled by ACPI
Jul 13 11:37:01 ubuntu kernel: [    0.383396] pci 0000:00:16.6: [15ad:07a0] type 01 class 0x060400
Jul 13 11:37:01 ubuntu kernel: [    0.383836] pci 0000:00:16.6: PME# supported from D0 D3hot D3cold
Jul 13 11:37:01 ubuntu kernel: [    0.383964] pci 0000:00:16.6: System wakeup disabled by ACPI
Jul 13 11:37:01 ubuntu kernel: [    0.384847] pci 0000:00:16.7: [15ad:07a0] type 01 class 0x060400
Jul 13 11:37:01 ubuntu kernel: [    0.385287] pci 0000:00:16.7: PME# supported from D0 D3hot D3cold
Jul 13 11:37:01 ubuntu kernel: [    0.385412] pci 0000:00:16.7: System wakeup disabled by ACPI
Jul 13 11:37:01 ubuntu kernel: [    0.386305] pci 0000:00:17.0: [15ad:07a0] type 01 class 0x060400
Jul 13 11:37:01 ubuntu kernel: [    0.386750] pci 0000:00:17.0: PME# supported from D0 D3hot D3cold
Jul 13 11:37:01 ubuntu kernel: [    0.386874] pci 0000:00:17.0: System wakeup disabled by ACPI
Jul 13 11:37:01 ubuntu kernel: [    0.387782] pci 0000:00:17.1: [15ad:07a0] type 01 class 0x060400
Jul 13 11:37:01 ubuntu kernel: [    0.388232] pci 0000:00:17.1: PME# supported from D0 D3hot D3cold
Jul 13 11:37:01 ubuntu kernel: [    0.388356] pci 0000:00:17.1: System wakeup disabled by ACPI
Jul 13 11:37:01 ubuntu kernel: [    0.389241] pci 0000:00:17.2: [15ad:07a0] type 01 class 0x060400
Jul 13 11:37:01 ubuntu kernel: [    0.389680] pci 0000:00:17.2: PME# supported from D0 D3hot D3cold
Jul 13 11:37:01 ubuntu kernel: [    0.389804] pci 0000:00:17.2: System wakeup disabled by ACPI
Jul 13 11:37:01 ubuntu kernel: [    0.390701] pci 0000:00:17.3: [15ad:07a0] type 01 class 0x060400
Jul 13 11:37:01 ubuntu kernel: [    0.391142] pci 0000:00:17.3: PME# supported from D0 D3hot D3cold
Jul 13 11:37:01 ubuntu kernel: [    0.391266] pci 0000:00:17.3: System wakeup disabled by ACPI
Jul 13 11:37:01 ubuntu kernel: [    0.392151] pci 0000:00:17.4: [15ad:07a0] type 01 class 0x060400
Jul 13 11:37:01 ubuntu kernel: [    0.392591] pci 0000:00:17.4: PME# supported from D0 D3hot D3cold
Jul 13 11:37:01 ubuntu kernel: [    0.392716] pci 0000:00:17.4: System wakeup disabled by ACPI
Jul 13 11:37:01 ubuntu kernel: [    0.393600] pci 0000:00:17.5: [15ad:07a0] type 01 class 0x060400
Jul 13 11:37:01 ubuntu kernel: [    0.394039] pci 0000:00:17.5: PME# supported from D0 D3hot D3cold
Jul 13 11:37:01 ubuntu kernel: [    0.394172] pci 0000:00:17.5: System wakeup disabled by ACPI
Jul 13 11:37:01 ubuntu kernel: [    0.395058] pci 0000:00:17.6: [15ad:07a0] type 01 class 0x060400
Jul 13 11:37:01 ubuntu kernel: [    0.395498] pci 0000:00:17.6: PME# supported from D0 D3hot D3cold
Jul 13 11:37:01 ubuntu kernel: [    0.395623] pci 0000:00:17.6: System wakeup disabled by ACPI
Jul 13 11:37:01 ubuntu kernel: [    0.396520] pci 0000:00:17.7: [15ad:07a0] type 01 class 0x060400
Jul 13 11:37:01 ubuntu kernel: [    0.396988] pci 0000:00:17.7: PME# supported from D0 D3hot D3cold
Jul 13 11:37:01 ubuntu kernel: [    0.397119] pci 0000:00:17.7: System wakeup disabled by ACPI
Jul 13 11:37:01 ubuntu kernel: [    0.398005] pci 0000:00:18.0: [15ad:07a0] type 01 class 0x060400
Jul 13 11:37:01 ubuntu kernel: [    0.398452] pci 0000:00:18.0: PME# supported from D0 D3hot D3cold
Jul 13 11:37:01 ubuntu kernel: [    0.398577] pci 0000:00:18.0: System wakeup disabled by ACPI
Jul 13 11:37:01 ubuntu kernel: [    0.399461] pci 0000:00:18.1: [15ad:07a0] type 01 class 0x060400
Jul 13 11:37:01 ubuntu kernel: [    0.399907] pci 0000:00:18.1: PME# supported from D0 D3hot D3cold
Jul 13 11:37:01 ubuntu kernel: [    0.400032] pci 0000:00:18.1: System wakeup disabled by ACPI
Jul 13 11:37:01 ubuntu kernel: [    0.400927] pci 0000:00:18.2: [15ad:07a0] type 01 class 0x060400
Jul 13 11:37:01 ubuntu kernel: [    0.401369] pci 0000:00:18.2: PME# supported from D0 D3hot D3cold
Jul 13 11:37:01 ubuntu kernel: [    0.401493] pci 0000:00:18.2: System wakeup disabled by ACPI
Jul 13 11:37:01 ubuntu kernel: [    0.402386] pci 0000:00:18.3: [15ad:07a0] type 01 class 0x060400
Jul 13 11:37:01 ubuntu kernel: [    0.402855] pci 0000:00:18.3: PME# supported from D0 D3hot D3cold
Jul 13 11:37:01 ubuntu kernel: [    0.402980] pci 0000:00:18.3: System wakeup disabled by ACPI
Jul 13 11:37:01 ubuntu kernel: [    0.403864] pci 0000:00:18.4: [15ad:07a0] type 01 class 0x060400
Jul 13 11:37:01 ubuntu kernel: [    0.404305] pci 0000:00:18.4: PME# supported from D0 D3hot D3cold
Jul 13 11:37:01 ubuntu kernel: [    0.404429] pci 0000:00:18.4: System wakeup disabled by ACPI
Jul 13 11:37:01 ubuntu kernel: [    0.405312] pci 0000:00:18.5: [15ad:07a0] type 01 class 0x060400
Jul 13 11:37:01 ubuntu kernel: [    0.405752] pci 0000:00:18.5: PME# supported from D0 D3hot D3cold
Jul 13 11:37:01 ubuntu kernel: [    0.405877] pci 0000:00:18.5: System wakeup disabled by ACPI
Jul 13 11:37:01 ubuntu kernel: [    0.406795] pci 0000:00:18.6: [15ad:07a0] type 01 class 0x060400
Jul 13 11:37:01 ubuntu kernel: [    0.407237] pci 0000:00:18.6: PME# supported from D0 D3hot D3cold
Jul 13 11:37:01 ubuntu kernel: [    0.407363] pci 0000:00:18.6: System wakeup disabled by ACPI
Jul 13 11:37:01 ubuntu kernel: [    0.408246] pci 0000:00:18.7: [15ad:07a0] type 01 class 0x060400
Jul 13 11:37:01 ubuntu kernel: [    0.408691] pci 0000:00:18.7: PME# supported from D0 D3hot D3cold
Jul 13 11:37:01 ubuntu kernel: [    0.408816] pci 0000:00:18.7: System wakeup disabled by ACPI
Jul 13 11:37:01 ubuntu kernel: [    0.409939] pci 0000:00:01.0: PCI bridge to [bus 01]
Jul 13 11:37:01 ubuntu kernel: [    0.410962] acpiphp: Slot [32] registered
Jul 13 11:37:01 ubuntu kernel: [    0.411567] acpiphp: Slot [33] registered
Jul 13 11:37:01 ubuntu kernel: [    0.412169] acpiphp: Slot [34] registered
Jul 13 11:37:01 ubuntu kernel: [    0.412771] acpiphp: Slot [35] registered
Jul 13 11:37:01 ubuntu kernel: [    0.413371] acpiphp: Slot [36] registered
Jul 13 11:37:01 ubuntu kernel: [    0.413970] acpiphp: Slot [37] registered
Jul 13 11:37:01 ubuntu kernel: [    0.414584] acpiphp: Slot [38] registered
Jul 13 11:37:01 ubuntu kernel: [    0.415184] acpiphp: Slot [39] registered
Jul 13 11:37:01 ubuntu kernel: [    0.415784] acpiphp: Slot [40] registered
Jul 13 11:37:01 ubuntu kernel: [    0.416385] acpiphp: Slot [41] registered
Jul 13 11:37:01 ubuntu kernel: [    0.416984] acpiphp: Slot [42] registered
Jul 13 11:37:01 ubuntu kernel: [    0.417582] acpiphp: Slot [43] registered
Jul 13 11:37:01 ubuntu kernel: [    0.418188] acpiphp: Slot [44] registered
Jul 13 11:37:01 ubuntu kernel: [    0.418787] acpiphp: Slot [45] registered
Jul 13 11:37:01 ubuntu kernel: [    0.419386] acpiphp: Slot [46] registered
Jul 13 11:37:01 ubuntu kernel: [    0.419986] acpiphp: Slot [47] registered
Jul 13 11:37:01 ubuntu kernel: [    0.420587] acpiphp: Slot [48] registered
Jul 13 11:37:01 ubuntu kernel: [    0.421190] acpiphp: Slot [49] registered
Jul 13 11:37:01 ubuntu kernel: [    0.421791] acpiphp: Slot [50] registered
Jul 13 11:37:01 ubuntu kernel: [    0.422398] acpiphp: Slot [51] registered
Jul 13 11:37:01 ubuntu kernel: [    0.422997] acpiphp: Slot [52] registered
Jul 13 11:37:01 ubuntu kernel: [    0.423597] acpiphp: Slot [53] registered
Jul 13 11:37:01 ubuntu kernel: [    0.424195] acpiphp: Slot [54] registered
Jul 13 11:37:01 ubuntu kernel: [    0.424795] acpiphp: Slot [55] registered
Jul 13 11:37:01 ubuntu kernel: [    0.425402] acpiphp: Slot [56] registered
Jul 13 11:37:01 ubuntu kernel: [    0.426003] acpiphp: Slot [57] registered
Jul 13 11:37:01 ubuntu kernel: [    0.426612] acpiphp: Slot [58] registered
Jul 13 11:37:01 ubuntu kernel: [    0.427212] acpiphp: Slot [59] registered
Jul 13 11:37:01 ubuntu kernel: [    0.427811] acpiphp: Slot [60] registered
Jul 13 11:37:01 ubuntu kernel: [    0.428410] acpiphp: Slot [61] registered
Jul 13 11:37:01 ubuntu kernel: [    0.429010] acpiphp: Slot [62] registered
Jul 13 11:37:01 ubuntu kernel: [    0.429610] acpiphp: Slot [63] registered
Jul 13 11:37:01 ubuntu kernel: [    0.430417] pci 0000:00:11.0: PCI bridge to [bus 02] (subtractive decode)
Jul 13 11:37:01 ubuntu kernel: [    0.431369] pci 0000:00:11.0:   bridge window [io  0x2000-0x3fff]
Jul 13 11:37:01 ubuntu kernel: [    0.431384] pci 0000:00:11.0:   bridge window [mem 0xfd600000-0xfdffffff]
Jul 13 11:37:01 ubuntu kernel: [    0.431410] pci 0000:00:11.0:   bridge window [mem 0xebb00000-0xebffffff 64bit pref]
Jul 13 11:37:01 ubuntu kernel: [    0.431412] pci 0000:00:11.0:   bridge window [mem 0x000a0000-0x000bffff window] (subtractive decode)
Jul 13 11:37:01 ubuntu kernel: [    0.431413] pci 0000:00:11.0:   bridge window [mem 0x000cc000-0x000cffff window] (subtractive decode)
Jul 13 11:37:01 ubuntu kernel: [    0.431414] pci 0000:00:11.0:   bridge window [mem 0x000d0000-0x000d3fff window] (subtractive decode)
Jul 13 11:37:01 ubuntu kernel: [    0.431415] pci 0000:00:11.0:   bridge window [mem 0x000d4000-0x000d7fff window] (subtractive decode)
Jul 13 11:37:01 ubuntu kernel: [    0.431417] pci 0000:00:11.0:   bridge window [mem 0x000d8000-0x000dbfff window] (subtractive decode)
Jul 13 11:37:01 ubuntu kernel: [    0.431418] pci 0000:00:11.0:   bridge window [mem 0x40000000-0xfebfffff window] (subtractive decode)
Jul 13 11:37:01 ubuntu kernel: [    0.431419] pci 0000:00:11.0:   bridge window [io  0x0000-0x0cf7 window] (subtractive decode)
Jul 13 11:37:01 ubuntu kernel: [    0.431420] pci 0000:00:11.0:   bridge window [io  0x0d00-0xfeff window] (subtractive decode)
Jul 13 11:37:01 ubuntu kernel: [    0.431691] pci 0000:03:00.0: [15ad:07b0] type 00 class 0x020000
Jul 13 11:37:01 ubuntu kernel: [    0.432824] pci 0000:03:00.0: reg 0x10: [mem 0xfd5fc000-0xfd5fcfff]
Jul 13 11:37:01 ubuntu kernel: [    0.433819] pci 0000:03:00.0: reg 0x14: [mem 0xfd5fd000-0xfd5fdfff]
Jul 13 11:37:01 ubuntu kernel: [    0.434825] pci 0000:03:00.0: reg 0x18: [mem 0xfd5fe000-0xfd5fffff]
Jul 13 11:37:01 ubuntu kernel: [    0.435817] pci 0000:03:00.0: reg 0x1c: [io  0x4000-0x400f]
Jul 13 11:37:01 ubuntu kernel: [    0.438818] pci 0000:03:00.0: reg 0x30: [mem 0x00000000-0x0000ffff pref]
Jul 13 11:37:01 ubuntu kernel: [    0.439021] pci 0000:03:00.0: supports D1 D2
Jul 13 11:37:01 ubuntu kernel: [    0.439022] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold
Jul 13 11:37:01 ubuntu kernel: [    0.439141] pci 0000:03:00.0: System wakeup disabled by ACPI
Jul 13 11:37:01 ubuntu kernel: [    0.439979] pci 0000:03:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
Jul 13 11:37:01 ubuntu kernel: [    0.441724] pci 0000:00:15.0: PCI bridge to [bus 03]
Jul 13 11:37:01 ubuntu kernel: [    0.442451] pci 0000:00:15.0:   bridge window [io  0x4000-0x4fff]
Jul 13 11:37:01 ubuntu kernel: [    0.442466] pci 0000:00:15.0:   bridge window [mem 0xfd500000-0xfd5fffff]
Jul 13 11:37:01 ubuntu kernel: [    0.442719] pci 0000:00:15.1: PCI bridge to [bus 04]
Jul 13 11:37:01 ubuntu kernel: [    0.443441] pci 0000:00:15.1:   bridge window [io  0x8000-0x8fff]
Jul 13 11:37:01 ubuntu kernel: [    0.443456] pci 0000:00:15.1:   bridge window [mem 0xfd100000-0xfd1fffff]
Jul 13 11:37:01 ubuntu kernel: [    0.443483] pci 0000:00:15.1:   bridge window [mem 0xeb700000-0xeb7fffff 64bit pref]
Jul 13 11:37:01 ubuntu kernel: [    0.443704] pci 0000:00:15.2: PCI bridge to [bus 05]
Jul 13 11:37:01 ubuntu kernel: [    0.444423] pci 0000:00:15.2:   bridge window [io  0xc000-0xcfff]
Jul 13 11:37:01 ubuntu kernel: [    0.444438] pci 0000:00:15.2:   bridge window [mem 0xfcd00000-0xfcdfffff]
Jul 13 11:37:01 ubuntu kernel: [    0.444464] pci 0000:00:15.2:   bridge window [mem 0xeb300000-0xeb3fffff 64bit pref]
Jul 13 11:37:01 ubuntu kernel: [    0.444683] pci 0000:00:15.3: PCI bridge to [bus 06]
Jul 13 11:37:01 ubuntu kernel: [    0.445419] pci 0000:00:15.3:   bridge window [mem 0xfc900000-0xfc9fffff]
Jul 13 11:37:01 ubuntu kernel: [    0.445446] pci 0000:00:15.3:   bridge window [mem 0xeaf00000-0xeaffffff 64bit pref]
Jul 13 11:37:01 ubuntu kernel: [    0.445663] pci 0000:00:15.4: PCI bridge to [bus 07]
Jul 13 11:37:01 ubuntu kernel: [    0.446412] pci 0000:00:15.4:   bridge window [mem 0xfc500000-0xfc5fffff]
Jul 13 11:37:01 ubuntu kernel: [    0.446439] pci 0000:00:15.4:   bridge window [mem 0xeab00000-0xeabfffff 64bit pref]
Jul 13 11:37:01 ubuntu kernel: [    0.446659] pci 0000:00:15.5: PCI bridge to [bus 08]
Jul 13 11:37:01 ubuntu kernel: [    0.447391] pci 0000:00:15.5:   bridge window [mem 0xfc100000-0xfc1fffff]
Jul 13 11:37:01 ubuntu kernel: [    0.447418] pci 0000:00:15.5:   bridge window [mem 0xea700000-0xea7fffff 64bit pref]
Jul 13 11:37:01 ubuntu kernel: [    0.447637] pci 0000:00:15.6: PCI bridge to [bus 09]
Jul 13 11:37:01 ubuntu kernel: [    0.448369] pci 0000:00:15.6:   bridge window [mem 0xfbd00000-0xfbdfffff]
Jul 13 11:37:01 ubuntu kernel: [    0.448396] pci 0000:00:15.6:   bridge window [mem 0xea300000-0xea3fffff 64bit pref]
Jul 13 11:37:01 ubuntu kernel: [    0.448613] pci 0000:00:15.7: PCI bridge to [bus 0a]
Jul 13 11:37:01 ubuntu kernel: [    0.449368] pci 0000:00:15.7:   bridge window [mem 0xfb900000-0xfb9fffff]
Jul 13 11:37:01 ubuntu kernel: [    0.449395] pci 0000:00:15.7:   bridge window [mem 0xe9f00000-0xe9ffffff 64bit pref]
Jul 13 11:37:01 ubuntu kernel: [    0.449615] pci 0000:00:16.0: PCI bridge to [bus 0b]
Jul 13 11:37:01 ubuntu kernel: [    0.450346] pci 0000:00:16.0:   bridge window [io  0x5000-0x5fff]
Jul 13 11:37:01 ubuntu kernel: [    0.450361] pci 0000:00:16.0:   bridge window [mem 0xfd400000-0xfd4fffff]
Jul 13 11:37:01 ubuntu kernel: [    0.450388] pci 0000:00:16.0:   bridge window [mem 0xeba00000-0xebafffff 64bit pref]
Jul 13 11:37:01 ubuntu kernel: [    0.450607] pci 0000:00:16.1: PCI bridge to [bus 0c]
Jul 13 11:37:01 ubuntu kernel: [    0.451337] pci 0000:00:16.1:   bridge window [io  0x9000-0x9fff]
Jul 13 11:37:01 ubuntu kernel: [    0.451351] pci 0000:00:16.1:   bridge window [mem 0xfd000000-0xfd0fffff]
Jul 13 11:37:01 ubuntu kernel: [    0.451378] pci 0000:00:16.1:   bridge window [mem 0xeb600000-0xeb6fffff 64bit pref]
Jul 13 11:37:01 ubuntu kernel: [    0.451599] pci 0000:00:16.2: PCI bridge to [bus 0d]
Jul 13 11:37:01 ubuntu kernel: [    0.452319] pci 0000:00:16.2:   bridge window [io  0xd000-0xdfff]
Jul 13 11:37:01 ubuntu kernel: [    0.452333] pci 0000:00:16.2:   bridge window [mem 0xfcc00000-0xfccfffff]
Jul 13 11:37:01 ubuntu kernel: [    0.452360] pci 0000:00:16.2:   bridge window [mem 0xeb200000-0xeb2fffff 64bit pref]
Jul 13 11:37:01 ubuntu kernel: [    0.452577] pci 0000:00:16.3: PCI bridge to [bus 0e]
Jul 13 11:37:01 ubuntu kernel: [    0.453348] pci 0000:00:16.3:   bridge window [mem 0xfc800000-0xfc8fffff]
Jul 13 11:37:01 ubuntu kernel: [    0.453375] pci 0000:00:16.3:   bridge window [mem 0xeae00000-0xeaefffff 64bit pref]
Jul 13 11:37:01 ubuntu kernel: [    0.453595] pci 0000:00:16.4: PCI bridge to [bus 0f]
Jul 13 11:37:01 ubuntu kernel: [    0.454340] pci 0000:00:16.4:   bridge window [mem 0xfc400000-0xfc4fffff]
Jul 13 11:37:01 ubuntu kernel: [    0.454367] pci 0000:00:16.4:   bridge window [mem 0xeaa00000-0xeaafffff 64bit pref]
Jul 13 11:37:01 ubuntu kernel: [    0.454588] pci 0000:00:16.5: PCI bridge to [bus 10]
Jul 13 11:37:01 ubuntu kernel: [    0.455320] pci 0000:00:16.5:   bridge window [mem 0xfc000000-0xfc0fffff]
Jul 13 11:37:01 ubuntu kernel: [    0.455347] pci 0000:00:16.5:   bridge window [mem 0xea600000-0xea6fffff 64bit pref]
Jul 13 11:37:01 ubuntu kernel: [    0.455566] pci 0000:00:16.6: PCI bridge to [bus 11]
Jul 13 11:37:01 ubuntu kernel: [    0.456298] pci 0000:00:16.6:   bridge window [mem 0xfbc00000-0xfbcfffff]
Jul 13 11:37:01 ubuntu kernel: [    0.456326] pci 0000:00:16.6:   bridge window [mem 0xea200000-0xea2fffff 64bit pref]
Jul 13 11:37:01 ubuntu kernel: [    0.456544] pci 0000:00:16.7: PCI bridge to [bus 12]
Jul 13 11:37:01 ubuntu kernel: [    0.457277] pci 0000:00:16.7:   bridge window [mem 0xfb800000-0xfb8fffff]
Jul 13 11:37:01 ubuntu kernel: [    0.457304] pci 0000:00:16.7:   bridge window [mem 0xe9e00000-0xe9efffff 64bit pref]
Jul 13 11:37:01 ubuntu kernel: [    0.457523] pci 0000:00:17.0: PCI bridge to [bus 13]
Jul 13 11:37:01 ubuntu kernel: [    0.458251] pci 0000:00:17.0:   bridge window [io  0x6000-0x6fff]
Jul 13 11:37:01 ubuntu kernel: [    0.458265] pci 0000:00:17.0:   bridge window [mem 0xfd300000-0xfd3fffff]
Jul 13 11:37:01 ubuntu kernel: [    0.458292] pci 0000:00:17.0:   bridge window [mem 0xeb900000-0xeb9fffff 64bit pref]
Jul 13 11:37:01 ubuntu kernel: [    0.458516] pci 0000:00:17.1: PCI bridge to [bus 14]
Jul 13 11:37:01 ubuntu kernel: [    0.459236] pci 0000:00:17.1:   bridge window [io  0xa000-0xafff]
Jul 13 11:37:01 ubuntu kernel: [    0.459251] pci 0000:00:17.1:   bridge window [mem 0xfcf00000-0xfcffffff]
Jul 13 11:37:01 ubuntu kernel: [    0.459277] pci 0000:00:17.1:   bridge window [mem 0xeb500000-0xeb5fffff 64bit pref]
Jul 13 11:37:01 ubuntu kernel: [    0.459501] pci 0000:00:17.2: PCI bridge to [bus 15]
Jul 13 11:37:01 ubuntu kernel: [    0.460223] pci 0000:00:17.2:   bridge window [io  0xe000-0xefff]
Jul 13 11:37:01 ubuntu kernel: [    0.460237] pci 0000:00:17.2:   bridge window [mem 0xfcb00000-0xfcbfffff]
Jul 13 11:37:01 ubuntu kernel: [    0.460264] pci 0000:00:17.2:   bridge window [mem 0xeb100000-0xeb1fffff 64bit pref]
Jul 13 11:37:01 ubuntu kernel: [    0.460483] pci 0000:00:17.3: PCI bridge to [bus 16]
Jul 13 11:37:01 ubuntu kernel: [    0.461220] pci 0000:00:17.3:   bridge window [mem 0xfc700000-0xfc7fffff]
Jul 13 11:37:01 ubuntu kernel: [    0.461247] pci 0000:00:17.3:   bridge window [mem 0xead00000-0xeadfffff 64bit pref]
Jul 13 11:37:01 ubuntu kernel: [    0.461465] pci 0000:00:17.4: PCI bridge to [bus 17]
Jul 13 11:37:01 ubuntu kernel: [    0.462205] pci 0000:00:17.4:   bridge window [mem 0xfc300000-0xfc3fffff]
Jul 13 11:37:01 ubuntu kernel: [    0.462232] pci 0000:00:17.4:   bridge window [mem 0xea900000-0xea9fffff 64bit pref]
Jul 13 11:37:01 ubuntu kernel: [    0.462452] pci 0000:00:17.5: PCI bridge to [bus 18]
Jul 13 11:37:01 ubuntu kernel: [    0.463185] pci 0000:00:17.5:   bridge window [mem 0xfbf00000-0xfbffffff]
Jul 13 11:37:01 ubuntu kernel: [    0.463212] pci 0000:00:17.5:   bridge window [mem 0xea500000-0xea5fffff 64bit pref]
Jul 13 11:37:01 ubuntu kernel: [    0.463431] pci 0000:00:17.6: PCI bridge to [bus 19]
Jul 13 11:37:01 ubuntu kernel: [    0.464163] pci 0000:00:17.6:   bridge window [mem 0xfbb00000-0xfbbfffff]
Jul 13 11:37:01 ubuntu kernel: [    0.464190] pci 0000:00:17.6:   bridge window [mem 0xea100000-0xea1fffff 64bit pref]
Jul 13 11:37:01 ubuntu kernel: [    0.464408] pci 0000:00:17.7: PCI bridge to [bus 1a]
Jul 13 11:37:01 ubuntu kernel: [    0.465141] pci 0000:00:17.7:   bridge window [mem 0xfb700000-0xfb7fffff]
Jul 13 11:37:01 ubuntu kernel: [    0.465167] pci 0000:00:17.7:   bridge window [mem 0xe9d00000-0xe9dfffff 64bit pref]
Jul 13 11:37:01 ubuntu kernel: [    0.465388] pci 0000:00:18.0: PCI bridge to [bus 1b]
Jul 13 11:37:01 ubuntu kernel: [    0.466114] pci 0000:00:18.0:   bridge window [io  0x7000-0x7fff]
Jul 13 11:37:01 ubuntu kernel: [    0.466129] pci 0000:00:18.0:   bridge window [mem 0xfd200000-0xfd2fffff]
Jul 13 11:37:01 ubuntu kernel: [    0.466155] pci 0000:00:18.0:   bridge window [mem 0xeb800000-0xeb8fffff 64bit pref]
Jul 13 11:37:01 ubuntu kernel: [    0.466378] pci 0000:00:18.1: PCI bridge to [bus 1c]
Jul 13 11:37:01 ubuntu kernel: [    0.467097] pci 0000:00:18.1:   bridge window [io  0xb000-0xbfff]
Jul 13 11:37:01 ubuntu kernel: [    0.467112] pci 0000:00:18.1:   bridge window [mem 0xfce00000-0xfcefffff]
Jul 13 11:37:01 ubuntu kernel: [    0.467138] pci 0000:00:18.1:   bridge window [mem 0xeb400000-0xeb4fffff 64bit pref]
Jul 13 11:37:01 ubuntu kernel: [    0.467356] pci 0000:00:18.2: PCI bridge to [bus 1d]
Jul 13 11:37:01 ubuntu kernel: [    0.468089] pci 0000:00:18.2:   bridge window [mem 0xfca00000-0xfcafffff]
Jul 13 11:37:01 ubuntu kernel: [    0.468117] pci 0000:00:18.2:   bridge window [mem 0xeb000000-0xeb0fffff 64bit pref]
Jul 13 11:37:01 ubuntu kernel: [    0.468340] pci 0000:00:18.3: PCI bridge to [bus 1e]
Jul 13 11:37:01 ubuntu kernel: [    0.469072] pci 0000:00:18.3:   bridge window [mem 0xfc600000-0xfc6fffff]
Jul 13 11:37:01 ubuntu kernel: [    0.469099] pci 0000:00:18.3:   bridge window [mem 0xeac00000-0xeacfffff 64bit pref]
Jul 13 11:37:01 ubuntu kernel: [    0.469319] pci 0000:00:18.4: PCI bridge to [bus 1f]
Jul 13 11:37:01 ubuntu kernel: [    0.470053] pci 0000:00:18.4:   bridge window [mem 0xfc200000-0xfc2fffff]
Jul 13 11:37:01 ubuntu kernel: [    0.470079] pci 0000:00:18.4:   bridge window [mem 0xea800000-0xea8fffff 64bit pref]
Jul 13 11:37:01 ubuntu kernel: [    0.470331] pci 0000:00:18.5: PCI bridge to [bus 20]
Jul 13 11:37:01 ubuntu kernel: [    0.471066] pci 0000:00:18.5:   bridge window [mem 0xfbe00000-0xfbefffff]
Jul 13 11:37:01 ubuntu kernel: [    0.471093] pci 0000:00:18.5:   bridge window [mem 0xea400000-0xea4fffff 64bit pref]
Jul 13 11:37:01 ubuntu kernel: [    0.471314] pci 0000:00:18.6: PCI bridge to [bus 21]
Jul 13 11:37:01 ubuntu kernel: [    0.472046] pci 0000:00:18.6:   bridge window [mem 0xfba00000-0xfbafffff]
Jul 13 11:37:01 ubuntu kernel: [    0.472073] pci 0000:00:18.6:   bridge window [mem 0xea000000-0xea0fffff 64bit pref]
Jul 13 11:37:01 ubuntu kernel: [    0.472293] pci 0000:00:18.7: PCI bridge to [bus 22]
Jul 13 11:37:01 ubuntu kernel: [    0.473025] pci 0000:00:18.7:   bridge window [mem 0xfb600000-0xfb6fffff]
Jul 13 11:37:01 ubuntu kernel: [    0.473051] pci 0000:00:18.7:   bridge window [mem 0xe9c00000-0xe9cfffff 64bit pref]
Jul 13 11:37:01 ubuntu kernel: [    0.474615] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *9 10 11 14 15)
Jul 13 11:37:01 ubuntu kernel: [    0.476101] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 *11 14 15)
Jul 13 11:37:01 ubuntu kernel: [    0.477581] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 *10 11 14 15)
Jul 13 11:37:01 ubuntu kernel: [    0.479072] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 11 14 15) *0, disabled.
Jul 13 11:37:01 ubuntu kernel: [    0.485059] ACPI: Enabled 2 GPEs in block 00 to 0F
Jul 13 11:37:01 ubuntu kernel: [    0.485915] vgaarb: setting as boot device: PCI:0000:00:0f.0
Jul 13 11:37:01 ubuntu kernel: [    0.486713] vgaarb: device added: PCI:0000:00:0f.0,decodes=io+mem,owns=io+mem,locks=none
Jul 13 11:37:01 ubuntu kernel: [    0.487859] vgaarb: loaded
Jul 13 11:37:01 ubuntu kernel: [    0.488278] vgaarb: bridge control possible 0000:00:0f.0
Jul 13 11:37:01 ubuntu kernel: [    0.489183] SCSI subsystem initialized
Jul 13 11:37:01 ubuntu kernel: [    0.489765] libata version 3.00 loaded.
Jul 13 11:37:01 ubuntu kernel: [    0.489782] ACPI: bus type USB registered
Jul 13 11:37:01 ubuntu kernel: [    0.490391] usbcore: registered new interface driver usbfs
Jul 13 11:37:01 ubuntu kernel: [    0.491176] usbcore: registered new interface driver hub
Jul 13 11:37:01 ubuntu kernel: [    0.491935] usbcore: registered new device driver usb
Jul 13 11:37:01 ubuntu kernel: [    0.492762] PCI: Using ACPI for IRQ routing
Jul 13 11:37:01 ubuntu kernel: [    0.511380] PCI: pci_cache_line_size set to 64 bytes
Jul 13 11:37:01 ubuntu kernel: [    0.511931] e820: reserve RAM buffer [mem 0x0009f800-0x0009ffff]
Jul 13 11:37:01 ubuntu kernel: [    0.511933] e820: reserve RAM buffer [mem 0x3fef0000-0x3fffffff]
Jul 13 11:37:01 ubuntu kernel: [    0.512029] NetLabel: Initializing
Jul 13 11:37:01 ubuntu kernel: [    0.512542] NetLabel:  domain hash size = 128
Jul 13 11:37:01 ubuntu kernel: [    0.513170] NetLabel:  protocols = UNLABELED CIPSOv4
Jul 13 11:37:01 ubuntu kernel: [    0.513882] NetLabel:  unlabeled traffic allowed by default
Jul 13 11:37:01 ubuntu kernel: [    0.514786] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0
Jul 13 11:37:01 ubuntu kernel: [    0.516613] hpet0: 16 comparators, 64-bit 14.318180 MHz counter
Jul 13 11:37:01 ubuntu kernel: [    0.519500] clocksource: Switched to clocksource hpet
Jul 13 11:37:01 ubuntu kernel: [    0.528265] AppArmor: AppArmor Filesystem Enabled
Jul 13 11:37:01 ubuntu kernel: [    0.528992] pnp: PnP ACPI init
Jul 13 11:37:01 ubuntu kernel: [    0.529593] system 00:00: [io  0x1000-0x103f] could not be reserved
Jul 13 11:37:01 ubuntu kernel: [    0.530473] system 00:00: [io  0x1040-0x104f] has been reserved
Jul 13 11:37:01 ubuntu kernel: [    0.532412] system 00:00: [io  0x0cf0-0x0cf1] has been reserved
Jul 13 11:37:01 ubuntu kernel: [    0.533247] system 00:00: Plug and Play ACPI device, IDs PNP0c02 (active)
Jul 13 11:37:01 ubuntu kernel: [    0.533273] pnp 00:01: Plug and Play ACPI device, IDs PNP0b00 (active)
Jul 13 11:37:01 ubuntu kernel: [    0.533289] pnp 00:02: Plug and Play ACPI device, IDs PNP0303 (active)
Jul 13 11:37:01 ubuntu kernel: [    0.533306] pnp 00:03: Plug and Play ACPI device, IDs PNP0f13 (active)
Jul 13 11:37:01 ubuntu kernel: [    0.533447] system 00:04: [mem 0xfed00000-0xfed003ff] has been reserved
Jul 13 11:37:01 ubuntu kernel: [    0.534369] system 00:04: Plug and Play ACPI device, IDs PNP0103 PNP0c01 (active)
Jul 13 11:37:01 ubuntu kernel: [    0.535633] pnp 00:05: Plug and Play ACPI device, IDs PNP0400 (active)
Jul 13 11:37:01 ubuntu kernel: [    0.535789] pnp 00:06: Plug and Play ACPI device, IDs PNP0501 (active)
Jul 13 11:37:01 ubuntu kernel: [    0.535937] pnp 00:07: Plug and Play ACPI device, IDs PNP0501 (active)
Jul 13 11:37:01 ubuntu kernel: [    0.536062] pnp 00:08: [dma 2]
Jul 13 11:37:01 ubuntu kernel: [    0.536089] pnp 00:08: Plug and Play ACPI device, IDs PNP0700 (active)
Jul 13 11:37:01 ubuntu kernel: [    0.536235] system 00:09: [io  0xfce0-0xfcff] has been reserved
Jul 13 11:37:01 ubuntu kernel: [    0.537073] system 00:09: [mem 0xf0000000-0xf7ffffff] has been reserved
Jul 13 11:37:01 ubuntu kernel: [    0.537991] system 00:09: [mem 0xfe800000-0xfe9fffff] has been reserved
Jul 13 11:37:01 ubuntu kernel: [    0.538909] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
Jul 13 11:37:01 ubuntu kernel: [    0.542200] pnp: PnP ACPI: found 10 devices
Jul 13 11:37:01 ubuntu kernel: [    0.548364] clocksource: acpi_pm: mask: 0xffffff max_cycles: 0xffffff, max_idle_ns: 2085701024 ns
Jul 13 11:37:01 ubuntu kernel: [    0.549772] pci 0000:00:15.0: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 03] add_size 200000 add_align 100000
Jul 13 11:37:01 ubuntu kernel: [    0.549892] pci 0000:00:15.3: bridge window [io  0x1000-0x0fff] to [bus 06] add_size 1000
Jul 13 11:37:01 ubuntu kernel: [    0.549933] pci 0000:00:15.4: bridge window [io  0x1000-0x0fff] to [bus 07] add_size 1000
Jul 13 11:37:01 ubuntu kernel: [    0.549975] pci 0000:00:15.5: bridge window [io  0x1000-0x0fff] to [bus 08] add_size 1000
Jul 13 11:37:01 ubuntu kernel: [    0.550016] pci 0000:00:15.6: bridge window [io  0x1000-0x0fff] to [bus 09] add_size 1000
Jul 13 11:37:01 ubuntu kernel: [    0.550057] pci 0000:00:15.7: bridge window [io  0x1000-0x0fff] to [bus 0a] add_size 1000
Jul 13 11:37:01 ubuntu kernel: [    0.550216] pci 0000:00:16.3: bridge window [io  0x1000-0x0fff] to [bus 0e] add_size 1000
Jul 13 11:37:01 ubuntu kernel: [    0.550258] pci 0000:00:16.4: bridge window [io  0x1000-0x0fff] to [bus 0f] add_size 1000
Jul 13 11:37:01 ubuntu kernel: [    0.550299] pci 0000:00:16.5: bridge window [io  0x1000-0x0fff] to [bus 10] add_size 1000
Jul 13 11:37:01 ubuntu kernel: [    0.550340] pci 0000:00:16.6: bridge window [io  0x1000-0x0fff] to [bus 11] add_size 1000
Jul 13 11:37:01 ubuntu kernel: [    0.550382] pci 0000:00:16.7: bridge window [io  0x1000-0x0fff] to [bus 12] add_size 1000
Jul 13 11:37:01 ubuntu kernel: [    0.550540] pci 0000:00:17.3: bridge window [io  0x1000-0x0fff] to [bus 16] add_size 1000
Jul 13 11:37:01 ubuntu kernel: [    0.550581] pci 0000:00:17.4: bridge window [io  0x1000-0x0fff] to [bus 17] add_size 1000
Jul 13 11:37:01 ubuntu kernel: [    0.550622] pci 0000:00:17.5: bridge window [io  0x1000-0x0fff] to [bus 18] add_size 1000
Jul 13 11:37:01 ubuntu kernel: [    0.550669] pci 0000:00:17.6: bridge window [io  0x1000-0x0fff] to [bus 19] add_size 1000
Jul 13 11:37:01 ubuntu kernel: [    0.550710] pci 0000:00:17.7: bridge window [io  0x1000-0x0fff] to [bus 1a] add_size 1000
Jul 13 11:37:01 ubuntu kernel: [    0.550831] pci 0000:00:18.2: bridge window [io  0x1000-0x0fff] to [bus 1d] add_size 1000
Jul 13 11:37:01 ubuntu kernel: [    0.550872] pci 0000:00:18.3: bridge window [io  0x1000-0x0fff] to [bus 1e] add_size 1000
Jul 13 11:37:01 ubuntu kernel: [    0.550913] pci 0000:00:18.4: bridge window [io  0x1000-0x0fff] to [bus 1f] add_size 1000
Jul 13 11:37:01 ubuntu kernel: [    0.550954] pci 0000:00:18.5: bridge window [io  0x1000-0x0fff] to [bus 20] add_size 1000
Jul 13 11:37:01 ubuntu kernel: [    0.550995] pci 0000:00:18.6: bridge window [io  0x1000-0x0fff] to [bus 21] add_size 1000
Jul 13 11:37:01 ubuntu kernel: [    0.551036] pci 0000:00:18.7: bridge window [io  0x1000-0x0fff] to [bus 22] add_size 1000
Jul 13 11:37:01 ubuntu kernel: [    0.551044] pci 0000:00:15.0: res[15]=[mem 0x00100000-0x000fffff 64bit pref] res_to_dev_res add_size 200000 min_align 100000
Jul 13 11:37:01 ubuntu kernel: [    0.551046] pci 0000:00:15.0: res[15]=[mem 0x00100000-0x002fffff 64bit pref] res_to_dev_res add_size 200000 min_align 100000
Jul 13 11:37:01 ubuntu kernel: [    0.551047] pci 0000:00:15.3: res[13]=[io  0x1000-0x0fff] res_to_dev_res add_size 1000 min_align 1000
Jul 13 11:37:01 ubuntu kernel: [    0.551049] pci 0000:00:15.3: res[13]=[io  0x1000-0x1fff] res_to_dev_res add_size 1000 min_align 1000
Jul 13 11:37:01 ubuntu kernel: [    0.551050] pci 0000:00:15.4: res[13]=[io  0x1000-0x0fff] res_to_dev_res add_size 1000 min_align 1000
Jul 13 11:37:01 ubuntu kernel: [    0.551051] pci 0000:00:15.4: res[13]=[io  0x1000-0x1fff] res_to_dev_res add_size 1000 min_align 1000
Jul 13 11:37:01 ubuntu kernel: [    0.551052] pci 0000:00:15.5: res[13]=[io  0x1000-0x0fff] res_to_dev_res add_size 1000 min_align 1000
Jul 13 11:37:01 ubuntu kernel: [    0.551054] pci 0000:00:15.5: res[13]=[io  0x1000-0x1fff] res_to_dev_res add_size 1000 min_align 1000
Jul 13 11:37:01 ubuntu kernel: [    0.551055] pci 0000:00:15.6: res[13]=[io  0x1000-0x0fff] res_to_dev_res add_size 1000 min_align 1000
Jul 13 11:37:01 ubuntu kernel: [    0.551056] pci 0000:00:15.6: res[13]=[io  0x1000-0x1fff] res_to_dev_res add_size 1000 min_align 1000
Jul 13 11:37:01 ubuntu kernel: [    0.551057] pci 0000:00:15.7: res[13]=[io  0x1000-0x0fff] res_to_dev_res add_size 1000 min_align 1000
Jul 13 11:37:01 ubuntu kernel: [    0.551058] pci 0000:00:15.7: res[13]=[io  0x1000-0x1fff] res_to_dev_res add_size 1000 min_align 1000
Jul 13 11:37:01 ubuntu kernel: [    0.551060] pci 0000:00:16.3: res[13]=[io  0x1000-0x0fff] res_to_dev_res add_size 1000 min_align 1000
Jul 13 11:37:01 ubuntu kernel: [    0.551061] pci 0000:00:16.3: res[13]=[io  0x1000-0x1fff] res_to_dev_res add_size 1000 min_align 1000
Jul 13 11:37:01 ubuntu kernel: [    0.551062] pci 0000:00:16.4: res[13]=[io  0x1000-0x0fff] res_to_dev_res add_size 1000 min_align 1000
Jul 13 11:37:01 ubuntu kernel: [    0.551063] pci 0000:00:16.4: res[13]=[io  0x1000-0x1fff] res_to_dev_res add_size 1000 min_align 1000
Jul 13 11:37:01 ubuntu kernel: [    0.551064] pci 0000:00:16.5: res[13]=[io  0x1000-0x0fff] res_to_dev_res add_size 1000 min_align 1000
Jul 13 11:37:01 ubuntu kernel: [    0.551066] pci 0000:00:16.5: res[13]=[io  0x1000-0x1fff] res_to_dev_res add_size 1000 min_align 1000
Jul 13 11:37:01 ubuntu kernel: [    0.551067] pci 0000:00:16.6: res[13]=[io  0x1000-0x0fff] res_to_dev_res add_size 1000 min_align 1000
Jul 13 11:37:01 ubuntu kernel: [    0.551068] pci 0000:00:16.6: res[13]=[io  0x1000-0x1fff] res_to_dev_res add_size 1000 min_align 1000
Jul 13 11:37:01 ubuntu kernel: [    0.551069] pci 0000:00:16.7: res[13]=[io  0x1000-0x0fff] res_to_dev_res add_size 1000 min_align 1000
Jul 13 11:37:01 ubuntu kernel: [    0.551070] pci 0000:00:16.7: res[13]=[io  0x1000-0x1fff] res_to_dev_res add_size 1000 min_align 1000
Jul 13 11:37:01 ubuntu kernel: [    0.551072] pci 0000:00:17.3: res[13]=[io  0x1000-0x0fff] res_to_dev_res add_size 1000 min_align 1000
Jul 13 11:37:01 ubuntu kernel: [    0.551073] pci 0000:00:17.3: res[13]=[io  0x1000-0x1fff] res_to_dev_res add_size 1000 min_align 1000
Jul 13 11:37:01 ubuntu kernel: [    0.551074] pci 0000:00:17.4: res[13]=[io  0x1000-0x0fff] res_to_dev_res add_size 1000 min_align 1000
Jul 13 11:37:01 ubuntu kernel: [    0.551075] pci 0000:00:17.4: res[13]=[io  0x1000-0x1fff] res_to_dev_res add_size 1000 min_align 1000
Jul 13 11:37:01 ubuntu kernel: [    0.551076] pci 0000:00:17.5: res[13]=[io  0x1000-0x0fff] res_to_dev_res add_size 1000 min_align 1000
Jul 13 11:37:01 ubuntu kernel: [    0.551077] pci 0000:00:17.5: res[13]=[io  0x1000-0x1fff] res_to_dev_res add_size 1000 min_align 1000
Jul 13 11:37:01 ubuntu kernel: [    0.551079] pci 0000:00:17.6: res[13]=[io  0x1000-0x0fff] res_to_dev_res add_size 1000 min_align 1000
Jul 13 11:37:01 ubuntu kernel: [    0.551080] pci 0000:00:17.6: res[13]=[io  0x1000-0x1fff] res_to_dev_res add_size 1000 min_align 1000
Jul 13 11:37:01 ubuntu kernel: [    0.551081] pci 0000:00:17.7: res[13]=[io  0x1000-0x0fff] res_to_dev_res add_size 1000 min_align 1000
Jul 13 11:37:01 ubuntu kernel: [    0.551082] pci 0000:00:17.7: res[13]=[io  0x1000-0x1fff] res_to_dev_res add_size 1000 min_align 1000
Jul 13 11:37:01 ubuntu kernel: [    0.551084] pci 0000:00:18.2: res[13]=[io  0x1000-0x0fff] res_to_dev_res add_size 1000 min_align 1000
Jul 13 11:37:01 ubuntu kernel: [    0.551085] pci 0000:00:18.2: res[13]=[io  0x1000-0x1fff] res_to_dev_res add_size 1000 min_align 1000
Jul 13 11:37:01 ubuntu kernel: [    0.551086] pci 0000:00:18.3: res[13]=[io  0x1000-0x0fff] res_to_dev_res add_size 1000 min_align 1000
Jul 13 11:37:01 ubuntu kernel: [    0.551087] pci 0000:00:18.3: res[13]=[io  0x1000-0x1fff] res_to_dev_res add_size 1000 min_align 1000
Jul 13 11:37:01 ubuntu kernel: [    0.551088] pci 0000:00:18.4: res[13]=[io  0x1000-0x0fff] res_to_dev_res add_size 1000 min_align 1000
Jul 13 11:37:01 ubuntu kernel: [    0.551090] pci 0000:00:18.4: res[13]=[io  0x1000-0x1fff] res_to_dev_res add_size 1000 min_align 1000
Jul 13 11:37:01 ubuntu kernel: [    0.551091] pci 0000:00:18.5: res[13]=[io  0x1000-0x0fff] res_to_dev_res add_size 1000 min_align 1000
Jul 13 11:37:01 ubuntu kernel: [    0.551092] pci 0000:00:18.5: res[13]=[io  0x1000-0x1fff] res_to_dev_res add_size 1000 min_align 1000
Jul 13 11:37:01 ubuntu kernel: [    0.551093] pci 0000:00:18.6: res[13]=[io  0x1000-0x0fff] res_to_dev_res add_size 1000 min_align 1000
Jul 13 11:37:01 ubuntu kernel: [    0.551094] pci 0000:00:18.6: res[13]=[io  0x1000-0x1fff] res_to_dev_res add_size 1000 min_align 1000
Jul 13 11:37:01 ubuntu kernel: [    0.551096] pci 0000:00:18.7: res[13]=[io  0x1000-0x0fff] res_to_dev_res add_size 1000 min_align 1000
Jul 13 11:37:01 ubuntu kernel: [    0.551097] pci 0000:00:18.7: res[13]=[io  0x1000-0x1fff] res_to_dev_res add_size 1000 min_align 1000
Jul 13 11:37:01 ubuntu kernel: [    0.551103] pci 0000:00:15.0: BAR 15: assigned [mem 0x40000000-0x401fffff 64bit pref]
Jul 13 11:37:01 ubuntu kernel: [    0.552264] pci 0000:00:0f.0: BAR 6: assigned [mem 0x40200000-0x40207fff pref]
Jul 13 11:37:01 ubuntu kernel: [    0.553379] pci 0000:00:10.0: BAR 6: assigned [mem 0x40208000-0x4020bfff pref]
Jul 13 11:37:01 ubuntu kernel: [    0.554446] pci 0000:00:15.3: BAR 13: no space for [io  size 0x1000]
Jul 13 11:37:01 ubuntu kernel: [    0.555366] pci 0000:00:15.3: BAR 13: failed to assign [io  size 0x1000]
Jul 13 11:37:01 ubuntu kernel: [    0.556337] pci 0000:00:15.4: BAR 13: no space for [io  size 0x1000]
Jul 13 11:37:01 ubuntu kernel: [    0.557251] pci 0000:00:15.4: BAR 13: failed to assign [io  size 0x1000]
Jul 13 11:37:01 ubuntu kernel: [    0.558229] pci 0000:00:15.5: BAR 13: no space for [io  size 0x1000]
Jul 13 11:37:01 ubuntu kernel: [    0.559177] pci 0000:00:15.5: BAR 13: failed to assign [io  size 0x1000]
Jul 13 11:37:01 ubuntu kernel: [    0.560144] pci 0000:00:15.6: BAR 13: no space for [io  size 0x1000]
Jul 13 11:37:01 ubuntu kernel: [    0.561130] pci 0000:00:15.6: BAR 13: failed to assign [io  size 0x1000]
Jul 13 11:37:01 ubuntu kernel: [    0.562087] pci 0000:00:15.7: BAR 13: no space for [io  size 0x1000]
Jul 13 11:37:01 ubuntu kernel: [    0.563022] pci 0000:00:15.7: BAR 13: failed to assign [io  size 0x1000]
Jul 13 11:37:01 ubuntu kernel: [    0.564061] pci 0000:00:16.3: BAR 13: no space for [io  size 0x1000]
Jul 13 11:37:01 ubuntu kernel: [    0.565010] pci 0000:00:16.3: BAR 13: failed to assign [io  size 0x1000]
Jul 13 11:37:01 ubuntu kernel: [    0.566326] pci 0000:00:16.4: BAR 13: no space for [io  size 0x1000]
Jul 13 11:37:01 ubuntu kernel: [    0.567267] pci 0000:00:16.4: BAR 13: failed to assign [io  size 0x1000]
Jul 13 11:37:01 ubuntu kernel: [    0.568264] pci 0000:00:16.5: BAR 13: no space for [io  size 0x1000]
Jul 13 11:37:01 ubuntu kernel: [    0.569217] pci 0000:00:16.5: BAR 13: failed to assign [io  size 0x1000]
Jul 13 11:37:01 ubuntu kernel: [    0.570190] pci 0000:00:16.6: BAR 13: no space for [io  size 0x1000]
Jul 13 11:37:01 ubuntu kernel: [    0.571114] pci 0000:00:16.6: BAR 13: failed to assign [io  size 0x1000]
Jul 13 11:37:01 ubuntu kernel: [    0.572080] pci 0000:00:16.7: BAR 13: no space for [io  size 0x1000]
Jul 13 11:37:01 ubuntu kernel: [    0.572997] pci 0000:00:16.7: BAR 13: failed to assign [io  size 0x1000]
Jul 13 11:37:01 ubuntu kernel: [    0.573951] pci 0000:00:17.3: BAR 13: no space for [io  size 0x1000]
Jul 13 11:37:01 ubuntu kernel: [    0.574860] pci 0000:00:17.3: BAR 13: failed to assign [io  size 0x1000]
Jul 13 11:37:01 ubuntu kernel: [    0.575827] pci 0000:00:17.4: BAR 13: no space for [io  size 0x1000]
Jul 13 11:37:01 ubuntu kernel: [    0.576738] pci 0000:00:17.4: BAR 13: failed to assign [io  size 0x1000]
Jul 13 11:37:01 ubuntu kernel: [    0.577750] pci 0000:00:17.5: BAR 13: no space for [io  size 0x1000]
Jul 13 11:37:01 ubuntu kernel: [    0.578666] pci 0000:00:17.5: BAR 13: failed to assign [io  size 0x1000]
Jul 13 11:37:01 ubuntu kernel: [    0.579656] pci 0000:00:17.6: BAR 13: no space for [io  size 0x1000]
Jul 13 11:37:01 ubuntu kernel: [    0.580568] pci 0000:00:17.6: BAR 13: failed to assign [io  size 0x1000]
Jul 13 11:37:01 ubuntu kernel: [    0.581548] pci 0000:00:17.7: BAR 13: no space for [io  size 0x1000]
Jul 13 11:37:01 ubuntu kernel: [    0.582459] pci 0000:00:17.7: BAR 13: failed to assign [io  size 0x1000]
Jul 13 11:37:01 ubuntu kernel: [    0.583452] pci 0000:00:18.2: BAR 13: no space for [io  size 0x1000]
Jul 13 11:37:01 ubuntu kernel: [    0.584428] pci 0000:00:18.2: BAR 13: failed to assign [io  size 0x1000]
Jul 13 11:37:01 ubuntu kernel: [    0.585388] pci 0000:00:18.3: BAR 13: no space for [io  size 0x1000]
Jul 13 11:37:01 ubuntu kernel: [    0.586299] pci 0000:00:18.3: BAR 13: failed to assign [io  size 0x1000]
Jul 13 11:37:01 ubuntu kernel: [    0.587255] pci 0000:00:18.4: BAR 13: no space for [io  size 0x1000]
Jul 13 11:37:01 ubuntu kernel: [    0.588177] pci 0000:00:18.4: BAR 13: failed to assign [io  size 0x1000]
Jul 13 11:37:01 ubuntu kernel: [    0.589167] pci 0000:00:18.5: BAR 13: no space for [io  size 0x1000]
Jul 13 11:37:01 ubuntu kernel: [    0.590110] pci 0000:00:18.5: BAR 13: failed to assign [io  size 0x1000]
Jul 13 11:37:01 ubuntu kernel: [    0.591094] pci 0000:00:18.6: BAR 13: no space for [io  size 0x1000]
Jul 13 11:37:01 ubuntu kernel: [    0.592016] pci 0000:00:18.6: BAR 13: failed to assign [io  size 0x1000]
Jul 13 11:37:01 ubuntu kernel: [    0.592999] pci 0000:00:18.7: BAR 13: no space for [io  size 0x1000]
Jul 13 11:37:01 ubuntu kernel: [    0.593948] pci 0000:00:18.7: BAR 13: failed to assign [io  size 0x1000]
Jul 13 11:37:01 ubuntu kernel: [    0.594961] pci 0000:00:18.7: BAR 13: no space for [io  size 0x1000]
Jul 13 11:37:01 ubuntu kernel: [    0.595914] pci 0000:00:18.7: BAR 13: failed to assign [io  size 0x1000]
Jul 13 11:37:01 ubuntu kernel: [    0.596903] pci 0000:00:18.6: BAR 13: no space for [io  size 0x1000]
Jul 13 11:37:01 ubuntu kernel: [    0.597851] pci 0000:00:18.6: BAR 13: failed to assign [io  size 0x1000]
Jul 13 11:37:01 ubuntu kernel: [    0.598840] pci 0000:00:18.5: BAR 13: no space for [io  size 0x1000]
Jul 13 11:37:01 ubuntu kernel: [    0.599791] pci 0000:00:18.5: BAR 13: failed to assign [io  size 0x1000]
Jul 13 11:37:01 ubuntu kernel: [    0.600813] pci 0000:00:18.4: BAR 13: no space for [io  size 0x1000]
Jul 13 11:37:01 ubuntu kernel: [    0.601726] pci 0000:00:18.4: BAR 13: failed to assign [io  size 0x1000]
Jul 13 11:37:01 ubuntu kernel: [    0.602712] pci 0000:00:18.3: BAR 13: no space for [io  size 0x1000]
Jul 13 11:37:01 ubuntu kernel: [    0.603609] pci 0000:00:18.3: BAR 13: failed to assign [io  size 0x1000]
Jul 13 11:37:01 ubuntu kernel: [    0.604539] pci 0000:00:18.2: BAR 13: no space for [io  size 0x1000]
Jul 13 11:37:01 ubuntu kernel: [    0.605462] pci 0000:00:18.2: BAR 13: failed to assign [io  size 0x1000]
Jul 13 11:37:01 ubuntu kernel: [    0.606467] pci 0000:00:17.7: BAR 13: no space for [io  size 0x1000]
Jul 13 11:37:01 ubuntu kernel: [    0.607416] pci 0000:00:17.7: BAR 13: failed to assign [io  size 0x1000]
Jul 13 11:37:01 ubuntu kernel: [    0.608415] pci 0000:00:17.6: BAR 13: no space for [io  size 0x1000]
Jul 13 11:37:01 ubuntu kernel: [    0.609357] pci 0000:00:17.6: BAR 13: failed to assign [io  size 0x1000]
Jul 13 11:37:01 ubuntu kernel: [    0.610343] pci 0000:00:17.5: BAR 13: no space for [io  size 0x1000]
Jul 13 11:37:01 ubuntu kernel: [    0.611287] pci 0000:00:17.5: BAR 13: failed to assign [io  size 0x1000]
Jul 13 11:37:01 ubuntu kernel: [    0.612295] pci 0000:00:17.4: BAR 13: no space for [io  size 0x1000]
Jul 13 11:37:01 ubuntu kernel: [    0.613287] pci 0000:00:17.4: BAR 13: failed to assign [io  size 0x1000]
Jul 13 11:37:01 ubuntu kernel: [    0.614278] pci 0000:00:17.3: BAR 13: no space for [io  size 0x1000]
Jul 13 11:37:01 ubuntu kernel: [    0.615219] pci 0000:00:17.3: BAR 13: failed to assign [io  size 0x1000]
Jul 13 11:37:01 ubuntu kernel: [    0.616244] pci 0000:00:16.7: BAR 13: no space for [io  size 0x1000]
Jul 13 11:37:01 ubuntu kernel: [    0.617184] pci 0000:00:16.7: BAR 13: failed to assign [io  size 0x1000]
Jul 13 11:37:01 ubuntu kernel: [    0.618171] pci 0000:00:16.6: BAR 13: no space for [io  size 0x1000]
Jul 13 11:37:01 ubuntu kernel: [    0.619108] pci 0000:00:16.6: BAR 13: failed to assign [io  size 0x1000]
Jul 13 11:37:01 ubuntu kernel: [    0.620099] pci 0000:00:16.5: BAR 13: no space for [io  size 0x1000]
Jul 13 11:37:01 ubuntu kernel: [    0.621051] pci 0000:00:16.5: BAR 13: failed to assign [io  size 0x1000]
Jul 13 11:37:01 ubuntu kernel: [    0.622064] pci 0000:00:16.4: BAR 13: no space for [io  size 0x1000]
Jul 13 11:37:01 ubuntu kernel: [    0.623023] pci 0000:00:16.4: BAR 13: failed to assign [io  size 0x1000]
Jul 13 11:37:01 ubuntu kernel: [    0.624014] pci 0000:00:16.3: BAR 13: no space for [io  size 0x1000]
Jul 13 11:37:01 ubuntu kernel: [    0.624946] pci 0000:00:16.3: BAR 13: failed to assign [io  size 0x1000]
Jul 13 11:37:01 ubuntu kernel: [    0.625938] pci 0000:00:15.7: BAR 13: no space for [io  size 0x1000]
Jul 13 11:37:01 ubuntu kernel: [    0.626890] pci 0000:00:15.7: BAR 13: failed to assign [io  size 0x1000]
Jul 13 11:37:01 ubuntu kernel: [    0.627910] pci 0000:00:15.6: BAR 13: no space for [io  size 0x1000]
Jul 13 11:37:01 ubuntu kernel: [    0.628845] pci 0000:00:15.6: BAR 13: failed to assign [io  size 0x1000]
Jul 13 11:37:01 ubuntu kernel: [    0.629864] pci 0000:00:15.5: BAR 13: no space for [io  size 0x1000]
Jul 13 11:37:01 ubuntu kernel: [    0.630815] pci 0000:00:15.5: BAR 13: failed to assign [io  size 0x1000]
Jul 13 11:37:01 ubuntu kernel: [    0.631793] pci 0000:00:15.4: BAR 13: no space for [io  size 0x1000]
Jul 13 11:37:01 ubuntu kernel: [    0.632727] pci 0000:00:15.4: BAR 13: failed to assign [io  size 0x1000]
Jul 13 11:37:01 ubuntu kernel: [    0.633695] pci 0000:00:15.3: BAR 13: no space for [io  size 0x1000]
Jul 13 11:37:01 ubuntu kernel: [    0.634653] pci 0000:00:15.3: BAR 13: failed to assign [io  size 0x1000]
Jul 13 11:37:01 ubuntu kernel: [    0.635618] pci 0000:00:01.0: PCI bridge to [bus 01]
Jul 13 11:37:01 ubuntu kernel: [    0.636414] pci 0000:00:11.0: PCI bridge to [bus 02]
Jul 13 11:37:01 ubuntu kernel: [    0.637150] pci 0000:00:11.0:   bridge window [io  0x2000-0x3fff]
Jul 13 11:37:01 ubuntu kernel: [    0.638063] pci 0000:00:11.0:   bridge window [mem 0xfd600000-0xfdffffff]
Jul 13 11:37:01 ubuntu kernel: [    0.639053] pci 0000:00:11.0:   bridge window [mem 0xebb00000-0xebffffff 64bit pref]
Jul 13 11:37:01 ubuntu kernel: [    0.640255] pci 0000:03:00.0: BAR 6: assigned [mem 0xfd500000-0xfd50ffff pref]
Jul 13 11:37:01 ubuntu kernel: [    0.641356] pci 0000:00:15.0: PCI bridge to [bus 03]
Jul 13 11:37:01 ubuntu kernel: [    0.642082] pci 0000:00:15.0:   bridge window [io  0x4000-0x4fff]
Jul 13 11:37:01 ubuntu kernel: [    0.642950] pci 0000:00:15.0:   bridge window [mem 0xfd500000-0xfd5fffff]
Jul 13 11:37:01 ubuntu kernel: [    0.643911] pci 0000:00:15.0:   bridge window [mem 0x40000000-0x401fffff 64bit pref]
Jul 13 11:37:01 ubuntu kernel: [    0.645058] pci 0000:00:15.1: PCI bridge to [bus 04]
Jul 13 11:37:01 ubuntu kernel: [    0.645772] pci 0000:00:15.1:   bridge window [io  0x8000-0x8fff]
Jul 13 11:37:01 ubuntu kernel: [    0.646645] pci 0000:00:15.1:   bridge window [mem 0xfd100000-0xfd1fffff]
Jul 13 11:37:01 ubuntu kernel: [    0.647605] pci 0000:00:15.1:   bridge window [mem 0xeb700000-0xeb7fffff 64bit pref]
Jul 13 11:37:01 ubuntu kernel: [    0.648735] pci 0000:00:15.2: PCI bridge to [bus 05]
Jul 13 11:37:01 ubuntu kernel: [    0.649450] pci 0000:00:15.2:   bridge window [io  0xc000-0xcfff]
Jul 13 11:37:01 ubuntu kernel: [    0.650323] pci 0000:00:15.2:   bridge window [mem 0xfcd00000-0xfcdfffff]
Jul 13 11:37:01 ubuntu kernel: [    0.651281] pci 0000:00:15.2:   bridge window [mem 0xeb300000-0xeb3fffff 64bit pref]
Jul 13 11:37:01 ubuntu kernel: [    0.652424] pci 0000:00:15.3: PCI bridge to [bus 06]
Jul 13 11:37:01 ubuntu kernel: [    0.653182] pci 0000:00:15.3:   bridge window [mem 0xfc900000-0xfc9fffff]
Jul 13 11:37:01 ubuntu kernel: [    0.654133] pci 0000:00:15.3:   bridge window [mem 0xeaf00000-0xeaffffff 64bit pref]
Jul 13 11:37:01 ubuntu kernel: [    0.655287] pci 0000:00:15.4: PCI bridge to [bus 07]
Jul 13 11:37:01 ubuntu kernel: [    0.656032] pci 0000:00:15.4:   bridge window [mem 0xfc500000-0xfc5fffff]
Jul 13 11:37:01 ubuntu kernel: [    0.656983] pci 0000:00:15.4:   bridge window [mem 0xeab00000-0xeabfffff 64bit pref]
Jul 13 11:37:01 ubuntu kernel: [    0.658120] pci 0000:00:15.5: PCI bridge to [bus 08]
Jul 13 11:37:01 ubuntu kernel: [    0.658846] pci 0000:00:15.5:   bridge window [mem 0xfc100000-0xfc1fffff]
Jul 13 11:37:01 ubuntu kernel: [    0.659810] pci 0000:00:15.5:   bridge window [mem 0xea700000-0xea7fffff 64bit pref]
Jul 13 11:37:01 ubuntu kernel: [    0.660943] pci 0000:00:15.6: PCI bridge to [bus 09]
Jul 13 11:37:01 ubuntu kernel: [    0.661668] pci 0000:00:15.6:   bridge window [mem 0xfbd00000-0xfbdfffff]
Jul 13 11:37:01 ubuntu kernel: [    0.662618] pci 0000:00:15.6:   bridge window [mem 0xea300000-0xea3fffff 64bit pref]
Jul 13 11:37:01 ubuntu kernel: [    0.663758] pci 0000:00:15.7: PCI bridge to [bus 0a]
Jul 13 11:37:01 ubuntu kernel: [    0.664486] pci 0000:00:15.7:   bridge window [mem 0xfb900000-0xfb9fffff]
Jul 13 11:37:01 ubuntu kernel: [    0.665437] pci 0000:00:15.7:   bridge window [mem 0xe9f00000-0xe9ffffff 64bit pref]
Jul 13 11:37:01 ubuntu kernel: [    0.666568] pci 0000:00:16.0: PCI bridge to [bus 0b]
Jul 13 11:37:01 ubuntu kernel: [    0.667282] pci 0000:00:16.0:   bridge window [io  0x5000-0x5fff]
Jul 13 11:37:01 ubuntu kernel: [    0.668161] pci 0000:00:16.0:   bridge window [mem 0xfd400000-0xfd4fffff]
Jul 13 11:37:01 ubuntu kernel: [    0.669112] pci 0000:00:16.0:   bridge window [mem 0xeba00000-0xebafffff 64bit pref]
Jul 13 11:37:01 ubuntu kernel: [    0.670251] pci 0000:00:16.1: PCI bridge to [bus 0c]
Jul 13 11:37:01 ubuntu kernel: [    0.670992] pci 0000:00:16.1:   bridge window [io  0x9000-0x9fff]
Jul 13 11:37:01 ubuntu kernel: [    0.671870] pci 0000:00:16.1:   bridge window [mem 0xfd000000-0xfd0fffff]
Jul 13 11:37:01 ubuntu kernel: [    0.672818] pci 0000:00:16.1:   bridge window [mem 0xeb600000-0xeb6fffff 64bit pref]
Jul 13 11:37:01 ubuntu kernel: [    0.673946] pci 0000:00:16.2: PCI bridge to [bus 0d]
Jul 13 11:37:01 ubuntu kernel: [    0.674658] pci 0000:00:16.2:   bridge window [io  0xd000-0xdfff]
Jul 13 11:37:01 ubuntu kernel: [    0.675534] pci 0000:00:16.2:   bridge window [mem 0xfcc00000-0xfccfffff]
Jul 13 11:37:01 ubuntu kernel: [    0.676483] pci 0000:00:16.2:   bridge window [mem 0xeb200000-0xeb2fffff 64bit pref]
Jul 13 11:37:01 ubuntu kernel: [    0.677608] pci 0000:00:16.3: PCI bridge to [bus 0e]
Jul 13 11:37:01 ubuntu kernel: [    0.678332] pci 0000:00:16.3:   bridge window [mem 0xfc800000-0xfc8fffff]
Jul 13 11:37:01 ubuntu kernel: [    0.679280] pci 0000:00:16.3:   bridge window [mem 0xeae00000-0xeaefffff 64bit pref]
Jul 13 11:37:01 ubuntu kernel: [    0.680445] pci 0000:00:16.4: PCI bridge to [bus 0f]
Jul 13 11:37:01 ubuntu kernel: [    0.681195] pci 0000:00:16.4:   bridge window [mem 0xfc400000-0xfc4fffff]
Jul 13 11:37:01 ubuntu kernel: [    0.682145] pci 0000:00:16.4:   bridge window [mem 0xeaa00000-0xeaafffff 64bit pref]
Jul 13 11:37:01 ubuntu kernel: [    0.683273] pci 0000:00:16.5: PCI bridge to [bus 10]
Jul 13 11:37:01 ubuntu kernel: [    0.684016] pci 0000:00:16.5:   bridge window [mem 0xfc000000-0xfc0fffff]
Jul 13 11:37:01 ubuntu kernel: [    0.684970] pci 0000:00:16.5:   bridge window [mem 0xea600000-0xea6fffff 64bit pref]
Jul 13 11:37:01 ubuntu kernel: [    0.686099] pci 0000:00:16.6: PCI bridge to [bus 11]
Jul 13 11:37:01 ubuntu kernel: [    0.686823] pci 0000:00:16.6:   bridge window [mem 0xfbc00000-0xfbcfffff]
Jul 13 11:37:01 ubuntu kernel: [    0.687784] pci 0000:00:16.6:   bridge window [mem 0xea200000-0xea2fffff 64bit pref]
Jul 13 11:37:01 ubuntu kernel: [    0.688918] pci 0000:00:16.7: PCI bridge to [bus 12]
Jul 13 11:37:01 ubuntu kernel: [    0.689644] pci 0000:00:16.7:   bridge window [mem 0xfb800000-0xfb8fffff]
Jul 13 11:37:01 ubuntu kernel: [    0.690951] pci 0000:00:16.7:   bridge window [mem 0xe9e00000-0xe9efffff 64bit pref]
Jul 13 11:37:01 ubuntu kernel: [    0.692093] pci 0000:00:17.0: PCI bridge to [bus 13]
Jul 13 11:37:01 ubuntu kernel: [    0.692807] pci 0000:00:17.0:   bridge window [io  0x6000-0x6fff]
Jul 13 11:37:01 ubuntu kernel: [    0.693675] pci 0000:00:17.0:   bridge window [mem 0xfd300000-0xfd3fffff]
Jul 13 11:37:01 ubuntu kernel: [    0.694626] pci 0000:00:17.0:   bridge window [mem 0xeb900000-0xeb9fffff 64bit pref]
Jul 13 11:37:01 ubuntu kernel: [    0.696875] pci 0000:00:17.1: PCI bridge to [bus 14]
Jul 13 11:37:01 ubuntu kernel: [    0.697589] pci 0000:00:17.1:   bridge window [io  0xa000-0xafff]
Jul 13 11:37:01 ubuntu kernel: [    0.698458] pci 0000:00:17.1:   bridge window [mem 0xfcf00000-0xfcffffff]
Jul 13 11:37:01 ubuntu kernel: [    0.699413] pci 0000:00:17.1:   bridge window [mem 0xeb500000-0xeb5fffff 64bit pref]
Jul 13 11:37:01 ubuntu kernel: [    0.700560] pci 0000:00:17.2: PCI bridge to [bus 15]
Jul 13 11:37:01 ubuntu kernel: [    0.701282] pci 0000:00:17.2:   bridge window [io  0xe000-0xefff]
Jul 13 11:37:01 ubuntu kernel: [    0.702150] pci 0000:00:17.2:   bridge window [mem 0xfcb00000-0xfcbfffff]
Jul 13 11:37:01 ubuntu kernel: [    0.703128] pci 0000:00:17.2:   bridge window [mem 0xeb100000-0xeb1fffff 64bit pref]
Jul 13 11:37:01 ubuntu kernel: [    0.704272] pci 0000:00:17.3: PCI bridge to [bus 16]
Jul 13 11:37:01 ubuntu kernel: [    0.705019] pci 0000:00:17.3:   bridge window [mem 0xfc700000-0xfc7fffff]
Jul 13 11:37:01 ubuntu kernel: [    0.705970] pci 0000:00:17.3:   bridge window [mem 0xead00000-0xeadfffff 64bit pref]
Jul 13 11:37:01 ubuntu kernel: [    0.707101] pci 0000:00:17.4: PCI bridge to [bus 17]
Jul 13 11:37:01 ubuntu kernel: [    0.707841] pci 0000:00:17.4:   bridge window [mem 0xfc300000-0xfc3fffff]
Jul 13 11:37:01 ubuntu kernel: [    0.708792] pci 0000:00:17.4:   bridge window [mem 0xea900000-0xea9fffff 64bit pref]
Jul 13 11:37:01 ubuntu kernel: [    0.709922] pci 0000:00:17.5: PCI bridge to [bus 18]
Jul 13 11:37:01 ubuntu kernel: [    0.710650] pci 0000:00:17.5:   bridge window [mem 0xfbf00000-0xfbffffff]
Jul 13 11:37:01 ubuntu kernel: [    0.711611] pci 0000:00:17.5:   bridge window [mem 0xea500000-0xea5fffff 64bit pref]
Jul 13 11:37:01 ubuntu kernel: [    0.712748] pci 0000:00:17.6: PCI bridge to [bus 19]
Jul 13 11:37:01 ubuntu kernel: [    0.713480] pci 0000:00:17.6:   bridge window [mem 0xfbb00000-0xfbbfffff]
Jul 13 11:37:01 ubuntu kernel: [    0.714431] pci 0000:00:17.6:   bridge window [mem 0xea100000-0xea1fffff 64bit pref]
Jul 13 11:37:01 ubuntu kernel: [    0.715569] pci 0000:00:17.7: PCI bridge to [bus 1a]
Jul 13 11:37:01 ubuntu kernel: [    0.716295] pci 0000:00:17.7:   bridge window [mem 0xfb700000-0xfb7fffff]
Jul 13 11:37:01 ubuntu kernel: [    0.717242] pci 0000:00:17.7:   bridge window [mem 0xe9d00000-0xe9dfffff 64bit pref]
Jul 13 11:37:01 ubuntu kernel: [    0.718371] pci 0000:00:18.0: PCI bridge to [bus 1b]
Jul 13 11:37:01 ubuntu kernel: [    0.719084] pci 0000:00:18.0:   bridge window [io  0x7000-0x7fff]
Jul 13 11:37:01 ubuntu kernel: [    0.719964] pci 0000:00:18.0:   bridge window [mem 0xfd200000-0xfd2fffff]
Jul 13 11:37:01 ubuntu kernel: [    0.720919] pci 0000:00:18.0:   bridge window [mem 0xeb800000-0xeb8fffff 64bit pref]
Jul 13 11:37:01 ubuntu kernel: [    0.722047] pci 0000:00:18.1: PCI bridge to [bus 1c]
Jul 13 11:37:01 ubuntu kernel: [    0.722760] pci 0000:00:18.1:   bridge window [io  0xb000-0xbfff]
Jul 13 11:37:01 ubuntu kernel: [    0.723639] pci 0000:00:18.1:   bridge window [mem 0xfce00000-0xfcefffff]
Jul 13 11:37:01 ubuntu kernel: [    0.724590] pci 0000:00:18.1:   bridge window [mem 0xeb400000-0xeb4fffff 64bit pref]
Jul 13 11:37:01 ubuntu kernel: [    0.725720] pci 0000:00:18.2: PCI bridge to [bus 1d]
Jul 13 11:37:01 ubuntu kernel: [    0.726445] pci 0000:00:18.2:   bridge window [mem 0xfca00000-0xfcafffff]
Jul 13 11:37:01 ubuntu kernel: [    0.727395] pci 0000:00:18.2:   bridge window [mem 0xeb000000-0xeb0fffff 64bit pref]
Jul 13 11:37:01 ubuntu kernel: [    0.728541] pci 0000:00:18.3: PCI bridge to [bus 1e]
Jul 13 11:37:01 ubuntu kernel: [    0.729267] pci 0000:00:18.3:   bridge window [mem 0xfc600000-0xfc6fffff]
Jul 13 11:37:01 ubuntu kernel: [    0.730216] pci 0000:00:18.3:   bridge window [mem 0xeac00000-0xeacfffff 64bit pref]
Jul 13 11:37:01 ubuntu kernel: [    0.731346] pci 0000:00:18.4: PCI bridge to [bus 1f]
Jul 13 11:37:01 ubuntu kernel: [    0.732084] pci 0000:00:18.4:   bridge window [mem 0xfc200000-0xfc2fffff]
Jul 13 11:37:01 ubuntu kernel: [    0.733034] pci 0000:00:18.4:   bridge window [mem 0xea800000-0xea8fffff 64bit pref]
Jul 13 11:37:01 ubuntu kernel: [    0.734164] pci 0000:00:18.5: PCI bridge to [bus 20]
Jul 13 11:37:01 ubuntu kernel: [    0.734890] pci 0000:00:18.5:   bridge window [mem 0xfbe00000-0xfbefffff]
Jul 13 11:37:01 ubuntu kernel: [    0.735852] pci 0000:00:18.5:   bridge window [mem 0xea400000-0xea4fffff 64bit pref]
Jul 13 11:37:01 ubuntu kernel: [    0.737037] pci 0000:00:18.6: PCI bridge to [bus 21]
Jul 13 11:37:01 ubuntu kernel: [    0.737764] pci 0000:00:18.6:   bridge window [mem 0xfba00000-0xfbafffff]
Jul 13 11:37:01 ubuntu kernel: [    0.738712] pci 0000:00:18.6:   bridge window [mem 0xea000000-0xea0fffff 64bit pref]
Jul 13 11:37:01 ubuntu kernel: [    0.739859] pci 0000:00:18.7: PCI bridge to [bus 22]
Jul 13 11:37:01 ubuntu kernel: [    0.740586] pci 0000:00:18.7:   bridge window [mem 0xfb600000-0xfb6fffff]
Jul 13 11:37:01 ubuntu kernel: [    0.741541] pci 0000:00:18.7:   bridge window [mem 0xe9c00000-0xe9cfffff 64bit pref]
Jul 13 11:37:01 ubuntu kernel: [    0.742700] pci_bus 0000:00: resource 4 [mem 0x000a0000-0x000bffff window]
Jul 13 11:37:01 ubuntu kernel: [    0.742701] pci_bus 0000:00: resource 5 [mem 0x000cc000-0x000cffff window]
Jul 13 11:37:01 ubuntu kernel: [    0.742702] pci_bus 0000:00: resource 6 [mem 0x000d0000-0x000d3fff window]
Jul 13 11:37:01 ubuntu kernel: [    0.742703] pci_bus 0000:00: resource 7 [mem 0x000d4000-0x000d7fff window]
Jul 13 11:37:01 ubuntu kernel: [    0.742704] pci_bus 0000:00: resource 8 [mem 0x000d8000-0x000dbfff window]
Jul 13 11:37:01 ubuntu kernel: [    0.742706] pci_bus 0000:00: resource 9 [mem 0x40000000-0xfebfffff window]
Jul 13 11:37:01 ubuntu kernel: [    0.742707] pci_bus 0000:00: resource 10 [io  0x0000-0x0cf7 window]
Jul 13 11:37:01 ubuntu kernel: [    0.742708] pci_bus 0000:00: resource 11 [io  0x0d00-0xfeff window]
Jul 13 11:37:01 ubuntu kernel: [    0.742709] pci_bus 0000:02: resource 0 [io  0x2000-0x3fff]
Jul 13 11:37:01 ubuntu kernel: [    0.742711] pci_bus 0000:02: resource 1 [mem 0xfd600000-0xfdffffff]
Jul 13 11:37:01 ubuntu kernel: [    0.742712] pci_bus 0000:02: resource 2 [mem 0xebb00000-0xebffffff 64bit pref]
Jul 13 11:37:01 ubuntu kernel: [    0.742713] pci_bus 0000:02: resource 4 [mem 0x000a0000-0x000bffff window]
Jul 13 11:37:01 ubuntu kernel: [    0.742714] pci_bus 0000:02: resource 5 [mem 0x000cc000-0x000cffff window]
Jul 13 11:37:01 ubuntu kernel: [    0.742715] pci_bus 0000:02: resource 6 [mem 0x000d0000-0x000d3fff window]
Jul 13 11:37:01 ubuntu kernel: [    0.742716] pci_bus 0000:02: resource 7 [mem 0x000d4000-0x000d7fff window]
Jul 13 11:37:01 ubuntu kernel: [    0.742717] pci_bus 0000:02: resource 8 [mem 0x000d8000-0x000dbfff window]
Jul 13 11:37:01 ubuntu kernel: [    0.742718] pci_bus 0000:02: resource 9 [mem 0x40000000-0xfebfffff window]
Jul 13 11:37:01 ubuntu kernel: [    0.742719] pci_bus 0000:02: resource 10 [io  0x0000-0x0cf7 window]
Jul 13 11:37:01 ubuntu kernel: [    0.742720] pci_bus 0000:02: resource 11 [io  0x0d00-0xfeff window]
Jul 13 11:37:01 ubuntu kernel: [    0.742721] pci_bus 0000:03: resource 0 [io  0x4000-0x4fff]
Jul 13 11:37:01 ubuntu kernel: [    0.742722] pci_bus 0000:03: resource 1 [mem 0xfd500000-0xfd5fffff]
Jul 13 11:37:01 ubuntu kernel: [    0.742723] pci_bus 0000:03: resource 2 [mem 0x40000000-0x401fffff 64bit pref]
Jul 13 11:37:01 ubuntu kernel: [    0.742725] pci_bus 0000:04: resource 0 [io  0x8000-0x8fff]
Jul 13 11:37:01 ubuntu kernel: [    0.742726] pci_bus 0000:04: resource 1 [mem 0xfd100000-0xfd1fffff]
Jul 13 11:37:01 ubuntu kernel: [    0.742727] pci_bus 0000:04: resource 2 [mem 0xeb700000-0xeb7fffff 64bit pref]
Jul 13 11:37:01 ubuntu kernel: [    0.742728] pci_bus 0000:05: resource 0 [io  0xc000-0xcfff]
Jul 13 11:37:01 ubuntu kernel: [    0.742729] pci_bus 0000:05: resource 1 [mem 0xfcd00000-0xfcdfffff]
Jul 13 11:37:01 ubuntu kernel: [    0.742730] pci_bus 0000:05: resource 2 [mem 0xeb300000-0xeb3fffff 64bit pref]
Jul 13 11:37:01 ubuntu kernel: [    0.742731] pci_bus 0000:06: resource 1 [mem 0xfc900000-0xfc9fffff]
Jul 13 11:37:01 ubuntu kernel: [    0.742732] pci_bus 0000:06: resource 2 [mem 0xeaf00000-0xeaffffff 64bit pref]
Jul 13 11:37:01 ubuntu kernel: [    0.742733] pci_bus 0000:07: resource 1 [mem 0xfc500000-0xfc5fffff]
Jul 13 11:37:01 ubuntu kernel: [    0.742734] pci_bus 0000:07: resource 2 [mem 0xeab00000-0xeabfffff 64bit pref]
Jul 13 11:37:01 ubuntu kernel: [    0.742735] pci_bus 0000:08: resource 1 [mem 0xfc100000-0xfc1fffff]
Jul 13 11:37:01 ubuntu kernel: [    0.742737] pci_bus 0000:08: resource 2 [mem 0xea700000-0xea7fffff 64bit pref]
Jul 13 11:37:01 ubuntu kernel: [    0.742738] pci_bus 0000:09: resource 1 [mem 0xfbd00000-0xfbdfffff]
Jul 13 11:37:01 ubuntu kernel: [    0.742739] pci_bus 0000:09: resource 2 [mem 0xea300000-0xea3fffff 64bit pref]
Jul 13 11:37:01 ubuntu kernel: [    0.742740] pci_bus 0000:0a: resource 1 [mem 0xfb900000-0xfb9fffff]
Jul 13 11:37:01 ubuntu kernel: [    0.742741] pci_bus 0000:0a: resource 2 [mem 0xe9f00000-0xe9ffffff 64bit pref]
Jul 13 11:37:01 ubuntu kernel: [    0.742743] pci_bus 0000:0b: resource 0 [io  0x5000-0x5fff]
Jul 13 11:37:01 ubuntu kernel: [    0.742744] pci_bus 0000:0b: resource 1 [mem 0xfd400000-0xfd4fffff]
Jul 13 11:37:01 ubuntu kernel: [    0.742745] pci_bus 0000:0b: resource 2 [mem 0xeba00000-0xebafffff 64bit pref]
Jul 13 11:37:01 ubuntu kernel: [    0.742746] pci_bus 0000:0c: resource 0 [io  0x9000-0x9fff]
Jul 13 11:37:01 ubuntu kernel: [    0.742747] pci_bus 0000:0c: resource 1 [mem 0xfd000000-0xfd0fffff]
Jul 13 11:37:01 ubuntu kernel: [    0.742748] pci_bus 0000:0c: resource 2 [mem 0xeb600000-0xeb6fffff 64bit pref]
Jul 13 11:37:01 ubuntu kernel: [    0.742749] pci_bus 0000:0d: resource 0 [io  0xd000-0xdfff]
Jul 13 11:37:01 ubuntu kernel: [    0.742750] pci_bus 0000:0d: resource 1 [mem 0xfcc00000-0xfccfffff]
Jul 13 11:37:01 ubuntu kernel: [    0.742751] pci_bus 0000:0d: resource 2 [mem 0xeb200000-0xeb2fffff 64bit pref]
Jul 13 11:37:01 ubuntu kernel: [    0.742752] pci_bus 0000:0e: resource 1 [mem 0xfc800000-0xfc8fffff]
Jul 13 11:37:01 ubuntu kernel: [    0.742753] pci_bus 0000:0e: resource 2 [mem 0xeae00000-0xeaefffff 64bit pref]
Jul 13 11:37:01 ubuntu kernel: [    0.742754] pci_bus 0000:0f: resource 1 [mem 0xfc400000-0xfc4fffff]
Jul 13 11:37:01 ubuntu kernel: [    0.742755] pci_bus 0000:0f: resource 2 [mem 0xeaa00000-0xeaafffff 64bit pref]
Jul 13 11:37:01 ubuntu kernel: [    0.742756] pci_bus 0000:10: resource 1 [mem 0xfc000000-0xfc0fffff]
Jul 13 11:37:01 ubuntu kernel: [    0.742757] pci_bus 0000:10: resource 2 [mem 0xea600000-0xea6fffff 64bit pref]
Jul 13 11:37:01 ubuntu kernel: [    0.742758] pci_bus 0000:11: resource 1 [mem 0xfbc00000-0xfbcfffff]
Jul 13 11:37:01 ubuntu kernel: [    0.742760] pci_bus 0000:11: resource 2 [mem 0xea200000-0xea2fffff 64bit pref]
Jul 13 11:37:01 ubuntu kernel: [    0.742761] pci_bus 0000:12: resource 1 [mem 0xfb800000-0xfb8fffff]
Jul 13 11:37:01 ubuntu kernel: [    0.742762] pci_bus 0000:12: resource 2 [mem 0xe9e00000-0xe9efffff 64bit pref]
Jul 13 11:37:01 ubuntu kernel: [    0.742763] pci_bus 0000:13: resource 0 [io  0x6000-0x6fff]
Jul 13 11:37:01 ubuntu kernel: [    0.742764] pci_bus 0000:13: resource 1 [mem 0xfd300000-0xfd3fffff]
Jul 13 11:37:01 ubuntu kernel: [    0.742765] pci_bus 0000:13: resource 2 [mem 0xeb900000-0xeb9fffff 64bit pref]
Jul 13 11:37:01 ubuntu kernel: [    0.742766] pci_bus 0000:14: resource 0 [io  0xa000-0xafff]
Jul 13 11:37:01 ubuntu kernel: [    0.742767] pci_bus 0000:14: resource 1 [mem 0xfcf00000-0xfcffffff]
Jul 13 11:37:01 ubuntu kernel: [    0.742768] pci_bus 0000:14: resource 2 [mem 0xeb500000-0xeb5fffff 64bit pref]
Jul 13 11:37:01 ubuntu kernel: [    0.742769] pci_bus 0000:15: resource 0 [io  0xe000-0xefff]
Jul 13 11:37:01 ubuntu kernel: [    0.742770] pci_bus 0000:15: resource 1 [mem 0xfcb00000-0xfcbfffff]
Jul 13 11:37:01 ubuntu kernel: [    0.742771] pci_bus 0000:15: resource 2 [mem 0xeb100000-0xeb1fffff 64bit pref]
Jul 13 11:37:01 ubuntu kernel: [    0.742772] pci_bus 0000:16: resource 1 [mem 0xfc700000-0xfc7fffff]
Jul 13 11:37:01 ubuntu kernel: [    0.742773] pci_bus 0000:16: resource 2 [mem 0xead00000-0xeadfffff 64bit pref]
Jul 13 11:37:01 ubuntu kernel: [    0.742774] pci_bus 0000:17: resource 1 [mem 0xfc300000-0xfc3fffff]
Jul 13 11:37:01 ubuntu kernel: [    0.742776] pci_bus 0000:17: resource 2 [mem 0xea900000-0xea9fffff 64bit pref]
Jul 13 11:37:01 ubuntu kernel: [    0.742777] pci_bus 0000:18: resource 1 [mem 0xfbf00000-0xfbffffff]
Jul 13 11:37:01 ubuntu kernel: [    0.742778] pci_bus 0000:18: resource 2 [mem 0xea500000-0xea5fffff 64bit pref]
Jul 13 11:37:01 ubuntu kernel: [    0.742779] pci_bus 0000:19: resource 1 [mem 0xfbb00000-0xfbbfffff]
Jul 13 11:37:01 ubuntu kernel: [    0.742780] pci_bus 0000:19: resource 2 [mem 0xea100000-0xea1fffff 64bit pref]
Jul 13 11:37:01 ubuntu kernel: [    0.742781] pci_bus 0000:1a: resource 1 [mem 0xfb700000-0xfb7fffff]
Jul 13 11:37:01 ubuntu kernel: [    0.742782] pci_bus 0000:1a: resource 2 [mem 0xe9d00000-0xe9dfffff 64bit pref]
Jul 13 11:37:01 ubuntu kernel: [    0.742784] pci_bus 0000:1b: resource 0 [io  0x7000-0x7fff]
Jul 13 11:37:01 ubuntu kernel: [    0.742785] pci_bus 0000:1b: resource 1 [mem 0xfd200000-0xfd2fffff]
Jul 13 11:37:01 ubuntu kernel: [    0.742786] pci_bus 0000:1b: resource 2 [mem 0xeb800000-0xeb8fffff 64bit pref]
Jul 13 11:37:01 ubuntu kernel: [    0.742787] pci_bus 0000:1c: resource 0 [io  0xb000-0xbfff]
Jul 13 11:37:01 ubuntu kernel: [    0.742788] pci_bus 0000:1c: resource 1 [mem 0xfce00000-0xfcefffff]
Jul 13 11:37:01 ubuntu kernel: [    0.742789] pci_bus 0000:1c: resource 2 [mem 0xeb400000-0xeb4fffff 64bit pref]
Jul 13 11:37:01 ubuntu kernel: [    0.742790] pci_bus 0000:1d: resource 1 [mem 0xfca00000-0xfcafffff]
Jul 13 11:37:01 ubuntu kernel: [    0.742791] pci_bus 0000:1d: resource 2 [mem 0xeb000000-0xeb0fffff 64bit pref]
Jul 13 11:37:01 ubuntu kernel: [    0.742792] pci_bus 0000:1e: resource 1 [mem 0xfc600000-0xfc6fffff]
Jul 13 11:37:01 ubuntu kernel: [    0.742793] pci_bus 0000:1e: resource 2 [mem 0xeac00000-0xeacfffff 64bit pref]
Jul 13 11:37:01 ubuntu kernel: [    0.742794] pci_bus 0000:1f: resource 1 [mem 0xfc200000-0xfc2fffff]
Jul 13 11:37:01 ubuntu kernel: [    0.742795] pci_bus 0000:1f: resource 2 [mem 0xea800000-0xea8fffff 64bit pref]
Jul 13 11:37:01 ubuntu kernel: [    0.742796] pci_bus 0000:20: resource 1 [mem 0xfbe00000-0xfbefffff]
Jul 13 11:37:01 ubuntu kernel: [    0.742797] pci_bus 0000:20: resource 2 [mem 0xea400000-0xea4fffff 64bit pref]
Jul 13 11:37:01 ubuntu kernel: [    0.742798] pci_bus 0000:21: resource 1 [mem 0xfba00000-0xfbafffff]
Jul 13 11:37:01 ubuntu kernel: [    0.742799] pci_bus 0000:21: resource 2 [mem 0xea000000-0xea0fffff 64bit pref]
Jul 13 11:37:01 ubuntu kernel: [    0.742801] pci_bus 0000:22: resource 1 [mem 0xfb600000-0xfb6fffff]
Jul 13 11:37:01 ubuntu kernel: [    0.742802] pci_bus 0000:22: resource 2 [mem 0xe9c00000-0xe9cfffff 64bit pref]
Jul 13 11:37:01 ubuntu kernel: [    0.742830] NET: Registered protocol family 2
Jul 13 11:37:01 ubuntu kernel: [    0.743599] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
Jul 13 11:37:01 ubuntu kernel: [    0.744595] TCP bind hash table entries: 8192 (order: 5, 131072 bytes)
Jul 13 11:37:01 ubuntu kernel: [    0.745513] TCP: Hash tables configured (established 8192 bind 8192)
Jul 13 11:37:01 ubuntu kernel: [    0.746428] UDP hash table entries: 512 (order: 2, 16384 bytes)
Jul 13 11:37:01 ubuntu kernel: [    0.747264] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
Jul 13 11:37:01 ubuntu kernel: [    0.748200] NET: Registered protocol family 1
Jul 13 11:37:01 ubuntu kernel: [    0.748843] pci 0000:00:00.0: Limiting direct PCI/PCI transfers
Jul 13 11:37:01 ubuntu kernel: [    0.749722] pci 0000:00:0f.0: Video device with shadowed ROM
Jul 13 11:37:01 ubuntu kernel: [    0.749959] PCI: CLS 32 bytes, default 64
Jul 13 11:37:01 ubuntu kernel: [    0.749999] Trying to unpack rootfs image as initramfs...
Jul 13 11:37:01 ubuntu kernel: [    1.795957] Freeing initrd memory: 7296K (ffff8800371b0000 - ffff8800378d0000)
Jul 13 11:37:01 ubuntu kernel: [    1.797120] RAPL PMU detected, API unit is 2^-32 Joules, 3 fixed counters 10737418240 ms ovfl timer
Jul 13 11:37:01 ubuntu kernel: [    1.798388] hw unit of domain pp0-core 2^-0 Joules
Jul 13 11:37:01 ubuntu kernel: [    1.799072] hw unit of domain package 2^-0 Joules
Jul 13 11:37:01 ubuntu kernel: [    1.799767] hw unit of domain dram 2^-0 Joules
Jul 13 11:37:01 ubuntu kernel: [    1.800431] clocksource: tsc: mask: 0xffffffffffffffff max_cycles: 0x257a3c3232d, max_idle_ns: 440795236700 ns
Jul 13 11:37:01 ubuntu kernel: [    1.801835] clocksource: Switched to clocksource tsc
Jul 13 11:37:01 ubuntu kernel: [    1.802599] Scanning for low memory corruption every 60 seconds
Jul 13 11:37:01 ubuntu kernel: [    1.803721] futex hash table entries: 256 (order: 2, 16384 bytes)
Jul 13 11:37:01 ubuntu kernel: [    1.804597] audit: initializing netlink subsys (disabled)
Jul 13 11:37:01 ubuntu kernel: [    1.805399] audit: type=2000 audit(1468406216.682:1): initialized
Jul 13 11:37:01 ubuntu kernel: [    1.806522] Initialise system trusted keyring
Jul 13 11:37:01 ubuntu kernel: [    1.807264] HugeTLB registered 2 MB page size, pre-allocated 0 pages
Jul 13 11:37:01 ubuntu kernel: [    1.809239] zbud: loaded
Jul 13 11:37:01 ubuntu kernel: [    1.809785] VFS: Disk quotas dquot_6.6.0
Jul 13 11:37:01 ubuntu kernel: [    1.810389] VFS: Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
Jul 13 11:37:01 ubuntu kernel: [    1.811695] fuse init (API version 7.23)
Jul 13 11:37:01 ubuntu kernel: [    1.812374] Key type big_key registered
Jul 13 11:37:01 ubuntu kernel: [    1.812976] Allocating IMA MOK and blacklist keyrings.
Jul 13 11:37:01 ubuntu kernel: [    1.813863] Key type asymmetric registered
Jul 13 11:37:01 ubuntu kernel: [    1.814463] Asymmetric key parser 'x509' registered
Jul 13 11:37:01 ubuntu kernel: [    1.815188] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 249)
Jul 13 11:37:01 ubuntu kernel: [    1.816627] io scheduler noop registered
Jul 13 11:37:01 ubuntu kernel: [    1.817208] io scheduler deadline registered (default)
Jul 13 11:37:01 ubuntu kernel: [    1.817959] io scheduler cfq registered
Jul 13 11:37:01 ubuntu kernel: [    1.830034] pcieport 0000:00:15.0: Signaling PME through PCIe PME interrupt
Jul 13 11:37:01 ubuntu kernel: [    1.831007] pci 0000:03:00.0: Signaling PME through PCIe PME interrupt
Jul 13 11:37:01 ubuntu kernel: [    1.831940] pcie_pme 0000:00:15.0:pcie01: service driver pcie_pme loaded
Jul 13 11:37:01 ubuntu kernel: [    1.832051] pcieport 0000:00:15.1: Signaling PME through PCIe PME interrupt
Jul 13 11:37:01 ubuntu kernel: [    1.833026] pcie_pme 0000:00:15.1:pcie01: service driver pcie_pme loaded
Jul 13 11:37:01 ubuntu kernel: [    1.833132] pcieport 0000:00:15.2: Signaling PME through PCIe PME interrupt
Jul 13 11:37:01 ubuntu kernel: [    1.834106] pcie_pme 0000:00:15.2:pcie01: service driver pcie_pme loaded
Jul 13 11:37:01 ubuntu kernel: [    1.834214] pcieport 0000:00:15.3: Signaling PME through PCIe PME interrupt
Jul 13 11:37:01 ubuntu kernel: [    1.835188] pcie_pme 0000:00:15.3:pcie01: service driver pcie_pme loaded
Jul 13 11:37:01 ubuntu kernel: [    1.835294] pcieport 0000:00:15.4: Signaling PME through PCIe PME interrupt
Jul 13 11:37:01 ubuntu kernel: [    1.836285] pcie_pme 0000:00:15.4:pcie01: service driver pcie_pme loaded
Jul 13 11:37:01 ubuntu kernel: [    1.836392] pcieport 0000:00:15.5: Signaling PME through PCIe PME interrupt
Jul 13 11:37:01 ubuntu kernel: [    1.837368] pcie_pme 0000:00:15.5:pcie01: service driver pcie_pme loaded
Jul 13 11:37:01 ubuntu kernel: [    1.837473] pcieport 0000:00:15.6: Signaling PME through PCIe PME interrupt
Jul 13 11:37:01 ubuntu kernel: [    1.838453] pcie_pme 0000:00:15.6:pcie01: service driver pcie_pme loaded
Jul 13 11:37:01 ubuntu kernel: [    1.838559] pcieport 0000:00:15.7: Signaling PME through PCIe PME interrupt
Jul 13 11:37:01 ubuntu kernel: [    1.839541] pcie_pme 0000:00:15.7:pcie01: service driver pcie_pme loaded
Jul 13 11:37:01 ubuntu kernel: [    1.839648] pcieport 0000:00:16.0: Signaling PME through PCIe PME interrupt
Jul 13 11:37:01 ubuntu kernel: [    1.840624] pcie_pme 0000:00:16.0:pcie01: service driver pcie_pme loaded
Jul 13 11:37:01 ubuntu kernel: [    1.840732] pcieport 0000:00:16.1: Signaling PME through PCIe PME interrupt
Jul 13 11:37:01 ubuntu kernel: [    1.841707] pcie_pme 0000:00:16.1:pcie01: service driver pcie_pme loaded
Jul 13 11:37:01 ubuntu kernel: [    1.841813] pcieport 0000:00:16.2: Signaling PME through PCIe PME interrupt
Jul 13 11:37:01 ubuntu kernel: [    1.842786] pcie_pme 0000:00:16.2:pcie01: service driver pcie_pme loaded
Jul 13 11:37:01 ubuntu kernel: [    1.842891] pcieport 0000:00:16.3: Signaling PME through PCIe PME interrupt
Jul 13 11:37:01 ubuntu kernel: [    1.843874] pcie_pme 0000:00:16.3:pcie01: service driver pcie_pme loaded
Jul 13 11:37:01 ubuntu kernel: [    1.843981] pcieport 0000:00:16.4: Signaling PME through PCIe PME interrupt
Jul 13 11:37:01 ubuntu kernel: [    1.844957] pcie_pme 0000:00:16.4:pcie01: service driver pcie_pme loaded
Jul 13 11:37:01 ubuntu kernel: [    1.845062] pcieport 0000:00:16.5: Signaling PME through PCIe PME interrupt
Jul 13 11:37:01 ubuntu kernel: [    1.846037] pcie_pme 0000:00:16.5:pcie01: service driver pcie_pme loaded
Jul 13 11:37:01 ubuntu kernel: [    1.846143] pcieport 0000:00:16.6: Signaling PME through PCIe PME interrupt
Jul 13 11:37:01 ubuntu kernel: [    1.847116] pcie_pme 0000:00:16.6:pcie01: service driver pcie_pme loaded
Jul 13 11:37:01 ubuntu kernel: [    1.847221] pcieport 0000:00:16.7: Signaling PME through PCIe PME interrupt
Jul 13 11:37:01 ubuntu kernel: [    1.848205] pcie_pme 0000:00:16.7:pcie01: service driver pcie_pme loaded
Jul 13 11:37:01 ubuntu kernel: [    1.848312] pcieport 0000:00:17.0: Signaling PME through PCIe PME interrupt
Jul 13 11:37:01 ubuntu kernel: [    1.849289] pcie_pme 0000:00:17.0:pcie01: service driver pcie_pme loaded
Jul 13 11:37:01 ubuntu kernel: [    1.849394] pcieport 0000:00:17.1: Signaling PME through PCIe PME interrupt
Jul 13 11:37:01 ubuntu kernel: [    1.850371] pcie_pme 0000:00:17.1:pcie01: service driver pcie_pme loaded
Jul 13 11:37:01 ubuntu kernel: [    1.850477] pcieport 0000:00:17.2: Signaling PME through PCIe PME interrupt
Jul 13 11:37:01 ubuntu kernel: [    1.852019] pcie_pme 0000:00:17.2:pcie01: service driver pcie_pme loaded
Jul 13 11:37:01 ubuntu kernel: [    1.852137] pcieport 0000:00:17.3: Signaling PME through PCIe PME interrupt
Jul 13 11:37:01 ubuntu kernel: [    1.853235] pcie_pme 0000:00:17.3:pcie01: service driver pcie_pme loaded
Jul 13 11:37:01 ubuntu kernel: [    1.853354] pcieport 0000:00:17.4: Signaling PME through PCIe PME interrupt
Jul 13 11:37:01 ubuntu kernel: [    1.854429] pcie_pme 0000:00:17.4:pcie01: service driver pcie_pme loaded
Jul 13 11:37:01 ubuntu kernel: [    1.854546] pcieport 0000:00:17.5: Signaling PME through PCIe PME interrupt
Jul 13 11:37:01 ubuntu kernel: [    1.855627] pcie_pme 0000:00:17.5:pcie01: service driver pcie_pme loaded
Jul 13 11:37:01 ubuntu kernel: [    1.855746] pcieport 0000:00:17.6: Signaling PME through PCIe PME interrupt
Jul 13 11:37:01 ubuntu kernel: [    1.856819] pcie_pme 0000:00:17.6:pcie01: service driver pcie_pme loaded
Jul 13 11:37:01 ubuntu kernel: [    1.856943] pcieport 0000:00:17.7: Signaling PME through PCIe PME interrupt
Jul 13 11:37:01 ubuntu kernel: [    1.858021] pcie_pme 0000:00:17.7:pcie01: service driver pcie_pme loaded
Jul 13 11:37:01 ubuntu kernel: [    1.858137] pcieport 0000:00:18.0: Signaling PME through PCIe PME interrupt
Jul 13 11:37:01 ubuntu kernel: [    1.859208] pcie_pme 0000:00:18.0:pcie01: service driver pcie_pme loaded
Jul 13 11:37:01 ubuntu kernel: [    1.859325] pcieport 0000:00:18.1: Signaling PME through PCIe PME interrupt
Jul 13 11:37:01 ubuntu kernel: [    1.860411] pcie_pme 0000:00:18.1:pcie01: service driver pcie_pme loaded
Jul 13 11:37:01 ubuntu kernel: [    1.860528] pcieport 0000:00:18.2: Signaling PME through PCIe PME interrupt
Jul 13 11:37:01 ubuntu kernel: [    1.861608] pcie_pme 0000:00:18.2:pcie01: service driver pcie_pme loaded
Jul 13 11:37:01 ubuntu kernel: [    1.861724] pcieport 0000:00:18.3: Signaling PME through PCIe PME interrupt
Jul 13 11:37:01 ubuntu kernel: [    1.862776] pcie_pme 0000:00:18.3:pcie01: service driver pcie_pme loaded
Jul 13 11:37:01 ubuntu kernel: [    1.862889] pcieport 0000:00:18.4: Signaling PME through PCIe PME interrupt
Jul 13 11:37:01 ubuntu kernel: [    1.863936] pcie_pme 0000:00:18.4:pcie01: service driver pcie_pme loaded
Jul 13 11:37:01 ubuntu kernel: [    1.864049] pcieport 0000:00:18.5: Signaling PME through PCIe PME interrupt
Jul 13 11:37:01 ubuntu kernel: [    1.865092] pcie_pme 0000:00:18.5:pcie01: service driver pcie_pme loaded
Jul 13 11:37:01 ubuntu kernel: [    1.865205] pcieport 0000:00:18.6: Signaling PME through PCIe PME interrupt
Jul 13 11:37:01 ubuntu kernel: [    1.866242] pcie_pme 0000:00:18.6:pcie01: service driver pcie_pme loaded
Jul 13 11:37:01 ubuntu kernel: [    1.866356] pcieport 0000:00:18.7: Signaling PME through PCIe PME interrupt
Jul 13 11:37:01 ubuntu kernel: [    1.867395] pcie_pme 0000:00:18.7:pcie01: service driver pcie_pme loaded
Jul 13 11:37:01 ubuntu kernel: [    1.867402] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jul 13 11:37:01 ubuntu kernel: [    1.868276] pciehp 0000:00:15.0:pcie04: Slot #160 AttnBtn+ PwrCtrl+ MRL- AttnInd- PwrInd- HotPlug+ Surprise- Interlock- NoCompl+ LLActRep+
Jul 13 11:37:01 ubuntu kernel: [    1.870123] pciehp 0000:00:15.0:pcie04: service driver pciehp loaded
Jul 13 11:37:01 ubuntu kernel: [    1.870150] pciehp 0000:00:15.1:pcie04: Slot #161 AttnBtn+ PwrCtrl+ MRL- AttnInd- PwrInd- HotPlug+ Surprise- Interlock- NoCompl+ LLActRep+
Jul 13 11:37:01 ubuntu kernel: [    1.872006] pciehp 0000:00:15.1:pcie04: service driver pciehp loaded
Jul 13 11:37:01 ubuntu kernel: [    1.872031] pciehp 0000:00:15.2:pcie04: Slot #162 AttnBtn+ PwrCtrl+ MRL- AttnInd- PwrInd- HotPlug+ Surprise- Interlock- NoCompl+ LLActRep+
Jul 13 11:37:01 ubuntu kernel: [    1.873836] pciehp 0000:00:15.2:pcie04: service driver pciehp loaded
Jul 13 11:37:01 ubuntu kernel: [    1.873861] pciehp 0000:00:15.3:pcie04: Slot #163 AttnBtn+ PwrCtrl+ MRL- AttnInd- PwrInd- HotPlug+ Surprise- Interlock- NoCompl+ LLActRep+
Jul 13 11:37:01 ubuntu kernel: [    1.875651] pciehp 0000:00:15.3:pcie04: service driver pciehp loaded
Jul 13 11:37:01 ubuntu kernel: [    1.875678] pciehp 0000:00:15.4:pcie04: Slot #164 AttnBtn+ PwrCtrl+ MRL- AttnInd- PwrInd- HotPlug+ Surprise- Interlock- NoCompl+ LLActRep+
Jul 13 11:37:01 ubuntu kernel: [    1.877464] pciehp 0000:00:15.4:pcie04: service driver pciehp loaded
Jul 13 11:37:01 ubuntu kernel: [    1.877490] pciehp 0000:00:15.5:pcie04: Slot #165 AttnBtn+ PwrCtrl+ MRL- AttnInd- PwrInd- HotPlug+ Surprise- Interlock- NoCompl+ LLActRep+
Jul 13 11:37:01 ubuntu kernel: [    1.879273] pciehp 0000:00:15.5:pcie04: service driver pciehp loaded
Jul 13 11:37:01 ubuntu kernel: [    1.879298] pciehp 0000:00:15.6:pcie04: Slot #166 AttnBtn+ PwrCtrl+ MRL- AttnInd- PwrInd- HotPlug+ Surprise- Interlock- NoCompl+ LLActRep+
Jul 13 11:37:01 ubuntu kernel: [    1.881149] pciehp 0000:00:15.6:pcie04: service driver pciehp loaded
Jul 13 11:37:01 ubuntu kernel: [    1.881175] pciehp 0000:00:15.7:pcie04: Slot #167 AttnBtn+ PwrCtrl+ MRL- AttnInd- PwrInd- HotPlug+ Surprise- Interlock- NoCompl+ LLActRep+
Jul 13 11:37:01 ubuntu kernel: [    1.883006] pciehp 0000:00:15.7:pcie04: service driver pciehp loaded
Jul 13 11:37:01 ubuntu kernel: [    1.883033] pciehp 0000:00:16.0:pcie04: Slot #192 AttnBtn+ PwrCtrl+ MRL- AttnInd- PwrInd- HotPlug+ Surprise- Interlock- NoCompl+ LLActRep+
Jul 13 11:37:01 ubuntu kernel: [    1.884826] pciehp 0000:00:16.0:pcie04: service driver pciehp loaded
Jul 13 11:37:01 ubuntu kernel: [    1.884852] pciehp 0000:00:16.1:pcie04: Slot #193 AttnBtn+ PwrCtrl+ MRL- AttnInd- PwrInd- HotPlug+ Surprise- Interlock- NoCompl+ LLActRep+
Jul 13 11:37:01 ubuntu kernel: [    1.886647] pciehp 0000:00:16.1:pcie04: service driver pciehp loaded
Jul 13 11:37:01 ubuntu kernel: [    1.886673] pciehp 0000:00:16.2:pcie04: Slot #194 AttnBtn+ PwrCtrl+ MRL- AttnInd- PwrInd- HotPlug+ Surprise- Interlock- NoCompl+ LLActRep+
Jul 13 11:37:01 ubuntu kernel: [    1.888466] pciehp 0000:00:16.2:pcie04: service driver pciehp loaded
Jul 13 11:37:01 ubuntu kernel: [    1.888492] pciehp 0000:00:16.3:pcie04: Slot #195 AttnBtn+ PwrCtrl+ MRL- AttnInd- PwrInd- HotPlug+ Surprise- Interlock- NoCompl+ LLActRep+
Jul 13 11:37:01 ubuntu kernel: [    1.890274] pciehp 0000:00:16.3:pcie04: service driver pciehp loaded
Jul 13 11:37:01 ubuntu kernel: [    1.890301] pciehp 0000:00:16.4:pcie04: Slot #196 AttnBtn+ PwrCtrl+ MRL- AttnInd- PwrInd- HotPlug+ Surprise- Interlock- NoCompl+ LLActRep+
Jul 13 11:37:01 ubuntu kernel: [    1.892122] pciehp 0000:00:16.4:pcie04: service driver pciehp loaded
Jul 13 11:37:01 ubuntu kernel: [    1.892147] pciehp 0000:00:16.5:pcie04: Slot #197 AttnBtn+ PwrCtrl+ MRL- AttnInd- PwrInd- HotPlug+ Surprise- Interlock- NoCompl+ LLActRep+
Jul 13 11:37:01 ubuntu kernel: [    1.893978] pciehp 0000:00:16.5:pcie04: service driver pciehp loaded
Jul 13 11:37:01 ubuntu kernel: [    1.894004] pciehp 0000:00:16.6:pcie04: Slot #198 AttnBtn+ PwrCtrl+ MRL- AttnInd- PwrInd- HotPlug+ Surprise- Interlock- NoCompl+ LLActRep+
Jul 13 11:37:01 ubuntu kernel: [    1.895821] pciehp 0000:00:16.6:pcie04: service driver pciehp loaded
Jul 13 11:37:01 ubuntu kernel: [    1.895848] pciehp 0000:00:16.7:pcie04: Slot #199 AttnBtn+ PwrCtrl+ MRL- AttnInd- PwrInd- HotPlug+ Surprise- Interlock- NoCompl+ LLActRep+
Jul 13 11:37:01 ubuntu kernel: [    1.897655] pciehp 0000:00:16.7:pcie04: service driver pciehp loaded
Jul 13 11:37:01 ubuntu kernel: [    1.897680] pciehp 0000:00:17.0:pcie04: Slot #224 AttnBtn+ PwrCtrl+ MRL- AttnInd- PwrInd- HotPlug+ Surprise- Interlock- NoCompl+ LLActRep+
Jul 13 11:37:01 ubuntu kernel: [    1.899461] pciehp 0000:00:17.0:pcie04: service driver pciehp loaded
Jul 13 11:37:01 ubuntu kernel: [    1.899486] pciehp 0000:00:17.1:pcie04: Slot #225 AttnBtn+ PwrCtrl+ MRL- AttnInd- PwrInd- HotPlug+ Surprise- Interlock- NoCompl+ LLActRep+
Jul 13 11:37:01 ubuntu kernel: [    1.901293] pciehp 0000:00:17.1:pcie04: service driver pciehp loaded
Jul 13 11:37:01 ubuntu kernel: [    1.901319] pciehp 0000:00:17.2:pcie04: Slot #226 AttnBtn+ PwrCtrl+ MRL- AttnInd- PwrInd- HotPlug+ Surprise- Interlock- NoCompl+ LLActRep+
Jul 13 11:37:01 ubuntu kernel: [    1.903143] pciehp 0000:00:17.2:pcie04: service driver pciehp loaded
Jul 13 11:37:01 ubuntu kernel: [    1.903167] pciehp 0000:00:17.3:pcie04: Slot #227 AttnBtn+ PwrCtrl+ MRL- AttnInd- PwrInd- HotPlug+ Surprise- Interlock- NoCompl+ LLActRep+
Jul 13 11:37:01 ubuntu kernel: [    1.904914] pciehp 0000:00:17.3:pcie04: service driver pciehp loaded
Jul 13 11:37:01 ubuntu kernel: [    1.904939] pciehp 0000:00:17.4:pcie04: Slot #228 AttnBtn+ PwrCtrl+ MRL- AttnInd- PwrInd- HotPlug+ Surprise- Interlock- NoCompl+ LLActRep+
Jul 13 11:37:01 ubuntu kernel: [    1.906672] pciehp 0000:00:17.4:pcie04: service driver pciehp loaded
Jul 13 11:37:01 ubuntu kernel: [    1.906696] pciehp 0000:00:17.5:pcie04: Slot #229 AttnBtn+ PwrCtrl+ MRL- AttnInd- PwrInd- HotPlug+ Surprise- Interlock- NoCompl+ LLActRep+
Jul 13 11:37:01 ubuntu kernel: [    1.909573] pciehp 0000:00:17.5:pcie04: service driver pciehp loaded
Jul 13 11:37:01 ubuntu kernel: [    1.909598] pciehp 0000:00:17.6:pcie04: Slot #230 AttnBtn+ PwrCtrl+ MRL- AttnInd- PwrInd- HotPlug+ Surprise- Interlock- NoCompl+ LLActRep+
Jul 13 11:37:01 ubuntu kernel: [    1.911328] pciehp 0000:00:17.6:pcie04: service driver pciehp loaded
Jul 13 11:37:01 ubuntu kernel: [    1.911353] pciehp 0000:00:17.7:pcie04: Slot #231 AttnBtn+ PwrCtrl+ MRL- AttnInd- PwrInd- HotPlug+ Surprise- Interlock- NoCompl+ LLActRep+
Jul 13 11:37:01 ubuntu kernel: [    1.913118] pciehp 0000:00:17.7:pcie04: service driver pciehp loaded
Jul 13 11:37:01 ubuntu kernel: [    1.913143] pciehp 0000:00:18.0:pcie04: Slot #256 AttnBtn+ PwrCtrl+ MRL- AttnInd- PwrInd- HotPlug+ Surprise- Interlock- NoCompl+ LLActRep+
Jul 13 11:37:01 ubuntu kernel: [    1.914876] pciehp 0000:00:18.0:pcie04: service driver pciehp loaded
Jul 13 11:37:01 ubuntu kernel: [    1.914900] pciehp 0000:00:18.1:pcie04: Slot #257 AttnBtn+ PwrCtrl+ MRL- AttnInd- PwrInd- HotPlug+ Surprise- Interlock- NoCompl+ LLActRep+
Jul 13 11:37:01 ubuntu kernel: [    1.916639] pciehp 0000:00:18.1:pcie04: service driver pciehp loaded
Jul 13 11:37:01 ubuntu kernel: [    1.916663] pciehp 0000:00:18.2:pcie04: Slot #258 AttnBtn+ PwrCtrl+ MRL- AttnInd- PwrInd- HotPlug+ Surprise- Interlock- NoCompl+ LLActRep+
Jul 13 11:37:01 ubuntu kernel: [    1.918413] pciehp 0000:00:18.2:pcie04: service driver pciehp loaded
Jul 13 11:37:01 ubuntu kernel: [    1.918439] pciehp 0000:00:18.3:pcie04: Slot #259 AttnBtn+ PwrCtrl+ MRL- AttnInd- PwrInd- HotPlug+ Surprise- Interlock- NoCompl+ LLActRep+
Jul 13 11:37:01 ubuntu kernel: [    1.920200] pciehp 0000:00:18.3:pcie04: service driver pciehp loaded
Jul 13 11:37:01 ubuntu kernel: [    1.920224] pciehp 0000:00:18.4:pcie04: Slot #260 AttnBtn+ PwrCtrl+ MRL- AttnInd- PwrInd- HotPlug+ Surprise- Interlock- NoCompl+ LLActRep+
Jul 13 11:37:01 ubuntu kernel: [    1.921984] pciehp 0000:00:18.4:pcie04: service driver pciehp loaded
Jul 13 11:37:01 ubuntu kernel: [    1.922009] pciehp 0000:00:18.5:pcie04: Slot #261 AttnBtn+ PwrCtrl+ MRL- AttnInd- PwrInd- HotPlug+ Surprise- Interlock- NoCompl+ LLActRep+
Jul 13 11:37:01 ubuntu kernel: [    1.923753] pciehp 0000:00:18.5:pcie04: service driver pciehp loaded
Jul 13 11:37:01 ubuntu kernel: [    1.923778] pciehp 0000:00:18.6:pcie04: Slot #262 AttnBtn+ PwrCtrl+ MRL- AttnInd- PwrInd- HotPlug+ Surprise- Interlock- NoCompl+ LLActRep+
Jul 13 11:37:01 ubuntu kernel: [    1.925506] pciehp 0000:00:18.6:pcie04: service driver pciehp loaded
Jul 13 11:37:01 ubuntu kernel: [    1.925530] pciehp 0000:00:18.7:pcie04: Slot #263 AttnBtn+ PwrCtrl+ MRL- AttnInd- PwrInd- HotPlug+ Surprise- Interlock- NoCompl+ LLActRep+
Jul 13 11:37:01 ubuntu kernel: [    1.927258] pciehp 0000:00:18.7:pcie04: service driver pciehp loaded
Jul 13 11:37:01 ubuntu kernel: [    1.927262] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Jul 13 11:37:01 ubuntu kernel: [    1.928220] intel_idle: does not run on family 6 model 45
Jul 13 11:37:01 ubuntu kernel: [    1.928354] ACPI: AC Adapter [ACAD] (on-line)
Jul 13 11:37:01 ubuntu kernel: [    1.929034] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
Jul 13 11:37:01 ubuntu kernel: [    1.930093] ACPI: Power Button [PWRF]
Jul 13 11:37:01 ubuntu kernel: [    1.930791] GHES: HEST is not enabled!
Jul 13 11:37:01 ubuntu kernel: [    1.931417] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
Jul 13 11:37:01 ubuntu kernel: [    1.955473] 00:06: ttyS0 at I/O 0x3f8 (irq = 4, base_baud = 115200) is a 16550A
Jul 13 11:37:01 ubuntu kernel: [    1.979792] 00:07: ttyS1 at I/O 0x2f8 (irq = 3, base_baud = 115200) is a 16550A
Jul 13 11:37:01 ubuntu kernel: [    1.981749] Linux agpgart interface v0.103
Jul 13 11:37:01 ubuntu kernel: [    1.982403] agpgart-intel 0000:00:00.0: Intel 440BX Chipset
Jul 13 11:37:01 ubuntu kernel: [    1.983721] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0x0
Jul 13 11:37:01 ubuntu kernel: [    1.986395] brd: module loaded
Jul 13 11:37:01 ubuntu kernel: [    1.987555] loop: module loaded
Jul 13 11:37:01 ubuntu kernel: [    1.988124] ata_piix 0000:00:07.1: version 2.13
Jul 13 11:37:01 ubuntu kernel: [    1.988496] scsi host0: ata_piix
Jul 13 11:37:01 ubuntu kernel: [    1.989042] scsi host1: ata_piix
Jul 13 11:37:01 ubuntu kernel: [    1.989560] ata1: PATA max UDMA/33 cmd 0x1f0 ctl 0x3f6 bmdma 0x1060 irq 14
Jul 13 11:37:01 ubuntu kernel: [    1.990515] ata2: PATA max UDMA/33 cmd 0x170 ctl 0x376 bmdma 0x1068 irq 15
Jul 13 11:37:01 ubuntu kernel: [    1.991697] libphy: Fixed MDIO Bus: probed
Jul 13 11:37:01 ubuntu kernel: [    1.992299] tun: Universal TUN/TAP device driver, 1.6
Jul 13 11:37:01 ubuntu kernel: [    1.993016] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
Jul 13 11:37:01 ubuntu kernel: [    1.994042] PPP generic driver version 2.4.2
Jul 13 11:37:01 ubuntu kernel: [    1.994709] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Jul 13 11:37:01 ubuntu kernel: [    1.995637] ehci-pci: EHCI PCI platform driver
Jul 13 11:37:01 ubuntu kernel: [    1.996290] ehci-platform: EHCI generic platform driver
Jul 13 11:37:01 ubuntu kernel: [    1.997035] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Jul 13 11:37:01 ubuntu kernel: [    1.997900] ohci-pci: OHCI PCI platform driver
Jul 13 11:37:01 ubuntu kernel: [    1.998548] ohci-platform: OHCI generic platform driver
Jul 13 11:37:01 ubuntu kernel: [    1.999295] uhci_hcd: USB Universal Host Controller Interface driver
Jul 13 11:37:01 ubuntu kernel: [    2.000241] i8042: PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:MOUS] at 0x60,0x64 irq 1,12
Jul 13 11:37:01 ubuntu kernel: [    2.002055] serio: i8042 KBD port at 0x60,0x64 irq 1
Jul 13 11:37:01 ubuntu kernel: [    2.002794] serio: i8042 AUX port at 0x60,0x64 irq 12
Jul 13 11:37:01 ubuntu kernel: [    2.003605] mousedev: PS/2 mouse device common for all mice
Jul 13 11:37:01 ubuntu kernel: [    2.024668] rtc_cmos 00:01: rtc core: registered rtc_cmos as rtc0
Jul 13 11:37:01 ubuntu kernel: [    2.025657] rtc_cmos 00:01: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
Jul 13 11:37:01 ubuntu kernel: [    2.026808] i2c /dev entries driver
Jul 13 11:37:01 ubuntu kernel: [    2.027384] device-mapper: uevent: version 1.0.3
Jul 13 11:37:01 ubuntu kernel: [    2.028140] device-mapper: ioctl: 4.34.0-ioctl (2015-10-28) initialised: dm-devel@redhat.com
Jul 13 11:37:01 ubuntu kernel: [    2.029404] ledtrig-cpu: registered to indicate activity on CPUs
Jul 13 11:37:01 ubuntu kernel: [    2.030310] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
Jul 13 11:37:01 ubuntu kernel: [    2.031912] NET: Registered protocol family 10
Jul 13 11:37:01 ubuntu kernel: [    2.032687] NET: Registered protocol family 17
Jul 13 11:37:01 ubuntu kernel: [    2.033342] Key type dns_resolver registered
Jul 13 11:37:01 ubuntu kernel: [    2.034063] microcode: CPU0 sig=0x206d2, pf=0x1, revision=0x710
Jul 13 11:37:01 ubuntu kernel: [    2.034917] microcode: Microcode Update Driver: v2.01 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
Jul 13 11:37:01 ubuntu kernel: [    2.036262] registered taskstats version 1
Jul 13 11:37:01 ubuntu kernel: [    2.036874] Loading compiled-in X.509 certificates
Jul 13 11:37:01 ubuntu kernel: [    2.038274] Loaded X.509 cert 'Build time autogenerated kernel key: 6ea974e07bd0b30541f4d838a3b7a8a80d5ca9af'
Jul 13 11:37:01 ubuntu kernel: [    2.039679] zswap: loaded using pool lzo/zbud
Jul 13 11:37:01 ubuntu kernel: [    2.041521] Key type trusted registered
Jul 13 11:37:01 ubuntu kernel: [    2.043939] Key type encrypted registered
Jul 13 11:37:01 ubuntu kernel: [    2.044532] AppArmor: AppArmor sha1 policy hashing enabled
Jul 13 11:37:01 ubuntu kernel: [    2.045299] ima: No TPM chip found, activating TPM-bypass!
Jul 13 11:37:01 ubuntu kernel: [    2.046081] evm: HMAC attrs: 0x1
Jul 13 11:37:01 ubuntu kernel: [    2.048779]   Magic number: 8:622:628
Jul 13 11:37:01 ubuntu kernel: [    2.049343] pci_bus 0000:0a: hash matches
Jul 13 11:37:01 ubuntu kernel: [    2.050041] rtc_cmos 00:01: setting system clock to 2016-07-13 10:36:57 UTC (1468406217)
Jul 13 11:37:01 ubuntu kernel: [    2.051236] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Jul 13 11:37:01 ubuntu kernel: [    2.052085] EDD information not available.
Jul 13 11:37:01 ubuntu kernel: [    2.052779] PM: Hibernation image not present or could not be loaded.
Jul 13 11:37:01 ubuntu kernel: [    2.158640] ata2.00: ATAPI: VMware Virtual IDE CDROM Drive, 00000001, max UDMA/33
Jul 13 11:37:01 ubuntu kernel: [    2.175674] ata2.00: configured for UDMA/33
Jul 13 11:37:01 ubuntu kernel: [    2.177993] scsi 1:0:0:0: CD-ROM            NECVMWar VMware IDE CDR10 1.00 PQ: 0 ANSI: 5
Jul 13 11:37:01 ubuntu kernel: [    2.187856] sr 1:0:0:0: [sr0] scsi3-mmc drive: 1x/1x writer dvd-ram cd/rw xa/form2 cdda tray
Jul 13 11:37:01 ubuntu kernel: [    2.189054] cdrom: Uniform CD-ROM driver Revision: 3.20
Jul 13 11:37:01 ubuntu kernel: [    2.189955] sr 1:0:0:0: Attached scsi CD-ROM sr0
Jul 13 11:37:01 ubuntu kernel: [    2.189994] sr 1:0:0:0: Attached scsi generic sg0 type 5
Jul 13 11:37:01 ubuntu kernel: [    2.193961] Freeing unused kernel memory: 1480K (ffffffff81f42000 - ffffffff820b4000)
Jul 13 11:37:01 ubuntu kernel: [    2.196703] Write protecting the kernel read-only data: 14336k
Jul 13 11:37:01 ubuntu kernel: [    2.199642] Freeing unused kernel memory: 1860K (ffff88000182f000 - ffff880001a00000)
Jul 13 11:37:01 ubuntu kernel: [    2.201681] Freeing unused kernel memory: 168K (ffff880001dd6000 - ffff880001e00000)
Jul 13 11:37:01 ubuntu kernel: [    2.211625] random: udevadm urandom read with 2 bits of entropy available
Jul 13 11:37:01 ubuntu kernel: [    2.286482] Fusion MPT base driver 3.04.20
Jul 13 11:37:01 ubuntu kernel: [    2.287123] Copyright (c) 1999-2008 LSI Corporation
Jul 13 11:37:01 ubuntu kernel: [    2.289942] VMware vmxnet3 virtual NIC driver - version 1.4.5.0-k-NAPI
Jul 13 11:37:01 ubuntu kernel: [    2.290893] vmxnet3 0000:03:00.0: # of Tx queues : 1, # of Rx queues : 1
Jul 13 11:37:01 ubuntu kernel: [    2.291884] Floppy drive(s): fd0 is 1.44M
Jul 13 11:37:01 ubuntu kernel: [    2.311118] FDC 0 is a post-1991 82077
Jul 13 11:37:01 ubuntu kernel: [    2.321322] Fusion MPT SPI Host driver 3.04.20
Jul 13 11:37:01 ubuntu kernel: [    2.333206] mptbase: ioc0: Initiating bringup
Jul 13 11:37:01 ubuntu kernel: [    2.341890] input: VirtualPS/2 VMware VMMouse as /devices/platform/i8042/serio1/input/input4
Jul 13 11:37:01 ubuntu kernel: [    2.343320] input: VirtualPS/2 VMware VMMouse as /devices/platform/i8042/serio1/input/input3
Jul 13 11:37:01 ubuntu kernel: [    2.364362] vmxnet3 0000:03:00.0 eth0: NIC Link is Up 10000 Mbps
Jul 13 11:37:01 ubuntu kernel: [    2.374060] AVX version of gcm_enc/dec engaged.
Jul 13 11:37:01 ubuntu kernel: [    2.374714] AES CTR mode by8 optimization enabled
Jul 13 11:37:01 ubuntu kernel: [    2.403696] ioc0: LSI53C1030 B0: Capabilities={Initiator}
Jul 13 11:37:01 ubuntu kernel: [    2.418624] vmxnet3 0000:03:00.0 ens160: renamed from eth0
Jul 13 11:37:01 ubuntu kernel: [    2.564926] scsi host2: ioc0: LSI53C1030 B0, FwRev=01032920h, Ports=1, MaxQ=128, IRQ=17
Jul 13 11:37:01 ubuntu kernel: [    2.680325] scsi 2:0:0:0: Direct-Access     VMware   Virtual disk     1.0  PQ: 0 ANSI: 2
Jul 13 11:37:01 ubuntu kernel: [    2.683539] scsi target2:0:0: Beginning Domain Validation
Jul 13 11:37:01 ubuntu kernel: [    2.686316] scsi target2:0:0: Domain Validation skipping write tests
Jul 13 11:37:01 ubuntu kernel: [    2.688763] scsi target2:0:0: Ending Domain Validation
Jul 13 11:37:01 ubuntu kernel: [    2.690966] scsi target2:0:0: FAST-40 WIDE SCSI 80.0 MB/s ST (25 ns, offset 127)
Jul 13 11:37:01 ubuntu kernel: [    2.693489] sd 2:0:0:0: [sda] 20971520 512-byte logical blocks: (10.7 GB/10.0 GiB)
Jul 13 11:37:01 ubuntu kernel: [    2.694890] sd 2:0:0:0: [sda] Write Protect is off
Jul 13 11:37:01 ubuntu kernel: [    2.695781] sd 2:0:0:0: [sda] Mode Sense: 61 00 00 00
Jul 13 11:37:01 ubuntu kernel: [    2.695805] sd 2:0:0:0: Attached scsi generic sg1 type 0
Jul 13 11:37:01 ubuntu kernel: [    2.696927] sd 2:0:0:0: [sda] Cache data unavailable
Jul 13 11:37:01 ubuntu kernel: [    2.697838] sd 2:0:0:0: [sda] Assuming drive cache: write through
Jul 13 11:37:01 ubuntu kernel: [    2.699624]  sda: sda1
Jul 13 11:37:01 ubuntu kernel: [    2.700475] sd 2:0:0:0: [sda] Attached SCSI disk
Jul 13 11:37:01 ubuntu kernel: [    3.852397] md: linear personality registered for level -1
Jul 13 11:37:01 ubuntu kernel: [    3.855925] md: multipath personality registered for level -4
Jul 13 11:37:01 ubuntu kernel: [    3.859468] md: raid0 personality registered for level 0
Jul 13 11:37:01 ubuntu kernel: [    3.863513] md: raid1 personality registered for level 1
Jul 13 11:37:01 ubuntu kernel: [    3.935508] raid6: sse2x1   gen()  6781 MB/s
Jul 13 11:37:01 ubuntu kernel: [    4.003505] raid6: sse2x1   xor()  5327 MB/s
Jul 13 11:37:01 ubuntu kernel: [    4.071502] raid6: sse2x2   gen()  9031 MB/s
Jul 13 11:37:01 ubuntu kernel: [    4.139501] raid6: sse2x2   xor()  7889 MB/s
Jul 13 11:37:01 ubuntu kernel: [    4.207504] raid6: sse2x4   gen() 12146 MB/s
Jul 13 11:37:01 ubuntu kernel: [    4.275502] raid6: sse2x4   xor()  9081 MB/s
Jul 13 11:37:01 ubuntu kernel: [    4.276126] raid6: using algorithm sse2x4 gen() 12146 MB/s
Jul 13 11:37:01 ubuntu kernel: [    4.276899] raid6: .... xor() 9081 MB/s, rmw enabled
Jul 13 11:37:01 ubuntu kernel: [    4.277605] raid6: using ssse3x2 recovery algorithm
Jul 13 11:37:01 ubuntu kernel: [    4.279627] xor: automatically using best checksumming function:
Jul 13 11:37:01 ubuntu kernel: [    4.319500]    avx       : 18154.000 MB/sec
Jul 13 11:37:01 ubuntu kernel: [    4.321345] async_tx: api initialized (async)
Jul 13 11:37:01 ubuntu kernel: [    4.330305] md: raid6 personality registered for level 6
Jul 13 11:37:01 ubuntu kernel: [    4.331074] md: raid5 personality registered for level 5
Jul 13 11:37:01 ubuntu kernel: [    4.331845] md: raid4 personality registered for level 4
Jul 13 11:37:01 ubuntu kernel: [    4.336565] md: raid10 personality registered for level 10
Jul 13 11:37:01 ubuntu kernel: [    4.365524] Btrfs loaded
Jul 13 11:37:01 ubuntu kernel: [    4.459640] blk_update_request: I/O error, dev fd0, sector 0
Jul 13 11:37:01 ubuntu kernel: [    4.461856] floppy: error -5 while reading block 0
Jul 13 11:37:01 ubuntu kernel: [    4.486525] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
Jul 13 11:37:01 ubuntu kernel: [    4.929311] Loading iSCSI transport class v2.0-870.
Jul 13 11:37:01 ubuntu kernel: [    4.939061] EXT4-fs (sda1): re-mounted. Opts: (null)
Jul 13 11:37:01 ubuntu kernel: [    4.956987] iscsi: registered transport (tcp)
Jul 13 11:37:01 ubuntu kernel: [    5.053542] iscsi: registered transport (iser)
Jul 13 11:37:01 ubuntu kernel: [    5.432525] parport_pc 00:05: reported by Plug and Play ACPI
Jul 13 11:37:01 ubuntu kernel: [    5.432714] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
Jul 13 11:37:01 ubuntu kernel: [    5.525818] vmw_vmci 0000:00:07.7: Found VMCI PCI device at 0x11080, irq 16
Jul 13 11:37:01 ubuntu kernel: [    5.525887] vmw_vmci 0000:00:07.7: Using capabilities 0xc
Jul 13 11:37:01 ubuntu kernel: [    5.526425] Guest personality initialized and is active
Jul 13 11:37:01 ubuntu kernel: [    5.526459] VMCI host device registered (name=vmci, major=10, minor=55)
Jul 13 11:37:01 ubuntu kernel: [    5.526460] Initialized host personality
Jul 13 11:37:01 ubuntu kernel: [    5.637782] random: nonblocking pool is initialized
Jul 13 11:37:01 ubuntu kernel: [    5.725909] ip_tables: (C) 2000-2006 Netfilter Core Team
Jul 13 11:37:01 ubuntu kernel: [    5.760921] nf_conntrack version 0.5.0 (7940 buckets, 31760 max)
Jul 13 11:37:01 ubuntu kernel: [    5.839619] ip6_tables: (C) 2000-2006 Netfilter Core Team
Jul 13 11:37:01 ubuntu kernel: [    5.865422] audit: type=1400 audit(1468406221.312:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="lxc-container-default" pid=682 comm="apparmor_parser"
Jul 13 11:37:01 ubuntu kernel: [    5.865426] audit: type=1400 audit(1468406221.312:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="lxc-container-default-cgns" pid=682 comm="apparmor_parser"
Jul 13 11:37:01 ubuntu kernel: [    5.865429] audit: type=1400 audit(1468406221.312:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="lxc-container-default-with-mounting" pid=682 comm="apparmor_parser"
Jul 13 11:37:01 ubuntu kernel: [    5.865432] audit: type=1400 audit(1468406221.312:5): apparmor="STATUS" operation="profile_load" profile="unconfined" name="lxc-container-default-with-nesting" pid=682 comm="apparmor_parser"
Jul 13 11:37:01 ubuntu kernel: [    5.869673] audit: type=1400 audit(1468406221.316:6): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=685 comm="apparmor_parser"
Jul 13 11:37:01 ubuntu kernel: [    5.869677] audit: type=1400 audit(1468406221.316:7): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=685 comm="apparmor_parser"
Jul 13 11:37:01 ubuntu kernel: [    5.869680] audit: type=1400 audit(1468406221.316:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-helper" pid=685 comm="apparmor_parser"
Jul 13 11:37:01 ubuntu kernel: [    5.869682] audit: type=1400 audit(1468406221.316:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=685 comm="apparmor_parser"
Jul 13 11:37:01 ubuntu kernel: [    5.872437] audit: type=1400 audit(1468406221.320:10): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/bin/freshclam" pid=687 comm="apparmor_parser"
Jul 13 11:37:01 ubuntu kernel: [    5.897362] ppdev: user-space parallel port driver
Jul 13 11:37:01 ubuntu kernel: [    5.984436] vmxnet3 0000:03:00.0 ens160: intr type 3, mode 0, 2 vectors allocated
Jul 13 11:37:01 ubuntu kernel: [    5.985758] vmxnet3 0000:03:00.0 ens160: NIC Link is Up 10000 Mbps
Jul 13 11:37:01 ubuntu kernel: [    5.990671] IPv4: martian source 255.255.255.255 from 10.128.3.132, on dev ens160
Jul 13 11:37:01 ubuntu kernel: [    5.990673] ll header: 00000000: ff ff ff ff ff ff 00 50 56 b5 50 c0 08 00        .......PV.P...
Jul 13 11:37:01 ubuntu kernel: [    5.991642] IPv4: martian source 255.255.255.255 from 10.128.3.132, on dev ens160
Jul 13 11:37:01 ubuntu kernel: [    5.991643] ll header: 00000000: ff ff ff ff ff ff 00 50 56 b5 50 c0 08 00        .......PV.P...
Jul 13 11:37:01 ubuntu kernel: [    6.197162] cgroup: new mount options do not match the existing superblock, will be ignored
Jul 13 11:37:01 ubuntu kernel: [    6.435206] NET: Registered protocol family 40



```

---

### Post by MAFoElffen on 2016-07-16
On my ESXi Server, I applied patch 6.0.2 about a month ago.What patch level are you at? 

So you already upgraded the VM's hardware version to 11 and it does not boot?  Did you do a snap shot or backup before you did that upgrade,s o you could revert back?

If not, it is still an accepted method to create a New VM in the hardware version -1 (10) and mount attach the disk of your non-booting version to it... Just saying. 

Re: [https://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=1028019](https://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=1028019)

That was something various VMware Workstation Pro 11 an 12 users had to do, when they were first released before the first patch release (updates). If your vSphere/Esxi is still at 6.0.0, if you apply your patches, that may be already updated in those patches. 6.0.2 was a cumulative patch (included the interim patches of 6.0 until that point).

---

### Post by MAFoElffen on 2016-07-16
Wait... Just got up this morning...
> **galbally2 said:**
> Kern.log from a WORKING Boot with v10 hardware below.
You said you could install and run a vanilla Server 16.04 on v11. Is there nay way that you could you post the log from that so I could compare to your v10 log on that cloud image?

---

### Post by galballyj on 2016-07-18
ESxi build is latest

---

### Post by galballyj on 2016-07-18
every time i try and post my kern.log i get an error. must be some sort of XSS blocking thing going on. and it wont let me attach it either. any ideas how i can post it?

---

### Post by MAFoElffen on 2016-07-18
If you append a ".txt" extension to the log file you should be able to attach it. On adding it to a post as text, it has to be put within code tags... but even then, there is a max limit on how many characters can be in one post...

... and since the forum rebuild last weekend, there is new security in place that may spit out some things if it thinks it's questionable.

If it's too large to post as an attachment, I guess you could post it at ubuntu.pastebin.com and post the link.

---

### Post by galballyj on 2016-07-20
thanks for the advise. here is the log attached from a base ISO build on v11 hardware

had to zip it as it bust the 19KB limit

[ATTACH]270239[/ATTACH]

---

