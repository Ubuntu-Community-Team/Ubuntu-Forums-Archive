---
title: "Stopping DNS-flood with UFW"
date: 2013-03-04
forum: Security
---

### Post by mikukkon on 2013-03-04
I have a fixed IP-address and recently suffered from DNS-flood attack, which where some random bots send tens of DNS-queries per second to my DNS server. 

After a lot of googling, I did not find any good answer, so after some try and error, here is what I came up with UFW rules:
```

53   ALLOW     <ip of my ISP's nameserver #1>
53   ALLOW     <ip of my ISP's nameserver #2>
53   ALLOW     192.168.<xxx>.<xxx>/<xx> <my private subnet>
53   DENY       Anywhere

```
So I allow only my upstream DNS-servers and devices in my local subnet to use my DNS server and block all others. Simple, but took some time to figure out. I hope this helps somebody else, it surely would have helped me! :)

--MiKu

---

