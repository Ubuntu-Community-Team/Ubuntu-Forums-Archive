---
title: "MySQL multiple instances in Ubuntu Server"
date: 2009-05-09
forum: Tutorials
---

### Post by mauroferreira on 2009-05-09
Tested by the author with mysql 5.1.30 and 5.1.34 in Ubuntu 8.10 and 9.04. Anyway, no guaranties of any kind: worked for me, that's all.

There are 2 cases where multiple instances of the same version of mysql in a server are necessary, or desirable:

You truly need A LOT of simultaneous connections for read-only and just one for write on the same database: in this case, you **must know ****very well what you are doing**, and be capable of develop applications that read from a read-only instance and write into a write-only instance. There can be variations, but the principle is the same: in a given time interval or moment, just one database engine instance can have write permission over a given information (database, table, field, etc). It's very like an one-machine-cluster. Sounds complex AND IT IS ! So, can't be described in just any howto.

The second cause is very trivial: you want or need to have multiple development versions of the same database(s) in the same machine and with the same name, and maybe (not recommended but still possible) a production version too. _**THIS**_ is the scope of this howto.

First, install mysql: you will found lots of explanations about in this forum and in the Internet. Just Google 'ubuntu mysql install' or 'ubuntu mysql 5.1 install' and be flooded by explanations for every known taste, and more :)

BEFORE START: Read twice or more times, and just start doing after understand the entire sequence, and then do it, checking every step. I tried hard to make this howto very linear and as simple as possible, but nothing (made by men) is foolproof. As this text isn't. Any **constructive** comment will be **welcome**.

Well, assuming that you have mysql installed, let's start.

As near all steps need root privileges, let's simplify things, working in a root privileged bash instance:

[FONT=courier new]# [/FONT]**sudo bash**
*(enter the password when asked for)*

Now, let's find some files we will need:

*(the following command line is just for ensure that locate will give a proper response :)* )
[FONT=courier new]# [/FONT][COLOR=Green]**[COLOR=#000000][FONT=courier new]updatedb[/FONT][/COLOR]**[/COLOR]

*(let's find the scripts we need)*
[FONT=courier new]# [/FONT]**[FONT=courier new]locate mysqld_multi[/FONT]**
 [FONT=courier new]/usr/bin/mysqld_multi[/FONT]
[FONT=courier new]/usr/share/man/man1/mysqld_multi.1.gz[/FONT]
 [FONT=courier new]/usr/share/mysql/mysqld_multi.server[/FONT]
[FONT=courier new]#[/FONT]
 
Bingo ! The first one is a Perl script that 'does the job'; the second is a man page (try 'man mysqld_multi' ;) ), and the third is a script to start/stop/etc the mysqld instances.

Now, let's prepare the automatic running of the mysqld instances:

*(**the following command line is **just for the sake of reversibility :)* )
 [FONT=courier new]# **mv /etc/init.d/mysql /etc/init.d/mysql_mono.server**[/FONT]

And then:

[FONT=courier new]# **cp /usr/share/mysql/mysqld_multi.server /etc/init.d/mysql**[/FONT]

With your favourite text editor, edit **/etc/init.d/mysql,** then find the lines:

[FONT=courier new]basedir=/usr/local/mysql[/FONT]
 [FONT=courier new]bindir=/usr/local/mysql/bin            [/FONT]

 and change to:

[FONT=courier new]basedir=/usr            [/FONT]
 [FONT=courier new]bindir=/usr/bin            [/FONT]

If your have a [FONT=courier new]root[/FONT] password in [FONT=courier new]localhost[/FONT], edit the file **[FONT=courier new]/usr/bin/mysqld_multi[/FONT]**, then find the line:

[FONT=courier new]$opt_password = undef()[/FONT]

and change to:

 [FONT=courier new]$opt_password = "password"
[/FONT]
changing "password" by the 'root'@'localhost' password. (thank's, [ecentinela]("http://ubuntuforums.org/member.php?u=98940") ;) ).

Now create a database directory for each additional mysqld instance:

[FONT=courier new]# **cp -pr /var/lib/mysql /var/lib/mysql[COLOR=Red]1[/COLOR]**[/FONT]
 [FONT=courier new]# **cp -pr /var/lib/mysql /var/lib/mysql[COLOR=Red]2[/COLOR]**[/FONT]

And so on... *(yep, the **/var/lib/mysql** folder and it's contents stay untouched, for the sake of reversibility or to help in make more instances or 'reset' a existent one)*.

Now we are going to explain to the mysqld_multi perl script about the mysqld instances that we want to have:

*(**the following command line is **just for the sake of reversibility:)*
[FONT=courier new]# **cp -p /etc/mysql/my.cnf /etc/my.cnf.mono**[/FONT]

Next, with your favourite text editor, edit **/etc/mysql/my.cnf** to have [mysqld1], [mysqld2], etc. sessions instead of the [mysqld] one. The [mysqld[COLOR=Red]#[/COLOR]] *(where [COLOR=Red]#[/COLOR] is the instance number)* lines that need to be changed, in order to tell to the mysqld instances about directories, files, sockets and tcp ports to use, are:

[COLOR=Silver][FONT=courier new][COLOR=Black]user            = root[/COLOR][/FONT]
[/COLOR][FONT=courier new]pid-file        = /var/run/mysqld[COLOR=Red]#[/COLOR].pid [/FONT]
 [FONT=courier new]socket          = /var/run/mysqld[COLOR=Red]#[/COLOR].sock[/FONT]
[FONT=courier new]port            = 330[COLOR=Red]#[/COLOR][/FONT]
 [FONT=courier new]datadir         = /var/lib/mysql[/FONT][COLOR=Red]#[/COLOR]
[FONT=courier new]log             = /var/log/mysql/mysql[COLOR=Red]#[/COLOR].log[/FONT]
 [FONT=courier new]log_bin         = /var/log/mysql/mysql[COLOR=Red]#[/COLOR]-bin.log[/FONT]
[FONT=courier new]server-id       = [COLOR=Red]#[/COLOR][/FONT]
 
Notes: 1) server-id isn't necessary, but sometimes is nice to know in what instance the application, procedure or trigger is going over just doing a '**[FONT=Courier New]SELECT @@server_id[/FONT]**', and
            2) the [FONT=Courier New]user = root[/FONT] line is to assure that the mysql daemons will have enough rights to create the socket, pid and log files.

Just to give an example, my **/etc/mysql/my.cnf** look like:

[COLOR=Silver]...
[FONT=courier new]nice            = 0[/FONT]
[/COLOR]
[FONT=courier new][mysqld[COLOR=Red]**1**[/COLOR]][/FONT]
 [COLOR=Silver][FONT=courier new][COLOR=Black]user            = root[/COLOR][/FONT]
[/COLOR][FONT=courier new]pid-file        = /var/run/mysqld[COLOR=Red]**1**[/COLOR].pid [/FONT]
 [FONT=courier new]socket          = /var/run/mysqld[COLOR=Red]**1**[/COLOR].sock[/FONT]
[FONT=courier new]port            = 330[COLOR=Red]**1**[/COLOR][/FONT]
 [COLOR=Silver][FONT=courier new]basedir         = /usr[/FONT]
[/COLOR][FONT=courier new]datadir         = /var/lib/mysql[COLOR=Red]**1**[/COLOR][/FONT]
 [COLOR=Silver][FONT=courier new]tmpdir          = /tmp[/FONT]
[FONT=courier new]language        = /usr/share/mysql/english[/FONT]
[FONT=courier new]old_passwords   = 1[/FONT]
[FONT=courier new]key_buffer              = 16M [/FONT]
[FONT=courier new]max_allowed_packet      = 16M [/FONT]
[FONT=courier new]thread_stack            = 128K[/FONT]
[FONT=courier new]thread_cache_size       = 8[/FONT]
[FONT=courier new]myisam-recover         = BACKUP[/FONT]
[FONT=courier new]query_cache_limit       = 1M [/FONT]
[FONT=courier new]query_cache_size        = 16M[/FONT]
[/COLOR]     [FONT=courier new]log                     = /var/log/mysql/mysql[COLOR=Red]**1**[/COLOR].log[/FONT]
[FONT=courier new]server-id               = [COLOR=Red]**1**[/COLOR][/FONT]
 [FONT=courier new]log_bin                 = /var/log/mysql/mysql[COLOR=Red]**1**[/COLOR]-bin.log[/FONT]
[COLOR=Silver][FONT=courier new]expire_logs_days        = 10  [/FONT]
[FONT=courier new]max_binlog_size         = 100M[/FONT]
[/COLOR] 
[FONT=courier new][mysqld[COLOR=Red]**2**[/COLOR]][/FONT]
 [COLOR=Silver][FONT=courier new][COLOR=Black]user            = root[/COLOR][/FONT]
[/COLOR][FONT=courier new]pid-file        = /var/run/mysqld[COLOR=Red]**2**[/COLOR].pid [/FONT]
 [FONT=courier new]socket          = /var/run/mysqld[COLOR=Red]**2**[/COLOR].sock[/FONT]
[FONT=courier new]port            = 330[COLOR=Red]**2**[/COLOR][/FONT]
 [COLOR=Silver][FONT=courier new]basedir         = /usr[/FONT]
[/COLOR][FONT=courier new]datadir         = /var/lib/mysql[COLOR=Red]**2**[/COLOR][/FONT]
 [COLOR=Silver][FONT=courier new]tmpdir          = /tmp[/FONT]
[FONT=courier new]language        = /usr/share/mysql/english[/FONT]
[FONT=courier new]old_passwords   = 1[/FONT]
[FONT=courier new]key_buffer              = 16M [/FONT]
[FONT=courier new]max_allowed_packet      = 16M [/FONT]
[FONT=courier new]thread_stack            = 128K[/FONT]
[FONT=courier new]thread_cache_size       = 8[/FONT]
[FONT=courier new]myisam-recover          = BACKUP[/FONT]
[FONT=courier new]query_cache_limit       = 1M [/FONT]
[FONT=courier new]query_cache_size        = 16M[/FONT]
[/COLOR]     [FONT=courier new]log                     = /var/log/mysql/mysql[COLOR=Red]**2**[/COLOR].log[/FONT]
[FONT=courier new]server-id               = [COLOR=Red]**2**[/COLOR][/FONT]
 [FONT=courier new]log_bin                 = /var/log/mysql/mysql[COLOR=Red]**2**[/COLOR]-bin.log[/FONT]
[COLOR=Silver][FONT=courier new]expire_logs_days        = 10  [/FONT]
[FONT=courier new]max_binlog_size         = 100M[/FONT]
[/COLOR] 
[COLOR=Silver][FONT=courier new][mysqldump][/FONT]
[FONT=courier new]...[/FONT]
[/COLOR] 
Note: texts in light gray are just for show that can be another parameters, and not to be copied: use your own parameters or those found in the my.cnf that is installed by default, as this file can change (and usually changes) for each mysql version: any not yet (or no more) recognized parameter can and do stop a mysql daemon at its start.

Now, let's start the instances:

[FONT=courier new]# **/etc/init.d/mysql start**[/FONT]

And then, if you did all right, the instances will silently run. Just for peace of mind, if you do:

[FONT=courier new]# **ps aux | grep mysql | grep -v grep**[/FONT]

will appear a big entry for each instance. In my case, it is:

[FONT=courier new]# **ps aux | grep mysql | grep -v grep**[/FONT]
[FONT=courier new]mysql 8395 0.0 2.0 158832 20768 pts/1 Sl 12:41 0:00 /usr/sbin/mysqld --no-defaults --user=mysql --pid-file=/var/run/mysqld1.pid[/FONT]  [FONT=courier new]--socket=/var/run/mysqld1.sock --port=3301 --basedir=/usr --datadir=/var/lib/mysql1 --tmpdir=/tmp --language=/usr/share/mysql/english [/FONT][FONT=courier new]--old_passwords=1 --key_buffer=16M --max_allowed_packet=16M --thread_stack=128K --thread_cache_size=8 --myisam-recover=BACKUP --query_cache_limit=1M [/FONT][FONT=courier new]--query_cache_size=16M --log=/var/log/mysql/mysql1.log --server-id=1 ...[/FONT]
[FONT=courier new]mysql 8400 0.0 2.0 224368 20768 pts/1 Sl 12:41 0:00 /usr/sbin/mysqld --no-defaults --user=mysql --pid-file=/var/run/mysqld2.pid [/FONT][FONT=courier new]--socket=/var/run/mysqld2.sock --port=3302 --basedir=/usr --datadir=/var/lib/mysql2 --tmpdir=/tmp --language=/usr/share/mysql/english[/FONT]  [FONT=courier new]--old_passwords=1 --key_buffer=16M --max_allowed_packet=16M --thread_stack=128K --thread_cache_size=8 --myisam-recover=BACKUP --query_cache_limit=1M[/FONT]
 [FONT=courier new] --query_cache_size=16M --log=/var/log/mysql/mysql2.log --server-id=2 ..[/FONT]
[FONT=courier new]# [/FONT]
 
From now, to use the mysql console you need to add the socket in the command line:

[FONT=courier new]# **mysql --socket=/var/run/mysqld[COLOR=Red]#[/COLOR].sock** 
*(where [COLOR=Red]#[/COLOR] is the mysqld instance number)*[/FONT]
 
...quite lengthy, huh ? Well, let's simplify this.
With your favourite text editor, edit *(create)* **/usr/sbin/mysql1**, and put the following lines on it:

[FONT=Courier New]#!/bin/bash
mysql --socket=/var/run/mysqld[COLOR=Red]**1**[/COLOR].sock $1 $2 $3 $4 $5 $6 $7 $8
[/FONT] 
Now, make the /usr/sbin/mysql1 file executable:

[FONT=courier new]# **chmod a+x /usr/sbin/mysql[COLOR=Red]1[/COLOR]**[/FONT]

Now, to invoke a console for the first mysqld instance, just type:

[FONT=courier new]# **mysql[COLOR=Red]1[/COLOR]**[/FONT]
[FONT=Courier New]Welcome to the MySQL monitor.  Commands end with ; or \g.
Your MySQL connection id is 4
Server version: 5.1.34-0.dotdeb.1-log (Debian)

Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

mysql> **select @@server_id;**
+-------------+
| @@server_id |
+-------------+
|                               [COLOR=Red]**1**[/COLOR] | 
+-------------+
1 row in set (0.00 sec)

mysql> ***(ctr+D)*** Aborted
[/FONT]
Now, make copies for each of the other mysqld instances:

[FONT=Courier New][FONT=courier new]# **cp /usr/sbin/mysql[COLOR=Red]1[/COLOR] /usr/sbin/mysql[COLOR=Red]#[/COLOR]**[/FONT]
[/FONT]
And edit each **/usr/sbin/mysql[COLOR=Red]#[/COLOR]** to ajust to the right socket(s):

[FONT=Courier New][FONT=courier new]#!/bin/bash[/FONT]
[FONT=courier new]mysql --socket=/var/run/mysqld**[COLOR=Red]#[/COLOR]**.sock $1 $2 $3 $4 $5 $6 $7 $8[/FONT]
[/FONT] 
And so on, for each additional mysqld instance you may have. Btw, the $1 thru $8 are parameters that you may use, like -uroot, -p'mysecret', mydatabase and so, just the same as for the mysql console.

Finally, to stop the root privileged bash:

[FONT=Courier New]# **ctrl+D**[/FONT]

And now, you (finally) have your mysqld multiple instances ready for use.

Technical explanations about, and examples to start/stop selected mysqld instances can be found at:
[http://dev.mysql.com/doc/refman/5.1/en/mysqld-multi.html](http://dev.mysql.com/doc/refman/5.1/en/mysqld-multi.html)

Now, have fun ! Or work, or whatever...

Mauro M. Ferreira
IPVoxVoIP

---

### Post by jpeddicord on 2009-05-12
Approved; thank you for your Tutorials & Tips contribution! :)

---

### Post by ecentinela on 2009-06-17
Thanks for the tutorial, it works... but after a reboot the mysql server is not starting anymore.

Someone can help me with this?

Thanks.

---

### Post by ecentinela on 2009-06-18
After some testing I have seen that the problem is the that the folder /var/run/mysqld is removed every time I reboot the system.
After the reboot, I can create the folder, give it permissions and start mysql normally.

Someone knows why this is occurring?

The second problem that I have now, is that I can't stop mysql server (only rebooting the system). I'm logged as root, but in the mysql log file I get this when I type (as root) "/etc/init.d/mysql stop"

090618  8:22:29       1 Connect     Access denied for user 'root'@'localhost' (using password: NO)

Please, I need this urgently.

Thank you

---

### Post by mauroferreira on 2009-06-18
About the 'root'@'localhost' user with password:

Edit the file /usr/bin/mysqld_multi, and change the line:

$opt_password    = undef();

To:

$opt_password    = "password";

Changing "password" by the user 'root'@'localhost' password.

HowTo changed to reflect this. Thanks for your valuable contribution !

About the /var/run/mysqld directory being deleted after the first time mysqld stops:

This isn't done by /usr/bin/mysqld_multi; probably a mysql or mysqladmin bug, i'll go after it's sources to search about.

---

### Post by ecentinela on 2009-06-18
Thanks!

Another way to "solve" the folder remove bug is to change the path for the pid and socket from "/var/run/mysqld/" to "/var/run/" and change the mysql user on my.cnf from "mysql" to "root".

Is the best way I have found at this time to don't need to create the folder after every reboot.

Hope it helps!

---

### Post by mauroferreira on 2009-06-18
Nice one ! I'll change the HowTo to reflect this. Thanks again, ecentinela !

---

### Post by southplatte on 2009-06-30
Hello,

I have recently found a need to run two MySQL instances on one box.  I had just performed a clean install of Ubuntu 9.04 and chose the LAMP option during the install just to speed up the process.

After finding your tutorial, I have found that I cannot, no matter what I have tried, get it to work.

The problem is, it starts the two servers, but then immediately shuts them down, without logging any errors in any of the log files.

I am, at this time, going to try to clean install the OS again, then instead of choosing the LAMP stack during the Ubuntu install, I plan on install MySQL first, then Apache, then PHP from the Ubuntu packages.

Have you ever seen why this config you wrote up would start the servers, then shut them down immediately all without any logged errors and all with out any errors to the console?

Thanks for the tutorial - am still trying and hope to shed light in case someone else is experiencing this same error.

Oh, the only difference I have noticed is I tried it with MySQL 5.1.31 rather 5.1.34 because that is what Ubuntu repositories said was the most recent version during the ***apt-get install mysql-server-5.1***.

---

### Post by mauroferreira on 2009-06-30
About MySQL version, this is not a problem, er - not a _direct_ one: the HowTo texts in gray are just for show that can be another parameters, and not to be copied: use your own parameters or those found in the my.cnf that is installed by default, as this file can change (and usually changes) for each mysql version: any not yet (or no more) recognized parameter can and do stop a mysql daemon at its start.

If this don't fix the problem, check the "[FONT=Courier New]user=[/FONT]" lines in [FONT=Courier New]/etc/mysql/my.cnf[/FONT]; all must be "[FONT=Courier New]user=root[/FONT]", else the mysql daemons will not be able to create the socket files, and then will silently shutdown.

Please return information about what you found and / or discovered: this is valuable to improve this HowTo.

---

### Post by szemere on 2009-07-17
Thanks!

However I had some problems with Apparmor refusing access to new data directories and sockets. This caused init-script to fail silently. 

Allowing these directories and socket creation from apparmor configs fixed the problem though. Also "user=mysql" now also works as expected.

---

### Post by linkrjr on 2009-07-26
Hi all,

I have followed this tutorial step-by-step and I am sure I haven't missed any step but I still cannot get it to work.

I am sure I am having problems with pid and socket files and the datadir.

When I set the datadir to the original folder /var/lib/mysql and use the original pid and socket file, the instance starts correctly but if I change to what the tutorial suggests (/var/lib/mysql1 - /var/run/mysqld/mysqld1.pid and /var/run/mysqld/mysqld1.sock), nothing works.

One doubt, might be stupid but, do I need to install mysql twice, one for each pair of pid and socket?

I have only installed mysql once using apt-get and then tried the tutorial.

Do you guys have any idea what I am doing wrong?

Any help is very much appreciated.

---

### Post by erll on 2009-10-15
I got bit by apparmor as well. 

I modified the file:

/etc/apparmor.d/usr.sbin.mysqld to contain:

  /var/lib/mysql?/ r,
  /var/lib/mysql?/** rwk,
  /var/log/mysql/ r,
  /var/log/mysql/** rw,
  /var/run/mysqld/mysqld?.pid w,
  /var/run/mysqld/mysqld?.sock w,

And then restarted apparmor (/etc/init.d/apparmor restart), and now I can start databases with mysqld_multi etc.

Thanks for the howto.

/Erland

---

### Post by erll on 2009-10-15
Also, having the myql database root password in the publicly readable file /usr/bin/mysqld_multi seems like a bad idea, so I did chmod o-rx /usr/bin/mysqld_multi.

---

### Post by peridot on 2009-10-19
You shouldn't be running mysql as root. If someone managed a database exploit, they'd have root permissions. Take the time to figure out where permissions are going wrong.

---

### Post by mcksmith on 2009-12-20
This tutorial was great, since I need to run two mysql servers on my dev server (one for each virtual host), but I didn't want to run mysql as root, or disable apparmor.

*[edit]* About the third time through the mysqld_multi man, I realized that the start of the example my.conf file had these lines for a [mysqld_multi] block, so I changed them to fit my environment:
```

[mysqld_multi]
mysqld = /usr/bin/mysqd_safe
mysqladmin = /usr/bin/mysqladmin
user = root

```Note that the example code has user "multi_admin" and password "multipass", and requires user "multi_pass" to have an account for each MySQL server with shutdown priveleges; therefore, I just used user root in the mysqld_mutil block since the servers themselves run as mysql and not root. This "fixes" the problem of not being able to recreate the /var/run/mysqld directory on startup, without having to run the servers as root. Which, as correctly pointed out above, is a bad idea.*[/edit]*

These were the other changes:
 
I did not edit [B][FONT=courier new]/usr/bin/mysqld_multi[FONT=Arial] 
[/FONT][/FONT][/B]
As mentioned earlier, I changed these four lines in [FONT=Courier New]/etc/apparmor.d/usr.sbin.mysq[/FONT]l to:
```

/var/lib/mysql[COLOR=Red]?[/COLOR]/ r,
/var/lib/mysql[COLOR=Red]?[/COLOR]/** rwk,
/var/run/mysqld/mysqld[COLOR=Red]?[/COLOR].pid w,
/var/run/mysqld/mysqld[COLOR=Red]?[/COLOR].sock w,
```And finally, my [FONT=Courier New]/etc/mysql/my.cn[/FONT]f file is:
```

[mysqld[COLOR=Red]1[/COLOR]]
user      = mysql
pid-file  = /tmp/mysqld[COLOR=Red]1[/COLOR].pid
socket    = /var/run/mysqld/mysqld[COLOR=Red]1[/COLOR].sock
port      = 330[COLOR=Red]1[/COLOR]
datadir   = /var/lib/mysql[COLOR=Red]1[/COLOR]
server-id = [COLOR=Red]1[/COLOR]
``` (only the pertinent lines shown above, and code repeated for each server).

I haven't done extensive testing, but as far as I can tell, everything is working correctly. i.e. after a reboot I can login to both servers, and mysql doesn't have to run as root.

---

### Post by JoeSabido on 2012-12-23
Great write-up!

It works perfectly but I have a problem, it won't start on boot.

I'm using Ubuntu 12 64bit, and apparmor was uninstalled before starting the procedure so I don't think that's the problem.

I don't see anything in the system log or mysql log.

After boot, I can start it just fine using 

sudo /etc/init.d/mysql start

Any ideas? I really need this to work so I can replace my Windows server with this!!

**EDIT: I just tried with 10.04 and I get the same behavior.

---

### Post by JoeSabido on 2012-12-23
I  made it run on startup by editing the file

/etc/init.d/rc.local

and adding the line "/etc/init.d/mysql start"

It works now, the instances start on boot, but is this the solution? Or is it not the right thing to do?

---

### Post by Kissell on 2013-02-19
When I run /etc/init.d/mysql start

I can see the processes running:
> 
root      5979     1  1 11:00 pts/0    00:00:00 /bin/sh /usr/bin/mysqld_safe --user=root --pid-file=/tmp/mysqld1.pid --socket=/var/run/mysqld/mysqld1.sock --port=3301 --basedir=/usr --datadir=/var/lib/mysql1 --tmpdir=/tmp --language=/usr/share/mysql/english --old_passwords=1 --key_buffer=16M --max_allowed_packet=16M --thread_stack=128K --thread_cache_size=8 --myisam-recover=BACKUP --query_cache_limit=1M --query_cache_size=16M --log=/var/log/mysql/mysql1.log --server-id=1 --log_bin=/var/log/mysql/mysql1-bin.log --expire_logs_days=10 --max_binlog_size=100M

root      5986     1  1 11:00 pts/0    00:00:00 /bin/sh /usr/bin/mysqld_safe --user=root --pid-file=/tmp/mysqld2.pid --socket=/var/run/mysqld/mysqld2.sock --port=3302 --basedir=/usr --datadir=/var/lib/mysql2 --tmpdir=/tmp --language=/usr/share/mysql/english --old_passwords=1 --key_buffer=16M --max_allowed_packet=16M --thread_stack=128K --thread_cache_size=8 --myisam-recover=BACKUP --query_cache_limit=1M --query_cache_size=16M --log=/var/log/mysql/mysql2.log --server-id=2 --log_bin=/var/log/mysql/mysql2-bin.log --expire_logs_days=10 --max_binlog_size=100M


But then a few seconds later they disappear and I don't seee anything in the log about it stopping or any errors.

---

### Post by klodoma on 2013-06-18
On my ubuntu(Ubuntu 10.04.4 LTS):

/var/run/mysqld1.pid
/var/run/mysqld1.sock are wrong. 

Also the user should be mysql and not root. 
Here is the config I use:

```


[mysqld1]
user = mysql
pid-file = /var/run/mysqld/mysqld1.pid
socket = /var/run/mysqld/mysqld1.sock
port = 3306
basedir = /usr
datadir = /var/lib/mysql1
tmpdir = /tmp
language = /usr/share/mysql/english
old_passwords = 1
key_buffer = 16M
max_allowed_packet = 16M
thread_stack = 128K
thread_cache_size = 8
myisam-recover = BACKUP
query_cache_limit = 1M
query_cache_size = 16M
log = /var/log/mysql/mysql1.log
server-id = 1
log_bin = /var/log/mysql/mysql1-bin.log
log_error = /var/log/mysql/error1.log
expire_logs_days = 10
max_binlog_size = 100M

[mysqld2]
user = mysql
pid-file = /var/run/mysqld/mysqld2.pid
socket = /var/run/mysqld/mysqld2.sock
port = 3307
basedir = /usr
datadir = /var/lib/mysql2
tmpdir = /tmp
language = /usr/share/mysql/english
old_passwords = 1
key_buffer = 16M
max_allowed_packet = 16M
thread_stack = 128K
thread_cache_size = 8
myisam-recover = BACKUP
query_cache_limit = 1M
query_cache_size = 16M
log = /var/log/mysql/mysql2.log
server-id = 2
log_bin = /var/log/mysql/mysql2-bin.log
log_error = /var/log/mysql/error2.log
expire_logs_days = 10
max_binlog_size = 100M

```

---

### Post by tnsilver on 2013-06-26
Using kubuntu 13.04 I was not able to get apparmor to allow the socket and pid files to be written anywhere, I've set permissions on /tmp, /var, /var/run etc.. to no effect. Nor was I able to instruct apparmor (as explained in this thread) to allow this. I tried all the tips in all the relevant posts here to no effect. Perhaps the apparmor syntax changed??? Upgraded??? Who knows... Too much reading to do in too short a time.

**Soultion A:**

My first solution was to disable apparmor using these commands (under root or with sudo):

```

## run as root or use sudo
## stop apparmor
/etc/init.d/apparmor stop
/etc/init.d/apparmor teardown

## start mysqld_multi
mysqld_multi start

##verify mysql instances up and running
ps aux | grep mysql | grep -v grep
```

This worked but the init.d script would not start so I had to run this manually after each reboot or login

[B]Soultion B:

[/B]With this approach you can run mysqld using your user 'root', or the better 'mysql' user. It's not an issue anymore since we will disable apparmor to stop protecting locations on the file system for the *usr.sbin.mysqld* profile. There is a package called *apparmor-utils* you will need to install, and then use the *aa-complain* command to make apparmor 'complain' instead of blocking the *usr.sbin.mysqld* profile

```

## run as root or use sudo
## install apparmor-utils
apt-get install apparmor-utils
```

Now you can instruct apparmor to complain about the *usr.sbin.mysqld* profile

```

## run as root or use sudo
aa-complain /usr/sbin/mysqld

```

Once this is done apparmor will echo the status of the profiles and you will be able to see the *usr.sbin.mysqld *profile is in complain mode*:*

```

## run as root or use sudo
/etc/init.d/apparmor status
```

This will show something like:

```
apparmor module is loaded.
6 profiles are loaded.
5 profiles are in enforce mode.
   /sbin/dhclient
   /usr/lib/NetworkManager/nm-dhcp-client.action
   /usr/lib/connman/scripts/dhclient-script
   /usr/lib/cups/backend/cups-pdf
   /usr/sbin/cupsd
1 profiles are in complain mode.
   /usr/sbin/mysqld
4 processes have profiles defined.
2 processes are in enforce mode.
   /sbin/dhclient (2043) 
   /usr/sbin/cupsd (1113) 

```

Next, you'll want to let init.d  run the mysql script in /etc/init.d on startup. This is done with:

```
## run as root or use sudo
update-rc.d mysql defaults
```

You can now reboot and have your instances up and running properly. 

The /etc/init.d/mysql script calls mysqld_multi and looks like this

```
#!/bin/sh
#
# A simple startup script for mysqld_multi by Tim Smith and Jani Tolonen.
# This script assumes that my.cnf file exists either in /etc/my.cnf or
# /root/.my.cnf and has groups [mysqld_multi] and [mysqldN]. See the
# mysqld_multi documentation for detailed instructions.
#
# This script can be used as /etc/init.d/mysql.server
#
# Comments to support chkconfig on RedHat Linux
# chkconfig: 2345 64 36
# description: A very fast and reliable SQL database engine.
#
# Version 1.0
#

basedir=/usr/
bindir=/usr/bin

if test -x $bindir/mysqld_multi
then
  mysqld_multi="$bindir/mysqld_multi";
else
  echo "Can't execute $bindir/mysqld_multi from dir $basedir";
  exit;
fi

case "$1" in
    'start' )
        "$mysqld_multi" start $2
        ;;
    'stop' )
        "$mysqld_multi" stop $2
        ;;
    'report' )
        "$mysqld_multi" report $2
        ;;
    'restart' )
        "$mysqld_multi" stop $2
        "$mysqld_multi" start $2
        ;;
    *)
        echo "Usage: $0 {start|stop|report|restart}" >&2
        ;;
esac

```

Good luck!

---

