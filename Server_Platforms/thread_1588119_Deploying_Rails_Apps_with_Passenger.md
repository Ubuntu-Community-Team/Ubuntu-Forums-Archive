---
title: "Deploying Rails Apps with Passenger"
date: 2010-10-04
forum: Server Platforms
---

### Post by verymagicalguy on 2010-10-04
I'm trying to deploy a rails app using passenger, however I'm getting an Error 101. Apache is running fine (I think), I have a site deployed on a different port that works fine. I'd like to know how to debug my problem as I have little experience regarding configuring apache. Also, any other advice regarding deploying rails apps is appreciated, maybe there's an easier way I don't know about.

Installation was as follows. Fresh Ubuntu Server 10.04.1 install. Ruby was installed via RVM and rails and sqlite3 were installed using gems. I installed passenger via 'passenger-install-apache2-module' and followed their instructions on configuring the module. 

In /etc/apache2/mods-available/passenger.conf I have:
```
assengerRoot /usr/local/rvm/gems/ruby-1.9.2-p0/gems/passenger-2.2.15
PassengerRuby /usr/local/rvm/rubies/ruby-1.9.2-p0/bin/ruby

```
In /etc/apache2/mods-available/passenger.load I have:
```
LoadModule passenger_module /usr/local/rvm/gems/ruby-1.9.2-p0/gems/passenger-2. 2.15/ext/apache2/mod_passenger.so

```
In /etc/apache2/sites-available/default I have:
```
<VirtualHost *:80>
    ServerName www.myservername.com
    DocumentRoot /var/www/myapp/public
    <Directory /var/www/myapp/public>
        AllowOverride all
        Options -MultiViews
    </Directory>
</VirtualHost>

<VirtualHost *:5000>
    DocumentRoot /var/www/tester
</VirtualHost>
```

Thanks for the help!

---

