---
title: "Server Shutting Down Every Night"
date: 2010-12-14
forum: Server Platforms
---

### Post by brwarner on 2010-12-14
I have Ubuntu Server 10 installed on my Desktop and it seems to shut down every night, requiring me to turn it on each morning. Is there any log/place I can check to figure out what's causing the shutdown?

---

### Post by Gareth_2007 on 2010-12-14
have you checked your system is not over heating and its the bios shutting the system down?

---

### Post by brwarner on 2010-12-14
I considered that, but how can I check? Do the BIOS generally have logs of shutdowns?

---

### Post by Gareth_2007 on 2010-12-15
no, unfortunately there are no logs! if you go into you bios look for a menu called "PC Health" or something along those lines and in there it will show your your cpu and system temperature. you can a maximum temperature limit so when it is reached the system will start bleeping

---

### Post by cbarron on 2010-12-15
does it beep at you when you turn it back on? most mobo manufacturers has put this function in to warn of problems.....Intel has been real good about this.  But I agree it sounds like a heat problem

---

### Post by redmk2 on 2010-12-15
> **Gareth_2007 said:**
> no, unfortunately there are no logs! if you go into you bios look for a menu called "PC Health" or something along those lines and in there it will show your your cpu and system temperature. you can a maximum temperature limit so when it is reached the system will start bleeping

Have you checked the system logs?  They are located at ```
/var/log/
```

The fasted way to check is to look at the dbus log from the CLI  this way```
dmesg
```

It will look something like this```

[   17.055305] PnPBIOS: Disabled by ACPI PNP
[   17.055881] PCI: Using ACPI for IRQ routing
[   17.055889] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   17.067865] NET: Registered protocol family 8
[   17.067870] NET: Registered protocol family 20
[   17.067971] NetLabel: Initializing
[   17.067976] NetLabel:  domain hash size = 128
[   17.067979] NetLabel:  protocols = UNLABELED CIPSOv4
[   17.068012] NetLabel:  unlabeled traffic allowed by default
[   17.068098] AppArmor: AppArmor Filesystem Enabled
[   17.077657] Time: tsc clocksource has been installed.
[   17.097782] system 00:0d: iomem range 0x0-0x9ffff could not be reserved
[   17.097790] system 00:0d: iomem range 0xe0000-0xfffff could not be reserved
[   17.097797] system 00:0d: iomem range 0x100000-0x1fffffff could not be reserved
[   17.097803] system 00:0d: iomem range 0x0-0x0 could not be reserved
[   17.097809] system 00:0d: iomem range 0x0-0x0 could not be reserved
[   17.128909] PCI: Bridge: 0000:00:01.0
[   17.128918]   IO window: c000-cfff
[   17.128926]   MEM window: ff700000-ff7fffff
[   17.128932]   PREFETCH window: ee900000-f69fffff
[   17.128948] PCI: Bridge: 0000:00:1e.0
[   17.128953]   IO window: d000-dfff
[   17.128960]   MEM window: ff800000-ff9fffff
[   17.128966]   PREFETCH window: f6a00000-f6afffff
[   17.128989] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   17.129021] NET: Registered protocol family 2
[   17.227813] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   17.228343] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[   17.228658] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[   17.229037] TCP: Hash tables configured (established 16384 bind 16384)
[   17.229044] TCP reno registered
[   17.257949] checking if image is initramfs...<7>Switched to high resolution mode on CPU 0
[   17.805567]  it is
[   18.467646] Freeing initrd memory: 7187k freed
[   18.468083] Simple Boot Flag at 0x7a set to 0x1
[   18.468870] audit: initializing netlink socket (disabled)
[   18.468902] audit(1292467149.140:1): initialized
[   18.469215] Total HugeTLB memory allocated, 0
[   18.473872] VFS: Disk quotas dquot_6.5.1
[   18.474088] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   18.474571] io scheduler noop registered
[   18.474579] io scheduler anticipatory registered
[   18.474584] io scheduler deadline registered (default)
[   18.474617] io scheduler cfq registered
[   18.474673] Boot video device is 0000:01:00.0
[   18.474686] PCI: Firmware left 0000:02:08.0 e100 interrupts enabled, disabling
[   18.475311] isapnp: Scanning for PnP cards...
[   18.831606] isapnp: No Plug & Play device found
[   18.909558] Real Time Clock Driver v1.12ac
[   18.909748] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   18.909924] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   18.911337] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   18.913109] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   18.913265] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   18.913502] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[   18.916509] serio: i8042 KBD port at 0x60,0x64 irq 1
[   18.916520] serio: i8042 AUX port at 0x60,0x64 irq 12
[   18.937418] mice: PS/2 mouse device common for all mice
[   18.937675] EISA: Probing bus 0 at eisa.0
[   18.937729] EISA: Detected 0 cards.
[   18.937736] cpuidle: using governor ladder
[   18.937740] cpuidle: using governor menu
[   18.938074] NET: Registered protocol family 1
[   18.938142] Using IPI No-Shortcut mode
[   18.938205] registered taskstats version 1
[   18.938419]   Magic number: 6:580:662
[   18.938491]   hash matches device ptyed
[   18.938594] BIOS EDD facility v0.16 2004-Jun-25, 6 devices found
[   18.940080] Freeing unused kernel memory: 384k freed
[   18.940214] Write protecting the kernel read-only data: 829k
[   18.973872] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   19.342993] fuse init (API version 7.9)
[   20.374054] SCSI subsystem initialized
[   20.576697] libata version 3.00 loaded.
[   20.602382] ata_piix 0000:00:1f.1: version 2.12
[   20.602502] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   20.616746] scsi0 : ata_piix
[   20.647901] scsi1 : ata_piix
[   20.648838] ACPI Exception (exoparg2-0442): AE_AML_PACKAGE_LIMIT, Index (000000007) is beyond end of object [20070126]
[   20.648856] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.IDE0.GTM_] (Node de1d22a0), AE_AML_PACKAGE_LIMIT
[   20.648929] ACPI Error (psparse-0537): Method parse/execution failed [\_SB_.PCI0.IDE0.CHN0._GTM] (Node de1d20f0), AE_AML_PACKAGE_LIMIT
[   20.648974] ata1: ACPI get timing mode failed (AE 0x300d)
[   20.649664] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[   20.649671] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[   20.716745] e100: Intel(R) PRO/100 Network Driver, 3.5.23-k4-NAPI
[   20.716754] e100: Copyright(c) 1999-2006 Intel Corporation
[   20.827891] ata1.00: ATA-5: WDC WD1200JB-00CRA0, 16.06V16, max UDMA/100
[   20.827902] ata1.00: 234441648 sectors, multi 16: LBA
[   20.867884] ata1.00: configured for UDMA/100
[   20.910057] usbcore: registered new interface driver usbfs
[   20.910108] usbcore: registered new interface driver hub
[   20.916704] usbcore: registered new device driver usb
[   20.936666] USB Universal Host Controller Interface driver v3.0
[   21.066702] Floppy drive(s): fd0 is 1.44M
[   21.090285] FDC 0 is a post-1991 82077
[   21.206865] ata2.00: ATAPI: Hewlett-Packard CD-Writer Plus 8100, 1.0g, max MWDMA1
[   21.406726] ata2.00: configured for MWDMA1
[   21.406974] scsi 0:0:0:0: Direct-Access     ATA      WDC WD1200JB-00C 16.0 PQ: 0 ANSI: 5
[   21.412835] scsi 1:0:0:0: CD-ROM            HP       CD-Writer+ 8100  1.0g PQ: 0 ANSI: 5
[   21.416939] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 11
[   21.416948] PCI: setting IRQ 11 as level-triggered
[   21.416954] ACPI: PCI Interrupt 0000:02:08.0[A] -> Link [LNKE] -> GSI 11 (level, low) -> IRQ 11
[   21.440838] e100: eth0: e100_probe: addr 0xff9f7000, irq 11, MAC addr 00:03:47:a4:45:fa
[   21.440910] sata_sil 0000:02:0a.0: version 2.3
[   21.441266] ACPI: PCI Interrupt Link [LNKG] enabled at IRQ 9
[   21.441272] PCI: setting IRQ 9 as level-triggered
[   21.441277] ACPI: PCI Interrupt 0000:02:0a.0[A] -> Link [LNKG] -> GSI 9 (level, low) -> IRQ 9
[   21.450188] scsi2 : sata_sil
[   21.455307] scsi3 : sata_sil
[   21.455421] ata3: SATA max UDMA/100 mmio m512@0xff9ffc00 tf 0xff9ffc80 irq 9
[   21.455428] ata4: SATA max UDMA/100 mmio m512@0xff9ffc00 tf 0xff9ffcc0 irq 9
[   21.776404] ata3: SATA link down (SStatus 0 SControl 310)
[   22.106286] ata4: SATA link down (SStatus 0 SControl 310)
[   22.106963] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 11
[   22.106972] ACPI: PCI Interrupt 0000:02:0b.0[A] -> Link [LNKH] -> GSI 11 (level, low) -> IRQ 11
[   22.106991] 3c59x: Donald Becker and others.
[   22.107002] 0000:02:0b.0: 3Com PCI 3c905C Tornado at e086e800.
[   22.129747] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 3
[   22.129757] PCI: setting IRQ 3 as level-triggered
[   22.129763] ACPI: PCI Interrupt 0000:00:1f.2[D] -> Link [LNKD] -> GSI 3 (level, low) -> IRQ 3
[   22.129784] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   22.129791] uhci_hcd 0000:00:1f.2: UHCI Host Controller
[   22.130261] uhci_hcd 0000:00:1f.2: new USB bus registered, assigned bus number 1
[   22.130301] uhci_hcd 0000:00:1f.2: irq 3, io base 0x0000ef80
[   22.130586] usb usb1: configuration #1 chosen from 1 choice
[   22.130645] hub 1-0:1.0: USB hub found
[   22.130657] hub 1-0:1.0: 2 ports detected
[   22.387924] Driver 'sd' needs updating - please use bus_type methods
[   22.391400] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[   22.391434] sd 0:0:0:0: [sda] Write Protect is off
[   22.391440] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   22.391484] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   22.391594] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[   22.391619] sd 0:0:0:0: [sda] Write Protect is off
[   22.391625] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   22.391666] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   22.391674]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   22.410266]  sda1 sda2 sda3 sda4
[   22.422131] sd 0:0:0:0: [sda] Attached SCSI disk
[   22.436412] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   22.436456] sr 1:0:0:0: Attached scsi generic sg1 type 5
[   22.444887] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[   22.444899] Uniform CD-ROM driver Revision: 3.20
[   22.445006] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   26.305215] Attempting manual resume
[   26.305224] swsusp: Resume From Partition 8:2
[   26.305227] PM: Checking swsusp image.
[   26.305464] PM: Resume from disk failed.
[   26.370081] kjournald starting.  Commit interval 5 seconds
[   26.370111] EXT3-fs: mounted filesystem with ordered data mode.
[   29.344727] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   30.403963] iTCO_vendor_support: vendor-support=0
[   30.443088] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   30.443233] iTCO_wdt: failed to reset NO_REBOOT flag, reboot disabled by hardware
[   30.443294] iTCO_wdt: No card detected
[   30.523939] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   30.574004] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   30.596489] Linux agpgart interface v0.102
[   30.663882] intel_rng: Firmware space is locked read-only. If you can't or
[   30.663889] intel_rng: don't want to disable this in firmware setup, and if
[   30.663893] intel_rng: you are certain that your system has a functional
[   30.663896] intel_rng: RNG, try using the 'no_fwh_detect' option.
[   30.723950] agpgart: Detected an Intel i815 Chipset.
[   30.727869] agpgart: AGP aperture is 64M @ 0xf8000000
[   31.343815] parport_pc 00:09: reported by Plug and Play ACPI
[   31.343851] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
[   31.611553] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 10
[   31.611563] PCI: setting IRQ 10 as level-triggered
[   31.611569] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
[   31.611598] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   31.734222] input: Power Button (FF) as /devices/virtual/input/input3
[   31.763499] ACPI: Power Button (FF) [PWRF]
[   31.763673] input: Sleep Button (CM) as /devices/virtual/input/input4
[   31.803493] ACPI: Sleep Button (CM) [SBTN]
[   32.293359] intel8x0_measure_ac97_clock: measured 50935 usecs
[   32.293369] intel8x0: clocking to 48000
[   34.506034] eth1:  setting full-duplex.
[   34.609323] input: ImExPS/2 Logitech Wheel Mouse as /devices/platform/i8042/serio1/input/input5
[   34.648527] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   35.527233] NET: Registered protocol family 10
[   35.527777] lo: Disabled Privacy Extensions
[   38.705584] loop: module loaded
[   38.739640] lp0: using parport0 (interrupt-driven).
[   38.961920] Adding 979956k swap on /dev/sda2.  Priority:-1 extents:1 across:979956k
[   39.288215] EXT3 FS on sda1, internal journal
[   40.120962] kjournald starting.  Commit interval 5 seconds
[   40.121193] EXT3 FS on sda3, internal journal
[   40.121203] EXT3-fs: mounted filesystem with ordered data mode.
[   40.137106] kjournald starting.  Commit interval 5 seconds
[   40.137398] EXT3 FS on sda4, internal journal
[   40.137406] EXT3-fs: mounted filesystem with ordered data mode.
[   40.639116] ip_tables: (C) 2000-2006 Netfilter Core Team
[   43.108907] NET: Registered protocol family 17
[   46.429199] eth1: no IPv6 routers present

```

You can look at the tail end of the various logs using the command *tail*.  The default is the last 10 lines.  You can increase it like this```
tail -25 /var/log/kern.log
```

The kernel error log will look like this```

>tail -25 /var/log/kern.log

Dec 15 18:39:33 rincon kernel: [   31.611598] PCI: Setting latency timer of device 0000:00:1f.5 to 64
Dec 15 18:39:33 rincon kernel: [   31.734222] input: Power Button (FF) as /devices/virtual/input/input3
Dec 15 18:39:33 rincon kernel: [   31.763499] ACPI: Power Button (FF) [PWRF]
Dec 15 18:39:33 rincon kernel: [   31.763673] input: Sleep Button (CM) as /devices/virtual/input/input4
Dec 15 18:39:33 rincon kernel: [   31.803493] ACPI: Sleep Button (CM) [SBTN]
Dec 15 18:39:33 rincon kernel: [   32.293359] intel8x0_measure_ac97_clock: measured 50935 usecs
Dec 15 18:39:33 rincon kernel: [   32.293369] intel8x0: clocking to 48000
Dec 15 18:39:33 rincon kernel: [   34.506034] eth1:  setting full-duplex.
Dec 15 18:39:33 rincon kernel: [   34.609323] input: ImExPS/2 Logitech Wheel Mouse as /devices/platform/i8042/serio1/input/input5
Dec 15 18:39:33 rincon kernel: [   34.648527] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
Dec 15 18:39:33 rincon kernel: [   35.527233] NET: Registered protocol family 10
Dec 15 18:39:33 rincon kernel: [   35.527777] lo: Disabled Privacy Extensions
Dec 15 18:39:33 rincon kernel: [   38.705584] loop: module loaded
Dec 15 18:39:33 rincon kernel: [   38.739640] lp0: using parport0 (interrupt-driven).
Dec 15 18:39:33 rincon kernel: [   38.961920] Adding 979956k swap on /dev/sda2.  Priority:-1 extents:1 across:979956k
Dec 15 18:39:33 rincon kernel: [   39.288215] EXT3 FS on sda1, internal journal
Dec 15 18:39:33 rincon kernel: [   40.120962] kjournald starting.  Commit interval 5 seconds
Dec 15 18:39:33 rincon kernel: [   40.121193] EXT3 FS on sda3, internal journal
Dec 15 18:39:33 rincon kernel: [   40.121203] EXT3-fs: mounted filesystem with ordered data mode.
Dec 15 18:39:33 rincon kernel: [   40.137106] kjournald starting.  Commit interval 5 seconds
Dec 15 18:39:33 rincon kernel: [   40.137398] EXT3 FS on sda4, internal journal
Dec 15 18:39:33 rincon kernel: [   40.137406] EXT3-fs: mounted filesystem with ordered data mode.
Dec 15 18:39:33 rincon kernel: [   40.639116] ip_tables: (C) 2000-2006 Netfilter Core Team
Dec 15 18:39:34 rincon kernel: [   43.108907] NET: Registered protocol family 17
Dec 15 18:39:37 rincon kernel: [   46.429199] eth1: no IPv6 routers present

```

---

### Post by elico on 2010-12-16
you should look on the kernel log and also the /var/log/messages

but not just the lat 25 lines but the last lines before the server was shutdown.
let say tail it for like 200 lines and with the less or more piping.. as

>tail -200 /var/log/kern.log | less
>tail -200 /var/log/messages | less


will give you more info.
and if 200 is not enough just try some 100 more..

---

