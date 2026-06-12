---
title: "iptables problem"
date: 2007-05-16
forum: Server Platforms
---

### Post by cookfromfrozen on 2007-05-16
Hi
What I want to do with iptables is to drop all incoming packets to the machine unless they are specifically allowed.

What I have done is this:

```

iptables -P INPUT DROP    # drop anything that isn't explicitly allowed
iptables -A INPUT -p tcp -s 192.168.0.2 -d 0/0 --destination-port 22 -j ACCEPT    #allow ssh from a specific machine
iptables -A INPUT -p icmp -s 192.168.0.2 -d 0/0 -j ACCEPT    # allow pings from a specific machine

```

Everything is dropped except SSH and pings from 192.168.0.2, which is what I want, but then I can't access the internet on that machine because anything coming back is dropped.

How do I set it to allow "responses" to traffic coming from my machine (like when I initiate a connection from a website)?

Surely there must be a way to do this rather than explicitly opening every port you want.

---

### Post by joft on 2007-05-16
Sure, there is a way, allowing what belongs to an outgoing connection. You have to use the "state" match of iptables:
```

iptables -A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT

```

---

### Post by cookfromfrozen on 2007-05-16
Hey, thanks a lot, that did the trick!

---

