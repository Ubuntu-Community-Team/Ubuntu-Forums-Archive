---
title: "PHP and GD In Ubuntu"
date: 2005-08-11
forum: Server Platforms
---

### Post by noob_Lance on 2005-08-11
Hey, well let me say... the first hour of having ubuntu installed... i was rippin out hair. now im gettin the hang of this. But im trying to get used to installing and config'ing it to a server. But i cant seem to get some extensions installed. 

I need to install the GD extention... but i have no clue how. can someone please help me. Thanks Alot

~Lance

---

### Post by drummer on 2005-08-11
sudo apt-get install php4-gd

you can search at [http://packages.ubuntu.com/](http://packages.ubuntu.com/) for available packages to install (if you're working from a command line) and there is some info on how to set up apache, mysql, etc. at [http://www.ubuntuguide.org/](http://www.ubuntuguide.org/)

---

### Post by noob_Lance on 2005-08-11
hm... ok well it went thru its little process, but whats next. im lost cuz im so new to linux :S help lol

---

### Post by relix42 on 2005-08-11
If you apt-get process completed successfully, you should be good.  You may want to restart apache2 for good measure (force php to re-read the php.ini file.)

Post back with a bit more detail if you are still having problems.

---

### Post by drummer on 2005-08-11
To test if PHP is working properly, you can create a new file (eg, info.php) in the root of your web server (/var/www by default) and put this in the file:[PHP]<?php phpinfo(); ?>[/PHP] Then browse to the page by going to [http://[ipofserver]/info.php](http://[ipofserver]/info.php)
Where [ipofserver] is the IP address of the computer in your home network, or 127.0.0.1 if the server is the computer you are using. If PHP is working correctly, you should get a long page of info about the server and PHP.

---

### Post by noob_Lance on 2005-08-11
ill tell ya i aint new to php thats for sure... but setting it up on Linux... well ya got me beat there. 

Reading package lists... Done
Building dependency tree... Done
php4-gd is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 63 not upgraded.

that is what i got after i did it the second time. as for restarting apache... how :p lol

now... Linux That im not good with lol

---

### Post by noob_Lance on 2005-08-11
haha... nvm... i got it =D thx for the help peeps =D

---

### Post by trtech on 2007-08-15
```
sudo apt-get install php5-gd
sudo /etc/init.d/apache2 reload
```

gd_info() returns:

[PHP]Array
(
    [GD Version] => 2.0 or higher
    [FreeType Support] => 1
    [FreeType Linkage] => with freetype
    [T1Lib Support] => 1
    [GIF Read Support] => 1
    [GIF Create Support] => 1
    [JPG Support] => 1
    [PNG Support] => 1
    [WBMP Support] => 1
    [XPM Support] => 
    [XBM Support] => 
    [JIS-mapped Japanese Font Support] => 
)[/PHP]

I couldn't believe my eyes. Ubuntu rocks!

---

