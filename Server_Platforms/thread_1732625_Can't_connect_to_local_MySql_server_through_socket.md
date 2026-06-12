---
title: "Can't connect to local MySql server through socket '/var/run/mysqld/mysqld.sock' (2)"
date: 2011-04-18
forum: Server Platforms
---

### Post by thoufiq on 2011-04-18
Hi All,
        I am very very new to linux and installing mysql server manually. i have successfully installed mysql server but when i am try to create database, it shows error like this

[COLOR=Red]ERROR 2002 (HY000): Can't connect to local MySql server through socket '/var/run/mysqld/mysqld.sock' (2)
[/COLOR]
[COLOR=Magenta]**[/COLOR] mysqld is not available in /var/run  and  error log file is also not available in /var/log [COLOR=Magenta]**[/COLOR]

Any suggestions will be appreciated....

Thanks

---

### Post by kimda on 2011-04-18
Maybe its not running? Enter the following command to start the mysql server: 

sudo service mysql start

---

### Post by usatonycuba on 2011-04-18
> **thoufiq said:**
> Hi All,
        I am very very new to linux and installing mysql server manually. i have successfully installed mysql server but when i am try to create database, it shows error like this

[COLOR=Red]ERROR 2002 (HY000): Can't connect to local MySql server through socket '/var/run/mysqld/mysqld.sock' (2)
[/COLOR]
[COLOR=Magenta]**[/COLOR] mysqld is not available in /var/run  and  error log file is also not available in /var/log [COLOR=Magenta]**[/COLOR]

Any suggestions will be appreciated....

Thanks
That type of error usually means that there is NOT a MySQL server running on the system or you are specifying a Unix socket file or port number TCP / IP when attempting to connect to the server.
> **kimda said:**
> Maybe its not running? Enter the following command to start the mysql server: 

sudo service mysql start
+ 1

---

### Post by thoufiq on 2011-04-19
> **kimda said:**
> Maybe its not running? Enter the following command to start the mysql server: 

sudo service mysql start


Hello Kimda,
                         Thanks for your suggestion. Anyway when using [COLOR=Magenta]sudo service mysql start[COLOR=Black],[/COLOR][/COLOR] it shows like this

[COLOR=Red]root@dhcppc4:~# sudo service start
mysql : unrecognized sevice[/COLOR]

Also can u pls briefly explain kimda, why [COLOR=Magenta]log file [COLOR=Black]and[/COLOR] mysqld[/COLOR] is not present  in [COLOR=Magenta]var/log/... and var/run/...[/COLOR]

---

### Post by kimda on 2011-04-19
Whats the output of: dpkg -l | grep mysql ?  Looks like there is no mysql-server installed. If theres no mysql-server in the list you can install it with the following command: 
sudo apt-get install mysql-server

---

### Post by usatonycuba on 2011-04-19
Using a [COLOR="Sienna"]ps[/COLOR] we can see if that parameter can specified where is the location of our MySQL socket:

```
ps -fea | grep mysqld
```

If not found as a parameter .. we should look at the section [COLOR="DarkRed"]mysqld/etc/my.cnf[/COLOR] to find the parameter by typing:
```
grep socket /etc/my.cnf
```
If you already know (find) where the socket is ... we must modify this same file ([COLOR="DarkRed"]/etc/my.cnf[/COLOR]) and add the parameter section client socket.. it will be something like:
```
[client]
default-character-set=utf8
socket=/var/lib/mysql/mysql.sock
```

Where  [COLOR="DarkRed"]/var/lib/mysql/[/COLOR]  is the location where we found our [COLOR="DarkRed"]mysql.sock[/COLOR] , from the   [COLOR="DarkRed"]ps[/COLOR] and/or [COLOR="DarkRed"]grep[/COLOR] commands..

I hope that this helps.. GL

PD:

It sometimes happens that (in that particular problem).. that we make install  (setting up) the MySQL client ..instead of MySQL Server

---

### Post by elnaw on 2013-02-01
Hi guys!
Since this is the only thread that is tuckling this issue it would be grate if I could get some help with my problem. I have the same problem in ubuntu 10.10 server with ispconfig, mail, web server the machine is been working fine for a long time but recently I started to get this mysql error accessing the website and at the same time will have a postfix imap error. Reloading the page will help but it's annoying and I don't why it keeps on happening
Your help is highly appreciated.
Elnaw

---

