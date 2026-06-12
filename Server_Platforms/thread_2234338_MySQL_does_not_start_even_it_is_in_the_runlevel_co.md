---
title: "MySQL does not start even it is in the runlevel configuration"
date: 2014-07-14
forum: Server Platforms
---

### Post by xarem on 2014-07-14
Hey all

on two of my ubuntu server 12.04, mysql does not start even it is in the runlevels:

```
root@...:~# update-rc.d -f mysql remove Removing any system startup links for /etc/init.d/mysql ...
   /etc/rc0.d/K20mysql
   /etc/rc1.d/K20mysql
   /etc/rc2.d/S20mysql
   /etc/rc3.d/S20mysql
   /etc/rc4.d/S20mysql
   /etc/rc5.d/S20mysql
   /etc/rc6.d/K20mysql
root@...:~# update-rc.d mysql defaults
update-rc.d: warning: /etc/init.d/mysql missing LSB information
update-rc.d: see <http://wiki.debian.org/LSBInitScripts>
 Adding system startup for /etc/init.d/mysql ...
   /etc/rc0.d/K20mysql -> ../init.d/mysql
   /etc/rc1.d/K20mysql -> ../init.d/mysql
   /etc/rc6.d/K20mysql -> ../init.d/mysql
   /etc/rc2.d/S20mysql -> ../init.d/mysql
   /etc/rc3.d/S20mysql -> ../init.d/mysql
   /etc/rc4.d/S20mysql -> ../init.d/mysql
   /etc/rc5.d/S20mysql -> ../init.d/mysql
```


in the initctl, it shows no «start on», what's very strange for me.
```
root@...:~# initctl show-config
...
mysql
  stop on starting rc RUNLEVEL=[016]
...
```

```
root@...:~# mysqld --version
mysqld  Ver 5.5.37-0ubuntu0.12.04.1 for debian-linux-gnu on x86_64 ((Ubuntu))
```



can someone help me please?

thanks a lot!

kind regards

---

