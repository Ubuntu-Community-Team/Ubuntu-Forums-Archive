---
title: "MySQL 5.7 Multiple Instances on Ubuntu 16.04 (systemd)"
date: 2017-01-17
forum: Server Platforms
---

### Post by voopoc on 2017-01-17
Hi Guys,

Anyone have an instruction on how to get multiple instances working on 16.04?  Its running systemd and I've been reading [https://dev.mysql.com/doc/refman/5.7/en/using-systemd.html#systemd-multiple-mysql-instances](https://dev.mysql.com/doc/refman/5.7/en/using-systemd.html#systemd-multiple-mysql-instances), however I feel that the systemd scripts aren’t correct and something is missing.

Thanks,

---

### Post by voopoc on 2017-01-18
it looks like scripts are missing and although I've resolved peaces to this, I have now moved to MariaDB, as it appears to have better support and scripts already deployed.

---

### Post by daishi on 2017-02-09
Would you elaborate on how you got everything working?

I am looking at

  [https://mariadb.com/kb/en/mariadb/systemd/](https://mariadb.com/kb/en/mariadb/systemd/)

and 

  [http://serverfault.com/questions/368204/what-is-the-debian-way-of-installing-multiple-mysql-instances-on-a-single-serv#368205](http://serverfault.com/questions/368204/what-is-the-debian-way-of-installing-multiple-mysql-instances-on-a-single-serv#368205)

and as you mention, I don't see the service files in /usr/lib/systemd/service or /lib/systemd/service.

It seems like the service file is automatically generated from the init-style script:

```

$ systemctl status mysql
&#9679; mysql.service - LSB: Start and stop the mysql database server daemon
   Loaded: loaded (/etc/init.d/mysql; bad; vendor preset: enabled)
   Active: active (running) since Thu 2017-02-09 18:20:18 UTC; 41min ago
     Docs: man:systemd-sysv-generator(8)
  Process: 3598 ExecStart=/etc/init.d/mysql start (code=exited, status=0/SUCCESS)
   CGroup: /system.slice/mysql.service
           &#9500;&#9472;3679 /bin/bash /usr/bin/mysqld_safe
           &#9500;&#9472;3888 /usr/sbin/mysqld --basedir=/usr --datadir=/var/lib/mysql --plugin-dir=/usr/lib/mysql/plugin --user=mysql --
           &#9492;&#9472;3889 logger -t mysqld -p daemon error

```

I am using mariadb like you instead of mysql:

```

$ dpkg -S /etc/init.d/mysql
mariadb-server-10.0: /etc/init.d/mysql
$ apt-cache policy mariadb-server-10.0
mariadb-server-10.0:
  Installed: 10.0.29-0ubuntu0.16.04.1
  Candidate: 10.0.29-0ubuntu0.16.04.1
  Version table:
 *** 10.0.29-0ubuntu0.16.04.1 500
        500 [http://mirrors.linode.com/ubuntu](http://mirrors.linode.com/ubuntu) xenial-updates/universe amd64 Packages
        500 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/universe amd64 Packages
        100 /var/lib/dpkg/status
     10.0.24-7 500
        500 [http://mirrors.linode.com/ubuntu](http://mirrors.linode.com/ubuntu) xenial/universe amd64 Packages

```

---

### Post by LHammonds on 2017-02-10
Don't know why you'd need to run multiple instances (maybe to isolate DB admins from different companies?) but this might be helpful:

[https://www.percona.com/blog/2014/08/26/mysqld_multi-how-to-run-multiple-instances-of-mysql/](https://www.percona.com/blog/2014/08/26/mysqld_multi-how-to-run-multiple-instances-of-mysql/)
[http://nirbhay.in/blog/2016/06/systemd-managing-multiple-mariadb-instances/](http://nirbhay.in/blog/2016/06/systemd-managing-multiple-mariadb-instances/)
[https://mariadb.com/kb/en/mariadb/running-multiple-copies-of-mariadb/](https://mariadb.com/kb/en/mariadb/running-multiple-copies-of-mariadb/)
[https://mariadb.com/kb/en/mariadb/mysqld-options/](https://mariadb.com/kb/en/mariadb/mysqld-options/)
[https://mariadb.com/kb/en/mariadb/mysqld-configuration-files-and-groups/](https://mariadb.com/kb/en/mariadb/mysqld-configuration-files-and-groups/)
[https://mariadb.com/kb/en/mariadb/mysqld_multi/](https://mariadb.com/kb/en/mariadb/mysqld_multi/)
[http://www.anntoin.com/Blog/Tutorials/MultipleDBInstances.html](http://www.anntoin.com/Blog/Tutorials/MultipleDBInstances.html)

And yes, please use MariaDB instead of MySQL.  MariaDB is a drop-in-replacement for MySQL and is updated regularly unlike MySQL.

---

