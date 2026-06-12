---
title: "Log files, 2 users logged in?"
date: 2011-04-12
forum: Security
---

### Post by .Guest. on 2011-04-12
Hello, Ubuntu Forums. I am new to Linux and Ubuntu.  I read the log```
  user.log.1
```.  

I found this print out:
```

Apr  x 00:00:00 x nagios3: LOG ROTATION: DAILY
Apr  x 00:00:00 x nagios3: LOG VERSION: 2.0
Apr  x 00:00:00 x nagios3: CURRENT HOST STATE: localhost;UP;HARD;1;PING OK - Packet loss = 0%, RTA = 0.19 ms
Apr  x 00:00:00 x nagios3: CURRENT SERVICE STATE: localhost;Current Load;OK;HARD;1;OK - load average: 0.55, 0.47, 0.35

**Apr  x 00:00:00 x nagios3: CURRENT SERVICE STATE: localhost;Current Users;OK;HARD;**1;**USERS OK - _2 users currently logged in_**

Apr  x 00:00:00 x nagios3: CURRENT SERVICE STATE: localhost;Disk Space;CRITICAL;HARD;4;DISK CRITICAL - /home/xx/.gvfs is not accessible: Permission denied
Apr  x 00:00:00 x nagios3: CURRENT SERVICE STATE: localhost;HTTP;CRITICAL;HARD;4;Connection refused

**Apr  x 00:00:00 x nagios3: CURRENT SERVICE STATE: localhost;_SSH;CRITICAL;HARD;4;Connection refused_**
Apr  x 00:00:00 x nagios3: CURRENT SERVICE STATE: localhost;Total Processes;OK;HARD;1;PROCS OK: 153 processes
```

The line in bold is the security issue. There is only 1 user account on the system. There should only be 1 user logged in, not 2 users logged in. The remainder of the log file lists 1 user logged in, for similar log output. 2 users logged in does not appear again in the log file.

Does the second line of bold indicate that an attempt was made to log in to the system using SSH?

There was an internet connection interruption (no service) around the time of the log file event. The service did return, later.

Does that line indicate that an unauthorized user logged in to the system?

I am looking for help interpreting the above lines of log files. Thanks.

---

### Post by CharlesA on 2011-04-12
Try this:

```
who
```

To see who is logged in. Could be that you are connected to two different ssh sessions.

---

### Post by .Guest. on 2011-04-12
This is the printout from 

who

```
user tty
user pts
```

Is that what the log file means by 2 users logged in?

---

### Post by CharlesA on 2011-04-12
Yes.

---

