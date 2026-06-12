---
title: "Can't open boot manager after installing Ubuntu"
date: 2014-11-22
forum: Ubuntu/Debian BASED
---

### Post by joe147 on 2014-11-22
After installing Ubuntu, upon restart I cannot get to my USB to boot into a LiveCD to wipe the HDD. It's INSANELY annoying. I turn my laptop on, the acer splash screen appears, and then when I hold F12 for the boot manager, Ubuntu just starts right away. I can't even access the boot manager to choose to boot from a USB. I just want to wipe my HDD.

---

### Post by joe147 on 2014-11-22
I figured it out, I just needed to get into my UEFI and change show the option from disabled to enabled. But now, I can't boot any other distro's using dd or unetbootin. I'm trying to install crunchbang but it just goes back to Ubuntu. Can someone please respond?

---

### Post by oldfred on 2014-11-22
Moved to Other OS since not Ubuntu.

Do you have system in UEFI boot mode? And does Crunchbang have UEFI capability?

Are you sure you downloaded working installs. Checked md5sum of ISO.

Only some installs will work using the dd copy as they have to be configured for that. But unetbootin usually works.

---

