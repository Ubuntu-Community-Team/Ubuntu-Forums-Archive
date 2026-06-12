---
title: "MySQL user does not show up on User Admisinistration Tool"
date: 2009-07-28
forum: Server Platforms
---

### Post by rainmanxxx on 2009-07-28
I have installed mysql-server. When I run User Administration Tool it only shows my user name (myname) and root. When I want to add mysql user it says that user mysql already exists but it doesn't shown on the User Administration Tool user list why? I checked the user list  
> cat /etc/passwd
and I can see the mysql user. After thanI set up  a home directory for mysql user 
> sudo usermod -d /home/mysql mysql
then I change user to mysql
> sudo -s -u mysql 
after then I want to go to home directory of mysql user.
> cd ~
pwd
it shows /home/myname not /home/mysql
I checked /etc/passwd and it show /home/mysql as a home directory for mysql user. Why it is like that?

---

### Post by rainmanxxx on 2009-07-28
The anwser is at [http://serverfault.com/questions/47015/mysql-user-does-not-show-up-on-user-admisinistration-tool]("http://serverfault.com/questions/47015/mysql-user-does-not-show-up-on-user-admisinistration-tool")

---

