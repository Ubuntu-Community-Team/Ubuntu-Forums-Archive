---
title: "ubuntu as web server?"
date: 2004-12-13
forum: Server Platforms
---

### Post by MatthewMetzger on 2004-12-13
Does anyone use ubuntu as a web server or as a testing (development) server? If so, could there be forum section devoted to using ubuntu as a web server?

I know that apache2 has its own documentation and forums devoted to it, but it would be good to have an addition to the ubuntu community forums. I've had a very difficult time finding the answers I need concerning virtual hosts on the default apache2 install on ubuntu.

---

### Post by wulf on 2004-12-14
I'm just starting to use it at work (webmaster for the local NHS hospital trust), replacing my previous Linux based systems (which ran into problems rebooting after an unscheduled power cycle, giving me an excuse to stick Ubuntu on, er, yesterday :D ). I found enough answers on here yesterday afternoon to convince me that the path of least resistence was installing apache2 rather than sticking with 1.3; I'm still working through establishing the rest but will have a better sense of Ubuntu as a webdev platform in the next couple of days.

Mind you, I haven't needed to learn about virtual hosts and so, alas, can't help you in that area.

Wulf

---

### Post by Alessio on 2004-12-14
[QUOTE=MatthewMetzger]Does anyone use ubuntu as a web server or as a testing (development) server? If so, could there be forum section devoted to using ubuntu as a web server?

I know that apache2 has its own documentation and forums devoted to it, but it would be good to have an addition to the ubuntu community forums. I've had a very difficult time finding the answers I need concerning virtual hosts on the default apache2 install on ubuntu.[/QUOTE]
 It's a good idea for me, Ubuntu doesn't have a php5 .deb!!

---

### Post by p!=f on 2004-12-14
[QUOTE=Alessio]It's a good idea for me, Ubuntu doesn't have a php5 .deb!![/QUOTE]
I think it's probably not considered stable enough yet. See your thread "PHP5 from sources". I'm getting to the finish. :)

---

### Post by MatthewMetzger on 2004-12-14
Hello, thanks for all your responses. I still think that having a forum dedicated to apache in ubuntu would be great, but I've decided to go back to XAMPP as it easily allows me to add virtual hosts to the bottom of the httpd.conf and it works as I expect it to. I think it would be great if XAMPP would be included in an ubuntu repository (even though it's not really necessary as XAMPP takes all of 30 seconds to install). I use apache as a test web server for my web development projects. Therefore, it doesn't have to be super secure, it just has to have the ability to work on multiple projects with each project having its own domain. XAMPP works great for this.

---

### Post by Alessio on 2004-12-14
[QUOTE=MatthewMetzger]Hello, thanks for all your responses. I still think that having a forum dedicated to apache in ubuntu would be great, but I've decided to go back to XAMPP as it easily allows me to add virtual hosts to the bottom of the httpd.conf and it works as I expect it to. I think it would be great if XAMPP would be included in an ubuntu repository (even though it's not really necessary as XAMPP takes all of 30 seconds to install). I use apache as a test web server for my web development projects. Therefore, it doesn't have to be super secure, it just has to have the ability to work on multiple projects with each project having its own domain. XAMPP works great for this.[/QUOTE]
 For local use, XAMPP it's ok :)

---

### Post by Daniel G. Taylor on 2004-12-14
I have to ask, what does Ubuntu offer for a server setup that pure Debian doesn't?

---

### Post by poofyhairguy on 2004-12-15
[QUOTE=Daniel G. Taylor]I have to ask, what does Ubuntu offer for a server setup that pure Debian doesn't?[/QUOTE]


African philosophy. Better hardware detection upon installation (for me at least). The very messy "debian menu" is put to rest. stable releases every six months. 

A cool message board to help you (I hate all the mailing lists for debian).

---

### Post by mpowell on 2005-02-02
[QUOTE=MatthewMetzger]Hello, thanks for all your responses. I still think that having a forum dedicated to apache in ubuntu would be great, but I've decided to go back to XAMPP as it easily allows me to add virtual hosts to the bottom of the httpd.conf and it works as I expect it to. I think it would be great if XAMPP would be included in an ubuntu repository (even though it's not really necessary as XAMPP takes all of 30 seconds to install). I use apache as a test web server for my web development projects. Therefore, it doesn't have to be super secure, it just has to have the ability to work on multiple projects with each project having its own domain. XAMPP works great for this.[/QUOTE]
 I am interested in using XAMPP.  I have already install apache, php and mysql.  I cannot get mysql to allow me to do anything - it keeps saying I don't have root privilieges.  Anyway will I need to uninstall these prior to installing XAMPP? and if so how do I uninstall?

Thanks 
mpowell

---

### Post by jdodson on 2005-02-02
we have a "ubuntu server talk" forum section.  all server related talk should go there.  i will pass on the idea of an apache/ubuntu section.

---

### Post by akurashy on 2005-02-02
[QUOTE=MatthewMetzger]Does anyone use ubuntu as a web server or as a testing (development) server? If so, could there be forum section devoted to using ubuntu as a web server?

I know that apache2 has its own documentation and forums devoted to it, but it would be good to have an addition to the ubuntu community forums. I've had a very difficult time finding the answers I need concerning virtual hosts on the default apache2 install on ubuntu.[/QUOTE]

I'm running a webserver in my ubuntu to do some php stuff because php in windows is crap, anyway is very efficent for me never failed for anything and apache doesnt gimme to much problems. oh and dont use xampp it never worked on me so well and is all prepared, so i prefer downloading apache, mysql, php from the repository and setting it up myself if you need any help just go to [http://ubuntuguide.org](http://ubuntuguide.org)

---

### Post by mpowell on 2005-02-02
[QUOTE=akurashy]I'm running a webserver in my ubuntu to do some php stuff because php in windows is crap, anyway is very efficent for me never failed for anything and apache doesnt gimme to much problems. oh and dont use xampp it never worked on me so well and is all prepared, so i prefer downloading apache, mysql, php from the repository and setting it up myself if you need any help just go to [http://ubuntuguide.org](http://ubuntuguide.org)[/QUOTE]
 I really am not sure I want to use xampp either.  However when i try to do anything in mysql I get the following error message:

'Access denied for user: '@localhost' to database 'mysql''

I can't change my password, create database, or anything.

mpowell

---

### Post by az on 2005-02-02
"I cannot get mysql to allow me to do anything - it keeps saying I don't have root privilieges"

Read the manual (/usr/share/doc/mysql-server)

mysqladmin -u root password 'make-up-your-password-here'

---

### Post by mpowell on 2005-02-02
[QUOTE=azz]"I cannot get mysql to allow me to do anything - it keeps saying I don't have root privilieges"

Read the manual (/usr/share/doc/mysql-server)

mysqladmin -u root password 'make-up-your-password-here'[/QUOTE]
 Yes, of course I have tried this and this is what I get:

mark@laptop:~ $ sudo mysqladmin -u root password 'my_password'
mysqladmin: unable to change password; error: 'Access denied for user: '@localhost' to database 'mysql''

---

### Post by az on 2005-02-02
Are you sure that mysql-server is installed?

---

### Post by akurashy on 2005-02-02
hmm thats weird
i didnt did use mysqladmin -u root password 'make-up-your-password-here' 
but it still worked for me :)

---

### Post by mpowell on 2005-02-02
[QUOTE=azz]Are you sure that mysql-server is installed?[/QUOTE]
 Yes, I installed it by apt-get install following the directions of the unofficial guide.  But when I try to create a password I get the above message.  Could it be file or directory permissions?

mpowell

---

### Post by mpowell on 2005-02-02
[QUOTE=akurashy]hmm thats weird
i didnt did use mysqladmin -u root password 'make-up-your-password-here' 
but it still worked for me :)[/QUOTE]
 So what did you do?  

Also what will happen if I run xampp with apache, php and mysql already installed?

mpowell

---

### Post by nocturn on 2005-02-03
[QUOTE=Daniel G. Taylor]I have to ask, what does Ubuntu offer for a server setup that pure Debian doesn't?[/QUOTE]

Well, unless you are willing to stick with apache1, MySQL 3 (which lacks some SQL features) etc, Debian will do ;-)

Seriously, a 'stable' tree for a server is cool, but the time they take to release is just plain crazy.

---

### Post by akurashy on 2005-02-03
[QUOTE=mpowell]So what did you do?  

Also what will happen if I run xampp with apache, php and mysql already installed?

mpowell[/QUOTE]

i dont know i never ran it, i gave me some weird errors so i got tired and installed my wbeserver manually

---

### Post by ensenadaubuntulover on 2005-05-30
[QUOTE=mpowell]So what did you do?  

Also what will happen if I run xampp with apache, php and mysql already installed?

mpowell[/QUOTE]

It will stop everything first and thrn start XAMPP ' s programs that are in /opt

---

### Post by ensenadaubuntulover on 2005-05-30
[QUOTE=mpowell]So what did you do?  

Also what will happen if I run xampp with apache, php and mysql already installed?

mpowell[/QUOTE]

It seems to me we are in the same boat difficukty with passwords, mysqladmin, no root in ubuntu so I am triing xammp (to learn something at least) and not spending time in configurations.

I have apache ind found out I have to stop it so xammps apache start

( /etc/init.d/apache2  stop)

then 

/opt/lammp/lammp start

so is like having two of everything!!!


I want to learn php and mysql and found some tutorials but since ubuntu is different (better for me at least) I get lost a lot.

so for meanwhile use xammp for learning and then MAYBE later I can manage to make a decent server.

by the way xammp has a lot of manuals and examples and makes life a little bit easier.

so you can have the serious stuff installed but when you figure out the password stuff drop me a line!

---

### Post by lozzd on 2005-06-01
I've just moved from a seriously underpowered Windows XP box with Apache to my dual Xeon Ubuntu Linux box with Apache and its fantastic. So much better overall. 
If you're interested, its running [http://www.denness.net](http://www.denness.net).

---

