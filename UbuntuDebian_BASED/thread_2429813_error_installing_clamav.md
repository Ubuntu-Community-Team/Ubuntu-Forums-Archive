---
title: "error installing clamav"
date: 2019-10-23
forum: Ubuntu/Debian BASED
---

### Post by eliott32 on 2019-10-23
Hi I work in a school and we have installed MAX, a spanish educative operating system based  on Ubuntu. When installing the clamav antivirus in a computer it shows the following error: 
This is a translation from english:

[FONT=Arial]oct 17 13:37:13 PC-1PRI systemd[1]: Failed to start MySQL Community Server.[/FONT]
[FONT=Arial]oct 17 13:37:13 PC-1PRI systemd[1]: mysql.service: Unit entered failed state.[/FONT]
[FONT=Arial]oct 17 13:37:13 PC-1PRI systemd[1]: mysql.service: Failed with result 'timeout'.[/FONT]
[FONT=Arial]Hint: Some lines were ellipsized, use -l to show in full.[/FONT]
[FONT=Arial]dpkg: error processingmysql-server-5.7 package (--configure):  the thread installed thepost-installation script returned the error exit code 1 dpkg: dependencyproblems prevent mysql-server configuration:  mysql-server depends onmysql-server-5.7; but nevertheless:  The `mysql-server-5.7 'package is notconfigured yet. dpkg: error processing mysql-server package (--configure): dependency issues - left unconfigured Errors were encountered whileprocessing:  mysql-server-5.7  mysql-server Processing triggers formax ... E: Sub-process / usr / bin / dpkg returned an error code (1) Madrid @PC-1PRI: ~ $

Thanks for the support
[/FONT]

[FONT=arial]dpkg: error processing mysql-server-5.7 package (--configure): the thread installed the post-installation script returned the error exit code 1dpkg: dependency problems prevent mysql-server configuration: mysql-server depends on mysql-server-5.7; but nevertheless: The `mysql-server-5.7 'package is not configured yet.dpkg: error processing mysql-server package (--configure): dependency issues - left unconfiguredErrors were encountered while processing: mysql-server-5.7 mysql-serverProcessing triggers for max ...E: Sub-process / usr / bin / dpkg returned an error code (1)Madrid @ PC-1PRI: ~ $[/FONT]

---

### Post by wildmanne39 on 2019-10-23
*Thread moved to **Ubuntu/Debian BASED a more appropriate sub-forum**.*

---

### Post by SeijiSensei on 2019-10-23
Since clamav does not require MySQL to operate, I suspect this has something to do with the MAX software.

You could try installing MySQL manually:

```
sudo apt install mysql-server
```

but I'm not sure that will solve the problem.  The question remains what is the database that MySQL is supposed to be hosting? I'd guess that MAX should have installed a database for you, though I'm surprised it didn't throw an error when it didn't find MySQL.   Perhaps you might start from scratch on one machine and first install Ubuntu, then install clamav, then MySQL, then MAX.

---

### Post by eliott32 on 2019-10-23
ok thanks

---

