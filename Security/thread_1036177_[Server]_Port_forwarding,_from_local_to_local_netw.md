---
title: "[Server] Port forwarding, from local to local network?"
date: 2009-01-10
forum: Security
---

### Post by Jiddo on 2009-01-10
Hello!

I've got a pretty annoying problem:
I'm using my server PC as a router in my network, running DHCP, firewall etc, and it has two network interfaces. eth0 - local network, eth1 - internet. Now, I have a PC on the local interface, which is going to run a service, and needs access from the net, thus I need to do some port forwarding. I also have a dynamic DNS for my external IP, which I want to use to connect to this service. 

I currently have Firestarter installed and running as the firewall on the server (up until today I was running shorewall, but I changed when I couldn't fix this problem myself, tho unfortunately it didn't help). 

Let's call my DNS "my.dns.com" and the port 1234. 

The thing is, I've managed to forward the port just fine, and it works to access the service from anywhere outside my local network, however, when  I try to connect using my.dns.com:1234 from any machine inside the local network (even from the machine that's hosting the service), the connection just times out. 

Now, I know that some of you will want to suggest using localhost, 127.0.0.1 or the local IP instead, but that is unfortunately not possible, since this server needs to tell it's clients the ip for the second, persistent connection attempt. Thus I need something that will work both locally and externally. 

Please, I really need this to work! 

Yours, Jiddo.

---

### Post by HermanAB on 2009-01-10
The way I handle that problem is to run a LAN DNS which resolves the local addresses, so that scripts and setups can be done once and will resolve to the correct IP address - LAN or public WAN.

Hope that helps!

Herman

---

### Post by Jiddo on 2009-01-10
That was actually (one of) the solutions I found on some other forum as well, but wouldn't this solution map all references to the DNS to the local PC? I still have several services running on the router/firewall PC which I'd still like to access with the DNS (that already works). If possible, I'd need a LAN DNS which is only used for calls with a set destinaton port. Is that possible? 

Thanks a lot for your reply!

Yours, Jiddo.

---

### Post by HermanAB on 2009-01-10
Google for "split horizon DNS".

Some info on doing this with BIND 9:
"The most elegant way of implementing split DNS is to use the
"view" mechanism of BIND 9 to run both an "internal" and
"external" version of your namespace (usually the internal version is a superset of the external version, with disparate addresses if NAT is in effect), maintained in parallel, with the appropriate version of the namespace presented to clients depending on their source address. One of the additional benefits of running both namespaces on the same box (as
opposed to the old-fashioned way where they had to run on separate nameservers) is that you can share the common entries between views via an $INCLUDE file."

As described here:
[http://www.bind9.net/manual/bind/9.3.2/Bv9ARM.ch04.html#id2549203](http://www.bind9.net/manual/bind/9.3.2/Bv9ARM.ch04.html#id2549203)

Cheers,

Herman

---

### Post by Jiddo on 2009-01-10
I've looked into the whole split DNS thing, and I've actually gotten a local dns server working, tho it turns out that it is not enough. It seems like this serice I'm trying to run actually resolves the hostname into an IP address before it sends it to the clients. As a result, I can now connect using the dynamic DNS, and even tho remote clients can get an initial connection, they cannot get the persistent one. Is there any way to limit so the DNS server is only used when the destination port is X or something like that? 

Also, why doesn't plain old port forwarding/DNAT work? This kind of thing always used to work when I used "normal" routers instead of a dedicated router PC. What's so different?

Yours, Jiddo.

---

