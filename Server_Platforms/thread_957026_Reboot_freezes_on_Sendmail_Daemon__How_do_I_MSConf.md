---
title: "Reboot freezes on Sendmail Daemon?  How do I MSConfig for Ubuntu?"
date: 2008-10-23
forum: Server Platforms
---

### Post by Ocelaris on 2008-10-23
I unwittingly rebooted, and my server now hangs at "enabling sendmail daemon" or "mail transport Agent" daemon. I uninstalled "apt-get remove sendmail" but still having problems! This may be basic, but how to I look at the services it is starting up and remove them? Like MSconfig for windows?

---

### Post by Ocelaris on 2008-10-23
Well, I figured out that sendmail was freezing because of some network reconfiguration which still for some reason doesn't let the server out of the local lan... but that's a battle to fight another day, once it was on dhcp instead of static, it was safe to boot up... BUT that shouldn't happen, sendmail shouldn't refuse to boot a box if it can't hit an external IP... that's bad juju.

---

### Post by promodus on 2008-10-24
msconfig for ubuntu... a candidate could be **B**oot-**U**p **M**anager

To install:
```
sudo apt-get install bum
```

To use:
```
sudo bum
```

---

