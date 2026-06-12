---
title: "Bonding/bridging problem in Xen on Ubuntu 8.04"
date: 2010-02-04
forum: Virtualisation
---

### Post by kRiSdAbAsTaRd on 2010-02-04
[SIZE=3][FONT=Consolas]I'm preparing HA configuration for Xen but experiencing problem with bridge/bonding configuration. My server has got several NIC's so at first I've created bond0 interface consisting of eth0 and eth4 working in pri-stb mode. I've tested it and it works just fine. Now, because I've found Xen's default "network-bridge" script useless in such configuration, I've turned it off in xend-config.sxp and created custom bridge in /etc/network/interfaces:[/FONT][/SIZE]
 
[SIZE=3][FONT=Consolas]root@xen03:/home/xen/domains# vi /etc/network/interfaces[/FONT][/SIZE]
[SIZE=3][FONT=Consolas]...[/FONT][/SIZE]
[SIZE=3][FONT=Consolas]auto xenbr0[/FONT][/SIZE]
[SIZE=3][FONT=Consolas]iface xenbr0 inet static[/FONT][/SIZE]
[SIZE=3][FONT=Consolas]address 192.168.1.13[/FONT][/SIZE]
[SIZE=3][FONT=Consolas]netmask 255.255.255.0[/FONT][/SIZE]
[SIZE=3][FONT=Consolas]broadcast 192.168.1.255[/FONT][/SIZE]
[SIZE=3][FONT=Consolas]network 192.168.1.0[/FONT][/SIZE]
[SIZE=3][FONT=Consolas]gateway 192.168.1.1[/FONT][/SIZE]
[SIZE=3][FONT=Consolas]pre-up ip link set eth0 up[/FONT][/SIZE]
[SIZE=3][FONT=Consolas]pre-up ip link set eth4 up[/FONT][/SIZE]
[SIZE=3][FONT=Consolas]pre-up modprobe -v bonding -o bond0 mode=1 miimon=100[/FONT][/SIZE]
[SIZE=3][FONT=Consolas]pre-up ip link set bond0 up[/FONT][/SIZE]
[SIZE=3][FONT=Consolas]pre-up ifenslave bond0 eth0 eth4[/FONT][/SIZE]
[SIZE=3][FONT=Consolas]pre-up modprobe bridge[/FONT][/SIZE]
[SIZE=3][FONT=Consolas]pre-up brctl addbr xenbr0[/FONT][/SIZE]
[SIZE=3][FONT=Consolas]pre-up brctl addif xenbr0 bond0[/FONT][/SIZE]
[SIZE=3][FONT=Consolas]pre-up brctl stp xenbr0 off[/FONT][/SIZE]
[SIZE=3][FONT=Consolas]pre-up brctl setfd xenbr0 0[/FONT][/SIZE]
 
[SIZE=3][FONT=Consolas]root@xen03:/home/xen/domains# ifconfig[/FONT][/SIZE]
[SIZE=3][FONT=Consolas]bond0 Link encap:Ethernet HWaddr 00:08:02:cd:4c:76[/FONT][/SIZE]
[SIZE=3][FONT=Consolas]inet6 addr: fe80::208:2ff:fecd:4c76/64 Scope:Link[/FONT][/SIZE]
[SIZE=3][FONT=Consolas]UP BROADCAST RUNNING MASTER MULTICAST MTU:1500 Metric:1[/FONT][/SIZE]
[SIZE=3][FONT=Consolas]RX packets:34806 errors:0 dropped:0 overruns:0 frame:0[/FONT][/SIZE]
[SIZE=3][FONT=Consolas]TX packets:21465 errors:0 dropped:0 overruns:0 carrier:0[/FONT][/SIZE]
[SIZE=3][FONT=Consolas]collisions:0 txqueuelen:0[/FONT][/SIZE]
[SIZE=3][FONT=Consolas]RX bytes:41126205 (39.2 MB) TX bytes:1716254 (1.6 MB)[/FONT][/SIZE]
 
[SIZE=3][FONT=Consolas]eth0 Link encap:Ethernet HWaddr 00:08:02:cd:4c:76[/FONT][/SIZE]
[SIZE=3][FONT=Consolas]UP BROADCAST RUNNING SLAVE MULTICAST MTU:1500 Metric:1[/FONT][/SIZE]
[SIZE=3][FONT=Consolas]RX packets:33191 errors:0 dropped:0 overruns:0 frame:0[/FONT][/SIZE]
[SIZE=3][FONT=Consolas]TX packets:21129 errors:0 dropped:0 overruns:0 carrier:0[/FONT][/SIZE]
[SIZE=3][FONT=Consolas]collisions:0 txqueuelen:1000[/FONT][/SIZE]
[SIZE=3][FONT=Consolas]RX bytes:41004583 (39.1 MB) TX bytes:1679726 (1.6 MB)[/FONT][/SIZE]
 
[SIZE=3][FONT=Consolas]eth4 Link encap:Ethernet HWaddr 00:08:02:cd:4c:76[/FONT][/SIZE]
[SIZE=3][FONT=Consolas]UP BROADCAST RUNNING SLAVE MULTICAST MTU:1500 Metric:1[/FONT][/SIZE]
[SIZE=3][FONT=Consolas]RX packets:1615 errors:0 dropped:0 overruns:0 frame:0[/FONT][/SIZE]
[SIZE=3][FONT=Consolas]TX packets:336 errors:0 dropped:0 overruns:0 carrier:0[/FONT][/SIZE]
[SIZE=3][FONT=Consolas]collisions:0 txqueuelen:1000[/FONT][/SIZE]
[SIZE=3][FONT=Consolas]RX bytes:121622 (118.7 KB) TX bytes:36528 (35.6 KB)[/FONT][/SIZE]
 
[SIZE=3][FONT=Consolas]xenbr0 Link encap:Ethernet HWaddr 00:08:02:cd:4c:76[/FONT][/SIZE]
[SIZE=3][FONT=Consolas]inet addr:192.168.1.13 Bcast:192.168.1.255 Mask:255.255.255.0[/FONT][/SIZE]
[SIZE=3][FONT=Consolas]inet6 addr: fe80::208:2ff:fecd:4c76/64 Scope:Link[/FONT][/SIZE]
[SIZE=3][FONT=Consolas]UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1[/FONT][/SIZE]
[SIZE=3][FONT=Consolas]RX packets:34366 errors:0 dropped:0 overruns:0 frame:0[/FONT][/SIZE]
[SIZE=3][FONT=Consolas]TX packets:21286 errors:0 dropped:0 overruns:0 carrier:0[/FONT][/SIZE]
[SIZE=3][FONT=Consolas]collisions:0 txqueuelen:0[/FONT][/SIZE]
[SIZE=3][FONT=Consolas]RX bytes:40612375 (38.7 MB) TX bytes:1706304 (1.6 MB)[/FONT][/SIZE]
 
[SIZE=3][FONT=Consolas]root@xen03:/home/xen/domains# brctl show[/FONT][/SIZE]
[SIZE=3][FONT=Consolas]bridge name bridge id STP enabled interfaces[/FONT][/SIZE]
[SIZE=3][FONT=Consolas]xenbr0 8000.000802cd4c76 no bond0[/FONT][/SIZE]
 
[SIZE=3][FONT=Consolas]This config seemed to work but… when I’ve tested redundancy (ifconfig eth0 down) pinging 192.168.1.13 at the same time from remote server, I’ve noticed packets loss. The same issue occurred when I brought up eth0 and brought down eth4. Could someone give me some pointers what can be the reason of this problem and how to eliminate it? [/FONT][/SIZE]

---

### Post by kRiSdAbAsTaRd on 2010-02-05
I've made some progress - "mode 0" was the key (failover + load ballancing) and ther's no packet loss now but... instead I experience DUP! every two packets while I'm pinging 192.168.1.13. Probably it's connected with switch configuration (etherchanell/lacp - I'm not sure for now). In my configuration I use only one switch - cisco 2950 - but I'm going to replace it with two hp procurve switches with trunk between them on Monday.

---

