---
title: "IP/DNS problem? Ubuntu server+desktop = &quot;no valid net connections found&quot;"
date: 2009-11-27
forum: Server Platforms
---

### Post by tdewire on 2009-11-27
hello! i'm a server newbie putting together a  home network. Here is a diagram of the network so far :[http://imgur.com/AFdwJ.png](http://imgur.com/AFdwJ.png)  

The ubuntu 9.1 desktop says "no valid network connections found" and the live network icon does not appear on the upper right hand corner. But! when i run ethtool eth0 in the terminal I get "Link detected: yes". I can ping the server boxes in the network. I cannot ping the internet. I can ping the internet from both network servers.

The follwing is output from the ubuntu desktop:

ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:13:72:9d:7e:ba  
          inet addr:192.168.0.5  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::213:72ff:fe9d:7eba/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:608 errors:0 dropped:0 overruns:0 frame:0
          TX packets:653 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:79562 (79.5 KB)  TX bytes:66321 (66.3 KB)

route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.255.0   U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         router          0.0.0.0         UG    100    0        0 eth0

traceroute 75.126.162.205
traceroute to 75.126.162.205 (75.126.162.205), 30 hops max, 60 byte packets
 1  * * *
 2  * * *
 3  * * *
 4  * * *
 5  * 204.186.240.197 (204.186.240.197)  8.093 ms  12.094 ms
 6  207.44.127.110 (207.44.127.110)  22.063 ms  16.414 ms  13.539 ms
 7  207.44.122.178 (207.44.122.178)  10.629 ms  12.716 ms  8.985 ms
 8  207.44.125.6 (207.44.125.6)  17.927 ms  15.796 ms  18.389 ms
 9  4.78.132.69 (4.78.132.69)  15.263 ms  16.201 ms  14.912 ms
10  4.68.16.254 (4.68.16.254)  34.183 ms 4.68.16.62 (4.68.16.62)  19.953 ms 4.68.16.190 (4.68.16.190)  20.205 ms
11  4.69.134.113 (4.69.134.113)  14.674 ms 4.69.134.125 (4.69.134.125)  14.453 ms 4.69.134.121 (4.69.134.121)  21.698 ms
12  4.69.137.121 (4.69.137.121)  51.195 ms  50.434 ms  52.185 ms
13  4.69.145.8 (4.69.145.8)  49.363 ms 4.69.145.72 (4.69.145.72)  50.686 ms 4.69.145.8 (4.69.145.8)  49.176 ms
14  4.71.198.18 (4.71.198.18)  49.671 ms  48.683 ms  48.657 ms
15  66.228.118.201 (66.228.118.201)  59.420 ms  60.184 ms  50.676 ms
16  66.228.118.178 (66.228.118.178)  50.171 ms  50.435 ms  50.439 ms
17  75.126.162.205 (75.126.162.205)  57.424 ms  57.436 ms  55.933 ms

nslookup ubuntuforums.org
;; connection timed out; no servers could be reached

thank u 4 ur help!

---

### Post by beniwtv on 2009-11-27
If you have installed with the server install CD, and afterwards installed the GUI, then most likely your interface is configured in the file /etc/network/interfaces, and thus, not available to the NetworkManager icon.

Either remove the interface definition from there, or look at the configuration to determine what's wrong. Probably the default gateway is not set properly.

---

