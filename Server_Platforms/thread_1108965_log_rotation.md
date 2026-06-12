---
title: "log rotation"
date: 2009-03-28
forum: Server Platforms
---

### Post by MisterM on 2009-03-28
Hi!

I have just learned that logrotate is not installed on our production web server. However, some log files are being rotated:
auth.log  daemon.log  debug  dmesg  kern.log  mail.err  mail.info  mail.log  mail.warn  messages  syslog

I intend to install logrotate now, and was just wondering, how the above logs are already being rotated. Is there another log rotation utility (other than logrotate) that is installed on ubuntu by default?

I should mention that the server runs ISPConfig 2. Is ISPConfig responsible for this?

---

### Post by tubezninja on 2009-03-28
[According to this]("https://help.ubuntu.com/community/LinuxLogFiles#Log%20Rotation"), logrotate is the default for ubuntu, and it's installed by default on all the ubuntu servers I've looked at.  If your installation is different,  check your /etc/cron* scripts to see what's running and rotating your files.

---

### Post by MisterM on 2009-03-28
I was quite surprised to find that logrotate is not installed, too.

I have already looked through the cronjobs and couldn't find anything relevant. I suspect either ISPConfig or logwatch is doing this. Both have cronjobs set up. Can anyone confirm this?

Thanks!

---

### Post by hictio on 2009-03-28
> **MisterM said:**
> I was quite surprised to find that logrotate is not installed, too.

I have already looked through the cronjobs and couldn't find anything relevant. I suspect either ISPConfig or logwatch is doing this. Both have cronjobs set up. Can anyone confirm this?

Thanks!

No, Logwatch (again, on a default install) does not rotate logs, simply scans them for interesting bits, and then mails the results.
Matter of fact, I had problems on some boxes, non Ubuntu, in which the '/var/log/secure' log wasn't being rotated, and I continually got Logwatch reports of ssh logins... It kept me a little crazy till I figure that one out :)

---

### Post by MisterM on 2009-03-28
Thanks for the info, hictio. I guess that leaves ISPConfig.

---

