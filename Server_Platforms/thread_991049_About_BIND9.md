---
title: "About BIND9"
date: 2008-11-23
forum: Server Platforms
---

### Post by satimis on 2008-11-23
Hi folks,


I'm prepared installing BIND9 as DNS server on a guest of Xen box serving other servers on the same.  What port shall I reserve for BIND9?  If another server on the same box needs the same port is there a glue?  TIA


B.R.
satimis

---

### Post by RealPSL on 2008-11-24
The DNS/Bind processes listen on port 53 and this is a register port. It is unlikely that another service will try to listen on that port.

> $ grep 53 /etc/services
domain		53/tcp				# name-domain server
domain		53/udp


---

### Post by satimis on 2008-11-24
> **RealPSL said:**
> The DNS/Bind processes listen on port 53 and this is a register port. It is unlikely that another service will try to listen on that port.
Hi


I got it.  Thanks


Is there anyway to overcome the difficulty on ONE external IP.


Besides if I don't know the port number is there anyway round to find it on package name?


TIA


B.R.
satimis

---

### Post by RealPSL on 2008-11-26
I am not aware of anyway around the single IP problem with DNS nor anyway of telling the port numbers from the package name.

---

