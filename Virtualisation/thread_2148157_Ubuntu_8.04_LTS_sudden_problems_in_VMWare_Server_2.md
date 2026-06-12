---
title: "Ubuntu 8.04 LTS sudden problems in VMWare Server 2 environment"
date: 2013-05-24
forum: Virtualisation
---

### Post by beowulf222 on 2013-05-24
Hello,

I am running Ubuntu 8.04 LTS on a VMWare Server 2 (Windows 2008 Server is the host's OS), and in the last few days I noticed lengthy Kernel messages. What triggered me to look at the Kernel messages was that the vServer was unreachable for lengthy periods of times while the ISP assured me that no network problems caused this.

I am running this Kernel
Linux beowulf.fastcomp.at 2.6.24-32-server #1 SMP Mon Dec 3 15:56:05 UTC 2012 i686

Here is the dmesg output
```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-32-server (buildd@lamiak) (gcc version 4.2.4 (Ubuntu 4.2.4-1ubuntu3)) #1 SMP Mon Dec 3 15:56:05 UTC 2012 (Ubuntu 2.6.24-32.107-server)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000ca000 - 00000000000cc000 (reserved)
[    0.000000]  BIOS-e820: 00000000000dc000 - 00000000000e0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001fef0000 (usable)
[    0.000000]  BIOS-e820: 000000001fef0000 - 000000001feff000 (ACPI data)
[    0.000000]  BIOS-e820: 000000001feff000 - 000000001ff00000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000001ff00000 - 0000000020000000 (usable)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fffe0000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 512MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f6aa0
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] Entering add_active_range(0, 0, 131072) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   131072
[    0.000000]   HighMem    131072 ->   131072
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   131072
[    0.000000] On node 0 totalpages: 131072
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 992 pages used for memmap
[    0.000000]   Normal zone: 125984 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP signature @ 0xC00F6A30 checksum 0
[    0.000000] ACPI: RSDP 000F6A30, 0024 (r2 PTLTD )
[    0.000000] ACPI: XSDT 1FEF0780, 004C (r1 INTEL  440BX     6040000 VMW   1324272)
[    0.000000] ACPI: FACP 1FEFEE98, 00F4 (r4 INTEL  440BX     6040000 PTL     F4240)
[    0.000000] ACPI: DSDT 1FEF0938, E560 (r1 PTLTD  Custom    6040000 MSFT  3000001)
[    0.000000] ACPI: FACS 1FEFFFC0, 0040
[    0.000000] ACPI: BOOT 1FEF0910, 0028 (r1 PTLTD  $SBFTBL$  6040000  LTP        1)
[    0.000000] ACPI: APIC 1FEF08C0, 0050 (r1 PTLTD  	 APIC    6040000  LTP        0)
[    0.000000] ACPI: MCFG 1FEF0884, 003C (r1 PTLTD  $PCITBL$  6040000  LTP        1)
[    0.000000] ACPI: SRAT 1FEF0804, 0080 (r2 VMWARE MEMPLUG   6040000 VMW         1)
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 7:7 APIC version 17
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 17, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:c0000000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000ca000
[    0.000000] swsusp: Registered nosave memory region: 00000000000ca000 - 00000000000cc000
[    0.000000] swsusp: Registered nosave memory region: 00000000000cc000 - 00000000000dc000
[    0.000000] swsusp: Registered nosave memory region: 00000000000dc000 - 00000000000e0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000e0000 - 00000000000e4000
[    0.000000] swsusp: Registered nosave memory region: 00000000000e4000 - 0000000000100000
[    0.000000] swsusp: Registered nosave memory region: 000000001fef0000 - 000000001feff000
[    0.000000] swsusp: Registered nosave memory region: 000000001feff000 - 000000001ff00000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 130048
[    0.000000] Kernel command line: root=/dev/mapper/beowulf-root ro quiet splash
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] TSC: Frequency read from the hypervisor
[    0.000000] Detected 2833.000 MHz processor.
[38628.082684] Console: colour VGA+ 80x25
[38628.082686] console [tty0] enabled
[38628.082836] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[38628.082950] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[38628.086896] Memory: 506976k/524288k available (2262k kernel code, 16692k reserved, 1037k data, 384k init, 0k highmem)
[38628.086900] virtual kernel memory layout:
[38628.086901]     fixmap  : 0xfff4c000 - 0xfffff000   ( 716 kB)
[38628.086901]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
[38628.086902]     vmalloc : 0xe0800000 - 0xffbfe000   ( 499 MB)
[38628.086903]     lowmem  : 0xc0000000 - 0xe0000000   ( 512 MB)
[38628.086903]       .init : 0xc0440000 - 0xc04a0000   ( 384 kB)
[38628.086904]       .data : 0xc03359db - 0xc0438fe4   (1037 kB)
[38628.086904]       .text : 0xc0100000 - 0xc03359db   (2262 kB)
[38628.086906] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[38628.086959] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[38628.088111] Calibrating delay loop (skipped), using tsc calculated value.. 5666.00 BogoMIPS (lpj=28330000)
[38628.088152] Security Framework initialized
[38628.088160] SELinux:  Disabled at boot.
[38628.088182] AppArmor: AppArmor initialized
[38628.088184] Failure registering capabilities with primary security module.
[38628.088193] Mount-cache hash table entries: 512
[38628.088386] Initializing cgroup subsys ns
[38628.088396] Initializing cgroup subsys cpuacct
[38628.088416] CPU: After generic identify, caps: 0febfbff 20100000 00000000 00000000 80082201 00000000 00000001 00000000
[38628.088429] CPU: L1 I cache: 32K, L1 D cache: 32K
[38628.088430] CPU: L2 cache: 6144K
[38628.088437] CPU: After all inits, caps: 0febfbff 20100000 00000000 00843940 80082201 00000000 00000001 00000000
[38628.088447] Compat vDSO mapped to ffffe000.
[38628.088495] Checking 'hlt' instruction... OK.
[38628.130054] SMP alternatives: switching to UP code
[38628.135352] Freeing SMP alternatives: 12k freed
[38628.135454] Early unpacking initramfs... done
[38628.374086] ACPI: Core revision 20070126
[38628.374198] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[38628.380588] CPU0: Intel(R) Core(TM)2 Quad CPU    Q9550  @ 2.83GHz stepping 0a
[38628.381029] Total of 1 processors activated (5666.00 BogoMIPS).
[38628.381450] ENABLING IO-APIC IRQs
[38628.381741] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[38628.597890] Brought up 1 CPUs
[38628.597971] CPU0 attaching sched-domain:
[38628.597977]  domain 0: span 01
[38628.597978]   groups: 01
[38628.598322] net_namespace: 64 bytes
[38628.598344] Booting paravirtualized kernel on bare hardware
[38628.598768] Time:  0:48:27  Date: 05/24/13
[38628.598812] NET: Registered protocol family 16
[38628.599115] EISA bus registered
[38628.599127] ACPI: bus type pci registered
[38628.599308] PCI: PCI BIOS revision 2.10 entry at 0xfd8a0, last bus=34
[38628.599309] PCI: Using configuration type 1
[38628.599325] Setting up standard PCI resources
[38628.619742] ACPI: EC: Look up EC in DSDT
[38628.659027] ACPI: BIOS _OSI(Linux) query ignored
[38628.659042] ACPI: DMI System Vendor: VMware, Inc.
[38628.659043] ACPI: DMI Product Name: VMware Virtual Platform
[38628.659044] ACPI: DMI Product Version: None
[38628.659045] ACPI: DMI Board Name: 440BX Desktop Reference Platform
[38628.659046] ACPI: DMI BIOS Vendor: Phoenix Technologies LTD
[38628.659047] ACPI: DMI BIOS Date: 07/29/2008
[38628.659048] ACPI: Please send DMI info above to linux-acpi@vger.kernel.org
[38628.659049] ACPI: If "acpi_osi=Linux" works better, please notify linux-acpi@vger.kernel.org
[38628.659557] ACPI: Interpreter enabled
[38628.659565] ACPI: (supports S0 S1 S4 S5)
[38628.659584] ACPI: Using IOAPIC for interrupt routing
[38628.707329] ACPI: PCI Root Bridge [PCI0] (0000:00)
[38628.709044] PCI quirk: region 1000-103f claimed by PIIX4 ACPI
[38628.709055] PCI quirk: region 1040-104f claimed by PIIX4 SMB
[38628.720982] PCI: Transparent bridge - 0000:00:11.0
[38628.737236] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[38628.940889] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *9 10 11 14 15)
[38628.941052] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 *11 14 15)
[38628.941202] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 *10 11 14 15)
[38628.941351] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 11 14 15) *0, disabled.
[38628.941509] Linux Plug and Play Support v0.97 (c) Adam Belay
[38628.941544] pnp: PnP ACPI init
[38628.941552] ACPI: bus type pnp registered
[38628.999572] pnp: PnP ACPI: found 13 devices
[38628.999577] ACPI: ACPI bus type pnp unregistered
[38628.999589] PnPBIOS: Disabled by ACPI PNP
[38628.999878] PCI: Using ACPI for IRQ routing
[38628.999880] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[38629.275813] NET: Registered protocol family 8
[38629.275816] NET: Registered protocol family 20
[38629.275839] NetLabel: Initializing
[38629.275842] NetLabel:  domain hash size = 128
[38629.275843] NetLabel:  protocols = UNLABELED CIPSOv4
[38629.275854] NetLabel:  unlabeled traffic allowed by default
[38629.275926] AppArmor: AppArmor Filesystem Enabled
[38629.285763] Time: tsc clocksource has been installed.
[38629.285786] Switched to high resolution mode on CPU 0
[38629.306227] system 00:01: ioport range 0x1000-0x103f has been reserved
[38629.306229] system 00:01: ioport range 0x1040-0x104f has been reserved
[38629.306236] system 00:0c: ioport range 0x1060-0x107f has been reserved
[38629.306242] system 00:0c: iomem range 0xe0000000-0xefffffff could not be reserved
[38629.306244] system 00:0c: iomem range 0xdb400000-0xdb5fffff has been reserved
[38629.337149] PCI: Bridge: 0000:00:01.0
[38629.337151]   IO window: disabled.
[38629.337184]   MEM window: disabled.
[38629.337203]   PREFETCH window: disabled.
[38629.337232] PCI: Bridge: 0000:00:11.0
[38629.337242]   IO window: 2000-3fff
[38629.337269]   MEM window: d8900000-d92fffff
[38629.337288]   PREFETCH window: db600000-dbafffff
[38629.337315] PCI: Bridge: 0000:00:15.0
[38629.337325]   IO window: 4000-4fff
[38629.337352]   MEM window: d9300000-d93fffff
[38629.337370]   PREFETCH window: dbb00000-dbbfffff
[38629.337436] PCI: Bridge: 0000:00:15.1
[38629.337447]   IO window: 8000-8fff
[38629.337473]   MEM window: d9700000-d97fffff
[38629.337492]   PREFETCH window: dbf00000-dbffffff
[38629.337532] PCI: Bridge: 0000:00:15.2
[38629.337543]   IO window: c000-cfff
[38629.337570]   MEM window: d9b00000-d9bfffff
[38629.337588]   PREFETCH window: dc300000-dc3fffff
[38629.337633] PCI: Bridge: 0000:00:15.3
[38629.337635]   IO window: disabled.
[38629.337662]   MEM window: d9f00000-d9ffffff
[38629.337681]   PREFETCH window: dc700000-dc7fffff
[38629.337720] PCI: Bridge: 0000:00:15.4
[38629.337722]   IO window: disabled.
[38629.337749]   MEM window: da300000-da3fffff
[38629.337768]   PREFETCH window: dcb00000-dcbfffff
[38629.337807] PCI: Bridge: 0000:00:15.5
[38629.337809]   IO window: disabled.
[38629.337839]   MEM window: da700000-da7fffff
[38629.337858]   PREFETCH window: dcf00000-dcffffff
[38629.337897] PCI: Bridge: 0000:00:15.6
[38629.337899]   IO window: disabled.
[38629.337926]   MEM window: dab00000-dabfffff
[38629.337944]   PREFETCH window: dd300000-dd3fffff
[38629.337984] PCI: Bridge: 0000:00:15.7
[38629.337985]   IO window: disabled.
[38629.338012]   MEM window: daf00000-daffffff
[38629.338031]   PREFETCH window: dd700000-dd7fffff
[38629.338070] PCI: Bridge: 0000:00:16.0
[38629.338081]   IO window: 5000-5fff
[38629.338108]   MEM window: d9400000-d94fffff
[38629.338126]   PREFETCH window: dbc00000-dbcfffff
[38629.338165] PCI: Bridge: 0000:00:16.1
[38629.338181]   IO window: 9000-9fff
[38629.338208]   MEM window: d9800000-d98fffff
[38629.338226]   PREFETCH window: dc000000-dc0fffff
[38629.338265] PCI: Bridge: 0000:00:16.2
[38629.338276]   IO window: d000-dfff
[38629.338303]   MEM window: d9c00000-d9cfffff
[38629.338322]   PREFETCH window: dc400000-dc4fffff
[38629.338361] PCI: Bridge: 0000:00:16.3
[38629.338362]   IO window: disabled.
[38629.338390]   MEM window: da000000-da0fffff
[38629.338408]   PREFETCH window: dc800000-dc8fffff
[38629.338447] PCI: Bridge: 0000:00:16.4
[38629.338449]   IO window: disabled.
[38629.338476]   MEM window: da400000-da4fffff
[38629.338495]   PREFETCH window: dcc00000-dccfffff
[38629.338534] PCI: Bridge: 0000:00:16.5
[38629.338535]   IO window: disabled.
[38629.338563]   MEM window: da800000-da8fffff
[38629.338581]   PREFETCH window: dd000000-dd0fffff
[38629.338620] PCI: Bridge: 0000:00:16.6
[38629.338622]   IO window: disabled.
[38629.338649]   MEM window: dac00000-dacfffff
[38629.338667]   PREFETCH window: dd400000-dd4fffff
[38629.338707] PCI: Bridge: 0000:00:16.7
[38629.338709]   IO window: disabled.
[38629.338736]   MEM window: db000000-db0fffff
[38629.338754]   PREFETCH window: dd800000-dd8fffff
[38629.338793] PCI: Bridge: 0000:00:17.0
[38629.338804]   IO window: 6000-6fff
[38629.338831]   MEM window: d9500000-d95fffff
[38629.338849]   PREFETCH window: dbd00000-dbdfffff
[38629.338888] PCI: Bridge: 0000:00:17.1
[38629.338899]   IO window: a000-afff
[38629.338926]   MEM window: d9900000-d99fffff
[38629.338945]   PREFETCH window: dc100000-dc1fffff
[38629.338984] PCI: Bridge: 0000:00:17.2
[38629.338994]   IO window: e000-efff
[38629.339021]   MEM window: d9d00000-d9dfffff
[38629.339040]   PREFETCH window: dc500000-dc5fffff
[38629.339079] PCI: Bridge: 0000:00:17.3
[38629.339081]   IO window: disabled.
[38629.339108]   MEM window: da100000-da1fffff
[38629.339126]   PREFETCH window: dc900000-dc9fffff
[38629.339165] PCI: Bridge: 0000:00:17.4
[38629.339167]   IO window: disabled.
[38629.339195]   MEM window: da500000-da5fffff
[38629.339213]   PREFETCH window: dcd00000-dcdfffff
[38629.339252] PCI: Bridge: 0000:00:17.5
[38629.339254]   IO window: disabled.
[38629.339281]   MEM window: da900000-da9fffff
[38629.339300]   PREFETCH window: dd100000-dd1fffff
[38629.339339] PCI: Bridge: 0000:00:17.6
[38629.339340]   IO window: disabled.
[38629.339367]   MEM window: dad00000-dadfffff
[38629.339386]   PREFETCH window: dd500000-dd5fffff
[38629.339425] PCI: Bridge: 0000:00:17.7
[38629.339427]   IO window: disabled.
[38629.339454]   MEM window: db100000-db1fffff
[38629.339472]   PREFETCH window: dd900000-dd9fffff
[38629.339511] PCI: Bridge: 0000:00:18.0
[38629.339522]   IO window: 7000-7fff
[38629.339549]   MEM window: d9600000-d96fffff
[38629.339568]   PREFETCH window: dbe00000-dbefffff
[38629.339606] PCI: Bridge: 0000:00:18.1
[38629.339617]   IO window: b000-bfff
[38629.339644]   MEM window: d9a00000-d9afffff
[38629.339663]   PREFETCH window: dc200000-dc2fffff
[38629.339702] PCI: Bridge: 0000:00:18.2
[38629.339713]   IO window: f000-ffff
[38629.339740]   MEM window: d9e00000-d9efffff
[38629.339758]   PREFETCH window: dc600000-dc6fffff
[38629.339800] PCI: Bridge: 0000:00:18.3
[38629.339802]   IO window: disabled.
[38629.339829]   MEM window: da200000-da2fffff
[38629.339848]   PREFETCH window: dca00000-dcafffff
[38629.339887] PCI: Bridge: 0000:00:18.4
[38629.339889]   IO window: disabled.
[38629.339916]   MEM window: da600000-da6fffff
[38629.339934]   PREFETCH window: dce00000-dcefffff
[38629.339973] PCI: Bridge: 0000:00:18.5
[38629.339975]   IO window: disabled.
[38629.340003]   MEM window: daa00000-daafffff
[38629.340022]   PREFETCH window: dd200000-dd2fffff
[38629.340061] PCI: Bridge: 0000:00:18.6
[38629.340063]   IO window: disabled.
[38629.340090]   MEM window: dae00000-daefffff
[38629.340108]   PREFETCH window: dd600000-dd6fffff
[38629.340147] PCI: Bridge: 0000:00:18.7
[38629.340149]   IO window: disabled.
[38629.340181]   MEM window: db200000-db2fffff
[38629.340200]   PREFETCH window: dda00000-ddafffff
[38629.340285] PCI: Setting latency timer of device 0000:00:01.0 to 64
[38629.340450] PCI: Setting latency timer of device 0000:00:15.0 to 64
[38629.340553] PCI: Setting latency timer of device 0000:00:15.1 to 64
[38629.340655] PCI: Setting latency timer of device 0000:00:15.2 to 64
[38629.340762] PCI: Setting latency timer of device 0000:00:15.3 to 64
[38629.340865] PCI: Setting latency timer of device 0000:00:15.4 to 64
[38629.340967] PCI: Setting latency timer of device 0000:00:15.5 to 64
[38629.341069] PCI: Setting latency timer of device 0000:00:15.6 to 64
[38629.341176] PCI: Setting latency timer of device 0000:00:15.7 to 64
[38629.341279] PCI: Setting latency timer of device 0000:00:16.0 to 64
[38629.341381] PCI: Setting latency timer of device 0000:00:16.1 to 64
[38629.341483] PCI: Setting latency timer of device 0000:00:16.2 to 64
[38629.341585] PCI: Setting latency timer of device 0000:00:16.3 to 64
[38629.341694] PCI: Setting latency timer of device 0000:00:16.4 to 64
[38629.341796] PCI: Setting latency timer of device 0000:00:16.5 to 64
[38629.341899] PCI: Setting latency timer of device 0000:00:16.6 to 64
[38629.342001] PCI: Setting latency timer of device 0000:00:16.7 to 64
[38629.342103] PCI: Setting latency timer of device 0000:00:17.0 to 64
[38629.342210] PCI: Setting latency timer of device 0000:00:17.1 to 64
[38629.342314] PCI: Setting latency timer of device 0000:00:17.2 to 64
[38629.342416] PCI: Setting latency timer of device 0000:00:17.3 to 64
[38629.342518] PCI: Setting latency timer of device 0000:00:17.4 to 64
[38629.342620] PCI: Setting latency timer of device 0000:00:17.5 to 64
[38629.342723] PCI: Setting latency timer of device 0000:00:17.6 to 64
[38629.342826] PCI: Setting latency timer of device 0000:00:17.7 to 64
[38629.342928] PCI: Setting latency timer of device 0000:00:18.0 to 64
[38629.343030] PCI: Setting latency timer of device 0000:00:18.1 to 64
[38629.343133] PCI: Setting latency timer of device 0000:00:18.2 to 64
[38629.343240] PCI: Setting latency timer of device 0000:00:18.3 to 64
[38629.343342] PCI: Setting latency timer of device 0000:00:18.4 to 64
[38629.343445] PCI: Setting latency timer of device 0000:00:18.5 to 64
[38629.343547] PCI: Setting latency timer of device 0000:00:18.6 to 64
[38629.343649] PCI: Setting latency timer of device 0000:00:18.7 to 64
[38629.343680] NET: Registered protocol family 2
[38629.435654] IP route cache hash table entries: 16384 (order: 4, 65536 bytes)
[38629.435789] TCP established hash table entries: 65536 (order: 7, 524288 bytes)
[38629.437480] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[38629.439912] TCP: Hash tables configured (established 65536 bind 65536)
[38629.439917] TCP reno registered
[38629.465684] checking if image is initramfs... it is
[38629.767457] Freeing initrd memory: 7884k freed
[38629.767661] Simple Boot Flag at 0x36 set to 0x1
[38629.768414] audit: initializing netlink socket (disabled)
[38629.768430] audit(1369356507.560:1): initialized
[38629.768681] Total HugeTLB memory allocated, 0
[38629.770918] VFS: Disk quotas dquot_6.5.1
[38629.771005] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[38629.771244] io scheduler noop registered
[38629.771246] io scheduler anticipatory registered
[38629.771249] io scheduler deadline registered (default)
[38629.771256] io scheduler cfq registered
[38629.771265] Limiting direct PCI/PCI transfers.
[38629.771287] Boot video device is 0000:00:0f.0
[38629.771519] PCI: Setting latency timer of device 0000:00:15.0 to 64
[38629.771940] assign_interrupt_mode Found MSI capability
[38629.772357] Allocate Port Service[0000:00:15.0:pcie00]
[38629.772398] Allocate Port Service[0000:00:15.0:pcie02]
[38629.772913] PCI: Setting latency timer of device 0000:00:15.1 to 64
[38629.773327] assign_interrupt_mode Found MSI capability
[38629.773728] Allocate Port Service[0000:00:15.1:pcie00]
[38629.773767] Allocate Port Service[0000:00:15.1:pcie02]
[38629.774277] PCI: Setting latency timer of device 0000:00:15.2 to 64
[38629.774695] assign_interrupt_mode Found MSI capability
[38629.775095] Allocate Port Service[0000:00:15.2:pcie00]
[38629.775113] Allocate Port Service[0000:00:15.2:pcie02]
[38629.775503] PCI: Setting latency timer of device 0000:00:15.3 to 64
[38629.775919] assign_interrupt_mode Found MSI capability
[38629.776324] Allocate Port Service[0000:00:15.3:pcie00]
[38629.776370] Allocate Port Service[0000:00:15.3:pcie02]
[38629.776896] PCI: Setting latency timer of device 0000:00:15.4 to 64
[38629.777310] assign_interrupt_mode Found MSI capability
[38629.777710] Allocate Port Service[0000:00:15.4:pcie00]
[38629.777749] Allocate Port Service[0000:00:15.4:pcie02]
[38629.778274] PCI: Setting latency timer of device 0000:00:15.5 to 64
[38629.778688] assign_interrupt_mode Found MSI capability
[38629.779088] Allocate Port Service[0000:00:15.5:pcie00]
[38629.779161] Allocate Port Service[0000:00:15.5:pcie02]
[38629.779668] PCI: Setting latency timer of device 0000:00:15.6 to 64
[38629.780086] assign_interrupt_mode Found MSI capability
[38629.780507] Allocate Port Service[0000:00:15.6:pcie00]
[38629.780542] Allocate Port Service[0000:00:15.6:pcie02]
[38629.781040] PCI: Setting latency timer of device 0000:00:15.7 to 64
[38629.781453] assign_interrupt_mode Found MSI capability
[38629.781852] Allocate Port Service[0000:00:15.7:pcie00]
[38629.781886] Allocate Port Service[0000:00:15.7:pcie02]
[38629.782386] PCI: Setting latency timer of device 0000:00:16.0 to 64
[38629.782806] assign_interrupt_mode Found MSI capability
[38629.783210] Allocate Port Service[0000:00:16.0:pcie00]
[38629.783244] Allocate Port Service[0000:00:16.0:pcie02]
[38629.783747] PCI: Setting latency timer of device 0000:00:16.1 to 64
[38629.784161] assign_interrupt_mode Found MSI capability
[38629.784561] Allocate Port Service[0000:00:16.1:pcie00]
[38629.784595] Allocate Port Service[0000:00:16.1:pcie02]
[38629.785111] PCI: Setting latency timer of device 0000:00:16.2 to 64
[38629.785445] assign_interrupt_mode Found MSI capability
[38629.785845] Allocate Port Service[0000:00:16.2:pcie00]
[38629.785886] Allocate Port Service[0000:00:16.2:pcie02]
[38629.786391] PCI: Setting latency timer of device 0000:00:16.3 to 64
[38629.786805] assign_interrupt_mode Found MSI capability
[38629.787211] Allocate Port Service[0000:00:16.3:pcie00]
[38629.787247] Allocate Port Service[0000:00:16.3:pcie02]
[38629.787753] PCI: Setting latency timer of device 0000:00:16.4 to 64
[38629.788172] assign_interrupt_mode Found MSI capability
[38629.788571] Allocate Port Service[0000:00:16.4:pcie00]
[38629.788607] Allocate Port Service[0000:00:16.4:pcie02]
[38629.789107] PCI: Setting latency timer of device 0000:00:16.5 to 64
[38629.789528] assign_interrupt_mode Found MSI capability
[38629.789928] Allocate Port Service[0000:00:16.5:pcie00]
[38629.789962] Allocate Port Service[0000:00:16.5:pcie02]
[38629.790461] PCI: Setting latency timer of device 0000:00:16.6 to 64
[38629.790884] assign_interrupt_mode Found MSI capability
[38629.791282] Allocate Port Service[0000:00:16.6:pcie00]
[38629.791316] Allocate Port Service[0000:00:16.6:pcie02]
[38629.791828] PCI: Setting latency timer of device 0000:00:16.7 to 64
[38629.792248] assign_interrupt_mode Found MSI capability
[38629.792649] Allocate Port Service[0000:00:16.7:pcie00]
[38629.792684] Allocate Port Service[0000:00:16.7:pcie02]
[38629.793197] PCI: Setting latency timer of device 0000:00:17.0 to 64
[38629.793612] assign_interrupt_mode Found MSI capability
[38629.794013] Allocate Port Service[0000:00:17.0:pcie00]
[38629.794048] Allocate Port Service[0000:00:17.0:pcie02]
[38629.794546] PCI: Setting latency timer of device 0000:00:17.1 to 64
[38629.794964] assign_interrupt_mode Found MSI capability
[38629.795282] Allocate Port Service[0000:00:17.1:pcie00]
[38629.795319] Allocate Port Service[0000:00:17.1:pcie02]
[38629.795824] PCI: Setting latency timer of device 0000:00:17.2 to 64
[38629.796244] assign_interrupt_mode Found MSI capability
[38629.796644] Allocate Port Service[0000:00:17.2:pcie00]
[38629.796685] Allocate Port Service[0000:00:17.2:pcie02]
[38629.797190] PCI: Setting latency timer of device 0000:00:17.3 to 64
[38629.797610] assign_interrupt_mode Found MSI capability
[38629.798010] Allocate Port Service[0000:00:17.3:pcie00]
[38629.798045] Allocate Port Service[0000:00:17.3:pcie02]
[38629.798556] PCI: Setting latency timer of device 0000:00:17.4 to 64
[38629.798971] assign_interrupt_mode Found MSI capability
[38629.799376] Allocate Port Service[0000:00:17.4:pcie00]
[38629.799411] Allocate Port Service[0000:00:17.4:pcie02]
[38629.799916] PCI: Setting latency timer of device 0000:00:17.5 to 64
[38629.800335] assign_interrupt_mode Found MSI capability
[38629.800736] Allocate Port Service[0000:00:17.5:pcie00]
[38629.800772] Allocate Port Service[0000:00:17.5:pcie02]
[38629.801278] PCI: Setting latency timer of device 0000:00:17.6 to 64
[38629.801697] assign_interrupt_mode Found MSI capability
[38629.802096] Allocate Port Service[0000:00:17.6:pcie00]
[38629.802131] Allocate Port Service[0000:00:17.6:pcie02]
[38629.802637] PCI: Setting latency timer of device 0000:00:17.7 to 64
[38629.803058] assign_interrupt_mode Found MSI capability
[38629.803458] Allocate Port Service[0000:00:17.7:pcie00]
[38629.803495] Allocate Port Service[0000:00:17.7:pcie02]
[38629.804004] PCI: Setting latency timer of device 0000:00:18.0 to 64
[38629.804423] assign_interrupt_mode Found MSI capability
[38629.804827] Allocate Port Service[0000:00:18.0:pcie00]
[38629.804862] Allocate Port Service[0000:00:18.0:pcie02]
[38629.805283] PCI: Setting latency timer of device 0000:00:18.1 to 64
[38629.805702] assign_interrupt_mode Found MSI capability
[38629.806105] Allocate Port Service[0000:00:18.1:pcie00]
[38629.806269] Allocate Port Service[0000:00:18.1:pcie02]
[38629.806772] PCI: Setting latency timer of device 0000:00:18.2 to 64
[38629.807190] assign_interrupt_mode Found MSI capability
[38629.807590] Allocate Port Service[0000:00:18.2:pcie00]
[38629.807625] Allocate Port Service[0000:00:18.2:pcie02]
[38629.808128] PCI: Setting latency timer of device 0000:00:18.3 to 64
[38629.808546] assign_interrupt_mode Found MSI capability
[38629.808944] Allocate Port Service[0000:00:18.3:pcie00]
[38629.808978] Allocate Port Service[0000:00:18.3:pcie02]
[38629.809482] PCI: Setting latency timer of device 0000:00:18.4 to 64
[38629.809901] assign_interrupt_mode Found MSI capability
[38629.810305] Allocate Port Service[0000:00:18.4:pcie00]
[38629.810339] Allocate Port Service[0000:00:18.4:pcie02]
[38629.810840] PCI: Setting latency timer of device 0000:00:18.5 to 64
[38629.811259] assign_interrupt_mode Found MSI capability
[38629.811660] Allocate Port Service[0000:00:18.5:pcie00]
[38629.811696] Allocate Port Service[0000:00:18.5:pcie02]
[38629.812204] PCI: Setting latency timer of device 0000:00:18.6 to 64
[38629.812622] assign_interrupt_mode Found MSI capability
[38629.813021] Allocate Port Service[0000:00:18.6:pcie00]
[38629.813062] Allocate Port Service[0000:00:18.6:pcie02]
[38629.813561] PCI: Setting latency timer of device 0000:00:18.7 to 64
[38629.813973] assign_interrupt_mode Found MSI capability
[38629.814373] Allocate Port Service[0000:00:18.7:pcie00]
[38629.814408] Allocate Port Service[0000:00:18.7:pcie02]
[38629.814989] isapnp: Scanning for PnP cards...
[38630.173190] isapnp: No Plug & Play device found
[38630.197913] Real Time Clock Driver v1.12ac
[38630.198031] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[38630.198453] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[38630.198851] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[38630.199565] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[38630.200081] 00:0a: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[38630.201088] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[38630.201152] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[38630.201251] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:MOUS] at 0x60,0x64 irq 1,12
[38630.734198] serio: i8042 KBD port at 0x60,0x64 irq 1
[38630.734206] serio: i8042 AUX port at 0x60,0x64 irq 12
[38630.764031] mice: PS/2 mouse device common for all mice
[38630.764199] EISA: Probing bus 0 at eisa.0
[38630.764212] Cannot allocate resource for EISA slot 1
[38630.764215] Cannot allocate resource for EISA slot 2
[38630.764217] Cannot allocate resource for EISA slot 3
[38630.764219] Cannot allocate resource for EISA slot 4
[38630.764221] Cannot allocate resource for EISA slot 5
[38630.764223] Cannot allocate resource for EISA slot 6
[38630.764225] Cannot allocate resource for EISA slot 7
[38630.764228] Cannot allocate resource for EISA slot 8
[38630.764230] EISA: Detected 0 cards.
[38630.764232] cpuidle: using governor ladder
[38630.764234] cpuidle: using governor menu
[38630.764294] NET: Registered protocol family 1
[38630.764324] Using IPI No-Shortcut mode
[38630.764347] registered taskstats version 1
[38630.764522]   Magic number: 13:580:810
[38630.764560]   hash matches device ptys4
[38630.764575]   hash matches device 0000:00:16.2:pcie02
[38630.764582]   hash matches device PNP0A05:02
[38630.764591] BIOS EDD facility v0.16 2004-Jun-25, 6 devices found
[38630.764952] Freeing unused kernel memory: 384k freed
[38630.764987] Write protecting the kernel read-only data: 830k
[38630.766142] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[38630.897295] VMware vmxnet virtual NIC driver
[38630.897405] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 18 (level, low) -> IRQ 16
[38630.897549] Found vmxnet/PCI at 0x2024, irq 16.
[38630.897606] features:
[38630.897616] numRxBuffers = 100, numRxBuffers2 = 1
[38630.899880] fuse init (API version 7.9)
[38630.908657] ACPI: Processor [CPU0] (supports 8 throttling states)
[38630.916467] device-mapper: uevent: version 1.0.3
[38630.916515] device-mapper: ioctl: 4.12.0-ioctl (2007-10-02) initialised: dm-devel@redhat.com
[38631.105856] SCSI subsystem initialized
[38631.115210] libata version 3.00 loaded.
[38631.123532] ata_piix 0000:00:07.1: version 2.12
[38631.124472] scsi0 : ata_piix
[38631.125604] scsi1 : ata_piix
[38631.125643] ata1: PATA max UDMA/33 cmd 0x1f0 ctl 0x3f6 bmdma 0x10c0 irq 14
[38631.125646] ata2: PATA max UDMA/33 cmd 0x170 ctl 0x376 bmdma 0x10c8 irq 15
[38631.125771] ata1: port disabled. ignoring.
[38631.133498] Fusion MPT base driver 3.04.06
[38631.133500] Copyright (c) 1999-2007 LSI Corporation
[38631.136032] Fusion MPT SPI Host driver 3.04.06
[38631.145511] pcnet32.c:v1.34 14.Aug.2007 tsbogend@alpha.franken.de
[38631.327841] Floppy drive(s): fd0 is 1.44M
[38631.344150] FDC 0 is a post-1991 82077
[38631.463194] ata2.00: ATAPI: VMware Virtual IDE CDROM Drive, 00000001, max UDMA/33
[38631.622996] ata2.00: configured for UDMA/33
[38631.623229] scsi 1:0:0:0: CD-ROM            NECVMWar VMware IDE CDR10 1.00 PQ: 0 ANSI: 5
[38631.623432] ACPI: PCI Interrupt 0000:00:10.0[A] -> GSI 17 (level, low) -> IRQ 17
[38631.623560] mptbase: ioc0: Initiating bringup
[38631.655463] Driver 'sr' needs updating - please use bus_type methods
[38631.657000] sr0: scsi3-mmc drive: 1x/1x xa/form2 cdda tray
[38631.657003] Uniform CD-ROM driver Revision: 3.20
[38631.657024] sr 1:0:0:0: Attached scsi CD-ROM sr0
[38631.658159] sr 1:0:0:0: Attached scsi generic sg0 type 5
[38631.802878] ioc0: LSI53C1030 B0: Capabilities={Initiator}
[38632.122835] scsi2 : ioc0: LSI53C1030 B0, FwRev=00000000h, Ports=1, MaxQ=128, IRQ=17
[38632.402175] scsi 2:0:0:0: Direct-Access     VMware,  VMware Virtual S 1.0  PQ: 0 ANSI: 2
[38632.402185]  target2:0:0: Beginning Domain Validation
[38632.402828]  target2:0:0: Domain Validation skipping write tests
[38632.402832]  target2:0:0: Ending Domain Validation
[38632.402865]  target2:0:0: FAST-40 WIDE SCSI 80.0 MB/s ST (25 ns, offset 127)
[38632.404420] scsi 2:0:0:0: Attached scsi generic sg1 type 0
[38632.422422] Driver 'sd' needs updating - please use bus_type methods
[38632.422573] sd 2:0:0:0: [sda] 62914560 512-byte hardware sectors (32212 MB)
[38632.422615] sd 2:0:0:0: [sda] Write Protect is off
[38632.422619] sd 2:0:0:0: [sda] Mode Sense: 5d 00 00 00
[38632.422713] sd 2:0:0:0: [sda] Cache data unavailable
[38632.422716] sd 2:0:0:0: [sda] Assuming drive cache: write through
[38632.422875] sd 2:0:0:0: [sda] 62914560 512-byte hardware sectors (32212 MB)
[38632.422916] sd 2:0:0:0: [sda] Write Protect is off
[38632.422919] sd 2:0:0:0: [sda] Mode Sense: 5d 00 00 00
[38632.422983] sd 2:0:0:0: [sda] Cache data unavailable
[38632.422986] sd 2:0:0:0: [sda] Assuming drive cache: write through
[38632.423090]  sda: sda1 sda2 < sda5 >
[38632.432063] sd 2:0:0:0: [sda] Attached SCSI disk
[38632.586714] Attempting manual resume
[38632.586723] swsusp: Resume From Partition 254:1
[38632.586726] PM: Checking swsusp image.
[38632.586789] PM: Resume from disk failed.
[38632.601741] kjournald starting.  Commit interval 5 seconds
[38632.601756] EXT3-fs: mounted filesystem with ordered data mode.
[38634.838744] VMCI: Major device number is: 254
[38634.838815] Probing for vmci/PCI.
[38634.838855] ACPI: PCI Interrupt 0000:00:07.7[A] -> GSI 16 (level, low) -> IRQ 18
[38634.838888] Found vmci/PCI at 0x1080, irq 18.
[38634.838960] VMCIUtil: Host capability check: PASSED
[38634.838972] Registered vmci device.
[38634.859419] input: PC Speaker as /devices/platform/pcspkr/input/input2
[38634.878882] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[38634.899331] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[38634.919192] Linux agpgart interface v0.102
[38634.961556] ACPI: AC Adapter [ACAD] (on-line)
[38634.979763] input: Power Button (FF) as /devices/virtual/input/input3
[38634.998581] ACPI: Power Button (FF) [PWRF]
[38634.998631] input: Sleep Button (CM) as /devices/virtual/input/input4
[38634.998709] agpgart: Detected an Intel 440BX Chipset.
[38634.999085] agpgart: AGP aperture is 256M @ 0x0
[38635.018519] piix4_smbus 0000:00:07.3: Found 0000:00:07.3 device
[38635.018546] piix4_smbus 0000:00:07.3: Host SMBus controller not enabled!
[38635.028496] ACPI: Sleep Button (CM) [SLPB]
[38635.123790] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input5
[38635.430604] parport_pc 00:08: reported by Plug and Play ACPI
[38635.430721] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[38635.628683] NET: Registered protocol family 10
[38635.628772] lo: Disabled Privacy Extensions
[38636.921833] loop: module loaded
[38636.944228] lp0: using parport0 (interrupt-driven).
[38637.160867] Adding 1331192k swap on /dev/mapper/beowulf-swap_1.  Priority:-1 extents:1 across:1331192k
[38646.380002] eth0: no IPv6 routers present
[38755.747694] EXT3 FS on dm-0, internal journal
[38760.512357] kjournald starting.  Commit interval 5 seconds
[38760.512649] EXT3 FS on sda1, internal journal
[38760.512652] EXT3-fs: mounted filesystem with ordered data mode.
[38760.656206] VMware hgfs: HGFS is disabled in the host
[38761.406077] NET: Registered protocol family 15
[38761.608476] padlock: VIA PadLock Hash Engine not detected.
[38761.722280] padlock: VIA PadLock Hash Engine not detected.
[38761.900592] padlock: VIA PadLock not detected.
[38762.524162] ip_tables: (C) 2000-2006 Netfilter Core Team
[38766.969445] No dock devices found.
[38766.981712] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[38767.041477] acpiphp: Slot [32] registered
[38767.041507] acpiphp: Slot [33] registered
[38767.041519] acpiphp: Slot [34] registered
[38767.041547] acpiphp: Slot [35] registered
[38767.041566] acpiphp: Slot [36] registered
[38767.041580] acpiphp: Slot [37] registered
[38767.041595] acpiphp: Slot [38] registered
[38767.041611] acpiphp: Slot [39] registered
[38767.041624] acpiphp: Slot [40] registered
[38767.041646] acpiphp: Slot [41] registered
[38767.041660] acpiphp: Slot [42] registered
[38767.041677] acpiphp: Slot [43] registered
[38767.041689] acpiphp: Slot [44] registered
[38767.041717] acpiphp: Slot [45] registered
[38767.041733] acpiphp: Slot [46] registered
[38767.041743] acpiphp: Slot [47] registered
[38767.041756] acpiphp: Slot [48] registered
[38767.041771] acpiphp: Slot [49] registered
[38767.041784] acpiphp: Slot [50] registered
[38767.041796] acpiphp: Slot [51] registered
[38767.041805] acpiphp: Slot [52] registered
[38767.041824] acpiphp: Slot [53] registered
[38767.041835] acpiphp: Slot [54] registered
[38767.041850] acpiphp: Slot [55] registered
[38767.041861] acpiphp: Slot [56] registered
[38767.041876] acpiphp: Slot [57] registered
[38767.041888] acpiphp: Slot [58] registered
[38767.041905] acpiphp: Slot [59] registered
[38767.041917] acpiphp: Slot [60] registered
[38767.041935] acpiphp: Slot [61] registered
[38767.041953] acpiphp: Slot [62] registered
[38767.041968] acpiphp: Slot [63] registered
[38767.042014] acpiphp: Slot [160] registered
[38767.042042] acpiphp: Slot [192] registered
[38767.042061] acpiphp: Slot [224] registered
[38767.042084] acpiphp: Slot [256] registered
[38767.042122] acpiphp: Slot [161] registered
[38767.042156] acpiphp: Slot [162] registered
[38767.042184] acpiphp: Slot [163] registered
[38767.042201] acpiphp: Slot [164] registered
[38767.042223] acpiphp: Slot [165] registered
[38767.042243] acpiphp: Slot [166] registered
[38767.042264] acpiphp: Slot [167] registered
[38767.042285] acpiphp: Slot [193] registered
[38767.042308] acpiphp: Slot [194] registered
[38767.042349] acpiphp: Slot [195] registered
[38767.042367] acpiphp: Slot [196] registered
[38767.042383] acpiphp: Slot [197] registered
[38767.042398] acpiphp: Slot [198] registered
[38767.042418] acpiphp: Slot [199] registered
[38767.042435] acpiphp: Slot [225] registered
[38767.042451] acpiphp: Slot [226] registered
[38767.042467] acpiphp: Slot [227] registered
[38767.042488] acpiphp: Slot [228] registered
[38767.042513] acpiphp: Slot [229] registered
[38767.042540] acpiphp: Slot [230] registered
[38767.042556] acpiphp: Slot [231] registered
[38767.042572] acpiphp: Slot [257] registered
[38767.042595] acpiphp: Slot [258] registered
[38767.042612] acpiphp: Slot [259] registered
[38767.042628] acpiphp: Slot [260] registered
[38767.042651] acpiphp: Slot [261] registered
[38767.042669] acpiphp: Slot [262] registered
[38767.042693] acpiphp: Slot [263] registered
[38767.377470] VMware hgfs: HGFS is disabled in the host
[38767.438735] VMware memory control driver initialized
[38767.439064] vmmemctl: started kernel thread pid=5156
[38767.514779] vsock: no version for "VMCIMemcpyToQueueV" found: kernel tainted.
[38774.037839] NET: Registered protocol family 17
[38774.073320] device eth0 entered promiscuous mode
[38774.073331] audit(1369356648.123:2): dev=eth0 prom=256 old_prom=0 auid=4294967295
[38774.073334] eth0: Promiscuous mode enabled.
[38784.000485] nf_conntrack version 0.5.0 (8192 buckets, 32768 max)
[38784.861727] Initializing XFRM netlink socket
[38785.074066] NET: Unregistered protocol family 15
[38785.673116] NET: Registered protocol family 15
[38785.812438] padlock: VIA PadLock Hash Engine not detected.
[38785.873749] padlock: VIA PadLock Hash Engine not detected.
[38786.072305] padlock: VIA PadLock not detected.
[38786.272448] Initializing XFRM netlink socket
[39076.017780] NET: Unregistered protocol family 15

```

To be honest, a lot doesn't make any sense but it sounds like the Ubuntu vServer has hardware or driver issues.

Can you give me some pointers, suggestions in which direction to dig further? Do you suggest an upgrade to Ubuntu 10.04 LTS?

-- nick

---

