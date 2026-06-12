---
title: "Samba problems"
date: 2009-01-23
forum: Server Platforms
---

### Post by davereynoldz on 2009-01-23
Hi all, I have a powermac powered ubuntu file server at home which has been a dream to me for at least 9 months. I use it to store and serve music and video and basically anything we need to share in my household. Everyone has been able access the samba shares from their respective windows pcs. We have been streaming media off this server flawlessly for 9 months or so, until the other night. 

After no updates or modifications to the server whatsoever, while we were watching a video it just froze up. The playback stopped and from that point on I could no longer browse the samba shares on my windows pcs. I can however shell in and make full use of the fileserver in a normal way, except that I can't browse the samba shares at the command prompt either. Restarting samba does not work, ghost samba processes always remain even if I try to force kill them. I have to completely reboot the server to get it back up and then it will only browse files for a minute or two before the same thing happens again. I have searched and searched and tried different configurations but to no avail. 

I have the samba shares set up to mount as ext3 in my fstab, and I have a mix of public and private shares in my smb.conf, which I've attached.

Please help I don't know what is up, I literally did nothing to my perfectly stable system and its just come crashing down.

---

### Post by aaron.d on 2009-01-23
> I can however shell in and make full use of the fileserver in a normal way, except that I can't browse the samba shares at the command prompt either

Please clarify this statement. You can't browse the partitions/directories at all? Have you checked to see if there are FS errors? what does
 ```
dmesg
``` 
say?

---

### Post by davereynoldz on 2009-01-23
dmesg output:

```
[    0.000000] Crash kernel location must be 0x2000000
[    0.000000] Reserving 0MB of memory at 32MB for crashkernel (System RAM: 512MB)
[    0.000000] Using PowerMac machine description
[    0.000000] Total memory = 512MB; using 1024kB for hash table (at cff00000)
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 2.6.24-16-powerpc (buildd@ross) (gcc version 4.1.3 20080308 (prerelease) (Ubuntu 4.1.2-21ubuntu1)) #1 Thu Apr 10 12:48:35 UTC 2008 (Ubuntu 2.6.24-16.30-powerpc)
[    0.000000] Found initrd at 0xc1a00000:0xc21c5000
[    0.000000] Found UniNorth memory controller & host bridge @ 0xf8000000 revision: 0x03
[    0.000000] Mapped at 0xfdfc0000
[    0.000000] Found a Keylargo mac-io controller, rev: 2, mapped at 0xfdf40000
[    0.000000] PowerMac motherboard: PowerMac G4 AGP Graphics
[    0.000000] console [udbg0] enabled
[    0.000000] Entering add_active_range(0, 0, 131072) 0 entries of 256 used
[    0.000000] Found UniNorth PCI host bridge at 0x00000000f0000000. Firmware bus number: 0->0
[    0.000000] Found UniNorth PCI host bridge at 0x00000000f2000000. Firmware bus number: 0->1
[    0.000000] Found UniNorth PCI host bridge at 0x00000000f4000000. Firmware bus number: 0->0
[    0.000000] via-pmu: Server Mode is disabled
[    0.000000] PMU driver v2 initialized for Core99, firmware: 0c
[    0.000000] nvram: Checking bank 0...
[    0.000000] nvram: gen0=334, gen1=335
[    0.000000] nvram: Active bank is: 1
[    0.000000] nvram: OF partition at 0x210
[    0.000000] nvram: XP partition at 0xffffffff
[    0.000000] nvram: NR partition at 0xffffffff
[    0.000000] Top of RAM: 0x20000000, Total RAM: 0x20000000
[    0.000000] Memory hole size: 0MB
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA             0 ->   131072
[    0.000000]   Normal     131072 ->   131072
[    0.000000]   HighMem    131072 ->   131072
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[1] active PFN ranges
[    0.000000]     0:        0 ->   131072
[    0.000000] On node 0 totalpages: 131072
[    0.000000]   DMA zone: 1024 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 130048 pages, LIFO batch:31
[    0.000000]   Normal zone: 0 pages used for memmap
[    0.000000]   HighMem zone: 0 pages used for memmap
[    0.000000]   Movable zone: 0 pages used for memmap
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 130048
[    0.000000] Kernel command line: root=/dev/hda3 ro quiet splash 
[    0.000000] mpic: Setting up MPIC " MPIC 1   " version 1.2 at 80040000, max 4 CPUs
[    0.000000] mpic: ISU size: 64, shift: 6, mask: 3f
[    0.000000] mpic: Initializing for 64 sources
[    0.000000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[    0.000000] GMT Delta read from XPRAM: 0 minutes, DST: on
[    0.000000] time_init: decrementer frequency = 24.909183 MHz
[    0.000000] time_init: processor frequency   = 400.000000 MHz
[    0.000012] clocksource: timebase mult[a095565] shift[22] registered
[    0.000028] clockevent: decrementer mult[660] shift[16] cpu[0]
[    0.000154] Console: colour dummy device 80x25
[    0.000167] console handover: boot [udbg0] -> real [tty0]
[    0.000781] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.001911] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.045216] High memory: 0k
[    0.045229] Memory: 505856k/524288k available (3624k kernel code, 17840k reserved, 148k data, 355k bss, 212k init)
[    0.045365] SLUB: Genslabs=11, HWalign=32, Order=0-1, MinObjects=4, CPUs=1, Nodes=1
[    0.045376] Calibrating delay loop... 49.66 BogoMIPS (lpj=99328)
[    0.124320] Security Framework initialized
[    0.124348] SELinux:  Disabled at boot.
[    0.124425] AppArmor: AppArmor initialized
[    0.124442] Failure registering capabilities with primary security module.
[    0.124469] Mount-cache hash table entries: 512
[    0.124937] device-tree: Duplicate name in /cpus/PowerPC,G4@0, renamed to "l2-cache#1"
[    0.126726] Initializing cgroup subsys ns
[    0.127559] net_namespace: 64 bytes
[    0.129075] NET: Registered protocol family 16
[    0.130489] KeyWest i2c @0x80018000 irq 26 /pci@f2000000/pci-bridge@d/mac-io@7/i2c@18000
[    0.130505]  channel 0 bus <multibus>
[    0.130526] PMU i2c /pci@f2000000/pci-bridge@d/mac-io@7/via-pmu@16000
[    0.130537]  channel 1 bus <multibus>
[    0.130544]  channel 2 bus <multibus>
[    0.130637] PCI: Probing PCI hardware
[    0.134430] PCI: Enabling device 0001:11:02.0 (0004 -> 0007)
[    0.144574] NET: Registered protocol family 8
[    0.144586] NET: Registered protocol family 20
[    0.144840] AppArmor: AppArmor Filesystem Enabled
[    0.146553] NET: Registered protocol family 2
[    0.148325] Time: timebase clocksource has been installed.
[    0.148364] Switched to high resolution mode on CPU 0
[    0.180527] IP route cache hash table entries: 16384 (order: 4, 65536 bytes)
[    0.181295] TCP established hash table entries: 65536 (order: 7, 524288 bytes)
[    0.182661] TCP bind hash table entries: 65536 (order: 6, 262144 bytes)
[    0.183368] TCP: Hash tables configured (established 65536 bind 65536)
[    0.183380] TCP reno registered
[    0.192890] checking if image is initramfs... it is
[    2.584176] Freeing initrd memory: 6144k freed
[    2.585885] Freeing initrd memory: 1808k freed
[    2.586433] Thermal assist unit using timers, shrink_timer: 500 jiffies
[    2.588112] audit: initializing netlink socket (disabled)
[    2.588164] audit(1232757776.584:1): initialized
[    2.597422] VFS: Disk quotas dquot_6.5.1
[    2.597519] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    2.598318] io scheduler noop registered
[    2.598330] io scheduler anticipatory registered
[    2.598339] io scheduler deadline registered
[    2.598392] io scheduler cfq registered (default)
[    2.599761] PCI: Enabling device 0000:00:10.0 (0086 -> 0087)
[    2.600492] aty128fb: Invalid ROM signature 1111 should  be 0xaa55
[    2.600516] aty128fb: BIOS not located, guessing timings.
[    2.600534] aty128fb: Rage128 PF PRO AGP [chip rev 0x1] 16M 128-bit SDR SGRAM (1:1)
[    2.619557] Console: switching to colour frame buffer device 128x48
[    2.637053] fb0: ATY Rage128 frame buffer device on Rage128 PF PRO AGP
[    2.785348] Generic RTC Driver v1.07
[    2.785546] Macintosh non-volatile memory driver v1.1
[    2.788520] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[    2.788787] MacIO PCI driver attached to Keylargo chipset
[    2.793018] input: Macintosh mouse button emulation as /devices/virtual/input/input0
[    2.793595] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[    2.793613] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[    2.793701] adb: starting probe task...
[    2.793720] adb: finished probe task...
[    3.812345] ide0: Found Apple KeyLargo ATA-4 controller, bus ID 2, irq 19
[    3.812372] Probing IDE interface ide0...
[    4.772647] hda: ST3120026A, ATA DISK drive
[    4.772717] hda: host max PIO4 wanted PIO255(auto-tune) selected PIO4
[    4.772922] hda: UDMA/66 mode selected
[    4.773242] ide0 at 0xe1016000-0xe1016007,0xe1016160 on irq 19
[    5.792345] ide1: Found Apple KeyLargo ATA-3 controller, bus ID 0, irq 20
[    5.792367] Probing IDE interface ide1...
[    7.380345] ide2: Found Apple KeyLargo ATA-3 controller, bus ID 1, irq 22
[    7.380366] Probing IDE interface ide2...
[    7.960654] mice: PS/2 mouse device common for all mice
[    7.961145] PowerMac i2c bus pmu 2 registered
[    7.961331] PowerMac i2c bus pmu 1 registered
[    7.961512] PowerMac i2c bus mac-io 0 registered
[    7.961881] NET: Registered protocol family 1
[    7.962050] registered taskstats version 1
[    7.962656] input: PMU as /devices/virtual/input/input1
[    7.972394] Freeing unused kernel memory: 212k init
[    8.739341] fuse init (API version 7.9)
[   10.851133] sungem.c:v0.98 8/24/03 David S. Miller (davem@redhat.com)
[   11.048694] PHY ID: 406212, addr: 0
[   11.049825] eth0: Sun GEM (PCI) 10/100/1000BaseT Ethernet 00:0a:27:b7:39:06
[   11.049837] eth0: Found BCM5201 PHY
[   11.467089] SCSI subsystem initialized
[   12.050730] usbcore: registered new interface driver usbfs
[   12.050820] usbcore: registered new interface driver hub
[   12.121292] usbcore: registered new device driver usb
[   12.326166] PCI: Enabling device 0001:11:0a.0 (0010 -> 0012)
[   12.375778] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[63]  MMIO=[80081000-800817ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[   12.387231] ohci_hcd: 2006 August 04 USB 1.1 'Open' Host Controller (OHCI) Driver
[   12.394986] hda: max request size: 512KiB
[   12.408734] hda: 234441648 sectors (120034 MB) w/8192KiB Cache, CHS=16383/255/63
[   12.410016] hda: cache flushes supported
[   12.410153]  hda:<7>libata version 3.00 loaded.
[   12.432833]  [mac] hda1 hda2 hda3 hda4
[   12.550401] PCI: Enabling device 0001:11:08.0 (0000 -> 0002)
[   12.550450] ohci_hcd 0001:11:08.0: OHCI Host Controller
[   12.550994] ohci_hcd 0001:11:08.0: new USB bus registered, assigned bus number 1
[   12.551063] ohci_hcd 0001:11:08.0: irq 27, io mem 0x80083000
[   12.624181] usb usb1: configuration #1 chosen from 1 choice
[   12.624291] hub 1-0:1.0: USB hub found
[   12.624355] hub 1-0:1.0: 2 ports detected
[   12.728726] PCI: Enabling device 0001:11:09.0 (0000 -> 0002)
[   12.728771] ohci_hcd 0001:11:09.0: OHCI Host Controller
[   12.728873] ohci_hcd 0001:11:09.0: new USB bus registered, assigned bus number 2
[   12.728935] ohci_hcd 0001:11:09.0: irq 28, io mem 0x80082000
[   12.804256] usb usb2: configuration #1 chosen from 1 choice
[   12.804423] hub 2-0:1.0: USB hub found
[   12.804458] hub 2-0:1.0: 2 ports detected
[   12.909233] sata_sil 0001:11:02.0: version 2.3
[   12.909366] sata_sil 0001:11:02.0: Applying R_ERR on DMA activate FIS errata fix
[   12.913814] scsi0 : sata_sil
[   12.919041] scsi1 : sata_sil
[   12.919199] ata1: SATA max UDMA/100 mmio m512@0x80080000 tf 0x80080080 irq 52
[   12.919213] ata2: SATA max UDMA/100 mmio m512@0x80080000 tf 0x800800c0 irq 52
[   13.384443] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[   13.408881] ata1.00: ATA-8: SAMSUNG HD501LJ, CR100-12, max UDMA7
[   13.408899] ata1.00: 976773168 sectors, multi 0: LBA48 NCQ (depth 0/32)
[   13.416873] ata1.00: configured for UDMA/100
[   13.448534] eth0: Link is up at 100 Mbps, full-duplex.
[   13.820791] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[000a27fffeb73906]
[   13.884415] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 310)
[   13.906285] ata2.00: ATA-7: WDC WD3200KS-75PFB0, 21.00M21, max UDMA/133
[   13.906304] ata2.00: 625142448 sectors, multi 0: LBA48 NCQ (depth 0/32)
[   13.912939] ata2.00: configured for UDMA/100
[   13.913391] scsi 0:0:0:0: Direct-Access     ATA      SAMSUNG HD501LJ  CR10 PQ: 0 ANSI: 5
[   13.913864] scsi 1:0:0:0: Direct-Access     ATA      WDC WD3200KS-75P 21.0 PQ: 0 ANSI: 5
[   14.673495] Driver 'sd' needs updating - please use bus_type methods
[   14.679714] sd 0:0:0:0: [sda] 976773168 512-byte hardware sectors (500108 MB)
[   14.680233] sd 0:0:0:0: [sda] Write Protect is off
[   14.680249] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   14.680404] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   14.680622] sd 0:0:0:0: [sda] 976773168 512-byte hardware sectors (500108 MB)
[   14.681852] sd 0:0:0:0: [sda] Write Protect is off
[   14.681868] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   14.681983] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   14.682002]  sda: sda1
[   14.753968] sd 0:0:0:0: [sda] Attached SCSI disk
[   14.754215] sd 1:0:0:0: [sdb] 625142448 512-byte hardware sectors (320073 MB)
[   14.754282] sd 1:0:0:0: [sdb] Write Protect is off
[   14.754295] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   14.754386] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   14.754584] sd 1:0:0:0: [sdb] 625142448 512-byte hardware sectors (320073 MB)
[   14.754642] sd 1:0:0:0: [sdb] Write Protect is off
[   14.754655] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[   14.754742] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   14.754759]  sdb: [mac] sdb1 sdb2
[   14.764587] sd 1:0:0:0: [sdb] Attached SCSI disk
[   14.818898] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   14.818980] sd 1:0:0:0: Attached scsi generic sg1 type 0
[   15.381595] Attempting manual resume
[   15.497612] EXT3-fs: INFO: recovery required on readonly filesystem.
[   15.497632] EXT3-fs: write access will be enabled during recovery.
[   17.185512] kjournald starting.  Commit interval 5 seconds
[   17.185576] EXT3-fs: hda3: orphan cleanup on readonly fs
[   17.185599] ext3_orphan_cleanup: deleting unreferenced inode 5523246
[   17.185782] ext3_orphan_cleanup: deleting unreferenced inode 5522180
[   17.212246] ext3_orphan_cleanup: deleting unreferenced inode 5522187
[   17.217726] ext3_orphan_cleanup: deleting unreferenced inode 5522188
[   17.220568] ext3_orphan_cleanup: deleting unreferenced inode 5490501
[   17.229985] EXT3-fs: hda3: 5 orphan inodes deleted
[   17.229996] EXT3-fs: recovery complete.
[   17.395224] EXT3-fs: mounted filesystem with ordered data mode.
[   25.124717] Linux agpgart interface v0.102
[   25.183203] agpgart: Detected Apple UniNorth chipset
[   25.183403] agpgart: configuring for size idx: 8
[   25.183567] agpgart: AGP aperture is 32M @ 0x0
[   25.772783] eth0: Link is up at 100 Mbps, full-duplex.
[   25.772804] eth0: Pause is disabled
[   27.795730] NET: Registered protocol family 10
[   27.796429] lo: Disabled Privacy Extensions
[   33.536475] pmac_zilog: 0.6 (Benjamin Herrenschmidt <benh@kernel.crashing.org>)
[   33.537265] ttyPZ0 at MMIO 0x80013020 (irq = 29) is a Z85c30 ESCC - Serial port
[   33.538625] ttyPZ1 at MMIO 0x80013000 (irq = 50) is a Z85c30 ESCC - Serial port
[   36.077219] apm_emu: PMU APM Emulation initialized.
[   36.164706] loop: module loaded
[   37.268353] input: PowerMac Beep as /devices/pci0001:10/0001:10:0d.0/0001:11:07.0/input/input2
[   37.954298] Adding 1505936k swap on /dev/hda4.  Priority:-1 extents:1 across:1505936k
[   38.116355] eth0: no IPv6 routers present
[   38.396104] EXT3 FS on hda3, internal journal
[   39.000122] kjournald starting.  Commit interval 5 seconds
[   39.000178] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
[   39.004572] EXT3 FS on sda1, internal journal
[   39.004586] EXT3-fs: recovery complete.
[   39.004602] EXT3-fs: mounted filesystem with ordered data mode.
[   39.033427] kjournald starting.  Commit interval 5 seconds
[   39.033463] EXT3-fs warning: checktime reached, running e2fsck is recommended
[   39.034497] EXT3 FS on sdb2, internal journal
[   39.034511] EXT3-fs: recovery complete.
[   39.034799] EXT3-fs: mounted filesystem with ordered data mode.
[   39.802973] ip_tables: (C) 2000-2006 Netfilter Core Team
[  380.912358] Machine check in kernel mode.
[  380.912388] Caused by (from SRR1=41030): Transfer error ack signal
[  380.912434] Oops: Machine check, sig: 7 [#1]
[  380.912615] PowerMac
[  380.912700] Modules linked in: iptable_filter ip_tables x_tables snd_powermac snd_pcm snd_timer snd soundcore snd_page_alloc sbp2 loop apm_emu apm_emulation pmac_zilog serial_core ipv6 evdev uninorth_agp agpgart ext3 jbd mbcache sg sd_mod sata_sil ide_disk ohci_hcd ohci1394 libata ieee1394 usbcore scsi_mod sungem sungem_phy windfarm_core fuse
[  380.914178] NIP: c0016e60 LR: e236f264 CTR: c0016e58
[  380.914367] REGS: c1cf5e20 TRAP: 0200   Not tainted  (2.6.24-16-powerpc)
[  380.921152] MSR: 00041030 <ME,IR,DR>  CR: 22008082  XER: 00000000
[  380.927866] TASK = de18ccc0[1480] 'scsi_eh_1' THREAD: c1cf4000
[  380.928078] GPR00: 00000000 c1cf5ed0 de18ccc0 000000f4 e102a008 e2364d64 e23653c0 e2364984 
[  380.934828] GPR08: 00000000 e10684d8 00000000 c0016e58 22000088 00000000 0170ae14 00241b0c 
[  380.941580] GPR16: 0170a0c8 002419c8 002419c0 017091e4 c1c86224 c1c86244 c1c38800 00000000 
[  380.948359] GPR24: e2369820 e2364984 e23653c0 e2364d64 00000000 00009032 c1c8407c c1c84000 
[  380.961793] NIP [c0016e60] ioread8+0x8/0x18
[  380.968664] LR [e236f264] ata_altstatus+0x3c/0x50 [libata]
[  380.975756] Call Trace:
[  380.982670] [c1cf5ed0] [00009032] 0x9032 (unreliable)
[  380.989759] [c1cf5ee0] [e236f40c] ata_bmdma_drive_eh+0x134/0x150 [libata]
[  380.997027] [c1cf5f10] [e2373eb4] ata_scsi_error+0x234/0x598 [libata]
[  381.004369] [c1cf5f60] [e20bc14c] scsi_error_handler+0xf0/0x534 [scsi_mod]
[  381.011883] [c1cf5fd0] [c004bcb8] kthread+0x48/0x84
[  381.019311] [c1cf5ff0] [c0013e80] kernel_thread+0x44/0x60
[  381.026756] Instruction dump:
[  381.034139] 38600004 4d860020 40be0010 38600003 4e800020 419e000c 38600000 4e800020 
[  381.041794] 38600002 4e800020 7c0004ac 88630000 <0c030000> 4c00012c 5463063e 4e800020 
[  381.049421] ---[ end trace 90e5447fdda78aa5 ]---

```

My setup is a G4 with a sata card plugged into a pci slot, I have two physical drives plugged into the sata card and as of today one of those drives is not working. However samba has been screwing up when serving from either drive.

---

### Post by aaron.d on 2009-01-23
```
[  380.912358] Machine check in kernel mode.
[  380.912388] Caused by (from SRR1=41030): Transfer error ack signal
[  380.912434] Oops: Machine check, sig: 7 [#1]
[  380.912615] PowerMac
[  380.912700] Modules linked in: iptable_filter ip_tables x_tables snd_powermac snd_pcm snd_timer snd soundcore snd_page_alloc sbp2 loop apm_emu apm_emulation pmac_zilog serial_core ipv6 evdev uninorth_agp agpgart ext3 jbd mbcache sg sd_mod sata_sil ide_disk ohci_hcd ohci1394 libata ieee1394 usbcore scsi_mod sungem sungem_phy windfarm_core fuse
[  380.914178] NIP: c0016e60 LR: e236f264 CTR: c0016e58
[  380.914367] REGS: c1cf5e20 TRAP: 0200   Not tainted  (2.6.24-16-powerpc)
[  380.921152] MSR: 00041030 <ME,IR,DR>  CR: 22008082  XER: 00000000
[  380.927866] TASK = de18ccc0[1480] 'scsi_eh_1' THREAD: c1cf4000
[  380.928078] GPR00: 00000000 c1cf5ed0 de18ccc0 000000f4 e102a008 e2364d64 e23653c0 e2364984 
[  380.934828] GPR08: 00000000 e10684d8 00000000 c0016e58 22000088 00000000 0170ae14 00241b0c 
[  380.941580] GPR16: 0170a0c8 002419c8 002419c0 017091e4 c1c86224 c1c86244 c1c38800 00000000 
[  380.948359] GPR24: e2369820 e2364984 e23653c0 e2364d64 00000000 00009032 c1c8407c c1c84000 
[  380.961793] NIP [c0016e60] ioread8+0x8/0x18
[  380.968664] LR [e236f264] ata_altstatus+0x3c/0x50 [libata]
[  380.975756] Call Trace:
[  380.982670] [c1cf5ed0] [00009032] 0x9032 (unreliable)
[  380.989759] [c1cf5ee0] [e236f40c] ata_bmdma_drive_eh+0x134/0x150 [libata]
[  380.997027] [c1cf5f10] [e2373eb4] ata_scsi_error+0x234/0x598 [libata]
[  381.004369] [c1cf5f60] [e20bc14c] scsi_error_handler+0xf0/0x534 [scsi_mod]
[  381.011883] [c1cf5fd0] [c004bcb8] kthread+0x48/0x84
[  381.019311] [c1cf5ff0] [c0013e80] kernel_thread+0x44/0x60
[  381.026756] Instruction dump:
[  381.034139] 38600004 4d860020 40be0010 38600003 4e800020 419e000c 38600000 4e800020 
[  381.041794] 38600002 4e800020 7c0004ac 88630000 <0c030000> 4c00012c 5463063e 4e800020 
[  381.049421] ---[ end trace 90e5447fdda78aa5 ]---
```

this looks bad. I havent done any digging but you may have issues with your controller. Might want to dig around to see if there are kernel updates and/or module issues. That is def the issue though.

---

