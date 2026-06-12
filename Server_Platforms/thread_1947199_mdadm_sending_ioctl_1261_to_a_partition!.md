---
title: "mdadm: sending ioctl 1261 to a partition!"
date: 2012-03-26
forum: Server Platforms
---

### Post by MakOwner on 2012-03-26
Anyone have any idea if this is a problem?
I found a thread about it debian mailing list here: [http://lists.debian.org/debian-kernel/2012/03/msg00185.html](http://lists.debian.org/debian-kernel/2012/03/msg00185.html)
but it is by no means clear at least to me whether this is a serious eat-your-data issue or just a spurious error.  
This thread seems to be about kernel 3.2 and I'm running 3.0.0 one on box and 2.6.32 on another.

I have a included a lengthy section of the dmesg log here from the 3.0.0 box, but the gist of it is I see 
 
mdam: sending ioctl 1261 to a partition!

and 

mdadm: sending ioctl 800c0910 to a partition!


during boot up and array assembly.

Very ominous looking errors that only showed up after the last set of updates that required a reboot.

If this is a problem, is there any fix?


```

[    0.739836] device-mapper: uevent: version 1.0.3
[    0.740027] device-mapper: ioctl: 4.20.0-ioctl (2011-02-02) initialised: dm-devel@redhat.com
[    0.740122] cpuidle: using governor ladder
[    0.740184] cpuidle: using governor menu
[    0.740244] EFI Variables Facility v0.08 2004-May-17
[    0.740683] TCP cubic registered
[    0.740943] NET: Registered protocol family 10
[    0.741760] NET: Registered protocol family 17
[    0.741844] Registering the dns_resolver key type
[    0.742055] PM: Hibernation image not present or could not be loaded.
[    0.742073] registered taskstats version 1
[    0.765178]   Magic number: 4:103:105
[    0.765255] usbmon usbmon1: hash matches
[    0.765403] rtc_cmos 00:04: setting system clock to 2012-03-26 01:07:28 UTC (1332724048)
[    0.765513] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.765579] EDD information not available.
[    0.793814] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input1
[    0.876342] ata1.00: ATAPI: HL-DT-ST  GCR-8240N, 1.06, max UDMA/33
[    0.892221] ata1.00: configured for UDMA/33
[    0.894055] scsi 0:0:0:0: CD-ROM            HL-DT-ST CD-ROM GCR-8240N 1.06 PQ: 0 ANSI: 5
[    0.896691] sr0: scsi3-mmc drive: 24x/24x cd/rw xa/form2 cdda tray
[    0.896759] cdrom: Uniform CD-ROM driver Revision: 3.20
[    0.896972] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    0.897056] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    0.899849] Freeing unused kernel memory: 988k freed
[    0.900386] Write protecting the kernel read-only data: 12288k
[    0.910409] Freeing unused kernel memory: 2032k freed
[    0.918209] Freeing unused kernel memory: 1388k freed
[    0.949844] udevd[84]: starting version 173
[    0.986077] md: linear personality registered for level -1
[    1.004677] md: multipath personality registered for level -4
[    1.012662] md: raid0 personality registered for level 0
[    1.022480] md: raid1 personality registered for level 1
[    1.031784] async_tx: api initialized (async)
[    1.075243] tg3.c:v3.119 (May 18, 2011)
[    1.075328] tg3 0000:04:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.075407] tg3 0000:04:00.0: setting latency timer to 64
[    1.089519] sata_sil24 0000:01:00.0: version 1.1
[    1.089541] sata_sil24 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.089710] sata_sil24 0000:01:00.0: setting latency timer to 64
[    1.100096] raid6: int64x1    843 MB/s
[    1.111740] Adaptec aacraid driver 1.1-7[28000]-ms
[    1.111873] aacraid 0000:03:02.0: PCI INT A -> GSI 35 (level, low) -> IRQ 35
[    1.112053] scsi2 : sata_sil24
[    1.115325] scsi4 : sata_sil24
[    1.115516] ata3: SATA max UDMA/100 host m128@0xfe9ffc00 port 0xfe9f8000 irq 16
[    1.115606] ata4: SATA max UDMA/100 host m128@0xfe9ffc00 port 0xfe9fa000 irq 16
[    1.168082] raid6: int64x2   1083 MB/s
[    1.178388] tg3 0000:04:00.0: eth0: Tigon3 [partno(BCM95721) rev 4101] (PCI Express) MAC address 00:14:22:7b:6b:e1
[    1.178491] tg3 0000:04:00.0: eth0: attached PHY is 5750 (10/100/1000Base-T Ethernet) (WireSpeed[1], EEE[0])
[    1.178586] tg3 0000:04:00.0: eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[1] TSOcap[1]
[    1.178675] tg3 0000:04:00.0: eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[    1.178846] tg3 0000:05:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.178924] tg3 0000:05:00.0: setting latency timer to 64
[    1.180717] Floppy drive(s): fd0 is 1.44M
[    1.202745] tg3 0000:05:00.0: eth1: Tigon3 [partno(BCM95721) rev 4101] (PCI Express) MAC address 00:14:22:7b:6b:e2
[    1.202847] tg3 0000:05:00.0: eth1: attached PHY is 5750 (10/100/1000Base-T Ethernet) (WireSpeed[1], EEE[0])
[    1.202941] tg3 0000:05:00.0: eth1: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[1] TSOcap[1]
[    1.203031] tg3 0000:05:00.0: eth1: dma_rwctrl[76180000] dma_mask[64-bit]
[    1.236041] raid6: int64x4    802 MB/s
[    1.240398] AAC0: kernel 4.1-0[7417] 
[    1.240466] AAC0: monitor 4.1-0[7417]
[    1.240529] AAC0: bios 4.1-0[7417]
[    1.240592] AAC0: serial 4D998B
[    1.241630] scsi3 : aacraid
[    1.245123] scsi 3:0:0:0: Direct-Access     CERC     RAID1            V1.0 PQ: 0 ANSI: 2
[    1.260071] Refined TSC clocksource calibration: 2800.098 MHz.
[    1.260147] Switching to clocksource tsc
[    1.304052] raid6: int64x8    845 MB/s
[    1.372021] raid6: sse2x1    1439 MB/s
[    1.440023] raid6: sse2x2    2589 MB/s
[    1.508031] raid6: sse2x4    2632 MB/s
[    1.508093] raid6: using algorithm sse2x4 (2632 MB/s)
[    1.798618] scsi 3:1:0:0: Direct-Access     ST316002 3AS              8.12 PQ: 0 ANSI: 2
[    1.804589] scsi 3:1:1:0: Direct-Access     ST316002 3AS              8.12 PQ: 0 ANSI: 2
[    2.140335] sd 3:0:0:0: [sda] 312432384 512-byte logical blocks: (159 GB/148 GiB)
[    2.140432] sd 3:0:0:0: Attached scsi generic sg1 type 0
[    2.140464] sd 3:0:0:0: [sda] Write Protect is off
[    2.140482] sd 3:0:0:0: [sda] Mode Sense: 06 00 00 00
[    2.140564] sd 3:0:0:0: [sda] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[    2.140963] scsi 3:1:0:0: Attached scsi generic sg2 type 0
[    2.141429] scsi 3:1:1:0: Attached scsi generic sg3 type 0
[    2.146365]  sda: sda1 sda2 sda3
[    2.146947] sd 3:0:0:0: [sda] Attached SCSI removable disk
[    3.292030] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 0)
[    3.292345] ata3.15: Port Multiplier 1.1, 0x1095:0x3726 r23, 6 ports, feat 0x1/0x9
[    3.294670] ata3.00: hard resetting link
[    3.612278] ata3.00: SATA link up 3.0 Gbps (SStatus 123 SControl 320)
[    3.612372] ata3.01: hard resetting link
[    3.932277] ata3.01: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    3.932371] ata3.02: hard resetting link
[    4.200028] floppy0: no floppy controllers found
[    4.252287] ata3.02: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    4.252387] ata3.03: hard resetting link
[    4.572278] ata3.03: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    4.572372] ata3.04: hard resetting link
[    4.892276] ata3.04: SATA link down (SStatus 0 SControl 320)
[    4.892391] ata3.05: hard resetting link
[    5.212277] ata3.05: SATA link up 1.5 Gbps (SStatus 113 SControl 320)
[    5.213561] ata3.00: ATA-8: ST31500541AS, CC34, max UDMA/133
[    5.213627] ata3.00: 2930277168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    5.215037] ata3.00: configured for UDMA/100
[    5.216235] ata3.01: ATA-8: ST31500541AS, CC34, max UDMA/133
[    5.216301] ata3.01: 2930277168 sectors, multi 0: LBA48 NCQ (depth 31/32)
[    5.217673] ata3.01: configured for UDMA/100
[    5.218868] ata3.02: ATA-8: ST31500541AS, CC34, max UDMA/133
[    5.218933] ata3.02: 2930277168 sectors, multi 0: LBA48 NCQ (depth 31/32)
[    5.220303] ata3.02: configured for UDMA/100
[    5.221466] ata3.03: ATA-8: ST31500541AS, CC34, max UDMA/133
[    5.221532] ata3.03: 2930277168 sectors, multi 0: LBA48 NCQ (depth 31/32)
[    5.222869] ata3.03: configured for UDMA/100
[    5.222986] ata3: EH complete
[    5.223207] scsi 2:0:0:0: Direct-Access     ATA      ST31500541AS     CC34 PQ: 0 ANSI: 5
[    5.223555] sd 2:0:0:0: [sdb] 2930277168 512-byte logical blocks: (1.50 TB/1.36 TiB)
[    5.223659] sd 2:0:0:0: Attached scsi generic sg4 type 0
[    5.223795] sd 2:0:0:0: [sdb] Write Protect is off
[    5.223865] sd 2:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    5.223929] sd 2:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.223982] scsi 2:1:0:0: Direct-Access     ATA      ST31500541AS     CC34 PQ: 0 ANSI: 5
[    5.224383] sd 2:1:0:0: Attached scsi generic sg5 type 0
[    5.224683] scsi 2:2:0:0: Direct-Access     ATA      ST31500541AS     CC34 PQ: 0 ANSI: 5
[    5.225075] sd 2:2:0:0: Attached scsi generic sg6 type 0
[    5.225388] scsi 2:3:0:0: Direct-Access     ATA      ST31500541AS     CC34 PQ: 0 ANSI: 5
[    5.225770] sd 2:3:0:0: Attached scsi generic sg7 type 0
[    5.226018] sd 2:1:0:0: [sdc] 2930277168 512-byte logical blocks: (1.50 TB/1.36 TiB)
[    5.226194] sd 2:1:0:0: [sdc] Write Protect is off
[    5.226259] sd 2:1:0:0: [sdc] Mode Sense: 00 3a 00 00
[    5.226296] sd 2:1:0:0: [sdc] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.226971] sd 2:2:0:0: [sdd] 2930277168 512-byte logical blocks: (1.50 TB/1.36 TiB)
[    5.227058] sd 2:3:0:0: [sde] 2930277168 512-byte logical blocks: (1.50 TB/1.36 TiB)
[    5.227234] sd 2:3:0:0: [sde] Write Protect is off
[    5.227306] sd 2:3:0:0: [sde] Mode Sense: 00 3a 00 00
[    5.227323] sd 2:2:0:0: [sdd] Write Protect is off
[    5.227384] sd 2:3:0:0: [sde] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.227486] sd 2:2:0:0: [sdd] Mode Sense: 00 3a 00 00
[    5.227554] sd 2:2:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.244405]  sdb: sdb1
[    5.244867] sd 2:0:0:0: [sdb] Attached SCSI disk
[    5.249080]  sdc: sdc1
[    5.249604] sd 2:1:0:0: [sdc] Attached SCSI disk
[    5.253873]  sdd: sdd1
[    5.254381] sd 2:2:0:0: [sdd] Attached SCSI disk
[    5.254655]  sde: sde1
[    5.255169] sd 2:3:0:0: [sde] Attached SCSI disk
[    7.424030] ata4: SATA link up 3.0 Gbps (SStatus 123 SControl 0)
[    7.424344] ata4.15: Port Multiplier 1.1, 0x1095:0x3726 r23, 6 ports, feat 0x1/0x9
[    7.426839] ata4.00: hard resetting link
[    7.744277] ata4.00: SATA link up 3.0 Gbps (SStatus 123 SControl 320)
[    7.745232] ata4.01: hard resetting link
[    8.064278] ata4.01: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    8.064370] ata4.02: hard resetting link
[    8.384278] ata4.02: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    8.384371] ata4.03: hard resetting link
[    8.704277] ata4.03: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    8.704370] ata4.04: hard resetting link
[    9.024277] ata4.04: SATA link down (SStatus 0 SControl 320)
[    9.024393] ata4.05: hard resetting link
[    9.344276] ata4.05: SATA link up 1.5 Gbps (SStatus 113 SControl 320)
[    9.345506] ata4.00: ATA-8: ST31500541AS, CC34, max UDMA/133
[    9.345572] ata4.00: 2930277168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    9.346945] ata4.00: configured for UDMA/100
[    9.348216] ata4.01: ATA-8: ST31500541AS, CC34, max UDMA/133
[    9.348282] ata4.01: 2930277168 sectors, multi 0: LBA48 NCQ (depth 31/32)
[    9.349705] ata4.01: configured for UDMA/100
[    9.350952] ata4.02: ATA-8: ST31500541AS, CC34, max UDMA/133
[    9.351017] ata4.02: 2930277168 sectors, multi 0: LBA48 NCQ (depth 31/32)
[    9.352419] ata4.02: configured for UDMA/100
[    9.353716] ata4.03: ATA-8: ST31500541AS, CC34, max UDMA/133
[    9.353782] ata4.03: 2930277168 sectors, multi 0: LBA48 NCQ (depth 31/32)
[    9.355237] ata4.03: configured for UDMA/100
[    9.355353] ata4: EH complete
[    9.355570] scsi 4:0:0:0: Direct-Access     ATA      ST31500541AS     CC34 PQ: 0 ANSI: 5
[    9.355909] sd 4:0:0:0: [sdf] 2930277168 512-byte logical blocks: (1.50 TB/1.36 TiB)
[    9.356030] sd 4:0:0:0: Attached scsi generic sg8 type 0
[    9.356164] sd 4:0:0:0: [sdf] Write Protect is off
[    9.356234] sd 4:0:0:0: [sdf] Mode Sense: 00 3a 00 00
[    9.356301] sd 4:0:0:0: [sdf] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    9.356372] scsi 4:1:0:0: Direct-Access     ATA      ST31500541AS     CC34 PQ: 0 ANSI: 5
[    9.356727] sd 4:1:0:0: Attached scsi generic sg9 type 0
[    9.357024] sd 4:1:0:0: [sdg] 2930277168 512-byte logical blocks: (1.50 TB/1.36 TiB)
[    9.357272] scsi 4:2:0:0: Direct-Access     ATA      ST31500541AS     CC34 PQ: 0 ANSI: 5
[    9.357642] sd 4:2:0:0: [sdh] 2930277168 512-byte logical blocks: (1.50 TB/1.36 TiB)
[    9.357719] sd 4:2:0:0: Attached scsi generic sg10 type 0
[    9.357938] sd 4:2:0:0: [sdh] Write Protect is off
[    9.357965] sd 4:1:0:0: [sdg] Write Protect is off
[    9.357974] sd 4:1:0:0: [sdg] Mode Sense: 00 3a 00 00
[    9.358064] sd 4:1:0:0: [sdg] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    9.358159] sd 4:2:0:0: [sdh] Mode Sense: 00 3a 00 00
[    9.358225] sd 4:2:0:0: [sdh] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    9.358689] scsi 4:3:0:0: Direct-Access     ATA      ST31500541AS     CC34 PQ: 0 ANSI: 5
[    9.359098] sd 4:3:0:0: [sdi] 2930277168 512-byte logical blocks: (1.50 TB/1.36 TiB)
[    9.359198] sd 4:3:0:0: Attached scsi generic sg11 type 0
[    9.359338] sd 4:3:0:0: [sdi] Write Protect is off
[    9.359419] sd 4:3:0:0: [sdi] Mode Sense: 00 3a 00 00
[    9.359490] sd 4:3:0:0: [sdi] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    9.373168]  sdg: sdg1
[    9.373184]  sdi: sdi1
[    9.373837] sd 4:3:0:0: [sdi] Attached SCSI disk
[    9.373843] sd 4:1:0:0: [sdg] Attached SCSI disk
[    9.377839]  sdh: sdh1
[    9.378365] sd 4:2:0:0: [sdh] Attached SCSI disk
[    9.380654]  sdf: sdf1
[    9.381170] sd 4:0:0:0: [sdf] Attached SCSI disk
[    9.382292] xor: automatically using best checksumming function: generic_sse
[    9.400055]    generic_sse:  3136.000 MB/sec
[    9.400131] xor: using function: generic_sse (3136.000 MB/sec)
[    9.402348] md: raid6 personality registered for level 6
[    9.402426] md: raid5 personality registered for level 5
[    9.402496] md: raid4 personality registered for level 4
[    9.415837] md: raid10 personality registered for level 10
[    9.627901] mdadm: sending ioctl 1261 to a partition!
[    9.627971] mdadm: sending ioctl 1261 to a partition!
[    9.628507] mdadm: sending ioctl 1261 to a partition!
[    9.628610] mdadm: sending ioctl 1261 to a partition!
[    9.629025] mdadm: sending ioctl 1261 to a partition!
[    9.629092] mdadm: sending ioctl 1261 to a partition!
[    9.629547] mdadm: sending ioctl 1261 to a partition!
[    9.629618] mdadm: sending ioctl 1261 to a partition!
[    9.630620] mdadm: sending ioctl 800c0910 to a partition!
[    9.630695] mdadm: sending ioctl 800c0910 to a partition!
[    9.637116] md: bind<sde1>
[    9.644467] md: bind<sdb1>
[    9.651741] md: bind<sdc1>
[    9.661619] md: bind<sdh1>
[    9.667896] md: bind<sdf1>
[    9.673939] md: bind<sdg1>
[    9.680187] md: bind<sdd1>
[    9.694352] md: bind<sdi1>
[    9.699644] bio: create slab <bio-1> at 1
[    9.699731] md/raid:md0: device sdi1 operational as raid disk 0
[    9.699798] md/raid:md0: device sdd1 operational as raid disk 5
[    9.699863] md/raid:md0: device sdg1 operational as raid disk 1
[    9.699928] md/raid:md0: device sdf1 operational as raid disk 4
[    9.699993] md/raid:md0: device sdh1 operational as raid disk 2
[    9.700128] md/raid:md0: device sdc1 operational as raid disk 6
[    9.700194] md/raid:md0: device sdb1 operational as raid disk 3
[    9.700259] md/raid:md0: device sde1 operational as raid disk 7
[    9.702090] md/raid:md0: allocated 8490kB
[    9.702230] md/raid:md0: raid level 5 active with 8 out of 8 devices, algorithm 2
[    9.702319] RAID conf printout:
[    9.702322]  --- level:5 rd:8 wd:8
[    9.702325]  disk 0, o:1, dev:sdi1
[    9.702328]  disk 1, o:1, dev:sdg1
[    9.702331]  disk 2, o:1, dev:sdh1
[    9.702334]  disk 3, o:1, dev:sdb1
[    9.702336]  disk 4, o:1, dev:sdf1
[    9.702339]  disk 5, o:1, dev:sdd1
[    9.702342]  disk 6, o:1, dev:sdc1
[    9.702345]  disk 7, o:1, dev:sde1
[    9.702402] md0: detected capacity change from 0 to 10502094389248
[    9.707416]  md0: p1
[   10.085058] EXT4-fs (sda3): INFO: recovery required on readonly filesystem
[   10.085133] EXT4-fs (sda3): write access will be enabled during recovery
[   10.300620] EXT4-fs (sda3): recovery complete
[   10.302081] EXT4-fs (sda3): mounted filesystem with ordered data mode. Opts: (null)
[   19.397640] udevd[397]: starting version 173
[   19.424366] bonding: Ethernet Channel Bonding Driver: v3.7.1 (April 27, 2011)
[   19.424376] bonding: Warning: either miimon or arp_interval and arp_ip_target module parameters must be specified, otherwise bonding will not detect link failures! see bonding.txt for details.
[   19.473633] lp: driver loaded but no devices found
[   19.482043] Adding 9667580k swap on /dev/sda2.  Priority:-1 extents:1 across:9667580k 
[   19.486344] type=1400 audit(1332724067.216:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=420 comm="apparmor_parser"
[   19.486890] type=1400 audit(1332724067.216:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=420 comm="apparmor_parser"
[   19.487211] type=1400 audit(1332724067.216:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=420 comm="apparmor_parser"
[   19.535505] bonding: bond0: Setting MII monitoring interval to 100.
[   19.550343] bonding: bond0: setting mode to balance-rr (0).
[   19.575929] ADDRCONF(NETDEV_UP): bond0: link is not ready
[   19.705094] EDAC MC: Ver: 2.1.0
[   19.720667] EDAC MC0: Giving out device to 'i3000_edac' 'i3000': DEV 0000:00:00.0
[   19.721222] EDAC PCI0: Giving out device to module 'i3000_edac' controller 'EDAC PCI controller': DEV '0000:00:00.0' (POLLED)
[   19.743038] Floppy drive(s): fd0 is 1.44M
[   19.763014] EXT4-fs (sda3): re-mounted. Opts: errors=remount-ro
[   20.092333] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   20.229927] intel_rng: FWH not detected
[   20.263584] bonding: bond0: Adding slave eth0.
[   20.325389] bonding: bond0: enslaving eth0 as an active interface with a down link.
[   20.325891] leds_ss4200: no LED devices found
[   20.354083] xgifb: module is from the staging directory, the quality is unknown, you have been warned.
[   20.419403] 
[   20.419406] XGIfb_init_module
[   20.419412] XGIfb: Mode 'none' not supported anymore. Using default.
[   20.419485] XGIfb: Options (null)
[   20.419533] XGIfb: Relocate IO address: bc80 [00000000]
[   20.419554] XGIfb:chipid = 30
[   20.419557] XGIfb: Video ROM usage disabled
[   20.419562] XGIfb: SR14=41 DramSzie 1000000 ChannelNum 1
[   20.447121] bonding: bond0: Adding slave eth1.
[   20.466544] EXT4-fs (md0p1): barriers disabled
[   20.491565] bonding: bond0: enslaving eth1 as an active interface with a down link.
[   20.660789] XGIfb: Framebuffer at 0xfc000000, mapped to 0xffffc90005a80000, size 16384k
[   20.660796] XGIfb: MMIO at 0xfe1c0000, mapped to 0xffffc90006b00000, size 256k
[   20.660800] XGIfb: XGIInitNew() ...12345678910111215171818118218319202122232425OK
[   20.668595] XGIfb: No or unknown bridge type detected
[   20.668603] XGIfb: Default mode is 800x600x16 (60Hz)
[   20.810553] mtrr: type mismatch for fc000000,1000000 old: write-back new: write-combining
[   20.810560] XGIfb: Added MTRRs
[   20.811828] fbcon:  (fb0) is primary device
[   20.813650] XGIfb: var->pixclock=25000, htotal=1056, vtotal=1256
[   20.813655] XGIfb: Change mode to 800x600x16-60Hz
[   20.851110] Console: switching to colour frame buffer device 100x37
[   20.887402] fb0:  frame buffer device, Version 0.8.01
[   21.110328] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   21.146447] EXT4-fs (md0p1): mounted filesystem with ordered data mode. Opts: errors=remount-ro,barrier=0
[   21.288642] init: plymouth-log main process (864) terminated with status 1
[   21.295353] init: plymouth-upstart-bridge main process (867) terminated with status 1
[   21.456726] input: ImExPS/2 Generic Explorer Mouse as /devices/platform/i8042/serio1/input/input2
[   21.537480] scsi_verify_blk_ioctl: 212 callbacks suppressed
[   21.537489] mdadm: sending ioctl 1261 to a partition!
[   21.537495] mdadm: sending ioctl 1261 to a partition!
[   21.657475] mdadm: sending ioctl 1261 to a partition!
[   21.657481] mdadm: sending ioctl 1261 to a partition!
[   21.686563] mdadm: sending ioctl 1261 to a partition!
[   21.686569] mdadm: sending ioctl 1261 to a partition!
[   21.696339] mdadm: sending ioctl 1261 to a partition!
[   21.696346] mdadm: sending ioctl 1261 to a partition!
[   21.705739] mdadm: sending ioctl 1261 to a partition!
[   21.705746] mdadm: sending ioctl 1261 to a partition!
[   22.768032] floppy0: no floppy controllers found
[   22.779807] tg3 0000:04:00.0: eth0: Link is up at 1000 Mbps, full duplex
[   22.779813] tg3 0000:04:00.0: eth0: Flow control is on for TX and on for RX
[   22.796030] bonding: bond0: link status definitely up for interface eth0, 1000 Mbps full duplex.
[   22.797202] ADDRCONF(NETDEV_CHANGE): bond0: link becomes ready
[   22.955782] tg3 0000:05:00.0: eth1: Link is up at 1000 Mbps, full duplex
[   22.955789] tg3 0000:05:00.0: eth1: Flow control is on for TX and on for RX
[   22.996039] bonding: bond0: link status definitely up for interface eth1, 1000 Mbps full duplex.
[   23.240116] bond0: IPv6 duplicate address fe80::214:22ff:fe7b:6be1 detected!
[   23.475660] init: ssh main process (876) terminated with status 255
[   23.535259] init: failsafe main process (902) killed by TERM signal
[   23.573668] type=1400 audit(1332724071.304:5): apparmor="STATUS" operation="profile_load" name="/usr/sbin/mysqld" pid=1122 comm="apparmor_parser"
[   23.574155] type=1400 audit(1332724071.304:6): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1121 comm="apparmor_parser"
[   23.574717] type=1400 audit(1332724071.304:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1121 comm="apparmor_parser"
[   23.575069] type=1400 audit(1332724071.304:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1121 comm="apparmor_parser"
[   23.578001] type=1400 audit(1332724071.308:9): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=1123 comm="apparmor_parser"
[   23.722689] RPC: Registered named UNIX socket transport module.
[   23.722696] RPC: Registered udp transport module.
[   23.722700] RPC: Registered tcp transport module.
[   23.722704] RPC: Registered tcp NFSv4.1 backchannel transport module.
[   23.735319] Installing knfsd (copyright (C) 1996 okir@monad.swb.de).
[   23.961933] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[   23.962493] NFSD: starting 90-second grace period
[   27.615591] init: plymouth-stop pre-start process (1323) terminated with status 1
[  668.659402] init: tty1 main process ended, respawning


```

---

### Post by zorg2 on 2012-04-06
Having cynically watched these forums for years....

I think your question will go unanswered on the Ubuntu forums because the majority of users here lack deep knowledge.  They simply don't know what you are talking about nor why you want to ask your question.  

I advise you ask on the Debian related lists as users are more technically inclined.

I have seen those messages in the logs since Jan 30th on 2.6.nn on Debian 6., which is when I installed this version of Squeeze. Current revision is 2.6.32-5-amd64
   	 	 	 	 	 		 	Jan 30 16:26:51 lsrv01 kernel: [    2.615421] mdadm: sending ioctl 1261 to a partition! ] 
I have not knowlingly seen any data corruption on the server (Its a quiet email server handling some 1,000 messages daily).

[https://lkml.org/lkml/2012/1/28/42](https://lkml.org/lkml/2012/1/28/42)

I know this does not help you a lot.

---

### Post by MakOwner on 2012-04-06
> **zorg2 said:**
> Having cynically watched these forums for years....

I think your question will go unanswered on the Ubuntu forums because the majority of users here lack deep knowledge.  They simply don't know what you are talking about nor why you want to ask your question.  

I advise you ask on the Debian related lists as users are more technically inclined.

I have seen those messages in the logs since Jan 30th on 2.6.nn on Debian 6., which is when I installed this version of Squeeze. Current revision is 2.6.32-5-amd64
   	 	 	 	 	 		 	Jan 30 16:26:51 lsrv01 kernel: [    2.615421] mdadm: sending ioctl 1261 to a partition! ] 
I have not knowlingly seen any data corruption on the server (Its a quiet email server handling some 1,000 messages daily).

[https://lkml.org/lkml/2012/1/28/42](https://lkml.org/lkml/2012/1/28/42)

I know this does not help you a lot.

It's much better than no response - at least I'm not the only one seeing them.  I haven't seen any corruption yet either, so at least we have that going.

Thanks for taking the time to post.

---

### Post by reddevil2064 on 2012-04-06
> **MakOwner said:**
> It's much better than no response - at least I'm not the only one seeing them.  I haven't seen any corruption yet either, so at least we have that going.

Thanks for taking the time to post.

If you back track in that mail list thread you posted, you will see the explanation from Linus as to why they included the warnings and errors. They will be suppressed in the next kernel release.

---

### Post by oregonbob on 2013-04-09
I had a 10.04 Lucid server crash after two years of running. It would not reboot, just hanged at initramfs prompt. I got it to boot with fsck of root filesystem, but now it logs messages:

**kernel: [208837.597358] grub-probe: sending ioctl 1261 to a partition!**

Repeatedly. As you said, Googling doesn't provide any clear solutions.

---

### Post by MakOwner on 2013-04-09
Yea, I guess someone forgot to suppress those message because I still sometimes see them when doing upgrades --  I only see this on servers wehre I run mdadm RAID.  I do hate being the only google result.

---

### Post by rickyrockrat on 2013-11-30
Might have a look over here.
[https://bbs.archlinux.org/viewtopic.php?id=142495](https://bbs.archlinux.org/viewtopic.php?id=142495)
I'm just now seeing this on a new RAID. If I figure anything out, I'll post back here.

---

