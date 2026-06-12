---
title: "Advice On Running XP In Ubuntu Via VirtualBox"
date: 2008-07-15
forum: Virtualisation
---

### Post by AlistairH on 2008-07-15
I have been Micrsoft free for over a year now and don't, for 1 minute, regret changing. However, I'm now in a bit of a quandry.

I make a significant second income from trading sports markets on Betfair but the cross-platform application I use is no longer being developed and is likely to stop working at anytime. Unfortunately, as far as I know, there are no other Betfair trading applications that will run natively on Linux. They are all Windows based and use the .NET framework which rules out WINE.

I'm left with 3 options: 1 - Go back to Microsoft completely and put up with all the reasons I abandoned it in the first place. 2 - Dual boot, but to be honest, since the vast majority of my computing time will be spent trading, I might as well do everything in Windows, rather than have to reboot. 3 - As the trading software would be the only Windows application I need to run, setting up a VirtualBox is perhaps my preferred option - but this is where I need some advice before I launch myself into it.

I'd be grateful if someone could provide answers/advice to the following please...

1. First of all, are there any issues with the specification of my machine?

Dual Core P4 3Ghz CPU
2GB Memory
SiS Graphics card - no intense graphics required and not running compiz
30GB root partion
150GB Home partition with 135GB free.
Screen Res 1440 x 900

The minimum spec for the Windows application I'd probably use is:
Operating system : Windows 2000, XP or Vista
CPU: Pentium 4 or AMD equivalent
RAM :256Mb RAM (512Mb recommend)
Hard disk space : 100Mb or higher in free space
Screen resolution: 1024*768
Internet connection : 56kbps dial up (Broadband recommended)
Software : Microsoft .NET framework 1.1 - Will install automatically if not present already

2. Do I need to create a new partion to hold the virtual disk created by virtualbox?
3. My existing partions are all formatted as ext3. Does this cause an issue with XP or is it all handled by the VirtualBox software?
4. Are there any specific tweaks I have to make in order to get the 'Windows' system to use my network connection, usb devices etc?
5. Do I need to install any other applications other than VirtualBox, XP and the trading software?
6. What sort of impact on PC performance can I expect?
7. I presume that the VirtualBox only runs when I need to launch my Windows OS or is it loaded at boot up?

No doubt I'll probably think of other questions later, but that will do for now.

Thanks in advance

---

### Post by scragar on 2008-07-15
> **AlistairH said:**
> 1. First of all, are there any issues with the specification of my machine?

Dual Core P4 3Ghz CPU
2GB Memory
SiS Graphics card - no intense graphics required and not running compiz
30GB root partion
150GB Home partition with 135GB free.
Screen Res 1440 x 900

The minimum spec for the Windows application I'd probably use is:
Operating system : Windows 2000, XP or Vista
CPU: Pentium 4 or AMD equivalent
RAM :256Mb RAM (512Mb recommend)
Hard disk space : 100Mb or higher in free space
Screen resolution: 1024*768
Internet connection : 56kbps dial up (Broadband recommended)
Software : Microsoft .NET framework 1.1 - Will install automatically if not present already
I run a virtualbox faily often on a lower system giving up about half of my 1GB ram to run a certain game, so your system is fine.
> 2. Do I need to create a new partion to hold the virtual disk created by virtualbox?
3. My existing partions are all formatted as ext3. Does this cause an issue with XP or is it all handled by the VirtualBox software?no to both, the hard drive for the virtualbox is what's called an image(think of an .iso file, you can mount it as a CD, the virtualbox is just a step further letting writing happen instead of being read only).
> 4. Are there any specific tweaks I have to make in order to get the 'Windows' system to use my network connection, usb devices etc?you may need to do a few small tweaks to get USB working, nothing impossibly hard.
> 5. Do I need to install any other applications other than VirtualBox, XP and the trading software?nothing that I can thinkoff.
> 6. What sort of impact on PC performance can I expect?depends, you will have the same impact on performance as running windows, but with a small added lag from Vbox itself.
> 7. I presume that the VirtualBox only runs when I need to launch my Windows OS or is it loaded at boot up?you launch it as needed.
> 
No doubt I'll probably think of other questions later, but that will do for now.

k, let me know them.> 
Thanks in advanceYour welcome :P

EDIT: [https://help.ubuntu.com/community/VirtualBox#Open%20Source%20Edition%20on%20Ubuntu%208.04%20(Hardy)](https://help.ubuntu.com/community/VirtualBox#Open%20Source%20Edition%20on%20Ubuntu%208.04%20(Hardy))

---

### Post by WRDN on 2008-07-15
Is it possible to make the program run in WINE?

---

### Post by AlistairH on 2008-07-15
Thanks for the replies folks.

WRDN: It won't run in WINE as the application is based on the .NET Framework which, at the moment doesn't work correctly in WINE. As this application involves me trading my hard earned cash, the last thing I'm going to do is use software that isn't 100% working.

SCRAGAR: I've managed to install VirtualBox quite happily, but when I go to install Win XP, I get the following error message popping up:

```
VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel and execute '/etc/init.d/vboxdrv start' as root.
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}
```

According to Synaptic PM the virtualbox-ose-modules package is already installed and the vboxdrv start command outlined above produces:

```
 * Starting VirtualBox kernel module vboxdrv                                    FATAL: Module vboxdrv not found.

 * Modprobe vboxdrv failed. Please use 'dmesg' to find out why.
```

I reinstalled the package, but I get the same error.

Running dmesg produces produces:
```
[    0.000000] Linux version 2.6.22-15-generic (buildd@terranova) (gcc version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Tue Jun 10 09:21:34 UTC 2008 (Ubuntu 2.6.22-15.54-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f400 (usable)
[    0.000000]  BIOS-e820: 000000000009f400 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007dff0000 (usable)
[    0.000000]  BIOS-e820: 000000007dff0000 - 000000007dff3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007dff3000 - 000000007e000000 (ACPI data)
[    0.000000]  BIOS-e820: 00000000fec00000 - 0000000100000000 (reserved)
[    0.000000] 1119MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f3ee0
[    0.000000] Entering add_active_range(0, 0, 516080) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   516080
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   516080
[    0.000000] On node 0 totalpages: 516080
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2239 pages used for memmap
[    0.000000]   HighMem zone: 284465 pages, LIFO batch:31
[    0.000000] DMI 2.2 present.
[    0.000000] ACPI: RSDP signature @ 0xC00F8030 checksum 0
[    0.000000] ACPI: RSDP 000F8030, 0014 (r0 AWARD )
[    0.000000] ACPI: RSDT 7DFF3040, 002C (r1 AWARD  AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: FACP 7DFF30C0, 0074 (r1 AWARD  AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: DSDT 7DFF3180, 3EDE (r1 AWARD  AWRDACPI     1000 MSFT  100000E)
[    0.000000] ACPI: FACS 7DFF0000, 0040
[    0.000000] ACPI: APIC 7DFF70C0, 0084 (r1 AWARD  AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:4 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] Processor #1 15:4 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x02] disabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x03] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x02] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x03] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x04] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 4, version 20, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 dfl dfl)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 80000000 (gap: 7e000000:80c00000)
[    0.000000] Built 1 zonelists.  Total pages: 512049
[    0.000000] Kernel command line: root=UUID=c3133e83-19e7-4e38-93a9-6940b1ed532b ro splash vga=771
[    0.000000] mapped APIC to ffffd000 (fee00000)
[    0.000000] mapped IOAPIC to ffffc000 (fec00000)
[    0.000000] Enabling fast FPU save and restore... done.
[    0.000000] Enabling unmasked SIMD FPU exception support... done.
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    0.000000] Detected 3000.452 MHz processor.
[   27.397129] Console: colour dummy device 80x25
[   27.397846] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[   27.398397] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[   27.494147] Memory: 2035104k/2064320k available (2016k kernel code, 27936k reserved, 919k data, 364k init, 1146816k highmem)
[   27.494171] virtual kernel memory layout:
[   27.494172]     fixmap  : 0xfff4d000 - 0xfffff000   ( 712 kB)
[   27.494173]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   27.494174]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[   27.494175]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[   27.494177]       .init : 0xc03e3000 - 0xc043e000   ( 364 kB)
[   27.494178]       .data : 0xc02f8036 - 0xc03dde84   ( 919 kB)
[   27.494179]       .text : 0xc0100000 - 0xc02f8036   (2016 kB)
[   27.494192] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   27.494251] SLUB: Genslabs=22, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   27.574210] Calibrating delay using timer specific routine.. 6004.38 BogoMIPS (lpj=12008769)
[   27.574254] Security Framework v1.0.0 initialized
[   27.574265] SELinux:  Disabled at boot.
[   27.574281] Mount-cache hash table entries: 512
[   27.574465] CPU: After generic identify, caps: bfebfbff 00100000 00000000 00000000 0000441d 00000000 00000000
[   27.574474] monitor/mwait feature present.
[   27.574477] using mwait in idle threads.
[   27.574486] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   27.574491] CPU: L2 cache: 1024K
[   27.574495] CPU: Physical Processor ID: 0
[   27.574498] CPU: After all inits, caps: bfebfbff 00100000 00000000 0000b180 0000441d 00000000 00000000
[   27.574512] Compat vDSO mapped to ffffe000.
[   27.574534] Checking 'hlt' instruction... OK.
[   27.590374] SMP alternatives: switching to UP code
[   27.591054] Early unpacking initramfs... done
[   27.876430] ACPI: Core revision 20070126
[   27.876491] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   27.897293] CPU0: Intel(R) Pentium(R) 4 CPU 3.00GHz stepping 01
[   27.897322] SMP alternatives: switching to SMP code
[   27.897458] Booting processor 1/1 eip 3000
[   27.907665] Initializing CPU#1
[   27.985844] Calibrating delay using timer specific routine.. 6000.68 BogoMIPS (lpj=12001361)
[   27.985856] CPU: After generic identify, caps: bfebfbff 00100000 00000000 00000000 0000441d 00000000 00000000
[   27.985863] monitor/mwait feature present.
[   27.985871] CPU: Trace cache: 12K uops, L1 D cache: 16K
[   27.985874] CPU: L2 cache: 1024K
[   27.985877] CPU: Physical Processor ID: 0
[   27.985879] CPU: After all inits, caps: bfebfbff 00100000 00000000 0000b180 0000441d 00000000 00000000
[   27.986261] CPU1: Intel(R) Pentium(R) 4 CPU 3.00GHz stepping 01
[   27.986322] Total of 2 processors activated (12005.06 BogoMIPS).
[   27.986423] ENABLING IO-APIC IRQs
[   27.986605] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[   28.026287] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
[   28.026291] ...trying to set up timer (IRQ0) through the 8259A ...  failed.
[   28.026297] ...trying to set up timer as Virtual Wire IRQ... works.
[   28.173807] checking TSC synchronization [CPU#0 -> CPU#1]: passed.
[   28.193808] Brought up 2 CPUs
[   28.339309] migration_cost=246
[   28.339522] Booting paravirtualized kernel on bare hardware
[   28.339603] Time: 15:32:38  Date: 06/15/108
[   28.339634] NET: Registered protocol family 16
[   28.339741] EISA bus registered
[   28.339749] ACPI: bus type pci registered
[   28.341284] PCI: PCI BIOS revision 2.10 entry at 0xfa270, last bus=1
[   28.341287] PCI: Using configuration type 1
[   28.341290] Setting up standard PCI resources
[   28.346176] ACPI: EC: Look up EC in DSDT
[   28.350737] ACPI: Interpreter enabled
[   28.350750] ACPI: (supports S0 S3 S4 S5)
[   28.350776] ACPI: Using IOAPIC for interrupt routing
[   28.356926] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   28.356940] PCI: Probing PCI hardware (bus 00)
[   28.357800] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   28.375582] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[   28.375699] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[   28.375812] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[   28.375923] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[   28.376035] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[   28.376146] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[   28.376259] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[   28.376371] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[   28.376496] Linux Plug and Play Support v0.97 (c) Adam Belay
[   28.376510] pnp: PnP ACPI init
[   28.376520] ACPI: bus type pnp registered
[   28.379473] pnp: PnP ACPI: found 12 devices
[   28.379478] ACPI: ACPI bus type pnp unregistered
[   28.379484] PnPBIOS: Disabled by ACPI PNP
[   28.379544] PCI: Using ACPI for IRQ routing
[   28.379549] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   28.385469] NET: Registered protocol family 8
[   28.385473] NET: Registered protocol family 20
[   28.385508] Time: tsc clocksource has been installed.
[   28.385560] pnp: 00:00: iomem range 0xf0000-0xf3fff could not be reserved
[   28.385565] pnp: 00:00: iomem range 0xf4000-0xf7fff could not be reserved
[   28.385569] pnp: 00:00: iomem range 0xf8000-0xfbfff could not be reserved
[   28.385574] pnp: 00:00: iomem range 0xfc000-0xfffff could not be reserved
[   28.415931] PCI: Bridge: 0000:00:01.0
[   28.415937]   IO window: d000-dfff
[   28.415944]   MEM window: ec000000-ec0fffff
[   28.415950]   PREFETCH window: e0000000-e7ffffff
[   28.415974] NET: Registered protocol family 2
[   28.453644] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[   28.453777] TCP established hash table entries: 131072 (order: 8, 1572864 bytes)
[   28.455122] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[   28.455753] TCP: Hash tables configured (established 131072 bind 65536)
[   28.455758] TCP reno registered
[   28.465843] checking if image is initramfs... it is
[   28.913373] Switched to high resolution mode on CPU 1
[   28.917227] Switched to high resolution mode on CPU 0
[   29.046223] Freeing initrd memory: 7068k freed
[   29.046936] audit: initializing netlink socket (disabled)
[   29.046958] audit(1216135958.224:1): initialized
[   29.047085] highmem bounce pool size: 64 pages
[   29.049529] VFS: Disk quotas dquot_6.5.1
[   29.049595] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   29.049711] io scheduler noop registered
[   29.049715] io scheduler anticipatory registered
[   29.049718] io scheduler deadline registered
[   29.049735] io scheduler cfq registered (default)
[   37.041855] 0000:00:03.3 EHCI: BIOS handoff failed (BIOS bug ?) 01010001
[   37.041879] Boot video device is 0000:01:00.0
[   37.042065] isapnp: Scanning for PnP cards...
[   37.393627] isapnp: No Plug & Play device found
[   37.421262] Real Time Clock Driver v1.12ac
[   37.421392] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   37.421496] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   37.421718] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   37.422349] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   37.422627] 00:09: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   37.423447] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   37.423722] input: Macintosh mouse button emulation as /class/input/input0
[   37.423817] PNP: PS/2 Controller [PNP0f13:PS2M] at 0x60,0x64 irq 12
[   37.423822] PNP: PS/2 controller doesn't have KBD irq; using default 1
[   37.424104] serio: i8042 KBD port at 0x60,0x64 irq 1
[   37.424119] serio: i8042 AUX port at 0x60,0x64 irq 12
[   37.424613] mice: PS/2 mouse device common for all mice
[   37.424749] EISA: Probing bus 0 at eisa.0
[   37.424761] Cannot allocate resource for EISA slot 1
[   37.424773] Cannot allocate resource for EISA slot 4
[   37.424792] EISA: Detected 0 cards.
[   37.424898] TCP cubic registered
[   37.424911] NET: Registered protocol family 1
[   37.424936] Using IPI No-Shortcut mode
[   37.425102]   Magic number: 0:202:538
[   37.425736] Freeing unused kernel memory: 364k freed
[   38.665190] AppArmor: AppArmor initialized<5>audit(1216135967.724:2):  type=1505 info="AppArmor initialized" pid=1203
[   38.674286] fuse init (API version 7.8)
[   38.680728] Failure registering capabilities with primary security module.
[   38.709438] ACPI: Fan [FAN] (on)
[   38.715372] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
[   38.715389] ACPI Exception (processor_core-0783): AE_NOT_FOUND, Processor Device is not present [20070126]
[   38.716677] ACPI: Thermal Zone [THRM] (62 C)
[   39.309097] usbcore: registered new interface driver usbfs
[   39.309139] usbcore: registered new interface driver hub
[   39.309232] usbcore: registered new device driver usb
[   39.310426] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   39.310477] ACPI: PCI Interrupt 0000:00:03.0[A] -> GSI 20 (level, low) -> IRQ 16
[   39.310497] ohci_hcd 0000:00:03.0: OHCI Host Controller
[   39.310697] ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus number 1
[   39.310720] ohci_hcd 0000:00:03.0: irq 16, io mem 0xec124000
[   39.336742] SCSI subsystem initialized
[   39.345543] libata version 2.21 loaded.
[   39.382251] usb usb1: configuration #1 chosen from 1 choice
[   39.382308] hub 1-0:1.0: USB hub found
[   39.382324] hub 1-0:1.0: 3 ports detected
[   39.398780] sis900.c: v1.08.10 Apr. 2 2006
[   39.471515] FDC 0 is a post-1991 82077
[   39.484244] ACPI: PCI Interrupt 0000:00:03.1[B] -> GSI 21 (level, low) -> IRQ 17
[   39.484268] ohci_hcd 0000:00:03.1: OHCI Host Controller
[   39.484470] ohci_hcd 0000:00:03.1: new USB bus registered, assigned bus number 2
[   39.484492] ohci_hcd 0000:00:03.1: irq 17, io mem 0xec120000
[   39.541798] usb usb2: configuration #1 chosen from 1 choice
[   39.541848] hub 2-0:1.0: USB hub found
[   39.541863] hub 2-0:1.0: 3 ports detected
[   39.643698] ACPI: PCI Interrupt 0000:00:03.2[C] -> GSI 22 (level, low) -> IRQ 18
[   39.643720] ohci_hcd 0000:00:03.2: OHCI Host Controller
[   39.643757] ohci_hcd 0000:00:03.2: new USB bus registered, assigned bus number 3
[   39.643777] ohci_hcd 0000:00:03.2: irq 18, io mem 0xec121000
[   39.701627] usb usb3: configuration #1 chosen from 1 choice
[   39.701670] hub 3-0:1.0: USB hub found
[   39.701684] hub 3-0:1.0: 2 ports detected
[   39.803599] pata_sis 0000:00:02.5: version 0.5.1
[   39.803648] ACPI: PCI Interrupt 0000:00:02.5[A] -> GSI 16 (level, low) -> IRQ 19
[   39.803810] scsi0 : pata_sis
[   39.804242] scsi1 : pata_sis
[   39.804432] ata1: PATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x00014000 irq 14
[   39.804437] ata2: PATA max UDMA/133 cmd 0x00010170 ctl 0x00010376 bmdma 0x00014008 irq 15
[   39.935321] usb 2-1: new low speed USB device using ohci_hcd and address 2
[   40.009546] ata1.00: ATA-7: ST3200820A, 3.AAE, max UDMA/100
[   40.009551] ata1.00: 390721968 sectors, multi 16: LBA48 
[   40.076035] ata1.00: configured for UDMA/100
[   40.154123] usb 2-1: configuration #1 chosen from 1 choice
[   40.395157] ata2.00: ATAPI: SONY    DVD RW AW-G170A, 1.71, max UDMA/66
[   40.458846] usb 3-1: new full speed USB device using ohci_hcd and address 2
[   40.570997] ata2.00: configured for UDMA/66
[   40.571166] scsi 0:0:0:0: Direct-Access     ATA      ST3200820A       3.AA PQ: 0 ANSI: 5
[   40.572162] scsi 1:0:0:0: CD-ROM            SONY     DVD RW AW-G170A  1.71 PQ: 0 ANSI: 5
[   40.572573] ACPI: PCI Interrupt 0000:00:03.3[D] -> GSI 23 (level, low) -> IRQ 20
[   40.572593] ehci_hcd 0000:00:03.3: EHCI Host Controller
[   40.572805] ehci_hcd 0000:00:03.3: new USB bus registered, assigned bus number 4
[   40.572853] PCI: cache line size of 128 is not supported by device 0000:00:03.3
[   40.572869] ehci_hcd 0000:00:03.3: irq 20, io mem 0xec122000
[   40.634695] ehci_hcd 0000:00:03.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   40.634848] usb usb4: configuration #1 chosen from 1 choice
[   40.634900] hub 4-0:1.0: USB hub found
[   40.634914] hub 4-0:1.0: 8 ports detected
[   40.739291] ACPI: PCI Interrupt 0000:00:04.0[A] -> GSI 19 (level, low) -> IRQ 21
[   40.740352] 0000:00:04.0: SiS 900 on Foxconn 661 7MI transceiver found at address 1.
[   40.750870] 0000:00:04.0: Using transceiver found at address 1 as default
[   40.754888] eth0: SiS 900 PCI Fast Ethernet at 0xe400, IRQ 21, 00:15:58:4a:cf:a6.
[   40.755960] sata_sis 0000:00:05.0: version 0.8
[   40.756008] ACPI: PCI Interrupt 0000:00:05.0[A] -> GSI 17 (level, low) -> IRQ 22
[   40.756019] sata_sis 0000:00:05.0: Detected SiS 180/181/964 chipset in SATA mode
[   40.756152] scsi2 : sata_sis
[   40.756255] scsi3 : sata_sis
[   40.756432] ata3: SATA max UDMA/133 cmd 0x0001e900 ctl 0x0001ea02 bmdma 0x0001ed00 irq 22
[   40.756444] ata4: SATA max UDMA/133 cmd 0x0001eb00 ctl 0x0001ec02 bmdma 0x0001ed08 irq 22
[   40.776011] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[   40.776019] Uniform CD-ROM driver Revision: 3.20
[   40.776344] sr 1:0:0:0: Attached scsi CD-ROM sr0
[   40.781542] sd 0:0:0:0: [sda] 390721968 512-byte hardware sectors (200050 MB)
[   40.781568] sd 0:0:0:0: [sda] Write Protect is off
[   40.781574] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   40.781605] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   40.781699] sd 0:0:0:0: [sda] 390721968 512-byte hardware sectors (200050 MB)
[   40.781716] sd 0:0:0:0: [sda] Write Protect is off
[   40.781720] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   40.781746] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   40.781753]  sda:<5>sd 0:0:0:0: Attached scsi generic sg0 type 0
[   40.784368] sr 1:0:0:0: Attached scsi generic sg1 type 5
[   40.805452]  sda1 sda2 sda3
[   40.815154] sd 0:0:0:0: [sda] Attached SCSI disk
[   41.042339] usb 3-1: device not accepting address 2, error -62
[   41.062363] ata3: SATA link down (SStatus 0 SControl 3F0)
[   41.095514] Attempting manual resume
[   41.095520] swsusp: Resume From Partition 8:2
[   41.095522] PM: Checking swsusp image.
[   41.095778] PM: Resume from disk failed.
[   41.137263] kjournald starting.  Commit interval 5 seconds
[   41.137278] EXT3-fs: mounted filesystem with ordered data mode.
[   41.226220] usb 2-1: USB disconnect, address 2
[   41.382080] ata4: SATA link down (SStatus 0 SControl 3F0)
[   41.781690] usb 4-3: new high speed USB device using ehci_hcd and address 3
[   41.915881] usb 4-3: configuration #1 chosen from 1 choice
[   41.916204] usbcore: registered new interface driver hiddev
[   42.217283] usb 2-1: new low speed USB device using ohci_hcd and address 3
[   42.419595] usb 2-1: configuration #1 chosen from 1 choice
[   42.430755] input: Dell Dell USB Keyboard as /class/input/input1
[   42.430769] input: USB HID v1.10 Keyboard [Dell Dell USB Keyboard] on usb-0000:00:03.1-1
[   42.430783] usbcore: registered new interface driver usbhid
[   42.430787] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   48.270656] input: PC Speaker as /class/input/input2
[   48.348480] Linux agpgart interface v0.102 (c) Dave Jones
[   48.513188] agpgart: Detected SiS chipset - id:1633
[   48.518458] agpgart: AGP aperture is 64M @ 0xe8000000
[   48.585246] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   48.588188] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   48.759283] usbcore: registered new interface driver libusual
[   48.799971] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   48.799979] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   48.803649] Initializing USB Mass Storage driver...
[   48.803790] scsi4 : SCSI emulation for USB Mass Storage devices
[   48.803908] usbcore: registered new interface driver usb-storage
[   48.803914] USB Mass Storage support registered.
[   48.804097] usb-storage: device found at 3
[   48.804101] usb-storage: waiting for device to settle before scanning
[   48.976838] ACPI: PCI Interrupt 0000:00:02.7[C] -> GSI 18 (level, low) -> IRQ 23
[   49.095268] input: ImPS/2 Generic Wheel Mouse as /class/input/input3
[   49.098783] parport_pc 00:0a: reported by Plug and Play ACPI
[   49.098838] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   49.299047] intel8x0_measure_ac97_clock: measured 54892 usecs
[   49.299052] intel8x0: clocking to 48000
[   50.304247] lp0: using parport0 (interrupt-driven).
[   50.359696] Adding 8024k swap on /dev/sda2.  Priority:-1 extents:1 across:8024k
[   50.625703] EXT3 FS on sda1, internal journal
[   51.179019] kjournald starting.  Commit interval 5 seconds
[   51.179245] EXT3 FS on sda3, internal journal
[   51.179251] EXT3-fs: mounted filesystem with ordered data mode.
[   51.932773] No dock devices found.
[   51.988524] input: Power Button (FF) as /class/input/input4
[   51.988560] ACPI: Power Button (FF) [PWRF]
[   51.988623] input: Power Button (CM) as /class/input/input5
[   51.988688] ACPI: Power Button (CM) [PWRB]
[   53.342843] Failure registering capabilities with primary security module.
[   53.553640] ppdev: user-space parallel port driver
[   53.729435] NET: Registered protocol family 10
[   53.729733] lo: Disabled Privacy Extensions
[   53.799376] usb-storage: device scan complete
[   53.804133] scsi 4:0:0:0: Direct-Access     ST340014 A                0000 PQ: 0 ANSI: 0
[   53.805487] sd 4:0:0:0: [sdb] 78165360 512-byte hardware sectors (40021 MB)
[   53.806378] sd 4:0:0:0: [sdb] Write Protect is off
[   53.806385] sd 4:0:0:0: [sdb] Mode Sense: 27 00 00 00
[   53.806391] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[   53.807217] sd 4:0:0:0: [sdb] 78165360 512-byte hardware sectors (40021 MB)
[   53.808091] sd 4:0:0:0: [sdb] Write Protect is off
[   53.808097] sd 4:0:0:0: [sdb] Mode Sense: 27 00 00 00
[   53.808102] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[   53.808109]  sdb: sdb1
[   53.813459] sd 4:0:0:0: [sdb] Attached SCSI disk
[   53.813534] sd 4:0:0:0: Attached scsi generic sg2 type 0
[   53.908697] audit(1216135983.667:3):  type=1503 operation="inode_permission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=4819 profile="/usr/sbin/cupsd"
[   55.618108] eth0: Media Link On 100mbps full-duplex 
[   58.784717] NET: Registered protocol family 17
[   71.173440] eth0: no IPv6 routers present
[  251.623293] sr0: CDROM not ready.  Make sure there is a disc in the drive.
[  340.094375] UDF-fs: No VRS found
[  880.191754] sr0: CDROM not ready.  Make sure there is a disc in the drive.
[ 5385.437997] sr0: CDROM not ready.  Make sure there is a disc in the drive.
[ 5895.051235] UDF-fs: No VRS found
```

I cannot see anything obvious in that, but then, I'm not certain what I'm looking for.


Any ideas where to go from here?

---

### Post by bumanie on 2008-07-15
Follow [this guide]("http://www.ubuntu1501.com/2007/12/installing-virtualbox-with-usb-support.html") it should work. But as you are using vbox for commerce, you should stick with the ose version (as you have done :)).

---

### Post by fidamehran on 2008-07-21
Guys, is it at all a good idea to be virtualizing one OS inside another? Specially a snobbish OS like Windows?

---

### Post by scragar on 2008-07-21
virtualisation may mean the OS runs a bit slower, and consumes a bit more ram than would be hoped for, but the lack of need to reboot and the better support for things like saved states etc makes a virtualbox a better solution for a lot of things.

---

### Post by AlistairH on 2008-07-21
> **fidamehran said:**
> Guys, is it at all a good idea to be virtualizing one OS inside another? Specially a snobbish OS like Windows?

If I wish to carry on using Ubuntu, then I have no choice. The software I need is no longer available for Linux and I have to use Windows based software.

I've still to purchase the required software, but even running it in VirtualBox may not be enough depending on any lag caused by the virtualisation software. It is the very nature of what I'll be doing that I may need to get in and out of the market very quickly. If the lag is too great, then it could cost me money. If that is the case, then I will have no option but to abandon Linux and go back to Windows.

---

### Post by Dunrobin on 2008-07-21
> **bumanie said:**
> Follow [this guide]("http://www.ubuntu1501.com/2007/12/installing-virtualbox-with-usb-support.html") it should work. But as you are using vbox for commerce, you should stick with the ose version (as you have done :)).

Thank you for posting that link, bumanie.  That was *exactly* what I was looking for.  :)

---

### Post by ladr0n on 2008-07-21
I run the music composition software Sibelius (think: big fat nasty obese program, especially when dealing with larger scores) in an XP virtualbox and it's more responsive than the same program was under native Vista.  You probably won't notice your app running any more slowly under vbox than it would on a native XP install.

---

### Post by crhylove on 2008-11-07
Not true.  My XP VMs are noticeably slower than a native XP OS.  However, everything on my computer runs faster than anything would on Vista.  In fact, my Vista VM runs faster than anything on Vista.  That's hugely ironic in my opinion, but stated as a true and demonstrable fact.  Other great programs in an XP VM:

Civilization 2.
Zsnes (with working joystick, Intrepid has no joystick support at all)
Winamp 2.81
Firefox and Flash (much better than native in Ubuntu)
Need For Speed 3: Hot Pursuit
Shareaza
uTorrent
VLC
Hydrogen (Open Source Drum Synth)

I highly recommend using MicroXP as your installation media.  It is technically piracy but if you have a valid XP license, I don't see how or why anyone would ever come after you.  The MicroXP iso is handy to keep around too, since it is < 100 mb!!!!!  I keep a copy right next to my VM .vdi, for the inevitable little odd times I need an ISO for a driver/program to finish installing.  MicroXP is a much more efficient and high performance OS than standard XP, and it works for everything *i* need.  Your mileage may vary though.

---

### Post by AlistairH on 2008-11-23
Thanks crhylove for the info regarding Micro XP. What's the most reliable source for this as searching the web seems to through up no end of download sites, some of which I wouldn't trust with a barge pole.

---

### Post by MystaMax on 2008-11-24
If you have your own copy of XP, you can create your own "MicroXP" using [nLiteOS]("http://www.nliteos.com/"). Its a much more legit way of going about slimming down your XP install. Its what I do, and XP boots in seconds (I actually never shutdown my XP VM, I just "save" its current state to disk). My slimmed XP install ISO is only about 250 MBs.

I have Photoshop CS3, Fireworks CS3, and Illustrator CS3 running in XP VM, and haven't noticed much of a slow down. In my opinion, my applications launch/run just as fast in my VM as they do natively. If there is a difference, I haven't noticed it.

One thing I did have to be careful w/ was when my PC started swapping; this drastically changed the performance of my VM. On my laptop, I only have 2GBs of RAM, and usually have tons of apps open. Now, I just have to be cautious when using my VMs, and running all of the CS3 suite inside. My desktop (4GB) never has this problem.

Understand that your situation will be different from others. While crhylove states his XP VMs are noticably slower, mine are not. I will say that my Vista VMs do consume a lot of memory.

---

### Post by theDaveTheRave on 2008-11-26
Dear All,

I have a virtualisation question, that I've not yet found a definitive answer too... so if anyone out there can help I would be forever gratefull (as would my boss no doubt!);


My situation.

Currently I run a dualboot XP and Ubuntu system.

My personal preference is too work on the Ubuntu system all the time (I've used linux for years now and found working in windows extremely painfull at times!)

What I want to do is run the XP partition inside of a VM (or similar) on my ubuntu system.

However, we don't have any XP system disks, and all my "programs" that I really need are sitting on my XP partition.

From what I have read I would need to create the virtual system as if I was creating a "new instal of XP", however as I have XP working fine on the extra partition on my computer this would seem a bit daft, can I not simply use the install that I allready have and boot straight into it??

From what I have read I have a few option:

Create an image of my XP, then create a "bootable" system disk from my instalation. Open a Virtualisation tool and set it up to hold XP...

Again to me this seems uneccesary due to having a fully functional XP system on my computer... also it is going to take a while to get set up!

but then I guess that is the case for anything!

thanks for the help in advance.

Dave

---

