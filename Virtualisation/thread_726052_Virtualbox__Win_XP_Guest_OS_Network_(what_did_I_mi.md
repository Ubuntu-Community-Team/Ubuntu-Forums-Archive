---
title: "Virtualbox:  Win XP Guest OS Network (what did I miss?)"
date: 2008-03-16
forum: Virtualisation
---

### Post by gambrjl on 2008-03-16
OK.  I've been through the virtualbox tutorial here and read through others.  I'm trying to get my work VPN to work in WinXP as the guest OS

[Link 1](http://paparadit.blogspot.com/2007/08/virtualbox-windows-xp-guest-in-linux.html)

and the virtualbox documentation on help.ubuntu.com

I created the bridge (br0) and the host (tap1) and bridged them together (at least I think I did)

When I go into Virtual box and set the network adapter to host and use "tap1" I'm not getting an ethernet connection anymore.

Here's my ifconfig.  what else do I need to show?  I can't figure out what I'm missing

```

br0       Link encap:Ethernet  HWaddr 00:1C:BF:32:34:D7  
          inet addr:192.168.2.102  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:bfff:fe32:34d7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:19388 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16726 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:18692256 (17.8 MB)  TX bytes:2360696 (2.2 MB)

eth0      Link encap:Ethernet  HWaddr 00:15:C5:7F:55:C2  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 

eth1      Link encap:Ethernet  HWaddr 00:1C:BF:32:34:D7  
          inet6 addr: fe80::21c:bfff:fe32:34d7/64 Scope:Link
          UP BROADCAST RUNNING PROMISC MULTICAST  MTU:1500  Metric:1
          RX packets:19384 errors:162 dropped:12752 overruns:0 frame:0
          TX packets:16898 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:136897901 (130.5 MB)  TX bytes:7850818 (7.4 MB)
          Interrupt:17 Base address:0xa000 Memory:fe8ff000-fe8fffff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:130 errors:0 dropped:0 overruns:0 frame:0
          TX packets:130 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6500 (6.3 KB)  TX bytes:6500 (6.3 KB)

tap1      Link encap:Ethernet  HWaddr 00:FF:0E:7D:29:62  
          inet6 addr: fe80::2ff:eff:fe7d:2962/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:147 errors:0 dropped:0 overruns:0 frame:0
          TX packets:261 errors:0 dropped:506 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:19452 (18.9 KB)  TX bytes:72028 (70.3 KB)

```

---

### Post by harvey186 on 2008-03-16
Hi, here is my working ipconfig. I have created a vbox0 for the bridge as descriped in the manual. It works fine.


br0       Protokoll:Ethernet  Hardware Adresse 00:1D:60:EA:C6:C9
          inet Adresse:192.168.1.4  Bcast:192.168.1.127  Maske:255.255.255.128
          inet6 Adresse: fe80::21d:60ff:feea:c6c9/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6435960 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16444130 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:0
          RX bytes:679413101 (647.9 MB)  TX bytes:22523287822 (20.9 GB)

eth0      Protokoll:Ethernet  Hardware Adresse 00:1D:60:EA:B7:19
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:23 Basisadresse:0xe000

eth1      Protokoll:Ethernet  Hardware Adresse 00:1D:60:EA:C6:C9
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6739480 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16648688 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000
          RX bytes:1078254784 (1.0 GB)  TX bytes:22608766933 (21.0 GB)
          Interrupt:22

lo        Protokoll:Lokale Schleife
          inet Adresse:127.0.0.1  Maske:255.0.0.0
          inet6 Adresse: ::1/128 Gültigkeitsbereich:Maschine
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:611 errors:0 dropped:0 overruns:0 frame:0
          TX packets:611 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:0
          RX bytes:186092 (181.7 KB)  TX bytes:186092 (181.7 KB)

vbox0     Protokoll:Ethernet  Hardware Adresse 00:FF:5F:94:8F:EF
          inet6 Adresse: fe80::2ff:5fff:fe94:8fef/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:206178 errors:0 dropped:0 overruns:0 frame:0
          TX packets:305392 errors:0 dropped:3425 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:500

---

### Post by gambrjl on 2008-03-16
are there special network settings on the guest OS that need to be done?  It's just set at DHCP from the TCP/IP protocol right now in XP

---

### Post by Jose Catre-Vandis on 2008-03-16
Worth trying a fixed IP address in your guest if you are not able to pick up one with DHCP?

---

### Post by scottro on 2008-03-16
I have a page on this--it's not really Ubuntu oriented but the principle should be the same.  

(In part, as was said, the guest O/S probably wants a static IP.)

Edit--it might help to put the link

[http://home.nyc.rr.com/computertaijutsu/vboxbridge.html](http://home.nyc.rr.com/computertaijutsu/vboxbridge.html)

---

### Post by Silvr2008 on 2008-03-17
I got mine to work by typing *sysctl net.ipv4.ip_forward=1* in the terminal. Then setting the network setting in VB to NAT. After reading the manual, I still can't get it to work when attached to a host interface though.

---

### Post by scottro on 2008-03-17
As I said in  [http://ubuntuforums.org/showthread.php?t=724783](http://ubuntuforums.org/showthread.php?t=724783)
let's try to keep it on one thread so I don't get confused. :)

You are trying to get wireless bridging to work, correct?  
(Please answer on the other thread, unless this is about wired bridging. In that case, it probably merits two threads.)

---

