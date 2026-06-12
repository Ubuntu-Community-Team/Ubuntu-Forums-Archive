---
title: "problem with ubuntu server 11.04 and ispconfig3 please help me"
date: 2011-09-27
forum: Server Platforms
---

### Post by gabikilalala on 2011-09-27
hello, 

well i am trying to install the "perfect server" with ubuntu 11.04 server 32 bit with a guide called smthing like isp config3-perfect server.
well it says that i must remove apparmor so i can continue the configuration and the installation of ispconfig 3.

please help me i am trying for weeks 
thank you very much:p

---

### Post by ibutho on 2011-09-27
Can you post a link to the tutorial you are using?

---

### Post by gabikilalala on 2011-09-27
yes yes yes...
thank you

[http://www.howtoforge.com/perfect-server-ubuntu-11.04-ispconfig-3-p4](http://www.howtoforge.com/perfect-server-ubuntu-11.04-ispconfig-3-p4)

:p

---

### Post by gabikilalala on 2011-09-27
well in page 3.and after i removed it a could not update or install any package. please help:D

---

### Post by ibutho on 2011-09-27
Did you uninstall apparmor or did you just disable it from starting up? If you uninstalled it, were any other packages removed along with apparmor?

---

### Post by gabikilalala on 2011-09-27
well i did what the guide says...i ran in terminal

/etc/init.d/apparmor stop
 update-rc.d -f apparmor remove
 apt-get remove apparmor apparmor-utils

in root mode..

everything goes well and then i ran 

apt-get install ntp ntpdate.
and it gets Errors..E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
well sorry if i dont describe this well./
thank you

---

### Post by ibutho on 2011-09-29
Try running
```
apt-get update
```
or 
```
apt-get update -m --fix-missing
```

---

