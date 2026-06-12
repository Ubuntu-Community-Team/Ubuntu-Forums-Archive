---
title: "ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysq"
date: 2012-05-26
forum: Server Platforms
---

### Post by Ed_Ziffel on 2012-05-26
Installed 12.04 LAMP phpmyadmin and all is well.  Actually starting to like Unity after playing with it for a while.  Not getting what all the fuss is about.  

Need to change the database directory.  Ran though all the changes made done in 10.04 but not working.  When trying to log into mysql using the terminal getting > ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

When trying to start mysql, sudo service mysql start, get Start:  Job failed to start.  So mysql is definately not running.  Restored apparmor.d/usr.sbin.mysqld, my.cnf, back to my backup of the origals then
sudo /etc/init.d/apache2 restart
sudo /etd/init.d/apparmor.d reload
sudo service mysql start 
and all works fine again.  Has to be a settings thing.  

Did a sudo cp -Pr /var/lib/mysql /MyDrive/Databases
Which didn't actually keep all the permissions straight so
sudo chown -r mysql:mysql /MyDrive/Databases
sudo chmod -r 770 /MyDrive/Databases
and checked using Nautilus

Did some homework and found a few entries talking about the server host is not set.  Added in /etc/apache2/http.conf the line "ServerName 127.0.0.1".  This works fine with the original files but again not with my changes which are as follows;
apparmor.d usr.sbin.mysqld
```

/usr/sbin/mysqld {
  #include <abstractions/base>
  #include <abstractions/nameservice>
  #include <abstractions/user-tmp>
  #include <abstractions/mysql>
  #include <abstractions/winbind>

  capability dac_override,
  capability sys_resource,
  capability setgid,
  capability setuid,

  network tcp,

  /etc/hosts.allow r,
  /etc/hosts.deny r,

  /etc/mysql/*.pem r,
  /etc/mysql/conf.d/ r,
  /etc/mysql/conf.d/* r,
  /etc/mysql/*.cnf r,
  /usr/lib/mysql/plugin/ r,
  /usr/lib/mysql/plugin/*.so* mr,
  /usr/sbin/mysqld mr,
  /usr/share/mysql/** r,
  /var/log/mysql.log rw,
  /var/log/mysql.err rw,
  # /var/lib/mysql/ r,  //comment out original 2 lines comments only for here not in file on machine.
  # /var/lib/mysql/** rwk,
  /MyDisk/Databases/ r,  // added these two in, again no comments in real file
  /MyDisk/Databases/** rwk,
  /var/log/mysql/ r,
  /var/log/mysql/* rw,
  /var/run/mysqld/mysqld.pid w,
  /var/run/mysqld/mysqld.sock w,
  /run/mysqld/mysqld.pid w,
  /run/mysqld/mysqld.sock w,

  /sys/devices/system/cpu/ r,

  # Site-specific additions and overrides. See local/README for details.
  #include <local/usr.sbin.mysqld>
}

```
my.cnf
```

[client]
port		= 3306
socket		= /var/run/mysqld/mysqld.sock

# Here is entries for some specific programs
# The following values assume you have at least 32M ram

# This was formally known as [safe_mysqld]. Both versions are currently parsed.
[mysqld_safe]
socket		= /var/run/mysqld/mysqld.sock
nice		= 0

[mysqld]
#
# * Basic Settings
#
user		= mysql
pid-file	= /var/run/mysqld/mysqld.pid
socket		= /var/run/mysqld/mysqld.sock
port		= 3306
basedir		= /usr
# datadir		= /var/lib/mysql
datadir		= /MyDisk/Databases
tmpdir		= /tmp:/kar3/sqlout
lc-messages-dir	= /usr/share/mysql
skip-external-locking

```

httpd.config
```

ServerName 127.0.0.1

```

Also tried as suggested in another post to make a file/var/run/mysqld/mysqld.sock change the permissions, etc.  and got:
```
Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (111)
```
which lead to another round of searching with no results.  

All worked with just changes to my.cnf and apparmor.d /usr.sbin.mysqld with 10.04.  What am I missing?

Thqanks

Ed

---

### Post by game1 on 2012-05-27
I had exactly the same problem 1 year ago. I have very simply solution. Try to install MySQL from Ubuntu repositories.

apt-get install mysql-server mysql-client

It will also automatically make MySQL starting at boot.

---

### Post by Ed_Ziffel on 2012-05-27
Thanks game1,

But have solved the problem.

Serveral things were wrong.  Stepped through by changing just one line at a time and testing starting from the original working install.  It does burn my a&& though to think that you have to use trial and error as oppossed to being able to find some sort of documentation on it.  Have to take points off of Linux approval for that: Poor to non-existant documentation. Have three 1000 pagers in my book libray but useless for details on custom issues. Hey Linux is a really big OS. Don't get me wrong, I love Linux and after trying Linux Mint, Linux Mint Degian, Debian, RedHat, Centos, and Scientific Linux recently, REALLY like Ubuntu.  Still, how can you seriously promote a product that you have to explain:  IE "Yeah George, Linux would be great for your business, only if you have a problem, it might take you two years to fix it by yourself because you can't find any documentation on it."  George would probably be better off sticking with microsoft as there are many more resources for him to solve problems with.  

That said, Here is what I did/ found out:
1.  You don't have to change the tmp directory in the my.cnf file.  Even adding a second directory, changing from tempdir =/tmp to =/tmp:/newdir crashed mysql.  In 10.04 using MySQL 5.1 you used to have to add the second path other wise you got an error something like can't write temp file....  Of course did change the datadir to /MyDisk/myNewDir

2.  Used the wrong permission flags on my file copy from the command line.  Should use cp -R -p /var/lib/mysql /MyDisk/myNewDir.  Not sure if that really mattered as trashed old dir and started over with the flags as stated so did not test with old permissions.  This did work.

3.  Added /MyDisk/myNewDir/ r, and /MyDisk/myNewDir/* rwk, to the bottom of etc/apparmor.d/usr.sbin.mysqld file.  Also changed the var/lib/mysql entries in apparmor as above

4.  Left in the var/run... file as created above.  Also not sure if that matters but already behind in getting the server updated so not really caring past having it working properly.  

sudo service mysql stop
sudo /etc/init.d/apparmor reload
sudo service mysql start 

and this worked.

---

