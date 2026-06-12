---
title: "Help ironing out kinks in this server!"
date: 2005-11-06
forum: Server Platforms
---

### Post by phend-one on 2005-11-06
I'm currently following this "How-To": [ISP-Server Setup - Ubuntu 5.10]("http://www.howtoforge.com/perfect_setup_ubuntu_5.10").

My situation is a little different though.
I've followed it through to the end. Now I'm trying to fix certain parts I didn't understand and ignored.

(1) /etc/hosts
I do not have a domain like [www.myserver.com](www.myserver.com)
I'm interested in a dyndns.org address though.

So the question is: How should I edit this file to accomodate this?
The example shows:
192.168.0.100   server1.example.com     server1

So should mine be 192.168.0.100   server1     server1 ?

Does it make a difference if this server1 name is different from the computer name the ubuntu installer asked from the beginning?

(2) I don't want to use /var/www, I want to use /home/www or something else. If this is not an option, I need to know how to link the directory from my /home/www directory to the /var/www 

Currently my home directory is the largest on the HD.
/ takes up about 10Gb
I'm guessing /var is in /, so I will run out of space sometime in the future.



That's all the problems I can think off the top of my head. Any help is appreciated!

---

### Post by kairu0 on 2005-11-06
It sounds like you're trying to set up an Apache server. Are you going to install BIND, FTP, etc. as well?

For Apache, there's an option in its primary configuration file called CanonicalName or something like that. If you give it the right value than it probably won't matter if you specific that dyndns address in your /etc/hosts.

And as for the Apache root folder (/var/www), you can also set that in the Apache primary configuration file. The option has an obvious name, like DocumentRoot or RootFolder or something.

(DISCLAIMER: I'm obviously no expert on this.)

---

### Post by phend-one on 2005-11-06
Yup, sorry, I should have made it more clear in the original post that I was trying to setup a webserver.

I found that How-To and decided to just follow it without knowing half of the things it was trying to accomplish. Like the bind9 ftp stuff etc.

All I really want is a place I can mess around with and access from the 'net. I just want to test out new things.

That guide provided me with the means, but didn't really tell me what it was all about.

I'm sure all I really need is Apache2, php5, mySQL and some sort of web administration program to better manage this. Something like LAMP or XAMPP, but I heard they weren't that secure and I also wanted to learn more about linux / webservers.

---

### Post by dbee on 2005-11-07
try webmin ... it's pretty much exactly what you need. And it's fairly secure if you set it to be accessed from localhost only in it's config file.

Just go up to synaptic and search for webmin ... then install all the modules you need.

---

### Post by phend-one on 2005-11-07
Thanks, I will look into webmin.


Any ideas how to undo all these things I've done from following the guide/tutorial/howto? I feel like starting from scratch. Unless there's an easy way to fix all this mess?


**EDIT:** Does webmin come with support for Apache2? I tried the one from Synaptic and it was an older version, but I tried anyways.

---

### Post by dbee on 2005-11-09
You may want to start again just so you can be absolutely sure what you've got on your server and what you haven't. HOW-TO's are good to get you started, but it's best to build on them from there ...

I'm fairly sure that the webmin-apache package covers apache2 also...

---

