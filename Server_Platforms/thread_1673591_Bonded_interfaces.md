---
title: "Bonded interfaces"
date: 2011-01-22
forum: Server Platforms
---

### Post by MakOwner on 2011-01-22
I have an older server with dual 100MB NICs and I want to bond them in a round-robin pair (Mode 0 bond)

This appears to be working on 10.04.1 LTS -- are there any gotchas that I'm missing?  I didn't expect dhcp to actually work, but the DHCP server is set up with the MAC address of the eth0 and the bond appears to take over that address and the traffic appears to be fairly evenly balanced.


# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
#auto eth0
#iface eth0 inet dhcp

auto bond0
iface bond0 inet dhcp 
slaves eth0 eth1
# LACP confuration
bond_mode 0
bond_miimon 100
#bond_lacp_rate 1



This is during a transfer from another server to this box using "mc" so I can see a displayed transfer rate - mc reports about 14 MB/s and the source server is reporting about 15~16 MiB/s. 
I was getting a little more than half this with only one interface.

bond0     Link encap:Ethernet  HWaddr 00:02:b3:b9:fc:5e  
          inet addr:192.168.0.28  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::202:b3ff:feb9:fc5e/64 Scope:Link
          UP BROADCAST RUNNING MASTER MULTICAST  MTU:1500  Metric:1
          RX packets:9185442 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7987439 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:988384024 (988.3 MB)  TX bytes:588319461 (588.3 MB)

eth0      Link encap:Ethernet  HWaddr 00:02:b3:b9:fc:5e  
          UP BROADCAST RUNNING SLAVE MULTICAST  MTU:1500  Metric:1
          RX packets:4596965 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3993720 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2648223996 (2.6 GB)  TX bytes:294163810 (294.1 MB)

eth1      Link encap:Ethernet  HWaddr 00:02:b3:b9:fc:5e  
          UP BROADCAST RUNNING SLAVE MULTICAST  MTU:1500  Metric:1
          RX packets:4588477 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3993719 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2635127324 (2.6 GB)  TX bytes:294155651 (294.1 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:108 errors:0 dropped:0 overruns:0 frame:0
          TX packets:108 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9016 (9.0 KB)  TX bytes:9016 (9.0 KB)

---

