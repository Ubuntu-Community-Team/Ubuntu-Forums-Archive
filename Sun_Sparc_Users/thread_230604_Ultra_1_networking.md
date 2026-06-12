---
title: "Ultra 1 networking??"
date: 2006-08-06
forum: Sun Sparc Users
---

### Post by mvdw on 2006-08-06
Hi all:

I have an ultra 1 which I had setup with a DHCP server in place, and the networking all worked no problem. Now I want to move it to an area with no DHCP server, so I need to supply it with a static address; I've tried editing /etc/network/interfaces, to look something like this (it's powered down at the moment, so can't confirm exact wording):
```

# primary network
auto eth0
iface eth0 inet static
    address 192.168.3.30
    netmask 255.255.255.0

```
Unfortunately, I can't seem to ping anything else on the network. It must be something basic I've left off - any ideas?

---

### Post by mips on 2006-08-06
maybe add gateway, broadcaast and network. also check the status of the interface.

---

### Post by mvdw on 2006-08-11
Problem solved - it was as simple as an incorrect network cable (stupid me put in a crossover).

Cheers,
mvdw

---

### Post by recupero on 2006-08-11
On the ultra1 Ubuntu works in graphics mode?

---

