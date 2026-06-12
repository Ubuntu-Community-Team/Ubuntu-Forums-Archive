---
title: "default /apache2/site-available/default  needed"
date: 2008-09-18
forum: Server Platforms
---

### Post by enforca on 2008-09-18
hey i have been hosting servers on ubuntu for quite some time now and i have come across a problem. 
i gave a person access to my server (stupid me) and they played around with the default apache server settings.
i was wondering if anyone had a copy of the default
/apache2/site-available/default
file for apache2 on ubuntu please.

---

### Post by cdenley on 2008-09-18
```

sudo apt-get -d --reinstall install apache2.2-common
dpkg -x /var/cache/apt/archives/apache2.2-common*.deb ~/apache2
less ~/apache2/etc/apache2/sites-available/default

```

---

