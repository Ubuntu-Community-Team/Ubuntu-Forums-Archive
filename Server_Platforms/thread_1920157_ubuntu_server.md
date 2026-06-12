---
title: "ubuntu server"
date: 2012-02-04
forum: Server Platforms
---

### Post by hdanap on 2012-02-04
> **dchen said:**
> Hi all,

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

Hi

I just wanted to ask the command to start gui from the command line.

I installed ubuntu desktop with command 

sudo apt-get install ubuntu-desktop

after the long wait, now i just need the command to start the x window via command line

This an ubuntu server and I know I  should not be using x window on a server but I just want to
also my server is with amazon ec2 

I Tried using /etc/init.d/

but could not locate the ubuntu desktop in the /etc/init.d file

pls assist

thanks

---

### Post by hdanap on 2012-02-04
Hi All,

I just wanted to ask the command to start gui from the command line.

I installed Ubuntu desktop with command 

sudo apt-get install Ubuntu-desktop

after the long wait, now i just need the command to start the x window via command line

This an Ubuntu server and I know I  should not be using x window on a server but I just want to
also my server is with amazon ec2 

I Tried using /etc/init.d/

but could not locate the Ubuntu desktop in the /etc/init.d file

pls assist

thanks

---

### Post by cryptotheslow on 2012-02-04
I ~think~ you would use:

```
startx
```

---

### Post by volkswagner on 2012-02-04
Login then run:

```
startx
```

---

### Post by coffeecat on 2012-02-04
@hdanap, I've moved your post (+ the reply) from the other thread you joined into your own one. Your two posts are identical. Please do not cross post. This dilutes community effort.

---

### Post by hdanap on 2012-02-04
> **coffeecat said:**
> @hdanap, I've moved your post (+ the reply) from the other thread you joined into your own one. Your two posts are identical. Please do not cross post. This dilutes community effort.

Please accept my apologies for over posting.

---

### Post by hdanap on 2012-02-04
> **volkswagner said:**
> Login then run:

```
startx
```

Hey thanx for the assistance but the startx command did not work, 

so i played around with a few commands and kept getting these errors.

```
 
ubuntu@ip-:~$ /etc/init.d/gdm start
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service gdm start

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the start(8) utility, e.g. start gdm
start: Rejected send message, 1 matched rules; type="method_call", sender=":1.25" (uid=1000 pid=10490 comm="start gdm ") interface="com.ubuntu.Upstart0_6.Job" member="Start" error name="(unset)" requested_reply="0" destination="com.ubuntu.Upstart" (uid=0 pid=1 comm="/sbin/init")


ubuntu@ip-:~$ /etc/init.d/gdm start
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service gdm start

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the start(8) utility, e.g. start gdm
start: Rejected send message, 1 matched rules; type="method_call", sender=":1.27" (uid=1000 pid=10495 comm="start gdm ") interface="com.ubuntu.Upstart0_6.Job" member="Start" error name="(unset)" requested_reply="0" destination="com.ubuntu.Upstart" (uid=0 pid=1 comm="/sbin/init")

ubuntu@ip-:~$ start gdm
start: Rejected send message, 1 matched rules; type="method_call", sender=":1.28" (uid=1000 pid=10496 comm="start gdm ") interface="com.ubuntu.Upstart0_6.Job" member="Start" error name="(unset)" requested_reply="0" destination="com.ubuntu.Upstart" (uid=0 pid=1 comm="/sbin/init")

ubuntu@ip:~$ service gdm start
start: Rejected send message, 1 matched rules; type="method_call", sender=":1.29" (uid=1000 pid=10497 comm="start gdm ") interface="com.ubuntu.Upstart0_6.Job" member="Start" error name="(unset)" requested_reply="0" destination="com.ubuntu.Upstart" (uid=0 pid=1 comm="/sbin/init")



```Pls assist.

---

### Post by volkswagner on 2012-02-04
Sounds like you don't have permission or you don't have all the necessary packages.

You should not need to use sudo to startx but try to see if it works.

```
sudo startx
```

If that starts X you may need to add yourself to some groups.

While logged in as yourself run:

```
groups
```

make sure you are a member of the video group.

You may need to be root to start GDM, but make sure it is installed.

```
sudo service gdm start
```


```
ls /etc/init.d
```

---

