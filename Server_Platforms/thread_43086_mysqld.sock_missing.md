---
title: "mysqld.sock missing"
date: 2005-06-20
forum: Server Platforms
---

### Post by c0ldfyr3 on 2005-06-20
Warning: mysql_connect(): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
i get this error no mater where the socket is told to go. ther is nothing in the mysqld folder nore in the postgresql folder, i am new to linux, but i have leared a lot in tha past few months, i have installed php4, and mysql through synaptic, and some tutorials form the ubuntulinux forums.
my phpinfo for mysql looks like this ```
MySQL Support	enabled
Active Persistent Links 	0
Active Links 	0
Client API version 	3.23.56
MYSQL_MODULE_TYPE 	external
MYSQL_SOCKET 	/var/run/mysqld/mysqld.sock
MYSQL_INCLUDE 	-I/usr/include/mysql
MYSQL_LIBS 	-L/usr/lib -lmysqlclient

```

if i could have you look at it i would, but i am not sure how to link my router to the apache server.

---

### Post by antwerx on 2005-06-20
Hello - I am not quite sure about your specific problem. 

But, most MySQL connect errors are due to the MySQL username/password/server combo in the config.

What MySQL /PHP app are you attempting to install and use?

 :)

---

### Post by LordHunter317 on 2005-06-20
That error most likely means the MySQL daemon isn't running.  Did you check to see if it is?

---

### Post by c0ldfyr3 on 2005-06-20
its not even running in the background. I searched through the "var/run/" folder and i see no mysqld.sock i did a search with root and found nothing. though synaptic says its installed.

---

### Post by LordHunter317 on 2005-06-20
You have to start the mysql daemon...:```
sudo /etc/init.d/mysql start
```

---

### Post by c0ldfyr3 on 2005-06-20
command not found.
i will try to reinstall the app and see it that helps.

---

### Post by LordHunter317 on 2005-06-21
You don't have the server portion installed then, which is in a seperate package.

---

