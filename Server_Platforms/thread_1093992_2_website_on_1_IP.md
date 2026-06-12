---
title: "2 website on 1 IP"
date: 2009-03-12
forum: Server Platforms
---

### Post by kishoreru on 2009-03-12
Hi,
    I am running a ruby on rails application in my server(e.g [www.onesite.com](www.onesite.com)), now I need to host another .html (e.g [www.twosite.com](www.twosite.com)) site on the same server, I am using apache2 as a  web server. 

 I am not able to understand how to run two web sites (different domain) on a single IP.Please need help to slove the problem

 Thanks in advance

---

### Post by volkswagner on 2009-03-12
The [server guide]("https://help.ubuntu.com/8.04/serverguide/C/index.html") documents can help.

Particularly [apache]("https://help.ubuntu.com/8.04/serverguide/C/httpd.html") look at setting up **virtual hosts**.

---

### Post by Grey08 on 2009-03-12
save different files under the same directory, the browser will search the file you need, 

such as 

/var/www/index.html
[ [http://YourIP/index.html](http://YourIP/index.html) ]

/var/www/1.html
[ [http://YourIP/1.html](http://YourIP/1.html)

Correct me.

---

### Post by kishoreru on 2009-03-12
I dont think so, you are correct. I think you didnt got what I want.. for example think my IP is 11.22.33.44 a I two web sites e.g [www.one.com](www.one.com) and [www.two.com](www.two.com). and i want to host the two web-site in same ip (11.22.33.44)

---

### Post by IsmailBhai on 2009-03-12
1 IP address can only point to 1 server.  If you type in the IP address in your browser, it will only connect to that particular IP.  I don't understand what you are trying to do. please explain a little more.  are you trying to do ip forwarding?

---

### Post by BkkBonanza on 2009-03-12
What you want is definitely virtual hosts using apache. That is exactly how all shared hosting works where they put hundreds of web sites on one ip address.

Just read the apache docs regarding virtual hosts and add a few lines of config for each domain name you want on your ip, and away you go. Works fine.

Add code like below to httpd.conf - see docs,

NameVirtualHost *

    <VirtualHost *>
    ServerName [www.one.com](www.one.com)
    DocumentRoot /www/one
    </VirtualHost>

    <VirtualHost *>
    ServerName [www.two.com](www.two.com)
    DocumentRoot /www/two
    </VirtualHost>

And then put files for one.com in the /www/one directory and likewise for two.com. Change the paths to whatever you need for your server but this is the right idea.

---

### Post by BkkBonanza on 2009-03-12
Also note if you want to access your sites without the www subdomain then also add the lines,

ServerAlias one.com

ServerAlias two.com

in the correct place just after the ServerName directives. Usually admins want that behaviour so that's why I mention it.

---

### Post by Iowan on 2009-03-12
[Here]("http://ubuntu-tutorials.com/2008/01/09/setting-up-name-based-virtual-hosting/") is info on name-based virtual hosting.

---

