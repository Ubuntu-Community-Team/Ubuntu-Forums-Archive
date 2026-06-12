---
title: "IHS &amp; SSL problems"
date: 2010-09-27
forum: Server Platforms
---

### Post by stevanbt on 2010-09-27
Hi,
I've installed IBM's IHS on Ubuntu 10.04 and it works - kind of.  The bit that I can't get to work is SSL.

I have an existing .kbd file from an AIX server and the following is a cut down version of my VirtualHost entry in httpd.conf:-
```

LoadModule ibm_ssl_module modules/mod_ibm_ssl.so

<VirtualHost mysite:443>
  ServerName mysite

  SSLEnable
  SSLProtocolDisable SSLv2
  KeyFile /tmp/serverkey.kdb 

  SSLServerCert mysite
  SSLDisable
  RedirectMatch  ^/$ /index.html
</VirtualHost>

```

When I do an ./apachectl the following appears in the error_log:-
```
[Mon Sep 27 08:58:58 2010] [notice] (20019)DSO load failed: SSL0166E: Failure attempting to load GSK library (libgsk7ssl.so) Configuration Failed

```

I have created sym links in /usr/lib to all gsk files in <installroot>/gsk7/lib/.  But it doesn't make any difference.

Has anyone got IHS & SSL to work on Ubuntu, if so where am I going wrong?

Thanks, Steve.

---

### Post by stevanbt on 2010-09-27
Sorted it.

First off I needed to install libstdc++5.  Then after that I had to remove the trailing SSLDisable in the httpd.conf.

Happy days.

Thanks, Steve.

---

