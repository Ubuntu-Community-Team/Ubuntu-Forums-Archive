---
title: "start mysql problem after replacing my.cnf with my-huge.cnf"
date: 2010-09-26
forum: Server Platforms
---

### Post by ladydi711 on 2010-09-26
Hi,

I want to use the my-huge.cnf file, but when I replace /etc/mysql/my.cnf with the one in /usr/share/doc/mysql-server-5.1/examples/my-huge.cnf, mysql will not start; it is just hanging the process.  The only thing i'm seeing in log files is repeating 

Sep 26 06:42:51 caseaware kernel: [52647.422669] type=1505 audit(1285497770.990:1240):  operation="profile_replace" pid=28591 name="/usr/sbin/mysqld"
Sep 26 06:43:22 caseaware kernel: [52678.675282] type=1505 audit(1285497802.320:1241):  operation="profile_replace" pid=28662 name="/usr/sbin/mysqld"
Sep 26 06:43:53 caseaware kernel: [52709.703567] type=1505 audit(1285497833.420:1242):  operation="profile_replace" pid=28732 name="/usr/sbin/mysqld"

in the /var/log/messages file.

Any thoughts on why my-huge.cnf is not working?  I do this all the time in Red Hat ES, but this is my first attempt with ubuntu.  My version is Ubuntu-Server 10.04.1 LTS _Lucid Lynx_ - Release amd64 (20100816.2).

Thanks in Advance!

---

### Post by ladydi711 on 2010-09-26
I figured it out...

user            = mysql

was not in the my-huge.cnf file. adding it solved my problem.

---

