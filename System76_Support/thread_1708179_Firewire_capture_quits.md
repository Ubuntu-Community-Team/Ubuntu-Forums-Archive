---
title: "Firewire capture quits"
date: 2011-03-16
forum: System76 Support
---

### Post by reid_rsv869 on 2011-03-16
Hi Group -

I have a Serp6 machine running 10.10 and have seen new trouble with Firewire captures from my camcorder.  

Odd thing is, it worked fine just a few month ago.  Now, the camcorder is recognized by the video editor (either Kino or Kdenlive), the capture starts, runs for a minute and then quits after a minute or less.  Then the device is no longer recognized until I reboot the machine.

Another odd thing is that I have a different 10.10 machine (and old desktop I built more than five years ago) and I loaded Kino and DVgrab last night, and the Firewire capture worked first time out. So, I went back to my Serp6, completely unloaded and reloaded Kino and DVGrab but the same issue and symptom persists.

I've included some diagnostic output from lspci and demesg commands.  Any thoughts appreciated.

----------------------------------------------------------------

reid@rsv-linux:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Core Processor DMI [8086:d132] (rev 11)
00:03.0 PCI bridge [0604]: Intel Corporation Core Processor PCI Express Root Port 1 [8086:d138] (rev 11)
00:08.0 System peripheral [0880]: Intel Corporation Core Processor System Management Registers [8086:d155] (rev 11)
00:08.1 System peripheral [0880]: Intel Corporation Core Processor Semaphore and Scratchpad Registers [8086:d156] (rev 11)
00:08.2 System peripheral [0880]: Intel Corporation Core Processor System Control and Status Registers [8086:d157] (rev 11)
00:08.3 System peripheral [0880]: Intel Corporation Core Processor Miscellaneous Registers [8086:d158] (rev 11)
00:10.0 System peripheral [0880]: Intel Corporation Core Processor QPI Link [8086:d150] (rev 11)
00:10.1 System peripheral [0880]: Intel Corporation Core Processor QPI Routing and Protocol Registers [8086:d151] (rev 11)
00:1a.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b3c] (rev 06)
00:1b.0 Audio device [0403]: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio [8086:3b56] (rev 06)
00:1c.0 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 [8086:3b42] (rev 06)
00:1c.1 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 [8086:3b44] (rev 06)
00:1c.3 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 [8086:3b48] (rev 06)
00:1c.4 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 [8086:3b4a] (rev 06)
00:1d.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b34] (rev 06)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev a6)
00:1f.0 ISA bridge [0601]: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller [8086:3b03] (rev 06)
00:1f.2 SATA controller [0106]: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller [8086:3b2f] (rev 06)
00:1f.3 SMBus [0c05]: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller [8086:3b30] (rev 06)
02:00.0 VGA compatible controller [0300]: nVidia Corporation G92 [GeForce GTX 285M] [10de:060f] (rev a2)
03:00.0 Network controller [0280]: Intel Corporation Ultimate N WiFi Link 5300 [8086:4235]
07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 03)
09:00.0 FireWire (IEEE 1394) [0c00]: JMicron Technology Corp. IEEE 1394 Host Controller [197b:2380]
09:00.1 System peripheral [0880]: JMicron Technology Corp. SD/MMC Host Controller [197b:2382]
09:00.2 SD Host controller [0805]: JMicron Technology Corp. Standard SD Host Controller [197b:2381]
09:00.3 System peripheral [0880]: JMicron Technology Corp. MS Host Controller [197b:2383]
ff:00.0 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture Generic Non-Core Registers [8086:2c52] (rev 04)
ff:00.1 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture System Address Decoder [8086:2c81] (rev 04)
ff:02.0 Host bridge [0600]: Intel Corporation Core Processor QPI Link 0 [8086:2c90] (rev 04)
ff:02.1 Host bridge [0600]: Intel Corporation Core Processor QPI Physical 0 [8086:2c91] (rev 04)
ff:03.0 Host bridge [0600]: Intel Corporation Core Processor Integrated Memory Controller [8086:2c98] (rev 04)
ff:03.1 Host bridge [0600]: Intel Corporation Core Processor Integrated Memory Controller Target Address Decoder [8086:2c99] (rev 04)
ff:03.4 Host bridge [0600]: Intel Corporation Core Processor Integrated Memory Controller Test Registers [8086:2c9c] (rev 04)
ff:04.0 Host bridge [0600]: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Control Registers [8086:2ca0] (rev 04)
ff:04.1 Host bridge [0600]: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Address Registers [8086:2ca1] (rev 04)
ff:04.2 Host bridge [0600]: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Rank Registers [8086:2ca2] (rev 04)
ff:04.3 Host bridge [0600]: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Thermal Control Registers [8086:2ca3] (rev 04)
ff:05.0 Host bridge [0600]: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Control Registers [8086:2ca8] (rev 04)
ff:05.1 Host bridge [0600]: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Address Registers [8086:2ca9] (rev 04)
ff:05.2 Host bridge [0600]: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Rank Registers [8086:2caa] (rev 04)
ff:05.3 Host bridge [0600]: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Thermal Control Registers [8086:2cab] (rev 04)
reid@rsv-linux:~$ 


________________________________________________________________________________________________________________________________________________________________


reid@rsv-linux:~$ 
reid@rsv-linux:~$ 
reid@rsv-linux:~$ dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.35-27-generic (buildd@crested) (gcc version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu5) ) #48-Ubuntu SMP Tue Feb 22 20:25:46 UTC 2011 (Ubuntu 2.6.35-27.48-generic 2.6.35.11)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-27-generic root=UUID=3be83d1d-2ecd-4406-80ec-5822c983da36 ro quiet splash
[    0.000000] BIOS-provided physical RAM map:


|
|
|
| Clipped out
|
|
- Hide quoted text -
[    7.515625] ata6: DUMMY
[    7.574237] firewire_ohci: isochronous cycle inconsistent
[    7.589422] firewire_ohci: Added fw-ohci device 0000:09:00.0, OHCI v1.10, 4 IR + 0 IT contexts, quirks 0x0
[    7.859077] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    7.861164] ata1.00: ATA-8: ST9500420AS, 0002SDM1, max UDMA/133
[    7.861170] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    7.863729] ata1.00: configured for UDMA/133
[    7.879220] scsi 0:0:0:0: Direct-Access     ATA      ST9500420AS      0002 PQ: 0 ANSI: 5
[    7.879389] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    7.879480] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    7.879567] sd 0:0:0:0: [sda] Write Protect is off
[    7.879573] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    7.879627] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    7.879931]  sda: sda1 sda2 < sda5 >
[    7.938345] sd 0:0:0:0: [sda] Attached SCSI disk
[    8.068832] firewire_core: created device fw0: GUID ffe473fffffffffe, S400
[    8.077935] firewire_core: created device fw1: GUID 00804580112bc4b8, S100
[    8.077941] firewire_core: phy config: card 0, new root=ffc1, gap_count=5
[    8.090971] firewire_core: skipped bus generations, destroying all nodes
[    8.588178] firewire_core: rediscovered device fw0
[    8.628143] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    8.640929] ata2.00: ATAPI: Optiarc DVD RW AD-7580S, FX04, max UDMA/100
[    8.656222] ata2.00: configured for UDMA/100
[    8.670535] scsi 1:0:0:0: CD-ROM            Optiarc  DVD RW AD-7580S  FX04 PQ: 0 ANSI: 5
[    8.686834] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    8.686839] Uniform CD-ROM driver Revision: 3.20
[    8.686968] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    8.687031] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    9.038855] ata3: SATA link down (SStatus 0 SControl 300)
[    9.407224] ata4: SATA link down (SStatus 0 SControl 300)
[    9.779888] ata5: SATA link down (SStatus 0 SControl 300)
[   10.261803] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[   18.336349] Adding 11852796k swap on /dev/sda5.  Priority:-1 extents:1 across:11852796k 
[   18.430763] udev[514]: starting version 163
[   18.439616] lp: driver loaded but no devices found
[   18.451867] [Firmware Bug]: ACPI(MXM3) defines _DOD but not _DOS
[   18.452242] [Firmware Bug]: ACPI: ACPI brightness control misses _BQC function
[   18.608848] acpi device:48: registered as cooling_device8
[   18.609343] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:47/LNXVIDEO:01/input/input6
[   18.609388] ACPI: Video Device [MXM3] (multi-head: yes  rom: no  post: no)
[   18.870991] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   19.100275] type=1400 audit(1300149877.496:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient3" pid=678 comm="apparmor_parser"
[   19.100633] type=1400 audit(1300149877.496:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=678 comm="apparmor_parser"
[   19.100828] type=1400 audit(1300149877.496:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=678 comm="apparmor_parser"
[   19.157456] r8169 0000:07:00.0: eth0: link down
[   19.157830] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   19.287371] EDAC MC: Ver: 2.1.0 Feb 22 2011
[   19.304523] cfg80211: Calling CRDA to update world regulatory domain
[   19.308610] nvidia: module license 'NVIDIA' taints kernel.
[   19.308613] Disabling lock debugging due to kernel taint
[   19.308626] EDAC i7core: Device not found: dev 00.0 PCI ID 8086:2c50
[   19.309779] jmb38x_ms 0000:09:00.3: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   19.309787] jmb38x_ms 0000:09:00.3: setting latency timer to 64
[   19.329597] cfg80211: World regulatory domain updated:
[   19.329599]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   19.329602]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   19.329605]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   19.329607]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   19.329609]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   19.329611]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   19.356230] Linux video capture interface: v2.00
[   19.364467] uvcvideo: Found UVC 1.00 device BisonCam, NB Pro (5986:0343)
[   19.367023] input: BisonCam, NB Pro as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.1/1-1.1:1.0/input/input7
[   19.367094] usbcore: registered new interface driver uvcvideo
[   19.367097] USB Video Class driver (v0.1.0)
[   19.393734] type=1400 audit(1300149877.786:5): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=1122 comm="apparmor_parser"
[   19.394904] type=1400 audit(1300149877.786:6): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient3" pid=1116 comm="apparmor_parser"
[   19.394969] type=1400 audit(1300149877.786:7): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=1119 comm="apparmor_parser"
[   19.395466] type=1400 audit(1300149877.786:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1116 comm="apparmor_parser"
[   19.395530] type=1400 audit(1300149877.786:9): apparmor="STATUS" operation="profile_load" name="/usr/sbin/mysqld-akonadi" pid=1120 comm="apparmor_parser"
[   19.395769] type=1400 audit(1300149877.786:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1116 comm="apparmor_parser"
[   19.413938] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   19.413941] iwlagn: Copyright(c) 2003-2010 Intel Corporation
[   19.413992] iwlagn 0000:03:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   19.414000] iwlagn 0000:03:00.0: setting latency timer to 64
[   19.414046] iwlagn 0000:03:00.0: Detected Intel(R) Ultimate N WiFi Link 5300 AGN, REV=0x24
[   19.435222] iwlagn 0000:03:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[   19.435274]   alloc irq_desc for 52 on node -1
[   19.435276]   alloc kstat_irqs on node -1
[   19.435293] iwlagn 0000:03:00.0: irq 52 for MSI/MSI-X
[   19.448365]   alloc irq_desc for 22 on node -1
[   19.448367]   alloc kstat_irqs on node -1
[   19.448373] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   19.448486]   alloc irq_desc for 53 on node -1
[   19.448488]   alloc kstat_irqs on node -1
[   19.448497] HDA Intel 0000:00:1b.0: irq 53 for MSI/MSI-X
[   19.448517] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   19.493459] iwlagn 0000:03:00.0: loaded firmware version 8.24.2.12
[   19.499857] phy0: Selected rate control algorithm 'iwl-agn-rs'
[   19.676282] nvidia 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   19.676288] nvidia 0000:02:00.0: setting latency timer to 64
[   19.676292] vgaarb: device changed decodes: PCI:0000:02:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   19.676415] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  260.19.06  Mon Sep 13 04:29:19 PDT 2010
[   19.747338] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   19.773233] Finger Sensing Pad, hw: 12.1.1, sw: 1.0.0-K, buttons: 2
[   19.828348] ppdev: user-space parallel port driver
[   20.190409] input: FSPPS/2 Sentelic FingerSensingPad as /devices/platform/i8042/serio4/input/input8
[   21.237792] vboxdrv: Found 8 processor cores.
[   21.237839] VBoxDrv: dbg - g_abExecMemory=ffffffffa0de05e0
[   21.238190] vboxdrv: fAsync=0 offMin=0x1bb offMax=0xbaf4
[   21.238224] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   21.238226] vboxdrv: Successfully loaded version 4.0.0 (interface 0x00160000).
[   23.375210] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   25.530241] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   39.840376] firewire_core: giving up on config rom for node id ffc1
[   39.840384] firewire_core: phy config: card 0, new root=ffc0, gap_count=5
[   39.864710] firewire_core: skipped bus generations, destroying all nodes
[   40.363665] firewire_core: rediscovered device fw0
[   40.459771] firewire_core: phy config: card 0, new root=ffc1, gap_count=5
[   40.484001] firewire_core: skipped bus generations, destroying all nodes
[   40.979176] firewire_core: rediscovered device fw0
[   40.990075] firewire_core: created device fw1: GUID 00804580112bc4b8, S100
[   40.990080] firewire_core: phy config: card 0, new root=ffc1, gap_count=5
[   41.013281] firewire_core: skipped bus generations, destroying all nodes
[   41.508513] firewire_core: rediscovered device fw0
[   41.608378] firewire_core: phy config: card 0, new root=ffc1, gap_count=5
[   41.628887] firewire_core: skipped bus generations, destroying all nodes
[   42.127785] firewire_core: rediscovered device fw0
[   42.227641] firewire_core: phy config: card 0, new root=ffc1, gap_count=5
[   42.251858] firewire_core: skipped bus generations, destroying all nodes
[   42.746973] firewire_core: rediscovered device fw0
[   42.846850] firewire_core: phy config: card 0, new root=ffc1, gap_count=5
[   42.868590] firewire_core: skipped bus generations, destroying all nodes
[   43.366305] firewire_core: rediscovered device fw0
[   43.466171] firewire_core: phy config: card 0, new root=ffc1, gap_count=5
[   43.490404] firewire_core: skipped bus generations, destroying all nodes
[   43.509859] firewire_core: giving up on config rom for node id ffc0
[   43.985543] firewire_core: rediscovered device fw0
[   44.085402] firewire_core: phy config: card 0, new root=ffc1, gap_count=5
[   44.109636] firewire_core: skipped bus generations, destroying all nodes
[   44.604784] firewire_core: rediscovered device fw0
[   44.614784] firewire_core: giving up on config rom for node id ffc0
[   44.704648] firewire_core: phy config: card 0, new root=ffc1, gap_count=5
[   44.728901] firewire_core: skipped bus generations, destroying all nodes
[   45.224039] firewire_core: rediscovered device fw0
[   45.323910] firewire_core: phy config: card 0, new root=ffc1, gap_count=5
[   45.348161] firewire_core: skipped bus generations, destroying all nodes
[   45.367636] firewire_core: giving up on config rom for node id ffc0
[   45.843316] firewire_core: rediscovered device fw0
[   45.851031] firewire_core: rediscovered device fw1
[   45.857031] firewire_core: giving up on config rom for node id ffc0
[   46.472533] firewire_core: giving up on config rom for node id ffc0
[   47.091801] firewire_core: giving up on config rom for node id ffc0
[   47.711022] firewire_core: giving up on config rom for node id ffc0
[   48.330300] firewire_core: giving up on config rom for node id ffc0
[  110.108578] wlan0: authenticate with 00:14:bf:46:34:dc (try 1)
[  110.111652] wlan0: authenticated
[  110.111696] wlan0: associate with 00:14:bf:46:34:dc (try 1)
[  110.114056] wlan0: RX AssocResp from 00:14:bf:46:34:dc (capab=0x411 status=0 aid=2)
[  110.114062] wlan0: associated
[  110.117318] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  111.147459] Intel AES-NI instructions are not detected.
[  111.230736] padlock: VIA PadLock not detected.
[  120.816438] wlan0: no IPv6 routers present
reid@rsv-linux:~$

---

### Post by isantop on 2011-03-16
Does the camera require Firewire 800? That might cause issues, since the port in the Serval is 400.

---

### Post by reid_rsv869 on 2011-03-16
No, not that I know of.  Same camera and my Serp6 worked two months ago without issue.

---

### Post by isantop on 2011-03-16
Hi.

I'm not super familiar with firewire. Does the camera show up in Nautilus at all? If so, can you transfer files manually through it?

---

