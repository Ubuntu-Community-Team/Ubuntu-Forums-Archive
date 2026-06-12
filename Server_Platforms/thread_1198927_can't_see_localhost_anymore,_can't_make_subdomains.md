---
title: "can't see localhost anymore, can't make subdomains"
date: 2009-06-28
forum: Server Platforms
---

### Post by morganpatrick on 2009-06-28
Hi.

I'm running normal Ubuntu. I installed the lamp stack. It worked.

Then started trying to set up my localhost subdomains.

I tried [this]("https://help.ubuntu.com/community/LocalhostSubdomain"). It didn't work. I noticed I didn't have a network configuration applet. I installed it, tried to change hosts through there instead, didn't work. I just got 500 errors

I changed everything back to the way it was and then tried [this]("http://ubuntuforums.org/showthread.php?p=3637593"). It didn't work. I put everything back. I tried [this]("http://thinkingnectar.com/2008/getting-ubuntu-to-work-creating-subdomain-in-localhost/"). It didn't work.

I've set everything back now and now localhost doesn't even work. Should I just wipe out apache and reinstall it? How do I get my subdomains??

---

### Post by morganpatrick on 2009-06-28
by the way, here's more info:

etc/hosts shows
```
127.0.0.0	localhost

127.0.1.1	morgan-laptop


# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

127.0.0.0 doesn't load but 127.0.0.1 does.

etc/apache2/httpd.conf is empty and was before i edited it.

in etc/apache2/sites-available I had created a file called myconfigs and ran a2ensite. Now I have run a2dissite to remove it. Here's what is in default:

```
<VirtualHost *:80>
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
        AllowOverride All
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>
```

---

### Post by commandergc on 2009-06-28
You need to change 127.0.0.0 to 127.0.0.1 in all your config's

127.0.0.0 is not valid.

---

### Post by morganpatrick on 2009-06-28
I see. OK so now  I have both localhost and morgan-laptop aliased to 127.0.0.1...

Now: the local copies of the sites I work on have to have some distinct way for me to get to them. I need to go in and define global paths for these and localhost/subsite will not do.

I would be happy to do:

127.0.0.1
127.0.0.2
127.0.0.3

~or~

site1.localhost
site2.localhost
site3.localhost

~or~

localhost:80
localhost:800
localhost:8000

whatever makes the most sense and is the most stable and easy. Subdomains seemed to make the most sense to me, but then I have all these different tutorials and none of them work.

I'm going to go back and restrace my steps in the event that I was using 127.0.0.0 the whole time and this was the issue. In the meantime, if anyone can tell me the easiest and best way to set up subdomains, this would be greatly appreciated.

Thank you.

---

### Post by morganpatrick on 2009-06-28
alright so I copied this [again]("http://thinkingnectar.com/2008/getting-ubuntu-to-work-creating-subdomain-in-localhost/"), using only one new subdomain, and 127.0.0.1. localhost goes to 127.0.0.1 and newsite.localhost also goes to 127.0.0.1, and not the subfolder i specified.

edit: I am also getting this warning: 

$ sudo /etc/init.d/apache2 restart
 * Restarting web server apache2                                                [Sun Jun 28 14:32:12 2009] [warn] NameVirtualHost *:80 has no VirtualHosts
 ... waiting [Sun Jun 28 14:32:13 2009] [warn] NameVirtualHost *:80 has no VirtualHosts

---

### Post by morganpatrick on 2009-06-28
in my site-available file, changing <VirtualHost *> to <VirtualHost *:80> removes the error. It also gives me a 500 error when i try to go to my subdomain. My localhost works fine.

---

### Post by Iowan on 2009-06-29
127.0.0.0 would be the network address (as mentioned - not valid for machine address). 
[Here]("http://ubuntu-tutorials.com/2008/01/09/setting-up-name-based-virtual-hosting/") is an article for name-based virtual hosts.

---

