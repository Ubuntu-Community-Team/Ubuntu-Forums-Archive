---
title: "Ubuntu 5.10 Server"
date: 2007-03-04
forum: Server Platforms
---

### Post by techresmgt on 2007-03-04
I am a complete newbie to Ubuntu/Linux, but am anxious to learn more.  I have a Ubuntu 5.10 Server (x386) and need to know how to administrate the account names and users on the server system.  Where can I get this kind of information?  Is it simply a matter of learning and using the BASH Shell?

---

### Post by jtc on 2007-03-04
A good place to start is [https://help.ubuntu.com/](https://help.ubuntu.com/)

What you might consider is that you probably want to upgrade your Ubuntu in the near future. If I'm not mistaken the 5.10 will soon (April?) not be supported anymore.

---

### Post by GoBieN on 2007-03-05
For easy administration of user accounts and such, i would recommend webmin. Its and web based management panel and its really good.

First set a root password if it has not been set yet -> sudo passwd root
Don't forget this password.

install webmin like this: sudo apt-get install webmin

afterwards surf to [https://ip-address:10000](https://ip-address:10000) and login with root and your password. On the system menu choose "users & groups"

---

