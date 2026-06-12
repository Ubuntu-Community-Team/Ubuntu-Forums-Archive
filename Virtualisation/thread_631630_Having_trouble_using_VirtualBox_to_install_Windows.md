---
title: "Having trouble using VirtualBox to install Windows"
date: 2007-12-03
forum: Virtualisation
---

### Post by RadiationHazard on 2007-12-03
look at the screen shot?? :confused:

---

### Post by Dr Small on 2007-12-03
I do believe I had this error once, here:
[http://ubuntuforums.org/showthread.php?t=562395](http://ubuntuforums.org/showthread.php?t=562395)

Try reading this thread:
[http://ubuntuforums.org/showthread.php?t=555996](http://ubuntuforums.org/showthread.php?t=555996)

---

### Post by RadiationHazard on 2007-12-03
ok i'm still not getting it!! will someone pleaseee step by step me trough it on aim=jordansagansta or yahoo=jordansagangsta

---

### Post by Dr Small on 2007-12-03
> **RadiationHazard said:**
> ok i'm still not getting it!! will someone pleaseee step by step me trough it on aim=jordansagansta or yahoo=jordansagangsta
If you can get on IRC, stop by #ubuntuforums-beginners @ irc.freenode.net

---

### Post by RadiationHazard on 2007-12-04
I really need someones help!!!!!!!!!!! I tried all last night and couldn't seem to get it. pleaseee help me out:confused:

---

### Post by Paqman on 2007-12-04
I've not ever used Virtualbox, but from their website:

Go to System > Administration > Software Sources and add this repo:

deb [http://www.virtualbox.org/debian](http://www.virtualbox.org/debian) gutsy non-free

Save [this key](http://www.virtualbox.org/debian/innotek.asc) to your machine and add it (under "authentication")

Fire up Synaptic, hit reload, and you should be able to get virtualbox

---

### Post by Paqman on 2007-12-04
Actually, hang on. [This page](http://packages.ubuntu.com/gutsy/misc/virtualbox-ose) says it's in the universe repo for Gutsy. Do you have universe enabled?

---

### Post by RadiationHazard on 2007-12-04
i guess not cuz idk what you're talkin bout? i'm fairly new to linux...

---

### Post by forestpixie on 2007-12-04
I downloaded the deb file from their site - [http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

Installed that and then started it - then hit New and filled in the boxes as I needed - virtual os etc

Then start actually starts the virtual os - at that point it will need to have the os you want to run as virtual installed.

I also installed the guest additions which can make life a bit easier - it's in the devices tab of the virtual machine

And that was it - I've not bothered with usb support in there - but there are threads here documenting it.

---

### Post by Paqman on 2007-12-04
> **RadiationHazard said:**
> i guess not cuz idk what you're talkin bout? i'm fairly new to linux...

Ok, no probs. Everybody was a newbie once, even Linus Torvalds ;)

You might want to go to [this guide to Synaptic](https://help.ubuntu.com/community/Repositories/Ubuntu#head-5bbef89639d9a7d93fe38f6356dc17847d373096). Add the universe repository, reload Synaptic and try searching for Virtualbox again.

---

### Post by overdrank on 2007-12-04
HI and this may help you help the op. 
[http://ubuntuforums.org/showthread.php?t=630772](http://ubuntuforums.org/showthread.php?t=630772)
I believe DrSmall  linked the op to help with the error.

---

### Post by RadiationHazard on 2007-12-04
dude that's my post! HAHAHA!! It didn't help any i still haven't figured it out...

---

### Post by RadiationHazard on 2007-12-04
alright man well i'm using Ubuntu Gusty Gibbon 7.10 and do i have to like burn something to a disk? i think i might? i have the program installed but i can't actually get it to run...:confused:

---

### Post by forestpixie on 2007-12-04
OK back to basics what are you actually trying to achieve here

I'm assuming you've got ubuntu installed and want to run another os within ubuntu as a virtual?

Or have you got another os installed and want to run ubuntu within it as a virtual?

what do you think you have to burn?

If you have got ubuntu installed and you think v'box is installed - open a terminal (apps >accessories) and run virtualbox from there

```
VirtualBox
```

---

### Post by RadiationHazard on 2007-12-04
i'm trying to run windows on my linux

---

### Post by forestpixie on 2007-12-04
Ok screenshot helps - have tried doing as it asks

open aterminal 

```
sudo apt-cache search virtualbox*
```
will find all the relevant packages - one will look like this - virtualbox-ose-modules-2.6.22-14-generic

It's wanting you to install that, replace packagename with correct modules package

```
sudo apt-get install *packagename*
```

once that's installed do the other bit

```
sudo /etc/init.d/vboxdrv start
```

and try to start it again

---

### Post by aysiu on 2007-12-04
**Step 1**
[Enable extra repositories](http://www.psychocats.net/ubuntu/sources)

**Step 2**
Go to System > Administration > Synaptic Package Manager

**Step 3**
Search for *virtualbox*

**Step 4**
Right-click VirtualBox and mark it for installation

**Step 5**
Click *Apply*

---

### Post by RadiationHazard on 2007-12-04
:confused::confused::confused::confused::confused::confused::confused:

---

### Post by forestpixie on 2007-12-04
> replace packagename with correct modules package

```
sudo apt-get install virtualbox-ose-modules-2.6.22-14-generic
```

and then run this again

```
sudo /etc/init.d/vboxdrv start
```

you won't find many packages called *packagename* :)

---

### Post by RadiationHazard on 2007-12-04
Am i still doing something wrong?? I'm guessing I am....

---

### Post by forestpixie on 2007-12-04
did you install the virtualbox modules?

---

### Post by RadiationHazard on 2007-12-04
yes...i put a screen shot of what's going on below...

---

### Post by forestpixie on 2007-12-04
can you open aterminal and put these commands in enter after each and post the whole thing here for us please

```
sudo apt-get install virtualbox-ose-modules-2.6.22-14-generic
```

```
sudo /etc/init.d/vboxdrv start
```

---

### Post by RadiationHazard on 2007-12-04
?

---

### Post by forestpixie on 2007-12-04
OK - just wanted to make sure - last view of terminaldidn't have the module install on it.

 try running dmesg in terminal then and post that here - it'll likely be long so use Post Reply rather than Quick Reply, select all the text and click the # at the top of the message box - it'll put it in code.

I don't know that I'll be able to help anymore though - you're threads in the best place - Aysiu will prob pitch up again as he's already been here once.

Good luck - I'll look in tomorrow to see how you are doing

---

### Post by RadiationHazard on 2007-12-04
```
[   16.649368] PCI: Setting latency timer of device 0000:08:03.0 to 64
[   16.649379] NET: Registered protocol family 2
[   16.774020] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   16.774082] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
[   16.775142] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   16.775527] TCP: Hash tables configured (established 131072 bind 65536)
[   16.775530] TCP reno registered
[   16.814129] checking if image is initramfs... it is
[   17.445380] Freeing initrd memory: 6696k freed
[   17.445497] Simple Boot Flag at 0x36 set to 0x1
[   17.446049] audit: initializing netlink socket (disabled)
[   17.446066] audit(1196805301.760:1): initialized
[   17.446146] highmem bounce pool size: 64 pages
[   17.448239] VFS: Disk quotas dquot_6.5.1
[   17.448296] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   17.448394] io scheduler noop registered
[   17.448396] io scheduler anticipatory registered
[   17.448398] io scheduler deadline registered (default)
[   17.448413] io scheduler cfq registered
[   17.448430] Boot video device is 0000:00:02.0
[   17.448594] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   17.448653] assign_interrupt_mode Found MSI capability
[   17.448656] Allocate Port Service[0000:00:1c.0:pcie00]
[   17.448692] Allocate Port Service[0000:00:1c.0:pcie02]
[   17.448792] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   17.448850] assign_interrupt_mode Found MSI capability
[   17.448853] Allocate Port Service[0000:00:1c.1:pcie00]
[   17.448889] Allocate Port Service[0000:00:1c.1:pcie02]
[   17.448989] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   17.449047] assign_interrupt_mode Found MSI capability
[   17.449050] Allocate Port Service[0000:00:1c.2:pcie00]
[   17.449084] Allocate Port Service[0000:00:1c.2:pcie02]
[   17.449255] isapnp: Scanning for PnP cards...
[   17.805851] isapnp: No Plug & Play device found
[   17.829732] Real Time Clock Driver v1.12ac
[   17.829976] hpet_resources: 0xfed00000 is busy
[   17.830004] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   17.831180] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   17.831319] input: Macintosh mouse button emulation as /class/input/input0
[   17.831400] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   17.835937] i8042.c: Detected active multiplexing controller, rev 1.1.
[   17.840131] serio: i8042 KBD port at 0x60,0x64 irq 1
[   17.840136] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[   17.840140] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[   17.840143] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[   17.840145] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[   17.840291] mice: PS/2 mouse device common for all mice
[   17.840418] EISA: Probing bus 0 at eisa.0
[   17.840427] Cannot allocate resource for EISA slot 1
[   17.840430] Cannot allocate resource for EISA slot 2
[   17.840433] Cannot allocate resource for EISA slot 3
[   17.840436] Cannot allocate resource for EISA slot 4
[   17.840438] Cannot allocate resource for EISA slot 5
[   17.840457] EISA: Detected 0 cards.
[   17.840549] TCP cubic registered
[   17.840566] NET: Registered protocol family 1
[   17.840588] Using IPI No-Shortcut mode
[   17.840765]   Magic number: 3:456:954
[   17.840781]   hash matches device ttya9
[   17.840843]   hash matches device ptyzb
[   17.841137] Freeing unused kernel memory: 364k freed
[   18.043607] input: AT Translated Set 2 keyboard as /class/input/input1
[   18.116392] input: AT Translated Set 2 keyboard as /class/input/input2
[   19.063602] fuse init (API version 7.8)
[   19.068495] Capability LSM initialized
[   19.083460] ACPI: SSDT 3F69131A, 0282 (r1   Sony     VAIO 20061206 PTL  20050624)
[   19.083936] ACPI: SSDT 3F690DBF, 04C9 (r1   Sony     VAIO 20061206 PTL  20050624)
[   19.084359] ACPI: CPU0 (power states: C1[C1] C2[C2])
[   19.084363] ACPI: Processor [CPU0] (supports 8 throttling states)
[   19.093437] ACPI: SSDT 3F69159C, 00DD (r1   Sony     VAIO 20061206 PTL  20050624)
[   19.093640] ACPI: SSDT 3F691288, 0092 (r1   Sony     VAIO 20061206 PTL  20050624)
[   19.094131] ACPI: CPU1 (power states: C1[C1] C2[C2])
[   19.094135] ACPI: Processor [CPU1] (supports 8 throttling states)
[   19.096028] ACPI Exception (thermal-0400): AE_NOT_FOUND, Invalid active threshold [0] [20070126]
[    3.730000] Marking TSC unstable due to: possible TSC halt in C2.
[    3.730000] ACPI: Thermal Zone [TZ00] (21 C)
[    3.730000] ACPI Exception (thermal-0400): AE_NOT_FOUND, Invalid active threshold [0] [20070126]
[    3.730000] ACPI: Thermal Zone [TZ01] (21 C)
[    3.740000] Time: hpet clocksource has been installed.
[    4.170000] usbcore: registered new interface driver usbfs
[    4.170000] usbcore: registered new interface driver hub
[    4.170000] usbcore: registered new device driver usb
[    4.170000] USB Universal Host Controller Interface driver v3.0
[    4.170000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 19
[    4.170000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[    4.170000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    4.170000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[    4.170000] uhci_hcd 0000:00:1d.0: irq 19, io base 0x00001820
[    4.170000] usb usb1: configuration #1 chosen from 1 choice
[    4.170000] hub 1-0:1.0: USB hub found
[    4.170000] hub 1-0:1.0: 2 ports detected
[    4.280000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 17 (level, low) -> IRQ 16
[    4.280000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[    4.280000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    4.280000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[    4.280000] uhci_hcd 0000:00:1d.1: irq 16, io base 0x00001840
[    4.280000] usb usb2: configuration #1 chosen from 1 choice
[    4.280000] hub 2-0:1.0: USB hub found
[    4.280000] hub 2-0:1.0: 2 ports detected
[    4.280000] SCSI subsystem initialized
[    4.290000] libata version 2.21 loaded.
[    4.390000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[    4.390000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[    4.390000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    4.390000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[    4.390000] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00001860
[    4.390000] usb usb3: configuration #1 chosen from 1 choice
[    4.390000] hub 3-0:1.0: USB hub found
[    4.390000] hub 3-0:1.0: 2 ports detected
[    4.500000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 19
[    4.500000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    4.500000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    4.500000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
[    4.500000] ehci_hcd 0000:00:1d.7: debug port 1
[    4.500000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[    4.500000] ehci_hcd 0000:00:1d.7: irq 19, io mem 0xdc444000
[    4.500000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    4.500000] usb usb4: configuration #1 chosen from 1 choice
[    4.500000] hub 4-0:1.0: USB hub found
[    4.500000] hub 4-0:1.0: 6 ports detected
[    4.610000] ata_piix 0000:00:1f.1: version 2.11
[    4.610000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
[    4.610000] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[    4.610000] scsi0 : ata_piix
[    4.610000] scsi1 : ata_piix
[    4.610000] ata1: PATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x00011810 irq 14
[    4.610000] ata2: PATA max UDMA/133 cmd 0x00010170 ctl 0x00010376 bmdma 0x00011818 irq 15
[    4.950000] ata1.00: ATAPI: SONY    DVD RW AW-G540A, 1.74, max UDMA/33
[    5.150000] ata1.00: configured for UDMA/33
[    5.150000] ata2: port disabled. ignoring.
[    5.150000] scsi 0:0:0:0: CD-ROM            SONY     DVD RW AW-G540A  1.74 PQ: 0 ANSI: 5
[    5.150000] ata_piix 0000:00:1f.2: MAP [ P0 P2 XX XX ]
[    5.150000] ata_piix 0000:00:1f.2: invalid MAP value 0
[    5.310000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 20
[    5.310000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[    5.310000] scsi2 : ata_piix
[    5.310000] scsi3 : ata_piix
[    5.310000] ata3: SATA max UDMA/133 cmd 0x000118b0 ctl 0x000118a6 bmdma 0x00011890 irq 20
[    5.310000] ata4: SATA max UDMA/133 cmd 0x000118a8 ctl 0x000118a2 bmdma 0x00011898 irq 20
[    5.490000] ata3.00: ATA-8: FUJITSU MHW2120BH, 00000012, max UDMA/100
[    5.490000] ata3.00: 234441648 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    5.530000] ata3.00: configured for UDMA/100
[    5.690000] scsi 2:0:0:0: Direct-Access     ATA      FUJITSU MHW2120B 0000 PQ: 0 ANSI: 5
[    5.690000] PCI: Enabling device 0000:08:03.1 (0000 -> 0002)
[    5.690000] ACPI: PCI Interrupt 0000:08:03.1[A] -> GSI 16 (level, low) -> IRQ 17
[    5.690000] PCI: Setting latency timer of device 0000:08:03.1 to 64
[    5.740000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[17]  MMIO=[dc005000-dc0057ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    5.750000] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    5.750000] Uniform CD-ROM driver Revision: 3.20
[    5.750000] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    5.750000] sd 2:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[    5.750000] sd 2:0:0:0: [sda] Write Protect is off
[    5.750000] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.750000] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.750000] sd 2:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[    5.750000] sd 2:0:0:0: [sda] Write Protect is off
[    5.750000] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.750000] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.750000]  sda: sda1 sda2 <<5>sr 0:0:0:0: Attached scsi generic sg0 type 5
[    5.760000] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    5.820000]  sda5 >
[    5.820000] sd 2:0:0:0: [sda] Attached SCSI disk
[    6.070000] Attempting manual resume
[    6.070000] swsusp: Resume From Partition 8:5
[    6.070000] PM: Checking swsusp image.
[    6.070000] PM: Resume from disk failed.
[    6.080000] EXT3-fs: INFO: recovery required on readonly filesystem.
[    6.080000] EXT3-fs: write access will be enabled during recovery.
[    7.060000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[08004603023d44b7]
[   10.370000] kjournald starting.  Commit interval 5 seconds
[   10.370000] EXT3-fs: recovery complete.
[   10.370000] EXT3-fs: mounted filesystem with ordered data mode.
[   16.200000] Linux agpgart interface v0.102 (c) Dave Jones
[   16.200000] agpgart: Detected an Intel 945GM Chipset.
[   16.200000] agpgart: Detected 7932K stolen memory.
[   16.220000] agpgart: AGP aperture is 256M @ 0xc0000000
[   16.740000] iTCO_vendor_support: vendor-support=0
[   16.760000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   16.770000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   16.890000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (21-Jan-2007)
[   16.960000] PCI: Enabling device 0000:08:03.2 (0000 -> 0002)
[   16.960000] ACPI: PCI Interrupt 0000:08:03.2[C] -> GSI 18 (level, low) -> IRQ 18
[   16.960000] PCI: Setting latency timer of device 0000:08:03.2 to 64
[   17.000000] Yenta: CardBus bridge found at 0000:08:03.0 [104d:8212]
[   17.000000] Yenta: Enabling burst memory read transactions
[   17.000000] Yenta: Using CSCINT to route CSC interrupts to PCI
[   17.000000] Yenta: Routing CardBus interrupts to PCI
[   17.000000] Yenta TI: socket 0000:08:03.0, mfunc 0x01111b22, devctl 0x64
[   17.040000] input: PS/2 Mouse as /class/input/input3
[   17.060000] input: AlpsPS/2 ALPS GlidePoint as /class/input/input4
[   17.060000] iTCO_wdt: Found a ICH7-M TCO device (Version=2, TCOBASE=0x1060)
[   17.060000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   17.080000] intel_rng: FWH not detected
[   17.250000] Yenta: ISA IRQ mask 0x0cf8, PCI irq 17
[   17.250000] Socket status: 30000006
[   17.250000] Yenta: Raising subordinate bus# of parent bus (#08) from #09 to #0c
[   17.250000] pcmcia: parent PCI bridge I/O window: 0x5000 - 0x5fff
[   17.250000] cs: IO port probe 0x5000-0x5fff: clean.
[   17.250000] pcmcia: parent PCI bridge Memory window: 0xdc000000 - 0xdc0fffff
[   17.250000] pcmcia: parent PCI bridge Memory window: 0x50000000 - 0x53ffffff
[   17.250000] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 17
[   17.250000] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   17.250000] sky2 0000:02:00.0: v1.18 addr 0xd6000000 irq 17 Yukon-FE (0xb7) rev 1
[   17.250000] sky2 eth0: addr 00:13:a9:80:d7:62
[   17.570000] cs: IO port probe 0x100-0x3af: clean.
[   17.570000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   17.570000] cs: IO port probe 0x820-0x8ff: clean.
[   17.570000] cs: IO port probe 0xc00-0xcf7: clean.
[   17.570000] cs: IO port probe 0xa00-0xaff: clean.
[   17.740000] lp: driver loaded but no devices found
[   17.800000] Adding 3004112k swap on /dev/sda5.  Priority:-1 extents:1 across:3004112k
[   18.150000] EXT3 FS on sda1, internal journal
[   19.050000] ACPI: AC Adapter [ADP1] (on-line)
[   19.150000] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   19.170000] No dock devices found.
[   19.340000] ACPI: Battery Slot [BAT0] (battery present)
[   19.350000] input: Lid Switch as /class/input/input5
[   19.350000] ACPI: Lid Switch [LID0]
[   19.350000] input: Power Button (CM) as /class/input/input6
[   19.350000] ACPI: Power Button (CM) [PWRB]
[   20.600000] ppdev: user-space parallel port driver
[   20.730000] sky2 eth0: enabling interface
[   20.840000] apm: BIOS not found.
[   21.050000] sonypi: Sony Programmable I/O Controller Driver v1.26.
[   21.050000] sonypi: please try the sony-laptop module instead and report failures, see also [http://www.linux.it/~malattia/wiki/index.php/Sony_drivers](http://www.linux.it/~malattia/wiki/index.php/Sony_drivers)
[   21.050000] sonypi: detected type3 model, verbose = 0, fnkeyinit = off, camera = off, compat = off, mask = 0xffffffff, useinput = on, acpi = on
[   21.050000] sonypi: enabled at irq=11, port1=0x1080, port2=0x1084
[   21.050000] sonypi: device allocated minor is 63
[   21.050000] input: Sony Vaio Jogdial as /class/input/input7
[   21.050000] input: Sony Vaio Keys as /class/input/input8
[   21.100000] sonypi command failed at /build/buildd/linux-source-2.6.22-2.6.22/drivers/char/sonypi.c : sonypi_call1 (line 652)
[   21.140000] sonypi command failed at /build/buildd/linux-source-2.6.22-2.6.22/drivers/char/sonypi.c : sonypi_call2 (line 663)
[   21.180000] sonypi command failed at /build/buildd/linux-source-2.6.22-2.6.22/drivers/char/sonypi.c : sonypi_call2 (line 665)
[   21.220000] sonypi command failed at /build/buildd/linux-source-2.6.22-2.6.22/drivers/char/sonypi.c : sonypi_call1 (line 652)
[   21.250000] sony-laptop: Sony Notebook Control Driver v0.5.
[   21.250000] input: Sony Vaio Keys as /class/input/input9
[   21.250000] input: Sony Vaio Jogdial as /class/input/input10
[   21.480000] Capability LSM initialized
[   21.630000] Bluetooth: Core ver 2.11
[   21.630000] NET: Registered protocol family 31
[   21.630000] Bluetooth: HCI device and connection manager initialized
[   21.630000] Bluetooth: HCI socket layer initialized
[   21.640000] Bluetooth: L2CAP ver 2.8
[   21.640000] Bluetooth: L2CAP socket layer initialized
[   21.690000] Bluetooth: RFCOMM socket layer initialized
[   21.690000] Bluetooth: RFCOMM TTY layer initialized
[   21.690000] Bluetooth: RFCOMM ver 1.8
[   22.400000] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control rx
[   25.900000] [drm] Initialized drm 1.1.0 20060810
[   25.900000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 17
[   25.900000] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   26.580000] NET: Registered protocol family 17
[   37.310000] NET: Registered protocol family 10
[   37.310000] lo: Disabled Privacy Extensions
[   47.660000] eth0: no IPv6 routers present
[  492.450000] sky2 eth0: Link is down.
[  495.000000] Clocksource tsc unstable (delta = -338109854 ns)
[  749.160000] sky2 eth0: disabling interface
[  749.510000] ACPI: PCI interrupt for device 0000:02:00.0 disabled
[  751.080000] PM: suspend-to-disk mode set to 'shutdown'
[  751.080000] swsusp: Basic memory bitmaps created
[  751.080000] Stopping tasks ... done.
[  751.150000] Shrinking memory... done (75689 pages freed)
[  755.390000] Freed 302756 kbytes in 4.23 seconds (71.57 MB/s)
[  755.390000] Suspending console(s)
[  755.430000] sonypi command failed at /build/buildd/linux-source-2.6.22-2.6.22/drivers/char/sonypi.c : sonypi_call2 (line 663)
[  755.470000] sonypi command failed at /build/buildd/linux-source-2.6.22-2.6.22/drivers/char/sonypi.c : sonypi_call2 (line 665)
[  755.480000] sd 2:0:0:0: [sda] Synchronizing SCSI cache
[  755.480000] usb_device usbdev4.1: PM: suspend 0->1, parent usb4 already 2
[  755.480000] usb_endpoint usbdev4.1_ep81: PM: suspend 0->1, parent 4-0:1.0 already 2
[  755.480000] hub 4-0:1.0: PM: suspend 2->1, parent usb4 already 2
[  755.480000] usb_endpoint usbdev4.1_ep00: PM: suspend 0->1, parent usb4 already 2
[  755.480000] usb_device usbdev3.1: PM: suspend 0->1, parent usb3 already 2
[  755.480000] usb_endpoint usbdev3.1_ep81: PM: suspend 0->1, parent 3-0:1.0 already 2
[  755.480000] hub 3-0:1.0: PM: suspend 2->1, parent usb3 already 2
[  755.480000] usb_endpoint usbdev3.1_ep00: PM: suspend 0->1, parent usb3 already 2
[  755.480000] usb_device usbdev2.1: PM: suspend 0->1, parent usb2 already 2
[  755.480000] usb_endpoint usbdev2.1_ep81: PM: suspend 0->1, parent 2-0:1.0 already 2
[  755.480000] hub 2-0:1.0: PM: suspend 2->1, parent usb2 already 2
[  755.480000] usb_endpoint usbdev2.1_ep00: PM: suspend 0->1, parent usb2 already 2
[  755.480000] usb_device usbdev1.1: PM: suspend 0->1, parent usb1 already 2
[  755.480000] usb_endpoint usbdev1.1_ep81: PM: suspend 0->1, parent 1-0:1.0 already 2
[  755.480000] hub 1-0:1.0: PM: suspend 2->1, parent usb1 already 2
[  755.480000] usb_endpoint usbdev1.1_ep00: PM: suspend 0->1, parent usb1 already 2
[  755.480000] ACPI: PCI interrupt for device 0000:08:03.2 disabled
[  755.530000] ACPI: PCI interrupt for device 0000:00:1f.2 disabled
[  755.530000] ACPI: PCI interrupt for device 0000:00:1f.1 disabled
[  755.530000] ACPI: PCI interrupt for device 0000:00:1d.7 disabled
[  755.550000] ACPI: PCI interrupt for device 0000:00:1d.2 disabled
[  755.550000] ACPI: PCI interrupt for device 0000:00:1d.1 disabled
[  755.550000] ACPI: PCI interrupt for device 0000:00:1d.0 disabled
[  755.550000] Disabling non-boot CPUs ...
[  755.690000] CPU 1 is now offline
[  755.690000] SMP alternatives: switching to UP code
[  755.690000] CPU1 is down
[  755.690000] PM: snapshotting memory.
[  755.690000] swsusp: critical section: 
[  755.690000] swsusp: Need to copy 120108 pages
[  755.690000] swsusp: Normal pages needed: 105553 + 1024 + 24, available pages: 125058
[  755.690000] PM: Image restored successfully.
[  755.690000] Enabling non-boot CPUs ...
[  755.720000] SMP alternatives: switching to SMP code
[  755.720000] Booting processor 1/1 eip 3000
[  755.730000] Initializing CPU#1
[  755.880000] Calibrating delay using timer specific routine.. 3458.06 BogoMIPS (lpj=17290325)
[  755.880000] CPU: After generic identify, caps: bfe9fbff 00100000 00000000 00000000 0000c189 00000000 00000000
[  755.880000] monitor/mwait feature present.
[  755.880000] CPU: L1 I cache: 32K, L1 D cache: 32K
[  755.880000] CPU: L2 cache: 2048K
[  755.880000] CPU: Physical Processor ID: 0
[  755.880000] CPU: Processor Core ID: 1
[  755.880000] CPU: After all inits, caps: bfe9fbff 00100000 00000000 00002940 0000c189 00000000 00000000
[  755.880000] CPU1: Intel Genuine Intel(R) CPU           T2250  @ 1.73GHz stepping 08
[  755.880000] CPU1 is up
[  755.880000] Switched to high resolution mode on CPU 1
[  755.890000] sony-laptop: unable to restore brightness level<6>ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 17
[  755.910000] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[  755.910000] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[  755.910000] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[  755.910000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 19
[  755.910000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[  755.910000] usb usb1: root hub lost power or was reset
[  755.910000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 17 (level, low) -> IRQ 16
[  755.910000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[  755.910000] usb usb2: root hub lost power or was reset
[  755.910000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[  755.910000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[  755.910000] usb usb3: root hub lost power or was reset
[  755.930000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 19
[  755.930000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[  755.930000] usb usb4: root hub lost power or was reset
[  755.930000] ehci_hcd 0000:00:1d.7: debug port 1
[  755.930000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[  755.930000] PM: Writing back config space on device 0000:00:1e.0 at offset 6 (was 20090800, writing 200c0800)
[  755.930000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[  755.930000] PM: Writing back config space on device 0000:00:1f.1 at offset 1 (was 2880001, writing 2880005)
[  755.930000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 18 (level, low) -> IRQ 18
[  755.930000] PCI: Setting latency timer of device 0000:00:1f.1 to 64
[  755.930000] PM: Writing back config space on device 0000:00:1f.2 at offset 1 (was 2b00003, writing 2b00007)
[  755.930000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 20
[  755.930000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[  755.930000] PM: Writing back config space on device 0000:02:00.0 at offset 1 (was 40100007, writing 100003)
[  755.930000] PM: Writing back config space on device 0000:08:03.0 at offset f (was 34001ff, writing 5c001ff)
[  755.930000] PM: Writing back config space on device 0000:08:03.0 at offset 3 (was 824000, writing 82a820)
[  755.930000] ata2: port disabled. ignoring.
[  755.950000] PM: Writing back config space on device 0000:08:03.1 at offset f (was 4030100, writing 4030107)
[  755.950000] PM: Writing back config space on device 0000:08:03.1 at offset 5 (was 0, writing dc000000)
[  755.950000] PM: Writing back config space on device 0000:08:03.1 at offset 4 (was 0, writing dc005000)
[  755.950000] PM: Writing back config space on device 0000:08:03.1 at offset 3 (was 800000, writing 804000)
[  755.950000] PM: Writing back config space on device 0000:08:03.1 at offset 1 (was 2100000, writing 2100006)
[  756.000000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[17]  MMIO=[dc005000-dc0057ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[  756.020000] PM: Writing back config space on device 0000:08:03.2 at offset 3 (was 800000, writing 804000)
[  756.020000] PM: Writing back config space on device 0000:08:03.2 at offset 1 (was 2100000, writing 2100006)
[  756.020000] ACPI: PCI Interrupt 0000:08:03.2[C] -> GSI 18 (level, low) -> IRQ 18
[  756.170000] ata3.00: configured for UDMA/100
[  756.170000] sd 2:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[  756.170000] sd 2:0:0:0: [sda] Write Protect is off
[  756.170000] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[  756.170000] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[  756.530000] sd 2:0:0:0: [sda] Starting disk
[  756.600000] sonypi command failed at /build/buildd/linux-source-2.6.22-2.6.22/drivers/char/sonypi.c : sonypi_call1 (line 652)
[  756.640000] sonypi command failed at /build/buildd/linux-source-2.6.22-2.6.22/drivers/char/sonypi.c : sonypi_call2 (line 663)
[  756.660000] ata1.00: configured for UDMA/33
[  756.680000] sonypi command failed at /build/buildd/linux-source-2.6.22-2.6.22/drivers/char/sonypi.c : sonypi_call2 (line 665)
[  756.720000] sonypi command failed at /build/buildd/linux-source-2.6.22-2.6.22/drivers/char/sonypi.c : sonypi_call1 (line 652)
[  756.720000] Restarting tasks ... done.
[  756.740000] swsusp: Basic memory bitmaps freed
[  759.010000] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 17
[  759.010000] PCI: Setting latency timer of device 0000:02:00.0 to 64
[  759.010000] sky2 0000:02:00.0: v1.18 addr 0xd6000000 irq 17 Yukon-FE (0xb7) rev 1
[  759.010000] sky2 eth0: addr 00:13:a9:80:d7:62
[  759.070000] sky2 eth0: enabling interface
[  759.080000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  759.650000] input: Lid Switch as /class/input/input11
[  759.650000] ACPI: Lid Switch [LID0]
[  759.650000] input: Power Button (CM) as /class/input/input12
[  759.650000] ACPI: Power Button (CM) [PWRB]
[  759.740000] ACPI Exception (thermal-0400): AE_NOT_FOUND, Invalid active threshold [0] [20070126]
[  759.740000] ACPI: Thermal Zone [TZ00] (32 C)
[  759.740000] ACPI Exception (thermal-0400): AE_NOT_FOUND, Invalid active threshold [0] [20070126]
[  759.750000] ACPI: Thermal Zone [TZ01] (32 C)
[  759.820000] ACPI: AC Adapter [ADP1] (on-line)
[  759.920000] ACPI: Battery Slot [BAT0] (battery present)
[  760.740000] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control rx
[  760.740000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  775.280000] eth0: no IPv6 routers present
[ 1020.170000] sky2 eth0: disabling interface
[ 1020.250000] sky2 eth0: enabling interface
[ 1020.250000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 1021.950000] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control rx
[ 1021.950000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 1040.170000] eth0: no IPv6 routers present
[ 3276.960000] sr0: CDROM not ready.  Make sure there is a disc in the drive.
[ 3935.780000] sky2 eth0: Link is down.
[ 3948.130000] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control rx
[ 3948.130000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 3955.850000] sky2 eth0: Link is down.
[ 3958.080000] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control rx
[ 3958.090000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 3975.540000] sky2 eth0: Link is down.
[ 3975.910000] eth0: no IPv6 routers present
[ 4449.580000] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control rx
[ 4449.590000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 4457.330000] sky2 eth0: Link is down.
[ 4459.580000] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control rx
[ 4459.580000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 4477.180000] eth0: no IPv6 routers present
jordan@jordan-laptop:~$
```

---

### Post by aysiu on 2007-12-04
> **forestpixie said:**
> 
I don't know that I'll be able to help anymore though - you're threads in the best place - Aysiu will prob pitch up again as he's already been here once. Unless there's something wrong with RadiationHazard's installation, the following steps should get VirtualBox up and running.

[Make sure you have extra repositories enabled](http://www.psychocats.net/ubuntu/sources). It looks as though you already do, though.

[[IMG]http://img475.imageshack.us/img475/6716/virtualbox1or2.th.png[/IMG]](http://img475.imageshack.us/my.php?image=virtualbox1or2.png)
Go to System > Administration > Synaptic Package Manager

[[IMG]http://img464.imageshack.us/img464/1539/virtualbox2rx3.th.png[/IMG]](http://img464.imageshack.us/my.php?image=virtualbox2rx3.png)
In Synaptic, click *Search* and search for *virtualbox*

[[IMG]http://img528.imageshack.us/img528/3084/virtualbox3iv8.th.png[/IMG]](http://img528.imageshack.us/my.php?image=virtualbox3iv8.png)
Mark VirtualBox for installation by right-clicking it. When prompted, click *Mark*

[[IMG]http://img475.imageshack.us/img475/2553/virtualbox5hh7.th.png[/IMG]](http://img475.imageshack.us/my.php?image=virtualbox5hh7.png)
Click *Apply* and click *Apply* again

[[IMG]http://img516.imageshack.us/img516/9549/virtualbox8wp3.th.png[/IMG]](http://img516.imageshack.us/my.php?image=virtualbox8wp3.png)
Wait for the installation packages to download and wait for the packages to be installed

[[IMG]http://img475.imageshack.us/img475/2456/virtualbox9pm7.th.png[/IMG]](http://img475.imageshack.us/my.php?image=virtualbox9pm7.png)
Quit Synaptic

[[IMG]http://img516.imageshack.us/img516/1750/virtualbox10gl7.th.png[/IMG]](http://img516.imageshack.us/my.php?image=virtualbox10gl7.png)
Go to Applications > System Tools > Innotek VirtualBox

[[IMG]http://img526.imageshack.us/img526/7820/virtualbox11ro0.th.png[/IMG]](http://img526.imageshack.us/my.php?image=virtualbox11ro0.png)
VirtualBox should launch

---

### Post by gb64 on 2007-12-04
After all this discussion, I hate to point out that Paqman in post #2 gave the precise instructions which should have been followed. The user is attempting to use the ose version which is limited and older, whereas the instructions posted in post#2 would have downloaded the latest full version virtualbox_1.5.2-25433_Ubuntu_gutsy_i386.deb. I installed it within Synaptic with no problem at all.
Secondly, I hope you can assign more memory to Vista than you are showing, as you may find slowness problems. I use 786MB.

---

### Post by aysiu on 2007-12-04
> **gb64 said:**
> After all this discussion, I hate to point out that Paqman in post #2 gave the precise instructions which should have been followed. The user is attempting to use the ose version which is limited and older, whereas the instructions posted in post#2 would have downloaded the latest full version virtualbox_1.5.2-25433_Ubuntu_gutsy_i386.deb. I installed it within Synaptic with no problem at all.
Secondly, I hope you can assign more memory to Vista than you are showing, as you may find slowness problems. I use 786MB.
Well my instructions also work, and those use the Universe repositories and not the VirtualBox repositories.

Synaptic either way.

---

### Post by RadiationHazard on 2007-12-04
ok guy...idk how to explain it but you all keep telling me the same things and they just don't work. i have virtualbox already on my computer. so since you guys don't seem to know what i'm doing i'll show you what i'm doing step by step till i reach the problem

---

### Post by RadiationHazard on 2007-12-04
here are 5 more...

---

### Post by RadiationHazard on 2007-12-04
5 more...

---

### Post by RadiationHazard on 2007-12-04
One More...:confused:

---

### Post by aysiu on 2007-12-04
So you already have it installed, and it appears to be working fine.

What's the problem?

---

### Post by RadiationHazard on 2007-12-04
look at the last screen shot. that stupid error keeps popping up!!

---

### Post by gb64 on 2007-12-04
Did you set yourself up as a user in the group vboxusers?
Go to User management and check if you are enrolled as a member.
When you installed the ose version did it set you as a user?
The latest full version I installed did that for me as the last thing.
Also, I notice there are modules listed for the ose in the repository.
Did it install those modules for you? The full version made for v7.10  also does that automatically.

---

### Post by RadiationHazard on 2007-12-04
yes i did. and i'm freaking out!! it shouldn't be this freaking hard!!!!! i've tried for hours now just to get this

---

### Post by gb64 on 2007-12-04
You might uninstall the ose, then put virtualbox repository and add the innotek.asc to the authorization page of Synaptic, reload, and make sure you download the latest 1.5.2 package. Let Synaptic install it, then retry.
I think the USB is limited or not there in the ose. 

Also, Vista is not going to  install the right networking driver at first. You will have to check out the VirtualBox site for possible workaround within Vista guest.

---

### Post by RadiationHazard on 2007-12-04
Ok here are some screen shots of me doing the user thing. am i doing it right??

---

### Post by RadiationHazard on 2007-12-04
somebody help me on aim?? if you get it working i'll post what we did on here then everyone's happy!!

---

### Post by gb64 on 2007-12-04
Take a look at this thread in the VirtualBox forums, just in case....
[http://forums.virtualbox.org/viewtopic.php?t=2834](http://forums.virtualbox.org/viewtopic.php?t=2834)

---

### Post by aysiu on 2007-12-04
Maybe [this](https://answers.launchpad.net/ubuntu/+question/17462) might help.

---

### Post by RadiationHazard on 2007-12-05
Ok I already have VirtualBox but i don't guess anyone can help me with that so maybe I should try VMWare? Pleasee someone help me get this nightmare over with!!!:(

---

### Post by Curdsy on 2007-12-05
Can you tell me which OS you are using and which version?

---

### Post by Curdsy on 2007-12-05
Ok if you are running Ubuntu 7.10 you should have VirtualBox OSE in the Universe repository.
If you haven't already you need to install VirtualBox. I find the easiest way is to open a terminal and type:

sudo apt-get install virtualbox

Once you have gone through the install process you will need to add yourself (and any other users who will want to use the Virtual Machine) to the vboxusers group.

You can do this by going to the System menu on the panel. Then go to System->Administration->Users and Groups
From there go to Manage Groups and near the bottom will be a group called vboxusers.
Select properties and ensure you are a member of the group.

If you need any help beyond this stage please reply to this post. :)

---

### Post by bodhi.zazen on 2007-12-05
After you add yourself to the vboxusers group you need to LOG OUT and then log back in for the changes to take effect.

Otherwise , please post error messages.

@Curdsy : It depends on which version you install from what repo.

To install from the Ubuntu repo :

sudo apt-get install virtualbox-ose

---

### Post by irv on 2008-01-02
I started out with a working virtualbox-ose but had a problem with USB drives when running XP. Everything else worked. After reading through this thread, I un-installed virtualbox-ose and installed virtualbox. But I don't have the foggiest idea how to start it. It doesn't put anything in Applications. If I do a search for virtualbox, it wants to install the -ose again. How do I start virtualbox once I have it installed?

---

### Post by irv on 2008-01-02
> **irv said:**
> I started out with a working virtualbox-ose but had a problem with USB drives when running XP. Everything else worked. After reading through this thread, I un-installed virtualbox-ose and installed virtualbox. But I don't have the foggiest idea how to start it. It doesn't put anything in Applications. If I do a search for virtualbox, it wants to install the -ose again. How do I start virtualbox once I have it installed?

After Rebooting everything works find again. Still no USB support. I will have to work on this one problem.

---

### Post by Arkaniad on 2008-01-02
> **RadiationHazard said:**
> look at the screen shot?? :confused:
You're running mac OSX? Because if you are , You can download Microsoft VirtualPC on their website i believe, and follow this guide, which im pretty sure you need the i8042.noloop or whatever command to boot the kernel & installer.

[http://arcanecode.wordpress.com/2007/10/18/installing-ubuntu-710-under-virtual-pc-2007/](http://arcanecode.wordpress.com/2007/10/18/installing-ubuntu-710-under-virtual-pc-2007/)

Its a bit difficult, but with VPC07 (or the mac version) You can run almost any OS.

---

