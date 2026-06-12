---
title: "Server/domain help"
date: 2007-06-13
forum: Server Platforms
---

### Post by Thirtysixway on 2007-06-13
I'm trying to make it so I can setup more than one website with ubuntu.

I have it right now where you go to my ip and it has a site under /var/www but i need it so i can add domains like example.com and example2.com and have them be different.  I already have the domains.

I'm new to setting up things like this, so if anyone can help me it would be great.  do i have to install something like dns software? :(


I got subdomains working from a tutorial, but i don't know how to do .com domains.
help please?:D


I have apache2, php5, mysql, and phpmyadmin installed.

---

### Post by az on 2007-06-13
In /etc/apache2/sites-availble, you have a default site set up.  Copy that file and call it what you want.  Edit that file to adjust your virtual host domain name and document root and so forth.

Then run

sudo a2ensite (name of site filename) 
to enable that site

you will have to force-reload apache for your site to be served.  You can add as many virtual hosts as you like, just make a file for each of them.

---

### Post by Jolly-Swagman on 2007-06-13
Thirtysixway,

Have found this to be useful link but havent got around to trying full implification yet I,m still in testing phase for my Lamp server.
[http://www.openfree.org/pet/index.php/Apache_2.0_-_Basic_-_on_Ubuntu_Linux](http://www.openfree.org/pet/index.php/Apache_2.0_-_Basic_-_on_Ubuntu_Linux)


Jolly-Swagman

---

