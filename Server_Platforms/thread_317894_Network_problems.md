---
title: "Network problems"
date: 2006-12-13
forum: Server Platforms
---

### Post by E-Jey on 2006-12-13
I have the following situation right now: an ubuntu edy eft machine with two NICs (eth2 and eth3). One is configured with DHCP and the other has a static ip (223.0.157.3 255.255.255.240) and is connected to a router. 
When I ping 223.0.157.2 (which is in the same subnet) everything works fine. But when I ping to 223.0.157.19 (which is in an other subnet and connected through the router), my computer tries to find that machine through eth2 (which is configured via DHCP). How can I solve this?

---

### Post by chrisfay on 2006-12-13
Aren't both 223.0.157.2 and 223.0.157.19 in the same subnet? Am I missing something?

---

### Post by E-Jey on 2006-12-13
> **chrisfay said:**
> Aren't both 223.0.157.2 and 223.0.157.19 in the same subnet? Am I missing something?

Yes, you are missing something. The strange thing is that when I tracert the 223.0.157.19, my computer tries to find that PC trought eth2. The default gateways are set oke, but still he's searching on the wrong interface.

---

### Post by chrisfay on 2006-12-13
Can you post the output of:
```
route
```
and 
```
ifconfig
```

---

### Post by E-Jey on 2006-12-14
Ifconfig:
> 
eth2      Link encap:Ethernet  HWaddr 00:12:17:51:C6:44  
          inet addr:10.203.206.120  Bcast:10.203.206.255  Mask:255.255.255.0
          inet6 addr: fe80::212:17ff:fe51:c644/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1351 errors:0 dropped:0 overruns:0 frame:0
          TX packets:899 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:805084 (786.2 KiB)  TX bytes:146471 (143.0 KiB)
          Interrupt:201 Base address:0xb800 

eth3      Link encap:Ethernet  HWaddr 00:0A:5E:46:3B:EF  
          inet addr:223.0.157.3  Bcast:223.0.157.15  Mask:255.255.255.240
          inet6 addr: fe80::20a:5eff:fe46:3bef/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:799 errors:0 dropped:0 overruns:12 frame:0
          TX packets:300 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:61191 (59.7 KiB)  TX bytes:60126 (58.7 KiB)
          Interrupt:209 Base address:0x8c00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1064 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1064 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:829454 (810.0 KiB)  TX bytes:829454 (810.0 KiB)


route: 
> 
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
223.0.157.0     *               255.255.255.240 U     0      0        0 eth3
10.203.206.0    *               255.255.255.0   U     0      0        0 eth2
default         223.0.157.1     0.0.0.0         UG    0      0        0 eth3
default         10.203.206.254  0.0.0.0         UG    0      0        0 eth2


Traceroute to 223.0.157.19:
> 
traceroute to 223.0.157.19 (223.0.157.19), 30 hops max, 40 byte packets
 1  10.203.206.254 (10.203.206.254)  0.313 ms  0.289 ms  0.273 ms
 2  10.203.0.250 (10.203.0.250)  0.524 ms !A *  0.456 ms !A



I hope someone can help me! :)

---

