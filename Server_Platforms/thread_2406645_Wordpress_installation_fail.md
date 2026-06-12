---
title: "Wordpress installation fail"
date: 2018-11-23
forum: Server Platforms
---

### Post by Lexion45 on 2018-11-23
I am trying to install wordpress on ubuntu lamp server 18.04 for a localhost test site.
When I go to my localhost ip, I get an index of/ page that shows a wordpress folder instead of the final setup stage.  

What am I doing wrong? 
I followed the directions from Digital Ocean.
 Seems easy enough, but I still managed to mess it up. ;)

Thank you

---

### Post by jeremy31 on 2018-11-23
Try localhost/wordpress?

---

### Post by Lexion45 on 2018-11-23
Yes, I get a blank white page.

---

### Post by SeijiSensei on 2018-11-23
Did you install Apache, etc, using

```
sudo apt install lamp-server^
```

You might be missing some needed modules.

Try this

```
sudo echo '<?php phpinfo()?>' > /var/www/html/info.php
```

Then point a browser to [http://localhost/info.php](http://localhost/info.php) 
You should get a whole slew of information in return.

---

### Post by Lexion45 on 2018-11-24
I installed apache2, mysql and php independently.
Php.info was displayed when I first started, but I disabled it as well as the apache2 'it works' page.
I have tried a few times so I probably corrupted the database at this point. :(

---

### Post by SeijiSensei on 2018-11-25
Any help in /var/log/apache2/error.log?

---

### Post by Lexion45 on 2018-11-25
I have not checked the error log yet.
   I was getting errors early on when I tried to restart apache, but I was able to fix that.
 Maybe I messed up when I set permissions for wordpress?
I would like to thank you seijisensei and jeremy31 for the help.:)

---

### Post by QIII on 2018-11-25
Moved to Server Platforms

---

### Post by mastablasta on 2018-11-26
for testing i found it is easier to install virtualbox and then just download a wordpress image from bitnami stack.: [https://bitnami.com/stack/wordpress/virtual-machine](https://bitnami.com/stack/wordpress/virtual-machine) 
how to import ova file: [https://www.maketecheasier.com/import-export-ova-files-in-virtualbox/](https://www.maketecheasier.com/import-export-ova-files-in-virtualbox/)

the reasons for this are:
- no install is needed, you just load the image
- if you mess it up you can easily restore the previous state in seconds (if you created a snapshot before you started messing around)
- you can easily run multiple separated servers at the same time.

there are other virtualisation options out there, but to me it seem that for new user virtualbox or a similar virtual device is easiest.

---

### Post by Lexion45 on 2018-11-26
Thanks mastablasta, that is a good point.
If I don't fix it soon, that is what I am going to try.
I did fix 'index of/' by restricting access though. (-index) 
Now I just have an empty page at localhost/wordpress. No errors.
I could just scrap it and start over but not knowing is killing me. :D

---

### Post by SeijiSensei on 2018-11-26
Again, what do you see in the error log?  My guess is a PHP error of some sort.

If you view the source of the page in your browser, is it blank?

I find all I need to do to set up another WordPress instance is create an empty MySQL database, unzip the current WP zipfile, [https://wordpress.org/latest.zip](https://wordpress.org/latest.zip), and unpack it in a directory under the web root.  Sounds like you did that, but it's not working for you.  That's why I asked if you had all the pieces for a LAMP server.

So the simplest thing would be to create another directory under /var/www/html, say "/var/www/html/newwp", unzip the Wordpress files into that location, and visit [http://localhost/newwp/](http://localhost/newwp/).

---

### Post by LHammonds on 2018-11-27
Here are the steps I do when setting up a wordpress site.  I also like to install components individually and in fact, I have dedicated servers (separate web server, database server, etc.)

[WordPress](http://hammondslegacy.com/forum/viewtopic.php?f=40&t=249)
[MariaDB](http://hammondslegacy.com/forum/viewtopic.php?f=40&t=245)

Maybe looking through these steps can help you with what you are doing.

LHammonds

---

