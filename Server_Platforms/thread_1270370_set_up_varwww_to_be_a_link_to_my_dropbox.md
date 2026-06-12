---
title: "set up /var/www to be a link to my dropbox ?"
date: 2009-09-19
forum: Server Platforms
---

### Post by Findarato on 2009-09-19
Hello everyone,

I have recently installed dropbox and wanted to share my laptop and desktop development folders.
I thought I could simply replace my /var/www with a symlink to /home/username/Dropbox/www, but when I do that, I get the following error:
You don't have permission to access /www on this server.

I have already given myself ALL the possible rights on this folder, but it won't solve the error. Does anyone have an idea ?

Thank you very much,

Findarato

---

### Post by Bachstelze on 2009-09-19
You must add a [font=monospace]<Directory>[/font] entry for /home/username/Dropbox/www to your Apache configuration allowing access to it. Since it's outside /var/www, access is denied by default.

Or you cound bind it to /var/www: [font=monospace]sudo mount -o bind /home/username/Dropbox/www /var/www[/font], but be sure to remove your symlink before and create /var/www as a regular, empty directory.

---

### Post by Findarato on 2009-09-19
Could you please tell me how that would look ?

My current /etc/apache2/sites-available/default looks like this :
```
<VirtualHost *:80>
	ServerAdmin webmaster@localhost

	DocumentRoot /var/www
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /var/www>
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
```

Also, I would like databases to be shared in the same way. Which file would I have to edit and how ?

---

### Post by Bachstelze on 2009-09-19
If you aren't going to use /var/www, you could as well move your DocumentRoot to /home/username/Dropbox/www. Just replace every occurrence of /var/www in your file with /home/username/Dropbox/www. Can't help you with databases.

---

### Post by Findarato on 2009-09-19
> **Bachstelze said:**
> If you aren't going to use /var/www, you could as well move your DocumentRoot to /home/username/Dropbox/www. Just replace every occurrence of /var/www in your file with /home/username/Dropbox/www. Can't help you with databases.

I already tried that, but I get exactly the same error

---

### Post by Bachstelze on 2009-09-19
Does Apache have read permission to the directory?

---

### Post by Findarato on 2009-09-19
yup, rights are set to 777

---

### Post by Bachstelze on 2009-09-19
Well, I guess we won't go through every possible cause one at a time. Post yur logs. ;)

---

### Post by Findarato on 2009-09-19
Here you go :)
```

[Sat Sep 19 21:50:49 2009] [error] [client 127.0.0.1] (13)Permission denied: access to /index.php denied
[Sat Sep 19 21:50:49 2009] [error] [client 127.0.0.1] (13)Permission denied: access to /index.xhtml denied
[Sat Sep 19 21:50:49 2009] [error] [client 127.0.0.1] (13)Permission denied: access to /index.htm denied
[Sat Sep 19 21:51:06 2009] [notice] caught SIGTERM, shutting down
[Sat Sep 19 21:51:07 2009] [notice] Apache/2.2.11 (Ubuntu) PHP/5.2.6-3ubuntu4.2 with Suhosin-Patch configured -- resuming normal operations
[Sat Sep 19 21:51:46 2009] [error] [client 127.0.0.1] Symbolic link not allowed or link target not accessible: /var/www/www2


```
Only the last line is relevant, the other lines refer to my testing of other solutions :)

---

### Post by Findarato on 2009-09-19
Problem solved, I had to give 755 permissions on my /user folder...

---

