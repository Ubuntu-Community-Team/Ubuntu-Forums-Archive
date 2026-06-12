---
title: "mysql not responding to remote-access on ubuntu"
date: 2008-12-11
forum: Server Platforms
---

### Post by abhinav90 on 2008-12-11
I have been trying to remotely connect to my mysql-server hosted on ubuntu but all i get is a long wait after trying to connect,

i found a reason why mysql-server on ubuntu stalls my connection. When i try to remotely try to connect to my server using mysql -u on my desktop after requesting password it keeps waiting forever,

When i checked out my server and typed netstat -tap | grep mysql  i first get:

(No info could be read for "-p": geteuid()=1000 but you should be root.)
tcp        0      0 173-45-231-96.sli:mysql *:*                     LISTEN      -               
tcp        0      0 173-45-231-96.sli:mysql 59.183.1.24:50296       ESTABLISHED

but then it becomes

(No info could be read for "-p": geteuid()=1000 but you should be root.)
tcp        0      0 173-45-231-96.sli:mysql *:*                     LISTEN      -               
tcp        0     66 173-45-231-96.sli:mysql 59.183.1.24:50046       FIN_WAIT1   -               

i think the FIN_WAIT1 is the problem but dont know how to fix this socket problem. What should i do? ? Any input would be appreciated.

---

### Post by mbeach on 2008-12-11
if you are at the terminal on the mysql machine, can you connect run the mysql client successfully?  If so, then perhaps you need to amend the my.cnf file, commenting out the "bind-address" line.  Restart mysql and try again.

---

### Post by mbeach on 2008-12-11
I love it when people double post the same issue.

If as your other thread says, you:
"i checked the files they are almost identical. Only difference is that i have made my bind address equal to my external ip of my server to allow remote connection. Any other solutions in mind ???"

don't make the bind address equal to the ip address of your server.  You also want to make sure that the user you are logging in as can connect from locations other than localhost.

You might want to read over:
[http://dev.mysql.com/doc/refman/5.0/en/adding-users.html](http://dev.mysql.com/doc/refman/5.0/en/adding-users.html)

for the record, this is a continuation of:
[http://ubuntuforums.org/showthread.php?t=1004527](http://ubuntuforums.org/showthread.php?t=1004527)

---

### Post by Sef on 2008-12-11
Duplicate Thread.  Locked.

---

