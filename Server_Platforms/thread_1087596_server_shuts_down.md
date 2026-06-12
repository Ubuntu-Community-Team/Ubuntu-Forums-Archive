---
title: "server shuts down"
date: 2009-03-05
forum: Server Platforms
---

### Post by bellalamb on 2009-03-05
Hi

I am running Ubuntu Server v7.04 with Webmin/Vitualmin

For the last 2 weeks, my server has been shutting itself off at 00.05 every day

Any idea where I should start to look to resolve the problem?

Otherwise it seems to be working perfectly

Regards

Paul

---

### Post by HermanAB on 2009-03-05
$ tail -n 10000 /var/log/messages | less

Cheers,

Herman

---

### Post by E_K on 2009-03-05
In other words check the logs to see what is happening just before the system shuts down. I'd bet that it's not a heat problem if it's shuting down at the same time every day exactly to the minute. Remember the logs they are the answer to the questions. Still don't know what's going on post back with some of the logs of what is happening just before the system shuts down.

---

### Post by bellalamb on 2009-03-12
Nothing is shown in the message log before shutdown 
debug log shows the same 

Not sure where to start looking 

this is the log on startup

```

Mar 12 05:49:00 ubuntu2 syslog-ng[3698]: syslog-ng starting up; version='2.0.0' 
Mar 12 05:49:00 ubuntu2 kernel: [    0.000000] Linux version 2.6.20-15-server (root@palmer) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Sun Apr 15 07:41:34 UTC 2007 (Ubuntu 2.6.20-15.27-server)
Mar 12 05:49:00 ubuntu2 kernel: [    0.000000] BIOS-provided physical RAM map:
Mar 12 05:49:00 ubuntu2 kernel: [    0.000000] sanitize start
Mar 12 05:49:00 ubuntu2 kernel: [    0.000000] sanitize end
Mar 12 05:49:00 ubuntu2 kernel: [    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009f800 end: 000000000009f800 type: 1
Mar 12 05:49:00 ubuntu2 kernel: [    0.000000] copy_e820_map() type is E820_RAM
Mar 12 05:49:00 ubuntu2 kernel: [    0.000000] copy_e820_map() start: 000000000009f800 size: 0000000000000800 end: 00000000000a0000 type: 2
Mar 12 05:49:00 ubuntu2 kernel: [    0.000000] copy_e820_map() start: 00000000000cc000 size: 0000000000004000 end: 00000000000d0000 type: 2
Mar 12 05:49:00 ubuntu2 kernel: [    0.000000] copy_e820_map() start: 00000000000e4000 size: 000000000001c000 end: 0000000000100000 type: 2
Mar 12 05:49:00 ubuntu2 kernel: [    0.000000] copy_e820_map() start: 0000000000100000 size: 000000003fdf0000 end: 000000003fef0000 type: 1
Mar 12 05:49:00 ubuntu2 kernel: [    0.000000] copy_e820_map() type is E820_RAM
Mar 12 05:49:00 ubuntu2 kernel: [    0.000000] copy_e820_map() start: 000000003fef0000 size: 000000000000f000 end: 000000003feff000 type: 3
Mar 12 05:49:00 ubuntu2 kernel: [    0.000000] copy_e820_map() start: 000000003feff000 size: 0000000000001000 end: 000000003ff00000 type: 4
Mar 12 05:49:00 ubuntu2 kernel: [    0.000000] copy_e820_map() start: 000000003ff00000 size: 0000000000100000 end: 0000000040000000 type: 1
Mar 12 05:49:00 ubuntu2 kernel: [    0.000000] copy_e820_map() type is E820_RAM
Mar 12 05:49:00 ubuntu2 kernel: [    0.000000] copy_e820_map() start: 00000000fec00000 size: 0000000000100000 end: 00000000fed00000 type: 2
Mar 12 05:49:00 ubuntu2 kernel: [    0.000000] copy_e820_map() start: 00000000fee00000 size: 0000000000001000 end: 00000000fee01000 type: 2
Mar 12 05:49:00 ubuntu2 kernel: [    0.000000] copy_e820_map() start: 00000000ffb80000 size: 0000000000080000 end: 00000000ffc00000 type: 2
Mar 12 05:49:00 ubuntu2 kernel: [    0.000000] copy_e820_map() start: 00000000fff00000 size: 0000000000100000 end: 0000000100000000 type: 2
Mar 12 05:49:00 ubuntu2 kernel: [    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
Mar 12 05:49:00 ubuntu2 kernel: [    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
Mar 12 05:49:00 ubuntu2 kernel: [    0.000000]  BIOS-e820: 00000000000cc000 - 00000000000d0000 (reserved)
Mar 12 05:49:00 ubuntu2 kernel: [    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
Mar 12 05:49:00 ubuntu2 kernel: [    0.000000]  BIOS-e820: 0000000000100000 - 000000003fef0000 (usable)
Mar 12 05:49:00 ubuntu2 kernel: [    0.000000]  BIOS-e820: 000000003fef0000 - 000000003feff000 (ACPI data)
Mar 12 05:49:00 ubuntu2 kernel: [    0.000000]  BIOS-e820: 000000003feff000 - 000000003ff00000 (ACPI NVS)
Mar 12 05:49:00 ubuntu2 kernel: [    0.000000]  BIOS-e820: 000000003ff00000 - 0000000040000000 (usable)
Mar 12 05:49:00 ubuntu2 kernel: [    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fed00000 (reserved)
Mar 12 05:49:00 ubuntu2 kernel: [    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
Mar 12 05:49:00 ubuntu2 kernel: [    0.000000]  BIOS-e820: 00000000ffb80000 - 00000000ffc00000 (reserved)
Mar 12 05:49:00 ubuntu2 kernel: [    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
Mar 12 05:49:00 ubuntu2 kernel: [    0.000000] 128MB HIGHMEM available.
Mar 12 05:49:00 ubuntu2 kernel: [    0.000000] 896MB LOWMEM available.
Mar 12 05:49:00 ubuntu2 kernel: [    0.000000] Zone PFN ranges:
Mar 12 05:49:00 ubuntu2 kernel: [    0.000000]   DMA             0 ->     4096
Mar 12 05:49:00 ubuntu2 kernel: [    0.000000]   Normal       4096 ->   229376
Mar 12 05:49:00 ubuntu2 kernel: [    0.000000]   HighMem    229376 ->   262144
Mar 12 05:49:00 ubuntu2 kernel: [    0.000000] early_node_map[1] active PFN ranges
Mar 12 05:49:00 ubuntu2 kernel: [    0.000000]     0:        0 ->   262144
Mar 12 05:49:00 ubuntu2 kernel: [    0.000000] DMI present.
Mar 12 05:49:00 ubuntu2 kernel: [    0.000000] ACPI: PM-Timer IO Port: 0xf008
Mar 12 05:49:00 ubuntu2 kernel: [    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
Mar 12 05:49:00 ubuntu2 kernel: [    0.000000] Processor #0 15:0 APIC version 20
Mar 12 05:49:00 ubuntu2 kernel: [    0.000000] ACPI: LAPIC_NMI (acpi_id[0xff] high edge lint[0x1])
Mar 12 05:49:00 ubuntu2 kernel: [    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
Mar 12 05:49:00 ubuntu2 kernel: [    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
Mar 12 05:49:00 ubuntu2 kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
Mar 12 05:49:00 ubuntu2 kernel: [    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
Mar 12 05:49:00 ubuntu2 kernel: [    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
Mar 12 05:49:00 ubuntu2 kernel: [    0.000000] Using ACPI (MADT) for SMP configuration information
Mar 12 05:49:00 ubuntu2 kernel: [    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:bec00000)
Mar 12 05:49:00 ubuntu2 kernel: [    0.000000] Detected 1398.616 MHz processor.
Mar 12 05:49:00 ubuntu2 kernel: [   12.090402] Built 1 zonelists.  Total pages: 260096
Mar 12 05:49:00 ubuntu2 kernel: [   12.090411] Kernel command line: root=UUID=727be14e-7ff1-49bc-8568-59f7d1f19c72 ro quiet splash
Mar 12 05:49:00 ubuntu2 kernel: [   12.090766] Enabling fast FPU save and restore... done.
Mar 12 05:49:00 ubuntu2 kernel: [   12.090772] Enabling unmasked SIMD FPU exception support... done.
Mar 12 05:49:00 ubuntu2 kernel: [   12.090793] Initializing CPU#0
Mar 12 05:49:00 ubuntu2 kernel: [   12.090901] PID hash table entries: 4096 (order: 12, 16384 bytes)
Mar 12 05:49:00 ubuntu2 kernel: [   12.092513] Console: colour VGA+ 80x25
Mar 12 05:49:00 ubuntu2 kernel: [   12.093702] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Mar 12 05:49:00 ubuntu2 kernel: [   12.095415] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Mar 12 05:49:00 ubuntu2 kernel: [   12.158319] Memory: 1028408k/1048576k available (2020k kernel code, 19344k reserved, 893k data, 328k init, 131008k highmem)
Mar 12 05:49:00 ubuntu2 kernel: [   12.158343] virtual kernel memory layout:
Mar 12 05:49:00 ubuntu2 kernel: [   12.158345]     fixmap  : 0xfff4f000 - 0xfffff000   ( 704 kB)
Mar 12 05:49:00 ubuntu2 kernel: [   12.158348]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
Mar 12 05:49:00 ubuntu2 kernel: [   12.158350]     vmalloc : 0xf8800000 - 0xffbfe000   ( 115 MB)
Mar 12 05:49:00 ubuntu2 kernel: [   12.158352]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
Mar 12 05:49:00 ubuntu2 kernel: [   12.158354]       .init : 0xc03df000 - 0xc0431000   ( 328 kB)
Mar 12 05:49:00 ubuntu2 kernel: [   12.158356]       .data : 0xc02f9114 - 0xc03d8754   ( 893 kB)
Mar 12 05:49:00 ubuntu2 kernel: [   12.158359]       .text : 0xc0100000 - 0xc02f9114   (2020 kB)
Mar 12 05:49:00 ubuntu2 kernel: [   12.158365] Checking if this processor honours the WP bit even in supervisor mode... Ok.
Mar 12 05:49:00 ubuntu2 kernel: [   12.300854] Calibrating delay using timer specific routine.. 2799.63 BogoMIPS (lpj=13998192)
Mar 12 05:49:00 ubuntu2 kernel: [   12.300957] Security Framework v1.0.0 initialized
Mar 12 05:49:00 ubuntu2 kernel: [   12.300979] SELinux:  Disabled at boot.
Mar 12 05:49:00 ubuntu2 kernel: [   12.301014] Mount-cache hash table entries: 512
Mar 12 05:49:00 ubuntu2 kernel: [   12.301408] CPU: Trace cache: 12K uops, L1 D cache: 8K
Mar 12 05:49:00 ubuntu2 kernel: [   12.301414] CPU: L2 cache: 256K
Mar 12 05:49:00 ubuntu2 kernel: [   12.301419] CPU: Hyper-Threading is disabled
Mar 12 05:49:00 ubuntu2 kernel: [   12.301453] Compat vDSO mapped to ffffe000.
Mar 12 05:49:00 ubuntu2 kernel: [   12.301464] Remapping vsyscall page to ffffe000
Mar 12 05:49:00 ubuntu2 kernel: [   12.301492] Checking 'hlt' instruction... OK.
Mar 12 05:49:00 ubuntu2 kernel: [   12.341107] SMP alternatives: switching to UP code
Mar 12 05:49:00 ubuntu2 kernel: [   12.341575] Freeing SMP alternatives: 11k freed
Mar 12 05:49:00 ubuntu2 kernel: [   12.342041] Early unpacking initramfs... done
Mar 12 05:49:00 ubuntu2 kernel: [   12.906473] ACPI: Core revision 20060707
Mar 12 05:49:00 ubuntu2 kernel: [   12.923537] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
Mar 12 05:49:00 ubuntu2 kernel: [   12.930140] CPU0: Intel(R) Pentium(R) 4 CPU 1400MHz stepping 0a
Mar 12 05:49:00 ubuntu2 kernel: [   12.930210] Total of 1 processors activated (2799.63 BogoMIPS).
Mar 12 05:49:00 ubuntu2 kernel: [   12.930368] ENABLING IO-APIC IRQs
Mar 12 05:49:00 ubuntu2 kernel: [   12.930594] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Mar 12 05:49:00 ubuntu2 kernel: [   13.150721] Brought up 1 CPUs
Mar 12 05:49:00 ubuntu2 kernel: [   13.151219] Booting paravirtualized kernel on bare hardware
Mar 12 05:49:00 ubuntu2 kernel: [   13.151377] Time:  5:48:42  Date: 02/12/109
Mar 12 05:49:00 ubuntu2 kernel: [   13.151437] NET: Registered protocol family 16
Mar 12 05:49:00 ubuntu2 kernel: [   13.151677] EISA bus registered
Mar 12 05:49:00 ubuntu2 kernel: [   13.151689] ACPI: bus type pci registered
Mar 12 05:49:00 ubuntu2 kernel: [   13.177134] PCI: PCI BIOS revision 2.10 entry at 0xfd963, last bus=2
Mar 12 05:49:00 ubuntu2 kernel: [   13.177138] PCI: Using configuration type 1
Mar 12 05:49:00 ubuntu2 kernel: [   13.177142] Setting up standard PCI resources
Mar 12 05:49:00 ubuntu2 kernel: [   13.204714] ACPI: Interpreter enabled
Mar 12 05:49:00 ubuntu2 kernel: [   13.204726] ACPI: Using IOAPIC for interrupt routing
Mar 12 05:49:00 ubuntu2 kernel: [   13.205526] ACPI: PCI Root Bridge [PCI0] (0000:00)
Mar 12 05:49:00 ubuntu2 kernel: [   13.206216] PCI quirk: region f000-f07f claimed by ICH4 ACPI/GPIO/TCO
Mar 12 05:49:00 ubuntu2 kernel: [   13.206224] PCI quirk: region f180-f1bf claimed by ICH4 GPIO
Mar 12 05:49:00 ubuntu2 kernel: [   13.206967] PCI: Transparent bridge - 0000:00:1e.0
Mar 12 05:49:00 ubuntu2 kernel: [   13.213385] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
Mar 12 05:49:00 ubuntu2 kernel: [   13.213831] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
Mar 12 05:49:00 ubuntu2 kernel: [   13.214243] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
Mar 12 05:49:00 ubuntu2 kernel: [   13.214653] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
Mar 12 05:49:00 ubuntu2 kernel: [   13.215052] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Mar 12 05:49:00 ubuntu2 kernel: [   13.215452] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Mar 12 05:49:00 ubuntu2 kernel: [   13.215848] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
Mar 12 05:49:00 ubuntu2 kernel: [   13.216264] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
Mar 12 05:49:00 ubuntu2 kernel: [   13.218569] ACPI: Device [ECP] status [00000008]: functional but not present; setting present
Mar 12 05:49:00 ubuntu2 kernel: [   13.220146] ACPI: Device [GAME] status [00000008]: functional but not present; setting present
Mar 12 05:49:00 ubuntu2 kernel: [   13.220472] ACPI: Device [MIDI] status [00000008]: functional but not present; setting present
Mar 12 05:49:00 ubuntu2 kernel: [   13.220850] Linux Plug and Play Support v0.97 (c) Adam Belay
Mar 12 05:49:00 ubuntu2 kernel: [   13.220877] pnp: PnP ACPI init
Mar 12 05:49:00 ubuntu2 kernel: [   13.224910] pnp: PnP ACPI: found 13 devices
Mar 12 05:49:00 ubuntu2 kernel: [   13.224925] PnPBIOS: Disabled by ACPI PNP
Mar 12 05:49:00 ubuntu2 kernel: [   13.225061] PCI: Using ACPI for IRQ routing
Mar 12 05:49:00 ubuntu2 kernel: [   13.225069] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
Mar 12 05:49:00 ubuntu2 kernel: [   13.229163] NET: Registered protocol family 8
Mar 12 05:49:00 ubuntu2 kernel: [   13.229168] NET: Registered protocol family 20
Mar 12 05:49:00 ubuntu2 kernel: [   13.229188] NetLabel: Initializing
Mar 12 05:49:00 ubuntu2 kernel: [   13.229191] NetLabel:  domain hash size = 128
Mar 12 05:49:00 ubuntu2 kernel: [   13.229194] NetLabel:  protocols = UNLABELED CIPSOv4
Mar 12 05:49:00 ubuntu2 kernel: [   13.229226] NetLabel:  unlabeled traffic allowed by default
Mar 12 05:49:00 ubuntu2 kernel: [   13.230257] PCI: Bridge: 0000:00:01.0
Mar 12 05:49:00 ubuntu2 kernel: [   13.230260]   IO window: disabled.
Mar 12 05:49:00 ubuntu2 kernel: [   13.230268]   MEM window: f4000000-f4ffffff
Mar 12 05:49:00 ubuntu2 kernel: [   13.230275]   PREFETCH window: f6000000-f7ffffff
Mar 12 05:49:00 ubuntu2 kernel: [   13.230283] PCI: Bridge: 0000:00:1e.0
Mar 12 05:49:00 ubuntu2 kernel: [   13.230289]   IO window: 3000-3fff
Mar 12 05:49:00 ubuntu2 kernel: [   13.230297]   MEM window: f5000000-f50fffff
Mar 12 05:49:00 ubuntu2 kernel: [   13.230305]   PREFETCH window: 50000000-500fffff
Mar 12 05:49:00 ubuntu2 kernel: [   13.230389] NET: Registered protocol family 2
Mar 12 05:49:00 ubuntu2 kernel: [   13.300771] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
Mar 12 05:49:00 ubuntu2 kernel: [   13.301208] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
Mar 12 05:49:00 ubuntu2 kernel: [   13.303735] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
Mar 12 05:49:00 ubuntu2 kernel: [   13.305122] TCP: Hash tables configured (established 131072 bind 65536)
Mar 12 05:49:00 ubuntu2 kernel: [   13.305134] TCP reno registered
Mar 12 05:49:00 ubuntu2 kernel: [   13.330933] checking if image is initramfs... it is
Mar 12 05:49:00 ubuntu2 kernel: [   14.438491] Freeing initrd memory: 6626k freed
Mar 12 05:49:00 ubuntu2 kernel: [   14.438929] Simple Boot Flag at 0x69 set to 0x1
Mar 12 05:49:00 ubuntu2 kernel: [   14.439417] audit: initializing netlink socket (disabled)
Mar 12 05:49:00 ubuntu2 kernel: [   14.439446] audit(1236836924.190:1): initialized
Mar 12 05:49:00 ubuntu2 kernel: [   14.439571] highmem bounce pool size: 64 pages
Mar 12 05:49:00 ubuntu2 kernel: [   14.439712] VFS: Disk quotas dquot_6.5.1
Mar 12 05:49:00 ubuntu2 kernel: [   14.439753] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Mar 12 05:49:00 ubuntu2 kernel: [   14.439866] io scheduler noop registered
Mar 12 05:49:00 ubuntu2 kernel: [   14.439872] io scheduler anticipatory registered
Mar 12 05:49:00 ubuntu2 kernel: [   14.439877] io scheduler deadline registered (default)
Mar 12 05:49:00 ubuntu2 kernel: [   14.439898] io scheduler cfq registered
Mar 12 05:49:00 ubuntu2 kernel: [   14.440451] isapnp: Scanning for PnP cards...
Mar 12 05:49:00 ubuntu2 kernel: [   14.797624] isapnp: No Plug & Play device found
Mar 12 05:49:00 ubuntu2 kernel: [   14.905447] Real Time Clock Driver v1.12ac
Mar 12 05:49:00 ubuntu2 kernel: [   14.905551] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
Mar 12 05:49:00 ubuntu2 kernel: [   14.905746] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Mar 12 05:49:00 ubuntu2 kernel: [   14.906292] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
Mar 12 05:49:00 ubuntu2 kernel: [   14.908271] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
Mar 12 05:49:00 ubuntu2 kernel: [   14.909043] 00:0c: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
Mar 12 05:49:00 ubuntu2 kernel: [   14.909707] mice: PS/2 mouse device common for all mice
Mar 12 05:49:00 ubuntu2 kernel: [   14.911070] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
Mar 12 05:49:00 ubuntu2 kernel: [   14.911638] input: Macintosh mouse button emulation as /class/input/input0
Mar 12 05:49:00 ubuntu2 kernel: [   14.911722] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Mar 12 05:49:00 ubuntu2 kernel: [   14.911732] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Mar 12 05:49:00 ubuntu2 kernel: [   14.912142] PNP: PS/2 Controller [PNP0303:KEYB,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
Mar 12 05:49:00 ubuntu2 kernel: [   14.915882] serio: i8042 KBD port at 0x60,0x64 irq 1
Mar 12 05:49:00 ubuntu2 kernel: [   14.915898] serio: i8042 AUX port at 0x60,0x64 irq 12
Mar 12 05:49:00 ubuntu2 kernel: [   14.916280] EISA: Probing bus 0 at eisa.0
Mar 12 05:49:00 ubuntu2 kernel: [   14.916295] Cannot allocate resource for EISA slot 1
Mar 12 05:49:00 ubuntu2 kernel: [   14.916300] Cannot allocate resource for EISA slot 2
Mar 12 05:49:00 ubuntu2 kernel: [   14.916304] Cannot allocate resource for EISA slot 3
Mar 12 05:49:00 ubuntu2 kernel: [   14.916337] EISA: Detected 0 cards.
Mar 12 05:49:00 ubuntu2 kernel: [   14.946532] TCP cubic registered
Mar 12 05:49:00 ubuntu2 kernel: [   14.946547] NET: Registered protocol family 1
Mar 12 05:49:00 ubuntu2 kernel: [   14.946592] Using IPI No-Shortcut mode
Mar 12 05:49:00 ubuntu2 kernel: [   14.946776] ACPI: (supports S0 S1 S3 S4 S5)
Mar 12 05:49:00 ubuntu2 kernel: [   14.946868]   Magic number: 1:198:820
Mar 12 05:49:00 ubuntu2 kernel: [   14.947073]   hash matches device ptyt0
Mar 12 05:49:00 ubuntu2 kernel: [   14.947859] Freeing unused kernel memory: 328k freed
Mar 12 05:49:00 ubuntu2 kernel: [   14.950161] Time: tsc clocksource has been installed.
Mar 12 05:49:00 ubuntu2 kernel: [   14.960473] input: AT Translated Set 2 keyboard as /class/input/input1
Mar 12 05:49:00 ubuntu2 kernel: [   15.325469] Capability LSM initialized
Mar 12 05:49:00 ubuntu2 kernel: [   16.798503] SCSI subsystem initialized
Mar 12 05:49:00 ubuntu2 kernel: [   16.818874] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x00012400 irq 14
Mar 12 05:49:00 ubuntu2 kernel: [   16.818952] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x00012408 irq 15
Mar 12 05:49:00 ubuntu2 kernel: [   16.818985] scsi0 : ata_piix
Mar 12 05:49:00 ubuntu2 kernel: [   16.903107] 8139too Fast Ethernet driver 0.9.28
Mar 12 05:49:00 ubuntu2 kernel: [   16.913297] usbcore: registered new interface driver usbfs
Mar 12 05:49:00 ubuntu2 kernel: [   16.913347] usbcore: registered new interface driver hub
Mar 12 05:49:00 ubuntu2 kernel: [   16.913407] usbcore: registered new device driver usb
Mar 12 05:49:00 ubuntu2 kernel: [   16.915567] USB Universal Host Controller Interface driver v3.0
Mar 12 05:49:00 ubuntu2 kernel: [   16.991176] ata1.00: ata_hpa_resize 1: sectors = 234441648, hpa_sectors = 234441648
Mar 12 05:49:00 ubuntu2 kernel: [   16.991186] ata1.00: ATA-6: WDC WD1200JB-00FUA0, 15.05R15, max UDMA/100
Mar 12 05:49:00 ubuntu2 kernel: [   16.991191] ata1.00: 234441648 sectors, multi 16: LBA48 
Mar 12 05:49:00 ubuntu2 kernel: [   17.011165] ata1.00: ata_hpa_resize 1: sectors = 234441648, hpa_sectors = 234441648
Mar 12 05:49:00 ubuntu2 kernel: [   17.011180] ata1.00: configured for UDMA/100
Mar 12 05:49:00 ubuntu2 kernel: [   17.011213] scsi1 : ata_piix
Mar 12 05:49:00 ubuntu2 kernel: [   17.140485] Floppy drive(s): fd0 is 1.44M
Mar 12 05:49:00 ubuntu2 kernel: [   17.215746] FDC 0 is a post-1991 82077
Mar 12 05:49:00 ubuntu2 kernel: [   17.350142] ata2.00: ATAPI, max UDMA/33
Mar 12 05:49:00 ubuntu2 kernel: [   17.530037] ata2.00: configured for UDMA/33
Mar 12 05:49:00 ubuntu2 kernel: [   17.530287] scsi 0:0:0:0: Direct-Access     ATA      WDC WD1200JB-00F 15.0 PQ: 0 ANSI: 5
Mar 12 05:49:00 ubuntu2 kernel: [   17.532402] scsi 1:0:0:0: CD-ROM            SAMSUNG  CD-R/RW SW-252B  R701 PQ: 0 ANSI: 5
Mar 12 05:49:00 ubuntu2 kernel: [   17.535484] ACPI: PCI Interrupt 0000:02:07.0[A] -> GSI 18 (level, low) -> IRQ 16
Mar 12 05:49:00 ubuntu2 kernel: [   17.535907] eth0: RealTek RTL8139 at 0xf8852000, 00:30:f1:42:83:07, IRQ 16
Mar 12 05:49:00 ubuntu2 kernel: [   17.535957] ACPI: PCI Interrupt 0000:00:1f.2[D] -> GSI 19 (level, low) -> IRQ 17
Mar 12 05:49:00 ubuntu2 kernel: [   17.535980] uhci_hcd 0000:00:1f.2: UHCI Host Controller
Mar 12 05:49:00 ubuntu2 kernel: [   17.536241] uhci_hcd 0000:00:1f.2: new USB bus registered, assigned bus number 1
Mar 12 05:49:00 ubuntu2 kernel: [   17.536290] uhci_hcd 0000:00:1f.2: irq 17, io base 0x00001000
Mar 12 05:49:00 ubuntu2 kernel: [   17.536546] usb usb1: configuration #1 chosen from 1 choice
Mar 12 05:49:00 ubuntu2 kernel: [   17.536600] hub 1-0:1.0: USB hub found
Mar 12 05:49:00 ubuntu2 kernel: [   17.536618] hub 1-0:1.0: 2 ports detected
Mar 12 05:49:00 ubuntu2 kernel: [   17.639867] ACPI: PCI Interrupt 0000:00:1f.4[C] -> GSI 23 (level, low) -> IRQ 18
Mar 12 05:49:00 ubuntu2 kernel: [   17.639898] uhci_hcd 0000:00:1f.4: UHCI Host Controller
Mar 12 05:49:00 ubuntu2 kernel: [   17.639945] uhci_hcd 0000:00:1f.4: new USB bus registered, assigned bus number 2
Mar 12 05:49:00 ubuntu2 kernel: [   17.639990] uhci_hcd 0000:00:1f.4: irq 18, io base 0x00001800
Mar 12 05:49:00 ubuntu2 kernel: [   17.640198] usb usb2: configuration #1 chosen from 1 choice
Mar 12 05:49:00 ubuntu2 kernel: [   17.640250] hub 2-0:1.0: USB hub found
Mar 12 05:49:00 ubuntu2 kernel: [   17.640268] hub 2-0:1.0: 2 ports detected
Mar 12 05:49:00 ubuntu2 kernel: [   17.774844] SCSI device sda: 234441648 512-byte hdwr sectors (120034 MB)
Mar 12 05:49:00 ubuntu2 kernel: [   17.774872] sda: Write Protect is off
Mar 12 05:49:00 ubuntu2 kernel: [   17.774911] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Mar 12 05:49:00 ubuntu2 kernel: [   17.775026] SCSI device sda: 234441648 512-byte hdwr sectors (120034 MB)
Mar 12 05:49:00 ubuntu2 kernel: [   17.775046] sda: Write Protect is off
Mar 12 05:49:00 ubuntu2 kernel: [   17.775082] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Mar 12 05:49:00 ubuntu2 kernel: [   17.775087]  sda: sda1 sda2 < sda5 >
Mar 12 05:49:00 ubuntu2 kernel: [   17.841422] sd 0:0:0:0: Attached scsi disk sda
Mar 12 05:49:00 ubuntu2 kernel: [   17.861137] sd 0:0:0:0: Attached scsi generic sg0 type 0
Mar 12 05:49:00 ubuntu2 kernel: [   17.861180] sr 1:0:0:0: Attached scsi generic sg1 type 5
Mar 12 05:49:00 ubuntu2 kernel: [   17.888697] sr0: scsi3-mmc drive: 52x/52x writer cd/rw xa/form2 cdda tray
Mar 12 05:49:00 ubuntu2 kernel: [   17.888709] Uniform CD-ROM driver Revision: 3.20
Mar 12 05:49:00 ubuntu2 kernel: [   18.099089] Attempting manual resume
Mar 12 05:49:00 ubuntu2 kernel: [   18.136702] EXT3-fs: INFO: recovery required on readonly filesystem.
Mar 12 05:49:00 ubuntu2 kernel: [   18.136712] EXT3-fs: write access will be enabled during recovery.
Mar 12 05:49:00 ubuntu2 kernel: [   19.241536] kjournald starting.  Commit interval 5 seconds
Mar 12 05:49:00 ubuntu2 kernel: [   19.241578] EXT3-fs: sda1: orphan cleanup on readonly fs
Mar 12 05:49:00 ubuntu2 kernel: [   19.241731] EXT3-fs: sda1: 5 orphan inodes deleted
Mar 12 05:49:00 ubuntu2 kernel: [   19.241734] EXT3-fs: recovery complete.
Mar 12 05:49:00 ubuntu2 kernel: [   19.257784] EXT3-fs: mounted filesystem with ordered data mode.
Mar 12 05:49:00 ubuntu2 kernel: [   22.180412] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Mar 12 05:49:00 ubuntu2 kernel: [   23.023478] NET: Registered protocol family 10
Mar 12 05:49:00 ubuntu2 kernel: [   23.023673] lo: Disabled Privacy Extensions
Mar 12 05:49:00 ubuntu2 kernel: [   24.928356] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Mar 12 05:49:00 ubuntu2 kernel: [   24.945122] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Mar 12 05:49:00 ubuntu2 kernel: [   25.251623] iTCO_vendor_support: vendor-support=0
Mar 12 05:49:00 ubuntu2 kernel: [   25.253989] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
Mar 12 05:49:00 ubuntu2 kernel: [   25.254125] iTCO_wdt: Found a ICH2 TCO device (Version=1, TCOBASE=0x7060)
Mar 12 05:49:00 ubuntu2 kernel: [   25.254153] iTCO_wdt: heartbeat value must be 2<heartbeat<39 (TCO v1) or 613 (TCO v2), using 30
Mar 12 05:49:00 ubuntu2 kernel: [   25.254198] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
Mar 12 05:49:00 ubuntu2 kernel: [   25.729486] input: PC Speaker as /class/input/input2
Mar 12 05:49:00 ubuntu2 kernel: [   25.925158] Linux agpgart interface v0.102 (c) Dave Jones
Mar 12 05:49:00 ubuntu2 kernel: [   25.928856] agpgart: Detected an Intel i845 Chipset.
Mar 12 05:49:00 ubuntu2 kernel: [   25.933077] agpgart: AGP aperture is 64M @ 0xf8000000
Mar 12 05:49:00 ubuntu2 kernel: [   26.039916] parport: PnPBIOS parport detected.
Mar 12 05:49:00 ubuntu2 kernel: [   26.039955] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
Mar 12 05:49:00 ubuntu2 kernel: [   26.434009] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 19
Mar 12 05:49:00 ubuntu2 kernel: [   26.747552] intel8x0_measure_ac97_clock: measured 50831 usecs
Mar 12 05:49:00 ubuntu2 kernel: [   26.747560] intel8x0: clocking to 48000
Mar 12 05:49:00 ubuntu2 kernel: [   27.082217] lp0: using parport0 (interrupt-driven).
Mar 12 05:49:00 ubuntu2 kernel: [   27.374302] Adding 3028212k swap on /dev/disk/by-uuid/34df129d-70ec-447d-9194-1a0d693d0f70.  Priority:-1 extents:1 across:3028212k
Mar 12 05:49:00 ubuntu2 kernel: [   27.581654] EXT3 FS on sda1, internal journal
Mar 12 05:49:06 ubuntu2 kernel: [   37.226846] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
Mar 12 05:49:07 ubuntu2 kernel: [   37.498355] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
Mar 12 05:49:07 ubuntu2 kernel: [   37.511620] NFSD: starting 90-second grace period
Mar 12 06:25:49 ubuntu2 syslog-ng[3698]: SIGHUP received, reloading configuration;  

```

---

