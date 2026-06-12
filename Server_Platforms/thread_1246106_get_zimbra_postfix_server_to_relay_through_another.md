---
title: "get zimbra postfix server to relay through another postfix host"
date: 2009-08-21
forum: Server Platforms
---

### Post by bluethundr on 2009-08-21
I am trying to get one postfix server (a zimbra server) to authenticate through sasl to another postfix server so it can be used as a relay host.

but I notice that the authentication method in /etc/postfix/sasl/smtpd.conf* on the other machine is auxprop because that machine uses mysql as a back end.

how do I get the first postfix server to authenticate against the second postfix server so that the second postfix server can be used to relay mail?

When I try to send mail using the postfix setup on the zimbra server I get:

```
<bluethundr@foo.com>: SASL authentication failed; server
    mail.beta.beezag.com[192.168.1.10] said: 535 5.7.8 Error: authentication
    failed: authentication failure
```

---

