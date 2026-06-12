---
title: "How do you make screendumps on Installation process?"
date: 2007-03-23
forum: The Cafe
---

### Post by jingo811 on 2007-03-23
I want to make my own Ubuntu installation Tutorial for beginners.
How do you make screendumps on Installation process?  Is that even possible, maybe there's some program one could use or some open-source images that's already made for these purposes?

---

### Post by stokedfish on 2007-03-23
Install Ubuntu in VMWare or Virtualbox.

---

### Post by maniacmusician on 2007-03-23
Yeah. I'm actually doing that right now too, as a part of my "Switching to Linux" series.

---

### Post by jingo811 on 2007-03-23
Need help Mr.Wizard!

```
taco@Einstein:~/Desktop/src$ **sudo dpkg -i VirtualBox_1.3.8_Ubuntu_dapper_i386.deb**
Selecting previously deselected package virtualbox.
(Reading database ... 86881 files and directories currently installed.)
Unpacking virtualbox (from VirtualBox_1.3.8_Ubuntu_dapper_i386.deb) ...
virtualbox-puel-1-2 license has already been accepted.
Setting up virtualbox (1.3.8_Ubuntu_dapper) ...
 * Starting VirtualBox kernel module vboxdrv FATAL: Module vboxdrv not found.

[COLOR="Red"] * [/COLOR]Modprobe vboxdrv failed. Please use 'dmesg' to find out why.

taco@Einstein:~/Desktop/src$** dmesg**
```

What am I supposed to look for in the dmesg ERROR table, and how do I proceed further when I've found the problem line?
That's one BIG list if you ask me :-s
```
[17179569.184000] Linux version 2.6.15-28-386 (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Thu Feb 1 15:51:56 UTC 2007
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[17179569.184000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000e0000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000001ffd0000 (usable)
[17179569.184000]  BIOS-e820: 000000001ffd0000 - 000000001ffde000 (ACPI data)
[17179569.184000]  BIOS-e820: 000000001ffde000 - 0000000020000000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fee00000 - 00000000fef00000 (reserved)
[17179569.184000]  BIOS-e820: 00000000ff780000 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 511MB LOWMEM available.
[17179569.184000] found SMP MP-table at 000ff780
[17179569.184000] On node 0 totalpages: 131024
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   DMA32 zone: 0 pages, LIFO batch:0
[17179569.184000]   Normal zone: 126928 pages, LIFO batch:31
[17179569.184000]   HighMem zone: 0 pages, LIFO batch:0
[17179569.184000] DMI present.
[17179569.184000] ACPI: RSDP (v000 ACPIAM                                ) @ 0x000f9830
[17179569.184000] ACPI: RSDT (v001 A M I  OEMRSDT  0x05000615 MSFT 0x00000097) @ 0x1ffd0000
[17179569.184000] ACPI: FADT (v002 A M I  OEMFACP  0x05000615 MSFT 0x00000097) @ 0x1ffd0200
[17179569.184000] ACPI: MADT (v001 A M I  OEMAPIC  0x05000615 MSFT 0x00000097) @ 0x1ffd0390
[17179569.184000] ACPI: MCFG (v001 A M I  OEMMCFG  0x05000615 MSFT 0x00000097) @ 0x1ffd0400
[17179569.184000] ACPI: OEMB (v001 A M I  AMI_OEM  0x05000615 MSFT 0x00000097) @ 0x1ffde040
[17179569.184000] ACPI: DSDT (v001  1ADGH 1ADGH004 0x00000004 INTL 0x20051117) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x2008
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[17179569.184000] Processor #0 15:15 APIC version 16
[17179569.184000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x81] disabled)
[17179569.184000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[17179569.184000] IOAPIC[0]: apic_id 1, version 17, address 0xfec00000, GSI 0-23[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[17179569.184000] ACPI: BIOS IRQ0 pin2 override ignored.
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[17179569.184000] ACPI: IRQ9 used by override.
[17179569.184000] ACPI: IRQ14 used by override.
[17179569.184000] ACPI: IRQ15 used by override.
[17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[17179569.184000] Using ACPI (MADT) for SMP configuration information
[17179569.184000] Allocating PCI resources starting at 30000000 (gap: 20000000:dec00000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/sda2 ro quiet splash
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 2048 (order: 11, 32768 bytes)
[17179569.184000] Detected 1608.466 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179570.704000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[17179570.704000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)[17179570.716000] Memory: 508724k/524096k available (1977k kernel code, 14800k reserved, 605k data, 288k init, 0k highmem)
[17179570.716000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179570.796000] Calibrating delay using timer specific routine.. 3220.98 BogoMIPS (lpj=6441966)
[17179570.796000] Security Framework v1.0.0 initialized
[17179570.796000] SELinux:  Disabled at boot.
[17179570.796000] Mount-cache hash table entries: 512
[17179570.796000] CPU: After generic identify, caps: 078bfbff ebd3fbff 00000000 00000000 00002001 00000000 00000019
[17179570.796000] CPU: After vendor identify, caps: 078bfbff ebd3fbff 00000000 00000000 00002001 00000000 00000019
[17179570.796000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[17179570.796000] CPU: L2 Cache: 256K (64 bytes/line)
[17179570.796000] CPU: After all inits, caps: 078bfbff ebd3fbff 00000000 00000410 00002001 00000000 00000019
[17179570.796000] mtrr: v2.0 (20020519)
[17179570.796000] CPU: AMD Sempron(tm) Processor 3000+ stepping 02
[17179570.796000] Enabling fast FPU save and restore... done.
[17179570.796000] Enabling unmasked SIMD FPU exception support... done.
[17179570.796000] Checking 'hlt' instruction... OK.
[17179570.812000] checking if image is initramfs... it is
[17179571.416000] Freeing initrd memory: 6616k freed
[17179571.420000] ACPI: Looking for DSDT ... not found!
[17179571.424000] ENABLING IO-APIC IRQs
[17179571.424000] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
[17179571.572000] NET: Registered protocol family 16
[17179571.572000] EISA bus registered
[17179571.572000] ACPI: bus type pci registered
[17179571.572000] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=6
[17179571.572000] PCI: Using MMCONFIG
[17179571.572000] ACPI: Subsystem revision 20051216
[17179571.580000] ACPI: Interpreter enabled
[17179571.580000] ACPI: Using IOAPIC for interrupt routing
[17179571.580000] Error attaching device data
[17179571.580000] Error attaching device data
[17179571.580000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179571.580000] PCI: Probing PCI hardware (bus 00)
[17179571.588000] PCI: Transparent bridge - 0000:00:06.0
[17179571.588000] Boot video device is 0000:06:00.0
[17179571.588000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179571.612000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[17179571.612000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR10._PRT]
[17179571.612000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR11._PRT]
[17179571.612000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR12._PRT]
[17179571.612000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR13._PRT]
[17179571.612000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR14._PRT]
[17179571.616000] ACPI: PCI Interrupt Link [LNKA] (IRQs 16 17 18 19) *0, disabled.
[17179571.616000] ACPI: PCI Interrupt Link [LNKB] (IRQs 16 17 18 19) *0, disabled.
[17179571.616000] ACPI: PCI Interrupt Link [LNKC] (IRQs 16 17 18 19) *0, disabled.
[17179571.616000] ACPI: PCI Interrupt Link [LNKD] (IRQs 16 17 18 19) *0, disabled.
[17179571.616000] ACPI: PCI Interrupt Link [LNEA] (IRQs 16 17 18 19) *0, disabled.
[17179571.616000] ACPI: PCI Interrupt Link [LNEB] (IRQs 16 17 18 19) *10
[17179571.616000] ACPI: PCI Interrupt Link [LNEC] (IRQs 16 17 18 19) *0, disabled.
[17179571.620000] ACPI: PCI Interrupt Link [LNED] (IRQs 16 17 18 19) *0, disabled.
[17179571.620000] ACPI: PCI Interrupt Link [LUB0] (IRQs 20 21 22 23) *10
[17179571.620000] ACPI: PCI Interrupt Link [LMAD] (IRQs 20 21 22 23) *0, disabled.
[17179571.620000] ACPI: PCI Interrupt Link [LUB2] (IRQs 20 21 22 23) *11
[17179571.620000] ACPI: PCI Interrupt Link [LMAC] (IRQs 20 21 22 23) *5
[17179571.620000] ACPI: PCI Interrupt Link [LAZA] (IRQs 20 21 22 23) *11
[17179571.620000] ACPI: PCI Interrupt Link [LSMB] (IRQs 20 21 22 23) *11
[17179571.624000] ACPI: PCI Interrupt Link [LPMU] (IRQs 20 21 22 23) *5
[17179571.624000] ACPI: PCI Interrupt Link [LSA0] (IRQs 20 21 22 23) *5
[17179571.624000] ACPI: PCI Interrupt Link [LSA1] (IRQs 20 21 22 23) *10
[17179571.624000] ACPI: PCI Interrupt Link [LATA] (IRQs 20 21 22 23) *0, disabled.
[17179571.624000] ACPI: PCI Interrupt Link [LSA2] (IRQs 20 21 22 23) *10
[17179571.624000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179571.624000] pnp: PnP ACPI init
[17179571.632000] pnp: PnP ACPI: found 13 devices
[17179571.632000] PnPBIOS: Disabled by ACPI PNP
[17179571.632000] PCI: Using ACPI for IRQ routing
[17179571.632000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179571.644000] pnp: 00:0a: ioport range 0xa00-0xa0f has been reserved
[17179571.644000] pnp: 00:0a: ioport range 0xa10-0xa1f has been reserved
[17179571.644000] PCI: Bridge: 0000:00:06.0
[17179571.644000]   IO window: disabled.
[17179571.644000]   MEM window: disabled.
[17179571.644000]   PREFETCH window: disabled.
[17179571.644000] PCI: Bridge: 0000:00:0b.0
[17179571.644000]   IO window: disabled.
[17179571.644000]   MEM window: disabled.
[17179571.644000]   PREFETCH window: disabled.
[17179571.644000] PCI: Bridge: 0000:00:0c.0
[17179571.644000]   IO window: disabled.
[17179571.644000]   MEM window: disabled.
[17179571.644000]   PREFETCH window: disabled.
[17179571.644000] PCI: Bridge: 0000:00:0d.0
[17179571.644000]   IO window: disabled.
[17179571.644000]   MEM window: disabled.
[17179571.644000]   PREFETCH window: disabled.
[17179571.644000] PCI: Bridge: 0000:00:0e.0
[17179571.644000]   IO window: disabled.
[17179571.644000]   MEM window: disabled.
[17179571.644000]   PREFETCH window: disabled.
[17179571.644000] PCI: Bridge: 0000:00:0f.0
[17179571.644000]   IO window: disabled.
[17179571.644000]   MEM window: fc000000-febfffff
[17179571.644000]   PREFETCH window: d0000000-dfffffff
[17179571.644000] PCI: Setting latency timer of device 0000:00:06.0 to 64
[17179571.644000] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[17179571.644000] PCI: Setting latency timer of device 0000:00:0c.0 to 64
[17179571.644000] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[17179571.644000] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[17179571.644000] PCI: Setting latency timer of device 0000:00:0f.0 to 64
[17179571.644000] audit: initializing netlink socket (disabled)
[17179571.644000] audit(1174673127.644:1): initialized
[17179571.644000] VFS: Disk quotas dquot_6.5.1
[17179571.644000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179571.644000] Initializing Cryptographic API
[17179571.644000] io scheduler noop registered
[17179571.644000] io scheduler anticipatory registered
[17179571.644000] io scheduler deadline registered
[17179571.644000] io scheduler cfq registered
[17179572.164000] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[17179572.164000] pcie_portdrv_probe->Dev[0374:10de] has invalid IRQ. Check vendor BIOS
[17179572.164000] assign_interrupt_mode Found MSI capability
[17179572.164000] Allocate Port Service[pcie00]
[17179572.164000] Allocate Port Service[pcie03]
[17179572.164000] PCI: Setting latency timer of device 0000:00:0c.0 to 64
[17179572.164000] pcie_portdrv_probe->Dev[0374:10de] has invalid IRQ. Check vendor BIOS
[17179572.164000] assign_interrupt_mode Found MSI capability
[17179572.164000] Allocate Port Service[pcie00]
[17179572.164000] Allocate Port Service[pcie03]
[17179572.164000] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[17179572.164000] pcie_portdrv_probe->Dev[0378:10de] has invalid IRQ. Check vendor BIOS
[17179572.164000] assign_interrupt_mode Found MSI capability
[17179572.164000] Allocate Port Service[pcie00]
[17179572.164000] Allocate Port Service[pcie03]
[17179572.164000] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[17179572.164000] pcie_portdrv_probe->Dev[0375:10de] has invalid IRQ. Check vendor BIOS
[17179572.164000] assign_interrupt_mode Found MSI capability
[17179572.164000] Allocate Port Service[pcie00]
[17179572.164000] Allocate Port Service[pcie03]
[17179572.164000] PCI: Setting latency timer of device 0000:00:0f.0 to 64
[17179572.164000] pcie_portdrv_probe->Dev[0377:10de] has invalid IRQ. Check vendor BIOS
[17179572.164000] assign_interrupt_mode Found MSI capability
[17179572.164000] Allocate Port Service[pcie00]
[17179572.164000] Allocate Port Service[pcie03]
[17179572.164000] isapnp: Scanning for PnP cards...
[17179572.516000] isapnp: No Plug & Play device found
[17179572.532000] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[17179572.532000] PNP: PS/2 controller doesn't have AUX irq; using default 12
[17179572.532000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179572.532000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179572.532000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[17179572.532000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179572.532000] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[17179572.536000] 00:04: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179572.536000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179572.536000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179572.536000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179572.536000] mice: PS/2 mouse device common for all mice
[17179572.536000] EISA: Probing bus 0 at eisa.0
[17179572.536000] Cannot allocate resource for EISA slot 2
[17179572.536000] EISA: Detected 0 cards.
[17179572.536000] NET: Registered protocol family 2
[17179572.576000] IP route cache hash table entries: 8192 (order: 3, 32768 bytes)
[17179572.576000] TCP established hash table entries: 32768 (order: 5, 131072 bytes)
[17179572.576000] TCP bind hash table entries: 32768 (order: 5, 131072 bytes)
[17179572.576000] TCP: Hash tables configured (established 32768 bind 32768)
[17179572.576000] TCP reno registered
[17179572.576000] TCP bic registered
[17179572.576000] NET: Registered protocol family 1
[17179572.576000] NET: Registered protocol family 8
[17179572.576000] NET: Registered protocol family 20
[17179572.576000] Using IPI Shortcut mode
[17179572.576000] ACPI wakeup devices:
[17179572.576000] PS2K NSMB USB0 USB2 NMAC NMAD P0P1 HDAC BR10 BR11 BR12 BR13 BR14 BR15
[17179572.576000] ACPI: (supports S0 S1 S3 S4 S5)
[17179572.576000] Freeing unused kernel memory: 288k freed
[17179572.580000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179572.620000] vga16fb: initializing
[17179572.620000] vga16fb: mapped to 0xc00a0000
[17179572.824000] Console: switching to colour frame buffer device 80x25
[17179572.824000] fb0: VGA16 VGA frame buffer device
[17179573.892000] Capability LSM initialized
[17179574.608000] SCSI subsystem initialized
[17179574.612000] ACPI: bus type scsi registered
[17179574.612000] libata version 1.20 loaded.
[17179574.612000] sata_nv 0000:00:05.0: version 0.8
[17179574.612000] **** SET: Misaligned resource pointer: dfc2c902 Type 07 Len 0
[17179574.612000] ACPI: PCI Interrupt Link [LSA0] enabled at IRQ 23
[17179574.612000] ACPI: PCI Interrupt 0000:00:05.0[A] -> Link [LSA0] -> GSI 23 (level, low) -> IRQ 225
[17179574.612000] PCI: Setting latency timer of device 0000:00:05.0 to 64
[17179574.612000] ata1: SATA max UDMA/133 cmd 0xE800 ctl 0xE482 bmdma 0xE000 irq 225
[17179574.612000] ata2: SATA max UDMA/133 cmd 0xE400 ctl 0xE082 bmdma 0xE008 irq 225
[17179574.980000] ata1: dev 0 cfg 00:0040 49:2f00 82:7c6b 83:5b09 84:4673 85:7c69 86:1a21 87:4663 88:407f 93:0000
[17179574.980000] ata1: dev 0 ATA-7, max UDMA/133, 160086528 sectors: LBA
[17179574.980000] sata_get_dev_handle: SATA dev addr=0x50000, handle=0xdffb7e60
[17179574.988000] ata1: dev 0 configured for UDMA/133
[17179574.988000] sata_get_dev_handle: SATA dev addr=0x50000, handle=0xdffb7e60
[17179574.996000] scsi0 : sata_nv
[17179575.200000] ata2: no device found (phy stat 00000000)
[17179575.200000] scsi1 : sata_nv
[17179575.200000]   Vendor: ATA       Model: Maxtor 6L080M0    Rev: BACE
[17179575.200000]   Type:   Direct-Access                      ANSI SCSI revision: 05
[17179575.200000] **** SET: Misaligned resource pointer: dfc2c702 Type 07 Len 0
[17179575.200000] ACPI: PCI Interrupt Link [LSA1] enabled at IRQ 22
[17179575.200000] ACPI: PCI Interrupt 0000:00:05.1[B] -> Link [LSA1] -> GSI 22 (level, low) -> IRQ 233
[17179575.200000] PCI: Setting latency timer of device 0000:00:05.1 to 64
[17179575.200000] ata3: SATA max UDMA/133 cmd 0xDC00 ctl 0xD882 bmdma 0xD400 irq 233
[17179575.200000] ata4: SATA max UDMA/133 cmd 0xD800 ctl 0xD482 bmdma 0xD408 irq 233
[17179575.204000] Driver 'sd' needs updating - please use bus_type methods
[17179575.204000] SCSI device sda: 160086528 512-byte hdwr sectors (81964 MB)
[17179575.204000] SCSI device sda: drive cache: write back
[17179575.208000] SCSI device sda: 160086528 512-byte hdwr sectors (81964 MB)
[17179575.208000] SCSI device sda: drive cache: write back
[17179575.208000]  sda: sda1 sda2 sda3 sda4
[17179575.244000] sd 0:0:0:0: Attached scsi disk sda
[17179575.404000] ata3: no device found (phy stat 00000000)
[17179575.404000] scsi2 : sata_nv
[17179575.608000] ata4: no device found (phy stat 00000000)
[17179575.608000] scsi3 : sata_nv
[17179575.608000] **** SET: Misaligned resource pointer: dfc2c602 Type 07 Len 0
[17179575.608000] ACPI: PCI Interrupt Link [LSA2] enabled at IRQ 21
[17179575.608000] ACPI: PCI Interrupt 0000:00:05.2[C] -> Link [LSA2] -> GSI 21 (level, low) -> IRQ 50
[17179575.608000] PCI: Setting latency timer of device 0000:00:05.2 to 64
[17179575.608000] ata5: SATA max UDMA/133 cmd 0xD080 ctl 0xD002 bmdma 0xC800 irq 50
[17179575.608000] ata6: SATA max UDMA/133 cmd 0xCC00 ctl 0xC882 bmdma 0xC808 irq 50
[17179575.812000] ata5: no device found (phy stat 00000000)
[17179575.812000] scsi4 : sata_nv
[17179576.016000] ata6: no device found (phy stat 00000000)
[17179576.016000] scsi5 : sata_nv
[17179576.016000] NFORCE-MCP55: IDE controller at PCI slot 0000:00:04.0
[17179576.016000] NFORCE-MCP55: chipset revision 161
[17179576.016000] NFORCE-MCP55: not 100% native mode: will probe irqs later
[17179576.016000] NFORCE-MCP55: BIOS didn't set cable bits correctly. Enabling workaround.
[17179576.016000] NFORCE-MCP55: 0000:00:04.0 (rev a1) UDMA133 controller
[17179576.016000]     ide0: BM-DMA at 0xffa0-0xffa7, BIOS settings: hda:DMA, hdb:pio
[17179576.016000] Probing IDE interface ide0...
[17179576.752000] hda: Optiarc DVD RW AD-5170A, ATAPI CD/DVD-ROM drive
[17179577.424000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179577.432000] hda: ATAPI 48X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(66)
[17179577.432000] Uniform CD-ROM driver Revision: 3.20
[17179577.548000] usbcore: registered new driver usbfs
[17179577.548000] usbcore: registered new driver hub
[17179577.548000] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[17179577.552000] **** SET: Misaligned resource pointer: dfa87cc2 Type 07 Len 0
[17179577.552000] ACPI: PCI Interrupt Link [LUB0] enabled at IRQ 20
[17179577.552000] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [LUB0] -> GSI 20 (level, low) -> IRQ 58
[17179577.552000] PCI: Setting latency timer of device 0000:00:02.0 to 64
[17179577.552000] ohci_hcd 0000:00:02.0: OHCI Host Controller
[17179577.644000] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
[17179577.644000] ohci_hcd 0000:00:02.0: irq 58, io mem 0xfbffb000
[17179577.672000] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.54.
[17179577.700000] hub 1-0:1.0: USB hub found
[17179577.700000] hub 1-0:1.0: 10 ports detected
[17179577.804000] **** SET: Misaligned resource pointer: dfa879c2 Type 07 Len 0
[17179577.804000] ACPI: PCI Interrupt Link [LUB2] enabled at IRQ 23
[17179577.804000] ACPI: PCI Interrupt 0000:00:02.1[B] -> Link [LUB2] -> GSI 23 (level, low) -> IRQ 225
[17179577.804000] PCI: Setting latency timer of device 0000:00:02.1 to 64
[17179577.804000] ehci_hcd 0000:00:02.1: EHCI Host Controller
[17179577.804000] ehci_hcd 0000:00:02.1: debug port 1
[17179577.804000] PCI: cache line size of 64 is not supported by device 0000:00:02.1
[17179577.804000] ehci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 2
[17179577.804000] ehci_hcd 0000:00:02.1: irq 225, io mem 0xfbffac00
[17179577.804000] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179577.804000] hub 2-0:1.0: USB hub found
[17179577.804000] hub 2-0:1.0: 10 ports detected
[17179577.908000] **** SET: Misaligned resource pointer: dfa876c2 Type 07 Len 0
[17179577.908000] ACPI: PCI Interrupt Link [LMAC] enabled at IRQ 22
[17179577.908000] ACPI: PCI Interrupt 0000:00:08.0[A] -> Link [LMAC] -> GSI 22 (level, low) -> IRQ 233
[17179577.908000] PCI: Setting latency timer of device 0000:00:08.0 to 64
[17179577.908000] forcedeth: using HIGHDMA
[17179578.148000] ohci_hcd 0000:00:02.0: wakeup
[17179578.428000] eth0: forcedeth.c: subsystem: 01462:7250 bound to 0000:00:08.0[17179578.444000] Probing IDE interface ide1...
[17179578.532000] usb 1-2: new low speed USB device using ohci_hcd and address 2[17179578.760000] usbcore: registered new driver hiddev
[17179578.768000] input: A4Tech USB Optical Mouse as /class/input/input1
[17179578.768000] input: USB HID v1.10 Mouse [A4Tech USB Optical Mouse] on usb-0000:00:02.0-2
[17179578.768000] usbcore: registered new driver usbhid
[17179578.768000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[17179579.048000] Attempting manual resume
[17179579.060000] kjournald starting.  Commit interval 5 seconds
[17179579.060000] EXT3-fs: mounted filesystem with ordered data mode.
[17179584.536000] ts: Compaq touchscreen protocol output
[17179584.892000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[17179586.900000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179586.904000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179587.212000] NET: Registered protocol family 17
[17179587.224000] **** SET: Misaligned resource pointer: dc236bc2 Type 07 Len 0
[17179587.224000] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 21
[17179587.224000] ACPI: PCI Interrupt 0000:00:06.1[B] -> Link [LAZA] -> GSI 21 (level, low) -> IRQ 50
[17179587.224000] PCI: Setting latency timer of device 0000:00:06.1 to 64
[17179587.228000] Real Time Clock Driver v1.12
[17179587.480000] input: PC Speaker as /class/input/input2
[17179587.516000] irda_init()
[17179587.516000] NET: Registered protocol family 23
[17179587.608000] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[17179587.684000] parport: PnPBIOS parport detected.
[17179587.684000] parport0: PC-style at 0x378, irq 7 [PCSPP]
[17179587.704000] Linux agpgart interface v0.101 (c) Dave Jones
[17179587.720000] nvidia: module license 'NVIDIA' taints kernel.
[17179587.824000] **** SET: Misaligned resource pointer: daa19202 Type 07 Len 0
[17179587.824000] ACPI: PCI Interrupt Link [LNEB] enabled at IRQ 19
[17179587.824000] ACPI: PCI Interrupt 0000:06:00.0[A] -> Link [LNEB] -> GSI 19 (level, low) -> IRQ 90
[17179587.824000] PCI: Setting latency timer of device 0000:06:00.0 to 64
[17179587.824000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-8776  Mon Oct 16 21:56:04 PDT 2006
[17179588.512000] lp0: using parport0 (interrupt-driven).
[17179588.564000] Adding 1614524k swap on /dev/sda3.  Priority:-1 extents:1 across:1614524k
[17179588.736000] EXT3 FS on sda2, internal journal
[17179588.896000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[17179588.896000] md: bitmap version 4.39
[17179589.644000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@redhat.com
[17179590.336000] cdrom: open failed.
[17179590.816000] kjournald starting.  Commit interval 5 seconds
[17179590.816000] EXT3 FS on sda4, internal journal
[17179590.816000] EXT3-fs: mounted filesystem with ordered data mode.
[17179590.872000] NTFS driver 2.1.25 [Flags: R/O MODULE].
[17179590.928000] NTFS volume version 3.1.
[17179591.936000] ACPI: Power Button (FF) [PWRF]
[17179591.936000] ACPI: Power Button (CM) [PWRB]
[17179592.032000] ibm_acpi: ec object not found
[17179592.060000] pcc_acpi: loading...
[17179592.560000] powernow-k8: Power state transitions not supported
[17179599.232000] ppdev: user-space parallel port driver
[17179599.480000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[17179599.480000] apm: overridden by ACPI.
[17179599.692000] Bluetooth: Core ver 2.8
[17179599.692000] NET: Registered protocol family 31
[17179599.692000] Bluetooth: HCI device and connection manager initialized
[17179599.692000] Bluetooth: HCI socket layer initialized
[17179599.812000] Bluetooth: L2CAP ver 2.8
[17179599.812000] Bluetooth: L2CAP socket layer initialized
[17179599.820000] Bluetooth: RFCOMM socket layer initialized
[17179599.820000] Bluetooth: RFCOMM TTY layer initialized
[17179599.820000] Bluetooth: RFCOMM ver 1.7
[17179634.896000] NET: Registered protocol family 10
[17179634.900000] lo: Disabled Privacy Extensions
[17179634.900000] IPv6 over IPv4 tunneling driver
[17179645.676000] eth0: no IPv6 routers present
[17179704.920000] Warning: /proc/ide/hd?/settings interface is obsolete, and will be removed soon!
[17179767.116000] ISO 9660 Extensions: Microsoft Joliet Level 3
[17179767.228000] ISO 9660 Extensions: RRIP_1991A
[17180025.092000] ibm_acpi: ec object not found
taco@Einstein:~/Desktop/src$
```

---

### Post by jingo811 on 2007-03-24
Never mind solved it 
[http://www.ubuntugeek.com/create-and-manage-virtual-machines-using-virtualbox.html](http://www.ubuntugeek.com/create-and-manage-virtual-machines-using-virtualbox.html)
that guy is a god.

---

