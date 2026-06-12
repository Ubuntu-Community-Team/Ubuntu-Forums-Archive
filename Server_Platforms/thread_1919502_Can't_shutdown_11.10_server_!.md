---
title: "Can't shutdown 11.10 server !"
date: 2012-02-03
forum: Server Platforms
---

### Post by dchen on 2012-02-03
Hi all,

Logged as a sysadmin acct, from the Unity GUI or from the command line, I can RESTART the server, but CAN'T Shutdown ! please help!

Here are last messages on the screen, but it repeatedly displayed the similar messages, just don't shutdown UNTIL I press the reset or the power button. 

Stopping Webmin server in /usr/share/webmin
 * Stopping the Winbind daemon winbind
 * Stopping PostgreSQL 8.4 database server
 * Stopping PostgreSQL 9.1 database server
 * Stopping ClamAV virus database updater freshclam
Stopping Open DKIM: opendkim
Stopping amavisd: amavisd-new
Stopping Spamassassin Mail Filter Daemon: spamd
 * Will now halt
[388.447452] INFO: rcu_sched_state detected stall on CPU 0 (t=15000 jiffies)
[480.896743] INFO: task fsnotify_mark:53 blocked for more than 120 seconds.
[480.916326] INFO: task dhclient:1076 blocked for more than 120 seconds.
[480.923575] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[480.938064] INFO: task pulseaudio:2120 blocked for more than 120 seconds.
[480.945738] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[601.076794] INFO: task udisk-daemon:2157 blocked for more than 120 seconds
...
[748.524010] INFO: rcu_sched_state detected stall on CPU 0 (t=105061 jiffies)
...

---

### Post by codmate on 2012-02-03
What command are you using to perform the system shutdown?

---

### Post by arrrghhh on 2012-02-03
> **codmate said:**
> What command are you using to perform the system shutdown?

This ^^.

Also, GUI on a server...?  Why not just run Ubuntu Desktop?

---

### Post by drdos2006 on 2012-02-03
I found I had to load the drivers for the video card for 11.10 server to shut down properly.

regards

---

### Post by JRV on 2012-02-03
> **codmate said:**
> What command are you using to perform the system shutdown?

Try```
sudo shutdown -h now
```

---

### Post by dchen on 2012-02-03
I tried the command below, it worked perhaps one or two times but got the same symptom most the time!

sudo shutdown -h now

---

### Post by collisionystm on 2012-02-03
sudo shutdown -P 0

^ the command I have always used

---

### Post by arrrghhh on 2012-02-03
> **collisionystm said:**
> sudo shutdown -P 0

^ the command I have always used

-h is pretty much the same... -h gives the system the choice to either halt or power off after being brought down.  -P just powers down the system.  -H just halts.  For the difference between halt and power off, [read here](http://ubuntuforums.org/showpost.php?p=10259392&postcount=12).

Also, to anyone having shutdown problems (especially the OP!) see [this post](http://ubuntuforums.org/showpost.php?p=6176637&postcount=28).

---

### Post by petehild on 2012-02-11
As I posted in another Thread, I have the same problem and for me it started with the update to kernel 3.0.0-15. Kernel  3.0.0-14 works like a charm. 3.0.0-16 (from ubuntu-proposed) doesn't  work either. For now I'll stick with 3.0.0-14.

Greetings
Pete

---

### Post by petehild on 2012-02-16
I played around with Kernel 3.2.0 under oneiric, and shutdown works again with that kernel for me.
[http://www.upubuntu.com/2012/01/how-to-install-linux-kernel-32-under.html](http://www.upubuntu.com/2012/01/how-to-install-linux-kernel-32-under.html)

Pete

---

