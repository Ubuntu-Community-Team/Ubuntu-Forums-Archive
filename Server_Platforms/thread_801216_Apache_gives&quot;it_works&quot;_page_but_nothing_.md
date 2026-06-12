---
title: "Apache gives&quot;it works&quot; page but nothing else"
date: 2008-05-20
forum: Server Platforms
---

### Post by lunatinker on 2008-05-20
EDIT :: I highlighted what the important point here was. thanks =)!
I read this thread about another person's problems:
[http://ubuntuforums.org/showthread.php?t=388765](http://ubuntuforums.org/showthread.php?t=388765)
I sincerely hope that the bug/issue discussed there is not still with Ubuntu at this time. I hope that the below just is an accident that helped me in my sleepiness.

I looked at my Ubuntu 8.04 fresh install and found this ->

sudo vi /etc/hosts:
[COLOR="Red"]127.0.0.1 localhost[/COLOR]
127.0.1.1 mycomputersname
-----------------------------
after installing the LAMP business, I could only get the "it works"  page and nothing beyond that in depth /var/www/folder 
or even contents of the /var/www/somefile.blahfoo same folder

I read that post, change the above to the below:
----------------------------
[sudo gedit for dumb lazy me]
sudo gedit /etc/hosts
[COLOR="Red"]
127.0.0.1 localhost mycomputersname[/COLOR]
127.0.1.1 mycomputersname
...........
----------------------------
save exit.
remove firefox 3b. reinstall firefox 3b.
I deselected gnome support and "ubufox" that came preinstalled.
I checked apache running (yup still)
for giggles I sudo /etc/init.d/apache2 restart
I also ran the ls -l and checked owner/group/permissions
for www/ folder but did not change them (none of that).
so now my page /var/www/dictionary-parser.php (or other crap)
works fine.

---

### Post by jjgomera on 2008-05-20
well, you can configure apache2 with file /etc/apache2/sites-available/default

for example:

```
NameVirtualHost *
<VirtualHost *>
	ServerAdmin webmaster@localhost
	
	DocumentRoot /var/www/
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
                #**RedirectMatch ^/$ /apache2-default/**
```
you must comment the bold line to see the /var/www normal index view

you can change that line to make default index another file

---

### Post by harishcm on 2009-09-11
I had the same problem. And I had followed the [server guide][sg] pretty well.

[sg]: [https://help.ubuntu.com/8.04/serverguide/C/httpd.html](https://help.ubuntu.com/8.04/serverguide/C/httpd.html)

In the end I realised that I had to refresh my firefox browser!! Bummer..

---

