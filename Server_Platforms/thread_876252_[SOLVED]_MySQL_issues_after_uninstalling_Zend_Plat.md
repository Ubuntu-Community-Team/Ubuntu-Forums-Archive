---
title: "[SOLVED] MySQL issues after uninstalling Zend Platform."
date: 2008-07-31
forum: Server Platforms
---

### Post by phantaszm on 2008-07-31
I recently uninstalled Zend Platform from my machine, and that's when my MySQL issues started popping up.

Here's a list of stuff I've observed and tried based on other related forum posts.

1. When using mysql client to connect to the local database (either using localhost or 127.0.0.1), 
```
mysql -h localhost
```
I get the error "ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/tmp/mysql.sock' (2)"

2. Running strace on the command 
```
strace mysql 2>&1 |grep my.cnf
```
shows that it looks for my.cnf in /etc/my.cnf, /root/.my.cnf and /usr/local/Zend/Core/etc/my.cnf. It doesn't look in /etc/mysql/my.cnf

3. Creating a symlink (or hard link) called /etc/my.cnf which points to  /etc/mysql/my.cnf work to some extent. This symlink 'hack' fails when I start db replication. It looks for the relay log in the wrong directory.

4. I've tried 'aptitude purge --purge-unused' on all the mysql related packages and reinstalled everything, but #2 still happens.

5. I have a perfectly identical system to this one, except that Zend platform was never installed on it. The my.cnf config files on both machines are identical. The other one, which never had Zend Platform installed, works without any issues.

6. I did an ldd on /usr/bin/mysql to list all the libraries it calls on, and performed an md5 check on all those libraries and compared it to the working machine. All identical.

7. The only thing I can think of is that there's some environment variable that the mysql client looks at that's been overwritten/changed when I installed Zend Platform, but I dunno where to start looking for that.

Any ideas or help would be greatly appreciated.

---

### Post by phantaszm on 2008-08-05
I've found the solution!

Zend installs its own libraries but doesn't remove it when it's uninstalled. 

For this mysql issue, I found the problematic libmysqlclient.so.xx in /lib/

Removing that file fixed everything!

Time to hunt down more unnecessary libraries that Zend had installed.

---

### Post by phantaszm on 2008-08-05
List of unnecessary libraries found in my installation

/usr/local/lib/libmcrypt.so.4
/usr/lib/libltdl.so.3
/lib/libmysqlclient.so.15

---

### Post by borfast on 2008-08-05
phantaszm, thanks for sharing the solution! :)

What did you do to find the problem?

Edit: it's probably a good idea to report this problem to Zend, so they can fix it.

---

### Post by phantaszm on 2008-08-05
I used 
```
slocate mysql |sort |nl
``` 
to list and number all the mysql related files on both systems.

I then compared the lists and noticed the broken one had one too many files. Moved the extra file elsewhere and it worked.

I ran strings on that library, just for the fun of it, and sure enough, there were references to the Zend dirs.

---

