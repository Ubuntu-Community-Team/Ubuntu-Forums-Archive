---
title: "Local Wordpress install"
date: 2009-12-16
forum: Server Platforms
---

### Post by Stoneface on 2009-12-16
I just created a wordpress installation in localhost/wordpress. I created a database wordpress and granted all priviliges on that database to myself:
```
mysql> create database wordpress
    -> ;
Query OK, 1 row affected (0.06 sec)

mysql> show databases;
+----------------------+
| Database             |
+----------------------+
| information_schema   | 
| mynewapp_development | 
| mysql                | 
| ruby                 | 
| wordpress            | 
+----------------------+
5 rows in set (0.05 sec)

mysql> GRANT ALL PRIVILEGES ON wordpress.* TO 'me'@'localhost' IDENTIFIED BY 'myapass';
Query OK, 0 rows affected (0.21 sec)

mysql> FLUSH PRIVILEGES;
Query OK, 0 rows affected (0.00 sec)

``` When I add wordpress as database, user myself and a password and localhost as host and press enter I get a white screen. I see not relevant apache errors that can help me. Any ideas how I can troubleshoot this issue?

---

### Post by Stoneface on 2009-12-16
I was looking for the php error log but could not find one. I changed php.ini ```
sudo gedit  /etc/php5/apache2/php.ini
```@  on line 395 ```
; Log errors to specified file.
error_log = /var/log/apache2/php.errors
``` to store PHP errors in a separate file. Then I created php.errors in /var/log/apache2/php.errors and made it CHMOD 777 and CHOWN root:admin . ```
me@ubuntu:/var/log/apache2$ ls -l
total 208
-rw-r----- 1 root adm    15099 2009-12-15 23:31 access.log
-rw-r----- 1 root adm   158396 2009-12-04 15:28 access.log.1
-rw-r----- 1 root adm      224 2009-11-10 19:57 access.log.2.gz
-rw-r----- 1 root adm      676 2009-12-15 23:22 error.log
-rw-r----- 1 root adm     1146 2009-12-15 11:18 error.log.1
-rw-r----- 1 root adm     1506 2009-12-07 19:26 error.log.2.gz
-rw-r----- 1 root adm      429 2009-11-21 14:18 error.log.3.gz
-rw-r----- 1 root adm      680 2009-12-15 11:18 other_vhosts_access.log
-rw-r----- 1 root adm      680 2009-12-07 19:26 other_vhosts_access.log.1
-rw-r--r-- 1 root root     179 2009-12-05 01:31 other_vhosts_access.log.2.gz
-rwxrwxrwx 1 root admin      0 2009-12-15 23:16 php.errors

```But it does not seem to register errors when I get the white screen while trying to install Wordpresss

When I created wp-config manually and restarted the installation at localhost/wordpress I got this error: ```
Fatal error: Call to undefined function wp() in /var/www/wordpress/wp-blog-header.php on line 14
```

---

### Post by Stoneface on 2009-12-16
Well making all files 777 - as it is a local test server - did not help a bit. Still no php errors logged and still a white screen of death. Any help would be appreciated :-(

---

### Post by Stoneface on 2009-12-16
Found the issue already. Forgot to install the php5-mysql module: ```
 sudo apt-get install php5-mysql
``` . I realized this after reading [http://www.cyberciti.biz/faq/install-mysql-php-support-for-wordpress/](http://www.cyberciti.biz/faq/install-mysql-php-support-for-wordpress/)

---

