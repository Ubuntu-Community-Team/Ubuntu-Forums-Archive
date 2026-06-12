---
title: "ubuntu eth0 nic copper link is down dell r210 poweredge"
date: 2010-08-01
forum: Server Platforms
---

### Post by gabak on 2010-08-01
i have a server dell poweredge r210 i got this message.

[78:384501] bnx2: eth0 NIC Copper Link is Down.


administrador@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr b8:ac:6f:86:2b:aa  
          inet addr:192.168.1.107  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::baac:6fff:fe86:2baa/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2161 errors:4 dropped:0 overruns:0 frame:4
          TX packets:1442 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1795833 (1.7 MB)  TX bytes:171676 (171.6 KB)
          Interrupt:16 Memory:da000000-da012800 

eth1      Link encap:Ethernet  HWaddr b8:ac:6f:86:2b:ab  
          inet addr:192.168.1.104  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 Memory:dc000000-dc012800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:112 errors:0 dropped:0 overruns:0 frame:0
          TX packets:112 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9384 (9.3 KB)  TX bytes:9384 (9.3 KB)

virbr0    Link encap:Ethernet  HWaddr 9e:51:36:c4:cf:fd  
          inet6 addr: fe80::9c51:36ff:fec4:cffd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:36 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:8223 (8.2 KB)

---

### Post by ruffEdgz on 2010-08-02
I think the question is when do you see that message of eth0 being down? Do you see it when you start up and shutdown? Is it only in the dmesg log file? Is eth0's IP setup to be static or dynamic? What does your /etc/network/interfaces look like? Can you ping your gateway 192.168.255.1?

Lets start there and see if this helps disagnose this problem further.

---

### Post by gabak on 2010-08-02
cuz this servers has two ethernet card. i see it in the one it is connected.
i connect one at the time i dont need to have connected both at the same time.
for now i m making some testing at this server b4 production

---

