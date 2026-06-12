---
title: "Massive syslog and other files"
date: 2010-01-31
forum: Security
---

### Post by ItsAaron on 2010-01-31
Hi. All I ever use my ubuntu for is programming C, and now I cant even do that because I dont have enough room. I looked around and these are the four files in my var/log folder that are causing me to have no space :/

kern.log -   5GB
messages - 1.9GB
syslog -      2.9GB
syslog.1 -   1.3GB

Can I delete these? And is there a fix for them doing whatever this is?

Thanks in advance.

---

### Post by ItsAaron on 2010-01-31
Bump. Its really irritating :/

---

### Post by unspawn on 2010-01-31
Seeing a "syslog.1" means your logs probably *did* get rotated, however log file sizes could be due to excessive errors or way verbose logging or unusual log rotation settings. For checking your log rotation see /etc/logrotate.conf and /etc/logrotate.d and /etc/cron.daily/sysklogd. 
* If your machine is not always on you might benefit from running anacron or equivalent.
** If you don't read system logs then I suggest you install Logwatch. Way easier to read the emailed reports and adjust whatever it alerts about. 
*** Yes, you may be miffed by syslog and such but bumping this fast is not polite.

---

### Post by tubbygweilo on 2010-01-31
Bump. Is really irritating :/

Aaron, a few users have reported such [problems]("http://ubuntuforums.org/showthread.php?t=1331883&highlight=syslog+space") > Specifically, syslog, syslog.1 and user.log are taking up 309GB of space altogether but these are entries relating to Pulse Audio and a couple of other applications. 

What is filling your logs?

---

### Post by HermanAB on 2010-01-31
Howdy,

You can simply delete those log files.  You can also stop the syslog daemon, so they won't come back.  Logging everything is usually a good idea, but on a development system in a R&D environment, it has little to no value.

---

