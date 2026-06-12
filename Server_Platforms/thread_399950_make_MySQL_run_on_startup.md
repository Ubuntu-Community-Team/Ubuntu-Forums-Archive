---
title: "make MySQL run on startup"
date: 2007-04-02
forum: Server Platforms
---

### Post by HighD on 2007-04-02
Ok so I installed MySQL 5.1 from source...now all i need is make it run on startup. I understand I have to copy the mysql.server that comes in suppor-files folder and copy it as mysql on /etc/init.d/. That's as far as I got to. Any help on what I'm missing? 

I must run this command as 'username' not as root. 

Thanks in advance for all the help :D

---

### Post by amohanty on 2007-04-03
Wont 5.0.22 (in the repos) not do ?? :)
Its a whole lot easier that way. If you still want to do it the hard way, well the mysql.server script will typically launch another program to start the actual server. To make sure that it runs it as user <username> hunt down where that call to the actual server is and prefix it with **su - username **.

Then create links in /etc/rc2.d to /etc/init.d/mysql.server. You have to create two. I explained this a while back here:
[http://ubuntuforums.org/showpost.php?p=1159446&postcount=2](http://ubuntuforums.org/showpost.php?p=1159446&postcount=2)

HTH
AM

---

### Post by WesRatcliff on 2007-04-03
> **amohanty said:**
> Wont 5.0.22 (in the repos) not do ?? :)

The 5.1 branch has some major improvements in the clustering support.

Can't wait to have 5.1 available via apt!

Wes

---

### Post by HighD on 2007-04-03
Thanks amohanty :D

> **amohanty said:**
> Wont 5.0.22 (in the repos) not do ?? :)

Well, the thing is I'm an student taking on a db course, and I was specifically told to install MySQL 5.1(even though it's beta).

> 

Then create links in /etc/rc2.d to /etc/init.d/mysql.server. You have to create two. I explained this a while back here:
[http://ubuntuforums.org/showpost.php?p=1159446&postcount=2](http://ubuntuforums.org/showpost.php?p=1159446&postcount=2)

HTH
AM



I created the two symbolic links for startup and shutdown and it didn't work, I also used sysv-rc-conf to run mysql at level 2 and at startup, i used various combinations and it did't work either, what could I be doing wrong?

I know the script works because when I execute
```

/etc/init.d/mysql start
```

the MySQL daemon starts and when i execute

```
/etc/ini.t/mysql stop
```

it stops!

I run these who commands as 'username' not as root, if I run them as root the daemon fails starting up, obviously because i specifically told the mysql_installdb script that the daemon should be only run as 'userame', as I don't want it to be run as root.

What could I be doing wrong?

---

### Post by amohanty on 2007-04-03
The scripts in /etc/init.d _are_ run as root. ANother way is to:
1. put mysql.server in /usr/local/bin
2. Use the script in the post as a template and call it run-mysql
3. in that script call the mysql.server script as: **su - username /usr/local/bin/mysql.server**
4. Put that in /etc/init.d and redo the whole linking thing.

If possible post the script you created here.

HTH
AM

---

### Post by HighD on 2007-04-03
Ok so I did the following

1) Put mysql.server on /usr/local/bin and made it executable

2) Created this script and named it 'run-mysql' as amohanty said  :


```
#! /bin/bash

case $1 in
  start)
    su highd /usr/local/bin/mysql.server start
    ;;
  stop)
    su highd /usr/local/bin/mysql.server stop
    ;;
  restart)
    stop
    start
    ;;
  *)
    echo Oops! bad options
    ;;
esac
exit 0
```

4) Made this above script executable

5) Used sysv-rc-conf to set run-mysql to run at level 2

6) Rebooted and it worked!! :D

I tried the linking as you said amohanty but it didn't work, so I tried with sysv-rc-conf.

Thanks for help amohanty! :mrgreen:

---

