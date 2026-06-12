---
title: "Apache2 httpd configuration"
date: 2012-06-24
forum: Server Platforms
---

### Post by grollsta on 2012-06-24
I've been searching for how to do this too.

My /sites-available shows the following if I ls -ali the directory
```
graeme@graeme-laptop:/etc/apache2/sites-available$ ls -ali
total 32
533766 drwxr-xr-x 2 root root 4096 Jun 24 18:54 .
533663 drwxr-xr-x 7 root root 4096 Jun 24 17:01 ..
534143 -rw-r--r-- 1 root root  957 Jun 24 17:59 default
534140 -rw-r--r-- 1 root root 1005 Jun 24 17:56 default~
533767 -rw-r--r-- 1 root root 7469 Feb  7 06:17 default-ssl
534137 -rw-r--r-- 1 root root  955 Jun 24 18:54 phpdev
534142 -rw-r--r-- 1 root root  956 Jun 24 17:59 phpdev~
graeme@graeme-laptop:/etc/apache2/sites-available$
```

I copied the "default" file to phpdev and want this to point to /$HOME/phpdev, where I have my index.html file waiting to be loaded...

my phpdev file has the following text in it:
> 
<VirtualHost *:80>
	ServerAdmin webmaster@localhost

	DocumentRoot /$HOME/phpdev
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

	ErrorLog ${APACHE_LOG_DIR}/error.log

	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel warn

	CustomLog ${APACHE_LOG_DIR}/access.log combined

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>

If I run [http://localhost](http://localhost), the apache2 server answer correctly with its default page.

But, I can't see how to get the server to see my /$HOME/phpdev folder and pick up the index/html sitting there.

I must be missing something...brains probably

---

### Post by SeijiSensei on 2012-06-25
If you're actually using $HOME to point to your home directory, that won't work.  (First, how would Apache know whose $HOME to use on a multi-user system?). 

You need to provide a complete, unambiguous path to the DocumentRoot directory, and that directory must be listable and readable by the pseudo-user under which the server runs called "www-data".

So if user janet has a site in /home/janet/website, you need to use that in any DocumentRoot or corresponding <Directory> entries.  You'll also need to change permissions on that directory since Ubuntu limits access to home directories by default to their owners.

```

cd /home
sudo chmod a+x janet
cd janet
chmod a+x website
chmod -R a+r website/*

```

Now the www-data can list and read files in /home/user/janet, though only janet can modify these files.

In this case you'd use "DocumentRoot /home/janet/website" to point to the site, and "<Directory /home/janet/website>" to hold the options associated with the directory.

As for the problem of supporting multiple sites, you need to read about [name-based virtual hosts]("http://httpd.apache.org/docs/2.2/vhosts/name-based.html").  At a minimum, you'll need a "ServerName" directive for your phpdev site, and an entry in /etc/hosts that points that name to 127.0.0.1 or to the server's network IP address.

Finally, as a general rule, it's better to start a new thread rather than extend an old one, especially if the old one is already marked [SOLVED].

---

### Post by nothingspecial on 2012-06-25
Moved to own thread.

---

