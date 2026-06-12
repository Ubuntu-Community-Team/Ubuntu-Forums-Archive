---
title: "Apache, port 443 working, port 80 not"
date: 2012-04-30
forum: Server Platforms
---

### Post by maxnutter on 2012-04-30
Hi,

I've got a bit of an odd problem with my server. Initially, I was doing everything through port 80, but I wanted to add a bit of security, so set up https and port 403. Now port 80 access is failing! Both ports are still open.

My setup:

httpd.conf:
[PHP]
Options +Indexes 
Options All 

ServerName localhost 
[/PHP]

ports.conf:
[PHP]
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
[/PHP]

sites-available/default:
[PHP]
<VirtualHost *:80>
  ServerAdmin webmaster@localhost

  DocumentRoot /var/www
  <Directory />
    Options FollowSymLinks
    AllowOverride All
  </Directory>

  <Directory /var/www/>
    Options Indexes FollowSymLinks MultiViews
    AllowOverride None
    Order allow,deny
    allow from all
  </Directory>
  
  <Directory /var/www/py>
    AddHandler mod_python .py
    PythonHandler hello
    PythonDebug On
  </Directory>

  <Proxy *>
    Order deny,allow
    Allow from all
  </Proxy>

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

  include includes/common.conf

</VirtualHost>
[/PHP]

sites-available/default-ssl:
[PHP]
<IfModule mod_ssl.c>
<VirtualHost *:443>
	ServerAdmin webmaster@localhost

	DocumentRoot /var/www/https
	<Directory />
		Options FollowSymLinks
		AllowOverride None
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
       SSLCertificateFile /etc/apache2/ssl/server.crt
       SSLCertificateKeyFile /etc/apache2/ssl/server.key

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

       include includes/common.conf

</VirtualHost>
</IfModule>
[/PHP]

includes/common.conf:
[PHP]
<Location /shell>
  ProxyPass http://localhost:4200/
  ProxyPassReverse http://localhost:4200/
</Location>
[/PHP]

Both default and default-ssl have been added via a2ensite, and are present in sites-enabled.

So, navigating to [http://www.mydomain.com](http://www.mydomain.com) will fail, but [https://www.mydomain.com/shell/](https://www.mydomain.com/shell/) works fine.

Any help on where I am going wrong would be gratefully received!
Thanks!

---

### Post by ruffEdgz on 2012-04-30
When looking over the conf files, nothing looks out of place but if I was trying to troubleshoot this myself, I would make sure to do the following:

[LIST]
[*]Check IPTables (if applicable)
[*]Network ports are open
[*]Files have the correct permissions for them to be viewed
[/LIST]

Also, when you say 'fail', do you mean it comes up with an Apache Error? If you do get an error, what number do you get?

---

### Post by maxnutter on 2012-04-30
> **ruffEdgz said:**
> When looking over the conf files, nothing looks out of place but if I was trying to troubleshoot this myself, I would make sure to do the following:

[LIST]
[*]Check IPTables (if applicable)
[*]Network ports are open
[*]Files have the correct permissions for them to be viewed
[/LIST]

Also, when you say 'fail', do you mean it comes up with an Apache Error? If you do get an error, what number do you get?

Thanks for the reply!

IPTables gives:
```

Chain INPUT (policy ACCEPT)                                                                                                                                                                                                                       
target     prot opt source               destination                                                                                                                                                                                              
                                                                                                                                                                                                                                                  
Chain FORWARD (policy ACCEPT)                                                                                                                                                                                                                     
target     prot opt source               destination                                                                                                                                                                                              
                                                                                                                                                                                                                                                  
Chain OUTPUT (policy ACCEPT)                                                                                                                                                                                                                      
target     prot opt source               destination 
```

The ports are open and being listened to.

[https://www.myserver.com](https://www.myserver.com) works, but [http://www.myserver.com](http://www.myserver.com) gives an "Oops! Google Chrome could not connect to www.myserver.com" message.

---

### Post by ruffEdgz on 2012-04-30
When looking over the conf files again, I was curious if you use any .htaccess files in either /var/ or /var/www/? I noticed that the port 80 conf file had AllowOverride set to 'all' which means that any .htaccess files will override the current config file.

[http://httpd.apache.org/docs/2.2/mod/core.html#allowoverride](http://httpd.apache.org/docs/2.2/mod/core.html#allowoverride)

---

### Post by maxnutter on 2012-04-30
> **ruffEdgz said:**
> When looking over the conf files again, I was curious if you use any .htaccess files in either /var/ or /var/www/? I noticed that the port 80 conf file had AllowOverride set to 'all' which means that any .htaccess files will override the current config file.

[http://httpd.apache.org/docs/2.2/mod/core.html#allowoverride](http://httpd.apache.org/docs/2.2/mod/core.html#allowoverride)

I don't have any .htaccess files anywhere, but regardless of that, you are correct so I have changed it to 'None' and restarted apache... no change!

it's like the 443 VirtualHost is overriding the one for port 80!

---

### Post by ruffEdgz on 2012-04-30
If that's what you think, it wouldn't hurt to watch the log files on your Apache server. I would just do the following command to watch the error log file while you are trying to connect to port 80:
```

sudo tail -f /var/log/apache2/error.log

```
or you can also watch the access logs as well:
```

sudo tail -f /var/log/apache2/access.log

```
To me, it just sounds like the default.conf file has a deny blocking that request since you can have both 80 and 443 requests be requested on a server. I just started up a default instance of a web server and added the SSL conf as well without any issues. It opened on both 80 and 443.

Let us know more about what you find in the logs if there is anything to share.

---

### Post by maxnutter on 2012-04-30
> **ruffEdgz said:**
> If that's what you think, it wouldn't hurt to watch the log files on your Apache server. I would just do the following command to watch the error log file while you are trying to connect to port 80:
```

sudo tail -f /var/log/apache2/error.log

```
or you can also watch the access logs as well:
```

sudo tail -f /var/log/apache2/access.log

```
To me, it just sounds like the default.conf file has a deny blocking that request since you can have both 80 and 443 requests be requested on a server. I just started up a default instance of a web server and added the SSL conf as well without any issues. It opened on both 80 and 443.

Let us know more about what you find in the logs if there is anything to share.

error.log:
```

[Tue May 01 00:29:22 2012] [warn] RSA server certificate CommonName (CN) `*******' does NOT match server name!?                                                                                    
[Tue May 01 00:29:22 2012] [warn] Init: Name-based SSL virtual hosts only work for clients with TLS server name indication support (RFC 4366)                                                           
[Tue May 01 00:29:22 2012] [notice] Apache/2.2.20 (Ubuntu) mod_python/3.3.1 Python/2.7.2+ mod_ssl/2.2.20 OpenSSL/1.0.0e configured -- resuming normal operations     

```

access.log:
```

xx.xx.xx.xx - - [30/Apr/2012:11:59:29 +0100] "\x16\x03" 501 288 "-" "-"                            
xx.xx.xx.xx - - [30/Apr/2012:11:59:29 +0100] "\x16\x03" 501 288 "-" "-"                            
xx.xx.xx.xx - - [30/Apr/2012:11:59:29 +0100] "\x16\x03" 501 288 "-" "-"                            
xx.xx.xx.xx - - [30/Apr/2012:11:59:29 +0100] "\x16\x03" 501 288 "-" "-"                            
xx.xx.xx.xx - - [30/Apr/2012:11:59:40 +0100] "\x16\x03" 501 288 "-" "-"                            
xx.xx.xx.xx - - [30/Apr/2012:11:59:40 +0100] "\x16\x03" 501 288 "-" "-"                            
xx.xx.xx.xx - - [30/Apr/2012:11:59:40 +0100] "\x16\x03" 501 288 "-" "-"                            
xx.xx.xx.xx - - [30/Apr/2012:11:59:40 +0100] "\x16\x03" 501 288 "-" "-"                            
xx.xx.xx.xx - - [30/Apr/2012:11:59:40 +0100] "\x16\x03" 501 288 "-" "-"                            
xx.xx.xx.xx - - [30/Apr/2012:11:59:40 +0100] "\x16\x03" 501 288 "-" "-"  

```

none of these coincide with attempted connection to port 80 though...

---

### Post by maxnutter on 2012-05-03
Update on this issue:

I've upgraded to Ubuntu 12.04 and the problem has gone away, both port 80 and 443 are working fine!
I've no idea how this has been fixed, but I'm not complaining and I'll mark this as solved.

Thanks for the help!

---

