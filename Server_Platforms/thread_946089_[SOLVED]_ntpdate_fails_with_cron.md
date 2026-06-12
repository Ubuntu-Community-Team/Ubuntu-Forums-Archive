---
title: "[SOLVED] ntpdate fails with cron"
date: 2008-10-13
forum: Server Platforms
---

### Post by dmizer on 2008-10-13
I am running an ubuntu cli web server in VMware. Unfortunately, the server time is always incorrect because of this more than annoying bug:
```
/dev/vmmon[30596]: host clock rate change request 8 -> 11
```
The "solution" posted here: [http://communities.vmware.com/message/820186](http://communities.vmware.com/message/820186) is to filter these messages out of the log. This is great, except when you consider that the guest time is also important.

In an effort to overcome this malfunction, I created a script and placed it in cron hourly so my server's clock would be checked and updated every hour.

Here is my /etc/cron.hourly script:
```
#!/bin/sh
ntpdate jp.pool.ntp.org ntp.ubuntu.com
```

I have tried all the solutions provided in this thread: [http://ubuntuforums.org/showthread.php?t=324842](http://ubuntuforums.org/showthread.php?t=324842)

The time is correctly updated if I manually run this command:
```
ntpdate jp.pool.ntp.org
```

However, when I edit files and make posts on my server, the date is still shown as Oct 8th. It's also still wrong after rebooting the server, and/or opening a new ssh session.

Interestingly here's the output when I run the enough:
```
$ date
Mon Oct 13 12:57:23 JST 2008
$ sudo /etc/cron.hourly/ntpdate
8 Oct 13:17:03 ntpdate[11299]: no servers can be used, exiting
```

Note: this DID work. It worked for about a week, and apparently stopped working around the 8th of October.

Here's some interesting and probably relevant dmesg output:
```
[3210581.337527] Clocksource tsc unstable (delta = 4689583361 ns)
[3210581.339302] Time: acpi_pm clocksource has been installed.
```

I'm stumped.

---

### Post by kevdog on 2008-10-13
I wish I had the answer for you as well:(

---

### Post by MJN on 2008-10-13
You say...
 
> **dmizer said:**
> The time is correctly updated if I manually run this command:
```
ntpdate jp.pool.ntp.org
```
 
but then...
 
> However, when I edit files and make posts on my server, the date is still shown as Oct 8th.Are you sure therefore that the time is getting updated?What do the logs say?
 
Have you tried with a different NTP source?
 
It may also be worth running a packet trace (e.g. using Ethereal etc) prior to running ntpdate just to see if the server name is being accepted (i.e. a DNS lookup is being performed, and a result obtained) and then whether it is attempting a connection to the server.
 
Mathew

---

### Post by dmizer on 2008-10-13
> **MJN said:**
> You say...
 

 
but then...
 
Are you sure therefore that the time is getting updated?What do the logs say?
 
Have you tried with a different NTP source?
 
It may also be worth running a packet trace (e.g. using Ethereal etc) prior to running ntpdate just to see if the server name is being accepted (i.e. a DNS lookup is being performed, and a result obtained) and then whether it is attempting a connection to the server.
 
Mathew
Actually, I think there may have been something more serious at fault. I haven't had time to look through the logs yet, but a short time after I noticed this problem, my ssh session became extremely sluggish, and simple commands like ifconfig and ping were not responding well. I tried to reboot the server but it froze up with kernel panic related to low memory.

After I bumped up the memory for the server, I've restarted it, and time seems to be updating as expected now. I'll let this go for a few days and see if something else happens, but I expect to be marking this thread as solved fairly soon.

---

### Post by dmizer on 2008-10-14
Marking this as solved. Here was my problem:

In an effort to solve a different problem, I bumped up the memory limit in php.ini to more than my available ram. The date problem was merely the first symptom I noticed. :oops:

After adjusting php.ini to something a bit more reasonable and increasing the available VM guest ram, I've since had no problmes with the date adjusting itself correctly in cron.hourly. 

):P

---

