---
title: "Server crashed, where to begin"
date: 2011-10-25
forum: Server Platforms
---

### Post by bigmonmulgrew on 2011-10-25
Hi 
I'm running a ubuntu server 11.04 LAMP server. Its running on Virtual box under Windows 7 x64
It had been running for a few days and this morning crashed.
It wouldnt respond in a web browser, via ssh or even locally. Rebooted and its fine.

My linux knowledge is a little limited.
Wheres the best place to start troubleshooting.


FYI
The server is running a drupal 7.8 website.
I have installed phpmyadmin, everything else is the default LAMP + SSH server install from the CD.

---

### Post by karlson on 2011-10-25
> **bigmonmulgrew said:**
> Hi 
I'm running a ubuntu server 11.04 LAMP server. Its running on Virtual box under Windows 7 x64
It had been running for a few days and this morning crashed.
It wouldnt respond in a web browser, via ssh or even locally. Rebooted and its fine.

My linux knowledge is a little limited.
Wheres the best place to start troubleshooting.


FYI
The server is running a drupal 7.8 website.
I have installed phpmyadmin, everything else is the default LAMP + SSH server install from the CD.

/var/log/messages
/var/log/daemon.log

/var/log/messages.0
/var/log/daemon.log.0

---

### Post by bigmonmulgrew on 2011-10-25
I dont have any of those log files, unless they're stores somewhere else.
I've attached a file showing the log files I do have.

---

### Post by bigmonmulgrew on 2011-10-25
OK let me say again I have no idea what a lot of this means. Even if its not related to the crash I'd appreciate an explination.

Best I can tell my server went down just before 7am
I have this in my auth.log
```
Oct 25 06:58:49 mewebserver sshd[316]: Server listening on :: port 22.
Oct 25 06:58:49 mewebserver sshd[316]: Server listening on 0.0.0.0 port 22.
Oct 25 06:58:50 mewebserver sshd[316]: Received signal 15; terminating.
Oct 25 06:58:50 mewebserver sshd[477]: Server listening on 0.0.0.0 port 22.
Oct 25 06:58:50 mewebserver sshd[477]: Server listening on :: port 22.
```

Also theres lots of failed logon attempts. I mean 1000s. They come in batches with slightly different IPs but all look somethign like this.
```
Oct 24 22:06:22 mewebserver sshd[19811]: reverse mapping checking getaddrinfo for 178-162-239-192.local [178.162.239.192] failed - POSSIBLE BREAK-IN ATTEMPT!
Oct 24 22:06:22 mewebserver sshd[19811]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=178.162.239.192  user=root
Oct 24 22:06:24 mewebserver sshd[19811]: Failed password for root from 178.162.239.192 port 36613 ssh2
```

my apache access log only list 1 item around this time
```
[25/Oct/2011:06:58:55 +0100] "GET / HTTP/1.1" 200 10956 "-" "Mozilla/5.0 (Windows NT 6.1; WOW64) AppleWebKit/535.1 (KHTML, like Gecko) Chrome/14.0.835.202 Safari/535.1"
```

same with the apache error log. 1 item around the time of the crash
```
[Tue Oct 25 06:58:55 2011] [notice] Apache/2.2.17 (Ubuntu) PHP/5.3.5-1ubuntu7.3 with Suhosin-Patch configured -- resuming normal operations
```

The mysql error.log contains about a dozen entries around this time.
```
111025  6:58:52 [Note] Plugin 'FEDERATED' is disabled.
111025  6:58:53  InnoDB: Initializing buffer pool, size = 8.0M
111025  6:58:53  InnoDB: Completed initialization of buffer pool
InnoDB: The log sequence number in ibdata files does not match
InnoDB: the log sequence number in the ib_logfiles!
111025  6:58:53  InnoDB: Database was not shut down normally!
InnoDB: Starting crash recovery.
InnoDB: Reading tablespace information from the .ibd files...
InnoDB: Restoring possible half-written data pages from the doublewrite
InnoDB: buffer...
111025  6:58:54  InnoDB: Started; log sequence number 0 364850364
111025  6:58:54 [Warning] Neither --relay-log nor --relay-log-index were used; so replication may break when this MySQL server acts as a slave and has his hostname changed!! Please use '--relay-log=mewebserver-relay-bin' to avoid this problem.
111025  6:58:54 [Note] Slave SQL thread initialized, starting replication in log 'mysql-bin.000109' at position 9297351, relay log './mewebserver-relay-bin.000004' position: 5254525
111025  6:58:54 [Note] Event Scheduler: Loaded 0 events
111025  6:58:54 [Note] /usr/sbin/mysqld: ready for connections.
Version: '5.1.54-1ubuntu4'  socket: '/var/run/mysqld/mysqld.sock'  port: 3306  (Ubuntu)
111025  6:58:54 [ERROR] Slave SQL: Error 'Duplicate entry '27467' for key 'PRIMARY'' on query. Default database: 'abc'. Query: 'INSERT INTO accesslog (title, path, url, hostname, uid, sid, timer, timestamp) VALUES ('My account', 'user', 'http://www.abcdollshouse.com/user', '192.168.0.10', '2', '9q-JPwaj_nxFG32QmXp0OAX_jCVl3LfSWSrgeNkkfDM', '5604', '1319031333')', Error_code: 1062
```

kern.log contains a lot of entries around the time of the crash I'll post them later if necessary.

I cant see anything else relevant in any of the other log files

---

### Post by Demented ZA on 2011-10-26
The log around the crash only shows what happened when the system became aware of the crash. The problem could have occured before that. Also, if it is hardware related and the system froze, it could very well be that nothing useful was written to the logs.

I'd say first fire up clonezilla and make a full backup to an external drive of the entire system.

1) Now you can't mess anything up, even if the hardware doesn't fail.
2) If the drive is failing, errors could come up during the backup, and give you an idea of the root cause. Just hope you get your precious data off in tact at least.
3) Even if errors do not show up during the backup, it doesn't rule out hardware.

My reasoning for the above is that Linux is generally very well behaved. If its been running stable for a while and suddenly starts acting up, the first question you should ask "is what changed?". If updates are off, and the server is headless, and no-one logged in to change anything, then I doubt its software related. I'd start looking at hardware, but at this point I ask myself if I have enough backups.

Keep in mind that hardware is in a constant state of degradation. At some point it will fail. Thus a hardware failure is inevitable.

Once you are backed up, check the hardware first, since software depends on it. Also, its a lot easier to check and rule out. 

If you are satisfied that the hardware is healthy, move on to software. Ask yourself what the last changes were that you or anyone made to the server, regardless of how long ago. If you didn't reboot the machine at the time, it may still be related to the current problem. Check the update logs, and see what security updates have been installed. I've had security updates on an 11.04 system that stopped a service to update it, but had the line to start that service again commented out. Nothing on the server worked untill it was rebooted. (Sound familliar?) Although, I could still access the system with its screen+keyboard. The fact that you couldn't, led me to believe something more fundemental went wrong.

---

### Post by lisati on 2011-10-26
Once you've got your server up and running again, you might want to consider installing something like fail2ban to help keep out the people trying to access your machine without your permission.

---

### Post by bigmonmulgrew on 2011-10-26
Thanks for the input.
This server is already backed up. All files are backed up regularly. I have a virtual clone of this server which I can switch to.
I regularly backup the server files and also clone the HDD and I'm backing up to multiple destinations.
Backup sorted on to the problem.

The one I'm troubleshooting on is running in virtual box under windows 7. It had only been setup for a little over a week before the crash. Security updates are set on automatic.

Hardware is ok. The host system is behaving and I've ran a few disgnostics on that already. 

Granted its not been running for long but I'd not changed anything since the initial setup. I think it was running for 9 days before the crash. Only any automated security updates should have changed anything. How do I check this?

@lisati
I'd been planning to install fail2ban for a while, following a previous recomendation. I was going to wait until I'd resloved this issue but what the hell. I'll take a fresh clone of the HDD and install it when I get a moment.

---

