---
title: "[SOLVED] Apache directory alias for uploads"
date: 2008-03-18
forum: Server Platforms
---

### Post by coops36 on 2008-03-18
Hi all, 
I am creating a PHP filesharing website. With uploads and downloads on my Ubuntu LAMP installation. Being both new to Linux and Apache, this is posing quite some problems, I currently have the web site located in the default /var/www/ folder. 

I am testing the PHP upload which works fine when the target directory is located in /var/www/uploads but if I want the uploaded files to sit on my second HD at  /media/storage/files/ folder with the following directory alias:

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

	ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
	<Directory "/usr/lib/cgi-bin">
		AllowOverride None
		Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
		Order allow,deny
		Allow from all
	</Directory>

[COLOR="Red"]Alias /uploads/ "/media/storage/files/"
<Directory "/media/storage/files/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Allow from all
</Directory>[/COLOR]

The PHP script uploads to ./uploads/ should not apache redirect the uploads to the alias location?


Any pointers appreciated.

Thanks

---

### Post by cozmicharlie on 2008-04-14
You have this marked as solved.   I am trying to do the same and I am curiuos how you got this to work.

---

