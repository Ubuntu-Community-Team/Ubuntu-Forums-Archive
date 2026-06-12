---
title: "After Upgrade to 7.10 new Pangolin lost CD Rom function"
date: 2007-10-20
forum: System76 Support
---

### Post by cwej on 2007-10-20
I upgraded to 7.10 this afternoon -- before doing so I noted report of problem with sound being disabled from other posts; however, followed directions on system76 support site to re-enable repository and reinstall latest driver version (2.11). 
- Sound was found disabled after upgrade, but got sound back by following above directions
- Also found that new CD ROM drive no longer works; (will not open CD/ shows "unable to mount selected volume"
- If anyone else has had this problem, and has solved, please let me know...

Thanks in advance

cwej

---

### Post by newsun on 2007-10-20
I have also just noticed taht my optical drive does not work, nothing is mounted and I don't seem to see anything with fdisk

what were the steps you took to get sound working as I still don't have that?

---

### Post by cwej on 2007-10-20
I just:

a)  downloaded the latest system76 driver (v2.1.1); 
b) re-enabled the repository (re-checked box) , at System -> Administration -> Software Sources --  "Third Party Software" tab, "http://planet76/rpositories/ ./" ;
c) reinstalled the drivers at " System -> Administration -> System 76 driver, "Install Drivers" tab, "Install"

I then rebooted, and the sound worked --- but not the CD ROM drive.

I'm thinking that maybe there needs to be one more round of driver update?

---

### Post by newsun on 2007-10-21
hmm, maybe I will try the sys76 driver again, although, I did that once after reading that there was a 2.1.1 driver. Honestly it was not until I was trying to do some work with virtualbox that I even noticed the optical drive not working.

---

### Post by thomasaaron on 2007-10-22
Put a disk in it that has something on it.

Does it spin up?
Does it give an error message?

---

### Post by ukripper on 2007-10-22
CDROM is automount when you put disk in. 

If it doesn't mount can you post output of following command after putting CD in 
```
dmesg
```

---

### Post by cwej on 2007-10-22
Put a disk in it that has something on it.

Does it spin up?
Does it give an error message?
__________________
HELP ME HELP YOU:
1. What version of Ubuntu are you using? (Ubuntu)
2. What is your System 76 Model Number? Pangolin value (PANv3)
3. What have you already tried? Installing/reinstalling Ubuntu 7.10, reinstalling latest driver v2.1.1

When I put in CDRom it spins, but eventually stops spinning (in ~10-15 sec) and doesn't mount (show icon) -- it's not just an icon issue, because when I search for drive, it simply isn't there; for example, I can put in a CD and select "->Places-> CD/DVD Creator -> (clicking) CD-ROM 1 on left panel, and get back error message: "Unable to mount the selected volume" -- further clicking "Details," I get: "mount: special device /dev/hda does not exist
"

Now, I can select the CDROM drive as a boot device by F12 on start-up. I did this to reinstall Ubuntu 7.04 (wherein the CDROM works again), then from there re-updating to Ubuntu 7.10 (whereupon both sound and the CDROM stop working, but reinstalling the v2.1.1 driver re-enables sound, at least. 

Thanks you for responding -- I don't believe I'm the only one... maybe the subject of a forthcoming driver update?

Cheers, Chuck

I actually

---

### Post by cwej on 2007-10-22
I may not have correctly answered my Pangolin Value model number - appears to be FL 91, if that makes sense...that's the only number list directly following the word "Model: " on the bottom of the laptop...

---

### Post by newsun on 2007-10-22
I have basically the same deal, drive opens and spins up, is not seen by gutsy

---

### Post by Karti on 2007-10-22
Ah well, I don't have a Pangolin, but same issues on 7.10 and 7.04 with full upgrades. I had dvd play etc, but now I only get the images as seeing blank cds, and if I mount it I am told its read only

Just thought I would join a thread I am keeping an eye on

K
;)

---

### Post by newsun on 2007-10-22
karti, if you can mount and it is read only, you may just have a permission issue with the group your optical drive is being mounted to. I bet you could change the group to disk and you would then have access to it.

For me I don't even have the drive recognized to try and mount it.

---

### Post by cwej on 2007-10-22
Responding to ukripper, the following is output of dmesg:

[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:bec00000)
[    0.000000] Built 1 zonelists.  Total pages: 257763
[    0.000000] Kernel command line: root=UUID=b489c754-c593-45a1-a22f-9d6242dbf1a7 ro quiet splash
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 1995.145 MHz processor.
[   15.011106] Console: colour VGA+ 80x25
[   15.011475] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   15.011779] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   15.032412] Memory: 1018300k/1039168k available (2015k kernel code, 20192k reserved, 916k data, 364k init, 121664k highmem)
[   15.032419] virtual kernel memory layout:
[   15.032420]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   15.032421]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   15.032422]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   15.032423]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   15.032423]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[   15.032424]       .data : 0xc02f7d26 - 0xc03dce84   ( 916 kB)
[   15.032425]       .text : 0xc0100000 - 0xc02f7d26   (2015 kB)
[   15.032427] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   15.032455] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   15.032580] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[   15.032584] hpet0: 3 64-bit timers, 14318180 Hz
[   15.113558] Calibrating delay using timer specific routine.. 3994.85 BogoMIPS (lpj=7989708)
[   15.113573] Security Framework v1.0.0 initialized
[   15.113577] SELinux:  Disabled at boot.
[   15.113586] Mount-cache hash table entries: 512
[   15.113674] CPU: After generic identify, caps: bfebfbff 20000000 00000000 00000000 0000e3bd 00000000 00000001
[   15.113680] monitor/mwait feature present.
[   15.113681] using mwait in idle threads.
[   15.113684] CPU: L1 I cache: 32K, L1 D cache: 32K
[   15.113686] CPU: L2 cache: 4096K
[   15.113688] CPU: Physical Processor ID: 0
[   15.113690] CPU: Processor Core ID: 0
[   15.113691] CPU: After all inits, caps: bfebfbff 20000000 00000000 00003940 0000e3bd 00000000 00000001
[   15.113698] Compat vDSO mapped to ffffe000.
[   15.113708] Checking 'hlt' instruction... OK.
[   15.129624] SMP alternatives: switching to UP code
[   15.129932] Early unpacking initramfs... done
[   15.390695] ACPI: Core revision 20070126
[   15.390732] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   15.462078] CPU0: Intel(R) Core(TM)2 Duo CPU     T7300  @ 2.00GHz stepping 0a
[   15.462092] SMP alternatives: switching to SMP code
[   15.462162] Booting processor 1/1 eip 3000
[   15.472576] Initializing CPU#1
[   15.549310] Calibrating delay using timer specific routine.. 3989.99 BogoMIPS (lpj=7979990)
[   15.549315] CPU: After generic identify, caps: bfebfbff 20000000 00000000 00000000 0000e3bd 00000000 00000001
[   15.549319] monitor/mwait feature present.
[   15.549322] CPU: L1 I cache: 32K, L1 D cache: 32K
[   15.549323] CPU: L2 cache: 4096K
[   15.549325] CPU: Physical Processor ID: 0
[   15.549327] CPU: Processor Core ID: 1
[   15.549328] CPU: After all inits, caps: bfebfbff 20000000 00000000 00003940 0000e3bd 00000000 00000001
[   15.550009] CPU1: Intel(R) Core(TM)2 Duo CPU     T7300  @ 2.00GHz stepping 0a
[   15.550033] Total of 2 processors activated (7984.84 BogoMIPS).
[   15.550214] ENABLING IO-APIC IRQs
[   15.550430] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   15.697309] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[   15.717311] Brought up 2 CPUs
[   15.848840] migration_cost=46
[   15.848952] Booting paravirtualized kernel on bare hardware
[   15.849039] Time: 19:51:01  Date: 09/22/107
[   15.849056] NET: Registered protocol family 16
[   15.849124] EISA bus registered
[   15.849129] ACPI: bus type pci registered
[   15.849517] PCI: PCI BIOS revision 2.10 entry at 0xfdde1, last bus=14
[   15.849519] PCI: Using configuration type 1
[   15.849520] Setting up standard PCI resources
[   15.851585] ACPI: EC: Look up EC in DSDT
[   15.852254] ACPI: EC: GPE=0x1c, ports=0x66, 0x62
[   15.861715] ACPI: System BIOS is requesting _OSI(Linux)
[   15.861717] ACPI: Please test with "acpi_osi=!Linux"
[   15.861718] Please send dmidecode to [email]linux-acpi@vger.kernel.org[/email]
[   15.862214] ACPI: Interpreter enabled
[   15.862217] ACPI: (supports S0 S3 S4 S5)
[   15.862232] ACPI: Using IOAPIC for interrupt routing
[   15.909759] ACPI: EC: GPE=0x1c, ports=0x66, 0x62
[   15.909795] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   15.909799] PCI: Probing PCI hardware (bus 00)
[   15.913519] PCI: Transparent bridge - 0000:00:1e.0
[   15.913698] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   15.914012] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[   15.914122] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[   15.914233] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP03._PRT]
[   15.914341] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[   15.914449] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP05._PRT]
[   15.914560] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP06._PRT]
[   15.914684] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[   15.919080] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 *5 6 7 10 12 14 15)
[   15.919172] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[   15.919262] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 *7 10 12 14 15)
[   15.919352] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[   15.919441] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[   15.919530] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[   15.919619] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[   15.919708] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[   15.919811] Linux Plug and Play Support v0.97 (c) Adam Belay
[   15.919819] pnp: PnP ACPI init
[   15.919827] ACPI: bus type pnp registered
[   15.941365] pnp: PnP ACPI: found 10 devices
[   15.941367] ACPI: ACPI bus type pnp unregistered
[   15.941370] PnPBIOS: Disabled by ACPI PNP
[   15.941407] PCI: Using ACPI for IRQ routing
[   15.941409] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   16.142137] NET: Registered protocol family 8
[   16.142139] NET: Registered protocol family 20
[   16.142179] pnp: 00:01: iomem range 0xfed1c000-0xfed1ffff could not be reserved
[   16.142182] pnp: 00:01: iomem range 0xfed14000-0xfed17fff could not be reserved
[   16.142185] pnp: 00:01: iomem range 0xfed18000-0xfed18fff could not be reserved
[   16.142188] pnp: 00:01: iomem range 0xfed19000-0xfed19fff could not be reserved
[   16.142194] pnp: 00:04: iomem range 0xfed00000-0xfed003ff could not be reserved
[   16.144981] Time: tsc clocksource has been installed.
[   16.144988] Switched to high resolution mode on CPU 0
[   16.145065] Switched to high resolution mode on CPU 1
[   16.172470] PCI: Bridge: 0000:00:1c.0
[   16.172474]   IO window: 2000-2fff
[   16.172482]   MEM window: c0000000-c3ffffff
[   16.172491]   PREFETCH window: cc000000-cdffffff
[   16.172502] PCI: Bridge: 0000:00:1c.1
[   16.172506]   IO window: 3000-3fff
[   16.172514]   MEM window: f0000000-f3ffffff
[   16.172522]   PREFETCH window: fa000000-fbffffff
[   16.172530] PCI: Bridge: 0000:00:1c.2
[   16.172535]   IO window: 4000-4fff
[   16.172544]   MEM window: f4000000-f7ffffff
[   16.172553]   PREFETCH window: fc000000-fdffffff
[   16.172560] PCI: Bridge: 0000:00:1c.3
[   16.172565]   IO window: 5000-5fff
[   16.172575]   MEM window: b8000000-bbffffff
[   16.172584]   PREFETCH window: c8000000-c9ffffff
[   16.172591] PCI: Bridge: 0000:00:1c.4
[   16.172592]   IO window: disabled.
[   16.172602]   MEM window: disabled.
[   16.172608]   PREFETCH window: disabled.
[   16.172618] PCI: Bridge: 0000:00:1c.5
[   16.172619]   IO window: disabled.
[   16.172629]   MEM window: f8200000-f82fffff
[   16.172638]   PREFETCH window: disabled.
[   16.172650] PCI: Bridge: 0000:00:1e.0
[   16.172651]   IO window: disabled.
[   16.172663]   MEM window: f8300000-f83fffff
[   16.172672]   PREFETCH window: disabled.
[   16.172721] ACPI: PCI Interrupt 0000:00:1c.0[A] -> GSI 17 (level, low) -> IRQ 16
[   16.172732] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   16.172774] ACPI: PCI Interrupt 0000:00:1c.1[B] -> GSI 16 (level, low) -> IRQ 17
[   16.172781] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   16.172822] ACPI: PCI Interrupt 0000:00:1c.2[C] -> GSI 18 (level, low) -> IRQ 18
[   16.172830] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   16.172871] ACPI: PCI Interrupt 0000:00:1c.3[D] -> GSI 19 (level, low) -> IRQ 19
[   16.172879] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[   16.172917] ACPI: PCI Interrupt 0000:00:1c.4[A] -> GSI 17 (level, low) -> IRQ 16
[   16.172928] PCI: Setting latency timer of device 0000:00:1c.4 to 64
[   16.172968] ACPI: PCI Interrupt 0000:00:1c.5[B] -> GSI 16 (level, low) -> IRQ 17
[   16.172978] PCI: Setting latency timer of device 0000:00:1c.5 to 64
[   16.173007] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[   16.173018] NET: Registered protocol family 2
[   16.220922] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   16.220980] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
[   16.221532] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   16.221718] TCP: Hash tables configured (established 131072 bind 65536)
[   16.221720] TCP reno registered
[   16.236996] checking if image is initramfs... it is
[   16.800777] Freeing initrd memory: 7348k freed
[   16.800896] Simple Boot Flag at 0x38 set to 0x1
[   16.801282] audit: initializing netlink socket (disabled)
[   16.801294] audit(1193082661.228:1): initialized
[   16.801366] highmem bounce pool size: 64 pages
[   16.802858] VFS: Disk quotas dquot_6.5.1
[   16.802896] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   16.802969] io scheduler noop registered
[   16.802970] io scheduler anticipatory registered
[   16.802972] io scheduler deadline registered
[   16.802983] io scheduler cfq registered (default)
[   16.802997] Boot video device is 0000:00:02.0
[   16.803252] PCI: Setting latency timer of device 0000:00:1c.0 to 64
[   16.803346] assign_interrupt_mode Found MSI capability
[   16.803348] Allocate Port Service[0000:00:1c.0:pcie00]
[   16.803373] Allocate Port Service[0000:00:1c.0:pcie02]
[   16.803519] PCI: Setting latency timer of device 0000:00:1c.1 to 64
[   16.803621] assign_interrupt_mode Found MSI capability
[   16.803623] Allocate Port Service[0000:00:1c.1:pcie00]
[   16.803647] Allocate Port Service[0000:00:1c.1:pcie02]
[   16.803785] PCI: Setting latency timer of device 0000:00:1c.2 to 64
[   16.803887] assign_interrupt_mode Found MSI capability
[   16.803889] Allocate Port Service[0000:00:1c.2:pcie00]
[   16.803913] Allocate Port Service[0000:00:1c.2:pcie02]
[   16.804061] PCI: Setting latency timer of device 0000:00:1c.3 to 64
[   16.804161] assign_interrupt_mode Found MSI capability
[   16.804163] Allocate Port Service[0000:00:1c.3:pcie00]
[   16.804187] Allocate Port Service[0000:00:1c.3:pcie02]
[   16.804315] PCI: Setting latency timer of device 0000:00:1c.4 to 64
[   16.804407] assign_interrupt_mode Found MSI capability
[   16.804409] Allocate Port Service[0000:00:1c.4:pcie00]
[   16.804433] Allocate Port Service[0000:00:1c.4:pcie02]
[   16.804561] PCI: Setting latency timer of device 0000:00:1c.5 to 64
[   16.804655] assign_interrupt_mode Found MSI capability
[   16.804657] Allocate Port Service[0000:00:1c.5:pcie00]
[   16.804682] Allocate Port Service[0000:00:1c.5:pcie02]
[   16.804856] isapnp: Scanning for PnP cards...
[   17.161791] isapnp: No Plug & Play device found
[   17.178020] Real Time Clock Driver v1.12ac
[   17.178227] hpet_resources: 0xfed00000 is busy
[   17.178254] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   17.179104] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   17.179207] input: Macintosh mouse button emulation as /class/input/input0
[   17.179267] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   17.220351] serio: i8042 KBD port at 0x60,0x64 irq 1
[   17.220356] serio: i8042 AUX port at 0x60,0x64 irq 12
[   17.220589] mice: PS/2 mouse device common for all mice
[   17.222586] EISA: Probing bus 0 at eisa.0
[   17.222594] Cannot allocate resource for EISA slot 1
[   17.222597] Cannot allocate resource for EISA slot 2
[   17.222599] Cannot allocate resource for EISA slot 3
[   17.222601] Cannot allocate resource for EISA slot 4
[   17.222603] Cannot allocate resource for EISA slot 5
[   17.222623] EISA: Detected 0 cards.
[   17.222754] TCP cubic registered
[   17.222765] NET: Registered protocol family 1
[   17.222782] Using IPI No-Shortcut mode
[   17.222922]   Magic number: 11:34:901
[   17.222954]   hash matches device ptyve
[   17.223311] Freeing unused kernel memory: 364k freed
[   17.252851] input: AT Translated Set 2 keyboard as /class/input/input1
[   18.399256] AppArmor: AppArmor initialized<5>audit(1193082662.728:2):  type=1505 info="AppArmor initialized" pid=1253
[   18.404121] fuse init (API version 7.8)
[   18.407730] Failure registering capabilities with primary security module.
[   18.442533] ACPI: SSDT 3F6D9598, 027A (r1  PmRef  Cpu0Ist     3000 INTL 20050624)
[   18.442724] ACPI: SSDT 3F6D9069, 04AA (r1  PmRef  Cpu0Cst     3001 INTL 20050624)
[   18.443298] Monitor-Mwait will be used to enter C-1 state
[   18.443301] Monitor-Mwait will be used to enter C-2 state
[   18.443303] Monitor-Mwait will be used to enter C-3 state
[   18.443306] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[   18.443310] ACPI: Processor [CPU0] (supports 8 throttling states)
[   18.446129] ACPI: SSDT 3F6D9812, 00C8 (r1  PmRef  Cpu1Ist     3000 INTL 20050624)
[   18.446305] ACPI: SSDT 3F6D9513, 0085 (r1  PmRef  Cpu1Cst     3000 INTL 20050624)
[    3.028000] Marking TSC unstable due to: possible TSC halt in C2.
[    3.032000] Time: hpet clocksource has been installed.
[    3.032000] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    3.032000] ACPI: Processor [CPU1] (supports 8 throttling states)
[    3.420000] usbcore: registered new interface driver usbfs
[    3.420000] usbcore: registered new interface driver hub
[    3.420000] usbcore: registered new device driver usb
[    3.420000] USB Universal Host Controller Interface driver v3.0
[    3.420000] ACPI: PCI Interrupt 0000:00:1a.0[A] -> GSI 16 (level, low) -> IRQ 17
[    3.420000] PCI: Setting latency timer of device 0000:00:1a.0 to 64
[    3.420000] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    3.420000] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    3.420000] uhci_hcd 0000:00:1a.0: irq 17, io base 0x00001820
[    3.420000] usb usb1: configuration #1 chosen from 1 choice
[    3.420000] hub 1-0:1.0: USB hub found
[    3.420000] hub 1-0:1.0: 2 ports detected
[    3.452000] SCSI subsystem initialized
[    3.456000] libata version 2.21 loaded.
[    3.524000] ACPI: PCI Interrupt 0000:00:1a.1[B] -> GSI 21 (level, low) -> IRQ 20
[    3.524000] PCI: Setting latency timer of device 0000:00:1a.1 to 64
[    3.524000] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    3.524000] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 2
[    3.524000] uhci_hcd 0000:00:1a.1: irq 20, io base 0x00001840
[    3.524000] usb usb2: configuration #1 chosen from 1 choice
[    3.524000] hub 2-0:1.0: USB hub found
[    3.524000] hub 2-0:1.0: 2 ports detected
[    3.628000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 23 (level, low) -> IRQ 21
[    3.628000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[    3.628000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    3.628000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 3
[    3.628000] uhci_hcd 0000:00:1d.0: irq 21, io base 0x00001860
[    3.628000] usb usb3: configuration #1 chosen from 1 choice
[    3.628000] hub 3-0:1.0: USB hub found
[    3.628000] hub 3-0:1.0: 2 ports detected
[    3.732000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 19 (level, low) -> IRQ 19
[    3.732000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[    3.732000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    3.732000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 4
[    3.732000] uhci_hcd 0000:00:1d.1: irq 19, io base 0x00001880
[    3.732000] usb usb4: configuration #1 chosen from 1 choice
[    3.732000] hub 4-0:1.0: USB hub found
[    3.732000] hub 4-0:1.0: 2 ports detected
[    3.836000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 18
[    3.836000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[    3.836000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    3.836000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 5
[    3.836000] uhci_hcd 0000:00:1d.2: irq 18, io base 0x000018a0
[    3.836000] usb usb5: configuration #1 chosen from 1 choice
[    3.836000] hub 5-0:1.0: USB hub found
[    3.836000] hub 5-0:1.0: 2 ports detected
[    3.940000] ACPI: PCI Interrupt 0000:0e:06.0[A] -> GSI 22 (level, low) -> IRQ 22
[    3.940000] ACPI: PCI Interrupt 0000:00:1a.7[C] -> GSI 18 (level, low) -> IRQ 18
[    3.940000] PCI: Setting latency timer of device 0000:00:1a.7 to 64
[    3.940000] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    3.940000] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 6
[    3.940000] ehci_hcd 0000:00:1a.7: debug port 1
[    3.940000] PCI: cache line size of 32 is not supported by device 0000:00:1a.7
[    3.940000] ehci_hcd 0000:00:1a.7: irq 18, io mem 0xf8604800
[    3.944000] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.944000] usb usb6: configuration #1 chosen from 1 choice
[    3.944000] hub 6-0:1.0: USB hub found
[    3.944000] hub 6-0:1.0: 4 ports detected
[    3.992000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[22]  MMIO=[f8300000-f83007ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    4.000000] Clocksource tsc unstable (delta = -358912959 ns)
[    4.048000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 23 (level, low) -> IRQ 21
[    4.048000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    4.048000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    4.048000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 7
[    4.048000] ehci_hcd 0000:00:1d.7: debug port 1
[    4.048000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[    4.048000] ehci_hcd 0000:00:1d.7: irq 21, io mem 0xf8604c00
[    4.052000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    4.052000] usb usb7: configuration #1 chosen from 1 choice
[    4.052000] hub 7-0:1.0: USB hub found
[    4.052000] hub 7-0:1.0: 6 ports detected
[    4.156000] tg3.c:v3.77 (May 31, 2007)
[    4.156000] ACPI: PCI Interrupt 0000:04:00.0[A] -> GSI 17 (level, low) -> IRQ 16
[    4.156000] PCI: Setting latency timer of device 0000:04:00.0 to 64
[    4.460000] eth0: Tigon3 [partno(BCM95906) rev c002 PHY(5906)] (PCI Express) 10/100Base-TX Ethernet 00:16:d4:de:e4:ac
[    4.460000] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] WireSpeed[0] TSOcap[1]
[    4.460000] eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[    4.460000] ahci 0000:00:1f.2: version 2.2
[    4.460000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 19
[    5.268000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00023f76bc4023cb]
[    5.464000] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 3 Gbps 0x7 impl SATA mode
[    5.464000] ahci 0000:00:1f.2: flags: 64bit ncq pm led clo pio slum part 
[    5.464000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[    5.464000] scsi0 : ahci
[    5.464000] scsi1 : ahci
[    5.464000] scsi2 : ahci
[    5.464000] ata1: SATA max UDMA/133 cmd 0xf886e100 ctl 0x00000000 bmdma 0x00000000 irq 19
[    5.464000] ata2: SATA max UDMA/133 cmd 0xf886e180 ctl 0x00000000 bmdma 0x00000000 irq 19
[    5.464000] ata3: SATA max UDMA/133 cmd 0xf886e200 ctl 0x00000000 bmdma 0x00000000 irq 19
[    5.952000] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    5.952000] ata1.00: ATA-7: Hitachi HTS541612J9SA00, SBDOC7KP, max UDMA/100
[    5.952000] ata1.00: 234441648 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    5.952000] ata1.00: configured for UDMA/100
[    6.264000] ata2: SATA link down (SStatus 0 SControl 300)
[    6.576000] ata3: SATA link down (SStatus 0 SControl 300)
[    6.576000] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS54161 SBDO PQ: 0 ANSI: 5
[    6.580000] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[    6.580000] sd 0:0:0:0: [sda] Write Protect is off
[    6.580000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    6.580000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.580000] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[    6.580000] sd 0:0:0:0: [sda] Write Protect is off
[    6.580000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    6.580000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.580000]  sda: sda1 sda2 < sda5 >
[    7.016000] sd 0:0:0:0: [sda] Attached SCSI disk
[    7.020000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    7.280000] Attempting manual resume
[    7.280000] swsusp: Resume From Partition 8:5
[    7.280000] PM: Checking swsusp image.
[    7.280000] PM: Resume from disk failed.
[    7.320000] kjournald starting.  Commit interval 5 seconds
[    7.320000] EXT3-fs: mounted filesystem with ordered data mode.
[   14.720000] ip_tables: (C) 2000-2006 Netfilter Core Team
[   14.752000] Netfilter messages via NETLINK v0.30.
[   14.756000] nf_conntrack version 0.5.0 (8118 buckets, 64944 max)
[   15.612000] Linux agpgart interface v0.102 (c) Dave Jones
[   15.648000] agpgart: Detected an Intel 965GM Chipset.
[   15.648000] agpgart: Detected 7676K stolen memory.
[   15.660000] agpgart: AGP aperture is 256M @ 0xd0000000
[   15.788000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   15.792000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   16.104000] ieee80211_crypt: registered algorithm 'NULL'
[   16.108000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   16.108000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   16.204000] sdhci: Secure Digital Host Controller Interface driver
[   16.204000] sdhci: Copyright(c) Pierre Ossman
[   16.204000] sdhci: SDHCI controller found at 0000:0e:06.1 [1180:0822] (rev 22)
[   16.204000] ACPI: PCI Interrupt 0000:0e:06.1[B] -> GSI 23 (level, low) -> IRQ 21
[   16.204000] mmc0: SDHCI at 0xf8300800 irq 21 DMA
[   16.236000] ipw3945: Intel(R) PRO/Wireless 3945 Network Connection driver for Linux, 1.2.2mp.ubuntu1
[   16.236000] ipw3945: Copyright(c) 2003-2006 Intel Corporation
[   16.236000] ACPI: PCI Interrupt 0000:0c:00.0[A] -> GSI 17 (level, low) -> IRQ 16
[   16.236000] PCI: Setting latency timer of device 0000:0c:00.0 to 64
[   16.236000] ipw3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[   16.752000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 20 (level, low) -> IRQ 23
[   16.752000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   16.952000]  patch_alc268 start .
[   16.952000] check board start 
[   16.952000]  ALC268_TOSHIBA 0x1, board_config 0x1.
[   18.168000] ipw3945: Detected geography ABG (11 802.11bg channels, 13 802.11a channels)
[   18.424000] input: ImPS/2 Logitech Wheel Mouse as /class/input/input2
[   18.432000] lp: driver loaded but no devices found
[   18.504000] Adding 3004112k swap on /dev/sda5.  Priority:-1 extents:1 across:3004112k
[   18.928000] EXT3 FS on sda1, internal journal
[   20.036000] ACPI: AC Adapter [ACAD] (off-line)
[   20.140000] No dock devices found.
[   20.156000] input: Power Button (FF) as /class/input/input3
[   20.156000] ACPI: Power Button (FF) [PWRF]
[   20.156000] input: Lid Switch as /class/input/input4
[   20.156000] ACPI: Lid Switch [LID0]
[   20.156000] input: Power Button (CM) as /class/input/input5
[   20.156000] ACPI: Power Button (CM) [PWRB]
[   20.288000] ACPI: Battery Slot [BAT1] (battery present)
[   20.340000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   20.352000] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   21.776000] PM: Writing back config space on device 0000:04:00.0 at offset c (was 24ef0000, writing 0)
[   24.264000] ppdev: user-space parallel port driver
[   24.416000] audit(1193082684.768:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=5209 profile="/usr/sbin/cupsd"
[   24.484000] apm: BIOS not found.
[   24.832000] Failure registering capabilities with primary security module.
[   25.104000] Bluetooth: Core ver 2.11
[   25.104000] NET: Registered protocol family 31
[   25.104000] Bluetooth: HCI device and connection manager initialized
[   25.104000] Bluetooth: HCI socket layer initialized
[   25.144000] Bluetooth: L2CAP ver 2.8
[   25.144000] Bluetooth: L2CAP socket layer initialized
[   25.220000] Bluetooth: RFCOMM socket layer initialized
[   25.220000] Bluetooth: RFCOMM TTY layer initialized
[   25.220000] Bluetooth: RFCOMM ver 1.8
[   26.140000] [drm] Initialized drm 1.1.0 20060810
[   26.144000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 17
[   26.144000] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   70.456000] ata1.00: exception Emask 0x2 SAct 0x75 SErr 0x0 action 0x2 frozen
[   70.456000] ata1.00: (spurious completions during NCQ issue=0x0 SAct=0x75 FIS=005040a1:00000008)
[   70.456000] ata1.00: cmd 60/08:00:77:c0:ca/00:00:07:00:00/40 tag 0 cdb 0x0 data 4096 in
[   70.456000]          res 50/00:08:77:02:f2/00:00:04:00:00/40 Emask 0x2 (HSM violation)
[   70.456000] ata1.00: cmd 60/08:10:9f:c4:c1/00:00:09:00:00/40 tag 2 cdb 0x0 data 4096 in
[   70.456000]          res 50/00:08:77:02:f2/00:00:04:00:00/40 Emask 0x2 (HSM violation)
[   70.456000] ata1.00: cmd 60/08:20:77:02:f2/00:00:04:00:00/40 tag 4 cdb 0x0 data 4096 in
[   70.456000]          res 50/00:08:77:02:f2/00:00:04:00:00/40 Emask 0x2 (HSM violation)
[   70.456000] ata1.00: cmd 60/08:28:b7:92:a7/00:00:04:00:00/40 tag 5 cdb 0x0 data 4096 in
[   70.456000]          res 50/00:08:77:02:f2/00:00:04:00:00/40 Emask 0x2 (HSM violation)
[   70.456000] ata1.00: cmd 60/08:30:bf:92:a7/00:00:04:00:00/40 tag 6 cdb 0x0 data 4096 in
[   70.456000]          res 50/00:08:77:02:f2/00:00:04:00:00/40 Emask 0x2 (HSM violation)
[   70.828000] ata1: soft resetting port
[   71.000000] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   71.000000] ata1.00: configured for UDMA/100
[   71.000000] ata1: EH complete
[   71.000000] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[   71.004000] sd 0:0:0:0: [sda] Write Protect is off
[   71.004000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   71.004000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   78.132000] NET: Registered protocol family 10
[   78.132000] lo: Disabled Privacy Extensions
[   78.132000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   78.132000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   81.872000] NET: Registered protocol family 17
[   85.072000] ieee80211_crypt: registered algorithm 'WEP'
[   85.132000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[   91.688000] usb 3-1: new low speed USB device using uhci_hcd and address 2
[   91.868000] usb 3-1: configuration #1 chosen from 1 choice
[   91.940000] usbcore: registered new interface driver hiddev
[   91.980000] input: Microsoft Microsoft USB Wireless Mouse as /class/input/input6
[   91.980000] input: USB HID v1.11 Mouse [Microsoft Microsoft USB Wireless Mouse] on usb-0000:00:1d.0-1
[   91.980000] usbcore: registered new interface driver usbhid
[   91.980000] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[  101.128000] eth1: no IPv6 routers present
[ 3452.136000] ata1.00: exception Emask 0x2 SAct 0x7fff9 SErr 0x0 action 0x2 frozen
[ 3452.136000] ata1.00: (spurious completions during NCQ issue=0x0 SAct=0x7fff9 FIS=005040a1:00000004)
[ 3452.136000] ata1.00: cmd 61/10:00:67:02:e0/00:00:07:00:00/40 tag 0 cdb 0x0 data 8192 out
[ 3452.136000]          res 50/00:08:87:05:c0/00:00:09:00:00/40 Emask 0x2 (HSM violation)
[ 3452.136000] ata1.00: cmd 61/08:18:7f:01:bc/00:00:07:00:00/40 tag 3 cdb 0x0 data 4096 out
[ 3452.136000]          res 50/00:08:87:05:c0/00:00:09:00:00/40 Emask 0x2 (HSM violation)
[ 3452.136000] ata1.00: cmd 61/10:20:8f:01:bc/00:00:07:00:00/40 tag 4 cdb 0x0 data 8192 out
[ 3452.136000]          res 50/00:08:87:05:c0/00:00:09:00:00/40 Emask 0x2 (HSM violation)
[ 3452.136000] ata1.00: cmd 61/08:28:47:02:bc/00:00:07:00:00/40 tag 5 cdb 0x0 data 4096 out
[ 3452.136000]          res 50/00:08:87:05:c0/00:00:09:00:00/40 Emask 0x2 (HSM violation)
[ 3452.136000] ata1.00: cmd 61/08:30:df:05:bc/00:00:07:00:00/40 tag 6 cdb 0x0 data 4096 out
[ 3452.136000]          res 50/00:08:87:05:c0/00:00:09:00:00/40 Emask 0x2 (HSM violation)
[ 3452.136000] ata1.00: cmd 61/08:38:ef:01:e0/00:00:07:00:00/40 tag 7 cdb 0x0 data 4096 out
[ 3452.136000]          res 50/00:08:87:05:c0/00:00:09:00:00/40 Emask 0x2 (HSM violation)
[ 3452.136000] ata1.00: cmd 61/08:40:9f:00:bc/00:00:07:00:00/40 tag 8 cdb 0x0 data 4096 out
[ 3452.136000]          res 50/00:08:87:05:c0/00:00:09:00:00/40 Emask 0x2 (HSM violation)
[ 3452.136000] ata1.00: cmd 61/08:48:ff:01:bc/00:00:07:00:00/40 tag 9 cdb 0x0 data 4096 out
[ 3452.136000]          res 50/00:08:87:05:c0/00:00:09:00:00/40 Emask 0x2 (HSM violation)
[ 3452.136000] ata1.00: cmd 61/18:50:ef:02:e0/00:00:07:00:00/40 tag 10 cdb 0x0 data 12288 out
[ 3452.136000]          res 50/00:08:87:05:c0/00:00:09:00:00/40 Emask 0x2 (HSM violation)
[ 3452.136000] ata1.00: cmd 61/08:58:8f:03:c0/00:00:09:00:00/40 tag 11 cdb 0x0 data 4096 out
[ 3452.136000]          res 50/00:08:87:05:c0/00:00:09:00:00/40 Emask 0x2 (HSM violation)
[ 3452.136000] ata1.00: cmd 61/18:60:3f:00:c0/00:00:09:00:00/40 tag 12 cdb 0x0 data 12288 out
[ 3452.136000]          res 50/00:08:87:05:c0/00:00:09:00:00/40 Emask 0x2 (HSM violation)
[ 3452.136000] ata1.00: cmd 61/18:68:5f:00:c0/00:00:09:00:00/40 tag 13 cdb 0x0 data 12288 out
[ 3452.136000]          res 50/00:08:87:05:c0/00:00:09:00:00/40 Emask 0x2 (HSM violation)
[ 3452.136000] ata1.00: cmd 61/08:70:1f:04:c0/00:00:09:00:00/40 tag 14 cdb 0x0 data 4096 out
[ 3452.136000]          res 50/00:08:87:05:c0/00:00:09:00:00/40 Emask 0x2 (HSM violation)
[ 3452.136000] ata1.00: cmd 61/08:78:ef:04:c0/00:00:09:00:00/40 tag 15 cdb 0x0 data 4096 out
[ 3452.136000]          res 50/00:08:87:05:c0/00:00:09:00:00/40 Emask 0x2 (HSM violation)
[ 3452.136000] ata1.00: cmd 61/08:80:87:05:c0/00:00:09:00:00/40 tag 16 cdb 0x0 data 4096 out
[ 3452.136000]          res 50/00:08:87:05:c0/00:00:09:00:00/40 Emask 0x2 (HSM violation)
[ 3452.136000] ata1.00: cmd 61/20:88:1f:02:bc/00:00:07:00:00/40 tag 17 cdb 0x0 data 16384 out
[ 3452.136000]          res 50/00:08:87:05:c0/00:00:09:00:00/40 Emask 0x2 (HSM violation)
[ 3452.136000] ata1.00: cmd 61/10:90:4f:02:e0/00:00:07:00:00/40 tag 18 cdb 0x0 data 8192 out
[ 3452.136000]          res 50/00:08:87:05:c0/00:00:09:00:00/40 Emask 0x2 (HSM violation)
[ 3452.448000] ata1: soft resetting port
[ 3452.632000] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[ 3452.632000] ata1.00: configured for UDMA/100
[ 3452.632000] ata1: EH complete
[ 3452.632000] sd 0:0:0:0: [sda] 234441648 512-byte hardware sectors (120034 MB)
[ 3452.632000] sd 0:0:0:0: [sda] Write Protect is off
[ 3452.632000] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 3452.632000] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
cwej@cwej-laptop:~$

---

### Post by agisfox on 2007-10-22
cwej / newsun:
This sounds like the issue i had/have with my Darter -  try entering
 
> sudo mknod /dev/hda b 22 0

and see if that helps the issue (though I've had to re-enter it after reboots).

---

### Post by cwej on 2007-10-22
Thanks, but didn't work...

---

### Post by thomasaaron on 2007-10-23
Please post the output of these two commands:

cat /etc/fstab


ls /media

---

### Post by thomasaaron on 2007-10-23
Summarizing:

1. After a CD install of Gutsy, CD drive does work.
2. After dist-upgrade, CD drive stops working.


Please post output of:

cat /etc/fstab
...and...
ls -A /media



NOTE: I'm imaging a panv3 via CD right now and will try to replicate.
Let's try to keep this thread focused... :lolflag:

---

### Post by cwej on 2007-10-23
First task:
~*~*~*~*~*~**~
cwej@cwej-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=b489c754-c593-45a1-a22f-9d6242dbf1a7 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=660ba118-98b6-4045-a5b5-357b0e53b441 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
cwej@cwej-laptop:
~*~*~*~*~*~ 
Second:
~*~*~*~*~*
cwej@cwej-laptop:~$ ls -A /media
cdrom  cdrom0  .hal-mtab
~*~*~*~*~*
...as requested...and thank you for continuing to assist! 
r/Chuck

---

### Post by cwej on 2007-10-23
Correction to your summary, to hopefully improve clarity and accuracy:

1. After initial Upgrade manager download and upgrade from 7.04 to 7.10, sound and CD ROM drive fails to mount upon insertion of data CD (multiple known good CDs tried), spins, but fails to mount, cannot gain access (never checked or noticed sound issue)... 

2. Downloaded/burned fresh iso image (on another system) for subsequent CD install of 7.10, CD again failed to work as before (along with sound not working - may have just noticed this for first time time)

3. So, I did retrograde install of 7.04, everything worked 

4. Upgraded again using Update manager 
 a. by this time I had been browsing forums
  b. so, and took advice to fetch new 2.1.1 driver, re-enable system 76 software repositories, and install new driver after upgrade
 c. sound restored, CD fails as before

5. Current state: CD ROMS still fail to mount...drive spins on data CD insert, but cannot access contents.

I hope this clears thing, again, thanks!

---

### Post by thomasaaron on 2007-10-23
[LIST]
[*]OK, I just installed 7.10 via CD-ROM.
[*]Ran sudo apt-get update && sudo apt-get dist-upgrade
[/LIST]

CD-ROM worked. Sound did not. (These were the expected results.)

[LIST]
[*]Downloaded and ran System 76 driver (Install Drivers Only)
[/LIST]

CD-ROM still worked. Sound did work. (These were the expected results.)

[LIST]
[*]Ran the System 76 Driver (Restore Tab and button).
[/LIST]

CD-ROM still worked. Sound still worked. (These were the expected results).



----SO-----

I don't know where things went wrong with your install, but somehow it is not creating the proper configuration to connect to your CD-drive.

My fstab identifies the cdrom as /dev/sdc0


----TRY THIS----

sudo gedit /etc/fstab

Change this line:
/dev/hda /media/cdrom0 udf,iso9660 user,noauto 0 0
To this:
/dev/hda0 /media/cdrom0 udf,iso9660 user,noauto 0 0

Reboot the computer and test the drive.

If that fails, change the line to this:
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto 0 0

Reboot the computer and test the drive.

---

### Post by cwej on 2007-10-23
Thanks, made change, to fstab, standing by for reboot but looking for handy data cd to test...
in the meantime...
I noticed that you downloaded and installed system 76 drivers (install tab), like I did to restore sound successfully, but then you did it again (I didn't), this time you went to restore tab and selected restore button...
why? instructions/documentation for me have been ambiguous on point of when to use install tab, button, and when to use restore tab and button... what does restore do that install does not? I didn't want to retrograde, and that's what I suspected "restore" did...

---

### Post by cwej on 2007-10-23
OK, sudo gedit of /etc/fstab accomplished, 
- attempt 1 with first recommended line, reboot, and known good CD -- negative results
- attempt 2 with second recommended line, reboot, and known good cd -- negative results

The following is current state of /etc/fstab file after second attempt:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=b489c754-c593-45a1-a22f-9d6242dbf1a7 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=660ba118-98b6-4045-a5b5-357b0e53b441 none            swap    sw              0       0
#/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

#replaced above and added below to troubleshoot cdrom drive

#/dev/hda0 /media/cdrom0 udf,iso9660 user,noauto 0 0

#below is second option if first doesn't work
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto 0 0

---

### Post by thomasaaron on 2007-10-23
> I noticed that you downloaded and installed system 76 drivers (install tab), like I did to restore sound successfully, but then you did it again (I didn't), this time you went to restore tab and selected restore button...
why? instructions/documentation for me have been ambiguous on point of when to use install tab, button, and when to use restore tab and button... what does restore do that install does not? I didn't want to retrograde, and that's what I suspected "restore" did...

I ran both the install and restore tabs to eliminate the possibility that either of them were causing problems. The restore function dumps in a new xorg.conf file. It may do other things too, depending on the computer model.

----Regarding your cd-rom----

First, try this:
sudo mknod /dev/scd0 b 22 0
(if that doesn't work, try: sudo mknot /dev/scd b 22 0)

Test the drive before AND after rebooting. Success?

Sorry for all of the testing, it's just that I can't duplicate this on our shop computer.

---

### Post by cwej on 2007-10-23
Well...interestingly, after 1st mknod command, the cd drive didn't mount, however, I wanted to check if error in "-> Places, CD/DVD creator still gave same error when clicked, i.r., "Unable to mount selected volume (then on selection of -  "Show more details" I got the usual "mount: special device /dev/scd0 does not exist"

However, suddenly, after pressing OK on msgbox, the drive mounted and I was able to see contents...

Then on reboot, nothing again...

I replicated staps above, and voila, see attached screenshot...

so in current situation, can mount on mknod, but only after selecting Places-> CD/DVD creator, and does not appear to be persistent condition following reboot...

progress...

---

### Post by thomasaaron on 2007-10-23
OK, well, that is something. Right?

Put a disk in the drive and, after it spins up, enter this command: lsmod

Do you see a module in there named: cdrom?

If not, enter this command: sudo modprobe cdrom
and then repeat the above steps to see if you can load the cd.

---

### Post by cwej on 2007-10-23
OK, well, first "lsmod" fails to show cdrom...

so, then I run 
                           ~$ sudo modprobe cdrom,
                                        -- which shows cdrom: "cdrom                  37536  1 ide_cd"

....but still won't mount inserted cd, so run:

               sudo mknod /dev/scd0 b 22 0

...and reinsert CD, still no mount, as before, until I click Places -> CD/DVD Creator, and then click (on left panel) "CD-ROM 1" icon

Then first I get an error message, Unable to mount the volume..., then on clicking the "Show more details," I get further msg:  
 
            mount: /dev/scd0 is not a valid block device -- BUT, when I click, OK button, it mounts CD! 

And from then on _until reboot,_ I have CD-ROM drive back...

---

### Post by thomasaaron on 2007-10-23
Let's try a quick shift in strategy.
Go to System > Admin > Users and Groups.
Highlight your username and then click properties.
Is the "Use CD-ROM'S" box checked?

---

### Post by cwej on 2007-10-23
Yes, box is checked, but, interestingly, when out of curiosity I then go to click on /root to check for permissions,  none of the boxes are checked, and when I right clicked mounted CD icon to get to properties page, it shows /root as owner... does this mean anything? (owner /root, but /root has no privileges?) Or is this how its supposed to work?

---

### Post by thomasaaron on 2007-10-23
Well, what you get when you check the privileges via the icon, depends on the CD you have in there. If you have a blank CD, it might say "unknown." If you put a driver CD in, it will say "root."

Also, under Users and Groups, my root account has no boxes checked either. So, I don't think that is the problem.

As best I can tell, something went wrong in your upgrade to Gutsy. I cannot duplicate it no matter how I install on our shop PanV3.

So, at this point, I am at a loss. As much as my pride will hurt, I'd suggest re-imaging. And I'd do it EXACTLY like this:

1. Install with an ALTERNATE CD in Text Mode.(Make sure you have a wired connection to the internet.)

2. When the install is finished, boot up and run these commands:

sudo gedit /etc/apt/sources.list
(then comment out the cdrom reference near the beginning of the file and save)

sudo apt-get update && sudo apt-get --assume-yes dist-upgrade
(Make sure you have a wired connection to the internet. If you start getting errors about it being unable to resolve url's, run: 'sudo ifdown eth0' and then sudo ifup eth0' and re-run the update and dist-upgrade commands.)

sudo reboot

3. Then go to planet76.com/repositories and download the latest System 76 driver (scroll all the way to the bottom). When you click on it, it will give you the option to open it with gdebi installer. Take it. When gdebi opens up, click install.

4. Go to System > Admin > System 76 Driver and run the restore function.

5. Reboot the computer.

If you have any questions during the install process about anything, give me a call or post to this forum. I'll be watching. Sorry for the inconvenience, but there just comes a time when finding the problem becomes way less efficient than a re-do.

May the Force be with you.

Tom

---

### Post by osx424242 on 2007-10-24
I had the same problem with my panv3, but just got it working.  I used:

```
(if it doesn't already exist, mkdir /mnt/cdrom)
sudo mknod /dev/hda b 22 0
sudo mount -t auto /dev/hda /mnt/cdrom
```

My fstab already had /dev/scd0 in it.  I'm attaching a 'script' output that shows what I did to get things working (I got them working, then rebooted to capture the commands, which is why I forgot the 'mknod' command, causing a few false starts in 'typescript').  The output also shows stuff like my /etc/fstab and hopefully other interesting info.

One thing I noticed from reading this thread is that I used the update manager GUI to do the Feisty->Gutsy upgrade, but you seem to have always used the terminal when testing.  I wouldn't _expect_ that to cause a problem, but it is the only difference I could see.

I got it figured out with clues from thread 580745 here, [http://linux.about.com/od/linux101/l/blnewbie4_2_2.htm](http://linux.about.com/od/linux101/l/blnewbie4_2_2.htm), and [http://www.devlib.org/forums/re-gutsy-windows-t409.html?](http://www.devlib.org/forums/re-gutsy-windows-t409.html?).

---

### Post by cwej on 2007-10-24
Tom,

First, I'd like to say thank you very much for your time, expertise and effort. Regardless of final outcome I've learned a lot throughout this process, and that's invaluable. 

Just so that you know, since I really dreaded the pain of another load from scratch (I've had to add several features to be interopreable with work and my grad school collaboration site (Webycho -  Unix in back-end, but notoriously Microsoft/IE proprietary demanding on customer end, go figure), I was prepared to just live with the workaround of terminal mknod'ing it on a per need basis.

However, I tried the procedures in the post after yours (osx424242), and it appears to have worked.   

First, I went ahead and uncommented the original fstab and commented back out my mods,
Then I checked /mnt for a dir called, cdrom, which didn't exist, so I mede it:  mkdir /mnt/cdrom)

Then, following osx424242's directions (cut-and-paste, actually), I:
 
sudo mknod /dev/hda b 22 0

I then put in a cd, and pasted the command:

sudo mount -t auto /dev/hda /mnt/cdrom

And the cd mounted without any additional intervention. I inserted and ejected sever times, and also rebooted. It appears to have taken care of the issue. I'm guessing that the the lack of a cdrom directory in /mnt gave it no place to stay presistent...(but will refrain from pretending to know what I'm talking about).

Again, tremendous thanks to Tom, osx424242, and my appreciation to all who have engaged with their ideas, all of which I've gained something from.

Cheers, Chuck

---

### Post by thomasaaron on 2007-10-24
Great job!

> One thing I noticed from reading this thread is that I used the update manager GUI to do the Feisty->Gutsy upgrade, but you seem to have always used the terminal when testing. I wouldn't _expect_ that to cause a problem, but it is the only difference I could see.

I was actually mulling that one over too. Another person mentioned he had used a Gutsy CD to upgrade from Feisty. I can't help but wonder.

---

### Post by cwej on 2007-10-24
Just a quick follow-up to get to the root-cause of why my upgrades might have gone wrong in the first place..

There are points in the actual installation routine, following download completion, where the installation pauses a number of times to ask whether to overwrite or preserve existing configuration files--

In the past I have reflexively answered no, reasoning that the unspecified current configuration files might have something to do with my specific internal architecture -- 

Is this bad reasoning? I ask because in your installation post, you say "assume yes," which I am assuming has to do with the user prompts???

In the future, should I say yes or no? 

If yes, then maybe a knowledge sticky to that effect might do others some good around upgrade release time. I couldn't be the only numbskull who makes such decisions based on best guess in absence of real understanding of the underlying yet unspecified details behind the question...(or maybe I could!)

Thanks!

chuck

---

### Post by thomasaaron on 2007-10-24
Right the assume-yes flag answers yes to all prompts.

So, maybe there is indeed something in there causing problems.

P.S: This seems to have happened to about a half-dozen computers as best I can tell. I'm becoming more convinced that the best fix is a fresh install.

---

### Post by osx424242 on 2007-10-24
I always answered yes during the upgrade, but I kept a list of all the files that had changed, by backing up the original files before accepting the change.  I can post the originals here if you'd like, tonight.  I have to run now.  They are (paths might not be exact because I just copied them into a directory by replacing '/' with '_' and may have made some mistakes):
/etc/default/acpi-support
/etc/default/avahi-daemon
/etc/init.d/bootmisc.sh
/etc/kde3/kdm/backgroundrc
/etc/kde3/kdm/kdmrc
[I had installed Kubuntu about a week prior to the Gutsy upgrade; I've since removed it while trying to troubleshoot the cdrom thing]
/etc/modprobe.d/alsa-base
something else, forget what, removed /usr/bin/X11 (an ln to . from within /usr/bin, which was already in the path) from the path, and changed some whitespace.

Also, completely unrelated, but I mistyped 'pwd' during the upgrade as 'pqs' and got a "KABOOM!!! Whoops, command-not-found has crashed!" followed by a Python backtrace. It was a little bit of entertainment during a long install :)

---

### Post by octathlon on 2007-10-24
Allll righty then ...

I have a panv3 and have been holding off on the gutsy upgrade while keeping an eye on how it was going for the others (mua ha ha).  Let's see if I am understanding things right:  
-The only known gutsy issue for panv3 is the cdrom thing.  
-The problem occurred when using the update manager but not when doing a clean install (I think?)
-In any case, if it happens, osx424242's fix seems to resolve the problem.

I was originally planning to do a clean install since I want to repartition my drive anyway, but I was thinking of trying the upgrade with the update manager first, just to see how that would work because I've never done it that way before.  Sounds like I might be better off not doing that after all, unless anyone wants me to for testing purposes.

---

### Post by thomasaaron on 2007-10-24
Well, i just did a fresh install (for about the third time) on our shop panv3 per the wiki instructions.

No sound problems.
No cdrom problems.

---

### Post by cwej on 2007-10-24
Wellllll....so I took the advice to do a clean install...

CDRom, no problems!

Sound, however, not there, and just reloading the drivers doesn't help...so, I'm going to start fishing the forums again...

---

### Post by Panacid on 2007-10-24
Hi all

I am a total newbie to Linux who is having the same problem getting the cdrom on my Pangolin to work under Gutsy. When I attempt the fix posted by osx424242, I get the following error:

robbie@ubuntu:~$ sudo mknod /dev/hda b 22 0
robbie@ubuntu:~$ sudo mount -t auto /dev/hda /mnt/cdrom
mount: /dev/hda is not a valid block device

The cdrom starts working again,  but it stops working if I reboot the computer. Any suggestions/further info needed?

Thanks in advance.

---

### Post by osx424242 on 2007-10-25
Hi Panacid,
I'm also brand new to Linux, and I do also need to send those commands again after every reboot (I use cd-roms rarely, so for now I just have an icon in my launchbar to call a shell script that sends those two commands), so I don't know what to tell you.  The problem _might_ lie in the /etc/fstab file, but I'm not really sure.  To help other people with troubleshooting, can you post the contents of your /etc/fstab (i.e. open a terminal, type "cat /etc/fstab" without the quotes, then copy the output into here)?
For reference, mine reads:

```
$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# file system         mount point          type      options          dump       pass
proc    /proc   proc    defaults        0       0
/dev/mapper/ubuntu-root /       ext3    defaults,errors=remount-ro      0      1
# /dev/sda1
UUID=9e92b6db-1f98-44ec-9305-803ec9ea45f9       /boot   ext3    defaults       02
/dev/mapper/ubuntu-swap_1       none    swap    sw      0       0
/dev/scd0       /media/cdrom0   udf,iso9660     user,noauto     0       0
$ 


```

---

### Post by newsun on 2007-10-25
I concur that with a fresh install I have optical drive working and sound is not so good, although, an improvement is that the mixer loads, just no sound comes out.

I will note that I am insalling Kubuntu 7.10, which should not make a difference on drivers and kernal stuff, but take it for what it is worth. everything worked in 7.04

---

### Post by Panacid on 2007-10-25
Hi osx424242

Thanks so much for the quick reply. Though I would prefer having my cdrom mount automatically, I too am ok with doing it manually each time I am going to use it... plus it totally increases my geek cred with the ladies when they see me using terminal.  ;)

As per your instructions, here are the contents of /etc/fstab:

```
# /etc/fstab: static file system information.
#
# file system         mount point          type      options          dump       pass
proc    /proc   proc    defaults        0       0
/dev/mapper/ubuntu-root /       ext3    defaults,errors=remount-ro      0      1
# /dev/sda1
UUID=9e92b6db-1f98-44ec-9305-803ec9ea45f9       /boot   ext3    defaults       02
/dev/mapper/ubuntu-swap_1       none    swap    sw      0       0
/dev/scd0       /media/cdrom0   udf,iso9660     user,noauto     0       0
```


Hope this helps diagnose the problem. Thanks again for all your assistance!

---

### Post by cwej on 2007-10-26
Since I started this, I should really clarify that my issues have been 

**SOLVED (totally)** 


The solution was to download an alternate install iso from Ubuntu, burn a cd, verify its integrety, and do clean install in text mode. 

Now everything works as advertized.

It should be noted that ThomasAaron recommended this fairly early in the process, but I resisted, because I had put (I thought) too much effort in configuring my system.

However, my lazyness ended up costing me more effort in the end...

Anyway, everything works now. Primary lesson learned &#8211; when an initial upgrade goes wrong, load fresh rather than flail too much trying to fix an unknown number of glitches.

---

### Post by kperkins on 2007-10-31
```

# /etc/fstab: static file system information.
#
# file system         mount point          type      options          dump       pass
proc    /proc   proc    defaults        0       0
/dev/mapper/ubuntu-root /       ext3    defaults,errors=remount-ro      0      1
# /dev/sda1
UUID=9e92b6db-1f98-44ec-9305-803ec9ea45f9       /boot   ext3    defaults       02
/dev/mapper/ubuntu-swap_1       none    swap    sw      0       0
/dev/scd0       /media/cdrom0   udf,iso9660     user,noauto     0       0


```
Here's my fstab.  Same story as the rest.  Did an upgrade through update manager, answered no to some of the config questions, and yes to others.  cdroms etc work now with the code above, but  have to do it everytime I reboot.  Not liking that, and really don't want to reinstall unless I have to.  I'll use this solution for now, but is a pain in the butt.

---

### Post by thomasaaron on 2007-10-31
The only way I've found to permanently fix it is a re-install. Email me for instructions.

---

### Post by cwej on 2007-10-31
That was the only way I finally fixed mine -- reinstalled from alternate CD in text mode fixed absolutely everything. 

So, to recap:

- All of my prior problems started when I did Update Manager upgrade
- Things got worse when I tried to fix, no matter what I tried
- Reinstall from Live CD failed to fix
- Full installation from Alternate CD in text more took care of everything...

---

