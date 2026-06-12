---
title: "Ubuntu Server Install"
date: 2006-06-21
forum: Server Platforms
---

### Post by Gscope on 2006-06-21
Hello all, I'm very very new to Linux. My whole plan was to get familiar with Linux by using it as an server OS. I currently have the Ubuntu Server Cd and i'm going to attempt an installation. 

Unfortunately, I've never set up a server and I don't quite understand how the whole process works. But the best teacher is experience :] I plan on using this server as a web server. 


Now down to the question. I was reading the documentation for the server installation and if I'm right there is an option to install a default server or a LAMP Linux, Apache, MySQL, PHP/Perl/python. From my one past experience I remember setting up a mySQL database for my website through the web hosting company I was paying. I'm not sure what it was for but I followed a guide for it :] It would be helpful if I understood what each of those mean. I know what PHP is  


So, do I install a lamp server? and if not what option do I choose. 


Thank you so much :]

---

### Post by foxylad on 2006-06-21
All depends on what you are trying to do. There are significant differences between servers and desktops - which are you actually interested in? Desktop users are usually more interested in installing new exciting apps, while server users want stable secure machines with no bells and whistles. There is nothing to stop you running server programs on a desktop - many developers do this so they can see how their web apps work directly, without having to upload files to another machine.

From your comments you seem to be unsure of what a server actually is. A server supplies services over a network, and these traditionally are web pages (a web server), data (a database server), files (a file server), or email (a mail server). When I say "server" here, I'm talking about a program that runs on a server machine, and several can run on the same machine. Even a desktop machine.

Web servers can supply two sorts of pages - static pages, which never change, or dynamic pages which are generated when a client requests them. Dynamis pages usually pull data out of a databse, and use a scripting language like PHP to turn them into an html page that the client can see. So if you want to run web applications, you need Apache (web server), MySQL (the database) and PHP (or python). Those are the A-M-P of LAMP, and Linux is the L.

So if you are interested in running or developing web apps, you should install LAMP. If you want to create a file or print server, you should go with the standard server install. and if you aren't really interesed in either of these, do a desktop install. The desktop lets you go under the covers when you need to, and I guess that is actually what you want.

---

### Post by Gscope on 2006-06-21
Well I understand what a server is... I just don't know the technical aspects of one. I basically want it to be a web hosting machine , a server. I want it to host a website. And being able to upload any files on the server so my website can utilize them.

So with that said... I basically want it to be like a webhosting companies server ... but free for me because I own it :] My website is for experimental purposes only. 


And by web applications are you refering to Apache Mysql ect...

If not... what web apps could I run ? Exactly what would be one.

---

### Post by foxylad on 2006-06-21
OK, sounds like you want a web server - i.e. the apache part. That will let you host websites on your network.

Web applications are websites written in PHP that do something, rather than just sit there and look pretty. Usually they pull data out of MySQL. Examples are forums like this one, content management systems, photo sharing sites, ebay, etc. If you want to do this, get a good book on PHP - there is a lot of very technical stuff you will have to get your head around.

---

### Post by mscman on 2006-06-21
I'm gonna agree with foxylad on this one, in that you may want to think about just doing a desktop installation.  It will allow you to learn the basics of Linux, yet you'll still be able to do webhosting and experiment with stuff.  That's how I run my webserver from home, just on my desktop machine (which I'm using now).  I think you'll find it a lot easier and more fulfilling if you just do a regular install.

For a good howto on running web services, you may want to check out these links:
[http://doc.gwos.org/index.php/ServerGuide](http://doc.gwos.org/index.php/ServerGuide)
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by Ozitraveller on 2006-06-21
Is this what you had in mind?


Ubuntu 6.06 LTS Server Edition to Include Certified LAMP Stack
[http://www.ubuntu.com/news/lamp](http://www.ubuntu.com/news/lamp)

The Perfect Setup - Ubuntu 6.06 LTS Server (Dapper Drake)
[http://www.howtoforge.com/perfect_setup_ubuntu_6.06](http://www.howtoforge.com/perfect_setup_ubuntu_6.06)
[http://digg.com/linux_unix/How_To_Build_A_LAMP_Server_With_Ubuntu_6.06_LTS](http://digg.com/linux_unix/How_To_Build_A_LAMP_Server_With_Ubuntu_6.06_LTS)

Ubuntu server kernel will not boot
[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/48266](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/48266)

---

### Post by Gscope on 2006-06-22
Im following that "the perfect setup" guide. I was also wondering... Ive read something about Samba... what ever that is, and using it as a way to manage the server from windows? I think thats what I read, Correct me if im wrong :]


What would be the best way to have some kind of control of my server from my windows XP pro comptuer that I use all the time. Im going to have my server down stairs when I finish installing and configuring everything. So it would be nice to be able to have some control over it from the computer in my room.

---

### Post by foxylad on 2006-06-22
Samba allows Windows computers to share files and printers connected to the machine running samba.

To admin the machine remotely, you can either use the command line, or use something like webmin which allows you to carry out most admin tasks from any browser on your networik - including windows machines, obviously.

Webmin is one of those web apps I mentioned above. If you need more information about... Google is your friend!

---

### Post by Gscope on 2006-06-22
How do I attain this notorious samba :]


Oh and another reason why im not using the desktop version is because I dont have enough memory in my computer I using for the server.  It has 128 mb

---

### Post by Ozitraveller on 2006-06-23
Ok, 

firstly, samba is in the main repositories, search for samba, and install samba and smbfs.

Below is some very places for documentation:

1. Unofficial Ubuntu 6.06 (Dapper Drake) Starter Guide
[http://ubuntuguide.org/wiki/Dapper](http://ubuntuguide.org/wiki/Dapper)


2.  Samba Server
[http://ubuntuguide.org/wiki/Dapper#Samba_Server](http://ubuntuguide.org/wiki/Dapper#Samba_Server)
There are section under this that will help you to configure samba.


Secondly, have you thought about having an Xfce desktop? Its quite lightweight.

How to install XFCE
[http://ubuntuguide.org/wiki/Dapper#How_to_install_XFCE](http://ubuntuguide.org/wiki/Dapper#How_to_install_XFCE)

I know some of the other users are running Xfce on 128mb. So give it a try.
I'm using Xfce at the moment! ;-)



Note: I read yesterday that fluxbox is being considered as the second lightweight desktop, Xfce would be the default, and fluxbox would be an alternative. Fluxbox is  even more lightweight than Xfce There are a number of distros that use Fluxbox DSL (Damn Small Linux) [http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/) around 50mb all up, VectorLinux [http://www.vectorlinux.com/](http://www.vectorlinux.com/). Puppy Linux uses Xfce [http://www.puppylinux.org/](http://www.puppylinux.org/)

I hope this helps...

---

### Post by rtcary on 2006-06-25
[QUOTE=Gscope]How do I attain this notorious samba :]


Oh and another reason why im not using the desktop version is because I dont have enough memory in my computer I using for the server.  It has 128 mb[/QUOTE]

Gscope -

In many ways my setup and depth of knowledge is similar to what you are trying to do: I have a home office server on which I post my daily work for my client's (I do software development, including PHP based Web sites) for the legal profession in Windows) and where I post my photographic images for my community photography.  I use a LAMP setup along with an additional database management system: Interbase.  I know just enough to get the system up and running, then I forget it...just use it.

To access the server I use Samba and from my perspective, it is what makes the system so powerful and an ease to use.  If my client phones me and requests a change in a PHP application, I can access the code code from Windows, make the change and have the client see the results instantly.  For my Delphi code I make the change and copy the EXE file to the FTP site where the client can download it.

My Rotary images can be seen at [http://209.204.172.137/rotary/](http://209.204.172.137/rotary/)

Contact me off line if you need any suggestions...

Todd

---

