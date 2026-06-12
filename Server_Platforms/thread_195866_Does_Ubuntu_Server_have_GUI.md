---
title: "Does Ubuntu Server have GUI"
date: 2006-06-13
forum: Server Platforms
---

### Post by pbowrin on 2006-06-13
I am fairly familiar with desktop and now am trying to use server to intergrate into my wondows 2003 domain.   I would like to first like to use ubuntu server as a database server for a mysql database which windows clients will access.   

I installed the LAMP version but I'm uncertain how to use the apps using the command line interface.   Is there a GUI (KDE or GNOME) for the server version that can applow me to use Mysql, apache and the others using a GUI interface?

Thanks for your help

---

### Post by bruce89 on 2006-06-13
No, but you can install one later. ```
sudo apt-get install (x)
``` where x is ubuntu-desktop, kubuntu-desktop or xubuntu-desktop, depending on whether you want GNOME, KDE or XFCE.  As for configuration programs, I don't know.

---

### Post by dlai on 2006-06-13
Generally i would not recommend you to install anything graphic... your server will be much faster if you don't and furthermore you'll have to do most of your configurations commandline anyway... The mysql side can easily be controlled from another computer with phpmyadmin, if your prefer doing it grapically...

---

### Post by Iowan on 2006-06-13
There's also the option of installing a desktop and running it ONLY when you need it...
Here's a similar thread:
[http://www.ubuntuforums.org/showthread.php?p=1133095#post1133095]("http://www.ubuntuforums.org/showthread.php?p=1133095#post1133095")

---

