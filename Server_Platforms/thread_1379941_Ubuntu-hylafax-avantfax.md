---
title: "Ubuntu-hylafax-avantfax"
date: 2010-01-13
forum: Server Platforms
---

### Post by dehere on 2010-01-13
Hi.everyone.
I setup the ubuntu9.04 and Hylafax. The hylafax running well.and it can send fax with the Frogfax.But when i use setup the Avantfax3.1.6(use the debian-install.sh) when i log in the avantfax,it show me that: 
*Notice: Undefined index: acc_enabled in /var/www/avantfax/includes/AFUserAccount.php on line 3*40
*Your account has been disabled.Please contact the administrator*.
what should i do?thanks 
 
this is my /etc/apache2/sites-enabled/000-default
 
<virtualHost *>
ServerAdmin webmaster@localhost
DocumentRoot /var/www/avantfax
<Directory />
Options FollowSymLinks
AllowOverride None
</Directory>
<Directory /var/www/avantfax>
Order allow,deny
allow from all
# This directive allows us to have apache2's default start page
# in /apache2-default/, but still have / go to the right place
#RedirectMatch ^/$ /apache2-default/
</Directory>
ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
<Directory "/usr/lib/cgi-bin">
AllowOverride None
Options ExecCGI -MultiViews +SymLinksIfOwnerMatch
Order allow,deny
Allow from all
</Directory>
# Possible values include: debug, info, notice, warn, error, crit,
# alert, emerg.
LogLevel warn
CustomLog /var/log/apache2/access.log combined
ServerSignature On
Alias /phpmyadmin "/usr/share/phpmyadmin/"
<Directory "/usr/share/phpmyadmin/">
Options Indexes MultiViews FollowSymLinks
</Directory>
Alias /doc/ "/usr/share/doc/"
<Directory "/usr/share/doc/">
Options Indexes MultiViews FollowSymLinks
AllowOverride None
Order deny,allow
Deny from all
Allow from 127.0.0.0/255.0.0.0 ::1/128
</Directory>
</VirtualHost>
<virtualHost *:80>
DocumentRoot /var/www/avantfax
ServerName avantfax
ErrorLog /var/log/avantfax-error_log
CustomLog /var/log/avantfax-access_log common
</VirtualHost>
 
PS:My english is poor ,and i'm a newbie.

---

### Post by Coreigh on 2010-01-21
Hi there 'dehere'

I am working on this too and I think the problem lies with the mysql database and not with your Apache sites-enabled 000-default file.

I do not know if you file is correct but the "Account Disabled" message is a result of a mysql database lookup.

-- Coreigh

---

### Post by dehere on 2010-01-26
> **Coreigh said:**
> Hi there 'dehere'
 
I am working on this too and I think the problem lies with the mysql database and not with your Apache sites-enabled 000-default file.
 
I do not know if you file is correct but the "Account Disabled" message is a result of a mysql database lookup.
 
-- Coreigh
 
Thank you.Coreigh 
l find some answer in the [COLOR=#008000]**forum.ubuntu.org.cn.** [COLOR=black]the problem is relating to  mysql[/COLOR]**,**[/COLOR][COLOR=#000000]but they don't provide the solution.[/COLOR]
and you?how to solve this problem?

---

### Post by dehere on 2010-01-27
when i use the debian-install.sh to install avantax,it show me that :
 
***ERROR 1045 (28000): Access denied for user ***[EMAIL="'root'@'localhost'"]***'root'@'localhost'***[/EMAIL][I][B] (using password: NO)
mysqladmin: CREATE DATABASE failed; error: 'Can't create database 'avantfax'; database exists'[/B][/I]
 
this part is about the mysql dabase creat in the  debian-install.sh: 
[B]

*# IMPORT MYSQL DATABASE*
*/etc/init.d/mysql start*
[I]echo "## Creating AvantFAX MySQL database ##"
mysql --user=root --password=$ROOTMYSQLPWD -e "GRANT ALL ON $DB.* TO [/I][EMAIL="$USER@localhost"]*$USER@localhost*[/EMAIL][I] IDENTIFIED BY \"$PASS\"" mysql
mysqladmin --default-character-set=utf8 --user=$USER --password=$PASS create $DB
mysql --user=$USER --password=$PASS $DB < create_tables.sql
mysqlshow --user=$USER --password=$PASS $DB[/I]
*# SYMLINK AVANTFAX SCRIPTS*
[I]ln -s $INSTDIR/includes/faxrcvd.php $SPOOL/bin/faxrcvd.php
ln -s $INSTDIR/includes/dynconf.php $SPOOL/bin/dynconf.php
ln -s $INSTDIR/includes/notify.php  $SPOOL/bin/notify.php[/I][/B]

---

### Post by netpro25 on 2010-01-31
The error:

```
Undefined index:  acc_enabled in /var/www/avantfax/includes/AFUserAccount.php on line 341
```

Is most likely because you have two users with the same name (admin) in your database as I did. Go into the avantFax database and under the useraccount table delete one of the users.

---

### Post by netpro25 on 2010-01-31
> **dehere said:**
> when i use the debian-install.sh to install avantax,it show me that :
 
***ERROR 1045 (28000): Access denied for user ***[EMAIL="'root'@'localhost'"]***'root'@'localhost'***[/EMAIL][I][B] (using password: NO)
mysqladmin: CREATE DATABASE failed; error: 'Can't create database 'avantfax'; database exists'[/B][/I]
 
this part is about the mysql dabase creat in the  debian-install.sh: 
[B]

*# IMPORT MYSQL DATABASE*
*/etc/init.d/mysql start*
[I]echo "## Creating AvantFAX MySQL database ##"
mysql --user=root --password=$ROOTMYSQLPWD -e "GRANT ALL ON $DB.* TO [/I][EMAIL="$USER@localhost"]*$USER@localhost*[/EMAIL][I] IDENTIFIED BY \"$PASS\"" mysql
mysqladmin --default-character-set=utf8 --user=$USER --password=$PASS create $DB
mysql --user=$USER --password=$PASS $DB < create_tables.sql
mysqlshow --user=$USER --password=$PASS $DB[/I]
*# SYMLINK AVANTFAX SCRIPTS*
[I]ln -s $INSTDIR/includes/faxrcvd.php $SPOOL/bin/faxrcvd.php
ln -s $INSTDIR/includes/dynconf.php $SPOOL/bin/dynconf.php
ln -s $INSTDIR/includes/notify.php  $SPOOL/bin/notify.php[/I][/B]


Just manually create the database as described in the install instructions.

```
# mysql -uroot -p < create_user.sql
# mysql -uavantfax -pd58fe49 avantfax < create_tables.sql
```

---

### Post by dehere on 2010-01-31
> **netpro25 said:**
> Just manually create the database as described in the install instructions.
 
```
# mysql -uroot -p < create_user.sql
# mysql -uavantfax -pd58fe49 avantfax < create_tables.sql
```
 
 
 
Thank you very much.
i manually create the database, the avantfax works although it can't connect to the Hylafax,the problems with mysql is sloved,i believe it's not far away from the success.
 
in the *avantfax-3.16.tgz* the file **"***prefs.txt***",**it has the statement as following,
***# if the MySQL password for root is set, specify it here***
***ROOTMYSQLPWD=***
when i fill in mysql password,i can setup the avantfax automatically with the ***debian-install.sh.***
 
[COLOR=red][SIZE=2]Thanks [/SIZE][SIZE=3][COLOR=#000000]**Coreigh **[SIZE=2]and[/SIZE] **netpro25** ![/COLOR][/SIZE][/COLOR]

---

### Post by wgomez_19 on 2010-03-11
> **netpro25 said:**
> The error:

```
Undefined index:  acc_enabled in /var/www/avantfax/includes/AFUserAccount.php on line 341
```Is most likely because you have two users with the same name (admin) in your database as I did. Go into the avantFax database and under the useraccount table delete one of the users.

Thnx i was lost with this error!

---

