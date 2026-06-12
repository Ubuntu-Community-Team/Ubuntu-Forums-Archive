---
title: "how to  do VirtualHost ?"
date: 2006-09-21
forum: Server Platforms
---

### Post by iraklirost on 2006-09-21
I have apache2.0.54 , php4 
I write command in terminal:

sudo /etc/init.d/apache2 restart  * Forcing reload of apache 2.0 web server... apache2: Could not determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
[Thu Sep 21 17:57:06 2006] [warn] NameVirtualHost *:0 has no VirtualHosts
[Thu Sep 21 17:57:06 2006] [warn] NameVirtualHost *:0 has no VirtualHosts
apache2: Could not determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
[Thu Sep 21 17:57:06 2006] [warn] N[COLOR="Red"]ameVirtualHost *:0 has no VirtualHost[/COLOR]s
[Thu Sep 21 17:57:06 2006] [warn] NameVirtualHost *:0 has no VirtualHosts

/etc/apache2/sites-available/1webi#

NameVirtualHost *
<VirtualHost 127.0.0.3:80>
ServerAdmin [email]webmaster@1web.org[/email]
servername 1web.org
DocumentRoot /var/www/1web
<Directory />
Options FollowSymLinks
AllowOverride None
</Directory>
<Directory /var/www/1web>
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

/etc/hosts
127.0.0.3 1web.org

---

### Post by spp on 2006-09-22
I think the problem stems from the fact that Apache is binding to the 127.0.0.1 IP address but you defined a virtual host for 127.0.0.3. It is telling you that 127.0.0.1 has no hosts.

I am not 100% certain but that sticks out in my mind.

SP

---

