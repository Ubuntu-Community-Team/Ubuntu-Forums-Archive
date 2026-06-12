---
title: "Unknown root process"
date: 2009-04-17
forum: Security
---

### Post by sleepingdragon on 2009-04-17
I keep seeing an unknown root process when running htop (it doesn't appear in top). It only lists itself of "-:0", not the usual /usr/bin/whatever. Has anyone else seen this? It seems to have used no RAM and has no runtime (00:00:00). Am I looking at a possible rootkit?

Both rkhunter and chkrootkit show nothing.

---

### Post by cdenley on 2009-04-17
> **sleepingdragon said:**
> I keep seeing an unknown root process when running htop (it doesn't appear in top). It only lists itself of "-:0", not the usual /usr/bin/whatever. Has anyone else seen this? It seems to have used no RAM and has no runtime (00:00:00). Am I looking at a possible rootkit?

Both rkhunter and chkrootkit show nothing.

I don't see anything like that, but I'm running ubuntu 9.04. Do you have the PID from htop?
```

sudo ps -p [pid] -f
sudo lsof -p [pid]

```

---

### Post by sleepingdragon on 2009-04-17
yes, it's 5405

> 
dracnoc@DracNoc:~$ sudo ps -p 5405 -f
UID        PID  PPID  C STIME TTY          TIME CMD
root      5405  5383  0 10:20 ?        00:00:00 -:0
dracnoc@DracNoc:~$ sudo lsof -p 5405
COMMAND  PID USER   FD   TYPE     DEVICE    SIZE    NODE NAME
kdm     5405 root  cwd    DIR        8,1    4096       2 /
kdm     5405 root  rtd    DIR        8,1    4096       2 /
kdm     5405 root  txt    REG        8,1  130332 3006911 /usr/bin/kdm
kdm     5405 root  mem    REG        8,1   38412 3007842 /lib/tls/i686/cmov/libnss_files-2.7.so
kdm     5405 root  mem    REG        8,1   34352 3007846 /lib/tls/i686/cmov/libnss_nis-2.7.so
kdm     5405 root  mem    REG        8,1   30436 3007838 /lib/tls/i686/cmov/libnss_compat-2.7.so
kdm     5405 root  mem    REG        8,1   95948 2990205 /lib/libselinux.so.1
kdm     5405 root  mem    REG        8,1   38300 3007829 /lib/tls/i686/cmov/libcrypt-2.7.so
kdm     5405 root  mem    REG        8,1   83708 3007836 /lib/tls/i686/cmov/libnsl-2.7.so
kdm     5405 root  mem    REG        8,1   47372 2992343 /lib/security/pam_unix.so
kdm     5405 root  mem    REG        8,1   93832 3010057 /usr/lib/libxcb.so.1.0.0
kdm     5405 root  mem    REG        8,1    4172 3010055 /usr/lib/libxcb-xlib.so.0.0.0
kdm     5405 root  mem    REG        8,1 1364388 3007825 /lib/tls/i686/cmov/libc-2.7.so
kdm     5405 root  mem    REG        8,1    9696 3007859 /lib/tls/i686/cmov/libutil-2.7.so
kdm     5405 root  mem    REG        8,1   67408 3007853 /lib/tls/i686/cmov/libresolv-2.7.so
kdm     5405 root  mem    REG        8,1  214624 3009378 /usr/lib/libdbus-1.so.3.4.0
kdm     5405 root  mem    REG        8,1    9684 3007831 /lib/tls/i686/cmov/libdl-2.7.so
kdm     5405 root  mem    REG        8,1   37956 2990186 /lib/libpam.so.0.81.6
kdm     5405 root  mem    REG        8,1   16616 3009216 /usr/lib/libXdmcp.so.6.0.0
kdm     5405 root  mem    REG        8,1    6988 3009205 /usr/lib/libXau.so.6.0.0
kdm     5405 root  mem    REG        8,1  944876 3009199 /usr/lib/libX11.so.6.2.0
kdm     5405 root  mem    REG        8,1    3056 2992331 /lib/security/pam_permit.so
kdm     5405 root  mem    REG        8,1   12628 2992322 /lib/security/pam_limits.so
kdm     5405 root  mem    REG        8,1   11612 2992312 /lib/security/pam_env.so
kdm     5405 root  mem    REG        8,1    4336 2992330 /lib/security/pam_nologin.so
kdm     5405 root  mem    REG        8,1  109152 2990099 /lib/ld-2.7.so
kdm     5405 root    0r   CHR        1,3            6932 /dev/null
kdm     5405 root    1w   REG        8,1    2057  229727 /var/log/kdm.log
kdm     5405 root    2w   REG        8,1    2057  229727 /var/log/kdm.log
kdm     5405 root    3u  unix 0xf6fe2a00           14440 socket
kdm     5405 root    4u  unix 0xf77b5e00           14871 socket
kdm     5405 root    6u  unix 0xdfac4800           14431 socket
kdm     5405 root   11r  FIFO        0,5           14436 pipe
kdm     5405 root   14w  FIFO        0,5           14437 pipe
kdm     5405 root   15r  FIFO        0,5           14438 pipe
kdm     5405 root   18w  FIFO        0,5           14439 pipe


---

### Post by cdenley on 2009-04-17
That definitely looks like KDM, the KDE login manager. You must be running kubuntu. Apparently it is a child process of KDM which hides it's arguments for some reason.
[http://www.unix.com/unix-dummies-questions-answers/16381-kdm-child-process.html](http://www.unix.com/unix-dummies-questions-answers/16381-kdm-child-process.html)
It does not appear to be anything you should be concerned about.

---

### Post by sleepingdragon on 2009-04-17
Yes, I am running KDM. Thanks for the info - there should be some decent documentation about that sort of thing. Finding that on your process list can make a man lose control of his lunch.

---

### Post by cdenley on 2009-04-17
[http://bugs.kde.org/show_bug.cgi?id=92325](http://bugs.kde.org/show_bug.cgi?id=92325)

---

