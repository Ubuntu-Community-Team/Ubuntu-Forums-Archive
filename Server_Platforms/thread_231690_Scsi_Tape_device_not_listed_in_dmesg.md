---
title: "Scsi Tape device not listed in dmesg"
date: 2006-08-07
forum: Server Platforms
---

### Post by sveinpj@broadpark.no on 2006-08-07
Hello

I've got a IBM PCI ServeRAID 4Lx controller installed on my new installed Ubuntu 6.06 server.
My problem is that my Tape device are not listet in dmesg, and therefore no /dev/st0 device :mad: 

The funny thing is that the tape device works on a Knoppix Live CD :-k 

The Knoppix dmesg shows:
> PCI: Found IRQ 11 for device 0000:00:0e.0
PCI: Sharing IRQ 11 with 0000:00:07.5
scsi0 : IBM PCI ServeRAID 7.12.05  Build 761 <ServeRAID 4Lx>
  Vendor: IBM       Model: SERVERAID         Rev: 1.00
  Type:   Processor                          ANSI SCSI revision: 02
  Vendor: SONY      Model: SDX-500V          Rev: 0101
  Type:   Sequential-Access                  ANSI SCSI revision: 02


whilst the Ubuntu shows:
> [42949381.550000] ACPI: PCI Interrupt 0000:00:0e.0[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[42949381.570000] scsi0 : IBM PCI ServeRAID 7.12.05  Build 761 <ServeRAID 4Lx>
[42949381.580000]   Vendor: IBM       Model: SERVERAID         Rev: 1.00
[42949381.580000]   Type:   Processor                          ANSI SCSI revision: 02



As I've browsed through the forum, I've also tried:
apt-get install mt-st with no effect, also tried rmmod ips & modprobe ips with no effect.

I am going nuts by this problem ](*,) 

Anyone got a tip?

Sincerely
Svein-P.Johnsen

---

### Post by sveinpj@broadpark.no on 2006-08-07
**Knoppix dmesg**

Linux version 2.6.17 (root@Knoppix) (gcc version 4.0.4 20060507 (prerelease) (Debian 4.0.3-3)) #4 SMP PREEMPT Wed May 10 13:53:45 CEST 2006
BIOS-provided physical RAM map:
 BIOS-e820: 0000000000000000 - 00000000000a0000 (usable)
 BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
 BIOS-e820: 0000000000100000 - 000000000fff0000 (usable)
 BIOS-e820: 000000000fff0000 - 000000000fff3000 (ACPI NVS)
 BIOS-e820: 000000000fff3000 - 0000000010000000 (ACPI data)
 BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
0MB HIGHMEM available.
255MB LOWMEM available.
On node 0 totalpages: 65520
  DMA zone: 4096 pages, LIFO batch:0
  Normal zone: 61424 pages, LIFO batch:15
DMI 2.2 present.
ACPI: RSDP (v000 MSISYS                                ) @ 0x000f65f0
ACPI: RSDT (v001 MSISYS AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x0fff3000
ACPI: FADT (v001 MSISYS AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x0fff3040
ACPI: DSDT (v001 MSISYS AWRDACPI 0x00001000 MSFT 0x0100000c) @ 0x00000000
ACPI: BIOS age (2001) fails cutoff (2002), acpi=force is required to enable ACPI
ACPI: Disabling ACPI support
Allocating PCI resources starting at 20000000 (gap: 10000000:efff0000)
Built 1 zonelists
Kernel command line: ramdisk_size=100000 init=/etc/init lang=us apm=power-off vga=791 initrd=minirt.gz nomce quiet BOOT_IMAGE=knoppix BOOT_IMAGE=linux 2
Local APIC disabled by BIOS -- you can enable it with "lapic"
mapped APIC to ffffd000 (0120a000)
Enabling fast FPU save and restore... done.
Enabling unmasked SIMD FPU exception support... done.
Initializing CPU#0
PID hash table entries: 1024 (order: 10, 4096 bytes)
Detected 866.835 MHz processor.
Using tsc for high-res timesource
Console: colour dummy device 80x25
Dentry cache hash table entries: 32768 (order: 5, 131072 bytes)
Inode-cache hash table entries: 16384 (order: 4, 65536 bytes)
Memory: 254736k/262080k available (2225k kernel code, 6728k reserved, 807k data, 324k init, 0k highmem)
Checking if this processor honours the WP bit even in supervisor mode... Ok.
Calibrating delay using timer specific routine.. 1737.77 BogoMIPS (lpj=3475548)
Security Framework v1.0.0 initialized
SELinux:  Disabled at boot.
Capability LSM initialized
Mount-cache hash table entries: 512
CPU: After generic identify, caps: 0383f9ff 00000000 00000000 00000000 00000000 00000000 00000000
CPU: After vendor identify, caps: 0383f9ff 00000000 00000000 00000000 00000000 00000000 00000000
CPU: L1 I cache: 16K, L1 D cache: 16K
CPU: L2 cache: 256K
CPU: After all inits, caps: 0383f9ff 00000000 00000000 00000040 00000000 00000000 00000000
Checking 'hlt' instruction... OK.
Checking for popad bug... OK.
SMP alternatives: switching to UP code
Freeing SMP alternatives: 12k freed
CPU0: Intel Pentium III (Coppermine) stepping 06
SMP motherboard not detected.
Local APIC not detected. Using dummy APIC emulation.
Brought up 1 CPUs
migration_cost=0
checking if image is initramfs...it isn't (no cpio magic); looks like an initrd
Freeing initrd memory: 729k freed
NET: Registered protocol family 16
EISA bus registered
PCI: PCI BIOS revision 2.10 entry at 0xfb2f0, last bus=1
Setting up standard PCI resources
ACPI: Subsystem revision 20060127
ACPI: Interpreter disabled.
Linux Plug and Play Support v0.97 (c) Adam Belay
pnp: PnP ACPI: disabled
PnPBIOS: Scanning system for PnP BIOS support...
PnPBIOS: Found PnP BIOS installation structure at 0xc00fbd00
PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0xbd30, dseg 0xf0000
PnPBIOS: 15 nodes reported by PnP BIOS; 15 recorded by driver
SCSI subsystem initialized
PCI: Probing PCI hardware
PCI: Probing PCI hardware (bus 00)
PCI quirk: region 4000-40ff claimed by vt82c586 ACPI
PCI quirk: region 6000-607f claimed by vt82c686 HW-mon
PCI quirk: region 5000-500f claimed by vt82c686 SMB
Boot video device is 0000:01:00.0
PCI: Using IRQ router VIA [1106/0686] at 0000:00:07.0
PCI: Bridge: 0000:00:01.0
  IO window: disabled.
  MEM window: dc000000-ddffffff
  PREFETCH window: d0000000-d7ffffff
PCI: Setting latency timer of device 0000:00:01.0 to 64
NET: Registered protocol family 2
IP route cache hash table entries: 2048 (order: 1, 8192 bytes)
TCP established hash table entries: 8192 (order: 4, 98304 bytes)
TCP bind hash table entries: 4096 (order: 3, 49152 bytes)
TCP: Hash tables configured (established 8192 bind 4096)
TCP reno registered
audit: initializing netlink socket (disabled)
audit(978309226.552:1): initialized
Total HugeTLB memory allocated, 0
VFS: Disk quotas dquot_6.5.1
Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Initializing Cryptographic API
io scheduler noop registered
io scheduler anticipatory registered
io scheduler deadline registered (default)
io scheduler cfq registered
PCI: Disabling Via external APIC routing
vesafb: framebuffer at 0xd0000000, mapped to 0xd0880000, using 3072k, total 8192k
vesafb: mode is 1024x768x16, linelength=2048, pages=4
vesafb: protected mode interface info at c000:7dc8
vesafb: scrolling: redraw
vesafb: Truecolor: size=0:5:6:5, shift=0:11:5:0
Console: switching to colour frame buffer device 128x48
fb0: VESA VGA frame buffer device
isapnp: Scanning for PnP cards...
isapnp: No Plug & Play device found
Real Time Clock Driver v1.12ac
Floppy drive(s): fd0 is 1.44M
FDC 0 is a post-1991 82077
RAMDISK driver initialized: 16 RAM disks of 100000K size 1024 blocksize
Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
VP_IDE: IDE controller at PCI slot 0000:00:07.1
VP_IDE: chipset revision 16
VP_IDE: not 100% native mode: will probe irqs later
VP_IDE: VIA vt82c686a (rev 22) IDE UDMA66 controller on pci0000:00:07.1
    ide0: BM-DMA at 0x9000-0x9007, BIOS settings: hda:pio, hdb:pio
    ide1: BM-DMA at 0x9008-0x900f, BIOS settings: hdc:DMA, hdd:pio
Probing IDE interface ide0...
Probing IDE interface ide1...
hdc: LTN485S, ATAPI CD/DVD-ROM drive
ide1 at 0x170-0x177,0x376 on irq 15
PDC20269: IDE controller at PCI slot 0000:00:0b.0
PCI: Found IRQ 10 for device 0000:00:0b.0
PCI: Sharing IRQ 10 with 0000:00:07.3
PDC20269: chipset revision 2
PDC20269: ROM enabled at 0x20118000
PDC20269: 100% native mode on irq 10
    ide2: BM-DMA at 0xbc00-0xbc07, BIOS settings: hde:pio, hdf:pio
    ide3: BM-DMA at 0xbc08-0xbc0f, BIOS settings: hdg:pio, hdh:pio
Probing IDE interface ide2...
hdf: WDC WD100BA, ATA DISK drive
ide2 at 0xac00-0xac07,0xb002 on irq 10
Probing IDE interface ide3...
Probing IDE interface ide0...
Probing IDE interface ide3...
hdf: max request size: 128KiB
hdf: 19541088 sectors (10005 MB) w/1961KiB Cache, CHS=19386/16/63
hdf: cache flushes not supported
 hdf: hdf1 hdf2 < hdf5 >
hdc: ATAPI 48X CD-ROM drive, 120kB Cache
Uniform CD-ROM driver Revision: 3.20
libata version 1.20 loaded.
PNP: PS/2 Controller [PNP0303] at 0x60,0x64 irq 1
PNP: PS/2 controller doesn't have AUX irq; using default 12
serio: i8042 AUX port at 0x60,0x64 irq 12
serio: i8042 KBD port at 0x60,0x64 irq 1
mice: PS/2 mouse device common for all mice
EISA: Probing bus 0 at eisa.0
Cannot allocate resource for EISA slot 4
Cannot allocate resource for EISA slot 5
Cannot allocate resource for EISA slot 6
EISA: Detected 0 cards.
NET: Registered protocol family 1
NET: Registered protocol family 15
Using IPI No-Shortcut mode
RAMDISK: Compressed image found at block 0
input: AT Translated Set 2 keyboard as /class/input/input0
VFS: Mounted root (ext2 filesystem).
Failed initialization of WD-7000 SCSI card!
usbcore: registered new driver usbfs
usbcore: registered new driver hub
USB Universal Host Controller Interface driver v3.0
PCI: Found IRQ 10 for device 0000:00:07.3
PCI: Sharing IRQ 10 with 0000:00:0b.0
uhci_hcd 0000:00:07.3: UHCI Host Controller
uhci_hcd 0000:00:07.3: new USB bus registered, assigned bus number 1
uhci_hcd 0000:00:07.3: irq 10, io base 0x00009800
usb usb1: configuration #1 chosen from 1 choice
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 2 ports detected
ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
Initializing USB Mass Storage driver...
usbcore: registered new driver usb-storage
USB Mass Storage support registered.
ieee1394: Initialized config rom entry `ip1394'
ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)
ieee1394: sbp2: Try serialize_io=0 for better performance
Warning: /proc/ide/hd?/settings interface is obsolete, and will be removed soon!
ISO 9660 Extensions: Microsoft Joliet Level 3
ISO 9660 Extensions: RRIP_1991A
cloop: Initializing cloop v2.04
cloop: loaded (max 8 devices)
cloop: /cdrom/KNOPPIX/KNOPPIX: 31120 blocks, 65536 bytes/block, largest block is 65552 bytes.
ISO 9660 Extensions: RRIP_1991A
Registering unionfs 20060221-0341
Freeing unused kernel memory: 324k freed
IBM machine detected. Enabling interrupts during APM calls.
apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
usbcore: registered new driver hiddev
usbcore: registered new driver usbhid
drivers/usb/input/hid-core.c: v2.6:USB HID core driver
Linux agpgart interface v0.101 (c) Dave Jones
agpgart: Detected VIA Apollo Pro 133 chipset
agpgart: AGP aperture is 64M @ 0xd8000000
pci_hotplug: PCI Hot Plug PCI Core version: 0.5
parport_pc: VIA 686A/8231 detected
parport_pc: probing current configuration
parport_pc: Current parallel port base: 0x378
parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]
parport_pc: VIA parallel port: io=0x378, irq=7
PCI: Found IRQ 11 for device 0000:00:0e.0
PCI: Sharing IRQ 11 with 0000:00:07.5
scsi0 : IBM PCI ServeRAID 7.12.05  Build 761 <ServeRAID 4Lx>
  Vendor: IBM       Model: SERVERAID         Rev: 1.00
  Type:   Processor                          ANSI SCSI revision: 02
  Vendor: SONY      Model: SDX-500V          Rev: 0101
  Type:   Sequential-Access                  ANSI SCSI revision: 02
e100: Intel(R) PRO/100 Network Driver, 3.5.10-k2-NAPI
e100: Copyright(c) 1999-2005 Intel Corporation
PCI: Found IRQ 5 for device 0000:00:09.0
PCI: Sharing IRQ 5 with 0000:00:0d.0
e100: eth0: e100_probe: addr 0xe0124000, irq 5, MAC addr 00:03:47:E2:C5:EB
PCI: Found IRQ 5 for device 0000:00:0d.0
PCI: Sharing IRQ 5 with 0000:00:09.0
e100: eth1: e100_probe: addr 0xe0125000, irq 5, MAC addr 00:02:55:20:F4:6C
shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing disabled
serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
00:0e: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
00:0f: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
PCI: Found IRQ 11 for device 0000:00:07.5
PCI: Sharing IRQ 11 with 0000:00:0e.0
PCI: Setting latency timer of device 0000:00:07.5 to 64
 0:0:15:0: Attached scsi generic sg0 type 3
 0:1:3:0: Attached scsi generic sg1 type 1
st: Version 20050830, fixed bufsize 32768, s/g segs 256
st 0:1:3:0: Attached scsi tape st0<4>st0: try direct i/o: yes (alignment 512 B)
fuse init (API version 7.6)
st0: Block limits 2 - 16777215 bytes.
device-mapper: 4.6.0-ioctl (2006-02-17) initialised: [email]dm-devel@redhat.com[/email]
kjournald starting.  Commit interval 5 seconds
EXT3-fs: mounted filesystem with ordered data mode.
Adding 433712k swap on /dev/hdf5.  Priority:-1 extents:1 across:433712k
NET: Registered protocol family 17
e100: eth1: e100_watchdog: link up, 100Mbps, full-duplex
e100: eth1: e100_watchdog: link up, 100Mbps, full-duplex

**Ubuntu dmesg**
[42949372.960000] Linux version 2.6.15-26-server (buildd@terranova) (gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)) #1 SMP Thu Aug 3 04:09:15 UTC 2006
[42949372.960000] BIOS-provided physical RAM map:
[42949372.960000]  BIOS-e820: 0000000000000000 - 00000000000a0000 (usable)
[42949372.960000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[42949372.960000]  BIOS-e820: 0000000000100000 - 000000000fff0000 (usable)
[42949372.960000]  BIOS-e820: 000000000fff0000 - 000000000fff3000 (ACPI NVS)
[42949372.960000]  BIOS-e820: 000000000fff3000 - 0000000010000000 (ACPI data)
[42949372.960000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[42949372.960000] 0MB HIGHMEM available.
[42949372.960000] 255MB LOWMEM available.
[42949372.960000] On node 0 totalpages: 65520
[42949372.960000]   DMA zone: 4096 pages, LIFO batch:0
[42949372.960000]   DMA32 zone: 0 pages, LIFO batch:0
[42949372.960000]   Normal zone: 61424 pages, LIFO batch:15
[42949372.960000]   HighMem zone: 0 pages, LIFO batch:0
[42949372.960000] DMI 2.2 present.
[42949372.960000] ACPI: RSDP (v000 MSISYS                                ) @ 0x000f65f0
[42949372.960000] ACPI: RSDT (v001 MSISYS AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x0fff3000
[42949372.960000] ACPI: FADT (v001 MSISYS AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x0fff3040
[42949372.960000] ACPI: DSDT (v001 MSISYS AWRDACPI 0x00001000 MSFT 0x0100000c) @ 0x00000000
[42949372.960000] ACPI: PM-Timer IO Port: 0x4008
[42949372.960000] Allocating PCI resources starting at 20000000 (gap: 10000000:efff0000)
[42949372.960000] Built 1 zonelists
[42949372.960000] Kernel command line: root=/dev/hde1 ro quiet splash
[42949372.960000] Local APIC disabled by BIOS (or by default) -- you can enable it with "lapic"
[42949372.960000] mapped APIC to ffffd000 (01242000)
[42949372.960000] Initializing CPU#0
[42949372.960000] PID hash table entries: 1024 (order: 10, 16384 bytes)
[42949372.960000] Detected 866.743 MHz processor.
[42949372.960000] Using pmtmr for high-res timesource
[42949372.960000] Console: colour VGA+ 80x25
[42949373.880000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[42949373.880000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[42949373.910000] Memory: 248416k/262080k available (2086k kernel code, 13004k reserved, 621k data, 332k init, 0k highmem)
[42949373.910000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[42949374.060000] Calibrating delay using timer specific routine.. 1735.21 BogoMIPS (lpj=8676071)
[42949374.060000] Security Framework v1.0.0 initialized
[42949374.060000] SELinux:  Disabled at boot.
[42949374.060000] Mount-cache hash table entries: 512
[42949374.060000] CPU: After generic identify, caps: 0383f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[42949374.060000] CPU: After vendor identify, caps: 0383f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[42949374.060000] CPU: L1 I cache: 16K, L1 D cache: 16K
[42949374.060000] CPU: L2 cache: 256K
[42949374.060000] CPU: After all inits, caps: 0383f9ff 00000000 00000000 00000040 00000000 00000000 00000000
[42949374.060000] mtrr: v2.0 (20020519)
[42949374.060000] Enabling fast FPU save and restore... done.
[42949374.060000] Enabling unmasked SIMD FPU exception support... done.
[42949374.060000] Checking 'hlt' instruction... OK.
[42949374.100000] checking if image is initramfs... it is
[42949375.330000] Freeing initrd memory: 6790k freed
[42949375.360000] ACPI: Looking for DSDT ... not found!
[42949375.360000] ACPI: setting ELCR to 0200 (from 0e20)
[42949375.360000] CPU0: Intel Pentium III (Coppermine) stepping 06
[42949375.360000] SMP motherboard not detected.
[42949375.360000] Local APIC not detected. Using dummy APIC emulation.
[42949375.360000] Brought up 1 CPUs
[42949375.360000] NET: Registered protocol family 16
[42949375.360000] EISA bus registered
[42949375.360000] ACPI: bus type pci registered
[42949375.380000] PCI: PCI BIOS revision 2.10 entry at 0xfb2f0, last bus=1
[42949375.380000] PCI: Using configuration type 1
[42949375.380000] ACPI: Subsystem revision 20051216
[42949375.390000] ACPI: Interpreter enabled
[42949375.390000] ACPI: Using PIC for interrupt routing
[42949375.390000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[42949375.390000] PCI: Probing PCI hardware (bus 00)
[42949375.390000] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[42949375.390000] PCI quirk: region 4000-40ff claimed by vt82c586 ACPI
[42949375.390000] PCI quirk: region 6000-607f claimed by vt82c686 HW-mon
[42949375.390000] PCI quirk: region 5000-500f claimed by vt82c686 SMB
[42949375.390000] Boot video device is 0000:01:00.0
[42949375.390000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[42949375.420000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *9 10 11 14 15)
[42949375.420000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 6 7 9 10 11 14 15)
[42949375.430000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 *11 14 15)
[42949375.430000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 *10 11 14 15)
[42949375.430000] Linux Plug and Play Support v0.97 (c) Adam Belay
[42949375.430000] pnp: PnP ACPI init
[42949375.440000] pnp: PnP ACPI: found 11 devices
[42949375.440000] PnPBIOS: Disabled by ACPI PNP
[42949375.440000] PCI: Using ACPI for IRQ routing
[42949375.440000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[42949375.490000] PCI: Bridge: 0000:00:01.0
[42949375.490000]   IO window: disabled.
[42949375.490000]   MEM window: dc000000-ddffffff
[42949375.490000]   PREFETCH window: d0000000-d7ffffff
[42949375.490000] PCI: Setting latency timer of device 0000:00:01.0 to 64
[42949375.490000] audit: initializing netlink socket (disabled)
[42949375.490000] audit(1154990466.480:1): initialized
[42949375.490000] VFS: Disk quotas dquot_6.5.1
[42949375.490000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[42949375.490000] Initializing Cryptographic API
[42949375.490000] io scheduler noop registered
[42949375.490000] io scheduler anticipatory registered
[42949375.490000] io scheduler deadline registered
[42949375.490000] io scheduler cfq registered
[42949375.490000] PCI: Disabling Via external APIC routing
[42949375.490000] isapnp: Scanning for PnP cards...
[42949375.850000] isapnp: No Plug & Play device found
[42949375.890000] Real Time Clock Driver v1.12
[42949375.890000] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[42949375.890000] PNP: PS/2 controller doesn't have AUX irq; using default 12
[42949375.890000] serio: i8042 AUX port at 0x60,0x64 irq 12
[42949375.890000] serio: i8042 KBD port at 0x60,0x64 irq 1
[42949375.890000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
[42949375.890000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[42949375.890000] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[42949375.900000] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[42949375.900000] 00:08: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[42949375.900000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[42949375.900000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[42949375.900000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[42949375.900000] mice: PS/2 mouse device common for all mice
[42949375.900000] EISA: Probing bus 0 at eisa.0
[42949375.900000] Cannot allocate resource for EISA slot 4
[42949375.900000] Cannot allocate resource for EISA slot 5
[42949375.900000] Cannot allocate resource for EISA slot 6
[42949375.900000] EISA: Detected 0 cards.
[42949375.900000] NET: Registered protocol family 2
[42949375.990000] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[42949375.990000] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[42949375.990000] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[42949375.990000] TCP: Hash tables configured (established 16384 bind 16384)
[42949375.990000] TCP reno registered
[42949375.990000] TCP bic registered
[42949375.990000] NET: Registered protocol family 1
[42949375.990000] NET: Registered protocol family 8
[42949375.990000] NET: Registered protocol family 20
[42949375.990000] Using IPI No-Shortcut mode
[42949375.990000] ACPI wakeup devices: 
[42949375.990000] PCI0 USB0 USB1 MODM UAR1 UAR2 ECP1 
[42949375.990000] ACPI: (supports S0 S1 S4 S5)
[42949375.990000] Freeing unused kernel memory: 332k freed
[42949376.100000] vga16fb: initializing
[42949376.100000] vga16fb: mapped to 0xc00a0000
[42949376.210000] Console: switching to colour frame buffer device 80x25
[42949376.210000] fb0: VGA16 VGA frame buffer device
[42949376.230000] Capability LSM initialized
[42949376.310000] ACPI: CPU0 (power states: C1[C1] C2[C2])
[42949376.310000] ACPI: Processor [CPU0] (supports 2 throttling states)
[42949377.490000] VP_IDE: IDE controller at PCI slot 0000:00:07.1
[42949377.490000] PCI: VIA IRQ fixup for 0000:00:07.1, from 255 to 0
[42949377.490000] VP_IDE: chipset revision 16
[42949377.490000] VP_IDE: not 100% native mode: will probe irqs later
[42949377.490000] VP_IDE: VIA vt82c686a (rev 22) IDE UDMA66 controller on pci0000:00:07.1
[42949377.490000]     ide0: BM-DMA at 0x9000-0x9007, BIOS settings: hda:pio, hdb:pio
[42949377.490000]     ide1: BM-DMA at 0x9008-0x900f, BIOS settings: hdc:DMA, hdd:pio
[42949377.490000] Probing IDE interface ide0...
[42949378.100000] Probing IDE interface ide1...
[42949379.020000] hdc: LTN485S, ATAPI CD/DVD-ROM drive
[42949379.380000] ide1 at 0x170-0x177,0x376 on irq 15
[42949379.400000] hdc: ATAPI 48X CD-ROM drive, 120kB Cache, UDMA(33)
[42949379.400000] Uniform CD-ROM driver Revision: 3.20
[42949379.460000] PDC20269: IDE controller at PCI slot 0000:00:0b.0
[42949379.460000] **** SET: Misaligned resource pointer: cfefe0c2 Type 07 Len 0
[42949379.460000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 10
[42949379.460000] PCI: setting IRQ 10 as level-triggered
[42949379.460000] ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [LNKD] -> GSI 10 (level, low) -> IRQ 10
[42949379.460000] PDC20269: chipset revision 2
[42949379.460000] PDC20269: ROM enabled at 0x20118000
[42949379.460000] PDC20269: 100% native mode on irq 10
[42949379.460000]     ide2: BM-DMA at 0xbc00-0xbc07, BIOS settings: hde:pio, hdf:pio
[42949379.460000]     ide3: BM-DMA at 0xbc08-0xbc0f, BIOS settings: hdg:pio, hdh:pio
[42949379.460000] Probing IDE interface ide2...
[42949379.770000] hde: SAMSUNG SP2514N, ATA DISK drive
[42949380.490000] ide2 at 0xac00-0xac07,0xb002 on irq 10
[42949380.490000] Probing IDE interface ide3...
[42949380.790000] hdg: Maxtor 6Y160P0, ATA DISK drive
[42949381.090000] hdh: Maxtor 6Y160L0, ATA DISK drive
[42949381.150000] ide3 at 0xb400-0xb407,0xb802 on irq 10
[42949381.180000] hde: max request size: 1024KiB
[42949381.190000] hde: 488397168 sectors (250059 MB) w/8192KiB Cache, CHS=30401/255/63, UDMA(133)
[42949381.190000] hde: cache flushes supported
[42949381.190000]  hde: hde1 hde2 < hde5 >
[42949381.220000] hdg: max request size: 1024KiB
[42949381.220000] hdg: 320173056 sectors (163928 MB) w/7936KiB Cache, CHS=19929/255/63, UDMA(133)
[42949381.220000] hdg: cache flushes supported
[42949381.220000]  hdg: hdg1
[42949381.230000] hdh: max request size: 1024KiB
[42949381.230000] hdh: 320173056 sectors (163928 MB) w/2048KiB Cache, CHS=19929/255/63, UDMA(133)
[42949381.230000] hdh: cache flushes supported
[42949381.230000]  hdh: hdh1
[42949381.540000] SCSI subsystem initialized
[42949381.550000] **** SET: Misaligned resource pointer: cfcc30e2 Type 07 Len 0
[42949381.550000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[42949381.550000] PCI: setting IRQ 11 as level-triggered
[42949381.550000] ACPI: PCI Interrupt 0000:00:0e.0[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[42949381.570000] scsi0 : IBM PCI ServeRAID 7.12.05  Build 761 <ServeRAID 4Lx>
[42949381.580000]   Vendor: IBM       Model: SERVERAID         Rev: 1.00
[42949381.580000]   Type:   Processor                          ANSI SCSI revision: 02
[42949381.730000] usbcore: registered new driver usbfs
[42949381.730000] usbcore: registered new driver hub
[42949381.740000] USB Universal Host Controller Interface driver v2.3
[42949381.740000] ACPI: PCI Interrupt 0000:00:07.3[D] -> Link [LNKD] -> GSI 10 (level, low) -> IRQ 10
[42949381.740000] uhci_hcd 0000:00:07.3: UHCI Host Controller
[42949381.740000] uhci_hcd 0000:00:07.3: new USB bus registered, assigned bus number 1
[42949381.740000] uhci_hcd 0000:00:07.3: irq 10, io base 0x00009800
[42949381.740000] hub 1-0:1.0: USB hub found
[42949381.740000] hub 1-0:1.0: 2 ports detected
[42949381.880000] Probing IDE interface ide0...
[42949382.540000] Attempting manual resume
[42949382.580000] kjournald starting.  Commit interval 5 seconds
[42949382.580000] EXT3-fs: mounted filesystem with ordered data mode.
[42949386.800000]  0:0:15:0: Attached scsi generic sg0 type 3
[42949386.950000] Linux agpgart interface v0.101 (c) Dave Jones
[42949386.950000] agpgart: Detected VIA Apollo Pro 133 chipset
[42949386.960000] agpgart: AGP aperture is 64M @ 0xd8000000
[42949387.280000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[42949387.280000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[42949388.520000] parport_pc: VIA 686A/8231 detected
[42949388.520000] parport_pc: probing current configuration
[42949388.520000] parport_pc: Current parallel port base: 0x378
[42949388.520000] parport0: PC-style at 0x378 (0x778), irq 7, using FIFO [PCSPP,TRISTATE,COMPAT,ECP]
[42949388.530000] Floppy drive(s): fd0 is 1.44M
[42949388.530000] savage4_smbus 0000:01:00.0: Using Savage4 at d0a00000
[42949388.550000] FDC 0 is a post-1991 82077
[42949388.600000] parport_pc: VIA parallel port: io=0x378, irq=7
[42949388.810000] e100: Intel(R) PRO/100 Network Driver, 3.4.14-k4-NAPI
[42949388.810000] e100: Copyright(c) 1999-2005 Intel Corporation
[42949388.810000] **** SET: Misaligned resource pointer: cec74ca2 Type 07 Len 0
[42949388.810000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 5
[42949388.810000] PCI: setting IRQ 5 as level-triggered
[42949388.810000] ACPI: PCI Interrupt 0000:00:09.0[A] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
[42949388.830000] e100: eth0: e100_probe: addr 0xe0124000, irq 5, MAC addr 00:03:47:E2:C5:EB
[42949388.830000] ACPI: PCI Interrupt 0000:00:0d.0[A] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
[42949388.860000] e100: eth1: e100_probe: addr 0xe0125000, irq 5, MAC addr 00:02:55:20:F4:6C
[42949388.890000] ACPI: PCI Interrupt 0000:00:07.5[C] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[42949388.890000] PCI: Setting latency timer of device 0000:00:07.5 to 64
[42949388.930000] input: PC Speaker as /class/input/input0
[42949389.590000] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[42949390.270000] lp0: using parport0 (interrupt-driven).
[42949390.330000] st: Version 20050830, fixed bufsize 32768, s/g segs 256
[42949390.510000] Adding 746980k swap on /dev/hde5.  Priority:-1 extents:1 across:746980k
[42949390.630000] EXT3 FS on hde1, internal journal
[42949390.910000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[42949390.910000] md: bitmap version 4.39
[42949391.300000] NET: Registered protocol family 10
[42949391.300000] lo: Disabled Privacy Extensions
[42949391.300000] IPv6 over IPv4 tunneling driver
[42949391.730000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: [email]dm-devel@redhat.com[/email]
[42949396.800000] cdrom: open failed.
[42949397.200000] kjournald starting.  Commit interval 5 seconds
[42949397.200000] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
[42949397.200000] EXT3 FS on hdg1, internal journal
[42949397.200000] EXT3-fs: mounted filesystem with ordered data mode.
[42949397.230000] kjournald starting.  Commit interval 5 seconds
[42949397.230000] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
[42949397.230000] EXT3 FS on hdh1, internal journal
[42949397.230000] EXT3-fs: mounted filesystem with ordered data mode.
[42949397.650000] NET: Registered protocol family 15
[42949398.890000] Initializing IPsec netlink socket
[42949401.810000] eth0: no IPv6 routers present

Sincerely
Svein-P.Johnsen

---

### Post by sveinpj@broadpark.no on 2006-08-08
Thanx for no help :sad: 
Guess this forum only applies to first-time-installers? :mrgreen: 

What I did to fix it was to compile a new kernel based on the Knoppix .config file, and whoila....... ;) 

//Svein

---

