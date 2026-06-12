---
title: "name based virtual hosting with two ip's"
date: 2007-07-04
forum: Server Platforms
---

### Post by nephish on 2007-07-04
lo there all,
we are running a server at work that we are hosting several websites ( about 6 ) with name based virtual hosting in apache.

every once in a while our isp dies. Then we are out of buisness for a few hours until they fix whatever it was that crashed. Meanwhile, we need another isp to serve on. So, here are my questions. We are using zoneedit as a dns server.

So my questions are these:
how would i go about adding another ip address for each of the name based virtual hosts on our server?

can a domain name be resolved to two different ip addresses ? ( or, since we are going to be paying for the isp even when we don't need it, can we make use of the extra bandwidth to serve with ?)

can a seemless solution be had, or if we drop one isp, can we continue to serve up web pages without having to change things in the dns server or apache http.conf file?

any tips would be great, or links for good set up how-tos.
thansk

---

### Post by Mr. C. on 2007-07-05
Just add another A record for your host.  Modern DNS servers will round-robin the results, give you load balancing.

MrC

---

### Post by nephish on 2007-07-05
so if one isp crashes, does that mean that the other will be the only one available?
thanks

---

### Post by Mr. C. on 2007-07-05
No.  This does not resolve unreachable hosts; it merely load balances.

You need a *reliable* host available at a *reliable* IP to perform what you want.  You can provide redundancy, but if your ISPs hosts / network is unreliable, you have a problem.  Change ISPs if your business needs are critical.  As a workaround, you can use a dynamic DNS service that provides A records; you'll have to update them when your primary ISP goes down, or automate that somehow.  That won't solve the problem with hosts that already have the old IP cached; there will be a window of time before their cached data expires (i.e. based upon the TTL - time to live - configured for the A records or the domain).

MrC

---

### Post by nephish on 2007-07-05
ok, thanks for the info.
we live in a remote area in west texas, good ISPs are hard to come by. 
But i suppose this is better than having no alternative at all.

again, thanks

---

### Post by Mr. C. on 2007-07-05
Or you can host your web server at a reliable host anywhere in the world.  There are plenty of reliable hosts.

MrC

---

