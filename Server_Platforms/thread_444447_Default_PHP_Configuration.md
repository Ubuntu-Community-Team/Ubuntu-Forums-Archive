---
title: "Default PHP Configuration?"
date: 2007-05-15
forum: Server Platforms
---

### Post by Naatan on 2007-05-15
Is there some sort of default configuration that all hosts use to configure PHP on their server? I have compiled PHP from source on mine but I'm having a bit of problems with some parts of it, for example eval gives a very different result on my php configuration..

I used:

./configure --prefix=/usr/local/php --with-apxs2=/usr/local/apache2/bin/apxs --with-mysql=/usr/local/mysql --with-mcrypt=/usr/local/lib/libmcrypt --enable-mbstring

Please advise me on what to install with PHP, what to enable and what to disable..

thanks in advance :)

---

### Post by Naatan on 2007-05-15
bump.. anyone?

---

### Post by Frosty Cold Drink on 2007-05-15
> **Naatan said:**
> Is there some sort of default configuration that all hosts use to configure PHP on their server? I have compiled PHP from source on mine but I'm having a bit of problems with some parts of it, for example eval gives a very different result on my php configuration..

I used:

./configure --prefix=/usr/local/php --with-apxs2=/usr/local/apache2/bin/apxs --with-mysql=/usr/local/mysql --with-mcrypt=/usr/local/lib/libmcrypt --enable-mbstring

Please advise me on what to install with PHP, what to enable and what to disable..

thanks in advance :)

There isn't really an "industry standard", but there are some modules which you will almost always find. eval() should always return something similar unless you are using it to call some optional module functions, platform dependant functions, or something else weird is going on (like register_globals issues). Perhaps if you posted what you are getting, and what you think you should be getting, some troubleshooting can be done.

That said, here is what my web host uses. They aren't normal, though. They are damn good, and specialize in high quality hosting and support, dynamic sites using content management systems and web forums, and space for web developers.

```
'./configure' '--prefix=/usr' '--bindir=/usr/bin' '--mandir=/usr/share/man' '--localstatedir=/var' '--libdir=/usr/lib' '--datadir=/usr/share' '--includedir=/usr/include' '--sysconfdir=/etc' '--cache-file=../config.cache' '--with-config-file-path=/etc' '--with-config-file-scan-dir=/etc/php.d' '--disable-debug' '--disable-rpath' '--with-bz2' '--with-db4=/usr' '--with-curl' '--with-exec-dir=/usr/bin' '--with-freetype-dir=/usr' '--with-png-dir=/usr' '--with-gd' '--with-gdbm' '--with-gettext' '--with-ncurses=shared' '--with-gmp' '--with-iconv' '--with-jpeg-dir=/usr' '--with-openssl' '--with-png' '--with-pspell' '--with-regex=system' '--with-xml' '--with-expat-dir=/usr' '--with-dom=shared,/usr' '--with-dom-xslt=/usr' '--with-dom-exslt=/usr' '--with-xmlrpc=shared' '--with-readline' '--with-pcre=/usr' '--with-zlib' '--with-layout=GNU' '--with-pear=/usr/share/pear' '--with-mhash=shared' '--with-imap=shared' '--with-imap-ssl' '--with-kerberos' '--with-ldap=shared' '--with-mcrypt=shared' '--with-mysql=shared,/usr' '--with-unixODBC=shared,/usr' '--with-pgsql=shared' '--without-oci8' '--with-snmp=shared,/usr' '--enable-ucd-snmp-hack' '--enable-bcmath' '--enable-exif' '--enable-ftp' '--enable-magic-quotes' '--enable-safe-mode' '--enable-sockets' '--enable-sysvsem' '--enable-sysvshm' '--enable-discard-path' '--enable-track-vars' '--enable-trans-sid' '--enable-yp' '--enable-wddx' '--enable-memory-limit' '--enable-bcmath' '--enable-shmop' '--enable-calendar' '--enable-dbx' '--enable-dio' '--enable-mcal' '--enable-mbstring=shared' '--enable-mbstr-enc-trans' '--enable-mbregex' '--enable-inline-optimization' '--enable-gd-native-ttf' '--enable-pic' '--with-apxs2=/usr/sbin/apxs'
```

---

