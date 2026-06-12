---
title: "Fresh Install Squid Proxy Version 3, with digest authentication, on Ubuntu 1604"
date: 2017-11-08
forum: Server Platforms
---

### Post by pcnetguru on 2017-11-08
In squid.conf, I Modified line 431 so that it shows "auth_param digest program /usr/lib/squid3/digest_pw_auth -c /etc/squid3/digest_passwd".


But the service is erroring saying "auth_param digest program /usr/lib/squid3/digest_pw_auth: No such file or directory.


I went to the directory and see the file is not there. I would have assumed that this file would be there automatically. Is there something broken here or is this normal behavior? How do I get the proper file there?

---

