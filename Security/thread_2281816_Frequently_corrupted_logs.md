---
title: "Frequently corrupted logs"
date: 2015-06-09
forum: Security
---

### Post by Lars Noodén on 2015-06-09
I'm getting frequently corrupted logs on an installation with Ubuntu server 14.04.x LTS.  What's the cause and how to prevent it?

From syslog:

```

Jun  1 19:09:56 gazp9 dbus[927]: [system] Activating service name='org.freedesktop.systemd1' (using servicehelper)
Jun  1 19:09:56 gazp9 dbus[927]: [system] Successfully activated service 'org.freedesktop.systemd1'
May 31 10:13:59 gazp9 rsyslogd: message repeated 11 times: [ [origin software="rsyslogd" swVersion="7.4.4" x-pid="1056" x-info="http://www.rsyslog.com"] rsyslogd was HUPed]
Jun  1 19:10:30 gazp9 rsyslogd: [origin software="rsyslogd" swVersion="7.4.4" x-pid="1056" x-info="http://www.rsyslog.com"] exiting on signal 15.
^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@
^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@
^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@
^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@
^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@
^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@
^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@
...
^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@Jun  1 19:13:28 gazp9 rsyslogd: [origin software="rsyslogd" swVersion="7.4.4" x-pid="891" x-info="http://www.rsyslog.com"] start

```

From authlog

```

Jun  1 19:08:30 gazp9 su[13937]: pam_unix(su:session): session opened for user foo by bar(uid=1001)
^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@Jun  1 19:13:28 gazp9 systemd-logind[939]: New seat seat0.
Jun  1 19:13:28 gazp9 systemd-logind[939]: Watching system buttons on /dev/input/event3 (Power Button)

```

---

### Post by cariboo on 2015-06-10
It almost looks like it may be a missing language pack problem.

---

