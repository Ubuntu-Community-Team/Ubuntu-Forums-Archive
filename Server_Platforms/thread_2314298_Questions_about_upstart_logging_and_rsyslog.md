---
title: "Questions about upstart logging and rsyslog"
date: 2016-02-20
forum: Server Platforms
---

### Post by Joe_Auty on 2016-02-20
I'm a little confused.

We are using an API framework provided by Strongloop that logs content that would otherwise be logged to stderr and stdlog to /var/log/upstart. We would like to ship these logs to our loghost. The following is set in rsyslog.conf

*.* @@10.67.27.10:514

and the loghost is receiving a bunch of logs (cron, kernel, postfix, sshd, etc.). However, the logs from /var/log/upstart are not being delivered.

Do we need to create some sort of upstart facility to accomplish this? I'm kind of confused as to generally speaking what is in the jurisdiction of the service logging data and the rsyslog service itself. Does any service that support rsyslog also by extension support delivering to a loghost like I'm trying to do? Does upstart support rsyslog? Is upstart unique somehow? Are facilities just for OS controlled stuff and are a means to categorize log output by severity, or can/do third party services have facilities too?

Really anxious to understand this a little better, but for now I would be happy just to start shipping logs. I thank you in advance!

---

### Post by Joe_Auty on 2016-02-20
Also, is it worth understanding how rsyslog contrasts with other logging systems such as syslog-ng, or has rsyslog effectively replaced these other logging daemons?

---

### Post by MAFoElffen on 2016-02-22
As upstart is still evolving-- In a little over a month, that will be easier... or at least a little different.

With the release of 16.04 LTS Server, systemd, journalctl to turn on journald, then...

In /etc/systemd/journald.conf, change / uncomment:
```

ForwardToSyslog=yes

```
Then your rsyslog would pick it up from the syslog.

They are working on remote pieces such as systemd-journald-remote and systemd-journald-gatewayd.service... but they are not there yet, and even then, it'll take a while to drift downstream.

---

