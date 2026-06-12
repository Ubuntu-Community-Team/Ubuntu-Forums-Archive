---
title: "Auto hardware detection"
date: 2008-08-12
forum: Server Platforms
---

### Post by alloydog on 2008-08-12
With the desktop version, it is possible to install Ubuntu on one PC, then move the harddrive over to another PC, with the new hardware being detected and set-up on boot.
 - I did this with an old laptop with an IDE Bus problem, it could not boot from CDROM (it is supposed to, but I was resurrecting a thrown away laptop).

Anyway, can this be done with the server edition?
I am installing a content management system on a spare laptop running Ubuntu 8.04 server, and when it's up and running, I want to just copy the installation across to the new PC.  Both are i386 architecture.

---

### Post by hyper_ch on 2008-08-12
> **alloydog said:**
> Anyway, can this be done with the server edition?
What is so different about the server edition that this should be possible to do? Or rather in what way does the server and desktop edition vary?

---

### Post by alloydog on 2008-08-12
What's different? The most obvious is that when you install the server edition, you get the option option to set-up what type of server system you want at the installation phase, such as a LAMP configuration.
Plus no desktop.

I was wondering if there was any less obvious changes which may have been made to optimise it for server use, such as making it more stable by changing/removing certain functionality.  For example, a desktop is likely to be modified, say with changes to graphics adapters, even processors.  Servers generally are not, so an auto-detect for hardware may not be considered necessary.

---

### Post by hyper_ch on 2008-08-12
There are differences, mainly in the kernel and that you ahve a lot less stuff installed.

However they way how the processor, ram, harddisk, network card etc. is accessesed, is still the same. So that should be no issue.

What might happen is if there runs some piece of hardware on the new system for which the kernel has no drivers. Besides that, you can just move the harddisk around.

---

