---
title: "How to in install a LAMP server"
date: 2006-06-13
forum: Server Platforms
---

### Post by boyou on 2006-06-13
I would like to install a LAMP server how do i go about it.

---

### Post by skafiskafnjak on 2006-06-13
Its best if you can download and burn Ubuntu Server disk (ISO).

Server installation disk have option that let you install LAMP.

---

### Post by jasonyu on 2006-06-14
[QUOTE=skafiskafnjak]Its best if you can download and burn Ubuntu Server disk (ISO).

Server installation disk have option that let you install LAMP.[/QUOTE]

Yes, it is more easy to setup a lamp server on ubuntu from 6.06 on. :razz:

---

### Post by boyou on 2006-06-14
I did download the server ISO and burned it to a CD . When i reboot the G5 holding down C key and i come to the boot: do i type in the option i want example:     boot: install a LAMP server   <enter> . The sever gudie book on page 11 gives me 2 options to choose from. When i boot up there are no options.

---

### Post by Pooldraft on 2006-06-14
Yea I was wondering the same thing the server guide give some comments on it but no details. I tried the "Install LAMP server" anyone have a more in depth guide or some hints. Thanks. 

-jdf

---

### Post by Indifferent on 2006-06-14
Try this walk through, it worked great for me:[http://www.howtoforge.com/perfect_setup_ubuntu_6.06]("http://www.howtoforge.com/perfect_setup_ubuntu_6.06")
Alternately, you can install the LAMP option from the CD and then configure it using this walk through.

---

### Post by boyou on 2006-06-14
Thank you Indifferent   P.S. It  must be an power pc problem because i tryed installing it on my powerbook G4 and i have the same issue of the install bye-passing the main ubuntu screen with the optons and go straight to the choose a language screen.

---

### Post by arix on 2006-07-12
You must install packages:
sudo apt-get install apache2-mpm-prefork mysql-server libapache2-mod-php5 php5-mysql

---

### Post by az on 2006-07-12
> **Pooldraft said:**
> Yea I was wondering the same thing the server guide give some comments on it but no details. I tried the "Install LAMP server" anyone have a more in depth guide or some hints. Thanks. 

-jdf

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)


Install 
apache2 php5-mysql libapache2-mod-php5 mysql-server

---

### Post by chrisfay on 2006-07-16
I wrote a tutorial on just this for new linux users. It may help:
[http://www.cjfay.com/lamp.html](http://www.cjfay.com/lamp.html)

---

