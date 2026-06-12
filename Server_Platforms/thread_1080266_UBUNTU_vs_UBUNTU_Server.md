---
title: "UBUNTU vs UBUNTU Server"
date: 2009-02-25
forum: Server Platforms
---

### Post by rostamiani on 2009-02-25
Hello
I'm a beginner in linux and want to configure a webserver with UBUNTU :lolflag:

I don't know why ubuntu server does not have any XWindow interface
Can Gnome couse problems?
what is the difference between Ubuntu and Ubuntu Server?

Thanks ;)

---

### Post by 505 on 2009-02-25
Ubuntu server is specially meant for servers. It does not include things that normally you do not want on a server, such as Gnome. However, if you want to install a webserver on your currect Ubuntu you can simply install the package "Apache2" using Synaptic.

---

### Post by rostamiani on 2009-02-25
> **505 said:**
> Ubuntu server is specially meant for servers. It does not include things that normally you do not want on a server, such as Gnome. However, if you want to install a webserver on your currect Ubuntu you can simply install the package "Apache2" using Synaptic.
Thanks a lot
What is prefered :

1.Installing UBUNTU + Apache2 + PHP + Mysql
2.Installing UBUNTU Server + Gnome

---

### Post by 505 on 2009-02-25
Install Ubuntu and then Apache2, PHP, and MySQL. It's a lot quicker/easier than installing Gnome on Ubuntu server. You can install everything using Synaptic.

Wathever way you chose, the result should be the same, because the same packages are installed.

---

### Post by rostamiani on 2009-02-25
Thanks a lot :p

1.Is default settings of apache the same in two options?
2.What about LAMP? Do you recommend it? :popcorn:

---

### Post by 505 on 2009-02-25
1. Yes, the packages are the same, so the the settings will also be the same.
2. LAMP is basically Linux+Apache+MySQL+PHP. If you install everything you have a powerful platform. If you install it on your desktop (Ubuntu) it is very nice as a development computer. If you really want to have a webserver to server the Internet it might be worthwhile to have a dedicated machine and install Debian, as opposed to Ubuntu server. Debian is even more tailored to server environments. However, in the end, Ubuntu is a spin-off of Debian, so taken the time Ubuntu server can be as powerful.

---

### Post by rostamiani on 2009-02-25
And what about Fedora
I want to use UBUNTU or Fedora

Which is prefered ?(for ease of installation and configuration)

Thanks a lot

---

### Post by rostamiani on 2009-02-25
Do you know any lightweight GUI to install on UBUNTU Server ?
Smaller than Gnome . even in text mode !(something like NC in MSDOS)

---

### Post by Iowan on 2009-02-25
> **rostamiani said:**
> And what about Fedora
I want to use UBUNTU or Fedora

Which is prefered ?(for ease of installation and configuration)

Thanks a lotI haven't used Fedora since it was RedHat, but installing a LAMP server from the server-CD was about the least painful install I've done.
> **rostamiani said:**
> Do you know any lightweight GUI to install on UBUNTU Server ?
Smaller than Gnome . even in text mode !(something like NC in MSDOS)XCFE might be an option.

---

