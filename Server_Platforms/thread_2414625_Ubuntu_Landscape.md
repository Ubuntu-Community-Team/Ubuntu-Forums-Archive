---
title: "Ubuntu Landscape"
date: 2019-03-13
forum: Server Platforms
---

### Post by james.w.krych on 2019-03-13
Okay, this is for the test server at home so I'm not worried if things break. The version of Ubuntu Server is 18.04 LTS. Landscape is 19.01.

Having resolved that my previous issue was something on my work side, I decided to repo sync on my home server. All is well and I can see the downloaded files in the proper location at /var/lib/landscape/landscape-repository/standalone/.

However, I am unable to browse to the locations as suggested in the manual:

[http://landscapetest.local/repository/standalone/ubuntu/pool/](http://landscapetest.local/repository/standalone/ubuntu/pool/)


 
and
[http://landscapetest.local/repository/standalone/ubuntu/dists/](http://landscapetest.local/repository/standalone/ubuntu/dists/)

Getting the following error for both url's.


**Not Found**

The requested URL /repository/standalone/ubuntu/pool/ was not found on this server.
[HR][/HR]
Apache/2.4.29 (Ubuntu) Server at landscapetest.local Port 80


I'm failing to see what my issue might be here.

Here are some of the files:
root@landscapetest:/var/lib/landscape/landscape-repository/standalone/ubuntu# cat /etc/hosts
127.0.0.1 localhost
#127.0.1.1 landscapetest.local landscapetest
192.168.1.7 landscapetest.local landscapetest
# The following lines are desirable for IPv6 capable hosts
::1 localhost ip6-localhost ip6-loopback
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
root@landscapetest:/var/lib/landscape/landscape-repository/standalone/ubuntu#

UFW Status is inactive

Finally,

root@landscapetest:/etc/apache2/sites-available# cat landscapetest.local.conf
<IfModule mpm_worker_module>
StartServers 2
MinSpareThreads 25
MaxSpareThreads 75
ThreadLimit 64
ThreadsPerChild 64
MaxClients 1024
MaxRequestsPerChild 0
</IfModule>


<IfModule mpm_prefork_module>
StartServers 5
MinSpareServers 5
MaxSpareServers 10
MaxClients 1024
MaxRequestsPerChild 0
</IfModule>


NameVirtualHost *:80
<VirtualHost *:80>
ServerName landscapetest.local
ServerAdmin [EMAIL="webmaster@landscapetest.local"]webmaster@landscapetest.local[/EMAIL]


ErrorLog /var/log/apache2/landscape_error.log
CustomLog /var/log/apache2/landscape_access.log combined
DocumentRoot /opt/canonical/landscape/canonical/landscape


# Set a Via header in outbound requests to the proxy, so proxied apps can
# know who the actual client is
ProxyVia on
ProxyTimeout 10


<Directory "/">
Options +Indexes
Order deny,allow
Allow from all
Require all granted
Satisfy Any
ErrorDocument 403 /offline/unauthorized.html
ErrorDocument 404 /offline/notfound.html
</Directory>


Alias /offline /opt/canonical/landscape/canonical/landscape/offline
Alias /static /opt/canonical/landscape/canonical/static
Alias /repository /var/lib/landscape/landscape-repository


<Location "/repository">
Order deny,allow
Deny from all
ErrorDocument 403 default
ErrorDocument 404 default
</Location>
<LocationMatch "/repository/[^/]+/[^/]+/(dists|pool)/.*">
Allow from all
</LocationMatch>
<Location "/icons">
Order allow,deny
Allow from all
</Location>
<Location "/ping">
Order allow,deny
Allow from all
</Location>


<Location "/message-system">
Order allow,deny
Allow from all
</Location>


<Location "/static">
Header always append X-Frame-Options SAMEORIGIN
</Location>
<Location "/r">
FileETag none
ExpiresActive on
ExpiresDefault "access plus 10 years"
Header append Cache-Control "public"
</Location>


RewriteEngine On


RewriteRule ^/r/([^/]+)/(.*) /$2


# The Landscape Ping Server runs on port 8070
RewriteRule ^/ping$ [http://localhost:8070/ping](http://localhost:8070/ping) [P]


RewriteCond %{REQUEST_URI} !^/server-status
RewriteCond %{REQUEST_URI} !^/icons
RewriteCond %{REQUEST_URI} !^/static/
RewriteCond %{REQUEST_URI} !^/offline/
RewriteCond %{REQUEST_URI} !^/repository/
RewriteCond %{REQUEST_URI} !^/message-system


# Replace the <hostname> with the DNS hostname for this machine.
# If you change the port number that Apache is providing SSL on, you must
# change the port number 443 here.
RewriteRule ^/(.*) https://landscapetest.local:443/$1 [R=permanent]
</VirtualHost>


<VirtualHost *:443>
ServerName landscapetest.local
ServerAdmin [EMAIL="webmaster@landscapetest.local"]webmaster@landscapetest.local[/EMAIL]


ErrorLog /var/log/apache2/landscape_error.log
CustomLog /var/log/apache2/landscape_access.log combined


DocumentRoot /opt/canonical/landscape/canonical/landscape


SSLEngine On
SSLCertificateFile /etc/ssl/certs/landscape_server.pem
SSLCertificateKeyFile /etc/ssl/private/landscape_server.key
# Disable to avoid POODLE attack
SSLProtocol all -SSLv3 -SSLv2 -TLSv1
SSLHonorCipherOrder On
SSLCompression Off
SSLCipherSuite EECDH+AESGCM+AES128:EDH+AESGCM+AES128:EECDH+AES128:EDH+AES128:ECDH+AESGCM+AES128:aRSA+AESGCM+AES128:ECDH+AES128:DH+AES128:aRSA+AES128:EECDH+AESGCM:EDH+AESGCM:EECDH:EDH:ECDH+AESGCM:aRSA+AESGCM:ECDH:DH:aRSA:HIGH:!MEDIUM:!aNULL:!NULL:!LOW:!3DES:!DSS:!EXP:!PSK:!SRP:!CAMELLIA:!DHE-RSA-AES128-SHA:!DHE-RSA-AES256-SHA:!aECDH
# Note: Some versions of Apache will not accept the SSLCertificateChainFile
# directive. Try using SSLCACertificateFile instead
SSLCertificateChainFile /etc/ssl/certs/landscape_server_ca.crt


# Try to keep this close to the storm timeout. Not less, maybe slightly
# more
ProxyTimeout 305


<Directory "/">
Options -Indexes
Order deny,allow
Allow from all
Require all granted
Satisfy Any
ErrorDocument 403 /offline/unauthorized.html
ErrorDocument 404 /offline/notfound.html
</Directory>


<Location "/ajax">
Order allow,deny
Allow from all
</Location>


Alias /config /opt/canonical/landscape/apacheroot
Alias /hash-id-databases /var/lib/landscape/hash-id-databases
Alias /offline /opt/canonical/landscape/canonical/landscape/offline


ProxyRequests off
<Proxy *>
Order deny,allow
Allow from all
ErrorDocument 403 /offline/unauthorized.html
ErrorDocument 500 /offline/exception.html
ErrorDocument 502 /offline/unplanned-offline.html
ErrorDocument 503 /offline/unplanned-offline.html
</Proxy>


ProxyPass /robots.txt !
ProxyPass /favicon.ico !
ProxyPass /static !
ProxyPass /offline !


ProxyPreserveHost on




<Location "/static">
Header always append X-Frame-Options SAMEORIGIN
</Location>
<Location "/r">
FileETag none
ExpiresActive on
ExpiresDefault "access plus 10 years"
Header append Cache-Control "public"
</Location>


RewriteEngine On


RewriteRule ^/.*\+\+.* / [F]
RewriteRule ^/r/([^/]+)/(.*) /$2


# See /etc/landscape/service.conf for a description of all the
# Landscape services and the ports they run on.


# If you change the port number that Apache is providing SSL on, you must
# change the port number 443 here.
RewriteRule ^/message-system [http://localhost:8090/++vh++https:landscapetest.local:443/++/](http://localhost:8090/++vh++https:landscapetest.local:443/++/) [P,L]


RewriteRule ^/ajax [http://localhost:9090/](http://localhost:9090/) [P,L]
RewriteRule ^/combo(.*) http://localhost:8080/combo$1 [P,L]
RewriteRule ^/api [http://localhost:9080/](http://localhost:9080/) [P,L]
RewriteRule ^/attachment/(.*) http://localhost:8090/attachment/$1 [P,L]
RewriteRule ^/upload/(.*) http://localhost:9100/$1 [P,L]


RewriteCond %{REQUEST_URI} !^/robots.txt$
RewriteCond %{REQUEST_URI} !^/favicon.ico$
# Ignore both /static and /r/####/static routes
RewriteCond %{REQUEST_URI} !^/(r/[^/]+/)?static/
RewriteCond %{REQUEST_URI} !^/offline/
RewriteCond %{REQUEST_URI} !^/config/
RewriteCond %{REQUEST_URI} !^/hash-id-databases/


# If you change the port number that Apache is providing SSL on, you must
# change the port number 443 here.
RewriteRule ^/(.*) http://localhost:8080/++vh++https:landscapetest.local:443/++/$1 [P]


<Location /message-system>
Order allow,deny
Allow from all
</Location>


<Location />
# Insert filter
SetOutputFilter DEFLATE


# Don't compress images or .debs
SetEnvIfNoCase Request_URI \
\.(?:gif|jpe?g|png|deb)$ no-gzip dont-vary


# Make sure proxies don't deliver the wrong content
Header append Vary User-Agent env=!dont-vary
</Location>


</VirtualHost>
root@landscapetest:/etc/apache2/sites-available#

---

### Post by james.w.krych on 2019-03-14
May have a solution once I get back home and power the server back up. The repo link may not have the correct owner/group...

---

### Post by james.w.krych on 2019-03-14
Nope. The repo link does have the correct owner:group and permissions.

---

### Post by james.w.krych on 2019-03-14
Funny thing happened on the way to just changing the ServerName to not having a ".local" to it.

Works now and I was able to wget a package from the synced repo.

'Night all!

---

