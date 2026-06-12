---
title: "FAILED su for user by root"
date: 2017-02-28
forum: Server Platforms
---

### Post by knix2 on 2017-02-28
After Rebooting i have several logs in the auth.log like:

No passwd entry for user 'user'
Feb 25 10:06:09 slft90 su[2698]: FAILED su for user by root
Feb 25 10:06:09 slft90 su[2698]: - ??? root:user

Software used: Ubuntu 16.04 LTS Server with Mate and XFCE-Desktop

/etc/nsswitch.conf
passwd:         compat nis ldap
group:          compat nis ldap
shadow:         compat nis ldap

LDAP-Connections are working properly.

How can this be fixed


These messages are automatically forworded to a central syslog server and generates there alerts.

---

### Post by howefield on 2017-02-28
Thread moved to the "*Server Platforms*" forum for a better fit.

---

