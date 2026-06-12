---
title: "make phpmyadmin worked with suphp"
date: 2011-05-09
forum: Server Platforms
---

### Post by mreza69 on 2011-05-09
hi everyone!
I had phpmyadmin installed on my ubuntu and when I install suphp, it broken and show me save as dialog on firefox. I searched on google and found nothing useful. finaly I mixed solutions and could solve this problem. th solution is:

**1-** after installing suphp goto **/etc/suphp/suphp.conf** and add your phpmyadmin address to scripts paths like this:
[PHP];Path all scripts have to be in
docroot=/var/www:${HOME}/public_html:/usr/share/phpmyadmin[/PHP]and make **min_uid** and **min_gid** to 33 (point to www-data user) like this:
[PHP]; Minimum UID
min_uid=33

; Minimum GID
min_gid=33[/PHP][B]
2-[/B] run this command on terminal to set user ang group of your phpmyadmin directory and subdirectory and files to www-data:
[PHP]chown -R www-data:www-data /usr/share/phpmyadmin[/PHP]**3- **run this command on terminal to remove mod_php loading:
[PHP]rm -rf /etc/apache2/mods-available/php5.load /etc/apache2/mods-enabled/php5.load[/PHP][B]
4-[/B] open your apache config file (always in **/etc/apache2/sites-available/default**) and find your phpmyadmin configure. now change settings for work in suphp. something like this:

[PHP]<VirtualHost *:80>
ServerAdmin webmaster@localhost
ServerName localhost
Alias /phpmyadmin /usr/share/phpmyadmin
suPHP_Engine on
#suPHP_UserGroup www-data www-data
AddHandler x-httpd-suphp .phpsu
#PHP_AddHandler x-httpd-suphp
<directory /usr/share/phpmyadmin>
Options Indexes FollowSymLinks
DirectoryIndex index.php
<ifmodule mod_php5.c>
AddType application/x-httpd-php .php
php_flag magic_quotes_gpc Off
php_flag track_vars On
php_flag register_globals Off
php_value include_path .
</ifmodule>
</directory>
# Disallow web access to directories that don't need it
<directory /usr/share/phpmyadmin/setup>
Order Deny,Allow
Deny from All
</directory>
<directory /usr/share/phpmyadmin/libraries>
Order Deny,Allow
Deny from All
</directory>
</VirtualHost>[/PHP]**5- **restart your apache2 in terminal:

[PHP]sudo service apache2 restart[/PHP]enjoy!

---

### Post by mvaldez on 2012-06-17
Hi,

lowering min_uid and min_gid so low may cause a security problem. Setting it to 33 means half the non-user accounts in Ubuntu (like backup, list, syslog, postfix, etc.) now can be allowed to run with suphp. The purpose of those settings is exactly the opposite: to allow only user accounts (or better, a subset of user accounts) to run PHP scripts.

The safer solution is to create an user for phpmyadmin with a higher UID/GID and then change the ownership of the files.


In my servers I have separate accounts used only for websites, with UIDs/GIDs starting at 5000.


Hope this helps.

Regards,

MValdez.

---

