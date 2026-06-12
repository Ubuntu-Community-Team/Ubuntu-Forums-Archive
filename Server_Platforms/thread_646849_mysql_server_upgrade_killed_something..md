---
title: "mysql server upgrade killed something."
date: 2007-12-21
forum: Server Platforms
---

### Post by nephish on 2007-12-21
hello there, i did an install updates from the package manager and got this spit out.
```

The following packages will be upgraded:
  findutils mysql-server-5.0
2 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 253kB/27.0MB of archives.
After unpacking 4096B disk space will be freed.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com gutsy-updates/main findutils 4.2.31-1ubuntu2.1 [253kB]
Fetched 253kB in 2s (108kB/s)     
Preconfiguring packages ...
(Reading database ... 101577 files and directories currently installed.)
Preparing to replace findutils 4.2.31-1ubuntu2 (using .../findutils_4.2.31-1ubuntu2.1_i386.deb) ...
Unpacking replacement findutils ...
Setting up findutils (4.2.31-1ubuntu2.1) ...

(Reading database ... 101577 files and directories currently installed.)
Preparing to replace mysql-server-5.0 5.0.45-1ubuntu3 (using .../mysql-server-5.0_5.0.45-1ubuntu3.1_i386.deb) ...
 * Stopping MySQL database server mysqld                                 [fail] 
invoke-rc.d: initscript mysql, action "stop" failed.
dpkg: warning - old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
 * Stopping MySQL database server mysqld                                 [fail] 
invoke-rc.d: initscript mysql, action "stop" failed.
dpkg: error processing /var/cache/apt/archives/mysql-server-5.0_5.0.45-1ubuntu3.1_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
 * Stopping MySQL database server mysqld                                 [fail] 
invoke-rc.d: initscript mysql, action "stop" failed.
 * Starting MySQL database server mysqld                                 [ OK ] 
/usr/bin/mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'debian-sys-maint'@'localhost' (using password: YES)'
Errors were encountered while processing:
 /var/cache/apt/archives/mysql-server-5.0_5.0.45-1ubuntu3.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

also, when i try to stop the server, i get this....
 ```

sudo /etc/init.d/mysql stop
 * Stopping MySQL database server mysqld                                 [fail] 

```

and when i try to restart... 
```

 sudo /etc/init.d/mysql restart
[sudo] password for piv:
 * Stopping MySQL database server mysqld                                [fail] 
 * Starting MySQL database server mysqld                                [ OK ] 
/usr/bin/mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'debian-sys-maint'@'localhost' (using password: YES)'

```


any ideas ?

thanks

---

### Post by Sef on 2007-12-21
Moved to servers and security.

---

### Post by Nano on 2007-12-28
Same here, now I can't install it anymore :(

---

### Post by nephish on 2007-12-28
ok, on my system, it would fail becuase it could not start or stop. here is what i did.

sudo chmod -x /etc/init.d/mysql

then i removed it, then installed it again. 

then gave execute permission back to the init script.
sudo chmod +x /etc/init.d/mysql

worked for me.
hope it helps

---

### Post by d3k4y on 2007-12-29
Success! The last reply may work, but I did not want to remove mysql as my sites depend on it.  Here is a quicker and easier way to get the update to work.

First, find the mysql processes by running:

**[FONT="System"]sudo ps -AL|grep sql[/FONT]**

and kill all the mysqld processes using:

**[FONT="System"]kill 15623[/FONT]**

replacing 15623 with whatever number comes up for you.
Once all the mysqld processes are killed, try the update again and it should go thru successfully.  As in the last post, for some reason mysql would not stop,  This is a way to force it down.  The update will, of course, update, and then restart mysql leaving all your settings and stuff intact.  As for why this happened in the first place, I dunno.

BTW, killing the process should work whenever you can't stop a service.  That may be obvious to some, but I thought I'd add it.

---

