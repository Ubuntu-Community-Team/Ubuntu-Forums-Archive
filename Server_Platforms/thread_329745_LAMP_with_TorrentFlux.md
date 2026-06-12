---
title: "LAMP with TorrentFlux"
date: 2007-01-02
forum: Server Platforms
---

### Post by TechnoPenguin on 2007-01-02
I've been trying to install a LAMP server with TorrentFlux using [this howto]("http://www.howtoforge.com/ubuntu_lamp_torrentflux_vmware"). I get so far that my apache server is running and I try to get to [http://myip/tf/](http://myip/tf/) and all I get is:

```
Fatal error: Call to undefined function: mysql_connect() in /var/www/tf/adodb/drivers/adodb-mysql.inc.php on line 354
```

What's this? I didn't actually install a LAMP server in the beginning, I installed a Xubuntu 6.06 and then manually apache, php4, mysql but I'm pretty sure I have everything needed.

---

### Post by ikonia on 2007-01-02
for some reason your application is not aware of the mysql_connect function.

The error is pretty clear. 

Line 354 of the file /var/www/tf/adodb/drivers/adodb-mysql.inc.php  calls a function that is not recognised.

This could be the wrong versions of mysql/php compatability, php using its own internal mysql libs rather than the mysql client libs, bad configuration, or just bad php.

Good luck tracing it.

---

### Post by TechnoPenguin on 2007-01-02
Ok, I got it working. By reading the TorrentFlux FAQ I found this:

> Fatal error: Call to undefined function: mysql_connect() in /var/www/html/adodb/drivers/adodb-mysql.inc.php on line 354
This means that your version of php can't connect to the mysql database. Usually installing a package like php-mysql will solve this although if it doesn't then open your php.ini file and find the line like extension=mysql.so, remove the comment from in front, and then restart your webserver.


I tried adding the line to php.ini (which I found in /etc/php4/apache) and booted the server, but nothing happened. Then I uninstalled php4-mysql and replaced it with php5-mysql and now it works.

---

### Post by dfreer on 2007-03-09
Same error, confirmed fix by:
```
sudo apt-get install php5-mysql
```
and then rebooting. :D Thanks!

---

### Post by detectiveinspekta on 2007-03-30
I thought the whole idea of installing a LAMP server so that you didn't have to go through the difficulty of stetting everything up correctly.

The 6.10 server disk is supposed to setup LAMP, if you speed through it like I did when the option comes up to install LAMP or DNS its a tricky one.
Normally you press enter to select but in this case you had to press [space] or something to select it. So in the end alot of people had trouble setting up php-mod5 for apache when they thought the disk had done it.

---

