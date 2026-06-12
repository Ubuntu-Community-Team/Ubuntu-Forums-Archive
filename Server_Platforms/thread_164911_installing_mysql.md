---
title: "installing mysql"
date: 2006-04-23
forum: Server Platforms
---

### Post by Rollo Tamasi on 2006-04-23
when i attempt to install mysql thru terminal i get this error 
> mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user: 'root@localhost' (Using password: NO)'


i was using this command 
```
mysqladmin -u root password yourrootsqlpassword
```

what should be in the password field? how do i sort that out. This is a fresh install so i thought i could put in anything as my rootsqlpassword.

---

### Post by Ensnared on 2006-04-23
Try this:
```
mysql -u root -p
```
Then enter your password when prompted.

EDIT
Err... nevermind - I read that incorrectly, sorry :) I'll see what I can find out though - maybe there's a default root password when installing on Ubuntu...

EDIT2
Try this:
```
mysqladmin -u root password "yourrootsqlpassword"
```
I suppose the quotes are mandatory, which might be why it fails.

---

### Post by Rollo Tamasi on 2006-04-23
[QUOTE=Ensnared]Try this:
```
mysql -u root -p
```
Then enter your password when prompted.

EDIT
Err... nevermind - I read that incorrectly, sorry :) I'll see what I can find out though - maybe there's a default root password when installing on Ubuntu...
[/QUOTE]

that worked!
i dont suppose you know how i would setup phpmyadmin now properly. When i log into it i dont have any premissons. i dont really know what to do

---

### Post by Ensnared on 2006-04-23
[QUOTE=Rollo Tamasi]that worked!
i dont suppose you know how i would setup phpmyadmin now properly. When i log into it i dont have any premissons. i dont really know what to do[/QUOTE]
Actually I have no idea... when I installed it I simply did "apt-get install phpmyadmin" and it Just Worked(tm)... Of course, I didn't start out with a fresh database, so there might be some quirk to it in that case.

Does it let you log in at all? Cause if so, it should all be set up properly. If it doesn't let you log in then it's a username/password issue, or some problem phpmyadmin has with communicating with the MySQL database.

Are you able to login with the command line client?```
mysql -u root -p
<enter password>
show databases;
use mysql;
select * from user;
exit;
```...just to try a couple of things to see if everything is set up right.

You can also try restarting apache and mysql after having it all installed.```
sudo /etc/init.d/apache2 restart
sudo /etc/init.d/mysql restart
```

---

### Post by Rollo Tamasi on 2006-04-23
i think my main problem is in creating a database. so far i have tried the guidelines outline in the ubuntu guide website. The most promising part of my quest has being with mysql control centre. I have that installed but i dont know what to do with it tbh. I have tried to create a new database but i have failed. All i really want is one database up and running. Any help is much appriciated.

---

### Post by Ensnared on 2006-04-23
Well, if all you want is a database up and running and you can log in as root using the command-line client, then this is how you do it:
```
mysql -u root -p
<enter password>
create database mydatabase;
grant all privileges on mydatabase.* to 'theuser'@'localhost' identified by 'thepassword' with grant option;
flush privileges;
exit;
```
You'll then have an empty database called "mydatabase", accessible by the user "theuser" logging in from the local computer, using the password "thepassword". I assume you're trying to set up some kind of web-based application (a forum perhaps?) in which case the user accessing the database will be logging in from the local computer. Just make sure you enter "localhost" as the database-server hostname in the installation of your application. If you enter the actual hostname or the IP-address then you'll probably need to add access to the user logging in from any of those two as well - if so, just use the same command as above (the "grant all privileges" one) but substitute "localhost" with either the actual hostname or the IP-address.

It's also supposed to be possible to specify "any host" but I never got that to work last time I tried, but that's... uhm... 5 years ago ;)

Anyway, if you want to allow the user to log in from anywhere, this is the command:
```
grant all privileges on mydatabase.* to 'theuser'@'%' identified by 'thepassword' with grant option;
```You can use that instead of the one specifying "localhost" above.

---

### Post by Rollo Tamasi on 2006-04-23
you are some legend man! thanks, i was at my wits end with this. I need this server up and running in like 12 hours for a demo but i have a million other things to do. One last problem. Whenever i go to view a php file it doesnt render in the browser

i have installed php5 but i get the php returned to me as a .txt file in the browser, if you know what i mean!

for example my phpinfo file reads out
<?php phpinfo(); ?>
when i type in localhost/phpinfo.php into the browser

---

### Post by Rollo Tamasi on 2006-04-23
fixed that problem. i had a issue with my mime types as i suspected.

---

### Post by Ensnared on 2006-04-23
Ouch... uhm... well, the first thing to try is restart apache - if you just installed php5 then the configuration it adds to apache hasn't been loaded yet. Also, you may not have installed the apache module for php5, so make sure that's in first:```
sudo apt-get install libapache2-mod-php5
```
If that doesn't help (or if it's already installed), try restarting the webserver:```
/etc/init.d/apache2 restart
```

That really should be all there is to it to make it work. And you also need the php5-mysql package, but I assume you have that if you have phpmyadmin installed.

If this doesn't help, check the directory /etc/apache2/mods-available and make sure you have the files php5.conf and php5.load in there. Then, check the directory /etc/apache2/mods-enabled and make sure the two files in mods-available have symlinks pointing to them in there. If they aren't, create them:```
cd /etc/apache2/mods-enabled
sudo ln -s /etc/apache2/mods-available/php5.conf .
sudo ln -s /etc/apache2/mods-available/php5.load .
```

Then restart apache again - let me know what you find out :)

EDIT
Ok, nevermind then ;) I was too slow this time around :D

---

### Post by LordHunter317 on 2006-04-23
FWIW, you don't need to do a 'FLUSH PRIVILEGES' when doing 'GRANT' or 'REVOKE'.

---

### Post by Ensnared on 2006-04-24
[QUOTE=LordHunter317]FWIW, you don't need to do a 'FLUSH PRIVILEGES' when doing 'GRANT' or 'REVOKE'.[/QUOTE]
That's true - I've just made a habit of doing it just to be on the safe side :)

---

