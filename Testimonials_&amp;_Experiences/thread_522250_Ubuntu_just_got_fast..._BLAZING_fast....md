---
title: "Ubuntu just got fast... BLAZING fast..."
date: 2007-08-10
forum: Testimonials &amp; Experiences
---

### Post by sab0403 on 2007-08-10
*** UPDATE! See last post for details ***

I think this is the appropiate forum for this...

SHORT VERSION: I tinkered with partitions, and somehow I ended up with a much, much faster bootup for Ubuntu. See bottom for different outputs of dmesg in case you're interested in figuring out the why.

LONG VERSION (warning: *really long*): Anyway, I've been tinkering with my HD/partitions the last couple of days, mainly because I needed to edit some video *fast*, and since I haven't found a decent video editor for Linux, I though - hey, why not use the restore DVD for my laptop and temporarily install WinXP and the editing tools that accompany it (it's a Sony VAIO, so it has a lot of tools). Before I did anything, my partitions looked like this:

| Ubuntu: 24 Gb | Debian: 4 Gb | Swap: 2 Gb | Data (mounted as home): 68 Gb |

Anyway, I used [this tutorial]("http://ubuntuforums.org/showthread.php?t=35087") and backed up my Ubuntu partition in a tarball (I use a separate partition for home, so that was easy). Then I proceeded to restore the PC's 'C' drive to XP (which, for some reason, only worked when I erased the Ubuntu partition, hence the backup). After I was done, I decided to keep the 

Windows partition around for a while in case this happened again. Right now my HD looks like this:

| WinXP: 30 Gb | Data (not mounted, being ext3): 68 Gb |

So I shrunk the XP partition to the bare minimum for it to work (since it had a lot of Sony and associated software, that's 10 Gb, with considerations for the swap file). I was left with about 20 Gb of free space. Now, normally I would leave everything back as it was (so 2 Gb for swap, 4 Gb for Debian and the rest - 14 Gb - for Ubuntu). However I noticed the tarball was quite small, and even when restored it would use slightly above 3 Gb. So I thought (since I'm sort of testing different distros): why not create an extended partition in that space, hence freeing up a "slot" for another primary (in case I wanted to create a share partition for Windows, for instance), and within that extended, logical partitions for Ubuntu, Debian and the swap. Plus - [COLOR="Red"]and this is the part that must've caused the speed up[/COLOR], since I can't see any other one - only use the space the OSs actually use, plus a little wiggle room. So without further ado, my HD now looks like this:

                                                          EXTENDED PARTITION                               
| WinXP: 10 Gb || Ubuntu: 5 Gb | Debian: 2 Gb | Swap: 2 Gb | Unused: 11 Gb || Data (mounted as home): 68 Gb |

So after this I restored the Ubuntu partition with tar (via the LiveCD), then I reinstalled GRUB. I adjusted the corresponding fstab and menu.lst files to match the new partitions, and I booted up. Normally (read: > 2 minutes). That was yesterday.

TODAY: I woke up, and since I poweroff every day, I booted up. Suddenly I heard the drums of the login screen. I turned around half-sleep, thinking "this day is going fast for me". I logon, but I thought this couldn't be just my imagination. So I outputted dmesg to a file. What I saw, my friends, was outstanding. I attatch both dmesg ouputs (a previous one I did when trying to make Ubuntu quicker, and today's). If you can pinpoint the reason why it's so fast, you'll earn a cookie.

Anyway, just wanted to share my experience. Good day! :popcorn:

dmesg (previous): ```
[    0.000000] Linux version 2.6.20-16-generic (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Thu Jun 7 20:19:32 UTC 2007 (Ubuntu 2.6.20-16.29-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009f800 end: 000000000009f800 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009f800 size: 0000000000000800 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000d8000 size: 0000000000028000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000003f590000 end: 000000003f690000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000003f690000 size: 0000000000015000 end: 000000003f6a5000 type: 3
[    0.000000] copy_e820_map() start: 000000003f6a5000 size: 000000000005b000 end: 000000003f700000 type: 4
[    0.000000] copy_e820_map() start: 000000003f700000 size: 0000000000900000 end: 0000000040000000 type: 2
[    0.000000] copy_e820_map() start: 00000000e0000000 size: 0000000010006000 end: 00000000f0006000 type: 2
[    0.000000] copy_e820_map() start: 00000000f0008000 size: 0000000000004000 end: 00000000f000c000 type: 2
[    0.000000] copy_e820_map() start: 00000000fed20000 size: 0000000000070000 end: 00000000fed90000 type: 2
[    0.000000] copy_e820_map() start: 00000000ff000000 size: 0000000001000000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d8000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003f690000 (usable)
[    0.000000]  BIOS-e820: 000000003f690000 - 000000003f6a5000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003f6a5000 - 000000003f700000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003f700000 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0006000 (reserved)
[    0.000000]  BIOS-e820: 00000000f0008000 - 00000000f000c000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed20000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] 118MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 259728) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   259728
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   259728
[    0.000000] On node 0 totalpages: 259728
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 237 pages used for memmap
[    0.000000]   HighMem zone: 30115 pages, LIFO batch:7
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP (v000 PTLTD                                 ) @ 0x000f68b0
[    0.000000] ACPI: RSDT (v001 SONY   Xy       0x06040000  LTP 0x00000000) @ 0x3f69f54e
[    0.000000] ACPI: FADT (v002 SONY   X6       0x06040000 LOHR 0x20050429) @ 0x3f6a4eb0
[    0.000000] ACPI: MADT (v001 INTEL  ALVISO   0x06040000 LOHR 0x0000005f) @ 0x3f6a4f34
[    0.000000] ACPI: MCFG (v001 INTEL  ALVISO   0x06040000 LOHR 0x0000005f) @ 0x3f6a4f9c
[    0.000000] ACPI: BOOT (v001 PTLTD  $SBFTBL$ 0x06040000  LTP 0x00000001) @ 0x3f6a4fd8
[    0.000000] ACPI: SSDT (v001 SataRe  SataPri 0x00001000 INTL 0x20030224) @ 0x3f6a03fc
[    0.000000] ACPI: SSDT (v001 SataRe  SataSec 0x00001000 INTL 0x20030224) @ 0x3f69fd6a
[    0.000000] ACPI: SSDT (v001  PmRef  Cpu0Ist 0x00003000 INTL 0x20030224) @ 0x3f69f925
[    0.000000] ACPI: SSDT (v001  PmRef  Cpu0Cst 0x00003001 INTL 0x20030224) @ 0x3f69f7af
[    0.000000] ACPI: SSDT (v001  PmRef    CpuPm 0x00003000 INTL 0x20030224) @ 0x3f69f596
[    0.000000] ACPI: DSDT (v001 SONY   X6       0x06040000 MSFT 0x0100000e) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:13 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:a0000000)
[    0.000000] Detected 1862.023 MHz processor.
[    7.374693] Built 1 zonelists.  Total pages: 257699
[    7.374697] Kernel command line: root=UUID=2d2f4049-e1e5-4770-9533-0e1e93e59cef ro quiet splash
[    7.374843] mapped APIC to ffffd000 (fee00000)
[    7.374846] mapped IOAPIC to ffffc000 (fec00000)
[    7.374848] Enabling fast FPU save and restore... done.
[    7.374851] Enabling unmasked SIMD FPU exception support... done.
[    7.374859] Initializing CPU#0
[    7.374929] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    7.376693] Console: colour VGA+ 80x25
[    7.377008] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    7.377407] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    7.406283] Memory: 1018732k/1038912k available (1992k kernel code, 19400k reserved, 900k data, 328k init, 121408k highmem)
[    7.406292] virtual kernel memory layout:
[    7.406293]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[    7.406294]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    7.406295]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[    7.406296]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[    7.406298]       .init : 0xc03d9000 - 0xc042b000   ( 328 kB)
[    7.406299]       .data : 0xc02f2374 - 0xc03d36d4   ( 900 kB)
[    7.406300]       .text : 0xc0100000 - 0xc02f2374   (1992 kB)
[    7.406303] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[    7.482757] Calibrating delay using timer specific routine.. 3728.02 BogoMIPS (lpj=7456057)
[    7.482794] Security Framework v1.0.0 initialized
[    7.482800] SELinux:  Disabled at boot.
[    7.482814] Mount-cache hash table entries: 512
[    7.482938] CPU: After generic identify, caps: afe9fbff 00100000 00000000 00000000 00000180 00000000 00000000
[    7.482949] CPU: L1 I cache: 32K, L1 D cache: 32K
[    7.482951] CPU: L2 cache: 2048K
[    7.482953] CPU: After all inits, caps: afe9fbff 00100000 00000000 00002040 00000180 00000000 00000000
[    7.482962] Compat vDSO mapped to ffffe000.
[    7.482965] Remapping vsyscall page to ffffe000
[    7.482975] Checking 'hlt' instruction... OK.
[    7.498813] SMP alternatives: switching to UP code
[    7.498976] Freeing SMP alternatives: 11k freed
[    7.499136] Early unpacking initramfs... done
[    7.801926] ACPI: Core revision 20060707
[    7.802287] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[    7.924328] CPU0: Intel(R) Pentium(R) M processor 1.86GHz stepping 08
[    7.924350] Total of 1 processors activated (3728.02 BogoMIPS).
[    7.924545] ENABLING IO-APIC IRQs
[    7.924738] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[    8.069811] Brought up 1 CPUs
[    8.070023] Booting paravirtualized kernel on bare hardware
[    8.070097] Time: 16:47:27  Date: 06/31/107
[    8.070120] NET: Registered protocol family 16
[    8.070192] EISA bus registered
[    8.070196] ACPI: bus type pci registered
[    8.070533] PCI: PCI BIOS revision 2.10 entry at 0xfd92e, last bus=7
[    8.070535] PCI: Using configuration type 1
[    8.070537] Setting up standard PCI resources
[    8.075660] ACPI: Interpreter enabled
[    8.075662] ACPI: Using IOAPIC for interrupt routing
[    8.076197] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    8.076202] PCI: Probing PCI hardware (bus 00)
[    8.076836] Boot video device is 0000:00:02.0
[    8.077330] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[    8.077334] PCI quirk: region 1180-11bf claimed by ICH6 GPIO
[    8.077897] PCI: Transparent bridge - 0000:00:1e.0
[    8.077964] PCI: Bus #07 (-#0a) is hidden behind transparent bridge #06 (-#07) (try 'pci=assign-busses')
[    8.077967] Please report the result to linux-kernel to fix this permanently
[    8.077990] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    8.081872] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    8.082542] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[    8.082736] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    8.082929] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 *3 4 5 6 7 10 12 14 15)
[    8.083124] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    8.083315] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[    8.083509] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    8.083701] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 *7 10 12 14 15)
[    8.083890] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 *5 6 7 11 12 14 15)
[    8.088212] Linux Plug and Play Support v0.97 (c) Adam Belay
[    8.088269] pnp: PnP ACPI init
[    8.089631] pnp: PnP ACPI: found 8 devices
[    8.089636] PnPBIOS: Disabled by ACPI PNP
[    8.089667] PCI: Using ACPI for IRQ routing
[    8.089669] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    8.107065] NET: Registered protocol family 8
[    8.107067] NET: Registered protocol family 20
[    8.107706] PCI: Ignore bogus resource 6 [0:0] of 0000:00:02.0
[    8.107720] PCI: Bus 7, cardbus bridge: 0000:06:09.0
[    8.107722]   IO window: 00002400-000024ff
[    8.107728]   IO window: 00002800-000028ff
[    8.107733]   PREFETCH window: 50000000-53ffffff
[    8.107738]   MEM window: 58000000-5bffffff
[    8.107743] PCI: Bridge: 0000:00:1e.0
[    8.107746]   IO window: 2000-2fff
[    8.107751]   MEM window: b0100000-b01fffff
[    8.107756]   PREFETCH window: 50000000-53ffffff
[    8.107773] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[    8.107830] ACPI: PCI Interrupt 0000:06:09.0[A] -> GSI 20 (level, low) -> IRQ 16
[    8.107851] NET: Registered protocol family 2
[    8.137716] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    8.137808] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    8.138553] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    8.139005] TCP: Hash tables configured (established 131072 bind 65536)
[    8.139008] TCP reno registered
[    8.149779] checking if image is initramfs... it is
[    8.737942] Freeing initrd memory: 6768k freed
[    8.738164] Simple Boot Flag at 0x35 set to 0x1
[    8.738382] audit: initializing netlink socket (disabled)
[    8.738396] audit(1185900447.332:1): initialized
[    8.738465] highmem bounce pool size: 64 pages
[    8.738524] VFS: Disk quotas dquot_6.5.1
[    8.738543] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    8.738593] io scheduler noop registered
[    8.738596] io scheduler anticipatory registered
[    8.738598] io scheduler deadline registered
[    8.738606] io scheduler cfq registered (default)
[    8.738868] isapnp: Scanning for PnP cards...
[    9.092531] isapnp: No Plug & Play device found
[    9.113988] Real Time Clock Driver v1.12ac
[    9.114040] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    9.114635] mice: PS/2 mouse device common for all mice
[    9.115115] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    9.115337] input: Macintosh mouse button emulation as /class/input/input0
[    9.115367] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[    9.115371] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[    9.115586] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    9.118510] serio: i8042 KBD port at 0x60,0x64 irq 1
[    9.118514] serio: i8042 AUX port at 0x60,0x64 irq 12
[    9.118619] EISA: Probing bus 0 at eisa.0
[    9.118628] Cannot allocate resource for EISA slot 1
[    9.118630] Cannot allocate resource for EISA slot 2
[    9.118654] EISA: Detected 0 cards.
[    9.148700] TCP cubic registered
[    9.148710] NET: Registered protocol family 1
[    9.148730] Using IPI No-Shortcut mode
[    9.148788] ACPI: (supports S0 S3 S4 S5)
[    9.148833]   Magic number: 15:269:794
[    9.148915]   hash matches device ptyr2
[    9.149103] Freeing unused kernel memory: 328k freed
[    9.151975] Time: tsc clocksource has been installed.
[    9.167690] input: AT Translated Set 2 keyboard as /class/input/input1
[   10.350870] Capability LSM initialized
[   10.380872] ACPI: CPU0 (power states: C1[C1] C2[C2])
[   10.380876] ACPI: Processor [CPU0] (supports 8 throttling states)
[   10.380884] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[   10.382910] ACPI: Thermal Zone [TZ01] (71 C)
[   10.685643] usbcore: registered new interface driver usbfs
[   10.685663] usbcore: registered new interface driver hub
[   10.685679] usbcore: registered new device driver usb
[   10.686373] USB Universal Host Controller Interface driver v3.0
[   10.686418] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 18 (level, low) -> IRQ 17
[   10.686429] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   10.686433] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   10.686562] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   10.686591] uhci_hcd 0000:00:1d.0: irq 17, io base 0x00001820
[   10.686686] usb usb1: configuration #1 chosen from 1 choice
[   10.686705] hub 1-0:1.0: USB hub found
[   10.686709] hub 1-0:1.0: 2 ports detected
[   10.742887] SCSI subsystem initialized
[   10.761358] libata version 2.20 loaded.
[   10.774944] 8139too Fast Ethernet driver 0.9.28
[   10.792613] ieee1394: Initialized config rom entry `ip1394'
[   10.793770] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 22 (level, low) -> IRQ 18
[   10.793782] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   10.793786] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   10.793811] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   10.793844] uhci_hcd 0000:00:1d.1: irq 18, io base 0x00001840
[   10.793923] usb usb2: configuration #1 chosen from 1 choice
[   10.793946] hub 2-0:1.0: USB hub found
[   10.793951] hub 2-0:1.0: 2 ports detected
[   10.901136] PCI: Enabling device 0000:00:1d.2 (0000 -> 0001)
[   10.901145] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 17
[   10.901157] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   10.901160] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   10.901182] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   10.901207] uhci_hcd 0000:00:1d.2: irq 17, io base 0x00001080
[   10.901289] usb usb3: configuration #1 chosen from 1 choice
[   10.901310] hub 3-0:1.0: USB hub found
[   10.901315] hub 3-0:1.0: 2 ports detected
[    3.324000] Time: acpi_pm clocksource has been installed.
[    3.464000] PCI: Enabling device 0000:00:1d.3 (0000 -> 0001)
[    3.464000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 19
[    3.464000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[    3.464000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    3.464000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[    3.464000] uhci_hcd 0000:00:1d.3: irq 19, io base 0x000010a0
[    3.464000] usb usb4: configuration #1 chosen from 1 choice
[    3.464000] hub 4-0:1.0: USB hub found
[    3.464000] hub 4-0:1.0: 2 ports detected
[    3.740000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 18 (level, low) -> IRQ 17
[    3.740000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    3.740000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    3.740000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[    3.740000] ehci_hcd 0000:00:1d.7: debug port 1
[    3.740000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[    3.740000] ehci_hcd 0000:00:1d.7: irq 17, io mem 0xb0004000
[    3.744000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.744000] usb usb5: configuration #1 chosen from 1 choice
[    3.744000] hub 5-0:1.0: USB hub found
[    3.744000] hub 5-0:1.0: 8 ports detected
[    3.852000] ahci 0000:00:1f.2: version 2.1
[    3.852000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 20
[    3.852000] ACPI: PCI interrupt for device 0000:00:1f.2 disabled
[    3.852000] ahci: probe of 0000:00:1f.2 failed with error -22
[    3.852000] ata_piix 0000:00:1f.2: version 2.10ac1
[    3.852000] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[    4.124000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 20
[    4.124000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[    4.124000] ata1: SATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x00011870 irq 14
[    4.124000] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x00011878 irq 15
[    4.124000] scsi0 : ata_piix
[    4.596000] ata1.00: ata_hpa_resize 1: sectors = 195371568, hpa_sectors = 195371568
[    4.596000] ata1.00: ATA-6: TOSHIBA MK1032GSX, AS021G, max UDMA/100
[    4.596000] ata1.00: 195371568 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    4.768000] ata1.00: ata_hpa_resize 1: sectors = 195371568, hpa_sectors = 195371568
[    4.768000] ata1.00: configured for UDMA/100
[    4.768000] scsi1 : ata_piix
[    5.696000] ata2.00: ATAPI, max UDMA/33
[    7.496000] ata2.00: configured for UDMA/33
[    7.496000] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK1032GS AS02 PQ: 0 ANSI: 5
[    7.504000] scsi 1:0:0:0: CD-ROM            PIONEER  DVD-RW  DVR-K16D 1.00 PQ: 0 ANSI: 5
[    7.508000] ACPI: PCI Interrupt 0000:06:08.0[A] -> GSI 17 (level, low) -> IRQ 21
[    7.508000] eth0: RealTek RTL8139 at 0xf8834000, 00:01:4a:f8:a8:27, IRQ 21
[    7.508000] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[    7.508000] ACPI: PCI Interrupt 0000:06:09.2[C] -> GSI 22 (level, low) -> IRQ 18
[    7.560000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[18]  MMIO=[b0104800-b0104fff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    7.560000] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    7.576000] SCSI device sda: 195371568 512-byte hdwr sectors (100030 MB)
[    7.576000] sda: Write Protect is off
[    7.576000] sda: Mode Sense: 00 3a 00 00
[    7.576000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.576000] SCSI device sda: 195371568 512-byte hdwr sectors (100030 MB)
[    7.576000] sda: Write Protect is off
[    7.576000] sda: Mode Sense: 00 3a 00 00
[    7.576000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.576000]  sda: sda1 sda2 sda3 sda4
[    7.628000] sd 0:0:0:0: Attached scsi disk sda
[    7.636000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    7.636000] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    7.684000] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    7.684000] Uniform CD-ROM driver Revision: 3.20
[    7.684000] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    7.876000] usb 5-5: new high speed USB device using ehci_hcd and address 3
[    7.920000] kjournald starting.  Commit interval 5 seconds
[    7.920000] EXT3-fs: mounted filesystem with ordered data mode.
[    8.072000] usb 5-5: configuration #1 chosen from 1 choice
[    9.432000] usb 2-1: new low speed USB device using uhci_hcd and address 2
[    9.696000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[080046030209696f]
[   10.096000] usb 2-1: configuration #1 chosen from 1 choice
[   27.928000] Linux agpgart interface v0.102 (c) Dave Jones
[   27.936000] agpgart: Detected an Intel 915GM Chipset.
[   27.936000] agpgart: Detected 7932K stolen memory.
[   27.952000] agpgart: AGP aperture is 256M @ 0xc0000000
[   28.212000] iTCO_vendor_support: vendor-support=0
[   28.228000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
[   28.228000] iTCO_wdt: Found a ICH6-M TCO device (Version=2, TCOBASE=0x1060)
[   28.228000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   28.236000] ACPI: PCI Interrupt 0000:06:09.3[B] -> GSI 21 (level, low) -> IRQ 22
[   28.272000] tifm_core: MMC/SD card detected in socket 0:0
[   28.276000] Yenta: CardBus bridge found at 0000:06:09.0 [104d:81f1]
[   28.276000] Yenta: Enabling burst memory read transactions
[   28.276000] Yenta: Using CSCINT to route CSC interrupts to PCI
[   28.276000] Yenta: Routing CardBus interrupts to PCI
[   28.276000] Yenta TI: socket 0000:06:09.0, mfunc 0x000a1b22, devctl 0x64
[   28.344000] intel_rng: FWH not detected
[   28.472000] ieee80211_crypt: registered algorithm 'NULL'
[   28.476000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   28.476000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   28.536000] Yenta: ISA IRQ mask 0x0cf8, PCI irq 16
[   28.536000] Socket status: 30000006
[   28.536000] Yenta: Raising subordinate bus# of parent bus (#06) from #07 to #0a
[   28.536000] pcmcia: parent PCI bridge I/O window: 0x2000 - 0x2fff
[   28.536000] cs: IO port probe 0x2000-0x2fff: clean.
[   28.536000] pcmcia: parent PCI bridge Memory window: 0xb0100000 - 0xb01fffff
[   28.536000] pcmcia: parent PCI bridge Memory window: 0x50000000 - 0x53ffffff
[   28.628000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 20 (level, low) -> IRQ 16
[   28.628000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   28.676000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.0kmprq
[   28.676000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   28.740000] input: PS/2 Mouse as /class/input/input2
[   28.760000] input: AlpsPS/2 ALPS GlidePoint as /class/input/input3
[   30.084000] hda_intel: azx_get_response timeout, switching to polling mode...
[   30.112000] usbcore: registered new interface driver hiddev
[   31.264000] hda_intel: azx_get_response timeout, switching to single_cmd mode...
[   31.284000] ACPI: PCI Interrupt 0000:06:0a.0[A] -> GSI 23 (level, low) -> IRQ 23
[   31.284000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   31.528000] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
[   31.540000] input: Genius       NetScroll+Mini Traveler as /class/input/input4
[   31.540000] input: USB HID v1.10 Mouse [Genius       NetScroll+Mini Traveler] on usb-0000:00:1d.1-1
[   31.540000] usbcore: registered new interface driver usbhid
[   31.540000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   31.896000] Linux video capture interface: v2.00
[   32.412000] cs: IO port probe 0x100-0x3af: clean.
[   32.412000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   32.412000] cs: IO port probe 0x820-0x8ff: clean.
[   32.412000] cs: IO port probe 0xc00-0xcf7: clean.
[   32.416000] cs: IO port probe 0xa00-0xaff: clean.
[   32.568000] ubuntu/media/gspcav1/gspca_core.c: USB SPCA5XX camera found.(VC0321) 
[   32.792000] usbcore: registered new interface driver gspca
[   32.792000] ubuntu/media/gspcav1/gspca_core.c: gspca driver 01.00.12 registered
[   33.892000] fuse init (API version 7.8)
[   34.372000] lp: driver loaded but no devices found
[   34.996000] Adding 2048276k swap on /dev/sda2.  Priority:-1 extents:1 across:2048276k
[   36.364000] EXT3 FS on sda1, internal journal
[   37.288000] kjournald starting.  Commit interval 5 seconds
[   37.288000] EXT3 FS on sda3, internal journal
[   37.288000] EXT3-fs: mounted filesystem with ordered data mode.
[   41.516000] NET: Registered protocol family 17
[   57.460000] ACPI: Battery Slot [BAT1] (battery present)
[   57.472000] Using specific hotkey driver
[   59.116000] No dock devices found.
[   59.124000] ACPI: Video Device [GFX0] (multi-head: yes  rom: yes  post: no)
[   59.132000] ACPI: AC Adapter [ACAD] (on-line)
[   59.152000] ibm_acpi: ec object not found
[   60.380000] input: Power Button (FF) as /class/input/input5
[   60.380000] ACPI: Power Button (FF) [PWRF]
[   60.380000] input: Lid Switch as /class/input/input6
[   60.380000] ACPI: Lid Switch [LID0]
[   60.384000] input: Power Button (CM) as /class/input/input7
[   60.384000] ACPI: Power Button (CM) [PWRB]
[   60.524000] ACPI Sony Notebook Control Driver v0.2 successfully installed
[   60.540000] pcc_acpi: loading...
[   73.588000] eth0: link down
[   79.424000] ppdev: user-space parallel port driver
[   85.884000] apm: BIOS not found.
[   87.084000] sonypi: Sony Programmable I/O Controller Driver v1.26.
[   87.108000] sonypi: detected type3 model, verbose = 0, fnkeyinit = off, camera = off, compat = off, mask = 0xffffffff, useinput = on, acpi = on
[   87.108000] sonypi: enabled at irq=11, port1=0x10c0, port2=0x10c4
[   87.108000] sonypi: device allocated minor is 62
[   87.212000] input: Sony Vaio Jogdial as /class/input/input8
[   87.288000] input: Sony Vaio Keys as /class/input/input9
[   87.352000] sonypi command failed at drivers/char/sonypi.c : sonypi_call1 (line 646)
[   87.396000] sonypi command failed at drivers/char/sonypi.c : sonypi_call2 (line 657)
[   87.436000] sonypi command failed at drivers/char/sonypi.c : sonypi_call2 (line 659)
[   87.480000] sonypi command failed at drivers/char/sonypi.c : sonypi_call1 (line 646)
[   88.796000] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
[   89.232000] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[   89.248000] NFSD: starting 90-second grace period
[   92.972000] vmmon: module license 'unspecified' taints kernel.
[   92.976000] /dev/vmmon[5209]: VMCI: Driver initialized.
[   92.980000] /dev/vmmon[5209]: Module vmmon: registered with major=10 minor=165
[   92.980000] /dev/vmmon[5209]: Module vmmon: initialized
[   93.468000] /dev/vmnet: open called by PID 5254 (vmnet-bridge)
[   93.468000] /dev/vmnet: hub 0 does not exist, allocating memory.
[   93.468000] /dev/vmnet: port on hub 0 successfully opened
[   93.468000] bridge-eth1: enabling the bridge
[   93.468000] bridge-eth1: is a Wireless Adapter
[   93.468000] bridge-eth1: up
[   93.468000] bridge-eth1: already up
[   93.468000] bridge-eth1: attached
[   93.924000] /dev/vmnet: open called by PID 5266 (vmnet-netifup)
[   93.924000] /dev/vmnet: hub 1 does not exist, allocating memory.
[   93.924000] /dev/vmnet: port on hub 1 successfully opened
[   94.160000] /dev/vmnet: open called by PID 5271 (vmnet-dhcpd)
[   94.160000] /dev/vmnet: port on hub 1 successfully opened
[   94.164000] /dev/vmnet: open called by PID 5288 (vmnet-netifup)
[   94.164000] /dev/vmnet: hub 8 does not exist, allocating memory.
[   94.164000] /dev/vmnet: port on hub 8 successfully opened
[   94.320000] /dev/vmnet: open called by PID 5295 (vmnet-dhcpd)
[   94.324000] /dev/vmnet: port on hub 8 successfully opened
[   94.348000] /dev/vmnet: open called by PID 5308 (vmnet-natd)
[   94.348000] /dev/vmnet: port on hub 8 successfully opened
[  208.236000] ieee80211_crypt: registered algorithm 'WEP'
[  395.536000] /dev/vmnet: open called by PID 6194 (vmware-vmx)
[  395.536000] /dev/vmnet: port on hub 8 successfully opened
[  395.972000] /dev/vmmon[6231]: host clock rate change request 0 -> 19
[  395.972000] /dev/vmmon[6231]: host clock rate change request 19 -> 83
```
dmesg (current): ```
[    0.000000] Linux version 2.6.20-16-generic (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Thu Jun 7 20:19:32 UTC 2007 (Ubuntu 2.6.20-16.29-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009f800 end: 000000000009f800 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009f800 size: 0000000000000800 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000d8000 size: 0000000000028000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000003f590000 end: 000000003f690000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000003f690000 size: 0000000000015000 end: 000000003f6a5000 type: 3
[    0.000000] copy_e820_map() start: 000000003f6a5000 size: 000000000005b000 end: 000000003f700000 type: 4
[    0.000000] copy_e820_map() start: 000000003f700000 size: 0000000000900000 end: 0000000040000000 type: 2
[    0.000000] copy_e820_map() start: 00000000e0000000 size: 0000000010006000 end: 00000000f0006000 type: 2
[    0.000000] copy_e820_map() start: 00000000f0008000 size: 0000000000004000 end: 00000000f000c000 type: 2
[    0.000000] copy_e820_map() start: 00000000fed20000 size: 0000000000070000 end: 00000000fed90000 type: 2
[    0.000000] copy_e820_map() start: 00000000ff000000 size: 0000000001000000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d8000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000003f690000 (usable)
[    0.000000]  BIOS-e820: 000000003f690000 - 000000003f6a5000 (ACPI data)
[    0.000000]  BIOS-e820: 000000003f6a5000 - 000000003f700000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000003f700000 - 0000000040000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0006000 (reserved)
[    0.000000]  BIOS-e820: 00000000f0008000 - 00000000f000c000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed20000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff000000 - 0000000100000000 (reserved)
[    0.000000] 118MB HIGHMEM available.
[    0.000000] 896MB LOWMEM available.
[    0.000000] Entering add_active_range(0, 0, 259728) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   229376
[    0.000000]   HighMem    229376 ->   259728
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   259728
[    0.000000] On node 0 totalpages: 259728
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 1760 pages used for memmap
[    0.000000]   Normal zone: 223520 pages, LIFO batch:31
[    0.000000]   HighMem zone: 237 pages used for memmap
[    0.000000]   HighMem zone: 30115 pages, LIFO batch:7
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP (v000 PTLTD                                 ) @ 0x000f68b0
[    0.000000] ACPI: RSDT (v001 SONY   Xy       0x06040000  LTP 0x00000000) @ 0x3f69f54e
[    0.000000] ACPI: FADT (v002 SONY   X6       0x06040000 LOHR 0x20050429) @ 0x3f6a4eb0
[    0.000000] ACPI: MADT (v001 INTEL  ALVISO   0x06040000 LOHR 0x0000005f) @ 0x3f6a4f34
[    0.000000] ACPI: MCFG (v001 INTEL  ALVISO   0x06040000 LOHR 0x0000005f) @ 0x3f6a4f9c
[    0.000000] ACPI: BOOT (v001 PTLTD  $SBFTBL$ 0x06040000  LTP 0x00000001) @ 0x3f6a4fd8
[    0.000000] ACPI: SSDT (v001 SataRe  SataPri 0x00001000 INTL 0x20030224) @ 0x3f6a03fc
[    0.000000] ACPI: SSDT (v001 SataRe  SataSec 0x00001000 INTL 0x20030224) @ 0x3f69fd6a
[    0.000000] ACPI: SSDT (v001  PmRef  Cpu0Ist 0x00003000 INTL 0x20030224) @ 0x3f69f925
[    0.000000] ACPI: SSDT (v001  PmRef  Cpu0Cst 0x00003001 INTL 0x20030224) @ 0x3f69f7af
[    0.000000] ACPI: SSDT (v001  PmRef    CpuPm 0x00003000 INTL 0x20030224) @ 0x3f69f596
[    0.000000] ACPI: DSDT (v001 SONY   X6       0x06040000 MSFT 0x0100000e) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 6:13 APIC version 20
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 50000000 (gap: 40000000:a0000000)
[    0.000000] Detected 1862.132 MHz processor.
[    8.101645] Built 1 zonelists.  Total pages: 257699
[    8.101649] Kernel command line: root=UUID=13b658e3-b92f-4200-8f2c-64fd2da77d5b ro quiet splash
[    8.101795] mapped APIC to ffffd000 (fee00000)
[    8.101797] mapped IOAPIC to ffffc000 (fec00000)
[    8.101800] Enabling fast FPU save and restore... done.
[    8.101802] Enabling unmasked SIMD FPU exception support... done.
[    8.101812] Initializing CPU#0
[    8.101882] PID hash table entries: 4096 (order: 12, 16384 bytes)
[    8.103643] Console: colour VGA+ 80x25
[    8.103958] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    8.104360] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    8.132916] Memory: 1018732k/1038912k available (1992k kernel code, 19400k reserved, 900k data, 328k init, 121408k highmem)
[    8.132925] virtual kernel memory layout:
[    8.132926]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[    8.132927]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    8.132928]     vmalloc : 0xf8800000 - 0xff7fe000   ( 111 MB)
[    8.132929]     lowmem  : 0xc0000000 - 0xf8000000   ( 896 MB)
[    8.132930]       .init : 0xc03d9000 - 0xc042b000   ( 328 kB)
[    8.132932]       .data : 0xc02f2374 - 0xc03d36d4   ( 900 kB)
[    8.132933]       .text : 0xc0100000 - 0xc02f2374   (1992 kB)
[    8.132936] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[    8.209710] Calibrating delay using timer specific routine.. 3728.04 BogoMIPS (lpj=7456099)
[    8.209747] Security Framework v1.0.0 initialized
[    8.209753] SELinux:  Disabled at boot.
[    8.209769] Mount-cache hash table entries: 512
[    8.209891] CPU: After generic identify, caps: afe9fbff 00100000 00000000 00000000 00000180 00000000 00000000
[    8.209902] CPU: L1 I cache: 32K, L1 D cache: 32K
[    8.209904] CPU: L2 cache: 2048K
[    8.209906] CPU: After all inits, caps: afe9fbff 00100000 00000000 00002040 00000180 00000000 00000000
[    8.209915] Compat vDSO mapped to ffffe000.
[    8.209918] Remapping vsyscall page to ffffe000
[    8.209929] Checking 'hlt' instruction... OK.
[    8.225766] SMP alternatives: switching to UP code
[    8.225929] Freeing SMP alternatives: 11k freed
[    8.226090] Early unpacking initramfs... done
[    8.528828] ACPI: Core revision 20060707
[    8.529188] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[    8.626827] CPU0: Intel(R) Pentium(R) M processor 1.86GHz stepping 08
[    8.626850] Total of 1 processors activated (3728.04 BogoMIPS).
[    8.627048] ENABLING IO-APIC IRQs
[    8.627241] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[    8.772805] Brought up 1 CPUs
[    8.773017] Booting paravirtualized kernel on bare hardware
[    8.773091] Time: 13:25:44  Date: 07/10/107
[    8.773116] NET: Registered protocol family 16
[    8.773187] EISA bus registered
[    8.773190] ACPI: bus type pci registered
[    8.773526] PCI: PCI BIOS revision 2.10 entry at 0xfd92e, last bus=7
[    8.773528] PCI: Using configuration type 1
[    8.773529] Setting up standard PCI resources
[    8.778645] ACPI: Interpreter enabled
[    8.778647] ACPI: Using IOAPIC for interrupt routing
[    8.779185] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    8.779191] PCI: Probing PCI hardware (bus 00)
[    8.779826] Boot video device is 0000:00:02.0
[    8.780323] PCI quirk: region 1000-107f claimed by ICH6 ACPI/GPIO/TCO
[    8.780327] PCI quirk: region 1180-11bf claimed by ICH6 GPIO
[    8.780889] PCI: Transparent bridge - 0000:00:1e.0
[    8.780955] PCI: Bus #07 (-#0a) is hidden behind transparent bridge #06 (-#07) (try 'pci=assign-busses')
[    8.780957] Please report the result to linux-kernel to fix this permanently
[    8.780979] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    8.784859] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[    8.785530] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[    8.785723] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    8.785915] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 *3 4 5 6 7 10 12 14 15)
[    8.786109] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    8.786300] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[    8.786495] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    8.786687] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 *7 10 12 14 15)
[    8.786876] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 *5 6 7 11 12 14 15)
[    8.790109] Linux Plug and Play Support v0.97 (c) Adam Belay
[    8.790116] pnp: PnP ACPI init
[    8.792323] pnp: PnP ACPI: found 8 devices
[    8.792328] PnPBIOS: Disabled by ACPI PNP
[    8.792358] PCI: Using ACPI for IRQ routing
[    8.792361] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[    8.809834] NET: Registered protocol family 8
[    8.809836] NET: Registered protocol family 20
[    8.810153] PCI: Ignore bogus resource 6 [0:0] of 0000:00:02.0
[    8.810168] PCI: Bus 7, cardbus bridge: 0000:06:09.0
[    8.810170]   IO window: 00002400-000024ff
[    8.810176]   IO window: 00002800-000028ff
[    8.810181]   PREFETCH window: 50000000-53ffffff
[    8.810186]   MEM window: 58000000-5bffffff
[    8.810191] PCI: Bridge: 0000:00:1e.0
[    8.810194]   IO window: 2000-2fff
[    8.810200]   MEM window: b0100000-b01fffff
[    8.810205]   PREFETCH window: 50000000-53ffffff
[    8.810223] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[    8.810279] ACPI: PCI Interrupt 0000:06:09.0[A] -> GSI 20 (level, low) -> IRQ 16
[    8.810300] NET: Registered protocol family 2
[    8.848691] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    8.848783] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    8.849531] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    8.849981] TCP: Hash tables configured (established 131072 bind 65536)
[    8.849984] TCP reno registered
[    8.860756] checking if image is initramfs... it is
[    9.449017] Freeing initrd memory: 6768k freed
[    9.449237] Simple Boot Flag at 0x35 set to 0x1
[    9.449456] audit: initializing netlink socket (disabled)
[    9.449469] audit(1186752344.340:1): initialized
[    9.449537] highmem bounce pool size: 64 pages
[    9.449598] VFS: Disk quotas dquot_6.5.1
[    9.449617] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    9.449667] io scheduler noop registered
[    9.449670] io scheduler anticipatory registered
[    9.449672] io scheduler deadline registered
[    9.449680] io scheduler cfq registered (default)
[    9.449944] isapnp: Scanning for PnP cards...
[    9.803635] isapnp: No Plug & Play device found
[    9.825486] Real Time Clock Driver v1.12ac
[    9.825539] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[    9.826151] mice: PS/2 mouse device common for all mice
[    9.826638] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    9.826863] input: Macintosh mouse button emulation as /class/input/input0
[    9.826893] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[    9.826897] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[    9.827172] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    9.831145] serio: i8042 KBD port at 0x60,0x64 irq 1
[    9.831149] serio: i8042 AUX port at 0x60,0x64 irq 12
[    9.831250] EISA: Probing bus 0 at eisa.0
[    9.831257] Cannot allocate resource for EISA slot 1
[    9.831260] Cannot allocate resource for EISA slot 2
[    9.831284] EISA: Detected 0 cards.
[    9.861329] TCP cubic registered
[    9.861339] NET: Registered protocol family 1
[    9.861358] Using IPI No-Shortcut mode
[    9.861416] ACPI: (supports S0 S3 S4 S5)
[    9.861460]   Magic number: 3:515:432
[    9.861728] Freeing unused kernel memory: 328k freed
[    9.862954] Time: tsc clocksource has been installed.
[    9.881081] input: AT Translated Set 2 keyboard as /class/input/input1
[   11.061715] Capability LSM initialized
[   11.091708] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3] C4[C3])
[   11.091713] ACPI: Processor [CPU0] (supports 8 throttling states)
[   11.091721] ACPI Exception (acpi_processor-0677): AE_NOT_FOUND, Processor Device is not present [20060707]
[   11.094551] ACPI: Thermal Zone [TZ01] (41 C)
[   11.396474] usbcore: registered new interface driver usbfs
[   11.396493] usbcore: registered new interface driver hub
[   11.396510] usbcore: registered new device driver usb
[   11.397206] USB Universal Host Controller Interface driver v3.0
[   11.397252] ACPI: PCI Interrupt 0000:00:1d.0[A] -> GSI 18 (level, low) -> IRQ 17
[   11.397263] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[   11.397267] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[   11.397399] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[   11.397428] uhci_hcd 0000:00:1d.0: irq 17, io base 0x00001820
[   11.397523] usb usb1: configuration #1 chosen from 1 choice
[   11.397542] hub 1-0:1.0: USB hub found
[   11.397547] hub 1-0:1.0: 2 ports detected
[   11.449321] SCSI subsystem initialized
[   11.472387] libata version 2.20 loaded.
[   11.485029] 8139too Fast Ethernet driver 0.9.28
[   11.502661] ACPI: PCI Interrupt 0000:00:1d.1[B] -> GSI 22 (level, low) -> IRQ 18
[   11.502673] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[   11.502677] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[   11.502705] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[   11.502736] uhci_hcd 0000:00:1d.1: irq 18, io base 0x00001840
[   11.502820] usb usb2: configuration #1 chosen from 1 choice
[   11.502841] hub 2-0:1.0: USB hub found
[   11.502847] hub 2-0:1.0: 2 ports detected
[   11.502947] ieee1394: Initialized config rom entry `ip1394'
[   11.604183] PCI: Enabling device 0000:00:1d.2 (0000 -> 0001)
[   11.604192] ACPI: PCI Interrupt 0000:00:1d.2[C] -> GSI 18 (level, low) -> IRQ 17
[   11.604204] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[   11.604208] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[   11.604228] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[   11.604254] uhci_hcd 0000:00:1d.2: irq 17, io base 0x00001080
[   11.604336] usb usb3: configuration #1 chosen from 1 choice
[   11.604357] hub 3-0:1.0: USB hub found
[   11.604362] hub 3-0:1.0: 2 ports detected
[    3.340000] Time: acpi_pm clocksource has been installed.
[    3.420000] PCI: Enabling device 0000:00:1d.3 (0000 -> 0001)
[    3.420000] ACPI: PCI Interrupt 0000:00:1d.3[D] -> GSI 16 (level, low) -> IRQ 19
[    3.420000] PCI: Setting latency timer of device 0000:00:1d.3 to 64
[    3.420000] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    3.420000] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 4
[    3.420000] uhci_hcd 0000:00:1d.3: irq 19, io base 0x000010a0
[    3.420000] usb usb4: configuration #1 chosen from 1 choice
[    3.420000] hub 4-0:1.0: USB hub found
[    3.420000] hub 4-0:1.0: 2 ports detected
[    3.524000] ACPI: PCI Interrupt 0000:00:1d.7[A] -> GSI 18 (level, low) -> IRQ 17
[    3.524000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[    3.524000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    3.524000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 5
[    3.524000] ehci_hcd 0000:00:1d.7: debug port 1
[    3.524000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[    3.524000] ehci_hcd 0000:00:1d.7: irq 17, io mem 0xb0004000
[    3.528000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[    3.528000] usb usb5: configuration #1 chosen from 1 choice
[    3.528000] hub 5-0:1.0: USB hub found
[    3.528000] hub 5-0:1.0: 8 ports detected
[    3.632000] ahci 0000:00:1f.2: version 2.1
[    3.632000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 20
[    3.632000] ACPI: PCI interrupt for device 0000:00:1f.2 disabled
[    3.632000] ahci: probe of 0000:00:1f.2 failed with error -22
[    3.632000] ata_piix 0000:00:1f.2: version 2.10ac1
[    3.632000] ata_piix 0000:00:1f.2: MAP [ P0 P2 IDE IDE ]
[    3.788000] ACPI: PCI Interrupt 0000:00:1f.2[B] -> GSI 19 (level, low) -> IRQ 20
[    3.788000] PCI: Setting latency timer of device 0000:00:1f.2 to 64
[    3.788000] ata1: SATA max UDMA/133 cmd 0x000101f0 ctl 0x000103f6 bmdma 0x00011870 irq 14
[    3.788000] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x00011878 irq 15
[    3.788000] scsi0 : ata_piix
[    3.916000] usb 5-5: new high speed USB device using ehci_hcd and address 2
[    3.952000] ata1.00: ata_hpa_resize 1: sectors = 195371568, hpa_sectors = 195371568
[    3.952000] ata1.00: ATA-6: TOSHIBA MK1032GSX, AS021G, max UDMA/100
[    3.952000] ata1.00: 195371568 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    3.960000] ata1.00: ata_hpa_resize 1: sectors = 195371568, hpa_sectors = 195371568
[    3.960000] ata1.00: configured for UDMA/100
[    3.960000] scsi1 : ata_piix
[    4.072000] usb 5-5: configuration #1 chosen from 1 choice
[    4.296000] ata2.00: ATAPI, max UDMA/33
[    4.476000] ata2.00: configured for UDMA/33
[    4.476000] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK1032GS AS02 PQ: 0 ANSI: 5
[    4.484000] scsi 1:0:0:0: CD-ROM            PIONEER  DVD-RW  DVR-K16D 1.00 PQ: 0 ANSI: 5
[    4.488000] ACPI: PCI Interrupt 0000:06:08.0[A] -> GSI 17 (level, low) -> IRQ 21
[    4.488000] eth0: RealTek RTL8139 at 0xf8834000, 00:01:4a:f8:a8:27, IRQ 21
[    4.488000] eth0:  Identified 8139 chip type 'RTL-8100B/8139D'
[    4.492000] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    4.492000] ACPI: PCI Interrupt 0000:06:09.2[C] -> GSI 22 (level, low) -> IRQ 18
[    4.540000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[18]  MMIO=[b0104800-b0104fff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    4.556000] SCSI device sda: 195371568 512-byte hdwr sectors (100030 MB)
[    4.556000] sda: Write Protect is off
[    4.556000] sda: Mode Sense: 00 3a 00 00
[    4.556000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.556000] SCSI device sda: 195371568 512-byte hdwr sectors (100030 MB)
[    4.556000] sda: Write Protect is off
[    4.556000] sda: Mode Sense: 00 3a 00 00
[    4.556000] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.556000]  sda: sda1 sda2 sda3 <sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    4.596000] Uniform CD-ROM driver Revision: 3.20
[    4.596000] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    4.600000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    4.600000] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    4.600000]  sda5 sda6 sda7 >
[    4.624000] sd 0:0:0:0: Attached scsi disk sda
[    4.984000] kjournald starting.  Commit interval 5 seconds
[    4.984000] EXT3-fs: mounted filesystem with ordered data mode.
[    5.812000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[080046030209696f]
[    8.380000] Linux agpgart interface v0.102 (c) Dave Jones
[    8.432000] agpgart: Detected an Intel 915GM Chipset.
[    8.432000] agpgart: Detected 7932K stolen memory.
[    8.524000] agpgart: AGP aperture is 256M @ 0xc0000000
[    9.052000] iTCO_vendor_support: vendor-support=0
[    9.104000] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
[    9.104000] iTCO_wdt: Found a ICH6-M TCO device (Version=2, TCOBASE=0x1060)
[    9.104000] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[    9.304000] ACPI: PCI Interrupt 0000:06:09.3[B] -> GSI 21 (level, low) -> IRQ 22
[    9.324000] intel_rng: FWH not detected
[    9.340000] tifm_core: MMC/SD card detected in socket 0:0
[    9.396000] ieee80211_crypt: registered algorithm 'NULL'
[    9.396000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[    9.396000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[    9.440000] Yenta: CardBus bridge found at 0000:06:09.0 [104d:81f1]
[    9.440000] Yenta: Enabling burst memory read transactions
[    9.440000] Yenta: Using CSCINT to route CSC interrupts to PCI
[    9.440000] Yenta: Routing CardBus interrupts to PCI
[    9.440000] Yenta TI: socket 0000:06:09.0, mfunc 0x000a1b22, devctl 0x64
[    9.484000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.0kmprq
[    9.484000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[    9.572000] Linux video capture interface: v2.00
[    9.684000] Yenta: ISA IRQ mask 0x0cf8, PCI irq 16
[    9.684000] Socket status: 30000006
[    9.684000] Yenta: Raising subordinate bus# of parent bus (#06) from #07 to #0a
[    9.684000] pcmcia: parent PCI bridge I/O window: 0x2000 - 0x2fff
[    9.684000] cs: IO port probe 0x2000-0x2fff: clean.
[    9.684000] pcmcia: parent PCI bridge Memory window: 0xb0100000 - 0xb01fffff
[    9.684000] pcmcia: parent PCI bridge Memory window: 0x50000000 - 0x53ffffff
[    9.684000] ACPI: PCI Interrupt 0000:06:0a.0[A] -> GSI 23 (level, low) -> IRQ 23
[    9.688000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[    9.700000] ubuntu/media/gspcav1/gspca_core.c: USB SPCA5XX camera found.(VC0321) 
[    9.700000] input: PS/2 Mouse as /class/input/input2
[    9.744000] input: AlpsPS/2 ALPS GlidePoint as /class/input/input3
[    9.820000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 20 (level, low) -> IRQ 16
[    9.820000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   10.028000] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
[   10.044000] usbcore: registered new interface driver gspca
[   10.044000] ubuntu/media/gspcav1/gspca_core.c: gspca driver 01.00.12 registered
[   10.172000] cs: IO port probe 0x100-0x3af: clean.
[   10.176000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   10.176000] cs: IO port probe 0x820-0x8ff: clean.
[   10.176000] cs: IO port probe 0xc00-0xcf7: clean.
[   10.176000] cs: IO port probe 0xa00-0xaff: clean.
[   10.684000] fuse init (API version 7.8)
[   10.812000] lp: driver loaded but no devices found
[   11.152000] Adding 2048248k swap on /dev/sda7.  Priority:-1 extents:1 across:2048248k
[   11.276000] EXT3 FS on sda5, internal journal
[   11.588000] kjournald starting.  Commit interval 5 seconds
[   11.588000] EXT3 FS on sda2, internal journal
[   11.588000] EXT3-fs: mounted filesystem with ordered data mode.
[   13.292000] NET: Registered protocol family 17
[   18.380000] ACPI: Battery Slot [BAT1] (battery present)
[   18.392000] No dock devices found.
[   18.424000] Using specific hotkey driver
[   18.492000] ACPI: AC Adapter [ACAD] (off-line)
[   18.508000] ibm_acpi: ec object not found
[   18.576000] input: Power Button (FF) as /class/input/input4
[   18.580000] ACPI: Power Button (FF) [PWRF]
[   18.612000] input: Lid Switch as /class/input/input5
[   18.612000] ACPI: Lid Switch [LID0]
[   18.644000] input: Power Button (CM) as /class/input/input6
[   18.648000] ACPI: Power Button (CM) [PWRB]
[   18.672000] ACPI: Video Device [GFX0] (multi-head: yes  rom: yes  post: no)
[   18.688000] pcc_acpi: loading...
[   18.716000] ACPI Sony Notebook Control Driver v0.2 successfully installed
[   23.008000] eth0: link down
[   25.612000] [drm] Initialized drm 1.1.0 20060810
[   25.620000] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 19
[   25.620000] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   26.268000] ppdev: user-space parallel port driver
[   29.932000] apm: BIOS not found.
[   30.496000] sonypi: Sony Programmable I/O Controller Driver v1.26.
[   30.516000] sonypi: detected type3 model, verbose = 0, fnkeyinit = off, camera = off, compat = off, mask = 0xffffffff, useinput = on, acpi = on
[   30.516000] sonypi: enabled at irq=11, port1=0x10c0, port2=0x10c4
[   30.516000] sonypi: device allocated minor is 62
[   30.564000] input: Sony Vaio Jogdial as /class/input/input7
[   30.648000] input: Sony Vaio Keys as /class/input/input8
[   30.712000] sonypi command failed at drivers/char/sonypi.c : sonypi_call1 (line 646)
[   30.752000] sonypi command failed at drivers/char/sonypi.c : sonypi_call2 (line 657)
[   30.796000] sonypi command failed at drivers/char/sonypi.c : sonypi_call2 (line 659)
[   30.840000] sonypi command failed at drivers/char/sonypi.c : sonypi_call1 (line 646)
[   31.344000] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
[   31.552000] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[   31.552000] NFSD: starting 90-second grace period
[   35.476000] vmmon: module license 'unspecified' taints kernel.
[   35.484000] /dev/vmmon[5168]: VMCI: Driver initialized.
[   35.484000] /dev/vmmon[5168]: Module vmmon: registered with major=10 minor=165
[   35.484000] /dev/vmmon[5168]: Module vmmon: initialized
[   36.088000] /dev/vmnet: open called by PID 5213 (vmnet-bridge)
[   36.088000] /dev/vmnet: hub 0 does not exist, allocating memory.
[   36.088000] /dev/vmnet: port on hub 0 successfully opened
[   36.088000] bridge-eth1: enabling the bridge
[   36.088000] bridge-eth1: is a Wireless Adapter
[   36.088000] bridge-eth1: up
[   36.088000] bridge-eth1: already up
[   36.088000] bridge-eth1: attached
[   36.368000] /dev/vmnet: open called by PID 5225 (vmnet-netifup)
[   36.368000] /dev/vmnet: hub 1 does not exist, allocating memory.
[   36.368000] /dev/vmnet: port on hub 1 successfully opened
[   36.464000] /dev/vmnet: open called by PID 5230 (vmnet-dhcpd)
[   36.464000] /dev/vmnet: port on hub 1 successfully opened
[   36.468000] /dev/vmnet: open called by PID 5248 (vmnet-netifup)
[   36.468000] /dev/vmnet: hub 8 does not exist, allocating memory.
[   36.468000] /dev/vmnet: port on hub 8 successfully opened
[   36.520000] /dev/vmnet: open called by PID 5262 (vmnet-dhcpd)
[   36.520000] /dev/vmnet: port on hub 8 successfully opened
[   36.556000] /dev/vmnet: open called by PID 5267 (vmnet-natd)
[   36.556000] /dev/vmnet: port on hub 8 successfully opened
[   42.628000] NET: Registered protocol family 10
[   42.628000] lo: Disabled Privacy Extensions
[   42.628000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   52.948000] vmnet1: no IPv6 routers present
[   53.184000] vmnet8: no IPv6 routers present
[   53.524000] eth1: no IPv6 routers present
[   63.520000] ieee80211_crypt: registered algorithm 'WEP'
[   78.376000] eth1: no IPv6 routers present
```

---

### Post by Steveway on 2007-08-10
Interesting.
But my old Laptop still beats your by about 38 seconds.
```
[    0.000000] Linux version 2.6.20-16-generic (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Thu Jun 7 20:19:32 UTC 2007 (Ubuntu 2.6.20-16.29-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009f800 end: 000000000009f800 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009f800 size: 0000000000000800 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000d8000 size: 0000000000028000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000001fe70000 end: 000000001ff70000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000001ff70000 size: 000000000000a000 end: 000000001ff7a000 type: 3
[    0.000000] copy_e820_map() start: 000000001ff7a000 size: 0000000000006000 end: 000000001ff80000 type: 4
[    0.000000] copy_e820_map() start: 000000001ff80000 size: 0000000000080000 end: 0000000020000000 type: 2
[    0.000000] copy_e820_map() start: 00000000fffe0000 size: 0000000000020000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d8000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001ff70000 (usable)
[    0.000000]  BIOS-e820: 000000001ff70000 - 000000001ff7a000 (ACPI data)
[    0.000000]  BIOS-e820: 000000001ff7a000 - 000000001ff80000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000001ff80000 - 0000000020000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fffe0000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 511MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f6910
[    0.000000] Entering add_active_range(0, 0, 130928) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   130928
[    0.000000]   HighMem    130928 ->   130928
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   130928
[    0.000000] On node 0 totalpages: 130928
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 990 pages used for memmap
[    0.000000]   Normal zone: 125842 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP (v000 PTLTD                                 ) @ 0x000f6a60
[    0.000000] ACPI: RSDT (v001 PTLTD    RSDT   0x06040000  LTP 0x00000000) @ 0x1ff73fde
[    0.000000] ACPI: FADT (v002 AMDK8  PTLTW    0x06040000 PTL_ 0x000f4240) @ 0x1ff79e56
[    0.000000] ACPI: SSDT (v001 PTLTD  POWERNOW 0x06040000  LTP 0x00000001) @ 0x1ff79eda
[    0.000000] ACPI: MADT (v001 PTLTD    APIC   0x06040000  LTP 0x00000000) @ 0x1ff79fb0
[    0.000000] ACPI: DSDT (v001  VIA   PTL_ACPI 0x06040000 MSFT 0x0100000e) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:8 APIC version 16
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 3, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:dffe0000)
[    0.000000] Detected 1801.161 MHz processor.
[   23.091753] Built 1 zonelists.  Total pages: 129906
[   23.091756] Kernel command line: root=UUID=22a39130-eb58-4398-9ecc-a98a236057f1 ro quiet splash
[   23.091897] mapped APIC to ffffd000 (fee00000)
[   23.091900] mapped IOAPIC to ffffc000 (fec00000)
[   23.091903] Enabling fast FPU save and restore... done.
[   23.091905] Enabling unmasked SIMD FPU exception support... done.
[   23.091914] Initializing CPU#0
[   23.091973] PID hash table entries: 2048 (order: 11, 8192 bytes)
[   23.093859] Console: colour VGA+ 80x25
[   23.094088] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   23.094530] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   23.104072] Memory: 508216k/523712k available (1992k kernel code, 14936k reserved, 900k data, 328k init, 0k highmem)
[   23.104083] virtual kernel memory layout:
[   23.104084]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   23.104085]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   23.104087]     vmalloc : 0xe0800000 - 0xff7fe000   ( 495 MB)
[   23.104088]     lowmem  : 0xc0000000 - 0xdff70000   ( 511 MB)
[   23.104089]       .init : 0xc03d9000 - 0xc042b000   ( 328 kB)
[   23.104091]       .data : 0xc02f2374 - 0xc03d36d4   ( 900 kB)
[   23.104092]       .text : 0xc0100000 - 0xc02f2374   (1992 kB)
[   23.104095] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   23.183894] Calibrating delay using timer specific routine.. 3605.69 BogoMIPS (lpj=7211395)
[   23.183932] Security Framework v1.0.0 initialized
[   23.183939] SELinux:  Disabled at boot.
[   23.183954] Mount-cache hash table entries: 512
[   23.184075] CPU: After generic identify, caps: 078bfbff c1d3fbff 00000000 00000000 00000000 00000000 00000000
[   23.184083] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   23.184086] CPU: L2 Cache: 128K (64 bytes/line)
[   23.184089] CPU: After all inits, caps: 078bfbff c1d3fbff 00000000 00000410 00000000 00000000 00000000
[   23.184098] Compat vDSO mapped to ffffe000.
[   23.184102] Remapping vsyscall page to ffffe000
[   23.184111] Checking 'hlt' instruction... OK.
[   23.199992] SMP alternatives: switching to UP code
[   23.200178] Freeing SMP alternatives: 11k freed
[   23.200388] Early unpacking initramfs... done
[   23.502476] ACPI: Core revision 20060707
[   23.504101] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   23.591979] CPU0: AMD Mobile AMD Sempron(tm) Processor 3000+ stepping 02
[   23.591998] Total of 1 processors activated (3605.69 BogoMIPS).
[   23.592495] ENABLING IO-APIC IRQs
[   23.592798] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=0 pin2=0
[   23.739405] Brought up 1 CPUs
[   23.739640] Booting paravirtualized kernel on bare hardware
[   23.739721] Time: 15:01:44  Date: 07/10/107
[   23.739749] NET: Registered protocol family 16
[   23.739835] EISA bus registered
[   23.739839] ACPI: bus type pci registered
[   23.746459] PCI: PCI BIOS revision 2.10 entry at 0xfd557, last bus=1
[   23.746461] PCI: Using configuration type 1
[   23.746463] Setting up standard PCI resources
[   23.750290] ACPI: Interpreter enabled
[   23.750295] ACPI: Using IOAPIC for interrupt routing
[   23.750675] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   23.750680] PCI: Probing PCI hardware (bus 00)
[   23.751983] PCI quirk: region 4000-407f claimed by vt8235 PM
[   23.751987] PCI quirk: region 8100-810f claimed by vt8235 SMB
[   23.752245] Boot video device is 0000:01:00.0
[   23.752349] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   23.766322] ACPI: PCI Interrupt Link [ALKA] (IRQs 16 17 18 19 20 21 22 23) *10, disabled.
[   23.766539] ACPI: PCI Interrupt Link [ALKB] (IRQs 16 17 18 19 20 21 22 23) *10, disabled.
[   23.766749] ACPI: PCI Interrupt Link [ALKC] (IRQs 22) *11, disabled.
[   23.766959] ACPI: PCI Interrupt Link [ALKD] (IRQs 21) *11, disabled.
[   23.767196] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 12 14 15) *10
[   23.767457] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 *10 12 14 15)
[   23.767698] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 *11 12 14 15)
[   23.767937] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[   23.788820] Linux Plug and Play Support v0.97 (c) Adam Belay
[   23.788836] pnp: PnP ACPI init
[   23.801422] pnp: PnP ACPI: found 11 devices
[   23.801428] PnPBIOS: Disabled by ACPI PNP
[   23.801483] PCI: Using ACPI for IRQ routing
[   23.801486] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   23.805097] NET: Registered protocol family 8
[   23.805098] NET: Registered protocol family 20
[   23.805380] pnp: 00:06: ioport range 0x600-0x60f has been reserved
[   23.805383] pnp: 00:06: ioport range 0x1c0-0x1cf has been reserved
[   23.805386] pnp: 00:06: ioport range 0x4d0-0x4d1 has been reserved
[   23.805389] pnp: 00:06: ioport range 0xfe10-0xfe11 could not be reserved
[   23.805630] PCI: Bridge: 0000:00:01.0
[   23.805632]   IO window: disabled.
[   23.805636]   MEM window: c1000000-c1ffffff
[   23.805640]   PREFETCH window: e0000000-efffffff
[   23.805644] PCI: Bus 2, cardbus bridge: 0000:00:0b.0
[   23.805646]   IO window: 00002000-000020ff
[   23.805650]   IO window: 00002400-000024ff
[   23.805653]   PREFETCH window: 30000000-33ffffff
[   23.805657]   MEM window: 34000000-37ffffff
[   23.805660] PCI: Bus 6, cardbus bridge: 0000:00:0b.1
[   23.805662]   IO window: 00002800-000028ff
[   23.805666]   IO window: 00002c00-00002cff
[   23.805670]   PREFETCH window: 38000000-3bffffff
[   23.805673]   MEM window: 3c000000-3fffffff
[   23.805689] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   23.805706] ACPI: PCI Interrupt 0000:00:0b.0[A] -> GSI 17 (level, low) -> IRQ 16
[   23.805714] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[   23.805724] PCI: Enabling device 0000:00:0b.1 (0000 -> 0003)
[   23.805727] ACPI: PCI Interrupt 0000:00:0b.1[B] -> GSI 18 (level, low) -> IRQ 17
[   23.805737] PCI: Setting latency timer of device 0000:00:0b.1 to 64
[   23.805765] NET: Registered protocol family 2
[   23.839350] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   23.839428] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[   23.839540] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[   23.839606] TCP: Hash tables configured (established 16384 bind 8192)
[   23.839609] TCP reno registered
[   23.851389] checking if image is initramfs... it is
[   24.449272] Freeing initrd memory: 6737k freed
[   24.449651] audit: initializing netlink socket (disabled)
[   24.449663] audit(1186758104.336:1): initialized
[   24.449762] VFS: Disk quotas dquot_6.5.1
[   24.449780] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   24.449825] io scheduler noop registered
[   24.449827] io scheduler anticipatory registered
[   24.449830] io scheduler deadline registered
[   24.449837] io scheduler cfq registered (default)
[   24.450121] isapnp: Scanning for PnP cards...
[   24.803767] isapnp: No Plug & Play device found
[   24.834092] Real Time Clock Driver v1.12ac
[   24.834135] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   24.834239] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   24.835021] mice: PS/2 mouse device common for all mice
[   24.835445] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   24.835649] input: Macintosh mouse button emulation as /class/input/input0
[   24.835677] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   24.835681] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   24.835901] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   24.839023] i8042.c: Detected active multiplexing controller, rev 1.1.
[   24.840311] serio: i8042 KBD port at 0x60,0x64 irq 1
[   24.840316] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[   24.840319] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[   24.840321] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[   24.840324] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[   24.840460] EISA: Probing bus 0 at eisa.0
[   24.840469] Cannot allocate resource for EISA slot 1
[   24.840471] Cannot allocate resource for EISA slot 2
[   24.840478] Cannot allocate resource for EISA slot 4
[   24.840495] EISA: Detected 0 cards.
[   24.870552] TCP cubic registered
[   24.870558] NET: Registered protocol family 1
[   24.870578] Using IPI No-Shortcut mode
[   24.870639] ACPI: (supports S0 S3 S4 S5)
[   24.870671]   Magic number: 3:315:32
[   24.870679]   hash matches device ttydf
[   24.871074] Freeing unused kernel memory: 328k freed
[   24.874308] Time: tsc clocksource has been installed.
[   24.885721] input: AT Translated Set 2 keyboard as /class/input/input1
[   26.112399] Capability LSM initialized
[   26.245994] ACPI: Thermal Zone [THRS] (33 C)
[   26.336846] ACPI: Thermal Zone [THRC] (50 C)
[   26.875743] ieee1394: Initialized config rom entry `ip1394'
[   26.876935] ACPI: PCI Interrupt 0000:00:0b.2[C] -> GSI 19 (level, low) -> IRQ 18
[   26.926758] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[18]  MMIO=[c0005000-c00057ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   26.937714] usbcore: registered new interface driver usbfs
[   26.937735] usbcore: registered new interface driver hub
[   26.937754] usbcore: registered new device driver usb
[   26.938602] USB Universal Host Controller Interface driver v3.0
[   26.938660] ACPI: PCI Interrupt 0000:00:10.0[A] -> GSI 21 (level, low) -> IRQ 19
[   26.938670] uhci_hcd 0000:00:10.0: UHCI Host Controller
[   26.938783] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[   26.938814] uhci_hcd 0000:00:10.0: irq 19, io base 0x00001c00
[   26.938928] usb usb1: configuration #1 chosen from 1 choice
[   26.938955] hub 1-0:1.0: USB hub found
[   26.938962] hub 1-0:1.0: 2 ports detected
[   27.009809] via-rhine.c:v1.10-LK1.4.2 Sept-11-2006 Written by Donald Becker
[   27.044370] ACPI: PCI Interrupt 0000:00:10.1[B] -> GSI 21 (level, low) -> IRQ 19
[   27.044382] uhci_hcd 0000:00:10.1: UHCI Host Controller
[   27.044402] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
[   27.044424] uhci_hcd 0000:00:10.1: irq 19, io base 0x00001c20
[   27.044512] usb usb2: configuration #1 chosen from 1 choice
[   27.044538] hub 2-0:1.0: USB hub found
[   27.044545] hub 2-0:1.0: 2 ports detected
[   27.152257] ACPI: PCI Interrupt 0000:00:10.2[C] -> GSI 21 (level, low) -> IRQ 19
[   27.152269] uhci_hcd 0000:00:10.2: UHCI Host Controller
[   27.152294] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
[   27.152317] uhci_hcd 0000:00:10.2: irq 19, io base 0x00001c40
[   27.152410] usb usb3: configuration #1 chosen from 1 choice
[   27.152436] hub 3-0:1.0: USB hub found
[   27.152443] hub 3-0:1.0: 2 ports detected
[   27.261932] ACPI: PCI Interrupt 0000:00:10.3[D] -> GSI 21 (level, low) -> IRQ 19
[   27.261950] ehci_hcd 0000:00:10.3: EHCI Host Controller
[   27.261994] ehci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
[   27.262034] ehci_hcd 0000:00:10.3: irq 19, io mem 0xc0005800
[   27.262041] ehci_hcd 0000:00:10.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   27.262131] usb usb4: configuration #1 chosen from 1 choice
[   27.262156] hub 4-0:1.0: USB hub found
[   27.262164] hub 4-0:1.0: 6 ports detected
[   27.287993] usb 1-1: new low speed USB device using uhci_hcd and address 2
[   27.368243] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 23 (level, low) -> IRQ 20
[   27.372233] eth0: VIA Rhine II at 0x11800, 00:0a:e4:a1:0e:db, IRQ 20.
[   27.372945] eth0: MII PHY found at address 1, status 0x7849 advertising 05e1 Link 0000.
[   27.374086] VP_IDE: IDE controller at PCI slot 0000:00:11.1
[   27.374172] ACPI: Unable to derive IRQ for device 0000:00:11.1
[   27.374175] ACPI: PCI Interrupt 0000:00:11.1[A]: no GSI
[   27.374184] VP_IDE: chipset revision 6
[   27.374186] VP_IDE: not 100% native mode: will probe irqs later
[   27.374196] VP_IDE: VIA vt8235 (rev 00) IDE UDMA133 controller on pci0000:00:11.1
[   27.374203]     ide0: BM-DMA at 0x1c60-0x1c67, BIOS settings: hda:DMA, hdb:pio
[   27.374215]     ide1: BM-DMA at 0x1c68-0x1c6f, BIOS settings: hdc:DMA, hdd:pio
[   27.374221] Probing IDE interface ide0...
[   27.799560] hda: TOSHIBA MK6025GAS, ATA DISK drive
[   28.199211] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[000ae404481044de]
[   28.422869] usb 4-2: new high speed USB device using ehci_hcd and address 3
[   28.478934] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   28.527870] Probing IDE interface ide1...
[   28.569404] usb 4-2: configuration #1 chosen from 1 choice
[   28.754843] usbcore: registered new interface driver libusual
[   28.761246] SCSI subsystem initialized
[   28.762596] Initializing USB Mass Storage driver...
[   28.998330] usb 1-1: new low speed USB device using uhci_hcd and address 3
[   29.168345] usb 1-1: configuration #1 chosen from 1 choice
[   29.402017] hdc: TSSTcorpCD/DVDW TS-L532A, ATAPI CD/DVD-ROM drive
[   29.413911] usb 2-2: new full speed USB device using uhci_hcd and address 2
[   29.644811] usb 2-2: configuration #1 chosen from 1 choice
[   29.648014] scsi0 : SCSI emulation for USB Mass Storage devices
[   29.648051] usb-storage: device found at 3
[   29.648053] usb-storage: waiting for device to settle before scanning
[   29.648070] usbcore: registered new interface driver usb-storage
[   29.648072] USB Mass Storage support registered.
[   29.649859] usbcore: registered new interface driver hiddev
[   29.662799] input: PS/2+USB Mouse as /class/input/input2
[   29.662818] input: USB HID v1.11 Mouse [PS/2+USB Mouse] on usb-0000:00:10.0-1
[   29.662834] usbcore: registered new interface driver usbhid
[   29.662838] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   30.087624] ide1 at 0x170-0x177,0x376 on irq 15
[   30.101306] libata version 2.20 loaded.
[   30.111002] hda: max request size: 128KiB
[   30.118661] hda: 117210240 sectors (60011 MB), CHS=65535/16/63, UDMA(100)
[   30.119007] hda: cache flushes supported
[   30.119063]  hda: hda1 hda2 hda3
[   30.207906] hdc: ATAPI 24X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(33)
[   30.207916] Uniform CD-ROM driver Revision: 3.20
[   34.644967] usb-storage: device scan complete
[   34.648339] scsi 0:0:0:0: Direct-Access     Maxtor 6 L250R0           0000 PQ: 0 ANSI: 0
[   34.655569] SCSI device sda: 490234752 512-byte hdwr sectors (251000 MB)
[   34.656431] sda: Write Protect is off
[   34.656434] sda: Mode Sense: 27 00 00 00
[   34.656436] sda: assuming drive cache: write through
[   34.657306] SCSI device sda: 490234752 512-byte hdwr sectors (251000 MB)
[   34.658178] sda: Write Protect is off
[   34.658181] sda: Mode Sense: 27 00 00 00
[   34.658182] sda: assuming drive cache: write through
[   34.658185]  sda: sda1 sda2
[   34.682834] sd 0:0:0:0: Attached scsi disk sda
[   34.686878] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   35.035957] kjournald starting.  Commit interval 5 seconds
[   35.035970] EXT3-fs: mounted filesystem with ordered data mode.
[   44.146697] eth1: link down
[   45.403631] NET: Registered protocol family 17
[   45.567199] Yenta: CardBus bridge found at 0000:00:0b.0 [1025:006e]
[   45.567216] Yenta: Using CSCINT to route CSC interrupts to PCI
[   45.567218] Yenta: Routing CardBus interrupts to PCI
[   45.567223] Yenta TI: socket 0000:00:0b.0, mfunc 0x010a1b22, devctl 0x64
[   45.591415] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   45.802826] Yenta: ISA IRQ mask 0x0cf8, PCI irq 16
[   45.802831] Socket status: 30000820
[   45.803030] Yenta: CardBus bridge found at 0000:00:0b.1 [1025:006e]
[   45.803044] Yenta: Using CSCINT to route CSC interrupts to PCI
[   45.803046] Yenta: Routing CardBus interrupts to PCI
[   45.803050] Yenta TI: socket 0000:00:0b.1, mfunc 0x010a1b22, devctl 0x64
[   45.839863] Linux agpgart interface v0.102 (c) Dave Jones
[   46.038604] Yenta: ISA IRQ mask 0x0cf8, PCI irq 17
[   46.038609] Socket status: 30000086
[   46.038839] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   46.131466] agpgart: Detected AGP bridge 0
[   46.139417] agpgart: AGP aperture is 256M @ 0xd0000000
[   46.153255] irda_init()
[   46.153272] NET: Registered protocol family 23
[   46.441478] pccard: CardBus card inserted into slot 0
[   46.809609] input: PC Speaker as /class/input/input3
[   47.003761] parport: PnPBIOS parport detected.
[   47.003839] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   47.053775] Linux video capture interface: v2.00
[   47.085683] ath_hal: module license 'Proprietary' taints kernel.
[   47.087169] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   47.229801] Synaptics Touchpad, model: 1, fw: 5.8, id: 0x9248b1, caps: 0x904713/0x4000
[   47.270700] input: SynPS/2 Synaptics TouchPad as /class/input/input4
[   47.735950] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 21
[   47.736245] NVRM: loading NVIDIA UNIX x86 Kernel Module  100.14.11  Wed Jun 13 18:21:22 PDT 2007
[   47.749646] nsc_ircc_pnp_probe() : From PnP, found firbase 0x3F8 ; irq 3 ; dma 1.
[   47.749674] nsc-ircc, chip->init
[   47.749685] nsc-ircc, Found chip at base=0x02e
[   47.749713] nsc-ircc, driver loaded (Dag Brattli)
[   47.749720] nsc_ircc_open(), can't get iobase of 0x3f8
[   47.749750] nsc-ircc, Found chip at base=0x02e
[   47.749777] nsc-ircc, driver loaded (Dag Brattli)
[   47.749780] nsc_ircc_open(), can't get iobase of 0x3f8
[   47.749945] pnp: Device 00:0a disabled.
[   47.796998] cs: IO port probe 0x100-0x3af: clean.
[   47.798901] cs: IO port probe 0x3e0-0x4ff: clean.
[   47.799698] cs: IO port probe 0x820-0x8ff: clean.
[   47.800386] cs: IO port probe 0xc00-0xcf7: clean.
[   47.801189] cs: IO port probe 0xa00-0xaff: clean.
[   47.868610] cs: IO port probe 0x100-0x3af: clean.
[   47.870516] cs: IO port probe 0x3e0-0x4ff: clean.
[   47.871309] cs: IO port probe 0x820-0x8ff: clean.
[   47.871984] cs: IO port probe 0xc00-0xcf7: clean.
[   47.872885] cs: IO port probe 0xa00-0xaff: clean.
[   47.943000] ubuntu/media/gspcav1/gspca_core.c: USB SPCA5XX camera found. (PAC207)
[   47.947457] usbcore: registered new interface driver gspca
[   47.947462] ubuntu/media/gspcav1/gspca_core.c: gspca driver 01.00.12 registered
[   47.979616] wlan: 0.8.4.2 (0.9.3.1)
[   48.018045] ath_pci: 0.9.4.5 (0.9.3.1)
[   48.018103] PCI: Enabling device 0000:02:00.0 (0000 -> 0002)
[   48.018111] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 17 (level, low) -> IRQ 16
[   48.672919] ath_rate_sample: 1.2 (0.9.3.1)
[   48.673668] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[   48.673675] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[   48.673691] wifi0: turboG rates: 6Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[   48.673696] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
[   48.673699] wifi0: mac 7.9 phy 4.5 radio 5.6
[   48.673704] wifi0: Use hw queue 1 for WME_AC_BE traffic
[   48.673706] wifi0: Use hw queue 0 for WME_AC_BK traffic
[   48.673708] wifi0: Use hw queue 2 for WME_AC_VI traffic
[   48.673710] wifi0: Use hw queue 3 for WME_AC_VO traffic
[   48.673712] wifi0: Use hw queue 8 for CAB traffic
[   48.673713] wifi0: Use hw queue 9 for beacons
[   48.720463] wifi0: Atheros 5212: mem=0x34000000, irq=16
[   48.721051] ACPI: PCI Interrupt 0000:00:11.6[C] -> GSI 22 (level, low) -> IRQ 22
[   48.727277] PCI: Setting latency timer of device 0000:00:11.6 to 64
[   49.238276] ACPI: PCI Interrupt 0000:00:11.5[C] -> GSI 22 (level, low) -> IRQ 22
[   49.238410] PCI: Setting latency timer of device 0000:00:11.5 to 64
[   49.933189] lp0: using parport0 (interrupt-driven).
[   50.010442] EXT3 FS on sda2, internal journal
[   53.421305] NET: Registered protocol family 10
[   53.421399] lo: Disabled Privacy Extensions
[   53.421455] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   55.813870] ACPI: AC Adapter [AC] (on-line)
[   55.868170] ACPI: Battery Slot [BAT0] (battery absent)
[   55.921905] input: Power Button (FF) as /class/input/input5
[   55.925840] ACPI: Power Button (FF) [PWRF]
[   55.962229] input: Lid Switch as /class/input/input6
[   55.966027] ACPI: Lid Switch [LID]
[   56.001590] input: Sleep Button (CM) as /class/input/input7
[   56.005419] ACPI: Sleep Button (CM) [SLPB]
[   56.023562] Using specific hotkey driver
[   56.056656] No dock devices found.
[   56.099007] ibm_acpi: ec object not found
[   56.184516] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   56.213052] pcc_acpi: loading...
[   56.467339] powernow-k8: Found 1 Mobile AMD Sempron(tm) Processor 3000+ processors (version 2.00.00)
[   56.467383] powernow-k8:    0 : fid 0xa (1800 MHz), vid 0x6
[   56.467386] powernow-k8:    1 : fid 0x8 (1600 MHz), vid 0xa
[   56.467388] powernow-k8:    2 : fid 0x0 (800 MHz), vid 0x18
[   56.468619] powernow-k8: ph2 null fid transition 0xa
[   57.415977] ttyS0: LSR safety check engaged!
[   59.906165] ppdev: user-space parallel port driver
[   60.646907] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[   60.646920] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[   60.646977] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[   61.488339] apm: BIOS not found.
[   39.344000] Time: acpi_pm clocksource has been installed.
[   40.036000] ath0: no IPv6 routers present
[  391.980000] Adding 2096472k swap on /dev/hda2.  Priority:-1 extents:1 across:2096472k
[  393.916000] kjournald starting.  Commit interval 5 seconds
[  393.916000] EXT3 FS on hda3, internal journal
[  393.916000] EXT3-fs: mounted filesystem with ordered data mode.
[  394.856000] kjournald starting.  Commit interval 5 seconds
[  394.860000] EXT3 FS on hda1, internal journal
[  394.860000] EXT3-fs: mounted filesystem with ordered data mode.

```
Those added Partition were done later by myself, manually. I don't mount them usually.

---

### Post by sab0403 on 2007-08-10
Nice... real nice... perhaps you want to share some tips with me? :popcorn:

Anyway, to me this is blazing fast, when compared to what it was before. The sad part is that it's about the same as Windows.  Nobody beats my Debian, though - 14 seconds cold. Of course, that's after a netinst and with no GUI, but I do have wireless available (btw, is there any way to make the GUI start automatically? Even better, to toggle this on/off?).

I love Linux 8)

---

### Post by Steveway on 2007-08-10
I think I know why my Pc boots faster.
Our CPUs seem to be pretty on par, but I have 512MB of Ram and you seem to have only about 118...wait...you have 1024MB?
You have a slightly faster Cpu and the double amount of memory, but your boottime is the double amount of mine?
There is something wrong with your setup,I'm using a pretty normal Xubuntu 7.04 Install, reinstalled it about a week ago.

---

### Post by sab0403 on 2007-08-10
Yup, 1024 Mb RAM.

Probably some devices need be disabled (such as the MemoryStick, which I *never* use).

I'm pretty giddy with this change, though. Still, whenever I need a blazing fast boot, I go straight to Debian. Since right now I spend most of my time transcribing/greping, don't need much more usually. Even for browsing, just load up X and I'm golden.

:popcorn:

---

### Post by misfitpierce on 2007-08-10
Keep in mind boot times do vary and can also be lengthened by startup trying to load a device but it fails. Possible to maybe watch bootup info take make sure all devices are installed properly.

---

### Post by _simon_ on 2007-08-10
My USB Hub seems to bump the time right up, unfortunately I do need it.

```

[    0.000000] Linux version 2.6.20-16-generic (root@king) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Thu Jun 7 19:00:28 UTC 2007 (Ubuntu 2.6.20-16.29-generic)
[    0.000000] Command line: root=UUID=b1f90171-318e-4980-bd93-dc70ed188850 ro quiet splash
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007ffb0000 (usable)
[    0.000000]  BIOS-e820: 000000007ffb0000 - 000000007ffc0000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007ffc0000 - 000000007fff0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007fff0000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fecc0000 - 00000000fecc1000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff380000 - 0000000100000000 (reserved)
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 524208) 1 entries of 3200 used
[    0.000000] end_pfn_map = 1048576
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP (v000 ACPIAM                                ) @ 0x00000000000f8e40
[    0.000000] ACPI: RSDT (v001 A M I  OEMRSDT  0x12000620 MSFT 0x00000097) @ 0x000000007ffb0000
[    0.000000] ACPI: FADT (v002 A M I  OEMFACP  0x12000620 MSFT 0x00000097) @ 0x000000007ffb0200
[    0.000000] ACPI: MADT (v001 A M I  OEMAPIC  0x12000620 MSFT 0x00000097) @ 0x000000007ffb0390
[    0.000000] ACPI: MCFG (v001 A M I  OEMMCFG  0x12000620 MSFT 0x00000097) @ 0x000000007ffb0400
[    0.000000] ACPI: OEMB (v001 A M I  AMI_OEM  0x12000620 MSFT 0x00000097) @ 0x000000007ffc0040
[    0.000000] ACPI: DSDT (v001  AS2GL AS2GL000 0x00000000 INTL 0x02002026) @ 0x0000000000000000
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] Number of nodes 1
[    0.000000] Node 0 MemBase 0000000000000000 Limit 000000007ffb0000
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 524208) 1 entries of 3200 used
[    0.000000] NUMA: Using 63 for the hash shift.
[    0.000000] Using node hash shift of 63
[    0.000000] Bootmem setup node 0 0000000000000000-000000007ffb0000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   DMA32        4096 ->  1048576
[    0.000000]   Normal    1048576 ->  1048576
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0:        0 ->      159
[    0.000000]     0:      256 ->   524208
[    0.000000] On node 0 totalpages: 524111
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 1087 pages reserved
[    0.000000]   DMA zone: 2856 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 7110 pages used for memmap
[    0.000000]   DMA32 zone: 513002 pages, LIFO batch:31
[    0.000000]   Normal zone: 0 pages used for memmap
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 (Bootup-CPU)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] Processor #1
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: IOAPIC (id[0x03] address[0xfecc0000] gsi_base[24])
[    0.000000] IOAPIC[1]: apic_id 3, address 0xfecc0000, GSI 24-47
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Setting APIC routing to physical flat
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Nosave address range: 000000000009f000 - 00000000000a0000
[    0.000000] Nosave address range: 00000000000a0000 - 00000000000e4000
[    0.000000] Nosave address range: 00000000000e4000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:60000000)
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] PERCPU: Allocating 34048 bytes of per cpu data
[    0.000000] Built 1 zonelists.  Total pages: 515858
[    0.000000] Kernel command line: root=UUID=b1f90171-318e-4980-bd93-dc70ed188850 ro quiet splash
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[   32.699689] Console: colour VGA+ 80x25
[   32.700377] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
[   32.701398] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
[   32.701756] Checking aperture...
[   32.701760] CPU 0: aperture @ 1022000000 size 32 MB
[   32.701761] Aperture too small (32 MB)
[   32.709801] No AGP bridge found
[   32.722847] Memory: 2053340k/2096832k available (2217k kernel code, 43104k reserved, 1162k data, 304k init)
[   32.800198] Calibrating delay using timer specific routine.. 4878.38 BogoMIPS (lpj=9756779)
[   32.800242] Security Framework v1.0.0 initialized
[   32.800246] SELinux:  Disabled at boot.
[   32.800264] Mount-cache hash table entries: 256
[   32.800370] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   32.800372] CPU: L2 Cache: 512K (64 bytes/line)
[   32.800374] CPU 0/0 -> Node 0
[   32.800376] CPU: Physical Processor ID: 0
[   32.800377] CPU: Processor Core ID: 0
[   32.800394] SMP alternatives: switching to UP code
[   32.800584] Early unpacking initramfs... done
[   33.040755] ACPI: Core revision 20060707
[   33.041107] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   33.083579] Using local APIC timer interrupts.
[   33.124596] result 12696364
[   33.124598] Detected 12.696 MHz APIC timer.
[   33.128341] SMP alternatives: switching to SMP code
[   33.128428] Booting processor 1/2 APIC 0x1
[   33.138763] Initializing CPU#1
[   33.216222] Calibrating delay using timer specific routine.. 4875.70 BogoMIPS (lpj=9751408)
[   33.216227] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   33.216229] CPU: L2 Cache: 512K (64 bytes/line)
[   33.216231] CPU 1/1 -> Node 0
[   33.216233] CPU: Physical Processor ID: 0
[   33.216234] CPU: Processor Core ID: 1
[   33.216297] AMD Athlon(tm) 64 X2 Dual Core Processor 4600+ stepping 02
[   33.220232] CPU 1: Syncing TSC to CPU 0.
[   33.220234] CPU 1: synchronized TSC with CPU 0 (last diff 0 cycles, maxerr 525 cycles)
[   33.220242] Brought up 2 CPUs
[   33.220295] Disabling vsyscall due to use of PM timer
[   33.220297] time.c: Using 3.579545 MHz WALL PM GTOD PM timer.
[   33.220299] time.c: Detected 2437.699 MHz processor.
[   33.790634] migration_cost=135
[   33.790928] Time:  9:32:47  Date: 07/10/107
[   33.790958] NET: Registered protocol family 16
[   33.791022] ACPI: bus type pci registered
[   33.791027] PCI: Using configuration type 1
[   33.798460] ACPI: Interpreter enabled
[   33.798463] ACPI: Using IOAPIC for interrupt routing
[   33.799476] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   33.799480] PCI: Probing PCI hardware (bus 00)
[   33.800785] Boot video device is 0000:06:00.0
[   33.801370] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   33.823231] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[   33.823479] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.NBPG._PRT]
[   33.823724] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.NBP0._PRT]
[   33.823969] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.NBP1._PRT]
[   33.824220] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.NBP2._PRT]
[   33.824334] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.NBP3._PRT]
[   33.829850] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P7._PRT]
[   33.830183] ACPI: PCI Root Bridge [PCI1] (0000:80)
[   33.830187] PCI: Probing PCI hardware (bus 80)
[   33.832325] ACPI: PCI Interrupt Routing Table [\_SB_.PCI1._PRT]
[   33.832693] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[   33.832894] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[   33.833097] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[   33.833296] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 *6 7 10 11 12 14 15)
[   33.833548] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   33.833752] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   33.833955] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   33.834161] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[   33.834230] Linux Plug and Play Support v0.97 (c) Adam Belay
[   33.834238] pnp: PnP ACPI init
[   33.838222] pnp: PnP ACPI: found 14 devices
[   33.838276] PCI: Using ACPI for IRQ routing
[   33.838278] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   33.838384] NET: Registered protocol family 8
[   33.838385] NET: Registered protocol family 20
[   33.839222] PCI: Bridge: 0000:00:01.0
[   33.839223]   IO window: disabled.
[   33.839227]   MEM window: disabled.
[   33.839230]   PREFETCH window: disabled.
[   33.839234] PCI: Bridge: 0000:00:02.0
[   33.839236]   IO window: e000-efff
[   33.839240]   MEM window: fc000000-febfffff
[   33.839243]   PREFETCH window: d0000000-dfffffff
[   33.839247] PCI: Bridge: 0000:00:03.0
[   33.839248]   IO window: disabled.
[   33.839252]   MEM window: disabled.
[   33.839255]   PREFETCH window: cff00000-cfffffff
[   33.839260] PCI: Bridge: 0000:00:03.1
[   33.839261]   IO window: disabled.
[   33.839265]   MEM window: disabled.
[   33.839268]   PREFETCH window: cfe00000-cfefffff
[   33.839272] PCI: Bridge: 0000:00:03.2
[   33.839275]   IO window: d000-dfff
[   33.839280]   MEM window: fbf00000-fbffffff
[   33.839283]   PREFETCH window: disabled.
[   33.839287] PCI: Bridge: 0000:00:03.3
[   33.839289]   IO window: c000-cfff
[   33.839294]   MEM window: fbe00000-fbefffff
[   33.839297]   PREFETCH window: disabled.
[   33.839312] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   33.839325] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 27 (level, low) -> IRQ 27
[   33.839330] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   33.839342] ACPI: PCI Interrupt 0000:00:03.0[A] -> GSI 31 (level, low) -> IRQ 31
[   33.839347] PCI: Setting latency timer of device 0000:00:03.0 to 64
[   33.839359] ACPI: PCI Interrupt 0000:00:03.1[B] -> GSI 35 (level, low) -> IRQ 35
[   33.839364] PCI: Setting latency timer of device 0000:00:03.1 to 64
[   33.839376] ACPI: PCI Interrupt 0000:00:03.2[C] -> GSI 39 (level, low) -> IRQ 39
[   33.839381] PCI: Setting latency timer of device 0000:00:03.2 to 64
[   33.839394] ACPI: PCI Interrupt 0000:00:03.3[D] -> GSI 43 (level, low) -> IRQ 43
[   33.839398] PCI: Setting latency timer of device 0000:00:03.3 to 64
[   33.839482] NET: Registered protocol family 2
[   33.880107] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
[   33.880379] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[   33.881823] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   33.882176] TCP: Hash tables configured (established 262144 bind 65536)
[   33.882179] TCP reno registered
[   33.892149] checking if image is initramfs... it is
[   34.386706] Freeing initrd memory: 6829k freed
[   34.389794] audit: initializing netlink socket (disabled)
[   34.389808] audit(1186738367.652:1): initialized
[   34.389974] VFS: Disk quotas dquot_6.5.1
[   34.389992] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   34.390034] io scheduler noop registered
[   34.390036] io scheduler anticipatory registered
[   34.390038] io scheduler deadline registered
[   34.390049] io scheduler cfq registered (default)
[   34.390307] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   34.390338] assign_interrupt_mode Found MSI capability
[   34.390341] Allocate Port Service[0000:00:02.0:pcie00]
[   34.390367] Allocate Port Service[0000:00:02.0:pcie02]
[   34.390445] PCI: Setting latency timer of device 0000:00:03.0 to 64
[   34.390482] assign_interrupt_mode Found MSI capability
[   34.390484] Allocate Port Service[0000:00:03.0:pcie00]
[   34.390506] Allocate Port Service[0000:00:03.0:pcie02]
[   34.390592] PCI: Setting latency timer of device 0000:00:03.1 to 64
[   34.390629] assign_interrupt_mode Found MSI capability
[   34.390632] Allocate Port Service[0000:00:03.1:pcie00]
[   34.390654] Allocate Port Service[0000:00:03.1:pcie02]
[   34.390741] PCI: Setting latency timer of device 0000:00:03.2 to 64
[   34.390778] assign_interrupt_mode Found MSI capability
[   34.390780] Allocate Port Service[0000:00:03.2:pcie00]
[   34.390802] Allocate Port Service[0000:00:03.2:pcie02]
[   34.390886] PCI: Setting latency timer of device 0000:00:03.3 to 64
[   34.390923] assign_interrupt_mode Found MSI capability
[   34.390926] Allocate Port Service[0000:00:03.3:pcie00]
[   34.390951] Allocate Port Service[0000:00:03.3:pcie02]
[   34.409643] Real Time Clock Driver v1.12ac
[   34.409677] Linux agpgart interface v0.102 (c) Dave Jones
[   34.409679] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   34.409785] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   34.409914] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   34.410305] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   34.410464] mice: PS/2 mouse device common for all mice
[   34.410891] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   34.411044] input: Macintosh mouse button emulation as /class/input/input0
[   34.411070] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   34.411073] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   34.411328] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[   34.411330] PNP: PS/2 controller doesn't have AUX irq; using default 12
[   34.411657] serio: i8042 KBD port at 0x60,0x64 irq 1
[   34.411661] serio: i8042 AUX port at 0x60,0x64 irq 12
[   34.411728] TCP cubic registered
[   34.411736] NET: Registered protocol family 1
[   34.411807] ACPI: (supports S0 S1 S3 S4 S5)
[   34.411840]   Magic number: 3:194:525
[   34.411939] drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   34.412012] Freeing unused kernel memory: 304k freed
[   34.430823] input: AT Translated Set 2 keyboard as /class/input/input1
[   35.564878] Capability LSM initialized
[   35.959957] SCSI subsystem initialized
[   35.975684] libata version 2.20 loaded.
[   35.975804] usbcore: registered new interface driver usbfs
[   35.975823] usbcore: registered new interface driver hub
[   35.975846] usbcore: registered new device driver usb
[   35.976594] USB Universal Host Controller Interface driver v3.0
[   35.976648] ACPI: PCI Interrupt 0000:00:10.0[A] -> GSI 20 (level, low) -> IRQ 20
[   35.976657] uhci_hcd 0000:00:10.0: UHCI Host Controller
[   35.976760] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[   35.976785] uhci_hcd 0000:00:10.0: irq 20, io base 0x0000a480
[   35.976888] usb usb1: configuration #1 chosen from 1 choice
[   35.976909] hub 1-0:1.0: USB hub found
[   35.976915] hub 1-0:1.0: 2 ports detected
[   36.083806] ACPI: PCI Interrupt 0000:00:10.1[B] -> GSI 22 (level, low) -> IRQ 22
[   36.083815] uhci_hcd 0000:00:10.1: UHCI Host Controller
[   36.083839] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
[   36.083863] uhci_hcd 0000:00:10.1: irq 22, io base 0x0000a800
[   36.083938] usb usb2: configuration #1 chosen from 1 choice
[   36.083959] hub 2-0:1.0: USB hub found
[   36.083964] hub 2-0:1.0: 2 ports detected
[   36.191749] ACPI: PCI Interrupt 0000:00:10.2[C] -> GSI 21 (level, low) -> IRQ 21
[   36.191757] uhci_hcd 0000:00:10.2: UHCI Host Controller
[   36.191774] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
[   36.191795] uhci_hcd 0000:00:10.2: irq 21, io base 0x0000a880
[   36.191865] usb usb3: configuration #1 chosen from 1 choice
[   36.191882] hub 3-0:1.0: USB hub found
[   36.191886] hub 3-0:1.0: 2 ports detected
[   36.299736] ACPI: PCI Interrupt 0000:00:10.3[D] -> GSI 23 (level, low) -> IRQ 23
[   36.299744] uhci_hcd 0000:00:10.3: UHCI Host Controller
[   36.299761] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
[   36.299782] uhci_hcd 0000:00:10.3: irq 23, io base 0x0000ac00
[   36.299855] usb usb4: configuration #1 chosen from 1 choice
[   36.299873] hub 4-0:1.0: USB hub found
[   36.299878] hub 4-0:1.0: 2 ports detected
[   36.323649] usb 1-1: new full speed USB device using uhci_hcd and address 2
[   36.407721] r8169 Gigabit Ethernet driver 2.2LK loaded
[   36.407745] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 36 (level, low) -> IRQ 36
[   36.407767] PCI: Setting latency timer of device 0000:03:00.0 to 64
[   36.407945] eth0: RTL8168b/8111b at 0xffffc20000004000, 00:19:66:00:a3:5e, IRQ 36
[   36.414496] ACPI: PCI Interrupt 0000:00:10.4[C] -> GSI 21 (level, low) -> IRQ 21
[   36.414513] ehci_hcd 0000:00:10.4: EHCI Host Controller
[   36.414544] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 5
[   36.414580] ehci_hcd 0000:00:10.4: irq 21, io mem 0xfbdffc00
[   36.414587] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   36.414656] usb usb5: configuration #1 chosen from 1 choice
[   36.414680] hub 5-0:1.0: USB hub found
[   36.414686] hub 5-0:1.0: 8 ports detected
[   36.521552] VP_IDE: IDE controller at PCI slot 0000:00:0f.1
[   36.521575] VP_IDE: chipset revision 7
[   36.521577] VP_IDE: not 100% native mode: will probe irqs later
[   36.521588] VP_IDE: VIA vt8237a (rev 00) IDE UDMA133 controller on pci0000:00:0f.1
[   36.521595]     ide0: BM-DMA at 0xfc00-0xfc07, BIOS settings: hda:DMA, hdb:pio
[   36.521604]     ide1: BM-DMA at 0xfc08-0xfc0f, BIOS settings: hdc:pio, hdd:pio
[   36.521609] Probing IDE interface ide0...
[   36.859550] usb 1-1: device not accepting address 2, error -71
[   37.387569] hda: PHILIPS PBDV1640P, ATAPI CD/DVD-ROM drive
[   38.060157] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   38.061590] Probing IDE interface ide1...
[   38.239324] usb 5-3: new high speed USB device using ehci_hcd and address 3
[   38.384608] usb 5-3: configuration #1 chosen from 1 choice
[   38.384816] hub 5-3:1.0: USB hub found
[   38.385048] hub 5-3:1.0: 4 ports detected
[   38.631359] ahci 0000:02:00.0: version 2.1
[   38.631383] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 40 (level, low) -> IRQ 40
[   38.637698] hda: ATAPI 40X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(33)
[   38.637704] Uniform CD-ROM driver Revision: 3.20
[   38.731238] usb 1-1: new full speed USB device using uhci_hcd and address 4
[   38.905877] usb 1-1: configuration #1 chosen from 1 choice
[   39.115403] usb 5-3.3: new full speed USB device using ehci_hcd and address 4
[   39.219822] usb 5-3.3: configuration #1 chosen from 1 choice
[   39.229111] usbcore: registered new interface driver hiddev
[   39.231801] input: Razer Razer Copperhead Laser Mouse as /class/input/input2
[   39.231817] input: USB HID v10.01 Mouse [Razer Razer Copperhead Laser Mouse] on usb-0000:00:10.4-3.3
[   39.233442] input: Razer Razer Copperhead Laser Mouse as /class/input/input3
[   39.233455] input: USB HID v10.01 Keyboard [Razer Razer Copperhead Laser Mouse] on usb-0000:00:10.4-3.3
[   39.233465] usbcore: registered new interface driver usbhid
[   39.233468] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   39.635110] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   39.635119] ahci 0000:02:00.0: AHCI 0001.0000 32 slots 2 ports 3 Gbps 0x3 impl SATA mode
[   39.635122] ahci 0000:02:00.0: flags: 64bit ncq pm led clo pmp pio slum part 
[   39.635210] ata1: SATA max UDMA/133 cmd 0xffffc2000001c100 ctl 0x0000000000000000 bmdma 0x0000000000000000 irq 40
[   39.635272] ata2: SATA max UDMA/133 cmd 0xffffc2000001c180 ctl 0x0000000000000000 bmdma 0x0000000000000000 irq 40
[   39.635281] scsi0 : ahci
[   40.119024] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   40.119873] ata1.00: ata_hpa_resize 1: sectors = 321672960, hpa_sectors = 321672960
[   40.119877] ata1.00: ATA-7: Hitachi HCS721616PLA380, P22OAB3A, max UDMA/133
[   40.119879] ata1.00: 321672960 sectors, multi 16: LBA48 NCQ (depth 31/32)
[   40.120877] ata1.00: ata_hpa_resize 1: sectors = 321672960, hpa_sectors = 321672960
[   40.120880] ata1.00: configured for UDMA/133
[   40.120888] scsi1 : ahci
[   40.434960] ata2: SATA link down (SStatus 0 SControl 300)
[   40.435042] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HCS72161 P22O PQ: 0 ANSI: 5
[   40.435715] sata_via 0000:00:0f.0: version 2.1
[   40.435730] ACPI: PCI Interrupt 0000:00:0f.0[B] -> GSI 21 (level, low) -> IRQ 21
[   40.435745] sata_via 0000:00:0f.0: routed to hard irq line 11
[   40.435783] ata3: SATA max UDMA/133 cmd 0x000000000001bc00 ctl 0x000000000001b882 bmdma 0x000000000001b400 irq 21
[   40.435806] ata4: SATA max UDMA/133 cmd 0x000000000001b800 ctl 0x000000000001b482 bmdma 0x000000000001b408 irq 21
[   40.435813] scsi2 : sata_via
[   40.440453] SCSI device sda: 321672960 512-byte hdwr sectors (164697 MB)
[   40.440463] sda: Write Protect is off
[   40.440465] sda: Mode Sense: 00 3a 00 00
[   40.440476] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   40.440514] SCSI device sda: 321672960 512-byte hdwr sectors (164697 MB)
[   40.440521] sda: Write Protect is off
[   40.440522] sda: Mode Sense: 00 3a 00 00
[   40.440533] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   40.440536]  sda: sda1 sda2
[   40.494489] sd 0:0:0:0: Attached scsi disk sda
[   40.497601] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   40.625017] Attempting manual resume
[   40.625020] swsusp: Resume From Partition 8:2
[   40.625022] PM: Checking swsusp image.
[   40.625150] PM: Resume from disk failed.
[   40.642923] ata3: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[   40.653646] ATA: abnormal status 0x7F on port 0x000000000001bc07
[   40.653688] scsi3 : sata_via
[   40.666498] kjournald starting.  Commit interval 5 seconds
[   40.666505] EXT3-fs: mounted filesystem with ordered data mode.
[   40.858887] ata4: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[   40.869610] ATA: abnormal status 0x7F on port 0x000000000001b807
[   40.870329] PCI: Enabling device 0000:02:00.1 (0000 -> 0001)
[   40.870338] ACPI: PCI Interrupt 0000:02:00.1[B] -> GSI 41 (level, low) -> IRQ 41
[   40.870359] PCI: Setting latency timer of device 0000:02:00.1 to 64
[   40.870398] ata5: PATA max UDMA/100 cmd 0x000000000001cc00 ctl 0x000000000001c882 bmdma 0x000000000001c400 irq 41
[   40.870423] ata6: PATA max UDMA/100 cmd 0x000000000001c800 ctl 0x000000000001c482 bmdma 0x000000000001c408 irq 41
[   40.870434] scsi4 : pata_jmicron
[   41.026917] scsi5 : pata_jmicron
[   41.193942] ATA: abnormal status 0x7F on port 0x000000000001c807
[   47.423909] r8169: eth0: link up
[   47.423897] r8169: eth0: link up
[   48.895684] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   48.939133] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   49.182147] parport: PnPBIOS parport detected.
[   49.182191] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   49.243836] NET: Registered protocol family 17
[   49.312583] input: PC Speaker as /class/input/input4
[   49.589541] nvidia: module license 'NVIDIA' taints kernel.
[   49.844330] ACPI: PCI Interrupt 0000:06:00.0[A] -> GSI 24 (level, low) -> IRQ 24
[   49.844340] PCI: Setting latency timer of device 0000:06:00.0 to 64
[   49.844395] irda_init()
[   49.844412] NET: Registered protocol family 23
[   49.844458] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  100.14.11  Wed Jun 13 16:33:22 PDT 2007
[   50.045155] ACPI: PCI Interrupt 0000:00:09.0[A] -> GSI 16 (level, low) -> IRQ 16
[   50.213482] fuse init (API version 7.8)
[   50.242760] lp0: using parport0 (interrupt-driven).
[   50.281911] Adding 514072k swap on /dev/disk/by-uuid/01c688cb-2707-4544-b43d-3e730dec9d0e.  Priority:-1 extents:1 across:514072k
[   50.402844] EXT3 FS on sda1, internal journal
[   54.275330] NET: Registered protocol family 10
[   54.275415] lo: Disabled Privacy Extensions
[   57.657767] ibm_acpi: ec object not found
[   57.725135] Using specific hotkey driver
[   57.841153] input: Power Button (FF) as /class/input/input5
[   57.841350] ACPI: Power Button (FF) [PWRF]
[   57.863119] input: Power Button (CM) as /class/input/input6
[   57.863151] ACPI: Power Button (CM) [PWRB]
[   57.881468] No dock devices found.
[   57.901854] pcc_acpi: loading...
[   62.120307] ppdev: user-space parallel port driver
[   63.320116] Bluetooth: Core ver 2.11
[   63.320165] NET: Registered protocol family 31
[   63.320167] Bluetooth: HCI device and connection manager initialized
[   63.320170] Bluetooth: HCI socket layer initialized
[   63.336489] Bluetooth: L2CAP ver 2.8
[   63.336492] Bluetooth: L2CAP socket layer initialized
[   63.521471] Bluetooth: RFCOMM socket layer initialized
[   63.521482] Bluetooth: RFCOMM TTY layer initialized
[   63.521484] Bluetooth: RFCOMM ver 1.8
[   74.393464] eth0: no IPv6 routers present
[12777.191787] ata1: D2H reg with I during NCQ, this message won't be printed again
[37577.502293] usb 5-3: USB disconnect, address 3
[37577.502298] usb 5-3.3: USB disconnect, address 4
[37577.504244] hald-addon-keyb[5009] general protection rip:2ad0ce12a21b rsp:7fffdd064810 error:0
[37577.746233] usb 5-3: new high speed USB device using ehci_hcd and address 5
[37577.854151] usb 5-3: configuration #1 chosen from 1 choice
[37577.854394] hub 5-3:1.0: USB hub found
[37577.854707] hub 5-3:1.0: 4 ports detected
[37581.016560] usb 5-3.3: new full speed USB device using ehci_hcd and address 7
[37581.117110] usb 5-3.3: configuration #1 chosen from 1 choice
[37581.119466] input: Razer Razer Copperhead Laser Mouse as /class/input/input7
[37581.119540] input: USB HID v10.01 Mouse [Razer Razer Copperhead Laser Mouse] on usb-0000:00:10.4-3.3
[37581.121411] input: Razer Razer Copperhead Laser Mouse as /class/input/input8
[37581.121446] input: USB HID v10.01 Keyboard [Razer Razer Copperhead Laser Mouse] on usb-0000:00:10.4-3.3
[37581.452597] usb 5-3.2: new high speed USB device using ehci_hcd and address 8
[37581.549019] usb 5-3.2: configuration #1 chosen from 1 choice
[37581.604713] usbcore: registered new interface driver libusual
[37581.636305] Initializing USB Mass Storage driver...
[37581.636369] scsi6 : SCSI emulation for USB Mass Storage devices
[37581.636419] usbcore: registered new interface driver usb-storage
[37581.636423] USB Mass Storage support registered.
[37581.636542] usb-storage: device found at 8
[37581.636544] usb-storage: waiting for device to settle before scanning
[37586.611579] usb-storage: device scan complete
[37586.637254] scsi 6:0:0:0: Direct-Access     SAMSUNG  ECLAIR USB MASS  1.00 PQ: 0 ANSI: 2
[37586.638862] SCSI device sdb: 494080 512-byte hdwr sectors (253 MB)
[37586.639485] sdb: Write Protect is off
[37586.639488] sdb: Mode Sense: 03 00 00 00
[37586.639491] sdb: assuming drive cache: write through
[37586.641239] SCSI device sdb: 494080 512-byte hdwr sectors (253 MB)
[37586.641860] sdb: Write Protect is off
[37586.641863] sdb: Mode Sense: 03 00 00 00
[37586.641865] sdb: assuming drive cache: write through
[37586.641869]  sdb: unknown partition table
[37586.677126] sd 6:0:0:0: Attached scsi removable disk sdb
[37586.677160] sd 6:0:0:0: Attached scsi generic sg1 type 0
[43273.412576] usb 5-3.2: USB disconnect, address 8
[43287.297880] usb 5-3: USB disconnect, address 5
[43287.297885] usb 5-3.3: USB disconnect, address 7
[43287.270890] hald-addon-keyb[28099] general protection rip:2aba7775c21b rsp:7fff33a33200 error:0
[43287.537820] usb 5-3: new high speed USB device using ehci_hcd and address 9
[43287.643737] usb 5-3: configuration #1 chosen from 1 choice
[43287.643936] hub 5-3:1.0: USB hub found
[43287.644163] hub 5-3:1.0: 4 ports detected
[43290.990230] usb 5-3.3: new full speed USB device using ehci_hcd and address 11
[43291.087284] usb 5-3.3: configuration #1 chosen from 1 choice
[43291.089874] input: Razer Razer Copperhead Laser Mouse as /class/input/input9
[43291.089938] input: USB HID v10.01 Mouse [Razer Razer Copperhead Laser Mouse] on usb-0000:00:10.4-3.3
[43291.091598] input: Razer Razer Copperhead Laser Mouse as /class/input/input10
[43291.091636] input: USB HID v10.01 Keyboard [Razer Razer Copperhead Laser Mouse] on usb-0000:00:10.4-3.3
[43291.422146] usb 5-3.2: new high speed USB device using ehci_hcd and address 12
[43291.514695] usb 5-3.2: configuration #1 chosen from 1 choice
[43291.514825] scsi7 : SCSI emulation for USB Mass Storage devices
[43291.542169] usb-storage: device found at 12
[43291.542172] usb-storage: waiting for device to settle before scanning
[43296.513138] usb-storage: device scan complete
[43296.540796] scsi 7:0:0:0: Direct-Access     SAMSUNG  ECLAIR USB MASS  1.00 PQ: 0 ANSI: 2
[43296.542161] SCSI device sdb: 494080 512-byte hdwr sectors (253 MB)
[43296.542783] sdb: Write Protect is off
[43296.542786] sdb: Mode Sense: 03 00 00 00
[43296.542788] sdb: assuming drive cache: write through
[43296.544407] SCSI device sdb: 494080 512-byte hdwr sectors (253 MB)
[43296.545031] sdb: Write Protect is off
[43296.545034] sdb: Mode Sense: 03 00 00 00
[43296.545036] sdb: assuming drive cache: write through
[43296.545039]  sdb: unknown partition table
[43296.589302] sd 7:0:0:0: Attached scsi removable disk sdb
[43296.589340] sd 7:0:0:0: Attached scsi generic sg1 type 0
[43355.315836] usb 5-3.2: USB disconnect, address 12
[43403.706652] usb 5-3: USB disconnect, address 9
[43403.706657] usb 5-3.3: USB disconnect, address 11
[43403.681972] hald-addon-keyb[31113] general protection rip:2b083202021b rsp:7fff7916e940 error:0
[43403.946591] usb 5-3: new high speed USB device using ehci_hcd and address 13
[43404.052571] usb 5-3: configuration #1 chosen from 1 choice
[43404.052767] hub 5-3:1.0: USB hub found
[43404.052997] hub 5-3:1.0: 4 ports detected
[43407.386941] usb 5-3.3: new full speed USB device using ehci_hcd and address 15
[43407.483247] usb 5-3.3: configuration #1 chosen from 1 choice
[43407.486097] input: Razer Razer Copperhead Laser Mouse as /class/input/input11
[43407.486173] input: USB HID v10.01 Mouse [Razer Razer Copperhead Laser Mouse] on usb-0000:00:10.4-3.3
[43407.487780] input: Razer Razer Copperhead Laser Mouse as /class/input/input12
[43407.487817] input: USB HID v10.01 Keyboard [Razer Razer Copperhead Laser Mouse] on usb-0000:00:10.4-3.3
[43407.782862] usb 5-3.2: new high speed USB device using ehci_hcd and address 16
[43407.875417] usb 5-3.2: configuration #1 chosen from 1 choice
[43407.875539] scsi8 : SCSI emulation for USB Mass Storage devices
[43407.902912] usb-storage: device found at 16
[43407.902915] usb-storage: waiting for device to settle before scanning
[43412.873976] usb-storage: device scan complete
[43412.901674] scsi 8:0:0:0: Direct-Access     SAMSUNG  ECLAIR USB MASS  1.00 PQ: 0 ANSI: 2
[43412.903159] SCSI device sdb: 494080 512-byte hdwr sectors (253 MB)
[43412.903781] sdb: Write Protect is off
[43412.903785] sdb: Mode Sense: 03 00 00 00
[43412.903787] sdb: assuming drive cache: write through
[43412.905406] SCSI device sdb: 494080 512-byte hdwr sectors (253 MB)
[43412.906030] sdb: Write Protect is off
[43412.906033] sdb: Mode Sense: 03 00 00 00
[43412.906035] sdb: assuming drive cache: write through
[43412.906039]  sdb: unknown partition table
[43412.950293] sd 8:0:0:0: Attached scsi removable disk sdb
[43412.950328] sd 8:0:0:0: Attached scsi generic sg1 type 0

```

---

### Post by sab0403 on 2007-08-10
Interesting, interesting... I'm still in the dark about getting the OS to *not* try and initialize/use certain devices on boot (say, that pesky eth0 I don't use...)

simon, you have a problem. Big one... :popcorn:

---

### Post by Steveway on 2007-08-10
Nah, Simon. I think that jump is after the system has allready started.
Should be similar to my mounted partitions at the end.
You don't wanna tell me that you need about 12 hours to boot up.
That:
> [   41.193942] ATA: abnormal status 0x7F on port 0x000000000001c807
Seems to be the biggest slowdown on your system, it puts you back for about 7 seconds.
EDIT: And you pcc and bluetooth thing.
EDIT2: What? Did it now got faster or slower?
```
[    0.000000] Linux version 2.6.20-16-generic (root@terranova) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Thu Jun 7 20:19:32 UTC 2007 (Ubuntu 2.6.20-16.29-generic)
[    0.000000] BIOS-provided physical RAM map:
[    0.000000] sanitize start
[    0.000000] sanitize end
[    0.000000] copy_e820_map() start: 0000000000000000 size: 000000000009f800 end: 000000000009f800 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000000009f800 size: 0000000000000800 end: 00000000000a0000 type: 2
[    0.000000] copy_e820_map() start: 00000000000d8000 size: 0000000000028000 end: 0000000000100000 type: 2
[    0.000000] copy_e820_map() start: 0000000000100000 size: 000000001fe70000 end: 000000001ff70000 type: 1
[    0.000000] copy_e820_map() type is E820_RAM
[    0.000000] copy_e820_map() start: 000000001ff70000 size: 000000000000a000 end: 000000001ff7a000 type: 3
[    0.000000] copy_e820_map() start: 000000001ff7a000 size: 0000000000006000 end: 000000001ff80000 type: 4
[    0.000000] copy_e820_map() start: 000000001ff80000 size: 0000000000080000 end: 0000000020000000 type: 2
[    0.000000] copy_e820_map() start: 00000000fffe0000 size: 0000000000020000 end: 0000000100000000 type: 2
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[    0.000000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000d8000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000001ff70000 (usable)
[    0.000000]  BIOS-e820: 000000001ff70000 - 000000001ff7a000 (ACPI data)
[    0.000000]  BIOS-e820: 000000001ff7a000 - 000000001ff80000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000001ff80000 - 0000000020000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fffe0000 - 0000000100000000 (reserved)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 511MB LOWMEM available.
[    0.000000] found SMP MP-table at 000f6910
[    0.000000] Entering add_active_range(0, 0, 130928) 0 entries of 256 used
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   Normal       4096 ->   130928
[    0.000000]   HighMem    130928 ->   130928
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   130928
[    0.000000] On node 0 totalpages: 130928
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 4064 pages, LIFO batch:0
[    0.000000]   Normal zone: 990 pages used for memmap
[    0.000000]   Normal zone: 125842 pages, LIFO batch:31
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000] DMI 2.3 present.
[    0.000000] ACPI: RSDP (v000 PTLTD                                 ) @ 0x000f6a60
[    0.000000] ACPI: RSDT (v001 PTLTD    RSDT   0x06040000  LTP 0x00000000) @ 0x1ff73fde
[    0.000000] ACPI: FADT (v002 AMDK8  PTLTW    0x06040000 PTL_ 0x000f4240) @ 0x1ff79e56
[    0.000000] ACPI: SSDT (v001 PTLTD  POWERNOW 0x06040000  LTP 0x00000001) @ 0x1ff79eda
[    0.000000] ACPI: MADT (v001 PTLTD    APIC   0x06040000  LTP 0x00000000) @ 0x1ff79fb0
[    0.000000] ACPI: DSDT (v001  VIA   PTL_ACPI 0x06040000 MSFT 0x0100000e) @ 0x00000000
[    0.000000] ACPI: PM-Timer IO Port: 0x4008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] Processor #0 15:8 APIC version 16
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x01] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 1, version 3, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 high edge)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 20000000:dffe0000)
[    0.000000] Detected 1801.122 MHz processor.
[   18.537760] Built 1 zonelists.  Total pages: 129906
[   18.537764] Kernel command line: root=UUID=22a39130-eb58-4398-9ecc-a98a236057f1 ro quiet splash
[   18.537905] mapped APIC to ffffd000 (fee00000)
[   18.537908] mapped IOAPIC to ffffc000 (fec00000)
[   18.537911] Enabling fast FPU save and restore... done.
[   18.537913] Enabling unmasked SIMD FPU exception support... done.
[   18.537921] Initializing CPU#0
[   18.537979] PID hash table entries: 2048 (order: 11, 8192 bytes)
[   18.539879] Console: colour VGA+ 80x25
[   18.540107] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[   18.540549] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[   18.550093] Memory: 508216k/523712k available (1992k kernel code, 14936k reserved, 900k data, 328k init, 0k highmem)
[   18.550104] virtual kernel memory layout:
[   18.550105]     fixmap  : 0xfff4e000 - 0xfffff000   ( 708 kB)
[   18.550107]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[   18.550108]     vmalloc : 0xe0800000 - 0xff7fe000   ( 495 MB)
[   18.550109]     lowmem  : 0xc0000000 - 0xdff70000   ( 511 MB)
[   18.550111]       .init : 0xc03d9000 - 0xc042b000   ( 328 kB)
[   18.550112]       .data : 0xc02f2374 - 0xc03d36d4   ( 900 kB)
[   18.550113]       .text : 0xc0100000 - 0xc02f2374   (1992 kB)
[   18.550116] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[   18.629901] Calibrating delay using timer specific routine.. 3605.64 BogoMIPS (lpj=7211290)
[   18.629939] Security Framework v1.0.0 initialized
[   18.629946] SELinux:  Disabled at boot.
[   18.629960] Mount-cache hash table entries: 512
[   18.630081] CPU: After generic identify, caps: 078bfbff c1d3fbff 00000000 00000000 00000000 00000000 00000000
[   18.630090] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   18.630092] CPU: L2 Cache: 128K (64 bytes/line)
[   18.630095] CPU: After all inits, caps: 078bfbff c1d3fbff 00000000 00000410 00000000 00000000 00000000
[   18.630105] Compat vDSO mapped to ffffe000.
[   18.630108] Remapping vsyscall page to ffffe000
[   18.630117] Checking 'hlt' instruction... OK.
[   18.645998] SMP alternatives: switching to UP code
[   18.646186] Freeing SMP alternatives: 11k freed
[   18.646397] Early unpacking initramfs... done
[   18.948484] ACPI: Core revision 20060707
[   18.950109] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   19.037992] CPU0: AMD Mobile AMD Sempron(tm) Processor 3000+ stepping 02
[   19.038011] Total of 1 processors activated (3605.64 BogoMIPS).
[   19.038507] ENABLING IO-APIC IRQs
[   19.038810] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=0 pin2=0
[   19.185418] Brought up 1 CPUs
[   19.185654] Booting paravirtualized kernel on bare hardware
[   19.185734] Time:  0:27:47  Date: 07/11/107
[   19.185762] NET: Registered protocol family 16
[   19.185848] EISA bus registered
[   19.185852] ACPI: bus type pci registered
[   19.192471] PCI: PCI BIOS revision 2.10 entry at 0xfd557, last bus=1
[   19.192474] PCI: Using configuration type 1
[   19.192475] Setting up standard PCI resources
[   19.196302] ACPI: Interpreter enabled
[   19.196308] ACPI: Using IOAPIC for interrupt routing
[   19.196688] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   19.196693] PCI: Probing PCI hardware (bus 00)
[   19.197996] PCI quirk: region 4000-407f claimed by vt8235 PM
[   19.198001] PCI quirk: region 8100-810f claimed by vt8235 SMB
[   19.198259] Boot video device is 0000:01:00.0
[   19.198363] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   19.212337] ACPI: PCI Interrupt Link [ALKA] (IRQs 16 17 18 19 20 21 22 23) *10, disabled.
[   19.212553] ACPI: PCI Interrupt Link [ALKB] (IRQs 16 17 18 19 20 21 22 23) *10, disabled.
[   19.212764] ACPI: PCI Interrupt Link [ALKC] (IRQs 22) *11, disabled.
[   19.212973] ACPI: PCI Interrupt Link [ALKD] (IRQs 21) *11, disabled.
[   19.213210] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 9 12 14 15) *10
[   19.213472] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 7 *10 12 14 15)
[   19.213713] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 *11 12 14 15)
[   19.213952] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[   19.234831] Linux Plug and Play Support v0.97 (c) Adam Belay
[   19.234847] pnp: PnP ACPI init
[   19.247420] pnp: PnP ACPI: found 11 devices
[   19.247426] PnPBIOS: Disabled by ACPI PNP
[   19.247482] PCI: Using ACPI for IRQ routing
[   19.247485] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   19.251095] NET: Registered protocol family 8
[   19.251097] NET: Registered protocol family 20
[   19.251379] pnp: 00:06: ioport range 0x600-0x60f has been reserved
[   19.251382] pnp: 00:06: ioport range 0x1c0-0x1cf has been reserved
[   19.251385] pnp: 00:06: ioport range 0x4d0-0x4d1 has been reserved
[   19.251388] pnp: 00:06: ioport range 0xfe10-0xfe11 could not be reserved
[   19.251630] PCI: Bridge: 0000:00:01.0
[   19.251632]   IO window: disabled.
[   19.251637]   MEM window: c1000000-c1ffffff
[   19.251640]   PREFETCH window: e0000000-efffffff
[   19.251644] PCI: Bus 2, cardbus bridge: 0000:00:0b.0
[   19.251646]   IO window: 00002000-000020ff
[   19.251650]   IO window: 00002400-000024ff
[   19.251653]   PREFETCH window: 30000000-33ffffff
[   19.251657]   MEM window: 34000000-37ffffff
[   19.251661] PCI: Bus 6, cardbus bridge: 0000:00:0b.1
[   19.251663]   IO window: 00002800-000028ff
[   19.251666]   IO window: 00002c00-00002cff
[   19.251670]   PREFETCH window: 38000000-3bffffff
[   19.251673]   MEM window: 3c000000-3fffffff
[   19.251690] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   19.251706] ACPI: PCI Interrupt 0000:00:0b.0[A] -> GSI 17 (level, low) -> IRQ 16
[   19.251715] PCI: Setting latency timer of device 0000:00:0b.0 to 64
[   19.251724] PCI: Enabling device 0000:00:0b.1 (0000 -> 0003)
[   19.251728] ACPI: PCI Interrupt 0000:00:0b.1[B] -> GSI 18 (level, low) -> IRQ 17
[   19.251738] PCI: Setting latency timer of device 0000:00:0b.1 to 64
[   19.251766] NET: Registered protocol family 2
[   19.285363] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[   19.285441] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[   19.285552] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[   19.285618] TCP: Hash tables configured (established 16384 bind 8192)
[   19.285621] TCP reno registered
[   19.297402] checking if image is initramfs... it is
[   19.895297] Freeing initrd memory: 6737k freed
[   19.895675] audit: initializing netlink socket (disabled)
[   19.895688] audit(1186792068.340:1): initialized
[   19.895786] VFS: Disk quotas dquot_6.5.1
[   19.895804] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[   19.895849] io scheduler noop registered
[   19.895851] io scheduler anticipatory registered
[   19.895854] io scheduler deadline registered
[   19.895861] io scheduler cfq registered (default)
[   19.896145] isapnp: Scanning for PnP cards...
[   20.249776] isapnp: No Plug & Play device found
[   20.280983] Real Time Clock Driver v1.12ac
[   20.281023] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   20.281127] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   20.281859] mice: PS/2 mouse device common for all mice
[   20.282295] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   20.282502] input: Macintosh mouse button emulation as /class/input/input0
[   20.282529] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   20.282533] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   20.282752] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   20.286119] i8042.c: Detected active multiplexing controller, rev 1.1.
[   20.287407] serio: i8042 KBD port at 0x60,0x64 irq 1
[   20.287411] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[   20.287414] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[   20.287417] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[   20.287419] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[   20.287549] EISA: Probing bus 0 at eisa.0
[   20.287557] Cannot allocate resource for EISA slot 1
[   20.287560] Cannot allocate resource for EISA slot 2
[   20.287567] Cannot allocate resource for EISA slot 4
[   20.287584] EISA: Detected 0 cards.
[   20.317645] TCP cubic registered
[   20.317651] NET: Registered protocol family 1
[   20.317670] Using IPI No-Shortcut mode
[   20.317731] ACPI: (supports S0 S3 S4 S5)
[   20.317763]   Magic number: 3:759:455
[   20.318168] Freeing unused kernel memory: 328k freed
[   20.320314] Time: tsc clocksource has been installed.
[   20.333500] input: AT Translated Set 2 keyboard as /class/input/input1
[   21.558413] Capability LSM initialized
[   21.692730] ACPI: Thermal Zone [THRS] (53 C)
[   21.783581] ACPI: Thermal Zone [THRC] (62 C)
[   22.347434] ieee1394: Initialized config rom entry `ip1394'
[   22.348606] ACPI: PCI Interrupt 0000:00:0b.2[C] -> GSI 19 (level, low) -> IRQ 18
[   22.414412] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[18]  MMIO=[c0005000-c00057ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   22.414649] usbcore: registered new interface driver usbfs
[   22.414668] usbcore: registered new interface driver hub
[   22.414687] usbcore: registered new device driver usb
[   22.415559] USB Universal Host Controller Interface driver v3.0
[   22.415616] ACPI: PCI Interrupt 0000:00:10.0[A] -> GSI 21 (level, low) -> IRQ 19
[   22.415627] uhci_hcd 0000:00:10.0: UHCI Host Controller
[   22.415734] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[   22.415765] uhci_hcd 0000:00:10.0: irq 19, io base 0x00001c00
[   22.415878] usb usb1: configuration #1 chosen from 1 choice
[   22.415905] hub 1-0:1.0: USB hub found
[   22.415912] hub 1-0:1.0: 2 ports detected
[   22.522370] ACPI: PCI Interrupt 0000:00:10.1[B] -> GSI 21 (level, low) -> IRQ 19
[   22.522382] uhci_hcd 0000:00:10.1: UHCI Host Controller
[   22.522402] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
[   22.522424] uhci_hcd 0000:00:10.1: irq 19, io base 0x00001c20
[   22.522503] usb usb2: configuration #1 chosen from 1 choice
[   22.522528] hub 2-0:1.0: USB hub found
[   22.522535] hub 2-0:1.0: 2 ports detected
[   22.563649] via-rhine.c:v1.10-LK1.4.2 Sept-11-2006 Written by Donald Becker
[   22.630201] ACPI: PCI Interrupt 0000:00:10.2[C] -> GSI 21 (level, low) -> IRQ 19
[   22.630213] uhci_hcd 0000:00:10.2: UHCI Host Controller
[   22.630238] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
[   22.630260] uhci_hcd 0000:00:10.2: irq 19, io base 0x00001c40
[   22.630349] usb usb3: configuration #1 chosen from 1 choice
[   22.630373] hub 3-0:1.0: USB hub found
[   22.630380] hub 3-0:1.0: 2 ports detected
[   22.739817] ACPI: PCI Interrupt 0000:00:10.3[D] -> GSI 21 (level, low) -> IRQ 19
[   22.739835] ehci_hcd 0000:00:10.3: EHCI Host Controller
[   22.739873] ehci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
[   22.739910] ehci_hcd 0000:00:10.3: irq 19, io mem 0xc0005800
[   22.739917] ehci_hcd 0000:00:10.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   22.740005] usb usb4: configuration #1 chosen from 1 choice
[   22.740031] hub 4-0:1.0: USB hub found
[   22.740039] hub 4-0:1.0: 6 ports detected
[   22.765976] usb 1-1: new low speed USB device using uhci_hcd and address 2
[   22.847303] VP_IDE: IDE controller at PCI slot 0000:00:11.1
[   22.847388] ACPI: Unable to derive IRQ for device 0000:00:11.1
[   22.847391] ACPI: PCI Interrupt 0000:00:11.1[A]: no GSI
[   22.847400] VP_IDE: chipset revision 6
[   22.847402] VP_IDE: not 100% native mode: will probe irqs later
[   22.847412] VP_IDE: VIA vt8235 (rev 00) IDE UDMA133 controller on pci0000:00:11.1
[   22.847419]     ide0: BM-DMA at 0x1c60-0x1c67, BIOS settings: hda:DMA, hdb:pio
[   22.847430]     ide1: BM-DMA at 0x1c68-0x1c6f, BIOS settings: hdc:DMA, hdd:pio
[   22.847437] Probing IDE interface ide0...
[   23.289531] hda: TOSHIBA MK6025GAS, ATA DISK drive
[   23.689187] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[000ae404481044de]
[   23.900851] usb 4-2: new high speed USB device using ehci_hcd and address 3
[   23.964910] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   24.014393] Probing IDE interface ide1...
[   24.047394] usb 4-2: configuration #1 chosen from 1 choice
[   24.232846] usbcore: registered new interface driver libusual
[   24.239285] SCSI subsystem initialized
[   24.240650] Initializing USB Mass Storage driver...
[   24.476295] usb 1-1: new low speed USB device using uhci_hcd and address 3
[   24.646287] usb 1-1: configuration #1 chosen from 1 choice
[   24.887989] hdc: TSSTcorpCD/DVDW TS-L532A, ATAPI CD/DVD-ROM drive
[   24.891899] usb 2-2: new full speed USB device using uhci_hcd and address 2
[   25.122820] usb 2-2: configuration #1 chosen from 1 choice
[   25.126012] scsi0 : SCSI emulation for USB Mass Storage devices
[   25.126051] usb-storage: device found at 3
[   25.126053] usb-storage: waiting for device to settle before scanning
[   25.126066] usbcore: registered new interface driver usb-storage
[   25.126069] USB Mass Storage support registered.
[   25.127942] usbcore: registered new interface driver hiddev
[   25.140759] input: PS/2+USB Mouse as /class/input/input2
[   25.140778] input: USB HID v1.11 Mouse [PS/2+USB Mouse] on usb-0000:00:10.0-1
[   25.140793] usbcore: registered new interface driver usbhid
[   25.140797] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   25.600886] ide1 at 0x170-0x177,0x376 on irq 15
[   25.614699] libata version 2.20 loaded.
[   25.617344] ACPI: PCI Interrupt 0000:00:12.0[A] -> GSI 23 (level, low) -> IRQ 20
[   25.621357] eth0: VIA Rhine II at 0x11800, 00:0a:e4:a1:0e:db, IRQ 20.
[   25.622070] eth0: MII PHY found at address 1, status 0x7849 advertising 05e1 Link 0000.
[   25.629629] hda: max request size: 128KiB
[   25.637794] hda: 117210240 sectors (60011 MB), CHS=65535/16/63, UDMA(100)
[   25.638709] hda: cache flushes supported
[   25.638753]  hda: hda1 hda2 hda3
[   25.718710] hdc: ATAPI 24X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(33)
[   25.718720] Uniform CD-ROM driver Revision: 3.20
[   30.122968] usb-storage: device scan complete
[   30.126341] scsi 0:0:0:0: Direct-Access     Maxtor 6 L250R0           0000 PQ: 0 ANSI: 0
[   30.133694] SCSI device sda: 490234752 512-byte hdwr sectors (251000 MB)
[   30.134557] sda: Write Protect is off
[   30.134559] sda: Mode Sense: 27 00 00 00
[   30.134561] sda: assuming drive cache: write through
[   30.135431] SCSI device sda: 490234752 512-byte hdwr sectors (251000 MB)
[   30.136304] sda: Write Protect is off
[   30.136306] sda: Mode Sense: 27 00 00 00
[   30.136308] sda: assuming drive cache: write through
[   30.136311]  sda: sda1 sda2
[   30.158708] sd 0:0:0:0: Attached scsi disk sda
[   30.162834] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   30.520204] kjournald starting.  Commit interval 5 seconds
[   30.520217] EXT3-fs: mounted filesystem with ordered data mode.
[   34.857240] eth1: link down
[   36.066263] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   36.070089] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   36.158740] Linux agpgart interface v0.102 (c) Dave Jones
[   36.161935] agpgart: Detected AGP bridge 0
[   36.169851] agpgart: AGP aperture is 256M @ 0xd0000000
[   36.245803] Yenta: CardBus bridge found at 0000:00:0b.0 [1025:006e]
[   36.245820] Yenta: Using CSCINT to route CSC interrupts to PCI
[   36.245822] Yenta: Routing CardBus interrupts to PCI
[   36.245827] Yenta TI: socket 0000:00:0b.0, mfunc 0x010a1b22, devctl 0x64
[   36.481465] Yenta: ISA IRQ mask 0x0cf8, PCI irq 16
[   36.481470] Socket status: 30000820
[   36.481662] Yenta: CardBus bridge found at 0000:00:0b.1 [1025:006e]
[   36.481676] Yenta: Using CSCINT to route CSC interrupts to PCI
[   36.481678] Yenta: Routing CardBus interrupts to PCI
[   36.481683] Yenta TI: socket 0000:00:0b.1, mfunc 0x010a1b22, devctl 0x64
[   36.717224] Yenta: ISA IRQ mask 0x0cf8, PCI irq 17
[   36.717229] Socket status: 30000086
[   37.120117] pccard: CardBus card inserted into slot 0
[   37.530873] nvidia: module license 'NVIDIA' taints kernel.
[   37.783768] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) -> IRQ 21
[   37.784064] NVRM: loading NVIDIA UNIX x86 Kernel Module  100.14.11  Wed Jun 13 18:21:22 PDT 2007
[   37.808558] parport: PnPBIOS parport detected.
[   37.808636] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[   37.879782] input: PC Speaker as /class/input/input3
[   38.104008] NET: Registered protocol family 17
[   38.127014] irda_init()
[   38.127033] NET: Registered protocol family 23
[   38.427611] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   38.525913] Linux video capture interface: v2.00
[   38.580142] ACPI: PCI Interrupt 0000:00:11.6[C] -> GSI 22 (level, low) -> IRQ 22
[   38.586749] PCI: Setting latency timer of device 0000:00:11.6 to 64
[   38.632106] cs: IO port probe 0x100-0x3af: clean.
[   38.634009] cs: IO port probe 0x3e0-0x4ff: clean.
[   38.634823] cs: IO port probe 0x820-0x8ff: clean.
[   38.635512] cs: IO port probe 0xc00-0xcf7: clean.
[   38.636327] cs: IO port probe 0xa00-0xaff: clean.
[   38.667551] Synaptics Touchpad, model: 1, fw: 5.8, id: 0x9248b1, caps: 0x904713/0x4000
[   38.709111] input: SynPS/2 Synaptics TouchPad as /class/input/input4
[   38.712211] nsc_ircc_pnp_probe() : From PnP, found firbase 0x3F8 ; irq 3 ; dma 1.
[   38.712239] nsc-ircc, chip->init
[   38.712249] nsc-ircc, Found chip at base=0x02e
[   38.712276] nsc-ircc, driver loaded (Dag Brattli)
[   38.712282] nsc_ircc_open(), can't get iobase of 0x3f8
[   38.712311] nsc-ircc, Found chip at base=0x02e
[   38.712337] nsc-ircc, driver loaded (Dag Brattli)
[   38.712339] nsc_ircc_open(), can't get iobase of 0x3f8
[   38.712509] pnp: Device 00:0a disabled.
[   38.776537] ubuntu/media/gspcav1/gspca_core.c: USB SPCA5XX camera found. (PAC207)
[   38.780974] usbcore: registered new interface driver gspca
[   38.780979] ubuntu/media/gspcav1/gspca_core.c: gspca driver 01.00.12 registered
[   38.807064] wlan: 0.8.4.2 (0.9.3.1)
[   38.830740] ath_pci: 0.9.4.5 (0.9.3.1)
[   38.831977] cs: IO port probe 0x100-0x3af: clean.
[   38.833879] cs: IO port probe 0x3e0-0x4ff: clean.
[   38.834700] cs: IO port probe 0x820-0x8ff: clean.
[   38.835389] cs: IO port probe 0xc00-0xcf7: clean.
[   38.836201] cs: IO port probe 0xa00-0xaff: clean.
[   39.095138] PCI: Enabling device 0000:02:00.0 (0000 -> 0002)
[   39.095148] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 17 (level, low) -> IRQ 16
[   39.688817] ath_rate_sample: 1.2 (0.9.3.1)
[   39.689160] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[   39.689166] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[   39.689174] wifi0: turboG rates: 6Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[   39.689180] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
[   39.689183] wifi0: mac 7.9 phy 4.5 radio 5.6
[   39.689193] wifi0: Use hw queue 1 for WME_AC_BE traffic
[   39.689195] wifi0: Use hw queue 0 for WME_AC_BK traffic
[   39.689197] wifi0: Use hw queue 2 for WME_AC_VI traffic
[   39.689200] wifi0: Use hw queue 3 for WME_AC_VO traffic
[   39.689201] wifi0: Use hw queue 8 for CAB traffic
[   39.689203] wifi0: Use hw queue 9 for beacons
[   39.749656] wifi0: Atheros 5212: mem=0x34000000, irq=16
[   39.749928] ACPI: PCI Interrupt 0000:00:11.5[C] -> GSI 22 (level, low) -> IRQ 22
[   39.750060] PCI: Setting latency timer of device 0000:00:11.5 to 64
[   40.526888] lp0: using parport0 (interrupt-driven).
[   40.808292] EXT3 FS on sda2, internal journal
[   43.812579] NET: Registered protocol family 10
[   43.812672] lo: Disabled Privacy Extensions
[   43.812729] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   47.237590] ACPI: AC Adapter [AC] (on-line)
[   47.292884] ACPI: Battery Slot [BAT0] (battery absent)
[   47.346379] input: Power Button (FF) as /class/input/input5
[   47.350195] ACPI: Power Button (FF) [PWRF]
[   47.385665] input: Lid Switch as /class/input/input6
[   47.389459] ACPI: Lid Switch [LID]
[   47.424936] input: Sleep Button (CM) as /class/input/input7
[   47.428709] ACPI: Sleep Button (CM) [SLPB]
[   47.446630] Using specific hotkey driver
[   47.482577] No dock devices found.
[   47.524936] ibm_acpi: ec object not found
[   47.610915] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   47.639571] pcc_acpi: loading...
[   48.024248] powernow-k8: Found 1 Mobile AMD Sempron(tm) Processor 3000+ processors (version 2.00.00)
[   48.024293] powernow-k8:    0 : fid 0xa (1800 MHz), vid 0x6
[   48.024295] powernow-k8:    1 : fid 0x8 (1600 MHz), vid 0xa
[   48.024298] powernow-k8:    2 : fid 0x0 (800 MHz), vid 0x18
[   48.025473] powernow-k8: ph2 null fid transition 0xa
[   49.441478] ttyS0: LSR safety check engaged!
[   53.482701] ppdev: user-space parallel port driver
[   54.012518] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[   54.012531] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[   54.012588] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[   54.751080] ath0: no IPv6 routers present
[   36.864000] Time: acpi_pm clocksource has been installed.

```
I'm gonna look if I can remove that parallel port driver, I don't really use the parallel port on my laptop.

---

### Post by kerry_s on 2007-08-10
it's the smaller partion you installed back on less seek time. that's why it's reccommended you split installs to several partions.

---

### Post by _simon_ on 2007-08-11
Well after some fiddling I'm down to this:

```

[    0.000000] Linux version 2.6.20-16-generic (root@king) (gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)) #2 SMP Thu Jun 7 19:00:28 UTC 2007 (Ubuntu 2.6.20-16.29-generic)
[    0.000000] Command line: root=UUID=b1f90171-318e-4980-bd93-dc70ed188850 ro quiet splash
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007ffb0000 (usable)
[    0.000000]  BIOS-e820: 000000007ffb0000 - 000000007ffc0000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007ffc0000 - 000000007fff0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007fff0000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fecc0000 - 00000000fecc1000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff380000 - 0000000100000000 (reserved)
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 524208) 1 entries of 3200 used
[    0.000000] end_pfn_map = 1048576
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP (v000 ACPIAM                                ) @ 0x00000000000f8e40
[    0.000000] ACPI: RSDT (v001 A M I  OEMRSDT  0x12000620 MSFT 0x00000097) @ 0x000000007ffb0000
[    0.000000] ACPI: FADT (v002 A M I  OEMFACP  0x12000620 MSFT 0x00000097) @ 0x000000007ffb0200
[    0.000000] ACPI: MADT (v001 A M I  OEMAPIC  0x12000620 MSFT 0x00000097) @ 0x000000007ffb0390
[    0.000000] ACPI: MCFG (v001 A M I  OEMMCFG  0x12000620 MSFT 0x00000097) @ 0x000000007ffb0400
[    0.000000] ACPI: OEMB (v001 A M I  AMI_OEM  0x12000620 MSFT 0x00000097) @ 0x000000007ffc0040
[    0.000000] ACPI: DSDT (v001  AS2GL AS2GL000 0x00000000 INTL 0x02002026) @ 0x0000000000000000
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] Number of nodes 1
[    0.000000] Node 0 MemBase 0000000000000000 Limit 000000007ffb0000
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 524208) 1 entries of 3200 used
[    0.000000] NUMA: Using 63 for the hash shift.
[    0.000000] Using node hash shift of 63
[    0.000000] Bootmem setup node 0 0000000000000000-000000007ffb0000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   DMA32        4096 ->  1048576
[    0.000000]   Normal    1048576 ->  1048576
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0:        0 ->      159
[    0.000000]     0:      256 ->   524208
[    0.000000] On node 0 totalpages: 524111
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 1087 pages reserved
[    0.000000]   DMA zone: 2856 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 7110 pages used for memmap
[    0.000000]   DMA32 zone: 513002 pages, LIFO batch:31
[    0.000000]   Normal zone: 0 pages used for memmap
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 (Bootup-CPU)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] Processor #1
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: IOAPIC (id[0x03] address[0xfecc0000] gsi_base[24])
[    0.000000] IOAPIC[1]: apic_id 3, address 0xfecc0000, GSI 24-47
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Setting APIC routing to physical flat
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] Nosave address range: 000000000009f000 - 00000000000a0000
[    0.000000] Nosave address range: 00000000000a0000 - 00000000000e4000
[    0.000000] Nosave address range: 00000000000e4000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:60000000)
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] PERCPU: Allocating 34048 bytes of per cpu data
[    0.000000] Built 1 zonelists.  Total pages: 515858
[    0.000000] Kernel command line: root=UUID=b1f90171-318e-4980-bd93-dc70ed188850 ro quiet splash
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[   29.626696] Console: colour VGA+ 80x25
[   29.627383] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
[   29.628403] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
[   29.628763] Checking aperture...
[   29.628766] CPU 0: aperture @ 1022000000 size 32 MB
[   29.628768] Aperture too small (32 MB)
[   29.636808] No AGP bridge found
[   29.649865] Memory: 2053340k/2096832k available (2217k kernel code, 43104k reserved, 1162k data, 304k init)
[   29.727202] Calibrating delay using timer specific routine.. 4878.47 BogoMIPS (lpj=9756958)
[   29.727246] Security Framework v1.0.0 initialized
[   29.727250] SELinux:  Disabled at boot.
[   29.727268] Mount-cache hash table entries: 256
[   29.727374] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   29.727376] CPU: L2 Cache: 512K (64 bytes/line)
[   29.727378] CPU 0/0 -> Node 0
[   29.727380] CPU: Physical Processor ID: 0
[   29.727381] CPU: Processor Core ID: 0
[   29.727398] SMP alternatives: switching to UP code
[   29.727589] Early unpacking initramfs... done
[   29.968422] ACPI: Core revision 20060707
[   29.968776] ACPI: Looking for DSDT in initramfs... file /DSDT.aml not found, using machine DSDT.
[   30.011259] Using local APIC timer interrupts.
[   30.052276] result 12696879
[   30.052278] Detected 12.696 MHz APIC timer.
[   30.055345] SMP alternatives: switching to SMP code
[   30.055432] Booting processor 1/2 APIC 0x1
[   30.065764] Initializing CPU#1
[   30.143222] Calibrating delay using timer specific routine.. 4875.61 BogoMIPS (lpj=9751233)
[   30.143227] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   30.143229] CPU: L2 Cache: 512K (64 bytes/line)
[   30.143231] CPU 1/1 -> Node 0
[   30.143233] CPU: Physical Processor ID: 0
[   30.143234] CPU: Processor Core ID: 1
[   30.143297] AMD Athlon(tm) 64 X2 Dual Core Processor 4600+ stepping 02
[   30.147233] CPU 1: Syncing TSC to CPU 0.
[   30.147238] CPU 1: synchronized TSC with CPU 0 (last diff 1 cycles, maxerr 525 cycles)
[   30.147246] Brought up 2 CPUs
[   30.147299] Disabling vsyscall due to use of PM timer
[   30.147301] time.c: Using 3.579545 MHz WALL PM GTOD PM timer.
[   30.147303] time.c: Detected 2437.798 MHz processor.
[   30.717478] migration_cost=140
[   30.717773] Time: 11:37:46  Date: 07/11/107
[   30.717803] NET: Registered protocol family 16
[   30.717867] ACPI: bus type pci registered
[   30.717872] PCI: Using configuration type 1
[   30.725297] ACPI: Interpreter enabled
[   30.725299] ACPI: Using IOAPIC for interrupt routing
[   30.726314] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   30.726318] PCI: Probing PCI hardware (bus 00)
[   30.727621] Boot video device is 0000:06:00.0
[   30.728206] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   30.750080] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[   30.750328] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.NBPG._PRT]
[   30.750573] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.NBP0._PRT]
[   30.750819] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.NBP1._PRT]
[   30.751065] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.NBP2._PRT]
[   30.751183] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.NBP3._PRT]
[   30.756697] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P7._PRT]
[   30.757030] ACPI: PCI Root Bridge [PCI1] (0000:80)
[   30.757034] PCI: Probing PCI hardware (bus 80)
[   30.759169] ACPI: PCI Interrupt Routing Table [\_SB_.PCI1._PRT]
[   30.759536] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[   30.759738] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[   30.759941] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[   30.760140] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 *6 7 10 11 12 14 15)
[   30.760391] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   30.760595] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   30.760798] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   30.761005] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[   30.761074] Linux Plug and Play Support v0.97 (c) Adam Belay
[   30.761081] pnp: PnP ACPI init
[   30.765067] pnp: PnP ACPI: found 14 devices
[   30.765122] PCI: Using ACPI for IRQ routing
[   30.765124] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   30.765231] NET: Registered protocol family 8
[   30.765232] NET: Registered protocol family 20
[   30.766067] PCI: Bridge: 0000:00:01.0
[   30.766068]   IO window: disabled.
[   30.766072]   MEM window: disabled.
[   30.766075]   PREFETCH window: disabled.
[   30.766079] PCI: Bridge: 0000:00:02.0
[   30.766081]   IO window: e000-efff
[   30.766085]   MEM window: fc000000-febfffff
[   30.766088]   PREFETCH window: d0000000-dfffffff
[   30.766092] PCI: Bridge: 0000:00:03.0
[   30.766093]   IO window: disabled.
[   30.766097]   MEM window: disabled.
[   30.766100]   PREFETCH window: cff00000-cfffffff
[   30.766105] PCI: Bridge: 0000:00:03.1
[   30.766106]   IO window: disabled.
[   30.766110]   MEM window: disabled.
[   30.766113]   PREFETCH window: cfe00000-cfefffff
[   30.766117] PCI: Bridge: 0000:00:03.2
[   30.766120]   IO window: d000-dfff
[   30.766124]   MEM window: fbf00000-fbffffff
[   30.766128]   PREFETCH window: disabled.
[   30.766132] PCI: Bridge: 0000:00:03.3
[   30.766134]   IO window: c000-cfff
[   30.766139]   MEM window: fbe00000-fbefffff
[   30.766142]   PREFETCH window: disabled.
[   30.766158] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   30.766171] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 27 (level, low) -> IRQ 27
[   30.766175] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   30.766187] ACPI: PCI Interrupt 0000:00:03.0[A] -> GSI 31 (level, low) -> IRQ 31
[   30.766192] PCI: Setting latency timer of device 0000:00:03.0 to 64
[   30.766205] ACPI: PCI Interrupt 0000:00:03.1[B] -> GSI 35 (level, low) -> IRQ 35
[   30.766209] PCI: Setting latency timer of device 0000:00:03.1 to 64
[   30.766222] ACPI: PCI Interrupt 0000:00:03.2[C] -> GSI 39 (level, low) -> IRQ 39
[   30.766226] PCI: Setting latency timer of device 0000:00:03.2 to 64
[   30.766239] ACPI: PCI Interrupt 0000:00:03.3[D] -> GSI 43 (level, low) -> IRQ 43
[   30.766244] PCI: Setting latency timer of device 0000:00:03.3 to 64
[   30.766328] NET: Registered protocol family 2
[   30.807138] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
[   30.807409] TCP established hash table entries: 262144 (order: 10, 4194304 bytes)
[   30.808852] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   30.809206] TCP: Hash tables configured (established 262144 bind 65536)
[   30.809209] TCP reno registered
[   30.819182] checking if image is initramfs... it is
[   31.356199] Freeing initrd memory: 6829k freed
[   31.359269] audit: initializing netlink socket (disabled)
[   31.359283] audit(1186832266.700:1): initialized
[   31.359450] VFS: Disk quotas dquot_6.5.1
[   31.359468] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   31.359511] io scheduler noop registered
[   31.359513] io scheduler anticipatory registered
[   31.359515] io scheduler deadline registered
[   31.359526] io scheduler cfq registered (default)
[   31.359784] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   31.359815] assign_interrupt_mode Found MSI capability
[   31.359818] Allocate Port Service[0000:00:02.0:pcie00]
[   31.359844] Allocate Port Service[0000:00:02.0:pcie02]
[   31.359923] PCI: Setting latency timer of device 0000:00:03.0 to 64
[   31.359960] assign_interrupt_mode Found MSI capability
[   31.359962] Allocate Port Service[0000:00:03.0:pcie00]
[   31.359984] Allocate Port Service[0000:00:03.0:pcie02]
[   31.360071] PCI: Setting latency timer of device 0000:00:03.1 to 64
[   31.360108] assign_interrupt_mode Found MSI capability
[   31.360111] Allocate Port Service[0000:00:03.1:pcie00]
[   31.360133] Allocate Port Service[0000:00:03.1:pcie02]
[   31.360220] PCI: Setting latency timer of device 0000:00:03.2 to 64
[   31.360257] assign_interrupt_mode Found MSI capability
[   31.360259] Allocate Port Service[0000:00:03.2:pcie00]
[   31.360281] Allocate Port Service[0000:00:03.2:pcie02]
[   31.360366] PCI: Setting latency timer of device 0000:00:03.3 to 64
[   31.360403] assign_interrupt_mode Found MSI capability
[   31.360405] Allocate Port Service[0000:00:03.3:pcie00]
[   31.360430] Allocate Port Service[0000:00:03.3:pcie02]
[   31.379120] Real Time Clock Driver v1.12ac
[   31.379155] Linux agpgart interface v0.102 (c) Dave Jones
[   31.379157] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   31.379262] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   31.379394] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[   31.379787] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   31.379949] mice: PS/2 mouse device common for all mice
[   31.380381] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   31.380493] input: Macintosh mouse button emulation as /class/input/input0
[   31.380519] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   31.380523] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   31.380775] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[   31.380777] PNP: PS/2 controller doesn't have AUX irq; using default 12
[   31.381106] serio: i8042 KBD port at 0x60,0x64 irq 1
[   31.381110] serio: i8042 AUX port at 0x60,0x64 irq 12
[   31.381177] TCP cubic registered
[   31.381185] NET: Registered protocol family 1
[   31.381260] ACPI: (supports S0 S1 S3 S4 S5)
[   31.381293]   Magic number: 3:584:630
[   31.381394] drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   31.381455] Freeing unused kernel memory: 304k freed
[   31.400198] input: AT Translated Set 2 keyboard as /class/input/input1
[   32.544063] Capability LSM initialized
[   32.935104] SCSI subsystem initialized
[   32.956090] libata version 2.20 loaded.
[   32.956175] usbcore: registered new interface driver usbfs
[   32.956192] usbcore: registered new interface driver hub
[   32.956211] usbcore: registered new device driver usb
[   32.956950] USB Universal Host Controller Interface driver v3.0
[   32.957000] ACPI: PCI Interrupt 0000:00:10.0[A] -> GSI 20 (level, low) -> IRQ 20
[   32.957009] uhci_hcd 0000:00:10.0: UHCI Host Controller
[   32.957104] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 1
[   32.957129] uhci_hcd 0000:00:10.0: irq 20, io base 0x0000a480
[   32.957223] usb usb1: configuration #1 chosen from 1 choice
[   32.957243] hub 1-0:1.0: USB hub found
[   32.957248] hub 1-0:1.0: 2 ports detected
[   33.062923] ACPI: PCI Interrupt 0000:00:10.1[B] -> GSI 22 (level, low) -> IRQ 22
[   33.062933] uhci_hcd 0000:00:10.1: UHCI Host Controller
[   33.062951] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 2
[   33.062976] uhci_hcd 0000:00:10.1: irq 22, io base 0x0000a800
[   33.063051] usb usb2: configuration #1 chosen from 1 choice
[   33.063069] hub 2-0:1.0: USB hub found
[   33.063074] hub 2-0:1.0: 2 ports detected
[   33.170864] ACPI: PCI Interrupt 0000:00:10.2[C] -> GSI 21 (level, low) -> IRQ 21
[   33.170873] uhci_hcd 0000:00:10.2: UHCI Host Controller
[   33.170890] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 3
[   33.170912] uhci_hcd 0000:00:10.2: irq 21, io base 0x0000a880
[   33.170981] usb usb3: configuration #1 chosen from 1 choice
[   33.171000] hub 3-0:1.0: USB hub found
[   33.171004] hub 3-0:1.0: 2 ports detected
[   33.278849] ACPI: PCI Interrupt 0000:00:10.3[D] -> GSI 23 (level, low) -> IRQ 23
[   33.278856] uhci_hcd 0000:00:10.3: UHCI Host Controller
[   33.278874] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 4
[   33.278895] uhci_hcd 0000:00:10.3: irq 23, io base 0x0000ac00
[   33.278961] usb usb4: configuration #1 chosen from 1 choice
[   33.278978] hub 4-0:1.0: USB hub found
[   33.278983] hub 4-0:1.0: 2 ports detected
[   33.306773] usb 1-1: new full speed USB device using uhci_hcd and address 2
[   33.386891] r8169 Gigabit Ethernet driver 2.2LK loaded
[   33.386918] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 36 (level, low) -> IRQ 36
[   33.386940] PCI: Setting latency timer of device 0000:03:00.0 to 64
[   33.387112] eth0: RTL8168b/8111b at 0xffffc20000004000, 00:19:66:00:a3:5e, IRQ 36
[   33.393663] ACPI: PCI Interrupt 0000:00:10.4[C] -> GSI 21 (level, low) -> IRQ 21
[   33.393678] ehci_hcd 0000:00:10.4: EHCI Host Controller
[   33.393697] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 5
[   33.393730] ehci_hcd 0000:00:10.4: irq 21, io mem 0xfbdffc00
[   33.393737] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   33.393808] usb usb5: configuration #1 chosen from 1 choice
[   33.393831] hub 5-0:1.0: USB hub found
[   33.393837] hub 5-0:1.0: 8 ports detected
[   33.498920] ahci 0000:02:00.0: version 2.1
[   33.498945] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 40 (level, low) -> IRQ 40
[   33.842700] usb 1-1: device not accepting address 2, error -71
[   34.506646] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   34.506656] ahci 0000:02:00.0: AHCI 0001.0000 32 slots 2 ports 3 Gbps 0x3 impl SATA mode
[   34.506659] ahci 0000:02:00.0: flags: 64bit ncq pm led clo pmp pio slum part 
[   34.506743] ata1: SATA max UDMA/133 cmd 0xffffc2000001c100 ctl 0x0000000000000000 bmdma 0x0000000000000000 irq 40
[   34.506805] ata2: SATA max UDMA/133 cmd 0xffffc2000001c180 ctl 0x0000000000000000 bmdma 0x0000000000000000 irq 40
[   34.506814] scsi0 : ahci
[   34.994570] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   34.995412] ata1.00: ata_hpa_resize 1: sectors = 321672960, hpa_sectors = 321672960
[   34.995417] ata1.00: ATA-7: Hitachi HCS721616PLA380, P22OAB3A, max UDMA/133
[   34.995419] ata1.00: 321672960 sectors, multi 16: LBA48 NCQ (depth 31/32)
[   34.996410] ata1.00: ata_hpa_resize 1: sectors = 321672960, hpa_sectors = 321672960
[   34.996414] ata1.00: configured for UDMA/133
[   34.996421] scsi1 : ahci
[   35.310517] ata2: SATA link down (SStatus 0 SControl 300)
[   35.310597] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HCS72161 P22O PQ: 0 ANSI: 5
[   35.312304] VP_IDE: IDE controller at PCI slot 0000:00:0f.1
[   35.312326] VP_IDE: chipset revision 7
[   35.312328] VP_IDE: not 100% native mode: will probe irqs later
[   35.312339] VP_IDE: VIA vt8237a (rev 00) IDE UDMA133 controller on pci0000:00:0f.1
[   35.312345]     ide0: BM-DMA at 0xfc00-0xfc07, BIOS settings: hda:DMA, hdb:pio
[   35.312355]     ide1: BM-DMA at 0xfc08-0xfc0f, BIOS settings: hdc:pio, hdd:pio
[   35.312361] Probing IDE interface ide0...
[   35.330567] SCSI device sda: 321672960 512-byte hdwr sectors (164697 MB)
[   35.334542] sda: Write Protect is off
[   35.334545] sda: Mode Sense: 00 3a 00 00
[   35.338564] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   35.339052] SCSI device sda: 321672960 512-byte hdwr sectors (164697 MB)
[   35.339066] sda: Write Protect is off
[   35.339067] sda: Mode Sense: 00 3a 00 00
[   35.340579] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   35.340586]  sda: sda1 sda2
[   35.396965] sd 0:0:0:0: Attached scsi disk sda
[   35.399865] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   35.414526] usb 1-1: new full speed USB device using uhci_hcd and address 4
[   35.582587] Attempting manual resume
[   35.582590] swsusp: Resume From Partition 8:2
[   35.582591] PM: Checking swsusp image.
[   35.582729] PM: Resume from disk failed.
[   35.594336] usb 1-1: configuration #1 chosen from 1 choice
[   35.627278] kjournald starting.  Commit interval 5 seconds
[   35.627289] EXT3-fs: mounted filesystem with ordered data mode.
[   35.838453] usb 1-2: new full speed USB device using uhci_hcd and address 5
[   36.027178] usb 1-2: configuration #1 chosen from 1 choice
[   36.182522] hda: PHILIPS PBDV1640P, ATAPI CD/DVD-ROM drive
[   36.859308] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   36.860754] Probing IDE interface ide1...
[   37.430373] sata_via 0000:00:0f.0: version 2.1
[   37.430391] ACPI: PCI Interrupt 0000:00:0f.0[B] -> GSI 21 (level, low) -> IRQ 21
[   37.430407] sata_via 0000:00:0f.0: routed to hard irq line 11
[   37.430453] ata3: SATA max UDMA/133 cmd 0x000000000001bc00 ctl 0x000000000001b882 bmdma 0x000000000001b400 irq 21
[   37.430477] ata4: SATA max UDMA/133 cmd 0x000000000001b800 ctl 0x000000000001b482 bmdma 0x000000000001b408 irq 21
[   37.430486] scsi2 : sata_via
[   37.638216] ata3: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[   37.648941] ATA: abnormal status 0x7F on port 0x000000000001bc07
[   37.648960] scsi3 : sata_via
[   37.854193] ata4: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[   37.864918] ATA: abnormal status 0x7F on port 0x000000000001b807
[   37.865684] PCI: Enabling device 0000:02:00.1 (0000 -> 0001)
[   37.865694] ACPI: PCI Interrupt 0000:02:00.1[B] -> GSI 41 (level, low) -> IRQ 41
[   37.865713] PCI: Setting latency timer of device 0000:02:00.1 to 64
[   37.865755] ata5: PATA max UDMA/100 cmd 0x000000000001cc00 ctl 0x000000000001c882 bmdma 0x000000000001c400 irq 41
[   37.865779] ata6: PATA max UDMA/100 cmd 0x000000000001c800 ctl 0x000000000001c482 bmdma 0x000000000001c408 irq 41
[   37.865794] scsi4 : pata_jmicron
[   38.022229] scsi5 : pata_jmicron
[   38.193260] ATA: abnormal status 0x7F on port 0x000000000001c807
[   42.524791] r8169: eth0: link up
[   42.524780] r8169: eth0: link up
[   43.957007] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   44.092369] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   44.107120] input: PC Speaker as /class/input/input2
[   44.204049] NET: Registered protocol family 17
[   44.267727] hda: ATAPI 40X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(33)
[   44.267733] Uniform CD-ROM driver Revision: 3.20
[   44.323378] usbcore: registered new interface driver hiddev
[   44.339508] parport: PnPBIOS parport detected.
[   44.339552] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   44.398424] irda_init()
[   44.398443] NET: Registered protocol family 23
[   44.424459] input: Razer Razer Copperhead Laser Mouse as /class/input/input3
[   44.424529] input: USB HID v10.01 Mouse [Razer Razer Copperhead Laser Mouse] on usb-0000:00:10.0-2
[   44.427472] input: Razer Razer Copperhead Laser Mouse as /class/input/input4
[   44.427503] input: USB HID v10.01 Keyboard [Razer Razer Copperhead Laser Mouse] on usb-0000:00:10.0-2
[   44.427511] usbcore: registered new interface driver usbhid
[   44.427514] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[   44.691912] nvidia: module license 'NVIDIA' taints kernel.
[   44.946688] ACPI: PCI Interrupt 0000:06:00.0[A] -> GSI 24 (level, low) -> IRQ 24
[   44.946697] PCI: Setting latency timer of device 0000:06:00.0 to 64
[   44.946814] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  100.14.11  Wed Jun 13 16:33:22 PDT 2007
[   45.097086] ACPI: PCI Interrupt 0000:00:09.0[A] -> GSI 16 (level, low) -> IRQ 16
[   45.234532] fuse init (API version 7.8)
[   45.263214] lp0: using parport0 (interrupt-driven).
[   45.301957] Adding 514072k swap on /dev/disk/by-uuid/01c688cb-2707-4544-b43d-3e730dec9d0e.  Priority:-1 extents:1 across:514072k
[   45.430209] EXT3 FS on sda1, internal journal
[   52.601684] ibm_acpi: ec object not found
[   52.667859] Using specific hotkey driver
[   52.776861] input: Power Button (FF) as /class/input/input5
[   52.777074] ACPI: Power Button (FF) [PWRF]
[   52.777998] input: Power Button (CM) as /class/input/input6
[   52.778183] ACPI: Power Button (CM) [PWRB]
[   52.800750] No dock devices found.
[   52.833303] pcc_acpi: loading...
[   57.369292] ppdev: user-space parallel port driver

```

As far as the ATA abnormal error goes, googling around it seems it's an issue with the drive and the controller. How I fix it I have no idea.

Also, not sure what pcc is or how I remove it if I don't need it?

---

### Post by sab0403 on 2007-08-14
Aha! Got an update on the weirdness that is this OS.

After extensive testing (actually, a casual but lucky observation), I've discovered that Ubuntu indeed got blazing fast to boot... when unplugged. Yup. Apparently if I unplug everything (basically power and a little usb mouse I use) the PC boots in about 24 seconds flat. If I keep the mouse plugged in, about 36-38 seconds. If I keep power (but no mouse) in, all the way to 1:30. Both, 1:36-1:40. All times to boot from the GRUB menu to the logon screen.

Anyway, maybe someone will get *something* out of this. For now, I'm just booting like Bon Jovi should never play - unplugged! :guitar:

:popcorn:

---

### Post by K.Mandla on 2007-08-14
> **sab0403 said:**
> is there any way to make the GUI start automatically?
> you can also run startx at startup using
```

if [ -z "$DISPLAY" ] && [ $(tty) == /dev/tty1 ]; then
       startx
fi
```
in your .bash_profile file
> **sab0403 said:**
> Apparently if I unplug everything (basically power and a little usb mouse I use) the PC boots in about 24 seconds flat. If I keep the mouse plugged in, about 36-38 seconds. If I keep power (but no mouse) in, all the way to 1:30. Both, 1:36-1:40. All times to boot from the GRUB menu to the logon screen.
This is a little self-aggrandizing, but if you'd like a collection of ideas on how to speed up Feisty, you might look at [this guide]("http://kmandla.wordpress.com/2007/04/22/howto-set-up-feisty-for-speed/").

You should be able to knock down your boot time quite a bit, depending on how lean you're willing to make your system. I've pushed 300Mhz machines to sub-35-second boots with some of those ideas.

And if you're willing to experiment with different distros, you'll probably find that a lot of them can be quite a bit faster than Ubuntu.

---

### Post by sab0403 on 2007-08-15
I'm going to give it a look. Thanks!

Don't you agree this is weird, though? Though there obviously is some rationale behind it... I can't see it. In a related story, the processor load is much heavier when connected to the power compared to when it's not. Right now I'm unplugged from power, and I have an average of 12% load - using Beryl, with Firefox open (and the NFS service up). If I plug it in, it jumps up to 60% average, with the corresponding shift in frequency - the ondemand governor is working fine, the load just gets crazy!

So it isn't just about speed, it's about speed/power management. And I think, given that the boot times are that separated when plugged and unplugged, that it's all related. So it probably boils down to how Ubuntu (or Feisty, haven't really tried any other version) handles the Pentium M (or mobiles in general).

Interesting stuff, though.

---

### Post by _simon_ on 2007-08-21
After a fresh install of Gutsy, my ATA abnormal error has gone :)

```

[    0.000000] Linux version 2.6.22-9-generic (buildd@yellow) (gcc version 4.1.3 20070718 (prerelease) (Ubuntu 4.1.2-14ubuntu1)) #1 SMP Fri Aug 3 00:20:35 GMT 2007 (Ubuntu 2.6.22-9.25-generic)
[    0.000000] Command line: root=UUID=25c1537a-1cea-4fc9-8830-1ca99cceeeda ro quiet splash
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000e4000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000007ffb0000 (usable)
[    0.000000]  BIOS-e820: 000000007ffb0000 - 000000007ffc0000 (ACPI data)
[    0.000000]  BIOS-e820: 000000007ffc0000 - 000000007fff0000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007fff0000 - 0000000080000000 (reserved)
[    0.000000]  BIOS-e820: 00000000e0000000 - 00000000f0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[    0.000000]  BIOS-e820: 00000000fecc0000 - 00000000fecc1000 (reserved)
[    0.000000]  BIOS-e820: 00000000ff380000 - 0000000100000000 (reserved)
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 524208) 1 entries of 3200 used
[    0.000000] end_pfn_map = 1048576
[    0.000000] DMI present.
[    0.000000] ACPI: RSDP 000F8E40, 0014 (r0 ACPIAM)
[    0.000000] ACPI: RSDT 7FFB0000, 0034 (r1 A M I  OEMRSDT  12000620 MSFT       97)
[    0.000000] ACPI: FACP 7FFB0200, 0084 (r2 A M I  OEMFACP  12000620 MSFT       97)
[    0.000000] ACPI: DSDT 7FFB0440, 4675 (r1  AS2GL AS2GL000        0 INTL  2002026)
[    0.000000] ACPI: FACS 7FFC0000, 0040
[    0.000000] ACPI: APIC 7FFB0390, 0068 (r1 A M I  OEMAPIC  12000620 MSFT       97)
[    0.000000] ACPI: MCFG 7FFB0400, 003C (r1 A M I  OEMMCFG  12000620 MSFT       97)
[    0.000000] ACPI: OEMB 7FFC0040, 0050 (r1 A M I  AMI_OEM  12000620 MSFT       97)
[    0.000000] Scanning NUMA topology in Northbridge 24
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-000000007ffb0000
[    0.000000] Entering add_active_range(0, 0, 159) 0 entries of 3200 used
[    0.000000] Entering add_active_range(0, 256, 524208) 1 entries of 3200 used
[    0.000000] Bootmem setup node 0 0000000000000000-000000007ffb0000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->     4096
[    0.000000]   DMA32        4096 ->  1048576
[    0.000000]   Normal    1048576 ->  1048576
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0:        0 ->      159
[    0.000000]     0:      256 ->   524208
[    0.000000] On node 0 totalpages: 524111
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 1125 pages reserved
[    0.000000]   DMA zone: 2818 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 7110 pages used for memmap
[    0.000000]   DMA32 zone: 513002 pages, LIFO batch:31
[    0.000000]   Normal zone: 0 pages used for memmap
[    0.000000] ACPI: PM-Timer IO Port: 0x808
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] Processor #0 (Bootup-CPU)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] Processor #1
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: IOAPIC (id[0x03] address[0xfecc0000] gsi_base[24])
[    0.000000] IOAPIC[1]: apic_id 3, address 0xfecc0000, GSI 24-47
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 low level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Setting APIC routing to flat
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] swsusp: Registered nosave memory region: 000000000009f000 - 00000000000a0000
[    0.000000] swsusp: Registered nosave memory region: 00000000000a0000 - 00000000000e4000
[    0.000000] swsusp: Registered nosave memory region: 00000000000e4000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 88000000 (gap: 80000000:60000000)
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] PERCPU: Allocating 34696 bytes of per cpu data
[    0.000000] Built 1 zonelists.  Total pages: 515820
[    0.000000] Kernel command line: root=UUID=25c1537a-1cea-4fc9-8830-1ca99cceeeda ro quiet splash
[    0.000000] Initializing CPU#0
[    0.000000] PID hash table entries: 4096 (order: 12, 32768 bytes)
[    0.000000] Marking TSC unstable due to TSCs unsynchronized
[   30.511211] time.c: Detected 2437.798 MHz processor.
[   30.512690] Console: colour VGA+ 80x25
[   30.512703] Checking aperture...
[   30.512706] CPU 0: aperture @ 1002000000 size 32 MB
[   30.512707] Aperture too small (32 MB)
[   30.520745] No AGP bridge found
[   30.534158] Memory: 2055892k/2096832k available (2271k kernel code, 40552k reserved, 1180k data, 300k init)
[   30.534193] SLUB: Genslabs=23, HWalign=64, Order=0-1, MinObjects=4, CPUs=2, Nodes=1
[   30.613191] Calibrating delay using timer specific routine.. 4878.21 BogoMIPS (lpj=9756437)
[   30.613215] Security Framework v1.0.0 initialized
[   30.613220] SELinux:  Disabled at boot.
[   30.613347] Dentry cache hash table entries: 262144 (order: 9, 2097152 bytes)
[   30.614195] Inode-cache hash table entries: 131072 (order: 8, 1048576 bytes)
[   30.614592] Mount-cache hash table entries: 256
[   30.614690] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   30.614692] CPU: L2 Cache: 512K (64 bytes/line)
[   30.614694] CPU 0/0 -> Node 0
[   30.614696] CPU: Physical Processor ID: 0
[   30.614697] CPU: Processor Core ID: 0
[   30.614711] SMP alternatives: switching to UP code
[   30.614893] Early unpacking initramfs... done
[   30.851895] ACPI: Core revision 20070126
[   30.851940] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   30.894216] Using local APIC timer interrupts.
[   30.935234] result 12696854
[   30.935236] Detected 12.696 MHz APIC timer.
[   30.937213] SMP alternatives: switching to SMP code
[   30.937296] Booting processor 1/2 APIC 0x1
[   30.947463] Initializing CPU#1
[   31.025249] Calibrating delay using timer specific routine.. 4875.79 BogoMIPS (lpj=9751580)
[   31.025255] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[   31.025256] CPU: L2 Cache: 512K (64 bytes/line)
[   31.025258] CPU 1/1 -> Node 0
[   31.025260] CPU: Physical Processor ID: 0
[   31.025261] CPU: Processor Core ID: 1
[   31.025324] AMD Athlon(tm) 64 X2 Dual Core Processor 4600+ stepping 02
[   31.029157] Brought up 2 CPUs
[   31.601300] migration_cost=142
[   31.601338] NET: Registered protocol family 16
[   31.601402] ACPI: bus type pci registered
[   31.601407] PCI: Using configuration type 1
[   31.604363] ACPI: EC: Look up EC in DSDT
[   31.608581] ACPI: Interpreter enabled
[   31.608583] ACPI: (supports S0 S1 S3 S4 S5)
[   31.608600] ACPI: Using IOAPIC for interrupt routing
[   31.615956] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   31.615964] PCI: Probing PCI hardware (bus 00)
[   31.617652] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   31.617816] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[   31.617879] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.NBPG._PRT]
[   31.617945] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.NBP0._PRT]
[   31.618012] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.NBP1._PRT]
[   31.618079] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.NBP2._PRT]
[   31.618146] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.NBP3._PRT]
[   31.618230] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P7._PRT]
[   31.632586] ACPI: PCI Root Bridge [PCI1] (0000:80)
[   31.632593] PCI: Probing PCI hardware (bus 80)
[   31.632666] ACPI: PCI Interrupt Routing Table [\_SB_.PCI1._PRT]
[   31.632834] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[   31.632924] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 10 *11 12 14 15)
[   31.633011] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 *5 6 7 10 11 12 14 15)
[   31.633124] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 *6 7 10 11 12 14 15)
[   31.633210] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   31.633298] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   31.633387] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
[   31.633475] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *10 11 12 14 15)
[   31.633546] Linux Plug and Play Support v0.97 (c) Adam Belay
[   31.633557] pnp: PnP ACPI init
[   31.633564] ACPI: bus type pnp registered
[   31.636874] pnp: PnP ACPI: found 14 devices
[   31.636876] ACPI: ACPI bus type pnp unregistered
[   31.636920] PCI: Using ACPI for IRQ routing
[   31.636923] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[   31.637031] NET: Registered protocol family 8
[   31.637033] NET: Registered protocol family 20
[   31.637203] pnp: 00:07: iomem range 0xfffffff0-0xffffffff could not be reserved
[   31.637208] pnp: 00:08: iomem range 0xfec00000-0xfec00fff could not be reserved
[   31.637211] pnp: 00:08: iomem range 0xfee00000-0xfee00fff could not be reserved
[   31.637216] pnp: 00:0b: iomem range 0xe0000000-0xefffffff could not be reserved
[   31.637220] pnp: 00:0c: iomem range 0x0-0x9ffff could not be reserved
[   31.637222] pnp: 00:0c: iomem range 0xc0000-0xcffff has been reserved
[   31.637225] pnp: 00:0c: iomem range 0xe0000-0xfffff could not be reserved
[   31.637227] pnp: 00:0c: iomem range 0x100000-0x7fffffff could not be reserved
[   31.637479] PCI: Bridge: 0000:00:01.0
[   31.637480]   IO window: disabled.
[   31.637484]   MEM window: disabled.
[   31.637487]   PREFETCH window: disabled.
[   31.637491] PCI: Bridge: 0000:00:02.0
[   31.637493]   IO window: e000-efff
[   31.637497]   MEM window: fc000000-febfffff
[   31.637500]   PREFETCH window: d0000000-dfffffff
[   31.637504] PCI: Bridge: 0000:00:03.0
[   31.637505]   IO window: disabled.
[   31.637509]   MEM window: disabled.
[   31.637513]   PREFETCH window: cff00000-cfffffff
[   31.637517] PCI: Bridge: 0000:00:03.1
[   31.637518]   IO window: disabled.
[   31.637522]   MEM window: disabled.
[   31.637525]   PREFETCH window: cfe00000-cfefffff
[   31.637529] PCI: Bridge: 0000:00:03.2
[   31.637532]   IO window: d000-dfff
[   31.637536]   MEM window: fbf00000-fbffffff
[   31.637540]   PREFETCH window: disabled.
[   31.637544] PCI: Bridge: 0000:00:03.3
[   31.637546]   IO window: c000-cfff
[   31.637551]   MEM window: fbe00000-fbefffff
[   31.637554]   PREFETCH window: disabled.
[   31.637570] PCI: Setting latency timer of device 0000:00:01.0 to 64
[   31.637583] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 27 (level, low) -> IRQ 27
[   31.637587] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   31.637600] ACPI: PCI Interrupt 0000:00:03.0[A] -> GSI 31 (level, low) -> IRQ 31
[   31.637605] PCI: Setting latency timer of device 0000:00:03.0 to 64
[   31.637617] ACPI: PCI Interrupt 0000:00:03.1[B] -> GSI 35 (level, low) -> IRQ 35
[   31.637622] PCI: Setting latency timer of device 0000:00:03.1 to 64
[   31.637635] ACPI: PCI Interrupt 0000:00:03.2[C] -> GSI 39 (level, low) -> IRQ 39
[   31.637639] PCI: Setting latency timer of device 0000:00:03.2 to 64
[   31.637652] ACPI: PCI Interrupt 0000:00:03.3[D] -> GSI 43 (level, low) -> IRQ 43
[   31.637656] PCI: Setting latency timer of device 0000:00:03.3 to 64
[   31.637715] NET: Registered protocol family 2
[   31.641180] Time: acpi_pm clocksource has been installed.
[   31.685125] IP route cache hash table entries: 65536 (order: 7, 524288 bytes)
[   31.685716] TCP established hash table entries: 262144 (order: 10, 6291456 bytes)
[   31.687956] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[   31.688355] TCP: Hash tables configured (established 262144 bind 65536)
[   31.688358] TCP reno registered
[   31.697167] checking if image is initramfs... it is
[   32.161719] Freeing initrd memory: 7184k freed
[   32.165101] audit: initializing netlink socket (disabled)
[   32.165113] audit(1187730365.616:1): initialized
[   32.166697] VFS: Disk quotas dquot_6.5.1
[   32.166738] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[   32.166812] io scheduler noop registered
[   32.166814] io scheduler anticipatory registered
[   32.166815] io scheduler deadline registered
[   32.166885] io scheduler cfq registered (default)
[   32.166888] PCI: MSI quirk detected. MSI deactivated.
[   32.166895] PCI: VIA PCI bridge detected. Disabling DAC.
[   32.167265] Boot video device is 0000:06:00.0
[   32.167388] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   32.167419] assign_interrupt_mode Found MSI capability
[   32.167421] Allocate Port Service[0000:00:02.0:pcie00]
[   32.167452] Allocate Port Service[0000:00:02.0:pcie02]
[   32.167516] PCI: Setting latency timer of device 0000:00:03.0 to 64
[   32.167553] assign_interrupt_mode Found MSI capability
[   32.167555] Allocate Port Service[0000:00:03.0:pcie00]
[   32.167576] Allocate Port Service[0000:00:03.0:pcie02]
[   32.167646] PCI: Setting latency timer of device 0000:00:03.1 to 64
[   32.167683] assign_interrupt_mode Found MSI capability
[   32.167685] Allocate Port Service[0000:00:03.1:pcie00]
[   32.167709] Allocate Port Service[0000:00:03.1:pcie02]
[   32.167777] PCI: Setting latency timer of device 0000:00:03.2 to 64
[   32.167814] assign_interrupt_mode Found MSI capability
[   32.167816] Allocate Port Service[0000:00:03.2:pcie00]
[   32.167840] Allocate Port Service[0000:00:03.2:pcie02]
[   32.167910] PCI: Setting latency timer of device 0000:00:03.3 to 64
[   32.167947] assign_interrupt_mode Found MSI capability
[   32.167949] Allocate Port Service[0000:00:03.3:pcie00]
[   32.167972] Allocate Port Service[0000:00:03.3:pcie02]
[   32.186755] Real Time Clock Driver v1.12ac
[   32.186825] Linux agpgart interface v0.102 (c) Dave Jones
[   32.186828] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[   32.187325] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[   32.187872] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[   32.187970] input: Macintosh mouse button emulation as /class/input/input0
[   32.188022] PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[   32.188025] PNP: PS/2 controller doesn't have AUX irq; using default 12
[   32.188339] serio: i8042 KBD port at 0x60,0x64 irq 1
[   32.188343] serio: i8042 AUX port at 0x60,0x64 irq 12
[   32.188424] mice: PS/2 mouse device common for all mice
[   32.188521] TCP cubic registered
[   32.188571] NET: Registered protocol family 1
[   32.188750] /build/buildd/linux-source-2.6.22-2.6.22/drivers/rtc/hctosys.c: unable to open rtc device (rtc0)
[   32.188756] Freeing unused kernel memory: 300k freed
[   32.237388] input: AT Translated Set 2 keyboard as /class/input/input1
[   33.338924] AppArmor: AppArmor initialized
[   33.338933] audit(1187730366.792:2): AppArmor initialized
[   33.338934] 
[   33.341949] AppArmor: Registered secondary security module: capability.
[   33.341953] Capability LSM initialized as secondary
[   33.763278] SCSI subsystem initialized
[   33.767257] libata version 2.21 loaded.
[   33.769861] sata_via 0000:00:0f.0: version 2.2
[   33.769882] ACPI: PCI Interrupt 0000:00:0f.0[B] -> GSI 21 (level, low) -> IRQ 21
[   33.769912] sata_via 0000:00:0f.0: routed to hard irq line 11
[   33.769998] scsi0 : sata_via
[   33.770038] scsi1 : sata_via
[   33.770062] ata1: SATA max UDMA/133 cmd 0x000000000001bc00 ctl 0x000000000001b882 bmdma 0x000000000001b400 irq 21
[   33.770065] ata2: SATA max UDMA/133 cmd 0x000000000001b800 ctl 0x000000000001b482 bmdma 0x000000000001b408 irq 21
[   33.789141] usbcore: registered new interface driver usbfs
[   33.789162] usbcore: registered new interface driver hub
[   33.808989] usbcore: registered new device driver usb
[   33.824753] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[   33.824758] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   33.826002] USB Universal Host Controller Interface driver v3.0
[   33.976783] ata1: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[   34.192756] ata2: SATA link down 1.5 Gbps (SStatus 0 SControl 300)
[   34.203687] ahci 0000:02:00.0: version 2.2
[   34.203713] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 40 (level, low) -> IRQ 40
[   34.203868] PCI: Disallowing DAC for device 0000:02:00.0
[   34.203989] ACPI: PCI Interrupt 0000:00:10.4[C] -> GSI 21 (level, low) -> IRQ 21
[   34.204094] ehci_hcd 0000:00:10.4: EHCI Host Controller
[   34.204391] ehci_hcd 0000:00:10.4: new USB bus registered, assigned bus number 1
[   34.204425] ehci_hcd 0000:00:10.4: irq 21, io mem 0xfbdffc00
[   34.204433] ehci_hcd 0000:00:10.4: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[   34.204757] usb usb1: configuration #1 chosen from 1 choice
[   34.204893] hub 1-0:1.0: USB hub found
[   34.204898] hub 1-0:1.0: 8 ports detected
[   35.208642] ahci 0000:02:00.0: AHCI 0001.0000 32 slots 2 ports 3 Gbps 0x3 impl SATA mode
[   35.208646] ahci 0000:02:00.0: flags: 64bit ncq pm led clo pmp pio slum part 
[   35.208652] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   35.208773] scsi2 : ahci
[   35.208829] scsi3 : ahci
[   35.208853] ata3: SATA max UDMA/133 cmd 0xffffc20000aa4100 ctl 0x0000000000000000 bmdma 0x0000000000000000 irq 40
[   35.208857] ata4: SATA max UDMA/133 cmd 0xffffc20000aa4180 ctl 0x0000000000000000 bmdma 0x0000000000000000 irq 40
[   35.696674] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   35.697531] ata3.00: ATA-7: Hitachi HCS721616PLA380, P22OAB3A, max UDMA/133
[   35.697534] ata3.00: 321672960 sectors, multi 16: LBA48 NCQ (depth 31/32)
[   35.698538] ata3.00: configured for UDMA/133
[   36.012631] ata4: SATA link down (SStatus 0 SControl 300)
[   36.012731] scsi 2:0:0:0: Direct-Access     ATA      Hitachi HCS72161 P22O PQ: 0 ANSI: 5
[   36.013427] VP_IDE: IDE controller at PCI slot 0000:00:0f.1
[   36.013449] VP_IDE: chipset revision 7
[   36.013450] VP_IDE: not 100% native mode: will probe irqs later
[   36.013461] VP_IDE: VIA vt8237a (rev 00) IDE UDMA133 controller on pci0000:00:0f.1
[   36.013468]     ide0: BM-DMA at 0xfc00-0xfc07, BIOS settings: hda:DMA, hdb:pio
[   36.013478]     ide1: BM-DMA at 0xfc08-0xfc0f, BIOS settings: hdc:pio, hdd:pio
[   36.013483] Probing IDE interface ide0...
[   36.024526] sd 2:0:0:0: [sda] 321672960 512-byte hardware sectors (164697 MB)
[   36.024536] sd 2:0:0:0: [sda] Write Protect is off
[   36.024539] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   36.024549] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   36.024597] sd 2:0:0:0: [sda] 321672960 512-byte hardware sectors (164697 MB)
[   36.024603] sd 2:0:0:0: [sda] Write Protect is off
[   36.024605] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   36.024614] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   36.024618]  sda: sda1 sda2 sda3
[   36.085452] sd 2:0:0:0: [sda] Attached SCSI disk
[   36.088161] sd 2:0:0:0: Attached scsi generic sg0 type 0
[   36.360323] Attempting manual resume
[   36.360326] swsusp: Resume From Partition 8:2
[   36.360328] PM: Checking swsusp image.
[   36.360754] PM: Resume from disk failed.
[   36.406955] kjournald starting.  Commit interval 5 seconds
[   36.406970] EXT3-fs: mounted filesystem with ordered data mode.
[   36.884513] hda: PHILIPS PBDV1640P, ATAPI CD/DVD-ROM drive
[   37.561108] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[   37.562653] Probing IDE interface ide1...
[   38.132349] PCI: Enabling device 0000:02:00.1 (0000 -> 0001)
[   38.132358] ACPI: PCI Interrupt 0000:02:00.1[B] -> GSI 41 (level, low) -> IRQ 41
[   38.132395] PCI: Setting latency timer of device 0000:02:00.1 to 64
[   38.132453] scsi4 : pata_jmicron
[   38.132509] scsi5 : pata_jmicron
[   38.132531] ata5: PATA max UDMA/100 cmd 0x000000000001cc00 ctl 0x000000000001c882 bmdma 0x000000000001c400 irq 41
[   38.132534] ata6: PATA max UDMA/100 cmd 0x000000000001c800 ctl 0x000000000001c482 bmdma 0x000000000001c408 irq 41
[   38.463420] ACPI: PCI Interrupt 0000:00:10.0[A] -> GSI 20 (level, low) -> IRQ 20
[   38.463428] uhci_hcd 0000:00:10.0: UHCI Host Controller
[   38.463450] uhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 2
[   38.463473] uhci_hcd 0000:00:10.0: irq 20, io base 0x0000a480
[   38.463561] usb usb2: configuration #1 chosen from 1 choice
[   38.463580] hub 2-0:1.0: USB hub found
[   38.463586] hub 2-0:1.0: 2 ports detected
[   38.568251] ACPI: PCI Interrupt 0000:00:10.1[B] -> GSI 22 (level, low) -> IRQ 22
[   38.568257] uhci_hcd 0000:00:10.1: UHCI Host Controller
[   38.568272] uhci_hcd 0000:00:10.1: new USB bus registered, assigned bus number 3
[   38.568292] uhci_hcd 0000:00:10.1: irq 22, io base 0x0000a800
[   38.568363] usb usb3: configuration #1 chosen from 1 choice
[   38.568382] hub 3-0:1.0: USB hub found
[   38.568386] hub 3-0:1.0: 2 ports detected
[   38.676225] ACPI: PCI Interrupt 0000:00:10.2[C] -> GSI 21 (level, low) -> IRQ 21
[   38.676231] uhci_hcd 0000:00:10.2: UHCI Host Controller
[   38.676246] uhci_hcd 0000:00:10.2: new USB bus registered, assigned bus number 4
[   38.676264] uhci_hcd 0000:00:10.2: irq 21, io base 0x0000a880
[   38.676332] usb usb4: configuration #1 chosen from 1 choice
[   38.676350] hub 4-0:1.0: USB hub found
[   38.676354] hub 4-0:1.0: 2 ports detected
[   38.784210] ACPI: PCI Interrupt 0000:00:10.3[D] -> GSI 23 (level, low) -> IRQ 23
[   38.784215] uhci_hcd 0000:00:10.3: UHCI Host Controller
[   38.784232] uhci_hcd 0000:00:10.3: new USB bus registered, assigned bus number 5
[   38.784252] uhci_hcd 0000:00:10.3: irq 23, io base 0x0000ac00
[   38.784320] usb usb5: configuration #1 chosen from 1 choice
[   38.784337] hub 5-0:1.0: USB hub found
[   38.784342] hub 5-0:1.0: 2 ports detected
[   38.808268] usb 2-1: new full speed USB device using uhci_hcd and address 2
[   38.892206] r8169 Gigabit Ethernet driver 2.2LK loaded
[   38.892226] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 36 (level, low) -> IRQ 36
[   38.892242] PCI: Disallowing DAC for device 0000:03:00.0
[   38.892248] PCI: Setting latency timer of device 0000:03:00.0 to 64
[   38.892419] eth0: RTL8168b/8111b at 0xffffc20000aa8000, 00:19:66:00:a3:5e, IRQ 36
[   38.987505] usb 2-1: configuration #1 chosen from 1 choice
[   39.232213] usb 2-2: new full speed USB device using uhci_hcd and address 3
[   39.420356] usb 2-2: configuration #1 chosen from 1 choice
[   42.357567] r8169: eth0: link up
[   42.357683] r8169: eth0: link up
[   43.278597] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   43.280109] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   43.491209] input: PC Speaker as /class/input/input2
[   43.622716] irda_init()
[   43.622734] NET: Registered protocol family 23
[   43.625845] parport_pc 00:06: reported by Plug and Play ACPI
[   43.625890] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   43.663186] nvidia: module license 'NVIDIA' taints kernel.
[   43.916645] ACPI: PCI Interrupt 0000:06:00.0[A] -> <6>NET: Registered protocol family 17
[   43.916651] GSI 24 (level, low) -> IRQ 24
[   43.916659] PCI: Setting latency timer of device 0000:06:00.0 to 64
[   43.916800] NVRM: loading NVIDIA Linux x86_64 Kernel Module  1.0-9631  Thu Nov  9 17:35:27 PST 2006
[   43.963161] usbcore: registered new interface driver hiddev
[   43.980821] hda: ATAPI 40X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(33)
[   43.980828] Uniform CD-ROM driver Revision: 3.20
[   44.017804] input: Razer Razer Copperhead Laser Mouse as /class/input/input3
[   44.017839] input: USB HID v10.01 Mouse [Razer Razer Copperhead Laser Mouse] on usb-0000:00:10.0-2
[   44.022643] input: Razer Razer Copperhead Laser Mouse as /class/input/input4
[   44.022677] input: USB HID v10.01 Keyboard [Razer Razer Copperhead Laser Mouse] on usb-0000:00:10.0-2
[   44.022690] usbcore: registered new interface driver usbhid
[   44.022693] /build/buildd/linux-source-2.6.22-2.6.22/drivers/hid/usbhid/hid-core.c: v2.6:USB HID core driver
[   44.228377] ACPI: PCI Interrupt 0000:00:09.0[A] -> GSI 16 (level, low) -> IRQ 16
[   45.159452] fuse init (API version 7.8)
[   45.180766] lp0: using parport0 (interrupt-driven).
[   45.250017] Adding 514072k swap on /dev/sda2.  Priority:-1 extents:1 across:514072k
[   45.518475] EXT3 FS on sda1, internal journal
[   46.394258] kjournald starting.  Commit interval 5 seconds
[   46.403735] EXT3 FS on sda3, internal journal
[   46.403739] EXT3-fs: mounted filesystem with ordered data mode.
[   46.579348] AppArmor: Unregistered secondary security module: capability
[   51.630729] input: Power Button (FF) as /class/input/input5
[   51.630744] ACPI: Power Button (FF) [PWRF]
[   51.630800] input: Power Button (CM) as /class/input/input6
[   51.630810] ACPI: Power Button (CM) [PWRB]
[   51.715956] No dock devices found.
[   53.297544] ppdev: user-space parallel port driver
[   53.691583] audit(1187730386.189:3): REJECTING w access to /dev/tty (cupsd(5079) profile /usr/sbin/cupsd active /usr/sbin/cupsd)
[   53.853254] AppArmor: Registered secondary security module: capability.
[   53.853258] Capability LSM initialized as secondary

```

---

