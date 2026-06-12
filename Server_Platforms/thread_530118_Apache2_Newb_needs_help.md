---
title: "Apache2 Newb needs help"
date: 2007-08-20
forum: Server Platforms
---

### Post by flyinggreg on 2007-08-20
I got an interesting problem...its probably something simple I am missing...

I am building a website for my company and I am learning to use Apache2 for the server.   I have successfully built a starter "Under Construction" page and can view it locally typing my website name (I have it behind the firewall currently).

I wrote the index.html and an AboutUs.html using OpenOffice Writer.  I found Kompozer and decided to rewrite the pages.  I deleted the old index.html and emptied the trashbin.  The problem I have is everytime I try to view the updated web pages using Firefox, I get the old files!  I am pretty confused how this could be.

It's been a few weeks since I worked on this, and I am already a newb with this - so everything I have been figuring out...I mentally dumped.

BTW - I have tried restarting Apache and rewrote my directory and servername directives several times.  I still get the old page that doesn't exist.

I am sure it is something simple...but I need another set of eyes and experience to help me find the problem!

Thanks in advance!

---

### Post by DeusEx on 2007-08-20
where are you storing the files and where's the www folder according to apache's conf file?

---

### Post by flyinggreg on 2007-08-20
The folder I setup in my /sites-avalaible/default (which has a symbolic link /sites/enabled/default) is to my directory where the files should be.  This is where the original files were and where the ones I changed are now.  What directive should I look for in my apache2.conf?

---

### Post by PimpDaddyA on 2007-08-20
It's almost a certainty that my comment won't help, but: I'm also new with Apache and had a similar problem which drove me absolutely mad for a few minutes until I explicitly RELOADED the page in Firefox.  It had been caching the old page until I forced it to reload.

Needless to say, I felt silly and angry all at once.  Good luck with your problem.

---

### Post by southernman on 2007-08-20
> **PimpDaddyA said:**
> It's almost a certainty that my comment won't help, but: I'm also new with Apache and had a similar problem which drove me absolutely mad for a few minutes until I explicitly RELOADED the page in Firefox.  It had been caching the old page until I forced it to reload.

Needless to say, I felt silly and angry all at once.  Good luck with your problem.
It's my first guess too... especially if they are browsing using a Windows box and IE... we all know that the default cache size for Windows is something in the area of a million MB. ;) Ok, not that large but large enough to be a strain.

Try clearing your cache and see if it helps.

---

### Post by flyinggreg on 2007-08-20
Ok, I cleared out Firefox's cache and reloaded Apache2...now I get a 403 Error:
Forbidden

You don't have permission to access / on this server.
Apache/2.2.3 (Ubuntu) mod_ssl/2.2.3 OpenSSL/0.9.8c Server at [www.wingandrotors.com](www.wingandrotors.com) Port 80

It looks like its trying to do SSL, which is incorrect...this is the unsecure portion (I haven't written the secure yet).

Or is it getting blocked by my firewall?  Before, the firewall would basically say the site doesn't exist...which I fixed on my nameserver.

I am really a newb with the website building, web serverbuilding, etc.  But I do appreciate all your patience and help - I am learning A TON from you guys and the web!!!  ;D

---

### Post by southernman on 2007-08-20
> **flyinggreg said:**
> Ok, I cleared out Firefox's cache and reloaded Apache2...now I get a 403 Error:
Forbidden

You don't have permission to access / on this server.
Apache/2.2.3 (Ubuntu) mod_ssl/2.2.3 OpenSSL/0.9.8c Server at [www.wingandrotors.com](www.wingandrotors.com) Port 80

It looks like its trying to do SSL, which is incorrect...this is the unsecure portion (I haven't written the secure yet).

Or is it getting blocked by my firewall?  Before, the firewall would basically say the site doesn't exist...which I fixed on my nameserver.

I am really a newb with the website building, web serverbuilding, etc.  But I do appreciate all your patience and help - I am learning A TON from you guys and the web!!!  ;DNo it's trying to connect on port 80, not 443. Your seeing that info cause you don't have it turned off in apache2.conf edit that file to show:

ServerSignature Off
ServerTokens Prod

You'll only see that it's apache service the files from that point on.

You've definately got something afoul with the default site configuration or at least it seems so. Post the contents of that file so we can take a look at it.

---

### Post by flyinggreg on 2007-08-20
I had a / directory showing and then it quit - now I get:

> Unable to connect
         

Firefox can't establish a connection to the server at [www.wingandrotors.com](www.wingandrotors.com).

    *   The site could be temporarily unavailable or too busy. Try again in a few
          moments.

    *   If you are unable to load any pages, check your computer's network
          connection.

    *   If your computer or network is protected by a firewall or proxy, make sure
          that Firefox is permitted to access the Web.





Ok, here's my /sites-available/default: 

```
NameVirtualHost *
<VirtualHost *>
	ServerAdmin webmaster@localhost
	ServerName localhost
	DocumentRoot /
		
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

#</VirtualHost>


<VirtualHost *>
	ServerName wingandrotors.com
		
	DocumentRoot /home/gjolah/Documents/Web_Server
	<Directory /home/gjolah/Documents/Web_Server/>
		Options Indexes FollowSymLinks MultiViews
                # pcw AllowOverride None
                AllowOverride All
                Order allow,deny
                allow from all
        </Directory>
```

---

### Post by southernman on 2007-08-20
Replace your default file with this below...
```

NameVirtualHost *
<VirtualHost *>
	ServerAdmin webmaster@localhost

	DocumentRoot /var/www		
	<Directory />
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
	ServerSignature Off

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

I wouldn't really make this more complicated than it is... seeing as the trouble your having finding the documentation to do what you've tried. Keep your website files under /var/www.

If you insist doing it your way, then read up on the virtual host section of the link below:
[https://help.ubuntu.com/community/ApacheMySQLPHP]("https://help.ubuntu.com/community/ApacheMySQLPHP")

You've got a lot on your plate trying to learn (emphasis on learn) how to build a website and become a Server Administrator (not web serverbuilding as you call it). It may behoove you to focus on learning HTML and web design... and let someone else host the website for you after it is ready. Just a thought... and sincere advice.

No harm in tinkering with a server on your computer, but making it internet facing your certainly asking for trouble.

---

