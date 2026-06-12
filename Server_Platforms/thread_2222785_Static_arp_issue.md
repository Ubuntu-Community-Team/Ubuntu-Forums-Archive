---
title: "Static arp issue"
date: 2014-05-08
forum: Server Platforms
---

### Post by z-p30p13 on 2014-05-08
Hi 2 all!

I try to configure static arp on same interface, but when i do this - server blocked any connection even from my pc's, wich in servers arp table...

i have a script, which run at startup:

```

......
ifconfig em1 -arp;
ifconfig -f $pathToFile;
#file containts pair: ip mac
......

```
command
```
arp -n
```
show all entries in my ip-mac pair file. So, all entries are added.
But it blocks any connection.

When i type in console
```
ifconfig em1 arp
```
all works fine.

What i do wrong?

---

