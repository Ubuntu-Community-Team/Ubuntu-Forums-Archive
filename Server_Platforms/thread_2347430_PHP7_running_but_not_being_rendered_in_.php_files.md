---
title: "PHP7 running but not being rendered in .php files"
date: 2016-12-24
forum: Server Platforms
---

### Post by nickTaylor1181 on 2016-12-24
Hi all


I have a new ubuntu studio (16.04) install... am trying to set a a LAMP stack... all seems ok, but if I load a .PHP file it just outputs the code.

This:

 php -r 'echo "\n\nYour PHP installation is working fine.\n\n\n";'

works fine.

I've spent quite a long time searching for a fix for this, but am getting nowhere, and don't really know what I'm doing - probably need something a little more diagnostic.


Any help much appreciated.

---

### Post by wildmanne39 on 2016-12-24
*Thread moved to **Server Platforms**.*for the possibility of better support.

---

### Post by cariboo on 2016-12-25
Have you got libapache2-mod-php7 installed and enabled?

---

### Post by nickTaylor1181 on 2016-12-29
Hiya - thanks for your reply.

I don't know how to check if  libapache2-mod-php7 installed and enabled.

I've tried various things, eg: 

[http://askubuntu.com/questions/760907/upgrade-to-16-04-php7-not-working-in-browser](http://askubuntu.com/questions/760907/upgrade-to-16-04-php7-not-working-in-browser)

It doesn't seem to have any lines referencing : [COLOR=#111111][FONT=Consolas]php7.0-fpm

[/FONT][/COLOR]But I don't even really know if I'm on the right track - and that whole page seems massively complicated in comparison to getting LAMP to work in the past. 


Any idea what I need to do to figure out what is going on here? Or if there's some way of installing LAMP that works out of the box, as they say?

---

### Post by cariboo on 2016-12-29
Check /etc/apache2/mods-enabled, to see if these two files are there:

```
ls -l php*
lrwxrwxrwx 1 root root 29 Aug  4 09:26 php7.0.conf -> ../mods-available/php7.0.conf
lrwxrwxrwx 1 root root 29 Aug  4 09:26 php7.0.load -> ../mods-available/php7.0.load
```

if not install apache2-mod-php7, and enable it using the following command:

```
 sudo a2enmod php7.0
```

---

### Post by nickTaylor1181 on 2016-12-29
Hiya - thanks for your reply.


Both of those are there... when I run [COLOR=#000000][FONT=&quot] sudo a2enmod php7.0[/FONT][/COLOR]  , it gives:

```

Considering conflict php5 for php7.0:
Module php7.0 already enabled

```

I'm not sure what the considering conflict message means - but after restarting apache, it still isn't rendering the PHP - just outputs the text

---

### Post by SeijiSensei on 2016-12-30
I've never used Studio.  I just installed 16.04.1 Server in a VM on this machine and created a script called "info.php" with the command
```
<?php phpinfo() ?>
```
in /var/www/html.  Navigating to [http://ip.addr.of.server/info.php](http://ip.addr.of.server/info.php) brings up the expected PHP information page, all running PHP 7.0.

Did you install Apache+PHP by using "sudo apt-get install lamp-server^"?  That also installs MySQL.  Using the lamp-server^ package always seems to work for me.

---

### Post by nickTaylor1181 on 2016-12-31
Thanks - I think I'm going to be re-installing the entire OS due to a disaster elsewhere, so I'll do the lamp-server thing next time.

This time I installed the A, M and P parts separately - normally they just work... all I need to do is change the web directory, get curl working and tweak a couple of php.ini things. This time round though something has broken PHP's ability to render in a browser, and danged if I can find out how to fix it.

---

### Post by nickTaylor1181 on 2017-01-05
Okay - completely reinstalled ubuntu and installed LAMP with 

"sudo apt-get install lamp-server^"?

It will render php (ie: phpinfo(): ) in var/www (the default location)

But when I try to change it to a directory in /home/ it displays the PHP as unparsed text.


I suspect it might have been doing this before... any idea why it would parse in one directory but not in another?

[COLOR=#000000]


[/COLOR]

---

### Post by nickTaylor1181 on 2017-01-05
Arghh.... elementary schoolboy error. Short-tags weren't switched on.

---

