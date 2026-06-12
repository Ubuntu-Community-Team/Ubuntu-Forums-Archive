---
title: "SQL Server on Ubuntu error setup"
date: 2017-01-27
forum: Server Platforms
---

### Post by ekangal on 2017-01-27
[COLOR=#242729][FONT=Arial]I want to install ms-sql to my Ubuntu 16.04: [/FONT][/COLOR][https://docs.microsoft.com/en-us/sql/linux/sql-server-linux-setup-ubuntu](https://docs.microsoft.com/en-us/sql/linux/sql-server-linux-setup-ubuntu)

[COLOR=#242729][FONT=Arial]But when I try to set a password for the SA with the command [/FONT][/COLOR]**sudo /opt/mssql/bin/sqlservr-setup**[FONT=Arial][COLOR=#242729] I got error: "[/COLOR][/FONT][B]sqlservr: Debugger.cpp:531: static void Debugger::Print(const void *, unsigned int): Assertion `m_IsAttached' failed."
[/B][COLOR=#242729][FONT=Arial]How to solve a problem?

[/FONT][/COLOR]Thanks

Microsoft(R) SQL Server(R) Setup


You can abort setup at anytime by pressing Ctrl-C. Start this program
with the --help option for information about running it in unattended
mode.


The license terms for this product can be downloaded from
[http://go.microsoft.com/fwlink/?LinkId=746388](http://go.microsoft.com/fwlink/?LinkId=746388) and found
in /usr/share/doc/mssql-server/LICENSE.TXT.


Do you accept the license terms? If so, please type "YES": YES


Please enter a password for the system administrator (SA) account: 
Please confirm the password for the system administrator (SA) account: 


Setting system administrator (SA) account password...
**sqlservr: Debugger.cpp:531: static void Debugger::Print(const void *, unsigned int): Assertion `m_IsAttached' failed.**
Hint: You are currently not seeing messages from other users and the system.
      Users in the 'systemd-journal' group can see all messages. Pass -q to
      turn off this notice.
No journal files were opened due to insufficient permissions.
Hint: You are currently not seeing messages from other users and the system.
      Users in the 'systemd-journal' group can see all messages. Pass -q to
      turn off this notice.
No journal files were opened due to insufficient permissions.
tail: cannot open '/var/log/syslog' for reading: Permission denied
ls: cannot access '/var/opt/mssql/log/errorlog*': No such file or directory
ls: cannot access '/var/opt/mssql/log/exception.log': No such file or directory
ls: cannot access '/var/opt/mssql/log/SQLDu*.txt': No such file or directory
ls: cannot access '/var/opt/mssql/log/SQLDu*.mdmp': No such file or directory
ls: cannot access '/var/opt/mssql/log/system_health*': No such file or directory
nohup: redirecting stderr to stdout

---

### Post by deadflowr on 2017-01-28
*Thread moved to **Server Platforms**.*

---

### Post by darkod on 2017-01-28
It reports more errors, not just that one. Are you sure it installed correctly without errors?

You should probably post a question to MS because it's their product. Just because you are trying to install it on Ubuntu it doesn't mean we will have the answers, especially since this is new software. Plus I bet almost no one uses MS SQL on linux servers, for me it beats the point. That's why long time proven and stable solutions like mysql exist. Don't forget, this seems to be first steps for MS SQL on ubuntu, be prepared for many bugs and unexplained errors.

---

### Post by SeijiSensei on 2017-01-28
I've used PostgreSQL for decades now.  From Windows I connect to it via its ODBC driver.  I don't use MySQL unless something requires it like WordPress.  I can't see much reason to run MS-SQL on Linux either.  If you're a Windows shop, then run it on Windows.  If you prefer Linux servers, use one of the SQL servers with a long history on the platform.

---

### Post by Habitual on 2017-01-29
> **ekangal said:**
> No journal files were opened due to insufficient permissions.
...
No journal files were opened due to insufficient permissions.
tail: cannot open '/var/log/syslog' for reading: Permission denied

stands out,

---

