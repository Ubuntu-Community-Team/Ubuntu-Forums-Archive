---
title: "Jaunty Virtual Host Problem"
date: 2009-08-10
forum: Server Platforms
---

### Post by Jyncka on 2009-08-10
I set up a lamp environment and tried setting up multiple virtual hosts.  Oddly, when I point my browser to "http://localhost" I get a working default host but any other named hosts I've set up can't be found.  I'll post my .conf file in a little while and anything else that needs to be posted.

I've tried enabling the sites and restarting apache without luck.

---

### Post by samosamo on 2009-08-10
Great thread you got going here.  Really.

---

### Post by Jyncka on 2009-08-10
At work, got caught up doing work, but nevertheless here is the default file:

<VirtualHost *:80>
        ServerName MySite
	ServerAdmin webmaster@localhost

	DocumentRoot /var/www/mysite
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /var/www/mysite>
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

Now I'm getting a NameVirtualHost *:80 has no VirtualHosts error.  Thanks for any help.

---

### Post by dreville on 2009-08-25
I get this same problem and I can't seem to figure it out.

Basically, instead of going to the proper location in my computer, it goes to the net and then gives me a "domain not found" error

> **Jyncka said:**
> I set up a lamp environment and tried setting up multiple virtual hosts.  Oddly, when I point my browser to "http://localhost" I get a working default host but any other named hosts I've set up can't be found.  I'll post my .conf file in a little while and anything else that needs to be posted.

I've tried enabling the sites and restarting apache without luck.

---

