---
title: "Wflogs unusable"
date: 2007-01-07
forum: Server Platforms
---

### Post by marekdef on 2007-01-07
Hello,

I have installed wflogs package. It is intended to generate human readable logs from iptables (from file where iptables logs to).
It runs as a cron job every day.

However, it can never produces any logs because gets killed becuase of consuming too much memory ...

[ 1679.759400] Total swap = 4064808kB
[ 1679.759402] Free swap:            0kB
[ 1679.766446] 262128 pages of RAM
[ 1679.766451] 6577 reserved pages
[ 1679.766453] 6044 pages shared
[ 1679.766454] 199 pages swap cached
[ 1679.766715] Out of Memory: Kill process 9614 (wflogs) score 1217036 and children.
[ 1679.766718] Out of memory: Killed process 9614 (wflogs).

I have 1GB memory, 2GB swap and swapspace running in the background (but it never is able to allocate swap before wflogs gets killed). Sometimes I have 8Gb swap allocated
and is too less.

... or because watchdog resets my machine because of heavy load (the machine is indeed not responsive),

Do you experience similar problems with wflogs?
My iptables logs are not so big (i hope they are not)

du -h /var/log/iptables/iptables.log
120K    /var/log/iptables/iptables.log

---

### Post by eric_stewart on 2007-01-07
> **marekdef said:**
> Hello,

I have installed wflogs package. It is intended to generate human readable logs from iptables (from file where iptables logs to).
It runs as a cron job every day.

However, it can never produces any logs because gets killed becuase of consuming too much memory ...

[ 1679.759400] Total swap = 4064808kB
[ 1679.759402] Free swap:            0kB
[ 1679.766446] 262128 pages of RAM
[ 1679.766451] 6577 reserved pages
[ 1679.766453] 6044 pages shared
[ 1679.766454] 199 pages swap cached
[ 1679.766715] Out of Memory: Kill process 9614 (wflogs) score 1217036 and children.
[ 1679.766718] Out of memory: Killed process 9614 (wflogs).

I have 1GB memory, 2GB swap and swapspace running in the background (but it never is able to allocate swap before wflogs gets killed). Sometimes I have 8Gb swap allocated
and is too less.

... or because watchdog resets my machine because of heavy load (the machine is indeed not responsive),

Do you experience similar problems with wflogs?
My iptables logs are not so big (i hope they are not)

du -h /var/log/iptables/iptables.log
120K    /var/log/iptables/iptables.log

That's weird.  I did a standard install of wflogs, then setup a cron job so it would parse /var/log/syslog hourly for issues vs. /var/log/iptables/iptables.log.  I wonder if this might be the issue...I know it sounds far-fetched?  It also sends me an email message when it's done its job.  Here's my cron table entry (/etc/crontab) for my Cisco PIX:
----------------------------------------------------------------------------------
# Automatic run of WallFire "wflogs" script at 1:30 am each day 17 *    * * *   root   wflogs -i cisco_pix -o html  /var/log/syslog  >  /var/www/wflogs/logs.html 2>/dev/null; echo "The log's been flogged! Navigate to [http://www.breezy.ca/wflogs/logs.html](http://www.breezy.ca/wflogs/logs.html) to check who's been wacking the Stewart Family Network" | mail -s "wflogs script run" [email]root@breezy.ca[/email]

Here's my cron table entry (/etc/crontab) for my Linksys (IPtables) firewall:
----------------------------------------------------------------------------------------
30 *    * * *   root   wflogs -i netfilter -o html /var/log/syslog > /var/www/wflogs/iptablelogs.html 2>/dev/null; echo "The log's been flogged for iptables events!  Navigate to [http://www.breezy.ca/wflogs/iptablelogs.html](http://www.breezy.ca/wflogs/iptablelogs.html) to check who's been wacking the Access Point" | mail -s "wflogs script run on Sky" [email]root@breezy.ca[/email]

I'm parsing syslog since I've configured syslog-ng to accept syslog messages from all of my network boxes as well as from the local host.  I'm wondering if the iptables log might be so active that your box is chasing its tail trying to allocate memory to parse the file with your script?

I've got a link over on the Linux & Networking site that I'm running that might interest you.  There's a link in my blog that will allow you to look at the output of wflogs

[http://www.breezy.ca/?q=comment/reply/90](http://www.breezy.ca/?q=comment/reply/90)  Maybe you will consider posting some information on your findings over at our site?  We'd love to hear from you!

/Eric
webmaster [www.breezy.ca](www.breezy.ca)

---

### Post by eric_stewart on 2007-01-08
Oops.  Just noticed that now that my logs are obscenely large that wflogs isn't working.  The log gets rotated again tonight...I'll bet its a syslog file issue.  My log file is over 17 MB in size...mainly because my PIX is dumping a bunch of messages to syslog because of my daughter's PC's traffic for BitTorrent being denied.  A *ton* of traffic.

That said, It does seem that wflogs has its limits.  I'll have to Google for any FAQs on the subject.

/Eric

---

