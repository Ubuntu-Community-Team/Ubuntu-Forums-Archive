---
title: "Set up private network using Squid and Switch"
date: 2011-11-20
forum: Server Platforms
---

### Post by palantir6er on 2011-11-20
So I have multiple machines, a switch box, and only one ethernet connection. I have a Ubuntu 10.04 server with 2 network interface cards where eth0 is configured in /etc/netowrk/interfaces to have the static ip address, subnet, etc I have been assigned by my isp. On this server I have a web server (which is already working fine) and Squid proxy server.

Goal: Have the 2nd interface card on my server connect to my switch and connect all my machines to this switch via ethernet cable so that they can all access the internet (through the switch and then through the server with 2 NICs). 

I have already configured Squid to accept connections from my laptop's ip temporarily and can proxy through my server. I want a transparent proxy so that all my desktop machines can access the internet. In squid config, I have allowed a private ip range like 192.168.0.0/24 to be allowed to proxy through the server, but I don't know how to configure the 2nd NIC of the server or how to configure all my linux machines which will connect to the switch? Any insights? 


*Note: I'm aware you could buy routers and whatnot to do this kind of stuff, but I want to figure this out and play around with it.

---

### Post by newbie-user on 2011-11-20
On the server, you have to enable ip forwarding within /etc/sysctl.conf by uncommenting the line:

  #net.ipv4.ip_forward=1

Then you have to edit squid.conf and add the following line to make squid transparent:

  http_port 3128 transparent

Next you'd have to configure iptables to route all port 80 requests from the LAN to port 3128, which is the squid port:

  iptables -A PREROUTING -i eth1 -p tcp -m tcp --dport 80 -j REDIRECT --to-ports 3128

You'd also have to configure your DHCP server to tell the clients which gateway to use (ip address of eth1 your squid server).  I assume you're serving DHCP from your Ubuntu server, so add the following line to your subnet declaration:

  option routers [ip address of eth1];

That should get you started.

---

