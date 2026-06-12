---
title: "Bootup scripts and alternate kernel"
date: 2009-05-17
forum: Server Platforms
---

### Post by mastergara on 2009-05-17
After compiling a kernel for a Cobalt RAQ3 (Basic kernel config and Cobalt patches taken from [http://wiki.parvi.org/index.php/Cobalt_Kernel_Patch](http://wiki.parvi.org/index.php/Cobalt_Kernel_Patch) ), I got Hardy Heron Server installed to the drive doing the Hard Drive swap. When attempting to boot, it sits and hangs on "kernel log daemon", and will eventually fail. Bootup process below:

```






         Sun Cobalt - Smaller, Bluer, Better, and Free
               Firmware version 2.10.3-ext3

Current date: May 17 22:18:13 UTC 2009
ROM build info: Thu Mar 11 08:51:36 MST 2004 .
System serial number: invalid csum!
System type: 3000 series system, Version 1 board
Silicon serial number: 52000000dfeece01
Monitor: 153536 bytes
Memory: 128 MB
CPU: 1 processor(s) detected
  CPU 0: AuthenticAMD 298MHz (3 x 100MHz host bus) [BSP]
Initializing flash: done
  Flash Bank 0: AMD AM29F080B 1024KB (01:d5)
  Flash Bank 1: not installed.
Mounting ROM fs: done
Initializing PCI: done
Initializing ethernet: 2 controller(s) found
Initializing IDE: found ALI M5229 at 00:78
  scanning ide0: master
  scanning ide1:
IDE: stabilizing spinup: 100%
Checking Memory: done

Press spacebar to enter ROM mode
Booting default method - From disk

First stage kernel (Linux): Decompressing - done
ERROR: cannot relocate with filesize 0
Second stage kernel: Decompressing - done
Linux version 2.6.27.23 (root@popcorn) (gcc version 4.4.0 (GCC) ) #1 PREEMPT Sat May 16 09:48:43 PDT 2009
BIOS-provided physical RAM map:
 BIOS-e801: 0000000000000000 - 000000000009f000 (usable)
 BIOS-e801: 0000000000100000 - 0000000008000000 (usable)
DMI not present or invalid.
last_pfn = 0x8000 max_arch_pfn = 0x100000
128MB LOWMEM available.
  mapped low ram: 0 - 08000000
  low ram: 00000000 - 08000000
  bootmap 00001000 - 00002000
(6 early reservations) ==> bootmem [0000000000 - 0008000000]
  #0 [0000000000 - 0000001000]   BIOS data page ==> [0000000000 - 0000001000]
  #1 [0000100000 - 00003a42ac]    TEXT DATA BSS ==> [0000100000 - 00003a42ac]
  #2 [00003a5000 - 00003a7000]    INIT_PG_TABLE ==> [00003a5000 - 00003a7000]
  #3 [000009f000 - 0000100000]    BIOS reserved ==> [000009f000 - 0000100000]
  #4 [0000007000 - 0000008000]          PGTABLE ==> [0000007000 - 0000008000]
  #5 [0000001000 - 0000002000]          BOOTMAP ==> [0000001000 - 0000002000]
Zone PFN ranges:
  DMA      0x00000000 -> 0x00001000
  Normal   0x00001000 -> 0x00008000
Movable zone start PFN for each node
early_node_map[2] active PFN ranges
    0: 0x00000000 -> 0x0000009f
    0: 0x00000100 -> 0x00008000
Allocating PCI resources starting at 10000000 (gap: 8000000:f8000000)
Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 32415
Kernel command line: console=ttyS0,115200 ip=off
Initializing CPU#0
PID hash table entries: 512 (order: 9, 2048 bytes)
TSC: Using PIT calibration value
Detected 298.795 MHz processor.
console [ttyS0] enabled
Dentry cache hash table entries: 16384 (order: 4, 65536 bytes)
Inode-cache hash table entries: 8192 (order: 3, 32768 bytes)
Memory: 126680k/131072k available (1969k kernel code, 3844k reserved, 489k data, 144k init, 0k highmem)
virtual kernel memory layout:
    fixmap  : 0xffffb000 - 0xfffff000   (  16 kB)
    vmalloc : 0xc8800000 - 0xffff9000   ( 887 MB)
    lowmem  : 0xc0000000 - 0xc8000000   ( 128 MB)
      .init : 0xc036a000 - 0xc038e000   ( 144 kB)
      .data : 0xc02ec61b - 0xc0366d40   ( 489 kB)
      .text : 0xc0100000 - 0xc02ec61b   (1969 kB)
Checking if this processor honours the WP bit even in supervisor mode...Ok.
SLUB: Genslabs=12, HWalign=32, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
Calibrating delay loop (skipped), value calculated using timer frequency.. 597.59 BogoMIPS (lpj=1195180)
Mount-cache hash table entries: 512
CPU: L1 I Cache: 32K (32 bytes/line), D cache 32K (32 bytes/line)
CPU: AMD-K6(tm) 3D processor stepping 0c
Checking 'hlt' instruction... OK.
Freeing SMP alternatives: 0k freed
net_namespace: 288 bytes
NET: Registered protocol family 16
PCI: Using configuration type 1 for base access
Linux Plug and Play Support v0.97 (c) Adam Belay
SCSI subsystem initialized
usbcore: registered new interface driver usbfs
usbcore: registered new interface driver hub
usbcore: registered new device driver usb
PCI: Probing PCI hardware
pci 0000:00:03.0: quirk: region 0c80-0c9f claimed by ali7101 SMB
pci 0000:00:10.0: PME# supported from D0 D1 D2 D3hot
pci 0000:00:10.0: PME# disabled
pci 0000:00:12.0: PME# supported from D0 D1 D2 D3hot
pci 0000:00:12.0: PME# disabled
pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
pci 0000:00:01.0:   IO window: disabled
pci 0000:00:01.0:   MEM window: disabled
pci 0000:00:01.0:   PREFETCH window: disabled
bus: 00 index 0 io port: [0, ffff]
bus: 00 index 1 mmio: [0, ffffffff]
bus: 01 index 0 mmio: [0, 0]
bus: 01 index 1 mmio: [0, 0]
bus: 01 index 2 mmio: [0, 0]
bus: 01 index 3 mmio: [0, 0]
NET: Registered protocol family 2
IP route cache hash table entries: 1024 (order: 0, 4096 bytes)
TCP established hash table entries: 4096 (order: 3, 32768 bytes)
TCP bind hash table entries: 4096 (order: 2, 16384 bytes)
TCP: Hash tables configured (established 4096 bind 4096)
TCP reno registered
NET: Registered protocol family 1
platform rtc_cmos: registered platform RTC device (no PNP device found)
msgmni has been set to 247
io scheduler noop registered
io scheduler deadline registered (default)
pci 0000:00:07.0: Activating ISA DMA hang workarounds
pci 0000:00:10.0: Firmware left e100 interrupts enabled; disabling
pci 0000:00:12.0: Firmware left e100 interrupts enabled; disabling
isapnp: Scanning for PnP cards...
isapnp: No Plug & Play device found
Real Time Clock Driver v1.12ac
Non-volatile memory driver v1.2
Serial: 8250/16550 driver2 ports, IRQ sharing disabled
serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
e100: Intel(R) PRO/100 Network Driver, 3.5.23-k4-NAPI
e100: Copyright(c) 1999-2006 Intel Corporation
e100: Modified by <jeff@404ster.com> to ignore bad EEPROM checksums
e100: 0000:00:10.0: e100_eeprom_load: EEPROM corrupted
e100 0000:00:10.0: PME# disabled
e100: eth0: e100_probe: addr 0xf7ffe000, irq 11, MAC addr 00:10:e0:03:3f:75
e100: 0000:00:12.0: e100_eeprom_load: EEPROM corrupted
e100 0000:00:12.0: PME# disabled
e100: eth1: e100_probe: addr 0xf7fbf000, irq 10, MAC addr 00:10:e0:03:3d:e3
Uniform Multi-Platform E-IDE driver
alim15x3 0000:00:0f.0: IDE controller (0x10b9:0x5229 rev 0xc1)
alim15x3 0000:00:0f.0: 100% native mode on irq 14
    ide0: BM-DMA at 0xffc0-0xffc7
    ide1: BM-DMA at 0xffc8-0xffcf
hda: ST310211A, ATA DISK drive
hda: UDMA/33 mode selected
ide0 at 0xfff0-0xfff7,0xffee on irq 14
ide1 at 0xffe0-0xffe7,0xffde on irq 15
hda: max request size: 128KiB
hda: 19541088 sectors (10005 MB) w/1024KiB Cache, CHS=19386/16/63
hda: cache flushes not supported
 hda: hda1 hda2 hda3
st: Version 20080504, fixed bufsize 32768, s/g segs 256
Driver 'st' needs updating - please use bus_type methods
Driver 'sd' needs updating - please use bus_type methods
Driver 'sr' needs updating - please use bus_type methods
usbmon: debugfs is not available
ohci_hcd 0000:00:02.0: OHCI Host Controller
ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
ohci_hcd 0000:00:02.0: irq 6, io mem 0xf7fff000
usb usb1: configuration #1 chosen from 1 choice
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 2 ports detected
Initializing USB Mass Storage driver...
usbcore: registered new interface driver usb-storage
USB Mass Storage support registered.
PNP: No PS/2 controller found. Probing ports directly.
serio: i8042 KBD port at 0x60,0x64 irq 1
mice: PS/2 mouse device common for all mice
alim7101_wdt: Steve Hill <steve@navaho.co.uk>.
alim7101_wdt: WDT driver for ALi M7101 initialised. timeout=30 sec (nowayout=0)
TCP cubic registered
NET: Registered protocol family 17
Using IPI Shortcut mode
Cobalt system type is Pacifica
Cobalt Networks LED driver 1.0 (modified by jeff@404ster.com)
Cobalt Networks LCD driver 4.0 (modified by jeff@404ster.com)
Cobalt Networks Serial Number driver 1.6 (modified by jeff@404ster.com)
Cobalt Networks Watchdog Timer driver 1.0 (modified by jeff@404ster.com)
Cobalt Networks Sensor driver 1.0 (modified by jeff@404ster.com)
Cobalt Networks RAM Info driver 1.0 (modified by jeff@404ster.com)
EXT3-fs: INFO: recovery required on readonly filesystem.
EXT3-fs: write access will be enabled during recovery.
kjournald starting.  Commit interval 5 seconds
EXT3-fs: recovery complete.
EXT3-fs: mounted filesystem with ordered data mode.
VFS: Mounted root (ext3 filesystem) readonly.
Freeing unused kernel memory: 144k freed
 * Setting preliminary keymap...                                                modprobe: FATAL: Could not load /lib/modules/2.6.27.23/modules.dep: No such file or directory

modprobe: FATAL: Could not load /lib/modules/2.6.27.23/modules.dep: No such file or directory

/bin/setupcon: 319: cannot open /dev/tty1: No such device or address
modprobe: FATAL: Could not load /lib/modules/2.6.27.23/modules.dep: No such file or directory

modprobe: FATAL: Could not load /lib/modules/2.6.27.23/modules.dep: No such file or directory

/bin/setupcon: 319: cannot open /dev/tty2: No such device or address
modprobe: FATAL: Could not load /lib/modules/2.6.27.23/modules.dep: No such file or directory

modprobe: FATAL: Could not load /lib/modules/2.6.27.23/modules.dep: No such file or directory

/bin/setupcon: 319: cannot open /dev/tty3: No such device or address
modprobe: FATAL: Could not load /lib/modules/2.6.27.23/modules.dep: No such file or directory

modprobe: FATAL: Could not load /lib/modules/2.6.27.23/modules.dep: No such file or directory

/bin/setupcon: 319: cannot open /dev/tty4: No such device or address
modprobe: FATAL: Could not load /lib/modules/2.6.27.23/modules.dep: No such file or directory

modprobe: FATAL: Could not load /lib/modules/2.6.27.23/modules.dep: No such file or directory

/bin/setupcon: 319: cannot open /dev/tty5: No such device or address
modprobe: FATAL: Could not load /lib/modules/2.6.27.23/modules.dep: No such file or directory

modprobe: FATAL: Could not load /lib/modules/2.6.27.23/modules.dep: No such file or directory

/bin/setupcon: 319: cannot open /dev/tty6: No such device or address
modprobe: FATAL: Could not load /lib/modules/2.6.27.23/modules.dep: No such file or directory

modprobe: FATAL: Could not load /lib/modules/2.6.27.23/modules.dep: No such file or directory

                                                                         [fail]
 * Setting the system clock
Cannot access the Hardware Clock via any known method.
Use the --debug option to see the details of our search for an access method.
 * Unable to set System Clock to: Sun May 17 15:18:50 PDT 2009
 * Starting basic networking...                                          [ OK ]
 * Starting kernel event manager...                                      [ OK ]
 * Loading hardware drivers...                                                  udev: renamed network interface eth0 to eth2
                                                                         [ OK ]
 * Setting the system clock
 * Loading kernel modules...                                                     * Loading manual drivers...                                             [ OK ]
 * Setting kernel variables...                                                  error: "vm.mmap_min_addr" is an unknown key
                                                                         [fail]
 * Activating swap...                                                    [ OK ]
 * Checking root file system...                                                 fsck 1.40.8 (13-Mar-2008)
/dev/hda3: clean, 17457/579360 files, 137508/2309580 blocks
                                                                         [ OK ]
 * Checking file systems...                                                     fsck 1.40.8 (13-Mar-2008)
/dev/hda1 was not cleanly unmounted, check forced.
/dev/hda1:                                                                      /lost+found not found.  CREATED.
/dev/hda1: 20/7936 files (20.0% non-contiguous), 20239/31720 blocks
fsck died with exit status 1
                                                                         [ OK ]
 * Mounting local filesystems...                                         [ OK ]
 * Activating swapfile swap...                                           [ OK ]
ls: cannot access /sys/module/apparmor: No such file or directory
ls: cannot access /sys/module/apparmor: No such file or directory
FATAL: Could not load /lib/modules/2.6.27.23/modules.dep: No such file or directory
$Loading AppArmor module: Failed.
 * Checking minimum space in /tmp...                                     [ OK ]
 * Skipping firewall: ufw (not enabled)...                               [ OK ]
 * Configuring network interfaces...                                     [ OK ]
 * Starting system log daemon...                                         [ OK ]
 * Starting kernel log daemon...                                         [fail]
 * Starting OpenBSD Secure Shell server sshd                             [ OK ]
 * Starting deferred execution scheduler atd                             [ OK ]
 * Starting periodic command scheduler crond                             [ OK ]
 * Running local boot scripts (/etc/rc.local)                            [ OK ]


```

After much waiting, it will eventually fail, and then sit there with no login. 

My Questions:

1. I think the lack of a login option has something to do with the serial console not configured for a login prompt. How do I configure that in Hardy Heron? As there is no monitor/frame buffer, we only need getty (or something of the like) on Serial Port 1 or 2, ttyS[01], right?
2. As the Cobalt has some pretty specific kernel requirements, how do I get the startup scripts to match my custom kernel, or are they even needed?
3. Since I cannot really boot into the "live" environment, is there a way to modify the proper files using the same hard-drive swap technique to accomplish the above tasks?

Any and all advice on this is much appreciated. Many thanks!

---

### Post by mastergara on 2009-05-19
Bump. Help would be good. Perhaps a primer on using upstart, and how it handles init-scripts?

I was able to get a serial login, and will soon be putting the cobalt on the network, so I can tick 1 and 3 off the list as completed, but information on the startup scripts and processing would help much. Many thanks in advance!

---

