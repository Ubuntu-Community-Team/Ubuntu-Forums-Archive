---
title: "cant figure oth how to create ssl"
date: 2014-10-29
forum: Security
---

### Post by guldberg72 on 2014-10-29
Hello guys.  i cant figure out how to get my apche server to run https instead of http
i have tried to follow this guide but without any luck..

[https://www.digitalocean.com/community/tutorials/how-to-create-a-ssl-certificate-on-apache-for-ubuntu-14-04](https://www.digitalocean.com/community/tutorials/how-to-create-a-ssl-certificate-on-apache-for-ubuntu-14-04)

i havent really configured my server other than installing lamp-server^ and then owncloud

my router ip is 192.168.1.1
host server 192.168.1.108
**wan ip 28.180.xx.xxx**


i ran these commands :
> 

sudo a2enmod ssl

> sudo service apache2 restart


> sudo mkdir /etc/apache2/ssl
> 
sudo openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout /etc/apache2/ssl/apache.key -out /etc/apache2/ssl/apache.crt

> 
Country Name (2 letter code) [AU]:Dk
State or Province Name (full name) [Some-State]:Sjælland
Locality Name (eg, city) []:København
Organization Name (eg, company) [Internet Widgits Pty Ltd]:Private
Organizational Unit Name (eg, section) []:Private
Common Name (e.g. server FQDN or YOUR name) []:82.180.xx.xxx
Email Address []:xxxxxx@xxxxx.com
> 
sudo nano /etc/apache2/sites-available/default-ssl.conf

> [B]<IfModule mod_ssl.c>
    <VirtualHost _default_:443>
        ServerAdmin webmaster@localhost
        DocumentRoot /var/www/html
        ErrorLog ${APACHE_LOG_DIR}/error.log
        CustomLog ${APACHE_LOG_DIR}/access.log combined
        SSLEngine on
        SSLCertificateFile /etc/apache2/ssl/apache.crt
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
</IfModule>[/B]


  			  		
  		 			 
**ownCloud version:** 7.0.2**Webserver:** Apache**Database:** MySQL**OS:** Linux **PHP version:** 5.5.9

---

### Post by guldberg72 on 2014-10-29
i am not completly sure what i should whrite as nameserver ?

---

