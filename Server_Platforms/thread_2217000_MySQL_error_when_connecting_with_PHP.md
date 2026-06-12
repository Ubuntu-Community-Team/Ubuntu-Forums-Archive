---
title: "MySQL error when connecting with PHP"
date: 2014-04-15
forum: Server Platforms
---

### Post by hungryOrb on 2014-04-15
Hi all,

Running an old 10.04 version of ubuntu server, because I must. It's got LAMP on it. I can access MySQL via MySQL workbench, and queries run nicely (I can also access it from the command line). If I try to connect to the database with PHP though, it fails. This is the error message:

```
Failed to connect to MySQL: Can't connect to MySQL server on '10.4.56.53' (111)
```

Any ideas as to why it's not connecting? I've tried adding another user (via CREATE USER) and that user doesn't work either. 
Here's the actual connection php:

```
<?php

$con=mysqli_connect("10.4.56.53","root","pass","db");
// Check connection
if (mysqli_connect_errno())
  {
  echo "Failed to connect to MySQL: " . mysqli_connect_error();
  }

$result = mysqli_query($con,"SELECT username,password FROM `db`.`users`;");

while($row = mysqli_fetch_array($result))
  {
  echo $row['username'] . " " . $row['password'];
  echo "<br>";
  }

mysqli_close($con);

?>
```

---

### Post by m_duck on 2014-04-15
If MySQL is running on the same machine as the PHP scripts are, try connecting to MySQL on "localhost" rather than "10.4.56.53".

I would have thought, when trying to connect to MySQL with an IP, it will have to have the necessary ports open and listening to accept external connections. If it is on the same machine however, this should not be an issue.

EDIT: Looks like that is right, MySQL probably only listens on localhost/127.0.0.1 by default. To make it accept other connections, it would have to be set up to do so ([reference]("http://stackoverflow.com/questions/1420839/cant-connect-to-mysql-server-error-111")). From a security perspective it is probably best to leave MySQL only listening on localhost unless it is necessary not to.

---

### Post by SeijiSensei on 2014-04-15
Make sure you have the **php5-mysql** package installed and connect to 127.0.0.1.

---

### Post by givecake on 2014-04-15
> **m_duck said:**
> If MySQL is running on the same machine as the PHP scripts are, try connecting to MySQL on "localhost" rather than "10.4.56.53".

I would have thought, when trying to connect to MySQL with an IP, it will have to have the necessary ports open and listening to accept external connections. If it is on the same machine however, this should not be an issue.

EDIT: Looks like that is right, MySQL probably only listens on localhost/127.0.0.1 by default. To make it accept other connections, it would have to be set up to do so ([reference]("http://stackoverflow.com/questions/1420839/cant-connect-to-mysql-server-error-111")). From a security perspective it is probably best to leave MySQL only listening on localhost unless it is necessary not to.

Hey man, thanks. I did fix the binding (by commenting it out), but I'm still getting:

```
[COLOR=#000000][FONT=Times New Roman]Failed to connect to MySQL: Access denied for user 'root'@'10.4.56.53' (using password: YES)[/FONT][/COLOR]
```

The part of my.cnf just before this says:

```

user            = mysqlsocket          = /var/run/mysqld/mysqld.sock
port            = 3306
basedir         = /usr
datadir         = /var/lib/mysql
tmpdir          = /tmp
skip-external-locking

```

That seems right, right?

I had a look at the /etc/apparmor.d/usr.sbin.mysqld file, but it seems to be dealing with just read and write access, which doesn't seem to be the issue here.

---

### Post by SeijiSensei on 2014-04-16
Access denied means that the connection is working as expected, but you probably didn't create a 'root'@'10.4.56.53' account in MySQL.  I suggest creating 'root'@'%' instead.  That uses the SQL wildcard and matches connections by root from any IP.

---

