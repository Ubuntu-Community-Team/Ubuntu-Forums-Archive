---
title: "Manually change network setting and coannt be reach by order network"
date: 2012-08-15
forum: Server Platforms
---

### Post by eriled on 2012-08-15
I install ubuntu 12.04 and I change the /etc/network/interfaces to have a manual ip set
 
auto eth0
iface eth0 inet static
address 11.95.16.23
getway 11.95.16.51
netmask 255.255.240.0
broadcast 11.95.31.255
 
but when I resart the networking I can't ping external network 192.0.0.XXX
 
Befor I do the change is work ok... 
So what I need change to make it works?
 
I copie you the ifconfig when is set by dhcp...
login as: bitnami
bitnami@11.95.16.23's password:
Welcome to Ubuntu 12.04 LTS (GNU/Linux 3.2.0-24-virtual x86_64)
* Documentation: [https://help.ubuntu.com/](https://help.ubuntu.com/)
Last login: Wed Aug 15 00:41:37 2012
bitnami@wg-Alfresco-01:~$ ifconfig
eth0 Link encap:Ethernet HWaddr 00:0c:29:39:bb:c3
inet addr:11.95.16.124 Bcast:11.95.31.255 Mask:255.255.240.0
inet6 addr: fe80::20c:29ff:fe39:bbc3/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:15763 errors:0 dropped:0 overruns:0 frame:0
TX packets:1596 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:1312793 (1.3 MB) TX bytes:1795241 (1.7 MB)
lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:46946 errors:0 dropped:0 overruns:0 frame:0
TX packets:46946 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:22625246 (22.6 MB) TX bytes:22625246 (22.6 MB)

---

