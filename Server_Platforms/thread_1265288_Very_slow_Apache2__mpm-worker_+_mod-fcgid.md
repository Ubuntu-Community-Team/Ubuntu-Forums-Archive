---
title: "Very slow Apache2 : mpm-worker + mod-fcgid"
date: 2009-09-13
forum: Server Platforms
---

### Post by BarsMonster2 on 2009-09-13
Hi, I am tuning performance of my web server.
Initially I had default LAMP installed on Ubuntu Server 9.04, and it was able to process around 250 hits per second.

Then I decided to improve it, and installed mpm-worker + mod-fcgid. Now it can do just 30 hits per second. It runs ALOT of php processes, and seems to not reuse them at all even when I am stress testing with concurrency 1 (when just 1 worker should be fine). I am happy I am not at traffic spike now :(

I was trying to limit number of php processed by:
/etc/apache2/mods-available/fcgid.conf via :

> <IfModule mod_fcgid.c>
  AddHandler    fcgid-script .fcgi
  IPCConnectTimeout 20
  MaxProcessCount 1
  DefaultMaxClassProcessCount 1

</IfModule>
But it does not help.

Other configuration is: domain.name.conf

> <VirtualHost domain.name>
DocumentRoot "/var/www/domain.name"
ServerName domain.name
<Directory "/var/www/domain.name">
Options +ExecCGI
AddHandler fcgid-script .php
FCGIWrapper /var/www/domain.name/php5.fcgi .php
allow from all
Options +Indexes
</Directory>
</VirtualHost>
php5.fcgi is:
> #!/bin/sh
PHPRC=/etc/php5/cgi/
export PHPRC
export PHP_FCGI_MAX_REQUESTS=5000
export PHP_FCGI_CHILDREN=8
exec /usr/lib/cgi-bin/php -c /var/www/domain.name/php.ini
Any ideas?

---

### Post by BarsMonster2 on 2009-09-13
While initial problem is still actual, I've tried to return to default configuration, and it works again fast, but... For some reason on the front page it returns PHP source instead of interpreting it. The rest of the site works fine. [http://3.14.by/](http://3.14.by/)

Hands down :(

---

### Post by BarsMonster2 on 2009-09-14
Any ideas?

---

### Post by deoren on 2010-10-30
Did you ever figure out the performance problem? I'm looking to migrate from mod_php/apache prefork to the setup you have.

Thanks.

---

### Post by hantechbl on 2010-10-31
Had a similar problem but with 10.04 not loading php at all, I upgraded to 10.10 and now it works fine, but alo very slowly, I don't think I have those modules either.

---

### Post by Cashel on 2011-01-05
Just sorting this out myself... found a lot of good info here:

[http://www.camelrichard.org/apache-prefork-vs-worker](http://www.camelrichard.org/apache-prefork-vs-worker)

Good Luck

---

