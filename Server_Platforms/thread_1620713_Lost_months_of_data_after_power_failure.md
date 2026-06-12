---
title: "Lost months of data after power failure"
date: 2010-11-13
forum: Server Platforms
---

### Post by lapichiflati on 2010-11-13
Running Ubuntu headless server 9.10 with a RAID 1 on ext3.  After a power failure (UPS power button was hit accidentally), I logged into the system via ssh and found that I had lost all data since my last reboot, which was 4 months ago.  It was as if I had a perfect snapshot of my machine from 4 months ago.  Everything, database files, logs, all report as if the machine had been off for 4 months.  Fortunately, I have quality backups of all my data so I am able to recover, but I have never had such a problem before and I cannot figure out what happened.  Any suggestions are appreciated.

I will post any logs necessary.

---

### Post by CharlesA on 2010-11-13
I haven't heard of that happening before. I would expect data corruption after a power failure, not a complete loss of data.

---

### Post by SeijiSensei on 2010-11-13
You're sure you booted the same partition for the filesystem root ("/")?  Sure that any other partitions that needed to be mounted were in fact remounted at reboot?  If, for instance, /var was once in the same filesystem as /, but then you later mounted a new /var over the old one that failed to be remounted, you'll now see the old /var instead.

---

### Post by lapichiflati on 2010-11-13
On this system there are no additional partitions, just / and swap and fstab is using UUIDs so not much chance it booted the wrong partition.  I am thinking it has to be a journaling issue or something to do with a raid 1 error.

Actually, it didn't rollback to last reboot, just another random moment, August 10, over 3 months ago, and this server is in daily use.


Just a glimpse of /var/log/messages:
> 
Aug 10 05:04:40 serv4 autossh[2290]: timeout polling to accept read connection
Aug 10 05:04:40 serv4 autossh[2290]: port down, restarting ssh
Aug 10 05:04:40 serv4 autossh[2290]: starting ssh (count 640)
Aug 10 05:04:40 serv4 autossh[2290]: ssh child pid is 5174
Aug 10 06:53:52 serv4 rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="1021" x-info="http://www.rsyslog.com"] rsyslogd was HUPed, type 'lightweight'.
Aug 10 19:47:50 serv4 kernel: Kernel logging (proc) stopped.
Nov 13 08:26:56 serv4 kernel: imklog 4.2.0, log source = /var/run/rsyslog/kmsg started.
Nov 13 08:26:56 serv4 rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="4904" x-info="http://www.rsyslog.com"] (re)start
Nov 13 08:26:57 serv4 rsyslogd: rsyslogd's groupid changed to 102
Nov 13 08:26:57 serv4 rsyslogd: rsyslogd's userid changed to 101
Nov 13 08:26:57 serv4 kernel: [    0.000000] Initializing cgroup subsys cpuset
Nov 13 08:26:57 serv4 kernel: [    0.000000] Initializing cgroup subsys cpu


---

### Post by CharlesA on 2010-11-13
That log looks normal, so I don't know why you'd be missing a chunk of data even after a power outage. Could it have been the result of a restore after the power came back on?

---

