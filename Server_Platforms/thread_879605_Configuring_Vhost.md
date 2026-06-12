---
title: "Configuring Vhost"
date: 2008-08-04
forum: Server Platforms
---

### Post by maidei on 2008-08-04
Trying to configure Vhost on Ubuntu Server 8.04 but not going well.
I can configure one site and everything work well,
as soon as I configure second site not able to access any site

using xxx.xx.4.10/firstsite
OR
xxx.xx.4.10/secondsite

Here are my configuration where should I change
(I have just change the first part and the rest left it as default)



sudo nano /etc/apache2/sites-available/default
NameVirtualHost *:80
<VirtualHost *:80>
        ServerAdmin webmaster@localhost

        DocumentRoot /var/www/firstsite
        ServerName [www.firstsite.com](www.firstsite.com)
        ServerAlias firstsite.com
      #Second site
</Virtualhost>
<VirtualHost *:80>
        DocumentRoot /var/www/secondsite
        ServerName [www.secondsite.com](www.secondsite.com)
        ServerAlias secondsite.com
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                            

***********
sudo nano /etc/apache2/sites-available/www.firstsite.com
NameVirtualHost *:80
<VirtualHost *:80>
        ServerAdmin webmaster@localhost

        DocumentRoot /var/www/firstsite
        ServerName [www.firstsite.com](www.firstsite.com)
        ServerAlias  firstsite.com

        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/>



                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>

**********
sudo nano /etc/apache2/sites-available/www.second.com
NameVirtualHost *:80
<VirtualHost *:80>
        ServerAdmin webmaster@localhost

        DocumentRoot /var/www/secondsite
        ServerName [www.secondsite.com](www.secondsite.com)
        ServerAlias secondsite.com
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>
****
/etc/apache2/sites-available# ls -l
total 12
-rw-r--r-- 1 root root 1236 2008-08-05 09:32 default
-rw-r--r-- 1 root root 1091 2008-08-05 09:28 [www.firstsite.com](www.firstsite.com)
-rw-r--r-- 1 root root 1080 2008-08-05 09:34 [www.secondsite.com](www.secondsite.com)


Reloading apache I got the following error


# sudo /etc/init.d/apache2 reload
 * Reloading web server config apache2
apache2: Could not reliably determine the server's fully qualified domain nam
using xxx.xxxx.xxx.10 for ServerName
[Tue Aug 05 09:57:01 2008] [warn] NameVirtualHost *:80 has no VirtualHosts
[Tue Aug 05 09:57:01 2008] [warn] NameVirtualHost *:80 has no VirtualHosts
[Tue Aug 05 09:57:01 2008] [warn] NameVirtualHost *:80 has no VirtualHosts

---

### Post by maidei on 2008-08-04
.

---

### Post by 3rods on 2008-08-04
While Apache is packaged with Ubuntu, these forums are probably not the best resource for Apache support.


Look here:
[http://httpd.apache.org/docs/2.0/vhosts/]("http://httpd.apache.org/docs/2.0/vhosts/")

And, name based hosts:
[http://httpd.apache.org/docs/2.0/vhosts/name-based.html]("http://httpd.apache.org/docs/2.0/vhosts/name-based.html")


And do this:
```
/usr/local/apache2/bin/httpd -S 
```

That will parse your config and help you find errors.

---

