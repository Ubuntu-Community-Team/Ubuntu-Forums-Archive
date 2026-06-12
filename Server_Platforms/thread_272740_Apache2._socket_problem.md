---
title: "Apache2. socket problem?"
date: 2006-10-06
forum: Server Platforms
---

### Post by peanut butter on 2006-10-06
after using the guide located at [http://www.howtoforge.com/ubuntu6.06_dtc_isp_server](http://www.howtoforge.com/ubuntu6.06_dtc_isp_server)
i get the following error at startup and when trying to start and restart apache2.
```
root@LAMP:~# /etc/init.d/apache2 restart
 * Forcing reload of apache 2.0 web server...                                   (98)Address already in use: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs
```

i tryed googleing but could not find anything.](*,) ](*,)

---

### Post by peanut butter on 2006-10-07
nevermind. seems to be apache2-mod-log-sql
the package is n0ot working.

Sigh giving up on this software

im going with ispconfig.

---

