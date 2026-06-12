---
title: "Starting apache with more file descriptors"
date: 2011-10-17
forum: Server Platforms
---

### Post by [mm] on 2011-10-17
Hello,

I'm using Ubuntu server 10.4 and I want to start my apache with more than the default 1024 file descriptors. So I enabled *pam_limits.so* in */etc/pam.d/su* and in */etc/security/limits.conf *I wrote the following:

```
root hard nofile 10000
root soft nofile 10000
www-data hard nofile 5000
www-data soft nofile 5000
```

If I type *su -c "ulimit -n" www-data* I get 5000, as expected. But if I restart the Apache as root and check */proc/<pid>/limits* it has 10000 descriptors. And if I reboot my system it still has only 1024.

Can anyone tell me how I could run my apache with more than those 1024 descriptors after a reboot?

---

### Post by [mm] on 2011-10-20
I don't know how to solve my problem with the limits.conf, but I found another solution: In  /etc/apache2/envvars you can set the following option:

```
APACHE_ULIMIT_MAX_FILES="ulimit -n 9999"
```

---

