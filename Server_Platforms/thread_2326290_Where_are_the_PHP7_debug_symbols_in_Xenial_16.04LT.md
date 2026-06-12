---
title: "Where are the PHP7 debug symbols in Xenial 16.04LTS ?"
date: 2016-05-30
forum: Server Platforms
---

### Post by bob_jones2 on 2016-05-30
It's pretty difficult to track down the cause of a PHP FPM core dump if you've got no debug symbols !  Previous versions of LTS had debug packages ?  But seemingly Xenial has none ?

```

$sudo apt-cache search php7 | fgrep debug   <=== yields no results ;-(

$ sudo apt-cache search php7-*
libapache2-mod-php7.0 - server-side, HTML-embedded scripting language (Apache 2 module)
php7.0 - server-side, HTML-embedded scripting language (metapackage)
php7.0-cgi - server-side, HTML-embedded scripting language (CGI binary)
php7.0-cli - command-line interpreter for the PHP scripting language
php7.0-common - documentation, examples and common module for PHP
php7.0-curl - CURL module for PHP
php7.0-dev - Files for PHP7.0 module development
php7.0-gd - GD module for PHP
php7.0-gmp - GMP module for PHP
php7.0-json - JSON module for PHP
php7.0-ldap - LDAP module for PHP
php7.0-mysql - MySQL module for PHP
php7.0-odbc - ODBC module for PHP
php7.0-opcache - Zend OpCache module for PHP
php7.0-pgsql - PostgreSQL module for PHP
php7.0-pspell - pspell module for PHP
php7.0-readline - readline module for PHP
php7.0-recode - recode module for PHP
php7.0-snmp - SNMP module for PHP
php7.0-sqlite3 - SQLite3 module for PHP
php7.0-tidy - tidy module for PHP
php7.0-xml - DOM, SimpleXML, WDDX, XML, and XSL module for PHP
php7.0-xmlrpc - XMLRPC-EPI module for PHP
php-all-dev - package depending on all supported PHP development packages
libphp7.0-embed - HTML-embedded scripting language (Embedded SAPI library)
php7.0-bcmath - Bcmath module for PHP
php7.0-bz2 - bzip2 module for PHP
php7.0-enchant - Enchant module for PHP
php7.0-fpm - server-side, HTML-embedded scripting language (FPM-CGI binary)
php7.0-imap - IMAP module for PHP
php7.0-interbase - Interbase module for PHP
php7.0-intl - Internationalisation module for PHP
php7.0-mbstring - MBSTRING module for PHP
php7.0-mcrypt - libmcrypt module for PHP
php7.0-phpdbg - server-side, HTML-embedded scripting language (PHPDBG binary)
php7.0-soap - SOAP module for PHP
php7.0-sybase - Sybase module for PHP
php7.0-zip - Zip module for PHP
php7.0-xsl - XSL module for PHP (dummy)
```

---

### Post by martijntje on 2016-05-31
For some reason - unknown to me - they do not show up in the repository. The package you are looking for, however, is called php7.0-cli-dbgsym and can be downloaded from launchpad:

[https://launchpad.net/ubuntu/xenial/amd64/php7.0-cli-dbgsym/7.0.4-7ubuntu2.1](https://launchpad.net/ubuntu/xenial/amd64/php7.0-cli-dbgsym/7.0.4-7ubuntu2.1)
[https://launchpad.net/ubuntu/xenial/amd64/php7.0-cli-dbgsym/7.0.4-7ubuntu2.1](https://launchpad.net/ubuntu/xenial/amd64/php7.0-cli-dbgsym/7.0.4-7ubuntu2.1)

Assuming a 64-bit system of course. This took me quite a while to find too!

---

### Post by bob_jones2 on 2016-05-31
Fabulous. Thank you.

---

### Post by nacc3 on 2016-05-31
As mentioned in [https://bugs.launchpad.net/ubuntu/+source/php7.0/+bug/1587528](https://bugs.launchpad.net/ubuntu/+source/php7.0/+bug/1587528), the correct fix to this issue is to use the ddeb archives as documented at [https://wiki.ubuntu.com/Debug%20Symbol%20Packages](https://wiki.ubuntu.com/Debug%20Symbol%20Packages).

---

