---
title: "Load Balancing HTTP POSTS Across Multiple Adapters"
date: 2009-11-16
forum: Server Platforms
---

### Post by BeardedChimp on 2009-11-16
I have multiple adapters running on different domains through different ISPS that need load balanced.
I've attached a terribly drawn diagram but the basic idea is:

computer that creates chunks -> router that is connected to x adapters -> server sitting on the internet.

Each chunk is sent as an HTTP post and will be about 50KB in size. Therefore each whole post will have to be sent down one adapter. This prevents me from using bonding as bonding operates on the per packet level and does not work across multiple ISPs.

Other load balancing methods involve having each adapter be solely used for each IP connected to, ie. eth0 will only be used when talking to 80.80.80.80 while eth1 will only be used for .81 . Unfortunately this doesn't work for me as I will be connecting to a single server.

Several of the solutions I have come up with are very much bodges and will not scale well.

I.e. have the router create internally used ip addresses such that when each chunk is sent they are sent round robin to these internal IP addresses where each IP is routed to a different iface. The router then converts the internal IP for each route to go to the same external IP.

This requires that the program producing the chunks to be hard coded to internal IP addresses and therefore if additional interfaces are added it will fail.

If anyone could help it would be great.

---

### Post by Lars Noodén on 2009-11-16
The lamest way would be to use DNS load balancing.  
But it may be enough in some situations:
[http://1wt.eu/articles/2006_lb/](http://1wt.eu/articles/2006_lb/)

You could even do it with iptables.  
[http://linuxgazette.net/108/odonovan.html](http://linuxgazette.net/108/odonovan.html)

There are specialized load balancers to look at.  Another name is reverse proxy.  They are often put on the gateway and shunt traffic to one machine or another.  

Apache2 mod_proxy
[http://httpd.apache.org/docs/2.2/mod/mod_proxy_balancer.html](http://httpd.apache.org/docs/2.2/mod/mod_proxy_balancer.html)

Pound
[http://www.apsis.ch/pound/](http://www.apsis.ch/pound/)

Squid
[http://www.squid-cache.org/](http://www.squid-cache.org/)

I'm sure I've missed a few.

---

### Post by BeardedChimp on 2009-12-03
Cheers for the reply,

I've been having a good go at getting it working through iptables but have been stuggling at what seems the last hurdle.

So it goes like this now:

Computer ----> router (running ubuntu) -----> internet

Where the router is connected to multiple connections.
I've tried numerous combinations, but I cannot seem to get it to work with a connection that is not the default route.

As I said before I am looking for each new connection to be round robin assigned a device, then subsequent packets travel along the same device until disconnection.
What I've been playing with is something like this:

iptables -t mangle -A PREROUTING -i eth0 -m conntrack --ctstate NEW -m statistic --mode nth --every 2 --packet 0 -j MARK --set-mark 1

Then using ip rule and multiple tables with different default routes.
I have also natted the packets travelling outwards so that they have the right IP using this:
iptables -A POSTROUTING -o ppp0 -t nat -j SNAT --to-source 10.46.238.92

However once the ack-packets are received the router does not seem to send them on to the computer on eth0. I can't use masquerding as each connection is on a different subnet.
I have tried using dnat to have the packets received go the the computer, but it never seems to detect the packets:
iptables -t mangle -t nat -i ppp0 -j DNAT --to-destination 192.168.1.203

Ta for any help.

---

### Post by zeny on 2009-12-03
what about heartbeat with ldirector? 

Thats how I load balance everything.

---

