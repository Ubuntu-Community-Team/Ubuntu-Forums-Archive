---
title: "lamp ( &quot;reset&quot; ) problems"
date: 2012-04-07
forum: Server Platforms
---

### Post by nico23 on 2012-04-07
//dont laugh but i fixed this (not entirely) by just restarting apache. funny thing; my windows logic fails at linux or something else. when i purged everything i assume there cant be a apache running and after (re)install it starts automatically right? so i dont really get why i restart fixed this.

now my next problem ist that my site requires "755 or 777" for 2 folders acording to getsimple cms. i set this folders to 777 but getsimple still tells be it cant write. the folder is by default owned by root. am i right this is wrong for write access from browser?

outdated:

This is a normal desktop kubuntu 12.04 workstation not a server but i think it fits this category
[B]
index.php[/B]
```
<html><body><h1>It works!</h1>
<p>This is the default web page for this server.</p>
<p>The web server software is running but no content has been added, yet.</p>
<?php phpinfo(); ?>
</body></html>
```

_short version:_
i have my firefox open me a phtml file download instead of serving me the generated html code from my php file.
lamp should be very stable even in beta right?

_long version:_
I am now rally getting crazy about my apache mysql php testing config.

It all started with the lamp install "sudo tasksel install lamp-server". It worked fine.  Then the sad bs happened. i wanted to write as a normal user to /var/www and i did this: [http://askubuntu.com/a/51337](http://askubuntu.com/a/51337) > "sudo adduser <username> www-data; sudo chgrp -R www-data /var/www; sudo chmod -R g+rw /var/www; find /var/www -type d -print0 | sudo xargs -0 chmod g+s" and i really dont understand advanced permissions and i dont want to right now to me honest. i mixed that up with the normal andwer with was. > sudo adduser <username> www-data
sudo chown -R www-data:www-data /var/www
sudo chmod -R g+rw /var/www

anyway i got this "half working" the and then i wanted to enable mod_rewrite and blabla i got a bad tut or something and set allow overwrite for the default site to Filesomething, it has the be All right?

anyway this mess ended into stange errors in some folders and others not. the maybe had to do with the permission stuff i messed up there.
i disabled the mod rewrite and deleted the .htacess and it still not worked.
**the strangest thing during this was happened was that some pages of the site worked and the ones with my code did not. (i am using a self coded site based on getsimple cms). it showed me a error in my main php file saying unexpeced $end. but i am 1000% sure that this site works on my windows xammp server and a older version of that file is online right now on a linux server of my webhost and it works! i tryed that as well - same error. so why the f*** is that a end of file error like i not closed a brackets of a function for a valid working php file?**

i tryed some packed reinstalling, after deinstalling some packages it wanted to automatically install php-cgi and i did even it i dont wanted. just because apt wanted it.

at this point i just wanted to start over i did 
[this]("https://help.ubuntu.com/community/ApacheMySQLPHP"). 

> sudo apt-get remove --purge apache2 apache2-mpm-prefork apache2-utils apache2.2-common libapache2-mod-php5 libapr1 libaprutil1 libdbd-mysql-perl libdbi-perl libmysqlclient15off libnet-daemon-perl libplrpc-perl libpq5 mysql-client-5.0 mysql-common mysql-server mysql-server-5.0 php5-common php5-mysql
the doc said i should simulate this. i did and i saw that i wanted to remove some other things. one for example was amarok and it replaced some mysql stuff with sqlite. what i am supposed to do if i dont want that? i went with it and just purged amarok and stuff all together. after that i completly deleted the /www/var dir

i end up with my firefox open me a phtml file download instead of serving me the generated html code from my php file.

so the big question now: when i PURGE all this stuff and now reinstalled it with "sudo tasksel install lamp-server" why the fu** is it not like it supposed the be and like it was in the first place. sorry but this is really annoying for me i am more a windows user but i like linux and i want to switch, but under windows all i would have to do is desinstall xmapp and reinstall it and it would be default like it should be.

so what is f..ed up now? can somebody explain what got not purged or not configured like the first time? of course there might be something i could do to get this working now. but i really like to understand why its not simply "reset".

next time i make a image of my disk after install. this is really annoying. i should have just edit my site as root and let it all be like it was default.

---

