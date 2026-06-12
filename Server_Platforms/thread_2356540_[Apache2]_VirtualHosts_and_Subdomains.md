---
title: "[Apache2] VirtualHosts and Subdomains"
date: 2017-03-24
forum: Server Platforms
---

### Post by kkosyfarinis on 2017-03-24
Good day to you all!
I am running a home server with access to the root account. I have made a VirtualHost to access a Subdomain of my Domain, (cp.example.com) but it does not seem to be working. I am currently using CloudFlare to speed up my website too. 

VirtualHost File: 
```

<VirtualHost *:*>
    ServerAdmin webmaster@localhost
    DocumentRoot /var/www/mccp
    ServerAlias   *.cp.example.com
    ServerName cp.example.com


    <Directory /var/www/mccp>
        Options Indexes FollowSymLinks MultiViews
        AllowOverride all
        Order allow,deny
        allow from all
        Require all granted
    </Directory>


#    ErrorLog ${APACHELOGDIR}/error.log
#   CustomLog ${APACHELOGDIR}/error.log/access.log combined


</VirtualHost>

```
I have tried, instead of VirtualHost *:*, _default_:80, *:80 and a few other different combinations, but nothing seems to be working. Any clues as to what I haven't done correctly? Permissions Shouldn't be incorrect since I've done 
```

chown -R (myusername):www-data /var/www/mccp/
chmod -R g+s /var/www/mccp/

```
As well as I have enabled the site using
```

a2ensite cp.example.com

```


Also, how would this VirtualHost config file (or one that works) would look like if I wanted to add SSL support to it? My default domain name does support SSL and I do have a Wildcard SSL Certificate, but some examples that I've used from the interent for a virtual host
with SSL did not seem to work for some reason.

---

### Post by howefield on 2017-03-24
Thread moved to the "*Server Platforms*" forum for a better fit.

---

### Post by monster-it on 2017-03-24
so a conf file i'm using which is working fine is 
```
<VirtualHost *:80>
ServerAdmin [email]admin@yourdomain.com[/email]
DocumentRoot /var/www/html/yetiforce/
ServerName your-domain.com
ServerAlias [www.your-domain.com](www.your-domain.com)
<Directory /var/www/html/yetiforce/>
Options FollowSymLinks
AllowOverride All
Order allow,deny
allow from all
</Directory>
ErrorLog /var/log/apache2/your-domain.com-error_log
CustomLog /var/log/apache2/your-domain.com-access_log common
</VirtualHost>
```

```
sudo a2enmod rewrite
sudo touch /etc/apache2/sites-available/yetiforce.conf
sudo ln -s /etc/apache2/sites-available/yetiforce.conf /etc/apache2/sites-enabled/yetiforce.conf
sudo nano /etc/apache2/sites-available/yetiforce.confe 
```

Give that a trythat a try and enable the file after by using touch for instance.

---

### Post by kkosyfarinis on 2017-03-24
It's still the same, error 522 after 15 seconds as seen at [http://cp.livemc.eu/](http://cp.livemc.eu/)

---

