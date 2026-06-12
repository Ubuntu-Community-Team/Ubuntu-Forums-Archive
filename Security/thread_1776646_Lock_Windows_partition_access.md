---
title: "Lock Windows partition access"
date: 2011-06-06
forum: Security
---

### Post by tribalboy on 2011-06-06
Hi Guys,

  I need to block access to my windows partition if someone boots from a LiveCD to mount the windows drive (or) shrinks the windows partition, installs Ubuntu and tries to access the Windows side. How can I achieve this

Thanks in advance

---

### Post by Lars Noodén on 2011-06-06
Set the BIOS on your computer to not boot from anything except the hard drive and then set a password on your BIOS to prevent changes.
Then put a password on grub.  There are howtos and tutorials for that.

---

### Post by amauk on 2011-06-06
Not really possible
If someone has physical access to a machine, there's little you can do to "protect" your windows install

Most BIOS passwords can be overridden with jumpers (to avoid accidentally locking yourself out)

---

### Post by bodhi.zazen on 2011-06-06
> **amauk said:**
> Not really possible
If someone has physical access to a machine, there's little you can do to "protect" your windows install

Most BIOS passwords can be overridden with jumpers (to avoid accidentally locking yourself out)

I agree with this advice. IMO the BIOS / Hard driver / grub passwords may make you feel better, but they add little to security.

You can add such things if you wish.

IMO the best solution is to encrypt any sensitive data, both LUKS and Truecrypt are cross platform.

---

### Post by tribalboy on 2011-06-06
Thanks guys, I have thought about using TrueCrypt but did not attempt it as I wasnt sure if it could be uninstalled.

---

### Post by bodhi.zazen on 2011-06-07
> **tribalboy said:**
> Thanks guys, I have thought about using TrueCrypt but did not attempt it as I wasnt sure if it could be uninstalled.

yes truecrypt can be removed

---

