---
title: "Setting MTU with VLAN.."
date: 2010-04-04
forum: Server Platforms
---

### Post by galluccib on 2010-04-04
[FONT=Arial][SIZE=2]Looking for any help I can get here.. We have a 9.10 server with both (ifenslave & VLAN) installed and configured. When we are running in bond mode (bond0) it sets the MTU to 9000 just fine.[/SIZE][/FONT]

[FONT=Arial][SIZE=2]iface bond0 inet static[/SIZE][/FONT]
[SIZE=2][FONT=Arial]hwaddress ether 00:04:7B:30:4A:AC[/FONT][/SIZE]
[SIZE=2][FONT=Arial]address 172.21.2.250[/FONT][/SIZE]
[FONT=Arial][SIZE=2]netmask 255.255.255.0[/SIZE][/FONT]
[SIZE=2][FONT=Arial]mtu 9000[/FONT][/SIZE]
[SIZE=2][FONT=Arial]post-up ifenslave bond0 eth0 eth1[/FONT][/SIZE]
 
 
[FONT=Arial][SIZE=2]But now when we bring a VLAN interface up it sets the MTU to 1500 even if we have it set to 9000 ->[/SIZE][/FONT]

[FONT=Arial][SIZE=2]auto bond0[/SIZE][/FONT]
[SIZE=2][FONT=Arial]iface bond0 inet manual[/FONT][/SIZE]
[SIZE=2][FONT=Arial]bond-mode 0[/FONT][/SIZE]
[SIZE=2][FONT=Arial]bond-miimon 100[/FONT][/SIZE]
[SIZE=2][FONT=Arial]slaves eth0 eth1[/FONT][/SIZE]
 
 
[FONT=Arial][SIZE=2]auto vlan3[/SIZE][/FONT]
[SIZE=2][FONT=Arial]iface vlan3 inet static[/FONT][/SIZE]
[SIZE=2][FONT=Arial]address 172.21.2.250[/FONT][/SIZE]
[FONT=Arial][SIZE=2]netmask 255.255.255.0[/SIZE][/FONT]
[SIZE=2][FONT=Arial]network 172.21.2.0[/FONT][/SIZE]
[SIZE=2][FONT=Arial]broadcast 172.21.2.255[/FONT][/SIZE]
[SIZE=2][FONT=Arial]mtu 9000[/FONT][/SIZE]
[SIZE=2][FONT=Arial]vlan_raw_device bond0[/FONT][/SIZE]

[FONT=Arial][SIZE=2]Then we try to set it it by hand..[/SIZE][/FONT]

[FONT=Arial][SIZE=2]vlan3 Link encap:Ethernet HWaddr 00:1d:09:6f:d9:63[/SIZE][/FONT]
[SIZE=2][FONT=Arial]inet addr:172.21.2.250 Bcast:172.21.2.255 Mask:255.255.255.0[/FONT][/SIZE]
[SIZE=2][FONT=Arial]inet6 addr: fe80::21d:9ff:fe6f:d963/64 Scope:Link[/FONT][/SIZE]
[SIZE=2][FONT=Arial]UP BROADCAST RUNNING MASTER MULTICAST MTU:1500 Metric:1[/FONT][/SIZE]
 
[SIZE=2][FONT=Arial]bond0 Link encap:Ethernet HWaddr 00:1d:09:6f:d9:63[/FONT][/SIZE]
[SIZE=2][FONT=Arial]inet6 addr: fe80::21d:9ff:fe6f:d963/64 Scope:Link[/FONT][/SIZE]
[SIZE=2][FONT=Arial]UP BROADCAST RUNNING MASTER MULTICAST MTU:1500 Metric:1[/FONT][/SIZE]
 

[FONT=Arial][SIZE=2]root@nfs01:/etc/network# ifconfig mtu 9000 vlan3[/SIZE][/FONT]
[SIZE=2][FONT=Arial]SIOCSIFADDR: No such device[/FONT][/SIZE]
[SIZE=2][FONT=Arial]mtu: ERROR while getting interface flags: No such device[/FONT][/SIZE]
[SIZE=2][FONT=Arial]vlan3: Unknown host[/FONT][/SIZE]
[SIZE=2][FONT=Arial]ifconfig: `--help' gives usage information.[/FONT][/SIZE]
[SIZE=2][FONT=Arial]root@nfs01:/etc/network#[/FONT][/SIZE]
 
 
[FONT=Arial][SIZE=2]root@nfs01:/etc/network# ifconfig mtu 9000 bond0[/SIZE][/FONT]
[SIZE=2][FONT=Arial]SIOCSIFADDR: No such device[/FONT][/SIZE]
[SIZE=2][FONT=Arial]mtu: ERROR while getting interface flags: No such device[/FONT][/SIZE]
[SIZE=2][FONT=Arial]bond0: Unknown host[/FONT][/SIZE]
[SIZE=2][FONT=Arial]ifconfig: `--help' gives usage information.[/FONT][/SIZE]
[SIZE=2][FONT=Arial]root@nfs01:/etc/network#[/FONT][/SIZE]
 
[FONT=Arial][SIZE=2]Can anybody point us in the right direction...[/SIZE][/FONT]

[FONT=Arial][SIZE=2]Thanks in advanced...[/SIZE][/FONT]

[FONT=Arial][SIZE=2]-Brian[/SIZE][/FONT]

---

### Post by HermanAB on 2010-04-04
Are both eth0 and eth1 MTU set to 9000?

---

### Post by galluccib on 2010-04-04
I have tried to set both in /etc/network/interfaces.. Here is a copy.
 
[EMAIL="root@nfs02://etc/network"]root@nfs02://etc/network[/EMAIL]# cat interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).
# The loopback network interface

auto lo eth0 eth1 eth3
iface lo inet loopback
 
# The primary network interface
iface eth3 inet static
        address 172.21.3.250
        netmask 255.255.255.0
        network 172.21.3.0
        broadcast 172.21.3.255
        gateway 172.21.3.1
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 172.21.3.9
        dns-search revshare.xo
 
iface eth0 inet manual
     mtu 9000
 
iface eth1 inet manual
     mtu 9000
 
auto bond0
iface bond0 inet manual
     bond-mode 0
     bond-miimon 100
     slaves eth0 eth1
     mtu 9000
#     xmit_hash_policy layer3+4
#     lacp_rate slow
 
auto bond0.3
iface bond0.3 inet static
      address 172.21.2.250
      netmask 255.255.255.0
      network 172.21.2.0
      broadcast 172.21.2.255
      vlan_raw_device bond0

 
bond0     Link encap:Ethernet  HWaddr 00:30:48:34:45:e6
          inet6 addr: fe80::230:48ff:fe34:45e6/64 Scope:Link
          UP BROADCAST RUNNING MASTER MULTICAST  MTU:1500  Metric:1
          RX packets:5885 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5640 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1061178 (1.0 MB)  TX bytes:1904180 (1.9 MB)
 
bond0.3   Link encap:Ethernet  HWaddr 00:30:48:34:45:e6
          inet addr:172.21.2.250  Bcast:172.21.2.255  Mask:255.255.255.0
          inet6 addr: fe80::230:48ff:fe34:45e6/64 Scope:Link
          UP BROADCAST RUNNING MASTER MULTICAST  MTU:1500  Metric:1
          RX packets:5836 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5637 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:975708 (975.7 KB)  TX bytes:1903950 (1.9 MB)
 
eth0      Link encap:Ethernet  HWaddr 00:30:48:34:45:e6
          UP BROADCAST RUNNING SLAVE MULTICAST  MTU:1500  Metric:1
          RX packets:420 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2820 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:47274 (47.2 KB)  TX bytes:950456 (950.4 KB)
          Memory:dc100000-dc120000
 
eth1      Link encap:Ethernet  HWaddr 00:30:48:34:45:e6
          UP BROADCAST RUNNING SLAVE MULTICAST  MTU:1500  Metric:1
          RX packets:5465 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2820 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1013904 (1.0 MB)  TX bytes:953724 (953.7 KB)
          Memory:dc120000-dc140000
 
eth3      Link encap:Ethernet  HWaddr 00:00:d1:a8:49:31
          inet addr:172.21.3.250  Bcast:172.21.3.255  Mask:255.255.255.0
          inet6 addr: fe80::200:d1ff:fea8:4931/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1046 errors:0 dropped:0 overruns:0 frame:0
          TX packets:59 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:41276 (41.2 KB)  TX bytes:9452 (9.4 KB)
          Interrupt:16

[EMAIL="root@nfs02://etc/network"]root@nfs02://etc/network[/EMAIL]# ifconfig mtu 9000 eth0
SIOCSIFADDR: No such device
mtu: ERROR while getting interface flags: No such device
eth0: Unknown host
ifconfig: `--help' gives usage information.
[EMAIL="root@nfs02://etc/network"]root@nfs02://etc/network[/EMAIL]#

---

### Post by galluccib on 2010-04-04
AS you can see if I take the VLAN interface out it works fine.. (But we need the VLAN interface)
 
[EMAIL="root@nfs02"]root@nfs02[/EMAIL]:~# ifconfig
bond0     Link encap:Ethernet  HWaddr 00:0b:7b:30:5f:78
          inet addr:172.21.2.250  Bcast:172.21.2.255  Mask:255.255.255.0
          inet6 addr: fe80::20b:7bff:fe30:5f78/64 Scope:Link
          UP BROADCAST RUNNING MASTER MULTICAST  **MTU:9000  **Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:468 (468.0 B)
 
eth0      Link encap:Ethernet  HWaddr 00:0b:7b:30:5f:78
          UP BROADCAST RUNNING SLAVE MULTICAST  **MTU:9000**  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:160 (160.0 B)
          Memory:dc100000-dc120000
 
eth1      Link encap:Ethernet  HWaddr 00:0b:7b:30:5f:78
          UP BROADCAST RUNNING SLAVE MULTICAST  **MTU:9000**  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:308 (308.0 B)
          Memory:dc120000-dc140000
 
 
[EMAIL="root@nfs02"]root@nfs02[/EMAIL]:~# cd /etc/network
[EMAIL="root@nfs02:/etc/network"]root@nfs02:/etc/network[/EMAIL]# cat interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).
# The loopback network interface

auto lo eth3 bond0
iface lo inet loopback
 
# The primary network interface
iface eth3 inet static
        address 172.21.3.250
        netmask 255.255.255.0
        network 172.21.3.0
        broadcast 172.21.3.255
        gateway 172.21.3.1
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 172.21.3.9
        dns-search revshare.xo
 
# NIC Bonding interface
iface bond0 inet static
       hwaddress ether 00:0B:7B:30:5F:78
       bond-mode 0
       bond-miimon 100
       slaves eth0 eth1
       mtu 9000
       address 172.21.2.250
       netmask 255.255.255.0
       post-up ifenslave bond0 eth0 eth1
# pre-down ifenslave -d bond0 eth0 eth1

---

### Post by mbradshaw on 2010-09-21
Hello,
   I found this thread while looking into a similar problem.  I'm trying to use a bridged interface with vlans and need jumbo frames.  Were you able to find a solution?  Maybe someone else has a good solution out there?

Thanks!
Michael

---

### Post by mbradshaw on 2010-09-22
So I got it to work this way:

# The primary network interface
auto eth0
iface eth0 inet manual

auto br-vlan3
iface br-vlan3 inet static
        address XX.XX.XX.XX
        netmask 255.255.0.0
	network XX.XX.0.0
	broadcast XX.XX.255.255
        gateway XX.XX.XX.XX
        vlan-raw-device eth0
        bridge_ports vlan3
        bridge_stop off
        bridge_fd 0
        bridge_maxwait 0
	post-up ifconfig eth0 mtu 9000
	post-up ifconfig vlan3 mtu 9000
 
auto br-vlan4
iface br-vlan4 inet static
	address XX.XX.XX.XX
	netmask 255.255.0.0
	network XX.XX.0.0
	broadcast XX.XX.255.255
	vlan-raw-device eth0
	bridge_ports vlan4
	bridge_stop off
	bridge_fd 0
	bridge_maxwait 0
	post-up ifconfig eth0 mtu 9000
	post-up ifconfig vlan4 mtu 9000

When I just had mtu 9000 as part of the interface settings (either above or below vlan-raw-device), everything would come up with mtu 1500 anyway.  

While the config above got me up and running, I'm sure there is a better way.  I'd love to hear what others have done.

Michael

---

