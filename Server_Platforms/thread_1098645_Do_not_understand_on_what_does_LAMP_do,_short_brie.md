---
title: "Do not understand on what does LAMP do, short brief please~!!"
date: 2009-03-17
forum: Server Platforms
---

### Post by Grey08 on 2009-03-17
Hi there
I m using Ubuntu server 8.10 with GUI, at the first few days after i installed Ubuntu server, i have installed Apache2 for simple web server. After get bored with simple web server, i read some articles about LAMP and i thought that LAMP was like some client base PHP maker or forum services, so i installed it with command, [HTML] sudo tasksel install lamp-server [/HTML]

After the installation, i found out at the bottom of the page from /var/www/ has this: 

[IMG]http://edwardchia.dyndns.org/pic/2.jpg[/IMG]
 [ Apache/2.2.9 (Ubuntu) PHP/5.2.6-2ubuntu4.1 with Suhosin-Patch Server at 192.168.1.8 Port 80 ]


. Is that alright?? 

I need some explanation on what is LAMP, how do i use it? What do mysql, myphp do? Do they have any GUI or client base for easy configuration?

Thanks in advanced.

---

### Post by namaku0 on 2009-03-17
Linux - Apache - MySQL - PHP

[http://en.wikipedia.org/wiki/LAMP_(software_bundle)](http://en.wikipedia.org/wiki/LAMP_(software_bundle))

---

### Post by raul_ on 2009-03-17
Yes, it's not actually an application, it just brings the software installed by default so you won't have to go through the hassle of installing the pieces one by one. Those 4 work well together and they are enough for doing most stuff.

---

### Post by Grey08 on 2009-03-18
-Does that mean i can now use php language to host a web site? 

-Refer to the picture above, do i have mysql?How do i use mysql?

-I m thinking to host forum, is there anyway i can own a forum with my web server?

---

### Post by windependence on 2009-03-18
MySQL is a database. PHP is a scripting laguage. Yes, most forum software uses these components. I would suggest simple machines forum software.

-Tim

---

### Post by ddrichardson on 2009-03-18
> **Grey08 said:**
> -Does that mean i can now use php language to host a web site?

Yes 

> **Grey08 said:**
> -Refer to the picture above, do i have mysql?

Yes if you installed the command you gave.

> **Grey08 said:**
> How do i use mysql?

Outside the scope of this forum really but mostly you only need to use phpMyAdmin to create a database. In fact phpBB which is a popular forum system does most of it for you.

> **Grey08 said:**
> -I m thinking to host forum, is there anyway i can own a forum with my web server?

[http://www.phpbb.com/](http://www.phpbb.com/) I have used it and it's very popular.

---

### Post by Grey08 on 2009-03-18
> **ddrichardson said:**
> Yes 
Yes if you installed the command you gave.




Refer to this shown at bottom of my site, [Apache/2.2.9 (Ubuntu) PHP/5.2.6-2ubuntu4.1 with Suhosin-Patch Server at 192.168.1.8 Port 80]

does that mean i already have mysql? How do i start using it?

regards,
Grey08

---

### Post by Grey08 on 2009-03-18
> **windependence said:**
> MySQL is a database. PHP is a scripting laguage. Yes, most forum software uses these components. I would suggest simple machines forum software.

-Tim

Is there any free services forum software i can install at my machine?

---

### Post by ddrichardson on 2009-03-18
> **Grey08 said:**
> Is there any free services forum software i can install at my machine?
I linked to one in my last post and Tim linked to [http://www.simplemachines.org/](http://www.simplemachines.org/)

---

### Post by Grey08 on 2009-03-18
What about MySQL? 

How do i start using it?

---

### Post by ddrichardson on 2009-03-19
> **Grey08 said:**
> What about MySQL? 

How do i start using it?
[https://help.ubuntu.com/8.04/serverguide/C/mysql.html](https://help.ubuntu.com/8.04/serverguide/C/mysql.html)
[https://help.ubuntu.com/community/ApacheMySQLPHP#Phpmyadmin%20and%20mysql-admin](https://help.ubuntu.com/community/ApacheMySQLPHP#Phpmyadmin%20and%20mysql-admin)

---

