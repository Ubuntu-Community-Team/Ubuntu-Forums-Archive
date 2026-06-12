---
title: "MySQL won't install"
date: 2011-12-05
forum: Server Platforms
---

### Post by WASasquatch on 2011-12-05
For some reason I couldn't login to my mysql server, so I removed it with autoremove, now when I try to reinstall to reconfigure, it can't install tried apt-get install mysql-server-5.5 and -f install but none will work. Even upgrade won't work.

```
root@smiths-laptop:~# apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 mysql-client : Depends: mysql-client-5.5 but it is not installed
E: Unmet dependencies. Try using -f.
root@smiths-laptop:~# apt-get -f upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following NEW packages will be installed:
  mysql-client-5.5
The following packages have been kept back:
  libapache2-mod-php5 php5 php5-cli php5-common php5-gd php5-mysql
0 upgraded, 1 newly installed, 0 to remove and 6 not upgraded.
1 not fully installed or removed.
Need to get 0 B/8,267 kB of archives.
After this operation, 30.5 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  mysql-client-5.5
Install these packages without verification [y/N]? y
(Reading database ... 89957 files and directories currently installed.)
Unpacking mysql-client-5.5 (from .../mysql-client-5.5_5.5.18-1~dotdeb.1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/mysql-client-5.5_5.5.18-1~dotdeb.1_i386.deb (--unpack):
 trying to overwrite '/usr/bin/mysql', which is also in package mysql-client-core-5.1 5.1.58-1ubuntu1
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/mysql-client-5.5_5.5.18-1~dotdeb.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@smiths-laptop:~#

```

---

### Post by lncoll on 2011-12-05
Seems the downloaded package is corrupt, you can clean your apt cache to force new download.
```

sudo apt-get clean

```
And try again with the install.

---

