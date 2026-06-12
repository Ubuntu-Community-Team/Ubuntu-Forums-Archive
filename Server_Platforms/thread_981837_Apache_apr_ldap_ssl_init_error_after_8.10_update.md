---
title: "Apache apr_ldap_ssl_init error after 8.10 update"
date: 2008-11-14
forum: Server Platforms
---

### Post by breiko on 2008-11-14
Hi,
i have just updated my ubuntu version to 8.10 and I can't start apache..
.. this is the error i got:

```
carlo@carlo-desktop:/usr/lib$ sudo /etc/init.d/apache2 restart
 * Restarting web server apache2   
/usr/sbin/apache2: symbol lookup error: /usr/sbin/apache2: undefined symbol: apr_ldap_ssl_init
     
```

I tried reinstalling apache and utils but I have always the same error.
Someone can sort it out?
Cheers.

---

### Post by breiko on 2008-11-17
(up)

---

### Post by Dedoimedo on 2008-11-17
Hello,

Did you disable any modules in httpd.conf - like ldap module?
Please go through the list and see if it's enabled.

Try running apache directly (httpd).

Dedoimedo

---

### Post by erben22 on 2008-11-21
The following worked for me after encountering this same issue going from 8.04 to 8.10:

```

sudo aptitude reinstall libapr1 libaprutil1

```

---

### Post by Archon810 on 2008-11-27
More info on this: [http://beerpla.net/2008/07/29/how-to-fix-symbol-lookup-error-usrsbinhttpd2-prefork-undefined-symbol-apr_ldap_ssl_init-2/](http://beerpla.net/2008/07/29/how-to-fix-symbol-lookup-error-usrsbinhttpd2-prefork-undefined-symbol-apr_ldap_ssl_init-2/)

---

### Post by salom on 2008-12-11
Hey i have tried everu thing listed above, and it still not working;( pleae can some one help me

---

### Post by freylingb on 2008-12-12
bump, trying now to get the older libapr packages so I can relink as suggested.

Tried reinstall of libapr1 libaprutil1 and apache2

brian@brian-hp:~$ ls -la /usr/lib | grep libapr
lrwxrwxrwx   1 root root       18 2008-12-12 08:04 libapr-1.so.0 -> libapr-1.so.0.2.12
-rw-r--r--   1 root root   170576 2008-06-19 08:33 libapr-1.so.0.2.12
lrwxrwxrwx   1 root root       22 2008-12-12 08:04 libaprutil-1.so.0 -> libaprutil-1.so.0.2.12
-rw-r--r--   1 root root   116956 2008-06-21 18:25 libaprutil-1.so.0.2.12

---

### Post by freylingb on 2008-12-15
I have now tried a purge of libapr1 and libaprutil1 which completely wiped those packages along with all apaches packages, subversions packages, and any files they leave on the filesystem, and then reinstalled.  I am still having the same problem : (.

brian@brian-hp:/etc$ sudo /etc/init.d/apache2 start
 * Starting web server apache2                                                  /usr/sbin/apache2: symbol lookup error: /usr/sbin/apache2: undefined symbol: apr_ldap_ssl_init
                                                                         [fail]

---

