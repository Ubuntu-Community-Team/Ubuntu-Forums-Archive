---
title: "apache issue with Virtual Hosts"
date: 2011-11-17
forum: Server Platforms
---

### Post by alain.roger on 2011-11-17
Hi,

this is the first time i try to setup virtual host on Ubuntu. Till now every time it was on Windows OS.

i searched over internet if something special needed to be done and i found the following tutorials [http://library.linode.com/lamp-guides/ubuntu-11.10-oneiric](http://library.linode.com/lamp-guides/ubuntu-11.10-oneiric)
and
[http://www.azsoftwaredownload.com/linux/installing-apache2-php5-and-mysql-support-ubuntu-1110](http://www.azsoftwaredownload.com/linux/installing-apache2-php5-and-mysql-support-ubuntu-1110)

therefore i decided to store my webpage under my user account as only this account is backuped till now.

thus my first virtual host is stored in
```
/home/alain/www/rogtek17
```now i created a file named rogtek17 which is saved in:
```
/etc/apache2/sites-available
```after using command ```
a2ensite rogtek17
``` and reloading/restarting apache i'm still not able to browse under FF [http://rogtek17.loc](http://rogtek17.loc)

where rogtek17.loc is my ServerName in the rogtek17 file.

basically here is my setting for virtual Host:
```
<VirtualHost *:80>
    ServerAdmin webmaster@localhost
    ServerName rogtek17.loc
    ServerAlias www.rogtek17.loc
    
    #AccessFileName ht.access

    DocumentRoot /home/alain/www/rogtek17
    <Directory />
        Options FollowSymLinks
        AllowOverride None
    </Directory>
    <Directory /home/alain/www/rogtek17>
        Options Indexes FollowSymLinks MultiViews
            AllowOverride AuthConfig FileInfo
        Order deny,allow
        Deny from all
    </Directory>

    ErrorLog /home/alain/www/rogtek17/logs/rogtek17.loc.error.log
    CustomLog /home/alain/www/rogtek17/logs/rogtek17.loc.access.log common

    # Possible values include: debug, info, notice, warn, error, crit,
    # alert, emerg.
    LogLevel warn

</VirtualHost>
```for now i just have a simple index.php file in this directory. However, it's like FF is not able to find the rogtek17.loc virtual host.

any dea from where could come the problem ?\thx.

A.

---

### Post by volkswagner on 2011-11-17
This is likely a lack of local DNS.  The system has no way of knowing what ip translates to your domain.

One step often not documented is the NameVirtual host directive.

Make sure you add
```
NameVirtualHost *:80
Listen 80

```

To /etc/apache2/ports.conf, and restart apache2.

You will then need local DNS such as BIND, or the simple approach is to use /etc/hosts file to map the ip to hostname.

Edit /etc/hosts and add

```
127.0.1.1	 rogtek17.loc www.rogtek17.loc
```

This would need to be added to any local client's "hosts" file on the LAN, that you want to have access to the virtual host.

---

### Post by alain.roger on 2011-11-17
thank a lot for your answer... i just forget to write in the /etc/hosts file :-( i'm so stupid sometimes :-)

---

