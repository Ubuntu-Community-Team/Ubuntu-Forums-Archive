---
title: "SSL Cert From GoDaddy"
date: 2010-01-16
forum: Server Platforms
---

### Post by trentscott4 on 2010-01-16
I've purchased an SSL certificate from godaddy and want to install it one one of my virtual hosts.  I have a virtual host for domain xxxx.com which resides in /var/www/xxxx.

Do I follow the same procedure of installing a2enmodssl and generating a CSR?  Which config files need to be updated to install the SSL cert on that virual host?

Thanks in advance for any help.

---

### Post by kevin11951 on 2010-01-16
> **trentscott4 said:**
> I've purchased an SSL certificate from godaddy and want to install it one one of my virtual hosts.  I have a virtual host for domain xxxx.com which resides in /var/www/xxxx.

Do I follow the same procedure of installing a2enmodssl and generating a CSR?  Which config files need to be updated to install the SSL cert on that virual host?

Thanks in advance for any help.

SSL certs are complex if you have never done it before...  The best bet is to go here: [https://help.ubuntu.com/8.04/serverguide/C/httpd.html](https://help.ubuntu.com/8.04/serverguide/C/httpd.html) and here: [https://help.ubuntu.com/8.04/serverguide/C/certificates-and-security.html](https://help.ubuntu.com/8.04/serverguide/C/certificates-and-security.html) , and read the last-ish section on ssl and installing it into apache.

---

### Post by xerophyte on 2010-01-16
just configure your apache with 

example something like this 
<VirtualHost *:443>

    DocumentRoot "/local/www/ssl_html"

    SSLEngine on
    SSLOptions +StrictRequire

    <Directory />
        SSLRequireSSL
    </Directory>

    SSLProtocol -all +TLSv1 +SSLv3
    SSLCipherSuite HIGH:MEDIUM:!aNULL:+SHA1:+MD5:+HIGH:+MEDIUM

    SSLRandomSeed startup file:/dev/urandom 1024
    SSLRandomSeed connect file:/dev/urandom 1024

    SSLSessionCache shm:/usr/local/apache2/logs/ssl_cache_shm
    SSLSessionCacheTimeout 600    

    SSLCertificateFile /etc/apache2/ssl/server.crt
    SSLCertificateKeyFile /etc/apache2/ssl/server.key

    SSLVerifyClient none
    SSLProxyEngine off

    <IfModule mime.c>
        AddType application/x-x509-ca-cert      .crt
        AddType application/x-pkcs7-crl         .crl
    </IfModule>

    SetEnvIf User-Agent ".*MSIE.*" \  
      nokeepalive ssl-unclean-shutdown \  
      downgrade-1.0 force-response-1.0
</VirtualHost>

---

### Post by kevin11951 on 2010-01-16
> **xerophyte said:**
> just configure your apache with 

example something like this 
<VirtualHost *:443>

    DocumentRoot "/local/www/ssl_html"

    SSLEngine on
    SSLOptions +StrictRequire

    <Directory />
        SSLRequireSSL
    </Directory>

    SSLProtocol -all +TLSv1 +SSLv3
    SSLCipherSuite HIGH:MEDIUM:!aNULL:+SHA1:+MD5:+HIGH:+MEDIUM

    SSLRandomSeed startup file:/dev/urandom 1024
    SSLRandomSeed connect file:/dev/urandom 1024

    SSLSessionCache shm:/usr/local/apache2/logs/ssl_cache_shm
    SSLSessionCacheTimeout 600    

    SSLCertificateFile /etc/apache2/ssl/server.crt
    SSLCertificateKeyFile /etc/apache2/ssl/server.key

    SSLVerifyClient none
    SSLProxyEngine off

    <IfModule mime.c>
        AddType application/x-x509-ca-cert      .crt
        AddType application/x-pkcs7-crl         .crl
    </IfModule>

    SetEnvIf User-Agent ".*MSIE.*" \  
      nokeepalive ssl-unclean-shutdown \  
      downgrade-1.0 force-response-1.0
</VirtualHost>

That is A LOT more than you need for a successful https connection!

edit:  here is mine:

> NameVirtualHost *:443
<VirtualHost *:443>
DocumentRoot /var/www/store

SSLEngine on
   SSLProtocol all -SSLv2
   SSLCipherSuite ALL:!ADH:!EXPORT:!SSLv2:RC4+RSA:+HIGH:+MEDIUM

   SSLCertificateFile /etc/ssl/certs/server.crt
   SSLCertificateKeyFile /etc/ssl/certs/server.key
   SSLCertificateChainFile /etc/ssl/certs/server.ca

</VirtualHost>


---

