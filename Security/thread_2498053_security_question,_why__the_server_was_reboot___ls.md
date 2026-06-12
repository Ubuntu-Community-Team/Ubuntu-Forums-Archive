---
title: "security question, why  the server was reboot   ls -al /sys/fs/pstore"
date: 2024-05-28
forum: Security
---

### Post by ginatullin on 2024-05-28
Hello friends. 
The question of security reasons.
I have got the ubuntu 20.04 server
my server been reboot
i was in another place.
this method showed ->$  sudo ls -al /sys/fs/pstore  
total 0
drwxr-x--- 2 root root 0 May 28 12:59 .
drwxr-xr-x 9 root root 0 May 28 11:17   <--  what does it mean ?

there is no  value (May 28  11:17) in the another logs  such as 
 $ who 
$ last
The question why the ubuntu server was reboot?
Been the server  reboot remotely or the human reboot the server by hand? 
The domain of the server is izhone.ru  .
It is very important to me to, know this. Please help.

---

### Post by currentshaft on 2024-05-28
1

---

### Post by ginatullin on 2024-05-28
the  /var/log/auth.log
showed this =>
May 28 09:39:01 izhone CRON[17048]: pam_unix(cron:session): session closed for user root
May 28 10:09:01 izhone CRON[17142]: pam_unix(cron:session): session opened for user root by (uid=0)
May 28 10:09:01 izhone CRON[17142]: pam_unix(cron:session): session closed for user root
May 28 10:17:01 izhone CRON[17236]: pam_unix(cron:session): session opened for user root by (uid=0)
May 28 10:17:01 izhone CRON[17236]: pam_unix(cron:session): session closed for user root
May 28 10:39:01 izhone CRON[17344]: pam_unix(cron:session): session opened for user root by (uid=0)
May 28 10:39:01 izhone CRON[17344]: pam_unix(cron:session): session closed for user root
May 28 11:09:01 izhone CRON[17431]: pam_unix(cron:session): session opened for user root by (uid=0)
May 28 11:09:01 izhone CRON[17431]: pam_unix(cron:session): session closed for user root
May 28 12:59:27 izhone systemd-logind[1183]: New seat seat0.
May 28 12:59:27 izhone systemd-logind[1183]: Watching system buttons on /dev/input/event1 (Power Button)
May 28 12:59:27 izhone systemd-logind[1183]: Watching system buttons on /dev/input/event0 (Power Button)
May 28 12:59:27 izhone systemd-logind[1183]: Watching system buttons on /dev/input/event2 (HID 04f3:0103)
May 28 12:59:27 izhone systemd-logind[1183]: Watching system buttons on /dev/input/event3 (HID 04f3:0103 Consumer Control)
May 28 12:59:27 izhone systemd-logind[1183]: Watching system buttons on /dev/input/event4 (HID 04f3:0103 System Control)
May 28 12:59:28 izhone sshd[1241]: Server listening on 0.0.0.0 port 22.
May 28 12:59:28 izhone sshd[1241]: Server listening on :: port 22.

---

### Post by ginatullin on 2024-05-28
The $last showed 
server-user pts/3            Tue May 28 20:21   still logged in
server-user pts/3            Tue May 28 19:23 - 19:23  (00:00)
server-user pts/0            Tue May 28 18:01   still logged in
server-user pts/2            Tue May 28 13:38   still logged in
server-user pts/2            Tue May 28 13:20 - 13:20  (00:00)
server-user pts/1            Tue May 28 13:11   still logged in
server-user pts/0            Tue May 28 13:04 - 14:11  (01:06)
server-user tty1         logged in        Tue May 28 13:00   still logged in
      reboot   system boot  5.4.0-182-generi Tue May 28 12:59   still running

---

### Post by ginatullin on 2024-05-28
thank you for this reply. its important log file

---

### Post by TheFu on 2024-05-28
/sys/fs/ is a fake file system.  It isn't on real storage, just in RAM.

```
$ df /sys
Filesystem      Size  Used Avail Use% Mounted on
sysfs              0     0     0    - /sys
```

There are other pseudo-file systems on all Linux and Unix systems. These are how the kernel provides visibility into the running environment and configuration.  Because different kernel releases can change what is stored where, it isn't a good idea to seek information directly from these pseudo-file systems.  They aren't guaranteed to work. Usually OS services are provided to query this information, unless it is really deep information that the kernel writers didn't think anyone else would ever need.

For example, 
```
$ cpuinfo    # the published command
$ more /proc/cpuinfo  # /proc is a psuedo-file system with CPU information.
```


FWIW, every hacker I know will scrub the last.log if they can.  This is why enterprises have log servers and send all logs to them as events happen.  Much harder to hack a log file that isn't on the hacked system.   systemd+journald did some amazing things for remote logging that were a put of a hassle before.  As much as I often hate systemd, the logging and remote logging is FANTASTIC!

---

### Post by ginatullin on 2024-05-29
thank you for this help, you are truly friends.
So i decided up the security of the server. 
Video CCTV or ip camera  is important thing.
Anyone know the best soft on Linux ubuntu for the ip wireless or wired camera for security reasons ?
Also need reliable manual or instruction. The solution of question in process.

---

### Post by vbgf3 on 2024-06-16
Hi,

First determine what ports and ip addresses your camera uses. netstat can help.
Then you should set up a firewall. consult the ufw man files. ( I use iptables not ufw ). General best practice is to have Deny All rule at the bottom of the firewall rules list. 

Hope this helps.

---

