---
title: "HOWTO Mysql5 from source"
date: 2005-11-22
forum: Server Platforms
---

### Post by dudus on 2005-11-22
This is my first Howto, so be kind to me an to my poor english.

I also added this to the wiki [here]("https://wiki.ubuntu.com/MYSQL5FromSource").


[B]
[SIZE="4"]Prerequisites[/SIZE][/B]

_[SIZE="3"]You must download MYSQL5 (of course ;)[/SIZE]_

```
wget http://dev.mysql.com/get/Downloads/MySQL-5.0/mysql-5.0.16.tar.gz/from/http://mysql.localhost.net.ar/
tar xzvf mysql-5.0.16.tar.gz
cd mysql-5.0.16/
```
[U]
[SIZE="3"]You must install packages[/SIZE][/U]

```
sudo apt-get install make build-essential
```

_[SIZE="3"]You need development libraries[/SIZE]_

... but I'm not sure about witch ones.


**[SIZE="4"]Compilation optimisation[/SIZE]**


You can speed up Mysql with processor optimisation

If you have a different processor, change the CHOST, CFLAGS, CXXFLAGS.

If you don't know what it is, Take the Generic one!

The configuration for specific processors were not tested. If it compiles you're fine. If it doesn't try the generic one.Use only one of the following three

[SIZE="3"]
_Athlon-tbird XP (AMD)[/SIZE]_
```

export CHOST="i686-pc-linux-gnu"
export CFLAGS="-march=athlon-xp -O3 -pipe -fomit-frame-pointer -msse -mmmx  -mfpmath=sse"
 -fomit-frame-pointer -msse -mmmx -mfpmath=sse"
export CXXFLAGS="-march=athlon-xp -O3 -pipe -fomit-frame-pointer -msse -mmmx -mfpmath=sse -felide-constructors -fno-exceptions -fno-rtti"
export CXX=gcc
```


_[SIZE="3"]Pentium 4 (Intel)[/SIZE]_
```

export CHOST="i686-pc-linux-gnu"
export CFLAGS="-march=pentium4 -mcpu=pentium4 -O3 -pipe -fomit-frame-pointer -msse -mmmx  -mfpmath=sse"
export CXXFLAGS="-march=pentium4 -mcpu=pentium4 -O3 -pipe -fomit-frame-pointer -msse -mmmx -mfpmath=sse -felide-constructors -fno-exceptions -fno-rtti"
export CXX=gcc
```

_[SIZE="3"] Generic[/SIZE]_
```

export CHOST="i686-pc-linux-gnu"
export CFLAGS="-mcpu=i686 -march=i686 -O3 -pipe -fomit-frame-pointer"
export CXX=gcc

```

-fomit-frame-pointer should be omitted if you intend to debug. Otherwise leave it as it make mysql faster.

**[SIZE="4"]Configuration[/SIZE]**

This is a full configuration.

Do it in the MYSQL5 folder.

You can add/delete some of the options if you don't need it. This is intended to be a default mysql5 installation, again I'm not sure about this.

```
./configure \
--prefix=/usr/local/mysql \
--with-mysqld-user=mysql \
--without-debug \
--with-client-ldflags=-all-static \
--with-mysqld-ldflags=-all-static \
--disable-shared \
--localstatedir=/usr/local/mysql/data \
--with-extra-charsets=none \
--enable-assembler \
--with-unix-socket-path=/tmp/mysql.socket

make
sudo make install
```

This will install mysql in /usr/local/mysql and data in /usr/local/mysql/data.

[U]
[SIZE="3"] my.conf [/SIZE][/U]
Now create the conf based in any of the pre-build confs. For small servers I recomend my-medium.cnf

```

sudo cp support-files/my-medium.cnf /etc/my.cnf

```

You should edit this file for your needs.

[U]
[SIZE="3"] Create GRANT tables [/SIZE][/U]
You must create the GRANT tables, and there is a very easy way to do so.
```

sudo /usr/local/mysql/bin/mysql_install_db --user=mysql

```

[U]
[SIZE="3"] Changing Owners [/SIZE][/U]
```

sudo chown -R root /usr/local/mysql
sudo chown -R mysql /usr/local/mysql/var
sudo chgrp -R mysql /usr/local/mysql

```

**[SIZE="4"]Testing[/SIZE]**

```

/usr/local/mysql/bin/mysqld_safe &
/usr/local/mysql/bin/mysql
```

You should add /usr/local/path/bin to your path so you can always use mysql, mysqldump, mysqladmin and some others right from the shell.

**[SIZE="4"]Starting Mysql at boot time[/SIZE]**


```
sudo cp support-files/mysql.server /etc/init.d/mysql
sudo chmod +x /etc/init.d/mysql
sudo update-rc.d mysql defaults

```
When you restart mysql should be up if everything went ok.

---

### Post by behnam_re on 2005-11-30
For all who had the same Prolem like me :

If you get some error like this :
No curses/termcap library found

configure you're Source Distribution with the
option --with-named-curses-
libs=/your/path/to/lib/libncurses.so.5.0

---

### Post by LordHunter317 on 2005-11-30
I should point out that while fast, that configuration isn't suited to any sort of genearl production situation, and shouldn't be used unless you no exactly what you're doing.

And if you have to ask, then no, you don't know what you're doing.

---

### Post by behnam_re on 2005-11-30
--with-named-curses-libs=/usr/lib/libncurses.a

---

### Post by dudus on 2005-11-30
[QUOTE=LordHunter317]I should point out that while fast, that configuration isn't suited to any sort of genearl production situation, and shouldn't be used unless you no exactly what you're doing.

And if you have to ask, then no, you don't know what you're doing.[/QUOTE]

I'm not an expert, and I had a realy hard time figuring this configuration out, couse I found no infos about mysql5 in Ubuntu at all. I'm using this in a production environment. And had no issues with this yet.

My propose was to make a configuration that was default, being both usefull for any situation and fast.

Maybe you could show you're point about why this isn't suited to production situations. And we could work on this to make it more usable.

---

### Post by LordHunter317 on 2005-11-30
[QUOTE=dudus]Maybe you could show you're point about why this isn't suited to production situations.[/quote]It's missing locale and encoding support, which is a big deal for those of us who have to support databases in multiple languages.

It's statically linked, which wastes memory and doesn't yield substantial gains anymore unless you're constantly cycling connections.   It also denies some features that are occasionally useful inside libc6 proper, and kills the ability to load user-defined modules.  It also will cause massive crashes in a bunch of situations.

I know mysql.com still recommends this all over the place, but their documenation on best how to compile stuff is out of date, and they do poor benching of this stuff anyway, and their code isn't static-safe.  The fact they  still talk about the long dead pgcc branch should be a big clue to take lots of stuff MySQL says about compilers with a grain of salt.

Also, I have a great distrust of any GCC optimizations the vendor doesn't provide or bless, because GCC's optimizer is known to generate bad code a lot of the time.  

You're missing some relevant configure options as well, for big tables, thread-safe-clients, etc.  Many of us need these features and rely on their existance.  In any case, they should be enabled for a general-purpose configuration.

Also, look at the amount of patching done to the other provided stuff in a Debian or Ubuntu package: most of the MySQL provided tools, docs, etc. need patching to be really usuable.  Everyone patches the MySQL distro reasonably heavy, because lots of the scripts and stuff are of poor quality.

You give that up doing a source build in this manner.

---

### Post by dudus on 2005-11-30
[QUOTE=LordHunter317]It's missing locale and encoding support, which is a big deal for those of us who have to support databases in multiple languages.[/QUOTE]
As a matter of fact I use portuguese, and this language use special characters so it's an important feature for me. But the basic encoding in mysql is latin1 witch seems to work well form me. As we aim a 'default configuration' it seems good as it is. People with special needs should be beyound the basics. But it would be nice to include this info in the how to.

[QUOTE=LordHunter317]
It's statically linked, which wastes memory and doesn't yield substantial gains anymore unless you're constantly cycling connections. [/QUOTE]
Some of the parameters were taken from [this configuration]("http://www.databasejournal.com/features/mysql/article.php/10897_1402311_1"). I don't have much experience neither did any bench on this. But they say static links make it runs 13% faster according to mysql. It's very case specific but I think it should work well generaly. 

[QUOTE=LordHunter317]
  It also denies some features that are occasionally useful inside libc6 proper, and kills the ability to load user-defined modules.  It also will cause massive crashes in a bunch of situations.[/QUOTE]
Didn't think in this at all. In fact, I don't even understand this very well, but it seems important. Maybe you could help with this to make the configuration more usable.


[QUOTE=LordHunter317]
You're missing some relevant configure options as well, for big tables, thread-safe-clients, etc.  Many of us need these features and rely on their existance.  In any case, they should be enabled for a general-purpose configuration.[/QUOTE]
This would be great to add. I'll look after that. Thanks

[QUOTE=LordHunter317]
Also, look at the amount of patching done to the other provided stuff in a Debian or Ubuntu package: most of the MySQL provided tools, docs, etc. need patching to be really usuable.  Everyone patches the MySQL distro reasonably heavy, because lots of the scripts and stuff are of poor quality.

You give that up doing a source build in this manner.
[/QUOTE]
Sure I would prefer to use a proper ubuntu or debian package. The reasen I'm doing this as it is, is because there isn't good deb packages at all. It's the only way I found until now to have mysql5 up and running in my Ubuntu box. Mysql5 has a lot of improvments and is mandatory for the application I'm running. This how to is for the ones like me that can't wait for the package or the ones that need special configuration flags.

Thanks for all your feedback LordHunter317. I'll try to improve this the best I can.

---

### Post by LordHunter317 on 2005-11-30
[QUOTE=dudus]As a matter of fact I use portuguese, and this language use special characters so it's an important feature for me. But the basic encoding in mysql is latin1 witch seems to work well form me.[/quote]Yes, but it won't work well for people using Arabic, Chinese, Cyrillic, Greek or many other languages.  And they outnumber you, so I don't think excluding all encodings but the default one is a smart idea :p

(If the whole world used Unicode, we wouldn't have this problem... that's another story I suppose).

> As we aim a 'default configuration' it seems good as it is.but it's not.  A default configuration should, w.r.t. encoding, cater to everyone.

>  But they say static links make it runs 13% faster according to mysql. It's very case specific but I think it should work well generaly. But it won't, and that's my whole point.  If you change your NSS settings ever, you will risking crashing MySQL and will have to recompile it.  If you change a few other odds and ends, you will crash MySQL and have to recompile.

For a general situation: MySQL + static linking (well static linking in general) is a no-no.  It just breaks too many things and will cause too many bugs.

FWIW, this applies generally on Linux, not just to MySQL.  MySQL's just a bad case because the code isn't truly static link safe, and because MySQL AB actively encourages such dangerous activities. 

> Didn't think in this at all. In fact, I don't even understand this very well, but it seems important. Maybe you could help with this to make the configuration more usable.What I'm saying is, don't use static linking unless you absolutely must.  Meaning, you've done everything else you can and this is your only recourse left.  

> Sure I would prefer to use a proper ubuntu or debian package. The reasen I'm doing this as it is, is because there isn't good deb packages at all.Debian unstable/testing has mysql-5.0 packages.  While unsupported, you could pull and pin from sid if you must.

---

### Post by dudus on 2005-12-01
Ok you completely convinced me. I agree with all your points! ;) 

I do think that charsets are very important. And I understand static linking is evil.:twisted:

I'll try to improve the howto to comply with this two.

But I don't see an answer to the package thing. It seems that ubuntu will last till dapper without mysql5 into the backports. And I don't feel confortable using debian packages. I'd rather compiling then and taking the integration consequences. I'm using it in my computer, and it seems fine, but you're right it's not the best thing to  production. I'll add some comments to make it clear for the ones that follow the howto.

Thank you very much again . =D>

---

### Post by LordHunter317 on 2005-12-01
If oyu're not comfortable using hte binary, adding a source line for sid, installing the source, and doing a backport by rebuilding the binary would be a smarter idea then.  At this point in time, it'll probably rebuild without too much fuss on breezy.

---

### Post by dudus on 2005-12-01
[QUOTE=LordHunter317]If oyu're not comfortable using hte binary, adding a source line for sid, installing the source, and doing a backport by rebuilding the binary would be a smarter idea then.  At this point in time, it'll probably rebuild without too much fuss on breezy.[/QUOTE]
I'm a total newbie on this. I don't know how to manage packages very well. I just apt-get them or at most i install with dpkg. I don't know nothing about their architecture or how to modify or create new ones. Sure If I knew I would rather make a package so I could safely install wherever I am. But it's not the case. 

But I'll look after that when I have some spare time. And in the time I learn I'll package that. Again I did it as I did 'couse I saw no other way. And a experienced user told me to compile it myself. So I did. And I wanted to share this.

Maybe this lines could be usefull for a not so experienced user who needs mysql or to someone who knows how to package things. Sure it need improvements, and I'm intended to work on this. It's not the better way to deal with the problem. But it just works. 

If you want you could help with the package thing, showing the way or doing it yourself. If not I'll include your modifications in a day or two. When I learn more about .debs maybe I can package this, in the meantime, it's all I can offer.

[]'s

---

### Post by LordHunter317 on 2005-12-01
I'd offer to backport MySQL5 from sid for you, but I presently cannot, as my Linux desktop (and my Vmware images) are down due to a dead HDD.  If you don't have resolution on that in a week or so (perhaps an offical Ubuntu backport is being done?) then I'll be happy to build packages for any Ubuntu release you desire.

---

### Post by dudus on 2005-12-01
[QUOTE=LordHunter317]I'd offer to backport MySQL5 from sid for you, but I presently cannot, as my Linux desktop (and my Vmware images) are down due to a dead HDD.  If you don't have resolution on that in a week or so (perhaps an offical Ubuntu backport is being done?) then I'll be happy to build packages for any Ubuntu release you desire.[/QUOTE]

That's realy great lordHunter. I read some threads in the backports forum and I noticied there's nothing being done to bring mysql5 to the backports. I think there isn't many people asking for it. But I see this as a very important package. Indeed I wanna learn how to package things so I wouldn't need to bother anyone every time I need a package, and I'd appreciate if you give me some light in this. But If you want to package this one it would be great. I'm sure it would be usefull for some users besides me.

Whats de difference between a debian package and an Ubuntu one? As long as I know they're the same but the ubuntu one was tested in Ubuntu. Is it right? If not how can I turn a debian package into one that wouldn't trash the ubuntu system. I don't know if I'm thinking in the right way here!

Thanks once again :razz:

---

### Post by Robgould on 2005-12-01
Please lordhunter....please.  I'm not above begging.

---

### Post by behnam_re on 2005-12-01
Hey Guys,
I followed this configuration but whenever I start mysqld_safe it starts 10 mysqld processes. any idea what is wrong?

---

### Post by dudus on 2005-12-01
[QUOTE=behnam_re]Hey Guys,
I followed this configuration but whenever I start mysqld_safe it starts 10 mysqld processes. any idea what is wrong?[/QUOTE]

MySQL is a multi-threaded server. That means it creates new threads for every new connection. 
 The MySQL server creates the following threads:

      [LIST]
[*]The TCP/IP connection thread handles all connection requests and creates a new dedicated thread to handle the authentication and SQL query processing for each connection.


[*]On Windows NT there is a named pipe handler thread that does the same work as the TCP/IP connection thread on named pipe connect requests.

[*]The signal thread handles all signals. This thread also normally handles alarms and calls process_alarm() to force timeouts on connections that have been idle too long.

[*]If mysqld is compiled with -DUSE_ALARM_THREAD, a dedicated thread that handles alarms is created. This is only used on some systems where there are problems with sigwait() or if you want to use the thr_alarm() code in your application without a dedicated signal handling thread.

[*]If one uses the --flush_time=val option, a dedicated thread is created to flush all tables at the given interval.

[*]Every connection has its own thread.

[*]Every different table on which one uses INSERT DELAYED gets its own thread.

[*]If you use --master-host, a slave replication thread is started to read and apply updates from the master.
[/LIST]

this info comes from the [official mysql5 reference manual]("http://dev.mysql.com/doc/refman/5.0/en/mysql-threads.html")

So this is normal. If you find that too many threads are slowing down your system you can adjust my.cnf setting to limit cache size or connections limit.

---

### Post by deflux on 2005-12-11
You are confusing multi-threaded with pre-forked. Like apache's MPM pre-fork method, what happens is mysql starts multiple processes.  One process is listening for connections and handing them to the other processes.  Each process has it's own memory space and acts as a independent process (with inter-communication between the master process and the child processes).

A true multi-threaded process will not show the individual threads in the process table (that I understand), and acts like the above, except the threads are in the same memory space.  The result is lower memory usage, and usually faster processing.

The reason I bring this up, is I believe mysql is a pre-forked application, much like how apache has been in the past (they offer alternatives).  However, if you see multiple mysql daemons started, and the result doesn't match what you have configured in my.cnf, then it's quite possible you are improperly configured, and have multiple mysql daemons running at the same time, potentially clobbering each other.

This is the danger you run when compiling applications from source.  ;)

Furthermore, I suggest the --prefix parameter be set to /opt/mysql5.  Using this, you do not run the risk of clobbering other mysql files installed by the ubuntu base system.  The result being you could potentially switch between mysql versions on the fly.

deflux

---

### Post by martyloo on 2005-12-13
[QUOTE=behnam_re]--with-named-curses-libs=/usr/lib/libncurses.a[/QUOTE]


Actually on my 5.10 installation, it's

--with-named-curses-libs=/lib/libncurses.so.5

---

### Post by tameritoke on 2005-12-20
this documentation was for me helpfull, except that I made in the configure script some modifications! 


./configure \
--prefix=/usr/local/mysql \
--with-mysqld-user=mysql \
--without-debug \
--with-unix-socket-path=/tmp/mysql.socket \
--with-named-curses-libs=/usr/lib/libncurses.a --with-ndbcluster \
--with-blackhole-storage-engine --with-extra-charsets=all

That works for me wonderfull! The options, which were for me unsure, I left it to mysql to decide it's own decission (which is usually the standard decission)

About the character stuff.... you should add "all" instead of none, then all character tables (including UTF-8) are inside the compiled distribution! 

About the CPU optimization flags: 
It should be viewable in the linux kernel documentation. Then you can check up if it is right! If yes, then I either would add it in the /etc/bash.bashrc script to export the values system wide! 

Tamer

---

### Post by Gracer on 2006-03-08
:-k 
Hi Dudus,

I'm completely new to MySQl (linux too). Ran through your install - all seeemed to go ok but cannot start my sql

ERROR 2002: Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

Any help or ideas appreciated ??

Thanks

Gracer

---

### Post by dudus on 2006-03-08
[QUOTE=Gracer]:-k 
Hi Dudus,

I'm completely new to MySQl (linux too). Ran through your install - all seeemed to go ok but cannot start my sql

ERROR 2002: Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

Any help or ideas appreciated ??

Thanks

Gracer[/QUOTE]

Hello try to connect using the ip 127.0.0.1 instead of localhost. Although they point to the same machine (self) the first one uses the socket.

If it doesn't work try this:
```
touch '/var/run/mysqld/mysqld.sock'
```
This may fix your sock but I'm not sure about this as I never tried

---

### Post by bennybobw on 2006-03-21
Dudus,
         Thanks for your wiki/posting on how to instlal MySQL from source.  Everything seemed to go fine, except I'm getting the same error as Gracer, and it appears that there is no such directory as /var/run/mysqld:

[FONT="Courier New"]bennybobw@ubuntu:/usr/local/mysql$ sudo /usr/bin/mysql
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
bennybobw@ubuntu:/usr/local/mysql$ ls /var/run/mysqld
ls: /var/run/mysqld: No such file or directory
[/FONT]

If I try to run it with the -p flag, I get:
[FONT="Courier New"]sudo ./bin/mysql -p
Enter password:
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/tmp/mysql.socket' (2)[/FONT]
I looked for that file too, and it also does not exist.

You suggested to Gracer to run it from 127.0.0.1 rather than local host, but I'm so new I don't know how to do that.  Can you explain?  Thanks for your help.

---

### Post by dudus on 2006-03-21
[QUOTE=bennybobw]Dudus,
         Thanks for your wiki/posting on how to instlal MySQL from source.  Everything seemed to go fine, except I'm getting the same error as Gracer, and it appears that there is no such directory as /var/run/mysqld:

[FONT="Courier New"]bennybobw@ubuntu:/usr/local/mysql$ sudo /usr/bin/mysql
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
bennybobw@ubuntu:/usr/local/mysql$ ls /var/run/mysqld
ls: /var/run/mysqld: No such file or directory
[/FONT]

If I try to run it with the -p flag, I get:
[FONT="Courier New"]sudo ./bin/mysql -p
Enter password:
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/tmp/mysql.socket' (2)[/FONT]
I looked for that file too, and it also does not exist.

You suggested to Gracer to run it from 127.0.0.1 rather than local host, but I'm so new I don't know how to do that.  Can you explain?  Thanks for your help.[/QUOTE]


When you connect to mysql you should especify the host.
If you followed the wiki mysql shoul be in the path /usr/local/mysql/bin/mysql. So try this:

```
/usr/local/mysql/bin/mysql --host=127.0.0.1
```

Let me know if you have any questions

---

### Post by bennybobw on 2006-03-22
Dudus,
         Thanks for your reply.  I tried running it on 127.0.0.1 and I got this:

bennybobw@ubuntu:~$ /usr/local/mysql/bin/mysql --host=127.0.0.1
ERROR 2003 (HY000): Can't connect to MySQL server on '127.0.0.1' (111)

I know the server is running, I just can't access it!  Do I need to try to reinstall, or am I just going to run into the same problems again?

Thanks.

---

### Post by dudus on 2006-03-22
[QUOTE=bennybobw]Dudus,
         Thanks for your reply.  I tried running it on 127.0.0.1 and I got this:

bennybobw@ubuntu:~$ /usr/local/mysql/bin/mysql --host=127.0.0.1
ERROR 2003 (HY000): Can't connect to MySQL server on '127.0.0.1' (111)

I know the server is running, I just can't access it!  Do I need to try to reinstall, or am I just going to run into the same problems again?

Thanks.[/QUOTE]

Ok Lets try some steps: :)

First try this if haven't change the default mysql port(3306) to ensure that mysql is running and listenning.
```
netstat -na |grep 3306
```
it shoul be something like this:
```
tcp        0      0 0.0.0.0:3306            0.0.0.0:*               LISTEN
```
Then try 
```
ps xa |grep mysql
```
And it should show at least one process.

----------------------

Now try to connect to that port. Try:
```
telnet localhost 3306
```
```
telnet 127.0.0.1 3306
```
This shoul print:
```
Trying 127.0.0.1...
Connected to 127.0.0.1.
```

If instead it shows:
```
Trying 127.0.0.1...
telnet: Unable to connect to remote host: Connection refused
```
Then you may be experimenting a firewall issue.

Just go to firestarter an allow all connection from localhost(and 127.0.0.1) into port 3306.
If you don't have firestarter:
```
sudo apt-get install firestarter
```

Good luck.

If this don't solve the problem please tell your mysql verssion and atach the file my.cnf that shoul be under /etc

---

### Post by bennybobw on 2006-03-27
Thanks Dudus!  It seems to be working now.  I think the firewall was the issue.  I didn't even think about having to make a rule for the server.  I'm new to this whole thing.

---

### Post by kayas80 on 2006-04-02
I installed MySql 5 from source using your guide. But, I am wondering how I uninstall MySql 5 because it doesn't show up in Synaptic!

---

### Post by dudus on 2006-04-03
[quote=kayas80]I installed MySql 5 from source using your guide. But, I am wondering how I uninstall MySql 5 because it doesn't show up in Synaptic![/quote]

Have you tried:

```
make uninstall
```

??
:confused:

---

### Post by kayas80 on 2006-04-03
[quote=dudus]Have you tried:

```
make uninstall
``` [/quote] 
I tried that and I get this:
```
kayas80@ubuntu:~/mysql-5.0.16$ make uninstall
make: *** No rule to make target `uninstall'.  Stop.

```

---

### Post by scratched on 2006-04-15
I tried installing MySQL 5 using your install guide, and as far as I could tell, I did everything right, but when I try running it I get this error:
```
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/tmp/mysql.socket' (2)

```

I tried the things on this forum to fix the sock but it didn't help. I can still connect to my old MySQL 4.1 server on the same machine however, and when I open MySQL administrator, I only see the old version 4.1

**EDIT:** I restarted my computer and now I can't connect at all. I have the same error as before. I've tried using firestarter to open my ports but that didn't help.

I'm new to linux so I don't really know what I'm doing wrong. Could anyone offer me any suggestions?

---

### Post by curtis on 2006-04-15
[QUOTE=kayas80]I tried that and I get this:
```
kayas80@ubuntu:~/mysql-5.0.16$ make uninstall
make: *** No rule to make target `uninstall'.  Stop.

```[/QUOTE]

```

make clean

```
That should work fine.

---

### Post by kayas80 on 2006-04-18
[quote=curtis]```

make clean

``` That should work fine.[/quote]

It worked. Thanks

---

### Post by shizow on 2006-05-10
should i first deinstall mysql 4.x before installing mysql 5?
is there not a repository version of MySQL or a deb file somewhere?

---

### Post by supanova on 2006-09-11
Hi All

Thanks for this

It should be easier though

See [http://ubuntuforums.org/showthread.php?t=255344](http://ubuntuforums.org/showthread.php?t=255344)

All I want to do is download the source from launchpad... change locations of directories and run it... but it does not seem possible... they don't seem to give you everything?

See [https://launchpad.net/+builds/+build/242389](https://launchpad.net/+builds/+build/242389)

Any help will be appreciated

Thanks

---

### Post by William Pickett on 2006-12-26
Hello..

I am a new <= 1 yr NewUbuntu er, and am attempting- to get Myth TV installed, and as "we" all get to know, it depends on MySql being properly set up.

Here are some recent entries:~$ mysql-server
bash: mysql-server: command not found
:~$ sudo mysql-server
sudo: mysql-server: command not found
:~$ sudo apt-get install mysql-server
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
:~$ sudo apt-get install mysql-server
Reading package lists... Done
Building dependency tree... Done
mysql-server is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
2 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up mythtv-database (0.20-0.2ubuntu2) ...
Failed to connect to database: Access denied for user 'root'@'localhost' (using password: YES) at -e line 5, <> line 1.
Failed to create database (incorrect admin username/password?)
If you supplied incorrect information, try:
dpkg-reconfigure --force mythtv-database
dpkg: error processing mythtv-database (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mythtv:
 mythtv depends on mythtv-database (= 0.20-0.2ubuntu2); however:
  Package mythtv-database is not configured yet.
dpkg: error processing mythtv (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 mythtv-database
 mythtv
E: Sub-process /usr/bin/dpkg returned an error code (1)
:~$ sudo groupadd mysql
groupadd: group mysql exists
:~$ sudo useradd -g mysql mysql
useradd: user mysql exists
:~$ cd mysql
bash: cd: mysql: No such file or directory
:~$ cd mysql-server
bash: cd: mysql-server: No such file or directory
:~$ cd/mysql5
bash: cd/mysql5: No such file or directory
:~$ cd\mysql5
bash: cdmysql5: command not found
:~$ cd mysql-5.0.24a-9
bash: cd: mysql-5.0.24a-9: No such file or directory
:~$ sudo apt-get install mysql-5.0.24a-9
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package mysql-5.0.24a-9
:~$ cd mysql-common
bash: cd: mysql-common: No such file or directory
:~$ sudo apt-get mysql-client
E: Invalid operation mysql-client
:~$ sudo apt-get install mysql all
Reading package lists... Done
Building dependency tree... Done
Package mysql is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package mysql has no installation candidate
desktop:~$ 

Is there a way around/thru this I am seriously missing? One good thing I am learning- a lot- is how to think for myself where programming is concerned. And I am quite sure I will be a master at all this in a few years and even write a new user book.

In the mean time, hee haw, and I have checked out many Ubuntu and other online helps, but somewhere I am not doing the Mysql setup properly- I know somewhere I have to sudo nano edit the mysql.conf file, but haven't found -(saved- will next time I cross it) where I ran across the changes I need to do to get mysql operational so it will take my new passwords etc. Any help, specific please, as in first you do (a) and (a) looks like this, etc... Thanks to all users who give of their time and effort- I will too as I have info to assist with.

William, learning and leaning on help from Community Support- :-):)

---

### Post by sriv1211 on 2007-08-06
i think the link above should work

---

### Post by sriv1211 on 2007-08-06
apt-get install libncurses5-dev
for curses error

---

### Post by larrylep on 2008-06-03
Was building mysql 5.1.24 on ubuntu 8.04 server and got an error message "checking for termcap functions library... configure: error: No curses/termcap library found"

by installing apt-get install libncurses5-dev this fixed the problem

---

### Post by vijayendra.suman on 2008-06-13
Hi

Can you please check with file "/etc/mysql/my.cnf" One my system it has line number 47.
I changed to

 45 # Instead of skip-networking the default is now to listen only on
 46 # localhost which is more compatible and is not less secure.
 47 bind-address            = 127.0.0.1
 48 #bind-address           = *

And it worked.
I am not sure why it worked.
V.Suman:confused:

---

