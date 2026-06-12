---
title: "Apache2 + SSL certs migrating from SuSE"
date: 2007-08-30
forum: Server Platforms
---

### Post by BarryBotha on 2007-08-30
Hi All

I am migrating from SuSE to Ubuntu and I have run into trouble with moving the SSL site across. I've copied the necessary .key and .crt files over and configured the vhost to use them. The server reloads fine without errors.

When I try to browse to the server I get an SSL error from Firefox and IE7 just won't work. I've googled the firefox error and it seems that the problem is that the server breaks the protocol.

Here is my SSL virtualhost file:
<VirtualHost secure.sitename.co.za:443>

        ServerAdmin [email]barry@sitename.com[/email]
        ServerName secure.sitename.co.za

        SSLEngine On
        SSLCertificateFile /etc/apache2/secure.sitename.co.za.crt
        SSLCertificateKeyFile /etc/apache2/secure.sitename.co.za.key
        SSLCACertificateFile /etc/apache2/thawte.crt

        DocumentRoot /var/www/sitename
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/sitename>
                Options Indexes FollowSymLinks MultiViews
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>

        ErrorLog /var/log/apache2/secure.sitename.co.za.error.log
        LogLevel debug

        CustomLog /var/log/apache2/secure.sitename.co.za.access.log combined
        ServerSignature On

</VirtualHost>

In my error log I get the following on each server reload:
[Thu Aug 30 18:24:13 2007] [info] Loading certificate & private key of SSL-aware server
[Thu Aug 30 18:24:13 2007] [debug] ssl_engine_pphrase.c(469): unencrypted RSA private key - pass phrase not required
[Thu Aug 30 18:24:13 2007] [info] Configuring server for SSL protocol
[Thu Aug 30 18:24:13 2007] [debug] ssl_engine_init.c(405): Creating new SSL context (protocols: SSLv2, SSLv3, TLSv1)
[Thu Aug 30 18:24:13 2007] [debug] ssl_engine_init.c(538): Configuring client authentication
[Thu Aug 30 18:24:13 2007] [debug] ssl_engine_init.c(1113): CA certificate: /C=ZA/O=Thawte Consulting (Pty) Ltd./CN=Thawte SGC CA
[Thu Aug 30 18:24:13 2007] [debug] ssl_engine_init.c(601): Configuring permitted SSL ciphers [ALL:!ADH:!EXPORT56:RC4+RSA:+HIGH:+MEDIUM:+LOW:+SSLv2:+EXP:+eNULL]
[Thu Aug 30 18:24:13 2007] [debug] ssl_engine_init.c(729): Configuring RSA server certificate
[Thu Aug 30 18:24:13 2007] [info] RSA server certificate enables Server Gated Cryptography (SGC)
[Thu Aug 30 18:24:13 2007] [debug] ssl_engine_init.c(768): Configuring RSA server private key

All looks fine according to that.
When I try to browse there the access log show this:
192.168.2.110 - - [30/Aug/2007:18:36:59 +0200] "\x16\x03\x01" 501 335 "-" "-"

I also constanlty get this:
127.0.0.1 - - [30/Aug/2007:18:36:13 +0200] "GET / HTTP/1.0" 200 960 "-" "Apache/2.2.3 (Ubuntu) PHP/5.2.1 mod_ssl/2.2.3 OpenSSL/0.9.8c (internal dummy connection)"

Which I guess is normal.

Please if somebody can point me into some direction, I'm feeling kind of lost at the moment.

Thanks
Barry

---

### Post by MJN on 2007-08-31
You mentioned Firefox gives an error - it might be helpful if you said what!
 
Mathew

---

