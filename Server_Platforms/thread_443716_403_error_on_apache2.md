---
title: "403 error on apache2"
date: 2007-05-14
forum: Server Platforms
---

### Post by saphil on 2007-05-14
I have set up a webserver with one quirk.
the /var/www directory is linked to  /media/sdb1/wwwroot 
The idea was to use the larger additional drive to host the multitudes of sites I imagine I will have there.  accessing the [http://localhost](http://localhost) or [http://[ip](http://[ip) address] brings a 403 error

the link /var/www mode is 777
the mode of /media/sdb1/wwwroot is 744
Owner on both is root

---

### Post by JamieC on 2007-05-14
Edit your apache2.conf file:-

Find:
```

DocumentRoot /var/www

```

Add below:
```


<Directory "/var/www">
    Options FollowSymLinks
    AllowOverride None
    Order allow,deny
    Allow from all
</Directory>

```

Restart apache:
```

/etc/init.d apache2 restart

```

What is the result now?

---

### Post by saphil on 2007-05-14
There was nothing like this suggested code in apache2.conf 
and nothing at all in the httpd.conf.  It made immediate sense to me, though 

```
 * Forcing reload of apache 2.0 web server... 
[Mon May 14 20:12:52 2007] [warn] NameVirtualHost *:0 has no VirtualHosts
[Mon May 14 20:12:53 2007] [warn] NameVirtualHost *:0 has no VirtualHosts

```Still 403 error
> **Forbidden**

 You don't have permission to access / on this server.
 Additionally, a 403 Forbidden error was encountered while trying to use an ErrorDocument to handle the request.
  Apache/2.0.55 (Ubuntu) PHP/5.1.2 mod_ssl/2.0.55 OpenSSL/0.9.8a Server at 72.16.181.39 Port 80

```
/etc/apache2/sites-available:
default  netd1

/etc/apache2/sites-enabled:
000-default  netd1

```Inside the default site...
```
NameVirtualHost *
<VirtualHost *>
        ServerAdmin webmaster@localhost

        DocumentRoot /var/www
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
                # Uncomment this directive is you want to see apache2's
                # default start page (in /apache2-default) when you go to /
                #RedirectMatch ^/$ /apache2-default/
        </Directory>

        ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
        <Directory "/usr/lib/cgi-bin">
                AllowOverride None
                Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
"/etc/apache2/sites-available/default" 46L,
```I remember the apache1.x had a line about virtual sites that said something about VirtualHost *:80  but I don't find anything like it in the apache2.conf file.

Do you think I would be better off starting from scratch, getting a server iso and letting it set up LAMP for me?  The next project is adding tomcat.  :-)

---

