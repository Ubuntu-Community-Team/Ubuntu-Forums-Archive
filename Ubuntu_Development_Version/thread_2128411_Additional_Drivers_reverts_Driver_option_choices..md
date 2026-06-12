---
title: "Additional Drivers reverts Driver option choices."
date: 2013-03-23
forum: Ubuntu Development Version
---

### Post by RJ12 on 2013-03-23
Hello!
An unexpected behavior seems to be popping up while trying to enable restricted drivers for my wireless card.. I go into settings, software & updates and choose Additional Drivers. I find the driver I want (the only one there actually :P) and check it and click Apply. I get prompted for authentication and authenticate as usual. At this point it seems to be trying to enable it (It starts saying "Applying Changes" with the progress bar) and then quickly stops with the driver option set back to "Do not use this device".

I find it weird that this is happening because it worked perfectly fine while using the LiveCD to install.. 


Any ideas?

---

### Post by dino99 on 2013-03-23
needs to be reported on launchpad

---

### Post by RJ12 on 2013-03-23
> **dino99 said:**
> needs to be reported on launchpad

You're right... I must be tired or something because I also figured out what was causing the issue.
Where would Ubuntu get these packages from? I plugged my LiveUSB back in and installed the driver manually and everything worked out. ^_^ I guess I should go to sleep..

---

