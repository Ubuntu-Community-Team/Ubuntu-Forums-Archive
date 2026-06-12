---
title: "A tale of woe: LAMP installed, working, but not working?"
date: 2009-01-25
forum: Server Platforms
---

### Post by NightFalcon90909 on 2009-01-25
Greetings! 

I'm on Ubuntu 8.10, which is running virtually within Virtual Box on Mac OS X 10.5.

I'm primarily on Linux because I am making a PHP webapplication for my science fair project this year.

I recently decided to try out KDE. So I did. It was cool and pretty, but the novelty soon wore off, and so I uninstalled it. Or at least, I tried to. I realized installing KDE with synaptic hadn't been such a great idea, since I therefore needed to manually remove each package. So I removed a truckload of programs and "libs" and stuff. Well as I watching all that happen in the terminal, I was horrified to see the output cheerily inform me that it was unistalling Apache, my meticulously fine tuned MySQL database, php and phpmyadmin. 

grrr...

Well no matter, I had installed it before, following these directions:

[http://www.downloadsquad.com/2008/06/13/flipping-the-linux-switch-linux-web-tools-pt-2-using-lamp-f/](http://www.downloadsquad.com/2008/06/13/flipping-the-linux-switch-linux-web-tools-pt-2-using-lamp-f/)

So I figured I'd just install it again. 

I fired up Synaptic, and followed the directions again, to the letter. I was a bit surprised, since the mysql prompt never came up this time, asking for my root password, since last time it had. I tried doing the command line command that was suggested in that tutorial:
```

mysql> SET PASSWORD FOR 'root'@'localhost'=PASSWORD('somepassword');
```

No luck:

```
ERROR 1044 (42000): Access denied for user ''@'localhost' to database 'mysql'

```

Well strange, but I decided to carry on. I went to [http://localhost/](http://localhost/)

Hooray, "It works!" [Screenshot]("https://dl.getdropbox.com/u/452629/It%20works.png")





It worked!

Very good, so I installed phpmyadmin, per instructions.

I visited [http://localhost/phpmyadmin](http://localhost/phpmyadmin)




No beans:

[IMG]https://dl.getdropbox.com/u/452629/It%20doesn%27t%20work.png[/IMG]




So there is my problem... thanks in advance for any help you may be able to give me, because I need it!

---

### Post by Dileeshvar on 2009-03-29
I too face the same problem some one help !!

---

### Post by hyper_ch on 2009-03-29
(1) on a server I would not install a gui

(2) for setting up a webserver I'd follow the perfect howtos by falko over at [http://www.howtoforge.com](http://www.howtoforge.com)

---

### Post by kamaji792 on 2009-03-29
Er...

The problem is not that you need to use:

[http://localhost/phpMyAdmin](http://localhost/phpMyAdmin)

(Note the capitalisation)

atb

---

### Post by koenn on 2009-03-29
the php part of the LAMP doesn't sem to be working correctly.

check that it's installed:
```
dpkg --get-selections |grep php
```

---

### Post by hyper_ch on 2009-03-29
```

sudo a2enmod php5

```

---

### Post by Grey08 on 2009-03-30
I remember that you need to tell the Apache2 to use php, which there is a line to add at apache config file, but i can't remember what is it. Maybe u can try find it out "how to tell apache2 u want to use php". :)

---

### Post by hyper_ch on 2009-03-30
grey: see the post above yours.

---

### Post by BkkBonanza on 2009-03-30
You need the line 

AddType application/x-httpd-php .php

in your httpd.conf file so that apache knows that php files need to be interpreted rather than sent to the user. The message you got is the browser wondering what you want to do with the php file - but it should never have got it in the first place.

BTW your mysql install probably worked fine because when you removed mysql it didn't delete your data files. So when you put it back they were still there. Which means the user and privelages tables were intact.

---

### Post by headdead on 2009-03-31
Greetings. (My first post)
Thank you hyper_ch for much valuable info in many other threads.

I also had this issue.  I followed all the advice above.  No fix.
However, I noticed in /var/www

doku.php
index.php
index.html.bak
Firefox 3.0.8 asked "What should FF do with this file? OPEN or SAVE?

I "sudo mv index.html.bak index.html"    so /var/www had:
doku.php
index.php
index.html
Cleared the cache: Firefox opened the html file properly.

I then "sudo mv index.html XXXindex.html"   so /var/www had:
doku.php
index.php
XXXindex.html
Cleared the cache: Firefox fired up my Dokuwiki perfectly.  Yeeeeeeeee Hahhhhhhh.

I guess my apache2.conf file does not know how to deal with a "*.bak" file.

I believe this issue can be fixed more elegantly by adding a DirectoryIndex entry to my /etc/apache2/apache2.conf file.  Untll then, don't have more than 1 file called "index.*"

BTW, sorry I haven't yet figured out how to copy/paste into Code: boxes.

---

### Post by hyper_ch on 2009-04-01
> **BkkBonaza said:**
> You need the line 

AddType application/x-httpd-php .php

in your httpd.conf file so that apache knows that php files need to be interpreted rather than sent to the user.

See this post:  [http://ubuntuforums.org/showpost.php?p=6978504&postcount=6](http://ubuntuforums.org/showpost.php?p=6978504&postcount=6) -> that's how you should use apache2

---

### Post by Grey08 on 2009-04-02
try add this line 

> Include /etc/phpmyadmin/apache.conf

to your /etc/apache2/apache2.conf

Then restart the...php and apache? ( i reboot machine when i set it)

This is to tell the apache use php and display it instead of download the php file.

Hope this helps :)

---

### Post by cariboo on 2009-04-02
If you set up LAMP and phpmyadmin from the repositories, they get configured on install no need to do anything else. The last time I installed it , about 6 months ago, I don't think I even had to restart apache2, it was all done automagically.

Jim

---

