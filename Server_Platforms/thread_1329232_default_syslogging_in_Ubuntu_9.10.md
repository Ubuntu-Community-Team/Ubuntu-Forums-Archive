---
title: "default syslogging in Ubuntu 9.10"
date: 2009-11-17
forum: Server Platforms
---

### Post by stephanhughson on 2009-11-17
Hi,

On my Ubuntu 9.04, I have /sbin/syslogd running.
On my Ubuntu 9.10, I have /usr/sbin/rsyslogd running.

I guess the default has changed?

I also notice that I can configure logging in /etc/rsyslog.d/ now.

so my question are:

Is /etc/syslog.conf being phased out?

Should I just be using the /etc/rsyslog.d/ directory now?

Should I / Can I delete /etc/syslog.conf if it's being ignored now anyway?

Is there somewhere where I can find out about these changes? I read the release notes for 9.10 (I think), but I didn't see this. I know it's a minor change but it would have been good to know. I made changes to /etc/syslog.conf today and they were ignored and I was confused for about 10 minutes.

---

