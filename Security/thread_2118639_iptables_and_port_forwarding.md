---
title: "iptables and port forwarding"
date: 2013-02-21
forum: Security
---

### Post by vodgut on 2013-02-21
So I'm trying to use iptables to port forward one port to another.  Great!

```
iptables -t nat -I PREROUTING -i <interface> -s <network> -p tcp --dport X -j REDIRECT --to-port Y
```

Y has its own more open rules.  X needs to be restricted to fewer networks.  If I use the -s, nothing works from anywhere.  If I don't use -s, everything is wide open on X.  It seems like X is inheriting the rules of Y, which is NOT what I want to have happen.  X needs to NOT follow the rules of Y - X needs to express itself as its own port, but shovel stuff off to Y from certain networks and dump everything else.

Halps?

---

### Post by zhaozhou on 2013-02-22
Can you redirect Y data _before_ you redirect X data?

---

### Post by The Cog on 2013-02-22
My first reaction is to wonder if you got the syntax for <network> correct. A good example might be 1.2.3.0/24.

---

### Post by vodgut on 2013-02-22
Y actually is the final destination, so there's no need to redirect that.  This is just port-to-port on the same machine.  I just want different behavior (filtering) from the redirected port.

Network syntax is fine - I'm actually filtering other ports successfully with the same network variable in my iptables script.  Just not redirecting them.

I've tried creating another rule that rejects packets to port X except from the network I want to be able to connect, but again, I think it takes the PREROUTING rule as precedence and adopts the rules of the destination port, before trying to reject the packet.

---

