---
title: "Ubuntu Mate 16.04 beta, error after software update: Unit mysql.service is masked"
date: 2016-04-07
forum: Ubuntu Development Version
---

### Post by aaron126 on 2016-04-07
Hi there.

I have installed Ubuntu Mate 16.04 beta 2, and all was well. This morning I ran a software update. I was prompted to confirm a partial update, which I confirmed, and now I am having a problem with mysql.

After a restart, when I try and use phpmyadmin I get this error:

   ***#2002 - No such file or directory<br />The server is not  responding (or the local server's socket is not correctly configured).***

In the terminal I attempted to restart mysql:

[B][I]   $ sudo service mysql start
   Failed to start mysql.service: Unit mysql.service is masked.
[/I][/B]
So I'm guessing something is now broken with mysql, and I am currently trying to fix things.

Has anyone else had this problem? Is there a quick fix?


Thanks in advance for any help,
Aaron

---

### Post by aaron126 on 2016-04-07
I'm slightly confused, but things seem to be fixed ...


After messing about with lots of different stuff, it appears mysql-server wasn't installed (properly) any more. I eventually did this and it worked:

       ***sudo apt-get install mysql-server***

It found all my existing configuration and databases.

Explanation? I don't know. I'm moving on.


I hope this helps someone. Cheers,
Aaron

---

### Post by ajgreeny on 2016-04-07
Please mark as SOLVED from the Thread Tools menu up top.

---

