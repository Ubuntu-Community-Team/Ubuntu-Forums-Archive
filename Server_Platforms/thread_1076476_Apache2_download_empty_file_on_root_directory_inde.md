---
title: "Apache2: download empty file on root directory index (again)"
date: 2009-02-21
forum: Server Platforms
---

### Post by BlueElk on 2009-02-21
Hi,

I have a "standard installation" (via the synaptic package manager) apache2-server with mysql and php support. (I followed these instructions: [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP))

When I try to access the document root at [http://localhost](http://localhost) my browser (firefox) pops a download-dialogue, saying: 

---
You have chosen to open

which is a: ~ file
from: [http://localhost](http://localhost)
---

What I would like to see is a directory listing. Directory listings for sub-directories work fine. Why is the server feeding me an empty file for the document root?

The same problem is described in this thread: [http://ubuntuforums.org/showthread.php?t=814606](http://ubuntuforums.org/showthread.php?t=814606)  but I am not to keen to try the suggested solution, which is to delete /etc/apache2 and re-install apache2.2-common. Is there no other way?

I tried adding a DirectoryIndex directive (and restart apache) but no dice.

This is me:

Apache/2.2.9 (Ubuntu) PHP/5.2.6-2ubuntu4.1 with Suhosin-Patch Server at localhost Port 80

Ubuntu 8.10 (intrepid)

Kernel 2.6.27-11-generic

---

### Post by BlueElk on 2009-02-26
*nudge*

---

### Post by Inigo Montoya on 2009-02-26
would you please list the content of your /etc/apache2/sites-available/default?

---

### Post by BlueElk on 2009-02-28
I made a copy of the default website, like so:

```
sudo cp /etc/apache2/sites-available/default /etc/apache2/sites-available/thomas
```

and changed DocumentRoot, and the relevant Directory directive. Finally:

```
sudo a2dissite default && sudo a2ensite thomas
```

and

```
sudo /etc/init.d/apache2 restart
```

Here's the file "thomas" (identical to "default" except for the changes I mentioned above) :

```
<VirtualHost *:80>
	ServerAdmin webmaster@localhost

	
	DocumentRoot /home/thomas/public_html/
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /home/thomas/public_html/>
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

---

### Post by BlueElk on 2009-03-07
*bump*

---

