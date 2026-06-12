---
title: "Zimbra not running after server changes..."
date: 2008-12-24
forum: Server Platforms
---

### Post by snake_eyes on 2008-12-24
Hello,

I installed Zimbra on test machine and it was working well, I prepared a new machine in order to be the production server, I follow those links:
[Moving ZCS to New Server - Zimbra :: Wiki](http://wiki.zimbra.com/index.php?title=Moving_ZCS_to_New_Server)
[Open Source Edition Backup Procedure - Zimbra :: Wiki](http://wiki.zimbra.com/index.php?title=Open_Source_Edition_Backup_Procedure)

finally when I tried to start the server I got:
```

zimbra@mail:~$ zmcontrol status
        antispam                Running
        antivirus               Running
        ldap                    Running
        logger                  Stopped
                logmysql.server is not running
        mailbox                 Stopped
                mysql.server is not running.
        mta                     Running
        snmp                    Running
        spell                   Running
        stats                   Stopped

```

If we execute logmysql as zimbra user, we get:

```

ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/opt/zimbra/logger/db/mysql.sock' (2)

```

The error in /opt/zimbra/log/logger_mysql_error is:
```

Warning: World-writable config file '/opt/zimbra/conf/my.logger.cnf' is ignored
Warning: World-writable config file '/opt/zimbra/conf/my.logger.cnf' is ignored
Starting mysqld daemon with databases from /opt/zimbra/mysql-standard-5.0.51a-pc-linux-gnu-i686-glibc23/var
081223 17:10:00  mysqld started
Warning: World-writable config file '/opt/zimbra/conf/my.logger.cnf' is ignored
081223 17:10:00 [Warning] Can't create test file /opt/zimbra/mysql-standard-5.0.51a-pc-linux-gnu-i686-glibc23/var/mail.lower-test
081223 17:10:00 [Warning] Can't create test file /opt/zimbra/mysql-standard-5.0.51a-pc-linux-gnu-i686-glibc23/var/mail.lower-test
^G/opt/zimbra/logger/mysql/libexec/mysqld: Can't change dir to '/opt/zimbra/mysql-standard-5.0.51a-pc-linux-gnu-i686-glibc23/var/' (Errcode: 2)
081223 17:10:00 [ERROR] Aborting

081223 17:10:00 [Note] /opt/zimbra/logger/mysql/libexec/mysqld: Shutdown complete

STOPPING server from pid file /opt/zimbra/mysql-standard-5.0.51a-pc-linux-gnu-i686-glibc23/var/mail.mydomain.com.pid
081223 17:10:00  mysqld ended
081223 17:10:00  mysqld ended

```

No output for the file /opt/zimbra/log/zmmyinit.log.

Also, I tried to access Zimbra Administration Console through HTTP, but it doesn't works.
Can someone please help?

Cheers,

---

### Post by gtdaqua on 2008-12-24
You are better off asking help in Zimbra Forums. A user named Phoenix, a zimbra employee, is very quick in responding. I remember having such errors on my non-production zimbra servers and got it resolved fairly quickly.

---

### Post by windependence on 2008-12-24
You didn't preserve permissions when you copied files.

Make sure you shut down the zimbra server first:

As root do:

```
#su - zimbra
#zmcontrol stop
```

Wait for the server to stop all services, then:

Log on to the Zimbra server **as root** and then run:

```
#/opt/zimbra/libexec/zfixperms
```

-Tim

---

### Post by snake_eyes on 2008-12-24
Hello windependence,

For sure I did, below is the command that I ran after the backup in order to restore zimbra into the new server:
```

su zimbra
zmcontrol stop
ps auxww | grep zimbra
ps auxww | awk '{print $1" "$2}' | grep zimbra | kill -9 `awk '{print $2}'`
mv /opt/zimbra [new location i.e. /tmp/zimbra-old]
cp -rp [location of backup] /opt
mv /opt/[backup name] /opt/zimbra
chown -R zimbra:zimbra /opt/zimbra
/opt/zimbra/libexec/zmfixperms
chmod -R 775 /opt/zimbra/logger/db/

```

Can anyone help me?

Cheers,

---

### Post by windependence on 2008-12-24
LOOK at your logs. You have config files that are 777 permissions. Zimbra will not use those because it is a security risk.  You must set those files to the correct permissions. You may want to try running the chown and zmfixperms again. 

What is the output of :

```
ls -la /opt/zimbra/conf
```

and 

```
ls -la /opt/zimbra/mysql-standard-5.0.51a-pc-linux-gnu-i686-glibc23
```



Did you do the dummy install? If you skip this it won't work.

-Tim

---

### Post by snake_eyes on 2008-12-24
Actual I uninstalled the zimbra and following this procedure of backup:
[http://www.zimbrablog.com/blog/archives/2007/10/moving-zcs-to-another-server.html](http://www.zimbrablog.com/blog/archives/2007/10/moving-zcs-to-another-server.html) what do you think about it? is it helpfully?

Thank you windependence for your immediate response.

Cheers,

---

### Post by windependence on 2008-12-24
Try this one:

[http://wiki.zimbra.com/index.php?title=Moving_ZCS_to_New_Server](http://wiki.zimbra.com/index.php?title=Moving_ZCS_to_New_Server)

---

### Post by snake_eyes on 2008-12-24
> **windependence said:**
> Try this one:

[http://wiki.zimbra.com/index.php?title=Moving_ZCS_to_New_Server](http://wiki.zimbra.com/index.php?title=Moving_ZCS_to_New_Server)

Because I'm using the OSE I checked the Method For Open Source Edition Users but wasn't help :(

Cheers,

---

### Post by windependence on 2008-12-24
I don't understand. the method for the OS edition is about half way down the page. I am suggesting you start over with this new method, or you could fix the permissions on the individual files (there are only two).

-Tim

---

### Post by snake_eyes on 2008-12-24
> **windependence said:**
> I don't understand. the method for the OS edition is about half way down the page. I am suggesting you start over with this new method, or you could fix the permissions on the individual files (there are only two).

-Tim

Yes it is not completed, so I'm following now this procedure:
[http://www.zimbrablog.com/blog/archives/2007/10/moving-zcs-to-another-server.html](http://www.zimbrablog.com/blog/archives/2007/10/moving-zcs-to-another-server.html) and I'm in the last step (4)

I will feedback you with the status as soon as I'm finish.

Thank you.

Cheers,

---

### Post by snake_eyes on 2008-12-24
Hello,

I've been finished all the steps and finally the logger has been worked, but I stubmled with the mailbox :) the mysql.server is not running any help please?

Cheers,

---

### Post by gtdaqua on 2008-12-25
> **snake_eyes said:**
> Hello,

I've been finished all the steps and finally the logger has been worked, but I stubmled with the mailbox :) the mysql.server is not running any help please?

Cheers,

Like I already said, are you asking for help in the Zimbra Forums? I know I am not answering your question, but just pointing you at a better direction.

---

### Post by snake_eyes on 2008-12-26
Hello,

Thank you my dear... the problem was solved and everything is working well.

Cheers,

---

### Post by kevinatkins on 2009-02-23
OK, so you got it running... but HOW?

I've got the same problem, and it would have been nice if you could have elaborated.....

---

