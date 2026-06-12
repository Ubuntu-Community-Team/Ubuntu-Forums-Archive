---
title: "Virtualbox err NS_ERROR_FAILURE (0x00004005)"
date: 2012-01-09
forum: Virtualisation
---

### Post by andy007007 on 2012-01-09
**I tried to solve this metod:**
*PresenceJune 26th, 2011, 09:12 PM*

[I]Here's how to get it working:
First thing you need to do is find out the id of the 'vboxusers' group. So:
grep vboxusers /etc/group
This will show something similar to vboxusers:x:XXX: where the XXX is the id of the group.
Now add this to /etc/fstab:
[COLOR=Red]none[/COLOR] /proc/bus/usb usbfs devgid=XXX,devmode=664,nodev,noexec,nosuid 0 0
Where the XXX is the id that you just found above.
The last thing to do is to add your user to the vboxusers group:
sudo usermod -a -G vboxusers user
Where user is your username.[/I]

**from here:**
[http://ubuntuforums.org/archive/index.php/t-918007.html](http://ubuntuforums.org/archive/index.php/t-918007.html)
**But ubuntu11.10 have not command** [COLOR=Red]none[/COLOR].

---

### Post by b0b138 on 2012-01-09
You don't need that line. Those are old directions for an older version of VB.

---

