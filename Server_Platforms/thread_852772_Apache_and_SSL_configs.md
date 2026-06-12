---
title: "Apache and SSL configs"
date: 2008-07-07
forum: Server Platforms
---

### Post by puelly on 2008-07-07
I have been trying to setup a subdomain with SSL encryption using a self-signed certificate.  I am close to achieving my goal but there are a few snags.

With my current config, whenever I go to a "http" location on my site I am redirected to the index.html page in the main domain document root.  For example, [http://monline.com](http://monline.com) and [http://mvi.monline.com](http://mvi.monline.com) open the same page.

The other things is that whenever I open a "https" location on my server I am redirected to the default file in the document root of my subdomain. For example, [https://monline.com](https://monline.com) and [https://mvi.monline.com](https://mvi.monline.com) open the same secure site at the doc root of mvi.monline.com

Ideally, I would like to use SSL only for [https://mvi.monline.com](https://mvi.monline.com) and redirect links to [http://mvi.monline.com](http://mvi.monline.com) to the secure site.  All other sites and subdomains should function as normal http: connections.

Can someone please help me to fine tune this problem.  Maybe I am not understanding some documentation properly.  I have posted my site configs below.  The subdomain is running a rails app, I am not sure how this affects apache's side of the secure config.

**default**

```
NameVirtualHost *:80

<VirtualHost *:80>

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

**mvi.ssl**

```
<Proxy *>

  Order allow,deny

  Allow from all

</Proxy>



<Proxy balancer://mvidb>

  BalancerMember http://127.0.0.1:9100

  BalancerMember http://127.0.0.1:9101

</Proxy>



<VirtualHost *:443>

  ServerName mvi.monline.com:443

  ServerAdmin richard@gmail.com

    DocumentRoot /home/richard/apps/mvidb/

      <Directory />

      Options Indexes FollowSymLinks MultiViews

           AllowOverride All

           Order allow,deny

           Allow from all

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

 	# Log Level

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



	#Rewrite Rules

	RewriteEngine On

	RewriteCond %{DOCUMENT_ROOT}/system/maintenance.html -f

	RewriteCond %{SCRIPT_FILENAME} !maintenance.html

	RewriteRule ^.*$ /system/maintenance.html [L]

	RewriteRule ^/$ /index.html [QSA]

	RewriteRule ^([^.]+)$ $1.html [QSA]



	RewriteCond %{DOCUMENT_ROOT}/%{REQUEST_FILENAME} !-f

	RewriteRule ^/(.*)$ balancer://mvidb%{REQUEST_URI} [P,QSA,L]



	# The actual SSL stuff below, make sure the engine is on, enable some 

	# options that the Gutsy page said I should,

	# and tell Apache where my key+CSR files are

	SSLEngine on

	SSLOptions +FakeBasicAuth +ExportCertData +StrictRequire

	SSLCertificateFile /etc/ssl/certs/mvi.monline.crt

	SSLCertificateKeyFile /etc/ssl/private/mvi.monline.key



	# Used by Rails. Mentioned in all the Rails SSL tutorials.

	RequestHeader set X_FORWARDED_PROTO "https"

</VirtualHost>   


```

I'd appreciate any help that can be given.  Thanks.

---

### Post by windependence on 2008-07-08
You can't do this with named virtual hosts.

> [B]Why can't I use SSL with name-based/non-IP-based virtual hosts?
[/B]
The reason is very technical, and a somewhat "chicken and egg" problem. The SSL protocol layer stays below the HTTP protocol layer and encapsulates HTTP. When an SSL connection (HTTPS) is established Apache/mod_ssl has to negotiate the SSL protocol parameters with the client. For this, mod_ssl has to consult the configuration of the virtual server (for instance it has to look for the cipher suite, the server certificate, etc.). But in order to go to the correct virtual server Apache has to know the Host HTTP header field. To do this, the HTTP request header has to be read. This cannot be done before the SSL handshake is finished, but the information is needed in order to complete the SSL handshake phase. Bingo!

**Why is it not possible to use Name-Based Virtual Hosting to identify different SSL virtual hosts?**

Name-Based Virtual Hosting is a very popular method of identifying different virtual hosts. It allows you to use the same IP address and the same port number for many different sites. When people move on to SSL, it seems natural to assume that the same method can be used to have lots of different SSL virtual hosts on the same server.

It comes as rather a shock to learn that it is impossible.

The reason is that the SSL protocol is a separate layer which encapsulates the HTTP protocol. So the SSL session is a separate transaction, that takes place before the HTTP session has begun. The server receives an SSL request on IP address X and port Y (usually 443). Since the SSL request does not contain any Host: field, the server has no way to decide which SSL virtual host to use. Usually, it will just use the first one it finds, which matches the port and IP address specified.

You can, of course, use Name-Based Virtual Hosting to identify many non-SSL virtual hosts (all on port 80, for example) and then have a single SSL virtual host (on port 443). But if you do this, you must make sure to put the non-SSL port number on the NameVirtualHost directive, e.g.

NameVirtualHost 192.168.1.1:80

Other workaround solutions include:

Using separate IP addresses for different SSL hosts. Using different port numbers for different SSL hosts.


[http://httpd.apache.org/docs/2.0/ssl/ssl_faq.html](http://httpd.apache.org/docs/2.0/ssl/ssl_faq.html)

-Tim

---

