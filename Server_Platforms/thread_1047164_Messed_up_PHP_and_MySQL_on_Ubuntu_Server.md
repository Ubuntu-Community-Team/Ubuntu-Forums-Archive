---
title: "Messed up PHP and MySQL on Ubuntu Server"
date: 2009-01-22
forum: Server Platforms
---

### Post by don_c on 2009-01-22
I have Ubuntu Server 6.06 as a web development test server and have been running trouble free for a very long time after doing only the original LAMP set-up.  PHP was version 5.1.2 and I made the mistake of following some advice to upgrade to 5.2.  It totally messed up my system and I need some help getting it back.

(I added the following to repositories and did an upgrade:
deb [http://packages.dotdeb.org](http://packages.dotdeb.org) stable all
deb-src [http://packages.dotdeb.org](http://packages.dotdeb.org) stable all)

Current problem - apache runs OK but when I call for a PHP page it wants to download the php source and not display anything.

Rightly or wrongly I removed the failed PHP5.2 and thought I would reinstall the current PHP version from the standard repositories.  Seemed to install OK but i have the problem above.

I have tried:
  apt-get install libapache2-mod-php5 - already newest version
  a2enmod php5 - already enabled
  restarting apache2 (a few times just in case...)

I have tried searching but the search terms throw up so much unrelated stuff I couldn't find anything relevant.

NOTE - this installation was working before and has been used extensively but I may have forgotten things I tweaked in the early days so don't assume anything...

I also screwed up MySQL but I thought I would get on and sort PHP first.

Any assistance will be hugely appreciated!

---

### Post by bobsta63 on 2009-01-22
Hi there,

Well it appears that Apache doesnt know to execute the PHP script that you call (hence why it just displays the source), So I would advise adding this line to your httpd.conf file, basically the line it telling Apache to parse any files with .php extentsion with PHP before sending the output.

```
AddHandler x-httpd-php .php
```

If this doesnt work let me know... I'll have another think im sure this is the problem however!! :)

Regards,
Bobby

---

### Post by don_c on 2009-01-22
Didn't work I'm afraid.

My httpd.conf is empty apart from a Option -Indexes I added myself to prevent users viewing an upload folder.  Otherwise the comments say it is only for backwards compatibility and to use the mods-enabled folder.

In that folder I have php5.conf and php5.load.  Maybe they are the wrong version?..

---

### Post by bobsta63 on 2009-01-22
> **don_c said:**
> Didn't work I'm afraid.

My httpd.conf is empty apart from a Option -Indexes I added myself to prevent users viewing an upload folder.  Otherwise the comments say it is only for backwards compatibility and to use the mods-enabled folder.

In that folder I have php5.conf and php5.load.  Maybe they are the wrong version?..

In that case, you should add the line to the php5.conf file, Apache is obviously not using httpd.conf and therefore a config file somewhere will be calling all scripts int he /mods-enabled folder. - In theory this should work... I hope you get it resolved soon.

I hope you understood my logic behind adding that line to the apache configuration file...

If you want you should be able to create a file in the /mods-enabled folder called enable_php.conf for example and add that line (as I wrote in my original post)... afterwards you will ofcourse need to restart the apache daemon for the changes to take effect :)

Regards,
Bobby

---

### Post by don_c on 2009-01-22
Had this in php5.conf already:

<IfModule mod_php5.c>
  AddType application/x-httpd-php .php .phtml .php3
  AddType application/x-httpd-php-source .phps
</IfModule>

Tried adding your suggestion first in here then in separate .conf file - still doesn't work...

---

