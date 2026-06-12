---
title: "OpenVPN UDP/TCP Question"
date: 2010-03-24
forum: Server Platforms
---

### Post by spynappels on 2010-03-24
I have an OpenVPN server running and have clients connecting through the UDP port and getting 10.18.0.x IPs from the servers.

I have one client that can not connect, because of a firewall issue and I would like to try to get it to connect through TCP. 

I know this requires a second server process to be running, but how do I set that service up to give an IP in the same range and on the same subnet, but not one that conflicts with the UDP service IPs. I want to be able to communicate between the TCP and UDP connected clients.

What conf should I use to achieve this on the second (TCP) service?

---

### Post by HermanAB on 2010-03-24
If the port number is different, then you can use the same IP address.

---

### Post by jrssystemsnet on 2010-03-24
The short answer is: you don't.

The slightly longer answer is: you set the tcp group of clients up on a different subnet, but you set up routing between the two subnets, and make sure your OpenVPN server will accept the traffic (I generally just enable [packet forwarding](http://ubuntuwiki.net/index.php/Packet_Forwarding) on my OpenVPN servers - which doesn't allow any filtering whatsoever, but if you just want a box to forward traffic between subnets and interfaces, it does the trick nicely), and Bob's your uncle.

If this is unacceptable to you, then you're left considering just moving ALL your clients to tcp.

---

### Post by jrssystemsnet on 2010-03-24
> **HermanAB said:**
> If the port number is different, then you can use the same IP address.This won't work - the two OpenVPN instances need different IP addresses because they each use a different tun/tap adapter.  (Note that we're talking about private tun/tap IP addresses here, not the public address used to *reach* the VPN over the internet.)

AFAIK if you try to set up both tun/tap adapters in the same subnet (one at 10.18.0.0 and one at 10.18.0.1 for instance) there is nothing to keep them from each trying to issue the same IPs to their clients, so that you end up with IP conflicts.

---

### Post by spynappels on 2010-03-24
> **jrssystemsnet said:**
> This won't work - the two OpenVPN instances need different IP addresses because they each use a different tun/tap adapter.  (Note that we're talking about private tun/tap IP addresses here, not the public address used to *reach* the VPN over the internet.)

AFAIK if you try to set up both tun/tap adapters in the same subnet (one at 10.18.0.0 and one at 10.18.0.1 for instance) there is nothing to keep them from each trying to issue the same IPs to their clients, so that you end up with IP conflicts.

That is what I was afraid of, so I'll have to have a separate IP subnet for the TCP setup then and fettle the routing between them.

I may be back for help on this later then!

---

### Post by jrssystemsnet on 2010-03-24
> **jrssystemsnet said:**
> (I generally just enable [packet forwarding](http://ubuntuwiki.net/index.php/Packet_Forwarding) on my OpenVPN servers - which doesn't allow any filtering whatsoever, but if you just want a box to forward traffic between subnets and interfaces, it does the trick nicely)

Packet forwarding is a ridiculously simple and fast way to get your OpenVPN server to move packets back and forth between the subnets, for clients to communicate directly to one another.

The only real routing you would need to set up is if your OpenVPN server enables access into a network it's connected to, in which case you'd have to duplicate whatever static routes you set up to and from 10.18.0.1 with 10.19.0.1 (or wherever you put your TCP clients).

If the only thing you want to enable is communication between clients, and communication between clients and the OpenVPN box, then there's nothing at all to do other than add the OpenVPN instance and make sure packet forwarding is enabled.  (Unless, of course, you want to make sure clients *can't* access a network your OpenVPN box is on... in which case you have to set up actual routing and filtering and such, oh my.)

---

### Post by spynappels on 2010-03-24
Got it working, just pushed routes in the server.conf file for each server process!

---

### Post by spynappels on 2010-03-24
OK, when I said got it working, imeant I got the two subnets to route to each other, the client behind the firewall still will not connect to my OVPN server though....

Bummer, need to talk to their IT dept now to see if I can get a rule opened for this VPN.

---

