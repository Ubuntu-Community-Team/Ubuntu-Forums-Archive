---
title: "Access permissions to TrueCrypt mount for non-admin users"
date: 2014-01-31
forum: Security
---

### Post by Alex_K. on 2014-01-31
I've installed TrueCrypt on my system (by downloading .deb file and installing it). By itself, TrueCrypt works perfectly, I even share/mount/use TrueCrypt volumes from windows partitions.  But, I've noticed a strange problem – only the administrator user have access to /media/truecryptX (which is where truecrypt mounts). Indeed, the permissions indicates only root access and none for group and none for user. But – I cannot change those permissions, for some reason.  Say I run: sudo chmod 777 /media/truecryptX and than : ls -l /media/truecryptX  And still, only root have access to this folder.  What I'm missing?

---

### Post by Dave_L on 2014-01-31
From my notes for Truecrypt 7.1a.  Replace USER with your actual username.

To allow mounting a truecrypt volume by non-root users, added the user group 'truecrypt', added the user 'USER' to that group and added the following to /etc/sudoers via visudo:
```
# Users in the truecrypt group are allowed to run TrueCrypt as root.
%truecrypt ALL=(root) NOPASSWD:/usr/bin/truecrypt
```
I had to log out/in before the change took effect.

---

### Post by Alex_K. on 2014-02-01
Thank you.  Worked like a charm.

---

