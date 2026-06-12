---
title: "Apache fails to start due to error in apache.conf regarding xml-rpc"
date: 2008-05-31
forum: Server Platforms
---

### Post by rsteckly7 on 2008-05-31
I get this error when I try to start apache2:

 * Starting web server apache2
apache2: Syntax error on line 185 of /etc/apache2/apache2.conf: Syntax error on line 1 of /etc/apache2/mods-enabled/xmlrpc.load: Cannot load /usr/lib/apache2/modules/mod_xmlrpc.so into server: /usr/lib/apache2/modules/mod_xmlrpc.so: undefined symbol: xmlrpc_registry_new
   ...fail!

What have I done wrong?

---

### Post by quelx on 2008-05-31
You may want to either install the debian unstable package of **libapache2-mod-xmlrpc2** or remove it from the enabled apache2 modules

```
sudo a2dismod xmlrpc
```
and restart apache

bugreport:
[https://bugs.launchpad.net/ubuntu/+source/libapache2-mod-xmlrpc2/+bug/157424](https://bugs.launchpad.net/ubuntu/+source/libapache2-mod-xmlrpc2/+bug/157424)

---

### Post by rsteckly7 on 2008-06-01
Thanks!  That got rid of the xml error.  But now I get:

apache2: bad user name ${APACHE_RUN_USER}

What could be wrong here?

---

### Post by quelx on 2008-06-01
ummm... maybe

[http://ubuntuforums.org/showthread.php?t=804436](http://ubuntuforums.org/showthread.php?t=804436)

Are you (re)starting apache with ```
sudo /etc/init.d/apache2 restart
```

---

### Post by rsteckly7 on 2008-06-01
Works like a champ now!  Thank you so much!

---

