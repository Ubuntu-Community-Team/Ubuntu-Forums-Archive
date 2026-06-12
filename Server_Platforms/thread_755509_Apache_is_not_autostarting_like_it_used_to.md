---
title: "Apache is not autostarting like it used to"
date: 2008-04-14
forum: Server Platforms
---

### Post by rompstar420 on 2008-04-14
Hi there...

I am running on Ubuntu 7.10 and Apaches used to start automatically without problems on boot or reboot. Everything seems to run well after boot, but Apache doesn't start automatically.

I have to issue a command like:

sudo /etc/init.d/apache2 restart

then it works, it says that apache is not running, and then it starts it... then everything seems to work... What log files would I look into to see where the problems lies ?

Maybe there is a configuration file that has something in it apache doesn't like.

Thanks

RompStar

---

### Post by mthaddon on 2008-04-14
Check for a symlink in /etc/rc2.d to /etc/init.d/apache2. If there isn't one, you'll want to create it. The notation is S{[0-9][0-9]} - the "S" means start (i.e. it will run on startup) and the number is the order in which it will be executed, relative to the other items in this folder.

---

### Post by rompstar420 on 2008-04-14
cool, I did this:

sudo ln -s /etc/init.d/apache2 S15apache

now reboot to test...

---

### Post by rompstar420 on 2008-04-14
It works, cool thanks!

---

