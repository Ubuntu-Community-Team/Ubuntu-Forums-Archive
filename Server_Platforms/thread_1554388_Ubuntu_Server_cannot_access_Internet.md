---
title: "Ubuntu Server cannot access Internet"
date: 2010-08-16
forum: Server Platforms
---

### Post by juancpryor on 2010-08-16
I just installed Ubuntu server on my Dell, and connection to the Internet (though cable) had no problem accesing as client when I had auto DHCP. 
 
I pretend to use the server as a mail/web server so I got a static IP from the local ISP. We forwarded the public IP to the local IP 192.168.0.50. 
 
The problem is that when I try to find the server from inside the network (local IP) there's no problem ("It works!") but I cannot reach it from outside the network (public IP) plus I have no access as a client to the internet from the server...sooo....
 
Any help???
 
ifconfig eth01
 
Link encap: Ehternet HWaddr 00:80:54:b0:17:6c
inet addr: 192.168.0.50 Bcast: 192.168.0.255 Mask: 255.255.255.0
inet6 addr: (stated address) Scope: Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets: 49708 errors: 0 dropped: 0 overrun: 0 frame: 0
TX packets: 7701 errors: 0 dropped: 0 overrun: 0 carrier: 0
collisiones: 0 txqueuelen: 1000
RX bytes: 6468789(6.4 MB) TX bytes 752183 (752.1 KB)
Interrupt: 11 Base address: 0xe880
 
 
etc/network/interfaces states:
 
auto eth1
iface eth1 inet static
address 192.168.0.50
netmask 255.255.255.0
gateway 192.168.0.1
broadcast 192.168.0.255
network 192.168.0.0
 
I placed the last two lines (although I understand they are default) because I was getting another error.

---

### Post by arrrghhh on 2010-08-16
If you're trying to access your server from the WAN, you'll need to open some ports.

Ubuntu by default doesn't have any ports 'listening', and therefore UFW (the default firewall config app) comes disabled out of the box.  It's basically a frontend for iptables if you prefer that method.

So assuming a vanilla Ubuntu install, the firewall in it is not the issue.  I would recommend enabling UFW and configuring it, however.

Do you have a router between your server and cable modem?  You'll need to open the necessary ports on that device - whatever services you're running - for http you need to open port 80, for ssh port 22, etc.

---

### Post by juancpryor on 2010-08-16
I have a Huawei Echolife HG520s, which basically acts both as modem and a router. I set it up so it would receive all incoming traffic directly to 192.68.0.50.
 
I'm thinking that something in the router configuration must be messed up but I cannot access it directly, only the ISP has the full access codes, i only have basic access. 
 
Still, the server should still have access to navigate the internet, which it has when I set it up as a dynamic IP, but when I set it to static, it stops working.

---

### Post by arrrghhh on 2010-08-17
When you configure the IP address statically, you also have to configure a DNS server manually.  Did you do that?  DHCP normally provides all those numbers automatically.

The file you need to modify for DNS is /etc/resolv.conf.

A way to check would be to ping [www.google.com](www.google.com) or equivalent from the server.  It'll probably fail.  Now ping it from a machine that has internet connectivity - it should give replies.  Take that IP address down and try pinging that (for example 74.125.224.18) and see if you can ping that from the server.  If you can, your issue is DNS name resolution.  If you still can't ping an external IP that you can from another machine, then there's something else that is wrong.

So what do you have access to configure on the router?  Can you set the DHCP pool range?  Usually you'd want it 100+ so you can configure static addresses as anything ending in less than 100 if that makes sense.

Example - DHCP pool of 100 addresses - 192.168.0.100-192.168.0.200, that way you can configure anything statically as 192.168.0.2-192.168.0.99 (.1 would be your gateway, typically).

---

