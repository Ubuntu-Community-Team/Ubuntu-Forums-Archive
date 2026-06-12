---
title: "strange /var/log/messages"
date: 2005-06-08
forum: Server Platforms
---

### Post by dallypost on 2005-06-08
My /var/log/messages is filled with...

Jun  8 01:45:58 localhost -- MARK --
Jun  8 02:05:58 localhost -- MARK --
Jun  8 02:25:58 localhost -- MARK --
Jun  8 02:45:58 localhost -- MARK --
Jun  8 03:05:58 localhost -- MARK --
Jun  8 03:25:58 localhost -- MARK --
Jun  8 03:45:58 localhost -- MARK --
Jun  8 04:05:58 localhost -- MARK --
Jun  8 04:25:58 localhost -- MARK --
Jun  8 04:45:58 localhost -- MARK --
Jun  8 05:05:59 localhost -- MARK --
Jun  8 05:25:59 localhost -- MARK --
Jun  8 05:45:59 localhost -- MARK --
Jun  8 06:05:59 localhost -- MARK --
Jun  8 06:25:30 localhost exiting on signal 15
Jun  8 06:25:31 localhost syslogd 1.4.1#16ubuntu6: restart.
Jun  8 06:45:31 localhost -- MARK --
Jun  8 07:05:31 localhost -- MARK --
Jun  8 07:25:31 localhost -- MARK --
Jun  8 07:45:31 localhost -- MARK --
Jun  8 08:05:32 localhost -- MARK --
Jun  8 08:25:32 localhost -- MARK --
Jun  8 08:45:32 localhost -- MARK --
Jun  8 09:05:32 localhost -- MARK --
Jun  8 09:25:32 localhost -- MARK --
Jun  8 09:45:32 localhost -- MARK --
Jun  8 10:05:32 localhost -- MARK --
Jun  8 10:25:32 localhost -- MARK --
*******@www:/var/log$ uptime
 10:42:30 up 42 days, 18:16,  1 user,  load average: 0.01, 0.50, 0.92

Can anyone tell me what is going on with this?

Lance Earl

---

### Post by skoal on 2005-06-08
Yeah, I get those too...

[...]
Jun  8 09:46:24 localhost -- MARK --
Jun  8 10:06:24 localhost -- MARK --
Jun  8 10:26:24 localhost -- MARK --
Jun  8 10:46:24 localhost -- MARK --
[...]

I just figured it was Mr. Shuttleworth using his remote shell to scan my box and make sure I didn't have any stale non-ubuntu .ISOs laying around.  Not a problem - I'm clean.

Seriously tho, I really don't know where those log entries come from either and would like to know myself.

\\//_

---

### Post by LordHunter317 on 2005-06-08
Syslog itself is adding those messages.  They're so you know the system was still up and running at that time.  It can be turned off by editing /etc/init.d/sysklogd IIRC.

---

