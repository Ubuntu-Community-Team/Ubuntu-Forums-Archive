---
title: "Webmin and postfix"
date: 2011-12-16
forum: Server Platforms
---

### Post by barezi6 on 2011-12-16
Hi everyone.
I am using the ubuntu server 8.04 LTS, all things works great, and the server is on the internet, have firewall, etc etc, but i need two things that i could not do before. i have a website, and when my clients create a new account, i need that my postfix send a "activation account" for the email of this user. when i used a localhost server (xampp) my code for use the smtp server works great, all the code is right, but now i need to configure the postfix on my server, i installed the postfix, and try some ways to configure it, but cant configure it well.i saw some tutorials about it, and the most simple was [https://help.ubuntu.com/community/PostfixBasicSetupHowto](https://help.ubuntu.com/community/PostfixBasicSetupHowto), but it dont work, when i put this code "telnet localhost 25" it dont work, say something like "Connection closed by foreign host." , and i will use smtp server.
it is the first problem.

the second is that i need to install the webmin, and i installed but when i will see it on the browser it dont work, the installation would not the best and now dont work.
if anyone know a good tutorial that can help, will be good, because some of tutorials that i found dont work. or something is wrong with my config.

it is the last two things, to the complete server configuration, if someone know about this problems help me to conclude the server :)

Thanks

---

### Post by NateN34 on 2011-12-16
Webmin installation for Ubuntu is fairly simple and is the same as for Debian.

Download: [http://prdownloads.sourceforge.net/webadmin/webmin_1.570_all.deb](http://prdownloads.sourceforge.net/webadmin/webmin_1.570_all.deb)

Then install it, following these instructions (make sure you have the required packages first otherwise it won't install!):[http://www.webmin.com/deb.html](http://www.webmin.com/deb.html)

How exactly did you install yours?

---

### Post by barezi6 on 2011-12-16
> **NateN34 said:**
> Webmin installation for Ubuntu is fairly simple and is the same as for Debian.

Download: [http://prdownloads.sourceforge.net/webadmin/webmin_1.570_all.deb](http://prdownloads.sourceforge.net/webadmin/webmin_1.570_all.deb)

Then install it, following these instructions (make sure you have the required packages first otherwise it won't install!):[http://www.webmin.com/deb.html](http://www.webmin.com/deb.html)

How exactly did you install yours?

i saw some tutorials by a searched on the google, install some packages and one .sh file but nothing appen when i will try to enter on the webmin.

now i saw i new tutorial for ubuntu server 8.o4 lts, the installation works great, but when i put the site  on the browser it do not nothing

[https://forums.openitc.co.uk/index.php?topic=12.0](https://forums.openitc.co.uk/index.php?topic=12.0)

---

### Post by barezi6 on 2011-12-17
> **barezi6 said:**
> i saw some tutorials by a searched on the google, install some packages and one .sh file but nothing appen when i will try to enter on the webmin.

now i saw i new tutorial for ubuntu server 8.o4 lts, the installation works great, but when i put the site  on the browser it do not nothing

[https://forums.openitc.co.uk/index.php?topic=12.0](https://forums.openitc.co.uk/index.php?topic=12.0)

up

---

