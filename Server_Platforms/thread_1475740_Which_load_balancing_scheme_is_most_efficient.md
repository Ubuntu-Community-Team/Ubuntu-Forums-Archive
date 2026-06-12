---
title: "Which load balancing scheme is most efficient?"
date: 2010-05-07
forum: Server Platforms
---

### Post by pi.boy.travis on 2010-05-07
I've been planning to add some additional Apache servers to my network and setup load balancing between them, and I've been wondering about the best way to go about it.  I figured I could either:

-Use Apache's load balancing proxy module

-Use Squid in accelerator mode (I already have one setup in proxy mode)

-Use Apache's load balancing with a Squid in front of it

I have no experience with load balancing, I've only played around with it with VMs.  What would the forum wisdom recommend? 

Thanks!

---

### Post by HermanAB on 2010-05-07
Round Robin DNS is most efficient.  It can simply be done with BIND.

---

### Post by dragos2 on 2010-05-07
> **HermanAB said:**
> Round Robin DNS is most efficient.  It can simply be done with BIND.

Nice share :) But does it scale ?

---

### Post by HermanAB on 2010-05-07
Of course it scales.  Do some repeated nslookups of the Amazon or CNN web sites and see what happens.

---

### Post by pi.boy.travis on 2010-05-09
Thanks, BIND is doing it very nicely!

---

### Post by EarthMind on 2010-05-10
Actually Round Robin isn't very reliable because it doesn't perform any checks, it just "balances" the requests chronologically. Personally, I have no experience with apache's [load balancer module]("http://httpd.apache.org/docs/2.2/mod/mod_proxy_balancer.html") but at least you it's more advanced than Round Robin.

---

