---
title: "Lighttpd + php fast_cgi"
date: 2009-08-27
forum: Server Platforms
---

### Post by dragos2 on 2009-08-27
I installed lighttpd and php using this tutorial
[https://wiki.ubuntu.com/Lighttpd+PHP](https://wiki.ubuntu.com/Lighttpd+PHP)

but when I reload the lighttpd configuration is fails
```

root@vps:/# /etc/init.d/lighttpd reload
 * Reloading web server configuration lighttpd                                2009-08-27 15:45:45: (plugin.c.165) dlopen() failed for: /usr/lib/lighttpd/mod_fastcgi.conf.so /usr/lib/lighttpd/mod_fastcgi.conf.so: cannot open shared object file: No such file or directory 
2009-08-27 15:45:45: (server.c.621) loading plugins finally failed 
                                                                       [fail]

```

Any ideas how to fix this ?

---

