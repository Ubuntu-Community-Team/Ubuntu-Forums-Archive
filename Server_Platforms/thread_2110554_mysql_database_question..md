---
title: "mysql database question."
date: 2013-01-30
forum: Server Platforms
---

### Post by lourendo on 2013-01-30
I am migrating from a paid host to my own personal host.  I am trying to install a forum and cannot seem to connect to my database.  I have 2 virtual hosts on the server right now and i have phpmyadmin installed and working fine so i know it is not a database issue.  i really do not know what i need to do to enable access.  i am assuming that i might need to direct the forum to the precise location of the database.  thank you for your help, louis.

---

### Post by linuxtechguy on 2013-01-30
Just verify your settings are right on your connection string. Make sure you are using localhost as the hostname and port as 3306. Unless you are connecting via a socket file then you would have to verify the path is right. Also make sure no firewall is blocking port 3306 on localhost connections. Make sure there is a line for localhost in /etc/hosts

Test that you can connect with the mysql cli by running the command:

```

mysql -u username -p

```

---

### Post by SeijiSensei on 2013-01-30
> **linuxtechguy said:**
> Test that you can connect with the mysql cli by running the command:

```

mysql -u username -p

```

He needs to connect to a remote server over the network, not localhost.

OP, try adding "-h servername" to the command above.  If you can connect to the database that way, then you can run mysqldump with the same options and extract your database to a plain text file.  That only works if you've given permission to the user 'username'@'%'.  If you only have a user named 'username'@'localhost', you'll have to run the mysqldump program on the server where the database is stored, or add an entry on the server for 'username'@'%'.  Read the MySQL documentation for details.

Once you have a dump file, you can use the mysql client on your local machine to read the dump into your local mysql instance.

---

### Post by lourendo on 2013-02-03
It was actually the opposite of your suggestions.  rather than connecting to my ip i needed to simply connect via localhost since it is all local.   Thanks for guiding me to look in the right direction.

---

