---
title: "can't access mysql remotely using mysql-admin or odbc"
date: 2008-03-29
forum: Server Platforms
---

### Post by jbprinicpato on 2008-03-29
I installed mysql and can connect without a problem using php. I can also user phpmyadmin web interface and administer the databases.  However, if I try and connect using mysql-admin on a remote pc or connect using an odbc I get an error number 2003 and can't connect message (10061).  I looked at the user table in the mysql database and there are three host entries for the root user, an '%', 'servername', and '127.0.0.0' entry.  I also created anothe user that has full privileges and that user has a host entry of '%'. I can ping the serve from the remote pc and use the phpmadmin web from the remote pc but nothing else.
I changed the my.cnf file bind variable to the localhost ip address.

  Any suggestions on getting the odbc and mysql-admin working?

---

### Post by jbprinicpato on 2008-03-30
I think it may be a restriction on port 3306.  I tried to telnet to the server using port 3306 but got no response from the server. It there a way to check and see if the iptables are retricting the traffic to remote computers for port 3306?

---

### Post by Poleh on 2008-03-31
more than likely if you installed mysql through apt-get it's because the mysql server only binds to 127.0.0.1 which is localhost.

Comment out the line under the networking section like this to let mysql bind to all ip's
#bind-address            = 127.0.0.1

Then you should be able to connect to the server, as long as you have users who have permissions in mysql to do so from a remote client.

---

