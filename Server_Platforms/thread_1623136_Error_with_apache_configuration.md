---
title: "Error with apache configuration"
date: 2010-11-16
forum: Server Platforms
---

### Post by Anika_ on 2010-11-16
Helo everyone. I'm a newbie at Linux, and i'm trying to install the Apache server with PHP support. when I type "/usr/local/apache2/bin/apachectl start" at terminal i got an error message [COLOR="DarkRed"]httpd: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName[/COLOR] .
Somebody know how could I fix it?

The versions are:
Apache 2.2.17
PHP 5.2.14

---

### Post by ronnie_perry on 2010-11-16
> **Anika_ said:**
> Helo everyone. I'm a newbie at Linux, and i'm trying to install the Apache server with PHP support. when I type "/usr/local/apache2/bin/apachectl start" at terminal i got an error message [COLOR=DarkRed]httpd: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName[/COLOR] .
Somebody know how could I fix it?

The versions are:
Apache 2.2.17
PHP 5.2.14

I believe you do not have a fqdn in your hosts file. This is normal.

---

