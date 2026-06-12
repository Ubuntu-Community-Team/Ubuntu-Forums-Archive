---
title: "systemd.sysusers.service fails - Ubuntu server 20.04"
date: 2021-01-09
forum: Server Platforms
---

### Post by holunde on 2021-01-09
I just upgrade a Ubuntu server from 18.04 LTS to 20.04.
It was almost without problems, except for one thing that puzzels me:

The service systemd.sysusers fails

I wonder if anyone has stumbled upon something similar?
Here is some info

in **syslog:** 

*Failed to start Create System Users*

**journalctl -u systemd-sysusers.service:**

[I]Jan 09 00:29:32 eserver systemd[1]: systemd-sysusers.service: Cannot add dependency job, ignoring: Unit systemd-sysusers.service is not loaded properly: Exec format error.
Jan 09 00:29:32 eserver systemd[1]: /lib/systemd/system/systemd-sysusers.service:22: Executable path is not absolute: systemd-sysusers[/I]

**systemctl status systemd-sysusers:**

[I]&#9679; systemd-sysusers.service - Create System Users
     Loaded: loaded (/lib/systemd/system/systemd-sysusers.service; static; vendor preset: enabled)
     Active: failed (Result: signal) since Sat 2021-01-09 11:38:22 CET; 4h 41min ago
       Docs: man:sysusers.d(5)
             man:systemd-sysusers.service(8)
    Process: 425 ExecStart=/bin/systemd-sysusers (code=killed, signal=SEGV)
   Main PID: 425 (code=killed, signal=SEGV)

Jan 09 11:38:22 eserver systemd[1]: Starting Create System Users...
Jan 09 11:38:22 eserver systemd[1]: systemd-sysusers.service: Main process exited, code=killed, status=11/SEGV
Jan 09 11:38:22 eserver systemd[1]: systemd-sysusers.service: Failed with result 'signal'.
Jan 09 11:38:22 eserver systemd[1]: Failed to start Create System Users.[/I]

**/lib/systemd/system/systemd-sysusers.service:**

[I][Unit]
Description=Create System Users
Documentation=man:sysusers.d(5) man:systemd-sysusers.service(8)
DefaultDependencies=no
Conflicts=shutdown.target
After=systemd-remount-fs.service
Before=sysinit.target shutdown.target systemd-update-done.service
ConditionNeedsUpdate=/etc

[Service]
Type=oneshot
RemainAfterExit=yes
ExecStart=systemd-sysusers
TimeoutSec=90s[/I]


**grpck:** 

reports no errors

[B]pwck: 
[/B]
[I]user 'lp': directory '/var/spool/lpd' does not exist
user 'news': directory '/var/spool/news' does not exist
user 'uucp': directory '/var/spool/uucp' does not exist
user 'list': directory '/var/list' does not exist
user 'irc': directory '/var/run/ircd' does not exist
user 'gnats': directory '/var/lib/gnats' does not exist
user 'nobody': directory '/nonexistent' does not exist
pwck: no changes[/I]

---

