---
title: "Syslog Server STOPPED Logging 4/9/2014"
date: 2014-04-16
forum: Server Platforms
---

### Post by anthony27 on 2014-04-16
My syslog production server stopped logging as of 4/9/2014 and I cannot figure out what went wrong.. I knew permissions were played with, with the main syslog file, but I'm not sure if this could be the issue. I am currently running 13.10. Below are a few example permissions I have set up for my /var/log/syslog_clients/2014 folder, where all of the IP address of the hosts are logging live. (The IP address 192.168.1.1 etc has been replaced of the real IPs in my environment.)

drw-r--r-- 5 syslog syslog 4096 Apr  1 02:00 192.168.1.1
drw-r--r-- 3 syslog syslog 4096 Jan  2 05:58 192.168.1.2
drw-r--r-- 3 syslog syslog 4096 Jan  2 05:58 192.168.1.3

Filesystem             Size  Used Avail Use% Mounted on
/dev/mapper/vol1-root   92G  2.1G   85G   3% /
none                   4.0K     0  4.0K   0% /sys/fs/cgroup
udev                   3.9G  4.0K  3.9G   1% /dev
tmpfs                  799M  568K  798M   1% /run
none                   5.0M     0  5.0M   0% /run/lock
none                   3.9G     0  3.9G   0% /run/shm
none                   100M     0  100M   0% /run/user
/dev/mapper/vol1-var   822G   75G  706G  10% /var

---

### Post by SeijiSensei on 2014-04-16
> 
drw-r--r-- 5 syslog syslog 4096 Apr 1 02:00 192.168.1.1
drw-r--r-- 3 syslog syslog 4096 Jan 2 05:58 192.168.1.2
drw-r--r-- 3 syslog syslog 4096 Jan 2 05:58 192.168.1.3


Directories need the execute bit set, or programs won't be able to list the directory's contents.  The execute bit means something entirely different when it's applied to directories.  You can find dozens of discussions about Unix permissions from a Google search.

You should reset the permissions to 755 with chmod, e.g.,
```

cd /parent/of/the/directories
chmod 755 192*

```
will make all directories whose names start with "192" have the correct permissions.  If you want to prohibit anyone other than root and the syslog pseudo-user to view those logs, use 750 instead of 755.

You might want to look into why those directories have the wrong permissions.  By default new directories get 755 permissions.  So either you or someone you work with accidentally removed the execute bit from the directories on April 9th.

---

