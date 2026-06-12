---
title: "Problems restarting apache (webdav issue) after installing PHP &amp; MySQL"
date: 2011-06-07
forum: Server Platforms
---

### Post by rockerboi402 on 2011-06-07
hello.  i am using ubuntu 10.10.  I had installed apache2 and subversion, using webdav, as described in the unbuntu wiki.  SVN was working as expected, I could commit files, etc.  I then installed php5 and mysql, as described in the ubuntu wiki, and i now get the following on apache restart: 

apache2: Syntax error on line 203 of /etc/apache2/apache2.conf: Syntax error on line 2 of /etc/apache2/mods-enabled/dav_svn.load: Cannot load /usr/lib/apache2/modules/mod_dav_svn.so into server: /usr/lib/libgssapi_krb5.so.2: symbol krb5_authdata_context_copy, version krb5_3_MIT not defined in file libkrb5.so.3 with link time reference Action 'configtest' failed.


Any help would be greatly appreciated.  Thank you.

---

### Post by ruffEdgz on 2011-06-07
If you do the following commands, what is the output:
```

sudo updatedb
locate mod_dav_svn.so

```
The error was probably pointing to the mods-enabled directory which then entailed the module 'dav_svn.load'. In that file, it can't load /usr/lib/apache2/modules/mod_dav_svn.so which then talks about certain Kerberos variables that I don't know much about.

Lets start here and then work are way up.

---

### Post by rockerboi402 on 2011-06-07
> **ruffEdgz said:**
> If you do the following commands, what is the output:
```

sudo updatedb
locate mod_dav_svn.so

```
The error was probably pointing to the mods-enabled directory which then entailed the module 'dav_svn.load'. In that file, it can't load /usr/lib/apache2/modules/mod_dav_svn.so which then talks about certain Kerberos variables that I don't know much about.

Lets start here and then work are way up.

The output is as follows:

```

root@gamma:~# updatedb
root@gamma:~# locate mod_dav_svn.so
/usr/lib/apache2/modules/mod_dav_svn.so

```

---

### Post by rockerboi402 on 2011-06-07
> **rockerboi402 said:**
> The output is as follows:

```

root@gamma:~# updatedb
root@gamma:~# locate mod_dav_svn.so
/usr/lib/apache2/modules/mod_dav_svn.so

```

The server was brand new and hand nothing on it. I re-imaged. The problem was I installed apache2 first, then subversion, then php5 and mysql.  This go round I installed apache2, php5 and mysql.  Once those were all working together I installed subversion and everything seems to work :) 

thanks, though!! appreciate it!

---

### Post by chadhs on 2011-06-20
this should be very fixable but it seems you've remedied it yourself by reinstalling the packages. Are you using apache for anything else or just as a means to have webdav for svn? svn+ssh also works very nice. If interested reply and I'll post a link to my blog entry on setting that up.  B-)

---

