---
title: "Server crashes randomly"
date: 2009-12-27
forum: Server Platforms
---

### Post by the_bard on 2009-12-27
Hi,

For some time my development server suddenly crash with no apparent reason.

Month ago I reinstalled and reconfigured a new copy of Karmic, all went fine, but keeps crashing randomly. I had only installed minimal required configuration for my requirements, all from repositories.

I don´t see anything strange in syslogs, even worst, I don´t see anything about the crash.

The hardware is quite old, but it should work fine.
One of the hard drives is 'new', and both runs badblocks and fsck wihout errors.

The crashes appear to be randomly, they appear at different hours and sometimes multiple times a day. I must reset manually the computer, keyboard doesn´t work, even the leds after pressing any block key.

Now, writting this posts it seems to be crashed one more time, the server was idle, I only was reading and downloading a copy of logs.

There is something in logs that i miss?

Thanks,


Result of `uname -a`:
```

Linux ubard 2.6.31-14-server #48-Ubuntu SMP Fri Oct 16 15:07:34 UTC 2009 x86_64 GNU/Linux

```

Contents of /var/log/messages :
```

Dec 26 06:34:55 ubard rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="847" x-info="http://www.rsyslog.com"] rsyslogd was HUPed, type 'lightweight'.
Dec 27 16:48:00 ubard kernel: imklog 4.2.0, log source = /var/run/rsyslog/kmsg started.
Dec 27 16:48:00 ubard rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="840" x-info="http://www.rsyslog.com"] (re)start
Dec 27 16:48:00 ubard rsyslogd: rsyslogd's groupid changed to 103
Dec 27 16:48:00 ubard rsyslogd: rsyslogd's userid changed to 101
Dec 27 16:48:00 ubard kernel: [    0.000000] Initializing cgroup subsys cpuset
Dec 27 16:48:00 ubard kernel: [    0.000000] Initializing cgroup subsys cpu
Dec 27 16:48:00 ubard kernel: [    0.000000] Linux version 2.6.31-14-server (buildd@crested) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #48-Ubuntu SMP Fri Oct 16 15:07:34 UTC 2009 (Ubuntu 2.6.31-14.48-server)
Dec 27 16:48:00 ubard kernel: [    0.000000] Command line: BOOT_IMAGE=/vmlinuz-2.6.31-14-server root=/dev/mapper/ubard-root ro quiet splash
Dec 27 16:48:00 ubard kernel: [    0.000000] KERNEL supported cpus:
Dec 27 16:48:00 ubard kernel: [    0.000000]   Intel GenuineIntel
Dec 27 16:48:00 ubard kernel: [    0.000000]   AMD AuthenticAMD
Dec 27 16:48:00 ubard kernel: [    0.000000]   Centaur CentaurHauls
Dec 27 16:48:00 ubard kernel: [    0.000000] BIOS-provided physical RAM map:
Dec 27 16:48:00 ubard kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Dec 27 16:48:00 ubard kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Dec 27 16:48:00 ubard kernel: [    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
Dec 27 16:48:00 ubard kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000007df30000 (usable)
Dec 27 16:48:00 ubard kernel: [    0.000000]  BIOS-e820: 000000007df30000 - 000000007df40000 (ACPI data)
Dec 27 16:48:00 ubard kernel: [    0.000000]  BIOS-e820: 000000007df40000 - 000000007dff0000 (ACPI NVS)
Dec 27 16:48:00 ubard kernel: [    0.000000]  BIOS-e820: 000000007dff0000 - 000000007e000000 (reserved)
Dec 27 16:48:00 ubard kernel: [    0.000000]  BIOS-e820: 00000000ff780000 - 0000000100000000 (reserved)
Dec 27 16:48:00 ubard kernel: [    0.000000] DMI 2.3 present.
Dec 27 16:48:00 ubard kernel: [    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
Dec 27 16:48:00 ubard kernel: [    0.000000] last_pfn = 0x7df30 max_arch_pfn = 0x400000000
Dec 27 16:48:00 ubard kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Dec 27 16:48:00 ubard kernel: [    0.000000] Scanning 0 areas for low memory corruption
Dec 27 16:48:00 ubard kernel: [    0.000000] modified physical RAM map:
Dec 27 16:48:00 ubard kernel: [    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
Dec 27 16:48:00 ubard kernel: [    0.000000]  modified: 0000000000010000 - 000000000009fc00 (usable)
Dec 27 16:48:00 ubard kernel: [    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
Dec 27 16:48:00 ubard kernel: [    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
Dec 27 16:48:00 ubard kernel: [    0.000000]  modified: 0000000000100000 - 000000007df30000 (usable)
Dec 27 16:48:00 ubard kernel: [    0.000000]  modified: 000000007df30000 - 000000007df40000 (ACPI data)
Dec 27 16:48:00 ubard kernel: [    0.000000]  modified: 000000007df40000 - 000000007dff0000 (ACPI NVS)
Dec 27 16:48:00 ubard kernel: [    0.000000]  modified: 000000007dff0000 - 000000007e000000 (reserved)
Dec 27 16:48:00 ubard kernel: [    0.000000]  modified: 00000000ff780000 - 0000000100000000 (reserved)
Dec 27 16:48:00 ubard kernel: [    0.000000] init_memory_mapping: 0000000000000000-000000007df30000
Dec 27 16:48:00 ubard kernel: [    0.000000] Using x86 segment limits to approximate NX protection
Dec 27 16:48:00 ubard kernel: [    0.000000] RAMDISK: 378db000 - 37fef991
Dec 27 16:48:00 ubard kernel: [    0.000000] ACPI: RSDP 00000000000fb140 00021 (v02 ACPIAM)
Dec 27 16:48:00 ubard kernel: [    0.000000] ACPI: XSDT 000000007df30100 0003C (v01 A M I  OEMXSDT  03000631 MSFT 00000097)
Dec 27 16:48:00 ubard kernel: [    0.000000] ACPI: FACP 000000007df30290 000F4 (v03 A M I  OEMFACP  03000631 MSFT 00000097)
Dec 27 16:48:00 ubard kernel: [    0.000000] ACPI: DSDT 000000007df303f0 03D5E (v01  A0264 A0264601 00000601 INTL 02002026)
Dec 27 16:48:00 ubard kernel: [    0.000000] ACPI: FACS 000000007df40000 00040
Dec 27 16:48:00 ubard kernel: [    0.000000] ACPI: APIC 000000007df30390 00054 (v01 A M I  OEMAPIC  03000631 MSFT 00000097)
Dec 27 16:48:00 ubard kernel: [    0.000000] ACPI: OEMB 000000007df40040 00040 (v01 A M I  AMI_OEM  03000631 MSFT 00000097)
Dec 27 16:48:00 ubard kernel: [    0.000000] Scanning NUMA topology in Northbridge 24
Dec 27 16:48:00 ubard kernel: [    0.000000] No NUMA configuration found
Dec 27 16:48:00 ubard kernel: [    0.000000] Faking a node at 0000000000000000-000000007df30000
Dec 27 16:48:00 ubard kernel: [    0.000000] Bootmem setup node 0 0000000000000000-000000007df30000
Dec 27 16:48:00 ubard kernel: [    0.000000]   NODE_DATA [0000000000012000 - 0000000000016fff]
Dec 27 16:48:00 ubard kernel: [    0.000000]   bootmap [0000000000017000 -  0000000000026be7] pages 10
Dec 27 16:48:00 ubard kernel: [    0.000000] (7 early reservations) ==> bootmem [0000000000 - 007df30000]
Dec 27 16:48:00 ubard kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
Dec 27 16:48:00 ubard kernel: [    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
Dec 27 16:48:00 ubard kernel: [    0.000000]   #2 [0001000000 - 00019e0ccc]    TEXT DATA BSS ==> [0001000000 - 00019e0ccc]
Dec 27 16:48:00 ubard kernel: [    0.000000]   #3 [00378db000 - 0037fef991]          RAMDISK ==> [00378db000 - 0037fef991]
Dec 27 16:48:00 ubard kernel: [    0.000000]   #4 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
Dec 27 16:48:00 ubard kernel: [    0.000000]   #5 [00019e1000 - 00019e11c8]              BRK ==> [00019e1000 - 00019e11c8]
Dec 27 16:48:00 ubard kernel: [    0.000000]   #6 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
Dec 27 16:48:00 ubard kernel: [    0.000000] found SMP MP-table at [ffff8800000ff780] ff780
Dec 27 16:48:00 ubard kernel: [    0.000000] Zone PFN ranges:
Dec 27 16:48:00 ubard kernel: [    0.000000]   DMA      0x00000010 -> 0x00001000
Dec 27 16:48:00 ubard kernel: [    0.000000]   DMA32    0x00001000 -> 0x00100000
Dec 27 16:48:00 ubard kernel: [    0.000000]   Normal   0x00100000 -> 0x00100000
Dec 27 16:48:00 ubard kernel: [    0.000000] Movable zone start PFN for each node
Dec 27 16:48:00 ubard kernel: [    0.000000] early_node_map[2] active PFN ranges
Dec 27 16:48:00 ubard kernel: [    0.000000]     0: 0x00000010 -> 0x0000009f
Dec 27 16:48:00 ubard kernel: [    0.000000]     0: 0x00000100 -> 0x0007df30
Dec 27 16:48:00 ubard kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x808
Dec 27 16:48:00 ubard kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Dec 27 16:48:00 ubard kernel: [    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
Dec 27 16:48:00 ubard kernel: [    0.000000] IOAPIC[0]: apic_id 1, version 20, address 0xfec00000, GSI 0-23
Dec 27 16:48:00 ubard kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Dec 27 16:48:00 ubard kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
Dec 27 16:48:00 ubard kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Dec 27 16:48:00 ubard kernel: [    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
Dec 27 16:48:00 ubard kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Dec 27 16:48:00 ubard kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Dec 27 16:48:00 ubard kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Dec 27 16:48:00 ubard kernel: [    0.000000] Allocating PCI resources starting at 7e000000 (gap: 7e000000:81780000)
Dec 27 16:48:00 ubard kernel: [    0.000000] NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:1 nr_node_ids:1
Dec 27 16:48:00 ubard kernel: [    0.000000] PERCPU: Embedded 30 pages at ffff8800019f2000, static data 90720 bytes
Dec 27 16:48:00 ubard kernel: [    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 508620
Dec 27 16:48:00 ubard kernel: [    0.000000] Policy zone: DMA32
Dec 27 16:48:00 ubard kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/vmlinuz-2.6.31-14-server root=/dev/mapper/ubard-root ro quiet splash
Dec 27 16:48:00 ubard kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
Dec 27 16:48:00 ubard kernel: [    0.000000] Initializing CPU#0
Dec 27 16:48:00 ubard kernel: [    0.000000] Checking aperture...
Dec 27 16:48:00 ubard kernel: [    0.000000] AGP bridge at 00:00:00
Dec 27 16:48:00 ubard kernel: [    0.000000] Aperture from AGP @ f8000000 old size 32 MB
Dec 27 16:48:00 ubard kernel: [    0.000000] Aperture from AGP @ f8000000 size 32 MB (APSIZE f38)
Dec 27 16:48:00 ubard kernel: [    0.000000] Node 0: aperture @ f8000000 size 32 MB
Dec 27 16:48:00 ubard kernel: [    0.000000] Aperture too small (32 MB) than (64 MB)
Dec 27 16:48:00 ubard kernel: [    0.000000] Memory: 2016780k/2063552k available (5303k kernel code, 452k absent, 46320k reserved, 3013k data, 660k init)
Dec 27 16:48:00 ubard kernel: [    0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
Dec 27 16:48:00 ubard kernel: [    0.000000] NR_IRQS:4352 nr_irqs:256
Dec 27 16:48:00 ubard kernel: [    0.000000] Fast TSC calibration using PIT
Dec 27 16:48:00 ubard kernel: [    0.000000] Detected 1795.303 MHz processor.
Dec 27 16:48:00 ubard kernel: [    0.000884] Console: colour VGA+ 80x25
Dec 27 16:48:00 ubard kernel: [    0.000888] console [tty0] enabled
Dec 27 16:48:00 ubard kernel: [    0.010000] allocated 20971520 bytes of page_cgroup
Dec 27 16:48:00 ubard kernel: [    0.010000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Dec 27 16:48:00 ubard kernel: [    0.010000] Calibrating delay loop (skipped), value calculated using timer frequency.. 3590.60 BogoMIPS (lpj=17953030)
Dec 27 16:48:00 ubard kernel: [    0.010000] Security Framework initialized
Dec 27 16:48:00 ubard kernel: [    0.010000] AppArmor: AppArmor initialized
Dec 27 16:48:00 ubard kernel: [    0.010000] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
Dec 27 16:48:00 ubard kernel: [    0.010000] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
Dec 27 16:48:00 ubard kernel: [    0.010000] Mount-cache hash table entries: 256
Dec 27 16:48:00 ubard kernel: [    0.010000] Initializing cgroup subsys ns
Dec 27 16:48:00 ubard kernel: [    0.010000] Initializing cgroup subsys cpuacct
Dec 27 16:48:00 ubard kernel: [    0.010000] Initializing cgroup subsys memory
Dec 27 16:48:00 ubard kernel: [    0.010000] Initializing cgroup subsys freezer
Dec 27 16:48:00 ubard kernel: [    0.010000] Initializing cgroup subsys net_cls
Dec 27 16:48:00 ubard kernel: [    0.010000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Dec 27 16:48:00 ubard kernel: [    0.010000] CPU: L2 Cache: 128K (64 bytes/line)
Dec 27 16:48:00 ubard kernel: [    0.010000] CPU 0/0x0 -> Node 0
Dec 27 16:48:00 ubard kernel: [    0.010000] mce: CPU supports 5 MCE banks
Dec 27 16:48:00 ubard kernel: [    0.010000] Performance Counters: AMD PMU driver.
Dec 27 16:48:00 ubard kernel: [    0.010000] ... version:                 0
Dec 27 16:48:00 ubard kernel: [    0.010000] ... bit width:               48
Dec 27 16:48:00 ubard kernel: [    0.010000] ... generic counters:        4
Dec 27 16:48:00 ubard kernel: [    0.010000] ... value mask:              0000ffffffffffff
Dec 27 16:48:00 ubard kernel: [    0.010000] ... max period:              00007fffffffffff
Dec 27 16:48:00 ubard kernel: [    0.010000] ... fixed-purpose counters:  0
Dec 27 16:48:00 ubard kernel: [    0.010000] ... counter mask:            000000000000000f
Dec 27 16:48:00 ubard kernel: [    0.010000] SMP alternatives: switching to UP code
Dec 27 16:48:00 ubard kernel: [    0.012715] Freeing SMP alternatives: 39k freed
Dec 27 16:48:00 ubard kernel: [    0.012747] ACPI: Core revision 20090521
Dec 27 16:48:00 ubard kernel: [    0.018402] Setting APIC routing to flat
Dec 27 16:48:00 ubard kernel: [    0.018651] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Dec 27 16:48:00 ubard kernel: [    0.118691] CPU0: AMD Sempron(tm) Processor 3000+ stepping 02
Dec 27 16:48:00 ubard kernel: [    0.120000] Brought up 1 CPUs
Dec 27 16:48:00 ubard kernel: [    0.120000] Total of 1 processors activated (3590.60 BogoMIPS).
Dec 27 16:48:00 ubard kernel: [    0.120000] Booting paravirtualized kernel on bare hardware
Dec 27 16:48:00 ubard kernel: [    0.120000] regulator: core version 0.5
Dec 27 16:48:00 ubard kernel: [    0.120000] Time: 15:47:40  Date: 12/27/09
Dec 27 16:48:00 ubard kernel: [    0.120000] NET: Registered protocol family 16
Dec 27 16:48:00 ubard kernel: [    0.120000] TOM: 0000000080000000 aka 2048M
Dec 27 16:48:00 ubard kernel: [    0.120000] ACPI: bus type pci registered
Dec 27 16:48:00 ubard kernel: [    0.120000] PCI: Using configuration type 1 for base access
Dec 27 16:48:00 ubard kernel: [    0.120000] bio: create slab <bio-0> at 0
Dec 27 16:48:00 ubard kernel: [    0.120000] ACPI: Interpreter enabled
Dec 27 16:48:00 ubard kernel: [    0.120000] ACPI: (supports S0 S1 S3 S4 S5)
Dec 27 16:48:00 ubard kernel: [    0.120000] ACPI: Using IOAPIC for interrupt routing
Dec 27 16:48:00 ubard kernel: [    0.125143] ACPI: No dock devices found.
Dec 27 16:48:00 ubard kernel: [    0.125258] ACPI: PCI Root Bridge [PCI0] (0000:00)
Dec 27 16:48:00 ubard kernel: [    0.125456] pci 0000:00:02.5: PME# supported from D3cold
Dec 27 16:48:00 ubard kernel: [    0.125460] pci 0000:00:02.5: PME# disabled
Dec 27 16:48:00 ubard kernel: [    0.125617] pci 0000:00:03.3: PME# supported from D0 D3hot D3cold
Dec 27 16:48:00 ubard kernel: [    0.125621] pci 0000:00:03.3: PME# disabled
Dec 27 16:48:00 ubard kernel: [    0.125680] pci 0000:00:04.0: PME# supported from D0 D1 D2 D3hot D3cold
Dec 27 16:48:00 ubard kernel: [    0.125684] pci 0000:00:04.0: PME# disabled
Dec 27 16:48:00 ubard kernel: [    0.125749] pci 0000:00:05.0: PME# supported from D3cold
Dec 27 16:48:00 ubard kernel: [    0.125752] pci 0000:00:05.0: PME# disabled
Dec 27 16:48:00 ubard kernel: [    0.125788] pci 0000:00:06.0: PME# supported from D0 D3hot D3cold
Dec 27 16:48:00 ubard kernel: [    0.125792] pci 0000:00:06.0: PME# disabled
Dec 27 16:48:00 ubard kernel: [    0.125827] pci 0000:00:07.0: PME# supported from D0 D3hot D3cold
Dec 27 16:48:00 ubard kernel: [    0.125831] pci 0000:00:07.0: PME# disabled
Dec 27 16:48:00 ubard kernel: [    0.125892] pci 0000:00:09.0: PME# supported from D0 D1 D2 D3cold
Dec 27 16:48:00 ubard kernel: [    0.125896] pci 0000:00:09.0: PME# disabled
Dec 27 16:48:00 ubard kernel: [    0.134421] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 10 *11 12 14 15)
Dec 27 16:48:00 ubard kernel: [    0.134535] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 *10 11 12 14 15)
Dec 27 16:48:00 ubard kernel: [    0.134646] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
Dec 27 16:48:00 ubard kernel: [    0.134752] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 7 10 11 12 14 15)
Dec 27 16:48:00 ubard kernel: [    0.134859] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 *11 12 14 15)
Dec 27 16:48:00 ubard kernel: [    0.134966] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 *4 5 7 10 11 12 14 15)
Dec 27 16:48:00 ubard kernel: [    0.135072] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 *7 10 11 12 14 15)
Dec 27 16:48:00 ubard kernel: [    0.135179] ACPI: PCI Interrupt Link [LNKH] (IRQs *3 4 5 7 10 11 12 14 15)
Dec 27 16:48:00 ubard kernel: [    0.135384] SCSI subsystem initialized
Dec 27 16:48:00 ubard kernel: [    0.135547] usbcore: registered new interface driver usbfs
Dec 27 16:48:00 ubard kernel: [    0.135566] usbcore: registered new interface driver hub
Dec 27 16:48:00 ubard kernel: [    0.135592] usbcore: registered new device driver usb
Dec 27 16:48:00 ubard kernel: [    0.135746] ACPI: WMI: Mapper loaded
Dec 27 16:48:00 ubard kernel: [    0.135748] PCI: Using ACPI for IRQ routing
Dec 27 16:48:00 ubard kernel: [    0.135766] pci 0000:00:00.0: BAR 0: can't allocate resource
Dec 27 16:48:00 ubard kernel: [    0.135916] Bluetooth: Core ver 2.15
Dec 27 16:48:00 ubard kernel: [    0.135966] NET: Registered protocol family 31
Dec 27 16:48:00 ubard kernel: [    0.135968] Bluetooth: HCI device and connection manager initialized
Dec 27 16:48:00 ubard kernel: [    0.135972] Bluetooth: HCI socket layer initialized
Dec 27 16:48:00 ubard kernel: [    0.135974] NetLabel: Initializing
Dec 27 16:48:00 ubard kernel: [    0.135976] NetLabel:  domain hash size = 128
Dec 27 16:48:00 ubard kernel: [    0.135978] NetLabel:  protocols = UNLABELED CIPSOv4
Dec 27 16:48:00 ubard kernel: [    0.135992] NetLabel:  unlabeled traffic allowed by default
Dec 27 16:48:00 ubard kernel: [    0.136080] agpgart-amd64 0000:00:00.0: AGP bridge [1039/0760]
Dec 27 16:48:00 ubard kernel: [    0.137149] agpgart-amd64 0000:00:00.0: AGP aperture is 32M @ 0xf8000000
Dec 27 16:48:00 ubard kernel: [    0.138902] pnp: PnP ACPI init
Dec 27 16:48:00 ubard kernel: [    0.138925] ACPI: bus type pnp registered
Dec 27 16:48:00 ubard kernel: [    0.141211] pnp: PnP ACPI: found 7 devices
Dec 27 16:48:00 ubard kernel: [    0.141215] ACPI: ACPI bus type pnp unregistered
Dec 27 16:48:00 ubard kernel: [    0.141230] system 00:05: ioport range 0x290-0x297 has been reserved
Dec 27 16:48:00 ubard kernel: [    0.141236] system 00:06: ioport range 0x480-0x48f has been reserved
Dec 27 16:48:00 ubard kernel: [    0.141240] system 00:06: ioport range 0x4d0-0x4d1 has been reserved
Dec 27 16:48:00 ubard kernel: [    0.141243] system 00:06: ioport range 0x800-0x8cf has been reserved
Dec 27 16:48:00 ubard kernel: [    0.141246] system 00:06: ioport range 0x8d0-0x8ff has been reserved
Dec 27 16:48:00 ubard kernel: [    0.141251] system 00:06: iomem range 0xfff80000-0xffffffff has been reserved
Dec 27 16:48:00 ubard kernel: [    0.141254] system 00:06: iomem range 0xffee0000-0xffefffff has been reserved
Dec 27 16:48:00 ubard kernel: [    0.141258] system 00:06: iomem range 0xfee00400-0xfee00fff has been reserved
Dec 27 16:48:00 ubard kernel: [    0.145941] AppArmor: AppArmor Filesystem Enabled
Dec 27 16:48:00 ubard kernel: [    0.145978] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
Dec 27 16:48:00 ubard kernel: [    0.145981] pci 0000:00:01.0:   IO window: 0xc000-0xcfff
Dec 27 16:48:00 ubard kernel: [    0.145986] pci 0000:00:01.0:   MEM window: 0xfbf00000-0xfbffffff
Dec 27 16:48:00 ubard kernel: [    0.145990] pci 0000:00:01.0:   PREFETCH window: 0xf0000000-0xf7ffffff
Dec 27 16:48:00 ubard kernel: [    0.145995] pci 0000:00:06.0: PCI bridge, secondary bus 0000:02
Dec 27 16:48:00 ubard kernel: [    0.145998] pci 0000:00:06.0:   IO window: 0xd000-0xdfff
Dec 27 16:48:00 ubard kernel: [    0.146002] pci 0000:00:06.0:   MEM window: disabled
Dec 27 16:48:00 ubard kernel: [    0.146006] pci 0000:00:06.0:   PREFETCH window: disabled
Dec 27 16:48:00 ubard kernel: [    0.146010] pci 0000:00:07.0: PCI bridge, secondary bus 0000:03
Dec 27 16:48:00 ubard kernel: [    0.146013] pci 0000:00:07.0:   IO window: 0xe000-0xefff
Dec 27 16:48:00 ubard kernel: [    0.146017] pci 0000:00:07.0:   MEM window: disabled
Dec 27 16:48:00 ubard kernel: [    0.146020] pci 0000:00:07.0:   PREFETCH window: disabled
Dec 27 16:48:00 ubard kernel: [    0.146109] NET: Registered protocol family 2
Dec 27 16:48:00 ubard kernel: [    0.146255] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
Dec 27 16:48:00 ubard kernel: [    0.147329] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
Dec 27 16:48:00 ubard kernel: [    0.150587] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
Dec 27 16:48:00 ubard kernel: [    0.151371] TCP: Hash tables configured (established 262144 bind 65536)
Dec 27 16:48:00 ubard kernel: [    0.151375] TCP reno registered
Dec 27 16:48:00 ubard kernel: [    0.151496] NET: Registered protocol family 1
Dec 27 16:48:00 ubard kernel: [    0.151565] Trying to unpack rootfs image as initramfs...
Dec 27 16:48:00 ubard kernel: [    0.354510] Freeing initrd memory: 7250k freed
Dec 27 16:48:00 ubard kernel: [    0.360490] Scanning for low memory corruption every 60 seconds
Dec 27 16:48:00 ubard kernel: [    0.360637] audit: initializing netlink socket (disabled)
Dec 27 16:48:00 ubard kernel: [    0.360653] type=2000 audit(1261928859.360:1): initialized
Dec 27 16:48:00 ubard kernel: [    0.371087] HugeTLB registered 2 MB page size, pre-allocated 0 pages
Dec 27 16:48:00 ubard kernel: [    0.372649] VFS: Disk quotas dquot_6.5.2
Dec 27 16:48:00 ubard kernel: [    0.372728] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
Dec 27 16:48:00 ubard kernel: [    0.373460] fuse init (API version 7.12)
Dec 27 16:48:00 ubard kernel: [    0.373570] msgmni has been set to 3953
Dec 27 16:48:00 ubard kernel: [    0.373839] alg: No test for stdrng (krng)
Dec 27 16:48:00 ubard kernel: [    0.373855] io scheduler noop registered
Dec 27 16:48:00 ubard kernel: [    0.373857] io scheduler anticipatory registered
Dec 27 16:48:00 ubard kernel: [    0.373860] io scheduler deadline registered (default)
Dec 27 16:48:00 ubard kernel: [    0.373934] io scheduler cfq registered
Dec 27 16:48:00 ubard kernel: [    0.450294] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Dec 27 16:48:00 ubard kernel: [    0.450318] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Dec 27 16:48:00 ubard kernel: [    0.450443] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
Dec 27 16:48:00 ubard kernel: [    0.450447] ACPI: Power Button [PWRF]
Dec 27 16:48:00 ubard kernel: [    0.450500] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
Dec 27 16:48:00 ubard kernel: [    0.450503] ACPI: Power Button [PWRB]
Dec 27 16:48:00 ubard kernel: [    0.450886] processor LNXCPU:00: registered as cooling_device0
Dec 27 16:48:00 ubard kernel: [    0.455032] Linux agpgart interface v0.103
Dec 27 16:48:00 ubard kernel: [    0.455047] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
Dec 27 16:48:00 ubard kernel: [    0.456242] brd: module loaded
Dec 27 16:48:00 ubard kernel: [    0.456726] loop: module loaded
Dec 27 16:48:00 ubard kernel: [    0.456829] input: Macintosh mouse button emulation as /devices/virtual/input/input2
Dec 27 16:48:00 ubard kernel: [    0.457130] sata_sis 0000:00:05.0: version 1.0
Dec 27 16:48:00 ubard kernel: [    0.457156] sata_sis 0000:00:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Dec 27 16:48:00 ubard kernel: [    0.457161] sata_sis 0000:00:05.0: Detected SiS 182/965L chipset
Dec 27 16:48:00 ubard kernel: [    0.457265] scsi0 : sata_sis
Dec 27 16:48:00 ubard kernel: [    0.457392] scsi1 : sata_sis
Dec 27 16:48:00 ubard kernel: [    0.457432] ata1: SATA max UDMA/133 cmd 0xb400 ctl 0xb000 bmdma 0xa000 irq 17
Dec 27 16:48:00 ubard kernel: [    0.457437] ata2: SATA max UDMA/133 cmd 0xa800 ctl 0xa400 bmdma 0xa008 irq 17
Dec 27 16:48:00 ubard kernel: [    0.458063] scsi2 : pata_sis
Dec 27 16:48:00 ubard kernel: [    0.458148] scsi3 : pata_sis
Dec 27 16:48:00 ubard kernel: [    0.458866] ata3: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
Dec 27 16:48:00 ubard kernel: [    0.458869] ata4: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
Dec 27 16:48:00 ubard kernel: [    0.459245] Fixed MDIO Bus: probed
Dec 27 16:48:00 ubard kernel: [    0.459282] PPP generic driver version 2.4.2
Dec 27 16:48:00 ubard kernel: [    0.459398] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Dec 27 16:48:00 ubard kernel: [    0.459511] ehci_hcd 0000:00:03.3: PCI INT D -> GSI 23 (level, low) -> IRQ 23
Dec 27 16:48:00 ubard kernel: [    0.459531] ehci_hcd 0000:00:03.3: EHCI Host Controller
Dec 27 16:48:00 ubard kernel: [    0.459614] ehci_hcd 0000:00:03.3: new USB bus registered, assigned bus number 1
Dec 27 16:48:00 ubard kernel: [    0.459677] ehci_hcd 0000:00:03.3: irq 23, io mem 0xfbeff000
Dec 27 16:48:00 ubard kernel: [    0.470050] ehci_hcd 0000:00:03.3: USB 2.0 started, EHCI 1.00
Dec 27 16:48:00 ubard kernel: [    0.470160] usb usb1: configuration #1 chosen from 1 choice
Dec 27 16:48:00 ubard kernel: [    0.470193] hub 1-0:1.0: USB hub found
Dec 27 16:48:00 ubard kernel: [    0.470203] hub 1-0:1.0: 8 ports detected
Dec 27 16:48:00 ubard kernel: [    0.470308] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Dec 27 16:48:00 ubard kernel: [    0.470384] ohci_hcd 0000:00:03.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
Dec 27 16:48:00 ubard kernel: [    0.470406] ohci_hcd 0000:00:03.0: OHCI Host Controller
Dec 27 16:48:00 ubard kernel: [    0.470465] ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus number 2
Dec 27 16:48:00 ubard kernel: [    0.470493] ohci_hcd 0000:00:03.0: irq 20, io mem 0xfbefc000
Dec 27 16:48:00 ubard kernel: [    0.532135] usb usb2: configuration #1 chosen from 1 choice
Dec 27 16:48:00 ubard kernel: [    0.532166] hub 2-0:1.0: USB hub found
Dec 27 16:48:00 ubard kernel: [    0.532178] hub 2-0:1.0: 3 ports detected
Dec 27 16:48:00 ubard kernel: [    0.532323] ohci_hcd 0000:00:03.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
Dec 27 16:48:00 ubard kernel: [    0.532342] ohci_hcd 0000:00:03.1: OHCI Host Controller
Dec 27 16:48:00 ubard kernel: [    0.532398] ohci_hcd 0000:00:03.1: new USB bus registered, assigned bus number 3
Dec 27 16:48:00 ubard kernel: [    0.532426] ohci_hcd 0000:00:03.1: irq 21, io mem 0xfbefd000
Dec 27 16:48:00 ubard kernel: [    0.592138] usb usb3: configuration #1 chosen from 1 choice
Dec 27 16:48:00 ubard kernel: [    0.592168] hub 3-0:1.0: USB hub found
Dec 27 16:48:00 ubard kernel: [    0.592179] hub 3-0:1.0: 3 ports detected
Dec 27 16:48:00 ubard kernel: [    0.592319] ohci_hcd 0000:00:03.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
Dec 27 16:48:00 ubard kernel: [    0.592338] ohci_hcd 0000:00:03.2: OHCI Host Controller
Dec 27 16:48:00 ubard kernel: [    0.592398] ohci_hcd 0000:00:03.2: new USB bus registered, assigned bus number 4
Dec 27 16:48:00 ubard kernel: [    0.592426] ohci_hcd 0000:00:03.2: irq 22, io mem 0xfbefe000
Dec 27 16:48:00 ubard kernel: [    0.630449] ata3.00: ATA-5: ST340016A, 3.05, max UDMA/100
Dec 27 16:48:00 ubard kernel: [    0.630452] ata3.00: 78165360 sectors, multi 16: LBA 
Dec 27 16:48:00 ubard kernel: [    0.652159] usb usb4: configuration #1 chosen from 1 choice
Dec 27 16:48:00 ubard kernel: [    0.652194] hub 4-0:1.0: USB hub found
Dec 27 16:48:00 ubard kernel: [    0.652205] hub 4-0:1.0: 2 ports detected
Dec 27 16:48:00 ubard kernel: [    0.652291] uhci_hcd: USB Universal Host Controller Interface driver
Dec 27 16:48:00 ubard kernel: [    0.652421] PNP: No PS/2 controller found. Probing ports directly.
Dec 27 16:48:00 ubard kernel: [    0.652670] serio: i8042 KBD port at 0x60,0x64 irq 1
Dec 27 16:48:00 ubard kernel: [    0.652679] serio: i8042 AUX port at 0x60,0x64 irq 12
Dec 27 16:48:00 ubard kernel: [    0.652748] mice: PS/2 mouse device common for all mice
Dec 27 16:48:00 ubard kernel: [    0.652837] rtc_cmos 00:02: RTC can wake from S4
Dec 27 16:48:00 ubard kernel: [    0.652878] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
Dec 27 16:48:00 ubard kernel: [    0.652899] rtc0: alarms up to one month, 114 bytes nvram
Dec 27 16:48:00 ubard kernel: [    0.653023] device-mapper: uevent: version 1.0.3
Dec 27 16:48:00 ubard kernel: [    0.653426] ata3.00: configured for UDMA/100
Dec 27 16:48:00 ubard kernel: [    0.653541] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
Dec 27 16:48:00 ubard kernel: [    0.653610] device-mapper: multipath: version 1.1.0 loaded
Dec 27 16:48:00 ubard kernel: [    0.653613] device-mapper: multipath round-robin: version 1.0.0 loaded
Dec 27 16:48:00 ubard kernel: [    0.653762] cpuidle: using governor ladder
Dec 27 16:48:00 ubard kernel: [    0.653765] cpuidle: using governor menu
Dec 27 16:48:00 ubard kernel: [    0.654291] TCP cubic registered
Dec 27 16:48:00 ubard kernel: [    0.654445] NET: Registered protocol family 10
Dec 27 16:48:00 ubard kernel: [    0.654934] lo: Disabled Privacy Extensions
Dec 27 16:48:00 ubard kernel: [    0.655254] NET: Registered protocol family 17
Dec 27 16:48:00 ubard kernel: [    0.655281] Bluetooth: L2CAP ver 2.13
Dec 27 16:48:00 ubard kernel: [    0.655283] Bluetooth: L2CAP socket layer initialized
Dec 27 16:48:00 ubard kernel: [    0.655286] Bluetooth: SCO (Voice Link) ver 0.6
Dec 27 16:48:00 ubard kernel: [    0.655288] Bluetooth: SCO socket layer initialized
Dec 27 16:48:00 ubard kernel: [    0.655349] Bluetooth: RFCOMM TTY layer initialized
Dec 27 16:48:00 ubard kernel: [    0.655352] Bluetooth: RFCOMM socket layer initialized
Dec 27 16:48:00 ubard kernel: [    0.655354] Bluetooth: RFCOMM ver 1.11
Dec 27 16:48:00 ubard kernel: [    0.655371] powernow-k8: Found 1 AMD Sempron(tm) Processor 3000+ processors (1 cpu cores) (version 2.20.00)
Dec 27 16:48:00 ubard kernel: [    0.655411] powernow-k8:    0 : fid 0xa (1800 MHz), vid 0x6
Dec 27 16:48:00 ubard kernel: [    0.655414] powernow-k8:    1 : fid 0x2 (1000 MHz), vid 0x12
Dec 27 16:48:00 ubard kernel: [    0.655675] registered taskstats version 1
Dec 27 16:48:00 ubard kernel: [    0.655800]   Magic number: 5:892:791
Dec 27 16:48:00 ubard kernel: [    0.655865] rtc_cmos 00:02: setting system clock to 2009-12-27 15:47:40 UTC (1261928860)
Dec 27 16:48:00 ubard kernel: [    0.655869] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Dec 27 16:48:00 ubard kernel: [    0.655871] EDD information not available.
Dec 27 16:48:00 ubard kernel: [    0.790068] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Dec 27 16:48:00 ubard kernel: [    0.811210] ata1.00: ATA-7: Maxtor 6V300F0, VA111630, max UDMA/133
Dec 27 16:48:00 ubard kernel: [    0.811214] ata1.00: 586114704 sectors, multi 16: LBA48 NCQ (depth 0/32)
Dec 27 16:48:00 ubard kernel: [    0.851219] ata1.00: configured for UDMA/133
Dec 27 16:48:00 ubard kernel: [    0.851322] scsi 0:0:0:0: Direct-Access     ATA      Maxtor 6V300F0   VA11 PQ: 0 ANSI: 5
Dec 27 16:48:00 ubard kernel: [    0.851477] sd 0:0:0:0: Attached scsi generic sg0 type 0
Dec 27 16:48:00 ubard kernel: [    0.851532] sd 0:0:0:0: [sda] 586114704 512-byte logical blocks: (300 GB/279 GiB)
Dec 27 16:48:00 ubard kernel: [    0.851579] sd 0:0:0:0: [sda] Write Protect is off
Dec 27 16:48:00 ubard kernel: [    0.851607] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Dec 27 16:48:00 ubard kernel: [    0.851740]  sda: sda1
Dec 27 16:48:00 ubard kernel: [    0.872752] sd 0:0:0:0: [sda] Attached SCSI disk
Dec 27 16:48:00 ubard kernel: [    1.020011] usb 4-2: new low speed USB device using ohci_hcd and address 2
Dec 27 16:48:00 ubard kernel: [    1.260191] usb 4-2: configuration #1 chosen from 1 choice
Dec 27 16:48:00 ubard kernel: [    3.090665] ata2: SATA link down (SStatus 1 SControl 300)
Dec 27 16:48:00 ubard kernel: [    3.090782] scsi 2:0:0:0: Direct-Access     ATA      ST340016A        3.05 PQ: 0 ANSI: 5
Dec 27 16:48:00 ubard kernel: [    3.090923] sd 2:0:0:0: Attached scsi generic sg1 type 0
Dec 27 16:48:00 ubard kernel: [    3.090972] sd 2:0:0:0: [sdb] 78165360 512-byte logical blocks: (40.0 GB/37.2 GiB)
Dec 27 16:48:00 ubard kernel: [    3.091017] sd 2:0:0:0: [sdb] Write Protect is off
Dec 27 16:48:00 ubard kernel: [    3.091043] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Dec 27 16:48:00 ubard kernel: [    3.091173]  sdb: sdb1 sdb2 < sdb5 >
Dec 27 16:48:00 ubard kernel: [    3.134838] sd 2:0:0:0: [sdb] Attached SCSI disk
Dec 27 16:48:00 ubard kernel: [    3.270249] ata4.00: ATAPI: _NEC DVD_RW ND-3500AG, 2.1A, max UDMA/33
Dec 27 16:48:00 ubard kernel: [    3.310261] ata4.00: configured for UDMA/33
Dec 27 16:48:00 ubard kernel: [    3.311261] scsi 3:0:0:0: CD-ROM            _NEC     DVD_RW ND-3500AG 2.1A PQ: 0 ANSI: 5
Dec 27 16:48:00 ubard kernel: [    3.313257] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
Dec 27 16:48:00 ubard kernel: [    3.313261] Uniform CD-ROM driver Revision: 3.20
Dec 27 16:48:00 ubard kernel: [    3.313423] sr 3:0:0:0: Attached scsi generic sg2 type 5
Dec 27 16:48:00 ubard kernel: [    3.313459] Freeing unused kernel memory: 660k freed
Dec 27 16:48:00 ubard kernel: [    3.313941] Write protecting the kernel read-only data: 7572k
Dec 27 16:48:00 ubard kernel: [    3.611588] 3c59x 0000:00:09.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Dec 27 16:48:00 ubard kernel: [    3.611604] 3c59x: Donald Becker and others.
Dec 27 16:48:00 ubard kernel: [    3.611612] 0000:00:09.0: 3Com PCI 3c905C Tornado at ffffc900008b6800.
Dec 27 16:48:00 ubard kernel: [    3.723249] 3c59x 0000:00:09.0: PCI INT A disabled
Dec 27 16:48:00 ubard kernel: [    3.723291] 3c59x: probe of 0000:00:09.0 failed with error -22
Dec 27 16:48:00 ubard kernel: [    3.818200] usbcore: registered new interface driver hiddev
Dec 27 16:48:00 ubard kernel: [    3.850949] input: Darfon USB Keyboard as /devices/pci0000:00/0000:00:03.2/usb4/4-2/4-2:1.0/input/input3
Dec 27 16:48:00 ubard kernel: [    3.851028] generic-usb 0003:0D62:0004.0001: input,hidraw0: USB HID v1.10 Keyboard [Darfon USB Keyboard] on usb-0000:00:03.2-2/input0
Dec 27 16:48:00 ubard kernel: [    3.880553] input: Darfon USB Keyboard as /devices/pci0000:00/0000:00:03.2/usb4/4-2/4-2:1.1/input/input4
Dec 27 16:48:00 ubard kernel: [    3.880664] generic-usb 0003:0D62:0004.0002: input,hiddev96,hidraw1: USB HID v1.10 Device [Darfon USB Keyboard] on usb-0000:00:03.2-2/input1
Dec 27 16:48:00 ubard kernel: [    3.880686] usbcore: registered new interface driver usbhid
Dec 27 16:48:00 ubard kernel: [    3.880689] usbhid: v2.6:USB HID core driver
Dec 27 16:48:00 ubard kernel: [    4.505786] PM: Starting manual resume from disk
Dec 27 16:48:00 ubard kernel: [    4.509969] EXT4-fs (dm-0): INFO: recovery required on readonly filesystem
Dec 27 16:48:00 ubard kernel: [    4.509976] EXT4-fs (dm-0): write access will be enabled during recovery
Dec 27 16:48:00 ubard kernel: [    4.539153] EXT4-fs (dm-0): barriers enabled
Dec 27 16:48:00 ubard kernel: [    5.859573] kjournald2 starting: pid 367, dev dm-0:8, commit interval 5 seconds
Dec 27 16:48:00 ubard kernel: [    5.859598] EXT4-fs (dm-0): delayed allocation enabled
Dec 27 16:48:00 ubard kernel: [    5.859601] EXT4-fs: file extents enabled
Dec 27 16:48:00 ubard kernel: [    5.860322] EXT4-fs: mballoc enabled
Dec 27 16:48:00 ubard kernel: [    5.860344] EXT4-fs (dm-0): orphan cleanup on readonly fs
Dec 27 16:48:00 ubard kernel: [    6.046790] EXT4-fs (dm-0): 5 orphan inodes deleted
Dec 27 16:48:00 ubard kernel: [    6.046794] EXT4-fs (dm-0): recovery complete
Dec 27 16:48:00 ubard kernel: [    6.102266] EXT4-fs (dm-0): mounted filesystem with ordered data mode
Dec 27 16:48:00 ubard kernel: [    6.807297] type=1505 audit(1261928866.644:2): operation="profile_load" pid=388 name=/bin/ping
Dec 27 16:48:00 ubard kernel: [    6.810713] type=1505 audit(1261928866.654:3): operation="profile_load" pid=389 name=/sbin/dhclient3
Dec 27 16:48:00 ubard kernel: [    6.811059] type=1505 audit(1261928866.654:4): operation="profile_load" pid=389 name=/usr/lib/NetworkManager/nm-dhcp-client.action
Dec 27 16:48:00 ubard kernel: [    6.811250] type=1505 audit(1261928866.654:5): operation="profile_load" pid=389 name=/usr/lib/connman/scripts/dhclient-script
Dec 27 16:48:00 ubard kernel: [    6.813729] type=1505 audit(1261928866.654:6): operation="profile_load" pid=390 name=/sbin/klogd
Dec 27 16:48:00 ubard kernel: [    6.826882] type=1505 audit(1261928866.664:7): operation="profile_load" pid=391 name=/sbin/syslog-ng
Dec 27 16:48:00 ubard kernel: [    6.829426] type=1505 audit(1261928866.664:8): operation="profile_load" pid=392 name=/sbin/syslogd
Dec 27 16:48:00 ubard kernel: [    6.832044] type=1505 audit(1261928866.674:9): operation="profile_load" pid=393 name=/usr/lib/dovecot/deliver
Dec 27 16:48:00 ubard kernel: [    6.834703] type=1505 audit(1261928866.674:10): operation="profile_load" pid=394 name=/usr/lib/dovecot/dovecot-auth
Dec 27 16:48:00 ubard kernel: [    6.837318] type=1505 audit(1261928866.674:11): operation="profile_load" pid=395 name=/usr/lib/dovecot/imap
Dec 27 16:48:00 ubard kernel: [    7.834892] Adding 1642488k swap on /dev/mapper/ubard-swap_1.  Priority:-1 extents:1 across:1642488k 
Dec 27 16:48:00 ubard kernel: [    8.666331] udev: starting version 147
Dec 27 16:48:00 ubard kernel: [   10.545711] sis190 Gigabit Ethernet driver 1.3 loaded.
Dec 27 16:48:00 ubard kernel: [   10.545744] sis190 0000:00:04.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Dec 27 16:48:00 ubard kernel: [   10.545778] 0000:00:04.0: Read MAC address from EEPROM
Dec 27 16:48:00 ubard kernel: [   10.545781] 0000:00:04.0: Error EEPROM read 0.
Dec 27 16:48:00 ubard kernel: [   10.545783] 0000:00:04.0: Read MAC address from APC.
Dec 27 16:48:00 ubard kernel: [   10.660018] 0000:00:04.0: Realtek PHY RTL8201 transceiver at address 1.
Dec 27 16:48:00 ubard kernel: [   10.795644] EDAC MC: Ver: 2.1.0 Oct 16 2009
Dec 27 16:48:00 ubard kernel: [   10.894185] lp: driver loaded but no devices found
Dec 27 16:48:00 ubard kernel: [   10.911866] EDAC amd64_edac:  Ver: 3.2.0 Oct 16 2009
Dec 27 16:48:00 ubard kernel: [   11.081386] ip_tables: (C) 2000-2006 Netfilter Core Team
Dec 27 16:48:00 ubard kernel: [   11.900013] 0000:00:04.0: Using transceiver at address 1 as default.
Dec 27 16:48:00 ubard kernel: [   11.980746] 0000:00:04.0: SiS 190 PCI Fast Ethernet adapter at ffffc90000cbac00 (IRQ: 19), 00:13:d4:73:df:b5
Dec 27 16:48:00 ubard kernel: [   11.980751] eth0: GMII mode.
Dec 27 16:48:00 ubard kernel: [   11.980757] eth0: Enabling Auto-negotiation.
Dec 27 16:48:00 ubard kernel: [   12.062014] EDAC amd64: This node reports that Memory ECC is currently disabled.
Dec 27 16:48:00 ubard kernel: [   12.062019] EDAC amd64: bit 0x400000 in register F3x44 of the MISC_CONTROL device (0000:00:18.3) should be enabled
Dec 27 16:48:00 ubard kernel: [   12.062023] EDAC amd64: WARNING: ECC is NOT currently enabled by the BIOS. Module will NOT be loaded.
Dec 27 16:48:00 ubard kernel: [   12.062025]     Either Enable ECC in the BIOS, or use the 'ecc_enable_override' parameter.
Dec 27 16:48:00 ubard kernel: [   12.062026]     Might be a BIOS bug, if BIOS says ECC is enabled
Dec 27 16:48:00 ubard kernel: [   12.062027]     Use of the override can cause unknown side effects.
Dec 27 16:48:00 ubard kernel: [   12.062041] amd64_edac: probe of 0000:00:18.2 failed with error -22
Dec 27 16:48:00 ubard kernel: [   12.064502] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Dec 27 16:48:00 ubard kernel: [   12.644602] ADDRCONF(NETDEV_UP): eth0: link is not ready
Dec 27 16:48:00 ubard kernel: [   12.720019] eth0: auto-negotiating...
Dec 27 16:48:00 ubard kernel: [   12.780017] eth0: auto-negotiating...
Dec 27 16:48:00 ubard kernel: [   13.720028] eth0: mii ext = 0000.
Dec 27 16:48:00 ubard kernel: [   13.780021] eth0: mii lpa=45e1 adv=01e1 exp=0001.
Dec 27 16:48:00 ubard kernel: [   13.780025] eth0: link on 100 Mbps Full Duplex mode.
Dec 27 16:48:00 ubard kernel: [   13.780385] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Dec 27 16:48:00 ubard kernel: [   17.035367] EXT4-fs (dm-0): internal journal on dm-0:8
Dec 27 16:48:00 ubard kernel: [   17.315823] kjournald starting.  Commit interval 5 seconds
Dec 27 16:48:00 ubard kernel: [   17.316096] EXT3 FS on sda1, internal journal
Dec 27 16:48:00 ubard kernel: [   17.316100] EXT3-fs: recovery complete.
Dec 27 16:48:00 ubard kernel: [   17.316225] EXT3-fs: mounted filesystem with writeback data mode.
Dec 27 16:48:00 ubard kernel: [   17.889300] __ratelimit: 51 callbacks suppressed
Dec 27 16:48:00 ubard kernel: [   17.889305] type=1505 audit(1261928880.861:29): operation="profile_replace" pid=874 name=/bin/ping
Dec 27 16:48:00 ubard kernel: [   17.891832] type=1505 audit(1261928880.871:30): operation="profile_replace" pid=875 name=/sbin/dhclient3
Dec 27 16:48:00 ubard kernel: [   17.892186] type=1505 audit(1261928880.871:31): operation="profile_replace" pid=875 name=/usr/lib/NetworkManager/nm-dhcp-client.action
Dec 27 16:48:00 ubard kernel: [   17.892383] type=1505 audit(1261928880.871:32): operation="profile_replace" pid=875 name=/usr/lib/connman/scripts/dhclient-script
Dec 27 16:48:00 ubard kernel: [   17.895992] type=1505 audit(1261928880.871:33): operation="profile_replace" pid=876 name=/sbin/klogd
Dec 27 16:48:00 ubard kernel: [   17.898278] type=1505 audit(1261928880.871:34): operation="profile_replace" pid=877 name=/sbin/syslog-ng
Dec 27 16:48:00 ubard kernel: [   17.900684] type=1505 audit(1261928880.881:35): operation="profile_replace" pid=878 name=/sbin/syslogd
Dec 27 16:48:00 ubard kernel: [   17.903891] type=1505 audit(1261928880.881:36): operation="profile_replace" pid=879 name=/usr/lib/dovecot/deliver
Dec 27 16:48:00 ubard kernel: [   17.906254] type=1505 audit(1261928880.881:37): operation="profile_replace" pid=880 name=/usr/lib/dovecot/dovecot-auth
Dec 27 16:48:00 ubard kernel: [   17.908633] type=1505 audit(1261928880.881:38): operation="profile_replace" pid=881 name=/usr/lib/dovecot/imap
Dec 27 16:48:05 ubard kernel: [   22.860039] eth0: mii ext = 0000.
Dec 27 16:48:05 ubard kernel: [   22.923944] eth0: mii lpa=45e1 adv=01e1 exp=0001.
Dec 27 16:48:05 ubard kernel: [   22.923949] eth0: link on 100 Mbps Full Duplex mode.
Dec 27 16:49:10 ubard kernel: [   87.110110] Marking TSC unstable due to cpufreq changes
Dec 27 16:49:10 ubard kernel: [   87.640060] Clocksource tsc unstable (delta = -222232781 ns)

```

Contents of /var/log/dmesg :
 ```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.31-14-server (buildd@crested) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #48-Ubuntu SMP Fri Oct 16 15:07:34 UTC 2009 (Ubuntu 2.6.31-14.48-server)
[    0.000000] Command line: BOOT_IMAGE=/vmlinuz-2.6.31-14-server root=/dev/mapper/ubard-root ro quiet splash
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007df30000 (usable)
[    0.000000]  BIOS-e820: 000000007df30000 - 000000007df40000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007df40000 - 000000007dff0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007dff0000 - 000000007e000000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff780000 - 0000000100000000 (reserved)
[    0.000000] DMI 2.3 present.
[    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0x7df30 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 0000000000 mask FF80000000 write-back
[    0.000000]   1 disabled
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] Scanning 0 areas for low memory corruption
[    0.000000] modified physical RAM map:
[    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
[    0.000000]  modified: 0000000000010000 - 000000000009fc00 (usable)
[    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
[    0.000000]  modified: 0000000000100000 - 000000007df30000 (usable)
[    0.000000]  modified: 000000007df30000 - 000000007df40000 (ACPI data)
[    0.000000]  modified: 000000007df40000 - 000000007dff0000 (ACPI NVS)
[    0.000000]  modified: 000000007dff0000 - 000000007e000000 (reserved)
[    0.000000]  modified: 00000000ff780000 - 0000000100000000 (reserved)
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] init_memory_mapping: 0000000000000000-000000007df30000
[    0.000000] Using x86 segment limits to approximate NX protection
[    0.000000]  0000000000 - 007de00000 page 2M
[    0.000000]  007de00000 - 007df30000 page 4k
[    0.000000] kernel direct mapping tables up to 7df30000 @ 10000-14000
[    0.000000] RAMDISK: 378db000 - 37fef991
[    0.000000] ACPI: RSDP 00000000000fb140 00021 (v02 ACPIAM)
[    0.000000] ACPI: XSDT 000000007df30100 0003C (v01 A M I  OEMXSDT  03000631 MSFT 00000097)
[    0.000000] ACPI: FACP 000000007df30290 000F4 (v03 A M I  OEMFACP  03000631 MSFT 00000097)
[    0.000000] ACPI: DSDT 000000007df303f0 03D5E (v01  A0264 A0264601 00000601 INTL 02002026)
[    0.000000] ACPI: FACS 000000007df40000 00040
[    0.000000] ACPI: APIC 000000007df30390 00054 (v01 A M I  OEMAPIC  03000631 MSFT 00000097)
[    0.000000] ACPI: OEMB 000000007df40040 00040 (v01 A M I  AMI_OEM  03000631 MSFT 00000097)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000007df30000
[    0.000000] Bootmem setup node 0 0000000000000000-000000007df30000
[    0.000000]   NODE_DATA [0000000000012000 - 0000000000016fff]
[    0.000000]   bootmap [0000000000017000 -  0000000000026be7] pages 10
[    0.000000] (7 early reservations) ==> bootmem [0000000000 - 007df30000]
[    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
[    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
[    0.000000]   #2 [0001000000 - 00019e0ccc]    TEXT DATA BSS ==> [0001000000 - 00019e0ccc]
[    0.000000]   #3 [00378db000 - 0037fef991]          RAMDISK ==> [00378db000 - 0037fef991]
[    0.000000]   #4 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
[    0.000000]   #5 [00019e1000 - 00019e11c8]              BRK ==> [00019e1000 - 00019e11c8]
[    0.000000]   #6 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
[    0.000000] found SMP MP-table at [ffff8800000ff780] ff780
[    0.000000]  [ffffea0000000000-ffffea0001bfffff] PMD -> [ffff880001e00000-ffff8800039fffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00100000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0007df30
[    0.000000] On node 0 totalpages: 515775
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 101 pages reserved
[    0.000000]   DMA zone: 3826 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 6998 pages used for memmap
[    0.000000]   DMA32 zone: 504794 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 20, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 24
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
[    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 7e000000 (gap: 7e000000:81780000)
[    0.000000] NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:1 nr_node_ids:1
[    0.000000] PERCPU: Embedded 30 pages at ffff8800019f2000, static data 90720 bytes
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 508620
[    0.000000] Policy zone: DMA32
[    0.000000] Kernel command line: BOOT_IMAGE=/vmlinuz-2.6.31-14-server root=/dev/mapper/ubard-root ro quiet splash
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] Checking aperture...
[    0.000000] AGP bridge at 00:00:00
[    0.000000] Aperture from AGP @ f8000000 old size 32 MB
[    0.000000] Aperture from AGP @ f8000000 size 32 MB (APSIZE f38)
[    0.000000] Node 0: aperture @ f8000000 size 32 MB
[    0.000000] Aperture too small (32 MB) than (64 MB)
[    0.000000] Memory: 2016780k/2063552k available (5303k kernel code, 452k absent, 46320k reserved, 3013k data, 660k init)
[    0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.000000] NR_IRQS:4352 nr_irqs:256
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1795.303 MHz processor.
[    0.000011] spurious 8259A interrupt: IRQ7.
[    0.000884] Console: colour VGA+ 80x25
[    0.000888] console [tty0] enabled
[    0.010000] allocated 20971520 bytes of page_cgroup
[    0.010000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.010000] Calibrating delay loop (skipped), value calculated using timer frequency.. 3590.60 BogoMIPS (lpj=17953030)
[    0.010000] Security Framework initialized
[    0.010000] AppArmor: AppArmor initialized
[    0.010000] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.010000] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.010000] Mount-cache hash table entries: 256
[    0.010000] Initializing cgroup subsys ns
[    0.010000] Initializing cgroup subsys cpuacct
[    0.010000] Initializing cgroup subsys memory
[    0.010000] Initializing cgroup subsys freezer
[    0.010000] Initializing cgroup subsys net_cls
[    0.010000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[    0.010000] CPU: L2 Cache: 128K (64 bytes/line)
[    0.010000] CPU 0/0x0 -> Node 0
[    0.010000] tseg: 0000000000
[    0.010000] mce: CPU supports 5 MCE banks
[    0.010000] Performance Counters: AMD PMU driver.
[    0.010000] ... version:                 0
[    0.010000] ... bit width:               48
[    0.010000] ... generic counters:        4
[    0.010000] ... value mask:              0000ffffffffffff
[    0.010000] ... max period:              00007fffffffffff
[    0.010000] ... fixed-purpose counters:  0
[    0.010000] ... counter mask:            000000000000000f
[    0.010000] SMP alternatives: switching to UP code
[    0.012715] Freeing SMP alternatives: 39k freed
[    0.012747] ACPI: Core revision 20090521
[    0.018402] Setting APIC routing to flat
[    0.018651] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.118691] CPU0: AMD Sempron(tm) Processor 3000+ stepping 02
[    0.120000] Brought up 1 CPUs
[    0.120000] Total of 1 processors activated (3590.60 BogoMIPS).
[    0.120000] CPU0 attaching NULL sched-domain.
[    0.120000] Booting paravirtualized kernel on bare hardware
[    0.120000] regulator: core version 0.5
[    0.120000] Time: 15:47:40  Date: 12/27/09
[    0.120000] NET: Registered protocol family 16
[    0.120000] node 0 link 0: io port [1000, ffffff]
[    0.120000] TOM: 0000000080000000 aka 2048M
[    0.120000] node 0 link 0: mmio [a0000, bffff]
[    0.120000] node 0 link 0: mmio [80000000, ffffffff]
[    0.120000] bus: [00,ff] on node 0 link 0
[    0.120000] bus: 00 index 0 io port: [0, ffff]
[    0.120000] bus: 00 index 1 mmio: [a0000, bffff]
[    0.120000] bus: 00 index 2 mmio: [80000000, fcffffffff]
[    0.120000] ACPI: bus type pci registered
[    0.120000] PCI: Using configuration type 1 for base access
[    0.120000] bio: create slab <bio-0> at 0
[    0.120000] ACPI: EC: Look up EC in DSDT
[    0.120000] ACPI: Interpreter enabled
[    0.120000] ACPI: (supports S0 S1 S3 S4 S5)
[    0.120000] ACPI: Using IOAPIC for interrupt routing
[    0.125143] ACPI: No dock devices found.
[    0.125258] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.125310] pci 0000:00:00.0: reg 10 32bit mmio: [0xf8000000-0xf9ffffff]
[    0.125437] pci 0000:00:02.5: reg 20 io port: [0xffa0-0xffaf]
[    0.125456] pci 0000:00:02.5: PME# supported from D3cold
[    0.125460] pci 0000:00:02.5: PME# disabled
[    0.125478] pci 0000:00:03.0: reg 10 32bit mmio: [0xfbefc000-0xfbefcfff]
[    0.125513] pci 0000:00:03.1: reg 10 32bit mmio: [0xfbefd000-0xfbefdfff]
[    0.125549] pci 0000:00:03.2: reg 10 32bit mmio: [0xfbefe000-0xfbefefff]
[    0.125589] pci 0000:00:03.3: reg 10 32bit mmio: [0xfbeff000-0xfbefffff]
[    0.125617] pci 0000:00:03.3: PME# supported from D0 D3hot D3cold
[    0.125621] pci 0000:00:03.3: PME# disabled
[    0.125646] pci 0000:00:04.0: reg 10 32bit mmio: [0xfbefbc00-0xfbefbc7f]
[    0.125652] pci 0000:00:04.0: reg 14 io port: [0xb800-0xb87f]
[    0.125677] pci 0000:00:04.0: supports D1 D2
[    0.125680] pci 0000:00:04.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.125684] pci 0000:00:04.0: PME# disabled
[    0.125706] pci 0000:00:05.0: reg 10 io port: [0xb400-0xb407]
[    0.125711] pci 0000:00:05.0: reg 14 io port: [0xb000-0xb003]
[    0.125716] pci 0000:00:05.0: reg 18 io port: [0xa800-0xa807]
[    0.125722] pci 0000:00:05.0: reg 1c io port: [0xa400-0xa403]
[    0.125727] pci 0000:00:05.0: reg 20 io port: [0xa000-0xa00f]
[    0.125733] pci 0000:00:05.0: reg 24 io port: [0x9800-0x987f]
[    0.125749] pci 0000:00:05.0: PME# supported from D3cold
[    0.125752] pci 0000:00:05.0: PME# disabled
[    0.125788] pci 0000:00:06.0: PME# supported from D0 D3hot D3cold
[    0.125792] pci 0000:00:06.0: PME# disabled
[    0.125827] pci 0000:00:07.0: PME# supported from D0 D3hot D3cold
[    0.125831] pci 0000:00:07.0: PME# disabled
[    0.125855] pci 0000:00:09.0: reg 10 io port: [0x9400-0x947f]
[    0.125860] pci 0000:00:09.0: reg 14 32bit mmio: [0xbbefb800-0xbbefb87f]
[    0.125877] pci 0000:00:09.0: reg 30 32bit mmio: [0xbbec0000-0xbbedffff]
[    0.125890] pci 0000:00:09.0: supports D1 D2
[    0.125892] pci 0000:00:09.0: PME# supported from D0 D1 D2 D3cold
[    0.125896] pci 0000:00:09.0: PME# disabled
[    0.125997] pci 0000:01:00.0: reg 10 32bit mmio: [0xf0000000-0xf7ffffff]
[    0.126001] pci 0000:01:00.0: reg 14 32bit mmio: [0xfbfe0000-0xfbffffff]
[    0.126006] pci 0000:01:00.0: reg 18 io port: [0xc800-0xc87f]
[    0.126021] pci 0000:01:00.0: supports D1 D2
[    0.126042] pci 0000:00:01.0: bridge io port: [0xc000-0xcfff]
[    0.126046] pci 0000:00:01.0: bridge 32bit mmio: [0xfbf00000-0xfbffffff]
[    0.126050] pci 0000:00:01.0: bridge 32bit mmio pref: [0xf0000000-0xf7ffffff]
[    0.126089] pci 0000:00:06.0: bridge io port: [0xd000-0xdfff]
[    0.126132] pci 0000:00:07.0: bridge io port: [0xe000-0xefff]
[    0.126150] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.126309] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[    0.126374] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P6._PRT]
[    0.126424] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P7._PRT]
[    0.134421] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 10 *11 12 14 15)
[    0.134535] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 *10 11 12 14 15)
[    0.134646] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[    0.134752] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 7 10 11 12 14 15)
[    0.134859] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 *11 12 14 15)
[    0.134966] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 *4 5 7 10 11 12 14 15)
[    0.135072] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 *7 10 11 12 14 15)
[    0.135179] ACPI: PCI Interrupt Link [LNKH] (IRQs *3 4 5 7 10 11 12 14 15)
[    0.135384] SCSI subsystem initialized
[    0.135466] libata version 3.00 loaded.
[    0.135547] usbcore: registered new interface driver usbfs
[    0.135566] usbcore: registered new interface driver hub
[    0.135592] usbcore: registered new device driver usb
[    0.135746] ACPI: WMI: Mapper loaded
[    0.135748] PCI: Using ACPI for IRQ routing
[    0.135763] pci 0000:00:00.0: BAR 0: address space collision on of device [0xf8000000-0xf9ffffff]
[    0.135766] pci 0000:00:00.0: BAR 0: can't allocate resource
[    0.135916] Bluetooth: Core ver 2.15
[    0.135966] NET: Registered protocol family 31
[    0.135968] Bluetooth: HCI device and connection manager initialized
[    0.135972] Bluetooth: HCI socket layer initialized
[    0.135974] NetLabel: Initializing
[    0.135976] NetLabel:  domain hash size = 128
[    0.135978] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.135992] NetLabel:  unlabeled traffic allowed by default
[    0.136080] agpgart-amd64 0000:00:00.0: AGP bridge [1039/0760]
[    0.137149] agpgart-amd64 0000:00:00.0: AGP aperture is 32M @ 0xf8000000
[    0.138902] pnp: PnP ACPI init
[    0.138925] ACPI: bus type pnp registered
[    0.141211] pnp: PnP ACPI: found 7 devices
[    0.141215] ACPI: ACPI bus type pnp unregistered
[    0.141230] system 00:05: ioport range 0x290-0x297 has been reserved
[    0.141236] system 00:06: ioport range 0x480-0x48f has been reserved
[    0.141240] system 00:06: ioport range 0x4d0-0x4d1 has been reserved
[    0.141243] system 00:06: ioport range 0x800-0x8cf has been reserved
[    0.141246] system 00:06: ioport range 0x8d0-0x8ff has been reserved
[    0.141251] system 00:06: iomem range 0xfff80000-0xffffffff has been reserved
[    0.141254] system 00:06: iomem range 0xffee0000-0xffefffff has been reserved
[    0.141258] system 00:06: iomem range 0xfee00400-0xfee00fff has been reserved
[    0.145941] AppArmor: AppArmor Filesystem Enabled
[    0.145978] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.145981] pci 0000:00:01.0:   IO window: 0xc000-0xcfff
[    0.145986] pci 0000:00:01.0:   MEM window: 0xfbf00000-0xfbffffff
[    0.145990] pci 0000:00:01.0:   PREFETCH window: 0xf0000000-0xf7ffffff
[    0.145995] pci 0000:00:06.0: PCI bridge, secondary bus 0000:02
[    0.145998] pci 0000:00:06.0:   IO window: 0xd000-0xdfff
[    0.146002] pci 0000:00:06.0:   MEM window: disabled
[    0.146006] pci 0000:00:06.0:   PREFETCH window: disabled
[    0.146010] pci 0000:00:07.0: PCI bridge, secondary bus 0000:03
[    0.146013] pci 0000:00:07.0:   IO window: 0xe000-0xefff
[    0.146017] pci 0000:00:07.0:   MEM window: disabled
[    0.146020] pci 0000:00:07.0:   PREFETCH window: disabled
[    0.146035] pci 0000:00:06.0: setting latency timer to 64
[    0.146042] pci 0000:00:07.0: setting latency timer to 64
[    0.146047] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.146050] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]
[    0.146053] pci_bus 0000:01: resource 0 io:  [0xc000-0xcfff]
[    0.146056] pci_bus 0000:01: resource 1 mem: [0xfbf00000-0xfbffffff]
[    0.146059] pci_bus 0000:01: resource 2 pref mem [0xf0000000-0xf7ffffff]
[    0.146062] pci_bus 0000:02: resource 0 io:  [0xd000-0xdfff]
[    0.146065] pci_bus 0000:03: resource 0 io:  [0xe000-0xefff]
[    0.146109] NET: Registered protocol family 2
[    0.146255] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
[    0.147329] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[    0.150587] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.151371] TCP: Hash tables configured (established 262144 bind 65536)
[    0.151375] TCP reno registered
[    0.151496] NET: Registered protocol family 1
[    0.151565] Trying to unpack rootfs image as initramfs...
[    0.354510] Freeing initrd memory: 7250k freed
[    0.360490] Scanning for low memory corruption every 60 seconds
[    0.360637] audit: initializing netlink socket (disabled)
[    0.360653] type=2000 audit(1261928859.360:1): initialized
[    0.371087] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.372649] VFS: Disk quotas dquot_6.5.2
[    0.372728] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.373460] fuse init (API version 7.12)
[    0.373570] msgmni has been set to 3953
[    0.373839] alg: No test for stdrng (krng)
[    0.373855] io scheduler noop registered
[    0.373857] io scheduler anticipatory registered
[    0.373860] io scheduler deadline registered (default)
[    0.373934] io scheduler cfq registered
[    0.450066] pci 0000:01:00.0: Boot video device
[    0.450294] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.450318] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.450443] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    0.450447] ACPI: Power Button [PWRF]
[    0.450500] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.450503] ACPI: Power Button [PWRB]
[    0.450886] processor LNXCPU:00: registered as cooling_device0
[    0.455032] Linux agpgart interface v0.103
[    0.455047] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.456242] brd: module loaded
[    0.456726] loop: module loaded
[    0.456829] input: Macintosh mouse button emulation as /devices/virtual/input/input2
[    0.457130] sata_sis 0000:00:05.0: version 1.0
[    0.457145]   alloc irq_desc for 17 on node 0
[    0.457147]   alloc kstat_irqs on node 0
[    0.457156] sata_sis 0000:00:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.457161] sata_sis 0000:00:05.0: Detected SiS 182/965L chipset
[    0.457265] scsi0 : sata_sis
[    0.457392] scsi1 : sata_sis
[    0.457432] ata1: SATA max UDMA/133 cmd 0xb400 ctl 0xb000 bmdma 0xa000 irq 17
[    0.457437] ata2: SATA max UDMA/133 cmd 0xa800 ctl 0xa400 bmdma 0xa008 irq 17
[    0.457943] pata_sis 0000:00:02.5: version 0.5.2
[    0.458063] scsi2 : pata_sis
[    0.458148] scsi3 : pata_sis
[    0.458866] ata3: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[    0.458869] ata4: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[    0.459245] Fixed MDIO Bus: probed
[    0.459282] PPP generic driver version 2.4.2
[    0.459398] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.459500]   alloc irq_desc for 23 on node 0
[    0.459503]   alloc kstat_irqs on node 0
[    0.459511] ehci_hcd 0000:00:03.3: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    0.459531] ehci_hcd 0000:00:03.3: EHCI Host Controller
[    0.459614] ehci_hcd 0000:00:03.3: new USB bus registered, assigned bus number 1
[    0.459659] ehci_hcd 0000:00:03.3: cache line size of 64 is not supported
[    0.459677] ehci_hcd 0000:00:03.3: irq 23, io mem 0xfbeff000
[    0.470050] ehci_hcd 0000:00:03.3: USB 2.0 started, EHCI 1.00
[    0.470160] usb usb1: configuration #1 chosen from 1 choice
[    0.470193] hub 1-0:1.0: USB hub found
[    0.470203] hub 1-0:1.0: 8 ports detected
[    0.470308] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.470373]   alloc irq_desc for 20 on node 0
[    0.470376]   alloc kstat_irqs on node 0
[    0.470384] ohci_hcd 0000:00:03.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.470406] ohci_hcd 0000:00:03.0: OHCI Host Controller
[    0.470465] ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus number 2
[    0.470493] ohci_hcd 0000:00:03.0: irq 20, io mem 0xfbefc000
[    0.532135] usb usb2: configuration #1 chosen from 1 choice
[    0.532166] hub 2-0:1.0: USB hub found
[    0.532178] hub 2-0:1.0: 3 ports detected
[    0.532313]   alloc irq_desc for 21 on node 0
[    0.532316]   alloc kstat_irqs on node 0
[    0.532323] ohci_hcd 0000:00:03.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.532342] ohci_hcd 0000:00:03.1: OHCI Host Controller
[    0.532398] ohci_hcd 0000:00:03.1: new USB bus registered, assigned bus number 3
[    0.532426] ohci_hcd 0000:00:03.1: irq 21, io mem 0xfbefd000
[    0.592138] usb usb3: configuration #1 chosen from 1 choice
[    0.592168] hub 3-0:1.0: USB hub found
[    0.592179] hub 3-0:1.0: 3 ports detected
[    0.592308]   alloc irq_desc for 22 on node 0
[    0.592311]   alloc kstat_irqs on node 0
[    0.592319] ohci_hcd 0000:00:03.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    0.592338] ohci_hcd 0000:00:03.2: OHCI Host Controller
[    0.592398] ohci_hcd 0000:00:03.2: new USB bus registered, assigned bus number 4
[    0.592426] ohci_hcd 0000:00:03.2: irq 22, io mem 0xfbefe000
[    0.630449] ata3.00: ATA-5: ST340016A, 3.05, max UDMA/100
[    0.630452] ata3.00: 78165360 sectors, multi 16: LBA 
[    0.652159] usb usb4: configuration #1 chosen from 1 choice
[    0.652194] hub 4-0:1.0: USB hub found
[    0.652205] hub 4-0:1.0: 2 ports detected
[    0.652291] uhci_hcd: USB Universal Host Controller Interface driver
[    0.652421] PNP: No PS/2 controller found. Probing ports directly.
[    0.652670] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.652679] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.652748] mice: PS/2 mouse device common for all mice
[    0.652837] rtc_cmos 00:02: RTC can wake from S4
[    0.652878] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    0.652899] rtc0: alarms up to one month, 114 bytes nvram
[    0.653023] device-mapper: uevent: version 1.0.3
[    0.653426] ata3.00: configured for UDMA/100
[    0.653541] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.653610] device-mapper: multipath: version 1.1.0 loaded
[    0.653613] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.653762] cpuidle: using governor ladder
[    0.653765] cpuidle: using governor menu
[    0.654291] TCP cubic registered
[    0.654445] NET: Registered protocol family 10
[    0.654934] lo: Disabled Privacy Extensions
[    0.655254] NET: Registered protocol family 17
[    0.655281] Bluetooth: L2CAP ver 2.13
[    0.655283] Bluetooth: L2CAP socket layer initialized
[    0.655286] Bluetooth: SCO (Voice Link) ver 0.6
[    0.655288] Bluetooth: SCO socket layer initialized
[    0.655349] Bluetooth: RFCOMM TTY layer initialized
[    0.655352] Bluetooth: RFCOMM socket layer initialized
[    0.655354] Bluetooth: RFCOMM ver 1.11
[    0.655371] powernow-k8: Found 1 AMD Sempron(tm) Processor 3000+ processors (1 cpu cores) (version 2.20.00)
[    0.655411] powernow-k8:    0 : fid 0xa (1800 MHz), vid 0x6
[    0.655414] powernow-k8:    1 : fid 0x2 (1000 MHz), vid 0x12
[    0.655663] PM: Resume from disk failed.
[    0.655675] registered taskstats version 1
[    0.655800]   Magic number: 5:892:791
[    0.655865] rtc_cmos 00:02: setting system clock to 2009-12-27 15:47:40 UTC (1261928860)
[    0.655869] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.655871] EDD information not available.
[    0.660077] Switched to high resolution mode on CPU 0
[    0.790068] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    0.811210] ata1.00: ATA-7: Maxtor 6V300F0, VA111630, max UDMA/133
[    0.811214] ata1.00: 586114704 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    0.851219] ata1.00: configured for UDMA/133
[    0.851322] scsi 0:0:0:0: Direct-Access     ATA      Maxtor 6V300F0   VA11 PQ: 0 ANSI: 5
[    0.851477] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    0.851532] sd 0:0:0:0: [sda] 586114704 512-byte logical blocks: (300 GB/279 GiB)
[    0.851579] sd 0:0:0:0: [sda] Write Protect is off
[    0.851583] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    0.851607] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.851740]  sda: sda1
[    0.872752] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.020011] usb 4-2: new low speed USB device using ohci_hcd and address 2
[    1.260191] usb 4-2: configuration #1 chosen from 1 choice
[    3.090665] ata2: SATA link down (SStatus 1 SControl 300)
[    3.090782] scsi 2:0:0:0: Direct-Access     ATA      ST340016A        3.05 PQ: 0 ANSI: 5
[    3.090923] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    3.090972] sd 2:0:0:0: [sdb] 78165360 512-byte logical blocks: (40.0 GB/37.2 GiB)
[    3.091017] sd 2:0:0:0: [sdb] Write Protect is off
[    3.091020] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    3.091043] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.091173]  sdb: sdb1 sdb2 < sdb5 >
[    3.134838] sd 2:0:0:0: [sdb] Attached SCSI disk
[    3.270249] ata4.00: ATAPI: _NEC DVD_RW ND-3500AG, 2.1A, max UDMA/33
[    3.310261] ata4.00: configured for UDMA/33
[    3.311261] scsi 3:0:0:0: CD-ROM            _NEC     DVD_RW ND-3500AG 2.1A PQ: 0 ANSI: 5
[    3.313257] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[    3.313261] Uniform CD-ROM driver Revision: 3.20
[    3.313365] sr 3:0:0:0: Attached scsi CD-ROM sr0
[    3.313423] sr 3:0:0:0: Attached scsi generic sg2 type 5
[    3.313459] Freeing unused kernel memory: 660k freed
[    3.313941] Write protecting the kernel read-only data: 7572k
[    3.611573]   alloc irq_desc for 16 on node 0
[    3.611578]   alloc kstat_irqs on node 0
[    3.611588] 3c59x 0000:00:09.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.611604] 3c59x: Donald Becker and others.
[    3.611612] 0000:00:09.0: 3Com PCI 3c905C Tornado at ffffc900008b6800.
[    3.723237] *** EEPROM MAC address is invalid.
[    3.723243] 3c59x: vortex_probe1 fails.  Returns -22
[    3.723249] 3c59x 0000:00:09.0: PCI INT A disabled
[    3.723291] 3c59x: probe of 0000:00:09.0 failed with error -22
[    3.818200] usbcore: registered new interface driver hiddev
[    3.850949] input: Darfon USB Keyboard as /devices/pci0000:00/0000:00:03.2/usb4/4-2/4-2:1.0/input/input3
[    3.851028] generic-usb 0003:0D62:0004.0001: input,hidraw0: USB HID v1.10 Keyboard [Darfon USB Keyboard] on usb-0000:00:03.2-2/input0
[    3.880553] input: Darfon USB Keyboard as /devices/pci0000:00/0000:00:03.2/usb4/4-2/4-2:1.1/input/input4
[    3.880664] generic-usb 0003:0D62:0004.0002: input,hiddev96,hidraw1: USB HID v1.10 Device [Darfon USB Keyboard] on usb-0000:00:03.2-2/input1
[    3.880686] usbcore: registered new interface driver usbhid
[    3.880689] usbhid: v2.6:USB HID core driver
[    4.505786] PM: Starting manual resume from disk
[    4.505792] PM: Resume from partition 252:1
[    4.505794] PM: Checking hibernation image.
[    4.506040] PM: Resume from disk failed.
[    4.509969] EXT4-fs (dm-0): INFO: recovery required on readonly filesystem
[    4.509976] EXT4-fs (dm-0): write access will be enabled during recovery
[    4.539153] EXT4-fs (dm-0): barriers enabled
[    5.859573] kjournald2 starting: pid 367, dev dm-0:8, commit interval 5 seconds
[    5.859598] EXT4-fs (dm-0): delayed allocation enabled
[    5.859601] EXT4-fs: file extents enabled
[    5.860322] EXT4-fs: mballoc enabled
[    5.860344] EXT4-fs (dm-0): orphan cleanup on readonly fs
[    5.860358] EXT4-fs (dm-0): ext4_orphan_cleanup: deleting unreferenced inode 172751
[    5.860632] EXT4-fs (dm-0): ext4_orphan_cleanup: deleting unreferenced inode 163297
[    5.860643] EXT4-fs (dm-0): ext4_orphan_cleanup: deleting unreferenced inode 163288
[    6.038362] EXT4-fs (dm-0): ext4_orphan_cleanup: deleting unreferenced inode 161381
[    6.046772] EXT4-fs (dm-0): ext4_orphan_cleanup: deleting unreferenced inode 158710
[    6.046790] EXT4-fs (dm-0): 5 orphan inodes deleted
[    6.046794] EXT4-fs (dm-0): recovery complete
[    6.102266] EXT4-fs (dm-0): mounted filesystem with ordered data mode
[    6.807297] type=1505 audit(1261928866.644:2): operation="profile_load" pid=388 name=/bin/ping
[    6.810713] type=1505 audit(1261928866.654:3): operation="profile_load" pid=389 name=/sbin/dhclient3
[    6.811059] type=1505 audit(1261928866.654:4): operation="profile_load" pid=389 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    6.811250] type=1505 audit(1261928866.654:5): operation="profile_load" pid=389 name=/usr/lib/connman/scripts/dhclient-script
[    6.813729] type=1505 audit(1261928866.654:6): operation="profile_load" pid=390 name=/sbin/klogd
[    6.826882] type=1505 audit(1261928866.664:7): operation="profile_load" pid=391 name=/sbin/syslog-ng
[    6.829426] type=1505 audit(1261928866.664:8): operation="profile_load" pid=392 name=/sbin/syslogd
[    6.832044] type=1505 audit(1261928866.674:9): operation="profile_load" pid=393 name=/usr/lib/dovecot/deliver
[    6.834703] type=1505 audit(1261928866.674:10): operation="profile_load" pid=394 name=/usr/lib/dovecot/dovecot-auth
[    6.837318] type=1505 audit(1261928866.674:11): operation="profile_load" pid=395 name=/usr/lib/dovecot/imap
[    7.834892] Adding 1642488k swap on /dev/mapper/ubard-swap_1.  Priority:-1 extents:1 across:1642488k 
[    8.666331] udev: starting version 147
[   10.545711] sis190 Gigabit Ethernet driver 1.3 loaded.
[   10.545732]   alloc irq_desc for 19 on node 0
[   10.545734]   alloc kstat_irqs on node 0
[   10.545744] sis190 0000:00:04.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   10.545754] sis190 0000:00:04.0: setting latency timer to 64
[   10.545778] 0000:00:04.0: Read MAC address from EEPROM
[   10.545781] 0000:00:04.0: Error EEPROM read 0.
[   10.545783] 0000:00:04.0: Read MAC address from APC.
[   10.660018] 0000:00:04.0: Realtek PHY RTL8201 transceiver at address 1.
[   10.795644] EDAC MC: Ver: 2.1.0 Oct 16 2009
[   10.894185] lp: driver loaded but no devices found
[   10.911866] EDAC amd64_edac:  Ver: 3.2.0 Oct 16 2009
[   11.081386] ip_tables: (C) 2000-2006 Netfilter Core Team
[   11.900013] 0000:00:04.0: Using transceiver at address 1 as default.
[   11.980746] 0000:00:04.0: SiS 190 PCI Fast Ethernet adapter at ffffc90000cbac00 (IRQ: 19), 00:13:d4:73:df:b5
[   11.980751] eth0: GMII mode.
[   11.980757] eth0: Enabling Auto-negotiation.
[   12.062014] EDAC amd64: This node reports that Memory ECC is currently disabled.
[   12.062019] EDAC amd64: bit 0x400000 in register F3x44 of the MISC_CONTROL device (0000:00:18.3) should be enabled
[   12.062023] EDAC amd64: WARNING: ECC is NOT currently enabled by the BIOS. Module will NOT be loaded.
[   12.062025]     Either Enable ECC in the BIOS, or use the 'ecc_enable_override' parameter.
[   12.062026]     Might be a BIOS bug, if BIOS says ECC is enabled
[   12.062027]     Use of the override can cause unknown side effects.
[   12.062041] amd64_edac: probe of 0000:00:18.2 failed with error -22
[   12.064502] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   12.644602] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   12.720019] eth0: auto-negotiating...
[   12.780017] eth0: auto-negotiating...
[   13.720028] eth0: mii ext = 0000.
[   13.780021] eth0: mii lpa=45e1 adv=01e1 exp=0001.
[   13.780025] eth0: link on 100 Mbps Full Duplex mode.
[   13.780385] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   17.035367] EXT4-fs (dm-0): internal journal on dm-0:8
[   17.315823] kjournald starting.  Commit interval 5 seconds
[   17.316096] EXT3 FS on sda1, internal journal
[   17.316100] EXT3-fs: recovery complete.
[   17.316225] EXT3-fs: mounted filesystem with writeback data mode.
[   17.889300] __ratelimit: 51 callbacks suppressed
[   17.889305] type=1505 audit(1261928880.861:29): operation="profile_replace" pid=874 name=/bin/ping
[   17.891832] type=1505 audit(1261928880.871:30): operation="profile_replace" pid=875 name=/sbin/dhclient3
[   17.892186] type=1505 audit(1261928880.871:31): operation="profile_replace" pid=875 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   17.892383] type=1505 audit(1261928880.871:32): operation="profile_replace" pid=875 name=/usr/lib/connman/scripts/dhclient-script
[   17.895992] type=1505 audit(1261928880.871:33): operation="profile_replace" pid=876 name=/sbin/klogd
[   17.898278] type=1505 audit(1261928880.871:34): operation="profile_replace" pid=877 name=/sbin/syslog-ng
[   17.900684] type=1505 audit(1261928880.881:35): operation="profile_replace" pid=878 name=/sbin/syslogd
[   17.903891] type=1505 audit(1261928880.881:36): operation="profile_replace" pid=879 name=/usr/lib/dovecot/deliver
[   17.906254] type=1505 audit(1261928880.881:37): operation="profile_replace" pid=880 name=/usr/lib/dovecot/dovecot-auth
[   17.908633] type=1505 audit(1261928880.881:38): operation="profile_replace" pid=881 name=/usr/lib/dovecot/imap

```

Contents of /var/log/debug :
```

Dec 23 09:00:03 ubard kernel: [   23.750024] eth0: no IPv6 routers present
Dec 27 16:48:00 ubard kernel: [    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
Dec 27 16:48:00 ubard kernel: [    0.000000] MTRR default type: uncachable
Dec 27 16:48:00 ubard kernel: [    0.000000] MTRR fixed ranges enabled:
Dec 27 16:48:00 ubard kernel: [    0.000000]   00000-9FFFF write-back
Dec 27 16:48:00 ubard kernel: [    0.000000]   A0000-EFFFF uncachable
Dec 27 16:48:00 ubard kernel: [    0.000000]   F0000-FFFFF write-protect
Dec 27 16:48:00 ubard kernel: [    0.000000] MTRR variable ranges enabled:
Dec 27 16:48:00 ubard kernel: [    0.000000]   0 base 0000000000 mask FF80000000 write-back
Dec 27 16:48:00 ubard kernel: [    0.000000]   1 disabled
Dec 27 16:48:00 ubard kernel: [    0.000000]   2 disabled
Dec 27 16:48:00 ubard kernel: [    0.000000]   3 disabled
Dec 27 16:48:00 ubard kernel: [    0.000000]   4 disabled
Dec 27 16:48:00 ubard kernel: [    0.000000]   5 disabled
Dec 27 16:48:00 ubard kernel: [    0.000000]   6 disabled
Dec 27 16:48:00 ubard kernel: [    0.000000]   7 disabled
Dec 27 16:48:00 ubard kernel: [    0.000000] initial memory mapped : 0 - 20000000
Dec 27 16:48:00 ubard kernel: [    0.000000]  0000000000 - 007de00000 page 2M
Dec 27 16:48:00 ubard kernel: [    0.000000]  007de00000 - 007df30000 page 4k
Dec 27 16:48:00 ubard kernel: [    0.000000] kernel direct mapping tables up to 7df30000 @ 10000-14000
Dec 27 16:48:00 ubard kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Dec 27 16:48:00 ubard kernel: [    0.000000]  [ffffea0000000000-ffffea0001bfffff] PMD -> [ffff880001e00000-ffff8800039fffff] on node 0
Dec 27 16:48:00 ubard kernel: [    0.000000] On node 0 totalpages: 515775
Dec 27 16:48:00 ubard kernel: [    0.000000]   DMA zone: 56 pages used for memmap
Dec 27 16:48:00 ubard kernel: [    0.000000]   DMA zone: 101 pages reserved
Dec 27 16:48:00 ubard kernel: [    0.000000]   DMA zone: 3826 pages, LIFO batch:0
Dec 27 16:48:00 ubard kernel: [    0.000000]   DMA32 zone: 6998 pages used for memmap
Dec 27 16:48:00 ubard kernel: [    0.000000]   DMA32 zone: 504794 pages, LIFO batch:31
Dec 27 16:48:00 ubard kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Dec 27 16:48:00 ubard kernel: [    0.000000] ACPI: IRQ0 used by override.
Dec 27 16:48:00 ubard kernel: [    0.000000] ACPI: IRQ2 used by override.
Dec 27 16:48:00 ubard kernel: [    0.000000] ACPI: IRQ9 used by override.
Dec 27 16:48:00 ubard kernel: [    0.000000] nr_irqs_gsi: 24
Dec 27 16:48:00 ubard kernel: [    0.000011] spurious 8259A interrupt: IRQ7.
Dec 27 16:48:00 ubard kernel: [    0.010000] tseg: 0000000000
Dec 27 16:48:00 ubard kernel: [    0.120000] CPU0 attaching NULL sched-domain.
Dec 27 16:48:00 ubard kernel: [    0.120000] node 0 link 0: io port [1000, ffffff]
Dec 27 16:48:00 ubard kernel: [    0.120000] node 0 link 0: mmio [a0000, bffff]
Dec 27 16:48:00 ubard kernel: [    0.120000] node 0 link 0: mmio [80000000, ffffffff]
Dec 27 16:48:00 ubard kernel: [    0.120000] bus: [00,ff] on node 0 link 0
Dec 27 16:48:00 ubard kernel: [    0.120000] bus: 00 index 0 io port: [0, ffff]
Dec 27 16:48:00 ubard kernel: [    0.120000] bus: 00 index 1 mmio: [a0000, bffff]
Dec 27 16:48:00 ubard kernel: [    0.120000] bus: 00 index 2 mmio: [80000000, fcffffffff]
Dec 27 16:48:00 ubard kernel: [    0.120000] ACPI: EC: Look up EC in DSDT
Dec 27 16:48:00 ubard kernel: [    0.125310] pci 0000:00:00.0: reg 10 32bit mmio: [0xf8000000-0xf9ffffff]
Dec 27 16:48:00 ubard kernel: [    0.125437] pci 0000:00:02.5: reg 20 io port: [0xffa0-0xffaf]
Dec 27 16:48:00 ubard kernel: [    0.125478] pci 0000:00:03.0: reg 10 32bit mmio: [0xfbefc000-0xfbefcfff]
Dec 27 16:48:00 ubard kernel: [    0.125513] pci 0000:00:03.1: reg 10 32bit mmio: [0xfbefd000-0xfbefdfff]
Dec 27 16:48:00 ubard kernel: [    0.125549] pci 0000:00:03.2: reg 10 32bit mmio: [0xfbefe000-0xfbefefff]
Dec 27 16:48:00 ubard kernel: [    0.125589] pci 0000:00:03.3: reg 10 32bit mmio: [0xfbeff000-0xfbefffff]
Dec 27 16:48:00 ubard kernel: [    0.125646] pci 0000:00:04.0: reg 10 32bit mmio: [0xfbefbc00-0xfbefbc7f]
Dec 27 16:48:00 ubard kernel: [    0.125652] pci 0000:00:04.0: reg 14 io port: [0xb800-0xb87f]
Dec 27 16:48:00 ubard kernel: [    0.125677] pci 0000:00:04.0: supports D1 D2
Dec 27 16:48:00 ubard kernel: [    0.125706] pci 0000:00:05.0: reg 10 io port: [0xb400-0xb407]
Dec 27 16:48:00 ubard kernel: [    0.125711] pci 0000:00:05.0: reg 14 io port: [0xb000-0xb003]
Dec 27 16:48:00 ubard kernel: [    0.125716] pci 0000:00:05.0: reg 18 io port: [0xa800-0xa807]
Dec 27 16:48:00 ubard kernel: [    0.125722] pci 0000:00:05.0: reg 1c io port: [0xa400-0xa403]
Dec 27 16:48:00 ubard kernel: [    0.125727] pci 0000:00:05.0: reg 20 io port: [0xa000-0xa00f]
Dec 27 16:48:00 ubard kernel: [    0.125733] pci 0000:00:05.0: reg 24 io port: [0x9800-0x987f]
Dec 27 16:48:00 ubard kernel: [    0.125855] pci 0000:00:09.0: reg 10 io port: [0x9400-0x947f]
Dec 27 16:48:00 ubard kernel: [    0.125860] pci 0000:00:09.0: reg 14 32bit mmio: [0xbbefb800-0xbbefb87f]
Dec 27 16:48:00 ubard kernel: [    0.125877] pci 0000:00:09.0: reg 30 32bit mmio: [0xbbec0000-0xbbedffff]
Dec 27 16:48:00 ubard kernel: [    0.125890] pci 0000:00:09.0: supports D1 D2
Dec 27 16:48:00 ubard kernel: [    0.125997] pci 0000:01:00.0: reg 10 32bit mmio: [0xf0000000-0xf7ffffff]
Dec 27 16:48:00 ubard kernel: [    0.126001] pci 0000:01:00.0: reg 14 32bit mmio: [0xfbfe0000-0xfbffffff]
Dec 27 16:48:00 ubard kernel: [    0.126006] pci 0000:01:00.0: reg 18 io port: [0xc800-0xc87f]
Dec 27 16:48:00 ubard kernel: [    0.126021] pci 0000:01:00.0: supports D1 D2
Dec 27 16:48:00 ubard kernel: [    0.126042] pci 0000:00:01.0: bridge io port: [0xc000-0xcfff]
Dec 27 16:48:00 ubard kernel: [    0.126046] pci 0000:00:01.0: bridge 32bit mmio: [0xfbf00000-0xfbffffff]
Dec 27 16:48:00 ubard kernel: [    0.126050] pci 0000:00:01.0: bridge 32bit mmio pref: [0xf0000000-0xf7ffffff]
Dec 27 16:48:00 ubard kernel: [    0.126089] pci 0000:00:06.0: bridge io port: [0xd000-0xdfff]
Dec 27 16:48:00 ubard kernel: [    0.126132] pci 0000:00:07.0: bridge io port: [0xe000-0xefff]
Dec 27 16:48:00 ubard kernel: [    0.126150] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Dec 27 16:48:00 ubard kernel: [    0.126309] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
Dec 27 16:48:00 ubard kernel: [    0.126374] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P6._PRT]
Dec 27 16:48:00 ubard kernel: [    0.126424] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P7._PRT]
Dec 27 16:48:00 ubard kernel: [    0.135466] libata version 3.00 loaded.
Dec 27 16:48:00 ubard kernel: [    0.146035] pci 0000:00:06.0: setting latency timer to 64
Dec 27 16:48:00 ubard kernel: [    0.146042] pci 0000:00:07.0: setting latency timer to 64
Dec 27 16:48:00 ubard kernel: [    0.146047] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
Dec 27 16:48:00 ubard kernel: [    0.146050] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]
Dec 27 16:48:00 ubard kernel: [    0.146053] pci_bus 0000:01: resource 0 io:  [0xc000-0xcfff]
Dec 27 16:48:00 ubard kernel: [    0.146056] pci_bus 0000:01: resource 1 mem: [0xfbf00000-0xfbffffff]
Dec 27 16:48:00 ubard kernel: [    0.146059] pci_bus 0000:01: resource 2 pref mem [0xf0000000-0xf7ffffff]
Dec 27 16:48:00 ubard kernel: [    0.146062] pci_bus 0000:02: resource 0 io:  [0xd000-0xdfff]
Dec 27 16:48:00 ubard kernel: [    0.146065] pci_bus 0000:03: resource 0 io:  [0xe000-0xefff]
Dec 27 16:48:00 ubard kernel: [    0.450066] pci 0000:01:00.0: Boot video device
Dec 27 16:48:00 ubard kernel: [    0.457145]   alloc irq_desc for 17 on node 0
Dec 27 16:48:00 ubard kernel: [    0.457147]   alloc kstat_irqs on node 0
Dec 27 16:48:00 ubard kernel: [    0.457943] pata_sis 0000:00:02.5: version 0.5.2
Dec 27 16:48:00 ubard kernel: [    0.459500]   alloc irq_desc for 23 on node 0
Dec 27 16:48:00 ubard kernel: [    0.459503]   alloc kstat_irqs on node 0
Dec 27 16:48:00 ubard kernel: [    0.459659] ehci_hcd 0000:00:03.3: cache line size of 64 is not supported
Dec 27 16:48:00 ubard kernel: [    0.470373]   alloc irq_desc for 20 on node 0
Dec 27 16:48:00 ubard kernel: [    0.470376]   alloc kstat_irqs on node 0
Dec 27 16:48:00 ubard kernel: [    0.532313]   alloc irq_desc for 21 on node 0
Dec 27 16:48:00 ubard kernel: [    0.532316]   alloc kstat_irqs on node 0
Dec 27 16:48:00 ubard kernel: [    0.592308]   alloc irq_desc for 22 on node 0
Dec 27 16:48:00 ubard kernel: [    0.592311]   alloc kstat_irqs on node 0
Dec 27 16:48:00 ubard kernel: [    0.655663] PM: Resume from disk failed.
Dec 27 16:48:00 ubard kernel: [    0.660077] Switched to high resolution mode on CPU 0
Dec 27 16:48:00 ubard kernel: [    0.851583] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Dec 27 16:48:00 ubard kernel: [    3.091020] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
Dec 27 16:48:00 ubard kernel: [    3.313365] sr 3:0:0:0: Attached scsi CD-ROM sr0
Dec 27 16:48:00 ubard kernel: [    3.611573]   alloc irq_desc for 16 on node 0
Dec 27 16:48:00 ubard kernel: [    3.611578]   alloc kstat_irqs on node 0
Dec 27 16:48:00 ubard kernel: [    4.505792] PM: Resume from partition 252:1
Dec 27 16:48:00 ubard kernel: [    4.505794] PM: Checking hibernation image.
Dec 27 16:48:00 ubard kernel: [    4.506040] PM: Resume from disk failed.
Dec 27 16:48:00 ubard kernel: [    5.860358] EXT4-fs (dm-0): ext4_orphan_cleanup: deleting unreferenced inode 172751
Dec 27 16:48:00 ubard kernel: [    5.860632] EXT4-fs (dm-0): ext4_orphan_cleanup: deleting unreferenced inode 163297
Dec 27 16:48:00 ubard kernel: [    5.860643] EXT4-fs (dm-0): ext4_orphan_cleanup: deleting unreferenced inode 163288
Dec 27 16:48:00 ubard kernel: [    6.038362] EXT4-fs (dm-0): ext4_orphan_cleanup: deleting unreferenced inode 161381
Dec 27 16:48:00 ubard kernel: [    6.046772] EXT4-fs (dm-0): ext4_orphan_cleanup: deleting unreferenced inode 158710
Dec 27 16:48:00 ubard kernel: [   10.545732]   alloc irq_desc for 19 on node 0
Dec 27 16:48:00 ubard kernel: [   10.545734]   alloc kstat_irqs on node 0
Dec 27 16:48:00 ubard kernel: [   10.545754] sis190 0000:00:04.0: setting latency timer to 64
Dec 27 16:48:07 ubard kernel: [   24.230016] eth0: no IPv6 routers present

```Contents of /var/log/syslog:
```

Dec 26 13:39:01 ubard CRON[7680]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Dec 27 16:48:00 ubard kernel: imklog 4.2.0, log source = /var/run/rsyslog/kmsg started.
Dec 27 16:48:00 ubard rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="840" x-info="http://www.rsyslog.com"] (re)start
Dec 27 16:48:00 ubard rsyslogd: rsyslogd's groupid changed to 103
Dec 27 16:48:00 ubard rsyslogd: rsyslogd's userid changed to 101
Dec 27 16:48:00 ubard kernel: [    0.000000] Initializing cgroup subsys cpuset
Dec 27 16:48:00 ubard kernel: [    0.000000] Initializing cgroup subsys cpu
Dec 27 16:48:00 ubard kernel: [    0.000000] Linux version 2.6.31-14-server (buildd@crested) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #48-Ubuntu SMP Fri Oct 16 15:07:34 UTC 2009 (Ubuntu 2.6.31-14.48-server)
Dec 27 16:48:00 ubard kernel: [    0.000000] Command line: BOOT_IMAGE=/vmlinuz-2.6.31-14-server root=/dev/mapper/ubard-root ro quiet splash
Dec 27 16:48:00 ubard kernel: [    0.000000] KERNEL supported cpus:
Dec 27 16:48:00 ubard kernel: [    0.000000]   Intel GenuineIntel
Dec 27 16:48:00 ubard kernel: [    0.000000]   AMD AuthenticAMD
Dec 27 16:48:00 ubard kernel: [    0.000000]   Centaur CentaurHauls
Dec 27 16:48:00 ubard kernel: [    0.000000] BIOS-provided physical RAM map:
Dec 27 16:48:00 ubard kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Dec 27 16:48:00 ubard kernel: [    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Dec 27 16:48:00 ubard kernel: [    0.000000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
Dec 27 16:48:00 ubard kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000007df30000 (usable)
Dec 27 16:48:00 ubard kernel: [    0.000000]  BIOS-e820: 000000007df30000 - 000000007df40000 (ACPI data)
Dec 27 16:48:00 ubard kernel: [    0.000000]  BIOS-e820: 000000007df40000 - 000000007dff0000 (ACPI NVS)
Dec 27 16:48:00 ubard kernel: [    0.000000]  BIOS-e820: 000000007dff0000 - 000000007e000000 (reserved)
Dec 27 16:48:00 ubard kernel: [    0.000000]  BIOS-e820: 00000000ff780000 - 0000000100000000 (reserved)
Dec 27 16:48:00 ubard kernel: [    0.000000] DMI 2.3 present.
Dec 27 16:48:00 ubard kernel: [    0.000000] AMI BIOS detected: BIOS may corrupt low RAM, working around it.
Dec 27 16:48:00 ubard kernel: [    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
Dec 27 16:48:00 ubard kernel: [    0.000000] last_pfn = 0x7df30 max_arch_pfn = 0x400000000
Dec 27 16:48:00 ubard kernel: [    0.000000] MTRR default type: uncachable
Dec 27 16:48:00 ubard kernel: [    0.000000] MTRR fixed ranges enabled:
Dec 27 16:48:00 ubard kernel: [    0.000000]   00000-9FFFF write-back
Dec 27 16:48:00 ubard kernel: [    0.000000]   A0000-EFFFF uncachable
Dec 27 16:48:00 ubard kernel: [    0.000000]   F0000-FFFFF write-protect
Dec 27 16:48:00 ubard kernel: [    0.000000] MTRR variable ranges enabled:
Dec 27 16:48:00 ubard kernel: [    0.000000]   0 base 0000000000 mask FF80000000 write-back
Dec 27 16:48:00 ubard kernel: [    0.000000]   1 disabled
Dec 27 16:48:00 ubard kernel: [    0.000000]   2 disabled
Dec 27 16:48:00 ubard kernel: [    0.000000]   3 disabled
Dec 27 16:48:00 ubard kernel: [    0.000000]   4 disabled
Dec 27 16:48:00 ubard kernel: [    0.000000]   5 disabled
Dec 27 16:48:00 ubard kernel: [    0.000000]   6 disabled
Dec 27 16:48:00 ubard kernel: [    0.000000]   7 disabled
Dec 27 16:48:00 ubard kernel: [    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
Dec 27 16:48:00 ubard kernel: [    0.000000] Scanning 0 areas for low memory corruption
Dec 27 16:48:00 ubard kernel: [    0.000000] modified physical RAM map:
Dec 27 16:48:00 ubard kernel: [    0.000000]  modified: 0000000000000000 - 0000000000010000 (reserved)
Dec 27 16:48:00 ubard kernel: [    0.000000]  modified: 0000000000010000 - 000000000009fc00 (usable)
Dec 27 16:48:00 ubard kernel: [    0.000000]  modified: 000000000009fc00 - 00000000000a0000 (reserved)
Dec 27 16:48:00 ubard kernel: [    0.000000]  modified: 00000000000e0000 - 0000000000100000 (reserved)
Dec 27 16:48:00 ubard kernel: [    0.000000]  modified: 0000000000100000 - 000000007df30000 (usable)
Dec 27 16:48:00 ubard kernel: [    0.000000]  modified: 000000007df30000 - 000000007df40000 (ACPI data)
Dec 27 16:48:00 ubard kernel: [    0.000000]  modified: 000000007df40000 - 000000007dff0000 (ACPI NVS)
Dec 27 16:48:00 ubard kernel: [    0.000000]  modified: 000000007dff0000 - 000000007e000000 (reserved)
Dec 27 16:48:00 ubard kernel: [    0.000000]  modified: 00000000ff780000 - 0000000100000000 (reserved)
Dec 27 16:48:00 ubard kernel: [    0.000000] initial memory mapped : 0 - 20000000
Dec 27 16:48:00 ubard kernel: [    0.000000] init_memory_mapping: 0000000000000000-000000007df30000
Dec 27 16:48:00 ubard kernel: [    0.000000] Using x86 segment limits to approximate NX protection
Dec 27 16:48:00 ubard kernel: [    0.000000]  0000000000 - 007de00000 page 2M
Dec 27 16:48:00 ubard kernel: [    0.000000]  007de00000 - 007df30000 page 4k
Dec 27 16:48:00 ubard kernel: [    0.000000] kernel direct mapping tables up to 7df30000 @ 10000-14000
Dec 27 16:48:00 ubard kernel: [    0.000000] RAMDISK: 378db000 - 37fef991
Dec 27 16:48:00 ubard kernel: [    0.000000] ACPI: RSDP 00000000000fb140 00021 (v02 ACPIAM)
Dec 27 16:48:00 ubard kernel: [    0.000000] ACPI: XSDT 000000007df30100 0003C (v01 A M I  OEMXSDT  03000631 MSFT 00000097)
Dec 27 16:48:00 ubard kernel: [    0.000000] ACPI: FACP 000000007df30290 000F4 (v03 A M I  OEMFACP  03000631 MSFT 00000097)
Dec 27 16:48:00 ubard kernel: [    0.000000] ACPI: DSDT 000000007df303f0 03D5E (v01  A0264 A0264601 00000601 INTL 02002026)
Dec 27 16:48:00 ubard kernel: [    0.000000] ACPI: FACS 000000007df40000 00040
Dec 27 16:48:00 ubard kernel: [    0.000000] ACPI: APIC 000000007df30390 00054 (v01 A M I  OEMAPIC  03000631 MSFT 00000097)
Dec 27 16:48:00 ubard kernel: [    0.000000] ACPI: OEMB 000000007df40040 00040 (v01 A M I  AMI_OEM  03000631 MSFT 00000097)
Dec 27 16:48:00 ubard kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Dec 27 16:48:00 ubard kernel: [    0.000000] Scanning NUMA topology in Northbridge 24
Dec 27 16:48:00 ubard kernel: [    0.000000] No NUMA configuration found
Dec 27 16:48:00 ubard kernel: [    0.000000] Faking a node at 0000000000000000-000000007df30000
Dec 27 16:48:00 ubard kernel: [    0.000000] Bootmem setup node 0 0000000000000000-000000007df30000
Dec 27 16:48:00 ubard kernel: [    0.000000]   NODE_DATA [0000000000012000 - 0000000000016fff]
Dec 27 16:48:00 ubard kernel: [    0.000000]   bootmap [0000000000017000 -  0000000000026be7] pages 10
Dec 27 16:48:00 ubard kernel: [    0.000000] (7 early reservations) ==> bootmem [0000000000 - 007df30000]
Dec 27 16:48:00 ubard kernel: [    0.000000]   #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
Dec 27 16:48:00 ubard kernel: [    0.000000]   #1 [0000006000 - 0000008000]       TRAMPOLINE ==> [0000006000 - 0000008000]
Dec 27 16:48:00 ubard kernel: [    0.000000]   #2 [0001000000 - 00019e0ccc]    TEXT DATA BSS ==> [0001000000 - 00019e0ccc]
Dec 27 16:48:00 ubard kernel: [    0.000000]   #3 [00378db000 - 0037fef991]          RAMDISK ==> [00378db000 - 0037fef991]
Dec 27 16:48:00 ubard kernel: [    0.000000]   #4 [000009fc00 - 0000100000]    BIOS reserved ==> [000009fc00 - 0000100000]
Dec 27 16:48:00 ubard kernel: [    0.000000]   #5 [00019e1000 - 00019e11c8]              BRK ==> [00019e1000 - 00019e11c8]
Dec 27 16:48:00 ubard kernel: [    0.000000]   #6 [0000010000 - 0000012000]          PGTABLE ==> [0000010000 - 0000012000]
Dec 27 16:48:00 ubard kernel: [    0.000000] found SMP MP-table at [ffff8800000ff780] ff780
Dec 27 16:48:00 ubard kernel: [    0.000000]  [ffffea0000000000-ffffea0001bfffff] PMD -> [ffff880001e00000-ffff8800039fffff] on node 0
Dec 27 16:48:00 ubard kernel: [    0.000000] Zone PFN ranges:
Dec 27 16:48:00 ubard kernel: [    0.000000]   DMA      0x00000010 -> 0x00001000
Dec 27 16:48:00 ubard kernel: [    0.000000]   DMA32    0x00001000 -> 0x00100000
Dec 27 16:48:00 ubard kernel: [    0.000000]   Normal   0x00100000 -> 0x00100000
Dec 27 16:48:00 ubard kernel: [    0.000000] Movable zone start PFN for each node
Dec 27 16:48:00 ubard kernel: [    0.000000] early_node_map[2] active PFN ranges
Dec 27 16:48:00 ubard kernel: [    0.000000]     0: 0x00000010 -> 0x0000009f
Dec 27 16:48:00 ubard kernel: [    0.000000]     0: 0x00000100 -> 0x0007df30
Dec 27 16:48:00 ubard kernel: [    0.000000] On node 0 totalpages: 515775
Dec 27 16:48:00 ubard kernel: [    0.000000]   DMA zone: 56 pages used for memmap
Dec 27 16:48:00 ubard kernel: [    0.000000]   DMA zone: 101 pages reserved
Dec 27 16:48:00 ubard kernel: [    0.000000]   DMA zone: 3826 pages, LIFO batch:0
Dec 27 16:48:00 ubard kernel: [    0.000000]   DMA32 zone: 6998 pages used for memmap
Dec 27 16:48:00 ubard kernel: [    0.000000]   DMA32 zone: 504794 pages, LIFO batch:31
Dec 27 16:48:00 ubard kernel: [    0.000000] ACPI: PM-Timer IO Port: 0x808
Dec 27 16:48:00 ubard kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Dec 27 16:48:00 ubard kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Dec 27 16:48:00 ubard kernel: [    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
Dec 27 16:48:00 ubard kernel: [    0.000000] IOAPIC[0]: apic_id 1, version 20, address 0xfec00000, GSI 0-23
Dec 27 16:48:00 ubard kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
Dec 27 16:48:00 ubard kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
Dec 27 16:48:00 ubard kernel: [    0.000000] ACPI: IRQ0 used by override.
Dec 27 16:48:00 ubard kernel: [    0.000000] ACPI: IRQ2 used by override.
Dec 27 16:48:00 ubard kernel: [    0.000000] ACPI: IRQ9 used by override.
Dec 27 16:48:00 ubard kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Dec 27 16:48:00 ubard kernel: [    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
Dec 27 16:48:00 ubard kernel: [    0.000000] nr_irqs_gsi: 24
Dec 27 16:48:00 ubard kernel: [    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
Dec 27 16:48:00 ubard kernel: [    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000e0000
Dec 27 16:48:00 ubard kernel: [    0.000000] PM: Registered nosave memory: 00000000000e0000 - 0000000000100000
Dec 27 16:48:00 ubard kernel: [    0.000000] Allocating PCI resources starting at 7e000000 (gap: 7e000000:81780000)
Dec 27 16:48:00 ubard kernel: [    0.000000] NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:1 nr_node_ids:1
Dec 27 16:48:00 ubard kernel: [    0.000000] PERCPU: Embedded 30 pages at ffff8800019f2000, static data 90720 bytes
Dec 27 16:48:00 ubard kernel: [    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 508620
Dec 27 16:48:00 ubard kernel: [    0.000000] Policy zone: DMA32
Dec 27 16:48:00 ubard kernel: [    0.000000] Kernel command line: BOOT_IMAGE=/vmlinuz-2.6.31-14-server root=/dev/mapper/ubard-root ro quiet splash
Dec 27 16:48:00 ubard kernel: [    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
Dec 27 16:48:00 ubard kernel: [    0.000000] Initializing CPU#0
Dec 27 16:48:00 ubard kernel: [    0.000000] Checking aperture...
Dec 27 16:48:00 ubard kernel: [    0.000000] AGP bridge at 00:00:00
Dec 27 16:48:00 ubard kernel: [    0.000000] Aperture from AGP @ f8000000 old size 32 MB
Dec 27 16:48:00 ubard kernel: [    0.000000] Aperture from AGP @ f8000000 size 32 MB (APSIZE f38)
Dec 27 16:48:00 ubard kernel: [    0.000000] Node 0: aperture @ f8000000 size 32 MB
Dec 27 16:48:00 ubard kernel: [    0.000000] Aperture too small (32 MB) than (64 MB)
Dec 27 16:48:00 ubard kernel: [    0.000000] Memory: 2016780k/2063552k available (5303k kernel code, 452k absent, 46320k reserved, 3013k data, 660k init)
Dec 27 16:48:00 ubard kernel: [    0.000000] SLUB: Genslabs=14, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
Dec 27 16:48:00 ubard kernel: [    0.000000] NR_IRQS:4352 nr_irqs:256
Dec 27 16:48:00 ubard kernel: [    0.000000] Fast TSC calibration using PIT
Dec 27 16:48:00 ubard kernel: [    0.000000] Detected 1795.303 MHz processor.
Dec 27 16:48:00 ubard kernel: [    0.000011] spurious 8259A interrupt: IRQ7.
Dec 27 16:48:00 ubard kernel: [    0.000884] Console: colour VGA+ 80x25
Dec 27 16:48:00 ubard kernel: [    0.000888] console [tty0] enabled
Dec 27 16:48:00 ubard kernel: [    0.010000] allocated 20971520 bytes of page_cgroup
Dec 27 16:48:00 ubard kernel: [    0.010000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
Dec 27 16:48:00 ubard kernel: [    0.010000] Calibrating delay loop (skipped), value calculated using timer frequency.. 3590.60 BogoMIPS (lpj=17953030)
Dec 27 16:48:00 ubard kernel: [    0.010000] Security Framework initialized
Dec 27 16:48:00 ubard kernel: [    0.010000] AppArmor: AppArmor initialized
Dec 27 16:48:00 ubard kernel: [    0.010000] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
Dec 27 16:48:00 ubard kernel: [    0.010000] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
Dec 27 16:48:00 ubard kernel: [    0.010000] Mount-cache hash table entries: 256
Dec 27 16:48:00 ubard kernel: [    0.010000] Initializing cgroup subsys ns
Dec 27 16:48:00 ubard kernel: [    0.010000] Initializing cgroup subsys cpuacct
Dec 27 16:48:00 ubard kernel: [    0.010000] Initializing cgroup subsys memory
Dec 27 16:48:00 ubard kernel: [    0.010000] Initializing cgroup subsys freezer
Dec 27 16:48:00 ubard kernel: [    0.010000] Initializing cgroup subsys net_cls
Dec 27 16:48:00 ubard kernel: [    0.010000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Dec 27 16:48:00 ubard kernel: [    0.010000] CPU: L2 Cache: 128K (64 bytes/line)
Dec 27 16:48:00 ubard kernel: [    0.010000] CPU 0/0x0 -> Node 0
Dec 27 16:48:00 ubard kernel: [    0.010000] tseg: 0000000000
Dec 27 16:48:00 ubard kernel: [    0.010000] mce: CPU supports 5 MCE banks
Dec 27 16:48:00 ubard kernel: [    0.010000] Performance Counters: AMD PMU driver.
Dec 27 16:48:00 ubard kernel: [    0.010000] ... version:                 0
Dec 27 16:48:00 ubard kernel: [    0.010000] ... bit width:               48
Dec 27 16:48:00 ubard kernel: [    0.010000] ... generic counters:        4
Dec 27 16:48:00 ubard kernel: [    0.010000] ... value mask:              0000ffffffffffff
Dec 27 16:48:00 ubard kernel: [    0.010000] ... max period:              00007fffffffffff
Dec 27 16:48:00 ubard kernel: [    0.010000] ... fixed-purpose counters:  0
Dec 27 16:48:00 ubard kernel: [    0.010000] ... counter mask:            000000000000000f
Dec 27 16:48:00 ubard kernel: [    0.010000] SMP alternatives: switching to UP code
Dec 27 16:48:00 ubard kernel: [    0.012715] Freeing SMP alternatives: 39k freed
Dec 27 16:48:00 ubard kernel: [    0.012747] ACPI: Core revision 20090521
Dec 27 16:48:00 ubard kernel: [    0.018402] Setting APIC routing to flat
Dec 27 16:48:00 ubard kernel: [    0.018651] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
Dec 27 16:48:00 ubard kernel: [    0.118691] CPU0: AMD Sempron(tm) Processor 3000+ stepping 02
Dec 27 16:48:00 ubard kernel: [    0.120000] Brought up 1 CPUs
Dec 27 16:48:00 ubard kernel: [    0.120000] Total of 1 processors activated (3590.60 BogoMIPS).
Dec 27 16:48:00 ubard kernel: [    0.120000] CPU0 attaching NULL sched-domain.
Dec 27 16:48:00 ubard kernel: [    0.120000] Booting paravirtualized kernel on bare hardware
Dec 27 16:48:00 ubard kernel: [    0.120000] regulator: core version 0.5
Dec 27 16:48:00 ubard kernel: [    0.120000] Time: 15:47:40  Date: 12/27/09
Dec 27 16:48:00 ubard kernel: [    0.120000] NET: Registered protocol family 16
Dec 27 16:48:00 ubard kernel: [    0.120000] node 0 link 0: io port [1000, ffffff]
Dec 27 16:48:00 ubard kernel: [    0.120000] TOM: 0000000080000000 aka 2048M
Dec 27 16:48:00 ubard kernel: [    0.120000] node 0 link 0: mmio [a0000, bffff]
Dec 27 16:48:00 ubard kernel: [    0.120000] node 0 link 0: mmio [80000000, ffffffff]
Dec 27 16:48:00 ubard kernel: [    0.120000] bus: [00,ff] on node 0 link 0
Dec 27 16:48:00 ubard kernel: [    0.120000] bus: 00 index 0 io port: [0, ffff]
Dec 27 16:48:00 ubard kernel: [    0.120000] bus: 00 index 1 mmio: [a0000, bffff]
Dec 27 16:48:00 ubard kernel: [    0.120000] bus: 00 index 2 mmio: [80000000, fcffffffff]
Dec 27 16:48:00 ubard kernel: [    0.120000] ACPI: bus type pci registered
Dec 27 16:48:00 ubard kernel: [    0.120000] PCI: Using configuration type 1 for base access
Dec 27 16:48:00 ubard kernel: [    0.120000] bio: create slab <bio-0> at 0
Dec 27 16:48:00 ubard kernel: [    0.120000] ACPI: EC: Look up EC in DSDT
Dec 27 16:48:00 ubard kernel: [    0.120000] ACPI: Interpreter enabled
Dec 27 16:48:00 ubard kernel: [    0.120000] ACPI: (supports S0 S1 S3 S4 S5)
Dec 27 16:48:00 ubard kernel: [    0.120000] ACPI: Using IOAPIC for interrupt routing
Dec 27 16:48:00 ubard kernel: [    0.125143] ACPI: No dock devices found.
Dec 27 16:48:00 ubard kernel: [    0.125258] ACPI: PCI Root Bridge [PCI0] (0000:00)
Dec 27 16:48:00 ubard kernel: [    0.125310] pci 0000:00:00.0: reg 10 32bit mmio: [0xf8000000-0xf9ffffff]
Dec 27 16:48:00 ubard kernel: [    0.125437] pci 0000:00:02.5: reg 20 io port: [0xffa0-0xffaf]
Dec 27 16:48:00 ubard kernel: [    0.125456] pci 0000:00:02.5: PME# supported from D3cold
Dec 27 16:48:00 ubard kernel: [    0.125460] pci 0000:00:02.5: PME# disabled
Dec 27 16:48:00 ubard kernel: [    0.125478] pci 0000:00:03.0: reg 10 32bit mmio: [0xfbefc000-0xfbefcfff]
Dec 27 16:48:00 ubard kernel: [    0.125513] pci 0000:00:03.1: reg 10 32bit mmio: [0xfbefd000-0xfbefdfff]
Dec 27 16:48:00 ubard kernel: [    0.125549] pci 0000:00:03.2: reg 10 32bit mmio: [0xfbefe000-0xfbefefff]
Dec 27 16:48:00 ubard kernel: [    0.125589] pci 0000:00:03.3: reg 10 32bit mmio: [0xfbeff000-0xfbefffff]
Dec 27 16:48:00 ubard kernel: [    0.125617] pci 0000:00:03.3: PME# supported from D0 D3hot D3cold
Dec 27 16:48:00 ubard kernel: [    0.125621] pci 0000:00:03.3: PME# disabled
Dec 27 16:48:00 ubard kernel: [    0.125646] pci 0000:00:04.0: reg 10 32bit mmio: [0xfbefbc00-0xfbefbc7f]
Dec 27 16:48:00 ubard kernel: [    0.125652] pci 0000:00:04.0: reg 14 io port: [0xb800-0xb87f]
Dec 27 16:48:00 ubard kernel: [    0.125677] pci 0000:00:04.0: supports D1 D2
Dec 27 16:48:00 ubard kernel: [    0.125680] pci 0000:00:04.0: PME# supported from D0 D1 D2 D3hot D3cold
Dec 27 16:48:00 ubard kernel: [    0.125684] pci 0000:00:04.0: PME# disabled
Dec 27 16:48:00 ubard kernel: [    0.125706] pci 0000:00:05.0: reg 10 io port: [0xb400-0xb407]
Dec 27 16:48:00 ubard kernel: [    0.125711] pci 0000:00:05.0: reg 14 io port: [0xb000-0xb003]
Dec 27 16:48:00 ubard kernel: [    0.125716] pci 0000:00:05.0: reg 18 io port: [0xa800-0xa807]
Dec 27 16:48:00 ubard kernel: [    0.125722] pci 0000:00:05.0: reg 1c io port: [0xa400-0xa403]
Dec 27 16:48:00 ubard kernel: [    0.125727] pci 0000:00:05.0: reg 20 io port: [0xa000-0xa00f]
Dec 27 16:48:00 ubard kernel: [    0.125733] pci 0000:00:05.0: reg 24 io port: [0x9800-0x987f]
Dec 27 16:48:00 ubard kernel: [    0.125749] pci 0000:00:05.0: PME# supported from D3cold
Dec 27 16:48:00 ubard kernel: [    0.125752] pci 0000:00:05.0: PME# disabled
Dec 27 16:48:00 ubard kernel: [    0.125788] pci 0000:00:06.0: PME# supported from D0 D3hot D3cold
Dec 27 16:48:00 ubard kernel: [    0.125792] pci 0000:00:06.0: PME# disabled
Dec 27 16:48:00 ubard kernel: [    0.125827] pci 0000:00:07.0: PME# supported from D0 D3hot D3cold
Dec 27 16:48:00 ubard kernel: [    0.125831] pci 0000:00:07.0: PME# disabled
Dec 27 16:48:00 ubard kernel: [    0.125855] pci 0000:00:09.0: reg 10 io port: [0x9400-0x947f]
Dec 27 16:48:00 ubard kernel: [    0.125860] pci 0000:00:09.0: reg 14 32bit mmio: [0xbbefb800-0xbbefb87f]
Dec 27 16:48:00 ubard kernel: [    0.125877] pci 0000:00:09.0: reg 30 32bit mmio: [0xbbec0000-0xbbedffff]
Dec 27 16:48:00 ubard kernel: [    0.125890] pci 0000:00:09.0: supports D1 D2
Dec 27 16:48:00 ubard kernel: [    0.125892] pci 0000:00:09.0: PME# supported from D0 D1 D2 D3cold
Dec 27 16:48:00 ubard kernel: [    0.125896] pci 0000:00:09.0: PME# disabled
Dec 27 16:48:00 ubard kernel: [    0.125997] pci 0000:01:00.0: reg 10 32bit mmio: [0xf0000000-0xf7ffffff]
Dec 27 16:48:00 ubard kernel: [    0.126001] pci 0000:01:00.0: reg 14 32bit mmio: [0xfbfe0000-0xfbffffff]
Dec 27 16:48:00 ubard kernel: [    0.126006] pci 0000:01:00.0: reg 18 io port: [0xc800-0xc87f]
Dec 27 16:48:00 ubard kernel: [    0.126021] pci 0000:01:00.0: supports D1 D2
Dec 27 16:48:00 ubard kernel: [    0.126042] pci 0000:00:01.0: bridge io port: [0xc000-0xcfff]
Dec 27 16:48:00 ubard kernel: [    0.126046] pci 0000:00:01.0: bridge 32bit mmio: [0xfbf00000-0xfbffffff]
Dec 27 16:48:00 ubard kernel: [    0.126050] pci 0000:00:01.0: bridge 32bit mmio pref: [0xf0000000-0xf7ffffff]
Dec 27 16:48:00 ubard kernel: [    0.126089] pci 0000:00:06.0: bridge io port: [0xd000-0xdfff]
Dec 27 16:48:00 ubard kernel: [    0.126132] pci 0000:00:07.0: bridge io port: [0xe000-0xefff]
Dec 27 16:48:00 ubard kernel: [    0.126150] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Dec 27 16:48:00 ubard kernel: [    0.126309] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
Dec 27 16:48:00 ubard kernel: [    0.126374] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P6._PRT]
Dec 27 16:48:00 ubard kernel: [    0.126424] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P7._PRT]
Dec 27 16:48:00 ubard kernel: [    0.134421] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 10 *11 12 14 15)
Dec 27 16:48:00 ubard kernel: [    0.134535] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 *10 11 12 14 15)
Dec 27 16:48:00 ubard kernel: [    0.134646] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
Dec 27 16:48:00 ubard kernel: [    0.134752] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 7 10 11 12 14 15)
Dec 27 16:48:00 ubard kernel: [    0.134859] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 10 *11 12 14 15)
Dec 27 16:48:00 ubard kernel: [    0.134966] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 *4 5 7 10 11 12 14 15)
Dec 27 16:48:00 ubard kernel: [    0.135072] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 *7 10 11 12 14 15)
Dec 27 16:48:00 ubard kernel: [    0.135179] ACPI: PCI Interrupt Link [LNKH] (IRQs *3 4 5 7 10 11 12 14 15)
Dec 27 16:48:00 ubard kernel: [    0.135384] SCSI subsystem initialized
Dec 27 16:48:00 ubard kernel: [    0.135466] libata version 3.00 loaded.
Dec 27 16:48:00 ubard kernel: [    0.135547] usbcore: registered new interface driver usbfs
Dec 27 16:48:00 ubard kernel: [    0.135566] usbcore: registered new interface driver hub
Dec 27 16:48:00 ubard kernel: [    0.135592] usbcore: registered new device driver usb
Dec 27 16:48:00 ubard kernel: [    0.135746] ACPI: WMI: Mapper loaded
Dec 27 16:48:00 ubard kernel: [    0.135748] PCI: Using ACPI for IRQ routing
Dec 27 16:48:00 ubard kernel: [    0.135763] pci 0000:00:00.0: BAR 0: address space collision on of device [0xf8000000-0xf9ffffff]
Dec 27 16:48:00 ubard kernel: [    0.135766] pci 0000:00:00.0: BAR 0: can't allocate resource
Dec 27 16:48:00 ubard kernel: [    0.135916] Bluetooth: Core ver 2.15
Dec 27 16:48:00 ubard kernel: [    0.135966] NET: Registered protocol family 31
Dec 27 16:48:00 ubard kernel: [    0.135968] Bluetooth: HCI device and connection manager initialized
Dec 27 16:48:00 ubard kernel: [    0.135972] Bluetooth: HCI socket layer initialized
Dec 27 16:48:00 ubard kernel: [    0.135974] NetLabel: Initializing
Dec 27 16:48:00 ubard kernel: [    0.135976] NetLabel:  domain hash size = 128
Dec 27 16:48:00 ubard kernel: [    0.135978] NetLabel:  protocols = UNLABELED CIPSOv4
Dec 27 16:48:00 ubard kernel: [    0.135992] NetLabel:  unlabeled traffic allowed by default
Dec 27 16:48:00 ubard kernel: [    0.136080] agpgart-amd64 0000:00:00.0: AGP bridge [1039/0760]
Dec 27 16:48:00 ubard kernel: [    0.137149] agpgart-amd64 0000:00:00.0: AGP aperture is 32M @ 0xf8000000
Dec 27 16:48:00 ubard kernel: [    0.138902] pnp: PnP ACPI init
Dec 27 16:48:00 ubard kernel: [    0.138925] ACPI: bus type pnp registered
Dec 27 16:48:00 ubard kernel: [    0.141211] pnp: PnP ACPI: found 7 devices
Dec 27 16:48:00 ubard kernel: [    0.141215] ACPI: ACPI bus type pnp unregistered
Dec 27 16:48:00 ubard kernel: [    0.141230] system 00:05: ioport range 0x290-0x297 has been reserved
Dec 27 16:48:00 ubard kernel: [    0.141236] system 00:06: ioport range 0x480-0x48f has been reserved
Dec 27 16:48:00 ubard kernel: [    0.141240] system 00:06: ioport range 0x4d0-0x4d1 has been reserved
Dec 27 16:48:00 ubard kernel: [    0.141243] system 00:06: ioport range 0x800-0x8cf has been reserved
Dec 27 16:48:00 ubard kernel: [    0.141246] system 00:06: ioport range 0x8d0-0x8ff has been reserved
Dec 27 16:48:00 ubard kernel: [    0.141251] system 00:06: iomem range 0xfff80000-0xffffffff has been reserved
Dec 27 16:48:00 ubard kernel: [    0.141254] system 00:06: iomem range 0xffee0000-0xffefffff has been reserved
Dec 27 16:48:00 ubard kernel: [    0.141258] system 00:06: iomem range 0xfee00400-0xfee00fff has been reserved
Dec 27 16:48:00 ubard kernel: [    0.145941] AppArmor: AppArmor Filesystem Enabled
Dec 27 16:48:00 ubard kernel: [    0.145978] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
Dec 27 16:48:00 ubard kernel: [    0.145981] pci 0000:00:01.0:   IO window: 0xc000-0xcfff
Dec 27 16:48:00 ubard kernel: [    0.145986] pci 0000:00:01.0:   MEM window: 0xfbf00000-0xfbffffff
Dec 27 16:48:00 ubard kernel: [    0.145990] pci 0000:00:01.0:   PREFETCH window: 0xf0000000-0xf7ffffff
Dec 27 16:48:00 ubard kernel: [    0.145995] pci 0000:00:06.0: PCI bridge, secondary bus 0000:02
Dec 27 16:48:00 ubard kernel: [    0.145998] pci 0000:00:06.0:   IO window: 0xd000-0xdfff
Dec 27 16:48:00 ubard kernel: [    0.146002] pci 0000:00:06.0:   MEM window: disabled
Dec 27 16:48:00 ubard kernel: [    0.146006] pci 0000:00:06.0:   PREFETCH window: disabled
Dec 27 16:48:00 ubard kernel: [    0.146010] pci 0000:00:07.0: PCI bridge, secondary bus 0000:03
Dec 27 16:48:00 ubard kernel: [    0.146013] pci 0000:00:07.0:   IO window: 0xe000-0xefff
Dec 27 16:48:00 ubard kernel: [    0.146017] pci 0000:00:07.0:   MEM window: disabled
Dec 27 16:48:00 ubard kernel: [    0.146020] pci 0000:00:07.0:   PREFETCH window: disabled
Dec 27 16:48:00 ubard kernel: [    0.146035] pci 0000:00:06.0: setting latency timer to 64
Dec 27 16:48:00 ubard kernel: [    0.146042] pci 0000:00:07.0: setting latency timer to 64
Dec 27 16:48:00 ubard kernel: [    0.146047] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
Dec 27 16:48:00 ubard kernel: [    0.146050] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffffffffffff]
Dec 27 16:48:00 ubard kernel: [    0.146053] pci_bus 0000:01: resource 0 io:  [0xc000-0xcfff]
Dec 27 16:48:00 ubard kernel: [    0.146056] pci_bus 0000:01: resource 1 mem: [0xfbf00000-0xfbffffff]
Dec 27 16:48:00 ubard kernel: [    0.146059] pci_bus 0000:01: resource 2 pref mem [0xf0000000-0xf7ffffff]
Dec 27 16:48:00 ubard kernel: [    0.146062] pci_bus 0000:02: resource 0 io:  [0xd000-0xdfff]
Dec 27 16:48:00 ubard kernel: [    0.146065] pci_bus 0000:03: resource 0 io:  [0xe000-0xefff]
Dec 27 16:48:00 ubard kernel: [    0.146109] NET: Registered protocol family 2
Dec 27 16:48:00 ubard kernel: [    0.146255] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
Dec 27 16:48:00 ubard kernel: [    0.147329] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
Dec 27 16:48:00 ubard kernel: [    0.150587] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
Dec 27 16:48:00 ubard kernel: [    0.151371] TCP: Hash tables configured (established 262144 bind 65536)
Dec 27 16:48:00 ubard kernel: [    0.151375] TCP reno registered
Dec 27 16:48:00 ubard kernel: [    0.151496] NET: Registered protocol family 1
Dec 27 16:48:00 ubard kernel: [    0.151565] Trying to unpack rootfs image as initramfs...
Dec 27 16:48:00 ubard kernel: [    0.354510] Freeing initrd memory: 7250k freed
Dec 27 16:48:00 ubard kernel: [    0.360490] Scanning for low memory corruption every 60 seconds
Dec 27 16:48:00 ubard kernel: [    0.360637] audit: initializing netlink socket (disabled)
Dec 27 16:48:00 ubard kernel: [    0.360653] type=2000 audit(1261928859.360:1): initialized
Dec 27 16:48:00 ubard kernel: [    0.371087] HugeTLB registered 2 MB page size, pre-allocated 0 pages
Dec 27 16:48:00 ubard kernel: [    0.372649] VFS: Disk quotas dquot_6.5.2
Dec 27 16:48:00 ubard kernel: [    0.372728] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
Dec 27 16:48:00 ubard kernel: [    0.373460] fuse init (API version 7.12)
Dec 27 16:48:00 ubard kernel: [    0.373570] msgmni has been set to 3953
Dec 27 16:48:00 ubard kernel: [    0.373839] alg: No test for stdrng (krng)
Dec 27 16:48:00 ubard kernel: [    0.373855] io scheduler noop registered
Dec 27 16:48:00 ubard kernel: [    0.373857] io scheduler anticipatory registered
Dec 27 16:48:00 ubard kernel: [    0.373860] io scheduler deadline registered (default)
Dec 27 16:48:00 ubard kernel: [    0.373934] io scheduler cfq registered
Dec 27 16:48:00 ubard kernel: [    0.450066] pci 0000:01:00.0: Boot video device
Dec 27 16:48:00 ubard kernel: [    0.450294] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Dec 27 16:48:00 ubard kernel: [    0.450318] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
Dec 27 16:48:00 ubard kernel: [    0.450443] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
Dec 27 16:48:00 ubard kernel: [    0.450447] ACPI: Power Button [PWRF]
Dec 27 16:48:00 ubard kernel: [    0.450500] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
Dec 27 16:48:00 ubard kernel: [    0.450503] ACPI: Power Button [PWRB]
Dec 27 16:48:00 ubard kernel: [    0.450886] processor LNXCPU:00: registered as cooling_device0
Dec 27 16:48:00 ubard kernel: [    0.455032] Linux agpgart interface v0.103
Dec 27 16:48:00 ubard kernel: [    0.455047] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
Dec 27 16:48:00 ubard kernel: [    0.456242] brd: module loaded
Dec 27 16:48:00 ubard kernel: [    0.456726] loop: module loaded
Dec 27 16:48:00 ubard kernel: [    0.456829] input: Macintosh mouse button emulation as /devices/virtual/input/input2
Dec 27 16:48:00 ubard kernel: [    0.457130] sata_sis 0000:00:05.0: version 1.0
Dec 27 16:48:00 ubard kernel: [    0.457145]   alloc irq_desc for 17 on node 0
Dec 27 16:48:00 ubard kernel: [    0.457147]   alloc kstat_irqs on node 0
Dec 27 16:48:00 ubard kernel: [    0.457156] sata_sis 0000:00:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Dec 27 16:48:00 ubard kernel: [    0.457161] sata_sis 0000:00:05.0: Detected SiS 182/965L chipset
Dec 27 16:48:00 ubard kernel: [    0.457265] scsi0 : sata_sis
Dec 27 16:48:00 ubard kernel: [    0.457392] scsi1 : sata_sis
Dec 27 16:48:00 ubard kernel: [    0.457432] ata1: SATA max UDMA/133 cmd 0xb400 ctl 0xb000 bmdma 0xa000 irq 17
Dec 27 16:48:00 ubard kernel: [    0.457437] ata2: SATA max UDMA/133 cmd 0xa800 ctl 0xa400 bmdma 0xa008 irq 17
Dec 27 16:48:00 ubard kernel: [    0.457943] pata_sis 0000:00:02.5: version 0.5.2
Dec 27 16:48:00 ubard kernel: [    0.458063] scsi2 : pata_sis
Dec 27 16:48:00 ubard kernel: [    0.458148] scsi3 : pata_sis
Dec 27 16:48:00 ubard kernel: [    0.458866] ata3: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
Dec 27 16:48:00 ubard kernel: [    0.458869] ata4: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
Dec 27 16:48:00 ubard kernel: [    0.459245] Fixed MDIO Bus: probed
Dec 27 16:48:00 ubard kernel: [    0.459282] PPP generic driver version 2.4.2
Dec 27 16:48:00 ubard kernel: [    0.459398] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
Dec 27 16:48:00 ubard kernel: [    0.459500]   alloc irq_desc for 23 on node 0
Dec 27 16:48:00 ubard kernel: [    0.459503]   alloc kstat_irqs on node 0
Dec 27 16:48:00 ubard kernel: [    0.459511] ehci_hcd 0000:00:03.3: PCI INT D -> GSI 23 (level, low) -> IRQ 23
Dec 27 16:48:00 ubard kernel: [    0.459531] ehci_hcd 0000:00:03.3: EHCI Host Controller
Dec 27 16:48:00 ubard kernel: [    0.459614] ehci_hcd 0000:00:03.3: new USB bus registered, assigned bus number 1
Dec 27 16:48:00 ubard kernel: [    0.459659] ehci_hcd 0000:00:03.3: cache line size of 64 is not supported
Dec 27 16:48:00 ubard kernel: [    0.459677] ehci_hcd 0000:00:03.3: irq 23, io mem 0xfbeff000
Dec 27 16:48:00 ubard kernel: [    0.470050] ehci_hcd 0000:00:03.3: USB 2.0 started, EHCI 1.00
Dec 27 16:48:00 ubard kernel: [    0.470160] usb usb1: configuration #1 chosen from 1 choice
Dec 27 16:48:00 ubard kernel: [    0.470193] hub 1-0:1.0: USB hub found
Dec 27 16:48:00 ubard kernel: [    0.470203] hub 1-0:1.0: 8 ports detected
Dec 27 16:48:00 ubard kernel: [    0.470308] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
Dec 27 16:48:00 ubard kernel: [    0.470373]   alloc irq_desc for 20 on node 0
Dec 27 16:48:00 ubard kernel: [    0.470376]   alloc kstat_irqs on node 0
Dec 27 16:48:00 ubard kernel: [    0.470384] ohci_hcd 0000:00:03.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
Dec 27 16:48:00 ubard kernel: [    0.470406] ohci_hcd 0000:00:03.0: OHCI Host Controller
Dec 27 16:48:00 ubard kernel: [    0.470465] ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus number 2
Dec 27 16:48:00 ubard kernel: [    0.470493] ohci_hcd 0000:00:03.0: irq 20, io mem 0xfbefc000
Dec 27 16:48:00 ubard kernel: [    0.532135] usb usb2: configuration #1 chosen from 1 choice
Dec 27 16:48:00 ubard kernel: [    0.532166] hub 2-0:1.0: USB hub found
Dec 27 16:48:00 ubard kernel: [    0.532178] hub 2-0:1.0: 3 ports detected
Dec 27 16:48:00 ubard kernel: [    0.532313]   alloc irq_desc for 21 on node 0
Dec 27 16:48:00 ubard kernel: [    0.532316]   alloc kstat_irqs on node 0
Dec 27 16:48:00 ubard kernel: [    0.532323] ohci_hcd 0000:00:03.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
Dec 27 16:48:00 ubard kernel: [    0.532342] ohci_hcd 0000:00:03.1: OHCI Host Controller
Dec 27 16:48:00 ubard kernel: [    0.532398] ohci_hcd 0000:00:03.1: new USB bus registered, assigned bus number 3
Dec 27 16:48:00 ubard kernel: [    0.532426] ohci_hcd 0000:00:03.1: irq 21, io mem 0xfbefd000
Dec 27 16:48:00 ubard kernel: [    0.592138] usb usb3: configuration #1 chosen from 1 choice
Dec 27 16:48:00 ubard kernel: [    0.592168] hub 3-0:1.0: USB hub found
Dec 27 16:48:00 ubard kernel: [    0.592179] hub 3-0:1.0: 3 ports detected
Dec 27 16:48:00 ubard kernel: [    0.592308]   alloc irq_desc for 22 on node 0
Dec 27 16:48:00 ubard kernel: [    0.592311]   alloc kstat_irqs on node 0
Dec 27 16:48:00 ubard kernel: [    0.592319] ohci_hcd 0000:00:03.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
Dec 27 16:48:00 ubard kernel: [    0.592338] ohci_hcd 0000:00:03.2: OHCI Host Controller
Dec 27 16:48:00 ubard kernel: [    0.592398] ohci_hcd 0000:00:03.2: new USB bus registered, assigned bus number 4
Dec 27 16:48:00 ubard kernel: [    0.592426] ohci_hcd 0000:00:03.2: irq 22, io mem 0xfbefe000
Dec 27 16:48:00 ubard kernel: [    0.630449] ata3.00: ATA-5: ST340016A, 3.05, max UDMA/100
Dec 27 16:48:00 ubard kernel: [    0.630452] ata3.00: 78165360 sectors, multi 16: LBA 
Dec 27 16:48:00 ubard kernel: [    0.652159] usb usb4: configuration #1 chosen from 1 choice
Dec 27 16:48:00 ubard kernel: [    0.652194] hub 4-0:1.0: USB hub found
Dec 27 16:48:00 ubard kernel: [    0.652205] hub 4-0:1.0: 2 ports detected
Dec 27 16:48:00 ubard kernel: [    0.652291] uhci_hcd: USB Universal Host Controller Interface driver
Dec 27 16:48:00 ubard kernel: [    0.652421] PNP: No PS/2 controller found. Probing ports directly.
Dec 27 16:48:00 ubard kernel: [    0.652670] serio: i8042 KBD port at 0x60,0x64 irq 1
Dec 27 16:48:00 ubard kernel: [    0.652679] serio: i8042 AUX port at 0x60,0x64 irq 12
Dec 27 16:48:00 ubard kernel: [    0.652748] mice: PS/2 mouse device common for all mice
Dec 27 16:48:00 ubard kernel: [    0.652837] rtc_cmos 00:02: RTC can wake from S4
Dec 27 16:48:00 ubard kernel: [    0.652878] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
Dec 27 16:48:00 ubard kernel: [    0.652899] rtc0: alarms up to one month, 114 bytes nvram
Dec 27 16:48:00 ubard kernel: [    0.653023] device-mapper: uevent: version 1.0.3
Dec 27 16:48:00 ubard kernel: [    0.653426] ata3.00: configured for UDMA/100
Dec 27 16:48:00 ubard kernel: [    0.653541] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
Dec 27 16:48:00 ubard kernel: [    0.653610] device-mapper: multipath: version 1.1.0 loaded
Dec 27 16:48:00 ubard kernel: [    0.653613] device-mapper: multipath round-robin: version 1.0.0 loaded
Dec 27 16:48:00 ubard kernel: [    0.653762] cpuidle: using governor ladder
Dec 27 16:48:00 ubard kernel: [    0.653765] cpuidle: using governor menu
Dec 27 16:48:00 ubard kernel: [    0.654291] TCP cubic registered
Dec 27 16:48:00 ubard kernel: [    0.654445] NET: Registered protocol family 10
Dec 27 16:48:00 ubard kernel: [    0.654934] lo: Disabled Privacy Extensions
Dec 27 16:48:00 ubard kernel: [    0.655254] NET: Registered protocol family 17
Dec 27 16:48:00 ubard kernel: [    0.655281] Bluetooth: L2CAP ver 2.13
Dec 27 16:48:00 ubard kernel: [    0.655283] Bluetooth: L2CAP socket layer initialized
Dec 27 16:48:00 ubard kernel: [    0.655286] Bluetooth: SCO (Voice Link) ver 0.6
Dec 27 16:48:00 ubard kernel: [    0.655288] Bluetooth: SCO socket layer initialized
Dec 27 16:48:00 ubard kernel: [    0.655349] Bluetooth: RFCOMM TTY layer initialized
Dec 27 16:48:00 ubard kernel: [    0.655352] Bluetooth: RFCOMM socket layer initialized
Dec 27 16:48:00 ubard kernel: [    0.655354] Bluetooth: RFCOMM ver 1.11
Dec 27 16:48:00 ubard kernel: [    0.655371] powernow-k8: Found 1 AMD Sempron(tm) Processor 3000+ processors (1 cpu cores) (version 2.20.00)
Dec 27 16:48:00 ubard kernel: [    0.655411] powernow-k8:    0 : fid 0xa (1800 MHz), vid 0x6
Dec 27 16:48:00 ubard kernel: [    0.655414] powernow-k8:    1 : fid 0x2 (1000 MHz), vid 0x12
Dec 27 16:48:00 ubard kernel: [    0.655663] PM: Resume from disk failed.
Dec 27 16:48:00 ubard kernel: [    0.655675] registered taskstats version 1
Dec 27 16:48:00 ubard kernel: [    0.655800]   Magic number: 5:892:791
Dec 27 16:48:00 ubard kernel: [    0.655865] rtc_cmos 00:02: setting system clock to 2009-12-27 15:47:40 UTC (1261928860)
Dec 27 16:48:00 ubard kernel: [    0.655869] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
Dec 27 16:48:00 ubard kernel: [    0.655871] EDD information not available.
Dec 27 16:48:00 ubard kernel: [    0.660077] Switched to high resolution mode on CPU 0
Dec 27 16:48:00 ubard kernel: [    0.790068] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
Dec 27 16:48:00 ubard kernel: [    0.811210] ata1.00: ATA-7: Maxtor 6V300F0, VA111630, max UDMA/133
Dec 27 16:48:00 ubard kernel: [    0.811214] ata1.00: 586114704 sectors, multi 16: LBA48 NCQ (depth 0/32)
Dec 27 16:48:00 ubard kernel: [    0.851219] ata1.00: configured for UDMA/133
Dec 27 16:48:00 ubard kernel: [    0.851322] scsi 0:0:0:0: Direct-Access     ATA      Maxtor 6V300F0   VA11 PQ: 0 ANSI: 5
Dec 27 16:48:00 ubard kernel: [    0.851477] sd 0:0:0:0: Attached scsi generic sg0 type 0
Dec 27 16:48:00 ubard kernel: [    0.851532] sd 0:0:0:0: [sda] 586114704 512-byte logical blocks: (300 GB/279 GiB)
Dec 27 16:48:00 ubard kernel: [    0.851579] sd 0:0:0:0: [sda] Write Protect is off
Dec 27 16:48:00 ubard kernel: [    0.851583] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
Dec 27 16:48:00 ubard kernel: [    0.851607] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Dec 27 16:48:00 ubard kernel: [    0.851740]  sda: sda1
Dec 27 16:48:00 ubard kernel: [    0.872752] sd 0:0:0:0: [sda] Attached SCSI disk
Dec 27 16:48:00 ubard kernel: [    1.020011] usb 4-2: new low speed USB device using ohci_hcd and address 2
Dec 27 16:48:00 ubard kernel: [    1.260191] usb 4-2: configuration #1 chosen from 1 choice
Dec 27 16:48:00 ubard kernel: [    3.090665] ata2: SATA link down (SStatus 1 SControl 300)
Dec 27 16:48:00 ubard kernel: [    3.090782] scsi 2:0:0:0: Direct-Access     ATA      ST340016A        3.05 PQ: 0 ANSI: 5
Dec 27 16:48:00 ubard kernel: [    3.090923] sd 2:0:0:0: Attached scsi generic sg1 type 0
Dec 27 16:48:00 ubard kernel: [    3.090972] sd 2:0:0:0: [sdb] 78165360 512-byte logical blocks: (40.0 GB/37.2 GiB)
Dec 27 16:48:00 ubard kernel: [    3.091017] sd 2:0:0:0: [sdb] Write Protect is off
Dec 27 16:48:00 ubard kernel: [    3.091020] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
Dec 27 16:48:00 ubard kernel: [    3.091043] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Dec 27 16:48:00 ubard kernel: [    3.091173]  sdb: sdb1 sdb2 < sdb5 >
Dec 27 16:48:00 ubard kernel: [    3.134838] sd 2:0:0:0: [sdb] Attached SCSI disk
Dec 27 16:48:00 ubard kernel: [    3.270249] ata4.00: ATAPI: _NEC DVD_RW ND-3500AG, 2.1A, max UDMA/33
Dec 27 16:48:00 ubard kernel: [    3.310261] ata4.00: configured for UDMA/33
Dec 27 16:48:00 ubard kernel: [    3.311261] scsi 3:0:0:0: CD-ROM            _NEC     DVD_RW ND-3500AG 2.1A PQ: 0 ANSI: 5
Dec 27 16:48:00 ubard kernel: [    3.313257] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
Dec 27 16:48:00 ubard kernel: [    3.313261] Uniform CD-ROM driver Revision: 3.20
Dec 27 16:48:00 ubard kernel: [    3.313365] sr 3:0:0:0: Attached scsi CD-ROM sr0
Dec 27 16:48:00 ubard kernel: [    3.313423] sr 3:0:0:0: Attached scsi generic sg2 type 5
Dec 27 16:48:00 ubard kernel: [    3.313459] Freeing unused kernel memory: 660k freed
Dec 27 16:48:00 ubard kernel: [    3.313941] Write protecting the kernel read-only data: 7572k
Dec 27 16:48:00 ubard kernel: [    3.611573]   alloc irq_desc for 16 on node 0
Dec 27 16:48:00 ubard kernel: [    3.611578]   alloc kstat_irqs on node 0
Dec 27 16:48:00 ubard kernel: [    3.611588] 3c59x 0000:00:09.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Dec 27 16:48:00 ubard kernel: [    3.611604] 3c59x: Donald Becker and others.
Dec 27 16:48:00 ubard kernel: [    3.611612] 0000:00:09.0: 3Com PCI 3c905C Tornado at ffffc900008b6800.
Dec 27 16:48:00 ubard kernel: [    3.723237] *** EEPROM MAC address is invalid.
Dec 27 16:48:00 ubard kernel: [    3.723243] 3c59x: vortex_probe1 fails.  Returns -22
Dec 27 16:48:00 ubard kernel: [    3.723249] 3c59x 0000:00:09.0: PCI INT A disabled
Dec 27 16:48:00 ubard kernel: [    3.723291] 3c59x: probe of 0000:00:09.0 failed with error -22
Dec 27 16:48:00 ubard kernel: [    3.818200] usbcore: registered new interface driver hiddev
Dec 27 16:48:00 ubard kernel: [    3.850949] input: Darfon USB Keyboard as /devices/pci0000:00/0000:00:03.2/usb4/4-2/4-2:1.0/input/input3
Dec 27 16:48:00 ubard kernel: [    3.851028] generic-usb 0003:0D62:0004.0001: input,hidraw0: USB HID v1.10 Keyboard [Darfon USB Keyboard] on usb-0000:00:03.2-2/input0
Dec 27 16:48:00 ubard kernel: [    3.880553] input: Darfon USB Keyboard as /devices/pci0000:00/0000:00:03.2/usb4/4-2/4-2:1.1/input/input4
Dec 27 16:48:00 ubard kernel: [    3.880664] generic-usb 0003:0D62:0004.0002: input,hiddev96,hidraw1: USB HID v1.10 Device [Darfon USB Keyboard] on usb-0000:00:03.2-2/input1
Dec 27 16:48:00 ubard kernel: [    3.880686] usbcore: registered new interface driver usbhid
Dec 27 16:48:00 ubard kernel: [    3.880689] usbhid: v2.6:USB HID core driver
Dec 27 16:48:00 ubard kernel: [    4.505786] PM: Starting manual resume from disk
Dec 27 16:48:00 ubard kernel: [    4.505792] PM: Resume from partition 252:1
Dec 27 16:48:00 ubard kernel: [    4.505794] PM: Checking hibernation image.
Dec 27 16:48:00 ubard kernel: [    4.506040] PM: Resume from disk failed.
Dec 27 16:48:00 ubard kernel: [    4.509969] EXT4-fs (dm-0): INFO: recovery required on readonly filesystem
Dec 27 16:48:00 ubard kernel: [    4.509976] EXT4-fs (dm-0): write access will be enabled during recovery
Dec 27 16:48:00 ubard kernel: [    4.539153] EXT4-fs (dm-0): barriers enabled
Dec 27 16:48:00 ubard kernel: [    5.859573] kjournald2 starting: pid 367, dev dm-0:8, commit interval 5 seconds
Dec 27 16:48:00 ubard kernel: [    5.859598] EXT4-fs (dm-0): delayed allocation enabled
Dec 27 16:48:00 ubard kernel: [    5.859601] EXT4-fs: file extents enabled
Dec 27 16:48:00 ubard kernel: [    5.860322] EXT4-fs: mballoc enabled
Dec 27 16:48:00 ubard kernel: [    5.860344] EXT4-fs (dm-0): orphan cleanup on readonly fs
Dec 27 16:48:00 ubard kernel: [    5.860358] EXT4-fs (dm-0): ext4_orphan_cleanup: deleting unreferenced inode 172751
Dec 27 16:48:00 ubard kernel: [    5.860632] EXT4-fs (dm-0): ext4_orphan_cleanup: deleting unreferenced inode 163297
Dec 27 16:48:00 ubard kernel: [    5.860643] EXT4-fs (dm-0): ext4_orphan_cleanup: deleting unreferenced inode 163288
Dec 27 16:48:00 ubard kernel: [    6.038362] EXT4-fs (dm-0): ext4_orphan_cleanup: deleting unreferenced inode 161381
Dec 27 16:48:00 ubard kernel: [    6.046772] EXT4-fs (dm-0): ext4_orphan_cleanup: deleting unreferenced inode 158710
Dec 27 16:48:00 ubard kernel: [    6.046790] EXT4-fs (dm-0): 5 orphan inodes deleted
Dec 27 16:48:00 ubard kernel: [    6.046794] EXT4-fs (dm-0): recovery complete
Dec 27 16:48:00 ubard kernel: [    6.102266] EXT4-fs (dm-0): mounted filesystem with ordered data mode
Dec 27 16:48:00 ubard kernel: [    6.807297] type=1505 audit(1261928866.644:2): operation="profile_load" pid=388 name=/bin/ping
Dec 27 16:48:00 ubard kernel: [    6.810713] type=1505 audit(1261928866.654:3): operation="profile_load" pid=389 name=/sbin/dhclient3
Dec 27 16:48:00 ubard kernel: [    6.811059] type=1505 audit(1261928866.654:4): operation="profile_load" pid=389 name=/usr/lib/NetworkManager/nm-dhcp-client.action
Dec 27 16:48:00 ubard kernel: [    6.811250] type=1505 audit(1261928866.654:5): operation="profile_load" pid=389 name=/usr/lib/connman/scripts/dhclient-script
Dec 27 16:48:00 ubard kernel: [    6.813729] type=1505 audit(1261928866.654:6): operation="profile_load" pid=390 name=/sbin/klogd
Dec 27 16:48:00 ubard kernel: [    6.826882] type=1505 audit(1261928866.664:7): operation="profile_load" pid=391 name=/sbin/syslog-ng
Dec 27 16:48:00 ubard kernel: [    6.829426] type=1505 audit(1261928866.664:8): operation="profile_load" pid=392 name=/sbin/syslogd
Dec 27 16:48:00 ubard kernel: [    6.832044] type=1505 audit(1261928866.674:9): operation="profile_load" pid=393 name=/usr/lib/dovecot/deliver
Dec 27 16:48:00 ubard kernel: [    6.834703] type=1505 audit(1261928866.674:10): operation="profile_load" pid=394 name=/usr/lib/dovecot/dovecot-auth
Dec 27 16:48:00 ubard kernel: [    6.837318] type=1505 audit(1261928866.674:11): operation="profile_load" pid=395 name=/usr/lib/dovecot/imap
Dec 27 16:48:00 ubard kernel: [    7.834892] Adding 1642488k swap on /dev/mapper/ubard-swap_1.  Priority:-1 extents:1 across:1642488k 
Dec 27 16:48:00 ubard kernel: [    8.666331] udev: starting version 147
Dec 27 16:48:00 ubard kernel: [   10.545711] sis190 Gigabit Ethernet driver 1.3 loaded.
Dec 27 16:48:00 ubard kernel: [   10.545732]   alloc irq_desc for 19 on node 0
Dec 27 16:48:00 ubard kernel: [   10.545734]   alloc kstat_irqs on node 0
Dec 27 16:48:00 ubard kernel: [   10.545744] sis190 0000:00:04.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Dec 27 16:48:00 ubard kernel: [   10.545754] sis190 0000:00:04.0: setting latency timer to 64
Dec 27 16:48:00 ubard kernel: [   10.545778] 0000:00:04.0: Read MAC address from EEPROM
Dec 27 16:48:00 ubard kernel: [   10.545781] 0000:00:04.0: Error EEPROM read 0.
Dec 27 16:48:00 ubard kernel: [   10.545783] 0000:00:04.0: Read MAC address from APC.
Dec 27 16:48:00 ubard kernel: [   10.660018] 0000:00:04.0: Realtek PHY RTL8201 transceiver at address 1.
Dec 27 16:48:00 ubard kernel: [   10.795644] EDAC MC: Ver: 2.1.0 Oct 16 2009
Dec 27 16:48:00 ubard kernel: [   10.894185] lp: driver loaded but no devices found
Dec 27 16:48:00 ubard kernel: [   10.911866] EDAC amd64_edac:  Ver: 3.2.0 Oct 16 2009
Dec 27 16:48:00 ubard kernel: [   11.081386] ip_tables: (C) 2000-2006 Netfilter Core Team
Dec 27 16:48:00 ubard kernel: [   11.900013] 0000:00:04.0: Using transceiver at address 1 as default.
Dec 27 16:48:00 ubard kernel: [   11.980746] 0000:00:04.0: SiS 190 PCI Fast Ethernet adapter at ffffc90000cbac00 (IRQ: 19), 00:13:d4:73:df:b5
Dec 27 16:48:00 ubard kernel: [   11.980751] eth0: GMII mode.
Dec 27 16:48:00 ubard kernel: [   11.980757] eth0: Enabling Auto-negotiation.
Dec 27 16:48:00 ubard kernel: [   12.062014] EDAC amd64: This node reports that Memory ECC is currently disabled.
Dec 27 16:48:00 ubard kernel: [   12.062019] EDAC amd64: bit 0x400000 in register F3x44 of the MISC_CONTROL device (0000:00:18.3) should be enabled
Dec 27 16:48:00 ubard kernel: [   12.062023] EDAC amd64: WARNING: ECC is NOT currently enabled by the BIOS. Module will NOT be loaded.
Dec 27 16:48:00 ubard rsyslogd-2039: Could no open output file '/dev/xconsole' [try http://www.rsyslog.com/e/2039 ]
Dec 27 16:48:00 ubard kernel: [   12.062025]     Either Enable ECC in the BIOS, or use the 'ecc_enable_override' parameter.
Dec 27 16:48:00 ubard kernel: [   12.062026]     Might be a BIOS bug, if BIOS says ECC is enabled
Dec 27 16:48:00 ubard kernel: [   12.062027]     Use of the override can cause unknown side effects.
Dec 27 16:48:00 ubard kernel: [   12.062041] amd64_edac: probe of 0000:00:18.2 failed with error -22
Dec 27 16:48:00 ubard kernel: [   12.064502] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Dec 27 16:48:00 ubard kernel: [   12.644602] ADDRCONF(NETDEV_UP): eth0: link is not ready
Dec 27 16:48:00 ubard kernel: [   12.720019] eth0: auto-negotiating...
Dec 27 16:48:00 ubard kernel: [   12.780017] eth0: auto-negotiating...
Dec 27 16:48:00 ubard kernel: [   13.720028] eth0: mii ext = 0000.
Dec 27 16:48:00 ubard kernel: [   13.780021] eth0: mii lpa=45e1 adv=01e1 exp=0001.
Dec 27 16:48:00 ubard kernel: [   13.780025] eth0: link on 100 Mbps Full Duplex mode.
Dec 27 16:48:00 ubard kernel: [   13.780385] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Dec 27 16:48:00 ubard kernel: [   17.035367] EXT4-fs (dm-0): internal journal on dm-0:8
Dec 27 16:48:00 ubard kernel: [   17.315823] kjournald starting.  Commit interval 5 seconds
Dec 27 16:48:00 ubard kernel: [   17.316096] EXT3 FS on sda1, internal journal
Dec 27 16:48:00 ubard kernel: [   17.316100] EXT3-fs: recovery complete.
Dec 27 16:48:00 ubard kernel: [   17.316225] EXT3-fs: mounted filesystem with writeback data mode.
Dec 27 16:48:00 ubard kernel: [   17.889300] __ratelimit: 51 callbacks suppressed
Dec 27 16:48:00 ubard kernel: [   17.889305] type=1505 audit(1261928880.861:29): operation="profile_replace" pid=874 name=/bin/ping
Dec 27 16:48:00 ubard kernel: [   17.891832] type=1505 audit(1261928880.871:30): operation="profile_replace" pid=875 name=/sbin/dhclient3
Dec 27 16:48:00 ubard kernel: [   17.892186] type=1505 audit(1261928880.871:31): operation="profile_replace" pid=875 name=/usr/lib/NetworkManager/nm-dhcp-client.action
Dec 27 16:48:00 ubard kernel: [   17.892383] type=1505 audit(1261928880.871:32): operation="profile_replace" pid=875 name=/usr/lib/connman/scripts/dhclient-script
Dec 27 16:48:00 ubard kernel: [   17.895992] type=1505 audit(1261928880.871:33): operation="profile_replace" pid=876 name=/sbin/klogd
Dec 27 16:48:00 ubard kernel: [   17.898278] type=1505 audit(1261928880.871:34): operation="profile_replace" pid=877 name=/sbin/syslog-ng
Dec 27 16:48:00 ubard kernel: [   17.900684] type=1505 audit(1261928880.881:35): operation="profile_replace" pid=878 name=/sbin/syslogd
Dec 27 16:48:00 ubard kernel: [   17.903891] type=1505 audit(1261928880.881:36): operation="profile_replace" pid=879 name=/usr/lib/dovecot/deliver
Dec 27 16:48:00 ubard kernel: [   17.906254] type=1505 audit(1261928880.881:37): operation="profile_replace" pid=880 name=/usr/lib/dovecot/dovecot-auth
Dec 27 16:48:00 ubard kernel: [   17.908633] type=1505 audit(1261928880.881:38): operation="profile_replace" pid=881 name=/usr/lib/dovecot/imap
Dec 27 16:48:01 ubard init: apport pre-start process (984) terminated with status 1
Dec 27 16:48:01 ubard init: apport post-stop process (1007) terminated with status 1
Dec 27 16:48:01 ubard cron[987]: (CRON) INFO (pidfile fd = 3)
Dec 27 16:48:01 ubard cron[1011]: (CRON) STARTUP (fork ok)
Dec 27 16:48:01 ubard cron[1011]: (CRON) INFO (Running @reboot jobs)
Dec 27 16:48:02 ubard named[1029]: starting BIND 9.6.1-P2 -u bind
Dec 27 16:48:02 ubard named[1029]: built with '--prefix=/usr' '--mandir=/usr/share/man' '--infodir=/usr/share/info' '--sysconfdir=/etc/bind' '--localstatedir=/var' '--enable-threads' '--enable-largefile' '--with-libtool' '--enable-shared' '--enable-static' '--with-openssl=/usr' '--with-gssapi=/usr' '--with-gnu-ld' '--with-dlz-postgres=no' '--with-dlz-mysql=no' '--with-dlz-bdb=yes' '--with-dlz-filesystem=yes' '--with-dlz-ldap=yes' '--with-dlz-stub=yes' '--with-geoip=/usr' '--enable-ipv6' 'CFLAGS=-fno-strict-aliasing -DDIG_SIGCHASE -O2' 'LDFLAGS=-Wl,-Bsymbolic-functions' 'CPPFLAGS=' 'CXXFLAGS=-g -O2' 'FFLAGS=-g -O2'
Dec 27 16:48:02 ubard named[1029]: adjusted limit on open files from 1024 to 1048576
Dec 27 16:48:02 ubard named[1029]: found 1 CPU, using 1 worker thread
Dec 27 16:48:02 ubard named[1029]: using up to 4096 sockets
Dec 27 16:48:02 ubard named[1029]: loading configuration from '/etc/bind/named.conf'
Dec 27 16:48:02 ubard named[1029]: using default UDP/IPv4 port range: [1024, 65535]
Dec 27 16:48:02 ubard named[1029]: using default UDP/IPv6 port range: [1024, 65535]
Dec 27 16:48:02 ubard named[1029]: listening on IPv6 interfaces, port 53
Dec 27 16:48:02 ubard named[1029]: listening on IPv4 interface lo, 127.0.0.1#53
Dec 27 16:48:02 ubard named[1029]: listening on IPv4 interface eth0, 192.168.0.50#53
Dec 27 16:48:02 ubard named[1029]: automatic empty zone: 254.169.IN-ADDR.ARPA
Dec 27 16:48:02 ubard named[1029]: automatic empty zone: 2.0.192.IN-ADDR.ARPA
Dec 27 16:48:02 ubard named[1029]: automatic empty zone: 255.255.255.255.IN-ADDR.ARPA
Dec 27 16:48:02 ubard named[1029]: automatic empty zone: 0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.IP6.ARPA
Dec 27 16:48:02 ubard named[1029]: automatic empty zone: 1.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.IP6.ARPA
Dec 27 16:48:02 ubard named[1029]: automatic empty zone: D.F.IP6.ARPA
Dec 27 16:48:02 ubard named[1029]: automatic empty zone: 8.E.F.IP6.ARPA
Dec 27 16:48:02 ubard named[1029]: automatic empty zone: 9.E.F.IP6.ARPA
Dec 27 16:48:02 ubard named[1029]: automatic empty zone: A.E.F.IP6.ARPA
Dec 27 16:48:02 ubard named[1029]: automatic empty zone: B.E.F.IP6.ARPA
Dec 27 16:48:02 ubard named[1029]: command channel listening on 127.0.0.1#953
Dec 27 16:48:02 ubard named[1029]: command channel listening on ::1#953
Dec 27 16:48:02 ubard named[1029]: zone 0.in-addr.arpa/IN: loaded serial 1
Dec 27 16:48:02 ubard named[1029]: zone 127.in-addr.arpa/IN: loaded serial 1
Dec 27 16:48:02 ubard named[1029]: zone 0.168.192.in-addr.arpa/IN: loaded serial 2009122401
Dec 27 16:48:02 ubard named[1029]: zone 255.in-addr.arpa/IN: loaded serial 1
Dec 27 16:48:02 ubard named[1029]: zone localhost/IN: loaded serial 2
Dec 27 16:48:02 ubard named[1029]: zone thebard.homedns.org/IN: loaded serial 2009122401
Dec 27 16:48:02 ubard named[1029]: running
Dec 27 16:48:02 ubard named[1029]: zone thebard.homedns.org/IN: sending notifies (serial 2009122401)
Dec 27 16:48:04 ubard /etc/mysql/debian-start[1273]: Upgrading MySQL tables if necessary.
Dec 27 16:48:04 ubard /etc/mysql/debian-start[1278]: Looking for 'mysql' as: /usr/bin/mysql
Dec 27 16:48:04 ubard /etc/mysql/debian-start[1278]: Looking for 'mysqlcheck' as: /usr/bin/mysqlcheck
Dec 27 16:48:04 ubard /etc/mysql/debian-start[1278]: This installation of MySQL is already upgraded to 5.1.37, use --force if you still need to run mysql_upgrade
Dec 27 16:48:04 ubard /etc/mysql/debian-start[1329]: Checking for insecure root accounts.
Dec 27 16:48:04 ubard /etc/mysql/debian-start[1333]: Triggering myisam-recover for all MyISAM tables
Dec 27 16:48:05 ubard kernel: [   22.860039] eth0: mii ext = 0000.
Dec 27 16:48:05 ubard kernel: [   22.923944] eth0: mii lpa=45e1 adv=01e1 exp=0001.
Dec 27 16:48:05 ubard kernel: [   22.923949] eth0: link on 100 Mbps Full Duplex mode.
Dec 27 16:48:05 ubard postfix/master[1403]: daemon started -- version 2.6.5, configuration /etc/postfix
Dec 27 16:48:07 ubard kernel: [   24.230016] eth0: no IPv6 routers present
Dec 27 16:49:10 ubard kernel: [   87.110110] Marking TSC unstable due to cpufreq changes
Dec 27 16:49:10 ubard kernel: [   87.640060] Clocksource tsc unstable (delta = -222232781 ns)
Dec 27 16:52:16 ubard ntpd[807]: synchronized to 91.189.94.4, stratum 2
Dec 27 16:52:16 ubard ntpd[807]: kernel time sync status change 2001

```

Result of `lspci` :
```

00:00.0 Host bridge: Silicon Integrated Systems [SiS] 760/M760 Host (rev 03)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SG86C202
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS965 [MuTIOL Media IO] (rev 48)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] 190 Ethernet Adapter
00:05.0 IDE interface: Silicon Integrated Systems [SiS] 182 SATA/RAID Controller (rev 01)
00:06.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:07.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:09.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 74)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter

```

Thanks,

---

### Post by WTF_Shelley on 2009-12-27
Im no l33t server admin but have you got the logs upto and including the moment of the crash, the logs you have provided (nice hardware btw ;)) only seem to show a machine booting up after the crash, not during.

If you could post them it might show file errors or kernel panics etc.

---

### Post by the_bard on 2009-12-27
Hi,

Thanks for your reply, but i don´t know what are the logs you mean.

In the posted logs i leave the last line after the last crash (Dec 26) (well, now Dec 27, while I was writing the post).

Anyway this is the contents between crashes of syslog, it only shows the cron logs, no Kernel panics, no other error... its frustrating

Contents of /var/log/syslog :
```

Dec 27 16:48:04 ubard /etc/mysql/debian-start[1273]: Upgrading MySQL tables if necessary.
Dec 27 16:48:04 ubard /etc/mysql/debian-start[1278]: Looking for 'mysql' as: /usr/bin/mysql
Dec 27 16:48:04 ubard /etc/mysql/debian-start[1278]: Looking for 'mysqlcheck' as: /usr/bin/mysqlcheck
Dec 27 16:48:04 ubard /etc/mysql/debian-start[1278]: This installation of MySQL is already upgraded to 5.1.37, use --force if you still need to run mysql_upgrade
Dec 27 16:48:04 ubard /etc/mysql/debian-start[1329]: Checking for insecure root accounts.
Dec 27 16:48:04 ubard /etc/mysql/debian-start[1333]: Triggering myisam-recover for all MyISAM tables
Dec 27 16:48:05 ubard kernel: [   22.860039] eth0: mii ext = 0000.
Dec 27 16:48:05 ubard kernel: [   22.923944] eth0: mii lpa=45e1 adv=01e1 exp=0001.
Dec 27 16:48:05 ubard kernel: [   22.923949] eth0: link on 100 Mbps Full Duplex mode.
Dec 27 16:48:05 ubard postfix/master[1403]: daemon started -- version 2.6.5, configuration /etc/postfix
Dec 27 16:48:07 ubard kernel: [   24.230016] eth0: no IPv6 routers present
Dec 27 16:49:10 ubard kernel: [   87.110110] Marking TSC unstable due to cpufreq changes
Dec 27 16:49:10 ubard kernel: [   87.640060] Clocksource tsc unstable (delta = -222232781 ns)
Dec 27 16:52:16 ubard ntpd[807]: synchronized to 91.189.94.4, stratum 2
Dec 27 16:52:16 ubard ntpd[807]: kernel time sync status change 2001
Dec 27 17:09:01 ubard CRON[1556]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -n 200 -r -0 rm)
Dec 27 17:17:01 ubard CRON[1667]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Dec 27 18:37:34 ubard kernel: imklog 4.2.0, log source = /var/run/rsyslog/kmsg started.
Dec 27 18:37:34 ubard rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="840" x-info="http://www.rsyslog.com"] (re)start
Dec 27 18:37:34 ubard rsyslogd: rsyslogd's groupid changed to 103
Dec 27 18:37:34 ubard rsyslogd: rsyslogd's userid changed to 101

```

Thanks,

pd. Tell me witch log may I post for getting help on finding the possible crash cause.

---

### Post by WTF_Shelley on 2009-12-27
sorry, i didn't mean to come off like a dick in my last post opps.

the log that might best show errors is /var/log/kern.log there should be only one but if theres more (if your box has been running for a while the latest one by date is the one you need.  Start at the end and scroll up until the timer in the square brackets hits [0.00000] and jumps to a high number, this is where the machine crashed and reset itself.  Look just above the [0.0000] and see if theres any hardware or software errors.

---

