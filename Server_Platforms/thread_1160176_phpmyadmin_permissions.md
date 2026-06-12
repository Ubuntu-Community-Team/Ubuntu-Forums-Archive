---
title: "phpmyadmin permissions?"
date: 2009-05-15
forum: Server Platforms
---

### Post by pstrbrc on 2009-05-15
I have a web server (Ubuntu server 8.04, LAMP) that I'm having fits getting my data bases functioning, am working toward running some typo3-based web pages. So, when I loaded MySQL I didn't give a new password, so I can sign in on "root", but then I don't have any privileges. 

[screen shot of phpMyadmin]("http://s129.photobucket.com/albums/p232/pstrbrc/server/?action=view&current=phpmyadmin1.jpg")

What am I missing? 
Now, I have access to the server, so I can use vi editor to fix this, but I don't have a clue what file to go to, or what to change. And I can't find any help in the online MySQL reference manual.

---

### Post by trentscott4 on 2009-05-15
I've run into this too and used the steps below from 'fredanthony' on this forum:

> I know this is old but I recently ran into this issue. Here is how I resolved it:

1) Stop mysql:

Quote:
$ /etc/init.d/mysql stop  

2) Make sure that all of the MySQL processes are actually stopped or killed. You can check for running MySQL processes with this command:


Quote:
$ ps waux  

3) If any MySQL processes are still running, they will look similar to the following:


Quote:
2102 32523 ... /bin/sh /usr/local/mysql/bin/safe_mysqld ...
2102 32557 ... /usr/local/mysql/libexec/mysqld --basedir= ...  

You can kill the processes with the kill command(Note: The second column is the Process ID or PID):


Quote:
kill -9 32523  

4) Restart mysql with --skip-grant-tables: 

Quote:
$ /usr/bin/mysqld_safe --skip-grant-tables  

5) Open a new seesion, leave the other open as well, in the new session:

Quote:
$ /usr/bin/mysql  

6) This should get you in, now:

Quote:
use mysql;  

7) Once you are using the mysql database, run the following:

Quote:
UPDATE user SET Password=PASSWORD('YOUR_PASSWORD_HERE') 
WHERE Host='localhost' AND User='root';  

 now quit out with quit; and then restart mysql:

Quote:
$ /etc/init.d/mysql restart  

Thats it, you should now be logged in.

---

