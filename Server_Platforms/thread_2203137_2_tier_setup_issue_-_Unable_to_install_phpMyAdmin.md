---
title: "2 tier setup issue - Unable to install phpMyAdmin"
date: 2014-02-01
forum: Server Platforms
---

### Post by Max_Shafiq on 2014-02-01
Hi Guys

I am newbie on this forum and a newbie to ubuntu. 

I have been trying to setup a 2 tier web application (Server 1) and database (Server 2) setup.

On server 1 (web app server), I am able to install Apache, PHP. These both check out OK by running a simple phpinfo script.

I then proceed to my second server and install MySQL. It appears to be installed just fine.

As a final step I go back (ssh) to Server 1 and install PhpMyAdmin. This is where the issue is starting. When I run the  

apt-get install phpmyadmin I get the following error: [FONT=Menlo]ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)[/FONT]

[FONT=Menlo]Given that the Server 2 (MYSQL) is on a separate subnet 11.22.33.44 (<- made up number), I proceeded to update the bind command in /etc/mysql/my.cnf on Server 1 (this is there the apache and php lives, and I was trying to install phpmyadmin, BUT NOT where MySQL lives).

I swapped out localhost for 11.22.33.44 for the bind-address. Restarted Apache but I still get the same error when I try to install phpmyadmin.

I am guessing at this stage that I need to add the IP of Server 2 to some additional config files, but have no idea which.

Any help/direction would be greatly appreciated.

[/FONT]

---

### Post by Max_Shafiq on 2014-02-01
Surely this is not that hard is it? :-)

Any help appreciated ...

---

### Post by Max_Shafiq on 2014-02-02
One more observation. There is a /etc/mysql/my.cnf installed on both the servers!

I had updated the bind address on server 1 (Apache/PhP/MyPhpAdmin) and not on Server 2 (MySQL only).

Is it normal to have it on both servers? or did I do a wrong step somewhere?

---

### Post by SeijiSensei on 2014-02-03
I believe a default Ubuntu MySQL installation binds the server to the localhost (127.0.0.1) interface.  Look in my.cnf on the *server* and add a hash mark to the beginning of the bind-address directive like this:
```
#bind-address = 127.0.0.1
```
then restart MySQL. You'll need to use sudo to edit my.cnf, of course.  That will tell MySQL to use its default of listening on all interfaces.

---

