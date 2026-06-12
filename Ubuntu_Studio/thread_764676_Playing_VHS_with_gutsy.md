---
title: "Playing VHS with gutsy"
date: 2008-04-24
forum: Ubuntu Studio
---

### Post by benjaminitz on 2008-04-24
I'd like to watch vhs tapes on my computer. I have a VCR hooked up to a video tuner via coax cable, but I've got no idea what program to use or how to go about it. I don't want to record vhs on to my harddrive or anything. I just want to watch them.

:popcorn: <-- I want this to be me     

:confused: <-- Not this

 I'm using gutsy and my tv tuner is generic with a Phillips SAA7134 chipset. As always, sorry if someone's already posted this thread.

---

### Post by super breadfish on 2008-04-24
Give TVtime a go.

```
sudo apt-get update
sudo apt-get install tvtime
```

That will install TVtime, To run TVtime, you can find it under Programs > Sound & Video > TVtime or just type tvtime into a terminal and press enter.

As you are using coax, you'll need to tune it in. This is on the TVtime menu under Channel Management > Scan channels for signal.

If you can't get anything, your tv card probably hasn't been detected. Run
```
dmesg
```
in a terminal and post the output if this is the case.

---

### Post by benjaminitz on 2008-04-24
I can't seem to find "Channel Management > Scan channels". In the Setup menu, my options are:

Input Configuration
Picture settings
Video processing
Output configuration

Is there another menu I should be looking for or does this mean my card isn't recognized? Here's my output form dmesg. I've highlighted everything I found that refers to the tv card. It looks like I need to indicate which card I have? I think "[   "63.549725] saa7134:   card=0 -> UNKNOWN/GENERIC" is the most appropriate choice; the tuner doesn't have a brand name anywhere.




[   44.162791] PnPBIOS: 14 nodes reported by PnP BIOS; 14 recorded by driver
[   44.162900] PCI: Probing PCI hardware
[   44.162909] PCI: Probing PCI hardware (bus 00)
[   44.163303] PCI quirk: region 6000-607f claimed by vt82c686 HW-mon
[   44.163310] PCI quirk: region 5000-500f claimed by vt82c686 SMB
[   44.165248] PCI: Using IRQ router VIA [1106/0686] at 0000:00:07.0
[   44.165270] PCI->APIC IRQ transform: 0000:00:07.2[D] -> IRQ 11
[   44.165276] PCI->APIC IRQ transform: 0000:00:07.3[D] -> IRQ 11
[   44.165283] PCI->APIC IRQ transform: 0000:00:08.0[A] -> IRQ 10
[   44.165288] PCI->APIC IRQ transform: 0000:00:09.0[A] -> IRQ 5
[   44.165294] PCI->APIC IRQ transform: 0000:00:0a.0[A] -> IRQ 11
[   44.165299] PCI->APIC IRQ transform: 0000:00:0b.0[A] -> IRQ 12
[   44.165304] PCI->APIC IRQ transform: 0000:00:0c.0[A] -> IRQ 10
[   44.165310] PCI->APIC IRQ transform: 0000:01:00.0[A] -> IRQ 12
[   44.232075] NET: Registered protocol family 8
[   44.232080] NET: Registered protocol family 20
[   44.232406] pnp: 00:07: iomem range 0x0-0x9ffff could not be reserved
[   44.232413] pnp: 00:07: iomem range 0xfffe0000-0xffffffff could not be reserved
[   44.232419] pnp: 00:07: iomem range 0xfec00000-0xfec0ffff could not be reserved
[   44.232425] pnp: 00:07: iomem range 0xfee00000-0xfee0ffff could not be reserved
[   44.232437] pnp: 00:08: iomem range 0xf0000-0xf3fff could not be reserved
[   44.232443] pnp: 00:08: iomem range 0xf4000-0xf7fff could not be reserved
[   44.232449] pnp: 00:08: iomem range 0xf8000-0xfffff could not be reserved
[   44.232454] pnp: 00:08: iomem range 0xcd000-0xcffff has been reserved
[   44.233207] PCI: Bridge: 0000:00:01.0
[   44.233212]   IO window: c000-cfff
[   44.233220]   MEM window: f4000000-f5ffffff
[   44.233226]   PREFETCH window: e0000000-efffffff
[   44.233248] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   44.233274] NET: Registered protocol family 2
[   44.234968] Time: tsc clocksource has been installed.
[   44.279015] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   44.279132] TCP established hash table entries: 16384 (order: 5, 196608 bytes)
[   44.279925] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[   44.280567] TCP: Hash tables configured (established 16384 bind 16384)
[   44.280575] TCP reno registered
[   44.291367] checking if image is initramfs... it is
[   45.393172] Freeing initrd memory: 7061k freed
[   45.394325] audit: initializing netlink socket (disabled)
[   45.394381] audit(1209049203.480:1): initialized
[   45.399376] VFS: Disk quotas dquot_6.5.1
[   45.399514] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   45.399873] io scheduler noop registered
[   45.399880] io scheduler anticipatory registered
[   45.399885] io scheduler deadline registered
[   45.399922] io scheduler cfq registered (default)
[   45.399975] Applying VIA southbridge workaround.
[   45.399983] PCI: VIA PCI bridge detected. Disabling DAC.
[   45.399989] PCI: Enabling Via external APIC routing
[   45.400036] Boot video device is 0000:01:00.0
[   45.400401] isapnp: Scanning for PnP cards...
[   45.754625] isapnp: No Plug & Play device found
[   45.814941] Real Time Clock Driver v1.12ac
[   45.815139] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   45.815333] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   45.815665] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   45.816885] 00:0d: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   45.817340] 00:0e: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   45.819170] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   45.819576] input: Macintosh mouse button emulation as /class/input/input0
[   45.819805] PNP: PS/2 Controller [PNP0303] at 0x60,0x64 irq 1
[   45.819811] PNP: PS/2 controller doesn't have AUX irq; using default 12
[   46.069475] serio: i8042 KBD port at 0x60,0x64 irq 1
[   46.069745] mice: PS/2 mouse device common for all mice
[   46.070016] EISA: Probing bus 0 at eisa.0
[   46.070049] Cannot allocate resource for EISA slot 4
[   46.070054] Cannot allocate resource for EISA slot 5
[   46.070059] Cannot allocate resource for EISA slot 6
[   46.070073] EISA: Detected 0 cards.
[   46.070360] TCP cubic registered
[   46.070408] NET: Registered protocol family 1
[   46.070481] Using IPI No-Shortcut mode
[   46.070740]   Magic number: 4:343:33
[   46.071820] Freeing unused kernel memory: 364k freed
[   47.476997] AppArmor: AppArmor initialized<5>audit(1209049205.480:2):  type=1505 info="AppArmor initialized" pid=1131
[   47.511340] fuse init (API version 7.8)
[   47.523571] Failure registering capabilities with primary security module.
[   47.622034] thermal: Unknown symbol acpi_processor_set_thermal_limit
[   48.586567] usbcore: registered new interface driver usbfs
[   48.586642] usbcore: registered new interface driver hub
[   48.586711] usbcore: registered new device driver usb
[   48.666315] SCSI subsystem initialized
[   48.695042] libata version 2.21 loaded.
[   48.756489] USB Universal Host Controller Interface driver v3.0
[   48.756831] uhci_hcd 0000:00:07.2: UHCI Host Controller
[   48.757293] uhci_hcd 0000:00:07.2: new USB bus registered, assigned bus number 1
[   48.757359] uhci_hcd 0000:00:07.2: irq 11, io base 0x0000d400
[   48.757723] usb usb1: configuration #1 chosen from 1 choice
[   48.757801] hub 1-0:1.0: USB hub found
[   48.757818] hub 1-0:1.0: 2 ports detected
[   48.766644] Floppy drive(s): fd0 is 1.44M
[   48.801053] Linux Tulip driver version 1.1.15 (Feb 27, 2007)
[   48.808278] FDC 0 is a post-1991 82077
[   48.859922] uhci_hcd 0000:00:07.3: UHCI Host Controller
[   48.860047] uhci_hcd 0000:00:07.3: new USB bus registered, assigned bus number 2
[   48.860086] uhci_hcd 0000:00:07.3: irq 11, io base 0x0000d800
[   48.860380] usb usb2: configuration #1 chosen from 1 choice
[   48.860447] hub 2-0:1.0: USB hub found
[   48.860469] hub 2-0:1.0: 2 ports detected
[   48.979327] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   48.979353] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   48.981987] VP_IDE: IDE controller at PCI slot 0000:00:07.1
[   48.982069] VP_IDE: chipset revision 6
[   48.982073] VP_IDE: not 100% native mode: will probe irqs later
[   48.982093] VP_IDE: VIA vt82c686b (rev 40) IDE UDMA100 controller on pci0000:00:07.1
[   48.982113]     ide0: BM-DMA at 0xd000-0xd007, BIOS settings: hda:DMA, hdb:pio
[   48.982135]     ide1: BM-DMA at 0xd008-0xd00f, BIOS settings: hdc:DMA, hdd:DMA
[   48.982150] Probing IDE interface ide0...
[   49.098768] usb 1-1: new low speed USB device using uhci_hcd and address 2
[   49.276098] usb 1-1: configuration #1 chosen from 1 choice
[   49.399058] hda: WDC WD1200JB-00DUA3, ATA DISK drive
[   49.518399] usb 1-2: new low speed USB device using uhci_hcd and address 3
[   49.694654] usb 1-2: configuration #1 chosen from 1 choice
[   49.950123] usbcore: registered new interface driver hiddev
[   49.965673] input: Darfon USB Combo Keyboard as /class/input/input1
[   49.965724] input: USB HID v1.00 Keyboard [Darfon USB Combo Keyboard] on usb-0000:00:07.2-1
[   49.996225] input: Darfon USB Combo Keyboard as /class/input/input2
[   49.996253] input: USB HID v1.00 Device [Darfon USB Combo Keyboard] on usb-0000:00:07.2-1
[   50.009481] input: Logitech USB-PS/2 Optical Mouse as /class/input/input3
[   50.009536] input: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:07.2-2
[   50.009558] usbcore: registered new interface driver usbhid
[   50.009566] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   50.072408] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   50.072591] Probing IDE interface ide1...
[   50.933726] hdc: SAMSUNG DVD-ROM SD-816B, ATAPI CD/DVD-ROM drive
[   51.717049] hdd: Optiarc DVD RW AD-7170A, ATAPI CD/DVD-ROM drive
[   51.773477] ide1 at 0x170-0x177,0x376 on irq 15
[   51.774688] tulip0:  MII transceiver #1 config 1000 status 7849 advertising 05e1.
[   51.780020] eth0: ADMtek Comet rev 17 at Port 0xdc00, 00:14:BF:53:B9:32, IRQ 10.
[   51.793273] hda: max request size: 512KiB
[   51.807813] hda: 234441648 sectors (120034 MB) w/8192KiB Cache, CHS=16383/255/63, UDMA(100)
[   51.809423] hda: cache flushes supported
[   51.809560]  hda: hda1 hda2 < hda5 >
[   51.868736] hdc: ATAPI 48X DVD-ROM drive, 512kB Cache, UDMA(33)
[   51.868755] Uniform CD-ROM driver Revision: 3.20
[   51.876346] hdd: ATAPI 48X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, UDMA(66)
[   52.297323] Attempting manual resume
[   52.297334] swsusp: Resume From Partition 3:5
[   52.297338] PM: Checking swsusp image.
[   52.320087] PM: Resume from disk failed.
[   52.390256] kjournald starting.  Commit interval 5 seconds
[   52.390288] EXT3-fs: mounted filesystem with ordered data mode.
[   62.012666] parport_pc: VIA 686A/8231 detected
[   62.012677] parport_pc: probing current configuration
[   62.012697] parport_pc: Current parallel port base: 0x378
[   62.012761] parport0: PC-style at 0x378, irq 7 [PCSPP,EPP]
[   62.047433] Linux agpgart interface v0.102 (c) Dave Jones
[   62.051187] agpgart: Detected VIA Apollo Pro 133 chipset
[   62.056806] agpgart: AGP aperture is 64M @ 0xf0000000
[   62.107548] parport_pc: VIA parallel port: io=0x378, irq=7
[   62.169833] ath_hal: module license 'Proprietary' taints kernel.
[   62.173041] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   62.538185] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   62.657995] wlan: 0.8.4.2 (0.9.3.2)
[   62.696532] ath_pci: 0.9.4.5 (0.9.3.2)
[   63.194286] input: PC Speaker as /class/input/input4
[   63.210408] Linux video capture interface: v2.00
[   63.390176] saa7130/34: v4l2 driver version 0.2.14 loaded
[   63.480715] ath_rate_sample: 1.2 (0.9.3.2)
[   63.506428] wifi0: 11a rates: 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[   63.506449] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[   63.506458] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[   63.506476] wifi0: turboA rates: 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[   63.506488] wifi0: turboG rates: 6Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[   63.506501] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
[   63.506509] wifi0: mac 5.9 phy 4.3 radio 3.6
[   63.506518] wifi0: Use hw queue 1 for WME_AC_BE traffic
[   63.506522] wifi0: Use hw queue 0 for WME_AC_BK traffic
[   63.506526] wifi0: Use hw queue 2 for WME_AC_VI traffic
[   63.506530] wifi0: Use hw queue 3 for WME_AC_VO traffic
[   63.506534] wifi0: Use hw queue 8 for CAB traffic
[   63.506538] wifi0: Use hw queue 9 for beacons
[   63.547355] wifi0: Atheros 5212: mem=0xf7000000, irq=11
[   63.547679] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[COLOR="Red"][   63.549679] saa7130[0]: found at 0000:00:0b.0, rev: 1, irq: 12, latency: 32, mmio: 0xf7012000
[   63.549699] saa7134: <rant>
[   63.549701] saa7134:  Congratulations!  Your TV card vendor saved a few
[   63.549704] saa7134:  cents for a eeprom, thus your pci board has no
[   63.549707] saa7134:  subsystem ID and I can't identify it automatically
[   63.549710] saa7134: </rant>
[   63.549712] saa7134: I feel better now.  Ok, here are the good news:
[   63.549715] saa7134: You can use the card=<nr> insmod option to specify
[   63.549718] saa7134: which board do you have.  The list:
[   63.549725] saa7134:   card=0 -> UNKNOWN/GENERIC                         
[   63.549733] saa7134:   card=1 -> Proteus Pro [philips reference design]   1131:2001 1131:2001
[   63.549743] saa7134:   card=2 -> LifeView FlyVIDEO3000                    5168:0138 4e42:0138
[   63.549752] saa7134:   card=3 -> LifeView/Typhoon FlyVIDEO2000            5168:0138 4e42:0138
[   63.549762] saa7134:   card=4 -> EMPRESS                                  1131:6752
[   63.549770] saa7134:   card=5 -> SKNet Monster TV                         1131:4e85
[   63.549777] saa7134:   card=6 -> Tevion MD 9717                          
[   63.549783] saa7134:   card=7 -> KNC One TV-Station RDS / Typhoon TV Tune 1131:fe01 1894:fe01
[   63.549792] saa7134:   card=8 -> Terratec Cinergy 400 TV                  153b:1142
[   63.549799] saa7134:   card=9 -> Medion 5044                             
[   63.549805] saa7134:   card=10 -> Kworld/KuroutoShikou SAA7130-TVPCI      
[   63.549811] saa7134:   card=11 -> Terratec Cinergy 600 TV                  153b:1143
[   63.549819] saa7134:   card=12 -> Medion 7134                              16be:0003
[   63.549827] saa7134:   card=13 -> Typhoon TV+Radio 90031                  
[   63.549833] saa7134:   card=14 -> ELSA EX-VISION 300TV                     1048:226b
[   63.549841] saa7134:   card=15 -> ELSA EX-VISION 500TV                     1048:226a
[   63.549849] saa7134:   card=16 -> ASUS TV-FM 7134                          1043:4842 1043:4830 1043:4840
[   63.549860] saa7134:   card=17 -> AOPEN VA1000 POWER                       1131:7133
[   63.549868] saa7134:   card=18 -> BMK MPEX No Tuner                       
[   63.549874] saa7134:   card=19 -> Compro VideoMate TV                      185b:c100
[   63.549882] saa7134:   card=20 -> Matrox CronosPlus                        102b:48d0
[   63.549890] saa7134:   card=21 -> 10MOONS PCI TV CAPTURE CARD              1131:2001
[   63.549898] saa7134:   card=22 -> AverMedia M156 / Medion 2819             1461:a70b
[   63.549906] saa7134:   card=23 -> BMK MPEX Tuner                          
[   63.549912] saa7134:   card=24 -> KNC One TV-Station DVR                   1894:a006
[   63.549920] saa7134:   card=25 -> ASUS TV-FM 7133                          1043:4843
[   63.549928] saa7134:   card=26 -> Pinnacle PCTV Stereo (saa7134)           11bd:002b
[   63.549936] saa7134:   card=27 -> Manli MuchTV M-TV002/Behold TV 403 FM   
[   63.549942] saa7134:   card=28 -> Manli MuchTV M-TV001/Behold TV 401      
[   63.549948] saa7134:   card=29 -> Nagase Sangyo TransGear 3000TV           1461:050c
[   63.549955] saa7134:   card=30 -> Elitegroup ECS TVP3XP FM1216 Tuner Card( 1019:4cb4
[   63.549963] saa7134:   card=31 -> Elitegroup ECS TVP3XP FM1236 Tuner Card  1019:4cb5
[   63.549971] saa7134:   card=32 -> AVACS SmartTV                           
[   63.549977] saa7134:   card=33 -> AVerMedia DVD EZMaker                    1461:10ff
[   63.549984] saa7134:   card=34 -> Noval Prime TV 7133                     
[   63.549990] saa7134:   card=35 -> AverMedia AverTV Studio 305              1461:2115
[   63.549998] saa7134:   card=36 -> UPMOST PURPLE TV                         12ab:0800
[   63.550007] saa7134:   card=37 -> Items MuchTV Plus / IT-005              
[   63.550013] saa7134:   card=38 -> Terratec Cinergy 200 TV                  153b:1152
[   63.550021] saa7134:   card=39 -> LifeView FlyTV Platinum Mini             5168:0212 4e42:0212
[   63.550031] saa7134:   card=40 -> Compro VideoMate TV PVR/FM               185b:c100
[   63.550039] saa7134:   card=41 -> Compro VideoMate TV Gold+                185b:c100
[   63.550047] saa7134:   card=42 -> Sabrent SBT-TVFM (saa7130)              
[   63.550053] saa7134:   card=43 -> :Zolid Xpert TV7134                     
[   63.550059] saa7134:   card=44 -> Empire PCI TV-Radio LE                  
[   63.550066] saa7134:   card=45 -> Avermedia AVerTV Studio 307              1461:9715
[   63.550074] saa7134:   card=46 -> AVerMedia Cardbus TV/Radio (E500)        1461:d6ee
[   63.550082] saa7134:   card=47 -> Terratec Cinergy 400 mobile              153b:1162
[   63.550090] saa7134:   card=48 -> Terratec Cinergy 600 TV MK3              153b:1158
[   63.550098] saa7134:   card=49 -> Compro VideoMate Gold+ Pal               185b:c200
[   63.550106] saa7134:   card=50 -> Pinnacle PCTV 300i DVB-T + PAL           11bd:002d
[   63.550114] saa7134:   card=51 -> ProVideo PV952                           1540:9524
[   63.550122] saa7134:   card=52 -> AverMedia AverTV/305                     1461:2108
[   63.550129] saa7134:   card=53 -> ASUS TV-FM 7135                          1043:4845
[   63.550137] saa7134:   card=54 -> LifeView FlyTV Platinum FM / Gold        5168:0214 5168:5214 1489:0214 5168:0304
[   63.550149] saa7134:   card=55 -> LifeView FlyDVB-T DUO / MSI TV@nywhere D 5168:0306 4e42:0306
[   63.550158] saa7134:   card=56 -> Avermedia AVerTV 307                     1461:a70a
[   63.550166] saa7134:   card=57 -> Avermedia AVerTV GO 007 FM               1461:f31f
[   63.550173] saa7134:   card=58 -> ADS Tech Instant TV (saa7135)            1421:0350 1421:0351 1421:0370 1421:1370
[   63.550186] saa7134:   card=59 -> Kworld/Tevion V-Stream Xpert TV PVR7134 
[   63.550193] saa7134:   card=60 -> LifeView/Typhoon/Genius FlyDVB-T Duo Car 5168:0502 4e42:0502 1489:0502
[   63.550204] saa7134:   card=61 -> Philips TOUGH DVB-T reference design     1131:2004
[   63.550212] saa7134:   card=62 -> Compro VideoMate TV Gold+II             
[   63.550219] saa7134:   card=63 -> Kworld Xpert TV PVR7134                 
[   63.550225] saa7134:   card=64 -> FlyTV mini Asus Digimatrix               1043:0210
[   63.550233] saa7134:   card=65 -> V-Stream Studio TV Terminator           
[   63.550239] saa7134:   card=66 -> Yuan TUN-900 (saa7135)                  
[   63.550245] saa7134:   card=67 -> Beholder BeholdTV 409 FM                 0000:4091
[   63.550254] saa7134:   card=68 -> GoTView 7135 PCI                         5456:7135
[   63.550262] saa7134:   card=69 -> Philips EUROPA V3 reference design       1131:2004
[   63.550269] saa7134:   card=70 -> Compro Videomate DVB-T300                185b:c900
[   63.550277] saa7134:   card=71 -> Compro Videomate DVB-T200                185b:c901
[   63.550285] saa7134:   card=72 -> RTD Embedded Technologies VFG7350        1435:7350
[   63.550293] saa7134:   card=73 -> RTD Embedded Technologies VFG7330        1435:7330
[   63.550301] saa7134:   card=74 -> LifeView FlyTV Platinum Mini2            14c0:1212
[   63.550310] saa7134:   card=75 -> AVerMedia AVerTVHD MCE A180              1461:1044
[   63.550317] saa7134:   card=76 -> SKNet MonsterTV Mobile                   1131:4ee9
[   63.550325] saa7134:   card=77 -> Pinnacle PCTV 40i/50i/110i (saa7133)     11bd:002e
[   63.550334] saa7134:   card=78 -> ASUSTeK P7131 Dual                       1043:4862 1043:4857
[   63.550343] saa7134:   card=79 -> Sedna/MuchTV PC TV Cardbus TV/Radio (ITO
[   63.550350] saa7134:   card=80 -> ASUS Digimatrix TV                       1043:0210
[   63.550358] saa7134:   card=81 -> Philips Tiger reference design           1131:2018
[   63.550366] saa7134:   card=82 -> MSI TV@Anywhere plus                     1462:6231
[   63.550374] saa7134:   card=83 -> Terratec Cinergy 250 PCI TV              153b:1160
[   63.550382] saa7134:   card=84 -> LifeView FlyDVB Trio                     5168:0319
[   63.550389] saa7134:   card=85 -> AverTV DVB-T 777                         1461:2c05 1461:2c05
[   63.550399] saa7134:   card=86 -> LifeView FlyDVB-T / Genius VideoWonder D 5168:0301 1489:0301
[   63.550409] saa7134:   card=87 -> ADS Instant TV Duo Cardbus PTV331        0331:1421
[   63.550416] saa7134:   card=88 -> Tevion/KWorld DVB-T 220RF                17de:7201
[   63.550424] saa7134:   card=89 -> ELSA EX-VISION 700TV                     1048:226c
[   63.550433] saa7134:   card=90 -> Kworld ATSC110                           17de:7350
[   63.550441] saa7134:   card=91 -> AVerMedia A169 B                         1461:7360
[   63.550449] saa7134:   card=92 -> AVerMedia A169 B1                        1461:6360
[   63.550456] saa7134:   card=93 -> Medion 7134 Bridge #2                    16be:0005
[   63.550464] saa7134:   card=94 -> LifeView FlyDVB-T Hybrid Cardbus         5168:3306 5168:3502
[   63.550474] saa7134:   card=95 -> LifeView FlyVIDEO3000 (NTSC)             5169:0138
[   63.550482] saa7134:   card=96 -> Medion Md8800 Quadro                     16be:0007 16be:0008
[   63.550491] saa7134:   card=97 -> LifeView FlyDVB-S /Acorp TV134DS         5168:0300 4e42:0300
[   63.550501] saa7134:   card=98 -> Proteus Pro 2309                         0919:2003
[   63.550510] saa7134:   card=99 -> AVerMedia TV Hybrid A16AR                1461:2c00
[   63.550517] saa7134:   card=100 -> Asus Europa2 OEM                         1043:4860
[   63.550525] saa7134:   card=101 -> Pinnacle PCTV 310i                       11bd:002f
[   63.550533] saa7134:   card=102 -> Avermedia AVerTV Studio 507              1461:9715
[   63.550541] saa7134:   card=103 -> Compro Videomate DVB-T200A              
[   63.550548] saa7134:   card=104 -> Hauppauge WinTV-HVR1110 DVB-T/Hybrid     0070:6701
[   63.550555] saa7134:   card=105 -> Terratec Cinergy HT PCMCIA               153b:1172
[   63.550563] saa7134:   card=106 -> Encore ENLTV                             1131:2342 1131:2341 3016:2344
[   63.550575] saa7134:   card=107 -> Encore ENLTV-FM                          1131:230f
[   63.550676] saa7134:   card=108 -> Terratec Cinergy HT PCI                  153b:1175
[   63.550684] saa7134:   card=109 -> Philips Tiger - S Reference design      
[   63.550690] saa7134:   card=110 -> Avermedia M102                           1461:f31e
[   63.550699] saa7134:   card=111 -> ASUS P7131 4871                          1043:4871
[   63.550707] saa7134:   card=112 -> ASUSTeK P7131 Hybrid                     1043:4876
[   63.550714] saa7134:   card=113 -> Elitegroup ECS TVP3XP FM1246 Tuner Card  1019:4cb6
[   63.550722] saa7134:   card=114 -> KWorld DVB-T 210                         17de:7250
[   63.550731] saa7134:   card=115 -> Sabrent PCMCIA TV-PCB05                  0919:2003
[   63.550740] saa7130[0]: subsystem: 1131:0000, board: UNKNOWN/GENERIC [card=0,autodetected]
[   63.550779] saa7130[0]: board init: gpio is 804000
[   63.655460] saa7130[0]: Huh, no eeprom present (err=-5)?
[   63.655605] saa7130[0]: registered device video0 [v4l2]
[   63.655716] saa7130[0]: registered device vbi0[/COLOR]
[   63.670445] usbcore: registered new interface driver xpad
[   63.670461] /build/buildd/linux-source-2.6.22-2.6.22/drivers/input/joystick/xpad.c: driver for Xbox controllers v0.1.6
[   63.992634] saa7134 ALSA driver for DMA sound loaded
[   63.992775] saa7130[0]/alsa: saa7130[0] at 0xf7012000 irq 12 registered as card -2
[   64.156551] snd-ca0106: Model 100a Rev 00000000 Serial 100a1102
[   64.458444] lp0: using parport0 (interrupt-driven).
[   64.543671] Adding 1510068k swap on /dev/hda5.  Priority:-1 extents:1 across:1510068k
[   64.960393] EXT3 FS on hda1, internal journal
[   66.907174] acpi_cpufreq: Unknown symbol acpi_processor_notify_smm
[   66.907309] acpi_cpufreq: Unknown symbol acpi_processor_unregister_performance
[   66.907683] acpi_cpufreq: Unknown symbol acpi_processor_preregister_performance
[   66.907854] acpi_cpufreq: Unknown symbol acpi_processor_register_performance
[   68.423624] ppdev: user-space parallel port driver
[   68.512203] audit(1209049226.899:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4534 profile="/usr/sbin/cupsd"
[   70.498344] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[   70.498365] apm: disabled - APM is not SMP safe.
[   71.221823] NET: Registered protocol family 10
[   71.222463] lo: Disabled Privacy Extensions
[   71.276252] Failure registering capabilities with primary security module.
[   71.547206] Bluetooth: Core ver 2.11
[   71.547659] NET: Registered protocol family 31
[   71.547664] Bluetooth: HCI device and connection manager initialized
[   71.547676] Bluetooth: HCI socket layer initialized
[   71.568537] Bluetooth: L2CAP ver 2.8
[   71.568568] Bluetooth: L2CAP socket layer initialized
[   71.610854] Bluetooth: RFCOMM socket layer initialized
[   71.610929] Bluetooth: RFCOMM TTY layer initialized
[   71.610934] Bluetooth: RFCOMM ver 1.8
[   73.826964] [drm] Initialized drm 1.1.0 20060810
[   73.840209] [drm] Initialized radeon 1.27.0 20060524 on minor 0
[   76.095890] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[   76.095944] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[   76.096015] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[   76.359997] [drm] Setting GART location based on new memory map
[   76.360021] [drm] Loading R200 Microcode
[   76.360102] [drm] writeback test succeeded in 1 usecs
[   81.698866] ath0: no IPv6 routers present
[  153.110149] UDF-fs: Partition marked readonly; forcing readonly mount
[  153.169167] UDF-fs INFO UDF 0.9.8.1 (2004/29/09) Mounting volume 'FELLOWSHIP_EXT_D1', timestamp 2002/08/20 04:13 (1ed4)
[  158.379618] NET: Registered protocol family 17
[  209.108461] ath0: no IPv6 routers present
[  221.533339] ath0: no IPv6 routers present
[ 7392.503529] usb 2-2: new full speed USB device using uhci_hcd and address 2
[ 7392.678911] usb 2-2: configuration #1 chosen from 1 choice
[ 7392.945913] usbcore: registered new interface driver libusual
[ 7393.030930] Initializing USB Mass Storage driver...
[ 7393.031735] scsi0 : SCSI emulation for USB Mass Storage devices
[ 7393.032025] usb-storage: device found at 2
[ 7393.032031] usb-storage: waiting for device to settle before scanning
[ 7393.032311] usbcore: registered new interface driver usb-storage
[ 7393.032457] USB Mass Storage support registered.
[ 7398.029066] usb-storage: device scan complete
[ 7398.032372] scsi 0:0:0:0: Direct-Access     Memorex  TD Classic 003B  PMAP PQ: 0 ANSI: 0 CCS
[ 7398.576361] sd 0:0:0:0: [sda] 2015232 512-byte hardware sectors (1032 MB)
[ 7398.582957] sd 0:0:0:0: [sda] Write Protect is off
[ 7398.582998] sd 0:0:0:0: [sda] Mode Sense: 23 00 00 00
[ 7398.583007] sd 0:0:0:0: [sda] Assuming drive cache: write through
[ 7398.595234] sd 0:0:0:0: [sda] 2015232 512-byte hardware sectors (1032 MB)
[ 7398.598210] sd 0:0:0:0: [sda] Write Protect is off
[ 7398.598218] sd 0:0:0:0: [sda] Mode Sense: 23 00 00 00
[ 7398.598224] sd 0:0:0:0: [sda] Assuming drive cache: write through
[ 7398.598242]  sda: sda1
[ 7398.605848] sd 0:0:0:0: [sda] Attached SCSI removable disk
[ 7398.635328] sd 0:0:0:0: Attached scsi generic sg0 type 0
[ 7442.876315] usb 2-2: USB disconnect, address 2

---

### Post by super breadfish on 2008-04-24
Yup, your card hasn't been detected. You need to find the right card and tuner numbers to get Linux to load the right drivers. A lot unbranded (or obscure branded) cards tend to be clones of more popular cards. My own card is a no-brand clone of a KWorld card, so I use KWorld settings. There are some odd cards out there though that might not work.

There are numerous threads discussing how to do this, and other websites like the Gentoo wiki can be useful for technical details. Here a few threads lurking in my subscribe list:

[http://ubuntuforums.org/showthread.php?t=712400]("http://ubuntuforums.org/showthread.php?t=712400")
[http://ubuntuforums.org/showthread.php?t=408307]("http://ubuntuforums.org/showthread.php?t=408307")
[http://ubuntuforums.org/showthread.php?t=405327]("http://ubuntuforums.org/showthread.php?t=405327")

---

### Post by benjaminitz on 2008-04-24
I tried following the instructions from this thread:[http://ubuntuforums.org/showthread.php?t=712400](http://ubuntuforums.org/showthread.php?t=712400) 

When I enter the code

```
modprobe -r saa7134
```

I get the following output:

```
FATAL: Module saa7134 is in use.
```

---

### Post by benjaminitz on 2008-04-24
I tried following the instructions from this thread:[http://ubuntuforums.org/showthread.php?t=712400](http://ubuntuforums.org/showthread.php?t=712400) 

When I enter the code

```
modprobe -r saa7134
```

I get the following output:

```
FATAL: Module saa7134 is in use.
```

---

