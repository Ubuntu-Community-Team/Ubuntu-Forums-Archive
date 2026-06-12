---
title: "Apache2 not redirecting http to https"
date: 2017-05-17
forum: Server Platforms
---

### Post by trygaba on 2017-05-17
Http is not redirecting to https I just get  "ERR_CONNECTION_TIMED_OUT" when trying to connect trough [http://.](http://.)  Connecting through https:// works fine here are my config files for  apache2 in sites available/enabled:

Http.conf:
```

<VirtualHost *:81> 

 ServerName website.fi
 DocumentRoot /var/www/website
 DirectoryIndex index.html
<Directory /var/www/website/>
 AllowOverride All
 Order Deny,Allow
 Allow from all
</Directory>
 RewriteEngine on
 RewriteRule ^ https://%{SERVER_NAME}%{REQUEST_URI} [END,QSA,R=permanent]
</VirtualHost>
```

https.conf:
```

<IfModule mod_ssl.c>
    <VirtualHost *:443>

    ServerAdmin webmaster@website.fi
    DocumentRoot /var/www/website
    ServerName website.fi
    DirectoryIndex index.html

    <Directory "/var/www/website">
        Options Indexes FollowSymLinks
        AllowOverride All
        Order allow,deny
        allow from all
    </Directory>

        ErrorLog ${APACHE_LOG_DIR}/error.log
        CustomLog ${APACHE_LOG_DIR}/access.log combined

        SSLEngine on
        SSLCertificateFile /etc/letsencrypt/live/website.fi-0001/fullchain.pem
                SSLCertificateKeyFile /etc/letsencrypt/live/website.fi-0001/privkey.pem
                SSLCertificateChainFile /etc/letsencrypt/live/website.fi-0001/chain.pem
                Include /etc/letsencrypt/options-ssl-apache.conf


        <FilesMatch "\.(cgi|shtml|phtml|php)$">
                SSLOptions +StdEnvVars
        </FilesMatch>
        <Directory /usr/lib/cgi-bin>
                SSLOptions +StdEnvVars
        </Directory>
    </VirtualHost>
</IfModule>

# vim: syntax=apache ts=4 sw=4 sts=4 sr noet
```

---

### Post by TheFu on 2017-05-17
<VirtualHost *:81>  ????

Perhaps you want:
<VirtualHost *:80>

---

### Post by trygaba on 2017-05-17
> **TheFu said:**
> <VirtualHost *:81>  ????

Perhaps you want:
<VirtualHost *:80>

No I setup it to listen port 81 because can't open port 80 in my router. I have listen port 81 in port.conf

---

### Post by TheFu on 2017-05-17
So your URL is ????
[http://domain.com:81/](http://domain.com:81/) ?

---

### Post by trygaba on 2017-05-17
> **TheFu said:**
> So your URL is ????
[http://domain.com:81/](http://domain.com:81/) ?

[https://domain.com](https://domain.com) works and [http://domain.com:81](http://domain.com:81) seems to redirect correctly but [http://domain.com](http://domain.com) not.

---

### Post by TheFu on 2017-05-17
> **trygaba said:**
> [https://domain.com](https://domain.com) works and [http://domain.com:81](http://domain.com:81) seems to redirect correctly but [http://domain.com](http://domain.com) not.

And it never will.  The standard port for all HTTP traffic which is set on billions of devices is port 80.  You changing your server to listen on 81 doesn't impress **any** of those other systems.

---

### Post by QIII on 2017-05-17
Is this site hosted on a server at your home?  Is your ISP blocking residential traffic on port 80?

---

### Post by trygaba on 2017-05-17
> **TheFu said:**
> And it never will.  The standard port for all HTTP traffic which is set on billions of devices is port 80.  You changing your server to listen on 81 doesn't impress **any** of those other systems.

Oh ok, now it works and I managed to open port 80 also in router.

---

