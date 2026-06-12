---
title: "Reliability monitor for Linux"
date: 2009-11-11
forum: The Cafe
---

### Post by Nevon on 2009-11-11
Lately I've been toying with the idea of creating an application similar to the realiability monitor in Windows Vista and 7, only for Linux, obviously. 

[img]http://pcauthorities.com/images/vista-reliability-monitor.jpg[/img]

The idea is that it collects data on system updates, crashes, etc. and displays them on a timeline. By doing so, you could more easily find correlations between updates and stuff breaking, among other things. The application has a lot of other functions as well, but I think this would be a good start.

What I'm wondering is from where you would be able to collect this data in Linux. Can you use the same method with all (or at least most) distributions, or is it different for different distros? 

So far I have only been able to find /var/log/dmesg as a possible data source. Are there others? Also, if you know of anyone who has already done work on this - please let me know.

---

### Post by SunnyRabbiera on 2009-11-11
/var/log/dmesg is the only one I am aware of, but seriously I dont see the need of such a tool as I rarely get crashes/freeze ups personally.
Once in a while I do though, but its rare

---

### Post by Nevon on 2009-11-11
After doing some reading it seems that the most interesting one from my perspective must be /var/log/messages as that not only contains kernel messages, but other stuff as well. 

> **SunnyRabbiera said:**
> I dont see the need of such a tool as I rarely get crashes/freeze ups personally.
Once in a while I do though, but its rare
I beg to differ. Right now, in fact, Empathy is crashing over and over for me. In /var/log/messages I can see the following line:
```
Nov 11 10:43:03 loltop kernel: [ 6180.918835] empathy[4958]: segfault at 8 ip 00a2c79e sp bfbf70a8 error 4 in libfontconfig.so.1.3.0[a16000+2b000]
```

If I could see what update might have caused this, I could possibly roll back the changes and get it working again. The only thing I can do now is to file a bug and hope that I can get it working somehow.

---

### Post by Xbehave on 2009-11-11
rsyslog and associated tools will do this (there may be more tools for the older syslog-ng or syslog)

---

### Post by SunnyRabbiera on 2009-11-11
> **Nevon said:**
> 
I beg to differ. Right now, in fact, Empathy is crashing over and over for me. In /var/log/messages I can see the following line:
```
Nov 11 10:43:03 loltop kernel: [ 6180.918835] empathy[4958]: segfault at 8 ip 00a2c79e sp bfbf70a8 error 4 in libfontconfig.so.1.3.0[a16000+2b000]
```


I am not using Karmic though :D

---

### Post by insane_alien on 2009-11-11
it'd definitely be useful for developers if some data gathering can be collected from the masses(obviously with user consent) to provide an objective account of stability and where the most troublesome bugs are (rather than just who's the most vocal on the bug reports)

---

### Post by spupy on 2009-11-11
> **SunnyRabbiera said:**
> /var/log/dmesg is the only one I am aware of, but seriously I dont see the need of such a tool as I rarely get crashes/freeze ups personally.
Once in a while I do though, but its rare

"But it works for me!" Sure, we may get crashes rare, but such an utility really got my interest.

To OP: you can also scan /var/log/Xorg.0.log. It's even easy, as all warnings are preceded with (WW) and errors with (EE).

---

### Post by Dougie187 on 2009-11-11
everything is in /var/log the main system ones would be messages, dmesg, and syslog, however there are more.

You could even parse auth.log to find out when people are trying to gain access to your machine. 

Either way, it sounds like a decent idea. Could help with troubleshooting especially for new users who are not very familiar with the way things work.

I am unsure if the different distros have the same log format though, CentOS looks to have /var/log with logs messages and dmesg but not syslog or auth. This would be the same for RHEL and I would assume fedora too. So it looks like you  cant make one package for all distros.

---

### Post by Sam on 2009-11-11
There are also kernel oops logs in /var/crash

---

### Post by Xbehave on 2009-11-11
> **insane_alien said:**
> it'd definitely be useful for developers if some data gathering can be collected from the masses(obviously with user consent) to provide an objective account of stability and where the most troublesome bugs are (rather than just who's the most vocal on the bug reports)
I don't think that can be don without phones home, however there are several libraries which offer that functionality, kde even  tells users how to submit useful debugging info (although by default it's tied up to kde there must be similar libs that are not)

> **Dougie187 said:**
> everything is in /var/log the main system ones would be messages, dmesg, and syslog, however there are more.
from [here]("http://www.cyberciti.biz/faq/linux-log-files-location-and-how-do-i-view-logs-files/")
    * /var/log/message: General message and system related stuff
    * /var/log/auth.log: Authenication logs
    * /var/log/kern.log: Kernel logs
    * /var/log/cron.log: Crond logs (cron job)
    * /var/log/boot.log : System boot log
    * /var/log/secure: Authentication log
    * /var/log/utmp or /var/log/wtmp : Login records file

> I am unsure if the different distros have the same log format though, CentOS looks to have /var/log with logs messages and dmesg but not syslog or auth. This would be the same for RHEL and I would assume fedora too. So it looks like you  cant make one package for all distros.
on modern desktop rsyslog does the logging and this is controlled by [/etc/rsyslog.conf]("/etc/rsyslog.conf"). The tricky part is finding a nice GUI to display all the logged data

AFAIK dmesg is not controlled by this as dmesg takes logs straight from the kernel (Infact i belive that syslog,etc will read dmesg (along with other sources) and use it to populate the other files)

---

