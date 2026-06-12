---
title: "Unbound DNS..."
date: 2011-12-24
forum: The Cafe
---

### Post by chong601 on 2011-12-24
Does anyone have experiences to speed up Unbound?
Any help is appreciated...

---

### Post by collisionystm on 2011-12-24
> **chong601 said:**
> Does anyone have experiences to speed up Unbound?
Any help is appreciated...

I have never used Unbound. Only Bind9.
Bind9 is great. I am not sure what your purposes for Unbound are but you can set Bind to be a caching server. 

You install it, set your forwarder to googles open DNS and your resolv.conf to 127.0.0.1

[http://code.google.com/speed/public-dns/](http://code.google.com/speed/public-dns/)

---

### Post by chong601 on 2011-12-24
> **collisionystm said:**
> I have never used Unbound. Only Bind9.
Bind9 is great. I am not sure what your purposes for Unbound are but you can set Bind to be a caching server. 

You install it, set your forwarder to googles open DNS and your resolv.conf to 127.0.0.1

[http://code.google.com/speed/public-dns/](http://code.google.com/speed/public-dns/)

I did use BIND 9 before as a caching server but using public DNS can cause privacy concerns :(. BIND 9 is getting a bit bloated after Nominum modified it to implement DNSSEC and some stuff and BIND is not really good to do recursion (which I really want it).

I use Unbound for recursive lookup (not caching) and to run away from ISP's poorly made DNS server.....

---

### Post by chong601 on 2011-12-25
I think not everyone use Unbound...... :(

---

### Post by Jive Turkey on 2012-01-21
I found your thread while researching unbound myself after messing with bind9 and not getting the results I want.  How is it working for you?  

I found this decent article on it and I think I will give it a go.
[https://calomel.org/unbound_dns.html](https://calomel.org/unbound_dns.html)

---

### Post by chong601 on 2012-01-28
> **Jive Turkey said:**
> I found your thread while researching unbound myself after messing with bind9 and not getting the results I want.  How is it working for you?  

I found this decent article on it and I think I will give it a go.
[https://calomel.org/unbound_dns.html](https://calomel.org/unbound_dns.html)

By the way, Calomel's article is useful but make Unbound much much much less secure due to repeating port number....

I had found the way but not really for company use....

---

