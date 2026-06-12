---
title: "HAProxy 1.6 Ubuntu 16.04 fails to start with 1.5 config file"
date: 2016-01-04
forum: Ubuntu Development Version
---

### Post by andrew102 on 2016-01-04
I'm testing Ubuntu 16.04

Seems that upgrading to 1.6.2 and also 1.6.3 of HAproxy, I cannot start the service with a custom config file that is working with v 1.5.x

Also it seems that the failure doesn't indicate any line number where the config may be failing. This is unusual given the previous experience with the HAproxy service startup script of 1.5.

It appears that the line for ```
frontend www bind 0.0.0.0:80
``` is the cause. I believe this would be a bug :/

---

### Post by andrew102 on 2016-01-04
Found the cause, sticky sessions are no longer supported:
[ALERT] 004/103442 (15031) : parsing [/etc/haproxy/haproxy.cfg:80] : 'appsession' is not supported anymore, please check the documentation.

---

