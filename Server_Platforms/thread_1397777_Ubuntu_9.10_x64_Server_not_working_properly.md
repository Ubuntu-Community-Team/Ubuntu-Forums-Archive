---
title: "Ubuntu 9.10 x64 Server not working properly"
date: 2010-02-03
forum: Server Platforms
---

### Post by dexter4000 on 2010-02-03
Hello all, 

Here's the problem i have with my server. Its running ubuntu 9.10 fresh installed 64bit version with dual gigabit nic Intel Pro 1000 MT. 
 -eth0 is connected to att uverse gateway on dmz .
 -eth1 is doing DHCP on 24 port switch.

For some reason i cant get the server to be able to reach the internet from intranet. If i ping the external ip of eth0 is pinging , and i'm able to connect to the server. If i connect a computer on the eth1 its getting a ip and i can ping the server locally but i cant ping google.com . I tried all the instruction on how to configure dhcp on ubuntu but its still not working.

Anyone any idea ?

Thanks.

---

### Post by adam814 on 2010-02-03
Are you able to connect to the internet *from* your server?  Can you ping external sites from the console?

---

### Post by dexter4000 on 2010-02-03
yeah i can ping and i can connect to the internet from the server(console) fine.  The machines the are on dhcp cant connect to the internet.

---

### Post by adam814 on 2010-02-03
Do you have IP forwarding enabled?  There are 2 options for it in /etc/sysctl.conf (one only applies to IPv6 though).  This will enable the in-kernel IP forwarding, which you'll need for what you're doing.

Also, have you set up any firewall rules to do the actual NAT?  The part of this guide for doing IP Masquerading with ufw is pretty good:
[https://help.ubuntu.com/8.04/serverguide/C/firewall.html](https://help.ubuntu.com/8.04/serverguide/C/firewall.html)

The last time I set up a router I also ran a DNS server on it.  This isn't strictly necessary, you could just pass your DNS servers as DHCP options, but it's not much more difficult either and it'll probably lower your latency.

---

### Post by dexter4000 on 2010-02-03
yeah i have all that but still not working. for some reason the internal traffic never hits the outside network(internet)

---

### Post by adam814 on 2010-02-03
Post the output of "route -n" from your router.  Also try to post at least the part from your dhcpd.conf for your local subnet.

---

### Post by dexter4000 on 2010-02-03
this is the output of the "route -n" command:

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.10.0    0.0.0.0         255.255.255.0   U     0      0        0 eth1
99.23.208.0     0.0.0.0         255.255.252.0   U     0      0        0 eth0
0.0.0.0         99.23.208.1     0.0.0.0         UG    100    0        0 eth0

and attached is the dhcpd.conf file

---

### Post by adam814 on 2010-02-03
The only thing I notice different from my setup is you have some options for your subnet outside the subnet declaration in your dhcpd.conf.  Of course just because it's different doesn't mean it's wrong.  Are the machines getting the proper IP addresses?

---

### Post by dexter4000 on 2010-02-03
yeah the machines get proper ips and everything works on local network but none of the machines can reach internet. I have no idea whats wrong. Could it be the network card ?

---

### Post by adam814 on 2010-02-03
It's hard to rule anything out for sure.  I suppose you could check that pinging a machine on the subnet from the router.  If you get your ping packets back your NIC is probably OK.

---

