---
title: "Date Change to 1971"
date: 2009-05-06
forum: Server Platforms
---

### Post by eduardo.r.t on 2009-05-06
I have an Ubuntu 8.04 server running as a VM inside of a VMWare ESX 3.5 environment.

The server is a basic LAMP box running several websites  At seemingly random times, the clock on the VM goes to a date in 1971. (Today it went to June 30, 1971.) After the clock goes crazy, Apache and the other parts of the system seem to hang. A reboot seems to fix the issue.

Does anyone have any idea what might be going on here?

Thank you in advance,

---

### Post by Wiebelhaus on 2009-05-06
What does the BIOS Report?

---

### Post by eduardo.r.t on 2009-05-06
Do not understand your question. 

 How do I verify this?

---

### Post by eduardo.r.t on 2009-05-06
The /var/log/messages


May  6 09:24:07 ams kernel: [    0.000000] Initializing cgroup subsys cpuset
May  6 09:24:07 ams kernel: [    0.000000] Initializing cgroup subsys cpu
May  6 09:24:07 ams kernel: [    0.000000] Linux version 2.6.24-19-server (buildd@palmer) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed Jun 18 15:18:00 UTC 2008 (Ubuntu 2.6.24-19.34-server)
May  6 09:24:07 ams kernel: [    0.000000] BIOS-provided physical RAM map:
May  6 09:24:07 ams kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
May  6 09:24:07 ams kernel: [    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
May  6 09:24:07 ams kernel: [    0.000000]  BIOS-e820: 00000000000ca000 - 00000000000cc000 (reserved)
May  6 09:24:07 ams kernel: [    0.000000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
May  6 09:24:07 ams kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 00000000efef0000 (usable)
May  6 09:24:07 ams kernel: [    0.000000]  BIOS-e820: 00000000efef0000 - 00000000efeff000 (ACPI data)
May  6 09:24:07 ams kernel: [    0.000000]  BIOS-e820: 00000000efeff000 - 00000000eff00000 (ACPI NVS)
May  6 09:24:07 ams kernel: [    0.000000]  BIOS-e820: 00000000eff00000 - 00000000f0000000 (usable)
May  6 09:24:07 ams kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
May  6 09:24:07 ams kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
May  6 09:24:07 ams kernel: [    0.000000]  BIOS-e820: 00000000fffe0000 - 0000000100000000 (reserved)
May  6 09:24:07 ams kernel: [    0.000000] 2944MB HIGHMEM available.
May  6 09:24:07 ams kernel: [    0.000000] 896MB LOWMEM available.
May  6 09:24:07 ams kernel: [    0.000000] found SMP MP-table at 000f6cd0
May  6 09:24:07 ams kernel: [    0.000000] Zone PFN ranges:
May  6 09:24:07 ams kernel: [    0.000000]   DMA             0 ->     4096
May  6 09:24:07 ams kernel: [    0.000000]   Normal       4096 ->   229376
May  6 09:24:07 ams kernel: [    0.000000]   HighMem    229376 ->   983040
May  6 09:24:07 ams kernel: [    0.000000] Movable zone start PFN for each node
May  6 09:24:07 ams kernel: [    0.000000] early_node_map[1] active PFN ranges
May  6 09:24:07 ams kernel: [    0.000000]     0:        0 ->   983040
May  6 09:24:07 ams kernel: [    0.000000] DMI present.
May  6 09:24:07 ams kernel: [    0.000000] ACPI: RSDP signature @ 0xC00F6C60 checksum 0
May  6 09:24:07 ams kernel: [    0.000000] ACPI: RSDP 000F6C60, 0014 (r0 PTLTD )
May  6 09:24:07 ams kernel: [    0.000000] ACPI: RSDT EFEFAB5A, 0030 (r1 PTLTD    RSDT    6040000  LTP        0)
May  6 09:24:07 ams kernel: [    0.000000] ACPI: FACP EFEFEF06, 0074 (r1 INTEL  440BX     6040000 PTL     F4240)
May  6 09:24:07 ams kernel: [    0.000000] ACPI: DSDT EFEFAB8A, 437C (r1 PTLTD  Custom    6040000 MSFT  100000D)
May  6 09:24:07 ams kernel: [    0.000000] ACPI: FACS EFEFFFC0, 0040
May  6 09:24:07 ams kernel: [    0.000000] ACPI: APIC EFEFEF7A, 005E (r1 PTLTD  ^I APIC    6040000  LTP        0)
May  6 09:24:07 ams kernel: [    0.000000] ACPI: BOOT EFEFEFD8, 0028 (r1 PTLTD  $SBFTBL$  6040000  LTP        1)
May  6 09:24:07 ams kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x1008
May  6 09:24:07 ams kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
May  6 09:24:07 ams kernel: [    0.000000] Processor #0 7:7 APIC version 17
May  6 09:24:07 ams kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
May  6 09:24:07 ams kernel: [    0.000000] Processor #1 7:7 APIC version 17
May  6 09:24:07 ams kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
May  6 09:24:07 ams kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
May  6 09:24:07 ams kernel: [    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
May  6 09:24:07 ams kernel: [    0.000000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
May  6 09:24:07 ams kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
May  6 09:24:07 ams kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
May  6 09:24:07 ams kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
May  6 09:24:07 ams kernel: [    0.000000] Allocating PCI resources starting at f1000000 (gap: f0000000:0ec00000)
May  6 09:24:07 ams kernel: [    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
May  6 09:24:07 ams kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000ca000
May  6 09:24:07 ams kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000ca000 - 00000000000cc000
May  6 09:24:07 ams kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000cc000 - 00000000000dc000
May  6 09:24:07 ams kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000dc000 - 0000000000100000
May  6 09:24:07 ams kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 975360
May  6 09:24:07 ams kernel: [    0.000000] Kernel command line: root=UUID=d56871c1-b6c4-4903-b3ec-065609b16db9 ro quiet splash
May  6 09:24:07 ams kernel: [    0.000000] Enabling fast FPU save and restore... done.
May  6 09:24:07 ams kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
May  6 09:24:07 ams kernel: [    0.000000] Initializing CPU#0
May  6 09:24:07 ams kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
May  6 09:24:07 ams kernel: [    0.000000] Detected 2492.587 MHz processor.
May  6 09:24:07 ams kernel: [    4.873585] Console: colour VGA+ 80x25
May  6 09:24:07 ams kernel: [    4.873752] console [tty0] enabled
May  6 09:24:07 ams kernel: [    4.874374] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
May  6 09:24:07 ams kernel: [    4.874711] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
May  6 09:24:07 ams kernel: [    5.044213] Memory: 3887784k/3932160k available (2256k kernel code, 43088k reserved, 1031k data, 384k init, 3014592k highmem)
May  6 09:24:07 ams kernel: [    5.044244] virtual kernel memory layout:
May  6 09:24:07 ams kernel: [    5.044247]     fixmap  : 0xfff4c000 - 0xfffff000   ( 716 kB)
May  6 09:24:07 ams kernel: [    5.044247]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
May  6 09:24:07 ams kernel: [    5.044248]     vmalloc : 0xf8800000 - 0xffbfe000   ( 115 MB)
May  6 09:24:07 ams kernel: [    5.044249]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
May  6 09:24:07 ams kernel: [    5.044250]       .init : 0xc043c000 - 0xc049c000   ( 384 kB)
May  6 09:24:07 ams kernel: [    5.044251]       .data : 0xc03341f5 - 0xc0435fe4   (1031 kB)
May  6 09:24:07 ams kernel: [    5.044252]       .text : 0xc0100000 - 0xc03341f5   (2256 kB)
May  6 09:24:07 ams kernel: [    5.044274] Checking if this processor honours the WP bit even in supervisor mode... Ok.
May  6 09:24:07 ams kernel: [    5.045131] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
May  6 09:24:07 ams kernel: [    5.195426] Calibrating delay using timer specific routine.. 5000.35 BogoMIPS (lpj=25001769)
May  6 09:24:07 ams kernel: [    5.195582] Security Framework initialized
May  6 09:24:07 ams kernel: [    5.195738] SELinux:  Disabled at boot.
May  6 09:24:07 ams kernel: [    5.195894] AppArmor: AppArmor initialized
May  6 09:24:07 ams kernel: [    5.196050] Failure registering capabilities with primary security module.
May  6 09:24:07 ams kernel: [    5.196206] Mount-cache hash table entries: 512
May  6 09:24:07 ams kernel: [    5.196362] Initializing cgroup subsys ns
May  6 09:24:07 ams kernel: [    5.196475] Initializing cgroup subsys cpuacct
May  6 09:24:07 ams kernel: [    5.196787] CPU: L1 I cache: 32K, L1 D cache: 32K
May  6 09:24:07 ams kernel: [    5.196811] CPU: L2 cache: 6144K
May  6 09:24:07 ams kernel: [    5.197042] Compat vDSO mapped to ffffe000.
May  6 09:24:07 ams kernel: [    5.197198] Checking 'hlt' instruction... OK.
May  6 09:24:07 ams kernel: [    5.235460] SMP alternatives: switching to UP code
May  6 09:24:07 ams kernel: [    5.235616] Early unpacking initramfs... done
May  6 09:24:07 ams kernel: [    5.525000] ACPI: Core revision 20070126
May  6 09:24:07 ams kernel: [    5.525156] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
May  6 09:24:07 ams kernel: [    5.525912] CPU0: Intel(R) Xeon(R) CPU           E5420  @ 2.50GHz stepping 08
May  6 09:24:07 ams kernel: [    5.526338] SMP alternatives: switching to SMP code
May  6 09:24:07 ams kernel: [    5.526494] Booting processor 1/1 eip 3000
May  6 09:24:07 ams kernel: [    5.538164] Initializing CPU#1
May  6 09:24:07 ams kernel: [    5.684688] Calibrating delay using timer specific routine.. 4988.39 BogoMIPS (lpj=24941964)
May  6 09:24:07 ams kernel: [    5.685357] CPU: L1 I cache: 32K, L1 D cache: 32K
May  6 09:24:07 ams kernel: [    5.685380] CPU: L2 cache: 6144K
May  6 09:24:07 ams kernel: [    5.686085] CPU1: Intel(R) Xeon(R) CPU           E5420  @ 2.50GHz stepping 08
May  6 09:24:07 ams kernel: [    5.686241] Total of 2 processors activated (9988.74 BogoMIPS).
May  6 09:24:07 ams kernel: [    5.686397] ENABLING IO-APIC IRQs
May  6 09:24:07 ams kernel: [    5.686750] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
May  6 09:24:07 ams kernel: [    5.905903] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
May  6 09:24:07 ams kernel: [    5.926412] Brought up 2 CPUs
May  6 09:24:07 ams kernel: [    5.927917] net_namespace: 64 bytes
May  6 09:24:07 ams kernel: [    5.927976] Booting paravirtualized kernel on bare hardware
May  6 09:24:07 ams kernel: [    5.928296] Time: 12:23:45  Date: 05/06/09
May  6 09:24:07 ams kernel: [    5.928354] NET: Registered protocol family 16
May  6 09:24:07 ams kernel: [    5.929064] EISA bus registered
May  6 09:24:07 ams kernel: [    5.929123] ACPI: bus type pci registered
May  6 09:24:07 ams kernel: [    5.929379] PCI: PCI BIOS revision 2.10 entry at 0xfd9a0, last bus=1
May  6 09:24:07 ams kernel: [    5.929421] PCI: Using configuration type 1
May  6 09:24:07 ams kernel: [    5.929479] Setting up standard PCI resources
May  6 09:24:07 ams kernel: [    5.936908] ACPI: Interpreter enabled
May  6 09:24:07 ams kernel: [    5.936934] ACPI: (supports S0 S1 S4 S5)
May  6 09:24:07 ams kernel: [    5.936993] ACPI: Using IOAPIC for interrupt routing
May  6 09:24:07 ams kernel: [    5.947834] ACPI: PCI Root Bridge [PCI0] (0000:00)
May  6 09:24:07 ams kernel: [    5.948000] PCI quirk: region 1000-103f claimed by PIIX4 ACPI
May  6 09:24:07 ams kernel: [    5.948044] PCI quirk: region 1040-104f claimed by PIIX4 SMB
May  6 09:24:07 ams kernel: [    5.949220] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 11 14 15) *0, disabled.
May  6 09:24:07 ams kernel: [    5.949278] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *9 10 11 14 15)
May  6 09:24:07 ams kernel: [    5.949336] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 *11 14 15)
May  6 09:24:07 ams kernel: [    5.949395] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 10 11 14 15) *0, disabled.
May  6 09:24:07 ams kernel: [    5.949651] Linux Plug and Play Support v0.97 (c) Adam Belay
May  6 09:24:07 ams kernel: [    5.949742] pnp: PnP ACPI init
May  6 09:24:07 ams kernel: [    5.949801] ACPI: bus type pnp registered
May  6 09:24:07 ams kernel: [    5.960653] pnp: PnP ACPI: found 12 devices
May  6 09:24:07 ams kernel: [    5.960691] ACPI: ACPI bus type pnp unregistered
May  6 09:24:07 ams kernel: [    5.960755] PnPBIOS: Disabled by ACPI PNP
May  6 09:24:07 ams kernel: [    5.961617] PCI: Using ACPI for IRQ routing
May  6 09:24:07 ams kernel: [    5.961666] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
May  6 09:24:07 ams kernel: [    6.014646] NET: Registered protocol family 8
May  6 09:24:07 ams kernel: [    6.014669] NET: Registered protocol family 20
May  6 09:24:07 ams kernel: [    6.014819] NetLabel: Initializing
May  6 09:24:07 ams kernel: [    6.014828] NetLabel:  domain hash size = 128
May  6 09:24:07 ams kernel: [    6.014836] NetLabel:  protocols = UNLABELED CIPSOv4
May  6 09:24:07 ams kernel: [    6.014992] NetLabel:  unlabeled traffic allowed by default
May  6 09:24:07 ams kernel: [    6.016258] AppArmor: AppArmor Filesystem Enabled
May  6 09:24:07 ams kernel: [    6.024555] Time: tsc clocksource has been installed.
May  6 09:24:07 ams kernel: [    6.044673] system 00:01: ioport range 0x1000-0x103f has been reserved
May  6 09:24:07 ams kernel: [    6.044687] system 00:01: ioport range 0x1040-0x104f has been reserved
May  6 09:24:07 ams kernel: [    6.076469] PCI: Bridge: 0000:00:01.0
May  6 09:24:07 ams kernel: [    6.076485]   IO window: disabled.
May  6 09:24:07 ams kernel: [    6.076571]   MEM window: disabled.
May  6 09:24:07 ams kernel: [    6.076633]   PREFETCH window: disabled.
May  6 09:24:07 ams kernel: [    6.076945] NET: Registered protocol family 2
May  6 09:24:07 ams kernel: [    6.174436] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
May  6 09:24:07 ams kernel: [    6.176049] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
May  6 09:24:07 ams kernel: [    6.176205] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
May  6 09:24:07 ams kernel: [    6.176361] TCP: Hash tables configured (established 131072 bind 65536)
May  6 09:24:07 ams kernel: [    6.176483] TCP reno registered
May  6 09:24:07 ams kernel: [    6.204364] checking if image is initramfs... it is
May  6 09:24:07 ams kernel: [    6.745677] Freeing initrd memory: 7191k freed
May  6 09:24:07 ams kernel: [    6.746052] Simple Boot Flag at 0x36 set to 0x1
May  6 09:24:07 ams kernel: [    6.749741] audit: initializing netlink socket (disabled)
May  6 09:24:07 ams kernel: [    6.749894] audit(1241612624.580:1): initialized
May  6 09:24:07 ams kernel: [    6.750725] highmem bounce pool size: 64 pages
May  6 09:24:07 ams kernel: [    6.750798] Total HugeTLB memory allocated, 0
May  6 09:24:07 ams kernel: [    6.756091] VFS: Disk quotas dquot_6.5.1
May  6 09:24:07 ams kernel: [    6.756304] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
May  6 09:24:07 ams kernel: [    6.756964] io scheduler noop registered
May  6 09:24:07 ams kernel: [    6.756992] io scheduler anticipatory registered
May  6 09:24:07 ams kernel: [    6.757015] io scheduler deadline registered (default)
May  6 09:24:07 ams kernel: [    6.757063] io scheduler cfq registered
May  6 09:24:07 ams kernel: [    6.757216] Limiting direct PCI/PCI transfers.
May  6 09:24:07 ams kernel: [    6.758924] isapnp: Scanning for PnP cards...
May  6 09:24:07 ams kernel: [    7.114215] isapnp: No Plug & Play device found
May  6 09:24:07 ams kernel: [    7.184295] Real Time Clock Driver v1.12ac
May  6 09:24:07 ams kernel: [    7.184632] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
May  6 09:24:07 ams kernel: [    7.185034] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
May  6 09:24:07 ams kernel: [    7.185410] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
May  6 09:24:07 ams kernel: [    7.186681] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
May  6 09:24:07 ams kernel: [    7.187193] 00:0a: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
May  6 09:24:07 ams kernel: [    7.189702] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
May  6 09:24:07 ams kernel: [    7.189987] input: Macintosh mouse button emulation as /devices/virtual/input/input0
May  6 09:24:07 ams kernel: [    7.190647] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:MOUS] at 0x60,0x64 irq 1,12
May  6 09:24:07 ams kernel: [    7.699445] serio: i8042 KBD port at 0x60,0x64 irq 1
May  6 09:24:07 ams kernel: [    7.699571] serio: i8042 AUX port at 0x60,0x64 irq 12
May  6 09:24:07 ams kernel: [    7.744137] mice: PS/2 mouse device common for all mice
May  6 09:24:07 ams kernel: [    7.744874] EISA: Probing bus 0 at eisa.0
May  6 09:24:07 ams kernel: [    7.744989] Cannot allocate resource for EISA slot 1
May  6 09:24:07 ams kernel: [    7.745048] EISA: Detected 0 cards.
May  6 09:24:07 ams kernel: [    7.745147] cpuidle: using governor ladder
May  6 09:24:07 ams kernel: [    7.745219] cpuidle: using governor menu
May  6 09:24:07 ams kernel: [    7.745334] NET: Registered protocol family 1
May  6 09:24:07 ams kernel: [    7.745450] Using IPI No-Shortcut mode
May  6 09:24:07 ams kernel: [    7.745565] registered taskstats version 1
May  6 09:24:07 ams kernel: [    7.745681]   Magic number: 9:537:379
May  6 09:24:07 ams kernel: [    7.745797] BIOS EDD facility v0.16 2004-Jun-25, 6 devices found
May  6 09:24:07 ams kernel: [    7.747380] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
May  6 09:24:07 ams kernel: [    7.747764] Freeing unused kernel memory: 384k freed
May  6 09:24:07 ams kernel: [    7.974761] fuse init (API version 7.9)
May  6 09:24:07 ams kernel: [    7.994896] ACPI: Processor [CPU0] (supports 8 throttling states)
May  6 09:24:07 ams kernel: [    7.995162] ACPI: Processor [CPU1] (supports 8 throttling states)
May  6 09:24:07 ams kernel: [    7.995278] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
May  6 09:24:07 ams kernel: [    7.995340] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
May  6 09:24:07 ams kernel: [    8.122167] SCSI subsystem initialized
May  6 09:24:07 ams kernel: [    8.171000] scsi0 : ata_piix
May  6 09:24:07 ams kernel: [    8.171641] scsi1 : ata_piix
May  6 09:24:07 ams kernel: [    8.171826] ata1: PATA max UDMA/33 cmd 0x1f0 ctl 0x3f6 bmdma 0x1050 irq 14
May  6 09:24:07 ams kernel: [    8.171843] ata2: PATA max UDMA/33 cmd 0x170 ctl 0x376 bmdma 0x1058 irq 15
May  6 09:24:07 ams kernel: [    8.244051] pcnet32.c:v1.34 14.Aug.2007 [email]tsbogend@alpha.franken.de[/email]
May  6 09:24:07 ams kernel: [    8.283999] Fusion MPT base driver 3.04.06
May  6 09:24:07 ams kernel: [    8.284014] Copyright (c) 1999-2007 LSI Corporation
May  6 09:24:07 ams kernel: [    8.294720] Fusion MPT SPI Host driver 3.04.06
May  6 09:24:07 ams kernel: [    8.303394] Floppy drive(s): fd0 is 1.44M
May  6 09:24:07 ams kernel: [    8.323405] FDC 0 is a post-1991 82077
May  6 09:24:07 ams kernel: [    8.490917] ata1.00: ATAPI: VMware Virtual IDE CDROM Drive, 00000001, max UDMA/33
May  6 09:24:07 ams kernel: [    8.649661] ata1.00: configured for UDMA/33
May  6 09:24:07 ams kernel: [    8.653267] scsi 0:0:0:0: CD-ROM            NECVMWar VMware IDE CDR00 1.00 PQ: 0 ANSI: 5
May  6 09:24:07 ams kernel: [    8.654563] ACPI: PCI Interrupt 0000:00:11.0[A] -> GSI 18 (level, low) -> IRQ 16
May  6 09:24:07 ams kernel: [    8.654961] pcnet32: PCnet/PCI II 79C970A at 0x1400, 00 50 56 bd 72 16 assigned IRQ 16.
May  6 09:24:07 ams kernel: [    8.655377] eth0: registered as PCnet/PCI II 79C970A
May  6 09:24:07 ams kernel: [    8.655504] pcnet32: 1 cards_found.
May  6 09:24:07 ams kernel: [    8.656134] ACPI: PCI Interrupt 0000:00:10.0[A] -> GSI 17 (level, low) -> IRQ 17
May  6 09:24:07 ams kernel: [    8.656340] mptbase: ioc0: Initiating bringup
May  6 09:24:07 ams kernel: [    8.829119] ioc0: LSI53C1030 B0: Capabilities={Initiator}
May  6 09:24:07 ams kernel: [    8.954942] Driver 'sr' needs updating - please use bus_type methods
May  6 09:24:07 ams kernel: [    8.958211] sr0: scsi3-mmc drive: 1x/1x xa/form2 cdda tray
May  6 09:24:07 ams kernel: [    8.958301] Uniform CD-ROM driver Revision: 3.20
May  6 09:24:07 ams kernel: [    8.961828] sr 0:0:0:0: Attached scsi generic sg0 type 5
May  6 09:24:07 ams kernel: [    9.151229] scsi2 : ioc0: LSI53C1030 B0, FwRev=00000000h, Ports=1, MaxQ=128, IRQ=17
May  6 09:24:07 ams kernel: [    9.430909] scsi 2:0:0:0: Direct-Access     VMware   Virtual disk     1.0  PQ: 0 ANSI: 2
May  6 09:24:07 ams kernel: [    9.431105]  target2:0:0: Beginning Domain Validation
May  6 09:24:07 ams kernel: [    9.431301]  target2:0:0: Domain Validation skipping write tests
May  6 09:24:07 ams kernel: [    9.431328]  target2:0:0: Ending Domain Validation
May  6 09:24:07 ams kernel: [    9.431524]  target2:0:0: FAST-40 WIDE SCSI 80.0 MB/s ST (25 ns, offset 127)
May  6 09:24:07 ams kernel: [    9.431917] scsi 2:0:0:0: Attached scsi generic sg1 type 0
May  6 09:24:07 ams kernel: [    9.461998] Driver 'sd' needs updating - please use bus_type methods
May  6 09:24:07 ams kernel: [    9.462195] sd 2:0:0:0: [sda] 83886080 512-byte hardware sectors (42950 MB)
May  6 09:24:07 ams kernel: [    9.462391] sd 2:0:0:0: [sda] Test WP failed, assume Write Enabled
May  6 09:24:07 ams kernel: [    9.462488] sd 2:0:0:0: [sda] Cache data unavailable
May  6 09:24:07 ams kernel: [    9.462705] sd 2:0:0:0: [sda] 83886080 512-byte hardware sectors (42950 MB)
May  6 09:24:07 ams kernel: [    9.462771] sd 2:0:0:0: [sda] Test WP failed, assume Write Enabled
May  6 09:24:07 ams kernel: [    9.462795] sd 2:0:0:0: [sda] Cache data unavailable
May  6 09:24:07 ams kernel: [    9.462936]  sda: sda1 sda2 < sda5 >
May  6 09:24:07 ams kernel: [    9.470749] sd 2:0:0:0: [sda] Attached SCSI disk
May  6 09:24:07 ams kernel: [    9.580514] Attempting manual resume
May  6 09:24:07 ams kernel: [    9.599981] EXT3-fs: INFO: recovery required on readonly filesystem.
May  6 09:24:07 ams kernel: [    9.599995] EXT3-fs: write access will be enabled during recovery.
May  6 09:24:07 ams kernel: [    9.783113] kjournald starting.  Commit interval 5 seconds
May  6 09:24:07 ams kernel: [    9.783353] EXT3-fs: sda1: orphan cleanup on readonly fs
May  6 09:24:07 ams kernel: [    9.784448] EXT3-fs: sda1: 5 orphan inodes deleted
May  6 09:24:07 ams kernel: [    9.784473] EXT3-fs: recovery complete.
May  6 09:24:07 ams kernel: [    9.787398] EXT3-fs: mounted filesystem with ordered data mode.
May  6 09:24:07 ams kernel: [   11.499887] Linux agpgart interface v0.102
May  6 09:24:07 ams kernel: [   11.535205] agpgart: Detected an Intel 440BX Chipset.
May  6 09:24:07 ams kernel: [   11.536378] agpgart: AGP aperture is 256M @ 0x0
May  6 09:24:07 ams kernel: [   11.562492] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
May  6 09:24:07 ams kernel: [   11.578706] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
May  6 09:24:07 ams kernel: [   11.650848] ACPI: AC Adapter [ACAD] (on-line)
May  6 09:24:07 ams kernel: [   11.676732] input: Power Button (FF) as /devices/virtual/input/input2
May  6 09:24:07 ams kernel: [   11.746031] ACPI: Power Button (FF) [PWRF]
May  6 09:24:07 ams kernel: [   11.748129] piix4_smbus 0000:00:07.3: Found 0000:00:07.3 device
May  6 09:24:07 ams kernel: [   12.076822] eth0: link up
May  6 09:24:07 ams kernel: [   12.738933] input: PC Speaker as /devices/platform/pcspkr/input/input3
May  6 09:24:07 ams kernel: [   13.315161] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input4
May  6 09:24:07 ams kernel: [   13.673079] NET: Registered protocol family 10
May  6 09:24:07 ams kernel: [   13.673572] lo: Disabled Privacy Extensions
May  6 09:24:07 ams kernel: [   14.228969] parport_pc 00:08: reported by Plug and Play ACPI
May  6 09:24:07 ams kernel: [   14.229354] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
May  6 09:24:07 ams kernel: [   15.100665] loop: module loaded
May  6 09:24:07 ams kernel: [   15.115993] lp0: using parport0 (interrupt-driven).
May  6 09:24:07 ams kernel: [   15.209080] Adding 1502036k swap on /dev/sda5.  Priority:-1 extents:1 across:1502036k
May  6 09:24:07 ams kernel: [   15.346429] EXT3 FS on sda1, internal journal
May  6 09:24:07 ams kernel: [   18.204133] ip_tables: (C) 2000-2006 Netfilter Core Team

---

### Post by kustomjs on 2009-05-06
you would need to access your bios when you get a boot screen. sometimes how to access bios would you would hit esc or delete or tab when your in the restart process.

---

### Post by Wiebelhaus on 2009-05-06
You'll need to [access the CMOS settings or BIOS and check the date and time]("http://www.smartcomputing.com/editorial/article.asp?article=articles%2F1992%2Ffeb92%2F0209%2F92n0209.asp") it may just be a dead [CMOS battery]("http://www.amazon.com/Sony-Lithium-Coin-Battery-CR2032/dp/B0001MQUOM") , cheap like 5 bucks.

Cheers. That should be all the information you need , you can also buy those batteries at Wal-Mart and Walgreens and drug stores and stuff.

---

### Post by brendan.lefoll on 2009-05-06
> **sx66gns said:**
> You'll need to [access the CMOS settings or BIOS and check the date and time]("http://www.smartcomputing.com/editorial/article.asp?article=articles%2F1992%2Ffeb92%2F0209%2F92n0209.asp") it may just be a dead [CMOS battery]("http://www.amazon.com/Sony-Lithium-Coin-Battery-CR2032/dp/B0001MQUOM") , cheap like 5 bucks.

Cheers. That should be all the information you need , you can also buy those batteries at Wal-Mart and Walgreens and drug stores and stuff.

it's a VM... there's no battery issue here...

In vmware tools you can enable time keeping with the host. This is probably the easiest way of getting rid of your problem.

Otherwise enable NTP normally. But i think doing it in vmware tools would be better.

Make sure there isnt a bug in ESX, there was something like that reported a while back I think - i dont follow it anymore, but i would check if your up to date.

---

