---
title: "Quick dumb n00b question about dual booting &amp; vms"
date: 2008-01-16
forum: Virtualisation
---

### Post by lunaz on 2008-01-16
Can I have a dual boot windows/linux system, THEN open up windows in a vm if I'm in linux?

---

### Post by ex_treeclimber on 2008-01-16
Yes, it would be possible.  When you use a dual-boot system, each O/S is independent of the other.   One system consists of Windows, the other consists of Linux with a VM instance of Windows within it.    You should be able to share disks between the two environments, but the two operating systems will remain independent.

---

### Post by ex_treeclimber on 2008-01-16
Here is a follow-up to my previous reply.

An interesting article on how to set up a dual-boot Windows/Linux environment can be found at - [http://www.matthewjmiller.net/howtos/dual-boot-linux-and-windows/](http://www.matthewjmiller.net/howtos/dual-boot-linux-and-windows/)

One key idea that I saw in the article is that it is easier to install Windows first, then install Ubuntu and then install the VM Windows environment under Ubuntu.

Also, the author of the article is very adamant about creating a Linux System Rescue CD before you begin the dual-boot installation.

---

