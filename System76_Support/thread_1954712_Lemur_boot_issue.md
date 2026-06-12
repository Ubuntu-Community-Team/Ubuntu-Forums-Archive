---
title: "Lemur boot issue"
date: 2012-04-08
forum: System76 Support
---

### Post by jgammel25 on 2012-04-08
Hello all,

I had gotten a new Lemur a couple months ago and have been getting to use it a lot more recently and have really enjoyed it; however, I've noticed a strange boot issue that has developed.

After the System76 Splash screen, it will sit on the purplish screen for 1:40-1:45, then flicker to the Ubuntu screen and then the login.  After this point everything is fine.  I've noticed no problems with the system other than this.

This is a video I made quickly illustrating the boot issue:
[http://www.youtube.com/watch?v=7TyvqNLNCs4](http://www.youtube.com/watch?v=7TyvqNLNCs4)

I'm very new to Linux and haven't done very much to alter the system other than install some recommended updates and applications.  I will provide any information needed to help, but you may have to help me find it :)

Thanks to anyone who takes a look!  Happy Easter!

---

### Post by Paddy Landau on 2012-04-09
Well, it's a bit unusual in that it doesn't show the Ubuntu + dots for a little while; but it's fine, so don't worry about it. My computer takes about as long to boot to the login, but it shows the Ubuntu + dots sooner.

---

### Post by jgammel25 on 2012-04-09
I wouldn't be concerned, other than that I feel like it used to boot much faster..  Like < 1 minute, so it would have been dramatically faster, but I don't know that for a fact.

So, I guess maybe I emphasized the flickering in my OP, but the actual issue is the duration on the purplish screen.

---

### Post by Paddy Landau on 2012-04-09
If it is taking significantly longer to boot, there may well be some problem. Unfortunately, I really do not know how to diagnose that, sorry.

---

### Post by pjman on 2012-04-09
That does seem to be taking quite a while to boot. After the BIOS screen, change to the terminal that displays messages to see what it's loading/hanging on. I'm pretty sure it's F6 or F8 (I can't remember right now but can check later tonight).

Ctrl+Alt+F6/F8

That should at least point you in the direction of what to troubleshoot next.

---

### Post by jgammel25 on 2012-04-09
I've tried several times and haven't been able to get the console to come up during the boot...  I could be doing something wrong but I wasn't able to find definitive commands for accomplishing that in 11.10.  If you're able to get it to work please let me know what command you used, Thanks!  Or if there is a log somewhere I could look at.?. that's the kind of thing I'm really unsure about.

---

### Post by ahood on 2012-04-09
There is a boot.log. To view, type the following in a terminal.

> cat /var/log/boot.log

There is also the dmesg log that also has useful information.

> cat /var/log/dmesg

Copy and paste the last boot up process into a message here.

:p

---

### Post by jgammel25 on 2012-04-09
boot.log
> fsck from util-linux 2.19.1
/dev/sda1: clean, 241545/30048256 files, 7043349/120165014 blocks (check in 3 mounts)
modem-manager[892]: <info>  ModemManager (version 0.5) starting...

modem-manager[892]: <info>  Loaded plugin Novatel

modem-manager[892]: <info>  Loaded plugin Option High-Speed

Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
 * Starting AppArmor profiles                                                  [ OK ]
speech-dispatcher disabled; edit /etc/default/speech-dispatcher
Checking for running unattended-upgrades: 
 * Stopping Failsafe Boot Delay                                                [ OK ]
 * Stopping System V initialisation compatibility                              [ OK ]
 * Starting System V runlevel compatibility                                    [ OK ]
 * Stopping automatic crash report generation                                  [fail]
 * Starting LightDM Display Manager                                            [ OK ]
 * Starting ACPI daemon                                                        [ OK ]
 * Starting anac(h)ronistic cron                                               [ OK ]
 * Starting save kernel messages                                               [ OK ]
 * Starting regular background program processing daemon                       [ OK ]
 * Starting deferred execution scheduler                                       [ OK ]
 * Starting CPU interrupts balancing daemon                                    [ OK ]
 * Stopping anac(h)ronistic cron                                               [ OK ]


dmesg
> [    1.050862] pci 0000:03:00.0: reg 30: [mem 0xf7c00000-0xf7c0ffff pref]
[    1.050948] pci 0000:03:00.0: PME# supported from D0 D3hot D3cold
[    1.050954] pci 0000:03:00.0: PME# disabled
[    1.050999] pci 0000:03:00.1: [197b:2392] type 0 class 0x000880
[    1.051021] pci 0000:03:00.1: reg 10: [mem 0xf7c26000-0xf7c260ff]
[    1.051219] pci 0000:03:00.2: [197b:2391] type 0 class 0x000805
[    1.051241] pci 0000:03:00.2: reg 10: [mem 0xf7c25000-0xf7c250ff]
[    1.051438] pci 0000:03:00.3: [197b:2393] type 0 class 0x000880
[    1.051460] pci 0000:03:00.3: reg 10: [mem 0xf7c24000-0xf7c240ff]
[    1.058570] pci 0000:00:1c.3: PCI bridge to [bus 03-03]
[    1.058578] pci 0000:00:1c.3:   bridge window [io  0xe000-0xefff]
[    1.058586] pci 0000:00:1c.3:   bridge window [mem 0xf7c00000-0xf7cfffff]
[    1.058598] pci 0000:00:1c.3:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    1.058630] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    1.058773] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    1.058803] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[    1.058830] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[    1.058921] \_SB_.PCI0:_OSC invalid UUID
[    1.058922] _OSC request data:1 1f 1f 
[    1.058926]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    1.058952] \_SB_.PCI0:_OSC invalid UUID
[    1.058953] _OSC request data:1 0 1d 
[    1.058956]  pci0000:00: ACPI _OSC request failed (AE_ERROR), returned control mask: 0x1d
[    1.058957] ACPI _OSC control for PCIe not granted, disabling ASPM
[    1.061626] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 10 *11 12 14 15)
[    1.061665] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 *4 5 6 10 11 12 14 15)
[    1.061703] ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 10 11 12 14 15)
[    1.061738] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 *10 11 12 14 15)
[    1.061773] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    1.061809] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 10 11 12 14 15) *0, disabled.
[    1.061844] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 *5 6 10 11 12 14 15)
[    1.061879] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 10 *11 12 14 15)
[    1.061951] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    1.061957] vgaarb: loaded
[    1.061958] vgaarb: bridge control possible 0000:00:02.0
[    1.062080] SCSI subsystem initialized
[    1.062122] libata version 3.00 loaded.
[    1.062152] usbcore: registered new interface driver usbfs
[    1.062159] usbcore: registered new interface driver hub
[    1.062177] usbcore: registered new device driver usb
[    1.062236] PCI: Using ACPI for IRQ routing
[    1.063757] PCI: pci_cache_line_size set to 64 bytes
[    1.063866] reserve RAM buffer: 000000000009d800 - 000000000009ffff 
[    1.063868] reserve RAM buffer: 00000000da535000 - 00000000dbffffff 
[    1.063871] reserve RAM buffer: 00000000da7e4000 - 00000000dbffffff 
[    1.063873] reserve RAM buffer: 00000000dacec000 - 00000000dbffffff 
[    1.063875] reserve RAM buffer: 000000021fe00000 - 000000021fffffff 
[    1.063940] NetLabel: Initializing
[    1.063941] NetLabel:  domain hash size = 128
[    1.063942] NetLabel:  protocols = UNLABELED CIPSOv4
[    1.063951] NetLabel:  unlabeled traffic allowed by default
[    1.063980] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0, 0, 0, 0, 0, 0
[    1.063985] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    1.065995] Switching to clocksource hpet
[    1.066532] Switched to NOHz mode on CPU #0
[    1.066606] Switched to NOHz mode on CPU #1
[    1.066614] Switched to NOHz mode on CPU #3
[    1.066654] Switched to NOHz mode on CPU #2
[    1.070254] AppArmor: AppArmor Filesystem Enabled
[    1.070275] pnp: PnP ACPI init
[    1.070287] ACPI: bus type pnp registered
[    1.070500] pnp 00:00: [bus 00-3e]
[    1.070502] pnp 00:00: [io  0x0000-0x0cf7 window]
[    1.070504] pnp 00:00: [io  0x0cf8-0x0cff]
[    1.070505] pnp 00:00: [io  0x0d00-0xffff window]
[    1.070507] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    1.070508] pnp 00:00: [mem 0x000c0000-0x000c3fff window]
[    1.070511] pnp 00:00: [mem 0x000c4000-0x000c7fff window]
[    1.070513] pnp 00:00: [mem 0x000c8000-0x000cbfff window]
[    1.070515] pnp 00:00: [mem 0x000cc000-0x000cffff window]
[    1.070516] pnp 00:00: [mem 0x000d0000-0x000d3fff window]
[    1.070518] pnp 00:00: [mem 0x000d4000-0x000d7fff window]
[    1.070519] pnp 00:00: [mem 0x000d8000-0x000dbfff window]
[    1.070521] pnp 00:00: [mem 0x000dc000-0x000dffff window]
[    1.070522] pnp 00:00: [mem 0x000e0000-0x000e3fff window]
[    1.070524] pnp 00:00: [mem 0x000e4000-0x000e7fff window]
[    1.070525] pnp 00:00: [mem 0x000e8000-0x000ebfff window]
[    1.070527] pnp 00:00: [mem 0x000ec000-0x000effff window]
[    1.070528] pnp 00:00: [mem 0x000f0000-0x000fffff window]
[    1.070530] pnp 00:00: [mem 0xdfa00000-0xfeafffff window]
[    1.070532] pnp 00:00: [mem 0xfed40000-0xfed44fff window]
[    1.070589] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    1.070599] pnp 00:01: [io  0x0000-0x001f]
[    1.070601] pnp 00:01: [io  0x0081-0x0091]
[    1.070602] pnp 00:01: [io  0x0093-0x009f]
[    1.070603] pnp 00:01: [io  0x00c0-0x00df]
[    1.070605] pnp 00:01: [dma 4]
[    1.070620] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
[    1.070626] pnp 00:02: [mem 0xff000000-0xffffffff]
[    1.070641] pnp 00:02: Plug and Play ACPI device, IDs INT0800 (active)
[    1.070700] pnp 00:03: [mem 0xfed00000-0xfed003ff]
[    1.070715] pnp 00:03: Plug and Play ACPI device, IDs PNP0103 (active)
[    1.070724] pnp 00:04: [io  0x002e-0x002f]
[    1.070726] pnp 00:04: [io  0x004e-0x004f]
[    1.070727] pnp 00:04: [io  0x0061]
[    1.070728] pnp 00:04: [io  0x0063]
[    1.070729] pnp 00:04: [io  0x0065]
[    1.070731] pnp 00:04: [io  0x0067]
[    1.070732] pnp 00:04: [io  0x0070]
[    1.070733] pnp 00:04: [io  0x0080]
[    1.070734] pnp 00:04: [io  0x0092]
[    1.070735] pnp 00:04: [io  0x00b2-0x00b3]
[    1.070737] pnp 00:04: [io  0x0680-0x069f]
[    1.070738] pnp 00:04: [io  0x0200-0x020f]
[    1.070739] pnp 00:04: [io  0xffff]
[    1.070740] pnp 00:04: [io  0xffff]
[    1.070742] pnp 00:04: [io  0x0400-0x0453]
[    1.070743] pnp 00:04: [io  0x0458-0x047f]
[    1.070744] pnp 00:04: [io  0x0500-0x057f]
[    1.070746] pnp 00:04: [io  0x164e-0x164f]
[    1.070782] system 00:04: [io  0x0680-0x069f] has been reserved
[    1.070784] system 00:04: [io  0x0200-0x020f] has been reserved
[    1.070786] system 00:04: [io  0xffff] has been reserved
[    1.070787] system 00:04: [io  0xffff] has been reserved
[    1.070789] system 00:04: [io  0x0400-0x0453] has been reserved
[    1.070791] system 00:04: [io  0x0458-0x047f] has been reserved
[    1.070793] system 00:04: [io  0x0500-0x057f] has been reserved
[    1.070795] system 00:04: [io  0x164e-0x164f] has been reserved
[    1.070797] system 00:04: Plug and Play ACPI device, IDs PNP0c02 (active)
[    1.070803] pnp 00:05: [io  0x0070-0x0077]
[    1.070815] pnp 00:05: [irq 8]
[    1.070829] pnp 00:05: Plug and Play ACPI device, IDs PNP0b00 (active)
[    1.070850] pnp 00:06: [io  0x0454-0x0457]
[    1.070873] system 00:06: [io  0x0454-0x0457] has been reserved
[    1.070875] system 00:06: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
[    1.070894] pnp 00:07: [io  0x0010-0x001f]
[    1.070896] pnp 00:07: [io  0x0022-0x003f]
[    1.070897] pnp 00:07: [io  0x0044-0x005f]
[    1.070898] pnp 00:07: [io  0x0072-0x007f]
[    1.070900] pnp 00:07: [io  0x0080]
[    1.070901] pnp 00:07: [io  0x0084-0x0086]
[    1.070902] pnp 00:07: [io  0x0088]
[    1.070903] pnp 00:07: [io  0x008c-0x008e]
[    1.070905] pnp 00:07: [io  0x0090-0x009f]
[    1.070906] pnp 00:07: [io  0x00a2-0x00bf]
[    1.070907] pnp 00:07: [io  0x00e0-0x00ef]
[    1.070908] pnp 00:07: [io  0x04d0-0x04d1]
[    1.070935] system 00:07: [io  0x04d0-0x04d1] has been reserved
[    1.070937] system 00:07: Plug and Play ACPI device, IDs PNP0c02 (active)
[    1.070944] pnp 00:08: [io  0x00f0-0x00ff]
[    1.070950] pnp 00:08: [irq 13]
[    1.070964] pnp 00:08: Plug and Play ACPI device, IDs PNP0c04 (active)
[    1.070982] pnp 00:09: [io  0x0060]
[    1.070984] pnp 00:09: [io  0x0064]
[    1.070989] pnp 00:09: [irq 1]
[    1.071007] pnp 00:09: Plug and Play ACPI device, IDs PNP0303 PNP030b (active)
[    1.071041] pnp 00:0a: [irq 12]
[    1.071057] pnp 00:0a: Plug and Play ACPI device, IDs PNP0f13 PNP0f03 (active)
[    1.071228] pnp 00:0b: [mem 0xfed1c000-0xfed1ffff]
[    1.071230] pnp 00:0b: [mem 0xfed10000-0xfed17fff]
[    1.071231] pnp 00:0b: [mem 0xfed18000-0xfed18fff]
[    1.071233] pnp 00:0b: [mem 0xfed19000-0xfed19fff]
[    1.071234] pnp 00:0b: [mem 0xf8000000-0xfbffffff]
[    1.071236] pnp 00:0b: [mem 0xfed20000-0xfed3ffff]
[    1.071237] pnp 00:0b: [mem 0xfed90000-0xfed93fff]
[    1.071238] pnp 00:0b: [mem 0xfed45000-0xfed8ffff]
[    1.071240] pnp 00:0b: [mem 0xff000000-0xffffffff]
[    1.071241] pnp 00:0b: [mem 0xfee00000-0xfeefffff]
[    1.071243] pnp 00:0b: [mem 0xdfa00000-0xdfa00fff]
[    1.071283] system 00:0b: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    1.071285] system 00:0b: [mem 0xfed10000-0xfed17fff] has been reserved
[    1.071287] system 00:0b: [mem 0xfed18000-0xfed18fff] has been reserved
[    1.071289] system 00:0b: [mem 0xfed19000-0xfed19fff] has been reserved
[    1.071291] system 00:0b: [mem 0xf8000000-0xfbffffff] has been reserved
[    1.071292] system 00:0b: [mem 0xfed20000-0xfed3ffff] has been reserved
[    1.071294] system 00:0b: [mem 0xfed90000-0xfed93fff] has been reserved
[    1.071296] system 00:0b: [mem 0xfed45000-0xfed8ffff] has been reserved
[    1.071298] system 00:0b: [mem 0xff000000-0xffffffff] has been reserved
[    1.071300] system 00:0b: [mem 0xfee00000-0xfeefffff] could not be reserved
[    1.071302] system 00:0b: [mem 0xdfa00000-0xdfa00fff] has been reserved
[    1.071304] system 00:0b: Plug and Play ACPI device, IDs PNP0c02 (active)
[    1.072587] pnp: PnP ACPI: found 12 devices
[    1.072588] ACPI: ACPI bus type pnp unregistered
[    1.078004] PCI: max bus depth: 1 pci_try_num: 2
[    1.078029] pci 0000:00:1c.0: PCI bridge to [bus 01-01]
[    1.078031] pci 0000:00:1c.0:   bridge window [io  disabled]
[    1.078035] pci 0000:00:1c.0:   bridge window [mem disabled]
[    1.078039] pci 0000:00:1c.0:   bridge window [mem pref disabled]
[    1.078045] pci 0000:00:1c.2: PCI bridge to [bus 02-02]
[    1.078046] pci 0000:00:1c.2:   bridge window [io  disabled]
[    1.078051] pci 0000:00:1c.2:   bridge window [mem 0xf7d00000-0xf7dfffff]
[    1.078054] pci 0000:00:1c.2:   bridge window [mem pref disabled]
[    1.078060] pci 0000:00:1c.3: PCI bridge to [bus 03-03]
[    1.078062] pci 0000:00:1c.3:   bridge window [io  0xe000-0xefff]
[    1.078067] pci 0000:00:1c.3:   bridge window [mem 0xf7c00000-0xf7cfffff]
[    1.078071] pci 0000:00:1c.3:   bridge window [mem pref disabled]
[    1.078088] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.078092] pci 0000:00:1c.0: setting latency timer to 64
[    1.078101] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.078104] pci 0000:00:1c.2: setting latency timer to 64
[    1.078113] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    1.078116] pci 0000:00:1c.3: setting latency timer to 64
[    1.078120] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    1.078122] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    1.078123] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    1.078125] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000d3fff]
[    1.078127] pci_bus 0000:00: resource 8 [mem 0x000d4000-0x000d7fff]
[    1.078128] pci_bus 0000:00: resource 9 [mem 0x000d8000-0x000dbfff]
[    1.078130] pci_bus 0000:00: resource 10 [mem 0x000dc000-0x000dffff]
[    1.078132] pci_bus 0000:00: resource 11 [mem 0x000e0000-0x000e3fff]
[    1.078133] pci_bus 0000:00: resource 12 [mem 0x000e4000-0x000e7fff]
[    1.078135] pci_bus 0000:00: resource 13 [mem 0xdfa00000-0xfeafffff]
[    1.078137] pci_bus 0000:00: resource 14 [mem 0xfed40000-0xfed44fff]
[    1.078139] pci_bus 0000:02: resource 1 [mem 0xf7d00000-0xf7dfffff]
[    1.078140] pci_bus 0000:03: resource 0 [io  0xe000-0xefff]
[    1.078142] pci_bus 0000:03: resource 1 [mem 0xf7c00000-0xf7cfffff]
[    1.078163] NET: Registered protocol family 2
[    1.078362] IP route cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    1.079227] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    1.080407] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    1.080531] TCP: Hash tables configured (established 524288 bind 65536)
[    1.080533] TCP reno registered
[    1.080546] UDP hash table entries: 4096 (order: 5, 131072 bytes)
[    1.080579] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
[    1.080659] NET: Registered protocol family 1
[    1.080671] pci 0000:00:02.0: Boot video device
[    1.080767] PCI: CLS 64 bytes, default 64
[    1.080771] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    1.080773] Placing 64MB software IO TLB between ffff8800d6535000 - ffff8800da535000
[    1.080775] software IO TLB at phys 0xd6535000 - 0xda535000
[    1.081144] audit: initializing netlink socket (disabled)
[    1.081155] type=2000 audit(1334019976.900:1): initialized
[    1.108066] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.124706] VFS: Disk quotas dquot_6.5.2
[    1.124746] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.125169] fuse init (API version 7.16)
[    1.125230] msgmni has been set to 15812
[    1.125499] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    1.125519] io scheduler noop registered
[    1.125521] io scheduler deadline registered
[    1.125547] io scheduler cfq registered (default)
[    1.125749] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.125764] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.125793] intel_idle: MWAIT substates: 0x21120
[    1.125795] intel_idle: v0.4 model 0x2A
[    1.125796] intel_idle: lapic_timer_reliable_states 0xffffffff
[    1.126960] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    1.127852] ACPI: AC Adapter [ADP0] (off-line)
[    1.127924] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    1.127929] ACPI: Power Button [PWRB]
[    1.127955] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1
[    1.127958] ACPI: Sleep Button [SLPB]
[    1.127983] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input2
[    1.132772] ACPI: Lid Switch [LID0]
[    1.132802] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    1.132804] ACPI: Power Button [PWRF]
[    1.132824] ACPI: acpi_idle yielding to intel_idle
[    1.139520] thermal LNXTHERM:00: registered as thermal_zone0
[    1.139522] ACPI: Thermal Zone [TZ0] (25 C)
[    1.139539] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    1.139550] ERST: Table is not found!
[    1.139588] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.149155] ACPI: Battery Slot [BAT0] (battery present)
[    1.329983] Linux agpgart interface v0.103
[    1.330043] agpgart-intel 0000:00:00.0: Intel Sandybridge Chipset
[    1.330170] agpgart-intel 0000:00:00.0: detected gtt size: 2097152K total, 262144K mappable
[    1.331276] agpgart-intel 0000:00:00.0: detected 65536K stolen memory
[    1.331362] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xe0000000
[    1.332048] brd: module loaded
[    1.332356] loop: module loaded
[    1.332631] Fixed MDIO Bus: probed
[    1.332645] PPP generic driver version 2.4.2
[    1.332666] tun: Universal TUN/TAP device driver, 1.6
[    1.332668] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.332717] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.332731] ehci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.332746] ehci_hcd 0000:00:1a.0: setting latency timer to 64
[    1.332749] ehci_hcd 0000:00:1a.0: EHCI Host Controller
[    1.332773] ehci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    1.332796] ehci_hcd 0000:00:1a.0: debug port 2
[    1.336674] ehci_hcd 0000:00:1a.0: cache line size of 64 is not supported
[    1.336689] ehci_hcd 0000:00:1a.0: irq 16, io mem 0xf7e08000
[    1.349603] ehci_hcd 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    1.349766] hub 1-0:1.0: USB hub found
[    1.349770] hub 1-0:1.0: 2 ports detected
[    1.349818] ehci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.349828] ehci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.349831] ehci_hcd 0000:00:1d.0: EHCI Host Controller
[    1.349857] ehci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.349876] ehci_hcd 0000:00:1d.0: debug port 2
[    1.353742] ehci_hcd 0000:00:1d.0: cache line size of 64 is not supported
[    1.353752] ehci_hcd 0000:00:1d.0: irq 23, io mem 0xf7e07000
[    1.369576] ehci_hcd 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    1.369727] hub 2-0:1.0: USB hub found
[    1.369729] hub 2-0:1.0: 2 ports detected
[    1.369765] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.369774] uhci_hcd: USB Universal Host Controller Interface driver
[    1.369814] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    1.372379] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.372440] mousedev: PS/2 mouse device common for all mice
[    1.372593] rtc_cmos 00:05: RTC can wake from S4
[    1.372675] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    1.372699] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    1.372770] device-mapper: uevent: version 1.0.3
[    1.372819] device-mapper: ioctl: 4.20.0-ioctl (2011-02-02) initialised: [email]dm-devel@redhat.com[/email]
[    1.372910] cpuidle: using governor ladder
[    1.373036] cpuidle: using governor menu
[    1.373037] EFI Variables Facility v0.08 2004-May-17
[    1.373752] TCP cubic registered
[    1.373871] NET: Registered protocol family 10
[    1.374195] NET: Registered protocol family 17
[    1.374205] Registering the dns_resolver key type
[    1.374273] PM: Hibernation image not present or could not be loaded.
[    1.374283] registered taskstats version 1
[    1.381592] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    1.387113]   Magic number: 8:903:103
[    1.387189] rtc_cmos 00:05: setting system clock to 2012-04-10 01:06:18 UTC (1334019978)
[    1.387700] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.387701] EDD information not available.
[    1.388752] Freeing unused kernel memory: 988k freed
[    1.388843] Write protecting the kernel read-only data: 12288k
[    1.392800] Freeing unused kernel memory: 2032k freed
[    1.395696] Freeing unused kernel memory: 1388k freed
[    1.406689] udevd[87]: starting version 173
[    1.423226] Btrfs loaded
[    1.436949] xor: automatically using best checksumming function: generic_sse
[    1.439029] sdhci: Secure Digital Host Controller Interface driver
[    1.439031] sdhci: Copyright(c) Pierre Ossman
[    1.439245] sdhci-pci 0000:03:00.1: SDHCI controller found [197b:2392] (rev 90)
[    1.439263] sdhci-pci 0000:03:00.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    1.439302] sdhci-pci 0000:03:00.1: setting latency timer to 64
[    1.439313] mmc0: no vmmc regulator found
[    1.439339] Registered led device: mmc0::
[    1.439375] mmc0: SDHCI controller on PCI [0000:03:00.1] using DMA
[    1.439384] sdhci-pci 0000:03:00.2: SDHCI controller found [197b:2391] (rev 90)
[    1.439397] sdhci-pci 0000:03:00.2: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    1.439401] sdhci-pci 0000:03:00.2: Refusing to bind to secondary interface.
[    1.439408] sdhci-pci 0000:03:00.2: PCI INT B disabled
[    1.440184] jme: JMicron JMC2XX ethernet driver version 1.0.8
[    1.440217] jme 0000:03:00.0: PCI INT C -> GSI 17 (level, low) -> IRQ 17
[    1.440227] jme 0000:03:00.0: setting latency timer to 64
[    1.441294] jme 0000:03:00.0: eth0: JMC250 Gigabit Ethernet chiprev:35 pcirev:5 macaddr:00:90:f5:c6:44:48
[    1.445181] ahci 0000:00:1f.2: version 3.0
[    1.445194] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.445241] ahci 0000:00:1f.2: irq 42 for MSI/MSI-X
[    1.453458]    generic_sse:  9941.000 MB/sec
[    1.453461] xor: using function: generic_sse (9941.000 MB/sec)
[    1.455001] device-mapper: dm-raid45: initialized v0.2594b
[    1.457476] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 6 Gbps 0x5 impl SATA mode
[    1.457481] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part ems apst 
[    1.457486] ahci 0000:00:1f.2: setting latency timer to 64
[    1.466000] scsi0 : ahci
[    1.466134] scsi1 : ahci
[    1.466253] scsi2 : ahci
[    1.466393] scsi3 : ahci
[    1.466472] scsi4 : ahci
[    1.466568] scsi5 : ahci
[    1.466693] ata1: SATA max UDMA/133 abar m2048@0xf7e06000 port 0xf7e06100 irq 42
[    1.466695] ata2: DUMMY
[    1.466696] ata3: SATA max UDMA/133 abar m2048@0xf7e06000 port 0xf7e06200 irq 42
[    1.466698] ata4: DUMMY
[    1.466698] ata5: DUMMY
[    1.466699] ata6: DUMMY
[    1.661247] usb 1-1: new high speed USB device number 2 using ehci_hcd
[    1.785090] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.788592] ata3.00: ATAPI: TSSTcorp CDDVDW TS-L633F, TM00, max UDMA/100
[    1.793081] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.793133] ata3.00: configured for UDMA/100
[    1.793677] hub 1-1:1.0: USB hub found
[    1.793772] hub 1-1:1.0: 6 ports detected
[    1.829840] ata1.00: ATA-8: ST9500420AS, 0002SDM1, max UDMA/133
[    1.829849] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    1.831936] ata1.00: configured for UDMA/133
[    1.832143] scsi 0:0:0:0: Direct-Access     ATA      ST9500420AS      0002 PQ: 0 ANSI: 5
[    1.832237] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.832248] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    1.832292] sd 0:0:0:0: [sda] Write Protect is off
[    1.832294] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.832306] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.834480] scsi 2:0:0:0: CD-ROM            TSSTcorp CDDVDW TS-L633F  TM00 PQ: 0 ANSI: 5
[    1.839288] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.839297] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.839447] sr 2:0:0:0: Attached scsi CD-ROM sr0
[    1.839506] sr 2:0:0:0: Attached scsi generic sg1 type 5
[    1.868933]  sda: sda1 sda2 < sda5 >
[    1.869216] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.904923] usb 2-1: new high speed USB device number 2 using ehci_hcd
[    2.037359] hub 2-1:1.0: USB hub found
[    2.037451] hub 2-1:1.0: 6 ports detected
[    2.076686] Refined TSC clocksource calibration: 2494.333 MHz.
[    2.076698] Switching to clocksource tsc
[    2.308545] usb 2-1.6: new high speed USB device number 3 using ehci_hcd
[    2.436556] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[   60.143501] ata1.00: exception Emask 0x0 SAct 0x1 SErr 0x0 action 0x0
[   60.143509] ata1.00: irq_stat 0x40000008
[   60.143516] ata1.00: failed command: READ FPDMA QUEUED
[   60.143529] ata1.00: cmd 60/08:00:84:28:84/00:00:0a:00:00/40 tag 0 ncq 4096 in
[   60.143532]          res 41/40:08:86:28:84/00:00:0a:00:00/00 Emask 0x409 (media error) <F>
[   60.143538] ata1.00: status: { DRDY ERR }
[   60.143542] ata1.00: error: { UNC }
[   60.160742] ata1.00: configured for UDMA/133
[   60.160765] ata1: EH complete
[  111.040267] udevd[333]: starting version 173
[  111.074992] mei: module is from the staging directory, the quality is unknown, you have been warned.
[  111.075266] mei 0000:00:16.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[  111.075272] mei 0000:00:16.0: setting latency timer to 64
[  111.079872] [drm] Initialized drm 1.1.0 20060810
[  111.081008] lp: driver loaded but no devices found
[  111.088004] jmb38x_ms 0000:03:00.3: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[  111.088012] jmb38x_ms 0000:03:00.3: setting latency timer to 64
[  111.095863] cfg80211: Calling CRDA to update world regulatory domain
[  111.095906] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[  111.095910] i915 0000:00:02.0: setting latency timer to 64
[  111.111280] type=1400 audit(1334020088.361:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=409 comm="apparmor_parser"
[  111.111600] type=1400 audit(1334020088.365:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=409 comm="apparmor_parser"
[  111.111805] type=1400 audit(1334020088.365:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=409 comm="apparmor_parser"
[  111.115930] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[  111.115933] iwlagn: Copyright(c) 2003-2011 Intel Corporation
[  111.116042] iwlagn 0000:02:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[  111.116072] iwlagn 0000:02:00.0: setting latency timer to 64
[  111.116165] iwlagn 0000:02:00.0: Detected Intel(R) Centrino(R) Advanced-N 6230 AGN, REV=0xB0
[  111.131535] iwlagn 0000:02:00.0: device EEPROM VER=0x716, CALIB=0x6
[  111.131537] iwlagn 0000:02:00.0: Device SKU: 0Xb
[  111.131539] iwlagn 0000:02:00.0: Valid Tx ant: 0X3, Valid Rx ant: 0X3
[  111.132083] iwlagn 0000:02:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[  111.132208] iwlagn 0000:02:00.0: irq 43 for MSI/MSI-X
[  111.149613] Adding 7725444k swap on /dev/sda5.  Priority:-1 extents:1 across:7725444k 
[  111.181239] i915 0000:00:02.0: irq 44 for MSI/MSI-X
[  111.181245] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[  111.181246] [drm] Driver supports precise vblank timestamp query.
[  111.181278] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[  111.184924] wmi: Mapper loaded
[  111.232462] cfg80211: World regulatory domain updated:
[  111.232465] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  111.232468] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  111.232471] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  111.232473] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  111.232476] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  111.232478] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  111.273921] iwlagn 0000:02:00.0: loaded firmware version 17.168.5.1 build 33993
[  111.274066] Registered led device: phy0-led
[  111.274089] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[  111.276328] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[  111.321031] Linux video capture interface: v2.00
[  111.321439] uvcvideo: Found UVC 1.00 device BisonCam, NB Pro (5986:0315)
[  111.360197] input: BisonCam, NB Pro as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.0/input/input5
[  111.360255] usbcore: registered new interface driver uvcvideo
[  111.360257] USB Video Class driver (v1.1.0)
[  111.414860] fbcon: inteldrmfb (fb0) is primary device
[  111.570665] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[  111.585700] Console: switching to colour frame buffer device 170x48
[  111.587523] fb0: inteldrmfb frame buffer device
[  111.587524] drm: registered panic notifier
[  111.602704] ACPI Warning: _BQC returned an invalid level (20110413/video-473)
[  111.602758] acpi device:46: registered as cooling_device4
[  111.602821] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input6
[  111.602869] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[  111.602921] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[  111.602992] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[  111.603048] HDA Intel 0000:00:1b.0: irq 45 for MSI/MSI-X
[  111.603065] HDA Intel 0000:00:1b.0: setting latency timer to 64
[  111.979861] type=1400 audit(1334020089.233:5): apparmor="STATUS" operation="profile_load" name="/opt/extras.ubuntu.com/unity-lens-askubuntu/unity-askubuntu-daemon" pid=919 comm="apparmor_parser"
[  111.981643] type=1400 audit(1334020089.233:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm-guest-session-wrapper" pid=918 comm="apparmor_parser"
[  111.984134] type=1400 audit(1334020089.237:7): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=921 comm="apparmor_parser"
[  111.984608] type=1400 audit(1334020089.237:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=923 comm="apparmor_parser"
[  111.985452] type=1400 audit(1334020089.237:9): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=920 comm="apparmor_parser"
[  111.985784] type=1400 audit(1334020089.237:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=920 comm="apparmor_parser"
[  111.985992] type=1400 audit(1334020089.237:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=920 comm="apparmor_parser"
[  112.074090] init: failsafe main process (861) killed by TERM signal
[  112.075005] init: apport pre-start process (955) terminated with status 1
[  112.075496] init: alsa-restore main process (962) terminated with status 19
[  112.087311] init: apport post-stop process (987) terminated with status 1
[  112.148953] hda_codec: ALC269VB: BIOS auto-probing.
[  112.154459] HDMI status: Pin=6 Presence_Detect=0 ELD_Valid=0
[  112.154612] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[  112.154768] input: HDA Intel PCH Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[  112.154823] input: HDA Intel PCH Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9


DOUBLE EDIT- trackpad works randomly again..  Only difference is my power cord is plugged in.

---

### Post by isantop on 2012-04-10
> **jgammel25 said:**
> boot.log


dmesg


DOUBLE EDIT- trackpad works randomly again..  Only difference is my power cord is plugged in.

That is abnormally long. It looks like it's hanging up while loading the Kernel or getting out of Grub. I would try running these commands from a terminal:

```
sudo grub-install --force /dev/sda
sudo update-grub
```

This will reinstall the bootloader into the MBR of the primary hard disk, then make sure all of the entries are up to date.

---

### Post by jgammel25 on 2012-04-10
After running those commands, I restarted and there was no change in the boot time.  Here are the logs:

boot.log
> fsck from util-linux 2.19.1
/dev/sda1 has been mounted 24 times without being checked, check forced.
/dev/sda1: 241755/30048256 files (0.2% non-contiguous), 7052517/120165014 blocks
Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
 * Starting AppArmor profiles                                                  [ OK ]
speech-dispatcher disabled; edit /etc/default/speech-dispatcher
Checking for running unattended-upgrades: 
 * Stopping Failsafe Boot Delay                                                [ OK ]
 * Stopping System V initialisation compatibility                              [ OK ]
 * Starting System V runlevel compatibility                                    [ OK ]
 * Stopping automatic crash report generation                                  [fail]
 * Starting deferred execution scheduler                                       [ OK ]
 * Starting regular background program processing daemon                       [ OK ]
 * Starting LightDM Display Manager                                            [ OK ]
 * Starting ACPI daemon                                                        [ OK ]
 * Starting anac(h)ronistic cron                                               [ OK ]
 * Starting save kernel messages                                               [ OK ]
 * Starting CPU interrupts balancing daemon                                    [ OK ]


dmesg
> [    1.074753] pnp 00:00: [mem 0x000c0000-0x000c3fff window]
[    1.074756] pnp 00:00: [mem 0x000c4000-0x000c7fff window]
[    1.074757] pnp 00:00: [mem 0x000c8000-0x000cbfff window]
[    1.074759] pnp 00:00: [mem 0x000cc000-0x000cffff window]
[    1.074761] pnp 00:00: [mem 0x000d0000-0x000d3fff window]
[    1.074762] pnp 00:00: [mem 0x000d4000-0x000d7fff window]
[    1.074764] pnp 00:00: [mem 0x000d8000-0x000dbfff window]
[    1.074765] pnp 00:00: [mem 0x000dc000-0x000dffff window]
[    1.074767] pnp 00:00: [mem 0x000e0000-0x000e3fff window]
[    1.074768] pnp 00:00: [mem 0x000e4000-0x000e7fff window]
[    1.074770] pnp 00:00: [mem 0x000e8000-0x000ebfff window]
[    1.074771] pnp 00:00: [mem 0x000ec000-0x000effff window]
[    1.074773] pnp 00:00: [mem 0x000f0000-0x000fffff window]
[    1.074774] pnp 00:00: [mem 0xdfa00000-0xfeafffff window]
[    1.074776] pnp 00:00: [mem 0xfed40000-0xfed44fff window]
[    1.074835] pnp 00:00: Plug and Play ACPI device, IDs PNP0a08 PNP0a03 (active)
[    1.074845] pnp 00:01: [io  0x0000-0x001f]
[    1.074846] pnp 00:01: [io  0x0081-0x0091]
[    1.074847] pnp 00:01: [io  0x0093-0x009f]
[    1.074849] pnp 00:01: [io  0x00c0-0x00df]
[    1.074851] pnp 00:01: [dma 4]
[    1.074865] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
[    1.074871] pnp 00:02: [mem 0xff000000-0xffffffff]
[    1.074886] pnp 00:02: Plug and Play ACPI device, IDs INT0800 (active)
[    1.074946] pnp 00:03: [mem 0xfed00000-0xfed003ff]
[    1.074960] pnp 00:03: Plug and Play ACPI device, IDs PNP0103 (active)
[    1.074970] pnp 00:04: [io  0x002e-0x002f]
[    1.074971] pnp 00:04: [io  0x004e-0x004f]
[    1.074972] pnp 00:04: [io  0x0061]
[    1.074974] pnp 00:04: [io  0x0063]
[    1.074975] pnp 00:04: [io  0x0065]
[    1.074976] pnp 00:04: [io  0x0067]
[    1.074977] pnp 00:04: [io  0x0070]
[    1.074979] pnp 00:04: [io  0x0080]
[    1.074980] pnp 00:04: [io  0x0092]
[    1.074981] pnp 00:04: [io  0x00b2-0x00b3]
[    1.074982] pnp 00:04: [io  0x0680-0x069f]
[    1.074984] pnp 00:04: [io  0x0200-0x020f]
[    1.074985] pnp 00:04: [io  0xffff]
[    1.074986] pnp 00:04: [io  0xffff]
[    1.074987] pnp 00:04: [io  0x0400-0x0453]
[    1.074989] pnp 00:04: [io  0x0458-0x047f]
[    1.074990] pnp 00:04: [io  0x0500-0x057f]
[    1.074991] pnp 00:04: [io  0x164e-0x164f]
[    1.075027] system 00:04: [io  0x0680-0x069f] has been reserved
[    1.075029] system 00:04: [io  0x0200-0x020f] has been reserved
[    1.075031] system 00:04: [io  0xffff] has been reserved
[    1.075033] system 00:04: [io  0xffff] has been reserved
[    1.075034] system 00:04: [io  0x0400-0x0453] has been reserved
[    1.075036] system 00:04: [io  0x0458-0x047f] has been reserved
[    1.075038] system 00:04: [io  0x0500-0x057f] has been reserved
[    1.075040] system 00:04: [io  0x164e-0x164f] has been reserved
[    1.075042] system 00:04: Plug and Play ACPI device, IDs PNP0c02 (active)
[    1.075049] pnp 00:05: [io  0x0070-0x0077]
[    1.075059] pnp 00:05: [irq 8]
[    1.075074] pnp 00:05: Plug and Play ACPI device, IDs PNP0b00 (active)
[    1.075094] pnp 00:06: [io  0x0454-0x0457]
[    1.075118] system 00:06: [io  0x0454-0x0457] has been reserved
[    1.075120] system 00:06: Plug and Play ACPI device, IDs INT3f0d PNP0c02 (active)
[    1.075139] pnp 00:07: [io  0x0010-0x001f]
[    1.075141] pnp 00:07: [io  0x0022-0x003f]
[    1.075142] pnp 00:07: [io  0x0044-0x005f]
[    1.075143] pnp 00:07: [io  0x0072-0x007f]
[    1.075144] pnp 00:07: [io  0x0080]
[    1.075146] pnp 00:07: [io  0x0084-0x0086]
[    1.075147] pnp 00:07: [io  0x0088]
[    1.075148] pnp 00:07: [io  0x008c-0x008e]
[    1.075149] pnp 00:07: [io  0x0090-0x009f]
[    1.075151] pnp 00:07: [io  0x00a2-0x00bf]
[    1.075152] pnp 00:07: [io  0x00e0-0x00ef]
[    1.075153] pnp 00:07: [io  0x04d0-0x04d1]
[    1.075180] system 00:07: [io  0x04d0-0x04d1] has been reserved
[    1.075182] system 00:07: Plug and Play ACPI device, IDs PNP0c02 (active)
[    1.075188] pnp 00:08: [io  0x00f0-0x00ff]
[    1.075194] pnp 00:08: [irq 13]
[    1.075209] pnp 00:08: Plug and Play ACPI device, IDs PNP0c04 (active)
[    1.075227] pnp 00:09: [io  0x0060]
[    1.075228] pnp 00:09: [io  0x0064]
[    1.075234] pnp 00:09: [irq 1]
[    1.075252] pnp 00:09: Plug and Play ACPI device, IDs PNP0303 PNP030b (active)
[    1.075286] pnp 00:0a: [irq 12]
[    1.075302] pnp 00:0a: Plug and Play ACPI device, IDs PNP0f13 PNP0f03 (active)
[    1.075474] pnp 00:0b: [mem 0xfed1c000-0xfed1ffff]
[    1.075476] pnp 00:0b: [mem 0xfed10000-0xfed17fff]
[    1.075477] pnp 00:0b: [mem 0xfed18000-0xfed18fff]
[    1.075479] pnp 00:0b: [mem 0xfed19000-0xfed19fff]
[    1.075480] pnp 00:0b: [mem 0xf8000000-0xfbffffff]
[    1.075482] pnp 00:0b: [mem 0xfed20000-0xfed3ffff]
[    1.075483] pnp 00:0b: [mem 0xfed90000-0xfed93fff]
[    1.075484] pnp 00:0b: [mem 0xfed45000-0xfed8ffff]
[    1.075486] pnp 00:0b: [mem 0xff000000-0xffffffff]
[    1.075487] pnp 00:0b: [mem 0xfee00000-0xfeefffff]
[    1.075489] pnp 00:0b: [mem 0xdfa00000-0xdfa00fff]
[    1.075529] system 00:0b: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    1.075531] system 00:0b: [mem 0xfed10000-0xfed17fff] has been reserved
[    1.075533] system 00:0b: [mem 0xfed18000-0xfed18fff] has been reserved
[    1.075535] system 00:0b: [mem 0xfed19000-0xfed19fff] has been reserved
[    1.075537] system 00:0b: [mem 0xf8000000-0xfbffffff] has been reserved
[    1.075539] system 00:0b: [mem 0xfed20000-0xfed3ffff] has been reserved
[    1.075540] system 00:0b: [mem 0xfed90000-0xfed93fff] has been reserved
[    1.075542] system 00:0b: [mem 0xfed45000-0xfed8ffff] has been reserved
[    1.075544] system 00:0b: [mem 0xff000000-0xffffffff] has been reserved
[    1.075546] system 00:0b: [mem 0xfee00000-0xfeefffff] could not be reserved
[    1.075548] system 00:0b: [mem 0xdfa00000-0xdfa00fff] has been reserved
[    1.075551] system 00:0b: Plug and Play ACPI device, IDs PNP0c02 (active)
[    1.076513] pnp: PnP ACPI: found 12 devices
[    1.076522] ACPI: ACPI bus type pnp unregistered
[    1.082037] PCI: max bus depth: 1 pci_try_num: 2
[    1.082062] pci 0000:00:1c.0: PCI bridge to [bus 01-01]
[    1.082064] pci 0000:00:1c.0:   bridge window [io  disabled]
[    1.082068] pci 0000:00:1c.0:   bridge window [mem disabled]
[    1.082072] pci 0000:00:1c.0:   bridge window [mem pref disabled]
[    1.082078] pci 0000:00:1c.2: PCI bridge to [bus 02-02]
[    1.082079] pci 0000:00:1c.2:   bridge window [io  disabled]
[    1.082084] pci 0000:00:1c.2:   bridge window [mem 0xf7d00000-0xf7dfffff]
[    1.082087] pci 0000:00:1c.2:   bridge window [mem pref disabled]
[    1.082093] pci 0000:00:1c.3: PCI bridge to [bus 03-03]
[    1.082095] pci 0000:00:1c.3:   bridge window [io  0xe000-0xefff]
[    1.082100] pci 0000:00:1c.3:   bridge window [mem 0xf7c00000-0xf7cfffff]
[    1.082103] pci 0000:00:1c.3:   bridge window [mem pref disabled]
[    1.082121] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.082125] pci 0000:00:1c.0: setting latency timer to 64
[    1.082134] pci 0000:00:1c.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    1.082138] pci 0000:00:1c.2: setting latency timer to 64
[    1.082146] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    1.082150] pci 0000:00:1c.3: setting latency timer to 64
[    1.082153] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    1.082155] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    1.082157] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    1.082158] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000d3fff]
[    1.082160] pci_bus 0000:00: resource 8 [mem 0x000d4000-0x000d7fff]
[    1.082162] pci_bus 0000:00: resource 9 [mem 0x000d8000-0x000dbfff]
[    1.082163] pci_bus 0000:00: resource 10 [mem 0x000dc000-0x000dffff]
[    1.082165] pci_bus 0000:00: resource 11 [mem 0x000e0000-0x000e3fff]
[    1.082167] pci_bus 0000:00: resource 12 [mem 0x000e4000-0x000e7fff]
[    1.082168] pci_bus 0000:00: resource 13 [mem 0xdfa00000-0xfeafffff]
[    1.082170] pci_bus 0000:00: resource 14 [mem 0xfed40000-0xfed44fff]
[    1.082172] pci_bus 0000:02: resource 1 [mem 0xf7d00000-0xf7dfffff]
[    1.082179] pci_bus 0000:03: resource 0 [io  0xe000-0xefff]
[    1.082180] pci_bus 0000:03: resource 1 [mem 0xf7c00000-0xf7cfffff]
[    1.082202] NET: Registered protocol family 2
[    1.082400] IP route cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    1.083278] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    1.084466] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    1.084591] TCP: Hash tables configured (established 524288 bind 65536)
[    1.084593] TCP reno registered
[    1.084607] UDP hash table entries: 4096 (order: 5, 131072 bytes)
[    1.084639] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
[    1.084721] NET: Registered protocol family 1
[    1.084732] pci 0000:00:02.0: Boot video device
[    1.084831] PCI: CLS 64 bytes, default 64
[    1.084835] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    1.084837] Placing 64MB software IO TLB between ffff8800d6535000 - ffff8800da535000
[    1.084838] software IO TLB at phys 0xd6535000 - 0xda535000
[    1.085212] audit: initializing netlink socket (disabled)
[    1.085223] type=2000 audit(1334076820.908:1): initialized
[    1.112118] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.128747] VFS: Disk quotas dquot_6.5.2
[    1.128788] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.129210] fuse init (API version 7.16)
[    1.129270] msgmni has been set to 15812
[    1.129571] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    1.129593] io scheduler noop registered
[    1.129595] io scheduler deadline registered
[    1.129622] io scheduler cfq registered (default)
[    1.129824] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.129839] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.129868] intel_idle: MWAIT substates: 0x21120
[    1.129870] intel_idle: v0.4 model 0x2A
[    1.129871] intel_idle: lapic_timer_reliable_states 0xffffffff
[    1.130876] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    1.131758] ACPI: AC Adapter [ADP0] (on-line)
[    1.131830] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    1.131835] ACPI: Power Button [PWRB]
[    1.131860] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1
[    1.131863] ACPI: Sleep Button [SLPB]
[    1.131888] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input2
[    1.133679] ACPI: Lid Switch [LID0]
[    1.133708] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
[    1.133711] ACPI: Power Button [PWRF]
[    1.133730] ACPI: acpi_idle yielding to intel_idle
[    1.140988] thermal LNXTHERM:00: registered as thermal_zone0
[    1.140991] ACPI: Thermal Zone [TZ0] (56 C)
[    1.141008] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    1.141019] ERST: Table is not found!
[    1.141058] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.151373] ACPI: Battery Slot [BAT0] (battery present)
[    1.342220] Linux agpgart interface v0.103
[    1.342281] agpgart-intel 0000:00:00.0: Intel Sandybridge Chipset
[    1.342407] agpgart-intel 0000:00:00.0: detected gtt size: 2097152K total, 262144K mappable
[    1.343514] agpgart-intel 0000:00:00.0: detected 65536K stolen memory
[    1.343604] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xe0000000
[    1.344295] brd: module loaded
[    1.344604] loop: module loaded
[    1.344885] Fixed MDIO Bus: probed
[    1.344899] PPP generic driver version 2.4.2
[    1.344920] tun: Universal TUN/TAP device driver, 1.6
[    1.344921] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.344971] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.344986] ehci_hcd 0000:00:1a.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.345000] ehci_hcd 0000:00:1a.0: setting latency timer to 64
[    1.345004] ehci_hcd 0000:00:1a.0: EHCI Host Controller
[    1.345028] ehci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    1.345051] ehci_hcd 0000:00:1a.0: debug port 2
[    1.348929] ehci_hcd 0000:00:1a.0: cache line size of 64 is not supported
[    1.348943] ehci_hcd 0000:00:1a.0: irq 16, io mem 0xf7e08000
[    1.361834] ehci_hcd 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    1.361998] hub 1-0:1.0: USB hub found
[    1.362002] hub 1-0:1.0: 2 ports detected
[    1.362048] ehci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[    1.362058] ehci_hcd 0000:00:1d.0: setting latency timer to 64
[    1.362061] ehci_hcd 0000:00:1d.0: EHCI Host Controller
[    1.362087] ehci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.362106] ehci_hcd 0000:00:1d.0: debug port 2
[    1.365997] ehci_hcd 0000:00:1d.0: cache line size of 64 is not supported
[    1.366006] ehci_hcd 0000:00:1d.0: irq 23, io mem 0xf7e07000
[    1.381806] ehci_hcd 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    1.381959] hub 2-0:1.0: USB hub found
[    1.381962] hub 2-0:1.0: 2 ports detected
[    1.381998] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.382006] uhci_hcd: USB Universal Host Controller Interface driver
[    1.382046] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[    1.906162] i8042: Detected active multiplexing controller, rev 1.1
[    1.908672] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.908676] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    1.908696] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    1.908709] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    1.908724] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    1.908786] mousedev: PS/2 mouse device common for all mice
[    1.908892] rtc_cmos 00:05: RTC can wake from S4
[    1.908973] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    1.908997] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    1.909065] device-mapper: uevent: version 1.0.3
[    1.909120] device-mapper: ioctl: 4.20.0-ioctl (2011-02-02) initialised: [email]dm-devel@redhat.com[/email]
[    1.909211] cpuidle: using governor ladder
[    1.909337] cpuidle: using governor menu
[    1.909339] EFI Variables Facility v0.08 2004-May-17
[    1.909485] TCP cubic registered
[    1.909568] NET: Registered protocol family 10
[    1.909867] NET: Registered protocol family 17
[    1.909877] Registering the dns_resolver key type
[    1.909941] PM: Hibernation image not present or could not be loaded.
[    1.909949] registered taskstats version 1
[    1.919642] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    1.922365]   Magic number: 8:773:893
[    1.922463] rtc_cmos 00:05: setting system clock to 2012-04-10 16:53:42 UTC (1334076822)
[    1.923094] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.923095] EDD information not available.
[    1.924213] Freeing unused kernel memory: 988k freed
[    1.924310] Write protecting the kernel read-only data: 12288k
[    1.928520] Freeing unused kernel memory: 2032k freed
[    1.931402] Freeing unused kernel memory: 1388k freed
[    1.942178] udevd[87]: starting version 173
[    1.956707] Btrfs loaded
[    1.961034] xor: automatically using best checksumming function: generic_sse
[    1.981041]    generic_sse: 11319.000 MB/sec
[    1.981044] xor: using function: generic_sse (11319.000 MB/sec)
[    1.981575] device-mapper: dm-raid45: initialized v0.2594b
[    1.983210] sdhci: Secure Digital Host Controller Interface driver
[    1.983213] sdhci: Copyright(c) Pierre Ossman
[    1.983762] sdhci-pci 0000:03:00.1: SDHCI controller found [197b:2392] (rev 90)
[    1.983782] sdhci-pci 0000:03:00.1: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    1.983820] sdhci-pci 0000:03:00.1: setting latency timer to 64
[    1.983832] mmc0: no vmmc regulator found
[    1.983860] Registered led device: mmc0::
[    1.983895] mmc0: SDHCI controller on PCI [0000:03:00.1] using DMA
[    1.983904] sdhci-pci 0000:03:00.2: SDHCI controller found [197b:2391] (rev 90)
[    1.983920] sdhci-pci 0000:03:00.2: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[    1.984087] sdhci-pci 0000:03:00.2: Refusing to bind to secondary interface.
[    1.984095] sdhci-pci 0000:03:00.2: PCI INT B disabled
[    1.986262] ahci 0000:00:1f.2: version 3.0
[    1.986275] ahci 0000:00:1f.2: PCI INT B -> GSI 19 (level, low) -> IRQ 19
[    1.986323] ahci 0000:00:1f.2: irq 42 for MSI/MSI-X
[    1.986863] jme: JMicron JMC2XX ethernet driver version 1.0.8
[    1.986892] jme 0000:03:00.0: PCI INT C -> GSI 17 (level, low) -> IRQ 17
[    1.986902] jme 0000:03:00.0: setting latency timer to 64
[    1.987946] jme 0000:03:00.0: eth0: JMC250 Gigabit Ethernet chiprev:35 pcirev:5 macaddr:00:90:f5:c6:44:48
[    2.001251] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 6 Gbps 0x5 impl SATA mode
[    2.001256] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part ems apst 
[    2.001260] ahci 0000:00:1f.2: setting latency timer to 64
[    2.009303] scsi0 : ahci
[    2.009387] scsi1 : ahci
[    2.009435] scsi2 : ahci
[    2.009481] scsi3 : ahci
[    2.009530] scsi4 : ahci
[    2.009576] scsi5 : ahci
[    2.009683] ata1: SATA max UDMA/133 abar m2048@0xf7e06000 port 0xf7e06100 irq 42
[    2.009685] ata2: DUMMY
[    2.009687] ata3: SATA max UDMA/133 abar m2048@0xf7e06000 port 0xf7e06200 irq 42
[    2.009688] ata4: DUMMY
[    2.009688] ata5: DUMMY
[    2.009689] ata6: DUMMY
[    2.080938] Refined TSC clocksource calibration: 2494.333 MHz.
[    2.080949] Switching to clocksource tsc
[    2.116898] usb 1-1: new high speed USB device number 2 using ehci_hcd
[    2.249358] hub 1-1:1.0: USB hub found
[    2.249447] hub 1-1:1.0: 6 ports detected
[    2.328623] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.332109] ata3.00: ATAPI: TSSTcorp CDDVDW TS-L633F, TM00, max UDMA/100
[    2.334449] ata3.00: configured for UDMA/100
[    2.336619] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.338371] ata1.00: ATA-8: ST9500420AS, 0002SDM1, max UDMA/133
[    2.338380] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    2.340470] ata1.00: configured for UDMA/133
[    2.340713] scsi 0:0:0:0: Direct-Access     ATA      ST9500420AS      0002 PQ: 0 ANSI: 5
[    2.340807] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.340815] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    2.340860] sd 0:0:0:0: [sda] Write Protect is off
[    2.340862] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.340874] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.343241] scsi 2:0:0:0: CD-ROM            TSSTcorp CDDVDW TS-L633F  TM00 PQ: 0 ANSI: 5
[    2.347834] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.347844] cdrom: Uniform CD-ROM driver Revision: 3.20
[    2.347998] sr 2:0:0:0: Attached scsi CD-ROM sr0
[    2.348059] sr 2:0:0:0: Attached scsi generic sg1 type 5
[    2.360589] usb 2-1: new high speed USB device number 2 using ehci_hcd
[    2.400404]  sda: sda1 sda2 < sda5 >
[    2.400713] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.493041] hub 2-1:1.0: USB hub found
[    2.493140] hub 2-1:1.0: 6 ports detected
[    2.564417] usb 1-1.2: new full speed USB device number 3 using ehci_hcd
[    2.663239] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2/1-1.2:1.0/input/input5
[    2.663337] generic-usb 0003:046D:C52F.0001: input,hidraw0: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:1a.0-1.2/input0
[    2.665594] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2/1-1.2:1.1/input/input6
[    2.665721] generic-usb 0003:046D:C52F.0002: input,hiddev0,hidraw1: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1a.0-1.2/input1
[    2.665734] usbcore: registered new interface driver usbhid
[    2.665736] usbhid: USB HID core driver
[    2.764224] usb 2-1.6: new high speed USB device number 3 using ehci_hcd
[    2.959401] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[  106.586245] udevd[340]: starting version 173
[  106.622095] mei: module is from the staging directory, the quality is unknown, you have been warned.
[  106.622382] mei 0000:00:16.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[  106.622388] mei 0000:00:16.0: setting latency timer to 64
[  106.622486] lp: driver loaded but no devices found
[  106.629891] cfg80211: Calling CRDA to update world regulatory domain
[  106.630278] [drm] Initialized drm 1.1.0 20060810
[  106.638010] Adding 7725444k swap on /dev/sda5.  Priority:-1 extents:1 across:7725444k 
[  106.644862] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[  106.644867] i915 0000:00:02.0: setting latency timer to 64
[  106.650322] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[  106.650325] iwlagn: Copyright(c) 2003-2011 Intel Corporation
[  106.650419] iwlagn 0000:02:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[  106.650449] iwlagn 0000:02:00.0: setting latency timer to 64
[  106.650523] iwlagn 0000:02:00.0: Detected Intel(R) Centrino(R) Advanced-N 6230 AGN, REV=0xB0
[  106.653895] jmb38x_ms 0000:03:00.3: PCI INT B -> GSI 16 (level, low) -> IRQ 16
[  106.653923] jmb38x_ms 0000:03:00.3: setting latency timer to 64
[  106.666287] iwlagn 0000:02:00.0: device EEPROM VER=0x716, CALIB=0x6
[  106.666291] iwlagn 0000:02:00.0: Device SKU: 0Xb
[  106.666293] iwlagn 0000:02:00.0: Valid Tx ant: 0X3, Valid Rx ant: 0X3
[  106.666568] iwlagn 0000:02:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[  106.666693] iwlagn 0000:02:00.0: irq 43 for MSI/MSI-X
[  106.683244] type=1400 audit(1334076927.392:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=481 comm="apparmor_parser"
[  106.683540] type=1400 audit(1334076927.392:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=481 comm="apparmor_parser"
[  106.683738] type=1400 audit(1334076927.392:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=481 comm="apparmor_parser"
[  106.707748] wmi: Mapper loaded
[  106.730482] i915 0000:00:02.0: irq 44 for MSI/MSI-X
[  106.730487] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[  106.730489] [drm] Driver supports precise vblank timestamp query.
[  106.730522] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[  106.809685] cfg80211: World regulatory domain updated:
[  106.809688] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  106.809691] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  106.809694] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  106.809696] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  106.809699] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  106.809701] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  106.826973] Linux video capture interface: v2.00
[  106.827446] uvcvideo: Found UVC 1.00 device BisonCam, NB Pro (5986:0315)
[  106.834739] input: BisonCam, NB Pro as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.6/2-1.6:1.0/input/input7
[  106.834799] usbcore: registered new interface driver uvcvideo
[  106.834801] USB Video Class driver (v1.1.0)
[  106.837152] iwlagn 0000:02:00.0: loaded firmware version 17.168.5.1 build 33993
[  106.837309] Registered led device: phy0-led
[  106.837343] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
[  106.840344] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[  107.029238] fbcon: inteldrmfb (fb0) is primary device
[  107.029527] Console: switching to colour frame buffer device 170x48
[  107.029548] fb0: inteldrmfb frame buffer device
[  107.029550] drm: registered panic notifier
[  107.109945] ACPI Error: Current brightness invalid (20110413/video-377)
[  107.110013] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input8
[  107.110070] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[  107.110122] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[  107.110168] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[  107.110235] HDA Intel 0000:00:1b.0: irq 45 for MSI/MSI-X
[  107.110257] HDA Intel 0000:00:1b.0: setting latency timer to 64
[  107.711392] hda_codec: ALC269VB: BIOS auto-probing.
[  107.716882] HDMI status: Pin=6 Presence_Detect=0 ELD_Valid=0
[  107.717040] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[  107.717219] input: HDA Intel PCH Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[  107.717294] input: HDA Intel PCH Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[  107.901577] Synaptics Touchpad, model: 1, fw: 7.2, id: 0x1c0b1, caps: 0xd04733/0xa40000/0xa0000
[  107.952395] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio2/input/input12
[  116.066304] ata1.00: exception Emask 0x0 SAct 0x3 SErr 0x0 action 0x0
[  116.066315] ata1.00: irq_stat 0x40000001
[  116.066322] ata1.00: failed command: READ FPDMA QUEUED
[  116.066335] ata1.00: cmd 60/00:00:4c:1c:c1/01:00:02:00:00/40 tag 0 ncq 131072 in
[  116.066338]          res 41/04:00:3c:1c:c1/00:00:02:00:00/00 Emask 0x1 (device error)
[  116.066344] ata1.00: status: { DRDY ERR }
[  116.066349] ata1.00: error: { ABRT }
[  116.066353] ata1.00: failed command: READ FPDMA QUEUED
[  116.066366] ata1.00: cmd 60/00:08:4c:1b:c1/01:00:02:00:00/40 tag 1 ncq 131072 in
[  116.066368]          res 41/40:00:3c:1c:c1/00:01:02:00:00/00 Emask 0x409 (media error) <F>
[  116.066374] ata1.00: status: { DRDY ERR }
[  116.066378] ata1.00: error: { UNC }
[  116.161360] ata1.00: configured for UDMA/133
[  116.161385] ata1: EH complete
[  130.712663] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[  130.753494] type=1400 audit(1334076951.492:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm-guest-session-wrapper" pid=998 comm="apparmor_parser"
[  130.754836] type=1400 audit(1334076951.496:6): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1002 comm="apparmor_parser"
[  130.755151] type=1400 audit(1334076951.496:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1002 comm="apparmor_parser"
[  130.756053] type=1400 audit(1334076951.496:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1002 comm="apparmor_parser"
[  130.758565] type=1400 audit(1334076951.500:9): apparmor="STATUS" operation="profile_load" name="/opt/extras.ubuntu.com/unity-lens-askubuntu/unity-askubuntu-daemon" pid=1001 comm="apparmor_parser"
[  130.762499] type=1400 audit(1334076951.504:10): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=1003 comm="apparmor_parser"
[  130.762526] type=1400 audit(1334076951.504:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=1011 comm="apparmor_parser"
[  130.762870] type=1400 audit(1334076951.504:12): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/telepathy-*" pid=1011 comm="apparmor_parser"
[  130.763687] type=1400 audit(1334076951.504:13): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=1014 comm="apparmor_parser"
[  130.764061] type=1400 audit(1334076951.504:14): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=1014 comm="apparmor_parser"
[  130.767072] ppdev: user-space parallel port driver
[  130.866381] init: failsafe main process (950) killed by TERM signal
[  130.867104] init: apport pre-start process (1069) terminated with status 1
[  130.880323] init: apport post-stop process (1103) terminated with status 1

---

### Post by jgammel25 on 2012-04-11
At this point I'm wondering if I should just try a fresh install..

The system itself seems to work fine once booted - but I've been beating my head against the desk trying to figure out what's going on with the boot.

Is there a chance the boot issue would persist through a new install?

---

### Post by Paddy Landau on 2012-04-12
If it used to work faster, a fresh installation should work for you (make a full backup first!).

However, if it's not a big deal, just boot the computer a couple of minutes before you need to use it.

---

