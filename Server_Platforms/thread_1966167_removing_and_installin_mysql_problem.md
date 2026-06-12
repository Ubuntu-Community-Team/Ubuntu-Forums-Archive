---
title: "removing and installin mysql problem"
date: 2012-04-26
forum: Server Platforms
---

### Post by EG-girl on 2012-04-26
hi guys 
this is my first topic in here and I hope I have a solution to my big confusion in this forum
I need to remove mysql totally and reinstalling it and I followed[COLOR=DeepSkyBlue]_ [this link]("http://stuffthatspins.com/2011/01/08/ubuntu-10-x-completely-remove-and-clean-mysql-installation/")_[/COLOR]'s instructions
but when I come to the command> service mysql status it gives me > mysql stop/waitingI am using ubuntu 10.4 all I want is how to get through mysql and start using it with mysql-admin ... but I am too confused to get the job done :confused::confused::confused:
I hope this will make the problem clear ... for more clarification please tell me ...

---

### Post by papibe on 2012-04-26
Hi EG-girl. Welcome to the forums!

Try this to start the mysql:
```
sudo service mysql start
```
or
```
sudo service mysql restart
```
Then you can check if it really started:
```
sudo service mysql status
```
Hope that helps, and tell us how it goes.
Regards.

---

### Post by EG-girl on 2012-04-26
thanks [papibe]("http://ubuntuforums.org/member.php?u=774785") for replying 
I already tried both of them and it gives me
> start: Job failed to start
> restart: Unknown instance:

I think I did something wrong .... :(

---

### Post by papibe on 2012-04-26
Did you use sudo for all your commands?

Regards.

---

### Post by EG-girl on 2012-04-26
when using the command
> mysqladmin -u root -p status 

i have this 
> mysqladmin: connect to server at 'localhost' failed
error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!


it this can give a hint ... i hope :(
I hope any one can help.. it will be appreciated

---

### Post by papibe on 2012-04-26
It looks like it is not properly installed. May be an error on the previous steps?

I think you should redo again the instructions, and post any output that may look like an error, so we can take a look.

Regards.

---

### Post by EG-girl on 2012-04-26
aptitude remove mysql-server command did something strange 

> Need to get 0B of archives. After unpacking 54.9MB will be freed.
Do you want to continue? [Y/n/?] y  
Writing extended state information... Done
(Reading database ... 193511 files and directories currently installed.)
Removing mysql-server ...
Removing mysql-server-5.1 ...
_**stop: Unknown instance: **_
Removing mysql-client-5.1 ...
Removing libdbd-mysql-perl ...
Removing libdbi-perl ...

then continue to remove stuff


then 
apt-cache rdepends mysql-server
 results in 
>  convirt2
    mysql-cluster-server-5.1
    mysql-server-5.1
  bbb-web
    mysql-cluster-server-5.1
    mysql-server-5.1
  mysql-testsuite
    mysql-cluster-server-5.1
    mysql-server-5.1
  mysql-server-5.1
  mysql-server-5.1
  wordpress
 |smbind
    mysql-cluster-server-5.1
    mysql-server-5.1 
 and the list goes on


and another list for the client dependencies:rolleyes::rolleyes::rolleyes:

???????? :(

---

### Post by papibe on 2012-04-26
Before continuing, could you post the result of this command?
```
apt-cache policy mysql-server mysql-client
```
Regards.

---

### Post by EG-girl on 2012-04-26
> mysql-server:
  Installed: 5.1.62-0ubuntu0.10.04.1
  Candidate: 5.1.62-0ubuntu0.10.04.1
  Version table:
 *** 5.1.62-0ubuntu0.10.04.1 0
        500 [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) lucid-proposed/main Packages
        100 /var/lib/dpkg/status
     5.1.61-0ubuntu0.10.04.1 0
        500 [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) lucid-updates/main Packages
        500 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Packages
     5.1.41-3ubuntu12.10 0
        500 [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) lucid-updates/main Packages
     5.1.41-3ubuntu12.7 0
        500 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Packages
     5.1.41-3ubuntu12 0
        500 [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) lucid/main Packages
mysql-client:
  Installed: 5.1.62-0ubuntu0.10.04.1
  Candidate: 5.1.62-0ubuntu0.10.04.1
  Version table:
 *** 5.1.62-0ubuntu0.10.04.1 0
        500 [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) lucid-proposed/main Packages
        100 /var/lib/dpkg/status
     5.1.61-0ubuntu0.10.04.1 0
        500 [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) lucid-updates/main Packages
        500 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Packages
     5.1.41-3ubuntu12.10 0
        500 [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) lucid-updates/main Packages
     5.1.41-3ubuntu12.7 0
        500 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Packages
     5.1.41-3ubuntu12 0
        500 [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) lucid/main Packages

thanks for your help

---

### Post by papibe on 2012-04-26
That's odd, at that point of the instructions both shouldn't be installed, but they are.

I'm not familiar with aptitude, so if I were you I would use apt-get.

Try this instructions:

To complete uninstall it:
```

sudo  apt-get  purge  mysql-server
sudo  apt-get  purge  mysql-client

sudo  apt-get   autoremove
sudo  apt-get   autoclean
```
To reinstall:
```
sudo  apt-get  install  mysql-server  mysql-client
```

Now it should be installed. Check if it is running:
```
sudo  service mysql status
```
If not, start it:
```
sudo service mysql start
```
Check Status with mysqladmin:
```
mysqladmin -u root -p status 
```
Tell us how it goes.
Regards.

---

### Post by EG-girl on 2012-04-27
same results unfortunately :confused::confused:

start: Job failed to start

I don't know what to do ??

---

### Post by papibe on 2012-04-27
Could you post the result of these command?
```
ls -l /etc/mysql

dmesg | grep sql

grep sql /var/log/kern.log
```
Regards.

---

### Post by EG-girl on 2012-04-27
> ls -l /etc/mysql
drwxr-xr-x 2 root root 4096 2012-04-28 01:21 conf.d
-rw------- 1 root root  333 2012-04-28 01:22 debian.cnf




> grep sql /var/log/kern.log

Apr 26 02:59:59 maha-lap kernel: [187159.238928] type=1505 audit(1335401999.160:20):  operation="profile_replace" pid=25492 name="/usr/sbin/mysqld"
Apr 26 02:59:59 maha-lap kernel: [187159.299603] type=1505 audit(1335401999.220:21):  operation="profile_replace" pid=25497 name="/usr/sbin/mysqld"
Apr 26 03:36:17 maha-lap kernel: [189337.281022] type=1503 audit(1335404177.204:22):  operation="capable" pid=26815 parent=26803 profile="/usr/sbin/mysqld" name="chown"
Apr 26 03:36:39 maha-lap kernel: [189359.506871] type=1505 audit(1335404199.428:23):  operation="profile_replace" pid=26900 name="/usr/sbin/mysqld"
Apr 26 17:10:03 maha-lap kernel: [   21.129809] type=1505 audit(1335453003.089:21):  operation="profile_load" pid=1114 name="/usr/sbin/mysqld"
Apr 27 03:43:23 maha-lap kernel: [13619.163702] type=1503 audit(1335491003.577:22):  operation="capable" pid=5493 parent=5481 profile="/usr/sbin/mysqld" name="chown"
Apr 27 03:43:51 maha-lap kernel: [13647.144114] type=1505 audit(1335491031.560:23):  operation="profile_replace" pid=5585 name="/usr/sbin/mysqld"
Apr 27 05:03:35 maha-lap kernel: [18430.824068] type=1503 audit(1335495815.237:24):  operation="capable" pid=6520 parent=6508 profile="/usr/sbin/mysqld" name="chown"
Apr 27 05:03:57 maha-lap kernel: [18452.875103] type=1505 audit(1335495837.288:25):  operation="profile_replace" pid=6598 name="/usr/sbin/mysqld"
Apr 28 00:18:41 maha-lap kernel: [25242.313953] type=1503 audit(1335565121.936:26):  operation="capable" pid=9653 parent=9641 profile="/usr/sbin/mysqld" name="chown"
Apr 28 00:19:10 maha-lap kernel: [25270.568264] type=1505 audit(1335565150.192:27):  operation="profile_replace" pid=9747 name="/usr/sbin/mysqld"
Apr 28 00:37:59 maha-lap kernel: [26399.761215] type=1503 audit(1335566279.384:28):  operation="capable" pid=10353 parent=10341 profile="/usr/sbin/mysqld" name="chown"
Apr 28 00:38:21 maha-lap kernel: [26422.159671] type=1505 audit(1335566301.780:29):  operation="profile_replace" pid=10431 name="/usr/sbin/mysqld"
Apr 28 01:22:00 maha-lap kernel: [29040.856207] type=1503 audit(1335568920.476:30):  operation="capable" pid=11224 parent=11212 profile="/usr/sbin/mysqld" name="chown"
Apr 28 01:22:28 maha-lap kernel: [29068.482416] type=1505 audit(1335568948.104:31):  operation="profile_replace" pid=11316 name="/usr/sbin/mysqld"


dmesg | grep sql
[   21.129809] type=1505 audit(1335453003.089:21):  operation="profile_load" pid=1114 name="/usr/sbin/mysqld"
[13619.163702] type=1503 audit(1335491003.577:22):  operation="capable" pid=5493 parent=5481 profile="/usr/sbin/mysqld" name="chown"
[13647.144114] type=1505 audit(1335491031.560:23):  operation="profile_replace" pid=5585 name="/usr/sbin/mysqld"
[18430.824068] type=1503 audit(1335495815.237:24):  operation="capable" pid=6520 parent=6508 profile="/usr/sbin/mysqld" name="chown"
[18452.875103] type=1505 audit(1335495837.288:25):  operation="profile_replace" pid=6598 name="/usr/sbin/mysqld"
[25242.313953] type=1503 audit(1335565121.936:26):  operation="capable" pid=9653 parent=9641 profile="/usr/sbin/mysqld" name="chown"
[25270.568264] type=1505 audit(1335565150.192:27):  operation="profile_replace" pid=9747 name="/usr/sbin/mysqld"
[26399.761215] type=1503 audit(1335566279.384:28):  operation="capable" pid=10353 parent=10341 profile="/usr/sbin/mysqld" name="chown"
[26422.159671] type=1505 audit(1335566301.780:29):  operation="profile_replace" pid=10431 name="/usr/sbin/mysqld"
[29040.856207] type=1503 audit(1335568920.476:30):  operation="capable" pid=11224 parent=11212 profile="/usr/sbin/mysqld" name="chown"
[29068.482416] type=1505 audit(1335568948.104:31):  operation="profile_replace" pid=11316 name="/usr/sbin/mysqld"

---

### Post by papibe on 2012-04-27
Thanks.

I'm missing your my.cnf

By any chance is in /etc ?
```
ls /etc/my.cnf
```

Also, Let's see what version is installed:
```
apt-cache   policy   mysql-server  mysql-server-5.1  mysql-common
```
Regards.


EDIT: also check if this solve the problem:
```
sudo dpkg-reconfigure mysql-common
```

---

### Post by EG-girl on 2012-04-30
ls /etc/my.cnf
ls: cannot access /etc/my.cnf: No such file or directory


apt-cache   policy   mysql-server  mysql-server-5.1  mysql-common

mysql-server:
  Installed: 5.1.62-0ubuntu0.10.04.1
  Candidate: 5.1.62-0ubuntu0.10.04.1
  Version table:
 *** 5.1.62-0ubuntu0.10.04.1 0
        500 [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) lucid-proposed/main Packages
        100 /var/lib/dpkg/status
     5.1.61-0ubuntu0.10.04.1 0
        500 [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) lucid-updates/main Packages
        500 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Packages
     5.1.41-3ubuntu12.10 0
        500 [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) lucid-updates/main Packages
     5.1.41-3ubuntu12.7 0
        500 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Packages
     5.1.41-3ubuntu12 0
        500 [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) lucid/main Packages
mysql-server-5.1:
  Installed: 5.1.62-0ubuntu0.10.04.1
  Candidate: 5.1.62-0ubuntu0.10.04.1
  Version table:
 *** 5.1.62-0ubuntu0.10.04.1 0
        500 [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) lucid-proposed/main Packages
        100 /var/lib/dpkg/status
     5.1.61-0ubuntu0.10.04.1 0
        500 [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) lucid-updates/main Packages
        500 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Packages
     5.1.41-3ubuntu12 0
        500 [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) lucid/main Packages
mysql-common:
  Installed: 5.1.62-0ubuntu0.10.04.1
  Candidate: 5.1.62-0ubuntu0.10.04.1
  Version table:
 *** 5.1.62-0ubuntu0.10.04.1 0
        500 [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) lucid-proposed/main Packages
        100 /var/lib/dpkg/status
     5.1.61-0ubuntu0.10.04.1 0
        500 [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) lucid-updates/main Packages
        500 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Packages
     5.1.41-3ubuntu12.10 0
        500 [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) lucid-updates/main Packages
     5.1.41-3ubuntu12.7 0
        500 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Packages
     5.1.41-3ubuntu12 0
        500 [http://eg.archive.ubuntu.com/ubuntu/](http://eg.archive.ubuntu.com/ubuntu/) lucid/main Packages


sudo dpkg-reconfigure mysql-common

nothing...... :(

---

### Post by papibe on 2012-04-30
Sorry that this problems has taken so much time.

I did several testing on a 11.4 server, and I found that mysql won't start without the file /etc/mysql/my.cnf

However, to my surprise, non of the command that I gave you so far reinstall or recopy that file.

Nevertheless, I deleted the same file on my system and force myself to find a solution (don't worry it is my test server).

This steps should reinstall the file:

First, force the download of the .deb file
```
sudo apt-get --reinstall install mysql-common
```
Then force the reinstall of config files explicitly from the deb itself:
```
sudo dpkg --force-confmiss -i /var/cache/apt/archives/mysql-common*.deb
```
That allowed to restart the service again:
```
sudo service mysql-server start
```
I hope that finally solve your problem. Tell us how it goes this time.
Regards.

---

### Post by EG-girl on 2012-04-30
I really appreciate what you've done till now but I really have no ides what I did wrong in the first place to cause such a mess :(

Like you I was hoping that these final commands should work but sadly it didn't
> sudo apt-get --reinstall install mysql-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 1 not upgraded.
Need to get 0B/79.5kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 193516 files and directories currently installed.)
Preparing to replace mysql-common 5.1.62-0ubuntu0.10.04.1 (using .../mysql-common_5.1.62-0ubuntu0.10.04.1_all.deb) ...
Unpacking replacement mysql-common ...
Setting up mysql-common (5.1.62-0ubuntu0.10.04.1) ...

> sudo dpkg --force-confmiss -i /var/cache/apt/archives/mysql-common*.deb
dpkg: warning: downgrading mysql-common from 5.1.62-0ubuntu0.10.04.1 to 5.1.61-0ubuntu0.10.04.1.
(Reading database ... 193516 files and directories currently installed.)
Preparing to replace mysql-common 5.1.62-0ubuntu0.10.04.1 (using .../mysql-common_5.1.61-0ubuntu0.10.04.1_all.deb) ...
Unpacking replacement mysql-common ...
Preparing to replace mysql-common 5.1.61-0ubuntu0.10.04.1 (using .../mysql-common_5.1.62-0ubuntu0.10.04.1_all.deb) ...
Unpacking replacement mysql-common ...
More than one copy of package mysql-common has been unpacked
 in this run !  Only configuring it once.
Setting up mysql-common (5.1.62-0ubuntu0.10.04.1) ...


> sudo service mysql-server start

mysql-server: unrecognized service
can I create my.cnf file myself ??

---

### Post by papibe on 2012-04-30
I see that there's 2 mysql-common debs. Try this:
```
sudo dpkg --force-confmiss -i /var/cache/apt/archives/mysql-common_5.1.62-0ubuntu0.10.04.1_all.deb
```

> **EG-girl said:**
> can I create my.cnf file myself ??

Yes you can.

There's several example files here:
```
/usr/share/doc/mysql-server-5.1/examples
```
Regards.

---

### Post by EG-girl on 2012-05-04
finally it's working thank you so much for your time and effort you made to solve my problem,it's running now I can't believe it :D Thanks a million

but I need more help on how to  administrate the server and if there is any GUI tools  to make creating the database easier

---

### Post by papibe on 2012-05-04
:) Great! Please mark the thread [solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") when you have the chance.

> **EG-girl said:**
> ...I need more help on how to  administrate the server and if there is any GUI tools  to make creating the database easier

Take a look at [phpMyAdmin]("https://help.ubuntu.com/community/phpMyAdmin").

I would recommend creating a new thread for that concern.

Regards.

---

