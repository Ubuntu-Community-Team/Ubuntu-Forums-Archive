---
title: "Logs advice when using SSH"
date: 2010-07-15
forum: Security
---

### Post by mr-woof on 2010-07-15
hi all,

i've been conducting a bit of an experiment lately, i've got an old dell poweredge 1750 with esxi 3.5 installed. I've setup ubuntu server 10.04 with ssh server, disabled root, changed password to keys, changed the port from 22 to 443, installed fail2ban etc

SSH was working inside the network from my little netbook, so the next test was to open a port on the router to the ubuntu server and try it from my 3g dongle on the netbook, works fine :) 

So this morning, I turned it on, tested it from inside the network and then the 3g dongle all fine, and went to work. The idea was to try and connect from our work network, to see if the firewalls/proxy servers would let it through. Well no connection, connection timed out etc. 

So I get home, the dell server is still on but I cant ping it etc, log into the esx console and the ubuntu server is off..I can't see anything in the logs, apart from:

Jul 15 08:33:40 Server1 sshd[1052]: Connection from x.x.x.x port 61082
Jul 15 08:33:43 Server1 sshd[1052]: Found matching RSA key: 46:0a:6d:05:b4:27:fe:2f:22:a6:71:ff:47:42:3e:14
Jul 15 08:33:43 Server1 sshd[1052]: Found matching RSA key: 46:0a:6d:05:b4:27:fe:2f:22:a6:71:ff:47:42:3e:14
Jul 15 08:33:43 Server1 sshd[1052]: Accepted publickey for me from x.x.x.x port 61082 ssh2
Jul 15 08:33:43 Server1 sshd[1052]: pam_unix(sshd:session): session opened for user me by (uid=0)
Jul 15 08:33:45 Server1 sshd[1052]: User child is on pid 1108
Jul 15 08:34:16 Server1 sshd[1108]: Received disconnect from x.x.x.x: 11: disconnected by user
Jul 15 08:34:16 Server1 sshd[1052]: pam_unix(sshd:session): session closed for user me
Jul 15 09:17:02 Server1 CRON[1129]: pam_unix(cron:session): session opened for user root by (uid=0)
Jul 15 09:17:02 Server1 CRON[1129]: pam_unix(cron:session): session closed for user root

now thats me at 8,33 from my 3g dongle, then I logged out and shutdown the xp machine that has the esxi console installed. Anyone got any ideas what the cron job is at 9.17? Thats the last entry before I switched it back on at 15.17.

Could that of shut down the machine? Does it look dodgy to you lot?

thanks all

---

### Post by CharlesA on 2010-07-15
I've got a bunch of those in my auth.log. It's just the system running some cronjob.

```
charles@thor:~$ tail /var/log/auth.log
Jul 15 07:14:04 thor smbd[21982]: pam_unix(samba:session): session opened for user htpc by (uid=0)
Jul 15 07:14:56 thor smbd[21982]: pam_unix(samba:session): session closed for user htpc
Jul 15 07:17:01 thor CRON[21987]: pam_unix(cron:session): session opened for user root by (uid=0)
Jul 15 07:17:01 thor CRON[21987]: pam_unix(cron:session): session closed for user root
Jul 15 08:00:01 thor CRON[22000]: pam_unix(cron:session): session opened for user root by (uid=0)
Jul 15 08:00:07 thor CRON[22000]: pam_unix(cron:session): session closed for user root
Jul 15 08:15:56 thor sshd[22008]: Accepted publickey for charles from 192.168.1.11 port 57945 ssh2
Jul 15 08:15:56 thor sshd[22008]: pam_unix(sshd:session): session opened for user charles by (uid=0)
Jul 15 08:17:01 thor CRON[22243]: pam_unix(cron:session): session opened for user root by (uid=0)
Jul 15 08:17:01 thor CRON[22243]: pam_unix(cron:session): session closed for user root

```

Haven't seen any problems. As for why the machine shutdown, did the system log say anything?

---

### Post by bodhi.zazen on 2010-07-15
Always nice to see people familiarizing themselves with the logs. It is essential to have at least a passing familiarity of what is "normal" if you ever want to use the logs for debugging something or tracking security issues.

Everything looks normal in what you have posted.

---

### Post by mr-woof on 2010-07-15
thanks for the feedback guys, I also thought the logs looked normal bar the root cronjob. I don't think I looked in the system logs, I'll have a look in a little bit.

I'm wondering if it's something to do with ESXi server itself, shutting down a virtual machine when there is no active for 30mins to an hour?

I'll have a look in the system logs and post back :)

---

### Post by mr-woof on 2010-07-15
This is from syslog:

Jul 15 08:27:16 Server1 kernel: [    8.596235] ip_tables: (C) 2000-2006 Netfilter Core Team
Jul 15 08:27:11 Server1 ntpdate[662]: step time server 91.189.94.4 offset -6.610476 sec
Jul 15 08:27:12 Server1 kernel: [   11.705307] type=1505 audit(1279178832.411:6): operation="profile_replace" pid=702 name=/$
Jul 15 08:27:12 Server1 kernel: [   11.716957] type=1505 audit(1279178832.423:7): operation="profile_replace" pid=702 name=/$
Jul 15 08:27:12 Server1 kernel: [   11.720122] type=1505 audit(1279178832.423:8): operation="profile_replace" pid=702 name=/$
Jul 15 08:27:13 Server1 kernel: [   11.772863] type=1505 audit(1279178832.479:9): operation="profile_replace" pid=703 name=/$
Jul 15 08:27:16 Server1 init: apport pre-start process (776) terminated with status 1
Jul 15 08:27:16 Server1 cron[780]: (CRON) INFO (pidfile fd = 3)
Jul 15 08:27:16 Server1 cron[793]: (CRON) STARTUP (fork ok)
Jul 15 08:27:16 Server1 cron[793]: (CRON) INFO (Running @reboot jobs)
Jul 15 08:27:16 Server1 init: apport post-stop process (791) terminated with status 1
Jul 15 08:27:20 Server1 kernel: [   19.624566] eth0: no IPv6 routers present
Jul 15 08:33:36 Server1 init: tty1 main process ended, respawning
Jul 15 09:17:02 Server1 CRON[1131]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jul 15 15:11:01 Server1 kernel: imklog 4.2.0, log source = /var/run/rsyslog/kmsg started.

Anything?

---

### Post by spynappels on 2010-07-15
Have you set the VM up to restart after a powercut? I've been caught out before when there has been a powercut, and BIOS has brought the ESXi host back up, but the individual VMs did not come back up because I had not set them to automatically reboot after a power outage.

---

### Post by mr-woof on 2010-07-15
Hmm i'm not sure to be honest on that, I'll need to turn it back on and have a look. Do we think it's probably a crash then?

---

