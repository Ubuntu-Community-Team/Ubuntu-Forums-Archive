---
title: "Apache2 - HTTP + HTTPS = No go."
date: 2009-04-23
forum: Server Platforms
---

### Post by StrangeWill on 2009-04-23
I can go one OR the other, depending on which one is first in the apache2.conf list... but they SHOULD be listening on seperate ports.


web.conf:
```

NameVirtualHost *
<VirtualHost *:80>
ServerAdmin webmaster@localhost

<Directory />
	Options FollowSymLinks
	AllowOverride All
</Directory>


<Directory "/var/www/">
Options FollowSymLinks Indexes MultiViews
AllowOverride None
	Order allow,deny
	allow from all
</Directory>

ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
<Directory "/usr/lib/cgi-bin">
AllowOverride None
Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
AddHandler cgi-script cgi pl
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
DocumentRoot /var/www/
SSLEngine off
</VirtualHost>


```

ssl.conf:
```

NameVirtualHost SSL
<VirtualHost *:443>
#SSL
SSLEngine on
SSLCertificateFile /etc/apache2/ssl/apache.pem
ServerAdmin webmaster@localhost

<Directory />
	Options FollowSymLinks
	AllowOverride All
</Directory>


<Directory "/var/www/">
Options FollowSymLinks Indexes MultiViews
AllowOverride None
	Order allow,deny
	allow from all
</Directory>

ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
<Directory "/usr/lib/cgi-bin">
AllowOverride None
Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
AddHandler cgi-script cgi pl
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
DocumentRoot /var/www/
</VirtualHost>

```


I cleared out default to make sure that the (now) web.conf wasn't overriding ssl.conf.

---

### Post by arsnova on 2009-04-23
In my case, I define NameVirtualHost (mine is port 8080) in the ports.conf file:

```
NameVirtualHost *:8080
Listen 8080

<IfModule mod_ssl.c>
    # SSL name based virtual hosts are not yet supported, therefore no
    # NameVirtualHost statement here
    Listen 443
</IfModule>
```

...and remove NameVirtualHost from the sites-available configurations. This pulls SSL or port 80 (or 8080 in my example) depending on the request. I would also remove the line 'NameVirtualHost SSL.' Try that and restart apache. Hope this helps!

---

