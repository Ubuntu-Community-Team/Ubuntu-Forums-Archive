---
title: "Apparmor profile for lightdm-guest-session does not seem to work"
date: 2014-06-05
forum: Security
---

### Post by Hungry Man on 2014-06-05
I've tried removing literally all capabilities in the lightdm-guest-session profile and I can still log in, launch applications, etc.Does this profile really do nothing?I'm looking to restrict this guest session considerably.

---

### Post by bapoumba on 2014-06-06
Although the info is for older Ubuntu releases, it's been edited recently so I guess it is still relevant.
[https://help.ubuntu.com/community/CustomizeGuestSession](https://help.ubuntu.com/community/CustomizeGuestSession)

I have found this one, so I guess you are more aware than I am about the apparmor stuff : [http://ubuntuforums.org/showthread.php?t=1969814](http://ubuntuforums.org/showthread.php?t=1969814)
Getting the ball rolling here, and bumping your thread :)

Do you mean that /etc/apparmor.d/abstractions/lightdm is not taken into account ? [https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/1243339](https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/1243339)

Other info :
[http://ubuntuforums.org/showthread.php?t=2205637](http://ubuntuforums.org/showthread.php?t=2205637)
[https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/1289731](https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/1289731)
[https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/1298021](https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/1298021)
[https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/1301625](https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/1301625)

---

