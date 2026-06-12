---
title: "Multiple NICs different subnets"
date: 2011-12-04
forum: Server Platforms
---

### Post by baz.g on 2011-12-04
Hi guys,

I have an ubuntu 10.04 server installed at work with 2 pci NICs (i dont need 2, this was a second hand server so I just left them installed) installed plus the 2 internal ethernet ports. so this makes eth0 through to eth5.

I currently have eth0 and eth5 bonded together in the /etc/networking/interfaces file with the IP 192.168.168.50. I followed a post I googled to setup the bond which included disabling the GUI network manager so nothing shows up in there.

This is working fine and has been for nearly a year.

We now have an internal wireless LAN on a different subnet which I have connected to this server to as well.

I have configured in the interfaces file (in addition to the existing bond); eth1 with IP 192.168.200.50.

When i restart  networking it doesnt bring up eth1 initially when i run ifconfig. So i run: sudo ifup eth1 and then I can see it when i run ifconfig.

I tried rebooting the server completely and then I could see every eth interface except eth1 - however, before I started any of this I could only see lo, bond0, eth0 and eth5.

The other problem is that I cannot access the internet and also I cannot access the server using the 200 subnet.

I can, thankfully, still access the server using the 168 subnet but it seems quite slow. I think this means that the server is getting quite confused as to where it should send the packets.

I googled for this and most of the sites I found were talking about ICS. But i do not want the server to do this as the 2 subnets should always be kept seperate i.e. somebody connecting on the 200 subnet should not be able to see anything on the 168 subnet.

Any ideas please? :)

---

### Post by trogdor1138 on 2011-12-04
Can you post your interfaces configuration file and the output of ifconfig? It's easier to help when you share the specifics of your setup :D

---

### Post by baz.g on 2011-12-05
hi trogdor

i realised afterwards that it was because i had specified 2 different gateways. i think i have solved it now but i havent rebooted again to see if eth1 comes up automatically

interfaces file:
```

# This file describes the network interfaces available on your system
 # and how to activate them. For more information, see interfaces(5).

 # The loopback network interface
auto lo bond0
 iface lo inet loopback

# The primary network interface

iface bond0 inet static
address 192.168.168.50
netmask 255.255.255.0
gateway 192.168.168.254
bond-slaves eth0 eth5

iface eth1 inet static
address 192.168.200.50
netmask 255.255.255.0

```

ifconfig:
```

bond0     Link encap:Ethernet  HWaddr 00:17:08:5c:5b:eb  
          inet addr:192.168.168.50  Bcast:192.168.168.255  Mask:255.255.255.0
          inet6 addr: fe80::217:8ff:fe5c:5beb/64 Scope:Link
          UP BROADCAST RUNNING MASTER MULTICAST  MTU:1500  Metric:1
          RX packets:448181 errors:0 dropped:0 overruns:0 frame:0
          TX packets:121874 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:69578704 (69.5 MB)  TX bytes:63823728 (63.8 MB)

eth0      Link encap:Ethernet  HWaddr 00:17:08:5c:5b:eb  
          UP BROADCAST RUNNING SLAVE MULTICAST  MTU:1500  Metric:1
          RX packets:75812 errors:0 dropped:0 overruns:0 frame:0
          TX packets:46979 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:19608507 (19.6 MB)  TX bytes:16465774 (16.4 MB)
          Interrupt:25 

eth1      Link encap:Ethernet  HWaddr 00:17:08:5c:5b:ea  
          inet addr:192.168.200.50  Bcast:192.168.200.255  Mask:255.255.255.0
          inet6 addr: fe80::217:8ff:fe5c:5bea/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4483 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3644 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:832244 (832.2 KB)  TX bytes:3846816 (3.8 MB)
          Interrupt:26 

eth2      Link encap:Ethernet  HWaddr 00:11:0a:62:6a:50  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth3      Link encap:Ethernet  HWaddr 00:11:0a:62:6a:51  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth4      Link encap:Ethernet  HWaddr 00:11:0a:62:6a:e2  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth5      Link encap:Ethernet  HWaddr 00:17:08:5c:5b:eb  
          UP BROADCAST RUNNING SLAVE MULTICAST  MTU:1500  Metric:1
          RX packets:372369 errors:0 dropped:0 overruns:0 frame:0
          TX packets:74895 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:49970197 (49.9 MB)  TX bytes:47357954 (47.3 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4478049 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4478049 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:402025156 (402.0 MB)  TX bytes:402025156 (402.0 MB)

```

i also do not know why suddenly all of the interfaces are showing up in ifconfig

i also followed the instructions here: [http://kindlund.wordpress.com/2007/11/19/configuring-multiple-default-routes-in-linux/](http://kindlund.wordpress.com/2007/11/19/configuring-multiple-default-routes-in-linux/)

and setup a different ip route for each subnet. although, i havent added the gateway back into the eth1 config as i am not bothered about internet access on both NICs.

I had firestarter already configured on the server and the only thing I changed was to setup ICS for NATing between the 2 interfaces.

Does this all sound correct? Is there anything I can change for the better?

Many many thanks :-)

---

