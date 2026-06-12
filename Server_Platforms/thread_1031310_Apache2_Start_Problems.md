---
title: "Apache2 Start Problems"
date: 2009-01-05
forum: Server Platforms
---

### Post by mixted on 2009-01-05
Hy everyone,i have installed on my sistem ubuntu 8.10 server and i have problems running apache2.i installed myself apache2,mysql,phpmyadmin and what i need.all the other services start normally but the apache2 service doesn't want to start
> mixted@mxc:~$ sudo /etc/init.d/apache2 start
 * Starting web server apache2                                                  apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
so the message appears but when i try localhost or [http://myip](http://myip) it doens't connect : 
> Failed Connection
Firefox can't establish a connection with server [www.*****.ro](www.*****.ro).
this message appears also when i try with localhost or with myip,i have checked to see if port 80 is blocked but i didn't observed anithyng strange....so please any suggestions?
Apache2 Version : 2.2.9
Distro : Ubuntu 8.10 Server 32-bit running on 64
Mod's enabled : perl,ssl,ruby

---

### Post by Uluen on 2009-01-05
```
# cat /etc/hostname
```, is that the same hostname you have given Apache?

The error message tells you what's wrong.

---

### Post by mixted on 2009-01-05
it seems not,the hostname is mxc but i think i sorted out finally,is seems that eaccelerator that i have installed is for php 5.2.4 and i have 5.2.6
anyhow i have succesfully made apache2 work by removing eaccelerator but i've still have some problems.i have eliminated the erros from the apache2 log with the binary and .ini php modules but i can't still acces port 80 on my server.i type the addres but it shows that it's loading but it doesn't load so fast,over 30seconds to load something.on the 81 port everything works very well,very fast i must say
i have realized that it can be the firewall but i have disabled it to test this and still it doesn't loads how it should.i have checked the error log and is full with lines like this : 
> [Mon Jan 05 20:56:50 2009] [notice] child pid 29256 exit signal Segmentation fault (11)
[Mon Jan 05 20:56:50 2009] [notice] child pid 29259 exit signal Segmentation fault (11)
[Mon Jan 05 20:56:50 2009] [notice] child pid 29260 exit signal Segmentation fault (11)
[Mon Jan 05 20:56:50 2009] [notice] child pid 29261 exit signal Segmentation fault (11)
[Mon Jan 05 20:56:51 2009] [notice] child pid 29265 exit signal Segmentation fault (11)
[Mon Jan 05 20:56:51 2009] [notice] child pid 29462 exit signal Segmentation fault (11)
[Mon Jan 05 20:56:51 2009] [notice] child pid 29463 exit signal Segmentation fault (11)
[Mon Jan 05 20:56:51 2009] [notice] child pid 29464 exit signal Segmentation fault (11)
[Mon Jan 05 20:56:51 2009] [notice] child pid 29465 exit signal Segmentation fault (11)
[Mon Jan 05 20:56:51 2009] [notice] child pid 29466 exit signal Segmentation fault (11)
[Mon Jan 05 20:56:51 2009] [notice] child pid 29467 exit signal Segmentation fault (11)
[Mon Jan 05 20:56:51 2009] [notice] child pid 29468 exit signal Segmentation fault (11)
[Mon Jan 05 20:56:51 2009] [notice] child pid 29469 exit signal Segmentation fault (11)
[Mon Jan 05 20:56:51 2009] [notice] child pid 29470 exit signal Segmentation fault (11)
[Mon Jan 05 20:56:51 2009] [notice] child pid 29471 exit signal Segmentation fault (11)
[Mon Jan 05 20:56:51 2009] [notice] child pid 29472 exit signal Segmentation fault (11)
[Mon Jan 05 20:56:51 2009] [notice] child pid 29474 exit signal Segmentation fault (11)
[Mon Jan 05 20:56:51 2009] [notice] child pid 29476 exit signal Segmentation fault (11)
[Mon Jan 05 20:56:51 2009] [notice] child pid 29477 exit signal Segmentation fault (11)
[Mon Jan 05 20:56:51 2009] [notice] child pid 29478 exit signal Segmentation fault (11)
[Mon Jan 05 20:56:51 2009] [notice] child pid 29479 exit signal Segmentation fault (11)
[Mon Jan 05 20:56:51 2009] [notice] child pid 29480 exit signal Segmentation fault (11)
[Mon Jan 05 20:56:51 2009] [notice] child pid 29481 exit signal Segmentation fault (11)
[Mon Jan 05 20:56:51 2009] [notice] child pid 29485 exit signal Segmentation fault (11)
any suggestions?

---

### Post by rururudy on 2009-04-29
Took me a few hours to track this down, but here is what fixed if for me ... 

> echo "fs.epoll.max_user_instances=4092" >> /etc/sysctl.conf
sysctl -p

The default setting of epoll=128 limits you to 128 apaches in Intrepid...

---

