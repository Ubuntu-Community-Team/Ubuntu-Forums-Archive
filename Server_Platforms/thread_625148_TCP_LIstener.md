---
title: "TCP LIstener"
date: 2007-11-27
forum: Server Platforms
---

### Post by rbarr2007 on 2007-11-27
Hi

Coming from a .Net background I have a Multi-threaded TCP listener that monitors TCP traffic from GPS devices that connect via GPRS and puts the position data into a SQL Server Database.

I am now trying to figure out which direction I need to go in order to do the whole thing with with Linux instead.

The devices connect to an IP address and port on TCP and then pass positions. These positions need to be stored in a database for later analysis.

I have used the tcpreen and tcplisten utilities to test, but what is the best way to monitor the ports I select and take the data forwarded to those ports into a MySQL database for example.

I tried figuring this out myself but I feel that I need a push in the right direction. Especially in terms of security, encryption etc.

Any help with which direction I should be looking at would be appreciated.

---

### Post by koenn on 2007-11-27
Are you looking for a program, or planning to write one ?
Without any experience in what you're trying to do, I'd guess that
- a tool such as nc ('netcat') in server (listening) mode could probably be used to read data coming to an arbitrary tcp port. You could dump the data in a file for another program to read, or pipe it to another tool   that writes the data to the database
- or you could write something with sockets, eg in C. I think Perl knows sockets too. 

putting data in a database is just a matter of creating sql INSERT and UPDATE statements and sending them to the database. The hard part will be creating the database connection - I don't know how well native MS SQL Server connections or ODBC are supported in Linux programming or scripting languagues.

Hope this gives you an idea.

---

### Post by rbarr2007 on 2007-11-27
I wouldn't mind writing my own program if I need to.

Just curious what would be the acceptable way of dealing with high volumes of traffic with Linux if there are many devices sending positions every second. 

If I could write my own TCP Listener or use some built-in function if that is available to receive the data and send it off to MySQL.

---

### Post by koenn on 2007-11-28
> **rbarr2007 said:**
> I wouldn't mind writing my own program if I need to.

Just curious what would be the acceptable way of dealing with high volumes of traffic with Linux if there are many devices sending positions every second. 

If I could write my own TCP Listener or use some built-in function if that is available to receive the data and send it off to MySQL.
I'm not a programmer so I con't really help you on how to deal with lots of data. 
As for the many devices simulltanously : the usual way is to "fork", eg you have a process with a socket listening, and when a remote host connects, the process "forks", i.e it creates a new ("child") proces, with a socket listening, while the original ("parent") processs 'sockets answers the call and moves to state 'connected',  (and deals with the incoming data)
Kinda like creating a new instance in OO languages, i think. 

But for this type of stuff you're probably better of in the programmers talk forum, or with a decent unix / socket programming manual. Look for "BSD Sockets progarmming" or something similar. Here's a primer : [http://www.cs.vu.nl/~jms/socket-info.html](http://www.cs.vu.nl/~jms/socket-info.html)

I suppose you're familiar with the concept of sockets. On Unix/linux, they behave pretty much like files that you can read from or write to, except that you write to a ipaddres : portnumber rather than an actual file. The equivalent on Windows would probably be a call to some code in winsock.dll or so, possibly through the interface of an object or a prefab component. 

As for writing to a database : as I said ; you need to figure out how common linux scripting or programming languages do that. Again, people on the programmers forum probably can help you out. The closest I ever got was a vb script on Xp that writes to a Mysql database on Linux through an ADODB connection with ODBC. In a Linux shell script I suppose you could use something along the lines of
```
mysql  -h dbserver_hostname  --execute="SQL statement goes here" database_name 
``` or by using redirection ( < ) to insert sql statems from a file (see man mysql). 
Again, I have no idea how real programmers would do it.  :)

programmers forum :
[http://ubuntuforums.org/forumdisplay.php?f=39](http://ubuntuforums.org/forumdisplay.php?f=39)

---

### Post by sciurus on 2007-11-29
IF you already have the program written in .Net, hopefully you can run it on Linux using [Mono]("http://www.mono-project.com/Main_Page") with minor modification.

---

