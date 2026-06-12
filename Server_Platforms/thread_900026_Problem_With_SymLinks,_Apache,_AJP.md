---
title: "Problem With SymLinks, Apache, AJP"
date: 2008-08-24
forum: Server Platforms
---

### Post by b0neless on 2008-08-24
Hi,

My apache, mod_proxy_ajp configuration is having issues following any symlinks in docroot.  Trying to access any URL that is a symlink results in 404.

Here is my setup:
    Ubuntu 7.10 64bit
    Apache 2.2.4 (installed from respository)
    default mod_proxy_ajp install with apache
    mod_proxy_ajp configured with JBoss 4.0.5

Here are the lines I added to /etc/apache2/sites-enabled/000-default to enable pass-through to Jboss:
```
ProxyPass / ajp://127.0.1.1:8009/
ProxyPassReverse / ajp://127.0.1.1:8009/

<Proxy Ajp://127.0.1.1>
    Options Indexes FollowSymLinks MultiViews
    AllowOverride None
    Order allow,deny
    allow from all
</Proxy>
```

I made a simple symlink test with test2.html -> test1.html.  To test the permissions, I set them to 777 and tried chowning to root, www-data, my username.  All test fail with 404.

If I disable ajp, all symlinks work fine in the default apache DocumentRoot.  

Any suggestions?

Thanks,

Jimmy

---

