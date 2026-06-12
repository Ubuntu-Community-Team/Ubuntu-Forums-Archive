---
title: "Daru1 Lost wireless with Hardy install!"
date: 2008-04-30
forum: System76 Support
---

### Post by TomLawell on 2008-04-30
Hardy install seems to have gone well except the revolving network icon looks for several seconds and then gives up. Clicking here show my router and a neighbor's.
I can connect to the internet using the cat5 cable on my Belkin preN router. 
No blue wireless light on lower left indicator panel. I am not sure about the small silver switch and push button in the upper left keyboard or how to use the (Fn F2) command that shows the wireless label. All worked well before upgrade. Still using 302 firmware. 
I need pointer to step by step check out. Pretty much a nubie!

Thank you.

Tom Lawell

---

### Post by ctsdownloads on 2008-04-30
> **TomLawell said:**
> Hardy install seems to have gone well except the revolving network icon looks for several seconds and then gives up. Clicking here show my router and a neighbor's.
I can connect to the internet using the cat5 cable on my Belkin preN router. 
No blue wireless light on lower left indicator panel. I am not sure about the small silver switch and push button in the upper left keyboard or how to use the (Fn F2) command that shows the wireless label. All worked well before upgrade. Still using 302 firmware. 
I need pointer to step by step check out. Pretty much a nubie!

Thank you.

Tom Lawell

We will need a bit of info, but not to worry, this is as easy as cut and paste, you can totally not concern yourself with anything with these commands, it is just providing needed info to help. Also, ensure that any switches that are corresponding to your wireless device are in fact, turned on with your computer. This is a common issue.

Let's start with this -  just goto: 

[I]Applications, Accessories, Terminal.
[/I]
In the terminal, type this exactly:

> lshw -C network

It will spit out a whole ton of stuff, using your mouse (as keyboard shortcuts will not work) copy and paste the contents of the output here.

Then rinse and repeat with 

> iwconfig

and

> ifconfig

and finally,

> dmesg


This is going to give us an idea of what your machine is trying to tell you with a lack of wireless. Basically, with these great diagnostic tools.

Providing the output for each of these is going to allow you to get this resolved MUCH faster as it will give everyone every detail they will need. Again, just type and cut/paste, that is all you need to do. And if you want, use your mouse to paste in the commands into the terminal, this prevents issues with case sensitive letters.

---

### Post by TomLawell on 2008-04-30
Thank you for the help. I am posting the outputs below.
I will post dmseg in the next post.

Tom Lawell


tomlawell@Jessie-ubuntu:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wmaster0
       version: 02
       serial: 00:18:de:28:b6:25
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 4
       bus info: pci@0000:05:04.0
       logical name: eth1
       version: 10
       serial: 00:18:f3:83:34:32
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes
tomlawell@Jessie-ubuntu:~$ 

tomlawell@Jessie-ubuntu:~$ iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

wmaster0  no wireless extensions.

eth2      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:11:50:20:E0:D9   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

tomlawell@Jessie-ubuntu:~$ 

tomlawell@Jessie-ubuntu:~$ ifconfig
eth1      Link encap:Ethernet  HWaddr 00:18:f3:83:34:32  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:22 Base address:0xd800 

eth2      Link encap:Ethernet  HWaddr 00:18:de:28:b6:25  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2938 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2938 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:148848 (145.3 KB)  TX bytes:148848 (145.3 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-18-DE-28-B6-25-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

tomlawell@Jessie-ubuntu:~$

---

### Post by TomLawell on 2008-04-30
Here is the dmseg output.


[   16.305551] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[   16.305577] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[   16.305612] uhci_hcd 0000:00:1d.3: irq 16, io base 0x0000e400
[   16.305740] usb usb4: configuration #1 chosen from 1 choice
[   16.305767] hub 4-0:1.0: USB hub found
[   16.305773] hub 4-0:1.0: 2 ports detected
[   16.409512] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 18
[   16.409530] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[   16.409535] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[   16.409564] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[   16.413464] ehci_hcd 0000:00:1d.7: debug port 1
[   16.413471] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[   16.413479] ehci_hcd 0000:00:1d.7: irq 18, io mem 0xfeb3bc00
[   16.429268] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   16.429424] usb usb5: configuration #1 chosen from 1 choice
[   16.429453] hub 5-0:1.0: USB hub found
[   16.429460] hub 5-0:1.0: 8 ports detected
[   16.533371] 8139cp 0000:05:04.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[   16.533378] 8139cp 0000:05:04.0: Try the "8139too" driver instead.
[   16.535991] ACPI: PCI Interrupt 0000:05:03.0[A] -> GSI 21 (level, low) -> IRQ 21
[   16.588709] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[21]  MMIO=[fe8ff800-fe8fffff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[   16.594696] 8139too Fast Ethernet driver 0.9.28
[   16.601265] ACPI: PCI Interrupt 0000:05:04.0[A] -> GSI 20 (level, low) -> IRQ 22
[   16.602289] eth0: RealTek RTL8139 at 0xd800, 00:18:f3:83:34:32, IRQ 22
[   16.602292] eth0:  Identified 8139 chip type 'RTL-8101'
[   16.603371] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 20
[   16.603409] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   16.603424] ACPI: PCI interrupt for device 0000:00:1f.1 disabled
[   16.609076] ata_piix 0000:00:1f.1: version 2.12
[   16.609096] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 20
[   16.609135] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[   16.610262] scsi0 : ata_piix
[   16.610917] scsi1 : ata_piix
[   16.612616] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xffa0 irq 14
[   16.612620] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xffa8 irq 15
[   16.953361] ata1.00: ATA-6: HTS541040G9AT00, MB2OA60A, max UDMA/100
[   16.953366] ata1.00: 78140160 sectors, multi 16: LBA48 
[   16.953398] ata1.01: ATAPI: TSSTcorpCD/DVDW TS-L632D, AS05, max UDMA/33
[   16.969239] ata1.00: configured for UDMA/100
[   17.156706] ata1.01: configured for UDMA/33
[   17.156762] ata2: port disabled. ignoring.
[   17.156904] scsi 0:0:0:0: Direct-Access     ATA      HTS541040G9AT00  MB2O PQ: 0 ANSI: 5
[   17.166014] scsi 0:0:1:0: CD-ROM            TSSTcorp CD/DVDW TS-L632D AS05 PQ: 0 ANSI: 5
[   17.176275] usb 3-2: new full speed USB device using uhci_hcd and address 2
[   17.176342] Driver 'sd' needs updating - please use bus_type methods
[   17.176432] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors (40008 MB)
[   17.176447] sd 0:0:0:0: [sda] Write Protect is off
[   17.176450] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   17.176470] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   17.176522] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors (40008 MB)
[   17.176534] sd 0:0:0:0: [sda] Write Protect is off
[   17.176537] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   17.176555] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   17.176559]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   17.198257]  sda1 sda2 < sda5 >
[   17.222072] sd 0:0:0:0: [sda] Attached SCSI disk
[   17.228500] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   17.228523] sr 0:0:1:0: Attached scsi generic sg1 type 5
[   17.294385] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[   17.294392] Uniform CD-ROM driver Revision: 3.20
[   17.294455] sr 0:0:1:0: Attached scsi CD-ROM sr0
[   17.421272] usb 3-2: configuration #1 chosen from 1 choice
[   17.549366] Attempting manual resume
[   17.549371] swsusp: Resume From Partition 8:5
[   17.549373] PM: Checking swsusp image.
[   17.549573] PM: Resume from disk failed.
[   17.586071] kjournald starting.  Commit interval 5 seconds
[   17.586087] EXT3-fs: mounted filesystem with ordered data mode.
[   17.867461] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00e01800036bab22]
[   29.109487] input: PC Speaker as /devices/platform/pcspkr/input/input2
[   29.975157] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   30.007157] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   30.059029] iTCO_vendor_support: vendor-support=0
[   30.098970] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.02 (26-Jul-2007)
[   30.099075] iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0x0860)
[   30.099114] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   30.222804] Linux agpgart interface v0.102
[   30.274785] agpgart: Detected an Intel 945GM Chipset.
[   30.275136] agpgart: Detected 7932K stolen memory.
[   30.293326] agpgart: AGP aperture is 256M @ 0xd0000000
[   30.402551] intel_rng: FWH not detected
[   31.126356] input: Power Button (FF) as /devices/virtual/input/input3
[   31.141559] ACPI: Power Button (FF) [PWRF]
[   31.141686] input: Lid Switch as /devices/virtual/input/input4
[   31.177767] ACPI: Lid Switch [LID]
[   31.177891] input: Sleep Button (CM) as /devices/virtual/input/input5
[   31.189487] ACPI: Sleep Button (CM) [SLPB]
[   31.189591] input: Power Button (CM) as /devices/virtual/input/input6
[   31.201472] ACPI: Power Button (CM) [PWRB]
[   31.235083] asus-laptop: Asus Laptop Support version 0.42
[   31.235399] asus-laptop:   Z35FM model detected
[   31.279770] Registered led device: asus:touchpad
[   32.174605] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.0
[   32.174610] iwl3945: Copyright(c) 2003-2007 Intel Corporation
[   32.175462] ACPI: PCI Interrupt 0000:04:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[   32.175479] PCI: Setting latency timer of device 0000:04:00.0 to 64
[   32.175533] iwl3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[   32.595999] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 16 (level, low) -> IRQ 16
[   32.596029] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   32.634379] sdhci: Secure Digital Host Controller Interface driver
[   32.634383] sdhci: Copyright(c) Pierre Ossman
[   33.449916] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x1a0b1, caps: 0xa04713/0x200000
[   33.486381] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input7
[   33.871056] ACPI: AC Adapter [AC0] (on-line)
[   33.956490] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input8
[   33.977797] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   34.141998] ACPI: Battery Slot [BAT0] (battery present)
[   34.273606] udev: renamed network interface eth0 to eth1
[   34.871217] Bluetooth: Core ver 2.11
[   34.874943] NET: Registered protocol family 31
[   34.874947] Bluetooth: HCI device and connection manager initialized
[   34.874951] Bluetooth: HCI socket layer initialized
[   34.896623] Bluetooth: HCI USB driver ver 2.9
[   34.899098] usbcore: registered new interface driver hci_usb
[   36.174706] sdhci: SDHCI controller found at 0000:05:03.1 [1180:0822] (rev 19)
[   36.174738] ACPI: PCI Interrupt 0000:05:03.1[B] -> GSI 20 (level, low) -> IRQ 22
[   36.174761] sdhci:slot0: Will use DMA mode even though HW doesn't fully claim to support it.
[   36.174835] mmc0: SDHCI at 0xfe8ff400 irq 22 DMA
[   36.234641] iwl3945: Tunable channels: 11 802.11bg, 13 802.11a channels
[   36.239664] wmaster0: Selected rate control algorithm 'iwl-3945-rs'
[   36.670981] udev: renamed network interface wlan0 to eth2
[   37.775277] lp: driver loaded but no devices found
[   38.636012] EXT3 FS on sda1, internal journal
[   39.944133] ip_tables: (C) 2000-2006 Netfilter Core Team
[   42.002769] No dock devices found.
[   44.236216] eth1: link down
[   45.447135] NET: Registered protocol family 10
[   45.447814] lo: Disabled Privacy Extensions
[   45.448549] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   45.449395] ADDRCONF(NETDEV_UP): eth2: link is not ready
[   46.540966] [drm] Initialized drm 1.1.0 20060810
[   46.544620] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
[   46.544630] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   46.544712] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   46.948380] ppdev: user-space parallel port driver
[   47.216790] audit(1209583128.572:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=5291 profile="/usr/sbin/cupsd" namespace="default"
[   47.276200] apm: BIOS not found.
[   47.624641] RPC: Registered udp transport module.
[   47.624647] RPC: Registered tcp transport module.
[   47.684262] Installing knfsd (copyright (C) 1996 [email]okir@monad.swb.de[/email]).
[   47.744111] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[   47.753030] NFSD: starting 90-second grace period
[   49.310744] Bluetooth: L2CAP ver 2.9
[   49.310749] Bluetooth: L2CAP socket layer initialized
[   49.317339] Bluetooth: RFCOMM socket layer initialized
[   49.317356] Bluetooth: RFCOMM TTY layer initialized
[   49.317358] Bluetooth: RFCOMM ver 1.8
[   72.682226] NET: Registered protocol family 17
[   74.512395] eth2: Initial auth_alg=0
[   74.512403] eth2: authenticate with AP 00:11:50:20:e0:d9
[   74.514038] eth2: Initial auth_alg=0
[   74.514043] eth2: authenticate with AP 00:11:50:20:e0:d9
[   74.514060] eth2: RX authentication from 00:11:50:20:e0:d9 (alg=0 transaction=2 status=0)
[   74.514063] eth2: authenticated
[   74.514066] eth2: associate with AP 00:11:50:20:e0:d9
[   74.514996] eth2: authentication frame received from 00:11:50:20:e0:d9, but not in authenticate state - ignored
[   74.516566] eth2: authentication frame received from 00:11:50:20:e0:d9, but not in authenticate state - ignored
[   74.517754] eth2: authentication frame received from 00:11:50:20:e0:d9, but not in authenticate state - ignored
[   74.519666] eth2: authentication frame received from 00:11:50:20:e0:d9, but not in authenticate state - ignored
[   74.521698] eth2: RX AssocResp from 00:11:50:20:e0:d9 (capab=0x401 status=18 aid=1)
[   74.521702] eth2: AP denied association (code=18)
[   74.711169] eth2: associate with AP 00:11:50:20:e0:d9
[   74.712560] eth2: RX AssocResp from 00:11:50:20:e0:d9 (capab=0x401 status=18 aid=1)
[   74.712565] eth2: AP denied association (code=18)
[   74.910916] eth2: associate with AP 00:11:50:20:e0:d9
[   74.912299] eth2: RX AssocResp from 00:11:50:20:e0:d9 (capab=0x401 status=18 aid=1)
[   74.912303] eth2: AP denied association (code=18)
[   75.110633] eth2: association with AP 00:11:50:20:e0:d9 timed out
[   87.154406] eth2: RX deauthentication from 00:11:50:20:e0:d9 (reason=7)
[   87.154412] eth2: deauthenticated
[   87.154417] eth2: RX deauthentication from 00:11:50:20:e0:d9 (reason=7)
[   87.154421] eth2: RX deauthentication from 00:11:50:20:e0:d9 (reason=7)
[   87.154425] eth2: RX deauthentication from 00:11:50:20:e0:d9 (reason=7)
[   87.154430] eth2: RX deauthentication from 00:11:50:20:e0:d9 (reason=7)
[   87.154434] eth2: RX deauthentication from 00:11:50:20:e0:d9 (reason=7)
[   87.154438] eth2: RX deauthentication from 00:11:50:20:e0:d9 (reason=7)
[   87.154442] eth2: RX deauthentication from 00:11:50:20:e0:d9 (reason=7)
[   87.154447] eth2: RX deauthentication from 00:11:50:20:e0:d9 (reason=7)
[   87.154451] eth2: RX deauthentication from 00:11:50:20:e0:d9 (reason=7)
[   87.154455] eth2: RX deauthentication from 00:11:50:20:e0:d9 (reason=7)
[   87.154459] eth2: RX deauthentication from 00:11:50:20:e0:d9 (reason=7)
[   87.156540] eth2: RX deauthentication from 00:11:50:20:e0:d9 (reason=7)
[   87.157061] eth2: Initial auth_alg=0
[   87.157065] eth2: authenticate with AP 00:11:50:20:e0:d9
[   87.158563] eth2: Initial auth_alg=0
[   87.158569] eth2: authenticate with AP 00:11:50:20:e0:d9
[   87.160187] eth2: RX authentication from 00:11:50:20:e0:d9 (alg=0 transaction=2 status=0)
[   87.160192] eth2: authenticated
[   87.160195] eth2: associate with AP 00:11:50:20:e0:d9
[   87.161590] eth2: RX AssocResp from 00:11:50:20:e0:d9 (capab=0x401 status=18 aid=1)
[   87.161594] eth2: AP denied association (code=18)
[   87.358239] eth2: associate with AP 00:11:50:20:e0:d9
[   87.359647] eth2: RX AssocResp from 00:11:50:20:e0:d9 (capab=0x401 status=18 aid=1)
[   87.359651] eth2: AP denied association (code=18)
[   87.557976] eth2: associate with AP 00:11:50:20:e0:d9
[   87.559379] eth2: RX AssocResp from 00:11:50:20:e0:d9 (capab=0x401 status=18 aid=1)
[   87.559383] eth2: AP denied association (code=18)
[   87.757702] eth2: association with AP 00:11:50:20:e0:d9 timed out
[   99.937151] eth2: RX deauthentication from 00:11:50:20:e0:d9 (reason=7)
[   99.937157] eth2: deauthenticated
[   99.937161] eth2: RX deauthentication from 00:11:50:20:e0:d9 (reason=7)
[   99.937166] eth2: RX deauthentication from 00:11:50:20:e0:d9 (reason=7)
[   99.937170] eth2: RX deauthentication from 00:11:50:20:e0:d9 (reason=7)
[   99.937174] eth2: RX deauthentication from 00:11:50:20:e0:d9 (reason=7)
[   99.937179] eth2: RX deauthentication from 00:11:50:20:e0:d9 (reason=7)
[   99.937183] eth2: RX deauthentication from 00:11:50:20:e0:d9 (reason=7)
[   99.937187] eth2: RX deauthentication from 00:11:50:20:e0:d9 (reason=7)
[   99.937191] eth2: RX deauthentication from 00:11:50:20:e0:d9 (reason=7)
[   99.937197] eth2: RX deauthentication from 00:11:50:20:e0:d9 (reason=7)
[   99.937202] eth2: RX deauthentication from 00:11:50:20:e0:d9 (reason=7)
[   99.937207] eth2: RX deauthentication from 00:11:50:20:e0:d9 (reason=7)
[   99.937212] eth2: RX deauthentication from 00:11:50:20:e0:d9 (reason=7)
[   99.937216] eth2: RX deauthentication from 00:11:50:20:e0:d9 (reason=7)
[   99.939934] eth2: RX deauthentication from 00:11:50:20:e0:d9 (reason=7)
[   99.941985] eth2: Initial auth_alg=0
[   99.941991] eth2: authenticate with AP 00:11:50:20:e0:d9
[   99.942682] eth2: Initial auth_alg=0
[   99.942686] eth2: authenticate with AP 00:11:50:20:e0:d9
[   99.944408] eth2: RX authentication from 00:11:50:20:e0:d9 (alg=0 transaction=2 status=0)
[   99.944412] eth2: authenticated
[   99.944415] eth2: associate with AP 00:11:50:20:e0:d9
[   99.946931] eth2: RX AssocResp from 00:11:50:20:e0:d9 (capab=0x401 status=18 aid=1)
[   99.946936] eth2: AP denied association (code=18)
[   99.948923] eth2: RX AssocResp from 00:11:50:20:e0:d9 (capab=0x401 status=18 aid=1)
[   99.948926] eth2: AP denied association (code=18)
[  100.141440] eth2: associate with AP 00:11:50:20:e0:d9
[  100.143230] eth2: RX AssocResp from 00:11:50:20:e0:d9 (capab=0x401 status=18 aid=1)
[  100.143235] eth2: AP denied association (code=18)
[  100.341175] eth2: associate with AP 00:11:50:20:e0:d9
[  100.343044] eth2: RX AssocResp from 00:11:50:20:e0:d9 (capab=0x401 status=18 aid=1)
[  100.343049] eth2: AP denied association (code=18)
[  100.344134] eth2: RX AssocResp from 00:11:50:20:e0:d9 (capab=0x401 status=18 aid=1)
[  100.344138] eth2: AP denied association (code=18)
[  100.540577] eth2: association with AP 00:11:50:20:e0:d9 timed out
[  117.221440] eth2: RX deauthentication from 00:11:50:20:e0:d9 (reason=7)
[  117.221446] eth2: deauthenticated
[  117.221452] eth2: RX deauthentication from 00:11:50:20:e0:d9 (reason=7)
[  117.224692] eth2: Initial auth_alg=0
[  117.224697] eth2: authenticate with AP 00:11:50:20:e0:d9
[  117.225524] eth2: Initial auth_alg=0
[  117.225527] eth2: authenticate with AP 00:11:50:20:e0:d9
[  117.421951] eth2: authenticate with AP 00:11:50:20:e0:d9
[  117.621678] eth2: authenticate with AP 00:11:50:20:e0:d9
[  117.821411] eth2: authentication with AP 00:11:50:20:e0:d9 timed out
[  118.162709] eth2: authentication frame received from 00:11:50:20:e0:d9, but not in authenticate state - ignored
[  118.266723] eth2: authentication frame received from 00:11:50:20:e0:d9, but not in authenticate state - ignored
[  118.286274] eth2: authentication frame received from 00:11:50:20:e0:d9, but not in authenticate state - ignored
[  118.306305] eth2: authentication frame received from 00:11:50:20:e0:d9, but not in authenticate state - ignored
[  118.307711] eth2: authentication frame received from 00:11:50:20:e0:d9, but not in authenticate state - ignored
[  118.325187] eth2: authentication frame received from 00:11:50:20:e0:d9, but not in authenticate state - ignored
[  118.326067] eth2: authentication frame received from 00:11:50:20:e0:d9, but not in authenticate state - ignored
[  128.827570] eth2: Initial auth_alg=0
[  128.827577] eth2: authenticate with AP 00:11:50:20:e0:d9
[  128.828961] eth2: Initial auth_alg=0
[  128.828965] eth2: authenticate with AP 00:11:50:20:e0:d9
[  129.026398] eth2: authenticate with AP 00:11:50:20:e0:d9
[  129.226131] eth2: authenticate with AP 00:11:50:20:e0:d9
[  129.425860] eth2: authentication with AP 00:11:50:20:e0:d9 timed out
[  140.425729] eth2: Initial auth_alg=0
[  140.425735] eth2: authenticate with AP 00:11:50:20:e0:d9
[  140.427159] eth2: Initial auth_alg=0
[  140.427164] eth2: authenticate with AP 00:11:50:20:e0:d9
[  140.626865] eth2: authenticate with AP 00:11:50:20:e0:d9
[  140.826588] eth2: authenticate with AP 00:11:50:20:e0:d9
[  141.026327] eth2: authentication with AP 00:11:50:20:e0:d9 timed out
[  152.043779] eth2: Initial auth_alg=0
[  152.043786] eth2: authenticate with AP 00:11:50:20:e0:d9
[  152.044610] eth2: Initial auth_alg=0
[  152.044614] eth2: authenticate with AP 00:11:50:20:e0:d9
[  152.243288] eth2: authenticate with AP 00:11:50:20:e0:d9
[  152.443019] eth2: authenticate with AP 00:11:50:20:e0:d9
[  152.642753] eth2: authentication with AP 00:11:50:20:e0:d9 timed out
[  163.660292] eth2: Initial auth_alg=0
[  163.660299] eth2: authenticate with AP 00:11:50:20:e0:d9
[  163.661928] eth2: Initial auth_alg=0
[  163.661932] eth2: authenticate with AP 00:11:50:20:e0:d9
[  163.859723] eth2: authenticate with AP 00:11:50:20:e0:d9
[  164.059456] eth2: authenticate with AP 00:11:50:20:e0:d9
[  164.259194] eth2: authentication with AP 00:11:50:20:e0:d9 timed out
[  170.452717] eth2: authentication frame received from 00:11:50:20:e0:d9, but not in authenticate state - ignored
[  175.278736] eth2: Initial auth_alg=0
[  175.278743] eth2: authenticate with AP 00:11:50:20:e0:d9
[  175.279621] eth2: Initial auth_alg=0
[  175.279626] eth2: authenticate with AP 00:11:50:20:e0:d9
[  175.476162] eth2: authenticate with AP 00:11:50:20:e0:d9
[  175.675890] eth2: authenticate with AP 00:11:50:20:e0:d9
[  175.875624] eth2: authentication with AP 00:11:50:20:e0:d9 timed out
[  186.894462] eth2: Initial auth_alg=0
[  186.894469] eth2: authenticate with AP 00:11:50:20:e0:d9
[  186.896546] eth2: Initial auth_alg=0
[  186.896551] eth2: authenticate with AP 00:11:50:20:e0:d9
[  187.092596] eth2: authenticate with AP 00:11:50:20:e0:d9
[  187.292333] eth2: authenticate with AP 00:11:50:20:e0:d9
[  187.492057] eth2: authentication with AP 00:11:50:20:e0:d9 timed out
[  203.756710] eth2: RX deauthentication from 00:11:50:20:e0:d9 (reason=2)
[  239.571982] eth2: authentication frame received from 00:11:50:20:e0:d9, but not in authenticate state - ignored
[  239.612754] eth2: authentication frame received from 00:11:50:20:e0:d9, but not in authenticate state - ignored
[  239.672168] eth2: authentication frame received from 00:11:50:20:e0:d9, but not in authenticate state - ignored
[  239.723415] eth2: authentication frame received from 00:11:50:20:e0:d9, but not in authenticate state - ignored
[  239.743962] eth2: authentication frame received from 00:11:50:20:e0:d9, but not in authenticate state - ignored
[  239.825698] eth2: authentication frame received from 00:11:50:20:e0:d9, but not in authenticate state - ignored
[  239.863306] eth2: authentication frame received from 00:11:50:20:e0:d9, but not in authenticate state - ignored
[  239.884417] eth2: authentication frame received from 00:11:50:20:e0:d9, but not in authenticate state - ignored
[  239.922412] eth2: authentication frame received from 00:11:50:20:e0:d9, but not in authenticate state - ignored
[  239.924873] eth2: authentication frame received from 00:11:50:20:e0:d9, but not in authenticate state - ignored
[  240.042641] eth2: authentication frame received from 00:11:50:20:e0:d9, but not in authenticate state - ignored
[  240.046536] eth2: authentication frame received from 00:11:50:20:e0:d9, but not in authenticate state - ignored
[  240.062616] eth2: authentication frame received from 00:11:50:20:e0:d9, but not in authenticate state - ignored
[  240.123934] eth2: authentication frame received from 00:11:50:20:e0:d9, but not in authenticate state - ignored
[  240.203401] eth2: authentication frame received from 00:11:50:20:e0:d9, but not in authenticate state - ignored
[  240.241214] eth2: authentication frame received from 00:11:50:20:e0:d9, but not in authenticate state - ignored
[  240.243519] eth2: authentication frame received from 00:11:50:20:e0:d9, but not in authenticate state - ignored
[  240.261168] eth2: authentication frame received from 00:11:50:20:e0:d9, but not in authenticate state - ignored
[  240.283586] eth2: authentication frame received from 00:11:50:20:e0:d9, but not in authenticate state - ignored
[  240.324226] eth2: authentication frame received from 00:11:50:20:e0:d9, but not in authenticate state - ignored
[  240.343021] eth2: authentication frame received from 00:11:50:20:e0:d9, but not in authenticate state - ignored
[  240.362792] eth2: authentication frame received from 00:11:50:20:e0:d9, but not in authenticate state - ignored
[  240.402940] eth2: authentication frame received from 00:11:50:20:e0:d9, but not in authenticate state - ignored
[  240.463428] eth2: authentication frame received from 00:11:50:20:e0:d9, but not in authenticate state - ignored
[  240.482369] eth2: authentication frame received from 00:11:50:20:e0:d9, but not in authenticate state - ignored
[  240.483917] eth2: authentication frame received from 00:11:50:20:e0:d9, but not in authenticate state - ignored
[  240.503021] eth2: authentication frame received from 00:11:50:20:e0:d9, but not in authenticate state - ignored
[  240.523387] eth2: authentication frame received from 00:11:50:20:e0:d9, but not in authenticate state - ignored
[  240.549704] eth2: authentication frame received from 00:11:50:20:e0:d9, but not in authenticate state - ignored
[  240.566779] eth2: authentication frame received from 00:11:50:20:e0:d9, but not in authenticate state - ignored
[  240.693551] eth2: authentication frame received from 00:11:50:20:e0:d9, but not in authenticate state - ignored
[  267.586543] eth2: authentication frame received from 00:11:50:20:e0:d9, but not in authenticate state - ignored
[  267.660416] eth2: authentication frame received from 00:11:50:20:e0:d9, but not in authenticate state - ignored
[  267.662995] eth2: authentication frame received from 00:11:50:20:e0:d9, but not in authenticate state - ignored
[  267.686504] eth2: authentication frame received from 00:11:50:20:e0:d9, but not in authenticate state - ignored
[  267.704885] eth2: authentication frame received from 00:11:50:20:e0:d9, but not in authenticate state - ignored
[  267.729407] eth2: authentication frame received from 00:11:50:20:e0:d9, but not in authenticate state - ignored
[  267.768546] eth2: authentication frame received from 00:11:50:20:e0:d9, but not in authenticate state - ignored
[  267.789043] eth2: authentication frame received from 00:11:50:20:e0:d9, but not in authenticate state - ignored
[  297.340900] ata1.01: qc timeout (cmd 0xa0)
[  297.340918] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[  297.340930] ata1.01: cmd a0/00:00:00:0c:00/00:00:00:00:00/b0 tag 0 pio 12 in
[  297.340932]          cdb 43 00 00 00 00 00 00 00  0c 00 00 00 00 00 00 00
[  297.340934]          res 51/20:03:00:00:00/00:00:00:00:00/b0 Emask 0x5 (timeout)
[  297.340938] ata1.01: status: { DRDY ERR }
[  302.378121] ata1: port is slow to respond, please be patient (Status 0xd1)
[  307.355452] ata1: device not ready (errno=-16), forcing hardreset
[  307.355460] ata1: soft resetting link
[  307.715639] ata1.00: configured for UDMA/100
[  307.903119] ata1.01: configured for UDMA/33
[  307.903142] ata1: EH complete
[  307.911162] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors (40008 MB)
[  307.919454] sd 0:0:0:0: [sda] Write Protect is off
[  307.919458] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  307.935132] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  307.951111] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors (40008 MB)
[  307.959999] sd 0:0:0:0: [sda] Write Protect is off
[  307.960003] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  307.976189] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  323.595828] eth2: RX deauthentication from 00:11:50:20:e0:d9 (reason=2)
[  647.903332] ata1.01: qc timeout (cmd 0xa0)
[  647.903349] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[  647.903361] ata1.01: cmd a0/00:00:00:00:00/00:00:00:00:00/b0 tag 0
[  647.903363]          cdb 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[  647.903364]          res 51/20:03:00:00:00/00:00:00:00:00/b0 Emask 0x5 (timeout)
[  647.903368] ata1.01: status: { DRDY ERR }
[  652.936391] ata1: port is slow to respond, please be patient (Status 0xd0)
[  657.913722] ata1: device not ready (errno=-16), forcing hardreset
[  657.913729] ata1: soft resetting link
[  658.273915] ata1.00: configured for UDMA/100
[  658.461388] ata1.01: configured for UDMA/33
[  658.461411] ata1: EH complete
[  658.463376] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors (40008 MB)
[  658.469452] sd 0:0:0:0: [sda] Write Protect is off
[  658.469456] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  658.486829] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  658.502369] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors (40008 MB)
[  658.510673] sd 0:0:0:0: [sda] Write Protect is off
[  658.510677] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  658.526259] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 2518.856180] usb 5-3: new high speed USB device using ehci_hcd and address 3
[ 2518.990735] usb 5-3: configuration #1 chosen from 1 choice
[ 2519.138061] usbcore: registered new interface driver libusual
[ 2519.199631] Initializing USB Mass Storage driver...
[ 2519.201922] scsi2 : SCSI emulation for USB Mass Storage devices
[ 2519.205173] usbcore: registered new interface driver usb-storage
[ 2519.205181] USB Mass Storage support registered.
[ 2519.206136] usb-storage: device found at 3
[ 2519.206140] usb-storage: waiting for device to settle before scanning
[ 2524.197210] usb-storage: device scan complete
[ 2524.198330] scsi 2:0:0:0: Direct-Access     Kingston DataTraveler 2.0 1.00 PQ: 0 ANSI: 2
[ 2524.200188] sd 2:0:0:0: [sdb] 1952768 512-byte hardware sectors (1000 MB)
[ 2524.201434] sd 2:0:0:0: [sdb] Write Protect is off
[ 2524.201439] sd 2:0:0:0: [sdb] Mode Sense: 23 00 00 00
[ 2524.201442] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[ 2524.205174] sd 2:0:0:0: [sdb] 1952768 512-byte hardware sectors (1000 MB)
[ 2524.206296] sd 2:0:0:0: [sdb] Write Protect is off
[ 2524.206301] sd 2:0:0:0: [sdb] Mode Sense: 23 00 00 00
[ 2524.206304] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[ 2524.207416]  sdb: sdb1
[ 2524.283935] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[ 2524.283983] sd 2:0:0:0: Attached scsi generic sg2 type 0
[ 2581.920661] usb 5-3: USB disconnect, address 3
tomlawell@Jessie-ubuntu:~$

---

### Post by ctsdownloads on 2008-04-30
I am no expert, but this seems a bit weird to me.

from dmesg:

> udev: renamed network interface wlan0 to eth2

Am I wrong on this folks?

Then an extra helping of;

> eth2: authentication frame received from 00:11:50:20:e0:d9, but not in authenticate state - ignored

Without a follow up of authenticated afterward, as with my own Intel 4965 wifi card where it is connecting fine.

Anyone have thoughts on this? Looks like an Intel 3945ABG device in his case.

---

### Post by thomasaaron on 2008-04-30
I'm not trying to be a weenie, here. But have you checked the simple stuff?
If you can SEE your wireless access point, your wireless card is fine. The silver switch should be all the way to the LEFT.

Can you connect to your wireless with another computer?

If you click the networking icon in the upper right of your monitor and select your own wireless access point and click it, does it ask you to enter your pass-phrase or anything like that?

All of our Darters here in the shop have wireless after upgrading, so I'm betting it is either a configuration with your router or with network manager.

NOTE: The wireless LED will not work in Hardy. It is a bug, and we are working on it, but it doesn't affect your ability to connect.

NOTE 2: Contact me at support(at)system76(dot)com to get instructions on upgrading your BIOS. The version you have will not allow you to adjust the brightness of your LCD with the FN-F5 and FN-F6 keys. Upgrading will fix that.

---

### Post by ctsdownloads on 2008-04-30
> **thomasaaron said:**
> I'm not trying to be a weenie, here. But have you checked the simple stuff?
If you can SEE your wireless access point, your wireless card is fine. The silver switch should be all the way to the LEFT.

Can you connect to your wireless with another computer?

If you click the networking icon in the upper right of your monitor and select your own wireless access point and click it, does it ask you to enter your pass-phrase or anything like that?

All of our Darters here in the shop have wireless after upgrading, so I'm betting it is either a configuration with your router or with network manager.

NOTE: The wireless LED will not work in Hardy. It is a bug, and we are working on it, but it doesn't affect your ability to connect.

NOTE 2: Contact me at support(at)system76(dot)com to get instructions on upgrading your BIOS. The version you have will not allow you to adjust the brightness of your LCD with the FN-F5 and FN-F6 keys. Upgrading will fix that.

Ah, that makes sense. I was working really hard at over complicating. ;)

But what is up with eth2? Why not stick with something like wlan0? Not that it matters, but it seems kinda of strange with newer Ubuntu releases? Please *edu-mu-cate* me. :)

---

### Post by thomasaaron on 2008-04-30
Yeah. That's a bit weird.

---

### Post by crichell on 2008-04-30
> **ctsdownloads said:**
> Ah, that makes sense. I was working really hard at over complicating. ;)

But what is up with eth2? Why not stick with something like wlan0?

renaming wlan cards comes from Ubuntu's switch to the iwl driver (rather than ipw).

---

### Post by TomLawell on 2008-04-30
I did check the simple stuff! I was working before the upgrade and of course during as I let the automatic updater do it's stuff. I am using the router with 2 other laptops (wireless) and two desktops (cat5).

Clicking the networking icon gives me a list of mine and neighbors' AP's. Click on mine causes the circling effect and then it stops with small x on icon. ( I am not using a passphase, I am controling MAC addresses.)

I did not make any switch changes after the upgrade. That is when it failed to connect.

Thanks all. 

Tom, I will update bios after this is solved.

---

### Post by thomasaaron on 2008-04-30
You need to check your Mac address settings, then, I think.
There was a post on the (now archived) forums very similar to this one.
I believe the change was in the routers Mac Address configurations.

---

### Post by TomLawell on 2008-04-30
Thanks, Tom but I turned off Router MAC control and firewall while troubleshooting this. I have reset the router and any other weinee thing I can think of. 

Thanks for the suggestion.

Tom L

---

### Post by crichell on 2008-04-30
Tom L,

/var/log/daemon.log is where network manager events are logged. In there we can see network manager start the device, attempt to authenticate, and hopefully the error.

You can watch what is happening by running the following command and then attempting to connect to your wireless access point:

```
tail -f /var/log/daemon.log
```

You can also run the following command to create a file on your desktop:

```
cat /var/log/daemon.log > ~/Desktop/daemon.log.txt
```

Attach the file and we'll have a look.

---

### Post by TomLawell on 2008-04-30
It sure looks like it is outside of my Darter, but I changed nothing and it didn't work after the reboot after upgrade.

Thanks for looking.

TomL

tomlawell@Jessie-ubuntu:~$ tail -f /var/log/daemon.log
Apr 30 17:30:45 Jessie-ubuntu NetworkManager: <info>  SUP: response was 'OK' 
Apr 30 17:30:45 Jessie-ubuntu NetworkManager: <info>  Activation (eth2) Stage 2 of 5 (Device Configure) complete. 
Apr 30 17:30:52 Jessie-ubuntu NetworkManager: <info>  Old device 'eth2' activating, won't change. 
Apr 30 17:31:30 Jessie-ubuntu last message repeated 3 times
Apr 30 17:32:38 Jessie-ubuntu last message repeated 5 times
Apr 30 17:32:45 Jessie-ubuntu NetworkManager: <info>  Activation (eth2/wireless): association took too long (>120s), failing activation. 
Apr 30 17:32:45 Jessie-ubuntu NetworkManager: <info>  Activation (eth2) failure scheduled... 
Apr 30 17:32:45 Jessie-ubuntu NetworkManager: <info>  Activation (eth2) failed for access point (Belkin_Pre-N_141142) 
Apr 30 17:32:45 Jessie-ubuntu NetworkManager: <info>  Activation (eth2) failed. 
Apr 30 17:32:45 Jessie-ubuntu NetworkManager: <info>  Deactivating device eth2. 
Apr 30 19:02:50 Jessie-ubuntu NetworkManager: <debug> [1209596570.059743] nm_device_802_11_wireless_get_activation_ap(): Forcing AP 'Belkin_Pre-N_141142' 
Apr 30 19:02:50 Jessie-ubuntu NetworkManager: <info>  User Switch: /org/freedesktop/NetworkManager/Devices/eth2 / Belkin_Pre-N_141142 
Apr 30 19:02:50 Jessie-ubuntu NetworkManager: <info>  Deactivating device eth2. 
Apr 30 19:02:50 Jessie-ubuntu NetworkManager: <info>  Device eth2 activation scheduled... 
Apr 30 19:02:50 Jessie-ubuntu NetworkManager: <info>  Activation (eth2) started... 
Apr 30 19:02:50 Jessie-ubuntu NetworkManager: <info>  Activation (eth2) Stage 1 of 5 (Device Prepare) scheduled... 
Apr 30 19:02:50 Jessie-ubuntu NetworkManager: <info>  Activation (eth2) Stage 1 of 5 (Device Prepare) started... 
Apr 30 19:02:50 Jessie-ubuntu NetworkManager: <info>  Activation (eth2) Stage 2 of 5 (Device Configure) scheduled... 
Apr 30 19:02:50 Jessie-ubuntu NetworkManager: <info>  Activation (eth2) Stage 1 of 5 (Device Prepare) complete. 
Apr 30 19:02:50 Jessie-ubuntu NetworkManager: <info>  Activation (eth2) Stage 2 of 5 (Device Configure) starting... 
Apr 30 19:02:50 Jessie-ubuntu NetworkManager: <info>  Activation (eth2/wireless): access point 'Belkin_Pre-N_141142' is unencrypted, no key needed. 
Apr 30 19:02:51 Jessie-ubuntu NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD eth2^I^Iwext^I/var/run/wpa_supplicant0^I' 
Apr 30 19:02:51 Jessie-ubuntu NetworkManager: <info>  SUP: response was 'OK' 
Apr 30 19:02:51 Jessie-ubuntu NetworkManager: <info>  SUP: sending command 'AP_SCAN 1' 
Apr 30 19:02:51 Jessie-ubuntu NetworkManager: <info>  SUP: response was 'OK' 
Apr 30 19:02:51 Jessie-ubuntu NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
Apr 30 19:02:51 Jessie-ubuntu NetworkManager: <info>  SUP: response was '0' 
Apr 30 19:02:51 Jessie-ubuntu NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 42656c6b696e5f5072652d4e5f313431313432' 
Apr 30 19:02:51 Jessie-ubuntu NetworkManager: <info>  SUP: response was 'OK' 
Apr 30 19:02:51 Jessie-ubuntu NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt NONE' 
Apr 30 19:02:51 Jessie-ubuntu NetworkManager: <info>  SUP: response was 'OK' 
Apr 30 19:02:51 Jessie-ubuntu NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
Apr 30 19:02:51 Jessie-ubuntu NetworkManager: <info>  SUP: response was 'OK' 
Apr 30 19:02:51 Jessie-ubuntu NetworkManager: <info>  Activation (eth2) Stage 2 of 5 (Device Configure) complete. 
Apr 30 19:02:58 Jessie-ubuntu NetworkManager: <info>  Old device 'eth2' activating, won't change. 
Apr 30 19:03:39 Jessie-ubuntu last message repeated 2 times
Apr 30 19:04:42 Jessie-ubuntu last message repeated 5 times
Apr 30 19:04:51 Jessie-ubuntu NetworkManager: <info>  Activation (eth2/wireless): association took too long (>120s), failing activation. 
Apr 30 19:04:51 Jessie-ubuntu NetworkManager: <info>  Activation (eth2) failure scheduled... 
Apr 30 19:04:51 Jessie-ubuntu NetworkManager: <info>  Activation (eth2) failed for access point (Belkin_Pre-N_141142) 
Apr 30 19:04:51 Jessie-ubuntu NetworkManager: <info>  Activation (eth2) failed. 
Apr 30 19:04:51 Jessie-ubuntu NetworkManager: <info>  Deactivating device eth2.

---

### Post by ctsdownloads on 2008-04-30
TomL, between Carl and the other Tom, they should be able to look at your logs and see what is going on. I am not sure myself, but I belive they will nail it for ya. ;)

---

### Post by thomasaaron on 2008-05-01
Sure sounds a lot like this:
[https://lists.ubuntu.com/archives/kernel-bugs/2008-February/032245.html](https://lists.ubuntu.com/archives/kernel-bugs/2008-February/032245.html)

I don't have an unencrypted network to test with at the moment.
Try setting up WPA and connecting.

---

### Post by TomLawell on 2008-05-01
You are right about the probable bug!

Using network settings manager and removing "Roaming mode enabled" which allows me to fill in the ESSID, password type, network password and configure to DHCP, I lose the wireless setting ability at the upper right icon.

I guess I do not know how to enable WEP.

Thanks again.

---

### Post by ethanay on 2008-05-01
hmm..re: the rename wlan0 to eth2 -- would that explain why when I suspend form resume, network manager sees and sets my wireless connection as a wired connection?

it's really weird.

disabling and re-enabling networking corrects the issue.

---

