---
title: "System 76 driver for 9.10??? what needs changing?"
date: 2009-08-19
forum: System76 Support
---

### Post by sccolbert on 2009-08-19
Hi, 

(bonp2)

I've installed kubuntu karmic alpha and it went into hibernate. Upon resume the screen was dimmed, and since my brightness hotkeys didnt work, I went to reinstall the latest System76 driver. It said my ubuntu version was unsupported, so I upacked the .deb and modified the System76driver.py to allow version 9.10. 

Unfortunately, it seems more than that is necessary. The driver now starts, but restore and update do nothing. They just bring up blank dialogs. 

What other mods do I need to make to the driver to allow it to function on 9.10?


as it stands, my brightness is set to minimum, and a restart doesnt bring it back up. I'll be your guinea pig because I need to get this fixed :) 

Cheers!

Chris

---

### Post by sccolbert on 2009-08-19
Ok, so I also modded base_system.py and driverscontrol.py to mimic the installs for bonp2 under 9.04. 

Now the dialogs launch but run indefinately. I think the issue lies with acpi.osiNotWindows(). 

On my machine, karmic 9.10 alpha 4 kubuntu, there is no file /boot/grub/menu.lst

further, a "grep acpi_osi /boot/grub/*" comes up with nothing. 

I really only care about getting the brightness keys to work. Is that done through this acpi setting, or the linux backports? 

Cheers!

Chris

---

### Post by sccolbert on 2009-08-19
it seems to be an issue with grub2 and its handling of double quotes:

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/411597](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/411597)

So there must still be a way to change the brightness of the screen without this setting, since it was bright before, but not now. 

Any ideas?

---

### Post by jml on 2009-08-19
I am not sure, but if you have a computer that uses an Intel video driver, it may be the Intel driver that is causing the problem.  There are known issues reported with that driver in both 9.04 and apparently 9.10. And also with many of the newer distros.  Here is a link to a distrowatch article talking about it.

[http://distrowatch.com/weekly.php?issue=20090817#feature](http://distrowatch.com/weekly.php?issue=20090817#feature)

It seems that the only way to get really solid/reliable video with an Intel chip set is to run one of the older distros, (Debian 5.0, Ubuntu 8.10, etc.)

Joe

---

### Post by sccolbert on 2009-08-19
this is with an nvidia gtx280m card. Worked fine in Jaunty.

---

