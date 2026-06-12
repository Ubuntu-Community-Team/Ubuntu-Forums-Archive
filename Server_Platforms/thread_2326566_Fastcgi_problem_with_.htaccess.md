---
title: "Fastcgi problem with .htaccess"
date: 2016-06-02
forum: Server Platforms
---

### Post by Rakesh_vijayan on 2016-06-02
Hi 


I have setup apache2 server with FASTCGI , By following the instruction but not worker mod 

[http://askubuntu.com/questions/378734/how-to-configure-apache-to-run-php-as-fastcgi-on-ubuntu-12-04-via-terminal](http://askubuntu.com/questions/378734/how-to-configure-apache-to-run-php-as-fastcgi-on-ubuntu-12-04-via-terminal)

after the installation I check the configuration with the following command and result seem  ok 

```
sudo apache2ctl configtest
```

My Website uses .htaccess files for site working .if the .htaccess comes up this conf , is it will cause any of the issue for smooth functioning  .and I am not using Virtual Hosting 

My Document root is /var/www/html 

Is the same way to enable .htaccess option in apache2.conf ?
```
<Directory /var/www/>
        Options Indexes FollowSymLinks
        AllowOverride All
        Require all granted
</Directory>
```
And for performance tuning I adjust the value in event mode 

```
sudo nano /etc/apache2/mods-available/mpm_event.conf
```

```
<IfModule mpm_event_module>

Timeout 300 

StartServers 2

ThreadLimit 64

ThreadsPerChild 64

MaxConnectionsPerChild 10000
 
MinSpareThreads 20

MaxSpareThreads 85

ServerLimit 8
MaxRequestWorkers 512 # AKA MaxClients
 
KeepAlive On
MaxKeepAliveRequests 50
KeepAliveTimeout 4

</IfModule>
```

Is this configuration is fine ?  I am going to move the DATA content to /var/www/html/ / Please Advice me with your comments 

Thanks

---

### Post by howefield on 2016-06-02
Thread moved to the "*Server Platforms*" forum, probably a better fit.

---

