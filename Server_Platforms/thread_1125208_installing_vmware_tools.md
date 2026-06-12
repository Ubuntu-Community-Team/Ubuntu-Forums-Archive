---
title: "installing vmware tools"
date: 2009-04-14
forum: Server Platforms
---

### Post by dustervoice on 2009-04-14
ive downloaded rpm and attempting to install vmware tools on my server but im receiving the following error. what does this mean?

error: Failed dependencies:
        /bin/sh is needed by VMwareTools-7428-126130.i386

---

### Post by HermanAB on 2009-04-14
Install binutils.

---

### Post by apel_2804 on 2009-04-14
or install open virtual maschine tools:

apt-get update
apt-get install module-assistant
apt-get install open-vm-source
module-assistant prepare open-vm
module-assistant auto-install open-vm

---

