---
title: "Virtual host not working."
date: 2006-08-02
forum: Server Platforms
---

### Post by ragdemai on 2006-08-02
Im working hard to make the virtual host work on my apache2, my problem is when type my apache's host name in other PC with IE6 it work but when I try type in gp.home.co it coultn't work, then I add the name(gp.home.co) point to my localhost (System -> Administration -> Networking, Network setting in Hosts tab), it work only my localhost(my apache2 server). Below is my setting  in sites-available & this apache will only use in local area network :

NameVirtualHost *
<VirtualHost johnny.co>
	ServerName johnny.co
        ServerAlias gp.home.co
        ServerAdmin webmaster@localhost
	DocumentRoot /var/www/johnny
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /var/www/johnny/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
	</Directory>
</VirtualHost>

* others configuration file is remain as original fresh install

---

