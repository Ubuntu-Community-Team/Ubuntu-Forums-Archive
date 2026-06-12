---
title: "Whats the ubuntu deal with root?"
date: 2007-05-20
forum: Server Platforms
---

### Post by zenkaon on 2007-05-20
Hey everyone,

I am generally happy to use sudo but could someone please explain why can't I log on as root? isn't this taking SELinux a step too far?

In a previous life, my ext3 partition had red hat installed and it would email the root user a summary of the network connections, cron jobs, yum updates etc etc. Where do these get mailed to in ubuntu? I really like to have the logs.

Also, how do I set the system log to keep all logs for a year (or more)? currently the system log only seems to do a few days.

---

### Post by seamless on 2007-05-20
Ubuntu does not use SELinux. For reasons you can find using Google, Ubuntu just doesn't use a root user and uses sudo instead. However, you can enable the root user if you choose. The logs are not mailed and are located in the /var/log/ directory. If you want them mailed to a specific user you will have to set that up yourself. The logs in that directory are kept for more than a few days but they are rotated so that a single log does not become to large to manage. Hence why there are .#.gz files in the log directory. If you don't want this to happen remove the logrotate entry from /etc/cron.daily/.

---

### Post by jtc on 2007-05-20
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by craigp84 on 2007-05-21
Because Ubuntu's not quite 100% up to speed yet for use as a server. Ok actually, it's fscking miles off the mark - it doesn't come setup to send nice useful reports like redhat does.

But, no worries, it's an easy fix - > sudo apt-get install logwatch - You'll now get your reports. Check /etc/aliases to see where the mails to root are going.

See /etc/logrotate.d/* for the log retention stuff.

Hope this helps,

-c

---

