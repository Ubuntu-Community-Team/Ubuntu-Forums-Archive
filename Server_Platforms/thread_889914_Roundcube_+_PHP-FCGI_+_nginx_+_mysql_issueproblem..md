---
title: "Roundcube + PHP-FCGI + nginx + mysql issue/problem."
date: 2008-08-14
forum: Server Platforms
---

### Post by thejinx on 2008-08-14
Hello,
 I just setup my server, well actually migrated from CentOS to Ubuntu 8.04.1. I installed nginx from Ubuntu repo, and build my own php-cgi, mysql server.

 Now the same things I was doing on CentOS and never had any issue with it. Seems now that roundcube doesn't work at all under Ubuntu. 

Here is the error: 

[14-Aug-2008 15:08:58 +0200] DB Error: DB Error: constraint violation Query: INSERT INTO session (sess_id, vars, ip, created, changed) VALUES ('3nuv7j7a9a3p1rndmegam1lnf5', 'user_lang|s:5:\"en_US\";auth_time|i:1218719338;temp|b:1;task|s:4:\"mail\";', NULL, now(), now()) [nativecode=1048 ** Column 'ip' cannot be null] in /srv/www/visualserver.org/mail.v2/program/include/rcube_db.inc on line 530
[14-Aug-2008 15:09:01 +0200] DB Error: DB Error: constraint violation Query: INSERT INTO session (sess_id, vars, ip, created, changed) VALUES ('3nuv7j7a9a3p1rndmegam1lnf5', 'user_lang|s:5:\"en_US\";auth_time|i:1218719341;temp|b:1;task|s:4:\"mail\";', NULL, now(), now()) [nativecode=1048 ** Column 'ip' cannot be null] in /srv/www/visualserver.org/mail.v2/program/include/rcube_db.inc on line 530
[14-Aug-2008 15:09:03 +0200] DB Error: DB Error: constraint violation Query: INSERT INTO session (sess_id, vars, ip, created, changed) VALUES ('3nuv7j7a9a3p1rndmegam1lnf5', 'user_lang|s:5:\"en_US\";auth_time|i:1218719343;temp|b:1;task|s:4:\"mail\";', NULL, now(), now()) [nativecode=1048 ** Column 'ip' cannot be null] in /srv/www/visualserver.org/mail.v2/program/include/rcube_db.inc on line 530

Seems that roundcube cant connect to update some parts or some infos in mysql. Also this error will appear in Postgresql.

Does anyone know what could be the issue?

Here are the build settings for the custom php and mysql:

PHP (also php is running as fastcgi on port 50000)
./configure --enable-fastcgi --disable-cli --enable-force-cgi-redirect --prefix=/application/php-cgi --with-config-file-path=/application/php-cgi/etc --enable-bcmath --enable-calendar --with-curl --enable-exif --enable-ftp --with-gd --with-gettext --with-iconv --enable-mbstring --enable-mbregex --with-mcrypt --with-mhash --enable-magic-quotes --with-mysql=/application/mysql --with-openssl --enable-discard-path --with-pear --with-pgsql=/application/pgsql --with-xsl --enable-sockets --with-ttf --enable-gd-native-ttf --with-zlib

MySQL 
./configure --prefix=/application/mysql --with-openssl --with-machine-type --with-system-type --with-mysqld-user=mysql --without-docs --without-bench --with-big-tables --enable-large-files-without-debug --disable-maintainer-mode

Both of this build settings worked on CentOS perfectly. As I said before Nginx is from Ubuntu repos.

Please let me know what is the problem and/or issue, or where I am going wrong.

(PHP was tested with the php.ini-recommended file and customer php.ini configuration file, doesn't change anything).

---

