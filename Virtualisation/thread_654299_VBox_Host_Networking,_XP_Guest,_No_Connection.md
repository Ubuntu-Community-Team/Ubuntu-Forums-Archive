---
title: "VBox Host Networking, XP Guest, No Connection"
date: 2007-12-30
forum: Virtualisation
---

### Post by bennybobw on 2007-12-30
My guest XP system cannot connect to the outside internet. I just installed Gutsy. The networking worked when I had NAT enabled, but I want to be able to access sites running on localhost as well as the regular internet from guest XP.

I used the VirtualBox manual and [this site]("http://www.bluetwanger.de/blog/2007/04/30/host-networking-with-virtualbox-on-ubuntu-704-feisty/") to configure.

Here's my /etc/network/interfaces:
```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet manual
   up ifconfig $IFACE 0.0.0.0 up
   down ifconfig $IFACE down 
   tunctl_user bennybobw
   
#the virtual network interface
auto tap0
iface tap0 inet manual
    up ifconfig $IFACE 0.0.0.0 up
    down ifconfig $IFACE down
    tunctl_user bennybobw

#The bridge interface
auto br0
iface br0 inet dhcp
    bridge_ports eth0 tap0
    bridge_maxwait 0

```

And after I restart networking, ifconfig gives me:
```

br0       Link encap:Ethernet  HWaddr 00:0D:60:78:BB:34  
          inet addr:192.168.2.102  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::20d:60ff:fe78:bb34/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4140 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3424 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4102737 (3.9 MB)  TX bytes:577096 (563.5 KB)

eth0      Link encap:Ethernet  HWaddr 00:0D:60:78:BB:34  
          inet6 addr: fe80::20d:60ff:fe78:bb34/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6204 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5088 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:6074956 (5.7 MB)  TX bytes:833084 (813.5 KB)
          Base address:0x8000 Memory:c0220000-c0240000 

eth1      Link encap:Ethernet  HWaddr 00:0C:F1:34:A6:43  
          inet6 addr: fe80::20c:f1ff:fe34:a643/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:515 errors:3 dropped:0 overruns:0 frame:0
          TX packets:25 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:115321 (112.6 KB)  TX bytes:1812 (1.7 KB)
          Interrupt:11 Base address:0x8000 Memory:c0210000-c0210fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

tap0      Link encap:Ethernet  HWaddr 00:FF:8C:B0:9C:15  
          inet6 addr: fe80::2ff:8cff:feb0:9c15/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:151 errors:0 dropped:0 overruns:0 frame:0
          TX packets:616 errors:0 dropped:52 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:23439 (22.8 KB)  TX bytes:195053 (190.4 KB)

```

In VirtualBox network is attached to Host interface and interface name is tap0.

Thanks for your help!

---

### Post by bennybobw on 2007-12-31
I should mention that my host connects fine to the internet, but I get can't connect from the guest XP.

---

### Post by popch on 2007-12-31
Your NIC with the name br0 seems to be the only one with an IP address, unless your LAN runs on IPv6. However, I find it somewhat strange that br0 and ETH0 use the same hardware address.

Make sure that your virtual machine actually uses br0 to communicate.

---

### Post by karyonix on 2008-01-15
It seems you have two NICs eth0 and eth1. eth0 is connected to LAN & internet.

- Your eth0 lacks PROMISC mode. This is probably the cause of your problem. 
  Try changing line 6 "up ifconfig $IFACE 0.0.0.0 up" to "up ifconfig $IFACE 0.0.0.0 up promisc"

- Add your user account to uml-net group if you have not done so.

- tunctl_user tells the script that the interface is TUN/TAP.
  There should not be the line "tunctl_user bennybobw" (line 8 ) under iface eth0.  What it does is trying to create a TUN/TAP interface named "eth0" for user "bennybobw" and failed with this error message "TUNSETIFF: Invalid argument".

- Only the bridge needs IP address. eth0 and tap0 does not need IP addresses.
- br0 and eth0 having same HWaddr is normal.  if DHCP server was set to provide a fixed IP address for eth0's HWaddr, br0 will get that IP address.

My /etc/network/interfaces is like this
```
auto lo eth0 tap0 br0

iface lo inet loopback

iface eth0 inet manual

iface tap0 inet manual
  tunctl_user *myusername*

iface br0 inet dhcp
  bridge_ports eth0 tap0
  pre-up ip link set eth0 promisc on
```
My host br0 and VM get IP addresses from DHCP server on the network and work well.

---

