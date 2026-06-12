---
title: "mod_chroot + LAMP server"
date: 2007-04-24
forum: Server Platforms
---

### Post by b0red on 2007-04-24
Ahh jeez,
it's been a tough last couple of days.......

I've been installing mod_chroot on a LAMP server. 

Chrooting apache and PHP is not a problem, the issue is MySQL, Once I get it running I can't connect to the backend database.

I have done this so far...

> 
# mkdir -p /var/www/var/run
# chown -R root.root /var/www/var/run

# nano /etc/apache2/httpd.conf:

PidFile /var/run/httpd.pid
ChrootDir /var/www
DocumentRoot /

# ln -s /var/www/var/run/httpd.pid /var/run/httpd.pid


I have also edited php.ini to make sure open_basedir is also correct.

I then did this:
> 
cd /var/chroot/apache/var/run
mkdir mysqld
chown mysql:mysql /var/chroot/apache/var/run/mysqld


then
> 

nano /etc/mysql/my.cnf
[client]
socket = /var/www/var/run/mysqld/mysqld.sock

[server]
socket = /var/www/var/run/mysqld/mysqld.sock
/etc/init.d/mysql restart

nano /root/.bashrc
alias mysql="mysql -S /var/chroot/apache/var/run/mysqld/mysqld.sock"


To allow apache to connect to MySQl from a file wihtin the jail. However MySQL choked and died.

Can anyone shine a light on this?

---

### Post by gaten on 2007-04-24
[http://www.securityfocus.com/infocus/1726](http://www.securityfocus.com/infocus/1726)

Check out that article. You'll have to change some stuff, and you don't really need to build mysql from source (although it makes chrooting it alot easier). It's old, but chrooting really hasn't changed in the past 4 years.

---

