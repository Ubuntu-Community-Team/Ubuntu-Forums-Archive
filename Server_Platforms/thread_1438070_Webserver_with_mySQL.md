---
title: "Webserver with mySQL"
date: 2010-03-24
forum: Server Platforms
---

### Post by Bietje on 2010-03-24
Hello!

I'm making a webserver (httpd + PHP + MySQL). I have installed and configured apache and libxml2 (for PHP) succesfully. But now, I wanted to install mySQL, but here i get some errors.

I downloaded [this]("http://dev.mysql.com/get/Downloads/MySQL-5.1/mysql-5.1.45.tar.gz/from/http://mysql.mirror.easycolocate.nl/") version of MySQL. Then I (tried) to run ./configure:
```
groupadd mysql
useradd -g mysql mysql 
./configure --prefix=/opt/gdxweb/mysql --with-mysql-user=mysql
```It starts to configure, nothing odd.. but then at the end:
```
checking for tgetent in -lncursesw... no
checking for tgetent in -lncurses... no
checking for tgetent in -lcurses... no
checking for tgetent in -ltermcap... no
checking for tgetent in -ltinfo... no
checking for termcap functions library... configure: error: No curses/termcap library found
root@PCmichel:/opt/PCmichelweb/mysql-5.1.45# 
```And when I type *make && make install* it returns the following:

```
make: *** Geen doelen opgegeven en geen makefile gevonden.  Gestopt.
```Yess, thats dutch >.< sorry for that. It means: "make: *** No targets are are given and makefile is not found. Stopped.".

I tried Mr. Google, but he couldn't help me. Can you?

Greetings and thanks in advance!

---

### Post by lykwydchykyn on 2010-03-24
- First, is there a compelling reason why you're compiling it and not using the version readily available from the repositories?

 - Second, the error you're getting is a standard error that you get when ./configure fails.  In this case, it looks like it failed because you don't have all your build dependencies installed.

If you want to keep going the compile route, I'd suggest this command:
```

sudo apt-get build-dep mysql-server

```

But barring any special reason to compile, I'd just use what's in the repository.

---

### Post by dudumomo on 2010-03-24
Hi !
Why did you want to install mysql by compiling it when apt-get can do everything for you ?

But anyway, I guess you get your reasons.
So according to the error message..it's seems termcap lib is missing.

You may try:
sudo apt-get install libncurses-dev

EDIT: GRILLED

---

### Post by cdenley on 2010-03-24
Apparently you will have problems with init scripts as well, even if you do manage to compile it.
[http://ubuntuforums.org/showthread.php?p=9021624#post9021624](http://ubuntuforums.org/showthread.php?p=9021624#post9021624)

---

### Post by Bietje on 2010-03-24
The reason I wanted to compile is
a) the tutorial I used here and there did use the source code
b) the entire webserver is installed in one map (/opt/PCmichelweb).

That last reason is most important for me actually. It would be great if I can install the deb file downloaded with apt-get in /opt/PCmichelweb instead of somewhere in /usr. I allready have expirimented a bit with changing install dir's of .deb's but that failed epicly.. So if someone can tell me how, would that be great!

Greetings!

---

