---
title: "Unable to telnet to Qmail even after starting it"
date: 2008-05-15
forum: Server Platforms
---

### Post by torelativity on 2008-05-15
I have installed Qmail 1.06 on Ubuntu Gutsy. I have installed qmailctl to start qmail.
When I used to type,
#qmailctl start
, I used to get the following message
Starting Qmail
qmail-send supervise not running
qmail-smtpd supervise not running

I found the solution to it, that I need to enter the following before using qmailctl to start qmail.
#svscanboot &
Now, I do not get the error message.
However, when I try to telnet 127.0.0.1, port 25, it says unable to connect to host:Connection refused.
Also, the following gives me no output:
netstat -a | grep smtp

What is going wrong? Please help me out.

---

### Post by torelativity on 2008-05-15
#ps -ef |grep qmail
On doing the above, I get the following message:

root      6872  7831  0 16:10 pts/0    00:00:00 grep qmail
root      7859  7856  0 14:39 pts/0    00:00:00 readproctitle service errors: ...nnot open `/var/qmail/control/me' for reading: No such file or directory?head: cannot open `/var/qmail/control/me' for reading: No such file or directory?head: cannot open `/var/qmail/control/me' for reading: No such file or directory?head: cannot open `/var/qmail/control/me' for reading: No such file or directory?head: cannot open `/var/qmail/control/me' for reading: No such file or directory?
root      7889  7886  0 14:39 pts/0    00:00:00 readproctitle service errors: ... temporary failure?supervise: fatal: unable to acquire log/supervise/lock: temporary failure?supervise: fatal: unable to acquire log/supervise/lock: temporary failure?supervise: fatal: unable to acquire qmail-smtpd/supervise/lock: temporary failure?supervise: fatal: unable to acquire log/supervise/lock: temporary failure?supervise: fatal: unable to acquire log/supervise/lock: temporary failure?
root      7892  7888  0 14:39 pts/0    00:00:00 supervise qmail-send
root      7899  7858  0 14:39 pts/0    00:00:00 supervise qmail-smtpd
qmails   18702  7892  0 15:11 pts/0    00:00:00 qmail-send
qmaill   18705  7900  0 15:11 pts/0    00:00:00 /usr/local/bin/multilog t /var/log/qmail/smtpd
qmaill   18708  7906  0 15:11 pts/0    00:00:00 /usr/local/bin/multilog t /var/log/qmail
root     18711 18702  0 15:11 pts/0    00:00:00 qmail-lspawn ./Mailbox
qmailr   18712 18702  0 15:11 pts/0    00:00:00 qmail-rspawn
qmailq   18713 18702  0 15:11 pts/0    00:00:00 qmail-clean

---

### Post by juan@forum on 2008-05-15
who knows where did you get that version of qmail 


taken from DJB's page ->
The latest published qmail package is qmail-1.03.tar.gz


are you using daemontools?

if so, it is not running probably

check -> 
ps awx | grep readproc
ps awx | grep svscanboot

you need to find out how to manage daemontools at boot time with upstart

---

### Post by juan@forum on 2008-05-15
it seems you have some kind of permissions problem


check your run scripts (both service and log service) and what they are trying to do

---

