---
title: "Virtual Hosts"
date: 2009-01-31
forum: Server Platforms
---

### Post by SeaborneClink on 2009-01-31
Okay, so I've got a couple sites enabled, say site2.com and site3.com

site2.com should direct to /var/www/site2.com
site3.com should direct to /var/www/site3.com
mydomain.com along with any wildcards (ip, another domain with A record to my ip) should direct to /var/www


Lets say site1.com is my site, and has a documentroot of /var/www

/etc/apache2/sites-available
 default
 site2.com
 site3.com

/var/www
 site2.com
 site3.com
 index.php

default
```
<VirtualHost *>
	ServerAdmin webmaster@localhost
	
	DocumentRoot /var/www/
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /var/www/>
		Options -Indexes FollowSymLinks MultiViews
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

```

site2.com
```
#
#  site2.com (/etc/apache2/sites-available/site2.com)
#

<VirtualHost *>
        ServerAdmin admin@site2.com
        ServerName  site2.com
        ServerAlias www.site2.com

        # Indexes + Directory Root.
        Options -Indexes
	DirectoryIndex index.php index.html
        DocumentRoot /var/www/site2.com/

        # CGI Directory
        ScriptAlias /cgi-bin/ /var/www/site2.com/cgi-bin/
        <Location /cgi-bin>
                Options +ExecCGI
        </Location>


        # Logfiles
        ErrorLog  /var/log/apache2/site2.com/error.log
        CustomLog /var/log/apache2/site2.com/access.log combined
</VirtualHost>

```

site3.com
```
#
#  site3.com (/etc/apache2/sites-available/site3.com)
#

<VirtualHost *>
        ServerAdmin admin@site3.com
        ServerName  site3.com
        ServerAlias www.site3.com

        # Indexes + Directory Root.
        Options -Indexes
	DirectoryIndex index.php index.html
        DocumentRoot /var/www/site3.com/

        # CGI Directory
        ScriptAlias /cgi-bin/ /var/www/site3.com/cgi-bin/
        <Location /cgi-bin>
                Options +ExecCGI
        </Location>


        # Logfiles
        ErrorLog  /var/log/apache2/site3.com/error.log
        CustomLog /var/log/apache2/site3.com/access.log combined
</VirtualHost>

```

site2.com directs fine to /var/www/site2.com
site3.com directs fine to /var/www/site2.com
However, when I use an IP, or mydomain.com it directs to the last enabled site.

ex. 
a2ensite site2.com
a2ensite site3.com

mydomain.com would direct to /var/www/site3.com instead of /var/www/

ex. 
a2ensite site3.com
a2ensite site2.com

mydomain.com would direct to /var/www/site2.com instead of /var/www/

As far as I can tell I have the sites configured correctly, but then again I might have overlooked something small and stupid.

I hope this isn't too much of a wall of code/text, and someone can help me get this sorted. :confused:

httpd.conf is empty
ports.cong contains
```

NameVirtualHost *
Listen 80

```

---

### Post by skunkbad on 2009-01-31
There's more to name based virtual hosting than default and sites-enabled/sites-available. Post your apache2.conf. Specifically, the following needs to be inside it:

# Include the virtual host configurations:
Include /etc/apache2/sites-enabled/

Your sites-available files are more elaborate than mine, while your default file looked identical. You might try reverting to something like what I will provide below, and check to see what happens:

```
<VirtualHost *>
	ServerName [www.site2.com](www.site2.com)
        ServerAlias site2.com	
	DocumentRoot /var/www/site2
	<Directory /var/www/site2>
		Options -Indexes FollowSymLinks MultiViews
		AllowOverride All
		Order allow,deny
		allow from all
	</Directory>
	ErrorLog /var/log/apache2/site2-error.log
</VirtualHost>
```

---

### Post by SeaborneClink on 2009-01-31
> **skunkbad said:**
> There's more to name based virtual hosting than default and sites-enabled/sites-available. Post your apache2.conf. Specifically, the following needs to be inside it:

# Include the virtual host configurations:
Include /etc/apache2/sites-enabled/

Your sites-available files are more elaborate than mine, while your default file looked identical. You might try reverting to something like what I will provide below, and check to see what happens:

```
<VirtualHost *>
	ServerName [www.site2.com](www.site2.com)
        ServerAlias site2.com	
	DocumentRoot /var/www/site2
	<Directory /var/www/site2>
		Options -Indexes FollowSymLinks MultiViews
		AllowOverride All
		Order allow,deny
		allow from all
	</Directory>
	ErrorLog /var/log/apache2/site2-error.log
</VirtualHost>
```
It's definitely there, ln #668

I just don't understand why a site (mydomain.com) would direct to ANY of the sites enabled unless there was a rule configured specifically to handle mydomain.com -> /var/www/foo

If there isn't a rule configured for it, should it not just direct to the web root? In this case /var/www/

---

### Post by skunkbad on 2009-01-31
So, you can verify your sites-available using vi, and what about the symbolic links that are in sites-enabled? I don't use a2ensite. The way I have been doing it is to manually create the files, and then create the symbolic link:

touch /etc/apache2/sites-available/site2
sudo vi /etc/apache2/sites-available/site2
sudo ln -s ../sites-available/site2 .

I have four sites running this way, and when trying to use a direct IP address, an error message says that directory browsing is not available.

My server version is 8.04, but i doubt it would make a difference.

---

### Post by SeaborneClink on 2009-02-01
> **skunkbad said:**
> So, you can verify your sites-available using vi, and what about the symbolic links that are in sites-enabled? I don't use a2ensite. The way I have been doing it is to manually create the files, and then create the symbolic link:

touch /etc/apache2/sites-available/site2
sudo vi /etc/apache2/sites-available/site2
sudo ln -s ../sites-available/site2 .

I have four sites running this way, and when trying to use a direct IP address, an error message says that directory browsing is not available.

My server version is 8.04, but i doubt it would make a difference.

Well the symbolic links are there, and they work just fine site2.com -> /var/www/site2.com

It's just when you use a url that **doesn't** have a virtualserver assigned to it, I get the unexpected results
ie, mydomain.com -> /var/www/site2.com :(

or enable the sites in order of say, site2.com, site3.com then mydomain.com would point -> /var/www/site3.com

Very bizarre that it points to the last enabled site.

I've even tried specifying in the apache2.conf
```
DocumentRoot /var/www
```
And it still doesn't seem to make a difference.

---

### Post by SeaborneClink on 2009-02-01
Bump. Any sugguestions?

---

### Post by SeaborneClink on 2009-02-02
Another day, another bump :(

---

### Post by SeaborneClink on 2009-02-03
Still unsolved :(

---

### Post by spiderbatdad on 2009-02-03
consider aliasing in /etc/hosts```
<ipaddress> site1.com site2.com site3.com
```
to resolve these names outside the lan or via dns you must actually register the additional sites to resolve to your public ip address.
You might also try specifying separate ports inside the vitual hosts file and in ports.conf:


```
<VirtualHost site2.com:81>

```

```
Listen 80
Listen 81

```Forward the additional ports from your router to server.
You dont need multiple vitual host files, just <VirtualHost> containers inside the one virtual host file you enable.

---

### Post by SeaborneClink on 2009-02-03
> **spiderbatdad said:**
> consider aliasing in /etc/hosts```
<ipaddress> site1.com site2.com site3.com
```
to resolve these names outside the lan or via dns you must actually register the additional sites to resolve to your public ip address.
You might also try specifying separate ports inside the vitual hosts file and in ports.conf:


```
<VirtualHost site2.com:81>

```

```
Listen 80
Listen 81

```Forward the additional ports from your router to server.
You dont need multiple vitual host files, just <VirtualHost> containers inside the one virtual host file you enable.

This isn't on a home server it's a production server. 

The odd thing is that I've got them all working now, except for one site. And that one site only responds to [www.site3.com](www.site3.com) but if you try to access it via site3.com it will direct to /var/www/ instead of /var/www/site3.com :shock: bizarre.

---

### Post by volkswagner on 2009-02-04
One thing I notice.  Your config file for site2 does not have the trailing slash in document and directory root as default and other sites.

I am not sure what problems this causes, but it is worth a shot to get them all the same.

You should follow the syntax in the default file.  Use proper open and close tags.
```

	DocumentRoot /var/www/
	[COLOR="Red"]<Directory />[/COLOR]
		Options FollowSymLinks
		AllowOverride None
	[COLOR="Red"]</Directory>
	<Directory /var/www/>[/COLOR]
		Options -Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
		# This directive allows us to have apache2's default start page
                # in /apache2-default/, but still have / go to the right place
                #RedirectMatch ^/$ /apache2-default/
	[COLOR="Red"]</Directory>[/COLOR]
```

---

### Post by SeaborneClink on 2009-02-04
> **volkswagner said:**
> One thing I notice.  Your config file for site2 does not have the trailing slash in document and directory root as default and other sites.

I am not sure what problems this causes, but it is worth a shot to get them all the same.

You should follow the syntax in the default file.  Use proper open and close tags.
```

	DocumentRoot /var/www/
	[COLOR="Red"]<Directory />[/COLOR]
		Options FollowSymLinks
		AllowOverride None
	[COLOR="Red"]</Directory>
	<Directory /var/www/>[/COLOR]
		Options -Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
		# This directive allows us to have apache2's default start page
                # in /apache2-default/, but still have / go to the right place
                #RedirectMatch ^/$ /apache2-default/
	[COLOR="Red"]</Directory>[/COLOR]
```
Yeah I noticed it was missing the trailing slash also, and corrected it in my file, reloaded, still the same problem.

I'm in the process of backing up the /var/www/ folder and all the log files and I'm going to purge apache and reinstall it.

We'll see how it goes. :-|

---

### Post by SeaborneClink on 2009-02-04
Well I've completely removed apache, and reinstalled it, and the problem persists. 

At this point I'm completely stumped. If anyone would like a copy of the **exact** Vhost file without the site's actual names edited out, send me a PM and I'd be happy to send them on their way if I can get this resolved. ](*,)

---

### Post by SeaborneClink on 2009-02-04
Quick update, I used a completely clear vhost file, and changed the vhost's documentroot folder to another website hosted on the server.

site2.com directs to /var/www/
[www.site2.com](www.site2.com) directs to /var/www/otherwebsite

Should I go put this up on an Apache mailing list?

---

### Post by SeaborneClink on 2009-02-05
Quick bump before I head off to bed :(

---

### Post by SeaborneClink on 2009-02-08
Another bump, still unresolved.

Should I put this on an apache mailing list?

---

### Post by SeaborneClink on 2009-02-10
> **SeaborneClink said:**
> Another bump, still unresolved.

Should I put this on an apache mailing list?

This is still unresolved. volkswagner and I spent a good two hours today trying to get to the bottom of why it's directing to random directories, and we've both come up stumped.

---

### Post by etali on 2009-02-10
This probably isn't going to help, but I had a similar problem with a VirtualHost pointing to the wrong folder, and it turned out that host was missing from the local IP line in my /etc/hosts file - I see that's already been mentioned, but it's worth double checking - hopefully it's just a typo in there?

---

### Post by cha0s on 2009-05-04
> **SeaborneClink said:**
> This is still unresolved. volkswagner and I spent a good two hours today trying to get to the bottom of why it's directing to random directories, and we've both come up stumped.


I'm having the same problem. I have 2 hosts, hippie and uc1.hippie pointing to 127.0.0.1 (in /etc/hosts).

Here's the kicker. If I go to uc1.hippie, I'm redirected to /var/www, but if I go to uc1.hippie/index.php or even uc1.hippie/?, it brings me to the correct location. I'm currently stumped.

sites-available/hippie:
```
<VirtualHost *:80>
	ServerName hippie

	DocumentRoot /share/www/dev/ubercart/2
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /share/www/dev/ubercart/2>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride All
		Order allow,deny
		allow from all
	</Directory>
</VirtualHost>
```

```
<VirtualHost *:80>
	ServerName uc1.hippie

	DocumentRoot /share/www/dev/ubercart/1
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /share/www/dev/ubercart/1>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride All
		Order allow,deny
		allow from all
	</Directory>
</VirtualHost>
```

Help is appreciated. :)

---

### Post by cha0s on 2009-05-04
Hey nevermind, I'm SO STUPID!

All I had to do was clear Firefox's cache! Damn :lolflag:

---

### Post by rich97 on 2009-11-02
For anyone googleing in the future (as I was) I found the problem for me was incorrect permissions in the parent folder.

Apache needs permissions 755 to see the document root it is pointing to.

Hope that helps someone. ;)

---

### Post by Vegan on 2009-11-02
On my site I have a post outlining how to setup vhosts, quick and painlessly. See the LAMP area in the forum.

---

