---
title: "First attempt at Iptables - does this look secure to you?"
date: 2017-04-21
forum: Security
---

### Post by Bobby_James on 2017-04-21
I have just set up my first installation of iptables. I am on a 192.168.x.x network behind a home router. My rules are:

```
-P INPUT DROP
-P FORWARD DROP
-P OUTPUT ACCEPT
-A INPUT -i lo -j ACCEPT
-A OUTPUT -o lo -j ACCEPT
-A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT
-A OUTPUT -m state --state RELATED,ESTABLISHED -j ACCEPT
```

The aim is to prevent incoming packets that do not result from an outbound request but to permit all such outbound requests along with stateful connections.

I have no servers on the internal IP hence my basic series of rules.

Does this look decent? Would you suggest any modifications? Thanks.

---

### Post by Doug S on 2017-04-21
With the default policy od ACCEPT for the OUTPUT chain, you do not need the specific rule there.
Otherwise O.K.

---

