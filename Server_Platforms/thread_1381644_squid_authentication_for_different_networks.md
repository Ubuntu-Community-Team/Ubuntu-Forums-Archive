---
title: "squid authentication for different networks"
date: 2010-01-15
forum: Server Platforms
---

### Post by tr3s on 2010-01-15
hi! i have a working squid ncsa authentication.

i have this in my squid.conf
```
acl password proxy_auth REQUIRED

acl employees src 192.168.0.2
acl admin src 192.168.1.2

http_access allow password
http_access allow employees
http_access allow admin
```

this setup makes squid authenticate both the employees and admin network.
how can i make squid just authenticate only the employees network? admin network should connect to squid without authentication.

many thanks

---

