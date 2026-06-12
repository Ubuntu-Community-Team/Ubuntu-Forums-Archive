---
title: "problema hibernar"
date: 2008-10-25
forum: Software
---

### Post by tsueseres on 2008-10-25
cuando le pongo hibernar me sale este mensaje,

hibernar
el problema completo es:
1899.684778 BUG:Softlockup-CPU #1 stuck for 11s! ntos_wp:4260


hay alguna manera de solucionarlo?

---

### Post by hictio on 2008-10-25
Pero te da ese error y que pasa?
Se cuelga?
Tenes que rebootearla?

A mi me pasa que cuando Suspendo o Hiberno la laptop, me funciona bien, excepto que cuando vuelve a la vida [no anda ningun puerto USB](https://bugs.launchpad.net/ubuntu/hardy/+source/linux/+bug/257293), aunque mi laptop no es 64 bits.
La unica forma que vuelvan a andar es rebooteando.

---

### Post by tsueseres on 2008-10-25
> **hictio said:**
> Pero te da ese error y que pasa?
Se cuelga?
Tenes que rebootearla?

A mi me pasa que cuando Suspendo o Hiberno la laptop, me funciona bien, excepto que cuando vuelve a la vida [no anda ningun puerto USB](https://bugs.launchpad.net/ubuntu/hardy/+source/linux/+bug/257293), aunque mi laptop no es 64 bits.
La unica forma que vuelvan a andar es rebooteando.

se pone la pantalla negra y luego me aparece eso y luego aparece muchas veces (no muy rapido) apare en un promedio de 1 por 5 segundos y tengo que reiniciarla

---

### Post by faktorqm on 2008-10-25
Ese no es el error, eso es lo que te avisa que hubo un error, pero no dice cual es. fijate si podes acceder a otra terminal y poner dmesg. salu2!

---

### Post by tsueseres on 2008-10-26
> **faktorqm said:**
> Ese no es el error, eso es lo que te avisa que hubo un error, pero no dice cual es. fijate si podes acceder a otra terminal y poner dmesg. salu2!

me aparece esto

[   29.531681] Early unpacking initramfs... done
[   29.847485] ACPI: Core revision 20070126
[   29.847534] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   29.892280] CPU0: Intel(R) Core(TM)2 CPU          4300  @ 1.80GHz stepping 02
[   29.892296] SMP alternatives: switching to SMP code
[   29.892973] Booting processor 1/1 eip 3000
[   29.903134] Initializing CPU#1
[   29.981621] Calibrating delay using timer specific routine.. 3611.27 BogoMIPS (lpj=7222554)
[   29.981627] CPU: After generic identify, caps: bfebfbff 20100000 00000000 00000000 0000e39d 00000000 00000001 00000000
[   29.981632] monitor/mwait feature present.
[   29.981635] CPU: L1 I cache: 32K, L1 D cache: 32K
[   29.981636] CPU: L2 cache: 2048K
[   29.981638] CPU: Physical Processor ID: 0
[   29.981639] CPU: Processor Core ID: 1
[   29.981641] CPU: After all inits, caps: bfebfbff 20100000 00000000 00043940 0000e39d 00000000 00000001 00000000
[   29.982121] CPU1: Intel(R) Core(TM)2 CPU          4300  @ 1.80GHz stepping 02
[   29.982140] Total of 2 processors activated (7225.36 BogoMIPS).
[   29.982282] ENABLING IO-APIC IRQs
[   29.982447] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   30.129690] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[   30.149700] Brought up 2 CPUs
[   30.149723] CPU0 attaching sched-domain:
[   30.149725]  domain 0: span 03
[   30.149727]   groups: 01 02
[   30.149730] CPU1 attaching sched-domain:
[   30.149731]  domain 0: span 03
[   30.149733]   groups: 02 01
[   30.149945] net_namespace: 64 bytes
[   30.149956] Booting paravirtualized kernel on bare hardware
[   30.150369] Time:  9:03:08  Date: 10/26/08
[   30.150394] NET: Registered protocol family 16
[   30.150579] EISA bus registered
[   30.150583] ACPI: bus type pci registered
[   30.150779] PCI: PCI BIOS revision 3.00 entry at 0xf0031, last bus=5
[   30.150781] PCI: Using configuration type 1
[   30.150799] Setting up standard PCI resources
[   30.161534] ACPI: EC: Look up EC in DSDT
[   30.167483] ACPI: Interpreter enabled
[   30.167486] ACPI: (supports S0 S1 S3 S4 S5)
[   30.167501] ACPI: Using IOAPIC for interrupt routing
[   30.174932] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   30.175602] PCI quirk: region 0800-087f claimed by ICH6 ACPI/GPIO/TCO
[   30.175606] PCI quirk: region 0480-04bf claimed by ICH6 GPIO
[   30.176558] PCI: Transparent bridge - 0000:00:1e.0
[   30.176590] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   30.176748] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P2._PRT]
[   30.176837] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[   30.176967] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P4._PRT]
[   30.177059] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P8._PRT]
[   30.177152] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P9._PRT]
[   30.192921] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[   30.193048] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[   30.193174] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[   30.193299] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 10 11 12 14 *15)
[   30.193423] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   30.193549] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 *14 15)
[   30.193673] ACPI: PCI Interrupt Link [LNKG] (IRQs *3 4 5 6 7 10 11 12 14 15)
[   30.193802] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 *7 10 11 12 14 15)
[   30.193931] ACPI Warning (tbutils-0217): Incorrect checksum in table [OEMB] -  EE, should be ED [20070126]
[   30.193938] Linux Plug and Play Support v0.97 (c) Adam Belay
[   30.193966] pnp: PnP ACPI init
[   30.193973] ACPI: bus type pnp registered
[   30.196630] pnp: PnP ACPI: found 14 devices
[   30.196633] ACPI: ACPI bus type pnp unregistered
[   30.196636] PnPBIOS: Disabled by ACPI PNP
[   30.196858] PCI: Using ACPI for IRQ routing
[   30.196860] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   30.225674] NET: Registered protocol family 8
[   30.225677] NET: Registered protocol family 20
[   30.225720] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   30.225726] hpet0: 3 64-bit timers, 14318180 Hz
[   30.226758] AppArmor: AppArmor Filesystem Enabled
[   30.229685] Time: tsc clocksource has been installed.
[   30.229699] Switched to high resolution mode on CPU 0
[   30.229791] Switched to high resolution mode on CPU 1
[   30.241739] system 00:01: iomem range 0xfed14000-0xfed19fff has been reserved
[   30.241752] system 00:07: ioport range 0x290-0x297 has been reserved
[   30.241760] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
[   30.241764] system 00:08: ioport range 0x800-0x87f has been reserved
[   30.241767] system 00:08: ioport range 0x480-0x4bf has been reserved
[   30.241772] system 00:08: iomem range 0xffafe000-0xffb0cbff could not be reserved
[   30.241776] system 00:08: iomem range 0xffb00000-0xffbfffff could not be reserved
[   30.241780] system 00:08: iomem range 0xfed1c000-0xfed1ffff has been reserved
[   30.241783] system 00:08: iomem range 0xfed20000-0xfed8ffff has been reserved
[   30.241787] system 00:08: iomem range 0xfff00000-0xfffffffe could not be reserved
[   30.241791] system 00:08: iomem range 0xfebfe000-0xfebfec00 has been reserved
[   30.241800] system 00:0a: iomem range 0xfec00000-0xfec00fff has been reserved
[   30.241804] system 00:0a: iomem range 0xfee00000-0xfee00fff could not be reserved
[   30.241813] system 00:0c: iomem range 0xe0000000-0xefffffff has been reserved
[   30.241821] system 00:0d: iomem range 0x0-0x9ffff could not be reserved
[   30.241825] system 00:0d: iomem range 0xc0000-0xcffff could not be reserved
[   30.241829] system 00:0d: iomem range 0xe0000-0xfffff could not be reserved
[   30.241833] system 00:0d: iomem range 0x100000-0x7fffffff could not be reserved
[   30.241837] system 00:0d: iomem range 0x0-0x0 could not be reserved
[   30.272270] PCI: Bridge: 0000:00:01.0
[   30.272272]   IO window: disabled.
[   30.272275]   MEM window: f2700000-f67fffff
[   30.272278]   PREFETCH window: 9fe00000-dfdfffff
[   30.272281] PCI: Bridge: 0000:00:1c.0
[   30.272282]   IO window: disabled.
[   30.272286]   MEM window: disabled.
[   30.272289]   PREFETCH window: dfe00000-dfefffff
[   30.272294] PCI: Bridge: 0000:00:1c.4
[   30.272296]   IO window: a000-afff
[   30.272300]   MEM window: f6900000-f69fffff
[   30.272304]   PREFETCH window: disabled.
[   30.272308] PCI: Bridge: 0000:00:1c.5
[   30.272310]   IO window: 9000-9fff
[   30.272314]   MEM window: f6800000-f68fffff
[   30.272317]   PREFETCH window: disabled.
[   30.272322] PCI: Bridge: 0000:00:1e.0
[   30.272325]   IO window: b000-bfff
[   30.272329]   MEM window: f6a00000-feafffff
[   30.272332]   PREFETCH window: disabled.
[   30.272347] ACPI: PCI Interrupt 0000:00:01.0[A] -> GSI 16 (level, low) -> IRQ 16
[   30.272352] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   30.272368] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 16 (level, low) -> IRQ 16
[   30.272372] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   30.272388] ACPI: PCI Interrupt 0000:00:1c.4[A] -> GSI 16 (level, low) -> IRQ 16
[   30.272392] PCI: Setting latency timer of device 0000:00:1c.4 to 64
[   30.272409] ACPI: PCI Interrupt 0000:00:1c.5[B] -> GSI 17 (level, low) -> IRQ 17
[   30.272413] PCI: Setting latency timer of device 0000:00:1c.5 to 64
[   30.272423] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   30.272432] NET: Registered protocol family 2
[   30.309745] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   30.310006] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[   30.310398] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   30.310589] TCP: Hash tables configured (established 131072 bind 65536)
[   30.310592] TCP reno registered
[   30.321827] checking if image is initramfs... it is
[   30.944909] Freeing initrd memory: 7317k freed
[   30.945653] audit: initializing netlink socket (disabled)
[   30.945666] audit(1225011788.352:1): initialized
[   30.945865] highmem bounce pool size: 64 pages
[   30.947744] VFS: Disk quotas dquot_6.5.1
[   30.947814] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   30.947938] io scheduler noop registered
[   30.947940] io scheduler anticipatory registered
[   30.947942] io scheduler deadline registered
[   30.947952] io scheduler cfq registered (default)
[   30.980674] Boot video device is 0000:01:00.0
[   30.980774] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   30.980808] assign_interrupt_mode Found MSI capability
[   30.980836] Allocate Port Service[0000:00:01.0:pcie00]
[   30.980910] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   30.980948] assign_interrupt_mode Found MSI capability
[   30.980979] Allocate Port Service[0000:00:1c.0:pcie00]
[   30.981009] Allocate Port Service[0000:00:1c.0:pcie02]
[   30.981085] PCI: Setting latency timer of device 0000:00:1c.4 to 64
[   30.981123] assign_interrupt_mode Found MSI capability
[   30.981153] Allocate Port Service[0000:00:1c.4:pcie00]
[   30.981184] Allocate Port Service[0000:00:1c.4:pcie02]
[   30.981259] PCI: Setting latency timer of device 0000:00:1c.5 to 64
[   30.981297] assign_interrupt_mode Found MSI capability
[   30.981328] Allocate Port Service[0000:00:1c.5:pcie00]
[   30.981359] Allocate Port Service[0000:00:1c.5:pcie02]
[   30.981596] isapnp: Scanning for PnP cards...
[   31.334718] isapnp: No Plug & Play device found
[   31.358375] Real Time Clock Driver v1.12ac
[   31.358568] hpet_resources: 0xfed00000 is busy
[   31.358613] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   31.358735] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   31.359289] 00:06: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   31.360008] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   31.360070] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[   31.360159] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[   31.360161] PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[   31.360675] serio: i8042 KBD port at 0x60,0x64 irq 1
[   31.381550] mice: PS/2 mouse device common for all mice
[   31.381710] EISA: Probing bus 0 at eisa.0
[   31.381737] EISA: Detected 0 cards.
[   31.381739] cpuidle: using governor ladder
[   31.381741] cpuidle: using governor menu
[   31.381813] NET: Registered protocol family 1
[   31.381839] Using IPI No-Shortcut mode
[   31.381864] registered taskstats version 1
[   31.381979]   Magic number: 12:444:71
[   31.382023] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   31.382025] EDD information not available.
[   31.382184] Freeing unused kernel memory: 368k freed
[   31.406171] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[   32.588902] fuse init (API version 7.9)
[   32.607987] ACPI Exception (processor_core-0822): AE_NOT_FOUND, Processor Device is not present [20070126]
[   32.608000] ACPI Exception (processor_core-0822): AE_NOT_FOUND, Processor Device is not present [20070126]
[   32.728101] usbcore: registered new interface driver usbfs
[   32.728122] usbcore: registered new interface driver hub
[   32.728761] usbcore: registered new device driver usb
[   32.730283] USB Universal Host Controller Interface driver v3.0
[   32.730329] ACPI: PCI Interrupt 0000:00:1a.0[A] -> GSI 16 (level, low) -> IRQ 16
[   32.730340] PCI: Setting latency timer of device 0000:00:1a.0 to 64
[   32.730344] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[   32.730541] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[   32.730568] uhci_hcd 0000:00:1a.0: irq 16, io base 0x0000dc00
[   32.730694] usb usb1: configuration #1 chosen from 1 choice
[   32.730717] hub 1-0:1.0: USB hub found
[   32.730722] hub 1-0:1.0: 2 ports detected
[   32.833167] ACPI: PCI Interrupt 0000:00:1a.1[B] -> GSI 17 (level, low) -> IRQ 17
[   32.833179] PCI: Setting latency timer of device 0000:00:1a.1 to 64
[   32.833182] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[   32.833203] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
[   32.833230] uhci_hcd 0000:00:1a.1: irq 17, io base 0x0000e000
[   32.833336] usb usb2: configuration #1 chosen from 1 choice
[   32.833358] hub 2-0:1.0: USB hub found
[   32.833362] hub 2-0:1.0: 2 ports detected
[   32.934494] SCSI subsystem initialized
[   32.941304] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 18
[   32.941314] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   32.941318] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   32.941348] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 3
[   32.941370] libata version 3.00 loaded.
[   32.941376] uhci_hcd 0000:00:1d.0: irq 18, io base 0x0000d480
[   32.941483] usb usb3: configuration #1 chosen from 1 choice
[   32.941505] hub 3-0:1.0: USB hub found
[   32.941509] hub 3-0:1.0: 2 ports detected
[   33.046111] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 19
[   33.046122] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   33.046126] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   33.046148] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 4
[   33.046175] uhci_hcd 0000:00:1d.1: irq 19, io base 0x0000d800
[   33.046281] usb usb4: configuration #1 chosen from 1 choice
[   33.046302] hub 4-0:1.0: USB hub found
[   33.046307] hub 4-0:1.0: 2 ports detected
[   33.074022] usb 1-1: new full speed USB device using uhci_hcd and address 2
[   33.150110] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 20
[   33.150121] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   33.150125] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   33.150147] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 5
[   33.150171] uhci_hcd 0000:00:1d.2: irq 20, io base 0x0000d880
[   33.150278] usb usb5: configuration #1 chosen from 1 choice
[   33.150300] hub 5-0:1.0: USB hub found
[   33.150305] hub 5-0:1.0: 2 ports detected
[   33.240583] usb 1-1: configuration #1 chosen from 1 choice
[   33.254156] ACPI: PCI Interrupt 0000:00:1a.7[C] -> GSI 18 (level, low) -> IRQ 20
[   33.254169] PCI: Setting latency timer of device 0000:00:1a.7 to 64
[   33.254173] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[   33.254195] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 6
[   33.258106] ehci_hcd 0000:00:1a.7: debug port 1
[   33.258112] PCI: cache line size of 32 is not supported by device 0000:00:1a.7
[   33.258118] ehci_hcd 0000:00:1a.7: irq 20, io mem 0xfebffc00
[   33.273975] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   33.274081] usb usb6: configuration #1 chosen from 1 choice
[   33.274105] hub 6-0:1.0: USB hub found
[   33.274110] hub 6-0:1.0: 4 ports detected
[   33.378078] PCI: Enabling device 0000:03:00.1 (0000 -> 0001)
[   33.378085] ACPI: PCI Interrupt 0000:03:00.1[B] -> GSI 17 (level, low) -> IRQ 17
[   33.378121] PCI: Setting latency timer of device 0000:03:00.1 to 64
[   33.378183] scsi0 : pata_jmicron
[   33.378230] scsi1 : pata_jmicron
[   33.378848] ata1: PATA max UDMA/100 cmd 0xac00 ctl 0xa880 bmdma 0xa400 irq 17
[   33.378852] ata2: PATA max UDMA/100 cmd 0xa800 ctl 0xa480 bmdma 0xa408 irq 17
[   33.481925] usb 3-2: new low speed USB device using uhci_hcd and address 2
[   33.662385] usb 3-2: configuration #1 chosen from 1 choice
[   33.699322] ata1.00: ATA-5: WDC WD800BB-00CAA1, 17.07W17, max UDMA/100
[   33.699327] ata1.00: 156301488 sectors, multi 0: LBA 
[   33.699350] ata1.01: ATAPI: CRD-8400B, 1.03, max UDMA/33
[   33.699356] ata1.00: limited to UDMA/33 due to 40-wire cable
[   33.699359] ata1.01: device is on DMA blacklist, disabling DMA
[   33.714385] ata1.00: configured for UDMA/33
[   33.869433] ata1.01: configured for PIO4
[   33.904834] usb 6-1: new high speed USB device using ehci_hcd and address 2
[   34.036324] scsi 0:0:0:0: Direct-Access     ATA      WDC WD800BB-00CA 17.0 PQ: 0 ANSI: 5
[   34.036687] scsi 0:0:1:0: CD-ROM            LG       CD-ROM CRD-8400B 1.03 PQ: 0 ANSI: 5
[   34.037085] ahci 0000:03:00.0: version 3.0
[   34.037115] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   34.038380] usb 6-1: configuration #1 chosen from 1 choice
[   34.038646] usb 1-1: USB disconnect, address 2
[   34.038850] usbcore: registered new interface driver hiddev
[   34.195654] input: Microsoft Microsoft Optical Mouse with Tilt Wheel as /devices/pci0000:00/0000:00:1d.0/usb3/3-2/3-2:1.0/input/input2
[   34.204819] input,hidraw0: USB HID v1.11 Mouse [Microsoft Microsoft Optical Mouse with Tilt Wheel] on usb-0000:00:1d.0-2
[   34.204839] usbcore: registered new interface driver usbhid
[   34.204844] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   35.040622] ahci 0000:03:00.0: AHCI 0001.0000 32 slots 2 ports 3 Gbps 0x3 impl SATA mode
[   35.040628] ahci 0000:03:00.0: flags: 64bit ncq pm led clo pmp pio slum part 
[   35.040635] PCI: Setting latency timer of device 0000:03:00.0 to 64
[   35.040778] scsi2 : ahci
[   35.040978] scsi3 : ahci
[   35.041038] ata3: SATA max UDMA/133 abar m8192@0xf69fe000 port 0xf69fe100 irq 16
[   35.041041] ata4: SATA max UDMA/133 abar m8192@0xf69fe000 port 0xf69fe180 irq 16
[   35.361512] ata3: SATA link down (SStatus 0 SControl 300)
[   35.680437] ata4: SATA link down (SStatus 0 SControl 300)
[   35.681445] ACPI: PCI Interrupt 0000:05:04.0[A] -> GSI 19 (level, low) -> IRQ 19
[   35.681478] skge 1.13 addr 0xfeaf4000 irq 19 chip Yukon-Lite rev 9
[   35.681750] skge eth0: addr 00:1a:92:bb:07:4a
[   35.681788] ACPI: PCI Interrupt 0000:05:03.0[A] -> GSI 21 (level, low) -> IRQ 21
[   35.683414] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 18
[   35.683422] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   35.683426] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   35.683454] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 7
[   35.687366] ehci_hcd 0000:00:1d.7: debug port 1
[   35.687371] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   35.687376] ehci_hcd 0000:00:1d.7: irq 18, io mem 0xfebff800
[   35.731534] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[21]  MMIO=[feaff800-feafffff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   35.731575] usb 3-2: USB disconnect, address 2
[   35.731687] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   35.731778] usb usb7: configuration #1 chosen from 1 choice
[   35.731801] hub 7-0:1.0: USB hub found
[   35.731807] hub 7-0:1.0: 6 ports detected
[   35.832600] ata_piix 0000:00:1f.2: version 2.12
[   35.832608] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[   35.832648] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 19
[   35.832678] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[   35.833374] scsi4 : ata_piix
[   35.833830] scsi5 : ata_piix
[   35.835279] ata5: SATA max UDMA/133 cmd 0xec00 ctl 0xe880 bmdma 0xe400 irq 19
[   35.835282] ata6: SATA max UDMA/133 cmd 0xe800 ctl 0xe480 bmdma 0xe408 irq 19
[   36.010041] ata5.00: ATA-8: WDC WD5000AAJS-00YFA0, 12.01C02, max UDMA/133
[   36.010048] ata5.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[   36.025436] ata5.00: configured for UDMA/133
[   36.191043] scsi 4:0:0:0: Direct-Access     ATA      WDC WD5000AAJS-0 12.0 PQ: 0 ANSI: 5
[   36.191114] ata_piix 0000:00:1f.5: MAP [ P0 -- P1 -- ]
[   36.191143] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 19 (level, low) -> IRQ 19
[   36.191170] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   36.191212] scsi6 : ata_piix
[   36.191259] scsi7 : ata_piix
[   36.192202] ata7: SATA max UDMA/133 cmd 0xd400 ctl 0xd080 bmdma 0xc880 irq 19
[   36.192204] ata8: SATA max UDMA/133 cmd 0xd000 ctl 0xcc00 bmdma 0xc888 irq 19
[   36.432287] usb 3-2: new low speed USB device using uhci_hcd and address 3
[   36.531144] Driver 'sd' needs updating - please use bus_type methods
[   36.531218] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   36.531229] sd 0:0:0:0: [sda] Write Protect is off
[   36.531232] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   36.531247] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   36.531292] sd 0:0:0:0: [sda] 156301488 512-byte hardware sectors (80026 MB)
[   36.531301] sd 0:0:0:0: [sda] Write Protect is off
[   36.531303] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   36.531318] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   36.531322]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   36.554396]  sda1
[   36.554470] sd 0:0:0:0: [sda] Attached SCSI disk
[   36.554548] sd 4:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[   36.554563] sd 4:0:0:0: [sdb] Write Protect is off
[   36.554566] sd 4:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   36.554589] sd 4:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   36.554641] sd 4:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[   36.554650] sd 4:0:0:0: [sdb] Write Protect is off
[   36.554652] sd 4:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   36.554667] sd 4:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   36.554670]  sdb:sr0: scsi3-mmc drive: 40x/40x cd/rw xa/form2 cdda tray
[   36.557632] Uniform CD-ROM driver Revision: 3.20
[   36.557693] sr 0:0:1:0: Attached scsi CD-ROM sr0
[   36.562264]  sdb1 sdb2 < sdb5 sdb6 sdb7 >
[   36.595798] sd 4:0:0:0: [sdb] Attached SCSI disk
[   36.600721] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   36.600740] sr 0:0:1:0: Attached scsi generic sg1 type 5
[   36.600758] sd 4:0:0:0: Attached scsi generic sg2 type 0
[   36.613747] usb 3-2: configuration #1 chosen from 1 choice
[   36.648113] input: Microsoft Microsoft Optical Mouse with Tilt Wheel as /devices/pci0000:00/0000:00:1d.0/usb3/3-2/3-2:1.0/input/input3
[   36.664382] input,hidraw0: USB HID v1.11 Mouse [Microsoft Microsoft Optical Mouse with Tilt Wheel] on usb-0000:00:1d.0-2
[   36.988123] Attempting manual resume
[   36.988126] swsusp: Resume From Partition 8:22
[   36.988127] PM: Checking swsusp image.
[   36.988286] PM: Resume from disk failed.
[   37.003804] EXT3-fs: INFO: recovery required on readonly filesystem.
[   37.003807] EXT3-fs: write access will be enabled during recovery.
[   37.005252] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[0011d80001318def]
[   41.195614] kjournald starting.  Commit interval 5 seconds
[   41.195627] EXT3-fs: sdb7: orphan cleanup on readonly fs
[   41.195635] ext3_orphan_cleanup: deleting unreferenced inode 1775555
[   41.195672] ext3_orphan_cleanup: deleting unreferenced inode 1772057
[   41.195689] ext3_orphan_cleanup: deleting unreferenced inode 1770647
[   41.195736] ext3_orphan_cleanup: deleting unreferenced inode 851986
[   41.195750] EXT3-fs: sdb7: 4 orphan inodes deleted
[   41.195753] EXT3-fs: recovery complete.
[   41.222507] EXT3-fs: mounted filesystem with ordered data mode.
[   47.798745] input: PC Speaker as /devices/platform/pcspkr/input/input4
[   47.883657] Linux agpgart interface v0.102
[   47.949592] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   47.977584] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   48.069548] iTCO_vendor_support: vendor-support=0
[   48.085601] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   48.085671] iTCO_wdt: Found a ICH8 or ICH8R TCO device (Version=2, TCOBASE=0x0860)
[   48.085705] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   48.239800] input: Power Button (FF) as /devices/virtual/input/input5
[   48.289485] ACPI: Power Button (FF) [PWRF]
[   48.289575] input: Power Button (CM) as /devices/virtual/input/input6
[   48.349502] ACPI: Power Button (CM) [PWRB]
[   48.980886] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[   48.980898] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   48.980921] sky2 0000:02:00.0: v1.20 addr 0xf68fc000 irq 17 Yukon-EC Ultra (0xb4) rev 2
[   48.981338] sky2 eth1: addr 00:1a:92:bb:0b:34
[   49.085360] nvidia: module license 'NVIDIA' taints kernel.
[   49.407945] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   49.407954] PCI: Setting latency timer of device 0000:01:00.0 to 64
[   49.408098] NVRM: loading NVIDIA UNIX x86 Kernel Module  169.12  Thu Feb 14 17:53:07 PST 2008
[   49.430140] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low) -> IRQ 22
[   49.430159] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   50.095974] lp: driver loaded but no devices found
[   50.165337] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   50.320990] usb 6-1: reset high speed USB device using ehci_hcd and address 2
[   50.467925] ndiswrapper: driver netwg11t (NETGEAR,09/05/2005,1.5.0.2102) loaded
[   50.468391] ndiswrapper (ZwQueryValueKey:2359): not fully implemented (yet)
[   51.109239] wlan0: ethernet device 00:14:6c:e9:89:18 using NDIS driver: netwg11t, version: 0x10005, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 1385:4251.F.conf
[   51.169242] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   51.169273] usbcore: registered new interface driver ndiswrapper
[   51.208876] Adding 3100504k swap on /dev/sdb6.  Priority:-1 extents:1 across:3100504k
[   51.753625] EXT3 FS on sdb7, internal journal
[   53.193427] ip_tables: (C) 2000-2006 Netfilter Core Team
[   53.560936] No dock devices found.
[   54.461050] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   54.461056] apm: disabled - APM is not SMP safe.
[   54.563742] ppdev: user-space parallel port driver
[   54.708352] audit(1225037011.707:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5241 profile="/usr/sbin/cupsd" namespace="default"
[   55.698257] skge eth0: enabling interface
[   55.713880] sky2 eth1: enabling interface
[   55.758802] Bluetooth: Core ver 2.11
[   55.759046] NET: Registered protocol family 31
[   55.759049] Bluetooth: HCI device and connection manager initialized
[   55.759052] Bluetooth: HCI socket layer initialized
[   55.772019] Bluetooth: L2CAP ver 2.9
[   55.772024] Bluetooth: L2CAP socket layer initialized
[   55.809159] Bluetooth: RFCOMM socket layer initialized
[   55.809171] Bluetooth: RFCOMM TTY layer initialized
[   55.809173] Bluetooth: RFCOMM ver 1.8
[   64.816128] NET: Registered protocol family 10
[   64.816369] lo: Disabled Privacy Extensions
[   64.816760] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   64.816968] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   64.817187] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   81.028064] NET: Registered protocol family 17
[   86.383686] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  108.079438] wlan0: no IPv6 routers present

---

### Post by faktorqm on 2008-10-27
Para la proxima, la salida entre tags de CODE por favor...

Vamos a probar de agregar algunas cosas al kernel a ver si se soluciona el problema.
Para ver como hacerlo, mira aca: [http://ubuntuforums.org/showthread.php?t=947334](http://ubuntuforums.org/showthread.php?t=947334)
pero las opciones que le vamos a agregar son:

Primero, "pci=routeirq" y arrancar. Si no arranca, no te asustes, reinicia y todo vuelve a como estaba antes. Si el problema persiste,
proba "noapic" y arranca, si no te arranca o pasa lo mismo, proba
"noapic nolapic", si no te arranca o pasa lo mismo, postea de vuelta. Salu2!!

---

### Post by tsueseres on 2008-10-28
> **faktorqm said:**
> Para la proxima, la salida entre tags de CODE por favor...

Vamos a probar de agregar algunas cosas al kernel a ver si se soluciona el problema.
Para ver como hacerlo, mira aca: [http://ubuntuforums.org/showthread.php?t=947334](http://ubuntuforums.org/showthread.php?t=947334)
pero las opciones que le vamos a agregar son:

Primero, "pci=routeirq" y arrancar. Si no arranca, no te asustes, reinicia y todo vuelve a como estaba antes. Si el problema persiste,
proba "noapic" y arranca, si no te arranca o pasa lo mismo, proba
"noapic nolapic", si no te arranca o pasa lo mismo, postea de vuelta. Salu2!!

ya los intente y sigue igual

---

### Post by emiliano_raso on 2009-01-08
Yo siempre tuve el mismo problema en la notebook: La suspension funciona barbaro, pero hibernar nunca anduvo.
Pongo hibernar y lo hace. Queda hibernando 2 o 3 segundos y se sale solo.

---

