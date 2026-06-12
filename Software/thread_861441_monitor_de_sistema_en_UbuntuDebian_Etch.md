---
title: "monitor de sistema en Ubuntu/Debian Etch"
date: 2008-07-16
forum: Software
---

### Post by lega on 2008-07-16
Hace unos dias instale Debian Lenny y noté que en el monitor de sistema en Debian no me detecta los 2 cpu del procesador, (Amd64 x2 4200) cosa que si hace en Ubuntu, en las dos versiones tengo instalada la de 32 bits, porque será? me faltará instalar algo en Debian? adjunto capturas, las primeras dos son de Ubuntu y la tercera de debian 
Gracias

---

### Post by Hei Ku on 2008-07-16
Fijate en /var/log/dmesg
En el momento de arrancar tira unos mensajes relacionados a la deteccion del micro. Compara lo que dice en Ubuntu y en Debian.

En mi caso, son unos mensajes de este estilo:

```

24.695317] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   24.695379] CPU: L2 Cache: 512K (64 bytes/line)
[   24.695439] CPU 0/0 -> Node 0
[   24.695496] CPU: Physical Processor ID: 0
[   24.695554] CPU: Processor Core ID: 0
[   24.695638] SMP alternatives: switching to UP code
[   24.696389] Early unpacking initramfs... done
[   24.987732] ACPI: Core revision 20070126
[   24.987845] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   24.989451] ACPI: setting ELCR to 0200 (from 0c20)
[   24.993688] Using local APIC timer interrupts.
[   25.039170] APIC timer calibration result 12500286
[   25.039171] Detected 12.500 MHz APIC timer.
[   25.039349] SMP alternatives: switching to SMP code
[   25.039976] Booting processor 1/2 APIC 0x1
[   25.050427] Initializing CPU#1
[   25.094458] spurious 8259A interrupt: IRQ7.
[   25.127489] Calibrating delay using timer specific routine.. 4400.15 BogoMIPS (lpj=8800318)
[   25.127495] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   25.127497] CPU: L2 Cache: 512K (64 bytes/line)
[   25.127499] CPU 1/1 -> Node 0
[   25.127501] CPU: Physical Processor ID: 0
[   25.127502] CPU: Processor Core ID: 1
[   25.127590] AMD Athlon(tm) 64 X2 Dual Core Processor 4200+ stepping 01
[   25.127291] Brought up 2 CPUs
[   25.127870] CPU0 attaching sched-domain:
[   25.127873]  domain 0: span 03
[   25.127874]   groups: 01 02
[   25.127877]   domain 1: span 03
[   25.127879]    groups: 03
[   25.127881] CPU1 attaching sched-domain:
[   25.127882]  domain 0: span 03
[   25.127884]   groups: 02 01
[   25.127886]   domain 1: span 03
[   25.127887]    groups: 03

```

Fijate como dice CPU0 y CPU1

---

### Post by sdennie on 2008-07-16
Me parece que no tenés el kernel correcto en Debian (falta SMP).  No se mucho de Debian pero fijate si podés instalar el kernel -686.

---

### Post by lega on 2008-07-16
Gracias por las respuestas me fijé donde dijo Hei Ku y esto me aparece en Ubuntu
```
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-19-generic (buildd@terranova) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Fri Jul 11 23:41:49 UTC 2008 (Ubuntu 2.6.24-19.36-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000037fb0000 (usable)
[    0.000000]  BIOS-e820: 0000000037fb0000 - 0000000037fbe000 (ACPI data)
[    0.000000]  BIOS-e820: 0000000037fbe000 - 0000000037fe0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 0000000037fe0000 - 0000000037fee000 (reserved)
[    0.000000]  BIOS-e820: 0000000037ff0000 - 0000000038000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fef00000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 895MB LOWMEM available.
[    0.000000] found SMP MP-table at 000ff780
[    0.000000] Entering add_active_range(0, 0, 229296) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229296
[    0.000000]   HighMem    229296 ->   229296
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   229296
[    0.000000] On node 0 totalpages: 229296
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1759 pages used for memmap
[    0.000000]   Normal zone: 223441 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP signature @ 0xC00FB770 checksum 0
[    0.000000] ACPI: RSDP 000FB770, 0014 (r0 ACPIAM)
[    0.000000] ACPI: RSDT 37FB0000, 0034 (r1 A_M_I_ OEMRSDT  12000704 MSFT       97)
[    0.000000] ACPI: FACP 37FB0200, 0084 (r2 A_M_I_ OEMFACP  12000704 MSFT       97)
[    0.000000] ACPI: DSDT 37FB05D0, 65BA (r1  A0865 A0865000        0 INTL 20051117)
[    0.000000] ACPI: FACS 37FBE000, 0040
[    0.000000] ACPI: MCFG 37FB0410, 003C (r1 A_M_I_ OEMMCFG  12000704 MSFT       97)
[    0.000000] ACPI: OEMB 37FBE040, 0060 (r1 A_M_I_ AMI_OEM  12000704 MSFT       97)
[    0.000000] ACPI: HPET 37FB6B90, 0038 (r1 A_M_I_ OEMHPET0 12000704 MSFT       97)
[    0.000000] ACPI: PM-Timer IO Port: 0x508
[    0.000000] ACPI: HPET id: 0x10de8201 base: 0xfed00000
[    0.000000] Intel MultiProcessor Specification v1.4
[    0.000000]     Virtual Wire compatibility mode.
[    0.000000] OEM ID: TEMPLATE Product ID: SE-Plus      APIC at: 0xFEE00000
[    0.000000] Processor #0 15:11 APIC version 16
[    0.000000] Processor #1 15:11 APIC version 16
[    0.000000] I/O APIC #2 Version 17 at 0xFEC00000.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Processors: 2
[    0.000000] Allocating PCI resources starting at 40000000 (gap: 38000000:c6c00000)
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000e4000
[    0.000000] swsusp: Registered nosave memory region: 00000000000e4000 - 0000000000100000
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 227505
[    0.000000] Kernel command line: root=UUID=6e1fe050-0e53-41ce-b474-0fbc94ff95cc ro quiet splash vga=795 
[    0.000000] mapped APIC to ffffb000 (fee00000)
[    0.000000] mapped IOAPIC to ffffa000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.

[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 2210.117 MHz processor.
[   20.825362] spurious 8259A interrupt: IRQ7.
[   20.825391] Console: colour dummy device 80x25
[   20.825395] console [tty0] enabled
[   20.825833] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   20.826254] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   20.841433] Memory: 897156k/917184k available (2177k kernel code, 19468k reserved, 1006k data, 368k init, 0k highmem)
[   20.841439] virtual kernel memory layout:
[   20.841440]     fixmap  : 0xfff4b000 - 0xfffff000   ( 720 kB)
[   20.841441]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   20.841442]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   20.841443]     lowmem  : 0xc0000000 - 0xf7fb0000   ( 895 MB)
[   20.841444]       .init : 0xc0421000 - 0xc047d000   ( 368 kB)
[   20.841445]       .data : 0xc0320474 - 0xc041bdc4   (1006 kB)
[   20.841446]       .text : 0xc0100000 - 0xc0320474   (2177 kB)
[   20.841449] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   20.841478] SLUB: Genslabs=11, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   20.841600] hpet clockevent registered
[   20.921545] Calibrating delay using timer specific routine.. 4424.50 BogoMIPS (lpj=8849002)
[   20.921562] Security Framework initialized
[   20.921567] SELinux:  Disabled at boot.
[   20.921578] AppArmor: AppArmor initialized
[   20.921582] Failure registering capabilities with primary security module.
[   20.921589] Mount-cache hash table entries: 512
[   20.921680] Initializing cgroup subsys ns
[   20.921683] Initializing cgroup subsys cpuacct
[   20.921691] CPU: After generic identify, caps: 178bfbff ebd3fbff 00000000 00000000 00002001 00000000 0000011f 00000000
[   20.921698] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   20.921700] CPU: L2 Cache: 512K (64 bytes/line)
[   20.921702] CPU 0(2) -> Core 0
[   20.921704] CPU: After all inits, caps: 178bfbff ebd3fbff 00000000 00000410 00002001 00000000 0000011f 00000000
[   20.921711] Compat vDSO mapped to ffffe000.
[   20.921720] Checking 'hlt' instruction... OK.
[   20.937775] SMP alternatives: switching to UP code
[   20.938840] Early unpacking initramfs... done
[   21.210591] ACPI: Core revision 20070126
[   21.210648] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   21.212740] ACPI: setting ELCR to 0200 (from 0c20)
[   21.213137] CPU0: AMD Athlon(tm) 64 X2 Dual Core Processor 4200+ stepping 02
[   21.213152] SMP alternatives: switching to SMP code
[   21.213613] Booting processor 1/1 eip 3000
[   21.224344] Initializing CPU#1
[   21.301995] Calibrating delay using timer specific routine.. 4420.12 BogoMIPS (lpj=8840240)
[   21.302001] CPU: After generic identify, caps: 178bfbff ebd3fbff 00000000 00000000 00002001 00000000 0000011f 00000000
[   21.302007] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   21.302009] CPU: L2 Cache: 512K (64 bytes/line)
[   21.302011] CPU 1(2) -> Core 1
[   21.302012] CPU: After all inits, caps: 178bfbff ebd3fbff 00000000 00000410 00002001 00000000 0000011f 00000000
[   21.301465] CPU1: AMD Athlon(tm) 64 X2 Dual Core Processor 4200+ stepping 02
[   21.301480] Total of 2 processors activated (8844.62 BogoMIPS).
[   21.301565] ExtINT not setup in hardware but reported by MP table
[   21.301717] ENABLING IO-APIC IRQs
[   21.301950] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=0 pin2=0
[   21.449265] Brought up 2 CPUs
[   21.449311] CPU0 attaching sched-domain:
[   21.449314]  domain 0: span 03
[   21.449315]   groups: 01 02
[   21.449318] CPU1 attaching sched-domain:
[   21.449319]  domain 0: span 03
[   21.449321]   groups: 02 01
[   21.449508] net_namespace: 64 bytes
[   21.449514] Booting paravirtualized kernel on bare hardware
[   21.449919] Time: 19:57:50  Date: 07/16/08
[   21.449945] NET: Registered protocol family 16
[   21.450116] EISA bus registered
[   21.450121] ACPI: bus type pci registered
[   21.450926] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=4
[   21.450928] PCI: Using configuration type 1
[   21.450935] Setting up standard PCI resources
[   21.459137] ACPI: EC: Look up EC in DSDT
[   21.464328] ACPI: Interpreter enabled
[   21.464331] ACPI: (supports S0 S1 S3 S4 S5)
[   21.464344] ACPI: Using PIC for interrupt routing
[   21.464605] Error attaching device data
[   21.464610] Error attaching device data
[   21.464613] Error attaching device data
[   21.464617] Error attaching device data
[   21.472998] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   21.473549] PCI: Transparent bridge - 0000:00:04.0
[   21.473717] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   21.473886] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[   21.473990] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P2._PRT]
[   21.474073] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR11._PRT]
[   21.474156] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR12._PRT]
[   21.480542] ACPI: PCI Interrupt Link [LNKA] (IRQs 5 7 10 11 14) *0, disabled.
[   21.480704] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7 10 11 14) *0, disabled.
[   21.480865] ACPI: PCI Interrupt Link [LNKC] (IRQs 5 7 10 11 14) *0, disabled.
[   21.481024] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 7 10 11 14) *0, disabled.
[   21.481187] ACPI: PCI Interrupt Link [LNEA] (IRQs 5 7 10 11 14) *0, disabled.
[   21.481348] ACPI: PCI Interrupt Link [LNEB] (IRQs 5 7 10 11 14) *0, disabled.
[   21.481507] ACPI: PCI Interrupt Link [LNEC] (IRQs 5 7 10 11 14) *0, disabled.
[   21.481666] ACPI: PCI Interrupt Link [LNED] (IRQs 5 7 10 11 14) *0, disabled.
[   21.481827] ACPI: PCI Interrupt Link [LUB0] (IRQs *5 7 10 11 14)
[   21.481987] ACPI: PCI Interrupt Link [LUB2] (IRQs 5 7 10 *11 14)
[   21.482146] ACPI: PCI Interrupt Link [LMAC] (IRQs *5 7 10 11 14)
[   21.482305] ACPI: PCI Interrupt Link [LAZA] (IRQs 5 7 *10 11 14)
[   21.482464] ACPI: PCI Interrupt Link [LACI] (IRQs 5 7 10 11 14) *0, disabled.
[   21.482625] ACPI: PCI Interrupt Link [LMC9] (IRQs 5 7 10 *11 14)
[   21.482786] ACPI: PCI Interrupt Link [LSMB] (IRQs 5 7 *10 11 14)
[   21.482946] ACPI: PCI Interrupt Link [LPMU] (IRQs 5 7 10 11 14) *0, disabled.
[   21.483106] ACPI: PCI Interrupt Link [LSA0] (IRQs 5 7 10 *11 14)
[   21.483266] ACPI: PCI Interrupt Link [LSA1] (IRQs 5 7 10 11 14) *0, disabled.
[   21.483461] ACPI: PCI Interrupt Link [LATA] (IRQs 5 7 10 11 14) *0, disabled.
[   21.483568] ACPI Warning (tbutils-0217): Incorrect checksum in table [OEMB] -  58, should be 4B [20070126]
[   21.483575] Linux Plug and Play Support v0.97 (c) Adam Belay
[   21.483600] pnp: PnP ACPI init
[   21.483607] ACPI: bus type pnp registered
[   21.489446] pnp: PnP ACPI: found 16 devices
[   21.489448] ACPI: ACPI bus type pnp unregistered
[   21.489451] PnPBIOS: Disabled by ACPI PNP
[   21.489632] PCI: Using ACPI for IRQ routing
[   21.489635] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   21.509123] NET: Registered protocol family 8
[   21.509125] NET: Registered protocol family 20
[   21.509155] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 31
[   21.509158] hpet0: 3 32-bit timers, 25000000 Hz
[   21.510200] AppArmor: AppArmor Filesystem Enabled
[   21.513115] Time: hpet clocksource has been installed.
[   21.513128] Switched to high resolution mode on CPU 0
[   21.513957] Switched to high resolution mode on CPU 1
[   21.521113] system 00:07: ioport range 0xa30-0xa37 has been reserved
[   21.521116] system 00:07: ioport range 0x4d0-0x4d1 has been reserved
[   21.521119] system 00:07: ioport range 0x800-0x80f has been reserved
[   21.521121] system 00:07: ioport range 0x500-0x57f has been reserved
[   21.521123] system 00:07: ioport range 0x580-0x5ff has been reserved
[   21.521125] system 00:07: ioport range 0x800-0x87f could not be reserved
[   21.521128] system 00:07: ioport range 0x880-0x8ff has been reserved
[   21.521130] system 00:07: ioport range 0xd00-0xd7f has been reserved
[   21.521133] system 00:07: ioport range 0xd80-0xdff has been reserved
[   21.521135] system 00:07: ioport range 0x900-0x97f has been reserved
[   21.521138] system 00:07: ioport range 0x980-0x9ff has been reserved
[   21.521140] system 00:07: ioport range 0x2000-0x207f has been reserved
[   21.521142] system 00:07: ioport range 0x2080-0x20ff has been reserved
[   21.521145] system 00:07: iomem range 0xfefe0000-0xfefe01ff has been reserved
[   21.521148] system 00:07: iomem range 0xfefe1000-0xfefe1fff has been reserved
[   21.521150] system 00:07: iomem range 0xfee01000-0xfeefffff could not be reserved
[   21.521153] system 00:07: iomem range 0xffb80000-0xffffffff could not be reserved
[   21.521155] system 00:07: iomem range 0xff300000-0xff3fffff has been reserved
[   21.521161] system 00:09: iomem range 0xfec00000-0xfec00fff could not be reserved
[   21.521163] system 00:09: iomem range 0xfee00000-0xfee00fff could not be reserved
[   21.521166] system 00:09: iomem range 0x38000000-0x3fffffff has been reserved
[   21.521171] system 00:0c: ioport range 0x230-0x23f has been reserved
[   21.521173] system 00:0c: ioport range 0x290-0x29f has been reserved
[   21.521175] system 00:0c: ioport range 0xa00-0xa0f has been reserved
[   21.521178] system 00:0c: ioport range 0xa10-0xa1f has been reserved
[   21.521183] system 00:0e: iomem range 0xe0000000-0xefffffff has been reserved
[   21.521187] system 00:0f: iomem range 0x0-0x9ffff could not be reserved
[   21.521190] system 00:0f: iomem range 0xc0000-0xcffff could not be reserved
[   21.521192] system 00:0f: iomem range 0xe0000-0xfffff could not be reserved
[   21.521194] system 00:0f: iomem range 0x100000-0x37ffffff could not be reserved
[   21.521197] system 00:0f: iomem range 0xff700000-0xffffffff could not be reserved
[   21.551527] PCI: Bridge: 0000:00:04.0
[   21.551528]   IO window: disabled.
[   21.551531]   MEM window: disabled.
[   21.551534]   PREFETCH window: disabled.
[   21.551536] PCI: Bridge: 0000:00:09.0
[   21.551537]   IO window: disabled.
[   21.551539]   MEM window: disabled.
[   21.551541]   PREFETCH window: disabled.
[   21.551543] PCI: Bridge: 0000:00:0b.0
[   21.551544]   IO window: disabled.
[   21.551546]   MEM window: disabled.
[   21.551547]   PREFETCH window: disabled.
[   21.551549] PCI: Bridge: 0000:00:0c.0
[   21.551551]   IO window: disabled.
[   21.551552]   MEM window: disabled.
[   21.551554]   PREFETCH window: disabled.
[   21.551563] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   21.551572] PCI: Setting latency timer of device 0000:00:09.0 to 64
[   21.551578] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[   21.551583] PCI: Setting latency timer of device 0000:00:0c.0 to 64
[   21.551593] NET: Registered protocol family 2
[   21.589109] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   21.589391] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   21.590333] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   21.590821] TCP: Hash tables configured (established 131072 bind 65536)
[   21.590824] TCP reno registered
[   21.601154] checking if image is initramfs... it is
[   22.133143] Freeing initrd memory: 7321k freed
[   22.134650] audit: initializing netlink socket (disabled)
[   22.134664] audit(1216238270.184:1): initialized
[   22.136451] VFS: Disk quotas dquot_6.5.1
[   22.136512] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   22.136622] io scheduler noop registered
[   22.136624] io scheduler anticipatory registered
[   22.136625] io scheduler deadline registered
[   22.136634] io scheduler cfq registered (default)
[   22.136662] pci 0000:00:00.0: Enabling HT MSI Mapping
[   22.136744] pci 0000:00:04.0: Enabling HT MSI Mapping
[   22.136758] pci 0000:00:05.0: Enabling HT MSI Mapping
[   22.136783] pci 0000:00:07.0: Enabling HT MSI Mapping
[   22.136795] pci 0000:00:08.0: Enabling HT MSI Mapping
[   22.136808] pci 0000:00:09.0: Enabling HT MSI Mapping
[   22.136822] pci 0000:00:0b.0: Enabling HT MSI Mapping
[   22.136835] pci 0000:00:0c.0: Enabling HT MSI Mapping
[   22.136847] Boot video device is 0000:00:0d.0
[   22.136939] PCI: Setting latency timer of device 0000:00:09.0 to 64
[   22.136959] assign_interrupt_mode Found MSI capability
[   22.136977] Allocate Port Service[0000:00:09.0:pcie00]
[   22.137034] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[   22.137052] assign_interrupt_mode Found MSI capability
[   22.137066] Allocate Port Service[0000:00:0b.0:pcie00]
[   22.137117] PCI: Setting latency timer of device 0000:00:0c.0 to 64
[   22.137136] assign_interrupt_mode Found MSI capability
[   22.137149] Allocate Port Service[0000:00:0c.0:pcie00]
[   22.137348] isapnp: Scanning for PnP cards...
[   22.490515] isapnp: No Plug & Play device found
[   22.516979] Real Time Clock Driver v1.12ac
[   22.517171] hpet_resources: 0xfed00000 is busy
[   22.517209] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   22.517328] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   22.517909] 00:0d: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   22.518608] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   22.518666] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   22.518758] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[   22.519113] serio: i8042 KBD port at 0x60,0x64 irq 1
[   22.519118] serio: i8042 AUX port at 0x60,0x64 irq 12
[   22.538120] mice: PS/2 mouse device common for all mice
[   22.538236] EISA: Probing bus 0 at eisa.0
[   22.538244] Cannot allocate resource for EISA slot 2
[   22.538260] EISA: Detected 0 cards.
[   22.538263] cpuidle: using governor ladder
[   22.538265] cpuidle: using governor menu
[   22.538341] NET: Registered protocol family 1
[   22.538364] Using IPI No-Shortcut mode
[   22.538397] registered taskstats version 1
[   22.538488]   Magic number: 0:666:1001
[   22.538494]   hash matches device ttye0
[   22.538623]   hash matches device 00:03
[   22.538642] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   22.538644] EDD information not available.
[   22.538915] Freeing unused kernel memory: 368k freed
[   22.577036] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   22.625761] vesafb: framebuffer at 0xc0000000, mapped to 0xf8880000, using 10240k, total 131072k
[   22.625767] vesafb: mode is 1280x1024x32, linelength=5120, pages=0
[   22.625769] vesafb: protected mode interface info at c000:d560
[   22.625772] vesafb: pmi: set display start = c00cd596, set palette = c00cd600
[   22.625773] vesafb: pmi: ports = b4c3 b503 ba03 c003 c103 c403 c503 c603 c703 c803 c903 cc03 ce03 cf03 d003 d103 d203 d303 d403 d503 da03 ff03 
[   22.625785] vesafb: scrolling: redraw
[   22.625787] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[   22.625900] Console: switching to colour frame buffer device 160x64
[   22.651124] fb0: VESA VGA frame buffer device
[   23.786564] fuse init (API version 7.9)
[   23.801247] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[   23.801261] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[   23.801271] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[   23.801280] ACPI Exception (processor_core-0816): AE_NOT_FOUND, Processor Device is not present [20070126]
[   24.119851] usbcore: registered new interface driver usbfs
[   24.119874] usbcore: registered new interface driver hub
[   24.120449] usbcore: registered new device driver usb
[   24.131283] ACPI: PCI Interrupt Link [LUB2] enabled at IRQ 11
[   24.131288] PCI: setting IRQ 11 as level-triggered
[   24.131292] ACPI: PCI Interrupt 0000:00:02.1[B] -> Link [LUB2] -> GSI 11 (level, low) -> IRQ 11
[   24.131304] PCI: Setting latency timer of device 0000:00:02.1 to 64
[   24.131307] ehci_hcd 0000:00:02.1: EHCI Host Controller
[   24.131577] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 1
[   24.131605] ehci_hcd 0000:00:02.1: debug port 1
[   24.131609] PCI: cache line size of 64 is not supported by device 0000:00:02.1
[   24.131622] ehci_hcd 0000:00:02.1: irq 11, io mem 0xdfffec00
[   24.143074] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   24.143194] usb usb1: configuration #1 chosen from 1 choice
[   24.143216] hub 1-0:1.0: USB hub found
[   24.143222] hub 1-0:1.0: 8 ports detected
[   24.157841] SCSI subsystem initialized
[   24.160301] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   24.171515] libata version 3.00 loaded.
[   24.239980] Floppy drive(s): fd0 is 1.44M
[   24.254883] ACPI: PCI Interrupt Link [LUB0] enabled at IRQ 5
[   24.254888] PCI: setting IRQ 5 as level-triggered
[   24.254892] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [LUB0] -> GSI 5 (level, low) -> IRQ 5
[   24.254906] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   24.254909] ohci_hcd 0000:00:02.0: OHCI Host Controller
[   24.254943] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 2
[   24.254964] ohci_hcd 0000:00:02.0: irq 5, io mem 0xdffff000
[   24.262977] FDC 0 is a post-1991 82077
[   24.310801] usb usb2: configuration #1 chosen from 1 choice
[   24.310825] hub 2-0:1.0: USB hub found
[   24.310835] hub 2-0:1.0: 8 ports detected
[   24.411970] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
[   24.412274] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 5
[   24.412277] ACPI: PCI Interrupt 0000:00:07.0[A] -> Link [LMAC] -> GSI 5 (level, low) -> IRQ 5
[   24.412282] PCI: Setting latency timer of device 0000:00:07.0 to 64
[   24.794545] usb 2-4: new full speed USB device using ohci_hcd and address 2
[   24.930876] forcedeth 0000:00:07.0: ifname eth0, PHY OUI 0x1374 @ 1, addr 00:1e:8c:c8:41:66
[   24.930879] forcedeth 0000:00:07.0: highdma pwrctl mgmt timirq gbit lnktim msi desc-v3
[   24.943261] pata_amd 0000:00:06.0: version 0.3.10
[   24.943328] PCI: Setting latency timer of device 0000:00:06.0 to 64
[   24.944317] scsi0 : pata_amd
[   24.946011] scsi1 : pata_amd
[   24.946622] ata1: PATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[   24.946624] ata2: PATA max UDMA/133 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[   25.023283] usb 2-4: configuration #1 chosen from 1 choice
[   25.271302] ata1.00: ATAPI: PIONEER DVD-RW  DVR-109, 1.58, max UDMA/66
[   25.272603] ata1.01: ATA-6: WDC WD1200BB-55GUC0, 08.02D08, max UDMA/100
[   25.272605] ata1.01: 234441648 sectors, multi 16: LBA48 
[   25.444031] ata1.00: configured for UDMA/66
[   25.460246] ata1.01: configured for UDMA/100
[   25.460278] ata2: port disabled. ignoring.
[   25.466848] scsi 0:0:0:0: CD-ROM            PIONEER  DVD-RW  DVR-109  1.58 PQ: 0 ANSI: 5
[   25.466945] scsi 0:0:1:0: Direct-Access     ATA      WDC WD1200BB-55G 08.0 PQ: 0 ANSI: 5
[   25.469098] sata_nv 0000:00:08.0: version 3.5
[   25.469383] ACPI: PCI Interrupt Link [LSA0] enabled at IRQ 11
[   25.469386] ACPI: PCI Interrupt 0000:00:08.0[A] -> Link [LSA0] -> GSI 11 (level, low) -> IRQ 11
[   25.469433] PCI: Setting latency timer of device 0000:00:08.0 to 64
[   25.469592] scsi2 : sata_nv
[   25.469633] scsi3 : sata_nv
[   25.469741] ata3: SATA max UDMA/133 cmd 0xe400 ctl 0xe080 bmdma 0xd880 irq 11
[   25.469743] ata4: SATA max UDMA/133 cmd 0xe000 ctl 0xdc00 bmdma 0xd888 irq 11
[   25.934407] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   25.958635] ata3.00: ATA-7: Hitachi HDS721616PLA320, P22OABGA, max UDMA/133
[   25.958637] ata3.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   25.974617] ata3.00: configured for UDMA/133
[   26.287120] ata4: SATA link down (SStatus 0 SControl 300)
[   26.297406] scsi 2:0:0:0: Direct-Access     ATA      Hitachi HDS72161 P22O PQ: 0 ANSI: 5
[   26.306413] Driver 'sd' needs updating - please use bus_type methods
[   26.306626] sd 0:0:1:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[   26.306640] sd 0:0:1:0: [sda] Write Protect is off
[   26.306643] sd 0:0:1:0: [sda] Mode Sense: 00 3a 00 00
[   26.306657] sd 0:0:1:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   26.306707] sd 0:0:1:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[   26.306715] sd 0:0:1:0: [sda] Write Protect is off
[   26.306717] sd 0:0:1:0: [sda] Mode Sense: 00 3a 00 00
[   26.306729] sd 0:0:1:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   26.306732]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   26.319476]  sda1 sda2 sda3 < sda5 >
[   26.362915] sd 0:0:1:0: [sda] Attached SCSI disk
[   26.362963] sd 2:0:0:0: [sdb] 312581808 512-byte hardware sectors (160042 MB)
[   26.362974] sd 2:0:0:0: [sdb] Write Protect is off
[   26.362976] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   26.362992] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   26.363118] sd 2:0:0:0: [sdb] 312581808 512-byte hardware sectors (160042 MB)
[   26.363127] sd 2:0:0:0: [sdb] Write Protect is off
[   26.363129] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   26.363146] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   26.363149]  sdb: sdb1 sdb2 sdb3
[   26.387608] sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[   26.387612] Uniform CD-ROM driver Revision: 3.20
[   26.387653] sr 0:0:0:0: Attached scsi CD-ROM sr0
[   26.403263] sd 2:0:0:0: [sdb] Attached SCSI disk
[   26.407269] sr 0:0:0:0: Attached scsi generic sg0 type 5
[   26.407288] sd 0:0:1:0: Attached scsi generic sg1 type 0
[   26.407305] sd 2:0:0:0: Attached scsi generic sg2 type 0
[   31.643739] usplash[1251]: segfault at b739c780 eip b7ef4ed2 esp bffab680 error 6
[   31.699371] kjournald starting.  Commit interval 5 seconds
[   31.699394] EXT3-fs: mounted filesystem with ordered data mode.
[   39.339731] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   39.524892] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   39.552945] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   39.744758] parport_pc 00:06: reported by Plug and Play ACPI
[   39.744803] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   39.779484] i2c-adapter i2c-0: nForce2 SMBus adapter at 0x600
[   39.779500] i2c-adapter i2c-1: nForce2 SMBus adapter at 0x700
[   39.820639] Linux agpgart interface v0.102
[   39.884695] input: Power Button (FF) as /devices/virtual/input/input3
[   39.909113] ACPI: Power Button (FF) [PWRF]
[   39.909197] input: Power Button (CM) as /devices/virtual/input/input4
[   39.940444] ACPI: Power Button (CM) [PWRB]
[   40.075761] nvidia: module license 'NVIDIA' taints kernel.
[   40.539802] ACPI: PCI Interrupt Link [LMC9] enabled at IRQ 11
[   40.539808] ACPI: PCI Interrupt 0000:00:0d.0[A] -> Link [LMC9] -> GSI 11 (level, low) -> IRQ 11
[   40.539814] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[   40.540068] NVRM: loading NVIDIA UNIX x86 Kernel Module  169.12  Thu Feb 14 17:53:07 PST 2008
[   40.997234] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 10
[   40.997238] PCI: setting IRQ 10 as level-triggered
[   40.997242] ACPI: PCI Interrupt 0000:00:05.0[B] -> Link [LAZA] -> GSI 10 (level, low) -> IRQ 10
[   40.997271] PCI: Setting latency timer of device 0000:00:05.0 to 64
[   41.030321] hda_codec: Unknown model for ALC662, trying auto-probe from BIOS...
[   41.124886] NET: Registered protocol family 10
[   41.125116] lo: Disabled Privacy Extensions
[   41.314248] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input5
[   42.092659] lp0: using parport0 (interrupt-driven).
[   42.445592] EXT3 FS on sdb1, internal journal
[   42.916504] kjournald starting.  Commit interval 5 seconds
[   42.916697] EXT3 FS on sdb2, internal journal
[   42.916702] EXT3-fs: mounted filesystem with ordered data mode.
[   43.455238] ip_tables: (C) 2000-2006 Netfilter Core Team


```

Esto me aparece en Debian
```
84-2709-4b30-8f2f-7c49044b551f ro quiet
mapped APIC to ffffb000 (fee00000)
mapped IOAPIC to ffffa000 (fec00000)
Enabling fast FPU save and restore... done.
Enabling unmasked SIMD FPU exception support... done.
Initializing CPU#0
PID hash table entries: 4096 (order: 12, 16384 bytes)
Detected 2210.105 MHz processor.
spurious 8259A interrupt: IRQ7.
Console: colour VGA+ 80x25
console [tty0] enabled
Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Memory: 897544k/917184k available (1752k kernel code, 18960k reserved, 723k data, 324k init, 0k highmem)
virtual kernel memory layout:
    fixmap  : 0xfffb3000 - 0xfffff000   ( 304 kB)
    vmalloc : 0xf8800000 - 0xfffb1000   ( 119 MB)
    lowmem  : 0xc0000000 - 0xf7fb0000   ( 895 MB)
      .init : 0xc036e000 - 0xc03bf000   ( 324 kB)
      .data : 0xc02b6005 - 0xc036ade4   ( 723 kB)
      .text : 0xc0100000 - 0xc02b6005   (1752 kB)
Checking if this processor honours the WP bit even in supervisor mode... Ok.
hpet clockevent registered
Calibrating delay using timer specific routine.. 4424.42 BogoMIPS (lpj=8848841)
Security Framework initialized
SELinux:  Disabled at boot.
Capability LSM initialized
Mount-cache hash table entries: 512
Initializing cgroup subsys ns
Initializing cgroup subsys cpuacct
CPU: After generic identify, caps: 178bfbff ebd3fbff 00000000 00000000 00002001 00000000 0000011f 00000000
CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
CPU: L2 Cache: 512K (64 bytes/line)
CPU: After all inits, caps: 178bfbff ebd3fbff 00000000 00000410 00002001 00000000 0000011f 00000000
Compat vDSO mapped to ffffe000.
CPU: AMD Athlon(tm) 64 X2 Dual Core Processor 4200+ stepping 02
Checking 'hlt' instruction... OK.
Freeing SMP alternatives: 0k freed
ACPI: Core revision 20070126
ACPI: setting ELCR to 0200 (from 0c20)
ExtINT not setup in hardware but reported by MP table
ENABLING IO-APIC IRQs
..TIMER: vector=0x31 apic1=0 pin1=2 apic2=0 pin2=0
net_namespace: 64 bytes
Booting paravirtualized kernel on bare hardware
NET: Registered protocol family 16
EISA bus registered
ACPI: bus type pci registered
PCI: BIOS Bug: MCFG area at e0000000 is not E820-reserved
PCI: Not using MMCONFIG.
PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=4
PCI: Using configuration type 1
Setting up standard PCI resources
ACPI: EC: Look up EC in DSDT
ACPI: Interpreter enabled
ACPI: (supports S0 S1 S3 S4 S5)
ACPI: Using PIC for interrupt routing
Error attaching device data
Error attaching device data
Error attaching device data
Error attaching device data
ACPI: PCI Root Bridge [PCI0] (0000:00)
PCI: Transparent bridge - 0000:00:04.0
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P2._PRT]
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR11._PRT]
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR12._PRT]
ACPI: PCI Interrupt Link [LNKA] (IRQs 5 7 10 11 14) *0, disabled.
ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7 10 11 14) *0, disabled.
ACPI: PCI Interrupt Link [LNKC] (IRQs 5 7 10 11 14) *0, disabled.
ACPI: PCI Interrupt Link [LNKD] (IRQs 5 7 10 11 14) *0, disabled.
ACPI: PCI Interrupt Link [LNEA] (IRQs 5 7 10 11 14) *0, disabled.
ACPI: PCI Interrupt Link [LNEB] (IRQs 5 7 10 11 14) *0, disabled.
ACPI: PCI Interrupt Link [LNEC] (IRQs 5 7 10 11 14) *0, disabled.
ACPI: PCI Interrupt Link [LNED] (IRQs 5 7 10 11 14) *0, disabled.
ACPI: PCI Interrupt Link [LUB0] (IRQs *5 7 10 11 14)
ACPI: PCI Interrupt Link [LUB2] (IRQs 5 7 10 *11 14)
ACPI: PCI Interrupt Link [LMAC] (IRQs *5 7 10 11 14)
ACPI: PCI Interrupt Link [LAZA] (IRQs 5 7 *10 11 14)
ACPI: PCI Interrupt Link [LACI] (IRQs 5 7 10 11 14) *0, disabled.
ACPI: PCI Interrupt Link [LMC9] (IRQs 5 7 10 *11 14)
ACPI: PCI Interrupt Link [LSMB] (IRQs 5 7 *10 11 14)
ACPI: PCI Interrupt Link [LPMU] (IRQs 5 7 10 11 14) *0, disabled.
ACPI: PCI Interrupt Link [LSA0] (IRQs 5 7 10 *11 14)
ACPI: PCI Interrupt Link [LSA1] (IRQs 5 7 10 11 14) *0, disabled.
ACPI: PCI Interrupt Link [LATA] (IRQs 5 7 10 11 14) *0, disabled.
ACPI Warning (tbutils-0217): Incorrect checksum in table [OEMB] -  58, should be 4B [20070126]
Linux Plug and Play Support v0.97 (c) Adam Belay
pnp: PnP ACPI init
ACPI: bus type pnp registered
pnp: PnP ACPI: found 16 devices
ACPI: ACPI bus type pnp unregistered
PnPBIOS: Disabled by ACPI PNP
PCI: Using ACPI for IRQ routing
PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
NET: Registered protocol family 8
NET: Registered protocol family 20
hpet0: at MMIO 0xfed00000, IRQs 2, 8, 31
hpet0: 3 32-bit timers, 25000000 Hz
ACPI: RTC can wake from S4
Time: tsc clocksource has been installed.
system 00:07: ioport range 0xa30-0xa37 has been reserved
system 00:07: ioport range 0x4d0-0x4d1 has been reserved
system 00:07: ioport range 0x800-0x80f has been reserved
system 00:07: ioport range 0x500-0x57f has been reserved
system 00:07: ioport range 0x580-0x5ff has been reserved
system 00:07: ioport range 0x800-0x87f could not be reserved
system 00:07: ioport range 0x880-0x8ff has been reserved
system 00:07: ioport range 0xd00-0xd7f has been reserved
system 00:07: ioport range 0xd80-0xdff has been reserved
system 00:07: ioport range 0x900-0x97f has been reserved
system 00:07: ioport range 0x980-0x9ff has been reserved
system 00:07: ioport range 0x2000-0x207f has been reserved
system 00:07: ioport range 0x2080-0x20ff has been reserved
system 00:07: iomem range 0xfefe0000-0xfefe01ff has been reserved
system 00:07: iomem range 0xfefe1000-0xfefe1fff has been reserved
system 00:07: iomem range 0xfee01000-0xfeefffff could not be reserved
system 00:07: iomem range 0xffb80000-0xffffffff could not be reserved
system 00:07: iomem range 0xff300000-0xff3fffff has been reserved
system 00:09: iomem range 0xfec00000-0xfec00fff could not be reserved
system 00:09: iomem range 0xfee00000-0xfee00fff could not be reserved
system 00:09: iomem range 0x38000000-0x3fffffff has been reserved
system 00:0c: ioport range 0x230-0x23f has been reserved
system 00:0c: ioport range 0x290-0x29f has been reserved
system 00:0c: ioport range 0xa00-0xa0f has been reserved
system 00:0c: ioport range 0xa10-0xa1f has been reserved
system 00:0e: iomem range 0xe0000000-0xefffffff has been reserved
system 00:0f: iomem range 0x0-0x9ffff could not be reserved
system 00:0f: iomem range 0xc0000-0xcffff could not be reserved
system 00:0f: iomem range 0xe0000-0xfffff could not be reserved
system 00:0f: iomem range 0x100000-0x37ffffff could not be reserved
system 00:0f: iomem range 0xff700000-0xffffffff could not be reserved
PCI: Bridge: 0000:00:04.0
  IO window: disabled.
  MEM window: disabled.
  PREFETCH window: disabled.
PCI: Bridge: 0000:00:09.0
  IO window: disabled.
  MEM window: disabled.
  PREFETCH window: disabled.
PCI: Bridge: 0000:00:0b.0
  IO window: disabled.
  MEM window: disabled.
  PREFETCH window: disabled.
PCI: Bridge: 0000:00:0c.0
  IO window: disabled.
  MEM window: disabled.
  PREFETCH window: disabled.
PCI: Setting latency timer of device 0000:00:04.0 to 64
PCI: Setting latency timer of device 0000:00:09.0 to 64
PCI: Setting latency timer of device 0000:00:0b.0 to 64
PCI: Setting latency timer of device 0000:00:0c.0 to 64
NET: Registered protocol family 2
IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
TCP bind hash table entries: 65536 (order: 6, 262144 bytes)
TCP: Hash tables configured (established 131072 bind 65536)
TCP reno registered
checking if image is initramfs...<7>Switched to high resolution mode on CPU 0
 it is
Freeing initrd memory: 7927k freed
audit: initializing netlink socket (disabled)
audit(1216252061.788:1): initialized
Total HugeTLB memory allocated, 0
VFS: Disk quotas dquot_6.5.1
Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
io scheduler noop registered
io scheduler anticipatory registered
io scheduler deadline registered
io scheduler cfq registered (default)
Boot video device is 0000:00:0d.0
PCI: Setting latency timer of device 0000:00:09.0 to 64
assign_interrupt_mode Found MSI capability
Allocate Port Service[0000:00:09.0:pcie00]
PCI: Setting latency timer of device 0000:00:0b.0 to 64
assign_interrupt_mode Found MSI capability
Allocate Port Service[0000:00:0b.0:pcie00]
PCI: Setting latency timer of device 0000:00:0c.0 to 64
assign_interrupt_mode Found MSI capability
Allocate Port Service[0000:00:0c.0:pcie00]
isapnp: Scanning for PnP cards...
isapnp: No Plug & Play device found
hpet_resources: 0xfed00000 is busy
Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
00:0d: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
RAMDISK driver initialized: 16 RAM disks of 8192K size 1024 blocksize
PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
serio: i8042 KBD port at 0x60,0x64 irq 1
serio: i8042 AUX port at 0x60,0x64 irq 12
mice: PS/2 mouse device common for all mice
EISA: Probing bus 0 at eisa.0
Cannot allocate resource for EISA slot 2
EISA: Detected 0 cards.
cpuidle: using governor ladder
cpuidle: using governor menu
TCP bic registered
NET: Registered protocol family 1
NET: Registered protocol family 17
Using IPI Shortcut mode
registered taskstats version 1
Freeing unused kernel memory: 324k freed
input: AT Translated Set 2 keyboard as /class/input/input0
usbcore: registered new interface driver usbfs
usbcore: registered new interface driver hub
usbcore: registered new device driver usb
ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
ACPI: PCI Interrupt Link [LUB0] enabled at IRQ 5
PCI: setting IRQ 5 as level-triggered
ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [LUB0] -> GSI 5 (level, low) -> IRQ 5
PCI: Setting latency timer of device 0000:00:02.0 to 64
ohci_hcd 0000:00:02.0: OHCI Host Controller
ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
ohci_hcd 0000:00:02.0: irq 5, io mem 0xdffff000
Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
usb usb1: configuration #1 chosen from 1 choice
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 8 ports detected
ACPI: PCI Interrupt Link [LUB2] enabled at IRQ 11
PCI: setting IRQ 11 as level-triggered
ACPI: PCI Interrupt 0000:00:02.1[B] -> Link [LUB2] -> GSI 11 (level, low) -> IRQ 11
PCI: Setting latency timer of device 0000:00:02.1 to 64
ehci_hcd 0000:00:02.1: EHCI Host Controller
ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 2
ehci_hcd 0000:00:02.1: debug port 1
PCI: cache line size of 64 is not supported by device 0000:00:02.1
ehci_hcd 0000:00:02.1: irq 11, io mem 0xdfffec00
ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
usb usb2: configuration #1 chosen from 1 choice
hub 2-0:1.0: USB hub found
hub 2-0:1.0: 8 ports detected
Floppy drive(s): fd0 is 1.44M
FDC 0 is a post-1991 82077
forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 5
ACPI: PCI Interrupt 0000:00:07.0[A] -> Link [LMAC] -> GSI 5 (level, low) -> IRQ 5
PCI: Setting latency timer of device 0000:00:07.0 to 64
forcedeth 0000:00:07.0: ifname eth0, PHY OUI 0x1374 @ 1, addr 00:1e:8c:c8:41:66
forcedeth 0000:00:07.0: highdma pwrctl mgmt timirq gbit lnktim msi desc-v3
NFORCE-MCP61: IDE controller (0x10de:0x03ec rev 0xa2) at  PCI slot 0000:00:06.0
NFORCE-MCP61: not 100% native mode: will probe irqs later
NFORCE-MCP61: BIOS didn't set cable bits correctly. Enabling workaround.
NFORCE-MCP61: 0000:00:06.0 (rev a2) UDMA133 controller
    ide0: BM-DMA at 0xffa0-0xffa7, BIOS settings: hda:DMA, hdb:DMA
NFORCE-MCP61: IDE port disabled
Probing IDE interface ide0...
SCSI subsystem initialized
libata version 3.00 loaded.
usb 1-4: new full speed USB device using ohci_hcd and address 2
hdb: WDC WD1200BB-55GUC0, ATA DISK drive
usb 1-4: configuration #1 chosen from 1 choice
hda: PIONEER DVD-RW DVR-109, ATAPI CD/DVD-ROM drive
hda: host max PIO5 wanted PIO255(auto-tune) selected PIO4
hda: UDMA/66 mode selected
hda: set_drive_speed_status: status=0x51 { DriveReady SeekComplete Error }
hda: set_drive_speed_status: error=0x04 { AbortedCommand }
hda: host max PIO5 wanted PIO255(auto-tune) selected PIO4
hdb: host max PIO5 wanted PIO255(auto-tune) selected PIO4
hdb: UDMA/100 mode selected
ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
sata_nv 0000:00:08.0: version 3.5
ACPI: PCI Interrupt Link [LSA0] enabled at IRQ 11
ACPI: PCI Interrupt 0000:00:08.0[A] -> Link [LSA0] -> GSI 11 (level, low) -> IRQ 11
PCI: Setting latency timer of device 0000:00:08.0 to 64
scsi0 : sata_nv
scsi1 : sata_nv
ata1: SATA max UDMA/133 cmd 0xe400 ctl 0xe080 bmdma 0xd880 irq 11
ata2: SATA max UDMA/133 cmd 0xe000 ctl 0xdc00 bmdma 0xd888 irq 11
hda: ATAPI 40X DVD-ROM DVD-R CD-R/RW drive, 2000kB Cache
Uniform CD-ROM driver Revision: 3.20
hdb: max request size: 512KiB
hdb: 234441648 sectors (120034 MB) w/2048KiB Cache, CHS=16383/255/63
hdb: cache flushes supported
 hdb: hdb1 hdb2 hdb3 < hdb5 >
ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
ata1.00: ATA-7: Hitachi HDS721616PLA320, P22OABGA, max UDMA/133
ata1.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 0/32)
ata1.00: configured for UDMA/133
ata2: SATA link down (SStatus 0 SControl 300)
scsi 0:0:0:0: Direct-Access     ATA      Hitachi HDS72161 P22O PQ: 0 ANSI: 5
Driver 'sd' needs updating - please use bus_type methods
sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
sd 0:0:0:0: [sda] Write Protect is off
sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
sd 0:0:0:0: [sda] 312581808 512-byte hardware sectors (160042 MB)
sd 0:0:0:0: [sda] Write Protect is off
sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
 sda: sda1 sda2 sda3
sd 0:0:0:0: [sda] Attached SCSI disk
Attempting manual resume
swsusp: Marking nosave pages: 000000000009f000 - 0000000000100000
swsusp: Basic memory bitmaps created
swsusp: Basic memory bitmaps freed
kjournald starting.  Commit interval 5 seconds
EXT3-fs: mounted filesystem with ordered data mode.
input: Power Button (FF) as /class/input/input1
i2c-adapter i2c-0: nForce2 SMBus adapter at 0x600
i2c-adapter i2c-1: nForce2 SMBus adapter at 0x700
ACPI: Power Button (FF) [PWRF]
input: Power Button (CM) as /class/input/input2
ACPI: Power Button (CM) [PWRB]
input: PC Speaker as /class/input/input3
Real Time Clock Driver v1.12ac
ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 10
PCI: setting IRQ 10 as level-triggered
ACPI: PCI Interrupt 0000:00:05.0[B] -> Link [LAZA] -> GSI 10 (level, low) -> IRQ 10
PCI: Setting latency timer of device 0000:00:05.0 to 64
hda_codec: Unknown model for ALC662, trying auto-probe from BIOS...
input: ImPS/2 Generic Wheel Mouse as /class/input/input4
parport_pc 00:06: reported by Plug and Play ACPI
parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
Adding 1983988k swap on /dev/hdb5.  Priority:-1 extents:1 across:1983988k
Adding 2000084k swap on /dev/sda3.  Priority:-2 extents:1 across:2000084k
EXT3 FS on hdb1, internal journal
loop: module loaded
kjournald starting.  Commit interval 5 seconds
EXT3 FS on hdb2, internal journal
EXT3-fs: mounted filesystem with ordered data mode.


```

En debian figura un solo CPU, me quedé pensando en lo que dijo vor, le erré de versión? yo baje la debian-LennyBeta2-i386-netinst creo que esta bien no? podria haber bajado la verson para 64 bits pero como en Ubuntu tengo la de 32b bajé esa.

---

### Post by Hei Ku on 2008-07-16
fijate si no hay una SMP o un kernel q termine en SMP

---

### Post by pablo0469 on 2008-07-17
Creo que el error esta en que instalaste la version i386, que viene con una configuracion por defecto para andar decentemente en cualquier maquina, quizas deberias instalar algunos modulos del kernel que necesita tu micro, aca te pongo lo referente a los AMD que saque de una guia para adaptar lo mejor posible Debian/Ubuntu justamente a los micros Pentium y AMD:

[B]-Si tenemos un microprocesador AMD: 

**sudo aptitude install linux-image-k7 linux-restricted-modules-k7**

-Y si tenemos más de un micro AMD o un AMD que virtualize más de una CPU: 

**sudo aptitude install linux-image-k7-smp linux-restricted-modules-k7-smp**
[/B]          
En lo personal instale los modulos correspondientes a mi Pentium D y vaya que se noto la diferencia.

Ojala te sirva y Saludos.

---

### Post by Hei Ku on 2008-07-17
En tu caso deberías buscar modulos que digan k8, que es lo que correspondería a tu modelo de procesador. Aunque podría ser que esté dentro del modulo de k7, nunca se sabe con el esquema de nombres de Debian.

---

### Post by lega on 2008-07-17
En el caso de Ubuntu me dice que ese paquete no existe,```
No se pudo encontrar ningún paquete cuyo nombre o descripción coincida con "linux-image-k7-smp"
No se pudo encontrar ningún paquete cuyo nombre o descripción coincida con "linux-restricted-modules-k7-smp"
No se pudo encontrar ningún paquete cuyo nombre o descripción coincida con "linux-image-k7-smp"
No se pudo encontrar ningún paquete cuyo nombre o descripción coincida con "linux-restricted-modules-k7-smp"
No se instalará, actualizará o eliminará ningún paquete.
0 paquetes actualizados, 0 nuevos instalados, 0 para eliminar y 0 sin actualizar.

```
Ahora inicio con Debian y me fijo, tampoco hay ningun paquete que diga k8 en Ubuntu

**Edit**, en Debian me tira lo mismo, por ahí hay que agregar algun repositorio, en fin, ya está, voy a ver si hay alguna versión que diga smp.
Gracias.

---

### Post by pablo0469 on 2008-07-18
Es cierto que ese no esta, tampoco encuentro ningun k8, pero a "linux-restricted-modules-k7" si lo tengo en mis repositorios. Mucho mas no puedo ayudarte, esto es demasiado finito para mis conocimientos de informatica.

Quizas en Debian este todo, ya sabemos que tiene repositorios mas extensos que Ubuntu. 

Creo que lo mejor que deberias hacer es instalar alguna arquitectura mas acorde con tu micro (con todos los modulos necesarios preinstalados), tengo entendido que las versiones i386 suelen traer este tipo de problemas con micros multiples.

Y amen de este traspie aprovecho para preguntarte si es cierto que Lenny anda sorprendentemente rapido en comparacion a otras distros "de punta".

Saludos.

---

### Post by lega on 2008-07-18
> **pablo0469 said:**
> 
Y amen de este traspie aprovecho para preguntarte si es cierto que Lenny anda sorprendentemente rapido en comparacion a otras distros "de punta".

Saludos.

Mirá, yo no he notado una "gran diferencia" en cuanto a velocidad con respecto a Hardy, puede ser porque no tengo instalada la version correcta y no me detecta bien el micro, pero incluso noto mas rápido a Hardy con Compiz Fusion instalado, en Lenny tampoco tengo instalado los drivers de nvidia, puede ser también por eso que no tenga el rendimiento adecuado,no sé, voy a ver  si busco una version para el micro que tengo.
Saludos

---

