---
title: "XP Virtualization: Using the UPGRADE disk"
date: 2009-07-18
forum: Virtualisation
---

### Post by strange_cathect on 2009-07-18
I am having difficulty installing XP within Ubuntu using KVM. During installation I am asked to show that I have a previous version of a Windows product (I have a Windows 98 disk). I am unable to go any further in the install; it doesn't recognize my disk for some reason and I have to abort.

Can anyone help with this or have any experience with this issue?

Thank you!

---

### Post by Shazaam on 2009-07-18
I have no answer for the disk problem but I might have a workaround. Try installing Win98 first then install XP over it.

---

### Post by strange_cathect on 2009-07-18
Hi, I tried that avenue first, but I couldn't get 98 to install.

---

### Post by Tomy on 2009-07-18
[B]When you start kvm are you setting up the floppy device?

the man page for qemu says to do something like this:

-fda /dev/fd0 

I don't have a floppy attached so I can't verify that this works.
[/B]

---

