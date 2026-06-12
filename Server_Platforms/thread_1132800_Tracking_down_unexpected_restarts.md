---
title: "Tracking down unexpected restarts"
date: 2009-04-22
forum: Server Platforms
---

### Post by Youresorock on 2009-04-22
I have an 8.04 Server ubuntu box running my department web and database server services.  I had an uptime of over 6months until recently when I'm getting a reboot at least once a day.  How can I track down if a program is initiating the reboots?  They are at suspiciously similar times each day.

rock@www:/var/log$ less syslog* | grep restart
Apr 22 07:47:18 www syslogd 1.5.0#1ubuntu1: restart.
Apr 21 07:59:01 www syslogd 1.5.0#1ubuntu1: restart.
Apr 21 07:59:04 www syslogd 1.5.0#1ubuntu1: restart.
Apr 20 07:43:20 www syslogd 1.5.0#1ubuntu1: restart.
Apr 20 11:09:06 www syslogd 1.5.0#1ubuntu1: restart.
Apr 19 07:50:16 www syslogd 1.5.0#1ubuntu1: restart.
Apr 18 08:03:59 www syslogd 1.5.0#1ubuntu1: restart.
Apr 17 07:48:06 www syslogd 1.5.0#1ubuntu1: restart.
Apr 16 07:35:35 www syslogd 1.5.0#1ubuntu1: restart.
Apr 15 07:48:56 www syslogd 1.5.0#1ubuntu1: restart.


All the reboots except for one are between 7:35 and 8:03am.  The 11 o'clock restart the server room admin confirmed was a power issue.  I'm having him check if the machine's UPS is functioning properly too.  I checked the logs on our windows machines in the same rack, and they haven't been rebooting.

---

### Post by daboroe on 2009-04-22
I saw something about this and can not remember where I saw it on the forum. I believe there is something on the forum about it. Its happening once a day and that is similar to the other problem Other than one thing I see now

> 
Apr 21 07:59:01 www syslogd 1.5.0#1ubuntu1: restart.
Apr 21 07:59:04 www syslogd 1.5.0#1ubuntu1: restart.


That day it happened twice.

I would think maybe a power issue. check the temperatures and make sure the system is not overheating.

---

### Post by Youresorock on 2009-04-22
Here is what I can find for temperatures:  Looks to be cool as a cucumber.

```
rock@www:~$ sudo smartctl -A /dev/sda | grep "Current Drive"
Current Drive Temperature:     35 C
```


```
rock@www:~$ sensors
coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +22.0°C  (crit = +85.0°C)                  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +24.0°C  (crit = +85.0°C)  
```

---

### Post by Youresorock on 2009-04-22
Ok, I'm a n00b apparently.

I was looking at when syslogd restarted.  Yes, it restarts every time you reboot, but it also restarts once daily to cycle through the log files.

I found a better why to check reboot history.

```
last | grep reboot

reboot   system boot  2.6.24-16-server Mon Apr 20 11:09 - 11:09 (2+00:00)  
```

So only that one time at 11:09 when there was a power problem was actually a reboot.  The 'last' log seems to go back to April 1st.

:guitar:

---

### Post by daboroe on 2009-04-22
> **Youresorock said:**
> Ok, I'm a n00b apparently.

I was looking at when syslogd restarted.  Yes, it restarts every time you reboot, but it also restarts once daily to cycle through the log files.

I found a better why to check reboot history.

```
last | grep reboot

reboot   system boot  2.6.24-16-server Mon Apr 20 11:09 - 11:09 (2+00:00)  
```

So only that one time at 11:09 when there was a power problem was actually a reboot.  The 'last' log seems to go back to April 1st.

:guitar:

good that you got it working.

---

