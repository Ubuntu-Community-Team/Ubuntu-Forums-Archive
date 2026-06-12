---
title: "Mysql problem"
date: 2011-04-15
forum: Server Platforms
---

### Post by satimis on 2011-04-15
Hi folks,

Ubuntu 1010 server 64bit

$ hostname```

ub1010ser03

```

$ hostname -a```

ub1010ser03

```

$ mysqladmin -h ub1010ser03 -u root password mysqlroopassword```

mysqladmin: connect to server at 'ub1010ser03' failed
error: 'Lost connection to MySQL server at 'reading initial communication packet', system error: 113'

```

I have been googling around, some suggesting changing my.cnf
```

port 3306

```

another suggesting```

port 3306/TCP

```

But I can't solve the problem.  Please help.  TIA

B.R.
satimis

---

### Post by kamaji792 on 2011-04-15
Are you on the box with the mysql server? Or are you connecting remotely?

What are you trying to do with the **mysqladmin** command.  The general form of the command is:

```
mysqladmin [options] command
```

What was the command you wanted to run?

Atb K

---

### Post by SeijiSensei on 2011-04-15
Is your hostname an alias for localhost, or is it assigned to another IP address in /etc/hosts?  MySQL by default on Ubuntu listens only on the localhost address (127.0.0.1).  Look at the "bind-address" directive in my.cnf.

---

### Post by satimis on 2011-04-15
Hi Atb K,

> **kamaji792 said:**
> Are you on the box with the mysql server? Or are you connecting remotely?

Yes, I'm on the box which is a virtual machine.  Mysql server is running on the VM

host - ubuntu 1010 desktop 64bit
virtualizer - Oracle VirtualBox
VM (guest) - Ubuntu 1010 server 64bit

> 
What are you trying to do with the **mysqladmin** command.  The general form of the command is:

```
mysqladmin [options] command
```

What was the command you wanted to run?

Atb K
I'm following;
Creating Simple Virtual Hosts With mod_mysql_vhost On Lighttpd (Debian Etch)
[http://www.howtoforge.com/creating-simple-vhosts-with-mod_mysql_vhost-on-lighttpd-debian-etch](http://www.howtoforge.com/creating-simple-vhosts-with-mod_mysql_vhost-on-lighttpd-debian-etch)

coming to the step;```

you should set a MySQL password for your hostname .....

```
I was stuck here.  Thanks

B.R.
satimis

---

### Post by satimis on 2011-04-15
Hi SeijiSensei,

> **SeijiSensei said:**
> Is your hostname an alias for localhost, or is it assigned to another IP address in /etc/hosts?  


$cat /etc/hosts```

127.0.0.1	localhost
local_IP	ub1010ser03.domain.com	ub1010ser03
....
....

```

$ cat /etc/hostname ```

ub1010ser03

```

> 
MySQL by default on Ubuntu listens only on the localhost address (127.0.0.1).  Look at the "bind-address" directive in my.cnf.
$ cat /etc/mysql/my.cnf | grep bind```

bind-address		= local_IP

```

Previously```

bind-address = 127.0.0.1

```
I encountered this problem.  Then I changed it to local_IP.  But the problem is still there.

B.R.
satimis

---

### Post by falko on 2011-04-16
What's the output of ```
netstat -tap
```?

---

### Post by kamaji792 on 2011-04-16
Try this:

[http://dev.mysql.com/doc/refman/5.0/en/can-not-connect-to-server.html](http://dev.mysql.com/doc/refman/5.0/en/can-not-connect-to-server.html)

Atb K

<edit>
You should only have to worry about the connection port (3306) if you are connecting remotely to mysql.

---

### Post by satimis on 2011-04-16
> **falko said:**
> What's the output of ```
netstat -tap
```?

$ netstat -tap```

(No info could be read for "-p": geteuid()=1000 but you should be root.)
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 localhost:mysql         *:*                     LISTEN      -               
tcp        0      0 *:ssh                   *:*                     LISTEN      -               
tcp        0      0 VM local_IP:ssh       host local_IP:57984     ESTABLISHED -               
tcp6       0      0 [::]:ssh                [::]:*                  LISTEN      -     

```
Remark: bind-address = 127.0.0.1          

$ sudo netstat -tap```

Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 localhost:mysql         *:*                     LISTEN      763/mysqld      
tcp        0      0 *:ssh                   *:*                     LISTEN      1003/sshd       
tcp        0      0 VM local_IP:ssh       host local_IP:57984     ESTABLISHED 1048/sshd: satimis 
tcp6       0      0 [::]:ssh                [::]:*                  LISTEN      1003/sshd       

```

B.R.
satimis

---

### Post by satimis on 2011-04-16
> **kamaji792 said:**
> Try this:

[http://dev.mysql.com/doc/refman/5.0/en/can-not-connect-to-server.html](http://dev.mysql.com/doc/refman/5.0/en/can-not-connect-to-server.html)

Atb K

<edit>
You should only have to worry about the connection port (3306) if you are connecting remotely to mysql.

Thanks for your advice and link

satimis

---

