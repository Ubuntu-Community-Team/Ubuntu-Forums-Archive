---
title: "Complete reinstall of mysql help"
date: 2007-01-03
forum: Server Platforms
---

### Post by szim90 on 2007-01-03
Hello. 

I apologize if this is stupid question, but I am new to mysql and I have not been able to find any answers.

I accidentally messed up my mysql installation (I corrupted the databases), and I tried to correct it by purging mysql-server and mysql-client, as well as emptying the /etc/mysql and /usr/share/mysql directories. Now, even after reinstalling the mysql-client, mysql-common, and mysql-server package, mysql will not start. How do I completely reinstall mysql, including all the default databases, and the /etc/mysql and /usr/share/mysql directories?

Thank you for any help.

Sean

---

### Post by moephan on 2007-01-04
When you uninstalled, did you mark it for "complete removal"?

Cheers, Rick

---

### Post by szim90 on 2007-01-04
I used the following command:

apt-get remove --purge mysql-server mysql-client

I think that is the same as synaptic's comlete removal.

Also, I was able to get back by /usr/share/mysql files by reinstalling all the mysql libs, but I still am missing files in /etc/mysql. Here is the error message:

 * Stopping MySQL database server mysqld                                 [ ok ] 
 * /etc/init.d/mysql: WARNING: /etc/mysql/my.cnf cannot be read. See README.Debian.gz
grep: /etc/mysql/my.cnf: No such file or directory
 * Starting MySQL database server mysqld                                 [ ok ] 
/etc/init.d/mysql: line 122: /etc/mysql/debian-start: No such file or directory

I tried reinstalling mysql-common, but that didn't help.

Sean

---

### Post by szim90 on 2007-01-04
I was able to fix the problem by purging and then reinstalling the mysql-common package. This recreated the files in /etc/mysql.

For future reference, if I corrupt the mysql databases again, what is the best way to reset the databases?

Sean

---

### Post by Brazen on 2007-01-05
> **szim90 said:**
> I was able to fix the problem by purging and then reinstalling the mysql-common package. This recreated the files in /etc/mysql.

For future reference, if I corrupt the mysql databases again, what is the best way to reset the databases?

Sean

Database files are kept in /var/lib/mysql so that is the directory that you needed to empty.  That was probably done when you purged the mysql-common package.

---

### Post by szim90 on 2007-01-14
Okay. Thanks for the help Brazen.

---

### Post by Wim Sturkenboom on 2007-01-15
From the mysql manual:
> **mysql_install_db** 
This script creates the MySQL database and initializes the grant tables with default privileges. It is usually executed only once, when first installing MySQL on a system. See Section 2.10.2, &#8220;Unix Post-Installation Procedures&#8221;.

---

