---
title: "Windows XP -&gt; Ubuntu linux networking"
date: 2006-06-11
forum: Server Platforms
---

### Post by Micik on 2006-06-11
hello,
can anyone explain me step by step how to enable network between ubuntu linux 5.04 and windows XP through static IP addresses?
thanks

---

### Post by adwait on 2006-06-11
1)Setup windows for a static address.
2)Setup the router for static addresses
3)
In ubuntu go to Systems>Admin Settings> Networking (oir something like that...I am using KDE...)
There click the configure button for eth0 and set it up for static IPs. Then Enable it..

4)Run
```
/etc/init.d/networking restart
```

Now try pinging the router and the other PC.

---

