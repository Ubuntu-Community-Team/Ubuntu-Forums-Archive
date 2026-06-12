---
title: "Need help with Apache rewrite syntax"
date: 2010-09-30
forum: Server Platforms
---

### Post by Jive Turkey on 2010-09-30
I have an ubuntu home server running apache and other services.  I also use the hosts file trick to block ads and other junk on all of my computers.

Instead of setting my hosts files to 127.0.0.1 or 0.0.0.0, I would like to point it to an IP for my server and have a nice looking tiled image served so that web pages with ads will have my nice index.html page shown instead of the ads or my browsers' "server not found" message in the advert elements.  I have apache serving the page but I think I need to make a apache rewrite rule to get my clients request for the ads' uri to get the substituted content.  I've looked at some rewrite examples and I just don't get the syntax.

In short, I want all requests to serve "index.html" even if "garbage/advert/obnoxiousflash-ad.flv" or anything else is requested.

This is what I've tried so far (the first thing that doesn't throw errors anyway)
```

<VirtualHost *:80>
	ServerAdmin webmaster@localhost

	DocumentRoot /var/www/ads
	<Directory />
		Options FollowSymLinks
		AllowOverride None
		[COLOR="Red"]RewriteEngine On
		RewriteRule ^(.*)$	$/index.html	[L][/COLOR]
	</Directory>
	<Directory /var/www/ads/>
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

```

---

### Post by Ryan Dwyer on 2010-09-30
That rule should work. Make sure you have mod_rewrite enabled (sudo a2enmod rewrite) and restart Apache after any config changes (sudo service apache2 restart).

Edit: Wait, remove the $ from $/index.html.

---

### Post by Jive Turkey on 2010-09-30
> **Ryan Dwyer said:**
> That rule should work. Make sure you have mod_rewrite enabled (sudo a2enmod rewrite) and restart Apache after any config changes (sudo service apache2 restart).

Edit: Wait, remove the $ from $/index.html.

That didn't quite do it for me but I think I'm getting closer.  Part of the problem is that I'm trying to have it rewrite everything to /index.html however, everything includes /index.html apache hates me for this.

I've come up with:```
               RewriteRule !\.index.html$ - [S=1]
                RewriteRule ^(.*)$ http://10.0.0.100/index.html [L]

```
The first line, I believe should skip the next rule if /index.html is requested and the next line should rewrite everything to /index.html
Still, nothing seems to be affected.  What I want should never return 404's because it should be serving index.html for all requests.  I'm still as confused.

---

### Post by Ryan Dwyer on 2010-09-30
Have you considered using an ErrorDocument instead of mod_rewrite?

This should do the trick:
ErrorDocument 404 /index.html

EDIT: This one works:

```

RewriteEngine On
RewriteRule index.html - [L]
RewriteRule . /index.html

```

---

