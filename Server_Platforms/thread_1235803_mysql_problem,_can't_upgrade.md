---
title: "mysql problem, can't upgrade"
date: 2009-08-09
forum: Server Platforms
---

### Post by rompstar on 2009-08-09
I can't seem to be able to log into my mysql client session, I am on the local server and I have the right password to the root and everything and it is not working:

I can't seem to upgrade:

raymond@dragonfly:~$ uname -a
Linux dragonfly 2.6.28-14-server #47-Ubuntu SMP Sat Jul 25 01:18:34 UTC 2009 i686 GNU/Linux

raymond@dragonfly:~$ mysql -u root -p
Enter password: 
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)
raymond@dragonfly:~$ 

I can't even log in to change this password problem...

Hello ?

Can anyone help ?

Right now I think the database is running in safe-mode and I can't even stop it... gives me the same error as above. :confused:

---

### Post by chrisdee on 2009-08-09
If I remember correctly you have to set root password for mysql first :

1) Login to mysql by writing : mysql
2) Then write : update user set password=password("new_password") where user="root";
3) Finally write : flush privileges;


Did this work for you ?

---

### Post by cariboo on 2009-08-09
[This]("http://www.digitalpeer.com/id/lost") may help you with your password problem, I've used it sucessfully myself.

---

### Post by rompstar on 2009-08-09
I can't seem to connect to mysql at all.


root@dragonfly:/tmp/orbit-root# mysql
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)


root@dragonfly:/tmp/orbit-root# mysql -p
Enter password: 
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)
root@dragonfly:/tmp/orbit-root#

---

### Post by rompstar on 2009-08-09
Ok, this worked for me, posting incase others have same problems...

First stop mysql:

for i in `ps -ef |grep mysqld |awk '{print $2}'`; do `kill -9 $i`; done

Then:

/usr/bin/mysqld_safe --skip-grant-tables &

mysql -h localhost
use mysql
update user set password = password('passwordhere...') where user = 'root' and host='localhost';

quit

restart command and it should work, then I did the update and everything worked, hooray!

Thanks guys!!!!

---

### Post by chrisdee on 2009-08-10
Good to hear it works. But i think you can stop mysql easier by writing : /etc/init.d/mysql stop

---

