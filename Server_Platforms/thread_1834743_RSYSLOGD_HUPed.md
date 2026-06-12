---
title: "RSYSLOGD HUPed ???"
date: 2011-08-28
forum: Server Platforms
---

### Post by hans b. on 2011-08-28
Hi,

Port 514 is closed
No logging on my server via rsyslogd?

I try to register the logging from my router on my Ubuntu server via port 514 ans RSYSLOGD.

I've installed my Ubuntu 11. on a small 64 Bit Atom-server and I've don a port scan to check if port 514 is open or closed? It's closed.

I've checke my logging and found:
omesrv rsyslogd: [origin software="rsyslogd" swVersion="4.6.4" x-pid="580" x-info="http://www.rsyslog.com"] rsyslogd was HUPed, type 'lightweight'.

Any suggestions how to solve this?

Hans

---

### Post by cconstantine on 2011-08-28
Is rsyslogd in the process table? ...open inbound udp/514 to allow rsyslogd to rcv msgs. Check netstat(1) to vrfy rsyslogd is listening.

---

### Post by konsole on 2011-08-28
By default rsyslogd is not configured for remote logging until you enable it.> man rsyslog.conf

---

