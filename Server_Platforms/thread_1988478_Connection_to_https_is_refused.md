---
title: "Connection to https is refused"
date: 2012-05-27
forum: Server Platforms
---

### Post by clay7 on 2012-05-27
Hello,

I can access my site over http (port 80) but if I try https (port 443) I get a connection refused error. Why is this?

I'm using:
Ubuntu server 12.04 LTS
Apache 2 with mod ssl. The default-ssl shows up in sites-available and in sites-enabled

IPTables shows:
-A INPUT -p tcp --dport 443 -j ACCEPT

I installed the SSL cert and its intermediate cert according to the website's instructions. I've done this before and had no problems.

Here is some of the info from sites-available/default-ssl

<VirtualHost xx.xx.xx.xx:443>
	ServerAdmin [email]admin@xxxx.com[/email]
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

#ErrorLog ${APACHE_LOG_DIR}/error.log
	ErrorLog /var/log/apache2/error.log

	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel warn

	CustomLog ${APACHE_LOG_DIR}/ssl_access.log combined

	Alias /doc/ "/usr/share/doc/"
	<Directory "/usr/share/doc/">
		Options Indexes MultiViews FollowSymLinks
		AllowOverride None
		Order deny,allow
		Deny from all
		Allow from 127.0.0.0/255.0.0.0 ::1/128
	</Directory>

	#   SSL Engine Switch:
	#   Enable/Disable SSL for this virtual host.
	SSLEngine on

	#   A self-signed (snakeoil) certificate can be created by installing
	#   the ssl-cert package. See
	#   /usr/share/doc/apache2.2-common/README.Debian.gz for more info.
	
	SSLCertificateFile /etc/ssl/certs/xxx.crt
	SSLCertificateKeyFile /etc/ssl/private/xxx.key
	SSLCertificateChainFile /etc/ssl/certs/xxx.crt


Thanks!

---

### Post by clay7 on 2012-05-27
Wow. 4 hours of frantic searching, only to find out that i didn't a2enmod ssl. 

Wow.

---

