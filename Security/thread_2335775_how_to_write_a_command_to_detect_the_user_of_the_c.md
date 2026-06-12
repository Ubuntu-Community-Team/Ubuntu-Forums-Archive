---
title: "how to write a command to detect the user of the command it run?"
date: 2016-09-01
forum: Security
---

### Post by zerop2 on 2016-09-01
how to write a command to detect the user of the command it run?

assume a hacker enter the computer, he use sudo ls list file, 

but i had change sudo command path to for example, \hackers\playground\ls

when the hacker run, it will this fake command, of course it can prank hackers, 

but i want to do more, how to make this fake command detect the users of this command?

---

### Post by sudodus on 2016-09-01
ps reports a snapshot of the current processes. See ```
man ps
``` for details.

You can list all processes with with the command

```
ps -Af
```

You can post-process the result with several tools, for example

```
$ [COLOR="#0000FF"]ps -Af|head  # lists the head end of the file[/COLOR]
UID        PID  PPID  C STIME TTY          TIME CMD
root         1     0  0 07:28 ?        00:00:01 /sbin/init splash
root         2     0  0 07:28 ?        00:00:00 [kthreadd]
root         3     2  0 07:28 ?        00:00:00 [ksoftirqd/0]
root         5     2  0 07:28 ?        00:00:00 [kworker/0:0H]
root         7     2  0 07:28 ?        00:00:04 [rcu_sched]
root         8     2  0 07:28 ?        00:00:00 [rcu_bh]
root         9     2  0 07:28 ?        00:00:00 [migration/0]
root        10     2  0 07:28 ?        00:00:00 [watchdog/0]
root        11     2  0 07:28 ?        00:00:00 [watchdog/1]
$ [COLOR="#0000FF"]ps -Af | tail -n 20  # lists the tail end of the file (in this case 20 processes)[/COLOR]
nio       5351  5350  0 08:27 ?        00:00:00 gnome-pty-helper
nio       5352  5350  0 08:27 pts/0    00:00:00 /bin/bash
nio       5369  4300  0 08:27 pts/0    00:00:01 xfce4-terminal --title=terminal v --geometry 105x30+0-25
nio       5374  5369  0 08:27 pts/0    00:00:00 gnome-pty-helper
nio       5375  5369  0 08:27 pts/2    00:00:00 bash
nio       5392  5369  0 08:27 pts/3    00:00:00 bash
root      7826     2  0 10:54 ?        00:00:04 [kworker/1:1]
nio       7895  4300  0 11:02 ?        00:00:00 /usr/lib/gvfs/gvfsd-network --spawner :1.16 /org/gtk/gvfs/exec_spaw/2
nio       7909  4300  0 11:02 ?        00:00:00 /usr/lib/gvfs/gvfsd-dnssd --spawner :1.16 /org/gtk/gvfs/exec_spaw/4
root      7926     2  0 11:02 ?        00:00:01 [kworker/3:0]
root      7961     2  0 11:04 ?        00:00:01 [kworker/2:2]
root      8721     2  0 12:14 ?        00:00:00 [kworker/u16:0]
nio       8936  4300 11 12:41 ?        00:01:15 /usr/lib/firefox/firefox https://bugs.launchpad.net/bugs/1619188
root      9007     2  0 12:41 ?        00:00:00 [kworker/0:1]
root      9009     2  0 12:41 ?        00:00:00 [kworker/1:0]
root      9013     2  0 12:41 ?        00:00:00 [kworker/3:1]
root      9029     2  0 12:42 ?        00:00:00 [kworker/u16:2]
root      9087     2  0 12:49 ?        00:00:00 [kworker/u16:1]
nio       9115  5375  0 12:52 pts/2    00:00:00 ps -Af
nio       9116  5375  0 12:52 pts/2    00:00:00 tail -n 20
```

---

