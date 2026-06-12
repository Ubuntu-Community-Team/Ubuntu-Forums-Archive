---
title: "Apache MySQL PHP installation problem"
date: 2006-03-07
forum: Server Platforms
---

### Post by Bunro on 2006-03-07
I have made use of the great tutorial [https://wiki.ubuntu.com/ApacheMySQLPHP](https://wiki.ubuntu.com/ApacheMySQLPHP)

But my MySQL server is not working.
Apache and PHP are working nicely.
By the way I installed Ubuntu 5.10.
-------------------------------------------------------------------------------------
I am getting the follow message:
root@laptop:/usr# ./bin/mysql_install_db --user=mysql
Installing all prepared tables
060307 11:44:04 /usr/sbin/mysqld: File '/var/log/mysql/mysql-bin.1' not found (E rrcode: 2)
060307 11:44:04 Could not use /var/log/mysql/mysql-bin for logging (error 2). Tu rning logging off for the whole duration of the MySQL server process. To turn it  on again: fix the cause, shutdown the MySQL server and restart it.
060307 11:44:04 /usr/sbin/mysqld: Shutdown Complete


To start mysqld at boot time you have to copy support-files/mysql.server
to the right place for your system

PLEASE REMEMBER TO SET A PASSWORD FOR THE MySQL root USER !
To do so, start the server, then issue the following commands:
/usr/bin/mysqladmin -u root password 'new-password'
/usr/bin/mysqladmin -u root -h laptop password 'new-password'
See the manual for more instructions.

NOTE:  If you are upgrading from a MySQL <= 3.22.10 you should run
the /usr/bin/mysql_fix_privilege_tables. Otherwise you will not be
able to use the new GRANT command!

You can start the MySQL daemon with:
cd /usr ; /usr/bin/mysqld_safe &

You can test the MySQL daemon with the benchmarks in the 'sql-bench' directory:
cd sql-bench ; perl run-all-tests

Please report any problems with the /usr/bin/mysqlbug script!

The latest information about MySQL is available on the web at
[http://www.mysql.com](http://www.mysql.com)
Support MySQL by buying support/licenses at [https://order.mysql.com](https://order.mysql.com)
-------------------------------------------------------------------------------------------------
went I run: /usr/bin/mysqladmin -u root password '***' 
I am getting the following error message:
/usr/bin/mysqladmin: connect to server at 'localhost' failed
error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
-------------------------------------------------------------------------------------------------
When I try to connect to the MySQL server I am getting the following error
ERROR 2002 Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' 
I have read on the forum that this is a permission issue on /var/run/mysqld/ 
So as discribed I changed the following Old status drwxr-xr-x  to new status drwxrwxr-x.
But In my situation it did not solve any thing.
-------------------------------------------------------------------------------------------------
Hopefully there is some who can help me out here.

Best regards, Robert

---

### Post by gmclachl on 2006-03-07
The final 2 error messages appear because the mysqld isn't running. Sounds as if the permissions are a bit fubar. If memory serves me right (it's been a long time since i installed from source) there is a details list of folder permission in the mysql INSTALL file.  

George

---

### Post by Bunro on 2006-03-07
Hi George,

Thanks for your replay.
Do you have any idee where I can find this document?

Regards, Robert

---

### Post by zac1333 on 2006-03-07
I usually follow this tutorial also.  

[http://www.ubuntuguide.org/#databaseserver]("http://www.ubuntuguide.org/#databaseserver")

---

### Post by Bunro on 2006-03-07
Thanks ZAC13333,

For the link these are the exact steps I have dun before.
Any new suggestions? I will reinstall it again.

Regards, Robert

---

### Post by Bunro on 2006-03-07
[https://wiki.ubuntu.com/MYSQL5FromSource](https://wiki.ubuntu.com/MYSQL5FromSource)
under testing I dit the following as discribed:

root@laptop:/home/robert# /usr/bin/mysqld_safe -user=mysql&
[2] 25379
[1]   Exit 127                /usr/local/mysql/bin/mysqld_safe -user=mysql
root@laptop:/home/robert# Starting mysqld daemon with databases from /var/lib/mysql
mysqld_safe[25415]: started
STOPPING server from pid file /var/run/mysqld/mysqld.pid
mysqld_safe[25421]: ended

As you can see the MySQL server is starting but stopping directly!!
Does any body have a clow??

Regards, Robert

---

### Post by gmclachl on 2006-03-08
Hi Bruno,
                   When you downloaded mysql and un-tarred it, there would have been a file inside called INSTALL (or README) if you look in that file there are some detailed install instructions, including the right permissions for the folders. 

 It's also worht mentioning that I run MySQL5 as well, but I didn't install from source i downloaded a package. 

 George

---

### Post by Bunro on 2006-03-08
Hi George,

Thanks for your replay.
I made a new and clean installation and first installed MySQL and assigned a password to it. My system is working fine now!
Thanks for the help!

I have still one question:
I did the following
[https://wiki.ubuntu.com/LocalhostSubdomain](https://wiki.ubuntu.com/LocalhostSubdomain)
sudo gedit /etc/apache2/sites-available/myconfig
<VirtualHost *>
        DocumentRoot /home/username/mysite/
        ServerName laptop 

        <Directory /home/username/mysite/>
                Options Indexes FollowSymLinks MultiViews +Includes
                AllowOverride None
                Order allow,deny
                allow from all
        </Directory>
</VirtualHost>

sudo a2ensite myconfig
sudo /etc/init.d/apache2 restart

I can reach the site via [http://laptop/htmltest.html](http://laptop/htmltest.html) but I get the following:
Forbidden
You don’t have permission to access /htmltest.html on this server.

Does any body have an idée to solve this problem?

Regards, Robert

---

### Post by gmclachl on 2006-03-08
Hi Bruno,
                Sounds like your permissions are wrong. Now I am not 100% sure, but you  will probably need to do the same as when you enable public_html 

  chmod 711 /home/user 
  chmod 755 /home/user/mysite 

  George

---

### Post by Bunro on 2006-03-08
Hi George,

Both are set to 775 already so it should not be the problem?

Regards, Robert

---

### Post by Bunro on 2006-03-08
Hi George,

Sorry I had a big miser!!!
The html file I copied from a windows machine, the permissions where 700.
It is working now!
Thanks for your help and patinas with me.

Regards, Robert

---

### Post by Bunro on 2006-03-13
Sorry wrong post

---

### Post by alcon on 2006-04-29
Hey Bunro, can you tell me exactly how you reinstalled mysql, what package/source distro you used and what steps you took?  I'm having the exact same problem that you did, I've been bashing my head against it for several days with no luck.  I tried clean installing mysql several times.  Tried installing from source.  Tried installing apache and php from source as well, nothings working for me.  I'd really appreciate instructions for how to get it running.  Thanks, Alcon

---

### Post by TreetopClimber on 2006-04-29
follow the directions from this link, [https://wiki.ubuntu.com/ApacheMySQLPHP](https://wiki.ubuntu.com/ApacheMySQLPHP)

---

### Post by alcon on 2006-04-29
That was the first thing I tried.  That's where I ended up with this problem.

---

### Post by TreetopClimber on 2006-04-30
I see ... well I have re-installed this ubuntu 5.10 several times I believe I am on #8 and used those directions and everytime it has worked. Are you sure you have typed things correctly? I am a n00b at this linux stuff but everything that I have read and used seems to have worked. Also make sure you check your Synaptic Package Manager> repository> settings> and click the breezy badger (binary) then add and set all those selections, then click on the (source) and do the same. this is the only other thing I know that needs to be set. then download and install the new packages

---

### Post by Bunro on 2006-10-24
Sorry for my late reaction!
 

 After a clean installation of Ubuntu.
 I installed the following packages with Synaptic Package Manager.
 Apache2
 php5-mysql
 libapache2-mod-php5
 mysql-server
 libapache2-mod-auth-mysql
 php5-gd
 php5-curl
 

 pphpmyadmin
 

 As discribed here:
 [https://wiki.ubuntu.com/ApacheMySQLPHP](https://wiki.ubuntu.com/ApacheMySQLPHP)
 

 Hopefully it can still help you and/or some one els.
 

 Best regards, Robert

---

