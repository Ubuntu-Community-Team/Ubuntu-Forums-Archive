---
title: "LAMP install"
date: 2006-07-05
forum: Sun Sparc Users
---

### Post by grantquinn on 2006-07-05
What is the best way to install AMP after you have Ubuntu running on a Server.
is it just apt-get install apache mysql-server php5 ?

---

### Post by chris_andrew on 2006-07-05
Hi,

Is there an option to do a LAMP install, when you boot the install.  I seem to remember seeing something.  failing that, it should be as simple as an apt-get.  If you search the Ubunu 6.06 release notes, it does mention a "one step lamp" procedure.  it amy be worth looking into that.

This link may help:

[https://help.ubuntu.com/pdf/ubuntu/C/serverguide.pdf](https://help.ubuntu.com/pdf/ubuntu/C/serverguide.pdf)

The "P" can also stand for Perl/ Python.....etc

Hope this helps.

Chris.

---

### Post by grantquinn on 2006-07-06
No unfortunately there is no option for LAMP install on the sparc install, thanks Grant

---

### Post by grantquinn on 2006-07-06
doing "sudo apt-get install apache2 php5-mysql libapache2-mod-php5 mysql-server" works!

---

### Post by chris_andrew on 2006-07-06
At the boot: prompt there is a "lamp-install" or "lamp-install-expert" option.

---

### Post by jpgeerets on 2006-07-06
i also missed a lamp install option during install on sparc.

i can try it tomorrow.
normaly, when booting of cd, you can type install. at this place you can type: 
"lamp-install" or "lamp-install-expert" ?

during install on a i386, lamp install was a menu option if i remember well

Jean-Paul

---

### Post by jpgeerets on 2006-07-07
lamp-install doesnt work at boot prompt.

im going to try the other suggestion.

thanks!

Jean-Paul

---

### Post by sinaen on 2006-07-07
i want to install a ubuntu server. but i only have a debian stable server. that is without cdrom. and i woder what the repositories is...

then i can upgrade and install lamp and other cool server-stuff

edit: and i don't have a screen to it either.

---

### Post by chrisfay on 2006-07-16
Check out this how-to I wrote on installing LAMP on Ubuntu 6.06 server. It is pretty dumbed down which may be a good or bad thing.... [http://www.cjfay.com/lamp.html](http://www.cjfay.com/lamp.html)

---

### Post by jpgeerets on 2006-07-25
> **grantquinn said:**
> doing "sudo apt-get install apache2 php5-mysql libapache2-mod-php5 mysql-server" works!

yeah,
this works...
now a little apache2 config and stuff worked well.

tnx!!

---

