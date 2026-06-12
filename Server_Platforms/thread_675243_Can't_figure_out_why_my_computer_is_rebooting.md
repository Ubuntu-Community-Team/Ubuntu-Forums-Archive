---
title: "Can't figure out why my computer is rebooting?"
date: 2008-01-22
forum: Server Platforms
---

### Post by Rizado on 2008-01-22
As the title say my computer seem to be rebooting sometimes. Uptime shows: ```
21:15:35 up 6 days,  4:27,  1 user,  load average: 0.00, 0.00, 0.00
```
last gives:
```
foobar      pts/1        xxxxxx           Wed Jan 16 18:56 - 18:58  (00:02)
foobar      pts/0        xxxxxx           Wed Jan 16 18:45 - 20:13  (01:28)
reboot      system boot  2.6.23.12        Wed Jan 16 16:49 - 21:17 (6+04:27)
foobar      pts/0        xxxxxx           Tue Jan 15 22:23 - 22:33  (00:10)

```

This has happened a couple of times irregularly the last month but I can't recall making a reboot anytime since early december. grep reboot .bash_history confirms this, and as you can see I wasn't logged in at the time of the reboot...

So what could be rebooting this computer?

---

### Post by MJN on 2008-01-22
At the very least check your logs (syslog in particular).

Mathew

---

### Post by Rizado on 2008-01-25
> **MJN said:**
> At the very least check your logs (syslog in particular).

MathewWeird, the system seem to reboot every wednesday starting a few weeks ago. Can't find anything in the logs (not sure which ones to check really). Only service open outwards is ssh running on a non-standard port and requires a private key along with a long password. So unless there's been any serious bugs in ssh since december I can't believe someone has access through there...

---

### Post by MJN on 2008-01-25
Syslog (/var/log/syslog) is probably the best place to start - post the contents around the Wednesday reboot time(s). A dozen or so lines before the event and a couple after should suffice.
 
Mathew

---

### Post by arkangel on 2008-01-25
every wednesday ?

take a look at  cron  and cron files

---

### Post by Rizado on 2008-01-25
I've checked cron, doesn't have any rebooting script.

```
Jan 23 16:34:52 foobar dhcpd: DHCPREQUEST for 192.168.1.2 from 00:02:XX:54:XX:XX via eth1
Jan 23 16:34:52 foobar dhcpd: DHCPACK on 192.168.1.2 to 00:02:XX:54:XX:XX via eth1
Jan 23 17:43:56 foobar syslogd 1.4.1#21ubuntu3: restart.
Jan 23 17:43:56 foobar kernel: Inspecting /boot/System.map-2.6.23.12
Jan 23 17:43:58 foobar no-ip[4145]: v2.1.7 daemon started
Jan 23 17:43:59 foobar no-ip[4145]: hostname.hopto.org was already set to xxx.xxx.xxx.xxx.
Jan 23 17:43:59 foobar kernel: Loaded 24737 symbols from /boot/System.map-2.6.23.12.
Jan 23 17:43:59 foobar kernel: Symbols match kernel version 2.6.23.
Jan 23 17:43:59 foobar kernel: No module symbols loaded - kernel modules not enabled.
```The computer seem to just die for an hour before it comes back online, although I haven't heard any complains about it doing so... Also there's nothing more going on before than DHCP requests and acks.

Lets say the power gets cut. Would the reboot user get logged in when the power is restored and system is booting again?

And the last line ```
kernel modules not enabled
```I have kernel modules so they can't really be disabled...

---

