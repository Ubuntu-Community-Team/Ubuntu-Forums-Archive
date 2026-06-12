---
title: "mysql error on new 9.10 server install"
date: 2010-02-13
forum: Server Platforms
---

### Post by CCG121 on 2010-02-13
I just installed ubuntu 9.10 Server on to my acer laptop that I have been using as a server with the desktop version and when trying to upgrade packages it says 

stopping mysql database server mysqld
 then it tries to start it and fails then it gives me a 
invoke-rc.d: initscript mysql, action "start" failed 
then it gives me a dpkg: error processing mysql-server-5.1 (--configure): 
then subprocess installed post-installation script returned error exit status 1 
then dpkg: dependency problems prevent configuration of mysql server  
then mysql-server depends on mysql-server-5.1; however package mysql-server-5.1 is not configured yet  
then dpkg: error processing mysql-server (--configure): dependency problems - leaving unconfigured 
then a line about this being a previous failure 
then Errors were encountered while processing
then mysql-server-5.1
then mysql-server
then e: sub-process /usr/bin/dpkg returned an error code (1)

Can anyone tell me what i need to do to fix this? sory if this has already been posted i tried multiple things i found and none of them seem to fix my problem

---

### Post by Bachstelze on 2010-02-13
Try starting it manually to see if you have a more helpful error message:

```
sudo /etc/init.d/mysql start
```

---

### Post by CCG121 on 2010-02-13
When i try that i get [fail] in red and it goes to the next line asking me for a command.

---

