---
title: "dansguardian can not access website http"
date: 2015-01-29
forum: Server Platforms
---

### Post by hohoangluan on 2015-01-29
Hi all.
    I've just install dansguardian 2.10.1.1 with new configuration. But when i restart, the client have just only access https website and http website can not access (error same internet connect lost). i'm appreciate your help.This is my configuration below.

Dansguardian.conf
```

filterip = 
filterport = 8080
proxyip = 127.0.0.1
proxyport = 3128

```

iptables
```

iptables -t nat -A PREROUTING -i eth1 -p tcp --dport 80 -j DNAT --to-destination 172.22.0.2:8080
iptables -t nat -A POSTROUTING -o eth2 -j MASQUERADE

```

---

