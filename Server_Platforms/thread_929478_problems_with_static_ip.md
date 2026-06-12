---
title: "problems with static ip"
date: 2008-09-25
forum: Server Platforms
---

### Post by BIPS on 2008-09-25
hi,
i have some problems with my server and static ip i dont know what iu have entered after broadcasting and network so my server can't connect to internet via static ip.

ifconfig shows:

benas@86:~$ ifconfig
eth0 Link encap:Ethernet HWaddr 00:11:2f:3e:eb:2a
inet addr:86.38.32.250 Bcast:86.38.32.255 Mask:255.255.255.248
inet6 addr: fe80::211:2fff:fe3e:eb2a/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:14634
TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes:1224 (1.1 KB)
Interrupt:18 Base address:0x2c00

eth1 Link encap:Ethernet HWaddr 00:1d:60:cf:15:c8
inet addr:192.168.1.10 Bcast:192.168.1.255 Mask:255.255.255.0
inet6 addr: fe80::21d:60ff:fecf:15c8/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:2620 errors:0 dropped:0 overruns:0 frame:0
TX packets:945 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:415999 (406.2 KB) TX bytes:757373 (739.6 KB)
Interrupt:16 Base address:0xef00

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:727 errors:0 dropped:0 overruns:0 frame:0
TX packets:727 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:104961 (102.5 KB) TX bytes:104961 (102.5 KB)

and sudo nano /etc/network/interfaces shows


# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo eth0 eth1
iface lo inet loopback

# The primary network interface
iface eth0 inet static
address 86.38.32.250
netmask 255.255.255.248
gateway 86.38.32.254

# The secondary network interface
iface eth1 inet dhcp

and it still not working, also the adres really works (tested on windows).

---

### Post by kamaji792 on 2008-09-25
Checking my **interfaces** file I have an additional line after the gateway line:

**dns-nameservers xxx.xxx.xxx.xxx**

Where xxx.xxx.xxx.xxx is the IP address of my gateway.  Though I am sure you could point it at an Internet nameserver.

There is another way of specifying the nameservers but for the life of me I can't remember it.  I'll check it out when I get to work.

All the best

PS - Check you can ping the gateway (ping -c4 86.38.32.254).

---

### Post by kamaji792 on 2008-09-25
You can also set the nameserers in the **/etc/resolve.conf** file.  The content of mine currently looks like:
```
search localhost
nameserver 123.456.789.98
nameserver 765.432.123.456

```

Hope one of my posts help :)

---

### Post by BIPS on 2008-09-25
i try to pinging to gateway and its Unreachable from server 

benas@86:~$ ping -c4 86.38.32.254
PING 86.38.32.254 (86.38.32.254) 56(84) bytes of data.
From 86.38.32.250 icmp_seq=1 Destination Host Unreachable
From 86.38.32.250 icmp_seq=2 Destination Host Unreachable
From 86.38.32.250 icmp_seq=3 Destination Host Unreachable
From 86.38.32.250 icmp_seq=4 Destination Host Unreachable

--- 86.38.32.254 ping statistics ---
4 packets transmitted, 0 received, +4 errors, 100% packet loss, time 3003ms
, pipe 3


but from home it's works normaly 

C:\Documents and Settings\Benas Linkevi&#269;ius>ping 86.38.3

Pinging 86.38.32.254 with 32 bytes of data:

Reply from 86.38.32.254: bytes=32 time=42ms TTL=57
Reply from 86.38.32.254: bytes=32 time=31ms TTL=57
Reply from 86.38.32.254: bytes=32 time=49ms TTL=57
Reply from 86.38.32.254: bytes=32 time=100ms TTL=57

Ping statistics for 86.38.32.254:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 31ms, Maximum = 100ms, Average = 55ms

tomorow i try from work to ping. also i call to internet provider and ask for help :D thanks for you trying

---

