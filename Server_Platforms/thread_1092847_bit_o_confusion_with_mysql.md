---
title: "bit o confusion with mysql"
date: 2009-03-10
forum: Server Platforms
---

### Post by brook adams on 2009-03-10
Hi Folks,

I used tasksel to install LAMP on my dell mini 9. After the install I tried out apache by going to localhost in my browser and it worked fine. I then put a little php script in www/var to test php and that went fine too. Then I opened a terminal and tried to start mysql and I got this error:

Can't connect to local MySql server through socket '/var/run/mysqld/mysqld.sock' (2)

Okay... so I went to /var/run and discover that there is no mysqld in that directory. I found a posting in help.ubuntu.com that explained about changing settings in /etc/mysql/my.cnf, so I went there and I see the variable called 'socket' equals my old friend /var/run/mysqld/mysqld.sock

This little adventure suggests to me that I should change this variable in this file but to What? If anyone has an idea, please lemme know.

---

### Post by Iowan on 2009-03-10
My server has the same value in the socket variable... but it also has a /var/run/mysqld directory (inside that directory is mysqld.pid and the aforementioned mysqld.sock).  Also, /etc/mysql/my.cnf mentions editing /etc/mysql/debian.cnf when changing socket location.

---

### Post by brook adams on 2009-03-11
hey you're right...

I went another nmachine that's running all the server stuff just fine and see that it has that directory but it refuses to be copied over to the little mo-sheen.

I'm thinkin' it may be time to leave the world of apt-get and learn to compile my own programs. eek.

---

