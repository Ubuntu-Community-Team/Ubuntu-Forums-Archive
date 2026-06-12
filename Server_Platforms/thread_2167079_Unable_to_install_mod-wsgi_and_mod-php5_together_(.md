---
title: "Unable to install mod-wsgi and mod-php5 together (Apache2)"
date: 2013-08-12
forum: Server Platforms
---

### Post by odi86 on 2013-08-12
I'm using Ubuntu 12.04 LTS on my server and I try desperately to install libapache2-mod-wsgi and libapache2-mod-php5 on it. But due to package conflicts this is not possible.

As aptitude is known for it's conflict resolution capabilitites, I tried many different configurations, but there was none that included both new packages:

```
odi@myserver:~$ sudo aptitude install libapache2-mod-wsgi libapache2-mod-php5
The following NEW packages will be installed:
  apache2{ab} apache2-bin{ab} apache2-data{ab} apache2.2-common{ab} libapache2-mod-php5 libapache2-mod-wsgi libapr1{a} libaprutil1{a} libaprutil1-dbd-sqlite3{a} libaprutil1-ldap{a} libjson-c2{a} 
  liblua5.1-0{a} libonig2{a} libqdbm14{a} php5-cli{a} php5-common{a} php5-json{a} ssl-cert{a} 
The following packages will be upgraded:
  libedit2 
1 packages upgraded, 18 newly installed, 0 to remove and 134 not upgraded.
Need to get 8,156 kB of archives. After unpacking 26.9 MB will be used.
The following packages have unmet dependencies:
 apache2 : Conflicts: apache2.2-common but 2.2.22-1ubuntu1.4 is to be installed.
 apache2.2-common : Depends: apache2.2-bin (= 2.2.22-1ubuntu1.4) but it is not going to be installed.
                    Depends: apache2-utils but it is not going to be installed.
 apache2-bin : Conflicts: apache2.2-common but 2.2.22-1ubuntu1.4 is to be installed.
 apache2-data : Conflicts: apache2.2-common but 2.2.22-1ubuntu1.4 is to be installed.
The following actions will resolve these dependencies:

     Keep the following packages at their current version:
1)     apache2.2-common [Not Installed]                   
2)     libapache2-mod-wsgi [Not Installed]                



Accept this solution? [Y/n/q/?]

```

Maybe I'm missing something obvious or is this a bug? Any help is appreciated.

---

### Post by odi86 on 2013-08-26
In the meantime I learned that this is a common problem, as mod-php5 need apache2-mpm-prefork, while mod-wsgi need apache2-mpm-worker.
The solution is pretty simple: don't use mod-php5, but use libapache2-mod-fcgid and php5-fpm and run PHP using fastcgi:

```
<Directory /var/www/app/>
  AddHandler fcgid-script .php
  FCGIWrapper /usr/bin/php .php
  Options ExecCGI
</Directory>
```

---

