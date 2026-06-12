---
title: "ERROR 2002 (HY000): Can't connect to local MySQL"
date: 2010-07-04
forum: Server Platforms
---

### Post by abibib on 2010-07-04
hello
I have ubuntu server 10 on my server.

but I can't access to Mysql. I didn't change anything 

I got this error : 

ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (111)

even when I want to restart mysql.

please help 

thanks

---

### Post by Rhiknow on 2010-07-05
This might help:

[http://ubuntuforums.org/showthread.php?p=9550558#post9550558](http://ubuntuforums.org/showthread.php?p=9550558#post9550558)

I've the same problem

---

### Post by jdieter on 2010-07-06
I have the same problem! Is there a fix?

---

### Post by Stoneface on 2010-07-18
Any fix found by jdieter or abibib?

---

### Post by Di.Mon on 2010-11-06
I had same problem on new installed Ubuntu Server 10

The only  solution that worked for me is reinstall all mysql packages.
 
Good news that it takes only couple minutes to do :)

So you need to do following steps to reinstall all that packages in couple commands:

```
dpkg -l | awk '{print $2}' | grep mysql > installed_packages.txt
```

This command will write to fille all packages with "mysql" in packet name

Then I uninstalled and then installed again al this packages with 2 commands:
```

apt-get remove `cat installed_packages.txt`
apt-get install `cat installed_packages.txt`

```

Hope this will helpful for anybody :)

---

