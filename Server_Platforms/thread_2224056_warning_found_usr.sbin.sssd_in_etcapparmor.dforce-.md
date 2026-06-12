---
title: "warning: found usr.sbin.sssd in /etc/apparmor.d/force-complain"
date: 2014-05-14
forum: Server Platforms
---

### Post by richard51 on 2014-05-14
I receive this message when booting my server: **warning: found usr.sbin.sssd in /etc/apparmor.d/force-complain**

There appears to be a symlink in the **/etc/apparmor.d/force-complain** folder that references **/etc/apparmor.d/usr.sbin.sssd**. Is it safe to remove the symlink from the **force-complain** folder? And why does the **sssd** installation put it there in the first place?

**Additional**: I also receive this message when booting my server: **skipped profile in /etc/apparmor.d/disabled/usr.sbin.rsyslogd**. This is a symlink referencing **/etc/apparmor.d/usr.sbin.rsyslogd**. I have only recently noticed these messages after installing **sssd** (which seems to be working fine).

---

