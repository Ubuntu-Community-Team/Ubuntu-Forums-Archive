---
title: "Squid caching localhost"
date: 2008-10-11
forum: Server Platforms
---

### Post by Aeros84 on 2008-10-11
Hi again,

I have my Ubuntu server box set up as a gateway/router, transparent squid cache proxy, and a *small* web development test server.

Everything seems to work fine, but one thing's bothering me a bit: Squid is caching all browsing I do on the Ubuntu box itself as well, in other words, it's caching everything hosted via apache on the same box.

From a development point of view, that's not ideal. Is there any way to stop it from doing that?

---

### Post by koenn on 2008-10-12
That depends on your browser : you've told it to use a proxy, so it does, and the proxy gets the pages from your web server, just as it is supposed to do.

configure your browser not to use a proxy for that specific server, or for addresses on your local network(s).

---

### Post by koenn on 2008-10-12
oops, overlooked that it's a transparent proxy ...
in that case you'd have to modify the redirect statement so that it doesn't redirect to your proxy for given server names or IP addresses / network ranges

---

### Post by Aeros84 on 2008-10-12
Thought so, but how would one do that?

My current redirect is as follows:

iptables -t nat -A PREROUTING -i eth1 -p tcp -m tcp --dport 80 -j DNAT --to-destination 10.0.0.1:3128
iptables -t nat -A PREROUTING -i eth0 -p tcp -m tcp –dport 80 -j REDIRECT --to-port 3128

---

### Post by koenn on 2008-10-12
man iptables and look for --source and --destination options (-s, -d).
I don't quite see how your network is layed out, but
assuming your web server runs at 10.0.0.1, you'd want to keep that destination out of the redirect/dnat, 
or, you want to redirect only if destination address not equal to 10.0.0.1
try something like 
```

iptables  .... -s ! 10.0.0.1 ... -J DNAT ...
#likewise for REDIRECT, probably)

```

---

### Post by Aeros84 on 2008-10-12
Ah, I see what you mean.

Isn't there an option in Squid to stop it from caching localhost though?

---

### Post by koenn on 2008-10-12
> **Aeros84 said:**
> Ah, I see what you mean.

although I should probably have use --destination, not --source in my example

> **Aeros84 said:**
> 
Isn't there an option in Squid to stop it from caching localhost though?
Ah, I see what you mean, you want that traffic to still go through the proxy, but just not being cached ?

squid.conf:
```
acl NOCACHEDOMAIN dstdomain www.redhat.com
no_cache deny NOCACHEDOMAIN 
```
[http://www.redhatmagazine.com/2008/02/27/tips-and-tricks-how-can-i-configure-squid-so-that-it-never-caches-some-web-sites/](http://www.redhatmagazine.com/2008/02/27/tips-and-tricks-how-can-i-configure-squid-so-that-it-never-caches-some-web-sites/)

---

### Post by Aeros84 on 2008-10-12
> **koenn said:**
> 
Ah, I see what you mean, you want that traffic to still go through the proxy, but just not being cached ?

squid.conf:
```
acl NOCACHEDOMAIN dstdomain www.redhat.com
no_cache deny NOCACHEDOMAIN 
```
[http://www.redhatmagazine.com/2008/02/27/tips-and-tricks-how-can-i-configure-squid-so-that-it-never-caches-some-web-sites/](http://www.redhatmagazine.com/2008/02/27/tips-and-tricks-how-can-i-configure-squid-so-that-it-never-caches-some-web-sites/)

Yes, it should be fine running through the proxy, as long as it doesn't get cached, right? Or am I missing something?

Thanks for that acl, by the way!

---

### Post by Aeros84 on 2008-10-12
Hm, by the way:

What's the difference between:

cache deny
and
no_cache deny

Those two directives still don't make sense to me.

---

### Post by koenn on 2008-10-13
> **Aeros84 said:**
> Yes, it should be fine running through the proxy, as long as it doesn't get cached, right? Or am I missing something?

I think so. And it keeps web access settings neatly together in squid.conf so int's cleaner and more maintainable.

---

### Post by koenn on 2008-10-13
> **Aeros84 said:**
> Hm, by the way:

What's the difference between:

cache deny
and
no_cache deny

Those two directives still don't make sense to me.

don't know - first time I saw this sort of thing was on that site I linked to. Guess you'll have to go find a squid manual or so



or ... (quick google ...)
[http://www.squid-cache.org/Versions/v2/2.7/cfgman/cache.html](http://www.squid-cache.org/Versions/v2/2.7/cfgman/cache.html)

---

### Post by Aeros84 on 2008-10-13
I have a suspicion that they both do the same thing, but where "cache" just stops it from caching, "no_cache" stops it from caching and deletes whatever matches that host in the cache at present as well. I think...

---

