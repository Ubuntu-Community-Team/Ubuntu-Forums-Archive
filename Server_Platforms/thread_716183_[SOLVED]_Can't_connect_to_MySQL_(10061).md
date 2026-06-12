---
title: "[SOLVED] Can't connect to MySQL (10061)"
date: 2008-03-05
forum: Server Platforms
---

### Post by 47_MasoN_47 on 2008-03-05
Hello,

I'm running MySQL 5.0.45 on Ubuntu 7.10 server edition.  I can login fine as either root or the user account I created from the server itself.  Those users can create tables, etc. just fine.  I want to be able to access the server from WinXP using the ODBC Connector, but every time I try to connect to the server I get error 10061.  I checked some other threads and Googled for the past hour but can't figure out what is wrong.  I cannot telnet to port 3306 either, but the firewall (Firestarter) is supposed to allow incoming connections to everyone on that port.  I can telnet to port 80 which Firestarter also says is open if that means anything.

Thanks, I'm a n00b to MySQL and linux servers in general.

---

### Post by firebadger on 2008-03-05
In /etc/mysql/my.cnf try changing the bind address to your IP address or your hostname (I think that should work too) then restart..
```
sudo /etc/init.d/mysql restart
```

---

### Post by 47_MasoN_47 on 2008-03-05
I read something about the bind-address thing in my.cnf but our server doesn't even have that anywhere.  How would I go about adding one in?

Thanks

EDIT:
I also can't connect to VNC.  I have tried connecting to both VNC and MySQL with Firestarter installed and with it uninstalled through the package manager.  I have rules setup to allow incoming connections on those ports for all IP ranges.  I also have it setup so that my IP is allowed in the host rules section.

---

### Post by firebadger on 2008-03-05
You'll find the my.cnf file in /etc/mysql - you just need to edit it.

---

### Post by 47_MasoN_47 on 2008-03-06
Yeah I found that file, but there's nothing even containing the word "bind" in it.

---

### Post by acidsolution on 2008-03-06
ok so you checked for bind in my.cnf file if it doesnot exist than ok no need of it it is only required when u want to bind it to particular ip
what you do is commment the line 

#skip-external-locking

if bind is present than comment the line 

#bind-address = 127.0.0.1

and than restart your mysql 
now you connect mysql from your localhost simply typing 
mysql -u root -p
and than go to database mysql 
and than to table user 
update the value of host for root by default it is localhost . Change it to % so that it can be accessed from remote machine 
now you may try to connect from remote machine if still the problem persists and if the error is client doesnot support the authentication protocol or some what like that 
than 
type 
mysql> SET PASSWORD FOR root=OLD_PASSWORD('your password');
mysql>FLUSH PRIVILEGES;



now when you try to connect the mysql 

it must work for you 
it worked perfectly for me :)
hope to see your response if any error persists than please post the error in detail.

---

### Post by 47_MasoN_47 on 2008-03-06
> update the value of host for root by default it is localhost . Change it to % so that it can be accessed from remote machine 

How do I do this?  Can you send me the line from your my.conf file so I can compare it to mine?

Thanks a lot for the reply.  Without being able to connect from a remote PC, we have no use for the database.

---

### Post by acidsolution on 2008-03-06
no you cant find the line for updating localhost to % in my.cnf 
you login to mysql in your computer locally first 
and than use following command line argument as shown :-

$ mysql -u root -p
you will be prompted with mysql password type password 

mysql>use mysql;
mysql>update user set Host='%' where User='root' ;
mysql>FLUSH PRIVILEGES;
or if you are using phpMyadmin than you can directly navigate to mysql database and than user table and update the value of locahost to '%'

In my.cnf file you just have to comment those lines thats all the use of my.cnf file to access that

It is better if you use phpMyadmin so that you can visualize what you are doing if you are not sure .

---

### Post by 47_MasoN_47 on 2008-03-07
Thanks, I did what you said and then restarted the server.  I can now add it to the ODBC and pull data from my table into Excel!  One step closer to our goal thanks to you buddy!

---

