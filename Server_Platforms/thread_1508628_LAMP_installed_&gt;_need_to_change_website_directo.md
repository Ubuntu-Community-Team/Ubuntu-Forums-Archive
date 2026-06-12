---
title: "LAMP installed &gt; need to change website directory"
date: 2010-06-13
forum: Server Platforms
---

### Post by sokekoke on 2010-06-13
Hello all,

I just installed LAMP on ubuntu 10.04
*(using this method: [http://tuxtweaks.com/2010/04/installing-lamp-on-ubuntu-10-04-lucid-lynx/](http://tuxtweaks.com/2010/04/installing-lamp-on-ubuntu-10-04-lucid-lynx/))*

Now i want to change the directory where my websites are; default is "/var/www" right. I have a partition using NTSF file system where i have a folder with all my websites. Can i configure LAMP to use this folder?

Thanks a lot! 
-JN

---

### Post by Ryan Dwyer on 2010-06-13
Edit /etc/apache2/sites-available/default. Change all instances of /var/www to the new directory. Then reload Apache.

---

### Post by sokekoke on 2010-06-13
> **Ryan Dwyer said:**
> Edit /etc/apache2/sites-available/default. Change all instances of /var/www to the new directory. Then reload Apache.

GREATS! thanks :-D

Just a quick beginner question, bare with me.

My NTSF partition is called DATA, so instead of /var/www/ i type media/DATA/Websites/ ?

this will output following error on localhost:

> Not Found

The requested URL / was not found on this server.

---

### Post by Ryan Dwyer on 2010-06-13
/media/DATA/Websites

Note the slash at the start and the missing slash at the end.

---

### Post by sokekoke on 2010-06-13
> > **Ryan Dwyer said:**
> /media/DATA/Websites

Note the slash at the start and the missing slash at the end.

Strange, i still get error. When i try reload server it says:

Warning: DocumentRoot [/media/DATA/Websites] does not exist

its a logical partition, when i installed ubuntu it was called "sda5", i can see the drive in menu: places > DATA

OKAY works with /media/DATA/Websites/

but now i get:

[B]Forbidden

You don't have permission to access / on this server.[/B]

from localhost

---

### Post by Ryan Dwyer on 2010-06-13
This is most likely a file permissions issue. Run ls -l /media/DATA/Websites/ and paste the results here.

---

### Post by sokekoke on 2010-06-13
> **Ryan Dwyer said:**
> This is most likely a file permissions issue. Run ls -l /media/DATA/Websites/ and paste the results here.

jonas@sokekoke:~$ ls -l /media/DATA/Websites/
total 2528
drwx------ 1 jonas jonas    4096 2010-06-11 01:28 backup
drwx------ 1 jonas jonas    4096 2010-06-11 01:30 CakePHP
drwx------ 1 jonas jonas       0 2010-06-11 01:30 FÓM Projekt
-rwxrwxrwx 2 jonas jonas 2574902 2007-08-05 00:00 Keil_OldHeader_photoshop.psd
drwx------ 1 jonas jonas       0 2010-06-11 01:30 keilstruplund
drwx------ 1 jonas jonas       0 2010-06-11 01:30 lokalprojekt
drwx------ 1 jonas jonas       0 2010-06-11 01:30 norlins
drwx------ 1 jonas jonas       0 2010-03-05 12:44 Super-ferie
drwx------ 1 jonas jonas       0 2010-06-11 01:31 temp
drwx------ 1 jonas jonas    4096 2010-06-11 01:31 Testsiden
drwx------ 1 jonas jonas       0 2010-06-11 01:31 traehuset

---

### Post by Ryan Dwyer on 2010-06-13
The webserver process doesn't have permission to read those files. We can fix this by adding the web server user (www-data) to the jonas group and giving the group read access to the files.

You should edit /etc/group and add www-data to the end of the jonas line.

eg.
jonas:x:1000:www-data

Then change the permissions so the group can read them:
chmod -R 740 /media/DATA/Websites

Then restart Apache.

---

### Post by sokekoke on 2010-06-13
Hmm dosent seem to do the trick, 

I renamed the line in group to: jonas: x:1000:www-data

then i run: chmod -R 740 /media/DATA/Websites

and restart apache. Get same localhost error and the *"ls -l /media/DATA/Websites/"* listing is the same

---

### Post by Ryan Dwyer on 2010-06-13
OK. Edit /etc/apache2/sites-available/default. Where it says Options -Indexes, change it to Options Indexes (just remove the dash). Reload Apache.

If you still have problems, post the output of: tail /var/log/apache2/error.log

---

### Post by sokekoke on 2010-06-13
Thanks for all your patience :)

I think this is already the case:

> <VirtualHost *:80>
	ServerAdmin webmaster@localhost

	DocumentRoot /media/DATA/Websites/
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /media/DATA/Websites/>
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

Error log:

jonas@sokekoke:~$ tail /var/log/apache2/error.log
[Sun Jun 13 15:34:00 2010] [error] [client 127.0.0.1] (13)Permission denied: access to / denied
[Sun Jun 13 15:35:47 2010] [notice] caught SIGTERM, shutting down
PHP Deprecated:  Comments starting with '#' are deprecated in /etc/php5/apache2/conf.d/mcrypt.ini on line 1 in Unknown on line 0
[Sun Jun 13 15:36:49 2010] [notice] Apache/2.2.14 (Ubuntu) PHP/5.3.2-1ubuntu4.2 with Suhosin-Patch configured -- resuming normal operations
[Sun Jun 13 15:38:14 2010] [error] [client ::1] File does not exist: /media/DATA
[Sun Jun 13 15:38:18 2010] [error] [client ::1] File does not exist: /media/DATA
[Sun Jun 13 15:47:44 2010] [notice] Graceful restart requested, doing restart
PHP Deprecated:  Comments starting with '#' are deprecated in /etc/php5/apache2/conf.d/mcrypt.ini on line 1 in Unknown on line 0
[Sun Jun 13 15:47:44 2010] [notice] Apache/2.2.14 (Ubuntu) PHP/5.3.2-1ubuntu4.2 with Suhosin-Patch configured -- resuming normal operations
[Sun Jun 13 15:48:14 2010] [error] [client ::1] (13)Permission denied: access to / denied

---

### Post by Ryan Dwyer on 2010-06-13
I suspect the drive isn't mounted when Apache starts. That's why you get "File does not exist: /media/DATA". Then as a fallback it's trying to serve from / which is incorrect.

Have you added the mount to your /etc/fstab? And how are you restarting Apache - by using /etc/init.d/apache2 restart or by rebooting the server itself?

---

### Post by sokekoke on 2010-06-13
I have not added the mount to the fstab i think, can i check this?

[B]EDIT: no, it only has /dev/sda7 and /dev/sda6 

my DATA drive is called /dev/sda5 but i dont know what to fill in the other options: mount point, type, options, dump, pass[/B]


WHen you tell me to restart apache i do this: "sudo /etc/init.d/apache2 reload"

---

### Post by Ryan Dwyer on 2010-06-13
You'll know if you added it to fstab. Adding it to fstab means it's mounted as the computer is booting. If you're using a desktop environment it will only mount once you try to open it by clicking the icon.

You should also be aware there is a difference in using reload vs restart in the apache command. Reload only reloads the configuration, whereas restart restarts the actual service. If you used restart it would read from the drive properly.

You should add your drive to fstab:
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131) (How to fstab)
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

You should then do a full reboot to make sure it's being mounted correctly on boot and that Apache is sweet.

---

### Post by Ryan Dwyer on 2010-06-13
> **sokekoke said:**
> EDIT: no, it only has /dev/sda7 and /dev/sda6 

my DATA drive is called /dev/sda5 but i dont know what to fill in the other options: mount point, type, options, dump, pass

mount point = /media/DATA
type = ntfs-3g
options = defaults
dump = 0
pass = 0

So your fstab line will be something like:
/media/DATA ntfs-3g defaults 0 0

If it doesn't work, tail your /var/log/syslog for clues.

I'm heading to bed now, so it'll be several hours before I reply.

---

### Post by sokekoke on 2010-06-13
I added the line you suggested, found something similar in the documentation provided but yours was simpler with "defaults".

and guess what... IT WORKS!!!

Thanks a ton for your time and help Ryan Dwyer, I'm new to linux so this a very nice success experience for me.

Now i will go make some websites :p

---

