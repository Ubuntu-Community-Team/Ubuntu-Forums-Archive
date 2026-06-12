---
title: "Cluster Networking Problems"
date: 2009-08-06
forum: Server Platforms
---

### Post by Raptor354 on 2009-08-06
I'm trying to set up an Apache cluster for my website.  When I set the Apache servers up, set the loopback alias, and reboot.  It stops at "Configuring network interfaces..." and doesn't move (for days) until I finally press Control-Alt-Delete, at which point it kills the networking processes and continues on the booting process without network interfaces (thus defeating the purpose of a web server).

As it turns out, when I remove the alias, it boots successfully, but the redundant part doesn't work at all.  The loopback area in /etc/network/interfaces looks like:
```
auto lo:0
iface lo:0 inet loopback
 address 192.168.11.20
 netmask 255.255.255.255
 pre-up sysctl -p > /dev/null
```

192.168.11.20 is the address to the server cluster.  I got the directions from [here]("http://www.howtoforge.com/set-up-a-loadbalanced-ha-apache-cluster-ubuntu8.04-p4").

Note: I'm using Ubuntu 9.04, but the interfaces file syntax couldn't have changed all that much, could they?  Or is it even a problem with the file?

Thanks for reading,

Raptor354

---

### Post by HermanAB on 2009-08-06
Howdy,
The easy way to do an Apache load sharing cluster is to make the servers the normal way, just like standalone servers (if you can make one, you can make many!), but with the same web site data on each.  Then you set up round-robin DNS to cause the connections to go to the bunch of them in rotation.

This type of setup is almost trivial to do and easy to debug, since all you do is create a bunch of servers each with its own IP address, then fool with the DNS to make the domain name resolve to a different IP address on each lookup.

---

### Post by Raptor354 on 2009-08-07
Normally that would be all fine and good, but I'm using session variables on my web pages (may not be the best way to do it, but it's for R&D).  Thus, I would absolutely hate for the users to spontaneously switch web servers in the middle of one of their sessions.

Raptor354

---

