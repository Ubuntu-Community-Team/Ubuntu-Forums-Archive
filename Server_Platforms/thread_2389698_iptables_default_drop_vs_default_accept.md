---
title: "iptables default drop vs default accept"
date: 2018-04-20
forum: Server Platforms
---

### Post by faizan90 on 2018-04-20
Which is better practice of the two?

```
-P INPUT DROP
-P FORWARD DROP
-P OUTPUT DROP


-A INPUT -i lo -j ACCEPT
-A OUTPUT -o lo -j ACCEPT

```

[B]OR

[/B]```

-P INPUT ACCEPT
-P FORWARD DROP
-P OUTPUT DROP


-A INPUT -i lo -j ACCEPT
-A OUTPUT -o lo -j ACCEPT
-A INPUT -j DROP

```

---

### Post by d-h-s on 2018-04-30
The first one.

That way, you cannot accidentally delete the fall-through.

---

