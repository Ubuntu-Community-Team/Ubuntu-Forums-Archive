---
title: "connect: No buffer space available"
date: 2009-02-23
forum: Server Platforms
---

### Post by breorg on 2009-02-23
Hi,
Im remotely managing a Ubuntu LTs 6.06 Lamp Server which is being used as a content filtering system (Squid, Dansguardian and basic IPTables Only)

My clients are experiencing slow Internet responce times, when i log into the server and try to ping Local IP Addresses i recieve the following error

connect: No buffer space available

Any Ideas?

Thanks,

---

### Post by breorg on 2009-02-25
Im guessing the lack of responces is due to not enough information.

This firewall was not setup by me, but has been running fine.

Router 10.0.0.138

 ifconfig

eth0      Link encap:Ethernet  HWaddr 00:1E:8C:13:01:8E
          inet addr:10.0.0.2  Bcast:10.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::21e:8cff:fe13:18e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:64492 errors:0 dropped:0 overruns:0 frame:0
          TX packets:195 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:3882730 (3.7 MiB)  TX bytes:30791 (30.0 KiB)
          Interrupt:193 Base address:0xdc00

eth1      Link encap:Ethernet  HWaddr 00:E0:4C:38:CB:01
          inet addr:10.0.0.250  Bcast:10.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::2e0:4cff:fe38:cb01/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:64331 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:3862972 (3.6 MiB)  TX bytes:528 (528.0 b)
          Interrupt:233

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:31 errors:0 dropped:0 overruns:0 frame:0
          TX packets:31 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1758 (1.7 KiB)  TX bytes:1758 (1.7 KiB)

free
             total       used       free     shared    buffers     cached
Mem:       1930672     300400    1630272          0       4300      93740
-/+ buffers/cache:     202360    1728312
Swap:      3186680          0    3186680

Please let me know of any other information which can be of assistance.

Thanks

---------------*
Update:
I've been told that when Internet Explorer is opened it says that it is connecting to 10.0.0.250 but thats as far as it gets, no Username and Password box appears.
---------------*

---

### Post by breorg on 2009-02-26
Any idea's? have i posted this in the wrong forum???

---

### Post by booshire on 2009-02-27
Looking at other google hits. Try not using network-manager. Also, may have info entered incorrectly, check that. Also driver incorrectly installed. Screw this, google this:

ifconfig no buffer space

Plenty of hits. Repost with more info

---

