---
title: "Fetchmail Spamming Syslog"
date: 2010-03-06
forum: Server Platforms
---

### Post by Letrazzrot on 2010-03-06
I realize this problem is not specific to Ubuntu Server, but I'll ask in case there is anyone here using Fetchmail who has had the same issue.

I have Fetchmail receiving mail from my ISP (pop3) and delivering to Dovecot.  Everything seems to work fine, but every time fetchmail does its poll, it writes log information that looks like this:

> Mar  6 15:28:51 delphi fetchmail[26167]: awakened at Sat 06 Mar 2010 03:28:51 PM CST
Mar  6 15:28:51 delphi fetchmail[26167]: Server CommonName mismatch: localhost.localdomain != pop3.tconl.com
Mar  6 15:28:51 delphi fetchmail[26167]: Server certificate verification error: self signed certificate
Mar  6 15:28:51 delphi fetchmail[26167]: Server certificate verification error: certificate has expiredThis gets written to syslog, and various mail.log files in /var/log.  Searching the internet, the best I can determine is that these error messages are not important, and can be safely ignored.

The problem, then, is that the syslog quickly gets overrun by these messages.  When just running fetchmail as a cron job, I could just send the output to /dev/null (I think).  However, the daemon is started in init.d, and I don't see a way to do this without mucking about in the default init.d/fetchmail script.

So, my question is:  is there a way to null fetchmail's output without modifying /etc/init.d/fetchmail?  Or am I missing something else here?  I am completely new to the world of Linux, along with mail routing, so I suspect the latter.

Thanks to anyone who can provide any tidbits of info.

---

### Post by Dr Small on 2010-03-06
I've never used fetchmail via init.d/. I've just always executed it via user crontab, and from there you can redirect output to /dev/null if you wanted.

---

### Post by Letrazzrot on 2010-03-06
> **Dr Small said:**
> I've never used fetchmail via init.d/. I've just always executed it via user crontab, and from there you can redirect output to /dev/null if you wanted.

I suppose that makes sense.  I do not quite understand all the ins and outs of daemons vs. cron jobs, so I wasn't sure if there was any advantage to using a daemon at startup (it was configured that way by default).  From what I gather, cron is a daemon itself, so it probably would amount to doing the same thing.

I'll try it out, thanks for the reply!

---

