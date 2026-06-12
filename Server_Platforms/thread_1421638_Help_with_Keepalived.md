---
title: "Help with Keepalived"
date: 2010-03-04
forum: Server Platforms
---

### Post by SDStorts on 2010-03-04
I am using keepalived for a project that it probably wasn't intended for but I'm hoping it will work for my application.  I have been running into an issue with it that I hope someone here can help me with.  I will explain my setup first.
Our company has two separate ISP's with one being the main and the other the failover.  We have anywhere from 100 to 250 internet users depending on the time of year.  All of these users go through a filtered proxy server in order to get to the internet.  I have two physical servers setup for the proxy(one is the main and the other the failover both running ubuntu 9.10 server 32 bit).  Server 1 has two interfaces. one has a direct connection to the main ISP and the other is internal. Server 2 has one interface(currently) with a nat'd connection to the failover ISP.  I have setup keepalived on these servers to failover to the second server if the first server dies.  both of these servers work well as a proxy with this setup and the failover is quick(about a second or 2) when the first Server loses it's VIP.  I would like to set it up to failover if the internet connection dies on the first server.  Right now the only thing that causes the failover is if the first server loses the virtual IP.  That doesn't help when the internet connection dies.  I have looked into ICMP_CHECK to a public server or HTTP_CHECK but I haven't found much documentation describing how this can be done.  

here is the keepalived.conf files of both servers:

vrrp_instance VI_1 {
 state MASTER
 interface eth1
 virtual_router_id 80
 priority 100
 authentication {
  auth_type PASS
  auth_pass password
 }
 virtual_ipaddress {
  10.10.10.80/24 brd 10.10.10.255 dev eth1
}

vrrp_instance VI_1 {
 state BACKUP
 interface eth1
 virtual_router_id 80
 priority 50
 authentication {
  auth_type PASS
  auth_pass password
 }
 virtual_ipaddress {
  10.10.10.80/24 brd 10.10.10.255 dev eth1
}

Thanks in advance.

---

