---
title: "Creating MySQL database on a VPS"
date: 2011-02-27
forum: Server Platforms
---

### Post by dz93 on 2011-02-27
I need help getting this going. I already installed mysql using sudo apt-get install mysql but I can't figure out how to set up a database. Can anyone point me in the right direction please?

---

### Post by Vegan on 2011-02-27
```
sudo mysql -u root -p
```

enter your password
```

create database mydatabase;
```

This will create the database, use a suitable name for the database name.

Next will need to grant permissions


you best bet is to read the manual on MYSQL as permissions ca be a tad tricky

---

### Post by dz93 on 2011-02-27
I'm a beginner to this whole database thing using terminal commands so it'd be awesome if someone could kinda walk me through it. What would you enter if you wanted to create a database.
That create database command you gave me is only one step of the whole thing. Won't I need to set a username and password for the database etc?

---

### Post by t3r0 on 2011-02-28
Hello,


Running apt-get install mysql will not install the mysql server software, but the mysql client insted..

To install the mysql server run following:

```

$ sudo apt-get install mysql-server

```

The installation process will ask for mysql root password.

After that is finished, you should be able to connect to the mysql server with the mysql-command:

```

$ mysql -uroot -p

```
This starts the mysql command line client with the mysql root user and the blank -p option will tell the mysql-client to promt for the password. Enter the same password when prompted that you used in the mysql server installation. After that the mysql client should establish a connection to the mysql server and you'll be shown a mysql prompt. eg:

```

Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 243
Server version: 5.1.49-1ubuntu8.1 (Ubuntu)

Copyright (c) 2000, 2010, Oracle and/or its affiliates. All rights reserved.
This software comes with ABSOLUTELY NO WARRANTY. This is free software,
and you are welcome to modify and redistribute it under the GPL v2 license

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql> 

```

Every command you type here are standard mysql commands. So to create new database enter:

```

mysql> create database my_new_database;

```

And to create new user who can access that database:

```

mysql> grant all on my_new_database.* to new_user@localhost identified by 'my secret password';
mysql> flush privileges;

```

To exit from the mysql client close the connection with
```

mysql> quit

```

Now you can test the new user just like you first connection to the mysql with the root user, just replace the -uroot with -unew_user.. 


- Tero

---

