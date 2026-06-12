---
title: "Oracle XE works only with oracle user"
date: 2009-08-19
forum: Server Platforms
---

### Post by sandrocchio_0.1 on 2009-08-19
Ubuntu 8.10 Linux 2.6.27-14-generic

I have installed Oracle XE 10g on my laptop, during configuration I disabled the autostart at boot, everything worked fine, including web interface, till I rebooted.
The problem now is that Oracle processes are up, but I cannot connect unless I run sqlplus as oracle user.

Has any one experienced the same problem?

Thanks in advance
Alessandro Ilardo

---

### Post by Paul Weaver on 2009-08-24
Do you have the following environment variables set?

ORACLE_BASE=/usr/lib/oracle/xe
ORACLE_HOME=$ORACLE_BASE/app/oracle/product/10.2.0/server/
PATH=$PATH:$ORACLE_HOME/bin

Then run
 sqlplus user/password@xe

should do the trick. If you're still having issues, try 
 tnsping xe

I'm not sure about the web page thing, we've never needed it.

---

### Post by dragos2 on 2009-08-24
> **sandrocchio_0.1 said:**
> Ubuntu 8.10 Linux 2.6.27-14-generic

I have installed Oracle XE 10g on my laptop, during configuration I disabled the autostart at boot, everything worked fine, including web interface, till I rebooted.
The problem now is that Oracle processes are up, but I cannot connect unless I run sqlplus as oracle user.

Has any one experienced the same problem?

Thanks in advance
Alessandro Ilardo

This is a feature, not a bug!!! Add other users to dba group if
you want them to allow access.

---

### Post by Waappu on 2009-08-24
Hi,

Fix some issues you could add your user to DBA group
```
sudo usermod -a -G dba your_username
```
also fix issue that DBA group can not start listener
```
sudo chmod g+w /usr/lib/oracle/xe/app/oracle/product/10.2.0/server/network/log/listener.log
```

After this Gnome menu links "Start Database" and "Stop Database" should work.


If you like enable database auto start then
```
sudo nano /etc/default/oracle-xe
```
and change line
```
ORACLE_DBENABLED=false
```
to```
ORACLE_DBENABLED=true
```



Edit:

And get enviroment variables set correctly
```
sudo nano /etc/profile
```
add line end of file
```
. /usr/lib/oracle/xe/app/oracle/product/10.2.0/server/bin/oracle_env.sh
```
then
```
sudo cp /usr/lib/oracle/xe/app/oracle/product/10.2.0/server/bin/nls_lang.sh /usr/lib/oracle/xe/app/oracle/product/10.2.0/server/bin/nls_lang.sh_original
sudo nano /usr/lib/oracle/xe/app/oracle/product/10.2.0/server/bin/nls_lang.sh
```
and change first line
```
#!/bin/sh
```
to
```
#!/bin/bash
```

---

### Post by iansane on 2010-08-24
Hi,

I am having the same issue and even though it is "a feature not a bug"
I would like to get around it.

I tried all the above commands and nothing has changed. I am a member of dba.

I have to do "su oracle" before I can connect to sqlplus.

Here's the result of my tnsping xe

```
lotus@lotus:~$ tnsping xe

TNS Ping Utility for Linux: Version 10.2.0.1.0 - Production on 24-AUG-2010 21:16:46

Copyright (c) 1997, 2005, Oracle.  All rights reserved.

Used parameter files:


Used TNSNAMES adapter to resolve the alias
Attempting to contact (DESCRIPTION = (ADDRESS = (PROTOCOL = TCP)(HOST = lotus)(PORT = 1521)) (CONNECT_DATA = (SERVER = DEDICATED) (SERVICE_NAME = XE)))
OK (0 msec)
lotus@lotus:~$ 

```


This is the bottom of my .bashrc file

```
#oracle path setup
ORACLE_HOME=/usr/lib/oracle/xe/app/oracle/product/10.2.0/server
PATH=$PATH:$ORACLE_HOME/bin
export ORACLE_HOME
export ORACLE_SID=XE
export PATH
```

Any suggestions? Also should I reverse the changes made by Waapuu suggested fixes since none of them fixed my problem?

Thanks

---

### Post by Waappu on 2010-08-25
Hi,

Have you logout after you have made those fixes ?
Those fixes have work in Ubuntu version 8.04 - 10.4 for me.

You say you are on dba group.
What is result of
```

sqlplus '/as sysdba'

```
?

What login details you use when you connect to SQLplus ?

---

### Post by iansane on 2010-10-15
Hi Waappu,

Sorry I didn't get the email notification and I've been on other projects for a while is why I didn't respond.

Yes I have logged out and rebooted the system many times since I last posted hear. I am still using "su oracle" first in order to be able to log in to sqlplus.

Here is the result of sqlplus 'as/sysdba'

```

SQL*Plus: Release 10.2.0.1.0 - Production on Fri Oct 15 18:03:42 2010

Copyright (c) 1982, 2005, Oracle.  All rights reserved.

ERROR:
ORA-09925: Unable to create audit trail file
Linux Error: 13: Permission denied
Additional information: 9925
ORA-09925: Unable to create audit trail file
Linux Error: 13: Permission denied
Additional information: 9925


Enter user-name: sys
Enter password: 
ERROR:
ORA-01034: ORACLE not available
ORA-27123: unable to attach to shared memory segment
Linux Error: 13: Permission denied


Enter user-name: 

```
I get the same if I use 
sqlplus sys as sysdba


But this works.
```
lotus@lotus:~$ su oracle
Password: 
oracle@lotus:/home/lotus$ sqlplus sys as sysdba

SQL*Plus: Release 10.2.0.1.0 - Production on Fri Oct 15 18:09:11 2010

Copyright (c) 1982, 2005, Oracle.  All rights reserved.

Enter password: 

Connected to:
Oracle Database 10g Express Edition Release 10.2.0.1.0 - Production

SQL> select * from v$tablespace;

       TS#
----------
NAME
--------------------------------------------------------------------------------
INCLUDED_ BIGFILE   FLASHBACK ENCRYPT_I
--------- --------- --------- ---------
     0
SYSTEM
YES      NO        YES

     1
UNDO
YES      NO        YES

       TS#
----------
NAME
--------------------------------------------------------------------------------
INCLUDED_ BIGFILE   FLASHBACK ENCRYPT_I
--------- --------- --------- ---------

     2
SYSAUX
YES      NO        YES

     4
USERS

       TS#
----------
NAME
--------------------------------------------------------------------------------
INCLUDED_ BIGFILE   FLASHBACK ENCRYPT_I
--------- --------- --------- ---------
YES      NO        YES

     3
TEMP
NO      NO        YES


SQL> 

```

I can't do it without su oracle first like it's not exporting the path for my user (lotus)

Everything works like a charm using "oracle" user

Thanks

---

### Post by kentr on 2010-12-22
> **iansane said:**
> I can't do it without su oracle first like it's not exporting the path for my user (lotus)

Everything works like a charm using "oracle" user

Thanks

Old thread, I know.  But in case it helps someone, this worked for me:

After adding your user to the 'dba' group as mentioned above, fully log out of unix and re-login.

---

