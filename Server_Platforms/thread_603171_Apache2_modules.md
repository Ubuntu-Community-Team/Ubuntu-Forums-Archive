---
title: "Apache2 modules"
date: 2007-11-04
forum: Server Platforms
---

### Post by mont@ssar on 2007-11-04
I need to install mod_proxy and mod security for apache2 on my feisty fawn  ..
I have apache2 already running with mysql/php5 ..
```

root@wappdefender:/vnux# apt-cache search mod_proxy
libapache-mod-rpaf - module for Apache which takes the last IP from the 'X-Forwarded-For' header
libapache2-mod-proxy-html - Apache2 filter module for HTML links rewriting
libapache2-mod-rpaf - module for Apache2 which takes the last IP from the 'X-Forwarded-For' header
```


```

root@wappdefender:/vnux# apt-cache search mod_security
libapache2-mod-ifier - Filter and reject incoming client requests
```

I found the names mod-rpaf and mod-ifier wierd, are they the right packages to install to get mod_proxy and mod_security on my box ?!

If no, would any one help me with the right names of these two packs and the repositories needed to get them ?!

Thanks

---

### Post by /etc/init.d/ on 2007-11-05
In Dapper and Edgy, mod_security is libapache2-mod-security.  In Feisty and later it seems to have disappeared or may have had its name changed (the fact you can't find it is not good).

As for mod_proxy, I have no idea.

---

### Post by MJN on 2007-11-05
I believe mod_proxy is shipped as part of the core build so check in /etc/apache2/mods-available. Enable it with **sudo a2enmod proxy**.

Mod_security, on the other hand, was removed from Fesity onwards due to licensing issues. You can either use the lesser-featured mod_ifier module or compile mod_security from source (the licensing issue is somewhat complex but involves the restriction of shipping pre-compiled binaries). Do some Google searching for further details.

Mathew

---

