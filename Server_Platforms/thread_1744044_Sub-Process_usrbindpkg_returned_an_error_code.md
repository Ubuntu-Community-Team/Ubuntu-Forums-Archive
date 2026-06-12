---
title: "Sub-Process /usr/bin/dpkg returned an error code"
date: 2011-04-30
forum: Server Platforms
---

### Post by thoufiq on 2011-04-30
Hello All,
              I am the new user of linux and i have installed ubuntu server 10.10. When giving the command **[COLOR=Red]sudo apt-get install mysql-server-5.1[/COLOR]**, it shows error like this

[B][COLOR=Red]dpkg: error processing /var/cache/apt/archives/mysql-server-5.1_5.1.49-1ubuntu8.1_i386.deb
tryng to overwrite '/etc/init.d/mysql' , which is also in package mysql-server 5.1.49-1ubuntu8.1
No apport report written because MaxReports is reached already
Errors were encountered while processing:
/var/cache/apt/archives/mysql-server-5.1_5.1.49-1ubuntu8.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)[/COLOR][/B]

And i got the same error while giving [B][COLOR=Red]sudo apt-get -f upgrade[COLOR=Black].[/COLOR]
[/COLOR][/B]

Thanks in advance

---

