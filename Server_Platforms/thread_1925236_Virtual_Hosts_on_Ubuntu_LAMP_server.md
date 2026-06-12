---
title: "Virtual Hosts on Ubuntu LAMP server"
date: 2012-02-14
forum: Server Platforms
---

### Post by Laage on 2012-02-14
Hey,

I'm working on a Ubuntu server 11.10 64-bit web-server. 

I'm trying to get Virtual Hosts running on Apache2/PHP/MySQL. I've got the primary site (Drupal) running as the default site and everything works as it should.

Say we have the following domains mydomain.com and md.com and I want to set up the server as follows.
[http://www.mydomain.com;](http://www.mydomain.com;) [http://www.md.com;](http://www.md.com;) [http://mydomain.com](http://mydomain.com) and [http://md.com](http://md.com) should point to the primary drupal site.
[http://blog.mydomain.com](http://blog.mydomain.com) and [http://blog.md.com](http://blog.md.com) should point to a virtual site running WordPress.

As far as I can tell I should do the following:
Change the /etc/hosts file to so the various domains are pointed to the local server ie:
```
127.0.0.1    [www.mydomain.com]("http://www.mydomain.com/")
127.0.0.1    blog.mydomain.com 
```Run the following command:
```
sudo a2enmod vhost_alias 
```and then restart apache

Copy the "default" file in the /etc/apache2/sites-available directory to a new blog.mydomain.com file and edit it to look somewhat like this:
```
   1 <VirtualHost *:80>
   2         ServerAdmin webmaster@localhost
   3
   4         ServerName blog.mydomain.com.local
   5         DocumentRoot /var/www/blog.mydomain.com
   6         <Directory />
   7                 Options FollowSymLinks
   8                 AllowOverride None
   9         </Directory>
  10         <Directory /var/www/blog.mydomain.com/>
  11                 Options Indexes FollowSymLinks MultiViews
  12                 AllowOverride None
  13                 Order allow,deny
  14                 allow from all
  15         </Directory>
  16
  17         ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
  18         <Directory "/usr/lib/cgi-bin">
  19                 AllowOverride None
  20                 Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
  21                 Order allow,deny
  22                 Allow from all
  23         </Directory>
  24
  25         ErrorLog ${APACHE_LOG_DIR}/error.log
  26
  27         # Possible values include: debug, info, notice, warn, error, crit,
  28         # alert, emerg.
  29         LogLevel warn
  30
  31         CustomLog ${APACHE_LOG_DIR}/access.log combined
  32
  33     Alias /doc/ "/usr/share/doc/"
  34     <Directory "/usr/share/doc/">
  35         Options Indexes MultiViews FollowSymLinks
  36         AllowOverride None
  37         Order deny,allow
  38         Deny from all
  39         Allow from 127.0.0.0/255.0.0.0 ::1/128
  40     </Directory>
  41
  42 </VirtualHost>
```  run this command:
 ```
 sudo a2ensite our-test-site
```  and restart apache again
  
  I've been doing this and trying to access my blog.mydomain.com domain from a client with an edited hosts file pointing both [www.mydomain.com]("http://www.mydomain.com") and blog.mydomain.com to the IP of the server, but I still only see the default drupal site when I try to surf to [http://blog.mydomain.com](http://blog.mydomain.com)

/Laage

---

### Post by perspectoff on 2012-02-14
You might find some useful tips at Ubuntuguide:

[http://ubuntuguide.org/wiki/Dynamic_IP_servers#Multiple_domain_name_URLs.2C_single_Dynamic_URL](http://ubuntuguide.org/wiki/Dynamic_IP_servers#Multiple_domain_name_URLs.2C_single_Dynamic_URL)

---

### Post by tamkt on 2012-02-14
You can use webmin to create virtualhost

---

### Post by Laage on 2012-02-16
Hi and thank you for your tips. However the only thing I could see that I had missed in the Ubuntu-guide was the ServerAlias directive which would allow me to add different domain-names to the same virtual host. And it did not solve the problem with all requests being routed to the default host.

I also tried installing Webmin, but as far as I can tell from the interface the virtual hosts (default and blog.mydomain.com) are defined and running, so I'm not sure what else may be wrong here.

/Laage

---

