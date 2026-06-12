---
title: "a question about home directory encryption"
date: 2010-11-30
forum: Security
---

### Post by Dreki on 2010-11-30
lets say I install Ubuntu 10.10 on my laptop.  I check the box that says encrypt my home directory, and my password is a randomly generated 10 character password using uppercase and lowercase letters and numbers.  The next day my laptop gets stolen or something.  How hard would it be for someone to decrypt the home directory if that were the goal?

---

### Post by FuturePilot on 2010-11-30
Extremely difficult if not impossible. The random password would definitely help in this case.

---

### Post by Sylchat on 2010-12-04
You may want to add a BIOS password too ;)

---

### Post by movieman on 2010-12-04
> **Sylchat said:**
> You may want to add a BIOS password too ;)

Aren't BIOS password trivial to remove (e.g. by pulling out the BIOS battery)?

In any case, if the login password is secure they can't read the files; if it's not secure, they can put the disk in a different machine and read them regardless.

---

### Post by dev.null on 2010-12-04
> **Sylchat said:**
> You may want to add a BIOS password too ;)

That lasts about as long as it takes someone to remove the disk and put it in their own machine for examination.

---

### Post by Sylchat on 2010-12-05
> **movieman said:**
> Aren't BIOS password trivial to remove (e.g. by pulling out the BIOS battery)?

Exactly, I talked too fast. Removing the small MB battery indeed resets the password. Some laptops have this battery soldered, and some batteries may be hard to remove (esp. laptops). 

However, not everyone knows how to reset the CMOS... or to move the hard disk in another case. I guess most thieves will want to steal a laptop for the hardware value rather than for the data inside.
Disk or Home encryption is however a better idea, but adding a BIOS password can make the things a little more painful.

> **movieman said:**
> In any case, if the login password is secure they can't read the files; if it's not secure, they can put the disk in a different machine and read them regardless.
That is, if the home is encrypted, the disk can't be read in another pc case. If the password is strong or weak, it's another question...

---

