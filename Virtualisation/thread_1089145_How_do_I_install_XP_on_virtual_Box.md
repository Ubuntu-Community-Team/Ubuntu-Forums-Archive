---
title: "How do I install XP on virtual Box"
date: 2009-03-06
forum: Virtualisation
---

### Post by pri.julien on 2009-03-06
IDK, I followed the walkthrough instructions but when I tried to fire it up, it displayed a message stating that I was missing a VERR_VM_DRIVER and the run '/etc/init.d/vboxdrv setup' although when I did attempt it, it refused to run. Maybe I did something wrong but is there any way to run Windows XP within Kubuntu without using wine.

---

### Post by Joeb454 on 2009-03-06
Moved to Virtualization :)

Try running ```
sudo /etc/init.d/vboxdrv setup
``` And it should work :)

---

