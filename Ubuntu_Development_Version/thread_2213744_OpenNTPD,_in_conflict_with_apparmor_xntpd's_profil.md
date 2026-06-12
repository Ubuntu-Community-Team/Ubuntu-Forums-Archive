---
title: "OpenNTPD, in conflict with apparmor xntpd's profile on Trusty (14.04 LTS)."
date: 2014-03-28
forum: Ubuntu Development Version
---

### Post by ksmigrod2 on 2014-03-28
I've tried to setup time synchronization with Domain Controller via ntpd on a machine running ubuntu.
Unfortunately default xntpd was unwilling to keep time in sync with DC. (it may have something to do with the fact, that network is isolated, and DC is relying on its own RTC, I'm trying to keep time in sync just for log's timestamps sake).

The workaround was to use OpenNTPD, but it failed to start. The reason was apparmor. I needed to add the folowing lines to /eta/apparmor.d/usr.sbin.ntpd file:

```
capability dac_override,
/etc/openntpd/** r,
/var/lib/openntpd/ntpd.drift rw,
/{,var/}run/openntpd.pid w,

```

First line is was needed to apply clock frequency adjustments,
Second line allows daemon read configuration,
Third line is needed to maintain drift information across reboots
Fourth line allows creation of pid file.

With this lines in apparmor profile I'm able to use OpenNTPD.

---

### Post by bapoumba on 2014-03-30
Moved to Ubuntu +1.

---

