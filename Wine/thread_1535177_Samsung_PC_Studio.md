---
title: "Samsung PC Studio"
date: 2010-07-20
forum: Wine
---

### Post by Tony.B on 2010-07-20
[FONT="Trebuchet MS"]I've got into a bit of a muddle (again):

I'm trying to install Samsung's PC Studio 3.2.2 so that I can transfer some photos from my cellphone to my laptop.

The CD supplied with the phone is (of course) compatible with Windows 2000, Windows XP & Windows Vista, but not with Ubuntu 10.04.

First I tried googling for assistance, but I couldn't find anything on the internet that would assist me.  Neither could I find anything on this forum.

Then I remembered from other posts on this forum that there's something called Wine that's designed to overcome installation problems like this.  So I found Wine in the Software Manager.  Actually there were lots of things called Wine, but I installed the one that was labelled 1.1.42.

I put in the Samsung disc again, but nothing happened.

At that point I chickened out, and I've removed the Wine installation just in case I was messing things up.  There seemed to be another two Wine files there, which I assumed were associated with 1.1.42, so I uninstalled them too.

I'm sorry to trouble you people again, but has anybody any idea how I can transfer my photos from my phone to my laptop?

Thanks,
Tony[/FONT]

---

### Post by asdfoo on 2010-07-22
> **Tony.B said:**
> [FONT="Trebuchet MS"]I've got into a bit of a muddle (again):

I'm trying to install Samsung's PC Studio 3.2.2 so that I can transfer some photos from my cellphone to my laptop.

The CD supplied with the phone is (of course) compatible with Windows 2000, Windows XP & Windows Vista, but not with Ubuntu 10.04.

First I tried googling for assistance, but I couldn't find anything on the internet that would assist me.  Neither could I find anything on this forum.

Then I remembered from other posts on this forum that there's something called Wine that's designed to overcome installation problems like this.  So I found Wine in the Software Manager.  Actually there were lots of things called Wine, but I installed the one that was labelled 1.1.42.

I put in the Samsung disc again, but nothing happened.

At that point I chickened out, and I've removed the Wine installation just in case I was messing things up.  There seemed to be another two Wine files there, which I assumed were associated with 1.1.42, so I uninstalled them too.

I'm sorry to trouble you people again, but has anybody any idea how I can transfer my photos from my phone to my laptop?

Thanks,
Tony[/FONT]


When you connect your cell phone, does it show up in ubuntu as a usb drive?  If it does, then you may find the photos on it directly.

---

### Post by Tony.B on 2010-07-22
[FONT="Trebuchet MS"]Hello asdfoo,

When I connect my cellphone, nothing at all seems to happen. Is there any way I can display USB port connections?

Thanks,
Tony
[/FONT]

---

### Post by asdfoo on 2010-07-22
connect the device, open a terminal and type dmesg
it will print a list of diagnostic messages relating to hardware activity, you can copy and paste the last 15 lines or so here

---

### Post by Tony.B on 2010-07-22
[FONT="Trebuchet MS"]Thanks for the reply, asdfoo.

When I typed dmesg, I got tons of output. Here are the last 20 lines:[/FONT]
```
  22.304636] Registered led device: ath5k-phy0::tx
[   22.304640] ath5k phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
[   22.400435] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   23.530748] ppdev: user-space parallel port driver
[  190.894117] wlan0: deauthenticating from 00:8b:5d:84:a5:8a by local choice (reason=3)
[  190.899009] wlan0: direct probe to AP 00:8b:5d:84:a5:8a (try 1)
[  190.902030] wlan0: direct probe responded
[  190.902033] wlan0: authenticate with AP 00:8b:5d:84:a5:8a (try 1)
[  190.904181] wlan0: authenticated
[  190.904199] wlan0: associate with AP 00:8b:5d:84:a5:8a (try 1)
[  190.906946] wlan0: RX AssocResp from 00:8b:5d:84:a5:8a (capab=0x431 status=0 aid=1)
[  190.906948] wlan0: associated
[  190.907582] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  190.947164] padlock: VIA PadLock not detected.
[  200.936049] wlan0: no IPv6 routers present
[  300.232092] usb 5-1: new full speed USB device using uhci_hcd and address 2
[  300.404413] usb 5-1: configuration #3 chosen from 1 choice
[  300.475097] cdc_acm 5-1:3.1: ttyACM0: USB ACM device
[  300.477512] usbcore: registered new interface driver cdc_acm
[  300.478260] cdc_acm: v0.26:USB Abstract Control Model driver for USB modems and ISDN adapters

```
[FONT="Trebuchet MS"]I hope this means more to you than it does to me!
Regards,
Tony[/FONT]

---

### Post by asdfoo on 2010-07-22
> **Tony.B said:**
> [FONT="Trebuchet MS"]Thanks for the reply, asdfoo.

When I typed dmesg, I got tons of output. Here are the last 20 lines:[/FONT]
```
  22.304636] Registered led device: ath5k-phy0::tx
[  300.232092] usb 5-1: new full speed USB device using uhci_hcd and address 2
[  300.404413] usb 5-1: configuration #3 chosen from 1 choice
[  300.475097] cdc_acm 5-1:3.1: ttyACM0: USB ACM device
[  300.477512] usbcore: registered new interface driver cdc_acm
[  300.478260] cdc_acm: v0.26:USB Abstract Control Model driver for USB modems and ISDN adapters

```
[FONT="Trebuchet MS"]I hope this means more to you than it does to me!
Regards,
Tony[/FONT]

No such luck it seems it only recognizes it as a modem for dialing, but not as a "storage device".  Is there any menu on your phone which mentions USB and lets you select a file transfer mode?  (just a wild guess)

Otherwise, it's possible that the software may dial some secret code over the modem line to "wake up" the storage device driver on the phone.  


The problem with trying to run your software in Wine is that USB support is not yet in Wine to the point where things like this might work.  You may have to look at linux only options.

---

### Post by Tony.B on 2010-07-22
> **asdfoo said:**
> No such luck it seems it only recognizes it as a modem for dialing, but not as a "storage device".  Is there any menu on your phone which mentions USB and lets you select a file transfer mode? 
[FONT="Trebuchet MS"]Unfortunately no.
[/FONT]

> **asdfoo said:**
> Otherwise, it's possible that the software may dial some secret code over the modem line to "wake up" the storage device driver on the phone.  


The problem with trying to run your software in Wine is that USB support is not yet in Wine to the point where things like this might work.  You may have to look at linux only options.
[FONT="Trebuchet MS"]Oh dear. Never mind.
Thanks for your help.
Cheers,
Tony[/FONT]

---

### Post by Trin Calway on 2010-09-11
I have gone around and around on this and it has been driving me crazy! I even tried different Linux Distros (I have Mint 9 right now)

I FINALLY got it to work. I have a Samsung SGH-a877. It is not recognized in either PC Studio or USB mode but for some reason if you connect it as **Media Player** it will work - you just need to specify to open with folder instead of RythymBox (or whatever your default player is).

I hope this works for you too!

Also PC Studio just does not work in Wine in fact it doesn't really work very well in Windows. LOL

---

### Post by Tony.B on 2010-09-11
Thank you for taking the trouble to reply, Trin. I got quite excited, found the connecting cable, plugged it in, selected **Media Player** and waited .... for an error message reading:

[CENTER]**Unable to mount SAMSUNG MTP Device**
Error initialising camera: -1:Unspecified Error[/CENTER]

The only option it gave me was to press the _O_K button which made the error message disappear.

But thanks for the thought and I'm glad it worked for you.  For now I'll have to struggle on without it!

---

### Post by Trin Calway on 2010-09-11
What Samsung phone do ya have? Also can we have a quick dmesg with it plugged in as Media Player?

---

### Post by Tony.B on 2010-09-12
Hello Trin,
> **Trin Calway said:**
> What Samsung phone do ya have?
It's a Samsung L700

> **Trin Calway said:**
> Also can we have a quick dmesg with it plugged in as Media Player?
I'm sorry I don't understand your question. I really am fairly clueless about these things (but learning fast).

I had originally posted this thread under **Absolute Beginner Talk**, but the moderators, in their absolute wisdom, have moved it.

Can you explain what "dmesg" is, please?

---

### Post by lymphor on 2010-09-20
> **Tony.B said:**
> 
Can you explain what "dmesg" is, please?

What Trin Calway meant to say is that you have to open the terminal and type **dmesg** in it having your phone plugged in as Media Player. After that copy-paste here the messages you get in the terminal.
Good luck!

(by the way I have a Samsung j700i: it worked for a while with Wammu, but at a certain point it just didn't anymore. So I installed Windows with VirtualBox and that way I was able to use Samsung PC Studio in it)

---

### Post by Tony.B on 2010-09-22
Thanks for the help, lymphor

> **lymphor said:**
> .... you have to open the terminal and type **dmesg** in it having your phone plugged in as Media Player. After that copy-paste here the messages you get in the terminal.
Good luck!

Here is the output after typing **dmesg** in the terminal:
```
[    0.214036] pci 0000:00:1f.3: reg 20 io port: [0x5000-0x501f]
[    0.214257] pci 0000:00:1c.0: bridge io port: [0x4000-0x4fff]
[    0.214262] pci 0000:00:1c.0: bridge 32bit mmio: [0x57300000-0x582fffff]
[    0.214289] pci 0000:00:1c.0: bridge 64bit mmio pref: [0x50000000-0x50ffffff]
[    0.214427] pci 0000:00:1c.1: bridge io port: [0x3000-0x3fff]
[    0.214450] pci 0000:00:1c.1: bridge 32bit mmio: [0x56300000-0x572fffff]
[    0.214459] pci 0000:00:1c.1: bridge 64bit mmio pref: [0x51000000-0x51ffffff]
[    0.214908] pci 0000:05:00.0: reg 10 64bit mmio: [0x55200000-0x5520ffff]
[    0.215426] pci 0000:05:00.0: PME# supported from D3hot D3cold
[    0.215437] pci 0000:05:00.0: PME# disabled
[    0.215669] pci 0000:00:1c.2: bridge io port: [0x2000-0x2fff]
[    0.215692] pci 0000:00:1c.2: bridge 32bit mmio: [0x55200000-0x562fffff]
[    0.215701] pci 0000:00:1c.2: bridge 64bit mmio pref: [0x52000000-0x52ffffff]
[    0.215885] pci 0000:06:00.0: reg 10 64bit mmio: [0x54100000-0x5410ffff]
[    0.216296] pci 0000:00:1c.3: bridge io port: [0x1000-0x1fff]
[    0.216301] pci 0000:00:1c.3: bridge 32bit mmio: [0x54100000-0x551fffff]
[    0.216328] pci 0000:00:1c.3: bridge 64bit mmio pref: [0x53000000-0x53ffffff]
[    0.216489] pci 0000:00:1e.0: transparent bridge
[    0.216590] pci_bus 0000:00: on NUMA node 0
[    0.216613] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.217063] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P32_._PRT]
[    0.217313] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP2._PRT]
[    0.217505] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP3._PRT]
[    0.217697] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.EXP4._PRT]
[    0.218174] ACPI Warning for \_SB_.PCI0._OSC: Parameter count mismatch - ASL declared 5, ACPI requires 4 (20090903/nspredef-336)
[    0.237185] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 10 *11 12)
[    0.237495] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 9 10 *11 12)
[    0.237783] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 9 10 *11 12)
[    0.238072] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 10 *11 12)
[    0.238360] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 11 12) *0, disabled.
[    0.238648] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 *10 11 12)
[    0.238939] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 9 10 *11 12)
[    0.239227] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 7 9 10 *11 12)
[    0.239506] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.239515] vgaarb: loaded
[    0.239797] SCSI subsystem initialized
[    0.239926] libata version 3.00 loaded.
[    0.240072] usbcore: registered new interface driver usbfs
[    0.240101] usbcore: registered new interface driver hub
[    0.240160] usbcore: registered new device driver usb
[    0.240546] ACPI: WMI: Mapper loaded
[    0.240548] PCI: Using ACPI for IRQ routing
[    0.241029] NetLabel: Initializing
[    0.241031] NetLabel:  domain hash size = 128
[    0.241033] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.241063] NetLabel:  unlabeled traffic allowed by default
[    0.241134] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.241157] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.244030] Switching to clocksource tsc
[    0.248244] AppArmor: AppArmor Filesystem Enabled
[    0.248276] pnp: PnP ACPI init
[    0.248331] ACPI: bus type pnp registered
[    0.250884] pnp 00:01: io resource (0x164e-0x164f) overlaps 0000:00:1c.3 BAR 13 (0x1000-0x1fff), disabling
[    0.272468] pnp: PnP ACPI: found 9 devices
[    0.272489] ACPI: ACPI bus type pnp unregistered
[    0.272492] PnPBIOS: Disabled by ACPI PNP
[    0.272523] system 00:01: ioport range 0x600-0x60f has been reserved
[    0.272526] system 00:01: ioport range 0x610-0x610 has been reserved
[    0.272529] system 00:01: ioport range 0x800-0x80f has been reserved
[    0.272532] system 00:01: ioport range 0x810-0x817 has been reserved
[    0.272552] system 00:01: ioport range 0x400-0x47f has been reserved
[    0.272555] system 00:01: ioport range 0x500-0x53f has been reserved
[    0.272558] system 00:01: ioport range 0xff2c-0xff2f has been reserved
[    0.272562] system 00:01: iomem range 0xe0000000-0xefffffff has been reserved
[    0.272583] system 00:01: iomem range 0xfed1c000-0xfed1ffff has been reserved
[    0.272586] system 00:01: iomem range 0xfed14000-0xfed17fff has been reserved
[    0.272589] system 00:01: iomem range 0xfed18000-0xfed18fff has been reserved
[    0.272592] system 00:01: iomem range 0xfed19000-0xfed19fff has been reserved
[    0.272595] system 00:01: iomem range 0xfec00000-0xfec00fff could not be reserved
[    0.272616] system 00:01: iomem range 0xfee00000-0xfee00fff has been reserved
[    0.272619] system 00:01: iomem range 0x32000000-0x320000ff could not be reserved
[    0.307746] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:02
[    0.307750] pci 0000:00:1c.0:   IO window: 0x4000-0x4fff
[    0.307775] pci 0000:00:1c.0:   MEM window: 0x57300000-0x582fffff
[    0.307781] pci 0000:00:1c.0:   PREFETCH window: 0x00000050000000-0x00000050ffffff
[    0.307807] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:04
[    0.307811] pci 0000:00:1c.1:   IO window: 0x3000-0x3fff
[    0.307818] pci 0000:00:1c.1:   MEM window: 0x56300000-0x572fffff
[    0.307842] pci 0000:00:1c.1:   PREFETCH window: 0x00000051000000-0x00000051ffffff
[    0.307851] pci 0000:00:1c.2: PCI bridge, secondary bus 0000:05
[    0.307875] pci 0000:00:1c.2:   IO window: 0x2000-0x2fff
[    0.307882] pci 0000:00:1c.2:   MEM window: 0x55200000-0x562fffff
[    0.307906] pci 0000:00:1c.2:   PREFETCH window: 0x00000052000000-0x00000052ffffff
[    0.307915] pci 0000:00:1c.3: PCI bridge, secondary bus 0000:06
[    0.307936] pci 0000:00:1c.3:   IO window: 0x1000-0x1fff
[    0.307943] pci 0000:00:1c.3:   MEM window: 0x54100000-0x551fffff
[    0.307966] pci 0000:00:1c.3:   PREFETCH window: 0x00000053000000-0x00000053ffffff
[    0.307975] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:07
[    0.307977] pci 0000:00:1e.0:   IO window: disabled
[    0.308001] pci 0000:00:1e.0:   MEM window: disabled
[    0.308006] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.308044]   alloc irq_desc for 16 on node -1
[    0.308064]   alloc kstat_irqs on node -1
[    0.308069] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.308094] pci 0000:00:1c.0: setting latency timer to 64
[    0.308105]   alloc irq_desc for 17 on node -1
[    0.308106]   alloc kstat_irqs on node -1
[    0.308128] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.308134] pci 0000:00:1c.1: setting latency timer to 64
[    0.308162]   alloc irq_desc for 18 on node -1
[    0.308164]   alloc kstat_irqs on node -1
[    0.308167] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.308190] pci 0000:00:1c.2: setting latency timer to 64
[    0.308201]   alloc irq_desc for 19 on node -1
[    0.308203]   alloc kstat_irqs on node -1
[    0.308227] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.308233] pci 0000:00:1c.3: setting latency timer to 64
[    0.308260] pci 0000:00:1e.0: setting latency timer to 64
[    0.308265] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.308268] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.308288] pci_bus 0000:02: resource 0 io:  [0x4000-0x4fff]
[    0.308291] pci_bus 0000:02: resource 1 mem: [0x57300000-0x582fffff]
[    0.308293] pci_bus 0000:02: resource 2 pref mem [0x50000000-0x50ffffff]
[    0.308296] pci_bus 0000:04: resource 0 io:  [0x3000-0x3fff]
[    0.308299] pci_bus 0000:04: resource 1 mem: [0x56300000-0x572fffff]
[    0.308319] pci_bus 0000:04: resource 2 pref mem [0x51000000-0x51ffffff]
[    0.308321] pci_bus 0000:05: resource 0 io:  [0x2000-0x2fff]
[    0.308324] pci_bus 0000:05: resource 1 mem: [0x55200000-0x562fffff]
[    0.308326] pci_bus 0000:05: resource 2 pref mem [0x52000000-0x52ffffff]
[    0.308329] pci_bus 0000:06: resource 0 io:  [0x1000-0x1fff]
[    0.308349] pci_bus 0000:06: resource 1 mem: [0x54100000-0x551fffff]
[    0.308352] pci_bus 0000:06: resource 2 pref mem [0x53000000-0x53ffffff]
[    0.308354] pci_bus 0000:07: resource 3 io:  [0x00-0xffff]
[    0.308357] pci_bus 0000:07: resource 4 mem: [0x000000-0xffffffff]
[    0.308424] NET: Registered protocol family 2
[    0.308614] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.309287] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.310556] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.311374] TCP: Hash tables configured (established 131072 bind 65536)
[    0.311395] TCP reno registered
[    0.311685] NET: Registered protocol family 1
[    0.311747] pci 0000:00:02.0: Boot video device
[    0.312839] cpufreq-nforce2: No nForce2 chipset.
[    0.312903] Scanning for low memory corruption every 60 seconds
[    0.313155] audit: initializing netlink socket (disabled)
[    0.313187] type=2000 audit(1285170911.311:1): initialized
[    0.335779] Trying to unpack rootfs image as initramfs...
[    0.360489] highmem bounce pool size: 64 pages
[    0.360513] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.367944] VFS: Disk quotas dquot_6.5.2
[    0.368074] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.369347] fuse init (API version 7.13)
[    0.369533] msgmni has been set to 1705
[    0.376308] alg: No test for stdrng (krng)
[    0.376488] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.376492] io scheduler noop registered
[    0.376493] io scheduler anticipatory registered
[    0.376495] io scheduler deadline registered
[    0.376589] io scheduler cfq registered (default)
[    0.376971]   alloc irq_desc for 24 on node -1
[    0.376973]   alloc kstat_irqs on node -1
[    0.377006] pcieport 0000:00:1c.0: irq 24 for MSI/MSI-X
[    0.377036] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.377399]   alloc irq_desc for 25 on node -1
[    0.377401]   alloc kstat_irqs on node -1
[    0.377428] pcieport 0000:00:1c.1: irq 25 for MSI/MSI-X
[    0.377457] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.377816]   alloc irq_desc for 26 on node -1
[    0.377817]   alloc kstat_irqs on node -1
[    0.377844] pcieport 0000:00:1c.2: irq 26 for MSI/MSI-X
[    0.377873] pcieport 0000:00:1c.2: setting latency timer to 64
[    0.378236]   alloc irq_desc for 27 on node -1
[    0.378238]   alloc kstat_irqs on node -1
[    0.378264] pcieport 0000:00:1c.3: irq 27 for MSI/MSI-X
[    0.378294] pcieport 0000:00:1c.3: setting latency timer to 64
[    0.378523] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.378558] Firmware did not grant requested _OSC control
[    0.378615] Firmware did not grant requested _OSC control
[    0.378646] Firmware did not grant requested _OSC control
[    0.378677] Firmware did not grant requested _OSC control
[    0.378721] Firmware did not grant requested _OSC control
[    0.378751] Firmware did not grant requested _OSC control
[    0.378781] Firmware did not grant requested _OSC control
[    0.378812] Firmware did not grant requested _OSC control
[    0.378845] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.380508] ACPI: AC Adapter [AC] (on-line)
[    0.380697] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:02/PNP0C0C:00/input/input0
[    0.380702] ACPI: Power Button [PWRB]
[    0.380795] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:02/PNP0C0D:00/input/input1
[    0.380893] ACPI: Lid Switch [LID0]
[    0.380989] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:02/PNP0C0E:00/input/input2
[    0.380991] ACPI: Sleep Button [SLPB]
[    0.381110] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    0.381113] ACPI: Power Button [PWRF]
[    0.388259] Monitor-Mwait will be used to enter C-1 state
[    0.388349] Monitor-Mwait will be used to enter C-2 state
[    0.388388] Monitor-Mwait will be used to enter C-3 state
[    0.388412] Marking TSC unstable due to TSC halts in idle
[    0.388552] processor LNXCPU:00: registered as cooling_device0
[    0.391094] Switching to clocksource hpet
[    0.431089] thermal LNXTHERM:01: registered as thermal_zone0
[    0.431117] ACPI: Thermal Zone [TZ01] (85 C)
[    0.437110] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.439864] brd: module loaded
[    0.440277] isapnp: Scanning for PnP cards...
[    0.453485] loop: module loaded
[    0.453706] input: Macintosh mouse button emulation as /devices/virtual/input/input4
[    0.453959] ata_piix 0000:00:1f.1: version 2.13
[    0.453994] ata_piix 0000:00:1f.1: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    0.454095] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.454315] scsi0 : ata_piix
[    0.454480] scsi1 : ata_piix
[    0.455847] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x50e0 irq 14
[    0.455850] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x50e8 irq 15
[    0.456745] Fixed MDIO Bus: probed
[    0.456838] PPP generic driver version 2.4.2
[    0.456937] tun: Universal TUN/TAP device driver, 1.6
[    0.456939] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.457102] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.457158] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.457197] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    0.457219] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    0.457288] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    0.457379] ehci_hcd 0000:00:1a.7: debug port 1
[    0.461288] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    0.512394] ehci_hcd 0000:00:1a.7: irq 18, io mem 0x58304c00
[    0.532729] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    0.533018] usb usb1: configuration #1 chosen from 1 choice
[    0.533085] hub 1-0:1.0: USB hub found
[    0.533114] hub 1-0:1.0: 4 ports detected
[    0.533270]   alloc irq_desc for 23 on node -1
[    0.533272]   alloc kstat_irqs on node -1
[    0.533298] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.533340] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.533362] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.533436] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    0.533523] ehci_hcd 0000:00:1d.7: debug port 1
[    0.537414] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.540357] ehci_hcd 0000:00:1d.7: irq 23, io mem 0x58304800
[    0.560703] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.561044] usb usb2: configuration #1 chosen from 1 choice
[    0.561107] hub 2-0:1.0: USB hub found
[    0.561118] hub 2-0:1.0: 6 ports detected
[    0.561275] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.561310] uhci_hcd: USB Universal Host Controller Interface driver
[    0.561435] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.561464] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    0.561468] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    0.561566] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    0.561660] uhci_hcd 0000:00:1a.0: irq 16, io base 0x000050c0
[    0.561853] usb usb3: configuration #1 chosen from 1 choice
[    0.561912] hub 3-0:1.0: USB hub found
[    0.561919] hub 3-0:1.0: 2 ports detected
[    0.562016]   alloc irq_desc for 21 on node -1
[    0.562036]   alloc kstat_irqs on node -1
[    0.562042] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.562049] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    0.562070] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    0.562139] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    0.562230] uhci_hcd 0000:00:1a.1: irq 21, io base 0x000050a0
[    0.562424] usb usb4: configuration #1 chosen from 1 choice
[    0.562483] hub 4-0:1.0: USB hub found
[    0.562489] hub 4-0:1.0: 2 ports detected
[    0.562586] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    0.562610] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.562614] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.562679] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    0.562745] uhci_hcd 0000:00:1d.0: irq 23, io base 0x00005080
[    0.562931] usb usb5: configuration #1 chosen from 1 choice
[    0.562972] hub 5-0:1.0: USB hub found
[    0.562999] hub 5-0:1.0: 2 ports detected
[    0.563095] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    0.563101] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.563123] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.563188] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    0.563261] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00005060
[    0.563451] usb usb6: configuration #1 chosen from 1 choice
[    0.563509] hub 6-0:1.0: USB hub found
[    0.563516] hub 6-0:1.0: 2 ports detected
[    0.563635] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.563642] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.563646] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.563708] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    0.563773] uhci_hcd 0000:00:1d.2: irq 18, io base 0x00005040
[    0.563959] usb usb7: configuration #1 chosen from 1 choice
[    0.566302] hub 7-0:1.0: USB hub found
[    0.566329] hub 7-0:1.0: 2 ports detected
[    0.566554] PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:MSE0] at 0x60,0x64 irq 1,12
[    0.681056] ata1.00: ATAPI: PIONEER DVD-RW DVRKD08RS, 1.02, max UDMA/33
[    0.693469] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.696722] ata1.00: configured for UDMA/33
[    0.698382] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.698768] mice: PS/2 mouse device common for all mice
[    0.699152] rtc_cmos 00:03: RTC can wake from S4
[    0.699248] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    0.699318] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
[    0.699576] device-mapper: uevent: version 1.0.3
[    0.703163] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: dm-devel@redhat.com
[    0.704285] device-mapper: multipath: version 1.1.0 loaded
[    0.704306] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.706550] EISA: Probing bus 0 at eisa.0
[    0.706576] Cannot allocate resource for EISA slot 1
[    0.706578] Cannot allocate resource for EISA slot 2
[    0.706580] Cannot allocate resource for EISA slot 3
[    0.706600] Cannot allocate resource for EISA slot 4
[    0.706602] Cannot allocate resource for EISA slot 5
[    0.706635] EISA: Detected 0 cards.
[    0.708678] cpuidle: using governor ladder
[    0.708805] cpuidle: using governor menu
[    0.709671] TCP cubic registered
[    0.709988] NET: Registered protocol family 10
[    0.710850] lo: Disabled Privacy Extensions
[    0.711423] NET: Registered protocol family 17
[    0.711524] Using IPI No-Shortcut mode
[    0.711714] PM: Resume from disk failed.
[    0.711743] registered taskstats version 1
[    0.713095]   Magic number: 10:154:943
[    0.713190] tty tty0: hash matches
[    0.713192] tty console: hash matches
[    0.716254] rtc_cmos 00:03: setting system clock to 2010-09-22 15:55:12 UTC (1285170912)
[    0.716258] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.716260] EDD information not available.
[    0.768649] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input5
[    0.888387] ACPI: Battery Slot [BAT0] (battery present)
[    1.229513] isapnp: No Plug & Play device found
[    1.236563] scsi 0:0:0:0: CD-ROM            PIONEER  DVD-RW DVRKD08RS 1.02 PQ: 0 ANSI: 5
[    1.257278] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.257284] Uniform CD-ROM driver Revision: 3.20
[    1.257571] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    1.257728] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    1.524651] usb 5-1: new low speed USB device using uhci_hcd and address 2
[    1.584814] Freeing initrd memory: 13390k freed
[    1.606482] Freeing unused kernel memory: 656k freed
[    1.607738] Write protecting the kernel text: 4676k
[    1.607798] Write protecting the kernel read-only data: 1840k
[    1.652633] udev: starting version 151
[    1.700188] usb 5-1: configuration #1 chosen from 1 choice
[    1.966716] usbcore: registered new interface driver hiddev
[    1.981773] input: PIXART USB OPTICAL MOUSE as /devices/pci0000:00/0000:00:1d.0/usb5/5-1/5-1:1.0/input/input6
[    1.982001] generic-usb 0003:093A:2510.0001: input,hidraw0: USB HID v1.11 Mouse [PIXART USB OPTICAL MOUSE] on usb-0000:00:1d.0-1/input0
[    1.982067] usbcore: registered new interface driver usbhid
[    1.982087] usbhid: v2.6:USB HID core driver
[    2.296770] Linux agpgart interface v0.103
[    2.318109] agpgart-intel 0000:00:00.0: Intel 965GM Chipset
[    2.318573] agpgart-intel 0000:00:00.0: detected 7676K stolen memory
[    2.339692] tg3.c:v3.102 (September 1, 2009)
[    2.339813] tg3 0000:05:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    2.339884] tg3 0000:05:00.0: setting latency timer to 64
[    2.388045] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0x40000000
[    2.388104] ahci 0000:00:1f.2: version 3.0
[    2.388140] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    2.388262]   alloc irq_desc for 28 on node -1
[    2.388264]   alloc kstat_irqs on node -1
[    2.388294] ahci 0000:00:1f.2: irq 28 for MSI/MSI-X
[    2.388465] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 3 Gbps 0x3 impl SATA mode
[    2.388486] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part ccc ems 
[    2.388492] ahci 0000:00:1f.2: setting latency timer to 64
[    2.390669] [drm] Initialized drm 1.1.0 20060810
[    2.410509] scsi2 : ahci
[    2.410858] scsi3 : ahci
[    2.411109] scsi4 : ahci
[    2.411487] ata3: SATA max UDMA/133 abar m2048@0x58304000 port 0x58304100 irq 28
[    2.411491] ata4: SATA max UDMA/133 abar m2048@0x58304000 port 0x58304180 irq 28
[    2.411493] ata5: DUMMY
[    2.715020] eth0: Tigon3 [partno(BCM95906) rev c002] (PCI Express) MAC address 00:1b:38:da:c0:f7
[    2.715024] eth0: attached PHY is 5906 (10/100Base-TX Ethernet) (WireSpeed[0])
[    2.715027] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[    2.715029] eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[    2.732111] ata4: SATA link down (SStatus 0 SControl 300)
[    3.008115] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    3.009233] ata3.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[    3.379601] ata3.00: ATA-8: TOSHIBA MK8046GSX, LB313J, max UDMA/100
[    3.379604] ata3.00: 156301488 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    3.381107] ata3.00: ACPI cmd 00/00:00:00:00:00:a0 (NOP) rejected by device (Stat=0x51 Err=0x04)
[    3.381437] ata3.00: configured for UDMA/100
[    3.396362] scsi 2:0:0:0: Direct-Access     ATA      TOSHIBA MK8046GS LB31 PQ: 0 ANSI: 5
[    3.396711] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    3.397231] sd 2:0:0:0: [sda] 156301488 512-byte logical blocks: (80.0 GB/74.5 GiB)
[    3.397328] sd 2:0:0:0: [sda] Write Protect is off
[    3.397349] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.397389] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.397698]  sda: sda1 sda2 < sda5 >
[    3.483448] sd 2:0:0:0: [sda] Attached SCSI disk
[    3.529953] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.529959] i915 0000:00:02.0: setting latency timer to 64
[    3.552931]   alloc irq_desc for 29 on node -1
[    3.552935]   alloc kstat_irqs on node -1
[    3.552965] i915 0000:00:02.0: irq 29 for MSI/MSI-X
[    3.552972] [drm] set up 7M of stolen space
[    3.729121] [drm] initialized overlay support
[    4.401492] fb0: inteldrmfb frame buffer device
[    4.401495] registered panic notifier
[    4.610545] acpi device:39: registered as cooling_device1
[    4.611749] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:01/input/input7
[    4.611970] ACPI: Video Device [OVGA] (multi-head: yes  rom: no  post: no)
[    4.612839] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    4.620911] vga16fb: initializing
[    4.620915] vga16fb: mapped to 0xc00a0000
[    4.620919] vga16fb: not registering due to another framebuffer present
[    4.764108] Console: switching to colour frame buffer device 160x50
[    5.620752] xor: automatically using best checksumming function: pIII_sse
[    5.640010]    pIII_sse  :  6889.000 MB/sec
[    5.640012] xor: using function: pIII_sse (6889.000 MB/sec)
[    5.647050] device-mapper: dm-raid45: initialized v0.2594b
[    5.843104] EXT4-fs (sda1): mounted filesystem with ordered data mode
[   17.716877] udev: starting version 151
[   17.757681] lp: driver loaded but no devices found
[   17.781658] Adding 2975736k swap on /dev/sda5.  Priority:-1 extents:1 across:2975736k 
[   18.345794] cfg80211: Calling CRDA to update world regulatory domain
[   18.381128] acer-wmi: Acer Laptop ACPI-WMI Extras
[   18.387115] acer-wmi: Brightness must be controlled by generic video driver
[   18.404458] cfg80211: World regulatory domain updated:
[   18.404462] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   18.404465] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   18.404468] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   18.404470] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   18.404473] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   18.404475] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   18.430275] ath5k 0000:06:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   18.430293] ath5k 0000:06:00.0: setting latency timer to 64
[   18.430336] ath5k 0000:06:00.0: registered as 'phy0'
[   19.000477] ip_tables: (C) 2000-2006 Netfilter Core Team
[   19.055618] nf_conntrack version 0.5.0 (15886 buckets, 63544 max)
[   19.057112] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Please use
[   19.057116] nf_conntrack.acct=1 kernel parameter, acct=1 nf_conntrack module option or
[   19.057117] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
[   19.154565]   alloc irq_desc for 22 on node -1
[   19.154569]   alloc kstat_irqs on node -1
[   19.154577] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   19.154626] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   19.158239] ip6_tables: (C) 2000-2006 Netfilter Core Team
[   19.309747] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input8
[   19.525787] input: PS/2 Mouse as /devices/platform/i8042/serio1/input/input9
[   19.538358]   alloc irq_desc for 30 on node -1
[   19.538362]   alloc kstat_irqs on node -1
[   19.538426] tg3 0000:05:00.0: irq 30 for MSI/MSI-X
[   19.607744] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input10
[   19.695865] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   19.912882] ath: EEPROM regdomain: 0x65
[   19.912885] ath: EEPROM indicates we should expect a direct regpair map
[   19.912889] ath: Country alpha2 being used: 00
[   19.912890] ath: Regpair used: 0x65
[   20.035113] phy0: Selected rate control algorithm 'minstrel'
[   20.035814] Registered led device: ath5k-phy0::rx
[   20.035832] Registered led device: ath5k-phy0::tx
[   20.035836] ath5k phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
[   20.129500] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   21.424798] ppdev: user-space parallel port driver
[  804.499041] wlan0: deauthenticating from 00:8b:5d:84:a5:8a by local choice (reason=3)
[  804.510266] wlan0: direct probe to AP 00:8b:5d:84:a5:8a (try 1)
[  804.513286] wlan0: direct probe responded
[  804.513291] wlan0: authenticate with AP 00:8b:5d:84:a5:8a (try 1)
[  804.515240] wlan0: authenticated
[  804.515262] wlan0: associate with AP 00:8b:5d:84:a5:8a (try 1)
[  804.518092] wlan0: RX AssocResp from 00:8b:5d:84:a5:8a (capab=0x431 status=0 aid=2)
[  804.518096] wlan0: associated
[  804.518745] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  804.552850] padlock: VIA PadLock not detected.
[  814.612017] wlan0: no IPv6 routers present
[ 6468.600033] usb 6-1: new full speed USB device using uhci_hcd and address 2
[ 6468.830189] usb 6-1: configuration #3 chosen from 1 choice
[ 6468.886865] cdc_acm 6-1:3.1: ttyACM0: USB ACM device
[ 6468.889245] usbcore: registered new interface driver cdc_acm
[ 6468.890036] cdc_acm: v0.26:USB Abstract Control Model driver for USB modems and ISDN adapters
[ 6478.920075] usb 6-1: USB disconnect, address 2
[ 6480.152035] usb 6-1: new full speed USB device using uhci_hcd and address 3
[ 6480.323191] usb 6-1: configuration #6 chosen from 1 choice
tony@tony-laptop ~ $ 

```

> **lymphor said:**
> ..... by the way I have a Samsung j700i: it worked for a while with Wammu, but at a certain point it just didn't anymore. So I installed Windows with VirtualBox and that way I was able to use Samsung PC Studio in it.
Wammu? VirtualBox? I'm completely lost at the moment. I'll have to see what I can glean from Google.

But thanks for your response,
Cheers,
Tony

---

### Post by alerum68 on 2010-11-26
> **lymphor said:**
> What Trin Calway meant to say is that you have to open the terminal and type **dmesg** in it having your phone plugged in as Media Player. After that copy-paste here the messages you get in the terminal.
Good luck!

(by the way I have a Samsung j700i: it worked for a while with Wammu, but at a certain point it just didn't anymore. So I installed Windows with VirtualBox and that way I was able to use Samsung PC Studio in it)

How were you able to get PC Studio to detect the phone in VirtualBox?  I am able to detect the phone as a USB device, but every time I try to run PC Studio to autodetect, it never finds the phone.  I tried changing the rules file as I found in another post, but that didn't help either.

---

### Post by lymphor on 2010-11-26
I had no problems.
In Windows did you install both driver and PC Studio in the correct order?
I remember it was important to install them in the correct order.

---

### Post by Duncan Williams on 2011-04-11
I know this may sound obvious and possibly time consuming but.
I use a samsung c5220 mobile phone as a 3G mobile modem.
When I want to copy files back and forth or copy mp3s to the phone or access texts/phone numbers etc.
I reboot into windows XP, use pcstudio, leave any files in a folder in windows.
After booting back into ubuntu I can access the files.

This may take a bit longer than doing it straight from ubuntu but it can be done easily and less often if required.

Also you can use say a 2 gig microSD card in your phone and then read it in ubuntu with a cheap usb card reader. You then save all your phone stuff on the sd card and swap your photos, mp3s etc that way.

---

### Post by Tony.B on 2011-04-13
> **Duncan Williams said:**
> I know this may sound obvious and possibly time consuming but.
I use a samsung c5220 mobile phone as a 3G mobile modem.
When I want to copy files back and forth or copy mp3s to the phone or access texts/phone numbers etc.
I reboot into windows XP, use pcstudio, leave any files in a folder in windows.
After booting back into ubuntu I can access the files.

This may take a bit longer than doing it straight from ubuntu but it can be done easily and less often if required.

Maybe that will work for people who still have Windows on their computer - unfortunately (*or should I say **fortunately**? *) that doesn't apply to me.

Since originally posting this query, my mobile phone service provider has given me a free upgrade, so this thread is no longer so important to me.  My new phone is a Nokia 5230 - very nice phone, but I can't get it to work as a modem on my laptop!

---

