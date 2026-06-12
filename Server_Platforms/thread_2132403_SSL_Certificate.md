---
title: "SSL Certificate"
date: 2013-04-04
forum: Server Platforms
---

### Post by AvengerX9 on 2013-04-04
I just followed these instructions with no errors
[https://www.digitalocean.com/community/articles/how-to-create-a-ssl-certificate-on-apache-for-ubuntu-12-04](https://www.digitalocean.com/community/articles/how-to-create-a-ssl-certificate-on-apache-for-ubuntu-12-04)

and now my apache server wont start after doing the reload. I get this error in the apache error log.

[PHP]
[Thu Apr 04 23:35:54 2013] [notice] Graceful restart requested, doing restart
[Thu Apr 04 23:35:54 2013] [warn] _default_ VirtualHost overlap on port 443, the first has precedence
[Thu Apr 04 23:35:54 2013] [warn] NameVirtualHost *:80 has no VirtualHosts
[Thu Apr 04 23:35:55 2013] [warn] RSA server certificate CommonName (CN) `truckstop24.no' does NOT match server name!?
[Thu Apr 04 23:35:55 2013] [error] Unable to configure RSA server private key
[Thu Apr 04 23:35:55 2013] [error] SSL Library Error: 185073780 error:0B080074:x509 certificate routines:X509_check_private_key:key values mismatch
[Thu Apr 04 23:36:39 2013] [warn] RSA server certificate CommonName (CN) `truckstop24.no' does NOT match server name!?
[Thu Apr 04 23:36:39 2013] [error] Unable to configure RSA server private key
[Thu Apr 04 23:36:39 2013] [error] SSL Library Error: 185073780 error:0B080074:x509 certificate routines:X509_check_private_key:key values mismatch
[/PHP]


Thanks for reading

---

### Post by AvengerX9 on 2013-04-04
I did this to make the certificate

```

sudo openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout /etc/apache2/ssl/apache.key -out /etc/apache2/ssl/apache.crt

```

---

### Post by AvengerX9 on 2013-04-04
I fixed it. Had to add the ServerName line into the /etc/apache2/ssl/default-ssl file just like I did in the /etc/apache2/ssl/default file 

Also added the line NameVirtualHost *:443 to the /etc/apache2/ports.conf file


but still my site comes up with an risky https. Anyone know why that happends ?

---

### Post by AvengerX9 on 2013-04-05
Okay, well I managed to get my apache server started again. Tried to obtain a ssl certificate over again using this way
[http://www.zoharbabin.com/install-ssl-on-ubuntu-and-enable-https](http://www.zoharbabin.com/install-ssl-on-ubuntu-and-enable-https)

Still have problems. I have the https part on the site, but it wont load anything. Just getting a 404 not found page.

This is my **/etc/apache2/ssl/default**

> 
<VirtualHost *:443>
	ServerName truckstop24.no:443

	SSLEngine on
	SSLCertificateFile /etc/apache2/ssl/server.crt
	SSLCertificateKeyFile /etc/apache2/ssl/server.key
</VirtualHost>

<VirtualHost *:80>
	ServerAdmin webmaster@localhost
	ServerName truckstop24.no:80

	DocumentRoot /var/www
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /var/www/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride All
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


</VirtualHost>



and my This is my **/etc/apache2/ssl/default-ssl**
> 
<IfModule mod_ssl.c>
<VirtualHost _default_:443>
	ServerAdmin webmaster@localhost
	ServerName truckstop24.no:443

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
	#   If both key and certificate are stored in the same file, only the
	#   SSLCertificateFile directive is needed.
	#SSLCertificateFile    /etc/ssl/certs/ssl-cert-snakeoil.pem
	#SSLCertificateKeyFile /etc/ssl/private/ssl-cert-snakeoil.key
	SSLCertificateFile    /etc/apache2/ssl/apache.pem
	SSLCertificateKeyFile /etc/apache2/ssl/apache.key

	#   Server Certificate Chain:
	#   Point SSLCertificateChainFile at a file containing the
	#   concatenation of PEM encoded CA certificates which form the
	#   certificate chain for the server certificate. Alternatively
	#   the referenced file can be the same as SSLCertificateFile
	#   when the CA certificates are directly appended to the server
	#   certificate for convinience.
	#SSLCertificateChainFile /etc/apache2/ssl.crt/server-ca.crt

	#   Certificate Authority (CA):
	#   Set the CA certificate verification path where to find CA
	#   certificates for client authentication or alternatively one
	#   huge file containing all of them (file must be PEM encoded)
	#   Note: Inside SSLCACertificatePath you need hash symlinks
	#         to point to the certificate files. Use the provided
	#         Makefile to update the hash symlinks after changes.
	#SSLCACertificatePath /etc/ssl/certs/
	#SSLCACertificateFile /etc/apache2/ssl.crt/ca-bundle.crt

	#   Certificate Revocation Lists (CRL):
	#   Set the CA revocation path where to find CA CRLs for client
	#   authentication or alternatively one huge file containing all
	#   of them (file must be PEM encoded)
	#   Note: Inside SSLCARevocationPath you need hash symlinks
	#         to point to the certificate files. Use the provided
	#         Makefile to update the hash symlinks after changes.
	#SSLCARevocationPath /etc/apache2/ssl.crl/
	#SSLCARevocationFile /etc/apache2/ssl.crl/ca-bundle.crl

	#   Client Authentication (Type):
	#   Client certificate verification type and depth.  Types are
	#   none, optional, require and optional_no_ca.  Depth is a
	#   number which specifies how deeply to verify the certificate
	#   issuer chain before deciding the certificate is not valid.
	#SSLVerifyClient require
	#SSLVerifyDepth  10

	#   Access Control:
	#   With SSLRequire you can do per-directory access control based
	#   on arbitrary complex boolean expressions containing server
	#   variable checks and other lookup directives.  The syntax is a
	#   mixture between C and Perl.  See the mod_ssl documentation
	#   for more details.
	#<Location />
	#SSLRequire (    %{SSL_CIPHER} !~ m/^(EXP|NULL)/ \
	#            and %{SSL_CLIENT_S_DN_O} eq "Snake Oil, Ltd." \
	#            and %{SSL_CLIENT_S_DN_OU} in {"Staff", "CA", "Dev"} \
	#            and %{TIME_WDAY} >= 1 and %{TIME_WDAY} <= 5 \
	#            and %{TIME_HOUR} >= 8 and %{TIME_HOUR} <= 20       ) \
	#           or %{REMOTE_ADDR} =~ m/^192\.76\.162\.[0-9]+$/
	#</Location>

	#   SSL Engine Options:
	#   Set various options for the SSL engine.
	#   o FakeBasicAuth:
	#     Translate the client X.509 into a Basic Authorisation.  This means that
	#     the standard Auth/DBMAuth methods can be used for access control.  The
	#     user name is the `one line' version of the client's X.509 certificate.
	#     Note that no password is obtained from the user. Every entry in the user
	#     file needs this password: `xxj31ZMTZzkVA'.
	#   o ExportCertData:
	#     This exports two additional environment variables: SSL_CLIENT_CERT and
	#     SSL_SERVER_CERT. These contain the PEM-encoded certificates of the
	#     server (always existing) and the client (only existing when client
	#     authentication is used). This can be used to import the certificates
	#     into CGI scripts.
	#   o StdEnvVars:
	#     This exports the standard SSL/TLS related `SSL_*' environment variables.
	#     Per default this exportation is switched off for performance reasons,
	#     because the extraction step is an expensive operation and is usually
	#     useless for serving static content. So one usually enables the
	#     exportation for CGI and SSI requests only.
	#   o StrictRequire:
	#     This denies access when "SSLRequireSSL" or "SSLRequire" applied even
	#     under a "Satisfy any" situation, i.e. when it applies access is denied
	#     and no other module can change it.
	#   o OptRenegotiate:
	#     This enables optimized SSL connection renegotiation handling when SSL
	#     directives are used in per-directory context.
	#SSLOptions +FakeBasicAuth +ExportCertData +StrictRequire
	<FilesMatch "\.(cgi|shtml|phtml|php)$">
		SSLOptions +StdEnvVars
	</FilesMatch>
	<Directory /usr/lib/cgi-bin>
		SSLOptions +StdEnvVars
	</Directory>

	#   SSL Protocol Adjustments:
	#   The safe and default but still SSL/TLS standard compliant shutdown
	#   approach is that mod_ssl sends the close notify alert but doesn't wait for
	#   the close notify alert from client. When you need a different shutdown
	#   approach you can use one of the following variables:
	#   o ssl-unclean-shutdown:
	#     This forces an unclean shutdown when the connection is closed, i.e. no
	#     SSL close notify alert is send or allowed to received.  This violates
	#     the SSL/TLS standard but is needed for some brain-dead browsers. Use
	#     this when you receive I/O errors because of the standard approach where
	#     mod_ssl sends the close notify alert.
	#   o ssl-accurate-shutdown:
	#     This forces an accurate shutdown when the connection is closed, i.e. a
	#     SSL close notify alert is send and mod_ssl waits for the close notify
	#     alert of the client. This is 100% SSL/TLS standard compliant, but in
	#     practice often causes hanging connections with brain-dead browsers. Use
	#     this only for browsers where you know that their SSL implementation
	#     works correctly.
	#   Notice: Most problems of broken clients are also related to the HTTP
	#   keep-alive facility, so you usually additionally want to disable
	#   keep-alive for those clients, too. Use variable "nokeepalive" for this.
	#   Similarly, one has to force some clients to use HTTP/1.0 to workaround
	#   their broken HTTP/1.1 implementation. Use variables "downgrade-1.0" and
	#   "force-response-1.0" for this.
	BrowserMatch "MSIE [2-6]" \
		nokeepalive ssl-unclean-shutdown \
		downgrade-1.0 force-response-1.0
	# MSIE 7 and newer should be able to use keepalive
	BrowserMatch "MSIE [17-9]" ssl-unclean-shutdown

</VirtualHost>
</IfModule>



and lastly the **/etc/apache2/ports.conf**

> 
# If you just change the port or add more ports here, you will likely also
# have to change the VirtualHost statement in
# /etc/apache2/sites-enabled/000-default
# This is also true if you have upgraded from before 2.2.9-3 (i.e. from
# Debian etch). See /usr/share/doc/apache2.2-common/NEWS.Debian.gz and
# README.Debian.gz

NameVirtualHost *:80
Listen 80

<IfModule mod_ssl.c>
    # If you add NameVirtualHost *:443 here, you will also have to change
    # the VirtualHost statement in /etc/apache2/sites-available/default-ssl
    # to <VirtualHost *:443>
    # Server Name Indication for SSL named virtual hosts is currently not
    # supported by MSIE on Windows XP.
    NameVirtualHost *:443
    Listen 443
</IfModule>

<IfModule mod_gnutls.c>
    Listen 443
</IfModule>



---

### Post by Azrayal on 2013-04-05
Hi,

What are the apache logs saying when you try access the site?

Also your cert is listed as:
SSLCertificateFile /etc/apache2/ssl/apache.pem
SSLCertificateKeyFile /etc/apache2/ssl/apache.key

shouldnt it be .crt instead of .pem?

---

### Post by AvengerX9 on 2013-04-05
I was just looking at the apache access and error log and there is nothing there about this issue as I can see. You might be right about the extension of the certificates, I don't really know what is right, just followed the tutorials step by step and this is what I came up with :)

Edit: Right now it says server.crt and server.key on those two lines, but there is no changes.

---

### Post by AvengerX9 on 2013-04-05
Changed the /etc/apache2/sites/available/default now to this and the https works, but not the http anymore **(still with an unverified identity)**

> 
<VirtualHost *:80>
	ServerName truckstop24.no

</VirtualHost>

<VirtualHost *:443>
	ServerAdmin webmaster@localhost
	ServerName truckstop24.no:443

	DocumentRoot /var/www
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /var/www/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride All
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


	SSLEngine on
	SSLCertificateFile /etc/apache2/ssl/server.crt
	SSLCertificateKeyFile /etc/apache2/ssl/server.key

</VirtualHost>


---

### Post by AvengerX9 on 2013-04-05
Now I changed the file to this and it now works with both http and https, but still with unverified identity
> 
<VirtualHost *:443>
	ServerName truckstop24.no:443
	DocumentRoot /var/www
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /var/www/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride All
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
	SSLEngine on
	SSLCertificateFile /etc/apache2/ssl/apache.crt
	SSLCertificateKeyFile /etc/apache2/ssl/apache.key
</VirtualHost>

<VirtualHost *:80>
	ServerAdmin webmaster@localhost
	ServerName truckstop24.no:80

	DocumentRoot /var/www
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /var/www/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride All
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



</VirtualHost>


---

### Post by Cheesemill on 2013-04-06
Is this a self-signed certificate?
If so then it's to be expected that it's unverified.

To get an official verified SSL certificate you have to purchase it from a CA.

---

### Post by AvengerX9 on 2013-04-06
its self signed :), well buying one is expensive so I dont really need that. Also facebook fan pages tabs requires ssl thats why I need it

---

### Post by CharlesA on 2013-04-07
> **AvengerX9 said:**
> its self signed :), well buying one is expensive so I dont really need that. Also facebook fan pages tabs requires ssl thats why I need it

Are you trying to host the site yourself? I thought everything on facebook was contained on their servers.

Anyway, if you don't want to use a self-signed cert, check out [StartSSL]("https://www.startssl.com/"). I am currently using their free SSL certs for my site, but if you want a class two cert, a two year one is 60 bucks.

---

### Post by AvengerX9 on 2013-04-07
Thanks. I think I figured out a way to host the chat. Using Woobox here [http://woobox.com/](http://woobox.com/)

---

