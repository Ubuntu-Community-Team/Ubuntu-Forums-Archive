---
title: "Connection SQL Developer with Oracle 11g"
date: 2015-09-08
forum: Ubuntu Application Development
---

### Post by docevil on 2015-09-08
Hi,
I'm newbie at ubuntu OS and i'm programmer.


I have installed Oracle 11g database, which I acces on the ubuntu terminal loggin as "su - oracle" and introducing the commands "sqlplus / as sysdba" and I can login successfully.


But when I run my sql developer from the script .sh sqldeveloper and it show the SqlDeveloper IDE, I try to set the connection with:
     -Description: SysAdminConn
     -User: sqlplus
     -Password: "Mypassword"
     -Port: 1521(Default Port i didnt change it)
     -SID: XE(Default from Oracle 11g)
I get an insufficient privileges connection [COLOR=#000000][FONT=Times New Roman]**ORA-01031: Insufficient privileges error from SQLDEVELOPER**[/FONT][/COLOR]
Could someone tell me why is producing this problem? I have already tried user permisions on sqldeveloper files and it didn't changed anything... I add my root user to de dba group and the same happens...
I dont know what more can I do.

Thanks for your attention :)

---

