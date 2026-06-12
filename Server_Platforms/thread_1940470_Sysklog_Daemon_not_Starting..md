---
title: "Sysklog Daemon not Starting."
date: 2012-03-13
forum: Server Platforms
---

### Post by mruiz@ic-sa.com on 2012-03-13
Ok I have a new error.  I found that rsyslog was not working well enough so I decided to try sysklog.  Now this one is giving me a new set of errors.  Is there a permission problems that I am not seeing?

 * Restarting system log daemon...
start-stop-daemon: warning: failed to kill 1841: Operation not permitted
chown: changing ownership of `/var/log/mail.warn': Operation not permitted
chown: changing ownership of `/var/log/user.log': Operation not permitted
chown: changing ownership of `/var/log/daemon.log': Operation not permitted
chown: changing ownership of `/var/log/messages': Operation not permitted
chown: changing ownership of `/var/log/debug': Operation not permitted
chown: changing ownership of `/var/log/auth.log': Operation not permitted
chown: changing ownership of `/var/log/mail.err': Operation not permitted
chown: changing ownership of `/var/log/news/news.notice': Operation not permitted
chown: changing ownership of `/var/log/cisco.log': Operation not permitted
chown: changing ownership of `/var/log/syslog': Operation not permitted
chown: changing ownership of `/var/log/news/news.crit': Operation not permitted
chown: changing ownership of `/var/log/mail.log': Operation not permitted
chown: changing ownership of `/var/log/kern.log': Operation not permitted
chown: changing ownership of `/var/log/lpr.log': Operation not permitted
chown: changing ownership of `/var/log/mail.info': Operation not permitted
chown: changing ownership of `/var/log/news/news.err': Operation not permitted
   ...fail!

---

