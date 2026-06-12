---
title: "Root password"
date: 2009-01-29
forum: Security
---

### Post by oldcelt on 2009-01-29
OK, I've installed Ubuntu 8.1 but it's set up the Home folder as the property of 'root'.  I'm getting startup error messages and I can't do anything about the problem because it says Home isn't owned by me.

This is the message:-

Users $HOME/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. Users $HOME directory must be owned by user and not writeable by others.
-------------------------------------------------------

Since I didn't set it up on installation there must be a default password for 'root'.  How do I find it please?

Ken

---

### Post by sisco311 on 2009-01-29
This should help you: [http://ubuntuforums.org/showthread.php?t=976610]("http://ubuntuforums.org/showthread.php?t=976610")


[uhelp]community/RootSudo[/uhelp]

The root account is disabled by default.
You can use sudo to run a command as root:
```
sudo command
```It will ask for your user password. Only users in the admin group can use sudo. The first user created on the system is in the admin group.

---

### Post by oldcelt on 2009-01-29
Thanks a million.  Worked perfectly.

Ken  :D

---

