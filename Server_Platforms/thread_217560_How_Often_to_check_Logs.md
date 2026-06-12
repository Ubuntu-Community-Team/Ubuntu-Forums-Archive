---
title: "How Often to check Logs?"
date: 2006-07-17
forum: Server Platforms
---

### Post by va3uxb on 2006-07-17
I've got a Dapper server running at home, which I use as a private FTP server to allow me to move files between home and the office, and as a backup repository for the nightly backups from work.  The server is set up headless, just a Mac Mini on a shelf in a storage room, sort of out-of-sight, out-of-mind.

Yesterday I happened to ssh onto it to check something. One of the things I was looking at included using the netstat command, specificaly netstat -ntap | grep EST -- to see what connections were established.  I found a strange IP address was connected to port 21, the ftp server.

So I had a look at /var/log/messages and found that this IP address had been hitting my FTP server almost nonstop for 2 days, trying to access the system.  Just a constant stream of log-on attempts.  Fortunately they were all failures.  I'm running pure-ftpd and it's locked down very tightly, no anonymous ftp, only one user account is enabled, but it still annoyed me.   So I switched it to running a non-standard port, so port 21 doesn't work any more.

But it got me thinking.  How often do people check their log files?  Should I be looking through them daily, or weekly?  Is there a standard rule-of-thumb?  

Thanks!

-Stephanie

---

### Post by Randomskk on 2006-07-17
The program logcheck, available in the repos, can email you new log entries every hour, and if an entry it repeated it just shows it once and says how many times it was repeated.
It's also configured to ignore normal and standard log messages, just showing things that are out of the ordinary, although you can configure this behaviour.

If nothing else it's great because you get a backup of the logs in your inbox, and when you stop getting them you know something's wrong.

---

