---
title: "Rootkit?: auth.log doesn't log anything"
date: 2008-05-09
forum: Security
---

### Post by bongoMaster on 2008-05-09
Hello,

I'm running kubuntu hardy up-to-date on my 32bit PC.

Yesterday I saw unexpected traffic on my network interface. I checked what's going on with netstat and lsof, and saw that a japanese computer was ssh-connected to my machine. Here the relevant line of lsof:

```
sshd      16376       sshd    3u     IPv6     411900                 TCP noname:ssh->pro-500-210.kagoya.net:33334 (ESTABLISHED)

```

unfortunaly I didn't save the output of netstat, so I can't show you, but the information it contained was approximatively the same. There was one active connection to this machine and several in the "TIME-WAIT" state.

I wanted to get more infos from /var/log/auth.log, but nothing got logged there since 3 hours before I noticed the attack. Normaly CRON logs things there ~ every 20 min, but that didn't happen too. I tried to ssh from another computer into my machine, and it didn't get logged... That makes me feel perplex, am I the victim of a root kit?

The output of lsof would be the same if someone tries to connect but didn't enter a password yet, so I cannot be sure that someone effectively got access to my pc. If there wasn't those lacking logs in auth.log, I wouldn't mind about those lsof/netstat outputs....

I checked for rootkits with rkhunter (latest, self compiled version), but it didn't find any problems. How reliable is this program? I also checked for viruses or trojans with clamav, with no results. Any ideas of what kind of other checks I could do? Should I reinstall my complete system? Does somebody know what process is responsible for logging to auth.log, is it sshd itself?

Any hints would be highly appreciated :confused:

have fun
Pascal

---

### Post by Monicker on 2008-05-09
Check the SyslogFacility option in /etc/ssh/sshd_config.  What is it set to?

Mine is this:

```
SyslogFacility AUTH
```

---

### Post by bongoMaster on 2008-05-09
I have the same entry. I disallowed root-logins, apart from that I left sshd_config as it was.

have fun
Pascal

---

### Post by Monicker on 2008-05-09
Hrmm. Are syslogd and klogd both running?

ps aux|grep log

---

### Post by bongoMaster on 2008-05-09
Now they are running, I couldn't say for sure that they were running yesterday, but they should, I didn't change any configurations...

```
pp@bongo:~$ ps aux | grep log
root      5253  0.0  0.0   1752   444 ?        Ss   11:15   0:00 /sbin/bootlogd -r
syslog    5506  0.0  0.0   1936   644 ?        Ss   11:15   0:00 /sbin/syslogd -u syslog
root      5566  0.0  0.0   1868   536 ?        S    11:15   0:00 /bin/dd bs 1 if /proc/kmsg of /var/run/klogd/kmsg
klog      5569  0.0  0.1   3788  2704 ?        Ss   11:15   0:00 /sbin/klogd -P /var/run/klogd/kmsg
root      5871  0.0  0.0   1700   556 ?        S    11:15   0:00 logger -p daemon.err -t mysqld_safe -i -t mysqld
pp       19074  0.0  0.0   3016   788 pts/3    S+   15:52   0:00 grep log

```

---

### Post by bongoMaster on 2008-05-09
Hi,

now i have the same situation again, that nothing got logged to /var/log/auth.log since 4 pm (it's now 7 pm). I checked all possible logs and couldn't find evidence for an intrusion. The output of 'lastlog' is ok too. netstat says that there are no others connected, and there is no traffic on the network. All loggers are up and running without interruption since I booted my computer at 11:15am:

```
pp@bongo:~$ ps aux | grep log
root      5253  0.0  0.0   1752   444 ?        Ss   11:15   0:00 /sbin/bootlogd -r
syslog    5506  0.0  0.0   1936   644 ?        Ss   11:15   0:00 /sbin/syslogd -u syslog
root      5566  0.0  0.0   1868   536 ?        S    11:15   0:00 /bin/dd bs 1 if /proc/kmsg of /var/run/klogd/kmsg
klog      5569  0.0  0.1   3788  2704 ?        Ss   11:15   0:00 /sbin/klogd -P /var/run/klogd/kmsg
root      5871  0.0  0.0   1700   556 ?        S    11:15   0:00 logger -p daemon.err -t mysqld_safe -i -t mysqld
pp       27166  0.0  0.0   3012   760 pts/2    R+   19:15   0:00 grep log

```


But again, if I ssh to my computer nothing gets logged :confused:
I no longer think that I have been hacked, I would rather think that hardy has problems with logging to auth.log. It wouldn't be the first annoying new bug that came with hardy ;) Any ideas? I would like to know which process writes to auth.log, is it sshd, sylogd, klogd, ... ?

have fun
Pascal

---

### Post by bongoMaster on 2008-05-09
> I would like to know which process writes to auth.log, is it sshd, sylogd, klogd, ... ?

ok, now I know that it's syslogd, I restarted it and now ssh logins are logged again...

---

