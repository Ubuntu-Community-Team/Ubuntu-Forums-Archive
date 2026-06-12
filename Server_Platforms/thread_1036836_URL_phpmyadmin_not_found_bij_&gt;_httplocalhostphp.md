---
title: "URL phpmyadmin not found bij &gt; http://localhost/phpmyadmin"
date: 2009-01-11
forum: Server Platforms
---

### Post by jazzguitarplayer on 2009-01-11
Hello,

A few days ago I installed LAMP for the first time with wordpress. Almost everything I succeeded (after putting alot of effort). My problem is that i can't manage the phpmyadmin panel. My Linux distro is Ubuntu 8.04. I reinstalled the phpmyadmin package but it didn't resolve the problem.

To manage phpmyadmin I could use the next URL: [http://localhost/phpmyadmin](http://localhost/phpmyadmin)  of [http://lan ip address/phpmyadmin](http://lan ip address/phpmyadmin)
The problem is that when enter urls above i got an error message as could be seen below.
I'm stuck for a few days. Help is appreciated!


Not Found

The requested URL /phpmyadmin was not found on this server.
Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.4 with Suhosin-Patch Server at localhost Port 80

---

### Post by bluefrog on 2009-01-11
what is your problem?

---

### Post by jazzguitarplayer on 2009-01-11
thanks all, i already found the problem.

---

### Post by Hasledash on 2009-01-30
Hi, I am very new to Ubuntu and even linux for that matter. I am having the exact same problem you had. Can you please share how you resolved the issue. 
 
   May help to know that I'm trying to use PhpMyAdmin from another computer through the Firefox via [http://serverip/phpmyadmin](http://serverip/phpmyadmin).

---

### Post by entetaylor on 2009-04-01
Add the line

Include /etc/phpmyadmin/apache.conf

in /etc/apache2/apache2.conf. 
This worked for me

(see also [https://help.ubuntu.com/community/phpMyAdmin]("https://help.ubuntu.com/community/phpMyAdmin"))

---

### Post by mattalexx on 2009-07-17
> **jazzguitarplayer said:**
> thanks all, i already found the problem.

This response is not community-friendly. If you find the solution to your problem, take the time to post it (or a link to it) so that people who read this post with the same problem can find it.

---

### Post by TitanKing on 2009-08-06
Your browser cant find phpmyadmin do : 

```
sudo ln -s /usr/share/phpmyadmin /var/www
```

Cheers...

---

### Post by hezuo on 2009-11-02
> **entetaylor said:**
> Add the line

Include /etc/phpmyadmin/apache.conf

in /etc/apache2/apache2.conf. 
This worked for me

(see also [https://help.ubuntu.com/community/phpMyAdmin]("https://help.ubuntu.com/community/phpMyAdmin"))

this worked for me. Thanks!

---

### Post by dsapoki on 2009-11-18
Hey, I was strugling as well and finally, simple
apt-get install phpmyadmin 
did the magic...
This was not included in LAMP install!!!

---

### Post by quimkaos on 2009-11-24
> **TitanKing said:**
> Your browser cant find phpmyadmin do : 

```
sudo ln -s /usr/share/phpmyadmin /var/www
```Cheers...

i take that this is valid if your web root folder is /var/www

because, since /var/www is not writable i've changed it to one folder inside my personal folder...
am I right?

---

### Post by titiiliescu on 2009-12-08
Thanks, entetaylor!
This worked perfectly!

---

### Post by RockOut on 2010-02-16
> **TitanKing said:**
> Your browser cant find phpmyadmin do : 

```
sudo ln -s /usr/share/phpmyadmin /var/www
```Cheers...


This solution worked for me! 

I'm on Ubuntu 9.10 with a fresh installation as of 02/01/2010, and had the same problem as the OP.

Thanks!

---

### Post by BillyMac856 on 2010-03-22
Thank-Youuuuu!
I myself was pulling my hair out with this one as well, and I am truly grateful for this forum and the support that you guys give freely to us new users of Ubuntu. 

I really love the fact that there is a place to go and get just about any problems and/or questions answered, (quickly & specific to Ubuntu) it's just awesome!
A Big Thank-You To You Guys  :D

> **TitanKing said:**
> Your browser cant find phpmyadmin do : 

```
sudo ln -s /usr/share/phpmyadmin /var/www
```Cheers...

---

### Post by theblackfu on 2010-12-27
Thanks, the Include worked for me

---

### Post by rakeshjames on 2011-02-08
[https://help.ubuntu.com/community/phpMyAdmin](https://help.ubuntu.com/community/phpMyAdmin)

please read the  doc , and do it in step by step
..):P):P

---

### Post by fovoc on 2013-01-09
> **entetaylor said:**
> Add the line

Include /etc/phpmyadmin/apache.conf

in /etc/apache2/apache2.conf. 
This worked for me

(see also [https://help.ubuntu.com/community/phpMyAdmin]("https://help.ubuntu.com/community/phpMyAdmin"))

worked like a charm!

---

### Post by CharlesA on 2013-01-09
Back to sleep you go...

---

