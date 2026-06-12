---
title: "Ubuntu Server 16 LTS Router configuration issue please help."
date: 2017-09-03
forum: Server Platforms
---

### Post by mcdrichj427 on 2017-09-03
Im setting up my server to do all my routing. The LAN side seems to be working fine (dhcp is assigning ip and connecting) however there is no internet conection to any of the clients. But I can ping [www.google.com](www.google.com) from the server and I get a response. It seems like the server is connected to the internet but doesnt share the connection. Im using isc-dhcp-server. Can someone help me?

Here is what I get when I run ifconfig

```
server:~$ ifconfig enp2s0 Link encap:Ethernet HWaddr 68:05:ca:2d:94:4b inet addr:192.168.0.1 Bcast:192.168.0.255 Mask:255.255.255.0 inet6 addr: fe80::6a05:caff:fe2d:944b/64 Scope:Link UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1 RX packets:2340 errors:0 dropped:0 overruns:0 frame:0 TX packets:336 errors:0 dropped:0 overruns:0 carrier:0 collisions:0 txqueuelen:1000 RX bytes:383418 (383.4 KB) TX bytes:67244 (67.2 KB) Interrupt:17 Memory:fe9e0000-fea00000

enp3s0 Link encap:Ethernet HWaddr 90:e6:ba:bd:6f:c9 inet addr:71.234.240.97 Bcast:255.255.255.255 Mask:255.255.248.0 inet6 addr: fe80::92e6:baff:febd:6fc9/64 Scope:Link UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1 RX packets:1305 errors:0 dropped:0 overruns:0 frame:0 TX packets:2496 errors:0 dropped:0 overruns:0 carrier:0 collisions:0 txqueuelen:1000 RX bytes:1235249 (1.2 MB) TX bytes:251739 (251.7 KB)

lo Link encap:Local Loopback inet addr:127.0.0.1 Mask:255.0.0.0 inet6 addr: ::1/128 Scope:Host UP LOOPBACK RUNNING MTU:65536 Metric:1 RX packets:1625 errors:0 dropped:0 overruns:0 frame:0 TX packets:1625 errors:0 dropped:0 overruns:0 carrier:0 collisions:0 txqueuelen:1 RX bytes:725919 (725.9 KB) TX bytes:725919 (725.9 KB)
```

---

### Post by wildmanne39 on 2017-09-03
*Thread moved to **Server Platforms**.*

---

### Post by ravinippu on 2017-09-04
I have exactly the same issue, i did all as mentioned in this link [https://arstechnica.com/gadgets/2016...-from-scratch/](https://arstechnica.com/gadgets/2016...-from-scratch/)  but no success, also I guess a bug when i do network cable unplugged intensely and then replug and restart the system network manager shows (Ethernet adapter) is unmanaged and you can't do anything with this.

---

### Post by darkod on 2017-09-04
Did you allow ipv4 forwarding in /etc/sysctl.conf? And do you have MASQUERADE rule for iptables?

Those are the only two things you need to make routing possible.

Open /etc/sysctl.conf and check that the ipv4_forward parameter is enabled.

You also need to create one MASQUERADE rule so that outgoing traffic is NATed correctly. And if you use iptables as FW you might also need to allow other traffic, depending.

---

### Post by elico on 2017-09-05
please attach the output of:
sysctl -a |grep v4|grep forward
iptables-save
netstat -ntulp
ss -ntulp

Also do you need isc-dhcp-server specifically because one of it's features?
If it's a tiny server then you'd better use dnsmasq instead.
Also, is it a physical or virtual machine?

---

