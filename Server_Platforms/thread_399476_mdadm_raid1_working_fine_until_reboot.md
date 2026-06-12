---
title: "mdadm raid1 working fine until reboot"
date: 2007-04-02
forum: Server Platforms
---

### Post by cprophecy on 2007-04-02
I've managed to get 2 sata drives on a Sil3114 controller in a raid1 array up and running with mdadm. My only problem now is that I cannot seem to make it remain working after a reboot. Whenever i reboot, /dev/md0 totally disappears. The only way to get my array back is to run the command:

```
sudo mdadm --assemble --auto=yes /dev/md0 /dev/sda1 /dev/sdb1
```

This is my mdadm.conf:


```
DEVICE		partitions
ARRAY		/dev/md0 devices=/dev/sda1,/dev/sdb1 level=raid1 num-devices=2 UUID=497368ee:2605885f:7a03036a:f557219a
##CREATE	owner=root group=disk mode=0660 auto=yes
```

I've tried uncommenting the CREATE line
on the DEVICE line, instead of partitions i've tried using /dev/sda1 /dev/sdb1
on the ARRAY line i've tried it without the device=/dev/sda1,/dev/sdb1

I've seen similar issues in a few posts around the forums.. I'm just not entirely sure I'm having the same issue, and I'm having trouble determining what exactly is causing this. I found a post here: 

[http://ubuntuforums.org/showthread.php?t=89432&highlight=mdadm](http://ubuntuforums.org/showthread.php?t=89432&highlight=mdadm) 

which the user states he is getting this error message:

```
mdadm: no devices found for /dev/md0 [fail]
```

I have checked my dmesg and i see nothing that relates to mdadm.

```
[17179569.184000] Linux version 2.6.17-11-generic (root@terranova) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Thu Feb 1 19:52:28 UTC 2007 (Ubuntu 2.6.17-11.35-generic)
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009ec00 (usable)
[17179569.184000]  BIOS-e820: 000000000009ec00 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000003fff0000 (usable)
[17179569.184000]  BIOS-e820: 000000003fff0000 - 000000003fff3000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 000000003fff3000 - 0000000040000000 (ACPI data)
[17179569.184000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[17179569.184000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[17179569.184000] 127MB HIGHMEM available.
[17179569.184000] 896MB LOWMEM available.
[17179569.184000] On node 0 totalpages: 262128
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   Normal zone: 225280 pages, LIFO batch:31
[17179569.184000]   HighMem zone: 32752 pages, LIFO batch:7
[17179569.184000] DMI 2.2 present.
[17179569.184000] ACPI: RSDP (v000 Nvidia                                ) @ 0x000f6b00
[17179569.184000] ACPI: RSDT (v001 Nvidia AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x3fff3000
[17179569.184000] ACPI: FADT (v001 Nvidia AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x3fff3040
[17179569.184000] ACPI: MADT (v001 Nvidia AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x3fff79c0
[17179569.184000] ACPI: DSDT (v001 NVIDIA AWRDACPI 0x00001000 MSFT 0x0100000d) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x4008
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[17179569.184000] Processor #0 6:10 APIC version 16
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[17179569.184000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[17179569.184000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[17179569.184000] ACPI: BIOS IRQ0 pin2 override ignored.
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[17179569.184000] ACPI: IRQ9 used by override.
[17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[17179569.184000] Using ACPI (MADT) for SMP configuration information
[17179569.184000] Allocating PCI resources starting at 50000000 (gap: 40000000:bec00000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hdc1 ro quiet splash
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] Enabling fast FPU save and restore... done.
[17179569.184000] Enabling unmasked SIMD FPU exception support... done.
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[17179569.184000] Detected 2079.685 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179571.872000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[17179571.872000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179571.900000] Memory: 1029624k/1048512k available (1911k kernel code, 18104k reserved, 1073k data, 308k init, 131008k highmem)
[17179571.900000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179571.980000] Calibrating delay using timer specific routine.. 4164.00 BogoMIPS (lpj=8328015)
[17179571.980000] Security Framework v1.0.0 initialized
[17179571.980000] SELinux:  Disabled at boot.
[17179571.980000] Mount-cache hash table entries: 512
[17179571.980000] CPU: After generic identify, caps: 0383fbff c1c3fbff 00000000 00000000 00000000 00000000 00000000
[17179571.980000] CPU: After vendor identify, caps: 0383fbff c1c3fbff 00000000 00000000 00000000 00000000 00000000
[17179571.980000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[17179571.980000] CPU: L2 Cache: 512K (64 bytes/line)
[17179571.980000] CPU: After all inits, caps: 0383fbff c1c3fbff 00000000 00000420 00000000 00000000 00000000
[17179571.980000] Checking 'hlt' instruction... OK.
[17179571.996000] SMP alternatives: switching to UP code
[17179571.996000] Freeing SMP alternatives: 16k freed
[17179571.996000] checking if image is initramfs... it is
[17179572.428000] Freeing initrd memory: 5326k freed
[17179572.428000] ACPI: Core revision 20060707
[17179572.436000] ACPI: Looking for DSDT ... not found!
[17179572.448000] CPU0: AMD Athlon(tm) XP 2800+ stepping 00
[17179572.448000] Total of 1 processors activated (4164.00 BogoMIPS).
[17179572.448000] ENABLING IO-APIC IRQs
[17179572.448000] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
[17179572.592000] Brought up 1 CPUs
[17179572.592000] migration_cost=0
[17179572.592000] NET: Registered protocol family 16
[17179572.592000] EISA bus registered
[17179572.592000] ACPI: bus type pci registered
[17179572.592000] PCI: PCI BIOS revision 2.10 entry at 0xfb420, last bus=2
[17179572.592000] PCI: Using configuration type 1
[17179572.592000] Setting up standard PCI resources
[17179572.600000] ACPI: Interpreter enabled
[17179572.600000] ACPI: Using IOAPIC for interrupt routing
[17179572.600000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179572.600000] PCI: Probing PCI hardware (bus 00)
[17179572.604000] PCI: nForce2 C1 Halt Disconnect fixup
[17179572.604000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:09.0
[17179572.604000] Boot video device is 0000:02:00.0
[17179572.608000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179572.672000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[17179572.672000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGPB._PRT]
[17179572.672000] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[17179572.672000] ACPI: PCI Interrupt Link [LNK2] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[17179572.672000] ACPI: PCI Interrupt Link [LNK3] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[17179572.672000] ACPI: PCI Interrupt Link [LNK4] (IRQs 3 4 5 6 7 10 11 *12 14 15)
[17179572.672000] ACPI: PCI Interrupt Link [LNK5] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[17179572.672000] ACPI: PCI Interrupt Link [LUBA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[17179572.672000] ACPI: PCI Interrupt Link [LUBB] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[17179572.676000] ACPI: PCI Interrupt Link [LMAC] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[17179572.676000] ACPI: PCI Interrupt Link [LAPU] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[17179572.676000] ACPI: PCI Interrupt Link [LACI] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[17179572.676000] ACPI: PCI Interrupt Link [LMCI] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[17179572.676000] ACPI: PCI Interrupt Link [LSMB] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[17179572.676000] ACPI: PCI Interrupt Link [LUB2] (IRQs 3 4 5 6 7 10 11 *12 14 15)
[17179572.676000] ACPI: PCI Interrupt Link [LFIR] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[17179572.676000] ACPI: PCI Interrupt Link [L3CM] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[17179572.676000] ACPI: PCI Interrupt Link [LIDE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[17179572.676000] ACPI: PCI Interrupt Link [APC1] (IRQs *16), disabled.
[17179572.676000] ACPI: PCI Interrupt Link [APC2] (IRQs *17), disabled.
[17179572.676000] ACPI: PCI Interrupt Link [APC3] (IRQs *18), disabled.
[17179572.680000] ACPI: PCI Interrupt Link [APC4] (IRQs *19), disabled.
[17179572.680000] ACPI: PCI Interrupt Link [APCE] (IRQs *16), disabled.
[17179572.680000] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22) *0, disabled.
[17179572.680000] ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22) *0, disabled.
[17179572.680000] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22) *0, disabled.
[17179572.680000] ACPI: PCI Interrupt Link [APCI] (IRQs 20 21 22) *0, disabled.
[17179572.680000] ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22) *0, disabled.
[17179572.680000] ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22) *0, disabled.
[17179572.680000] ACPI: PCI Interrupt Link [APCS] (IRQs *23), disabled.
[17179572.680000] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22) *0, disabled.
[17179572.680000] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22) *0, disabled.
[17179572.684000] ACPI: PCI Interrupt Link [AP3C] (IRQs 20 21 22) *0, disabled.
[17179572.684000] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22) *0, disabled.
[17179572.684000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179572.684000] pnp: PnP ACPI init
[17179572.692000] pnp: PnP ACPI: found 14 devices
[17179572.692000] PnPBIOS: Disabled by ACPI PNP
[17179572.692000] PCI: Using ACPI for IRQ routing
[17179572.692000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179572.736000] pnp: 00:00: ioport range 0x4000-0x407f could not be reserved
[17179572.736000] pnp: 00:00: ioport range 0x4080-0x40ff has been reserved
[17179572.736000] pnp: 00:00: ioport range 0x4400-0x447f has been reserved
[17179572.736000] pnp: 00:00: ioport range 0x4480-0x44ff could not be reserved
[17179572.736000] pnp: 00:00: ioport range 0x4200-0x427f has been reserved
[17179572.736000] pnp: 00:00: ioport range 0x4280-0x42ff has been reserved
[17179572.736000] pnp: 00:01: ioport range 0x5000-0x503f has been reserved
[17179572.736000] pnp: 00:01: ioport range 0x5100-0x513f has been reserved
[17179572.740000] PCI: Bridge: 0000:00:08.0
[17179572.740000]   IO window: a000-cfff
[17179572.740000]   MEM window: df000000-e0ffffff
[17179572.740000]   PREFETCH window: 50000000-500fffff
[17179572.740000] PCI: Bridge: 0000:00:1e.0
[17179572.740000]   IO window: disabled.
[17179572.740000]   MEM window: dc000000-deffffff
[17179572.740000]   PREFETCH window: d0000000-d7ffffff
[17179572.740000] PCI: Setting latency timer of device 0000:00:08.0 to 64
[17179572.740000] NET: Registered protocol family 2
[17179572.776000] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179572.776000] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[17179572.776000] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[17179572.776000] TCP: Hash tables configured (established 131072 bind 65536)
[17179572.776000] TCP reno registered
[17179572.776000] audit: initializing netlink socket (disabled)
[17179572.776000] audit(1175483234.776:1): initialized
[17179572.776000] highmem bounce pool size: 64 pages
[17179572.776000] VFS: Disk quotas dquot_6.5.1
[17179572.776000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179572.776000] Initializing Cryptographic API
[17179572.776000] io scheduler noop registered
[17179572.776000] io scheduler anticipatory registered
[17179572.776000] io scheduler deadline registered
[17179572.776000] io scheduler cfq registered (default)
[17179572.776000] isapnp: Scanning for PnP cards...
[17179573.132000] isapnp: No Plug & Play device found
[17179573.152000] Real Time Clock Driver v1.12ac
[17179573.152000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[17179573.152000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179573.152000] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[17179573.156000] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179573.156000] 00:0b: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[17179573.156000] mice: PS/2 mouse device common for all mice
[17179573.156000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179573.156000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179573.156000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179573.156000] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[17179573.156000] PNP: PS/2 controller doesn't have AUX irq; using default 12
[17179573.156000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179573.156000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179573.156000] EISA: Probing bus 0 at eisa.0
[17179573.156000] Cannot allocate resource for EISA slot 4
[17179573.156000] Cannot allocate resource for EISA slot 5
[17179573.156000] EISA: Detected 0 cards.
[17179573.156000] TCP bic registered
[17179573.156000] NET: Registered protocol family 1
[17179573.156000] NET: Registered protocol family 8
[17179573.156000] NET: Registered protocol family 20
[17179573.156000] Using IPI No-Shortcut mode
[17179573.156000] ACPI: (supports S0 S1 S4 S5)
[17179573.160000] Freeing unused kernel memory: 308k freed
[17179573.372000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179574.284000] Capability LSM initialized
[17179574.312000] ACPI: Fan [FAN] (on)
[17179574.320000] ACPI: Thermal Zone [THRM] (46 C)
[17179574.620000] SCSI subsystem initialized
[17179574.620000] libata version 1.20 loaded.
[17179574.624000] NFORCE2: IDE controller at PCI slot 0000:00:09.0
[17179574.624000] NFORCE2: chipset revision 162
[17179574.624000] NFORCE2: not 100% native mode: will probe irqs later
[17179574.624000] NFORCE2: 0000:00:09.0 (rev a2) UDMA133 controller
[17179574.624000]     ide0: BM-DMA at 0xf000-0xf007, BIOS settings: hda:DMA, hdb:DMA
[17179574.624000]     ide1: BM-DMA at 0xf008-0xf00f, BIOS settings: hdc:DMA, hdd:DMA
[17179574.624000] Probing IDE interface ide0...
[17179575.364000] hda: LITE-ON DVDRW SOHW-812S, ATAPI CD/DVD-ROM drive
[17179576.040000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179576.040000] Probing IDE interface ide1...
[17179576.328000] hdc: ST3200826A, ATA DISK drive
[17179577.008000] ide1 at 0x170-0x177,0x376 on irq 15
[17179577.020000] hda: ATAPI 40X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(33)
[17179577.020000] Uniform CD-ROM driver Revision: 3.20
[17179577.032000] hdc: max request size: 512KiB
[17179577.032000] hdc: 390721968 sectors (200049 MB) w/8192KiB Cache, CHS=24321/255/63, UDMA(33)
[17179577.032000] hdc: cache flushes supported
[17179577.032000]  hdc: hdc1 hdc2 < hdc5 >
[17179577.212000] sata_sil 0000:01:0a.0: version 0.9
[17179577.212000] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
[17179577.212000] ACPI: PCI Interrupt 0000:01:0a.0[A] -> Link [APC3] -> GSI 18 (level, high) -> IRQ 177
[17179577.212000] ata1: SATA max UDMA/100 cmd 0xF887C080 ctl 0xF887C08A bmdma 0xF887C000 irq 177
[17179577.212000] ata2: SATA max UDMA/100 cmd 0xF887C0C0 ctl 0xF887C0CA bmdma 0xF887C008 irq 177
[17179577.212000] ata3: SATA max UDMA/100 cmd 0xF887C280 ctl 0xF887C28A bmdma 0xF887C200 irq 177
[17179577.212000] ata4: SATA max UDMA/100 cmd 0xF887C2C0 ctl 0xF887C2CA bmdma 0xF887C208 irq 177
[17179577.572000] ata1: SATA link up 1.5 Gbps (SStatus 113)
[17179577.588000] ata1: dev 0 cfg 49:2f00 82:346b 83:7d01 84:4023 85:3469 86:3c01 87:4023 88:207f
[17179577.588000] ata1: dev 0 ATA-7, max UDMA/133, 625142448 sectors: LBA48
[17179577.600000] ata1: dev 0 configured for UDMA/100
[17179577.600000] scsi0 : sata_sil
[17179577.960000] ata2: SATA link up 1.5 Gbps (SStatus 113)
[17179577.972000] ata2: dev 0 cfg 49:2f00 82:346b 83:7d01 84:4023 85:3469 86:3c01 87:4023 88:207f
[17179577.972000] ata2: dev 0 ATA-7, max UDMA/133, 625142448 sectors: LBA48
[17179577.984000] ata2: dev 0 configured for UDMA/100
[17179577.984000] scsi1 : sata_sil
[17179578.188000] ata3: SATA link down (SStatus 0)
[17179578.200000] scsi2 : sata_sil
[17179578.560000] ata4: SATA link up 1.5 Gbps (SStatus 113)
[17179578.572000] ata4: dev 0 cfg 49:2f00 82:346b 83:7d01 84:4003 85:3469 86:3c01 87:4003 88:207f
[17179578.572000] ata4: dev 0 ATA-6, max UDMA/133, 234441648 sectors: LBA48
[17179578.584000] ata4: dev 0 configured for UDMA/100
[17179578.584000] scsi3 : sata_sil
[17179578.584000]   Vendor: ATA       Model: ST3320620AS       Rev: 3.AA
[17179578.584000]   Type:   Direct-Access                      ANSI SCSI revision: 05
[17179578.584000]   Vendor: ATA       Model: ST3320620AS       Rev: 3.AA
[17179578.584000]   Type:   Direct-Access                      ANSI SCSI revision: 05
[17179578.584000]   Vendor: ATA       Model: ST3120827AS       Rev: 3.42
[17179578.584000]   Type:   Direct-Access                      ANSI SCSI revision: 05
[17179578.584000] ACPI: PCI Interrupt 0000:01:0b.0[A] -> Link [APC3] -> GSI 18 (level, high) -> IRQ 177
[17179578.584000] ata5: SATA max UDMA/100 cmd 0xF88A4080 ctl 0xF88A408A bmdma 0xF88A4000 irq 177
[17179578.584000] ata6: SATA max UDMA/100 cmd 0xF88A40C0 ctl 0xF88A40CA bmdma 0xF88A4008 irq 177
[17179578.944000] ata5: SATA link up 1.5 Gbps (SStatus 113)
[17179578.956000] ata5: dev 0 cfg 49:2f00 82:7c69 83:7f09 84:4003 85:7c69 86:3e01 87:4003 88:207f
[17179578.956000] ata5: dev 0 ATA-7, max UDMA/133, 320173056 sectors: LBA48
[17179578.968000] ata5: dev 0 configured for UDMA/100
[17179578.968000] scsi4 : sata_sil
[17179579.328000] ata6: SATA link up 1.5 Gbps (SStatus 113)
[17179579.340000] ata6: dev 0 cfg 49:2f00 82:7c69 83:7f09 84:4003 85:7c69 86:3e01 87:4003 88:207f
[17179579.340000] ata6: dev 0 ATA-7, max UDMA/133, 320173056 sectors: LBA48
[17179579.352000] ata6: dev 0 configured for UDMA/100
[17179579.352000] scsi5 : sata_sil
[17179579.352000]   Vendor: ATA       Model: Maxtor 6Y160M0    Rev: YAR5
[17179579.352000]   Type:   Direct-Access                      ANSI SCSI revision: 05
[17179579.356000]   Vendor: ATA       Model: Maxtor 6Y160M0    Rev: YAR5
[17179579.356000]   Type:   Direct-Access                      ANSI SCSI revision: 05
[17179579.372000] SCSI device sda: 625142448 512-byte hdwr sectors (320073 MB)
[17179579.372000] sda: Write Protect is off
[17179579.372000] sda: Mode Sense: 00 3a 00 00
[17179579.372000] SCSI device sda: drive cache: write back
[17179579.372000] SCSI device sda: 625142448 512-byte hdwr sectors (320073 MB)
[17179579.372000] sda: Write Protect is off
[17179579.372000] sda: Mode Sense: 00 3a 00 00
[17179579.372000] SCSI device sda: drive cache: write back
[17179579.372000]  sda: sda1
[17179579.388000] sd 0:0:0:0: Attached scsi disk sda
[17179579.392000] SCSI device sdb: 625142448 512-byte hdwr sectors (320073 MB)
[17179579.392000] sdb: Write Protect is off
[17179579.392000] sdb: Mode Sense: 00 3a 00 00
[17179579.392000] SCSI device sdb: drive cache: write back
[17179579.396000] SCSI device sdb: 625142448 512-byte hdwr sectors (320073 MB)
[17179579.400000] sdb: Write Protect is off
[17179579.400000] sdb: Mode Sense: 00 3a 00 00
[17179579.400000] SCSI device sdb: drive cache: write back
[17179579.400000]  sdb: sdb1
[17179579.424000] sd 1:0:0:0: Attached scsi disk sdb
[17179579.428000] SCSI device sdc: 234441648 512-byte hdwr sectors (120034 MB)
[17179579.428000] sdc: Write Protect is off
[17179579.428000] sdc: Mode Sense: 00 3a 00 00
[17179579.428000] SCSI device sdc: drive cache: write back
[17179579.432000] SCSI device sdc: 234441648 512-byte hdwr sectors (120034 MB)
[17179579.436000] sdc: Write Protect is off
[17179579.436000] sdc: Mode Sense: 00 3a 00 00
[17179579.436000] SCSI device sdc: drive cache: write back
[17179579.436000]  sdc: sdc1
[17179579.456000] sd 3:0:0:0: Attached scsi disk sdc
[17179579.460000] SCSI device sdd: 320173056 512-byte hdwr sectors (163929 MB)
[17179579.460000] sdd: Write Protect is off
[17179579.460000] sdd: Mode Sense: 00 3a 00 00
[17179579.460000] SCSI device sdd: drive cache: write back
[17179579.464000] SCSI device sdd: 320173056 512-byte hdwr sectors (163929 MB)
[17179579.464000] sdd: Write Protect is off
[17179579.464000] sdd: Mode Sense: 00 3a 00 00
[17179579.468000] SCSI device sdd: drive cache: write back
[17179579.468000]  sdd: sdd1
[17179579.492000] sd 4:0:0:0: Attached scsi disk sdd
[17179579.496000] SCSI device sde: 320173056 512-byte hdwr sectors (163929 MB)
[17179579.496000] sde: Write Protect is off
[17179579.496000] sde: Mode Sense: 00 3a 00 00
[17179579.496000] SCSI device sde: drive cache: write back
[17179579.496000] SCSI device sde: 320173056 512-byte hdwr sectors (163929 MB)
[17179579.500000] sde: Write Protect is off
[17179579.500000] sde: Mode Sense: 00 3a 00 00
[17179579.500000] SCSI device sde: drive cache: write back
[17179579.500000]  sde: sde1
[17179579.524000] sd 5:0:0:0: Attached scsi disk sde
[17179579.756000] usbcore: registered new driver usbfs
[17179579.756000] usbcore: registered new driver hub
[17179579.756000] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[17179579.756000] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 22
[17179579.756000] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [APCF] -> GSI 22 (level, high) -> IRQ 185
[17179579.756000] PCI: Setting latency timer of device 0000:00:02.0 to 64
[17179579.756000] ohci_hcd 0000:00:02.0: OHCI Host Controller
[17179579.756000] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
[17179579.760000] ohci_hcd 0000:00:02.0: irq 185, io mem 0xe1080000
[17179579.788000] ieee1394: Initialized config rom entry `ip1394'
[17179579.820000] usb usb1: configuration #1 chosen from 1 choice
[17179579.820000] hub 1-0:1.0: USB hub found
[17179579.820000] hub 1-0:1.0: 3 ports detected
[17179579.928000] ACPI: PCI Interrupt Link [APCG] enabled at IRQ 21
[17179579.928000] ACPI: PCI Interrupt 0000:00:02.1[B] -> Link [APCG] -> GSI 21 (level, high) -> IRQ 193
[17179579.928000] PCI: Setting latency timer of device 0000:00:02.1 to 64
[17179579.928000] ohci_hcd 0000:00:02.1: OHCI Host Controller
[17179579.928000] ohci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 2
[17179579.928000] ohci_hcd 0000:00:02.1: irq 193, io mem 0xe1083000
[17179579.988000] usb usb2: configuration #1 chosen from 1 choice
[17179579.988000] hub 2-0:1.0: USB hub found
[17179579.988000] hub 2-0:1.0: 3 ports detected
[17179580.096000] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 20
[17179580.096000] ACPI: PCI Interrupt 0000:00:02.2[C] -> Link [APCL] -> GSI 20 (level, high) -> IRQ 201
[17179580.096000] PCI: Setting latency timer of device 0000:00:02.2 to 64
[17179580.096000] ehci_hcd 0000:00:02.2: EHCI Host Controller
[17179580.096000] ehci_hcd 0000:00:02.2: new USB bus registered, assigned bus number 3
[17179580.096000] ehci_hcd 0000:00:02.2: selective suspend/wakeup unavailable
[17179580.096000] ehci_hcd 0000:00:02.2: debug port 1
[17179580.096000] PCI: cache line size of 64 is not supported by device 0000:00:02.2
[17179580.096000] ehci_hcd 0000:00:02.2: irq 201, io mem 0xe1086000
[17179580.096000] ehci_hcd 0000:00:02.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179580.096000] usb usb3: configuration #1 chosen from 1 choice
[17179580.096000] hub 3-0:1.0: USB hub found
[17179580.096000] hub 3-0:1.0: 6 ports detected
[17179580.204000] ACPI: PCI Interrupt Link [APCM] enabled at IRQ 22
[17179580.204000] ACPI: PCI Interrupt 0000:00:0d.0[A] -> Link [APCM] -> GSI 22 (level, high) -> IRQ 185
[17179580.204000] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[17179580.256000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[185]  MMIO=[e1084000-e10847ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[17179580.316000] Attempting manual resume
[17179580.356000] kjournald starting.  Commit interval 5 seconds
[17179580.356000] EXT3-fs: mounted filesystem with ordered data mode.
[17179580.996000] usb 3-2: new high speed USB device using ehci_hcd and address 3
[17179581.132000] usb 3-2: configuration #1 chosen from 1 choice
[17179581.132000] hub 3-2:1.0: USB hub found
[17179581.132000] hub 3-2:1.0: 4 ports detected
[17179581.372000] ohci1394: fw-host0: SelfID received outside of bus reset sequence
[17179581.580000] usb 3-5: new high speed USB device using ehci_hcd and address 4
[17179581.644000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[000000508df21621]
[17179581.728000] usb 3-5: configuration #1 chosen from 1 choice
[17179581.728000] ohci_hcd 0000:00:02.0: wakeup
[17179582.028000] usb 3-2.1: new high speed USB device using ehci_hcd and address 5
[17179582.128000] usb 3-2.1: configuration #1 chosen from 1 choice
[17179582.344000] usb 3-2.4: new low speed USB device using ehci_hcd and address 6
[17179582.488000] usb 3-2.4: configuration #1 chosen from 1 choice
[17179582.796000] usb 1-1: new low speed USB device using ohci_hcd and address 3
[17179583.028000] usb 1-1: configuration #1 chosen from 1 choice
[17179591.736000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179591.740000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179591.772000] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.54.
[17179591.772000] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 21
[17179591.772000] ACPI: PCI Interrupt 0000:00:04.0[A] -> Link [APCH] -> GSI 21 (level, high) -> IRQ 193
[17179591.772000] PCI: Setting latency timer of device 0000:00:04.0 to 64
[17179592.076000] Linux agpgart interface v0.101 (c) Dave Jones
[17179592.292000] eth0: forcedeth.c: subsystem: 0147b:1c00 bound to 0000:00:04.0
[17179592.292000] agpgart: Detected NVIDIA nForce2 chipset
[17179592.300000] agpgart: AGP aperture is 64M @ 0xd8000000
[17179592.300000] i2c_adapter i2c-0: nForce2 SMBus adapter at 0x5000
[17179592.300000] i2c_adapter i2c-1: nForce2 SMBus adapter at 0x5100
[17179592.300000] ACPI: PCI Interrupt Link [APCJ] enabled at IRQ 20
[17179592.300000] ACPI: PCI Interrupt 0000:00:06.0[A] -> Link [APCJ] -> GSI 20 (level, high) -> IRQ 201
[17179592.300000] PCI: Setting latency timer of device 0000:00:06.0 to 64
[17179592.548000] input: PC Speaker as /class/input/input1
[17179592.576000] Floppy drive(s): fd0 is 1.44M
[17179592.596000] FDC 0 is a post-1991 82077
[17179592.624000] intel8x0_measure_ac97_clock: measured 56775 usecs
[17179592.624000] intel8x0: clocking to 48000
[17179592.680000] usbcore: registered new driver hiddev
[17179592.736000] nvidia: module license 'NVIDIA' taints kernel.
[17179593.060000] ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
[17179593.060000] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [APC4] -> GSI 19 (level, high) -> IRQ 209
[17179593.060000] NVRM: loading NVIDIA UNIX x86 Kernel Module  1.0-9746  Fri Dec 15 09:54:45 PST 2006
[17179593.076000] parport: PnPBIOS parport detected.
[17179593.076000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
[17179593.168000] hiddev96: USB HID v1.10 Device [American Power Conversion Back-UPS BR  800 FW:9.o2 .D USB FW:o2 ] on usb-0000:00:02.2-2.4
[17179593.244000] input: Microsoft Microsoft IntelliMouse&#65533; Optical as /class/input/input2
[17179593.244000] input: USB HID v1.00 Mouse [Microsoft Microsoft IntelliMouse&#65533; Optical] on usb-0000:00:02.0-1
[17179593.244000] usbcore: registered new driver libusual
[17179593.244000] usbcore: registered new driver usbhid
[17179593.244000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[17179593.260000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[17179593.260000] sd 1:0:0:0: Attached scsi generic sg1 type 0
[17179593.260000] sd 3:0:0:0: Attached scsi generic sg2 type 0
[17179593.260000] sd 4:0:0:0: Attached scsi generic sg3 type 0
[17179593.260000] sd 5:0:0:0: Attached scsi generic sg4 type 0
[17179593.264000] Initializing USB Mass Storage driver...
[17179593.280000] scsi6 : SCSI emulation for USB Mass Storage devices
[17179593.280000] usb-storage: device found at 4
[17179593.280000] usb-storage: waiting for device to settle before scanning
[17179593.280000] scsi7 : SCSI emulation for USB Mass Storage devices
[17179593.280000] usbcore: registered new driver usb-storage
[17179593.280000] USB Mass Storage support registered.
[17179593.280000] usb-storage: device found at 5
[17179593.280000] usb-storage: waiting for device to settle before scanning
[17179593.508000] ts: Compaq touchscreen protocol output
[17179593.952000] NET: Registered protocol family 10
[17179593.952000] lo: Disabled Privacy Extensions
[17179593.952000] IPv6 over IPv4 tunneling driver
[17179594.124000] lp0: using parport0 (interrupt-driven).
[17179594.144000] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)
[17179594.144000] ieee1394: sbp2: Try serialize_io=0 for better performance
[17179594.164000] tun: Universal TUN/TAP device driver, 1.6
[17179594.164000] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[17179594.192000] Adding 3028212k swap on /dev/disk/by-uuid/16a7b8b2-45b4-4e6f-903e-20fa0567c60c.  Priority:-1 extents:1 across:3028212k
[17179594.260000] EXT3 FS on hdc1, internal journal
[17179594.492000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[17179594.492000] md: bitmap version 4.39
[17179595.992000] NET: Registered protocol family 17
[17179598.280000] usb-storage: device scan complete
[17179598.280000] usb-storage: device scan complete
[17179598.284000]   Vendor: USB2.0    Model: CardReader CF RW  Rev: 0.0>
[17179598.284000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17179598.336000]   Vendor: Maxtor    Model: OneTouch II       Rev: 023d
[17179598.336000]   Type:   Direct-Access                      ANSI SCSI revision: 04
[17179598.404000] SCSI device sdf: 398297088 512-byte hdwr sectors (203928 MB)
[17179598.456000] sdf: Write Protect is off
[17179598.456000] sdf: Mode Sense: 24 00 00 00
[17179598.456000] sdf: assuming drive cache: write through
[17179598.508000] SCSI device sdf: 398297088 512-byte hdwr sectors (203928 MB)
[17179598.532000]   Vendor: USB2.0    Model: CardReader SD RW  Rev: 0.0>
[17179598.532000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17179598.536000]   Vendor: USB2.0    Model: CardReader SM RW  Rev: 0.0>
[17179598.536000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17179598.536000]   Vendor: USB2.0    Model: CardReader MS RW  Rev: 0.0>
[17179598.536000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17179598.564000] sdf: Write Protect is off
[17179598.564000] sdf: Mode Sense: 24 00 00 00
[17179598.564000] sdf: assuming drive cache: write through
[17179598.564000]  sdf: sdf1
[17179598.592000] sd 7:0:0:0: Attached scsi disk sdf
[17179598.592000] sd 7:0:0:0: Attached scsi generic sg5 type 0
[17179598.596000] sd 6:0:0:0: Attached scsi removable disk sdg
[17179598.596000] sd 6:0:0:0: Attached scsi generic sg6 type 0
[17179598.600000] sd 6:0:0:1: Attached scsi removable disk sdh
[17179598.600000] sd 6:0:0:1: Attached scsi generic sg7 type 0
[17179598.604000] SCSI device sdi: 64000 512-byte hdwr sectors (33 MB)
[17179598.604000] sdi: Write Protect is off
[17179598.604000] sdi: Mode Sense: 02 00 00 00
[17179598.604000] sdi: assuming drive cache: write through
[17179598.608000] SCSI device sdi: 64000 512-byte hdwr sectors (33 MB)
[17179598.608000] sdi: Write Protect is off
[17179598.608000] sdi: Mode Sense: 02 00 00 00
[17179598.608000] sdi: assuming drive cache: write through
[17179598.608000]  sdi: sdi1
[17179598.612000] sd 6:0:0:2: Attached scsi removable disk sdi
[17179598.612000] sd 6:0:0:2: Attached scsi generic sg8 type 0
[17179598.616000] sd 6:0:0:3: Attached scsi removable disk sdj
[17179598.616000] sd 6:0:0:3: Attached scsi generic sg9 type 0
[17179601.452000] ACPI: Power Button (FF) [PWRF]
[17179601.452000] ACPI: Power Button (CM) [PWRB]
[17179601.552000] ibm_acpi: ec object not found
[17179601.576000] pcc_acpi: loading...
[17179604.040000] eth0: no IPv6 routers present
[17179604.428000] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[17179604.428000] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[17179604.428000] agpgart: Putting AGP V3 device at 0000:02:00.0 into 8x mode
[17179606.240000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[17179606.240000] apm: overridden by ACPI.
[17179611.344000] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
[17179611.580000] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[17179611.592000] NFSD: starting 90-second grace period
[17179612.656000] Bluetooth: Core ver 2.8
[17179612.656000] NET: Registered protocol family 31
[17179612.656000] Bluetooth: HCI device and connection manager initialized
[17179612.656000] Bluetooth: HCI socket layer initialized
[17179612.688000] Bluetooth: L2CAP ver 2.8
[17179612.688000] Bluetooth: L2CAP socket layer initialized
[17179612.720000] Bluetooth: RFCOMM socket layer initialized
[17179612.720000] Bluetooth: RFCOMM TTY layer initialized
[17179612.720000] Bluetooth: RFCOMM ver 1.7
[17179624.912000] kjournald starting.  Commit interval 5 seconds
[17179624.924000] EXT3 FS on sdf1, internal journal
[17179624.924000] EXT3-fs: mounted filesystem with ordered data mode.
[17179626.372000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
]
```

Maybe i need to be looking somewhere other than dmesg for my error messages? I am not aware of any specific mdadm logs. The user mentioned in the issue above said he solved the problem by changing some "rcS.d" file, changing the order or some links because mdadm was trying to setup the array before the sata controller was initialized. Again, I am not sure how to check if this is the case or not. thanks

---

### Post by cprophecy on 2007-04-09
anybody have any idea? id appreciate it

---

### Post by OliW on 2007-11-09
I'm having the same issue with the same controller. I can't see how that (the controller) would cause this problem though.

Did you ever manage to get this working? I'd love a hand.

---

### Post by OliW on 2007-11-23
Well I fixed it.

I ran:
sudo dppg-reconfigure mdadm

Accepted all the defaults. If you've never played silly-buggers with your kernels, this *might* fix it for you, but as it was, I have built a couple of kernels before and the initramfs-update was trying to write to one of those (that I don't use). So I had to remove all the custom kernels and reinstall 2.6.22-14-generic in synaptic. I then ran dpkg-reconfigure again, it wrote the to correct kernel image, I rebooted, and my RAID works. Woo!

Oh one important (I think) note, my mdadm.conf contains the UUID of my HDs, not names because the names seem to be quite fluid (they kept changing name every boot). If you're not set up like this, I suggest doing so.

---

### Post by rnewman38 on 2007-12-01
Here is a thought. Did you put the same mbr on BOTH drives?

 Install the Grub MBR on Both Drives.

 Rob

---

