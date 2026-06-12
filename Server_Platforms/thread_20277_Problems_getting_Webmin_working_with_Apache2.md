---
title: "Problems getting Webmin working with Apache2"
date: 2005-03-15
forum: Server Platforms
---

### Post by obelix on 2005-03-15
I just finished installing webmin as per:
[http://ubuntuforums.org/archive/index.php/t-7507.html](http://ubuntuforums.org/archive/index.php/t-7507.html)

And I'm having troubles getting it to stop/start the Apache server. I installed Apache through apt-get and I configured it for ssl. Setting up webmin was a breeze but I just can't figure this out. I hit "Start Apache" and it works for a second and then prints out this message:

Failed to start apache : Apache does not appear to be running :

Yet when I do a ps aux|grep apache2 it shows the server running. If I kill the process and hit start again... sure enough apache2 is there again. So why is webmin not displaying it as running? See my attached screenshot for details.

---

### Post by obelix on 2005-03-16
Nevermind I got it. It's not httpd.conf its apache2.conf under ubuntu. All works now :D

---

### Post by fduplex on 2005-04-24
I'm curious, did you manage to get webmin to start/stop apache properly? i'm having the same problem

---

### Post by Beernut on 2005-04-24
[QUOTE=fduplex]I'm curious, did you manage to get webmin to start/stop apache properly? i'm having the same problem[/QUOTE]

You have togo to webmin click on servers then apache webserver.  In the upper left hand corner you will see a link for module config.  When you click that you need to make some changes you need to replace apache with apache2 and as said above httpd.conf to apache2.conf.  Click the screenshot below to see all the "System Configurations Setting"  this should work if you installed apache using synaptic or apt-get.

HTH

---

### Post by christel on 2005-08-06
Thanks a lot!!!
I'm a newbie, and i've tried to configure apache under webmin many times. After your nice screenshot it works!!!
 :)

---

### Post by mrweirdo on 2005-08-09
thanks great info infact tut worthy ;)

---

### Post by Nazulatatunkce on 2006-02-02
A great thanks to all, I was doing the same thing Obelix was doing.  Bob

---

### Post by EwwBunToo on 2006-02-06
A great help.... Thanks\\:D/

---

### Post by lionsnob on 2006-08-04
Hello,

I'm also getting the above error, yet when I put /usr/sbin/apache2 instead of /usr/sbin/apache2ctl I can't even get that far.  Any advice?

Thanks!

---

### Post by lionsnob on 2006-08-04
Never mind, silly mistake on my part.  I have apache working now, but I can't get an http:// connection to work, only https://

Can I get them both to work?

Thanks!

---

### Post by Jayzilla on 2006-09-03
Weird, I have no apache2.conf in my /etc/apache2 directory.  I do, however, have an httpd.conf...which is blank.  What the heck?

---

### Post by copycat on 2007-03-06
when I install dapper LAMP with webmin everything works fine.  I did some tests with oscommerce and joomla and after a while the apache server stops working.  It is started but I can not connect to the tefault page.

---

### Post by bunintheoventoo on 2007-03-06
Thanks, screenshot got it working after 6 hours of removing and trashing all config files, full re-install and re config to no avail, was apache2.conf all along.

---

