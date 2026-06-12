---
title: "Failed to Load Kernel Modules"
date: 2018-03-25
forum: Virtualisation
---

### Post by rizzle2 on 2018-03-25
Hi guys, 

I have been attempting to install a different version of virtual box.
 I booted as normal, added Oracle PPA, installed and then removed a virtual box install using "apt autoremove --purge"

Now when I boot I get this:
[IMG]https://ibb.co/imDpN7[/IMG]

Upon running "systemctl status systemd-modules-load.service" I get this:
[IMG]https://ibb.co/mKBXaS[/IMG]

Any ideas?
Cheers,
Rizzle

---

### Post by wildmanne39 on 2018-03-25
*Thread moved to **Virtualisation, a more appropriate forum**.*

---

### Post by cruzer001 on 2018-03-25
You must first remove vBox then install your new version.  So try removing the current install, then reinstall.

Your guest installs are located in you home directory, do not remove them.

---

