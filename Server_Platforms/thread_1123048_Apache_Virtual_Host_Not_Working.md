---
title: "Apache Virtual Host Not Working"
date: 2009-04-11
forum: Server Platforms
---

### Post by Black Mage on 2009-04-11
I am using Ubuntu 8.10 and I cannot get my virtual host to work. It work on my previous web server which ran Ubuntu 7.04. The problem is every url that comes in goes to the same site. The following is from my /etc/apache2/sites-avaible and I do have a symlink in sites-enabled. 

<VirtualHost *>
ServerAdmin webmaster@localhost
ServerName [www.prTrack.net](www.prTrack.net)
DocumentRoot /var/www/prTrack
<Directory />
Options FollowSymLinks
AllowOverride None
</Directory>
<Directory /var/www/prTrack>
Options Indexes FollowSymLinks MultiViews
AllowOverride None
Order allow,deny
allow from all
# This directive allows us to have apache2's default start page
# in /apache2-default/, but still have / go to the right place
#RedirectMatch ^/$ /apache2-default/
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
ServerSignature On

Alias /doc/ "/usr/share/doc/"
<Directory "/usr/share/doc/">
Options Indexes MultiViews FollowSymLinks
AllowOverride None
Order deny,allow
Deny from all
Allow from 127.0.0.0/255.0.0.0 ::1/128
</Directory>

</VirtualHost>


And

<VirtualHost *>

ServerAdmin webmaster@localhost
ServerName scribeshare.net
ServerAlias [www.scribeshare.net](www.scribeshare.net)
DocumentRoot /var/www/scribeshare
<Directory />
Options FollowSymLinks
AllowOverride None
</Directory>
<Directory /var/www/scribeshare>
Options Indexes FollowSymLinks MultiViews
AllowOverride None
Order allow,deny
allow from all
# This directive allows us to have apache2's default start page
# in /apache2-default/, but still have / go to the right place
#RedirectMatch ^/$ /apache2-default/
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
ServerSignature On

Alias /doc/ "/usr/share/doc/"
<Directory "/usr/share/doc/">
Options Indexes MultiViews FollowSymLinks
AllowOverride None
Order deny,allow
Deny from all
Allow from 127.0.0.0/255.0.0.0 ::1/128
</Directory>

</VirtualHost>



Does anyone have an idea of what is wrong with this?

---

### Post by skunkbad on 2009-04-12
Sorry, I'm not at my main computer,  but I know there is more to setting up virtual hosts than just sites-available, and sites-enabled. You might look at Ubuntu's guide to setting it up, because there is more to it.

---

### Post by apel_2804 on 2009-04-12
Just to enshure it, the two URL's point to the same IP of that server, right (DNS)? And you reload apache after you added the vhost config file?

---

### Post by qaylin on 2009-04-12
The only thing that I can see that you may want to add is

```

<VirtualHost *:80>

```

Just so apache knows to listen on port 80 for any request to that host.  Hope that helps.

---

### Post by Iowan on 2009-04-12
[Here]("http://ubuntu-tutorials.com/2008/01/09/setting-up-name-based-virtual-hosting/") is a How-To for name based virtual hosting.

---

