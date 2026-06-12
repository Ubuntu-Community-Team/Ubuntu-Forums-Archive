---
title: "guest networking not working"
date: 2008-08-29
forum: Virtualisation
---

### Post by Mykal73 on 2008-08-29
I have a ubuntu 8.04 host machine with a windows xp pro guest under virtualbox 1.6.4. I used to be able to be able to utilize host networking to connect to the network. I applied some updates on Tuesday and now I cannot get the guest to access the network. Does anyone have any ideas?:confused:

---

### Post by Thelasko on 2008-08-29
Obvious question, but I have to ask it.  Is the network card enabled in the VirtualBox settings?

---

### Post by Mykal73 on 2008-09-02
Sorry it took so long to get back to you. Yes, networking is enabled in virtualbox and I've built the bridge according to the instructions I've found here: [http://samiux.wordpress.com/2008/07/30/bridging-virtualbox-162-on-ubuntu-8041/](http://samiux.wordpress.com/2008/07/30/bridging-virtualbox-162-on-ubuntu-8041/). 

my ifconfig output follows:

br0       Link encap:Ethernet  HWaddr 00:1c:23:49:29:19  
          inet addr:192.168.10.62  Bcast:192.168.10.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:23ff:fe49:2919/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2319 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1242 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1832153 (1.7 MB)  TX bytes:130988 (127.9 KB)

eth0      Link encap:Ethernet  HWaddr 00:1c:23:49:29:19  
          inet6 addr: fe80::21c:23ff:fe49:2919/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2424 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1402 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1883236 (1.7 MB)  TX bytes:146460 (143.0 KB)
          Interrupt:17 

eth1      Link encap:Ethernet  HWaddr 00:16:44:bd:d3:f4  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1512 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1512 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:75600 (73.8 KB)  TX bytes:75600 (73.8 KB)

vbox0     Link encap:Ethernet  HWaddr 00:ff:ac:29:cd:a4  
          inet6 addr: fe80::2ff:acff:fe29:cda4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:539 errors:0 dropped:0 overruns:0 frame:0
          TX packets:697 errors:0 dropped:672 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:90249 (88.1 KB)  TX bytes:101982 (99.5 KB)

---

### Post by mellowd on 2008-09-02
Are you able to ping anything on the network? What's the IP address of the guest machine? What's it's default gateway?

---

### Post by Mykal73 on 2008-09-02
I can only reach the host machine. I can't contact my default gateway or my DNS servers on the guest machine (windows xp pr0 sp3). I can force a static ip address on the guest machine but the connection still doesn't get outside of the host machine. I've noticed that the vbox0 interface is dropping a lot of TX packets. If I try to contact the bridge on the host machine via ping or tracert it says "destination host unreachable" .

---

### Post by mellowd on 2008-09-02
What are the addresses given

---

### Post by Mykal73 on 2008-09-02
I'm using dhcp to configure my bridge, and it was given a 192.168.10.62 address. If I release/renew the ip in the guest machine it gives me 169.254.128.166.

---

### Post by Mykal73 on 2008-09-03
OK, I got it to work, I had to start the virtual machine with the virtual cable disconnected (in the network settings) and then connect the cable once the vm had started. Hopefully this works for anyone else that has a similar issue.:-s

---

