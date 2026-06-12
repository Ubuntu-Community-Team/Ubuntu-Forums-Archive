---
title: "How to share bandwidth usage for each client on network"
date: 2015-10-08
forum: Server Platforms
---

### Post by efexorce on 2015-10-08
_**i**_ want to limit users for internet bandwidth usage
100 clients are using internet and some of them are downloading too much.
i mean 100MBps => 1MBps for each client (or share clients equal)
My network LAN (eth1) = 192.168.2.0/24

privoxy+dansguardian are working on same ubuntu server(14.04)
is there any solution for example iptables ...

---

### Post by gordintoronto on 2015-10-09
This is typically handled by whatever you are using as a router. For example, I'm think that pfSense can do what you want.

You'll probably face a user revolt if you cut them back to 1 MBps.

---

### Post by matt_symes on 2015-10-12
Hi

You can perform traffic shaping using the command...

```
tc
```

You'll want to read the man page and look on tutorials on the net as it' a big area.

Kind regards

---

### Post by antonza on 2015-10-14
> **gordintoronto said:**
> This is typically handled by whatever you are using as a router. For example, I'm think that pfSense can do what you want.

You'll probably face a user revolt if you cut them back to 1 MBps.

Agreed on using a router with QoS, pfSense, Mikrotik, etc. will do the trick.

---

