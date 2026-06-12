---
title: "How to make ubuntu my website"
date: 2006-06-08
forum: Server Platforms
---

### Post by wolf414 on 2006-06-08
How do I make ubuntu run a website?? and can I run windows on 1 hard drive (like be on windows) and have ubuntu running my website on the other hard drive.?? at the same time? (1 computer)

If not cancel this ?
How do I make ubuntu run my website??

---

### Post by oly on 2006-06-08
you can not really run both simultanously unless you use some sort of emulation or virulisation software ie run one os inside another.

however there are two ways to server websites one is to get the ubuntu server distrubution which sets up just about everything you need, the other is to install apache2 package from synaptics.

[http://localhost/](http://localhost/) is your web address on first install and /var/www/ is where you put your website files.

---

### Post by Iowan on 2006-06-08
[http://www.howtoforge.com/perfect_setup_ubuntu_5.10]("http://www.howtoforge.com/perfect_setup_ubuntu_5.10")
or
[http://www.howtoforge.com/perfect_setup_ubuntu_6.06]("http://www.howtoforge.com/perfect_setup_ubuntu_6.06")

[http://www.ubuntuwebservers.com/]("http://www.ubuntuwebservers.com/")

---

### Post by az on 2006-06-08
[QUOTE=wolf414]How do I make ubuntu run a website?? 

??[/QUOTE]
Install the LAMP stack.
LAMP is Linux Apache Mysql and Php.  You usually need those to run a dynamic website.


sudo apt-get install apache2 php5 mysql-client-5.0 mysql-server-5.0 phpmyadmin libapache2-mod-php5 libapache2-mod-auth-mysql php5-mysql

([http://www.ubuntuforums.org/showpost.php?p=1108004&postcount=8](http://www.ubuntuforums.org/showpost.php?p=1108004&postcount=8))


You can do that on your current setup, if you don't want to have a dedicated box as your server.  While running a desktop (graphical environment) is probably a security risk you want to avoid when you set up a server connected to the web, it does not prevent you from running the LAMP stack applications.


Here:

[https://wiki.ubuntu.com/Servers](https://wiki.ubuntu.com/Servers)
[https://wiki.ubuntu.com/ApacheMySQLPHP?action=show&redirect=ApachePHPMySQL](https://wiki.ubuntu.com/ApacheMySQLPHP?action=show&redirect=ApachePHPMySQL)

[QUOTE=wolf414]
and can I run windows on 1 hard drive (like be on windows) and have ubuntu running my website on the other hard drive.????[/QUOTE]

You can dual boot.

[QUOTE=wolf414]
 at the same time? (1 computer)??[/QUOTE]
As stated, you would need to have some sort of virtual machine like vmware, qemu or xen.  You would need to either boot into windows and virtualise your linux system or boot into linux and virtualise your windows desktop.

Can you just find an old computer and install the ubuntu LAMP stack on that?  You don't even need a monitor.

And what do you want your website to do?  What features do you need?

---

### Post by wolf414 on 2006-06-08
So I would be better off using my old computer p3 800mz. And setting that up with ubuntu server and then connecting it to my cable connection(with my other computer) Then running it off of there? Then it would be more secure right? and alot easier to maintian. And also if that  works it could be up 24/7 right?

O and i just want a regular website. Like html and maby some php scripts. I only know how to use dreamweaver. so I am no expert on websites. O and mysql for forums phpbb2.

This is my current website. 
[http://therespected.org/](http://therespected.org/)

And does it mater what the specs are on my computer for running a website?
and how does getting the [www.MySite.com](www.MySite.com) to run on ubuntu work?

I am very new to all of this. Just to let everybody know. before 1 week ago I never used linux.

---

### Post by az on 2006-06-08
[QUOTE=wolf414]So I would be better off using my old computer p3 800mz. And setting that up with ubuntu server and then connecting it to my cable connection(with my other computer) Then running it off of there? Then it would be more secure right? and alot easier to maintian. And also if that  works it could be up 24/7 right?

O and i just want a regular website. Like html and maby some php scripts. I only know how to use dreamweaver. so I am no expert on websites. O and mysql for forums phpbb2.

This is my current website. 
[http://therespected.org/](http://therespected.org/)

And does it mater what the specs are on my computer for running a website?
and how does getting the [www.MySite.com](www.MySite.com) to run on ubuntu work?

I am very new to all of this. Just to let everybody know. before 1 week ago I never used linux.[/QUOTE]

Guns, eeew!

Anyway, depending on your traffic, you can run a nice little webserver on a pentium I!  If you have more than ten people on at the same time, it will be a little slow.  It depends.  As for your site, you need a CMS.  I like drupal (drupal.org) but look at cmsmatrix.org to see what is available and best suits your needs.

---

### Post by wolf414 on 2006-06-08
So drupal is like a portal run on php? And what about my ? how to get my site linked to [www.Whatever.com](www.Whatever.com) or org or net. I need to buy a domain frist right? then when i set the server up i input the info there then my computer will host it 24/7?

And btw I apreciate all the help. srry if I am a pain, but I'm really new to all this. Thanks

---

### Post by az on 2006-06-10
[QUOTE=wolf414]So drupal is like a portal run on php? And what about my ? how to get my site linked to [www.Whatever.com](www.Whatever.com) or org or net. I need to buy a domain frist right? then when i set the server up i input the info there then my computer will host it 24/7?

And btw I apreciate all the help. srry if I am a pain, but I'm really new to all this. Thanks[/QUOTE]
By portal, you mean a website?  One type of website software is a CMS (Content Management System - it is very versatile and typically includes blogs, forums, and lots of other features.  That's probably what you want.)  To get your box found by domain name requires a static IP address (from your ISP - you pay more for it than an IP address that changes often)  as well as a registered domain name (you pay about 20 bucks a year for this service)

If you don't have a static ip address, you can use the free dynamic dns servi ce offered by a number of different providers.  Google "dynamic dns".   The way that would work is that you set it up and then people can access your box using

yourname.dyndns.com
 
A decent dynamic dns client on ubuntu is ddclient.  You can install it using synaptic


There is a server guide in the documentation wiki.  Probably there should be a page made about basement webservers.

---

