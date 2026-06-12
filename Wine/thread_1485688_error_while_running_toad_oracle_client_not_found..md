---
title: "error while running toad oracle client not found."
date: 2010-05-17
forum: Wine
---

### Post by faisalloe on 2010-05-17
Hello, 

I have installed oracle client on ubuntu 10 when i write sqlplus on terminal and it asks for the username and pass to login its mean oracle client is installed.

how to run toad using wine ?

---

### Post by Waappu on 2010-05-17
Hi,

I propose you use SQL developer
[http://www.oracle.com/technology/software/products/sql/index.html](http://www.oracle.com/technology/software/products/sql/index.html)

It is free and you do not need run it with Wine.
And you do not need Oracle client to be installed

---

### Post by mentalcic on 2010-05-19
Hi,

Consider using [TOra]("http://torasql.com")
I think you might find it useful as much as TOAD

I'm not an expert but you should also consider, if Oracle client is installed, adding oracle paths to your user paths if they are not added already - client applications like TOAD use entries from tnsnames.ora (located in /oracle/<version>/network/admin/) in order to connect to the desired database.

If you installed Oracle client with the default database created during installation (default option is to create this database), typing only sqlplus in command window will assume that you want to connect to your default database installed on your local machine (default value of ORACLE_SID).Here you should input username/password (sys/password you have entered during the installation). In order to check the connectivity to other databases you have access try typing the following in command window:

set ORACLE_SID=<insert TNS name of the database you have in your TNSnames.ora file mentioned above>
sqlplus /nolog #This will prompt you with sqlplus command interface without prompting for anything. from there type the following connection command
connect logon #where logon is <username>[/<password>][@<connect_identifier>]

If the prompt is "Connected." this "test" confirms your Oracle client installation and connectivity.

---

