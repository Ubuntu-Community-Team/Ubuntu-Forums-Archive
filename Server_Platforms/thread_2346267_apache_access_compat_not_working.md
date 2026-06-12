---
title: "apache access_compat not working"
date: 2016-12-13
forum: Server Platforms
---

### Post by bastibasti2 on 2016-12-13
Hi Im trying to convert a suse webserver (apache2.2) to ubuntu 16.04 server (Apache 2.4.18)

Seems like the access compat module doesnt work
```

       Options Indexes FollowSymLinks
        AllowOverride All
        Order allow,deny
        Allow from all

```
If I add 
```
Require all granted
```

to the config it seems to work. 

However the access_compat module and its dependencies seem to be loaded
```

apachectl -t -D DUMP_MODULES | grep -E "(access|authn|authz)"
 access_compat_module (shared)
 authn_core_module (shared)
 authn_file_module (shared)
 authz_core_module (shared)
 authz_host_module (shared)
 authz_user_module (shared)


```

Is this a bug?

---

### Post by slickymaster on 2016-12-13
*Thread moved to **Server Platforms**.*

---

### Post by SeijiSensei on 2016-12-13
The access control directives were changed in 2.4.  Read this: [https://httpd.apache.org/docs/2.4/howto/access.html](https://httpd.apache.org/docs/2.4/howto/access.html)

---

### Post by bastibasti2 on 2016-12-13
Hi,

I know. thats why I activated the access_compat module as stated here

[https://httpd.apache.org/docs/2.4/mod/mod_access_compat.html](https://httpd.apache.org/docs/2.4/mod/mod_access_compat.html)

and in my above code snipplet.
However I found that this module is inop on ubuntu, - whereas is really works well on opensuse 42.2 which makes me wonder whether the ubuntu package is faulty or not.

---

### Post by SeijiSensei on 2016-12-13
I just changed my configuration files to use the new directives.  Wasn't that hard.

---

### Post by bastibasti2 on 2016-12-14
thtas not the purpose of the module, isnt it?

---

### Post by SeijiSensei on 2016-12-14
I'm suggesting you forget about the module and just deal directly with the change.

---

