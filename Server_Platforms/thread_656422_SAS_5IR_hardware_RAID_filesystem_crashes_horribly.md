---
title: "SAS 5IR hardware RAID: filesystem crashes horribly"
date: 2008-01-02
forum: Server Platforms
---

### Post by NewKindaArt on 2008-01-02
Hi,

I have Ubuntu 7.04 on a Dell PowerEdge 1430 with a SAS 5iR hardware RAID adapter.  I have 2x 250 GB SATA drives in a RAID 1 array.  ext3 filesystem.

After a couple of months of uptime, something weird happened to the file system.  Many files couldn't be opened or written, although most directories could still be listed.  (I only noticed because some images were not showing up on the served web pages... 90% of the pages were fine.  I'm guessing apache had all the HTML cached in memory).

I think that the problem got progressively worse over time (ie more and more files became inaccessible), but I can't back that up.

Worst of all, when I finally decided to do something about it, I found that all the files in /sbin were inaccessible.  That meant I couldn't do anything requiring a 'sudo'!  Not even a 'sudo shutdown -Fr'.  I had to do a hard reboot, which was inconvenient  (the machine is in a locked room, I have to find somebody to let me in, etc).

After rebooting the machine, I ran fsck, but it seemed to come up clean.

I got this server 4 months ago, and it's happened twice.  (On December 25th, too!  Extra inconvenient because the people with the key to the room were on vacation until Jan 2...)

Questions:
1) Is this a problem with the hard drives?  fsck coming up clean would seem to suggest that it isn't.
2) Is this a known problem?  Can I solve it by making the machine auto-reboot every week or something?
3) Is there any way to safeguard against losing all the important stuff in /sbin?  maybe a copy of /sbin in a ramdisk or something?

Some relevant log files are attached.  Please let me know if there's any more info that would be helpful.

Thanks!

/var/log/fsck/checkfs:
Log of fsck -C -R -A -a
Wed Jan  2 10:31:45 2008

fsck 1.40-WIP (14-Nov-2006)

Wed Jan  2 10:31:45 2008
----------------


a chunk of /var/log/kern.log:
Dec 26 07:12:49 lagrange kernel: [248610.406229] mptscsih: ioc0: attempting task abort! (sc=ffff81001b1e6080)
Dec 26 07:12:49 lagrange kernel: [248610.406240] sd 4:1:0:0:
Dec 26 07:12:49 lagrange kernel: [248610.406247]         command: Write(10): 2a 00 0a 1a 21 8f 00 00 08 00
Dec 26 07:12:50 lagrange kernel: [248610.526163] mptscsih: ioc0: task abort: FAILED (sc=ffff81001b1e6080)
Dec 26 07:12:50 lagrange kernel: [248610.526175] mptscsih: ioc0: attempting task abort! (sc=ffff81001b1e6280)
Dec 26 07:12:50 lagrange kernel: [248610.526183] sd 4:1:0:0:
Dec 26 07:12:50 lagrange kernel: [248610.526187]         command: Write(10): 2a 00 0a 1a 1e af 00 00 08 00
Dec 26 07:12:50 lagrange kernel: [248610.646105] mptscsih: ioc0: task abort: FAILED (sc=ffff81001b1e6280)
Dec 26 07:12:50 lagrange kernel: [248610.646115] mptscsih: ioc0: attempting task abort! (sc=ffff81001b1e6480)
Dec 26 07:12:50 lagrange kernel: [248610.646125] sd 4:1:0:0:
Dec 26 07:12:50 lagrange kernel: [248610.646128]         command: Write(10): 2a 00 0a 19 ad f7 00 00 08 00
Dec 26 07:12:50 lagrange kernel: [248610.766044] mptscsih: ioc0: task abort: FAILED (sc=ffff81001b1e6480)
Dec 26 07:12:50 lagrange kernel: [248610.766054] mptscsih: ioc0: attempting task abort! (sc=ffff81001b1e6680)
Dec 26 07:12:50 lagrange kernel: [248610.766063] sd 4:1:0:0:
Dec 26 07:12:50 lagrange kernel: [248610.766066]         command: Write(10): 2a 00 0a 19 a5 ff 00 00 08 00
Dec 26 07:12:50 lagrange kernel: [248610.885985] mptscsih: ioc0: task abort: FAILED (sc=ffff81001b1e6680)

---

### Post by NewKindaArt on 2008-01-02
In case it helps, here's /var/log/dmesg:

```
[    0.000000] Linux version 2.6.20-15-generic (root@yellow) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Apr 15 06:17:24 UTC 2007 (Ubuntu 2.6.20-15.27-generic)
[    0.000000] Command line: root=UUID=09327215-c569-4302-b5ac-a1a6a1b4ede1 ro quiet splash
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 00000000000a0000 (usable)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000dffa8000 (usable)
[    0.000000]  BIOS-e820: 00000000dffa8000 - 00000000dffb7c00 (ACPI data)
[    0.000000]  BIOS-e820: 00000000dffb7c00 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fe000000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100000000 - 0000000120000000 (usable)
[    0.000000] Entering add_active_range(0, 0, 160) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 917416) 1 entries of 3200 used
[    0.000000] Entering add_active_range(0, 1048576, 1179648) 2 entries of 3200 used
[    0.000000] end_pfn_map = 1179648
[    0.000000] DMI 2.4 present.
[    0.000000] ACPI: RSDP (v002 DELL                                  ) @ 0x00000000000f2820
[    0.000000] ACPI: XSDT (v001 DELL   PE_SC3   0x00000001 DELL 0x00000001) @ 0x00000000000f289c
[    0.000000] ACPI: FADT (v003 DELL   PE_SC3   0x00000001 DELL 0x00000001) @ 0x00000000000f299c
[    0.000000] ACPI: MADT (v001 DELL   PE_SC3   0x00000001 DELL 0x00000001) @ 0x00000000000f2a90
[    0.000000] ACPI: HPET (v001 DELL   PE_SC3   0x00000001 DELL 0x00000001) @ 0x00000000000f2b59
[    0.000000] ACPI: MCFG (v001 DELL   PE_SC3   0x00000001 DELL 0x00000001) @ 0x00000000000f2b91
[    0.000000] ACPI: DSDT (v001 DELL   PE_SC3   0x00000001 MSFT 0x0100000e) @ 0x0000000000000000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-0000000120000000
[    0.000000] Entering add_active_range(0, 0, 160) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 917416) 1 entries of 3200 used
[    0.000000] Entering add_active_range(0, 1048576, 1179648) 2 entries of 3200 used
[    0.000000] Bootmem setup node 0 0000000000000000-0000000120000000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   DMA32        4096 ->  1048576
[    0.000000]   Normal    1048576 ->  1179648
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0:        0 ->      160
[    0.000000]     0:      256 ->   917416
[    0.000000]     0:  1048576 ->  1179648
[    0.000000] On node 0 totalpages: 1048392
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 1089 pages reserved
[    0.000000]   DMA zone: 2855 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 899040 pages, LIFO batch:31
[    0.000000]   Normal zone: 1792 pages used for memmap
[    0.000000]   Normal zone: 129280 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 (Bootup-CPU)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] enabled)
[    0.000000] Processor #2
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x01] enabled)
[    0.000000] Processor #1
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
[    0.000000] Processor #3
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x14] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x15] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x16] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x17] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x04] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x05] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x06] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x07] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x08] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: IOAPIC (id[0x05] address[0xfec80000] gsi_base[32])
[    0.000000] IOAPIC[1]: apic_id 5, address 0xfec80000, GSI 32-55
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Setting APIC routing to physical flat
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Nosave address range: 00000000000a0000 - 0000000000100000
[    0.000000] Nosave address range: 00000000dffa8000 - 00000000dffb7000
[    0.000000] Nosave address range: 00000000dffb7000 - 00000000dffb8000
[    0.000000] Nosave address range: 00000000dffb8000 - 00000000f0000000
[    0.000000] Nosave address range: 00000000f0000000 - 00000000fe000000
[    0.000000] Nosave address range: 00000000fe000000 - 0000000100000000
[    0.000000] Allocating PCI resources starting at f1000000 (gap: f0000000:e000000)
[    0.000000] SMP: Allowing 8 CPUs, 4 hotplug CPUs
[    0.000000] PERCPU: Allocating 34048 bytes of per cpu data
[    0.000000] Built 1 zonelists.  Total pages: 1031175
[    0.000000] Kernel command line: root=UUID=09327215-c569-4302-b5ac-a1a6a1b4ede1 ro quiet splash
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[   45.115312] Console: colour VGA+ 80x25
[   45.117608] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[   45.121067] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[   45.121474] Checking aperture...
[   45.121488] Calgary: detecting Calgary via BIOS EBDA area
[   45.121491] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[   45.121494] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[   45.159141] Placing software IO TLB between 0x166a000 - 0x566a000
[   45.196317] Memory: 4045568k/4718592k available (2217k kernel code, 148000k reserved, 1162k data, 304k init)
[   45.275494] Calibrating delay using timer specific routine.. 5991.57 BogoMIPS (lpj=11983149)
[   45.275561] Security Framework v1.0.0 initialized
[   45.275567] SELinux:  Disabled at boot.
[   45.275598] Mount-cache hash table entries: 256
[   45.275772] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   45.275775] CPU: L2 cache: 2048K
[   45.275779] CPU 0/0 -> Node 0
[   45.275780] using mwait in idle threads.
[   45.275782] CPU: Physical Processor ID: 0
[   45.275784] CPU: Processor Core ID: 0
[   45.275795] CPU0: Thermal monitoring enabled (TM1)
[   45.275808] SMP alternatives: switching to UP code
[   45.276137] Early unpacking initramfs... done
[   45.554793] ACPI: Core revision 20060707
[   45.558469] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   45.600127] Using local APIC timer interrupts.
[   45.633529] result 10390538
[   45.633531] Detected 10.390 MHz APIC timer.
[   45.635551] SMP alternatives: switching to SMP code
[   45.635705] Booting processor 1/4 APIC 0x2
[   45.646440] Initializing CPU#1
[   45.723244] Calibrating delay using timer specific routine.. 5985.29 BogoMIPS (lpj=11970595)
[   45.723256] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   45.723258] CPU: L2 cache: 2048K
[   45.723261] CPU 1/2 -> Node 0
[   45.723263] CPU: Physical Processor ID: 0
[   45.723265] CPU: Processor Core ID: 1
[   45.723275] CPU1: Thermal monitoring enabled (TM1)
[   45.723647]                   Intel(R) Xeon(TM) CPU 3.00GHz stepping 04
[   45.727479] SMP alternatives: switching to SMP code
[   45.727512] Booting processor 2/4 APIC 0x1
[   45.738190] Initializing CPU#2
[   45.815194] Calibrating delay using timer specific routine.. 5985.29 BogoMIPS (lpj=11970586)
[   45.815209] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   45.815211] CPU: L2 cache: 2048K
[   45.815215] CPU 2/1 -> Node 0
[   45.815217] CPU: Physical Processor ID: 0
[   45.815219] CPU: Processor Core ID: 0
[   45.815231] CPU2: Thermal monitoring enabled (TM1)
[   45.815607]                   Intel(R) Xeon(TM) CPU 3.00GHz stepping 04
[   45.819463] SMP alternatives: switching to SMP code
[   45.819610] Booting processor 3/4 APIC 0x3
[   45.830351] Initializing CPU#3
[   45.907144] Calibrating delay using timer specific routine.. 5985.16 BogoMIPS (lpj=11970325)
[   45.907157] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   45.907159] CPU: L2 cache: 2048K
[   45.907162] CPU 3/3 -> Node 0
[   45.907164] CPU: Physical Processor ID: 0
[   45.907165] CPU: Processor Core ID: 1
[   45.907175] CPU3: Thermal monitoring enabled (TM1)
[   45.907558]                   Intel(R) Xeon(TM) CPU 3.00GHz stepping 04
[   45.911160] Brought up 4 CPUs
[   45.911213] time.c: Using 14.318180 MHz WALL HPET GTOD HPET/TSC timer.
[   45.911215] time.c: Detected 2992.496 MHz processor.
[   46.274205] migration_cost=5,1027
[   46.274643] Time: 18:31:31  Date: 00/02/108
[   46.274695] NET: Registered protocol family 16
[   46.274796] ACPI: bus type pci registered
[   46.274804] PCI: Using configuration type 1
[   46.280190] ACPI: Interpreter enabled
[   46.280193] ACPI: Using IOAPIC for interrupt routing
[   46.281384] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   46.281390] PCI: Probing PCI hardware (bus 00)
[   46.289817] PCI: PXH quirk detected, disabling MSI for SHPC device
[   46.303809] Boot video device is 0000:09:09.0
[   46.303842] PCI: Transparent bridge - 0000:00:1e.0
[   46.303906] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   46.308013] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX2._PRT]
[   46.308393] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX2.UPST._PRT]
[   46.308667] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX2.UPST.DWN1._PRT]
[   46.309016] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX2.PE2X._PRT]
[   46.309478] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEX3._PRT]
[   46.309809] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.SBEX._PRT]
[   46.310107] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.COMP._PRT]
[   46.313768] ACPI: PCI Interrupt Link [LK00] (IRQs 3 4 *5 6 7 10 11 12)
[   46.314095] ACPI: PCI Interrupt Link [LK01] (IRQs *3 4 5 6 7 10 11 12)
[   46.314421] ACPI: PCI Interrupt Link [LK02] (IRQs 3 4 5 6 7 10 11 12) *0, disabled.
[   46.314750] ACPI: PCI Interrupt Link [LK03] (IRQs 3 4 5 6 7 10 11 12) *0, disabled.
[   46.315077] ACPI: PCI Interrupt Link [LK04] (IRQs 3 4 5 6 7 *10 11 12)
[   46.315399] ACPI: PCI Interrupt Link [LK05] (IRQs 3 4 5 6 7 10 *11 12)
[   46.315724] ACPI: PCI Interrupt Link [LK06] (IRQs 3 4 5 6 7 10 11 12) *0, disabled.
[   46.316051] ACPI: PCI Interrupt Link [LK07] (IRQs 3 4 5 *6 7 10 11 12)
[   46.316189] Linux Plug and Play Support v0.97 (c) Adam Belay
[   46.316211] pnp: PnP ACPI init
[   46.321658] pnp: PnP ACPI: found 11 devices
[   46.321722] PCI: Using ACPI for IRQ routing
[   46.321725] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   46.322295] NET: Registered protocol family 8
[   46.322298] NET: Registered protocol family 20
[   46.322312] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   46.322318] hpet0: 3 64-bit timers, 14318180 Hz
[   46.323339] PCI-GART: No AMD northbridge found.
[   46.324780] pnp: 00:08: ioport range 0x800-0x87f could not be reserved
[   46.324784] pnp: 00:08: ioport range 0x880-0x8bf has been reserved
[   46.324786] pnp: 00:08: ioport range 0x8c0-0x8df has been reserved
[   46.324789] pnp: 00:08: ioport range 0x8e0-0x8e3 has been reserved
[   46.324792] pnp: 00:08: ioport range 0xc00-0xc7f has been reserved
[   46.325844] PCI: Bridge: 0000:04:00.0
[   46.325877]   IO window: e000-efff
[   46.326015]   MEM window: fdb00000-fdcfffff
[   46.326106]   PREFETCH window: disabled.
[   46.326244] PCI: Bridge: 0000:03:00.0
[   46.326290]   IO window: e000-efff
[   46.326427]   MEM window: fdb00000-fdcfffff
[   46.326519]   PREFETCH window: disabled.
[   46.326656] PCI: Bridge: 0000:03:01.0
[   46.326658]   IO window: disabled.
[   46.326794]   MEM window: disabled.
[   46.326886]   PREFETCH window: disabled.
[   46.327024] PCI: Bridge: 0000:02:00.0
[   46.327070]   IO window: e000-efff
[   46.327208]   MEM window: fdb00000-fdcfffff
[   46.327299]   PREFETCH window: disabled.
[   46.327437] PCI: Bridge: 0000:02:00.3
[   46.327438]   IO window: disabled.
[   46.327574]   MEM window: disabled.
[   46.327666]   PREFETCH window: disabled.
[   46.327804] PCI: Bridge: 0000:00:02.0
[   46.327806]   IO window: e000-efff
[   46.327811]   MEM window: fd900000-fdcfffff
[   46.327814]   PREFETCH window: disabled.
[   46.327818] PCI: Bridge: 0000:00:03.0
[   46.327819]   IO window: disabled.
[   46.327823]   MEM window: disabled.
[   46.327826]   PREFETCH window: disabled.
[   46.327830] PCI: Bridge: 0000:00:1c.0
[   46.327831]   IO window: disabled.
[   46.327836]   MEM window: fdd00000-fdefffff
[   46.327840]   PREFETCH window: disabled.
[   46.327847] PCI: Bridge: 0000:00:1e.0
[   46.327850]   IO window: d000-dfff
[   46.327855]   MEM window: fd700000-fd8fffff
[   46.327859]   PREFETCH window: f0000000-f7ffffff
[   46.327877] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
[   46.327883] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   46.328264] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   46.328355] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   46.328905] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   46.328997] PCI: Setting latency timer of device 0000:03:00.0 to 64
[   46.329640] PCI: Setting latency timer of device 0000:04:00.0 to 64
[   46.330191] ACPI: PCI Interrupt 0000:03:01.0[A] -> GSI 16 (level, low) -> IRQ 16
[   46.330282] PCI: Setting latency timer of device 0000:03:01.0 to 64
[   46.330833] PCI: Setting latency timer of device 0000:02:00.3 to 64
[   46.330884] ACPI: PCI Interrupt 0000:00:03.0[A] -> GSI 16 (level, low) -> IRQ 16
[   46.330889] PCI: Setting latency timer of device 0000:00:03.0 to 64
[   46.330906] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
[   46.330915] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   46.330926] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   46.330983] NET: Registered protocol family 2
[   46.369261] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[   46.369717] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[   46.371835] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   46.372416] TCP: Hash tables configured (established 262144 bind 65536)
[   46.372420] TCP reno registered
[   46.385399] checking if image is initramfs... it is
[   46.926787] Freeing initrd memory: 6590k freed
[   46.932141] audit: initializing netlink socket (disabled)
[   46.932159] audit(1199298691.796:1): initialized
[   46.932600] VFS: Disk quotas dquot_6.5.1
[   46.932642] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   46.932741] io scheduler noop registered
[   46.932744] io scheduler anticipatory registered
[   46.932746] io scheduler deadline registered
[   46.932783] io scheduler cfq registered (default)
[   46.933125] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   46.933161] assign_interrupt_mode Found MSI capability
[   46.933166] Allocate Port Service[0000:00:02.0:pcie00]
[   46.933270] PCI: Setting latency timer of device 0000:00:03.0 to 64
[   46.933306] assign_interrupt_mode Found MSI capability
[   46.933309] Allocate Port Service[0000:00:03.0:pcie00]
[   46.933409] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   46.933453] assign_interrupt_mode Found MSI capability
[   46.933457] Allocate Port Service[0000:00:1c.0:pcie00]
[   46.933798] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   46.935358] Allocate Port Service[0000:02:00.0:pcie10]
[   46.938203] PCI: Setting latency timer of device 0000:03:00.0 to 64
[   46.939858] assign_interrupt_mode Found MSI capability
[   46.939862] Allocate Port Service[0000:03:00.0:pcie20]
[   46.942654] PCI: Setting latency timer of device 0000:03:01.0 to 64
[   46.944260] assign_interrupt_mode Found MSI capability
[   46.944263] Allocate Port Service[0000:03:01.0:pcie20]
[   46.977823] Real Time Clock Driver v1.12ac
[   46.978008] hpet_resources: 0xfed00000 is busy
[   46.978030] Linux agpgart interface v0.102 (c) Dave Jones
[   46.978033] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   46.978174] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   46.978825] 00:05: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   46.979068] mice: PS/2 mouse device common for all mice
[   46.979848] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   46.980022] input: Macintosh mouse button emulation as /class/input/input0
[   46.980068] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   46.980074] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   46.980399] PNP: No PS/2 controller found. Probing ports directly.
[   46.982904] serio: i8042 KBD port at 0x60,0x64 irq 1
[   46.982911] serio: i8042 AUX port at 0x60,0x64 irq 12
[   46.983045] TCP cubic registered
[   46.983060] NET: Registered protocol family 1
[   46.983197] ACPI: (supports S0 S4 S5)
[   46.983240]   Magic number: 8:504:543
[   46.983432] drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   46.983505] Freeing unused kernel memory: 304k freed
[   47.135231] Capability LSM initialized
[   47.178126] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[   47.178136] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[   47.178144] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[   47.178151] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[   47.653436] usbcore: registered new interface driver usbfs
[   47.653493] usbcore: registered new interface driver hub
[   47.654039] usbcore: registered new device driver usb
[   47.662577] SCSI subsystem initialized
[   47.696021] libata version 2.20 loaded.
[   47.696130] USB Universal Host Controller Interface driver v3.0
[   47.696254] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 21 (level, low) -> IRQ 21
[   47.696271] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   47.696277] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   47.696430] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   47.696464] uhci_hcd 0000:00:1d.0: irq 21, io base 0x0000cce0
[   47.696676] usb usb1: configuration #1 chosen from 1 choice
[   47.696728] hub 1-0:1.0: USB hub found
[   47.696741] hub 1-0:1.0: 2 ports detected
[   47.734382] Fusion MPT base driver 3.04.03
[   47.734386] Copyright (c) 1999-2007 LSI Logic Corporation
[   47.738506] Fusion MPT SAS Host driver 3.04.03
[   47.801218] tg3.c:v3.72 (January 8, 2007)
[   47.801226] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 20 (level, low) -> IRQ 20
[   47.801241] ACPI: PCI Interrupt 0000:01:00.0[A] -> <7>PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   47.801251] GSI 16 (level, low) -> IRQ 16
[   47.801255] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   47.801268] PCI: Setting latency timer of device 0000:01:00.0 to 64
[   47.801492] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   47.801523] uhci_hcd 0000:00:1d.1: irq 20, io base 0x0000ccc0
[   47.802156] usb usb2: configuration #1 chosen from 1 choice
[   47.802389] hub 2-0:1.0: USB hub found
[   47.802397] hub 2-0:1.0: 2 ports detected
[   47.820792] eth0: Tigon3 [partno(BCM95751) rev 4201 PHY(5750)] (PCI Express) 10/100/1000Base-T Ethernet 00:19:b9:19:c8:c6
[   47.820804] eth0: RXcsums[1] LinkChgREG[1] MIirq[1] ASF[0] Split[0] WireSpeed[1] TSOcap[1] 
[   47.820809] eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[   47.908615] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 21 (level, low) -> IRQ 21
[   47.908627] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   47.908631] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   47.908655] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   47.908681] uhci_hcd 0000:00:1d.2: irq 21, io base 0x0000cca0
[   47.908786] usb usb3: configuration #1 chosen from 1 choice
[   47.908816] hub 3-0:1.0: USB hub found
[   47.908823] hub 3-0:1.0: 2 ports detected
[   48.012561] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 20 (level, low) -> IRQ 20
[   48.012572] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   48.012575] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   48.012599] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[   48.012624] uhci_hcd 0000:00:1d.3: irq 20, io base 0x0000cc80
[   48.012725] usb usb4: configuration #1 chosen from 1 choice
[   48.012757] hub 4-0:1.0: USB hub found
[   48.012764] hub 4-0:1.0: 2 ports detected
[   48.040418] usb 1-1: new low speed USB device using uhci_hcd and address 2
[   48.116731] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 21 (level, low) -> IRQ 21
[   48.116757] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   48.116763] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   48.116809] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[   48.116868] ehci_hcd 0000:00:1d.7: debug port 1
[   48.116878] PCI: cache line size of 128 is not supported by device 0000:00:1d.7
[   48.116891] ehci_hcd 0000:00:1d.7: irq 21, io mem 0xfdf00400
[   48.120795] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   48.120932] usb usb5: configuration #1 chosen from 1 choice
[   48.120971] hub 5-0:1.0: USB hub found
[   48.120982] hub 5-0:1.0: 8 ports detected
[   48.224651] ata_piix 0000:00:1f.1: version 2.10ac1
[   48.224926] ACPI: PCI Interrupt 0000:00:1f.1[A] -> <6>ACPI: PCI Interrupt 0000:05:08.0[A] -> GSI 16 (level, low) -> IRQ 16
[   48.224938] GSI 16 (level, low) -> IRQ 16
[   48.225012] mptbase: Initiating ioc0 bringup
[   48.225016] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   48.225250] ata1: PATA max UDMA/100 cmd 0x00000000000101f0 ctl 0x00000000000103f6 bmdma 0x000000000001fc00 irq 14
[   48.225302] ata2: PATA max UDMA/100 cmd 0x0000000000010170 ctl 0x0000000000010376 bmdma 0x000000000001fc08 irq 15
[   48.225324] scsi0 : ata_piix
[   48.560514] ata1.00: ATAPI, max UDMA/33
[   48.575636] usb 1-1: device not accepting address 2, error -71
[   48.739867] ata1.00: configured for UDMA/33
[   48.739890] scsi1 : ata_piix
[   48.740172] ata2: port disabled. ignoring.
[   48.741040] scsi 0:0:0:0: CD-ROM            HL-DT-ST CDRW/DVD GCC4482 E114 PQ: 0 ANSI: 5
[   48.741191] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[   48.895611] ACPI: PCI Interrupt 0000:00:1f.2[C] -> GSI 23 (level, low) -> IRQ 23
[   48.895639] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   48.895710] ata3: SATA max UDMA/133 cmd 0x000000000001cc78 ctl 0x000000000001cc72 bmdma 0x000000000001cc40 irq 23
[   48.895761] ata4: SATA max UDMA/133 cmd 0x000000000001cc60 ctl 0x000000000001cc5a bmdma 0x000000000001cc48 irq 23
[   48.895775] scsi2 : ata_piix
[   48.927588] ioc0: SAS1068: Capabilities={Initiator}
[   49.062201] ATA: abnormal status 0x7F on port 0x000000000001cc7f
[   49.062227] scsi3 : ata_piix
[   49.230136] ATA: abnormal status 0x7F on port 0x000000000001cc67
[   49.367552] usb 1-1: new low speed USB device using uhci_hcd and address 4
[   49.605573] usb 1-1: configuration #1 chosen from 1 choice
[   49.847457] usb 1-2: new low speed USB device using uhci_hcd and address 5
[   50.034344] usb 1-2: configuration #1 chosen from 1 choice
[   50.037366] usbcore: registered new interface driver hiddev
[   50.052387] input: CHICONY USB Keyboard as /class/input/input1
[   50.052402] input: USB HID v1.10 Keyboard [CHICONY USB Keyboard] on usb-0000:00:1d.0-1
[   50.065308] input: CHICONY USB Keyboard as /class/input/input2
[   50.065333] input: USB HID v1.10 Mouse [CHICONY USB Keyboard] on usb-0000:00:1d.0-1
[   50.079305] input: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) as /class/input/input3
[   50.079329] input: USB HID v1.10 Mouse [Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)] on usb-0000:00:1d.0-2
[   50.079341] usbcore: registered new interface driver usbhid
[   50.079344] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   50.731240] floppy0: no floppy controllers found
[   50.763085] scsi4 : ioc0: LSISAS1068, FwRev=000a3100h, Ports=1, MaxQ=286, IRQ=16
[   50.788278] scsi 4:0:0:0: Direct-Access     ATA      WDC WD2500YS-18S 6C06 PQ: 0 ANSI: 5
[   50.792156] scsi 4:0:1:0: Direct-Access     ATA      WDC WD2500YS-18S 6C06 PQ: 0 ANSI: 5
[   50.795424] scsi 4:1:0:0: Direct-Access     Dell     VIRTUAL DISK     1028 PQ: 0 ANSI: 5
[   50.804858] SCSI device sda: 486326272 512-byte hdwr sectors (248999 MB)
[   50.805090] sda: Write Protect is off
[   50.805094] sda: Mode Sense: 03 00 00 08
[   50.805503] SCSI device sda: write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[   50.805955] SCSI device sda: 486326272 512-byte hdwr sectors (248999 MB)
[   50.806185] sda: Write Protect is off
[   50.806189] sda: Mode Sense: 03 00 00 08
[   50.806602] SCSI device sda: write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[   50.806609]  sda:sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[   50.815099] Uniform CD-ROM driver Revision: 3.20
[   50.815172] sr 0:0:0:0: Attached scsi CD-ROM sr0
[   50.830142]  sda1 sda2 < sda5 >
[   50.853501] sd 4:1:0:0: Attached scsi disk sda
[   50.859275] sr 0:0:0:0: Attached scsi generic sg0 type 5
[   50.859642] scsi 4:0:0:0: Attached scsi generic sg1 type 0
[   50.859923] scsi 4:0:1:0: Attached scsi generic sg2 type 0
[   50.860136] sd 4:1:0:0: Attached scsi generic sg3 type 0
[   51.081799] Attempting manual resume
[   51.081803] swsusp: Resume From Partition 8:5
[   51.081805] PM: Checking swsusp image.
[   51.081995] PM: Resume from disk failed.
[   51.108540] kjournald starting.  Commit interval 5 seconds
[   51.108555] EXT3-fs: mounted filesystem with ordered data mode.
[   56.042042] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   56.051925] intel_rng: FWH not detected
[   56.083300] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   56.141684] parport: PnPBIOS parport detected.
[   56.141722] parport0: PC-style at 0x378, irq 7 [PCSPP,EPP]
[   56.478339] tg3: eth0: Link is up at 100 Mbps, full duplex.
[   56.478343] tg3: eth0: Flow control is on for TX and on for RX.
[   56.671315] NET: Registered protocol family 17
[   59.085310] floppy0: no floppy controllers found
[   59.241855] lp0: using parport0 (interrupt-driven).
[   59.402688] Adding 9896000k swap on /dev/disk/by-uuid/e40e4953-854c-4d22-9aae-215ce20696ca.  Priority:-1 extents:1 across:9896000k
[   59.562562] EXT3 FS on sda1, internal journal
[   59.893983] NET: Registered protocol family 10
[   59.894115] lo: Disabled Privacy Extensions
```

---

### Post by sr20ve on 2008-01-02
First thing that comes to my mind is the firmware on the controller and the hard drives. The hard drive firmware appears to be up to date with version 6C06. 

What is the firmware version on the raid controller?

---

### Post by NewKindaArt on 2008-01-03
Controller firmware: 0.10.49.00-IR

Any tips on updating the firmware would be appreciated.  I guess I need "lsitool" as described in 

[http://www.tomasek.cz/software/SAS5iRperf/index.html](http://www.tomasek.cz/software/SAS5iRperf/index.html)

but I can't seem to find any info on what the latest firmware is, or how to get it.

Thanks!

---

### Post by crouton on 2008-01-03
[http://linux.dell.com/storage.shtml#sas](http://linux.dell.com/storage.shtml#sas) might be of some use.

---

### Post by sr20ve on 2008-01-03
> **NewKindaArt said:**
> Controller firmware: 0.10.49.00-IR


Here is a newer version. I would just update via floppy (if you have one). The link below will extract a bootable floppy image with the update.

Dell SAS 5/iR Adapter, Firmware, English, Multi System, v.00.10.51.00.06.12.05.00, A03
[http://ftp.us.dell.com/SAS-RAID/BR168471.exe](http://ftp.us.dell.com/SAS-RAID/BR168471.exe)

Fixes/Enhancements
==================

1. Fixed an issue that causes errors during cable disconnect scenarios when connected to a Dell MD3000 enclosure
2. Addressed an issue where interrupt warnings were seen during Operating system installations
3. Fixed an issue with rebuild progress reporting in an OS environment
4. Improved Tape performance on SAS 5/E with External SAS Tape Units
5. Disabled option in BIOS to change the "report device missing delay" which could potentially cause timing related issues and performance related issues with attached devices when toggled
6. Modified Webpack script for SAS 5 cards so that it is compatible with other 6th Generation SAS controllers
7. Modified the SAS5 Option ROM to improve CHS (Cylinder/Head/Sector) to LBA (Logical Block Address) translation, to add support for newer disk partition utilities
==================

Or if you don't have a floppy, here is an ISO image I created that will make a bootable CD with the firmware update on it.

[sas5ir_firmware.iso]("http://www.retardedracing.com/stuff/sas5ir_firmware.iso")

1. Burn the ISO image to a cd.
2. Once you have burned the cd reboot the system and boot to the cd.
    On Most PowerEdge servers you can press F11 at the bios splash screen to get to the boot menu.
3. Once you have booted to an A:\ prompt type "R:" (without the quotes) and press enter to get to the R: drive
4. Once you are at an R:\ prompt execute the firmware flash by typing: SAS5IRA.bat

---

### Post by NewKindaArt on 2008-01-09
Thanks for the procedure and the firmware update!

The server in question needs to be highly available from now until Feb 10th, so I decided to pull the RAID controller card and just run one of the drives solo.  (I have a secondary backup system).

I tried each drive individually, and one of them reports errors on startup.  So it looks like it *was* a hardware failure (contrary to my earlier guess).

This raises a question: how can the status of the individual drives be checked when in the RAID?  I'm guessing that maybe the "Diagnostics" routine in lsiutil might do it.

After Feb 10th I'll replace the card, update the firmware, and rebuild the array (with a replacement drive... thanks, Dell).  If I get any further insights, I'll post them here.

Thanks for your help!

---

