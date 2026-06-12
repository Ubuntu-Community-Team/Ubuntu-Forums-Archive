---
title: "Converting Websites to SSL"
date: 2016-10-24
forum: Security
---

### Post by astarmathsandphysics on 2016-10-24
I changed all my websites to ssl this year and being penniless, I didn;t spend a penny on it. Heres how.
I got a free ssl certificate from cloudflare and saved it to  /etc/ssl/certs/domain.com.pem and the key to /etc/ssl/private/domain.com.key
Go to /etc/apache2/sites-available/domain.tlf.conf and edit the file to look like this

<VirtualHost 192.168.0.10:80>
	ServerName domain.com
	ServerAlias [www.domain.com](www.domain.com)
   Redirect permanent / [https://domain.com](https://domain.com)
</VirtualHost>
<VirtualHost 192.168.0.10:443>
SSLEngine      on
SSLCertificateFile        /etc/ssl/certs/domain.com.pem
SSLCertificateKeyFile     /etc/ssl/private/domain.com.key
Alias /awstatsclasses "/usr/share/awstats/lib/"
Alias /awstats-icon "/usr/share/awstats/icon/"
Alias /awstatscss "/usr/share/doc/awstats/examples/css"
ScriptAlias /awstats/ /usr/lib/cgi-bin/
Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
	ServerAdmin [email]admin@domain.com[/email]
	ServerName domain.com
	ServerAlias [www.domain.com](www.domain.com)
	DocumentRoot /var/www/domain
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /var/www/domain/>
		Options ExecCGI Indexes FollowSymLinks MultiViews
		AllowOverride All
		Order allow,deny
		allow from all
	</Directory>

	ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
	<Directory "/usr/lib/cgi-bin">
		AllowOverride All
		Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
		Order allow,deny
		Allow from all
	</Directory>

<IfModule mod_security2.c>
  SecRuleEngine Off
</IfModule>

	Errorlog /var/www/domain_error_log
#	ErrorLog ${APACHE_LOG_DIR}/error.log

	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel warn

	CustomLog ${APACHE_LOG_DIR}/domain.log combined

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>
 Make sure ports 80 and 443 are open in router firewall and ufw.
Add this to /var/www/domain/.htaccess

RewriteEngine On
RewriteCond %{HTTP_HOST} ^[www.domain.com](www.domain.com) [NC]
RewriteRule ^(.*)$ http://domain.com/$1 [L,R=301]

RewriteCond %{HTTPS} off
RewriteRule (.*) https://%{HTTP_HOST}%{REQUEST_URI} [R,L]
In my case this redirect everything to https:/domain.com/etc

In your domain config or settings file or the database you might need to change the base url to [https://etc](https://etc).
You will also need to edit some settings in cloudflare. I chose to max security at every opportunity.

Hop this helps someone.

---

### Post by TheFu on 2016-10-25
Interesting.  

Let's Encrypt offers free certs and free renewals.  It is pretty trivial to setup if you use apache - everything is handled through a script:  
```
  sudo apt install letsencrypt python-letsencrypt-apache
  sudo letsencrypt --apache --agree-tos --email webmaster@example.com -d ssl.example.com
  sudo vi /etc/apache2/sites-available/ssl.example.com.conf  # check that everything is fine; it was here.
  sudo systemctl reload apache2

```
For nginx, the manual steps are needed - there is a specific file that has to be available through the website for Let's Encrypt to find.
Then don't forget to setup a crontab to renew the certs every 75 days with a simple  **/usr/bin/letsencrypt  renew** from the root crontab.

And your visitors don't have to worry about some 3rd party seeing all the traffic or caching everything indefinitely. 
[https://scotthelme.co.uk/tls-conundrum-and-leaving-cloudflare/](https://scotthelme.co.uk/tls-conundrum-and-leaving-cloudflare/)

BTW, *code tags* in the OP would be appreciated. Helps with readability.

---

