---
title: "libc - Ahsay OBM"
date: 2013-11-25
forum: Server Platforms
---

### Post by Philip2222 on 2013-11-25
Hi,
I have probelms to get Ahsay OBM client for Linux running due to problems with libc. I'm running Ubuntu Server 12.04.3 LTS. I get the following error: 
```

# sudo /usr/local/obm/bin/RunBackupSet.sh JAWEB01-File
Using APP_HOME:    : /usr/local/obm
Using BACKUP_SET   : JAWEB01-File
Using BACKUP_TYPE  : FILE
Using SETTING_HOME :
Using DELTA_MODE   :
Using DEBUG_MODE   : NO-DEBUG
[2013/11/25 21:25:00] Start [ Linux 3.5.0-43-generic (JAWEB01), AhsayOBM 6.15.0.0 ]
#
# A fatal error has been detected by the Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x00007fbe2c338134, pid=15889, tid=140454705903360
#
# JRE version: 6.0_23-b05
# Java VM: Java HotSpot(TM) 64-Bit Server VM (19.0-b09 mixed mode linux-amd64 compressed oops)
# Problematic frame:
# C  [libc.so.6+0x9a134]
#
# An error report file with more information is saved as:
# /usr/local/obm/bin/hs_err_pid15889.log
#
# If you would like to submit a bug report, please visit:
#   http://java.sun.com/webapps/bugreport/crash.jsp
# The crash happened outside the Java Virtual Machine in native code.
# See problematic frame for where to report the bug.
#
Aborted (core dumped)

```

I have tried to make symbolic links like this:
```

# ls -la /lib/libc.so.6
lrwxrwxrwx 1 root root 31 Nov 25 20:56 /lib/libc.so.6 -> /lib/x86_64-linux-gnu/libc.so.6

# ls -la /lib64/libc.so.6
lrwxrwxrwx 1 root root 31 Nov 25 20:59 /lib64/libc.so.6 -> /lib/x86_64-linux-gnu/libc.so.6

 ls -la /lib32/libc.so.6
lrwxrwxrwx 1 root root 12 Sep 30 17:06 /lib32/libc.so.6 -> libc-2.15.so

# ls -la /lib/x86_64-linux-gnu/libc.so.6
lrwxrwxrwx 1 root root 12 Sep 30 17:05 /lib/x86_64-linux-gnu/libc.so.6 -> libc-2.15.so

```

But that doesn't help... What went wrong?

---

