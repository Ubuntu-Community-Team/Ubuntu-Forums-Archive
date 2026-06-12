---
title: "Fix or refresh apparmor profiles?"
date: 2019-11-07
forum: Security
---

### Post by Dáire Fagan on 2019-11-07
I only became aware of apparmor as I was following this guide to move the location of my mysql dir:

[How To Move a MySQL Data Directory to a New Location on Ubuntu 18.04]("https://www.digitalocean.com/community/tutorials/how-to-move-a-mysql-data-directory-to-a-new-location-on-ubuntu-18-04")

After creating the alias in */etc/apparmor.d/tunables/alias*, and trying:

 ```
sudo systemctl restart apparmor
```

I receive the error:

```
Job for apparmor.service failed because the control process exited with error code.See "systemctl status apparmor.service" and "journalctl -xe" for details.
```

```
runswithascript@apparatus:~$ systemctl status apparmor.service
&#9679; apparmor.service - AppArmor initialization
   Loaded: loaded (/lib/systemd/system/apparmor.service; enabled; vendor preset: enabled)
   Active: failed (Result: exit-code) since Thu 2019-11-07 09:06:04 GMT; 5min ago
     Docs: man:apparmor(7)
           http://wiki.apparmor.net/
  Process: 4539 ExecStart=/etc/init.d/apparmor start (code=exited, status=123)
 Main PID: 4539 (code=exited, status=123)


Nov 07 09:06:04 apparatus apparmor[4539]: Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
Nov 07 09:06:04 apparatus apparmor[4539]: AppArmor parser error for /etc/apparmor.d/usr.lib.dovecot.auth in /etc/apparmor.d/usr.lib.dovecot.auth at line 18: Could not open 'abstractions/mysql'
Nov 07 09:06:04 apparatus apparmor[4539]: AppArmor parser error for /etc/apparmor.d/usr.lib.dovecot.dict in /etc/apparmor.d/usr.lib.dovecot.dict at line 16: Could not open 'abstractions/mysql'
Nov 07 09:06:04 apparatus apparmor[4539]: AppArmor parser error for /etc/apparmor.d/usr.sbin.dovecot in /etc/apparmor.d/usr.sbin.dovecot at line 19: Could not open 'abstractions/mysql'
Nov 07 09:06:04 apparatus apparmor[4539]: AppArmor parser error for /etc/apparmor.d/usr.sbin.mysqld in /etc/apparmor.d/usr.sbin.mysqld at line 9: Could not open 'abstractions/mysql'
Nov 07 09:06:04 apparatus apparmor[4539]: Skipping profile in /etc/apparmor.d/disable: usr.sbin.rsyslogd
Nov 07 09:06:04 apparatus apparmor[4539]:    ...fail!
Nov 07 09:06:04 apparatus systemd[1]: apparmor.service: Main process exited, code=exited, status=123/n/a
Nov 07 09:06:04 apparatus systemd[1]: apparmor.service: Failed with result 'exit-code'.
Nov 07 09:06:04 apparatus systemd[1]: Failed to start AppArmor initialization.
```

[Pastebin of ]("https://paste.ubuntu.com/p/Y8RsdRFXs7/")[I][journalctl -xe]("https://paste.ubuntu.com/p/Y8RsdRFXs7/")

[/I]```

runswithascript@apparatus:~$ sudo journalctl -u apparmor
Nov 07 09:06:04 apparatus systemd[1]: Starting AppArmor initialization...
Nov 07 09:06:04 apparatus apparmor[4539]:  * Starting AppArmor profiles
Nov 07 09:06:04 apparatus apparmor[4539]: AppArmor parser error for /etc/apparmor.d/sbin.syslog-ng in /etc/apparmor.d/sbin.syslog-ng at line 22: Could not open 'abstractions/mysql'
Nov 07 09:06:04 apparatus apparmor[4539]: Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
Nov 07 09:06:04 apparatus apparmor[4539]: AppArmor parser error for /etc/apparmor.d/usr.lib.dovecot.auth in /etc/apparmor.d/usr.lib.dovecot.auth at line 18: Could not open 'abstractions/mysql'
Nov 07 09:06:04 apparatus apparmor[4539]: AppArmor parser error for /etc/apparmor.d/usr.lib.dovecot.dict in /etc/apparmor.d/usr.lib.dovecot.dict at line 16: Could not open 'abstractions/mysql'
Nov 07 09:06:04 apparatus apparmor[4539]: AppArmor parser error for /etc/apparmor.d/usr.sbin.dovecot in /etc/apparmor.d/usr.sbin.dovecot at line 19: Could not open 'abstractions/mysql'
Nov 07 09:06:04 apparatus apparmor[4539]: Skipping profile in /etc/apparmor.d/disable: usr.sbin.rsyslogd
Nov 07 09:06:04 apparatus apparmor[4539]: AppArmor parser error for /etc/apparmor.d/usr.sbin.mysqld in /etc/apparmor.d/usr.sbin.mysqld at line 9: Could not open 'abstractions/mysql'
Nov 07 09:06:04 apparatus apparmor[4539]: AppArmor parser error for /etc/apparmor.d/sbin.syslog-ng in /etc/apparmor.d/sbin.syslog-ng at line 22: Could not open 'abstractions/mysql'
Nov 07 09:06:04 apparatus apparmor[4539]: Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
Nov 07 09:06:04 apparatus apparmor[4539]: AppArmor parser error for /etc/apparmor.d/usr.lib.dovecot.auth in /etc/apparmor.d/usr.lib.dovecot.auth at line 18: Could not open 'abstractions/mysql'
Nov 07 09:06:04 apparatus apparmor[4539]: AppArmor parser error for /etc/apparmor.d/usr.lib.dovecot.dict in /etc/apparmor.d/usr.lib.dovecot.dict at line 16: Could not open 'abstractions/mysql'
Nov 07 09:06:04 apparatus apparmor[4539]: AppArmor parser error for /etc/apparmor.d/usr.sbin.dovecot in /etc/apparmor.d/usr.sbin.dovecot at line 19: Could not open 'abstractions/mysql'
Nov 07 09:06:04 apparatus apparmor[4539]: AppArmor parser error for /etc/apparmor.d/usr.sbin.mysqld in /etc/apparmor.d/usr.sbin.mysqld at line 9: Could not open 'abstractions/mysql'
Nov 07 09:06:04 apparatus apparmor[4539]: Skipping profile in /etc/apparmor.d/disable: usr.sbin.rsyslogd
Nov 07 09:06:04 apparatus apparmor[4539]:    ...fail!
Nov 07 09:06:04 apparatus systemd[1]: apparmor.service: Main process exited, code=exited, status=123/n/a
Nov 07 09:06:04 apparatus systemd[1]: apparmor.service: Failed with result 'exit-code'.
Nov 07 09:06:04 apparatus systemd[1]: Failed to start AppArmor initialization.

```

From what I have read, the issue appears to be with a firefox and rsyslogd? I assume that the references to mysql were because I was unable to restart apparmor and complete the guide I was following, but that once the underlaying issues are resolved everything will be okay with mysql. I followed the same guide also on my desktop, which also runs 18.04, and apparmor restarted fine. I do not remember ever using apparmor before or configuring profiles, I actually stopped using Firefox several years ago, and I am not sure I ever even opened it on this install.

Is there a way to delete the offending profiles, or regenerate them please?

---

### Post by bernard010 on 2019-12-21
Ubuntu Documentation for AppArmor       [https://help.ubuntu.com/lts/serverguide/apparmor.html](https://help.ubuntu.com/lts/serverguide/apparmor.html)

                                                           [https://help.ubuntu.com/community/AppArmor](https://help.ubuntu.com/community/AppArmor)


This May help with changing or updating profiles for AppArmor  [https://askubuntu.com/questions/236381/what-is-apparmor](https://askubuntu.com/questions/236381/what-is-apparmor)

List of all of AppArmor Profiles    [https://wiki.ubuntu.com/SecurityTeam/KnowledgeBase/AppArmorProfiles](https://wiki.ubuntu.com/SecurityTeam/KnowledgeBase/AppArmorProfiles)

I hope this is some help.

---

