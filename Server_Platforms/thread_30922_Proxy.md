---
title: "Proxy"
date: 2005-05-01
forum: Server Platforms
---

### Post by linutzo on 2005-05-01
Can anyone recommend a simple setup for a proxy server.
I'm going through the squid docs but I'm stuck in the setup sorry.

I can download the tool via apt-get and have read the docs and conf file.

I want to be able to connect through a proxy from work using my home ubuntu machine, and connect to the proxy with our M$ work machines through the inetwiz setup.

Thank You.

---

### Post by defkewl on 2005-05-01
What do you want to achieve with your proxy server?

---

### Post by linutzo on 2005-05-03
Well in all fairness I want to be able to uses the proxy on my server at home to view blocked sites. Believe it or not but this Ubuntu Forum site is blocked at work because the firewall at work will not allow forums.

Reason number two is someone showed me his proxy server and altough I can setup apache with PHP, setting up squid is just something I would like to know how to do and not break while attempting to do so, instead of mindlessly surfing the web.

---

### Post by lt_kije on 2005-05-10
While this won't get you a cacheing, web proxy like Squid, it will work for viewing blocked sites, etc. Instead of setting up a full-on web proxy, you could create a SOCKS-like proxy using ssh. SOCKS is an application proxy that can tunnel all sorts of connections, including web, from a client to a server. I use the following:

ssh -D 10000 user@remotehost

I then point Firefox to localhost:10000 in the proxy set up; the connection is tunneled over my encrypted ssh session to the remotehost, and from there to the internet. There's brief information about the -D flag in the ssh manpage, but O'Reilly also mentions it in their book about wireless security. It's a great alternative to a rather major application like Squid, especially if you don't need chacheing or filtering.

HTH,
lt_kije

---

