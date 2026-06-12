---
title: "one nic two ips how to?"
date: 2006-07-26
forum: Server Platforms
---

### Post by joshchernoff on 2006-07-26
ok so I want to set up a dns nameserver. I got two ip's from my isp provider. how do I set up my nic to handle two ip's?

---

### Post by JuanWelthagen on 2006-07-27
```
/sbin/ifconfig eth0:1 192.168.1.5 netmask 255.255.255.0
```

---

### Post by joshchernoff on 2006-07-27
so then would i 
/sbin/ifconfig eth0:2 192.168.1.6 netmask 255.255.255.0

for the other IP?

---

