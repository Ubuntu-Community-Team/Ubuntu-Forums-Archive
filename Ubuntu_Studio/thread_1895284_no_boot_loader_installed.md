---
title: "no boot loader installed"
date: 2011-12-14
forum: Ubuntu Studio
---

### Post by espo111 on 2011-12-14
I just installed Ubuntu Studio 11.10 in a dual-XP boot environment.

XP is completely on a SATA drive while Ubuntu Studio is completely on a separate IDE drive.

The SATA drive is configured in the BIOS to boot first.

After the install, there was no boot loader installed and it goes straight into XP.

If I unplug the XP SATA drive, nothing at all boots, i cannot not get into the Ubuntu system.

I have no experience with installing boot loaders (grub or lilo) so I was hoping someone can point me in the right direction.

thanks

-f

---

### Post by BC59 on 2011-12-14
Looks like the Grub is loaded on the IDE drive. Can you change from the BIOS to boot first?

---

### Post by espo111 on 2011-12-14
I was able to fix this.

I booted a live cd with internet.
then followed this:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)


and it worked!

---

