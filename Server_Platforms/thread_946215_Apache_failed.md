---
title: "Apache failed"
date: 2008-10-13
forum: Server Platforms
---

### Post by talon21 on 2008-10-13
Hi, 

I'm runing a VPS on Debian OS.
It's seems that I manage to mess up my apache when I try to restart it I receive the following:

vps:/etc/apache2/sites-available# /etc/init.d/apache2 restart
Forcing reload of web server (apache2).../etc/init.d/apache2: line 78: kill: (15746) - No such process
apache2: Syntax error on line 185 of /etc/apache2/apache2.conf: Syntax error on line 1 of /etc/apache2/mods-enabled/php5.load: Cannot load /usr/lib/apache2/modules/libphp5.so into server: /usr/lib/apache2/modules/libphp5.so: cannot open shared object file: No such file or directory
 failed!
 
Please advice thanks,
Tal

---

### Post by lykwydchykyn on 2008-10-13
Offhand, it sounds like your php5 installation is messed up.  Try:
```

aptitude reinstall php5 libapache2-mod-php5

```

---

