---
title: "Problem: mysql create users.."
date: 2008-07-01
forum: Server Platforms
---

### Post by ChriZathens on 2008-07-01
Hello to everybody! :D
I'm facing a problem and I don't know how to resolve it..:
A while ago I had installed Ubuntu 7.10 Server in an old P3 PC on a 20 GB hard disk.
But 20 gb apparently were not enough (had also torrentflux installed), so I decided to copy my disk to a larger one that I had (80GB) and extend the root partition.
At the end I realized that this procedure is not so certain to have successful results, especially if you are not an advanced user:).
So the 20 gb was messed up and decided to perform a new installation using 8.04 server.
After finishing installation (LAMP with SSH and FTP server) I also installed phpmyadmin and webmin. And now the problem begins:
In my old installation If I wanted to install a testing forum, or torrentflux I was going to Webmin-->Servers-->Mysql server-->User permissions-->create new user.
I was entering the username, then a password, usually assign permissions for all hosts and so, I had a new user with a password which I could use in any installation.
But now, this does not seem to work. The user is created OK with a password, but no web installation will accept the new user's credentials to connect to the database :(
The only user that is allowed to connect is root with his password.
I tested this using Joomla, Torrentflux and phpbb. They all need root user to connect - every other user I create can not connect regardless if they have a password or not.

What is wrong? Any help please? I don't want to always use the root's username and pass for every installation I make. I'd like to have different users and passwords for every different installation, as I used to.. If someone could point me to the correct direction, I would really appreciate it.
Thanks in advance,
Chris

---

### Post by ChriZathens on 2008-07-09
Nobody? :(

---

### Post by windependence on 2008-07-09
This is why you should learn the command line. Even tools like Webmin don't always work like they should. They are just front ends for the actual configuration files anyway. You really should learn how to create users from the command line in MySQL.

You must also grant users permission on the database. I know phpBB has specific instructions for this. You also have to make sure the files and directories have the correct permissions.

[http://www.debuntu.org/how-to-create-a-mysql-database-and-set-privileges-to-a-user](http://www.debuntu.org/how-to-create-a-mysql-database-and-set-privileges-to-a-user)

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

-Tim

---

