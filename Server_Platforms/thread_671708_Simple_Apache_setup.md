---
title: "Simple Apache setup"
date: 2008-01-18
forum: Server Platforms
---

### Post by wheezer on 2008-01-18
Sorry to cross post, but I have scoured these boards, and the net.  Everyone discusses little fragments of this problem, but I don't see a concise solution to this exact problem, but many asking something like it,  so I felt a better subject line might help others.

**I have installed apache2 via synaptic ** and tried to start it, but got these errors. Can someone explain each to me, and why I cannot get it started in a basic way?


$ /etc/init.d/apache2 start

open: Permission denied
* Restarting web server apache2 apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
httpd (pid 24692?) not running
install: cannot change owner and/or group of `/var/lock/apache2': Operation not permitted
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
(13)Permission denied: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs
open: Permission denied

PS
I do have a simply path to my server root in apache2/sites-enabled, like so, but this is the only configuration I have done. I

e.g

filename = 000-default
NameVirtualHost *
<VirtualHost *>
	ServerAdmin webmaster@localhost
	
	DocumentRoot /home/me/http/
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /home/me/http/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
	</Directory>

---

### Post by Vinno on 2008-01-18
Did you run start command with sudo?

---

### Post by wheezer on 2008-01-18
> **Vinno said:**
> Did you run start command with sudo?

Uh... um... errrr...   argggggggggggggh!

Thanks.  I have the default root now showing "it works"

This,I proceed to my virtual hosts (after a beer).  Thanks vino!

---

