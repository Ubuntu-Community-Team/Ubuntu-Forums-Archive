---
title: "Server randomly becomes unresponsive"
date: 2009-11-03
forum: Server Platforms
---

### Post by david00 on 2009-11-03
Hi, this is a fairly difficult issue to diagnose, so be patient...

We have a server running Ubuntu 8.04.  It runs the following services: MySQL, Apache (prefork/mod_php), JBoss, memcached.  As well as some other less demanding services like sshd, exim, ntpd, etc.

It has 4 cores and 8GB RAM.  MySQL is allocated around 3GB of this RAM.  JBoss takes another GB roughly, and ~60 Apache worker processes means that it averages 5-6GB RAM usage.  It has a 2GB swap partition.

As the uptime of the machine goes up, the swap usage (shown by htop) climbs.  The machine is not actually paging in, but it is swapping large processes out to disk - JBoss and some other large ones.  This is not a problem, since these are rarely used, and there's not much benefit in keeping them resident.  However, the swap usage will become 99% in a few weeks of the server being up.

Since we have Nagios monitoring the system through NRPE, we get alerts for high load averages, RAM usage, HTTP traffic, etc.  However, occasionally and randomly, the server will just hang.  Since it's remote, we can't tell exactly what's happening, but attempts to SSH will hang, though the server will still respond to ping, and all services will time out.  The only way to fix this is to reboot the server (which we can do remotely).  It comes back up without a problem, but there's _nothing_ in the log files to indicate a problem.

The only cause I can think is that something pushed the server into swap - but we have a good 3GB of headroom in RAM, plus alerts monitoring the RAM usage, and none are triggered.  In any case, surely either the kernel should start killing processes, or it should start paging heavily and sending the load skyrocketing (thus triggering an alert) before just dying in this way?

By the way, I should mention what logs I checked for this problem: syslog, messages, kern.log.  Also analyzed the HTTP access log for the time, and there's no unusual traffic - plus I've seen in the past that high traffic causes high load, but not blanket unresponsiveness like this.  We also have alerts for the MySQL queries per second value, and these never get triggered.

I'm out of ideas - can anyone suggest anything?

---

### Post by ploum on 2009-11-03
I often have that kind of trouble with a server and the solution I've found is always the same : change the RAM. Sometimes, RAM can be corrupted in as few as 6 months.

That's my experience but I'm not sure it explains every crash.

---

