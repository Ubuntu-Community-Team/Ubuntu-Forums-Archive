---
title: "Is restart after updating necessary?"
date: 2011-04-04
forum: Security
---

### Post by Kljuka on 2011-04-04
every now and then, ubuntu update includes new image (initrd.img or something like that - a new kernel as I understood) that requires a restart of server after installation.

How safe is it not to restart (and still use old kernel) for a while (until next scheduled service in a month or two)? The computer is a server and I don't want to restart it unless there are security concerns.
Is there a page that tells you what are the changes in the new kernel? And if there are any security holes that have been patched?

I'm currently using img version 2.6.32-28-server (and there is already 2.6.32-30-server).
Thank you for your help

---

### Post by wilee-nilee on 2011-04-04
Check this out.
[http://www.ubuntugeek.com/install-ubuntu-kernel-updates-without-rebooting-using-ksplice-uptrack.html](http://www.ubuntugeek.com/install-ubuntu-kernel-updates-without-rebooting-using-ksplice-uptrack.html)

---

### Post by Kljuka on 2011-04-04
Thanks wilee-nilee, this looks great.
But is it safe? It's also in repository (apt-get install ksplice), so do I really need to create ksplice account? And is it free for Ubuntu 10.04 Server (on ther webpage free version only mentions Ubuntu Desktop)?

---

### Post by wilee-nilee on 2011-04-04
> **Kljuka said:**
> Thanks wilee-nilee, this looks great.
But is it safe? It's also in repository (apt-get install ksplice), so do I really need to create ksplice account? And is it free for Ubuntu 10.04 Server (on ther webpage free version only mentions Ubuntu Desktop)?

I'm  not sure I had it installed a while back for kicks, I don't remember signing up for anything per sey.

I just found this link as well I was wondering about the development being up to date with the releases.
[http://www.webupd8.org/2010/10/install-kernel-updates-without.html](http://www.webupd8.org/2010/10/install-kernel-updates-without.html)

I just noticed that it is in my Maverick synaptic, it may be that if all you want is the no reboot on kernel upgrades that this works, with out all the uptrack clutter.

---

### Post by wilee-nilee on 2011-04-04
I suspected you were running a server I don't think this is the utility, but you never know, others will be a better help in the server area.

---

