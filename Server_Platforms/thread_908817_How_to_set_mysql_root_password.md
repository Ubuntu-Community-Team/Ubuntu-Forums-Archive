---
title: "How to set mysql root password?"
date: 2008-09-02
forum: Server Platforms
---

### Post by yinglcs2 on 2008-09-02
I just install mysql and i did not do any configuration.

When I do this:

:/home/scheung# mysql -u root -p
Enter password: 
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)

I just press ENTER for the password.

I tried these:

 $ sudo mysqladmin -u root password hello
mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'root'@'localhost' (using password: NO)'


It fails as well.

Thank you for any help.

---

### Post by windependence on 2008-09-02
Here ya go:

[https://help.ubuntu.com/community/MysqlPasswordReset](https://help.ubuntu.com/community/MysqlPasswordReset)

-Tim

---

### Post by yinglcs2 on 2008-09-03
I am getting this error:

$ sudo mysqld --skip-grant-tables --user=root
[sudo] password for yinglcs: 
080903 10:36:26 [Warning] Ignoring user change to 'root' because the user was set to 'mysql' earlier on the command line

080903 10:36:27  InnoDB: Started; log sequence number 0 43655
080903 10:36:27 [ERROR] Can't start server : Bind on unix socket: No such file or directory
080903 10:36:27 [ERROR] Do you already have another mysqld server running on socket: /var/run/mysqld/mysqld.sock ?
080903 10:36:27 [ERROR] Aborting

080903 10:36:27  InnoDB: Starting shutdown...
080903 10:36:29  InnoDB: Shutdown completed; log sequence number 0 43655
080903 10:36:29 [Note] mysqld: Shutdown complete


I have even reboot my machine , I still get the same error.

---

### Post by cariboo on 2008-09-03
Try:

```
dpkg-reconfigure mysql-server
```

Of course this will only work if you installed mysql from the repositories

Jim

---

### Post by windependence on 2008-09-03
No, Cariboo, he doesn't have to do that. The problem is he is trying to start mysqld with it already running. He just needs to shut down the daemon. 

What this command does is start MySQL without reading the grant tables meaning you have all the poer you need to reset the root password.

Try this to see if your daemon is still running and if so kill it before you try the command:

```
sudo netstat -tlp | grep mysql

tcp  0  0  host.domain:mysql  *:*  LISTEN  20310/mysqld (don't type this)

sudo killall mysqld
sudo netstat -tlp | grep mysql
```

-Tim

---

### Post by yinglcs2 on 2008-09-08
hi,

I did what you suggested, but I still get the same error:

```

$ sudo netstat -tlp | grep mysql
[sudo] password for scheung: 
$ sudo netstat -tlp | grep mysql
[sudo] password for scheung: 
$ sudo killall mysqld
mysqld: no process killed
$ sudo mysqld --skip-grant-tables --user=root
080908 10:38:48 [Warning] Ignoring user change to 'root' because the user was set to 'mysql' earlier on the command line

080908 10:38:48  InnoDB: Started; log sequence number 0 43655
080908 10:38:48 [ERROR] Can't start server : Bind on unix socket: No such file or directory
080908 10:38:48 [ERROR] Do you already have another mysqld server running on socket: /var/run/mysqld/mysqld.sock ?
080908 10:38:48 [ERROR] Aborting

080908 10:38:48  InnoDB: Starting shutdown...
080908 10:38:50  InnoDB: Shutdown completed; log sequence number 0 43655
080908 10:38:50 [Note] mysqld: Shutdown complete


```

---

### Post by hyper_ch on 2008-09-08
```

mysqladmin -u root password yourrootsqlpassword

```

---

### Post by yinglcs2 on 2008-09-08
I tried that, and I get this:

```

$ mysqladmin -u root password hello
mysqladmin: connect to server at 'localhost' failed
error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!


```

---

### Post by hyper_ch on 2008-09-09
is mysql running? what does the my.cnf look like?

---

### Post by jonger on 2008-09-10
I have the same problem, where is my.cnf ? It think the error is because mysql isn't running. I think the problem might be the fact that the 8.04 repositories are using msql version 5.0.51. All the guide I see are using something earlier. There is also a problem with ubuntu default having no root password. i have set one and i'm not sure if that changes anything for all the guides and advice. i haven't found much from ubuntu on how to set mysql for amarok.


I solved my problem on the next page!!!

---

### Post by jonger on 2008-09-10
Thank you windependence. too many people trying to collect beans and not letting the troubleshooting process go step by step. your link did it. 

Alright here is what worked for me:


```
sudo /etc/init.d/mysql stop

/usr/bin/mysqld --skip-grant-tables --user=root

mysql -u root

>   USE mysql
>   UPDATE user SET Password = PASSWORD('newpwd')
>   WHERE Host = 'localhost' AND User = 'root';
>   FLUSH PRIVILEGES;

sudo /etc/init.d/mysql stop

sudo /etc/init.d/mysql start
```

---

### Post by waxwing_user on 2008-09-14
Hello,

I've been following a number of these threads in order to move forward on using xampp.  I have tried to reset my mysql password but I don't have the mysql stop "function" in the init.d folder.  Should I reference some other folder?  

Thanks

---

### Post by cariboo on 2008-09-15
IF you are runinng Ubuntu, you start and stop all the services in /etc/init.d. To start and stop services, open a terminal and using mysql as an example type:

```
sudo /etc/init.d/mysql stop
```

to stop the server and

```
sudo /etc/init.d/mysql start
```

to start the server.

After typing the above I had a look at the start and stop commands of xampp on this page here:

[http://www.apachefriends.org/en/xampp-linux.html#377](http://www.apachefriends.org/en/xampp-linux.html#377)

It looks pretty simple.

Jim

---

### Post by waxwing_user on 2008-09-15
I thought so too.  I've tried that and I get "No Such File or Directory."  Clearly, in my installation, files necessary to mysql have not been added to init.d and I have no idea why not.  I've deinstalled and reinstalled many times and only once have I been able to get this to work.  Then, other problems arose and after making adjustments, I haven't been able to get back to "mysql stop" functionality.  To add context to this, ultimately, I want to run Joomla.  To do that I'm told you have to use the command "mysql -u root" with other characters depending on whether there are problems or not.  I can run phpmyinfo from lampp/localhost.  Should I be using that somehow to set the password for mysql or not concern myself with that function.  It does seem strange that init.d does not have anything for mysql.  Help!

---

### Post by waxwing_user on 2008-09-15
Oh, one more thing...when i type "mysql -u root" i get "ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)"

This is my ultimate failure to date and needs to be resolved.

---

### Post by guitsy on 2009-07-11
hi friend.
the solution which worked for me
 
install webmin. to install webmin

Preparing Your System

You need to install the following packages

sudo apt-get install perl libnet-ssleay-perl openssl libauthen-pam-perl libpam-runtime libio-pty-perl libmd5-perl

Download latest webmin using the following command

wget [http://prdownloads.sourceforge.net/webadmin/webmin_1.340_all.deb](http://prdownloads.sourceforge.net/webadmin/webmin_1.340_all.deb)

Now we have webmin_1.340_all.deb package you need to install using the following command

sudo dpkg -i webmin_1.340_all.deb

If your server complains that there is some library things does not find. Just run the following command

sudo apt- get install -f

You should now be able to login to Webmin at the URL [https://localhost:10000/](https://localhost:10000/)

go to webmin login
click on mysql
click change password option,put ur new password.....now on terminal type.

mysql -uroot  -p ..........bingoo......

---

### Post by windependence on 2009-07-11
You'd be better off installing from the repositories. 

Are you aware this thread is over a year old?

-Tim

---

