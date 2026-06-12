---
title: "Can't get domain names to work"
date: 2014-11-28
forum: Server Platforms
---

### Post by adam104 on 2014-11-28
Hi! I'm gonna take all of this from the begninning for you to understand I'm out on deep waters.

1. I installed ubuntu server to my server rig.
2. I installed LAMP stack to the server.
3. I installed owncloud to the server. ([http://owncloud.org/](http://owncloud.org/))
4. I changed the DNS settnings from Domain Provider to point at my server.
5. I changed the 000-Default.conf file in apache's "sites available" folder so it would redirect directly to my /owncloud/ folder instead of mydomain/owncloud.

This didn't quite work...
What I wanna archive is actually to point a subdomain.mydomain.com to a specified folder. 
Also to point a second mydomain2.com to a specified folder.

I'm all new to the shiny world of ubuntu, but as of now I'm stuck like a kitten in concrete....

---

### Post by volkswagner on 2014-11-28
> **adam104 said:**
> 
...snip

This didn't quite work...
What I wanna archive is actually to point a subdomain.mydomain.com to a specified folder. 
Also to point a second mydomain2.com to a specified folder.



"This didn't quite work..." is not descriptive.
Please explain what happens when navigating to the url.
What error if any is encountered?
Are you trying from inside your LAN? Is your server behind a router/same router as your LAN?
Did you open ports in router?
Can you ping the domain name from inside your lan?
Try running the following command:
```
host subdomain.mydomain.com
```
Do you get your server's public ip address?
From memory, Owncloud "expects" url to be as configured. You may have to "tell" owncloud the
new url/domain in configuration.  I have also had unexpected results when trying to access owncloud from local
and WAN urls (your milage may vary).

---

### Post by adam104 on 2014-11-28
> **volkswagner said:**
> "This didn't quite work..." is not descriptive.
Please explain what happens when navigating to the url.
What error if any is encountered?
Are you trying from inside your LAN? Is your server behind a router/same router as your LAN?
Did you open ports in router?
Can you ping the domain name from inside your lan?
Try running the following command:
```
host subdomain.mydomain.com
```
Do you get your server's public ip address?
From memory, Owncloud "expects" url to be as configured. You may have to "tell" owncloud the
new url/domain in configuration.  I have also had unexpected results when trying to access owncloud from local
and WAN urls (your milage may vary).

When I try connect to mydomain.com/owncloud I get in and it works just fine.
When I connect trough mysubdomain.com/owncloud I get into the default "Apache2 Default page".
I'm trying both inside LAN and outside.
All ports are open to the server, I can ping it from outside and inside LAN.
Isn't there a deafult config file to tell like if mydomain.com is used send to /www/mydomain/pi/ and if mydomain2.com is used send to /www/mydomain/pi2/?

---

### Post by volkswagner on 2014-11-28
Please post your host files in /etc/apache2/sites-available/

---

### Post by adam104 on 2014-11-29
I got 3 files there:
000-default.conf
```
 <VirtualHost *:80>





ServerAdmin webmaster@localhost
ServerName domain.com
ServerAlias www.domain.com
DocumentRoot /var/www/owncloud/




    


    ErrorLog ${APACHE_LOG_DIR}/error.log
    CustomLog ${APACHE_LOG_DIR}/access.log combined


    
</VirtualHost>


# vim: syntax=apache ts=4 sw=4 sts=4 sr noet

```

subdomain.domain.com

```

<VirtualHost *80>
ServerName www.subdomain.domain.com
DocumentRoot /var/www/owncloud
</VirtualHost>

```

default-ssl.com

```

<IfModule mod_ssl.c>
    <VirtualHost _default_:443>
        ServerAdmin webmaster@localhost


        DocumentRoot /var/www/html


ErrorLog ${APACHE_LOG_DIR}/error.log
        CustomLog ${APACHE_LOG_DIR}/access.log combined
SSLEngine on
SSLCertificateFile    /etc/ssl/certs/ssl-cert-snakeoil.pem
        SSLCertificateKeyFile /etc/ssl/private/ssl-cert-snakeoil.key
<FilesMatch "\.(cgi|shtml|phtml|php)$">
                SSLOptions +StdEnvVars
        </FilesMatch>
        <Directory /usr/lib/cgi-bin>
                SSLOptions +StdEnvVars
        </Directory>


BrowserMatch "MSIE [2-6]" \
                nokeepalive ssl-unclean-shutdown \
                downgrade-1.0 force-response-1.0
        # MSIE 7 and newer should be able to use keepalive
        BrowserMatch "MSIE [17-9]" ssl-unclean-shutdown


    </VirtualHost>
</IfModule>


# vim: syntax=apache ts=4 sw=4 sts=4 sr noet

```

---

### Post by volkswagner on 2014-11-29
If you are using Ubuntu 14.04, I believe you need to have .conf extension on your vhost files.
Typically documentRoot does not have a trailing slash "/".
Your host files are a bit sparse as well (there's no directory directive).
Both files point to the same document root. In this case you should use the alias directive rather than two unique .conf files.

Example directory directive:
```
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


```

---

