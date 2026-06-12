---
title: "Apache and gnu_tls"
date: 2012-06-15
forum: Server Platforms
---

### Post by Trzone on 2012-06-15
I am attempting to use the apache mod gnu_tls
(testing in a VM before configuring on the server)

The module is enabled: sudo a2enmod gnutls
Module gnutls already enabled
Output of ports.conf:
NameVirtualHost *:443
  Listen 443
--------------------------------------
Output of /etc/apache2/sites-available/default
<VirtualHost *:443>

        DocumentRoot /var/www
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        
	GnuTLSEnable on
        GnuTLSCacheTimeout 500
	GnuTLSSessionTickets on
	GnuTLSPriorities NORMAL
	GnuTLSExportCertificates on
	GnuTLSCertificateFile /home/theodore/server.crt
        GnuTLSKeyFile /home/theodore/server.key
      </VirtualHost>
--------------------------------------
I generated the .crt and .key file (in my home directory) 
openssl genrsa -out server.key 1024
openssl req -new -x509 -nodes -sha1 -days 365 -key server.key > server.crt
------------------
output of curl
http: curl 127.0.0.1:443 (returns the html file)
https: curl [https://127.0.0.1](https://127.0.0.1)
curl: (35) error:140770FC:SSL routines:SSL23_GET_SERVER_HELLO:unknown protocol

It is speaking http and not https, so I'm stumped...
I did configure the website with openssl to make sure it wasn't a simple openssl error. Though I did use the 'snakeoil' .pem and .key

Sorry for the long post, just want to be thorough.
Thanks!
[Edit] Using Ubuntu 12.04 LTS 64 bit

---

