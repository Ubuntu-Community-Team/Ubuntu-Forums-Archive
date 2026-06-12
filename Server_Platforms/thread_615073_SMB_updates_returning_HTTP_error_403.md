---
title: "SMB updates returning HTTP error 403"
date: 2007-11-16
forum: Server Platforms
---

### Post by epee on 2007-11-16
I've got 6 updates 'ready' but when I try to install them I get messages like:
> W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/samba/winbind_3.0.26a-1ubuntu2.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/s/samba/winbind_3.0.26a-1ubuntu2.1_amd64.deb)
  403 Forbidden
Anyone got any idea what's going on here? :confused:

---

### Post by bash.gordon on 2007-11-16
> **epee said:**
> I've got 6 updates 'ready' but when I try to install them I get messages like:

Anyone got any idea what's going on here? :confused:
Lucky you ;)
Have a look at this thread
[http://ubuntuforums.org/showthread.php?t=614558](http://ubuntuforums.org/showthread.php?t=614558),
be happy you don't have to downgrade, and wait for fixed updates...

Regards,
Andreas

---

### Post by netlogic on 2007-11-16
some partial solutions
go here for now
[http://ubuntuforums.org/showthread.php?t=614558](http://ubuntuforums.org/showthread.php?t=614558)

your best bet is mark samba and other samba related packages as not upgradeable in synaptic or aptitude and upgrade the rest. samba is having problems.  there are few different steps covered on the thread.

---

