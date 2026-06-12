---
title: "[SOLVED] su not working"
date: 2007-11-19
forum: Server Platforms
---

### Post by mouseboyx on 2007-11-19
su does not work with my password
i installed a server edition, and my default account is not in the sudoers file, how stupid is this?
i cannot login to root with the password of the default acount  or these:
root
ubuntu
sudo
su
How do i login to root? is there some specail password for su? or sudo

---

### Post by SgtDude on 2007-11-19
*su* won't work because it require's **root**'s password, and by default, the **root** account is disabled.

Your solution is *sudo*.  *sudo* requires the user's password, so whatever password you used to log in, you'll use when *sudo* asks you for a password.

Please post a reply if this doesn't work.

hint:  If you really want to log in as root, use *sudo su*.

---

### Post by mouseboyx on 2007-11-19
[http://www.ubuntugeek.com/how-to-recover-password-under-ubuntu.html](http://www.ubuntugeek.com/how-to-recover-password-under-ubuntu.html)

---

### Post by aysiu on 2007-11-19
SgtDude is right.

Further reading here:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

