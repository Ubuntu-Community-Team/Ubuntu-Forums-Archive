---
title: "ubuntu broadcast data in background??"
date: 2017-09-16
forum: Security
---

### Post by unityforever on 2017-09-16
when i plug in my USB mouse or remove it, ubuntu will broadcast a package in local network.

```
23:25:39.559714 IP6 fe80::300c:6942:8d20:82e0.8610 > ip6-allnodes.8612: UDP, length 16
23:25:39.559743 IP6 fe80::300c:6942:8d20:82e0.8610 > ip6-allnodes.8610: UDP, length 16
23:25:39.569838 IP 192.168.1.118.8612 > 192.168.1.255.8612: UDP, length 16
23:25:39.569850 IP 192.168.1.118.8612 > 192.168.1.255.8610: UDP, length 16


```

```
23:25:43.163207 IP 192.168.1.118.42005 > 255.255.255.255.1124: UDP, length 37

```

happen every times.

---

### Post by unityforever on 2017-09-29
anyone?

---

### Post by kevin160 on 2017-09-30
A quick google search for "usb port 8612" revealed 

[https://bugs.kali.org/view.php?id=3094](https://bugs.kali.org/view.php?id=3094)

A canon print driver checks for a printer on the network and on the usb every time a usb device is attached or removed.  Definitely odd but harmless.

---

### Post by TheFu on 2017-10-01
Don't use Canon printers.  Not an Ubuntu issue.

Closed?

---

### Post by kjell-tring on 2018-03-11
Same issue still going on with anything connected to usb, any phone too.

here is a paste from tcpview the 2 first seconds after usb connection
,, it initiates traffic from my computer(myubuntu), at port 8612,
out to broadcast of my particular network at 10.0.1.255 port 8610
then do some not understandable payloads, , then some dns querys,,
then trys more broadcasting to 255.255.255.255 ,, i dont like it..


01:25:02.945142 IP (tos 0x0, ttl 64, id 45856, offset 0, flags [DF], proto UDP (17), length 44)
    myubuntu.8612 > 10.0.1.255.8612: [bad udp cksum 0x172a -> 0x12da!] UDP, length 16
01:25:02.945157 IP (tos 0x0, ttl 64, id 45857, offset 0, flags [DF], proto UDP (17), length 44)
    myubuntu.8612 > 10.0.1.255.8610: [bad udp cksum 0x172a -> 0x07e0!] UDP, length 16
01:25:02.945180 IP6 (flowlabel 0x2bd7f, hlim 1, next-header UDP (17) payload length: 24) fe80::3d8a:dd72:2e02:12aa.8612 > ip6-allnodes.8612: [bad udp cksum 0x5957 -> 0xd0ac!] UDP, length 16
01:25:02.945189 IP6 (flowlabel 0x91751, hlim 1, next-header UDP (17) payload length: 24) fe80::3d8a:dd72:2e02:12aa.8612 > ip6-allnodes.8610: [bad udp cksum 0x5957 -> 0xc5b2!] UDP, length 16
01:25:02.955294 IP (tos 0x0, ttl 64, id 45859, offset 0, flags [DF], proto UDP (17), length 44)
    myubuntu.8612 > 10.0.1.255.8612: [bad udp cksum 0x172a -> 0x12da!] UDP, length 16
01:25:02.955305 IP (tos 0x0, ttl 64, id 45860, offset 0, flags [DF], proto UDP (17), length 44)
    myubuntu.8612 > 10.0.1.255.8610: [bad udp cksum 0x172a -> 0x07e0!] UDP, length 16
01:25:02.955328 IP6 (flowlabel 0x2bd7f, hlim 1, next-header UDP (17) payload length: 24) fe80::3d8a:dd72:2e02:12aa.8612 > ip6-allnodes.8612: [bad udp cksum 0x5957 -> 0xd0ac!] UDP, length 16
01:25:03.039747 IP (tos 0x0, ttl 64, id 8572, offset 0, flags [DF], proto UDP (17), length 118)
    myubuntu.59880 > Inteno.lan.domain: [bad udp cksum 0x1676 -> 0x5fbd!] 10971+ PTR? a.a.2.1.2.0.e.2.2.7.d.d.a.8.d.3.0.0.0.0.0.0.0.0.0.0.0.0.0.8.e.f.ip6.arpa. (90)
01:25:03.067669 IP (tos 0x0, ttl 64, id 0, offset 0, flags [DF], proto UDP (17), length 167)
    Inteno.lan.domain > myubuntu.59880: [udp sum ok] 10971 NXDomain* q: PTR? a.a.2.1.2.0.e.2.2.7.d.d.a.8.d.3.0.0.0.0.0.0.0.0.0.0.0.0.0.8.e.f.ip6.arpa. 0/1/0 ns: 8.E.F.IP6.ARPA. SOA 8.E.F.IP6.ARPA. . 0 28800 7200 604800 86400 (139)
01:25:03.067882 IP (tos 0x0, ttl 64, id 8573, offset 0, flags [DF], proto UDP (17), length 67)
    myubuntu.33583 > Inteno.lan.domain: [bad udp cksum 0x1643 -> 0xe0db!] 630+ PTR? 1.1.0.10.in-addr.arpa. (39)
01:25:03.068783 IP (tos 0x0, ttl 64, id 0, offset 0, flags [DF], proto UDP (17), length 91)
    Inteno.lan.domain > myubuntu.33583: [udp sum ok] 630* q: PTR? 1.1.0.10.in-addr.arpa. 1/0/0 1.1.0.10.in-addr.arpa. PTR Inteno.lan. (63)
01:25:03.612074 IP (tos 0x0, ttl 64, id 42027, offset 0, flags [DF], proto UDP (17), length 43)
    myubuntu.35590 > 255.255.255.255.3289: [bad udp cksum 0x0b2a -> 0x74f0!] UDP, length 15
01:25:03.612196 IP (tos 0x0, ttl 64, id 8688, offset 0, flags [DF], proto UDP (17), length 74)
    myubuntu.53418 > Inteno.lan.domain: [bad udp cksum 0x164a -> 0x9421!] 36500+ PTR? 255.255.255.255.in-addr.arpa. (46)
01:25:03.639342 IP (tos 0x0, ttl 64, id 0, offset 0, flags [DF], proto UDP (17), length 137)
    Inteno.lan.domain > myubuntu.53418: [udp sum ok] 36500* q: PTR? 255.255.255.255.in-addr.arpa. 0/1/0 ns: 255.255.255.255.IN-ADDR.ARPA. SOA 255.255.255.255.IN-ADDR.ARPA. . 0 28800 7200 604800 86400 (109)
01:25:04.621492 IP (tos 0x0, ttl 64, id 42197, offset 0, flags [DF], proto UDP (17), length 65)
    myubuntu.46278 > 255.255.255.255.1124: [bad udp cksum 0x0b40 -> 0x961c!] UDP, length 37

---

