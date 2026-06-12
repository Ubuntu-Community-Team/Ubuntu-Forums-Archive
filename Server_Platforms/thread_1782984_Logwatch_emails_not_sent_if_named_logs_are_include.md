---
title: "Logwatch emails not sent if named logs are included"
date: 2011-06-15
forum: Server Platforms
---

### Post by Barry Cent on 2011-06-15
Hi,

I've suddenly stopped getting emails from logwatch which runs on an Ubuntu server daily using cron.

After a good day or so of troubleshooting, I was able to establish that it was the 'Service = named' line in my logwatch.conf file, which was stopping the emails from coming through. If I commented out this line, the logwatch emails come through with no issues, uncomment, and I don't get an email. I don't get any error from logwatch itself when I run it, even with '--debug high', leading me to think that my email configuration is setup ok, at least. Furthermore, I tried running logwatch with '--output file --format html' and logwatch produces a valid html file.

I then thought: "Could I have a entry in my Bind/named log files which could be rejected by my ISP's smtp server?". So, (to the best of my knowledge) I cleared out the log files in /var/log that contained messages from named. I then ran logwatch (including the named service in my logwatch.conf file) and I got an email through, with a pretty much empty named section, which is exactly what I anticipated. Great! - it's fixed.

So, the cron.daily ran early this morning, but still no email in my inbox when I got up... :-(

I then tried to run 'logwatch --Range today' and lo and behold, I got a logwatch report email, which included a named section, with log entries in there. So it seems that something that's been logged by named overnight to my logfiles (i.e. '--Range yesterday') has caused issues again with logwatch's ability to send reports through my ISP's smtp servers.

Now, my question is: How on earth do I go about fixing this? I've no idea where to start troubleshooting it!

I hope someone can help.

Cheers,

Joe

---

### Post by Barry Cent on 2011-08-17
Just for anyone who faces this issue too:

It turns out that this issue seems to be Apple's MobileMe email service which was blocking these emails for some reason.

It seemed to start working again, and since then I have replaced the server which this was relating to and I still get the odd one from my DNS server that gets blocked. I guess MobileMe is flagging something up as spam in my logwatch report, or something like that.

Joe

---

