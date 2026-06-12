---
title: "Transparent proxy: iptables+privoxy+polipo"
date: 2009-12-05
forum: Security
---

### Post by pcarter on 2009-12-05
I am using this to route all http traffic to privoxy:
```

iptables -t nat -A OUTPUT -p tcp --dport 80 -j REDIRECT --to-ports 8118
iptables -t nat -A OUTPUT -p tcp --dport 80 -m owner --uid-owner privoxy -j ACCEPT

```
which works with privoxy by itself. But once I use polipo as a parent proxy, this setup no longer works. Even after using:
```

iptables -t nat -A OUTPUT -p tcp --dport 80 -m owner --uid-owner polipo -j ACCEPT

```
polipo times out pages, showing "Read from server failed: Timeout" in /var/log/polipo.

I've verified that it's the iptables + polipo combination that is causing problems: polipo + privoxy without iptables intercepting, and manually specifying a proxy in Firefox works as expected... and iptables + privoxy works perfectly aswell. iptables + polipo does not.

It comes down to my lack of iptables knowledge. Help? :)

**Edit:** As confirmed by htop, polipo is successfully running as its own user; polipo.

---

### Post by Rubicon_82 on 2009-12-05
> **pcarter said:**
> I am using this to route all http traffic to privoxy:
```

iptables -t nat -A OUTPUT -p tcp --dport 80 -j REDIRECT --to-ports 8118
iptables -t nat -A OUTPUT -p tcp --dport 80 -m owner --uid-owner privoxy -j ACCEPT

```


I'm surprised those rules worked for privoxy.  Iptables works on a 'first match wins' approach.  This means that your rules, as written, will direct **all** port 80 traffic to port 8118, regardless of whether the traffic is owned by privoxy.  The following approach should work better:

```

iptables -t nat -A OUTPUT -p tcp --dport 80 -m owner --uid-owner polipo -j ACCEPT
iptables -t nat -A OUTPUT -p tcp --dport 80 -j REDIRECT --to-ports 8118

```

Done this way, port 80 traffic owned by polipo is allowed to leave the system, whereas other port 80 traffic is directed to port 8118.

Note that I'm assuming you've disabled privoxy before trying to get polipo to listen on port 8118.  There may be issues if you try to have two different proxies listening to the same port.

---

### Post by pcarter on 2009-12-05
> **Rubicon_82 said:**
> I'm surprised those rules worked for privoxy.  Iptables works on a 'first match wins' approach.  This means that your rules, as written, will direct **all** port 80 traffic to port 8118, regardless of whether the traffic is owned by privoxy.
This was the problem! I didn't realize the order of the rules mattered.

> **Rubicon_82 said:**
> 
Note that I'm assuming you've disabled privoxy before trying to get polipo to listen on port 8118.  There may be issues if you try to have two different proxies listening to the same port.
Well, polipo listens in 8123 and privoxy is using that (127.0.0.1:8123) as its parent proxy. It works now that I've switched the order of the rules.

Thanks! :)

---

