---
title: "Open SSL Configuration"
date: 2014-11-01
forum: Server Platforms
---

### Post by ericgcollyer on 2014-11-01
EDIT: The title of this should be SSL Configuration, not Open SSL Configuration

Hello all! I am attempting to configure my server to accept SSL connections, but I can't seem to get it to work. The following is my .conf file:

<VirtualHost *:80>
        ServerName imgurminecraft.com

        ServerAdmin webmaster@localhost
        DocumentRoot /media/additionalStorage/Apache/Apache2/htdocs

        <Directory /media/additionalStorage/Apache/Apache2/htdocs>
            Options FollowSymLinks MultiViews
            AllowOverride All
            Order allow,deny
            allow from all
        </Directory>

        ErrorLog ${APACHE_LOG_DIR}/error.log
        CustomLog ${APACHE_LOG_DIR}/access.log combined

</VirtualHost>
<VirtualHost *:443>
         ServerAdmin webmaster@localhost

         DocumentRoot /media/additionalStorage/Apache/Apache2/htdocs

         ErrorLog ${APACHE_LOG_DIR}/error.log
         CustomLog ${APACHE_LOG_DIR}/access.log combined

         SSLEngine on
         SSLCertificateFile /certs/certs/www_imgurminecraft_com.crt
         SSLCertificateKeyFile /certs/certs/myserver.key
         SSLCertificateChainFile /certs/certs/imgurminecraft.com.ca-bundle

</VirtualHost>

The following is the error message I'm getting:

AH01909: RSA certificate configured for 127.0.1.1:443 does NOT include an ID which matches the server name
AH02292: Init: Name-based SSL virtual hosts only work for clients with TLS server name indication support (RFC 4366)
AH00163: Apache/2.4.7 (Ubuntu) PHP/5.5.9-1ubuntu4.5 OpenSSL/1.0.1f configured -- resuming normal operations
AH00169: caught SIGTERM, shutting down

I can still connect with a non SSL connection, but I cannot connect with SSL. I've tried connecting on Chrome and Firefox, and I get an error message suggesting I need to check my computer's network connection. Any help would be appreciated. Thanks in advance!

---

### Post by volkswagner on 2014-11-01
I'm no expert, but you are missing:
```
ServerName imgurminecraft.com
```
in your <VirtualHost *:443>

---

### Post by ericgcollyer on 2014-11-01
Thanks for checking it out, I added that code and HTTPS still isn't working.

---

### Post by ericgcollyer on 2014-11-01
My new site file looks like this:

<VirtualHost *:80>

        ServerName imgurminecraft.com
        ServerAdmin webmaster@localhost

        DocumentRoot /media/additionalStorage/Apache/Apache2/htdocs

        <Directory /media/additionalStorage/Apache/Apache2/htdocs>
            Options FollowSymLinks MultiViews
            AllowOverride All
            Order allow,deny
            allow from all
        </Directory>

        ErrorLog ${APACHE_LOG_DIR}/error.log
        CustomLog ${APACHE_LOG_DIR}/access.log combined

</VirtualHost>
<VirtualHost *:443>

        ServerName imgurminecraft.com
        ServerAdmin webmaster@localhost

        DocumentRoot /media/additionalStorage/Apache/Apache2/htdocs

        ErrorLog ${APACHE_LOG_DIR}/error.log
        CustomLog ${APACHE_LOG_DIR}/access.log combined

        SSLEngine on
        SSLCertificateFile /etc/ssl/certs/www_imgurminecraft_com.crt
        SSLCertificateKeyFile /etc/ssl/private/myserver.key
        SSLCertificateChainFile /certs/certs/imgurminecraft.com.ca-bundle

</VirtualHost>

---

### Post by volkswagner on 2014-11-01
You have several errors, I would start with one error at a time:
```
RSA certificate configured for 127.0.1.1:443 does NOT include an ID which matches the server name
```
Have you compared the name certificate with your hostname/domain name. Does it have www. if so you'll need to 
include www in url.
Is port 443 open, listening? Is this a home server? If so, browse to [www.canyouseeme.org](www.canyouseeme.org) and check port 443, it should be open.

---

### Post by ericgcollyer on 2014-11-01
*Facepalm* Thanks for the help. As it turns out, I forgot to forward port 443 to my server. Thanks for the recommendation to check canyouseeme.org.

---

