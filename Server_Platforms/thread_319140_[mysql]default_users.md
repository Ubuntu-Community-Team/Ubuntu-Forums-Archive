---
title: "[mysql]default users"
date: 2006-12-15
forum: Server Platforms
---

### Post by Wim Sturkenboom on 2006-12-15
Just installed ubuntu server using the lamp option. I checked the mysql users and found a user debian-sys-maint (with password) with a large subset of the root-privileges
Q1)
What's the password for this user (brute force takes too long :D ); I tried the username as a password and it did not work.
Q2)
The purpose of this user; just a generic admin user?
What are the implications of removing this user? Will it affect the ability to update the mysql server by apt-get (from a mysql configuration point)?

```
GRANT SELECT, INSERT, UPDATE, DELETE, CREATE, DROP, 
RELOAD, SHUTDOWN, PROCESS, FILE, REFERENCES, INDEX, ALTER, SHOW DATABASES, 
SUPER, CREATE TEMPORARY TABLES, LOCK TABLES, EXECUTE, 
REPLICATION SLAVE, REPLICATION CLIENT 
ON *.* TO 'debian-sys-maint'@'localhost' IDENTIFIED BY PASSWORD '1f3bad2e2f81ece6' 
WITH GRANT OPTION
```

---

### Post by tturrisi on 2006-12-15
debian-sys-maint is the default mysql user on debian systems that loads mysql.  The password (encrypted) is in /etc/mysql/debian.cnf  See post by speedman   here: [http://ubuntuforums.org/showthread.php?t=27156&page=2](http://ubuntuforums.org/showthread.php?t=27156&page=2)

---

