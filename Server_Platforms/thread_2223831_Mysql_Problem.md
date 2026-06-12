---
title: "Mysql Problem"
date: 2014-05-13
forum: Server Platforms
---

### Post by andrea30 on 2014-05-13
Today i wanted to install the automysqlbackup package.
The installation went fine.


When i run it, i get this error:
ERROR 1045 (28000): Access denied for user 'debian-sys-maint'@'localhost' (using password: YES)




So, i tried to connect to mysql server in order to give full privileges  to the debian-sys-maint user.
Then i logged into the mysql server with mysql -u root -p command, but when i try to execute the following command:
GRANT ALL PRIVILEGES ON *.* TO 'debian-sys-maint'@'localhost' IDENTIFIED BY 'secret';


i get this error:
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)


But i'm executing the command as root logged into the console.
Some idea?

---

### Post by slickymaster on 2014-05-13
Hi andrea30, welcome to the forums.

Debian has a MySQL account debian-sys-maint used for switching on/off and checking status. The password for that user should be the same as stored in **/etc/mysql/debian.cnf**.

The file looks like this:```
# Automatically generated for Debian scripts. DO NOT TOUCH!
[client]
host     = localhost
user     = debian-sys-maint
password = <password>
socket   = /var/run/mysqld/mysqld.sock
[mysql_upgrade]
host     = localhost
user     = debian-sys-maint
password = <password>
socket   = /var/run/mysqld/mysqld.sock
basedir  = /usr
```
If the password doesn't match (for example because you changed it manually) the init script won't work anymore. You should set the password according to the file. So:
```
mysql -u root -p
# Then type MySQL root password
GRANT ALL PRIVILEGES ON *.* TO 'debian-sys-maint'@'localhost' IDENTIFIED BY '<password>';
```

---

### Post by andrea30 on 2014-05-19
Many thanks slickymaster,

I've solved my problem assigning manually full privileges db by db and it worked, except for the mysql database.
I dont know why, but seems that i cant give privileges to other account with root account to others.

Fortunatly, the mysql db in my context is not important.

---

