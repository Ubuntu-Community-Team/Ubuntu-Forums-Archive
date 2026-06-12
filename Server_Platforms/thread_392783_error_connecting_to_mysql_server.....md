---
title: "error connecting to mysql server...."
date: 2007-03-24
forum: Server Platforms
---

### Post by Mia_tech on 2007-03-24
I have installed mysql, php, and apache, just getting started, and I'm trying to connect to mysql and I get this error:

jorge@ubuntu-box:/$ mysqladmin -h root@localhost -u root -p password password
Enter password:
mysqladmin: connect to server at 'root@localhost' failed
error: 'Unknown MySQL server host 'root@localhost' (1)'
Check that mysqld is running on root@localhost and that the port is 3306.
You can check this by doing 'telnet root@localhost 3306'

after running nmap and restarting mysql, it is running on port 3306, but I can't connect not even with mysqladmin user interface using the loopback address
any help appreciated 
thanks

---

### Post by conjur3r on 2007-03-25
Take out the root@ from the hostname.

---

