---
title: "Host Based NAT?"
date: 2010-02-12
forum: Server Platforms
---

### Post by linorics on 2010-02-12
Hi there I'm running A Linux based firewall/router with DHCP NAT and DNS.

I can only have one public ip address. I have two servers running identical programs, each using port 9352(And I can change that).

Server a.domain.com | Server b.domain.com

My client program  want to connect to a.domain.com and b.domain.com using port 9352(Also can't be changed... very stupid program...).

So is there a way to tell a router that if the request is for a.domain.com forward to host a on the nat 192.168.0.50, and b.domain.com to host b 192.168.0.60?

I have no idea if this is possible, but i would think there is something that I could do.

---

### Post by gmargo on 2010-02-13
You don't mention what protocol is used.  If it is HTTP and the Host: header is included to differentiate the requests, then you can use some sort of reverse proxy. [http://en.wikipedia.org/wiki/Reverse_proxy](http://en.wikipedia.org/wiki/Reverse_proxy).

---

### Post by linorics on 2010-03-30
That will work, however I just payed the developers to allow me to change the ports.

---

