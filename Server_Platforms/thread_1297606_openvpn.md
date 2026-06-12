---
title: "openvpn"
date: 2009-10-21
forum: Server Platforms
---

### Post by jay3712 on 2009-10-21
I am working on setting up a vpn to access my home network resources from my office. I have been following this howto: [https://help.ubuntu.com/community/OpenVPN](https://help.ubuntu.com/community/OpenVPN)

My server has a static ip of 192.168.1.200 on the local network given by the router (dd-wrt).

This is the output of ifconfig:
```
eth0      Link encap:Ethernet  HWaddr 00:30:48:dc:77:9a
          inet addr:192.168.1.200  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::230:48ff:fedc:779a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3287 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3062 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1611712 (1.6 MB)  TX bytes:639010 (639.0 KB)
          Interrupt:252 Base address:0x6000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:68 errors:0 dropped:0 overruns:0 frame:0
          TX packets:68 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:5981 (5.9 KB)  TX bytes:5981 (5.9 KB)
```

This is /etc/network/interfaces:
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

```

1) How do I need to change this to add the bridged connection?
2) My server motherboard has two NICs, would it be some benefit to dedicate the second one (eth1) to the vpn?

Thanks!

Jason

---

### Post by Zeosa on 2009-10-22
First, from your interfaces file, you're server doesn't have a static ip, it's getting it via dhcp from the router. You're going to need to set a static ip for the box using an ip thats free on your network. Your interfaces file should look something like this:

```

auto lo br0
iface lo inet loopback

iface br0 inet static 
  address 192.168.1.200 
  netmask 255.255.255.0
  gateway 192.168.1.1
  bridge_ports eth0

iface eth0 inet manual
  up ifconfig $IFACE 0.0.0.0 up
  up ip link set $IFACE promisc on
  down ip link set $IFACE promisc off
  down ifconfig $IFACE down 

```

This will assign the static ip to the bridge that you're creating. which you will eventually forward the vpn traffic to via your router.


> 
2) My server motherboard has two NICs, would it be some benefit to dedicate the second one (eth1) to the vpn?


You can do either, but at this point to keep it simple you should probably just concentrate on what you've got so you don't confuse yourself during the setup (the first time is always the hardest). There's a few reasons to do it, 1) if your vpn traffic killing the other traffic on the NIC (pretty much impossible in your situation). or 2) you want your vpn traffic on a seperate subnet from your lan traffic (which complicates the setup a bit)

---

### Post by jay3712 on 2009-10-22
Thanks for the reply Zeosa. What does each line in this section mean? Why 0.0.0.0?

```

iface eth0 inet manual
  up ifconfig $IFACE 0.0.0.0 up
  up ip link set $IFACE promisc on
  down ip link set $IFACE promisc off
  down ifconfig $IFACE down 

```

Thanks again,
Jason

---

### Post by Zeosa on 2009-10-22
.

```

#This line sets the interface to be started manually (no, you don't have to do it yourself)
iface eth0 inet manual
#this brings the interface up with no ip
  up ifconfig $IFACE 0.0.0.0 up
#This sets the interface into promiscuous mode for the bridge
  up ip link set $IFACE promisc on
#This brings the interface out of promiscuous mode when before bringing it down.
  down ip link set $IFACE promisc off
#This brings the interface down 
 down ifconfig $IFACE down 

```



Once everything is running, your ifconfig output will look something like this:

```

br0       Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:xx  
          inet addr:192.168.1.200  Bcast: 192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::a00:27ff:feb7:2173/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:27388 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1586 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:xxxxx (3.0 MB)  TX bytes:xxxxx (242.6 KB)

eth0      Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx  
          inet6 addr: fe80::a00:27ff:feb7:2173/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:xxx errors:xxx dropped:0 overruns:0 frame:0
          TX packets:1592 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:xxxxx (781.0 MB)  TX bytes:xxxxx (243.1 KB)
          Interrupt:11 Base address:0xd020 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1592 (1.5 KB)  TX bytes:1592 (1.5 KB)

tap0      Link encap:Ethernet  HWaddr 00:ff:60:a9:95:62  
          inet6 addr: fe80::2ff:60ff:fea9:9562/64 Scope:Link
          UP BROADCAST RUNNING PROMISC MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16452 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:0 (0.0 B)  TX bytes:xxx (x.x MB)

```

Thanks again,
Jason[/QUOTE]

---

