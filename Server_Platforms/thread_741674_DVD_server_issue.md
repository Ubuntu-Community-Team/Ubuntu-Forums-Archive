---
title: "DVD server issue"
date: 2008-04-01
forum: Server Platforms
---

### Post by DaylanDarby on 2008-04-01
I'm new (be gentle).  I have Ubuntu AMD64 up and running on my desktop - works great.  

I've installed Ubuntu server on an old 386 - work's great.  I swapped out the CD drive for a DVD.  The 386 can boot from the DVD, but it doesn't show up as /dev/dvd (as it does on my AMD64).    Which path to follow?

1) Reinstall Ubuntu server and hope it finds/configure the DVD
2) Install Ubuntu desktop (and disable the GUI)
3) Install some driver or configure something that one of you kind souls knows about on my current server setup

Thanks

---

### Post by dmizer on 2008-04-01
type this command:
```
dmesg -c
```
this will clear the cache of dmesg so we can get a clean dmesg output.

pop a dvd in the drive, and close it.  then, run dmesg again and post the output here.

---

### Post by DaylanDarby on 2008-04-01
Thanks for your assistance.   I did:
1) dmesg -c                       (lot's of output not captured)
2) popped in a DVD
3) dmesg                            (absolutely no output)
4) reboot  
5) dmesg > /tmp/output      (appended below. Note times 33.189693  & 33.613332)
6) ls -l /dev/s*

AM I MISSING A DRIVER?

brw-rw---- 1 root cdrom 11,   0 2008-04-01 20:23 /dev/scd0
brw-rw---- 1 root disk   8,   0 2008-04-01 20:23 /dev/sda
brw-rw---- 1 root disk   8,   1 2008-04-01 20:23 /dev/sda1
brw-rw---- 1 root disk   8,   2 2008-04-01 20:23 /dev/sda2
brw-rw---- 1 root disk   8,   5 2008-04-01 20:23 /dev/sda5
crw-rw---- 1 root audio 14,   1 2008-04-01 20:23 /dev/sequencer
crw-rw---- 1 root audio 14,   8 2008-04-01 20:23 /dev/sequencer2
crw-rw---- 1 root cdrom 21,   0 2008-04-01 20:23 /dev/sg0
crw-rw---- 1 root root  21,   1 2008-04-01 20:23 /dev/sg1
crw-rw---- 1 root root  10, 231 2008-04-01 20:23 /dev/snapshot
lrwxrwxrwx 1 root root       24 2008-04-01 20:23 /dev/sndstat -> /proc/asound/oss/sndstat
lrwxrwxrwx 1 root root        4 2008-04-01 20:23 /dev/sr0 -> scd0
lrwxrwxrwx 1 root root       15 2008-04-01 20:23 /dev/stderr -> /proc/self/fd/2
lrwxrwxrwx 1 root root       15 2008-04-01 20:23 /dev/stdin -> /proc/self/fd/0
lrwxrwxrwx 1 root root       15 2008-04-01 20:23 /dev/stdout -> /proc/self/fd/1


[    0.000000] Linux version 2.6.22-14-server (buildd@palmer) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Sun Oct 14 23:34:23 GMT 2007 (Ubuntu 2.6.22-14.46-server)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e5800 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 0000000007ef0000 (usable)
[    0.000000]  BIOS-e820: 0000000007ef0000 - 0000000007effc00 (ACPI data)
[    0.000000]  BIOS-e820: 0000000007effc00 - 0000000007f00000 (ACPI NVS)
[    0.000000]  BIOS-e820: 0000000007f00000 - 0000000008000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fff00000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 126MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 32496) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->    32496
[    0.000000]   HighMem     32496 ->    32496
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->    32496
[    0.000000] On node 0 totalpages: 32496
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 221 pages used for memmap
[    0.000000]   Normal zone: 28179 pages, LIFO batch:7
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI 2.2 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F7380 checksum 0
[    0.000000] ACPI: RSDP 000F7380, 0014 (r0 PTLTD )
[    0.000000] ACPI: RSDT 07EFCECE, 0028 (r1 PTLTD    RSDT    6040000  LTP        0)
[    0.000000] ACPI: FACP 07EFFB8C, 0074 (r1 HP     HPBDD_IP  6040000 PTL     F4240)
[    0.000000] ACPI: DSDT 07EFCEF6, 2C96 (r1  INTEL  Whitney  6040000 MSFT  100000B)
[    0.000000] ACPI: FACS 07EFFFC0, 0040
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] Allocating PCI resources starting at 10000000 (gap: 08000000:f7f00000)
[    0.000000] Built 1 zonelists.  Total pages: 32243
[    0.000000] Kernel command line: root=UUID=c545a18f-8946-4b77-bc7d-19a0004238f1 ro quiet splash
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] mapped APIC to ffffd000 (0110c000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 512 (order: 9, 2048 bytes)[    0.000000] Detected 996.829 MHz processor.
[   27.818920] Console: colour VGA+ 80x25
[   27.819124] Dentry cache hash table entries: 16384 (order: 4, 65536 bytes)
[   27.819286] Inode-cache hash table entries: 8192 (order: 3, 32768 bytes)
[   27.830692] Memory: 117492k/129984k available (2047k kernel code, 11964k reserved, 920k data, 364k init, 0k highmem)
[   27.830715] virtual kernel memory layout:
[   27.830718]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   27.830721]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
[   27.830724]     vmalloc : 0xc8800000 - 0xffbfe000   ( 883 MB)
[   27.830727]     lowmem  : 0xc0000000 - 0xc7ef0000   ( 126 MB)
[   27.830730]       .init : 0xc03eb000 - 0xc0446000   ( 364 kB)
[   27.830733]       .data : 0xc02ffcc6 - 0xc03e5f04   ( 920 kB)
[   27.830736]       .text : 0xc0100000 - 0xc02ffcc6   (2047 kB)
[   27.830744] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   27.830822] SLUB: Genslabs=22, HWalign=32, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[   27.980805] Calibrating delay using timer specific routine.. 1994.77 BogoMIPS (lpj=9973877)
[   27.980860] Security Framework v1.0.0 initialized
[   27.980879] SELinux:  Disabled at boot.
[   27.980910] Mount-cache hash table entries: 512
[   27.981168] CPU: After generic identify, caps: 0383f9ff 00000000 00000000 00000000 00000000 00000000 00000000
[   27.981191] CPU: L1 I cache: 16K, L1 D cache: 16K
[   27.981197] CPU: L2 cache: 256K
[   27.981203] CPU: After all inits, caps: 0383f9ff 00000000 00000000 00000040 00000000 00000000 00000000
[   27.981226] Compat vDSO mapped to ffffe000.
[   27.981256] Checking 'hlt' instruction... OK.
[   28.021003] SMP alternatives: switching to UP code
[   28.021339] Freeing SMP alternatives: 11k freed
[   28.021937] Early unpacking initramfs... done
[   28.648854] ACPI: Core revision 20070126
[   28.649081] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   28.651496] ACPI: setting ELCR to 0200 (from 0e80)
[   28.652924] CPU0: Intel Pentium III (Coppermine) stepping 0a
[   28.652938] SMP motherboard not detected.
[   28.652944] Local APIC not detected. Using dummy APIC emulation.
[   28.653038] Brought up 1 CPUs
[   28.653342] Booting paravirtualized kernel on bare hardware
[   28.653465] Time:  2:23:27  Date: 03/02/108
[   28.653535] NET: Registered protocol family 16
[   28.653786] EISA bus registered
[   28.653811] ACPI: bus type pci registered
[   28.654710] PCI: PCI BIOS revision 2.10 entry at 0xfd9ae, last bus=1
[   28.654716] PCI: Using configuration type 1
[   28.654720] Setting up standard PCI resources[   28.661749] ACPI: EC: Look up EC in DSDT
[   28.681539] ACPI: Interpreter enabled
[   28.681549] ACPI: (supports S0 S1 S3 S4 S5)
[   28.681580] ACPI: Using PIC for interrupt routing
[   28.716014] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   28.716042] PCI: Probing PCI hardware (bus 00)
[   28.716354] PCI quirk: region 1000-107f claimed by ICH4 ACPI/GPIO/TCO
[   28.716362] PCI quirk: region 1180-11bf claimed by ICH4 GPIO
[   28.716741] PCI: Transparent bridge - 0000:00:1e.0
[   28.716776] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   28.716922] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB_._PRT]
[   28.718844] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 *10 11 12 14 15)
[   28.718993] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 *9 10 11 12 14 15)
[   28.719135] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 *7 9 10 11 12 14 15)
[   28.719277] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[   28.719458] Linux Plug and Play Support v0.97 (c) Adam Belay
[   28.719481] pnp: PnP ACPI init
[   28.719503] ACPI: bus type pnp registered
[   28.773555] pnp: PnP ACPI: found 12 devices
[   28.773564] ACPI: ACPI bus type pnp unregistered
[   28.773574] PnPBIOS: Disabled by ACPI PNP
[   28.773703] PCI: Using ACPI for IRQ routing
[   28.773711] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   28.775676] NET: Registered protocol family 8
[   28.775681] NET: Registered protocol family 20
[   28.775716] NetLabel: Initializing
[   28.775720] NetLabel:  domain hash size = 128
[   28.775724] NetLabel:  protocols = UNLABELED CIPSOv4
[   28.775756] NetLabel:  unlabeled traffic allowed by default
[   28.775893] pnp: 00:02: iomem range 0xfff80000-0xffffffff could not be reserved
[   28.780575] Time: tsc clocksource has been installed.
[   28.806560] PCI: Bridge: 0000:00:1e.0
[   28.806566]   IO window: 2000-2fff
[   28.806577]   MEM window: ec100000-ec1fffff
[   28.806584]   PREFETCH window: 10000000-100fffff
[   28.806604] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   28.806635] NET: Registered protocol family 2
[   28.900640] IP route cache hash table entries: 1024 (order: 0, 4096 bytes)
[   28.900734] TCP established hash table entries: 4096 (order: 3, 49152 bytes)
[   28.900870] TCP bind hash table entries: 4096 (order: 3, 32768 bytes)
[   28.900964] TCP: Hash tables configured (established 4096 bind 4096)
[   28.900971] TCP reno registered
[   28.930818] checking if image is initramfs...<6>Switched to high resolution mode on CPU 0
[   29.456551]  it is
[   30.118846] Freeing initrd memory: 6922k freed
[   30.119709] audit: initializing netlink socket (disabled)
[   30.119745] audit(1207103007.960:1): initialized[   30.124803] VFS: Disk quotas dquot_6.5.1
[   30.124970] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   30.125277] io scheduler noop registered
[   30.125285] io scheduler anticipatory registered
[   30.125290] io scheduler deadline registered (default)
[   30.125346] io scheduler cfq registered
[   30.125381] Boot video device is 0000:00:02.0
[   30.125711] isapnp: Scanning for PnP cards...
[   30.482441] isapnp: No Plug & Play device found
[   30.567911] Real Time Clock Driver v1.12ac
[   30.568100] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   30.568223] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   30.568624] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   30.570340] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   30.570965] 00:0a: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   30.572599] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   30.573132] input: Macintosh mouse button emulation as /class/input/input0
[   30.573305] PNP: PS/2 Controller [PNP0303:KBC0] at 0x60,0x64 irq 1
[   30.573313] PNP: PS/2 controller doesn't have AUX irq; using default 12
[   30.820411] serio: i8042 KBD port at 0x60,0x64 irq 1
[   30.820803] mice: PS/2 mouse device common for all mice
[   30.821048] EISA: Probing bus 0 at eisa.0
[   30.821065] Cannot allocate resource for EISA slot 1
[   30.821073] Cannot allocate resource for EISA slot 2
[   30.821113] EISA: Detected 0 cards.
[   30.821334] TCP cubic registered
[   30.821373] NET: Registered protocol family 1
[   30.821436] Using IPI No-Shortcut mode
[   30.821756]   Magic number: 4:168:358
[   30.823171] Freeing unused kernel memory: 364k freed
[   30.890162] input: AT Translated Set 2 keyboard as /class/input/input1
[   31.214635] AppArmor: AppArmor initialized<5>audit(1207103008.960:2):  type=1505 info="AppArmor initialized" pid=1046
[   31.230158] fuse init (API version 7.8)
[   31.242635] Failure registering capabilities with primary security module.
[   31.284810] ACPI: Invalid PBLK length [5]
[   32.811184] SCSI subsystem initialized
[   32.847594] libata version 2.21 loaded.
[   32.853584] usbcore: registered new interface driver usbfs
[   32.853639] usbcore: registered new interface driver hub
[   32.853708] usbcore: registered new device driver usb
[   32.853785] ata_piix 0000:00:1f.1: version 2.11
[   32.853904] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   32.857235] scsi0 : ata_piix
[   32.857372] scsi1 : ata_piix
[   32.857592] ata1: PATA max UDMA/66 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x00011800 irq 14[   32.857601] ata2: PATA max UDMA/66 cmd 0x00010170 ctl 0x00010376 bmdma 0x00011808 irq 15
[   32.857756] USB Universal Host Controller Interface driver v3.0
[   33.171951] Floppy drive(s): fd0 is 1.44M
[   33.189693] ata1.00: ATAPI: PIONEER DVD-RW  DVR-115D, 1.13, max UDMA/66
[   33.211336] FDC 0 is a National Semiconductor PC87306
[   33.389595] ata1.00: configured for UDMA/66
[   33.569730] ata2.00: ATA-7: Maxtor 6Y160P0, YAR41BW0, max UDMA/133
[   33.569740] ata2.00: 320173056 sectors, multi 16: LBA48
[   33.569761] ata2.00: limited to UDMA/33 due to 40-wire cable
[   33.609715] ata2.00: configured for UDMA/33
[   33.613332] scsi 0:0:0:0: CD-ROM            PIONEER  DVD-RW  DVR-115D 1.13 PQ: 0 ANSI: 5
[   33.614294] scsi 1:0:0:0: Direct-Access     ATA      Maxtor 6Y160P0   YAR4 PQ: 0 ANSI: 5
[   33.621549] PCI: Enabling device 0000:00:1f.2 (0000 -> 0001)
[   33.621904] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[   33.621913] PCI: setting IRQ 11 as level-triggered
[   33.621919] ACPI: PCI Interrupt 0000:00:1f.2[D] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[   33.621943] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   33.621950] uhci_hcd 0000:00:1f.2: UHCI Host Controller
[   33.622244] uhci_hcd 0000:00:1f.2: new USB bus registered, assigned bus number 1
[   33.622282] uhci_hcd 0000:00:1f.2: irq 11, io base 0x00001820
[   33.622582] usb usb1: configuration #1 chosen from 1 choice
[   33.622648] hub 1-0:1.0: USB hub found
[   33.622667] hub 1-0:1.0: 2 ports detected
[   33.730191] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 7
[   33.730202] PCI: setting IRQ 7 as level-triggered
[   33.730209] ACPI: PCI Interrupt 0000:01:04.0[A] -> Link [LNKC] -> GSI 7 (level, low) -> IRQ 7
[   33.730227] 3c59x: Donald Becker and others.
[   33.730239] 0000:01:04.0: 3Com PCI 3c905C Tornado at c881a000.
[   33.782107] sd 1:0:0:0: [sda] 320173056 512-byte hardware sectors (163929 MB)
[   33.782140] sd 1:0:0:0: [sda] Write Protect is off
[   33.782147] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   33.782182] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   33.782289] sd 1:0:0:0: [sda] 320173056 512-byte hardware sectors (163929 MB)
[   33.782310] sd 1:0:0:0: [sda] Write Protect is off
[   33.782316] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   33.782348] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   33.782356]  sda: sda1 sda2 <sr0: scsi3-mmc drive: 125x/125x writer cd/rw xa/form2 cdda tray
[   33.793416] Uniform CD-ROM driver Revision: 3.20
[   33.793551] sr 0:0:0:0: Attached scsi CD-ROM sr0
[   33.822927]  sda5 >
[   33.823180] sd 1:0:0:0: [sda] Attached SCSI disk
[   33.851226] sr 0:0:0:0: Attached scsi generic sg0 type 5
[   33.851273] sd 1:0:0:0: Attached scsi generic sg1 type 0
[   34.009233] usb 1-1: new low speed USB device using uhci_hcd and address 2
[   34.182439] Attempting manual resume
[   34.182449] swsusp: Resume From Partition 8:5
[   34.182454] PM: Checking swsusp image.
[   34.182842] PM: Resume from disk failed.
[   34.201736] usb 1-1: configuration #1 chosen from 1 choice
[   34.241983] usbcore: registered new interface driver hiddev
[   34.258924] input: Microsoft Microsoft 3-Button Mouse with IntelliEye(TM) as /class/input/input2
[   34.258978] input: USB HID v1.10 Mouse [Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)] on usb-0000:00:1f.2-1
[   34.259014] usbcore: registered new interface driver usbhid
[   34.259023] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   34.330299] kjournald starting.  Commit interval 5 seconds
[   34.330328] EXT3-fs: mounted filesystem with ordered data mode.
[   37.991614] eth0:  setting full-duplex.
[   40.138603] NET: Registered protocol family 17
[   40.933111] Linux agpgart interface v0.102 (c) Dave Jones
[   41.160056] agpgart: Detected an Intel i815 Chipset.
[   41.170369] agpgart: AGP aperture is 64M @ 0xf0000000
[   41.200578] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   41.206122] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   41.238966] intel_rng: FWH not detected
[   41.261979] i810_smbus 0000:00:02.0: i810/i815 i2c device found.
[   41.578117] iTCO_vendor_support: vendor-support=0
[   41.587219] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007)
[   41.587344] iTCO_wdt: Found a ICH TCO device (Version=1, TCOBASE=0x1060)
[   41.587399] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   42.565725] input: PC Speaker as /class/input/input3
[   42.787028] parport_pc 00:0b: reported by Plug and Play ACPI
[   42.787068] parport0: PC-style at 0x278, irq 5 [PCSPP,TRISTATE,EPP]
[   43.441417] PCI: Enabling device 0000:00:1f.5 (0000 -> 0001)
[   43.441764] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 9
[   43.441771] PCI: setting IRQ 9 as level-triggered
[   43.441777] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKB] -> GSI 9 (level, low) -> IRQ 9
[   43.441813] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   44.036553] intel8x0_measure_ac97_clock: measured 51535 usecs
[   44.036564] intel8x0: clocking to 48000
[   45.171595] loop: module loaded
[   45.215952] lp0: using parport0 (interrupt-driven).
[   45.457320] Adding 353388k swap on /dev/sda5.  Priority:-1 extents:1 across:353388k
[   45.800709] EXT3 FS on sda1, internal journal
[   47.279299] NET: Registered protocol family 10
[   47.279537] lo: Disabled Privacy Extensions
[   53.095236] Failure registering capabilities with primary security module.[   54.065950] ppdev: user-space parallel port driver
[   54.527084] audit(1207103033.314:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=3988 profile="/usr/sbin/cupsd"
[   57.709207] eth0: no IPv6 routers present

---

### Post by mrsteveman1 on 2008-04-02
It should be /dev/sr0

---

