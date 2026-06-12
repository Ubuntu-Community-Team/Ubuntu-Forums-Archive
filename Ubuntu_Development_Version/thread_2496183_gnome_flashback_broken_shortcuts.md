---
title: "gnome flashback broken shortcuts"
date: 2024-03-17
forum: Ubuntu Development Version
---

### Post by Claus7 on 2024-03-17
Hello,

the following shortcuts from Indicator applet complete are broken:
Time & Date Settings
About This Computer
System Settings...

instead they are pointing to the last option chosen under settings. It is understandable though, since many changes took place under settings.

Regards!

---

### Post by jbicha on 2024-03-17
Please file a bug. But not many people are maintaining GNOME Flashback now so it could take a while for it to get fixed.

It might be interesting to see if any Ubuntu desktop flavors are also affected like Unity or MATE or Xubuntu.

---

### Post by Claus7 on 2024-03-17
Hello,

> **jbicha said:**
> Please file a bug. But not many people are maintaining GNOME Flashback now so it could take a while for it to get fixed.

It might be interesting to see if any Ubuntu desktop flavors are also affected like Unity or MATE or Xubuntu.

since you are aware about flashback, do you have any idea what will happen to it, when wayland will be the default everywhere? Will it have a future or it is time to say farewell?

I will, and I will post the link here.

Regards!

---

### Post by jbicha on 2024-03-17
I expect it will be possible to run certain X sessions for quite a while. At some point, it might not be possible to use GDM and gnome-session to log into those sessions but maybe you could use lightdm and whatever session helper is used by other old desktops and window managers.

---

### Post by Claus7 on 2024-03-17
Hello,

> **jbicha said:**
> I expect it will be possible to run certain X sessions for quite a while. At some point, it might not be possible to use GDM and gnome-session to log into those sessions but maybe you could use lightdm and whatever session helper is used by other old desktops and window managers.

thank you for your input.

Regards!

---

### Post by Claus7 on 2024-03-18
Hello,

the link of the bug report:
[https://bugs.launchpad.net/ubuntu/+source/indicator-applet/+bug/2058239](https://bugs.launchpad.net/ubuntu/+source/indicator-applet/+bug/2058239)

Regards!

---

### Post by Claus7 on 2024-04-08
Hello,

checking back again things are working nicely.

Regards!

---

### Post by cscj01 on 2024-09-02
Just as a point of interest, how did you get to sign in to a gnome-flashback session after upgrade.  I can get into a Gnome session but cannot get into a Flashback session.  When I try to enter the Flashback session, the screen returns to the login screen as if I had done nothing at all.  I would really like to get in, but am at a loss on how to approach this issue.  Thanks for any ideas you may have.

---

### Post by Claus7 on 2024-09-03
Hello,

I had come across login loop ~ 6 years ago. I will provide some links that might be helpful to you as well. The problem arose after an upgrade as well. I remember that I had to get rid of a specific package, which you will find in the links provided.

1) click again while trying to login
[https://ubuntuforums.org/showthread.php?t=2467441&highlight=loop](https://ubuntuforums.org/showthread.php?t=2467441&highlight=loop)

2) create another user and see if problem persists
[https://ubuntuforums.org/showthread.php?t=2401584&page=2&highlight=loop](https://ubuntuforums.org/showthread.php?t=2401584&page=2&highlight=loop)

3) indicator multiload
[https://ubuntuforums.org/showthread.php?t=2398232&highlight=loop](https://ubuntuforums.org/showthread.php?t=2398232&highlight=loop)

4) upstart package
[https://ubuntuforums.org/showthread.php?t=2384556&page=2&highlight=loop](https://ubuntuforums.org/showthread.php?t=2384556&page=2&highlight=loop)

5) various
[https://ubuntuforums.org/showthread.php?t=2390722&highlight=loop](https://ubuntuforums.org/showthread.php?t=2390722&highlight=loop)

Regards!

---

