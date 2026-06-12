---
title: "Point of Sale"
date: 2007-12-27
forum: The Cafe
---

### Post by Vaen on 2007-12-27
Hello,

Well, i just want to give my mom a linux pc, No-dsl connection :) as she don't know how to browse, no bar code scanner "just a simple monitor with cpu and printer and simple POS program that can store store invoices etc.

I would like to know if there is a software-based POS available in ubuntu?

I already search in google, all i see is a web-based (php and mysql) POS and mostly are for windows and cost a lot.

I found several POS for linux but i can't find a software-based.

I am not a programmer, don't know much about languages and still learning about linux... and i downloaded several linux POS and i don't know how to make start.sh run :lolflag:

---

### Post by mellowd on 2007-12-27
POS as in point of sale? Like tills? I don't think it comes with one by default. There are a number of open source POS enviroments avalible on sourceforge

---

### Post by ruz322 on 2007-12-27
Try tuxshop. The interface isn't all the pretty, but it runs well. It uses a mysql database to store information about your store. I'll post a link:

[http://www.shcircuit.com/~ross/view.php/page/download](http://www.shcircuit.com/~ross/view.php/page/download)

---

### Post by mips on 2007-12-27
[http://ubuntuforums.org/showthread.php?t=471289](http://ubuntuforums.org/showthread.php?t=471289)
[http://ubuntuforums.org/showthread.php?t=161036](http://ubuntuforums.org/showthread.php?t=161036)

---

### Post by justins1983 on 2007-12-28
Is anyone familiar with setting up PHP point of sale? I'm stuck at trying to install, the directions tell me to open '/path/index.php' in a web browser. When I do this in firefox, I'm asked to choose a program to handle that file type. I followed guides to install mysql, apache and php5 as these are requirements, but I dont know what program to use or how to locate it by browsing. Anyone else done this?

---

### Post by macogw on 2007-12-28
Do you have all of the PHP plugins for Apache?

---

### Post by justins1983 on 2007-12-28
no idea. I followed the ubuntuguide.org steps for installing apache, mysql, and php since these were listed as requirements for php point of sale. I have no idea how to find or open these programs in a gui or add/check plugins.

---

### Post by popch on 2007-12-28
> **justins1983 said:**
> ...  the directions tell me to open '/path/index.php' in a web browser. When I do this in firefox, I'm asked to choose a program to handle that file type. I followed guides to install mysql, apache and php5 as these are requirements, but I dont know what program to use or how to locate it by browsing. ... 

Judging by your description, you should point your browser at 'http://localhost/parth/index.php' while you appear to have pointed it at 'file:/path/index.php'. That would explain why the browser needed to know what program to use in order to show the php file.

Unless you are doing this just in order to learn how to do this, I would suggest not to make some shop dependend for its daily operation on your skills in installing and maintaining the POS software.

---

### Post by macogw on 2007-12-28
[http://forums.xandros.com/viewtopic.php?p=206370&sid=b9c5c349a5f8f28ebc9bbcc838c287ce](http://forums.xandros.com/viewtopic.php?p=206370&sid=b9c5c349a5f8f28ebc9bbcc838c287ce)

Scroll to the 2nd-to-last post.  That should fix it.

---

### Post by justins1983 on 2007-12-28
> **popch said:**
> Judging by your description, you should point your browser at 'http://localhost/parth/index.php' while you appear to have pointed it at 'file:/path/index.php'. That would explain why the browser needed to know what program to use in order to show the php file.

Unless you are doing this just in order to learn how to do this, I would suggest not to make some shop dependend for its daily operation on your skills in installing and maintaining the POS software.

To be honest, I dont know what folder "local host" might be. I put the unpacked download of PHP point of sale in /var/lib/mysql because I thought thats what the instructions were telling me to do. Theres probably 10 different folders named mysql or apache2 but its not clear to me which one, if any, are the "localhost" folder. 

> **macogw said:**
> [http://forums.xandros.com/viewtopic.php?p=206370&sid=b9c5c349a5f8f28ebc9bbcc838c287ce](http://forums.xandros.com/viewtopic.php?p=206370&sid=b9c5c349a5f8f28ebc9bbcc838c287ce)

Scroll to the 2nd-to-last post.  That should fix it.

ok, I read that but when i went to synaptic, I already have libapache2-mod-php5 installed and without any errors. Should I still edit my httpd.conf file? its currently empty. Also, there is no modules.conf file, should I create one?

---

### Post by macogw on 2007-12-29
Localhost isn't a directory, exactly.   It's what shows up at your loopback address (127.0.0.1) when you run a webserver on a computer.  I think websites usually go in /var/www/ by default though, and then when you put [http://localhost](http://localhost) or 127.0.0.1 in Firefox it will go to whatever's in /var/www/  Right now, if you go to [http://localhost](http://localhost) (not file:///localhost), it should show Apache's default start page.

---

### Post by mellowd on 2007-12-29
Yup, localhost is your own ubuntu box. You could either use 127.0.0.1 the default and you can also use your boxes external IP. For example if your box has an IP address of 192.168.0.10 you could use either 192.168.0.1 or 127.0.0.1 (Though only on that box, if you wanted to access it from your lan you would need to use the 192 address)

---

### Post by oyvindaa on 2007-12-29
> **justins1983 said:**
> Is anyone familiar with setting up PHP point of sale? I'm stuck at trying to install, the directions tell me to open '/path/index.php' in a web browser. When I do this in firefox, I'm asked to choose a program to handle that file type. I followed guides to install mysql, apache and php5 as these are requirements, but I dont know what program to use or how to locate it by browsing. Anyone else done this?

I'm also interested in getting this to work.
I put the PHP Point of sale folder in /var/www , and typed this in my browser:

[http://localhost/PHP_Point_Of_Sale_9.1/install/index.php](http://localhost/PHP_Point_Of_Sale_9.1/install/index.php)

Then I get to a form where I put various information like database name etc..

When I click install I notice it moves to [http://localhost/PHP_Point_Of_Sale_9.1/install/makeinstall.php](http://localhost/PHP_Point_Of_Sale_9.1/install/makeinstall.php)

but after that, nothing happens. That's where I'm stuck.

---

### Post by justins1983 on 2007-12-29
> **macogw said:**
> Localhost isn't a directory, exactly.   It's what shows up at your loopback address (127.0.0.1) when you run a webserver on a computer.  I think websites usually go in /var/www/ by default though, and then when you put [http://localhost](http://localhost) or 127.0.0.1 in Firefox it will go to whatever's in /var/www/  Right now, if you go to [http://localhost](http://localhost) (not file:///localhost), it should show Apache's default start page.

Oh thanks for that, I would have never guessed what folder 'localhost' correlated to. Ive got the php file to open, just have to figure out why it gives me a blank screen after I fill out the required info and click install. Any ever used this program (PHP point of sale)??

---

### Post by justins1983 on 2007-12-29
> **oyvindaa said:**
> I'm also interested in getting this to work.
I put the PHP Point of sale folder in /var/www , and typed this in my browser:

[http://localhost/PHP_Point_Of_Sale_9.1/install/index.php](http://localhost/PHP_Point_Of_Sale_9.1/install/index.php)

Then I get to a form where I put various information like database name etc..

When I click install I notice it moves to [http://localhost/PHP_Point_Of_Sale_9.1/install/makeinstall.php](http://localhost/PHP_Point_Of_Sale_9.1/install/makeinstall.php)

but after that, nothing happens. That's where I'm stuck.

I'm having the same problem. I thought maybe it was due to not having a database in the /var/www/ folder but creating one there did not change anything. I also gave read/write permissions to settings.php to see if that was the cause, still getting the same blank page after I click install. :confused:

---

### Post by justins1983 on 2008-01-01
bump

---

### Post by justins1983 on 2008-01-06
PHP Point Of Sale 9.1
----------------------------------------------------------------
Requirements:
----------------------------------------------------------------
PHP 4.3 or greater recommended
My SQL
Any Windows, Mac, Or Unix Computer
Apache Web Server recommended

[COLOR="Red"]I used synaptic to install php, mySQL and Apache[/COLOR]

How to install:
------------------------------------------------------------------------------------------
1. Unzip the Program and place the folder onto a web-server with PHP and MYSQL.

[COLOR="Red"]I unzipped into /var/www/ on a blind guess because theres no documentation that I can find to direct me elsewhere.[/COLOR]

2. In a browser go to:  [http://Yourwebserver.com/Path](http://Yourwebserver.com/Path) To Point Of Sale/install/index.php  YOUR DEFAULT USERNAME IS : admin YOUR DEFAULT PASSWORD IS: pointofsale
3. Fill out the information and click install

[COLOR="Red"]Did this. After clicking install I get a blank page[/COLOR]

4. The tables will be created in your selected database.
5. You will be redirected to login (admin/pointofsale)
6. Add customers, brands, categories, suppliers, and items and you are ready to start selling!
*** Make sure the database you choose is already created!

[COLOR="Red"]I did this, my DB folder was saved in /var/www[/COLOR]

** Make sure you add brands, categories, and suppliers first then add items.
* Make sure the settings.php file is writable 

[COLOR="Red"]I used chmod to give write permissions to settings.php. 

So what did I do wrong here? How can I get this program to install?[/COLOR]

---

### Post by macogw on 2008-01-06
Do the installation files have execute permissions?  Maybe that's needed...  Umm...I think most files for the internet are supposed to be 755

---

### Post by justins1983 on 2008-01-06
> **macogw said:**
> Do the installation files have execute permissions?  Maybe that's needed...  Umm...I think most files for the internet are supposed to be 755

ok, changed the whole folder. now I just have to figure out how to get [http://localhost](http://localhost) to stop timing out. ugh

---

