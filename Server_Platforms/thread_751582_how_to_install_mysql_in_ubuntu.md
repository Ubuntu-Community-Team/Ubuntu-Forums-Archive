---
title: "how to install mysql in ubuntu"
date: 2008-04-10
forum: Server Platforms
---

### Post by jamess_jack on 2008-04-10
H

---

### Post by mmichalik on 2008-04-10
If you are trying to set up a MySQL Server on your machine:

sudo apt-get install mysql-server

if there are any dependencies, apt-get will install them as well.

If you just want the client, it's:

sudo apt-get install mysql-client

---

### Post by jamess_jack on 2008-04-10
Thankx 

It is installed and I have started by

sudo " /etc/init.d/mysql start"

But Now I want access the server so what should I do ??

---

### Post by mmichalik on 2008-04-10
The easiest thing to do is go to [www.webmin.com](www.webmin.com) and download and install the debian package.

Webmin is a GUI administration program that will help you run all sorts of different things in Ubuntu.  It has a great MySQL module that works very nicely.

Give it a try, it's easy to use and works very well.

---

### Post by Deathrend on 2008-04-11
I use phpMyAdmin for most of my MySQL needs, which is really easy to install on ubuntu

```

sudo apt-get phpmyadmin

```

Normally you have to do a lot of setup, however this does it all for you.

Check out [http://www.phpmyadmin.net/home_page/index.php](http://www.phpmyadmin.net/home_page/index.php) for more information.

---

### Post by Koybe on 2008-04-11
To just connect trough the command line :

```
mysql -u user -p
``` if you have a password
```
mysql -u user
``` if you don't

---

### Post by Deathrend on 2008-04-11
> **Koybe said:**
> To just connect trough the command line :

```
mysql -u user -p
``` if you have a password
```
mysql -u user
``` if you don't

I don't see him knowing what to do once he's in there, if he can't figure out how to even log though.  I'm guessing he's just trying to set up a database for an outside program/web ap, which if you don't know what you're doing, is much eiser to do via phpmyadmin than using the CLI

---

### Post by Koybe on 2008-04-11
Well I was just telling another way. If he doesn't want to use it, up to him. It's the server platform forum not the beginner one...

It could be to practice SQL or whatever, his question was quite short! :o

Sorry but I don't see why you're complaining, just let my post go then...

---

