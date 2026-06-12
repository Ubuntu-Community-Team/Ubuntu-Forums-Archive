---
title: "Fresh Ubuntu installation"
date: 2019-10-07
forum: Ubuntu, Linux and OS Chat
---

### Post by gerard1 on 2019-10-07
After my server crashed, reinstalled Ubuntu, however, nothing worked correct.
Than I remembered, from a year ago.
Reinstalling Ubuntu does not clean the previous installation.
Even when you use that option, erase disk.

I place this remark there the issue is present for more than a year.

Greetings Gerard,

Only using Gparted will solve the issues.

---

### Post by QIII on 2019-10-07
Hello.

I am not sure what you are saying here, as a "Use Entire Disk" does, indeed, write over the entire previous installation.  The previous installation is preserved if and only if you chose to have it preserved.

If you think you have discovered a bug, this is not the place to report it.  We are all volunteer end-users such as yourself (including the Staff).  We are not developers.  Bugs can be reported at launchpad.net.

As this is not a support request, moved to ULOSC.

---

### Post by Skaperen on 2019-10-07
what i do to force a truly fresh install is to boot up the try+install image (i have a few USB memory sticks ready to go with it, but you can burn it on a DVD, if you prefer), select "try Ubuntu" to get a running Ubuntu system, open a terminal to a shell, the wipe the drive's partition table with the command "[COLOR=#0000cd][FONT=courier new]**dd if=/dev/zero bs=4096 count=256 oflag=sync of=/dev/sda1**[/FONT][/COLOR]".  be very careful if you have more than one storage device, as a mistake can wipe it or your USB memory stick if you booted from one.  then there is nothing to re-use on that device.  as an alternate, leave out the _count=_ option to wipe the whole device to be super clean (not enough to meet top-secret requirements).

i also, then, partition the device my preferred way (i have a script) and use the "something else" option during the install.

---

