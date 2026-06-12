---
title: "UNetbootin"
date: 2007-11-27
forum: The Cafe
---

### Post by igknighted on 2007-11-27
[http://www.download.com/UNetbootin/3000-2094_4-10755820.html?tag=lst-0-2](http://www.download.com/UNetbootin/3000-2094_4-10755820.html?tag=lst-0-2)

Was browsing cnet for a good registry cleaner for work and stumbled across this... don't have time to look too much into it at the moment, but it seems like the absolute ideal way for an install.  I plan to try it out later, but I'm wondering if anyone else has tried it and what they thought.

---

### Post by ice60 on 2007-11-27
are you looking for something for windows? i haven't used windows for a few years, but there are loads of threads at a forum i go to about programs that let you install programs in a virtual machine, or let you boot up windows and do whatever you want, then when you reboot everything goes back to when you first started.

here are some programs i just found in one of the threads -
Returnil, Powershadow, Shadowprotect, Deepfreeze

---

### Post by mindtrick on 2007-11-27
[http://lubi.sourceforge.net/unetbootin.html](http://lubi.sourceforge.net/unetbootin.html)

Worked pretty well for me.

---

### Post by igknighted on 2007-11-27
> **ice60 said:**
> are you looking for something for windows? i haven't used windows for a few years, but there are loads of threads at a forum i go to about programs that let you install programs in a virtual machine, or let you boot up windows and do whatever you want, then when you reboot everything goes back to when you first started.

here are some programs i just found in one of the threads -
Returnil, Powershadow, Shadowprotect, Deepfreeze

Nope, just away to avoid the inevitable coaster of a bad distro :).  But the option to use it on either windows or linux (as unetbootin seems to be able to do) is a definite plus.

The thing that really appealed to me is this creates the new install on a true partition.  I was very excited about Wubi, but then I learned it was only a loop-mounted partition and not the real thing. Very disapointing.  Again, I am looking at this as an alternative to the burn-a-disk-to-install philosophy, not a new-user-try-me-out solution.

---

### Post by lvleph on 2007-11-28
I want to know if it uses GRUB or Boot.ini for the main boot manager. I don't like dual boot using GRUB, so if it uses boot.ini I am all over it. Currently I am using Wubi, and so the loop-mounted partition has caused some limitations that are quite annoying. QEMU isn't working well enough for me to migrate completely to Ubuntu, but I am working on that.

EDIT: It uses GRUB, but if one decides to Uninstall UNetbootin it automagically restores the Boot.ini.

---

