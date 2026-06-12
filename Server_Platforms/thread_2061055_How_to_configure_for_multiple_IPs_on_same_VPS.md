---
title: "How to configure for multiple IPs on same VPS"
date: 2012-09-21
forum: Server Platforms
---

### Post by clay7 on 2012-09-21
Hello,

**What changes will I need to make, besides getting a separate IP address, so I can host 2 domains on the VPS?**

I have a domain hosted on a VPS at Linode (I'm pretty happy with them) and would like to add another domain to the same VPS with its own IP address. Here is my setup:

Ubuntu Server 12.04
Apache, current
PHP, current
MySQL, current

From what I read on the Apache site, I'm going to want separate daemons of httpd because I want the virtual servers and their data to be separate.

I know I'll need to get another IP from Linode. Linode's DNS Manager shows me as having the subdomain "mydomain.com". (the name between the quotes has been changed.

Here is what my files currently look like:

**/etc/hostname**
```
server1
```

**/etc/hosts**
```
127.0.0.1	localhost
xx.xx.xx.xx	server1.mydomain.com server1

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
```

**/etc/resolve.conf**
```
domain hello.linode.com
search hello.linode.com
nameserver xx.xxx.xx.4
nameserver xx.xxx.xx.5
```
("hello" is a substitute name)

**/etc/apache2/ports.conf**
```
NameVirtualHost xx.xx.xx.xx:80
Listen 80

<IfModule mod_ssl.c>
    Listen 443
</IfModule>

<IfModule mod_gnutls.c>
    Listen 443
</IfModule>

/etc/apache2/apache2.conf
ServerRoot "/etc/apache2"
LockFile /var/lock/apache2/accept.lock
PidFile ${APACHE_PID_FILE}
Timeout 300
KeepAlive On
MaxKeepAliveRequests 100
KeepAliveTimeout 5
<IfModule mpm_prefork_module>
    StartServers          5
    MinSpareServers       5
    MaxSpareServers      10
    MaxClients          150
    MaxRequestsPerChild   0
</IfModule>

<IfModule mpm_worker_module>
    StartServers          2
    MinSpareThreads      25
    MaxSpareThreads      75 
    ThreadLimit          64
    ThreadsPerChild      25
    MaxClients          150
    MaxRequestsPerChild   0
</IfModule>

<IfModule mpm_event_module>
    StartServers          2
    MinSpareThreads      25
    MaxSpareThreads      75 
    ThreadLimit          64
    ThreadsPerChild      25
    MaxClients          150
    MaxRequestsPerChild   0
</IfModule>

User ${APACHE_RUN_USER}
Group ${APACHE_RUN_GROUP}

AccessFileName .htaccess

<Files ~ "^\.ht">
    Order allow,deny
    Deny from all
    Satisfy all
</Files>

DefaultType None
HostnameLookups Off

ErrorLog /var/log/apache2/error.log
LogLevel warn

Include /etc/apache2/mods-enabled/*.load
Include /etc/apache2/mods-enabled/*.conf
Include /etc/apache2/httpd.conf
Include /etc/apache2/ports.conf
Include /etc/apache2/conf.d/
Include /etc/apache2/sites-enabled/
```

**/etc/apache2/sites-available/default**
```
<VirtualHost xx.xx.xx.xx:80>
	#ServerAdmin webmaster@localhost
	ServerAdmin admin@mydomain.com
	ServerName www.mydomain.com
	ServerAlias mydomain.com

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

	ErrorLog /var/log/apache2/error.log
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
```

**/etc/apache2/sites-available/default-ssl**
```
<IfModule mod_ssl.c>
<VirtualHost xx.xx.xx.xx:443>
	ServerAdmin admin@mydomain.com
	ServerName www.mydomain.com

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

	ErrorLog /var/log/apache2/error.log
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

	SSLEngine on

	SSLCertificateFile /etc/ssl/certs/cert.crt
	SSLCertificateKeyFile /etc/ssl/private/mykey.key
	SSLCertificateChainFile /etc/ssl/certs/intermediate.crt

	<FilesMatch "\.(cgi|shtml|phtml|php)$">
		SSLOptions +StdEnvVars
	</FilesMatch>
	<Directory /usr/lib/cgi-bin>
		SSLOptions +StdEnvVars
	</Directory>
	
	BrowserMatch "MSIE [2-6]" \
		nokeepalive ssl-unclean-shutdown \
		downgrade-1.0 force-response-1.0
	BrowserMatch "MSIE [17-9]" ssl-unclean-shutdown

</VirtualHost>
</IfModule>
```

---

### Post by sandyd on 2012-09-23
What are you aiming for?

a) seperated content, i.e. me.com serves content from /srv/me.com while me2.com serves content from /srv/me.com

b) seperated threads, running threads under a different user so that that user has no permission to access other user's files.

If it is b), I would recommend going for mod_ruid2. Using POSIX threads to change the thread owner, it is much faster than suexec, suphp, .etc .etc
If it is a), there is no need to use seperate daemons - just do a directory structure like
/srv
-site1.com
-site2.com

and point your virtual hosts there.

Also, there is no need to get an extra ip, That is what Virtual Name Based hosting is for.

---

### Post by clay7 on 2012-09-24
It is option "a".

Wouldn't I need separate IPs for the purpose of SSL certificates?

---

### Post by sandyd on 2012-09-24
No, if you want, you can do something like this.

[http://en.gentoo-wiki.com/wiki/Apache2/SSL_and_Name_Based_Virtual_Hosts](http://en.gentoo-wiki.com/wiki/Apache2/SSL_and_Name_Based_Virtual_Hosts)

as for a)
You can just copy /etc/apache2/sites-available/default into another file at /etc/apache2/sites-available/ , and edit the new file with your second domain's info (i.e. changing domain, serving directory)

Copy /etc/apache2/sites-available/default-ssl into another file at /etc/apache2/sites-available/ and edit the file with your second domain's info (i.e. changing domain, serving directory, SSL Cert)

---

### Post by clay7 on 2012-09-24
Thanks for the info...I'll give this a shot tonight. Good to know about not needing separate IPs anymore.

I appreciate your help!

---

