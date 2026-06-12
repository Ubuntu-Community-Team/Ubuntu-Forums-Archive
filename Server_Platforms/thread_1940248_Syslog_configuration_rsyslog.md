---
title: "Syslog configuration rsyslog"
date: 2012-03-13
forum: Server Platforms
---

### Post by mruiz@ic-sa.com on 2012-03-13
I am having problems getting my syslog to come up.  I show the daemon is running, however, I am not showing the netstat -a is listening.  Is it my ip tables blocking it?

---

### Post by mruiz@ic-sa.com on 2012-03-13
> **mruiz@ic-sa.com said:**
> I am having problems getting my syslog to come up.  I show the daemon is running, however, I am not showing the netstat -a is listening.  Is it my ip tables blocking it?

I found the issue.  It was not iptables actually. It was actually UDPserverRun 514 was Rem'd out.  Once I took care of that, I restarted the service and syslog started working.  Hope that helps someone out there.  By the way I have it working very well on a Hyper-V server.

---

