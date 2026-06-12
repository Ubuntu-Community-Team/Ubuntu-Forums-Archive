---
title: "Kernel Panic, cpqphp module, Compaq/HP Proliant ML570 G2"
date: 2009-01-04
forum: Server Platforms
---

### Post by rbcurtis on 2009-01-04
I'm getting a non-fatal kernel panic when booting an ML570 on hardy / server.  Boot continues after panic, but I'd like to clean this up if possible.  I do not have any devices I'd like to hotplug, so disabling hotplug altogether is not unreasonable for my needs...

Apropos snippet here, full boot log below:


```
Jan  4 11:48:42 unleaded kernel: [    6.331049] udevd version 124 started
Jan  4 11:48:42 unleaded kernel: [    7.131284] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jan  4 11:48:42 unleaded kernel: [    7.158803] cpqphp: Compaq Hot Plug PCI Controller Driver version: 0.9.8
Jan  4 11:48:42 unleaded kernel: [    7.159005] compaq_pci_hotplug 0000:01:1e.0: PCI INT A -> GSI 34 (level, low) -> IRQ 34
Jan  4 11:48:42 unleaded kernel: [    7.159113] cpqphp: Hot Plug Subsystem Device ID: a2fe
Jan  4 11:48:42 unleaded kernel: [    7.159190] cpqphp: Initializing the PCI hot plug controller residing on PCI bus 1
Jan  4 11:48:42 unleaded kernel: [    7.159292] PCI: Using BIOS Interrupt Routing Table
Jan  4 11:48:42 unleaded kernel: [    7.159480] PCI: Using BIOS Interrupt Routing Table
Jan  4 11:48:42 unleaded kernel: [    7.168071] *pdpt = 0000000037cf9001 *pde = 0000000000000000
Jan  4 11:48:42 unleaded kernel: [    7.168410] Modules linked in: cpqphp(+) pci_hotplug ext3 jbd mbcache sr_mod cdrom sg ata_generic pata_acpi pata_serverworks libata ohci_hcd e100 cciss mii usbcore scsi_mod dock dm_snapshot thermal processor fan fbcon tileblit font bitblit softcursor fuse dm_raid4_5 dm_region_hash dm_mem_cache dm_message dm_mirror dm_log dm_mod
Jan  4 11:48:42 unleaded kernel: [    7.170319]
Jan  4 11:48:42 unleaded kernel: [    7.170388] Pid: 2717, comm: modprobe Not tainted (2.6.27-9-server #1)
Jan  4 11:48:42 unleaded kernel: [    7.170474] EIP: 0060:[<c026b1a4>] EFLAGS: 00010213 CPU: 2
Jan  4 11:48:42 unleaded kernel: [    7.170557] EIP is at pci_create_slot+0x24/0x110
Jan  4 11:48:42 unleaded kernel: [    7.170646] EAX: c048e168 EBX: 00000001 ECX: f5546cb0 EDX: 00000000
Jan  4 11:48:42 unleaded kernel: [    7.170736] ESI: f78c0c60 EDI: 00000000 EBP: f7db7d18 ESP: f7db7cf4
Jan  4 11:48:42 unleaded kernel: [    7.170815]  DS: 007b ES: 007b FS: 00d8 GS: 0033 SS: 0068
Jan  4 11:48:42 unleaded kernel: [    7.181512] ---[ end trace 7ee6509651b16fae ]---
```

Full Boot log:

```

Jan  4 12:23:20 unleaded syslogd 1.5.0#2ubuntu6: restart.
Jan  4 12:23:20 unleaded kernel: Inspecting /boot/System.map-2.6.27-9-server
Jan  4 12:23:20 unleaded kernel: Cannot find map file.
Jan  4 12:23:20 unleaded kernel: Loaded 45243 symbols from 61 modules.
Jan  4 12:23:20 unleaded kernel: [    0.000000] Initializing cgroup subsys cpuset
Jan  4 12:23:20 unleaded kernel: [    0.000000] Initializing cgroup subsys cpu
Jan  4 12:23:20 unleaded kernel: [    0.000000] Linux version 2.6.27-9-server (buildd@rothera) (gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) ) #1 SMP Thu Nov 20 22:53:41 UTC 2008 (Ubuntu 2.6.27-9.19-server)
Jan  4 12:23:20 unleaded kernel: [    0.000000] BIOS-provided physical RAM map:
Jan  4 12:23:20 unleaded kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f400 (usable)
Jan  4 12:23:20 unleaded kernel: [    0.000000]  BIOS-e820: 000000000009f400 - 00000000000a0000 (reserved)
Jan  4 12:23:20 unleaded kernel: [    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Jan  4 12:23:20 unleaded kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 00000000bfff8000 (usable)
Jan  4 12:23:20 unleaded kernel: [    0.000000]  BIOS-e820: 00000000bfff8000 - 00000000c0000000 (ACPI data)
Jan  4 12:23:20 unleaded kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
Jan  4 12:23:20 unleaded kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee10000 (reserved)
Jan  4 12:23:20 unleaded kernel: [    0.000000]  BIOS-e820: 00000000ffc00000 - 0000000100000000 (reserved)
Jan  4 12:23:20 unleaded kernel: [    0.000000] last_pfn = 0xbfff8 max_arch_pfn = 0x1000000
Jan  4 12:23:20 unleaded kernel: [    0.000000] RAMDISK: 007b9000 - 00fffac0
Jan  4 12:23:20 unleaded kernel: [    0.000000] DMI 2.3 present.
Jan  4 12:23:20 unleaded kernel: [    0.000000] ACPI: RSDP 000F4F70, 0014 (r0 COMPAQ)
Jan  4 12:23:20 unleaded kernel: [    0.000000] ACPI: RSDT BFFF8000, 0038 (r1 COMPAQ P32             2   Ò^D     162E)
Jan  4 12:23:20 unleaded kernel: [    0.000000] ACPI: FACP BFFF8040, 0074 (r1 COMPAQ P32             2   Ò^D     162E)
Jan  4 12:23:20 unleaded kernel: [    0.000000] ACPI: DSDT BFFF82C0, 45C4 (r1 COMPAQ     DSDT        1 MSFT  100000B)
Jan  4 12:23:20 unleaded kernel: [    0.000000] ACPI: FACS BFFF80C0, 0040
Jan  4 12:23:20 unleaded kernel: [    0.000000] ACPI: APIC BFFF8100, 00AC (r1 COMPAQ 00000083        2             0)
Jan  4 12:23:20 unleaded kernel: [    0.000000] ACPI: SPCR BFFF81C0, 0050 (r1 COMPAQ SPCRRBSU        1   Ò^D     162E)
Jan  4 12:23:20 unleaded kernel: [    0.000000] ACPI: SRAT BFFF8240, 0058 (r1 HP     P32             1             0)
Jan  4 12:23:20 unleaded kernel: [    0.000000] ACPI: SSDT BFFFE000, 02EF (r1 COMPAQ     SSDT        1 MSFT  100000B)
Jan  4 12:23:20 unleaded kernel: [    0.000000] 2175MB HIGHMEM available.
Jan  4 12:23:20 unleaded kernel: [    0.000000] 896MB LOWMEM available.
Jan  4 12:23:20 unleaded kernel: [    0.000000]   mapped low ram: 0 - 38000000
Jan  4 12:23:20 unleaded kernel: [    0.000000]   low ram: 00000000 - 38000000
Jan  4 12:23:20 unleaded kernel: [    0.000000]   bootmap 00009000 - 00010000
Jan  4 12:23:20 unleaded kernel: [    0.000000] (9 early reservations) ==> bootmem [0000000000 - 0038000000]
Jan  4 12:23:20 unleaded kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
Jan  4 12:23:20 unleaded kernel: [    0.000000]   #1 [0000001000 - 0000002000]    EX TRAMPOLINE ==> [0000001000 - 0000002000]
Jan  4 12:23:20 unleaded kernel: [    0.000000]   #2 [0000006000 - 0000007000]       TRAMPOLINE ==> [0000006000 - 0000007000]
Jan  4 12:23:20 unleaded kernel: [    0.000000]   #3 [0000100000 - 00005e8220]    TEXT DATA BSS ==> [0000100000 - 00005e8220]
Jan  4 12:23:20 unleaded kernel: [    0.000000]   #4 [00007b9000 - 0000fffac0]          RAMDISK ==> [00007b9000 - 0000fffac0]
Jan  4 12:23:20 unleaded kernel: [    0.000000]   #5 [00005e9000 - 00005f1000]    INIT_PG_TABLE ==> [00005e9000 - 00005f1000]
Jan  4 12:23:20 unleaded kernel: [    0.000000]   #6 [000009f400 - 0000100000]    BIOS reserved ==> [000009f400 - 0000100000]
Jan  4 12:23:20 unleaded kernel: [    0.000000]   #7 [0000007000 - 0000009000]          PGTABLE ==> [0000007000 - 0000009000]
Jan  4 12:23:20 unleaded kernel: [    0.000000]   #8 [0000009000 - 0000010000]          BOOTMAP ==> [0000009000 - 0000010000]
Jan  4 12:23:20 unleaded kernel: [    0.000000] found SMP MP-table at [c00f4fd0] 000f4fd0
Jan  4 12:23:20 unleaded kernel: [    0.000000] Zone PFN ranges:
Jan  4 12:23:20 unleaded kernel: [    0.000000]   DMA      0x00000000 -> 0x00001000
Jan  4 12:23:20 unleaded kernel: [    0.000000]   Normal   0x00001000 -> 0x00038000
Jan  4 12:23:20 unleaded kernel: [    0.000000]   HighMem  0x00038000 -> 0x000bfff8
Jan  4 12:23:20 unleaded kernel: [    0.000000] Movable zone start PFN for each node
Jan  4 12:23:20 unleaded kernel: [    0.000000] early_node_map[2] active PFN ranges
Jan  4 12:23:20 unleaded kernel: [    0.000000]     0: 0x00000000 -> 0x0000009f
Jan  4 12:23:20 unleaded kernel: [    0.000000]     0: 0x00000100 -> 0x000bfff8
Jan  4 12:23:20 unleaded kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x920
Jan  4 12:23:20 unleaded kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] disabled)
Jan  4 12:23:20 unleaded kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
Jan  4 12:23:20 unleaded kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x04] enabled)
Jan  4 12:23:20 unleaded kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x06] enabled)
Jan  4 12:23:20 unleaded kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
Jan  4 12:23:20 unleaded kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
Jan  4 12:23:20 unleaded kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x05] enabled)
Jan  4 12:23:20 unleaded kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x07] enabled)
Jan  4 12:23:20 unleaded kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0xff] dfl dfl lint[0x1])
Jan  4 12:23:20 unleaded kernel: [    0.000000] ACPI: IOAPIC (id[0x08] address[0xfec00000] gsi_base[0])
Jan  4 12:23:20 unleaded kernel: [    0.000000] IOAPIC[0]: apic_id 8, version 17, address 0xfec00000, GSI 0-15
Jan  4 12:23:20 unleaded kernel: [    0.000000] ACPI: IOAPIC (id[0x09] address[0xfec01000] gsi_base[16])
Jan  4 12:23:20 unleaded kernel: [    0.000000] IOAPIC[1]: apic_id 9, version 17, address 0xfec01000, GSI 16-31
Jan  4 12:23:20 unleaded kernel: [    0.000000] ACPI: IOAPIC (id[0x0a] address[0xfec02000] gsi_base[32])
Jan  4 12:23:20 unleaded kernel: [    0.000000] IOAPIC[2]: apic_id 10, version 17, address 0xfec02000, GSI 32-47
Jan  4 12:23:20 unleaded kernel: [    0.000000] ACPI: IOAPIC (id[0x0b] address[0xfec03000] gsi_base[48])
Jan  4 12:23:20 unleaded kernel: [    0.000000] IOAPIC[3]: apic_id 11, version 17, address 0xfec03000, GSI 48-63
Jan  4 12:23:20 unleaded kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
Jan  4 12:23:20 unleaded kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 4 I/O APICs
Jan  4 12:23:20 unleaded kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Jan  4 12:23:20 unleaded kernel: [    0.000000] SMP: Allowing 8 CPUs, 4 hotplug CPUs
Jan  4 12:23:20 unleaded kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Jan  4 12:23:20 unleaded kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
Jan  4 12:23:20 unleaded kernel: [    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
Jan  4 12:23:20 unleaded kernel: [    0.000000] Allocating PCI resources starting at c4000000 (gap: c0000000:3ec00000)
Jan  4 12:23:20 unleaded kernel: [    0.000000] PERCPU: Allocating 45852 bytes of per cpu data
Jan  4 12:23:20 unleaded kernel: [    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 779415
Jan  4 12:23:20 unleaded kernel: [    0.000000] Kernel command line: BOOT_IMAGE=Linux ro root=/dev/mapper/unleaded-unleaded--root rootdelay=45
Jan  4 12:23:20 unleaded kernel: [    0.000000] Enabling fast FPU save and restore... done.
Jan  4 12:23:20 unleaded kernel: [    0.000000] Enabling unmasked SIMD FPU exception support... done.
Jan  4 12:23:20 unleaded kernel: [    0.000000] Initializing CPU#0
Jan  4 12:23:20 unleaded kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
Jan  4 12:23:20 unleaded kernel: [    0.000000] TSC: PIT calibration confirmed by PMTIMER.
Jan  4 12:23:20 unleaded kernel: [    0.000000] TSC: using PMTIMER calibration value
Jan  4 12:23:20 unleaded kernel: [    0.000000] Detected 1996.117 MHz processor.
Jan  4 12:23:20 unleaded kernel: [    0.010000] Console: colour VGA+ 80x25
Jan  4 12:23:20 unleaded kernel: [    0.010000] console [tty0] enabled
Jan  4 12:23:20 unleaded kernel: [    0.010000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Jan  4 12:23:20 unleaded kernel: [    0.010000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Jan  4 12:23:20 unleaded kernel: [    0.010000] Memory: 3102020k/3145696k available (2628k kernel code, 42456k reserved, 1201k data, 436k init, 2228192k highmem)
Jan  4 12:23:20 unleaded kernel: [    0.010000] virtual kernel memory layout:
Jan  4 12:23:20 unleaded kernel: [    0.010000]     fixmap  : 0xffc78000 - 0xfffff000   (3612 kB)
Jan  4 12:23:20 unleaded kernel: [    0.010000]     pkmap   : 0xff800000 - 0xffa00000   (2048 kB)
Jan  4 12:23:20 unleaded kernel: [    0.010000]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
Jan  4 12:23:20 unleaded kernel: [    0.010000]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
Jan  4 12:23:20 unleaded kernel: [    0.010000]       .init : 0xc04c3000 - 0xc0530000   ( 436 kB)
Jan  4 12:23:20 unleaded kernel: [    0.010000]       .data : 0xc03910d6 - 0xc04bd800   (1201 kB)
Jan  4 12:23:20 unleaded kernel: [    0.010000]       .text : 0xc0100000 - 0xc03910d6   (2628 kB)
Jan  4 12:23:20 unleaded kernel: [    0.010000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
Jan  4 12:23:20 unleaded kernel: [    0.010000] SLUB: Genslabs=12, HWalign=128, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
Jan  4 12:23:20 unleaded kernel: [    0.010020] Calibrating delay loop (skipped), value calculated using timer frequency.. 3992.23 BogoMIPS (lpj=19961170)
Jan  4 12:23:20 unleaded kernel: [    0.010188] Security Framework initialized
Jan  4 12:23:20 unleaded kernel: [    0.010267] SELinux:  Disabled at boot.
Jan  4 12:23:20 unleaded kernel: [    0.010372] AppArmor: AppArmor initialized
Jan  4 12:23:20 unleaded kernel: [    0.010460] Mount-cache hash table entries: 512
Jan  4 12:23:20 unleaded kernel: [    0.010913] Initializing cgroup subsys ns
Jan  4 12:23:20 unleaded kernel: [    0.010986] Initializing cgroup subsys cpuacct
Jan  4 12:23:20 unleaded kernel: [    0.011058] Initializing cgroup subsys memory
Jan  4 12:23:20 unleaded kernel: [    0.011152] CPU: Trace cache: 12K uops, L1 D cache: 8K
Jan  4 12:23:20 unleaded kernel: [    0.011269] CPU: L2 cache: 512K
Jan  4 12:23:20 unleaded kernel: [    0.011336] CPU: L3 cache: 1024K
Jan  4 12:23:20 unleaded kernel: [    0.011403] CPU: Physical Processor ID: 2
Jan  4 12:23:20 unleaded kernel: [    0.011489] Checking 'hlt' instruction... OK.
Jan  4 12:23:20 unleaded kernel: [    0.053523] ACPI: Core revision 20080609
Jan  4 12:23:20 unleaded kernel: [    0.057553] ACPI: Checking initramfs for custom DSDT
Jan  4 12:23:20 unleaded kernel: [    0.580719] ENABLING IO-APIC IRQs
Jan  4 12:23:20 unleaded kernel: [    0.581004] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Jan  4 12:23:20 unleaded kernel: [    0.689480] CPU0: Intel(R) Xeon(TM) MP CPU 2.00GHz stepping 05
Jan  4 12:23:20 unleaded kernel: [    0.690000] Booting processor 1/6 ip 6000
Jan  4 12:23:20 unleaded kernel: [    0.010000] Initializing CPU#1
Jan  4 12:23:20 unleaded kernel: [    0.010000] Calibrating delay using timer specific routine.. 3992.43 BogoMIPS (lpj=19962176)
Jan  4 12:23:20 unleaded kernel: [    0.010000] CPU: Trace cache: 12K uops, L1 D cache: 8K
Jan  4 12:23:20 unleaded kernel: [    0.010000] CPU: L2 cache: 512K
Jan  4 12:23:20 unleaded kernel: [    0.010000] CPU: L3 cache: 1024K
Jan  4 12:23:20 unleaded kernel: [    0.010000] CPU: Physical Processor ID: 3
Jan  4 12:23:20 unleaded kernel: [    0.840541] CPU1: Intel(R) Xeon(TM) MP CPU 2.00GHz stepping 05
Jan  4 12:23:20 unleaded kernel: [    0.841121] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
Jan  4 12:23:20 unleaded kernel: [    0.850154] Booting processor 2/5 ip 6000
Jan  4 12:23:20 unleaded kernel: [    0.010000] Initializing CPU#2
Jan  4 12:23:20 unleaded kernel: [    0.010000] Calibrating delay using timer specific routine.. 3992.32 BogoMIPS (lpj=19961623)
Jan  4 12:23:20 unleaded kernel: [    0.010000] CPU: Trace cache: 12K uops, L1 D cache: 8K
Jan  4 12:23:20 unleaded kernel: [    0.010000] CPU: L2 cache: 512K
Jan  4 12:23:20 unleaded kernel: [    0.010000] CPU: L3 cache: 1024K
Jan  4 12:23:20 unleaded kernel: [    0.010000] CPU: Physical Processor ID: 2
Jan  4 12:23:20 unleaded kernel: [    1.010549] CPU2: Intel(R) Xeon(TM) MP CPU 2.00GHz stepping 05
Jan  4 12:23:20 unleaded kernel: [    1.011157] checking TSC synchronization [CPU#0 -> CPU#2]: passed.
Jan  4 12:23:20 unleaded kernel: [    1.020248] Booting processor 3/7 ip 6000
Jan  4 12:23:20 unleaded kernel: [    0.010000] Initializing CPU#3
Jan  4 12:23:20 unleaded kernel: [    0.010000] Calibrating delay using timer specific routine.. 3992.44 BogoMIPS (lpj=19962228)
Jan  4 12:23:20 unleaded kernel: [    0.010000] CPU: Trace cache: 12K uops, L1 D cache: 8K
Jan  4 12:23:20 unleaded kernel: [    0.010000] CPU: L2 cache: 512K
Jan  4 12:23:20 unleaded kernel: [    0.010000] CPU: L3 cache: 1024K
Jan  4 12:23:20 unleaded kernel: [    0.010000] CPU: Physical Processor ID: 3
Jan  4 12:23:20 unleaded kernel: [    1.180523] CPU3: Intel(R) Xeon(TM) MP CPU 2.00GHz stepping 05
Jan  4 12:23:20 unleaded kernel: [    1.181121] checking TSC synchronization [CPU#0 -> CPU#3]: passed.
Jan  4 12:23:20 unleaded kernel: [    1.190015] Brought up 4 CPUs
Jan  4 12:23:20 unleaded kernel: [    1.190091] Total of 4 processors activated (15969.43 BogoMIPS).
Jan  4 12:23:20 unleaded kernel: [    1.190538] net_namespace: 840 bytes
Jan  4 12:23:20 unleaded kernel: [    1.190538] Booting paravirtualized kernel on bare hardware
Jan  4 12:23:20 unleaded kernel: [    1.190653] Time: 12:20:42  Date: 01/04/09
Jan  4 12:23:20 unleaded kernel: [    1.190776] NET: Registered protocol family 16
Jan  4 12:23:20 unleaded kernel: [    1.190884] EISA bus registered
Jan  4 12:23:20 unleaded kernel: [    1.190884] ACPI: bus type pci registered
Jan  4 12:23:20 unleaded kernel: [    1.207950] PCI: PCI BIOS revision 2.10 entry at 0xf0094, last bus=16
Jan  4 12:23:20 unleaded kernel: [    1.208025] PCI: Using configuration type 1 for base access
Jan  4 12:23:20 unleaded kernel: [    1.208140] mtrr: your CPUs had inconsistent fixed MTRR settings
Jan  4 12:23:20 unleaded kernel: [    1.208140] mtrr: probably your BIOS does not setup all CPUs.
Jan  4 12:23:20 unleaded kernel: [    1.210003] mtrr: corrected configuration.
Jan  4 12:23:20 unleaded kernel: [    1.228576] ACPI: Interpreter enabled
Jan  4 12:23:20 unleaded kernel: [    1.228649] ACPI: (supports S0 S4 S5)
Jan  4 12:23:20 unleaded kernel: [    1.228870] ACPI: Using IOAPIC for interrupt routing
Jan  4 12:23:20 unleaded kernel: [    1.240746] ACPI: PCI Root Bridge [PCI0] (0000:00)
Jan  4 12:23:20 unleaded kernel: [    1.240746] pci 0000:00:04.0: PME# supported from D0 D1 D2 D3hot D3cold
Jan  4 12:23:20 unleaded kernel: [    1.240746] pci 0000:00:04.0: PME# disabled
Jan  4 12:23:20 unleaded kernel: [    1.250461] ACPI: PCI Root Bridge [PCI1] (0000:01)
Jan  4 12:23:20 unleaded kernel: [    1.250684] ACPI: PCI Root Bridge [PCI5] (0000:05)
Jan  4 12:23:20 unleaded kernel: [    1.250946] ACPI: PCI Root Bridge [PCI9] (0000:09)
Jan  4 12:23:20 unleaded kernel: [    1.250946] ACPI: PCI Root Bridge [PCID] (0000:0d)
Jan  4 12:23:20 unleaded kernel: [    1.250946] ACPI: PCI Interrupt Link [IUSB] (IRQs 4 5 7 10 *11 15)
Jan  4 12:23:20 unleaded kernel: [    1.251034] ACPI: PCI Interrupt Link [IN16] (IRQs 4 5 7 10 11 15) *0, disabled.
Jan  4 12:23:20 unleaded kernel: [    1.251906] ACPI: PCI Interrupt Link [IN17] (IRQs 4 5 7 10 11 15) *0, disabled.
Jan  4 12:23:20 unleaded kernel: [    1.252776] ACPI: PCI Interrupt Link [IN18] (IRQs 4 5 7 10 11 15) *0, disabled.
Jan  4 12:23:20 unleaded kernel: [    1.253659] ACPI: PCI Interrupt Link [IN19] (IRQs 4 5 7 10 11 15) *0, disabled.
Jan  4 12:23:20 unleaded kernel: [    1.260562] ACPI: PCI Interrupt Link [IN20] (IRQs 4 5 7 10 11 *15)
Jan  4 12:23:20 unleaded kernel: [    1.261336] ACPI: PCI Interrupt Link [IN21] (IRQs 4 5 7 10 11 15) *0, disabled.
Jan  4 12:23:20 unleaded kernel: [    1.262209] ACPI: PCI Interrupt Link [IN22] (IRQs 4 5 7 10 11 15) *0, disabled.
Jan  4 12:23:20 unleaded kernel: [    1.263078] ACPI: PCI Interrupt Link [IN23] (IRQs 4 5 7 10 11 15) *0, disabled.
Jan  4 12:23:20 unleaded kernel: [    1.263950] ACPI: PCI Interrupt Link [IN24] (IRQs 4 5 7 10 11 15) *0, disabled.
Jan  4 12:23:20 unleaded kernel: [    1.264821] ACPI: PCI Interrupt Link [IN25] (IRQs 4 5 7 10 11 15) *0, disabled.
Jan  4 12:23:20 unleaded kernel: [    1.265692] ACPI: PCI Interrupt Link [IN26] (IRQs 4 5 7 10 11 15) *0, disabled.
Jan  4 12:23:20 unleaded kernel: [    1.266563] ACPI: PCI Interrupt Link [IN27] (IRQs 4 5 7 10 11 15) *0, disabled.
Jan  4 12:23:20 unleaded kernel: [    1.267434] ACPI: PCI Interrupt Link [IN28] (IRQs 4 5 7 10 11 15) *3
Jan  4 12:23:20 unleaded kernel: [    1.268245] ACPI: PCI Interrupt Link [IN29] (IRQs 4 5 7 *10 11 15)
Jan  4 12:23:20 unleaded kernel: [    1.269019] ACPI: PCI Interrupt Link [IN30] (IRQs 4 5 7 10 11 15) *0, disabled.
Jan  4 12:23:20 unleaded kernel: [    1.269892] ACPI: PCI Interrupt Link [IN31] (IRQs 4 5 7 10 11 15) *0, disabled.
Jan  4 12:23:20 unleaded kernel: [    1.270776] ACPI: PCI Interrupt Link [IN32] (IRQs 4 5 7 10 11 15) *0, disabled.
Jan  4 12:23:20 unleaded kernel: [    1.271657] ACPI: PCI Interrupt Link [IN33] (IRQs 4 5 7 10 11 15) *0, disabled.
Jan  4 12:23:20 unleaded kernel: [    1.272531] ACPI: PCI Interrupt Link [IN34] (IRQs 4 5 7 10 *11 15)
Jan  4 12:23:20 unleaded kernel: [    1.273143] Linux Plug and Play Support v0.97 (c) Adam Belay
Jan  4 12:23:20 unleaded kernel: [    1.273143] pnp: PnP ACPI init
Jan  4 12:23:20 unleaded kernel: [    1.273143] ACPI: bus type pnp registered
Jan  4 12:23:20 unleaded kernel: [    1.283108] pnp: PnP ACPI: found 15 devices
Jan  4 12:23:20 unleaded kernel: [    1.283180] ACPI: ACPI bus type pnp unregistered
Jan  4 12:23:20 unleaded kernel: [    1.283250] PnPBIOS: Disabled by ACPI PNP
Jan  4 12:23:20 unleaded kernel: [    1.283359] PCI: Using ACPI for IRQ routing
Jan  4 12:23:20 unleaded kernel: [    1.310026] NET: Registered protocol family 8
Jan  4 12:23:20 unleaded kernel: [    1.310098] NET: Registered protocol family 20
Jan  4 12:23:20 unleaded kernel: [    1.310210] NetLabel: Initializing
Jan  4 12:23:20 unleaded kernel: [    1.310210] NetLabel:  domain hash size = 128
Jan  4 12:23:20 unleaded kernel: [    1.310210] NetLabel:  protocols = UNLABELED CIPSOv4
Jan  4 12:23:20 unleaded kernel: [    1.310244] NetLabel:  unlabeled traffic allowed by default
Jan  4 12:23:20 unleaded kernel: [    1.314523] tracer: 772 pages allocated for 65536 entries of 48 bytes
Jan  4 12:23:20 unleaded kernel: [    1.314598]    actual entries 65620
Jan  4 12:23:20 unleaded kernel: [    1.314896] AppArmor: AppArmor Filesystem Enabled
Jan  4 12:23:20 unleaded kernel: [    1.330054] system 00:01: ioport range 0xf50-0xf58 has been reserved
Jan  4 12:23:20 unleaded kernel: [    1.330129] system 00:01: ioport range 0x408-0x40f has been reserved
Jan  4 12:23:20 unleaded kernel: [    1.330203] system 00:01: ioport range 0x900-0x903 has been reserved
Jan  4 12:23:20 unleaded kernel: [    1.330277] system 00:01: ioport range 0x910-0x911 has been reserved
Jan  4 12:23:20 unleaded kernel: [    1.330351] system 00:01: ioport range 0x920-0x923 has been reserved
Jan  4 12:23:20 unleaded kernel: [    1.330425] system 00:01: ioport range 0x930-0x937 has been reserved
Jan  4 12:23:20 unleaded kernel: [    1.330498] system 00:01: ioport range 0x940-0x947 has been reserved
Jan  4 12:23:20 unleaded kernel: [    1.330572] system 00:01: ioport range 0x950-0x957 has been reserved
Jan  4 12:23:20 unleaded kernel: [    1.330646] system 00:01: ioport range 0xc06-0xc08 has been reserved
Jan  4 12:23:20 unleaded kernel: [    1.330720] system 00:01: ioport range 0xc14-0xc14 has been reserved
Jan  4 12:23:20 unleaded kernel: [    1.330794] system 00:01: ioport range 0xc49-0xc4a has been reserved
Jan  4 12:23:20 unleaded kernel: [    1.330869] system 00:01: ioport range 0xc50-0xc52 has been reserved
Jan  4 12:23:20 unleaded kernel: [    1.330943] system 00:01: ioport range 0xc6c-0xc6f has been reserved
Jan  4 12:23:20 unleaded kernel: [    1.331017] system 00:01: ioport range 0x230-0x233 has been reserved
Jan  4 12:23:20 unleaded kernel: [    1.331092] system 00:01: ioport range 0x260-0x267 has been reserved
Jan  4 12:23:20 unleaded kernel: [    1.331166] system 00:01: ioport range 0x4d0-0x4d1 has been reserved
Jan  4 12:23:20 unleaded kernel: [    1.331239] system 00:01: ioport range 0x700-0x70f has been reserved
Jan  4 12:23:20 unleaded kernel: [    1.331317] system 00:01: ioport range 0x800-0x81f has been reserved
Jan  4 12:23:20 unleaded kernel: [    1.331394] system 00:01: ioport range 0xc80-0xc83 has been reserved
Jan  4 12:23:20 unleaded kernel: [    1.331470] system 00:01: ioport range 0xcd4-0xcd7 has been reserved
Jan  4 12:23:20 unleaded kernel: [    1.331545] system 00:01: ioport range 0xcf9-0xcf9 could not be reserved
Jan  4 12:23:20 unleaded kernel: [    1.331620] system 00:01: ioport range 0x374-0x375 has been reserved
Jan  4 12:23:20 unleaded kernel: [    1.331694] system 00:01: ioport range 0x377-0x377 has been reserved
Jan  4 12:23:20 unleaded kernel: [    1.368151] pci 0000:05:01.0: PCI bridge, secondary bus 0000:06
Jan  4 12:23:20 unleaded kernel: [    1.368229] pci 0000:05:01.0:   IO window: 0x3000-0x3fff
Jan  4 12:23:20 unleaded kernel: [    1.368306] pci 0000:05:01.0:   MEM window: 0xf7f00000-0xf7ffffff
Jan  4 12:23:20 unleaded kernel: [    1.368381] pci 0000:05:01.0:   PREFETCH window: 0x000000c4200000-0x000000c42fffff
Jan  4 12:23:20 unleaded kernel: [    1.368490] bus: 00 index 0 io port: [0, ffff]
Jan  4 12:23:20 unleaded kernel: [    1.368561] bus: 00 index 1 mmio: [0, ffffffffffffffff]
Jan  4 12:23:20 unleaded kernel: [    1.368632] bus: 01 index 0 io port: [0, ffff]
Jan  4 12:23:20 unleaded kernel: [    1.368701] bus: 01 index 1 mmio: [0, ffffffffffffffff]
Jan  4 12:23:20 unleaded kernel: [    1.368771] bus: 05 index 0 io port: [0, ffff]
Jan  4 12:23:20 unleaded kernel: [    1.368840] bus: 05 index 1 mmio: [0, ffffffffffffffff]
Jan  4 12:23:20 unleaded kernel: [    1.368910] bus: 06 index 0 io port: [3000, 3fff]
Jan  4 12:23:20 unleaded kernel: [    1.368980] bus: 06 index 1 mmio: [f7f00000, f7ffffff]
Jan  4 12:23:20 unleaded kernel: [    1.369051] bus: 06 index 2 mmio: [c4200000, c42fffff]
Jan  4 12:23:20 unleaded kernel: [    1.369121] bus: 06 index 3 mmio: [0, 0]
Jan  4 12:23:20 unleaded kernel: [    1.369189] bus: 09 index 0 io port: [0, ffff]
Jan  4 12:23:20 unleaded kernel: [    1.369258] bus: 09 index 1 mmio: [0, ffffffffffffffff]
Jan  4 12:23:20 unleaded kernel: [    1.369328] bus: 0d index 0 io port: [0, ffff]
Jan  4 12:23:20 unleaded kernel: [    1.369398] bus: 0d index 1 mmio: [0, ffffffffffffffff]
Jan  4 12:23:20 unleaded kernel: [    1.369485] NET: Registered protocol family 2
Jan  4 12:23:20 unleaded kernel: [    1.400133] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Jan  4 12:23:20 unleaded kernel: [    1.400771] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Jan  4 12:23:20 unleaded kernel: [    1.401877] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Jan  4 12:23:20 unleaded kernel: [    1.402544] TCP: Hash tables configured (established 131072 bind 65536)
Jan  4 12:23:20 unleaded kernel: [    1.402618] TCP reno registered
Jan  4 12:23:20 unleaded kernel: [    1.420259] NET: Registered protocol family 1
Jan  4 12:23:20 unleaded kernel: [    1.420549] checking if image is initramfs...<7>Switched to high resolution mode on CPU 3
Jan  4 12:23:20 unleaded kernel: [    1.923076]  it is
Jan  4 12:23:20 unleaded kernel: [    2.489428] Freeing initrd memory: 8474k freed
Jan  4 12:23:20 unleaded kernel: [    2.490167] platform rtc_cmos: registered platform RTC device (no PNP device found)
Jan  4 12:23:20 unleaded kernel: [    2.491910] audit: initializing netlink socket (disabled)
Jan  4 12:23:20 unleaded kernel: [    2.492015] type=2000 audit(1231071642.490:1): initialized
Jan  4 12:23:20 unleaded kernel: [    2.499293] highmem bounce pool size: 64 pages
Jan  4 12:23:20 unleaded kernel: [    2.499378] HugeTLB registered 2 MB page size, pre-allocated 0 pages
Jan  4 12:23:20 unleaded kernel: [    2.505332] VFS: Disk quotas dquot_6.5.1
Jan  4 12:23:20 unleaded kernel: [    2.505633] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Jan  4 12:23:20 unleaded kernel: [    2.505937] msgmni has been set to 1724
Jan  4 12:23:20 unleaded kernel: [    2.506282] io scheduler noop registered
Jan  4 12:23:20 unleaded kernel: [    2.506352] io scheduler anticipatory registered
Jan  4 12:23:20 unleaded kernel: [    2.506422] io scheduler deadline registered (default)
Jan  4 12:23:20 unleaded kernel: [    2.506511] io scheduler cfq registered
Jan  4 12:23:20 unleaded kernel: [    2.506633] pci 0000:00:04.0: Firmware left e100 interrupts enabled; disabling
Jan  4 12:23:20 unleaded kernel: [    2.521194] isapnp: Scanning for PnP cards...
Jan  4 12:23:20 unleaded kernel: [    2.834526] isapnp: No Plug & Play device found
Jan  4 12:23:20 unleaded kernel: [    2.921773] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
Jan  4 12:23:20 unleaded kernel: [    2.922069] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Jan  4 12:23:20 unleaded kernel: [    2.922581] serial8250: ttyS2 at I/O 0x3e8 (irq = 4) is a 16550A
Jan  4 12:23:20 unleaded kernel: [    2.923744] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Jan  4 12:23:20 unleaded kernel: [    2.924379] 00:09: ttyS2 at I/O 0x3e8 (irq = 5) is a 16550A
Jan  4 12:23:20 unleaded kernel: [    2.929419] brd: module loaded
Jan  4 12:23:20 unleaded kernel: [    2.929650] input: Macintosh mouse button emulation as /devices/virtual/input/input0
Jan  4 12:23:20 unleaded kernel: [    2.930064] PNP: PS/2 Controller [PNP0303:KBD,PNP0f0e:PS2M] at 0x60,0x64 irq 1,12
Jan  4 12:23:20 unleaded kernel: [    2.931840] serio: i8042 KBD port at 0x60,0x64 irq 1
Jan  4 12:23:20 unleaded kernel: [    2.931921] serio: i8042 AUX port at 0x60,0x64 irq 12
Jan  4 12:23:20 unleaded kernel: [    2.940387] mice: PS/2 mouse device common for all mice
Jan  4 12:23:20 unleaded kernel: [    2.941034] EISA: Probing bus 0 at eisa.0
Jan  4 12:23:20 unleaded kernel: [    2.941110] EISA: Cannot allocate resource for mainboard
Jan  4 12:23:20 unleaded kernel: [    2.941184] Cannot allocate resource for EISA slot 1
Jan  4 12:23:20 unleaded kernel: [    2.941256] Cannot allocate resource for EISA slot 2
Jan  4 12:23:20 unleaded kernel: [    2.941333] Cannot allocate resource for EISA slot 3
Jan  4 12:23:20 unleaded kernel: [    2.941436] EISA: Detected 0 cards.
Jan  4 12:23:20 unleaded kernel: [    2.941506] cpuidle: using governor ladder
Jan  4 12:23:20 unleaded kernel: [    2.941575] cpuidle: using governor menu
Jan  4 12:23:20 unleaded kernel: [    2.942771] TCP cubic registered
Jan  4 12:23:20 unleaded kernel: [    2.942889] Using IPI No-Shortcut mode
Jan  4 12:23:20 unleaded kernel: [    2.943524] registered taskstats version 1
Jan  4 12:23:20 unleaded kernel: [    2.943882]   Magic number: 9:809:328
Jan  4 12:23:20 unleaded kernel: [    2.944113] /build/buildd/linux-2.6.27/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
Jan  4 12:23:20 unleaded kernel: [    2.944205] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Jan  4 12:23:20 unleaded kernel: [    2.944276] EDD information not available.
Jan  4 12:23:20 unleaded kernel: [    2.944849] Freeing unused kernel memory: 436k freed
Jan  4 12:23:20 unleaded kernel: [    2.945124] Write protecting the kernel text: 2632k
Jan  4 12:23:20 unleaded kernel: [    2.945292] Write protecting the kernel read-only data: 956k
Jan  4 12:23:20 unleaded kernel: [    2.977989] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
Jan  4 12:23:20 unleaded kernel: [    3.175909] device-mapper: uevent: version 1.0.3
Jan  4 12:23:20 unleaded kernel: [    3.176526] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
Jan  4 12:23:20 unleaded kernel: [    3.210338] device-mapper: dm-raid45: initialized v0.2427
Jan  4 12:23:20 unleaded kernel: [    3.224079] fuse init (API version 7.9)
Jan  4 12:23:20 unleaded kernel: [    3.268075] processor ACPI0007:04: registered as cooling_device0
Jan  4 12:23:20 unleaded kernel: [    3.268345] processor ACPI0007:05: registered as cooling_device1
Jan  4 12:23:20 unleaded kernel: [    3.268598] processor ACPI0007:06: registered as cooling_device2
Jan  4 12:23:20 unleaded kernel: [    3.268839] processor ACPI0007:07: registered as cooling_device3
Jan  4 12:23:20 unleaded kernel: [    3.273962] thermal LNXTHERM:01: registered as thermal_zone0
Jan  4 12:23:20 unleaded kernel: [    3.275648] ACPI: Thermal Zone [THM0] (8 C)
Jan  4 12:23:20 unleaded kernel: [    3.907641] usbcore: registered new interface driver usbfs
Jan  4 12:23:20 unleaded kernel: [    3.907800] usbcore: registered new interface driver hub
Jan  4 12:23:20 unleaded kernel: [    3.908045] usbcore: registered new device driver usb
Jan  4 12:23:20 unleaded kernel: [    3.928538] ACPI: PCI Interrupt Link [IUSB] enabled at IRQ 11
Jan  4 12:23:20 unleaded kernel: [    3.928645] ohci_hcd 0000:00:0f.2: PCI INT A -> Link[IUSB] -> GSI 11 (level, low) -> IRQ 11
Jan  4 12:23:20 unleaded kernel: [    3.928775] ohci_hcd 0000:00:0f.2: OHCI Host Controller
Jan  4 12:23:20 unleaded kernel: [    3.928980] ohci_hcd 0000:00:0f.2: new USB bus registered, assigned bus number 1
Jan  4 12:23:20 unleaded kernel: [    3.929114] ohci_hcd 0000:00:0f.2: irq 11, io mem 0xf5df0000
Jan  4 12:23:20 unleaded kernel: [    3.932830] e100: Intel(R) PRO/100 Network Driver, 3.5.23-k4-NAPI
Jan  4 12:23:20 unleaded kernel: [    3.932913] e100: Copyright(c) 1999-2006 Intel Corporation
Jan  4 12:23:20 unleaded kernel: [    3.957854] No dock devices found.
Jan  4 12:23:20 unleaded kernel: [    3.995340] usb usb1: configuration #1 chosen from 1 choice
Jan  4 12:23:20 unleaded kernel: [    3.995519] hub 1-0:1.0: USB hub found
Jan  4 12:23:20 unleaded kernel: [    3.995614] hub 1-0:1.0: 4 ports detected
Jan  4 12:23:20 unleaded kernel: [    4.000145] SCSI subsystem initialized
Jan  4 12:23:20 unleaded kernel: [    4.057397] HP CISS Driver (v 3.6.20)
Jan  4 12:23:20 unleaded kernel: [    4.111347] e100 0000:00:04.0: PCI INT A -> GSI 29 (level, low) -> IRQ 29
Jan  4 12:23:20 unleaded kernel: [    4.209219] e100 0000:00:04.0: PME# disabled
Jan  4 12:23:20 unleaded kernel: [    4.210196] e100: eth0: e100_probe: addr 0xf5fe0000, irq 29, MAC addr 00:0e:7f:25:43:80
Jan  4 12:23:20 unleaded kernel: [    4.210869] scsi0 : pata_serverworks
Jan  4 12:23:20 unleaded kernel: [    4.211176] scsi1 : pata_serverworks
Jan  4 12:23:20 unleaded kernel: [    4.211382] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x2000 irq 14
Jan  4 12:23:20 unleaded kernel: [    4.211470] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x2008 irq 15
Jan  4 12:23:20 unleaded kernel: [    4.390503] ata1.00: ATAPI: HL-DT-ST CD-ROM GCR-8482B, 2.09, max UDMA/33
Jan  4 12:23:20 unleaded kernel: [    4.431681] ata1.00: configured for UDMA/33
Jan  4 12:23:20 unleaded kernel: [    4.601186] scsi 0:0:0:0: CD-ROM            HL-DT-ST CD-ROM GCR-8482B 2.09 PQ: 0 ANSI: 5
Jan  4 12:23:20 unleaded kernel: [    4.601974] cciss 0000:06:04.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
Jan  4 12:23:20 unleaded kernel: [    4.700061] cciss0: <0x46> at PCI 0000:06:04.0 IRQ 20 using DAC
Jan  4 12:23:20 unleaded kernel: [    4.701094]       blocks= 71106240 block_size= 512
Jan  4 12:23:20 unleaded kernel: [    4.701266]       heads=255, sectors=32, cylinders=8714
Jan  4 12:23:20 unleaded kernel: [    4.701268] 
Jan  4 12:23:20 unleaded kernel: [    4.701703]       blocks= 71106240 block_size= 512
Jan  4 12:23:20 unleaded kernel: [    4.701870]       heads=255, sectors=32, cylinders=8714
Jan  4 12:23:20 unleaded kernel: [    4.701872] 
Jan  4 12:23:20 unleaded kernel: [    4.702004]  cciss/c0d0: p1 p2
Jan  4 12:23:20 unleaded kernel: [    4.706256]       blocks= 711261810 block_size= 512
Jan  4 12:23:20 unleaded kernel: [    4.706462]       heads=255, sectors=63, cylinders=44274
Jan  4 12:23:20 unleaded kernel: [    4.706466] 
Jan  4 12:23:20 unleaded kernel: [    4.707009]       blocks= 711261810 block_size= 512
Jan  4 12:23:20 unleaded kernel: [    4.707218]       heads=255, sectors=63, cylinders=44274
Jan  4 12:23:20 unleaded kernel: [    4.707222] 
Jan  4 12:23:20 unleaded kernel: [    4.707380]  cciss/c0d1: p1
Jan  4 12:23:20 unleaded kernel: [    4.751360] scsi 0:0:0:0: Attached scsi generic sg0 type 5
Jan  4 12:23:20 unleaded kernel: [    4.779174] Driver 'sr' needs updating - please use bus_type methods
Jan  4 12:23:20 unleaded kernel: [    4.784948] sr0: scsi3-mmc drive: 48x/48x cd/rw xa/form2 cdda tray
Jan  4 12:23:20 unleaded kernel: [    4.785034] Uniform CD-ROM driver Revision: 3.20
Jan  4 12:23:20 unleaded kernel: [    5.124663] PM: Starting manual resume from disk
Jan  4 12:23:20 unleaded kernel: [    5.170959] kjournald starting.  Commit interval 5 seconds
Jan  4 12:23:20 unleaded kernel: [    5.170995] EXT3-fs: mounted filesystem with ordered data mode.
Jan  4 12:23:20 unleaded kernel: [    6.371432] udevd version 124 started
Jan  4 12:23:20 unleaded kernel: [    7.207616] Linux agpgart interface v0.103
Jan  4 12:23:20 unleaded kernel: [    7.254855] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Jan  4 12:23:20 unleaded kernel: [    7.313924] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Jan  4 12:23:20 unleaded kernel: [    7.336122] cpqphp: Compaq Hot Plug PCI Controller Driver version: 0.9.8
Jan  4 12:23:20 unleaded kernel: [    7.336313] compaq_pci_hotplug 0000:01:1e.0: PCI INT A -> GSI 34 (level, low) -> IRQ 34
Jan  4 12:23:20 unleaded kernel: [    7.336419] cpqphp: Hot Plug Subsystem Device ID: a2fe
Jan  4 12:23:20 unleaded kernel: [    7.336496] cpqphp: Initializing the PCI hot plug controller residing on PCI bus 1
Jan  4 12:23:20 unleaded kernel: [    7.336597] PCI: Using BIOS Interrupt Routing Table
Jan  4 12:23:20 unleaded kernel: [    7.336869] PCI: Using BIOS Interrupt Routing Table
Jan  4 12:23:20 unleaded kernel: [    7.345462] *pdpt = 00000000359cb001 *pde = 0000000000000000 
Jan  4 12:23:20 unleaded kernel: [    7.345798] Modules linked in: cpqphp(+) shpchp sworks_agp pci_hotplug agpgart ext3 jbd mbcache sr_mod cdrom sg ata_generic pata_acpi pata_serverworks cciss libata scsi_mod dock e100 ohci_hcd mii usbcore dm_snapshot thermal processor fan fbcon tileblit font bitblit softcursor fuse dm_raid4_5 dm_region_hash dm_mem_cache dm_message dm_mirror dm_log dm_mod
Jan  4 12:23:20 unleaded kernel: [    7.347854] 
Jan  4 12:23:20 unleaded kernel: [    7.347923] Pid: 2689, comm: modprobe Not tainted (2.6.27-9-server #1)
Jan  4 12:23:20 unleaded kernel: [    7.348337] EIP: 0060:[<c026b1a4>] EFLAGS: 00010213 CPU: 2
Jan  4 12:23:20 unleaded kernel: [    7.348421] EIP is at pci_create_slot+0x24/0x110
Jan  4 12:23:20 unleaded kernel: [    7.348503] EAX: c048e168 EBX: 00000001 ECX: f78bfca0 EDX: 00000000
Jan  4 12:23:20 unleaded kernel: [    7.348589] ESI: f59e4f40 EDI: 00000000 EBP: f7e9dd18 ESP: f7e9dcf4
Jan  4 12:23:20 unleaded kernel: [    7.348674]  DS: 007b ES: 007b FS: 00d8 GS: 0033 SS: 0068
Jan  4 12:23:20 unleaded kernel: [    7.360042] ---[ end trace a5a134d308824b28 ]---
Jan  4 12:23:20 unleaded kernel: [    7.382125] input: PC Speaker as /devices/platform/pcspkr/input/input2
Jan  4 12:23:20 unleaded kernel: [    7.471907] scb2_flash: warning - can't reserve rom window, continuing
Jan  4 12:23:20 unleaded kernel: [    7.912924] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
Jan  4 12:23:20 unleaded kernel: [    7.962186] ACPI: Power Button (FF) [PWRF]
Jan  4 12:23:20 unleaded kernel: [    9.049557] parport_pc 00:07: reported by Plug and Play ACPI
Jan  4 12:23:20 unleaded kernel: [    9.049720] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
Jan  4 12:23:20 unleaded kernel: [  186.778393] loop: module loaded
Jan  4 12:23:20 unleaded kernel: [  186.810492] lp0: using parport0 (interrupt-driven).
Jan  4 12:23:20 unleaded kernel: [  187.112716] Adding 3145720k swap on /dev/mapper/unleaded-unleaded--swap.  Priority:-1 extents:1 across:3145720k
Jan  4 12:23:20 unleaded kernel: [  187.381715] EXT3 FS on dm-1, internal journal
Jan  4 12:23:20 unleaded kernel: [  188.150059] kjournald starting.  Commit interval 5 seconds
Jan  4 12:23:20 unleaded kernel: [  188.150222] EXT3 FS on cciss/c0d0p1, internal journal
Jan  4 12:23:20 unleaded kernel: [  188.150235] EXT3-fs: mounted filesystem with ordered data mode.
Jan  4 12:23:20 unleaded kernel: [  188.155541] kjournald starting.  Commit interval 5 seconds
Jan  4 12:23:20 unleaded kernel: [  188.155963] EXT3 FS on dm-2, internal journal
Jan  4 12:23:20 unleaded kernel: [  188.155974] EXT3-fs: mounted filesystem with ordered data mode.
Jan  4 12:23:20 unleaded kernel: [  188.625252] ip_tables: (C) 2000-2006 Netfilter Core Team
Jan  4 12:23:20 unleaded kernel: [  188.742111] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
Jan  4 12:23:20 unleaded kernel: [  189.940247] NET: Registered protocol family 17
Jan  4 12:23:20 unleaded kernel: [  190.396277] NET: Registered protocol family 10
Jan  4 12:23:20 unleaded kernel: [  190.397444] lo: Disabled Privacy Extensions


```

---

