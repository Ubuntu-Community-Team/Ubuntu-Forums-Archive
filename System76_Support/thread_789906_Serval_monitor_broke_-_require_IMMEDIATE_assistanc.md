---
title: "Serval monitor broke - require IMMEDIATE assistance"
date: 2008-05-11
forum: System76 Support
---

### Post by 982000971 on 2008-05-11
I was ripping a CD, Ubuntu froze and nothing responded. So I manually shut off my Serval Performance and then turned it back on. The monitor never came back up, just a completely blank screen. Obviously if I can't see anything I can't do anything. I plugged in a monitor using the VGA slot and magically ONE TIME it actually appeared and I saw my log in screen but there was no response from my keyboard or mouse so it was pretty useless. And I can't get the whole external monitor thing to actually work again. I figured I would try an external mouse and keyboard next time too, but I can't get the monitor thing working.

It's finals week. I dont have time for this. I need my laptop, I need the files on the HD. I'm irrational right now and don't know jack about computers or linux and need help ASAP! What are my options? Is there any way, any cable I can connect to a desktop, or anything. That will allow me to access my laptops HD?

---

### Post by DRM_free on 2008-05-11
Try hooking your laptop to the internet and SSH-ing to it from another computer. Then attach the output of the following commands to this thread:

1) dmesg
2) cat Xorg.0.log

Also, does BIOS and grub appear on the screen, and are they responsive to the keyboard?

---

### Post by 982000971 on 2008-05-11
I tried again using the external monitor this morning and it worked first try. But it never made it to the log in screen. It is stuck on the Phoenix Technologies boot screen (the first thing I would normally see when I turn it on. Usually it would flash that for a few seconds before booting). Anyway it says hit F2 for SETUP or F12 for BOOT SELECTION. The laptop keyboard is unresponsive so I can't press either. So I hooked up both an external keyboard and an external mouse and neither of those respond either (the keyboard doesn't even light up so it's obviously not even getting any power).

When you asked if BIOS or GRUB appeared on screen were you referring to my external VGA monitor or the laptop monitor itself? Because the laptop monitor is completely dead and hasn't showed a hint of power since it first stopped working. As far as the external I don't know, I've only gotten a picture twice. Once I saw the log in screen and now I see the Phoenix Technology screen.

---

### Post by brigadoon on 2008-05-11
It sounds as if your laptop CPU has died. Freezing at different steps in the boot up sequence is a good indication that this is the case. Not being able to get by the Phoenix bios screen is a very strong indication that the CPU is fried. Your best course of action is to take your hard drive out and install it into another laptop. Get the critical files you need and get through your finals.

---

### Post by 982000971 on 2008-05-11
I'm desperate and so I am more than willing to go out and buy a new laptop today. But as far as compatibility with Ubuntu how will I know what to buy?

Regardless, I'm leaving right now. Maybe I'll just buy several laptops...

---

### Post by 982000971 on 2008-05-11
I swear a miracle just occurred. I kid you not I punched my laptop out of anger and the next time I tried to turn it on the monitor worked. Loaded up, logged in, uploaded my Finals to Google Docs then it froze. Two lights on the laptop flashed green. One was a lock with an "A" in the middle, the other a lock with an arrow pointing down. I turned it off then back on and it came up again. I logged in, checked my email, then it just rebooted without warning.

I ran dmesg and will attach it to this thread when I get the chance (the cat Xorg thing was an unrecognized command). For now it seems crisis averted, but obviously I have some laptop issues here that I will need some help with. Doing the rest of my finals without my laptop isn't preferred but it is possible, so I should be happy for now...

---

### Post by 982000971 on 2008-05-11
Here is what I received from dmesg

> [   16.435670] ACPI: BIOS _OSI(Linux) query ignored via DMI
[   16.435672] ACPI: If "acpi_osi=Linux" works better, please notify [email]linux-acpi@vger.kernel.org[/email]
[   16.435863] ACPI: Interpreter enabled
[   16.435865] ACPI: (supports S0 S3 S4 S5)
[   16.435877] ACPI: Using IOAPIC for interrupt routing
[   16.439473] ACPI: EC: GPE = 0x19, I/O: command/status = 0x66, data = 0x62
[   16.439476] ACPI: EC: driver started in poll mode
[   16.439515] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   16.440269] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[   16.440273] PCI quirk: region 1180-11bf claimed by ICH6 GPIO
[   16.441771] PCI: Transparent bridge - 0000:00:1e.0
[   16.441861] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   16.442099] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PEGP._PRT]
[   16.442205] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[   16.442308] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[   16.442409] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[   16.442519] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[   16.448410] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 *7 10 12 14 15)
[   16.448491] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[   16.448569] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[   16.448647] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[   16.448725] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[   16.448802] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
[   16.448880] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[   16.448958] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 *5 6 7 11 12 14 15)
[   16.449086] Linux Plug and Play Support v0.97 (c) Adam Belay
[   16.449116] pnp: PnP ACPI init
[   16.449122] ACPI: bus type pnp registered
[   16.450492] pnp: PnP ACPI: found 11 devices
[   16.450494] ACPI: ACPI bus type pnp unregistered
[   16.450497] PnPBIOS: Disabled by ACPI PNP
[   16.450719] PCI: Using ACPI for IRQ routing
[   16.450721] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   16.450726] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.3
[   16.450728] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.3
[   16.459871] NET: Registered protocol family 8
[   16.459872] NET: Registered protocol family 20
[   16.459909] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   16.459912] hpet0: 3 64-bit timers, 14318180 Hz
[   16.460943] AppArmor: AppArmor Filesystem Enabled
[   16.463773] Time: tsc clocksource has been installed.
[   16.463785] Switched to high resolution mode on CPU 0
[   16.463877] Switched to high resolution mode on CPU 1
[   16.480763] system 00:01: ioport range 0xfe00-0xfe7f has been reserved
[   16.480766] system 00:01: ioport range 0xfe80-0xfeff has been reserved
[   16.480768] system 00:01: ioport range 0xff00-0xff7f has been reserved
[   16.480771] system 00:01: iomem range 0xe0000000-0xefffffff could not be reserved
[   16.480773] system 00:01: iomem range 0xfed14000-0xfed17fff could not be reserved
[   16.480776] system 00:01: iomem range 0xfed18000-0xfed18fff could not be reserved
[   16.480778] system 00:01: iomem range 0xfed19000-0xfed19fff could not be reserved
[   16.480780] system 00:01: iomem range 0xfed1c000-0xfed1ffff could not be reserved
[   16.480783] system 00:01: iomem range 0xfed20000-0xfed3ffff could not be reserved
[   16.480785] system 00:01: iomem range 0xfed45000-0xfed8ffff could not be reserved
[   16.480792] system 00:05: iomem range 0xfed00000-0xfed003ff could not be reserved
[   16.480797] system 00:07: ioport range 0x800-0x80f has been reserved
[   16.480800] system 00:07: ioport range 0x1000-0x107f has been reserved
[   16.480802] system 00:07: ioport range 0x1180-0x11bf has been reserved
[   16.511208] PCI: Failed to allocate mem resource #6:20000@d0000000 for 0000:01:00.0
[   16.511210] PCI: Bridge: 0000:00:01.0
[   16.511212]   IO window: 2000-2fff
[   16.511216]   MEM window: d0000000-d1ffffff
[   16.511218]   PREFETCH window: c0000000-cfffffff
[   16.511222] PCI: Bridge: 0000:00:1c.0
[   16.511223]   IO window: disabled.
[   16.511228]   MEM window: d2100000-d21fffff
[   16.511232]   PREFETCH window: disabled.
[   16.511238] PCI: Bridge: 0000:00:1c.2
[   16.511240]   IO window: 3000-3fff
[   16.511246]   MEM window: d2200000-d22fffff
[   16.511250]   PREFETCH window: 88000000-880fffff
[   16.511255] PCI: Bridge: 0000:00:1c.3
[   16.511257]   IO window: disabled.
[   16.511262]   MEM window: disabled.
[   16.511266]   PREFETCH window: disabled.
[   16.511278] PCI: Bus 7, cardbus bridge: 0000:06:04.0
[   16.511279]   IO window: 00004000-000040ff
[   16.511284]   IO window: 00004400-000044ff
[   16.511289]   PREFETCH window: 8c000000-8fffffff
[   16.511294]   MEM window: 90000000-93ffffff
[   16.511299] PCI: Bridge: 0000:00:1e.0
[   16.511301]   IO window: 4000-4fff
[   16.511307]   MEM window: d2000000-d20fffff
[   16.511311]   PREFETCH window: disabled.
[   16.511326] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
[   16.511331] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   16.511353] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 17
[   16.511358] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   16.511381] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 18
[   16.511386] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   16.511409] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 19
[   16.511416] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[   16.511426] PCI: Enabling device 0000:00:1e.0 (0004 -> 0007)
[   16.511432] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   16.511448] ACPI: PCI Interrupt 0000:06:04.0[A] -> GSI 16 (level, low) -> IRQ 16
[   16.511460] NET: Registered protocol family 2
[   16.555740] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   16.555924] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   16.556295] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   16.556478] TCP: Hash tables configured (established 131072 bind 65536)
[   16.556480] TCP reno registered
[   16.567786] checking if image is initramfs...<6>ACPI: EC: non-query interrupt received, switching to interrupt mode
[   16.843760]  it is
[   17.140802] Freeing initrd memory: 7389k freed
[   17.140963] Simple Boot Flag at 0x36 set to 0x1
[   17.141567] audit: initializing netlink socket (disabled)
[   17.141582] audit(1210522393.240:1): initialized
[   17.141795] highmem bounce pool size: 64 pages
[   17.143639] VFS: Disk quotas dquot_6.5.1
[   17.143712] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   17.143831] io scheduler noop registered
[   17.143833] io scheduler anticipatory registered
[   17.143834] io scheduler deadline registered
[   17.143843] io scheduler cfq registered (default)
[   17.143944] Boot video device is 0000:01:00.0
[   17.144050] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   17.144085] assign_interrupt_mode Found MSI capability
[   17.144115] Allocate Port Service[0000:00:01.0:pcie00]
[   17.144192] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   17.144248] assign_interrupt_mode Found MSI capability
[   17.144292] Allocate Port Service[0000:00:1c.0:pcie00]
[   17.144323] Allocate Port Service[0000:00:1c.0:pcie02]
[   17.144420] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   17.144476] assign_interrupt_mode Found MSI capability
[   17.144520] Allocate Port Service[0000:00:1c.2:pcie00]
[   17.144552] Allocate Port Service[0000:00:1c.2:pcie02]
[   17.144651] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[   17.144707] assign_interrupt_mode Found MSI capability
[   17.144751] Allocate Port Service[0000:00:1c.3:pcie00]
[   17.144783] Allocate Port Service[0000:00:1c.3:pcie02]
[   17.145029] isapnp: Scanning for PnP cards...
[   17.499737] isapnp: No Plug & Play device found
[   17.522775] Real Time Clock Driver v1.12ac
[   17.522976] hpet_resources: 0xfed00000 is busy
[   17.523004] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   17.524103] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   17.524165] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   17.524255] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   17.544226] i8042.c: Detected active multiplexing controller, rev 1.1.
[   17.561028] serio: i8042 KBD port at 0x60,0x64 irq 1
[   17.561032] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[   17.561034] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[   17.561037] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[   17.561038] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[   17.579186] mice: PS/2 mouse device common for all mice
[   17.579287] EISA: Probing bus 0 at eisa.0
[   17.579293] Cannot allocate resource for EISA slot 1
[   17.579295] Cannot allocate resource for EISA slot 2
[   17.579296] Cannot allocate resource for EISA slot 3
[   17.579298] Cannot allocate resource for EISA slot 4
[   17.579315] EISA: Detected 0 cards.
[   17.579318] cpuidle: using governor ladder
[   17.579319] cpuidle: using governor menu
[   17.579386] NET: Registered protocol family 1
[   17.579411] Using IPI No-Shortcut mode
[   17.579436] registered taskstats version 1
[   17.579529]   Magic number: 8:683:236
[   17.579539]   hash matches device ttyv6
[   17.579581] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   17.579582] EDD information not available.
[   17.579762] Freeing unused kernel memory: 364k freed
[   17.594520] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   18.760728] fuse init (API version 7.9)
[   18.781389] ACPI: SSDT 7FE6D0CB, 0231 (r1  PmRef  Cpu0Ist     3000 INTL 20050624)
[   18.781564] ACPI: SSDT 7FE6CB90, 04B6 (r1  PmRef  Cpu0Cst     3001 INTL 20050624)
[   18.782947] Monitor-Mwait will be used to enter C-1 state
[   18.782950] Monitor-Mwait will be used to enter C-2 state
[   18.782952] Monitor-Mwait will be used to enter C-3 state
[   18.783070] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   18.783074] ACPI: Processor [CPU0] (supports 8 throttling states)
[   18.783259] ACPI: SSDT 7FE6D2FC, 00B1 (r1  PmRef  Cpu1Ist     3000 INTL 20050624)
[   18.783419] ACPI: SSDT 7FE6D046, 0085 (r1  PmRef  Cpu1Cst     3000 INTL 20050624)
[   18.784009] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[   18.784014] ACPI: Processor [CPU1] (supports 8 throttling states)
[   18.962832] usbcore: registered new interface driver usbfs
[   18.962852] usbcore: registered new interface driver hub
[   18.963922] usbcore: registered new device driver usb
[   18.969632] r8169 Gigabit Ethernet driver 2.2LK loaded
[   18.969666] ACPI: PCI Interrupt 0000:04:00.0[A] -> GSI 18 (level, low) -> IRQ 18
[   18.969687] PCI: Setting latency timer of device 0000:04:00.0 to 64
[   18.969997] eth0: RTL8168b/8111b at 0xf8872000, 00:16:d4:11:e9:78, XID 38000000 IRQ 219
[   18.976357] USB Universal Host Controller Interface driver v3.0
[   18.976400] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 20
[   18.976407] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   18.976411] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   18.976612] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   18.976645] uhci_hcd 0000:00:1d.0: irq 20, io base 0x00001800
[   18.976763] usb usb1: configuration #1 chosen from 1 choice
[   18.976784] hub 1-0:1.0: USB hub found
[   18.976788] hub 1-0:1.0: 2 ports detected
[   19.078330] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 19
[   19.078339] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   19.078343] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   19.078362] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   19.078392] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001820
[   19.078490] usb usb2: configuration #1 chosen from 1 choice
[   19.078509] hub 2-0:1.0: USB hub found
[   19.078514] hub 2-0:1.0: 2 ports detected
[   19.187404] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[   19.187414] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   19.187418] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   19.187437] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   19.187469] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001840
[   19.187568] usb usb3: configuration #1 chosen from 1 choice
[   19.187588] hub 3-0:1.0: USB hub found
[   19.187592] hub 3-0:1.0: 2 ports detected
[   19.290924] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 16
[   19.290933] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[   19.290936] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   19.290955] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[   19.290987] uhci_hcd 0000:00:1d.3: irq 16, io base 0x00001860
[   19.291085] usb usb4: configuration #1 chosen from 1 choice
[   19.291105] hub 4-0:1.0: USB hub found
[   19.291109] hub 4-0:1.0: 2 ports detected
[   19.322853] usb 1-2: new full speed USB device using uhci_hcd and address 2
[   19.396327] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 20
[   19.396340] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   19.396343] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   19.396365] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[   19.400283] ehci_hcd 0000:00:1d.7: debug port 1
[   19.400289] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   19.400295] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xd2504000
[   19.458527] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   19.458810] usb usb5: configuration #1 chosen from 1 choice
[   19.458835] hub 5-0:1.0: USB hub found
[   19.458840] hub 5-0:1.0: 8 ports detected
[   19.568203] ACPI: PCI Interrupt 0000:06:00.0[A] -> GSI 20 (level, low) -> IRQ 21
[   19.568212] PCI: Setting latency timer of device 0000:06:00.0 to 64
[   19.621029] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[21]  MMIO=[fabff800-fabfffff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   19.631736] SCSI subsystem initialized
[   19.647183] libata version 3.00 loaded.
[   19.651045] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 19
[   19.651077] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   19.651089] ACPI: PCI interrupt for device 0000:00:1f.2 disabled
[   19.653783] ata_piix 0000:00:1f.2: version 2.12
[   19.653789] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[   19.805868] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 19
[   19.805901] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   19.806715] scsi0 : ata_piix
[   19.807233] scsi1 : ata_piix
[   19.807936] ata1: SATA max UDMA/133 cmd 0x1f0 ctl 0x3f6 bmdma 0x18b0 irq 14
[   19.807938] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x18b8 irq 15
[   19.858816] usb 1-2: device not accepting address 2, error -71
[   19.970219] ata1.00: ATA-7: ST980825AS, 3.04, max UDMA/133
[   19.970223] ata1.00: 156301488 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   19.986215] ata1.00: configured for UDMA/133
[   20.336560] ata2.00: ATAPI: Slimtype DVDRW SSM-8515S, GSL1, max UDMA/33
[   20.505916] ata2.00: configured for UDMA/33
[   20.506094] scsi 0:0:0:0: Direct-Access     ATA      ST980825AS       3.04 PQ: 0 ANSI: 5
[   20.507752] scsi 1:0:0:0: CD-ROM            Slimtype DVDRW SSM-8515S  GSL1 PQ: 0 ANSI: 5
[   20.512995] Driver 'sd' needs updating - please use bus_type methods
[   20.513048] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   20.513058] sd 0:0:0:0: [sda] Write Protect is off
[   20.513060] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   20.513074] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   20.513121] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   20.513130] sd 0:0:0:0: [sda] Write Protect is off
[   20.513132] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   20.513145] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   20.513148]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   20.521595]  sda1 sda2 < sda5 >
[   20.549072] sd 0:0:0:0: [sda] Attached SCSI disk
[   20.552928] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   20.552944] sr 1:0:0:0: Attached scsi generic sg1 type 5
[   20.563445] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[   20.563448] Uniform CD-ROM driver Revision: 3.20
[   20.563486] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   20.657377] usb 5-4: new high speed USB device using ehci_hcd and address 3
[   20.796092] usb 5-4: configuration #1 chosen from 1 choice
[   20.897222] Clocksource tsc unstable (delta = -924373236 ns)
[   20.903929] Time: hpet clocksource has been installed.
[   20.905604] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00023f65934002bc]
[   21.179218] Attempting manual resume
[   21.179221] swsusp: Resume From Partition 8:5
[   21.179222] PM: Checking swsusp image.
[   21.179431] PM: Resume from disk failed.
[   21.220599] EXT3-fs: INFO: recovery required on readonly filesystem.
[   21.220605] EXT3-fs: write access will be enabled during recovery.
[   21.272418] usb 1-2: new full speed USB device using uhci_hcd and address 4
[   21.419241] usb 1-2: configuration #1 chosen from 1 choice
[   21.472125] usb 3-2: new full speed USB device using uhci_hcd and address 2
[   21.483075] kjournald starting.  Commit interval 5 seconds
[   21.483108] EXT3-fs: sda1: orphan cleanup on readonly fs
[   21.483118] ext3_orphan_cleanup: deleting unreferenced inode 4720957
[   21.483166] ext3_orphan_cleanup: deleting unreferenced inode 5505127
[   21.483180] EXT3-fs: sda1: 2 orphan inodes deleted
[   21.483183] EXT3-fs: recovery complete.
[   21.486830] EXT3-fs: mounted filesystem with ordered data mode.
[   21.542087] usb 3-2: configuration #1 chosen from 1 choice
[   33.101077] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   33.134720] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   33.186847] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   33.222809] iTCO_vendor_support: vendor-support=0
[   33.237519] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   33.295177] Linux agpgart interface v0.102
[   33.436937] tpm_inf_pnp 00:02: Found TPM with ID IFX0102
[   33.436992] tpm_inf_pnp 00:02: TPM found: config base 0x4e, data base 0x1670, chip version 0x000b, vendor id 0x15d1 (Infineon), product id 0x000b (SLB 9635 TT 1.2)
[   33.506678] input: Power Button (FF) as /devices/virtual/input/input3
[   33.549555] ACPI: Power Button (FF) [PWRF]
[   33.549609] input: Lid Switch as /devices/virtual/input/input4
[   33.581598] ACPI: Lid Switch [LID0]
[   33.581646] input: Power Button (CM) as /devices/virtual/input/input5
[   33.645504] ACPI: Power Button (CM) [PWRB]
[   33.654409] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:01/LNXVIDEO:00/input/input6
[   33.709470] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   33.709631] ACPI: AC Adapter [ACAD] (off-line)
[   33.718442] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:01/input/input7
[   33.774438] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   33.818991] ACPI: Battery Slot [BAT1] (battery present)
[   33.917937] input: ImPS/2 Logitech Wheel Mouse as /devices/platform/i8042/serio4/input/input8
[   33.979009] iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0x1060)
[   33.979047] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   33.997027] nvidia: module license 'NVIDIA' taints kernel.
[   34.357110] Yenta: CardBus bridge found at 0000:06:04.0 [14c0:0020]
[   34.357135] Yenta: Using CSCINT to route CSC interrupts to PCI
[   34.357137] Yenta: Routing CardBus interrupts to PCI
[   34.357142] Yenta TI: socket 0000:06:04.0, mfunc 0x88501212, devctl 0x44
[   34.474005] intel_rng: FWH not detected
[   34.589763] Yenta: ISA IRQ mask 0x0cf8, PCI irq 16
[   34.589767] Socket status: 30000006
[   34.589770] Yenta: Raising subordinate bus# of parent bus (#06) from #07 to #0a
[   34.589774] pcmcia: parent PCI bridge I/O window: 0x4000 - 0x4fff
[   34.589777] cs: IO port probe 0x4000-0x4fff: clean.
[   34.589995] pcmcia: parent PCI bridge Memory window: 0xd2000000 - 0xd20fffff
[   34.641125] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   34.641137] PCI: Setting latency timer of device 0000:01:00.0 to 64
[   34.641251] NVRM: loading NVIDIA Linux x86 Kernel Module  96.43.05  Tue Jan 22 19:36:58 PST 2008
[   34.715549] sdhci: Secure Digital Host Controller Interface driver
[   34.715552] sdhci: Copyright(c) Pierre Ossman
[   34.715595] sdhci: SDHCI controller found at 0000:06:04.2 [1524:0550] (rev 1)
[   34.715616] PCI: Enabling device 0000:06:04.2 (0000 -> 0002)
[   34.715622] ACPI: PCI Interrupt 0000:06:04.2[B] -> GSI 17 (level, low) -> IRQ 17
[   34.715678] mmc0: SDHCI at 0xd2001c00 irq 17 PIO
[   34.715686] sdhci: SDHCI controller found at 0000:06:04.4 [1524:0551] (rev 1)
[   34.715703] PCI: Enabling device 0000:06:04.4 (0000 -> 0002)
[   34.715707] ACPI: PCI Interrupt 0000:06:04.4[B] -> GSI 17 (level, low) -> IRQ 17
[   34.715739] mmc1: SDHCI at 0xd2001000 irq 17 PIO
[   34.728526] Bluetooth: Core ver 2.11
[   34.732171] NET: Registered protocol family 31
[   34.732173] Bluetooth: HCI device and connection manager initialized
[   34.732176] Bluetooth: HCI socket layer initialized
[   34.736834] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.0
[   34.736837] iwl3945: Copyright(c) 2003-2007 Intel Corporation
[   34.736930] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   34.736945] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   34.736963] iwl3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[   34.803893] Bluetooth: HCI USB driver ver 2.9
[   34.805847] usbcore: registered new interface driver hci_usb
[   34.842042] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 22
[   34.842065] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   34.875601] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[   35.567941] iwl3945: Tunable channels: 11 802.11bg, 13 802.11a channels
[   35.568288] wmaster0: Selected rate control algorithm 'iwl-3945-rs'
[   35.678989] udev: renamed network interface wlan0 to eth1
[   35.706271] cs: IO port probe 0x100-0x3af: clean.
[   35.708327] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   35.709183] cs: IO port probe 0x820-0x8ff: clean.
[   35.709859] cs: IO port probe 0xc00-0xcf7: clean.
[   35.710699] cs: IO port probe 0xa00-0xaff: clean.
[   35.852274] lp: driver loaded but no devices found
[   35.912497] Adding 3907864k swap on /dev/sda5.  Priority:-1 extents:1 across:3907864k
[   35.942793] EXT3 FS on sda1, internal journal
[   36.521328] ip_tables: (C) 2000-2006 Netfilter Core Team
[   37.436455] No dock devices found.
[   41.337613] ppdev: user-space parallel port driver
[   43.179422] audit(1210522423.386:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5191 profile="/usr/sbin/cupsd" namespace="default"
[   43.471777] apm: BIOS not found.
[   43.687081] RPC: Registered udp transport module.
[   43.687084] RPC: Registered tcp transport module.
[   43.738272] Installing knfsd (copyright (C) 1996 [email]okir@monad.swb.de[/email]).
[   43.810345] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[   43.819697] NFSD: starting 90-second grace period
[   47.188586] r8169: eth0: link down
[   57.272801] NET: Registered protocol family 10
[   57.273226] lo: Disabled Privacy Extensions
[   57.275025] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   57.276465] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   71.884202] CPU0 attaching NULL sched-domain.
[   71.884211] CPU1 attaching NULL sched-domain.
[   71.897607] CPU0 attaching sched-domain:
[   71.897611]  domain 0: span 03
[   71.897614]   groups: 01 02
[   71.897617]   domain 1: span 03
[   71.897618]    groups: 03
[   71.897622] CPU1 attaching sched-domain:
[   71.897624]  domain 0: span 03
[   71.897626]   groups: 02 01
[   71.897630]   domain 1: span 03
[   71.897632]    groups: 03
[   76.870797] iwl3945: Radio Frequency Kill Switch is On:
[   76.870802] Kill switch must be turned off for wireless networking to work.
[   76.874518] atkbd.c: Unknown key pressed (translated set 2, code 0xf1 on isa0060/serio0).
[   76.874525] atkbd.c: Use 'setkeycodes e071 <keycode>' to make it known.
[   76.885621] atkbd.c: Unknown key released (translated set 2, code 0xf1 on isa0060/serio0).
[   76.885627] atkbd.c: Use 'setkeycodes e071 <keycode>' to make it known.
[   76.921090] usb 1-2: USB disconnect, address 4
[   76.937685] atkbd.c: Unknown key pressed (translated set 2, code 0xf1 on isa0060/serio0).
[   76.937694] atkbd.c: Use 'setkeycodes e071 <keycode>' to make it known.
[   77.043239] atkbd.c: Unknown key released (translated set 2, code 0xf1 on isa0060/serio0).
[   77.043247] atkbd.c: Use 'setkeycodes e071 <keycode>' to make it known.
[   77.659934] usb 1-2: new full speed USB device using uhci_hcd and address 5
[   77.832481] usb 1-2: configuration #1 chosen from 1 choice
[   89.330557] NET: Registered protocol family 17
[   89.927201] eth1: Initial auth_alg=0
[   89.927209] eth1: authenticate with AP 00:18:01:ec:56:34
[   89.928700] eth1: Initial auth_alg=0
[   89.928707] eth1: authenticate with AP 00:18:01:ec:56:34
[   89.928723] eth1: RX authentication from 00:18:01:ec:56:34 (alg=0 transaction=2 status=0)
[   89.928727] eth1: authenticated
[   89.928731] eth1: associate with AP 00:18:01:ec:56:34
[   89.930682] eth1: authentication frame received from 00:18:01:ec:56:34, but not in authenticate state - ignored
[   89.931909] eth1: RX AssocResp from 00:18:01:ec:56:34 (capab=0x421 status=0 aid=1)
[   89.931915] eth1: associated
[   89.931920] eth1: CTS protection enabled (BSSID=00:18:01:ec:56:34)
[   89.932001] eth1: WMM queue=2 aci=0 acm=0 aifs=3 cWmin=15 cWmax=1023 burst=0
[   89.932007] eth1: WMM queue=3 aci=1 acm=0 aifs=7 cWmin=15 cWmax=1023 burst=0
[   89.932012] eth1: WMM queue=1 aci=2 acm=0 aifs=2 cWmin=7 cWmax=15 burst=30
[   89.932017] eth1: WMM queue=0 aci=3 acm=0 aifs=2 cWmin=3 cWmax=7 burst=15
[   89.935584] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[   94.877579] eth1: no IPv6 routers present


---

### Post by thomasaaron on 2008-05-12
Please don't punch your laptop anymore. If you are still having difficulties with it, call me at System76, and I'll walk you through some stuff. In a nutshell, I would re-set the cmos and re-seat the memory for starters.

---

### Post by intel on 2008-05-13
All hail the "Scroll Lock" key (the light with the arrow pointed down"

People no longer remember the ancient power of the scroll lock.

Hahaha.

---

