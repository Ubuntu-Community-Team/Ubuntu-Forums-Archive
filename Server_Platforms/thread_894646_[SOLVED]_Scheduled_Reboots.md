---
title: "[SOLVED] Scheduled Reboots?"
date: 2008-08-19
forum: Server Platforms
---

### Post by Ximbiot on 2008-08-19
I have two Hardy Heron (8.04LTS) Server installs, one of them almost clean as of last week with little other than the minimum install and Subversion on it, and both reboot almost every morning at 7:30am EST.  I have been digging through cron config files and logs to figure out why but I haven't been able to track the source of the problem down.

Does anyone know why this might be happening?  It is really annoying as it keeps interrupting a scheduled backup over the network of a large drive.  As near as I can tell, it has been going on since I installed the machines, but I didn't notice until I tried to set up the backups.

It happens almost every day, though it appears to skip some days unpredictably.  The missing reboot on the 11th below may have had to do with a power outage, but I verified in the syslogs that both machines were working this weekend before a reboot yesterday (and the long-lived backup process made it through the weekend leaving files timestamped through 7:28am Monday), and both skipped this morning:

older$ last |grep 07:30
reboot   system boot  2.6.24-19-server Mon Aug 18 07:30 - 13:16 (1+05:46)
reboot   system boot  2.6.24-19-server Fri Aug 15 07:30 - 13:16 (4+05:46)
reboot   system boot  2.6.24-19-server Thu Aug 14 07:30 - 13:16 (5+05:46)
reboot   system boot  2.6.24-19-server Wed Aug 13 07:30 - 13:16 (6+05:46)
reboot   system boot  2.6.24-19-server Tue Aug 12 07:30 - 13:16 (7+05:46)
reboot   system boot  2.6.24-19-server Sun Aug 10 07:30 - 13:16 (9+05:46)
reboot   system boot  2.6.24-19-server Thu Aug  7 07:30 - 13:16 (12+05:46)
reboot   system boot  2.6.24-19-server Wed Aug  6 07:30 - 13:16 (13+05:46)
reboot   system boot  2.6.24-19-server Tue Aug  5 07:30 - 13:16 (14+05:46)
reboot   system boot  2.6.24-19-server Mon Aug  4 07:30 - 13:16 (15+05:46)
reboot   system boot  2.6.24-19-server Sun Aug  3 07:30 - 13:16 (16+05:46)
reboot   system boot  2.6.24-19-server Sat Aug  2 07:30 - 13:16 (17+05:46)

fresh$ last |grep 07:30
reboot   system boot  2.6.24-19-server Mon Aug 18 07:30 - 13:21 (1+05:51)
reboot   system boot  2.6.24-19-server Fri Aug 15 07:30 - 13:21 (4+05:51)


:confused:

---

### Post by MJN on 2008-08-19
Post the syslog for the few moments before a reboot and see if it gives any clues - you might just have missed them.

(I like the wtf tag by the way!)

Mathew

---

### Post by Ximbiot on 2008-08-19
Thanks!  Here are the log lines you requested, starting with the cron.daily syslog restart through the latest reboots.

The older server is a mail server and thus the syslog is extremely messy with blocked connection attempts, but if I remove references to spamd and postfix, this is what is left:

lois$ egrep -v 'spamd|postfix' syslog.0 |head -10
Aug 18 07:11:49 lois syslogd 1.5.0#1ubuntu1: restart.
Aug 18 07:17:01 lois /USR/SBIN/CRON[29621]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug 18 07:30:18 lois syslogd 1.5.0#1ubuntu1: restart.
Aug 18 07:30:18 lois kernel: Inspecting /boot/System.map-2.6.24-19-server
Aug 18 07:30:18 lois kernel: Loaded 28743 symbols from /boot/System.map-2.6.24-19-server.
Aug 18 07:30:18 lois kernel: Symbols match kernel version 2.6.24.
Aug 18 07:30:18 lois kernel: Loaded 17960 symbols from 74 modules.
Aug 18 07:30:18 lois kernel: [    0.000000] Initializing cgroup subsys cpuset
Aug 18 07:30:18 lois kernel: [    0.000000] Initializing cgroup subsys cpu
Aug 18 07:30:18 lois kernel: [    0.000000] Linux version 2.6.24-19-server (buildd@terranova) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Sat Jul 12 00:40:01 UTC 2008 (Ubuntu 2.6.24-19.36-server)


The fresh install is my router, dhcp server, and name server.  It is also noisy because I do a lot of packet logging.  Filtering these out yields about the same thing:

shazam$ egrep -v 'IN=.*OUT=|dhcpd|named' syslog.0 |head -10
Aug 18 06:41:12 shazam syslogd 1.5.0#1ubuntu1: restart.
Aug 18 07:17:01 shazam /USR/SBIN/CRON[5908]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug 18 07:30:07 shazam syslogd 1.5.0#1ubuntu1: restart.
Aug 18 07:30:07 shazam kernel: Inspecting /boot/System.map-2.6.24-19-server
Aug 18 07:30:07 shazam kernel: Loaded 28743 symbols from /boot/System.map-2.6.24-19-server.
Aug 18 07:30:07 shazam kernel: Symbols match kernel version 2.6.24.
Aug 18 07:30:07 shazam kernel: Loaded 16049 symbols from 73 modules.
Aug 18 07:30:07 shazam kernel: [    0.000000] Initializing cgroup subsys cpuset
Aug 18 07:30:07 shazam kernel: [    0.000000] Initializing cgroup subsys cpu
Aug 18 07:30:07 shazam kernel: [    0.000000] Linux version 2.6.24-19-server (buildd@terranova) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Sat Jul 12 00:40:01 UTC 2008 (Ubuntu 2.6.24-19.36-server)

---

### Post by MJN on 2008-08-19
When are you daily cron scheduled to start?

What is curious is that both servers exhibit the same behaviour.... or do they share the same config (in terms of one being a copy of the other)?

Mathew

---

### Post by Ximbiot on 2008-08-19
> **MJN said:**
> When are you daily cron scheduled to start?

lois$ cat /etc/crontab
...
# m h dom mon dow user  command
17 *    * * *   root    cd / && run-parts --report /etc/cron.hourly
25 6    * * *   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
47 6    * * 7   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )
52 6    1 * *   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )
#


> **MJN said:**
> What is curious is that both servers exhibit the same behaviour.... or do they share the same config (in terms of one being a copy of the other)?

They do not share a configuration, other than that they were both installed from the same Ubuntu 8.04LTS DVD and updated from the same Ubuntu Apt servers (ubuntu.com's).

Both have an empty /etc/cron.d and the common /etc/cron.{hourly,daily,monthly} files are: 

shazam$ ls /etc/cron.{hourly,daily,monthly}
/etc/cron.daily:
apt  aptitude  bsdmainutils  logrotate  man-db  mlocate  standard  sysklogd

/etc/cron.hourly:

/etc/cron.monthly:
standard

---

### Post by MJN on 2008-08-19
I'm afraid I'm stumped...

I must say I thought it was going to be something simple that you'd overlooked but it appears to be too weird for words...

Maybe someone else can come in and continue my stabbing in the dark... ;)

Mathew

---

### Post by Cheesehead on 2008-08-19
What processes are running before the reboot? (please post, if you can)
Anything of interest in their config files?
Which were started manually?

Is this the ONLY reboot (intended or otherwise) that they do in 24 hours? - One of the logs showed another reboot ~30 min earlier.

Have someone, perhaps, saved a strange configuration change on a previous logout? Is your environment different in any other way?

---

### Post by Ximbiot on 2008-08-19
> **Cheesehead said:**
> What processes are running before the reboot? (please post, if you can)
Anything of interest in their config files?
Which were started manually?

I don't really know and I'll have to get here before 7:30 and watch `top' closely to figure it out, unless you have a suggestion for how to log all running processes from 7:20 to 7:40 or something like that.


> **Cheesehead said:**
> Is this the ONLY reboot (intended or otherwise) that they do in 24 hours? - One of the logs showed another reboot ~30 min earlier.

Actually, the line I think you are referring to is the cron.daily run of logrotate, which is only restarting the syslog:

> Aug 18 06:41:12 shazam syslogd 1.5.0#1ubuntu1: restart.

There *were* some other reboots on the mail server, but mostly they happened during times I was likely in the office upgrading kernels or the like.  There are three, however, that happened at an odd time when no one should have been in the office and I cannot explain them yet, but hadn't mentioned them for fear of muddying the waters:

> reboot   system boot  2.6.24-19-server Sun Aug 10 23:07 - 16:03 (8+16:55)
reboot   system boot  2.6.24-19-server Sun Aug 10 22:47 - 16:03 (8+17:16)
reboot   system boot  2.6.24-19-server Sun Aug 10 19:39 - 16:03 (8+20:23)


> **Cheesehead said:**
> Have someone, perhaps, saved a strange configuration change on a previous logout? Is your environment different in any other way?

On *both machines*?  Unlikely.  I am the only one who can log into either of these machines and I certainly didn't do make such a change on purpose.

The mail server may have been in service long enough to have become slightly messy, but on the router, in particular, I started with a minimal Ubuntu 8.04LTS Server install, added Subversion, Bind, & DHCPD, then added some of my own configuration for Bind, DHCPD, the interfaces, & iptables.  This machine doesn't do anything except hand out IPs and route packets and I just installed it last Thursday, so its configuration hasn't had much time to diverge from my memory of it.

---

### Post by MJN on 2008-08-19
> **Ximbiot said:**
> I don't really know and I'll have to get here before 7:30 and watch `top' closely to figure it out

I don't suppose the cleaner does their rounds at 7:20am and plugs the vacuum cleaner in...?! ;) (sorry to get so technical)

Mathew

---

### Post by Ximbiot on 2008-08-19
> **MJN said:**
> I don't suppose the cleaner does their rounds at 7:20am and plugs the vacuum cleaner in...?! ;) (sorry to get so technical)

:lolflag: Similar thoughts had crossed my mind, but when I've encountered cleaning staff here, it has been in the evenings.  I won't know that for sure until I come in and stare at the machine and `top' at 7:30am, but I doubt this would have quite such exact timing if it was being caused by regular human activity.

---

### Post by cdenley on 2008-08-19
It's got to be something in cron.
```

sudo cat /var/spool/cron/crontabs/*>cron.txt
sudo cat /etc/cron.*/*>>cron.txt
sudo cat /etc/crontab>>cron.txt

```

---

### Post by Ximbiot on 2008-08-19
> **cdenley said:**
> It's got to be something in cron.
```

sudo cat /var/spool/cron/crontabs/*>cron.txt
sudo cat /etc/cron.*/*>>cron.txt
sudo cat /etc/crontab>>cron.txt

```

/var/spool/cron/crontabs and /etc/cron.d are empty on the router, and the other /etc/cron.* have only the files I listed earlier, but they are all normal scripts, are all installed by an Ubuntu package manager, are all run only via the entries in /etc/crontab (which I also listed earlier) and none of the lines in /etc/crontab has an entry for 7:30.  Again, on both machines:

```
$ cat /etc/crontab
...
# m h dom mon dow user  command
17 *    * * *   root    cd / && run-parts --report /etc/cron.hourly
25 6    * * *   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )
47 6    * * 7   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.weekly )
52 6    1 * *   root    test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.monthly )
#

```

---

### Post by Ximbiot on 2008-08-20
Okay, this is getting ridiculous.  I came in at 7:20 this morning, started up a bunch of logs and didn't get a reboot.  Killed the logs and stopped watching top at about 7:35 and both machines rebooted at 7:37.

AAAAAAAAARRRRRRRRRRRRRRRRRGGGGGGGGGGGGGGGGHHHHHHHHHHHHHHHHH!

](*,)

---

### Post by MJN on 2008-08-20
(Cleaner late in?)
 
I think what you've observed could well be a pointer in the right direction.... Next time stick around a little longer (at least past 7:37) just to see if the reboots occur once more after you leaving the terminal.
 
If this was just one machine it might be like looking for a needle in a haystick.... but the fact two machines are behaving identically is obviously of massive significance so don't give up looking for that common link!
 
Mathew

---

### Post by Ximbiot on 2008-08-20
> **MJN said:**
> (Cleaner late in?)

Huh?

> **MJN said:**
> I think what you've observed could well be a pointer in the right direction.... Next time stick around a little longer (at least past 7:37) just to see if the reboots occur once more after you leaving the terminal.
 
If this was just one machine it might be like looking for a needle in a haystick.... but the fact two machines are behaving identically is obviously of massive significance so don't give up looking for that common link!

Yes, I planned to keep looking.  Don't have much choice if I want my backups to run.  :)

Just for kicks, I'm adding one of my last logs of the output of `top'.  Looks like it's just kernel processes to me and nothing is eating up much CPU or memory, which blows my (previously unstated) theory about my logging in eating up CPU or IO and slowing the processes causing the reboots down (the fact that the timing on two machines stayed in sync is also points against that theory):

```
Tasks: 103 total,   1 running, 102 sleeping,   0 stopped,   0 zombie
Cpu(s):  0.0%us,  0.1%sy,  0.0%ni, 99.9%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   3626848k total,  1279032k used,  2347816k free,   678344k buffers
Swap:  3004112k total,        0k used,  3004112k free,   266476k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
    1 root      20   0  1812  840  612 S    0  0.0   0:01.53 init
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.01 migration/0
    4 root      15  -5     0    0    0 S    0  0.0   0:02.90 ksoftirqd/0
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.01 migration/1
    7 root      15  -5     0    0    0 S    0  0.0   0:00.46 ksoftirqd/1
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1
    9 root      15  -5     0    0    0 S    0  0.0   0:00.66 events/0
   10 root      15  -5     0    0    0 S    0  0.0   0:00.50 events/1
   11 root      15  -5     0    0    0 S    0  0.0   0:00.01 khelper
   46 root      15  -5     0    0    0 S    0  0.0   0:00.16 kblockd/0

```

---

### Post by wirepuller134 on 2008-08-21
This is a shot in the dark, but has caused us a lot of grief.  we had a problem with ups alarms going off at odd times.  After checking everything on our power distribution in our server room we found nothing wrong.  so I hooked up a recording meter to our incoming power, what we found was power dips and pf going way down at 6 am and between 9 and 11 pm.  These times coincided with the alarms.  This was solved by contacting the power company, whom found a faulty capacitor bank at a sub station.  The times coincided with two processing plants starting up production. 
    Since yours is local to just these two units I would agree someone is plugging something in, or something has been added to the circuit that is causing a voltage drop when turning on (coffee pot or heater example).  If your company has a maintenance department I would get them to do some power recording or install a power conditioner (constant voltage transformer) or a ups.

---

### Post by beniwtv on 2008-08-21
I agree with wirepuller, check your UPS and power sources...

We've had 3 machines routinely rebooting at 1:24 PM every tuesday. And EXACTLY at 1:24, and every time on tuesday! I replaced the UPS unit and everything has been smooth since.

Go figure!

Cheers,

---

### Post by Ximbiot on 2008-08-22
I think I've solved the problem.  Both rebooting machines were plugged into the same UPS.  I bought a new UPS and plugged only the mail server into it.  Lo and behold, the router rebooted at exactly 7:30am again this morning and the mail server stayed up even though they had previously been rebooting in exact sync.

So my final diagnosis is a bad UPS (~8 years old) and some sort of regular power spike or dip in the building.  The regular power event could be a power plant coming online, the factory down the street turning something on, or maybe the dentist downstairs turning on her X-ray machine in the morning.

I may still try and get some meters in here so I can report the issue to the power company and they can perhaps do something about it if it isn't the dentist, but the new UPS appears to prevent the reboots.

Thanks for all the help!

:guitar:

---

### Post by wirepuller134 on 2008-08-22
Glad to hear you got it worked out, it can be frustrating at times, trying to figure out if a problem is software or hardware related or a combination of both.  we replace the batteries in ours every 2 years, cheap insurance compared to the damage that could be done by them not working.

---

