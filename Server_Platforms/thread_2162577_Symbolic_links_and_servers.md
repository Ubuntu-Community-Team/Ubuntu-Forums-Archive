---
title: "Symbolic links and servers"
date: 2013-07-15
forum: Server Platforms
---

### Post by Mariane on 2013-07-15
Hi, 

I have a problem with apache2, it seems to block symbolic links. 

There are 2 disks on this machine:
- One virtual system disk ("sys")
- One storage disk ("store")

The space on "sys" is provided by my ISP (gandi.net) and cannot be increased.
The space on "store", where the web files are, is large enough.

phpmyadmin now fails because it cannot write session info. "sys" is full. 

I created a php5 directory on "store" and made a symbolic link to the place where phpmyadmin wants to write. In /sys/var/lib I wrote:

```

ln -s /store/var/lib/php5 php5

```

This would function on a local machine but it does not function on a remote one. When I go to mysite/phpmyadmine I get:

```

phpMyAdmin - Error
Cannot start session without errors, please check errors given in your PHP and/or webserver log file and configure your PHP installation properly.

```

On:
[http://wiki.phpmyadmin.net/pma/session.save_path](http://wiki.phpmyadmin.net/pma/session.save_path)
It says the problem comes from apache, but it does not really say what to do. It says "Like many other PHP applications phpMyAdmin tries to save user related data in a folder on the web server which should be defined in the loaded php.ini (or in httpd.conf or .htaccess if you are using the Apache web server)".

Is there a simple command I could type to tell apache to follow symbolic links? I found an example of stuff to write in httpd.conf here:
[https://www.linuxquestions.org/questions/linux-software-2/apache-and-symbolic-links-42393/](https://www.linuxquestions.org/questions/linux-software-2/apache-and-symbolic-links-42393/)

I wrote:
```

<Directory />
    Options FollowSymLinks
    AllowOverride All
</Directory>

```

in /etc/apache2/httpd.conf (which was an empty file), but I still get the same error from phpmyadmin.

---

### Post by SeijiSensei on 2013-07-15
Delete that material from httpd.conf and edit /var/www/apache2/sites-available/default instead.  That is the file that controls basic server access.  Add the FollowSymLinks directive to the stanza for <Directory /> there instead.  Restart Apache with "sudo service apache2 restart" when you're done.

I suggest reading the [Ubuntu Server Guide]("https://help.ubuntu.com/lts/serverguide/httpd.html") to learn about how Ubuntu divides up the Apache configurations.  It is very different from the default Apache structure, or the structure used on RedHat-flavored machines, so online tutorials may not apply.

Another option you might consider is the [Alias]("http://httpd.apache.org/docs/current/mod/mod_alias.html") directive.  When placed in a virtual host definition, it allows you to point an arbitrary directory alias to any directory on the system.  Of course, the www-data user needs to have read privileges to that directory if you want to share its files.

---

### Post by Mariane on 2013-07-15
Thank you. 

I didn't find it, in /var/www/ there is one directory called apache2-default, but it only has pictures and an html file:
/var/www/apache2-default# ls
apache_pb22_ani.gif  apache_pb22.gif  apache_pb22.png  apache_pb.gif  apache_pb.png  index.html

I found /etc/apache2/sites-available/ with a file called default. Uh-ho. After what you told me, I'm wondering if this is Ubuntu. I am on Ubuntu, but it does not mean that this machine is also running Ubuntu... Anyway, I'll follow your suggestion on the "default" file and post again.

---

### Post by Mariane on 2013-07-15
All the "Options FollowSymLinks/AllowOverride" were set to None. I set them all to "All":

```

NameVirtualHost *
<VirtualHost *>
	ServerAdmin webmaster@localhost
	
	DocumentRoot /var/www/
	<Directory />
		Options FollowSymLinks
		AllowOverride All
	</Directory>
	<Directory /var/www/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride All
		Order allow,deny
		allow from all
		# This directive allows us to have apache2's default start page
                # in /apache2-default/, but still have / go to the right place
                #RedirectMatch ^/$ /apache2-default/
	</Directory>

	ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
	<Directory "/usr/lib/cgi-bin">
		AllowOverride All
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
        AllowOverride All
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>

```

---

### Post by Mariane on 2013-07-15
To restart mine I need:
```
 
/etc/init.d/apache2 restart

```

But now the whole site is offline... Heeeeeeeeeeelp!

---

### Post by SeijiSensei on 2013-07-15
Sorry.  Of course, the configurations are in /etc/apache2.  

What do you see in /var/log/apache2/error.log?

You do not need a NameVirtualHost declaration.  It is set in /etc/apache2/ports.conf to "NameVirtualHost *:80".  You should use the original shipped version of /etc/apache2/sites-available/default that starts with 
```
<VirtualHost *:80>
```
rather than
```
<VirtualHost *>
```

Are you really running 9.04?  The entire method for starting and stopping daemons has changed since then with the introduction of [Upstart]("http://upstart.ubuntu.com/").  The "service" command is part of Upstart (and, in fact, matches the equivalent command on RedHat-flavored systems).  You really should consider upgrading to at least 12.04LTS.

---

### Post by Mariane on 2013-07-16
Hi SeijiSensei, 

You are so kind to come back to that thread, I really appreciate that :). I'm not running 9.04, I should update my profile info on this forum. 

The error message of the restart is:

```

/etc/init.d/apache2 restart
 * Restarting web server apache2                                                                                                                                                   Warning: DocumentRoot [/srv/d_Charlotte/www/www.agence-de-dampierre.fr/htdocs/] does not exist
[Tue Jul 16 10:43:49 2013] [warn] NameVirtualHost *:80 has no VirtualHosts
httpd (no pid file) not running
Warning: DocumentRoot [/srv/d_Charlotte/www/www.agence-de-dampierre.fr/htdocs/] does not exist
[Tue Jul 16 10:44:00 2013] [warn] NameVirtualHost *:80 has no VirtualHosts

```

And it says "fail", written in red... :' 

The agence de dampierre site should be removed altogether, it does  not exist anymore. But that is not urgent.

---

### Post by Mariane on 2013-07-16
error.log is a huge file, and it keeps repeating stuff several times. I deleted multiple occurences of the same text to post here and I'm going to delete this file and replace it with an empty txt file. 

```

sendmail: fatal: lapf(1001): queue file write error
postdrop: warning: uid=1001: No space left on device
sendmail: fatal: lapf(1001): queue file write error
postdrop: warning: uid=1001: No space left on device
sendmail: fatal: lapf(1001): queue file write error
[Wed Jan 30 21:48:08 2013] [crit] mod_ruby: failed to create ruby thread
[Wed Jan 30 21:48:08 2013] [error] (12)Cannot allocate memory: fork: Unable to fork new process
Out of memory
[Wed Jan 30 21:48:18 2013] [error] (12)Cannot allocate memory: fork: Unable to fork new process
Out of memory
postdrop: warning: uid=1001: No space left on device
sendmail: fatal: lapf(1001): queue file write error
Out of memory
postdrop: warning: uid=1001: No space left on device
sendmail: fatal: lapf(1001): queue file write error
[Wed Jan 30 23:11:15 2013] [error] (12)Cannot allocate memory: fork: Unable to fork new process
Out of memory
[Wed Jan 30 23:11:17 2013] [error] (12)Cannot allocate memory: fork: Unable to fork new process
postdrop: warning: uid=1001: No space left on device
sendmail: fatal: lapf(1001): queue file write error
Out of memory
Out of postdrop: warning: uid=1001: No space left on device
sendmail: fatal: lapf(1001): queue file write error
postdrop: warning: uid=1001: No space left on device
sendmail: fatal: lapf(1001): queue file write error
[Thu May 30 19:29:59 2013] [crit] mod_ruby: failed to create ruby thread
[Thu May 30 19:29:59 2013] [error] (12)Cannot allocate memory: fork: Unable to fork new process
postdrop: warning: uid=1001: No space left on device
sendmail: fatal: lapf(1001): queue file write error
Out of memory
postdrop: warning: uid=1001: No space left on device
sendmail: fatal: lapf(2)No such file or directory: apache2: could not open error log file /srv/d_Charlotte/www/www.agence-de-dampierre.fr/logs/www.agence-de-dampierre.fr-error.log.
Unable to open logs
(2)No such file or directory: apache2: could not open error log file /srv/d_Charlotte/www/www.agence-de-dampierre.fr/logs/www.agence-de-dampierre.fr-error.log.
Unable to open logs

```

---

### Post by Mariane on 2013-07-16
Hurray! Hurray! Hurray!
You gave me the clue I needed!
error.log was such a huge file, with stuff dating back to 2009, that I decided to delete it. There was another one, access.log, which I also deleted. error.log was recreated when I did:
```

/etc/init.d/apache2 restart

```

When I saw it had been recreated, I looked at it. In error.log it was written:
```

(2)No such file or directory: apache2: could not open error log file /srv/d_Charlotte/www/www.agence-de-dampierre.fr/logs/www.agence-de-dampierre.fr-error.log.
Unable to open logs

```

Of course it could not open it, I had deleted the whole "www.agence-de-dampierre.fr" directory, to make space on the disk. I recreated this directory and a sub-directory called "logs". Then I did:

```

/etc/init.d/apache2 restart

```
again. 

And this time it said "OK" instead of "fail", and my site is online again!!! 

Now I have learnt that I should not try to remove an old web site by simply deleting it's directory. I'll remember that. I have to find out how to tell apache to forget "agence-de-dampierre" first.

---

### Post by SeijiSensei on 2013-07-16
If you follow the Ubuntu method of putting each site in a separate file in /etc/apache2/sites-available/, then deleting a site is as easy as either deleting the configuration file itself, or deleting the symlink to it from /etc/apache2/sites-enabled/.

You might want to consider running [logrotate]("http://linux.die.net/man/8/logrotate") on that machine to help keep your logs under control.  I also maintain site-specific logs in /var/log/apache2 by adding a TransferLog and an ErrorLog directive in each site's configuration that point to unique logs.

---

