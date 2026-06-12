---
title: "using logger and syslog/rsyslog to log a non-standard log file (xbmc)"
date: 2010-01-14
forum: Server Platforms
---

### Post by prupert on 2010-01-14
Hi

I have successfully created a remote logging server using syslog-ng and logzilla. It is running on 8.04 LTS (though I'll upgrade to 10.04 LTS when it comes out), hence I have to use syslog-ng and not rsyslog (since the 8.04 version is too old).

I have a number of Ubuntu boxes logging to this remote server. I would like to also log some non-standard log files as well, such as the xbmc.log file, amongst others. 

I thus need a way to send the xbmc.log (and others) to the server. The only way I can think of doing it, is to use the logger command to send the xbmc.log to the local syslog, which then logs it to the server. However, from my experiments using logger will send the whole file each time, not just the updates (fair enough, how does it know what is new).

So, I then though I'd try using tail and logger so:

tail -f .xbmc.log | logger -t xbmc

But this doesn't seem to work, since it wasn't updating any changes either, not to sure why, but it seems tail is following the changes....

So, I was wondering if anyone out there has any suggestions how I might do this, or if there are any scripts out there?

BTW, this isn't just for xbmc, I was just using that log as an example.

Cheers

---

### Post by prupert on 2010-01-15
So, I'll reply to myself. 

Some kind dude replied to my question on the xbmc forum:

[http://xbmc.org/forum/showpost.php?p=483987&postcount=7](http://xbmc.org/forum/showpost.php?p=483987&postcount=7)

This seems to work, well atleast for apache2.logs, not for xbmc logs, but that is apparently a bug with xbmc.

So, coolio.

---

