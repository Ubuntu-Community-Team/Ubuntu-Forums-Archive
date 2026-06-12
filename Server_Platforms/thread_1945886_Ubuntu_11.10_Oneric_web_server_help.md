---
title: "Ubuntu 11.10 Oneric web server help"
date: 2012-03-23
forum: Server Platforms
---

### Post by Hyodoh on 2012-03-23
Hey guys I was hoping I could get some help over here. Now just to let anyone know I'm a nub when it comes to this stuff. 

But anyway, I attempted to create a web server for me to test a website I'm building for one of my classes. I used the desktop version of ubuntu and installed Lamp on it to make it a web server, or try to make it a web sever. Everything installed good, at least I think. 

I was struggling with moving files into the /var/www folder, so I found a tutorial and switched it to my /home/www folder. I think I did it right, I'm not sure and I'm not 100% sure where I found that tutorial at. 

If I type in my IP address for my "server," I can see everything that's in the www folder. The problem I'm having at the moment is actually opening those files. I'm using dreamweaver on my desktop, and using FTP to move it over to my websever. Now when I do that, and go to the IP and try to open it i get a: 403 forbidden you don’t have permission to access / on this server. ANd this is where I'm 100% stumped. I was hoping you guys could point in the right direction so I can just dump stuff onto the server and type the IP into a browser and have stuff open so I can test my site.

---

### Post by dharmavir on 2012-03-24
Hi Hyodoh,

First thing you did wrong is that you should not move your /www folder to /home directory, what you should do is you should move your files from your working folder which can be /home/www to /var/www but if you just want to use your desktop as we development machine and not as actual web-server you can try another less secure option too.

1) You should use sudo to copy file from /home/www to /var/www - 
 $ sudo cp -R /home/www/* /var/www
That's it your all file while be copied over to /var/www, now here when you sudo something you have to provide your password. Password for your current (admin) account, with which you have logged in.

2) Another way is you can provide write permission to /var/www for all users using following command - but understand that this is not a secure option for production server and you should just try it for your development machine.
 $ sudo chmod -R 777 /var/www

Even after doing all stuff mentioned you get the files downloaded than the problem is that you don't have server side program install which is binaries or compilers or mods for the language in which you're trying to write program/website/web-app;

I am not sure what you're using php / ruby / python or something else.
but if it's php you should do following:

 $ sudo apt-get install php5 libapache2-mod-php5
 $ sudo service apache2 restart

Try googling and you should find good help or just post back if problem still persists.

---

