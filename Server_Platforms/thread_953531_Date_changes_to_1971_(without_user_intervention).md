---
title: "Date changes to 1971 (without user intervention)"
date: 2008-10-20
forum: Server Platforms
---

### Post by jssykes on 2008-10-20
I have an Ubuntu 8.04 server running as a VM inside of a VMWare ESX 3.5 environment.

The server is a basic LAMP box running several websites (using Joomla!, Word Press, Media Wiki).  At seemingly random times, the clock on the VM goes to a date in 1971.  (Today it went to June 30, 1971.)  After the clock goes crazy, Apache and the other parts of the system seem to hang.  A reboot seems to fix the issue.

I've setup the server using NTP to pull time off of a local server, but even that doesn't seem to prevent the behavior.

Does anyone have any idea what might be going on here?

Thank you in advance,

--JS

---

### Post by drubin on 2008-10-20
take a look at   the last few lines of /var/log/messages, See if something funny is going on with the system.  
```
tail -fn1000 /var/log/messages
```

Also you say your system hangs try  see what is using up the recourses. 
```
top 
```

Also a clarification, after a reboot does your time come back to the correct value.

---

### Post by jssykes on 2008-10-24
Sorry for the delay in the response.  I had to wait for the problem to occur again:

When this happens…
[INDENT]
a)top and vmstat hang at execution, but our snmp aggregator shows that that around 90-95% of memory is in use
b)ps aux shows that mysqld is using around 130M of virtual (VSZ)
c)shutdown –r now results in a system hang during the shutdown messages and we have to bounce the VM guest[/INDENT]

Thankfully we did just snag this in /var/log/messages when we first noticed the problem:

Oct 23 08:17:15 ignatius -- MARK --
Oct 23 08:37:15 ignatius -- MARK --
Oct 23 08:57:15 ignatius -- MARK --
Oct 23 09:17:15 ignatius -- MARK --
Oct 23 09:37:15 ignatius -- MARK --
Oct 23 09:57:15 ignatius -- MARK --
Oct 23 10:17:15 ignatius -- MARK --
Oct 23 10:37:15 ignatius -- MARK --
Oct 23 10:57:15 ignatius -- MARK --
Jan 10 11:06:11 ignatius kernel: [267813.033677] Clocksource tsc unstable (delta = 1307923969317ns)

NTP status:

stephen@ignatius:~$ ntpq --peers
     remote           refid      st t when poll reach   delay   offset  jitter
==============================================================================
 xavier.nts.edu  64.113.33.2      3 u    3   64   37    0.443  7872.16 9321.70
 ns1.kirkforcong 64.183.56.58     2 u    3   64   37   67.893  7873.11 9684.60

---

