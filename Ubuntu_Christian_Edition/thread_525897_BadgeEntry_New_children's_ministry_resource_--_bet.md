---
title: "BadgeEntry: New children's ministry resource -- beta testers wanted"
date: 2007-08-14
forum: Ubuntu Christian Edition
---

### Post by mssever on 2007-08-14
The churches in my area recently held a camp meeting, and my brother was in charge of one of the kids' groups. He asked me to design an attendance system that involved badges with the kids' photos and a barcode on them. They would scan those badges to gain entry into the "top secret lab" and us staff would have an automatic, accurate attendance system. (From comments I heard after the event, this system also helped give our program an additional "quality polish" as the badges turned out well.)

The system that emerged is called BadgeEntry. After successfully using it for our event, I've decided to release it to the public.

With school starting soon, it's a little late for VBS use, but I'm still looking for people to test it and provide feedback. While any comments, bug reports, and criticisms are welcome, I'm especially interested in feedback about the install process, documentation, and user interface.

Also, BadgeEntry should run on Windows and MacOS, in addition to Linux. However, since I've switched completely to Linux, I haven't been able to test those other platforms. (I wrote the Windows documentation from memory as I wasn't able to test it, so I hope it's accurate.) I realize that this is a Linux forum, but perhaps someone still uses one of those other OSes and can test BadgeEntry on it.

You can find out more on the [BadgeEntry website]("http://badgeentry.sourceforge.net/"), which is also the place to go to download BadgeEntry.

---

### Post by jbob23 on 2008-08-18
Hey! 
I know you posted this a long time ago but...
I was searching the web for an Open Source ID badge system and stumbled upon yours, 
first off - this looks promising and i would love to help you test it further, that is if i could get a little further in the process.
Granted though, that i have not installed it on a Linux box yet, but through windows xp, installation went through without any trouble through xampplite (cept for the actual database creation would not let me use badgeentry as a database name... but that could have very well been because i did something goofy) once i renamed the database it started up just great.  Started to configure the database and got as far as the badge template page, i wanted to use the defaults so i clicked on continue and came up with a 404 and could not get past it for anything, would love to help you get this project further cause frankly i think this would be a really cool idea to implement into a VBS as for other things too, (plus i am excited to have found a Christian Ubuntu forum! :)
-Jake

---

### Post by mssever on 2008-08-18
> **jbob23 said:**
> Granted though, that i have not installed it on a Linux box yet, but through windows xp, installation went through without any trouble through xampplite (cept for the actual database creation would not let me use badgeentry as a database name... but that could have very well been because i did something goofy) once i renamed the database it started up just great.  Started to configure the database and got as far as the badge template page, i wanted to use the defaults so i clicked on continue and came up with a 404 and could not get past it for anything, would love to help you get this project further cause frankly i think this would be a really cool idea to implement into a VBS as for other things too, (plus i am excited to have found a Christian Ubuntu forum! :)
-Jake
You didn't mention any version numbers. Which version of BadgeEntry are you using? Which version of PHP? MySQL? Apache? Which URL produces the 404?

BadgeEntry does NOT work with PHP 4. Perhaps that's the problem. I've heard of this problem before, and I don't remember whether that was the solution. I do know that BadgeEntry 0.7 fixes some bugs that I discovered around the same time, and that the person who was having that program eventually installed BadgeEntry on Linux. But I don't know that the OS was the problem.

---

### Post by jbob23 on 2008-08-19
I am using the newest:
BadgeEntry 0.7
XAMPP lite version 1.6.7 which includes:
Apache 2.2.9
PHP 5.2.6
MySQL 5.0.51b 
and...
phpMyAdmin 2.11.7
OpenSSL 0.9.8h
SQLite 2.8.15

the 404 comes right after clicking the continue button on the default template for the badges page: 
/index.php/configuration/badges/intro
you are directed to:
/configuration/badges/confirm
which in turn is giving me the 404 Object not found page

just a little bit more info; the server side of this is running in VMware: Windows XP SP3
Client side (the actual host computer of the VMware) is the one accessing the pages through FireFox, and is also Windows XP SP3

---

### Post by mssever on 2008-08-19
It appears that your .htaccess file either doesn't exist or isn't being read. Try going to /index.php/configuration/badges/confirm. If that works, then my suspicion is correct. Otherwise, the problem is something else.

Make sure that the file .htaccess got properly copied. It might be hidden by default.

---

### Post by jbob23 on 2008-08-20
> **mssever said:**
> Try going to /index.php/configuration/badges/confirm.

I had tried that before, but went ahead and tried it again, 
it gives me the exact same page as 
/index.php/configuration/badges/intro

i completely deleted xampp and badgeentry, reinstalled both, and even removed everything from htdocs in xampp before copying badgeentry over.

followed the instructions from [http://badgeentry.sourceforge.net/install.html](http://badgeentry.sourceforge.net/install.html)

i did get another error that i had gotten before, first time i load it up after renaming database-template.php to database.php and adding BadgeEntry from cmd with mysqladmin:
going to the ip address for the first time i get an error saying that database badgeentry already exists so i go back into database.php and rename the default to testbadge and add it into mysql also... go to the ip address and i get a confirmation that the database has been created and then it starts me off in the setup of the database...
get all the way to /index.php/configuration/badges/intro
click on continue and the same thing again...
/configuration/badges/confirm - 404 error
using 
/index.php/configuration/badges/confirm takes me right back to the same page as 
/index.php/configuration/badges/intro but is labeled confirm instead of intro
click on continue again and it produces the exact same error

i checked to see if the .htaccess was there, and i am guessing that you were meaning the one that is accompanying index.php on the root, and it is, and i even extracted a new copy just to be sure, yet i also notice other .htaccess files throughout the folders

i know this sounds kind of stupid :-) but my degree and expertise is in hardware; software is more a hobby... yet i have not tread into php's or mysql's territory nearly at all...
Thanks for Helping!

---

### Post by mssever on 2008-08-22
Hmm... I really don't know what's happening. Could you try it without using XAMPP and see if that works? For example, in Ubuntu, type ```
sudo tasksel
```and choose LAMP server.

The thing is, I don't know what the problem is, and I've never used XAMPP, personally.

---

### Post by netgifted on 2008-10-16
Well I have also a problem. I have XAMPP on a MAC OSX machine. I can run any web application but I cannot figure out how to configure the .htaccess file on bdgeentry. I keep having an error 500 "Internal Server Error". I am no php guru so I would really appreciate some help with this. Thanks

---

### Post by mssever on 2008-10-16
> **netgifted said:**
> Well I have also a problem. I have XAMPP on a MAC OSX machine. I can run any web application but I cannot figure out how to configure the .htaccess file on bdgeentry. I keep having an error 500 "Internal Server Error". I am no php guru so I would really appreciate some help with this. Thanks
This discussion continues on the [BadgeEntry forum]("https://sourceforge.net/forum/forum.php?thread_id=2381632&forum_id=722408").

EDIT: The discussion I'm referring to is the particular discussion with netgifted, not the whole thread.

---

### Post by Sef on 2008-10-16
Reopened per OP request

---

