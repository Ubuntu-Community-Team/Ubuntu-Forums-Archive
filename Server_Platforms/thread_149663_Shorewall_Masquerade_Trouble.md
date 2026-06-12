---
title: "Shorewall Masquerade Trouble"
date: 2006-03-24
forum: Server Platforms
---

### Post by otakuj462 on 2006-03-24
Hi, I'm currently trying to configure an old machine to act as wireless-to-ethernet bridge. The Ubuntu box has two network interfaces, a wireless card (ath0), and a wired ethernet card (eth0). The idea is to have a Windows PC connected via a crossover ethernet cable to eth0 be able to access the internet through ath0. eth0 has a static ip address 192.168.1.10, and ath0 has a dynamic ip address 10.59.1.*
Thus far, I've installed Shorewall on the ubuntu box, and I've successfully configured it to act as a telnet and ftp server as well, but I've been unsuccessful in completing the masquerade. The PC can ping the ip addresses of both ath0 and eth0, but when it comes to pinging the ubuntu box's default gateway (10.59.1.1), it fails. The ubuntu box can ping the gateway just fine.
Unfortunately, my understanding of iptables isn't sufficient to troubleshoot this and I was hoping someone on this forum could tell me where it's going wrong. Here is the information I have:

Output of route:
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.59.1.0       *               255.255.255.0   U     0      0        0 ath0
192.168.0.0     *               255.255.255.0   U     0      0        0 eth0
default         10.59.1.1       0.0.0.0         UG    0      0        0 ath0

```


Ifconfig output:
```

ath0      Link encap:Ethernet  HWaddr 00:0D:88:56:0D:9B  
          inet addr:10.59.1.87  Bcast:10.59.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:767 errors:89999 dropped:0 overruns:0 frame:89999
          TX packets:987 errors:131 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:151287 (147.7 KiB)  TX bytes:179512 (175.3 KiB)
          Interrupt:12 Memory:c4be0000-c4bf0000 

eth0      Link encap:Ethernet  HWaddr 00:50:04:D8:39:2A  
          inet addr:192.168.0.10  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13432 errors:0 dropped:0 overruns:1 frame:0
          TX packets:11029 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:1270408 (1.2 MiB)  TX bytes:1682167 (1.6 MiB)
          Interrupt:11 Base address:0xd000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:80 errors:0 dropped:0 overruns:0 frame:0
          TX packets:80 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:21463 (20.9 KiB)  TX bytes:21463 (20.9 KiB)

```


Shorewall masq configuration file:
```

#INTERFACE		SUBNET		ADDRESS		PROTO	PORT(S)	IPSEC
ath0                    eth0	
#LAST LINE -- ADD YOUR ENTRIES ABOVE THIS LINE -- DO NOT REMOVE

```

Thanks!

-Jake

---

