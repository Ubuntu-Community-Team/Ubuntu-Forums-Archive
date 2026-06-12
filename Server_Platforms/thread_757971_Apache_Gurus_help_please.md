---
title: "Apache Gurus help please"
date: 2008-04-17
forum: Server Platforms
---

### Post by belfasttim on 2008-04-17
Hi-- 

I installed knowledgetree's open source stack package on my dev server. However, since knowledgetree is a "closed" environment package, with its own mySQL, apache, etc, I need to find a way to expose it to my "real" server environment.

Right now, knowledgetree is listening at port 8080 on the server, so you can hit it fine at IP (192.168.1.110:8080) if you're on the local network. The same server's "real" apache listens on port 80 and resolves to "whatever.com" to the outside world, so no problems. 

How do I forward requests for "knowledgetree.whatever.com" to the knowledgetree apache server port 8080?

Is this a proxy request or a virtual server I need ot be looking at? Or should I just use the router's port forwarding?

Detailed help much appreciated! (pretend you're talking to a 5 year old!) :)

---

### Post by AlphaWu on 2008-04-18
Yes.Load proxy_module.

LoadModule proxy_module modules/mod_proxy.so
LoadModule proxy_http_module modules/mod_proxy_http.so

then edit the conf file

ProxyPass knowledgetree.whatever.com [http://192.168.1.110:8080](http://192.168.1.110:8080)
ProxyPassReverse knowledgetree.whatever.com [http://192.168.1.110:8080](http://192.168.1.110:8080)

PS.
I didn't test it! Just try!

---

