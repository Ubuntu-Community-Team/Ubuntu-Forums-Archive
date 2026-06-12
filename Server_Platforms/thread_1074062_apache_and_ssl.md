---
title: "apache and ssl?"
date: 2009-02-18
forum: Server Platforms
---

### Post by rhcm123 on 2009-02-18
I am very confused. Because my ISP blocks port 80, i've been having to route all http traffic through port 8080. i decided for 3 reasons that i wanted to route all traffic through https (443) because of the following:

1. I really don't want people eavesdropping on my traffic
2. I just installed squirrelmail and i don't want people reading my passwords (i'll get back to this in a sec)
3. My ISP does not block 443.

In case you haven't guessed, it doesn't work. :). I know that apache and it's ssl module are working cause i can access the webmin module on port 10000 (and i get the firefox warning about a self-signed certificate.)

I want to get all files in /var/www (i keep photos, etc in there) and /usr/share/squirrelmail/src (for online email). I was told that i would have to make virtual servers, but i have no clue how to do that. halp!!!

---

### Post by spiderbatdad on 2009-02-18
Have a look through this: [http://www.onlamp.com/pub/a/onlamp/2008/03/04/step-by-step-configuring-ssl-under-apache.html](http://www.onlamp.com/pub/a/onlamp/2008/03/04/step-by-step-configuring-ssl-under-apache.html)

basically, creating virtual hosts is done in the file /etc/apache2/sites-available/your_site. You will have to create the folder "your_site" or whatever you want to call it. Copy the default site into your site, as a template and then edit the file to meet your needs. It will probably take a little google work to resolve the issues you encounter. If you are also hosting SM, I suggest making that the first vhost. I find it easiest to register more than one name...so: example1.com, examplemail.com, and so forth.

---

### Post by rhcm123 on 2009-02-18
> **spiderbatdad said:**
> Have a look through this: [http://www.onlamp.com/pub/a/onlamp/2008/03/04/step-by-step-configuring-ssl-under-apache.html](http://www.onlamp.com/pub/a/onlamp/2008/03/04/step-by-step-configuring-ssl-under-apache.html)

basically, creating virtual hosts is done in the file /etc/apache2/sites-available/your_site. You will have to create the folder "your_site" or whatever you want to call it. Copy the default site into your site, as a template and then edit the file to meet your needs. It will probably take a little google work to resolve the issues you encounter. If you are also hosting SM, I suggest making that the first vhost. I find it easiest to register more than one name...so: example1.com, examplemail.com, and so forth.

I take it SM stands for SquirrelMail :).
can i make virtual hosts with webmin? If so, how?

And if i make a virtual host (e.g. your_site) and cp /var/www/ into... where?

---

### Post by spiderbatdad on 2009-02-18
I have never tried to use webmin.
The simple way to create virtual hosts is launch your browser with super user privs. Note this is not standard, but it gets you away from cli a little bit.
```
gksu nautilus
```will launch your file browser as super user. You have to be careful not to open all kinds of files and accidentally/on purpose go editing the root file system...you can break your system.

Once the bowser is open, navigate to file system> /etc/apache2/sites-available. Right click and select create a document...name it. Now copy and paste default into your_site. Then edit the file appropriately...your ServerName, DocumentRoot, etc...etc.
To use the new sites, you have to tell apache to disable the default site and use your_site:
```
sudo a2dissite default && sudo a2ensite your_site
```

then restart the server:```
sudo /etc/init.d/apache2 restart
```

I think I understand the original question finally...There is no need to move the files in your document root just because you are changing the port apache listens on.

---

### Post by rhcm123 on 2009-02-18
> **spiderbatdad said:**
> I have never tried to use webmin.
The simple way to create virtual hosts is launch your browser with super user privs. Note this is not standard, but it gets you away from cli a little bit.
```
gksu nautilus
```will launch your file browser as super user. You have to be careful not to open all kinds of files and accidentally/on purpose go editing the root file system...you can break your system.

Once the bowser is open, navigate to file system> /etc/apache2/sites-available. Right click and select create a document...name it. Now copy and paste default into your_site. Then edit the file appropriately...your ServerName, DocumentRoot, etc...etc.
To use the new sites, you have to tell apache to disable the default site and use your_site:
```
sudo a2dissite default && sudo a2ensite your_site
```

then restart the server:```
sudo /etc/init.d/apache2 restart
```

Alright, i did as you said, and i created a site called main-ssl, and i edited it as such:```
<IfModule mod_ssl.c>
<VirtualHost _default_:443>
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

	CustomLog /var/log/apache2/ssl_access.log combined

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
	SSLCertificateFile    /etc/ssl/certs/ssl-cert-snakeoil.pem
	SSLCertificateKeyFile /etc/ssl/private/ssl-cert-snakeoil.key

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
	BrowserMatch ".*MSIE.*" \
		nokeepalive ssl-unclean-shutdown \
		downgrade-1.0 force-response-1.0

</VirtualHost>
</IfModule>

```

but whenever i navigate to [https://(omitted](https://(omitted), it's my last name).dyndns.org, it just says "failed to connect"

---

### Post by spiderbatdad on 2009-02-18
a basic vitual host might look like this...assuming you were using authorization:
```
<VirtualHost myDomain.org:443>
        ServerAdmin myEmail@gmail.com
        ServerName myDomain.org

        DocumentRoot /var/www/
		SSLEngine On
        <Directory />
                AuthType Basic
                AuthName "Restricted Files"
                AuthUserFile /home/myuser/.htpasswords
                Require valid-user
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>
        LogLevel warn

        CustomLog /var/log/apache2/access.log combined
        ServerSignature On
</VirtualHost>

```
ssl directives i keep in httpd.conf
```
ServerName myDomain.org
<Directory /var/www>
 <IfModule mod_rewrite.c>
        <IfModule mod_ssl.c>
#       <Location /squirrelmail>
                RewriteEngine on
                RewriteCond %{HTTPS} !^on$ [NC]
                RewriteRule . https://%{HTTP_HOST}%{REQUEST_URI}  [L]
#       </Location>
        </IfModule>
        </IfModule>


SSLOptions +StrictRequire
</Directory>

SSLProtocol -all +TLSv1 +SSLv3
SSLCipherSuite HIGH:MEDIUM:!aNULL:+SHA1:+MD5:+HIGH:+MEDIUM

<Directory /usr/local/apache2/htdocs>
# but finally deny all browsers which haven't upgraded
SSLRequire %{SSL_CIPHER_USEKEYSIZE} >= 128
</Directory> 

#SSLPassPhraseDialog builtin
SSLCertificateFile /etc/apache2/ssl.crt/server.crt
SSLCertificateKeyFile /etc/apache2/ssl.key/server.key

SSLVerifyClient none
SSLProxyEngine off

```
SM commented out cause I'm not using it now. You have to remember to make sure ports.conf is listening on 443, ```
 <IfModule mod_ssl.c>
    Listen 443
</IfModule>

``` port forward 443, make sure your firewall isnt blocking it...restart your server.

---

### Post by spiderbatdad on 2009-02-18
your browser address should be "htpps" http will cause a site not found, the rewrite rule in httpd.conf should fix that for you.

---

### Post by rhcm123 on 2009-02-18
Ok i generated an RSA key and made the directory /etc/apache2/ssl.key, then copied the key into said directory. I commented out the CA certificate line cause I'm the only one who is going to be using this site. not really worth getting a CA to sighn this.

however, now, when i run /etc/init.d/apache2 restart it simply says [fail]. No error output, just fail. I know it isn't stopped, as i can go to my other non-ssl sites and they work fine.

am i doing somthing wrong? :(

---

### Post by windependence on 2009-02-18
FYI, Wenmin uses it's own http server, not Apache so just because that one is working does not mean your Apache configuration is working.

If you are going to host your site on 443, all you have to do is change the port in your configuration file.

```
sudo nano /etc/apache2/ports.conf
```

Change the listen directive to this:

```
LISTEN *:443
```

Then, restart Apache:

```
sudo /etc/init.d/apache2 restart
```

Your server will now listen only on port 443.

-Tim

---

### Post by spiderbatdad on 2009-02-18
mmm. i believe you still have to have the ca...it is just going to be self-signed. Your browser will complain and you will have to "add an exception."

---

### Post by windependence on 2009-02-18
> **rhcm123 said:**
> Ok i generated an RSA key and made the directory /etc/apache2/ssl.key, then copied the key into said directory. I commented out the CA certificate line cause I'm the only one who is going to be using this site. not really worth getting a CA to sighn this.

however, now, when i run /etc/init.d/apache2 restart it simply says [fail]. No error output, just fail. I know it isn't stopped, as i can go to my other non-ssl sites and they work fine.

am i doing somthing wrong? :(

To see what's going on do:

```
cat /var/log/apache2/error.log
```

Post it here and we'll take a look.

-Tim

---

### Post by rhcm123 on 2009-02-19
> **windependence said:**
> To see what's going on do:

```
cat /var/log/apache2/error.log
```

Post it here and we'll take a look.

-Tim

Sorry about this output being verbose, i was toying around with different settings last night, and was restarting the server alot.

In case i did not make myself clear in what i want to accomplish (which happens alot :) ) i want to STOP apache using HTTP (listening on ports 80/8080) and START apache using HTTPS (listening on the standard port 443)

This is what /var/log/apache2/error.log states:
```
[Mon Feb 16 15:08:37 2009] [notice] Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.1 with Suhosin-Patch configured -- resuming normal operations
[Mon Feb 16 15:40:51 2009] [notice] caught SIGWINCH, shutting down gracefully
[Mon Feb 16 15:43:49 2009] [notice] Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.1 with Suhosin-Patch configured -- resuming normal operations
[Mon Feb 16 16:22:42 2009] [error] [client 192.168.2.102] File does not exist: /var/www/favicon.ico
[Mon Feb 16 16:22:45 2009] [error] [client 192.168.2.102] File does not exist: /var/www/favicon.ico
[Tue Feb 17 01:22:37 2009] [error] [client 66.246.218.29] File does not exist: /var/www/samair_test.htm
[Wed Feb 18 12:50:29 2009] [notice] Graceful restart requested, doing restart
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Wed Feb 18 12:50:33 2009] [notice] Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.5 with Suhosin-Patch configured -- resuming normal operations
[Wed Feb 18 15:57:22 2009] [notice] caught SIGWINCH, shutting down gracefully
[Wed Feb 18 17:02:51 2009] [notice] Apache/2.2.9 (Ubuntu) PHP/5.2.6-2ubuntu4.1 with Suhosin-Patch configured -- resuming normal operations
[Wed Feb 18 17:04:28 2009] [notice] Graceful restart requested, doing restart
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Wed Feb 18 17:04:30 2009] [notice] Apache/2.2.9 (Ubuntu) PHP/5.2.6-2ubuntu4.1 with Suhosin-Patch configured -- resuming normal operations
[Wed Feb 18 17:17:46 2009] [notice] caught SIGTERM, shutting down
[Wed Feb 18 17:20:04 2009] [notice] Apache/2.2.9 (Ubuntu) PHP/5.2.6-2ubuntu4.1 with Suhosin-Patch configured -- resuming normal operations
[Wed Feb 18 18:03:08 2009] [notice] Graceful restart requested, doing restart
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Wed Feb 18 18:03:10 2009] [notice] Apache/2.2.9 (Ubuntu) PHP/5.2.6-2ubuntu4.1 with Suhosin-Patch configured -- resuming normal operations
[Wed Feb 18 18:04:09 2009] [error] [client 192.168.2.1] File does not exist: /htdocs
[Wed Feb 18 18:04:10 2009] [error] [client 192.168.2.1] File does not exist: /htdocs
[Wed Feb 18 18:04:13 2009] [error] [client 192.168.2.1] File does not exist: /htdocs
[Wed Feb 18 18:04:18 2009] [error] [client 192.168.2.1] Invalid method in request \x16\x03\x01
[Wed Feb 18 18:04:19 2009] [error] [client 192.168.2.1] Invalid method in request \x16\x03\x01
[Wed Feb 18 18:04:22 2009] [error] [client 192.168.2.1] Invalid method in request \x16\x03\x01
[Wed Feb 18 18:04:30 2009] [notice] Graceful restart requested, doing restart
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Wed Feb 18 18:04:31 2009] [notice] Apache/2.2.9 (Ubuntu) PHP/5.2.6-2ubuntu4.1 with Suhosin-Patch configured -- resuming normal operations
[Wed Feb 18 18:04:39 2009] [notice] caught SIGTERM, shutting down
[Wed Feb 18 18:04:40 2009] [notice] Apache/2.2.9 (Ubuntu) PHP/5.2.6-2ubuntu4.1 with Suhosin-Patch configured -- resuming normal operations
[Wed Feb 18 18:06:30 2009] [notice] caught SIGTERM, shutting down
[Wed Feb 18 18:06:31 2009] [notice] Apache/2.2.9 (Ubuntu) PHP/5.2.6-2ubuntu4.1 with Suhosin-Patch configured -- resuming normal operations
[Wed Feb 18 18:06:37 2009] [error] [client 192.168.2.1] File does not exist: /htdocs
[Wed Feb 18 18:08:27 2009] [notice] caught SIGTERM, shutting down
[Wed Feb 18 18:08:29 2009] [notice] Apache/2.2.9 (Ubuntu) PHP/5.2.6-2ubuntu4.1 with Suhosin-Patch configured -- resuming normal operations
[Wed Feb 18 18:08:42 2009] [error] [client 192.168.2.1] File does not exist: /htdocs
[Wed Feb 18 18:08:46 2009] [error] [client 192.168.2.1] File does not exist: /htdocs
[Wed Feb 18 18:08:48 2009] [error] [client 192.168.2.1] File does not exist: /htdocs
[Wed Feb 18 18:08:50 2009] [error] [client 192.168.2.1] File does not exist: /htdocs
[Wed Feb 18 18:08:50 2009] [error] [client 192.168.2.1] File does not exist: /htdocs
[Wed Feb 18 18:08:51 2009] [error] [client 192.168.2.1] File does not exist: /htdocs
[Wed Feb 18 18:08:51 2009] [error] [client 192.168.2.1] File does not exist: /htdocs
[Wed Feb 18 18:08:52 2009] [error] [client 192.168.2.1] File does not exist: /htdocs
[Wed Feb 18 18:08:52 2009] [error] [client 192.168.2.1] File does not exist: /htdocs
[Wed Feb 18 18:08:53 2009] [error] [client 192.168.2.1] File does not exist: /htdocs
[Wed Feb 18 18:08:53 2009] [error] [client 192.168.2.1] File does not exist: /htdocs
[Wed Feb 18 18:08:54 2009] [error] [client 192.168.2.1] File does not exist: /htdocs
[Wed Feb 18 18:08:54 2009] [error] [client 192.168.2.1] File does not exist: /htdocs
[Wed Feb 18 18:08:55 2009] [error] [client 192.168.2.1] File does not exist: /htdocs
[Wed Feb 18 18:08:55 2009] [error] [client 192.168.2.1] File does not exist: /htdocs
[Wed Feb 18 18:08:56 2009] [error] [client 192.168.2.1] File does not exist: /htdocs
[Wed Feb 18 18:08:56 2009] [error] [client 192.168.2.1] File does not exist: /htdocs
[Wed Feb 18 18:08:57 2009] [error] [client 192.168.2.1] File does not exist: /htdocs
[Wed Feb 18 18:08:57 2009] [error] [client 192.168.2.1] File does not exist: /htdocs
[Wed Feb 18 18:09:06 2009] [error] [client 192.168.2.1] File does not exist: /htdocs
[Wed Feb 18 19:34:25 2009] [error] [client 192.168.2.1] File does not exist: /htdocs
[Wed Feb 18 19:37:23 2009] [error] [client 192.168.2.1] File does not exist: /htdocs
[Wed Feb 18 19:37:23 2009] [error] [client 192.168.2.1] File does not exist: /htdocs
[Wed Feb 18 19:37:26 2009] [error] [client 192.168.2.1] File does not exist: /htdocs
[Wed Feb 18 19:37:26 2009] [error] [client 192.168.2.1] File does not exist: /htdocs
[Wed Feb 18 19:37:26 2009] [error] [client 192.168.2.1] File does not exist: /htdocs
[Wed Feb 18 19:37:26 2009] [error] [client 192.168.2.1] File does not exist: /htdocs
[Wed Feb 18 19:38:02 2009] [notice] caught SIGTERM, shutting down
[Wed Feb 18 19:38:04 2009] [notice] Apache/2.2.9 (Ubuntu) PHP/5.2.6-2ubuntu4.1 with Suhosin-Patch configured -- resuming normal operations
[Wed Feb 18 19:41:00 2009] [notice] caught SIGTERM, shutting down
[Wed Feb 18 19:41:01 2009] [notice] Apache/2.2.9 (Ubuntu) PHP/5.2.6-2ubuntu4.1 with Suhosin-Patch configured -- resuming normal operations
[Wed Feb 18 19:41:41 2009] [notice] caught SIGTERM, shutting down
[Wed Feb 18 19:41:42 2009] [notice] Apache/2.2.9 (Ubuntu) PHP/5.2.6-2ubuntu4.1 with Suhosin-Patch configured -- resuming normal operations
[Wed Feb 18 21:58:55 2009] [notice] caught SIGTERM, shutting down
[Wed Feb 18 21:58:57 2009] [notice] Apache/2.2.9 (Ubuntu) PHP/5.2.6-2ubuntu4.1 with Suhosin-Patch configured -- resuming normal operations
[Wed Feb 18 22:05:28 2009] [notice] caught SIGTERM, shutting down
[Wed Feb 18 22:05:30 2009] [notice] Apache/2.2.9 (Ubuntu) PHP/5.2.6-2ubuntu4.1 with Suhosin-Patch configured -- resuming normal operations
[Wed Feb 18 22:06:09 2009] [error] [client 192.168.2.1] Invalid method in request \x16\x03\x01
[Wed Feb 18 22:06:09 2009] [error] [client 192.168.2.1] Invalid method in request \x16\x03\x01
[Wed Feb 18 22:06:12 2009] [error] [client 192.168.2.1] Invalid method in request \x16\x03\x01
[Wed Feb 18 22:08:09 2009] [notice] Graceful restart requested, doing restart
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Wed Feb 18 22:08:10 2009] [notice] Apache/2.2.9 (Ubuntu) PHP/5.2.6-2ubuntu4.1 with Suhosin-Patch configured -- resuming normal operations
[Wed Feb 18 22:18:29 2009] [notice] Graceful restart requested, doing restart
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
[Wed Feb 18 22:18:30 2009] [notice] Apache/2.2.9 (Ubuntu) PHP/5.2.6-2ubuntu4.1 with Suhosin-Patch configured -- resuming normal operations
[Wed Feb 18 22:18:40 2009] [error] [client 192.168.2.1] Invalid method in request \x16\x03\x01
[Wed Feb 18 22:18:43 2009] [error] [client 192.168.2.1] Invalid method in request \x16\x03\x01
[Wed Feb 18 22:18:43 2009] [error] [client 192.168.2.1] Invalid method in request \x16\x03\x01
[Wed Feb 18 22:18:44 2009] [error] [client 192.168.2.1] Invalid method in request \x16\x03\x01
[Wed Feb 18 22:18:45 2009] [error] [client 192.168.2.1] Invalid method in request \x16\x03\x01
[Wed Feb 18 22:20:25 2009] [error] [client 192.168.2.1] Invalid method in request \x16\x03\x01
[Wed Feb 18 22:21:14 2009] [error] [client 192.168.2.1] File does not exist: /var/www/favicon.ico
[Wed Feb 18 22:21:17 2009] [error] [client 192.168.2.1] File does not exist: /var/www/favicon.ico
[Wed Feb 18 22:32:02 2009] [notice] caught SIGTERM, shutting down
[Wed Feb 18 22:46:32 2009] [error] Server should be SSL-aware but has no certificate configured [Hint: SSLCertificateFile]
[Wed Feb 18 22:46:39 2009] [error] Server should be SSL-aware but has no certificate configured [Hint: SSLCertificateFile]
[Wed Feb 18 22:46:53 2009] [error] Server should be SSL-aware but has no certificate configured [Hint: SSLCertificateFile]
[Wed Feb 18 22:48:50 2009] [error] Server should be SSL-aware but has no certificate configured [Hint: SSLCertificateFile]
[Wed Feb 18 22:54:59 2009] [error] Server should be SSL-aware but has no certificate configured [Hint: SSLCertificateFile]

```

This is what /etc/apache2/sites-available/main-ssl looks like:
```
<VirtualHost (blank).dyndns.org:443>
        ServerAdmin ussr@(blank).dyndns.org
        ServerName (blank).dyndns.org

        DocumentRoot /var/www/
		SSLEngine On
        <Directory />
                AuthType Basic
                AuthName "Restricted Files"
                AuthUserFile /home/myuser/.htpasswords
                Require valid-user
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>
        LogLevel warn

        CustomLog /var/log/apache2/access.log combined
        ServerSignature On
</VirtualHost>

```

This is what /etc/apache2/httpd.conf looks like:
```
ServerName myDomain.org
<Directory /var/www>
 <IfModule mod_rewrite.c>
        <IfModule mod_ssl.c>
#       <Location /squirrelmail>
                RewriteEngine on
                RewriteCond %{HTTPS} !^on$ [NC]
                RewriteRule . https://%{HTTP_HOST}%{REQUEST_URI}  [L]
#       </Location>
        </IfModule>
        </IfModule>


SSLOptions +StrictRequire
</Directory>

SSLProtocol -all +TLSv1 +SSLv3
SSLCipherSuite HIGH:MEDIUM:!aNULL:+SHA1:+MD5:+HIGH:+MEDIUM

<Directory /usr/local/apache2/htdocs>
# but finally deny all browsers which haven't upgraded
SSLRequire %{SSL_CIPHER_USEKEYSIZE} >= 128
</Directory> 

#SSLPassPhraseDialog builtin
#SSLCertificateFile /etc/apache2/ssl.crt/server.crt
SSLCertificateKeyFile /etc/apache2/ssl.key/server.key

SSLVerifyClient none
SSLProxyEngine off

```

IF you see anything wrong, tell me.

---

### Post by spiderbatdad on 2009-02-19
you have to use the certificate. When you restart, enter the password you signed the certificate with.

---

### Post by rhcm123 on 2009-02-19
> **spiderbatdad said:**
> you have to use the certificate. When you restart, enter the password you signed the certificate with.

wait a minute. I've gotten myself completley lost. How do i do this and what am i missing.

---

### Post by spiderbatdad on 2009-02-19
```
 sudo openssl req -new -days 999 -keyout /etc/apache2/server.key -out /etc/apache2/server.crt


```
Make sure httpd.conf points to the same location specified above.

Then restart apache2.

According to community docs, use this command: sudo apache2-ssl-certificate -days 365
as found here: [https://help.ubuntu.com/community/forum/server/apache2/SSL](https://help.ubuntu.com/community/forum/server/apache2/SSL)

---

### Post by rhcm123 on 2009-02-19
> **spiderbatdad said:**
> ```
 sudo openssl req -new -days 999 -keyout /etc/apache2/server.key -out /etc/apache2/server.crt


```
Make sure httpd.conf points to the same location specified above.

Then restart apache2.

According to community docs, use this command: sudo apache2-ssl-certificate -days 365
as found here: [https://help.ubuntu.com/community/forum/server/apache2/SSL](https://help.ubuntu.com/community/forum/server/apache2/SSL)

I did the openssl command and pointed httpd to the proper files (i just used the locations you gave in the command. I then restarted apache2 (and got and error, as you may have guessed.

In additon, the sudo apache2-ssl-certificate command you gave returned a bash "command not found" error.

Here's the output from the error log, cut down to all of today.
```
[Thu Feb 19 21:32:11 2009] [error] Init: Unable to read server certificate from file /etc/apache2/server.crt
[Thu Feb 19 21:32:11 2009] [error] SSL Library Error: 218529960 error:0D0680A8:asn1 encoding routines:ASN1_CHECK_TLEN:wrong tag
[Thu Feb 19 21:32:11 2009] [error] SSL Library Error: 218595386 error:0D07803A:asn1 encoding routines:ASN1_ITEM_EX_D2I:nested asn1 error
[Thu Feb 19 21:35:30 2009] [error] Init: Unable to read server certificate from file /etc/apache2/server.crt
[Thu Feb 19 21:35:30 2009] [error] SSL Library Error: 218529960 error:0D0680A8:asn1 encoding routines:ASN1_CHECK_TLEN:wrong tag
[Thu Feb 19 21:35:30 2009] [error] SSL Library Error: 218595386 error:0D07803A:asn1 encoding routines:ASN1_ITEM_EX_D2I:nested asn1 error

```

---

### Post by rhcm123 on 2009-02-20
> **spiderbatdad said:**
> ```
 sudo openssl req -new -days 999 -keyout /etc/apache2/server.key -out /etc/apache2/server.crt


```
Make sure httpd.conf points to the same location specified above.

Then restart apache2.

According to community docs, use this command: sudo apache2-ssl-certificate -days 365
as found here: [https://help.ubuntu.com/community/forum/server/apache2/SSL](https://help.ubuntu.com/community/forum/server/apache2/SSL)


Ok, the guide you provided did the trick. Occams razor: simplest solution is the best. :)
Now, i got pop3s, imaps, https, all the good stuff. I ditched my 8080 port and now cruise my server encrypted on a RSA certificate. (that mozilla complains about because it's "self-signed"

I love these forums, they always stick it out and get the job done.

---

