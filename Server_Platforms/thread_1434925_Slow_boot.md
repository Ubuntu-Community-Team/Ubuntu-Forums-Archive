---
title: "Slow boot"
date: 2010-03-20
forum: Server Platforms
---

### Post by ris8 on 2010-03-20
I was updating my e1000e (intel gigabit module) and my server became very slow to boot. I have since rolled back the module, but boot time has not changed... anybody has any idea what may be going on? Or how I can get a more detailed dmesg to know what happends?

Excerpt from latest boot dmesg:
```
[    5.362573] e1000e: Intel(R) PRO/1000 Network Driver - 1.0.2-k2
[    5.362576] e1000e: Copyright (c) 1999-2008 Intel Corporation.
[    5.362673] e1000e 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    5.362708] e1000e 0000:02:00.0: setting latency timer to 64
[    5.362868]   alloc irq_desc for 29 on node 0
[    5.362870]   alloc kstat_irqs on node 0
[    5.362888] e1000e 0000:02:00.0: irq 29 for MSI/MSI-X
[    5.375426] Floppy drive(s): fd0 is 1.44M
[    5.393794] FDC 0 is a post-1991 82077
[    5.407033] ohci1394 0000:05:03.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    5.407040] ohci1394 0000:05:03.0: setting latency timer to 64
[    5.419285] device-mapper: dm-raid45: initialized v0.2594b
[    5.427852] md: linear personality registered for level -1
[    5.429794] md: multipath personality registered for level -4
[    5.431537] md: raid0 personality registered for level 0
[    5.434278] md: raid1 personality registered for level 1
[    5.435947] async_tx: api initialized (async)
[    5.462066] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[fd9ff000-fd9ff7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[    5.573113] 0000:02:00.0: eth0: (PCI Express:2.5GB/s:Width x1) 00:15:17:c7:b3:e5
[    5.573116] 0000:02:00.0: eth0: Intel(R) PRO/1000 Network Connection
[    5.573201] 0000:02:00.0: eth0: MAC: 1, PHY: 4, PBA No: d50861-003
[    5.600002] raid6: int64x1   1687 MB/s
[    5.672459] md: bind<sda1>
[    5.687799] md: bind<sdb1>
[    5.692850] md: bind<sdd1>
[    5.770024] raid6: int64x2   2250 MB/s
[    5.898308] md: bind<sdc1>
[    5.913195] md: raid10 personality registered for level 10
[    5.913480] raid10: raid set md0 active with 4 out of 4 devices
[    5.913504] md0: detected capacity change from 0 to 2000404348928
[    5.914690]  md0: unknown partition table
[    5.940016] raid6: int64x4   1588 MB/s
[    6.110006] raid6: int64x8   1467 MB/s
[    6.280010] raid6: sse2x1    3268 MB/s
[    6.450004] raid6: sse2x2    4412 MB/s
[    6.620004] raid6: sse2x4    6385 MB/s
[    6.620005] raid6: using algorithm sse2x4 (6385 MB/s)
[    6.622514] md: raid6 personality registered for level 6
[    6.622517] md: raid5 personality registered for level 5
[    6.622519] md: raid4 personality registered for level 4
[    6.780178] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[000129200005c346]
[    6.994683] PM: Starting manual resume from disk
[    6.994686] PM: Resume from partition 8:101
[    6.994688] PM: Checking hibernation image.
[    6.994798] PM: Resume from disk failed.
[    7.033018] kjournald starting.  Commit interval 5 seconds
[    7.033025] EXT3-fs: mounted filesystem with writeback data mode.
[    7.809448] type=1505 audit(1269127427.656:2): operation="profile_load" pid=471 name=/sbin/dhclient3
[    7.810227] type=1505 audit(1269127427.666:3): operation="profile_load" pid=471 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    7.810592] type=1505 audit(1269127427.666:4): operation="profile_load" pid=471 name=/usr/lib/connman/scripts/dhclient-script
[    7.815667] type=1505 audit(1269127427.666:5): operation="profile_load" pid=472 name=/usr/bin/virt-aa-helper
[    7.883601] type=1505 audit(1269127427.735:6): operation="profile_load" pid=473 name=/usr/sbin/libvirtd
[    7.902710] type=1505 audit(1269127427.756:7): operation="profile_load" pid=474 name=/usr/sbin/mysqld
[    7.927820] type=1505 audit(1269127427.776:8): operation="profile_load" pid=475 name=/usr/sbin/tcpdump
[  256.244278] Adding 9936160k swap on /dev/sdg5.  Priority:-1 extents:1 across:9936160k 
[  256.483566] udev: starting version 147
[  256.749345] udev: renamed network interface eth0 to eth2
[  257.039211] EDAC MC: Ver: 2.1.0 Mar 12 2010
[  257.039302] intel_rng: FWH not detected
[  257.041541] EDAC i82975x: ECC disabled on both channels.
[  257.069551] parport_pc 00:09: reported by Plug and Play ACPI
[  257.069612] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[  257.077176] ip_tables: (C) 2000-2006 Netfilter Core Team
[  257.079649] lp: driver loaded but no devices found
[  257.087650] ppdev: user-space parallel port driver
[  257.111308] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[  257.111360] HDA Intel 0000:00:1b.0: setting latency timer to 64
[  257.150373] lp0: using parport0 (interrupt-driven).
[  257.237377] hda_codec: Unknown model for ALC882, trying auto-probe from BIOS...
[  257.237554] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input4
[  257.671857] EXT3 FS on sdg1, internal journal
[  258.108316] Bridge firewalling registered
[  258.110749] device eth2 entered promiscuous mode
[  258.290248] e1000e 0000:02:00.0: irq 29 for MSI/MSI-X
[  258.350187] e1000e 0000:02:00.0: irq 29 for MSI/MSI-X
[  258.351446] ADDRCONF(NETDEV_UP): eth2: link is not ready
[  258.752654] type=1505 audit(1269127678.606:9): operation="profile_replace" pid=1158 name=/sbin/dhclient3
[  258.753501] type=1505 audit(1269127678.606:10): operation="profile_replace" pid=1158 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[  258.753867] type=1505 audit(1269127678.606:11): operation="profile_replace" pid=1158 name=/usr/lib/connman/scripts/dhclient-script
[  258.775388] type=1505 audit(1269127678.626:12): operation="profile_replace" pid=1159 name=/usr/bin/virt-aa-helper
[  258.897826] kjournald starting.  Commit interval 5 seconds
[  258.898342] EXT3 FS on sde1, internal journal
[  258.898348] EXT3-fs: mounted filesystem with writeback data mode.
[  258.993400] type=1505 audit(1269127678.846:13): operation="profile_replace" pid=1160 name=/usr/sbin/libvirtd
[  258.998345] kjournald starting.  Commit interval 5 seconds
[  259.007606] EXT3 FS on md0, internal journal
[  259.007613] EXT3-fs: mounted filesystem with writeback data mode.
[  259.020670] type=1505 audit(1269127678.876:14): operation="profile_replace" pid=1168 name=/usr/sbin/mysqld
[  259.037458] type=1505 audit(1269127678.886:15): operation="profile_replace" pid=1172 name=/usr/sbin/tcpdump
[  259.917625] type=1503 audit(1269127679.766:16): operation="open" pid=1389 parent=1388 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[  259.974493] type=1503 audit(1269127679.826:17): operation="open" pid=1409 parent=1408 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[  260.033131] type=1503 audit(1269127679.885:18): operation="open" pid=1524 parent=1416 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
[  260.981037] e1000e: eth2 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: RX/TX
[  260.981975] ADDRCONF(NETDEV_CHANGE): eth2: link becomes ready
[  260.982187] br0: port 1(eth2) entering forwarding state
[  263.841815] virbr0: starting userspace STP failed, starting kernel STP
[  264.115398] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[  264.115628] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Please use
[  264.115631] nf_conntrack.acct=1 kernel parameter, acct=1 nf_conntrack module option or
[  264.115633] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
[  264.721340] __ratelimit: 6 callbacks suppressed
[  264.721343] type=1505 audit(1269127684.575:21): operation="profile_load" pid=2339 name=libvirt-8161eb7e-0493-b92f-2ba8-8dad57b9c48b
[  264.754629] tun: Universal TUN/TAP device driver, 1.6
[  264.754632] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[  264.755666] device vnet0 entered promiscuous mode
[  264.756624] br0: port 2(vnet0) entering forwarding state
[  265.053614] lo: Disabled Privacy Extensions
[  271.000009] eth2: no IPv6 routers present
[  273.177356] kvm: emulating exchange as write
[  275.161257] vnet0: no IPv6 routers present

```


Excerpt from last good boot dmesg:
```
Mar 18 19:33:49 SERVER02 kernel: [    5.298549] e1000e: Intel(R) PRO/1000 Network Driver - 1.0.2-k2
Mar 18 19:33:49 SERVER02 kernel: [    5.298553] e1000e: Copyright (c) 1999-2008 Intel Corporation.
Mar 18 19:33:49 SERVER02 kernel: [    5.299758] e1000e 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Mar 18 19:33:49 SERVER02 kernel: [    5.299794] e1000e 0000:02:00.0: setting latency timer to 64
Mar 18 19:33:49 SERVER02 kernel: [    5.299955]   alloc irq_desc for 29 on node 0
Mar 18 19:33:49 SERVER02 kernel: [    5.299958]   alloc kstat_irqs on node 0
Mar 18 19:33:49 SERVER02 kernel: [    5.299976] e1000e 0000:02:00.0: irq 29 for MSI/MSI-X
Mar 18 19:33:49 SERVER02 kernel: [    5.311170] Floppy drive(s): fd0 is 1.44M
Mar 18 19:33:49 SERVER02 kernel: [    5.317128] xor: automatically using best checksumming function: generic_sse
Mar 18 19:33:49 SERVER02 kernel: [    5.360008]    generic_sse:  7783.200 MB/sec
Mar 18 19:33:49 SERVER02 kernel: [    5.360011] xor: using function: generic_sse (7783.200 MB/sec)
Mar 18 19:33:49 SERVER02 kernel: [    5.360691] FDC 0 is a post-1991 82077
Mar 18 19:33:49 SERVER02 kernel: [    5.369116] ohci1394 0000:05:03.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
Mar 18 19:33:49 SERVER02 kernel: [    5.369123] ohci1394 0000:05:03.0: setting latency timer to 64
Mar 18 19:33:49 SERVER02 kernel: [    5.378808] device-mapper: dm-raid45: initialized v0.2594b
Mar 18 19:33:49 SERVER02 kernel: [    5.390466] md: linear personality registered for level -1
Mar 18 19:33:49 SERVER02 kernel: [    5.392466] md: multipath personality registered for level -4
Mar 18 19:33:49 SERVER02 kernel: [    5.394460] md: raid0 personality registered for level 0
Mar 18 19:33:49 SERVER02 kernel: [    5.397019] md: raid1 personality registered for level 1
Mar 18 19:33:49 SERVER02 kernel: [    5.398611] async_tx: api initialized (async)
Mar 18 19:33:49 SERVER02 kernel: [    5.432041] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[19]  MMIO=[fd9ff000-fd9ff7ff]  Max Packet=[2048]  IR/IT contexts=[4/8]
Mar 18 19:33:49 SERVER02 kernel: [    5.480386] md: bind<sdd1>
Mar 18 19:33:49 SERVER02 kernel: [    5.492609] md: bind<sdc1>
Mar 18 19:33:49 SERVER02 kernel: [    5.538630] md: bind<sda1>
Mar 18 19:33:49 SERVER02 kernel: [    5.570039] raid6: int64x1   1685 MB/s
Mar 18 19:33:49 SERVER02 kernel: [    5.573093] 0000:02:00.0: eth0: (PCI Express:2.5GB/s:Width x1) 00:15:17:c7:b3:e5
Mar 18 19:33:49 SERVER02 kernel: [    5.573096] 0000:02:00.0: eth0: Intel(R) PRO/1000 Network Connection
Mar 18 19:33:49 SERVER02 kernel: [    5.573180] 0000:02:00.0: eth0: MAC: 1, PHY: 4, PBA No: d50861-003
Mar 18 19:33:49 SERVER02 kernel: [    5.738634] md: bind<sdb1>
Mar 18 19:33:49 SERVER02 kernel: [    5.740022] raid6: int64x2   2258 MB/s
Mar 18 19:33:49 SERVER02 kernel: [    5.741630] md: raid10 personality registered for level 10
Mar 18 19:33:49 SERVER02 kernel: [    5.741911] raid10: raid set md0 active with 4 out of 4 devices
Mar 18 19:33:49 SERVER02 kernel: [    5.741936] md0: detected capacity change from 0 to 2000404348928
Mar 18 19:33:49 SERVER02 kernel: [    5.743046]  md0: unknown partition table
Mar 18 19:33:49 SERVER02 kernel: [    5.910032] raid6: int64x4   1592 MB/s
Mar 18 19:33:49 SERVER02 kernel: [    6.080018] raid6: int64x8   1467 MB/s
Mar 18 19:33:49 SERVER02 kernel: [    6.250011] raid6: sse2x1    3268 MB/s
Mar 18 19:33:49 SERVER02 kernel: [    6.420008] raid6: sse2x2    4414 MB/s
Mar 18 19:33:49 SERVER02 kernel: [    6.590003] raid6: sse2x4    6392 MB/s
Mar 18 19:33:49 SERVER02 kernel: [    6.590005] raid6: using algorithm sse2x4 (6392 MB/s)
Mar 18 19:33:49 SERVER02 kernel: [    6.592513] md: raid6 personality registered for level 6
Mar 18 19:33:49 SERVER02 kernel: [    6.592516] md: raid5 personality registered for level 5
Mar 18 19:33:49 SERVER02 kernel: [    6.592518] md: raid4 personality registered for level 4
Mar 18 19:33:49 SERVER02 kernel: [    6.750283] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[000129200005c346]
Mar 18 19:33:49 SERVER02 kernel: [    6.978389] PM: Starting manual resume from disk
Mar 18 19:33:49 SERVER02 kernel: [    6.978392] PM: Resume from partition 8:101
Mar 18 19:33:49 SERVER02 kernel: [    6.978394] PM: Checking hibernation image.
Mar 18 19:33:49 SERVER02 kernel: [    6.978505] PM: Resume from disk failed.
Mar 18 19:33:49 SERVER02 kernel: [    7.012087] kjournald starting.  Commit interval 5 seconds
Mar 18 19:33:49 SERVER02 kernel: [    7.012094] EXT3-fs: mounted filesystem with writeback data mode.
Mar 18 19:33:49 SERVER02 kernel: [    7.771774] type=1505 audit(1268955224.626:2): operation="profile_load" pid=496 name=/sbin/dhclient3
Mar 18 19:33:49 SERVER02 kernel: [    7.772547] type=1505 audit(1268955224.626:3): operation="profile_load" pid=496 name=/usr/lib/NetworkManager/nm-dhcp-client.action
Mar 18 19:33:49 SERVER02 kernel: [    7.772910] type=1505 audit(1268955224.626:4): operation="profile_load" pid=496 name=/usr/lib/connman/scripts/dhclient-script
Mar 18 19:33:49 SERVER02 kernel: [    7.777997] type=1505 audit(1268955224.626:5): operation="profile_load" pid=497 name=/usr/bin/virt-aa-helper
Mar 18 19:33:49 SERVER02 kernel: [    7.845804] type=1505 audit(1268955224.696:6): operation="profile_load" pid=498 name=/usr/sbin/libvirtd
Mar 18 19:33:49 SERVER02 kernel: [    7.865029] type=1505 audit(1268955224.716:7): operation="profile_load" pid=499 name=/usr/sbin/mysqld
Mar 18 19:33:49 SERVER02 kernel: [    7.890143] type=1505 audit(1268955224.746:8): operation="profile_load" pid=500 name=/usr/sbin/tcpdump
Mar 18 19:33:49 SERVER02 kernel: [    8.919866] Adding 9936160k swap on /dev/sdg5.  Priority:-1 extents:1 across:9936160k 
Mar 18 19:33:49 SERVER02 kernel: [    9.295315] EXT3 FS on sdg1, internal journal
Mar 18 19:33:49 SERVER02 kernel: [    9.897096] udev: starting version 147
Mar 18 19:33:49 SERVER02 kernel: [   10.552378] udev: renamed network interface eth0 to eth2
Mar 18 19:33:49 SERVER02 kernel: [   11.905715] kjournald starting.  Commit interval 5 seconds
Mar 18 19:33:49 SERVER02 kernel: [   11.906247] EXT3 FS on sdf1, internal journal
Mar 18 19:33:49 SERVER02 kernel: [   11.906253] EXT3-fs: mounted filesystem with writeback data mode.
Mar 18 19:33:49 SERVER02 kernel: [   11.917289] EDAC MC: Ver: 2.1.0 Mar 12 2010
Mar 18 19:33:49 SERVER02 kernel: [   11.929450] kjournald starting.  Commit interval 5 seconds
Mar 18 19:33:49 SERVER02 kernel: [   11.954296] EXT3 FS on md0, internal journal
Mar 18 19:33:49 SERVER02 kernel: [   11.954303] EXT3-fs: mounted filesystem with writeback data mode.
Mar 18 19:33:49 SERVER02 kernel: [   11.984165] parport_pc 00:09: reported by Plug and Play ACPI
Mar 18 19:33:49 SERVER02 kernel: [   11.984227] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
Mar 18 19:33:49 SERVER02 kernel: [   11.988047] intel_rng: FWH not detected
Mar 18 19:33:49 SERVER02 kernel: [   11.991206] lp: driver loaded but no devices found
Mar 18 19:33:49 SERVER02 kernel: [   11.991495] EDAC i82975x: ECC disabled on both channels.
Mar 18 19:33:49 SERVER02 kernel: [   12.061489] lp0: using parport0 (interrupt-driven).
Mar 18 19:33:49 SERVER02 kernel: [   12.201618] ppdev: user-space parallel port driver
Mar 18 19:33:49 SERVER02 kernel: [   12.318752] ip_tables: (C) 2000-2006 Netfilter Core Team
Mar 18 19:33:48 SERVER02 rsyslogd-2039: Could no open output file '/dev/xconsole' [try http://www.rsyslog.com/e/2039 ]
Mar 18 19:33:49 SERVER02 kernel: [   12.829367] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Mar 18 19:33:49 SERVER02 kernel: [   12.829432] HDA Intel 0000:00:1b.0: setting latency timer to 64
Mar 18 19:33:49 SERVER02 kernel: [   13.137672] hda_codec: Unknown model for ALC882, trying auto-probe from BIOS...
Mar 18 19:33:49 SERVER02 kernel: [   13.137851] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input3
Mar 18 19:33:51 SERVER02 kernel: [   15.041678] type=1505 audit(1268955231.896:9): operation="profile_replace" pid=1117 name=/sbin/dhclient3
Mar 18 19:33:51 SERVER02 kernel: [   15.042357] type=1505 audit(1268955231.896:10): operation="profile_replace" pid=1117 name=/usr/lib/NetworkManager/nm-dhcp-client.action
Mar 18 19:33:51 SERVER02 kernel: [   15.042722] type=1505 audit(1268955231.896:11): operation="profile_replace" pid=1117 name=/usr/lib/connman/scripts/dhclient-script
Mar 18 19:33:51 SERVER02 kernel: [   15.044318] type=1505 audit(1268955231.896:12): operation="profile_replace" pid=1118 name=/usr/bin/virt-aa-helper
Mar 18 19:33:51 SERVER02 kernel: [   15.123712] type=1505 audit(1268955231.976:13): operation="profile_replace" pid=1119 name=/usr/sbin/libvirtd
Mar 18 19:33:51 SERVER02 kernel: [   15.125586] type=1505 audit(1268955231.976:14): operation="profile_replace" pid=1124 name=/usr/sbin/mysqld
Mar 18 19:33:51 SERVER02 kernel: [   15.127550] type=1505 audit(1268955231.976:15): operation="profile_replace" pid=1125 name=/usr/sbin/tcpdump
Mar 18 19:33:53 SERVER02 kernel: [   16.356923] Bridge firewalling registered
Mar 18 19:33:53 SERVER02 kernel: [   16.359261] device eth2 entered promiscuous mode
Mar 18 19:33:53 SERVER02 kernel: [   16.530311] e1000e 0000:02:00.0: irq 29 for MSI/MSI-X
Mar 18 19:33:53 SERVER02 kernel: [   16.590166] e1000e 0000:02:00.0: irq 29 for MSI/MSI-X
Mar 18 19:33:53 SERVER02 kernel: [   16.591431] ADDRCONF(NETDEV_UP): eth2: link is not ready
Mar 18 19:33:53 SERVER02 init: apport pre-start process (1341) terminated with status 1
Mar 18 19:33:53 SERVER02 init: apport post-stop process (1366) terminated with status 1
Mar 18 19:33:53 SERVER02 cron[1348]: (CRON) INFO (pidfile fd = 3)
Mar 18 19:33:53 SERVER02 cron[1375]: (CRON) STARTUP (fork ok)
Mar 18 19:33:54 SERVER02 cron[1375]: (CRON) INFO (Running @reboot jobs)
Mar 18 19:33:54 SERVER02 kernel: [   17.979551] type=1503 audit(1268955234.827:16): operation="open" pid=1422 parent=1421 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
Mar 18 19:33:55 SERVER02 kernel: [   18.213794] type=1503 audit(1268955235.066:17): operation="open" pid=1446 parent=1445 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
Mar 18 19:33:55 SERVER02 mysqld_safe: Starting mysqld daemon with databases from /var/lib/mysql
Mar 18 19:33:55 SERVER02 kernel: [   18.382094] type=1503 audit(1268955235.236:18): operation="open" pid=1561 parent=1453 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
Mar 18 19:33:55 SERVER02 mysqld: 100318 19:33:55 [Note] Plugin 'FEDERATED' is disabled.
Mar 18 19:33:55 SERVER02 mysqld: 100318 19:33:55  InnoDB: Started; log sequence number 0 43655
Mar 18 19:33:55 SERVER02 mysqld: 100318 19:33:55 [Note] Event Scheduler: Loaded 0 events
Mar 18 19:33:55 SERVER02 mysqld: 100318 19:33:55 [Note] /usr/sbin/mysqld: ready for connections.
Mar 18 19:33:55 SERVER02 mysqld: Version: '5.1.37-1ubuntu5.1'  socket: '/var/run/mysqld/mysqld.sock'  port: 3306  (Ubuntu)
Mar 18 19:33:56 SERVER02 kernel: [   19.191033] e1000e: eth2 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: RX/TX
Mar 18 19:33:56 SERVER02 kernel: [   19.191948] ADDRCONF(NETDEV_CHANGE): eth2: link becomes ready
Mar 18 19:33:56 SERVER02 kernel: [   19.192161] br0: port 1(eth2) entering forwarding state
```

How do I find out what is going in the 5 minutes that the boot hangs?

Thanks!

---

### Post by ris8 on 2010-03-21
A quick comparison of the 2 boot logs, these are the only lines that are in the new log but not in the old:

```

virbr0: starting userspace STP failed, starting kernel STP
nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Please use
nf_conntrack.acct=1 kernel parameter, acct=1 nf_conntrack module option or
sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
__ratelimit: 6 callbacks suppressed

```

This is different:
```

OLD:
input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input3
NEW:
input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input4

```

This disappeared (i.e., was there, not any more):
```

xor: automatically using best checksumming function: generic_sse
generic_sse:  7783.200 MB/sec
xor: using function: generic_sse (7783.200 MB/sec)

```

Not sure why I am starting to get STP messages, though, as STP is off in my /etc/network/interfaces (and it has not changed in a while):

```

auto eth2
iface eth2 inet manual
      MTU 9000

auto br0
iface br0 inet static
      	address x.x.x.x
	netmask x.x.x.x
	gateway x.x.x.x
	broadcast x.x.x.x
        bridge_ports eth2
        bridge_fd 0
	bridge_maxwait 5
        bridge_stp off

```

I guess I will experiment with the bridge options... any other idea?

Thanks

---

### Post by smc18 on 2010-03-21
How weird. I was just reading earlier today on how certain daemons (Sendmail, Apache, Samba) cause a slow boot if the kernel cannot resolve the host name to an IP address, it just waits until it times out.

FYI, I'm not going to be a real amount of help but;
 
Do you have any of the above daemons running?  AND
Is there any reason /etc/resolv.conf does not have your DNS server listed? OR
In /etc/hosts your station's hostname is not listed?

---

### Post by ris8 on 2010-03-21
Worth a shot... my resolv.conf seems innocuous:

```

domain nyc.rr.com
search nyc.rr.com
nameserver 192.168.100.1

```

But my hosts has my server (SERVER02) under 127.0.1.1... ? Should I remove it? Put it as 127.0.0.1? Or put it to its static IP?

```

127.0.0.1	localhost
127.0.1.1	SERVER02.nyc.rr.com	SERVER02

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

I'll play around after I am done with the SMART self-tests on all disks...

Thanks

---

### Post by ris8 on 2010-03-21
I tried a few different things for the hosts, no luck.

I installed the bootchart package. Interestingly the first boot after installing the package was a quick one (first time since I started the thread!). Unfortunately the second was back to 5+ minutes.
I tried uploading the png files, but they are too large to attach... (the attached files are not readable)
As a summary, in the slow boot, there are 5 processes that stick around way longer than the others (essentially they start in the first few secs and never stop):
[LIST]
[*]init
[*]collector
[*]ureadahead
[*]kthreadd
[*]kswapd0
[/LIST]
Moreover, disk throughput is fairly constant at 70 MB/sec, and 1 core idle, the other spending 100% in I/O (waiting).
Any idea? something happening with the swap file?

Thanks

---

