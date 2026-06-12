---
title: "sudo doesn't require password with ldap"
date: 2006-08-15
forum: Server Platforms
---

### Post by mwge on 2006-08-15
I have set up libpam-ldap and libnss-ldap to talk to edirectory.
I can log in correctly and use getent to list ldap groups and users.
I then modified sudoers (using visudo) to allow members of an ldap group to use sudo.

All this works as expected on the console, however when I log in using ssh sudo doesn't request a password. If I login using SSH as a local user in the admin group sudo does request a password.

Any help much appreciated.

---

### Post by LordHunter317 on 2006-08-15
Posting sudo's PAM config would be helpful.  Make sure to get any included files.

Did you verify that the paswords are being properly read from eDirectory and included in /etc/shadow (getent shadow)?  If it fails to read them, libnss-ldap will leave blank entries in /etc/shadow.

You may want to remove it from the shadow NSS Entry all together.  That's what I've done on my AD-joined boxes.

---

