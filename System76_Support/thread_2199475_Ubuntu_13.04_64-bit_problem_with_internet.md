---
title: "Ubuntu 13.04 64-bit problem with internet"
date: 2014-01-14
forum: System76 Support
---

### Post by kovalev32 on 2014-01-14
I use galago ultra pro with  Intel® Dual Band Wireless-AC 7260 802.11

Problem: constantly downloaded some data from the Internet. It makes use of the internet is very difficult.
What could be the reason?
P.S. When I connect to the Internet via cable, there is no problem.

evgeny@galago:~$ uname -a
Linux galago 3.11.0-15-generic #23-Ubuntu SMP Mon Dec 9 18:17:04 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

evgeny@galago:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:90:f5:f0:76:3b  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 &#1055;&#1072;&#1084;&#1103;&#1090;&#1100;:f7e00000-f7e20000 

lo        Link encap:&#1051;&#1086;&#1082;&#1072;&#1083;&#1100;&#1085;&#1072;&#1103; &#1087;&#1077;&#1090;&#1083;&#1103; (Loopback)  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:340 errors:0 dropped:0 overruns:0 frame:0
          TX packets:340 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:48823 (48.8 KB)  TX bytes:48823 (48.8 KB)

wlan0     Link encap:Ethernet  HWaddr 0c:8b:fd:5f:22:6a  
          inet addr:192.168.0.104  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::e8b:fdff:fe5f:226a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:397616 errors:0 dropped:0 overruns:0 frame:0
          TX packets:62057 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:551469126 (551.4 MB)  TX bytes:6178980 (6.1 MB)

---

### Post by kovalev32 on 2014-01-14
evgeny@galago:~$ sudo netstat -vantup
Proto Recv-Q Send-Q Local Address Foreign Address State       PID/Program name
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      843/cupsd       
tcp        0      0 127.0.1.1:53            0.0.0.0:*               LISTEN      1679/dnsmasq    
tcp6       0      0 ::1:631                 :::*                    LISTEN      843/cupsd       
udp        0      0 0.0.0.0:60587           0.0.0.0:*                           756/avahi-daemon: r
udp        0      0 0.0.0.0:5353            0.0.0.0:*                           756/avahi-daemon: r
udp        0      0 127.0.1.1:53            0.0.0.0:*                           1679/dnsmasq    
udp        0      0 0.0.0.0:68              0.0.0.0:*                           1604/dhclient   
udp        0      0 0.0.0.0:64020           0.0.0.0:*                           1604/dhclient   
udp        0      0 0.0.0.0:631             0.0.0.0:*                           964/cups-browsed
udp6       0      0 :::58396                :::*                                1604/dhclient   
udp6       0      0 :::5353                 :::*                                756/avahi-daemon: r
udp6       0      0 :::36913                :::*                                756/avahi-daemon: r

---

