---
title: "Syslog with remote logging - cannot seem to split the log?"
date: 2007-06-02
forum: Server Platforms
---

### Post by jimwillsher on 2007-06-02
Hi all,

I've enabled remote logging on my NetGear router, and I've configured it to send to my syslog server (Feisty 7.04) using "local7".

Within /etc/syslog.conf I have

```
# JRW For Netgear
local7.*                        /var/log/router.log

```

and I am seeing entries logged successfully in syslog:

```
Jun  2 10:50:05 192.168.1.1 DGFV338 Logout succeeded for user admin
Jun  2 10:50:09 192.168.1.1 DGFV338 Login succeeded: user admin from 192.168.1.101
```

However, my /var/log/router.log file is always empty.

What am I missing? Am I correct in speciifying local7.* in the conf file?

Many thanks,


Jim

PS Running logger:

```
logger -p local7.info "Hello"
``` successfully writes to  the router.log file. So does this help?

---

