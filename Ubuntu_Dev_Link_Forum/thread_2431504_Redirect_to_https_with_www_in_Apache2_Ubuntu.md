---
title: "Redirect to https with www in Apache2 Ubuntu"
date: 2019-11-17
forum: Ubuntu Dev Link Forum
---

### Post by mithradantor on 2019-11-17
after many attempts I am still unable to redirect properly from non https or non www to https with www. I hope someone here can help me out. I'll explain what I have so far (which is working):

I have my main file mysite.conf in my sites-available directory (Apache2 on Ubuntu 18.04).

```
<VirtualHost *:80>
     ServerName mysite.nl
     ServerAlias www.mysite.nl
     DocumentRoot /var/www/mysite.nl
     ServerAdmin info@mysite.nl

     <Directory /var/www/mysite.nl>
         Options Indexes FollowSymLinks
         AllowOverride All
         Require all granted
     </Directory>

     <FilesMatch ".php$">
         SetHandler "proxy:unix:/var/run/php/php7.3-fpm.sock|fcgi://localhost/"
      </FilesMatch>

      ErrorLog ${APACHE_LOG_DIR}/error.log
      CustomLog ${APACHE_LOG_DIR}/access.log combined

RewriteEngine on
#RewriteCond %{SERVER_NAME} =mysite.nl
#RewriteRule ^ https://%{SERVER_NAME}%{REQUEST_URI} [END,NE,R=permanent]

Redirect permanent / https://www.mysite.nl/

</VirtualHost>
```

My Certbot made a new file which will be used for HTTPS. The file is written below:


```
<IfModule mod_ssl.c>
<VirtualHost *:443>
     ServerName mysite.nl
     ServerAlias www.mysite.nl
     DocumentRoot /var/www/mysite.nl
     ServerAdmin info@mysite.nl

     <Directory /var/www/mysite.nl>
         Options Indexes FollowSymLinks
         AllowOverride All
         Require all granted
     </Directory>

     <FilesMatch ".php$">
         SetHandler "proxy:unix:/var/run/php/php7.3-fpm.sock|fcgi://localhost/"
      </FilesMatch>

      ErrorLog ${APACHE_LOG_DIR}/error.log
      CustomLog ${APACHE_LOG_DIR}/access.log combined

RewriteEngine on
# Some rewrite rules in this file were disabled on your HTTPS site,
# because they have the potential to create redirection loops.

# RewriteCond %{SERVER_NAME} =mysite.nl
# RewriteRule ^ https://%{SERVER_NAME}%{REQUEST_URI} [END,NE,R=permanent]

#Redirect permanent / https://www.mysite.nl

Include /etc/letsencrypt/options-ssl-apache.conf
SSLCertificateFile /etc/letsencrypt/live/www.mysite.nl/fullchain.pem
SSLCertificateKeyFile /etc/letsencrypt/live/www.mysite.nl/privkey.pem
</VirtualHost>
</IfModule>
```


The problem I am having now is that I always want the user to end up at [https://www.mysite.nl/](https://www.mysite.nl/)
So in any other case for example:

- [www.mysite.nl](www.mysite.nl)
- [http://mysite.nl](http://mysite.nl)
- [https://mysite.nl](https://mysite.nl)
- [http://www.mysite.nl](http://www.mysite.nl)

I want the user to be redirected to [https://www.mysite.nl/](https://www.mysite.nl/).

I hope someone can help me out on how to fix this as I have failed on any attempt that I made the last two days.

---

### Post by SeijiSensei on 2019-11-17
```

<VirtualHost *:80>
     ServerName www.mysite.nl
     ServerAlias mysite.nl 

     Redirect permanent / https://www.mysite.nl/
</VirtualHost>

```

In the configuration for port 443 you would include mysite.nl as a ServerAlias for [www.mysite.nl](www.mysite.nl).

I'd have the ServerName refer to whatever name is associated with the A record for this host. It should also have reverse resolution configured for that name.  In other words, the "canonical" name for this host.

---

### Post by mithradantor on 2019-11-17
Thank you for your reply seijiSensei, but wouldnt that result in an infinite redirect? I was thinking I would need something like a RewriteCondition and for that condition a Redirect permanent :) 
Something along the line of,

if no www or if no https then redirect

---

### Post by SeijiSensei on 2019-11-18
No, it would just redirect the request to port 443 where it would be handled by configuration for the secure host.  The <VirtualHost *:443> configuration should include the usual DocumentRoot directive and <Directory> stanza.  I've used this technique and know it works.

---

### Post by mithradantor on 2019-11-19
sorry for the late reply! when I do this I still can go to [https://mysite.com](https://mysite.com) and it will give me a warning that the SSL is not valid for this domain :( it wont redirect me to [https://www](https://www)..... I did exactly as you wrote :) 
I will keep trying in the meantime!

---

### Post by SeijiSensei on 2019-11-19
Remove any ServerAlias references to mysite.nl in the other SSL configuration files. Then create a configuration for mysite.nl like this:
```

<VirtualHost *:443>
     ServerName mysite.nl 

     Redirect permanent / https://www.mysite.nl/
</VirtualHost>

```
Does that work?

I assume the other redirections are doing what you want?

---

### Post by mithradantor on 2019-11-21
I will try this, this weekend and I will definately let you know the outcome! once again thank you for your reply!

---

