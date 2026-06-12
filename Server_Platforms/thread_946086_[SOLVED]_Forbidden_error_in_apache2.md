---
title: "[SOLVED] Forbidden error in apache2"
date: 2008-10-13
forum: Server Platforms
---

### Post by Eto_Demerzel on 2008-10-13
This is a common error (as seen by searching on Google and these forums, but none of the solutions given help me)

After a complete removal of apache2 and re-installation. I test it with [http://my_ip_address/](http://my_ip_address/) and it displays the page index.html in /var/www/

Next, I modify the file /etc/apache2/sites-available/default

```

NameVirtualHost *
<VirtualHost *>
	ServerAdmin webmaster@localhost
	
	DocumentRoot **/var/www/**
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory **/var/www/**>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
	</Directory>
```

to

```
NameVirtualHost *
<VirtualHost *>
	ServerAdmin webmaster@localhost
	
	DocumentRoot **/home/myusername/my_www/**
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory **/home/myusername/my_www/**>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
	</Directory>
```

I create a folder called my_www/ in home/myusername/ and do
```
chmod -R 777 my_www/
```

and restart the server. But trying [http://my_ip_address/](http://my_ip_address/) gives me the Forbidden error.

What is most surprising is that if I place my_www/ folder anywhere **other** than under my home directory **hierarchy**, it works. But if I place it anywhere within /home/myusername/... it doesn't work.

Why can't apache2 access anything inside my home folder? 

Thanks.

---

### Post by Eto_Demerzel on 2008-10-13
Solved it! This thread had a similar problem.

[http://ubuntuforums.org/showthread.php?t=922964&highlight=public_html](http://ubuntuforums.org/showthread.php?t=922964&highlight=public_html)

This is where I was getting stumped:

> Ah.. but we haven't seen the permissions of the parent directory tree - these folders all need execute permissions setting to allow Apache to traverse them.

---

