---
title: "systemd logging (journalctl) defaults"
date: 2015-03-30
forum: Ubuntu Development Version
---

### Post by merc82 on 2015-03-30
Systemd has its own logging tool, journalctl. In some cases the the traditional logs such as syslog and kern.log continue to exist; but in the case of pm-suspend.log it is no longer updated. Now you must rely on journalctl for power management event logging. The default settings for systemd in 15.04 only keep journalctl logs since the last reboot. This has been a problem for me as I'm trying to diagnose a system that occasionally hangs on resuming from suspend.

To keep records across boots you must change the default settings. 
Details:
-journalctl settings are in /etc/systemd/journald.conf.
-to keep logs across boots setting "Storage=auto" needs to be "Storage=persistent"
-I created a modified journald.conf in /etc/systemd/journald.conf.d/

I think the default should be to keep these logs. I considered opening a launchpad bug against systemd but this is a feature request not a true bug and support is aware of this default.

Is it possible to have pm-suspend.log work under systemd?

---

### Post by cariboo on 2015-03-30
We are in Feature Freeze now, but I'd suggest you create a feature request bug for W* W* (15.10). :)

---

### Post by sgage on 2015-03-30
> **cariboo907 said:**
> We are in Feature Freeze now, but I'd suggest you create a feature request bug for W* W* (15.10). :)

BTW, I had a great idea for W* W*. What do you think of this:

Warty Warthog

;-)

(Warty was my first Ubuntu installation - that's starting to be a long time ago...)

---

### Post by dino99 on 2015-03-31
> **merc82 said:**
> Systemd has its own logging tool, journalctl. In some cases the the traditional logs such as syslog and kern.log continue to exist; but in the case of pm-suspend.log it is no longer updated. Now you must rely on journalctl for power management event logging. The default settings for systemd in 15.04 only keep journalctl logs since the last reboot. This has been a problem for me as I'm trying to diagnose a system that occasionally hangs on resuming from suspend.

To keep records across boots you must change the default settings. 
Details:
-journalctl settings are in /etc/systemd/journald.conf.
-to keep logs across boots setting "Storage=auto" needs to be "Storage=persistent"
-I created a modified journald.conf in /etc/systemd/journald.conf.d/

I think the default should be to keep these logs. I considered opening a launchpad bug against systemd but this is a feature request not a true bug and support is aware of this default.

Is it possible to have pm-suspend.log work under systemd?

you can also create /var/log/journal/ to store persistent data, without tweaking the conf file.

---

