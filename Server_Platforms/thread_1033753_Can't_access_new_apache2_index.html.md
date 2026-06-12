---
title: "Can't access new apache2 index.html"
date: 2009-01-07
forum: Server Platforms
---

### Post by lumix on 2009-01-07
My etc/apache2/sites-available/default file has:

```
<VirtualHost *:80>
	ServerAdmin webmaster@localhost
	
	DocumentRoot /var/www/
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

```

and netstat -a shows:

> tcp        0      0 *:www                   *:*                     LISTEN  

and I have the standard "It Works!" index.html in said /var/www.

What am I missing?

---

### Post by volkswagner on 2009-01-07
You may need to provide additional information.
[LIST]
[*]How are you accessing localhost or LAN connected, or via internet
[*]What error message or what happens when you try to access site?
[/LIST]

---

### Post by lumix on 2009-01-07
Well, somehow the lo interface was turned off.  Kinda odd since I *never* turn off the loopback (knowingly, anyway), for just this reason.

---

