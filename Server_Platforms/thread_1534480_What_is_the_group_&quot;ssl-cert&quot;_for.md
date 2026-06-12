---
title: "What is the group &quot;ssl-cert&quot; for?"
date: 2010-07-19
forum: Server Platforms
---

### Post by ygoe on 2010-07-19
I'm configuring services that will be using SSL encryption. Since I want to keep access to my SSL certificate as narrow as possible, I intend to put all granted service system users (for http, smtp, imap, ftp, ...) into a special user group and only grant that group access to the SSL certificate files.

In /etc/group I found the group named "ssl-cert" (112). The group doesn't seem to be well documented. It appears to belong to the package of the same name which can be used to generate self-signed SSL certificates. I'm not doing that, I have a signed SSL certificate. Could I safely use that group for my purpose or should I create another group for that?

---

### Post by richardjh on 2010-07-20
The only files on the system that have group ssl-cert are

/etc/ssl/private
/etc/ssl/private/ssl-cert-snakeoil.key

Which suggests this group is used solely for protecting private ssl keys.

I believe your idea to use this group for each service (httpd, dovecot, proftpd etc) is a good idea.
It will make managing permissions very easy.

I don't believe there is any necessity to create another group for this purpose as ssl-cert appears to be a perfect match.

---

