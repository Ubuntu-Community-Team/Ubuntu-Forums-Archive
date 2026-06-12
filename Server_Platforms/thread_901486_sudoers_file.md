---
title: "sudoers file"
date: 2008-08-26
forum: Server Platforms
---

### Post by Xen0n on 2008-08-26
Hello, i got a little problem here. i was trying to install an FTP server, wich went very wrong, in the guide it said **usermod -G ftpuser USER** and now, when i do a sudo command it says **USER is not in the sudoers file.  This incident will be reported.** whenever i try to write **su - root** it asks for a password but i don't have one, for root user. so, is there any solution to this problem? other then reinstalling everything?

Thanks in advance

---

### Post by kellemes on 2008-08-26
Try the following to fix sudo..

Reboot your computer. At the bootloader-menu, select the Ubuntu recovery mode.

You'll be getting to console. You need to add yourself to the admin group.

```
usermod -a -G admin yourusername
```
(obviously fill in your real login/username)

Reboot computer and see if it works..

By the way, if you need persistant root-privileges from terminal you can enter..
```
sudo -i
```

This instead of "su".

---

### Post by Xen0n on 2008-08-26
> **kellemes said:**
> Try the following to fix sudo..

Reboot your computer. At the bootloader-menu, select the Ubuntu recovery mode.

You'll be getting to console. You need to add yourself to the admin group.

```
usermod -a -G admin yourusername
```
(obviously fill in your real login/username)

Reboot computer and see if it works..

By the way, if you need persistant root-privileges from terminal you can enter..
```
sudo -i
```

This instead of "su".

Thank you for the reply, that solved the problem. :D

---

