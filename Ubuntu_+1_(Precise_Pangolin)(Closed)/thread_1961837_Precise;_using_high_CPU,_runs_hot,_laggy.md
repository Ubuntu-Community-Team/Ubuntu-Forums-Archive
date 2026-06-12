---
title: "Precise; using high CPU, runs hot, laggy"
date: 2012-04-19
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by tobydeemer on 2012-04-19
Hey all-

I've recently installed precise on my laptop, fresh install. The machine is HP DV7-1242, running AMD X2 2.1 ghz, dedicated ATI card, 6 GB DDR2, SSD with encrypted home dir. I have a second monitor hooked up as well.

The system uses excessive resources in an idle state- meaning when I'm not doing anything. If I simply log in, run a terminal with htop, Compiz & Unity will cycle between 4-12% continually. Also, the fan seems to run at a much higher level than when the machine was running 10.04, and it far more frequently spins to very high speeds. The laptop overall runs much hotter on Precise than it ever did on Lucid.

I have simliar results running Unity 2D. The CPU usage isn't quite as bad, but only marginally so. It's still far more than Lucid was on Gnome2 with Compiz enabled.

If I watch a youtube or amazon prime video, the machine becomes almost unusable with lag, and the fan spins so fast that I have to crank the volume to even watch the video... 

I avoided the last two releases because of Unity and stayed on Lucid, but I wanted to genuinely give it a shot. From what I see in Precise, apart from what I'm describing here, I really like it. It has some very cool features and improvements. 

However, the great interface suffering under the extreme system load completely removes any benefit. If I can't have a snappy responsive system, I very definitely will revert to Mate, WindowMaker, XFCE or something else. When I bought this machine, it ran Windows Vista. That OS ran more smoothly than Precise is now.

more detailed specs:
AMD Turion(tm) X2 Dual-Core Mobile RM-72
ATI RS780M/RS780MN [Mobility Radeon HD 3200 Graphics]
dpkg -l | grep fglrx >>
fglrx 2:8.960-0ubuntu1 
fglrx-amdcccle 2:8.960-0ubuntu1
uname -a >>
3.2.0-23-generic #36-Ubuntu SMP Tue Apr 10 20:39:51 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

Any suggestions or ideas? I've read through some stuff on Launchpad and in the forums, but what I've seen is related to more specific situations like hardware or apps, etc.

---

### Post by for.i.am.root on 2012-04-19
My advice is to sell the laptop. The DV7 series was recalled due to insufficient thermal dissipation resulting in permanently damaged motherboards. Note that only the AMD version was affected.

I had a DV6700z with similar issues. When I owned mine it was possible to roll your dsdt to correct the ACPI issues you are having.

At least I am assuming it is ACPI issues. Sounds like ACPI anyway. Try acpi=off on your next boot. Also post your dmesg log for further examination.

---

### Post by tobydeemer on 2012-04-19
That's an unacceptable solution. That doesn't address the fact that Unity / Precise are pushing this machine harder than previous versions. I ran this machine as my work laptop for three years on Lucid, hosting a Windows 7 VM every day for work applications. It never ran this hard or hot doing that, regardless of heat issues.

---

### Post by for.i.am.root on 2012-04-19
Hi

I was merely informing you of the current status of that specific laptop and what I would do.

I did extend an invitation to post your dmesg log so I could assist with your issue. My laptop worked fine with Intrepid, however, had ACPI issues with Jaunty. I am assuming you have a similar issue as to mine due to the similarities with our laptops.

It's not overheating because of the work load, it's overheating due to the ACPI not being utilized properly ( I think, however, I need more info.)

If you try booting with acpi=off it will give us an idea as to whether or not that is the issue. You can also try noapic to see if that helps.

Your dmesg log will tell us exactly what the problem is.

I apologize if I upset / offended you in any way.

Note that post Jaunty rolling your own dsdt.aml is no longer supported. Hence why I just switched to lucid 2 months ago.

---

### Post by tobydeemer on 2012-04-20
No, sorry, I rather misinterpreted your comment.

In any event, with the newer grub configs, to boot with acpi=off, should I edit /etc/default/grub, or which file? I haven't had to do that in a while... Also, I'm attaching a txt of dmesg. Thanks for your input. :)

---

### Post by tobydeemer on 2012-04-20
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.2.0-23-generic (buildd@crested) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu4) ) #36-Ubuntu SMP Tue Apr 10 20:39:51 UTC 2012 (Ubuntu 3.2.0-23.36-generic 3.2.14)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-23-generic root=UUID=e85d1618-63bb-44a2-927d-772949d198c3 ro quiet splash vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000afd70000 (usable)
[    0.000000]  BIOS-e820: 00000000afd70000 - 00000000afdbf000 (reserved)
[    0.000000]  BIOS-e820: 00000000afdbf000 - 00000000afe58000 (usable)
[    0.000000]  BIOS-e820: 00000000afe58000 - 00000000afebf000 (ACPI NVS)
[    0.000000]  BIOS-e820: 00000000afebf000 - 00000000afeed000 (usable)
[    0.000000]  BIOS-e820: 00000000afeed000 - 00000000afeff000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000afeff000 - 00000000aff00000 (usable)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000e1000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 00000001c0000000 (usable)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI 2.4 present.
[    0.000000] DMI: Hewlett-Packard HP Pavilion dv7 Notebook PC/30FC, BIOS F.35 12/04/2008
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] No AGP bridge found
[    0.000000] last_pfn = 0x1c0000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-FFFFF uncachable
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 00FFF00000 mask FFFFF00000 write-protect
[    0.000000]   1 base 0000000000 mask FF80000000 write-back
[    0.000000]   2 base 0080000000 mask FFE0000000 write-back
[    0.000000]   3 base 00A0000000 mask FFF0000000 write-back
[    0.000000]   4 base 0100000000 mask FF80000000 write-back
[    0.000000]   5 base 0180000000 mask FFC0000000 write-back
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] TOM2: 00000001c0000000 aka 7168M
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] last_pfn = 0xaff00 max_arch_pfn = 0x400000000
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] Base memory trampoline at [ffff88000009a000] 9a000 size 20480
[    0.000000] init_memory_mapping: 0000000000000000-00000000aff00000
[    0.000000]  0000000000 - 00afe00000 page 2M
[    0.000000]  00afe00000 - 00aff00000 page 4k
[    0.000000] kernel direct mapping tables up to aff00000 @ 1fffb000-20000000
[    0.000000] init_memory_mapping: 0000000100000000-00000001c0000000
[    0.000000]  0100000000 - 01c0000000 page 2M
[    0.000000] kernel direct mapping tables up to 1c0000000 @ afee5000-afeed000
[    0.000000] RAMDISK: 35942000 - 36c99000
[    0.000000] ACPI: RSDP 00000000000fe020 00024 (v02 HP    )
[    0.000000] ACPI: XSDT 00000000afefe120 0005C (v01 HPQOEM SLIC-MPC 00000001      01000013)
[    0.000000] ACPI: FACP 00000000afefd000 000F4 (v04 HP     TRINITY  00000003 LOHR 01000013)
[    0.000000] ACPI: DSDT 00000000afef0000 09FEA (v01 HP     TRINITY  F0000000 LOHR 01000013)
[    0.000000] ACPI: FACS 00000000afe61000 00040
[    0.000000] ACPI: HPET 00000000afefc000 00038 (v01 HPQOEM SLIC-MPC 00000001 LOHR 01000013)
[    0.000000] ACPI: APIC 00000000afefb000 00084 (v02 HPQOEM SLIC-MPC 00000001 LOHR 01000013)
[    0.000000] ACPI: MCFG 00000000afefa000 0003C (v01 HPQOEM SLIC-MPC 00000001 LOHR 01000013)
[    0.000000] ACPI: BOOT 00000000afeef000 00028 (v01 HPQOEM SLIC-MPC 00000001 LOHR 01000013)
[    0.000000] ACPI: SLIC 00000000afeee000 00176 (v01 HPQOEM SLIC-MPC 00000001 LOHR 01000013)
[    0.000000] ACPI: SSDT 00000000afeed000 00386 (v01 AMD    PowerNow 00000001 AMD  00000001)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-00000001c0000000
[    0.000000] Initmem setup node 0 0000000000000000-00000001c0000000
[    0.000000]   NODE_DATA [00000001bfffb000 - 00000001bfffffff]
[    0.000000]  [ffffea0000000000-ffffea0006ffffff] PMD -> [ffff8801b9a00000-ffff8801bf5fffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x001c0000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[6] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x000afd70
[    0.000000]     0: 0x000afdbf -> 0x000afe58
[    0.000000]     0: 0x000afebf -> 0x000afeed
[    0.000000]     0: 0x000afeff -> 0x000aff00
[    0.000000]     0: 0x00100000 -> 0x001c0000
[    0.000000] On node 0 totalpages: 1506759
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 5 pages reserved
[    0.000000]   DMA zone: 3914 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 16320 pages used for memmap
[    0.000000]   DMA32 zone: 700024 pages, LIFO batch:31
[    0.000000]   Normal zone: 12288 pages used for memmap
[    0.000000]   Normal zone: 774144 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x00] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 33, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x1002a201 base: 0xfed00000
[    0.000000] SMP: Allowing 4 CPUs, 2 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000afd70000 - 00000000afdbf000
[    0.000000] PM: Registered nosave memory: 00000000afe58000 - 00000000afebf000
[    0.000000] PM: Registered nosave memory: 00000000afeed000 - 00000000afeff000
[    0.000000] PM: Registered nosave memory: 00000000aff00000 - 00000000e0000000
[    0.000000] PM: Registered nosave memory: 00000000e0000000 - 00000000e1000000
[    0.000000] PM: Registered nosave memory: 00000000e1000000 - 00000000fec00000
[    0.000000] PM: Registered nosave memory: 00000000fec00000 - 00000000fec01000
[    0.000000] PM: Registered nosave memory: 00000000fec01000 - 00000000fee00000
[    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee01000
[    0.000000] PM: Registered nosave memory: 00000000fee01000 - 00000000fff00000
[    0.000000] PM: Registered nosave memory: 00000000fff00000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at aff00000 (gap: aff00000:30100000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:4 nr_node_ids:1
[    0.000000] PERCPU: Embedded 28 pages/cpu @ffff8801bfc00000 s83072 r8192 d23424 u524288
[    0.000000] pcpu-alloc: s83072 r8192 d23424 u524288 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 1478082
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-23-generic root=UUID=e85d1618-63bb-44a2-927d-772949d198c3 ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 5830680k/7340032k available (6566k kernel code, 1312996k absent, 196356k reserved, 6637k data, 920k init)
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=4, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:16640 nr_irqs:712 16
[    0.000000] spurious 8259A interrupt: IRQ7.
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 48234496 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2100.073 MHz processor.
[    0.004005] Calibrating delay loop (skipped), value calculated using timer frequency.. 4200.14 BogoMIPS (lpj=8400292)
[    0.004010] pid_max: default: 32768 minimum: 301
[    0.004044] Security Framework initialized
[    0.004063] AppArmor: AppArmor initialized
[    0.004065] Yama: becoming mindful.
[    0.008835] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.014293] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.016747] Mount-cache hash table entries: 256
[    0.016947] Initializing cgroup subsys cpuacct
[    0.016954] Initializing cgroup subsys memory
[    0.016966] Initializing cgroup subsys devices
[    0.016969] Initializing cgroup subsys freezer
[    0.016971] Initializing cgroup subsys blkio
[    0.016981] Initializing cgroup subsys perf_event
[    0.017020] tseg: 00aff00000
[    0.017022] CPU: Physical Processor ID: 0
[    0.017024] CPU: Processor Core ID: 0
[    0.017027] mce: CPU supports 5 MCE banks
[    0.019648] ACPI: Core revision 20110623
[    0.028016] ftrace: allocating 27049 entries in 107 pages
[    0.032583] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.074960] CPU0: AMD Turion(tm) X2 Dual-Core Mobile RM-72 stepping 01
[    0.076004] Performance Events: AMD PMU driver.
[    0.076004] ... version:                0
[    0.076004] ... bit width:              48
[    0.076004] ... generic registers:      4
[    0.076004] ... value mask:             0000ffffffffffff
[    0.076004] ... max period:             00007fffffffffff
[    0.076004] ... fixed-purpose events:   0
[    0.076004] ... event mask:             000000000000000f
[    0.076004] NMI watchdog enabled, takes one hw-pmu counter.
[    0.076004] Booting Node   0, Processors  #1
[    0.076004] smpboot cpu 1: start_ip = 9a000
[    0.164009] TSC synchronization [CPU#0 -> CPU#1]:
[    0.164009] Measured 204578897 cycles TSC warp between CPUs, turning off TSC clock.
[    0.164009] Marking TSC unstable due to check_tsc_sync_source failed
[    0.164033] NMI watchdog enabled, takes one hw-pmu counter.
[    0.164067] Brought up 2 CPUs
[    0.164070] Total of 2 processors activated (8389.88 BogoMIPS).
[    0.164696] devtmpfs: initialized
[    0.165972] EVM: security.selinux
[    0.165974] EVM: security.SMACK64
[    0.165976] EVM: security.capability
[    0.166062] PM: Registering ACPI NVS region at afe58000 (421888 bytes)
[    0.168359] print_constraints: dummy: 
[    0.168427] RTC time:  4:01:32, date: 04/20/12
[    0.168481] NET: Registered protocol family 16
[    0.168691] TOM: 00000000c0000000 aka 3072M
[    0.168691] Fam 10h mmconf [mem 0xe0000000-0xe0ffffff]
[    0.168691] TOM2: 00000001c0000000 aka 7168M
[    0.168691] Trying to unpack rootfs image as initramfs...
[    0.168778] Extended Config Space enabled on 0 nodes
[    0.168795] ACPI: bus type pci registered
[    0.168922] PCI: MMCONFIG for domain 0000 [bus 00-0f] at [mem 0xe0000000-0xe0ffffff] (base 0xe0000000)
[    0.168927] PCI: MMCONFIG at [mem 0xe0000000-0xe0ffffff] reserved in E820
[    0.171217] PCI: Using configuration type 1 for base access
[    0.172737] bio: create slab <bio-0> at 0
[    0.172872] ACPI: Added _OSI(Module Device)
[    0.172874] ACPI: Added _OSI(Processor Device)
[    0.172876] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.172878] ACPI: Added _OSI(Processor Aggregator Device)
[    0.174225] ACPI: EC: Look up EC in DSDT
[    0.175728] ACPI: Executed 1 blocks of module-level executable AML code
[    0.178267] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.192077] ACPI: Interpreter enabled
[    0.192082] ACPI: (supports S0 S3 S4 S5)
[    0.192110] ACPI: Using IOAPIC for interrupt routing
[    0.192703] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[    0.193020] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[    0.302498] ACPI: EC: GPE = 0x3, I/O: command/status = 0x66, data = 0x62
[    0.302710] ACPI: No dock devices found.
[    0.302712] HEST: Table not found.
[    0.302717] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.303543] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.304813] pci_root PNP0A08:00: host bridge window [io  0x0000-0x0cf7]
[    0.304817] pci_root PNP0A08:00: host bridge window [io  0x0d00-0xffff]
[    0.304820] pci_root PNP0A08:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.304823] pci_root PNP0A08:00: host bridge window [mem 0x000c0000-0x000c3fff]
[    0.304825] pci_root PNP0A08:00: host bridge window [mem 0x000c4000-0x000c7fff]
[    0.304828] pci_root PNP0A08:00: host bridge window [mem 0x000c8000-0x000cbfff]
[    0.304831] pci_root PNP0A08:00: host bridge window [mem 0x000cc000-0x000cffff]
[    0.304834] pci_root PNP0A08:00: host bridge window [mem 0x000d0000-0x000d3fff]
[    0.304837] pci_root PNP0A08:00: host bridge window [mem 0x000d4000-0x000d7fff]
[    0.304840] pci_root PNP0A08:00: host bridge window [mem 0x000d8000-0x000dbfff]
[    0.304842] pci_root PNP0A08:00: host bridge window [mem 0x000dc000-0x000dffff]
[    0.304845] pci_root PNP0A08:00: host bridge window [mem 0x000e0000-0x000e3fff]
[    0.304848] pci_root PNP0A08:00: host bridge window [mem 0x000e4000-0x000e7fff]
[    0.304851] pci_root PNP0A08:00: host bridge window [mem 0x000e8000-0x000ebfff]
[    0.304854] pci_root PNP0A08:00: host bridge window [mem 0x000ec000-0x000effff]
[    0.304857] pci_root PNP0A08:00: host bridge window [mem 0xc0000000-0xdfffffff]
[    0.304860] pci_root PNP0A08:00: host bridge window [mem 0xe1000000-0xffffffff]
[    0.304869] pci_root PNP0A08:00: ignoring host bridge window [mem 0x000cc000-0x000cffff] (conflicts with Video ROM [mem 0x000c0000-0x000ce9ff])
[    0.304898] pci 0000:00:00.0: [1022:9600] type 0 class 0x000600
[    0.304987] pci 0000:00:01.0: [103c:9602] type 1 class 0x000604
[    0.305087] pci 0000:00:04.0: [1022:9604] type 1 class 0x000604
[    0.305144] pci 0000:00:04.0: PME# supported from D0 D3hot D3cold
[    0.305149] pci 0000:00:04.0: PME# disabled
[    0.305172] pci 0000:00:05.0: [1022:9605] type 1 class 0x000604
[    0.305228] pci 0000:00:05.0: PME# supported from D0 D3hot D3cold
[    0.305231] pci 0000:00:05.0: PME# disabled
[    0.305254] pci 0000:00:06.0: [1022:9606] type 1 class 0x000604
[    0.305310] pci 0000:00:06.0: PME# supported from D0 D3hot D3cold
[    0.305313] pci 0000:00:06.0: PME# disabled
[    0.305335] pci 0000:00:07.0: [1022:9607] type 1 class 0x000604
[    0.305391] pci 0000:00:07.0: PME# supported from D0 D3hot D3cold
[    0.305395] pci 0000:00:07.0: PME# disabled
[    0.305470] pci 0000:00:11.0: [1002:4391] type 0 class 0x000106
[    0.305494] pci 0000:00:11.0: reg 10: [io  0x8038-0x803f]
[    0.305507] pci 0000:00:11.0: reg 14: [io  0x804c-0x804f]
[    0.305520] pci 0000:00:11.0: reg 18: [io  0x8030-0x8037]
[    0.305532] pci 0000:00:11.0: reg 1c: [io  0x8048-0x804b]
[    0.305544] pci 0000:00:11.0: reg 20: [io  0x8010-0x801f]
[    0.305557] pci 0000:00:11.0: reg 24: [mem 0xd2508000-0xd25083ff]
[    0.305632] pci 0000:00:12.0: [1002:4397] type 0 class 0x000c03
[    0.305649] pci 0000:00:12.0: reg 10: [mem 0xd2507000-0xd2507fff]
[    0.305733] pci 0000:00:12.1: [1002:4398] type 0 class 0x000c03
[    0.305750] pci 0000:00:12.1: reg 10: [mem 0xd2506000-0xd2506fff]
[    0.305841] pci 0000:00:12.2: [1002:4396] type 0 class 0x000c03
[    0.305865] pci 0000:00:12.2: reg 10: [mem 0xd2508500-0xd25085ff]
[    0.305970] pci 0000:00:12.2: supports D1 D2
[    0.305972] pci 0000:00:12.2: PME# supported from D0 D1 D2 D3hot
[    0.305977] pci 0000:00:12.2: PME# disabled
[    0.306008] pci 0000:00:13.0: [1002:4397] type 0 class 0x000c03
[    0.306025] pci 0000:00:13.0: reg 10: [mem 0xd2505000-0xd2505fff]
[    0.306109] pci 0000:00:13.1: [1002:4398] type 0 class 0x000c03
[    0.306126] pci 0000:00:13.1: reg 10: [mem 0xd2504000-0xd2504fff]
[    0.306217] pci 0000:00:13.2: [1002:4396] type 0 class 0x000c03
[    0.306242] pci 0000:00:13.2: reg 10: [mem 0xd2508400-0xd25084ff]
[    0.306346] pci 0000:00:13.2: supports D1 D2
[    0.306348] pci 0000:00:13.2: PME# supported from D0 D1 D2 D3hot
[    0.306354] pci 0000:00:13.2: PME# disabled
[    0.306387] pci 0000:00:14.0: [1002:4385] type 0 class 0x000c05
[    0.306516] pci 0000:00:14.1: [1002:439c] type 0 class 0x000101
[    0.306537] pci 0000:00:14.1: reg 10: [io  0x0000-0x0007]
[    0.306549] pci 0000:00:14.1: reg 14: [io  0x0000-0x0003]
[    0.306562] pci 0000:00:14.1: reg 18: [io  0x0000-0x0007]
[    0.306574] pci 0000:00:14.1: reg 1c: [io  0x0000-0x0003]
[    0.306587] pci 0000:00:14.1: reg 20: [io  0x8000-0x800f]
[    0.306663] pci 0000:00:14.2: [1002:4383] type 0 class 0x000403
[    0.306690] pci 0000:00:14.2: reg 10: [mem 0xd2500000-0xd2503fff 64bit]
[    0.306774] pci 0000:00:14.2: PME# supported from D0 D3hot D3cold
[    0.306779] pci 0000:00:14.2: PME# disabled
[    0.306798] pci 0000:00:14.3: [1002:439d] type 0 class 0x000601
[    0.306895] pci 0000:00:14.4: [1002:4384] type 1 class 0x000604
[    0.306961] pci 0000:00:18.0: [1022:1300] type 0 class 0x000600
[    0.306998] pci 0000:00:18.1: [1022:1301] type 0 class 0x000600
[    0.307027] pci 0000:00:18.2: [1022:1302] type 0 class 0x000600
[    0.307057] pci 0000:00:18.3: [1022:1303] type 0 class 0x000600
[    0.307094] pci 0000:00:18.4: [1022:1304] type 0 class 0x000600
[    0.307202] pci 0000:01:05.0: [1002:9612] type 0 class 0x000300
[    0.307216] pci 0000:01:05.0: reg 10: [mem 0xc0000000-0xcfffffff pref]
[    0.307223] pci 0000:01:05.0: reg 14: [io  0x7000-0x70ff]
[    0.307231] pci 0000:01:05.0: reg 18: [mem 0xd2400000-0xd240ffff]
[    0.307247] pci 0000:01:05.0: reg 24: [mem 0xd2300000-0xd23fffff]
[    0.307276] pci 0000:01:05.0: supports D1 D2
[    0.307293] pci 0000:01:05.1: [1002:960f] type 0 class 0x000403
[    0.307306] pci 0000:01:05.1: reg 10: [mem 0xd2410000-0xd2413fff]
[    0.307357] pci 0000:01:05.1: supports D1 D2
[    0.307440] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.307446] pci 0000:00:01.0:   bridge window [io  0x7000-0x7fff]
[    0.307450] pci 0000:00:01.0:   bridge window [mem 0xd2300000-0xd24fffff]
[    0.307455] pci 0000:00:01.0:   bridge window [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.307493] pci 0000:00:04.0: PCI bridge to [bus 02-07]
[    0.307499] pci 0000:00:04.0:   bridge window [io  0x3000-0x6fff]
[    0.307503] pci 0000:00:04.0:   bridge window [mem 0xd1300000-0xd22fffff]
[    0.307508] pci 0000:00:04.0:   bridge window [mem 0xd0000000-0xd0ffffff 64bit pref]
[    0.307564] pci 0000:08:00.0: [197b:2382] type 0 class 0x000880
[    0.307582] pci 0000:08:00.0: reg 10: [mem 0xd1200300-0xd12003ff]
[    0.307652] pci 0000:08:00.0: reg 30: [mem 0xffff0000-0xffffffff pref]
[    0.307750] pci 0000:08:00.2: [197b:2381] type 0 class 0x000805
[    0.307769] pci 0000:08:00.2: reg 10: [mem 0xd1200200-0xd12002ff]
[    0.307928] pci 0000:08:00.3: [197b:2383] type 0 class 0x000880
[    0.307947] pci 0000:08:00.3: reg 10: [mem 0xd1200100-0xd12001ff]
[    0.308129] pci 0000:08:00.4: [197b:2384] type 0 class 0x000880
[    0.308148] pci 0000:08:00.4: reg 10: [mem 0xd1200000-0xd12000ff]
[    0.316045] pci 0000:00:05.0: PCI bridge to [bus 08-08]
[    0.316052] pci 0000:00:05.0:   bridge window [mem 0xd1200000-0xd12fffff]
[    0.316111] pci 0000:09:00.0: [168c:002a] type 0 class 0x000280
[    0.316133] pci 0000:09:00.0: reg 10: [mem 0xd1100000-0xd110ffff 64bit]
[    0.316238] pci 0000:09:00.0: supports D1
[    0.316241] pci 0000:09:00.0: PME# supported from D0 D1 D3hot
[    0.316246] pci 0000:09:00.0: PME# disabled
[    0.316269] pci 0000:09:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    0.316279] pci 0000:00:06.0: PCI bridge to [bus 09-09]
[    0.316286] pci 0000:00:06.0:   bridge window [mem 0xd1100000-0xd11fffff]
[    0.316344] pci 0000:0a:00.0: [10ec:8136] type 0 class 0x000200
[    0.316360] pci 0000:0a:00.0: reg 10: [io  0x2000-0x20ff]
[    0.316387] pci 0000:0a:00.0: reg 18: [mem 0xd1010000-0xd1010fff 64bit pref]
[    0.316404] pci 0000:0a:00.0: reg 20: [mem 0xd1000000-0xd100ffff 64bit pref]
[    0.316416] pci 0000:0a:00.0: reg 30: [mem 0xfffe0000-0xffffffff pref]
[    0.316476] pci 0000:0a:00.0: supports D1 D2
[    0.316479] pci 0000:0a:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.316484] pci 0000:0a:00.0: PME# disabled
[    0.324033] pci 0000:00:07.0: PCI bridge to [bus 0a-0a]
[    0.324038] pci 0000:00:07.0:   bridge window [io  0x2000-0x2fff]
[    0.324046] pci 0000:00:07.0:   bridge window [mem 0xd1000000-0xd10fffff 64bit pref]
[    0.324122] pci 0000:00:14.4: PCI bridge to [bus 80-8f] (subtractive decode)
[    0.324128] pci 0000:00:14.4:   bridge window [io  0x1000-0x1fff]
[    0.324137] pci 0000:00:14.4:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.324140] pci 0000:00:14.4:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.324143] pci 0000:00:14.4:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.324146] pci 0000:00:14.4:   bridge window [mem 0x000c0000-0x000c3fff] (subtractive decode)
[    0.324150] pci 0000:00:14.4:   bridge window [mem 0x000c4000-0x000c7fff] (subtractive decode)
[    0.324153] pci 0000:00:14.4:   bridge window [mem 0x000c8000-0x000cbfff] (subtractive decode)
[    0.324156] pci 0000:00:14.4:   bridge window [mem 0x000d0000-0x000d3fff] (subtractive decode)
[    0.324159] pci 0000:00:14.4:   bridge window [mem 0x000d4000-0x000d7fff] (subtractive decode)
[    0.324163] pci 0000:00:14.4:   bridge window [mem 0x000d8000-0x000dbfff] (subtractive decode)
[    0.324166] pci 0000:00:14.4:   bridge window [mem 0x000dc000-0x000dffff] (subtractive decode)
[    0.324169] pci 0000:00:14.4:   bridge window [mem 0x000e0000-0x000e3fff] (subtractive decode)
[    0.324173] pci 0000:00:14.4:   bridge window [mem 0x000e4000-0x000e7fff] (subtractive decode)
[    0.324176] pci 0000:00:14.4:   bridge window [mem 0x000e8000-0x000ebfff] (subtractive decode)
[    0.324179] pci 0000:00:14.4:   bridge window [mem 0x000ec000-0x000effff] (subtractive decode)
[    0.324182] pci 0000:00:14.4:   bridge window [mem 0xc0000000-0xdfffffff] (subtractive decode)
[    0.324186] pci 0000:00:14.4:   bridge window [mem 0xe1000000-0xffffffff] (subtractive decode)
[    0.324245] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.324378] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    0.324431] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB4_._PRT]
[    0.324497] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB5_._PRT]
[    0.324576] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP6._PRT]
[    0.324634] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PB7_._PRT]
[    0.324732] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P2P_._PRT]
[    0.325022]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.325387]  pci0000:00: ACPI _OSC request failed (AE_SUPPORT), returned control mask: 0x0d
[    0.325389] ACPI _OSC control for PCIe not granted, disabling ASPM
[    0.335427] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.335483] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.335537] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.335589] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.335642] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.335699] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.335751] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.335804] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.335987] vgaarb: device added: PCI:0000:01:05.0,decodes=io+mem,owns=io+mem,locks=none
[    0.335994] vgaarb: loaded
[    0.335996] vgaarb: bridge control possible 0000:01:05.0
[    0.336170] i2c-core: driver [aat2870] using legacy suspend method
[    0.336172] i2c-core: driver [aat2870] using legacy resume method
[    0.336286] SCSI subsystem initialized
[    0.336379] libata version 3.00 loaded.
[    0.336455] usbcore: registered new interface driver usbfs
[    0.336473] usbcore: registered new interface driver hub
[    0.336512] usbcore: registered new device driver usb
[    0.336640] PCI: Using ACPI for IRQ routing
[    0.337019] PCI: pci_cache_line_size set to 64 bytes
[    0.337213] reserve RAM buffer: 000000000009fc00 - 000000000009ffff 
[    0.337217] reserve RAM buffer: 00000000afd70000 - 00000000afffffff 
[    0.337221] reserve RAM buffer: 00000000afe58000 - 00000000afffffff 
[    0.337224] reserve RAM buffer: 00000000afeed000 - 00000000afffffff 
[    0.337228] reserve RAM buffer: 00000000aff00000 - 00000000afffffff 
[    0.337370] NetLabel: Initializing
[    0.337372] NetLabel:  domain hash size = 128
[    0.337374] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.337392] NetLabel:  unlabeled traffic allowed by default
[    0.337497] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0
[    0.337503] hpet0: 4 comparators, 32-bit 14.318180 MHz counter
[    0.339538] Switching to clocksource hpet
[    0.346688] AppArmor: AppArmor Filesystem Enabled
[    0.346734] pnp: PnP ACPI init
[    0.346758] ACPI: bus type pnp registered
[    0.347422] pnp 00:00: [bus 00-ff]
[    0.347426] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.347428] pnp 00:00: [io  0x0d00-0xffff window]
[    0.347431] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.347434] pnp 00:00: [mem 0x000c0000-0x000c3fff window]
[    0.347437] pnp 00:00: [mem 0x000c4000-0x000c7fff window]
[    0.347440] pnp 00:00: [mem 0x000c8000-0x000cbfff window]
[    0.347442] pnp 00:00: [mem 0x000cc000-0x000cffff window]
[    0.347445] pnp 00:00: [mem 0x000d0000-0x000d3fff window]
[    0.347448] pnp 00:00: [mem 0x000d4000-0x000d7fff window]
[    0.347451] pnp 00:00: [mem 0x000d8000-0x000dbfff window]
[    0.347454] pnp 00:00: [mem 0x000dc000-0x000dffff window]
[    0.347456] pnp 00:00: [mem 0x000e0000-0x000e3fff window]
[    0.347459] pnp 00:00: [mem 0x000e4000-0x000e7fff window]
[    0.347462] pnp 00:00: [mem 0x000e8000-0x000ebfff window]
[    0.347465] pnp 00:00: [mem 0x000ec000-0x000effff window]
[    0.347468] pnp 00:00: [mem 0xc0000000-0xdfffffff window]
[    0.347470] pnp 00:00: [mem 0xe1000000-0xffffffff window]
[    0.347473] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.347573] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    0.347638] pnp 00:01: [mem 0xfec00000-0xfec00fff]
[    0.347641] pnp 00:01: [mem 0xfee00000-0xfee00fff]
[    0.347735] system 00:01: [mem 0xfec00000-0xfec00fff] could not be reserved
[    0.347739] system 00:01: [mem 0xfee00000-0xfee00fff] has been reserved
[    0.347743] system 00:01: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.347908] pnp 00:02: [io  0x0000-0x000f]
[    0.347910] pnp 00:02: [io  0x0081-0x008f]
[    0.347913] pnp 00:02: [io  0x00c0-0x00df]
[    0.347916] pnp 00:02: [dma 4]
[    0.347956] pnp 00:02: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.347967] pnp 00:03: [io  0x00f0-0x00fe]
[    0.348070] pnp 00:03: [irq 13]
[    0.348112] pnp 00:03: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.348181] pnp 00:04: [io  0x0070-0x0071]
[    0.348224] pnp 00:04: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.348235] pnp 00:05: [io  0x0061]
[    0.348275] pnp 00:05: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.348288] pnp 00:06: [io  0x0060]
[    0.348291] pnp 00:06: [io  0x0064]
[    0.348330] pnp 00:06: [irq 1]
[    0.348374] pnp 00:06: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.348422] pnp 00:07: [irq 12]
[    0.348467] pnp 00:07: Plug and Play ACPI device, IDs SYN0153 AUI0216 AUI0217 PNP0f13 (active)
[    0.348482] pnp 00:08: [io  0x0010-0x001f]
[    0.348488] pnp 00:08: [io  0x002e-0x002f]
[    0.348490] pnp 00:08: [io  0x0072-0x0073]
[    0.348493] pnp 00:08: [io  0x0080]
[    0.348495] pnp 00:08: [io  0x00b0-0x00b1]
[    0.348497] pnp 00:08: [io  0x0092]
[    0.348499] pnp 00:08: [io  0x0400-0x04cf]
[    0.348502] pnp 00:08: [io  0x04d0-0x04d1]
[    0.348504] pnp 00:08: [io  0x04d6]
[    0.348506] pnp 00:08: [io  0x0680-0x06ff]
[    0.348509] pnp 00:08: [io  0x077a]
[    0.348511] pnp 00:08: [io  0x0c00-0x0c01]
[    0.348513] pnp 00:08: [io  0x0c14]
[    0.348515] pnp 00:08: [io  0x0c50-0x0c52]
[    0.348518] pnp 00:08: [io  0x0c6c]
[    0.348520] pnp 00:08: [io  0x0c6f]
[    0.348522] pnp 00:08: [io  0x0cd0-0x0cdb]
[    0.348604] system 00:08: [io  0x0400-0x04cf] has been reserved
[    0.348608] system 00:08: [io  0x04d0-0x04d1] has been reserved
[    0.348611] system 00:08: [io  0x04d6] has been reserved
[    0.348614] system 00:08: [io  0x0680-0x06ff] has been reserved
[    0.348617] system 00:08: [io  0x077a] has been reserved
[    0.348620] system 00:08: [io  0x0c00-0x0c01] has been reserved
[    0.348624] system 00:08: [io  0x0c14] has been reserved
[    0.348627] system 00:08: [io  0x0c50-0x0c52] has been reserved
[    0.348630] system 00:08: [io  0x0c6c] has been reserved
[    0.348633] system 00:08: [io  0x0c6f] has been reserved
[    0.348637] system 00:08: [io  0x0cd0-0x0cdb] has been reserved
[    0.348640] system 00:08: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.348659] pnp 00:09: [mem 0x000e0000-0x000fffff]
[    0.348662] pnp 00:09: [mem 0xfff00000-0xffffffff]
[    0.348736] system 00:09: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.348740] system 00:09: [mem 0xfff00000-0xffffffff] has been reserved
[    0.348744] system 00:09: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.396109] pnp 00:0a: [io  0xfd60-0xfd63]
[    0.396149] pnp 00:0a: [irq 4]
[    0.396203] pnp 00:0a: Plug and Play ACPI device, IDs ENE0100 (active)
[    0.396240] pnp 00:0b: [irq 23]
[    0.396289] pnp 00:0b: Plug and Play ACPI device, IDs HPQ0004 (active)
[    0.396476] pnp: PnP ACPI: found 12 devices
[    0.396478] ACPI: ACPI bus type pnp unregistered
[    0.403720] pci 0000:08:00.0: no compatible bridge window for [mem 0xffff0000-0xffffffff pref]
[    0.403731] pci 0000:0a:00.0: no compatible bridge window for [mem 0xfffe0000-0xffffffff pref]
[    0.403738] PCI: max bus depth: 1 pci_try_num: 2
[    0.403831] pci 0000:00:05.0: BAR 15: assigned [mem 0xd2600000-0xd26fffff pref]
[    0.403836] pci 0000:00:07.0: BAR 14: assigned [mem 0xd2700000-0xd27fffff]
[    0.403843] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.403846] pci 0000:00:01.0:   bridge window [io  0x7000-0x7fff]
[    0.403851] pci 0000:00:01.0:   bridge window [mem 0xd2300000-0xd24fffff]
[    0.403855] pci 0000:00:01.0:   bridge window [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.403861] pci 0000:00:04.0: PCI bridge to [bus 02-07]
[    0.403864] pci 0000:00:04.0:   bridge window [io  0x3000-0x6fff]
[    0.403869] pci 0000:00:04.0:   bridge window [mem 0xd1300000-0xd22fffff]
[    0.403873] pci 0000:00:04.0:   bridge window [mem 0xd0000000-0xd0ffffff 64bit pref]
[    0.403881] pci 0000:08:00.0: BAR 6: assigned [mem 0xd2600000-0xd260ffff pref]
[    0.403884] pci 0000:00:05.0: PCI bridge to [bus 08-08]
[    0.403889] pci 0000:00:05.0:   bridge window [mem 0xd1200000-0xd12fffff]
[    0.403893] pci 0000:00:05.0:   bridge window [mem 0xd2600000-0xd26fffff pref]
[    0.403899] pci 0000:00:06.0: PCI bridge to [bus 09-09]
[    0.403903] pci 0000:00:06.0:   bridge window [mem 0xd1100000-0xd11fffff]
[    0.403911] pci 0000:0a:00.0: BAR 6: assigned [mem 0xd1020000-0xd103ffff pref]
[    0.403914] pci 0000:00:07.0: PCI bridge to [bus 0a-0a]
[    0.403917] pci 0000:00:07.0:   bridge window [io  0x2000-0x2fff]
[    0.403922] pci 0000:00:07.0:   bridge window [mem 0xd2700000-0xd27fffff]
[    0.403926] pci 0000:00:07.0:   bridge window [mem 0xd1000000-0xd10fffff 64bit pref]
[    0.403932] pci 0000:00:14.4: PCI bridge to [bus 80-8f]
[    0.403970] pci 0000:00:14.4:   bridge window [io  0x1000-0x1fff]
[    0.404020] pci 0000:00:01.0: setting latency timer to 64
[    0.404049] pci 0000:00:04.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.404054] pci 0000:00:04.0: setting latency timer to 64
[    0.404064] pci 0000:00:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.404069] pci 0000:00:05.0: setting latency timer to 64
[    0.404080] pci 0000:00:06.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.404084] pci 0000:00:06.0: setting latency timer to 64
[    0.404094] pci 0000:00:07.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.404098] pci 0000:00:07.0: setting latency timer to 64
[    0.404108] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.404111] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.404114] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.404117] pci_bus 0000:00: resource 7 [mem 0x000c0000-0x000c3fff]
[    0.404119] pci_bus 0000:00: resource 8 [mem 0x000c4000-0x000c7fff]
[    0.404122] pci_bus 0000:00: resource 9 [mem 0x000c8000-0x000cbfff]
[    0.404125] pci_bus 0000:00: resource 10 [mem 0x000d0000-0x000d3fff]
[    0.404128] pci_bus 0000:00: resource 11 [mem 0x000d4000-0x000d7fff]
[    0.404130] pci_bus 0000:00: resource 12 [mem 0x000d8000-0x000dbfff]
[    0.404133] pci_bus 0000:00: resource 13 [mem 0x000dc000-0x000dffff]
[    0.404136] pci_bus 0000:00: resource 14 [mem 0x000e0000-0x000e3fff]
[    0.404139] pci_bus 0000:00: resource 15 [mem 0x000e4000-0x000e7fff]
[    0.404141] pci_bus 0000:00: resource 16 [mem 0x000e8000-0x000ebfff]
[    0.404144] pci_bus 0000:00: resource 17 [mem 0x000ec000-0x000effff]
[    0.404147] pci_bus 0000:00: resource 18 [mem 0xc0000000-0xdfffffff]
[    0.404150] pci_bus 0000:00: resource 19 [mem 0xe1000000-0xffffffff]
[    0.404153] pci_bus 0000:01: resource 0 [io  0x7000-0x7fff]
[    0.404156] pci_bus 0000:01: resource 1 [mem 0xd2300000-0xd24fffff]
[    0.404159] pci_bus 0000:01: resource 2 [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.404162] pci_bus 0000:02: resource 0 [io  0x3000-0x6fff]
[    0.404165] pci_bus 0000:02: resource 1 [mem 0xd1300000-0xd22fffff]
[    0.404168] pci_bus 0000:02: resource 2 [mem 0xd0000000-0xd0ffffff 64bit pref]
[    0.404172] pci_bus 0000:08: resource 1 [mem 0xd1200000-0xd12fffff]
[    0.404175] pci_bus 0000:08: resource 2 [mem 0xd2600000-0xd26fffff pref]
[    0.404178] pci_bus 0000:09: resource 1 [mem 0xd1100000-0xd11fffff]
[    0.404181] pci_bus 0000:0a: resource 0 [io  0x2000-0x2fff]
[    0.404184] pci_bus 0000:0a: resource 1 [mem 0xd2700000-0xd27fffff]
[    0.404187] pci_bus 0000:0a: resource 2 [mem 0xd1000000-0xd10fffff 64bit pref]
[    0.404190] pci_bus 0000:80: resource 0 [io  0x1000-0x1fff]
[    0.404193] pci_bus 0000:80: resource 4 [io  0x0000-0x0cf7]
[    0.404196] pci_bus 0000:80: resource 5 [io  0x0d00-0xffff]
[    0.404199] pci_bus 0000:80: resource 6 [mem 0x000a0000-0x000bffff]
[    0.404202] pci_bus 0000:80: resource 7 [mem 0x000c0000-0x000c3fff]
[    0.404205] pci_bus 0000:80: resource 8 [mem 0x000c4000-0x000c7fff]
[    0.404207] pci_bus 0000:80: resource 9 [mem 0x000c8000-0x000cbfff]
[    0.404210] pci_bus 0000:80: resource 10 [mem 0x000d0000-0x000d3fff]
[    0.404213] pci_bus 0000:80: resource 11 [mem 0x000d4000-0x000d7fff]
[    0.404216] pci_bus 0000:80: resource 12 [mem 0x000d8000-0x000dbfff]
[    0.404219] pci_bus 0000:80: resource 13 [mem 0x000dc000-0x000dffff]
[    0.404222] pci_bus 0000:80: resource 14 [mem 0x000e0000-0x000e3fff]
[    0.404225] pci_bus 0000:80: resource 15 [mem 0x000e4000-0x000e7fff]
[    0.404228] pci_bus 0000:80: resource 16 [mem 0x000e8000-0x000ebfff]
[    0.404231] pci_bus 0000:80: resource 17 [mem 0x000ec000-0x000effff]
[    0.404234] pci_bus 0000:80: resource 18 [mem 0xc0000000-0xdfffffff]
[    0.404237] pci_bus 0000:80: resource 19 [mem 0xe1000000-0xffffffff]
[    0.404303] NET: Registered protocol family 2
[    0.404640] IP route cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.407479] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.412740] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.413427] TCP: Hash tables configured (established 524288 bind 65536)
[    0.413430] TCP reno registered
[    0.413462] UDP hash table entries: 4096 (order: 5, 131072 bytes)
[    0.413565] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
[    0.413784] NET: Registered protocol family 1
[    0.413801] pci 0000:00:01.0: MSI quirk detected; subordinate MSI disabled
[    0.413872] pci 0000:00:12.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.468084] pci 0000:00:12.0: PCI INT A disabled
[    0.468094] pci 0000:00:12.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.524066] pci 0000:00:12.1: PCI INT A disabled
[    0.524078] pci 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.524104] pci 0000:00:12.2: PCI INT B disabled
[    0.524114] pci 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.580063] pci 0000:00:13.0: PCI INT A disabled
[    0.580074] pci 0000:00:13.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.634456] Freeing initrd memory: 19804k freed
[    0.636061] pci 0000:00:13.1: PCI INT A disabled
[    0.636074] pci 0000:00:13.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.636098] pci 0000:00:13.2: PCI INT B disabled
[    0.636133] pci 0000:01:05.0: Boot video device
[    0.636159] PCI: CLS 64 bytes, default 64
[    0.636163] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.636166] Placing 64MB software IO TLB between ffff8800abd70000 - ffff8800afd70000
[    0.636169] software IO TLB at phys 0xabd70000 - 0xafd70000
[    0.636213] Simple Boot Flag at 0x44 set to 0x1
[    0.636798] audit: initializing netlink socket (disabled)
[    0.636814] type=2000 audit(1334894491.636:1): initialized
[    0.692900] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.753327] VFS: Disk quotas dquot_6.5.2
[    0.753412] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.754264] fuse init (API version 7.17)
[    0.754585] msgmni has been set to 11426
[    0.756198] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.756486] io scheduler noop registered
[    0.756490] io scheduler deadline registered
[    0.756542] io scheduler cfq registered (default)
[    0.756731] pcieport 0000:00:04.0: setting latency timer to 64
[    0.756779] pcieport 0000:00:04.0: irq 40 for MSI/MSI-X
[    0.756846] pcieport 0000:00:05.0: setting latency timer to 64
[    0.756882] pcieport 0000:00:05.0: irq 41 for MSI/MSI-X
[    0.756946] pcieport 0000:00:06.0: setting latency timer to 64
[    0.756982] pcieport 0000:00:06.0: irq 42 for MSI/MSI-X
[    0.757043] pcieport 0000:00:07.0: setting latency timer to 64
[    0.757078] pcieport 0000:00:07.0: irq 43 for MSI/MSI-X
[    0.757170] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.757203] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.757401] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.757494] ACPI: AC Adapter [ACAD] (on-line)
[    0.757567] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    0.757575] ACPI: Power Button [PWRB]
[    0.757646] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
[    0.757750] ACPI: Lid Switch [LID]
[    0.757806] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.757810] ACPI: Power Button [PWRF]
[    0.856432] thermal LNXTHERM:00: registered as thermal_zone0
[    0.856435] ACPI: Thermal Zone [TZ01] (65 C)
[    0.856463] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.856474] ACPI: Battery Slot [BAT0] (battery present)
[    0.856509] ERST: Table is not found!
[    0.856511] GHES: HEST is not enabled!
[    0.856695] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.948655] Linux agpgart interface v0.103
[    0.952447] brd: module loaded
[    0.954332] loop: module loaded
[    0.954539] ahci 0000:00:11.0: version 3.0
[    0.954604] ahci 0000:00:11.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[    0.954853] ahci 0000:00:11.0: AHCI 0001.0100 32 slots 6 ports 3 Gbps 0x3f impl SATA mode
[    0.954858] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part ccc 
[    0.956605] scsi0 : ahci
[    0.956956] scsi1 : ahci
[    0.957287] scsi2 : ahci
[    0.957603] scsi3 : ahci
[    0.957913] scsi4 : ahci
[    0.958233] scsi5 : ahci
[    0.958335] ata1: SATA max UDMA/133 abar m1024@0xd2508000 port 0xd2508100 irq 22
[    0.958340] ata2: SATA max UDMA/133 abar m1024@0xd2508000 port 0xd2508180 irq 22
[    0.958345] ata3: SATA max UDMA/133 abar m1024@0xd2508000 port 0xd2508200 irq 22
[    0.958349] ata4: SATA max UDMA/133 abar m1024@0xd2508000 port 0xd2508280 irq 22
[    0.958353] ata5: SATA max UDMA/133 abar m1024@0xd2508000 port 0xd2508300 irq 22
[    0.958358] ata6: SATA max UDMA/133 abar m1024@0xd2508000 port 0xd2508380 irq 22
[    0.958560] pata_acpi 0000:00:14.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.958605] pata_acpi 0000:00:14.1: setting latency timer to 64
[    0.959077] Fixed MDIO Bus: probed
[    0.959105] tun: Universal TUN/TAP device driver, 1.6
[    0.959107] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.959226] PPP generic driver version 2.4.2
[    0.959612] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.959632] ehci_hcd 0000:00:12.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.959667] ehci_hcd 0000:00:12.2: setting latency timer to 64
[    0.959672] ehci_hcd 0000:00:12.2: EHCI Host Controller
[    0.959847] ehci_hcd 0000:00:12.2: new USB bus registered, assigned bus number 1
[    0.959859] ehci_hcd 0000:00:12.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    0.959895] QUIRK: Enable AMD PLL fix
[    0.959899] ehci_hcd 0000:00:12.2: applying AMD SB600/SB700 USB freeze workaround
[    0.959916] ehci_hcd 0000:00:12.2: debug port 1
[    0.959950] ehci_hcd 0000:00:12.2: irq 17, io mem 0xd2508500
[    0.968057] ehci_hcd 0000:00:12.2: USB 2.0 started, EHCI 1.00
[    0.968329] hub 1-0:1.0: USB hub found
[    0.968335] hub 1-0:1.0: 6 ports detected
[    0.968529] ehci_hcd 0000:00:13.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.968546] ehci_hcd 0000:00:13.2: setting latency timer to 64
[    0.968550] ehci_hcd 0000:00:13.2: EHCI Host Controller
[    0.968619] ehci_hcd 0000:00:13.2: new USB bus registered, assigned bus number 2
[    0.968628] ehci_hcd 0000:00:13.2: applying AMD SB700/SB800/Hudson-2/3 EHCI dummy qh workaround
[    0.968645] ehci_hcd 0000:00:13.2: applying AMD SB600/SB700 USB freeze workaround
[    0.968662] ehci_hcd 0000:00:13.2: debug port 1
[    0.968687] ehci_hcd 0000:00:13.2: irq 19, io mem 0xd2508400
[    0.980057] ehci_hcd 0000:00:13.2: USB 2.0 started, EHCI 1.00
[    0.980204] hub 2-0:1.0: USB hub found
[    0.980208] hub 2-0:1.0: 6 ports detected
[    0.980348] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.980399] ohci_hcd 0000:00:12.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.980415] ohci_hcd 0000:00:12.0: setting latency timer to 64
[    0.980420] ohci_hcd 0000:00:12.0: OHCI Host Controller
[    0.980595] ohci_hcd 0000:00:12.0: new USB bus registered, assigned bus number 3
[    0.980629] ohci_hcd 0000:00:12.0: irq 16, io mem 0xd2507000
[    1.040186] hub 3-0:1.0: USB hub found
[    1.040216] hub 3-0:1.0: 3 ports detected
[    1.040310] ohci_hcd 0000:00:12.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.040327] ohci_hcd 0000:00:12.1: setting latency timer to 64
[    1.040331] ohci_hcd 0000:00:12.1: OHCI Host Controller
[    1.040559] ohci_hcd 0000:00:12.1: new USB bus registered, assigned bus number 4
[    1.040579] ohci_hcd 0000:00:12.1: irq 16, io mem 0xd2506000
[    1.100179] hub 4-0:1.0: USB hub found
[    1.100209] hub 4-0:1.0: 3 ports detected
[    1.100344] ohci_hcd 0000:00:13.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.100362] ohci_hcd 0000:00:13.0: setting latency timer to 64
[    1.100366] ohci_hcd 0000:00:13.0: OHCI Host Controller
[    1.100432] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus number 5
[    1.100464] ohci_hcd 0000:00:13.0: irq 18, io mem 0xd2505000
[    1.160209] hub 5-0:1.0: USB hub found
[    1.160249] hub 5-0:1.0: 3 ports detected
[    1.160345] ohci_hcd 0000:00:13.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.160368] ohci_hcd 0000:00:13.1: setting latency timer to 64
[    1.160372] ohci_hcd 0000:00:13.1: OHCI Host Controller
[    1.160438] ohci_hcd 0000:00:13.1: new USB bus registered, assigned bus number 6
[    1.160459] ohci_hcd 0000:00:13.1: irq 18, io mem 0xd2504000
[    1.220198] hub 6-0:1.0: USB hub found
[    1.220229] hub 6-0:1.0: 3 ports detected
[    1.220331] uhci_hcd: USB Universal Host Controller Interface driver
[    1.220422] usbcore: registered new interface driver libusual
[    1.220480] i8042: PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.256195] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.256203] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.256608] mousedev: PS/2 mouse device common for all mice
[    1.259097] rtc_cmos 00:04: RTC can wake from S4
[    1.259228] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    1.259260] rtc0: alarms up to one day, 114 bytes nvram, hpet irqs
[    1.259379] device-mapper: uevent: version 1.0.3
[    1.259516] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
[    1.259527] cpuidle: using governor ladder
[    1.259530] cpuidle: using governor menu
[    1.259532] EFI Variables Facility v0.08 2004-May-17
[    1.259890] TCP cubic registered
[    1.260098] NET: Registered protocol family 10
[    1.260764] NET: Registered protocol family 17
[    1.260791] Registering the dns_resolver key type
[    1.261050] PM: Hibernation image not present or could not be loaded.
[    1.261068] registered taskstats version 1
[    1.280107] ata3: SATA link down (SStatus 0 SControl 300)
[    1.280174] ata6: SATA link down (SStatus 0 SControl 300)
[    1.280229] ata5: SATA link down (SStatus 0 SControl 300)
[    1.301062]   Magic number: 8:871:9
[    1.301075] hub 4-0:1.0: hash matches
[    1.301248] rtc_cmos 00:04: setting system clock to 2012-04-20 04:01:33 UTC (1334894493)
[    1.301384] powernow-k8: Found 1 AMD Turion(tm) X2 Dual-Core Mobile RM-72 (2 cpu cores) (version 2.20.00)
[    1.301432] powernow-k8:    0 : pstate 0 (2100 MHz)
[    1.301434] powernow-k8:    1 : pstate 1 (1050 MHz)
[    1.301437] powernow-k8:    2 : pstate 2 (525 MHz)
[    1.302874] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.302877] EDD information not available.
[    1.310419] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    1.316135] ACPI: Battery Slot [BAT0] (battery present)
[    1.392085] usb 1-6: new high-speed USB device number 4 using ehci_hcd
[    1.452058] ata4: softreset failed (device not ready)
[    1.452062] ata4: applying PMP SRST workaround and retrying
[    1.452082] ata1: softreset failed (device not ready)
[    1.452087] ata1: applying PMP SRST workaround and retrying
[    1.452105] ata2: softreset failed (device not ready)
[    1.452109] ata2: applying PMP SRST workaround and retrying
[    1.624069] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.624101] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.624131] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.635868] ata1.00: ATA-8: Patriot PS-100 32GB SSD, VER3.002, max UDMA/100
[    1.635872] ata1.00: 62533296 sectors, multi 1: LBA48 
[    1.636972] ata4.00: ATAPI: Optiarc DVD RW AD-7561S, AH03, max UDMA/100
[    1.637305] ata1.00: configured for UDMA/100
[    1.637558] scsi 0:0:0:0: Direct-Access     ATA      Patriot PS-100 3 VER3 PQ: 0 ANSI: 5
[    1.637765] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.637786] sd 0:0:0:0: [sda] 62533296 512-byte logical blocks: (32.0 GB/29.8 GiB)
[    1.637956] sd 0:0:0:0: [sda] Write Protect is off
[    1.637960] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.638013] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.640810]  sda: sda1 sda2 < sda5 >
[    1.642005] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.650573] ata4.00: configured for UDMA/100
[    1.654777] ata2.00: ATA-8: WDC WD3200BEKT-00F3T0, 11.01A11, max UDMA/133
[    1.654781] ata2.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.657538] ata2.00: configured for UDMA/133
[    1.657788] scsi 1:0:0:0: Direct-Access     ATA      WDC WD3200BEKT-0 11.0 PQ: 0 ANSI: 5
[    1.657953] sd 1:0:0:0: Attached scsi generic sg1 type 0
[    1.657960] sd 1:0:0:0: [sdb] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    1.658029] sd 1:0:0:0: [sdb] Write Protect is off
[    1.658033] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    1.658098] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.658984] scsi 3:0:0:0: CD-ROM            Optiarc  DVD RW AD-7561S  AH03 PQ: 0 ANSI: 5
[    1.663068] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.663072] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.663262] sr 3:0:0:0: Attached scsi CD-ROM sr0
[    1.663355] sr 3:0:0:0: Attached scsi generic sg2 type 5
[    1.689874]  sdb: sdb1 sdb2
[    1.690208] sd 1:0:0:0: [sdb] Attached SCSI disk
[    1.692222] Freeing unused kernel memory: 920k freed
[    1.692729] Write protecting the kernel read-only data: 12288k
[    1.699383] Freeing unused kernel memory: 1608k freed
[    1.705353] Freeing unused kernel memory: 1196k freed
[    1.739740] udevd[100]: starting version 175
[    1.804131] usb 3-1: new low-speed USB device number 2 using ohci_hcd
[    1.845986] wmi: Mapper loaded
[    1.881068] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[    1.887840] acpi device:04: registered as cooling_device2
[    1.887968] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:02/LNXVIDEO:00/input/input4
[    1.888118] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[    1.890455] sdhci: Secure Digital Host Controller Interface driver
[    1.890459] sdhci: Copyright(c) Pierre Ossman
[    1.890856] sdhci-pci 0000:08:00.0: SDHCI controller found [197b:2382] (rev 0)
[    1.890880] sdhci-pci 0000:08:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.890935] sdhci-pci 0000:08:00.0: setting latency timer to 64
[    1.890955] mmc0: no vmmc regulator found
[    1.891001] Registered led device: mmc0::
[    1.895380] mmc0: SDHCI controller on PCI [0000:08:00.0] using ADMA
[    1.895412] sdhci-pci 0000:08:00.2: SDHCI controller found [197b:2381] (rev 0)
[    1.895434] sdhci-pci 0000:08:00.2: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.895447] sdhci-pci 0000:08:00.2: Refusing to bind to secondary interface.
[    1.895471] sdhci-pci 0000:08:00.2: PCI INT A disabled
[    1.906577] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.906609] r8169 0000:0a:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.906684] r8169 0000:0a:00.0: setting latency timer to 64
[    1.906742] r8169 0000:0a:00.0: irq 44 for MSI/MSI-X
[    1.907274] r8169 0000:0a:00.0: eth0: RTL8102e at 0xffffc90002788000, 00:23:5a:1e:d9:bb, XID 04a00000 IRQ 44
[    1.928328] scsi6 : pata_atiixp
[    1.932603] scsi7 : pata_atiixp
[    1.933332] ata7: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x8000 irq 14
[    1.933336] ata8: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x8008 irq 15
[    2.096406] input: Kensington Kensington USB Wheel Mouse as /devices/pci0000:00/0000:00:12.0/usb3/3-1/3-1:1.0/input/input5
[    2.096575] generic-usb 0003:047D:1032.0001: input,hidraw0: USB HID v1.10 Mouse [Kensington Kensington USB Wheel Mouse] on usb-0000:00:12.0-1/input0
[    2.096600] usbcore: registered new interface driver usbhid
[    2.096602] usbhid: USB HID core driver
[    2.244063] usb 4-2: new low-speed USB device number 2 using ohci_hcd
[    2.418478] input: Generic USB K/B as /devices/pci0000:00/0000:00:12.1/usb4/4-2/4-2:1.0/input/input6
[    2.418602] generic-usb 0003:13BA:0017.0002: input,hidraw1: USB HID v1.10 Keyboard [Generic USB K/B] on usb-0000:00:12.1-2/input0
[    2.423519] input: Generic USB K/B as /devices/pci0000:00/0000:00:12.1/usb4/4-2/4-2:1.1/input/input7
[    2.423696] generic-usb 0003:13BA:0017.0003: input,hidraw2: USB HID v1.10 Mouse [Generic USB K/B] on usb-0000:00:12.1-2/input1
[    3.151757] vesafb: mode is 1152x864x32, linelength=4608, pages=0
[    3.151763] vesafb: scrolling: redraw
[    3.151767] vesafb: Truecolor: size=0:8:8:8, shift=0:16:8:0
[    3.152850] vesafb: framebuffer at 0xc0000000, mapped to 0xffffc90002800000, using 3904k, total 3904k
[    3.153052] Console: switching to colour frame buffer device 144x54
[    3.153080] fb0: VESA VGA frame buffer device
[    3.456270] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
[    3.456276] EXT4-fs (sda1): write access will be enabled during recovery
[   10.752442] EXT4-fs (sda1): recovery complete
[   10.760806] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[   11.301350] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   11.341362] udevd[415]: starting version 175
[   11.391262] lp: driver loaded but no devices found
[   11.396157] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   11.525193] ene_ir: chip is 0x3926 - kbver = 0x00, rev = 0xc0
[   11.525198] ene_ir: PLL freq = 1406
[   11.525200] ene_ir: KB3926C detected
[   11.525214] ene_ir: Firmware regs: c0 01
[   11.525216] ene_ir: Hardware features:
[   11.525218] ene_ir: * Uses GPIO 40 for IR demodulated input
[   11.533102] hp_accel: hardware type DV7 found
[   11.533805] lis3lv02d: 8 bits sensor found
[   11.557690] IR NEC protocol handler initialized
[   11.570768] IR RC5(x) protocol handler initialized
[   11.581823] IR RC6 protocol handler initialized
[   11.582051] Registered IR keymap rc-rc6-mce
[   11.582162] input: ENE eHome Infrared Remote Receiver as /devices/virtual/rc/rc0/input8
[   11.582277] rc0: ENE eHome Infrared Remote Receiver as /devices/virtual/rc/rc0
[   11.587358] ene_ir: driver has been successfully loaded
[   11.595928] IR JVC protocol handler initialized
[   11.606841] IR Sony protocol handler initialized
[   11.613566] input: MCE IR Keyboard/Mouse (ene_ir) as /devices/virtual/input/input9
[   11.613745] IR MCE Keyboard/mouse protocol handler initialized
[   11.617723] lirc_dev: IR Remote Control driver registered, major 250 
[   11.618062] rc rc0: lirc_dev: driver ir-lirc-codec (ene_ir) registered at minor = 0
[   11.618065] IR LIRC bridge handler initialized
[   11.672656] input: ST LIS3LV02DL Accelerometer as /devices/platform/lis3lv02d/input/input10
[   11.673048] Registered led device: hp::hddprotect
[   11.673132] hp_accel: driver loaded
[   11.713311] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   11.730371] jmb38x_ms 0000:08:00.3: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   11.730383] jmb38x_ms 0000:08:00.3: setting latency timer to 64
[   11.731534] cfg80211: Calling CRDA to update world regulatory domain
[   11.747880] type=1400 audit(1334894503.939:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=628 comm="apparmor_parser"
[   11.748525] type=1400 audit(1334894503.943:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=628 comm="apparmor_parser"
[   11.748856] type=1400 audit(1334894503.943:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=628 comm="apparmor_parser"
[   11.790851] ath9k 0000:09:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   11.790866] ath9k 0000:09:00.0: setting latency timer to 64
[   11.867280] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0xb00, revision 0
[   11.868039] SP5100 TCO timer: SP5100 TCO WatchDog Timer Driver v0.01
[   11.869252] SP5100 TCO timer: mmio address 0xfec000f0 already in use
[   11.921862] EXT4-fs (sdb1): mounted filesystem with ordered data mode. Opts: (null)
[   12.001725] Linux video capture interface: v2.00
[   12.007717] uvcvideo: Found UVC 1.00 device HP Webcam (064e:c107)
[   12.037221] input: HP Webcam as /devices/pci0000:00/0000:00:12.2/usb1/1-6/1-6:1.0/input/input11
[   12.037438] usbcore: registered new interface driver uvcvideo
[   12.037441] USB Video Class driver (1.1.1)
[   12.038431] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   12.038438] Disabling lock debugging due to kernel taint
[   12.263945] ath: EEPROM regdomain: 0x69
[   12.263950] ath: EEPROM indicates we should expect a direct regpair map
[   12.263956] ath: Country alpha2 being used: 00
[   12.263958] ath: Regpair used: 0x69
[   12.276079] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   12.276086] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   12.276088] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   12.276092] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   12.276094] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   12.276097] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   12.276100] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   12.276103] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   12.276106] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   12.276109] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   12.276111] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   12.276114] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   12.276117] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   12.276120] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   12.276122] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   12.276125] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   12.276128] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   12.276131] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   12.276134] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   12.276137] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   12.276139] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   12.276142] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   12.276145] cfg80211: Disabling freq 2467 MHz as custom regd has no rule that fits a 20 MHz wide channel
[   12.276148] cfg80211: Disabling freq 2472 MHz as custom regd has no rule that fits a 20 MHz wide channel
[   12.276150] cfg80211: Disabling freq 2484 MHz as custom regd has no rule that fits a 20 MHz wide channel
[   12.276153] cfg80211: Updating information on frequency 5180 MHz for a 20 MHz width channel with regulatory rule:
[   12.276156] cfg80211: 5140000 KHz - 5360000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
[   12.276159] cfg80211: Updating information on frequency 5200 MHz for a 20 MHz width channel with regulatory rule:
[   12.276162] cfg80211: 5140000 KHz - 5360000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
[   12.276165] cfg80211: Updating information on frequency 5220 MHz for a 20 MHz width channel with regulatory rule:
[   12.276168] cfg80211: 5140000 KHz - 5360000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
[   12.276170] cfg80211: Updating information on frequency 5240 MHz for a 20 MHz width channel with regulatory rule:
[   12.276173] cfg80211: 5140000 KHz - 5360000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
[   12.276176] cfg80211: Updating information on frequency 5260 MHz for a 20 MHz width channel with regulatory rule:
[   12.276179] cfg80211: 5140000 KHz - 5360000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
[   12.276181] cfg80211: Updating information on frequency 5280 MHz for a 20 MHz width channel with regulatory rule:
[   12.276184] cfg80211: 5140000 KHz - 5360000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
[   12.276187] cfg80211: Updating information on frequency 5300 MHz for a 20 MHz width channel with regulatory rule:
[   12.276190] cfg80211: 5140000 KHz - 5360000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
[   12.276192] cfg80211: Updating information on frequency 5320 MHz for a 20 MHz width channel with regulatory rule:
[   12.276195] cfg80211: 5140000 KHz - 5360000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
[   12.276198] cfg80211: Updating information on frequency 5500 MHz for a 20 MHz width channel with regulatory rule:
[   12.276201] cfg80211: 5460000 KHz - 5860000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
[   12.276203] cfg80211: Updating information on frequency 5520 MHz for a 20 MHz width channel with regulatory rule:
[   12.276207] cfg80211: 5460000 KHz - 5860000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
[   12.276209] cfg80211: Updating information on frequency 5540 MHz for a 20 MHz width channel with regulatory rule:
[   12.276212] cfg80211: 5460000 KHz - 5860000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
[   12.276215] cfg80211: Updating information on frequency 5560 MHz for a 20 MHz width channel with regulatory rule:
[   12.276218] cfg80211: 5460000 KHz - 5860000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
[   12.276220] cfg80211: Updating information on frequency 5580 MHz for a 20 MHz width channel with regulatory rule:
[   12.276223] cfg80211: 5460000 KHz - 5860000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
[   12.276226] cfg80211: Updating information on frequency 5600 MHz for a 20 MHz width channel with regulatory rule:
[   12.276229] cfg80211: 5460000 KHz - 5860000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
[   12.276231] cfg80211: Updating information on frequency 5620 MHz for a 20 MHz width channel with regulatory rule:
[   12.276234] cfg80211: 5460000 KHz - 5860000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
[   12.276237] cfg80211: Updating information on frequency 5640 MHz for a 20 MHz width channel with regulatory rule:
[   12.276240] cfg80211: 5460000 KHz - 5860000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
[   12.276242] cfg80211: Updating information on frequency 5660 MHz for a 20 MHz width channel with regulatory rule:
[   12.276245] cfg80211: 5460000 KHz - 5860000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
[   12.276248] cfg80211: Updating information on frequency 5680 MHz for a 20 MHz width channel with regulatory rule:
[   12.276251] cfg80211: 5460000 KHz - 5860000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
[   12.276253] cfg80211: Updating information on frequency 5700 MHz for a 20 MHz width channel with regulatory rule:
[   12.276257] cfg80211: 5460000 KHz - 5860000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
[   12.276259] cfg80211: Updating information on frequency 5745 MHz for a 20 MHz width channel with regulatory rule:
[   12.276262] cfg80211: 5460000 KHz - 5860000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
[   12.276265] cfg80211: Updating information on frequency 5765 MHz for a 20 MHz width channel with regulatory rule:
[   12.276268] cfg80211: 5460000 KHz - 5860000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
[   12.276270] cfg80211: Updating information on frequency 5785 MHz for a 20 MHz width channel with regulatory rule:
[   12.276273] cfg80211: 5460000 KHz - 5860000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
[   12.276276] cfg80211: Updating information on frequency 5805 MHz for a 20 MHz width channel with regulatory rule:
[   12.276279] cfg80211: 5460000 KHz - 5860000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
[   12.276281] cfg80211: Updating information on frequency 5825 MHz for a 20 MHz width channel with regulatory rule:
[   12.276284] cfg80211: 5460000 KHz - 5860000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
[   12.296221] ppdev: user-space parallel port driver
[   12.326073] Bluetooth: Core ver 2.16
[   12.326114] NET: Registered protocol family 31
[   12.326117] Bluetooth: HCI device and connection manager initialized
[   12.326122] Bluetooth: HCI socket layer initialized
[   12.326125] Bluetooth: L2CAP socket layer initialized
[   12.326134] Bluetooth: SCO socket layer initialized
[   12.329614] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   12.329619] Bluetooth: BNEP filters: protocol multicast
[   12.333629] [fglrx] Maximum main memory to use for locked dma buffers: 5524 MBytes.
[   12.333753] [fglrx]   vendor: 1002 device: 9612 count: 1
[   12.334500] [fglrx] ioport: bar 1, base 0x7000, size: 0x100
[   12.334520] pci 0000:01:05.0: power state changed by ACPI to D0
[   12.334524] pci 0000:01:05.0: power state changed by ACPI to D0
[   12.334536] pci 0000:01:05.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   12.334541] pci 0000:01:05.0: setting latency timer to 64
[   12.335201] [fglrx] Kernel PAT support is enabled
[   12.335234] [fglrx] module loaded - fglrx 8.96.4 [Mar 12 2012] with 1 minors
[   12.403278] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[   12.442221] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[   12.456378] Registered led device: ath9k-phy0
[   12.456396] ieee80211 phy0: Atheros AR9280 Rev:2 mem=0xffffc900027a0000, irq=18
[   12.488151] Bluetooth: RFCOMM TTY layer initialized
[   12.488160] Bluetooth: RFCOMM socket layer initialized
[   12.488163] Bluetooth: RFCOMM ver 1.11
[   12.489880] type=1400 audit(1334894504.683:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=811 comm="apparmor_parser"
[   12.492201] type=1400 audit(1334894504.687:6): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=811 comm="apparmor_parser"
[   12.653055] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   12.666583] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   12.694542] r8169 0000:0a:00.0: eth0: link down
[   12.694555] r8169 0000:0a:00.0: eth0: link down
[   12.701646] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   12.711068] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   12.810143] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   12.810154] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   12.823259] init: failsafe main process (860) killed by TERM signal
[   12.938242] snd_hda_intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   12.938335] snd_hda_intel 0000:00:14.2: setting latency timer to 64
[   12.962836] type=1400 audit(1334894505.155:7): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=966 comm="apparmor_parser"
[   12.971911] type=1400 audit(1334894505.163:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=967 comm="apparmor_parser"
[   12.988196] type=1400 audit(1334894505.183:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=967 comm="apparmor_parser"
[   12.988531] type=1400 audit(1334894505.183:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=967 comm="apparmor_parser"
[   13.003341] type=1400 audit(1334894505.195:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=974 comm="apparmor_parser"
[   13.013508] input: HP WMI hotkeys as /devices/virtual/input/input12
[   13.117687] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[   13.117694] cfg80211: World regulatory domain updated:
[   13.117697] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   13.117700] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.117703] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   13.117706] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   13.117709] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.117712] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   13.195235] input: HDA ATI SB Mic as /devices/pci0000:00/0000:00:14.2/sound/card0/input13
[   13.195751] input: HDA ATI SB Front Headphone as /devices/pci0000:00/0000:00:14.2/sound/card0/input14
[   13.199881] snd_hda_intel 0000:01:05.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[   13.199951] snd_hda_intel 0000:01:05.1: setting latency timer to 64
[   13.571103] psmouse serio1: synaptics: Touchpad model: 1, fw: 7.2, id: 0x1a0b1, caps: 0xd04751/0xa00000/0x20000
[   13.688861] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input15
[   13.736340] [fglrx] ATIF platform detected with notification ID: 0x81
[   13.840901] [fglrx] Could not enable MSI; System prevented initialization
[   13.841824] [fglrx] Firegl kernel thread PID: 1319
[   13.842045] [fglrx] Firegl kernel thread PID: 1320
[   13.842260] [fglrx] Firegl kernel thread PID: 1321
[   13.842405] [fglrx] IRQ 18 Enabled
[   14.518887] r8169 0000:0a:00.0: eth0: link up
[   14.520216] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   16.064260] Adding 6024188k swap on /dev/mapper/cryptswap1.  Priority:-1 extents:1 across:6024188k SS
[   16.296344] [fglrx] Gart USWC size:1279 M.
[   16.296350] [fglrx] Gart cacheable size:508 M.
[   16.296355] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
[   16.296358] [fglrx] Reserved FB block: Unshared offset:fbfa000, size:401000 
[   16.296361] [fglrx] Reserved FB block: Unshared offset:fffb000, size:5000 
[   21.208892] wlan0: authenticate with 00:25:9c:18:bd:72 (try 1)
[   21.210858] wlan0: authenticated
[   21.211241] wlan0: associate with 00:25:9c:18:bd:72 (try 1)
[   21.213799] wlan0: RX AssocResp from 00:25:9c:18:bd:72 (capab=0x411 status=0 aid=1)
[   21.213803] wlan0: associated
[   21.216139] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   25.232014] eth0: no IPv6 routers present
[   32.064025] wlan0: no IPv6 routers present
```

---

### Post by for.i.am.root on 2012-04-20
I would just reboot than at the boot menu press "e" and add a pi=off at the end of the kernel line then "b" to boot.

I haven't used this version of Ubuntu so I'm not sure what grub it is using.

Historically it is /boot/grub/menu.lst, however, that would make the change permanent and not a single boot.

Edit: Hey guru's: Is the option to roll our own dsdt back?!?!

Looks like there is a kernel power bug related to:

ACPI _OSC control for PCIe not granted, disabling ASPM
[http://askubuntu.com/questions/65198/do-i-need-to-add-a-boot-parameter-to-work-around-this-kernel-power-bug-on-a-sony](http://askubuntu.com/questions/65198/do-i-need-to-add-a-boot-parameter-to-work-around-this-kernel-power-bug-on-a-sony)

A few issues related to poor performance due to your Intel HD audio and kernel 3.0 that downgrading ALSA fixes.
ACPI _OSC request failed (AE_SUPPORT), returned control mask: 0x0d

This guy reports sluggish performance, especially when browsing.
[http://forums.debian.net/viewtopic.php?f=30&t=76458](http://forums.debian.net/viewtopic.php?f=30&t=76458)

Reverse patching seemed to help this guy.
[http://lists.debian.org/debian-kernel/2011/07/msg00628.html](http://lists.debian.org/debian-kernel/2011/07/msg00628.html)

Another forum (hard to multi-tab on a tablet :-D) reported upgrading to the 3.2 kernel helped him with similar issues.

---

### Post by tobydeemer on 2012-04-20
Well, unfortunately, I tried all three options [acpi=off, noapic, and GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"] to no avail. Still seeing the same level of consumption.

---

### Post by for.i.am.root on 2012-04-20
Does suspend work? How is your audio?

Kind of stumped now. Need to do some more reading. Gotta be up in about 5 and a half hours for work, so I can only give you about another half hour of research or so before I must sleep.

I'll dig around some more and see what else I can figure out. It sounded so much Ike ACPI issues *sigh* reckon I might be getting old.

Forgot to refresh the page so it looked I was the last poster so I edited my above post a few times with notes before I remembered to refresh.

Discreet graphics! fglrx issue anybody?

Kind of hard to read through your entire log. Can you post dmesg | grep fglrx for me? Thanks!

---

### Post by tobydeemer on 2012-04-20
No worries at all. I appreciate the input. I have to be up for work sooner than I care to think about as well. I'll look into the other posts you listed and see what I get. I'll update as soon as I have any further detail. 

Thanks again!

---

### Post by for.i.am.root on 2012-04-20
Confirmed bug relating to the discreet graphics results in sluggish performance and dv7 running extremely hot.

[http://askubuntu.com/questions/68764/hp-pavilion-dv7-graphics-driver](http://askubuntu.com/questions/68764/hp-pavilion-dv7-graphics-driver)
[https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/870560?comments=all](https://bugs.launchpad.net/ubuntu/+source/jockey/+bug/870560?comments=all)

---

### Post by tobydeemer on 2012-04-20
I'm at work now, so I'll dig into the graphics issues when I get home.

For now, here's the dmesg piped to filter for fglrx:

```
[   12.038431] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[   12.333629] [fglrx] Maximum main memory to use for locked dma buffers: 5524 MBytes.
[   12.333753] [fglrx]   vendor: 1002 device: 9612 count: 1
[   12.334500] [fglrx] ioport: bar 1, base 0x7000, size: 0x100
[   12.335201] [fglrx] Kernel PAT support is enabled
[   12.335234] [fglrx] module loaded - fglrx 8.96.4 [Mar 12 2012] with 1 minors
[   13.736340] [fglrx] ATIF platform detected with notification ID: 0x81
[   13.840901] [fglrx] Could not enable MSI; System prevented initialization
[   13.841824] [fglrx] Firegl kernel thread PID: 1319
[   13.842045] [fglrx] Firegl kernel thread PID: 1320
[   13.842260] [fglrx] Firegl kernel thread PID: 1321
[   13.842405] [fglrx] IRQ 18 Enabled
[   16.296344] [fglrx] Gart USWC size:1279 M.
[   16.296350] [fglrx] Gart cacheable size:508 M.
[   16.296355] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
[   16.296358] [fglrx] Reserved FB block: Unshared offset:fbfa000, size:401000 
[   16.296361] [fglrx] Reserved FB block: Unshared offset:fffb000, size:5000 
```

Thanks again.

---

### Post by Mathor on 2012-04-20
> **tobydeemer said:**
> No worries at all. I appreciate the input. I have to be up for work sooner than I care to think about as well. I'll look into the other posts you listed and see what I get. I'll update as soon as I have any further detail. 

Thanks again!

I have the same computer as you and had similar problems, so I got a laptop fan and it has been running very well since. It ran the same on Windows 7 as well as any Gnome3-based desktop environment (because of the 3d acceleration which makes it run a little warmer).

That was some time ago, but I have Precise now and it is exactly what you said: snappy.

---

### Post by georgelappies on 2012-04-20
Are you using the ATI proprietary drivers installed via jockey? If so that is the cause of the problem when laptop starts to go idle.

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/980195](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/980195)

That bug there effects me as well but only if I use the proprietary drivers. If I use the default opensource driver in the kernel all works fine.

---

### Post by dino99 on 2012-04-20
can you confirm that:

- you are running the generic kernel with 6 Gb of ram ? In such case, install the generic-pae kernel instead to fully use your ram. You should run System Monitor to view which processes are heavily crunching, and how much swap is used when you get high cpu.

- if its a dist-upgrade, then clean the room with bleachbit (as root) or make a clean 64 bit install.

---

### Post by for.i.am.root on 2012-04-20
According to dmesg he is running the generic kernel.
He is using fglrx according to dmesg.

Install the open source driver for your discreet graphics. Take Dino's advice and install the generic-pae kernel.

All will be fine.

---

### Post by tobydeemer on 2012-04-20
To answer some of the questions- 
suspend works like a champ. audio also works without issue. 

I did install the ATI driver via Jockey, and after reviewing the earlier links while I was at work today, I am working on removing it now, and will reboot to the open source driver when it's finished. Hopefully we'll see an improvement. I'll let the machine cool off a bit and test again.

It is a clean 64bit installation, using the default 64bit iso. When I run htop, it does show I have 5717mb of ram, and it never showed an swap usage, even when it was runnig terribly. Would installing the pae kernel improve that at all?

Thanks again all. I'll be back shortly.

---

### Post by tobydeemer on 2012-04-20
Well, update is that now Unity won't load at all. I login and I get my wallpaper, which is still right-clickable. The shortcut to open a terminal still works, so I can run graphical programs like firefox, etc. I think I may remove jockey and install the fglrx via synaptic directly, and see how it goes. :-/

---

### Post by Irihapeti on 2012-04-20
Is Xorg the problem, by any chance? Running top in a terminal or checking system monitor would clarify that.

I've had that happen from time to time - lagginess caused by Xorg running with 100% CPU or close to it. There's a bug report at [https://bugs.launchpad.net/ubuntu/+source/thunderbird/+bug/967905](https://bugs.launchpad.net/ubuntu/+source/thunderbird/+bug/967905) OK, it says Thunderbird, but since I submitted that bug, I've found that it happens without Thunderbird running.

Logging out and in again is the short-term fix for me.

The computer isn't a laptop, but I'm not sure how much difference that makes.

---

### Post by dino99 on 2012-04-21
> **tobydeemer said:**
> To answer some of the questions- 

It is a clean 64bit installation, using the default 64bit iso. When I run htop, it does show I have 5717mb of ram, and it never showed an swap usage, even when it was runnig terribly. Would installing the pae kernel improve that at all?

Thanks again all. I'll be back shortly.

NO you dont have installed a 64 bits ubuntu, but a 32 one : look at the log about kernel, it says "generic", meaning 32 bits.
You seems ignore a lot ;)

---

### Post by Synthetic Sam on 2012-04-21
> **dino99 said:**
> NO you dont have installed a 64 bits ubuntu, but a 32 one : look at the log about kernel, it says "generic", meaning 32 bits.
You seems ignore a lot ;)

Generic does not refer to a 32 bit kernel, but the fact that the kernel has generic application, i.e. it is not tweaked for a specific application such as server usage.  Here is a 64 bit generic kernel for example: [https://launchpad.net/ubuntu/precise/amd64/linux-image-generic/3.2.0.23.25](https://launchpad.net/ubuntu/precise/amd64/linux-image-generic/3.2.0.23.25)

---

### Post by tobydeemer on 2012-04-21
As in my initial post from the "more detailed specs" section:
uname -a >>
3.2.0-23-generic #36-Ubuntu SMP Tue Apr 10 20:39:51 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

I didn't ignore that much.

---

### Post by dino99 on 2012-04-21
> **tobydeemer said:**
> As in my initial post from the "more detailed specs" section:
uname -a >>
3.2.0-23-generic #36-Ubuntu SMP Tue Apr 10 20:39:51 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

I didn't ignore that much.

really looks like a 64 kernel installed on an initial 32 system. Better to format it and install a clean one.

---

### Post by tobydeemer on 2012-04-21
There's nothing there that indicates a 32bit system. It's a clean install that's less than two weeks old, installed from the beta2 64bit iso. I've not installed a new kernel, other than what was done via updates. In order to have a 32b system running a 64b kernel, I would have had to use a different iso than what I have, and selectively installed the PAE kernel after the fact. 

As per other user updates in the previously listed bug-report links, I was able to install the fglrx-updates and fglrx-amdcccle-updates packages via apt rather than using Jockey.

I removed Jockey, and using apt was able to remove the fglrx modules cleanly. After this as I noted last night, Unity would not load, either in 2D or 3D. Since I was able to reinstall the fglrx modules directly from apt, the performance has been marginally better. It still runs hotter than normal and any sort of video (flash, DVD, etc) is still impacted, but it's not *as* extreme as previously.

I don't have onboard and discreet combo as indicated in the one bug report. grep'ing through lspci output shows only the Radeon 3200 VGA controller. The only Intel related hardware that's present is an audio component. All the rest of the chipset and controllers are all AMD.

Due to the nature of the posted bugs related to various ATI / AMD components in this cycle, it's likely I'll just have to live with it util updates and/or upstream release some fixes.

Thanks again to everyone for the input.

---

