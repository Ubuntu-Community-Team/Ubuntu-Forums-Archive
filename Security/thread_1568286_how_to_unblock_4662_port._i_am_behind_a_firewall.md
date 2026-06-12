---
title: "how to unblock 4662 port. i am behind a firewall"
date: 2010-09-05
forum: Security
---

### Post by stevestark on 2010-09-05
i must be behind a firewall in this ubuntu 9.10 karmic. i need to access the Standard client TCP port. can i have step by step instructions please on how to put a port into the firewall so that it is not blocked?

edit: thank you d3v1150m471c

---

### Post by d3v1150m471c on 2010-09-05
```

iptables -A INPUT -p tcp --dport theportnumbergoeshere -j ACCEPT

```

---

### Post by bodhi.zazen on 2010-09-05
> **stevestark said:**
> i must be behind a firewall in this ubuntu 9.10 karmic. i need to access the Standard client TCP port. can i have step by step instructions please on how to put a port into the firewall so that it is not blocked?

edit: thank you d3v1150m471c

> **d3v1150m471c said:**
> ```

iptables -A INPUT -p tcp --dport theportnumbergoeshere -j ACCEPT

```

By default, the firewall is permissive, so you do not need to use that iptables rule.

You need to configure port forwarding on your router. The details of how to do that vary by router.

[http://portforward.com/](http://portforward.com/)

---

