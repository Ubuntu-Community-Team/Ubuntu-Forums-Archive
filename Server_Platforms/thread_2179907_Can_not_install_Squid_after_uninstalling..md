---
title: "Can not install Squid after uninstalling."
date: 2013-10-10
forum: Server Platforms
---

### Post by jpaytoncfd on 2013-10-10
I am trying to install Squid on my server but I configured wrong and decided to remove and install from scratch. 

Now I have tried everything to install and I get this error:
```
root@SERVER:/home/jpayton# apt-get install squidReading package lists... Done
Building dependency tree
Reading state information... Done
squid is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]?
Setting up squid3 (3.1.20-1ubuntu3) ...
stat: cannot stat â/var/spool/squidâ: No such file or directory
chown: cannot access â/var/spool/squidâ: No such file or directory
dpkg: error processing squid3 (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of squid:
 squid depends on squid3; however:
  Package squid3 is not configured yet.


dpkg: error processing squid (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 squid3
 squid
E: Sub-process /usr/bin/dpkg returned an error code (1)



```

I have tried purge, install -f, update, upgrade, --reinstall, everything seems to relate back to that error.

---

### Post by jpaytoncfd on 2013-10-10
update 
I tried removing the packages from /var/lib/dpkg/info and I can not install squid but it dosent install. Still mentions squid3 package.

```
jpayton@SERVER:~$ sudo apt-get install squidReading package lists... Done
Building dependency tree
Reading state information... Done
The following NEW packages will be installed:
  squid
0 upgraded, 1 newly installed, 0 to remove and 2 not upgraded.
Need to get 6,246 B of archives.
After this operation, 129 kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com/ubuntu/ raring/universe squid amd64 3.1.20-1ubuntu3 [6,246 B]
Fetched 6,246 B in 0s (25.3 kB/s)
Selecting previously unselected package squid.
dpkg: warning: files list file for package 'squid3' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'squid-langpack' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'squid3-common' missing; assuming package has no files currently installed
(Reading database ... 164196 files and directories currently installed.)
Unpacking squid (from .../squid_3.1.20-1ubuntu3_amd64.deb) ...
Setting up squid (3.1.20-1ubuntu3) ...
jpayton@SERVER:~$ sudo apt-get install squid3
Reading package lists... Done
Building dependency tree
Reading state information... Done
squid3 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
jpayton@SERVER:~$ sudo service squid3 restart
stop: Unknown instance:
squid3 start/running, process 5224
jpayton@SERVER:~$ sudo service squid3 stop
stop: Unknown instance:
jpayton@SERVER:~$



```

---

### Post by papibe on 2013-10-10
Hi jpaytoncfd.

It looks like, from your first post, that something went wrong when you remove the package. How did you remove it? What command did you use?

BTW, it is not safe to manually remove files from /var/lib/dpkg/info. What files did you remove?

Regards.

---

### Post by jpaytoncfd on 2013-10-11
I think it was ```
Sudo apt-get autoremove squid
``` I removed those package files after trying everything else. With them removed Squid installs but non of the dependencies seem to. like squid3 and squid3-common.

---

### Post by Amorphous Serendipity on 2013-10-11
Hi jpaytoncfd,

         "squid" is a dummy transitional package for  "squid3" (basically meaning it's sort of like a redirect to the newly  named version "squid3"). Because of this, when you originally issued the  command to uninstall "squid", it removed only the dummy package.  The output of the first command for installation looked like it yelled at you because technically you never removed "squid3" and it did not want to install the dummy package (as it should not be necessary).  The output of the second command looked like you broke "squid3" when you manually deleted whatever you deleted (this is not a good idea to do as there are many other references to the package throughout the system [that's what a package manager is for])

 
I'm  not sure what you deleted so I can't be certain this will work, but you  would usually remove "squid3" with the following command
```
sudo apt-get remove squid3*
```
which would have also removed the "squid" dummy package.


I would try running
```
sudo apt-get autoclean
```
and
```
sudo apt-get clean
```
before you run the command I listed to uninstall "squid3".

---

