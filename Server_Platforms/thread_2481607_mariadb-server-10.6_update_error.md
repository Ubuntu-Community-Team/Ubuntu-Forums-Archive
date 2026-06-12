---
title: "mariadb-server-10.6 update error"
date: 2022-12-04
forum: Server Platforms
---

### Post by pqwoerituytrueiwoq on 2022-12-04
```
[FONT=monospace][COLOR=#000000]$ sudo apt-get install -f [/COLOR]
Reading package lists... Done 
Building dependency tree... Done 
Reading state information... Done 
Correcting dependencies... Done 
The following packages were automatically installed and are no longer required: 
  libmbedcrypto7 libmbedtls14 libmbedx509-1 libnanomsg5 libpcre2-posix3 sysuser-helper 
Use 'sudo apt autoremove' to remove them. 
The following additional packages will be installed: 
  mariadb-server-10.6 
Suggested packages: 
  mailx mariadb-test 
The following packages will be upgraded: 
  mariadb-server-10.6 
1 upgraded, 0 newly installed, 0 to remove and 38 not upgraded. 
4 not fully installed or removed. 
Need to get 0 B/4078 kB of archives. 
After this operation, 122 kB of additional disk space will be used. 
Do you want to continue? [Y/n] y 
debconf: delaying package configuration, since apt-utils is not installed 
(Reading database ... 143427 files and directories currently installed.) 
Preparing to unpack .../mariadb-server-10.6_1%3a10.6.11-0ubuntu0.22.04.1_amd64.deb ... 
dpkg: warning: version '/var/lib/mysql/debian-.flag' has bad syntax: version number does not start with digit 
dpkg: warning: version '/var/lib/mysql/debian-.flag' has bad syntax: version number does not start with digit 
/var/lib/mysql: found previous version /var/lib/mysql/debian-.flag 
dpkg: warning: version '/var/lib/mysql/debian-.flag' has bad syntax: version number does not start with digit 
dpkg: warning: version '/var/lib/mysql/debian-.flag' has bad syntax: version number does not start with digit 
dpkg: warning: version '/var/lib/mysql/debian-.flag' has bad syntax: version number does not start with digit 
The file /var/lib/mysql/debian-/var/lib/mysql/debian-.flag.flag indicates a 
version that cannot automatically be upgraded. Therefore the 
previous data directory will be renamed to /var/lib/mysql-/var/lib/mysql/debian-.flag and 
a new data directory will be initialized at /var/lib/mysql. 
Please manually export/import your data (e.g. with mysqldump) if needed. 
mv: cannot move '/var/lib/mysql' to '/var/lib/mysql-/var/lib/mysql/debian-.flag': No such file or directory 
dpkg: error processing archive /var/cache/apt/archives/mariadb-server-10.6_1%3a10.6.11-0ubuntu0.22.04.1_amd64.deb (--
unpack): 
 new mariadb-server-10.6 package pre-installation script subprocess returned error exit status 1 
Errors were encountered while processing: 
 /var/cache/apt/archives/mariadb-server-10.6_1%3a10.6.11-0ubuntu0.22.04.1_amd64.deb 
needrestart is being skipped since dpkg has failed 
E: Sub-process /usr/bin/dpkg returned an error code (1)
[/FONT]
```

```

[FONT=monospace][COLOR=#000000]ls -l /var/lib/mysql/ [/COLOR]
total 188876 
-rw-rw---- 1 mysql mysql    417792 Dec  4 11:29 aria_log.00000001 
-rw-rw---- 1 mysql mysql        52 Dec  4 11:29 aria_log_control 
-rw-rw---- 1 mysql mysql         9 Dec  4 11:29 ddl_recovery.log 
-rw-r--r-- 1 root  root          0 Nov 13 16:45 debian-.flag 
-rw-rw---- 1 mysql mysql      4287 Dec  4 11:29 ib_buffer_pool 
-rw-rw---- 1 mysql mysql 100663296 Dec  4 11:46 ib_logfile0 
-rw-rw---- 1 mysql mysql  79691776 Dec  4 11:29 ibdata1 
-rw-rw---- 1 mysql mysql  12582912 Dec  4 11:29 ibtmp1 
-rw-rw---- 1 mysql mysql         0 Nov 13 16:46 multi-master.info 
drwx------ 2 mysql root       4096 Nov 13 16:45 [COLOR=#5454ff]**mysql**[/COLOR][COLOR=#000000] [/COLOR]
-rw-r--r-- 1 mysql root         14 Nov 13 16:45 mysql_upgrade_info 
drwx------ 2 mysql mysql      4096 Nov 13 16:50 [COLOR=#5454ff]**owncloud**[/COLOR][COLOR=#000000] [/COLOR]
drwx------ 2 mysql root       4096 Nov 13 16:45 [COLOR=#5454ff]**performance_schema**[/COLOR][COLOR=#000000] [/COLOR]
drwx------ 2 mysql root      12288 Nov 13 16:45 [COLOR=#5454ff][B]sys
[/B][/COLOR]
[/FONT][FONT=monospace][COLOR=#000000]$apt-cache policy mariadb-server-10.6 [/COLOR]
mariadb-server-10.6: 
  Installed: 1:10.6.7-2ubuntu1.1 
  Candidate: 1:10.6.11-0ubuntu0.22.04.1 
  Version table: 
     1:10.6.11-0ubuntu0.22.04.1 500 
        500 http://us.archive.ubuntu.com/ubuntu jammy-updates/universe amd64 Packages 
        500 http://us.archive.ubuntu.com/ubuntu jammy-security/universe amd64 Packages 
 *** 1:10.6.7-2ubuntu1.1 100 
        100 /var/lib/dpkg/status 
     1:10.6.7-2ubuntu1 500 
        500 http://us.archive.ubuntu.com/ubuntu jammy/universe amd64 Packages

[/FONT]

```

---

### Post by pqwoerituytrueiwoq on 2022-12-12
[FONT=monospace][COLOR=#000000]deleting this file let it upgrade, no dataloss occurred, made a backup using [/COLOR][/FONT][FONT=monospace][FONT=courier new][COLOR=#000000]`sudo mysqldump --all-databases > sqldump.new`[/COLOR][/FONT]
[/FONT]
[FONT=monospace][COLOR=#000000]```
sudo rm /var/lib/mysql/debian-.flag
```[/COLOR][/FONT]

---

### Post by LHammonds on 2022-12-12
Thanks for letting us know how you resolved it.  Sorry I did not see this earlier.

LHammonds

---

