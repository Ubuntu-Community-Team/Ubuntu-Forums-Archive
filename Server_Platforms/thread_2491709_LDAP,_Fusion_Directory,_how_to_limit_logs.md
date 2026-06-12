---
title: "LDAP, Fusion Directory, how to limit logs?"
date: 2023-10-18
forum: Server Platforms
---

### Post by civilpolisen on 2023-10-18
```
2002-2023 [The FusionDirectory team, 1.3]("http://www.fusiondirectory.org")
```

We are not many people at the office but the log file fills up in no-time! The software is very "talky", so to speak! Talk much and logs it all!
Somewhere in the user interface there is a setting on these things... where is that!?

I enclose the screenshot, just for reference!

---

### Post by TheFu on 2023-10-18
/etc/systemd/journald.conf is where log size configuration can be addressed, assuming the tool uses the system to handle logging.
The manpage for journald.conf is fairly extensive and explains all the settings possible.  Date, size, numbers of log files .... all configurable.  

Don't forget logrotate for the older style logs. There are lots of examples in the logrotate.d/ directory.

Forget GUIs for this stuff. Doesn't exist.

---

### Post by civilpolisen on 2023-10-19
Thank you for your advice! There were no such file as logrotate, but I made earlier in this week. Maybe that was the trick?
Bbecause after this, the server seem to behave!

```
civilpolisen@ldap:~$ cat /etc/logrotate.d/ldap
/var/log/ldap.log {
       copytruncate
       daily
       rotate 7
       delaycompress
       compress
       notifempty
       missingok
}

/var/log/slapd.log {
       copytruncate
       daily
       rotate 7
       delaycompress
       compress
       notifempty
       missingok
}
civilpolisen@ldap:~$ df -h
Filesystem                         Size  Used Avail Use% Mounted on
udev                               1.9G     0  1.9G   0% /dev
tmpfs                              390M  1.1M  389M   1% /run
/dev/mapper/ubuntu--vg-ubuntu--lv   19G  6.0G   12G  34% /
tmpfs                              2.0G     0  2.0G   0% /dev/shm
tmpfs                              5.0M     0  5.0M   0% /run/lock
tmpfs                              2.0G     0  2.0G   0% /sys/fs/cgroup
/dev/loop2                          64M   64M     0 100% /snap/core20/1974
/dev/vda2                          974M  152M  755M  17% /boot
/dev/loop6                          64M   64M     0 100% /snap/core20/2015
/dev/loop0                          41M   41M     0 100% /snap/snapd/20092
/dev/loop1                          46M   46M     0 100% /snap/certbot/3369
/dev/loop5                          41M   41M     0 100% /snap/snapd/20290
/dev/loop3                          46M   46M     0 100% /snap/certbot/3390
tmpfs                              390M     0  390M   0% /run/user/1002
civilpolisen@ldap:~$ 
```

---

### Post by TheFu on 2023-10-19
Daily is common, but you can also use the size to force a rotation, if that works better.  For security related things, I keep at least 6 months of logs. Just sayin'.

Also, your df command is showing a bunch of fake storage. May want to setup an alias to remove that.  I use
```
alias dft='df -hT -x squashfs -x tmpfs -x devtmpfs'
```
so I don't get bogged down with useless junk in the output.  In 23.10, looks like the df command has been changed to remove the snap loop devices in some way.

---

