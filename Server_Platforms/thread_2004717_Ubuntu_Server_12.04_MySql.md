---
title: "Ubuntu Server 12.04 MySql"
date: 2012-06-16
forum: Server Platforms
---

### Post by brent1975 on 2012-06-16
I recently created a VM to test the stability and to make sure everything is a smooth transition to upgrade from 10.04 to 12.04. I installed apache2 and MySql and imported all my databases and everything was a pretty smooth move. Until last night I went to take a look at some notes that I create using a phpbb forums and got a mysql error. I went to the phpmyadmin site and was getting this error 

```
Connection for controluser as defined in your configuration failed.
```I have done some research on this error and everything that I have read was really old 2009 time frame. Unfortunately I moved everything over to this VM server in preparation to upgrade the main server. and then did a clean install of 12.04. I  did a sudo cp -R /var/lim/mysql /home/brent/mysql  Just incase I need to blow away mysql and rebuild it. 

Naturally that would be last resort.  Anyone have any ideas why I would all of a sudden start getting this error message? It was working fine for a couple of weeks,

---

### Post by N0oki3 on 2012-06-16
try this, might help 
```

vi /etc/mysql/my.cnf

```
find Bind Address = 

Set Bind address to appropriate IP address of server

Restart mysql

---

### Post by brent1975 on 2012-06-16
> **N0oki3 said:**
> try this, might help 
```

vi /etc/mysql/my.cnf

```find Bind Address = 

Set Bind address to appropriate IP address of server

Restart mysql

Thanks, but that is one of the first things I do after i install mysql.

---

### Post by N0oki3 on 2012-06-16
Hmmm...well as you said that you have been checking up to 2009 ?

Have you tried to create new user ?

or this thread, [post #5](http://ubuntuforums.org/showthread.php?t=1152326)

---

### Post by NigelRen on 2012-06-16
Have a look through [http://www.cyberciti.biz/tips/how-do-i-enable-remote-access-to-mysql-database-server.html](http://www.cyberciti.biz/tips/how-do-i-enable-remote-access-to-mysql-database-server.html), especially step #5.

---

### Post by LHammonds on 2012-06-16
I upgraded my database server from the 10.04 server to 12.04 server and it worked (and is working) flawlessly.

My setup is a bit different than most found on the Internet in that I setup my database server as a pure database server.  Wiki and phpbb sites are served from a separate web server.

I did what you did in that I installed a new ubuntu 12.04 server, installed mysql and then exported the database into a single sql file and imported them on the new server.  I then shutdown the old database server and changed the IP on the new server to that of the old server and I was done.

---

### Post by brent1975 on 2012-06-19
Thanks everyone for the help and assistance. I did get it fixed without having to create a new user. I just reinstall mysql-server. I will keep my 10.04 VM running as primary till I feel comfortable that 12.04 is stable enough to migrate too.

again thank you,

Brent

---

