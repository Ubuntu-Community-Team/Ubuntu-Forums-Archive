---
title: "Loads of unrecognized network traffic!"
date: 2008-06-09
forum: Security
---

### Post by relexed on 2008-06-09
Hey guys,

since tonight my firestarter started going nuts. I checked my logs and found out loads of network traffic is going on without me knowing which service is causing this. Is there anyone who could help me figure out where to look? Sorry for the large output, but better to provide to much information. :)

This is from the log:
Jun 10 01:17:02 sys-op-dsktp exiting on signal 15
Jun 10 01:18:11 sys-op-dsktp syslogd 1.5.0#1ubuntu1: restart.
Jun 10 01:18:11 sys-op-dsktp kernel: Inspecting /boot/System.map-2.6.24-18-generic
Jun 10 01:18:11 sys-op-dsktp kernel: Loaded 27880 symbols from /boot/System.map-2.6.24-18-generic.
Jun 10 01:18:11 sys-op-dsktp kernel: Symbols match kernel version 2.6.24.
Jun 10 01:18:12 sys-op-dsktp kernel: Loaded 15155 symbols from 81 modules.
Jun 10 01:18:12 sys-op-dsktp kernel: [    0.000000] Initializing cgroup subsys cpuset
Jun 10 01:18:12 sys-op-dsktp kernel: [    0.000000] Initializing cgroup subsys cpu
Jun 10 01:18:12 sys-op-dsktp kernel: [    0.000000] Linux version 2.6.24-18-generic (buildd@terranova) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed May 28 20:27:26 UTC 2008 (Ubuntu 2.6.24-18.32-generic)
Jun 10 01:18:12 sys-op-dsktp kernel: [    0.000000] BIOS-provided physical RAM map:
Jun 10 01:18:12 sys-op-dsktp kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Jun 10 01:18:12 sys-op-dsktp kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Jun 10 01:18:12 sys-op-dsktp kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Jun 10 01:18:12 sys-op-dsktp kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000001ffec000 (usable)
Jun 10 01:18:12 sys-op-dsktp kernel: [    0.000000]  BIOS-e820: 000000001ffec000 - 000000001ffef000 (ACPI data)
Jun 10 01:18:12 sys-op-dsktp kernel: [    0.000000]  BIOS-e820: 000000001ffef000 - 000000001ffff000 (reserved)
Jun 10 01:18:12 sys-op-dsktp kernel: [    0.000000]  BIOS-e820: 000000001ffff000 - 0000000020000000 (ACPI NVS)
Jun 10 01:18:12 sys-op-dsktp kernel: [    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
Jun 10 01:18:12 sys-op-dsktp kernel: [    0.000000] 0MB HIGHMEM available.
Jun 10 01:18:12 sys-op-dsktp kernel: [    0.000000] 511MB LOWMEM available.
Jun 10 01:18:12 sys-op-dsktp kernel: [    0.000000] Zone PFN ranges:
Jun 10 01:18:12 sys-op-dsktp kernel: [    0.000000]   DMA             0 ->     4096
Jun 10 01:18:12 sys-op-dsktp kernel: [    0.000000]   Normal       4096 ->   131052
Jun 10 01:18:12 sys-op-dsktp kernel: [    0.000000]   HighMem    131052 ->   131052
Jun 10 01:18:12 sys-op-dsktp kernel: [    0.000000] Movable zone start PFN for each node
Jun 10 01:18:12 sys-op-dsktp kernel: [    0.000000] early_node_map[1] active PFN ranges
Jun 10 01:18:12 sys-op-dsktp kernel: [    0.000000]     0:        0 ->   131052
Jun 10 01:18:12 sys-op-dsktp kernel: [    0.000000] DMI 2.3 present.
Jun 10 01:18:12 sys-op-dsktp kernel: [    0.000000] ACPI: RSDP signature @ 0xC00F6A90 checksum 0
Jun 10 01:18:12 sys-op-dsktp kernel: [    0.000000] ACPI: RSDP 000F6A90, 0014 (r0 ASUS  )
Jun 10 01:18:12 sys-op-dsktp kernel: [    0.000000] ACPI: RSDT 1FFEC000, 002C (r1 ASUS   A7V      30303031 MSFT 31313031)
Jun 10 01:18:12 sys-op-dsktp kernel: [    0.000000] ACPI: FACP 1FFEC080, 0074 (r1 ASUS   A7V      30303031 MSFT 31313031)
Jun 10 01:18:12 sys-op-dsktp kernel: [    0.000000] ACPI: DSDT 1FFEC100, 2CE1 (r1   ASUS A7V          1000 MSFT  100000B)
Jun 10 01:18:12 sys-op-dsktp kernel: [    0.000000] ACPI: FACS 1FFFF000, 0040
Jun 10 01:18:12 sys-op-dsktp kernel: [    0.000000] ACPI: BOOT 1FFEC040, 0028 (r1 ASUS   A7V      30303031 MSFT 31313031)
Jun 10 01:18:12 sys-op-dsktp kernel: [    0.000000] ACPI: PM-Timer IO Port: 0xe408
Jun 10 01:18:12 sys-op-dsktp kernel: [    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:dfff0000)
Jun 10 01:18:12 sys-op-dsktp kernel: [    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
Jun 10 01:18:12 sys-op-dsktp kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000f0000
Jun 10 01:18:12 sys-op-dsktp kernel: [    0.000000] swsusp: Registered nosave memory region: 00000000000f0000 - 0000000000100000
Jun 10 01:18:12 sys-op-dsktp kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 130029
Jun 10 01:18:12 sys-op-dsktp kernel: [    0.000000] Kernel command line: root=UUID=4981ea32-f65a-41ad-b7ba-775d2db22391 ro quiet splash
Jun 10 01:18:12 sys-op-dsktp kernel: [    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
Jun 10 01:18:12 sys-op-dsktp kernel: [    0.000000] Enabling fast FPU save and restore... done.
Jun 10 01:18:12 sys-op-dsktp kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Jun 10 01:18:12 sys-op-dsktp kernel: [    0.000000] Initializing CPU#0
Jun 10 01:18:12 sys-op-dsktp kernel: [    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
Jun 10 01:18:12 sys-op-dsktp kernel: [    0.000000] Detected 1009.004 MHz processor.
Jun 10 01:18:12 sys-op-dsktp kernel: [   22.707976] Console: colour VGA+ 80x25
Jun 10 01:18:12 sys-op-dsktp kernel: [   22.707984] console [tty0] enabled
Jun 10 01:18:12 sys-op-dsktp kernel: [   22.708680] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
Jun 10 01:18:12 sys-op-dsktp kernel: [   22.709824] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
Jun 10 01:18:12 sys-op-dsktp kernel: [   22.736726] Memory: 507652k/524208k available (2176k kernel code, 15932k reserved, 1006k data, 368k init, 0k highmem)
Jun 10 01:18:12 sys-op-dsktp kernel: [   22.736742] virtual kernel memory layout:
Jun 10 01:18:12 sys-op-dsktp kernel: [   22.736744]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
Jun 10 01:18:12 sys-op-dsktp kernel: [   22.736746]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
Jun 10 01:18:12 sys-op-dsktp kernel: [   22.736749]     vmalloc : 0xe0800000 - 0xff7fe000   ( 495 MB)
Jun 10 01:18:12 sys-op-dsktp kernel: [   22.736751]     lowmem  : 0xc0000000 - 0xdffec000   ( 511 MB)
Jun 10 01:18:12 sys-op-dsktp kernel: [   22.736754]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
Jun 10 01:18:12 sys-op-dsktp kernel: [   22.736756]       .data : 0xc03201f4 - 0xc041bdc4   (1006 kB)
Jun 10 01:18:12 sys-op-dsktp kernel: [   22.736758]       .text : 0xc0100000 - 0xc03201f4   (2176 kB)
Jun 10 01:18:12 sys-op-dsktp kernel: [   22.736765] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Jun 10 01:18:12 sys-op-dsktp kernel: [   22.736849] SLUB: Genslabs=11, HWalign=32, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
Jun 10 01:18:12 sys-op-dsktp kernel: [   22.816817] Calibrating delay using timer specific routine.. 2020.41 BogoMIPS (lpj=4040821)
Jun 10 01:18:12 sys-op-dsktp kernel: [   22.816879] Security Framework initialized
Jun 10 01:18:12 sys-op-dsktp kernel: [   22.816893] SELinux:  Disabled at boot.
Jun 10 01:18:12 sys-op-dsktp kernel: [   22.816929] AppArmor: AppArmor initialized
Jun 10 01:18:12 sys-op-dsktp kernel: [   22.816940] Failure registering capabilities with primary security module.
Jun 10 01:18:12 sys-op-dsktp kernel: [   22.816960] Mount-cache hash table entries: 512
Jun 10 01:18:12 sys-op-dsktp kernel: [   22.817231] Initializing cgroup subsys ns
Jun 10 01:18:12 sys-op-dsktp kernel: [   22.817243] Initializing cgroup subsys cpuacct
Jun 10 01:18:12 sys-op-dsktp kernel: [   22.817283] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Jun 10 01:18:12 sys-op-dsktp kernel: [   22.817288] CPU: L2 Cache: 64K (64 bytes/line)
Jun 10 01:18:12 sys-op-dsktp kernel: [   22.817317] Compat vDSO mapped to ffffe000.
Jun 10 01:18:12 sys-op-dsktp kernel: [   22.817343] Checking 'hlt' instruction... OK.
Jun 10 01:18:12 sys-op-dsktp kernel: [   22.833283] SMP alternatives: switching to UP code
Jun 10 01:18:12 sys-op-dsktp kernel: [   22.835562] Freeing SMP alternatives: 11k freed
Jun 10 01:18:12 sys-op-dsktp kernel: [   22.835829] Early unpacking initramfs... done
Jun 10 01:18:12 sys-op-dsktp kernel: [   23.496850] ACPI: Core revision 20070126
Jun 10 01:18:12 sys-op-dsktp kernel: [   23.497018] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Jun 10 01:18:12 sys-op-dsktp kernel: [   23.499040] ACPI: setting ELCR to 0200 (from 0c18)
Jun 10 01:18:12 sys-op-dsktp kernel: [   23.499265] CPU0: AMD Duron(tm) Processor stepping 00
Jun 10 01:18:12 sys-op-dsktp kernel: [   23.499276] SMP motherboard not detected.
Jun 10 01:18:12 sys-op-dsktp kernel: [   23.499281] Local APIC not detected. Using dummy APIC emulation.
Jun 10 01:18:12 sys-op-dsktp kernel: [   23.499396] Brought up 1 CPUs
Jun 10 01:18:12 sys-op-dsktp kernel: [   23.499935] net_namespace: 64 bytes
Jun 10 01:18:12 sys-op-dsktp kernel: [   23.499954] Booting paravirtualized kernel on bare hardware
Jun 10 01:18:12 sys-op-dsktp kernel: [   23.500975] Time: 23:17:34  Date: 06/09/08
Jun 10 01:18:12 sys-op-dsktp kernel: [   23.501054] NET: Registered protocol family 16
Jun 10 01:18:12 sys-op-dsktp kernel: [   23.501579] EISA bus registered
Jun 10 01:18:12 sys-op-dsktp kernel: [   23.501611] ACPI: bus type pci registered
Jun 10 01:18:12 sys-op-dsktp kernel: [   23.504567] PCI: PCI BIOS revision 2.10 entry at 0xf1180, last bus=1
Jun 10 01:18:12 sys-op-dsktp kernel: [   23.504574] PCI: Using configuration type 1
Jun 10 01:18:12 sys-op-dsktp kernel: [   23.504578] Setting up standard PCI resources
Jun 10 01:18:12 sys-op-dsktp kernel: [   23.525867] ACPI: Interpreter enabled
Jun 10 01:18:12 sys-op-dsktp kernel: [   23.525879] ACPI: (supports S0 S1 S4 S5)
Jun 10 01:18:12 sys-op-dsktp kernel: [   23.525907] ACPI: Using PIC for interrupt routing
Jun 10 01:18:12 sys-op-dsktp kernel: [   23.537483] ACPI: PCI Root Bridge [PCI0] (0000:00)
Jun 10 01:18:12 sys-op-dsktp kernel: [   23.537937] PCI quirk: region e400-e4ff claimed by vt82c586 ACPI
Jun 10 01:18:12 sys-op-dsktp kernel: [   23.537944] PCI quirk: region e200-e27f claimed by vt82c686 HW-mon
Jun 10 01:18:12 sys-op-dsktp kernel: [   23.537951] PCI quirk: region e800-e80f claimed by vt82c686 SMB
Jun 10 01:18:12 sys-op-dsktp kernel: [   23.605718] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
Jun 10 01:18:12 sys-op-dsktp kernel: [   23.605877] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
Jun 10 01:18:12 sys-op-dsktp kernel: [   23.606022] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 *4 5 6 7 9 10 11 12 14 15)
Jun 10 01:18:12 sys-op-dsktp kernel: [   23.606164] ACPI: PCI Interrupt Link [LNKD] (IRQs *3 4 5 6 7 9 10 11 12 14 15)
Jun 10 01:18:12 sys-op-dsktp kernel: [   23.606508] Linux Plug and Play Support v0.97 (c) Adam Belay
Jun 10 01:18:12 sys-op-dsktp kernel: [   23.606588] pnp: PnP ACPI init
Jun 10 01:18:12 sys-op-dsktp kernel: [   23.606612] ACPI: bus type pnp registered
Jun 10 01:18:12 sys-op-dsktp kernel: [   23.610789] pnp: PnP ACPI: found 10 devices
Jun 10 01:18:12 sys-op-dsktp kernel: [   23.610800] ACPI: ACPI bus type pnp unregistered
Jun 10 01:18:12 sys-op-dsktp kernel: [   23.610809] PnPBIOS: Disabled by ACPI PNP
Jun 10 01:18:12 sys-op-dsktp kernel: [   23.611452] PCI: Using ACPI for IRQ routing
Jun 10 01:18:12 sys-op-dsktp kernel: [   23.611461] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Jun 10 01:18:12 sys-op-dsktp kernel: [   23.628282] NET: Registered protocol family 8
Jun 10 01:18:12 sys-op-dsktp kernel: [   23.628290] NET: Registered protocol family 20
Jun 10 01:18:12 sys-op-dsktp kernel: [   23.628535] AppArmor: AppArmor Filesystem Enabled
Jun 10 01:18:12 sys-op-dsktp kernel: [   23.632161] Time: tsc clocksource has been installed.
Jun 10 01:18:12 sys-op-dsktp kernel: [   23.640305] system 00:00: iomem range 0x0-0x9ffff could not be reserved
Jun 10 01:18:12 sys-op-dsktp kernel: [   23.640314] system 00:00: iomem range 0xf0000-0xfffff could not be reserved
Jun 10 01:18:12 sys-op-dsktp kernel: [   23.640320] system 00:00: iomem range 0x100000-0x1fffffff could not be reserved
Jun 10 01:18:12 sys-op-dsktp kernel: [   23.640327] system 00:00: iomem range 0xfffe0000-0xffffffff could not be reserved
Jun 10 01:18:12 sys-op-dsktp kernel: [   23.640345] system 00:02: ioport range 0x3f0-0x3f1 has been reserved
Jun 10 01:18:12 sys-op-dsktp kernel: [   23.640351] system 00:02: ioport range 0x4d0-0x4d1 has been reserved
Jun 10 01:18:12 sys-op-dsktp kernel: [   23.640365] system 00:03: ioport range 0xe400-0xe47f has been reserved
Jun 10 01:18:12 sys-op-dsktp kernel: [   23.640371] system 00:03: ioport range 0xe800-0xe80f has been reserved
Jun 10 01:18:12 sys-op-dsktp kernel: [   23.671372] PCI: Bridge: 0000:00:01.0
Jun 10 01:18:12 sys-op-dsktp kernel: [   23.671381]   IO window: d000-dfff
Jun 10 01:18:12 sys-op-dsktp kernel: [   23.671388]   MEM window: c6800000-c7efffff
Jun 10 01:18:12 sys-op-dsktp kernel: [   23.671394]   PREFETCH window: c8000000-dfffffff
Jun 10 01:18:12 sys-op-dsktp kernel: [   23.671451] NET: Registered protocol family 2
Jun 10 01:18:12 sys-op-dsktp kernel: [   23.708294] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
Jun 10 01:18:12 sys-op-dsktp kernel: [   23.708790] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
Jun 10 01:18:12 sys-op-dsktp kernel: [   23.709181] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
Jun 10 01:18:12 sys-op-dsktp kernel: [   23.709567] TCP: Hash tables configured (established 16384 bind 16384)
Jun 10 01:18:12 sys-op-dsktp kernel: [   23.709576] TCP reno registered
Jun 10 01:18:12 sys-op-dsktp kernel: [   23.720426] checking if image is initramfs...<7>Switched to high resolution mode on CPU 0
Jun 10 01:18:12 sys-op-dsktp kernel: [   24.274980]  it is
Jun 10 01:18:12 sys-op-dsktp kernel: [   24.959351] Freeing initrd memory: 7288k freed
Jun 10 01:18:12 sys-op-dsktp kernel: [   24.959723] Simple Boot Flag at 0x3a set to 0x1
Jun 10 01:18:12 sys-op-dsktp kernel: [   24.960731] audit: initializing netlink socket (disabled)
Jun 10 01:18:12 sys-op-dsktp kernel: [   24.960765] audit(1213053455.228:1): initialized
Jun 10 01:18:12 sys-op-dsktp kernel: [   24.965374] VFS: Disk quotas dquot_6.5.1
Jun 10 01:18:12 sys-op-dsktp kernel: [   24.965578] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Jun 10 01:18:12 sys-op-dsktp kernel: [   24.965964] io scheduler noop registered
Jun 10 01:18:12 sys-op-dsktp kernel: [   24.965971] io scheduler anticipatory registered
Jun 10 01:18:12 sys-op-dsktp kernel: [   24.965975] io scheduler deadline registered
Jun 10 01:18:12 sys-op-dsktp kernel: [   24.966005] io scheduler cfq registered (default)
Jun 10 01:18:12 sys-op-dsktp kernel: [   24.966037] PCI: VIA PCI bridge detected. Disabling DAC.
Jun 10 01:18:12 sys-op-dsktp kernel: [   24.966044] PCI: Disabling Via external APIC routing
Jun 10 01:18:12 sys-op-dsktp kernel: [   24.966765] isapnp: Scanning for PnP cards...
Jun 10 01:18:12 sys-op-dsktp kernel: [   25.321110] isapnp: No Plug & Play device found
Jun 10 01:18:12 sys-op-dsktp kernel: [   25.451410] Real Time Clock Driver v1.12ac
Jun 10 01:18:12 sys-op-dsktp kernel: [   25.451614] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Jun 10 01:18:12 sys-op-dsktp kernel: [   25.454733] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Jun 10 01:18:12 sys-op-dsktp kernel: [   25.454902] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Jun 10 01:18:12 sys-op-dsktp kernel: [   25.455131] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
Jun 10 01:18:12 sys-op-dsktp kernel: [   25.455138] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
Jun 10 01:18:12 sys-op-dsktp kernel: [   25.455371] serio: i8042 KBD port at 0x60,0x64 irq 1
Jun 10 01:18:12 sys-op-dsktp kernel: [   25.466872] mice: PS/2 mouse device common for all mice
Jun 10 01:18:12 sys-op-dsktp kernel: [   25.467177] EISA: Probing bus 0 at eisa.0
Jun 10 01:18:12 sys-op-dsktp kernel: [   25.467223] Cannot allocate resource for EISA slot 7
Jun 10 01:18:12 sys-op-dsktp kernel: [   25.467227] Cannot allocate resource for EISA slot 8
Jun 10 01:18:12 sys-op-dsktp kernel: [   25.467231] EISA: Detected 0 cards.
Jun 10 01:18:12 sys-op-dsktp kernel: [   25.467238] cpuidle: using governor ladder
Jun 10 01:18:12 sys-op-dsktp kernel: [   25.467242] cpuidle: using governor menu
Jun 10 01:18:12 sys-op-dsktp kernel: [   25.467596] NET: Registered protocol family 1
Jun 10 01:18:12 sys-op-dsktp kernel: [   25.467666] Using IPI No-Shortcut mode
Jun 10 01:18:12 sys-op-dsktp kernel: [   25.467754] registered taskstats version 1
Jun 10 01:18:12 sys-op-dsktp kernel: [   25.467950]   Magic number: 12:834:301
Jun 10 01:18:12 sys-op-dsktp kernel: [   25.468230]   hash matches device tty30
Jun 10 01:18:12 sys-op-dsktp kernel: [   25.468288] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Jun 10 01:18:12 sys-op-dsktp kernel: [   25.468292] EDD information not available.
Jun 10 01:18:12 sys-op-dsktp kernel: [   25.469293] Freeing unused kernel memory: 368k freed
Jun 10 01:18:12 sys-op-dsktp kernel: [   25.510600] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
Jun 10 01:18:12 sys-op-dsktp kernel: [   27.098640] fuse init (API version 7.9)
Jun 10 01:18:12 sys-op-dsktp kernel: [   27.154213] ACPI: CPU0 (power states: C1[C1] C2[C2])
Jun 10 01:18:12 sys-op-dsktp kernel: [   27.154227] ACPI: Processor [CPU0] (supports 16 throttling states)
Jun 10 01:18:12 sys-op-dsktp kernel: [   27.892587] SCSI subsystem initialized
Jun 10 01:18:12 sys-op-dsktp kernel: [   28.168109] scsi0 : pata_via
Jun 10 01:18:12 sys-op-dsktp kernel: [   28.184130] scsi1 : pata_via
Jun 10 01:18:12 sys-op-dsktp kernel: [   28.185218] ata1: PATA max UDMA/66 cmd 0x1f0 ctl 0x3f6 bmdma 0xb800 irq 14
Jun 10 01:18:12 sys-op-dsktp kernel: [   28.185226] ata2: PATA max UDMA/66 cmd 0x170 ctl 0x376 bmdma 0xb808 irq 15
Jun 10 01:18:12 sys-op-dsktp kernel: [   28.240178] usbcore: registered new interface driver usbfs
Jun 10 01:18:12 sys-op-dsktp kernel: [   28.240229] usbcore: registered new interface driver hub
Jun 10 01:18:12 sys-op-dsktp kernel: [   28.264076] usbcore: registered new device driver usb
Jun 10 01:18:12 sys-op-dsktp kernel: [   28.284060] USB Universal Host Controller Interface driver v3.0
Jun 10 01:18:12 sys-op-dsktp kernel: [   28.513022] ata1.00: ATA-6: WDC WD800JB-00FSA0, 77.07W77, max UDMA/100
Jun 10 01:18:12 sys-op-dsktp kernel: [   28.513034] ata1.00: 156301488 sectors, multi 16: LBA48 
Jun 10 01:18:12 sys-op-dsktp kernel: [   28.513075] ata1.01: ATAPI: TOSHIBA DVD-ROM SD-M1712, 1004, max UDMA/33
Jun 10 01:18:12 sys-op-dsktp kernel: [   28.530490] ata1.00: configured for UDMA/66
Jun 10 01:18:12 sys-op-dsktp kernel: [   28.634365] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Jun 10 01:18:12 sys-op-dsktp kernel: [   28.634382] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Jun 10 01:18:12 sys-op-dsktp kernel: [   28.747903] ata1.01: configured for UDMA/33
Jun 10 01:18:12 sys-op-dsktp kernel: [   28.883592] Floppy drive(s): fd0 is 1.44M
Jun 10 01:18:12 sys-op-dsktp kernel: [   28.903161] FDC 0 is a post-1991 82077
Jun 10 01:18:12 sys-op-dsktp kernel: [   29.223640] ata2.00: ATAPI: ASUS    CD-S520/A5, 1.1, max UDMA/33
Jun 10 01:18:12 sys-op-dsktp kernel: [   29.223684] ata2.01: ATAPI: Hewlett-Packard DVD Writer 300, 1.25, max UDMA/33
Jun 10 01:18:12 sys-op-dsktp kernel: [   29.395263] ata2.00: configured for UDMA/33
Jun 10 01:18:12 sys-op-dsktp kernel: [   29.568732] ata2.01: configured for UDMA/33
Jun 10 01:18:12 sys-op-dsktp kernel: [   29.569035] scsi 0:0:0:0: Direct-Access     ATA      WDC WD800JB-00FS 77.0 PQ: 0 ANSI: 5
Jun 10 01:18:12 sys-op-dsktp kernel: [   29.605794] scsi 0:0:1:0: CD-ROM            TOSHIBA  DVD-ROM SD-M1712 1004 PQ: 0 ANSI: 5
Jun 10 01:18:12 sys-op-dsktp kernel: [   29.606394] scsi 1:0:0:0: CD-ROM            ASUS     CD-S520/A5       1.1  PQ: 0 ANSI: 5
Jun 10 01:18:12 sys-op-dsktp kernel: [   29.609637] scsi 1:0:1:0: CD-ROM            HP       DVD Writer 300n  1.25 PQ: 0 ANSI: 5
Jun 10 01:18:12 sys-op-dsktp kernel: [   29.610646] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 3
Jun 10 01:18:12 sys-op-dsktp kernel: [   29.610664] ACPI: PCI Interrupt 0000:00:04.2[D] -> Link [LNKD] -> GSI 3 (level, low) -> IRQ 3
Jun 10 01:18:12 sys-op-dsktp kernel: [   29.610691] uhci_hcd 0000:00:04.2: UHCI Host Controller
Jun 10 01:18:12 sys-op-dsktp kernel: [   29.611531] uhci_hcd 0000:00:04.2: new USB bus registered, assigned bus number 1
Jun 10 01:18:12 sys-op-dsktp kernel: [   29.611579] uhci_hcd 0000:00:04.2: irq 3, io base 0x0000b400
Jun 10 01:18:12 sys-op-dsktp kernel: [   29.611920] usb usb1: configuration #1 chosen from 1 choice
Jun 10 01:18:12 sys-op-dsktp kernel: [   29.611972] hub 1-0:1.0: USB hub found
Jun 10 01:18:12 sys-op-dsktp kernel: [   29.611986] hub 1-0:1.0: 2 ports detected
Jun 10 01:18:12 sys-op-dsktp kernel: [   29.714975] ACPI: PCI Interrupt 0000:00:04.3[D] -> Link [LNKD] -> GSI 3 (level, low) -> IRQ 3
Jun 10 01:18:12 sys-op-dsktp kernel: [   29.715005] uhci_hcd 0000:00:04.3: UHCI Host Controller
Jun 10 01:18:12 sys-op-dsktp kernel: [   29.715060] uhci_hcd 0000:00:04.3: new USB bus registered, assigned bus number 2
Jun 10 01:18:12 sys-op-dsktp kernel: [   29.715096] uhci_hcd 0000:00:04.3: irq 3, io base 0x0000b000
Jun 10 01:18:12 sys-op-dsktp kernel: [   29.715347] usb usb2: configuration #1 chosen from 1 choice
Jun 10 01:18:12 sys-op-dsktp kernel: [   29.715406] hub 2-0:1.0: USB hub found
Jun 10 01:18:12 sys-op-dsktp kernel: [   29.715420] hub 2-0:1.0: 2 ports detected
Jun 10 01:18:12 sys-op-dsktp kernel: [   29.819715] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 10
Jun 10 01:18:12 sys-op-dsktp kernel: [   29.819735] ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
Jun 10 01:18:12 sys-op-dsktp kernel: [   29.819751] 3c59x: Donald Becker and others.
Jun 10 01:18:12 sys-op-dsktp kernel: [   29.819765] 0000:00:0b.0: 3Com PCI 3c905C Tornado at e081e000.
Jun 10 01:18:12 sys-op-dsktp kernel: [   29.842974] PDC20265: IDE controller (0x105a:0x0d30 rev 0x02) at  PCI slot 0000:00:11.0
Jun 10 01:18:12 sys-op-dsktp kernel: [   29.843017] ACPI: PCI Interrupt 0000:00:11.0[A] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
Jun 10 01:18:12 sys-op-dsktp kernel: [   29.843037] PDC20265: 100% native mode on irq 10
Jun 10 01:18:12 sys-op-dsktp kernel: [   29.843050] PDC20265: (U)DMA Burst Bit DISABLED Primary PCI Mode Secondary PCI Mode.
Jun 10 01:18:12 sys-op-dsktp kernel: [   29.843055] PDC20265: FORCING BURST BIT 0x00->0x01 ACTIVE
Jun 10 01:18:12 sys-op-dsktp kernel: [   29.843062]     ide2: BM-DMA at 0x7800-0x7807, BIOS settings: hde:pio, hdf:DMA
Jun 10 01:18:12 sys-op-dsktp kernel: [   29.843083]     ide3: BM-DMA at 0x7808-0x780f, BIOS settings: hdg:pio, hdh:pio
Jun 10 01:18:12 sys-op-dsktp kernel: [   29.954584] usb 1-1: new low speed USB device using uhci_hcd and address 2
Jun 10 01:18:12 sys-op-dsktp kernel: [   30.131382] usb 1-1: configuration #1 chosen from 1 choice
Jun 10 01:18:12 sys-op-dsktp kernel: [   30.374118] usb 1-2: new full speed USB device using uhci_hcd and address 3
Jun 10 01:18:12 sys-op-dsktp kernel: [   30.471354] Driver 'sd' needs updating - please use bus_type methods
Jun 10 01:18:12 sys-op-dsktp kernel: [   30.473925] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
Jun 10 01:18:12 sys-op-dsktp kernel: [   30.474028] sd 0:0:0:0: [sda] Write Protect is off
Jun 10 01:18:12 sys-op-dsktp kernel: [   30.474076] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jun 10 01:18:12 sys-op-dsktp kernel: [   30.474197] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
Jun 10 01:18:12 sys-op-dsktp kernel: [   30.474220] sd 0:0:0:0: [sda] Write Protect is off
Jun 10 01:18:12 sys-op-dsktp kernel: [   30.474261] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Jun 10 01:18:12 sys-op-dsktp kernel: [   30.474273]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
Jun 10 01:18:12 sys-op-dsktp kernel: [   30.491829]  sda1 sda2 < sda5 >
Jun 10 01:18:12 sys-op-dsktp kernel: [   30.518306] sd 0:0:0:0: [sda] Attached SCSI disk
Jun 10 01:18:12 sys-op-dsktp kernel: [   30.538291] sd 0:0:0:0: Attached scsi generic sg0 type 0
Jun 10 01:18:12 sys-op-dsktp kernel: [   30.538337] sr 0:0:1:0: Attached scsi generic sg1 type 5
Jun 10 01:18:12 sys-op-dsktp kernel: [   30.538375] scsi 1:0:0:0: Attached scsi generic sg2 type 5
Jun 10 01:18:12 sys-op-dsktp kernel: [   30.538411] scsi 1:0:1:0: Attached scsi generic sg3 type 5
Jun 10 01:18:12 sys-op-dsktp kernel: [   30.569361] sr0: scsi3-mmc drive: 48x/48x cd/rw xa/form2 cdda tray
Jun 10 01:18:12 sys-op-dsktp kernel: [   30.569375] Uniform CD-ROM driver Revision: 3.20
Jun 10 01:18:12 sys-op-dsktp kernel: [   30.573572] sr1: scsi3-mmc drive: 0x/52x cd/rw xa/form2 cdda tray
Jun 10 01:18:12 sys-op-dsktp kernel: [   30.579051] sr2: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
Jun 10 01:18:12 sys-op-dsktp kernel: [   30.607874] usb 1-2: configuration #1 chosen from 1 choice
Jun 10 01:18:12 sys-op-dsktp kernel: [   30.977862] usb 2-2: new full speed USB device using uhci_hcd and address 2
Jun 10 01:18:12 sys-op-dsktp kernel: [   31.146946] usb 2-2: configuration #1 chosen from 1 choice
Jun 10 01:18:12 sys-op-dsktp kernel: [   31.149227] hub 2-2:1.0: USB hub found
Jun 10 01:18:12 sys-op-dsktp kernel: [   31.150748] hub 2-2:1.0: 4 ports detected
Jun 10 01:18:12 sys-op-dsktp kernel: [   31.219229] Attempting manual resume
Jun 10 01:18:12 sys-op-dsktp kernel: [   31.261771] usbcore: registered new interface driver hiddev
Jun 10 01:18:12 sys-op-dsktp kernel: [   31.274496] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:04.2/usb1/1-1/1-1:1.0/input/input2
Jun 10 01:18:12 sys-op-dsktp kernel: [   31.289393] input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:04.2-1
Jun 10 01:18:12 sys-op-dsktp kernel: [   31.289443] usbcore: registered new interface driver usbhid
Jun 10 01:18:12 sys-op-dsktp kernel: [   31.289451] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
Jun 10 01:18:12 sys-op-dsktp kernel: [   31.297293] kjournald starting.  Commit interval 5 seconds
Jun 10 01:18:12 sys-op-dsktp kernel: [   31.297342] EXT3-fs: mounted filesystem with ordered data mode.
Jun 10 01:18:12 sys-op-dsktp kernel: [   42.354382] ip_tables: (C) 2000-2006 Netfilter Core Team
Jun 10 01:18:12 sys-op-dsktp kernel: [   42.420111] nf_conntrack version 0.5.0 (8192 buckets, 32768 max)
Jun 10 01:18:12 sys-op-dsktp kernel: [   44.962053] Linux agpgart interface v0.102
Jun 10 01:18:12 sys-op-dsktp kernel: [   45.029082] agpgart: Detected VIA Twister-K/KT133x/KM133 chipset
Jun 10 01:18:12 sys-op-dsktp kernel: [   45.108846] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jun 10 01:18:12 sys-op-dsktp kernel: [   45.160915] agpgart: AGP aperture is 128M @ 0xe0000000
Jun 10 01:18:12 sys-op-dsktp kernel: [   45.177734] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Jun 10 01:18:12 sys-op-dsktp kernel: [   45.287047] parport_pc: VIA parallel port disabled in BIOS
Jun 10 01:18:12 sys-op-dsktp kernel: [   45.592622] via686a 0000:00:04.4: Sensors disabled, enable with force_addr=0xe200
Jun 10 01:18:12 sys-op-dsktp kernel: [   46.165158] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 4
Jun 10 01:18:12 sys-op-dsktp kernel: [   46.165179] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [LNKC] -> GSI 4 (level, low) -> IRQ 4
Jun 10 01:18:12 sys-op-dsktp kernel: [   46.312087] input: PC Speaker as /devices/platform/pcspkr/input/input3
Jun 10 01:18:12 sys-op-dsktp kernel: [   46.991546] input: Power Button (FF) as /devices/virtual/input/input4
Jun 10 01:18:12 sys-op-dsktp kernel: [   47.003011] ACPI: Power Button (FF) [PWRF]
Jun 10 01:18:12 sys-op-dsktp kernel: [   47.003295] input: Power Button (CM) as /devices/virtual/input/input5
Jun 10 01:18:12 sys-op-dsktp kernel: [   47.038976] ACPI: Power Button (CM) [PWRB]
Jun 10 01:18:12 sys-op-dsktp kernel: [   50.511474] Linux video capture interface: v2.00
Jun 10 01:18:12 sys-op-dsktp kernel: [   50.572241] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/gspcav1/gspca_core.c: USB GSPCA camera found. (PAC207)
Jun 10 01:18:12 sys-op-dsktp kernel: [   50.577137] usbcore: registered new interface driver gspca
Jun 10 01:18:12 sys-op-dsktp kernel: [   50.577152] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/gspcav1/gspca_core.c: gspca driver 01.00.20 registered
Jun 10 01:18:12 sys-op-dsktp kernel: [   55.032011] lp: driver loaded but no devices found
Jun 10 01:18:12 sys-op-dsktp kernel: [   55.169468] Adding 1510068k swap on /dev/sda5.  Priority:-1 extents:1 across:1510068k
Jun 10 01:18:12 sys-op-dsktp kernel: [   55.824366] EXT3 FS on sda1, internal journal
Jun 10 01:18:12 sys-op-dsktp kernel: [   59.315453] No dock devices found.
Jun 10 01:18:12 sys-op-dsktp kernel: [   61.587243] NET: Registered protocol family 10
Jun 10 01:18:12 sys-op-dsktp kernel: [   61.588525] lo: Disabled Privacy Extensions
Jun 10 01:18:15 sys-op-dsktp kernel: [   64.622078] ppdev: user-space parallel port driver
Jun 10 01:18:15 sys-op-dsktp kernel: [   64.762774] audit(1213053495.953:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5047 profile="/usr/sbin/cupsd" namespace="default"
Jun 10 01:18:16 sys-op-dsktp dhcdbd: Started up.
Jun 10 01:18:20 sys-op-dsktp kernel: [   69.135815] eth0:  setting half-duplex.
Jun 10 01:18:20 sys-op-dsktp kernel: [   69.269717] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun 10 01:18:20 sys-op-dsktp dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Jun 10 01:18:21 sys-op-dsktp kernel: [   70.644701] NET: Registered protocol family 17
Jun 10 01:18:22 sys-op-dsktp kernel: [   71.524670] [drm] Initialized drm 1.1.0 20060810
Jun 10 01:18:22 sys-op-dsktp kernel: [   71.567028] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
Jun 10 01:18:22 sys-op-dsktp kernel: [   71.567055] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
Jun 10 01:18:22 sys-op-dsktp kernel: [   71.567280] [drm] Initialized radeon 1.28.0 20060524 on minor 0
Jun 10 01:18:24 sys-op-dsktp kernel: [   73.256991] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
Jun 10 01:18:24 sys-op-dsktp kernel: [   73.257625] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
Jun 10 01:18:24 sys-op-dsktp kernel: [   73.258080] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
Jun 10 01:18:24 sys-op-dsktp kernel: [   73.640209] [drm] Setting GART location based on new memory map
Jun 10 01:18:24 sys-op-dsktp kernel: [   73.640237] [drm] Loading R200 Microcode
Jun 10 01:18:24 sys-op-dsktp kernel: [   73.640286] [drm] writeback test succeeded in 1 usecs
Jun 10 01:18:56 sys-op-dsktp dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.reason
Jun 10 01:18:59 sys-op-dsktp kernel: [  108.725313] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Jun 10 01:19:06 sys-op-dsktp dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.host_name
Jun 10 01:19:06 sys-op-dsktp dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.nis_domain
Jun 10 01:19:06 sys-op-dsktp dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.nis_servers
Jun 10 01:19:06 sys-op-dsktp dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.interface_mtu
Jun 10 01:19:09 sys-op-dsktp kernel: [  118.569695] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=81.22.86.146 DST=192.168.2.5 LEN=71 TOS=0x00 PREC=0x00 TTL=52 ID=15253 PROTO=UDP SPT=60767 DPT=15684 LEN=51 
Jun 10 01:19:10 sys-op-dsktp kernel: [  118.815950] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=203.219.71.74 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=112 ID=34933 PROTO=UDP SPT=48673 DPT=15684 LEN=71 
Jun 10 01:19:11 sys-op-dsktp kernel: [  120.632856] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=78.16.167.37 DST=192.168.2.5 LEN=70 TOS=0x00 PREC=0x00 TTL=115 ID=6851 PROTO=UDP SPT=24467 DPT=15684 LEN=50 
Jun 10 01:19:12 sys-op-dsktp kernel: [  121.481130] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=81.152.84.239 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=107 ID=5922 PROTO=UDP SPT=65245 DPT=15684 LEN=71 
Jun 10 01:19:14 sys-op-dsktp kernel: [  123.194114] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=86.97.72.195 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=115 ID=25127 PROTO=UDP SPT=12464 DPT=15684 LEN=71 
Jun 10 01:19:14 sys-op-dsktp kernel: [  123.471659] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=86.69.180.134 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=115 ID=57518 PROTO=UDP SPT=56931 DPT=15684 LEN=71 
Jun 10 01:19:14 sys-op-dsktp kernel: [  123.585647] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=81.224.255.170 DST=192.168.2.5 LEN=70 TOS=0x00 PREC=0x00 TTL=118 ID=39336 PROTO=UDP SPT=33650 DPT=15684 LEN=50 
Jun 10 01:19:18 sys-op-dsktp kernel: [  127.448011] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=24.196.82.40 DST=192.168.2.5 LEN=70 TOS=0x00 PREC=0x00 TTL=49 ID=26975 PROTO=UDP SPT=58661 DPT=15684 LEN=50 
Jun 10 01:19:18 sys-op-dsktp kernel: [  127.605913] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=125.14.21.75 DST=192.168.2.5 LEN=93 TOS=0x00 PREC=0x00 TTL=46 ID=53516 PROTO=UDP SPT=65028 DPT=15684 LEN=73 
Jun 10 01:19:22 sys-op-dsktp kernel: [  131.346615] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=217.226.75.39 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=118 ID=25550 PROTO=UDP SPT=57048 DPT=15684 LEN=71 
Jun 10 01:19:23 sys-op-dsktp kernel: [  132.681786] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=124.170.179.174 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=111 ID=13282 PROTO=UDP SPT=50100 DPT=15684 LEN=71 
Jun 10 01:19:26 sys-op-dsktp kernel: [  135.569205] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=84.59.53.36 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=117 ID=42312 PROTO=UDP SPT=18495 DPT=15684 LEN=71 
Jun 10 01:19:28 sys-op-dsktp kernel: [  137.279484] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=90.227.89.211 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=118 ID=17215 PROTO=UDP SPT=11815 DPT=15684 LEN=71 
Jun 10 01:19:31 sys-op-dsktp kernel: [  140.345559] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=24.196.82.40 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=49 ID=5154 PROTO=UDP SPT=58661 DPT=15684 LEN=71 
Jun 10 01:19:34 sys-op-dsktp kernel: [  143.463417] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=208.120.61.198 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=113 ID=51798 PROTO=UDP SPT=21078 DPT=15684 LEN=71 
Jun 10 01:19:36 sys-op-dsktp kernel: [  144.803223] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=84.217.140.207 DST=192.168.2.5 LEN=70 TOS=0x00 PREC=0x00 TTL=118 ID=33012 PROTO=UDP SPT=21 DPT=15684 LEN=50 
Jun 10 01:19:37 sys-op-dsktp kernel: [  146.017234] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=217.226.75.39 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=118 ID=26281 PROTO=UDP SPT=57048 DPT=15684 LEN=71 
Jun 10 01:19:37 sys-op-dsktp kernel: [  146.625625] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=83.109.241.97 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=118 ID=13131 PROTO=UDP SPT=5000 DPT=15684 LEN=71 
Jun 10 01:19:38 sys-op-dsktp kernel: [  147.329893] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=67.161.190.204 DST=192.168.2.5 LEN=70 TOS=0x00 PREC=0x00 TTL=42 ID=56533 PROTO=UDP SPT=55126 DPT=15684 LEN=50 
Jun 10 01:19:39 sys-op-dsktp kernel: [  147.769381] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=81.224.255.170 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=118 ID=41655 PROTO=UDP SPT=33650 DPT=15684 LEN=71 
Jun 10 01:19:42 sys-op-dsktp kernel: [  151.386000] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=72.198.36.210 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=118 ID=3628 PROTO=UDP SPT=39283 DPT=15684 LEN=71 
Jun 10 01:19:42 sys-op-dsktp kernel: [  151.609599] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=97.101.188.231 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=113 ID=40362 PROTO=UDP SPT=49812 DPT=15684 LEN=71 
Jun 10 01:19:44 sys-op-dsktp kernel: [  153.146159] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=90.193.125.94 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=116 ID=23708 PROTO=UDP SPT=59148 DPT=15684 LEN=71 
Jun 10 01:19:46 sys-op-dsktp kernel: [  154.821980] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=75.148.160.117 DST=192.168.2.5 LEN=93 TOS=0x00 PREC=0x00 TTL=42 ID=25206 PROTO=UDP SPT=40732 DPT=15684 LEN=73 
Jun 10 01:19:54 sys-op-dsktp kernel: [  163.331430] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=91.113.127.4 DST=192.168.2.5 LEN=93 TOS=0x00 PREC=0x00 TTL=121 ID=1865 PROTO=UDP SPT=47450 DPT=15684 LEN=73 
Jun 10 01:19:56 sys-op-dsktp kernel: [  165.309872] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=24.200.93.126 DST=192.168.2.5 LEN=95 TOS=0x00 PREC=0x00 TTL=109 ID=1590 PROTO=UDP SPT=55569 DPT=15684 LEN=75 
Jun 10 01:20:04 sys-op-dsktp kernel: [  172.873706] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=86.150.110.67 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=108 ID=53207 PROTO=UDP SPT=56194 DPT=15684 LEN=71 
Jun 10 01:20:04 sys-op-dsktp kernel: [  173.534156] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=71.138.128.172 DST=192.168.2.5 LEN=93 TOS=0x00 PREC=0x00 TTL=116 ID=17354 PROTO=UDP SPT=35782 DPT=15684 LEN=73 
Jun 10 01:20:04 sys-op-dsktp kernel: [  173.554302] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=81.224.255.170 DST=192.168.2.5 LEN=70 TOS=0x00 PREC=0x00 TTL=118 ID=44056 PROTO=UDP SPT=33650 DPT=15684 LEN=50 
Jun 10 01:20:07 sys-op-dsktp kernel: [  175.774846] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=84.60.172.232 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=54 ID=53581 PROTO=UDP SPT=55243 DPT=15684 LEN=71 
Jun 10 01:20:09 sys-op-dsktp kernel: [  178.232528] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=76.205.78.73 DST=192.168.2.5 LEN=93 TOS=0x00 PREC=0x00 TTL=115 ID=56194 PROTO=UDP SPT=42532 DPT=15684 LEN=73 
Jun 10 01:20:11 sys-op-dsktp kernel: [  180.699552] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=190.46.217.41 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=118 ID=11340 PROTO=UDP SPT=51503 DPT=15684 LEN=71 
Jun 10 01:20:12 sys-op-dsktp kernel: [  180.857046] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=69.123.212.253 DST=192.168.2.5 LEN=71 TOS=0x00 PREC=0x00 TTL=113 ID=47635 PROTO=UDP SPT=19099 DPT=15684 LEN=51 
Jun 10 01:20:12 sys-op-dsktp kernel: [  181.495583] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=84.217.140.207 DST=192.168.2.5 LEN=70 TOS=0x00 PREC=0x00 TTL=118 ID=33220 PROTO=UDP SPT=21 DPT=15684 LEN=50 
Jun 10 01:20:15 sys-op-dsktp kernel: [  183.848950] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=82.224.158.206 DST=192.168.2.5 LEN=93 TOS=0x00 PREC=0x00 TTL=54 ID=57797 PROTO=UDP SPT=36675 DPT=15684 LEN=73 
Jun 10 01:20:16 sys-op-dsktp kernel: [  185.036593] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=24.160.245.68 DST=192.168.2.5 LEN=93 TOS=0x00 PREC=0x00 TTL=50 ID=60887 PROTO=UDP SPT=59969 DPT=15684 LEN=73 
Jun 10 01:20:16 sys-op-dsktp kernel: [  185.377739] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=69.63.16.42 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=111 ID=34195 PROTO=UDP SPT=14596 DPT=15684 LEN=71 
Jun 10 01:20:16 sys-op-dsktp kernel: [  185.456005] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=72.198.36.210 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=118 ID=5912 PROTO=UDP SPT=39283 DPT=15684 LEN=71 
Jun 10 01:20:20 sys-op-dsktp kernel: [  189.387541] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=75.31.252.177 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=117 ID=45214 PROTO=UDP SPT=50002 DPT=15684 LEN=71 
Jun 10 01:20:23 sys-op-dsktp kernel: [  192.112150] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=189.94.109.187 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=47 ID=55489 PROTO=UDP SPT=19125 DPT=15684 LEN=71 
Jun 10 01:20:23 sys-op-dsktp kernel: [  192.699314] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=69.136.108.146 DST=192.168.2.5 LEN=71 TOS=0x00 PREC=0x00 TTL=40 ID=5259 PROTO=UDP SPT=39615 DPT=15684 LEN=51 
Jun 10 01:20:27 sys-op-dsktp kernel: [  195.713865] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=76.64.59.59 DST=192.168.2.5 LEN=93 TOS=0x00 PREC=0x00 TTL=42 ID=44406 PROTO=UDP SPT=48086 DPT=15684 LEN=73 
Jun 10 01:20:27 sys-op-dsktp kernel: [  196.231799] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=69.63.16.42 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=111 ID=63594 PROTO=UDP SPT=14596 DPT=15684 LEN=71 
Jun 10 01:20:27 sys-op-dsktp kernel: [  196.673512] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=217.226.75.39 DST=192.168.2.5 LEN=70 TOS=0x00 PREC=0x00 TTL=118 ID=29090 PROTO=UDP SPT=57048 DPT=15684 LEN=50 
Jun 10 01:20:28 sys-op-dsktp kernel: [  196.980251] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=86.88.130.5 DST=192.168.2.5 LEN=93 TOS=0x00 PREC=0x00 TTL=56 ID=59180 PROTO=UDP SPT=64740 DPT=15684 LEN=73 
Jun 10 01:20:29 sys-op-dsktp kernel: [  197.735353] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=124.98.6.73 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=44 ID=60037 PROTO=UDP SPT=14909 DPT=15684 LEN=71 
Jun 10 01:20:29 sys-op-dsktp kernel: [  198.134132] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=83.101.11.83 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=54 ID=0 DF PROTO=UDP SPT=46131 DPT=15684 LEN=71 
Jun 10 01:20:31 sys-op-dsktp kernel: [  199.872440] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=77.205.20.116 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=117 ID=1645 PROTO=UDP SPT=11202 DPT=15684 LEN=71 
Jun 10 01:20:31 sys-op-dsktp kernel: [  200.612223] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=71.62.171.228 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=104 ID=36428 PROTO=UDP SPT=63782 DPT=15684 LEN=71 
Jun 10 01:20:35 sys-op-dsktp kernel: [  204.053678] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=69.123.212.253 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=113 ID=47849 PROTO=UDP SPT=19099 DPT=15684 LEN=71 
Jun 10 01:20:35 sys-op-dsktp kernel: [  204.203082] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=217.132.249.193 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=117 ID=28072 PROTO=UDP SPT=7846 DPT=15684 LEN=71 
Jun 10 01:20:36 sys-op-dsktp kernel: [  205.117375] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=200.116.19.202 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=113 ID=62516 PROTO=UDP SPT=58073 DPT=15684 LEN=71 
Jun 10 01:20:40 sys-op-dsktp kernel: [  209.264651] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=92.227.178.218 DST=192.168.2.5 LEN=93 TOS=0x00 PREC=0x00 TTL=118 ID=30148 PROTO=UDP SPT=55263 DPT=15684 LEN=73 
Jun 10 01:20:41 sys-op-dsktp kernel: [  209.769135] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=62.143.180.113 DST=192.168.2.5 LEN=93 TOS=0x00 PREC=0x00 TTL=114 ID=10633 PROTO=UDP SPT=45105 DPT=15684 LEN=73 
Jun 10 01:20:42 sys-op-dsktp kernel: [  211.019484] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=77.212.140.91 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=116 ID=19021 PROTO=UDP SPT=14558 DPT=15684 LEN=71 
Jun 10 01:20:42 sys-op-dsktp kernel: [  211.374853] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=80.223.172.62 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=113 ID=7270 PROTO=UDP SPT=48247 DPT=15684 LEN=71 
Jun 10 01:20:43 sys-op-dsktp kernel: [  212.162191] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=41.224.153.123 DST=192.168.2.5 LEN=93 TOS=0x00 PREC=0x00 TTL=108 ID=9631 PROTO=UDP SPT=44745 DPT=15684 LEN=73 
Jun 10 01:20:46 sys-op-dsktp kernel: [  215.357843] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=76.116.194.140 DST=192.168.2.5 LEN=93 TOS=0x00 PREC=0x00 TTL=102 ID=17662 PROTO=UDP SPT=37172 DPT=15684 LEN=73 
Jun 10 01:20:53 sys-op-dsktp kernel: [  222.088997] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=71.232.147.106 DST=192.168.2.5 LEN=70 TOS=0x00 PREC=0x00 TTL=105 ID=12483 PROTO=UDP SPT=38302 DPT=15684 LEN=50 
Jun 10 01:20:53 sys-op-dsktp kernel: [  222.388942] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=75.168.91.212 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=115 ID=29192 PROTO=UDP SPT=62910 DPT=15684 LEN=71 
Jun 10 01:20:56 sys-op-dsktp kernel: [  224.838046] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=88.5.0.35 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=114 ID=4640 PROTO=UDP SPT=18007 DPT=15684 LEN=71 
Jun 10 01:20:56 sys-op-dsktp kernel: [  225.035976] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=87.78.71.197 DST=192.168.2.5 LEN=70 TOS=0x00 PREC=0x00 TTL=118 ID=10664 PROTO=UDP SPT=56412 DPT=15684 LEN=50 
Jun 10 01:20:56 sys-op-dsktp kernel: [  225.046237] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=87.78.71.197 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=118 ID=10673 PROTO=UDP SPT=56412 DPT=15684 LEN=71 
Jun 10 01:20:56 sys-op-dsktp kernel: [  225.124433] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=88.5.0.35 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=114 ID=4667 PROTO=UDP SPT=18007 DPT=15684 LEN=71 
Jun 10 01:20:59 sys-op-dsktp kernel: [  228.410772] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=68.188.36.187 DST=192.168.2.5 LEN=93 TOS=0x00 PREC=0x00 TTL=115 ID=17999 PROTO=UDP SPT=33752 DPT=15684 LEN=73 
Jun 10 01:21:03 sys-op-dsktp kernel: [  232.058982] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=71.191.21.127 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=51 ID=19246 PROTO=UDP SPT=50663 DPT=15684 LEN=71 
Jun 10 01:21:05 sys-op-dsktp kernel: [  233.692657] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=88.165.15.166 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=119 ID=312 PROTO=UDP SPT=32363 DPT=15684 LEN=71 
Jun 10 01:21:05 sys-op-dsktp kernel: [  234.441570] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=84.217.140.207 DST=192.168.2.5 LEN=70 TOS=0x00 PREC=0x00 TTL=118 ID=33560 PROTO=UDP SPT=21 DPT=15684 LEN=50 
Jun 10 01:21:14 sys-op-dsktp kernel: [  242.743929] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=70.136.125.210 DST=192.168.2.5 LEN=93 TOS=0x00 PREC=0x00 TTL=115 ID=28197 PROTO=UDP SPT=59000 DPT=15684 LEN=73 
Jun 10 01:21:14 sys-op-dsktp kernel: [  243.098163] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=69.123.212.253 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=113 ID=48142 PROTO=UDP SPT=19099 DPT=15684 LEN=71 
Jun 10 01:21:15 sys-op-dsktp kernel: [  243.791668] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=72.244.71.68 DST=192.168.2.5 LEN=70 TOS=0x00 PREC=0x00 TTL=50 ID=12090 PROTO=UDP SPT=26107 DPT=15684 LEN=50 
Jun 10 01:21:15 sys-op-dsktp kernel: [  244.092674] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=72.244.71.68 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=50 ID=12103 PROTO=UDP SPT=26107 DPT=15684 LEN=71 
Jun 10 01:21:17 sys-op-dsktp kernel: [  246.337291] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=200.127.242.174 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=106 ID=18741 PROTO=UDP SPT=55831 DPT=15684 LEN=71 
Jun 10 01:21:18 sys-op-dsktp kernel: [  246.776336] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=69.136.108.146 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=40 ID=12731 PROTO=UDP SPT=39615 DPT=15684 LEN=71 
Jun 10 01:21:18 sys-op-dsktp kernel: [  247.128100] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=62.143.159.175 DST=192.168.2.5 LEN=70 TOS=0x00 PREC=0x00 TTL=115 ID=2292 PROTO=UDP SPT=14744 DPT=15684 LEN=50 
Jun 10 01:21:19 sys-op-dsktp kernel: [  248.223283] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=69.123.212.253 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=113 ID=48225 PROTO=UDP SPT=19099 DPT=15684 LEN=71 
Jun 10 01:21:20 sys-op-dsktp kernel: [  248.793380] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=69.123.212.253 DST=192.168.2.5 LEN=71 TOS=0x00 PREC=0x00 TTL=113 ID=48237 PROTO=UDP SPT=19099 DPT=15684 LEN=51 
Jun 10 01:21:21 sys-op-dsktp kernel: [  250.213055] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=77.5.228.165 DST=192.168.2.5 LEN=93 TOS=0x00 PREC=0x00 TTL=115 ID=1257 PROTO=UDP SPT=36624 DPT=15684 LEN=73 
Jun 10 01:21:21 sys-op-dsktp kernel: [  250.213143] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=24.85.74.31 DST=192.168.2.5 LEN=93 TOS=0x00 PREC=0x00 TTL=113 ID=21815 PROTO=UDP SPT=34249 DPT=15684 LEN=73 
Jun 10 01:21:25 sys-op-dsktp kernel: [  253.695698] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=139.78.10.16 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=111 ID=48865 PROTO=UDP SPT=29935 DPT=15684 LEN=71 
Jun 10 01:21:28 sys-op-dsktp kernel: [  257.072171] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=84.48.43.116 DST=192.168.2.5 LEN=93 TOS=0x00 PREC=0x00 TTL=110 ID=25229 PROTO=UDP SPT=63324 DPT=15684 LEN=73 
Jun 10 01:21:29 sys-op-dsktp kernel: [  257.716195] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=24.125.7.85 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=38 ID=31021 PROTO=UDP SPT=34977 DPT=15684 LEN=71 
Jun 10 01:21:31 sys-op-dsktp kernel: [  259.654410] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=92.244.43.220 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=112 ID=58907 PROTO=UDP SPT=49152 DPT=15684 LEN=71 
Jun 10 01:21:31 sys-op-dsktp kernel: [  259.799119] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=82.59.148.77 DST=192.168.2.5 LEN=93 TOS=0x00 PREC=0x00 TTL=115 ID=35029 PROTO=UDP SPT=22675 DPT=15684 LEN=73 
Jun 10 01:21:31 sys-op-dsktp kernel: [  260.422928] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=90.33.189.181 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=113 ID=4219 PROTO=UDP SPT=32449 DPT=15684 LEN=71 
Jun 10 01:21:32 sys-op-dsktp kernel: [  261.607151] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=24.223.140.224 DST=192.168.2.5 LEN=93 TOS=0x00 PREC=0x00 TTL=111 ID=2314 PROTO=UDP SPT=47916 DPT=15684 LEN=73 
Jun 10 01:21:34 sys-op-dsktp kernel: [  263.191718] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=76.92.132.215 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=114 ID=29849 PROTO=UDP SPT=31602 DPT=15684 LEN=71 
Jun 10 01:21:36 sys-op-dsktp kernel: [  264.805564] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=83.249.100.254 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=115 ID=9663 PROTO=UDP SPT=29079 DPT=15684 LEN=71 
Jun 10 01:21:36 sys-op-dsktp kernel: [  265.497399] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=77.205.20.116 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=117 ID=10902 PROTO=UDP SPT=11202 DPT=15684 LEN=71 
Jun 10 01:21:37 sys-op-dsktp kernel: [  266.263701] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=76.200.159.192 DST=192.168.2.5 LEN=93 TOS=0x00 PREC=0x00 TTL=116 ID=36117 PROTO=UDP SPT=28044 DPT=15684 LEN=73 
Jun 10 01:21:41 sys-op-dsktp kernel: [  269.701356] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=82.253.135.149 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=119 ID=28812 PROTO=UDP SPT=27749 DPT=15684 LEN=71 
Jun 10 01:21:41 sys-op-dsktp kernel: [  270.608147] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=62.57.59.226 DST=192.168.2.5 LEN=86 TOS=0x00 PREC=0x00 TTL=115 ID=3904 PROTO=UDP SPT=6881 DPT=15684 LEN=66 
Jun 10 01:21:45 sys-op-dsktp kernel: [  274.493013] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=58.49.193.213 DST=192.168.2.5 LEN=70 TOS=0x00 PREC=0x00 TTL=43 ID=34842 PROTO=UDP SPT=13861 DPT=15684 LEN=50 
Jun 10 01:21:46 sys-op-dsktp kernel: [  274.665754] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=87.78.71.197 DST=192.168.2.5 LEN=70 TOS=0x00 PREC=0x00 TTL=118 ID=29022 PROTO=UDP SPT=56412 DPT=15684 LEN=50 
Jun 10 01:21:47 sys-op-dsktp kernel: [  276.159940] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=96.239.26.250 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=115 ID=64240 PROTO=UDP SPT=37251 DPT=15684 LEN=71 
Jun 10 01:21:49 sys-op-dsktp kernel: [  277.774693] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=88.5.0.35 DST=192.168.2.5 LEN=70 TOS=0x00 PREC=0x00 TTL=114 ID=8481 PROTO=UDP SPT=18007 DPT=15684 LEN=50 
Jun 10 01:21:51 sys-op-dsktp kernel: [  279.785377] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=69.123.212.253 DST=192.168.2.5 LEN=71 TOS=0x00 PREC=0x00 TTL=113 ID=48476 PROTO=UDP SPT=19099 DPT=15684 LEN=51 
Jun 10 01:21:52 sys-op-dsktp kernel: [  281.143207] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=210.214.26.15 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=110 ID=11113 PROTO=UDP SPT=56322 DPT=15684 LEN=71 
Jun 10 01:21:53 sys-op-dsktp kernel: [  282.171953] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=69.144.46.207 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=44 ID=57204 PROTO=UDP SPT=63814 DPT=15684 LEN=71 
Jun 10 01:21:54 sys-op-dsktp kernel: [  282.989874] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=71.201.121.220 DST=192.168.2.5 LEN=93 TOS=0x00 PREC=0x00 TTL=42 ID=49963 PROTO=UDP SPT=18988 DPT=15684 LEN=73 
Jun 10 01:21:59 sys-op-dsktp kernel: [  287.636100] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=74.71.127.203 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=49 ID=62180 PROTO=UDP SPT=29015 DPT=15684 LEN=71 
Jun 10 01:22:01 sys-op-dsktp kernel: [  290.123942] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=193.43.223.132 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=112 ID=51903 PROTO=UDP SPT=59500 DPT=15684 LEN=71 
Jun 10 01:22:02 sys-op-dsktp kernel: [  291.095525] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=76.21.16.39 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=108 ID=12889 PROTO=UDP SPT=16118 DPT=15684 LEN=71 
Jun 10 01:22:08 sys-op-dsktp kernel: [  296.620158] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=69.140.117.243 DST=192.168.2.5 LEN=93 TOS=0x00 PREC=0x00 TTL=40 ID=5274 PROTO=UDP SPT=65535 DPT=15684 LEN=73 
Jun 10 01:22:09 sys-op-dsktp kernel: [  297.815994] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=220.240.200.130 DST=192.168.2.5 LEN=93 TOS=0x00 PREC=0x00 TTL=111 ID=42970 PROTO=UDP SPT=12397 DPT=15684 LEN=73 
Jun 10 01:22:09 sys-op-dsktp kernel: [  298.499276] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=76.117.41.19 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=39 ID=43028 PROTO=UDP SPT=54545 DPT=15684 LEN=71 
Jun 10 01:22:10 sys-op-dsktp kernel: [  298.982685] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=70.58.61.150 DST=192.168.2.5 LEN=93 TOS=0x00 PREC=0x00 TTL=114 ID=26830 PROTO=UDP SPT=10420 DPT=15684 LEN=73 
Jun 10 01:22:10 sys-op-dsktp kernel: [  299.231561] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=98.207.153.252 DST=192.168.2.5 LEN=93 TOS=0x00 PREC=0x00 TTL=107 ID=59433 PROTO=UDP SPT=16870 DPT=15684 LEN=73 
Jun 10 01:22:15 sys-op-dsktp kernel: [  304.526244] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=71.135.39.231 DST=192.168.2.5 LEN=93 TOS=0x00 PREC=0x00 TTL=116 ID=6935 PROTO=UDP SPT=53082 DPT=15684 LEN=73 
Jun 10 01:22:16 sys-op-dsktp kernel: [  304.765253] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=84.56.223.88 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=116 ID=46745 PROTO=UDP SPT=19552 DPT=15684 LEN=71 
Jun 10 01:22:16 sys-op-dsktp kernel: [  304.788268] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=69.136.108.146 DST=192.168.2.5 LEN=70 TOS=0x00 PREC=0x00 TTL=40 ID=35585 PROTO=UDP SPT=39615 DPT=15684 LEN=50 
Jun 10 01:22:17 sys-op-dsktp kernel: [  305.951718] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=213.140.6.104 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=36 ID=2640 PROTO=UDP SPT=52728 DPT=15684 LEN=71 
Jun 10 01:22:17 sys-op-dsktp kernel: [  306.479950] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=71.232.147.106 DST=192.168.2.5 LEN=70 TOS=0x00 PREC=0x00 TTL=105 ID=13855 PROTO=UDP SPT=38302 DPT=15684 LEN=50 
Jun 10 01:22:20 sys-op-dsktp kernel: [  309.331954] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=98.208.90.156 DST=192.168.2.5 LEN=70 TOS=0x00 PREC=0x00 TTL=103 ID=2924 PROTO=UDP SPT=54038 DPT=15684 LEN=50 
Jun 10 01:22:22 sys-op-dsktp kernel: [  311.529900] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=24.17.71.66 DST=192.168.2.5 LEN=93 TOS=0x00 PREC=0x00 TTL=102 ID=26540 PROTO=UDP SPT=22940 DPT=15684 LEN=73 
Jun 10 01:22:24 sys-op-dsktp kernel: [  312.749301] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=77.88.172.197 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=47 ID=8582 PROTO=UDP SPT=61443 DPT=15684 LEN=71 
Jun 10 01:22:25 sys-op-dsktp kernel: [  313.654093] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=84.217.140.207 DST=192.168.2.5 LEN=70 TOS=0x00 PREC=0x00 TTL=118 ID=34052 PROTO=UDP SPT=21 DPT=15684 LEN=50 
Jun 10 01:22:27 sys-op-dsktp kernel: [  316.290816] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=71.77.136.108 DST=192.168.2.5 LEN=93 TOS=0x00 PREC=0x00 TTL=111 ID=1008 PROTO=UDP SPT=55179 DPT=15684 LEN=73 
Jun 10 01:22:28 sys-op-dsktp kernel: [  317.356267] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=68.105.66.24 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=53 ID=36024 PROTO=UDP SPT=35508 DPT=15684 LEN=71 
Jun 10 01:22:34 sys-op-dsktp kernel: [  323.176832] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=68.105.66.24 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=53 ID=58651 PROTO=UDP SPT=35508 DPT=15684 LEN=71 
Jun 10 01:22:34 sys-op-dsktp kernel: [  323.568796] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=203.206.249.158 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=111 ID=31010 PROTO=UDP SPT=37291 DPT=15684 LEN=71 
Jun 10 01:22:37 sys-op-dsktp kernel: [  326.306983] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=67.161.190.204 DST=192.168.2.5 LEN=70 TOS=0x00 PREC=0x00 TTL=42 ID=46121 PROTO=UDP SPT=55052 DPT=15684 LEN=50 
Jun 10 01:22:39 sys-op-dsktp kernel: [  328.442501] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=70.68.60.233 DST=192.168.2.5 LEN=93 TOS=0x00 PREC=0x00 TTL=112 ID=21145 PROTO=UDP SPT=60002 DPT=15684 LEN=73 
Jun 10 01:22:43 sys-op-dsktp kernel: [  331.813238] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=89.83.99.182 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=118 ID=25580 PROTO=UDP SPT=55033 DPT=15684 LEN=71 
Jun 10 01:22:44 sys-op-dsktp kernel: [  332.805565] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=91.32.250.235 DST=192.168.2.5 LEN=70 TOS=0x00 PREC=0x00 TTL=117 ID=10170 PROTO=UDP SPT=51406 DPT=15684 LEN=50 
Jun 10 01:22:45 sys-op-dsktp kernel: [  334.008643] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=83.249.100.254 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=115 ID=47962 PROTO=UDP SPT=29079 DPT=15684 LEN=71 
Jun 10 01:22:46 sys-op-dsktp kernel: [  334.614645] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=76.174.63.158 DST=192.168.2.5 LEN=93 TOS=0x00 PREC=0x00 TTL=113 ID=23114 PROTO=UDP SPT=16589 DPT=15684 LEN=73 
Jun 10 01:22:46 sys-op-dsktp kernel: [  334.960884] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=83.249.100.254 DST=192.168.2.5 LEN=70 TOS=0x00 PREC=0x00 TTL=115 ID=48486 PROTO=UDP SPT=29079 DPT=15684 LEN=50 
Jun 10 01:22:48 sys-op-dsktp kernel: [  337.107409] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=91.32.250.235 DST=192.168.2.5 LEN=70 TOS=0x00 PREC=0x00 TTL=118 ID=11217 PROTO=UDP SPT=51406 DPT=15684 LEN=50 
Jun 10 01:22:52 sys-op-dsktp kernel: [  341.059754] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=79.25.11.205 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=116 ID=24151 PROTO=UDP SPT=35970 DPT=15684 LEN=71 
Jun 10 01:22:52 sys-op-dsktp kernel: [  341.103650] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=70.162.155.206 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=114 ID=15195 PROTO=UDP SPT=55551 DPT=15684 LEN=71 
Jun 10 01:22:53 sys-op-dsktp kernel: [  341.912091] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=190.45.244.81 DST=192.168.2.5 LEN=93 TOS=0x00 PREC=0x00 TTL=118 ID=13616 PROTO=UDP SPT=38344 DPT=15684 LEN=73 
Jun 10 01:22:53 sys-op-dsktp kernel: [  342.015428] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=76.185.153.121 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=109 ID=34680 PROTO=UDP SPT=6881 DPT=15684 LEN=71 
Jun 10 01:22:53 sys-op-dsktp kernel: [  342.373189] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=76.117.41.19 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=40 ID=50557 PROTO=UDP SPT=54545 DPT=15684 LEN=71 
Jun 10 01:22:55 sys-op-dsktp kernel: [  344.248676] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=88.188.241.69 DST=192.168.2.5 LEN=93 TOS=0x00 PREC=0x00 TTL=53 ID=9911 PROTO=UDP SPT=64370 DPT=15684 LEN=73 
Jun 10 01:22:55 sys-op-dsktp kernel: [  344.433844] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=78.16.167.37 DST=192.168.2.5 LEN=70 TOS=0x00 PREC=0x00 TTL=115 ID=16177 PROTO=UDP SPT=24467 DPT=15684 LEN=50 
Jun 10 01:22:58 sys-op-dsktp kernel: [  346.766129] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=89.129.166.25 DST=192.168.2.5 LEN=93 TOS=0x00 PREC=0x00 TTL=114 ID=50461 PROTO=UDP SPT=58108 DPT=15684 LEN=73 
Jun 10 01:22:58 sys-op-dsktp kernel: [  347.141354] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=75.82.216.93 DST=192.168.2.5 LEN=93 TOS=0x00 PREC=0x00 TTL=111 ID=46175 PROTO=UDP SPT=18373 DPT=15684 LEN=73 
Jun 10 01:23:00 sys-op-dsktp kernel: [  349.362261] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=75.72.245.164 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=107 ID=30951 PROTO=UDP SPT=37212 DPT=15684 LEN=71 
Jun 10 01:23:00 sys-op-dsktp kernel: [  349.494335] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=60.38.182.118 DST=192.168.2.5 LEN=70 TOS=0x00 PREC=0x00 TTL=107 ID=30265 PROTO=UDP SPT=56010 DPT=15684 LEN=50 
Jun 10 01:23:00 sys-op-dsktp kernel: [  349.544993] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=60.38.182.118 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=107 ID=30267 PROTO=UDP SPT=56010 DPT=15684 LEN=71 
Jun 10 01:23:01 sys-op-dsktp kernel: [  349.848154] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=87.220.127.254 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=109 ID=14916 PROTO=UDP SPT=2333 DPT=15684 LEN=71 
Jun 10 01:23:01 sys-op-dsktp kernel: [  350.514753] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=87.203.158.128 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=115 ID=5385 PROTO=UDP SPT=17146 DPT=15684 LEN=71 
Jun 10 01:23:03 sys-op-dsktp kernel: [  352.480920] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=79.25.11.205 DST=192.168.2.5 LEN=70 TOS=0x00 PREC=0x00 TTL=116 ID=24424 PROTO=UDP SPT=35970 DPT=15684 LEN=50 
Jun 10 01:23:05 sys-op-dsktp kernel: [  354.370987] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=190.134.13.247 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=118 ID=23178 PROTO=UDP SPT=10708 DPT=15684 LEN=71 
Jun 10 01:23:11 sys-op-dsktp kernel: [  360.481566] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=71.170.15.175 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=115 ID=47992 PROTO=UDP SPT=63660 DPT=15684 LEN=71 
Jun 10 01:23:11 sys-op-dsktp kernel: [  360.507858] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=83.249.100.254 DST=192.168.2.5 LEN=70 TOS=0x00 PREC=0x00 TTL=115 ID=62682 PROTO=UDP SPT=29079 DPT=15684 LEN=50 
Jun 10 01:23:12 sys-op-dsktp kernel: [  361.180422] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=82.44.74.22 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=51 ID=1160 PROTO=UDP SPT=45591 DPT=15684 LEN=71 
Jun 10 01:23:13 sys-op-dsktp kernel: [  362.082405] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=67.161.190.204 DST=192.168.2.5 LEN=70 TOS=0x00 PREC=0x00 TTL=42 ID=56657 PROTO=UDP SPT=55052 DPT=15684 LEN=50 
Jun 10 01:23:14 sys-op-dsktp kernel: [  362.699606] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=99.241.62.104 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=113 ID=11473 PROTO=UDP SPT=40203 DPT=15684 LEN=71 
Jun 10 01:23:23 sys-op-dsktp kernel: [  372.178910] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=99.239.214.113 DST=192.168.2.5 LEN=70 TOS=0x00 PREC=0x00 TTL=114 ID=16663 PROTO=UDP SPT=52625 DPT=15684 LEN=50 
Jun 10 01:23:26 sys-op-dsktp kernel: [  375.026326] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=93.81.21.118 DST=192.168.2.5 LEN=93 TOS=0x00 PREC=0x00 TTL=113 ID=25629 PROTO=UDP SPT=49152 DPT=15684 LEN=73 
Jun 10 01:23:26 sys-op-dsktp kernel: [  375.431806] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=89.245.41.112 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=53 ID=49282 PROTO=UDP SPT=55380 DPT=15684 LEN=71 
Jun 10 01:23:27 sys-op-dsktp kernel: [  375.686238] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=82.44.74.22 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=51 ID=5846 PROTO=UDP SPT=45591 DPT=15684 LEN=71 
Jun 10 01:23:27 sys-op-dsktp kernel: [  375.723904] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=67.174.14.161 DST=192.168.2.5 LEN=93 TOS=0x00 PREC=0x00 TTL=106 ID=6709 PROTO=UDP SPT=18432 DPT=15684 LEN=73 
Jun 10 01:23:30 sys-op-dsktp kernel: [  378.627553] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=70.65.149.117 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=114 ID=64623 PROTO=UDP SPT=60975 DPT=15684 LEN=71 
Jun 10 01:23:30 sys-op-dsktp kernel: [  379.477065] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=91.153.213.179 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=119 ID=38788 PROTO=UDP SPT=60026 DPT=15684 LEN=71 
Jun 10 01:23:31 sys-op-dsktp kernel: [  379.746286] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=87.194.98.44 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=53 ID=57048 PROTO=UDP SPT=45548 DPT=15684 LEN=71 
Jun 10 01:23:31 sys-op-dsktp kernel: [  379.934123] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=78.191.78.7 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=115 ID=57655 PROTO=UDP SPT=19665 DPT=15684 LEN=71 
Jun 10 01:23:31 sys-op-dsktp kernel: [  380.335219] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=71.109.123.243 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=114 ID=34283 PROTO=UDP SPT=58528 DPT=15684 LEN=71 
Jun 10 01:23:32 sys-op-dsktp kernel: [  380.825686] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=88.74.182.203 DST=192.168.2.5 LEN=93 TOS=0x00 PREC=0x00 TTL=115 ID=1983 PROTO=UDP SPT=27846 DPT=15684 LEN=73 
Jun 10 01:23:36 sys-op-dsktp kernel: [  384.626651] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=60.38.182.118 DST=192.168.2.5 LEN=70 TOS=0x00 PREC=0x00 TTL=107 ID=32470 PROTO=UDP SPT=56010 DPT=15684 LEN=50 
Jun 10 01:23:38 sys-op-dsktp kernel: [  387.340068] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=71.135.36.133 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=116 ID=31472 PROTO=UDP SPT=29557 DPT=15684 LEN=71 
Jun 10 01:23:39 sys-op-dsktp kernel: [  388.446319] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=213.46.133.246 DST=192.168.2.5 LEN=70 TOS=0x00 PREC=0x00 TTL=120 ID=30362 PROTO=UDP SPT=6881 DPT=15684 LEN=50 
Jun 10 01:23:41 sys-op-dsktp kernel: [  389.591187] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=71.196.227.235 DST=192.168.2.5 LEN=93 TOS=0x00 PREC=0x00 TTL=107 ID=955 PROTO=UDP SPT=6881 DPT=15684 LEN=73 
Jun 10 01:23:41 sys-op-dsktp kernel: [  389.772386] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=80.98.240.247 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=109 ID=53417 PROTO=UDP SPT=48877 DPT=15684 LEN=71 
Jun 10 01:23:42 sys-op-dsktp kernel: [  390.841438] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=83.46.80.183 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=115 ID=63717 PROTO=UDP SPT=20901 DPT=15684 LEN=71 
Jun 10 01:23:43 sys-op-dsktp kernel: [  392.313968] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=88.218.85.136 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=116 ID=11629 PROTO=UDP SPT=65514 DPT=15684 LEN=71 
Jun 10 01:23:44 sys-op-dsktp kernel: [  392.944189] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=96.230.98.249 DST=192.168.2.5 LEN=93 TOS=0x00 PREC=0x00 TTL=114 ID=6415 PROTO=UDP SPT=28137 DPT=15684 LEN=73 
Jun 10 01:23:49 sys-op-dsktp kernel: [  398.215664] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=81.210.117.138 DST=192.168.2.5 LEN=70 TOS=0x00 PREC=0x00 TTL=113 ID=43133 PROTO=UDP SPT=6887 DPT=15684 LEN=50 
Jun 10 01:23:49 sys-op-dsktp kernel: [  398.333381] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=68.94.76.135 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=116 ID=22170 PROTO=UDP SPT=55056 DPT=15684 LEN=71 
Jun 10 01:23:51 sys-op-dsktp kernel: [  400.515245] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=201.103.123.58 DST=192.168.2.5 LEN=93 TOS=0x00 PREC=0x00 TTL=116 ID=24168 PROTO=UDP SPT=16686 DPT=15684 LEN=73 
Jun 10 01:23:52 sys-op-dsktp kernel: [  401.380439] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=84.59.218.86 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=117 ID=62593 PROTO=UDP SPT=16716 DPT=15684 LEN=71 
Jun 10 01:23:53 sys-op-dsktp kernel: [  401.755280] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=71.82.10.26 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=115 ID=55955 PROTO=UDP SPT=43078 DPT=15684 LEN=71 
Jun 10 01:23:53 sys-op-dsktp kernel: [  402.359135] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=82.225.65.84 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=119 ID=50269 PROTO=UDP SPT=28535 DPT=15684 LEN=71 
Jun 10 01:23:53 sys-op-dsktp kernel: [  402.439379] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=58.49.193.213 DST=192.168.2.5 LEN=70 TOS=0x00 PREC=0x00 TTL=43 ID=22710 PROTO=UDP SPT=13861 DPT=15684 LEN=50 
Jun 10 01:23:53 sys-op-dsktp kernel: [  402.520327] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=83.177.54.177 DST=192.168.2.5 LEN=71 TOS=0x00 PREC=0x00 TTL=115 ID=11358 PROTO=UDP SPT=51200 DPT=15684 LEN=51 
Jun 10 01:23:55 sys-op-dsktp kernel: [  403.921245] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=98.208.90.156 DST=192.168.2.5 LEN=70 TOS=0x00 PREC=0x00 TTL=103 ID=3447 PROTO=UDP SPT=54038 DPT=15684 LEN=50 
Jun 10 01:23:55 sys-op-dsktp kernel: [  404.355635] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=82.13.47.148 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=114 ID=35399 PROTO=UDP SPT=14812 DPT=15684 LEN=71 
Jun 10 01:23:55 sys-op-dsktp kernel: [  404.396289] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=68.161.134.218 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=115 ID=48767 PROTO=UDP SPT=63372 DPT=15684 LEN=71 
Jun 10 01:23:56 sys-op-dsktp kernel: [  405.460925] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=77.201.20.204 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=118 ID=20271 PROTO=UDP SPT=55106 DPT=15684 LEN=71 
Jun 10 01:23:57 sys-op-dsktp kernel: [  405.721496] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=62.216.20.78 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=122 ID=38698 PROTO=UDP SPT=10558 DPT=15684 LEN=71 
Jun 10 01:23:57 sys-op-dsktp kernel: [  406.337605] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=82.225.65.84 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=119 ID=50806 PROTO=UDP SPT=28535 DPT=15684 LEN=71 
Jun 10 01:23:57 sys-op-dsktp kernel: [  406.432053] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=88.218.85.136 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=116 ID=11917 PROTO=UDP SPT=65514 DPT=15684 LEN=71 
Jun 10 01:23:58 sys-op-dsktp kernel: [  406.612832] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=81.210.117.138 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=113 ID=44131 PROTO=UDP SPT=6887 DPT=15684 LEN=71 
Jun 10 01:24:01 sys-op-dsktp kernel: [  409.857863] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=209.131.79.130 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=116 ID=9215 PROTO=UDP SPT=54508 DPT=15684 LEN=71 
Jun 10 01:24:03 sys-op-dsktp kernel: [  412.215542] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=82.128.188.212 DST=192.168.2.5 LEN=93 TOS=0x00 PREC=0x00 TTL=109 ID=16785 PROTO=UDP SPT=56302 DPT=15684 LEN=73 
Jun 10 01:24:03 sys-op-dsktp kernel: [  412.428179] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=83.190.118.26 DST=192.168.2.5 LEN=93 TOS=0x00 PREC=0x00 TTL=110 ID=3637 PROTO=UDP SPT=12067 DPT=15684 LEN=73 
Jun 10 01:24:04 sys-op-dsktp kernel: [  413.394731] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=205.200.171.160 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=119 ID=37365 PROTO=UDP SPT=41128 DPT=15684 LEN=71 
Jun 10 01:24:07 sys-op-dsktp kernel: [  415.514168] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=68.119.175.118 DST=192.168.2.5 LEN=93 TOS=0x00 PREC=0x00 TTL=114 ID=28687 PROTO=UDP SPT=10930 DPT=15684 LEN=73 
Jun 10 01:24:07 sys-op-dsktp kernel: [  415.688098] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=83.226.194.184 DST=192.168.2.5 LEN=93 TOS=0x00 PREC=0x00 TTL=118 ID=10227 PROTO=UDP SPT=56962 DPT=15684 LEN=73 
Jun 10 01:24:09 sys-op-dsktp kernel: [  417.807649] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=84.69.251.210 DST=192.168.2.5 LEN=93 TOS=0x00 PREC=0x00 TTL=117 ID=26035 PROTO=UDP SPT=15392 DPT=15684 LEN=73 
Jun 10 01:24:09 sys-op-dsktp kernel: [  417.926426] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=79.179.114.92 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=117 ID=16796 PROTO=UDP SPT=13214 DPT=15684 LEN=71 
Jun 10 01:24:10 sys-op-dsktp kernel: [  418.953778] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=70.53.135.95 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=108 ID=32026 PROTO=UDP SPT=28807 DPT=15684 LEN=71 
Jun 10 01:24:12 sys-op-dsktp kernel: [  420.938484] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=82.44.74.22 DST=192.168.2.5 LEN=70 TOS=0x00 PREC=0x00 TTL=51 ID=54363 PROTO=UDP SPT=45591 DPT=15684 LEN=50 
Jun 10 01:24:12 sys-op-dsktp kernel: [  421.208523] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=190.134.183.13 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=119 ID=33165 PROTO=UDP SPT=34234 DPT=15684 LEN=71 
Jun 10 01:24:13 sys-op-dsktp kernel: [  422.446810] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=74.216.45.152 DST=192.168.2.5 LEN=93 TOS=0x00 PREC=0x00 TTL=119 ID=14869 PROTO=UDP SPT=61015 DPT=15684 LEN=73 
Jun 10 01:24:16 sys-op-dsktp kernel: [  425.415493] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=82.13.47.148 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=114 ID=35953 PROTO=UDP SPT=14812 DPT=15684 LEN=71 
Jun 10 01:24:18 sys-op-dsktp kernel: [  427.485546] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=88.184.36.73 DST=192.168.2.5 LEN=93 TOS=0x00 PREC=0x00 TTL=116 ID=26711 PROTO=UDP SPT=43588 DPT=15684 LEN=73 
Jun 10 01:24:19 sys-op-dsktp kernel: [  427.902097] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=81.182.216.232 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=51 ID=13947 PROTO=UDP SPT=36533 DPT=15684 LEN=71 
Jun 10 01:24:19 sys-op-dsktp kernel: [  428.388130] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=78.27.79.209 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=113 ID=20265 PROTO=UDP SPT=36928 DPT=15684 LEN=71 
Jun 10 01:24:21 sys-op-dsktp kernel: [  429.702017] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=86.31.155.14 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=52 ID=42227 PROTO=UDP SPT=36810 DPT=15684 LEN=71 
Jun 10 01:24:23 sys-op-dsktp kernel: [  431.666575] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=82.13.47.148 DST=192.168.2.5 LEN=70 TOS=0x00 PREC=0x00 TTL=114 ID=36190 PROTO=UDP SPT=14812 DPT=15684 LEN=50 
Jun 10 01:24:26 sys-op-dsktp kernel: [  434.588639] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=124.13.202.81 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=110 ID=4013 PROTO=UDP SPT=6881 DPT=15684 LEN=71 
Jun 10 01:24:28 sys-op-dsktp kernel: [  437.127874] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=88.15.118.83 DST=192.168.2.5 LEN=70 TOS=0x00 PREC=0x00 TTL=113 ID=430 PROTO=UDP SPT=29660 DPT=15684 LEN=50 
Jun 10 01:24:28 sys-op-dsktp kernel: [  437.181877] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=82.152.7.137 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=118 ID=64873 PROTO=UDP SPT=64564 DPT=15684 LEN=71 
Jun 10 01:24:28 sys-op-dsktp kernel: [  437.423287] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=24.151.24.52 DST=192.168.2.5 LEN=93 TOS=0x00 PREC=0x00 TTL=112 ID=27492 PROTO=UDP SPT=58325 DPT=15684 LEN=73 
Jun 10 01:24:31 sys-op-dsktp kernel: [  439.713591] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=81.132.233.243 DST=192.168.2.5 LEN=93 TOS=0x00 PREC=0x00 TTL=107 ID=7819 PROTO=UDP SPT=58787 DPT=15684 LEN=73 
Jun 10 01:24:33 sys-op-dsktp kernel: [  441.705309] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=82.83.170.212 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=116 ID=10892 PROTO=UDP SPT=60785 DPT=15684 LEN=71 
Jun 10 01:24:34 sys-op-dsktp kernel: [  442.920101] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=67.183.142.194 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=41 ID=5789 PROTO=UDP SPT=55005 DPT=15684 LEN=71 
Jun 10 01:24:34 sys-op-dsktp kernel: [  443.058901] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=124.129.63.218 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=110 ID=7733 PROTO=UDP SPT=19860 DPT=15684 LEN=71 
Jun 10 01:24:35 sys-op-dsktp kernel: [  444.136408] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=87.221.7.48 DST=192.168.2.5 LEN=93 TOS=0x00 PREC=0x00 TTL=113 ID=26234 PROTO=UDP SPT=22605 DPT=15684 LEN=73 
Jun 10 01:24:37 sys-op-dsktp kernel: [  445.900762] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=71.109.217.181 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=114 ID=9208 PROTO=UDP SPT=40671 DPT=15684 LEN=71 
Jun 10 01:24:38 sys-op-dsktp kernel: [  446.626158] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=58.49.193.213 DST=192.168.2.5 LEN=70 TOS=0x00 PREC=0x00 TTL=43 ID=36779 PROTO=UDP SPT=13861 DPT=15684 LEN=50 
Jun 10 01:24:40 sys-op-dsktp kernel: [  449.027978] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=78.54.179.18 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=54 ID=0 DF PROTO=UDP SPT=32223 DPT=15684 LEN=71 
Jun 10 01:24:43 sys-op-dsktp kernel: [  451.818148] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=91.61.236.47 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=117 ID=18634 PROTO=UDP SPT=40502 DPT=15684 LEN=71 
Jun 10 01:24:44 sys-op-dsktp kernel: [  452.754434] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=91.152.78.64 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=54 ID=0 DF PROTO=UDP SPT=52025 DPT=15684 LEN=71 
Jun 10 01:24:45 sys-op-dsktp kernel: [  453.720277] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=72.208.89.99 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=118 ID=65034 PROTO=UDP SPT=31265 DPT=15684 LEN=71 
Jun 10 01:24:46 sys-op-dsktp kernel: [  454.810184] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=84.9.123.170 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=112 ID=64559 PROTO=UDP SPT=46001 DPT=15684 LEN=71 
Jun 10 01:24:46 sys-op-dsktp kernel: [  455.176226] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=82.13.47.148 DST=192.168.2.5 LEN=70 TOS=0x00 PREC=0x00 TTL=114 ID=36942 PROTO=UDP SPT=14812 DPT=15684 LEN=50 
Jun 10 01:24:47 sys-op-dsktp kernel: [  455.517542] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=70.56.173.8 DST=192.168.2.5 LEN=93 TOS=0x00 PREC=0x00 TTL=114 ID=2329 PROTO=UDP SPT=25408 DPT=15684 LEN=73 
Jun 10 01:24:47 sys-op-dsktp kernel: [  455.961731] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=96.224.21.203 DST=192.168.2.5 LEN=93 TOS=0x00 PREC=0x00 TTL=51 ID=28820 PROTO=UDP SPT=50483 DPT=15684 LEN=73 
Jun 10 01:24:48 sys-op-dsktp kernel: [  457.064513] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=71.111.14.66 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=114 ID=10324 PROTO=UDP SPT=48990 DPT=15684 LEN=71 
Jun 10 01:24:49 sys-op-dsktp kernel: [  458.249011] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=60.38.182.118 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=107 ID=37494 PROTO=UDP SPT=56010 DPT=15684 LEN=71 
Jun 10 01:24:50 sys-op-dsktp kernel: [  458.896469] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=87.122.191.189 DST=192.168.2.5 LEN=93 TOS=0x00 PREC=0x00 TTL=114 ID=51670 PROTO=UDP SPT=54446 DPT=15684 LEN=73 
Jun 10 01:24:50 sys-op-dsktp kernel: [  458.903753] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=88.218.85.136 DST=192.168.2.5 LEN=70 TOS=0x00 PREC=0x00 TTL=116 ID=13147 PROTO=UDP SPT=65514 DPT=15684 LEN=50 
Jun 10 01:24:52 sys-op-dsktp kernel: [  460.639659] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=76.123.25.163 DST=192.168.2.5 LEN=93 TOS=0x00 PREC=0x00 TTL=105 ID=20639 PROTO=UDP SPT=41593 DPT=15684 LEN=73 
Jun 10 01:24:52 sys-op-dsktp kernel: [  460.794793] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=98.148.226.190 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=110 ID=16871 PROTO=UDP SPT=32845 DPT=15684 LEN=71 
Jun 10 01:24:52 sys-op-dsktp kernel: [  461.146657] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=72.21.245.82 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=114 ID=9938 PROTO=UDP SPT=64267 DPT=15684 LEN=71 
Jun 10 01:24:52 sys-op-dsktp kernel: [  461.342486] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=24.40.131.189 DST=192.168.2.5 LEN=93 TOS=0x00 PREC=0x00 TTL=46 ID=0 DF PROTO=UDP SPT=45627 DPT=15684 LEN=73 
Jun 10 01:24:53 sys-op-dsktp kernel: [  461.666476] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=67.162.161.98 DST=192.168.2.5 LEN=93 TOS=0x00 PREC=0x00 TTL=36 ID=32348 PROTO=UDP SPT=55361 DPT=15684 LEN=73 
Jun 10 01:24:55 sys-op-dsktp kernel: [  463.906658] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=24.235.37.226 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=49 ID=56258 PROTO=UDP SPT=60200 DPT=15684 LEN=71 
Jun 10 01:24:55 sys-op-dsktp kernel: [  463.909392] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=60.48.189.194 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=113 ID=28641 PROTO=UDP SPT=47881 DPT=15684 LEN=71 
Jun 10 01:24:55 sys-op-dsktp kernel: [  464.248615] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=212.195.103.156 DST=192.168.2.5 LEN=71 TOS=0x00 PREC=0x00 TTL=121 ID=28682 PROTO=UDP SPT=62581 DPT=15684 LEN=51 
Jun 10 01:24:55 sys-op-dsktp kernel: [  464.418017] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=212.195.103.156 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=121 ID=28697 PROTO=UDP SPT=62581 DPT=15684 LEN=71 
Jun 10 01:24:56 sys-op-dsktp kernel: [  464.553672] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=69.107.125.24 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=115 ID=1288 PROTO=UDP SPT=59369 DPT=15684 LEN=71 
Jun 10 01:24:56 sys-op-dsktp kernel: [  464.919133] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=209.131.79.130 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=116 ID=10753 PROTO=UDP SPT=54508 DPT=15684 LEN=71 
Jun 10 01:24:59 sys-op-dsktp kernel: [  467.899920] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=70.241.124.120 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=116 ID=39401 PROTO=UDP SPT=50064 DPT=15684 LEN=71 
Jun 10 01:24:59 sys-op-dsktp kernel: [  468.074906] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=74.128.210.255 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=51 ID=5128 PROTO=UDP SPT=15449 DPT=15684 LEN=71 
Jun 10 01:25:00 sys-op-dsktp kernel: [  468.879482] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=92.4.182.156 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=118 ID=34989 PROTO=UDP SPT=35771 DPT=15684 LEN=71 
Jun 10 01:25:02 sys-op-dsktp kernel: [  470.494875] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=81.236.150.209 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=117 ID=28608 PROTO=UDP SPT=43595 DPT=15684 LEN=71 
Jun 10 01:25:04 sys-op-dsktp kernel: [  473.236107] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=71.143.225.212 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=116 ID=2154 PROTO=UDP SPT=14594 DPT=15684 LEN=71 
Jun 10 01:25:05 sys-op-dsktp kernel: [  473.876834] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=66.158.201.14 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=114 ID=30345 PROTO=UDP SPT=30755 DPT=15684 LEN=71 
Jun 10 01:25:05 sys-op-dsktp kernel: [  473.990830] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=99.234.137.77 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=114 ID=59044 PROTO=UDP SPT=62191 DPT=15684 LEN=71 
Jun 10 01:25:07 sys-op-dsktp kernel: [  475.643034] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=76.11.40.73 DST=192.168.2.5 LEN=93 TOS=0x00 PREC=0x00 TTL=108 ID=51593 PROTO=UDP SPT=46673 DPT=15684 LEN=73 
Jun 10 01:25:08 sys-op-dsktp kernel: [  476.542008] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=81.210.117.138 DST=192.168.2.5 LEN=70 TOS=0x00 PREC=0x00 TTL=113 ID=52129 PROTO=UDP SPT=6887 DPT=15684 LEN=50 
Jun 10 01:25:08 sys-op-dsktp kernel: [  477.357978] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=71.232.147.106 DST=192.168.2.5 LEN=70 TOS=0x00 PREC=0x00 TTL=105 ID=16502 PROTO=UDP SPT=38302 DPT=15684 LEN=50 
Jun 10 01:25:09 sys-op-dsktp kernel: [  477.599494] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=82.152.7.137 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=118 ID=1528 PROTO=UDP SPT=64564 DPT=15684 LEN=71 
Jun 10 01:25:09 sys-op-dsktp kernel: [  478.133680] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=71.242.64.72 DST=192.168.2.5 LEN=93 TOS=0x00 PREC=0x00 TTL=114 ID=43445 PROTO=UDP SPT=50864 DPT=15684 LEN=73 
Jun 10 01:25:10 sys-op-dsktp kernel: [  479.359796] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=87.78.71.197 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=118 ID=4834 PROTO=UDP SPT=56412 DPT=15684 LEN=71 
Jun 10 01:25:13 sys-op-dsktp kernel: [  481.535274] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=88.218.85.136 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=116 ID=13674 PROTO=UDP SPT=65514 DPT=15684 LEN=71 
Jun 10 01:25:13 sys-op-dsktp kernel: [  482.264264] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=82.233.85.90 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=56 ID=32997 PROTO=UDP SPT=52194 DPT=15684 LEN=71 
Jun 10 01:25:13 sys-op-dsktp kernel: [  482.285099] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=58.109.76.233 DST=192.168.2.5 LEN=93 TOS=0x00 PREC=0x00 TTL=108 ID=5358 PROTO=UDP SPT=55000 DPT=15684 LEN=73 
Jun 10 01:25:15 sys-op-dsktp kernel: [  483.891624] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=209.131.79.130 DST=192.168.2.5 LEN=70 TOS=0x00 PREC=0x00 TTL=116 ID=11226 PROTO=UDP SPT=54508 DPT=15684 LEN=50 
Jun 10 01:25:15 sys-op-dsktp kernel: [  483.916376] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=62.195.75.166 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=119 ID=2630 PROTO=UDP SPT=61009 DPT=15684 LEN=71 
Jun 10 01:25:18 sys-op-dsktp kernel: [  487.244272] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=81.183.36.11 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=116 ID=50903 PROTO=UDP SPT=56274 DPT=15684 LEN=71 
Jun 10 01:25:20 sys-op-dsktp kernel: [  489.140819] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=69.107.125.24 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=115 ID=5076 PROTO=UDP SPT=59369 DPT=15684 LEN=71 
Jun 10 01:25:28 sys-op-dsktp kernel: [  496.441634] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=81.222.204.216 DST=192.168.2.5 LEN=93 TOS=0x00 PREC=0x00 TTL=120 ID=7053 PROTO=UDP SPT=60930 DPT=15684 LEN=73 
Jun 10 01:25:30 sys-op-dsktp kernel: [  498.615292] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=58.71.109.21 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=110 ID=10262 PROTO=UDP SPT=63422 DPT=15684 LEN=71 
Jun 10 01:25:32 sys-op-dsktp kernel: [  500.954558] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=79.101.66.206 DST=192.168.2.5 LEN=70 TOS=0x00 PREC=0x00 TTL=111 ID=52721 PROTO=UDP SPT=57716 DPT=15684 LEN=50 
Jun 10 01:25:32 sys-op-dsktp kernel: [  501.012770] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=79.101.66.206 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=111 ID=52724 PROTO=UDP SPT=57716 DPT=15684 LEN=71 
Jun 10 01:25:32 sys-op-dsktp kernel: [  501.227250] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=82.230.189.107 DST=192.168.2.5 LEN=93 TOS=0x00 PREC=0x00 TTL=118 ID=23202 PROTO=UDP SPT=46359 DPT=15684 LEN=73 
Jun 10 01:25:34 sys-op-dsktp kernel: [  502.937995] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=68.161.134.218 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=115 ID=60306 PROTO=UDP SPT=63372 DPT=15684 LEN=71 
Jun 10 01:25:34 sys-op-dsktp kernel: [  503.399267] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=209.131.79.130 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=116 ID=11713 PROTO=UDP SPT=54508 DPT=15684 LEN=71 
Jun 10 01:25:35 sys-op-dsktp kernel: [  504.066140] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=92.73.132.134 DST=192.168.2.5 LEN=93 TOS=0x00 PREC=0x00 TTL=114 ID=38083 PROTO=UDP SPT=13877 DPT=15684 LEN=73 
Jun 10 01:25:37 sys-op-dsktp kernel: [  505.648903] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=78.54.179.18 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=54 ID=0 DF PROTO=UDP SPT=32223 DPT=15684 LEN=71 
Jun 10 01:25:38 sys-op-dsktp kernel: [  507.142096] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=41.248.162.26 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=117 ID=55084 PROTO=UDP SPT=34448 DPT=15684 LEN=71 
Jun 10 01:25:39 sys-op-dsktp kernel: [  507.672344] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=99.231.120.202 DST=192.168.2.5 LEN=93 TOS=0x00 PREC=0x00 TTL=113 ID=44378 PROTO=UDP SPT=62920 DPT=15684 LEN=73 
Jun 10 01:25:40 sys-op-dsktp kernel: [  508.901098] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=70.241.124.120 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=116 ID=40045 PROTO=UDP SPT=50064 DPT=15684 LEN=71 
Jun 10 01:25:41 sys-op-dsktp kernel: [  510.150083] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=80.0.59.99 DST=192.168.2.5 LEN=93 TOS=0x00 PREC=0x00 TTL=115 ID=19030 PROTO=UDP SPT=59812 DPT=15684 LEN=73 
Jun 10 01:25:42 sys-op-dsktp kernel: [  510.442109] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=90.55.36.153 DST=192.168.2.5 LEN=93 TOS=0x00 PREC=0x00 TTL=113 ID=5863 PROTO=UDP SPT=62213 DPT=15684 LEN=73 
Jun 10 01:25:42 sys-op-dsktp kernel: [  510.968491] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=70.240.76.132 DST=192.168.2.5 LEN=93 TOS=0x00 PREC=0x00 TTL=116 ID=19146 PROTO=UDP SPT=63920 DPT=15684 LEN=73 
Jun 10 01:25:42 sys-op-dsktp kernel: [  511.288146] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=88.153.25.177 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=114 ID=58606 PROTO=UDP SPT=58213 DPT=15684 LEN=71 
Jun 10 01:25:46 sys-op-dsktp kernel: [  514.666969] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=71.195.247.249 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=105 ID=3091 PROTO=UDP SPT=55281 DPT=15684 LEN=71 
Jun 10 01:25:49 sys-op-dsktp kernel: [  517.927781] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=71.232.147.106 DST=192.168.2.5 LEN=70 TOS=0x00 PREC=0x00 TTL=105 ID=17109 PROTO=UDP SPT=38302 DPT=15684 LEN=50 
Jun 10 01:25:53 sys-op-dsktp kernel: [  521.711911] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=84.13.150.245 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=109 ID=1145 PROTO=UDP SPT=60661 DPT=15684 LEN=71 
Jun 10 01:25:54 sys-op-dsktp kernel: [  522.632468] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=200.83.202.184 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=119 ID=21359 PROTO=UDP SPT=19987 DPT=15684 LEN=71 
Jun 10 01:25:54 sys-op-dsktp kernel: [  522.947978] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=86.212.217.151 DST=192.168.2.5 LEN=70 TOS=0x00 PREC=0x00 TTL=50 ID=46956 PROTO=UDP SPT=46819 DPT=15684 LEN=50 
Jun 10 01:26:00 sys-op-dsktp kernel: [  529.172471] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=69.123.212.253 DST=192.168.2.5 LEN=71 TOS=0x00 PREC=0x00 TTL=113 ID=50841 PROTO=UDP SPT=19099 DPT=15684 LEN=51 
Jun 10 01:26:01 sys-op-dsktp kernel: [  529.477486] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=83.140.193.172 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=114 ID=35981 PROTO=UDP SPT=44047 DPT=15684 LEN=71 
Jun 10 01:26:02 sys-op-dsktp kernel: [  531.156578] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=212.195.103.156 DST=192.168.2.5 LEN=70 TOS=0x00 PREC=0x00 TTL=121 ID=34451 PROTO=UDP SPT=62581 DPT=15684 LEN=50 
Jun 10 01:26:03 sys-op-dsktp kernel: [  531.609451] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=68.191.45.208 DST=192.168.2.5 LEN=93 TOS=0x00 PREC=0x00 TTL=112 ID=43871 PROTO=UDP SPT=44233 DPT=15684 LEN=73 
Jun 10 01:26:03 sys-op-dsktp kernel: [  532.196756] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=62.143.159.175 DST=192.168.2.5 LEN=70 TOS=0x00 PREC=0x00 TTL=115 ID=40363 PROTO=UDP SPT=14744 DPT=15684 LEN=50 
Jun 10 01:26:04 sys-op-dsktp kernel: [  532.618776] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=67.185.231.216 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=114 ID=58857 PROTO=UDP SPT=65333 DPT=15684 LEN=71 
Jun 10 01:26:06 sys-op-dsktp kernel: [  534.800095] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=76.172.77.121 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=112 ID=60487 PROTO=UDP SPT=59685 DPT=15684 LEN=71 
Jun 10 01:26:06 sys-op-dsktp kernel: [  535.386471] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=209.131.79.130 DST=192.168.2.5 LEN=70 TOS=0x00 PREC=0x00 TTL=116 ID=12574 PROTO=UDP SPT=54508 DPT=15684 LEN=50 
Jun 10 01:26:08 sys-op-dsktp kernel: [  537.058794] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=213.46.19.145 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=120 ID=32841 PROTO=UDP SPT=30389 DPT=15684 LEN=71 
Jun 10 01:26:11 sys-op-dsktp kernel: [  539.410909] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=24.160.250.191 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=49 ID=5743 PROTO=UDP SPT=13018 DPT=15684 LEN=71 
Jun 10 01:26:11 sys-op-dsktp kernel: [  539.502947] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=86.29.84.17 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=115 ID=5327 PROTO=UDP SPT=32067 DPT=15684 LEN=71 
Jun 10 01:26:12 sys-op-dsktp kernel: [  540.673949] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=90.16.25.132 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=113 ID=26053 PROTO=UDP SPT=48564 DPT=15684 LEN=71 
Jun 10 01:26:12 sys-op-dsktp kernel: [  540.869169] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=79.103.198.216 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=116 ID=51320 PROTO=UDP SPT=51214 DPT=15684 LEN=71 
Jun 10 01:26:15 sys-op-dsktp kernel: [  544.242475] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=82.22.177.16 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=111 ID=13662 PROTO=UDP SPT=6881 DPT=15684 LEN=71 
Jun 10 01:26:16 sys-op-dsktp kernel: [  544.640790] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=71.198.127.127 DST=192.168.2.5 LEN=70 TOS=0x00 PREC=0x00 TTL=108 ID=25072 PROTO=UDP SPT=61225 DPT=15684 LEN=50 
Jun 10 01:26:18 sys-op-dsktp kernel: [  546.762916] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=74.161.68.177 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=114 ID=12114 PROTO=UDP SPT=49111 DPT=15684 LEN=71 
Jun 10 01:26:19 sys-op-dsktp kernel: [  547.691941] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=85.134.8.47 DST=192.168.2.5 LEN=95 TOS=0x00 PREC=0x00 TTL=119 ID=268 PROTO=UDP SPT=41214 DPT=15684 LEN=75 
Jun 10 01:26:26 sys-op-dsktp kernel: [  554.556871] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=77.6.62.135 DST=192.168.2.5 LEN=93 TOS=0x00 PREC=0x00 TTL=114 ID=43663 PROTO=UDP SPT=64646 DPT=15684 LEN=73 
Jun 10 01:26:26 sys-op-dsktp kernel: [  554.885463] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=86.218.22.70 DST=192.168.2.5 LEN=93 TOS=0x00 PREC=0x00 TTL=114 ID=15059 PROTO=UDP SPT=59516 DPT=15684 LEN=73 
Jun 10 01:26:26 sys-op-dsktp kernel: [  554.939042] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=150.101.162.229 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=50 ID=32162 PROTO=UDP SPT=10001 DPT=15684 LEN=71 
Jun 10 01:26:26 sys-op-dsktp kernel: [  555.246511] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=80.216.51.169 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=51 ID=53834 PROTO=UDP SPT=59455 DPT=15684 LEN=71 
Jun 10 01:26:27 sys-op-dsktp kernel: [  556.204413] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=86.8.134.157 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=114 ID=20302 PROTO=UDP SPT=45832 DPT=15684 LEN=71 
Jun 10 01:26:30 sys-op-dsktp kernel: [  559.184395] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=70.241.124.120 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=116 ID=40984 PROTO=UDP SPT=50064 DPT=15684 LEN=71 
Jun 10 01:26:30 sys-op-dsktp kernel: [  559.356098] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=85.228.216.160 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=120 ID=52398 PROTO=UDP SPT=56302 DPT=15684 LEN=71 
Jun 10 01:26:32 sys-op-dsktp kernel: [  560.667937] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=212.195.103.156 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=121 ID=36390 PROTO=UDP SPT=62581 DPT=15684 LEN=71 
Jun 10 01:26:32 sys-op-dsktp kernel: [  561.297535] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=96.224.21.203 DST=192.168.2.5 LEN=93 TOS=0x00 PREC=0x00 TTL=51 ID=37882 PROTO=UDP SPT=50483 DPT=15684 LEN=73 
Jun 10 01:26:34 sys-op-dsktp kernel: [  562.745429] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=82.152.7.137 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=118 ID=6171 PROTO=UDP SPT=64564 DPT=15684 LEN=71 
Jun 10 01:26:34 sys-op-dsktp kernel: [  562.839292] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=72.226.197.11 DST=192.168.2.5 LEN=70 TOS=0x00 PREC=0x00 TTL=51 ID=50226 PROTO=UDP SPT=60619 DPT=15684 LEN=50 
Jun 10 01:26:35 sys-op-dsktp kernel: [  563.571291] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=202.160.13.90 DST=192.168.2.5 LEN=71 TOS=0x00 PREC=0x00 TTL=108 ID=32625 PROTO=UDP SPT=36052 DPT=15684 LEN=51 
Jun 10 01:26:35 sys-op-dsktp kernel: [  564.113845] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=88.7.168.81 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=114 ID=31588 PROTO=UDP SPT=25615 DPT=15684 LEN=71 
Jun 10 01:26:37 sys-op-dsktp kernel: [  565.982970] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=90.133.28.85 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=109 ID=58954 PROTO=UDP SPT=62660 DPT=15684 LEN=71 
Jun 10 01:26:40 sys-op-dsktp kernel: [  568.528694] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=67.167.120.51 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=107 ID=8429 PROTO=UDP SPT=60737 DPT=15684 LEN=71 
Jun 10 01:26:42 sys-op-dsktp kernel: [  570.608143] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=70.160.15.134 DST=192.168.2.5 LEN=93 TOS=0x00 PREC=0x00 TTL=114 ID=31620 PROTO=UDP SPT=53118 DPT=15684 LEN=73 
Jun 10 01:26:42 sys-op-dsktp kernel: [  570.669650] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=96.240.117.202 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=113 ID=59143 PROTO=UDP SPT=49152 DPT=15684 LEN=71 
Jun 10 01:26:43 sys-op-dsktp kernel: [  571.463421] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=65.34.217.235 DST=192.168.2.5 LEN=93 TOS=0x00 PREC=0x00 TTL=99 ID=954 PROTO=UDP SPT=62379 DPT=15684 LEN=73 
Jun 10 01:26:43 sys-op-dsktp kernel: [  572.011951] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=202.160.13.90 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=108 ID=32904 PROTO=UDP SPT=36052 DPT=15684 LEN=71 
Jun 10 01:26:44 sys-op-dsktp kernel: [  572.739214] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=82.231.151.4 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=118 ID=8602 PROTO=UDP SPT=6881 DPT=15684 LEN=71 
Jun 10 01:26:44 sys-op-dsktp kernel: [  572.774142] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=58.109.76.233 DST=192.168.2.5 LEN=93 TOS=0x00 PREC=0x00 TTL=108 ID=14817 PROTO=UDP SPT=55000 DPT=15684 LEN=73 
Jun 10 01:26:44 sys-op-dsktp kernel: [  572.816482] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=79.101.66.206 DST=192.168.2.5 LEN=71 TOS=0x00 PREC=0x00 TTL=111 ID=53391 PROTO=UDP SPT=57882 DPT=15684 LEN=51 
Jun 10 01:26:48 sys-op-dsktp kernel: [  576.527563] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=78.53.53.251 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=118 ID=17387 PROTO=UDP SPT=14229 DPT=15684 LEN=71 
Jun 10 01:26:52 sys-op-dsktp kernel: [  580.829506] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=96.240.117.202 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=113 ID=62306 PROTO=UDP SPT=49152 DPT=15684 LEN=71 
Jun 10 01:26:53 sys-op-dsktp kernel: [  582.150384] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=76.64.59.59 DST=192.168.2.5 LEN=93 TOS=0x00 PREC=0x00 TTL=42 ID=11309 PROTO=UDP SPT=48086 DPT=15684 LEN=73 
Jun 10 01:26:54 sys-op-dsktp kernel: [  583.347592] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=24.7.181.79 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=106 ID=15371 PROTO=UDP SPT=49247 DPT=15684 LEN=71 
Jun 10 01:26:58 sys-op-dsktp kernel: [  586.370650] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=80.174.156.190 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=113 ID=47879 PROTO=UDP SPT=11351 DPT=15684 LEN=71 
Jun 10 01:26:58 sys-op-dsktp kernel: [  586.420741] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=85.137.29.76 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=116 ID=23077 PROTO=UDP SPT=58631 DPT=15684 LEN=71 
Jun 10 01:26:58 sys-op-dsktp kernel: [  586.621731] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=202.160.13.90 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=108 ID=33495 PROTO=UDP SPT=36052 DPT=15684 LEN=71 
Jun 10 01:26:59 sys-op-dsktp kernel: [  587.779469] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=68.48.89.141 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=40 ID=39093 PROTO=UDP SPT=59879 DPT=15684 LEN=71 
Jun 10 01:27:00 sys-op-dsktp kernel: [  588.521400] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=82.22.177.16 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=111 ID=20399 PROTO=UDP SPT=6881 DPT=15684 LEN=71 
Jun 10 01:27:02 sys-op-dsktp kernel: [  590.525327] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=76.118.30.103 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=105 ID=6962 PROTO=UDP SPT=40678 DPT=15684 LEN=71 
Jun 10 01:27:05 sys-op-dsktp kernel: [  594.140829] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=78.51.76.137 DST=192.168.2.5 LEN=93 TOS=0x00 PREC=0x00 TTL=120 ID=10390 PROTO=UDP SPT=55555 DPT=15684 LEN=73 
Jun 10 01:27:06 sys-op-dsktp kernel: [  594.788521] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=68.149.234.113 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=115 ID=21700 PROTO=UDP SPT=12073 DPT=15684 LEN=71 
Jun 10 01:27:06 sys-op-dsktp kernel: [  595.039865] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=92.17.153.55 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=116 ID=11985 PROTO=UDP SPT=18440 DPT=15684 LEN=71 
Jun 10 01:27:07 sys-op-dsktp kernel: [  595.449998] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=89.14.199.80 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=55 ID=0 DF PROTO=UDP SPT=54377 DPT=15684 LEN=71 
Jun 10 01:27:08 sys-op-dsktp kernel: [  596.505239] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=92.97.193.217 DST=192.168.2.5 LEN=93 TOS=0x00 PREC=0x00 TTL=115 ID=19353 PROTO=UDP SPT=25334 DPT=15684 LEN=73 
Jun 10 01:27:11 sys-op-dsktp kernel: [  600.090773] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=82.173.205.246 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=119 ID=11758 PROTO=UDP SPT=60641 DPT=15684 LEN=71 
Jun 10 01:27:12 sys-op-dsktp kernel: [  600.447226] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=82.249.55.161 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=118 ID=8526 PROTO=UDP SPT=51480 DPT=15684 LEN=71 
Jun 10 01:27:12 sys-op-dsktp kernel: [  601.292076] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=80.121.33.73 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=56 ID=40069 PROTO=UDP SPT=35051 DPT=15684 LEN=71 
Jun 10 01:27:19 sys-op-dsktp kernel: [  607.378868] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=212.195.103.156 DST=192.168.2.5 LEN=70 TOS=0x00 PREC=0x00 TTL=121 ID=38833 PROTO=UDP SPT=62581 DPT=15684 LEN=50 
Jun 10 01:27:22 sys-op-dsktp kernel: [  610.571656] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=78.86.119.212 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=117 ID=17455 PROTO=UDP SPT=63838 DPT=15684 LEN=71 
Jun 10 01:27:22 sys-op-dsktp kernel: [  610.720715] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=82.69.109.60 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=112 ID=18137 PROTO=UDP SPT=27893 DPT=15684 LEN=71 
Jun 10 01:27:23 sys-op-dsktp kernel: [  611.930604] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=88.7.180.33 DST=192.168.2.5 LEN=70 TOS=0x00 PREC=0x00 TTL=114 ID=50043 PROTO=UDP SPT=4662 DPT=15684 LEN=50 
Jun 10 01:27:24 sys-op-dsktp kernel: [  612.517066] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=82.229.211.97 DST=192.168.2.5 LEN=93 TOS=0x00 PREC=0x00 TTL=120 ID=45876 PROTO=UDP SPT=65294 DPT=15684 LEN=73 
Jun 10 01:27:28 sys-op-dsktp kernel: [  617.167739] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=68.111.64.229 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=115 ID=7751 PROTO=UDP SPT=23448 DPT=15684 LEN=71 
Jun 10 01:27:28 sys-op-dsktp kernel: [  617.212273] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=81.98.250.5 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=115 ID=251 PROTO=UDP SPT=55066 DPT=15684 LEN=71 
Jun 10 01:27:32 sys-op-dsktp kernel: [  620.917696] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=84.156.54.82 DST=192.168.2.5 LEN=93 TOS=0x00 PREC=0x00 TTL=117 ID=31906 PROTO=UDP SPT=11353 DPT=15684 LEN=73 
Jun 10 01:27:33 sys-op-dsktp kernel: [  621.779956] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=81.210.117.138 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=113 ID=3518 PROTO=UDP SPT=6887 DPT=15684 LEN=71 
Jun 10 01:27:34 sys-op-dsktp kernel: [  622.934256] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=124.110.189.82 DST=192.168.2.5 LEN=70 TOS=0x00 PREC=0x00 TTL=110 ID=875 PROTO=UDP SPT=38528 DPT=15684 LEN=50 
Jun 10 01:27:36 sys-op-dsktp kernel: [  624.871141] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=150.101.162.229 DST=192.168.2.5 LEN=70 TOS=0x00 PREC=0x00 TTL=50 ID=36589 PROTO=UDP SPT=10001 DPT=15684 LEN=50 
Jun 10 01:27:39 sys-op-dsktp kernel: [  627.477009] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=87.78.252.111 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=53 ID=17519 PROTO=UDP SPT=48165 DPT=15684 LEN=71 
Jun 10 01:27:40 sys-op-dsktp kernel: [  628.804867] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=12.215.209.34 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=116 ID=23695 PROTO=UDP SPT=63143 DPT=15684 LEN=71 
Jun 10 01:27:41 sys-op-dsktp kernel: [  629.355653] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=88.7.168.81 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=114 ID=2407 PROTO=UDP SPT=25615 DPT=15684 LEN=71 
Jun 10 01:27:41 sys-op-dsktp kernel: [  630.067842] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=72.226.197.11 DST=192.168.2.5 LEN=70 TOS=0x00 PREC=0x00 TTL=51 ID=24604 PROTO=UDP SPT=60619 DPT=15684 LEN=50 
Jun 10 01:27:44 sys-op-dsktp kernel: [  632.952876] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=87.175.94.116 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=118 ID=13735 PROTO=UDP SPT=15743 DPT=15684 LEN=71 
Jun 10 01:27:45 sys-op-dsktp kernel: [  633.980041] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=202.160.13.90 DST=192.168.2.5 LEN=71 TOS=0x00 PREC=0x00 TTL=108 ID=35545 PROTO=UDP SPT=36052 DPT=15684 LEN=51 
Jun 10 01:27:47 sys-op-dsktp kernel: [  635.722385] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=82.31.217.28 DST=192.168.2.5 LEN=91 TOS=0x00 PREC=0x00 TTL=114 ID=42561 PROTO=UDP SPT=32768 DPT=15684 LEN=71 
Jun 10 01:27:47 sys-op-dsktp kernel: [  635.794472] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=88.7.168.81 DST=192.168.2.5 LEN=70 TOS=0x00 PREC=0x00 TTL=114 ID=2711 PROTO=UDP SPT=25615 DPT=15684 LEN=50 
Jun 10 01:27:48 sys-op-dsktp kernel: [  636.992059] Inbound IN=wlan0 OUT= MAC=00:1c:10:65:8f:b4:00:01:e3:e4:c4:4b:08:00 SRC=86.11.107.121 DST=192.168.2.5

This all happens in just a few minutes and keeps going on like this.

Hope someone can help me out with this cause I start to worry.. :)

Kind regards,

ReLexEd.

---

### Post by HalPomeranz on 2008-06-09
Looks like the traffic is all happening on port 15684, so I recommend you run "sudo lsof -i :15684".  That should show you what process is listening on that port.

---

### Post by acrostic on 2008-06-10
Some application on your machine is listening on UDP port 15684 , which is getting connections from internet.

to identify this process you could issue following command

sudo netstat -panu |grep 15684

Paste the output here if you do not recognize the application name.

---

