---
title: "Connect Two Ubuntu Computers using USB Ethernet Adaptor"
date: 2011-12-28
forum: System76 Support
---

### Post by jobattle on 2011-12-28
I have a System76 MadDog and am trying to connect it wo my old Debian computer using a Linkxyx USB Ethernet Dongle and a Linksys Switch.  I set the Debian machine IP address with:

ifconfig eth0 192.168.1.200

When I do an ifconfig on the System76 machine, I get :

eth0      Link encap:Ethernet  HWaddr e0:69:95:c3:a4:72  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::e269:95ff:fec3:a472/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5516 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3801 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2429587 (2.4 MB)  TX bytes:805823 (805.8 KB)
          Interrupt:20 Memory:f7200000-f7220000 

eth3      Link encap:Ethernet  HWaddr 00:e0:98:7d:fc:b8  
          inet addr:169.254.12.16  Bcast:169.254.255.255  Mask:255.255.0.0
          inet6 addr: fe80::2e0:98ff:fe7d:fcb8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:133 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:28249 (28.2 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:328 errors:0 dropped:0 overruns:0 frame:0
          TX packets:328 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:41278 (41.2 KB)  TX bytes:41278 (41.2 KB)

I also did a route command:

[HOTROD]~/route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1      0        0 eth3
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
224.0.0.0       0.0.0.0         240.0.0.0       U     0      0        0 eth3

This seems to indicate that eth3 (the usb dongle) is at 169.254.12.16, but when I try to ssh to that ip address, it connects me back to my System76 maching instead of to the Deb machine.  Anyway, where does that address come from?  What's going on here?

Thanks

John Battle (Ref Order# 20466)
[email]jobattle@gmail.com[/email]

---

### Post by isantop on 2011-12-28
Do you have router software installed on one of the machines? I believe you'll need some kind of router in there somewhere. The easiest way to do it is with a dedicated hardware router, which can be purchased from a local electronics store.

---

### Post by gsgleason on 2011-12-30
You should manually configure the address on the two machines that are connected to each other.

Put them on a different subnet than the other interface.

---

### Post by jschall1 on 2011-12-31
> **jobattle said:**
> I have a System76 MadDog and am trying to connect it wo my old Debian computer using a Linkxyx USB Ethernet Dongle and a Linksys Switch.  I set the Debian machine IP address with:

ifconfig eth0 192.168.1.200

When I do an ifconfig on the System76 machine, I get :

eth0      Link encap:Ethernet  HWaddr e0:69:95:c3:a4:72  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::e269:95ff:fec3:a472/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5516 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3801 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2429587 (2.4 MB)  TX bytes:805823 (805.8 KB)
          Interrupt:20 Memory:f7200000-f7220000 

eth3      Link encap:Ethernet  HWaddr 00:e0:98:7d:fc:b8  
          inet addr:169.254.12.16  Bcast:169.254.255.255  Mask:255.255.0.0
          inet6 addr: fe80::2e0:98ff:fe7d:fcb8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:133 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:28249 (28.2 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:328 errors:0 dropped:0 overruns:0 frame:0
          TX packets:328 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:41278 (41.2 KB)  TX bytes:41278 (41.2 KB)

I also did a route command:

[HOTROD]~/route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1      0        0 eth3
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
224.0.0.0       0.0.0.0         240.0.0.0       U     0      0        0 eth3

This seems to indicate that eth3 (the usb dongle) is at 169.254.12.16, but when I try to ssh to that ip address, it connects me back to my System76 maching instead of to the Deb machine.  Anyway, where does that address come from?  What's going on here?

Thanks

John Battle (Ref Order# 20466)
[email]jobattle@gmail.com[/email]

You may or may not need a crossover cable to connect them. You should be able to get them to connect to each other by giving them IP addresses on the same subnet. For example, 192.168.0.10 255.255.255.0 on old debian machine and 192.168.0.11 255.255.255.0 on the system76 machine. You won't be able to get out to the internet through the machine unless it is set up to bridge to another adapter.
If they have IP addresses on the same subnet and are connected to each other, try changing the cable out for a crossover cable and see if that works.

---

