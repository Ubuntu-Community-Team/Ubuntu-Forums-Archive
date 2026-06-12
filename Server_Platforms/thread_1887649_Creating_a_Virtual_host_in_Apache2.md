---
title: "Creating a Virtual host in Apache2"
date: 2011-11-27
forum: Server Platforms
---

### Post by Koffers on 2011-11-27
Hello, 

I'm trying to create a virtual host on my Ubuntu server so that I can host two different sites.


The first is called metrocrush.es and the second is metrocrushbrasil.com. 

I have inserted the following into the /etc/apache2/apache2.conf file and /etc/apache2/httpd.conf as well:

# Include the virtual host configurations:
Include /etc/apache2/sites-enabled/
<VirtualHost *:80>
DocumentRoot "/var/www/metrocrush.es/wordpress"
ServerName metrocrush.es
<Directory "/var/www/metrocrush.es/wordpress">
allow from all
Options +Indexes
</Directory>
</VirtualHost>

#Include the virtual host configurations
Include /etc/apache2/sites-enabled/
<VirtualHost *:80>
DocumentRoot "/var/www/metrocrushbrasil.com/wordpress"
ServerName metrocrushbrasil.com
<Directory "/var/www/metrocrushbrasil.com/wordpress">
allow from all
Options +Indexes
</Directory>
</VirtualHost>

I have also created two files in /etc/apache2/sites-available named metrocrush_es and metrocrushbrasil respectively that contain this:


<VirtualHost>
ServerAdmin webmaster@localhost
ServerName MetroCrush.es
 
        DocumentRoot /var/www/metrocrush.es/wordpress
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/metrocrush.es/wordpress>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>
 
        ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
        <Directory "/usr/lib/cgi-bin">
                AllowOverride None
                Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
                Order allow,deny
                Allow from all
        </Directory>
 
        ErrorLog /var/log/apache2/error.log
 
        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn
 
        CustomLog /var/log/apache2/access.log combined
 
    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>

The DNS for both domains are configured correctly. Currently, however only metrocrush.es is working. Metrocrushbrasil.com returns a Server 500 error. 

Can someone point me in the right direction as to where I'm going wrong? 

Apologies if I have not found the correct forum for this topic.

Many thanks in advance,
Andy

---

### Post by artjomtro on 2011-11-27
undo all your steps!

this guide will help you!

1) create metrocrush.es in folder  sites-available
```
cd /etc/apache2/sites-available/
sudo nano metrocrush.es
```2) write to file this
```
<VirtualHost *:80>
    ServerAdmin webmaster@localhost
    ServerName metrocrush.es
    DocumentRoot /var/www/metrocrush.es
    <Directory />
        Options FollowSymLinks 
        AllowOverride None
        Order deny,allow
        Deny from all
    </Directory>
    <Directory /var/www/metrocrush.es>
        Options Indexes FollowSymLinks -MultiViews
        AllowOverride all
        Order deny,allow
        allow from all
    </Directory>

    ErrorLog /var/log/apache2/metrocrush.es-error.log
    LogLevel warn
    CustomLog /var/log/apache2/metrocrush.es-access.log combined  
```3) create folder 
```
cd /var/www/
sudo mkdir metrocrush.es
```4)create wordpress.metrocrush.es in folder  sites-available
```
cd /ets/apache2/sites-available/
sudo nano wordpress.metrocrush.es
```5) write to file this
```
<VirtualHost *:80>
    ServerAdmin webmaster@localhost
    ServerName wordpress.metrocrush.es
    DocumentRoot /var/www/wordpress.metrocrush.es
    <Directory />
        Options FollowSymLinks 
        AllowOverride None
        Order deny,allow
        Deny from all
    </Directory>
    <Directory /var/www/wordpress.metrocrush.es>
        Options Indexes FollowSymLinks -MultiViews
        AllowOverride all
        Order deny,allow
        allow from all
    </Directory>

    ErrorLog /var/log/apache2/wordpress.metrocrush.es-error.log
    LogLevel warn
    CustomLog /var/log/apache2/wordpress.metrocrush.es-access.log combined  
```6) create folder wordpress.metrocrush.es
```
cd /var/www/
sudo mkdir wordpress.metrocrush.es
```7) enable sites
```
sudo a2ensite metrocrush.es
``````
sudo a2ensite wordpress.metrocrush.es
```8) disable default

```
sudo a2dissite default
```9) restart apache 
```
sudo /etc/init.d/apache2 restart
```or 
```
sudo /etc/init.d/apache2 reload
``` it's all
if you need sometfing like metrocrush.es/wordpress
undo all your steps!
just ignore my post and create folder in /var/www/ 
```
sudo mkdir wordpress
```

---

### Post by dmattox10 on 2011-11-27
When I have difficulty with server tasks, I use webmin, and it's built in dialogs for apache...

---

### Post by artjomtro on 2011-11-28
don't use webmin he downgrade your security!

---

