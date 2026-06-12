---
title: "Serval boot problems"
date: 2008-06-22
forum: System76 Support
---

### Post by pitseleh on 2008-06-22
I've posted about this problem before, but I thought I'd stop hijacking the other thread and start my own because I'm slightly afraid it goes beyond just wireless boot time problems.

I've got a brand spanking new Serval Performance with a Core 2 Duo T8300 2.4 GHz and 4 gigs of ram, running Hardy 64 bit. Unfortunately, my 3 year old Thinkpad (1.4ghz Pentium, 1 gig of ram, Feisty) is totally kicking this guys butt. My Thinkpad takes a couple of minutes to run through the required file system check that shows up every once in a while... my Serval takes 20 minutes. My Serval can take anywhere from a minute to 5 minutes to get to the Ubuntu login screen. The boots are always really random... sometimes it goes through a list of things it OKs (and hangs a bit), sometimes it hangs at the load bar for a minute or so, and this last time around it got stuck at a blank screen with both the blue LED lock icons blinking (above the delete key). It is driving me insane...

Here is an output from a hang up a while back:
> Jun 8 12:35:46 Stavros syslogd 1.5.0#1ubuntu1: restart.
Jun 8 12:35:46 Stavros kernel: Inspecting /boot/System.map-2.6.24-18-generic
Jun 8 12:35:46 Stavros kernel: Loaded 28488 symbols from /boot/System.map-2.6.24-18-generic.
Jun 8 12:35:46 Stavros kernel: Symbols match kernel version 2.6.24.
Jun 8 12:35:46 Stavros kernel: Loaded 35069 symbols from 94 modules.
Jun 8 12:35:46 Stavros kernel: [ 0.000000] Initializing cgroup subsys cpuset
Jun 8 12:35:46 Stavros kernel: [ 0.000000] Initializing cgroup subsys cpu
Jun 8 12:35:46 Stavros kernel: [ 0.000000] Linux version 2.6.24-18-generic (buildd@king) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed May 28 19:28:38 UTC 2008 (Ubuntu 2.6.24-18.32-generic)
Jun 8 12:35:46 Stavros kernel: [ 0.000000] Command line: root=UUID=6c814527-5db0-4129-b3bc-f41a16213147 ro quiet splash
Jun 8 12:35:46 Stavros kernel: [ 0.000000] BIOS-provided physical RAM map:
Jun 8 12:35:46 Stavros kernel: [ 0.000000] BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
Jun 8 12:35:46 Stavros kernel: [ 0.000000] BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
Jun 8 12:35:46 Stavros kernel: [ 0.000000] BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
Jun 8 12:35:46 Stavros kernel: [ 0.000000] BIOS-e820: 0000000000100000 - 00000000bfed0000 (usable)
Jun 8 12:35:46 Stavros kernel: [ 0.000000] BIOS-e820: 00000000bfed0000 - 00000000bfee3000 (ACPI NVS)
Jun 8 12:35:46 Stavros kernel: [ 0.000000] BIOS-e820: 00000000bfee3000 - 00000000c0000000 (reserved)
Jun 8 12:35:46 Stavros kernel: [ 0.000000] BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
Jun 8 12:35:46 Stavros kernel: [ 0.000000] BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
Jun 8 12:35:46 Stavros kernel: [ 0.000000] BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
Jun 8 12:35:46 Stavros kernel: [ 0.000000] BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
Jun 8 12:35:46 Stavros kernel: [ 0.000000] BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Jun 8 12:35:46 Stavros kernel: [ 0.000000] BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
Jun 8 12:35:46 Stavros kernel: [ 0.000000] BIOS-e820: 0000000100000000 - 0000000140000000 (usable)
Jun 8 12:35:46 Stavros kernel: [ 0.000000] end_pfn_map = 1310720
Jun 8 12:35:46 Stavros kernel: [ 0.000000] DMI present.
Jun 8 12:35:46 Stavros kernel: [ 0.000000] ACPI: RSDP signature @ 0xFFFF8100000F7B40 checksum 0
Jun 8 12:35:46 Stavros kernel: [ 0.000000] ACPI: RSDP 000F7B40, 0024 (r2 Compal)
Jun 8 12:35:46 Stavros kernel: [ 0.000000] ACPI: XSDT BFED8622, 008C (r1 Compal CRESTLNE 6040000 LTP 0)
Jun 8 12:35:46 Stavros kernel: [ 0.000000] ACPI: FACP BFEDFBD2, 00F4 (r3 INTEL CRESTLNE 6040000 ALAN 1)
Jun 8 12:35:46 Stavros kernel: [ 0.000000] ACPI: DSDT BFED9B51, 600D (r2 Compal CRESTLNE 6040000 INTL 20061109)
Jun 8 12:35:46 Stavros kernel: [ 0.000000] ACPI: FACS BFEE2FC0, 0040
Jun 8 12:35:46 Stavros kernel: [ 0.000000] ACPI: APIC BFEDFCC6, 0068 (r1 INTEL CRESTLNE 6040000 LOHR 5A)
Jun 8 12:35:46 Stavros kernel: [ 0.000000] ACPI: HPET BFEDFD2E, 0038 (r1 Compal CRESTLNE 6040000 LOHR 5A)
Jun 8 12:35:46 Stavros kernel: [ 0.000000] ACPI: MCFG BFEDFD66, 003C (r1 INTEL CRESTLNE 6040000 LOHR 5A)
Jun 8 12:35:46 Stavros kernel: [ 0.000000] ACPI: TCPA BFEDFDA2, 0032 (r1 Intel CRESTLNE 6040000 LOHR 5A)
Jun 8 12:35:46 Stavros kernel: [ 0.000000] ACPI: TMOR BFEDFDD4, 0026 (r1 PTLTD 6040000 PTL 3)
Jun 8 12:35:46 Stavros kernel: [ 0.000000] ACPI: SLIC BFEDFDFA, 0176 (r1 Compal CRESTLNE 6040000 TBD 1)
Jun 8 12:35:46 Stavros kernel: [ 0.000000] ACPI: APIC BFEDFF70, 0068 (r1 PTLTD ^I APIC 6040000 LTP 0)
Jun 8 12:35:46 Stavros kernel: [ 0.000000] ACPI: BOOT BFEDFFD8, 0028 (r1 PTLTD $SBFTBL$ 6040000 LTP 1)
Jun 8 12:35:46 Stavros kernel: [ 0.000000] ACPI: SSDT BFED988C, 02C5 (r1 SataRe SataAhci 1000 INTL 20050624)
Jun 8 12:35:46 Stavros kernel: [ 0.000000] ACPI: SSDT BFED8C3A, 025F (r1 PmRef Cpu0Tst 3000 INTL 20050624)
Jun 8 12:35:46 Stavros kernel: [ 0.000000] ACPI: SSDT BFED8B94, 00A6 (r1 PmRef Cpu1Tst 3000 INTL 20050624)
Jun 8 12:35:46 Stavros kernel: [ 0.000000] ACPI: SSDT BFED86AE, 04E6 (r1 PmRef CpuPm 3000 INTL 20050624)
Jun 8 12:35:46 Stavros kernel: [ 0.000000] ACPI: BIOS bug: multiple APIC/MADT found, using 0
Jun 8 12:35:46 Stavros kernel: [ 0.000000] ACPI: If "acpi_apic_instance=2" works better, notify [email]linux-acpi@vger.kernel.org[/email]
Jun 8 12:35:46 Stavros kernel: [ 0.000000] ACPI: DMI detected: Compal
Jun 8 12:35:46 Stavros kernel: [ 0.000000] No NUMA configuration found
Jun 8 12:35:46 Stavros kernel: [ 0.000000] Faking a node at 0000000000000000-0000000140000000
Jun 8 12:35:46 Stavros kernel: [ 0.000000] Bootmem setup node 0 0000000000000000-0000000140000000
Jun 8 12:35:46 Stavros kernel: [ 0.000000] Zone PFN ranges:
Jun 8 12:35:46 Stavros kernel: [ 0.000000] DMA 0 -> 4096
Jun 8 12:35:46 Stavros kernel: [ 0.000000] DMA32 4096 -> 1048576
Jun 8 12:35:46 Stavros kernel: [ 0.000000] Normal 1048576 -> 1310720
Jun 8 12:35:46 Stavros kernel: [ 0.000000] Movable zone start PFN for each node
Jun 8 12:35:46 Stavros kernel: [ 0.000000] early_node_map[3] active PFN ranges
Jun 8 12:35:46 Stavros kernel: [ 0.000000] 0: 0 -> 159
Jun 8 12:35:46 Stavros kernel: [ 0.000000] 0: 256 -> 786128
Jun 8 12:35:46 Stavros kernel: [ 0.000000] 0: 1048576 -> 1310720
Jun 8 12:35:46 Stavros kernel: [ 0.000000] ACPI: PM-Timer IO Port: 0x1008
Jun 8 12:35:46 Stavros kernel: [ 0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Jun 8 12:35:46 Stavros kernel: [ 0.000000] Processor #0 (Bootup-CPU)
Jun 8 12:35:46 Stavros kernel: [ 0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Jun 8 12:35:46 Stavros kernel: [ 0.000000] Processor #1
Jun 8 12:35:46 Stavros kernel: [ 0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Jun 8 12:35:46 Stavros kernel: [ 0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Jun 8 12:35:46 Stavros kernel: [ 0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
Jun 8 12:35:46 Stavros kernel: [ 0.000000] IOAPIC[0]: apic_id 1, address 0xfec00000, GSI 0-23
Jun 8 12:35:46 Stavros kernel: [ 0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Jun 8 12:35:46 Stavros kernel: [ 0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Jun 8 12:35:46 Stavros kernel: [ 0.000000] Setting APIC routing to flat
Jun 8 12:35:46 Stavros kernel: [ 0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
Jun 8 12:35:46 Stavros kernel: [ 0.000000] Using ACPI (MADT) for SMP configuration information
Jun 8 12:35:46 Stavros kernel: [ 0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
Jun 8 12:35:46 Stavros kernel: [ 0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000dc000
Jun 8 12:35:46 Stavros kernel: [ 0.000000] swsusp: Registered nosave memory region: 00000000000dc000 - 0000000000100000
Jun 8 12:35:46 Stavros kernel: [ 0.000000] swsusp: Registered nosave memory region: 00000000bfed0000 - 00000000bfee3000
Jun 8 12:35:46 Stavros kernel: [ 0.000000] swsusp: Registered nosave memory region: 00000000bfee3000 - 00000000c0000000
Jun 8 12:35:46 Stavros kernel: [ 0.000000] swsusp: Registered nosave memory region: 00000000c0000000 - 00000000fec00000
Jun 8 12:35:46 Stavros kernel: [ 0.000000] swsusp: Registered nosave memory region: 00000000fec00000 - 00000000fec10000
Jun 8 12:35:46 Stavros kernel: [ 0.000000] swsusp: Registered nosave memory region: 00000000fec10000 - 00000000fed00000
Jun 8 12:35:46 Stavros kernel: [ 0.000000] swsusp: Registered nosave memory region: 00000000fed00000 - 00000000fed14000
Jun 8 12:35:46 Stavros kernel: [ 0.000000] swsusp: Registered nosave memory region: 00000000fed14000 - 00000000fed1a000
Jun 8 12:35:46 Stavros kernel: [ 0.000000] swsusp: Registered nosave memory region: 00000000fed1a000 - 00000000fed1c000
Jun 8 12:35:46 Stavros kernel: [ 0.000000] swsusp: Registered nosave memory region: 00000000fed1c000 - 00000000fed90000
Jun 8 12:35:46 Stavros kernel: [ 0.000000] swsusp: Registered nosave memory region: 00000000fed90000 - 00000000fee00000
Jun 8 12:35:46 Stavros kernel: [ 0.000000] swsusp: Registered nosave memory region: 00000000fee00000 - 00000000fee01000
Jun 8 12:35:46 Stavros kernel: [ 0.000000] swsusp: Registered nosave memory region: 00000000fee01000 - 00000000ff000000
Jun 8 12:35:46 Stavros kernel: [ 0.000000] swsusp: Registered nosave memory region: 00000000ff000000 - 0000000100000000
Jun 8 12:35:46 Stavros kernel: [ 0.000000] Allocating PCI resources starting at c4000000 (gap: c0000000:3ec00000)
Jun 8 12:35:46 Stavros kernel: [ 0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
Jun 8 12:35:46 Stavros kernel: [ 0.000000] PERCPU: Allocating 34656 bytes of per cpu data
Jun 8 12:35:46 Stavros kernel: [ 0.000000] Built 1 zonelists in Node order, mobility grouping on. Total pages: 1029033
Jun 8 12:35:46 Stavros kernel: [ 0.000000] Policy zone: Normal
Jun 8 12:35:46 Stavros kernel: [ 0.000000] Kernel command line: root=UUID=6c814527-5db0-4129-b3bc-f41a16213147 ro quiet splash
Jun 8 12:35:46 Stavros kernel: [ 0.000000] Initializing CPU#0
Jun 8 12:35:46 Stavros kernel: [ 0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
Jun 8 12:35:46 Stavros kernel: [ 0.000000] Extended CMOS year: 2000
Jun 8 12:35:46 Stavros kernel: [ 0.000000] TSC calibrated against HPET
Jun 8 12:35:46 Stavros kernel: [ 16.684936] Marking TSC unstable due to TSCs unsynchronized
Jun 8 12:35:46 Stavros kernel: [ 16.684937] time.c: Detected 2394.002 MHz processor.
Jun 8 12:35:46 Stavros kernel: [ 16.688865] Console: colour VGA+ 80x25
Jun 8 12:35:46 Stavros kernel: [ 16.688868] console [tty0] enabled
Jun 8 12:35:46 Stavros kernel: [ 16.688886] Checking aperture...
Jun 8 12:35:46 Stavros kernel: [ 16.688899] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
Jun 8 12:35:46 Stavros kernel: [ 16.723604] Placing software IO TLB between 0x103b000 - 0x503b000
Jun 8 12:35:46 Stavros kernel: [ 16.759780] Memory: 4042428k/5242880k available (2488k kernel code, 150272k reserved, 1319k data, 320k init)
Jun 8 12:35:46 Stavros kernel: [ 16.759814] SLUB: Genslabs=12, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
Jun 8 12:35:46 Stavros kernel: [ 16.838658] Calibrating delay using timer specific routine.. 4792.42 BogoMIPS (lpj=958484
Jun 8 12:35:46 Stavros kernel: [ 16.838687] Security Framework initialized
Jun 8 12:35:46 Stavros kernel: [ 16.838693] SELinux: Disabled at boot.
Jun 8 12:35:46 Stavros kernel: [ 16.838703] AppArmor: AppArmor initialized
Jun 8 12:35:46 Stavros kernel: [ 16.838706] Failure registering capabilities with primary security module.
Jun 8 12:35:46 Stavros kernel: [ 16.838978] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
Jun 8 12:35:46 Stavros kernel: [ 16.841352] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
Jun 8 12:35:46 Stavros kernel: [ 16.842480] Mount-cache hash table entries: 256
Jun 8 12:35:46 Stavros kernel: [ 16.842601] Initializing cgroup subsys ns
Jun 8 12:35:46 Stavros kernel: [ 16.842607] Initializing cgroup subsys cpuacct
Jun 8 12:35:46 Stavros kernel: [ 16.842620] CPU: L1 I cache: 32K, L1 D cache: 32K
Jun 8 12:35:46 Stavros kernel: [ 16.842622] CPU: L2 cache: 3072K
Jun 8 12:35:46 Stavros kernel: [ 16.842623] CPU 0/0 -> Node 0
Jun 8 12:35:46 Stavros kernel: [ 16.842624] using mwait in idle threads.
Jun 8 12:35:46 Stavros kernel: [ 16.842626] CPU: Physical Processor ID: 0
Jun 8 12:35:46 Stavros kernel: [ 16.842627] CPU: Processor Core ID: 0
Jun 8 12:35:46 Stavros kernel: [ 16.842643] SMP alternatives: switching to UP code
Jun 8 12:35:46 Stavros kernel: [ 16.843367] Early unpacking initramfs... done
Jun 8 12:35:46 Stavros kernel: [ 17.108929] ACPI: Core revision 20070126
Jun 8 12:35:46 Stavros kernel: [ 17.108964] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Jun 8 12:35:46 Stavros kernel: [ 17.155258] Using local APIC timer interrupts.
Jun 8 12:35:46 Stavros kernel: [ 17.196961] Detected 12.468 MHz APIC timer.
Jun 8 12:35:46 Stavros kernel: [ 17.197024] SMP alternatives: switching to SMP code
Jun 8 12:35:46 Stavros kernel: [ 17.197635] Booting processor 1/2 APIC 0x1
Jun 8 12:35:46 Stavros kernel: [ 17.208005] Initializing CPU#1
Jun 8 12:35:46 Stavros kernel: [ 17.284815] Calibrating delay using timer specific routine.. 4788.03 BogoMIPS (lpj=9576075)
Jun 8 12:35:46 Stavros kernel: [ 17.284820] CPU: L1 I cache: 32K, L1 D cache: 32K
Jun 8 12:35:46 Stavros kernel: [ 17.284821] CPU: L2 cache: 3072K
Jun 8 12:35:46 Stavros kernel: [ 17.284823] CPU 1/1 -> Node 0
Jun 8 12:35:46 Stavros kernel: [ 17.284824] CPU: Physical Processor ID: 0
Jun 8 12:35:46 Stavros kernel: [ 17.284825] CPU: Processor Core ID: 1
Jun 8 12:35:46 Stavros kernel: [ 17.284830] CPU1: Thermal monitoring enabled (TM2)
Jun 8 12:35:46 Stavros kernel: [ 17.285258] Intel(R) Core(TM)2 Duo CPU T8300 @ 2.40GHz stepping 06
Jun 8 12:35:46 Stavros kernel: [ 17.285327] Brought up 2 CPUs
Jun 8 12:35:46 Stavros kernel: [ 17.285597] net_namespace: 120 bytes
Jun 8 12:35:46 Stavros kernel: [ 17.285895] Time: 17:35:04 Date: 06/08/08
Jun 8 12:35:46 Stavros kernel: [ 17.285916] NET: Registered protocol family 16
Jun 8 12:35:46 Stavros kernel: [ 17.286069] ACPI: bus type pci registered
Jun 8 12:35:46 Stavros kernel: [ 17.286126] PCI: Using configuration type 1
Jun 8 12:35:46 Stavros kernel: [ 17.288574] ACPI: BIOS _OSI(Linux) query ignored via DMI
Jun 8 12:35:46 Stavros kernel: [ 17.288576] ACPI: If "acpi_osi=Linux" works better, please notify [email]linux-acpi@vger.kernel.org[/email]
Jun 8 12:35:46 Stavros kernel: [ 17.288987] ACPI: Interpreter enabled
Jun 8 12:35:46 Stavros kernel: [ 17.288990] ACPI: (supports S0 S3 S4 S5)
Jun 8 12:35:46 Stavros kernel: [ 17.289002] ACPI: Using IOAPIC for interrupt routing
Jun 8 12:35:46 Stavros kernel: [ 17.329161] ACPI: EC: GPE = 0x1c, I/O: command/status = 0x66, data = 0x62
Jun 8 12:35:46 Stavros kernel: [ 17.329163] ACPI: EC: driver started in poll mode
Jun 8 12:35:46 Stavros kernel: [ 17.329191] ACPI: PCI Root Bridge [PCI0] (0000:00)
Jun 8 12:35:46 Stavros kernel: [ 17.330141] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
Jun 8 12:35:46 Stavros kernel: [ 17.330144] PCI quirk: region 1180-11bf claimed by ICH6 GPIO
Jun 8 12:35:46 Stavros kernel: [ 17.331852] PCI: Transparent bridge - 0000:00:1e.0
Jun 8 12:35:46 Stavros kernel: [ 17.336426] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 *5 6 7 10 12 14 15)
Jun 8 12:35:46 Stavros kernel: [ 17.336501] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
Jun 8 12:35:46 Stavros kernel: [ 17.336576] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 *7 10 12 14 15)
Jun 8 12:35:46 Stavros kernel: [ 17.336650] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
Jun 8 12:35:46 Stavros kernel: [ 17.336731] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
Jun 8 12:35:46 Stavros kernel: [ 17.336806] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 *11 12 14 15)
Jun 8 12:35:46 Stavros kernel: [ 17.336879] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
Jun 8 12:35:46 Stavros kernel: [ 17.336952] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
Jun 8 12:35:46 Stavros kernel: [ 17.337056] Linux Plug and Play Support v0.97 (c) Adam Belay
Jun 8 12:35:46 Stavros kernel: [ 17.337081] pnp: PnP ACPI init
Jun 8 12:35:46 Stavros kernel: [ 17.337086] ACPI: bus type pnp registered
Jun 8 12:35:46 Stavros kernel: [ 17.356839] pnp: PnP ACPI: found 11 devices
Jun 8 12:35:46 Stavros kernel: [ 17.356840] ACPI: ACPI bus type pnp unregistered
Jun 8 12:35:46 Stavros kernel: [ 17.357010] PCI: Using ACPI for IRQ routing
Jun 8 12:35:46 Stavros kernel: [ 17.357012] PCI: If a device doesn't work, try "pci=routeirq". If it helps, post a report
Jun 8 12:35:46 Stavros kernel: [ 17.357015] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.0
Jun 8 12:35:46 Stavros kernel: [ 17.357017] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.3
Jun 8 12:35:46 Stavros kernel: [ 17.368685] NET: Registered protocol family 8
Jun 8 12:35:46 Stavros kernel: [ 17.368686] NET: Registered protocol family 20
Jun 8 12:35:46 Stavros kernel: [ 17.368711] PCI-GART: No AMD northbridge found.
Jun 8 12:35:46 Stavros kernel: [ 17.368716] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
Jun 8 12:35:46 Stavros kernel: [ 17.368718] hpet0: 3 64-bit timers, 14318180 Hz
Jun 8 12:35:46 Stavros kernel: [ 17.369744] AppArmor: AppArmor Filesystem Enabled
Jun 8 12:35:46 Stavros kernel: [ 17.372665] Time: hpet clocksource has been installed.
Jun 8 12:35:46 Stavros kernel: [ 17.380644] system 00:01: iomem range 0xfed1c000-0xfed1ffff could not be reserved
Jun 8 12:35:46 Stavros kernel: [ 17.380647] system 00:01: iomem range 0xfed14000-0xfed17fff could not be reserved
Jun 8 12:35:46 Stavros kernel: [ 17.380649] system 00:01: iomem range 0xfed18000-0xfed18fff could not be reserved
Jun 8 12:35:46 Stavros kernel: [ 17.380652] system 00:01: iomem range 0xfed19000-0xfed19fff could not be reserved
Jun 8 12:35:46 Stavros kernel: [ 17.380654] system 00:01: iomem range 0xe0000000-0xefffffff has been reserved
Jun 8 12:35:46 Stavros kernel: [ 17.380656] system 00:01: iomem range 0xfed20000-0xfed3ffff could not be reserved
Jun 8 12:35:46 Stavros kernel: [ 17.380658] system 00:01: iomem range 0xfed40000-0xfed44fff could not be reserved
Jun 8 12:35:46 Stavros kernel: [ 17.380660] system 00:01: iomem range 0xfed45000-0xfed8ffff could not be reserved
Jun 8 12:35:46 Stavros kernel: [ 17.380666] system 00:05: iomem range 0xfed00000-0xfed003ff could not be reserved
Jun 8 12:35:46 Stavros kernel: [ 17.380670] system 00:07: ioport range 0x680-0x69f has been reserved
Jun 8 12:35:46 Stavros kernel: [ 17.380672] system 00:07: ioport range 0x800-0x80f has been reserved
Jun 8 12:35:46 Stavros kernel: [ 17.380674] system 00:07: ioport range 0x1000-0x107f has been reserved
Jun 8 12:35:46 Stavros kernel: [ 17.380676] system 00:07: ioport range 0x1180-0x11bf has been reserved
Jun 8 12:35:46 Stavros kernel: [ 17.380679] system 00:07: ioport range 0x1640-0x164f has been reserved
Jun 8 12:35:46 Stavros kernel: [ 17.380681] system 00:07: ioport range 0xfe00-0xfe00 has been reserved
Jun 8 12:35:46 Stavros kernel: [ 17.380683] system 00:07: ioport range 0xff00-0xff7f has been reserved
Jun 8 12:35:46 Stavros kernel: [ 17.381000] PCI: Failed to allocate mem resource #6:20000@e0000000 for 0000:01:00.0
Jun 8 12:35:46 Stavros kernel: [ 17.381002] PCI: Bridge: 0000:00:01.0
Jun 8 12:35:46 Stavros kernel: [ 17.381003] IO window: 2000-2fff
Jun 8 12:35:46 Stavros kernel: [ 17.381006] MEM window: c4000000-c6ffffff
Jun 8 12:35:46 Stavros kernel: [ 17.381008] PREFETCH window: d0000000-dfffffff
Jun 8 12:35:46 Stavros kernel: [ 17.381010] PCI: Bridge: 0000:00:1c.0
Jun 8 12:35:46 Stavros kernel: [ 17.381012] IO window: 3000-3fff
Jun 8 12:35:46 Stavros kernel: [ 17.381017] MEM window: disabled.
Jun 8 12:35:46 Stavros kernel: [ 17.381021] PREFETCH window: cc000000-cdffffff
Jun 8 12:35:46 Stavros kernel: [ 17.381026] PCI: Bridge: 0000:00:1c.1
Jun 8 12:35:46 Stavros kernel: [ 17.381028] IO window: 4000-4fff
Jun 8 12:35:46 Stavros kernel: [ 17.381033] MEM window: f0000000-f3ffffff
Jun 8 12:35:46 Stavros kernel: [ 17.381037] PREFETCH window: fa000000-fbffffff
Jun 8 12:35:46 Stavros kernel: [ 17.381042] PCI: Bridge: 0000:00:1c.2
Jun 8 12:35:46 Stavros kernel: [ 17.381044] IO window: 5000-5fff
Jun 8 12:35:46 Stavros kernel: [ 17.381049] MEM window: f4000000-f7ffffff
Jun 8 12:35:46 Stavros kernel: [ 17.381053] PREFETCH window: fc000000-fdffffff
Jun 8 12:35:46 Stavros kernel: [ 17.381058] PCI: Bridge: 0000:00:1c.3
Jun 8 12:35:46 Stavros kernel: [ 17.381060] IO window: 6000-6fff
Jun 8 12:35:46 Stavros kernel: [ 17.381065] MEM window: disabled.
Jun 8 12:35:46 Stavros kernel: [ 17.381069] PREFETCH window: c8000000-c9ffffff
Jun 8 12:35:46 Stavros kernel: [ 17.381074] PCI: Bridge: 0000:00:1c.4
Jun 8 12:35:46 Stavros kernel: [ 17.381074] IO window: disabled.
Jun 8 12:35:46 Stavros kernel: [ 17.381079] MEM window: disabled.
Jun 8 12:35:46 Stavros kernel: [ 17.381082] PREFETCH window: disabled.
Jun 8 12:35:46 Stavros kernel: [ 17.381087] PCI: Bridge: 0000:00:1c.5
Jun 8 12:35:46 Stavros kernel: [ 17.381088] IO window: disabled.
Jun 8 12:35:46 Stavros kernel: [ 17.381093] MEM window: f8000000-f80fffff
Jun 8 12:35:46 Stavros kernel: [ 17.381096] PREFETCH window: disabled.
Jun 8 12:35:46 Stavros kernel: [ 17.381101] PCI: Bridge: 0000:00:1e.0
Jun 8 12:35:46 Stavros kernel: [ 17.381102] IO window: disabled.
Jun 8 12:35:46 Stavros kernel: [ 17.381107] MEM window: f8100000-f81fffff
Jun 8 12:35:46 Stavros kernel: [ 17.381111] PREFETCH window: disabled.
Jun 8 12:35:46 Stavros kernel: [ 17.381124] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
Jun 8 12:35:46 Stavros kernel: [ 17.381148] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 17
Jun 8 12:35:46 Stavros kernel: [ 17.381173] ACPI: PCI Interrupt 0000:00:1c.1[b] -> GSI 16 (level, low) -> IRQ 16
Jun 8 12:35:46 Stavros kernel: [ 17.381199] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 18
Jun 8 12:35:46 Stavros kernel: [ 17.381225] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 19
Jun 8 12:35:46 Stavros kernel: [ 17.381251] ACPI: PCI Interrupt 0000:00:1c.4[A] -> GSI 17 (level, low) -> IRQ 17
Jun 8 12:35:46 Stavros kernel: [ 17.381276] ACPI: PCI Interrupt 0000:00:1c.5[b] -> GSI 16 (level, low) -> IRQ 16
Jun 8 12:35:46 Stavros kernel: [ 17.381300] NET: Registered protocol family 2
Jun 8 12:35:46 Stavros kernel: [ 17.416661] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
Jun 8 12:35:46 Stavros kernel: [ 17.417556] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
Jun 8 12:35:46 Stavros kernel: [ 17.421642] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
Jun 8 12:35:46 Stavros kernel: [ 17.422190] TCP: Hash tables configured (established 524288 bind 65536)
Jun 8 12:35:46 Stavros kernel: [ 17.422192] TCP reno registered
Jun 8 12:35:46 Stavros kernel: [ 17.432667] checking if image is initramfs... it is
Jun 8 12:35:46 Stavros kernel: [ 17.995959] Freeing initrd memory: 7477k freed
Jun 8 12:35:46 Stavros kernel: [ 17.999369] Simple Boot Flag at 0x38 set to 0x80
Jun 8 12:35:46 Stavros kernel: [ 18.000058] audit: initializing netlink socket (disabled)
Jun 8 12:35:46 Stavros kernel: [ 18.000075] audit(1212946504.284:1): initialized
Jun 8 12:35:46 Stavros kernel: [ 18.001784] VFS: Disk quotas dquot_6.5.1
Jun 8 12:35:46 Stavros kernel: [ 18.001832] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
Jun 8 12:35:46 Stavros kernel: [ 18.001922] io scheduler noop registered
Jun 8 12:35:46 Stavros kernel: [ 18.001924] io scheduler anticipatory registered
Jun 8 12:35:46 Stavros kernel: [ 18.001925] io scheduler deadline registered
Jun 8 12:35:46 Stavros kernel: [ 18.002007] io scheduler cfq registered (default)
Jun 8 12:35:46 Stavros kernel: [ 18.005313] assign_interrupt_mode Found MSI capability
Jun 8 12:35:46 Stavros kernel: [ 18.005482] assign_interrupt_mode Found MSI capability
Jun 8 12:35:46 Stavros kernel: [ 18.005687] assign_interrupt_mode Found MSI capability
Jun 8 12:35:46 Stavros kernel: [ 18.005892] assign_interrupt_mode Found MSI capability
Jun 8 12:35:46 Stavros kernel: [ 18.006100] assign_interrupt_mode Found MSI capability
Jun 8 12:35:46 Stavros kernel: [ 18.006304] assign_interrupt_mode Found MSI capability
Jun 8 12:35:46 Stavros kernel: [ 18.006509] assign_interrupt_mode Found MSI capability
Jun 8 12:35:46 Stavros kernel: [ 18.025117] Real Time Clock Driver v1.12ac
Jun 8 12:35:46 Stavros kernel: [ 18.025318] Linux agpgart interface v0.102
Jun 8 12:35:46 Stavros kernel: [ 18.025320] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Jun 8 12:35:46 Stavros kernel: [ 18.026144] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Jun 8 12:35:46 Stavros kernel: [ 18.026194] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Jun 8 12:35:46 Stavros kernel: [ 18.026260] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Jun 8 12:35:46 Stavros kernel: [ 18.068737] serio: i8042 KBD port at 0x60,0x64 irq 1
Jun 8 12:35:46 Stavros kernel: [ 18.068741] serio: i8042 AUX port at 0x60,0x64 irq 12
Jun 8 12:35:46 Stavros kernel: [ 18.088435] mice: PS/2 mouse device common for all mice
Jun 8 12:35:46 Stavros kernel: [ 18.088464] cpuidle: using governor ladder
Jun 8 12:35:46 Stavros kernel: [ 18.088465] cpuidle: using governor menu
Jun 8 12:35:46 Stavros kernel: [ 18.088571] NET: Registered protocol family 1
Jun 8 12:35:46 Stavros kernel: [ 18.088650] registered taskstats version 1
Jun 8 12:35:46 Stavros kernel: [ 18.088754] Magic number: 12:432:592
Jun 8 12:35:46 Stavros kernel: [ 18.088835] /build/buildd/linux-2.6.24/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
Jun 8 12:35:46 Stavros kernel: [ 18.088838] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Jun 8 12:35:46 Stavros kernel: [ 18.088839] EDD information not available.
Jun 8 12:35:46 Stavros kernel: [ 18.088845] Freeing unused kernel memory: 320k freed
Jun 8 12:35:46 Stavros kernel: [ 18.121389] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
Jun 8 12:35:46 Stavros kernel: [ 19.234381] fuse init (API version 7.9)
Jun 8 12:35:46 Stavros kernel: [ 19.250241] ACPI: SSDT BFED9508, 02BC (r1 PmRef Cpu0Ist 3000 INTL 20050624)
Jun 8 12:35:46 Stavros kernel: [ 19.250418] ACPI: SSDT BFED8E99, 05EA (r1 PmRef Cpu0Cst 3001 INTL 20050624)
Jun 8 12:35:46 Stavros kernel: [ 19.252064] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
Jun 8 12:35:46 Stavros kernel: [ 19.252068] ACPI: Processor [CPU0] (supports 8 throttling states)
Jun 8 12:35:46 Stavros kernel: [ 19.252241] ACPI: SSDT BFED97C4, 00C8 (r1 PmRef Cpu1Ist 3000 INTL 20050624)
Jun 8 12:35:46 Stavros kernel: [ 19.252388] ACPI: SSDT BFED9483, 0085 (r1 PmRef Cpu1Cst 3000 INTL 20050624)
Jun 8 12:35:46 Stavros kernel: [ 19.253122] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
Jun 8 12:35:46 Stavros kernel: [ 19.253126] ACPI: Processor [CPU1] (supports 8 throttling states)
Jun 8 12:35:46 Stavros kernel: [ 19.384135] usbcore: registered new interface driver usbfs
Jun 8 12:35:46 Stavros kernel: [ 19.384154] usbcore: registered new interface driver hub
Jun 8 12:35:46 Stavros kernel: [ 19.398541] usbcore: registered new device driver usb
Jun 8 12:35:46 Stavros kernel: [ 19.421462] USB Universal Host Controller Interface driver v3.0
Jun 8 12:35:46 Stavros kernel: [ 19.421518] ACPI: PCI Interrupt 0000:00:1a.0[A] -> GSI 16 (level, low) -> IRQ 16
Jun 8 12:35:46 Stavros kernel: [ 19.421533] uhci_hcd 0000:00:1a.0: UHCI Host Controller
Jun 8 12:35:46 Stavros kernel: [ 19.421798] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
Jun 8 12:35:46 Stavros kernel: [ 19.421833] uhci_hcd 0000:00:1a.0: irq 16, io base 0x00001800
Jun 8 12:35:46 Stavros kernel: [ 19.421944] usb usb1: configuration #1 chosen from 1 choice
Jun 8 12:35:46 Stavros kernel: [ 19.421961] hub 1-0:1.0: USB hub found
Jun 8 12:35:46 Stavros kernel: [ 19.421967] hub 1-0:1.0: 2 ports detected
Jun 8 12:35:46 Stavros kernel: [ 19.524947] ACPI: PCI Interrupt 0000:00:1a.1[b] -> GSI 21 (level, low) -> IRQ 21
Jun 8 12:35:46 Stavros kernel: [ 19.524963] uhci_hcd 0000:00:1a.1: UHCI Host Controller
Jun 8 12:35:46 Stavros kernel: [ 19.524982] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
Jun 8 12:35:46 Stavros kernel: [ 19.525016] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00001820
Jun 8 12:35:46 Stavros kernel: [ 19.525103] usb usb2: configuration #1 chosen from 1 choice
Jun 8 12:35:46 Stavros kernel: [ 19.525119] hub 2-0:1.0: USB hub found
Jun 8 12:35:46 Stavros kernel: [ 19.525124] hub 2-0:1.0: 2 ports detected
Jun 8 12:35:46 Stavros kernel: [ 19.538550] SCSI subsystem initialized
Jun 8 12:35:46 Stavros kernel: [ 19.628772] ACPI: PCI Interrupt 0000:00:1a.7[C] -> GSI 18 (level, low) -> IRQ 18
Jun 8 12:35:46 Stavros kernel: [ 19.629539] ehci_hcd 0000:00:1a.7: EHCI Host Controller
Jun 8 12:35:46 Stavros kernel: [ 19.629586] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 3
Jun 8 12:35:46 Stavros kernel: [ 19.633548] ehci_hcd 0000:00:1a.7: debug port 1
Jun 8 12:35:46 Stavros kernel: [ 19.633576] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xf8404800
Jun 8 12:35:46 Stavros kernel: [ 19.649620] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Jun 8 12:35:46 Stavros kernel: [ 19.649696] usb usb3: configuration #1 chosen from 1 choice
Jun 8 12:35:46 Stavros kernel: [ 19.649713] hub 3-0:1.0: USB hub found
Jun 8 12:35:46 Stavros kernel: [ 19.649719] hub 3-0:1.0: 4 ports detected
Jun 8 12:35:46 Stavros kernel: [ 19.754914] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 23
Jun 8 12:35:46 Stavros kernel: [ 19.754929] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Jun 8 12:35:46 Stavros kernel: [ 19.754947] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 4
Jun 8 12:35:46 Stavros kernel: [ 19.754980] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001840
Jun 8 12:35:46 Stavros kernel: [ 19.755064] usb usb4: configuration #1 chosen from 1 choice
Jun 8 12:35:46 Stavros kernel: [ 19.755079] hub 4-0:1.0: USB hub found
Jun 8 12:35:46 Stavros kernel: [ 19.755084] hub 4-0:1.0: 2 ports detected
Jun 8 12:35:46 Stavros kernel: [ 19.856340] ACPI: PCI Interrupt 0000:00:1d.1[b] -> GSI 19 (level, low) -> IRQ 19
Jun 8 12:35:46 Stavros kernel: [ 19.856354] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Jun 8 12:35:46 Stavros kernel: [ 19.856370] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 5
Jun 8 12:35:46 Stavros kernel: [ 19.856399] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001860
Jun 8 12:35:46 Stavros kernel: [ 19.856477] usb usb5: configuration #1 chosen from 1 choice
Jun 8 12:35:46 Stavros kernel: [ 19.856493] hub 5-0:1.0: USB hub found
Jun 8 12:35:46 Stavros kernel: [ 19.856497] hub 5-0:1.0: 2 ports detected
Jun 8 12:35:46 Stavros kernel: [ 19.893252] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
Jun 8 12:35:46 Stavros kernel: [ 19.893269] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Jun 8 12:35:46 Stavros kernel: [ 19.893306] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 6
Jun 8 12:35:46 Stavros kernel: [ 19.893330] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001880
Jun 8 12:35:46 Stavros kernel: [ 19.893401] usb usb6: configuration #1 chosen from 1 choice
Jun 8 12:35:46 Stavros kernel: [ 19.893415] hub 6-0:1.0: USB hub found
Jun 8 12:35:46 Stavros kernel: [ 19.893419] hub 6-0:1.0: 2 ports detected
Jun 8 12:35:46 Stavros kernel: [ 19.946800] usb 3-2: new high speed USB device using ehci_hcd and address 2
Jun 8 12:35:46 Stavros kernel: [ 19.982985] tg3.c:v3.86 (November 9, 2007)
Jun 8 12:35:46 Stavros kernel: [ 19.983064] ACPI: PCI Interrupt 0000:04:00.0[A] -> GSI 17 (level, low) -> IRQ 17
Jun 8 12:35:46 Stavros kernel: [ 20.105181] usb 3-2: configuration #1 chosen from 1 choice
Jun 8 12:35:46 Stavros kernel: [ 20.130501] Clocksource tsc unstable (delta = -81306172 ns)
Jun 8 12:35:46 Stavros kernel: [ 20.362409] usb 2-2: new full speed USB device using uhci_hcd and address 2
Jun 8 12:35:46 Stavros kernel: [ 20.375984] eth0: Tigon3 [partno(none) rev b002 PHY(5787)] (PCI Express) 10/100/1000Base-T Ethernet 00:1b:38:d6:a7:72
Jun 8 12:35:46 Stavros kernel: [ 20.375987] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] WireSpeed[1] TSOcap[1]
Jun 8 12:35:46 Stavros kernel: [ 20.375989] eth0: dma_rwctrl[76180000] dma_mask[64-bit]
Jun 8 12:35:46 Stavros kernel: [ 20.376067] ACPI: PCI Interrupt 0000:00:1f.2[b] -> GSI 19 (level, low) -> IRQ 19
Jun 8 12:35:46 Stavros kernel: [ 20.409423] usb 2-2: configuration #1 chosen from 1 choice
Jun 8 12:35:46 Stavros kernel: [ 20.569906] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 3 Gbps 0x7 impl SATA mode
Jun 8 12:35:46 Stavros kernel: [ 20.569912] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part
Jun 8 12:35:46 Stavros kernel: [ 20.570502] scsi0 : ahci
Jun 8 12:35:46 Stavros kernel: [ 20.570595] scsi1 : ahci
Jun 8 12:35:46 Stavros kernel: [ 20.570676] scsi2 : ahci
Jun 8 12:35:46 Stavros kernel: [ 20.570760] ata1: SATA max UDMA/133 abar m2048@0xf8404000 port 0xf8404100 irq 504
Jun 8 12:35:46 Stavros kernel: [ 20.570763] ata2: SATA max UDMA/133 abar m2048@0xf8404000 port 0xf8404180 irq 504
Jun 8 12:35:46 Stavros kernel: [ 20.570766] ata3: SATA max UDMA/133 abar m2048@0xf8404000 port 0xf8404200 irq 504
Jun 8 12:35:46 Stavros kernel: [ 20.676962] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Jun 8 12:35:46 Stavros kernel: [ 20.678309] ata1.00: ATA-7: ST9160823AS, 3.AAB, max UDMA/133
Jun 8 12:35:46 Stavros kernel: [ 20.678312] ata1.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 31/32)
Jun 8 12:35:46 Stavros kernel: [ 20.679797] ata1.00: configured for UDMA/133
Jun 8 12:35:46 Stavros kernel: [ 20.731744] ata2: SATA link down (SStatus 0 SControl 300)
Jun 8 12:35:46 Stavros kernel: [ 20.787579] ata3: SATA link down (SStatus 0 SControl 300)
Jun 8 12:35:46 Stavros kernel: [ 20.787705] scsi 0:0:0:0: Direct-Access ATA ST9160823AS 3.AA PQ: 0 ANSI: 5
Jun 8 12:35:46 Stavros kernel: [ 20.787984] ACPI: PCI Interrupt 0000:0e:06.0[A] -> GSI 22 (level, low) -> IRQ 22
Jun 8 12:35:46 Stavros kernel: [ 20.841009] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[22] MMIO=[f8100000-f81007ff] Max Packet=[2048] IR/IT contexts=[4/4]
Jun 8 12:35:46 Stavros kernel: [ 20.845325] Driver 'sd' needs updating - please use bus_type methods
Jun 8 12:35:46 Stavros kernel: [ 20.845379] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
Jun 8 12:35:46 Stavros kernel: [ 20.845388] sd 0:0:0:0: [sda] Write Protect is off
Jun 8 12:35:46 Stavros kernel: [ 20.845400] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jun 8 12:35:46 Stavros kernel: [ 20.845436] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
Jun 8 12:35:46 Stavros kernel: [ 20.845442] sd 0:0:0:0: [sda] Write Protect is off
Jun 8 12:35:46 Stavros kernel: [ 20.845454] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jun 8 12:35:46 Stavros kernel: [ 20.845456] sda:<6>ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 19 (level, low) -> IRQ 19
Jun 8 12:35:46 Stavros kernel: [ 20.850372] ACPI: PCI interrupt for device 0000:00:1f.1 disabled
Jun 8 12:35:46 Stavros kernel: [ 20.850430] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 23
Jun 8 12:35:46 Stavros kernel: [ 20.851166] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Jun 8 12:35:46 Stavros kernel: [ 20.851214] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 7
Jun 8 12:35:46 Stavros kernel: [ 20.855115] ehci_hcd 0000:00:1d.7: debug port 1
Jun 8 12:35:46 Stavros kernel: [ 20.855126] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf8404c00
Jun 8 12:35:46 Stavros kernel: [ 20.859016] sda1 sda2 sda3
Jun 8 12:35:46 Stavros kernel: [ 20.859090] sd 0:0:0:0: [sda] Attached SCSI disk
Jun 8 12:35:46 Stavros kernel: [ 20.861581] sd 0:0:0:0: Attached scsi generic sg0 type 0
Jun 8 12:35:46 Stavros kernel: [ 20.868225] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Jun 8 12:35:46 Stavros kernel: [ 20.868308] usb usb7: configuration #1 chosen from 1 choice
Jun 8 12:35:46 Stavros kernel: [ 20.868325] hub 7-0:1.0: USB hub found
Jun 8 12:35:46 Stavros kernel: [ 20.868331] hub 7-0:1.0: 6 ports detected
Jun 8 12:35:46 Stavros kernel: [ 20.950520] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 19 (level, low) -> IRQ 19
Jun 8 12:35:46 Stavros kernel: [ 20.950611] scsi3 : ata_piix
Jun 8 12:35:46 Stavros kernel: [ 20.951108] scsi4 : ata_piix
Jun 8 12:35:46 Stavros kernel: [ 20.951515] ata4: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x18a0 irq 14
Jun 8 12:35:46 Stavros kernel: [ 20.951518] ata5: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x18a8 irq 15
Jun 8 12:35:46 Stavros kernel: [ 21.106099] Attempting manual resume
Jun 8 12:35:46 Stavros kernel: [ 21.130319] kjournald starting. Commit interval 5 seconds
Jun 8 12:35:46 Stavros kernel: [ 21.130341] EXT3-fs: mounted filesystem with ordered data mode.
Jun 8 12:35:46 Stavros kernel: [ 21.206807] ata4.00: ATAPI: MATSHITADVD-RAM UJ-850S, 1.60, max UDMA/33
Jun 8 12:35:46 Stavros kernel: [ 21.286490] ata4.00: configured for UDMA/33
Jun 8 12:35:46 Stavros kernel: [ 21.356647] scsi 3:0:0:0: CD-ROM MATSHITA DVD-RAM UJ-850S 1.60 PQ: 0 ANSI: 5
Jun 8 12:35:46 Stavros kernel: [ 21.356735] scsi 3:0:0:0: Attached scsi generic sg1 type 5
Jun 8 12:35:46 Stavros kernel: [ 29.210607] iTCO_vendor_support: vendor-support=0
Jun 8 12:35:46 Stavros kernel: [ 29.237281] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
Jun 8 12:35:46 Stavros kernel: [ 29.255550] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jun 8 12:35:46 Stavros kernel: [ 29.273575] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Jun 8 12:35:46 Stavros kernel: [ 29.384907] input: Power Button (FF) as /devices/virtual/input/input2
Jun 8 12:35:46 Stavros kernel: [ 29.444703] ACPI: Power Button (FF) [PWRF]
Jun 8 12:35:46 Stavros kernel: [ 29.444754] input: Lid Switch as /devices/virtual/input/input3
Jun 8 12:35:46 Stavros kernel: [ 29.476707] ACPI: Lid Switch [LID0]
Jun 8 12:35:46 Stavros kernel: [ 29.476747] input: Power Button (CM) as /devices/virtual/input/input4
Jun 8 12:35:46 Stavros kernel: [ 29.540543] ACPI: Power Button (CM) [PWRB]
Jun 8 12:35:46 Stavros kernel: [ 29.540605] ACPI: WMI-Acer: Mapper loaded
Jun 8 12:35:46 Stavros kernel: [ 29.573704] ACPI: EC: non-query interrupt received, switching to interrupt mode
Jun 8 12:35:46 Stavros kernel: [ 29.575649] ACPI: AC Adapter [ACAD] (on-line)
Jun 8 12:35:46 Stavros kernel: [ 29.629277] ricoh-mmc: Ricoh MMC Controller disabling driver
Jun 8 12:35:46 Stavros kernel: [ 29.629279] ricoh-mmc: Copyright(c) Philip Langdale
Jun 8 12:35:46 Stavros kernel: [ 29.629314] ricoh-mmc: Ricoh MMC controller found at 0000:0e:06.2 [1180:0843] (rev 12)
Jun 8 12:35:46 Stavros kernel: [ 29.629325] ricoh-mmc: Controller is now disabled.
Jun 8 12:35:46 Stavros kernel: [ 29.652227] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:02/LNXVIDEO:00/input/input5
Jun 8 12:35:46 Stavros kernel: [ 29.709264] ACPI: Video Device [VGA] (multi-head: yes rom: no post: no)
Jun 8 12:35:46 Stavros kernel: [ 29.720677] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:01/input/input6
Jun 8 12:35:46 Stavros kernel: [ 29.721979] sdhci: Secure Digital Host Controller Interface driver
Jun 8 12:35:46 Stavros kernel: [ 29.721981] sdhci: Copyright(c) Pierre Ossman
Jun 8 12:35:46 Stavros kernel: [ 29.722011] sdhci: SDHCI controller found at 0000:0e:06.1 [1180:0822] (rev 22)
Jun 8 12:35:46 Stavros kernel: [ 29.722032] ACPI: PCI Interrupt 0000:0e:06.1[b] -> GSI 23 (level, low) -> IRQ 23
Jun 8 12:35:46 Stavros kernel: [ 29.722763] sdhci:slot0: Will use DMA mode even though HW doesn't fully claim to support it.
Jun 8 12:35:46 Stavros kernel: [ 29.722832] mmc0: SDHCI at 0xf8100800 irq 23 DMA
Jun 8 12:35:46 Stavros kernel: [ 29.773121] ACPI: Video Device [GFX0] (multi-head: yes rom: no post: no)
Jun 8 12:35:46 Stavros kernel: [ 29.793739] ACPI: Battery Slot [BAT1] (battery present)
Jun 8 12:35:46 Stavros kernel: [ 29.851552] nvidia: module license 'NVIDIA' taints kernel.
Jun 8 12:35:46 Stavros kernel: [ 30.193874] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
Jun 8 12:35:46 Stavros kernel: [ 30.193991] NVRM: loading NVIDIA UNIX x86_64 Kernel Module 169.12 Thu Feb 14 17:51:09 PST 2008
Jun 8 12:35:46 Stavros kernel: [ 30.580177] Driver 'sr' needs updating - please use bus_type methods
Jun 8 12:35:46 Stavros kernel: [ 30.586856] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
Jun 8 12:35:46 Stavros kernel: [ 30.586860] Uniform CD-ROM driver Revision: 3.20
Jun 8 12:35:46 Stavros kernel: [ 30.601567] Linux video capture interface: v2.00
Jun 8 12:35:46 Stavros kernel: [ 30.666378] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 20 (level, low) -> IRQ 20
Jun 8 12:35:46 Stavros kernel: [ 30.750480] uvcvideo: Found UVC 1.00 device USB 2.0 Camera (04f2:b01
Jun 8 12:35:46 Stavros kernel: [ 30.760801] usbcore: registered new interface driver uvcvideo
Jun 8 12:35:46 Stavros kernel: [ 30.760804] USB Video Class driver (v0.1.0)
Jun 8 12:35:46 Stavros kernel: [ 30.822689] iwl4965: Intel(R) Wireless WiFi Link 4965AGN driver for Linux, 1.2.25
Jun 8 12:35:46 Stavros kernel: [ 30.822692] iwl4965: Copyright(c) 2003-2007 Intel Corporation
Jun 8 12:35:46 Stavros kernel: [ 30.822826] ACPI: PCI Interrupt 0000:0c:00.0[A] -> GSI 17 (level, low) -> IRQ 17
Jun 8 12:35:46 Stavros kernel: [ 30.823646] iwl4965: Detected Intel Wireless WiFi Link 4965AGN
Jun 8 12:35:46 Stavros kernel: [ 30.973490] ACPI: PCI interrupt for device 0000:0c:00.0 disabled
Jun 8 12:35:46 Stavros kernel: [ 31.055657] input: ImPS/2 Logitech Wheel Mouse as /devices/platform/i8042/serio1/input/input7
Jun 8 12:35:46 Stavros kernel: [ 31.066952] iTCO_wdt: Found a ICH8M TCO device (Version=2, TCOBASE=0x1060)
Jun 8 12:35:46 Stavros kernel: [ 31.066999] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
Jun 8 12:35:46 Stavros kernel: [ 31.067347] input: PC Speaker as /devices/platform/pcspkr/input/input8
Jun 8 12:35:46 Stavros kernel: [ 31.379006] lp: driver loaded but no devices found
Jun 8 12:35:46 Stavros kernel: [ 31.462800] Adding 3862296k swap on /dev/sda2. Priority:-1 extents:1 across:3862296k
Jun 8 12:35:46 Stavros kernel: [ 31.752634] EXT3 FS on sda1, internal journal
Jun 8 12:35:46 Stavros kernel: [ 32.164047] kjournald starting. Commit interval 5 seconds
Jun 8 12:35:46 Stavros kernel: [ 32.164298] EXT3 FS on sda3, internal journal
Jun 8 12:35:46 Stavros kernel: [ 32.164305] EXT3-fs: mounted filesystem with ordered data mode.
Jun 8 12:35:46 Stavros kernel: [ 32.449943] ip_tables: (C) 2000-2006 Netfilter Core Team
Jun 8 12:35:46 Stavros kernel: [ 32.791446] No dock devices found.
Jun 8 12:35:47 Stavros kernel: [ 33.730547] ppdev: user-space parallel port driver
Jun 8 12:35:48 Stavros kernel: [ 33.906523] audit(1212946548.040:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5151 profile="/usr/sbin/cupsd" namespace="default"
Jun 8 12:35:48 Stavros dhcdbd: Started up.
Jun 8 12:35:49 Stavros kernel: [ 34.847697] ACPI: PCI Interrupt 0000:0c:00.0[A] -> GSI 17 (level, low) -> IRQ 17
Jun 8 12:35:49 Stavros kernel: [ 35.148882] iwl4965: Tunable channels: 11 802.11bg, 13 802.11a channels
Jun 8 12:35:49 Stavros kernel: [ 35.157802] Registered led device: iwl-phy0:RX
Jun 8 12:35:49 Stavros kernel: [ 35.157840] Registered led device: iwl-phy0:TX
Jun 8 12:35:50 Stavros dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Jun 8 12:36:08 Stavros kernel: [ 45.807881] NET: Registered protocol family 10
Jun 8 12:36:08 Stavros kernel: [ 45.808324] lo: Disabled Privacy Extensions
Jun 8 12:36:08 Stavros kernel: [ 45.809623] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jun 8 12:36:08 Stavros kernel: [ 45.810720] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun 8 12:36:20 Stavros dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.reason
Jun 8 12:36:22 Stavros kernel: [ 59.798572] NET: Registered protocol family 17
Jun 8 12:40:14 Stavros dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.reason
Jun 8 12:44:51 Stavros dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.reason
Jun 8 12:46:48 Stavros dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.reason
Jun 8 12:47:57 Stavros kernel: [ 212.270919] gvfs-fuse-daemo[5820] general protection rip:7febb879f423 rsp:7fffc23c7fd0 error:0
Jun 8 12:48:00 Stavros kernel: [ 215.851842] ip6_tables: (C) 2000-2006 Netfilter Core Team
Jun 8 12:48:01 Stavros exiting on signal 15
Jun 8 12:49:01 Stavros syslogd 1.5.0#1ubuntu1: restart.
Jun 8 12:49:01 Stavros kernel: Inspecting /boot/System.map-2.6.24-18-generic
Jun 8 12:49:01 Stavros kernel: Loaded 28488 symbols from /boot/System.map-2.6.24-18-generic.
Jun 8 12:49:01 Stavros kernel: Symbols match kernel version 2.6.24.
Jun 8 12:49:01 Stavros kernel: Loaded 35045 symbols from 93 modules.
Jun 8 12:49:01 Stavros kernel: [ 0.000000] Initializing cgroup subsys cpuset
Jun 8 12:49:01 Stavros kernel: [ 0.000000] Initializing cgroup subsys cpu
Jun 8 12:49:01 Stavros kernel: [ 0.000000] Linux version 2.6.24-18-generic (buildd@king) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed May 28 19:28:38 UTC 2008 (Ubuntu 2.6.24-18.32-generic)
Jun 8 12:49:01 Stavros kernel: [ 0.000000] Command line: root=UUID=6c814527-5db0-4129-b3bc-f41a16213147 ro quiet splash
Jun 8 12:49:01 Stavros kernel: [ 0.000000] BIOS-provided physical RAM map:
Jun 8 12:49:01 Stavros kernel: [ 0.000000] BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
Jun 8 12:49:01 Stavros kernel: [ 0.000000] BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
Jun 8 12:49:01 Stavros kernel: [ 0.000000] BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
Jun 8 12:49:01 Stavros kernel: [ 0.000000] BIOS-e820: 0000000000100000 - 00000000bfed0000 (usable)
Jun 8 12:49:01 Stavros kernel: [ 0.000000] BIOS-e820: 00000000bfed0000 - 00000000bfee3000 (ACPI NVS)
Jun 8 12:49:01 Stavros kernel: [ 0.000000] BIOS-e820: 00000000bfee3000 - 00000000c0000000 (reserved)
Jun 8 12:49:01 Stavros kernel: [ 0.000000] BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
Jun 8 12:49:01 Stavros kernel: [ 0.000000] BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
Jun 8 12:49:01 Stavros kernel: [ 0.000000] BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
Jun 8 12:49:01 Stavros kernel: [ 0.000000] BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
Jun 8 12:49:01 Stavros kernel: [ 0.000000] BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Jun 8 12:49:01 Stavros kernel: [ 0.000000] BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
Jun 8 12:49:01 Stavros kernel: [ 0.000000] BIOS-e820: 0000000100000000 - 0000000140000000 (usable)
Jun 8 12:49:01 Stavros kernel: [ 0.000000] end_pfn_map = 1310720
Jun 8 12:49:01 Stavros kernel: [ 0.000000] DMI present.
Jun 8 12:49:01 Stavros kernel: [ 0.000000] ACPI: RSDP signature @ 0xFFFF8100000F7B40 checksum 0
Jun 8 12:49:01 Stavros kernel: [ 0.000000] ACPI: RSDP 000F7B40, 0024 (r2 Compal)
Jun 8 12:49:01 Stavros kernel: [ 0.000000] ACPI: XSDT BFED8622, 008C (r1 Compal CRESTLNE 6040000 LTP 0)
Jun 8 12:49:01 Stavros kernel: [ 0.000000] ACPI: FACP BFEDFBD2, 00F4 (r3 INTEL CRESTLNE 6040000 ALAN 1)
Jun 8 12:49:01 Stavros kernel: [ 0.000000] ACPI: DSDT BFED9B51, 600D (r2 Compal CRESTLNE 6040000 INTL 20061109)
Jun 8 12:49:01 Stavros kernel: [ 0.000000] ACPI: FACS BFEE2FC0, 0040
Jun 8 12:49:01 Stavros kernel: [ 0.000000] ACPI: APIC BFEDFCC6, 0068 (r1 INTEL CRESTLNE 6040000 LOHR 5A)
Jun 8 12:49:01 Stavros kernel: [ 0.000000] ACPI: HPET BFEDFD2E, 0038 (r1 Compal CRESTLNE 6040000 LOHR 5A)
Jun 8 12:49:01 Stavros kernel: [ 0.000000] ACPI: MCFG BFEDFD66, 003C (r1 INTEL CRESTLNE 6040000 LOHR 5A)
Jun 8 12:49:01 Stavros kernel: [ 0.000000] ACPI: TCPA BFEDFDA2, 0032 (r1 Intel CRESTLNE 6040000 LOHR 5A)
Jun 8 12:49:01 Stavros kernel: [ 0.000000] ACPI: TMOR BFEDFDD4, 0026 (r1 PTLTD 6040000 PTL 3)
Jun 8 12:49:01 Stavros kernel: [ 0.000000] ACPI: SLIC BFEDFDFA, 0176 (r1 Compal CRESTLNE 6040000 TBD 1)
Jun 8 12:49:01 Stavros kernel: [ 0.000000] ACPI: APIC BFEDFF70, 0068 (r1 PTLTD ^I APIC 6040000 LTP 0)
Jun 8 12:49:01 Stavros kernel: [ 0.000000] ACPI: BOOT BFEDFFD8, 0028 (r1 PTLTD $SBFTBL$ 6040000 LTP 1)
Jun 8 12:49:01 Stavros kernel: [ 0.000000] ACPI: SSDT BFED988C, 02C5 (r1 SataRe SataAhci 1000 INTL 20050624)
Jun 8 12:49:01 Stavros kernel: [ 0.000000] ACPI: SSDT BFED8C3A, 025F (r1 PmRef Cpu0Tst 3000 INTL 20050624)
Jun 8 12:49:01 Stavros kernel: [ 0.000000] ACPI: SSDT BFED8B94, 00A6 (r1 PmRef Cpu1Tst 3000 INTL 20050624)
Jun 8 12:49:01 Stavros kernel: [ 0.000000] ACPI: SSDT BFED86AE, 04E6 (r1 PmRef CpuPm 3000 INTL 20050624)
Jun 8 12:49:01 Stavros kernel: [ 0.000000] ACPI: BIOS bug: multiple APIC/MADT found, using 0
Jun 8 12:49:01 Stavros kernel: [ 0.000000] ACPI: If "acpi_apic_instance=2" works better, notify [email]linux-acpi@vger.kernel.org[/email]
Jun 8 12:49:01 Stavros kernel: [ 0.000000] ACPI: DMI detected: Compal
Jun 8 12:49:01 Stavros kernel: [ 0.000000] No NUMA configuration found
Jun 8 12:49:01 Stavros kernel: [ 0.000000] Faking a node at 0000000000000000-0000000140000000
Jun 8 12:49:01 Stavros kernel: [ 0.000000] Bootmem setup node 0 0000000000000000-0000000140000000
Jun 8 12:49:01 Stavros kernel: [ 0.000000] Zone PFN ranges:
Jun 8 12:49:01 Stavros kernel: [ 0.000000] DMA 0 -> 4096
Jun 8 12:49:01 Stavros kernel: [ 0.000000] DMA32 4096 -> 1048576
Jun 8 12:49:01 Stavros kernel: [ 0.000000] Normal 1048576 -> 1310720
Jun 8 12:49:01 Stavros kernel: [ 0.000000] Movable zone start PFN for each node
Jun 8 12:49:01 Stavros kernel: [ 0.000000] early_node_map[3] active PFN ranges
Jun 8 12:49:01 Stavros kernel: [ 0.000000] 0: 0 -> 159
Jun 8 12:49:01 Stavros kernel: [ 0.000000] 0: 256 -> 786128
Jun 8 12:49:01 Stavros kernel: [ 0.000000] 0: 1048576 -> 1310720
Jun 8 12:49:01 Stavros kernel: [ 0.000000] ACPI: PM-Timer IO Port: 0x1008
Jun 8 12:49:01 Stavros kernel: [ 0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Jun 8 12:49:01 Stavros kernel: [ 0.000000] Processor #0 (Bootup-CPU)
Jun 8 12:49:01 Stavros kernel: [ 0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Jun 8 12:49:01 Stavros kernel: [ 0.000000] Processor #1
Jun 8 12:49:01 Stavros kernel: [ 0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
Jun 8 12:49:01 Stavros kernel: [ 0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
Jun 8 12:49:01 Stavros kernel: [ 0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
Jun 8 12:49:01 Stavros kernel: [ 0.000000] IOAPIC[0]: apic_id 1, address 0xfec00000, GSI 0-23
Jun 8 12:49:01 Stavros kernel: [ 0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Jun 8 12:49:01 Stavros kernel: [ 0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Jun 8 12:49:01 Stavros kernel: [ 0.000000] Setting APIC routing to flat
Jun 8 12:49:01 Stavros kernel: [ 0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
Jun 8 12:49:01 Stavros kernel: [ 0.000000] Using ACPI (MADT) for SMP configuration information
Jun 8 12:49:01 Stavros kernel: [ 0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
Jun 8 12:49:01 Stavros kernel: [ 0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000dc000
Jun 8 12:49:01 Stavros kernel: [ 0.000000] swsusp: Registered nosave memory region: 00000000000dc000 - 0000000000100000
Jun 8 12:49:01 Stavros kernel: [ 0.000000] swsusp: Registered nosave memory region: 00000000bfed0000 - 00000000bfee3000
Jun 8 12:49:01 Stavros kernel: [ 0.000000] swsusp: Registered nosave memory region: 00000000bfee3000 - 00000000c0000000
Jun 8 12:49:01 Stavros kernel: [ 0.000000] swsusp: Registered nosave memory region: 00000000c0000000 - 00000000fec00000
Jun 8 12:49:01 Stavros kernel: [ 0.000000] swsusp: Registered nosave memory region: 00000000fec00000 - 00000000fec10000
Jun 8 12:49:01 Stavros kernel: [ 0.000000] swsusp: Registered nosave memory region: 00000000fec10000 - 00000000fed00000
Jun 8 12:49:01 Stavros kernel: [ 0.000000] swsusp: Registered nosave memory region: 00000000fed00000 - 00000000fed14000
Jun 8 12:49:01 Stavros kernel: [ 0.000000] swsusp: Registered nosave memory region: 00000000fed14000 - 00000000fed1a000
Jun 8 12:49:01 Stavros kernel: [ 0.000000] swsusp: Registered nosave memory region: 00000000fed1a000 - 00000000fed1c000
Jun 8 12:49:01 Stavros kernel: [ 0.000000] swsusp: Registered nosave memory region: 00000000fed1c000 - 00000000fed90000
Jun 8 12:49:01 Stavros kernel: [ 0.000000] swsusp: Registered nosave memory region: 00000000fed90000 - 00000000fee00000
Jun 8 12:49:01 Stavros kernel: [ 0.000000] swsusp: Registered nosave memory region: 00000000fee00000 - 00000000fee01000
Jun 8 12:49:01 Stavros kernel: [ 0.000000] swsusp: Registered nosave memory region: 00000000fee01000 - 00000000ff000000
Jun 8 12:49:01 Stavros kernel: [ 0.000000] swsusp: Registered nosave memory region: 00000000ff000000 - 0000000100000000
Jun 8 12:49:01 Stavros kernel: [ 0.000000] Allocating PCI resources starting at c4000000 (gap: c0000000:3ec00000)
Jun 8 12:49:01 Stavros kernel: [ 0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
Jun 8 12:49:01 Stavros kernel: [ 0.000000] PERCPU: Allocating 34656 bytes of per cpu data
Jun 8 12:49:01 Stavros kernel: [ 0.000000] Built 1 zonelists in Node order, mobility grouping on. Total pages: 1029033
Jun 8 12:49:01 Stavros kernel: [ 0.000000] Policy zone: Normal
Jun 8 12:49:01 Stavros kernel: [ 0.000000] Kernel command line: root=UUID=6c814527-5db0-4129-b3bc-f41a16213147 ro quiet splash
Jun 8 12:49:01 Stavros kernel: [ 0.000000] Initializing CPU#0
Jun 8 12:49:01 Stavros kernel: [ 0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
Jun 8 12:49:01 Stavros kernel: [ 0.000000] Extended CMOS year: 2000
Jun 8 12:49:01 Stavros kernel: [ 0.000000] TSC calibrated against HPET
Jun 8 12:49:01 Stavros kernel: [ 17.085461] Marking TSC unstable due to TSCs unsynchronized
Jun 8 12:49:01 Stavros kernel: [ 17.085463] time.c: Detected 2394.003 MHz processor.
Jun 8 12:49:01 Stavros kernel: [ 17.089384] Console: colour VGA+ 80x25
Jun 8 12:49:01 Stavros kernel: [ 17.089386] console [tty0] enabled
Jun 8 12:49:01 Stavros kernel: [ 17.089404] Checking aperture...
Jun 8 12:49:01 Stavros kernel: [ 17.089417] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
Jun 8 12:49:01 Stavros kernel: [ 17.124127] Placing software IO TLB between 0x103b000 - 0x503b000
Jun 8 12:49:01 Stavros kernel: [ 17.160280] Memory: 4042428k/5242880k available (2488k kernel code, 150272k reserved, 1319k data, 320k init)
Jun 8 12:49:01 Stavros kernel: [ 17.160314] SLUB: Genslabs=12, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
Jun 8 12:49:01 Stavros kernel: [ 17.239184] Calibrating delay using timer specific routine.. 4792.47 BogoMIPS (lpj=9584942)
Jun 8 12:49:01 Stavros kernel: [ 17.239211] Security Framework initialized
Jun 8 12:49:01 Stavros kernel: [ 17.239217] SELinux: Disabled at boot.
Jun 8 12:49:01 Stavros kernel: [ 17.239227] AppArmor: AppArmor initialized
Jun 8 12:49:01 Stavros kernel: [ 17.239231] Failure registering capabilities with primary security module.
Jun 8 12:49:01 Stavros kernel: [ 17.239502] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
Jun 8 12:49:01 Stavros kernel: [ 17.241876] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
Jun 8 12:49:01 Stavros kernel: [ 17.243005] Mount-cache hash table entries: 256
Jun 8 12:49:01 Stavros kernel: [ 17.243126] Initializing cgroup subsys ns
Jun 8 12:49:01 Stavros kernel: [ 17.243132] Initializing cgroup subsys cpuacct
Jun 8 12:49:01 Stavros kernel: [ 17.243145] CPU: L1 I cache: 32K, L1 D cache: 32K
Jun 8 12:49:01 Stavros kernel: [ 17.243146] CPU: L2 cache: 3072K
Jun 8 12:49:01 Stavros kernel: [ 17.243148] CPU 0/0 -> Node 0
Jun 8 12:49:01 Stavros kernel: [ 17.243149] using mwait in idle threads.
Jun 8 12:49:01 Stavros kernel: [ 17.243151] CPU: Physical Processor ID: 0
Jun 8 12:49:01 Stavros kernel: [ 17.243151] CPU: Processor Core ID: 0
Jun 8 12:49:01 Stavros kernel: [ 17.243168] SMP alternatives: switching to UP code
Jun 8 12:49:01 Stavros kernel: [ 17.243892] Early unpacking initramfs... done
Jun 8 12:49:01 Stavros kernel: [ 17.509462] ACPI: Core revision 20070126
Jun 8 12:49:01 Stavros kernel: [ 17.509497] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Jun 8 12:49:01 Stavros kernel: [ 17.556898] Using local APIC timer interrupts.
Jun 8 12:49:01 Stavros kernel: [ 17.598601] Detected 12.468 MHz APIC timer.
Jun 8 12:49:01 Stavros kernel: [ 17.598663] SMP alternatives: switching to SMP code
Jun 8 12:49:01 Stavros kernel: [ 17.599277] Booting processor 1/2 APIC 0x1
Jun 8 12:49:01 Stavros kernel: [ 17.609647] Initializing CPU#1
Jun 8 12:49:01 Stavros kernel: [ 17.686454] Calibrating delay using timer specific routine.. 4788.03 BogoMIPS (lpj=9576074)
Jun 8 12:49:01 Stavros kernel: [ 17.686459] CPU: L1 I cache: 32K, L1 D cache: 32K
Jun 8 12:49:01 Stavros kernel: [ 17.686460] CPU: L2 cache: 3072K
Jun 8 12:49:01 Stavros kernel: [ 17.686462] CPU 1/1 -> Node 0
Jun 8 12:49:01 Stavros kernel: [ 17.686463] CPU: Physical Processor ID: 0
Jun 8 12:49:01 Stavros kernel: [ 17.686464] CPU: Processor Core ID: 1
Jun 8 12:49:01 Stavros kernel: [ 17.686469] CPU1: Thermal monitoring enabled (TM2)
Jun 8 12:49:01 Stavros kernel: [ 17.686897] Intel(R) Core(TM)2 Duo CPU T8300 @ 2.40GHz stepping 06
Jun 8 12:49:01 Stavros kernel: [ 17.686967] Brought up 2 CPUs
Jun 8 12:49:01 Stavros kernel: [ 17.687238] net_namespace: 120 bytes
Jun 8 12:49:01 Stavros kernel: [ 17.687531] Time: 17:48:27 Date: 06/08/08
Jun 8 12:49:01 Stavros kernel: [ 17.687552] NET: Registered protocol family 16
Jun 8 12:49:01 Stavros kernel: [ 17.687704] ACPI: bus type pci registered
Jun 8 12:49:01 Stavros kernel: [ 17.687761] PCI: Using configuration type 1
Jun 8 12:49:01 Stavros kernel: [ 17.690212] ACPI: BIOS _OSI(Linux) query ignored via DMI
Jun 8 12:49:01 Stavros kernel: [ 17.690214] ACPI: If "acpi_osi=Linux" works better, please notify [email]linux-acpi@vger.kernel.org[/email]
Jun 8 12:49:01 Stavros kernel: [ 17.690628] ACPI: Interpreter enabled
Jun 8 12:49:01 Stavros kernel: [ 17.690631] ACPI: (supports S0 S3 S4 S5)
Jun 8 12:49:01 Stavros kernel: [ 17.690642] ACPI: Using IOAPIC for interrupt routing
Jun 8 12:49:01 Stavros kernel: [ 17.730801] ACPI: EC: GPE = 0x1c, I/O: command/status = 0x66, data = 0x62
Jun 8 12:49:01 Stavros kernel: [ 17.730803] ACPI: EC: driver started in poll mode
Jun 8 12:49:01 Stavros kernel: [ 17.730830] ACPI: PCI Root Bridge [PCI0] (0000:00)
Jun 8 12:49:01 Stavros kernel: [ 17.731786] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
Jun 8 12:49:01 Stavros kernel: [ 17.731789] PCI quirk: region 1180-11bf claimed by ICH6 GPIO
Jun 8 12:49:01 Stavros kernel: [ 17.733433] PCI: Transparent bridge - 0000:00:1e.0
Jun 8 12:49:01 Stavros kernel: [ 17.737970] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 *5 6 7 10 12 14 15)
Jun 8 12:49:01 Stavros kernel: [ 17.738046] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
Jun 8 12:49:01 Stavros kernel: [ 17.738120] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 *7 10 12 14 15)
Jun 8 12:49:01 Stavros kernel: [ 17.738194] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
Jun 8 12:49:01 Stavros kernel: [ 17.738270] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
Jun 8 12:49:01 Stavros kernel: [ 17.738344] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 *11 12 14 15)
Jun 8 12:49:01 Stavros kernel: [ 17.738420] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
Jun 8 12:49:01 Stavros kernel: [ 17.738493] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
Jun 8 12:49:01 Stavros kernel: [ 17.738600] Linux Plug and Play Support v0.97 (c) Adam Belay
Jun 8 12:49:01 Stavros kernel: [ 17.738624] pnp: PnP ACPI init
Jun 8 12:49:01 Stavros kernel: [ 17.738629] ACPI: bus type pnp registered
Jun 8 12:49:01 Stavros kernel: [ 17.758478] pnp: PnP ACPI: found 11 devices
Jun 8 12:49:01 Stavros kernel: [ 17.758479] ACPI: ACPI bus type pnp unregistered
Jun 8 12:49:01 Stavros kernel: [ 17.758647] PCI: Using ACPI for IRQ routing
Jun 8 12:49:01 Stavros kernel: [ 17.758649] PCI: If a device doesn't work, try "pci=routeirq". If it helps, post a report
Jun 8 12:49:01 Stavros kernel: [ 17.758653] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.0
Jun 8 12:49:01 Stavros kernel: [ 17.758655] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.3
Jun 8 12:49:01 Stavros kernel: [ 17.770324] NET: Registered protocol family 8
Jun 8 12:49:01 Stavros kernel: [ 17.770325] NET: Registered protocol family 20
Jun 8 12:49:01 Stavros kernel: [ 17.770350] PCI-GART: No AMD northbridge found.
Jun 8 12:49:01 Stavros kernel: [ 17.770354] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
Jun 8 12:49:01 Stavros kernel: [ 17.770357] hpet0: 3 64-bit timers, 14318180 Hz
Jun 8 12:49:01 Stavros kernel: [ 17.771384] AppArmor: AppArmor Filesystem Enabled
Jun 8 12:49:01 Stavros kernel: [ 17.774304] Time: hpet clocksource has been installed.
Jun 8 12:49:01 Stavros kernel: [ 17.782282] system 00:01: iomem range 0xfed1c000-0xfed1ffff could not be reserved
Jun 8 12:49:01 Stavros kernel: [ 17.782285] system 00:01: iomem range 0xfed14000-0xfed17fff could not be reserved
Jun 8 12:49:01 Stavros kernel: [ 17.782287] system 00:01: iomem range 0xfed18000-0xfed18fff could not be reserved
Jun 8 12:49:01 Stavros kernel: [ 17.782290] system 00:01: iomem range 0xfed19000-0xfed19fff could not be reserved
Jun 8 12:49:01 Stavros kernel: [ 17.782292] system 00:01: iomem range 0xe0000000-0xefffffff has been reserved
Jun 8 12:49:01 Stavros kernel: [ 17.782294] system 00:01: iomem range 0xfed20000-0xfed3ffff could not be reserved
Jun 8 12:49:01 Stavros kernel: [ 17.782296] system 00:01: iomem range 0xfed40000-0xfed44fff could not be reserved
Jun 8 12:49:01 Stavros kernel: [ 17.782299] system 00:01: iomem range 0xfed45000-0xfed8ffff could not be reserved
Jun 8 12:49:01 Stavros kernel: [ 17.782304] system 00:05: iomem range 0xfed00000-0xfed003ff could not be reserved
Jun 8 12:49:01 Stavros kernel: [ 17.782308] system 00:07: ioport range 0x680-0x69f has been reserved
Jun 8 12:49:01 Stavros kernel: [ 17.782310] system 00:07: ioport range 0x800-0x80f has been reserved
Jun 8 12:49:01 Stavros kernel: [ 17.782312] system 00:07: ioport range 0x1000-0x107f has been reserved
Jun 8 12:49:01 Stavros kernel: [ 17.782314] system 00:07: ioport range 0x1180-0x11bf has been reserved
Jun 8 12:49:01 Stavros kernel: [ 17.782317] system 00:07: ioport range 0x1640-0x164f has been reserved
Jun 8 12:49:01 Stavros kernel: [ 17.782319] system 00:07: ioport range 0xfe00-0xfe00 has been reserved
Jun 8 12:49:01 Stavros kernel: [ 17.782321] system 00:07: ioport range 0xff00-0xff7f has been reserved
Jun 8 12:49:01 Stavros kernel: [ 17.782640] PCI: Failed to allocate mem resource #6:20000@e0000000 for 0000:01:00.0
Jun 8 12:49:01 Stavros kernel: [ 17.782643] PCI: Bridge: 0000:00:01.0
Jun 8 12:49:01 Stavros kernel: [ 17.782644] IO window: 2000-2fff
Jun 8 12:49:01 Stavros kernel: [ 17.782647] MEM window: c4000000-c6ffffff
Jun 8 12:49:01 Stavros kernel: [ 17.782649] PREFETCH window: d0000000-dfffffff
Jun 8 12:49:01 Stavros kernel: [ 17.782651] PCI: Bridge: 0000:00:1c.0
Jun 8 12:49:01 Stavros kernel: [ 17.782653] IO window: 3000-3fff
Jun 8 12:49:01 Stavros kernel: [ 17.782658] MEM window: disabled.
Jun 8 12:49:01 Stavros kernel: [ 17.782661] PREFETCH window: cc000000-cdffffff
Jun 8 12:49:01 Stavros kernel: [ 17.782666] PCI: Bridge: 0000:00:1c.1
Jun 8 12:49:01 Stavros kernel: [ 17.782668] IO window: 4000-4fff
Jun 8 12:49:01 Stavros kernel: [ 17.782673] MEM window: f0000000-f3ffffff
Jun 8 12:49:01 Stavros kernel: [ 17.782677] PREFETCH window: fa000000-fbffffff
Jun 8 12:49:01 Stavros kernel: [ 17.782682] PCI: Bridge: 0000:00:1c.2
Jun 8 12:49:01 Stavros kernel: [ 17.782685] IO window: 5000-5fff
Jun 8 12:49:01 Stavros kernel: [ 17.782689] MEM window: f4000000-f7ffffff
Jun 8 12:49:01 Stavros kernel: [ 17.782693] PREFETCH window: fc000000-fdffffff
Jun 8 12:49:01 Stavros kernel: [ 17.782698] PCI: Bridge: 0000:00:1c.3
Jun 8 12:49:01 Stavros kernel: [ 17.782700] IO window: 6000-6fff
Jun 8 12:49:01 Stavros kernel: [ 17.782705] MEM window: disabled.
Jun 8 12:49:01 Stavros kernel: [ 17.782708] PREFETCH window: c8000000-c9ffffff
Jun 8 12:49:01 Stavros kernel: [ 17.782714] PCI: Bridge: 0000:00:1c.4
Jun 8 12:49:01 Stavros kernel: [ 17.782714] IO window: disabled.
Jun 8 12:49:01 Stavros kernel: [ 17.782719] MEM window: disabled.
Jun 8 12:49:01 Stavros kernel: [ 17.782722] PREFETCH window: disabled.
Jun 8 12:49:01 Stavros kernel: [ 17.782727] PCI: Bridge: 0000:00:1c.5
Jun 8 12:49:01 Stavros kernel: [ 17.782728] IO window: disabled.
Jun 8 12:49:01 Stavros kernel: [ 17.782733] MEM window: f8000000-f80fffff
Jun 8 12:49:01 Stavros kernel: [ 17.782737] PREFETCH window: disabled.
Jun 8 12:49:01 Stavros kernel: [ 17.782742] PCI: Bridge: 0000:00:1e.0
Jun 8 12:49:01 Stavros kernel: [ 17.782743] IO window: disabled.
Jun 8 12:49:01 Stavros kernel: [ 17.782748] MEM window: f8100000-f81fffff
Jun 8 12:49:01 Stavros kernel: [ 17.782752] PREFETCH window: disabled.
Jun 8 12:49:01 Stavros kernel: [ 17.782765] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
Jun 8 12:49:01 Stavros kernel: [ 17.782790] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 17
Jun 8 12:49:01 Stavros kernel: [ 17.782815] ACPI: PCI Interrupt 0000:00:1c.1[b] -> GSI 16 (level, low) -> IRQ 16
Jun 8 12:49:01 Stavros kernel: [ 17.782842] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 18
Jun 8 12:49:01 Stavros kernel: [ 17.782867] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 19
Jun 8 12:49:01 Stavros kernel: [ 17.782892] ACPI: PCI Interrupt 0000:00:1c.4[A] -> GSI 17 (level, low) -> IRQ 17
Jun 8 12:49:01 Stavros kernel: [ 17.782917] ACPI: PCI Interrupt 0000:00:1c.5[b] -> GSI 16 (level, low) -> IRQ 16
Jun 8 12:49:01 Stavros kernel: [ 17.782942] NET: Registered protocol family 2
Jun 8 12:49:01 Stavros kernel: [ 17.818299] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
Jun 8 12:49:01 Stavros kernel: [ 17.819194] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
Jun 8 12:49:01 Stavros kernel: [ 17.823277] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
Jun 8 12:49:01 Stavros kernel: [ 17.823824] TCP: Hash tables configured (established 524288 bind 65536)
Jun 8 12:49:01 Stavros kernel: [ 17.823826] TCP reno registered
Jun 8 12:49:01 Stavros kernel: [ 17.834305] checking if image is initramfs... it is
Jun 8 12:49:01 Stavros kernel: [ 18.397638] Freeing initrd memory: 7477k freed
Jun 8 12:49:01 Stavros kernel: [ 18.401050] Simple Boot Flag at 0x38 set to 0x80
Jun 8 12:49:01 Stavros kernel: [ 18.401750] audit: initializing netlink socket (disabled)
Jun 8 12:49:01 Stavros kernel: [ 18.401767] audit(1212947307.284:1): initialized
Jun 8 12:49:01 Stavros kernel: [ 18.403476] VFS: Disk quotas dquot_6.5.1
Jun 8 12:49:01 Stavros kernel: [ 18.403525] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
Jun 8 12:49:01 Stavros kernel: [ 18.403614] io scheduler noop registered
Jun 8 12:49:01 Stavros kernel: [ 18.403616] io scheduler anticipatory registered
Jun 8 12:49:01 Stavros kernel: [ 18.403617] io scheduler deadline registered
Jun 8 12:49:01 Stavros kernel: [ 18.403697] io scheduler cfq registered (default)
Jun 8 12:49:01 Stavros kernel: [ 18.407001] assign_interrupt_mode Found MSI capability
Jun 8 12:49:01 Stavros kernel: [ 18.407170] assign_interrupt_mode Found MSI capability
Jun 8 12:49:01 Stavros kernel: [ 18.407375] assign_interrupt_mode Found MSI capability
Jun 8 12:49:01 Stavros kernel: [ 18.407579] assign_interrupt_mode Found MSI capability
Jun 8 12:49:01 Stavros kernel: [ 18.407788] assign_interrupt_mode Found MSI capability
Jun 8 12:49:01 Stavros kernel: [ 18.407993] assign_interrupt_mode Found MSI capability
Jun 8 12:49:01 Stavros kernel: [ 18.408197] assign_interrupt_mode Found MSI capability
Jun 8 12:49:01 Stavros kernel: [ 18.426817] Real Time Clock Driver v1.12ac
Jun 8 12:49:01 Stavros kernel: [ 18.427018] Linux agpgart interface v0.102
Jun 8 12:49:01 Stavros kernel: [ 18.427020] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Jun 8 12:49:01 Stavros kernel: [ 18.427840] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Jun 8 12:49:01 Stavros kernel: [ 18.427889] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Jun 8 12:49:01 Stavros kernel: [ 18.427956] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Jun 8 12:49:01 Stavros kernel: [ 18.470887] serio: i8042 KBD port at 0x60,0x64 irq 1
Jun 8 12:49:01 Stavros kernel: [ 18.470890] serio: i8042 AUX port at 0x60,0x64 irq 12
Jun 8 12:49:01 Stavros kernel: [ 18.490075] mice: PS/2 mouse device common for all mice
Jun 8 12:49:01 Stavros kernel: [ 18.490104] cpuidle: using governor ladder
Jun 8 12:49:01 Stavros kernel: [ 18.490106] cpuidle: using governor menu
Jun 8 12:49:01 Stavros kernel: [ 18.490210] NET: Registered protocol family 1
Jun 8 12:49:01 Stavros kernel: [ 18.490289] registered taskstats version 1
Jun 8 12:49:01 Stavros kernel: [ 18.490394] Magic number: 12:191:845
Jun 8 12:49:01 Stavros kernel: [ 18.490444] hash matches device ptyre
Jun 8 12:49:01 Stavros kernel: [ 18.490478] /build/buildd/linux-2.6.24/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
Jun 8 12:49:01 Stavros kernel: [ 18.490480] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Jun 8 12:49:01 Stavros kernel: [ 18.490482] EDD information not available.
Jun 8 12:49:01 Stavros kernel: [ 18.490488] Freeing unused kernel memory: 320k freed
Jun 8 12:49:01 Stavros kernel: [ 18.523099] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
Jun 8 12:49:01 Stavros kernel: [ 19.646880] fuse init (API version 7.9)
Jun 8 12:49:01 Stavros kernel: [ 19.678805] ACPI: SSDT BFED9508, 02BC (r1 PmRef Cpu0Ist 3000 INTL 20050624)
Jun 8 12:49:01 Stavros kernel: [ 19.678984] ACPI: SSDT BFED8E99, 05EA (r1 PmRef Cpu0Cst 3001 INTL 20050624)
Jun 8 12:49:01 Stavros kernel: [ 19.680605] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
Jun 8 12:49:01 Stavros kernel: [ 19.680609] ACPI: Processor [CPU0] (supports 8 throttling states)
Jun 8 12:49:01 Stavros kernel: [ 19.680779] ACPI: SSDT BFED97C4, 00C8 (r1 PmRef Cpu1Ist 3000 INTL 20050624)
Jun 8 12:49:01 Stavros kernel: [ 19.680926] ACPI: SSDT BFED9483, 0085 (r1 PmRef Cpu1Cst 3000 INTL 20050624)
Jun 8 12:49:01 Stavros kernel: [ 19.681756] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
Jun 8 12:49:01 Stavros kernel: [ 19.681760] ACPI: Processor [CPU1] (supports 8 throttling states)
Jun 8 12:49:01 Stavros kernel: [ 19.841580] usbcore: registered new interface driver usbfs
Jun 8 12:49:01 Stavros kernel: [ 19.841597] usbcore: registered new interface driver hub
Jun 8 12:49:01 Stavros kernel: [ 19.841930] usbcore: registered new device driver usb
Jun 8 12:49:01 Stavros kernel: [ 19.847660] USB Universal Host Controller Interface driver v3.0
Jun 8 12:49:01 Stavros kernel: [ 19.847703] ACPI: PCI Interrupt 0000:00:1a.0[A] -> GSI 16 (level, low) -> IRQ 16
Jun 8 12:49:01 Stavros kernel: [ 19.847715] uhci_hcd 0000:00:1a.0: UHCI Host Controller
Jun 8 12:49:01 Stavros kernel: [ 19.847920] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
Jun 8 12:49:01 Stavros kernel: [ 19.847951] uhci_hcd 0000:00:1a.0: irq 16, io base 0x00001800
Jun 8 12:49:01 Stavros kernel: [ 19.848050] usb usb1: configuration #1 chosen from 1 choice
Jun 8 12:49:01 Stavros kernel: [ 19.848065] hub 1-0:1.0: USB hub found
Jun 8 12:49:01 Stavros kernel: [ 19.848070] hub 1-0:1.0: 2 ports detected
Jun 8 12:49:01 Stavros kernel: [ 19.951519] ACPI: PCI Interrupt 0000:00:1a.1[b] -> GSI 21 (level, low) -> IRQ 21
Jun 8 12:49:01 Stavros kernel: [ 19.951534] uhci_hcd 0000:00:1a.1: UHCI Host Controller
Jun 8 12:49:01 Stavros kernel: [ 19.951558] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
Jun 8 12:49:01 Stavros kernel: [ 19.951589] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00001820
Jun 8 12:49:01 Stavros kernel: [ 19.951670] usb usb2: configuration #1 chosen from 1 choice
Jun 8 12:49:01 Stavros kernel: [ 19.951687] hub 2-0:1.0: USB hub found
Jun 8 12:49:01 Stavros kernel: [ 19.951692] hub 2-0:1.0: 2 ports detected
Jun 8 12:49:01 Stavros kernel: [ 20.053115] SCSI subsystem initialized
Jun 8 12:49:01 Stavros kernel: [ 20.056912] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 23
Jun 8 12:49:01 Stavros kernel: [ 20.056925] uhci_hcd 0000:00:1d.0: UHCI Host Controller
Jun 8 12:49:01 Stavros kernel: [ 20.056942] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 3
Jun 8 12:49:01 Stavros kernel: [ 20.056972] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00001840
Jun 8 12:49:01 Stavros kernel: [ 20.057057] usb usb3: configuration #1 chosen from 1 choice
Jun 8 12:49:01 Stavros kernel: [ 20.057074] hub 3-0:1.0: USB hub found
Jun 8 12:49:01 Stavros kernel: [ 20.057079] hub 3-0:1.0: 2 ports detected
Jun 8 12:49:01 Stavros kernel: [ 20.159143] ACPI: PCI Interrupt 0000:00:1d.1[b] -> GSI 19 (level, low) -> IRQ 19
Jun 8 12:49:01 Stavros kernel: [ 20.159157] uhci_hcd 0000:00:1d.1: UHCI Host Controller
Jun 8 12:49:01 Stavros kernel: [ 20.159175] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 4
Jun 8 12:49:01 Stavros kernel: [ 20.159205] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001860
Jun 8 12:49:01 Stavros kernel: [ 20.159287] usb usb4: configuration #1 chosen from 1 choice
Jun 8 12:49:01 Stavros kernel: [ 20.159304] hub 4-0:1.0: USB hub found
Jun 8 12:49:01 Stavros kernel: [ 20.159308] hub 4-0:1.0: 2 ports detected
Jun 8 12:49:01 Stavros kernel: [ 20.262976] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
Jun 8 12:49:01 Stavros kernel: [ 20.262991] uhci_hcd 0000:00:1d.2: UHCI Host Controller
Jun 8 12:49:01 Stavros kernel: [ 20.263016] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 5
Jun 8 12:49:01 Stavros kernel: [ 20.263049] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001880
Jun 8 12:49:01 Stavros kernel: [ 20.263135] usb usb5: configuration #1 chosen from 1 choice
Jun 8 12:49:01 Stavros kernel: [ 20.263151] hub 5-0:1.0: USB hub found
Jun 8 12:49:01 Stavros kernel: [ 20.263155] hub 5-0:1.0: 2 ports detected
Jun 8 12:49:01 Stavros kernel: [ 20.352930] ACPI: PCI Interrupt 0000:00:1a.7[C] -> GSI 18 (level, low) -> IRQ 18
Jun 8 12:49:01 Stavros kernel: [ 20.353730] ehci_hcd 0000:00:1a.7: EHCI Host Controller
Jun 8 12:49:01 Stavros kernel: [ 20.353797] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 6
Jun 8 12:49:01 Stavros kernel: [ 20.357701] ehci_hcd 0000:00:1a.7: debug port 1
Jun 8 12:49:01 Stavros kernel: [ 20.357713] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xf8404800
Jun 8 12:49:01 Stavros kernel: [ 20.372677] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Jun 8 12:49:01 Stavros kernel: [ 20.372781] usb usb6: configuration #1 chosen from 1 choice
Jun 8 12:49:01 Stavros kernel: [ 20.372798] hub 6-0:1.0: USB hub found
Jun 8 12:49:01 Stavros kernel: [ 20.372804] hub 6-0:1.0: 4 ports detected
Jun 8 12:49:01 Stavros kernel: [ 20.476746] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 23
Jun 8 12:49:01 Stavros kernel: [ 20.477552] ehci_hcd 0000:00:1d.7: EHCI Host Controller
Jun 8 12:49:01 Stavros kernel: [ 20.477596] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 7
Jun 8 12:49:01 Stavros kernel: [ 20.481520] ehci_hcd 0000:00:1d.7: debug port 1
Jun 8 12:49:01 Stavros kernel: [ 20.481532] ehci_hcd 0000:00:1d.7: irq 23, io mem 0xf8404c00
Jun 8 12:49:01 Stavros kernel: [ 20.496480] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
Jun 8 12:49:01 Stavros kernel: [ 20.496570] usb usb7: configuration #1 chosen from 1 choice
Jun 8 12:49:01 Stavros kernel: [ 20.496588] hub 7-0:1.0: USB hub found
Jun 8 12:49:01 Stavros kernel: [ 20.496594] hub 7-0:1.0: 6 ports detected
Jun 8 12:49:01 Stavros kernel: [ 20.551587] ACPI: PCI Interrupt 0000:0e:06.0[A] -> GSI 22 (level, low) -> IRQ 22
Jun 8 12:49:01 Stavros kernel: [ 20.604691] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[22] MMIO=[f8100000-f81007ff] Max Packet=[2048] IR/IT contexts=[4/4]
Jun 8 12:49:01 Stavros kernel: [ 20.608816] ACPI: PCI Interrupt 0000:00:1f.2[b] -> GSI 19 (level, low) -> IRQ 19
Jun 8 12:49:01 Stavros kernel: [ 20.683523] usb 6-2: new high speed USB device using ehci_hcd and address 2
Jun 8 12:49:01 Stavros kernel: [ 20.811056] Clocksource tsc unstable (delta = -239936037 ns)
Jun 8 12:49:01 Stavros kernel: [ 20.842687] usb 6-2: configuration #1 chosen from 1 choice
Jun 8 12:49:01 Stavros kernel: [ 21.060168] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 3 Gbps 0x7 impl SATA mode
Jun 8 12:49:01 Stavros kernel: [ 21.060174] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part
Jun 8 12:49:01 Stavros kernel: [ 21.060397] scsi0 : ahci
Jun 8 12:49:01 Stavros kernel: [ 21.060435] scsi1 : ahci
Jun 8 12:49:01 Stavros kernel: [ 21.060464] scsi2 : ahci
Jun 8 12:49:01 Stavros kernel: [ 21.060527] ata1: SATA max UDMA/133 abar m2048@0xf8404000 port 0xf8404100 irq 504
Jun 8 12:49:01 Stavros kernel: [ 21.060530] ata2: SATA max UDMA/133 abar m2048@0xf8404000 port 0xf8404180 irq 504
Jun 8 12:49:01 Stavros kernel: [ 21.060533] ata3: SATA max UDMA/133 abar m2048@0xf8404000 port 0xf8404200 irq 504
Jun 8 12:49:01 Stavros kernel: [ 21.076186] usb 2-2: new full speed USB device using uhci_hcd and address 2
Jun 8 12:49:01 Stavros kernel: [ 21.117712] usb 2-2: configuration #1 chosen from 1 choice
Jun 8 12:49:01 Stavros kernel: [ 21.190252] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Jun 8 12:49:01 Stavros kernel: [ 21.192535] ata1.00: ATA-7: ST9160823AS, 3.AAB, max UDMA/133
Jun 8 12:49:01 Stavros kernel: [ 21.192537] ata1.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 31/32)
Jun 8 12:49:01 Stavros kernel: [ 21.193231] ata1.00: configured for UDMA/133
Jun 8 12:49:01 Stavros kernel: [ 21.243471] ata2: SATA link down (SStatus 0 SControl 300)
Jun 8 12:49:01 Stavros kernel: [ 21.299155] ata3: SATA link down (SStatus 0 SControl 300)
Jun 8 12:49:01 Stavros kernel: [ 21.299283] scsi 0:0:0:0: Direct-Access ATA ST9160823AS 3.AA PQ: 0 ANSI: 5
Jun 8 12:49:01 Stavros kernel: [ 21.300185] tg3.c:v3.86 (November 9, 2007)
Jun 8 12:49:01 Stavros kernel: [ 21.300266] ACPI: PCI Interrupt 0000:04:00.0[A] -> GSI 17 (level, low) -> IRQ 17
Jun 8 12:49:01 Stavros kernel: [ 21.305117] Driver 'sd' needs updating - please use bus_type methods
Jun 8 12:49:01 Stavros kernel: [ 21.313081] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
Jun 8 12:49:01 Stavros kernel: [ 21.313089] sd 0:0:0:0: [sda] Write Protect is off
Jun 8 12:49:01 Stavros kernel: [ 21.313102] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jun 8 12:49:01 Stavros kernel: [ 21.313137] sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
Jun 8 12:49:01 Stavros kernel: [ 21.313143] sd 0:0:0:0: [sda] Write Protect is off
Jun 8 12:49:01 Stavros kernel: [ 21.313155] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jun 8 12:49:01 Stavros kernel: [ 21.313158] sda: sda1 sda2 sda3
Jun 8 12:49:01 Stavros kernel: [ 21.357262] sd 0:0:0:0: [sda] Attached SCSI disk
Jun 8 12:49:01 Stavros kernel: [ 21.359637] sd 0:0:0:0: Attached scsi generic sg0 type 0
Jun 8 12:49:01 Stavros kernel: [ 21.586363] Attempting manual resume
Jun 8 12:49:01 Stavros kernel: [ 21.620247] kjournald starting. Commit interval 5 seconds
Jun 8 12:49:01 Stavros kernel: [ 21.620265] EXT3-fs: mounted filesystem with ordered data mode.
Jun 8 12:49:01 Stavros kernel: [ 21.916330] eth0: Tigon3 [partno(none) rev b002 PHY(5787)] (PCI Express) 10/100/1000Base-T Ethernet 00:1b:38:d6:a7:72
Jun 8 12:49:01 Stavros kernel: [ 21.916335] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] WireSpeed[1] TSOcap[1]
Jun 8 12:49:01 Stavros kernel: [ 21.916336] eth0: dma_rwctrl[76180000] dma_mask[64-bit]
Jun 8 12:49:01 Stavros kernel: [ 21.916507] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 19 (level, low) -> IRQ 19
Jun 8 12:49:01 Stavros kernel: [ 21.916547] ACPI: PCI interrupt for device 0000:00:1f.1 disabled
Jun 8 12:49:01 Stavros kernel: [ 29.027359] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jun 8 12:49:01 Stavros kernel: [ 29.088042] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Jun 8 12:49:01 Stavros kernel: [ 29.157445] iTCO_vendor_support: vendor-support=0
Jun 8 12:49:01 Stavros kernel: [ 29.172810] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
Jun 8 12:49:01 Stavros kernel: [ 29.284300] input: Power Button (FF) as /devices/virtual/input/input2
Jun 8 12:49:01 Stavros kernel: [ 29.298388] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 19 (level, low) -> IRQ 19
Jun 8 12:49:01 Stavros kernel: [ 29.317142] scsi3 : ata_piix
Jun 8 12:49:01 Stavros kernel: [ 29.329605] scsi4 : ata_piix
Jun 8 12:49:01 Stavros kernel: [ 29.330042] ata4: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x18a0 irq 14
Jun 8 12:49:01 Stavros kernel: [ 29.330044] ata5: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x18a8 irq 15
Jun 8 12:49:01 Stavros kernel: [ 29.334139] ACPI: Power Button (FF) [PWRF]
Jun 8 12:49:01 Stavros kernel: [ 29.334184] input: Lid Switch as /devices/virtual/input/input3
Jun 8 12:49:01 Stavros kernel: [ 29.366128] ACPI: Lid Switch [LID0]
Jun 8 12:49:01 Stavros kernel: [ 29.366172] input: Power Button (CM) as /devices/virtual/input/input4
Jun 8 12:49:01 Stavros kernel: [ 29.433948] ACPI: Power Button (CM) [PWRB]
Jun 8 12:49:01 Stavros kernel: [ 29.434031] ACPI: WMI-Acer: Mapper loaded
Jun 8 12:49:01 Stavros kernel: [ 29.436353] ACPI: EC: non-query interrupt received, switching to interrupt mode
Jun 8 12:49:01 Stavros kernel: [ 29.453365] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:02/LNXVIDEO:00/input/input5
Jun 8 12:49:01 Stavros kernel: [ 29.493858] ACPI: Video Device [VGA] (multi-head: yes rom: no post: no)
Jun 8 12:49:01 Stavros kernel: [ 29.516392] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:01/input/input6
Jun 8 12:49:01 Stavros kernel: [ 29.573704] ACPI: Video Device [GFX0] (multi-head: yes rom: no post: no)
Jun 8 12:49:01 Stavros kernel: [ 29.593030] ACPI: Battery Slot [BAT1] (battery present)
Jun 8 12:49:01 Stavros kernel: [ 29.595808] ACPI: AC Adapter [ACAD] (on-line)
Jun 8 12:49:01 Stavros kernel: [ 29.649029] ata4.00: ATAPI: MATSHITADVD-RAM UJ-850S, 1.60, max UDMA/33
Jun 8 12:49:01 Stavros kernel: [ 29.820547] ata4.00: configured for UDMA/33
Jun 8 12:49:01 Stavros kernel: [ 29.989091] scsi 3:0:0:0: CD-ROM MATSHITA DVD-RAM UJ-850S 1.60 PQ: 0 ANSI: 5
Jun 8 12:49:01 Stavros kernel: [ 29.989157] scsi 3:0:0:0: Attached scsi generic sg1 type 5
Jun 8 12:49:01 Stavros kernel: [ 30.045290] nvidia: module license 'NVIDIA' taints kernel.
Jun 8 12:49:01 Stavros kernel: [ 30.326357] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
Jun 8 12:49:01 Stavros kernel: [ 30.326458] NVRM: loading NVIDIA UNIX x86_64 Kernel Module 169.12 Thu Feb 14 17:51:09 PST 2008
Jun 8 12:49:01 Stavros kernel: [ 30.358254] Linux video capture interface: v2.00
Jun 8 12:49:01 Stavros kernel: [ 30.415676] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 20 (level, low) -> IRQ 20
Jun 8 12:49:01 Stavros kernel: [ 30.441004] uvcvideo: Found UVC 1.00 device USB 2.0 Camera (04f2:b01
Jun 8 12:49:01 Stavros kernel: [ 30.442982] usbcore: registered new interface driver uvcvideo
Jun 8 12:49:01 Stavros kernel: [ 30.442985] USB Video Class driver (v0.1.0)
Jun 8 12:49:01 Stavros kernel: [ 30.464048] sdhci: Secure Digital Host Controller Interface driver
Jun 8 12:49:01 Stavros kernel: [ 30.464050] sdhci: Copyright(c) Pierre Ossman
Jun 8 12:49:01 Stavros kernel: [ 30.479783] iwl4965: Intel(R) Wireless WiFi Link 4965AGN driver for Linux, 1.2.25
Jun 8 12:49:01 Stavros kernel: [ 30.479786] iwl4965: Copyright(c) 2003-2007 Intel Corporation
Jun 8 12:49:01 Stavros kernel: [ 30.527673] sdhci: SDHCI controller found at 0000:0e:06.1 [1180:0822] (rev 22)
Jun 8 12:49:01 Stavros kernel: [ 30.527698] ACPI: PCI Interrupt 0000:0e:06.1[b] -> GSI 23 (level, low) -> IRQ 23
Jun 8 12:49:01 Stavros kernel: [ 30.528450] sdhci:slot0: Will use DMA mode even though HW doesn't fully claim to support it.
Jun 8 12:49:01 Stavros kernel: [ 30.528516] mmc0: SDHCI at 0xf8100800 irq 23 DMA
Jun 8 12:49:01 Stavros kernel: [ 30.528632] ACPI: PCI Interrupt 0000:0c:00.0[A] -> GSI 17 (level, low) -> IRQ 17
Jun 8 12:49:01 Stavros kernel: [ 30.529364] iwl4965: Detected Intel Wireless WiFi Link 4965AGN
Jun 8 12:49:01 Stavros kernel: [ 30.629792] Driver 'sr' needs updating - please use bus_type methods
Jun 8 12:49:01 Stavros kernel: [ 30.636383] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
Jun 8 12:49:01 Stavros kernel: [ 30.636386] Uniform CD-ROM driver Revision: 3.20
Jun 8 12:49:01 Stavros kernel: [ 30.679146] ACPI: PCI interrupt for device 0000:0c:00.0 disabled
Jun 8 12:49:01 Stavros kernel: [ 30.799254] input: ImPS/2 Logitech Wheel Mouse as /devices/platform/i8042/serio1/input/input7
Jun 8 12:49:01 Stavros kernel: [ 30.807081] iTCO_wdt: Found a ICH8M TCO device (Version=2, TCOBASE=0x1060)
Jun 8 12:49:01 Stavros kernel: [ 30.807132] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
Jun 8 12:49:01 Stavros kernel: [ 30.814320] input: PC Speaker as /devices/platform/pcspkr/input/input8
Jun 8 12:49:01 Stavros kernel: [ 31.463316] lp: driver loaded but no devices found
Jun 8 12:49:01 Stavros kernel: [ 31.557794] Adding 3862296k swap on /dev/sda2. Priority:-1 extents:1 across:3862296k
Jun 8 12:49:01 Stavros kernel: [ 31.803669] EXT3 FS on sda1, internal journal
Jun 8 12:49:01 Stavros kernel: [ 32.260328] kjournald starting. Commit interval 5 seconds
Jun 8 12:49:01 Stavros kernel: [ 32.260657] EXT3 FS on sda3, internal journal
Jun 8 12:49:01 Stavros kernel: [ 32.260663] EXT3-fs: mounted filesystem with ordered data mode.
Jun 8 12:49:01 Stavros kernel: [ 32.554341] ip_tables: (C) 2000-2006 Netfilter Core Team
Jun 8 12:49:01 Stavros kernel: [ 32.902777] No dock devices found.
Jun 8 12:49:02 Stavros kernel: [ 33.825989] ppdev: user-space parallel port driver
Jun 8 12:49:02 Stavros kernel: [ 34.007822] audit(1212947342.620:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5133 profile="/usr/sbin/cupsd" namespace="default"
Jun 8 12:49:02 Stavros dhcdbd: Started up.
Jun 8 12:49:03 Stavros kernel: [ 34.920828] ACPI: PCI Interrupt 0000:0c:00.0[A] -> GSI 17 (level, low) -> IRQ 17
Jun 8 12:49:03 Stavros kernel: [ 35.182596] iwl4965: Tunable channels: 11 802.11bg, 13 802.11a channels
Jun 8 12:49:03 Stavros kernel: [ 35.187720] Registered led device: iwl-phy0:RX
Jun 8 12:49:03 Stavros kernel: [ 35.187733] Registered led device: iwl-phy0:TX
Jun 8 12:49:05 Stavros dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Jun 8 12:49:22 Stavros kernel: [ 45.354355] NET: Registered protocol family 10
Jun 8 12:49:22 Stavros kernel: [ 45.354990] lo: Disabled Privacy Extensions
Jun 8 12:49:22 Stavros kernel: [ 45.356025] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jun 8 12:49:22 Stavros kernel: [ 45.357084] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun 8 12:49:35 Stavros dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.reason
Jun 8 12:49:37 Stavros kernel: [ 59.603960] NET: Registered protocol family 17
Jun 8 12:56:44 Stavros kernel: [ 145.807152] ip6_tables: (C) 2000-2006 Netfilter Core Team
Jun 8 12:56:45 Stavros exiting on signal 15
Jun 8 22:08:31 Stavros syslogd 1.5.0#1ubuntu1: restart.
Jun 8 22:08:31 Stavros kernel: Inspecting /boot/System.map-2.6.24-18-generic
Jun 8 22:08:32 Stavros kernel: Loaded 28488 symbols from /boot/System.map-2.6.24-18-generic.
Jun 8 22:08:32 Stavros kernel: Symbols match kernel version 2.6.24.
Jun 8 22:08:32 Stavros kernel: Loaded 35069 symbols from 94 modules.
Jun 8 22:08:32 Stavros kernel: [ 0.000000] Initializing cgroup subsys cpuset
Jun 8 22:08:32 Stavros kernel: [ 0.000000] Initializing cgroup subsys cpu
Jun 8 22:08:32 Stavros kernel: [ 0.000000] Linux version 2.6.24-18-generic (buildd@king) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed May 28 19:28:38 UTC 2008 (Ubuntu 2.6.24-18.32-generic)
Jun 8 22:08:32 Stavros kernel: [ 0.000000] Command line: root=UUID=6c814527-5db0-4129-b3bc-f41a16213147 ro quiet splash
Jun 8 22:08:32 Stavros kernel: [ 0.000000] BIOS-provided physical RAM map:
Jun 8 22:08:32 Stavros kernel: [ 0.000000] BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
Jun 8 22:08:32 Stavros kernel: [ 0.000000] BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
Jun 8 22:08:32 Stavros kernel: [ 0.000000] BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
Jun 8 22:08:32 Stavros kernel: [ 0.000000] BIOS-e820: 0000000000100000 - 00000000bfed0000 (usable)
Jun 8 22:08:32 Stavros kernel: [ 0.000000] BIOS-e820: 00000000bfed0000 - 00000000bfee3000 (ACPI NVS)
Jun 8 22:08:32 Stavros kernel: [ 0.000000] BIOS-e820: 00000000bfee3000 - 00000000c0000000 (reserved)
Jun 8 22:08:32 Stavros kernel: [ 0.000000] BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
Jun 8 22:08:32 Stavros kernel: [ 0.000000] BIOS-e820: 00000000fed00000 - 00000000fed00400 (reserved)
Jun 8 22:08:32 Stavros kernel: [ 0.000000] BIOS-e820: 00000000fed14000 - 00000000fed1a000 (reserved)
Jun 8 22:08:32 Stavros kernel: [ 0.000000] BIOS-e820: 00000000fed1c000 - 00000000fed90000 (reserved)
Jun 8 22:08:32 Stavros kernel: [ 0.000000] BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Jun 8 22:08:32 Stavros kernel: [ 0.000000] BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
Jun 8 22:08:32 Stavros kernel: [ 0.000000] BIOS-e820: 0000000100000000 - 0000000140000000 (usable)
Jun 8 22:08:32 Stavros kernel: [ 0.000000] end_pfn_map = 1310720
Jun 8 22:08:32 Stavros kernel: [ 0.000000] DMI present.
Jun 8 22:08:32 Stavros kernel: [ 0.000000] ACPI: RSDP signature @ 0xFFFF8100000F7B40 checksum 0
Jun 8 22:08:32 Stavros kernel: [ 0.000000] ACPI: RSDP 000F7B40, 0024 (r2 Compal)
Jun 8 22:08:32 Stavros kernel: [ 0.000000] ACPI: XSDT BFED8622, 008C (r1 Compal CRESTLNE 6040000 LTP 0)
Jun 8 22:08:32 Stavros kernel: [ 0.000000] ACPI: FACP BFEDFBD2, 00F4 (r3 INTEL CRESTLNE 6040000 ALAN 1)
Jun 8 22:08:32 Stavros kernel: [ 0.000000] ACPI: DSDT BFED9B51, 600D (r2 Compal CRESTLNE 6040000 INTL 20061109)
Jun 8 22:08:32 Stavros kernel: [ 0.000000] ACPI: FACS BFEE2FC0, 0040
Jun 8 22:08:32 Stavros kernel: [ 0.000000] ACPI: APIC BFEDFCC6, 0068 (r1 INTEL CRESTLNE 6040000 LOHR 5A)
Jun 8 22:08:32 Stavros kernel: [ 0.000000] ACPI: HPET BFEDFD2E, 0038 (r1 Compal CRESTLNE 6040000 LOHR 5A)
Jun 8 22:08:32 Stavros kernel: [ 0.000000] ACPI: MCFG BFEDFD66, 003C (r1 INTEL CRESTLNE 6040000 LOHR 5A)
Jun 8 22:08:32 Stavros kernel: [ 0.000000] ACPI: TCPA BFEDFDA2, 0032 (r1 Intel CRESTLNE 6040000 LOHR 5A)
Jun 8 22:08:32 Stavros kernel: [ 0.000000] ACPI: TMOR BFEDFDD4, 0026 (r1 PTLTD 6040000 PTL 3)
Jun 8 22:08:32 Stavros kernel: [ 0.000000] ACPI: SLIC BFEDFDFA, 0176 (r1 Compal CRESTLNE 6040000 TBD 1)
Jun 8 22:08:32 Stavros kernel: [ 0.000000] ACPI: APIC BFEDFF70, 0068 (r1 PTLTD ^I APIC 6040000 LTP 0)
Jun 8 22:08:32 Stavros kernel: [ 0.000000] ACPI: BOOT BFEDFFD8, 0028 (r1 PTLTD $SBFTBL$ 6040000 LTP 1)
Jun 8 22:08:32 Stavros kernel: [ 0.000000] ACPI: SSDT BFED988C, 02C5 (r1 SataRe SataAhci 1000 INTL 20050624)
Jun 8 22:08:32 Stavros kernel: [ 0.000000] ACPI: SSDT BFED8C3A, 025F (r1 PmRef Cpu0Tst 3000 INTL 20050624)
Jun 8 22:08:32 Stavros kernel: [ 0.000000] ACPI: SSDT BFED8B94, 00A6 (r1 PmRef Cpu1Tst 3000 INTL 20050624)
Jun 8 22:08:32 Stavros kernel: [ 0.000000] ACPI: SSDT BFED86AE, 04E6 (r1 PmRef CpuPm 3000 INTL 20050624)
Jun 8 22:08:32 Stavros kernel: [ 0.000000] ACPI: BIOS bug: multiple APIC/MADT found, using 0
Jun 8 22:08:32 Stavros kernel: [ 0.000000] ACPI: If "acpi_apic_instance=2" works better, notify [email]linux-acpi@vger.kernel.org[/email]
Jun 8 22:08:32 Stavros kernel: [ 0.000000] ACPI: DMI detected: Compal
Jun 8 22:08:32 Stavros kernel: [ 0.000000] No NUMA configuration found
Jun 8 22:08:32 Stavros kernel: [ 0.000000] Faking a node at 0000000000000000-0000000140000000
Jun 8 22:08:32 Stavros kernel: [ 0.000000] Bootmem setup node 0 0000000000000000-0000000140000000
Jun 8 22:08:32 Stavros kernel: [ 0.000000] Zone PFN ranges:
Jun 8 22:08:32 Stavros kernel: [ 0.000000] DMA 0 -> 4096
Jun 8 22:08:32 Stavros kernel: [ 0.000000] DMA32 4096 -> 1048576
Jun 8 22:08:32 Stavros kernel: [ 0.000000] Normal 1048576 -> 1310720
Jun 8 22:08:32 Stavros kernel: [ 0.000000] Movable zone start PFN for each node
Jun 8 22:08:32 Stavros kernel: [ 0.000000] early_node_map[3] active PFN ranges
Jun 8 22:08:32 Stavros kernel: [ 0.000000] 0: 0 -> 159
Jun 8 22:08:32 Stavros kernel: [ 0.000000] 0: 256 -> 786128
Jun 8 22:08:32 Stavros kernel: [ 0.000000] 0: 1048576 -> 1310720

---

### Post by jdb on 2008-06-22
I compared your log (the first boot in it) to mine & this is what I found.

Both our computers take a little more than 20 seconds to get from "restart" to "NET: Registered protocol family 10".

After that mine takes about another 10 seconds to come up but yours takes almost another 11 minutes to come up.

Our messages during that time look about the same but I have one saying wlan0 becomes ready that you don't have.
Also, yours has long pauses between the handler not found messages.

Here are the relevent messages, first mine then yours:

Jun 22 19:38:54 dads kernel: [   55.727242] NET: Registered protocol family 10
Jun 22 19:38:54 dads kernel: [   55.727745] lo: Disabled Privacy Extensions
Jun 22 19:38:54 dads kernel: [   55.728587] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jun 22 19:38:54 dads kernel: [   55.729517] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun 22 19:38:55 dads kernel: [   56.814302] NET: Registered protocol family 17
Jun 22 19:38:57 dads kernel: [   57.998050] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Jun 22 19:39:05 dads dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.host_name
Jun 22 19:39:05 dads dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.nis_domain
Jun 22 19:39:05 dads dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.nis_servers
Jun 22 19:39:05 dads dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.interface_mtu


Jun 8 12:36:08 Stavros kernel: [ 45.807881] NET: Registered protocol family 10
Jun 8 12:36:08 Stavros kernel: [ 45.808324] lo: Disabled Privacy Extensions
Jun 8 12:36:08 Stavros kernel: [ 45.809623] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jun 8 12:36:08 Stavros kernel: [ 45.810720] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun 8 12:36:20 Stavros dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.reason
Jun 8 12:36:22 Stavros kernel: [ 59.798572] NET: Registered protocol family 17
Jun 8 12:40:14 Stavros dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.reason
Jun 8 12:44:51 Stavros dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.reason
Jun 8 12:46:48 Stavros dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.reason

I don't know what would be causing this, but it sure seems to have something to do with networking.

If you look in the syslog in the same timestamp range as the "handler not found messages" you might get some more information.

jdb

---

### Post by thomasaaron on 2008-06-23
Try this... It has worked in the past on slow booting issues.

To fix your /etc/network/interfaces file, go to a terminal
(Application > Accessories > Terminal) and enter the following command:

sudo gedit /etc/network/interfaces

This will launch a text editor with the interfaces file opened in it.

In this file, put a comment (#) in front of EVERY line of the file
EXCEPT for these two lines:

auto lo
iface lo inet loopback

Click SAVE on the text editor and reboot your computer.
It should now boot faster and connect to networks more easily.

NOTE:
Unless you are dealing with static IP addresses (which is pretty rare for the
general end-user) you should NOT establish a network connection by going to
System > Administration > Network.

Instead, you should connect to the Internet using the Network Manager icon
in the upper right corner of your screen (the one that looks like a little
computer monitor).

---

