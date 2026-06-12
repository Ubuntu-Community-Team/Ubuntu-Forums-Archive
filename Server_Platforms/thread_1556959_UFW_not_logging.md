---
title: "UFW not logging"
date: 2010-08-20
forum: Server Platforms
---

### Post by h1tm4n on 2010-08-20
Hi All,
Using a fresh Ubuntu server install, i setup UFW :


$ sudo ufw allow OpenSSH
$ sudo ufw allow Apache
$ sudo ufw logging full
$ sudo ufw enable
$ sudo ufw status verbose

Status: active
Logging: on (full)
Default: deny (incoming), allow (outgoing)
New profiles: skip

To Action From
-- ------ ----
22/tcp (OpenSSH) ALLOW IN Anywhere
80/tcp (Apache) ALLOW IN Anywhere


When connecting from external box to this server on port 25, the connection is properly blocked by UFW but i can't find any UFW log (/var/log/kern.log, /var/log/messages, /var/log/ufw.log ...).

I'm using default rsyslog.

Any idea ?
Many thanks.

---

### Post by h1tm4n on 2010-08-23
Replacing rsyslog with syslog-ng do resolve the issue.

---

