---
title: "disable root help"
date: 2009-03-13
forum: Security
---

### Post by cbf305 on 2009-03-13
We had a server hacked and I, being used to running Debian servers, did a passwd root and changed the root password.  Only after that I remembered that it was an Ubuntu server, and Ubuntu does something special with the root password so it can't be used.  I disabled the root account with passwd -l root, but when I sudo I get a stupid account is disabled error message.  I re-enabled root and I gave it a crazy long random password, but is there a way to set it back to the "special" no possible encrypted value password that the installer gives it as described on this page?

[https://help.ubuntu.com/8.04/serverguide/C/user-management.html](https://help.ubuntu.com/8.04/serverguide/C/user-management.html)

It's 8.10 server.

Thanks!

---

### Post by bodhi.zazen on 2009-03-13
Actually this is a bug in both Debian and Ubuntu :twisted:

This comes up most often on , well servers ;)

To disable (lock) the root account :

```
sudo usermod --lock root
```

I am sorry, I no longer have the link to the original bug report in either Debian or Ubuntu, it is an old bug.

---

### Post by cbf305 on 2009-03-13
Thank you that worked perfectly. :D

---

### Post by hyper_ch on 2009-03-13
if the server was hacked then you need to re-set it up.

---

