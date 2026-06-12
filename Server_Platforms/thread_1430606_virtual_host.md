---
title: "virtual host"
date: 2010-03-15
forum: Server Platforms
---

### Post by bluedrakonis on 2010-03-15
I have a website up and running usuing ubuntu 9.1 can anyone tell me how to host more than one site on it, i know you use the virtual host of apache but how? thanks in advance guys

---

### Post by dudumomo on 2010-03-15
Hi Bluedrakonis,
Yes, it is quite easy to do so. You will have to create set up a virtual host.
You can read my how to about LAMP: [http://www.freelydifferent.com/self-hosting/lamp-for-linux-apache-mysql-php/](http://www.freelydifferent.com/self-hosting/lamp-for-linux-apache-mysql-php/)
(And let me know if you have any problem, hence, I will improve it thanks to you)

Anyway, in short, you have to redirect your subdomain to your IP, then, create a folder in /var/www by example, then add your subdomain in your /etc/hosts
And in /etc/apache2/sites-available, create (or modify) a virtual host.
Example: 
```
<VirtualHost *:80>
        ServerAdmin spam_me@freelydifferent.com  ## your real address
        ServerName freelydifferent.com   ## what you have added in your /etc/hosts
        ServerAlias www.freelydifferent.com  ## From your domain redirection
 
        DocumentRoot /var/www/freelydifferent  ## The folder you have just created
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory /var/www/freelydifferent> ## The folder you have just created
                Options Indexes FollowSymLinks MultiViews
etc..
```

---

### Post by Lucky. on 2010-03-15
dudumomo, that's a real nice tutorial.  I've been working on one myself, but then I took a detour and went to file permissions, IP addressing, and shell commands.  One of these decades I might actually get around to writing about the fun stuff!

---

### Post by dudumomo on 2010-03-16
Thank you !
Nice to hear that !

---

### Post by Iowan on 2010-03-16
[Here]("https://help.ubuntu.com/9.10/serverguide/C/httpd.html") is another help page to check.

---

### Post by bluedrakonis on 2010-03-16
thanks guys, i think that has it up and going

---

