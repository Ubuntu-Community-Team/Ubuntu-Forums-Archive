---
title: "Guest OS (WinXP) can't ping gateway/internet"
date: 2008-05-17
forum: Virtualisation
---

### Post by notmyidea on 2008-05-17
I have been wrestling with bridging in VirtualBox for 2 days now and just can't get this to work.  I swear everything is set up right, but it just won't work.  What am I missing?

My host can ping my guest, gateway, internet all is fine
My guest can ping the br0 interface
My guest can not ping anything else

Here is /etc/network/interfaces:
auto lo
iface lo inet loopback

auto tap0
iface tap0 inet manual
up ifconfig $IFACE 0.0.0.0 up 
down ifconfig $IFACE down
tunctl_user jasonc

auto eth2
iface eth2 inet manual
up ifconfig $IFACE 0.0.0.0 up promisc
down ifconfig $IFACE down

auto br0
iface br0 inet static
address 192.168.1.12
network 192.168.1.0
netmask 255.255.255.128
gateway 192.168.1.1
    bridge_ports eth2 tap0

Guest network settings:
are IP 192.168.1.4, netmask 255.255.255.128, gateway 192.168.1.1 and DNS 192.168.1.1
In VirtualBox, I have set the Network Adapter to Host Interface, with tap0 as the interface name

route output:
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.128 U     0      0        0 br0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 br0
0.0.0.0         192.168.1.1     0.0.0.0         UG    100    0        0 br0

dmesg reports:
[ 4883.855130] br0: port 2(tap0) entering disabled state
[ 4883.947923] r8169: eth2: link up
[ 4884.000269] br0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature.
[ 4884.002634] device tap0 entered promiscuous mode
[ 4884.002640] audit(1211065896.518:22): dev=tap0 prom=256 old_prom=0 auid=4294967295
[ 4884.003881] br0: port 2(tap0) entering learning state
[ 4884.003884] br0: port 1(eth2) entering learning state
[ 4894.456481] tap0: no IPv6 routers present
[ 4894.488429] eth2: no IPv6 routers present
[ 4894.512287] br0: no IPv6 routers present
[ 4898.954261] br0: topology change detected, propagating
[ 4898.954266] br0: port 2(tap0) entering forwarding state
[ 4898.954267] br0: topology change detected, propagating
[ 4898.954269] br0: port 1(eth2) entering forwarding state

Output of ifconfig:
br0       Link encap:Ethernet  HWaddr 00:1d:7d:9e:d2:38  
          inet addr:192.168.1.12  Bcast:192.168.1.127  Mask:255.255.255.128
          inet6 addr: fe80::21d:7dff:fe9e:d238/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:255 errors:0 dropped:0 overruns:0 frame:0
          TX packets:224 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:171336 (167.3 KB)  TX bytes:30050 (29.3 KB)

eth2      Link encap:Ethernet  HWaddr 00:1d:7d:9e:d2:38  
          inet6 addr: fe80::21d:7dff:fe9e:d238/64 Scope:Link
          UP BROADCAST RUNNING PROMISC MULTICAST  MTU:1500  Metric:1
          RX packets:8152 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8272 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5858482 (5.5 MB)  TX bytes:1183565 (1.1 MB)
          Interrupt:219 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6384 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6384 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:400719 (391.3 KB)  TX bytes:400719 (391.3 KB)

tap0      Link encap:Ethernet  HWaddr 00:ff:6b:dc:a9:b0  
          inet6 addr: fe80::2ff:6bff:fedc:a9b0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:295 errors:0 dropped:0 overruns:0 frame:0
          TX packets:485 errors:0 dropped:47 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:40744 (39.7 KB)  TX bytes:47375 (46.2 KB)


I am using Xubuntu 8.04 and VirtualBox 1.5.6

Any advice would help!
Thanks Jason

*****FOUND PROBLEM*****

Note to all those who are using MoBlock:
You must put your network address range in WHITE_IP_FORWARD
ex. WHITE_IP_FORWARD="192.168.1.0/24" in addition to WHITE_IP_IN and WHITE_IP_OUT

---

### Post by spur on 2008-06-12
If you're using NAT you can't ping.

---

### Post by linux6994 on 2008-06-12
In Virtualbox if you do ipconfig you will see the virtualdefault gw such as 10.0.2.2 or what ever it shows.

---

### Post by spur on 2008-06-12
Ok, so what exactly are you saying?
Original poster says problem solved, but I know from searching myself a lot of people are having problems getting a virtual xp to connect to the internet (me included) and have tried everything I have found. Using intel manually configuring, and repeatedly restarting both the connection and the os.
But still no joy.
The pinging is not the problem if you have NAT as it says in several places NAT does not allow pinging, which is why I put it there. So someone reading the post would not spend ages thinking they can.

---

