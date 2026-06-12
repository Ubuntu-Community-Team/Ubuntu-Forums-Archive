---
title: "Problem with Samba"
date: 2011-08-26
forum: Server Platforms
---

### Post by stamatiou on 2011-08-26
Hey guys,
I have Ubuntu 11.04 and I installed the package samba4 but whenever I run samba it shows me:
```
Unknown parameter encountered: "max log size"
Ignoring unknown parameter "max log size"
Unknown parameter encountered: "syslog"
Ignoring unknown parameter "syslog"
Unknown parameter encountered: "passdb backend"
Ignoring unknown parameter "passdb backend"
Unknown parameter encountered: "unix password sync"
Ignoring unknown parameter "unix password sync"
Unknown parameter encountered: "passwd program"
Ignoring unknown parameter "passwd program"
Unknown parameter encountered: "pam password change"
Ignoring unknown parameter "pam password change"
Unknown parameter encountered: "map to guest"
Ignoring unknown parameter "map to guest"
Unknown parameter encountered: "usershare allow guests"
Ignoring unknown parameter "usershare allow guests"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
[Fri Aug 26 12:32:56 2011 EEST, 0 ../smbd/server.c:367:binary_smbd_main()]
samba version 4.0.0alpha15-UNKNOWN started.
Copyright Andrew Tridgell and the Samba Team 1992-2011

```Also when I tried to create a user with:
```
sudo smbpasswd -a username
```it tells me:
```
Failed to add entry for user username.
```Also I have not edited the smb.conf at all!

---

### Post by e79 on 2011-08-26
> samba version 4.0.0alpha15-UNKNOWN startedYou seem to have installed the wrong version of Samba which is still under development.

[https://bugs.launchpad.net/ubuntu/+source/samba4/+bug/792189](https://bugs.launchpad.net/ubuntu/+source/samba4/+bug/792189)

Id suggest you to start over again :

```
sudo apt-get remove --purge samba4
```

```
sudo apt-get install samba
```Hope this helps

---

