---
title: "Can't install MariaDB 5.5 or 10 in Ubuntu 12.04. MYSQLD Failed to start?"
date: 2013-04-27
forum: Server Platforms
---

### Post by THPubs on 2013-04-27
I tried o install MariaDB on my Ubuntu 12.04 server. First it gave dependency issues and I fixed it by following this question : [http://stackoverflow.com/questions/16214517/installing-mariadb-unmet-dependencies-mariadb-server-5-5](http://stackoverflow.com/questions/16214517/installing-mariadb-unmet-dependencies-mariadb-server-5-5)


But when installing mariadb-server, it fails to start the mysqld. Here is the apt log :

```
    root@sinha:/etc/apt# sudo apt-get install mariadb-server
    Reading package lists... Done
    Building dependency tree       
    Reading state information... Done
    The following extra packages will be installed:
      libdbd-mysql-perl libmariadbclient18 libmysqlclient18 mariadb-client-10.0 mariadb-client-core-10.0 mariadb-common mariadb-server-10.0 mariadb-server-core-10.0 mysql-common
    Suggested packages:
      tinyca mailx mariadb-test
    The following NEW packages will be installed:
      libdbd-mysql-perl libmariadbclient18 mariadb-client-10.0 mariadb-client-core-10.0 mariadb-common mariadb-server mariadb-server-10.0 mariadb-server-core-10.0
    The following packages will be upgraded:
      libmysqlclient18 mysql-common
    2 upgraded, 8 newly installed, 0 to remove and 0 not upgraded.
    Need to get 30.8 MB of archives.
    After this operation, 105 MB of additional disk space will be used.
    Do you want to continue [Y/n]? y
    Get:1 http://mirrors.supportex.net/mariadb/repo/10.0/ubuntu/ precise/main mysql-common all 10.0.1-mariadb1~precise [8,826 B]
    Get:2 http://mirrors.supportex.net/mariadb/repo/10.0/ubuntu/ precise/main mariadb-common all 10.0.1-mariadb1~precise [3,304 B]
    Get:3 http://lk.archive.ubuntu.com/ubuntu/ precise/main libdbd-mysql-perl amd64 4.020-1build2 [106 kB]
    Get:4 http://mirrors.supportex.net/mariadb/repo/10.0/ubuntu/ precise/main libmariadbclient18 amd64 10.0.1-mariadb1~precise [846 kB]
    Get:5 http://mirrors.supportex.net/mariadb/repo/10.0/ubuntu/ precise/main libmysqlclient18 amd64 10.0.1-mariadb1~precise [2,956 B]
    Get:6 http://mirrors.supportex.net/mariadb/repo/10.0/ubuntu/ precise/main mariadb-client-core-10.0 amd64 10.0.1-mariadb1~precise [1,814 kB]
    Get:7 http://mirrors.supportex.net/mariadb/repo/10.0/ubuntu/ precise/main mariadb-client-10.0 amd64 10.0.1-mariadb1~precise [5,103 kB]
    Get:8 http://mirrors.supportex.net/mariadb/repo/10.0/ubuntu/ precise/main mariadb-server-core-10.0 amd64 10.0.1-mariadb1~precise [5,517 kB]
    Get:9 http://mirrors.supportex.net/mariadb/repo/10.0/ubuntu/ precise/main mariadb-server-10.0 amd64 10.0.1-mariadb1~precise [17.4 MB]
    Get:10 http://mirrors.supportex.net/mariadb/repo/10.0/ubuntu/ precise/main mariadb-server all 10.0.1-mariadb1~precise [2,992 B]
    Fetched 30.8 MB in 1s (17.0 MB/s)      
    Preconfiguring packages ...
    (Reading database ... 119368 files and directories currently installed.)
    Preparing to replace mysql-common 5.5.31-0ubuntu0.12.04.1 (using .../mysql-common_10.0.1-mariadb1~precise_all.deb) ...
    Unpacking replacement mysql-common ...
    Selecting previously unselected package mariadb-common.
    Unpacking mariadb-common (from .../mariadb-common_10.0.1-mariadb1~precise_all.deb) ...
    Selecting previously unselected package libmariadbclient18.
    Unpacking libmariadbclient18 (from .../libmariadbclient18_10.0.1-mariadb1~precise_amd64.deb) ...
    Preparing to replace libmysqlclient18 5.5.31-0ubuntu0.12.04.1 (using .../libmysqlclient18_10.0.1-mariadb1~precise_amd64.deb) ...
    Unpacking replacement libmysqlclient18 ...
    Selecting previously unselected package libdbd-mysql-perl.
    Unpacking libdbd-mysql-perl (from .../libdbd-mysql-perl_4.020-1build2_amd64.deb) ...
    Selecting previously unselected package mariadb-client-core-10.0.
    Unpacking mariadb-client-core-10.0 (from .../mariadb-client-core-10.0_10.0.1-mariadb1~precise_amd64.deb) ...
    Selecting previously unselected package mariadb-client-10.0.
    Unpacking mariadb-client-10.0 (from .../mariadb-client-10.0_10.0.1-mariadb1~precise_amd64.deb) ...
    Selecting previously unselected package mariadb-server-core-10.0.
    Unpacking mariadb-server-core-10.0 (from .../mariadb-server-core-10.0_10.0.1-mariadb1~precise_amd64.deb) ...
    Processing triggers for man-db ...
    Setting up mysql-common (10.0.1-mariadb1~precise) ...
    Installing new version of config file /etc/mysql/my.cnf ...
    Setting up mariadb-common (10.0.1-mariadb1~precise) ...
    Selecting previously unselected package mariadb-server-10.0.
    (Reading database ... 119534 files and directories currently installed.)
    Unpacking mariadb-server-10.0 (from .../mariadb-server-10.0_10.0.1-mariadb1~precise_amd64.deb) ...
    Selecting previously unselected package mariadb-server.
    Unpacking mariadb-server (from .../mariadb-server_10.0.1-mariadb1~precise_all.deb) ...
    Processing triggers for ureadahead ...
    ureadahead will be reprofiled on next reboot
    Processing triggers for man-db ...
    Setting up libmysqlclient18 (10.0.1-mariadb1~precise) ...
    Setting up libdbd-mysql-perl (4.020-1build2) ...
    Setting up libmariadbclient18 (10.0.1-mariadb1~precise) ...
    Setting up mariadb-client-core-10.0 (10.0.1-mariadb1~precise) ...
    Setting up mariadb-client-10.0 (10.0.1-mariadb1~precise) ...
    Setting up mariadb-server-core-10.0 (10.0.1-mariadb1~precise) ...
    Setting up mariadb-server-10.0 (10.0.1-mariadb1~precise) ...
     * Stopping MariaDB database server mysqld                                                                                                                                                              [ OK ] 
    130427 13:43:14 [Note] Plugin 'InnoDB' is disabled.
    130427 13:43:14 [Note] Plugin 'FEEDBACK' is disabled.
     * Starting MariaDB database server mysqld                                                                                                                                                              [fail] 
    invoke-rc.d: initscript mysql, action "start" failed.
    dpkg: error processing mariadb-server-10.0 (--configure):
     subprocess installed post-installation script returned error exit status 1
    dpkg: dependency problems prevent configuration of mariadb-server:
     mariadb-server depends on mariadb-server-10.0; however:
      Package mariadb-server-10.0 is not configured yet.
    dpkg: error processing mariadb-server (--configure):
     dependency problems - leaving unconfigured
    Processing triggers for libc-bin ...
    ldconfig deferred processing now taking place
    No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                              Errors were encountered while processing:
     mariadb-server-10.0
     mariadb-server
    E: Sub-process /usr/bin/dpkg returned an error code (1)

```


Tried re installing mariadb-server, purged everything... removed mysql packages, installed mariadb-server-5.5... Nothing works.

---

### Post by sandyd on 2013-04-27
what does
```

sudo /etc/init.d/mysql-server restart
```
output?

---

### Post by HiddenFly on 2013-04-28
Have you tried using "apt-get install -f"? It might help specifically after that output you pasted.

---

### Post by jill-f on 2013-11-29
I am having the exact same problems in Raring Ringtail. Messages are identical except I'm installing mariadb 5.5.34. I tried all the suggested fixes and none works.
I've seen suggestions to purge all mysql & mariadb with 
sudo apt-get purge mysql* mariadb* && sudo apt-get autoclean && sudo apt-get autoremove
in order to get a clean install, but I'm afraid that that might remove my databases. I have a backup but have never tried resoring and have had problems two weeks ago with losing all my work and having to recreate it. Mariadb is on the localhost.

What is the recommended method to recover from this error?

I'm growing increasingly frustrated and worried that my application, which is slated for delivery in a couple of weeks to client, will not be ready, or that it will be prone to crashing.

Thanks for any help.

---

### Post by HiddenFly on 2013-11-29
If you wish to be sure you can restore, backup the folder /var/lib/mysql. That contains all the information the MySQL uses (except configuration and possible encryption keys). Be sure to not touch it while the server is running, though!

You can then restore after the package has been installed.

Though, it might be wise to check these logs for any errors as well:

/var/log/syslog
/var/log/mysql*
/var/lib/mysql/<hostname>.err

They might contain useful information on why it failed if the issue happened while the server was starting up.

---

