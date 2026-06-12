---
title: "Transport Layer Security problem"
date: 2014-02-28
forum: Server Platforms
---

### Post by Frank P on 2014-02-28
Ubuntu 12.04LTS Apache 2.4 I've installed TLS be following the steps on this link [https://help.ubuntu.com/community/GnuTLS](https://help.ubuntu.com/community/GnuTLS)
When restarting Apache I get the following error
                            apache2: Syntax error on line 212 of /etc/apache2/apache2.conf:              Syntax error on line 1 of /etc/apache2/mods-enabled/gnutls.load:                          Cannot load /usr/lib/apache2/modules/mod_gnutls.so into server: /usr/lib/apache2/modules/mod_gnutls.so:                        undefined symbol: unixd_config

If I remove the @gnutls.conf file from the /etc/apache2/mods-enabled directory Apache restarts
Any suggestions would be appreciated
Thanks
Frank

It's been suggested that the GnuTLS package in 12.04LTS hasn't been updated for apache 2.4 If that's the case is there a repository with an updated version or should I revert to apache2.2

---

### Post by howefield on 2014-03-02
Thread moved, you'll likely get better support here in the "Server Platforms" forum.

---

### Post by neel3 on 2014-03-05
Might be related to this...
[http://arstechnica.com/security/2014/03/critical-crypto-bug-leaves-linux-hundreds-of-apps-open-to-eavesdropping/](http://arstechnica.com/security/2014/03/critical-crypto-bug-leaves-linux-hundreds-of-apps-open-to-eavesdropping/)

---

