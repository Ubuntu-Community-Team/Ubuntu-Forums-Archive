---
title: "problem with mysqld"
date: 2009-09-15
forum: Server Platforms
---

### Post by adramalech on 2009-09-15
okay i don't know what i did i have gone through the phpmyadmin db-config.php, /etc/mysql/my.cnf, and the other mysql configuration files and guess what everything about the servers is localhost and default port 3306 and it still errors saying it cannot start dbserver on localhost in the daemon.log file....i don't know what to do besides uninstall everything and reload the defaults....

until i get this going correctly it is screwing up phpmyadmin....and i cannot do anything with my website...

i have tried restarting everything....with no success and it doesn't seem to give me a damn explicit problem it just says it won't start on localhost even though i have port 3306 open for tcp on ufw for any ip address...

any suggestions or help would be very nice...

---

### Post by adramalech on 2009-09-15
i got rid of dhcp3 if this makes any difference....because my server is just static....

also this is what i get when i try to find the status of mysql server

```

>> mysqladmin status
mysqladmin: connect to server at 'localhost' failed
error:  'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Check that mysqld is runnning and that the socket: '/var/run/mysqld/mysqld.sock' exists!

```

also this is what i also got from trying to start service on localhost manually

```


>> mysql -u youruser -p
Enter Password:
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)


```

i checked the directory /var/run/mysqld/mysqld.sock and it doesn't exist!!  the /var/run/msyqld is there but nothing inside of it that i could see...maybe it is hidden but anyways should i stop messing around and reinstall mysql???

i got it from taskel in LAMP option...

---

