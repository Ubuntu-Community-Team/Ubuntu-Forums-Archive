---
title: "phpmyadmin configuration failed"
date: 2010-01-28
forum: Server Platforms
---

### Post by G9M29 on 2010-01-28
I've tried to install phpmyadmin, but when the blue screen pop up, I forgot to choose the server end press enter directly, so I now have localhost working and localhost/phpmyadmin not working. 

I'd be glad to hear the answer of solving the problem of How to config my phpadmin so it can work.

I've tried to remove all files ( and after every row I've always checked with

sudo apt-get remove phpmyadmin 

and it aways send to me that the package was not installed so it cannot be removed, but every time after that, when I tried to install it again the blue screen never poped up again [-o<[-o<[-o< please help

---

### Post by G9M29 on 2010-01-28
I've tried to install phpmyadmin, but when the blue screen pop up, I forgot to choose the server end press enter directly, so I now have localhost working and localhost/phpmyadmin not working.

I'd be glad to hear the answer of solving the problem of How to config my phpadmin so it can work.

I've tried to remove all files ( and after every row I've always checked with

sudo apt-get remove phpmyadmin

and it aways send to me that the package was not installed so it cannot be removed, but every time after that, when I tried to install it again the blue screen never poped up again please help

sorry for the double post, I just found the right place for the topic and I'm very nervous because of the problem

SOLVED

just reconfiguration the old fails :)

---

### Post by G9M29 on 2010-01-28
I've tried to install phpmyadmin, but when the blue screen pop up, I forgot to choose the server end press enter directly, so I now have localhost working and localhost/phpmyadmin not working.

I'd be glad to hear the answer of solving the problem of How to config my phpadmin so it can work.

I've tried to remove all files ( and after every row I've always checked with

sudo apt-get remove phpmyadmin

and it aways send to me that the package was not installed so it cannot be removed, but every time after that, when I tried to install it again the blue screen never poped up again please help

sorry for the double post, I just found the right place for the topic and I'm very nervous because of the problem


SOLVED

just reconfiguration the old fails :)

---

### Post by John Rivera on 2010-01-28
Have you any anything at all on your webserver ?
If not and you are having dedicated server I would recomend fresh install. I ran to this problem once and manually fixing may not be easy... and fresh install could be even faster, if you don't need to format hard drives etc...

---

### Post by timgood on 2010-01-28
Run

sudo dpkg-reconfigure -plow phpmyadmin

in terminal which will take you through the set-up again.

Hope this helps.

---

### Post by john newbuntu on 2010-01-28
If what timgood suggested does not work, edit the file /etc/dbconfig-common/phpmyadmin.conf (using gksudo) and then run "sudo dpkg-reconfigure phpmyadmin"

---

### Post by cariboo on 2010-01-28
Please don't create multiple posts on the same subject. I have merged your two threads.

---

