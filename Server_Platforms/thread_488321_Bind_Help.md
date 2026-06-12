---
title: "Bind Help"
date: 2007-06-30
forum: Server Platforms
---

### Post by Shadow Jolteon on 2007-06-30
I have been trying to get bind9 to work in Ubuntu for a couple days using **[this guide](http://www.ubuntugeek.com/dns-server-setup-using-bind-in-ubuntu.html)** for help, but I do not fully understand it.. I think I have done everything right, but when I try to reset it, it shows **[this](http://s127.photobucket.com/albums/p130/ShadowJolteon/bind9.png)**..

---

### Post by PaulFr on 2007-06-30
If this is the first time you are running bind, perhaps you should run **sudo /etc/init.d/bind9 start** and not restart ? You may also want to check **/var/log/syslog** for messages related to bind. See **[https://help.ubuntu.com/community/BIND9ServerHowto](https://help.ubuntu.com/community/BIND9ServerHowto)** for more details.

---

### Post by glenndavy on 2007-07-01
hey mr shadow... how'd you go with this?

---

