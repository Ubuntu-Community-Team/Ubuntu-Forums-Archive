---
title: "not being prompted for password but getting authentication is required error message"
date: 2009-12-11
forum: Security
---

### Post by dgmahesh on 2009-12-11
hi. ubuntu karmic user here.
i tried to edit sudoers to avoid password prompts but reverted the changes. later after restart it was prompting for password during login indefinitely( though i enabled automatic login). then i logged in using failsafe mode. everything has been working fine but while mounting windows drive, i'm getting an error " authentication is required" and i'm not able to change even the system date and time. later i restarted many times it is taking me to the desktop without showing login screen. so i'm not sure whether i'm in failsafe mode or not. please help me out

---

### Post by dgmahesh on 2009-12-12
Hi all.... fixed it by myself. Actually it was into fail safe mode. So I assigned password to root. 
Signed in as root.  Then System > Administration > Users and groups > Manage groups and added my user name to my group. It started working fine. Now I'm working in normal(GNOME) mode.

---

