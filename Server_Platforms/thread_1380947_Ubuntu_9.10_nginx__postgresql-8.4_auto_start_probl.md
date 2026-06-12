---
title: "Ubuntu 9.10 nginx / postgresql-8.4 auto start problem"
date: 2010-01-14
forum: Server Platforms
---

### Post by hovakkr on 2010-01-14
Hello,

I have a problem with making nginx and postgresql-8.4 auto start on boot on my notebook running Ubuntu 9.10. postgresql-8.4 was installed with apt-get but nginx-0.8.32 was installed using the makefile from the tar.gz  - there are no packages for it yet anyways. The /etc/rc.* K/S files exist but none of the /var/log files appear to mention nginx or psql at all - I have no idea why they do not start up on boot.

Any ideas? Any log files which might show something relevant? I am getting tired of having to start them up manually.

```

login as: travadkiyidwaranesel
travadkiyidwaranesel@207.46.232.182's password:
Linux atheos 2.6.31-17-generic #54-Ubuntu SMP Thu Dec 10 17:01:44 UTC 2009 x86_6                                                                                                                                4

To access official Ubuntu documentation, please visit:
http://help.ubuntu.com/

Last login: Tue Oct 20 02:08:04 2009
travadkiyidwaranesel@atheos:~$ telnet 127.0.0.1 80
Trying 127.0.0.1...
telnet: Unable to connect to remote host: Connection refused
travadkiyidwaranesel@atheos:~$ locate nginx | grep /etc
/etc/nginx
/etc/init.d/nginx
/etc/logrotate.d/nginx
/etc/nginx/fastcgi_params
/etc/nginx/koi-utf
/etc/nginx/koi-win
/etc/nginx/mime.types
/etc/nginx/nginx.conf
/etc/nginx/sites-available
/etc/nginx/sites-enabled
/etc/nginx/win-utf
/etc/nginx/sites-available/default
/etc/nginx/sites-enabled/default
/etc/rc0.d/K20nginx
/etc/rc1.d/K20nginx
/etc/rc2.d/S20nginx
/etc/rc3.d/S20nginx
/etc/rc4.d/S20nginx
/etc/rc5.d/S20nginx
/etc/rc6.d/K20nginx
/etc/ufw/applications.d/nginx
travadkiyidwaranesel@atheos:~$ sudo /etc/init.d/nginx start
[sudo] password for travadkiyidwaranesel:
Starting nginx: the configuration file /usr/local/nginx/conf/nginx.conf syntax is ok
configuration file /usr/local/nginx/conf/nginx.conf test is successful
nginx.
travadkiyidwaranesel@atheos:~$ telnet 127.0.0.1 80
Trying 127.0.0.1...
Connected to 127.0.0.1.
Escape character is '^]'.
^]
telnet> quit
Connection closed.
travadkiyidwaranesel@atheos:~$ locate postgresql | grep /etc
/etc/postgresql
/etc/postgresql-common
/etc/init.d/postgresql-8.4
/etc/logrotate.d/postgresql-common
/etc/postgresql/8.4
/etc/postgresql/8.4/main
/etc/postgresql/8.4/main/environment
/etc/postgresql/8.4/main/pg_ctl.conf
/etc/postgresql/8.4/main/pg_hba.conf
/etc/postgresql/8.4/main/pg_ident.conf
/etc/postgresql/8.4/main/postgresql.conf
/etc/postgresql/8.4/main/start.conf
/etc/postgresql-common/pg_upgradecluster.d
/etc/postgresql-common/root.crt
/etc/postgresql-common/user_clusters
/etc/rc0.d/K21postgresql-8.4
/etc/rc1.d/K21postgresql-8.4
/etc/rc2.d/S19postgresql-8.4
/etc/rc3.d/S19postgresql-8.4
/etc/rc4.d/S19postgresql-8.4
/etc/rc5.d/S19postgresql-8.4
/etc/rc6.d/K21postgresql-8.4
travadkiyidwaranesel@atheos:~$ telnet 127.0.0.1 5432
Trying 127.0.0.1...
telnet: Unable to connect to remote host: Connection refused
travadkiyidwaranesel@atheos:~$ sudo /etc/init.d/postgresql-8.4 start
 * Starting PostgreSQL 8.4 database server                                                                                                                                                               [ OK ]
travadkiyidwaranesel@atheos:~$ telnet 127.0.0.1 5432
Trying 127.0.0.1...
Connected to 127.0.0.1.
Escape character is '^]'.
^]
telnet> quit
Connection closed.
travadkiyidwaranesel@atheos:~$

```

---

