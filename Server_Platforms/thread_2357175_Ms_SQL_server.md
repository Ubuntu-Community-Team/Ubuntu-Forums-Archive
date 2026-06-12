---
title: "Ms SQL server"
date: 2017-03-30
forum: Server Platforms
---

### Post by degan2 on 2017-03-30
Hi
I am a beginner linux user.
I'm trying to install MS SQL server. ( [https://docs.microsoft.com/en-us/sql/linux/sql-server-linux-setup-ubuntu](https://docs.microsoft.com/en-us/sql/linux/sql-server-linux-setup-ubuntu) )
System version: Ubuntu Server 16.04.2 LTS


I have an error while sudo / opt / mssql / bin / mssql-conf setup


Setting up Microsoft SQL Server
Enter the new SQL Server system administrator password:
Confirm the new SQL Server system administrator password:
Ls: can not access '/ var / opt / mssql / log / errorlog *': No such file or directory
Ls: can not access '/var/opt/mssql/log/exception.log': No such file or directory
Ls: can not access '/var/opt/mssql/log/SQLDu*.txt': No such file or directory
Ls: can not access '/var/opt/mssql/log/SQLDu*.mdmp': No such file or directory
Ls: can not access '/ var / opt / mssql / log / system_health *': No such file or directory
Nohup: redirecting stderr to stdout
Failed to change administrator password with error code 1.
Please check the log setup in /var/opt/mssql/log/setup-20170329-153059.log.
For more information.


The problem does not look very difficult, but I'm already fighting him for the third day. Please help.

---

### Post by cariboo on 2017-03-30
Have a look [here]("http://askubuntu.com/questions/850957/how-do-i-install-mssql-server-and-or-tools-for-linux-on-16-04"), it may help.

---

