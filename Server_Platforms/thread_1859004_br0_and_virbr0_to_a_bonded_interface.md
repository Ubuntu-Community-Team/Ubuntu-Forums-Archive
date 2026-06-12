---
title: "br0 and virbr0 to a bonded interface?"
date: 2011-10-13
forum: Server Platforms
---

### Post by kelargo on 2011-10-13
Any suggestions on how to enable virbr0 and br0 to a bonded interface? Bond0 and not a single interface, eth4 in my case?

virbr0 has RX packets:0

thanks

>  [FONT="Courier New"]# brctl show
bridge name	bridge id		STP enabled	interfaces
br0		8000.003048bb2430	yes		eth4
							vnet0
virbr0		8000.000000000000	yes		[/FONT]

and

> [FONT="Courier New"]# ifconfig -a
bond0     Link encap:Ethernet  HWaddr 00:30:48:bb:24:30  
          inet addr:192.168.0.50  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::230:48ff:febb:2430/64 Scope:Link
          UP BROADCAST RUNNING MASTER MULTICAST  MTU:1500  Metric:1
          RX packets:175471809 errors:879 dropped:66687 overruns:0 frame:651
          TX packets:74366172 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:123926921001 (123.9 GB)  TX bytes:250073473215 (250.0 GB)

br0       Link encap:Ethernet  HWaddr 00:30:48:bb:24:30  
          inet6 addr: fe80::230:48ff:febb:2430/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:933 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10664 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:253031 (253.0 KB)  TX bytes:919760 (919.7 KB)

eth4      Link encap:Ethernet  HWaddr 00:30:48:bb:24:30  
          UP BROADCAST RUNNING SLAVE MULTICAST  MTU:1500  Metric:1
          RX packets:173409132 errors:0 dropped:40 overruns:0 frame:0
          TX packets:72970246 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:123701840896 (123.7 GB)  TX bytes:249940451803 (249.9 GB)
          Interrupt:70 Base address:0xa000 

eth5      Link encap:Ethernet  HWaddr 00:30:48:bb:24:30  
          UP BROADCAST RUNNING SLAVE MULTICAST  MTU:1500  Metric:1
          RX packets:2062677 errors:879 dropped:1 overruns:0 frame:651
          TX packets:1395926 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:225080105 (225.0 MB)  TX bytes:133021412 (133.0 MB)
          Interrupt:71 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1720048 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1720048 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:192703884 (192.7 MB)  TX bytes:192703884 (192.7 MB)

virbr0    Link encap:Ethernet  HWaddr 46:60:da:54:93:1e  
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7236 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:742608 (742.6 KB)

vnet0     Link encap:Ethernet  HWaddr fe:54:00:52:ac:8b  
          inet6 addr: fe80::fc54:ff:fe52:ac8b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:26 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:2343 (2.3 KB)  TX bytes:4536 (4.5 KB)[/FONT]



---

### Post by kelargo on 2011-10-13
not quite solved.. changed the values to below : 
virbro0 still RX=0,  still investigating. 

> [FONT="Courier New"]$  cat /etc/network/interfaces
# The loopback network interface
auto lo
iface lo inet loopback

# The bond interface - mode 4 is 802.3ad LACP. No slaves are defined here.
auto bond0
iface bond0 inet manual
	bond-slaves none
	bond-mode 4
	bond-miimon 100
	address 192.168.0.50
	netmask 255.255.255.0
	network 192.168.0.0
	broadcast 192.168.0.255
	gateway 192.168.0.1
	up /sbin/ifenslave bond0 eth4 eth5
	down /sbin/ifenslave bond0 eth4 eth5
	dns-nameservers 8.8.8.8 8.8.8.4
	
 
auto eth4
iface eth4 inet manual
	bond-master bond0
	bond-primary eth4 eth5

auto eth5
iface eth5 inet manual
	bond-master bond0
	bond-primary eth4 eth5


auto br0
iface br0 inet manual
#	bridge_ports eth4 
	bridge_ports bond0
	bridge_stp on
	bridge_maxage 0
	bridge_ageing 0
	bridge_maxwait 0
	brigde_fd 0[/FONT]


and re-ran my "enable bond script" .. instead of restarting networking. 
just restarting networking failed.

>  cat enable_bond 
#! /bin/sh
### BEGIN INIT INFO
# Provides:        enables bond interface 
# Required-Start:
# Required-Stop:
# Default-Start:
# Default-Stop:      6
# Short-Description:  enables bond interface
# Description:
### END INIT INFO

modprobe bonding
sleep 20
ifconfig bond0 192.168.0.50 netmask 255.255.255.0
sleep 20
ifenslave bond0 eth4 eth5
sleep 20
route add default gw 192.168.0.1
sleep 20
/etc/init.d/ntp stop
sleep 20
/etc/init.d/ntp start


---

