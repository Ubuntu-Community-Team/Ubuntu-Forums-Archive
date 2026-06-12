---
title: "MySQL connection issues"
date: 2006-12-11
forum: Server Platforms
---

### Post by DrNick on 2006-12-11
Hi all

I've been having problems connecting to my newly installed ubuntu server box with MySQL. I have not changed the default firewall rules (i.e. none), and I can connect to the machine's FTP, www and ssh services with no problems, which makes me think it is not a firewall issue.

I have performed all the usual post-installation steps, i.e. ran 'mysql_install_db' to initialise the grant tables using the mysql user. I have checked the permissions of the files in /var/lib/mysql/ to verify they are owned by the mysql user. I have verified the server is running (ps aux | grep mysqld).  Lastly, I have created the appropriate root user for the workstation I wish to admin MySQL from, and followed the creation of this user with a 'FLUSH PRIVILEGES', just to be sure.

Displaying the contents of the mysql.user table reveals that the new user has definitely been created. (I have checked this by displaying the 'Host' column to verify that both the local and remote root accounts are there). Also DNS resolves  the hostname to the IP address fine, (it can ping the host fine and also other services work with no problems using the hostname.)

I am trying to connect to the SQL server with the MySQL GUI tools from a Windows client, on the default port (3306), with my newly created root user. On attempting to connect, a MySQL error number 2003 appears, stating it cannot connect to the MySQL instance. Reading the error page for error 2003 has given me no joy.

Apologies for the rather lengthy post, but I wanted to include as much relevant information as possible. In summary, its not a firewall issue, its not a DNS issue, its not a permissions issue, its not because the server isn't running, and its not because the user accounts haven't been set up. So I've ran out of ideas... anything else anyone could suggest would be very much appreciated.

Cheers,
Tom Byrne

---

### Post by Terryj1974 on 2006-12-11
Are you only having connectivity issues coming from the Windows box, or does it happen when you sign on locally?

I have a few ideas as to what it might be, but need just a little more information.

TJ

---

### Post by Wallace on 2006-12-11
Have you checked to see what IP MySQL is bound to? By default, it only binds to 127.0.0.1. To make it bind to a network IP, edit the /etc/mysql/my.cnf file and edit the bind-address (or comment it out to bind to everything).

---

### Post by DrNick on 2006-12-12
Thanks you for both your replies. The problem was the bind address in the config file... I wasn't aware this was now the default! It probably did say something about it on the error page for error 2003 and I probably missed it, but anyway all fixed now!

---

### Post by amgra on 2006-12-15
> **Wallace said:**
> Have you checked to see what IP MySQL is bound to? By default, it only binds to 127.0.0.1. To make it bind to a network IP, edit the /etc/mysql/my.cnf file and edit the bind-address (or comment it out to bind to everything).

It took me 3 hours reading forums to realize this, I installed Ubuntu server version, I could connect in the server (localhost) after setting the new password for root as in the manual said, but quen I tried to connect from other computer with mysql tols (browser,admin) I just got the 2003 error with 10061 error message, after as I mentioned 3 hours reading, found that in /etc/mysql/my.cnf there was this freaking line 

**bind-address 127.0.0.1**

I just commented it and my windows mysql browser connected !!!! 8)

---

### Post by ArieM on 2007-12-21
> **Wallace said:**
> Have you checked to see what IP MySQL is bound to? By default, it only binds to 127.0.0.1. To make it bind to a network IP, edit the /etc/mysql/my.cnf file and edit the bind-address (or comment it out to bind to everything).

Many thanks

---

### Post by ndmaque on 2007-12-24
thanks m8 

i set the bind to the ipaddress of the server 192.168.2.10 and restarted the sql server ... ta-da it connected first time,

linux newb :-)

---

### Post by TurboRush on 2007-12-24
After 3 days of playing with MySQL on and off, this finally fixed my issue with MySQL failing on startup.

---

