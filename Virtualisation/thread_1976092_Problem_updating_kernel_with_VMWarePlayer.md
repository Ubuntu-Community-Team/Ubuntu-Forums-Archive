---
title: "Problem updating kernel with VMWarePlayer"
date: 2012-05-08
forum: Virtualisation
---

### Post by neorich2002 on 2012-05-08
Dear All, 

Having recently upgraded (via total wipe and fresh install) to Ubuntu 12.04, from 11.10 I tried to install and run VMWarePlayer

The install works fine, but on starting the player, I receive the following message:

```

_VMWare Kernel Module Updator_
Before you can run VMWare, several modules must be compiled and loaded into the running kernel.

```

I click "Install" and the the install fails on the Virtual Network Device part.

See attached screen captures and log file.

Having looked in the log file I suspected an issue with the linux headers and tried to install the latest package, but apparently I already have it installed.

If anyone has any thoughts on what's happening here it would be much appreciated.

Thanks

Regards

neorich2002

---

### Post by smurphy on 2012-05-08
I had the same issues in the past, and had decided after that to use virtualbox. Does the same, and runs the OS's out of VMware images fine.

Sorry I can't help with the vmware part.

---

### Post by SlugSlug on 2012-05-08
This fixed my vm workstation

[http://weltall.heliohost.org/wordpress/2012/01/26/vmware-workstation-8-0-2-player-4-0-2-fix-for-linux-kernel-3-2-and-3-3/](http://weltall.heliohost.org/wordpress/2012/01/26/vmware-workstation-8-0-2-player-4-0-2-fix-for-linux-kernel-3-2-and-3-3/)

may help for vmwareplayer ?

---

### Post by sisco311 on 2012-05-08
Thread moved to **Virtualization** forum.

---

### Post by traditionalist on 2012-05-08
This fixed mine;

[http://ubuntuforums.org/showthread.php?t=1953805](http://ubuntuforums.org/showthread.php?t=1953805)

Regards...Trad

---

### Post by neorich2002 on 2012-05-10
Thanks a lot, the details on that thread fixed my problem.

Regards

neorich2002

---

