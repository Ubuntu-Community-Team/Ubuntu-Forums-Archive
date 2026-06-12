---
title: "php execution Permission denied"
date: 2009-05-28
forum: Server Platforms
---

### Post by tutunmayan on 2009-05-28
Hi

I created a php socket server similar to [http://djz.hu/2007/07/26/php-socket-server-chat-gateway-for-flash-clients/](http://djz.hu/2007/07/26/php-socket-server-chat-gateway-for-flash-clients/) 

first line is **#!/usr/bin/php -q** in the example
(I guess this tells to linux where is php located)

But in my ubuntu there is no location like /usr/bin/php

Typing whereis php5 I get this result:

**php5: /etc/php5 /usr/lib/php5 /usr/lib64/php5 /usr/share/php5**

i tried these four location as first line (for exapmle: #!/etc/php5 -q) but all returns the same error:
**-bash: /var/www/chat/socketShell.php: /usr/share/php5: bad interpreter: Permission denied**

my php file is executable


What is the problem I cant figure out.
Please help


**My Ubunutu is**
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.10
DISTRIB_CODENAME=intrepid
DISTRIB_DESCRIPTION="Ubuntu 8.10"


I searched php location and it returns this:

**find / -name "php*"**

/var/lib/php5
/var/lib/dpkg/info/php5-common.conffiles
/var/lib/dpkg/info/php5-sybase.conffiles
/var/lib/dpkg/info/php5-mysql.postinst
/var/lib/dpkg/info/php5-curl.postinst
/var/lib/dpkg/info/php5-sybase.list
/var/lib/dpkg/info/php5-mysql.conffiles
/var/lib/dpkg/info/php5-common.list
/var/lib/dpkg/info/php5-common.md5sums
/var/lib/dpkg/info/php5-mysql.md5sums
/var/lib/dpkg/info/php5-gd.conffiles
/var/lib/dpkg/info/php5-mcrypt.conffiles
/var/lib/dpkg/info/php5-curl.list
/var/lib/dpkg/info/php5-gd.list
/var/lib/dpkg/info/php5-curl.md5sums
/var/lib/dpkg/info/php5-sybase.postinst
/var/lib/dpkg/info/php5-sybase.prerm
/var/lib/dpkg/info/php5-gd.md5sums
/var/lib/dpkg/info/php5-mcrypt.list
/var/lib/dpkg/info/php5-curl.conffiles
/var/lib/dpkg/info/php5-mysql.list
/var/lib/dpkg/info/php5-mcrypt.md5sums
/var/lib/dpkg/info/php5-mcrypt.preinst
/var/lib/dpkg/info/php5-sybase.md5sums
/var/lib/dpkg/info/php5-sybase.preinst
/var/lib/dpkg/info/php5-common.postrm
/var/lib/dpkg/info/php5-gd.postinst
/var/lib/dpkg/info/php5-sybase.postrm
/var/cache/apt/archives/php5-common_5.2.6-2ubuntu4.1_amd64.deb
/var/cache/apt/archives/php5-mcrypt_5.2.6-0ubuntu2_amd64.deb
/var/cache/apt/archives/php5-curl_5.2.6-2ubuntu4.1_amd64.deb
/var/cache/apt/archives/php5-sybase_5.2.6-2ubuntu4.1_amd64.deb
/var/cache/apt/archives/php5-gd_5.2.6-2ubuntu4_amd64.deb
/var/cache/apt/archives/php5-gd_5.2.6-2ubuntu4.2_amd64.deb
/var/cache/apt/archives/php5-common_5.2.6-2ubuntu4.2_amd64.deb
/var/cache/apt/archives/php5-gd_5.2.6-2ubuntu4.1_amd64.deb
/var/cache/apt/archives/php5-curl_5.2.6-2ubuntu4_amd64.deb
/var/cache/apt/archives/php5-mysql_5.2.6-2ubuntu4.1_amd64.deb
/var/cache/apt/archives/php5-sybase_5.2.6-2ubuntu4.2_amd64.deb
/var/cache/apt/archives/php5-curl_5.2.6-2ubuntu4.2_amd64.deb
/var/cache/apt/archives/php5-sybase_5.2.6-2ubuntu4_amd64.deb
/var/cache/apt/archives/php5-mysql_5.2.6-2ubuntu4.2_amd64.deb
/usr/share/lintian/overrides/php5-common
/usr/share/webmin/phpini
/usr/share/webmin/phpini/phpini-lib.pl
/usr/share/webmin/mailboxes/xinha/contrib/php-xinha.php
/usr/share/webmin/file/xinha/contrib/php-xinha.php
/usr/share/webmin/blue-theme/phpini
/usr/share/ubuntu-serverguide/html/C/php5.html
/usr/share/doc/php5-common
/usr/share/doc/php5-common/examples/php.ini-paranoid
/usr/share/doc/php5-common/examples/php.ini-recommended
/usr/share/doc/php5-common/examples/php.ini-dist
/usr/share/doc/php5-mysql
/usr/share/doc/php5-curl
/usr/share/doc/php5-mcrypt
/usr/share/doc/php5-gd
/usr/share/doc/php5-sybase
/usr/share/php5
/usr/share/php5/php.ini-dist.cli
/usr/share/php5/php.ini-dist
/usr/lib/php5
/etc/apparmor.d/abstractions/php5
/etc/webmin/phpini
/etc/cron.d/php5
/etc/apache2/mods-available/php5.load
/etc/apache2/mods-available/php5.conf
/etc/apache2/mods-enabled/php5.load
/etc/apache2/mods-enabled/php5.conf
/etc/php5
/etc/php5/apache2/php.ini

---

### Post by cdenley on 2009-05-28
```

sudo apt-get install php5-cli

```

---

### Post by BkkBonanza on 2009-05-28
Judging by your /var/cache/apt file list you don't have php5-cli package installed which is needed for the command line interpreter. The command line interperter is usually installed at /usr/bin. So I expect that you need to install using **sudo apt-get install php5-cli**

---

