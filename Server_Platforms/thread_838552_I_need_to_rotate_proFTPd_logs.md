---
title: "I need to rotate proFTPd logs"
date: 2008-06-23
forum: Server Platforms
---

### Post by IbuildDW on 2008-06-23
The last requirement I need to complete before deploying a new FTP server is log rotation.  I have searched most of today to try to determine how to set this up with no luck.  As I understand I need to use FIFO? and parse that file somehow.  Does anyone have an example how this is setup?

---

### Post by RealPSL on 2008-06-23
How about this example directly from proftpd? I was a little surprised that Ubuntu does not seem to provide this as a part of the proftpd package.

[http://www.proftpd.org/localsite/Userguide/linked/x341.html]("http://www.proftpd.org/localsite/Userguide/linked/x341.html")

---

### Post by cariboo on 2008-06-24
Proftpd does rotate logs here is an example from my server:

```
-rw-r----- 1 root adm      0 2008-06-18 19:46 proftpd.log
-rw-r----- 1 root adm 179733 2008-06-07 23:12 proftpd.log.0
-rw-r----- 1 root adm    929 2008-05-13 22:11 proftpd.log.1.gz
-rw-r----- 1 root adm   2280 2008-04-13 22:45 proftpd.log.2.gz
-rw-r----- 1 root adm  73848 2008-03-12 12:55 proftpd.log.3.gz
-rw-r----- 1 root adm      0 2008-06-18 19:46 xferlog
-rw-r----- 1 root adm 234126 2008-06-05 15:18 xferlog.0
-rw-r----- 1 root adm   1062 2008-04-26 21:07 xferlog.1.gz
-rw-r----- 1 root adm   3029 2008-04-13 22:14 xferlog.2.gz
-rw-r----- 1 root adm 632686 2008-03-10 18:30 xferlog.3.gz
-rw-r----- 1 root adm      0 2008-06-18 19:46 xferreport
-rw-r----- 1 root adm      0 2008-05-13 20:14 xferreport.0
-rw-r----- 1 root adm     33 2008-04-13 22:12 xferreport.1.gz
-rw-r----- 1 root adm     33 2008-03-12 12:48 xferreport.2.gz
-rw-r----- 1 root adm     33 2008-03-12 12:48 xferreport.3.gz
```

As you can see it also does transfer  and transfer reports. The logs are located in /var/log/proftpd

Jim

---

### Post by windependence on 2008-06-24
cariboo907 is correct, the logs should rotate by themselves. This is set up in cron when the app is installed. You can modify how often they are rotated or force a rotate if you want, but otherwise you should not have to touch them.

-Tim

---

### Post by IbuildDW on 2008-06-24
> **RealPSL said:**
> How about this example directly from proftpd? I was a little surprised that Ubuntu does not seem to provide this as a part of the proftpd package.

[http://www.proftpd.org/localsite/Userguide/linked/x341.html]("http://www.proftpd.org/localsite/Userguide/linked/x341.html")

I looked at that script, but I thought it stops the service to copy the log.  That's not really an option, the server needs to stay up and running 24/7.  Maybe I need to better understand what 

"killall -HUP proftpd" 

will actually do.

---

### Post by IbuildDW on 2008-06-24
> **cariboo907 said:**
> Proftpd does rotate logs here is an example from my server:
Jim

Maybe I need to leave it up and running for a bit.  I don't yet have any .0,.1,.2 files in my /var/log/proftpd directory.

---

### Post by IbuildDW on 2008-06-24
> **windependence said:**
> cariboo907 is correct, the logs should rotate by themselves. This is set up in cron when the app is installed. You can modify how often they are rotated or force a rotate if you want, but otherwise you should not have to touch them.

-Tim

I did a "crontab -l" and "sudo crontab -l" and I didn't see any scheduled jobs.  Should I be looking somewhere else?

TIA

---

### Post by windependence on 2008-06-24
> **IbuildDW said:**
> I looked at that script, but I thought it stops the service to copy the log.  That's not really an option, the server needs to stay up and running 24/7.  Maybe I need to better understand what 

"killall -HUP proftpd" 

will actually do.


This kills the proftp process and restarts it.

What we are all trying to tell you is that this is set up already automatically. You don't have to do anything or create any files or crontabs. The log will rotate by itself.

-Tim

---

