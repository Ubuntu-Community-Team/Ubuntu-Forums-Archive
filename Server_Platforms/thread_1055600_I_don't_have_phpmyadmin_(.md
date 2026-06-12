---
title: "I don't have phpmyadmin :("
date: 2009-01-30
forum: Server Platforms
---

### Post by dj_ee3 on 2009-01-30
Hi, I just installed lamp on my ubuntu 8.10. The problem is that nothing comes at [http://localhost/phpmyadmin](http://localhost/phpmyadmin) . I follow this tutorial right here: [http://albertux.ayalasoft.com/2008/11/10/lamp-on-ubuntu-810-desktop-edition/](http://albertux.ayalasoft.com/2008/11/10/lamp-on-ubuntu-810-desktop-edition/) I have done everything in it. After I completed the install I tried to install a script for which I had to create a database. I tried to access [http://localhost/phpmyadmin](http://localhost/phpmyadmin) and it showed me an error. Than  I come back to the tutorial and saw that it doesn't say to install phpmyadmin. So I did it on my own. I typed  sudo apt-get install phpmyadmin in the terminal. I installed it but still nothing comes at [http://localhost/phpmyadmin](http://localhost/phpmyadmin) can you help me please. Thank you in advice.

---

### Post by aaron.d on 2009-01-30
> I follow this tutorial right here: [http://albertux.ayalasoft.com/2008/1...sktop-edition/](http://albertux.ayalasoft.com/2008/1...sktop-edition/) I have done everything in it.

You mean the tutorial that DOESNT include instructions on installing phpmyadmin?

try:
[https://help.ubuntu.com/community/phpMyAdmin](https://help.ubuntu.com/community/phpMyAdmin)

also, no more references to "http://localhost/phpmyadmin", thrice was surely enough :)

---

### Post by dj_ee3 on 2009-01-30
I have install it by myself. But I can't open it so I can create a database.

---

### Post by kustomjs on 2009-01-31
do you have a domain? if you do it would be something like this [http://localdomain.com/phpmyadmin](http://localdomain.com/phpmyadmin)   or IP like this 10.23.88.44/phpmyadmin.

---

### Post by dj_ee3 on 2009-01-31
I have a real ip if that is what you mean. You can access my server from [http://68.55.1.14](http://68.55.1.14) again if you try [http://68.55.1.14/phpmyadmin](http://68.55.1.14/phpmyadmin) nothing will come up :(

---

### Post by kustomjs on 2009-01-31
ok here is what you need to do is remove it and re-install it by doing this apt-get install phpmyadmin in command line if you using putty.

and here is a guide how to do it:[https://help.ubuntu.com/community/phpMyAdmin]("https://help.ubuntu.com/community/phpMyAdmin")

---

### Post by dj_ee3 on 2009-02-02
I did it again from the terminal. Also I did what the Url you give me says and it doesn't work... I few really bad. I need that server!

---

