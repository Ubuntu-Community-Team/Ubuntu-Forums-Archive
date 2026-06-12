---
title: "Another apache2 start problem"
date: 2007-04-05
forum: Server Platforms
---

### Post by silurius on 2007-04-05
I had a healthy LAMP going with Xfce installed, and all was well until I allowed an automatic update through without carefully checking it.

I did note that each update component was directly related to the LAMP stuff, but should probably have researched each individual update before letting it proceed.  I do not know how to go back into a log to determine what was installed or patched today, so I can't seem to share the specifics on what was updated, here, yet.

Soon after, apache pages were no longer loading.  All my config files are present, and file/folder permissions look OK, so I tried stopping and starting apache2 over SSH and got this:

```
root@[mybox]:/var/log/apache2# sudo /etc/init.d/apache2 start
 * Starting apache 2.0 web server...
apache2: Could not determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
(98): make_sock: could not bind to address [::]:80
no listening sockets available, shutting down
Unable to open logs
   ...fail!
root@[mybox]:/var/log/apache2#
```

Just for the heck of it, I tried it in an Xfce session:

```
root@[mybox]:~$ sudo /etc/init.d/apache2 start
Password:
 * Starting apache 2.0 web server...                                            apache2: Could not determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
(98): make_sock: could not bind to address [::]:80
no listening sockets available, shutting down
Unable to open logs
                                                                         [fail]
root@[mybox]:~$ 
```

And yet, stopping (either method) seems to be OK:

```
root@[mybox]:~# sudo /etc/init.d/apache2 stop
 * Stopping apache 2.0 web server...
   ...done.
```

Thinking one of the updates may have borked something, I decided to reinstall and got:

```
root@[mybox]:~# sudo aptitude reinstall apache2
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages will be REINSTALLED:
  apache2
0 packages upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0B/36.0kB of archives. After unpacking 0B will be used.
Writing extended state information... Done
(Reading database ... 167853 files and directories currently installed.)
Preparing to replace apache2 2.0.55-4ubuntu4 (using .../apache2_2.0.55-4ubuntu4_i386.deb) ...
Unpacking replacement apache2 ...
Setting up apache2 (2.0.55-4ubuntu4) ...
root@[mybox]:~#
```

and

```
root@[mybox]:/var/log/apache2# sudo aptitude reinstall php5 libapache2-mod-php5
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages will be REINSTALLED:
  libapache2-mod-php5 php5
0 packages upgraded, 0 newly installed, 2 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0B/2319kB of archives. After unpacking 0B will be used.
Writing extended state information... Done
(Reading database ... 167853 files and directories currently installed.)
Preparing to replace libapache2-mod-php5 5.1.6-1ubuntu2.3 (using .../libapache2-mod-php5_5.1.6-1ubuntu2.3_i386.deb) ...
Unpacking replacement libapache2-mod-php5 ...
Preparing to replace php5 5.1.6-1ubuntu2.3 (using .../php5_5.1.6-1ubuntu2.3_all.deb) ...
Unpacking replacement php5 ...
Setting up libapache2-mod-php5 (5.1.6-1ubuntu2.3) ...
 * Forcing reload of apache 2.0 web server...
apache2: Could not determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
(98): make_sock: could not bind to address [::]:80
no listening sockets available, shutting down
Unable to open logs
   ...fail!
invoke-rc.d: initscript apache2, action "force-reload" failed.

Setting up php5 (5.1.6-1ubuntu2.3) ...
root@[mybox]:/var/log/apache2#
```

Permissions for /var/log/apache2 directory are 0755.

The only errors I see in /var/log/apache2/error.log are:

```
[Sun Apr 01 07:35:16 2007] [notice] Apache/2.0.55 (Ubuntu) PHP/5.1.6 configured -- resuming normal operations
[Mon Apr 02 08:40:55 2007] [notice] caught SIGTERM, shutting down
[Mon Apr 02 08:42:12 2007] [notice] Apache/2.0.55 (Ubuntu) PHP/5.1.6 configured -- resuming normal operations
[Tue Apr 03 14:54:57 2007] [notice] caught SIGTERM, shutting down
[Tue Apr 03 14:56:05 2007] [notice] Apache/2.0.55 (Ubuntu) PHP/5.1.6 configured -- resuming normal operations
[Tue Apr 03 15:11:19 2007] [notice] caught SIGTERM, shutting down
[Tue Apr 03 15:12:37 2007] [notice] Apache/2.0.55 (Ubuntu) PHP/5.1.6 configured -- resuming normal operations
[Thu Apr 05 09:01:16 2007] [notice] caught SIGTERM, shutting down
[Thu Apr 05 09:01:31 2007] [notice] Apache/2.0.55 (Ubuntu) PHP/5.1.6 configured -- resuming normal operations
[Thu Apr 05 14:23:39 2007] [notice] caught SIGTERM, shutting down
```

My /etc/apache2/sites-available/default:

```
NameVirtualHost *
<VirtualHost *>
	ServerAdmin webmaster@localhost
	
	DocumentRoot /var/www

	RewriteEngine on
	
	<Directory />
		Options FollowSymLinks
		AllowOverride All
	</Directory>
	<Directory /var/www/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride All
		Order allow,deny
		allow from all
		# Uncomment this directive is you want to see apache2's
		# default start page (in /apache2-default) when you go to /
		#RedirectMatch ^/$ /apache2-default/
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

```

Checked to see what apache2 might be running, and got:

```
root@[mybox]:~# ps aux | grep apache2
root      5565  0.0  0.0   2800   752 pts/0    R+   16:40   0:00 grep apache2
root@[mybox]:~#
```

Ran ps aux|grep apache and got:

```
root@[mybox]:~# ps aux|grep apache
root      4807  0.0  0.4   7032  4236 ?        S    16:58   0:00 /usr/sbin/apache
www-data  4812  0.0  0.2   7032  2412 ?        S    16:58   0:00 /usr/sbin/apache
www-data  4813  0.0  0.1   7032  2008 ?        S    16:58   0:00 /usr/sbin/apache
www-data  4814  0.0  0.1   7032  2008 ?        S    16:58   0:00 /usr/sbin/apache
www-data  4815  0.0  0.1   7032  2008 ?        S    16:58   0:00 /usr/sbin/apache
www-data  4816  0.0  0.1   7032  2008 ?        S    16:58   0:00 /usr/sbin/apache
www-data  5164  0.0  0.1   7032  2008 ?        S    17:02   0:00 /usr/sbin/apache
root      5171  0.0  0.0   2796   748 pts/0    R+   17:05   0:00 grep apache
root@[mybox]:~#
```

...but I wasn't sure what it signified.  Just in case, I tried killing the apache processes:

```
root@[mybox]:~# sudo kill {4812,4813,4814,4815,4816,5164}
```

But the processes reappear again soon after.

[I](edits to log troubleshooting steps and remove rant)
(edited to flag as resolved)[/I]

---

### Post by silurius on 2007-04-05
Figured it out.

Earlier today, I installed Request Tracker using the "For Dummies" method (ran Synaptic and didn't monitor the dependencies).  As far as I can tell, Request Tracker 3.4.4-2 likes to install apache.  Or perhaps I overlooked something.  In any case, removing apache and starting apache2 took care of the problem.

So satisfying to fix a problem more or less on my own for once.

---

