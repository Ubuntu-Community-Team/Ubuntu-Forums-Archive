---
title: "usr.sbin.sssd Caching disabled"
date: 2022-06-20
forum: Ubuntu Development Version
---

### Post by osse7 on 2022-06-20
Just getting that warning while upgrading apparmor:

Reloading AppArmor profiles 
Skipping profile in /etc/apparmor.d/disable: usr.sbin.rsyslogd
Warning: found usr.sbin.sssd in /etc/apparmor.d/force-complain, forcing complain mode
Warning from /etc/apparmor.d (/etc/apparmor.d/usr.sbin.sssd line 60): Caching disabled for: 'usr.sbin.sssd' due to force complain

Do i need to report it ?

(kinetic Mate )

---

### Post by #&amp;thj^% on 2022-06-20
Sounds like it's already reported: [https://bugs.launchpad.net/ubuntu/+source/apparmor/+bug/1899218](https://bugs.launchpad.net/ubuntu/+source/apparmor/+bug/1899218)
If your brave you disable it, I found it generates far to many logs>>>apparmor notices
Turn it off

```
sudo ln -sf /etc/apparmor.d/usr.sbin.sssd /etc/apparmor.d/disable/
sudo apparmor_parser -R /etc/apparmor.d/usr.sbin.sssd
```

Turn it back on

```
sudo unlink /etc/apparmor.d/disable/usr.sbin.sssd
sudo apparmor_parser -r /etc/apparmor.d/usr.sbin.sssd
sudo aa-status # to verify visually
```
This bug just keeps on popping up. ;)

---

