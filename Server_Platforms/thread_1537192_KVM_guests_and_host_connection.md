---
title: "KVM guests and host connection?"
date: 2010-07-23
forum: Server Platforms
---

### Post by stegus on 2010-07-23
We got a new server with 2 network interface cards with 4 MAC addresses in total. 
We would like to run two virtual machines (*vserver1* and *vserver2*); one should connect via 
eth1, the other via eth2, and the host (*mainserver*) via eth0.
The content of */etc/network/interfaces* is as follows:
```
auto lo
iface lo inet loopback

#### mainserver
auto eth0
iface eth0 inet static
        address XXX.xx.XXX.32
        netmask 255.255.255.0
        network XXX.xx.XXX.0
        broadcast XXX.xx.XXX.255
        gateway XXX.xx.XXX.49
        dns-nameservers XXX.xx.XXX.7 XXX.xx.XXX.3
        dns-search subdomain.domain.de

#### vserver1
auto br1
iface br1 inet static
    address XXX.xx.XXX.33
    netmask 255.255.255.0
    network XXX.xx.XXX.0
    broadcast XXX.xx.XXX.255
    gateway XXX.xx.XXX.49
    bridge_ports eth1
    bridge_stp off
    bridge_maxwait 0
    dns-nameservers XXX.xx.XXX.7 XXX.xx.XXX.3
    dns-search subdomain.domain.de


#### vserver2
auto br2
iface br2 inet static
    address XXX.xx.XXX.35
    netmask 255.255.255.0
    network XXX.xx.XXX.0
    broadcast XXX.xx.XXX.255
    gateway XXX.xx.XXX.49
    bridge_ports eth2
    bridge_stp off
    bridge_maxwait 0
    dns-nameservers XXX.xx.XXX.7 XXX.xx.XXX.3
    dns-search subdomain.domain.de
```We added a few lines to /etc/sysctl.conf; we already tried different combinations of these lines:
```

net.ipv4.conf.all.arp_ignore=1
net.ipv4.conf.all.arp_announce=2

#net.ipv4.icmp_echo_ignore_broadcasts=1

net.ipv4.ip_forward=1
net.ipv6.conf.all.forwarding=1

net.bridge.bridge-nf-call-ip6tables = 0
net.bridge.bridge-nf-call-iptables = 0
net.bridge.bridge-nf-call-arptables = 0

```Output from *ifconfig* is:
```
br1       Link encap:Ethernet  Hardware Adresse 00:15:17:dd:e7:c3  
          inet Adresse:XXX.xx.XXX.33  Bcast:XXX.xx.XXX.255  Maske:255.255.255.0
          inet6-Adresse: fe80::215:17ff:fedd:e7c3/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metrik:1
          RX packets:5638 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:0 
          RX bytes:462110 (462.1 KB)  TX bytes:1022 (1.0 KB)

br2       Link encap:Ethernet  Hardware Adresse 00:25:90:04:eb:62  
          inet Adresse:XXX.xx.XXX.35  Bcast:XXX.xx.XXX.255  Maske:255.255.255.0
          inet6-Adresse: fe80::225:90ff:fe04:eb62/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metrik:1
          RX packets:5638 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:0 
          RX bytes:462002 (462.0 KB)  TX bytes:368 (368.0 B)

eth0      Link encap:Ethernet  Hardware Adresse 00:15:17:dd:e7:c2  
          inet Adresse:XXX.xx.XXX.32  Bcast:XXX.xx.XXX.255  Maske:255.255.255.0
          inet6-Adresse: fe80::215:17ff:fedd:e7c2/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metrik:1
          RX packets:17485289 errors:0 dropped:0 overruns:0 frame:0
          TX packets:914625 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX bytes:25387596277 (25.3 GB)  TX bytes:161282993 (161.2 MB)
          Speicher:fafe0000-fb000000 

eth1      Link encap:Ethernet  Hardware Adresse 00:15:17:dd:e7:c3  
          inet6-Adresse: fe80::215:17ff:fedd:e7c3/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metrik:1
          RX packets:6036 errors:0 dropped:0 overruns:0 frame:0
          TX packets:176 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX bytes:586964 (586.9 KB)  TX bytes:28029 (28.0 KB)
          Speicher:faf80000-fafa0000 

eth2      Link encap:Ethernet  Hardware Adresse 00:25:90:04:eb:62  
          inet6-Adresse: fe80::225:90ff:fe04:eb62/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metrik:1
          RX packets:5846 errors:0 dropped:0 overruns:0 frame:0
          TX packets:65 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX bytes:569024 (569.0 KB)  TX bytes:7797 (7.7 KB)
          Speicher:face0000-fad00000 

lo        Link encap:Lokale Schleife  
          inet Adresse:127.0.0.1  Maske:255.0.0.0
          inet6-Adresse: ::1/128 Gültigkeitsbereich:Maschine
          UP LOOPBACK RUNNING  MTU:16436  Metrik:1
          RX packets:372 errors:0 dropped:0 overruns:0 frame:0
          TX packets:372 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:0 
          RX bytes:35196 (35.1 KB)  TX bytes:35196 (35.1 KB)

vnet0     Link encap:Ethernet  Hardware Adresse 62:d9:ff:3a:f1:db  
          inet6-Adresse: fe80::60d9:ffff:fe3a:f1db/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metrik:1
          RX packets:178 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5889 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:500 
          RX bytes:27869 (27.8 KB)  TX bytes:566691 (566.6 KB)

vnet1     Link encap:Ethernet  Hardware Adresse c6:c8:50:31:18:66  
          inet6-Adresse: fe80::c4c8:50ff:fe31:1866/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metrik:1
          RX packets:72 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5697 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:500 
          RX bytes:8039 (8.0 KB)  TX bytes:548685 (548.6 KB) 

```The nameserver knows the correct IPs of the three machines (eth0, br1, br2). 
All machines (*mainserver*, *vserver1*, *vserver2*) are accessible via ssh from our network and even from the outside. 
A connection from *vserver1* to *vserver2* (and vice versa) or from *vserverx* to any machine in our network or to the outside is possible without problems.

**Now the problem: **
After login (via ssh) to *vserver1*, a connection to *mainserver* (ping, ssh) is not possible:
    *ssh: connect to host mainserver port 22: No route to host*

A connection from *mainserver* to *vserver1* or *vserver2* is not possible; a ssh connection from *mainserver* to *vserverx* ends with a login to *mainserver*.

Any help is appreciated.

---

### Post by clrg on 2010-07-23
May I see

```
netstat -rn
```

---

### Post by stegus on 2010-07-24
Of course. Thanks.
*netstat -rn*
```
Kernel-IP-Routentabelle
Ziel            Router          Genmask         Flags   MSS Fenster irtt Iface
XXX.xx.XXX.33   0.0.0.0         255.255.255.255 UH        0 0          0 br3
XXX.xx.XXX.0    0.0.0.0         255.255.255.0   U         0 0          0 eth0
XXX.xx.XXX.0    0.0.0.0         255.255.255.0   U         0 0          0 br2
XXX.xx.XXX.0    0.0.0.0         255.255.255.0   U         0 0          0 br1
0.0.0.0         XXX.xx.XXX.49   0.0.0.0         UG        0 0          0 br2
0.0.0.0         XXX.xx.XXX.49   0.0.0.0         UG        0 0          0 eth0
```XXX.xx.XXX.33 is *vserver1*; XXX.xx.XXX.49 is the router; *vserver2 *is down[I].
[/I]

---

