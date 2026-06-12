---
title: "Problem with raid5 setup, array not assembling on boot"
date: 2009-02-17
forum: Server Platforms
---

### Post by arj03 on 2009-02-17
Hi

I'm having trouble assembling my md0 array. It seems that for some
reason the discs got different UUID's. So that only one disc is added
to the array now and because of that it won't start. Is there any way
I can change the raid UUID for the other discs?

Here's the complete story with lots of debugging information.

I had a raid 5 array consisting of 4 identical Western Digital
WD5000AAKS, where one of the drives died on me.
I physically removed the dead drive from the computer and sent it to
WD for RMA. When i finally got back a new drive I plugged it in, made
a primary partition on the drive using fdisk. Then I did an "mdadm --
manage --add /dev/md0 /dev/sda1" to add the replacement drive to the
raid array. The new drive showed up as a Spare drive and I could not
get the array to start the recovery process. I did not do an "mdadm --
manage --remove ..." of the failed drive.
I also tried an "mdadm --assemble --update=resync /dev/md0 /dev/sda1 /
dev/sdb1 /dev/sdc1 /dev/sdd1" but this just reported that it was
unable to do this as the array was active. I don't know if this
matters, but I though I'd better mention it.

The next time I booted the computer "/dev/md0" was no longer active and
the drives attached to the array now only consisted of "sdc1". All the
original drives still contain a Linux raid partition as reported by
fdisk.
I have tried everything I can think of, but with no success, so please
if anyone has a suggestion, it would be greatly appreciated.
I have included some information to help diagnose the problem, please
ask if you need more information.

Thank you in advance.

Computer specs:
----------------------
Athlon64 3000+
Asus A8N-E (nVidia nForce 4 Ultra chipset)
512 MB DDR
Radeon x600 PCI-E videocard
Maxtor 80 GB PATA as system drive
4x Western Digital WD5000AAKS 500 GB SATA drives configured in SW Raid
5 array

------------------------------------------------
bo@QB3:~$ cat /proc/mdstat
Personalities : [raid6] [raid5] [raid4]
md0 : inactive sdc1[2](S)
      488383936 blocks

unused devices: <none>
-------------------------------------------------

dmesg
----------------------------------------------------------------------------------------------
```
[   24.336033] ACPI: PCI Interrupt Link [LUB2] (IRQs 3 4 5 7 9 10 *11
12 14 15)
[   24.336360] ACPI: PCI Interrupt Link [LIDE] (IRQs 3 4 5 7 9 10 11
12 14 15) *0, disabled.
[   24.336700] ACPI: PCI Interrupt Link [LSID] (IRQs 3 4 5 7 9 10 *11
12 14 15)
[   24.337044] ACPI: PCI Interrupt Link [LFID] (IRQs 3 4 *5 7 9 10 11
12 14 15)
[   24.337386] ACPI: PCI Interrupt Link [LPCA] (IRQs 3 4 5 7 9 10 11
12 14 15) *0, disabled.
[   24.337763] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0, disabled.
[   24.338133] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0, disabled.
[   24.338504] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0, disabled.
[   24.338881] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0, disabled.
[   24.339164] ACPI: PCI Interrupt Link [APC5] (IRQs *16), disabled.
[   24.339549] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22 23) *0,
disabled.
[   24.339954] ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22 23) *0,
disabled.
[   24.340339] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0,
disabled.
[   24.340724] ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22 23) *0,
disabled.
[   24.341107] ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22 23) *0,
disabled.
[   24.341493] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0,
disabled.
[   24.341876] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22 23) *0,
disabled.
[   24.342262] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0,
disabled.
[   24.342657] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0,
disabled.
[   24.343053] ACPI: PCI Interrupt Link [APSJ] (IRQs 20 21 22 23) *0,
disabled.
[   24.343451] ACPI: PCI Interrupt Link [APCP] (IRQs 20 21 22 23) *0,
disabled.
[   24.346869] Linux Plug and Play Support v0.97 (c) Adam Belay
[   24.346878] pnp: PnP ACPI init
[   24.353055] pnp: PnP ACPI: found 13 devices
[   24.353059] PnPBIOS: Disabled by ACPI PNP
[   24.353105] PCI: Using ACPI for IRQ routing
[   24.353110] PCI: If a device doesn't work, try "pci=routeirq".  If
it helps, post a report
[   24.411114] NET: Registered protocol family 8
[   24.411116] NET: Registered protocol family 20
[   24.411523] pnp: 00:01: ioport range 0x4000-0x407f could not be
reserved
[   24.411526] pnp: 00:01: ioport range 0x4080-0x40ff has been
reserved
[   24.411529] pnp: 00:01: ioport range 0x4400-0x447f has been
reserved
[   24.411532] pnp: 00:01: ioport range 0x4480-0x44ff could not be
reserved
[   24.411535] pnp: 00:01: ioport range 0x4800-0x487f has been
reserved
[   24.411537] pnp: 00:01: ioport range 0x4880-0x48ff has been
reserved
[   24.411743] PCI: Bridge: 0000:00:09.0
[   24.411745]   IO window: disabled.
[   24.411748]   MEM window: disabled.
[   24.411750]   PREFETCH window: disabled.
[   24.411753] PCI: Bridge: 0000:00:0b.0
[   24.411754]   IO window: disabled.
[   24.411756]   MEM window: disabled.
[   24.411758]   PREFETCH window: disabled.
[   24.411761] PCI: Bridge: 0000:00:0c.0
[   24.411762]   IO window: disabled.
[   24.411764]   MEM window: disabled.
[   24.411766]   PREFETCH window: disabled.
[   24.411769] PCI: Bridge: 0000:00:0d.0
[   24.411770]   IO window: disabled.
[   24.411773]   MEM window: disabled.
[   24.411775]   PREFETCH window: disabled.
[   24.411777] PCI: Bridge: 0000:00:0e.0
[   24.411779]   IO window: a000-afff
[   24.411782]   MEM window: d0000000-d1ffffff
[   24.411785]   PREFETCH window: c0000000-cfffffff
[   24.411793] PCI: Setting latency timer of device 0000:00:09.0 to 64
[   24.411800] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[   24.411806] PCI: Setting latency timer of device 0000:00:0c.0 to 64
[   24.411812] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[   24.411817] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[   24.411841] NET: Registered protocol family 2
[   24.451474] IP route cache hash table entries: 4096 (order: 2,
16384 bytes)
[   24.451546] TCP established hash table entries: 16384 (order: 5,
131072 bytes)
[   24.451666] TCP bind hash table entries: 8192 (order: 4, 65536
bytes)
[   24.451726] TCP: Hash tables configured (established 16384 bind
8192)
[   24.451728] TCP reno registered
[   24.463484] checking if image is initramfs... it is
[   25.083388] Freeing initrd memory: 7033k freed
[   25.083777] audit: initializing netlink socket (disabled)
[   25.083791] audit(1234713454.512:1): initialized
[   25.083887] VFS: Disk quotas dquot_6.5.1
[   25.083902] Dquot-cache hash table entries: 1024 (order 0, 4096
bytes)
[   25.083944] io scheduler noop registered
[   25.083947] io scheduler anticipatory registered
[   25.083949] io scheduler deadline registered
[   25.083955] io scheduler cfq registered (default)
[   25.106347] PCI: Found disabled HT MSI Mapping on 0000:00:0b.0
[   25.106354] PCI: Found enabled HT MSI Mapping on 0000:00:00.0
[   25.106360] PCI: Found disabled HT MSI Mapping on 0000:00:0c.0
[   25.106367] PCI: Found enabled HT MSI Mapping on 0000:00:00.0
[   25.106373] PCI: Found disabled HT MSI Mapping on 0000:00:0d.0
[   25.106380] PCI: Found enabled HT MSI Mapping on 0000:00:00.0
[   25.106386] PCI: Found disabled HT MSI Mapping on 0000:00:0e.0
[   25.106393] PCI: Found enabled HT MSI Mapping on 0000:00:00.0
[   25.106536] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[   25.106555] assign_interrupt_mode Found MSI capability
[   25.106558] Allocate Port Service[0000:00:0b.0:pcie00]
[   25.106617] PCI: Setting latency timer of device 0000:00:0c.0 to 64
[   25.106637] assign_interrupt_mode Found MSI capability
[   25.106640] Allocate Port Service[0000:00:0c.0:pcie00]
[   25.106694] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[   25.106714] assign_interrupt_mode Found MSI capability
[   25.106716] Allocate Port Service[0000:00:0d.0:pcie00]
[   25.106771] PCI: Setting latency timer of device 0000:00:0e.0 to 64
[   25.106790] assign_interrupt_mode Found MSI capability
[   25.106793] Allocate Port Service[0000:00:0e.0:pcie00]
[   25.106888] isapnp: Scanning for PnP cards...
[   25.458949] isapnp: No Plug & Play device found
[   25.479230] Real Time Clock Driver v1.12ac
[   25.479274] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports,
IRQ sharing enabled
[   25.479378] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   25.479874] 00:07: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   25.480056] mice: PS/2 mouse device common for all mice
[   25.480490] RAMDISK driver initialized: 16 RAM disks of 65536K size
1024 blocksize
[   25.480685] input: Macintosh mouse button emulation as /class/input/
input0
[   25.480711] Uniform Multi-Platform E-IDE driver Revision:
7.00alpha2
[   25.480715] ide: Assuming 33MHz system bus speed for PIO modes;
override with idebus=xx
[   25.480882] PNP: No PS/2 controller found. Probing ports directly.
[   25.484451] serio: i8042 KBD port at 0x60,0x64 irq 1
[   25.484457] serio: i8042 AUX port at 0x60,0x64 irq 12
[   25.484618] EISA: Probing bus 0 at eisa.0
[   25.484630] Cannot allocate resource for EISA slot 4
[   25.484641] EISA: Detected 0 cards.
[   25.514675] TCP cubic registered
[   25.514681] NET: Registered protocol family 1
[   25.514698] Using IPI No-Shortcut mode
[   25.514740] ACPI: (supports S0 S1 S3 S4 S5)
[   25.514789]   Magic number: 13:135:993
[   25.514798]   hash matches device ttyd6
[   25.515176] Freeing unused kernel memory: 328k freed
[   25.517621] Time: tsc clocksource has been installed.
[   26.720852] Capability LSM initialized
[   26.749423] ACPI: Fan [FAN] (on)
[   26.752744] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND,
Processor Device is not present [20060707]
[   26.754042] ACPI: Thermal Zone [THRM] (40 C)
[   26.808319] raid5: automatically using best checksumming function:
pIII_sse
[   26.827436]    pIII_sse  :  5543.000 MB/sec
[   26.827439] raid5: using function: pIII_sse (5543.000 MB/sec)
[   26.895345] raid6: int32x1    775 MB/s
[   26.963286] raid6: int32x2    786 MB/s
[   27.031161] raid6: int32x4    655 MB/s
[   27.099041] raid6: int32x8    487 MB/s
[   27.166898] raid6: mmxx1     1451 MB/s
[   27.234778] raid6: mmxx2     2656 MB/s
[   27.302665] raid6: sse1x1    1345 MB/s
[   27.370549] raid6: sse1x2    2251 MB/s
[   27.438421] raid6: sse2x1    2345 MB/s
[   27.506326] raid6: sse2x2    2949 MB/s
[   27.506328] raid6: using algorithm sse2x2 (2949 MB/s)
[   27.506331] md: raid6 personality registered for level 6
[   27.506333] md: raid5 personality registered for level 5
[   27.506335] md: raid4 personality registered for level 4
[   27.854628] usbcore: registered new interface driver usbfs
[   27.854649] usbcore: registered new interface driver hub
[   27.854669] usbcore: registered new device driver usb
[   27.855836] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 23
[   27.855846] ACPI: PCI Interrupt 0000:00:02.1[B] -> Link [APCL] ->
GSI 23 (level, low) -> IRQ 16
[   27.855857] PCI: Setting latency timer of device 0000:00:02.1 to 64
[   27.855860] ehci_hcd 0000:00:02.1: EHCI Host Controller
[   27.856008] ehci_hcd 0000:00:02.1: new USB bus registered, assigned
bus number 1
[   27.856038] ehci_hcd 0000:00:02.1: debug port 1
[   27.856042] PCI: cache line size of 64 is not supported by device
0000:00:02.1
[   27.856051] ehci_hcd 0000:00:02.1: irq 16, io mem 0xfeb00000
[   27.856057] ehci_hcd 0000:00:02.1: USB 2.0 started, EHCI 1.00,
driver 10 Dec 2004
[   27.856130] usb usb1: configuration #1 chosen from 1 choice
[   27.856154] hub 1-0:1.0: USB hub found
[   27.856163] hub 1-0:1.0: 10 ports detected
[   27.874582] SCSI subsystem initialized
[   27.878978] libata version 2.20 loaded.
[   27.953978] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller
(OHCI) Driver
[   27.969627] sata_nv 0000:00:07.0: version 3.3
[   27.970178] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 22
[   27.970188] ACPI: PCI Interrupt 0000:00:07.0[A] -> Link [APSI] ->
GSI 22 (level, low) -> IRQ 17
[   27.970197] sata_nv 0000:00:07.0: Using ADMA mode
[   27.970210] PCI: Setting latency timer of device 0000:00:07.0 to 64
[   27.970304] ata1: SATA max UDMA/133 cmd 0xe085a480 ctl 0xe085a4a0
bmdma 0x0001d800 irq 17
[   27.970352] ata2: SATA max UDMA/133 cmd 0xe085a580 ctl 0xe085a5a0
bmdma 0x0001d808 irq 17
[   27.970362] scsi0 : sata_nv
[   27.977174] forcedeth.c: Reverse Engineered nForce ethernet driver.
Version 0.59.
[   28.436831] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   28.450940] ata1.00: ata_hpa_resize 1: sectors = 976773168,
hpa_sectors = 976773168
[   28.450946] ata1.00: ATA-8: WDC WD5000AAKS-00A7B0, 01.03B01, max
UDMA/133
[   28.450949] ata1.00: 976773168 sectors, multi 1: LBA48 NCQ (depth
31/32)
[   28.457294] ata1.00: ata_hpa_resize 1: sectors = 976773168,
hpa_sectors = 976773168
[   28.457297] ata1.00: configured for UDMA/133
[   28.457307] scsi1 : sata_nv
[   28.924026] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   28.943058] ata2.00: ata_hpa_resize 1: sectors = 976773168,
hpa_sectors = 976773168
[   28.943062] ata2.00: ATA-7: WDC WD5000AAKS-00TMA0, 12.01C01, max
UDMA/133
[   28.943065] ata2.00: 976773168 sectors, multi 1: LBA48 NCQ (depth
31/32)
[   28.949059] ata2.00: ata_hpa_resize 1: sectors = 976773168,
hpa_sectors = 976773168
[   28.949063] ata2.00: configured for UDMA/133
[   28.949159] scsi 0:0:0:0: Direct-Access     ATA      WDC
WD5000AAKS-0 01.0 PQ: 0 ANSI: 5
[   28.949167] ata1: bounce limit 0xFFFFFFFFFFFFFFFF, segment boundary
0xFFFFFFFF, hw segs 61
[   28.949834] scsi 1:0:0:0: Direct-Access     ATA      WDC
WD5000AAKS-0 12.0 PQ: 0 ANSI: 5
[   28.949839] ata2: bounce limit 0xFFFFFFFFFFFFFFFF, segment boundary
0xFFFFFFFF, hw segs 61
[   28.950882] ACPI: PCI Interrupt Link [APSJ] enabled at IRQ 21
[   28.950891] ACPI: PCI Interrupt 0000:00:08.0[A] -> Link [APSJ] ->
GSI 21 (level, low) -> IRQ 18
[   28.950900] sata_nv 0000:00:08.0: Using ADMA mode
[   28.950913] PCI: Setting latency timer of device 0000:00:08.0 to 64
[   28.950977] ata3: SATA max UDMA/133 cmd 0xe085c480 ctl 0xe085c4a0
bmdma 0x0001c400 irq 18
[   28.951025] ata4: SATA max UDMA/133 cmd 0xe085c580 ctl 0xe085c5a0
bmdma 0x0001c408 irq 18
[   28.951036] scsi2 : sata_nv
[   29.415213] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   29.428909] ata3.00: ata_hpa_resize 1: sectors = 976773168,
hpa_sectors = 976773168
[   29.428914] ata3.00: ATA-7: WDC WD5000AAKS-00TMA0, 12.01C01, max
UDMA/133
[   29.428917] ata3.00: 976773168 sectors, multi 1: LBA48 NCQ (depth
31/32)
[   29.435975] ata3.00: ata_hpa_resize 1: sectors = 976773168,
hpa_sectors = 976773168
[   29.435979] ata3.00: configured for UDMA/133
[   29.435985] scsi3 : sata_nv
[   29.902408] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   29.921354] ata4.00: ata_hpa_resize 1: sectors = 976773168,
hpa_sectors = 976773168
[   29.921359] ata4.00: ATA-7: WDC WD5000AAKS-00TMA0, 12.01C01, max
UDMA/133
[   29.921361] ata4.00: 976773168 sectors, multi 1: LBA48 NCQ (depth
31/32)
[   29.926594] ata4.00: ata_hpa_resize 1: sectors = 976773168,
hpa_sectors = 976773168
[   29.926598] ata4.00: configured for UDMA/133
[   29.926683] scsi 2:0:0:0: Direct-Access     ATA      WDC
WD5000AAKS-0 12.0 PQ: 0 ANSI: 5
[   29.926691] ata3: bounce limit 0xFFFFFFFFFFFFFFFF, segment boundary
0xFFFFFFFF, hw segs 61
[   29.927357] scsi 3:0:0:0: Direct-Access     ATA      WDC
WD5000AAKS-0 12.0 PQ: 0 ANSI: 5
[   29.927363] ata4: bounce limit 0xFFFFFFFFFFFFFFFF, segment boundary
0xFFFFFFFF, hw segs 61
[   29.933004] NFORCE-CK804: IDE controller at PCI slot 0000:00:06.0
[   29.933023] NFORCE-CK804: chipset revision 242
[   29.933025] NFORCE-CK804: not 100% native mode: will probe irqs
later
[   29.933031] NFORCE-CK804: 0000:00:06.0 (rev f2) UDMA133 controller
[   29.933039]     ide0: BM-DMA at 0xf000-0xf007, BIOS settings:
hda:DMA, hdb:DMA
[   29.933048]     ide1: BM-DMA at 0xf008-0xf00f, BIOS settings:
hdc:DMA, hdd:DMA
[   29.933055] Probing IDE interface ide0...
[   30.441576] hdb: MAXTOR 6L080L4, ATA DISK drive
[   30.497743] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   30.513485] Probing IDE interface ide1...
[   31.527780] hdd: LITE-ON DVDRW SOHW-1693S, ATAPI CD/DVD-ROM drive
[   31.584133] ide1 at 0x170-0x177,0x376 on irq 15
[   31.585950] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 20
[   31.585959] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [APCF] ->
GSI 20 (level, low) -> IRQ 19
[   31.585971] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   31.585974] ohci_hcd 0000:00:02.0: OHCI Host Controller
[   31.586104] ohci_hcd 0000:00:02.0: new USB bus registered, assigned
bus number 2
[   31.586119] ohci_hcd 0000:00:02.0: irq 19, io mem 0xd2004000
[   31.642384] usb usb2: configuration #1 chosen from 1 choice
[   31.642526] hub 2-0:1.0: USB hub found
[   31.642536] hub 2-0:1.0: 10 ports detected
[   31.744700] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 23
[   31.744705] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [APCH] ->
GSI 23 (level, low) -> IRQ 16
[   31.744711] PCI: Setting latency timer of device 0000:00:0a.0 to 64
[   31.744718] forcedeth: using HIGHDMA
[   32.046853] usb 2-2: new low speed USB device using ohci_hcd and
address 2
[   32.261067] usb 2-2: configuration #1 chosen from 1 choice
[   32.262827] eth0: forcedeth.c: subsystem: 01043:8141 bound to
0000:00:0a.0
[   32.273465] usbcore: registered new interface driver hiddev
[   32.285568] input: Logitech USB Receiver as /class/input/input1
[   32.285584] input: USB HID v1.10 Keyboard [Logitech USB Receiver]
on usb-0000:00:02.0-2
[   32.289857] hdb: max request size: 128KiB
[   32.295550] input: Logitech USB Receiver as /class/input/input2
[   32.295598] input,hiddev96: USB HID v1.10 Mouse [Logitech USB
Receiver] on usb-0000:00:02.0-2
[   32.295612] usbcore: registered new interface driver usbhid
[   32.295615] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   32.296540] hdb: 156355584 sectors (80054 MB) w/1819KiB Cache,
CHS=65535/16/63, UDMA(133)
[   32.298715] hdb: cache flushes supported
[   32.298760]  hdb: hdb1 hdb2 hdb3 <<5>SCSI device sda: 976773168 512-
byte hdwr sectors (500108 MB)
[   32.310538] sda: Write Protect is off
[   32.310541] sda: Mode Sense: 00 3a 00 00
[   32.310554] SCSI device sda: write cache: enabled, read cache:
enabled, doesn't support DPO or FUA
[   32.310604] SCSI device sda: 976773168 512-byte hdwr sectors
(500108 MB)
[   32.310612] sda: Write Protect is off
[   32.310614] sda: Mode Sense: 00 3a 00 00
[   32.310625] SCSI device sda: write cache: enabled, read cache:
enabled, doesn't support DPO or FUA
[   32.310628]  sda: sda1
[   32.330036] sd 0:0:0:0: Attached scsi disk sda
[   32.330210] SCSI device sdb: 976773168 512-byte hdwr sectors
(500108 MB)
[   32.330220] sdb: Write Protect is off
[   32.330223] sdb: Mode Sense: 00 3a 00 00
[   32.330235] SCSI device sdb: write cache: enabled, read cache:
enabled, doesn't support DPO or FUA
[   32.330279] SCSI device sdb: 976773168 512-byte hdwr sectors
(500108 MB)
[   32.330286] sdb: Write Protect is off
[   32.330288] sdb: Mode Sense: 00 3a 00 00
[   32.330300] SCSI device sdb: write cache: enabled, read cache:
enabled, doesn't support DPO or FUA
[   32.330302]  sdb: hdb5 >
[   32.343154] hdd: ATAPI 48X DVD-ROM DVD-R CD-R/RW drive, 2048kB
Cache, UDMA(66)
[   32.343162] Uniform CD-ROM driver Revision: 3.20
[   32.343203]  sdb1
[   32.343500] sd 1:0:0:0: Attached scsi disk sdb
[   32.344897] SCSI device sdc: 976773168 512-byte hdwr sectors
(500108 MB)
[   32.344910] sdc: Write Protect is off
[   32.344912] sdc: Mode Sense: 00 3a 00 00
[   32.352417] SCSI device sdc: write cache: enabled, read cache:
enabled, doesn't support DPO or FUA
[   32.352515] SCSI device sdc: 976773168 512-byte hdwr sectors
(500108 MB)
[   32.352525] sdc: Write Protect is off
[   32.352527] sdc: Mode Sense: 00 3a 00 00
[   32.352539] SCSI device sdc: write cache: enabled, read cache:
enabled, doesn't support DPO or FUA
[   32.352542]  sdc: sdc1
[   32.362187] sd 2:0:0:0: Attached scsi disk sdc
[   32.363799] SCSI device sdd: 976773168 512-byte hdwr sectors
(500108 MB)
[   32.364084] sdd: Write Protect is off
[   32.364086] sdd: Mode Sense: 00 3a 00 00
[   32.364386] SCSI device sdd: write cache: enabled, read cache:
enabled, doesn't support DPO or FUA
[   32.364437] SCSI device sdd: 976773168 512-byte hdwr sectors
(500108 MB)
[   32.364445] sdd: Write Protect is off
[   32.364447] sdd: Mode Sense: 00 3a 00 00
[   32.364459] SCSI device sdd: write cache: enabled, read cache:
enabled, doesn't support DPO or FUA
[   32.364462]  sdd: sdd1
[   32.373655] sd 3:0:0:0: Attached scsi disk sdd
[   32.378216] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   32.378384] sd 1:0:0:0: Attached scsi generic sg1 type 0
[   32.378502] sd 2:0:0:0: Attached scsi generic sg2 type 0
[   32.378619] sd 3:0:0:0: Attached scsi generic sg3 type 0
[   32.471237] md: md0 stopped.
[   32.480880] md: bind<sda1>
[   32.481016] md: bind<sdd1>
[   32.496022] md: md0 stopped.
[   32.496032] md: unbind<sdd1>
[   32.496042] md: export_rdev(sdd1)
[   32.496053] md: unbind<sda1>
[   32.496057] md: export_rdev(sda1)
[   32.501961] md: bind<sdc1>
[   32.505427] md: array md0 already has disks!
[   32.508892] md: array md0 already has disks!
[   32.512458] md: array md0 already has disks!
[   32.515856] md: array md0 already has disks!
[   32.519230] md: array md0 already has disks!
[   32.522720] md: array md0 already has disks!
[   32.526149] md: array md0 already has disks!
[   32.530245] md: array md0 already has disks!
[   32.533813] md: array md0 already has disks!
[   32.537311] md: array md0 already has disks!
[   32.540744] md: array md0 already has disks!
[   32.544144] md: array md0 already has disks!
[   32.547638] md: array md0 already has disks!
[   32.551069] md: array md0 already has disks!
[   32.554506] md: array md0 already has disks!
[   32.557938] md: array md0 already has disks!
[   32.561429] md: array md0 already has disks!
[   32.565008] md: array md0 already has disks!
[   32.569542] md: array md0 already has disks!
[   32.573085] md: array md0 already has disks!
[   32.576541] md: array md0 already has disks!
[   32.580050] md: array md0 already has disks!
[   32.583666] md: array md0 already has disks!
[   32.587226] md: array md0 already has disks!
[   32.590727] md: array md0 already has disks!
[   32.594126] md: array md0 already has disks!
[   32.598215] md: array md0 already has disks!
[   32.601685] md: array md0 already has disks!
[   32.605041] md: array md0 already has disks!
[   32.608406] md: array md0 already has disks!
[   32.611835] md: array md0 already has disks!
[   32.615163] md: array md0 already has disks!
[   32.618561] md: array md0 already has disks!
[   32.621886] md: array md0 already has disks!
[   32.625249] md: array md0 already has disks!
[   32.628644] md: array md0 already has disks!
[   32.632008] md: array md0 already has disks!
[   32.635443] md: array md0 already has disks!
[   32.638836] md: array md0 already has disks!
[   32.642200] md: array md0 already has disks!
[   32.645663] md: array md0 already has disks!
[   32.649062] md: array md0 already has disks!
[   32.652715] md: array md0 already has disks!
[   32.656835] md: array md0 already has disks!
[   32.660502] md: array md0 already has disks!
[   32.664080] md: array md0 already has disks!
[   32.664871] Attempting manual resume
[   32.664874] swsusp: Resume From Partition 3:69
[   32.664876] PM: Checking swsusp image.
[   32.667637] md: array md0 already has disks!
[   32.671106] md: array md0 already has disks!
[   32.674437] md: array md0 already has disks!
[   32.677478] PM: Resume from disk failed.
[   32.677880] md: array md0 already has disks!
[   32.681747] md: array md0 already has disks!
[   32.687099] md: array md0 already has disks!
[   32.692842] md: array md0 already has disks!
[   32.696411] md: array md0 already has disks!
[   32.699877] md: array md0 already has disks!
[   32.703343] md: array md0 already has disks!
[   32.706670] md: array md0 already has disks!
[   32.710067] md: array md0 already has disks!
[   32.713566] md: array md0 already has disks!
[   32.714724] kjournald starting.  Commit interval 5 seconds
[   32.714737] EXT3-fs: mounted filesystem with ordered data mode.
[   32.717218] md: array md0 already has disks!
[   32.721342] md: array md0 already has disks!
[   32.724981] md: array md0 already has disks!
[   32.728654] md: array md0 already has disks!
[   32.732501] md: array md0 already has disks!
[   32.736020] md: array md0 already has disks!
[   32.739357] md: array md0 already has disks!
[   32.742753] md: array md0 already has disks!
[   32.746267] md: array md0 already has disks!
[   43.466955] eth0: no link during initialization.
[   43.882437] md: md0 stopped.
[   43.882447] md: unbind<sdc1>
[   43.882457] md: export_rdev(sdc1)
[   43.886946] md: bind<sdc1>
[   43.893950] md: md0 stopped.
[   43.893960] md: unbind<sdc1>
[   43.893970] md: export_rdev(sdc1)
[   43.898664] md: bind<sdc1>
[   44.819794] NET: Registered protocol family 17
[   45.219229] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   45.222244] shpchp: Standard Hot Plug PCI Controller Driver
version: 0.4
[   45.806106] i2c_adapter i2c-0: nForce2 SMBus adapter at 0x4c00
[   45.806136] i2c_adapter i2c-1: nForce2 SMBus adapter at 0x4c40
[   46.126234] input: PC Speaker as /class/input/input3
[   46.254309] parport: PnPBIOS parport detected.
[   46.254356] parport0: PC-style at 0x378 (0x778), irq 7, dma 3
[PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   46.444286] ACPI: PCI Interrupt Link [APCJ] enabled at IRQ 22
[   46.444292] ACPI: PCI Interrupt 0000:00:04.0[A] -> Link [APCJ] ->
GSI 22 (level, low) -> IRQ 17
[   46.444314] PCI: Setting latency timer of device 0000:00:04.0 to 64
[   46.762539] intel8x0_measure_ac97_clock: measured 54727 usecs
[   46.762542] intel8x0: clocking to 46909
[   46.881319] fuse init (API version 7.8)
[   46.918808] lp0: using parport0 (interrupt-driven).
[   47.238046] it87: Found IT8712F chip at 0x290, revision 7
[   47.238055] it87: in3 is VCC (+5V)
[   47.238057] it87: in7 is VCCH (+5V Stand-By)
[   47.240520] it87-isa 9191-0290: Detected broken BIOS defaults,
disabling PWM interface
[   47.266595] Adding 1108444k swap on /dev/disk/by-uuid/
81c5a81c-84dc-4c51-9eb5-cfdd71069e8f.  Priority:-1 extents:1 across:
1108444k
[   47.371788] EXT3 FS on hdb2, internal journal
[   47.456325] md: md0 stopped.
[   47.456335] md: unbind<sdc1>
[   47.456344] md: export_rdev(sdc1)
[   47.460650] md: bind<sdc1>
[   47.552922] EXT3-fs: unable to read superblock
[   52.923856] ibm_acpi: ec object not found
[   52.948610] No dock devices found.
[   53.002249] Using specific hotkey driver
[   53.106357] input: Power Button (FF) as /class/input/input4
[   53.110096] ACPI: Power Button (FF) [PWRF]
[   53.144270] input: Power Button (CM) as /class/input/input5
[   53.148002] ACPI: Power Button (CM) [PWRB]
[   53.243850] pcc_acpi: loading...
[   53.472036] powernow-k8: Found 1 AMD Athlon(tm) 64 Processor 3000+
processors (version 2.00.00)
[   53.472070] powernow-k8:    0 : fid 0xa (1800 MHz), vid 0x6
[   53.472073] powernow-k8:    1 : fid 0x2 (1000 MHz), vid 0x12
[   57.872360] Linux agpgart interface v0.102 (c) Dave Jones
[   57.895000] [drm] Initialized drm 1.1.0 20060810
[   57.908468] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
[   57.908480] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [APC3] ->
GSI 18 (level, low) -> IRQ 20
[   57.909339] [drm] Initialized radeon 1.25.0 20060524 on minor 0
[   58.455480] ppdev: user-space parallel port driver
[   59.604737] apm: BIOS version 1.2 Flags 0x07 (Driver version
1.16ac)
[   59.604742] apm: overridden by ACPI.
[   36.864000] Time: acpi_pm clocksource has been installed.
[   37.752000] NET: Registered protocol family 10
[   37.752000] lo: Disabled Privacy Extensions
[   37.752000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   50.700000] [drm] Setting GART location based on new memory map
[   50.700000] [drm] Loading R300 Microcode
[   50.700000] [drm] writeback test succeeded in 1 usecs

```---------------------------------------------------------------------------------------

sda (the new drive that became a Spare when I added it)
-----------------------------------------------------------
bo@QB3:~$ sudo mdadm --examine /dev/sda1
/dev/sda1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 7d54a5d5:a6731a04:235d0391:92d83ba4
  Creation Time : Sat Aug 18 17:14:42 2007
     Raid Level : raid5
    Device Size : 488383936 (465.76 GiB 500.11 GB)
     Array Size : 1465151808 (1397.28 GiB 1500.32 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0

    Update Time : Thu Jan  1 17:35:33 2009
          State : active
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 306982ac - correct
         Events : 0.4085

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     4       8        1       -1      spare   /dev/sda1

   0     0       8        1        0      active sync   /dev/sda1
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       8       33        2      active sync   /dev/sdc1
   3     3       8       49        3      active sync   /dev/sdd1
--------------------------------------------------------------------

sdb (one of the original drives)
------------------------------------------------------------------
bo@QB3:~$ sudo mdadm --examine /dev/sdb1
/dev/sdb1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 7d54a5d5:a6731a04:235d0391:92d83ba4
  Creation Time : Sat Aug 18 17:14:42 2007
     Raid Level : raid5
    Device Size : 488383936 (465.76 GiB 500.11 GB)
     Array Size : 1465151808 (1397.28 GiB 1500.32 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0

    Update Time : Thu Jan  1 17:35:33 2009
          State : active
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 306982b3 - correct
         Events : 0.4085

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     1       8       17        1      active sync   /dev/sdb1

   0     0       8        1        0      active sync   /dev/sda1
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       8       33        2      active sync   /dev/sdc1
   3     3       8       49        3      active sync   /dev/sdd1
--------------------------------------------------------------------------

sdc (one of the original drives)
---------------------------------------------------------------------------
bo@QB3:~$ sudo mdadm --examine /dev/sdc1
/dev/sdc1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 7d54a5d5:a6731a04:7541ee53:adfe8685 (local to host
QB3)
  Creation Time : Sat Aug 18 17:14:42 2007
     Raid Level : raid5
    Device Size : 488383936 (465.76 GiB 500.11 GB)
     Array Size : 1465151808 (1397.28 GiB 1500.32 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0

    Update Time : Thu Jan  1 17:35:33 2009
          State : active
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 9d74b868 - correct
         Events : 0.4085

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     2       8       33        2      active sync   /dev/sdc1

   0     0       8        1        0      active sync   /dev/sda1
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       8       33        2      active sync   /dev/sdc1
   3     3       8       49        3      active sync   /dev/sdd1
--------------------------------------------------------------------

sdd (one of the original drives)
---------------------------------------------------------
bo@QB3:~$ sudo mdadm --examine /dev/sdd1
/dev/sdd1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 7d54a5d5:a6731a04:235d0391:92d83ba4
  Creation Time : Sat Aug 18 17:14:42 2007
     Raid Level : raid5
    Device Size : 488383936 (465.76 GiB 500.11 GB)
     Array Size : 1465151808 (1397.28 GiB 1500.32 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0

    Update Time : Thu Jan  1 17:35:33 2009
          State : active
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 306982d7 - correct
         Events : 0.4085

         Layout : left-symmetric
     Chunk Size : 64K

      Number   Major   Minor   RaidDevice State
this     3       8       49        3      active sync   /dev/sdd1

   0     0       8        1        0      active sync   /dev/sda1
   1     1       8       17        1      active sync   /dev/sdb1
   2     2       8       33        2      active sync   /dev/sdc1
   3     3       8       49        3      active sync   /dev/sdd1
-------------------------------------------------------------------

bo@QB3:~$ sudo mdadm --misc --detail /dev/md0
mdadm: md device /dev/md0 does not appear to be active.

-------------------------------------------------------------------

bo@QB3:~$ sudo mdadm --examine --brief --scan --config=partitions
ARRAY /dev/md0 level=raid5 num-devices=4
UUID=7d54a5d5:a6731a04:7541ee53:adfe8685
ARRAY /dev/md0 level=raid5 num-devices=4
UUID=7d54a5d5:a6731a04:235d0391:92d83ba4
   spares=1

(*this seems a bit weird to me, why would there be two /dev/md0?)
-------------------------------------------------------------------

bo@QB3:~$ sudo mdadm --assemble /dev/md0 /dev/sdb /dev/sdc /dev/sdd
mdadm: no recogniseable superblock on /dev/sdb
mdadm: /dev/sdb has no superblock - assembly aborted

-------------------------------------------------------------------

bo@QB3:~$ sudo mdadm --query /dev/md0
/dev/md0: is an md device which is not active

-------------------------------------------------------------------

---

### Post by handy on 2009-02-18
I have asked the mod's to move this thread to the Server Platforms sub-forum, where you really should have a better chance of attracting help.

---

### Post by bapoumba on 2009-02-18
So moved :)

---

### Post by fjgaude on 2009-02-18
Well, it takes years to gather all the info on how to handle **mdadm** arrays under all conditions. The thing that starts the problems is doing things without realizing the issues.

You removed a drive without first faulting it and then removing it with the mdadm -f and -r commands. That leaves the UUID superblock thinking you still have the drive there, even though you physically removed it.

My only suggestion at this point would be this. Rename or delete the **/etc/mdadm/mdadm.conf** file, purge mdadm using **apt-get**, reboot. Then re-install mdadm and run this:

```
sudo mdadm --assemble --scan
```

A new mdadm.conf file will be recreated. See what it shows regarding UUID, show it to us.

We will take it from there.

---

### Post by arj03 on 2009-02-23
Thank you for your reply. Sadly several things included 7.04 being removed from the mirrors has kept me from testing the things you mentioned. I'll reply when I get the machine working again.

---

### Post by bapoumba on 2009-02-23
> **arj03 said:**
> Thank you for your reply. Sadly several things included 7.04 being removed from the mirrors has kept me from testing the things you mentioned. I'll reply when I get the machine working again.
Feisty is here: [http://old-releases.ubuntu.com/releases/](http://old-releases.ubuntu.com/releases/)

---

### Post by arj03 on 2009-03-01
> **fjgaude said:**
> Well, it takes years to gather all the info on how to handle **mdadm** arrays under all conditions. The thing that starts the problems is doing things without realizing the issues.

You removed a drive without first faulting it and then removing it with the mdadm -f and -r commands. That leaves the UUID superblock thinking you still have the drive there, even though you physically removed it.

My only suggestion at this point would be this. Rename or delete the **/etc/mdadm/mdadm.conf** file, purge mdadm using **apt-get**, reboot. Then re-install mdadm and run this:

```
sudo mdadm --assemble --scan
```

A new mdadm.conf file will be recreated. See what it shows regarding UUID, show it to us.

We will take it from there.

The raid array is now alive again. I installed latest ubuntu, installed mdadm. Then followed this thread ([http://ubuntuforums.org/archive/index.php/t-410136.html](http://ubuntuforums.org/archive/index.php/t-410136.html)) to get the array up and running again even though the UUID's was a wrong on one of the drives. I used the create command with missing on the drive that is now dead.

So the problem right now is that the array is running with only 3 drives. I have an extra drive, but the problem seems to be that the old one which died is not marked as faulty. 

So how do I mark a disc as faulty if it has died? And how do I add the new one into the array so that it will rebuild itself?

Thanks!

---

### Post by fjgaude on 2009-03-01
What does running this show:

```
sudo mdadm -D /dev/md0
```

Try reading this link and you may get ideas. If not come back and we'll see what it takes to do what you wish:

[http://www.hscripts.com/tutorials/linux-services/mdadm.html](http://www.hscripts.com/tutorials/linux-services/mdadm.html)
[http://linux-raid.osdl.org/index.php/Growing](http://linux-raid.osdl.org/index.php/Growing)

Happy reading...

---

### Post by arj03 on 2009-03-01
> **fjgaude said:**
> What does running this show:

```
sudo mdadm -D /dev/md0
```

Try reading this link and you may get ideas. If not come back and we'll see what it takes to do what you wish:

[http://www.hscripts.com/tutorials/linux-services/mdadm.html](http://www.hscripts.com/tutorials/linux-services/mdadm.html)
[http://linux-raid.osdl.org/index.php/Growing](http://linux-raid.osdl.org/index.php/Growing)

Happy reading...

Thanks, but I don't want to grow the array. I just want to add a disc so that the array won't stop working if a disc dies again.

---

### Post by fjgaude on 2009-03-01
Okay, I'll try to help but first:

```
sudo mdadm -D /dev/md0
```

Please.

Added:

[http://blog.tcg.com/tcg/2006/04/recovering_raid.html](http://blog.tcg.com/tcg/2006/04/recovering_raid.html)

This might be useful.

---

### Post by arj03 on 2009-03-02
> **fjgaude said:**
> Okay, I'll try to help but first:

```
sudo mdadm -D /dev/md0
```

Please.

Added:

[http://blog.tcg.com/tcg/2006/04/recovering_raid.html](http://blog.tcg.com/tcg/2006/04/recovering_raid.html)

This might be useful.

Here you are:

```

bo@qb3:~$ sudo mdadm -D /dev/md0
/dev/md0:
        Version : 00.90
  Creation Time : Sun Mar  1 15:35:35 2009
     Raid Level : raid5
     Array Size : 1465151808 (1397.28 GiB 1500.32 GB)
  Used Dev Size : 488383936 (465.76 GiB 500.11 GB)
   Raid Devices : 4
  Total Devices : 3
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Mon Mar  2 18:18:01 2009
          State : clean, degraded
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : 84238fe7:61401e30:1af8e058:68926172 (local to host qb3)
         Events : 0.16

    Number   Major   Minor   RaidDevice State
       0       0        0        0      removed
       1       8       33        1      active sync   /dev/sdc1
       2       8       49        2      active sync   /dev/sdd1
       3       8       65        3      active sync   /dev/sde1
```

I was wondering if now that the device is gone because the drive is faulty, that maybe one could do a touch /dev/sda1 and then do a mdadm --fail /dev/hda1 --remove /dev/hda1, or won't that work?

Thanks

---

### Post by fjgaude on 2009-03-02
Try what you suggested... if you get a "drive busy" type error message. Then zero the drive's superblock:

```
sudo mdadm zero-superblock /dev/sdb1
```

or whatever the drive is you have faulted and removed.

Then after that add the drive back into the array with the -a command.

Use this to watch it resync:

```
sudo watch cat /proc/mdstat
```

That should do it... if you have anyway to back up what's on the three-drive degraded array I would do it before doing any of the above, if you get my drift.

---

