---
title: "Connecting to mysql"
date: 2005-05-07
forum: Server Platforms
---

### Post by xjimtx on 2005-05-07
Hello out there
Im a web designer who wanted to start dabbling in php and mysql. Somewhat new to linux, Ive been following the Unoffical Ubuntu Starter Guide and installed apache, php and mysql according to the directions. 
My questions are
1) What did this command do when I installed mysql "mysqladmin -u root password db_user_password' ?

2) How do I connect to mysql? Nothing I try while following online tuts is working for me

Jim

---

### Post by xjimtx on 2005-05-08
Well cant find any help to get it runnin using sudo commands so i'll set up a root account so i can follow along with my mysql book

---

### Post by LordHunter317 on 2005-05-08
[QUOTE=xjimtx]1) What did this command do when I installed mysql "mysqladmin -u root password db_user_password' ?[/quote]It set the password for the root mysql user.

> Well cant find any help to get it runnin using sudo commands so i'll set up a root account so i can follow along with my mysql bookPosting a link to the tutorial you're following, what command you ran and what errors it gave would be more helpful, I think.

---

### Post by Sniffer on 2005-05-09
[QUOTE=xjimtx]

2) How do I connect to mysql? Nothing I try while following online tuts is working for me

Jim[/QUOTE]

Did you try to connect to your localhost: 127.0.0.1!!

---

### Post by Ric_ on 2005-05-09
If your connecting to the mysql server from another host, you have to edit

/etc/mysql/my.cnf

about line 47 there is the line 

skip-networking

# this out and the run

/etc/init.d/mysql restart

You will now be able to connect to the DB server from anywhere. You may want to lock this down either using IPTABLES firewall or host.allow.

Hope that helps

---

### Post by xjimtx on 2005-05-09
Thx for the input guys
I didnt setup a root account on my computer (thinking this would solve my problem). I reinstalled mysql and didnt use the "mysqladmin -u root password db_user_password" command, I just logged in as root ($ mysql -u root) then created my root password the way its stated in my book (mysql> set password for root@localhost=password ('your password'); ). And of coarse, 'your password' isnt my actuall password

Jim

---

### Post by LordHunter317 on 2005-05-09
Doing that was completely unnecessary and it's more than possible to do it the way they suggest.  Like I said, had you posted output, we could have helped you through it.

---

### Post by xjimtx on 2005-05-10
LordHunter
Its working fine now, dont think I did anything that was unnecessary (dont know if I was clear on the way I solved the problem).

I dont have the exact error i was getting before but basically the error said root@localhost could not connect to the server.

Part of the problem was not being able to find a explaination for the command "mysqladmin -u root password db_user_password", I know it sets the password, but that doesnt tell me what the password was set at.

So after a fresh reinstall of mysql I followed the instructions on the [mysql website](http://dev.mysql.com/tech-resources/articles/mysql_intro.html#SECTION0003000000) for connecting to the database for the first time and setting the root password and its been running smooth since

But thanks again for the input, I'm sure I'll have more questions when i finish my mysql book and start installing apache and php

---

### Post by LordHunter317 on 2005-05-10
[QUOTE=xjimtx]LordHunter
Its working fine now, dont think I did anything that was unnecessary (dont know if I was clear on the way I solved the problem).[/QUOTE]You enabled the system root account, which is not necessary.

> Part of the problem was not being able to find a explaination for the command "mysqladmin -u root password db_user_password", I know it sets the password, but that doesnt tell me what the password was set at.db_user_password.

---

