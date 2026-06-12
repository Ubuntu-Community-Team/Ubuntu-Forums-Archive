---
title: "ProxySet: unknown Balancer parameter failonstatus"
date: 2011-01-03
forum: Server Platforms
---

### Post by seraphimalia on 2011-01-03
Hi,

Happy new year fellow members :)

Ubuntu Version:
```
cat /etc/issue
Ubuntu 10.04.1 LTS \n \l
```

Apache Version:
```
Server Version: Apache/2.2.14 (Ubuntu) mod_ssl/2.2.14 OpenSSL/0.9.8k JRun/4.0
Server Built: Nov 18 2010 21:20:56
```

According to [https://issues.apache.org/bugzilla/show_bug.cgi?id=48939](https://issues.apache.org/bugzilla/show_bug.cgi?id=48939) this fix was added in 2.2.15 and later adjusted in 2.2.17.  I need this functionality, but an "apt-get update" and then "apt-get upgrade apache2" only upgrades my apache to 2.2.14.

How do I get the functionality without downloading the latest release of apache from the apache site and replacing it on my server.  I would really like to continue use apt-get so perhaps there a way to tell apt-get I want the latest version or somehow patch the current installation by just overwriting some files so that I can continue to use apt-get at a later stage?

Please advise? :)

Regards,
Seraph

---

