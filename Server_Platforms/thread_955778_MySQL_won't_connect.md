---
title: "MySQL won't connect"
date: 2008-10-22
forum: Server Platforms
---

### Post by Zespris on 2008-10-22
Hi, I updated recently to 8.04LTS, and tried to install Joomla!, it said it would not connect to MySQL. Then I tried to install SMF, and it said the following:

Client does not support authentication protocol requested by server; consider upgrading MySQL client

I'm currently using packages mysql-client-5.0 and mysql-server-5.0, any ideas? It just seemed to work before...

---

### Post by ajwak95 on 2008-10-22
have you tried using PHPMyAdmin? If you are, then try to reboot the machine. If you aren't try doing sudo apt-get install phpmyadmin, and follow some instructions online, just google "PHPMyAdmin on ubuntu Server with apache2".

---

### Post by cariboo on 2008-10-22
Have you set up users to connect to mysql? Can you access the mysql console in a terminal? Using the user you set during mysql installation, try in a terminal:

```
mysql -u root -p
```

you should get an output like this:

```
 mysql -u root -p
Enter password: 
Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 663
Server version: 5.0.51a-3ubuntu5.1 (Ubuntu)

Type 'help;' or '\h' for help. Type '\c' to clear the buffer.

mysql>
```

If you can't connect, you may have to set your root password again. the easiest way is to run in a terminal:

```
sudo dpkg-reconfigure mysql-server-5.0
```

Jim

---

