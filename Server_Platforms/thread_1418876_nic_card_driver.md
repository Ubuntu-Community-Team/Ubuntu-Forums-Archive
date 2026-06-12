---
title: "nic card driver"
date: 2010-03-01
forum: Server Platforms
---

### Post by ub007 on 2010-03-01
Hi 

How do i find out which is the driver for my nic card?

dmesg |grep eth

eth0: Tigon3 [partno(N/A) rev 2100 (5704)]

is there any way to find out the current driver version and more details ??

David

---

### Post by Bachstelze on 2010-03-01
```
lspci -k
```

Will give you the name of the kernel module acting as a driver for your NIC. Then your favourite search engine should give you plenty of information about it.

---

