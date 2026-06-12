---
title: "Forbidden error with new apache2 install"
date: 2016-03-24
forum: Server Platforms
---

### Post by jdogzilla2 on 2016-03-24
Hi all, I have a brand new install of Xubuntu 15.10 desktop.  Installed apache2, php5 and phpmyadmin from apt-get.  Created a simple phpinfo.php file in /var/www/html as guided.  However, with both [http://localhost/phpmyadmin.php](http://localhost/phpmyadmin.php) and [http://localhost/phpmyadmin](http://localhost/phpmyadmin), I get a "403 Forbidden" error and nothing else.  So for someone who has newly installed this setup, where should I look for potential issues?  I didn't even see anything in the log files for apache2 in /var/log/apaches ... and tried a bunch of other options upon searching, but nothing seems to work.  Any help will be appreciated.

---

### Post by Doug S on 2016-03-25
For  [http://localhost/index.html](http://localhost/index.html) do you get the default apache web page? If yes, provide the output for "ls -l /var/www/html"

---

### Post by jdogzilla2 on 2016-03-26
Hi Doug, thanks for your reply.  Here is the output you requested.  Also nothing seems to be coming in the log files in /var/log/apache2 either ... 

user@HP-ENVY-6-Notebook:/var/www/html$ ll
total 28
drwxr-xr-x 2 www-data www-data  4096 Mar 23 22:06 ./
drwxr-sr-x 3 root     root      4096 Mar 23 22:55 ../
lrwxrwxrwx 1 www-data www-data    27 Mar 23 21:36 bandwidthd -> /var/lib/bandwidthd/htdocs//
-rwxr--r-- 1 www-data www-data 11321 Mar 23 10:53 index.html*
-rwxr--r-- 1 www-data www-data  3356 Mar 11 14:14 index.lighttpd.html*
-rwxr-xr-x 1 www-data www-data    20 Mar 23 21:43 phpinfo.php*
lrwxrwxrwx 1 www-data www-data    22 Mar 23 21:50 phpmyadmin -> /usr/share/phpmyadmin//
lrwxrwxrwx 1 www-data www-data    21 Mar 23 22:06 wordpress -> /usr/share/wordpress//
user@HP-ENVY-6-Notebook:/var/www/html$ 

Any help will be appreciated.

---

### Post by jdogzilla2 on 2016-03-26
And sorry, yes I can reach the default index.html page through [http://localhost](http://localhost) or [http://localhost/index.html](http://localhost/index.html)

---

### Post by Doug S on 2016-03-26
Well, it is not clear to me what is wrong. Try turning up the LogLevel. Edit /etc/apache2/apache2.conf and change this area:
```
#
# LogLevel: Control the severity of messages logged to the error_log.
# Available values: trace8, ..., trace1, debug, info, notice, warn,
# error, crit, alert, emerg.
# It is also possible to configure the log level for particular modules, e.g.
# "LogLevel info ssl:warn"
#
LogLevel warn

```Perhaps to debug or even higher. Then see if that provides more insight.
Note: you need to edit as sudo, and be sure to re-start apache or re-boot after the edit. Perhaps save an original copy of your apache2.conf file first.

---

### Post by nerdtron on 2016-03-26
Permission errors could mean the permissions on the Links you have:
```
lrwxrwxrwx 1 www-data www-data    22 Mar 23 21:50 phpmyadmin -> /usr/share/phpmyadmin//
lrwxrwxrwx 1 www-data www-data    21 Mar 23 22:06 wordpress -> /usr/share/wordpress// 
```

Are you sure the permissions of the folder are 755 and files 644?
Di you enabled the Options FollowSymlinks on your apachec config?

---

### Post by jdogzilla2 on 2016-03-27
Did as suggested ... make log level warn (and tried with info), but this is what my log looks like ...

user@HP-ENVY-6-Notebook:/var/log/apache2$ ll
total 8
drwxr-x---  2 root adm    4096 Mar 23 21:16 ./
drwxrwxr-x 20 root syslog 4096 Mar 27 18:55 ../
-rw-r-----  1 root adm       0 Mar 23 21:16 access.log
-rw-r-----  1 root adm       0 Mar 23 21:16 error.log
-rw-r-----  1 root adm       0 Mar 23 21:16 other_vhosts_access.log

So nothing being written to error.log or access.log

Also, apache2.conf file has the following:
<Directory />
        Options FollowSymLinks
        AllowOverride None
        Require all denied
</Directory>


<Directory /usr/share>
        AllowOverride None
        Require all granted
</Directory>


<Directory /var/www/html>
        Options Indexes FollowSymLinks
        AllowOverride All
        Require all granted
</Directory>

AccessFileName .htaccess

# Include generic snippets of statements
IncludeOptional conf-enabled/*.conf


# Include the virtual host configurations:
IncludeOptional sites-enabled/*.conf

---

### Post by jdogzilla2 on 2016-03-28
Found the problem ... had lighttpd also installed and running which was conflicting with apache.  As soon as I uninstalled it, everything started working.  Thanks for your help.

---

