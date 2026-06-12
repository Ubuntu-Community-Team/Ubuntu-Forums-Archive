---
title: "apache2 ssl subdomain"
date: 2010-06-20
forum: Server Platforms
---

### Post by spezticle on 2010-06-20
Inside of a default apache2 ports.conf file is this entry:
```

<IfModule mod_ssl.c>
    # SSL name based virtual hosts are not yet supported, therefore no
    # NameVirtualHost statement here
    Listen 443
</IfModule>

```
if this is so, then how can i  have 
x.domain.com
y.domain.com
z.domain.com

with SSL?

---

### Post by Bachstelze on 2010-06-20
Which version of Ubuntu are you using? If you are using Lucid, then this is outdated. You can do that starting with Apache 2.2.12, and Lucid uses 2.2.14.

[http://httpd.apache.org/docs/2.2/ssl/ssl_faq.html#vhosts](http://httpd.apache.org/docs/2.2/ssl/ssl_faq.html#vhosts)

---

### Post by spezticle on 2010-06-20
> **Bachstelze said:**
> Which version of Ubuntu are you using? If you are using Lucid, then this is outdated. You can do that starting with Apache 2.2.12, and Lucid uses 2.2.14.

[http://httpd.apache.org/docs/2.2/ssl/ssl_faq.html#vhosts](http://httpd.apache.org/docs/2.2/ssl/ssl_faq.html#vhosts)

ah, i'm using karmic. i'll re-install and do lucid.

---

### Post by Bachstelze on 2010-06-20
> **spezticle said:**
> ah, i'm using karmic. i'll re-install and do lucid.

That's fine also, Karmic uses 2.2.12.

---

