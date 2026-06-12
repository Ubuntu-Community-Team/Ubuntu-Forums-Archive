---
title: "MySQL works (from php) but returns &quot;Killed&quot; in bash"
date: 2009-12-09
forum: Server Platforms
---

### Post by weryl on 2009-12-09
Hi again,

I recently upgraded my server to Karmic and everything went pretty well except for the following problem. I host several php forums on a LAMP server and each of them still works fine (read/write to mysql, php, etc) but whenever i try to access mysql over ssh i get the following answer:

```
mike@myserver:/$ mysql
Killed
mike@myserver:/$ mysql dbForum
Killed
mike@myserver:/$ mysql -u root -p
Killed
mike@myserver:/$ mysql banana
Killed
```

I tried restarting the service and here's what I get:

```
mike@huitcent:/$ sudo /etc/init.d/mysql restart
 * Stopping MySQL database server mysqld [ OK ] 
 * Starting MySQL database server mysqld [ OK ] 
 * Checking for corrupt, not cleanly closed and upgrade needing tables.
```

I don't really feel like exporting my data, completely removing MySQL and reinstalling as I'm not local and I'm afraid to bring the whole server down for a few weeks (until i get there). In the meantime it's not so bad since everything works fine from the web but I can't do basic maintenance (for instance I'd like to change a few user passwords). I have mysql-server-5.1 and mysql-client-5.1 installed, as well as the latest apache2/php5 libraries (i believe they are, ive just run do-release-upgrade and dist-upgraded).

I'm sure more data would be necessary so don't hesitate to ask (and provide appropriate commands if possible)!

Thanks alot,

Mike

---

### Post by craigp84 on 2009-12-10
Hi,

Do you have any ulimits set for users logging in via ssh? Use ```
ulimit -a
``` to see.

If you do, maybe on cputime or memory usage, this is the behaviour you might see.
```

me@myhost # ulimit -t 1
me@myhost # ulimit -a
time(cpu-seconds)    1
file(blocks)         unlimited
coredump(blocks)     unlimited
data(kbytes)         unlimited
stack(kbytes)        10240
lockedmem(kbytes)    32
memory(kbytes)       unlimited
nofiles(descriptors) 1024
processes            1064959
me@myhost # yes > /dev/null
Killed
me@myhost #

```

---

