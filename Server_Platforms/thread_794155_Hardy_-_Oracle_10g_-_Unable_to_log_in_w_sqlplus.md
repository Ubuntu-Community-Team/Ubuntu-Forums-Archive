---
title: "Hardy - Oracle 10g - Unable to log in w/ sqlplus"
date: 2008-05-14
forum: Server Platforms
---

### Post by mrbrice on 2008-05-14
Greetings.

I've never used Oracle before, but it's been requested of me, so I've installed it, however, I'm having some trouble logging in. 

System:
Ubuntu 8.04
HARDY

As I'm unable to plug the server into the network, I'm having to download files and dependencies off another machine, copy them to usb drive, and move them over (quite a pain).

I downloaded and installed the .deb from Oracle (oracle-xe-universal_10.2.0.1-1.0_i386.deb)

I installed it just fine (no errors)

After installation I ran: /etc/init.d/oracle-xe configure

I configured it with default options and set the requested password as "password" (I know, bad password, but it's a test machine.)

After the configuration ran successfully, I included the following in my user's .bashrc :

```
ORACLE_HOME=/usr/lib/oracle/xe/app/oracle/product/10.2.0/server
PATH=${PATH}:$ORACLE_HOME/bin
export ORACLE_HOME
export ORACLE_SID=XE
export PATH
```

To test, I rebooted. The machine started without any issues, and shows the Net Listener, etc, started perfectly.

I then try to log in with 'sqlplus'. I'll make it simple:

```
#sqlplus

SQL*Plus: RElease 10.2.0.1.0 - Production on Wed May 14 09:11:30 2008

Copyright (c) 1982, 2005 Oracle. All rights reserved.

Enter user-name: sys (only user available from start?)
Enter password: password (password I set in configuration)
ERROR:
ORA-01034: ORACLE not available
ORA-27101: shared memory realm does not exist
Linux Error: 2: No such file or directory
```

Note: I get the same no matter which account I'm logged into the machine with (root/usera/userb/etc). 

This is about as far as I've gotten. I've googled all around for an answer to this. Seems other people have come across it, but nobody has a solid solution. 

Am I missing something? Am I doing something incorrect? I've never used Oracle before. It could be anything, but it feels like I'm close and I'm just doing something stupid.

Any help would be greatly appreciated. If you need any further information, just ask. 

Regards

---

### Post by Satisfied w/o Micro$oft on 2008-08-27
^Bump^

I am having exactly the same problem - are there any solutions for this?

:confused:

Thanks in advance.

---

### Post by lnxman on 2008-10-28
Another one, I've the same problem... the installation goes well but when I try to access with sqlplus I get the same error...
Does anyone have any ideas?

Pleaseeeeeeeeee [-o<

---

### Post by lykwydchykyn on 2008-10-28
Caveat:  I don't work with Oracle XE on Ubuntu, but I do work with Oracle Enterprise on SLES.  So things might be different.

Generally this error comes up when Oracle is not running.  Check /etc/oratab.  There should be a line referring to your instance of oracle.  At the end of the line is probably a "N", meaning "no, don't start the database instance automatically".  Change that to "Y", and restart Oracle.

If that doesn't work, try the following:
```

sqlpus "/ as sysdba"
startup

```

If any of this is way off base, it's probably due to differences between enterprise and XE, so sorry in advance if I'm just confusing things.

---

### Post by finite9 on 2008-10-29
The problem is that the instance is not running, ie the memory structures have not been started.  You need to go to terminal, make sure you got ORACLE_HOME and ORACLE_SID exported correctly and then type sqlplus

It should reply "connected to an inactive instance".

Type startup.  If it starts correctly then OK.  oratab is misleading because it will not automatically start your database for you just because there is a Y at the end of the line.  You need to create an init script that starts Oracle and stops oracle and then use rc-update.d to put the start/stop scripts in the right locations.

If you get an error when starting the database then post it here and i'll tell you what to do.

---

