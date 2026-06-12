---
title: "Didn't install LAMP?"
date: 2007-07-13
forum: Server Platforms
---

### Post by Cirdan7 on 2007-07-13
Ok, NVM. I figured it out.

I installed Feisty 7.0.4 Server edition and told it to install the LAMP. When I finished the installation, I opened the browser to the computer's ip and it didn't load a default web page. I can ping the computer. i ran 'ps -A' and saw no apache, mysql, and no php. So I presume I need to start it some how?

According to ( [http://ubuntuguide.org/wiki/Ubuntu:Feisty#Servers](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Servers) ) there was nothing more to do after I installed it. I tried to run sudo aptitude install lamp-server but it said it couldn't find anything like that.

---

### Post by xjdriver69 on 2007-07-30
Cirdan7,
  Typically on a 7.04 server it will ask you whether you want a DNS or a LAMP server, you have to select the one you want by pressing the spacebar.  if you dont want to reinstall 7.04 server then you will have to install the apache2 Mysql and PHP by themselves or there maybe a way that i am not familiar with. if you need to start them then here are the some commands.

apache2: sudo /etc/init.d/apache2 start

mysql: sudo /etc/init.d/mysql start

---

### Post by JohnBee on 2007-08-26
There is something wrong with the latest versions of Ubuntu sever. I tried both x64 and x86 versions and chose LAMP installation on both and they both did not install LAMP after installation was completed. 

Pretty nasty bugs to say the least.

---

### Post by insane_alien on 2007-08-26
LAMP installed fine for me, did it have the asterisk next to it before you hit next or did you just hit enter which wouldn't have selected it?

and are you sure the error page isn't just because you have nothing in /var/www/

---

