---
title: "[SOLVED] apache and cgi-scripts"
date: 2008-10-20
forum: Server Platforms
---

### Post by TreeFinger on 2008-10-20
I am trying to get a python script to work that would run from my web server.

I created the directory /var/www/cgi-bin and put a working python script file in there.

when trying to access the script, [http://192.168.0.2/cgi-bin/servertime.py](http://192.168.0.2/cgi-bin/servertime.py)

I get a 404 error, file not found. It is there tho, trust me :)

when trying to browse cgi-bin I get a Forbidden page.

httpd.conf file
```

# cat /etc/apache2/httpd.conf
ScriptAlias /cgi-bin/ /var/www/cgi-bin/

```

I did not edit any other configuration files, the rest are default.

```

/var/www# ls -al
total 20
drwxr-xr-x  3 root root 4096 2008-10-20 15:04 .
drwxr-xr-x 14 root root 4096 2008-10-18 21:51 ..
drwxr-xr-x  2 root root 4096 2008-10-20 15:01 cgi-bin
-rw-r--r--  1 root root   45 2008-10-18 21:51 index.html
-rw-r--r--  1 root root   20 2008-10-20 14:49 testphp.php

```

---

### Post by cariboo on 2008-10-20
If you just put cgi scripts anywhere you want they aren't going to work, you would have to change the path to where they are located. Cgi-bin scripts are normally located in /usr/lib/cgi-bin. You would have to edit /etc/apache2/sites-available/default to change the path. Here is the section of the config file you would have to change:

```
	ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
	<Directory "/usr/lib/cgi-bin">
		AllowOverride None
		Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
		Order allow,deny
		Allow from all
	</Directory>
```

Jim

---

### Post by TreeFinger on 2008-10-20
> **cariboo907 said:**
> If you just put cgi scripts anywhere you want they aren't going to work, you would have to change the path to where they are located. Cgi-bin scripts are normally located in /usr/lib/cgi-bin. You would have to edit /etc/apache2/sites-available/default to change the path. Here is the section of the config file you would have to change:

```
	ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
	<Directory "/usr/lib/cgi-bin">
		AllowOverride None
		Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
		Order allow,deny
		Allow from all
	</Directory>
```

Jim

Well, I plan on having users of my web server upload files via sftp. What would be a good configuration for this?

---

### Post by cariboo on 2008-10-20
The problem with having cgi-bin scripts in /var/www is that it wouldn't take much guessing to access the directory and just run the scripts and maybe do bad things to your server. Running the scripts in the standard location even if a visitor to your site knew where the scripts are they can't access /usr/lib/cgi-bin from /var/www

Jim

---

### Post by TreeFinger on 2008-10-21
> **cariboo907 said:**
> The problem with having cgi-bin scripts in /var/www is that it wouldn't take much guessing to access the directory and just run the scripts and maybe do bad things to your server. Running the scripts in the standard location even if a visitor to your site knew where the scripts are they can't access /usr/lib/cgi-bin from /var/www

Jim


Thank you, very much. Moved my example python script to /usr/lib/cgi-bin and it worked great :)

now, I must read up on the best way to allow users to upload files to my web server.

---

