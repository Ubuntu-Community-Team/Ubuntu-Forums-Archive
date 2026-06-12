---
title: "Please be more careful when updating GRUB."
date: 2006-08-03
forum: Ubuntu Backports
---

### Post by Narpas on 2006-08-03
Backporters: When updating the GRUB files, please be careful to maintain the menu.lst on each user's computer. 

Also, if you haven't accepted the updates yet, please make sure to back up menu.lst before doing so.

My menu.lst was reverted back to it's original form after the update, making my computer unbootable until I was able to change it. Thumbs down, especially when I've been telling people about how easy this system is to use. You've GOT to be careful about things like this.

---

### Post by mlind on 2006-08-03
> **Narpas said:**
> Backporters: When updating the GRUB files, please be careful to maintain the menu.lst on each user's computer. 

Also, if you haven't accepted the updates yet, please make sure to back up menu.lst before doing so.

My menu.lst was reverted back to it's original form after the update, making my computer unbootable until I was able to change it. Thumbs down, especially when I've been telling people about how easy this system is to use. You've GOT to be careful about things like this.

I don't know other packages than kernel image that has anything to do with /boot/grub/menu.lst, and it modifies this file indirectly by invoking update-grub script.

Kernel upgrades are not done by Ubuntu backports project, but official kernel team. I think you installed kernel update that was released few days ago and have modified entries on "AUTOMAGIC KERNELS LIST" without understanding that that section is always rewritten by update-grub.

---

### Post by Narpas on 2006-08-07
I havn't modified that, but I'll look into it. Sorry for the misplaced blame.

---

### Post by mlind on 2006-08-07
> **Narpas said:**
> I havn't modified that, but I'll look into it. Sorry for the misplaced blame.

You have every right to do so, if you believe it was something that was done by backported/updated package.
I personally think this was result of kernel upgrade and wrong **kopt** and **groot** parameters in menu.lst.

You should probably direct your concerns to [dapper-backports]("https://launchpad.net/products/dapper-backports/+bugs") or [dapper-updates]("https://launchpad.net/distros/ubuntu/+milestone/dapper-updates") on launchpad.

---

