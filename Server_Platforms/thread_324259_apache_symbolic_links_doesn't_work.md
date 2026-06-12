---
title: "apache symbolic links doesn't work"
date: 2006-12-23
forum: Server Platforms
---

### Post by swigrid on 2006-12-23
hi,

I've got trouble with following simbolic links in my root direcotry of apache. I've got ubuntu dapper, if it is important...

my config file is:

[PHP]/etc/apache2/sites-available/default[/PHP]

[PHP]
NameVirtualHost *
<VirtualHost *>
	ServerAdmin webmaster@localhost
	
	DocumentRoot /var/www
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /var/www/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
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
[/PHP]

---

### Post by tturrisi on 2006-12-23
Symbolic links to "where"?

---

### Post by swigrid on 2006-12-24
i have symbolic links in /var/www. for example i've got there apache sym link which leads to my www sites in my documents on other partition (FA32). another sym link is for example tmp which leads to next partition and i use it for loading files for my friends. they can download from there whatever. in my next distribution gentoo isn't any problem with sym links. i've compared config files, but they are different and i m just confused.

anyway thanx for your replay

---

### Post by tturrisi on 2006-12-24
I do not believe you can symlink to other dirs that are not www dirs by default.  The easiest way to do what you want is to create a dir here:
/home/user/public_html and symlink to that dir.  Do NOT give www access to levels above public_html or above /var/www/, that's way too insecure.

---

### Post by toast2coast on 2007-12-25
I think that if you make a symbolic link from /var/www/ to somewhere in your home directory you need to make sure that you have r (and maybe x) permissions for 'others' for all directories in path. I had the exact same problem, changed /home/toast from 700 to 755 and... success!

Kind of sketchy but I have never been able to get apache2 working using the 'preferred' methods...

---

### Post by ytene on 2007-12-25
I have exactly the same problem, have done a little more experimentation, and found some weird results.

Basically, I think the issue is that Apache 2.2 will not follow Symbolic Links to the FAT32 file system. I'd like to be able to say that this includes FAT16, but I don't have such a partition on my machine and am therefore unable to test. 

At first I thought this was related to my upgrade from ubuntu 6.10 to 7.10 [ I just did a lift and drop of my configuration files into 

/etc/apache2/sites-available

and then did the softlinks in to the equivalent sites-enabled folder. I discovered that only some of my web sites seemed to be working, which is of course rather weird. 

I'd be interested to know if anyone else has found this. I haven't yet completed my experimentation, but will post more if I find anything else...

---

