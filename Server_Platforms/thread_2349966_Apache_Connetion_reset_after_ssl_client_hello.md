---
title: "Apache: Connetion reset after ssl client hello"
date: 2017-01-20
forum: Server Platforms
---

### Post by StreLochKi on 2017-01-20
Hi,

I have set up my first https web server and I ran into some trouble.
I have a 14.4LTS server and I used tis tutorial.
[https://www.digitalocean.com/community/tutorials/how-to-create-a-ssl-certificate-on-apache-for-ubuntu-14-04](https://www.digitalocean.com/community/tutorials/how-to-create-a-ssl-certificate-on-apache-for-ubuntu-14-04)

The servers listens on 443 and accepts telnet connections on 443.
Wireshark sees a valid tcp connection, a ssl Client hello, then a RST from the server.
gnutls-cli-debug gives output: Server does not support any of SSL 3.0, TLS 1.0 and TLS 1.1 and TLS 1.2
ssllabs.com: Assessment failed: No secure protocols supported 

default-ssl.conf
```
<IfModule mod_ssl.c>
        <VirtualHost _default_:443>
                ServerAdmin webmaster@localhost

                DocumentRoot /var/www/html

                ErrorLog ${APACHE_LOG_DIR}/error.log
                CustomLog ${APACHE_LOG_DIR}/access.log combined

                SSLEngine on
                SSLCipherSuite HIGH
                SSLProtocol -ALL +SSLv3 +TLSv1.2 +TLSv1.1 +TLSv1
                SSLHonorCipherOrder On
                SSLCipherSuite EECDH+ECDSA+AESGCM:EECDH+ECDSA+SHA384:EECDH+ECDSA+SHA256:ECDH+AESGCM:DH+AESGCM:ECDH+AES256:DH+AES256:ECDH+AES128:DH+AES:ECDH+3DES:DH+3DES:RSA+AES:RSA+3DES:!ADH:!AECDH:!MD5:!DSS

                SSLCertificateFile      /etc/apache2/ssl/apache.crt
                SSLCertificateKeyFile /etc/apache2/ssl/apache.key

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


thanks in advance.

===Edit1===
On later inspection: ```
openssl s_client -connect 127.0.0.1:443 -prexit
``` run on the server itself did return a valid tls handshake.
When I ran packet captures on both sides they both blamed the other end for resetting the connection. I have now contacted my provider to check there firewall.

===Edit2===
Solved the application firewall only allowed http traffic.

Tags: apache apache2 mod_ssl ssl sslengine tls https Cipher

---

### Post by cariboo on 2017-01-20
This question is probably a better fit here.

---

