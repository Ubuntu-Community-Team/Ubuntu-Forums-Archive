---
title: "[SOLVED] php5 not working... massive server troubles"
date: 2008-08-25
forum: Server Platforms
---

### Post by deepak1uw on 2008-08-25
Hi people!,

I installed PHP5, apache2 and MySQL for a testing server.

using this reference ```
http://sidrit.wordpress.com/2008/08/03/lamp-linux-apache-mysql-php-server-on-ubuntu-804/
```

This is what I have installed:
[B]PhpMyAdmin 
MySql-Server-5.0
Apache2.2-common
PHP-5.0
& all dependencies.[/B]

Now When I went into [**http://localhost/**](**http://localhost/**) then I get the message: **"IT WORKS!"** in browser...which is fine i guess??
However, after that i tried to locate **phpMyadmin** folder inside **/var/www**.... guess what..it's not there and i never able to locate it either.
then i created one file named** phpinfo.php** in **/var/www/** using this php code : **<?php echo php_info()  ?>** inside it.  

then i restarted apache & mysql manually.

now when i try opening a php file (**http:/localhost/phpinfo.php**) it asks me to download that same php file instead of running it like a normal server.

then i referred this post 

```
http://ubuntuforums.org/showthread.php?t=227033
```

but still when I try opening a php file (**http:/localhost/testphp.php**) it simply showing me web page containing that same code -- **<?php echo php_info()  ?>**.

So Finally the list which i can sum up is
[B]PhpMyAdmin ------------- [COLOR="Blue"]Don't know where to find it in my computer.[/COLOR]
MySql-Server-5.0 ------- [COLOR="Blue"]i don't know it's working fine or not.[/COLOR]
Apache2.2-common ------- [COLOR="Green"]this one only working fine.[/COLOR]
PHP-5.0 ---------------- [COLOR="Red"]obviously not working at all.[/COLOR][/B]


How do I get php pages to work...please help??

---

### Post by gtdaqua on 2008-08-25
Did you encounter any installation errors? Did you install by apt-get or compiled from source?

May be a borken installation. Try a fix:

```

sudo apt-get install -f

```

---

### Post by deepak1uw on 2008-08-25
No I didn't encounter any installation problems/errors.

---

### Post by mbeach on 2008-08-25
according to:
[http://ubuntuforums.org/showthread.php?p=5613998](http://ubuntuforums.org/showthread.php?p=5613998)
you can likely find phpmyadmin at:
/usr/share/phpmyadmin
there is probably some pointer to it in either /etc/apache2/apache2.conf or in /etc/apache2/sites-available
I also far prefer mysql's tools ([http://www.mysql.com/products/tools/](http://www.mysql.com/products/tools/)) instead of phpmyadmin, but that's a matter of personal preference.

if you change the ownership of the php file, you'll probably get what you are after:
```
sudo chown www-data:www-data /var/www/phpinfo.php
```

but I don't think you need the 'echo'.
you just need:
[PHP]<?php
// Show all information, defaults to INFO_ALL
phpinfo();
?php>[/PHP]

---

### Post by ingeva on 2008-08-27
> **deepak1uw said:**
> I installed PHP5, apache2 and MySQL for a testing server.

With all the competent people around here I'm surprised that no one understands the problem.

I have exactly the same one.

I've followed the books and tried all tips (some made for older versions of Linux, Ubuntu or Apache).

Apache was redesigned a version or two ago. Could this have anything to do with it?

What's in the php file has nothing to do with the problem. The fact is that Apache doesn't recognize it as a php file, and knows nothing about php -- so it delivers it to the browser in a way that makes it ask if you want to download it -- or execute a program for it.
The program, php, must be executed on the server side, not on the client side. It does not matter if the two are on the same computer. Even if you ask it to execute php, it wouldn help one bit. The best that could happen was that you'd get the html output as pure text.

A lot of my time goes to developing and maintaining websites. I've worked with Ubuntu for about a month, and much of the time has gone to make Apache work.
The trouble I've been through has made me wonder if it wouldn't be better to return to Windows -- but the webserver I used in Windows is obsolete, and I couldn't mae Apache work in Windows either. So I would just be back with the same trouble.

I think Apache should be redesigned again. AND present some more understandable documentation.

But that takes time. While we're waiting, could comeone tell use the well hidden secret?

Please?

---

### Post by windependence on 2008-08-27
We perfectly understand the problem, but apparently we aren't getting all the information we need to fix it.

First off I need to know if you installed both Apache and php from packages or did you compile any one of them from source?

-Tim

---

### Post by ingeva on 2008-08-27
> **windependence said:**
> We perfectly understand the problem, but apparently we aren't getting all the information we need to fix it.

First off I need to know if you installed both Apache and php from packages or did you compile any one of them from source?

-Tim

Well I for one have already posted this information in another thread in this forum,
but here it is again:

I installed apache like this:

```
#! /bin/bash
# Needs to be called with "sudo bash installs"

#php5 and apache2
apt-get install php5 php-pear libapache2-mod-php5 php5-common
apt-get install apache2 apache2.2-common apache2-mpm-prefork apache2-utils apache2-doc

```

I've set up links to my own configuration files thus:
```
#! /bin/bash
# Called with "sudo bash setapache"
cd /etc/apache2
ln -sf /home/inge/settings/httpd.conf httpd.conf
cd sites-enabled
rm *
ln -sf /home/inge/settings/test test
# (And so on for each VH)

```

I found something to put into the httpd.conf file:

AddType application/x-httpd-php .php

but that was from a very old help file and didn't make any difference.

I haven't found ONE WORD about php in the Apache documentation, which is very accurate but very hard to read. There are many details but very little context.

My next step would be to install Ubuntu server on another computer and see how things were set up (and if it would work! ). That will be my final configuration anyway. The other computer is just not ready yet.

---

### Post by ingeva on 2008-08-27
LAST:

I found something at [http://dan.drydog.com/apache2php.html](http://dan.drydog.com/apache2php.html) .
I copied this code into my httpd.conf file:

```
# Use for PHP 5.x:
LoadModule php5_module        modules/libphp5.so
AddHandler php5-script php 

# Add index.php to your DirectoryIndex line:
DirectoryIndex index.html index.php

AddType text/html       php

# PHP Syntax Coloring
# (optional but useful for reading PHP source for debugging):
AddType application/x-httpd-php-source phps

```

and before that I defined a link to the libphp5.so module (or rather, to the directory it's in):

sudo ln -s /usr/lib/apache2/modules modules

After doing this, Apache understands php, but I've also discovered that it (no longer?) uses the correct virtual host.

One of my VHs is "intertrafico". This is also the first Virtual Host in the sequence. The same thing happens to the other VHs. Apache goes to "intertrafico.com " for every one of them.
I also had a lot of trouble setting up my VHs. The documentation is not clear and takes things out of context. However, I'll keep working on that and take possible questions about it in another thread.

---

### Post by windependence on 2008-08-27
Don't use httpd.conf in Apache2. It's deprecated. That may be where most of your trouble is. I can tell you if you have your vhosts in there, then that is most likey the problem with them.

Why all the 

```
#! /bin/bash
# Needs to be called with "sudo bash installs"
```

comments in the install commands? Did you install this with a script? I'm confused.

I think a simple

```
sudo apt-get install apache2 
```

would have done it, but I don't run any of my hosts on Linux. They're all *BSD. Much simpler, more stable <flame suit on> ;)

-Tim

---

### Post by ingeva on 2008-08-27
> **windependence said:**
> Don't use httpd.conf in Apache2. It's deprecated. That may be where most of your trouble is. I can tell you if you have your vhosts in there, then that is most likey the problem with them.

I don't think it's deprecated. Why would it then be called from apache2.conf?
The only thing is when installed, it's an empty file -- ready for customisation.

> **windependence said:**
> Why all the 

```
#! /bin/bash
# Needs to be called with "sudo bash installs"
```comments in the install commands? Did you install this with a script? I'm confused.

Pardon me? would YOU type all those command over and over again? OF COURSE I make a bash file!

The comments are for YOUR convenience, to see how it's used.

> **windependence said:**
> 
I think a simple

```
sudo apt-get install apache2 
```would have done it, but I don't run any of my hosts on Linux. They're all *BSD. Much simpler, more stable <flame suit on> ;)

How do you think I started?

When the "simple" things don't work, you try to find out what's needed to make it work.

[flame on]
Why do you post any comments at all, if you don't know what you're talking about?[flame off]

---

### Post by kennedy7 on 2008-08-27
Just take off everything off but apache and install phpgroupware. That will let you run php scripts and stuff, all that you wanta do. It will help allot.
That what im running on my webserver.

---

### Post by kennedy7 on 2008-08-27
But what im saying is phpgroupware is much easier to setup.
all you gota do is make all your passwords the same in the setup,just makes them easier to remember, when it comes to a screen that wants your hostname type in your ip. you can get your ip by going to [http://checkip.dyndns.org]("http://checkip.dyndns.org") that will be your ip. thats what you type in to the box. 
I had the same problem when i first started a webpage about a year ago. then i heard about phpgroupware. installed it and everthing worked.

---

### Post by forger on 2008-08-27
How about checking out the ubuntu help guide:
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by ingeva on 2008-08-27
> **kennedy7 said:**
> Just take off everything off but apache and install phpgroupware. That will let you run php scripts and stuff, all that you wanta do. It will help allot.
That what im running on my webserver.

Thanks! I'll make a note of this. Never heard of phpgroupware before. If someone had told me about it before I might have saved a lot of trouble.

However, I've solved the php problem, and there's just a small problem left regarding Virtual Hosts. I'll either solve that or find another solution.

The most important reason to stick to apache in spite of its unfriendliness, is that the "real" web server uses it, and I like as much as possible to be the same. Apache has the .htaccess and the .passwd files etc.. It's very nice to know that everything will work the same when things are uploaded.

---

### Post by ingeva on 2008-08-27
> **deepak1uw said:**
> Hi people!,

I installed PHP5, apache2 and MySQL for a testing server.


How has this turned out for you now?
(I don't use MySQL myself, but I might in the future. If you have resolved your problem, please inform us about the solution here, and mark the thread as [Solved].

Thanks!

---

### Post by ingeva on 2008-08-27
> **kennedy7 said:**
> But what im saying is phpgroupware is much easier to setup.
all you gota do is make all your passwords the same in the setup,just makes them easier to remember, when it comes to a screen that wants your hostname type in your ip. you can get your ip by going to [http://checkip.dyndns.org](http://checkip.dyndns.org) that will be your ip. thats what you type in to the box. 
I had the same problem when i first started a webpage about a year ago. then i heard about phpgroupware. installed it and everthing worked.

My web server is strictly confined to my local network. It is not meant to be accessible from outside. I have an external host for that.
phpgroupware might still be used, of course.

---

### Post by mbeach on 2008-08-27
the httpd.conf file is there in case some third party application is hardwired to put its settings there (like Cold fusion (jrun)).  Apache.conf loads it for that reason only.

Apache is not a difficult thing.  I don't imagine there'll be much in the Apache documentation about Cold Fusion, Python, PHP, Ruby etc - why would there be.

To get php working once all the bits are in place (which several tutorials explain) is to ensure the the www-data user can run the script.  The easiest way I've seen is to ensure www-data owns the file.

If apache has no awareness of php, then something was skipped in the setup.  I'd install "libapache2-mod-php5" then try a "sudo a2enmod php5", then ensure that /etc/apache2/mods-available/php5.conf" is as you want it.

The apache documentation is fine - what could make it better?

I suspect that after following several tutorials and adding things to configuration files, and not removing them when they didn't work may have left you with quite a non-standard setup.

---

### Post by kennedy7 on 2008-08-27
Thank you.

---

### Post by ingeva on 2008-08-28
> **mbeach said:**
> If apache has no awareness of php, then something was skipped in the setup.  I'd install "libapache2-mod-php5" then try a "sudo a2enmod php5", then ensure that /etc/apache2/mods-available/php5.conf" is as you want it.


I posted my installation setup here. No one reported anything missing there, and nothing was. But Apache needs instructions about when and how php should be scheduled.

> **mbeach said:**
> The apache documentation is fine - what could make it better? 

The Apache documentation is TERRIBLY confusing. Almost any change would make it better! :)  But of course, it should be supplemented with a "directions for use" section, instead of taking every chapter out of context. After all, things hang together. The apache doc. doesn't explain much about how.

> **mbeach said:**
> I suspect that after following several tutorials and adding things to configuration files, and not removing them when they didn't work may have left you with quite a non-standard setup.

The nice thing is that I have not removed a syllable except the "default" VH file.
Also, I have ensured that my setup will not be affected by an upgrade or re-installation since I've moved the working files to a disk number 2 (under the /home directory).

I wouldn't think that what and how I've been writing here should give the impression that I had hardly used a computer before. I'm new to Linux and Ubuntu, but I've been working with Unix systems as a real-time programmer for years (and with other RT systems before that). I've just not had any need for Apache before, and that program is probably the worst example I've ever encountered, to how to complicate things that are really quite simple. A simple user's guide should be all that's required, and I wouldn't call the present documentation **that**. :)

---

### Post by windependence on 2008-08-28
You don't need to remove the default VH file, just disbale it like this:

```
sudo a2dissite default
```

This removes the symlink in /etc/apache2/sites-enabled and allows all your Vhosts to work as expected.

Apache is really very well laid out IF you use it as designed with the modular configuration. Don't be tempted to "override" things by using httpd.conf or putting configs directly in sites-enabled.

I don't mean to be rude here but it's quite obvious to me that you do not have the experience you claim with Unix and Unix-like systems. There is nothing wrong with that, all of us had to start somewhere. Just try to keep and open mind when someone suggests that you might be doing things the "non-standard" way.

-Tim

---

### Post by ingeva on 2008-08-28
> **windependence said:**
> You don't need to remove the default VH file, just disbale it like this:

I know that now, but I removed it anyway (or rather moved it to sites-available)

> **windependence said:**
> things by using httpd.conf or putting configs directly in sites-enabled.

I didn't tell you that I didn't use the links in sites-enabled. You must have gotten that from somewhere else.

> **windependence said:**
> I don't mean to be rude here but it's quite obvious to me that you do not have the experience you claim with Unix and Unix-like systems. There is nothing wrong with that, all of us had to start somewhere. Just try to keep and open mind when someone suggests that you might be doing things the "non-standard" way.

I may be a little rusty after 10 years with only Windows, but my experience with unix systems should be adequate. NOT Linux. I've just touched that before, many years ago, but it was too immature then.
It's also very strange that even after searching so much for information and studying so much documentation that only added to the confusion, that someone didn't tell me about the "standard" way before I found a slight variation from the standard that actually works.

Instead of keeping some commands in the httpd.conf file, I could move them to apache2.conf instead. But that would give me a modified (and non-standard!!) file!

No customisation is "standard" anyway.

Without this forum I wouldn't have been where I am now. After one week with Ubuntu I had everything going near perfect. The ONLY thing I had some trouble with was Apache, and now I have a backlog because there are several web sites in dire need of an upgrade. I can finally start working on those now.

---

### Post by deepak1uw on 2008-08-30
> **mbeach said:**
> according to:
[http://ubuntuforums.org/showthread.php?p=5613998](http://ubuntuforums.org/showthread.php?p=5613998)
you can likely find phpmyadmin at:
/usr/share/phpmyadmin
there is probably some pointer to it in either /etc/apache2/apache2.conf or in /etc/apache2/sites-available
I also far prefer mysql's tools ([http://www.mysql.com/products/tools/](http://www.mysql.com/products/tools/)) instead of phpmyadmin, but that's a matter of personal preference.

if you change the ownership of the php file, you'll probably get what you are after:
```
sudo chown www-data:www-data /var/www/phpinfo.php
```

but I don't think you need the 'echo'.
you just need:
[PHP]<?php
// Show all information, defaults to INFO_ALL
phpinfo();
?php>[/PHP]

Thanks mbeach.... every things working fine now !!


> **ingeva said:**
> How has this turned out for you now?
(I don't use MySQL myself, but I might in the future. If you have resolved your problem, please inform us about the solution here, and mark the thread as [Solved].

Thanks!

Sorry for late reply but i was out of station and i just came back today and tried "mbeach's " solution and now every thing (PhpMyAdmin, MySql-Server-5.0, Apache2.2-common,PHP-5.0) working fine for me.

---

### Post by ingeva on 2008-08-30
> **deepak1uw said:**
> Sorry for late reply but i was out of station and i just came back today and tried "mbeach's " solution and now every thing (PhpMyAdmin, MySql-Server-5.0, Apache2.2-common,PHP-5.0) working fine for me.


I'm glad to hear it!
I haven't configured phpMyAdmin myself, but I had similar problems as yours with php. It simply wouldn't work "out of the box" like everyone claimed it should.

If I ever need MySql in my own computer or network (Can't see that I will) I'll know where to go! :)

Sorry for hijacking your thread! I just hope that the conversation helped you too.

---

