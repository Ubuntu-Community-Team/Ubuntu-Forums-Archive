---
title: "Tutorial for asterisk + freepbx on ubuntu no hacking!!"
date: 2011-05-08
forum: Server Platforms
---

### Post by elico on 2011-05-08
(EDIT: i got it to work and then after a while i got a bug cause of a problematic module of freepbx, i will work on something more perfect).

if you will search ubuntu forums you will find only 10 results for freepbx.
there are couple of issues related to installing freepbx on ubuntu apache server.
(the most recent info you should know about freepbx on ubuntu else then mine
[https://wiki.ubuntu.com/AsteriskOnUbuntu/Current](https://wiki.ubuntu.com/AsteriskOnUbuntu/Current)
)
so in the tutorials and readme files of freepbx it's a must for freepbx to run apache as the user and group: asterisk.
but the problem is that all ubuntu apache servers comes with a default www-data user as the OS user of apache.
you can change apache to run as asterisk and adding the www-data user to the asterisk group but it will make for many websites and server admins a security issue.
installing asterisk on ubuntu is simple but running freepbs will be a pain in the ***.
there was one guy that made some "hacking" in freepbs to make it work.
so these hackes are not needed but just to know apache capabilities in a basic level.

the steps for installation are:
```
apt-get update
apt-get install mysql-server asterisk-mp3 asterisk-mysql asterisk-ooh323c asterisk-sounds-extra op-panel asterisk asterisk-config asterisk-h323 asterisk-sounds-main apache2 php5 php5-curl php5-cli php5-mysql php-pear php-db php5-gd php5-suhosin curl openssh-server gastman sox 
```edit /etc/php5/apache2/php.ini
and make sure the next settings are applied:
```

max_execution_time = 30
memory_limit = 100M
error_reporting = E_COMPILE_ERROR|E_RECOVERABLE_ERROR|E_ERROR|E_CORE_ERROR
display_errors = Off
log_errors = On
error_log = /var/log/php.log
register_globals = Off
;PHP's built-in default is text/html
default_mimetype = "text/html"
;default_charset = "ISO-8859-1"
default_charset = "utf8";
magic_quotes_gpc = Off
``````
 sudo a2enmod php5
```download the latest freepbx tar into the /var/www/freepbx (or whatever your webserver dir is)
```
cd /var/www
wget [http://mirror.freepbx.org/freepbx-2.8.1.tar.gz](http://mirror.freepbx.org/freepbx-2.8.1.tar.gz)
tar -xvf freepbx-2.8.1.tar.gz
mv freepbx-2.8.1 freepbx
cd freepbx
chown -R asterisk:asterisk
```#to make only freepbx use asterisk user and the whole server will stay using www-data
#we are making a rule in the .htaccess file.
#for it to work you must allow the usage of htaccess and the mod_env apache module
#[https://help.ubuntu.com/community/EnablingUseOfApacheHtaccessFiles](https://help.ubuntu.com/community/EnablingUseOfApacheHtaccessFiles)
#or just add to your site dir config "AllowOverride All"\ change from "AllowOverride None"
echo "SetEnv APACHE_RUN_USER asterisk"> .htaccess
echo "SetEnv APACHE_RUN_GROUP asterisk">> .htaccess

now we will create the databases:
```
mysql -p
create database asterisk;
create database asteriskcdrdb;
GRANT ALL PRIVILEGES ON asteriskcdrdb.* TO asterisk@localhost IDENTIFIED BY 'CHANGEME';
GRANT ALL PRIVILEGES ON asterisk.* TO asterisk@localhost IDENTIFIED BY 'CHANGEME';
GRANT ALL PRIVILEGES ON asteriskcdrdb.* TO asterisk@127.0.0.1 IDENTIFIED BY 'CHANGEME';
GRANT ALL PRIVILEGES ON asterisk.* TO asterisk@127.0.0.1 IDENTIFIED BY 'CHANGEME';
flush privileges;
exit
```#to populate the databases for freepbx
```
mysql -p asterisk < SQL/newinstall.sql
mysql -p asteriskcdrdb< SQL/cdr_mysql_table.sql
```#and install freepbx (CHANGEME is the passoword from before)
```
 sudo ./install_amp --username=asterisk --password=CHANGEME
``````
 /etc/init.d/apache2 restart
```#and after you will set the admin user of freepbx password
```
 change in the /etc/amportal.conf file
```the option
```
 AUTHTYPE
```from
```
 AUTHTYPE=none
```to
```
 AUTHTYPE=database
```and clear you web browser cookies to make sure it is working.

works for me
a great asterisk local PBX with SIP trunks (no DAHDI or complicated stuff as ISDN and PRI)

---

