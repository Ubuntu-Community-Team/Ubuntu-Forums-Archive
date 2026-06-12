---
title: "Change new default home directory permissions"
date: 2007-03-22
forum: Server Platforms
---

### Post by WhiteNoiseWN on 2007-03-22
I was surprised to learn that when I added user accounts the default permissions for 'other' and group were r-x.  I know I can manually chmod 0700 the home directories when i create them, but how can I change the default behavior?

I tried changing umask in /etc/login.defs, but this doesn't seem to alter the permissions for new user home directories.

I have tried googling, and searching the forums, but their was so much noise on the subject of permissions in general that I wasn't getting far.

Thanks in advance for the help.

---

### Post by Mr. C. on 2007-03-22
The /etc/login.defs file is used on login, not upon home directory creation.  The umask there allows for a default umask setting, which a user can reset as they please.

See /etc/adduser.conf instead.

MrC

---

### Post by WhiteNoiseWN on 2007-03-22
Perfect --  thank you very much!

---

