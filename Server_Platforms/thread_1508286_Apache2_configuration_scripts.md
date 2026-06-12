---
title: "Apache2 configuration scripts"
date: 2010-06-12
forum: Server Platforms
---

### Post by Datamac on 2010-06-12
I am bit lost with configuring my apache2 web  server. From the book I am using it says for me to configure apache2 to  support PHP I need to execute "./configure --prefix=/usr/local/apache2  --enable-so".  From what I can determine Apache2 is located in  "/etc/init.d/apache2" folder.  I used a Ubuntu 9.04 distro (I386 Server  Ed.) to install the server. I added "Kubuntu-desktop" for viewing.  Then  performed web upgrade to Karmic 9.10.  All went well !!  Question is;  Where do I execute a command to enable PHP support?  Once again, the  command is to look something like "./configure  --prefix=/usr/local/apache2 --enable-so"

---

### Post by Ryan Dwyer on 2010-06-12
The book you're using is assuming you're compiling the source code. I wouldn't follow the instructions in that book.

You can install php5 support by running sudo apt-get install libapache2-mod-php5.

---

### Post by dapperdanny77 on 2010-06-13
Hi,

I think this could be a good starting point for you

[https://help.ubuntu.com/community/ApacheMySQLPHP]("https://help.ubuntu.com/community/ApacheMySQLPHP")

compiling from the sources is definitely harder than installing the distribution packages - from my point of view this is only necessary if you have your special needs 

cheers

---

