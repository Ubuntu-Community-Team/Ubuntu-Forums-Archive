---
title: "Debian network interface goes down after no internet activity"
date: 2008-10-16
forum: Server Platforms
---

### Post by dboot on 2008-10-16
I just installed Debian Etch on two different servers for a basic LAMP setup. On BOTH servers the network interface shuts off after a few minutes. I have to log into the server directly then send out internet traffic in some way for it be back on the network and after a couple of seconds the outgoing traffic will work.

For instance:
- I will have an active SSH connection with either server
- I'll stop working on the server for a few minutes
- when I try to continue working on the server, the connection will be down completely
- I log into the server directly
- run apt-get update
- nothing will happen for a few seconds (as if it is not on the network)
- then it works perfectly and I can SSH to it again

My only solution so far is to ping the default router every 5 minutes continually.

Any suggestions?

---

### Post by kerry_s on 2008-10-16
sounds like some kind of power saving feature, check your bios.

---

### Post by dboot on 2008-10-17
I agree. It does sound like a power saving, but do you think that BOTH servers would have the same bios setting?

---

### Post by kerry_s on 2008-10-17
> **dboot said:**
> I agree. It does sound like a power saving, but do you think that BOTH servers would have the same bios setting?

yeap, in my bios it's under power management section, energy efficent is the new rule, so if you never changed it, i bet it's on. :lolflag:

---

### Post by dboot on 2008-10-17
It doesn't look like that's the problem. Power Management option is set to Disabled on both servers (both have a different bios).

Any other ideas?

My ISP requires that I have DHCP enabled for the interfaces even though they don't change my IP. Is there any setting that could cause the interface to shut off until there's out going traffic?

Thanks for your help!

---

### Post by kerry_s on 2008-10-17
> **dboot said:**
> It doesn't look like that's the problem. Power Management option is set to Disabled on both servers (both have a different bios).

Any other ideas?

My ISP requires that I have DHCP enabled for the interfaces even though they don't change my IP. Is there any setting that could cause the interface to shut off until there's out going traffic?

Thanks for your help!

i don't know, try disabling the power saving feature in the os( xset -dpms ) if your using the gui make sure there all set to never in the power manager.

---

### Post by dboot on 2008-10-17
I'm not using any gui. Could you go into more detail about xset -dpms?

Also, I just noticed that the interface is immediately off when I'm not logged into the server. So, I have to then log into it, then initiate internet traffic (via ping or apt-get update), then the interface is back up.

---

### Post by Dr Small on 2008-10-17
> **dboot said:**
> I'm not using any gui. Could you go into more detail about xset -dpms?

Also, I just noticed that the interface is immediately off when I'm not logged into the server. So, I have to then log into it, then initiate internet traffic (via ping or apt-get update), then the interface is back up.
From the man page:
```
       -dpms   The -dpms option disables DPMS (Energy Star) features.
```

---

### Post by kerry_s on 2008-10-17
> **dboot said:**
> I'm not using any gui. Could you go into more detail about xset -dpms?

Also, I just noticed that the interface is immediately off when I'm not logged into the server. So, I have to then log into it, then initiate internet traffic (via ping or apt-get update), then the interface is back up.

you can use "man name-of-program" to get information, in this case "man xset".

try using "ifup eth0" to bring it back up.

i'm not really good with servers and have no futher ideas, hopefully someone more knowledgable can help you. the only other thing i can think of is perhaps something is crashing the connection, check your /var/log for any clues. sorry

---

### Post by dboot on 2008-10-17
It doesn't look like xset is installed since it only needs to be installed with an Xserver. Since I have not installed a GUI, there must be some other reason for the interface to go down on its own.

There also doesn't seem to be anything in the log files. I'm not sure exactly what to look for though.

Thanks for any help!

---

### Post by lswb on 2008-10-17
It might be something that your ISP does. If you are connected via some form of ppp you could check out the lcp-echo options.

As a last resort you could run something like "ping -i 60 some.ip.address.com" 
from /etc/rc.local.

---

### Post by cariboo on 2008-10-17
Are there any indications in either dmesg or /var/log/messages to what is happening to your interfaces.

Jim

---

### Post by dboot on 2008-10-18
> **lswb said:**
> It might be something that your ISP does. If you are connected via some form of ppp you could check out the lcp-echo options.

As a last resort you could run something like "ping -i 60 some.ip.address.com" 
from /etc/rc.local.

The interface is not ppp but it could be my ISP. Could you go into more details to add ping to /etc/rc.local? Running ping every 5 minutes seems to be the only way to keep it online.

Here are the last few entries in /var/log/messages:
```
Oct 17 18:36:17 mail kernel: loop: loaded (max 8 devices)
Oct 17 18:36:17 mail kernel: device-mapper: ioctl: 4.7.0-ioctl (2006-06-24) initialised: dm-devel@redhat.com
Oct 17 18:36:17 mail kernel: eth0: Media Link On 100mbps full-duplex 
Oct 17 18:36:17 mail kernel: ACPI: Power Button (FF) [PWRF]
Oct 17 18:36:17 mail kernel: ACPI: Power Button (CM) [PWRB]
Oct 17 18:36:18 mail kernel: NET: Registered protocol family 10
Oct 17 18:36:18 mail kernel: lo: Disabled Privacy Extensions
Oct 17 18:36:18 mail kernel: IPv6 over IPv4 tunneling driver
Oct 17 18:56:17 mail -- MARK --
Oct 17 19:16:17 mail -- MARK --
Oct 17 19:36:17 mail -- MARK --
Oct 17 19:56:17 mail -- MARK --
Oct 17 20:16:18 mail -- MARK --
Oct 17 20:36:18 mail -- MARK --
Oct 17 20:56:18 mail -- MARK --
Oct 17 21:16:18 mail -- MARK --
Oct 17 21:36:19 mail -- MARK --
Oct 17 21:56:19 mail -- MARK --
Oct 17 22:16:19 mail -- MARK --
Oct 17 22:36:19 mail -- MARK --
Oct 17 22:56:20 mail -- MARK --
Oct 17 23:16:20 mail -- MARK --
Oct 17 23:36:20 mail -- MARK --
Oct 17 23:56:20 mail -- MARK --

```

It seems so weird that it's happening to BOTH servers...

---

### Post by lswb on 2008-10-18
> **dboot said:**
> The interface is not ppp but it could be my ISP. Could you go into more details to add ping to /etc/rc.local? Running ping every 5 minutes seems to be the only way to keep it online.


/etc/rc.local is just a script that is run (as root) after all the init scripts finish (It is not run in single-user/recovery mode though) The default file just has some comments and a single command: exit.

So just include the ping command before the exit line and it should work OK. You could use 

ping -i 300 google.com

or maybe your ISP nameserver for the pingee. The " -i 300 " sets the ping interval to 300 seconds

---

### Post by dboot on 2008-10-18
Does the script need to run continually?

Currently the only way I can keep the servers online is to run "ping -i 300 defaultrouter" on both. I have to be logged into the servers and do this. It doesn't seem like putting it in /etc/rc.local would ping the default router over and over.

Thanks for the help!

---

### Post by promodus on 2008-10-18
I would think:
/var/log/dmesg would be a better place to look than /var/log/messages
Check rotated logs, also.

Would you mind posting the verbose output from lspci?
```
lspci -v -v 
```
> put the output within quote tags to save space

---

### Post by dboot on 2008-10-18
dmesg:

```
mail:/var/log# cat dmesg
Linux version 2.6.18-5-686 (Debian 2.6.18.dfsg.1-17) (dannf@debian.org) (gcc version 4.1.2 20061115 (prerelease) (Debian 4.1.1-21)) #1 SMP Mon Dec 24 16:41:07 UTC 2007
BIOS-provided physical RAM map:
 BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
 BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
 BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
 BIOS-e820: 0000000000100000 - 000000007fffc000 (usable)
 BIOS-e820: 000000007fffc000 - 000000007ffff000 (ACPI data)
 BIOS-e820: 000000007ffff000 - 0000000080000000 (ACPI NVS)
 BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
 BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
 BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
1151MB HIGHMEM available.
896MB LOWMEM available.
On node 0 totalpages: 524284
  DMA zone: 4096 pages, LIFO batch:0
  Normal zone: 225280 pages, LIFO batch:31
  HighMem zone: 294908 pages, LIFO batch:31
DMI 2.3 present.
ACPI: RSDP (v000 ASUS                                  ) @ 0x000f5770
ACPI: RSDT (v001 ASUS   P4S8X-X  0x42302e31 MSFT 0x31313031) @ 0x7fffc000
ACPI: FADT (v001 ASUS   P4S8X-X  0x42302e31 MSFT 0x31313031) @ 0x7fffc0c0
ACPI: BOOT (v001 ASUS   P4S8X-X  0x42302e31 MSFT 0x31313031) @ 0x7fffc030
ACPI: MADT (v001 ASUS   P4S8X-X  0x42302e31 MSFT 0x31313031) @ 0x7fffc058
ACPI: DSDT (v001   ASUS P4S8X-X  0x00001000 MSFT 0x0100000b) @ 0x00000000
ACPI: PM-Timer IO Port: 0xe408
ACPI: Local APIC address 0xfee00000
ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
Processor #0 15:2 APIC version 20
ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
Processor #1 15:2 APIC version 20
ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
IOAPIC[0]: apic_id 2, version 128, address 0xfec00000, GSI 0-23
ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl edge)
ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 20 low level)
ACPI: IRQ0 used by override.
ACPI: IRQ2 used by override.
Enabling APIC mode:  Flat.  Using 1 I/O APICs
Using ACPI (MADT) for SMP configuration information
Allocating PCI resources starting at 88000000 (gap: 80000000:7ec00000)
Detected 3066.487 MHz processor.
Built 1 zonelists.  Total pages: 524284
Kernel command line: root=/dev/hdc1 ro 
mapped APIC to ffffd000 (fee00000)
mapped IOAPIC to ffffc000 (fec00000)
Enabling fast FPU save and restore... done.
Enabling unmasked SIMD FPU exception support... done.
Initializing CPU#0
PID hash table entries: 4096 (order: 12, 16384 bytes)
Console: colour VGA+ 80x25
Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
Memory: 2071596k/2097136k available (1541k kernel code, 24292k reserved, 576k data, 196k init, 1179632k highmem)
Checking if this processor honours the WP bit even in supervisor mode... Ok.
Calibrating delay using timer specific routine.. 6136.69 BogoMIPS (lpj=12273382)
Security Framework v1.0.0 initialized
SELinux:  Disabled at boot.
Capability LSM initialized
Mount-cache hash table entries: 512
CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000 00000000
CPU: After vendor identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000 00000000
CPU: Trace cache: 12K uops, L1 D cache: 8K
CPU: L2 cache: 512K
CPU: Physical Processor ID: 0
CPU: After all inits, caps: bfebfbff 00000000 00000000 00000080 00004400 00000000 00000000
Intel machine check architecture supported.
Intel machine check reporting enabled on CPU#0.
CPU0: Intel P4/Xeon Extended MCE MSRs (12) available
CPU0: Thermal monitoring enabled
Compat vDSO mapped to ffffe000.
Checking 'hlt' instruction... OK.
SMP alternatives: switching to UP code
ACPI: Core revision 20060707
CPU0: Intel(R) Pentium(R) 4 CPU 3.06GHz stepping 07
SMP alternatives: switching to SMP code
Booting processor 1/1 eip 3000
Initializing CPU#1
Calibrating delay using timer specific routine.. 6133.06 BogoMIPS (lpj=12266124)
CPU: After generic identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000 00000000
CPU: After vendor identify, caps: bfebfbff 00000000 00000000 00000000 00004400 00000000 00000000
CPU: Trace cache: 12K uops, L1 D cache: 8K
CPU: L2 cache: 512K
CPU: Physical Processor ID: 0
CPU: After all inits, caps: bfebfbff 00000000 00000000 00000080 00004400 00000000 00000000
Intel machine check architecture supported.
Intel machine check reporting enabled on CPU#1.
CPU1: Intel P4/Xeon Extended MCE MSRs (12) available
CPU1: Thermal monitoring enabled
CPU1: Intel(R) Pentium(R) 4 CPU 3.06GHz stepping 07
Total of 2 processors activated (12269.75 BogoMIPS).
ENABLING IO-APIC IRQs
..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
checking TSC synchronization across 2 CPUs: passed.
Brought up 2 CPUs
migration_cost=195
checking if image is initramfs... it is
Freeing initrd memory: 4383k freed
NET: Registered protocol family 16
ACPI: bus type pci registered
PCI: PCI BIOS revision 2.10 entry at 0xf10f0, last bus=1
PCI: Using configuration type 1
Setting up standard PCI resources
ACPI: Interpreter enabled
ACPI: Using IOAPIC for interrupt routing
ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 6 7 10 *11 12 14 15)
ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *10 11 12 14 15)
ACPI: PCI Interrupt Link [LNKC] (IRQs *3 4 5 6 7 10 11 12 14 15)
ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 *5 6 7 10 11 12 14 15)
ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 *6 7 10 11 12 14 15)
ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 10 11 12 14 15) *9
ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 10 11 12 14 15) *0, disabled.
ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 10 11 12 14 15) *9
ACPI: PCI Root Bridge [PCI0] (0000:00)
PCI: Probing PCI hardware (bus 00)
ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
Enabling SiS 96x SMBus.
PCI: Ignoring BAR0-3 of IDE controller 0000:00:02.5
Boot video device is 0000:01:00.0
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
Linux Plug and Play Support v0.97 (c) Adam Belay
pnp: PnP ACPI init
pnp: PnP ACPI: found 15 devices
PnPBIOS: Disabled by ACPI PNP
PCI: Using ACPI for IRQ routing
PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
pnp: 00:02: ioport range 0xe400-0xe47f could not be reserved
pnp: 00:02: ioport range 0xe480-0xe4ff has been reserved
pnp: 00:02: ioport range 0xe600-0xe61f has been reserved
pnp: 00:02: ioport range 0x480-0x48f has been reserved
pnp: 00:0e: ioport range 0x295-0x296 has been reserved
PCI: Bridge: 0000:00:01.0
  IO window: disabled.
  MEM window: e7000000-e7ffffff
  PREFETCH window: ef700000-febfffff
PCI: Setting latency timer of device 0000:00:01.0 to 64
NET: Registered protocol family 2
IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
TCP: Hash tables configured (established 131072 bind 65536)
TCP reno registered
Simple Boot Flag at 0x3a set to 0x1
audit: initializing netlink socket (disabled)
audit(1224282941.988:1): initialized
highmem bounce pool size: 64 pages
VFS: Disk quotas dquot_6.5.1
Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
Initializing Cryptographic API
io scheduler noop registered
io scheduler anticipatory registered
io scheduler deadline registered
io scheduler cfq registered (default)
isapnp: Scanning for PnP cards...
isapnp: No Plug & Play device found
Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
ACPI: PCI Interrupt 0000:00:0d.0[A] -> GSI 17 (level, low) -> IRQ 177
RAMDISK driver initialized: 16 RAM disks of 8192K size 1024 blocksize
PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
serio: i8042 AUX port at 0x60,0x64 irq 12
serio: i8042 KBD port at 0x60,0x64 irq 1
mice: PS/2 mouse device common for all mice
TCP bic registered
NET: Registered protocol family 1
NET: Registered protocol family 17
NET: Registered protocol family 8
NET: Registered protocol family 20
Starting balanced_irq
Using IPI No-Shortcut mode
ACPI: (supports S0 S1 S4 S5)
Freeing unused kernel memory: 196k freed
Time: tsc clocksource has been installed.
input: AT Translated Set 2 keyboard as /class/input/input0
ACPI: Invalid PBLK length [5]
Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
SIS5513: IDE controller at PCI slot 0000:00:02.5
ACPI: PCI Interrupt 0000:00:02.5[A] -> GSI 16 (level, low) -> IRQ 185
SIS5513: chipset revision 0
SIS5513: not 100% native mode: will probe irqs later
SIS5513: SiS 962/963 MuTIOL IDE UDMA133 controller
    ide0: BM-DMA at 0xb400-0xb407, BIOS settings: hda:pio, hdb:DMA
    ide1: BM-DMA at 0xb408-0xb40f, BIOS settings: hdc:DMA, hdd:pio
Probing IDE interface ide0...
usbcore: registered new driver usbfs
usbcore: registered new driver hub
ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
sis900.c: v1.08.10 Apr. 2 2006
hdb: JLMS XJ-HD166S, ATAPI CD/DVD-ROM drive
ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
Probing IDE interface ide1...
hdc: WDC WD800BB-00DKA0, ATA DISK drive
ide1 at 0x170-0x177,0x376 on irq 15
ACPI: PCI Interrupt 0000:00:03.0[A] -> GSI 20 (level, low) -> IRQ 169
ohci_hcd 0000:00:03.0: OHCI Host Controller
ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus number 1
ohci_hcd 0000:00:03.0: irq 169, io mem 0xe6800000
usb usb1: configuration #1 chosen from 1 choice
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 3 ports detected
ACPI: PCI Interrupt 0000:00:03.1[B] -> GSI 21 (level, low) -> IRQ 193
ohci_hcd 0000:00:03.1: OHCI Host Controller
ohci_hcd 0000:00:03.1: new USB bus registered, assigned bus number 2
ohci_hcd 0000:00:03.1: irq 193, io mem 0xe6000000
usb usb2: configuration #1 chosen from 1 choice
hub 2-0:1.0: USB hub found
hub 2-0:1.0: 3 ports detected
ACPI: PCI Interrupt 0000:00:03.2[D] -> GSI 23 (level, low) -> IRQ 201
ehci_hcd 0000:00:03.2: EHCI Host Controller
ehci_hcd 0000:00:03.2: new USB bus registered, assigned bus number 3
PCI: cache line size of 128 is not supported by device 0000:00:03.2
ehci_hcd 0000:00:03.2: irq 201, io mem 0xe5800000
ehci_hcd 0000:00:03.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
usb usb3: configuration #1 chosen from 1 choice
hub 3-0:1.0: USB hub found
hub 3-0:1.0: 6 ports detected
ACPI: PCI Interrupt 0000:00:04.0[A] -> GSI 19 (level, low) -> IRQ 209
0000:00:04.0: Realtek RTL8201 PHY transceiver found at address 1.
0000:00:04.0: Using transceiver found at address 1 as default
eth0: SiS 900 PCI Fast Ethernet at 0x9800, IRQ 209, 00:0e:a6:55:ab:2e.
hdb: ATAPI 48X DVD-ROM drive, 512kB Cache, UDMA(33)
Uniform CD-ROM driver Revision: 3.20
hdc: max request size: 512KiB
hdc: 156301488 sectors (80026 MB) w/2048KiB Cache, CHS=16383/255/63, UDMA(100)
hdc: cache flushes supported
 hdc: hdc1 hdc2 < hdc5 >
Attempting manual resume
kjournald starting.  Commit interval 5 seconds
EXT3-fs: mounted filesystem with ordered data mode.
pci_hotplug: PCI Hot Plug PCI Core version: 0.5
shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
input: PC Speaker as /class/input/input1
Linux agpgart interface v0.101 (c) Dave Jones
agpgart: Detected SiS 648 chipset
agpgart: AGP aperture is 64M @ 0xe8000000
Real Time Clock Driver v1.12ac
sis96x_smbus 0000:00:02.1: SiS96x SMBus base address: 0xe600
Intel 810 + AC97 Audio, version 1.01, 17:03:13 Dec 24 2007
ACPI: PCI Interrupt 0000:00:02.7[C] -> GSI 18 (level, low) -> IRQ 217
i810: SiS 7012 found at IO 0xa000 and 0xa400, MEM 0x0000 and 0x0000, IRQ 217
parport: PnPBIOS parport detected.
parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
i810_audio: Audio Controller supports 6 channels.
i810_audio: Defaulting to base 2 channel mode.
i810_audio: Resetting connection 0
ac97_codec: AC97 Audio codec, id: ADS112 (Analog Devices AD1981)
i810_audio: AC'97 codec 0 supports AMAP, total channels = 6
input: ImPS/2 Generic Wheel Mouse as /class/input/input2
ts: Compaq touchscreen protocol output
Adding 2650684k swap on /dev/hdc5.  Priority:-1 extents:1 across:2650684k
EXT3 FS on hdc1, internal journal
loop: loaded (max 8 devices)
device-mapper: ioctl: 4.7.0-ioctl (2006-06-24) initialised: [email]dm-devel@redhat.com[/email]
eth0: Media Link On 100mbps full-duplex
```

lspci -v -v:

```
mail:/var/log# lspci -v -v
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 645xx (rev 11)
	Subsystem: ASUSTeK Computer Inc. Unknown device 8086
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ >SERR- <PERR-
	Latency: 32
	Region 0: Memory at e8000000 (32-bit, non-prefetchable) [size=64M]
	Capabilities: [c0] AGP version 3.5
		Status: RQ=32 Iso- ArqSz=0 Cal=0 SBA+ ITACoh- GART64- HTrans- 64bit- FW+ AGP3- Rate=x1,x2,x4
		Command: RQ=1 ArqSz=0 Cal=0 SBA- AGP- GART64- 64bit- FW- Rate=<none>

00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge) (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz+ UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 64
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	Memory behind bridge: e7000000-e7ffffff
	Prefetchable memory behind bridge: ef700000-febfffff
	Secondary status: 66MHz+ FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort+ <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA- VGA+ MAbort- >Reset- FastB2B-

00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS963 [MuTIOL Media IO] (rev 25)
	Control: I/O+ Mem+ BusMaster+ SpecCycle+ MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0

00:02.1 SMBus: Silicon Integrated Systems [SiS] SiS961/2 SMBus Controller
	Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Interrupt: pin B routed to IRQ 0
	Region 4: I/O ports at e600 [size=32]

00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (prog-if 80 [Master])
	Subsystem: ASUSTeK Computer Inc. Unknown device 8087
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 128
	Interrupt: pin ? routed to IRQ 185
	Region 4: I/O ports at b400 [size=16]

00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
	Subsystem: ASUSTeK Computer Inc. Unknown device 80b0
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 32 (13000ns min, 2750ns max)
	Interrupt: pin C routed to IRQ 217
	Region 0: I/O ports at a400 [size=256]
	Region 1: I/O ports at a000 [size=128]
	Capabilities: [48] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=55mA PME(D0-,D1-,D2-,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-

00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f) (prog-if 10 [OHCI])
	Subsystem: ASUSTeK Computer Inc. Unknown device 8087
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 32 (20000ns max), Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 169
	Region 0: Memory at e6800000 (32-bit, non-prefetchable) [size=4K]

00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f) (prog-if 10 [OHCI])
	Subsystem: ASUSTeK Computer Inc. Unknown device 8087
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 32 (20000ns max), Cache Line Size: 32 bytes
	Interrupt: pin B routed to IRQ 193
	Region 0: Memory at e6000000 (32-bit, non-prefetchable) [size=4K]

00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller (prog-if 20 [EHCI])
	Subsystem: ASUSTeK Computer Inc. Unknown device 8087
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 32 (20000ns max)
	Interrupt: pin D routed to IRQ 201
	Region 0: Memory at e5800000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [50] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=375mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-

00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
	Subsystem: ASUSTeK Computer Inc. Unknown device 80a7
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 32 (13000ns min, 2750ns max)
	Interrupt: pin A routed to IRQ 209
	Region 0: I/O ports at 9800 [size=256]
	Region 1: Memory at e5000000 (32-bit, non-prefetchable) [size=4K]
	Expansion ROM at ef6e0000 [disabled] [size=128K]
	Capabilities: [40] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-

00:0d.0 Modem: PCTel Inc HSP MicroModem 56 (rev 02) (prog-if 04 [Hayes/16750])
	Subsystem: PCTel Inc HSP MicroModem 56
	Control: I/O+ Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping+ SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Interrupt: pin A routed to IRQ 177
	Region 0: I/O ports at 9400 [size=64]
	Capabilities: [40] Power Management version 2
		Flags: PMEClk- DSI+ D1- D2+ AuxCurrent=55mA PME(D0+,D1-,D2+,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-

01:00.0 VGA compatible controller: nVidia Corporation NV25 [GeForce4 Ti 4600] (rev a3) (prog-if 00 [VGA])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 64 (1250ns min, 250ns max)
	Interrupt: pin A routed to IRQ 11
	Region 0: Memory at e7000000 (32-bit, non-prefetchable) [size=16M]
	Region 1: Memory at f0000000 (32-bit, prefetchable) [size=128M]
	Region 2: Memory at ef800000 (32-bit, prefetchable) [size=512K]
	Expansion ROM at ef7e0000 [disabled] [size=128K]
	Capabilities: [60] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [44] AGP version 2.0
		Status: RQ=32 Iso- ArqSz=0 Cal=0 SBA+ ITACoh- GART64- HTrans- 64bit- FW+ AGP3- Rate=x1,x2,x4
		Command: RQ=1 ArqSz=0 Cal=0 SBA- AGP- GART64- 64bit- FW- Rate=<none>

```

Here's the output of the other serv# lspci -v -v
```

00:00.0 Host bridge: VIA Technologies, Inc. VT82C693A/694x [Apollo PRO133x] (rev c4)
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ >SERR- <PERR-
	Latency: 0
	Region 0: Memory at d8000000 (32-bit, prefetchable) [size=64M]
	Capabilities: [a0] AGP version 2.0
		Status: RQ=32 Iso- ArqSz=0 Cal=0 SBA+ ITACoh- GART64- HTrans- 64bit- FW- AGP3- Rate=x1,x2
		Command: RQ=1 ArqSz=0 Cal=0 SBA- AGP- GART64- 64bit- FW- Rate=<none>
	Capabilities: [c0] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-

00:01.0 PCI bridge: VIA Technologies, Inc. VT82C598/694x [Apollo MVP3/Pro133x AGP] (prog-if 00 [Normal decode])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort+ >SERR- <PERR-
	Latency: 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: dc000000-ddffffff
	Prefetchable memory behind bridge: d0000000-d7ffffff
	Secondary status: 66MHz- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- <SERR- <PERR-
	BridgeCtl: Parity- SERR- NoISA+ VGA+ MAbort- >Reset- FastB2B-
	Capabilities: [80] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-

00:07.0 ISA bridge: VIA Technologies, Inc. VT82C596 ISA [Mobile South] (rev 23)
	Subsystem: VIA Technologies, Inc. VT82C596/A/B PCI to ISA Bridge
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping+ SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0

00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 10) (prog-if 8a [Master SecP PriP])
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 32
	Region 4: I/O ports at e000 [size=16]
	Capabilities: [c0] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-

00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 11) (prog-if 00 [UHCI])
	Subsystem: VIA Technologies, Inc. (Wrong ID) USB Controller
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 32, Cache Line Size: 32 bytes
	Interrupt: pin D routed to IRQ 10
	Region 4: I/O ports at e400 [size=32]
	Capabilities: [80] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-

00:07.3 Host bridge: VIA Technologies, Inc. VT82C596 Power Management (rev 30)
	Control: I/O- Mem- BusMaster- SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap- 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-

00:10.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)
	Subsystem: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 32 (8000ns min, 16000ns max), Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 11
	Region 0: I/O ports at e800 [size=256]
	Region 1: Memory at df000000 (32-bit, non-prefetchable) [size=256]
	[virtual] Expansion ROM at 30000000 [disabled] [size=128K]
	Capabilities: [dc] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=375mA PME(D0-,D1+,D2+,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-

01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE] (prog-if 00 [VGA])
	Subsystem: PC Partner Limited RV100 QY [Sapphire Radeon VE 7000]
	Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping+ SERR- FastB2B-
	Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 32 (2000ns min), Cache Line Size: 32 bytes
	Interrupt: pin A routed to IRQ 11
	Region 0: Memory at d0000000 (32-bit, prefetchable) [size=128M]
	Region 1: I/O ports at d000 [size=256]
	Region 2: Memory at dd000000 (32-bit, non-prefetchable) [size=64K]
	[virtual] Expansion ROM at dc000000 [disabled] [size=128K]
	Capabilities: [58] AGP version 2.0
		Status: RQ=48 Iso- ArqSz=0 Cal=0 SBA+ ITACoh- GART64- HTrans- 64bit- FW- AGP3- Rate=x1,x2,x4
		Command: RQ=1 ArqSz=0 Cal=0 SBA+ AGP- GART64- 64bit- FW- Rate=<none>
	Capabilities: [50] Power Management version 2
		Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-

```

---

### Post by promodus on 2008-10-18
not dmesg specifically.
Check /var/log/dmesg.#.gz files... look for info in the log approximately the same date you had the symptom.

I'm wondering if your modem is giving your network card problems?
Could try moving the modem to a different slot?
If this is a laptop, I don't know what to tell you.

For a server, IMO, the best network cards are intel.

---

### Post by dboot on 2008-10-18
The servers are two very different boxes. One was built with spare parts and the other was my old desktop. The hardware (including the NICs: one is integrated and the other is PCI) in each is very different. The same exact problem is happening on both servers. This makes me think that it's an OS issue. I used Debian 4 (Etch) net install.

The network is setup so that my ISP has fiber to a 60 port ethernet gigabit router. I'm given 3 static IP's for server use. Every box connected, including the static IP's, has to use DHCP to resolve an IP.

Even though the servers are somewhat like Dr. Frankenstein's monster, I'd like to turn them into production level servers.

Thanks for all suggestions!

---

### Post by promodus on 2008-10-18
I never even thought of it...

How are your network interfaces configured?
I'm wondering if after some time DHCP tries to renew the cards, yet fails to grab an address?

```
cat /etc/network/interfaces
```

and

```
dpkg -l | grep dhcp
```

Any luck with the dmesg logs?

---

### Post by dboot on 2008-10-18
Both servers are configured the same:

```
mail:~# cat /etc/network/interfaces 
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp
mail:~# dpkg -l | grep dhcp
ii  dhcp3-client                      3.0.4-13                             DHCP Client
ii  dhcp3-common                      3.0.4-13                             Common files used by all the dhcp3* packages

```

---

### Post by promodus on 2008-10-18
> **dboot said:**
> The network is setup so that my ISP has fiber to a 60 port ethernet gigabit router.[COLOR="RoyalBlue"] I'm given 3 static IP's for server use.[/COLOR] Every box connected, including the static IP's, has to use DHCP to resolve an IP.




> **dboot said:**
> [COLOR="RoyalBlue"]Both servers are configured the same:[/COLOR]

```
mail:~# cat /etc/network/interfaces 
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
[COLOR="RoyalBlue"]iface eth0 inet dhcp[/COLOR]
mail:~# dpkg -l | grep dhcp
ii  dhcp3-client                      3.0.4-13                             DHCP Client
ii  dhcp3-common                      3.0.4-13                             Common files used by all the dhcp3* packages

```

Change your configuration to use static addresses, since your ISP has assigned you static IP's anyway...

I'm guessing that your dhcp client is trying to renew an address but fails. This could be a problem with your ISP's DHCP service...

But yeah, try setting them static to see if the problem persists.

---

### Post by dboot on 2008-10-18
Can you think of any reason why setting a static IP would cause my ISP trouble? I've been requested to make sure every box uses DHCP.

I'll give it a shot though and let you know in a few minutes.

---

### Post by dboot on 2008-10-18
After changing the /etc/network/interfaces to use a static IP, the server is still up. I'm not sure if the problem is fixed or if I simply haven't given it enough time to go down.

I'll report back tomorrow. Thanks for that simple solution!!

---

### Post by lswb on 2008-10-18
I'm glad that promodus solution worked, I was thinking about that ping command in /etc/rc.local, If you do try it, use the -q option so it doesn't keep trying to output resutls, and background it or /etc/rc.local won't exit.

ping -q -i 300 somewhere.com &

Sorry I didn't think about that before.

---

### Post by dboot on 2008-10-18
It turns out that making the IP static is not the solution...

I'll try adding "ping -q -i 300 somewhere.com &" to rc.local.

---

### Post by dboot on 2008-10-18
After adding "ping -q -i 300 somewhere.com &" to rc.local, I restarted the server and it did NOT come on the network.

Unless there are any other ideas, I'll just continue to run ping directly on the server.

I appreciate the help.

---

### Post by promodus on 2008-10-18
There must be a clue to this problem in your logs.

---

