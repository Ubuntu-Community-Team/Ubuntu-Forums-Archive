---
title: "Am I right in saying that Ubuntu Server has no GUI?"
date: 2011-07-22
forum: Server Platforms
---

### Post by DeanoCeltic on 2011-07-22
Hi. Newbie here so please go easy :wink:

I've been playing about with Ubuntu Desktop on my laptop and it's been woking fine - it just fell on and has a nice GUI for you to use.

I decided to give Ubuntu Server a try on my PC so I installed it on a fresh hard drive. After installation completed I get the login screen prompt. Is the command line interface all I will see with Ubuntu Server? :confused:

I am used to Windows Server and am taking the step into the world of Ubuntu because I am going back to college and one of the first things I need to do is build a Linux server running Apache! Thanks!!

---

### Post by howefield on 2011-07-22
It is normal not to have a GUI on the server, so what you see is correct and quite normal.

You can however install your desktop GUI of choice, if you have to.

---

### Post by DeanoCeltic on 2011-07-22
Thanks howefield. I guess I'll just have to get used to the commands quickly! I'm going to pop into a bookstore and pick up a book. Got to start somewhere!

[[COLOR=#d40000]****[/COLOR]]("http://ubuntuforums.org/member.php?u=186490")

---

### Post by howefield on 2011-07-22
If you haven't come across it yet, here's a link that might help.

[https://help.ubuntu.com/10.04/serverguide/C/index.html](https://help.ubuntu.com/10.04/serverguide/C/index.html)

Also have a look at webmin.

[http://www.webmin.com/](http://www.webmin.com/)

> Webmin is a web-based interface for system administration for Unix. Using any modern web browser, you can setup user accounts, Apache, DNS, file sharing and much more.

---

### Post by DeanoCeltic on 2011-07-22
Great - thanks :)

---

### Post by dagamant on 2011-07-22
there is no GUI because it wants to save the CPU time for more important things like the webserver or SQL server. installing one is super easy once you decide which one you want, I use either lxde or xfce when I config a server for someone who needs one. to install xfce just run 'sudo apt-get install xubuntu-desktop' that will install everything xfce needs. keep in mind that most of the server applications that are available do not have a GUI interface and are managed through config files so even with a GUI installed you will still be working through a terminal in most cases.

---

### Post by dozycat on 2011-07-22
that´s true that usually application are configurated by text file by sometimes you can install gui for them, for example xsamba for samba.

---

