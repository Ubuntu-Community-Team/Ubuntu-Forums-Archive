---
title: "transmission-daemon isn't playing nice: &quot;409: Conflict&quot;"
date: 2012-05-16
forum: Server Platforms
---

### Post by sirspazzolot on 2012-05-16
> 409: Conflict

Your request had an invalid session-id header.

To fix this, follow these steps:

When reading a response, get its X-Transmission-Session-Id header and remember it
Add the updated header to your outgoing requests
When you get this 409 error message, resend your request with the updated header
This requirement has been added to help prevent CSRF attacks.

error occurs even when apache is not running. I've tried a zillion different proposed solutions involving RewriteRules and ProxyPasses but golly I'm just clueless. help me?

following is my apache thing, y'know, just in case.
```
<VirtualHost *:80>
	RewriteEngine on
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

	ErrorLog ${APACHE_LOG_DIR}/error.log

	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel warn

	CustomLog ${APACHE_LOG_DIR}/access.log combined

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>
############HERE IS THE TRANSMISSION PART####################
	RewriteRule /transmission[/]?$ /transmission/web [R=permanent]

	ProxyPass /transmission http://127.0.0.1:9091/transmission
	ProxyPassReverse /transmission http://127.0.0.1:9091/transmission
	Redirect permanent / /transmission/web

    <Location /transmission>

      Order Allow,Deny
      Allow from All

      # Make pictures, scripts and styling client-cacheable
      <IfModule expires_module>
         ExpiresActive On
         ExpiresByType image/gif A43200
         ExpiresByType image/png A43200
         ExpiresByType application/javascript A43200
         ExpiresByType text/css A43200
      </IfModule>

   </Location>

</VirtualHost>

```

---

