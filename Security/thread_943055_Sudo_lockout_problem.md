---
title: "Sudo lockout problem"
date: 2008-10-09
forum: Security
---

### Post by croutonkid94 on 2008-10-09
I have changed my /etc/sudoers file by mistake, and now cannot run commands as root.  Is there any way I can get around this, or do I have to nuke/pave my system?

---

### Post by aysiu on 2008-10-09
This should help:
[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

---

### Post by Dr Small on 2008-10-09
> **croutonkid94 said:**
> I have changed my /etc/sudoers file by mistake, and now cannot run commands as root.  Is there any way I can get around this, or do I have to nuke/pave my system?
Reboot into Recovery Mode (from the GRUB menu).
This will log you in as root (by default), from there, you should be able to correct your mistake.

---

### Post by Ptero-4 on 2008-10-09
Boot with the "Recovery" entry in the grub menu. That give you root access.

---

