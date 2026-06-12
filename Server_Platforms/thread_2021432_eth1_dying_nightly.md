---
title: "eth1 dying nightly"
date: 2012-07-09
forum: Server Platforms
---

### Post by jwright8 on 2012-07-09
I have a system with two NICs.  One, eth0, is a PCI network card.  The other, eth1, is on-board.  I have them set in a bridge configuration, br0, with OpenVPN (tap0 interface) and IPTables; nothing else, besides Snort/Denyhosts/Tiger, is on the system.  The setup I have is as follows:

Remote client for VPN -> Internet -> Router with port forwarded -> Ubuntu server 10.04LTS (the one in question) -> LAN clients (Windows machines)

Here is my ifconfig:

```


root@Alatheia:/var/log# ifconfig
br0       Link encap:Ethernet  HWaddr 00:1e:90:38:25:11
          inet addr:10.1.10.70  Bcast:10.1.10.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:90ff:fe38:2511/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13062 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4306 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:13923492 (13.9 MB)  TX bytes:326246 (326.2 KB)

eth0      Link encap:Ethernet  HWaddr e0:46:9a:2b:bc:ca
          inet6 addr: fe80::e246:9aff:fe2b:bcca/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:118458 errors:0 dropped:0 overruns:0 frame:0
          TX packets:326 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:47146625 (47.1 MB)  TX bytes:33301 (33.3 KB)
          Interrupt:19 Base address:0x2000

eth1      Link encap:Ethernet  HWaddr 00:1e:90:38:25:11
          inet6 addr: fe80::21e:90ff:fe38:2511/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9661 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8558 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:13817616 (13.8 MB)  TX bytes:763035 (763.0 KB)
          Interrupt:16

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

tap0      Link encap:Ethernet  HWaddr 66:a2:3a:97:45:75
          inet6 addr: fe80::64a2:3aff:fe97:4575/64 Scope:Link
          UP BROADCAST RUNNING PROMISC MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3713 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100
          RX bytes:0 (0.0 B)  TX bytes:359951 (359.9 KB)

```Onto the problem.  Every night (since Friday night/Saturday morning) the machine would stop responding to SSH/OpenVPN connections.  After rebooting the machine, it would be fine until the next night/morning, and it would stop accepting connections again.  Looking at the logs, it seems as if the system itself is fine, but the eth1 (the on-board one) is giving problems.  

While my first instinct is to say the NIC is bad, I really don't think that's the case here.  In spite of that, though, I'm going to go get another PCI NIC today and put it in the box and configure br0 to eth0 + eth2 (new card I am presuming).

This is pasted from the syslog:
```

Jul  8 12:35:21 Alatheia snort[1205]:         --== Initialization Complete ==--
Jul  8 12:35:21 Alatheia snort[1205]: Snort initialization completed successfully (pid=1205)
Jul  8 12:35:21 Alatheia snort[1205]: Not Using PCAP_FRAMES
Jul  8 12:35:25 Alatheia kernel: [   24.892011] eth0: no IPv6 routers present
Jul  8 12:35:26 Alatheia kernel: [   25.232009] br0: no IPv6 routers present
Jul  8 12:35:28 Alatheia kernel: [   27.356013] eth1: no IPv6 routers present
Jul  8 12:35:28 Alatheia kernel: [   27.432509] tap0: no IPv6 routers present
Jul  8 12:35:30 Alatheia kernel: [   29.532029] br0: port 2(eth0) entering forwarding state
Jul  8 12:35:32 Alatheia kernel: [   31.768012] br0: port 3(tap0) entering forwarding state
Jul  8 12:35:32 Alatheia kernel: [   31.804016] br0: port 1(eth1) entering forwarding state
Jul  8 12:35:33 Alatheia init: ssh main process (1030) terminated with status 255
Jul  8 12:35:35 Alatheia ntpdate[1316]: step time server 91.189.94.4 offset 1.392620 sec
Jul  8 12:43:24 Alatheia kernel: [  502.000028] ------------[ cut here ]------------
Jul  8 12:43:24 Alatheia kernel: [  502.000047] WARNING: at /build/buildd/linux-2.6.32/net/sched/sch_generic.c:261 dev_watchdog+0x1fe/0x210()
Jul  8 12:43:24 Alatheia kernel: [  502.000052] Hardware name: E2610
Jul  8 12:43:24 Alatheia kernel: [  502.000055] NETDEV WATCHDOG: eth1 (tg3): transmit queue 0 timed out
Jul  8 12:43:24 Alatheia kernel: [  502.000058] Modules linked in: sha256_generic aes_i586 aes_generic dm_crypt bridge stp snd_hda_codec_realtek$
Jul  8 12:43:24 Alatheia kernel: [  502.000116] Pid: 0, comm: swapper Not tainted 2.6.32-41-generic-pae #91-Ubuntu
Jul  8 12:43:24 Alatheia kernel: [  502.000119] Call Trace:
Jul  8 12:43:24 Alatheia kernel: [  502.000129]  [<c0154e82>] warn_slowpath_common+0x72/0xa0
Jul  8 12:43:24 Alatheia kernel: [  502.000136]  [<c050287e>] ? dev_watchdog+0x1fe/0x210
Jul  8 12:43:24 Alatheia kernel: [  502.000141]  [<c050287e>] ? dev_watchdog+0x1fe/0x210
Jul  8 12:43:24 Alatheia kernel: [  502.000147]  [<c0154efb>] warn_slowpath_fmt+0x2b/0x30
Jul  8 12:43:24 Alatheia kernel: [  502.000152]  [<c050287e>] dev_watchdog+0x1fe/0x210
Jul  8 12:43:24 Alatheia kernel: [  502.000159]  [<c016424c>] ? lock_timer_base+0x2c/0x60
Jul  8 12:43:24 Alatheia kernel: [  502.000164]  [<c01650f2>] ? mod_timer+0x102/0x1e0
Jul  8 12:43:24 Alatheia kernel: [  502.000170]  [<c01649ee>] run_timer_softirq+0x13e/0x2c0
Jul  8 12:43:24 Alatheia kernel: [  502.000177]  [<c017fef4>] ? tick_dev_program_event+0x74/0xd0
Jul  8 12:43:24 Alatheia kernel: [  502.000183]  [<c0502680>] ? dev_watchdog+0x0/0x210
Jul  8 12:43:24 Alatheia kernel: [  502.000188]  [<c015bc88>] __do_softirq+0x98/0x1b0
Jul  8 12:43:24 Alatheia kernel: [  502.000195]  [<c0180340>] ? tick_do_update_jiffies64+0x120/0x170
Jul  8 12:43:24 Alatheia kernel: [  502.000201]  [<c015bde5>] do_softirq+0x45/0x50
Jul  8 12:43:24 Alatheia kernel: [  502.000205]  [<c015bf35>] irq_exit+0x65/0x70
Jul  8 12:43:24 Alatheia kernel: [  502.000212]  [<c05bc58c>] smp_apic_timer_interrupt+0x5c/0x8b
Jul  8 12:43:24 Alatheia kernel: [  502.000219]  [<c010a1d1>] apic_timer_interrupt+0x31/0x40
Jul  8 12:43:24 Alatheia kernel: [  502.000226]  [<c0111045>] ? mwait_idle+0x55/0xa0
Jul  8 12:43:24 Alatheia kernel: [  502.000232]  [<c01085a4>] cpu_idle+0x94/0xd0
Jul  8 12:43:24 Alatheia kernel: [  502.000239]  [<c05a3ed2>] rest_init+0x62/0x70
Jul  8 12:43:24 Alatheia kernel: [  502.000245]  [<c07ea90c>] start_kernel+0x356/0x35c
Jul  8 12:43:24 Alatheia kernel: [  502.000251]  [<c07ea3e2>] ? unknown_bootoption+0x0/0x19e
Jul  8 12:43:24 Alatheia kernel: [  502.000257]  [<c07ea0bb>] i386_start_kernel+0xaa/0xb1
Jul  8 12:43:24 Alatheia kernel: [  502.000261] ---[ end trace df1232be1107471d ]---
Jul  8 12:43:24 Alatheia kernel: [  502.000264] tg3: eth1: transmit timed out, resetting
Jul  8 12:43:24 Alatheia kernel: [  502.000315] tg3: DEBUG: MAC_TX_STATUS[ffffffff] MAC_RX_STATUS[ffffffff]
Jul  8 12:43:24 Alatheia kernel: [  502.000373] tg3: DEBUG: RDMAC_STATUS[ffffffff] WDMAC_STATUS[ffffffff]
Jul  8 12:43:24 Alatheia kernel: [  502.103756] tg3: tg3_stop_block timed out, ofs=2c00 enable_bit=2
Jul  8 12:43:24 Alatheia kernel: [  502.204229] tg3: tg3_stop_block timed out, ofs=2000 enable_bit=2
Jul  8 12:43:24 Alatheia kernel: [  502.304714] tg3: tg3_stop_block timed out, ofs=2400 enable_bit=2
Jul  8 12:43:24 Alatheia kernel: [  502.405195] tg3: tg3_stop_block timed out, ofs=2800 enable_bit=2
Jul  8 12:43:24 Alatheia kernel: [  502.505666] tg3: tg3_stop_block timed out, ofs=3000 enable_bit=2
Jul  8 12:43:24 Alatheia kernel: [  502.606837] tg3: tg3_stop_block timed out, ofs=1400 enable_bit=2
Jul  8 12:43:25 Alatheia kernel: [  502.707326] tg3: tg3_stop_block timed out, ofs=1800 enable_bit=2
Jul  8 12:43:25 Alatheia kernel: [  502.807805] tg3: tg3_stop_block timed out, ofs=c00 enable_bit=2
Jul  8 12:43:25 Alatheia kernel: [  502.908276] tg3: tg3_stop_block timed out, ofs=4800 enable_bit=2
Jul  8 12:43:25 Alatheia kernel: [  503.008747] tg3: tg3_stop_block timed out, ofs=1000 enable_bit=2
Jul  8 12:43:25 Alatheia kernel: [  503.109217] tg3: tg3_stop_block timed out, ofs=1c00 enable_bit=2
Jul  8 12:43:25 Alatheia kernel: [  503.209737] tg3: tg3_abort_hw timed out for eth1, TX_MODE_ENABLE will not clear MAC_TX_MODE=ffffffff
Jul  8 12:43:25 Alatheia kernel: [  503.310233] tg3: tg3_stop_block timed out, ofs=3c00 enable_bit=2
Jul  8 12:43:25 Alatheia kernel: [  503.410704] tg3: tg3_stop_block timed out, ofs=4c00 enable_bit=2
Jul  8 12:43:27 Alatheia kernel: [  504.783824] tg3: eth1: No firmware running.
Jul  8 12:43:28 Alatheia kernel: [  505.989183] tg3: tg3_abort_hw timed out for eth1, TX_MODE_ENABLE will not clear MAC_TX_MODE=ffffffff
Jul  8 12:43:41 Alatheia kernel: [  519.375630] tg3: eth1: Link is down.
Jul  8 12:43:41 Alatheia kernel: [  519.440187] br0: port 1(eth1) entering disabled state
Jul  8 13:00:01 Alatheia CRON[1338]: (root) CMD (   test -x /usr/sbin/tigercron && { [ -r "$DEFAULT" ] && . "$DEFAULT" ; nice -n$NICETIGER /usr/$
Jul  8 13:17:01 Alatheia CRON[1445]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul  8 13:36:29 Alatheia kernel: imklog 4.2.0, log source = /proc/kmsg started.

```Out of curiosity, I've tried removing snort and tiger. The problem still persists.

Another instance of the problem in the syslog:

```

Jul  8 14:20:46 Alatheia kernel: [   70.115413] ip_tables: (C) 2000-2006 Netfilter Core Team
Jul  8 14:20:46 Alatheia kernel: [   70.137234] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
Jul  8 14:20:46 Alatheia kernel: [   70.137866] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Please use
Jul  8 14:20:46 Alatheia kernel: [   70.137872] nf_conntrack.acct=1 kernel parameter, acct=1 nf_conntrack module option or
Jul  8 14:20:46 Alatheia kernel: [   70.137876] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
Jul  8 14:20:51 Alatheia kernel: [   75.472412] br0: port 3(tap0) entering disabled state
Jul  8 14:20:51 Alatheia kernel: [   75.488215] br0: port 3(tap0) entering disabled state
Jul  8 14:20:52 Alatheia kernel: [   76.714149] device tap0 entered promiscuous mode
Jul  8 14:20:52 Alatheia kernel: [   76.716188] br0: port 3(tap0) entering learning state
Jul  8 14:21:02 Alatheia kernel: [   86.724012] tap0: no IPv6 routers present
Jul  8 14:21:07 Alatheia kernel: [   91.716012] br0: port 3(tap0) entering forwarding state
Jul  8 15:00:01 Alatheia CRON[1835]: (root) CMD (   test -x /usr/sbin/tigercron && { [ -r "$DEFAULT" ] && . "$DEFAULT" ; nice -n$NICETIGER /usr/$
Jul  8 15:17:01 Alatheia CRON[1842]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul  8 16:00:01 Alatheia CRON[1846]: (root) CMD (   test -x /usr/sbin/tigercron && { [ -r "$DEFAULT" ] && . "$DEFAULT" ; nice -n$NICETIGER /usr/$
Jul  8 16:17:01 Alatheia CRON[1849]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul  8 17:00:01 Alatheia CRON[1853]: (root) CMD (   test -x /usr/sbin/tigercron && { [ -r "$DEFAULT" ] && . "$DEFAULT" ; nice -n$NICETIGER /usr/$
Jul  8 17:07:09 Alatheia kernel: [10054.000021] ------------[ cut here ]------------
Jul  8 17:07:09 Alatheia kernel: [10054.000037] WARNING: at /build/buildd/linux-2.6.32/net/sched/sch_generic.c:261 dev_watchdog+0x1fe/0x210()
Jul  8 17:07:09 Alatheia kernel: [10054.000042] Hardware name: E2610
Jul  8 17:07:09 Alatheia kernel: [10054.000046] NETDEV WATCHDOG: eth1 (tg3): transmit queue 0 timed out
Jul  8 17:07:09 Alatheia kernel: [10054.000049] Modules linked in: ipt_REJECT ipt_LOG xt_state xt_tcpudp iptable_nat nf_nat nf_conntrack_ipv4 nf$
Jul  8 17:07:09 Alatheia kernel: [10054.000123] Pid: 0, comm: swapper Not tainted 2.6.32-41-generic-pae #91-Ubuntu
Jul  8 17:07:09 Alatheia kernel: [10054.000127] Call Trace:
Jul  8 17:07:09 Alatheia kernel: [10054.000136]  [<c0154e82>] warn_slowpath_common+0x72/0xa0
Jul  8 17:07:09 Alatheia kernel: [10054.000143]  [<c050287e>] ? dev_watchdog+0x1fe/0x210
Jul  8 17:07:09 Alatheia kernel: [10054.000148]  [<c050287e>] ? dev_watchdog+0x1fe/0x210
Jul  8 17:07:09 Alatheia kernel: [10054.000153]  [<c0154efb>] warn_slowpath_fmt+0x2b/0x30
Jul  8 17:07:09 Alatheia kernel: [10054.000159]  [<c050287e>] dev_watchdog+0x1fe/0x210
Jul  8 17:07:09 Alatheia kernel: [10054.000166]  [<c016424c>] ? lock_timer_base+0x2c/0x60
Jul  8 17:07:09 Alatheia kernel: [10054.000171]  [<c01650f2>] ? mod_timer+0x102/0x1e0
Jul  8 17:07:09 Alatheia kernel: [10054.000176]  [<c01649ee>] run_timer_softirq+0x13e/0x2c0
Jul  8 17:07:09 Alatheia kernel: [10054.000183]  [<c017fef4>] ? tick_dev_program_event+0x74/0xd0
Jul  8 17:07:09 Alatheia kernel: [10054.000189]  [<c0502680>] ? dev_watchdog+0x0/0x210
Jul  8 17:07:09 Alatheia kernel: [10054.000194]  [<c015bc88>] __do_softirq+0x98/0x1b0
Jul  8 17:07:09 Alatheia kernel: [10054.000200]  [<c0180340>] ? tick_do_update_jiffies64+0x120/0x170
Jul  8 17:07:09 Alatheia kernel: [10054.000206]  [<c015bde5>] do_softirq+0x45/0x50
Jul  8 17:07:09 Alatheia kernel: [10054.000211]  [<c015bf35>] irq_exit+0x65/0x70
Jul  8 17:07:09 Alatheia kernel: [10054.000218]  [<c05bc58c>] smp_apic_timer_interrupt+0x5c/0x8b
Jul  8 17:07:09 Alatheia kernel: [10054.000224]  [<c010a1d1>] apic_timer_interrupt+0x31/0x40
Jul  8 17:07:09 Alatheia kernel: [10054.000230]  [<c0111045>] ? mwait_idle+0x55/0xa0
Jul  8 17:07:09 Alatheia kernel: [10054.000237]  [<c01085a4>] cpu_idle+0x94/0xd0
Jul  8 17:07:09 Alatheia kernel: [10054.000243]  [<c05a3ed2>] rest_init+0x62/0x70
Jul  8 17:07:09 Alatheia kernel: [10054.000250]  [<c07ea90c>] start_kernel+0x356/0x35c
Jul  8 17:07:09 Alatheia kernel: [10054.000255]  [<c07ea3e2>] ? unknown_bootoption+0x0/0x19e
Jul  8 17:07:09 Alatheia kernel: [10054.000261]  [<c07ea0bb>] i386_start_kernel+0xaa/0xb1
Jul  8 17:07:09 Alatheia kernel: [10054.000265] ---[ end trace b37673d1a3c92014 ]---
Jul  8 17:07:09 Alatheia kernel: [10054.000269] tg3: eth1: transmit timed out, resetting
Jul  8 17:07:09 Alatheia kernel: [10054.000321] tg3: DEBUG: MAC_TX_STATUS[ffffffff] MAC_RX_STATUS[ffffffff]
Jul  8 17:07:09 Alatheia kernel: [10054.000378] tg3: DEBUG: RDMAC_STATUS[ffffffff] WDMAC_STATUS[ffffffff]
Jul  8 17:07:10 Alatheia kernel: [10054.103760] tg3: tg3_stop_block timed out, ofs=2c00 enable_bit=2
Jul  8 17:07:10 Alatheia kernel: [10054.204243] tg3: tg3_stop_block timed out, ofs=2000 enable_bit=2
Jul  8 17:07:10 Alatheia kernel: [10054.304716] tg3: tg3_stop_block timed out, ofs=2400 enable_bit=2
Jul  8 17:07:10 Alatheia kernel: [10054.405188] tg3: tg3_stop_block timed out, ofs=2800 enable_bit=2
Jul  8 17:07:10 Alatheia kernel: [10054.505664] tg3: tg3_stop_block timed out, ofs=3000 enable_bit=2
Jul  8 17:07:10 Alatheia kernel: [10054.606136] tg3: tg3_stop_block timed out, ofs=1400 enable_bit=2
Jul  8 17:07:10 Alatheia kernel: [10054.706607] tg3: tg3_stop_block timed out, ofs=1800 enable_bit=2
Jul  8 17:07:10 Alatheia kernel: [10054.807079] tg3: tg3_stop_block timed out, ofs=c00 enable_bit=2
Jul  8 17:07:10 Alatheia kernel: [10054.907554] tg3: tg3_stop_block timed out, ofs=4800 enable_bit=2
Jul  8 17:07:10 Alatheia kernel: [10055.008027] tg3: tg3_stop_block timed out, ofs=1000 enable_bit=2
Jul  8 17:07:11 Alatheia kernel: [10055.108498] tg3: tg3_stop_block timed out, ofs=1c00 enable_bit=2
Jul  8 17:07:11 Alatheia kernel: [10055.209032] tg3: tg3_abort_hw timed out for eth1, TX_MODE_ENABLE will not clear MAC_TX_MODE=ffffffff
Jul  8 17:07:11 Alatheia kernel: [10055.309530] tg3: tg3_stop_block timed out, ofs=3c00 enable_bit=2
Jul  8 17:07:11 Alatheia kernel: [10055.410002] tg3: tg3_stop_block timed out, ofs=4c00 enable_bit=2
Jul  8 17:07:12 Alatheia kernel: [10056.783272] tg3: eth1: No firmware running.
Jul  8 17:07:13 Alatheia kernel: [10057.988634] tg3: tg3_abort_hw timed out for eth1, TX_MODE_ENABLE will not clear MAC_TX_MODE=ffffffff
Jul  8 17:07:27 Alatheia kernel: [10071.367039] tg3: eth1: Link is down.
Jul  8 17:07:27 Alatheia kernel: [10071.432186] br0: port 1(eth1) entering disabled state

```

From messages log:
```

Jul  8 13:36:29 Alatheia kernel: [   10.628274] udev: starting version 151
Jul  8 13:36:29 Alatheia kernel: [   10.997575] parport_pc 00:08: reported by Plug and Play ACPI
Jul  8 13:36:29 Alatheia kernel: [   10.997629] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
Jul  8 13:36:29 Alatheia kernel: [   11.003246] lp: driver loaded but no devices found
Jul  8 13:36:29 Alatheia kernel: [   11.009135] intel_rng: FWH not detected
Jul  8 13:36:29 Alatheia kernel: [   11.049395] ppdev: user-space parallel port driver
Jul  8 13:36:29 Alatheia kernel: [   11.095143] lp0: using parport0 (interrupt-driven).
Jul  8 13:36:29 Alatheia kernel: [   11.120887] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jul  8 13:36:29 Alatheia kernel: [   11.217535] Bridge firewalling registered
Jul  8 13:36:29 Alatheia kernel: [   11.218063] hda_codec: ALC888: BIOS auto-probing.
Jul  8 13:36:29 Alatheia kernel: [   11.219923] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input4
Jul  8 13:36:29 Alatheia kernel: [   11.244486] device eth1 entered promiscuous mode
Jul  8 13:36:29 Alatheia kernel: [   11.436714] ADDRCONF(NETDEV_UP): eth1: link is not ready
Jul  8 13:36:29 Alatheia kernel: [   11.450108] device eth0 entered promiscuous mode
Jul  8 13:36:29 Alatheia kernel: [   11.451519] r8169: eth0: link up
Jul  8 13:36:29 Alatheia kernel: [   11.489599] type=1505 audit(1341768987.484:2):  operation="profile_load" pid=604 name="/sbin/dhclient3"
Jul  8 13:36:29 Alatheia kernel: [   11.490419] type=1505 audit(1341768987.484:3):  operation="profile_load" pid=604 name="/usr/lib/NetworkManag$
Jul  8 13:36:29 Alatheia kernel: [   11.490890] type=1505 audit(1341768987.484:4):  operation="profile_load" pid=604 name="/usr/lib/connman/scri$
Jul  8 13:36:29 Alatheia kernel: [   11.493553] type=1505 audit(1341768987.488:5):  operation="profile_replace" pid=603 name="/sbin/dhclient3"
Jul  8 13:36:29 Alatheia kernel: [   11.494390] type=1505 audit(1341768987.488:6):  operation="profile_replace" pid=603 name="/usr/lib/NetworkMa$
Jul  8 13:36:29 Alatheia kernel: [   11.494843] type=1505 audit(1341768987.488:7):  operation="profile_replace" pid=603 name="/usr/lib/connman/s$
Jul  8 13:36:29 Alatheia kernel: [   11.497414] type=1505 audit(1341768987.492:8):  operation="profile_replace" pid=639 name="/sbin/dhclient3"
Jul  8 13:36:29 Alatheia kernel: [   11.498237] type=1505 audit(1341768987.492:9):  operation="profile_replace" pid=639 name="/usr/lib/NetworkMa$
Jul  8 13:36:29 Alatheia kernel: [   11.498711] type=1505 audit(1341768987.492:10):  operation="profile_replace" pid=639 name="/usr/lib/connman/$
Jul  8 13:36:29 Alatheia kernel: [   11.501971] type=1505 audit(1341768987.496:11):  operation="profile_replace" pid=716 name="/sbin/dhclient3"
Jul  8 13:36:29 Alatheia kernel: [   11.539882] br0: port 2(eth0) entering learning state
Jul  8 13:36:29 Alatheia kernel: [   12.428943] padlock: VIA PadLock not detected.
Jul  8 13:36:29 Alatheia kernel: [   12.451351] padlock: VIA PadLock Hash Engine not detected.
Jul  8 13:36:29 Alatheia kernel: [   13.040614] Adding 9801720k swap on /dev/mapper/cryptswap1.  Priority:-1 extents:1 across:9801720k
Jul  8 13:36:29 Alatheia kernel: [   13.813827] tg3: eth1: Link is up at 1000 Mbps, full duplex.
Jul  8 13:36:29 Alatheia kernel: [   13.813832] tg3: eth1: Flow control is on for TX and on for RX.
Jul  8 13:36:29 Alatheia kernel: [   13.813964] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
Jul  8 13:36:29 Alatheia kernel: [   13.814008] br0: port 1(eth1) entering learning state
Jul  8 13:36:29 Alatheia kernel: [   13.849644] device tap0 entered promiscuous mode
Jul  8 13:36:29 Alatheia kernel: [   13.851418] br0: port 3(tap0) entering learning state
Jul  8 13:36:42 Alatheia kernel: [   26.536147] br0: port 2(eth0) entering forwarding state
Jul  8 13:36:44 Alatheia kernel: [   28.812026] br0: port 1(eth1) entering forwarding state
Jul  8 13:36:44 Alatheia kernel: [   28.848011] br0: port 3(tap0) entering forwarding state
Jul  8 13:46:54 Alatheia kernel: [  637.491242] ip_tables: (C) 2000-2006 Netfilter Core Team
Jul  8 13:46:54 Alatheia kernel: [  637.515073] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
Jul  8 13:46:54 Alatheia kernel: [  637.515848] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Please use
Jul  8 13:46:54 Alatheia kernel: [  637.515855] nf_conntrack.acct=1 kernel parameter, acct=1 nf_conntrack module option or
Jul  8 13:46:54 Alatheia kernel: [  637.515861] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.

```

Any help is much appreciated!

As an aside, I don't believe I've updated recently (to try to rule out that issue).  I've checked the unattended-upgrades logs and nothing seems to be there, either.

---

### Post by SeijiSensei on 2012-07-09
Have you considered setting up a simple ping job to try and keep the network card awake?  Something like

```
ping -i 60 -c 999999999 some.ip.address &
```

That pings some.ip.address each minute (-i 60) 999999999 times.

---

### Post by jwright8 on 2012-07-09
While I was typing my post and looking at the logs, it went down again and gave the following:

```

Jul  9 08:51:22 Alatheia kernel: [ 2974.478159] ip_tables: (C) 2000-2006 Netfilter Core Team
Jul  9 08:51:22 Alatheia kernel: [ 2974.510926] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
Jul  9 08:51:22 Alatheia kernel: [ 2974.511649] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Please use
Jul  9 08:51:22 Alatheia kernel: [ 2974.511657] nf_conntrack.acct=1 kernel parameter, acct=1 nf_conntrack module option or
Jul  9 08:51:22 Alatheia kernel: [ 2974.511664] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
Jul  9 09:00:01 Alatheia CRON[1748]: (root) CMD (   test -x /usr/sbin/tigercron && { [ -r "$DEFAULT" ] && . "$DEFAULT" ; nice -n$NICETIGER /usr/sbin/tigercron -q ; })
Jul  9 09:17:01 Alatheia CRON[1759]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul  9 09:21:06 Alatheia kernel: [ 4757.980429] tg3: eth1: Link is down.
Jul  9 09:21:06 Alatheia kernel: [ 4757.996186] br0: port 2(eth1) entering disabled state
Jul  9 09:22:13 Alatheia kernel: [ 4824.829379] tg3: eth1: Link is up at 1000 Mbps, full duplex.
Jul  9 09:22:13 Alatheia kernel: [ 4824.829384] tg3: eth1: Flow control is on for TX and on for RX.
Jul  9 09:22:13 Alatheia kernel: [ 4824.829557] br0: port 2(eth1) entering learning state
Jul  9 09:22:24 Alatheia kernel: [ 4836.376539] br0: port 3(tap0) entering disabled state
Jul  9 09:22:24 Alatheia kernel: [ 4836.376552] br0: port 2(eth1) entering disabled state
Jul  9 09:22:24 Alatheia kernel: [ 4836.376558] br0: port 1(eth0) entering disabled state
Jul  9 09:22:24 Alatheia kernel: [ 4836.549892] tg3 0000:01:00.0: PME# enabled
Jul  9 09:22:24 Alatheia kernel: [ 4836.566127] device eth1 left promiscuous mode
Jul  9 09:22:24 Alatheia kernel: [ 4836.566134] br0: port 2(eth1) entering disabled state
Jul  9 09:22:24 Alatheia kernel: [ 4836.594240] device eth0 left promiscuous mode
Jul  9 09:22:24 Alatheia kernel: [ 4836.594247] br0: port 1(eth0) entering disabled state
Jul  9 09:22:24 Alatheia kernel: [ 4836.646052] br0: port 3(tap0) entering disabled state
Jul  9 09:22:25 Alatheia kernel: [ 4836.949997] device eth1 entered promiscuous mode
Jul  9 09:22:25 Alatheia kernel: [ 4836.953832] tg3 0000:01:00.0: PME# disabled
Jul  9 09:22:25 Alatheia kernel: [ 4836.968657] tg3 0000:01:00.0: irq 25 for MSI/MSI-X
Jul  9 09:22:25 Alatheia kernel: [ 4837.160705] ADDRCONF(NETDEV_UP): eth1: link is not ready
Jul  9 09:22:25 Alatheia kernel: [ 4837.162165] device eth0 entered promiscuous mode
Jul  9 09:22:25 Alatheia kernel: [ 4837.163514] r8169: eth0: link up
Jul  9 09:22:25 Alatheia kernel: [ 4837.223314] br0: port 2(eth0) entering learning state
Jul  9 09:22:27 Alatheia kernel: [ 4839.722278] tg3: eth1: Link is up at 1000 Mbps, full duplex.
Jul  9 09:22:27 Alatheia kernel: [ 4839.722283] tg3: eth1: Flow control is on for TX and on for RX.
Jul  9 09:22:27 Alatheia kernel: [ 4839.722449] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
Jul  9 09:22:27 Alatheia kernel: [ 4839.722497] br0: port 1(eth1) entering learning state
Jul  9 09:22:35 Alatheia kernel: [ 4847.412012] eth0: no IPv6 routers present
Jul  9 09:22:36 Alatheia kernel: [ 4848.060008] br0: no IPv6 routers present
Jul  9 09:22:38 Alatheia kernel: [ 4849.944011] eth1: no IPv6 routers present
Jul  9 09:22:40 Alatheia kernel: [ 4852.220013] br0: port 2(eth0) entering forwarding state
Jul  9 09:22:42 Alatheia kernel: [ 4854.720010] br0: port 1(eth1) entering forwarding state
Jul  9 09:22:43 Alatheia init: ssh main process (1267) terminated with status 255
Jul  9 09:22:48 Alatheia ntpdate[2173]: name server cannot be used, reason: Temporary failure in name resolution
Jul  9 09:24:05 Alatheia kernel: imklog 4.2.0, log source = /proc/kmsg started.
Jul  9 09:24:05 Alatheia rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="906" x-info="http://www.rsyslog.com"] (re)start
Jul  9 09:24:05 Alatheia rsyslogd: rsyslogd's groupid changed to 103
Jul  9 09:24:05 Alatheia rsyslogd: rsyslogd's userid changed to 101
Jul  9 09:24:05 Alatheia rsyslogd-2039: Could no open output file '/dev/xconsole' [try http://www.rsyslog.com/e/2039 ]

```I also went back to the server and tried to do:
```

./etc/init.d/networking restart

```And it showed the following (hopefully you can read it):

[IMG]http://i2.photobucket.com/albums/y34/gmwtmw/photo.jpg[/IMG]

Also, while I'm not sure if this helps, this is my /etc/network/interfaces:

```


# The loopback network interface
auto lo br0
iface lo inet loopback

# Need to set up the interfaces manually
iface eth0 inet manual

iface eth1 inet manual

# Bridge setup
# Static IP configuration
iface br0 inet static
        bridge_ports eth1 eth0 # Was eth0 eth1, but since the onboard is now eth1...
        address 10.1.10.70
        netmask 255.255.255.0
        network 10.1.10.0
        broadcast 10.1.10.255
        gateway 10.1.10.1

```

---

### Post by jwright8 on 2012-07-09
> **SeijiSensei said:**
> Have you considered setting up a simple ping job to try and keep the network card awake?  Something like

```
ping -i 60 -c 999999999 some.ip.address &
```That pings some.ip.address each minute (-i 60) 999999999 times.

Does the problem lie in the network card "going to sleep?"  The only reason I am confused by this is that up until Friday night, the system had been up for around 16 days or so without any problems.

EDIT: Just realized that it really did NOT like my comments at the end of that line, so I've removed them.

I also want to point out that I can immediately recreate this problem by doing the:

```

./etc/init.d/networking restart

```command. It will then not work until I reboot the system entirely.

---

### Post by jwright8 on 2012-07-09
Sorry for the triple post, but I figured I would report back.  I happened to have a backup from June 20th on a flash drive, so I restored it to that.  Upon doing apt-get update, it showed this:

```

root@Alatheia:/# apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be upgraded:
  libgcrypt11 linux-firmware linux-headers-2.6.32-41 linux-headers-2.6.32-41-generic-pae
  linux-image-2.6.32-41-generic-pae
5 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/56.8MB of archives.
After this operation, 3,523kB of additional disk space will be used.
Do you want to continue [Y/n]? n
Abort.

```So it does, in fact, seem as if the image for Linux had been upgraded.  Judging by the fact that after I restored the system, the problems (so far.. knock on wood) have gone away.  I can also do the command

```

./etc/init.d/networking restart

```without any problems, other than temporarily kicking me from SSH for about 45 seconds or so.  I hope this helps someone else... and I hope that someone keeps their old backups handy (I typically take one a week and keep the past month and a half).

I'll also post back here later on today, or more likely tomorrow, to say if the system has stopped giving trouble.  

Thanks for the help as always SeijiSensei!

EDIT:

As an afterthought, I'm not sure how to do it, but it might be a good idea to report it as a bug for them to take a look at, especially if this turns out to be something that is actually broken by the update.

On my (updated only as of June 20, 2012) copy, my syslog looks like this:

```

Jul  9 10:02:40 Alatheia snort[1213]:         --== Initialization Complete ==--
Jul  9 10:02:40 Alatheia snort[1213]: Snort initialization completed successfully (pid=1213)
Jul  9 10:02:40 Alatheia snort[1213]: Not Using PCAP_FRAMES
Jul  9 10:02:46 Alatheia kernel: [   24.160011] br0: no IPv6 routers present
Jul  9 10:02:46 Alatheia kernel: [   24.908007] eth0: no IPv6 routers present
Jul  9 10:02:48 Alatheia kernel: [   26.344049] tap0: no IPv6 routers present
Jul  9 10:02:48 Alatheia kernel: [   26.432008] eth1: no IPv6 routers present
Jul  9 10:02:51 Alatheia kernel: [   29.100012] br0: port 2(eth0) entering forwarding state
Jul  9 10:02:52 Alatheia kernel: [   30.568011] br0: port 3(tap0) entering forwarding state
Jul  9 10:02:53 Alatheia kernel: [   31.428010] br0: port 1(eth1) entering forwarding state
Jul  9 10:02:54 Alatheia init: ssh main process (906) terminated with status 255
Jul  9 10:02:54 Alatheia ntpdate[1323]: step time server 91.189.94.4 offset -0.384073 sec
Jul  9 10:03:11 Alatheia sudo: pam_sm_authenticate: Called
Jul  9 10:03:11 Alatheia sudo: pam_sm_authenticate: username = [xxxxxxx]
Jul  9 10:03:11 Alatheia sudo: Passphrase file wrapped
Jul  9 10:03:13 Alatheia sudo: Error attempting to add filename encryption key to user session keyring; rc = [1]
Jul  9 10:03:14 Alatheia sudo: Error attempting to add passphrase key to user session keyring; rc = [1]
Jul  9 10:05:00 Alatheia ntfs-3g[1430]: Version 2010.3.6 external FUSE 28
Jul  9 10:05:00 Alatheia ntfs-3g[1430]: Mounted /dev/sdb1 (Read-Write, label "xxxxxx16GB", NTFS 3.1)
Jul  9 10:05:00 Alatheia ntfs-3g[1430]: Cmdline options: rw
Jul  9 10:05:00 Alatheia ntfs-3g[1430]: Mount options: rw,silent,allow_other,nonempty,relatime,fsname=/dev/sdb1,blkdev,blksize=4096
Jul  9 10:05:00 Alatheia ntfs-3g[1430]: Ownership and permissions disabled, configuration type 1
Jul  9 10:06:21 Alatheia kernel: [  239.468382] ip_tables: (C) 2000-2006 Netfilter Core Team
Jul  9 10:06:21 Alatheia kernel: [  239.494773] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
Jul  9 10:06:21 Alatheia kernel: [  239.495621] CONFIG_NF_CT_ACCT is deprecated and will be removed soon. Please use
Jul  9 10:06:21 Alatheia kernel: [  239.495629] nf_conntrack.acct=1 kernel parameter, acct=1 nf_conntrack module option or
Jul  9 10:06:21 Alatheia kernel: [  239.495635] sysctl net.netfilter.nf_conntrack_acct=1 to enable it.
Jul  9 10:13:06 Alatheia kernel: [  645.400773] br0: port 3(tap0) entering disabled state
Jul  9 10:13:07 Alatheia kernel: [  645.412229] br0: port 3(tap0) entering disabled state
Jul  9 10:13:08 Alatheia kernel: [  646.651411] device tap0 entered promiscuous mode
Jul  9 10:13:08 Alatheia kernel: [  646.653715] br0: port 3(tap0) entering learning state
Jul  9 10:13:18 Alatheia kernel: [  656.684013] tap0: no IPv6 routers present
Jul  9 10:13:23 Alatheia kernel: [  661.652018] br0: port 3(tap0) entering forwarding state
Jul  9 10:17:01 Alatheia CRON[1844]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul  9 10:21:51 Alatheia kernel: [ 1169.980535] br0: port 3(tap0) entering disabled state
Jul  9 10:21:51 Alatheia kernel: [ 1169.980548] br0: port 2(eth0) entering disabled state
Jul  9 10:21:51 Alatheia kernel: [ 1169.980564] br0: port 1(eth1) entering disabled state
Jul  9 10:21:51 Alatheia kernel: [ 1170.254655] tg3 0000:01:00.0: PME# enabled
Jul  9 10:21:51 Alatheia kernel: [ 1170.282235] device eth1 left promiscuous mode
Jul  9 10:21:51 Alatheia kernel: [ 1170.282241] br0: port 1(eth1) entering disabled state
Jul  9 10:21:51 Alatheia kernel: [ 1170.306006] br0: port 2(eth0) entering disabled state
Jul  9 10:21:51 Alatheia kernel: [ 1170.399577] br0: port 3(tap0) entering disabled state
Jul  9 10:21:52 Alatheia kernel: [ 1170.510300] device eth1 entered promiscuous mode
Jul  9 10:21:52 Alatheia kernel: [ 1170.513507] tg3 0000:01:00.0: PME# disabled
Jul  9 10:21:52 Alatheia kernel: [ 1170.529378] tg3 0000:01:00.0: irq 25 for MSI/MSI-X
Jul  9 10:21:52 Alatheia kernel: [ 1170.724950] ADDRCONF(NETDEV_UP): eth1: link is not ready
Jul  9 10:21:52 Alatheia kernel: [ 1170.731740] r8169: eth0: link up
Jul  9 10:21:52 Alatheia kernel: [ 1170.813226] br0: port 2(eth0) entering learning state
Jul  9 10:21:54 Alatheia kernel: [ 1173.324935] tg3: eth1: Link is up at 1000 Mbps, full duplex.
Jul  9 10:21:54 Alatheia kernel: [ 1173.324942] tg3: eth1: Flow control is on for TX and on for RX.
Jul  9 10:21:54 Alatheia kernel: [ 1173.325260] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
Jul  9 10:21:54 Alatheia kernel: [ 1173.325320] br0: port 1(eth1) entering learning state
Jul  9 10:22:02 Alatheia kernel: [ 1180.972010] eth0: no IPv6 routers present
Jul  9 10:22:02 Alatheia kernel: [ 1181.284008] br0: no IPv6 routers present
Jul  9 10:22:04 Alatheia kernel: [ 1183.352010] eth1: no IPv6 routers present
Jul  9 10:22:07 Alatheia kernel: [ 1185.816012] br0: port 2(eth0) entering forwarding state
Jul  9 10:22:09 Alatheia kernel: [ 1188.328012] br0: port 1(eth1) entering forwarding state

```

So I'm kind of thinking that the "problem," as it were, is still there, and the update changed the way that particular issue was handled.  Please correct me if I'm wrong.

---

### Post by jwright8 on 2012-07-10
Just posting on this thread to update everyone that it might help.

Turns out the NIC on eth1 was bad, so I just got another PCI NIC and disabled the onboard in the BIOS.  Linux actually worked nicely with it, and mapped the new NIC to eth1, so I didn't have to change a thing and it all worked out well.

Thanks for the help guys, I'll make this one solved.

---

