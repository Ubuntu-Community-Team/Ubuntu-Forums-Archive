---
title: "Virtual host /Coldfusion Problem"
date: 2009-01-31
forum: Server Platforms
---

### Post by tgs1952 on 2009-01-31
Shortly after receiving my new system 76 machine w/ubuntu I set up a virtual host in my home directory.

Later I installed Coldfusion8. Install went ok - cfm files in my virtual directory open and are parsed correctly.

However, during the install I gave /var/www/html as the root directory for CF Administrator and it was installed there. That is how I set it up at work on Fedora 7 and it works fine. I find however that I can't access it at [http://localhost/CFIDE/Administrator](http://localhost/CFIDE/Administrator) on Ubuntu. In fact I can't access anything in that directory except localhost/phpmyadmin.

I am assuming it is something with my 'hosts' file which reads:

127.0.0.1 localhost.localdomain localhost dev.example.com [www.dev.example.com](www.dev.example.com)

Or do I need to set up a virtual host for /var/www/html?

Thanks in advance

---

### Post by RealPSL on 2009-02-01
The default document root is /srv/www. As a result you have to either define a new virtual host or a little easier define a directory alias:

```
Alias /CFIDE /var/www/html/CFIDE

<Directory /var/www/html/CFIDE>
  Order allow,deny
  Allow from all
</Directory>
```

This should make [http://localhost/CFIDE](http://localhost/CFIDE) or which ever virtual host you add it to work.

---

### Post by tgs1952 on 2009-03-04
Really sorry for responding so late - but that did work.

---

