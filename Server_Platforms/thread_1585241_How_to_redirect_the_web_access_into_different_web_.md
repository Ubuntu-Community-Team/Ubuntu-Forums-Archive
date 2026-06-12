---
title: "How to redirect the web access into different web apps. location using apache httpd.c"
date: 2010-09-30
forum: Server Platforms
---

### Post by albertwt on 2010-09-30
Hi Everyone,

I got two web apps in my single linux box, they are Wiki and Mantis
the screenshot of the web apps directory shown below.

I have created the DNS CNAME record for this server which point to the main server SV6

service.domain.com --> SV6
rather than: [http://sv6/mantis/my_view_page.php](http://sv6/mantis/my_view_page.php)

wiki.domain.com --> SV6
rather than: [http://sv6/mediawiki/index.php/Main_Page](http://sv6/mediawiki/index.php/Main_Page)

```
<VirtualHost *:80>
    ServerAdmin sysadmin@domain.com
    DocumentRoot /usr/share/mantis/www
    ServerName service.domain.com
    ErrorLog logs/service.domain.com-error_log
    CustomLog logs/service.domain.com-access_log common
</VirtualHost>

<VirtualHost *:80>
    ServerAdmin sysadmin@domain.com
    DocumentRoot /var/lib/mediawiki
    ServerName wiki.domain.com
    ErrorLog logs/wiki.domain.com-error_log
    CustomLog logs/wiki.domain.com-access_log common
</VirtualHost>


root@sv6:/etc/apache2# apache2ctl start

root@sv6:/etc/apache2# apache2ctl status
w3m: Can't load http://localhost:80/server-status.

root@sv6:/etc/apache2# vi httpd.conf

root@sv6:/etc/apache2# apache2ctl restart
Warning: DocumentRoot [/var/www/html/] does not exist

root@sv6:/etc/apache2# apache2ctl configtest
Warning: DocumentRoot [/var/www/html/] does not exist
Syntax OK

root@sv6:/etc/apache2# apache2ctl status
w3m: Can't load http://localhost:80/server-status.

root@sv6:/etc/apache2#
```

here's the :/etc/apache2/httpd.conf file content

somehow i got error after i edit it and restart the Apache server.

can anyone help me please ?

Thanks,
Albert

---

### Post by ricerider1 on 2010-10-01
I found this page while working on my server. You can probably skip down to step 7 and go from there. However, in addition to making directories in the /var/www/ you will also need to modify the /etc/apache2/sites-available and /etc/apache2/sites-enabled files and the /etc/apache2/apache2.conf. The first is a link to mentioned page, the second is a link to Ubuntu server 10.04 guide.

[http://net.tutsplus.com/tutorials/php/how-to-setup-a-dedicated-web-server-for-free/](http://net.tutsplus.com/tutorials/php/how-to-setup-a-dedicated-web-server-for-free/)

[https://help.ubuntu.com/10.04/serverguide/C/index.html](https://help.ubuntu.com/10.04/serverguide/C/index.html)

   Hope it helps ya!:)

---

### Post by albertwt on 2010-10-21
Cool, thanks man for your help.

here it is the solution that is working for me finally.

> <VirtualHost *:80>
   ServerName wiki.domain.com
   DocumentRoot /var/lib/mediawiki
</VirtualHost>

<VirtualHost *:80>
   ServerName service.domain.com
   ServerAlias bugs.domain.com
   DocumentRoot /usr/share/mantis/www
</VirtualHost>

---

