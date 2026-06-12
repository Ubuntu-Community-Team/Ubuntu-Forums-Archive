---
title: "iptables and proxy servers"
date: 2008-01-28
forum: Server Platforms
---

### Post by MarkCrossley on 2008-01-28
I want to ensure that all network traffic passes through a specific proxy.

After browsing many websites I've come across the following:

```
iptables -t nat -A PREROUTING -p tcp --dport 80 -i eth0  -j DNAT --to 
1.2.3.4:3128
```

Would this iptables command force all network traffic to go through the proxy 1.2.3.4:3128?

Basically I don't want to have to set up the proxy settings in every application I use. Additionally I don't want anyone to be able to change the proxy settings.

---

### Post by The Cog on 2008-01-28
I think that would not wok. Although that ipta bles rule will redirect all HTTP connections to 1.2.3.4 port 3128, it is my understanding that the HTTP request to a proxy server has a different format to the normal direct HTTP request. A normal direct request can just say "GET /", but the request to a proxy must also say which real server the request must be forwarded to. like "GET ww.foo.com/"

---

### Post by koenn on 2008-01-28
> **MarkCrossley said:**
> I want to ensure that **all network traffic **passes through a specific proxy.

```
iptables -t nat -A PREROUTING -p tcp --dport 80 -i eth0  -j DNAT --to 
1.2.3.4:3128
```

Would this iptables command force **all network traffic** to go through the proxy 1.2.3.4:3128?


no, only network traffic with destination port = 80

---

### Post by MarkCrossley on 2008-01-28
Any suggestions what would work?

---

### Post by The Cog on 2008-01-28
I have heard of a thing called a **transparent proxy**. I don't know how it works though. Might be worth googling for.

---

### Post by koenn on 2008-01-28
are you sure you want *all* traffic proxied ? mail ? ssh ? ...
or are we talking about http (web) ?

---

