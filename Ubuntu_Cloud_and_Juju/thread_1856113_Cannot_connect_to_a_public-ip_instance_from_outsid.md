---
title: "Cannot connect to a public-ip instance from outside"
date: 2011-10-07
forum: Ubuntu Cloud and Juju
---

### Post by mengxr on 2011-10-07
We are using Ubuntu UEC 11.04. The server's IP is

a.b.c.122

and the server is an IP provider and there are 50 IPs reserved:

a.b.c.150-a.b.c.199

I launched three instances with public IPs:

a.b.c.150, a.b.c.151, a.b.c.152

I can ssh to them from the server but not from outside.

I attached the ifconfig output and the "ip addr show" output from the server. I don't quite understand how to let computers outside know that those IPs are provided by the server. Your help would be greatly appreciated!

==========================================================
eth0      Link encap:Ethernet  HWaddr 
          inet addr:a.b.c.122  Bcast:a.b.c.255  Mask:255.255.255.0
          inet6 addr:  Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:59792 errors:0 dropped:0 overruns:0 frame:0
          TX packets:42988 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:20505623 (20.5 MB)  TX bytes:26502735 (26.5 MB)
          Interrupt:36 Memory:f2000000-f2012800 

eth1      Link encap:Ethernet  HWaddr 
          inet addr:192.168.10.1  Bcast:192.168.10.255  Mask:255.255.255.0
          inet6 addr:  Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:582385 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3309102 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:66207221 (66.2 MB)  TX bytes:4694847918 (4.6 GB)
          Interrupt:48 Memory:f4000000-f4012800 

eth0:pub  Link encap:Ethernet  HWaddr 
          inet addr:a.b.c.150  Bcast:0.0.0.0  Mask:255.255.255.255
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:36 Memory:f2000000-f2012800 

eth1:metadata Link encap:Ethernet  HWaddr 
          inet addr:169.254.169.254  Bcast:0.0.0.0  Mask:255.255.255.255
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:48 Memory:f4000000-f4012800 

eth1:priv Link encap:Ethernet  HWaddr  
          inet addr:172.19.1.1  Bcast:172.19.1.31  Mask:255.255.255.224
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:48 Memory:f4000000-f4012800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:250348 errors:0 dropped:0 overruns:0 frame:0
          TX packets:250348 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:55578166 (55.5 MB)  TX bytes:55578166 (55.5 MB)
======================================
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 16436 qdisc noqueue state UNKNOWN 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP qlen 1000
    link/ether brd ff:ff:ff:ff:ff:ff
    inet a.b.c.122/24 brd a.b.c.255 scope global eth0
    inet a.b.c.150/32 scope global eth0:pub
    inet a.b.c.151/32 scope global eth0:pub
    inet a.b.c.152/32 scope global eth0:pub
    inet6  scope link 
       valid_lft forever preferred_lft forever
3: eth1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP qlen 1000
    link/ether  brd ff:ff:ff:ff:ff:ff
    inet 169.254.169.254/32 scope link eth1:metadata
    inet 192.168.10.1/24 brd 192.168.10.255 scope global eth1
    inet 172.19.1.1/27 brd 172.19.1.31 scope global eth1:priv
    inet6  scope link 
       valid_lft forever preferred_lft forever
===================================================

---

### Post by mengxr on 2011-10-08
[SOLVED] It is an upstream firewall issue. After we opened ssh ports, we could connect to the public-IP instances from outside.

---

