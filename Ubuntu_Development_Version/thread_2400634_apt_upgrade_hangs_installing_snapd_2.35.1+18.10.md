---
title: "apt upgrade hangs installing snapd 2.35.1+18.10"
date: 2018-09-08
forum: Ubuntu Development Version
---

### Post by corradoventu on 2018-09-08
installing maint on a fresh installed ubuntu 18.10 apt upgrade hangs installing snapd 2.35.1+18.10

Preparing to unpack .../snapd_2.35.1+18.10_amd64.deb ...
Unpacking snapd (2.35.1+18.10) over (2.35+18.10) ...
Setting up snapd (2.35.1+18.10) ...
Installing new version of config file /etc/apparmor.d/usr.lib.snapd.snap-confine.real ...
snapd.failure.service is a disabled or a static unit, not starting it.
snapd.snap-repair.service is a disabled or a static unit, not starting it.
Progress: [ 67%] [#################################################################.................................]

apt hangs forever...

[https://bugs.launchpad.net/ubuntu/+source/snapd/+bug/1791087](https://bugs.launchpad.net/ubuntu/+source/snapd/+bug/1791087)

---

### Post by P-I H on 2018-09-08
I installed  today's(8/9) ISO and upgraded, which worked OK. However I suppose that's only because there was no update or install of snapd. I installed the ISO from about a week back and had problems with upgrades and snapd.
The old problem with gnome-calculator still exist.
```
p-i@pi-GA-990FXA-UD3:~$ snap changes
ID   Status  Spawn                Ready                Summary
1    Doing   today at 16:09 CEST  -                    Initialize system state
2    Done    today at 16:09 CEST  today at 16:09 CEST  Initialize device
```
Initialize system state is hanging.

Added a comment in bug report
[https://bugs.launchpad.net/ubuntu/+source/ubuntu-meta/+bug/1772844](https://bugs.launchpad.net/ubuntu/+source/ubuntu-meta/+bug/1772844)

---

### Post by cariboo on 2018-09-08
See bug # [lpbug]1776622[/lpbug].

---

### Post by corradoventu on 2018-09-15
for me problem solved by last upgrade
> Preparing to unpack .../11-snapd_2.35.2+18.10_amd64.deb ...
Unpacking snapd (2.35.2+18.10) over (2.35.1+18.10) ...

---

### Post by P-I H on 2018-09-15
In my case too.
```
Start-Date: 2018-09-14  07:35:29
Commandline: aptdaemon role='role-commit-packages' sender=':1.336'
Upgrade: snapd:amd64 (2.35.1+18.10, 2.35.2+18.10)
End-Date: 2018-09-14  07:35:34
```

---

### Post by corradoventu on 2018-09-16
but related bugs are not declared closed?

---

