---
title: "Apache on Vista AND Ubuntu"
date: 2007-09-04
forum: Server Platforms
---

### Post by hellonull on 2007-09-04
I have Apache installed on both Vista (via WinLAMP) and Ubuntu 7.04. The document root directory for both is a folder that I put on a third partition (Vista and Ubuntu each have their own partition). The third partition is a FAT32 filesystem. When I am in Vista and I type "localhost" into my browser, it works as expected. However, when I type "localhost" into the browser in Ubuntu, it gives me a "403 Forbidden" error. I tried sudo chmodding the document root directory to 777 but I am still getting the 403 error. Does anyone have any idea what's going on?

---

### Post by conjur3r on 2007-09-05
What do your apache error logs say?  They should be in /var/log/apache2/.  Also, could you do a ls -l on the document root?  And finally, paste the contents of your apache config relating to the document root.

---

### Post by hellonull on 2007-09-05
This error in the log appears repeatedly and is the one related to the issue:

> [error] [client 127.0.0.1] (13)Permission denied: access to / denied

ls -l produces the following:

> sean@sean-linux:/media/sda4/server/www$ ls -l
total 64
-rwxrwx---  1 root plugdev   143 2007-09-04 19:41 mktime.php
drwxrwx--- 13 root plugdev 16384 2007-08-20 19:55 nhs3
drwxrwx--- 13 root plugdev 16384 2007-08-20 19:55 nhs3-servered
-rwxrwx---  1 root plugdev    16 2007-09-04 04:32 phpinfo.php


This is the contents of the "000-default" file that is located in /etc/apache2/sites-enabled:

> NameVirtualHost *
<VirtualHost *>
	ServerAdmin webmaster@localhost
	
	DocumentRoot /media/sda4/server/www/
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /var/www/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
		# This directive allows us to have apache2's default start page
                # in /apache2-default/, but still have / go to the right place
                #RedirectMatch ^/$ /apache2-default/
	</Directory>

	ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
	<Directory "/usr/lib/cgi-bin">
		AllowOverride None
		Options ExecCGI -MultiViews +SymLinksIfOwnerMatch
		Order allow,deny
		Allow from all
	</Directory>

	ErrorLog /var/log/apache2/error.log

	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel warn

	CustomLog /var/log/apache2/access.log combined
	ServerSignature On

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>

---

### Post by conjur3r on 2007-09-05
Try the following:

DocumentRoot /media/sda4/server/www/
<Directory />
Options FollowSymLinks
AllowOverride None
</Directory>
<Directory [COLOR="Red"]/media/sda4/server/www/[/COLOR]>
Options Indexes FollowSymLinks MultiViews
AllowOverride None
Order allow,deny
allow from all
# This directive allows us to have apache2's default start page
# in /apache2-default/, but still have / go to the right place
#RedirectMatch ^/$ /apache2-default/
</Directory>

---

### Post by hellonull on 2007-09-05
I tried that but it still does not work.

I think the issue is that Apache tries to access the files as user "www-data" but that user is not set up to have permissions to access the directory. I logged in as root (the owner of the DocumentRoot directory) to try and change the permissions to allow all users read access to the directory but it said that the change was not allowed. Should I edit the Apache configuration file and set it to access the folder as the root user? Or how do I change the permissions so that www-data can have access to the folder?

---

### Post by conjur3r on 2007-09-05
I'm quite positive that on a FAT32 partition, permissions are not supported.  But at the very least, you should have read access.  Could you do a

# ls -l /media/sda4/server/www
# ls -l /media/sda4/server

The solution could be a matter of editing the mount options in your fstab!  ie, quite easy!

---

### Post by hellonull on 2007-09-06
```

sean@sean-linux:~$ ls -l /media/sda4/server/www
total 64
-rwxrwx---  1 root plugdev   143 2007-09-04 19:41 mktime.php
drwxrwx--- 13 root plugdev 16384 2007-08-20 19:55 nhs3
drwxrwx--- 13 root plugdev 16384 2007-08-20 19:55 nhs3-servered
-rwxrwx---  1 root plugdev    16 2007-09-04 04:32 phpinfo.php
sean@sean-linux:~$ ls -l /media/sda4/server
total 32
drwxrwx--- 3 root plugdev 16384 2007-08-20 18:50 mysql
drwxrwx--- 4 root plugdev 16384 2007-08-20 19:55 www

```

---

### Post by conjur3r on 2007-09-06
That's it.  The perms say that no one but root and anyone in the plugdev group can access the folder and its files.

Try editing your /etc/fstab by adding a few options to the line with sda4:

uid=www-data,gid=www-data

Or whatever to your liking.  Have a look at line 606 from "man mount" for more information.  This will tell it to mount the drive assigning it the specified user id and/or group id.

Once you've edited your fstab file, unmount /media/sda4 then remount it to apply the changes.  Then try ls -l again.  They should have www-data (or whatever you specified) now.  Apache should now be able to access the folders/files.

---

### Post by Naib Stilgar on 2008-05-09
Personally, I don't like to modify fstab (since I still want plugdev to own the shared drive). 
What I did is to add the user "www-data" to the group "plugdev". In order to do so, edit file /etc/group for the group "plugdev", by example:
```
plugdev:x:46:haldaemon,www-data
```

---

