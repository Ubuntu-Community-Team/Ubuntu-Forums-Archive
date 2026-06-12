---
title: "Setting up a MySQL server with remote connection to the Database"
date: 2008-01-07
forum: Server Platforms
---

### Post by CitroenC4 on 2008-01-07
I have been asked to setup a server to host a MySQL database for an organization I belong to. Someone in the group has written an application with visual basic to act as the front end to a MS SQL database. What he wants is to have have this database sitting on a server that has a static IP and to be able to make the connection stings from his front end to connect back to the remote server. I suggested we use MySQL if his database will run OK as I don't want to have to run a Microsoft operating system on the server. So my question is (I am sorry but I have little database experience) how is the best way to setup MySQL so the connection strings from this guys front end will talk back to the server?

---

### Post by Chayak on 2008-01-07
When you install MySQL the default port it works on is 3306.  If you set the server up with a static IP and don't block that port with a firewall he should be able to connect to the database.

[http://dev.mysql.com/doc/refman/5.1/en/index.html]("http://dev.mysql.com/doc/refman/5.1/en/index.html")

That should tell you what you need to know to check the configs.  If you still can't figure it out there is a link to the MySQL forums on which they eat, sleep, and breathe MySQL.  If anyone they can help you.

---

### Post by k_grdn on 2008-01-07
Hi,

You need to change the bind address (listens on localhost by default):

/etc/mysql/my.cnf 
bind-address            = 192.168.1.100

....................And assign user rights to the database:

GRANT ALL ON database.* TO bar@'remote-address' IDENTIFIED BY 'PASSWORD';

Regards,

k_grdn

---

### Post by koenn on 2008-01-07
If your friend is using Visual basic, he's probably thinking about ADODB Connections.  I don't know if there are any generic ADODB connection providers for MySQL in VB, but you can do it with the ODBC driver you can get at the mysql website. This needs to be installed on the system where the VB application is running. 
You can set up an ODBC connection and your application can use that, or you can define the connection in the application, something like

```
	Set Conn = CreateObject("ADODB.Connection")
	
	'make the connection
	conn.Open "Driver={MySQL ODBC 3.51 Driver};Server=192.168.10.20;Port=3306;Database=dbSillyNetMon;User=netmon;Password=netmon_pass;Option=3;"

```

Note that you will need to create the given user+password in MySQL., with SELECT privileges for reading, INSERT and/or UPDATE privileges for writing


Here's a working exemple in vb script.
[http://users.telenet.be/mydotcom/program/bibmon/mysqlcheckin.txt](http://users.telenet.be/mydotcom/program/bibmon/mysqlcheckin.txt)
(context : [http://users.telenet.be/mydotcom/program/bibmon/](http://users.telenet.be/mydotcom/program/bibmon/) )

---

