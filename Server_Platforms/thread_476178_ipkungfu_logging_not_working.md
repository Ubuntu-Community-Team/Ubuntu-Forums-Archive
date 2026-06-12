---
title: "ipkungfu logging not working"
date: 2007-06-16
forum: Server Platforms
---

### Post by noahwallach on 2007-06-16
Hi there,

ipkungfu is explicitly configured for verbose logging output.  I am
unable to find rejected packets in the syslog.

Any clues what I am going wrong?

Here is my /etc/ipkungfu/log.conf file

Syslog is running:
$ ps -uaxww | grep syslog
Warning: bad ps syntax, perhaps a bogus '-'? See
[http://procps.sf.net/faq.html](http://procps.sf.net/faq.html)
syslog    9963  0.0  0.0   1764   664 ?        Ss   15:23   0:00
/sbin/syslogd -u syslog
noah     10483  0.0  0.0   2876   796 pts/0    S+   21:18   0:00 grep syslog




--- snip ---

$ cat /etc/ipkungfu/log.conf
# Please read the README for more info.
#
# Many systems use /var/log/syslog for logging
#

# Logging facility to use. Default is syslog, as you
# must have ulog support in your kernel, and your
# userspace iptables, as well as have ulogd properly
# configured and running to use ulog.
LOG_FACILITY=syslog
#LOG_FACILITY=ulog

# This will make a log of all new connections established
# on the external device
LOG_EST_EXT=1

# This will log all new connections established on your
# internal device(s)
LOG_EST_INT=1

# Log packets that aren't caught by any specific rules
LOG_CATCH_ALL=1

# Log port scans
LOG_PORT_SCANS=1

# How many syslog entries per second (or minute) per rule?
LOG_FLOOD="3/s"
#LOG_FLOOD="1/m"

# Log dropped icmp echo request packets beyond what you have
# specified in PING_FLOOD
LOG_PING=1

# Log packets potentially related to a Denial of Service attack
LOG_DOS=1

# Log invalid packets
LOG_INVALID=1

# Log fragmented packets
LOG_FRAGMENTS=1

# Drop packets on these tcp ports without logging
DONT_LOG_TCP="135 137 139 6666"

# Drop packets on these udp ports without logging
DONT_LOG_UDP="1434"



--- snip ---

---

