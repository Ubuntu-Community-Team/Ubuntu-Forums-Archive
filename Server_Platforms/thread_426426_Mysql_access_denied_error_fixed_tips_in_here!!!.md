---
title: "Mysql access denied error fixed tips in here!!!"
date: 2007-04-28
forum: Server Platforms
---

### Post by hockey97 on 2007-04-28
Hi I got mysql working I knew what was wrong so I thought I should share my experience with you guy's.

Well here are the steps hope this helps people that have problems with mysql on access denied at localhost ect

first stop the server  /etc/init.d/mysql stop 

second start the mysqld
and it locate depends on how you installed the mysql (rpm or compile)
but it's usually locate in /usr/sbin/
so your command is
/usr/sbin/mysqld --skip-grant-tables  
when you do that get out of terminal and open a new one 

get into mysql by typeing  mysql -u root -p and then enter password when prompted.

then type this

[update mysql.user set password = PASSWORD('newpass')
-> where user = 'root';
\q ]
 in between [] don't add the [ ] things that just show that all code in between [] you type.
where PASSWORD('newpass")  is where you put the new name.

the /q should quit the session 

then type

mysqladmin shutdown 
or any way you think would shutdown mysqladmin maybe in the /usr dir area.


then shutdown mysql again, by /etc/init.d/mysql stop
then start it up  by /etc/init.d/mysql start

now if you have webmin then the next part would be easy. 

in webmin go to mysql area it will still show the error access denied don't worry go and click the config link
 in their change the admin user sometime it gives you or uses your user name type in root

and then save .  If you don't have webmin you can do this same step in mysql config file 

by default it's at  /etc/mysql/my.cnf

in that file also comment out the bind = 127.0.0.1

this cleared up my problem my mysql server is up and running and webmin does the rest.
finaly happy to fix this spent 4 weeks on this lol.

---

