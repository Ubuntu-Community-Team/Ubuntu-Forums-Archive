---
title: "Secure connection between Daemon and PHP site"
date: 2010-02-14
forum: Security
---

### Post by thomasn123 on 2010-02-14
Hi Guys,

I have coded a daemon in php that will perform system admin actions like adding users and editing system files. I also have a php website / dashboard that users can login to and use. How can I get the php site to talk to the daemon securely? Can the daemon check where the request originates from so it will only process commands from the dashboard?

The server is like a home server, users can login on their local network but I would also like to let users login over the net. 

I have read about using sockets, but dont really know anything about them / their security?

Thanks

Tom

---

### Post by jfparis on 2010-02-16
Big question 

First thing, you can have the daemon listening to a local socket or to the network but only from connection on the from localhost 127.0.0.1. Nobody from outside will be able to access it

That won't prevent local users to send orders to the daemon

If you use a socket you can set the permission on that socket so only the webserver can talk to the daemon 

Last but not least you can have a password (or some more complex certificate) accessible only by the server and know by the deamon that authenticate the orders

Be sure that the users on the machine can't access to that password or to the certificate

---

### Post by thomasn123 on 2010-02-17
Thanks for the info!

> First thing, you can have the daemon listening to a local socket or to the network but only from connection on the from localhost 127.0.0.1

The webserver and daemon are on the same machine so that is no problem.

> That won't prevent local users to send orders to the daemon

This isn't a problem as the system is going to be headless. 

Do you know exactly how to setup the socket with the permissions you mentioned and the password protection. Also, will this socket be secure enough to send clear passwords through?

Thanks once again,

Tom

---

### Post by jfparis on 2010-02-17
For the sockets have a look here

[http://www.devshed.com/c/a/PHP/Socket-Programming-With-PHP/](http://www.devshed.com/c/a/PHP/Socket-Programming-With-PHP/)
and 
[http://php.net/manual/en/book.sockets.php](http://php.net/manual/en/book.sockets.php)

You might want to use unix sockets (less overhead). have a look here: [http://www.php.net/manual/en/function.socket-create.php](http://www.php.net/manual/en/function.socket-create.php)

I don't remember how to set the permissions when creating a unix socket. Chmod on the file use as a socket should be ok. (you create a group "phpdeamon". the file is owned by that group and only that group can read/write. The daemon is executed by a user in that group and php frontend is also run by a user in that group)

If you want to add the "shared secret" password, it need to be in a file and with permissions that make it readable by the daemon and the server only (a shared unix group with the right permissions). One issue though. The php frontend gonna run with the permissions of apache (I assume you use apache here). Therefore any other script running on that apache will have the same permissions and will be able to read the file where the password is (any user running a php script within the same apache might do it). So you might want to set up a specific apache for the front end.

Maybe other solutions exist but I don't know them

jf

---

### Post by thomasn123 on 2010-02-18
Thanks once again.

Could I save the command data  (say for example adding a user it would be the username and password) in a mysql database, then have the php site to tell the daemon to check the database and run the command. That way i can store the mysql password in the daemon file and php file. I would still use a socket to tell the daemon to check the database but at least then there isn't the security issue of anything on the apache server being able to perform system commands!

Tom

---

### Post by jfparis on 2010-02-18
Yes that is an option but that would make your system asynchronous (which might be fan)

But instead of mysql have a look at ActiveMQ: [http://activemq.apache.org/](http://activemq.apache.org/)

Implementing a message queue (which is what you propose) with an sql database might not be the best option. A queue messaging system like activeMQ might be better.

---

### Post by thomasn123 on 2010-02-26
By asyncronous you mean it can only do one thing at a time? Surely though with ActiveMQ, it can only do one thing at a time? As it is a queue of commands?

Found this [tutorial.]("http://www.webdeveloperjuice.com/2010/02/02/11-easy-steps-for-installing-apache-activemq-and-configuring-it-for-php-application/")

The tutorial says that I need to add extension=stomp.so, can i have that as well as the mysql extension?

Thanks once again,

Tom

---

