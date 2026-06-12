---
title: "Mysql"
date: 2006-03-11
forum: Server Platforms
---

### Post by etiennemula on 2006-03-11
Hi to all , 
I am new to the UBuntu and Linux system and i have a problem setting up an mail server , i was reading this website which i have found which is good [http://flurdy.com/docs/postfix/index.html](http://flurdy.com/docs/postfix/index.html) but when i am triying to create new users in Mysql the terminal gives out this error 

 connect to server at 'localhost' failed
error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
 
Infact this file doesn't even exists

Please help me out

---

### Post by Koybe on 2006-03-11
What if you :
```
sudo /etc/init.d/mysql restart
```
and (using root mysql password) :
```
sudo mysql -u root -p
```

You need to give us more details if you want help. ;-)

---

