---
title: "i get a 403 after trying to split ubuntu server via apache"
date: 2016-09-01
forum: Server Platforms
---

### Post by micahpage on 2016-09-01
I have an ubuntu server setup...but i want to add a second website.  The main website is python-gaming.com and the second domain is metulburr.com I would like to split off metulburr.com to a different directory than the original. How can i accomplish this?

I have .conf files for both sites

```
metulburr /etc/apache2/sites-available $ ls000-default.conf  default-ssl.conf  domain1.com.conf  metulburr.com.conf  python-gaming.com.conf



```

with the second conf as 

```
metulburr /etc/apache2/sites-available $ cat metulburr.com.conf <VirtualHost *:80>
    ServerAlias www.metulburr.com
    ServerAdmin webmaster@localhost
    DocumentRoot /var/www/metulburr.com
    ServerName metulburr.com
    <Directory /var/www/metulburr.com>
        Order allow,deny
        Allow from all
    </Directory>


    
        # The ServerName directive sets the request scheme, hostname and port that
        # the server uses to identify itself. This is used when creating
        # redirection URLs. In the context of virtual hosts, the ServerName
        # specifies what hostname must appear in the request's Host: header to
        # match this virtual host. For th`e default virtual host (this file) this
        # value is not decisive as it is used as a last resort host regardless.
        # However, you must set it for any further virtual host explicitly.
        #ServerName www.example.com




        # Available loglevels: trace8, ..., trace1, debug, info, notice, warn,
        # error, crit, alert, emerg.
        # It is also possible to configure the loglevel for particular
        # modules, e.g.
        #LogLevel info ssl:warn


        ErrorLog ${APACHE_LOG_DIR}/error.log
        CustomLog ${APACHE_LOG_DIR}/access.log combined


        # For most configuration files from conf-available/, which are
        # enabled or disabled at a global level, it is possible to
        # include a line for only one particular virtual host. For example the
        # following line enables the CGI configuration for this host only
        # after it has been globally disabled with "a2disconf".
        #Include conf-available/serve-cgi-bin.conf
</VirtualHost>



```

before this both domains pointed to where python-gaming.com does now. But after running

```
metulburr /etc/apache2/sites-available $ sudo a2ensite metulburr.com.conf Enabling site metulburr.com.
To activate the new configuration, you need to run:
  service apache2 reload
metulburr /etc/apache2/sites-available $ sudo service apache2 reload
 * Reloading web server apache2
 * 



```

I get a 403 on the second domain to the document root which is /var/www/metulburr.com, but i dont know why because that directory has read and execute permissions

```
metulburr /var/www $ ls -ltotal 192
drwxr-xr-x 23 root root 180224 Oct 13  2015 Dump
drwxr-xr-x  6 root root   4096 Oct 26  2015 ftp
drwxr-xr-x 11 root root   4096 Mar 15 10:01 html
drwxr-xr-x  2 root root   4096 Feb  4  2016 metulburr.com



```

---

### Post by slickymaster on 2016-09-01
*Thread moved to **Server Platforms**.*

---

### Post by Graham_Willis on 2016-09-02
I can see that the site metulburr.com is already up and running. Can you share with us what the problem was (my guess would be that it was about owner and group owner of the metulburr.com directory)?

---

