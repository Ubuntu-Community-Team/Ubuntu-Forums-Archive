---
title: "Block An IP Range In Iptables"
date: 2009-05-10
forum: Server Platforms
---

### Post by zemon_ on 2009-05-10
How do I block an ip range in ip tables?

I block one address by this

```
iptables -A INPUT -s 192.168.100.0 -j DROP
```

Thought I could block a range by this

```
iptables -A INPUT -s 192.168.100.0/24 -j DROP
```

But I get an error

Try `iptables -h' or 'iptables --help' for more information.

Thanks in advance

---

### Post by konsole on 2009-05-12
> **zemon_ said:**
> How do I block an ip range in ip tables?

I block one address by this

```
iptables -A INPUT -s 192.168.100.0 -j DROP
```

Thought I could block a range by this

```
iptables -A INPUT -s 192.168.100.0/24 -j DROP
```

But I get an error

Try `iptables -h' or 'iptables --help' for more information.

Thanks in advance

Something like... ```
sudo iptables -A INPUT -m iprange --src-range 192.168.100.0-192.168.100.255 -j DROP
```

---

