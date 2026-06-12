---
title: "404 Not Found error with nginx"
date: 2021-11-06
forum: Server Platforms
---

### Post by sniper8752 on 2021-11-06
I have a subdomain called mail on mydomain.com.  I am running nginx on the server.  I have a mail.mydomain.com.conf file in sites-available, and linked in the sites-enabled folder.  My server's hostname is "mail".  In the .conf file, I've set the server_name to mail.mydomain.com, and root to /var/www/html/roundcube.  I want to be able to access the installer/index.php file.  I go to in my browser, mail.mydomain.com/installer, and I get a 404 Not Found error message.  The files/folders are owned by www-data.  What am I doing wrong?

---

### Post by TheFu on 2021-11-06
> **sniper8752 said:**
>   I go to in my browser, mail.mydomain.com/installer, and I get a 404 Not Found error message.  The files/folders are owned by www-data.  _What am I doing wrong?_

You didn't actually post the config file for the site or the ls -al for the location with the files you expect to work.
You didn't say if you setup DNS either.
Did you look at the nginx log files for that specific domain?  What's in the access log and the error log?

---

### Post by sniper8752 on 2021-11-09
I installed the following for DNS: [FONT=monospace][COLOR=#000000]bind9 bind9utils bind9-dnsutils bind9-doc bind9-host.
 The roundcube directory:

[/COLOR][/FONT]```
[FONT=monospace][COLOR=#000000]ls -al[/COLOR]
total 508
drwxrwxr-x 17 www-data www-data   4096 Nov  6 16:09 [COLOR=#5454FF]**.**[/COLOR]
drwxr-xr-x  3 root     root       4096 Nov  6 16:19 [COLOR=#5454FF]**..**[/COLOR]
-rw-rw-r--  1 www-data www-data    252 Nov  6 15:54 .editorconfig
drwxrwxr-x  8 www-data www-data   4096 Nov  6 15:54 [COLOR=#5454FF]**.git**[/COLOR]
drwxrwxr-x  3 www-data www-data   4096 Nov  6 15:54 [COLOR=#5454FF]**.github**[/COLOR]
-rw-rw-r--  1 www-data www-data    527 Nov  6 15:54 .gitignore
-rw-rw-r--  1 www-data www-data   2551 Nov  6 15:54 .htaccess
drwxrwxr-x  2 www-data www-data   4096 Nov  6 15:54 [COLOR=#5454FF]**.tx**[/COLOR]
-rw-rw-r--  1 www-data www-data 200198 Nov  6 15:54 CHANGELOG.md
-rw-rw-r--  1 www-data www-data  12661 Nov  6 15:54 INSTALL
-rw-rw-r--  1 www-data www-data  35147 Nov  6 15:54 LICENSE
-rw-rw-r--  1 www-data www-data   4130 Nov  6 15:54 Makefile
-rw-rw-r--  1 www-data www-data   4133 Nov  6 15:54 README.md
-rw-rw-r--  1 www-data www-data    967 Nov  6 15:54 SECURITY.md
drwxrwxr-x  7 www-data www-data   4096 Nov  6 15:54 [COLOR=#5454FF]**SQL**[/COLOR]
-rw-rw-r--  1 www-data www-data   4657 Nov  6 15:54 UPGRADING
drwxrwxr-x  2 www-data www-data   4096 Nov  6 15:54 [COLOR=#5454FF]**bin**[/COLOR]
-rw-rw-r--  1 www-data www-data    979 Nov  6 15:54 composer.json
-rw-rw-r--  1 www-data www-data 127619 Nov  6 16:04 composer.lock
drwxrwxr-x  2 www-data www-data   4096 Nov  6 15:54 [COLOR=#5454FF]**config**[/COLOR]
-rw-rw-r--  1 www-data www-data  11191 Nov  6 15:54 index.php
drwxrwxr-x  3 www-data www-data   4096 Nov  6 15:54 [COLOR=#5454FF]**installer**[/COLOR]
-rw-rw-r--  1 www-data www-data   4298 Nov  6 15:54 jsdeps.json
drwxrwxr-x  2 www-data www-data   4096 Nov  6 23:13 [COLOR=#5454FF]**logs**[/COLOR]
drwxrwxr-x 37 www-data www-data   4096 Nov  6 15:54 [COLOR=#5454FF]**plugins**[/COLOR]
drwxrwxr-x  8 www-data www-data   4096 Nov  6 15:54 [COLOR=#5454FF]**program**[/COLOR]
drwxrwxr-x  3 www-data www-data   4096 Nov  6 15:54 [COLOR=#5454FF]**public_html**[/COLOR]
drwxrwxr-x  5 www-data www-data   4096 Nov  6 15:54 [COLOR=#5454FF]**skins**[/COLOR]
drwxrwxr-x  2 www-data www-data   4096 Nov  6 15:54 [COLOR=#5454FF]**temp**[/COLOR]
drwxrwxr-x  7 www-data www-data   4096 Nov  6 15:54 [COLOR=#5454FF]**tests**[/COLOR]
drwxrwxr-x 13 www-data www-data   4096 Nov  6 16:04 [COLOR=#5454FF]**vendor**[/COLOR]

[/FONT]
```[FONT=monospace]
The installer directory:
[/FONT]```
[FONT=monospace][COLOR=#000000]ls -al[/COLOR]
total 84
drwxrwxr-x  3 www-data www-data  4096 Nov  6 15:54 [COLOR=#5454FF]**.**[/COLOR]
drwxrwxr-x 17 www-data www-data  4096 Nov  6 16:09 [COLOR=#5454FF]**..**[/COLOR]
-rw-rw-r--  1 www-data www-data  9222 Nov  6 15:54 check.php
-rw-rw-r--  1 www-data www-data  1655 Nov  6 15:54 client.js
-rw-rw-r--  1 www-data www-data 22714 Nov  6 15:54 config.php
drwxrwxr-x  2 www-data www-data  4096 Nov  6 15:54 [COLOR=#5454FF]**images**[/COLOR]
-rw-rw-r--  1 www-data www-data  6734 Nov  6 15:54 index.php
-rw-rw-r--  1 www-data www-data  3348 Nov  6 15:54 styles.css
-rw-rw-r--  1 www-data www-data 16448 Nov  6 15:54 test.php

[/FONT]
```[FONT=monospace]
the mail.mydomain.com.conf file:

[/FONT]```


server {
    listen 80;
    server_name mail.mydomain.com;
    root /var/www/html/roundcube;


    error_log /var/log/nginx/roundcube.error;
    access_log /var/log/nginx/roundcube.access;


    location ~ /.well-known/acme-challenge {
      allow all;
    }
   location ~ ^/(README|INSTALL|LICENSE|CHANGELOG|UPGRADING)$ {
      deny all;
    }
    location ~ ^/(bin|SQL)/ {
      deny all;
    }
   # A long browser cache lifetime can speed up repeat visits to your page
    location ~* \.(jpg|jpeg|gif|png|webp|svg|woff|woff2|ttf|css|js|ico|xml)$ {
       access_log        off;
       log_not_found     off;
       expires           360d;
    }


    index index.php index.html index.htm;


    location / {
        try_files $uri $uri/ =404;
    }


    location ~ \.php$ {
        include snippets/fastcgi-php.conf;
        fastcgi_pass unix:/var/run/php/php7.4-fpm.sock;
     }


    location ~ /\.ht {
        deny all;
    }


}



```[FONT=monospace]


[/FONT]

---

### Post by mIk3_08 on 2021-11-09
> **sniper8752 said:**
> I installed the following for DNS: [FONT=monospace][COLOR=#000000]bind9 bind9utils bind9-dnsutils bind9-doc bind9-host.
 The roundcube directory:

[/COLOR][/FONT]```
[FONT=monospace][COLOR=#000000]ls -al[/COLOR]
total 508
drwxrwxr-x 17 www-data www-data   4096 Nov  6 16:09 [COLOR=#5454FF]**.**[/COLOR]
drwxr-xr-x  3 root     root       4096 Nov  6 16:19 [COLOR=#5454FF]**..**[/COLOR]
-rw-rw-r--  1 www-data www-data    252 Nov  6 15:54 .editorconfig
drwxrwxr-x  8 www-data www-data   4096 Nov  6 15:54 [COLOR=#5454FF]**.git**[/COLOR]
drwxrwxr-x  3 www-data www-data   4096 Nov  6 15:54 [COLOR=#5454FF]**.github**[/COLOR]
-rw-rw-r--  1 www-data www-data    527 Nov  6 15:54 .gitignore
-rw-rw-r--  1 www-data www-data   2551 Nov  6 15:54 .htaccess
drwxrwxr-x  2 www-data www-data   4096 Nov  6 15:54 [COLOR=#5454FF]**.tx**[/COLOR]
-rw-rw-r--  1 www-data www-data 200198 Nov  6 15:54 CHANGELOG.md
-rw-rw-r--  1 www-data www-data  12661 Nov  6 15:54 INSTALL
-rw-rw-r--  1 www-data www-data  35147 Nov  6 15:54 LICENSE
-rw-rw-r--  1 www-data www-data   4130 Nov  6 15:54 Makefile
-rw-rw-r--  1 www-data www-data   4133 Nov  6 15:54 README.md
-rw-rw-r--  1 www-data www-data    967 Nov  6 15:54 SECURITY.md
drwxrwxr-x  7 www-data www-data   4096 Nov  6 15:54 [COLOR=#5454FF]**SQL**[/COLOR]
-rw-rw-r--  1 www-data www-data   4657 Nov  6 15:54 UPGRADING
drwxrwxr-x  2 www-data www-data   4096 Nov  6 15:54 [COLOR=#5454FF]**bin**[/COLOR]
-rw-rw-r--  1 www-data www-data    979 Nov  6 15:54 composer.json
-rw-rw-r--  1 www-data www-data 127619 Nov  6 16:04 composer.lock
drwxrwxr-x  2 www-data www-data   4096 Nov  6 15:54 [COLOR=#5454FF]**config**[/COLOR]
-rw-rw-r--  1 www-data www-data  11191 Nov  6 15:54 index.php
drwxrwxr-x  3 www-data www-data   4096 Nov  6 15:54 [COLOR=#5454FF]**installer**[/COLOR]
-rw-rw-r--  1 www-data www-data   4298 Nov  6 15:54 jsdeps.json
drwxrwxr-x  2 www-data www-data   4096 Nov  6 23:13 [COLOR=#5454FF]**logs**[/COLOR]
drwxrwxr-x 37 www-data www-data   4096 Nov  6 15:54 [COLOR=#5454FF]**plugins**[/COLOR]
drwxrwxr-x  8 www-data www-data   4096 Nov  6 15:54 [COLOR=#5454FF]**program**[/COLOR]
drwxrwxr-x  3 www-data www-data   4096 Nov  6 15:54 [COLOR=#5454FF]**public_html**[/COLOR]
drwxrwxr-x  5 www-data www-data   4096 Nov  6 15:54 [COLOR=#5454FF]**skins**[/COLOR]
drwxrwxr-x  2 www-data www-data   4096 Nov  6 15:54 [COLOR=#5454FF]**temp**[/COLOR]
drwxrwxr-x  7 www-data www-data   4096 Nov  6 15:54 [COLOR=#5454FF]**tests**[/COLOR]
drwxrwxr-x 13 www-data www-data   4096 Nov  6 16:04 [COLOR=#5454FF]**vendor**[/COLOR]

[/FONT]
```[FONT=monospace]
The installer directory:
[/FONT]```
[FONT=monospace][COLOR=#000000]ls -al[/COLOR]
total 84
drwxrwxr-x  3 www-data www-data  4096 Nov  6 15:54 [COLOR=#5454FF]**.**[/COLOR]
drwxrwxr-x 17 www-data www-data  4096 Nov  6 16:09 [COLOR=#5454FF]**..**[/COLOR]
-rw-rw-r--  1 www-data www-data  9222 Nov  6 15:54 check.php
-rw-rw-r--  1 www-data www-data  1655 Nov  6 15:54 client.js
-rw-rw-r--  1 www-data www-data 22714 Nov  6 15:54 config.php
drwxrwxr-x  2 www-data www-data  4096 Nov  6 15:54 [COLOR=#5454FF]**images**[/COLOR]
-rw-rw-r--  1 www-data www-data  6734 Nov  6 15:54 index.php
-rw-rw-r--  1 www-data www-data  3348 Nov  6 15:54 styles.css
-rw-rw-r--  1 www-data www-data 16448 Nov  6 15:54 test.php

[/FONT]
```[FONT=monospace]
the mail.mydomain.com.conf file:

[/FONT]```


server {
    listen 80;
    server_name mail.mydomain.com;
    root /var/www/html/roundcube;


    error_log /var/log/nginx/roundcube.error;
    access_log /var/log/nginx/roundcube.access;


    location ~ /.well-known/acme-challenge {
      allow all;
    }
   location ~ ^/(README|INSTALL|LICENSE|CHANGELOG|UPGRADING)$ {
      deny all;
    }
    location ~ ^/(bin|SQL)/ {
      deny all;
    }
   # A long browser cache lifetime can speed up repeat visits to your page
    location ~* \.(jpg|jpeg|gif|png|webp|svg|woff|woff2|ttf|css|js|ico|xml)$ {
       access_log        off;
       log_not_found     off;
       expires           360d;
    }


    index index.php index.html index.htm;


    location / {
        try_files $uri $uri/ =404;
    }


    location ~ \.php$ {
        include snippets/fastcgi-php.conf;
        fastcgi_pass unix:/var/run/php/php7.4-fpm.sock;
     }


    location ~ /\.ht {
        deny all;
    }


}



```[FONT=monospace]


[/FONT]
Please correct me if I'm wrong, I think you should declare the site location folder from the nginx server. This should be inside the nginx.conf
It should be declared as:
```
include /sitelocationfolder/*.conf
```
What I'm thinking is that the server port declaration is different from the nginx declaration. That's only my opinion. I don't know if it sync on you. I'm asking for an apology for my english.
I am try to explain further but I'm not that good at it. So Good Luck and Regards.

---

### Post by TheFu on 2021-11-09
Bind needs all sorts of manual configuration. Just installing it doesn't do anything.
You can cheat by modifying the local /etc/hosts files on every system to point to the correct place.  That is both on the clients and on the server. With fewer than 5 systems, this is easiest.  With more than 5, perhaps running a pi-hole that also does DNS makes sense.  In a work environment, a fully configured DNS makes the most sense.

I don't use roundcube and avoid php-based webapps, so I can't help with it. Sorry.
For nginx look at the access and error logs. Those are critical.

---

### Post by ameinild on 2021-11-09
To me it also sounds like DNS is not configured. Try and do a DNS lookup for the site to see if you get a response:

```
nslookup mail.mydomain.com
```

You should get an output similar to:

```
Server:         127.0.0.1
Address:        127.0.0.1#53

Name:    mail.mydomain.com
Address: your.ip.add.ress
```

If not, then DNS is not configured properly.

---

### Post by sniper8752 on 2021-11-11
I've updated my hosts file with the following entries:
mail 127.0.0.1
mail.mydomain.com 127.0.0.1

Upon attempting to load the page, I am confronted with the same 404 error message, as well as in the access log file.

---

### Post by TheFu on 2021-11-11
That doesn't look correct.

You need to use the correct format for the /etc/hosts file. There are thousands of example and articles about that on the internet.  We don't get to make up whatever format we like.
Also, 127.0.0.1 or any IP that begins with 127 is only for the localhost.  It won't help a client locate any remote server (different machine). It is useful to connect to different servers on the same logical host machine only.

---

### Post by sniper8752 on 2021-11-11
I've updated the hosts file to be <ip>  <hostname> instead.
 It still throws a 404.
I see this in error.log: 2021/11/11 19:03:22 [warn] 769#769: conflicting server name "mail.mydomain.com" on 0.0.0.0:80, ignored

---

### Post by TheFu on 2021-11-11
Less descriptions.
More facts.  Please post files and CLEARLY say where they are and one which system they are on.
For example, the client system (running a browser) doesn't magically know anything about the server /etc/hosts updates.  The client machine /etc/hosts file must be updated.

Basic IP networking.  How's your knowledge at that?  If weak, best to get the basics down first.

---

