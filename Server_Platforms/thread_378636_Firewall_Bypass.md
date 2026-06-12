---
title: "Firewall Bypass"
date: 2007-03-07
forum: Server Platforms
---

### Post by wuhaa on 2007-03-07
Hi,

I have a ubuntu 6.10 server running at home with webmin. The admin at work has blocked off mosy of the parts. 

My issue is that I can't access my webmin interface which runs on port 10000.

Is there a way to access this port from port 80. Maybe with a proxy or something??!!


Thanks,

---

### Post by dbott67 on 2007-03-07
Is your home server behind a router/firewall (such as D-Link, Linksys, etc.)?  If so, are you using port-forwarding?

Instead of using port 10,000 as the public port to be forwarded to your internal private IP address, you could always use port 80 and forward it to port 10,000.

See attached diagram for more clarification.

-Dave

---

### Post by dbott67 on 2007-03-07
Another alternative in case you're unable to change the port:

[http://www.http-tunnel.com/html/solutions/http_tunnel/client.asp](http://www.http-tunnel.com/html/solutions/http_tunnel/client.asp)

It's not free, but it's relatively inexpensie ($4.99 per month; slightly less if you subscribe for multiple months).

---

### Post by wuhaa on 2007-03-07
Thanks for the reply.

I am forwarding the same port which is 10000 from my server through my D-link router.

In fact everything works the way its suppose to from any other remote computer except my work! 

I can't forward the webmin to port 80 cus I have Apache running on it.

I was wondering if it is possible to do something like this:

[http://www.the-cloak.com/Cloaked/]("http://www.the-cloak.com/Cloaked/")

Thanks,

---

