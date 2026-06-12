---
title: "http Load balancer"
date: 2012-01-09
forum: Server Platforms
---

### Post by fernandoch on 2012-01-09
How would you setup an http load balancer? With what software? Any tutorials?

---

### Post by Lars Noodén on 2012-01-09
There are a lot of ways to set it up.  You could use Apache, Squid, or Varnish.

[http://httpd.apache.org/docs/2.2/mod/mod_proxy_balancer.html](http://httpd.apache.org/docs/2.2/mod/mod_proxy_balancer.html)
[http://wiki.squid-cache.org/SquidFaq/ReverseProxy](http://wiki.squid-cache.org/SquidFaq/ReverseProxy)
[https://www.varnish-cache.org/trac/wiki/LoadBalancing](https://www.varnish-cache.org/trac/wiki/LoadBalancing)

---

### Post by fernandoch on 2012-01-09
Thank you for the quick reply.

Which one is the most effective? 

What about nginx?

---

### Post by Lars Noodén on 2012-01-09
I'm not sure which one is most effective.  If I had to take an uneducated guess I would try Varnish first, it's the more recent of the three.  If you have time you could set up some simple tests.  

I had nginx in the list initially but it is going "open core" which really rubs me the wrong way.  Scroll down to "proprietary" in this article:
[http://www.freesoftwaremagazine.com/comment/78827](http://www.freesoftwaremagazine.com/comment/78827)
It's not a good thing to build up a community through being open and then pulling out once big enough.

---

### Post by fernandoch on 2012-01-09
Very good article, I was not aware of that site.

Take a look at the wikipedia's architecture

[http://meta.wikimedia.org/wiki/Wikimedia_servers#System_architecture](http://meta.wikimedia.org/wiki/Wikimedia_servers#System_architecture)

If you scroll down a bit, on the right you can see all the servers. They only run ubuntu servers...

They use LVS for load balancing.

---

### Post by SeijiSensei on 2012-01-09
A light-weight option is to use round-robin DNS.  In the zone file for your domain, you'd have an entry like:

```

www     IN     A    10.1.1.1
        IN     A    192.168.1.1
        IN     A    172.25.101.7

```

The nameserver will hand out one of these IPs at random when asked to resolve the "www" hostname in your domain.

This is an easy solution, but only if the servers distribute static content.  If you need to use session cookies or have a dynamic site backed by an SQL database, you need one of the more sophisticated approaches to load-balancing discussed above.

---

