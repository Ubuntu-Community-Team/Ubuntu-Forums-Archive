---
title: "apache.conf"
date: 2014-07-16
forum: Server Platforms
---

### Post by edison2 on 2014-07-16
Hello, I'm relatively new to this but I have a question about how this works. Normally I understand that the apache2.conf is under /etc/apache2/. However, I installed BackupPC on the server and I can access the service through [http://server/backuppc](http://server/backuppc). I then expected there to be a backuppc folder under /var/www/. That folder was empty except for the default index.html. 

Digging further, I found an apache.conf file under /etc/backuppc that defined the alias for /backup. So my question is how does apache know about this apache.conf file located under /etc/backuppc?

The server itself is fine so I'm just looking to understand how this all works.

Thanks.

---

### Post by capscrew on 2014-07-16
> **edison2 said:**
> Hello, I'm relatively new to this but I have a question about how this works. Normally I understand that the apache2.conf is under /etc/apache2/. However, I installed BackupPC on the server and I can access the service through [http://server/backuppc](http://server/backuppc). I then expected there to be a backuppc folder under /var/www/. That folder was empty except for the default index.html. 

Digging further, I found an apache.conf file under /etc/backuppc that defined the alias for /backup. So my question is how does apache know about this apache.conf file located under /etc/backuppc?

The server itself is fine so I'm just looking to understand how this all works.

Thanks.

It's pretty messy but you can start your education [http://httpd.apache.org/docs/current/sections.html]("http://httpd.apache.org/docs/current/sections.html")here.

---

### Post by cj13579 on 2014-07-31
It is confusing. You will probably find a symbolic link under /etc/apache2/conf.d to the file you referenced. When you start apache it sources all of the files specified in that directory. Other programs like phpmyadmin use this configuration as well.

---

