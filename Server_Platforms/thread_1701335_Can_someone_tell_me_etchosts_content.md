---
title: "Can someone tell me /etc/hosts content?"
date: 2011-03-06
forum: Server Platforms
---

### Post by acastrolorenzo on 2011-03-06
I´ve modified it and now cant restore.

Thanks in advance!

---

### Post by Demented ZA on 2011-03-06
On a new and bland Ubuntu system, it should look something similar to this:
```
127.0.0.1       localhost
127.0.1.1       gateway.yourdomain.co.za gateway

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
```

---

