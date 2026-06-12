---
title: "help with understanding iptables"
date: 2007-07-14
forum: Server Platforms
---

### Post by kjacks on 2007-07-14
I'm trying to understand how iptables works in order to setup port knocking.  What I don't understand is why when I retrieve my iptables nothing shows up, but my port 22 and 80 work fine.  Here is what I'm looking at:

me@Ubuntu:/etc$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

I can close and open the port with command :
sudo iptables -A INPUT -p tcp -i eth0 --dport 80 -j DROP
sudo iptables -D INPUT -p tcp -i eth0 --dport 80 -j DROP

How can a port be open without being in the iptables?  I've read about established sessions in iptables but can't find how to retrieve them or modify them.  Thanks for any help you can offer.

Kevin

---

### Post by Mr. C. on 2007-07-14
If I'm understanding your question correctly, a firewall (eg. iptables) and a server application are at different layers.

An application listens for connections on a port.  The port is not "open", it is simple waiting for incoming connections.  A port scan ma show this port as "open", but it really means "listening".

A firewall can be configured to allow or block these incoming requests.  It can also be configured to forwards requests on one port to another port.

Your iptables shows you have all chains defaulting to ACCEPT traffic.  Your Add/Delete rules are not opening and closing the port - they are merely allowing or denying packets destined to that port.

Make sense ?

MrC

---

### Post by kjacks on 2007-07-14
Excellent!  Thank you.   :)

What I was trying was backwards from how you explained it.  I was trying to allow a port to listen only when a certain criteria was met.  What I should have done was disallow that port until that criteria was met. 

I just retried everything and it works great.  Thanks again.

---

### Post by Mr. C. on 2007-07-14
Great.

There is a very good tutorial regarding iptables from the author.  Start here:

[http://www.netfilter.org/documentation/HOWTO//packet-filtering-HOWTO.html](http://www.netfilter.org/documentation/HOWTO//packet-filtering-HOWTO.html)

MrC

---

