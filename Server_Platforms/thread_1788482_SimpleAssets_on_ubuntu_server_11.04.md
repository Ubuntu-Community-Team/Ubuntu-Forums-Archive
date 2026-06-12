---
title: "SimpleAssets on ubuntu server 11.04"
date: 2011-06-22
forum: Server Platforms
---

### Post by fbifido on 2011-06-22
my ip: 192.168.0.160
hostname: simpleassets

I can't get this to work, blank page at [http://ip/sqlsimpleassets/](http://ip/sqlsimpleassets/)

software homepage: [http://simpleassets.sourceforge.net/](http://simpleassets.sourceforge.net/)

i have install ubuntu server 11.04 with only ssh selected.
sudo passwd root
:pass123
:pass123
exit

then login as root with password pass123
then tasksel install lamp-server.

press enter for mysql root password.

download simplesql.zip

apt-get install zip unzip.

unzip simplesql.zip

cd Inetpub/wwwroot/
mv sqlsimpleassets /var/www/

vi /var/www/sqlsimpleassets/config.php
set $ip to "192.168.0.160"
set $sql_login to "root"
set $sql_pass to ""

from a another pc, in IE 9 and opera 11.11, type
[http://192.168.0.160/sqlsimpleassets/](http://192.168.0.160/sqlsimpleassets/)

blank page.  ????? why

can someone help me out?

---

### Post by dtfinch on 2011-06-22
I'd open /etc/php5/apache2/php.ini and make sure display_errors and display_startup_errors are both enabled (both were disabled by default last I checked, resulting in blank pages whenever there's an error). Then restart apache with "apache2ctl restart".

---

### Post by fbifido on 2011-06-23
Thanks all i found the problem:

vi /var/www/sqlsimpleassets/config.php
 set $ip to "192.168.0.160"
 set $sql_login to "root"
 set $sql_pass to ""


set $ip must be "127.0.0.1"


BTW: their is a new version out call assetssosimple.
[http://assetssosimple.sourceforge.net/](http://assetssosimple.sourceforge.net/)

---

