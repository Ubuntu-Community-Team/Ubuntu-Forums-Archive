---
title: "user group modifictaion via command line"
date: 2008-02-13
forum: Security Discussions
---

### Post by unicron0827 on 2008-02-13
a coworker of mind was trying to mess with user admin, and somehow broke it.

he enabled the root account but not root login and at the same time removed ADMIN from his only account (user-operator, for syntax sake) secondary group list

and now everytime he tries to make any setting change, or anything else that involves SU/SUDO it fails on both his password and the root password, is there any way to fix this, im presuming its via command line

---

### Post by Jussi Kukkonen on 2008-02-13
Boot into single user mode (you'll be root), then set password or change the groups as you like.Booting into single user mode is possible just by selecting the option in grub on a default ubuntu install, IIRC

---

### Post by k_grdn on 2008-02-13
Hi,

You'll need the root password for single user mode. :(

At grub menu, esc, e to edit then add:

init=/bin/bash

To the end of the kernel string.

Regards,

k_grdn

---

### Post by Jussi Kukkonen on 2008-02-14
> You'll need the root password for single user mode.
oh? I know Debian does that, but I thought Ubuntu didn't... Good to know.

EDIT: Now that I think about it, it probably depends on whether root password is set. :)

---

### Post by The Cog on 2008-02-17
Ubuntu has a mod whereby if no root password is set (as with a standard install) then single-user mode drops into a shell without even asking for a password.

---

### Post by bodhi.zazen on 2008-02-18
> **unicron0827 said:**
> a coworker of mind was trying to mess with user admin, and somehow broke it.

he enabled the root account but not root login and at the same time removed ADMIN from his only account (user-operator, for syntax sake) secondary group list

and now everytime he tries to make any setting change, or anything else that involves SU/SUDO it fails on both his password and the root password, is there any way to fix this, im presuming its via command line

The way to fix the problem is to boot a live CD, mount your ubuntu partition at say /media/ubuntu

Then edit /media/ubuntu/etc/group and add the user back to the admin group.

---

