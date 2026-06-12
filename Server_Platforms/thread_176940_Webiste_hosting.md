---
title: "Webiste hosting"
date: 2006-05-15
forum: Server Platforms
---

### Post by Socratez on 2006-05-15
I am using ISPconfig on my Ubuntu install and when connecting to the server I get a "Shared Ip" message. Like what the hell is the deal with multiple host on a single machine ? Maybe I am thick but how come I can't host 3 4 5 or even more websites on one server? could it be an apache 1.3 or apache2 thing? should I use only one of them? I think ISPconfig installed 1.3 and i had 2 on the machine already ... 

Can I get a hand with this? I am truely lost and I don't want to start all over? What info do I need to post to have some helping hands?

Soc

---

### Post by Socratez on 2006-05-15
I have gotten rid of the error but I am still at a loss for creating multiple webs? what am I doing worng? Do I need to assigne aliases to my network interfaces? or something like that? How can I have it not point to a defualt directory? and how can I creat things to be simple ... my main web right now is the apache2-defualt but in the /var/www there is an apache2-default ,  sharedip , twiki , webalizer directories. How can I make my Twiki a simple hostname/twiki url ??

Soc

---

### Post by cvmiller on 2006-05-16
[QUOTE=Socratez]How can I make my Twiki a simple hostname/twiki url ??
Soc[/QUOTE]

You may want to look at the apache doc for virtual hosting, as there are different types of vhosting.
[http://httpd.apache.org/docs/2.0/vhosts/](http://httpd.apache.org/docs/2.0/vhosts/)

Or if all you want is a simple hostname/twiki, but a symbolic link at your DocRoot pointing to whereever you have twiki installed (make sure you have FollowSymLink turned on).

I hope this helps,

Craig...

---

### Post by brodock on 2006-05-16
how to make use of "sites-available" and "sites-enabled" ?

---

### Post by peanut butter on 2006-05-17
neither VHCS nor ipconfig work properly on ubuntu. oyu might just do it using the link above.

---

### Post by brodock on 2006-05-17
i got virtual hosts to work... using the principle of "sites-available" and "sites-enabled"...

the idea is to create a file at sites-availables with virtualhosts configuration inside and then symbolic link it at sites-enabled following the name convention already used there.

then restart apache and everything works

(using apache2)

---

### Post by Zelut on 2006-08-15
I have used VHCS and ISPConfig for some time and want to tell everyone to stay away from VHCS.  There has been a **gaping** security flaw since Feb 06 that has been untouched.  I have been hacked a half-dozen times and the developers do nothing about it.

I'm looking for a new system, but DO NOT use [VHCS v2.4.7.1 Pro]("http://christer.homeip.net/index.php/vhcs-v2471-pro/")(link to my writeup), or any other version.

---

