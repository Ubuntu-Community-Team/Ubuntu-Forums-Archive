---
title: "Shutdown button (Dell Poweredge)"
date: 2011-08-20
forum: Server Platforms
---

### Post by bbqroast on 2011-08-20
I am running Natty (server) on a Dell Power edge T110 I normally  shutdown the rest of my computers before realizing it is still running.
Sadly the power button does not shutdown the computer and I have to kill  the power or reboot windows (you have no idea how long that takes).
The same goes for shutdowns when I do remember to do a proper shutdown.  The Poweredge keeps running after its been turned off (I guess I can  safely kill the power then).

---

### Post by Basher101 on 2011-08-20
i somehow missed your point here...your server is natty? then why do you have to > I have to kill the power or reboot windows

---

### Post by bbqroast on 2011-08-21
I run Windows on my school laptop which I use to control my server, as I normally can't hear my poweredge over my laptops cooling fans (running word puts windows into critical temps) I only realize its running till I shut it down.

---

### Post by SecretCode on 2011-08-21
Why - and how often - do you have to shut it down? I expect servers to stay running.

Will the box switch off fully if you
```
sudo shutdown -P now
```
from an ssh session? Or direct console if you have one attached?

Do you have acpid installed, and what are the contents of _/etc/acpi/powerbtn.sh_?

---

