---
title: "Correct server call?"
date: 2014-02-13
forum: Server Platforms
---

### Post by Heb_Boozad on 2014-02-13
So a user on my machine would have to run to configure the date on the machine: ```
rdate X.X.X.X
```

How could I check (with bash) if the server called with rdate command was the right server (X.X.X.X), if the time on the machine was synced with the right server.


Thanks.

---

### Post by Dave_L on 2014-02-13
Why not set up a task to do the time synchronization automatically?

Actually, Ubuntu, by default, sets up ntpdate to do that.

---

### Post by Heb_Boozad on 2014-02-13
The problem is not in time sync. rdate is being used for that, and I need to verify if it's being synced with the correct server.

---

### Post by Heb_Boozad on 2014-02-13
bump, please

---

### Post by Bucky Ball on 2014-02-13
*Thread moved to **Server Platforms**.*

It is forum etiquette to wait 24 hours before bumping. Please adhere to this. Thanks.

---

### Post by Kirboosy on 2014-02-14
Welcome to the forums Heb_Boozad :D

[ntpdate]("http://linux.die.net/man/8/ntpdate") supercedes [rdate]("http://linux.die.net/man/1/rdate"). I'm not sure how you would list out very verbose server information. The rdate utility is very basic and doesn't have a lot of functionality. Perhaps this would get you in the right direction?

```
rdate -p -l <IPADDRESS>
```

I would highly recommend using ntpdate as it is more commonly used and has a more robust feature set.

[Time Protocol]("http://en.wikipedia.org/wiki/TIME_protocol")

Hope that helps!
~Caboose

---

### Post by tgalati4 on 2014-02-14
With *ntpd*(part of the ntp metapackage), you can specify multiple time servers.  So your time base will be the average of those servers.  If there is a large discrepancy between times, you will get a system log entry.  You can run ntp on each client's machine.  It is a low-overhead service.

I don't understand the OP's question.  The user would normally not have to run rdate because ntpd sets the time automatically and keeps it to within microseconds of a national time standard with corrections every hour.

*ntpdate*, which is installed by default in Linux systems will set the correct time once on boot. This may be good enough, but if you don't reboot for several weeks, then you can experience drift.  I'm not sure if ntpdate is called after resume-from-suspend to check for the correct time.

---

### Post by Heb_Boozad on 2014-02-14
I'm aware that ntpd is superior to rdate. But my assignment is to check if the machine used the right server with rdate. So if I know that rdate was used, and know the correct server (e.g. X.X.X.X), how could I check if the rdate command used had the right server (X.X.X.X) used as argument.

---

### Post by Kirboosy on 2014-02-14
Check your cron jobs or wherever you have setup the rdate command to run. If it has the right IP then everything should be working just fine.

---

### Post by tgalati4 on 2014-02-15
This sounds like a homework assignment where the issue is not the time but rather write a script to check that a correct parameter was passed. With [rdate]("http://manpages.ubuntu.com/manpages/precise/man3/rtime.3.html"), I presume that a time correction is logged somewhere (/var/log/rdate or syslog).  So after the command is run, have the script grep the log file and pull out the time server IP address.  Then compare that IP address to a grep of the user's history file to compare IP addresses to see if they are the same.  

Again, I'm not sure what the lesson here is, but I would be filling out my drop card.

```
grep time /var/log/syslog
```

This gives me:

Feb 14 15:42:27 Mint14-Extensa ntpdate[9186]: adjust time server **67.212.118.201** offset -0.050166 sec

---

### Post by Heb_Boozad on 2014-02-15
> **tgalati4 said:**
> This sounds like a homework assignment where the issue is not the time but rather write a script to check that a correct parameter was passed. With [rdate]("http://manpages.ubuntu.com/manpages/precise/man3/rtime.3.html"), I presume that a time correction is logged somewhere (/var/log/rdate or syslog).  So after the command is run, have the script grep the log file and pull out the time server IP address.  Then compare that IP address to a grep of the user's history file to compare IP addresses to see if they are the same.  

Again, I'm not sure what the lesson here is, but I would be filling out my drop card.

```
grep time /var/log/syslog
```

This gives me:

Feb 14 15:42:27 Mint14-Extensa ntpdate[9186]: adjust time server **67.212.118.201** offset -0.050166 sec


This is what I'm trying to achive, yes. But I already tried to grep /var/log/syslog but there is no log of this command in syslog. Maybe in any other log file?

---

### Post by tgalati4 on 2014-02-15
I gave the incorrect manual page for rdate.  This should be correct:  [http://manpages.ubuntu.com/manpages/precise/en/man8/rdate.8.html](http://manpages.ubuntu.com/manpages/precise/en/man8/rdate.8.html)

According to the manual page:

> FILES
     /var/log/wtmp  record of date resets and time changes

---

### Post by Heb_Boozad on 2014-02-16
> **tgalati4 said:**
> I gave the incorrect manual page for rdate.  This should be correct:  [http://manpages.ubuntu.com/manpages/precise/en/man8/rdate.8.html](http://manpages.ubuntu.com/manpages/precise/en/man8/rdate.8.html)

According to the manual page:


I'm almost certain that you can't see which server was used in [COLOR=#000000]*/var/log/wtmp. You have the change log but no server IP.*[/COLOR]

---

### Post by tgalati4 on 2014-02-16
You are right.  The correct answer for your homework is not to use *rdate* but use *ntp*.

---

