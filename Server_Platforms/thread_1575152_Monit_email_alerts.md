---
title: "Monit email alerts"
date: 2010-09-15
forum: Server Platforms
---

### Post by c8a7w on 2010-09-15
in the office we have a local file/web server and ive setup monit to monitor these deamons.

monit seems to be working fine. there is still some tweaking to be done but i can not get email messages working.

ive checked with my host who do allow smtp connections and ive tested that from my laptop but when monit tries to send the mail i get 

```
error    : Sendmail error: 504 5.7.4 Unrecognized authentication type.
```

the server does not use ssl or tls and the monit config is 

```
 SET MAILSERVER smtp.emailprovider.com PORT 25 USERNAME "email@address" PASSWORD "$Password$"

```

any suggestions guys?

---

