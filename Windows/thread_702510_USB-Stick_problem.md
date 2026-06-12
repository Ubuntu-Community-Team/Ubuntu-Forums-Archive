---
title: "USB-Stick problem"
date: 2008-02-20
forum: Windows
---

### Post by Jelmoh on 2008-02-20
Well.. not really a discussion..
But my USB stick won't work.. neither windows or Ubuntu...
In windows it does mount, and appear in My Computer as G:/
But when I click on it to access it.. it says I should put a media in drive G...

Please help.. Didn't back up since ages... (my fault I know.. :P)
Thanks in advance! :)

---

### Post by anubhavrocks on 2008-02-20
On ubuntu plug in the USB drive give the following command
```
dmesg

``` 

Please provide the output of that command

---

### Post by Jelmoh on 2008-02-20
[    8.434575]   IO window: disabled. 
[    8.434580]   MEM window: disabled. 
[    8.434585]   PREFETCH window: disabled. 
[    8.434592] PCI: Bus 7, cardbus bridge: 0000:06:01.0 
[    8.434594]   IO window: 00002400-000024ff 
[    8.434600]   IO window: 00002800-000028ff 
[    8.434605]   PREFETCH window: 30000000-33ffffff 
[    8.434610]   MEM window: 38000000-3bffffff 
[    8.434615] PCI: Bridge: 0000:00:1e.0 
[    8.434618]   IO window: 2000-2fff 
[    8.434624]   MEM window: b0100000-b01fffff 
[    8.434629]   PREFETCH window: 30000000-33ffffff 
[    8.434656] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 16 
[    8.434664] PCI: Setting latency timer of device 0000:00:1c.0 to 64 
[    8.434677] PCI: Setting latency timer of device 0000:00:1e.0 to 64 
[    8.434694] ACPI: PCI Interrupt 0000:06:01.0[A] -> GSI 18 (level, low) -> IRQ 17 
[    8.434708] NET: Registered protocol family 2 
[    8.474338] IP route cache hash table entries: 4096 (order: 2, 16384 bytes) 
[    8.474370] TCP established hash table entries: 16384 (order: 5, 196608 bytes) 
[    8.474509] TCP bind hash table entries: 16384 (order: 5, 131072 bytes) 
[    8.474606] TCP: Hash tables configured (established 16384 bind 16384) 
[    8.474608] TCP reno registered 
[    8.486415] checking if image is initramfs... it is 
[    8.938290] Switched to high resolution mode on CPU 0 
[    9.140367] Freeing initrd memory: 7031k freed 
[    9.140524] Simple Boot Flag at 0x36 set to 0x1 
[    9.140770] audit: initializing netlink socket (disabled) 
[    9.140785] audit(1203538102.028:1): initialized 
[    9.142612] VFS: Disk quotas dquot_6.5.1 
[    9.142659] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes) 
[    9.142748] io scheduler noop registered 
[    9.142752] io scheduler anticipatory registered 
[    9.142754] io scheduler deadline registered 
[    9.142768] io scheduler cfq registered (default) 
[    9.142783] Boot video device is 0000:00:02.0 
[    9.142944] PCI: Setting latency timer of device 0000:00:1c.0 to 64 
[    9.142996] assign_interrupt_mode Found MSI capability 
[    9.142999] Allocate Port Service[0000:00:1c.0:pcie00] 
[    9.143029] Allocate Port Service[0000:00:1c.0:pcie02] 
[    9.143176] isapnp: Scanning for PnP cards... 
[    9.497296] isapnp: No Plug & Play device found 
[    9.520501] Real Time Clock Driver v1.12ac 
[    9.520608] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled 
[    9.521695] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize 
[    9.521892] input: Macintosh mouse button emulation as /class/input/input0 
[    9.521964] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12 
[    9.535729] serio: i8042 KBD port at 0x60,0x64 irq 1 
[    9.535736] serio: i8042 AUX port at 0x60,0x64 irq 12 
[    9.535877] mice: PS/2 mouse device common for all mice 
[    9.535968] EISA: Probing bus 0 at eisa.0 
[    9.535978] Cannot allocate resource for EISA slot 1 
[    9.535980] Cannot allocate resource for EISA slot 2 
[    9.536004] EISA: Detected 0 cards. 
[    9.536100] TCP cubic registered 
[    9.536114] NET: Registered protocol family 1 
[    9.536138] Using IPI No-Shortcut mode 
[    9.536304]   Magic number: 12:663:144 
[    9.536427]   hash matches device device:15 
[    9.536614] Freeing unused kernel memory: 364k freed 
[    9.574231] input: AT Translated Set 2 keyboard as /class/input/input1 
[   10.716905] AppArmor: AppArmor initialized<5>audit(1203538103.528:2):  type=1505 info="AppArmor initialized" pid=1195 
[   10.721857] fuse init (API version 7.8) 
[   10.725376] Failure registering capabilities with primary security module. 
[   10.746229] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3]) 
[   10.746234] ACPI: Processor [CPU0] (supports 8 throttling states) 
[   10.746245] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126] 
[   10.748963] ACPI: Thermal Zone [THRM] (26 C) 
[   11.108860] usbcore: registered new interface driver usbfs 
[   11.108883] usbcore: registered new interface driver hub 
[   11.108900] usbcore: registered new device driver usb 
[   11.109627] USB Universal Host Controller Interface driver v3.0 
[   11.109725] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 18 
[   11.109735] PCI: Setting latency timer of device 0000:00:1d.0 to 64 
[   11.109740] uhci_hcd 0000:00:1d.0: UHCI Host Controller 
[   11.109917] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1 
[   11.109948] uhci_hcd 0000:00:1d.0: irq 18, io base 0x00001820 
[   11.110059] usb usb1: configuration #1 chosen from 1 choice 
[   11.110082] hub 1-0:1.0: USB hub found 
[   11.110086] hub 1-0:1.0: 2 ports detected 
[   11.194797] SCSI subsystem initialized 
[   11.199749] libata version 2.21 loaded. 
[   11.214145] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 19 
[   11.214157] PCI: Setting latency timer of device 0000:00:1d.1 to 64 
[   11.214161] uhci_hcd 0000:00:1d.1: UHCI Host Controller 
[   11.214183] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2 
[   11.214214] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001840 
[   11.214307] usb usb2: configuration #1 chosen from 1 choice 
[   11.214330] hub 2-0:1.0: USB hub found 
[   11.214335] hub 2-0:1.0: 2 ports detected 
[   11.253285] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004) 
[   11.318154] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 17 
[   11.318167] PCI: Setting latency timer of device 0000:00:1d.2 to 64 
[   11.318172] uhci_hcd 0000:00:1d.2: UHCI Host Controller 
[   11.318194] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3 
[   11.318229] uhci_hcd 0000:00:1d.2: irq 17, io base 0x00001860 
[   11.318319] usb usb3: configuration #1 chosen from 1 choice 
[   11.318347] hub 3-0:1.0: USB hub found 
[   11.318352] hub 3-0:1.0: 2 ports detected 
[   11.422127] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 20 
[   11.422140] PCI: Setting latency timer of device 0000:00:1d.3 to 64 
[   11.422145] uhci_hcd 0000:00:1d.3: UHCI Host Controller 
[   11.422167] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4 
[   11.422199] uhci_hcd 0000:00:1d.3: irq 20, io base 0x00001880 
[   11.422294] usb usb4: configuration #1 chosen from 1 choice 
[   11.422319] hub 4-0:1.0: USB hub found 
[   11.422324] hub 4-0:1.0: 2 ports detected 
[    3.548000] Marking TSC unstable due to: possible TSC halt in C2. 
[    3.552000] Time: acpi_pm clocksource has been installed. 
[    3.556000] Clocksource tsc unstable (delta = -144509522 ns) 
[    3.648000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 18 
[    3.648000] PCI: Setting latency timer of device 0000:00:1d.7 to 64 
[    3.648000] ehci_hcd 0000:00:1d.7: EHCI Host Controller 
[    3.648000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5 
[    3.648000] ehci_hcd 0000:00:1d.7: debug port 1 
[    3.648000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7 
[    3.648000] ehci_hcd 0000:00:1d.7: irq 18, io mem 0xb0004000 
[    3.652000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004 
[    3.652000] usb usb5: configuration #1 chosen from 1 choice 
[    3.652000] hub 5-0:1.0: USB hub found 
[    3.652000] hub 5-0:1.0: 8 ports detected 
[    3.756000] ata_piix 0000:00:1f.1: version 2.11 
[    3.756000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 17 
[    3.756000] PCI: Setting latency timer of device 0000:00:1f.1 to 64 
[    3.756000] scsi0 : ata_piix 
[    3.756000] scsi1 : ata_piix 
[    3.756000] ata1: PATA max UDMA/100 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x00011810 irq 14 
[    3.756000] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x00011818 irq 15 
[    4.084000] ata1.00: ATA-6: HTS541060G9AT00, MB3OA60A, max UDMA/100 
[    4.084000] ata1.00: 117210240 sectors, multi 16: LBA48  
[    4.084000] ata1.01: ATAPI: PHILIPS DVD+/-RW SDVD8441, PX38, max UDMA/33 
[    4.084000] ata1.00: limited to UDMA/33 due to 40-wire cable 
[    4.100000] ata1.00: configured for UDMA/33 
[    4.272000] ata1.01: configured for UDMA/33 
[    4.272000] ata2: port disabled. ignoring. 
[    4.272000] scsi 0:0:0:0: Direct-Access     ATA      HTS541060G9AT00  MB3O PQ: 0 ANSI: 5 
[    4.272000] scsi 0:0:1:0: CD-ROM            PHILIPS  DVD+-RW SDVD8441 PX38 PQ: 0 ANSI: 5 
[    4.272000] ACPI: PCI Interrupt 0000:06:01.2[A] -> GSI 18 (level, low) -> IRQ 17 
[    4.324000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[17]  MMIO=[b0107000-b01077ff]  Max Packet=[2048]  IR/IT contexts=[4/8] 
[    4.324000] 8139cp 0000:06:08.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip 
[    4.324000] 8139cp 0000:06:08.0: Try the "8139too" driver instead. 
[    4.324000] 8139too Fast Ethernet driver 0.9.28 
[    4.328000] ACPI: PCI Interrupt 0000:06:08.0[A] -> GSI 16 (level, low) -> IRQ 20 
[    4.328000] eth0: RealTek RTL8139 at 0xe004c800, 00:c0:9f:d9:39:91, IRQ 20 
[    4.328000] eth0:  Identified 8139 chip type 'RTL-8100B/8139D' 
[    4.340000] sd 0:0:0:0: [sda] 117210240 512-byte hardware sectors (60012 MB) 
[    4.340000] sd 0:0:0:0: [sda] Write Protect is off 
[    4.340000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00 
[    4.340000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA 
[    4.340000] sd 0:0:0:0: [sda] 117210240 512-byte hardware sectors (60012 MB) 
[    4.340000] sd 0:0:0:0: [sda] Write Protect is off 
[    4.340000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00 
[    4.340000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA 
[    4.340000]  sda: sda1 sda2 sda3 
[    4.380000] sd 0:0:0:0: [sda] Attached SCSI disk 
[    4.384000] sd 0:0:0:0: Attached scsi generic sg0 type 0 
[    4.384000] scsi 0:0:1:0: Attached scsi generic sg1 type 5 
[    4.400000] sr0: scsi3-mmc drive: 12x/24x writer cd/rw xa/form2 cdda tray 
[    4.400000] Uniform CD-ROM driver Revision: 3.20 
[    4.400000] sr 0:0:1:0: Attached scsi CD-ROM sr0 
[    4.604000] Attempting manual resume 
[    4.604000] swsusp: Resume From Partition 8:2 
[    4.604000] PM: Checking swsusp image. 
[    4.604000] PM: Resume from disk failed. 
[    4.616000] EXT3-fs: INFO: recovery required on readonly filesystem. 
[    4.616000] EXT3-fs: write access will be enabled during recovery. 
[    5.596000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00c09f00006fa698] 
[    6.324000] kjournald starting.  Commit interval 5 seconds 
[    6.324000] EXT3-fs: recovery complete. 
[    6.324000] EXT3-fs: mounted filesystem with ordered data mode. 
[   13.260000] Linux agpgart interface v0.102 (c) Dave Jones 
[   13.296000] agpgart: Detected an Intel 915GM Chipset. 
[   13.300000] agpgart: Detected 7932K stolen memory. 
[   13.316000] agpgart: AGP aperture is 256M @ 0xc0000000 
[   13.336000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5 
[   13.408000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4 
[   13.552000] Yenta: CardBus bridge found at 0000:06:01.0 [17ff:058c] 
[   13.552000] Yenta: Enabling burst memory read transactions 
[   13.552000] Yenta: Using CSCINT to route CSC interrupts to PCI 
[   13.552000] Yenta: Routing CardBus interrupts to PCI 
[   13.552000] Yenta TI: socket 0000:06:01.0, mfunc 0x00a21b22, devctl 0x64 
[   13.784000] Yenta: ISA IRQ mask 0x0cf8, PCI irq 17 
[   13.784000] Socket status: 30000006 
[   13.784000] Yenta: Raising subordinate bus# of parent bus (#06) from #07 to #0a 
[   13.784000] pcmcia: parent PCI bridge I/O window: 0x2000 - 0x2fff 
[   13.784000] cs: IO port probe 0x2000-0x2fff: clean. 
[   13.784000] pcmcia: parent PCI bridge Memory window: 0xb0100000 - 0xb01fffff 
[   13.784000] pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x33ffffff 
[   13.824000] intel_rng: FWH not detected 
[   14.072000] ieee80211_crypt: registered algorithm 'NULL' 
[   14.088000] ieee80211: 802.11 data/management/control stack, git-1.1.13 
[   14.088000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com> 
[   14.112000] ACPI: PCI Interrupt 0000:06:01.3[A] -> GSI 18 (level, low) -> IRQ 17 
[   14.324000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.0kmprq 
[   14.324000] ipw2200: Copyright(c) 2003-2006 Intel Corporation 
[   14.324000] ACPI: PCI Interrupt 0000:06:03.0[A] -> GSI 17 (level, low) -> IRQ 16 
[   14.324000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection 
[   14.336000] iTCO_vendor_support: vendor-support=0 
[   14.528000] ipw2200: Radio Frequency Kill Switch is On: 
[   14.528000] Kill switch must be turned off for wireless networking to work. 
[   14.528000] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels) 
[   14.532000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007) 
[   14.532000] iTCO_wdt: Found a ICH6-M TCO device (Version=2, TCOBASE=0x1060) 
[   14.532000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0) 
[   14.836000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 16 (level, low) -> IRQ 20 
[   14.836000] PCI: Setting latency timer of device 0000:00:1b.0 to 64 
[   14.884000] cs: IO port probe 0x100-0x3af: clean. 
[   14.888000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7 
[   14.888000] cs: IO port probe 0x820-0x8ff: clean. 
[   14.888000] cs: IO port probe 0xc00-0xcf7: clean. 
[   14.888000] cs: IO port probe 0xa00-0xaff: clean. 
[   15.212000] Synaptics Touchpad, model: 1, fw: 5.10, id: 0x258eb1, caps: 0xa04713/0x0 
[   15.248000] input: SynPS/2 Synaptics TouchPad as /class/input/input2 
[   16.164000] lp: driver loaded but no devices found 
[   16.216000] Adding 498004k swap on /dev/sda2.  Priority:-1 extents:1 across:498004k 
[   16.656000] EXT3 FS on sda1, internal journal 
[   17.252000] kjournald starting.  Commit interval 5 seconds 
[   17.252000] EXT3 FS on sda3, internal journal 
[   17.252000] EXT3-fs: mounted filesystem with ordered data mode. 
[   17.824000] ACPI: Smart Battery System [SBS0]: AC Adapter [AC0] (on-line) 
[   18.452000] ACPI: Smart Battery System [SBS0]: Battery Slot [BAT0] (battery present) 
[   18.544000] input: Power Button (FF) as /class/input/input3 
[   18.548000] ACPI: Power Button (FF) [PWRF] 
[   18.592000] input: Lid Switch as /class/input/input4 
[   18.592000] ACPI: Lid Switch [LID] 
[   18.632000] input: Power Button (CM) as /class/input/input5 
[   18.636000] ACPI: Power Button (CM) [PWRB] 
[   18.676000] input: Sleep Button (CM) as /class/input/input6 
[   18.680000] ACPI: Sleep Button (CM) [SLPB] 
[   18.688000] ACPI: Video Device [GFX0] (multi-head: yes  rom: yes  post: no) 
[   18.704000] No dock devices found. 
[   19.864000] ppdev: user-space parallel port driver 
[   19.952000] eth0: link down 
[   20.108000] audit(1203538121.999:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4719 profile="/usr/sbin/cupsd" 
[   20.232000] apm: BIOS not found. 
[   20.520000] vboxdrv: Trying to deactivate the NMI watchdog permanently... 
[   20.520000] vboxdrv: Successfully done. 
[   20.524000] vboxdrv: Successfully loaded version 1.5.4 (interface 0x00050002). 
[   20.820000] Failure registering capabilities with primary security module. 
[   20.964000] Bluetooth: Core ver 2.11 
[   20.964000] NET: Registered protocol family 31 
[   20.964000] Bluetooth: HCI device and connection manager initialized 
[   20.964000] Bluetooth: HCI socket layer initialized 
[   20.988000] Bluetooth: L2CAP ver 2.8 
[   20.988000] Bluetooth: L2CAP socket layer initialized 
[   21.072000] Bluetooth: RFCOMM socket layer initialized 
[   21.072000] Bluetooth: RFCOMM TTY layer initialized 
[   21.072000] Bluetooth: RFCOMM ver 1.8 
[   24.080000] [drm] Initialized drm 1.1.0 20060810 
[   24.084000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 20 
[   24.088000] [drm] Initialized i915 1.6.0 20060119 on minor 0 
[   70.280000] usb 5-4: new high speed USB device using ehci_hcd and address 2 
[   70.412000] usb 5-4: configuration #1 chosen from 1 choice 
[   70.576000] usbcore: registered new interface driver libusual 
[   70.676000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2 
[   70.676000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx 
[   70.684000] Initializing USB Mass Storage driver... 
[   70.684000] scsi2 : SCSI emulation for USB Mass Storage devices 
[   70.688000] usb-storage: device found at 2 
[   70.688000] usb-storage: waiting for device to settle before scanning 
[   70.688000] usbcore: registered new interface driver usb-storage 
[   70.688000] USB Mass Storage support registered. 
[   75.688000] usb-storage: device scan complete 
[   75.688000] scsi 2:0:0:0: Direct-Access     Freecom  DataBar USB2.0   PMAP PQ: 0 ANSI: 0 CCS 
[   76.624000] sd 2:0:0:0: [sdb] 8060928 512-byte hardware sectors (4127 MB) 
[   76.624000] sd 2:0:0:0: [sdb] Write Protect is on 
[   76.624000] sd 2:0:0:0: [sdb] Mode Sense: 23 00 80 00 
[   76.624000] sd 2:0:0:0: [sdb] Assuming drive cache: write through 
[   76.628000] sd 2:0:0:0: [sdb] 8060928 512-byte hardware sectors (4127 MB) 
[   76.628000] sd 2:0:0:0: [sdb] Write Protect is on 
[   76.628000] sd 2:0:0:0: [sdb] Mode Sense: 23 00 80 00 
[   76.628000] sd 2:0:0:0: [sdb] Assuming drive cache: write through 
[   76.628000]  sdb: unknown partition table 
[   76.628000] sd 2:0:0:0: [sdb] Attached SCSI removable disk 
[   76.628000] sd 2:0:0:0: Attached scsi generic sg2 type 0 
[   77.276000] sd 2:0:0:0: [sdb] Device not ready: <6>: Sense Key : Not Ready [current]  
[   77.276000] : Add. Sense: Medium not present 
[   77.276000] end_request: I/O error, dev sdb, sector 8060912 
[   77.276000] Buffer I/O error on device sdb, logical block 1007614 
[   77.276000] sd 2:0:0:0: [sdb] Device not ready: <6>: Sense Key : Not Ready [current]  
[   77.276000] : Add. Sense: Medium not present 
[   77.276000] end_request: I/O error, dev sdb, sector 8060912 
[   77.276000] Buffer I/O error on device sdb, logical block 1007614 
[   77.280000] sd 2:0:0:0: [sdb] Device not ready: <6>: Sense Key : Not Ready [current]  
[   77.280000] : Add. Sense: Medium not present 
[   77.280000] end_request: I/O error, dev sdb, sector 0 
[   77.280000] Buffer I/O error on device sdb, logical block 0 
[   77.280000] sd 2:0:0:0: [sdb] Device not ready: <6>: Sense Key : Not Ready [current]  
[   77.280000] : Add. Sense: Medium not present 
[   77.280000] end_request: I/O error, dev sdb, sector 0 
[   77.280000] Buffer I/O error on device sdb, logical block 0 
[   77.284000] sd 2:0:0:0: [sdb] Device not ready: <6>: Sense Key : Not Ready [current]  
[   77.284000] : Add. Sense: Medium not present 
[   77.284000] end_request: I/O error, dev sdb, sector 8 
[   77.284000] Buffer I/O error on device sdb, logical block 1 
[   77.284000] sd 2:0:0:0: [sdb] Device not ready: <6>: Sense Key : Not Ready [current]  
[   77.284000] : Add. Sense: Medium not present 
[   77.284000] end_request: I/O error, dev sdb, sector 16 
[   77.284000] Buffer I/O error on device sdb, logical block 2 
[   77.284000] sd 2:0:0:0: [sdb] Device not ready: <6>: Sense Key : Not Ready [current]  
[   77.284000] : Add. Sense: Medium not present 
[   77.284000] end_request: I/O error, dev sdb, sector 0 
[   77.284000] Buffer I/O error on device sdb, logical block 0 
[   77.288000] sd 2:0:0:0: [sdb] Device not ready: <6>: Sense Key : Not Ready [current]  
[   77.288000] : Add. Sense: Medium not present 
[   77.288000] end_request: I/O error, dev sdb, sector 8060920 
[   77.288000] Buffer I/O error on device sdb, logical block 1007615 
[   77.288000] sd 2:0:0:0: [sdb] Device not ready: <6>: Sense Key : Not Ready [current]  
[   77.288000] : Add. Sense: Medium not present 
[   77.288000] end_request: I/O error, dev sdb, sector 8060920 
[   77.288000] Buffer I/O error on device sdb, logical block 1007615 
[   77.288000] sd 2:0:0:0: [sdb] Device not ready: <6>: Sense Key : Not Ready [current]  
[   77.288000] : Add. Sense: Medium not present 
[   77.288000] end_request: I/O error, dev sdb, sector 8060920 
[   77.288000] Buffer I/O error on device sdb, logical block 1007615 
[   77.292000] sd 2:0:0:0: [sdb] Device not ready: <6>: Sense Key : Not Ready [current]  
[   77.292000] : Add. Sense: Medium not present 
[   77.292000] end_request: I/O error, dev sdb, sector 8060920 
[   77.292000] sd 2:0:0:0: [sdb] Device not ready: <6>: Sense Key : Not Ready [current]  
[   77.292000] : Add. Sense: Medium not present 
[   77.292000] end_request: I/O error, dev sdb, sector 8060920 
[   77.292000] sd 2:0:0:0: [sdb] Device not ready: <6>: Sense Key : Not Ready [current]  
[   77.292000] : Add. Sense: Medium not present 
[   77.292000] end_request: I/O error, dev sdb, sector 8060920 
[   77.296000] sd 2:0:0:0: [sdb] Device not ready: <6>: Sense Key : Not Ready [current]  
[   77.296000] : Add. Sense: Medium not present 
[   77.296000] end_request: I/O error, dev sdb, sector 8060864 
[   77.296000] sd 2:0:0:0: [sdb] Device not ready: <6>: Sense Key : Not Ready [current]  
[   77.296000] : Add. Sense: Medium not present 
[   77.296000] end_request: I/O error, dev sdb, sector 8060912 
[   77.300000] sd 2:0:0:0: [sdb] Device not ready: <6>: Sense Key : Not Ready [current]  
[   77.300000] : Add. Sense: Medium not present 
[   77.300000] end_request: I/O error, dev sdb, sector 8060920 
[   77.300000] sd 2:0:0:0: [sdb] Device not ready: <6>: Sense Key : Not Ready [current]  
[   77.300000] : Add. Sense: Medium not present 
[   77.300000] end_request: I/O error, dev sdb, sector 8060920 
[   77.300000] sd 2:0:0:0: [sdb] Device not ready: <6>: Sense Key : Not Ready [current]  
[   77.300000] : Add. Sense: Medium not present 
[   77.300000] end_request: I/O error, dev sdb, sector 0 
[   77.304000] sd 2:0:0:0: [sdb] Device not ready: <6>: Sense Key : Not Ready [current]  
[   77.304000] : Add. Sense: Medium not present 
[   77.304000] end_request: I/O error, dev sdb, sector 0 
[   77.304000] sd 2:0:0:0: [sdb] Device not ready: <6>: Sense Key : Not Ready [current]  
[   77.304000] : Add. Sense: Medium not present 
[   77.304000] end_request: I/O error, dev sdb, sector 0 
[   77.304000] sd 2:0:0:0: [sdb] Device not ready: <6>: Sense Key : Not Ready [current]  
[   77.304000] : Add. Sense: Medium not present 
[   77.304000] end_request: I/O error, dev sdb, sector 0 
[   77.308000] sd 2:0:0:0: [sdb] Device not ready: <6>: Sense Key : Not Ready [current]  
[   77.308000] : Add. Sense: Medium not present 
[   77.308000] end_request: I/O error, dev sdb, sector 0 
[   77.312000] sd 2:0:0:0: [sdb] Device not ready: <6>: Sense Key : Not Ready [current]  
[   77.312000] : Add. Sense: Medium not present 
[   77.312000] end_request: I/O error, dev sdb, sector 0 
[   77.312000] sd 2:0:0:0: [sdb] Device not ready: <6>: Sense Key : Not Ready [current]  
[   77.312000] : Add. Sense: Medium not present 
[   77.312000] end_request: I/O error, dev sdb, sector 0 
[   77.312000] sd 2:0:0:0: [sdb] Device not ready: <6>: Sense Key : Not Ready [current]  
[   77.312000] : Add. Sense: Medium not present 
[   77.312000] end_request: I/O error, dev sdb, sector 0 
[   77.316000] sd 2:0:0:0: [sdb] Device not ready: <6>: Sense Key : Not Ready [current]  
[   77.316000] : Add. Sense: Medium not present 
[   77.316000] end_request: I/O error, dev sdb, sector 0 
[   77.316000] sd 2:0:0:0: [sdb] Device not ready: <6>: Sense Key : Not Ready [current]  
[   77.316000] : Add. Sense: Medium not present 
[   77.316000] end_request: I/O error, dev sdb, sector 0 
[   77.320000] sd 2:0:0:0: [sdb] Device not ready: <6>: Sense Key : Not Ready [current]  
[   77.320000] : Add. Sense: Medium not present 
[   77.320000] end_request: I/O error, dev sdb, sector 0 
[   77.320000] sd 2:0:0:0: [sdb] Device not ready: <6>: Sense Key : Not Ready [current]  
[   77.320000] : Add. Sense: Medium not present 
[   77.320000] end_request: I/O error, dev sdb, sector 0 
[   77.320000] sd 2:0:0:0: [sdb] Device not ready: <6>: Sense Key : Not Ready [current]  
[   77.320000] : Add. Sense: Medium not present 
[   77.320000] end_request: I/O error, dev sdb, sector 0 
[   77.324000] sd 2:0:0:0: [sdb] Device not ready: <6>: Sense Key : Not Ready [current]  
[   77.324000] : Add. Sense: Medium not present 
[   77.324000] end_request: I/O error, dev sdb, sector 0 
[   77.324000] sd 2:0:0:0: [sdb] Device not ready: <6>: Sense Key : Not Ready [current]  
[   77.324000] : Add. Sense: Medium not present 
[   77.324000] end_request: I/O error, dev sdb, sector 0 
[   77.324000] sd 2:0:0:0: [sdb] Device not ready: <6>: Sense Key : Not Ready [current]  
[   77.324000] : Add. Sense: Medium not present 
[   77.324000] end_request: I/O error, dev sdb, sector 0 
[   77.328000] sd 2:0:0:0: [sdb] Device not ready: <6>: Sense Key : Not Ready [current]  
[   77.328000] : Add. Sense: Medium not present 
[   77.328000] end_request: I/O error, dev sdb, sector 0 
[   77.328000] sd 2:0:0:0: [sdb] Device not ready: <6>: Sense Key : Not Ready [current]  
[   77.328000] : Add. Sense: Medium not present 
[   77.328000] end_request: I/O error, dev sdb, sector 0 
[   77.332000] sd 2:0:0:0: [sdb] Device not ready: <6>: Sense Key : Not Ready [current]  
[   77.332000] : Add. Sense: Medium not present 
[   77.332000] end_request: I/O error, dev sdb, sector 0 
[   77.332000] sd 2:0:0:0: [sdb] Device not ready: <6>: Sense Key : Not Ready [current]  
[   77.332000] : Add. Sense: Medium not present 
[   77.332000] end_request: I/O error, dev sdb, sector 0 
[   77.332000] sd 2:0:0:0: [sdb] Device not ready: <6>: Sense Key : Not Ready [current]  
[   77.332000] : Add. Sense: Medium not present 
[   77.332000] end_request: I/O error, dev sdb, sector 0 
[   77.336000] sd 2:0:0:0: [sdb] Device not ready: <6>: Sense Key : Not Ready [current]  
[   77.336000] : Add. Sense: Medium not present 
[   77.336000] end_request: I/O error, dev sdb, sector 0 
[   77.336000] sd 2:0:0:0: [sdb] Device not ready: <6>: Sense Key : Not Ready [current]  
[   77.336000] : Add. Sense: Medium not present 
[   77.336000] end_request: I/O error, dev sdb, sector 0 
[   77.336000] sd 2:0:0:0: [sdb] Device not ready: <6>: Sense Key : Not Ready [current]  
[   77.336000] : Add. Sense: Medium not present 
[   77.336000] end_request: I/O error, dev sdb, sector 0 
[   77.340000] sd 2:0:0:0: [sdb] Device not ready: <6>: Sense Key : Not Ready [current]  
[   77.340000] : Add. Sense: Medium not present 
[   77.340000] end_request: I/O error, dev sdb, sector 0 


Sorry for the huge lap of text.. :P
I don't know how to get those scroll things.. :$

---

### Post by Hilko on 2008-02-22
If you like to ask your questions in Dutch:

[http://forum.ubuntu-nl.org/]("http://forum.ubuntu-nl.org/")

---

### Post by sayakb on 2008-02-23
Same problem here with my USB disk..

---

