---
title: "How to allow MSN/AOL/Jabber/etc thru transparent proxy ?"
date: 2009-01-07
forum: Server Platforms
---

### Post by kurtkraut on 2009-01-07
Hi,

I have a working Squid transparent proxy but only web browsing is working properly. What should I do to allow the usage of MSN/AOL/Jabber/other instant messaging apps thru my transparent proxy ?

Here is my squid.conf:

```

http_port 3127 transparent
cache_mem 8 MB
cache_dir ufs /var/spool/squid 100 16 256
cache_log /var/log/squid/cache.log
cache_store_log /var/log/squid/store.log
pid_filename /var/run/squid.pid
visible_hostname adngateway
cache_effective_user proxy
cache_effective_group proxy
acl REDE_INTERNA src 192.168.1.0/255.255.255.0
acl WIRELESS src 192.168.2.0/255.255.255.0
acl all src 0.0.0.0/0.0.0.0
http_access allow REDE_INTERNA
http_access allow WIRELESS
http_access deny all
```

Here is my iptables rule:

```

iptables -t nat -A PREROUTING -i eth1 -p tcp -j REDIRECT --to-port 3127

```

---

