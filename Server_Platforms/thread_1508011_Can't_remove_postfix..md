---
title: "Can't remove postfix."
date: 2010-06-12
forum: Server Platforms
---

### Post by Synnapse on 2010-06-12
Hello, 
I'm trying to remove postfix so I can install citadel but it isn't working:
```

Removing postfix ...
 * Stopping Postfix Mail Transport Agent postfix                                postfix: fatal: config variable inet_interfaces: host not found: allsmtpd_sasl_auth_enable
                                                                         [fail]
invoke-rc.d: initscript postfix, action "stop" failed.
dpkg: error processing postfix (--purge):
 subprocess pre-removal script returned error exit status 1
Errors were encountered while processing:
 postfix
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

How can I solve this?

Thanks for your time :)

---

