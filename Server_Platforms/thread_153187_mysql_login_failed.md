---
title: "mysql login failed????"
date: 2006-03-31
forum: Server Platforms
---

### Post by mEtho on 2006-03-31
[FONT="Book Antiqua"]hello, how are you!!!

i would be more then happy if any of you could solve 'mysql' problem for me!!

the following is the result when i try to login, i dont know why i am getting the error!!!

> root@ubuntu:/home/metho# /usr/local/mysql/bin/mysql
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)


i use this[https://wiki.ubuntu.com/MYSQL5FromSource]("https://wiki.ubuntu.com/MYSQL5FromSource") guide to install the mysql server, installation worked fine but i made one change, which could be the main cause of this problem. 

i changed this following line
/usr/local/mysql/bin/mysqladmin -u root password new_password
with this line
/usr/local/mysql/bin/mysqladmin -u root password 123

i assumed the new_password is where u put new password so i just put 123, i dont know if thats the cause of the problem!!!

-mEtho[/FONT]

---

### Post by opus on 2006-03-31
when you use the mysql client, you need to use the following command:
```
mysql -u root -p
```
It will then prompt you for a password.

Aaron

---

### Post by mEtho on 2006-03-31
[QUOTE=opus]when you use the mysql client, you need to use the following command:
```
mysql -u root -p
```
It will then prompt you for a password.

Aaron[/QUOTE]


hello
thanks for the reply but for some reasons that command didnt work!!!

> root@ubuntu:/home/metho# mysql -u root -p
bash: mysql: command not found
root@ubuntu:/home/metho#


---

### Post by opus on 2006-04-01
Try
```
/usr/local/mysql/bin/mysql -u root -p
```
You may not have /usr/local/mysql/bin in your path so you have to fully qualify the command.  Did you install via apt or is this a custom mysql install?

Aaron

---

