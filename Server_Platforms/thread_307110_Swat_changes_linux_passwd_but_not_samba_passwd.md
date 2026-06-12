---
title: "Swat changes linux passwd but not samba passwd"
date: 2006-11-26
forum: Server Platforms
---

### Post by peter@kkvs on 2006-11-26
Samba does not use PAM to authenticate passwds but SWAT does. My problem is that swat changes the linux password and not the samba one.
In smb.conf the passwd backend = tdbsam

Obviously PAM is not reading the tdbsam.
In other distros there is a module _pam_smbpass.so_ called in pam.d/login which tells PAM where to find the samba passwds according to the smb.conf.

Unfortunately in Ubuntu distro this is absent.

So how do I tell pam to look at and make changes to the tdbsam backend rather than to the linux.

---

