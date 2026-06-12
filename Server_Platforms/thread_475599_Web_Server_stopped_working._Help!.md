---
title: "Web Server stopped working. Help!"
date: 2007-06-16
forum: Server Platforms
---

### Post by NumberOne on 2007-06-16
Hello,
I am running lamp server 7.04 with the gnome desktop installed.  My web server was working fine until I tried to install Citadel.  The Citadel install went fine.  I could'nt get it to work si I uninstalled Citadel.  Now my web server is not responding.  I did a re install of Apache2 to no avail.  I've checked my network settings and all is normal.

Can any one offer any suggestions as to how I can get my web server to work again.  Everything else is working (FTP server) fine.

---

### Post by hockey97 on 2007-06-16
I am having the same problem and been asking on her for like a month. 

Does it work at all?? is it like that it works only on the computer with the server?? and dosne't appear on other computers??

If it doesen't  show on the computer that has the web server, then did you try uninstalling it in the

terminal, typeing this  :   sudo apt-get remove Citadel   

This happened to me, I installed squid proxy server and cvs and then my web server went gone.

Good luck finding out what happened,  if you find out please tell me, I will do the same.

But just to inform you that I had this problem for a  month, and kept asking on here and got 

no answers or replies.

Are you using webmin??? your just plain the linux type server config types??

So Good luck.

---

### Post by NumberOne on 2007-06-16
Well, I got my web server working.  All I did was access my web site as such "http://www.yourwebsite.com:80".

When I did this my web site came up.  Then all subsequent accesses to my site did not require the :80 (port number).

HTH

---

### Post by gaten on 2007-06-17
This probably happened because Citadel uses port 80 or something. The same with squid, the default port is 80, so it conflict with Apache

---

### Post by hockey97 on 2007-06-17
HI I have webmin and tried starting my apache2 server and I get this error.

Failed to start apache : Apache does not appear to be running :

and I pressed the start button in webmin to start the server.

I have 2 versions of apache, the apache 2 and apache 1.3 .

I tried each one at a time, apache 1.3 works but I can't see it on my network like I only can access

it on the computer that is hosting it that's all,  but then I tried apache 2 and gave me that error.

and yes apache 1.3 I turned off when trying apache2 ,  I am trying to get a webserver and and working,  I want it to be seen on my network. 

Could it be a problem with bind9?? dns server, I have the defaults on that.

---

