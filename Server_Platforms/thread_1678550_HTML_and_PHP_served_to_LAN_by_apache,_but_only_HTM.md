---
title: "HTML and PHP served to LAN by apache, but only HTML served to Internet"
date: 2011-01-30
forum: Server Platforms
---

### Post by thaum16 on 2011-01-30
OS: Ubuntu 64bit 10.04 LTS Server
Problem with: apache2 and php5?

My specific problem seems unique indeed, because google/ubuntuforums doesn't seem to have anything directly related to it. I have successfully been running apache2 for quite some time now. HTML and PHP files are being served by apache on the LAN without a problem. HTML files are also being served to the net without a problem. But when I try to access a PHP file from the internet, I get a "timed out error" in the web browser! **Again, PHP files are being served on the LAN without a problem.** What on earth could be causing this? Clearly php5 is working, and apache2 is able to recognize and deliver the webpage to other computers on the LAN, but why not to the internet like HTML files?

Thank you anybody! I can't seem to get past this for the life of me!

---

### Post by koenn on 2011-01-30
what does your network look like, how is this server connected to the internet, how do you browse those pages from the lan, and how do you do it from the internet ?

how did you set up that web site - is it apache's default site or did you configure additional "virtual hosts" ?

---

### Post by thaum16 on 2011-01-30
Thank you for the quick response koenn... Please bear with me since I am a novice in most respects.

> what does your network look like, how is this server connected to the internet

I am behind a router. I have forwarded all relevant ports. Just in case, while I've been troubleshooting this issue, I made the server the DMZ. The router provides the server with an IP via Static DHCP. After giving it a static IP with /etc/hosts, windows computers had some trouble resolving it's host name, so this is why I've been using Static DHCP from my router. (btw, the OS on my linksys wr54g Linksys outer is dd-wrt)

> how do you browse those pages from the lan, and how do you do it from the internet ?

I am using the latest Firefox to browse from both the LAN and remotely on the internet.

> 
how did you set up that web site - is it apache's default site or did you configure additional "virtual hosts" ?

I installed apache2 and php5 using the ubuntu package manager. Very little has been changed with regard to the default configuration settings of apache. I followed [this guide]("http://www.tc.umn.edu/~brams006/selfsign_ubuntu.html") to setup up ssl/https without a problem. In this process, I created a directory called /var/www-ssl/html, which is where I added the PHP file to be hosted.

I'm not sure if I have virtual hosts configured or not. Would configuring ssl/https as I have in the guide I linked to above have created virtual hosts in apache? A configuration file at located at /etc/apache2/sites-enabled/000-default-ssl mentions something about a virtual host. I attached it for you to take quick look at. All this means is that I am using port 443 to broadcast webpages in https, right? Keep in mind that I don't have trouble using https to access any of the PHP files on the LAN.

**Clarification:** It may help to know that I am trying to use [Ajaxplorer]("http://www.ajaxplorer.info/wordpress/") to host my files because I want users to have the convenience of a web GUI for downloading/uploading files. However, this is not the only example of a PHP file not being served to the internet correctly, so I am pretty sure I'm not dealing with an issue related to Ajaxplorer. I am also trying to use [phpLDAPadmin]("http://phpldapadmin.sourceforge.net/wiki/index.php/Main_Page"), and it also can only be accessed from the LAN. I have searched for a way to make these applications visible to the internet in the configuration files, but no such option exists seem to exist. **Is it possible that maybe some setting in the PHP configuration needs to be enabled?**

---

### Post by thaum16 on 2011-01-30
UPDATE: Okay, so apparently I am having trouble serving HTML files as well now. I am using virtual hosts, so it must be a setting in apache or a virtual hosts file that I need to change in order to gain access on the internet. I apologize for this as it seems to change the issue at hand from the one I originally posted about. I thought that I was serving HTML files to the net because I can use Subsonic (a music streaming application being served by apache) over the net. Any advice on settings I might try changing?

Thank you for your patience!

Here is my default-ssl virtual host file:

```
<IfModule mod_ssl.c>
<VirtualHost *:443>
	ServerAdmin webmaster@localhost
	ServerName thermo-server
	DocumentRoot /var/www-ssl/html
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
	SSLCertificateFile    /etc/apache2/ssl/server.crt
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

</VirtualHost>
</IfModule>
```

---

### Post by koenn on 2011-01-31
> **thaum16 said:**
>  I apologize for this as it seems to change the issue at hand from the one I originally posted about. 
Well, it does rather. I was beginning to look for network config issues (DNS, NAT, ...) combined with apache vhost configs that might explain such odd behaviour you originally posted about. 

Can you summarize again exactly what is and what isn't working ?

---

### Post by thaum16 on 2011-01-31
Again, sorry for the confusion.

Based on [this tutorial]("http://www.tc.umn.edu/~brams006/selfsign_ubuntu.html") that I followed for https/ssl browsing, it appears (b/c I was unsure what I was doing at the time) that I have created a vhost in apache2 so that any html or php file that I add to this directory /var/www-ssl/html/ will be served as https on port 443. But the pages in this directory are only viewable on the LAN. Is there an option either in the vhost configuration below or somewhere else in apache that I need to change/add to get these served to the internet? Port 443 is open on my router, and while testing my server, I set it to the DMZ.

```
<IfModule mod_ssl.c>
<VirtualHost *:443>
	ServerAdmin webmaster@localhost
	ServerName thermo-server
	DocumentRoot /var/www-ssl/html
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
	SSLCertificateFile    /etc/apache2/ssl/server.crt
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

</VirtualHost>
</IfModule>
```



Thank you!

---

### Post by koenn on 2011-01-31
vhosts are identified by servername. In order for that to work, that name needs to resolve to an address. In this case, that has to happen on the internet, so somewhere on the internet there needs to be a DNS server that knows the address of "thermo-server.<domain.tld>". Did you set that up as well ? 

Also, can you test that 
a/ port 443 on that (public) address is reacheable, and 
b/ actually reaches your web server (through the portforwarding you set up - this is what some residential routers call "DMZ")

---

### Post by thaum16 on 2011-02-01
koenn,

Thank you for your help. I just discovered that my problem was much simpler than I had originally thought. **My ISP was blocking both ports 80 for http and 443 for https.** Once I changed the port number for my vhost, I had no further problems.

Thank you for your patience and trying to help me! You did help me eliminate several things from my list of potential causes.

Moderators, please mark this thread as solved.

---

